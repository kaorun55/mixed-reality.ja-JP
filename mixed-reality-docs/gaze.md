---
title: 視線入力
description: 視線の先は、入力の最初のフォームでの複合現実内で対象とする主な形式です。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 設計、実際には、視線の先、相互作用を混在
ms.openlocfilehash: 9e50067f9dfeacf3dce5ea9a928990d1b142e4d0
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453709"
---
# <a name="gaze"></a>視線入力

**視線**入力の最初のフォームは、複合現実内で対象とするの主な形式です。 視線の先では、ユーザーが世界中を検索していると、その目的を決定することができますを指示します。 現実の世界ではする通常と対話するオブジェクトについて説明します。 これは、視線入力と同じです。

Mixed reality ヘッドセットでは、位置とユーザーの頭の向きを使用して、そのヘッド視線入力ベクトルを決定します。 このベクトルは、ユーザーの目の間で直接からまっすぐレーザー ポインタとして考えることができます。 アプリケーションことができます独自ホログラムとでこの射線が交差するように、ユーザーは、部屋は、[空間マッピング](spatial-mapping.md)メッシュがどのようなユーザーが表示されます仮想または実際のオブジェクトを決定します。

HoloLens 2 は、相互作用はユーザーのヘッド視線入力、目視線の先の対象となることができます、近くまでまたはまたは相互作用をはるかに渡します。
HoloLens で (第 1 世代)、そのユーザーの視線入力ヘッドからターゲットではなくしようとしてレンダリングまたはして手のアイコンの場所に直接対話の相互作用の派生一般にします。 コントロールに手の相対的な動きを使用可能性があります相互作用が開始されたら、[ジェスチャ](gestures.md)と同様、[操作やナビゲーション](gestures.md#composite-gestures)ジェスチャ。 イマーシブ ヘッドセットとを対象にできますかヘッド視線の先を使用してポイント対応または[コント ローラーのモーション](motion-controllers.md)します。

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>機能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> Head 視線入力</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr><tr>
<td> 目の視線入力</td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>

> [!NOTE]
> HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。


## <a name="uses-of-gaze"></a>視線の先の使用

開発者は、複合現実で行えること多くヘッドまたは目視線の先。
* アプリには、ユーザーの注意の場所を確認すると、シーン内ホログラム視線の先が交差することができます。
* ジェスチャとコント ローラーの押下の選択、アクティブ化、取得、スクロールして、またはそれ以外の場合、ホログラムとの対話をユーザーに知らせて、ユーザーの視線入力に基づいて、アプリの対象に。
* アプリでは、空間マッピング メッシュでその注視射線が交差するで現実世界のサーフェスにホログラムを配置するユーザーをさせることができます。
* アプリは、ユーザーが場合を知ることが*いない*、そのオブジェクトに有効にするビジュアルおよびオーディオの手掛かりを提供するアプリにつながることが重要なオブジェクトの方向に検索します。

## <a name="cursor"></a>カーソル

ヘッド視線の先、ほとんどのアプリを使用する必要があります、[カーソル](cursors.md)(またはその他の聴覚的/visual indication) と対話しようとしている内容でユーザーの信頼を付与します。 通常、そのヘッド注視レイ ホログラムまたは実際の画面がある、オブジェクトが交差する最初の世界では、このカーソルを置きます。

![視線の先を表示する例を visual カーソル](images/cursor.jpg)<br>
*視線の先を表示する例を visual カーソル*

目の視線の一般的な推奨*いない*をシステムとユーザーの面倒をすぐにこのことができます、カーソルを表示します。 代わりに微妙ビジュアル ターゲットを強調表示またはが対話するユーザーの信頼性を提供する非常に薄い目のカーソルを使用します。 詳細についてを参照してください、[目に基づく入力の設計ガイダンス](eye-tracking.md)HoloLens 2 にします。

## <a name="giving-action-to-the-users-gaze"></a>ユーザーの視線の先へアクションの提供

ホログラムまたは、視線の先を使用して実際のオブジェクトの対象に、ユーザーが後、次の手順が、そのオブジェクトに対してアクションを実行します。 ユーザーがアクションを実行するための主な方法は[ジェスチャ](gestures.md)、[コント ローラーのモーション](motion-controllers.md)と[音声](voice-input.md)します。

## <a name="see-also"></a>関連項目
* [MR 入力 210:Head 視線入力](holograms-210.md)
* [DirectX でのヘッド視線入力とアイ視線入力](gaze-in-directx.md)
* [Unity で Head 視線入力](gaze-in-unity.md)
* [HoloLens 2 の視線](eye-tracking.md)
* [Mixed Reality Toolkit を使用して Unity で目視線入力](https://aka.ms/mrtk-eyes)
