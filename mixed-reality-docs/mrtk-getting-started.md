---
title: MRTK バージョン2の概要
description: MRTK の活用に関心がある新しい開発者向け
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality、test、Mixed Reality Toolkit、MRTK バージョン2、MRTK、tools、SDK、HoloLens、HoloLens 2
ms.openlocfilehash: 7eded2c766765a5ccebf741eed2f8b7fe8f65a93
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507927"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="f0999-104">MRTK v2 の概要</span><span class="sxs-lookup"><span data-stu-id="f0999-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="f0999-105">MRTK はじめにガイド</span><span class="sxs-lookup"><span data-stu-id="f0999-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="f0999-106">MRTK V2 の概要については、「 [mrtk ファーストステップガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0999-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="f0999-107">Mixed Reality Toolkit (MRTK) とは</span><span class="sxs-lookup"><span data-stu-id="f0999-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="f0999-108">MRTK は、HoloLens が最初にリリースされた後に行われていたすばらしいオープンソースのツールキットであり、現在のところ、開発者コミュニティが提供されているので、このツールキットを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f0999-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="f0999-109">過去3年間、microsoft は開発者コミュニティのフィードバックを受け、最大の関心事を考慮するために MRTK v2 を構築しました。</span><span class="sxs-lookup"><span data-stu-id="f0999-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="f0999-110">Unity を使用した MRTK v2 は、mixed reality アプリケーション用のオープンソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="f0999-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="f0999-111">MRTK バージョン2は、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームを対象とするアプリケーションの開発を促進することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="f0999-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="f0999-112">このプロジェクトは、Mixed Reality アプリケーション作成への参入の障壁を減らし、私たち全員の成長とともにコミュニティに貢献することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="f0999-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="f0999-113">詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0999-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="f0999-114">機能領域</span><span class="sxs-lookup"><span data-stu-id="f0999-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="入力システム" width="105"> <span data-ttu-id="f0999-116">入力システム</span><span class="sxs-lookup"><span data-stu-id="f0999-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="ハンドトラッキング (HoloLens 2)" width="105"> <span data-ttu-id="f0999-118">ハンドトラッキング (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="f0999-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="視線追跡 (HoloLens 2)" width="105">
    <span data-ttu-id="f0999-120">視線追跡 (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="f0999-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="音声によるコマンド" width="105"> <span data-ttu-id="f0999-122">音声によるコマンド</span><span class="sxs-lookup"><span data-stu-id="f0999-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="宝石 + 選択 (HoloLens (第1世代))" width="105">
    <span data-ttu-id="f0999-124">宝石 + 選択 (HoloLens (第1世代))</span><span class="sxs-lookup"><span data-stu-id="f0999-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="受付" width="105"> <span data-ttu-id="f0999-126">受付</span><span class="sxs-lookup"><span data-stu-id="f0999-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI コントロール" width="105"> <span data-ttu-id="f0999-128">UI コントロール</span><span class="sxs-lookup"><span data-stu-id="f0999-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="ソルバーと相互作用" width="105"> <span data-ttu-id="f0999-130">ソルバーと相互作用</span><span class="sxs-lookup"><span data-stu-id="f0999-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="コントローラーの視覚化" width="105"> <span data-ttu-id="f0999-132">コントローラーの視覚化</span><span class="sxs-lookup"><span data-stu-id="f0999-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="空間の理解" width="105"> <span data-ttu-id="f0999-134">空間の理解</span><span class="sxs-lookup"><span data-stu-id="f0999-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="診断ツール" width="105"> <span data-ttu-id="f0999-136">診断ツール</span><span class="sxs-lookup"><span data-stu-id="f0999-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK 標準シェーダー" width="105"> <span data-ttu-id="f0999-138">MRTK 標準シェーダー</span><span class="sxs-lookup"><span data-stu-id="f0999-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="f0999-139">UI と相互作用の構成要素</span><span class="sxs-lookup"><span data-stu-id="f0999-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="ボタン" width="250"><br>
    <span data-ttu-id="f0999-141">**Button**</span><span class="sxs-lookup"><span data-stu-id="f0999-141">**Button**</span></span><br>
    <span data-ttu-id="f0999-142">HoloLens 2 の手を含むさまざまな入力方法をサポートするボタンコントロール<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="境界ボックス" width="250"><br>
    <span data-ttu-id="f0999-144">**境界ボックス**</span><span class="sxs-lookup"><span data-stu-id="f0999-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="f0999-145">3D 空間内のオブジェクトを操作するための標準 UI<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="操作ハンドラー" width="250"><br>
    <span data-ttu-id="f0999-147">**操作ハンドラー**</span><span class="sxs-lookup"><span data-stu-id="f0999-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="f0999-148">1人または2人の手でオブジェクトを操作するためのスクリプト<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="翻訳" width="250"><br>
    <span data-ttu-id="f0999-150">**翻訳**</span><span class="sxs-lookup"><span data-stu-id="f0999-150">**Slate**</span></span> <br>
    <span data-ttu-id="f0999-151">入力によるスクロールをサポートする2D スタイルプレーン<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="システムキーボード" width="250"><br>
    <span data-ttu-id="f0999-153">**システムキーボード**</span><span class="sxs-lookup"><span data-stu-id="f0999-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="f0999-154">Unity でシステムキーボードを使用するサンプルスクリプト<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="対話型" width="250"><br>
     <span data-ttu-id="f0999-156">**対話型**</span><span class="sxs-lookup"><span data-stu-id="f0999-156">**Interactable**</span></span> <br>
     <span data-ttu-id="f0999-157">視覚的な状態とテーマのサポートを使用してオブジェクトを対話型するためのスクリプト<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title=":" width="250"><br>
    <span data-ttu-id="f0999-159">**:**</span><span class="sxs-lookup"><span data-stu-id="f0999-159">**Solver**</span></span> <br>
    <span data-ttu-id="f0999-160">タグに沿って、本文ロック、定数ビューサイズ、表面吸着などのさまざまなオブジェクトの配置動作<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="オブジェクトコレクション" width="250"><br>
    <span data-ttu-id="f0999-162">**オブジェクトコレクション**</span><span class="sxs-lookup"><span data-stu-id="f0999-162">**Object Collection**</span></span><br>
    <span data-ttu-id="f0999-163">3次元図形内のオブジェクトの配列をレイアウトするためのスクリプト<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="ヒント" width="250">  <br>
    <span data-ttu-id="f0999-165">**ボタン**</span><span class="sxs-lookup"><span data-stu-id="f0999-165">**Tooltip**</span></span><br>
    <span data-ttu-id="f0999-166">モーションコントローラーとオブジェクトのラベル付けに使用できる柔軟なアンカー/ピボットシステムを使用した注釈 UI<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="アプリバー" width="250"><br>
    <span data-ttu-id="f0999-168">**アプリバー**</span><span class="sxs-lookup"><span data-stu-id="f0999-168">**App Bar**</span></span><br>
    <span data-ttu-id="f0999-169">境界ボックスの手動アクティブ化の UI<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="ポインター" width="250"><br>
    <span data-ttu-id="f0999-171">**ポインター**</span><span class="sxs-lookup"><span data-stu-id="f0999-171">**Pointers**</span></span><br>
    <span data-ttu-id="f0999-172">さまざまな種類のポインターについて<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="指先の視覚化" width="250"><br>
     <span data-ttu-id="f0999-174">**指先の視覚化**</span><span class="sxs-lookup"><span data-stu-id="f0999-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="f0999-175">指先での Visual affordance による直接的な相互作用の信頼性の向上<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="スライダー" width="250"><br>
    <span data-ttu-id="f0999-177">**Slider**</span><span class="sxs-lookup"><span data-stu-id="f0999-177">**Slider**</span></span><br>
    <span data-ttu-id="f0999-178">ダイレクトハンドトラッキングの相互作用をサポートする値を調整するためのスライダー UI<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 標準シェーダー" width="250"><br>
    <span data-ttu-id="f0999-180">**MRTK 標準シェーダー**</span><span class="sxs-lookup"><span data-stu-id="f0999-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="f0999-181">MRTK の標準シェーダーでは、パフォーマンスを備えたさまざまな Fluent デザイン要素がサポートされています。<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="手ジョイント Chaser" width="250"><br>
     <span data-ttu-id="f0999-183">**手ジョイント Chaser**</span><span class="sxs-lookup"><span data-stu-id="f0999-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="f0999-184">ソルバーを使用してオブジェクトを手の継手に接続する方法を示します。<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="目の追跡:ターゲットの選択" width="250"><br>
    <span data-ttu-id="f0999-186">**目の追跡:ターゲットの選択**</span><span class="sxs-lookup"><span data-stu-id="f0999-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="f0999-187">視点、音声、手入力を組み合わせてシーン全体のホログラムをすばやく簡単に選択する<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="目の追跡:ナビゲーション" width="250"><br>
    <span data-ttu-id="f0999-189">**目の追跡:領域**</span><span class="sxs-lookup"><span data-stu-id="f0999-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="f0999-190">表示内容に基づいて、テキストを自動的にスクロールするか、フォーカスされているコンテンツにズームする方法について説明します。<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="目の追跡:ヒートマップ" width="250"><br>
    <span data-ttu-id="f0999-192">**目の追跡:ヒートマップ**</span><span class="sxs-lookup"><span data-stu-id="f0999-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="f0999-193">アプリに表示されているユーザーのログ記録、読み込み、視覚化の例<a/></span><span class="sxs-lookup"><span data-stu-id="f0999-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="f0999-194">MRTK v2 の最小要件</span><span class="sxs-lookup"><span data-stu-id="f0999-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="f0999-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="f0999-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="f0999-196">Microsoft Visual Studio 2017 以降</span><span class="sxs-lookup"><span data-stu-id="f0999-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="f0999-197">Windows SDK 18362 +</span><span class="sxs-lookup"><span data-stu-id="f0999-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="f0999-198">Windows 10 1803 以降</span><span class="sxs-lookup"><span data-stu-id="f0999-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="f0999-199">MRTK v2 の新バージョン</span><span class="sxs-lookup"><span data-stu-id="f0999-199">New with MRTK v2</span></span>
<span data-ttu-id="f0999-200">これらのプラットフォームツールに対するコミットメントを重視したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="f0999-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="f0999-201">実際、MRTK バージョン2を利用して、setup experience (OOBE) や Mixed Reality Learning アプリケーションなどの受信トレイエクスペリエンスを開発しました。</span><span class="sxs-lookup"><span data-stu-id="f0999-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="f0999-202">また、プラットフォームで開発するのに最適な方法であると考えられるため、新しい HoloLens 2 機能が MRTK を通じて最初に公開されることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="f0999-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="f0999-203">方式</span><span class="sxs-lookup"><span data-stu-id="f0999-203">Modular</span></span>
<span data-ttu-id="f0999-204">モジュール型の方法でビルドしたため、ツールキットをすべてプロジェクトに取り込む必要がありません。</span><span class="sxs-lookup"><span data-stu-id="f0999-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="f0999-205">これには、実際にいくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="f0999-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="f0999-206">これにより、プロジェクトのサイズが小さくなり、管理も容易になります。</span><span class="sxs-lookup"><span data-stu-id="f0999-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="f0999-207">それに加えて、スクリプト可能なオブジェクトを使用して構築され、インターフェイスによって駆動されるため、独自のに含まれているコンポーネントを置き換えることで、他のサービス、システム、およびプラットフォームをサポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f0999-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="f0999-208">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="f0999-208">Cross-platform</span></span>
<span data-ttu-id="f0999-209">他のプラットフォームの場合は、クロスプラットフォームのサポートがあります。</span><span class="sxs-lookup"><span data-stu-id="f0999-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="f0999-210">これは、すべての単一プラットフォームが既定でサポートされているわけではありませんが、ビルドターゲットを他のプラットフォームに切り替えると、どのツールキットコードも破損しないようにしました。</span><span class="sxs-lookup"><span data-stu-id="f0999-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="f0999-211">モジュール型の設計による堅牢性と拡張性により、ARCore、Arcore、OpenVR などの複数のプラットフォームをサポートするための優れたパスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="f0999-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="f0999-212">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="f0999-212">Performant</span></span>
<span data-ttu-id="f0999-213">モバイルプラットフォームを使用すると、パフォーマンスを考慮して構築されています。</span><span class="sxs-lookup"><span data-stu-id="f0999-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="f0999-214">これは非常に重要であり、ツールがお客様に対して機能しないようにする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="f0999-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="f0999-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0999-215">See also</span></span>
* [<span data-ttu-id="f0999-216">MRTK ファーストステップガイド</span><span class="sxs-lookup"><span data-stu-id="f0999-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="f0999-217">MRTK ドキュメントホーム</span><span class="sxs-lookup"><span data-stu-id="f0999-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="f0999-218">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="f0999-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="f0999-219">HTK/MRTK から MRTK バージョン2への移植</span><span class="sxs-lookup"><span data-stu-id="f0999-219">Porting from HTK/MRTK to MRTK version 2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
