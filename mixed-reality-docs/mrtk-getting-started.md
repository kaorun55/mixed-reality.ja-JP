---
title: MRTK バージョン 2 の概要
description: 新しい開発者 MRTK を活用することに関心が向け
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality、テスト、Mixed Reality Toolkit、MRTK バージョン 2、MRTK、ツール、SDK、HoloLens、HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750370"
---
# <a name="getting-started-with-mrtk-v2"></a>MRTK v2 の概要

## <a name="mrtk-getting-started-guide"></a>MRTK ファースト ステップ ガイド
参照してください、 [MRTK ファースト ステップ ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)MRTK V2 の概要についてはします。

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Mixed Reality ツールキット (MRTK) とは何ですか。
MRTK は、HoloLens はリリース当初とでは、今せずに作成した開発者コミュニティの困難な作業はできないためにきました驚くようなオープン ソースのツールキットです。 過去 3 年の間、開発者コミュニティのフィードバックに応えし、する最大の懸念事項を考慮に入れて MRTK v2 を作成しました。  

Unity を使った MRTK v2 には、複合現実のアプリケーション用のオープン ソース クロス プラットフォーム開発キットです。  MRTK バージョン 2 の目的は、Microsoft HoloLens、Windows Mixed Reality 没入型 (VR) ヘッドセットと OpenVR プラットフォームを対象とするアプリケーションの開発を促進します。 プロジェクトの目的は、複合現実のアプリケーションを作成しすべての拡大に伴い、コミュニティに貢献するエントリに対する障壁を削減です。 


参照してください、 [MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)詳細。

## <a name="feature-areas"></a>機能領域

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="入力システム" width="105"> 入力システム 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="追跡 (HoloLens 2) を渡す" width="105"> 追跡 (HoloLens 2) を渡す
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="視線 (HoloLens 2)" width="105">
    視線 (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="音声コマンドの実行" width="105"> 音声コマンドの実行
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="視線 + の選択 (HoloLens (第 1 世代))" width="105">
    視線 + の選択 (HoloLens (第 1 世代))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> Teleportation
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
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="コント ローラーの視覚化" width="105"> コント ローラーの視覚化
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

## <a name="ui-and-interaction-building-blocks"></a>UI と相互作用の構築ブロック

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Button" width="250"><br>
    **ボタン**<br>
    HoloLens 2 の関節手の形を含む、さまざまな入力方式をサポートするボタン コントロール <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="境界ボックス" width="250"><br>
    **境界ボックス**<br>
    3 次元空間でオブジェクトを操作するための標準の UI <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="操作ハンドラー" width="250"><br>
    **操作ハンドラー**<br>
    1 つまたは 2 つの手を持つオブジェクトを操作するためのスクリプト <a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="スレート" width="250"><br>
    **スレート** <br>
    スタイルの 2D 平面関節手入力でスクロールをサポートします。 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="システム キーボード" width="250"><br>
    **システム キーボード**<br>
    Unity でシステム キーボードを使用するサンプル スクリプト <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="対話型" width="250"><br>
     **対話型** <br>
     Visual state とテーマのサポートと対話型のオブジェクトを行うためのスクリプト <a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="ソルバー" width="250"><br>
    **ソルバー** <br>
    さまざまなオブジェクトの配置動作 tag-along、本文ロック、定数のビュー サイズおよび surface 磁力など <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="オブジェクトのコレクション" width="250"><br>
    **オブジェクトのコレクション**<br>
    3 次元の図形内のオブジェクトの配列を配置用のスクリプト <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="ヒント" width="250">  <br>
    **ツール ヒント**<br>
    注釈 UI アニメーション コント ローラーやオブジェクトのラベル付けに使用できる柔軟なアンカー/ピボット システム <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="アプリ バー" width="250"><br>
    **アプリ バー**<br>
    手動ライセンス認証の境界ボックスの UI <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="ポインター" width="250"><br>
    **ポインター**<br>
    ポインターのさまざまな種類について説明します <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="指の視覚化" width="250"><br>
     **指の視覚化**<br>
     指を直接やり取りする信頼度を向上させる visual アフォー ダンス <a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="スライダー" width="250"><br>
    **スライダー**<br>
    スライダー UI を調整するための操作を追跡するサポートの直接手を値します。 <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 標準シェーダー" width="250"><br>
    **MRTK 標準シェーダー**<br>
    MRTK の標準的なシェーダーがパフォーマンスのさまざまな Fluent デザインの要素をサポートしています <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="ハンド共同 Chaser" width="250"><br>
     **ハンド共同 Chaser**<br>
     ソルバーを使用して手ジョイントにオブジェクトをアタッチする方法を示します <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="視線:ターゲットの選択" width="250"><br>
    **視線:ターゲットの選択**<br>
    目、音声と手を迅速かつ簡単に、シーンの間でホログラムを選択します。 入力を結合します。 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="視線:ナビゲーション" width="250"><br>
    **視線:ナビゲーション**<br>
    自動スクロールのテキストまたはスムーズで検索する内容に基づくフォーカスのあるコンテンツを拡大する方法について説明します <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="視線:ヒート マップ" width="250"><br>
    **視線:ヒート マップ**<br>
    ログ記録の例については、読み込みとどのようなユーザーの視覚化が探してで、アプリで <a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>MRTK v2 の最小要件
* Unity 2018.3.x
* Microsoft Visual Studio 2017 またはそれ以降
* Windows SDK 18362+ 
* Windows 10 1803 以降

## <a name="new-with-mrtk-v2"></a>新しい MRTK v2
これらのプラットフォーム ツールに対するマイクロソフトのコミットメントを強調します。  実際には、セットアップ experience (OOBE) や Mixed Reality Learning アプリケーションなど、受信トレイ エクスペリエンスを開発する MRTK バージョン 2 を利用します。  最初は、プラットフォーム上で開発する最善の方法を考えているためです MRTK を通じて公開されている新しい HoloLens 2 機能を確認することも期待できます。 

### <a name="modular"></a>モジュール
ツールキットのすべてのビットをプロジェクトを考慮する必要はありませんようにして、モジュール方式で作成しましたがあります。  これを実際には、いくつかの利点があります。  プロジェクトのサイズを小さく維持だけでなく管理しやすくなります。  スクリプト可能なオブジェクトで構築されていますので、インターフェイス駆動ことも、その他のサービス、システム、およびプラットフォームをサポートするために、独自に含まれているコンポーネントを交換するため。


### <a name="cross-platform"></a>クロスプラットフォーム
その他のプラットフォームと言えば、クロス プラットフォーム サポートしています。  すべて 1 つのプラットフォームがサポートしているわけでは中、に他のプラットフォーム、ビルド ターゲットを切り替えたときに中断されます toolkit のことを確認されました。  堅牢性とモジュールの設計による拡張機能を ARCore、ARKit、OpenVR など、複数のプラットフォームをサポートできる適切なパスを設定します。


### <a name="performant"></a>パフォーマンスの高い
モバイル プラットフォームを使用 20050607 がパフォーマンスに注意してください。  これは非常に重要なツールが働きますしようとしていないことを確認したいです。


## <a name="see-also"></a>関連項目
* [MRTK ファースト ステップ ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK ドキュメント ホーム](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [ツールのインストール](install-the-tools.md)
* [HTK/MRTK から MRTK バージョン 2 への移植](mrtk-porting-guide.md)
