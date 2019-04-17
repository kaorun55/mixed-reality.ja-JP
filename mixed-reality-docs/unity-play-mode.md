---
title: Unity の再生モード
description: Unity エディターで再生モードを使用して、アプリを展開することがなく、デバイスで変更をプレビューします。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、リモート処理、holographic のリモート処理、プレーヤーの holographic のリモート処理
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597824"
---
# <a name="unity-play-mode"></a>Unity の再生モード

Unity プロジェクトの作業をする高速の方法では、「再生モード」を使用します。 これは、アプリを実行、ローカル Unity エディターで、PC に。 Unity では、Holographic のリモート処理を使用して、実際の HoloLens デバイスでコンテンツをプレビューする高速の方法を提供します。

## <a name="unity-play-mode-with-holographic-remoting"></a>リモート処理で Holographic unity 再生モード

Holographic リモート処理では、Unity エディターで、PC で実行中、HoloLens でアプリが発生することができます。 視線、ジェスチャ、音声、および入力空間のマッピングは、お使いのコンピューター、HoloLens から送信されます。 レンダリングされたフレーム、HoloLens に送信されます。 これは、迅速に構築および完全なプロジェクトを展開することがなく、アプリをデバッグする優れた方法です。
1. HoloLens に移動し、 **Microsoft Store**をインストールし、 **[Holographic のリモート処理 Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** アプリ。
2. HoloLens、起動、 **Holographic のリモート処理 Player**アプリ。
3. Unity に移動、**ウィンドウ**メニュー選択し、 **Holographic エミュレーション**します。
4. 設定**エミュレーション モード**に**デバイスにリモート**します。
5. **リモート マシン**、HoloLens の IP アドレスを入力します。
6. **[接続]** をクリックします。 わかります**接続の状態**変更**接続済み**HoloLens で空白の画面が表示とします。
7. をクリックして、**再生**再生モードを開始し、HoloLens でアプリを体験するボタンをクリックします。

Holographic のリモート処理では、高速の PC と Wi-fi 接続が必要です。 参照してください[Holographic のリモート処理 Player](holographic-remoting-player.md)の完全な詳細情報。

最良の結果をアプリが正しく設定を確認します、[フォーカス ポイント](focus-point-in-unity.md)します。 これにより、最適なワイヤレス接続の待機時間にシーンを適応させる Holographic のリモート処理ができます。

## <a name="see-also"></a>関連項目
* [リモート処理の holographic プレーヤー](holographic-remoting-player.md)
