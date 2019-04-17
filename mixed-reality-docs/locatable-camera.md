---
title: 場所を特定できるカメラ
description: HoloLens の前面に公開されたカメラに関する一般情報。
author: wguyman
ms.author: wguyman
ms.date: 02/24/2019
ms.topic: article
keywords: カメラ、hololens、色のカメラの前面向け
ms.openlocfilehash: ffcd6faf15dd8556db393237d468a3cdf60e4bdb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603621"
---
# <a name="locatable-camera"></a><span data-ttu-id="c0690-104">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="c0690-104">Locatable camera</span></span>

<span data-ttu-id="c0690-105">HoloLens には、アプリをユーザーに表示される内容を参照してください。 有効にするデバイスの前面に取り付け世界に接続されたカメラが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c0690-105">HoloLens includes a world-facing camera mounted on the front of the device which enables apps to see what the user sees.</span></span> <span data-ttu-id="c0690-106">開発者へのアクセスと、カメラのコントロールのスマート フォン、ノートブック、またはデスクトップの色のカメラと同様にあります。</span><span class="sxs-lookup"><span data-stu-id="c0690-106">Developers have access to and control of the camera just as they would for color cameras on smartphones, portables, or desktops.</span></span> <span data-ttu-id="c0690-107">同じユニバーサル windows[メディアのキャプチャ](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)HoloLens では、windows メディア ファンデーション モバイルとデスクトップで機能する Api の動作。</span><span class="sxs-lookup"><span data-stu-id="c0690-107">The same universal windows [media capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) and windows media foundation APIs that work on mobile and desktop work on HoloLens.</span></span> <span data-ttu-id="c0690-108">Unity[がこれらの windows Api をラップしても](locatable-camera-in-unity.md)HoloLens にカメラを正規の写真やビデオ (ホログラムの有無にかかわらず) を取得し、上でのカメラの位置とパースペクティブを検索するなどのタスクの簡単な使用を抽象化するため、シーンです。</span><span class="sxs-lookup"><span data-stu-id="c0690-108">Unity [has also wrapped these windows APIs](locatable-camera-in-unity.md) to abstract simple usage of the camera on HoloLens for tasks such as taking regular photos and videos (with or without holograms) and locating the camera's position in and perspective on the scene.</span></span>

## <a name="device-camera-information"></a><span data-ttu-id="c0690-109">デバイスのカメラの情報</span><span class="sxs-lookup"><span data-stu-id="c0690-109">Device camera information</span></span>

### <a name="hololens-first-generation"></a><span data-ttu-id="c0690-110">HoloLens (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="c0690-110">HoloLens (first-generation)</span></span>

