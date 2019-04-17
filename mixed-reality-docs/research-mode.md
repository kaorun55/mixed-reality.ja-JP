---
title: HoloLens 研究モード
description: HoloLens の研究モードを使用して、アプリケーションは、主要なデバイス センサー ストリーム (深さ、追跡、環境および IR 反射) にアクセスできます。
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: モード、cv、rs4、コンピューター ビジョン研究、HoloLens を調査します。
ms.openlocfilehash: 5feda021bd6a1a90fd98c751b1cea768eed980af
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597511"
---
# <a name="hololens-research-mode"></a>HoloLens 研究モード

> [!NOTE]
> この機能は、の一部として追加された、 [Windows 10 April 2018 Update](release-notes-april-2018.md) HoloLens のと、以前のリリースでは使用できません。

研究モードは、デバイスにアプリケーション キーのセンサーへのアクセスを提供する HoloLens の新しい機能です。 次のようなクラスがあります。
- 4 つのマップの構築と head の追跡、システムで使用されるカメラを追跡する環境。
- 深度カメラ データ – 高頻度 (30 FPS) 深さの近くの検知、一般的に使用される追跡と低頻度 (1 FPS) 深さまで検出用の 2 つのバージョンは、空間のマッピングによって現在使用
- これらのイメージ、HoloLens から明るいとある程度周辺光による影響を受けるは、深さが価値ある独自の権限でのコンピューティングするために使用、HoloLens、IR 反射ストリームの 2 つのバージョン。

![Research モードのアプリのスクリーン ショット](images/sensor-stream-viewer.jpg)<br>
*Research モードで使用可能な 8 つのセンサー ストリームを表示するテスト アプリケーションの複合現実のキャプチャ*

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>機能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> 研究モード</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="before-using-research-mode"></a>調査モードを使用する前に

という名前の研究モード: コンピューター ビジョンとロボット工学のフィールドに新しいアイデアを試す学術的および産業の研究者に適しています。  研究モードは、企業全体に展開または Microsoft Store で使用できるアプリケーションのものではありません。 この理由は、研究モードは、デバイスのセキュリティを削減し、通常の操作よりもはるかに多くのバッテリ電力を消費です。 Microsoft は、将来のデバイスでこのモードをサポートしていないコミットしています。 そのため、開発し、新しいアイデアをテストに使用する推奨します。ただし、広くは引き続き将来のハードウェアで動作する任意の保証、研究モードを使用して、またはアプリケーションをデプロイすることはできません。

## <a name="enabling-research-mode"></a>調査モードを有効にします。

研究モードは、開発者モードのサブ モードです。 まず、設定アプリで開発者モードを有効にする必要があります (**設定 > 更新とセキュリティ > 開発者向け**)。

1. 「開発者向けの機能を使用して、」を設定**で**
2. 「デバイスのポータルを有効にする」を設定**で**

HoloLens の IP アドレスに移動し、HoloLens と同じ Wi-fi ネットワークに接続されている web ブラウザーを使用して (経由で取得した**設定 > ネットワークとインターネット > Wi-fi > ハードウェア プロパティ**)。 これは、[デバイス ポータル](using-the-windows-device-portal.md)、およびポータルの"System"セクションでは「Research モード」ページが表示されます。

![HoloLens デバイス ポータルの [モード] タブを調査します。](images/ResearchModeDevPortal.png)<br>
*HoloLens デバイスのポータルでの研究モード*

選択した後**センサー ストリームへのアクセスを許可する**HoloLens を再起動する必要があります。 これは、ページの上部にある"Power"のメニュー項目で、デバイス ポータルから行うことができます。

デバイスの再起動後デバイス ポータルから読み込まれているアプリケーションは Research モードのストリームにアクセスできる必要があります。

## <a name="using-sensor-data-in-your-apps"></a>アプリでのセンサー データの使用

アプリケーションは開くことでセンサー データのストリームにアクセスできます[メディア ファンデーション](https://msdn.microsoft.com/library/windows/desktop/ms694197)写真とビデオのカメラのストリームにアクセスする、まったく同じ方法でストリーム。 

HoloLens の開発に使用できるすべての Api も調査モードで使用できます。 具体的には、アプリケーションは正確に場所がわかっている HoloLens 6 dof 領域で各センサーのフレームのキャプチャ時にします。

さまざまな調査モードのストリームにアクセスする方法、組み込みおよび extrinsics を使用する方法、およびストリームを記録する方法を示すサンプル アプリケーションが表示されます、 [HoloLensForCV GitHub リポジトリ](https://github.com/Microsoft/HoloLensForCV)します。

## <a name="known-issues"></a>既知の問題

参照してください、 [issue トラッカー](https://github.com/Microsoft/HololensForCV/issues) HoloLensForCV リポジトリにします。

## <a name="see-also"></a>関連項目

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV GitHub リポジトリ](https://github.com/Microsoft/HoloLensForCV)
* [Windows Device Portal のを使用](using-the-windows-device-portal.md)
