---
title: 対話型オブジェクト
description: ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。 3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality、コントロール、対話、ui、ux
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415298"
---
# <a name="interactable-object"></a>対話型オブジェクト

ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。 3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。 イベントをトリガーする**対話型オブジェクト**を指定できます。 対話型オブジェクトは、テーブル上のコーヒーカップの任意のものとして、無線でバルーンに表示できます。 ダイアログ UI などの特定の状況では、従来のボタンを引き続き使用します。 ボタンのビジュアル表現は、コンテキストによって異なります。

![Interactible オブジェクト](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>対話型オブジェクトの重要なプロパティ

### <a name="visual-cue"></a>ビジュアルキュー

視覚的な手掛かりとは、光の形で見てきた sensory キューであり、視覚認識中にビジュアルシステムによって処理されます。 ビジュアルシステムは多くの人、特に人間にとって最も重要であるため、視覚的な手掛かりは、世界の知覚に関する情報源です。

Mixed reality では、holographic オブジェクトは実際の環境と混合されているため、どのオブジェクトが対話型されているかを理解するのは困難な場合があります。 対話型オブジェクトについては、各入力状態の視覚的な手掛かりを区別することが重要です。 これにより、ユーザーは、エクスペリエンスのどの部分が対話型されているかを理解し、一貫性のある対話方式をユーザーに確認することができます。

#### <a name="far-interactions"></a>遠くのやり取り

ユーザーが、宝石、ハンドレイ、およびモーションコントローラーの射線と対話できるオブジェクトについては、次の3つの入力状態に対して異なる視覚的な合図を使用することをお勧めします。
* **既定 (監視)** :オブジェクトの既定のアイドル状態。
* **対象 (ホバー)** :オブジェクトが、見つめカーソル、指近接、またはモーションコントローラーのポインターの対象になっている場合。
* **押さ**れました:オブジェクトがエアタップジェスチャで押されている場合、指を押すか、モーションコントローラーの [選択] ボタンをクリックします。

強調表示や拡大/縮小などの手法を使用して、ユーザーの入力状態を視覚的に示すことができます。 Windows Mixed Reality では、[スタート] メニューと [アプリバー] ボタンでさまざまな入力状態を視覚化する例を見つけることができます。 

![監視状態、対象状態、および押された状態を視覚化する例](images/640px-interactibleobject-states.png)<br>
*監視状態、対象状態、および押された状態を視覚化する例*

![Holographic ボタンでの監視状態、対象状態、および押された状態](images/MRTK_InteractableState.png)<br>
*Holographic ボタンでの監視状態、対象状態、および押された状態*

#### <a name="neardirect-interactions"></a>Near (ダイレクト) 相互作用

HoloLens 2 では、オブジェクトを操作できるようにするための入力追跡入力がサポートされています。 Haptic のフィードバックや完璧な知識を持っていない場合、オブジェクトから手の外に出てくることや、タッチしているかどうかを判断するのは困難な場合があります。 オブジェクトの状態と、特に、ホログラムとの関係を伝えるために十分な視覚的な手掛かりを提供することが重要です。

視覚的フィードバックを使用して、次のことを伝えます。
* **既定 (監視)** :オブジェクトの既定のアイドル状態。
* **ホバー**:手がホログラムの近くにある場合は、ビジュアルを変更して、その手がホログラムをターゲットにしていることを伝えます。 
* **距離と操作ポイント**: 手の形でのホログラムによる取り組みとして、投影された対話ポイントと、オブジェクトから指がどの程度離れているかを伝えるフィードバックをデザインします。
* **連絡先の開始**:視覚エフェクトが発生したことを通知するようにビジュアル (明るい色) を変更する
* **Grasped**:オブジェクトが grasped されたときのビジュアル (明るい色) を変更します。
* **連絡先の終了**:タッチが終了したときにビジュアル (明るい、色) を変更します。

![近くの対話状態を視覚化する例](images/640px-interactibleobject-states-near.jpg)<br>
*近くの対話状態を視覚化する例*

[HoloLens 2 のボタン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)は、さまざまな入力相互作用状態を視覚化する例を示しています。

![HoloLens 2 の pressable ボタンの例](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*HoloLens 2 の pressable ボタンの例*

HoloLens 2 では、追加の視覚的な手掛かりがあるので、ユーザーの信頼度が高くなります。 指先がオブジェクトに近づいたときに、指先のリングが表示され、スケールダウンされます。 リングは、最終的には、押された状態のドットに収束します。 このビジュアル affordance は、ユーザーがオブジェクトからの距離を理解するのに役立ちます。

![指先リングの視覚化](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*HoloLens 2 での指先 ring の視覚化*

![手書きの視覚的フィードバック](images/HoloLens2_Proximity.gif)<br>
*近接境界ボックスに基づくビジュアルフィードバックの例*


### <a name="audio-cue"></a>オーディオキュー
直接の対話では、適切なオーディオフィードバックによってユーザーエクスペリエンスが大幅に向上します。 オーディオフィードバックを使用して、次のことを伝えます。
* **連絡先の開始**:タッチの開始時にサウンドを再生する
* **連絡先の終了**:タッチエンドでサウンドを再生する
* **グラブ開始**:グラブの開始時にサウンドを再生する
* **グラブの終了**:グラブ終了時にサウンドを再生する

### <a name="voice-command"></a>音声コマンド
対話型オブジェクトについては、代替の対話オプションをサポートすることが重要です。 既定では、対話型されているすべてのオブジェクトに対して音声コマンドをサポートすることをお勧めします。 検索性を向上させるために、ホバー状態のヒントを提供できます。

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="音声コマンドのツールヒント" width="350"><br/>*音声コマンドのツールヒント*

## <a name="sizing"></a>サイズ変更
すべての対話型オブジェクトをユーザーが簡単に操作できるようにするには、ユーザーからの距離に基づいて、対話型が最小サイズ (視覚的な弧の角度で測定されることが多い) を満たしていることを確認することをお勧めします。 視覚的な角度は、ユーザーの視点とオブジェクトの間の距離に基づいており、一定のままになります。一方、ターゲットの物理的なサイズは、ユーザーからの距離が変化すると変化する可能性があります。 ユーザーからの距離に基づいてオブジェクトの必要な物理サイズを判断するには、[この](http://elvers.us/perception/visualAngle/)ような視覚的な角度計算ツールを使用します。

対話型コンテンツの最小サイズに関する推奨事項を以下に示します。

### <a name="target-size-for-direct-hand-interaction"></a>ダイレクトハンド操作のターゲットサイズ
| 単位 | 表示角度 | サイズ |
|---------|---------|---------|
| 45cm  | 2°未満 | 1.6 x 1.6 cm |

![ダイレクトハンド操作のターゲットサイズ](images/TargetSizingNear.jpg)<br>
*ダイレクトハンド操作のターゲットサイズ*

直接対話するためのボタンを作成する場合は、3.2 x 3.2 cm の最小サイズを大きくすることをお勧めします。これにより、アイコンと、場合によってはテキスト * * を格納するのに十分な領域が確保されます。

| 単位 | 最小サイズ |
|---------|---------|
| 45cm  | 3.2 x 3.2 cm |

![ボタンのターゲットサイズ](images/TargetSizingButtons.png)<br>
*ボタンのターゲットサイズ*


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>ハンドレイまたは宝石の相互作用の目標サイズ
| 単位 | 表示角度 | サイズ |
|---------|---------|---------|
| 2分  | 1°未満 | 3.5 x 3.5 cm |

![ハンドレイまたは宝石の相互作用の目標サイズ](images/TargetSizingFar.jpg)<br>
*ハンドレイまたは宝石の相互作用の目標サイズ*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit (MRTK) を使用した対話型オブジェクトの作成

**[混合 Reality ツールキット](https://github.com/Microsoft/MixedRealityToolkit-Unity)** では、対話型オブジェクトの作成に役立つ一連の Unity スクリプトと prefabs を見つけることができます。 これらを使用すると、さまざまな種類の入力相互作用状態にオブジェクトを応答させることができます。

* [対話型](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [ハンド操作の例シーン](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

MixedRealityToolkit の標準シェーダーには、ビジュアルおよびオーディオキューを作成するのに役立つ**近接光**などのさまざまなオプションが用意されています。
* [MRTK 標準シェーダー](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a>関連項目

* [境界ボックス](app-bar-and-bounding-box.md)
* [オブジェクト コレクション](object-collection.md)
* [Billboard と Tag-along](billboarding-and-tag-along.md)