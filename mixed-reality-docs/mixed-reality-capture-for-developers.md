---
title: 開発者向けの Mixed reality キャプチャ
description: 開発者向けの mixed reality キャプチャのベストプラクティス。
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
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="2f7bf-104">開発者向けの Mixed reality キャプチャ</span><span class="sxs-lookup"><span data-stu-id="2f7bf-104">Mixed reality capture for developers</span></span>

> <span data-ttu-id="2f7bf-105">[注!]HoloLens 2 の新しい MRC 機能に関するガイダンスについては、以下の[PV カメラのレンダー](#render-from-the-pv-camera-opt-in)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-105">[NOTE!] See [Render from the PV camera](#render-from-the-pv-camera-opt-in) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="2f7bf-106">ユーザーは、常に[mixed reality キャプチャ](mixed-reality-capture.md)(MRC) の写真またはビデオを取得できるため、アプリケーションを開発する際には注意が必要な点がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-106">Since a user could take a [mixed reality capture](mixed-reality-capture.md) (MRC) photo or video at any time, there are a few things that you should keep in mind when developing your application.</span></span> <span data-ttu-id="2f7bf-107">これには、MRC ビジュアル品質のベストプラクティスと、MRCs のキャプチャ中にシステムの変更に応答するためのベストプラクティスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-107">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="2f7bf-108">開発者は、混合現実のキャプチャと挿入をシームレスにアプリに統合することもできます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-108">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="2f7bf-109">HoloLens の MRC (最初世代) では、720p までのビデオと写真がサポートされています。 HoloLens 2 の MRC では、最大1080p および最大4K 解像度までのビデオがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-109">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="2f7bf-110">品質の MRC の重要性</span><span class="sxs-lookup"><span data-stu-id="2f7bf-110">The importance of quality MRC</span></span>

<span data-ttu-id="2f7bf-111">多くの場合、ユーザーがアプリを使用するのは、大量の現実にキャプチャされた写真とビデオです。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-111">Mixed reality captured photos and videos are likely the first exposure a user will have of your app.</span></span> <span data-ttu-id="2f7bf-112">Microsoft Store ページに mixed reality スクリーンショットとして使用するか、ソーシャルネットワーク上で MRCs を共有する他のユーザーからのものであるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-112">Whether as mixed reality screenshots on your Microsoft Store page or from other users sharing MRCs on social networks.</span></span> <span data-ttu-id="2f7bf-113">MRC を使用して、アプリをデモし、ユーザーを教育し、世界中の対話を共有するようユーザーに促すことができます。また、ユーザーの調査や問題の解決にも対応できます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-113">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="2f7bf-114">MRC がアプリに与える影響</span><span class="sxs-lookup"><span data-stu-id="2f7bf-114">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="2f7bf-115">アプリでの MRC の有効化</span><span class="sxs-lookup"><span data-stu-id="2f7bf-115">Enabling MRC in your app</span></span>

<span data-ttu-id="2f7bf-116">既定では、アプリは、ユーザーが混合現実のキャプチャを実行できるようにするために何も行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-116">By default, an app does not have to do anything to enable users to take mixed reality captures.</span></span>

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a><span data-ttu-id="2f7bf-117">アプリでの MRC のアラインメントの向上を可能にする</span><span class="sxs-lookup"><span data-stu-id="2f7bf-117">Enabling improved alignment for MRC in your app</span></span>

<span data-ttu-id="2f7bf-118">既定では、mixed reality キャプチャは、右目の holographic 出力と写真/ビデオ (PV) カメラを結合します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-118">By default, mixed reality capture combines the right eye's holographic output with the photo/video (PV) camera.</span></span> <span data-ttu-id="2f7bf-119">この2つのソースは、現在実行中のイマーシブアプリによって設定されたフォーカスポイントを使用して結合されます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-119">These two sources are combined using the focus point set by the currently running immersive app.</span></span>

<span data-ttu-id="2f7bf-120">これは、フォーカス平面外のホログラムが、(PV カメラと右ディスプレイの間の物理的な距離によって) も整列しないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-120">This means that holograms outside the focus plane won't align as well (due to the physical distance between the PV camera and the right display).</span></span>

#### <a name="set-the-focus-point"></a><span data-ttu-id="2f7bf-121">フォーカスポイントを設定する</span><span class="sxs-lookup"><span data-stu-id="2f7bf-121">Set the focus point</span></span>

<span data-ttu-id="2f7bf-122">イマーシブアプリ (HoloLens) では、安定化平面を使用する場所の[フォーカスポイント](focus-point-in-unity.md)を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-122">Immersive apps (on HoloLens) should set the [focus point](focus-point-in-unity.md) of where they want their stabilization plane to be.</span></span> <span data-ttu-id="2f7bf-123">これにより、ヘッドセットと mixed reality キャプチャの両方で最適なアラインメントが実現されます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-123">This ensures the best alignment in both the headset and in mixed reality capture.</span></span>

<span data-ttu-id="2f7bf-124">フォーカスポイントが設定されていない場合、安定化平面は既定で2メートルになります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-124">If a focus point is not set, the stabilization plane will default to two meters.</span></span>

#### <a name="render-from-the-pv-camera-opt-in"></a><span data-ttu-id="2f7bf-125">PV カメラからのレンダリング (オプトイン)</span><span class="sxs-lookup"><span data-stu-id="2f7bf-125">Render from the PV camera (opt-in)</span></span>

<span data-ttu-id="2f7bf-126">HoloLens 2 では、mixed reality キャプチャが実行されている間に、アプリが**PV カメラからレンダリング**する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-126">HoloLens 2 adds the ability for an immersive app to **render from the PV camera** while mixed reality capture is running.</span></span> <span data-ttu-id="2f7bf-127">アプリで追加のレンダリングが正しくサポートされるようにするには、アプリでこの機能をオプトインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-127">To ensure the app supports the additional render correctly, the app has to opt-in to this functionality.</span></span>

<span data-ttu-id="2f7bf-128">PV カメラからのレンダリングでは、既定の MRC エクスペリエンスに対して次の点が改善されています。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-128">Render from the PV camera offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="2f7bf-129">物理環境とハンズオン (ほぼ相互作用のため) の両方に対するホログラムのアラインメントは、既定の MRC で見られるように、フォーカスポイント以外の距離でオフセットを使用するのではなく、すべての距離で正確である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-129">Hologram alignment to both your physical environment and hands (for near interactions) should be accurate at all distances, instead of having an offset at distances other than the focus point as you might see in the default MRC.</span></span>
* <span data-ttu-id="2f7bf-130">ヘッドセットの右目は、MRC 出力のホログラムをレンダリングするために使用されないため、侵害されることはありません。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-130">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

<span data-ttu-id="2f7bf-131">PV カメラからのレンダリングを有効にするには、次の3つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-131">There are three steps to enable rendering from the PV camera:</span></span>
1. <span data-ttu-id="2f7bf-132">PhotoVideoCamera HolographicViewConfiguration を有効にする</span><span class="sxs-lookup"><span data-stu-id="2f7bf-132">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>
2. <span data-ttu-id="2f7bf-133">追加の HolographicCamera render を処理する</span><span class="sxs-lookup"><span data-stu-id="2f7bf-133">Handle the additional HolographicCamera render</span></span>
3. <span data-ttu-id="2f7bf-134">この追加の HolographicCamera からシェーダーとコードが正しくレンダリングされることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-134">Verify your shaders and code render correctly from this additional HolographicCamera</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a><span data-ttu-id="2f7bf-135">PhotoVideoCamera HolographicViewConfiguration を有効にする</span><span class="sxs-lookup"><span data-stu-id="2f7bf-135">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>

<span data-ttu-id="2f7bf-136">オプトインするには、アプリは単に PhotoVideoCamera の[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)を有効にします。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-136">To opt-in, an app simply enables the PhotoVideoCamera's [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span></span>
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a><span data-ttu-id="2f7bf-137">DirectX で追加の HolographicCamera render を処理する</span><span class="sxs-lookup"><span data-stu-id="2f7bf-137">Handle the additional HolographicCamera render in DirectX</span></span>

<span data-ttu-id="2f7bf-138">アプリが PV カメラから表示するオプトインを持っていて、mixed reality キャプチャが開始される場合:</span><span class="sxs-lookup"><span data-stu-id="2f7bf-138">When the app has opt-in to render from the PV camera and mixed reality capture starts:</span></span>
1. <span data-ttu-id="2f7bf-139">HolographicSpace の CameraAdded イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-139">HolographicSpace's CameraAdded event will fire.</span></span> <span data-ttu-id="2f7bf-140">このイベントは、アプリがこの時点でカメラを処理できない場合に遅延する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-140">This event can be deferred if the app cannot handle the camera at this time.</span></span>
2. <span data-ttu-id="2f7bf-141">イベントが完了すると (未処理の遅延がない場合)、HolographicCamera は次の HolographicFrame の AddedCameras の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-141">Once the event has completed (and there are no outstanding deferrals) the HolographicCamera will appear in the next HolographicFrame's AddedCameras list.</span></span>

<span data-ttu-id="2f7bf-142">Mixed reality キャプチャが停止した場合 (または mixed reality キャプチャが実行されているときにアプリがビューの構成を無効にした場合)、次の HolographicFrame の RemovedCameras の一覧に HolographicCamera が表示され、HolographicSpace の CameraRemoved イベントが発生します。起動.</span><span class="sxs-lookup"><span data-stu-id="2f7bf-142">When mixed reality capture stops (or if the app disables the view configuration while mixed reality capture is running): the HolographicCamera will appear in the next HolographicFrame's RemovedCameras list and the HolographicSpace's CameraRemoved event will fire.</span></span>

<span data-ttu-id="2f7bf-143">HolographicCamera に[viewconfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)プロパティが追加され、カメラが属している構成を識別できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-143">A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) property has been added to HolographicCamera to help identify the configuration a camera belongs to.</span></span>

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a><span data-ttu-id="2f7bf-144">Unity で追加の HolographicCamera render を処理する</span><span class="sxs-lookup"><span data-stu-id="2f7bf-144">Handle the additional HolographicCamera render in Unity</span></span>

>[!NOTE]
> <span data-ttu-id="2f7bf-145">PV カメラから表示する Unity サポートは開発中であり、まだ使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-145">Unity support to render from the PV camera is under development and can't be used, yet.</span></span> <span data-ttu-id="2f7bf-146">このドキュメントは、PV カメラからのレンダリングをサポートする Unity のビルドが利用可能になったときに更新されます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-146">This documentation will be updated when a build of Unity with support for rendering from the PV camera is available.</span></span>

##### <a name="verify-shaders-and-code-support-additional-cameras"></a><span data-ttu-id="2f7bf-147">シェーダーとコードがサポートする追加のカメラを確認する</span><span class="sxs-lookup"><span data-stu-id="2f7bf-147">Verify shaders and code support additional cameras</span></span>

<span data-ttu-id="2f7bf-148">Mixed reality キャプチャを実行し、異常な配置、コンテンツ不足、またはパフォーマンスの問題がないか確認します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-148">Run a mixed reality capture and check for unusual alignment, missing content, or performance issues.</span></span> <span data-ttu-id="2f7bf-149">必要に応じてシェーダーとコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-149">Update shaders and code as appropriate.</span></span>

<span data-ttu-id="2f7bf-150">追加のカメラへのレンダリングをサポートできない特定のシーンがある場合は、その間に PhotoVideoCamera の HolographicViewConfiguration を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-150">If there are certain scenes that cannot support rendering to an additional camera, you can disable the PhotoVideoCamera's HolographicViewConfiguration during them.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="2f7bf-151">アプリでの MRC の無効化</span><span class="sxs-lookup"><span data-stu-id="2f7bf-151">Disabling MRC in your app</span></span>

#### <a name="2d-app"></a><span data-ttu-id="2f7bf-152">2D アプリ</span><span class="sxs-lookup"><span data-stu-id="2f7bf-152">2D app</span></span>

<span data-ttu-id="2f7bf-153">次の方法で混合の現実のキャプチャを実行すると、2D アプリでビジュアルコンテンツを非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-153">2D apps can choose to have their visual content obscured when mixed reality capture is running by:</span></span>
* <span data-ttu-id="2f7bf-154">[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)フラグ付きで表示する</span><span class="sxs-lookup"><span data-stu-id="2f7bf-154">Present with the [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) flag</span></span>
* <span data-ttu-id="2f7bf-155">[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)フラグを使用してアプリのスワップチェーンを作成する</span><span class="sxs-lookup"><span data-stu-id="2f7bf-155">Create the app's swap chain with the [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) flag</span></span>
* <span data-ttu-id="2f7bf-156">Windows 10 5 月2019更新プログラムで、ApplicationView の[IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)を設定します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-156">With the Windows 10 May 2019 Update, setting ApplicationView's [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span></span>

#### <a name="immersive-app"></a><span data-ttu-id="2f7bf-157">イマーシブアプリ</span><span class="sxs-lookup"><span data-stu-id="2f7bf-157">Immersive app</span></span>

<span data-ttu-id="2f7bf-158">イマーシブアプリでは、複合現実のキャプチャからビジュアルコンテンツを除外することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-158">Immersive apps can choose to have their visual content excluded from mixed reality capture by:</span></span>
* <span data-ttu-id="2f7bf-159">HolographicCameraRenderingParameter の[Iscontentprotectionenabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled)を設定して、関連付けられているフレームに対して mixed reality キャプチャを無効にしています</span><span class="sxs-lookup"><span data-stu-id="2f7bf-159">Setting HolographicCameraRenderingParameter's [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) to disable mixed reality capture for its associated frame</span></span>
* <span data-ttu-id="2f7bf-160">HolographicCamera の[IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled)を設定して、関連付けられている holographic カメラの mixed reality キャプチャを無効にする</span><span class="sxs-lookup"><span data-stu-id="2f7bf-160">Setting HolographicCamera's [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) to disable mixed reality capture for its associated holographic camera</span></span>

#### <a name="password-keyboard"></a><span data-ttu-id="2f7bf-161">パスワードキーボード</span><span class="sxs-lookup"><span data-stu-id="2f7bf-161">Password Keyboard</span></span>

<span data-ttu-id="2f7bf-162">Windows 10 5 月2019更新プログラムでは、パスワードまたは pin キーボードが表示されたときに、ビジュアルコンテンツが mixed reality キャプチャから自動的に除外されます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-162">With the Windows 10 May 2019 Update, visual content is automatically excluded from mixed reality capture when a password or pin keyboard is visible.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="2f7bf-163">MRC がアクティブであることを把握しています</span><span class="sxs-lookup"><span data-stu-id="2f7bf-163">Knowing when MRC is active</span></span>

<span data-ttu-id="2f7bf-164">アプリで[Appcapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture)クラスを使用すると、システムの混合現実のキャプチャが実行されているかどうかを知ることができます (オーディオまたはビデオのいずれか)。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-164">The [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="2f7bf-165">デバイスで混合 reality キャプチャを利用できない場合、AppCapture の[GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API は null を返すことがあります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-165">AppCapture's [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="2f7bf-166">アプリが中断されたときに CapturingChanged イベントの登録を解除することも重要です。それ以外の場合、MRC はブロックされた状態になります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-166">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="2f7bf-167">ベストプラクティス (HoloLens 固有)</span><span class="sxs-lookup"><span data-stu-id="2f7bf-167">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="2f7bf-168">MRC は開発者による追加作業がなくても機能することが期待されていますが、アプリで最適な mixed reality キャプチャエクスペリエンスを提供するために注意すべき点がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-168">MRC is expected to work without additional work from developers, but there are a few things to be aware of to provide the best mixed reality capture experience of your app.</span></span>

<span data-ttu-id="2f7bf-169">**MRC は、ホログラムのアルファチャネルを使用して、[カメラ](locatable-camera.md)の画像とブレンドします。**</span><span class="sxs-lookup"><span data-stu-id="2f7bf-169">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="2f7bf-170">最も重要な手順は、アプリが不透明な黒にクリアするのではなく、透明な黒にクリアされるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-170">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="2f7bf-171">Unity では、これは既定で MixedRealityToolkit に対して行われますが、Unity 以外で開発している場合は、1行の変更が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-171">In Unity, this is done by default with the MixedRealityToolkit but if you are developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="2f7bf-172">以下は、アプリが透明な黒にクリアされていない場合に、MRC に表示される可能性のあるアイテムの一部です。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-172">Here are some of the artifacts you might see in MRC if your app is not clearing to transparent black:</span></span>

<span data-ttu-id="2f7bf-173">**エラーの例**:コンテンツの周囲に黒い端がある (透明な黒にクリアされない)</span><span class="sxs-lookup"><span data-stu-id="2f7bf-173">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

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

<span data-ttu-id="2f7bf-174">**エラーの例**:ホログラムの背景シーン全体が黒で表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-174">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="2f7bf-175">背景のアルファ値1を設定すると、背景が黒になります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-175">Setting a background alpha value of 1 results in a black background</span></span>

![背景のアルファ値1を設定すると、背景が黒になります。](images/clearopaqueblack-300px.png)

<span data-ttu-id="2f7bf-177">**期待される結果**:ホログラムが現実の世界と適切にブレンドされている (透明な黒に消去すると予想される結果)</span><span class="sxs-lookup"><span data-stu-id="2f7bf-177">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![透過的な黒に消去する場合に予期される結果](images/cleartransparentblack-300px.png)

<span data-ttu-id="2f7bf-179">**解決方法**:</span><span class="sxs-lookup"><span data-stu-id="2f7bf-179">**Solution**:</span></span>
* <span data-ttu-id="2f7bf-180">アルファ値を0にするために、不透明な黒で表示されているコンテンツを変更します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-180">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="2f7bf-181">アプリが透明な黒にクリアされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-181">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="2f7bf-182">Unity の既定値は、MixedRealityToolkit で自動的にクリアされるようにクリアされますが、Unity 以外のアプリの場合は、ID3D11DeiceContext:: ClearRenderTargetView () で使用される色を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-182">Unity defaults to clear to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="2f7bf-183">不透明な黒 (0、0、0、1) ではなく、透明な黒 (0、0、0、0) であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-183">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="2f7bf-184">必要に応じてアセットのアルファ値を調整できるようになりましたが、通常は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-184">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="2f7bf-185">ほとんどの場合、MRCs はすぐに使えるように見えます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-185">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="2f7bf-186">MRC は、前乗算したアルファを前提としています。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-186">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="2f7bf-187">アルファ値は、MRC キャプチャにのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-187">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="2f7bf-188">HoloLens が HoloLens で有効になっている場合に予期されること</span><span class="sxs-lookup"><span data-stu-id="2f7bf-188">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="2f7bf-189">以下は、特に明記されていない限り、HoloLens (第1世代) と HoloLens 2 の両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-189">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="2f7bf-190">システムによって、アプリケーションが 30 Hz レンダリングに調整されます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-190">The system will throttle the application to 30Hz rendering.</span></span> <span data-ttu-id="2f7bf-191">これにより、MRC を実行するためのヘッドルームが作成されます。これにより、アプリは一定の予算予約を維持する必要がなく、30 fps の MRC ビデオレコードレートにも一致します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-191">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30fps</span></span>
* <span data-ttu-id="2f7bf-192">デバイスの右上にあるホログラムコンテンツは、録画/ストリーミングの場合、"スパーク" と表示されることがあります。テキストが読みにくくなり、ホログラムの端がより jaggy に見える可能性があります ( **HoloLens 2**での3番目のカメラのレンダリングでは、この侵害を回避します)。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-192">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting-in to 3rd camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="2f7bf-193">アプリケーションで有効になっている場合、MRC の写真やビデオによってアプリケーションの[フォーカスポイント](focus-point-in-unity.md)が尊重されます。これにより、ホログラムが正確に配置されます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-193">MRC photos and videos will respect the application’s [focus point](focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="2f7bf-194">ビデオの場合、フォーカスポイントが滑らかになるため、フォーカスポイントの深さが大幅に変化した場合に、ホログラムが徐々にずれて表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-194">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="2f7bf-195">フォーカスポイントと異なる深さにあるホログラムは、実際の世界からのオフセットとして表示されることがあります (下の例を参照してください。フォーカスポイントが2メートルで設定されていますが、ホログラムは1メーターに配置されています)。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-195">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![2メートルのホログラムは、世界に完全に登録されます。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="2f7bf-198">アプリ内からの MRC 機能の統合</span><span class="sxs-lookup"><span data-stu-id="2f7bf-198">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="2f7bf-199">Mixed reality アプリでは、アプリ内から MRC の写真またはビデオキャプチャを開始できます。キャプチャされたコンテンツは、デバイスの "カメラロール" に格納されていなくてもアプリで利用できます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-199">Your mixed reality app can initiate MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="2f7bf-200">カスタムの MRC レコーダーを作成することも、組み込みのカメラキャプチャ UI を利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-200">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="2f7bf-201">組み込みのカメラ UI を使用した MRC</span><span class="sxs-lookup"><span data-stu-id="2f7bf-201">MRC with built-in camera UI</span></span>

<span data-ttu-id="2f7bf-202">開発者は、 *[カメラキャプチャ UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* を使用して、わずか数行のコードでユーザーがキャプチャした mixed reality の写真またはビデオを取得できます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-202">Developers can use the *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="2f7bf-203">この API は組み込みの MRC カメラ UI を起動します。この UI では、ユーザーは写真やビデオを撮影し、結果として得られたキャプチャをアプリに返すことができます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-203">This API launches the built-in MRC camera UI, from which the user can take a photo or video, and returns the resulting capture to your app.</span></span>  <span data-ttu-id="2f7bf-204">独自のカメラ UI を作成する場合、またはキャプチャストリームへの低いレベルのアクセスが必要な場合は、カスタムの Mixed Reality キャプチャレコーダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-204">If you want to create your own camera UI, or need lower-level access to the capture stream, you can create a custom Mixed Reality Capture recorder.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="2f7bf-205">カスタム MRC レコーダーの作成</span><span class="sxs-lookup"><span data-stu-id="2f7bf-205">Creating a custom MRC recorder</span></span>

<span data-ttu-id="2f7bf-206">ユーザーは、常にシステム MRC キャプチャサービスを使用して写真またはビデオをトリガーできますが、アプリケーションではカスタムカメラアプリを作成する必要がありますが、ホログラムは、MRC と同様にカメラストリームに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-206">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app but include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="2f7bf-207">これにより、アプリケーションはユーザーの代わりにキャプチャを開始したり、カスタムの記録 UI を作成したり、MRC 設定をカスタマイズしていくつかの例に名前を設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-207">This allows the application to kick off captures on behalf of the user, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="2f7bf-208">**HoloStudio は、MRC 効果を使用してカスタム MRC カメラを追加します**</span><span class="sxs-lookup"><span data-stu-id="2f7bf-208">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio は、MRC 効果を使用してカスタム MRC カメラを追加します](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="2f7bf-210">Unity アプリケーションでは、プロパティの[Locatable_camera_in_Unity](locatable-camera-in-unity.md)を確認して、ホログラムを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-210">Unity Applications should see [Locatable_camera_in_Unity](locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="2f7bf-211">その他のアプリケーションでは、 [Windows Media Capture api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture)を使用してカメラを制御し、ビデオとオーディオ効果を追加して、仮想ホログラムとアプリケーションオーディオを静止画やビデオに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-211">Other applications can do this by using the [Windows Media Capture APIs](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="2f7bf-212">アプリケーションには、効果を追加するためのオプションが2つあります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-212">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="2f7bf-213">以前の API:[MediaCapture. AddEffectAsync () を取得します。](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span><span class="sxs-lookup"><span data-stu-id="2f7bf-213">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span></span>
* <span data-ttu-id="2f7bf-214">新しい Microsoft 推奨 API (オブジェクトを返し、動的プロパティを操作できるようにします)。[MediaCapture ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [MediaCapture](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) () では、アプリが独自の[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)実装を作成する必要があります。これは、アプリケーションを必要として[います。IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-214">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) which require the app create its own implementation of [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) and [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition).</span></span> <span data-ttu-id="2f7bf-215">使用例については、MRC 効果のサンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-215">Please see the MRC effect sample for sample usage.</span></span>

>[!NOTE]
> <span data-ttu-id="2f7bf-216">MixedRealityCapture 名前空間は Visual Studio で認識されませんが、文字列はまだ有効です。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-216">The Windows.Media.MixedRealityCapture namespace will not be recognized by Visual Studio, but the strings are still valid.</span></span>

<span data-ttu-id="2f7bf-217">MRC ビデオ効果 (**MixedRealityCapture. MixedRealityCaptureVideoEffect**)</span><span class="sxs-lookup"><span data-stu-id="2f7bf-217">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="2f7bf-218">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="2f7bf-218">Property Name</span></span>  |  <span data-ttu-id="2f7bf-219">種類</span><span class="sxs-lookup"><span data-stu-id="2f7bf-219">Type</span></span>  |  <span data-ttu-id="2f7bf-220">既定値</span><span class="sxs-lookup"><span data-stu-id="2f7bf-220">Default Value</span></span>  |  <span data-ttu-id="2f7bf-221">説明</span><span class="sxs-lookup"><span data-stu-id="2f7bf-221">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="2f7bf-222">StreamType</span><span class="sxs-lookup"><span data-stu-id="2f7bf-222">StreamType</span></span>  |  <span data-ttu-id="2f7bf-223">UINT32 ([Mediastreamtype](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span><span class="sxs-lookup"><span data-stu-id="2f7bf-223">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span></span>  |  <span data-ttu-id="2f7bf-224">1 (VideoRecord)</span><span class="sxs-lookup"><span data-stu-id="2f7bf-224">1 (VideoRecord)</span></span>  |  <span data-ttu-id="2f7bf-225">この効果がどのキャプチャストリームに使用されるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-225">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="2f7bf-226">オーディオは使用できません。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-226">Audio is not available.</span></span> | 
|  <span data-ttu-id="2f7bf-227">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="2f7bf-227">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="2f7bf-228">boolean</span><span class="sxs-lookup"><span data-stu-id="2f7bf-228">boolean</span></span>  |  <span data-ttu-id="2f7bf-229">TRUE</span><span class="sxs-lookup"><span data-stu-id="2f7bf-229">TRUE</span></span>  |  <span data-ttu-id="2f7bf-230">ビデオキャプチャのホログラムを有効または無効にするフラグ。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-230">Flag to enable or disable holograms in video capture.</span></span> | 
|  <span data-ttu-id="2f7bf-231">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="2f7bf-231">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="2f7bf-232">boolean</span><span class="sxs-lookup"><span data-stu-id="2f7bf-232">boolean</span></span>  |  <span data-ttu-id="2f7bf-233">TRUE</span><span class="sxs-lookup"><span data-stu-id="2f7bf-233">TRUE</span></span>  |  <span data-ttu-id="2f7bf-234">ホログラムのキャプチャ中に画面の記録インジケーターを有効または無効にするフラグ。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-234">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> | 
|  <span data-ttu-id="2f7bf-235">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="2f7bf-235">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="2f7bf-236">boolean</span><span class="sxs-lookup"><span data-stu-id="2f7bf-236">boolean</span></span>  |  <span data-ttu-id="2f7bf-237">FALSE</span><span class="sxs-lookup"><span data-stu-id="2f7bf-237">FALSE</span></span>  |  <span data-ttu-id="2f7bf-238">HoloLens トラッカーを使用して、ビデオの安定化を有効または無効にするフラグ。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-238">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> | 
|  <span data-ttu-id="2f7bf-239">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="2f7bf-239">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="2f7bf-240">UINT32</span><span class="sxs-lookup"><span data-stu-id="2f7bf-240">UINT32</span></span>  |  <span data-ttu-id="2f7bf-241">0</span><span class="sxs-lookup"><span data-stu-id="2f7bf-241">0</span></span>  |  <span data-ttu-id="2f7bf-242">ビデオ安定化に使用する履歴フレームの数を設定します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-242">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="2f7bf-243">0は待機時間が0で、電源とパフォーマンスの観点からはほぼ "無料" です。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-243">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="2f7bf-244">最大品質には15が推奨されます (待機時間とメモリの15フレームのコスト)。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-244">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> | 
|  <span data-ttu-id="2f7bf-245">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="2f7bf-245">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="2f7bf-246">FLOAT</span><span class="sxs-lookup"><span data-stu-id="2f7bf-246">float</span></span>  |  <span data-ttu-id="2f7bf-247">0.9 (HoloLens) 1.0 (イマーシブヘッドセット)</span><span class="sxs-lookup"><span data-stu-id="2f7bf-247">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="2f7bf-248">0\.0 (完全に透明) から 1.0 (完全に不透明) までの範囲内のホログラムのグローバル不透明度係数を設定します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-248">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> | 
|  <span data-ttu-id="2f7bf-249">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="2f7bf-249">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="2f7bf-250">boolean</span><span class="sxs-lookup"><span data-stu-id="2f7bf-250">boolean</span></span>  |  <span data-ttu-id="2f7bf-251">FALSE</span><span class="sxs-lookup"><span data-stu-id="2f7bf-251">FALSE</span></span>  |  <span data-ttu-id="2f7bf-252">保護されたコンテンツを示す 2d UWP アプリがある場合に空のフレームを返すことを有効または無効にするフラグ。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-252">Flag to enable or disable returning an empty frame if there is a 2d UWP app showing protected content.</span></span> <span data-ttu-id="2f7bf-253">このフラグが false で、2d UWP アプリで保護されたコンテンツが表示されている場合、2d UWP アプリはヘッドセットと mixed reality キャプチャの両方で保護されたコンテンツテクスチャに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-253">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="2f7bf-254">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="2f7bf-254">ShowHiddenMesh</span></span>  |  <span data-ttu-id="2f7bf-255">boolean</span><span class="sxs-lookup"><span data-stu-id="2f7bf-255">boolean</span></span>  |  <span data-ttu-id="2f7bf-256">FALSE</span><span class="sxs-lookup"><span data-stu-id="2f7bf-256">FALSE</span></span>  |  <span data-ttu-id="2f7bf-257">Holographic カメラの非表示領域メッシュと隣接するコンテンツの表示を有効または無効にするフラグ。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-257">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |
| <span data-ttu-id="2f7bf-258">OutputSize</span><span class="sxs-lookup"><span data-stu-id="2f7bf-258">OutputSize</span></span> | <span data-ttu-id="2f7bf-259">サイズ</span><span class="sxs-lookup"><span data-stu-id="2f7bf-259">Size</span></span> | <span data-ttu-id="2f7bf-260">0、0</span><span class="sxs-lookup"><span data-stu-id="2f7bf-260">0, 0</span></span> | <span data-ttu-id="2f7bf-261">ビデオの安定化のトリミング後に、目的の出力サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-261">Set the desired output size after cropping for video stabilization.</span></span> <span data-ttu-id="2f7bf-262">0または無効な出力サイズが指定されている場合は、既定のトリミングサイズが選択されます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-262">A default crop size is chosen if 0 or an invalid output size is specified.</span></span> |
| <span data-ttu-id="2f7bf-263">PreferredHologramPerspective</span><span class="sxs-lookup"><span data-stu-id="2f7bf-263">PreferredHologramPerspective</span></span> | <span data-ttu-id="2f7bf-264">UINT32</span><span class="sxs-lookup"><span data-stu-id="2f7bf-264">UINT32</span></span> | <span data-ttu-id="2f7bf-265">1 (PhotoVideoCamera)</span><span class="sxs-lookup"><span data-stu-id="2f7bf-265">1 (PhotoVideoCamera)</span></span> | <span data-ttu-id="2f7bf-266">キャプチャする holographic カメラビュー構成を示すために使用される列挙です。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-266">Enum used to indicate which holographic camera view configuration should be captured.</span></span> <span data-ttu-id="2f7bf-267">0 (表示) に設定すると、アプリは写真/ビデオカメラから表示するように要求されません。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-267">Setting 0 (Display) means that the app won't be asked to render from the photo/video camera</span></span> |

<span data-ttu-id="2f7bf-268">MRC オーディオ効果 (**MixedRealityCapture. MixedRealityCaptureAudioEffect**)</span><span class="sxs-lookup"><span data-stu-id="2f7bf-268">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

<table>
<tr>
<th><span data-ttu-id="2f7bf-269">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="2f7bf-269">Property Name</span></span></th>
<th><span data-ttu-id="2f7bf-270">種類</span><span class="sxs-lookup"><span data-stu-id="2f7bf-270">Type</span></span></th>
<th><span data-ttu-id="2f7bf-271">既定値</span><span class="sxs-lookup"><span data-stu-id="2f7bf-271">Default Value</span></span></th>
<th><span data-ttu-id="2f7bf-272">説明</span><span class="sxs-lookup"><span data-stu-id="2f7bf-272">Description</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="2f7bf-273">MixerMode</span><span class="sxs-lookup"><span data-stu-id="2f7bf-273">MixerMode</span></span></td>
<td><span data-ttu-id="2f7bf-274">UINT32</span><span class="sxs-lookup"><span data-stu-id="2f7bf-274">UINT32</span></span></td>
<td><span data-ttu-id="2f7bf-275">2</span><span class="sxs-lookup"><span data-stu-id="2f7bf-275">2</span></span></td>
<td>
<ul>
<li><span data-ttu-id="2f7bf-276">0Mic オーディオのみ</span><span class="sxs-lookup"><span data-stu-id="2f7bf-276">0 : Mic audio only</span></span></li>
<li><span data-ttu-id="2f7bf-277">1システムオーディオのみ</span><span class="sxs-lookup"><span data-stu-id="2f7bf-277">1 : System audio only</span></span></li>
<li><span data-ttu-id="2f7bf-278">3Mic とシステムオーディオ</span><span class="sxs-lookup"><span data-stu-id="2f7bf-278">2 : Mic and System audio</span></span></li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="2f7bf-279">同時の MRC の制限事項</span><span class="sxs-lookup"><span data-stu-id="2f7bf-279">Simultaneous MRC limitations</span></span>

<span data-ttu-id="2f7bf-280">同時に、複数のアプリが MRC にアクセスすることには、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-280">There are certain limitations around multiple apps accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="2f7bf-281">写真/ビデオカメラへのアクセス</span><span class="sxs-lookup"><span data-stu-id="2f7bf-281">Photo/video camera access</span></span>

<span data-ttu-id="2f7bf-282">写真/ビデオカメラは、同時にアクセスできるプロセスの数に制限されています。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-282">The photo/video camera is limited to the number of processes that can access it at the same time.</span></span> <span data-ttu-id="2f7bf-283">プロセスがビデオを記録したり、写真を撮影したりしている間、他のプロセスは写真/ビデオカメラの取得に失敗します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-283">While a process is recording video or taking a photo any other process will fail to acquire the photo/video camera.</span></span> <span data-ttu-id="2f7bf-284">(これは Mixed Reality キャプチャと標準の写真/ビデオキャプチャの両方に適用されます)</span><span class="sxs-lookup"><span data-stu-id="2f7bf-284">(this applies to both Mixed Reality Capture and standard photo/video capture)</span></span>

<span data-ttu-id="2f7bf-285">HoloLens 2 では、アプリは MediaCaptureInitializationSettings の[Sharingmode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode)プロパティを使用して、写真/ビデオカメラを排他的に制御する必要がない場合に sharedreadonly を実行するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-285">With HoloLens 2, an app can use MediaCaptureInitializationSettings's [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) property to indicate that they want to run SharedReadOnly if they don't need exclusive control over the photo/video camera.</span></span> <span data-ttu-id="2f7bf-286">これにより、キャプチャの解像度とフレームレートは、他のアプリによって提供されるように構成されている他のアプリに制限されます。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-286">Doing so means the resolution and framerate of the capture will be limited to what other apps have configured the camera to provide.</span></span>

##### <a name="built-in-mrc-photovideo-camera-access"></a><span data-ttu-id="2f7bf-287">組み込みの MRC フォト/ビデオカメラアクセス</span><span class="sxs-lookup"><span data-stu-id="2f7bf-287">Built-in MRC photo/video camera access</span></span>

<span data-ttu-id="2f7bf-288">Windows 10 に組み込まれた MRC 機能 (Cortana、スタートメニュー、ハードウェアショートカット、Miracast、Windows デバイスポータル):</span><span class="sxs-lookup"><span data-stu-id="2f7bf-288">MRC functionality built into Windows 10 (via Cortana, Start Menu, hardware shortcuts, Miracast, Windows Device Portal):</span></span>
* <span data-ttu-id="2f7bf-289">既定では ExclusiveControl を使用して実行されます</span><span class="sxs-lookup"><span data-stu-id="2f7bf-289">Will run with ExclusiveControl by default</span></span>

<span data-ttu-id="2f7bf-290">ただし、各サブシステムには、共有モードで動作するためのサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-290">However, support has been added to each subsystem to operate in a shared mode:</span></span>
* <span data-ttu-id="2f7bf-291">アプリが写真/ビデオカメラへの ExclusiveControl アクセスを要求した場合、組み込みの MRC は、アプリの要求が成功するように、写真/ビデオカメラの使用を自動的に停止します。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-291">If an app requests ExclusiveControl access to the photo/video camera, built-in MRC will automatically stop using the photo/video camera so the app's request will succeed</span></span>
* <span data-ttu-id="2f7bf-292">アプリの ExclusiveControl 中に組み込みの MRC が開始された場合、組み込みの MRC は SharedReadOnly モードで実行されます</span><span class="sxs-lookup"><span data-stu-id="2f7bf-292">If built-in MRC is started while an app has ExclusiveControl, built-in MRC will run in SharedReadOnly mode</span></span>

<span data-ttu-id="2f7bf-293">この共有モード機能には、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-293">This shared mode functionality has certain restrictions:</span></span>
* <span data-ttu-id="2f7bf-294">Cortana、ハードウェアショートカット、または [スタート] メニューを使用した写真:Windows 10 April 2018 更新プログラム (またはそれ以降) が必要です。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-294">Photo via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="2f7bf-295">Cortana、ハードウェアショートカット、または [スタート] メニューを使用したビデオ:Windows 10 April 2018 更新プログラム (またはそれ以降) が必要です。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-295">Video via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="2f7bf-296">Miracast 経由のストリーミング MRC:Windows 10 10 月2018更新プログラム (またはそれ以降) が必要です。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-296">Streaming MRC over Miracast: Requires the Windows 10 October 2018 Update (or later)</span></span>
* <span data-ttu-id="2f7bf-297">Windows デバイスポータルまたは HoloLens コンパニオンアプリを使用したストリーミングの場合:HoloLens 2 が必要</span><span class="sxs-lookup"><span data-stu-id="2f7bf-297">Streaming MRC over Windows Device Portal or via the HoloLens companion app: Requires HoloLens 2</span></span>

>[!NOTE]
> <span data-ttu-id="2f7bf-298">別のアプリが写真/ビデオカメラを使用している場合、組み込みの MRC カメラ UI の解像度とフレームレートは通常の値から小さくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-298">The resolution and framerate of the built-in MRC camera UI might be reduced from its normal values when another app is using the photo/video camera.</span></span>

#### <a name="mrc-access"></a><span data-ttu-id="2f7bf-299">MRC アクセス</span><span class="sxs-lookup"><span data-stu-id="2f7bf-299">MRC access</span></span>

<span data-ttu-id="2f7bf-300">Windows 10 April 2018 更新プログラムでは、MRC ストリームにアクセスする複数のアプリに関する制限はなくなりました (ただし、写真/ビデオカメラへのアクセスにはまだ制限があります)。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-300">With the Windows 10 April 2018 Update, there is no longer a limitation around multiple apps accessing the MRC stream (however, the access to the photo/video camera still has limitations).</span></span>

<span data-ttu-id="2f7bf-301">Windows 10 April 2018 Update より前のバージョンでは、アプリのカスタム MRC レコーダーはシステム MRC と同時に使用できませんでした (写真をキャプチャする、ビデオをキャプチャする、または Windows デバイスポータルからストリーミングする)。</span><span class="sxs-lookup"><span data-stu-id="2f7bf-301">Previous to the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f7bf-302">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f7bf-302">See also</span></span>
* [<span data-ttu-id="2f7bf-303">複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="2f7bf-303">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="2f7bf-304">Spectator View</span><span class="sxs-lookup"><span data-stu-id="2f7bf-304">Spectator view</span></span>](spectator-view.md)
