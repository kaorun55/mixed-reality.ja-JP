---
title: 要素の定期処理テーブル
description: 要素のテーブルを定期的では、Microsoft の混合現実デザイン ラボ オブジェクトのコレクションを使用して、さまざまな表面型で、3 D 空間内のオブジェクトの配列をレイアウトする方法を学びますからオープン ソースのサンプル アプリです。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、サンプル アプリ、コントロール
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604114"
---
# <a name="periodic-table-of-the-elements"></a>要素の定期処理テーブル

>[!NOTE]
>この資料で説明した調査用のサンプル、[混合現実デザイン Labs](https://github.com/Microsoft/MRDesignLabs_Unity)、について学習したことを共有の場所とに関する推奨事項は、現実アプリ開発を混在させます。 新しい検出を行ったときは、デザインに関連する記事とコードも進化します。

[要素のテーブルを定期的](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)は Microsoft の混合現実デザイン ラボからオープン ソースのサンプル アプリです。 このプロジェクトのさまざまなサーフェイスのタイプを使用して 3D 空間でオブジェクトの配列を配置する方法を学びます、 **[オブジェクト コレクション](object-collection.md)** します。 HoloLens からの標準入力に応答する対話型のオブジェクトを作成する方法についても説明します。 実際にはアプリのエクスペリエンスを混合独自に作成する、このプロジェクトのコンポーネントを使用することができます。

![要素のアプリの期間のテーブル](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>アプリの詳細について

要素の周期の表は、化学の要素とそのプロパティを 3D 空間での各は視覚化します。 HoloLens の注視しエア タップなどの基本的な対話が組み込まれています。 ユーザーは、アニメーションの 3D モデルの要素について学習できます。 要素の electron シェルであり、その中核は-protons と neutrons で構成されますが、視覚的に理解できます。

## <a name="background"></a>背景

HoloLens をまずが発生した後、周期表アプリは、複合現実で実験したいことがわかってアイデアをしました。 各要素には、テキストで表示されるデータ ポイントの数があるのでを 3D 空間での文字体裁の合成を探索するための優れた主題になると考えました。 要素の電子モデルを視覚化することがこのプロジェクトの別の興味深い部分です。

## <a name="design"></a>設計

定期テーブルの既定のビューの各要素の電子モデルが含まれる 3 次元のボックスは想像していた。 ユーザーが要素のボリュームの大まかに理解をすることができるように、各ボックスの画面は半透明なります。 視線入力や air をタップして、ユーザーは各要素の詳細なビューを開くでした。 テーブルのビューと詳細ビュー間の遷移をスムーズかつ自然にするには、しました、現実の世界を開く ボックスの物理的な相互作用に似ています。

![設計のスケッチ](images/640px-sketch20170406.jpg)<br>
*設計のスケッチ*

詳細ビューで 3D 空間で美しく表示されるテキストの各要素の情報を視覚化することを考えました。 アニメーション化された 3D electron モデルでは、中央の領域に表示され、さまざまな角度から表示できます。

![操作](images/640px-periodictable-interaction.jpg)

![プロトタイプ](images/640px-periodictable-prototypes.jpg)<br>
*プロトタイプの対話*

ユーザーは、テーブルの下部にあるボタンをタップして air によってサーフェスのタイプを変更することができます - プレーン、円柱、球、散布図を切り替えることができます、します。

## <a name="common-controls-and-patterns-used-in-this-app"></a>一般的なコントロールとこのアプリで使用されるパターン

### <a name="interactable-object-button"></a>対話型のオブジェクト (ボタン)

[対話型のオブジェクト](interactable-object.md)HoloLens の基本的な入力に応答できるオブジェクトです。 これは、任意のオブジェクトを簡単に適用できるプレハブ/スクリプトとして提供されます。 たとえば、こと、シーン内のコーヒー カップを対話型し、視線の先、エア タップ、移動および操作のジェスチャなどの入力に応答できます。 [詳細情報](interactable-object.md)

![nteractable オブジェクト](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>オブジェクトのコレクション

[オブジェクト コレクション](object-collection.md)オブジェクトは、さまざまな図形で複数のオブジェクトをレイアウトするのに役立ちます。 平面、円柱、球、散布図をサポートします。 Radius、行との間隔の数などの追加プロパティを構成することができます。 [詳細情報](object-collection.md)

![オブジェクトのコレクション](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

既定では、ホログラムをユーザーが gazing は場所に配置するが、現時点では、アプリケーションが起動します。 これは、ホログラム壁の背後にある、またはテーブルの中央に配置されているなどの望ましくない結果にもつながります。 Fitbox 視線の先を使用して、ホログラムを配置する場所を決定することができます。 これは、独自のイメージや 3D オブジェクトを簡単にカスタマイズ可能な単純な PNG イメージ テクスチャで作成されます。

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>技術的な詳細

見つかりますスクリプトとプレハブ要素アプリの定期的テーブルで、 [Mixed Reality デザイン Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)します。

## <a name="application-examples"></a>アプリケーションの例

ここではこのプロジェクト内のコンポーネントを活用することで作成する可能性があります。

### <a name="stock-data-visualization-app"></a>株価データ視覚化アプリ

要素のサンプルの定期テーブルとしては、同じコントロールと対話モデルを使用して、株式市場データを視覚化するアプリを構築できます。 この例では、オブジェクトのコレクションのコントロールを使用して球を図形の株価データをレイアウトします。 詳細ビューが興味深い方法で各株式に関する追加情報を表示でしたを想像できます。

![アプリケーションの例:Finance (1/3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![アプリケーションの例:Finance (2/3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![アプリケーションの例:Finance (3/3)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*要素のサンプル アプリの定期的テーブルで使用されるオブジェクトのコレクションを財務アプリで使用する方法の例*

### <a name="sports-app"></a>スポーツ アプリ

これは、オブジェクトのコレクションと要素のサンプル アプリの定期的テーブルからその他のコンポーネントを使用して、スポーツ データの視覚化の例です。

![アプリケーションの例:スポーツ (1/3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![アプリケーションの例:スポーツ (2/3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![アプリケーションの例:スポーツ (3/3)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*要素のサンプル appcould の周期の表ではオブジェクトのコレクションを使用する方法の例は、スポーツ アプリで使用します。*

## <a name="about-the-author"></a>執筆者紹介

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>ドン Yoon Park</b><br>UX デザイナー @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>関連項目

* [対話型のオブジェクト](interactable-object.md)
* [オブジェクトのコレクション](object-collection.md)
