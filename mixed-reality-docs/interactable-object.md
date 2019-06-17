---
title: 対話型のオブジェクト
description: ボタンには、2 D 抽象世界でイベントをトリガーに使用されるメタファが長年です。 3 次元の複合現実の世界では、この抽象化はもはやの世界に限定しました必要はありません。
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality、コントロール、相互作用、ui、ux
ms.openlocfilehash: b0397e00763f70e4caf55a84b6541085e56fafd4
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148733"
---
# <a name="interactable-object"></a>対話型のオブジェクト

ボタンには、2 D 抽象世界でイベントをトリガーに使用されるメタファが長年です。 3 次元の複合現実の世界では、この抽象化はもはやの世界に限定しました必要はありません。 何もすることができます、**対話型のオブジェクト**イベントをトリガーします。 対話型のオブジェクトは、そのテーブルに、コーヒー カップから空中に浮かんでバルーンをものとして表現できます。 引き続き行うことで特定の状況はダイアログの UI などの従来のボタンを使用します。 ボタンの視覚的表現は、コンテキストによって異なります。

![Interactible オブジェクト](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>対話型のオブジェクトの重要なプロパティ

### <a name="visual-cue"></a>視覚的な合図

視覚的な手掛かりは、ライトの形式で目によって受信され、視覚認識の中に visual システムによって処理される感覚的な手掛かりです。 Species 多く、特にの人間では、ビジュアルのシステムから視覚的な手掛かりは、世界を認識する方法の情報の大規模な源です。

複合現実で holographic オブジェクトは、実際の環境とが混在しているため困難になることな対話型のオブジェクトを理解します。 お客様のエクスペリエンスで対話型のオブジェクトの状態を各入力に差別化された視覚的な合図を提供する重要なは。 これにより、ユーザーのエクスペリエンスの部分が対話型と一貫性のある相互作用方式で確実に、ユーザーは、理解できます。

#### <a name="far-interactions"></a>ここまでの相互作用

任意のオブジェクトにそのユーザーおよび操作できます視線の先、手の形のレイ モーション コント ローラーのレイをお勧めこれら 3 つの入力の状態の別の視覚的に。
* **既定 (監視)** :オブジェクトの既定のアイドル状態です。
* **対象となる (ホバー)** :オブジェクトは視線の先のカーソルにターゲットになると、本の指近接やアニメーション コント ローラーのポインター。
* **押された**:オブジェクトをエア タップ ジェスチャや指キーを押してモーション コント ローラーの [選択] ボタンを押したときにします。

強調表示機能やスケーリングなどの手法を使用すると、ユーザーの入力の状態を視覚的な合図を提供します。 Windows Mixed Reality では、[スタート] メニューおよびアプリ バー ボタンのさまざまな入力の状態を視覚化の例が見つかります。 

![監視状態を視覚化するための例は、状態、対象とし、状態の押されました。](images/640px-interactibleobject-states.png)<br>
*監視状態を視覚化するための例は、状態、対象とし、状態の押されました。*

![監視の状態、状態、対象となるおよび holographic ボタンの状態を押した](images/MRTK_InteractableState.png)<br>
*監視の状態、状態、対象となるおよび holographic ボタンの状態を押した*

#### <a name="neardirect-interactions"></a>Near(direct) 相互作用

HoloLens 2 には、追跡オブジェクトと対話できる入力関節手がサポートされています。 Haptic フィードバックや完璧な深さ perception もなしはオブジェクトからの手がどれほど離れてか接触するかどうかを判断することができます。 特に手ホログラムに関連するのと、オブジェクトの状態を通信するために十分な視覚的手掛かりを提供する重要です。

次の通信に視覚的なフィードバックを使用します。
* **既定 (監視)** :オブジェクトの既定のアイドル状態です。
* **マウス ポインターを移動**:手の形の場合は、ほぼホログラム、手札を通信するためにビジュアルを変更すると、ホログラムが対象とします。 
* **相互作用のポイントとの距離**: 手が近づくホログラム、指は、オブジェクトから遠く離れた方法と、操作の射影されたポイントの通信にフィードバックをデザインします。
* **Begin にお問い合わせください**:そのタッチを通信するためのビジュアルの変更 (色、光) が発生しました
* **文章**:変更 (色、光) のビジュアル オブジェクトを見せるとき。
* **最後にお問い合わせください**:変更 (色、光) ビジュアル タッチが終了したとき。

![操作の状態の近くの視覚化の例](images/640px-interactibleobject-states-near.jpg)<br>
*操作の状態の近くの視覚化の例*

[HoloLens 2 ボタン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)さまざまな入力の対話操作の状態を視覚化の例を示します。

![HoloLens 2 pressable ボタンの例](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*HoloLens 2 pressable ボタンの例*

HoloLens の 2 を深さ perception でユーザーの信頼度を向上させるその他の視覚的があります。 指のリングでは、表示し、指がオブジェクトに近づくようにスケール ダウンします。 リングは、キーを押して状態でドットに最終的に収束します。 この visual アフォー ダンスでは、ユーザーがオブジェクトからの距離を理解するのに役立ちます。

![指先リングの視覚化](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*HoloLens 2 では、指先リングの視覚エフェクト*

![近接の手の形で視覚的なフィードバック](images/HoloLens2_Proximity.gif)<br>
*境界ボックスの近接度に基づいて視覚的なフィードバックの例*


### <a name="audio-cue"></a>オーディオ キュー
直接手の相互作用の適切なオーディオをフィードバックはユーザー エクスペリエンスを大幅に向上することができます。 次の通信にオーディオをフィードバックを使用します。
* **連絡先の開始**:タッチの開始時にサウンドを再生します。
* **連絡先の終了**:タッチ エンドでサウンドを再生します。
* **グラブ開始**:グラブの開始時にサウンドを再生します。
* **最後に取得**:グラブ エンドでサウンドを再生します。

### <a name="voice-command"></a>音声コマンド
対話型のオブジェクトが別の相互作用オプションをサポートするために重要です。 既定では、対話型である任意のオブジェクトの音声コマンドをサポートすることをお勧めします。 探索可能性を向上させるのには、ホバー状態のツールヒントを行うことができます。

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="音声コマンドのツールヒント" width="350"><br/>*音声コマンドのツールヒント*

## <a name="sizing"></a>サイズ変更
対話型のすべてのオブジェクトの有効期限は簡単にすることを確認するにはユーザーによって影響を受けるをお勧め、最小サイズ (多くの場合、ビジュアルの角度を度数で測定)、ユーザーからファイルを配置する距離に基づく対話型を満たしていることを確認します。 ビジュアルの角度を度では、ユーザーと、オブジェクト間の距離に基づいておりは一定のまま、ターゲットの物理サイズがユーザーの変更からの距離として変更可能性があります。 確認してくださいと程度からの距離に基づくオブジェクトのために必要な物理サイズを決定するには、は、visual 角度は、電卓を使用して試してください。 http://elvers.us/perception/visualAngle/

対話型コンテンツの最小サイズの推奨事項を以下に示します

### <a name="target-size-for-direct-hand-interaction"></a>直接手の相互作用の目標サイズ
| 距離 | 表示角度 | サイズ |
|---------|---------|---------|
| 45 cm  | 2 度以上 | 1.6 × 1.6 cm |

![直接手の相互作用の目標サイズ](images/TargetSizingNear.jpg)<br>
*直接手の相互作用の目標サイズ*

確認して 3.2 x 3.2 cm の大規模な最小サイズは、アイコンを格納するための十分な領域、可能性のあるいくつかテキスト * * をお勧めの直接の対話のボタンを作成する場合

| 距離 | 最小サイズ |
|---------|---------|
| 45 cm  | 3.2 x 3.2 cm |

![ターゲット サイズのボタン](images/TargetSizingButtons.png)<br>
*ターゲット サイズのボタン*


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>ターゲット光線の手の形のサイズまたは相互作用の視線
| 距離 | 表示角度 | サイズ |
|---------|---------|---------|
| 2 分  | 1 度以上 | 3.5 x 3.5 cm |

![ターゲット光線の手の形のサイズまたは相互作用の視線](images/TargetSizingFar.jpg)<br>
*ターゲット光線の手の形のサイズまたは相互作用の視線*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit (MRTK) との対話型のオブジェクトを作成します。

**[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 対話型のオブジェクトを作成する際に役立つプレハブ、一連の Unity のスクリプトを見つけることができます。 これらは、オブジェクトのさまざまな種類の入力の対話操作の状態に応答を使用することができます。

* [対話型](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [ボタン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [手の形の相互作用の例のシーン](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

MixedRealityToolkit の標準的なシェーダーがなどのさまざまなオプションを提供します**近接 light**を視覚的およびオーディオを作成できます。
* [MRTK 標準シェーダー](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a>関連項目

* [境界ボックス](app-bar-and-bounding-box.md)
* [オブジェクト コレクション](object-collection.md)
* [Billboard と Tag-along](billboarding-and-tag-along.md)