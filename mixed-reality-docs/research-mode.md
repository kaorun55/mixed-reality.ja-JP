---
title: HoloLens Research モード
description: HoloLens で Research モードを使用すると、アプリケーションは主要なデバイスセンサーストリーム (深さ、環境追跡、および赤外線反射) にアクセスできます。
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: research モード, cv, rs4, コンピュータービジョン, 研究, HoloLens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829935"
---
# <a name="hololens-research-mode"></a>HoloLens Research モード

> [!NOTE]
> この機能は、HoloLens 用の[Windows 10 April 2018 更新プログラム](release-notes-april-2018.md)の一部として追加されたものであり、以前のリリースでは使用できません。

Research モードは、デバイス上のキーセンサーへのアプリケーションアクセスを提供する HoloLens の新機能です。 これには次が含まれます。
- マップの構築とヘッド追跡のためにシステムで使用される4つの環境追跡カメラ。
- 深度カメラデータの2つのバージョン (高周波数 (30 FPS) のほぼ詳細な検出、通常は手動での追跡、および空間マッピングで現在使用されている低頻度 (1 FPS) の詳細な検出のため)
- IR 反射反射ストリームの2つのバージョン。 HoloLens では深度を計算するために使用されますが、これらのイメージは HoloLens から照らされ、アンビエントライトによって適度に影響を受けないという利点があります。

![Research モードアプリのスクリーンショット](images/sensor-stream-viewer.jpg)<br>
*リサーチモードで使用可能な8個のセンサーストリームを表示するテストアプリケーションの mixed reality キャプチャ*

## <a name="device-support"></a>デバイスのサポート

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>リサーチモード</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a>調査モードを使用する前に

リサーチモードは、"Computer Vision" と "ロボット" のフィールドの新しいアイデアを試す教育機関および産業用の研究者を対象としています。  リサーチモードは、企業全体に展開されるか、Microsoft Store で利用可能になるアプリケーションを対象としたものではありません。 その理由は、リサーチモードはデバイスのセキュリティを低下させ、通常の操作よりもはるかに多くのバッテリ電源を消費するためです。 今後のデバイスでは、このモードのサポートに対するコミットは行われません。 そのため、新しいアイデアを開発してテストするために使用することをお勧めします。ただし、リサーチモードを使用するアプリケーションを広く展開することはできません。また、将来のハードウェアでも引き続き動作することが保証されています。

## <a name="enabling-research-mode"></a>リサーチモードを有効にする

リサーチモードは、開発者モードのサブモードです。 まず、設定アプリで開発者モードを有効にする必要があります (**開発者向け & セキュリティ > の設定 > 更新**)。

1. [開発機能の使用] を **[オン**] に設定します。
2. [デバイスポータルを有効にする] を **[オン**] に設定します。

次に、HoloLens と同じ Wi-fi ネットワークに接続されている web ブラウザーを使用して、HoloLens の IP アドレスに移動します (**設定 > network & Internet > wi-fi > ハードウェアプロパティ**)。 これは[デバイスポータル](using-the-windows-device-portal.md)であり、ポータルの [システム] セクションに "リサーチモード" ページがあります。

![HoloLens デバイスポータルの [リサーチモード] タブ](images/ResearchModeDevPortal.png)<br>
*HoloLens デバイスポータルでのリサーチモード*

[**センサーストリームへのアクセスを許可**する] を選択した後、HoloLens を再起動する必要があります。 これを行うには、デバイスポータルのページ上部にある [Power] (電源) メニュー項目を使用します。

デバイスが再起動されると、デバイスポータルから読み込まれたアプリケーションは、リサーチモードのストリームにアクセスできるようになります。

## <a name="using-sensor-data-in-your-apps"></a>アプリでセンサーデータを使用する

アプリケーションは、写真/ビデオカメラストリームにアクセスするのとまったく同じ方法で[メディアファンデーション](https://msdn.microsoft.com/library/windows/desktop/ms694197)ストリームを開くことによって、センサーストリームデータにアクセスできます。 

HoloLens 開発に使用できるすべての Api は、リサーチモードでも使用できます。 特に、アプリケーションは、各センサーフレームのキャプチャ時間において HoloLens が6つの領域にある場所を正確に把握できます。

さまざまなリサーチモードのストリームにアクセスする方法、組み込みと extrを使用する方法、およびストリームを記録する方法を示すサンプルアプリケーションは、 [HoloLensForCV GitHub リポジトリ](https://github.com/Microsoft/HoloLensForCV)で入手できます。

## <a name="known-issues"></a>既知の問題

HoloLensForCV リポジトリの[問題トラッカー](https://github.com/Microsoft/HololensForCV/issues)をご覧ください。

## <a name="see-also"></a>関連項目

* [Microsoft メディア ファンデーション](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV GitHub リポジトリ](https://github.com/Microsoft/HoloLensForCV)
* [Windows Device Portal を使用する](using-the-windows-device-portal.md)