* <span data-ttu-id="c0690-111">固定のフォーカス写真/ビデオ (PV) カメラでは、自動ホワイト バランス、自動公開、および完全なイメージ処理のパイプを使用</span><span class="sxs-lookup"><span data-stu-id="c0690-111">Fixed focus photo/video (PV) camera, with auto white balance, auto exposure, and full image processing pipe</span></span>
* <span data-ttu-id="c0690-112">カメラがアクティブなときに世界が直面しているホワイト プライバシー LED が点灯します。</span><span class="sxs-lookup"><span data-stu-id="c0690-112">White Privacy LED facing the world will illuminate whenever the camera is active</span></span>
* <span data-ttu-id="c0690-113">カメラには、30、24、20、15、および 5 fps で次のモード (すべてのモードはアスペクト比 16:9) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c0690-113">The camera supports the following modes (all modes are 16:9 aspect ratio) at 30, 24, 20, 15, and 5 fps:</span></span>

  |  <span data-ttu-id="c0690-114">Video</span><span class="sxs-lookup"><span data-stu-id="c0690-114">Video</span></span>  |  <span data-ttu-id="c0690-115">[プレビュー]</span><span class="sxs-lookup"><span data-stu-id="c0690-115">Preview</span></span>  |  <span data-ttu-id="c0690-116">それでもなお</span><span class="sxs-lookup"><span data-stu-id="c0690-116">Still</span></span>  |  <span data-ttu-id="c0690-117">水平視野 (FOV H)</span><span class="sxs-lookup"><span data-stu-id="c0690-117">Horizontal Field of View (H-FOV)</span></span> |  <span data-ttu-id="c0690-118">推奨される使用状況</span><span class="sxs-lookup"><span data-stu-id="c0690-118">Suggested usage</span></span> | 
  |----------|----------|----------|----------|----------|
  |  <span data-ttu-id="c0690-119">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="c0690-119">1280x720</span></span> |  <span data-ttu-id="c0690-120">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="c0690-120">1280x720</span></span> |  <span data-ttu-id="c0690-121">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="c0690-121">1280x720</span></span> |  <span data-ttu-id="c0690-122">45deg</span><span class="sxs-lookup"><span data-stu-id="c0690-122">45deg</span></span>  |  <span data-ttu-id="c0690-123">(既定のモードでビデオ安定化)</span><span class="sxs-lookup"><span data-stu-id="c0690-123">(default mode with video stabilization)</span></span> | 
  |  <span data-ttu-id="c0690-124">なし</span><span class="sxs-lookup"><span data-stu-id="c0690-124">N/A</span></span> |  <span data-ttu-id="c0690-125">なし</span><span class="sxs-lookup"><span data-stu-id="c0690-125">N/A</span></span> |  <span data-ttu-id="c0690-126">2048 x 1152</span><span class="sxs-lookup"><span data-stu-id="c0690-126">2048x1152</span></span> |  <span data-ttu-id="c0690-127">67deg</span><span class="sxs-lookup"><span data-stu-id="c0690-127">67deg</span></span> |  <span data-ttu-id="c0690-128">最高の解像度の静止画</span><span class="sxs-lookup"><span data-stu-id="c0690-128">Highest resolution still image</span></span> | 
  |  <span data-ttu-id="c0690-129">1408 x 792</span><span class="sxs-lookup"><span data-stu-id="c0690-129">1408x792</span></span> |  <span data-ttu-id="c0690-130">1408 x 792</span><span class="sxs-lookup"><span data-stu-id="c0690-130">1408x792</span></span> |  <span data-ttu-id="c0690-131">1408 x 792</span><span class="sxs-lookup"><span data-stu-id="c0690-131">1408x792</span></span> |  <span data-ttu-id="c0690-132">48deg</span><span class="sxs-lookup"><span data-stu-id="c0690-132">48deg</span></span> |  <span data-ttu-id="c0690-133">ビデオ安定化する前にオーバー (埋め込み) の解決</span><span class="sxs-lookup"><span data-stu-id="c0690-133">Overscan (padding) resolution before video stabilization</span></span> | 
  |  <span data-ttu-id="c0690-134">1344 x 756</span><span class="sxs-lookup"><span data-stu-id="c0690-134">1344x756</span></span> |  <span data-ttu-id="c0690-135">1344 x 756</span><span class="sxs-lookup"><span data-stu-id="c0690-135">1344x756</span></span> |  <span data-ttu-id="c0690-136">1344 x 756</span><span class="sxs-lookup"><span data-stu-id="c0690-136">1344x756</span></span> |  <span data-ttu-id="c0690-137">67deg</span><span class="sxs-lookup"><span data-stu-id="c0690-137">67deg</span></span> |  <span data-ttu-id="c0690-138">オーバーでの大規模な FOV ビデオ モード</span><span class="sxs-lookup"><span data-stu-id="c0690-138">Large FOV video mode with overscan</span></span> | 
  |  <span data-ttu-id="c0690-139">896 x 504</span><span class="sxs-lookup"><span data-stu-id="c0690-139">896x504</span></span> |  <span data-ttu-id="c0690-140">896 x 504</span><span class="sxs-lookup"><span data-stu-id="c0690-140">896x504</span></span> |  <span data-ttu-id="c0690-141">896 x 504</span><span class="sxs-lookup"><span data-stu-id="c0690-141">896x504</span></span> |  <span data-ttu-id="c0690-142">48deg</span><span class="sxs-lookup"><span data-stu-id="c0690-142">48deg</span></span> |  <span data-ttu-id="c0690-143">低電力]、[イメージの低解像度モード処理タスク</span><span class="sxs-lookup"><span data-stu-id="c0690-143">Low power / Low resolution mode for image processing tasks</span></span> | 

### <a name="hololens-2"></a><span data-ttu-id="c0690-144">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c0690-144">HoloLens 2</span></span>

* <span data-ttu-id="c0690-145">自動フォーカス写真/ビデオ (PV) カメラでは、自動ホワイト バランス、自動公開、および完全なイメージ処理のパイプを使用</span><span class="sxs-lookup"><span data-stu-id="c0690-145">Auto-focus photo/video (PV) camera, with auto white balance, auto exposure, and full image processing pipe</span></span>
* <span data-ttu-id="c0690-146">カメラがアクティブなときに世界が直面しているホワイト プライバシー LED が点灯します。</span><span class="sxs-lookup"><span data-stu-id="c0690-146">White Privacy LED facing the world will illuminate whenever the camera is active</span></span>
* <span data-ttu-id="c0690-147">カメラには、(すべてのビデオ モードはアスペクト比 16:9)、次のモードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c0690-147">The camera supports the following modes (all video modes are 16:9 aspect ratio):</span></span>

  >[!NOTE]
  ><span data-ttu-id="c0690-148">これらのモードは、HoloLens 2 一般公開前に変更される可能性が。</span><span class="sxs-lookup"><span data-stu-id="c0690-148">These modes are subject to change prior to HoloLens 2 general availability.</span></span>

  |  <span data-ttu-id="c0690-149">Video</span><span class="sxs-lookup"><span data-stu-id="c0690-149">Video</span></span>  |  <span data-ttu-id="c0690-150">[プレビュー]</span><span class="sxs-lookup"><span data-stu-id="c0690-150">Preview</span></span>  |  <span data-ttu-id="c0690-151">それでもなお</span><span class="sxs-lookup"><span data-stu-id="c0690-151">Still</span></span>  |  <span data-ttu-id="c0690-152">フレーム レート</span><span class="sxs-lookup"><span data-stu-id="c0690-152">Frame rates</span></span>  |  <span data-ttu-id="c0690-153">水平視野 (FOV H)</span><span class="sxs-lookup"><span data-stu-id="c0690-153">Horizontal Field of View (H-FOV)</span></span> |  <span data-ttu-id="c0690-154">推奨される使用状況</span><span class="sxs-lookup"><span data-stu-id="c0690-154">Suggested usage</span></span> | 
  |----------|----------|----------|----------|----------|----------|
  |  <span data-ttu-id="c0690-155">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="c0690-155">1920x1080</span></span> |  <span data-ttu-id="c0690-156">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="c0690-156">1920x1080</span></span> |  <span data-ttu-id="c0690-157">なし</span><span class="sxs-lookup"><span data-stu-id="c0690-157">N/A</span></span> |  <span data-ttu-id="c0690-158">30、15 fps</span><span class="sxs-lookup"><span data-stu-id="c0690-158">30, 15 fps</span></span>  |  <span data-ttu-id="c0690-159">54deg</span><span class="sxs-lookup"><span data-stu-id="c0690-159">54deg</span></span>  |  <span data-ttu-id="c0690-160">(既定のモードでビデオ安定化)</span><span class="sxs-lookup"><span data-stu-id="c0690-160">(default mode with video stabilization)</span></span> | 
  |  <span data-ttu-id="c0690-161">なし</span><span class="sxs-lookup"><span data-stu-id="c0690-161">N/A</span></span> |  <span data-ttu-id="c0690-162">なし</span><span class="sxs-lookup"><span data-stu-id="c0690-162">N/A</span></span> |  <span data-ttu-id="c0690-163">3904 X 2196</span><span class="sxs-lookup"><span data-stu-id="c0690-163">3904X2196</span></span> |  <span data-ttu-id="c0690-164">なし</span><span class="sxs-lookup"><span data-stu-id="c0690-164">N/A</span></span>  |  <span data-ttu-id="c0690-165">64deg</span><span class="sxs-lookup"><span data-stu-id="c0690-165">64deg</span></span> |  <span data-ttu-id="c0690-166">最高の解像度の静止画</span><span class="sxs-lookup"><span data-stu-id="c0690-166">Highest resolution still image</span></span> | 
  |  <span data-ttu-id="c0690-167">2272 x 1278</span><span class="sxs-lookup"><span data-stu-id="c0690-167">2272x1278</span></span> |  <span data-ttu-id="c0690-168">2272 x 1278</span><span class="sxs-lookup"><span data-stu-id="c0690-168">2272x1278</span></span> |  <span data-ttu-id="c0690-169">なし</span><span class="sxs-lookup"><span data-stu-id="c0690-169">N/A</span></span> |  <span data-ttu-id="c0690-170">30、15 fps</span><span class="sxs-lookup"><span data-stu-id="c0690-170">30, 15 fps</span></span>  |  <span data-ttu-id="c0690-171">64deg</span><span class="sxs-lookup"><span data-stu-id="c0690-171">64deg</span></span> |  <span data-ttu-id="c0690-172">ビデオ安定化する前にオーバー (埋め込み) の解決</span><span class="sxs-lookup"><span data-stu-id="c0690-172">Overscan (padding) resolution before video stabilization</span></span> | 
  |  <span data-ttu-id="c0690-173">1952 x 1100</span><span class="sxs-lookup"><span data-stu-id="c0690-173">1952x1100</span></span> |  <span data-ttu-id="c0690-174">1952 x 1100</span><span class="sxs-lookup"><span data-stu-id="c0690-174">1952x1100</span></span> |  <span data-ttu-id="c0690-175">1952 x 1100</span><span class="sxs-lookup"><span data-stu-id="c0690-175">1952x1100</span></span>  |  <span data-ttu-id="c0690-176">30、15 fps</span><span class="sxs-lookup"><span data-stu-id="c0690-176">30, 15 fps</span></span>  |  <span data-ttu-id="c0690-177">64deg</span><span class="sxs-lookup"><span data-stu-id="c0690-177">64deg</span></span> |  <span data-ttu-id="c0690-178">高品質のストリーミング</span><span class="sxs-lookup"><span data-stu-id="c0690-178">High-quality streaming</span></span> | 
  |  <span data-ttu-id="c0690-179">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="c0690-179">1280x720</span></span> |  <span data-ttu-id="c0690-180">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="c0690-180">1280x720</span></span> |  <span data-ttu-id="c0690-181">なし</span><span class="sxs-lookup"><span data-stu-id="c0690-181">N/A</span></span> |  <span data-ttu-id="c0690-182">30、15、5 fps</span><span class="sxs-lookup"><span data-stu-id="c0690-182">30, 15, 5 fps</span></span>  |  <span data-ttu-id="c0690-183">64deg</span><span class="sxs-lookup"><span data-stu-id="c0690-183">64deg</span></span> |  <span data-ttu-id="c0690-184">イメージ処理タスクのストリーミングと低電源/解像度モード</span><span class="sxs-lookup"><span data-stu-id="c0690-184">Low power/resolution mode for streaming and image processing tasks</span></span> | 

## <a name="locating-the-device-camera-in-the-world"></a><span data-ttu-id="c0690-185">世界中で、デバイスのカメラを検索します。</span><span class="sxs-lookup"><span data-stu-id="c0690-185">Locating the Device Camera in the World</span></span>

<span data-ttu-id="c0690-186">HoloLens では、写真やビデオを受け取り、ときにキャプチャされたフレームには、透視投影カメラのほか、世界中で、カメラの位置が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c0690-186">When HoloLens takes photos and videos, the captured frames include the location of the camera in the world, as well as the perspective projection of the camera.</span></span> <span data-ttu-id="c0690-187">これにより、イメージング シナリオを拡張現実の世界でカメラの位置に関する理由アプリケーションことができます。</span><span class="sxs-lookup"><span data-stu-id="c0690-187">This allows applications to reason about the position of the camera in the real world for augmented imaging scenarios.</span></span> <span data-ttu-id="c0690-188">開発者は、お気に入りの画像処理またはカスタム コンピューター ビジョンのライブラリを使用して、独自のシナリオをロール独創的なことができます。</span><span class="sxs-lookup"><span data-stu-id="c0690-188">Developers can creatively roll their own scenarios using their favorite image processing or custom computer vision libraries.</span></span>

<span data-ttu-id="c0690-189">HoloLens のドキュメントの他の場所では「カメラ」は、「仮想ゲームのカメラ」(アプリの視錐台をレンダリングする) を参照できます。</span><span class="sxs-lookup"><span data-stu-id="c0690-189">"Camera" elsewhere in HoloLens documentation may refer to the "virtual game camera" (the frustum the app renders to).</span></span> <span data-ttu-id="c0690-190">それ以外の場合に示されるように、しない限り、このページでは「カメラ」は現実世界の RGB 色のカメラを指します。</span><span class="sxs-lookup"><span data-stu-id="c0690-190">Unless denoted otherwise, "camera" on this page refers to the real-world RGB color camera.</span></span>

<span data-ttu-id="c0690-191">詳細については、このページのカバー [Media Foundation 属性](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx)、組み込み関数を使用してカメラをプルするための Api がありますも[WinRT Api](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics)します。</span><span class="sxs-lookup"><span data-stu-id="c0690-191">The details on this page cover [Media Foundation Attributes](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx), however there are also APIs to pull camera intrinsics using [WinRT APIs](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics).</span></span>  

### <a name="images-with-coordinate-systems"></a><span data-ttu-id="c0690-192">座標系を使用したイメージ</span><span class="sxs-lookup"><span data-stu-id="c0690-192">Images with Coordinate Systems</span></span>

<span data-ttu-id="c0690-193">各イメージのフレーム (かどうかの写真またはビデオ)、座標系と 2 つの重要な変換が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c0690-193">Each image frame (whether photo or video) includes a coordinate system, as well as two important transforms.</span></span> <span data-ttu-id="c0690-194">"View"は、カメラに指定された座標システムからのマップおよびイメージのピクセルにカメラからの「射影」マップを変換します。</span><span class="sxs-lookup"><span data-stu-id="c0690-194">The "view" transform maps from the provided coordinate system to the camera, and the "projection" maps from the camera to pixels in the image.</span></span> <span data-ttu-id="c0690-195">同時に、これらの変換の定義の各ピクセル光線ピクセルを生成した光子で使用されるパスを表す 3 次元空間で。</span><span class="sxs-lookup"><span data-stu-id="c0690-195">Together, these transforms define for each pixel a ray in 3D space representing the path taken by the photons that produced the pixel.</span></span> <span data-ttu-id="c0690-196">フレームの座標系からいくつかその他の座標系に変換を取得することにより、アプリで他のコンテンツへこれら光線を関連付けることができます (などから、[フレームの静止した基準](coordinate-systems.md#stationary-frame-of-reference))。</span><span class="sxs-lookup"><span data-stu-id="c0690-196">These rays can be related to other content in the app by obtaining the transform from the frame's coordinate system to some other coordinate system (e.g. from a [stationary frame of reference](coordinate-systems.md#stationary-frame-of-reference)).</span></span> <span data-ttu-id="c0690-197">要約すると、各フレームの画像は次のよう</span><span class="sxs-lookup"><span data-stu-id="c0690-197">To summarize, each image frame provides the following:</span></span>
* <span data-ttu-id="c0690-198">ピクセル形式のデータ (を RGB、NV12、JPEG/など)</span><span class="sxs-lookup"><span data-stu-id="c0690-198">Pixel Data (in RGB/NV12/JPEG/etc. format)</span></span>
* <span data-ttu-id="c0690-199">メタデータの 3 つの要素 (として格納されている[IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)) 各フレームを"場所を特定できる"ようにします。</span><span class="sxs-lookup"><span data-stu-id="c0690-199">3 pieces of metadata (stored as [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)) that make each frame "locatable":</span></span>

|  <span data-ttu-id="c0690-200">属性名</span><span class="sxs-lookup"><span data-stu-id="c0690-200">Attribute name</span></span>  |  <span data-ttu-id="c0690-201">種類</span><span class="sxs-lookup"><span data-stu-id="c0690-201">Type</span></span>  |  <span data-ttu-id="c0690-202">GUID</span><span class="sxs-lookup"><span data-stu-id="c0690-202">GUID</span></span>  |  <span data-ttu-id="c0690-203">説明</span><span class="sxs-lookup"><span data-stu-id="c0690-203">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="c0690-204">MFSampleExtension_Spatial_CameraCoordinateSystem</span><span class="sxs-lookup"><span data-stu-id="c0690-204">MFSampleExtension_Spatial_CameraCoordinateSystem</span></span>  |  <span data-ttu-id="c0690-205">IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))</span><span class="sxs-lookup"><span data-stu-id="c0690-205">IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))</span></span>  |  <span data-ttu-id="c0690-206">{9D13C82F-2199-4E67-91CD-D1A4181F2534}</span><span class="sxs-lookup"><span data-stu-id="c0690-206">{9D13C82F-2199-4E67-91CD-D1A4181F2534}</span></span>  |  <span data-ttu-id="c0690-207">ストア、[座標系](coordinate-systems-in-directx.md)キャプチャされたフレームの</span><span class="sxs-lookup"><span data-stu-id="c0690-207">Stores the [coordinate system](coordinate-systems-in-directx.md) of the captured frame</span></span> | 
|  <span data-ttu-id="c0690-208">MFSampleExtension_Spatial_CameraViewTransform</span><span class="sxs-lookup"><span data-stu-id="c0690-208">MFSampleExtension_Spatial_CameraViewTransform</span></span>  |  <span data-ttu-id="c0690-209">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span><span class="sxs-lookup"><span data-stu-id="c0690-209">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span></span>  |  <span data-ttu-id="c0690-210">{4E251FA4-830F-4770-859A-4B8D99AA809B}</span><span class="sxs-lookup"><span data-stu-id="c0690-210">{4E251FA4-830F-4770-859A-4B8D99AA809B}</span></span>  |  <span data-ttu-id="c0690-211">座標システムでのカメラの外部の変換を格納します。</span><span class="sxs-lookup"><span data-stu-id="c0690-211">Stores the camera's extrinsic transform in the coordinate system</span></span> | 
|  <span data-ttu-id="c0690-212">MFSampleExtension_Spatial_CameraProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="c0690-212">MFSampleExtension_Spatial_CameraProjectionTransform</span></span>  |  <span data-ttu-id="c0690-213">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span><span class="sxs-lookup"><span data-stu-id="c0690-213">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span></span>  |  <span data-ttu-id="c0690-214">{47F9FCB5-2A02-4F26-A477-792FDF95886A}</span><span class="sxs-lookup"><span data-stu-id="c0690-214">{47F9FCB5-2A02-4F26-A477-792FDF95886A}</span></span>  |  <span data-ttu-id="c0690-215">カメラの projection 変換を格納します。</span><span class="sxs-lookup"><span data-stu-id="c0690-215">Stores the camera's projection transform</span></span> | 

