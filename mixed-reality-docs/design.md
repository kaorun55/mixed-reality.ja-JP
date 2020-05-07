---
layout: LandingPage
title: 設計とプロトタイプ作成を開始する
description: 何かを作成する準備ができたら、設計とプロトタイプ作成を開始するために必要な基本的な概念について学習しましょう。
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 検出, 配布, インデックス, ランディング ページ, 設計, 開発, チュートリアル, サンプル アプリ, 基本事項, ケース スタディ, リソース, HoloLens の使い方, オープン ソース プロジェクト, 主要な概念, 操作
ms.openlocfilehash: 9ef408e1551e9f6c52a6c5fcf7df3123cc099c8c
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "75334153"
---
# <a name="start-designing-and-prototyping"></a>設計とプロトタイプ作成を開始する


![Mixed Reality の設計の概要](images/03_Design.png)

## <a name="expand-your-design-process"></a>[デザイン プロセスを展開する](case-study-expanding-the-design-process-for-mixed-reality.md)

2016 年に Microsoft が待ち望む開発者のために HoloLens を発表したとき、チームは既に Microsoft の内外のスタジオと協力してデバイスの起動エクスペリエンスを構築していました。 これらのチームは、Mixed Reality の設計の新しいフィールドにおける機会と課題の両方を明らかにして学習しました。 [詳細を見る](case-study-expanding-the-design-process-for-mixed-reality.md)

<br>

---

## <a name="what-are-the-core-concepts-of-an-experience"></a>エクスペリエンスの主要な概念は何か

### <a name="keep-the-user-comfortable---comfort"></a>[ユーザーの快適さを維持する (快適さ)](comfort.md)
ヘッド マウント ディスプレイを可能な限り快適なものにするため、デザイナーと開発者は、これらの手掛かりの自然界での動作方法と同じようにコンテンツを作成して提示することが重要です。

<br>

### <a name="consider-how-the-user-sees-the-world---holographic-frame"></a>[ユーザーには世界がどのように見えるかを考える - (ホログラフィック フレーム)](holographic-frame.md)
ユーザーは、ヘッドセットによって作成される四角形のビューポートを通して、Mixed Reality の世界を見ることになります。 HoloLens では、この四角形の領域はホログラフィック フレームと呼ばれ、ユーザーは自分の周囲の現実世界に重ねてデジタル コンテンツを見ることができます。

<br>

### <a name="types-of-mixed-reality-apps"></a>[複合現実アプリの種類](types-of-mixed-reality-apps.md)
Mixed Reality 用アプリを開発する利点の 1 つは、プラットフォームでサポートできるエクスペリエンスの広さです。 完全にイマーシブな仮想環境から、ユーザーの現在の環境に重ねて表示されるちょっとした情報まで、Mixed Reality では、エクスペリエンスを実現するための堅牢な一連のツールが提供されています。

<br>

### <a name="keeping-holograms-in-place---coordinate-systems"></a>[ホログラムの配置 - (座標系)](coordinate-systems.md)
基本的に、Mixed Reality アプリは、ホログラムをユーザーの世界に配置し、実際のオブジェクトと同様に見えたり聞こえたりするようにします。 これには、物理的な部屋であれ、作成した仮想領域であれ、ユーザーにとって意味のある世界の特定の位置にこれらのホログラムを正確に配置することが関係します。

<br>

### <a name="making-holographic-objects-feel-real---spatial-mapping"></a>[ホログラフィック オブジェクトを現実的なものにする - (空間マッピング)](spatial-mapping.md)
空間マッピングにより、オブジェクトを実際のサーフェスの上に配置できるようになります。 これは、オブジェクトをユーザーの世界に固定し、現実世界の奥行きの手掛かりを利用するのに役立ちます。

<br>


---

<br>

![操作の設計の要素](images/MRTK_BoundingBox_Main.png)

## <a name="interaction-design-factors-to-consider"></a>考慮する必要がある操作の設計の要素


### <a name="choose-an-interaction-model-for-your-customer"></a>[顧客の操作モデルを選択する](interaction-fundamentals.md)
シンプルで本能的な操作の理念は、Mixed Reality プラットフォーム全体に織り込まれています。 アプリケーションのデザイナーや開発者が顧客に簡単で直感的な操作を提供できるように、3 つの手順を使用しています。

<br>

### <a name="hands-and-motion-controllers"></a>[手とモーション コントローラー](hands-and-tools.md)
ユーザーは、現実世界のオブジェクトの場合と同様に、片手または両手で直接ホログラムに触れて操作できます。 また、モーション コントローラーを使用すると、広範囲にわたる正確な操作を提供することにより、ユーザーの身体能力を拡張できます。

<br>

