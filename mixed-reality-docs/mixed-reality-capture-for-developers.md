---
title: 開発者向けの実際のキャプチャの混在
description: 開発者の複合現実のベスト プラクティスをキャプチャします。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、写真、ビデオ、キャプチャ、カメラ
ms.openlocfilehash: c2d98baf16b2ea724247224aabadc1e2ca533ec1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599454"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="552f2-104">開発者向けの実際のキャプチャの混在</span><span class="sxs-lookup"><span data-stu-id="552f2-104">Mixed reality capture for developers</span></span>

> [!NOTE]
> <span data-ttu-id="552f2-105">HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。</span><span class="sxs-lookup"><span data-stu-id="552f2-105">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span> 

<span data-ttu-id="552f2-106">参照してください[アプリで有効にする MRC](#enabling-mrc-in-your-app)下 HoloLens 2 のガイダンスについては新しい MRC 機能。</span><span class="sxs-lookup"><span data-stu-id="552f2-106">See [Enabling MRC in your app](#enabling-mrc-in-your-app) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="552f2-107">ユーザーがかかる場合がありますので、[実際のキャプチャを混合](mixed-reality-capture.md)(MRC) 写真またはビデオをいつでも、いくつか点が、アプリケーションを開発するときに点に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="552f2-107">Since a user could take a [mixed reality capture](mixed-reality-capture.md) (MRC) photo or video at any time, there are a few things that you should keep in mind when developing your application.</span></span> <span data-ttu-id="552f2-108">これには、MRC 画質と MRCs をキャプチャ中にシステムの変更に応答するためのベスト プラクティスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="552f2-108">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="552f2-109">開発者は、それぞれのアプリに、複合現実のキャプチャと挿入を統合できますもシームレスにします。</span><span class="sxs-lookup"><span data-stu-id="552f2-109">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="552f2-110">MRC HoloLens (第 1 世代) では、ビデオをサポートしており、720 p、最大の写真を MRC HoloLens 2 の 4 K 解像度を最大 1080p と写真のビデオをサポートします。</span><span class="sxs-lookup"><span data-stu-id="552f2-110">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="552f2-111">品質 MRC の重要性</span><span class="sxs-lookup"><span data-stu-id="552f2-111">The importance of quality MRC</span></span>

<span data-ttu-id="552f2-112">複合現実にキャプチャされた写真とビデオが初めてユーザーがアプリの必要があります。</span><span class="sxs-lookup"><span data-stu-id="552f2-112">Mixed reality captured photos and videos are likely the first exposure a user will have of your app.</span></span> <span data-ttu-id="552f2-113">Microsoft Store のページで、またはソーシャル ネットワーク上で MRCs を共有する他のユーザーから複合現実のスクリーン ショットとしてかどうか。</span><span class="sxs-lookup"><span data-stu-id="552f2-113">Whether as mixed reality screenshots on your Microsoft Store page or from other users sharing MRCs on social networks.</span></span> <span data-ttu-id="552f2-114">MRC を使用するには、アプリのデモ、ユーザーを教育する、その混合世界の相互作用を共有するユーザーに促すユーザー調査および問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="552f2-114">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="552f2-115">MRC がアプリに与える影響</span><span class="sxs-lookup"><span data-stu-id="552f2-115">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="552f2-116">アプリで MRC を有効にします。</span><span class="sxs-lookup"><span data-stu-id="552f2-116">Enabling MRC in your app</span></span>

<span data-ttu-id="552f2-117">既定では、アプリは複合現実のキャプチャを実行するユーザーを有効にする何もありません。</span><span class="sxs-lookup"><span data-stu-id="552f2-117">By default, an app does not have to do anything to enable users to take mixed reality captures.</span></span> <span data-ttu-id="552f2-118">ただし、HoloLens 2 の設計では、写真/ビデオ (PV) カメラと画面間の距離を増加するためを導入することの PV カメラに配置されたサード カメラ レンダリングを生成するために新しいオプション**HoloLens 2**します。</span><span class="sxs-lookup"><span data-stu-id="552f2-118">However, because the design of HoloLens 2 increases the distance between the photo/video (PV) camera and the display, we'll be introducing a new option to produce a 3rd camera render aligned to the PV camera of **HoloLens 2**.</span></span> 

<span data-ttu-id="552f2-119">第 3 のカメラをで選択するとレンダリング HoloLens 2 プランの次の機能強化既定 MRC のエクスペリエンス。</span><span class="sxs-lookup"><span data-stu-id="552f2-119">Opting-in to 3rd camera render on HoloLens 2 offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="552f2-120">ホログラム位置は、物理環境と (ほぼ相互作用) を手にする必要があります正確なすべてのではなくオフセット距離で他にも、距離、[フォーカス ポイント](focus-point-in-unity.md)既定 MRC でわかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="552f2-120">Hologram alignment to both your physical environment and hands (for near interactions) should be accurate at all distances, instead of having an offset at distances other than the [focus point](focus-point-in-unity.md) as you might see in the default MRC.</span></span>
* <span data-ttu-id="552f2-121">MRC 出力ホログラムを表示するために使用されないよう、ヘッドセットで適切な目を侵害されるは。</span><span class="sxs-lookup"><span data-stu-id="552f2-121">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="552f2-122">アプリで MRC を無効にします。</span><span class="sxs-lookup"><span data-stu-id="552f2-122">Disabling MRC in your app</span></span>

<span data-ttu-id="552f2-123">2D アプリを使用する場合[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx)または[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx)を適切に構成されたスワップ チェーンを持つ保護されたコンテンツを表示するには、アプリのビジュアル コンテンツになります複合現実のキャプチャの実行中に隠されて自動的にします。</span><span class="sxs-lookup"><span data-stu-id="552f2-123">When a 2D app uses [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx) or [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx) to show protected content with a properly-configured swap chain, the app's visual content will be automatically obscured while mixed reality capture is running.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="552f2-124">MRC がアクティブな場合を知る</span><span class="sxs-lookup"><span data-stu-id="552f2-124">Knowing when MRC is active</span></span>

<span data-ttu-id="552f2-125">[AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx)クラスは、(オーディオまたはビデオ) の実際のキャプチャを混在システムを実行する場合を把握するアプリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="552f2-125">The [AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="552f2-126">AppCapture の[GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx)デバイスの実際のキャプチャを混合する場合は null を使用できない API を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="552f2-126">AppCapture's [GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="552f2-127">CapturingChanged イベントが中断されると、アプリの登録を解除しても、それ以外の場合 MRC がブロックされた状態を取得できます。</span><span class="sxs-lookup"><span data-stu-id="552f2-127">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="552f2-128">ベスト プラクティス (HoloLens 固有)</span><span class="sxs-lookup"><span data-stu-id="552f2-128">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="552f2-129">開発者から、追加の作業なしで動作する MRC が必要ですが、アプリの最適な複合現実キャプチャ エクスペリエンスを提供する注意すべきいくつかの点があります。</span><span class="sxs-lookup"><span data-stu-id="552f2-129">MRC is expected to work without additional work from developers, but there are a few things to be aware of to provide the best mixed reality capture experience of your app.</span></span>

<span data-ttu-id="552f2-130">**MRC ブレンドするホログラムのアルファ チャネルを使用して、[カメラ](locatable-camera.md)画像**</span><span class="sxs-lookup"><span data-stu-id="552f2-130">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="552f2-131">最も重要な手順では、アプリが不透明な黒にオフになったときではなく透明な黒色にクリアするかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="552f2-131">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="552f2-132">Unity では、既定では、MixedRealityToolkit これは、非 Unity で開発している場合は、1 つの行を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="552f2-132">In Unity, this is done by default with the MixedRealityToolkit but if you are developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="552f2-133">場合は、アプリが透明な黒を消去しないで MRC で見成果物の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="552f2-133">Here are some of the artifacts you might see in MRC if your app is not clearing to transparent black:</span></span>

<span data-ttu-id="552f2-134">**例エラー**:エッジ (透明な黒色に失敗した) コンテンツの周囲の黒</span><span class="sxs-lookup"><span data-stu-id="552f2-134">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

<span data-ttu-id="552f2-135">**例エラー**:ホログラムのシーン全体の背景が黒で表示されます。</span><span class="sxs-lookup"><span data-stu-id="552f2-135">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="552f2-136">黒の背景で結果が 1 のバック グラウンドのアルファ値を設定</span><span class="sxs-lookup"><span data-stu-id="552f2-136">Setting a background alpha value of 1 results in a black background</span></span>

![黒の背景で結果が 1 のバック グラウンドのアルファ値を設定](images/clearopaqueblack-300px.png)

<span data-ttu-id="552f2-138">**予想される結果**:ホログラムが現実 (透明な黒色に消去する場合に予期される結果) を組み合わせた正しく表示されます。</span><span class="sxs-lookup"><span data-stu-id="552f2-138">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![透明な黒色に消去する場合、予期される結果](images/cleartransparentblack-300px.png)

<span data-ttu-id="552f2-140">**解決方法**:</span><span class="sxs-lookup"><span data-stu-id="552f2-140">**Solution**:</span></span>
* <span data-ttu-id="552f2-141">アルファ値は 0 不透明な黒で表示されている任意のコンテンツを変更します。</span><span class="sxs-lookup"><span data-stu-id="552f2-141">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="552f2-142">アプリが透明な黒色にクリアすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="552f2-142">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="552f2-143">Unity をオフに ID3D11DeiceContext::ClearRenderTargetView() で使用される色を変更する必要があります以外 Unity アプリの場合は、MixedRealityToolkit で自動的に既定値です。</span><span class="sxs-lookup"><span data-stu-id="552f2-143">Unity defaults to clear to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="552f2-144">不透明な黒 (0,0,0,1) ではなく、透明な黒 (0,0,0,0) をオフにすることを確認するには。</span><span class="sxs-lookup"><span data-stu-id="552f2-144">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="552f2-145">資産のアルファ値を調整できるは、場合に、通常にする必要はありませんようになりました。</span><span class="sxs-lookup"><span data-stu-id="552f2-145">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="552f2-146">ほとんどの場合、MRCs を適切にすぐに表示されます。</span><span class="sxs-lookup"><span data-stu-id="552f2-146">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="552f2-147">MRC には、前乗算されたアルファが想定しています。</span><span class="sxs-lookup"><span data-stu-id="552f2-147">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="552f2-148">アルファ値は、MRC キャプチャのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="552f2-148">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="552f2-149">HoloLens で MRC が有効な場合の注意点</span><span class="sxs-lookup"><span data-stu-id="552f2-149">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="552f2-150">次と両方に適用 HoloLens (第 1 世代) HoloLens 2 では、それ以外の場合に記載されていない場合。</span><span class="sxs-lookup"><span data-stu-id="552f2-150">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="552f2-151">システム 30 Hz レンダリングするアプリケーションが調整されます。</span><span class="sxs-lookup"><span data-stu-id="552f2-151">The system will throttle the application to 30Hz rendering.</span></span> <span data-ttu-id="552f2-152">これによって MRC、アプリは、定数の予算の予約を保持する必要があるために実行する余地が作成され、30 fps の MRC レコードのビデオ フレーム レートとも一致</span><span class="sxs-lookup"><span data-stu-id="552f2-152">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30fps</span></span>
* <span data-ttu-id="552f2-153">記録/ストリーミング時に"sparkle"に、デバイスの適切な目でホログラム内容が表示 MRC: テキストが読みにくくなる可能性があり、ホログラム端のギザギザよりが表示される (第 3 のカメラをで選択すると、上でレンダリング**HoloLens 2**を回避できますこのセキュリティの侵害)</span><span class="sxs-lookup"><span data-stu-id="552f2-153">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting-in to 3rd camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="552f2-154">MRC 写真やビデオをアプリケーションの尊重[フォーカス ポイント](focus-point-in-unity.md)場合、アプリケーションが有効になっている、ホログラムを確認するために役立つ正確に配置します。</span><span class="sxs-lookup"><span data-stu-id="552f2-154">MRC photos and videos will respect the application’s [focus point](focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="552f2-155">ビデオ、ホログラムが緩やかに変化にドリフト フォーカス ポイントの深さが大幅に変更された場合に表示されるように、フォーカス ポイントが滑らかです。</span><span class="sxs-lookup"><span data-stu-id="552f2-155">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="552f2-156">フォーカス ポイントから別の深さではホログラムが現実の世界を参照してください以下の例をフォーカス ポイントが 2 つのメートル単位で設定がホログラムが 1 m に配置されてからオフセット表示されます。</span><span class="sxs-lookup"><span data-stu-id="552f2-156">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![世界中に完全に登録されている 2 m 離れたでホログラムが表示されます。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="552f2-159">アプリ内から MRC 機能の統合</span><span class="sxs-lookup"><span data-stu-id="552f2-159">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="552f2-160">複合現実アプリは MRC 写真や、アプリ内からビデオのキャプチャを開始できるし、キャプチャされたコンテンツが格納されることがなく、アプリを使用できる、デバイスの「カメラ ロールです」を。</span><span class="sxs-lookup"><span data-stu-id="552f2-160">Your mixed reality app can initiate MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="552f2-161">カスタム MRC レコーダーを作成したり、組み込みのカメラ キャプチャ UI を利用することができます。</span><span class="sxs-lookup"><span data-stu-id="552f2-161">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="552f2-162">組み込みのカメラ UI で MRC</span><span class="sxs-lookup"><span data-stu-id="552f2-162">MRC with built-in camera UI</span></span>

<span data-ttu-id="552f2-163">開発者が使用できる、 *[カメラ キャプチャ UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 複合現実のユーザーにキャプチャされた写真またはほんの数行のコードでビデオを取得します。</span><span class="sxs-lookup"><span data-stu-id="552f2-163">Developers can use the *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="552f2-164">この API は、組み込み MRC カメラ元となる、ユーザーが写真やビデオにかかるし、アプリにキャプチャされたを返しますの UI を起動します。</span><span class="sxs-lookup"><span data-stu-id="552f2-164">This API launches the built-in MRC camera UI, from which the user can take a photo or video, and returns the resulting capture to your app.</span></span>  <span data-ttu-id="552f2-165">か、独自のカメラ UI を作成する必要がある下位レベル キャプチャ ストリームへのアクセス、Mixed Reality キャプチャのカスタム recorder を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="552f2-165">If you want to create your own camera UI, or need lower-level access to the capture stream, you can create a custom Mixed Reality Capture recorder.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="552f2-166">カスタム MRC レコーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="552f2-166">Creating a custom MRC recorder</span></span>

<span data-ttu-id="552f2-167">ユーザーが写真をトリガーできる常にまたはシステムを使用してビデオ MRC キャプチャ サービス、カスタム カメラ アプリの構築がホログラム MRC と同じように、カメラのストリームに含めるアプリケーションもかまいません。</span><span class="sxs-lookup"><span data-stu-id="552f2-167">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app but include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="552f2-168">これにより、ユーザーの代理としてキャプチャを開始、カスタムの記録、UI をビルドまたは MRC 設定例をいくつかの名前をカスタマイズするアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="552f2-168">This allows the application to kick off captures on behalf of the user, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="552f2-169">**HoloStudio は、MRC 効果を使用してカスタム MRC カメラを追加します**</span><span class="sxs-lookup"><span data-stu-id="552f2-169">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio は、MRC 効果を使用してカスタム MRC カメラを追加します](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="552f2-171">Unity アプリケーションを参照する必要があります[Locatable_camera_in_Unity](locatable-camera-in-unity.md)ホログラムを有効にするプロパティ。</span><span class="sxs-lookup"><span data-stu-id="552f2-171">Unity Applications should see [Locatable_camera_in_Unity](locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="552f2-172">他のアプリケーションを使用してこれを行うことができます、 [Windows メディア キャプチャ Api](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)をカメラを制御し、仮想ホログラムおよびアプリケーションのオーディオ静止画と動画に含める MRC ビデオおよびオーディオ効果を追加します。</span><span class="sxs-lookup"><span data-stu-id="552f2-172">Other applications can do this by using the [Windows Media Capture APIs](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="552f2-173">アプリケーションでは、効果を追加する 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="552f2-173">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="552f2-174">古い API:[Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)</span><span class="sxs-lookup"><span data-stu-id="552f2-174">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)</span></span>
* <span data-ttu-id="552f2-175">新しい Microsoft は、API (動的プロパティを操作できるように、オブジェクトを返します) をお勧めします。[Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) の独自の実装を作成、アプリが必要な[IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx)と[IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx)します。</span><span class="sxs-lookup"><span data-stu-id="552f2-175">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) which require the app create its own implementation of [IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx) and [IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx).</span></span> <span data-ttu-id="552f2-176">サンプルの使用法の MRC 効果のサンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="552f2-176">Please see the MRC effect sample for sample usage.</span></span>

<span data-ttu-id="552f2-177">(これらの名前空間は、Visual Studio によって認識されませんが、文字列がまだ有効なことに注意してください)</span><span class="sxs-lookup"><span data-stu-id="552f2-177">(Note that these namespaces will not be recognized by Visual Studio, but the strings are still valid)</span></span>

<span data-ttu-id="552f2-178">MRC ビデオ特殊効果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span><span class="sxs-lookup"><span data-stu-id="552f2-178">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="552f2-179">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="552f2-179">Property Name</span></span>  |  <span data-ttu-id="552f2-180">種類</span><span class="sxs-lookup"><span data-stu-id="552f2-180">Type</span></span>  |  <span data-ttu-id="552f2-181">既定値</span><span class="sxs-lookup"><span data-stu-id="552f2-181">Default Value</span></span>  |  <span data-ttu-id="552f2-182">説明</span><span class="sxs-lookup"><span data-stu-id="552f2-182">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="552f2-183">StreamType</span><span class="sxs-lookup"><span data-stu-id="552f2-183">StreamType</span></span>  |  <span data-ttu-id="552f2-184">UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))</span><span class="sxs-lookup"><span data-stu-id="552f2-184">UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))</span></span>  |  <span data-ttu-id="552f2-185">1 (VideoRecord)</span><span class="sxs-lookup"><span data-stu-id="552f2-185">1 (VideoRecord)</span></span>  |  <span data-ttu-id="552f2-186">この効果を使用するキャプチャ ストリームについて説明します。</span><span class="sxs-lookup"><span data-stu-id="552f2-186">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="552f2-187">オーディオは、ご利用いただけません。</span><span class="sxs-lookup"><span data-stu-id="552f2-187">Audio is not available.</span></span> | 
|  <span data-ttu-id="552f2-188">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="552f2-188">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="552f2-189">boolean</span><span class="sxs-lookup"><span data-stu-id="552f2-189">boolean</span></span>  |  <span data-ttu-id="552f2-190">TRUE</span><span class="sxs-lookup"><span data-stu-id="552f2-190">TRUE</span></span>  |  <span data-ttu-id="552f2-191">有効またはホログラム ビデオのキャプチャを無効にするフラグします。</span><span class="sxs-lookup"><span data-stu-id="552f2-191">Flag to enable or disable holograms in video capture.</span></span> | 
|  <span data-ttu-id="552f2-192">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="552f2-192">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="552f2-193">boolean</span><span class="sxs-lookup"><span data-stu-id="552f2-193">boolean</span></span>  |  <span data-ttu-id="552f2-194">TRUE</span><span class="sxs-lookup"><span data-stu-id="552f2-194">TRUE</span></span>  |  <span data-ttu-id="552f2-195">有効またはホログラム キャプチャ中に画面の記録のインジケーターを無効にするフラグします。</span><span class="sxs-lookup"><span data-stu-id="552f2-195">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> | 
|  <span data-ttu-id="552f2-196">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="552f2-196">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="552f2-197">boolean</span><span class="sxs-lookup"><span data-stu-id="552f2-197">boolean</span></span>  |  <span data-ttu-id="552f2-198">FALSE</span><span class="sxs-lookup"><span data-stu-id="552f2-198">FALSE</span></span>  |  <span data-ttu-id="552f2-199">有効または、HoloLens の追跡ツールを搭載したビデオ安定化を無効にするフラグします。</span><span class="sxs-lookup"><span data-stu-id="552f2-199">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> | 
|  <span data-ttu-id="552f2-200">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="552f2-200">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="552f2-201">UINT32</span><span class="sxs-lookup"><span data-stu-id="552f2-201">UINT32</span></span>  |  <span data-ttu-id="552f2-202">0</span><span class="sxs-lookup"><span data-stu-id="552f2-202">0</span></span>  |  <span data-ttu-id="552f2-203">ビデオ安定化の使用は履歴フレームの数を設定します。</span><span class="sxs-lookup"><span data-stu-id="552f2-203">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="552f2-204">0 は、待機時間が 0 と能力とパフォーマンスの観点から「無料」ほぼです。</span><span class="sxs-lookup"><span data-stu-id="552f2-204">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="552f2-205">(待機時間とメモリの 15 フレーム) が最高品質には、15 を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="552f2-205">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> | 
|  <span data-ttu-id="552f2-206">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="552f2-206">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="552f2-207">FLOAT</span><span class="sxs-lookup"><span data-stu-id="552f2-207">float</span></span>  |  <span data-ttu-id="552f2-208">0.9 (HoloLens) 1.0 (イマーシブ ヘッドセット)</span><span class="sxs-lookup"><span data-stu-id="552f2-208">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="552f2-209">グローバルの不透明度の係数ホログラムの範囲内で 0.0 (完全に透明) から 1.0 に設定 (完全に不透明)。</span><span class="sxs-lookup"><span data-stu-id="552f2-209">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> | 
|  <span data-ttu-id="552f2-210">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="552f2-210">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="552f2-211">boolean</span><span class="sxs-lookup"><span data-stu-id="552f2-211">boolean</span></span>  |  <span data-ttu-id="552f2-212">FALSE</span><span class="sxs-lookup"><span data-stu-id="552f2-212">FALSE</span></span>  |  <span data-ttu-id="552f2-213">有効または 2d の UWP アプリの表示が保護されたコンテンツがある場合は、空のフレームを返すことを無効にするフラグします。</span><span class="sxs-lookup"><span data-stu-id="552f2-213">Flag to enable or disable returning an empty frame if there is a 2d UWP app showing protected content.</span></span> <span data-ttu-id="552f2-214">このフラグが false と 2d の UWP アプリの場合は保護されている表示をコンテンツの 2d の UWP アプリは、複合現実のキャプチャとヘッドセットの両方で保護されたコンテンツ テクスチャによって置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="552f2-214">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="552f2-215">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="552f2-215">ShowHiddenMesh</span></span>  |  <span data-ttu-id="552f2-216">boolean</span><span class="sxs-lookup"><span data-stu-id="552f2-216">boolean</span></span>  |  <span data-ttu-id="552f2-217">FALSE</span><span class="sxs-lookup"><span data-stu-id="552f2-217">FALSE</span></span>  |  <span data-ttu-id="552f2-218">有効または無効 holographic のカメラの非表示の領域のメッシュを表示して、隣接するコンテンツにフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="552f2-218">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |

<span data-ttu-id="552f2-219">MRC オーディオ効果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span><span class="sxs-lookup"><span data-stu-id="552f2-219">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

<table>
<tr>
<th><span data-ttu-id="552f2-220">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="552f2-220">Property Name</span></span></th>
<th><span data-ttu-id="552f2-221">種類</span><span class="sxs-lookup"><span data-stu-id="552f2-221">Type</span></span></th>
<th><span data-ttu-id="552f2-222">既定値</span><span class="sxs-lookup"><span data-stu-id="552f2-222">Default Value</span></span></th>
<th><span data-ttu-id="552f2-223">説明</span><span class="sxs-lookup"><span data-stu-id="552f2-223">Description</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="552f2-224">MixerMode</span><span class="sxs-lookup"><span data-stu-id="552f2-224">MixerMode</span></span></td>
<td><span data-ttu-id="552f2-225">UINT32</span><span class="sxs-lookup"><span data-stu-id="552f2-225">UINT32</span></span></td>
<td><span data-ttu-id="552f2-226">2</span><span class="sxs-lookup"><span data-stu-id="552f2-226">2</span></span></td>
<td>
<ul>
<li><span data-ttu-id="552f2-227">0 :マイクのオーディオのみ</span><span class="sxs-lookup"><span data-stu-id="552f2-227">0 : Mic audio only</span></span></li>
<li><span data-ttu-id="552f2-228">1 :システム オーディオのみ</span><span class="sxs-lookup"><span data-stu-id="552f2-228">1 : System audio only</span></span></li>
<li><span data-ttu-id="552f2-229">2 :Mic およびシステム オーディオ</span><span class="sxs-lookup"><span data-stu-id="552f2-229">2 : Mic and System audio</span></span></li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="552f2-230">同時 MRC の制限事項</span><span class="sxs-lookup"><span data-stu-id="552f2-230">Simultaneous MRC limitations</span></span>

<span data-ttu-id="552f2-231">MRC にアクセスすると同時に複数のアプリに関する制限があります。</span><span class="sxs-lookup"><span data-stu-id="552f2-231">There are certain limitations around multiple apps accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="552f2-232">写真/ビデオ カメラへのアクセス</span><span class="sxs-lookup"><span data-stu-id="552f2-232">Photo/video camera access</span></span>

<span data-ttu-id="552f2-233">写真/ビデオのカメラは、同時にアクセスできるプロセスの数に制限されます。</span><span class="sxs-lookup"><span data-stu-id="552f2-233">The photo/video camera is limited to the number of processes that can access it at the same time.</span></span> <span data-ttu-id="552f2-234">プロセスを記録中にビデオやその他のプロセスの写真の撮影写真とビデオのカメラの取得に失敗します。</span><span class="sxs-lookup"><span data-stu-id="552f2-234">While a process is recording video or taking a photo any other process will fail to acquire the photo/video camera.</span></span> <span data-ttu-id="552f2-235">(これは混合の実際のキャプチャと標準のフォトとビデオのキャプチャの両方に適用されます)</span><span class="sxs-lookup"><span data-stu-id="552f2-235">(this applies to both Mixed Reality Capture and standard photo/video capture)</span></span>

<span data-ttu-id="552f2-236">Windows 10 April 2018 Update では、この制限は適用されません組み込み MRC カメラ UI を使用する写真とビデオのカメラを使用して、アプリが開始した後に、写真やビデオを実行する場合。</span><span class="sxs-lookup"><span data-stu-id="552f2-236">With the Windows 10 April 2018 Update, this restriction does not apply if the built-in MRC camera UI is used to take a photo or a video after an app has started using the photo/video camera.</span></span> <span data-ttu-id="552f2-237">この場合、解像度と組み込みの MRC カメラ UI のフレーム レートが標準値から低下する可能性です。</span><span class="sxs-lookup"><span data-stu-id="552f2-237">When this happens, the resolution and framerate of the built-in MRC camera UI might be reduced from its normal values.</span></span>

<span data-ttu-id="552f2-238">Windows 10 年 2018年 10 月 Update では、この制限は適用されません Miracast を介して MRC をストリーミングします。</span><span class="sxs-lookup"><span data-stu-id="552f2-238">With the Windows 10 October 2018 Update, this restriction does not apply to streaming MRC over Miracast.</span></span>

#### <a name="mrc-access"></a><span data-ttu-id="552f2-239">MRC アクセス</span><span class="sxs-lookup"><span data-stu-id="552f2-239">MRC access</span></span>

<span data-ttu-id="552f2-240">Windows 10 April 2018 Update が複数のアプリ (ただし、写真とビデオのカメラへのアクセスをまだ制限) MRC ストリームへのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="552f2-240">With the Windows 10 April 2018 Update, there is no longer a limitation around multiple apps accessing the MRC stream (however, the access to the photo/video camera still has limitations).</span></span>

<span data-ttu-id="552f2-241">前に、Windows 10 April 2018 Update、アプリのカスタム MRC レコーダーでは、システム MRC (写真をキャプチャ、キャプチャするビデオ、または、Windows Device Portal からのストリーミング) で相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="552f2-241">Previous to the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="552f2-242">関連項目</span><span class="sxs-lookup"><span data-stu-id="552f2-242">See also</span></span>
* [<span data-ttu-id="552f2-243">複合現実のキャプチャ</span><span class="sxs-lookup"><span data-stu-id="552f2-243">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="552f2-244">Spectator ビュー</span><span class="sxs-lookup"><span data-stu-id="552f2-244">Spectator view</span></span>](spectator-view.md)
