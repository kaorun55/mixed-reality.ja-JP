---
title: 文字体裁
description: テキストは、アプリのエクスペリエンスで情報を提供する重要な要素です。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、スタイル、フォント、文字体裁、ui、ux
ms.openlocfilehash: b4bac35cbc412ec7102748350c2f5c1e236c2f7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603250"
---
# <a name="typography"></a>文字体裁

テキストは、アプリのエクスペリエンスで情報を提供する重要な要素です。 2D 画面に文字体裁と同じようには、目的が明確で読みやすくします。 複合現実の 3 次元の側面には、テキストと全体的なユーザーに影響する機会をさらに優れた方法でのエクスペリエンス。

![HoloLens の文字体裁の例](images/640px-typography-hero2.jpg)<br>
*HoloLens の文字体裁の例*

3D での型について話すとき押し出された、帯域幅消費型の 3D テキストを考える傾向があります。 一部のロゴのデザインと他のいくつかの制限付きアプリケーションを除く押し出されたテキストは、テキストの読みやすさが低下する傾向があります。 場合でも、私たちは 3D のエクスペリエンスを設計して、2 D 型のため、使用がより読みやすく、読みやすくします。

HoloLens では、種類はホログラム加法色のシステムに基づく light を使用してで構築されます。 他のホログラムと同じように型配置できる実際の環境で世界がロックされており、あらゆる角度から観察されたこと。 [視差](https://en.wikipedia.org/wiki/Parallax)型と、環境の間の効果の深さをエクスペリエンスにも追加します。

## <a name="typography-in-mixed-reality"></a>複合現実での文字体裁

複合現実での文字体裁の規則はありませんから任意の場所です。 物理環境と仮想環境の両方のテキストを読みやすく、読み取り可能にする必要があります。 テキストは、壁に可能性があります。 または物理オブジェクト上に重ねて表示します。 デジタルのユーザー インターフェイスと共に浮動でした。 コンテキストに関係なく、読み取りと認識と同じ表記規則が適用されます。

### <a name="create-clear-hierarchy"></a>明確な階層を作成します。

さまざまなサイズと重みを使用して、コントラスト、および階層をビルドします。 種類ごとの傾斜増加を定義して、アプリのエクスペリエンス全体で一貫性のある情報の階層で優れたユーザー エクスペリエンスを送りします。

![種類ごとの傾斜増加の例](images/typography-ramp-1000px.jpg)<br>
*種類ごとの傾斜増加の例*

### <a name="limit-your-fonts"></a>フォントを制限します。

1 つのコンテキストで 2 つ以上の別のフォント ファミリを使用しないでください。 調和と整合性のエクスペリエンスの中断を困難に情報を使用します。 HoloLens で、情報が、物理環境の上に重なって表示ためが多すぎるのフォント スタイルを使用してが低下経験します。 Segoe UI は、すべての Microsoft デジタル設計フォントです。 Windows Mixed Reality シェルで一貫して使用されます。 Segoe UI フォント ファイルをダウンロードすることができます、 [Windows デザイン ツールキット ページ](https://docs.microsoft.com/windows/uwp/design-downloads/)します。

[Segoe UI フォントの詳細について](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>細いフォントの太さを回避します。

シンの垂直線はバイブレーションし、読みやすさが低下するために、42 pt 型のサイズの明るいまたは semilight のフォントの太さを使用しないでください。 十分なストロークの太さで最新のフォントがうまく機能します。 たとえば、Helvetica と Arial は HoloLens で非常に判読または正規の太字の重みを使用してます。

### <a name="color"></a>色

は、HoloLens、ホログラムが加法ライト システムで構築されているために、白いテキストは非常に読みやすいが。 [スタート] メニューと、アプリ バーに白いテキストの例が表示されます。 白いテキストは、HoloLens でバック プレートなしでも機能する場合でも複雑な物理背景でしたする種類読みにくくします。 ユーザーのフォーカスを改善し、物理的なバック グラウンドからの邪魔を最小限に抑える、暗色または戻る色付きの版に白いテキストを使用をお勧めします。

<br>


![濃いまたは色付きのバック版に白いテキストを使用することをお勧めします。](images/typography-whiteonblack2-1000px.jpg)

濃いまたは色付きのバック版に白いテキストを使用することをお勧めします。

<br>


![黒のテキストの例](images/640px-typography-textcolors.jpg)

暗いテキストを使用するには、読み明るいバック皿を使用する必要があります。 付加的な色のシステムでは黒が透明色として表示されます。 つまり、プレートのバックアップを色なし、黒色のテキストを表示することはできません。

<br>


![黒のテキストの例](images/640px-typography-blackonwhite.jpg)

UWP アプリ ストアなどの設定では、黒のテキストの例が見つかります。

## <a name="recommended-font-size"></a>推奨のフォント サイズ

![2 つのメーターは、テキストを表示するための最適な距離です。](images/typography-distance-1000px.jpg)

2 つのメーターは、テキストを表示するための最適な距離です。

複合現実には、3 次元の深さが含まれているので簡単ではありません常にフォントのサイズを通信するためにします。 ユーザーの快適性、2 つのメーターはホログラムを配置するための最適な距離です。 この距離、最適なフォント サイズを確認するのに基礎として使用できます。

予想されることができますの 2 m 離れた距離にある非常に小さく、PC またはタブレット デバイス (通常は 12: 32 ポイント) 間を参照してくださいで使用するサイズを入力します。 各フォントの特性によって異なりますが、一般に、ストロークの振動ことがなく読みやすいように推奨される最小値の型のサイズには約 30 pt。 アプリは、近い距離に使用することになって、比較的小さなサイズの型を使用できます。 **ポイントのサイズは、Unity のテキストを 3D メッシュと UI テキストに基づきます。詳細なメトリックとスケール ファクターを参照してください[Unity 内のテキスト](text-in-unity.md)します。**

## <a name="resources"></a>参考資料
* [Segoe フォント](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [HoloLens のフォント](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

![HoloLens のフォントは、Windows Mixed Reality で使用されるシンボルのグリフを提供します。](images/300px-hololensmdl2symbols.jpg)

HoloLens のフォントでは、Windows Mixed Reality で使用されるシンボルのグリフを提供します。

## <a name="see-also"></a>関連項目
* [Unity 内のテキスト](http://holodocsfuture/index.php?title=Text_in_Unity&action=edit&redlink=1)
* [色、ライト、マテリアル](color,-light-and-materials.md)
