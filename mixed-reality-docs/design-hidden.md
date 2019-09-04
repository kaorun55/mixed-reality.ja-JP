---
layout: LandingPage
title: 設計とプロトタイプ作成を開始する
description: 何かを作成する準備ができました。 設計とプロトタイプ作成を開始するために必要な基本的な概念について説明します。
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 検出, 配布, インデックス, ランディング ページ, 設計, 開発, チュートリアル, サンプル アプリ, 基本事項, ケース スタディ, リソース, HoloLens の使い方, オープン ソース プロジェクト
ms.openlocfilehash: 3efb411425d18a8f50a209b69b00bfa038d594f1
ms.sourcegitcommit: 183b6248807f600fe7d83daa13a6fe0b0f0dc846
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70148013"
---
# <a name="start-designing-and-prototyping"></a>設計とプロトタイプ作成を開始する


![構成要素](images/text_in_unity_viewingangle.jpg)

## <a name="what-are-the-core-concepts-of-an-experience"></a>エクスペリエンスの主要な概念は何か

### <a name="keep-the-user-comfortable---comfortcomfortmd"></a>[ユーザーの快適さを維持する (快適さ)](comfort.md)
ヘッド マウント ディスプレイを可能な限り快適なものにするため、デザイナーと開発者は、これらの手掛かりの自然界での動作方法と同じようにコンテンツを作成して提示することが重要です。

<br>

### <a name="consider-how-the-user-sees-the-world---holographic-frameholographic-framemd"></a>[ユーザーには世界がどのように見えるかを考える - (ホログラフィック フレーム)](holographic-frame.md)
ユーザーは、ヘッドセットによって作成される四角形のビューポートを通して、Mixed Reality の世界を見ることになります。 HoloLens では、この四角形の領域はホログラフィック フレームと呼ばれ、ユーザーは自分の周囲の現実世界に重ねてデジタル コンテンツを見ることができます。

<br>

### <a name="making-holographic-objects-feel-real---spatial-mappingspatial-mappingmd"></a>[ホログラフィック オブジェクトを現実的なものにする - (空間マッピング)](spatial-mapping.md)
空間マッピングにより、オブジェクトを実際のサーフェスの上に配置できるようになります。 これは、オブジェクトをユーザーの世界に固定し、現実世界の奥行きの手掛かりを利用するのに役立ちます。

<br>

### <a name="suggesting-the-scale-of-an-object---scalescalemd"></a>[オブジェクトのスケールを示す - (スケール)](scale.md)
ホログラフィック形式で現実的に見えるようにコンテンツを表示する鍵は、現実世界の視覚的な統計に可能な限り近付けることです。 これは、オブジェクトがどこにあるか、どのくらいの大きさか、何でできているのかを (現実世界で) 理解するのに役立つ視覚的な手掛かりを、できる限り多く組み込むことを意味します。

<br>

### <a name="clear-and-readable-typographytypographymd"></a>[明確で読みやすい文字体裁](typography.md)
2D 画面の文字体裁と同じように、明確で読みやすくすることを目指します。 Mixed Reality の 3 次元の側面により、テキストと全体的なユーザー エクスペリエンスをいっそう優れたものにする機会があります。

<br>

### <a name="color-light-and-materialscolor-light-and-materialsmd"></a>[色、ライト、マテリアル](color,-light-and-materials.md)
Mixed Reality のコンテンツの設計では、エクスペリエンスで使用される各ビジュアル資産の色、ライト、マテリアルを慎重に検討する必要があります。


<br>

---



![操作の設計の要素](images/MRTK_BoundingBox_Main.png)

## <a name="interaction-design-factors-to-consider"></a>考慮する必要がある操作の設計の要素


### <a name="expanding-the-design-process-for-mixed-realitycase-study-expanding-the-design-process-for-mixed-realitymd"></a>[複合現実の設計プロセスを拡張する](case-study-expanding-the-design-process-for-mixed-reality.md)
2016 年に Microsoft が待ち望む開発者のために HoloLens を発表したとき、チームは既に Microsoft の内外のスタジオと協力してデバイスの起動エクスペリエンスを構築していました。 これらのチームは、Mixed Reality の設計の新しいフィールドにおける機会と課題の両方を明らかにして学習しました。

<br>

