---
title: Spectator ビュー
description: 外部ディスプレイで mixed reality エクスペリエンスをデモンストレーションする手段として、または mixed reality エクスペリエンスのビデオを録画する手段として、外部デバイスからホログラムを視覚化します。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator View、iPhone、iOS、iPad、OpenCV、カメラ、ARKit、HoloLens、Mixed Reality、MixedRealityToolkit、demo、record
ms.openlocfilehash: 135a566456f1000669d2033edcf0d0b4649ccdf3
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387669"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>HoloLens および HoloLens 用 Spectator ビュー2

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>概要

HoloLens を装着すると、それを持っていない人は、可能な偉大なる象徴を体験することができなくなります。 Spectator View を使用すると、他のユーザーは、世界で HoloLens ユーザーに表示される2D 画面で見ることができます。
Spectator View は、モバイルデバイスで HD のホログラムを記録するための、高速で手頃な価格のアプローチを提供します。 また、ビデオカメラを使用したホログラムの高品質記録も提供します。

## <a name="key-resources"></a>主要リソース

* [**GitHub の Spectator ビュー**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**構造**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Architecture.md)
* [**Samples**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)
* [**モバイルセットアップの手順**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.md)
* [**ビデオカメラのセットアップ手順**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.VideoCamera.md)

## <a name="use-cases"></a>ユース ケース
* IPhone または Android デバイスを使用して、mixed reality エクスペリエンスを記録できます。 フル HD で記録し、ホログラムと偶数の影にアンチエイリアシングを適用します。 これは、ホログラムのビデオをキャプチャする費用効果が高く、迅速な方法です。
* ライブ mixed reality エクスペリエンスを iPhone または iPad から直接 Apple TV にストリーミングし、すぐに利用できるようにします。
* ゲストとのエクスペリエンスを共有します。非 HoloLens ユーザーが自分の電話やタブレットから直接ホログラムを使用できるようにします。

## <a name="current-features"></a>現在の機能

* ホログラムの空間同期によって、すべてのユーザーが同じ場所でホログラムを確認できるようになります。
* iOS (ARKit 対応デバイス) と Android (Arkit 対応デバイス) はサポートされています。
複数の iOS ゲスト。
ビデオ + ホログラム + アンビエントサウンド + ホログラムサウンドの記録。
ビデオを保存したり、電子メールで送信したり、他のサポートアプリと共有したりできるように、シートを共有します。

![](images/SpecViewPhoneDemo.jpg)
マーカーマーカー![マーカー](images/hololensspectatorview-500px.jpg) ![](images/spectatorview-300px.png)

次の表は、Spectator ビューのさまざまな機能とその機能を示しています。 ビデオ記録のニーズに最適なオプションを選択します。

|                                      | 携帯                  |                    ビデオカメラ              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD 品質                           |         フル HD         |        Professional quality 撮影 (ビデオカメラによって決定)      |
| カメラの移動を簡単に                 |            ✔            |                      ✔                      |
| 3人のユーザービュー                    |            ✔            |                      ✔                      |
| 画面にストリームできます           |            ✔            |                      ✔                      |
| 移植性があります。                             |            ✔            |                                             |
| ワイヤレス                             |            ✔            |                                             |
| 追加の必要なハードウェア         |     Android フォン、iPhone    | HoloLens + テストマシン + 三脚 + ビデオカメラ + PC + Unity |
| ハードウェア投資                  |           Low            |                     高                    |
| クロスプラットフォーム                       |           Android、iOS   |                                             |
| 同期されたコンテンツ                 |            ✔            |                      ✔                      |
| ランタイムのセットアップ期間               |         リプレイ          |                     スロー (低速)                    |
## <a name="see-also"></a>関連項目

* [複合現実キャプチャ](mixed-reality-capture.md) 
* [開発者向け複合現実キャプチャ](mixed-reality-capture-for-developers.md)
* [複合現実での共有エクスペリエンス](shared-experiences-in-mixed-reality.md)
