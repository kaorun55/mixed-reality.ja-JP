---
title: Unity での空間マッピング
description: Unity で実際のジオメトリをレンダリングし、衝突します。
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、空間マッピング、レンダラー、collider、メッシュ、スキャン、コンポーネント
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148648"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="4f36c-104">Unity での空間マッピング</span><span class="sxs-lookup"><span data-stu-id="4f36c-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="4f36c-105">このトピックでは、Unity プロジェクトで[空間マッピング](spatial-mapping.md)を使用する方法について説明します。また、HoloLens デバイスを中心にしたワールドの表面を表す三角形のメッシュを取得して、配置、閉鎖、ルーム分析などを行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="4f36c-106">Unity には、次の方法で開発者に公開される空間マッピングの完全なサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4f36c-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="4f36c-107">MixedRealityToolkit で使用可能な空間マッピングコンポーネント。これは、空間マッピングを開始するための便利で迅速なパスを提供します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="4f36c-108">フルコントロールを提供し、より高度なアプリケーション固有のカスタマイズを可能にする、下位レベルの空間マッピング Api</span><span class="sxs-lookup"><span data-stu-id="4f36c-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="4f36c-109">アプリで空間マッピングを使用するには、Package.appxmanifest で spatialPerception 機能を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="4f36c-110">SpatialPerception 機能の設定</span><span class="sxs-lookup"><span data-stu-id="4f36c-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="4f36c-111">アプリで空間マッピングデータを使用するためには、SpatialPerception 機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="4f36c-112">SpatialPerception 機能を有効にする方法:</span><span class="sxs-lookup"><span data-stu-id="4f36c-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="4f36c-113">Unity エディターで、 **[プレーヤーの設定**] ウィンドウを開きます (> プロジェクトの設定を編集し > player)</span><span class="sxs-lookup"><span data-stu-id="4f36c-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="4f36c-114">**[Windows ストア]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f36c-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="4f36c-115">[**発行の設定]** を展開し、 **[機能]** ボックスの一覧の **"SpatialPerception"** 機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="4f36c-116">既に Unity プロジェクトを Visual Studio ソリューションにエクスポートしている場合は、新しいフォルダーにエクスポートするか、 [Visual studio の package.appxmanifest でこの機能](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)を手動で設定する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4f36c-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="4f36c-117">空間マッピングでは、少なくとも10.0.10586.0 の MaxVersionTested が必要です。</span><span class="sxs-lookup"><span data-stu-id="4f36c-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="4f36c-118">Visual Studio でソリューションエクスプローラーで package.appxmanifest を右クリックし、 **[コードの表示]** を選択し**ます。**</span><span class="sxs-lookup"><span data-stu-id="4f36c-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="4f36c-119">**TargetDeviceFamily**を指定する行を探し、 **maxversiontested = ""** を**maxversiontested 済み = "10.0.10586.0"** に変更します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="4f36c-120">Package.appxmanifest を**保存**します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="4f36c-121">Unity の組み込みの空間マッピングコンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="4f36c-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="4f36c-122">Unity には、アプリに空間マッピングを簡単に追加するためのコンポーネントが2つ用意されています。空間マッピングの**レンダラー**と**空間マッピングの Collider**です。</span><span class="sxs-lookup"><span data-stu-id="4f36c-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="4f36c-123">空間マッピングレンダラー</span><span class="sxs-lookup"><span data-stu-id="4f36c-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="4f36c-124">空間マッピングレンダラーを使用すると、空間マッピングメッシュを視覚化できます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Unity の空間マッピングレンダラー](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="4f36c-126">空間マッピング Collider</span><span class="sxs-lookup"><span data-stu-id="4f36c-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="4f36c-127">空間マッピングの Collider を使用すると、領域マッピングメッシュを使用して、物理などの holographic コンテンツ (または文字) の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Unity の空間マッピング Collider](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="4f36c-129">組み込みの空間マッピングコンポーネントの使用</span><span class="sxs-lookup"><span data-stu-id="4f36c-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="4f36c-130">物理サーフェスを視覚化して操作する場合は、両方のコンポーネントをアプリに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="4f36c-131">Unity アプリでこれらの2つのコンポーネントを使用するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="4f36c-132">空間サーフェスメッシュを検出する領域の中央にある [ユーザー] オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="4f36c-133">[インスペクター] ウィンドウで、**コンポーネント** > **XR** > **空間マッピング Collider** または**空間マッピングレンダラー**を追加します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="4f36c-134">これらのコンポーネントの使用方法の詳細については、 <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity ドキュメントサイト</a>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f36c-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="4f36c-135">組み込みの空間マッピングコンポーネント以外に</span><span class="sxs-lookup"><span data-stu-id="4f36c-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="4f36c-136">これらのコンポーネントを使用すると、空間マッピングを簡単に開始できるように、ドラッグアンドドロップ操作を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="4f36c-137"> 詳細に進むには、次の2つの主要なパスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f36c-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="4f36c-138">独自の下位レベルのメッシュ処理を行うには、以下の「低レベルの空間マッピングスクリプト API について」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f36c-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="4f36c-139">上位レベルのメッシュ分析を行うには、 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>の SpatialUnderstanding ライブラリに関する以下のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f36c-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="4f36c-140">低レベルの Unity 空間マッピング API の使用</span><span class="sxs-lookup"><span data-stu-id="4f36c-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="4f36c-141">空間マッピングレンダラーコンポーネントと空間マッピング Collider コンポーネントから取得するよりも制御が必要な場合は、低レベルの空間マッピングスクリプト Api を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="4f36c-142">**名前空間:**  *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="4f36c-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="4f36c-143">**型**:*SurfaceObserver*、 *SurfaceChange*、 *SurfaceData*、 *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="4f36c-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="4f36c-144">空間マッピング Api を使用するアプリケーションで推奨されるフローの概要を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="4f36c-145">SurfaceObserver を設定する</span><span class="sxs-lookup"><span data-stu-id="4f36c-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="4f36c-146">空間マッピングデータが必要な、アプリケーションで定義された領域の領域ごとに1つの SurfaceObserver オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="4f36c-147">SetVolumeAsSphere、SetVolumeAsAxisAlignedBox、SetVolumeAsOrientedBox、または Setvolumeassphere を呼び出すことによって、各 SurfaceObserver オブジェクトがデータを提供する領域を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="4f36c-148">これらのメソッドのいずれかを再度呼び出すだけで、後で領域の領域を再定義することができます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="4f36c-149">SurfaceObserver () を呼び出す場合は、空間マッピングシステムに新しい情報が格納されている SurfaceObserver の領域領域の各空間サーフェスに対して、ハンドラーを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="4f36c-150">このハンドラーは、1つの空間サーフェスに対してを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="4f36c-151">サーフェイスの変更の処理</span><span class="sxs-lookup"><span data-stu-id="4f36c-151">Handling Surface Changes</span></span>

<span data-ttu-id="4f36c-152">処理する主なケースがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-152">There are several main cases to handle.</span></span> <span data-ttu-id="4f36c-153">同じコードパスを使用して削除することができる更新 & が追加されました。</span><span class="sxs-lookup"><span data-stu-id="4f36c-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="4f36c-154">この例で追加された & 更新されたケースでは、このメッシュを表す SurfaceData オブジェクトをディクショナリから追加または取得し、必要なコンポーネントを含む構造体を作成した後、RequestMeshDataAsync を呼び出して、このオブジェクトにメッシュデータを設定します。シーン内の位置。</span><span class="sxs-lookup"><span data-stu-id="4f36c-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="4f36c-155">削除された場合は、このメッシュを表すオブジェクトをディクショナリから削除し、破棄します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a><span data-ttu-id="4f36c-156">データの準備完了</span><span class="sxs-lookup"><span data-stu-id="4f36c-156">Handling Data Ready</span></span>

<span data-ttu-id="4f36c-157">OnDataReady ハンドラーは、SurfaceData オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="4f36c-158">WorldAnchor、MeshFilter、および (必要に応じて) MeshCollider オブジェクトには、関連付けられている空間サーフェスの最新の状態が反映されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="4f36c-159">必要に応じて、MeshFilter オブジェクトのメッシュメンバーにアクセスして、メッシュデータの分析や[処理](spatial-mapping.md#mesh-processing)を実行します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="4f36c-160">最新のメッシュを使用して空間サーフェスをレンダリングし、必要に応じて物理衝突と raycasts に使用します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="4f36c-161">SurfaceData の内容が null でないことを確認することが重要です。</span><span class="sxs-lookup"><span data-stu-id="4f36c-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="4f36c-162">更新の処理を開始します</span><span class="sxs-lookup"><span data-stu-id="4f36c-162">Start processing on updates</span></span>

<span data-ttu-id="4f36c-163">SurfaceObserver () は、すべてのフレームではなく、遅延時に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="4f36c-164">高レベルのメッシュ分析:SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="4f36c-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="4f36c-165"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>は、Holographic Unity api に基づいて構築された holographic 開発用の便利なユーティリティコードを集めたものです。</span><span class="sxs-lookup"><span data-stu-id="4f36c-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="4f36c-166">空間の理解</span><span class="sxs-lookup"><span data-stu-id="4f36c-166">Spatial Understanding</span></span>

<span data-ttu-id="4f36c-167">物理的な世界にホログラムを配置するときは、多くの場合、空間マッピングのメッシュとサーフェス平面を超えることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4f36c-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="4f36c-168">Procedurally の配置が完了したら、より高いレベルの環境を理解することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4f36c-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="4f36c-169">これには通常、floor、天井、および壁面の決定を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="4f36c-170">また、配置の制約のセットに対して最適化して、holographic オブジェクトにとって最も望ましい物理的な場所を決定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="4f36c-171">若い Conker とフラグメントの開発中に、Asobo スタジオはこの問題に直面し、この目的のための部屋のソルバーを開発していました。</span><span class="sxs-lookup"><span data-stu-id="4f36c-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="4f36c-172">これらの各ゲームにはゲーム固有のニーズがありましたが、中心的な空間認識テクノロジを共有しています。</span><span class="sxs-lookup"><span data-stu-id="4f36c-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="4f36c-173">HoloToolkit ライブラリは、このテクノロジをカプセル化しています。これにより、壁上の空のスペースをすばやく検索したり、オブジェクトを天井に配置したり、文字の位置を識別したり、その他の多くの空間を理解したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="4f36c-174">すべてのソースコードが含まれているので、ニーズに合わせてカスタマイズし、その機能強化をコミュニティと共有することができます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="4f36c-175">このC++ソルバーのコードは、UWP dll にラップされ、MixedRealityToolkit 内に含まれている drop in prefab を使用して Unity に公開されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="4f36c-176">モジュールについて</span><span class="sxs-lookup"><span data-stu-id="4f36c-176">Understanding Modules</span></span>

<span data-ttu-id="4f36c-177">モジュールによって公開される3つの主要なインターフェイスは、単純な surface と空間クエリのトポロジ、オブジェクト検出のための図形、およびオブジェクトセットの配置に基づくオブジェクト配置ソルバーです。</span><span class="sxs-lookup"><span data-stu-id="4f36c-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="4f36c-178">これらのそれぞれについて以下に説明します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-178">Each of these is described below.</span></span> <span data-ttu-id="4f36c-179">3つの主要なモジュールインターフェイスに加えて、射線のキャストインターフェイスを使用してタグ付きサーフェス型を取得し、カスタムの watertight playspace メッシュをコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="4f36c-180">射線のキャスト</span><span class="sxs-lookup"><span data-stu-id="4f36c-180">Ray Casting</span></span>

<span data-ttu-id="4f36c-181">部屋がスキャンされ、完了すると、床、天井、壁などの表面にラベルが内部的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="4f36c-182">"PlayRaycastResult Eraycast" 関数は、射線を受け取り、光線が既知の表面と競合している場合は、その表面に関する情報を "" の形式で返します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="4f36c-183">内部的には、raycast は、playspace の計算された8cm キューブ voxel 表現に対して計算されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="4f36c-184">各 voxel には、処理されたトポロジデータを含む surface 要素のセットが含まれています (「」)。</span><span class="sxs-lookup"><span data-stu-id="4f36c-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="4f36c-185">交差する voxel セルに含まれているが比較され、トポロジ情報の検索に使用される最適な一致が得られます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="4f36c-186">このトポロジデータには、"SurfaceTypes" 列挙型の形式で返されるラベルと、交差するサーフェイスの表面領域が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="4f36c-187">Unity のサンプルでは、カーソルは各フレームに射線をキャストします。</span><span class="sxs-lookup"><span data-stu-id="4f36c-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="4f36c-188">まず、Unity の colliders に対して行います。</span><span class="sxs-lookup"><span data-stu-id="4f36c-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="4f36c-189">2つ目は、モジュールのワールド表現を理解することです。</span><span class="sxs-lookup"><span data-stu-id="4f36c-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="4f36c-190">最後に、UI 要素を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-190">And finally, again UI elements.</span></span> <span data-ttu-id="4f36c-191">このアプリケーションでは、UI の優先順位を取得し、結果を理解した後、Unity の colliders を取得します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="4f36c-192">SurfaceType は、カーソルの横にテキストとして報告されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="4f36c-193">![Surface の種類がカーソルの横に表示される](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f36c-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="4f36c-194">*Surface の種類がカーソルの横に表示される*</span><span class="sxs-lookup"><span data-stu-id="4f36c-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="4f36c-195">トポロジクエリ</span><span class="sxs-lookup"><span data-stu-id="4f36c-195">Topology Queries</span></span>

<span data-ttu-id="4f36c-196">DLL 内では、トポロジマネージャーは環境のラベル付けを処理します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="4f36c-197">前述のように、データの大部分は、voxel ボリューム内に含まれる、1つのデータに格納されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="4f36c-198">さらに、"Playspace 情報" 構造体は、再生スペースに関する情報を格納するために使用されます。これには、ワールドアラインメント (下記の詳細情報)、floor、および天井高さが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="4f36c-199">ヒューリスティックは、floor、シーリング、および壁面を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="4f36c-200">たとえば、1 ~ 2 の範囲を超える水平方向サーフェイスは、床面と見なされます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="4f36c-201">このプロセスでは、スキャン処理中のカメラパスも使用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4f36c-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="4f36c-202">トポロジマネージャーによって公開されるクエリのサブセットは、dll を通じて公開されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="4f36c-203">公開されているトポロジクエリは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4f36c-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="4f36c-204">各クエリには、クエリの種類に固有のパラメーターのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="4f36c-205">次の例では、必要なボリュームの最小の高さ & 幅、床の上の最小配置高さ、およびボリュームの前面にある最小のクリアランスの量をユーザーが指定しています。</span><span class="sxs-lookup"><span data-stu-id="4f36c-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="4f36c-206">すべての測定値は、メーターで計算されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="4f36c-207">これらの各クエリは、"TopologyResult" 構造体の事前に割り当てられた配列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="4f36c-208">"LocationCount" パラメーターは、渡された配列の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="4f36c-209">戻り値は、返された場所の数を報告します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="4f36c-210">この数は、渡された "locationCount" パラメーターよりも大きくありません。</span><span class="sxs-lookup"><span data-stu-id="4f36c-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="4f36c-211">"TopologyResult" には、返されたボリュームの中央の位置、フェーシングの方向 (通常は)、および検出された領域のサイズが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="4f36c-212">Unity サンプルでは、これらの各クエリが仮想 UI パネルのボタンにリンクされていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4f36c-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="4f36c-213">サンプルでは、これらの各クエリのパラメーターを妥当な値にハードコーディングしています。</span><span class="sxs-lookup"><span data-stu-id="4f36c-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="4f36c-214">その他の例については、サンプルコードの SpaceVisualizer.cs を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f36c-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="4f36c-215">クエリのシェイプ</span><span class="sxs-lookup"><span data-stu-id="4f36c-215">Shape Queries</span></span>

<span data-ttu-id="4f36c-216">Dll 内では、shape analyzer ("ShapeAnalyzer_W") がトポロジアナライザーを使用して、ユーザーが定義したカスタム図形と照合します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="4f36c-217">Unity のサンプルでは、図形のセットを定義し、[図形] タブ内の [アプリ内クエリ] メニューを使用して結果を表示します。その目的は、ユーザーが独自のオブジェクト図形のクエリを定義し、アプリケーションの必要に応じてそれらを利用できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="4f36c-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="4f36c-218">図形の分析は、水平方向のサーフェイスでのみ動作することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4f36c-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="4f36c-219">たとえば、ソファは、平らな座席の表面とソファの上面によって定義されています。</span><span class="sxs-lookup"><span data-stu-id="4f36c-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="4f36c-220">Shape クエリでは、特定のサイズ、高さ、および縦横範囲の2つのサーフェスが検索され、2つのサーフェスがアラインされ、接続されています。</span><span class="sxs-lookup"><span data-stu-id="4f36c-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="4f36c-221">Api の用語を使用して、ソファ座席と背面は形状コンポーネントであり、アラインメント要件はシェイプコンポーネントの制約です。</span><span class="sxs-lookup"><span data-stu-id="4f36c-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="4f36c-222">"Sittable" オブジェクトの Unity サンプル (ShapeDefinition.cs) で定義されているクエリの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="4f36c-223">各図形クエリは、一連の図形コンポーネントによって定義されます。各図形コンポーネントには、一連のコンポーネント制約と、コンポーネント間の依存関係を示す一連の図形制約があります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="4f36c-224">この例では、1つのコンポーネント定義に3つの制約が含まれており、コンポーネント間に図形の制約はありません (コンポーネントが1つだけであるため)。</span><span class="sxs-lookup"><span data-stu-id="4f36c-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="4f36c-225">これに対し、ソファ図形には、2つの図形コンポーネントと4つのシェイプ制約があります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="4f36c-226">コンポーネントは、ユーザーのコンポーネントリスト内のインデックスによって識別されることに注意してください (この例では0と 1)。</span><span class="sxs-lookup"><span data-stu-id="4f36c-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="4f36c-227">カスタム図形の定義を簡単に作成するために、Unity モジュールにラッパー関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="4f36c-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="4f36c-228">コンポーネントとシェイプの制約の完全な一覧は、"ShapeComponentConstraint" 構造と "ShapeConstraint" 構造内の "SpatialUnderstandingDll.cs" にあります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="4f36c-229">![四角形の形状がこの画面にあります](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f36c-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="4f36c-230">*四角形の形状がこの画面にあります*</span><span class="sxs-lookup"><span data-stu-id="4f36c-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="4f36c-231">オブジェクト配置のソルバー</span><span class="sxs-lookup"><span data-stu-id="4f36c-231">Object Placement Solver</span></span>

<span data-ttu-id="4f36c-232">オブジェクト配置のソルバーを使用して、オブジェクトを配置する物理的な部屋内の理想的な場所を識別できます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="4f36c-233">ソルバーは、オブジェクトのルールと制約を指定して最適な場所を見つけます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="4f36c-234">さらに、オブジェクトクエリは、オブジェクトが "Solver_RemoveObject" または "Solver_RemoveAllObjects" 呼び出しで削除されるまで保持されます。これにより、制約された複数オブジェクト配置が可能になります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="4f36c-235">オブジェクト配置クエリは、3つの部分で構成されます。パラメーターを持つ配置の種類、規則の一覧、および制約の一覧です。</span><span class="sxs-lookup"><span data-stu-id="4f36c-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="4f36c-236">クエリを実行するには、次の API を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-236">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="4f36c-237">この関数は、オブジェクト名、配置定義、および規則と制約の一覧を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="4f36c-238">ラッパー C#は、規則と制約の構築を容易にする構築ヘルパー関数を提供します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="4f36c-239">配置定義には、次のいずれかのクエリの種類が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-239">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

<span data-ttu-id="4f36c-240">各配置型には、型に固有のパラメーターのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="4f36c-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="4f36c-241">"ObjectPlacementDefinition" 構造体には、これらの定義を作成するための静的ヘルパー関数のセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4f36c-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="4f36c-242">たとえば、床にオブジェクトを配置する場所を見つけるには、次の関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="4f36c-243">public static Objectplacement Ementdefinition Create_OnFloor (Vector3 半 Dims) 配置の種類に加えて、一連のルールと制約を指定できます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="4f36c-244">規則に違反することはありません。</span><span class="sxs-lookup"><span data-stu-id="4f36c-244">Rules cannot be violated.</span></span> <span data-ttu-id="4f36c-245">型とルールを満たす配置場所は、最適な配置場所を選択するために、一連の制約に対して最適化されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="4f36c-246">各ルールと制約は、指定された静的作成関数によって作成できます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="4f36c-247">ルールと制約の構築関数の例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="4f36c-248">次のオブジェクト配置クエリは、表面の端に半分のメーターキューブを配置する場所を探しています。これは、以前に配置された他のオブジェクトから、部屋の中心付近に向かっています。</span><span class="sxs-lookup"><span data-stu-id="4f36c-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="4f36c-249">成功した場合、配置位置、次元、および向きを含む "Objectplacement Ementresult" 構造体が返されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="4f36c-250">また、配置は、配置されたオブジェクトの dll の内部リストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="4f36c-251">後続の配置クエリでは、このオブジェクトが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="4f36c-252">Unity サンプルの "LevelSolver.cs" ファイルには、クエリの例が多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="4f36c-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="4f36c-253">![オブジェクトの配置の結果](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f36c-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="4f36c-254">*図 3:青色のボックスは、カメラの位置ルールから離れた場所にある3つのフロアクエリの結果を示すものです。*</span><span class="sxs-lookup"><span data-stu-id="4f36c-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="4f36c-255">レベルまたはアプリケーションのシナリオで必要とされる複数のオブジェクトの配置場所を解決する場合、は、領域が見つかる確率を最大化するために、最初に不可欠なオブジェクトとラージオブジェクトを解決します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="4f36c-256">配置順序は重要です。</span><span class="sxs-lookup"><span data-stu-id="4f36c-256">Placement order is important.</span></span> <span data-ttu-id="4f36c-257">オブジェクトの配置が見つからない場合は、制限の少ない構成を試してください。</span><span class="sxs-lookup"><span data-stu-id="4f36c-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="4f36c-258">一連のフォールバック構成を設定することは、多くの部屋構成で機能をサポートするために不可欠です。</span><span class="sxs-lookup"><span data-stu-id="4f36c-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="4f36c-259">ルームスキャンプロセス</span><span class="sxs-lookup"><span data-stu-id="4f36c-259">Room Scanning Process</span></span>

<span data-ttu-id="4f36c-260">HoloLens によって提供される空間マッピングソリューションは、問題のある領域全体のニーズに対応できるように設計されていますが、空間認識モジュールは、2つの特定のゲームのニーズをサポートするように構築されています。</span><span class="sxs-lookup"><span data-stu-id="4f36c-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="4f36c-261">このソリューションは、次に示すように、特定のプロセスと想定のセットに基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="4f36c-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="4f36c-262">ユーザー駆動型の playspace "描画" –スキャンフェーズ中に、ユーザーは再生速度を移動して、必要な領域を効果的に描画します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="4f36c-263">生成されたメッシュは、このフェーズでユーザーからのフィードバックを提供するために重要です。</span><span class="sxs-lookup"><span data-stu-id="4f36c-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="4f36c-264">屋内で home または office セットアップ–クエリ関数は、フラットなサーフェイスと壁面を中心に設計されています。</span><span class="sxs-lookup"><span data-stu-id="4f36c-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="4f36c-265">これは、ソフトな制限です。</span><span class="sxs-lookup"><span data-stu-id="4f36c-265">This is a soft limitation.</span></span> <span data-ttu-id="4f36c-266">ただし、スキャンフェーズでは、主要軸と補助軸に沿ってメッシュテセレーションを最適化するために、主軸分析が完了します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="4f36c-267">含まれている SpatialUnderstanding.cs ファイルは、スキャンフェーズプロセスを管理します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="4f36c-268">次の関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-268">It calls the following functions.</span></span>

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

<span data-ttu-id="4f36c-269">"SpatialUnderstanding" 動作によって実行されるスキャンフローは、InitScan を呼び出し、その後、各フレームに対してアップデートを実行します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="4f36c-270">統計クエリによって適切なカバレッジが報告されると、ユーザーは、ユーザーが RequestFinish を呼び出して、スキャンフェーズの終了を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="4f36c-271">戻り値が dll の処理を完了したことを示すまで、アップデートを引き続き呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="4f36c-272">メッシュについて</span><span class="sxs-lookup"><span data-stu-id="4f36c-272">Understanding Mesh</span></span>

<span data-ttu-id="4f36c-273">Dll を理解すると、内部的に再生スペースが8cm サイズの voxel キューブのグリッドとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="4f36c-274">スキャンの初期部分では、主要なコンポーネント分析が完了して、部屋の軸が決定されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="4f36c-275">内部的には、これらの軸に合わせて voxel 領域を格納します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="4f36c-276">メッシュは、voxel ボリュームから isosurface を抽出することによって、約1秒ごとに生成されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="4f36c-277">![Voxel ボリュームから生成されたメッシュを生成しました](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f36c-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="4f36c-278">*Voxel ボリュームから生成されたメッシュを生成しました*</span><span class="sxs-lookup"><span data-stu-id="4f36c-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="4f36c-279">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="4f36c-279">Troubleshooting</span></span>
* <span data-ttu-id="4f36c-280">[SpatialPerception](#setting-the-spatialperception-capability)機能が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4f36c-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="4f36c-281">追跡が失われると、次の OnSurfaceChanged イベントによってすべてのメッシュが削除されます。</span><span class="sxs-lookup"><span data-stu-id="4f36c-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="4f36c-282">混合 Reality ツールキットでの空間マッピング</span><span class="sxs-lookup"><span data-stu-id="4f36c-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="4f36c-283">混合 Reality Toolkit v2 での空間マッピングの使用の詳細については、MRTK ドキュメントの「<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">空間認識」セクション</a>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f36c-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f36c-284">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f36c-284">See also</span></span>
* [<span data-ttu-id="4f36c-285">MR 空間 230:空間マッピング</span><span class="sxs-lookup"><span data-stu-id="4f36c-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="4f36c-286">座標系</span><span class="sxs-lookup"><span data-stu-id="4f36c-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="4f36c-287">Unity の座標系</span><span class="sxs-lookup"><span data-stu-id="4f36c-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="4f36c-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="4f36c-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="4f36c-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="4f36c-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="4f36c-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="4f36c-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="4f36c-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine。境界</a></span><span class="sxs-lookup"><span data-stu-id="4f36c-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
