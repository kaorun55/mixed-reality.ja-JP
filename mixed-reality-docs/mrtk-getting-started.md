---
title: MRTK バージョン2の概要
description: MRTK の活用に関心がある新しい開発者向け
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality、test、Mixed Reality Toolkit、MRTK バージョン2、MRTK、tools、SDK、HoloLens、HoloLens 2
ms.openlocfilehash: c785498e1533b2117249d3b21952ff56190126c0
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2019
ms.locfileid: "68937085"
---
# <a name="getting-started-with-mrtk-v2"></a>MRTK v2 の概要

## <a name="mrtk-getting-started-guide"></a>MRTK はじめにガイド
MRTK V2 の概要については、「 [mrtk ファーストステップガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)」を参照してください。

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit (MRTK) とは
MRTK は、HoloLens が最初にリリースされた後に行われていたすばらしいオープンソースのツールキットであり、現在のところ、開発者コミュニティが提供されているので、このツールキットを使用することはできません。 過去3年間、microsoft は開発者コミュニティのフィードバックを受け、最大の関心事を考慮するために MRTK v2 を構築しました。  

Unity を使用した MRTK v2 は、mixed reality アプリケーション用のオープンソースのクロスプラットフォーム開発キットです。  MRTK バージョン2は、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームを対象とするアプリケーションの開発を促進することを目的としています。 このプロジェクトは、Mixed Reality アプリケーション作成への参入の障壁を減らし、私たち全員の成長とともにコミュニティに貢献することを目的としています。 


詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)を参照してください。

## <a name="feature-areas"></a>機能領域

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="入力システム" width="105"> 入力システム 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="ハンドトラッキング (HoloLens 2)" width="105"> ハンドトラッキング (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="視線追跡 (HoloLens 2)" width="105">
    視線追跡 (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="音声によるコマンド" width="105"> 音声によるコマンド
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="宝石 + 選択 (HoloLens (第1世代))" width="105">
    宝石 + 選択 (HoloLens (第1世代))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="受付" width="105"> 受付
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI コントロール" width="105"> UI コントロール
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="ソルバーと相互作用" width="105"> ソルバーと相互作用
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="コントローラーの視覚化" width="105"> コントローラーの視覚化
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="空間の理解" width="105"> 空間の理解
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="診断ツール" width="105"> 診断ツール
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK 標準シェーダー" width="105"> MRTK 標準シェーダー
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>UI と相互作用の構成要素

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="ボタン" width="250"><br>
    **Button**<br>
    HoloLens 2 の手を含むさまざまな入力方法をサポートするボタンコントロール<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="境界ボックス" width="250"><br>
    **境界ボックス**<br>
    3D 空間内のオブジェクトを操作するための標準 UI<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="操作ハンドラー" width="250"><br>
    **操作ハンドラー**<br>
    1人または2人の手でオブジェクトを操作するためのスクリプト<a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="翻訳" width="250"><br>
    **翻訳** <br>
    入力によるスクロールをサポートする2D スタイルプレーン<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="システムキーボード" width="250"><br>
    **システムキーボード**<br>
    Unity でシステムキーボードを使用するサンプルスクリプト<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="対話型" width="250"><br>
     **対話型** <br>
     視覚的な状態とテーマのサポートを使用してオブジェクトを対話型するためのスクリプト<a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title=":" width="250"><br>
    **:** <br>
    タグに沿って、本文ロック、定数ビューサイズ、表面吸着などのさまざまなオブジェクトの配置動作<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="オブジェクトコレクション" width="250"><br>
    **オブジェクトコレクション**<br>
    3次元図形内のオブジェクトの配列をレイアウトするためのスクリプト<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="ヒント" width="250">  <br>
    **ボタン**<br>
    モーションコントローラーとオブジェクトのラベル付けに使用できる柔軟なアンカー/ピボットシステムを使用した注釈 UI<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="アプリバー" width="250"><br>
    **アプリバー**<br>
    境界ボックスの手動アクティブ化の UI<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="ポインター" width="250"><br>
    **ポインター**<br>
    さまざまな種類のポインターについて<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="指先の視覚化" width="250"><br>
     **指先の視覚化**<br>
     指先での Visual affordance による直接的な相互作用の信頼性の向上<a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="スライダー" width="250"><br>
    **Slider**<br>
    ダイレクトハンドトラッキングの相互作用をサポートする値を調整するためのスライダー UI<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 標準シェーダー" width="250"><br>
    **MRTK 標準シェーダー**<br>
    MRTK の標準シェーダーでは、パフォーマンスを備えたさまざまな Fluent デザイン要素がサポートされています。<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="手ジョイント Chaser" width="250"><br>
     **手ジョイント Chaser**<br>
     ソルバーを使用してオブジェクトを手の継手に接続する方法を示します。<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="目の追跡:ターゲットの選択" width="250"><br>
    **目の追跡:ターゲットの選択**<br>
    視点、音声、手入力を組み合わせてシーン全体のホログラムをすばやく簡単に選択する<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="目の追跡:ナビゲーション" width="250"><br>
    **目の追跡:領域**<br>
    表示内容に基づいて、テキストを自動的にスクロールするか、フォーカスされているコンテンツにズームする方法について説明します。<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="目の追跡:ヒートマップ" width="250"><br>
    **目の追跡:ヒートマップ**<br>
    アプリに表示されているユーザーのログ記録、読み込み、視覚化の例<a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>MRTK v2 の最小要件
* Unity 2018.4
* Microsoft Visual Studio 2017 以降
* Windows SDK 18362 + 
* Windows 10 1803 以降

## <a name="new-with-mrtk-v2"></a>MRTK v2 の新バージョン
これらのプラットフォームツールに対するコミットメントを重視したいと考えています。  実際、MRTK バージョン2を利用して、setup experience (OOBE) や Mixed Reality Learning アプリケーションなどの受信トレイエクスペリエンスを開発しました。  また、プラットフォームで開発するのに最適な方法であると考えられるため、新しい HoloLens 2 機能が MRTK を通じて最初に公開されることが予想されます。 

### <a name="modular"></a>方式
モジュール型の方法でビルドしたため、ツールキットをすべてプロジェクトに取り込む必要がありません。  これには、実際にいくつかの利点があります。  これにより、プロジェクトのサイズが小さくなり、管理も容易になります。  それに加えて、スクリプト可能なオブジェクトを使用して構築され、インターフェイスによって駆動されるため、独自のに含まれているコンポーネントを置き換えることで、他のサービス、システム、およびプラットフォームをサポートすることもできます。


### <a name="cross-platform"></a>クロスプラットフォーム
他のプラットフォームの場合は、クロスプラットフォームのサポートがあります。  これは、すべての単一プラットフォームが既定でサポートされているわけではありませんが、ビルドターゲットを他のプラットフォームに切り替えると、どのツールキットコードも破損しないようにしました。  モジュール型の設計による堅牢性と拡張性により、ARCore、Arcore、OpenVR などの複数のプラットフォームをサポートするための優れたパスを設定できます。


### <a name="performant"></a>パフォーマンス
モバイルプラットフォームを使用すると、パフォーマンスを考慮して構築されています。  これは非常に重要であり、ツールがお客様に対して機能しないようにする必要がありました。


## <a name="see-also"></a>関連項目
* [MRTK ファーストステップガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK ドキュメントホーム](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [ツールのインストール](install-the-tools.md)
* [HTK/MRTK から MRTK バージョン2への移植](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
