---
title: 3D アプリ起動ツールの設計ガイダンス
description: 3D アプリ起動ツールは、アプリの起動を選択できるユーザーの複合現実の家の「物理」オブジェクトです。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、3D アプリ起動ツール、イマーシブ ヘッドセット、ライブのキューブ
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598551"
---
# <a name="3d-app-launcher-design-guidance"></a>3D アプリ起動ツールの設計ガイダンス

山と水で囲まれた cliff に存在する家として視覚化されます、ホーム Windows Mixed Reality を入力する没入型 (VR) Windows Mixed Reality ヘッドセットに配置するときに (こともできます[他の環境を選択し、自作](add-custom-home-environments.md)). この領域内で、ユーザーは無料、3 D オブジェクトとどのように、関心のあるアプリを整理します。 A **3D アプリ起動ツール**「物理」のオブジェクトでは、ユーザーがアプリを起動するを選択することを実際に家を混在です。

![例:フローティング Bird 3D アプリ起動ツール](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*フローティング Bird 3D アプリ ランチャー例 (架空のアプリ)*

## <a name="3d-app-launcher-creation-process"></a>3D アプリ起動ツールの作成プロセス

3D アプリ起動ツールを作成する 3 つの手順があります。
1. デザインと concepting (この記事)
2. [モデリングとエクスポート](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. アプリケーションに統合します。
    * [UWP アプリ](implementing-3d-app-launchers.md)
    * [Win32 アプリ](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>設計概念

### <a name="fantastic-yet-familiar"></a>空想まだ理解しています。

アプリ起動ツールが存在する Windows Mixed Reality 環境では、一部使いやすく、パーツ ファンタジック/sci-fi です。 最適なランチャーでは、この世界の規則に従います。 使い慣れた、代表的なオブジェクトをアプリから実行しますが、実際には実際の規則のいくつか曲げないように方法と考えてください。 マジックが発生します。

### <a name="intuitive"></a>直感的です

アプリ起動ツールを確認して - アプリを起動する目的で明確にする必要があります、混乱が生じることはできません。 たとえば、ランチャーがも親しみやすく、Cliff の家のについて混乱しないこと、アプリの明らかなのに十分なの代表であることを確認します。 アプリ起動ツールには、タッチとその選択に人を招待する必要があります。

![例:最新の注 3D アプリ起動ツール](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*新しいメモ 3D アプリ ランチャー例 (架空のアプリ)*

### <a name="home-scale"></a>ホーム スケール

Cliff 家に住んで 3D アプリ ランチャーと、既定のサイズが、領域の「物理」の他のオブジェクトを使用する意味を確認してください。 場合は、横にある、ランチャーを配置すると、たとえば、家の工場またはいくつかの家具、ように思われる size-wise、自宅で。 出発点として適していますが、30 の立方センチメートルで外観を確認が、ユーザーことができます、スケール アップまたはスケール ダウン必要な場合に注意してください。

### <a name="own-able"></a>所有できません。

アプリ起動ツールと感じる人が自分のスペースであることを嬉しく思いますなりますオブジェクト必要があります。 ある事実上を囲む自体これらの点では、ランチャーように思われるもののようにユーザーと考えることが望ましい探そうとして、近くに保つため。

![例:3.5. コンフィグレーション Warp の 3D アプリ起動ツール](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*3.5. コンフィグレーション Warp 3D アプリ起動ツールの例 (架空のアプリ)*

### <a name="recognizable"></a>認識可能です

3D アプリ起動ツールは、それを表示してユーザーを「アプリのブランド」を express 瞬時にする必要があります。 アプリにスター文字または特にを特定できるオブジェクトがある、設計の大きな部分として使用することをお勧めします。 複合現実の世界では、オブジェクトは単独でロゴだけよりもユーザーから注目を描画します。 認識可能なオブジェクトは、迅速かつ明確にブランドを通信します。

### <a name="volumetric"></a>帯域幅消費型

平面にロゴを配置して、つもりだけでは、アプリが必要です。 ユーザーの領域で、物理魅力的な 3D オブジェクトのように、ランチャーように思われる。 アプリこれは、バルーン Macy の感謝祭続々 と登場するを想像することをお勧めします。 自問何がうなら人沿いになるようですか。 どの優れたすべて表示する角度からでしょうか。


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a>適切な 3D モデルのヒント

### <a name="best-practices"></a>ベスト プラクティス
* を、アプリ起動ツールの寸法を計画するときは、約 30 cm キューブの撮影してください。 これは、1:1:1 の比率。
* モデルには、10,000 多角形を使用する必要があります。 [三角形の数とレベル (Lod) の詳細の詳細については](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* 可能であれば、イマーシブ ヘッドセットをテストします。
* 可能な限りビルド詳細をモデルのジオメトリ – 詳細のテクスチャに依存しないようにします。
* "Water 緊密な"閉じられたジオメトリを作成します。 モデル化されていない穴なしにします。
* オブジェクトの自然なマテリアルを使用します。 現実の世界での作成を想像してください。
* さまざまな距離とサイズにも、モデルを読み取りを確認します。
* モデルは、準備ができましたが、読み取られたとき、[資産のガイドラインをエクスポートする](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)します。

![テクスチャの微妙な細部を使用するモデルします。](images/20171013-143334-mixedreality-640px.jpg)<br>
*テクスチャの微妙な細部を使用するモデルします。*

### <a name="what-to-avoid"></a>避けるべきこと
* ハイ コントラストの詳細または小さな、ビジー状態のパターンとテクスチャを使用しないでください。
* シン ジオメトリを使用しないでください – 距離はうまく動作しはエイリアスが正しくないことができます。
* モデルの部分に拡張しないように、1 を超える多すぎる: 1:1 の比率。 スケーリングの問題が作成されます。

![ハイ コントラスト、小規模のビジー状態のパターンを避ける](images/20171013-143603-mixedreality-640px.jpg)<br>
*ハイ コントラスト、小さな、ビジー状態のパターンを避ける*

## <a name="how-to-handle-type"></a>型を処理する方法

### <a name="best-practices"></a>ベスト プラクティス
* 型は、アプリ起動ツール (以上) の約 1/3 を構成することをお勧めします。 種類は、人、ランチャーは、実際には、非常に多くの場合は便利なので、ランチャーでアイデアを提供することです。
* Super ワイド型しないように – ようにするアプリケーション ランチャーの範囲内でコア ディメンション (増減) お試しください。
* フラットな型は、作業できますが、ことは、特定の角度からと特定の環境に表示する時間が難しいことができますに注意してください。 ソリッド オブジェクトまたはこれを支援することの背景を配置することを検討する可能性があります。
* 追加のディメンションの種類を感じる 3D での改善。 型の側面を網掛け別、暗い色は読みやすさの役立ちます。


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


**作業の種類の色**
* White
* 黒
* 度の低い彩度の色を明るい

![作業の色を入力します。](images/20171016-112111-mixedreality-640px.jpg)<br>
*作業の種類の色*

### <a name="what-to-avoid"></a>避けるべきこと

**問題を引き起こす種類の色**
* 中間トーン
* 灰色
* 彩度が過剰または再度が下げられた色

![問題を引き起こす色を入力します。](images/20171016-112246-mixedreality-640px.jpg)<br>
*問題を引き起こす種類の色*

## <a name="lighting"></a>照明

アプリ起動ツールのライティング、Cliff 家環境に由来します。 光と影の両方で問題がなくなるため、家全体で複数の場所で、ランチャーをテストすることを確認します。 良い知らせは、このドキュメントでその他の設計ガイダンスに従った場合、ランチャー、Cliff 家でほとんどの照明の形をとても良いです。

テスト環境でさまざまなライトで、ランチャーの外観に適した場所は、メディアのルーム、外側の任意の場所と、戻すテラス (芝生の上の具体的な領域) に、Studio です。 別の適切なテストでは、半分の光と影の半分に配置し、どのように見えるを参照してください。

![光と影の両方で、ランチャーが問題を確認します。](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*光と影の両方で、ランチャーが問題かどうかを確認します。*

## <a name="texturing"></a>テクスチャ リング

### <a name="authoring-your-textures"></a>テクスチャの作成

3D アプリ起動ツールの終了の形式を PBR (物理的に基づくレンダリング) パイプラインを使用して作成された .glb ファイルとなります。 これは、厄介なプロセスでは、まだ行っていない場合は、技術的なアーティストを採用する良い機会です。 場合は、勇敢な DIY-er、時間をかけて[調査および PBR 用語について説明します](http://wiki.polycount.com/wiki/PBR)と何が起こっているか、内部で開始する前にする際に役立つ一般的なミスを回避します。 

![例:新しいメモ アプリ](images/pbr-freshnote1-640px-500px.png)<br>
*新しいメモ 3D アプリ ランチャー例 (架空のアプリ)*

**オーサリング ツールをお勧めします**

使用することをお勧めします。[物質のコピー/貼り付け](https://www.allegorithmic.com/products/substance-painter)Allegorithmic、最終的なファイルを作成しています。 物質ペインタ、ここで PBR シェーダーの作成に詳しくない場合、[チュートリアル](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)します。

(または[3D Coat](https://3dcoat.com/home/)、 [Quixel Suite 2](https://quixel.se/suite2/)、または[Marmoset Toolbag](https://www.marmoset.co/toolbag/)これらのいずれかの経験がある場合のように動作します)。

### <a name="best-practices"></a>ベスト プラクティス

* PBR のアプリ ランチャー オブジェクトが作成された場合、は、Cliff 家環境に変換する非常に簡単ですがあります。
* シェーダーが金属/粗さ作業の流れを指定してください:、Unreal PBR シェーダーが閉じる複製。
* 保持、テクスチャをエクスポートするときに、[推奨されるテクスチャ サイズ](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines)に注意してください。
* リアルタイムの光、オブジェクトを構築することを確認、つまり。
    * ベークド shadows – や影を描画しないように
    * テクスチャでベークド照明を回避します。
    * パッケージを作成する PBR 材料の 1 つを使用して、シェーダーの生成された適切なマップを取得するには

## <a name="see-also"></a>関連項目

* [複合現実を自宅で使用するための 3D モデルを作成します。](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [3D アプリ ランチャー (UWP アプリ) の実装します。](implementing-3d-app-launchers.md)
* [3D アプリ ランチャー (Win32 アプリ) の実装します。](implementing-3d-app-launchers-win32.md)
