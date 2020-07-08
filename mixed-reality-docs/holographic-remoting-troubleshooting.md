---
title: Holographic リモート処理のトラブルシューティングと制限事項
description: HoloLens 2 での Holographic Remoting のトラブルシューティングの手順
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality, ホログラム, holographic リモート処理, リモートレンダリング, ネットワークレンダリング, HoloLens, リモートホログラム, トラブルシューティング, ヘルプ
ms.openlocfilehash: 79650ceab5d0125a8a06c776a59a45a78d0aa20c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061115"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="afb1b-104">Holographic リモート処理のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="afb1b-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="afb1b-105">このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="afb1b-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="afb1b-106">Spectre の緩和されたライブラリが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="afb1b-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="afb1b-107">Holographic リモート処理サンプルアプリでは、リリース構成で Spectre 軽減策 (/Qspectre) が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="afb1b-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="afb1b-108">"Vccorlib .lib" を開くことができないという致命的なリンカーエラーが発生した場合は、Visual Studio ワークロードに Spectre 軽減可能なライブラリが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="afb1b-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="afb1b-109">詳細については、「https://aka.ms/Ofhn4c」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afb1b-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="speech"></a><span data-ttu-id="afb1b-110">音声</span><span class="sxs-lookup"><span data-stu-id="afb1b-110">Speech</span></span>

<span data-ttu-id="afb1b-111">Holographic Remoting Player は診断オーバーレイをサポートしています。これは、「」と言って無効にすることで有効にすることができ ```Enable Diagnostics``` ```Disable Diagnostics``` ます。</span><span class="sxs-lookup"><span data-stu-id="afb1b-111">The Holographic Remoting Player supports a diagnostics overlay which can be enabled by saying ```Enable Diagnostics``` and disabled by saying ```Disable Diagnostics```.</span></span> <span data-ttu-id="afb1b-112">これらの音声コマンドで問題が発生した場合は、URL としてを使用して web ブラウザーで Holographic リモート処理プレーヤーを起動することもできます ```ms-holographic-remoting:?stats``` 。</span><span class="sxs-lookup"><span data-stu-id="afb1b-112">If you have trouble with these voice commands you can also launch the Holographic Remoting player via a web browser using ```ms-holographic-remoting:?stats``` as an URL.</span></span>

## <a name="limitations"></a><span data-ttu-id="afb1b-113">制限事項</span><span class="sxs-lookup"><span data-stu-id="afb1b-113">Limitations</span></span>

