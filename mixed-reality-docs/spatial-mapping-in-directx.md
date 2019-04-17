---
title: DirectX での空間のマッピング
description: DirectX アプリで空間マッピングを実装する方法について説明します。 これには、ユニバーサル Windows プラットフォーム SDK に含まれている空間マッピングのサンプル アプリケーションの詳細な説明が含まれます。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: 実際には、空間マッピング、環境、相互作用、directx、winrt、api、サンプルのコードを混在 Windows UWP, SDK, チュートリアル
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605138"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="9bb4a-105">DirectX での空間のマッピング</span><span class="sxs-lookup"><span data-stu-id="9bb4a-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="9bb4a-106">このトピックでは、実装する方法を説明します[空間マッピング](spatial-mapping.md)DirectX アプリでします。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="9bb4a-107">これには、ユニバーサル Windows プラットフォーム SDK に含まれている空間マッピングのサンプル アプリケーションの詳細な説明が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="9bb4a-108">このトピックではコードを使用、 [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP のコード サンプル。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="9bb4a-109">この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="9bb4a-110">概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="9bb4a-111">DirectX の開発の概要</span><span class="sxs-lookup"><span data-stu-id="9bb4a-111">DirectX development overview</span></span>

<span data-ttu-id="9bb4a-112">空間マッピング用のネイティブ アプリケーションの開発は、Api を使用して、 [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)名前空間。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="9bb4a-113">これらの Api は空間マッピングによって公開される Api を直接と同様の方法では、空間マッピング機能のフル コントロールを提供[Unity](spatial-mapping-in-unity.md)します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="9bb4a-114">認識 Api</span><span class="sxs-lookup"><span data-stu-id="9bb4a-114">Perception APIs</span></span>

<span data-ttu-id="9bb4a-115">空間マッピングの開発用の主な種類は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="9bb4a-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) SpatialSurfaceInfo オブジェクトの形式で、ユーザーの近くの領域のアプリケーションで指定されたリージョンでの画面について説明します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="9bb4a-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)単一既存空間のサーフェス、一意の ID を含む、境界のボリュームと最終変更時刻をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="9bb4a-118">要求時に非同期的の SpatialSurfaceMesh が提供されます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="9bb4a-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) SpatialSurfaceInfo から要求された SpatialSurfaceMesh オブジェクトのカスタマイズに使用されるパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="9bb4a-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)メッシュ データを 1 つの空間サーフェスを表します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="9bb4a-121">頂点の位置、頂点の法線と三角形のインデックスのデータは、メンバー SpatialSurfaceMeshBuffer オブジェクトに含まれます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="9bb4a-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx)メッシュのデータの 1 つの型をラップします。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="9bb4a-123">これらの Api を使用してアプリケーションを開発する場合は、(以下で説明するサンプル アプリケーションで説明します)、このよう基本的なプログラム フローが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="9bb4a-124">**設定する、SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="9bb4a-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="9bb4a-125">呼び出す[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)ユーザーがデバイスの空間のマッピング機能を使用するアプリケーションのアクセス許可を割り当てられているようにしてください。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="9bb4a-126">SpatialSurfaceObserver オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="9bb4a-127">呼び出す[SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx)空間サーフェスに関する情報を挿入するスペースの領域を指定します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="9bb4a-128">もう一度この関数を呼び出すだけで、将来これらのリージョンを変更することがあります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="9bb4a-129">使用して各リージョンを指定する[SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="9bb4a-130">登録、 [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx)イベントで、新しい情報が指定した領域のリージョン内の空間のサーフェスについて利用可能なときに起動されます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="9bb4a-131">**ObservedSurfacesChanged イベントを処理します。**</span><span class="sxs-lookup"><span data-stu-id="9bb4a-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="9bb4a-132">イベント ハンドラーで呼び出す[GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) SpatialSurfaceInfo オブジェクトのマップを受信します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="9bb4a-133">このマップを使用して、空間サーフェスのレコードを更新することができます[、ユーザーの環境に存在](spatial-mapping.md#mesh-caching)します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="9bb4a-134">照会することがあります、SpatialSurfaceInfo オブジェクトごとに[TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx)で表される、サーフェイス上の空間のエクステントを判断する、[空間座標系](coordinate-systems.md)独自の。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="9bb4a-135">空間画面用のメッシュを要求する場合は、呼び出す[TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="9bb4a-136">三角形の目的、密度とメッシュが返されるデータの形式を指定するオプションを指定することがあります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="9bb4a-137">**受信および処理メッシュ**</span><span class="sxs-lookup"><span data-stu-id="9bb4a-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="9bb4a-138">TryComputeLatestMeshAsync は aysnchronously に対する各呼び出しは、1 つの SpatialSurfaceMesh オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="9bb4a-139">このオブジェクトから三角形のインデックス、頂点の位置にアクセスするには含まれている SpatialSurfaceMeshBuffer オブジェクトにアクセスすることができます (要求) 場合、メッシュの頂点の法線。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="9bb4a-140">このデータは直接互換性のある形式になります、 [direct3d11 の Api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx)メッシュの描画に使用します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="9bb4a-141">ここから、アプリケーションは必要に応じて分析を実行または[処理](spatial-mapping.md#mesh-processing)メッシュのデータの使用と[レンダリング](spatial-mapping.md#rendering)と物理法則[レイキャストと衝突](spatial-mapping.md#raycasting-and-collision)。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="9bb4a-142">注意する 1 つの重要な詳細は、(たとえば、メッシュをレンダリングするために使用される頂点シェーダー) にメッシュの頂点の位置に、スケールを適用する必要があります、それらが格納されている、バッファー内に最適化された整数単位からそれらを変換するための新旧従量課金のことです。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="9bb4a-143">このスケールを取得するには呼び出すことによって[VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="9bb4a-144">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9bb4a-144">Troubleshooting</span></span>
* <span data-ttu-id="9bb4a-145">によって返されるスケールを使用して、頂点シェーダーでメッシュの頂点の位置をスケールすることを忘れないでください[SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="9bb4a-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="9bb4a-146">空間マッピングのコード サンプルのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="9bb4a-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="9bb4a-147">[Holographic 空間マッピング](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)コード サンプルには、管理するためのインフラストラクチャを含む、アプリへの表面メッシュの読み込みを開始する際し、レンダリング サーフェイス メッシュ コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="9bb4a-148">次に、DirectX アプリに画面のマップ機能を追加する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="9bb4a-149">このコードを追加することができます、[アプリ テンプレートを Windows Holographic](creating-a-holographic-directx-project.md)上記で説明したコード サンプルを参照して、プロジェクト、またはするに従うことができます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="9bb4a-150">このコード サンプルは、Windows Holographic のアプリ テンプレートに基づきます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="9bb4a-151">SpatialPerception 機能を使用するアプリをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="9bb4a-152">アプリは、空間のマッピング機能を使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="9bb4a-153">これは、機能は、空間メッシュ プライベート データを検討できるユーザーの環境の表現であるため、必要です。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="9bb4a-154">アプリの package.appxmanifest ファイルでこの機能を宣言します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="9bb4a-155">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="9bb4a-156">機能に由来します**uap2**名前空間。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="9bb4a-157">マニフェストでこの名前空間へのアクセスを取得するには、それを含める、 *xlmns*属性、&lt;パッケージ > 要素。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="9bb4a-158">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="9bb4a-159">空間マッピング機能のサポートを確認します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="9bb4a-160">Windows Mixed Reality は、さまざまな空間マッピングがサポートされていないデバイスを含め、デバイスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="9bb4a-161">アプリは、空間のマッピングを使用することができますまたは機能を提供する空間のマッピングを使用する必要があります、これを使用する前に、空間マッピングがサポートされているかどうかを確認ください。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="9bb4a-162">たとえば、空間マッピングは、mixed reality アプリで必要な場合メッセージが表示、それに対応するユーザーは、空間のマッピングがないデバイスで実行しようとするとします。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="9bb4a-163">または、アプリがユーザーの環境では、空間マッピングが使用可能な場合に何が起こるようなエクスペリエンスを提供する代わりに、独自の仮想環境を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="9bb4a-164">いずれの場合も、この API といない空間マッピング データを取得し、適切な方法で応答を認識するため、アプリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="9bb4a-165">空間マッピング サポートを現在のデバイスを確認するには、最初に、UWP のコントラクトは、4 以上のレベルで確認してから SpatialSurfaceObserver::IsSupported() を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="9bb4a-166">コンテキストで実行するには、 [Holographic 空間マッピング](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)コード サンプル。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="9bb4a-167">サポートは、アクセスを要求する前にチェックされます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="9bb4a-168">SpatialSurfaceObserver::IsSupported() API では、SDK バージョン 15063 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="9bb4a-169">必要に応じて、この API を使用する前にプラットフォームのバージョン 15063 プロジェクトの再ターゲットします。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

<span data-ttu-id="9bb4a-170">ある UWP コントラクトがレベル 4 より小さい場合は、アプリを続行する、デバイスは空間マッピング処理を実行できるように注意してください。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="9bb4a-171">空間マッピング データへのアクセスを要求します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="9bb4a-172">アプリは、任意の画面のオブザーバーを作成する前に、空間マッピングのデータにアクセスする許可を要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="9bb4a-173">詳細については後でこのページで提供されると、画面のマッピング コード サンプルに基づく例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a><span data-ttu-id="9bb4a-174">画面のオブザーバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-174">Create a surface observer</span></span>

<span data-ttu-id="9bb4a-175">**Windows::Perception::Spatial::Surfaces**名前空間が含まれています、 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)クラスで指定した 1 つまたは複数のボリュームの監視、 [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="9bb4a-176">使用して、 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)なる表面メッシュをリアルタイムでデータにアクセスするインスタンス。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="9bb4a-177">**AppMain.h**:</span><span class="sxs-lookup"><span data-stu-id="9bb4a-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="9bb4a-178">前述の前のセクションは、アプリで使用できる前に、空間マッピング データへのアクセスを要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="9bb4a-179">このアクセスは、HoloLens で自動的に付与されます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-179">This access is granted automatically on the HoloLens.</span></span>

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

<span data-ttu-id="9bb4a-180">次に、境界の特定のボリュームを観察する表面のオブザーバーを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="9bb4a-181">ここでは、20 x 20 x 5 メーター、座標系の原点を中心とするボックスを確認します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

<span data-ttu-id="9bb4a-182">複数の外接するボリュームを代わりに設定できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="9bb4a-183">*これは、擬似コードです。*</span><span class="sxs-lookup"><span data-stu-id="9bb4a-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="9bb4a-184">ビューの視錐台などの他の外接する図形を使用することもまたはは軸ではない境界ボックスが配置されます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="9bb4a-185">*これは、擬似コードです。*</span><span class="sxs-lookup"><span data-stu-id="9bb4a-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="9bb4a-186">場合に応答するコードを記述することができますが異なる方法で何も行うサーフェスのマッピング データが利用できない場合、アプリが必要な場合で、 [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx)でない**許可**- たとえば、できなく Pc で没入型のデバイスをそれらのデバイスは空間マッピングのハードウェアがあるないため、接続されているとします。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="9bb4a-187">これらのデバイスの代わりに、空間ステージについては、ユーザーの環境とデバイスの構成に依存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="9bb4a-188">初期化し、なる表面メッシュ コレクションの更新</span><span class="sxs-lookup"><span data-stu-id="9bb4a-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="9bb4a-189">Surface のオブザーバーが正常に作成すると場合、は、表面メッシュ コレクションを初期化するために進むことができます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="9bb4a-190">ここでは、監視対象のサーフェスの現在のセットをすぐに取得するのに、プル モデルの API を使用します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

<span data-ttu-id="9bb4a-191">表面メッシュのデータの取得に使用可能なプッシュ モデルもあります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="9bb4a-192">自由にアプリを設計する場合をポーリングするデータを頻繁に、選択した場合、プル モデルのみを使用すると答えると、または特定の期間中に、フレームごとに 1 回など、ゲームのセットアップ中にします。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="9bb4a-193">そうである場合、上記のコードは必要なものには。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="9bb4a-194">コード サンプルでは、教育目的では、両方のモデルの使用を示すために選択しました。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="9bb4a-195">ここでは、システムは、変更を認識するたびに、表面メッシュを最新の状態データを受信するイベントに定期受信します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="9bb4a-196">コード サンプルは、これらのイベントに応答することも構成されます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="9bb4a-197">その方法を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="9bb4a-198">**注:** これによって、メッシュのデータを処理するアプリの最も効率的な方法ができない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="9bb4a-199">このコードでは、わかりやすくするためが書き込まれ、最適化されていません。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="9bb4a-200">読み取り専用マップを格納する表面メッシュのデータが提供される[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)オブジェクトを使用して[Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx)キー値として。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="9bb4a-201">このデータを処理するには、コレクション内ではないキー値の最初の項目について説明します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="9bb4a-202">このサンプル アプリでデータを格納する方法の詳細については、このトピックの「表示されます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

<span data-ttu-id="9bb4a-203">また、表面メッシュ、表面メッシュ コレクション内にあるが、今後のシステム コレクションにないを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="9bb4a-204">これを行うにはここで紹介を追加すると、メッシュ; の更新の反対のようなもの必要があります。アプリのコレクションを確認する場合にループ処理、 **Guid**があるがシステム コレクション内にします。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="9bb4a-205">システム コレクションにない場合は都合から削除します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="9bb4a-206">AppMain.cpp でイベント ハンドラー: から</span><span class="sxs-lookup"><span data-stu-id="9bb4a-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="9bb4a-207">RealtimeSurfaceMeshRenderer.cpp でメッシュの排除の実装:</span><span class="sxs-lookup"><span data-stu-id="9bb4a-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="9bb4a-208">取得し、なる表面メッシュ データ バッファーの使用</span><span class="sxs-lookup"><span data-stu-id="9bb4a-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="9bb4a-209">表面メッシュ情報を取得することは、データ コレクションを取得し、そのコレクションの更新の処理と同じくらい簡単でした。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="9bb4a-210">ここで詳しく説明します詳細データを使用する方法。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="9bb4a-211">このコード例では、レンダリングの表面メッシュを使用する選択しました。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="9bb4a-212">これは、現実世界のサーフェスの背後にあるホログラムが他の一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="9bb4a-213">メッシュをレンダリングまたは処理されたバージョンを表示できますが、ルームがのどの領域をユーザーに表示するアプリやゲームの機能の提供を開始する前にスキャンされます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="9bb4a-214">コード サンプルは、前のセクションで説明したイベント ハンドラーからなる表面メッシュの更新プログラムを受信したときに、プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="9bb4a-215">この関数のコードの重要な行は、サーフェイスを更新する呼び出し*メッシュ*: この時点までが既に処理されたメッシュの情報とに応じて、使用するため、頂点とインデックスのデータを取得しようとしています。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="9bb4a-216">RealtimeSurfaceMeshRenderer.cpp: から</span><span class="sxs-lookup"><span data-stu-id="9bb4a-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

<span data-ttu-id="9bb4a-217">サンプル コードが設計されていますように、データ クラス**SurfaceMesh**、ハンドル メッシュのデータ処理および表示します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="9bb4a-218">これらのメッシュはどのような**RealtimeSurfaceMeshRenderer**のマップを実際に保持します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="9bb4a-219">1 つずつは送信元 SpatialSurfaceMesh への参照を備え、メッシュの頂点またはインデックス バッファーにアクセスしたり、メッシュの変換を取得する必要がある任意の時間を使用します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="9bb4a-220">ここで、更新プログラムを必要とすると、メッシュをフラグです。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="9bb4a-221">SurfaceMesh.cpp: から</span><span class="sxs-lookup"><span data-stu-id="9bb4a-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="9bb4a-222">次回、メッシュが自身を描画するように求めは、フラグまず確認します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="9bb4a-223">更新プログラムが必要な場合は、GPU で頂点とインデックス バッファーが更新されます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

<span data-ttu-id="9bb4a-224">最初に、生データ バッファーを取得します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="9bb4a-225">次に、Direct3D デバイス バッファーを作成、HoloLens によって提供されるメッシュ データ。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

<span data-ttu-id="9bb4a-226">**注:** 前のスニペットで使用される、CreateDirectXBuffer ヘルパー関数では、画面のマッピングのコード サンプルを参照してください。SurfaceMesh.cpp、GetDataFromIBuffer.h します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="9bb4a-227">これで、デバイス リソースの作成が完了して、メッシュが読み込まれ、更新プログラムの準備をして、表示すると見なされます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="9bb4a-228">更新し、表面メッシュをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-228">Update and render surface meshes</span></span>

<span data-ttu-id="9bb4a-229">SurfaceMesh クラスでは、特殊化された update 関数があります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="9bb4a-230">各[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)独自の変換を備え、サンプルの現在の座標系を使用する、 **SpatialStationaryReferenceFrame**変換を取得します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="9bb4a-231">GPU 上でモデルの定数バッファーを更新します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-231">Then it updates the model constant buffer on the GPU.</span></span>

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

<span data-ttu-id="9bb4a-232">表面メッシュをレンダリングするときは、ときに、コレクションを表示する前に、いくつかの準備作業を行います。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="9bb4a-233">現在の表示構成のシェーダーのパイプラインを設定し、入力アセンブラー ステージを設定します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="9bb4a-234">なお、holographic カメラ ヘルパー クラス**CameraResources.cpp**  /ビューのプロジェクション定数バッファーをここまでで既に設定が。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="9bb4a-235">**RealtimeSurfaceMeshRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="9bb4a-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

<span data-ttu-id="9bb4a-236">これが完了すると、メッシュにループを自体を描画するために 1 つずつに伝えます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="9bb4a-237">**注:** 何らかの視錐台カリングを使用するこのサンプル コードが最適化されていないが、アプリでこの機能を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

<span data-ttu-id="9bb4a-238">個々 のメッシュは、頂点とインデックス バッファー、stride、およびモデル変換定数バッファーを設定します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="9bb4a-239">同様に、Windows Holographic のアプリケーション テンプレートで回転するキューブ、インスタンス化を使用してステレオスコ ピックのバッファーを表示します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="9bb4a-240">**SurfaceMesh::Draw**:</span><span class="sxs-lookup"><span data-stu-id="9bb4a-240">From **SurfaceMesh::Draw**:</span></span>

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="9bb4a-241">画面のマッピングの選択肢を表示</span><span class="sxs-lookup"><span data-stu-id="9bb4a-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="9bb4a-242">画面のマッピングのコード サンプルには、表面メッシュのデータのレンダリングをオクルー ジョン専用となる表面メッシュのデータの表示が画面に表示されるコードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="9bb4a-243">パスを選ぶかまたは両方がアプリケーションに依存します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="9bb4a-244">このドキュメントで両方の構成を説明します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="9bb4a-245">**Holographic 効果のレンダリング オクルー ジョン バッファー**</span><span class="sxs-lookup"><span data-stu-id="9bb4a-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="9bb4a-246">現在、仮想カメラのレンダー ターゲット ビューをオフにして開始します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="9bb4a-247">AppMain.cpp: から</span><span class="sxs-lookup"><span data-stu-id="9bb4a-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="9bb4a-248">これは、「プリレンダ リング」パスです。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="9bb4a-249">ここでは、深さのみを表示するために、メッシュ レンダラーを要求することによって、オクルー ジョン バッファーを作成します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="9bb4a-250">この構成では、レンダー ターゲット ビューを接続せず、メッシュ レンダラーでは、ピクセル シェーダーのステージを設定**nullptr**ピクセルを描画するために、GPU をわざわざしないようにします。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="9bb4a-251">ジオメトリを深度バッファーにラスタライズして、グラフィックス パイプラインの停止があります。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

<span data-ttu-id="9bb4a-252">ホログラムとオクルー ジョンのマッピングの画面バッファーに対する追加の深度テスト描画できます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="9bb4a-253">このコード サンプルでレンダリング キューブ上のピクセルを別の色、画面の背面にある場合。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="9bb4a-254">AppMain.cpp: から</span><span class="sxs-lookup"><span data-stu-id="9bb4a-254">From AppMain.cpp:</span></span>

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

<span data-ttu-id="9bb4a-255">SpecialEffectPixelShader.hlsl からコードに基づいています。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

<span data-ttu-id="9bb4a-256">**注:** **GatherDepthLess**ルーチン、画面のマッピングのコード サンプルを参照してください。SpecialEffectPixelShader.hlsl します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="9bb4a-257">**表示になる表面メッシュ データのレンダリング**</span><span class="sxs-lookup"><span data-stu-id="9bb4a-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="9bb4a-258">表面メッシュだけでもステレオ表示バッファーに描画できます。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="9bb4a-259">ライティング、完全な面を描画することにしましたが、自由ワイヤー フレームを描画、レンダリングの前にメッシュの処理、テクスチャ マップでは、適用および具合にします。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="9bb4a-260">ここでは、コード サンプルは、コレクションを描画するために、メッシュ レンダラーを指示します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="9bb4a-261">この時間ピクセル シェーダーをアタッチし、現在の仮想のカメラの指定したターゲットを使用してレンダリング パイプラインを完了するため、深さのみのパスの場合を指定しますはありません。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

```cpp
// SR mesh rendering pass: Draw SR mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a><span data-ttu-id="9bb4a-262">関連項目</span><span class="sxs-lookup"><span data-stu-id="9bb4a-262">See also</span></span>
* [<span data-ttu-id="9bb4a-263">Holographic DirectX プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9bb4a-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="9bb4a-264">Windows.Perception.Spatial API</span><span class="sxs-lookup"><span data-stu-id="9bb4a-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
