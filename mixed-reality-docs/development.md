---
layout: LandingPage
title: ツールとアーキテクチャについて学習する
description: HoloLens とイマーシブ ヘッドセットの Mixed Reality 開発者向け説明書です。
author: grbury
ms.author: grbury
ms.date: 08/27/2019
ms.topic: overview
ms.localizationpriority: high
keywords: Mixed Reality, 開発する, 開発, HoloLens, Unity, DirectX
ms.openlocfilehash: 7b1a67f05941fc862ad3f36834efe071b0d1c57b
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334253"
---
# <a name="learn-the-tools-and-architecture"></a>ツールとアーキテクチャについて学習する

![抽象的な 3D の球](images/07_Development.png)

## <a name="expand-your-design-processcase-study-expanding-the-design-process-for-mixed-realitymd"></a>[デザイン プロセスを展開する](case-study-expanding-the-design-process-for-mixed-reality.md)

2016 年に Microsoft が待ち望む開発者のために HoloLens を発表したとき、チームは既に Microsoft の内外のスタジオと協力してデバイスの起動エクスペリエンスを構築していました。 これらのチームは、Mixed Reality の設計の新しいフィールドにおける機会と課題の両方を明らかにして学習しました。 [詳細を見る](case-study-expanding-the-design-process-for-mixed-reality.md)


<br>

---


## <a name="what-technology-path-are-you-interested-in"></a>どのようなテクノロジ パスに興味がありますか? 


:::row:::   
    :::column:::    
       [![Unity](images/unity_logo.png)](development.md#unity)<br>
        **[Unity](development.md#unity)**<br>   
        Mixed Reality アプリを構築する最速のパスは、Unity を使用するものです。 
    :::column-end:::    
    :::column:::    
        [![Unreal](images/Unreal_logo.png)](development.md#unreal)<br>
         **[Unreal](development.md#unreal)**<br>    
        HoloLens 2 の実稼働可能サポートも、Unreal Engine 4.23 に含まれる予定です。    
    :::column-end:::
    :::column:::    
        [![WebVR](images/WebVR_logo.png)](development.md#webvr)<br>
        **[WebVR](development.md#webvr)**<br>
        WebVR は、ブラウザーで VR を体験できるようにするオープン仕様です。 
    :::column-end:::        
    :::column:::    
        [![Native](images/VisualStudio-small_logo.png)](development.md#native)<br>
        **[Native](development.md#native)**<br> 
        Windows Mixed Reality API に直接コーディングすることで、Mixed Reality アプリを作成します。 
    :::column-end:::    
:::row-end:::

<br>

---

## <a name="unity"></a>Unity


### <a name="unity-development-overviewunity-development-overviewmd"></a>[Unity 開発の概要](unity-development-overview.md)
時間を取って、Unity のチュートリアルをご覧になることをお勧めします。 資産が必要な場合、Unity には包括的な資産ストアがあります。 

<br>

### <a name="microsofts-mixed-reality-toolkit-mrtk-for-unitymrtk-getting-startedmd"></a>[Microsoft の Unity 用 Mixed Reality ツールキット (MRTK)](mrtk-getting-started.md)
Unity での MRTK v2 は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。 MRTK バージョン 2 は、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。

<br>

### <a name="open-source-sample-apps-and-step-by-step-tutorialstutorialsmd"></a>[オープンソースのサンプル アプリとステップバイステップ チュートリアル](tutorials.md)
HoloLens 2 のチュートリアルは、開発者が Mixed Reality アプリケーションの開発に関する手法とベスト プラクティスの両方を学習できるように設計されています。 チュートリアルは、Mixed Reality ツールキット 2.0 (MRTK 2.0) が基になっています。

<br>

### <a name="hand-interaction-examples-scene-mrtk-for-unityhttpsmicrosoftgithubiomixedrealitytoolkit-unitydocumentationgettingstartedwiththemrtkhtmlopen-and-run-the-handinteractionexamples-scene-in-editor"></a>[Unity 用の手による操作のサンプル シーン (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#open-and-run-the-handinteractionexamples-scene-in-editor)
HandInteractionExamples.unity のサンプル シーンには、多関節ハンド入力が強調されているさまざまな種類の操作と UI コントロールが含まれています。
>[!NOTE]
>MRTK Foundation パッケージとサンプル Unity パッケージのインストールが必要です。

### <a name="eye-tracking-examples-mrtk-for-unityhttpsmicrosoftgithubiomixedrealitytoolkit-unitydocumentationeyetrackingeyetracking_examplesoverviewhtml"></a>[Unity 用の視線追跡のサンプル (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_ExamplesOverview.html)
このページでは、提供されている MRTK の視線追跡サンプルを基に構築することにより、MRTK での視線追跡をすばやく開始する方法について説明します。
>[!NOTE]
>MRTK Foundation パッケージとサンプル Unity パッケージのインストールが必要です。

<br>

---

## <a name="unreal"></a>Unreal

### <a name="unreal-development-overviewunreal-development-overviewmd"></a>[Unreal 開発の概要](unreal-development-overview.md)
Unreal を使用した Mixed Reality アプリの構築方法について説明します。

<br>

---

## <a name="webvr"></a>WebVR    

### <a name="babylon-development-overviewhttpsdocbabylonjscom"></a>[Babylon 開発の概要](https://doc.babylonjs.com/)  
Babylon を使用した Mixed Reality アプリの構築方法について説明します。 時間を取って、Babylon のチュートリアルをご覧になることをお勧めします。

<br>

---

## <a name="native"></a>ネイティブ


### <a name="native-development-overviewdirectx-development-overviewmd"></a>[ネイティブ開発の概要](directx-development-overview.md)
ネイティブな Mixed Reality アプリを構築するための最速のパスです。

<br>

### <a name="directx-uwp-app-templates-for-mixed-realityhttpsmarketplacevisualstudiocomitemsitemnamewindowsmixedrealityteamwindowsmixedrealityapptemplatesvsix"></a>[Mixed Reality 用 DirectX UWP アプリ テンプレート](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)
DirectX を使用して Mixed Reality アプリを記述するのに必要なものすべてが含まれます。

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
        [![作成者になる](images/icon-design.jpg)](design.md)<br>
         **[作成者になる](design.md)**<br>
        設計とプロトタイプ作成を開始するために必要な基本的な概念について説明します。
    :::column-end:::
    :::column:::
        [![ツールのインストール](images/icon-developer.jpg)](install-the-tools.md)<br>
         **[ツールのインストール](install-the-tools.md)**<br>
        インストール チェックリストを使用して、HoloLens や Mixed Reality 用のアプリを構築するのに必要なツールを取得します。
    :::column-end:::
    :::column:::
        [![イベントに参加する](images/icon-calendar.jpg)](sf-academy-events.md)<br>
         **[イベントに参加する](sf-academy-events.md)**<br>
        最初の HoloLens 2 アプリケーションを作成するには、ハードウェアを参照し、ハンズオン チュートリアルを入手してください。
    :::column-end:::
:::row-end:::


<br>

<br>
