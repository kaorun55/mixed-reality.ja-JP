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
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="18d12-104">MRTK v2 の概要</span><span class="sxs-lookup"><span data-stu-id="18d12-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="18d12-105">MRTK ファースト ステップ ガイド</span><span class="sxs-lookup"><span data-stu-id="18d12-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="18d12-106">参照してください、 [MRTK ファースト ステップ ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)MRTK V2 の概要についてはします。</span><span class="sxs-lookup"><span data-stu-id="18d12-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="18d12-107">Mixed Reality ツールキット (MRTK) とは何ですか。</span><span class="sxs-lookup"><span data-stu-id="18d12-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="18d12-108">MRTK は、HoloLens はリリース当初とでは、今せずに作成した開発者コミュニティの困難な作業はできないためにきました驚くようなオープン ソースのツールキットです。</span><span class="sxs-lookup"><span data-stu-id="18d12-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="18d12-109">過去 3 年の間、開発者コミュニティのフィードバックに応えし、する最大の懸念事項を考慮に入れて MRTK v2 を作成しました。</span><span class="sxs-lookup"><span data-stu-id="18d12-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="18d12-110">Unity を使った MRTK v2 には、複合現実のアプリケーション用のオープン ソース クロス プラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="18d12-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="18d12-111">MRTK バージョン 2 の目的は、Microsoft HoloLens、Windows Mixed Reality 没入型 (VR) ヘッドセットと OpenVR プラットフォームを対象とするアプリケーションの開発を促進します。</span><span class="sxs-lookup"><span data-stu-id="18d12-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="18d12-112">プロジェクトの目的は、複合現実のアプリケーションを作成しすべての拡大に伴い、コミュニティに貢献するエントリに対する障壁を削減です。</span><span class="sxs-lookup"><span data-stu-id="18d12-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="18d12-113">参照してください、 [MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)詳細。</span><span class="sxs-lookup"><span data-stu-id="18d12-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="18d12-114">機能領域</span><span class="sxs-lookup"><span data-stu-id="18d12-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="入力システム" width="105"> <span data-ttu-id="18d12-116">入力システム</span><span class="sxs-lookup"><span data-stu-id="18d12-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="追跡 (HoloLens 2) を渡す" width="105"> <span data-ttu-id="18d12-118">追跡 (HoloLens 2) を渡す</span><span class="sxs-lookup"><span data-stu-id="18d12-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="視線 (HoloLens 2)" width="105">
    <span data-ttu-id="18d12-120">視線 (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="18d12-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="音声コマンドの実行" width="105"> <span data-ttu-id="18d12-122">音声コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="18d12-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="視線 + の選択 (HoloLens (第 1 世代))" width="105">
    <span data-ttu-id="18d12-124">視線 + の選択 (HoloLens (第 1 世代))</span><span class="sxs-lookup"><span data-stu-id="18d12-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> <span data-ttu-id="18d12-126">Teleportation</span><span class="sxs-lookup"><span data-stu-id="18d12-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI コントロール" width="105"> <span data-ttu-id="18d12-128">UI コントロール</span><span class="sxs-lookup"><span data-stu-id="18d12-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="ソルバーと相互作用" width="105"> <span data-ttu-id="18d12-130">ソルバーと相互作用</span><span class="sxs-lookup"><span data-stu-id="18d12-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="コント ローラーの視覚化" width="105"> <span data-ttu-id="18d12-132">コント ローラーの視覚化</span><span class="sxs-lookup"><span data-stu-id="18d12-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="空間の理解" width="105"> <span data-ttu-id="18d12-134">空間の理解</span><span class="sxs-lookup"><span data-stu-id="18d12-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="診断ツール" width="105"> <span data-ttu-id="18d12-136">診断ツール</span><span class="sxs-lookup"><span data-stu-id="18d12-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK 標準シェーダー" width="105"> <span data-ttu-id="18d12-138">MRTK 標準シェーダー</span><span class="sxs-lookup"><span data-stu-id="18d12-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="18d12-139">UI と相互作用の構築ブロック</span><span class="sxs-lookup"><span data-stu-id="18d12-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Button" width="250"><br>
    <span data-ttu-id="18d12-141">**ボタン**</span><span class="sxs-lookup"><span data-stu-id="18d12-141">**Button**</span></span><br>
    <span data-ttu-id="18d12-142">HoloLens 2 の関節手の形を含む、さまざまな入力方式をサポートするボタン コントロール <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="境界ボックス" width="250"><br>
    <span data-ttu-id="18d12-144">**境界ボックス**</span><span class="sxs-lookup"><span data-stu-id="18d12-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="18d12-145">3 次元空間でオブジェクトを操作するための標準の UI <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="操作ハンドラー" width="250"><br>
    <span data-ttu-id="18d12-147">**操作ハンドラー**</span><span class="sxs-lookup"><span data-stu-id="18d12-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="18d12-148">1 つまたは 2 つの手を持つオブジェクトを操作するためのスクリプト <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="スレート" width="250"><br>
    <span data-ttu-id="18d12-150">**スレート**</span><span class="sxs-lookup"><span data-stu-id="18d12-150">**Slate**</span></span> <br>
    <span data-ttu-id="18d12-151">スタイルの 2D 平面関節手入力でスクロールをサポートします。 <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="システム キーボード" width="250"><br>
    <span data-ttu-id="18d12-153">**システム キーボード**</span><span class="sxs-lookup"><span data-stu-id="18d12-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="18d12-154">Unity でシステム キーボードを使用するサンプル スクリプト <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="対話型" width="250"><br>
     <span data-ttu-id="18d12-156">**対話型**</span><span class="sxs-lookup"><span data-stu-id="18d12-156">**Interactable**</span></span> <br>
     <span data-ttu-id="18d12-157">Visual state とテーマのサポートと対話型のオブジェクトを行うためのスクリプト <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="ソルバー" width="250"><br>
    <span data-ttu-id="18d12-159">**ソルバー**</span><span class="sxs-lookup"><span data-stu-id="18d12-159">**Solver**</span></span> <br>
    <span data-ttu-id="18d12-160">さまざまなオブジェクトの配置動作 tag-along、本文ロック、定数のビュー サイズおよび surface 磁力など <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="オブジェクトのコレクション" width="250"><br>
    <span data-ttu-id="18d12-162">**オブジェクトのコレクション**</span><span class="sxs-lookup"><span data-stu-id="18d12-162">**Object Collection**</span></span><br>
    <span data-ttu-id="18d12-163">3 次元の図形内のオブジェクトの配列を配置用のスクリプト <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="ヒント" width="250">  <br>
    <span data-ttu-id="18d12-165">**ツール ヒント**</span><span class="sxs-lookup"><span data-stu-id="18d12-165">**Tooltip**</span></span><br>
    <span data-ttu-id="18d12-166">注釈 UI アニメーション コント ローラーやオブジェクトのラベル付けに使用できる柔軟なアンカー/ピボット システム <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="アプリ バー" width="250"><br>
    <span data-ttu-id="18d12-168">**アプリ バー**</span><span class="sxs-lookup"><span data-stu-id="18d12-168">**App Bar**</span></span><br>
    <span data-ttu-id="18d12-169">手動ライセンス認証の境界ボックスの UI <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="ポインター" width="250"><br>
    <span data-ttu-id="18d12-171">**ポインター**</span><span class="sxs-lookup"><span data-stu-id="18d12-171">**Pointers**</span></span><br>
    <span data-ttu-id="18d12-172">ポインターのさまざまな種類について説明します <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="指の視覚化" width="250"><br>
     <span data-ttu-id="18d12-174">**指の視覚化**</span><span class="sxs-lookup"><span data-stu-id="18d12-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="18d12-175">指を直接やり取りする信頼度を向上させる visual アフォー ダンス <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="スライダー" width="250"><br>
    <span data-ttu-id="18d12-177">**スライダー**</span><span class="sxs-lookup"><span data-stu-id="18d12-177">**Slider**</span></span><br>
    <span data-ttu-id="18d12-178">スライダー UI を調整するための操作を追跡するサポートの直接手を値します。 <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 標準シェーダー" width="250"><br>
    <span data-ttu-id="18d12-180">**MRTK 標準シェーダー**</span><span class="sxs-lookup"><span data-stu-id="18d12-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="18d12-181">MRTK の標準的なシェーダーがパフォーマンスのさまざまな Fluent デザインの要素をサポートしています <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="ハンド共同 Chaser" width="250"><br>
     <span data-ttu-id="18d12-183">**ハンド共同 Chaser**</span><span class="sxs-lookup"><span data-stu-id="18d12-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="18d12-184">ソルバーを使用して手ジョイントにオブジェクトをアタッチする方法を示します <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="視線:ターゲットの選択" width="250"><br>
    <span data-ttu-id="18d12-186">**視線:ターゲットの選択**</span><span class="sxs-lookup"><span data-stu-id="18d12-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="18d12-187">目、音声と手を迅速かつ簡単に、シーンの間でホログラムを選択します。 入力を結合します。 <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="視線:ナビゲーション" width="250"><br>
    <span data-ttu-id="18d12-189">**視線:ナビゲーション**</span><span class="sxs-lookup"><span data-stu-id="18d12-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="18d12-190">自動スクロールのテキストまたはスムーズで検索する内容に基づくフォーカスのあるコンテンツを拡大する方法について説明します <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="視線:ヒート マップ" width="250"><br>
    <span data-ttu-id="18d12-192">**視線:ヒート マップ**</span><span class="sxs-lookup"><span data-stu-id="18d12-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="18d12-193">ログ記録の例については、読み込みとどのようなユーザーの視覚化が探してで、アプリで <a/></span><span class="sxs-lookup"><span data-stu-id="18d12-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="18d12-194">MRTK v2 の最小要件</span><span class="sxs-lookup"><span data-stu-id="18d12-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="18d12-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="18d12-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="18d12-196">Microsoft Visual Studio 2017 またはそれ以降</span><span class="sxs-lookup"><span data-stu-id="18d12-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="18d12-197">Windows SDK 18362+</span><span class="sxs-lookup"><span data-stu-id="18d12-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="18d12-198">Windows 10 1803 以降</span><span class="sxs-lookup"><span data-stu-id="18d12-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="18d12-199">新しい MRTK v2</span><span class="sxs-lookup"><span data-stu-id="18d12-199">New with MRTK v2</span></span>
<span data-ttu-id="18d12-200">これらのプラットフォーム ツールに対するマイクロソフトのコミットメントを強調します。</span><span class="sxs-lookup"><span data-stu-id="18d12-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="18d12-201">実際には、セットアップ experience (OOBE) や Mixed Reality Learning アプリケーションなど、受信トレイ エクスペリエンスを開発する MRTK バージョン 2 を利用します。</span><span class="sxs-lookup"><span data-stu-id="18d12-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="18d12-202">最初は、プラットフォーム上で開発する最善の方法を考えているためです MRTK を通じて公開されている新しい HoloLens 2 機能を確認することも期待できます。</span><span class="sxs-lookup"><span data-stu-id="18d12-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="18d12-203">モジュール</span><span class="sxs-lookup"><span data-stu-id="18d12-203">Modular</span></span>
<span data-ttu-id="18d12-204">ツールキットのすべてのビットをプロジェクトを考慮する必要はありませんようにして、モジュール方式で作成しましたがあります。</span><span class="sxs-lookup"><span data-stu-id="18d12-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="18d12-205">これを実際には、いくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="18d12-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="18d12-206">プロジェクトのサイズを小さく維持だけでなく管理しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="18d12-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="18d12-207">スクリプト可能なオブジェクトで構築されていますので、インターフェイス駆動ことも、その他のサービス、システム、およびプラットフォームをサポートするために、独自に含まれているコンポーネントを交換するため。</span><span class="sxs-lookup"><span data-stu-id="18d12-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="18d12-208">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="18d12-208">Cross-platform</span></span>
<span data-ttu-id="18d12-209">その他のプラットフォームと言えば、クロス プラットフォーム サポートしています。</span><span class="sxs-lookup"><span data-stu-id="18d12-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="18d12-210">すべて 1 つのプラットフォームがサポートしているわけでは中、に他のプラットフォーム、ビルド ターゲットを切り替えたときに中断されます toolkit のことを確認されました。</span><span class="sxs-lookup"><span data-stu-id="18d12-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="18d12-211">堅牢性とモジュールの設計による拡張機能を ARCore、ARKit、OpenVR など、複数のプラットフォームをサポートできる適切なパスを設定します。</span><span class="sxs-lookup"><span data-stu-id="18d12-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="18d12-212">パフォーマンスの高い</span><span class="sxs-lookup"><span data-stu-id="18d12-212">Performant</span></span>
<span data-ttu-id="18d12-213">モバイル プラットフォームを使用 20050607 がパフォーマンスに注意してください。</span><span class="sxs-lookup"><span data-stu-id="18d12-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="18d12-214">これは非常に重要なツールが働きますしようとしていないことを確認したいです。</span><span class="sxs-lookup"><span data-stu-id="18d12-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="18d12-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="18d12-215">See also</span></span>
* [<span data-ttu-id="18d12-216">MRTK ファースト ステップ ガイド</span><span class="sxs-lookup"><span data-stu-id="18d12-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="18d12-217">MRTK ドキュメント ホーム</span><span class="sxs-lookup"><span data-stu-id="18d12-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="18d12-218">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="18d12-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="18d12-219">HTK/MRTK から MRTK バージョン 2 への移植</span><span class="sxs-lookup"><span data-stu-id="18d12-219">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)
