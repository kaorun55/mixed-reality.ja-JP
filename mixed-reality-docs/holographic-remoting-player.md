---
title: Holographic リモート処理プレーヤー
description: Holographic Remoting Player は、Holographic リモート処理をサポートする PC アプリやゲームに接続するコンパニオンアプリです。 Holographic リモート処理では、Wi-fi 接続を使用して、PC から Microsoft HoloLens にコンテンツを Holographic します。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: b8354295f9752e73cc9b34c1769254e49808b63f
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813722"
---
# <a name="holographic-remoting-player"></a>Holographic リモート処理プレーヤー

Holographic Remoting Player は、Holographic リモート処理をサポートする PC アプリやゲームに接続するコンパニオンアプリです。 Holographic リモート処理では、Wi-fi 接続を使用して、PC から Microsoft HoloLens にコンテンツを Holographic します。

Holographic リモート処理プレーヤーは、特に Holographic リモート処理をサポートするように設計された PC アプリでのみ使用できます。

Holographic リモート処理プレーヤーは、HoloLens と HoloLens 2 の両方で使用できます。  Hololens を使用した Holographic リモート処理をサポートする PC アプリは、HoloLens 2 で Holographic Remをサポートするように更新する必要があります。  サポートされているバージョンについて不明な点がある場合は、アプリプロバイダーにお問い合わせください。

## <a name="connecting-to-the-holographic-remoting-player"></a>Holographic リモート処理プレーヤーに接続する

アプリの指示に従って、Holographic リモート処理プレーヤーに接続します。 HoloLens デバイスの IP アドレスを入力する必要があります。これは、次のように、リモート処理プレーヤーのメイン画面で確認できます。

![Holographic リモート処理プレーヤー](images/holographicremotingplayer.png)

メイン画面が表示されるたびに、アプリが接続されていないことがわかります。

Holographic remoting 接続は暗号化されて**いない**ことに注意してください。 信頼できる Wi-fi 接続では、常に Holographic リモート処理を使用する必要があります。

## <a name="quality-and-performance"></a>品質とパフォーマンス

エクスペリエンスの品質とパフォーマンスは、次の3つの要因によって異なります。
* 実行している**holographic エクスペリエンス**-高解像度または高度なコンテンツをレンダリングするアプリでは、より高速な PC またはより高速なワイヤレス接続が必要になる場合があります。
* **Pc のハードウェア**-pc は、1秒あたり60のフレームで holographic エクスペリエンスを実行およびエンコードできる必要があります。 グラフィックスカードの場合は、一般に、GeForce GTX 970 または AMD Radeon R9 290 以上をお勧めします。 ここでも、特定のエクスペリエンスでは、より高いまたは低いカードが必要になる場合があります。
* Wi-fi**接続**-holographic エクスペリエンスは wi-fi 経由でストリーミングされます。 低負荷の高速ネットワークを使用して、品質を最大化します。 Wi-fi ではなくイーサネットケーブルで接続されている PC を使用すると、品質が向上する場合もあります。

## <a name="diagnostics"></a>診断

接続の品質を測定するには、Holographic リモート処理プレーヤーのメイン画面で [**診断の有効化]** を言います。 診断が有効になっている場合、アプリには次の情報が表示されます。
* **FPS** -リモートプレーヤーが受信して1秒間にレンダリングするレンダリングフレームの平均数。 最適なは 60 FPS です。
* **[待機時間]** -フレームが PC から HoloLens に移動するまでにかかる平均時間。 精度が低下します。 これは、Wi-fi ネットワークに大きく依存します。

メイン画面では、 **[診断を無効**にする] を使用して診断を無効にすることができます。

## <a name="pc-system-requirements"></a>PC のシステム要件
* お使いの PC では、Windows 10 の記念日更新以降が実行されている**必要があり**ます。
* GeForce GTX 970 または AMD Radeon R9 290 以上のグラフィックスカードをお勧めします。
* ワイヤレスホップの数を減らすには、コンピューターをイーサネット経由でネットワークに接続することをお勧めします。

## <a name="see-also"></a>関連項目
* [Holographic リモート ソフトウェア ライセンス条項](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
