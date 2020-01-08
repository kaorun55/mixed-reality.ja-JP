---
title: Mixed Reality とは
description: この記事では、mixed reality を定義し、単純な AR デバイスと VR デバイス、および Microsoft HoloLens や Windows Mixed Reality イマーシブヘッドセットなどの Windows Mixed Reality デバイスと、混合現実の範囲について説明します。
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: mixed reality、holographic、ar、vr、mr、xr、強化現実、仮想現実、説明
ms.openlocfilehash: e3205590ce46e0fc9113421e0dbaeb87fe6bc0c2
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334052"
---
# <a name="what-is-mixed-reality"></a>Mixed Reality とは

![ハンズオンを使用したポイントとコミット (HoloLens 2)](images/02_MixedRealitySlashMixedReality.png)

Mixed Reality は現実世界とデジタル世界を組み合わせたものです。 Mixed Reality は、人間、コンピューター、および環境の相互作用における次の進化であり、これまでは想像することしかできなかった可能性が実現されます。 これは、コンピュータービジョン、グラフィカル処理能力、表示テクノロジ、および入力システムの機能強化によって可能になります。 *Mixed reality*という用語は、当初、Paul ミルグラムと Fumio Kishino によって[1994 のホワイト](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)ペーパーに導入されました。 このホワイトペーパーでは、 *virtuality 連続性*の概念を紹介し、分類の分類がどのように表示されるかに焦点を絞っています。 そのため、混合現実のアプリケーションは表示されません。 また、環境の入力、空間サウンド、場所も含まれます。

混合現実のスペクトルを ![](images/mixedrealityspectrum-worlds.png)<br>
*画像: Mixed reality は、物理的な世界とデジタルの世界をブレンドした結果です。*

<br>

---

## <a name="environmental-input-and-perception"></a>環境の入力と認識

過去数年にわたり、人間とコンピューターの両方の入力の関係が十分に調査されました。 また、*人間のコンピューターの操作*や HCI と呼ばれる、広く研究されている分野もあります。 人間の入力は、キーボード、マウス、タッチ、インク、音声、さらには Kinect の骨格追跡など、さまざまな方法で行われます。

