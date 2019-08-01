---
layout: LandingPage
title: 設計
description: このガイダンスは、ホログラフィック デバイス (HoloLens など) やイマーシブ デバイス (Acer および HP Windows Mixed Reality ヘッドセットなど) にわたって作業しているマイクロソフトのデザイナー、開発者、プログラム マネージャー、研究者によって作成されています。 そのため、この作業を 'Windows ヘッドマウント ディスプレイ向けの設計方法' のための一連のトピックと見なしてください。
author: rwinj
ms.author: randyw
ms.date: 03/21/2018
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality、設計、操作、スタイル、色、アプリ パターン、コントロール、サンプル アプリ、Mixed Reality ツールキット、MRTK
ms.openlocfilehash: 6601f4c2dd75e6e555dd79bc92abcccc15eb1ab4
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326189"
---
# <a name="design-for-mixed-reality"></a>Mixed Reality 向けの設計

![Mixed Reality 向けの設計](images/Bicycle-Leschi10.gif)


このガイダンスは、ホログラフィック デバイス (HoloLens など) やイマーシブ デバイス (Acer および HP Windows Mixed Reality ヘッドセットなど) にわたって作業しているマイクロソフトのデザイナー、開発者、プログラム マネージャー、研究者によって作成されています。 そのため、この作業を Windows ヘッドマウント ディスプレイ向けの設計方法のための一連のトピックと見なしてください。


## <a name="article-categories"></a>記事のカテゴリ

<ul class="panelContent cardsF">
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/GetStartedIcon.png" alt="Getting started icon">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>設計の概要</h3>
                        <p>
                            <a href="mixed-reality.md">Mixed Reality とは</a>
                        </p>
                        <p>
                            <a href="about-this-design-guidance.md">このガイダンスについて</a>
                        </p>
                        <p>
                            <a href="case-study-my-first-year-on-the-hololens-design-team.md">設計チームでの最初の年</a>
                        </p>
                        <p>
                            <a href="case-study-expanding-the-design-process-for-mixed-reality.md">Mixed Reality 向けの設計プロセスの拡張</a>
                        </p>
                        <p>
                            <a href="case-study-the-pursuit-of-more-personal-computing.md">よりパーソナルなコンピューティングの追求</a>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/Interaction_Icon_120x130.png" alt="MR design system and tools icon">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>MR 設計システムとツール</h3>
                        <p>
                            <a href="comfort.md">快適性</a>
                        </p>
            <p>
                            <a href="interaction-fundamentals.md">本能的な操作</a>
                        </p>
                        <p>
                            <a href="hands-and-tools.md">手とモーション コントローラー</a>
                        </p>
                        <p>
                            <a href="hands-free.md">ハンズフリー</a>
                        </p>
                         <p>
                            <a href="gaze-and-commit.md">頭の視線入力とコミット</a>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/Style_Icon_120x130.png" alt="Style icon">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>スタイル</h3>
                        <p>
                            <a href="color,-light-and-materials.md">色、ライト、素材</a>
                        </p>
                         <p>
                            <a href="spatial-sound-design.md">立体音響の設計</a>
                        </p>
                        <p>
                            <a href="typography.md">文字体裁</a>
                        </p>
                        <p>
                            <a href="scale.md">スケール</a>
                        </p>                      
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/App_patterns_Icon_120x130.png" alt="App patterns icon">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>アプリのパターン</h3>
                        <p>
                            <a href="types-of-mixed-reality-apps.md">Mixed Reality アプリの種類</a>
                        </p>
                        <p>
                            <a href="room-scan-visualization.md">部屋のスキャンの可視化</a>
                        </p>
                        <p>
                            <a href="cursors.md">カーソル</a>
                        </p>
                        <p>
                            <a href="billboarding-and-tag-along.md">Billboard と Tag-along</a>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/Controls_Icon_120x130.png" alt="Controls icon">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>コントロール</h3>
                        <p>
                            <a href="text-in-unity.md">Unity のテキスト</a>
                        </p>
                        <p>
                            <a href="interactable-object.md">対話可能なオブジェクト</a>
                        </p>
                        <p>
                            <a href="object-collection.md">オブジェクト コレクション</a>
                        </p>
                        <p>
                            <a href="progress.md">進行状況の表示</a>
                        </p>
                        <p>
                            <a href="app-bar-and-bounding-box.md">境界ボックスとアプリ バー</a>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </li>    
</ul>


## <a name="sample-apps"></a>サンプル アプリ

マイクロソフトのチームが設計および作成したサンプルからすばらしいエクスペリエンスを構築してください。

