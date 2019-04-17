---
title: 導入事例 - 安定化平面を使用して holographic 乱気流を削減するには
description: 安定化平面を使用して holographic 乱気流を削減するには
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、安定化、ケース スタディ
ms.openlocfilehash: a084ede5f9bf3d5f058cc81ec75840e2c2e75af2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597531"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>導入事例 - 安定化平面を使用して holographic 乱気流を削減するには

ホログラムで作業は、厄介なことがあります。 領域内を移動およびすべてのさまざまな角度から、ホログラムを参照してください。 できることのファクトは、通常のコンピューター画面では実現できない immersion のレベルを提供します。 インプレースこれらホログラムを維持する方法と、現実的な検索は、Microsoft HoloLens のハードウェアと holographic アプリのインテリジェントなデザインの両方によって実現技術偉業です。

## <a name="the-tech"></a>技術者

ホログラムを実際には、領域を共有している場合と同様に表示するために、する必要がありますが正しくレンダリング、色の分離なし。 これは、一部をホログラムいわゆるに固定の保持、HoloLens のハードウェアに組み込まれているテクノロジによって、[安定化平面](hologram-stability.md#stabilization-plane)します。

ポイントして、通常の平面が定義されているが、常にたいので、カメラに直面する平面、私たちは平面のポイントの設定を実際には考慮します。 ポイントすべて固定を維持するには、その処理を集中している HoloLens を指示し、安定したこのフォーカス ポイントを設定する方法アプリに固有しできますしたりすることはコンテンツに応じて、アプリを中断します。

ホログラムのときに最適に動作簡単に言うと、安定化平面が正しく適用されていますが、作成中のアプリケーションの種類に手段が実際に依存するどのような。 この問題に取り組む HoloLens で現在使用できるアプリのいくつかの方法を見てをみましょう。

## <a name="behind-the-scenes"></a>しくみ

次のアプリを開発する場合、平面を使用していないときにオブジェクトが sway 頭の移動し、クイック ヘッドまたはホログラム動きによる色の分離がわかりますが検出されました。 開発期間の過程で、わかった試行錯誤を安定化プレーンを活用する方法に関する問題を修正できないことを会社のアプリを設計する方法。

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy エクスプ ローラー:静止したコンテンツ、3 D の対話機能

[Galaxy エクスプ ローラー](galaxy-explorer.md)シーン内の 2 つの主要な要素を持ちます。宇宙のコンテンツと、視線の先に続く小さな UI ツールバーのメイン ビュー。 安定化のロジックと、現在の視線入力ベクトルと交差する指定された競合レイヤー上のすべてにヒットしたかどうかを判断するには、各フレームでに注目します。 この場合は、関心のレイヤーは、惑星、安定化の平面がありますに配置して、視線の先が、地球上にある場合。 ターゲットの衝突レイヤー内のオブジェクトの [なし] に達すると、アプリは、セカンダリ「プラン B」レイヤーを使用します。 何も問題で gazed されているが場合のコンテンツを gazing 時と同じ距離にある安定化平面は保持されます。 UI ツールはそのまま平面のターゲットとしての近くの間でのジャンプを検出し、はるかに全体的なシーンの安定性を削減します。

Galaxy エクスプ ローラーの設計安定に保つことと、色の分離の影響を軽減するのにも役立ちます。 歩き回りとコンテンツを軌道ではなく、並列沿いに移動する、ユーザーが推奨され、惑星の色の分離が顕著ではないことできるほどゆっくり移動されます。 さらに、色の分離の発生を防止するうえで長いようになるが、定数 60 FPS が維持されます。

自分でこれをチェックする LSRPlaneModifier.cs という名前のファイルの検索、 [Galaxy エクスプ ローラーの GitHub のコード](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities)します。

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio:UI フォーカスのあるコンテンツが静止しています。

HoloStudio では、同じモデルを見てでの作業時間の大半を費やします。 新しいツールを選択するか、単純な平面設定ロジックを保持しますできますので、UI を移動するときに、視線の先以外の膨大な量を移動しません。 UI を見たときに、平面は、視線の先をスナップにどのような UI 要素に設定されます。 モデルを調べる場合と、モデルの既定の距離に対応する、設定された距離は、平面。

![安定化平面の視覚化にホーム ボタンのユーザーとして HoloStudio gazes](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour と 3D のビューアー:アニメーションとムービーに関するコンテンツが静止しています。

HoloTour と 3D のビューアーでの表示されている単独のアニメーション化されたオブジェクトや映画の 3D 効果の上に追加します。 これらのアプリの安定化は、どの表示している現在に設定されます。

HoloTour 防ぐことも固定の場所ではなくを移動することにより、仮想の世界から離れすぎて straying します。 これにより、十分な安定性の問題が生じる可能性の他のホログラムからの取得されません。

![HoloTour からこの例では、安定化平面はハドリアヌスの Pantheon のこのムービーに設定されます。](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid:動的なコンテンツおよび環境的な対話

RoboRaid で安定化平面を設定することは、最も突然の動きを必要とするアプリであるにもかかわらず、驚くほど簡単です。 平面がについて言えば、壁に特化したまたは周囲オブジェクトしそれらから十分に離れているときにする前に一定の距離に配置されます。

RoboRaid 安定化面を考慮して設計されました。 Head ロックであるため、ほとんどの移動、十字線は、赤と青の色の最先端を最小限に抑えますのみを使用してこれを回避できます。 ちょっとした深さは、既に予期される視差効果をマスクすることで発生するすべての色裁ち落としを最小限に抑え、各部分の間も含まれています。 ロボットは非常に高速に移動して、一定の間隔で短い距離を移動するだけしないでください。 既定では、安定化が設定されている、前に約 2 m 離れたを維持する傾向があります。

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>フラグメントと若い Conker:環境とのやり取りを動的なコンテンツ

Asobo Studio によって書き込まれるC++、フラグメントと Young Conker は、別のアプローチが安定化平面を設定します。 関心 (地点 POI) のポイントは、コードで定義されているし、優先度の観点から順序付けします。 Poi は Young Conker、メニューの狙いを定める目盛り、およびロゴに Conker モデルなど、ゲーム内のコンテンツです。 ユーザーの視線入力と交差、Poi され、平面は最高の優先順位を持つオブジェクトの中心に設定されます。 積集合が発生しない場合は、平面が既定の間隔に設定されます。

フラグメントと Young Conker、プレイ領域として以前スキャンされて、内容の外部に移動する場合、アプリを一時停止して、ホログラムから離れすぎて straying 周囲設計もできます。 そのため、するは、最も安定したエクスペリエンスを提供する境界内で維持します。

## <a name="do-it-yourself"></a>自分で行う

HoloLens あり説明した概念をいろいろしたい場合は、テスト シーンをダウンロードし、次の演習を試します。 Unity の組み込みの商品 API を使用して、面が設定されているを視覚化することは必要があります。 このコードは、このケース スタディのスクリーン ショットをキャプチャするでも使用されていました。
1. 最新バージョンの同期[MixedRealityToolkit Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)します。
2. 開く、 [HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity)シーンです。
3. 構築し、生成されたプロジェクトを構成します。
4. デバイスで実行します。

### <a name="exercise-1"></a>手順 1

異なる向きで周囲のいくつか白いドットが表示されます。 前に、別の深さで 3 つのドットが表示されます。 ドット (.)、平面を変更するエア タップに設定されます。 この演習では、および他の 2 つは、ドットで gazing 中に、スペースを移動します。 上下に、ヘッドの左、右を有効にします。 点から近くに配置し、父親を移動します。 安定化の平面が別のターゲットに設定されている場合の対処方法を参照してください。

### <a name="exercise-2"></a>手順 2

次に、水平方向のパスと垂直方向のパスに 1 つで不安定な 1 つ、2 つの移動ドットが表示されるまでは直接に有効にします。 繰り返しますが、エア タップ平面に設定されているどのドットを変更します。 色の分離を軽減する方法に注意してくださいでは、面に接続されているドットが表示されます。 平面設定関数のドットの速度を使用するには、もう一度タップします。 このパラメーターは、目的のオブジェクトの動きについて、HoloLens にヒントを示します。 重要なことは 1 つのドットで velocity を使用するときにわかる、これを使用する場合については、他の移動のドットが色分離を表示します。 このアプリを設計する際に注意してください注意: 成果物が表示されないようにヘルプ、オブジェクトの動きをまとまりのあるフローがあることができます。

### <a name="exercise-3"></a>手順 3

ドットの新しい構成が表示されるまで 1 回以上、右側にします。 ここでは、距離にあるドットと 1 つのドットを前に、サインアウト迫ったりです。 エア タップして、プレーンは背面にドットとドットは、モーションが交互に設定するドットを変更します。 成果物のすべての場所を表示でどのように行うプロペラ ドットの面の位置と速度の設定に注意してください。

**ヒント**
* 平面設定ロジックはシンプルにします。 で説明したように魅力的なエクスペリエンスを複素平面の設定のアルゴリズムは不要です。 安定化平面は、パズルのピースを 1 つだけです。
* すべての可能なときに常に平面を移動ターゲット間で円滑にします。 瞬時に離れた場所にあるターゲットの切り替えとシーンを視覚的に中断されることができます。
* 非常に特定のターゲットにロックする平面設定ロジックでのオプションのことを検討します。 そのように、必要な場合は、ロゴまたはタイトルの画面などのオブジェクトでロックされているプレーンことができます。

## <a name="about-the-author"></a>執筆者紹介

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>ソフトウェア エンジニア @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>関連項目
* [MR 基礎 100:Unity の概要](holograms-100.md)
* [Unity でのフォーカス ポイント](focus-point-in-unity.md)
* [ホログラム安定性](hologram-stability.md)
