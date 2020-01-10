---
title: ハンドメニュー
description: メニューを使用すると、ユーザーは頻繁に使用される関数のための直接の UI をすぐに表示できます。 これらは、メニューのベストプラクティスと推奨事項です。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: ハンド、メニュー、ボタン、クイックアクセス、レイアウト
ms.openlocfilehash: c0e1800be69a15706e17f40b1601fc79d05e5d75
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723261"
---
# <a name="hand-menu"></a>ハンドメニュー

![Ulnar side location](images/UX/UX_Hero_HandMenu.jpg)

メニューを使用すると、ユーザーは頻繁に使用される関数のための直接の UI をすぐに表示できます。 

メニューについては、以下のベストプラクティスをご覧ください。 また、 [Mrtk](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)の手の形を示すシーンの例も見つかります。

<br>

---

## <a name="behavior-best-practices"></a>動作のベストプラクティス
**A. ボタンの数を小さく**します。ハンドロックされたメニューと目の間の距離が近づいているため、またはユーザーが比較的小さな視覚面に焦点を当てる傾向がある場合 (attentional コーンは約10度)、ボタンの数を小さくしておくことをお勧めします。 この探索に基づいて、3つのボタンがある1つの列は、ユーザーが視界の中央に移動した場合でも、ビューのフィールド (視界) 内のすべてのコンテンツを保持することで効果的に機能します。 

**B. 迅速な対処のために手のメニューを使用**します。 arm を持ち上げて位置を維持すると、arm の疲労が簡単になります。 短い対話を必要とするメニューには、ハンドロックされたメソッドを使用します。 メニューが複雑で、対話時間の延長が必要な場合は、代わりにワールドロックまたは本体ロックを使用することを検討してください。 

**C. ボタン/パネルアングル:** メニューは、両端が反対のショルダーと真ん中になるようにする必要があります。これにより、自然な移動は反対の手でメニューと対話し、ボタンをタッチするときに不快または不快な針を回避できます。 

**D. ワンきき操作またはハンズフリー操作のサポートを検討する:** 両方のユーザーが常に使用できるとは限りません。 一方または両方のハンズオンが使用できない場合は、さまざまなコンテキストを検討し、そのような状況に合わせて設計アカウントを確認します。 片手メニューをサポートするには、手動でロックしたときに、メニューの配置を手動でロックしてみてください。 ハンドフリーのシナリオでは、音声コマンドを使用して、メニューボタンを起動することを検討してください。

**E. 2 段階呼び出し:** ポップアップをイベントとして使用した場合は、不要になったときに誤って表示されることがあります (偽陽性)。これは、ユーザーが (通信とオブジェクトの操作のために) 意図的に (通信とオブジェクトの操作のために)、意図せずに手を移動するためです。 アプリで誤検知が発生した場合は、完全に開いた指などの手のメニューを呼び出すために、パームアップイベント以外に追加の手順を追加することを検討してください。

**F. 手首 (システムホームボタン) の近くにボタンを追加しないよう**にします。メニューボタンが [ホーム] ボタンの近くにある場合、メニューを操作しているときに誤ってトリガーされることがあります。

**G. テスト、テスト、テスト:** 人間は、快適で不快感のためにさまざまなしきい値を持つさまざまな本体を持っています。設計をでテストし、さまざまなユーザーからフィードバックを受け取るようにしてください。

<br>

---

## <a name="hand-menu-placement-best-practices"></a>手動によるメニューの配置のベストプラクティス

人間の構造では、ulnar は ulnar のボーンの近くで実行されます。 Ulna は、l 肘から最小の指まで伸縮する長い骨の中にあります。

次に、探索に基づく2つの推奨される配置を示します。


:::row:::
    :::column:::
        ![Ulnar side location](images/UlnarSideHandMenu.gif)<br>
        **Palm 内部の Ulnar**<br>
        この位置は、両手が互いに重ならないため、信頼性が高くなります。 これは、正確な手動検出と追跡に不可欠です。
    :::column-end:::
    :::column:::
        ![Ulnar side location](images/UlnarAboveHandMenu.gif)<br>
        **B. Ulnar (手動)**<br>
        この場所はユーザーにとって使いやすいものです。ユーザーは arm を起動して、手のメニューと対話する必要がないからです。 メニュー **13cm**をパームの上に配置し、ボタンを ulnar palm の内側に配置することをお勧めします。 [最適なボタンサイズの詳細を確認する](interactable-object.md)<br>
        <br>
        技術的な理由により、この場所は1つの必須の実装にすることをお勧めします。開発者は、ユーザーの反対側がこのメニューを操作するために終了した後で、メニューを固定する必要があります。 これにより、jitteriness が重複しないようにすることができ、ボタンをより高速にターゲット設定できるようになります。<br>
        <br>
        HoloLens 2 カメラは、互いに独立しているときに正確に識別します。 両手が重なると、メニューがアンカー位置から離れてしまう可能性があります。<br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a>推奨されないメニュー位置
さまざまなメニューのレイアウトや場所を使用したユーザーの調査を行っていますが、次のメニューの場所は推奨されて**いません**。以下の各研究の欠点を確認してください。


:::row:::
    :::column:::
        arm](images/AboveArm.gif) 上の ![<br>
        **Arm の上**<br>
        1-適切な追跡を維持することが困難<br>
        2-不自然な位置が原因でユーザーの疲労が発生する
    :::column-end:::
    :::column:::
        ![指](images/AboveFingers.gif)<br>
        **上の指**<br>
        長い時間を保持することによる1手の疲労<br>
        インデックスとミドルフィンガーでの2ハンドトラッキングの問題
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        中央の](images/handCenter.gif) の ![<br>
        **上-中央のパーム**<br>
        両手が重なっているために問題を追跡する<br>
        メニューと対話するためにハンドを長時間保持することによる2ハンドの疲労
    :::column-end:::
    :::column:::
        top**指先**の ![top 指先](images/TopFingerTip.gif)<br>
        1ハンドトラッキングの問題<br>
        標準の姿勢を超える2ハンドの疲労<br>
        3-指間のスペースが限られているために偶発的に他の指でボタンを押す問題
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        Arm](images/BackOfTheArm.gif) の ![戻します。<br>
        **Arm の背面**<br>
        1-事故によってホームボタンをトリガーできる<br>
        2-ユーザーに自然な、または使いやすい位置
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity の MRTK (Mixed Reality Toolkit) の手の形のメニュー
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、ハンドメニューのスクリプトとサンプルシーンが用意されています。 HandConstraintPalmUp ソルバースクリプトを使用すると、さまざまな構成可能なオプションを使用して、任意のオブジェクトを簡単にアタッチできます。

* [HandConstraintPalmUp を使用した MRTK ハンドメニュー](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)


<br>

---


## <a name="see-also"></a>「

* [カーソル](cursors.md)
* [ハンド レイ](point-and-commit.md)
* [ボタン](button.md)
* [対話可能なオブジェクト](interactable-object.md)
* [境界ボックスとアプリ バー](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [ハンド メニュー](hand-menu.md)
* [メニューの近く](near-menu.md)
* [オブジェクト コレクション](object-collection.md)
* [音声コマンド](voice-input.md)
* [キーボード](keyboard.md)
* [ヒント](tooltip.md)
* [スレート](slate.md)
* [スライダー](slider.md)
* [シェーダー](shader.md)
* [Billboard と Tag-along](billboarding-and-tag-along.md)
* [進行状況を表示する](progress.md)
* [表面吸着](surface-magnetism.md)
