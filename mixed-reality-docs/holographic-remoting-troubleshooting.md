---
title: Holographic リモート処理のトラブルシューティングと制限事項
description: HoloLens 2 での Holographic Remoting のトラブルシューティングの手順
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 08/01/2019
ms.topic: article
keywords: Windows Mixed Reality, ホログラム, holographic リモート処理, リモートレンダリング, ネットワークレンダリング, HoloLens, リモートホログラム, トラブルシューティング, ヘルプ
ms.openlocfilehash: 86b6979dbfc9b514b3af13ebdcc3d3ece17e6335
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718146"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="491ac-104">Holographic リモート処理のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="491ac-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="491ac-105">このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="491ac-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="491ac-106">Spectre の緩和されたライブラリが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="491ac-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="491ac-107">Holographic リモート処理サンプルアプリでは、リリース構成で Spectre 軽減策 (/Qspectre) が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="491ac-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="491ac-108">"Vccorlib .lib" を開くことができないという致命的なリンカーエラーが発生した場合は、Visual Studio ワークロードに Spectre 軽減可能なライブラリが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="491ac-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="491ac-109">詳細については、「 https://aka.ms/Ofhn4c 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="491ac-109">See https://aka.ms/Ofhn4c for more information.</span></span>

# <a name="limitations"></a><span data-ttu-id="491ac-110">制限事項</span><span class="sxs-lookup"><span data-stu-id="491ac-110">Limitations</span></span>

<span data-ttu-id="491ac-111">Holographic Remoting を HoloLens 2 に使用する場合、次の api は現在サポートされ```ERROR_NOT_SUPPORTED```て**いません**。特に明記されていない限り、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="491ac-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="491ac-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="491ac-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="491ac-113">HolographicCamera</span><span class="sxs-lookup"><span data-stu-id="491ac-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [<span data-ttu-id="491ac-114">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="491ac-114">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="491ac-115">HolographicCameraPose ビューポート</span><span class="sxs-lookup"><span data-stu-id="491ac-115">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="491ac-116">HolographicCameraPose</span><span class="sxs-lookup"><span data-stu-id="491ac-116">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* <span data-ttu-id="491ac-117">[HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)は失敗しませんが、深度バッファーはリモート処理されません。</span><span class="sxs-lookup"><span data-stu-id="491ac-117">[HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) - Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="491ac-118">HolographicDisplay の構成</span><span class="sxs-lookup"><span data-stu-id="491ac-118">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [<span data-ttu-id="491ac-119">HolographicSpace プレゼンテーションモニター</span><span class="sxs-lookup"><span data-stu-id="491ac-119">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[<span data-ttu-id="491ac-120">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="491ac-120">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="491ac-121">SpatialLocation AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="491ac-121">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="491ac-122">SpatialLocation AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="491ac-122">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="491ac-123">SpatialLocation AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="491ac-123">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="491ac-124">SpatialLocation AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="491ac-124">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="491ac-125">SpatialLocation AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="491ac-125">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/is-is/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="491ac-126">SpatialLocation AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="491ac-126">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* <span data-ttu-id="491ac-127">[SpatialStageFrameOfReference](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) -常にを返し```nullptr```ます。</span><span class="sxs-lookup"><span data-stu-id="491ac-127">[SpatialStageFrameOfReference.Current](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) - Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="491ac-128">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="491ac-128">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="491ac-129">SpatialAnchor. RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="491ac-129">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* <span data-ttu-id="491ac-130">[SpatialAnchorExporter-常にを返し```nullptr```ます。](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)</span><span class="sxs-lookup"><span data-stu-id="491ac-130">[SpatialAnchorExporter.GetDefault](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
) - Always returns ```nullptr```.</span></span>
* <span data-ttu-id="491ac-131">[SpatialAnchorExporter 操作は、常にで```SpatialPerceptionAccessStatus.DeniedBySystem```完了します。](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)</span><span class="sxs-lookup"><span data-stu-id="491ac-131">[SpatialAnchorExporter.RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
) - Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* <span data-ttu-id="491ac-132">[SpatialAnchorTransferManager](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)操作は、常にで```SpatialPerceptionAccessStatus.DeniedBySystem```完了します。</span><span class="sxs-lookup"><span data-stu-id="491ac-132">[SpatialAnchorTransferManager.RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync) - Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* <span data-ttu-id="491ac-133">[SpatialAnchorTransferManager TryExportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_) -Async 操作は常にで```false```完了します。</span><span class="sxs-lookup"><span data-stu-id="491ac-133">[SpatialAnchorTransferManager.TryExportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_) - Async operation always completes with ```false```.</span></span>
* <span data-ttu-id="491ac-134">[SpatialAnchorTransferManager TryImportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
) -Async 操作は常にで```nullptr```完了します。</span><span class="sxs-lookup"><span data-stu-id="491ac-134">[SpatialAnchorTransferManager.TryImportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
) - Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="491ac-135">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="491ac-135">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="491ac-136">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="491ac-136">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="491ac-137">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="491ac-137">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="491ac-138">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="491ac-138">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="491ac-139">SpatialGraphInteropPreview. CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="491ac-139">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="491ac-140">SpatialGraphInteropPreview. Trycreateofreference</span><span class="sxs-lookup"><span data-stu-id="491ac-140">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="491ac-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="491ac-141">See Also</span></span>
* [<span data-ttu-id="491ac-142">Holographic Remoting ホストアプリの作成</span><span class="sxs-lookup"><span data-stu-id="491ac-142">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="491ac-143">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="491ac-143">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="491ac-144">Holographic リモート処理ソフトウェアライセンス条項</span><span class="sxs-lookup"><span data-stu-id="491ac-144">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="491ac-145">Microsoft のプライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="491ac-145">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)