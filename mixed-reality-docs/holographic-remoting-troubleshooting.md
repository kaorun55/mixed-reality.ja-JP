---
title: Holographic リモート処理のトラブルシューティングと制限事項
description: HoloLens 2 での Holographic Remoting のトラブルシューティングの手順
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 10/28/2019
ms.topic: article
keywords: Windows Mixed Reality, ホログラム, holographic リモート処理, リモートレンダリング, ネットワークレンダリング, HoloLens, リモートホログラム, トラブルシューティング, ヘルプ
ms.openlocfilehash: 7b438d9169c9306e0056655e561c04b62b1662cf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434236"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="b9c5d-104">Holographic リモート処理のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b9c5d-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9c5d-105">このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="b9c5d-106">Spectre の緩和されたライブラリが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="b9c5d-107">Holographic リモート処理サンプルアプリでは、リリース構成で Spectre 軽減策 (/Qspectre) が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="b9c5d-108">"Vccorlib .lib" を開くことができないという致命的なリンカーエラーが発生した場合は、Visual Studio ワークロードに Spectre 軽減可能なライブラリが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="b9c5d-109">詳細については、「 https://aka.ms/Ofhn4c 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="b9c5d-110">制限事項</span><span class="sxs-lookup"><span data-stu-id="b9c5d-110">Limitations</span></span>

<span data-ttu-id="b9c5d-111">Holographic Remoting を HoloLens 2 に使用する場合、次の Api は現在サポートされて**いません**。特に明記されていない限り、```ERROR_NOT_SUPPORTED``` エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="b9c5d-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="b9c5d-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="b9c5d-113">HolographicCamera</span><span class="sxs-lookup"><span data-stu-id="b9c5d-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [<span data-ttu-id="b9c5d-114">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="b9c5d-114">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="b9c5d-115">HolographicCameraPose ビューポート</span><span class="sxs-lookup"><span data-stu-id="b9c5d-115">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="b9c5d-116">HolographicCameraPose</span><span class="sxs-lookup"><span data-stu-id="b9c5d-116">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="b9c5d-117">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="b9c5d-117">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="b9c5d-118">は失敗しませんが、深度バッファーはリモート処理されません。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-118">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="b9c5d-119">HolographicDisplay の構成</span><span class="sxs-lookup"><span data-stu-id="b9c5d-119">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [<span data-ttu-id="b9c5d-120">HolographicSpace プレゼンテーションモニター</span><span class="sxs-lookup"><span data-stu-id="b9c5d-120">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[<span data-ttu-id="b9c5d-121">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="b9c5d-121">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="b9c5d-122">SpatialLocation AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="b9c5d-122">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="b9c5d-123">SpatialLocation AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="b9c5d-123">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="b9c5d-124">SpatialLocation AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="b9c5d-124">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="b9c5d-125">SpatialLocation AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="b9c5d-125">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="b9c5d-126">SpatialLocation AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="b9c5d-126">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="b9c5d-127">SpatialLocation AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="b9c5d-127">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="b9c5d-128">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="b9c5d-128">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="b9c5d-129">常に ```nullptr```を返します。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-129">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="b9c5d-130">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="b9c5d-130">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="b9c5d-131">SpatialAnchor. RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="b9c5d-131">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="b9c5d-132">SpatialAnchorExporter</span><span class="sxs-lookup"><span data-stu-id="b9c5d-132">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="b9c5d-133">バージョン[2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-133">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="b9c5d-134">以前のバージョンでは、常に ```nullptr```を返します。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-134">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="b9c5d-135">SpatialAnchorExporter</span><span class="sxs-lookup"><span data-stu-id="b9c5d-135">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="b9c5d-136">バージョン[2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-136">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="b9c5d-137">以前のバージョンでは、非同期操作は常に ```SpatialPerceptionAccessStatus.DeniedBySystem```で完了しました。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-137">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="b9c5d-138">SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="b9c5d-138">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="b9c5d-139">非同期操作は常に ```SpatialPerceptionAccessStatus.DeniedBySystem```で完了します。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-139">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="b9c5d-140">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="b9c5d-140">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="b9c5d-141">非同期操作は常に ```false```で完了します。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-141">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="b9c5d-142">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="b9c5d-142">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="b9c5d-143">非同期操作は常に ```nullptr```で完了します。</span><span class="sxs-lookup"><span data-stu-id="b9c5d-143">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="b9c5d-144">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="b9c5d-144">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="b9c5d-145">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="b9c5d-145">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="b9c5d-146">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="b9c5d-146">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="b9c5d-147">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="b9c5d-147">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="b9c5d-148">SpatialGraphInteropPreview. CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="b9c5d-148">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="b9c5d-149">SpatialGraphInteropPreview. Trycreateofreference</span><span class="sxs-lookup"><span data-stu-id="b9c5d-149">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="b9c5d-150">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="b9c5d-150">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="b9c5d-151">参照</span><span class="sxs-lookup"><span data-stu-id="b9c5d-151">See Also</span></span>
* [<span data-ttu-id="b9c5d-152">Holographic リモート処理のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="b9c5d-152">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="b9c5d-153">Holographic Remoting ホストアプリの作成</span><span class="sxs-lookup"><span data-stu-id="b9c5d-153">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="b9c5d-154">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="b9c5d-154">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="b9c5d-155">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="b9c5d-155">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="b9c5d-156">Microsoft のプライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="b9c5d-156">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
