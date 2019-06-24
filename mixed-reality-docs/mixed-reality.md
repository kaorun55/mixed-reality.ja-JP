---
title: どのような複合現実をですか。
description: この記事では、複合現実を定義し、複合現実スペクトルに沿っての単純な AR、VR デバイス、だけではなく、Microsoft HoloLens と Windows Mixed Reality のイマーシブ ヘッドセットなどの Windows Mixed Reality デバイスの配置場所を示します。
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: 複合現実、holographic、ar、vr、mr、xr、拡張現実、仮想現実、説明
ms.openlocfilehash: fbac8176b36cf28673dd9633cc059e5856a50296
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326310"
---
# <a name="what-is-mixed-reality"></a>どのような複合現実をですか。

複合現実では、デジタルの世界と現実の世界をブレンドの結果です。 複合現実では、ユーザー、コンピューター、および環境の相互作用における次の進化は、し、可能性をこれまで、imaginations に制限されていましたのロックを解除します。 これは、コンピューター ビジョン、グラフィカルな処理能力、表示テクノロジ、および入力システムの進歩によって実現されます。 用語*複合現実*Paul Milgram して Fumio Kishino、1994年ホワイト ペーパーで導入された"[混合の分類を実際には視覚的な表示](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)"。 そのホワイト ペーパーの概念が導入、*仮想 continuum*に適用される分類法の分類を表示する方法に重点を置いてとします。 その後、複合現実のアプリケーションが表示されますを超えます。 環境の入力、サウンドの空間、および場所も含まれています。

## <a name="environmental-input-and-perception"></a>環境の入力や認識

![コンピューター、人間、環境間の相互作用を示す venn ダイアグラム](images/mixed-reality-venn-diagram-300px.png)<br> 

過去何十年にも、経由では、人間とコンピューター入力間のリレーションシップをもについて説明されているしました。 呼ばれる広く研究された規範に*人間のコンピューター間の対話*または HCI します。 ユーザーによる入力は、さまざまなキーボード、マウス、タッチ、インク、音声、および Kinect スケルトンの追跡もなどの方法では発生します。

