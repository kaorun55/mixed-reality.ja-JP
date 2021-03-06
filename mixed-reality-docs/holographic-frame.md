---
title: ホログラフィック フレーム
description: ユーザーは、holographic フレームを通じて混合現実の世界を見ることができます。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/25/2020
ms.topic: article
keywords: HoloLens、Windows Mixed Reality、holographic frame、ビューのフィールド
ms.openlocfilehash: 0eae511d6dcbe5b379c8368d8878df6114d805aa
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441769"
---
# <a name="holographic-frame"></a>ホログラフィック フレーム

ユーザーは、ヘッドセットによって作成される四角形のビューポートを通して、Mixed Reality の世界を見ることになります。 HoloLens では、この四角形の領域はホログラフィック フレームと呼ばれ、ユーザーは自分の周囲の現実世界に重ねてデジタル コンテンツを見ることができます。 Holographic フレーム用に最適化されたエクスペリエンスを設計することで、機会を生み出し、課題を軽減し、混合現実アプリケーションのユーザーエクスペリエンスを向上させることができます。

## <a name="designing-for-content"></a>コンテンツのデザイン

多くの場合、デザイナーは、ユーザーがオブジェクト全体を見ることができるように、実際のスケールを犠牲にして、ユーザーがすぐに見ることができるように、エクスペリエンスの範囲を制限する必要があります。 同様に複雑なアプリケーションを含むデザイナーは、多くの場合、コンテンツを使用して holographic フレームをオーバーロードし、ユーザーが困難な相互作用と乱雑なインターフェイスを持つことができます。 複合現実のコンテンツを作成するデザイナーでは、ユーザーの前に直接表示し、すぐに表示することができます。 ユーザーの周りの物理的な世界がマップされている場合、これらのすべてのサーフェイスは、デジタルコンテンツと対話のためのキャンバスと見なされる必要があります。 操作とコンテンツを適切にデザインするには、ユーザーがスペースを移動し、重要なコンテンツに注目し、mixed reality の可能性を最大限に発揮できるようにすることをお勧めします。

アプリ内での移動と探索を促進する最も重要な手法は、**ユーザーがエクスペリエンスを調整できる**ようにすることです。 デバイスを使用して、ユーザーに短い期間の "タスクを無料で" 時間を与えます。 これは、空間にオブジェクトを配置し、ユーザーが画面内を移動したり、エクスペリエンスの概要をナレーションたりするのと同様に簡単です。 この時間は、重要なタスクや特定のジェスチャ (エアタップなど) ではなく、ユーザーがデバイスを介してコンテンツを表示できるようにすることを目的としています。 このユーザーが初めてデバイスを使用する場合は、holographic フレームやホログラムの性質を通じてコンテンツが見やすくなるため、これは特に重要です。

### <a name="large-objects"></a>大きなオブジェクト

多くの場合、経験のあるコンテンツ (特に実際のコンテンツ) は、holographic フレームよりも大きくなります。 通常、holographic フレーム内に収まりきらないオブジェクトは、最初に導入されたとき (小さいスケールまたは距離) に収まるように縮小する必要があります。 キーは、スケールがフレームを overwhelms する前に、**ユーザーがオブジェクトの完全なサイズを確認できる**ようにするためのものです。 たとえば、holographic ゾウは、フレーム内に完全に収まるように表示される必要があります。これにより、ユーザーは、ユーザーに近い[ワールドスケール](scale.md)にサイズを設定する前に、動物の全体的な形状を空間的に理解することができます。

オブジェクトの完全なサイズを念頭に置いて、ユーザーは、そのオブジェクトの特定の部分をどこに移動して探すかを想定しています。 同様に、イマーシブコンテンツを使用している場合は、そのコンテンツの完全なサイズを参照する方法があると便利です。 たとえば、仮想家のモデルを処理する経験がある場合は、ユーザーが社内のどこにいるかを理解するためにユーザーがトリガーできる人形のサイズの小さなバージョンのエクスペリエンスが必要になることがあります。