<span data-ttu-id="c0690-216">Projection 変換は、X と Y の両方の軸の +1-1 からまでをイメージ平面上のマップ レンズの組み込みプロパティ (焦点距離、投影の中心の傾斜) を表します。</span><span class="sxs-lookup"><span data-stu-id="c0690-216">The projection transform represents the intrinsic properties (focal length, center of projection, skew) of the lens mapped onto an image plane that extends from -1 to +1 in both the X and Y axis.</span></span>

```
Matrix4x4 format          Terms
   m11 m12 m13 m14      fx    0   0   0
   m21 m22 m23 m24     skew  fy   0   0
   m31 m32 m33 m34      cx   cy   A  -1
   m41 m42 m43 m44       0    0   B   0
```

<span data-ttu-id="c0690-217">さまざまなアプリケーションは、さまざまな座標系必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0690-217">Different applications will have different coordinate systems.</span></span> <span data-ttu-id="c0690-218">1 つのアプリケーションのカメラのピクセルを検索するフローの概要を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c0690-218">Here's an overview of the flow to locate a camera pixel for a single application:</span></span>

![カメラの座標系に適用された変換](images/pvcameratransform5-500px.png)

### <a name="camera-to-application-specified-coordinate-system"></a><span data-ttu-id="c0690-220">アプリケーションで指定された座標系にカメラ</span><span class="sxs-lookup"><span data-stu-id="c0690-220">Camera to Application-specified Coordinate System</span></span>

