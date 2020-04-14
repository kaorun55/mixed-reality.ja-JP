---
title: Holographic リモート処理のトラブルシューティングと制限事項
description: HoloLens 2 での Holographic Remoting のトラブルシューティングの手順
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality, ホログラム, holographic リモート処理, リモートレンダリング, ネットワークレンダリング, HoloLens, リモートホログラム, トラブルシューティング, ヘルプ
ms.openlocfilehash: c6d8333bf22c3abb254a9f1b6e30a785effa9999
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277350"
---
# <a name="holographic-remoting-troubleshooting"></a>Holographic リモート処理のトラブルシューティング

> [!IMPORTANT]
> このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。

## <a name="spectre-mitigated-libraries-not-found"></a>Spectre の緩和されたライブラリが見つかりません。

Holographic リモート処理サンプルアプリでは、リリース構成で Spectre 軽減策 (/Qspectre) が有効になっています。

"Vccorlib .lib" を開くことができないという致命的なリンカーエラーが発生した場合は、Visual Studio ワークロードに Spectre 軽減可能なライブラリが含まれていることを確認してください。 詳細については、「 https://aka.ms/Ofhn4c」を参照してください。

## <a name="limitations"></a>制限事項

Holographic Remoting を HoloLens 2 に使用する場合、次の Api は現在サポートされて**いません**。特に明記されていない限り、```ERROR_NOT_SUPPORTED``` エラーが発生します。

[Windows.Graphics.Holographic](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [HolographicCamera](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降
  - 以前のバージョンでは、常にエラーが発生します。
* [HolographicViewConfiguration.RequestRenderTargetSize](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - は失敗しませんが、レンダーターゲットのサイズは変更されません。
* [HolographicCameraPose.OverrideProjectionTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose ビューポート](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - は失敗しませんが、深度バッファーはリモート処理されません。
  - サポートされているバージョン[2.1.0](holographic-remoting-version-history.md#v2.1.0)以降
* [HolographicDisplay の構成](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - HolographicViewConfigurationKind にクエリを実行すると、常に ```nullptr```が返されます。
  - サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降
  - 以前のバージョンでは、常にエラーが発生します。
* [HolographicSpace プレゼンテーションモニター](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - は、接続が確立される前に呼び出された場合にエラーを報告します。


[Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [SpatialLocation AbsoluteAngularAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation AbsoluteAngularAccelerationAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation AbsoluteAngularVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation AbsoluteAngularVelocityAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation AbsoluteLinearAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation AbsoluteLinearVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - 常に ```nullptr```を返します。
* [SpatialStageFrameOfReference.RequestNewStageAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [SpatialAnchor. RemovedByUser](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - バージョン[2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。 
  - 以前のバージョンでは、常に ```nullptr```を返します。 
* [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - バージョン[2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。 
  - 以前のバージョンでは、非同期操作は常に ```SpatialPerceptionAccessStatus.DeniedBySystem```で完了しました。
* [SpatialAnchorTransferManager](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - 非同期操作は常に ```SpatialPerceptionAccessStatus.DeniedBySystem```で完了します。
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - 非同期操作は常に ```false```で完了します。
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - 非同期操作は常に ```nullptr```で完了します。

[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview. CreateLocatorForNode](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview. Trycreateofreference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [SpatialInteractionSource](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a>参照
* [Holographic リモート処理のバージョン履歴](holographic-remoting-version-history.md)
* [Holographic リモート処理リモートアプリの作成](holographic-remoting-create-host.md)
* [カスタム Holographic リモート処理プレーヤーアプリの作成](holographic-remoting-create-player.md)
* [Holographic Remoting ソフトウェア ライセンス条項](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
