---
title: 視線入力
description: 見つめは入力の最初の形式であり、mixed reality 内でターゲットを設定する主な形式です。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed reality、宝石、相互作用、設計
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414371"
---
# <a name="gaze"></a>視線入力

**見つめ**は入力の最初の形式であり、mixed reality 内でターゲットを設定する主な形式です。 宝石は、ユーザーが世界中のどこを見ているかを示し、その意図を判断することができます。 実世界では、通常、対話するオブジェクトを見ていきます。 これは、宝石と同じです。

Mixed reality ヘッドセットでは、ユーザーの頭の位置と向きを使用して、頭を見つめたベクトルを決定します。 このベクトルは、ユーザーの目の間で直接のレーザーポインターと考えることができます。 ユーザーが部屋を見ていくと、アプリケーションはこの射線と独自のホログラムを持つことができ、[空間マッピング](spatial-mapping.md)メッシュを使用して、ユーザーが見ている仮想オブジェクトや実世界オブジェクトを判断できます。

HoloLens 2 では、ユーザーの頭部、視線、またはほぼ手動の相互作用によって相互作用を対象にすることができます。
HoloLens (第1世代) では、通常、ユーザーの顔からターゲットを導き出す必要があります。これは、ユーザーの位置を直接レンダリングしたり操作したりすることではありません。 相互作用が開始されたら、[操作やナビゲーション](gestures.md#composite-gestures)ジェスチャと同様に、ハンドの相対的な動きを使って[ジェスチャ](gestures.md)を制御できます。 イマーシブヘッドセットを使用すると、ヘッド見つめまたはポイント対応の[モーションコントローラー](motion-controllers.md)を使用してターゲットを調整できます。

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a>デバイスのサポート

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>頭を見つめます</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>視線</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> HoloLens 2 に固有のその他のガイダンスは[近日対応予定](index.md#news-and-notes)です。


## <a name="uses-of-gaze"></a>見つめの使用

Mixed reality の開発者として、ヘッドまたは目を見つめながら、さまざまなことを行うことができます。
* アプリは、ユーザーの注意がどこであるかを判断するために、シーン内のホログラムとの間で使用できます。
* アプリでは、ユーザーの宝石に基づいてジェスチャとコントローラーの押下をターゲットにして、ユーザーによる選択、アクティブ化、グラブ、スクロール、またはその他のホログラムとの対話を可能にすることができます。
* アプリを使用すると、空間マッピングメッシュを使用して、宝石を実際の表面に配置できます。
* アプリでは、ユーザーが重要なオブジェクトの方向を確認し*ていない*ことを知ることができます。これにより、アプリは、そのオブジェクトに対して視覚的な合図やオーディオの手掛かりを与えることができます。

## <a name="cursor"></a>カーソル

ヘッドを見つめする場合は、ほとんどのアプリで[カーソル](cursors.md)(またはその他の聴覚/視覚表示) を使用して、ユーザーが対話しようとしている内容に自信を持っている必要があります。 通常、このカーソルを世界中に配置して、頭の中線が1つ目のオブジェクトと交差するようにします。これは、ホログラムや実際の表面です。

![宝石を示すビジュアルカーソルの例](images/cursor.jpg)<br>
*宝石を示すビジュアルカーソルの例*

目を見つめて、通常はカーソルを表示し*ない*ことをお勧めします。これは、ユーザーにとって煩雑で面倒になるためです。 代わりに、視覚的なターゲットを微妙に強調表示するか、非常に薄い目のカーソルを使用して、ユーザーが何を操作しようとしているかについて自信を持っています。 詳細については、HoloLens 2 での[目に基づく入力の設計ガイダンスを](eye-tracking.md)参照してください。

## <a name="giving-action-to-the-users-gaze"></a>ユーザーの宝石にアクションを与える

ユーザーが宝石を使用してホログラムまたは実際のオブジェクトを対象にしたら、次にそのオブジェクトに対してアクションを実行します。 ユーザーがアクションを実行する主な方法は、[ジェスチャ](gestures.md)、[モーションコントローラー](motion-controllers.md) 、[音声](voice-input.md)を使用することです。

## <a name="see-also"></a>関連項目
* [MR 入力 210:頭を見つめます](holograms-210.md)
* [DirectX でのヘッド視線入力とアイ視線入力](gaze-in-directx.md)
* [Unity の頭を見つめます](gaze-in-unity.md)
* [HoloLens 2 での視線](eye-tracking.md)
* [Mixed Reality Toolkit を使用した Unity での視線](https://aka.ms/mrtk-eyes)