<br>
<ul id="cardtypes-W" class="cardsW panelContent" style="display: flex; margin-top: 0px;">
    <li>
        <a href="periodic-table-of-the-elements.md" title="要素の定期的なテーブル" data-linktype="absolute-path">
            <div class="cardSize">
                <div class="cardPadding">
                    <div class="card">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img src="images/periodictableofelementsapp-tile.jpg" alt="Periodic Table of the Elements< icon">
                            </div>
                        </div>
                        <div class="cardText">
                            <h3>要素の定期的なテーブル</h3>
                            <p>オブジェクト コレクションを使用して、さまざまな表面の種類を持つ 3D 空間内のオブジェクトの配列をレイアウトする方法を説明します。</p>
                        </div>
                    </div>
                </div>
            </div>
        </a>        
    </li>
    <li>
        <a href="lunar-module.md" title="月着陸船" data-linktype="absolute-path">
            <div class="cardSize">
                <div class="cardPadding">
                    <div class="card">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img src="images/lunar-module-tile.png" alt="Lunar Module icon">
                            </div>
                        </div>
                        <div class="cardText">
                            <h3>月着陸船</h3>
                            <p>HoloLens ベースのジェスチャを両手の追跡と Xbox コントローラーの入力で拡張する方法を説明します。 input.</p>
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li>
        <a href="galaxy-explorer.md" title="Galaxy Explorer" data-linktype="absolute-path">
            <div class="cardSize">
                <div class="cardPadding">
                    <div class="card">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img src="images/galaxyexplorer-tile.jpg" alt="Galaxy Explorer icon">
                            </div>
                        </div>
                        <div class="cardText">
                            <h3>Galaxy Explorer</h3>
                            <p>Galaxy Explorer プロジェクトの準備が完了しました。 これまではコミュニティとアイデアを共有し、アプリケーションを選択し、チームによるその構築を見てきましたが、ソース コードを取得できるようになりました。</p>
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
</ul>



## <a name="design-tools"></a>デザイン ツール


<ul id="cardtypes-D" class="cardsD panelContent" style="display: flex; margin-top: 0px;">
    <li>
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/README.html#ui-and-interaction-building-blocks" title="Mixed Reality ツールキット - Unity" data-linktype="absolute-path">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/MRTKandUnity.png" alt="Mixed Reality Toolkit - Unity">
                        </div>
                    </div>                    
            <div class="cardText">
                        <h3>Mixed Reality ツールキット - Unity</h3>
                        <p> </p>
                    </div>
                </div>
            </div>
        </div>
      </a>  
    </li>
    <li>
    <a href="https://github.com/Microsoft/MixedRealityToolkit" title="Mixed Reality ツールキット" data-linktype="absolute-path">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/MRTK.png" alt="Mixed Reality Toolkit">
                        </div>
                    </div>                    
            <div class="cardText">
                        <h3>Mixed Reality ツールキット</h3>
                        <p> </p>
                    </div>
                </div>
            </div>
        </div>
      </a>  
    </li>       
            <li>
    <a href="https://www.simplygon.com" title="Simplygon" data-linktype="absolute-path">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/Simplygon.png" alt="Simplygon">
                        </div>
                    </div>                    
            <div class="cardText">
                        <h3>Simplygon</h3>
                        <p> </p>
                    </div>
                </div>
            </div>
        </div>
      </a>  
    </li>
</ul>


## <a name="general-design-resources"></a>一般的な設計リソース

<ul id="cardtypes-D" class="cardsD panelContent" style="display: flex; margin-top: 0px;">
    <li>
    <a href="http://fluent.microsoft.com" title="Fluent Design System" data-linktype="absolute-path">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/Fluent.png" alt="Fluent Design System">
                        </div>
                    </div>                    
            <div class="cardText">
                        <h3>Fluent Design System</h3>
                        <p> </p>
                    </div>
                </div>
            </div>
        </div>
      </a>  
    </li>
    <li>
    <a href="https://www.microsoft.com/design/inclusive" title="マイクロソフトでの包括性を備えた設計" data-linktype="absolute-path">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/Inclusive.png" alt="Inclusive design at Microsoft">
                        </div>
                    </div>                    
            <div class="cardText">
                        <h3>マイクロソフトでの包括性を備えた設計</h3>
                        <p> </p>
                    </div>
                </div>
            </div>
        </div>
      </a>  
    </li>   
        <li>
    <a href="https://developer.microsoft.com/windows/apps/design" title="ユニバーサル Windows プラットフォーム (UWP) アプリケーションの設計" data-linktype="absolute-path">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/UWP.png" alt="Universal Windows Platform (UWP) app design">
                        </div>
                    </div>                    
            <div class="cardText">
                        <h3>ユニバーサル Windows プラットフォーム (UWP) アプリケーションの設計</h3>
                        <p> </p>
                    </div>
                </div>
            </div>
        </div>
      </a>  
    </li>   
</ul>
