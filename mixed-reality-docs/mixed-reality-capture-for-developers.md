---
title: 開発者向けの実際のキャプチャの混在
description: 開発者の複合現実のベスト プラクティスをキャプチャします。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、写真、ビデオ、キャプチャ、カメラ
ms.openlocfilehash: d1675d2d6c74c6d15ca245a66719e00f2a7c2111
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694362"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="fcdf0-104">開発者向けの実際のキャプチャの混在</span><span class="sxs-lookup"><span data-stu-id="fcdf0-104">Mixed reality capture for developers</span></span>

> <span data-ttu-id="fcdf0-105">[注!]参照してください[PV カメラからレンダリング](#render-from-the-pv-camera-opt-in)下 HoloLens 2 のガイダンスについては新しい MRC 機能。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-105">[NOTE!] See [Render from the PV camera](#render-from-the-pv-camera-opt-in) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="fcdf0-106">ユーザーがかかる場合がありますので、[実際のキャプチャを混合](mixed-reality-capture.md)(MRC) 写真またはビデオをいつでも、いくつか点が、アプリケーションを開発するときに点に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-106">Since a user could take a [mixed reality capture](mixed-reality-capture.md) (MRC) photo or video at any time, there are a few things that you should keep in mind when developing your application.</span></span> <span data-ttu-id="fcdf0-107">これには、MRC 画質と MRCs をキャプチャ中にシステムの変更に応答するためのベスト プラクティスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-107">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="fcdf0-108">開発者は、それぞれのアプリに、複合現実のキャプチャと挿入を統合できますもシームレスにします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-108">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="fcdf0-109">MRC HoloLens (第 1 世代) では、ビデオをサポートしており、720 p、最大の写真を MRC HoloLens 2 の 4 K 解像度を最大 1080p と写真のビデオをサポートします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-109">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="fcdf0-110">品質 MRC の重要性</span><span class="sxs-lookup"><span data-stu-id="fcdf0-110">The importance of quality MRC</span></span>

<span data-ttu-id="fcdf0-111">複合現実にキャプチャされた写真とビデオが初めてユーザーがアプリの必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-111">Mixed reality captured photos and videos are likely the first exposure a user will have of your app.</span></span> <span data-ttu-id="fcdf0-112">Microsoft Store のページで、またはソーシャル ネットワーク上で MRCs を共有する他のユーザーから複合現実のスクリーン ショットとしてかどうか。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-112">Whether as mixed reality screenshots on your Microsoft Store page or from other users sharing MRCs on social networks.</span></span> <span data-ttu-id="fcdf0-113">MRC を使用するには、アプリのデモ、ユーザーを教育する、その混合世界の相互作用を共有するユーザーに促すユーザー調査および問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-113">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="fcdf0-114">MRC がアプリに与える影響</span><span class="sxs-lookup"><span data-stu-id="fcdf0-114">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="fcdf0-115">アプリで MRC を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-115">Enabling MRC in your app</span></span>

<span data-ttu-id="fcdf0-116">既定では、アプリは複合現実のキャプチャを実行するユーザーを有効にする何もありません。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-116">By default, an app does not have to do anything to enable users to take mixed reality captures.</span></span>

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a><span data-ttu-id="fcdf0-117">アプリで MRC の強化された配置を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-117">Enabling improved alignment for MRC in your app</span></span>

<span data-ttu-id="fcdf0-118">既定では、複合現実のキャプチャは、写真/ビデオ (PV) カメラで適切な目の holographic の出力を結合します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-118">By default, mixed reality capture combines the right eye's holographic output with the photo/video (PV) camera.</span></span> <span data-ttu-id="fcdf0-119">これら 2 つのソースは、フォーカス ポイントが現在実行中の没入型のアプリで設定を使用して結合されます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-119">These two sources are combined using the focus point set by the currently running immersive app.</span></span>

<span data-ttu-id="fcdf0-120">これは、フォーカス平面外ホログラムがも (PV カメラと適切なディスプレイの物理的な距離) により配置できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-120">This means that holograms outside the focus plane won't align as well (due to the physical distance between the PV camera and the right display).</span></span>

#### <a name="set-the-focus-point"></a><span data-ttu-id="fcdf0-121">フォーカス ポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-121">Set the focus point</span></span>

<span data-ttu-id="fcdf0-122">(HoloLens) に体感型アプリを設定する必要があります、[フォーカス ポイント](focus-point-in-unity.md)の目的の場所にある場合は、安定化平面。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-122">Immersive apps (on HoloLens) should set the [focus point](focus-point-in-unity.md) of where they want their stabilization plane to be.</span></span> <span data-ttu-id="fcdf0-123">これにより、複合現実のキャプチャとヘッドセットの両方で位置が最適です。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-123">This ensures the best alignment in both the headset and in mixed reality capture.</span></span>

<span data-ttu-id="fcdf0-124">フォーカス ポイントが設定されていない場合は、安定化の平面が既定 2 つのメーターになります。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-124">If a focus point is not set, the stabilization plane will default to two meters.</span></span>

#### <a name="render-from-the-pv-camera-opt-in"></a><span data-ttu-id="fcdf0-125">(オプトイン) PV カメラからレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-125">Render from the PV camera (opt-in)</span></span>

<span data-ttu-id="fcdf0-126">HoloLens 2 没入型のアプリに機能が追加**PV カメラからレンダリング**複合現実のキャプチャの実行中にします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-126">HoloLens 2 adds the ability for an immersive app to **render from the PV camera** while mixed reality capture is running.</span></span> <span data-ttu-id="fcdf0-127">アプリが、追加のレンダリングを正しくサポートするためには、アプリは、この機能にオプトインするがします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-127">To ensure the app supports the additional render correctly, the app has to opt-in to this functionality.</span></span>

<span data-ttu-id="fcdf0-128">既定の MRC エクスペリエンスを次の機能強化を PV カメラのプランから表示します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-128">Render from the PV camera offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="fcdf0-129">ホログラム配置、物理環境と (ほぼ相互作用) を手にする必要がありますで正確なすべての既定 MRC でわかる場合があります、フォーカス ポイント以外の距離でオフセットになくの距離。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-129">Hologram alignment to both your physical environment and hands (for near interactions) should be accurate at all distances, instead of having an offset at distances other than the focus point as you might see in the default MRC.</span></span>
* <span data-ttu-id="fcdf0-130">MRC 出力ホログラムを表示するために使用されないよう、ヘッドセットで適切な目を侵害されるは。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-130">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

<span data-ttu-id="fcdf0-131">PV カメラからのレンダリングを有効にする 3 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-131">There are three steps to enable rendering from the PV camera:</span></span>
1. <span data-ttu-id="fcdf0-132">PhotoVideoCamera HolographicViewConfiguration を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-132">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>
2. <span data-ttu-id="fcdf0-133">追加の HolographicCamera レンダリングを処理します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-133">Handle the additional HolographicCamera render</span></span>
3. <span data-ttu-id="fcdf0-134">この追加 HolographicCamera から、シェーダーとコード レンダリング正しくを確認します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-134">Verify your shaders and code render correctly from this additional HolographicCamera</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a><span data-ttu-id="fcdf0-135">PhotoVideoCamera HolographicViewConfiguration を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-135">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>

<span data-ttu-id="fcdf0-136">オプトイン アプリだけができます、PhotoVideoCamera の[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span><span class="sxs-lookup"><span data-stu-id="fcdf0-136">To opt-in, an app simply enables the PhotoVideoCamera's [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span></span>
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a><span data-ttu-id="fcdf0-137">DirectX で追加 HolographicCamera レンダリングを処理します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-137">Handle the additional HolographicCamera render in DirectX</span></span>

<span data-ttu-id="fcdf0-138">PV カメラから表示するためにオプトインがアプリと、複合現実のキャプチャを開始します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-138">When the app has opt-in to render from the PV camera and mixed reality capture starts:</span></span>
1. <span data-ttu-id="fcdf0-139">HolographicSpace の CameraAdded イベントが起動されます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-139">HolographicSpace's CameraAdded event will fire.</span></span> <span data-ttu-id="fcdf0-140">この時点で、アプリがカメラを処理できない場合、このイベントを延期できます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-140">This event can be deferred if the app cannot handle the camera at this time.</span></span>
2. <span data-ttu-id="fcdf0-141">イベントが完了した (および未処理の遅延はありません)、HolographicCamera 次 HolographicFrame の AddedCameras 一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-141">Once the event has completed (and there are no outstanding deferrals) the HolographicCamera will appear in the next HolographicFrame's AddedCameras list.</span></span>

<span data-ttu-id="fcdf0-142">ときに、複合現実キャプチャは停止します (または、アプリは、複合現実のキャプチャの実行中に、構成の表示を無効にします): HolographicCamera が次 HolographicFrame の RemovedCameras 一覧に表示され、HolographicSpace の CameraRemoved イベントには起動します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-142">When mixed reality capture stops (or if the app disables the view configuration while mixed reality capture is running): the HolographicCamera will appear in the next HolographicFrame's RemovedCameras list and the HolographicSpace's CameraRemoved event will fire.</span></span>

<span data-ttu-id="fcdf0-143">A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) HolographicCamera にカメラが属している構成を識別できるようにするプロパティが追加されました。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-143">A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) property has been added to HolographicCamera to help identify the configuration a camera belongs to.</span></span>

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a><span data-ttu-id="fcdf0-144">Unity で追加 HolographicCamera レンダリングを処理します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-144">Handle the additional HolographicCamera render in Unity</span></span>

>[!NOTE]
> <span data-ttu-id="fcdf0-145">PV カメラから表示するために unity のサポートは、開発中、使用できません、まだです。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-145">Unity support to render from the PV camera is under development and can't be used, yet.</span></span> <span data-ttu-id="fcdf0-146">PV カメラからのレンダリングのサポートにより Unity のビルドが利用可能な場合は、このドキュメントが更新されます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-146">This documentation will be updated when a build of Unity with support for rendering from the PV camera is available.</span></span>

##### <a name="verify-shaders-and-code-support-additional-cameras"></a><span data-ttu-id="fcdf0-147">シェーダーを確認し、コードの追加のカメラのサポート</span><span class="sxs-lookup"><span data-stu-id="fcdf0-147">Verify shaders and code support additional cameras</span></span>

<span data-ttu-id="fcdf0-148">複合現実のキャプチャと異常な配置や不足しているコンテンツは、パフォーマンスの問題のチェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-148">Run a mixed reality capture and check for unusual alignment, missing content, or performance issues.</span></span> <span data-ttu-id="fcdf0-149">シェーダーと適切なコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-149">Update shaders and code as appropriate.</span></span>

<span data-ttu-id="fcdf0-150">特定のシーンを追加カメラへのレンダリングをサポートできない場合は、それらの中に PhotoVideoCamera の HolographicViewConfiguration を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-150">If there are certain scenes that cannot support rendering to an additional camera, you can disable the PhotoVideoCamera's HolographicViewConfiguration during them.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="fcdf0-151">アプリで MRC を無効にします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-151">Disabling MRC in your app</span></span>

#### <a name="2d-app"></a><span data-ttu-id="fcdf0-152">2D アプリ</span><span class="sxs-lookup"><span data-stu-id="fcdf0-152">2D app</span></span>

<span data-ttu-id="fcdf0-153">2D アプリは、複合現実のキャプチャがで実行されている場合に隠されて、ビジュアル コンテンツを選択できます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-153">2D apps can choose to have their visual content obscured when mixed reality capture is running by:</span></span>
* <span data-ttu-id="fcdf0-154">存在する、 [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)フラグ</span><span class="sxs-lookup"><span data-stu-id="fcdf0-154">Present with the [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) flag</span></span>
* <span data-ttu-id="fcdf0-155">使ったアプリのスワップ チェーンを作成、 [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)フラグ</span><span class="sxs-lookup"><span data-stu-id="fcdf0-155">Create the app's swap chain with the [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) flag</span></span>
* <span data-ttu-id="fcdf0-156">Windows 10 では 2019 設定の更新、ApplicationView の[IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span><span class="sxs-lookup"><span data-stu-id="fcdf0-156">With the Windows 10 May 2019 Update, setting ApplicationView's [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span></span>

#### <a name="immersive-app"></a><span data-ttu-id="fcdf0-157">体感型アプリ</span><span class="sxs-lookup"><span data-stu-id="fcdf0-157">Immersive app</span></span>

<span data-ttu-id="fcdf0-158">体感型アプリは、ビジュアル コンテンツを複合現実のキャプチャから除外できます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-158">Immersive apps can choose to have their visual content excluded from mixed reality capture by:</span></span>
* <span data-ttu-id="fcdf0-159">設定 HolographicCameraRenderingParameter の[IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled)複合現実で関連するフレームのキャプチャを無効にするには</span><span class="sxs-lookup"><span data-stu-id="fcdf0-159">Setting HolographicCameraRenderingParameter's [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) to disable mixed reality capture for its associated frame</span></span>
* <span data-ttu-id="fcdf0-160">設定 HolographicCamera の[IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled)複合現実での関連付けられている holographic カメラ キャプチャを無効にするには</span><span class="sxs-lookup"><span data-stu-id="fcdf0-160">Setting HolographicCamera's [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) to disable mixed reality capture for its associated holographic camera</span></span>

#### <a name="password-keyboard"></a><span data-ttu-id="fcdf0-161">パスワードのキーボード</span><span class="sxs-lookup"><span data-stu-id="fcdf0-161">Password Keyboard</span></span>

<span data-ttu-id="fcdf0-162">また、Windows 10 で 2019年更新ことが、ビジュアル コンテンツはパスワードまたは pin のキーボードが表示されている場合、自動的に複合現実のキャプチャから除外します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-162">With the Windows 10 May 2019 Update, visual content is automatically excluded from mixed reality capture when a password or pin keyboard is visible.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="fcdf0-163">MRC がアクティブな場合を知る</span><span class="sxs-lookup"><span data-stu-id="fcdf0-163">Knowing when MRC is active</span></span>

<span data-ttu-id="fcdf0-164">[AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture)クラスは、(オーディオまたはビデオ) の実際のキャプチャを混在システムを実行する場合を把握するアプリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-164">The [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="fcdf0-165">AppCapture の[GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview)デバイスの実際のキャプチャを混合する場合は null を使用できない API を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-165">AppCapture's [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="fcdf0-166">CapturingChanged イベントが中断されると、アプリの登録を解除しても、それ以外の場合 MRC がブロックされた状態を取得できます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-166">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="fcdf0-167">ベスト プラクティス (HoloLens 固有)</span><span class="sxs-lookup"><span data-stu-id="fcdf0-167">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="fcdf0-168">開発者から、追加の作業なしで動作する MRC が必要ですが、アプリの最適な複合現実キャプチャ エクスペリエンスを提供する注意すべきいくつかの点があります。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-168">MRC is expected to work without additional work from developers, but there are a few things to be aware of to provide the best mixed reality capture experience of your app.</span></span>

<span data-ttu-id="fcdf0-169">**MRC ブレンドするホログラムのアルファ チャネルを使用して、[カメラ](locatable-camera.md)画像**</span><span class="sxs-lookup"><span data-stu-id="fcdf0-169">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="fcdf0-170">最も重要な手順では、アプリが不透明な黒にオフになったときではなく透明な黒色にクリアするかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-170">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="fcdf0-171">Unity では、既定では、MixedRealityToolkit これは、非 Unity で開発している場合は、1 つの行を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-171">In Unity, this is done by default with the MixedRealityToolkit but if you are developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="fcdf0-172">場合は、アプリが透明な黒を消去しないで MRC で見成果物の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-172">Here are some of the artifacts you might see in MRC if your app is not clearing to transparent black:</span></span>

<span data-ttu-id="fcdf0-173">**例エラー**:エッジ (透明な黒色に失敗した) コンテンツの周囲の黒</span><span class="sxs-lookup"><span data-stu-id="fcdf0-173">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

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

<span data-ttu-id="fcdf0-174">**例エラー**:ホログラムのシーン全体の背景が黒で表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-174">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="fcdf0-175">黒の背景で結果が 1 のバック グラウンドのアルファ値を設定</span><span class="sxs-lookup"><span data-stu-id="fcdf0-175">Setting a background alpha value of 1 results in a black background</span></span>

![黒の背景で結果が 1 のバック グラウンドのアルファ値を設定](images/clearopaqueblack-300px.png)

<span data-ttu-id="fcdf0-177">**予想される結果**:ホログラムが現実 (透明な黒色に消去する場合に予期される結果) を組み合わせた正しく表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-177">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![透明な黒色に消去する場合、予期される結果](images/cleartransparentblack-300px.png)

<span data-ttu-id="fcdf0-179">**解決方法**:</span><span class="sxs-lookup"><span data-stu-id="fcdf0-179">**Solution**:</span></span>
* <span data-ttu-id="fcdf0-180">アルファ値は 0 不透明な黒で表示されている任意のコンテンツを変更します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-180">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="fcdf0-181">アプリが透明な黒色にクリアすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-181">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="fcdf0-182">Unity をオフに ID3D11DeiceContext::ClearRenderTargetView() で使用される色を変更する必要があります以外 Unity アプリの場合は、MixedRealityToolkit で自動的に既定値です。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-182">Unity defaults to clear to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="fcdf0-183">不透明な黒 (0,0,0,1) ではなく、透明な黒 (0,0,0,0) をオフにすることを確認するには。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-183">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="fcdf0-184">資産のアルファ値を調整できるは、場合に、通常にする必要はありませんようになりました。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-184">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="fcdf0-185">ほとんどの場合、MRCs を適切にすぐに表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-185">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="fcdf0-186">MRC には、前乗算されたアルファが想定しています。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-186">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="fcdf0-187">アルファ値は、MRC キャプチャのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-187">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="fcdf0-188">HoloLens で MRC が有効な場合の注意点</span><span class="sxs-lookup"><span data-stu-id="fcdf0-188">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="fcdf0-189">次と両方に適用 HoloLens (第 1 世代) HoloLens 2 では、それ以外の場合に記載されていない場合。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-189">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="fcdf0-190">システム 30 Hz レンダリングするアプリケーションが調整されます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-190">The system will throttle the application to 30Hz rendering.</span></span> <span data-ttu-id="fcdf0-191">これによって MRC、アプリは、定数の予算の予約を保持する必要があるために実行する余地が作成され、30 fps の MRC レコードのビデオ フレーム レートとも一致</span><span class="sxs-lookup"><span data-stu-id="fcdf0-191">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30fps</span></span>
* <span data-ttu-id="fcdf0-192">記録/ストリーミング時に"sparkle"に、デバイスの適切な目でホログラム内容が表示 MRC: テキストが読みにくくなる可能性があり、ホログラム端のギザギザよりが表示される (第 3 のカメラをで選択すると、上でレンダリング**HoloLens 2**を回避できますこのセキュリティの侵害)</span><span class="sxs-lookup"><span data-stu-id="fcdf0-192">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting-in to 3rd camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="fcdf0-193">MRC 写真やビデオをアプリケーションの尊重[フォーカス ポイント](focus-point-in-unity.md)場合、アプリケーションが有効になっている、ホログラムを確認するために役立つ正確に配置します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-193">MRC photos and videos will respect the application’s [focus point](focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="fcdf0-194">ビデオ、ホログラムが緩やかに変化にドリフト フォーカス ポイントの深さが大幅に変更された場合に表示されるように、フォーカス ポイントが滑らかです。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-194">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="fcdf0-195">フォーカス ポイントから別の深さではホログラムが現実の世界を参照してください以下の例をフォーカス ポイントが 2 つのメートル単位で設定がホログラムが 1 m に配置されてからオフセット表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-195">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![世界中に完全に登録されている 2 m 離れたでホログラムが表示されます。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="fcdf0-198">アプリ内から MRC 機能の統合</span><span class="sxs-lookup"><span data-stu-id="fcdf0-198">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="fcdf0-199">複合現実アプリは MRC 写真や、アプリ内からビデオのキャプチャを開始できるし、キャプチャされたコンテンツが格納されることがなく、アプリを使用できる、デバイスの「カメラ ロールです」を。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-199">Your mixed reality app can initiate MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="fcdf0-200">カスタム MRC レコーダーを作成したり、組み込みのカメラ キャプチャ UI を利用することができます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-200">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="fcdf0-201">組み込みのカメラ UI で MRC</span><span class="sxs-lookup"><span data-stu-id="fcdf0-201">MRC with built-in camera UI</span></span>

<span data-ttu-id="fcdf0-202">開発者が使用できる、 *[カメラ キャプチャ UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 複合現実のユーザーにキャプチャされた写真またはほんの数行のコードでビデオを取得します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-202">Developers can use the *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="fcdf0-203">この API は、組み込み MRC カメラ元となる、ユーザーが写真やビデオにかかるし、アプリにキャプチャされたを返しますの UI を起動します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-203">This API launches the built-in MRC camera UI, from which the user can take a photo or video, and returns the resulting capture to your app.</span></span>  <span data-ttu-id="fcdf0-204">か、独自のカメラ UI を作成する必要がある下位レベル キャプチャ ストリームへのアクセス、Mixed Reality キャプチャのカスタム recorder を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-204">If you want to create your own camera UI, or need lower-level access to the capture stream, you can create a custom Mixed Reality Capture recorder.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="fcdf0-205">カスタム MRC レコーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-205">Creating a custom MRC recorder</span></span>

<span data-ttu-id="fcdf0-206">ユーザーが写真をトリガーできる常にまたはシステムを使用してビデオ MRC キャプチャ サービス、カスタム カメラ アプリの構築がホログラム MRC と同じように、カメラのストリームに含めるアプリケーションもかまいません。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-206">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app but include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="fcdf0-207">これにより、ユーザーの代理としてキャプチャを開始、カスタムの記録、UI をビルドまたは MRC 設定例をいくつかの名前をカスタマイズするアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-207">This allows the application to kick off captures on behalf of the user, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="fcdf0-208">**HoloStudio は、MRC 効果を使用してカスタム MRC カメラを追加します**</span><span class="sxs-lookup"><span data-stu-id="fcdf0-208">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio は、MRC 効果を使用してカスタム MRC カメラを追加します](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="fcdf0-210">Unity アプリケーションを参照する必要があります[Locatable_camera_in_Unity](locatable-camera-in-unity.md)ホログラムを有効にするプロパティ。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-210">Unity Applications should see [Locatable_camera_in_Unity](locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="fcdf0-211">他のアプリケーションを使用してこれを行うことができます、 [Windows メディア キャプチャ Api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture)をカメラを制御し、仮想ホログラムおよびアプリケーションのオーディオ静止画と動画に含める MRC ビデオおよびオーディオ効果を追加します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-211">Other applications can do this by using the [Windows Media Capture APIs](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="fcdf0-212">アプリケーションでは、効果を追加する 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-212">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="fcdf0-213">古い API:[Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span><span class="sxs-lookup"><span data-stu-id="fcdf0-213">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span></span>
* <span data-ttu-id="fcdf0-214">新しい Microsoft は、API (動的プロパティを操作できるように、オブジェクトを返します) をお勧めします。[Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) の独自の実装を作成、アプリが必要な[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)と[IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-214">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) which require the app create its own implementation of [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) and [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition).</span></span> <span data-ttu-id="fcdf0-215">サンプルの使用法の MRC 効果のサンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-215">Please see the MRC effect sample for sample usage.</span></span>

>[!NOTE]
> <span data-ttu-id="fcdf0-216">Windows.Media.MixedRealityCapture 名前空間は、Visual Studio によって認識されませんが、文字列が現在も有効です。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-216">The Windows.Media.MixedRealityCapture namespace will not be recognized by Visual Studio, but the strings are still valid.</span></span>

<span data-ttu-id="fcdf0-217">MRC ビデオ特殊効果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span><span class="sxs-lookup"><span data-stu-id="fcdf0-217">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="fcdf0-218">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="fcdf0-218">Property Name</span></span>  |  <span data-ttu-id="fcdf0-219">種類</span><span class="sxs-lookup"><span data-stu-id="fcdf0-219">Type</span></span>  |  <span data-ttu-id="fcdf0-220">既定値</span><span class="sxs-lookup"><span data-stu-id="fcdf0-220">Default Value</span></span>  |  <span data-ttu-id="fcdf0-221">説明</span><span class="sxs-lookup"><span data-stu-id="fcdf0-221">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="fcdf0-222">StreamType</span><span class="sxs-lookup"><span data-stu-id="fcdf0-222">StreamType</span></span>  |  <span data-ttu-id="fcdf0-223">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span><span class="sxs-lookup"><span data-stu-id="fcdf0-223">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span></span>  |  <span data-ttu-id="fcdf0-224">1 (VideoRecord)</span><span class="sxs-lookup"><span data-stu-id="fcdf0-224">1 (VideoRecord)</span></span>  |  <span data-ttu-id="fcdf0-225">この効果を使用するキャプチャ ストリームについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-225">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="fcdf0-226">オーディオは、ご利用いただけません。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-226">Audio is not available.</span></span> | 
|  <span data-ttu-id="fcdf0-227">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="fcdf0-227">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="fcdf0-228">boolean</span><span class="sxs-lookup"><span data-stu-id="fcdf0-228">boolean</span></span>  |  <span data-ttu-id="fcdf0-229">TRUE</span><span class="sxs-lookup"><span data-stu-id="fcdf0-229">TRUE</span></span>  |  <span data-ttu-id="fcdf0-230">有効またはホログラム ビデオのキャプチャを無効にするフラグします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-230">Flag to enable or disable holograms in video capture.</span></span> | 
|  <span data-ttu-id="fcdf0-231">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="fcdf0-231">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="fcdf0-232">boolean</span><span class="sxs-lookup"><span data-stu-id="fcdf0-232">boolean</span></span>  |  <span data-ttu-id="fcdf0-233">TRUE</span><span class="sxs-lookup"><span data-stu-id="fcdf0-233">TRUE</span></span>  |  <span data-ttu-id="fcdf0-234">有効またはホログラム キャプチャ中に画面の記録のインジケーターを無効にするフラグします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-234">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> | 
|  <span data-ttu-id="fcdf0-235">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="fcdf0-235">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="fcdf0-236">boolean</span><span class="sxs-lookup"><span data-stu-id="fcdf0-236">boolean</span></span>  |  <span data-ttu-id="fcdf0-237">FALSE</span><span class="sxs-lookup"><span data-stu-id="fcdf0-237">FALSE</span></span>  |  <span data-ttu-id="fcdf0-238">有効または、HoloLens の追跡ツールを搭載したビデオ安定化を無効にするフラグします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-238">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> | 
|  <span data-ttu-id="fcdf0-239">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="fcdf0-239">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="fcdf0-240">UINT32</span><span class="sxs-lookup"><span data-stu-id="fcdf0-240">UINT32</span></span>  |  <span data-ttu-id="fcdf0-241">0</span><span class="sxs-lookup"><span data-stu-id="fcdf0-241">0</span></span>  |  <span data-ttu-id="fcdf0-242">ビデオ安定化の使用は履歴フレームの数を設定します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-242">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="fcdf0-243">0 は、待機時間が 0 と能力とパフォーマンスの観点から「無料」ほぼです。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-243">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="fcdf0-244">(待機時間とメモリの 15 フレーム) が最高品質には、15 を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-244">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> | 
|  <span data-ttu-id="fcdf0-245">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="fcdf0-245">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="fcdf0-246">FLOAT</span><span class="sxs-lookup"><span data-stu-id="fcdf0-246">float</span></span>  |  <span data-ttu-id="fcdf0-247">0.9 (HoloLens) 1.0 (イマーシブ ヘッドセット)</span><span class="sxs-lookup"><span data-stu-id="fcdf0-247">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="fcdf0-248">グローバルの不透明度の係数ホログラムの範囲内で 0.0 (完全に透明) から 1.0 に設定 (完全に不透明)。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-248">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> | 
|  <span data-ttu-id="fcdf0-249">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="fcdf0-249">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="fcdf0-250">boolean</span><span class="sxs-lookup"><span data-stu-id="fcdf0-250">boolean</span></span>  |  <span data-ttu-id="fcdf0-251">FALSE</span><span class="sxs-lookup"><span data-stu-id="fcdf0-251">FALSE</span></span>  |  <span data-ttu-id="fcdf0-252">有効または 2d の UWP アプリの表示が保護されたコンテンツがある場合は、空のフレームを返すことを無効にするフラグします。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-252">Flag to enable or disable returning an empty frame if there is a 2d UWP app showing protected content.</span></span> <span data-ttu-id="fcdf0-253">このフラグが false と 2d の UWP アプリの場合は保護されている表示をコンテンツの 2d の UWP アプリは、複合現実のキャプチャとヘッドセットの両方で保護されたコンテンツ テクスチャによって置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-253">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="fcdf0-254">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="fcdf0-254">ShowHiddenMesh</span></span>  |  <span data-ttu-id="fcdf0-255">boolean</span><span class="sxs-lookup"><span data-stu-id="fcdf0-255">boolean</span></span>  |  <span data-ttu-id="fcdf0-256">FALSE</span><span class="sxs-lookup"><span data-stu-id="fcdf0-256">FALSE</span></span>  |  <span data-ttu-id="fcdf0-257">有効または無効 holographic のカメラの非表示の領域のメッシュを表示して、隣接するコンテンツにフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-257">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |
| <span data-ttu-id="fcdf0-258">OutputSize</span><span class="sxs-lookup"><span data-stu-id="fcdf0-258">OutputSize</span></span> | <span data-ttu-id="fcdf0-259">サイズ</span><span class="sxs-lookup"><span data-stu-id="fcdf0-259">Size</span></span> | <span data-ttu-id="fcdf0-260">0, 0</span><span class="sxs-lookup"><span data-stu-id="fcdf0-260">0, 0</span></span> | <span data-ttu-id="fcdf0-261">ビデオ安定化のトリミング後の目的の出力サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-261">Set the desired output size after cropping for video stabilization.</span></span> <span data-ttu-id="fcdf0-262">既定のトリミングのサイズは、0 またはサイズが無効な出力が指定されている場合に選択されます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-262">A default crop size is chosen if 0 or an invalid output size is specified.</span></span> |
| <span data-ttu-id="fcdf0-263">PreferredHologramPerspective</span><span class="sxs-lookup"><span data-stu-id="fcdf0-263">PreferredHologramPerspective</span></span> | <span data-ttu-id="fcdf0-264">UINT32</span><span class="sxs-lookup"><span data-stu-id="fcdf0-264">UINT32</span></span> | <span data-ttu-id="fcdf0-265">1 (PhotoVideoCamera)</span><span class="sxs-lookup"><span data-stu-id="fcdf0-265">1 (PhotoVideoCamera)</span></span> | <span data-ttu-id="fcdf0-266">列挙型は、カメラのホログラフィック ビュー構成をキャプチャするかを示すために使用します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-266">Enum used to indicate which holographic camera view configuration should be captured.</span></span> <span data-ttu-id="fcdf0-267">写真/ビデオ カメラから表示するために、アプリを求められません 0 の (表示) 場合の設定</span><span class="sxs-lookup"><span data-stu-id="fcdf0-267">Setting 0 (Display) means that the app won't be asked to render from the photo/video camera</span></span> |

<span data-ttu-id="fcdf0-268">MRC オーディオ効果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span><span class="sxs-lookup"><span data-stu-id="fcdf0-268">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

<table>
<tr>
<th><span data-ttu-id="fcdf0-269">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="fcdf0-269">Property Name</span></span></th>
<th><span data-ttu-id="fcdf0-270">種類</span><span class="sxs-lookup"><span data-stu-id="fcdf0-270">Type</span></span></th>
<th><span data-ttu-id="fcdf0-271">既定値</span><span class="sxs-lookup"><span data-stu-id="fcdf0-271">Default Value</span></span></th>
<th><span data-ttu-id="fcdf0-272">説明</span><span class="sxs-lookup"><span data-stu-id="fcdf0-272">Description</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="fcdf0-273">MixerMode</span><span class="sxs-lookup"><span data-stu-id="fcdf0-273">MixerMode</span></span></td>
<td><span data-ttu-id="fcdf0-274">UINT32</span><span class="sxs-lookup"><span data-stu-id="fcdf0-274">UINT32</span></span></td>
<td><span data-ttu-id="fcdf0-275">2</span><span class="sxs-lookup"><span data-stu-id="fcdf0-275">2</span></span></td>
<td>
<ul>
<li><span data-ttu-id="fcdf0-276">0 :マイクのオーディオのみ</span><span class="sxs-lookup"><span data-stu-id="fcdf0-276">0 : Mic audio only</span></span></li>
<li><span data-ttu-id="fcdf0-277">1 :システム オーディオのみ</span><span class="sxs-lookup"><span data-stu-id="fcdf0-277">1 : System audio only</span></span></li>
<li><span data-ttu-id="fcdf0-278">2 :Mic およびシステム オーディオ</span><span class="sxs-lookup"><span data-stu-id="fcdf0-278">2 : Mic and System audio</span></span></li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="fcdf0-279">同時 MRC の制限事項</span><span class="sxs-lookup"><span data-stu-id="fcdf0-279">Simultaneous MRC limitations</span></span>

<span data-ttu-id="fcdf0-280">MRC にアクセスすると同時に複数のアプリに関する制限があります。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-280">There are certain limitations around multiple apps accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="fcdf0-281">写真/ビデオ カメラへのアクセス</span><span class="sxs-lookup"><span data-stu-id="fcdf0-281">Photo/video camera access</span></span>

<span data-ttu-id="fcdf0-282">写真/ビデオのカメラは、同時にアクセスできるプロセスの数に制限されます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-282">The photo/video camera is limited to the number of processes that can access it at the same time.</span></span> <span data-ttu-id="fcdf0-283">プロセスを記録中にビデオやその他のプロセスの写真の撮影写真とビデオのカメラの取得に失敗します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-283">While a process is recording video or taking a photo any other process will fail to acquire the photo/video camera.</span></span> <span data-ttu-id="fcdf0-284">(これは混合の実際のキャプチャと標準のフォトとビデオのキャプチャの両方に適用されます)</span><span class="sxs-lookup"><span data-stu-id="fcdf0-284">(this applies to both Mixed Reality Capture and standard photo/video capture)</span></span>

<span data-ttu-id="fcdf0-285">アプリが MediaCaptureInitializationSettings の使用時に、HoloLens の 2 [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode)写真とビデオのカメラを排他的に制御しないで済む場合 SharedReadOnly を実行することを示すプロパティです。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-285">With HoloLens 2, an app can use MediaCaptureInitializationSettings's [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) property to indicate that they want to run SharedReadOnly if they don't need exclusive control over the photo/video camera.</span></span> <span data-ttu-id="fcdf0-286">解像度やフレーム レートがキャプチャのための手段を行うパターンはどのような他のアプリ構成を提供するカメラに制限されます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-286">Doing so means the resolution and framerate of the capture will be limited to what other apps have configured the camera to provide.</span></span>

##### <a name="built-in-mrc-photovideo-camera-access"></a><span data-ttu-id="fcdf0-287">組み込み MRC 写真とビデオのカメラへのアクセス</span><span class="sxs-lookup"><span data-stu-id="fcdf0-287">Built-in MRC photo/video camera access</span></span>

<span data-ttu-id="fcdf0-288">(Cortana、[スタート] メニューのハードウェアのショートカット、Miracast、Windows Device Portal) 経由で Windows 10 に組み込まれた MRC 機能:</span><span class="sxs-lookup"><span data-stu-id="fcdf0-288">MRC functionality built into Windows 10 (via Cortana, Start Menu, hardware shortcuts, Miracast, Windows Device Portal):</span></span>
* <span data-ttu-id="fcdf0-289">既定で ExclusiveControl で実行されます。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-289">Will run with ExclusiveControl by default</span></span>

<span data-ttu-id="fcdf0-290">ただし、共有モードで動作するには、各サブシステムにサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-290">However, support has been added to each subsystem to operate in a shared mode:</span></span>
* <span data-ttu-id="fcdf0-291">アプリでは、写真とビデオのカメラに ExclusiveControl へのアクセスを要求している場合組み込み MRC がアプリの要求が成功するために、写真とビデオ カメラを使用して自動的に停止します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-291">If an app requests ExclusiveControl access to the photo/video camera, built-in MRC will automatically stop using the photo/video camera so the app's request will succeed</span></span>
* <span data-ttu-id="fcdf0-292">組み込み MRC は SharedReadOnly モードで実行されている場合は、アプリが ExclusiveControl 組み込み MRC が開始されると、</span><span class="sxs-lookup"><span data-stu-id="fcdf0-292">If built-in MRC is started while an app has ExclusiveControl, built-in MRC will run in SharedReadOnly mode</span></span>

<span data-ttu-id="fcdf0-293">この共有モードの機能には、特定の制限があります。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-293">This shared mode functionality has certain restrictions:</span></span>
* <span data-ttu-id="fcdf0-294">Cortana、ハードウェアのショートカット、または [スタート] メニューを使用して写真:Windows が必要です 10 April 2018 Update (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="fcdf0-294">Photo via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="fcdf0-295">Cortana、ハードウェアのショートカット、または [スタート] メニューを使用してビデオ:Windows が必要です 10 April 2018 Update (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="fcdf0-295">Video via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="fcdf0-296">Miracast 経由でストリーミング MRC:Windows が必要です 10 年 10 月 2018 の更新 (またはそれ以降)。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-296">Streaming MRC over Miracast: Requires the Windows 10 October 2018 Update (or later)</span></span>
* <span data-ttu-id="fcdf0-297">または、HoloLens のコンパニオン アプリを使用して Windows Device Portal 経由でストリーミング MRC は:HoloLens 2 が必要です。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-297">Streaming MRC over Windows Device Portal or via the HoloLens companion app: Requires HoloLens 2</span></span>

>[!NOTE]
> <span data-ttu-id="fcdf0-298">写真/ビデオのカメラを使用しているとき、別のアプリ、解像度と組み込みの MRC カメラ UI のフレーム レートは標準値から低下可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-298">The resolution and framerate of the built-in MRC camera UI might be reduced from its normal values when another app is using the photo/video camera.</span></span>

#### <a name="mrc-access"></a><span data-ttu-id="fcdf0-299">MRC アクセス</span><span class="sxs-lookup"><span data-stu-id="fcdf0-299">MRC access</span></span>

<span data-ttu-id="fcdf0-300">Windows 10 April 2018 Update が複数のアプリ (ただし、写真とビデオのカメラへのアクセスをまだ制限) MRC ストリームへのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-300">With the Windows 10 April 2018 Update, there is no longer a limitation around multiple apps accessing the MRC stream (however, the access to the photo/video camera still has limitations).</span></span>

<span data-ttu-id="fcdf0-301">前に、Windows 10 April 2018 Update、アプリのカスタム MRC レコーダーでは、システム MRC (写真をキャプチャ、キャプチャするビデオ、または、Windows Device Portal からのストリーミング) で相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="fcdf0-301">Previous to the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="fcdf0-302">関連項目</span><span class="sxs-lookup"><span data-stu-id="fcdf0-302">See also</span></span>
* [<span data-ttu-id="fcdf0-303">複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="fcdf0-303">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="fcdf0-304">Spectator View</span><span class="sxs-lookup"><span data-stu-id="fcdf0-304">Spectator view</span></span>](spectator-view.md)
