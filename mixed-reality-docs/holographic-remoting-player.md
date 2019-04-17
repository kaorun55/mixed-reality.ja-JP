---
title: リモート処理の holographic プレーヤー
description: リモート処理の Holographic のプレイヤーとは、Holographic のリモート処理をサポートする PC のアプリおよびゲームに接続するコンパニオン アプリです。 Holographic のリモート処理で、Microsoft HoloLens を PC から holographic のコンテンツをストリーム リアルタイム、Wi-fi 接続を使用します。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、リモート処理、Holographic のリモート処理
ms.openlocfilehash: 16add6c72b594822cacbef6c92ce196ab9b13429
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605001"
---
# <a name="holographic-remoting-player"></a>リモート処理の holographic プレーヤー

リモート処理の Holographic のプレイヤーとは、Holographic のリモート処理をサポートする PC のアプリおよびゲームに接続するコンパニオン アプリです。 Holographic のリモート処理で、Microsoft HoloLens を PC から holographic のコンテンツをストリーム リアルタイム、Wi-fi 接続を使用します。

Holographic のリモート処理 Player は、Holographic のリモート処理をサポートするために作られた PC のアプリでのみ使用できます。

> [!NOTE]
> HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。

## <a name="connecting-to-the-holographic-remoting-player"></a>リモート処理の Holographic プレーヤーへの接続

Holographic のリモート処理 Player に接続するアプリの手順に従います。 リモート処理のプレイヤーのメイン画面上の「次のように、HoloLens デバイスの IP アドレスを入力する必要があります。

![リモート処理の holographic プレーヤー](images/holographicremotingplayer.png)

メイン画面が表示されるたびに、接続されているアプリがないことがわかります。

Holographic のリモート処理接続は**暗号化されていない**します。 Holographic のリモート処理は、信頼できるセキュリティで保護された Wi-fi 接続経由で常に使用する必要があります。

## <a name="quality-and-performance"></a>品質とパフォーマンス

品質およびパフォーマンスのエクスペリエンスの 3 つの要因に基づいて異なります。
* **ホログラフィック操作を実行している**-高速の PC またはワイヤレス接続を高速、高解像度または詳細なコンテンツを表示するアプリは必要があります。
* **お客様の PC のハードウェア**-PC を実行し、1 秒あたり 60 フレームで、ホログラフィック操作をエンコードすることができる必要があります。 グラフィックス カードは、一般的な推奨 GeForce GTX 970 または AMD Radeon R9 290 またはそれ以上。 ここでも、特定のエクスペリエンスには、上位または下位のカードが必要です。
* **Wi-fi 接続**-Wi-fi 経由で、ホログラフィック操作がストリーミングされます。 低輻輳で品質を最大限に高速ネットワークを使用します。 イーサネット ケーブルを介して接続されている PC を使用して、Wi-fi ではなく向上にも品質。

## <a name="diagnostics"></a>診断

接続の品質を測定するには、たとえば **「診断を有効にする」** Holographic のリモート処理のプレイヤーのメイン画面にします。 診断を有効にするアプリが表示されます。
* **FPS** - レンダリングされたフレームの数の平均値、リモート処理のプレーヤーを受け取って 1 秒あたりのレンダリングします。 理想では、60 FPS です。
* **待機時間**-お使いの PC から、HoloLens に移動するためのフレームにかかる平均時間。 小さいほど良いです。 これは、Wi-fi ネットワークに大きく依存します。

メインの画面で言うことができる **「診断を無効にする」** 診断をオフにします。

## <a name="pc-system-requirements"></a>PC のシステム要件
* お使いの PC**する必要があります**Windows 10 Anniversary Update を実行します。
* GeForce GTX 970 または AMD Radeon R9 290 または改善のグラフィックス カードをお勧めします。
* お使いの PC をワイヤレス ホップの数を減らすイーサネット経由でネットワークに接続することをお勧めします。

## <a name="see-also"></a>関連項目
* [ソフトウェア ライセンス条項の holographic のリモート処理](microsoft-holographic-remoting-software-license-terms.md)
* [Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