センサーと処理の進歩は、環境からのコンピューター入力の新しい領域に大きくなります。 コンピューターと環境の間の相互作用は、実質的には環境の理解または*認識*です。 そのため、環境情報を公開する Windows の API 名は、[認識 api](https://docs.microsoft.com/uwp/api/Windows.Perception)と呼ばれます。 環境入力は、世界中のユーザーの位置 ([ヘッドトラッキング](coordinate-systems.md)など)、表面と境界 ([空間マッピング](spatial-mapping.md)と[シーンの理解](scene-understanding.md)など)、アンビエント照明、環境サウンド、オブジェクト認識、および場所などをキャプチャします。

<br>

コンピューター、人間、および環境間の相互作用を示すベン図 ![](images/mixed-reality-venn-diagram-300px.png)<br> 
*イメージ: コンピューター、人間、環境の間の相互作用。*

<br>

ここで、3つの**コンピューターの処理、人間による入力、および環境入力**のすべてを組み合わせて、真の mixed reality エクスペリエンスを作成する機会を設定します。 物理的な世界への移動は、デジタル世界での動きにつながる可能性があります。 物理的な世界の境界は、デジタル環境でのゲームプレイなどのアプリケーションエクスペリエンスに影響を与える可能性があります。 環境情報を入力しないと、経験によって物理的な現実とデジタルの現実とを組み合わせることはできません。<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>混合現実のスペクトラム

Mixed reality は物理的な世界とデジタルの両方の面を融合しているため、これらの2つの現実は、virtuality の連続性と呼ばれるスペクトルの極端を定義しています。 わかりやすくするために、これを*混合現実のスペクトラム*と呼びます。 左側には、人間が存在する物理的な現実があります。右側には、対応するデジタル現実があります。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>拡張と仮想現実の比較

現在市場にあるほとんどの携帯電話では、環境を理解する機能はほとんどありません。 そのため、これらのエクスペリエンスでは、物理的な現実とデジタルの現実を混在させることはできません。 物理的な世界のビデオストリームにグラフィックスを重ね合わせるというエクスペリエンスが、*現実*に拡張されています。 デジタルエクスペリエンスを提供するためにビューを occlude するエクスペリエンスは、*仮想現実*です。 ご覧のように、これら2つの極端な間で有効になっているエクスペリエンスは*mixed reality*です。
* 物理的な世界から、ホログラムなどのデジタルオブジェクトを実際に存在しているかのように配置します。
* 物理的な世界から、別の人のデジタル表現 (アバター) を使用して、ノートを離れるときの場所を示しています。 つまり、さまざまな時点での非同期コラボレーションを表すエクスペリエンスです。
* デジタル環境では、壁や家具など、物理的な世界の物理的な境界は、ユーザーが物理的なオブジェクトを回避するのに役立つように、エクスペリエンス内にデジタルで表示されます。


<br>

混合現実のスペクトルを ![](images/mixedrealityspectrum.png)<br>
*Image: mixed reality のスペクトル*

<br>

現在利用可能なほとんどの拡張現実および仮想現実のオファリングは、この範囲のごく一部を表しています。 ただし、より大きな混合現実の範囲のサブセットです。 Windows 10 は、すべての点を念頭に置いて構築されており、人間、場所、および物のデジタル表現を実際の世界にブレンドできます。




## <a name="devices-and-experiences"></a>デバイスとエクスペリエンス


Windows Mixed Reality エクスペリエンスを提供するデバイスには、主に次の2種類があります。
1. **Holographic デバイス。** これらの特性は、デバイスが実際に存在しているかのように、実際の世界にデジタルコンテンツを配置する機能によって特徴付けられています。
2. **イマーシブデバイス。** これらは、物理的な世界を隠し、デジタル体験で置き換えることによって、デバイスの機能によって特徴付けられています。

<table>
<tr>
<th width="30%"> 特性</th><th width="35%"> Holographic デバイス</th><th width="35%"> イマーシブデバイス</th>
</tr><tr>
<td><strong>デバイスの例</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey +<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Display</strong></td><td> 「」を参照してください。 ヘッドセットを装着しているときに、ユーザーが物理環境を確認できるようにします。</td><td> 非透過ディスプレイ。 ヘッドセットの装着中に物理環境をブロックします。</td>
</tr><tr>
<td><strong>動かす</strong></td><td> 回転と翻訳の両方で、完全に6度の自由な移動。</td><td> 回転と翻訳の両方で、完全に6度の自由な移動。</td>
</tr>
</table>



デバイスが別の PC に接続されているかどうか (USB ケーブルまたは Wi-fi 経由)、または自己完結型 (ならでは) であるかどうかは、デバイスが holographic かイマーシブかは反映されません。 確かに、モビリティを向上させる機能によりエクスペリエンスが向上し、holographic デバイスとイマーシブデバイスの両方がテザリングさまたはならではになる可能性があります。


技術的な進歩は、mixed reality エクスペリエンスを有効にしたものです。 現在、すべての範囲でエクスペリエンスを実行できるデバイスはありません。 ただし、Windows 10 では、デバイスの製造元と開発者の両方に共通の mixed reality プラットフォームが提供されます。 現在のデバイスは、混合現実の範囲内の特定の範囲をサポートできます。 時間の経過と共に、新しいデバイスによってその範囲が拡張されます。 将来、holographic デバイスはよりイマーシブになり、イマーシブデバイスはより holographic になります。

<br>

混合現実スペクトルでのデバイスの種類の ![](images/Final_WhatIsMixedReality07.png)<br>
*イメージ: デバイスが混合現実のスペクトラムに存在する*

多くの場合、アプリケーションまたはゲーム開発者が作成しようとしているエクスペリエンスの種類を考えることをお勧めします。 エクスペリエンスは、通常、特定のポイントまたは部分を対象としています。 次に、開発者は、対象とするデバイスの機能を考慮する必要があります。 たとえば、物理的な世界に依存するエクスペリエンスは、HoloLens で最高のパフォーマンスを発揮します。
* **左側 (ほぼ物理的な現実)。** ユーザーは、物理的な環境内に存在していて、その環境が離れていると信じられることはありません。
* **中央に (完全に混在する現実)。** これらのエクスペリエンスでは、現実世界とデジタル世界を融合しています。 映画の[Jumanji](https://en.wikipedia.org/wiki/Jumanji)を見た閲覧者は、ストーリーがどこで行われたかについて、その家の物理的な構造を調整して、ジャングル環境と連携させることができます。
* **右側に (デジタル現実に近い)。** ユーザーは、完全なデジタル環境を体験し、物理的な環境で何が起こっているかを認識していません。


## <a name="see-also"></a>「

* [ホログラムとは](hologram.md)
* [Mixed reality の基本を理解する](index.md#understand-the-basics)
* [作成とプロトタイプ作成を開始する](design.md)
* [ツールとアーキテクチャについて学習する](development.md)

