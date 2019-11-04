---
title: システムジェスチャ
description: '[スタート] メニューを呼び出すシステムジェスチャ。'
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 混合現実、ジェスチャ、相互作用、設計
ms.openlocfilehash: b46f642babb18387da2e76d5bdbb7631577c85de
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439823"
---
# <a name="system-gesture"></a>システムジェスチャ

システムジェスチャは、[スタート] メニューを呼び出すために使用するハンドジェスチャです。 これは、キーボードの Windows キー、Xbox コントローラーの Xbox ボタン、またはイマーシブヘッドセットモーションコントローラーの Windows ボタンを押すことに相当します。 相互作用を設計するときの競合を防ぐため、各 Mixed Reality デバイスでシステム用に予約されているジェスチャを理解することが重要です。

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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>ブルーム</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>手首ボタン</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>視線とパームアップのピンチ</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>ブルーム
HoloLens (第1世代) の [スタート] メニューを表示するには、"ブルーム" を設計しました。これは、花開花を模倣したシンボリックジェスチャです。 これは、簡単に操作できるようにするためのものであり、簡単に実行でき、簡単に再現できます。 HoloLens (第1世代) でブルームジェスチャを実行するには、手を手に入れてすぐに手に入れ、指を押しながら手を開けます。

:::row:::
    :::column:::
        ![ブルーム close](images/bloom-close.png)<br>
        **手順 1: すぐに使用することができます。**<br>
    :::column-end:::
    :::column:::
        ![ブルーム open](images/bloom-open.png)<br>
        **手順 2: すぐに使える spreaded**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a>手首ボタン
HoloLens 2 では、ブルームジェスチャを仮想手首ボタンに置き換えました。これにより、追加の教育を必要としない instinctual の対話が可能になります。 手首にユーザーを表示することにより、ユーザーは直感的に接続して、もう一方の手で押すことができます。

:::row:::
    :::column:::
        ![手首ボタンの準備完了](images/wrist-button-ready.png)<br>
        **手順 1: パームアップ: 手首ボタンを表示する**<br>
    :::column-end:::
    :::column:::
        ![手首ボタンを押し](images/wrist-button-press.png)<br>
        **手順 2: 手首ボタンを押す**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a>視線とパームアップのピンチ
また、HoloLens 2 でのアクセスを容易にするための1つのソリューションを設計しました。 このジェスチャを使用するには、ユーザーが手首ボタンをクリックし、同じ手で親指とインデックスの指を使用して、パームアップピンチを実行する必要があります。<br>
:::row:::
    :::column:::
        ![手首ボタンの準備完了](images/wrist-button-ready.png)<br>
        **手順 1: パームアップ: 手首ボタンを表示する**<br>
    :::column-end:::
    :::column:::
        ![手首ボタンのピンチ](images/wrist-button-pinch.png)<br>
        **手順: ボタンをクリックしてからピンチする**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>関連項目

* [本能的な操作](interaction-fundamentals.md)
* [アイ視線入力](eye-tracking.md)
* [音声入力](voice-input.md)
