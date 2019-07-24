---
title: Mixed reality とは
description: この記事では、mixed reality を定義し、単純な AR デバイスと VR デバイス、および Microsoft HoloLens や Windows Mixed Reality イマーシブヘッドセットなどの Windows Mixed Reality デバイスと、混合現実の範囲について説明します。
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: mixed reality、holographic、ar、vr、mr、xr、強化現実、仮想現実、説明
ms.openlocfilehash: fbac8176b36cf28673dd9633cc059e5856a50296
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326310"
---
# <a name="what-is-mixed-reality"></a>Mixed reality とは

Mixed reality は、物理的な世界とデジタルの世界をブレンドした結果です。 Mixed reality は、人間、コンピューター、および環境の相互作用における次の進化であり、現在の夢見るに制限されている可能性があります。 これは、コンピュータービジョン、グラフィカル処理能力、表示テクノロジ、および入力システムの機能強化によって可能になります。 *Mixed reality*という用語は、当初、Paul ミルグラムと Fumio Kishino によって1994のホワイトペーパーに導入されまし[た。](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html) このホワイトペーパーでは、 *virtuality 連続性*の概念を紹介し、分類の分類がどのように表示されるかに焦点を絞っています。 そのため、混合現実のアプリケーションは表示されません。 また、環境の入力、空間サウンド、場所も含まれます。

## <a name="environmental-input-and-perception"></a>環境の入力と認識

![コンピューター、人間、および環境間の相互作用を示すベン図](images/mixed-reality-venn-diagram-300px.png)<br> 

過去数年にわたり、人間とコンピューターの両方の入力の関係が十分に調査されました。 また、*人間のコンピューターの操作*や HCI と呼ばれる、広く研究されている分野もあります。 人間の入力は、キーボード、マウス、タッチ、インク、音声、さらには Kinect の骨格追跡など、さまざまな方法で行われます。