### <a name="types-of-mixed-reality-appstypes-of-mixed-reality-appsmd"></a>[複合現実アプリの種類](types-of-mixed-reality-apps.md)
Windows Mixed Reality 用アプリを開発する利点の 1 つは、プラットフォームでサポートできるエクスペリエンスの広さです。 完全にイマーシブな仮想環境から、ユーザーの現在の環境に重ねて表示されるちょっとした情報まで、Windows Mixed Reality では、エクスペリエンスを実現するための堅牢な一連のツールが提供されています。

<br>

### <a name="choose-an-interaction-model-for-your-customerinteraction-fundamentalsmd"></a>[顧客の操作モデルを選択する](interaction-fundamentals.md)
シンプルで本能的な操作の理念は、Mixed Reality プラットフォーム全体に織り込まれています。 アプリケーションのデザイナーや開発者が顧客に簡単で直感的な操作を提供できるように、3 つの手順を使用しています。

<br>

### <a name="hands-and-motion-controllershands-and-toolsmd"></a>[手とモーション コントローラー](hands-and-tools.md)
2D 画面の文字体裁と同じように、明確で読みやすくすることを目指します。 Mixed Reality の 3 次元の側面により、テキストと全体的なユーザー エクスペリエンスをいっそう優れたものにする機会があります。

<br>

### <a name="voice-commandingvoice-designmd"></a>[音声コマンド](voice-design.md)
音声コマンドを使用する場合、視線入力は通常、ターゲットを設定するメカニズムとして使用されます。ポインターとして (「選択」)、またはアプリケーションにコマンドを送る (「見て発音する」) 目的で使用します。

<br>

### <a name="leveraging-the-users-eye-gazeeye-trackingmd"></a>[ユーザーの目の視線入力を利用する](eye-tracking.md)
HoloLens 2 を使用すると、開発者はユーザーが見ているものについての情報を使用できるので、ホログラフィック エクスペリエンスにおけるコンテキストと人間の理解が大きく進みます。


<br>


---

## <a name="choose-a-prototyping-option"></a>プロトタイプ作成のオプションを選択する  





:::row:::
    :::column:::
        <img alt="Unity Logo" width="70" height="70" src="images/unity_logo.png">
         <a href="https://learn.unity.com/" target="">Learn Unity</a>
        Learn how to create interactive experiences with Unity
    :::column-end:::
        :::column:::
       <img alt="MRTK Logo" width="70" height="70" src="images/MRTK_Logo_Sq_Text.png">
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="">Mixed Reality ツールキット</a> Mixed Reality ツールキットの空間操作と UI 構成ブロックを使用すると、Unity での Mixed Reality の設計と開発をすぐに始めることができます。
    :::column-end:::
    :::column:::
        <img alt="MRDL Logo" width="70" height="70" src="images/MRDL_Logo_Sq_Text.png">
         <a href="https://github.com/Microsoft/MRDL_Unity_PeriodicTable" target="">Mixed Reality Design Labs</a>
        Mixed Reality Design Lab's sample apps shows how to use MRTK's building blocks to create beautiful mixed reality experiences.
    :::column-end:::
    :::column:::
        <img alt="Maquette Logo" width="70" height="70" src="images/MicrosoftMaquette_logo_glow.png">
         <a href="https://www.maquette.ms/" target="">Microsoft Maquette</a>
        Design for VR. Microsoft Maquette makes spatial prototyping easy, quick, and immersive.
    :::column-end:::
:::row-end:::


<br>

---



## <a name="what-would-you-like-to-do-next"></a>次に行うこと


:::row:::
    :::column:::
       ![基本を理解する](images/icon-lightbulb.jpg)
        ### [Understand the basics](index-hidden.md)
        Get a better understanding of what defines mixed reality and how it’s being used.
    :::column-end:::
    :::column:::
        ![Install the tools](images/icon-design.jpg)
         ### [Install the tools](install-the-tools.md)
        Use the installation checklist to get the tools you need to build applications for Microsoft HoloLens and Windows Mixed Reality.
    :::column-end:::
    :::column:::
        ![Come to an event](images/icon-calendar.jpg)
         ### [Come to an event](sf-academy-events.md)
        See the hardware and get a hands-on tutorial to make your first HoloLens 2 application.
    :::column-end:::
    :::column:::
        ![Start developing](images/icon-developer.jpg)
         ### [Start developing](development-hidden.md)
        Choose a development path based on your skill level, work style. or platform interest.
    :::column-end:::
:::row-end:::