ラージオブジェクトの設計の例については、「 [Volvo 車](holographic-frame.md#volvo-cars)」を参照してください。

### <a name="many-objects"></a>多数のオブジェクト

多くのオブジェクトまたはコンポーネントを使用する経験では、ユーザーの前に holographic フレームが直接乱雑にならないように、ユーザーの周囲の全領域を使用することを検討してください。 一般に、エクスペリエンスにコンテンツを導入することをお勧めします。これは特に、多くのオブジェクトをユーザーに提供することを計画している経験に当てはまります。 大きなオブジェクトの場合と同様に、重要なのは、ユーザーがエクスペリエンスの**コンテンツのレイアウトを理解**できるようにすることです。これにより、エクスペリエンスにコンテンツが追加されたときの周囲を把握することができます。

これを実現するための1つの方法は、コンテンツを実際の世界に固定するエクスペリエンスで、永続的なポイント (ランドマークとも呼ばれます) を提供することです。 たとえば、ランドマークは、デジタルコンテンツが表示されているテーブルやデジタルオブジェクト (コンテンツが頻繁に表示されるデジタル画面のセットなど) など、実際の環境における物理的なオブジェクトである可能性があります。 また、オブジェクトを holographic フレームの周囲に配置して、ユーザーがキーの内容を確認できるようにすることもできます。一方、周囲を超えるコンテンツの検出は、[アテンションディレクター](holographic-frame.md#attention-directors)によって支援されます。

オブジェクトを周囲に配置することで、ユーザーに対して、ユーザーに確認を促すことができます。また、以下に説明するように、アテンションディレクターによって支援を受けることができます。 Holographic フレームの考慮事項の詳細については、「[快適](comfort.md#holographic-frame-considerations)さ」を参照してください。

<br>

---

## <a name="interaction-considerations"></a>相互作用に関する考慮事項

コンテンツと同様に、mixed reality エクスペリエンスにおける相互作用については、ユーザーがすぐに確認できるものに限定される必要はありません。 対話は、ユーザーの周りの実際の空間のどこででも実行できます。これらの相互作用は、ユーザーによるエクスペリエンスの移動と探索を促進するのに役立ちます。

### <a name="attention-directors"></a>アテンションディレクター

関心のあるポイントまたはキーの相互作用を示すことは、ユーザーの経験を通じてユーザーを進めるうえで重要な場合があります。 Holographic フレームのユーザーへの注意と移動は、微妙な方法または重い方法で行うことができます。 ユーザーが圧倒されるのを防ぐために、(特にエクスペリエンスの開始時に) 混在環境では、注目のディレクターを無料で探索する期間とのバランスを取るようにしてください。 一般に、次の2種類のアテンションディレクターがあります。
* **ビジュアルディレクター:** 特定の方向に移動する必要があることをユーザーに通知する最も簡単な方法は、視覚的な表示を提供することです。 これは、視覚的な効果 (たとえば、ユーザーがエクスペリエンスの次の部分に向かって視覚的に従うことができるパス) や、単純方向矢印として実行できます。 視覚インジケーターは、holographic フレームまたはカーソルに ' 添付 ' ではなく、ユーザーの環境内で接地される必要があることに注意してください。
* **オーディオディレクター:** [空間サウンド](spatial-sound-design.md)は、シーン内のオブジェクトを確立するための強力な方法を提供します (操作を開始するオブジェクトのユーザーに警告します)。または、領域内の特定の位置に注目する (ユーザーのビューをキーオブジェクトに移動する) ことができます。 オーディオディレクターを使用してユーザーの注目を導くことは、視覚ディレクターに比べて微妙で、手間がかからないことがあります。 場合によっては、オーディオディレクターから開始し、ユーザーがキューを認識していない場合はビジュアルディレクターに移動することをお勧めします。 また、オーディオダイレクタをビジュアルダイレクタとペアリングして強調することもできます。

### <a name="commanding-navigation-and-menus"></a>コマンド、ナビゲーション、およびメニュー

混合環境でのインターフェイスは、制御するデジタルコンテンツと緊密にペアリングされています。 そのため、多くの場合、フリーフローティングの2D メニューは対話には適していないため、holographic フレーム内でユーザーが快適に使用するのが困難になることがあります。 メニューやテキストフィールドなどのインターフェイス要素を必要とするエクスペリエンスについては、短い遅延後に holographic フレームの後に[タグに沿ったメソッド](billboarding-and-tag-along.md)を使用することを検討してください。 ヘッドアップディスプレイのようなフレームへのコンテンツのロックは避けてください。これは、ユーザーにとっては無効になり、シーン内の他のデジタルオブジェクトの immersion の意味を損なう可能性があるためです。

または、制御する特定のコンテンツにインターフェイス要素を直接配置することを検討してください。これにより、ユーザーの物理的な領域を自然に操作できます。 たとえば、複雑なメニューを分割します。 各ボタンまたはコントロールのグループが特定のオブジェクトにアタッチされ、相互作用が影響を及ぼします。 この概念をさらに活用するには、[対話型オブジェクト](interactable-object.md)の使用を検討してください。

### <a name="gaze-and-gaze-targeting"></a>ターゲットを見つめおよび宝石にする

Holographic フレームは、開発者が対話をトリガーし、ユーザーの注意事項を評価するツールを提供します。 [宝石](gaze-and-commit.md)は[HoloLens の主要な相互作用](interaction-fundamentals.md)の1つであり、宝石は[ジェスチャ](gaze-and-commit.md#composite-gestures)(エアタップを含む) や[音声](voice-input.md)にペアリングすることができます (より自然で自然な音声ベースの対話を可能にします)。 そのため、holographic フレームはデジタルコンテンツを監視するための領域と、それと対話するための領域の両方になります。 ユーザーのスペースに対して複数のオブジェクトとの対話を行う経験がある場合 (たとえば、ユーザーのスペースを見つめながらジェスチャで多重選択する場合など) は、それらのオブジェクトをユーザーの表示にするか、必要なヘッドの移動量を制限して、[ユーザーの快適](comfort.md)さを促進することを検討してください。

また、ユーザーの操作を追跡し、ユーザーが最も注意を払っているオブジェクトまたはシーンの部分を確認するためにも使用できます。 これは、特にエクスペリエンスのデバッグに使用されます。ヒートマップなどの分析ツールを使用すると、ユーザーが最も多くの時間を費やしているか、特定のオブジェクトや対話が不足している場所を確認できます。 また、facilitators のエクスペリエンスに強力なツールを提供することもできます ( [Lowe のキッチン](holographic-frame.md#lowes-kitchen)の例を参照してください)。

<br>

---

## <a name="performance"></a>パフォーマンス

Holographic フレームを適切に使用することは、[パフォーマンス品質](understanding-performance-for-mixed-reality.md)エクスペリエンスの基礎となります。 一般的な技術 (およびユーザビリティ) の課題は、ユーザーのフレームをデジタルコンテンツでオーバーロードすることで、レンダリングのパフォーマンスが低下する原因となっています。 代わりに、前述の方法を使用して、デジタルコンテンツを整理するために、ユーザーの周囲に十分な領域を使用して、レンダリングの負担を軽減し、表示品質を最適化することを検討してください。

HoloLens の holographic フレーム内のデジタルコンテンツを[安定化面](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)と組み合わせて、最適なパフォーマンスとホログラムの[安定性](hologram-stability.md)を実現することもできます。

<br>

---

## <a name="examples"></a>例

### <a name="volvo-cars"></a>Volvo 車

<iframe width="940" height="530" src="https://www.youtube.com/embed/DilzwF90vec" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Volvo 車の showroom エクスペリエンスでは、ユーザーは、Volvo の関連付けによって指示された HoloLens エクスペリエンスの新しい自動車の機能について学習するように招待されています。 Volvo は holographic フレームの課題に直面しています。完全な車が大きすぎてユーザーの隣に配置できません。 このソリューションでは、物理的なランドマーク (showroom の中央テーブル) を使用して、自動車の小型のデジタルモデルをテーブルの上に配置しました。 これにより、ユーザーは導入された車を確実に見ることができます。これにより、車が実際の規模に達した後でも、空間を理解することができます。

また、volvo の経験によって、ビジュアルダイレクタも利用され、テーブルの小規模な自動車モデルから [部屋の表示] の壁に対して大きな視覚効果が生じます。 これにより、"マジックウィンドウ" 効果が生じ、距離に自動車の全ビューが表示されます。これは、実際のスケールでの自動車のさらなる特徴を示しています。 ヘッドの移動は水平方向であり、ユーザーから直接やり取りすることはありません (代わりに、合図を視覚的に収集し、Volvo によって操作のナレーションを関連付けます)。

<br>

---

### <a name="lowes-kitchen"></a>Lowe の台所

Lowe のストアエクスペリエンスは、お客様に対して、HoloLens を通じて見たさまざまな remodeling の機会を紹介するために、お客様にキッチンのフルスケールのモックアップを招待します。 店舗のキッチンは、デジタルオブジェクトの物理的な背景、アプライアンスの空のキャンバス、countertops 大部分、および混合の現実エクスペリエンスを実現するためのキャビネットを提供します。

物理的な面は、ユーザーが自分の経験を持ってきたときのための固定の目印として機能します。 Lowe の関連付けにより、ユーザーがさまざまな製品オプションを使用して作業を完了するためです。 このようにして、関連付けによって、ユーザーの注意を "冷蔵庫" または "口頭で他者" に誘導し、デジタルコンテンツを紹介することができます。

![Lowe の関連付けでは、タブレットを使用して HoloLens エクスペリエンスをユーザーに案内します。](images/loweskitchen-750px.jpg)<br>
*Lowe の関連付けでは、タブレットを使用して HoloLens エクスペリエンスをユーザーに案内します。*

ユーザーのエクスペリエンスは、部分的に、Lowe の関連付けによって制御されるタブレットエクスペリエンスによって管理されます。 このケースでは、関連するロールの一部として、過度のヘッド移動を制限して、キッチンの関心のある地点間でスムーズに注意を向けることもできます。 また、タブレットのエクスペリエンスでは、キッチンのヒートマップビューの形式で、ユーザーがどこに dwelling しているか (たとえば、キャビネットの特定領域など) を理解し、remodeling のガイダンスをより正確に提供するために役立ちます。

Lowe のキッチンエクスペリエンスの詳細については、 [Ignite 2016 のマイクロソフトの基調講演](https://www.youtube.com/watch?v=gC_4JxF0e_k)を参照してください。

<br>

---

### <a name="fragments"></a>fragments

HoloLens ゲームのフラグメントでは、生きた部屋が仮想犯罪シーンに変換されます。このシーンでは、ヒントと証拠、および仮想ミーティングルームが示されています。このシーンでは、椅子に座って壁上にある文字と話します。

![フラグメントは、ユーザーの自宅で実行されるように設計されており、文字は実際のオブジェクトとサーフェイスと対話します。](images/fragments-750px.jpg)<br>
*フラグメントは、ユーザーの自宅で実行されるように設計されており、文字は実際のオブジェクトとサーフェイスと対話します。*

ユーザーが最初に経験を始めたときには、わずかな調整が与えられます。この場合、ほとんどの操作は必要ありません。 これにより、ゲームの対話型コンテンツに対してルームが正しくマップされるようにも役立ちます。

このエクスペリエンス全体を通じて、文字は注目ポイントになり、視覚ダイレクタとして機能します (文字の間のヘッド移動、関心のある領域の検索とジェスチャの切り替え)。 また、ゲームでは、ユーザーがオブジェクトやイベントを検索するのに時間がかかりすぎて、空間オーディオ (特にシーンを入力するときに文字音がある) を頻繁に使用する場合に、より目立つ視覚的な合図にも依存しています。

<br>

---

### <a name="destination-mars"></a>宛先: Mars

これは、 [NASA のケネディのケネディ空間センター](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/)で提供されている mars エクスペリエンスです。訪問者は、mars の表面へのイマーシブトリップに招待されました。これは、伝説 Astronaut 評判 aldrin 仮想表現によってガイドされています。

![「」では、仮想の話題が、宛先のユーザーの中心点になります。](images/destinationmars-750px.png)<br>
*「」では、仮想の話題が、宛先のユーザーの中心点になります。*

イマーシブエクスペリエンスとして、これらのユーザーは、仮想 Martian ランドスケープを確認するために、すべての方向に移動することをお勧めしました。 ユーザーの快適さを確保するために、のナレーションと仮想プレゼンスは、エクスペリエンス全体を通じて焦点を置いてきました。 この話題 ( [Microsoft の Mixed Reality Capture スタジオ](https://www.microsoft.com/mixed-reality/capture-studios)によって作成された) のこの仮想記録は、部屋の隅にあるそこで、ユーザーがほぼ完全なビューで閲覧できるようにします。 ユーザーのナレーションは、特定のシーンの変化やオブジェクトを使用して、環境内のさまざまなポイント (たとえば、床の Martian のセットや距離の山の範囲など) に専念するように誘導しました。

![仮想 narrators は、ユーザーの動きに従って、エクスペリエンス全体を通じて強力な焦点を発揮します。](images/gazereset-750px.png)<br>
*仮想 narrators は、ユーザーの動きに従って、エクスペリエンス全体を通じて強力な焦点を発揮します。*

写実的な表現は、強力な焦点として提供されていました。微妙な手法を使用すると、ユーザーにとっては、話をしているように見えます。 ユーザーが経験を移動すると、ユーザーが周囲を超えて移動したときにニュートラル状態に戻る前に、話題がしきい値に移ります。 たとえば、シーン内の他の場所を見ているように、ユーザーが完全に話題に移動した後で、その後で、ユーザーに対してナレーターの方向が再びフォーカスされます。 このような手法は、immersion の強力な意味を持ち、holographic フレーム内に焦点を合わせています。これにより、過度のヘッド移動が減少し、[ユーザーの快適](comfort.md)さが促進されます。

## <a name="see-also"></a>関連項目
* [本能的な操作](interaction-fundamentals.md)
* [快適性](comfort.md)
* [スケール](scale.md)
* [ヘッド視線入力とドウェル](gaze-and-dwell.md)
* [ホログラムの安定性](hologram-stability.md)