センサーと処理の進歩は、環境からのコンピューター入力の新しい領域に大きくなります。 コンピューターと環境の間の相互作用は、実質的には環境の理解または*認識*です。 そのため、環境情報を公開する Windows の API 名は、[認識 api](https://docs.microsoft.com/uwp/api/Windows.Perception)と呼ばれます。 環境入力では、世界中のユーザーの位置 ([ヘッドトラッキング](coordinate-systems.md)など)、表面と境界 ([空間マッピング](spatial-mapping.md)と[空間の理解](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)など)、アンビエント照明、環境サウンド、オブジェクトなどがキャプチャされます。認識と場所。

ここで、3つのコンピューターの処理、人間による入力、および環境入力のすべてを組み合わせて、真の mixed reality エクスペリエンスを作成する機会を設定します。 物理的な世界への移動は、デジタル世界での動きにつながる可能性があります。 物理的な世界の境界は、デジタル環境でのゲームプレイなどのアプリケーションエクスペリエンスに影響を与える可能性があります。 環境情報を入力しないと、経験によって物理的な現実とデジタルの現実とを組み合わせることはできません。

## <a name="the-mixed-reality-spectrum"></a>混合現実のスペクトラム

Mixed reality は物理的な世界とデジタルの両方の面を融合しているため、これらの2つの現実は、virtuality の連続性と呼ばれるスペクトルの極端を定義しています。 わかりやすくするために、これを*混合現実のスペクトラム*と呼びます。 左側には、人間が存在する物理的な現実があります。右側には、対応するデジタル現実があります。

<br>

>[!VIDEO https://www.youtube.com/embed/_xpI0JosYUk]

現在市場にあるほとんどの携帯電話では、環境を理解する機能はほとんどありません。 そのため、これらのエクスペリエンスでは、物理的な現実とデジタルの現実を混在させることはできません。 物理的な世界のビデオストリームにグラフィックスを重ね合わせるというエクスペリエンスが、*現実*に拡張されています。 デジタルエクスペリエンスを提供するためにビューを occlude するエクスペリエンスは、*仮想現実*です。 ご覧のように、これら2つの極端な間で有効になっているエクスペリエンスは*mixed reality*です。
* 物理的な世界から、ホログラムなどのデジタルオブジェクトを実際に存在しているかのように配置します。
* 物理的な世界から、別の人のデジタル表現 (アバター) を使用して、ノートを離れるときの場所を示しています。 つまり、さまざまな時点での非同期コラボレーションを表すエクスペリエンスです。
* デジタル環境では、壁や家具など、物理的な世界の物理的な境界は、ユーザーが物理的なオブジェクトを回避するのに役立つように、エクスペリエンス内にデジタルで表示されます。

![混合現実のスペクトラム](images/mixed-reality-spectrum-550px.png)

現在利用可能なほとんどの拡張現実および仮想現実のオファリングは、この範囲のごく一部を表しています。 ただし、より大きな混合現実の範囲のサブセットです。 Windows 10 は、すべての点を念頭に置いて構築されており、人間、場所、および物のデジタル表現を実際の世界にブレンドできます。

![混合現実スペクトルのデバイスの種類](images/mixed-reality-spectrum-device-types-550px.png)

Windows Mixed Reality エクスペリエンスを提供するデバイスには、主に次の2種類があります。
1. **Holographic デバイス。** これらの特性は、デバイスが実際に存在しているかのように、実際の世界にデジタルコンテンツを配置する機能によって特徴付けられています。
2. **イマーシブデバイス。** これらは、物理的な世界を隠し、デジタル体験で置き換えることによって、デバイスの機能によって特徴付けられています。

<table>
<tr>
<th width="20%"> 特性</th><th width="40%"> Holographic デバイス</th><th width="40%"> イマーシブデバイス</th>
</tr><tr>
<td> デバイスの例</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Acer Windows Mixed Reality Development Edition<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> ディスプレイ</td><td> <i>「」を参照してください。</i> ヘッドセットを装着しているときに、ユーザーが物理環境を確認できるようにします。</td><td> <i>非透過ディスプレイ。</i> ヘッドセットの装着中に物理環境をブロックします。</td>
</tr><tr>
<td> 動かす</td><td> 回転と翻訳の両方で、完全に6度の自由な移動。</td><td> 回転と翻訳の両方で、完全に6度の自由な移動。</td>
</tr>
</table>

デバイスが別の PC に接続されているかどうか (USB ケーブルまたは Wi-fi 経由)、または自己完結型 (ならでは) であるかどうかは、デバイスが holographic かイマーシブかは反映されません。 確かに、モビリティを向上させる機能によりエクスペリエンスが向上し、holographic デバイスとイマーシブデバイスの両方がテザリングさまたはならではになる可能性があります。

## <a name="devices-and-experiences"></a>デバイスとエクスペリエンス

技術的な進歩は、mixed reality エクスペリエンスを有効にしたものです。 現在、すべての範囲でエクスペリエンスを実行できるデバイスはありません。 ただし、Windows 10 では、デバイスの製造元と開発者の両方に共通の mixed reality プラットフォームが提供されます。 現在のデバイスは、混合現実の範囲内の特定の範囲をサポートできます。 時間の経過と共に、新しいデバイスによってその範囲が拡張されます。 将来、holographic デバイスはよりイマーシブになり、イマーシブデバイスはより holographic になります。

![デバイスが混合現実のスペクトラムにどのように配置されているか](images/mixed-reality-spectrum-device-placement-550px.png)

多くの場合、アプリケーションまたはゲーム開発者が作成しようとしているエクスペリエンスの種類を考えることをお勧めします。 エクスペリエンスは、通常、特定のポイントまたは部分を対象としています。 次に、開発者は、対象とするデバイスの機能を考慮する必要があります。 たとえば、物理的な世界に依存するエクスペリエンスは、HoloLens で最高のパフォーマンスを発揮します。
* **左側 (ほぼ物理的な現実)。** ユーザーは、物理的な環境内に存在していて、その環境が離れていると信じられることはありません。
* **中央に (完全に混在する現実)。** これらのエクスペリエンスでは、現実世界とデジタル世界を融合しています。 映画の[Jumanji](https://en.wikipedia.org/wiki/Jumanji)を見た閲覧者は、ストーリーがどこで行われたかについて、その家の物理的な構造を調整して、ジャングル環境と連携させることができます。
* **右側に (デジタル現実に近い)。** ユーザーは、完全なデジタル環境を体験し、物理的な環境で何が起こっているかを認識していません。


## <a name="see-also"></a>関連項目
* [API リファレンス:Windows. 認識](https://docs.microsoft.com/uwp/api/Windows.Perception)
* [API リファレンス:Windows... 空間](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial)
* [API リファレンス:Windows... 空間](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial.Surfaces)