### <a name="directly-commanding-objects-with-voice-input"></a>[音声入力でオブジェクトに直接コマンドを実行する](voice-input.md)
音声は、HoloLens の主な入力形式の 1 つです。 音声を使うと、ジェスチャを使用せずに、ホログラムに直接コマンドを実行できます。 音声入力は、意図を伝える自然な方法として使用できます。

<br>

### <a name="leveraging-the-users-eye-gaze"></a>[ユーザーの目の視線入力を利用する](eye-tracking.md)
HoloLens 2 を使用すると、開発者はユーザーが見ているものについての情報を使用できるので、ホログラフィック エクスペリエンスにおけるコンテキストと人間の理解が大きく進みます。

<br>

### <a name="color-light-and-materials"></a>[色、ライト、マテリアル](color,-light-and-materials.md)
Mixed Reality のコンテンツの設計では、エクスペリエンスで使用される各ビジュアル資産の色、ライト、マテリアルを慎重に検討する必要があります。

<br>

### <a name="suggesting-the-scale-of-an-object"></a>[オブジェクトのスケールを示す](scale.md)
ホログラフィック形式で現実的に見えるようにコンテンツを表示する鍵は、現実世界の視覚的な特徴に可能な限り近付けることです。 これは、オブジェクトがどこにあるか、どのくらいの大きさか、何でできているのかを (現実世界で) 理解するのに役立つ視覚的な手掛かりを、できる限り多く組み込むことを意味します。

<br>

### <a name="clear-and-readable-typography"></a>[明確で読みやすい文字体裁](typography.md)
2D 画面の文字体裁と同じように、明確で読みやすくすることを目指します。 Mixed Reality の 3 次元の側面により、テキストと全体的なユーザー エクスペリエンスをいっそう優れたものにする機会があります。

<br>

### <a name="ux-elements-for-the-mixed-reality"></a>[複合現実のための UX 要素](app-patterns-landingpage.md)
Mixed Reality での空間相互作用と UI の構成要素について説明します。
<br>


---

## <a name="choose-a-prototyping-option"></a>プロトタイプ作成のオプションを選択する  

:::row:::   
    :::column:::    
       [![Unity について学習する](images/Final_unity_logo.png)](https://learn.unity.com/)<br>
        **[Unity について学習する](https://learn.unity.com/)**<br>
        Unity で対話型エクスペリエンスを作成する方法について学習します。 最初から最後まで、実践によって学習できます。
    :::column-end:::    
    :::column:::    
        [![Mixed Reality ツールキット (MRTK)](images/Final_mrtk-small_logo.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[Mixed Reality ツールキット (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**<br>  
        空間操作と UI 構成ブロックを使用すると、Unity での Mixed Reality の設計と開発をすぐに始めることができます。   
    :::column-end:::
    :::column:::    
        [![Mixed Reality Design Labs](images/Final_mrdl_logo.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[Mixed Reality Design Labs](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**<br>  
        MRTK の構成要素を使用して美しい Mixed Reality エクスペリエンスを作成する方法を示すサンプル アプリを入手できます。
    :::column-end:::        
    :::column:::    
        [![Microsoft Maquette](images/Final_maquette_logo.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        VR 向けの設計。 Microsoft Maquette を使用すると、空間のプロトタイプ作成をすばやく、簡単、かつイマーシブに実行できます。 
    :::column-end:::    
:::row-end:::

<br>

---



## <a name="what-would-you-like-to-do-next"></a>次に行うこと

:::row:::
    :::column:::
       [![基本を理解する](images/icon-lightbulb.png)](index.md#understand-the-basics)<br>
        **[基本を理解する](index.md#understand-the-basics)**<br>
        Mixed Reality が何によって定義され、どのように使用されているかについて理解を深めます。
    :::column-end:::
    :::column:::
        [![イベントに参加する](images/icon-calendar.jpg)](sf-academy-events.md)<br>
         **[イベントに参加する](sf-academy-events.md)**<br>
        最初の HoloLens 2 アプリケーションを作成するには、ハードウェアを参照し、ハンズオン チュートリアルを入手してください。
    :::column-end:::
    :::column:::
        [![ツールのインストール](images/icon-design.jpg)](install-the-tools.md)<br>
         **[ツールのインストール](install-the-tools.md)**<br>
        インストール チェックリストを使用して、HoloLens や Mixed Reality 用のアプリを構築するのに必要なツールを取得します。
    :::column-end:::
    :::column:::
        [![開発を始める](images/icon-developer.jpg)](development.md)<br>
        **[開発を始める](development.md)**<br>
        スキル レベル、ワーク スタイル、プラットフォームへの関心に基づいて、開発パスを選択します。
    :::column-end:::
:::row-end:::


<br>

<br>


