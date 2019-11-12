---
title: Holographic リモート処理のバージョン履歴
description: HoloLens 2 での Holographic リモート処理のバージョン履歴。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: 9ff6a5f7594eb67dd4c1c8690812ab724cac9012
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926650"
---
# <a name="holographic-remoting-version-history"></a>Holographic リモート処理のバージョン履歴

> [!IMPORTANT]
> このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。

## バージョン 2.0.14 (2019 年10月26日)<a name="v2.0.14"></a>
* New PerceptionDevice Api のサポート (Windows 10 11 月2019更新プログラム)。
* SpatialGestureRecognizer によって保留中のジェスチャイベントがトリガーされない問題を修正しました。
* SpatialSurfaceObserver を使用する場合のスレッド処理の問題を修正します。 SetBoundingVolume。

## バージョン 2.0.12 (2019 年10月18日)<a name="v2.0.12"></a>
* NavigationRail (X/Y/Z) を使用するときの SpatialGestureRecognizer のクラッシュを修正します。

## バージョン 2.0.10 (2019 年10月10日)<a name="v2.0.10"></a>
* VR コントローラーの [トリガー] ボタンを使用するときのクラッシュを修正します。 Holographic リモート処理はコントローラーを完全にサポートしていません。 HoloLens 2 とペアになっている場合は、[トリガー] ボタンと [Windows] ボタンのみが動作します。

## バージョン 2.0.9 (2019 年9月19日)<a name="v2.0.9"></a>
* [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)のサポートを追加しました
* 次のメンバーを提供する新しいインターフェイス ```IPlayerContext2``` (```PlayerContext```によって実装されます) を追加しました。
  - [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)プロパティ。
* ```Failed_RemoteFrameTooOld``` 値を ```BlitResult``` に追加しました
* 安定性と信頼性の向上

## バージョン 2.0.8 (2019 年8月20日)<a name="v2.0.8"></a>

* [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as パラメーターを指定して[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)を呼び出すときのクラッシュを修正します。
* 安定性と信頼性の向上

## バージョン 2.0.7 (2019 年7月26日)<a name="v2.0.7"></a>

* HoloLens 2 の Holographic リモート処理の最初のパブリックリリース。

## <a name="see-also"></a>参照
* [カスタム Holographic リモート処理プレーヤーアプリの作成](holographic-remoting-create-player.md)
* [Holographic Remoting ホストアプリの作成](holographic-remoting-create-host.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic Remoting ソフトウェア ライセンス条項](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