<span data-ttu-id="afb1b-114">Holographic Remoting を HoloLens 2 に使用する場合、次の Api は現在サポートされて**いません**。特に明記されて ```ERROR_NOT_SUPPORTED``` いない限り、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="afb1b-114">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="afb1b-115">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="afb1b-115">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="afb1b-116">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="afb1b-116">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="afb1b-117">サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降</span><span class="sxs-lookup"><span data-stu-id="afb1b-117">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="afb1b-118">以前のバージョンでは、常にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="afb1b-118">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="afb1b-119">HolographicCamera.IsHardwareContentProtectionEnabled</span><span class="sxs-lookup"><span data-stu-id="afb1b-119">HolographicCamera.IsHardwareContentProtectionEnabled</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [<span data-ttu-id="afb1b-120">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="afb1b-120">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="afb1b-121">は失敗しませんが、レンダーターゲットのサイズは変更されません。</span><span class="sxs-lookup"><span data-stu-id="afb1b-121">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="afb1b-122">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="afb1b-122">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="afb1b-123">HolographicCameraPose ビューポート</span><span class="sxs-lookup"><span data-stu-id="afb1b-123">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="afb1b-124">HolographicCameraPose</span><span class="sxs-lookup"><span data-stu-id="afb1b-124">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="afb1b-125">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="afb1b-125">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="afb1b-126">は失敗しませんが、深度バッファーはリモート処理されません。</span><span class="sxs-lookup"><span data-stu-id="afb1b-126">Does not fail but depth buffer will not be remoted.</span></span>
  - <span data-ttu-id="afb1b-127">サポートされているバージョン[2.1.0](holographic-remoting-version-history.md#v2.1.0)以降</span><span class="sxs-lookup"><span data-stu-id="afb1b-127">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="afb1b-128">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="afb1b-128">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="afb1b-129">HolographicViewConfigurationKind にクエリを実行すると、常にが返されます ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="afb1b-129">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="afb1b-130">サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降</span><span class="sxs-lookup"><span data-stu-id="afb1b-130">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="afb1b-131">以前のバージョンでは、常にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="afb1b-131">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="afb1b-132">HolographicSpace プレゼンテーションモニター</span><span class="sxs-lookup"><span data-stu-id="afb1b-132">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="afb1b-133">HolographicDisplay</span><span class="sxs-lookup"><span data-stu-id="afb1b-133">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="afb1b-134">は、接続が確立される前に呼び出された場合にエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="afb1b-134">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="afb1b-135">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="afb1b-135">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="afb1b-136">SpatialLocation AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="afb1b-136">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="afb1b-137">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="afb1b-137">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="afb1b-138">SpatialLocation AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="afb1b-138">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="afb1b-139">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="afb1b-139">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="afb1b-140">SpatialLocation AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="afb1b-140">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="afb1b-141">SpatialLocation AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="afb1b-141">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="afb1b-142">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="afb1b-142">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="afb1b-143">バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="afb1b-143">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="afb1b-144">以前のバージョンでは、は常にを返し ```nullptr``` ます。</span><span class="sxs-lookup"><span data-stu-id="afb1b-144">On previous versions always returns ```nullptr```.</span></span>
* [<span data-ttu-id="afb1b-145">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="afb1b-145">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - <span data-ttu-id="afb1b-146">バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="afb1b-146">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="afb1b-147">SpatialAnchor. RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="afb1b-147">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="afb1b-148">SpatialAnchorExporter.GetDefault</span><span class="sxs-lookup"><span data-stu-id="afb1b-148">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="afb1b-149">バージョン[2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="afb1b-149">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="afb1b-150">以前のバージョンでは、は常にを返し ```nullptr``` ます。</span><span class="sxs-lookup"><span data-stu-id="afb1b-150">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="afb1b-151">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="afb1b-151">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="afb1b-152">バージョン[2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="afb1b-152">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="afb1b-153">以前のバージョンでは、非同期操作は常にで完了していました ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。</span><span class="sxs-lookup"><span data-stu-id="afb1b-153">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="afb1b-154">SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="afb1b-154">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="afb1b-155">非同期操作は常にで完了 ```SpatialPerceptionAccessStatus.DeniedBySystem``` します。</span><span class="sxs-lookup"><span data-stu-id="afb1b-155">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="afb1b-156">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="afb1b-156">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="afb1b-157">非同期操作は常にで完了 ```false``` します。</span><span class="sxs-lookup"><span data-stu-id="afb1b-157">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="afb1b-158">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="afb1b-158">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="afb1b-159">非同期操作は常にで完了 ```nullptr``` します。</span><span class="sxs-lookup"><span data-stu-id="afb1b-159">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="afb1b-160">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="afb1b-160">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="afb1b-161">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="afb1b-161">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="afb1b-162">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="afb1b-162">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [<span data-ttu-id="afb1b-163">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="afb1b-163">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - <span data-ttu-id="afb1b-164">バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="afb1b-164">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>

[<span data-ttu-id="afb1b-165">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="afb1b-165">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="afb1b-166">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="afb1b-166">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="afb1b-167">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="afb1b-167">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="afb1b-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="afb1b-168">See Also</span></span>
* [<span data-ttu-id="afb1b-169">Holographic リモート処理のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="afb1b-169">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="afb1b-170">Holographic Remoting リモート アプリの作成</span><span class="sxs-lookup"><span data-stu-id="afb1b-170">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="afb1b-171">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="afb1b-171">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="afb1b-172">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="afb1b-172">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="afb1b-173">Microsoft のプライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="afb1b-173">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
