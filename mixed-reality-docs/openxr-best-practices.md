---
title: OpenXR のベストプラクティス
description: OpenXR アプリケーションのビジュアル品質、安定性、およびパフォーマンスに関するベストプラクティスについて説明します。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア、ベストプラクティス、パフォーマンス、品質、安定性
ms.openlocfilehash: c0ddbd0604760ccae34d347e93b918be4aead269
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362023"
---
# <a name="openxr-app-best-practices"></a><span data-ttu-id="3144b-104">OpenXR アプリのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="3144b-104">OpenXR app best practices</span></span>

<span data-ttu-id="3144b-105">以下のベストプラクティスの例については、 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>の OpenXRProgram ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3144b-105">You can see an example of the best practices below in <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>'s OpenXRProgram.cpp file.</span></span> <span data-ttu-id="3144b-106">最初の Run () 関数は、初期化からイベントおよびレンダリングループへの一般的な OpenXR app コードフローをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="3144b-106">The Run() function at the beginning captures a typical OpenXR app code flow from initialization to the event and rendering loop.</span></span>

## <a name="best-practices-for-visual-quality-and-stability"></a><span data-ttu-id="3144b-107">ビジュアルの品質と安定性に関するベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="3144b-107">Best practices for visual quality and stability</span></span>

<span data-ttu-id="3144b-108">このセクションのベストプラクティスでは、OpenXR アプリケーションで最高の画質と安定性を実現する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3144b-108">The best practices in this section describe how to get the best visual quality and stability in any OpenXR application.</span></span>

