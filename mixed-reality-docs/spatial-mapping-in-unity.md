---
title: Unity での空間のマッピング
description: レンダリングして、Unity で周囲の実際のジオメトリとの衝突とします。
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、空間マッピング、レンダラー、コライダー、メッシュ、スキャン、コンポーネント
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148648"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="534de-104">Unity での空間のマッピング</span><span class="sxs-lookup"><span data-stu-id="534de-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="534de-105">このトピックでは、使用する方法を説明します[空間マッピング](spatial-mapping.md)Unity プロジェクトで、配置、オクルー ジョン、部屋の分析などの HoloLens デバイスの世界でサーフェスを表す三角形メッシュを取得します。</span><span class="sxs-lookup"><span data-stu-id="534de-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="534de-106">Unity には、次の方法で開発者に公開される空間マッピングは、完全にサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="534de-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="534de-107">空間マッピング、MixedRealityToolkit で利用可能なコンポーネントが便利で高速のパスを指定空間マッピングの概要</span><span class="sxs-lookup"><span data-stu-id="534de-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="534de-108">下位の空間マッピング Api では、完全に提供する制御しより高度なアプリケーション固有のカスタマイズを有効にします。</span><span class="sxs-lookup"><span data-stu-id="534de-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="534de-109">空間マッピングを使用して、アプリで、spatialPerception 機能は、AppxManifest で設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="534de-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="534de-110">SpatialPerception 機能の設定</span><span class="sxs-lookup"><span data-stu-id="534de-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="534de-111">アプリ データを空間マッピングを使用するためには、SpatialPerception 機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="534de-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="534de-112">SpatialPerception 機能を有効にする方法。</span><span class="sxs-lookup"><span data-stu-id="534de-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="534de-113">Unity エディターで開き、 **「プレーヤー設定」** ウィンドウ (編集 > プロジェクトの設定 > Player)</span><span class="sxs-lookup"><span data-stu-id="534de-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="534de-114">をクリックして、 **"Windows Store"**  タブ</span><span class="sxs-lookup"><span data-stu-id="534de-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="534de-115">展開 **「発行の設定」** を確認し、 **"SpatialPerception"** 機能、 **「機能」** 一覧</span><span class="sxs-lookup"><span data-stu-id="534de-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="534de-116">Visual Studio ソリューションに既に Unity プロジェクトをエクスポートした場合でも、新しいフォルダーに手動でまたはいずれかのエクスポートする必要がする[Visual Studio で AppxManifest でこの機能を設定](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)します。</span><span class="sxs-lookup"><span data-stu-id="534de-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="534de-117">空間マッピングには、少なくとも 10.0.10586.0 の MaxVersionTested も必要です。</span><span class="sxs-lookup"><span data-stu-id="534de-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="534de-118">Visual Studio で右クリック**Package.appxmanifest**クリックし、ソリューション エクスプ ローラーで**コードの表示**</span><span class="sxs-lookup"><span data-stu-id="534de-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="534de-119">行を指定するように検索**TargetDeviceFamily**変更と**MaxVersionTested =「10.0.10240.0」** に**MaxVersionTested「=10.0.10586.0」**</span><span class="sxs-lookup"><span data-stu-id="534de-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="534de-120">**保存**Package.appxmanifest します。</span><span class="sxs-lookup"><span data-stu-id="534de-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="534de-121">Unity の組み込みの空間マッピング コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="534de-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="534de-122">Unity は、アプリを簡単に空間マッピングを追加するための 2 つのコンポーネントを提供**空間マッピング レンダラー**と**空間マッピング Collider**します。</span><span class="sxs-lookup"><span data-stu-id="534de-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="534de-123">空間マッピングのレンダラー</span><span class="sxs-lookup"><span data-stu-id="534de-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="534de-124">空間マッピング レンダラーでは、空間マッピング メッシュの視覚化ができます。</span><span class="sxs-lookup"><span data-stu-id="534de-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Unity での空間マッピング レンダラー](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="534de-126">空間マッピング Collider</span><span class="sxs-lookup"><span data-stu-id="534de-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="534de-127">空間マッピング Collider で holographic コンテンツ (または文字) は、空間マッピングのメッシュと物理学などの対話します。</span><span class="sxs-lookup"><span data-stu-id="534de-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Unity での空間マッピング Collider](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="534de-129">空間マッピングの組み込みコンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="534de-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="534de-130">視覚化して、物理画面と対話したい場合は、アプリに両方のコンポーネントを追加できます。</span><span class="sxs-lookup"><span data-stu-id="534de-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="534de-131">Unity のアプリでは、これら 2 つのコンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="534de-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="534de-132">空間表面メッシュを検出するために領域を中心の GameObject を選択します。</span><span class="sxs-lookup"><span data-stu-id="534de-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="534de-133">Inspector ウィンドウで、**コンポーネントの追加** > **XR** > **空間マッピング Collider** または**空間マッピング レンダラー**します。</span><span class="sxs-lookup"><span data-stu-id="534de-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="534de-134">これらのコンポーネントを使用する方法の詳細についての詳細を確認することができます、 <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity ドキュメント サイト</a>します。</span><span class="sxs-lookup"><span data-stu-id="534de-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="534de-135">組み込みの空間マッピング コンポーネントの先を行く</span><span class="sxs-lookup"><span data-stu-id="534de-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="534de-136">これらのコンポーネントようにドラッグ アンド ドロップ簡単空間マッピングを開始します。</span><span class="sxs-lookup"><span data-stu-id="534de-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="534de-137"> さらに移動する場合は、2 つのメイン パスを探索するがあります。</span><span class="sxs-lookup"><span data-stu-id="534de-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="534de-138">下位レベルのメッシュ処理を行うには、低レベルの空間マッピング スクリプト API の詳細については、以下のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="534de-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="534de-139">メッシュのより高度な分析で SpatialUnderstanding ライブラリの詳細については、以下のセクションを参照してください。 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>します。</span><span class="sxs-lookup"><span data-stu-id="534de-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="534de-140">API を使用して、低レベル Unity 空間マッピング</span><span class="sxs-lookup"><span data-stu-id="534de-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="534de-141">空間マッピングのレンダラーと空間マッピング コライダー コンポーネントから取得するよりも詳細に制御が必要な場合は、低レベルの空間マッピング スクリプト Api を使用できます。</span><span class="sxs-lookup"><span data-stu-id="534de-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="534de-142">**名前空間:**  *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="534de-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="534de-143">**型**:*SurfaceObserver*、 *SurfaceChange*、 *SurfaceData*、 *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="534de-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="534de-144">空間マッピング Api を使用するアプリケーションの推奨されるフローの概要を次に示します。</span><span class="sxs-lookup"><span data-stu-id="534de-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="534de-145">設定する、SurfaceObserver(s)</span><span class="sxs-lookup"><span data-stu-id="534de-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="534de-146">空間のマッピング データが必要な領域をアプリケーションで定義された地域ごとに 1 つの SurfaceObserver オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="534de-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="534de-147">各 SurfaceObserver オブジェクトは SetVolumeAsSphere、SetVolumeAsAxisAlignedBox、SetVolumeAsOrientedBox、または SetVolumeAsFrustum を呼び出すことでのデータを提供する領域の領域を指定します。</span><span class="sxs-lookup"><span data-stu-id="534de-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="534de-148">これらのメソッドのいずれかをもう一度呼び出すだけで、将来の領域の領域を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="534de-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="534de-149">SurfaceObserver.Update() を呼び出すときに、各空間のサーフェス空間マッピング システムが新しい情報の領域の SurfaceObserver のリージョンでのハンドラーを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="534de-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="534de-150">このハンドラーは、空間の 1 つの画面には。</span><span class="sxs-lookup"><span data-stu-id="534de-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="534de-151">画面の変更の処理</span><span class="sxs-lookup"><span data-stu-id="534de-151">Handling Surface Changes</span></span>

<span data-ttu-id="534de-152">処理するためにいくつかの主要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="534de-152">There are several main cases to handle.</span></span> <span data-ttu-id="534de-153">追加 (&) 同じが使用できる更新コードのパスおよび削除します。</span><span class="sxs-lookup"><span data-stu-id="534de-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="534de-154">例では、更新 (&)、追加された場合は、追加または取得ディクショナリからメッシュを必要なコンポーネントで SurfaceData 構造体を作成し、GameObject にメッシュのデータを設定する RequestMeshDataAsync を呼び出しますこの GameObject 表すこととシーンに配置します。</span><span class="sxs-lookup"><span data-stu-id="534de-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="534de-155">削除済みの場合は、ディクショナリからこのメッシュを表す GameObject を削除し、それを破棄します。</span><span class="sxs-lookup"><span data-stu-id="534de-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

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

### <a name="handling-data-ready"></a><span data-ttu-id="534de-156">処理データの準備完了</span><span class="sxs-lookup"><span data-stu-id="534de-156">Handling Data Ready</span></span>

<span data-ttu-id="534de-157">OnDataReady ハンドラーは、SurfaceData オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="534de-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="534de-158">WorldAnchor、MeshFilter および (必要に応じて) MeshCollider オブジェクトが含まれている、関連付けられている空間画面の最新の状態を反映します。</span><span class="sxs-lookup"><span data-stu-id="534de-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="534de-159">必要に応じて分析を実行または[処理](spatial-mapping.md#mesh-processing)MeshFilter オブジェクトのメッシュのメンバーにアクセスしてメッシュ データ。</span><span class="sxs-lookup"><span data-stu-id="534de-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="534de-160">最新のメッシュに空間サーフェイスを描画して、(必要に応じて) 物理衝突と raycasts に使用します。</span><span class="sxs-lookup"><span data-stu-id="534de-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="534de-161">SurfaceData の内容が null でないことを確認するのには重要です。</span><span class="sxs-lookup"><span data-stu-id="534de-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="534de-162">更新プログラムの処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="534de-162">Start processing on updates</span></span>

<span data-ttu-id="534de-163">SurfaceObserver.Update() は、遅延、すべてのフレームに呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="534de-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="534de-164">高度なメッシュ分析:SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="534de-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="534de-165"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> holographic Unity Api に基づいて構築された holographic の開発のための便利なユーティリティ コードのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="534de-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="534de-166">空間の理解</span><span class="sxs-lookup"><span data-stu-id="534de-166">Spatial Understanding</span></span>

<span data-ttu-id="534de-167">現実の世界でホログラムを配置するときに、空間のマッピングを超えるメッシュし、平面の画面を移動することが望ましいは多くの場合です。</span><span class="sxs-lookup"><span data-stu-id="534de-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="534de-168">配置が完了したら手続きより高いレベルの環境の理解をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="534de-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="534de-169">通常、このエラーは、floor、ceiling、および壁についての決定が必要です。</span><span class="sxs-lookup"><span data-stu-id="534de-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="534de-170">さらに、holographic オブジェクトの最も望ましいの物理的な場所を確認する配置の制約のセットに対して最適化するために機能します。</span><span class="sxs-lookup"><span data-stu-id="534de-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="534de-171">、Young Conker とフラグメントの開発中に、この目的のルーム問題を解くプログラムの開発には、この問題ヘッドが Asobo スタジオに直面しています。</span><span class="sxs-lookup"><span data-stu-id="534de-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="534de-172">これらのゲームのゲームの特定のニーズがテクノロジの空間についてのコアを共有しています。</span><span class="sxs-lookup"><span data-stu-id="534de-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="534de-173">配置するには、文字と、多種多様な空間についての他のクエリを識別するとすばやく検索空白には、壁、オブジェクトの切り上げを配置することができます。 このテクノロジがライブラリにカプセル化します HoloToolkit.SpatialUnderstanding が配置されます。</span><span class="sxs-lookup"><span data-stu-id="534de-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="534de-174">すべてのソース コードは、ニーズに合わせてカスタマイズし、改善をコミュニティで共有することができます、含まれています。</span><span class="sxs-lookup"><span data-stu-id="534de-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="534de-175">コードをC++ソルバーが UWP dll にラップされの場合は、MixedRealityToolkit 内に含まれるプレハブを Unity に公開します。</span><span class="sxs-lookup"><span data-stu-id="534de-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="534de-176">モジュールについて</span><span class="sxs-lookup"><span data-stu-id="534de-176">Understanding Modules</span></span>

<span data-ttu-id="534de-177">モジュールによって公開される 3 つのプライマリ インターフェイスがあります。 単純な画面と空間クエリ、オブジェクト検出では、図形、および制約ベースの配置オブジェクトのセットのオブジェクト配置のソルバーのトポロジ。</span><span class="sxs-lookup"><span data-stu-id="534de-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="534de-178">これらのそれぞれについて、次に示します。</span><span class="sxs-lookup"><span data-stu-id="534de-178">Each of these is described below.</span></span> <span data-ttu-id="534de-179">3 つのプライマリ モジュール インターフェイスに加えて、ray キャスト インターフェイスを使用して、タグが付けられたサーフェイスのタイプを取得することし、カスタムのような厳重な playspace メッシュをコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="534de-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="534de-180">光線のキャスト</span><span class="sxs-lookup"><span data-stu-id="534de-180">Ray Casting</span></span>

<span data-ttu-id="534de-181">ルームをスキャンされ、完了した後、ラベルは floor、ceiling、壁のようなサーフェイス内部的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="534de-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="534de-182">"RaycastResult"の形式で表示される情報、"PlayspaceRaycast"関数が光線に受け取り、ray が既知の画面と競合している場合であればを返します。</span><span class="sxs-lookup"><span data-stu-id="534de-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

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

<span data-ttu-id="534de-183">内部的には、playspace の計算の 8 cm cubed voxel 表現に対して、raycast が計算されます。</span><span class="sxs-lookup"><span data-stu-id="534de-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="534de-184">各 voxel には、一連画面要素に処理されたトポロジのデータ (surfels とも呼ばれます) にはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="534de-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="534de-185">Voxel が交差するセル内に含まれる surfels が比較され、最も一致するトポロジ情報を検索するために使用します。</span><span class="sxs-lookup"><span data-stu-id="534de-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="534de-186">このトポロジのデータを含む"SurfaceTypes"列挙型のフォームと交差する画面の表面領域で返される、ラベル付けします。</span><span class="sxs-lookup"><span data-stu-id="534de-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="534de-187">Unity のサンプルでは、カーソルは各フレームに伸びる射線をキャストします。</span><span class="sxs-lookup"><span data-stu-id="534de-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="534de-188">Unity のコライダーに対して最初に。</span><span class="sxs-lookup"><span data-stu-id="534de-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="534de-189">Understanding モジュールの世界の表現に対して第 2 に。</span><span class="sxs-lookup"><span data-stu-id="534de-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="534de-190">最後に、もう一度 UI 要素。</span><span class="sxs-lookup"><span data-stu-id="534de-190">And finally, again UI elements.</span></span> <span data-ttu-id="534de-191">このアプリケーションで UI は、理解の結果と Unity のコライダーの最後に、次に、優先順位を取得します。</span><span class="sxs-lookup"><span data-stu-id="534de-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="534de-192">カーソルの横にあるテキストとして、SurfaceType が報告されます。</span><span class="sxs-lookup"><span data-stu-id="534de-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="534de-193">![画面の種類のカーソルの横にあるラベルは](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="534de-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="534de-194">*画面の種類のカーソルの横にあるラベルは*</span><span class="sxs-lookup"><span data-stu-id="534de-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="534de-195">トポロジのクエリ</span><span class="sxs-lookup"><span data-stu-id="534de-195">Topology Queries</span></span>

<span data-ttu-id="534de-196">DLL 内では、トポロジのマネージャーは、環境のラベル付けを処理します。</span><span class="sxs-lookup"><span data-stu-id="534de-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="534de-197">前述のように、surfels、voxel ボリューム内に含まれるデータの多く格納されます。</span><span class="sxs-lookup"><span data-stu-id="534de-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="534de-198">さらに、"PlaySpaceInfos"構造を使用して、世界中の配置 (詳細については後述)、floor、ceiling 高さなど、playspace についての情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="534de-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="534de-199">ヒューリスティックは、floor、ceiling、壁を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="534de-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="534de-200">たとえば、1 m2 のサーフェス領域よりも大きいと、最大および最小の水平方向の画面は、床面と見なされます。</span><span class="sxs-lookup"><span data-stu-id="534de-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="534de-201">スキャン プロセス中にカメラのパスがこのプロセスで使用されるもことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="534de-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="534de-202">トポロジのマネージャーによって公開されているクエリのサブセットは、出力 dll を介して公開されます。</span><span class="sxs-lookup"><span data-stu-id="534de-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="534de-203">公開されているトポロジのクエリは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="534de-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="534de-204">各クエリは、クエリの種類に固有のパラメーターのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="534de-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="534de-205">次の例では、ユーザーは、高さの最小値と最小の配置、フロア、クリアランスの前に、ボリュームの最小量の高さ、目的のボリュームの幅を指定します。</span><span class="sxs-lookup"><span data-stu-id="534de-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="534de-206">すべての測定値では、メートル単位で。</span><span class="sxs-lookup"><span data-stu-id="534de-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="534de-207">これらの各クエリは、事前に割り当てられた"TopologyResult"構造体の配列を受け取る。</span><span class="sxs-lookup"><span data-stu-id="534de-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="534de-208">"LocationCount"パラメーターには、渡された配列の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="534de-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="534de-209">戻り値は、返される位置の数を報告します。</span><span class="sxs-lookup"><span data-stu-id="534de-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="534de-210">この数値が渡されたを超えることはありません"locationCount"パラメーターにします。</span><span class="sxs-lookup"><span data-stu-id="534de-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="534de-211">"TopologyResult"には、返されるボリュームに接続する方向 (つまり標準)、および検索の領域の大きさの中央の位置が含まれています。</span><span class="sxs-lookup"><span data-stu-id="534de-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="534de-212">Unity のサンプルでは、これらの各クエリがリンクされている仮想 UI パネルのボタンに注意してください。</span><span class="sxs-lookup"><span data-stu-id="534de-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="534de-213">ハードのサンプル コードは妥当な値にこれらのクエリの各パラメーター。</span><span class="sxs-lookup"><span data-stu-id="534de-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="534de-214">例については、サンプル コードでは、SpaceVisualizer.cs を参照してください。</span><span class="sxs-lookup"><span data-stu-id="534de-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="534de-215">Shape クエリ</span><span class="sxs-lookup"><span data-stu-id="534de-215">Shape Queries</span></span>

<span data-ttu-id="534de-216">Dll 内では、図形アナライザー ("ShapeAnalyzer_W") は、ユーザーが定義したカスタム図形と照合するトポロジ アナライザーを使用します。</span><span class="sxs-lookup"><span data-stu-id="534de-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="534de-217">Unity のサンプルでは、図形のセットを定義し、アプリ内のクエリ メニューの 図形 タブ内からの結果を生成を公開します。ユーザーが独自オブジェクト図形のクエリを定義しを加えることは、アプリケーションの必要に応じて、それらの使用します。</span><span class="sxs-lookup"><span data-stu-id="534de-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="534de-218">形状の分析が水平方向のサーフェスのみで機能するに注意してください。</span><span class="sxs-lookup"><span data-stu-id="534de-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="534de-219">たとえば、ソファーは、戻るカウチのフラットの上端とフラット seat 画面によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="534de-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="534de-220">Shape クエリは、特定のサイズ、高さ、および縦横範囲の配置し、接続されている 2 つのサーフェスの 2 つのサーフェスを探します。</span><span class="sxs-lookup"><span data-stu-id="534de-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="534de-221">Api の用語を使用するには、ソファ シートとバック上部は、図形のコンポーネントと、アラインメント要件は次の図形のコンポーネントの制約。</span><span class="sxs-lookup"><span data-stu-id="534de-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="534de-222">"Sittable"オブジェクトの Unity サンプル (ShapeDefinition.cs) で定義されているクエリの例は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="534de-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

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

<span data-ttu-id="534de-223">各図形のクエリは、一連の図形コンポーネントは、それぞれに、一連のコンポーネントの制約と、一連の図形の制約によって定義されるコンポーネント間の依存関係を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="534de-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="534de-224">この例には、(1 つだけのコンポーネントであるため)、1 つのコンポーネントの定義とコンポーネント間で制約のない図形で次の 3 つの制約が含まれます。</span><span class="sxs-lookup"><span data-stu-id="534de-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="534de-225">これに対し、ソファ図形は、2 つのコンポーネントの図形と図形の 4 つの制約をが。</span><span class="sxs-lookup"><span data-stu-id="534de-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="534de-226">コンポーネントが (0 からこの例では 1) のユーザーのコンポーネントの一覧で、インデックスで識別されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="534de-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="534de-227">ラッパー関数は、カスタム図形の定義を簡単に作成の Unity モジュールで提供されます。</span><span class="sxs-lookup"><span data-stu-id="534de-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="534de-228">コンポーネントと図形の制約の完全な一覧は、"SpatialUnderstandingDll.cs"、"ShapeComponentConstraint"および"ShapeConstraint"構造内で確認できます。</span><span class="sxs-lookup"><span data-stu-id="534de-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="534de-229">![四角形がこの画面で見つかった](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="534de-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="534de-230">*四角形がこの画面で見つかった*</span><span class="sxs-lookup"><span data-stu-id="534de-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="534de-231">オブジェクト配置のソルバー</span><span class="sxs-lookup"><span data-stu-id="534de-231">Object Placement Solver</span></span>

<span data-ttu-id="534de-232">オブジェクトの配置を対象としてプログラムは、オブジェクトを配置する物理的な部屋に理想的な場所を識別するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="534de-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="534de-233">オブジェクトの規則と制約を指定した位置に最適なソルバーが見つかります。</span><span class="sxs-lookup"><span data-stu-id="534de-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="534de-234">さらに、オブジェクト クエリは、"Solver_RemoveObject"により、オブジェクトが削除されますか、複数のオブジェクトの配置の制約付き"Solver_RemoveAllObjects"呼び出しを許可するまで保持されます。</span><span class="sxs-lookup"><span data-stu-id="534de-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="534de-235">オブジェクト配置のクエリは、3 つの部分で構成されています: パラメーター、一連の規則、制約のリストと配置の種類。</span><span class="sxs-lookup"><span data-stu-id="534de-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="534de-236">クエリを実行するには、次の API を使用します。</span><span class="sxs-lookup"><span data-stu-id="534de-236">To run a query, use the following API.</span></span>

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

<span data-ttu-id="534de-237">この関数は、オブジェクトの名前、配置の定義と規則と制約の一覧を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="534de-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="534de-238">C#ラッパーは構築の規則と制約の構築を簡単にヘルパー関数を提供します。</span><span class="sxs-lookup"><span data-stu-id="534de-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="534de-239">配置の定義には、次の 1 つは、クエリの種類 – が含まれています。</span><span class="sxs-lookup"><span data-stu-id="534de-239">The placement definition contains the query type – that is, one of the following.</span></span>

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

<span data-ttu-id="534de-240">パラメーターの型に固有の各配置の種類があります。</span><span class="sxs-lookup"><span data-stu-id="534de-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="534de-241">"ObjectPlacementDefinition"構造体には、これらの定義を作成するための静的なヘルパー関数のセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="534de-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="534de-242">たとえば、床の上にオブジェクトを配置する場所を検索するには、次の関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="534de-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="534de-243">パブリック静的 ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) でさらに、配置の種類を一連の規則と制約を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="534de-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="534de-244">規則に違反することはできません。</span><span class="sxs-lookup"><span data-stu-id="534de-244">Rules cannot be violated.</span></span> <span data-ttu-id="534de-245">型とルールに適合するような配置場所は、最適な配置場所を選択するには、一連の制約に対して最適化されています。</span><span class="sxs-lookup"><span data-stu-id="534de-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="534de-246">指定された静的作成関数によって各規則と制約を作成できます。</span><span class="sxs-lookup"><span data-stu-id="534de-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="534de-247">規則と制約の構築関数の例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="534de-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="534de-248">オブジェクトの下の配置のクエリは、画面の端に半分メーター キューブを配置から他のオブジェクトを配置前およびルームの中央の近くの場所を確保検索します。</span><span class="sxs-lookup"><span data-stu-id="534de-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

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

<span data-ttu-id="534de-249">成功した場合、配置の位置を含む"ObjectPlacementResult"構造体のサイズや方向が返されます。</span><span class="sxs-lookup"><span data-stu-id="534de-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="534de-250">さらに、配置は、配置されたオブジェクトの dll の内部一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="534de-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="534de-251">後続の配置のクエリ アカウントにこのオブジェクトになります。</span><span class="sxs-lookup"><span data-stu-id="534de-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="534de-252">Unity のサンプルでは、"LevelSolver.cs"ファイルより多くの例のクエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="534de-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="534de-253">![オブジェクトの配置の結果](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="534de-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="534de-254">*図 3:青いボックスでカメラの位置の規則から床の上の 3 つの場所からの結果のクエリ*</span><span class="sxs-lookup"><span data-stu-id="534de-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="534de-255">レベルまたはアプリケーションのシナリオに必要な複数のオブジェクトの配置場所を解決するときに最初に、領域に含まれる確率を最大化するための順序で欠かせないと大きなオブジェクトを解決します。</span><span class="sxs-lookup"><span data-stu-id="534de-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="534de-256">配置の順序が重要です。</span><span class="sxs-lookup"><span data-stu-id="534de-256">Placement order is important.</span></span> <span data-ttu-id="534de-257">オブジェクトへの配置が見つからない場合は、あまりに制約付きの構成をお試しください。</span><span class="sxs-lookup"><span data-stu-id="534de-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="534de-258">フォールバック構成のセットは、ルーム構成で多くの機能をサポートしているに不可欠です。</span><span class="sxs-lookup"><span data-stu-id="534de-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="534de-259">ルームのスキャン プロセス</span><span class="sxs-lookup"><span data-stu-id="534de-259">Room Scanning Process</span></span>

<span data-ttu-id="534de-260">あらゆる問題領域のニーズを満たすのに十分なジェネリック、HoloLens によって提供される空間マッピング ソリューションを設計中に、空間理解モジュールは、2 つの特定のゲームのニーズをサポートするために構築されました。</span><span class="sxs-lookup"><span data-stu-id="534de-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="534de-261">そのソリューションは、特定のプロセスと前提条件、以下の集計のセットを中心に構成されます。</span><span class="sxs-lookup"><span data-stu-id="534de-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="534de-262">ユーザー駆動 playspace「描画」– スキャン フェーズでは、ユーザーが移動し、ペースの再生に関する次の必要があります領域を効果的に描画します。</span><span class="sxs-lookup"><span data-stu-id="534de-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="534de-263">生成したメッシュは、このフェーズ中にユーザーからのフィードバックを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="534de-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="534de-264">屋内ホームまたは office セットアップ – 関数がフラット サーフェスと直角に交わって壁を中心に設計されたクエリ。</span><span class="sxs-lookup"><span data-stu-id="534de-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="534de-265">これは、ソフト制限です。</span><span class="sxs-lookup"><span data-stu-id="534de-265">This is a soft limitation.</span></span> <span data-ttu-id="534de-266">ただし、スキャン フェーズでは、プライマリ軸の分析がメジャーおよびマイナーの軸に沿ったメッシュ テセレーションを最適化するために完了します。</span><span class="sxs-lookup"><span data-stu-id="534de-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="534de-267">インクルード SpatialUnderstanding.cs ファイルは、スキャン フェーズの処理を管理します。</span><span class="sxs-lookup"><span data-stu-id="534de-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="534de-268">次の関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="534de-268">It calls the following functions.</span></span>

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

<span data-ttu-id="534de-269">"SpatialUnderstanding"動作によって、スキャンのフローは、各フレーム InitScan、し UpdateScan を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="534de-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="534de-270">統計情報のクエリが妥当なカバレッジを報告したとき、ユーザーは、スキャン フェーズの終了を示す RequestFinish を呼び出す airtap にできます。</span><span class="sxs-lookup"><span data-stu-id="534de-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="534de-271">UpdateScan の継続が戻り値になるまでに呼び出される値は、dll の処理が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="534de-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="534de-272">Understanding メッシュ</span><span class="sxs-lookup"><span data-stu-id="534de-272">Understanding Mesh</span></span>

<span data-ttu-id="534de-273">Understanding dll は、サイズ 8 cm voxel キューブのグリッドとして、playspace を内部的に格納します。</span><span class="sxs-lookup"><span data-stu-id="534de-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="534de-274">スキャンの初期段階では、部屋の軸を決定する主要なコンポーネントの分析が完了しました。</span><span class="sxs-lookup"><span data-stu-id="534de-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="534de-275">内部的には、これらの軸に配置されたその voxel 領域を格納します。</span><span class="sxs-lookup"><span data-stu-id="534de-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="534de-276">メッシュには、voxel ボリュームからアイソサーフェスを抽出することによって毎秒約が生成されます。</span><span class="sxs-lookup"><span data-stu-id="534de-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="534de-277">![Voxel ボリュームから生成したメッシュが生成されます。](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="534de-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="534de-278">*Voxel ボリュームから生成したメッシュが生成されます。*</span><span class="sxs-lookup"><span data-stu-id="534de-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="534de-279">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="534de-279">Troubleshooting</span></span>
* <span data-ttu-id="534de-280">設定することを確認、 [SpatialPerception](#setting-the-spatialperception-capability)機能</span><span class="sxs-lookup"><span data-stu-id="534de-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="534de-281">追跡が失われると、次の OnSurfaceChanged イベントはすべてのメッシュを削除します。</span><span class="sxs-lookup"><span data-stu-id="534de-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="534de-282">Mixed Reality toolkit 空間マッピング</span><span class="sxs-lookup"><span data-stu-id="534de-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="534de-283">空間マッピングを使用して、Mixed Reality Toolkit v2 での詳細については、次を参照してください。、<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">空間認識セクション</a>MRTK docs の。</span><span class="sxs-lookup"><span data-stu-id="534de-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="534de-284">関連項目</span><span class="sxs-lookup"><span data-stu-id="534de-284">See also</span></span>
* [<span data-ttu-id="534de-285">MR 空間 230:空間マッピング</span><span class="sxs-lookup"><span data-stu-id="534de-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="534de-286">座標系</span><span class="sxs-lookup"><span data-stu-id="534de-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="534de-287">Unity の座標系</span><span class="sxs-lookup"><span data-stu-id="534de-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="534de-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="534de-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="534de-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="534de-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="534de-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="534de-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="534de-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span><span class="sxs-lookup"><span data-stu-id="534de-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
