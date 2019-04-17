---
title: 対話型のオブジェクト
description: ボタンには、2 D 抽象世界でイベントをトリガーに使用されるメタファが長年です。 3 次元の複合現実の世界では、この抽象化はもはやの世界に限定しました必要はありません。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality、コントロール、相互作用、ui、ux
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601181"
---
# <a name="interactable-object"></a>対話型のオブジェクト

ボタンには、2 D 抽象世界でイベントをトリガーに使用されるメタファが長年です。 3 次元の複合現実の世界では、この抽象化はもはやの世界に限定しました必要はありません。 何もすることができます、**対話型のオブジェクト**イベントをトリガーします。 対話型のオブジェクトは、そのテーブルに、コーヒー カップから空中に浮かんでバルーンをものとして表現できます。 引き続き行うことで特定の状況はダイアログの UI などの従来のボタンを使用します。 ボタンの視覚的表現は、コンテキストによって異なります。

![Interactible オブジェクト ヒーローのイメージ](images/640px-interactibleobject-hero-640px.jpg)


 **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 一連の Unity のスクリプトを作成したとする際に役立つプレハブは、対話型のオブジェクトを作成します。 これらを使用して、これらの標準的な対話状態を使用すると、対話できるユーザー オブジェクトの任意の型を作成することができます: 監視、対象となる状態および押されています。 独自の資産とビジュアル デザインを簡単にカスタマイズすることができます。 詳細なアニメーションを作成して、Unity のアニメーション コント ローラーでの操作状態の対応するアニメーション クリップの割り当てまたはオフセットとスケールを使用していずれかによってカスタマイズできます。 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a>さまざまな入力の対話操作の状態の視覚的なフィードバック

複合現実で holographic オブジェクトは、実際の環境とが混在しているため困難になることな対話型のオブジェクトを理解します。 お客様のエクスペリエンスで対話型のオブジェクトの状態を各入力に差別化された視覚的なフィードバックを提供する重要なは。 これにより、ユーザーのエクスペリエンスの部分が対話型と一貫性のある相互作用方式で確実に、ユーザーは、理解できます。

任意のオブジェクトにそのユーザーが操作できるをお勧めするこれら 3 つの入力の状態のさまざまな視覚的なフィードバックがあります。
* **監視**:オブジェクトの既定のアイドル状態です。
* **対象となる**:オブジェクトは視線の先のカーソルにターゲットになると、本の指近接やアニメーション コント ローラーのポインター。
* **押された**:オブジェクトをエア タップ ジェスチャや指キーを押してモーション コント ローラーの [選択] ボタンを押したときにします。

![Holographic ボタン](images/640px-interactibleobject-holographicbutton-650px.jpg)<br>
*状態、状態、対象となるおよびれた押された状態の監視*

Windows Mixed Reality では、[スタート] メニューおよびアプリ バー ボタンのさまざまな入力の状態を視覚化の例が見つかります。 強調表示機能やスケーリングなどの手法を使用すると、ユーザーの入力の状態を視覚的なフィードバックを提供します。

HoloLens 2 で絶対手の形が、入力の追跡をサポートしているので提供できます、手の近接度に基づいて追加アフォー。 [HoloLens 2 ボタン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)この例を示します。

![Pressable ボタン](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a>対話型のオブジェクトのサンプル

### <a name="mesh-button"></a>メッシュのボタン

![メッシュのボタン](images/640px-interactibleobject-meshbutton.jpg)

これらは、対話型のオブジェクトとしてプリミティブとインポートされた 3 D メッシュの使用例です。 各入力の対話操作の状態に応答するさまざまな規模、オフセット、および色の値を簡単に割り当てることができます。

### <a name="toolbar"></a>ツール バー

![ツール バー](images/640px-interactibleobject-toolbar.jpg)

ツールバーは、複合現実エクスペリエンスで広く使用されているパターンです。 追加の動作とボタンの単純なコレクションなどが[Billboarding と tag-along](billboarding-and-tag-along.md)します。 この例、MixedRealityToolkit から Billboarding と tag-along スクリプトを使用します。 速度としきい値の値の移動距離を含む詳細な動作を制御できます。

### <a name="traditional-button"></a>従来のボタン

![従来のボタン](images/640px-interactibleobject-traditionalbutton.jpg)

この例では、従来の 2D スタイル ボタンを使用します。 各入力の状態には、若干異なる深さとアニメーションのプロパティがあります。

### <a name="other-examples"></a>その他の例

![プッシュ ボタン](images/640px-interactibleobject-pushbutton.jpg)<br>
*プッシュ ボタン*
<br>
![実際の有効期間オブジェクト](images/640px-interactibleobject-reallifeobject.jpg)<br>
*実際のオブジェクト*

HoloLens では、物理領域を利用できます。 物理的な壁に holographic プッシュ ボタンを想像してください。 または、実際のテーブルでは、コーヒー カップについてでしょうか。 ソフトウェアのモデリングからインポートした 3D モデルを使用して、実際のオブジェクトのような対話型のオブジェクトを作成できます。 デジタル オブジェクトであるために魔法のような相互作用を追加できます。

## <a name="interactable-object-in-mixed-reality-toolkit"></a>Mixed Reality Toolkit で対話型のオブジェクト
検索することができます、 [Interactable の例については、Mixed Reality toolkit オブジェクト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)


## <a name="see-also"></a>関連項目
* [Mixed Reality ツールキット - unity pressable ボタン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [オブジェクトのコレクション](object-collection.md)
* [ビルボード処理と tag-along](billboarding-and-tag-along.md)