<span data-ttu-id="3144b-109">HoloLens 2 に固有のパフォーマンスの推奨事項については、後述の「 [hololens 2 のパフォーマンスに関するベストプラクティス](#best-practices-for-performance-on-hololens-2)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3144b-109">For further performance recommendations specific to HoloLens 2, see the [Best practices for performance on HoloLens 2](#best-practices-for-performance-on-hololens-2) section below.</span></span>

### <a name="gamma-correct-rendering"></a><span data-ttu-id="3144b-110">ガンマ-正しいレンダリング</span><span class="sxs-lookup"><span data-stu-id="3144b-110">Gamma-correct rendering</span></span>

<span data-ttu-id="3144b-111">レンダリングパイプラインのガンマが正しいことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3144b-111">Care must be taken to ensure that your rendering pipeline is gamma-correct.</span></span> <span data-ttu-id="3144b-112">スワップチェーンにレンダリングする場合、レンダーターゲットビュー形式は、スワップチェーン形式 (スワップチェーン形式とレンダーターゲットビューの両方の DXGI_FORMAT_B8G8R8A8_UNORM_SRGB など) と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3144b-112">When rendering to a swapchain, the render-target view format should match the swapchain format (e.g. DXGI_FORMAT_B8G8R8A8_UNORM_SRGB for both the swapchain format and the render-target view).</span></span>
<span data-ttu-id="3144b-113">例外は、アプリのレンダリングパイプラインがシェーダーコードで手動の sRGB 変換を行う場合です。この場合、アプリでは、sRGB スワップチェーン形式を要求しますが、レンダリングターゲットビューには線形形式を使用します (たとえば、要求 DXGI_FORMAT_B8G8R8A8_UNORM_SRGB をコンテンツがダブルガンマ補正されないようにするために、DXGI_FORMAT_B8G8R8A8_UNORM をレンダーターゲットビューとして使用します)。</span><span class="sxs-lookup"><span data-stu-id="3144b-113">The exception is if the app's rendering pipeline does a manual sRGB conversion in shader code, in which case the app should request an sRGB swapchain format but use the linear format for the render-target view (e.g. request DXGI_FORMAT_B8G8R8A8_UNORM_SRGB as the swapchain format but use DXGI_FORMAT_B8G8R8A8_UNORM as the render-target view) to prevent content from being double-gamma corrected.</span></span>

### <a name="submit-depth-buffer-for-projection-layers"></a><span data-ttu-id="3144b-114">プロジェクションレイヤーの深度バッファーを送信します</span><span class="sxs-lookup"><span data-stu-id="3144b-114">Submit depth buffer for projection layers</span></span>

<span data-ttu-id="3144b-115">`xrEndFrame`にフレームを送信する場合は、常に `XR_KHR_composition_layer_depth` 拡張機能を使用し、深度バッファーを投影レイヤーと一緒に送信します。</span><span class="sxs-lookup"><span data-stu-id="3144b-115">Always use `XR_KHR_composition_layer_depth` extension and submit the depth buffer together with the projection layer when submitting a frame to `xrEndFrame`.</span></span>
<span data-ttu-id="3144b-116">これにより、HoloLens 2 でハードウェアの深さの再投影を有効にすることで、ホログラムの安定性が向上します。</span><span class="sxs-lookup"><span data-stu-id="3144b-116">This improves hologram stability by enabling hardware depth reprojection on HoloLens 2.</span></span>

### <a name="choose-a-reasonable-depth-range"></a><span data-ttu-id="3144b-117">適切な深さの範囲を選択してください</span><span class="sxs-lookup"><span data-stu-id="3144b-117">Choose a reasonable depth range</span></span>

<span data-ttu-id="3144b-118">HoloLens でのホログラムの安定性を向上させるために、より狭い深さの範囲を使用して仮想コンテンツの範囲を絞り込みます。</span><span class="sxs-lookup"><span data-stu-id="3144b-118">Prefer a narrower depth range to scope the virtual content to help hologram stability on HoloLens.</span></span>
<span data-ttu-id="3144b-119">たとえば、OpenXrProgram サンプルでは、0.1 ~ 20 メートルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="3144b-119">For example, the OpenXrProgram.cpp sample is using 0.1 to 20 meters.</span></span>
<span data-ttu-id="3144b-120">より一貫した深さの解決には、[逆順-Z](https://developer.nvidia.com/content/depth-precision-visualized)を使用します。</span><span class="sxs-lookup"><span data-stu-id="3144b-120">Use [reversed-Z](https://developer.nvidia.com/content/depth-precision-visualized) for a more uniform depth resolution.</span></span>
<span data-ttu-id="3144b-121">HoloLens 2 では、推奨される `DXGI_FORMAT_D16_UNORM` 深度形式を使用すると、フレームレートとパフォーマンスが向上します。ただし、16ビット深度バッファーでは、24ビット深度バッファーよりも深さの解像度が低くなります。</span><span class="sxs-lookup"><span data-stu-id="3144b-121">Note that, on HoloLens 2, using the preferred `DXGI_FORMAT_D16_UNORM` depth format will help achieve better frame rate and performance, although 16-bit depth buffers provide less depth resolution than 24-bit depth buffers.</span></span>
<span data-ttu-id="3144b-122">そのため、これらのベストプラクティスに従って、その深さの解決を最大限に活用することが重要になります。</span><span class="sxs-lookup"><span data-stu-id="3144b-122">Therefore, following these best practices to make best use of the depth resolution becomes more important.</span></span>

### <a name="prepare-for-different-environment-blend-modes"></a><span data-ttu-id="3144b-123">さまざまな環境の blend モードを準備する</span><span class="sxs-lookup"><span data-stu-id="3144b-123">Prepare for different environment blend modes</span></span>

<span data-ttu-id="3144b-124">また、世界を完全にブロックするイマーシブヘッドセットでアプリケーションを実行する場合は、`xrEnumerateEnvironmentBlendModes` API を使用してサポートされている環境の blend モードを列挙し、それに応じてレンダリングコンテンツを準備してください。</span><span class="sxs-lookup"><span data-stu-id="3144b-124">If your application will also run on immersive headsets that completely block out the world, be sure to enumerate supported environment blend modes using `xrEnumerateEnvironmentBlendModes` API, and prepare your rendering content accordingly.</span></span>
<span data-ttu-id="3144b-125">たとえば、HoloLens などの `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` を搭載したシステムの場合、アプリでは透明色として透明を使用する必要があります。一方、`XR_ENVIRONMENT_BLEND_MODE_OPAQUE`のシステムの場合、アプリは不透明色または一部の仮想ルームをバックグラウンドでレンダリングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3144b-125">For example, for a system with `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` such as the HoloLens, the app should use transparent as the clear color, while for a system with `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`, the app should render some opaque color or some virtual room in the background.</span></span>

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a><span data-ttu-id="3144b-126">アプリケーションのルート領域として非バインド参照スペースを選択する</span><span class="sxs-lookup"><span data-stu-id="3144b-126">Choose unbounded reference space as application's root space</span></span>

<span data-ttu-id="3144b-127">通常、アプリケーションは、ビュー、アクション、およびホログラムを連結するために、いくつかのルートワールド座標空間を確立します。</span><span class="sxs-lookup"><span data-stu-id="3144b-127">Applications typically establish some root world coordinate space to connect views, actions and holograms together.</span></span>
<span data-ttu-id="3144b-128">拡張機能を使用して[世界規模の座標系](coordinate-systems.md#building-a-world-scale-experience)を確立することがサポートされている場合は `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` を使用します。これにより、アプリの開始位置からユーザーが遠く (たとえば、5メートル離れた場所) に移動したときに望ましくないホログラムのずれが発生するのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="3144b-128">Use `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` when the extension is supported to establish a [world-scale coordinate system](coordinate-systems.md#building-a-world-scale-experience), enabling your app to avoid undesired hologram drift when the user moves far (e.g. 5 meters away) from where the app starts.</span></span>
<span data-ttu-id="3144b-129">非バインド領域の拡張機能が存在しない場合は、フォールバックとして `XR_REFERENCE_SPACE_TYPE_LOCAL` を使用します。</span><span class="sxs-lookup"><span data-stu-id="3144b-129">Use `XR_REFERENCE_SPACE_TYPE_LOCAL` as a fallback if the unbounded space extension doesn't exist.</span></span>

### <a name="associate-hologram-with-spatial-anchor"></a><span data-ttu-id="3144b-130">ホログラムを空間アンカーに関連付ける</span><span class="sxs-lookup"><span data-stu-id="3144b-130">Associate hologram with spatial anchor</span></span>

<span data-ttu-id="3144b-131">バインドされていない参照空間を使用する場合、その参照空間に直接配置したホログラムは、遠くの部屋に移動した後に戻ったときに、[ずれを生じる可能性があり](coordinate-systems.md#building-a-world-scale-experience)ます。</span><span class="sxs-lookup"><span data-stu-id="3144b-131">When using an unbounded reference space, holograms you place directly in that reference space [may drift as the user walks to distant rooms and then comes back](coordinate-systems.md#building-a-world-scale-experience).</span></span>
<span data-ttu-id="3144b-132">ホログラムユーザーが世界中の個別の場所に配置されるようにするには、`xrCreateSpatialAnchorSpaceMSFT` 拡張機能を使用して[空間アンカーを作成](spatial-anchors.md#best-practices)し、その原点にホログラムを配置します。</span><span class="sxs-lookup"><span data-stu-id="3144b-132">For hologram users place at a discrete location in the world, [create a spatial anchor](spatial-anchors.md#best-practices) using the `xrCreateSpatialAnchorSpaceMSFT` extension function and position the hologram at its origin.</span></span>
<span data-ttu-id="3144b-133">これにより、そのホログラムは時間の経過と共に個別に安定した状態に保たれます</span><span class="sxs-lookup"><span data-stu-id="3144b-133">That will keep that hologram independently stable over time.</span></span>

### <a name="support-mixed-reality-capture"></a><span data-ttu-id="3144b-134">混合現実のキャプチャをサポートする</span><span class="sxs-lookup"><span data-stu-id="3144b-134">Support mixed reality capture</span></span>

<span data-ttu-id="3144b-135">HoloLens 2 のプライマリディスプレイは加法の環境ブレンドを使用しますが、ユーザーが[mixed reality キャプチャ](mixed-reality-capture-for-developers.md)を開始すると、アプリのレンダリングコンテンツは環境のビデオストリームとアルファブレンドされます。</span><span class="sxs-lookup"><span data-stu-id="3144b-135">Although HoloLens 2's primary display uses additive environment blending, when the user initiates [mixed reality capture](mixed-reality-capture-for-developers.md), the app's rendering content will be alpha-blended with the environment video stream.</span></span>
<span data-ttu-id="3144b-136">Mixed reality のキャプチャビデオで最高の画質を実現するには、投影レイヤーの `layerFlags`に `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` を設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3144b-136">To achieve the best visual quality in mixed reality capture videos, it's best to set the `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` in your projection layer's `layerFlags`.</span></span>

## <a name="best-practices-for-performance-on-hololens-2"></a><span data-ttu-id="3144b-137">HoloLens 2 でのパフォーマンスに関するベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="3144b-137">Best practices for performance on HoloLens 2</span></span>

<span data-ttu-id="3144b-138">ハードウェアの再プロジェクションをサポートするモバイルデバイスとして、HoloLens 2 には最適なパフォーマンスを得るための厳しい要件があります。</span><span class="sxs-lookup"><span data-stu-id="3144b-138">As a mobile device with hardware reprojection support, HoloLens 2 has stricter requirements to obtain optimal performance.</span></span>  <span data-ttu-id="3144b-139">`xrEndFrame` を使用してコンポジションデータを送信する方法は多数あります。その結果、パフォーマンスが大幅に低下する後処理が発生します。</span><span class="sxs-lookup"><span data-stu-id="3144b-139">There are a number of ways to submit composition data through `xrEndFrame` which will result in post-processing that will have a noticeable performance penalty.</span></span>

### <a name="select-a-swapchain-format"></a><span data-ttu-id="3144b-140">スワップチェーン形式を選択してください</span><span class="sxs-lookup"><span data-stu-id="3144b-140">Select a swapchain format</span></span>

<span data-ttu-id="3144b-141">常に `xrEnumerateSwapchainFormats`を使用してサポートされているピクセル形式を列挙し、アプリがサポートするランタイムから最初の色と深度のピクセル形式を選択します。これは、最適なパフォーマンスのためにランタイムが推奨するものであるためです。</span><span class="sxs-lookup"><span data-stu-id="3144b-141">Always enumerate supported pixel formats using `xrEnumerateSwapchainFormats`, and choose the first color and depth pixel format from the runtime that the app supports, because that's what the runtime prefers for optimal performance.</span></span> <span data-ttu-id="3144b-142">HoloLens 2 では、通常、レンダリングのパフォーマンスを向上させるために、`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` と `DXGI_FORMAT_D16_UNORM` が最初に選択されます。</span><span class="sxs-lookup"><span data-stu-id="3144b-142">Note, on HoloLens 2, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` and `DXGI_FORMAT_D16_UNORM` is typically the first choice to achieve better rendering performance.</span></span> <span data-ttu-id="3144b-143">この設定は、デスクトップ PC で実行されている VR ヘッドセットでは異なっていてもかまいません。24ビットの深度バッファーでは、パフォーマンスへの影響が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="3144b-143">This preference can be different on VR headsets running on a Desktop PC, where 24-bit depth buffers have less of a performance impact.</span></span>
  
<span data-ttu-id="3144b-144">**パフォーマンスの警告:** プライマリスワップチェーンカラー形式以外の形式を使用すると、パフォーマンスが大幅に低下するランタイム後処理が発生します。</span><span class="sxs-lookup"><span data-stu-id="3144b-144">**Performance Warning:** Using a format other than the primary swapchain color format will result in runtime post-processing which comes at a significant performance penalty.</span></span>

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a><span data-ttu-id="3144b-145">推奨されるレンダリングパラメーターとフレームタイミングを使用したレンダリング</span><span class="sxs-lookup"><span data-stu-id="3144b-145">Render with recommended rendering parameters and frame timing</span></span>

<span data-ttu-id="3144b-146">常に、推奨されるビュー構成の幅/高さ (`recommendedImageRectWidth` と `recommendedImageRectHeight` `XrViewConfigurationView`) でレンダリングします。また、表示する前に、常に `xrLocateViews` API を使用して、推奨されるビューの設定、視界、およびその他のレンダリングパラメーターのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="3144b-146">Always render with the recommended view configuration width/height (`recommendedImageRectWidth` and `recommendedImageRectHeight` from `XrViewConfigurationView`), and always use `xrLocateViews` API to query for the recommended view pose, fov, and other rendering parameters before rendering.</span></span>
<span data-ttu-id="3144b-147">ポーズとビューに対してクエリを実行する場合は、常に最新の `xrWaitFrame` 呼び出しの `XrFrameEndInfo.predictedDisplayTime` を使用します。</span><span class="sxs-lookup"><span data-stu-id="3144b-147">Always use the `XrFrameEndInfo.predictedDisplayTime` from the latest `xrWaitFrame` call when querying for poses and views.</span></span>
<span data-ttu-id="3144b-148">これにより、HoloLens は、HoloLens を装着しているユーザーに対してレンダリングを調整し、視覚品質を最適化することができます。</span><span class="sxs-lookup"><span data-stu-id="3144b-148">This allows HoloLens to adjust rendering and optimize visual quality for the person who is wearing the HoloLens.</span></span>

### <a name="use-a-single-projection-layer"></a><span data-ttu-id="3144b-149">1つの投影レイヤーを使用する</span><span class="sxs-lookup"><span data-stu-id="3144b-149">Use a single projection layer</span></span>

<span data-ttu-id="3144b-150">HoloLens 2 では、アプリケーションがコンテンツをレンダリングするための GPU 機能が制限されており、単一の投影レイヤー用に最適化されたハードウェアコンポジターが使用されています。</span><span class="sxs-lookup"><span data-stu-id="3144b-150">HoloLens 2 has limited GPU power for applications to render content and a hardware compositor optimized for a single projection layer.</span></span>
<span data-ttu-id="3144b-151">常に1つの投影レイヤーを使用すると、アプリケーションのフレームレート、ホログラムの安定性、およびビジュアルの品質を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="3144b-151">Always using a single projection layer can help the application's framerate, hologram stability and visual quality.</span></span>  
  
<span data-ttu-id="3144b-152">**パフォーマンスの警告:** 1つの保護レイヤーだけを送信すると、パフォーマンスが大幅に低下するランタイム後処理が発生します。</span><span class="sxs-lookup"><span data-stu-id="3144b-152">**Performance Warning:** Submitting anything but a single protection layer will result in runtime post-processing which comes at a significant performance penalty.</span></span>

### <a name="render-with-texture-array-and-vprt"></a><span data-ttu-id="3144b-153">テクスチャ配列と VPRT を使用したレンダリング</span><span class="sxs-lookup"><span data-stu-id="3144b-153">Render with texture array and VPRT</span></span>

<span data-ttu-id="3144b-154">`arraySize=2` を使用して、色スワップチェーンに対して1つの `xrSwapchain` を作成し、1つを深さに対して作成します。</span><span class="sxs-lookup"><span data-stu-id="3144b-154">Create one `xrSwapchain` for both left and right eye using `arraySize=2` for color swapchain, and one for depth.</span></span>
<span data-ttu-id="3144b-155">スライス0に左側を表示し、スライス1に目を入れます。</span><span class="sxs-lookup"><span data-stu-id="3144b-155">Render the left eye into slice 0 and the right eye into slice 1.</span></span>
<span data-ttu-id="3144b-156">VPRT のシェーダーとインスタンス化された描画呼び出しのステレオスコピックレンダリングを使用して、GPU の負荷を最小限に抑えます。</span><span class="sxs-lookup"><span data-stu-id="3144b-156">Use a shader with VPRT and instanced draw calls for stereoscopic rendering to minimize GPU load.</span></span>
<span data-ttu-id="3144b-157">これにより、ランタイムの最適化によって HoloLens 2 で最高のパフォーマンスを実現できます。</span><span class="sxs-lookup"><span data-stu-id="3144b-157">This also enables the runtime's optimization to achieve the best performance on HoloLens 2.</span></span>
<span data-ttu-id="3144b-158">2つのテクスチャ配列を使用する代わりに、2倍のレンダリングや個別のスワップチェーンなどを使用する代わりに、パフォーマンスが大幅に低下するランタイム後処理が発生します。</span><span class="sxs-lookup"><span data-stu-id="3144b-158">Alternatives to using a texture array, such as double-wide rendering or a separate swapchain per eye, will result in runtime post-processing which comes at a significant performance penalty.</span></span>

### <a name="avoid-quad-layers"></a><span data-ttu-id="3144b-159">クワッドレイヤーを避ける</span><span class="sxs-lookup"><span data-stu-id="3144b-159">Avoid quad layers</span></span>

<span data-ttu-id="3144b-160">`XrCompositionLayerQuad`を使用して構成レイヤーとしてクワッドレイヤーを送信するのではなく、クワッドコンテンツを射影 swapchain に直接レンダリングします。</span><span class="sxs-lookup"><span data-stu-id="3144b-160">Rather than submitting quad layers as composition layers with `XrCompositionLayerQuad`, render the quad content directly into the projection swapchain.</span></span>

<span data-ttu-id="3144b-161">**パフォーマンスの警告:** クワッドレイヤーなど、1つの投影レイヤーを超えて追加のレイヤーを提供すると、パフォーマンスが大幅に低下するランタイム後処理が発生します。</span><span class="sxs-lookup"><span data-stu-id="3144b-161">**Performance Warning:** Providing additional layers beyond a single projection layer, such as quad layers, will result in runtime post-processing which comes at a significant performance penalty.</span></span>