---
title: Holographic リモート処理のトラブルシューティングと制限事項
description: HoloLens 2 での Holographic Remoting のトラブルシューティングの手順
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 12/17/2019
ms.topic: article
keywords: Windows Mixed Reality, ホログラム, holographic リモート処理, リモートレンダリング, ネットワークレンダリング, HoloLens, リモートホログラム, トラブルシューティング, ヘルプ
ms.openlocfilehash: 05333c8911010945a543cf603b9925eb30c841db
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181972"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="ec882-104">Holographic リモート処理のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ec882-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec882-105">このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="ec882-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="ec882-106">Spectre の緩和されたライブラリが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="ec882-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="ec882-107">Holographic リモート処理サンプルアプリでは、リリース構成で Spectre 軽減策 (/Qspectre) が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="ec882-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="ec882-108">"Vccorlib .lib" を開くことができないという致命的なリンカーエラーが発生した場合は、Visual Studio ワークロードに Spectre 軽減可能なライブラリが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ec882-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="ec882-109">詳細については、「 https://aka.ms/Ofhn4c 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec882-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="ec882-110">制限事項</span><span class="sxs-lookup"><span data-stu-id="ec882-110">Limitations</span></span>

<span data-ttu-id="ec882-111">Holographic Remoting を HoloLens 2 に使用する場合、次の Api は現在サポートされて**いません**。特に明記されていない限り、```ERROR_NOT_SUPPORTED``` エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ec882-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="ec882-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="ec882-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="ec882-113">HolographicCamera</span><span class="sxs-lookup"><span data-stu-id="ec882-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="ec882-114">サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降</span><span class="sxs-lookup"><span data-stu-id="ec882-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="ec882-115">以前のバージョンでは、常にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ec882-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="ec882-116">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="ec882-116">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="ec882-117">は失敗しませんが、レンダーターゲットのサイズは変更されません。</span><span class="sxs-lookup"><span data-stu-id="ec882-117">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="ec882-118">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="ec882-118">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="ec882-119">HolographicCameraPose ビューポート</span><span class="sxs-lookup"><span data-stu-id="ec882-119">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="ec882-120">HolographicCameraPose</span><span class="sxs-lookup"><span data-stu-id="ec882-120">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="ec882-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="ec882-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="ec882-122">は失敗しませんが、深度バッファーはリモート処理されません。</span><span class="sxs-lookup"><span data-stu-id="ec882-122">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="ec882-123">HolographicDisplay の構成</span><span class="sxs-lookup"><span data-stu-id="ec882-123">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="ec882-124">HolographicViewConfigurationKind にクエリを実行すると、常に ```nullptr```が返されます。</span><span class="sxs-lookup"><span data-stu-id="ec882-124">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="ec882-125">サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降</span><span class="sxs-lookup"><span data-stu-id="ec882-125">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="ec882-126">以前のバージョンでは、常にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ec882-126">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="ec882-127">HolographicSpace プレゼンテーションモニター</span><span class="sxs-lookup"><span data-stu-id="ec882-127">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="ec882-128">HolographicDisplay</span><span class="sxs-lookup"><span data-stu-id="ec882-128">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="ec882-129">は、接続が確立される前に呼び出された場合にエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="ec882-129">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="ec882-130">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="ec882-130">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="ec882-131">SpatialLocation AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="ec882-131">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="ec882-132">SpatialLocation AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="ec882-132">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="ec882-133">SpatialLocation AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="ec882-133">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="ec882-134">SpatialLocation AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="ec882-134">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="ec882-135">SpatialLocation AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="ec882-135">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="ec882-136">SpatialLocation AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="ec882-136">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="ec882-137">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="ec882-137">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="ec882-138">常に ```nullptr``` を返します。</span><span class="sxs-lookup"><span data-stu-id="ec882-138">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="ec882-139">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="ec882-139">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="ec882-140">SpatialAnchor. RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="ec882-140">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="ec882-141">SpatialAnchorExporter</span><span class="sxs-lookup"><span data-stu-id="ec882-141">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="ec882-142">バージョン[2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ec882-142">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="ec882-143">以前のバージョンでは、常に ```nullptr```を返します。</span><span class="sxs-lookup"><span data-stu-id="ec882-143">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="ec882-144">SpatialAnchorExporter</span><span class="sxs-lookup"><span data-stu-id="ec882-144">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="ec882-145">バージョン[2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ec882-145">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="ec882-146">以前のバージョンでは、非同期操作は常に ```SpatialPerceptionAccessStatus.DeniedBySystem```で完了しました。</span><span class="sxs-lookup"><span data-stu-id="ec882-146">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="ec882-147">SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="ec882-147">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="ec882-148">非同期操作は常に ```SpatialPerceptionAccessStatus.DeniedBySystem```で完了します。</span><span class="sxs-lookup"><span data-stu-id="ec882-148">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="ec882-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="ec882-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="ec882-150">非同期操作は常に ```false```で完了します。</span><span class="sxs-lookup"><span data-stu-id="ec882-150">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="ec882-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="ec882-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="ec882-152">非同期操作は常に ```nullptr```で完了します。</span><span class="sxs-lookup"><span data-stu-id="ec882-152">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="ec882-153">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="ec882-153">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="ec882-154">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="ec882-154">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="ec882-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="ec882-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="ec882-156">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="ec882-156">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="ec882-157">SpatialGraphInteropPreview. CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="ec882-157">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="ec882-158">SpatialGraphInteropPreview. Trycreateofreference</span><span class="sxs-lookup"><span data-stu-id="ec882-158">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="ec882-159">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="ec882-159">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="ec882-160">参照</span><span class="sxs-lookup"><span data-stu-id="ec882-160">See Also</span></span>
* [<span data-ttu-id="ec882-161">Holographic リモート処理のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="ec882-161">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="ec882-162">Holographic Remoting ホストアプリの作成</span><span class="sxs-lookup"><span data-stu-id="ec882-162">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="ec882-163">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="ec882-163">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="ec882-164">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="ec882-164">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="ec882-165">Microsoft プライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="ec882-165">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
