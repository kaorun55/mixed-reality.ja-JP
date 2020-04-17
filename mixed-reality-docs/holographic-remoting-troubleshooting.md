---
title: Holographic リモート処理のトラブルシューティングと制限事項
description: HoloLens 2 での Holographic Remoting のトラブルシューティングの手順
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality, ホログラム, holographic リモート処理, リモートレンダリング, ネットワークレンダリング, HoloLens, リモートホログラム, トラブルシューティング, ヘルプ
ms.openlocfilehash: fc379eb4ad849fb5b236b82719711b37fead8a68
ms.sourcegitcommit: 48456c607a2d0dcf035a77e8ba67615396b0a211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484312"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="9661a-104">Holographic リモート処理のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9661a-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9661a-105">このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="9661a-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="9661a-106">Spectre の緩和されたライブラリが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="9661a-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="9661a-107">Holographic リモート処理サンプルアプリでは、リリース構成で Spectre 軽減策 (/Qspectre) が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="9661a-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="9661a-108">"Vccorlib .lib" を開くことができないという致命的なリンカーエラーが発生した場合は、Visual Studio ワークロードに Spectre 軽減可能なライブラリが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9661a-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="9661a-109">詳細については、「 https://aka.ms/Ofhn4c」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9661a-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="9661a-110">制限事項</span><span class="sxs-lookup"><span data-stu-id="9661a-110">Limitations</span></span>

<span data-ttu-id="9661a-111">Holographic Remoting を HoloLens 2 に使用する場合、次の Api は現在サポートされて**いません**。特に明記されていない限り、```ERROR_NOT_SUPPORTED``` エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9661a-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="9661a-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="9661a-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="9661a-113">HolographicCamera</span><span class="sxs-lookup"><span data-stu-id="9661a-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="9661a-114">サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降</span><span class="sxs-lookup"><span data-stu-id="9661a-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="9661a-115">以前のバージョンでは、常にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9661a-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="9661a-116">HolographicCamera.IsHardwareContentProtectionEnabled</span><span class="sxs-lookup"><span data-stu-id="9661a-116">HolographicCamera.IsHardwareContentProtectionEnabled</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [<span data-ttu-id="9661a-117">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="9661a-117">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="9661a-118">は失敗しませんが、レンダーターゲットのサイズは変更されません。</span><span class="sxs-lookup"><span data-stu-id="9661a-118">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="9661a-119">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="9661a-119">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="9661a-120">HolographicCameraPose ビューポート</span><span class="sxs-lookup"><span data-stu-id="9661a-120">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="9661a-121">HolographicCameraPose</span><span class="sxs-lookup"><span data-stu-id="9661a-121">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="9661a-122">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="9661a-122">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="9661a-123">は失敗しませんが、深度バッファーはリモート処理されません。</span><span class="sxs-lookup"><span data-stu-id="9661a-123">Does not fail but depth buffer will not be remoted.</span></span>
  - <span data-ttu-id="9661a-124">サポートされているバージョン[2.1.0](holographic-remoting-version-history.md#v2.1.0)以降</span><span class="sxs-lookup"><span data-stu-id="9661a-124">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="9661a-125">HolographicDisplay の構成</span><span class="sxs-lookup"><span data-stu-id="9661a-125">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="9661a-126">HolographicViewConfigurationKind にクエリを実行すると、常に ```nullptr```が返されます。</span><span class="sxs-lookup"><span data-stu-id="9661a-126">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="9661a-127">サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降</span><span class="sxs-lookup"><span data-stu-id="9661a-127">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="9661a-128">以前のバージョンでは、常にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9661a-128">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="9661a-129">HolographicSpace プレゼンテーションモニター</span><span class="sxs-lookup"><span data-stu-id="9661a-129">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="9661a-130">HolographicDisplay</span><span class="sxs-lookup"><span data-stu-id="9661a-130">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="9661a-131">は、接続が確立される前に呼び出された場合にエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="9661a-131">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="9661a-132">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="9661a-132">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="9661a-133">SpatialLocation AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="9661a-133">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="9661a-134">SpatialLocation AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="9661a-134">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="9661a-135">SpatialLocation AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="9661a-135">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="9661a-136">SpatialLocation AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="9661a-136">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="9661a-137">SpatialLocation AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="9661a-137">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="9661a-138">SpatialLocation AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="9661a-138">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="9661a-139">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="9661a-139">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="9661a-140">常に ```nullptr```を返します。</span><span class="sxs-lookup"><span data-stu-id="9661a-140">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="9661a-141">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="9661a-141">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="9661a-142">SpatialAnchor. RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="9661a-142">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="9661a-143">SpatialAnchorExporter</span><span class="sxs-lookup"><span data-stu-id="9661a-143">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="9661a-144">バージョン[2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9661a-144">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="9661a-145">以前のバージョンでは、常に ```nullptr```を返します。</span><span class="sxs-lookup"><span data-stu-id="9661a-145">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="9661a-146">SpatialAnchorExporter</span><span class="sxs-lookup"><span data-stu-id="9661a-146">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="9661a-147">バージョン[2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9661a-147">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="9661a-148">以前のバージョンでは、非同期操作は常に ```SpatialPerceptionAccessStatus.DeniedBySystem```で完了しました。</span><span class="sxs-lookup"><span data-stu-id="9661a-148">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="9661a-149">SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="9661a-149">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="9661a-150">非同期操作は常に ```SpatialPerceptionAccessStatus.DeniedBySystem```で完了します。</span><span class="sxs-lookup"><span data-stu-id="9661a-150">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="9661a-151">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="9661a-151">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="9661a-152">非同期操作は常に ```false```で完了します。</span><span class="sxs-lookup"><span data-stu-id="9661a-152">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="9661a-153">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="9661a-153">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="9661a-154">非同期操作は常に ```nullptr```で完了します。</span><span class="sxs-lookup"><span data-stu-id="9661a-154">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="9661a-155">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="9661a-155">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="9661a-156">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="9661a-156">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="9661a-157">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="9661a-157">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [<span data-ttu-id="9661a-158">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="9661a-158">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

[<span data-ttu-id="9661a-159">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="9661a-159">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="9661a-160">SpatialGraphInteropPreview. CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="9661a-160">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="9661a-161">SpatialGraphInteropPreview. Trycreateofreference</span><span class="sxs-lookup"><span data-stu-id="9661a-161">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="9661a-162">参照</span><span class="sxs-lookup"><span data-stu-id="9661a-162">See Also</span></span>
* [<span data-ttu-id="9661a-163">Holographic リモート処理のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="9661a-163">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="9661a-164">Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="9661a-164">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="9661a-165">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="9661a-165">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="9661a-166">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="9661a-166">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="9661a-167">Microsoft のプライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="9661a-167">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