<span data-ttu-id="c0690-221">アプリケーション/ワールド座標系を 'カメラビュー' と 'CameraCoordinateSystem' からは、次が必要です。</span><span class="sxs-lookup"><span data-stu-id="c0690-221">To go from the 'CameraView' and 'CameraCoordinateSystem' to your application/world coordinate system, you'll need the following:</span></span>

<span data-ttu-id="c0690-222">[Unity での場所を特定できるカメラ](locatable-camera-in-unity.md):CameraToWorldMatrix は、(ため CameraCoordinateSystem 変換について心配する必要はありません) に自動的に PhotoCaptureFrame クラスによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="c0690-222">[Locatable camera in Unity](locatable-camera-in-unity.md): CameraToWorldMatrix is automatically provided by PhotoCaptureFrame class(so you don't need to worry about the CameraCoordinateSystem transforms).</span></span>

<span data-ttu-id="c0690-223">[DirectX の場所を特定できるカメラ](locatable-camera-in-directx.md):カメラの座標系と独自アプリケーション coordinate system(s) 間で変換を照会する非常に簡単な方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c0690-223">[Locatable camera in DirectX](locatable-camera-in-directx.md): Shows the fairly straightforward way to query for the transform between the camera's coordinate system and your own application coordinate system(s).</span></span>

### <a name="application-specified-coordinate-system-to-pixel-coordinates"></a><span data-ttu-id="c0690-224">ピクセル座標を座標システムのアプリケーションで指定されました。</span><span class="sxs-lookup"><span data-stu-id="c0690-224">Application-specified Coordinate System to Pixel Coordinates</span></span>

<span data-ttu-id="c0690-225">検索またはでカメラ イメージ 3d の特定の場所に描画したいとします。</span><span class="sxs-lookup"><span data-stu-id="c0690-225">Let's say you wanted to find or draw at a specific 3d location on a camera image:</span></span>

<span data-ttu-id="c0690-226">ビューおよび射影変換の両方の 4 × 4 行列の中には、若干異なる方法で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0690-226">The view and projection transforms, while both 4x4 matrices, need to be utilized slightly differently.</span></span> <span data-ttu-id="c0690-227">Namely の射影を実行するには後、1 つは"正規化 w で'、投影でこの余分な手順をシミュレート (つまり特定光線に沿ったものに表示されます、同じピクセル)、画面上の同じ 2d 場所として複数の異なる 3d 場所が最終的にできます。</span><span class="sxs-lookup"><span data-stu-id="c0690-227">Namely after performing the Projection, one would 'normalize by w', this extra step in the projection simulates how multiple different 3d locations can end up as the same 2d location on a screen (i.e. anything along a certain ray will show up on the same pixel).</span></span> <span data-ttu-id="c0690-228">(シェーダー コード) で、キーのポイント:</span><span class="sxs-lookup"><span data-stu-id="c0690-228">So key points (in shader code):</span></span>

```
// Usual 3d math:
 float4x4 WorldToCamera = inverse( CameraToWorld );
 float4 CameraSpacePos = mul( WorldToCamera, float4( WorldSpacePos.xyz, 1 ) ); // use 1 as the W component
 // Projection math:
 float4 ImagePosUnnormalized = mul( CameraProjection, float4( CameraSpacePos.xyz, 1 ) ); // use 1 as the W component
 float2 ImagePosProjected = ImagePosUnnormalized.xy / ImagePosUnnormalized.w; // normalize by W, gives -1 to 1 space
 float2 ImagePosZeroToOne = ( ImagePosProjected * 0.5 ) + float2( 0.5, 0.5 ); // good for GPU textures
 int2 PixelPos = int2( ImagePosZeroToOne.x * ImageWidth, ( 1 - ImagePosZeroToOne.y ) * ImageHeight ); // good for CPU textures
```

### <a name="pixel-to-application-specified-coordinate-system"></a><span data-ttu-id="c0690-229">アプリケーションで指定された座標系にピクセル</span><span class="sxs-lookup"><span data-stu-id="c0690-229">Pixel to Application-specified Coordinate System</span></span>

<span data-ttu-id="c0690-230">ワールド座標をピクセルからの移動には、やや難しくなります。</span><span class="sxs-lookup"><span data-stu-id="c0690-230">Going from pixel to world coordinates is a little trickier:</span></span>

```
float2 ImagePosZeroToOne = float2( PixelPos.x / ImageWidth, 1.0 - (PixelPos.y / ImageHeight ) );
 float2 ImagePosProjected = ( ( ImagePosZeroToOne * 2.0 ) - float2(1,1) ); // -1 to 1 space
 float3 CameraSpacePos = UnProjectVector( Projection, float3( ImagePosProjected, 1) );
 float3 WorldSpaceRayPoint1 = mul( CameraToWorld, float4(0,0,0,1) ); // camera location in world space
 float3 WorldSpaceRayPoint2 = mul( CameraToWorld, CameraSpacePos ); // ray point in world space
```

<span data-ttu-id="c0690-231">場所として UnProject を定義します。</span><span class="sxs-lookup"><span data-stu-id="c0690-231">Where we define UnProject as:</span></span>

```
public static Vector3 UnProjectVector(Matrix4x4 proj, Vector3 to)
 {
   Vector3 from = new Vector3(0, 0, 0);
   var axsX = proj.GetRow(0);
   var axsY = proj.GetRow(1);
   var axsZ = proj.GetRow(2);
   from.z = to.z / axsZ.z;
   from.y = (to.y - (from.z * axsY.z)) / axsY.y;
   from.x = (to.x - (from.z * axsX.z)) / axsX.x;
   return from;
 }
```

<span data-ttu-id="c0690-232">ポイントの実際の世界の場所を検索する必要がありますか。 2 つの世界光線とそれぞれの積集合、またはポイントの既知のサイズを検索します。</span><span class="sxs-lookup"><span data-stu-id="c0690-232">To find the actual world location of a point, you'll need either: two world rays and find their intersection, or a known size of the points.</span></span>

### <a name="distortion-error"></a><span data-ttu-id="c0690-233">歪みのエラー</span><span class="sxs-lookup"><span data-stu-id="c0690-233">Distortion Error</span></span>

<span data-ttu-id="c0690-234">HoloLens、ビデオおよび静止画像ストリームされない、システムのイメージ処理パイプラインでは変形 (プレビュー ストリームは、元の歪んだフレームを含む)、アプリケーションで使用できるように、フレーム前にします。</span><span class="sxs-lookup"><span data-stu-id="c0690-234">On HoloLens, the video and still image streams are undistorted in the system's image processing pipeline before the frames are made available to the application (the preview stream contains the original distorted frames).</span></span> <span data-ttu-id="c0690-235">射影行列のみが利用できるので、アプリケーションでも、イメージ フレームを表しますを完璧な一カメラを想定する必要があります、イメージ プロセッサ関数、歪みを除去ただししまう可能性がありますも最大 10 個のピクセルのエラーで投影行列を使用する場合フレームのメタデータ。</span><span class="sxs-lookup"><span data-stu-id="c0690-235">Because only the projection matrix is made available, applications must assume image frames represent a perfect pinhole camera, however the undistortion function in the image processor may still leave an error of up to 10 pixels when using the projection matrix in the frame metadata.</span></span> <span data-ttu-id="c0690-236">多くのユース ケース、場合など、現実世界のポスター/マーカーにホログラムを配置してわかりますが、このエラーが問題ない、< 10px オフセット (位置 2 メートル離れたホログラムの約 11 mm) このゆがみエラーが原因になります。</span><span class="sxs-lookup"><span data-stu-id="c0690-236">In many use cases, this error will not matter, but if you are aligning holograms to real world posters/markers, for example, and you notice a <10px offset (roughly 11mm for holograms positioned 2 meters away) this distortion error could be the cause.</span></span>

## <a name="locatable-camera-usage-scenarios"></a><span data-ttu-id="c0690-237">場所を特定できるカメラの使用シナリオ</span><span class="sxs-lookup"><span data-stu-id="c0690-237">Locatable Camera Usage Scenarios</span></span>

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a><span data-ttu-id="c0690-238">キャプチャされた世界で写真やビデオを表示します。</span><span class="sxs-lookup"><span data-stu-id="c0690-238">Show a photo or video in the world where it was captured</span></span>

<span data-ttu-id="c0690-239">デバイスのカメラのフレームには"カメラ World"の変換になり、イメージが作成されたときに、デバイスの正確なが表示に使用できます。</span><span class="sxs-lookup"><span data-stu-id="c0690-239">The Device Camera frames come with a "Camera To World" transform, that can be used to show exactly where the device was when the image was taken.</span></span> <span data-ttu-id="c0690-240">小さい holographic アイコン (CameraToWorld.MultiplyPoint(Vector3.zero)) およびも描画カメラには (CameraToWorld.MultiplyVector(Vector3.forward)) が直面していました方向に小さな矢印は、この場所に配置する例。</span><span class="sxs-lookup"><span data-stu-id="c0690-240">For example you could position a small holographic icon at this location (CameraToWorld.MultiplyPoint(Vector3.zero)) and even draw a little arrow in the direction that the camera was facing (CameraToWorld.MultiplyVector(Vector3.forward)).</span></span>

### <a name="painting-the-world-using-a-camera-shader"></a><span data-ttu-id="c0690-241">カメラのシェーダーを使用して、世界中の描画</span><span class="sxs-lookup"><span data-stu-id="c0690-241">Painting the world using a camera shader</span></span>

<span data-ttu-id="c0690-242">このセクションで作成します素材 'シェーダー' 世界が、デバイスのカメラのビューに含めました場所に基づいてその色。</span><span class="sxs-lookup"><span data-stu-id="c0690-242">In this section we'll create a material 'shader' that colors the world based on where it showed up in a device camera's view.</span></span> <span data-ttu-id="c0690-243">効果的に行うことは各頂点は、カメラを基準には、その場所を把握、ごとのピクセルが図に投影行列を利用し、イメージに関連付けられているテクセルを出力します。</span><span class="sxs-lookup"><span data-stu-id="c0690-243">Effectively what we'll do is that every vertex will figure out its location relative to the camera, and then every pixel will utilize the 'projection matrix' to figure out which image texel it is associated with.</span></span> <span data-ttu-id="c0690-244">最後に、および必要に応じてよりも多くの夢のようなメモリを表示するイメージのコーナー フェードアウトします。</span><span class="sxs-lookup"><span data-stu-id="c0690-244">Lastly, and optionally, we'll fade out the corners of the image to make it appear more as a dream-like memory:</span></span>

```
// In the vertex shader:
 float4 worldSpace = mul( ObjectToWorld, float4( vertexPos.xyz, 1));
 float4 cameraSpace = mul( CameraWorldToLocal, float4(worldSpace.xyz, 1));

 // In the pixel shader:
 float4 unprojectedTex = mul( CameraProjection, float4( cameraSpace .xyz, 1));
 float2 projectedTex = (unprojectedTex.xy / unprojectedTex.w);
 float2 unitTexcoord = ((projectedTex * 0.5) + float4(0.5, 0.5, 0, 0));
 float4 cameraTextureColor = tex2D(_CameraTex, unitTexcoord);
 // Fade out edges for better look:
 float pctInView = saturate((1.0 - length(projectedTex.xy)) * 3.0);
 float4 finalColor = float4( cameraTextureColor.rgb, pctInView );
```

### <a name="tag--pattern--poster--object-tracking"></a><span data-ttu-id="c0690-245">タグ/パターン/ポスター/追跡オブジェクト</span><span class="sxs-lookup"><span data-stu-id="c0690-245">Tag / Pattern / Poster / Object Tracking</span></span>

<span data-ttu-id="c0690-246">複合現実の多くのアプリケーションでは、認識可能なイメージや視覚的なパターンを使用して、領域に適したポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="c0690-246">Many mixed reality applications use a recognizable image or visual pattern to create a trackable point in space.</span></span> <span data-ttu-id="c0690-247">これはオブジェクトを基準としたか、既知の場所を作成、表示するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c0690-247">This is then used to render objects relative to that point or create a known location.</span></span> <span data-ttu-id="c0690-248">HoloLens の使用は、調べて (例: QR コードをテレビ モニター) でタグ付けされた現実の世界のオブジェクトを検索、ホログラムを調べて、経由で配置する視覚的に経由での HoloLens との通信にセットアップされているタブレットなどの非 HoloLens デバイスとペアリングWi-fi。</span><span class="sxs-lookup"><span data-stu-id="c0690-248">Some uses for HoloLens include finding a real world object tagged with fiducials (e.g. a TV monitor with a QR code), placing holograms over fiducials, and visually pairing with non-HoloLens devices like tablets that have been setup to communicate with HoloLens via Wi-Fi.</span></span>

<span data-ttu-id="c0690-249">を視覚的なパターンを認識して、アプリケーションのワールド空間におけるそのオブジェクトを配置するには、いくつかの点を必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0690-249">To recognize a visual pattern, and then place that object in the applications world space, you'll need a few things:</span></span>
1. <span data-ttu-id="c0690-250">イメージのパターン認識ツールキット円トラッカー、OCR など、QR コード、AR タグ、顔 finder など。</span><span class="sxs-lookup"><span data-stu-id="c0690-250">An image pattern recognition toolkit, such as QR code, AR tags, face finder, circle trackers, OCR etc.</span></span>
2. <span data-ttu-id="c0690-251">実行時に、イメージ フレームを収集して認識レイヤーに渡す</span><span class="sxs-lookup"><span data-stu-id="c0690-251">Collect image frames at runtime, and pass them to the recognition layer</span></span>
3. <span data-ttu-id="c0690-252">世界中の位置や可能性の高い世界光線に戻す、画像の場所を unproject します。</span><span class="sxs-lookup"><span data-stu-id="c0690-252">Unproject their image locations back into world positions, or likely world rays.</span></span> <span data-ttu-id="c0690-253">参照先</span><span class="sxs-lookup"><span data-stu-id="c0690-253">See</span></span>
4. <span data-ttu-id="c0690-254">世界中のこれらの場所の上、仮想モデルを配置します。</span><span class="sxs-lookup"><span data-stu-id="c0690-254">Position your virtual models over these world locations</span></span>

<span data-ttu-id="c0690-255">いくつかの重要なイメージ処理リンク:</span><span class="sxs-lookup"><span data-stu-id="c0690-255">Some important image processing links:</span></span>
* [<span data-ttu-id="c0690-256">OpenCV</span><span class="sxs-lookup"><span data-stu-id="c0690-256">OpenCV</span></span>](http://opencv.org/)
* [<span data-ttu-id="c0690-257">QR タグ</span><span class="sxs-lookup"><span data-stu-id="c0690-257">QR Tags</span></span>](https://en.wikipedia.org/wiki/QR_code)
* [<span data-ttu-id="c0690-258">FaceSDK</span><span class="sxs-lookup"><span data-stu-id="c0690-258">FaceSDK</span></span>](http://research.microsoft.com/projects/facesdk/)
* [<span data-ttu-id="c0690-259">Microsoft Translator</span><span class="sxs-lookup"><span data-stu-id="c0690-259">Microsoft Translator</span></span>](https://www.microsoft.com/translator/business)

<span data-ttu-id="c0690-260">対話型アプリケーションのフレーム レートを維持することは、します実行時間の長いイメージ認識アルゴリズムを扱う場合に特に重要な。</span><span class="sxs-lookup"><span data-stu-id="c0690-260">Keeping an interactive application frame-rate is critical, especially when dealing with long-running image recognition algorithms.</span></span> <span data-ttu-id="c0690-261">このため、次のパターンよく使用します。</span><span class="sxs-lookup"><span data-stu-id="c0690-261">For this reason we commonly use the following pattern:</span></span>
1. <span data-ttu-id="c0690-262">メイン スレッド: カメラ オブジェクトを管理します。</span><span class="sxs-lookup"><span data-stu-id="c0690-262">Main Thread: manages the camera object</span></span>
2. <span data-ttu-id="c0690-263">メイン スレッド: 要求の新しいフレーム (非同期)</span><span class="sxs-lookup"><span data-stu-id="c0690-263">Main Thread: requests new frames (async)</span></span>
3. <span data-ttu-id="c0690-264">メイン スレッド: スレッドを追跡する新しいフレームを渡す</span><span class="sxs-lookup"><span data-stu-id="c0690-264">Main Thread: pass new frames to tracking thread</span></span>
4. <span data-ttu-id="c0690-265">重要なポイントを収集するスレッドの追跡: プロセスのイメージ</span><span class="sxs-lookup"><span data-stu-id="c0690-265">Tracking Thread: processes image to collect key points</span></span>
5. <span data-ttu-id="c0690-266">メイン スレッド: 一致するように仮想モデルの移動が検出された重要なポイント</span><span class="sxs-lookup"><span data-stu-id="c0690-266">Main Thread: moves virtual model to match found key points</span></span>
6. <span data-ttu-id="c0690-267">手順 2 からメイン スレッド: 繰り返し</span><span class="sxs-lookup"><span data-stu-id="c0690-267">Main Thread: repeat from step 2</span></span>

<span data-ttu-id="c0690-268">イメージのマーカー システムによってのみ 1 つのピクセルの場所を提供する (完全な変換を提供する場合、このセクションでは必要ありません)、可能な場所の光線に相当します。</span><span class="sxs-lookup"><span data-stu-id="c0690-268">Some image marker systems only provide a single pixel location (others provide the full transform in which case this section will not be needed), which equates to a ray of possible locations.</span></span> <span data-ttu-id="c0690-269">1 つの 3d の場所を取得するには複数光線を活用し、おおよその重なる部分によって、最終的な結果を検索します。</span><span class="sxs-lookup"><span data-stu-id="c0690-269">To get to a single 3d location we can then leverage multiple rays and find the final result by their approximate intersection.</span></span> <span data-ttu-id="c0690-270">これを行うには、する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0690-270">To do this you'll need to:</span></span>
1. <span data-ttu-id="c0690-271">複数のカメラのイメージの収集とループします。</span><span class="sxs-lookup"><span data-stu-id="c0690-271">Get a loop going collecting multiple camera images</span></span>
2. <span data-ttu-id="c0690-272">検索、[関連付けられている機能のポイント](#pixel-to-application-specified-coordinate-system)、およびその世界光線</span><span class="sxs-lookup"><span data-stu-id="c0690-272">Find the [associated feature points](#pixel-to-application-specified-coordinate-system), and their world rays</span></span>
3. <span data-ttu-id="c0690-273">機能は、それぞれに複数の世界光線のディクショナリがある場合は、その光線が交差する位置を解決するために、次のコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c0690-273">When you have a dictionary of features, each with multiple world rays, you can use the following code to solve for the intersection of those rays:</span></span>

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

<span data-ttu-id="c0690-274">2 つ以上の追跡対象タグの場所を指定するには、ユーザーの現在のシナリオに合わせて modelled シーンを配置できます。</span><span class="sxs-lookup"><span data-stu-id="c0690-274">Given two or more tracked tag locations, you can position a modelled scene to fit the users current scenario.</span></span> <span data-ttu-id="c0690-275">重力を想定することはできませんがある場合は、次の 3 つのタグの場所を必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0690-275">If you can't assume gravity, then you'll need three tag locations.</span></span> <span data-ttu-id="c0690-276">使用して多くの場合白の球体がリアルタイムを表す単純な配色、タグの場所を追跡して青の球体がモデル化のタグの場所を表す、これにより、ユーザーを視覚的に配置の品質を測定します。</span><span class="sxs-lookup"><span data-stu-id="c0690-276">In many cases we use a simple color scheme where white spheres represent real-time tracked tag locations, and blue spheres represent modelled tag locations, this allows the user to visually gauge the alignment quality.</span></span> <span data-ttu-id="c0690-277">すべてのアプリケーションで、次の設定と仮定します。</span><span class="sxs-lookup"><span data-stu-id="c0690-277">We assume the following setup in all our applications:</span></span>
* <span data-ttu-id="c0690-278">2 つまたは複数のモデル化のタグの場所</span><span class="sxs-lookup"><span data-stu-id="c0690-278">Two or more modelled tag locations</span></span>
* <span data-ttu-id="c0690-279">1 つは「調整スペース」が、シーン内のタグの親であります。</span><span class="sxs-lookup"><span data-stu-id="c0690-279">One 'calibration space' which in the scene is the parent of the tags</span></span>
* <span data-ttu-id="c0690-280">カメラの機能の識別子</span><span class="sxs-lookup"><span data-stu-id="c0690-280">Camera feature identifier</span></span>
* <span data-ttu-id="c0690-281">(は親領域自体、modelled マーカーいないを移動するように注意してください。 他の接続がそれらの相対位置であるため)、リアルタイムのタグを使用して、modelled タグに合わせて調整領域を移動する動作。</span><span class="sxs-lookup"><span data-stu-id="c0690-281">Behavior which moves the calibration space to align the modelled tags with the real-time tags (we are careful to move the parent space, not the modelled markers themselves, because other connect is positions relative to them).</span></span>

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="render-holograms-from-the-cameras-position"></a><span data-ttu-id="c0690-282">カメラの位置からホログラムをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="c0690-282">Render holograms from the Camera's position</span></span>

<span data-ttu-id="c0690-283">注:独自に作成しようとしている場合[実際のキャプチャ (MRC) を混在](mixed-reality-capture.md)、カメラのストリームを持つホログラムをブレンドする、使用することができます、 [MRC 効果](mixed-reality-capture-for-developers.md)showHolograms プロパティを有効にまたは[Unity での場所を特定できるカメラ](locatable-camera-in-unity.md)します。</span><span class="sxs-lookup"><span data-stu-id="c0690-283">Note: If you are trying to create your own [Mixed reality capture (MRC)](mixed-reality-capture.md), which blends holograms with the Camera stream, you can use the [MRC effects](mixed-reality-capture-for-developers.md) or enable the showHolograms property in [Locatable camera in Unity](locatable-camera-in-unity.md).</span></span>

<span data-ttu-id="c0690-284">RGB カメラ ストリーム上で直接特殊なレンダリングを実行したい場合、カスタム ホログラム記録/ライブ プレビューを提供するためにカメラの位置からの領域でホログラム ビデオ フィードとの同期をレンダリングすることは。</span><span class="sxs-lookup"><span data-stu-id="c0690-284">If you'd like to do a special render directly on the RGB Camera stream, it's possible to render holograms in space from the Camera's position in sync with a video feed in order to provide a custom hologram recording/live preview.</span></span>

<span data-ttu-id="c0690-285">Skype、HoloLens のユーザーが認識されて、リモート クライアントを表示して、同じホログラムと対話することを行います。</span><span class="sxs-lookup"><span data-stu-id="c0690-285">In Skype, we do this to show the remote client what the HoloLens user is seeing and allow them to interact with the same holograms.</span></span> <span data-ttu-id="c0690-286">Skype サービスを通じて各ビデオのフレーム経由で送信する前に、各フレームの対応するカメラのデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="c0690-286">Before sending over each video frame through the Skype service, we grab each frame's corresponding camera data.</span></span> <span data-ttu-id="c0690-287">ビデオのフレームを使用してカメラの外部と組み込みのメタデータをパッケージ化し、Skype サービス経由で送信します。</span><span class="sxs-lookup"><span data-stu-id="c0690-287">We then package the camera's extrinsic and intrinsic metadata with the video frame and then send it over the Skype service.</span></span>

<span data-ttu-id="c0690-288">受信側では、Unity を使用してした既に同期されてすべて同じ座標系を使用して、HoloLens のユーザーの領域でホログラムの。</span><span class="sxs-lookup"><span data-stu-id="c0690-288">On the receiving side, using Unity, we've already synced all of the holograms in the HoloLens user's space using the same coordinate system.</span></span> <span data-ttu-id="c0690-289">これにより、カメラの外部メタデータを使用して、HoloLens のユーザーがそのビデオのフレームをキャプチャしたときに立っていました (、ホログラムの残りの部分) を基準と世界中で正確な場所に Unity のカメラを配置するカメラの組み込みの情報を使用して、できます。ビューは、同じことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c0690-289">This allows us to use the camera's extrinsic metadata to place the Unity camera in the exact place in the world (relative to the rest of the holograms) that the HoloLens user was standing when that video frame was captured, and use the camera intrinsic information to ensure the view is the same.</span></span>

<span data-ttu-id="c0690-290">カメラが適切に設定したら、Skype、HoloLens ユーザーには Graphics.Blit を使用しての複合現実ビューの作成から受け取りましたフレーム上にカメラが表示されるどのようなホログラムを組み合わせています。</span><span class="sxs-lookup"><span data-stu-id="c0690-290">Once we have the camera set up properly, we combine what holograms the camera sees onto the frame we received from Skype, creating a mixed reality view of what the HoloLens user sees using Graphics.Blit.</span></span>

```cs
private void OnFrameReceived(Texture frameTexture, Vector3 cameraPosition, Quaternion cameraRotation, Matrix4x4 cameraProjectionMatrix)
{
    //set material that will be blitted onto the RenderTexture
    this.compositeMaterial.SetTexture(CompositeRenderer.CameraTextureMaterialProperty, frameTexture);
    //set the camera to be that of the HoloLens's device camera
    this.Camera.transform.position = cameraPosition;
    this.Camera.transform.rotation = cameraRotation;
    this.Camera.projectionMatrix = cameraProjectionMatrix;
    //trigger the Graphics's Blit now that the frame and camera are set up
    this.TextureReady = false;
}
private void OnRenderImage(RenderTexture source, RenderTexture destination)
{
    if (!this.TextureReady)
    {
        Graphics.Blit(source, destination, this.compositeMaterial);
        this.TextureReady = true;
    }
}
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a><span data-ttu-id="c0690-291">追跡またはタグ付けされた固定の識別または移動現実世界のオブジェクト/顔 Led または認識エンジンの他のライブラリを使用して</span><span class="sxs-lookup"><span data-stu-id="c0690-291">Track or Identify Tagged Stationary or Moving real-world objects/faces using LEDs or other recognizer libraries</span></span>

<span data-ttu-id="c0690-292">例:</span><span class="sxs-lookup"><span data-stu-id="c0690-292">Examples:</span></span>
* <span data-ttu-id="c0690-293">Led の産業ロボット (または低速に移動するため QR コードのオブジェクト)</span><span class="sxs-lookup"><span data-stu-id="c0690-293">Industrial robots with LEDs (or QR codes for slower moving objects)</span></span>
* <span data-ttu-id="c0690-294">識別し、ルーム内のオブジェクトを認識</span><span class="sxs-lookup"><span data-stu-id="c0690-294">Identify and recognize objects in the room</span></span>
* <span data-ttu-id="c0690-295">識別し、(例: 場所 holographic 連絡先カード顔) ルーム内のユーザーの認識</span><span class="sxs-lookup"><span data-stu-id="c0690-295">Identify and recognize people in the room (e.g. place holographic contact cards over faces)</span></span>

## <a name="see-also"></a><span data-ttu-id="c0690-296">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0690-296">See also</span></span>
* [<span data-ttu-id="c0690-297">DirectX の場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="c0690-297">Locatable camera in DirectX</span></span>](locatable-camera-in-directx.md)
* [<span data-ttu-id="c0690-298">Unity での場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="c0690-298">Locatable camera in Unity</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="c0690-299">複合現実のキャプチャ</span><span class="sxs-lookup"><span data-stu-id="c0690-299">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="c0690-300">開発者向けの実際のキャプチャの混在</span><span class="sxs-lookup"><span data-stu-id="c0690-300">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="c0690-301">メディアのキャプチャの概要</span><span class="sxs-lookup"><span data-stu-id="c0690-301">Media capture introduction</span></span>](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