センサーと処理の進歩は環境から、コンピューターの入力の新しい領域に上昇に付与されます。 コンピューターと環境間の相互作用が効果的に環境の理解や*perception*します。 環境情報を表示するための Windows での API 名が呼び出されるため、 [perception Api](https://docs.microsoft.com/uwp/api/Windows.Perception)します。 環境の入力などの世界で個人の位置をキャプチャする (例:[ヘッド追跡](coordinate-systems.md))、サーフェスと境界 (例:[空間マッピング](spatial-mapping.md)と[空間理解](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md))、環境光、環境音、オブジェクトの認識、および場所です。

ここで、3 - すべてのコンピューター処理の組み合わせ、人間の入力、および環境の入力 - 設定 true 複合現実エクスペリエンスを作成すること。 現実の世界での移動は、デジタルの世界での移動に変換できます。 現実の世界で境界デジタルの世界でのゲーム プレイなどのアプリケーション エクスペリエンスに影響を与えることができます。 環境の入力を行わなくてもエクスペリエンスは、物理とデジタルの現実の間で blend ことはできません。

## <a name="the-mixed-reality-spectrum"></a>複合現実スペクトル

複合現実では、物理とデジタルの両方の長所をブレンド、ために、これら 2 つの現実は仮想 continuum と呼ばれるスペクトルの極座標 end を定義します。 わかりやすくするため、これに言及、*複合現実スペクトル*します。 左側にある私たち人間に存在する; 物理的現実があります。右側にある、対応するデジタル現実があります。

<br>

>[!VIDEO https://www.youtube.com/embed/_xpI0JosYUk]

市場でのほとんどの携帯電話には、今日 no にほとんどの環境についての機能がありません。 したがって物理とデジタルの現実の間、エクスペリエンスを提供するを混ぜることはできません。 現実の世界のビデオ ストリーム上の画像をオーバーレイするエクスペリエンスは*拡張現実*します。 ビュー、デジタル エクスペリエンスを提供するエクスペリエンスは*仮想現実*します。 ご覧のように、これら 2 つの両極端の間で有効なの経験は*複合現実*:
* 現実の世界では、実際には、そこにあったかのように、ホログラムなどのデジタル オブジェクトを配置することで開始しています。
* 現実の世界では、- 別のユーザーのデジタル形式で始まる--アバターがノートの終了時に、立っていた場所を示しています。 つまり、さまざまな時点での非同期のコラボレーションを表すエクスペリエンス。
* ユーザーが物理オブジェクトを回避するためのエクスペリエンスで以降デジタルの世界では、壁や、家具など、現実の世界から物理的な境界をデジタル表示します。

![複合現実スペクトル](images/mixed-reality-spectrum-550px.png)

最も拡張現実と使用可能な仮想現実内容今日このスペクトルのごく一部を表します。 ただし、大きい複合現実スペクトルのサブセットです。 Windows 10 では、全体の範囲を考慮して、使用して作成され、により、人物、場所、および現実の世界でのデジタルの表現を描画します。

![複合現実スペクトルにデバイスの種類](images/mixed-reality-spectrum-device-types-550px.png)

Windows Mixed Reality エクスペリエンスを提供するデバイスの 2 つの主な種類あります。
1. **Holographic デバイス。** これらは、実際に存在した場合と同じ、現実の世界にデジタル コンテンツを配置するデバイスの機能によって特徴付けられます。
2. **没入型のデバイス。** これらは、「プレゼンス」--現実の世界を非表示化とデジタル エクスペリエンスに置き換えることの意味を作成するデバイスの機能によって特徴付けられます。

<table>
<tr>
<th width="20%"> 特性</th><th width="40%"> Holographic デバイス</th><th width="40%"> 没入型のデバイス</th>
</tr><tr>
<td> デバイスの例</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Acer の Windows Mixed Reality Development Edition<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> ディスプレイ</td><td> <i>透かしが表示されます。</i> ヘッドセット ソックスを着けずにいるときに、物理環境を参照できます。</td><td> <i>非透過が表示されます。</i> ソックスを着けずにヘッドセット中には、物理環境をブロックします。</td>
</tr><tr>
<td> 移動</td><td> 完全な 6 つ自由度の移動、回転と変換の両方。</td><td> 完全な 6 つ自由度の移動、回転と変換の両方。</td>
</tr>
</table>

なお、デバイスに接続されているかどうかまたは (USB ケーブルまたは Wi-fi) 経由で別の PC または自己完結型の (無制限) はテザリングされたデバイスとは holographic または没入型かどうかは含まれません。 確かに、モビリティを強化する機能より優れたエクスペリエンスにつながるおよび holographic と没入型の両方のデバイスがであるテザリングされたか無制限。

## <a name="devices-and-experiences"></a>デバイスとエクスペリエンス

技術の進歩では、何が複合現実エクスペリエンスを有効にします。 全体の広範囲にわたる経験を実行できるデバイスを今すぐはありません。 ただし、Windows 10 では、デバイスの製造元と開発者の両方の共通の複合現実プラットフォームを提供します。 今すぐのデバイスは、複合現実の範囲内の特定の範囲をサポートできます。 時間の経過と共に新しいデバイスはその範囲を展開します。 今後、holographic デバイスになり、没入感が向上、没入型のデバイスはより holographic になります。

![デバイスが複合現実スペクトルにレイアウトします。](images/mixed-reality-spectrum-device-placement-550px.png)

多くの場合、またはゲーム開発者が作成するアプリケーション エクスペリエンスの種類を考慮することをお勧めします。 特定の時点または、領域の一部、エクスペリエンスは通常対象に。 次に、開発者は、対象とデバイスの機能を検討する必要があります。 たとえば、現実の世界に依存するエクスペリエンスは、HoloLens で最適な実行されます。
* **に向かって (近くに物理的現実) 左。** ユーザーは残りますが、物理環境に存在して、残りの環境とお考えに加えられたことはありません。
* **中間 (完全複合現実)。** これらのエクスペリエンスは、現実の世界とデジタルの世界をブレンドします。 閲覧者向けビデオを見てきました[Jumanji](https://en.wikipedia.org/wiki/Jumanji)ジャングル環境とストーリーが行われた家の物理構造のブレンドされた方法を調整できます。
* **(近くに実際にはデジタル) 右方向。** ユーザーは、完全にデジタル環境が発生しての周囲に物理的な環境で発生するイベントに対応していません。


## <a name="see-also"></a>関連項目
* [API リファレンス:Windows.Perception](https://docs.microsoft.com/uwp/api/Windows.Perception)
* [API リファレンス:Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial)
* [API リファレンス:Windows.Perception.Spatial.Surfaces](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial.Surfaces)
