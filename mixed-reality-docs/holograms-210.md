---
title: MR 入力 210 - 視線入力
description: このコーディングの視線の先の概念の詳細については、Unity、Visual Studio および HoloLens の使用に関するチュートリアルに従います。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit unity academy、チュートリアル、視線入力
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993552"
---
>[!NOTE]
><span data-ttu-id="29811-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="29811-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="29811-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="29811-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="29811-106">これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="29811-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="29811-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="29811-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="29811-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="29811-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="29811-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="29811-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="29811-110">MR 入力 210:視線入力</span><span class="sxs-lookup"><span data-stu-id="29811-110">MR Input 210: Gaze</span></span>

<span data-ttu-id="29811-111">[視線](gaze.md)入力の最初のフォームであり、ユーザーの意図と認識が表示されます。</span><span class="sxs-lookup"><span data-stu-id="29811-111">[Gaze](gaze.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="29811-112">MR 入力 210 (プロジェクト エクスプ ローラーとも呼ばれます) は、Windows Mixed Reality の視線の先に関連する概念に詳しく知るです。</span><span class="sxs-lookup"><span data-stu-id="29811-112">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="29811-113">追加される予定コンテキストの認識をカーソルやホログラム、ユーザーの視線入力について知っている、アプリをフル活用します。</span><span class="sxs-lookup"><span data-stu-id="29811-113">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="29811-114">ここにあるわかりやすい「宇宙飛行士視線の先の概念を学習するためです。</span><span class="sxs-lookup"><span data-stu-id="29811-114">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="29811-115">[MR 基本 101](holograms-101.md)、単純カーソルだけ、視線の先に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="29811-115">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="29811-116">今すぐ歩単純カーソルを移動するとき。</span><span class="sxs-lookup"><span data-stu-id="29811-116">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="29811-117">行ったカーソルと、ホログラム視線の先に注意してください: - ユーザーが検索している、またはユーザーのいるに基づいてどちらも変更されます*いない*検索します。</span><span class="sxs-lookup"><span data-stu-id="29811-117">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="29811-118">これにより、コンテキストに対応しています。</span><span class="sxs-lookup"><span data-stu-id="29811-118">This makes them context-aware.</span></span>
* <span data-ttu-id="29811-119">フィードバックは、カーソルと何が対象の詳細なコンテキストを付与するためにホログラムを追加します。</span><span class="sxs-lookup"><span data-stu-id="29811-119">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="29811-120">このフィードバックは、音声と視覚的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="29811-120">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="29811-121">小規模なターゲットにユーザーを対象とする手法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="29811-121">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="29811-122">方向インジケーターで、ホログラムにユーザーの注目を集める方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="29811-122">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="29811-123">彼女は、世界中の周りが移動すると、ユーザーと、ホログラムを実行するための手法を学ぶ。</span><span class="sxs-lookup"><span data-stu-id="29811-123">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="29811-124">以前のバージョンの Unity と Mixed Reality Toolkit を使用して、以下の各章に埋め込まれたビデオが記録されています。</span><span class="sxs-lookup"><span data-stu-id="29811-124">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="29811-125">詳細な手順については、正確かつ最新ですが、スクリプトとは、無効な対応するビデオの中でビジュアルを表示があります。</span><span class="sxs-lookup"><span data-stu-id="29811-125">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="29811-126">ビデオでは、後生のために含まれる保持され、概念説明のため、引き続き適用されます。</span><span class="sxs-lookup"><span data-stu-id="29811-126">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="29811-127">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="29811-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="29811-128">コース</span><span class="sxs-lookup"><span data-stu-id="29811-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="29811-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="29811-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="29811-130"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="29811-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="29811-131">MR 入力 210:視線入力</span><span class="sxs-lookup"><span data-stu-id="29811-131">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="29811-132">✔️</span><span class="sxs-lookup"><span data-stu-id="29811-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="29811-133">✔️</span><span class="sxs-lookup"><span data-stu-id="29811-133">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="29811-134">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="29811-134">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="29811-135">前提条件</span><span class="sxs-lookup"><span data-stu-id="29811-135">Prerequisites</span></span>

* <span data-ttu-id="29811-136">正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="29811-136">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="29811-137">基本的なC#プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="29811-137">Some basic C# programming ability.</span></span>
* <span data-ttu-id="29811-138">完了する必要があります[MR 基本 101](holograms-101.md)します。</span><span class="sxs-lookup"><span data-stu-id="29811-138">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="29811-139">HoloLens デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。</span><span class="sxs-lookup"><span data-stu-id="29811-139">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="29811-140">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="29811-140">Project files</span></span>

* <span data-ttu-id="29811-141">ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip)プロジェクトに必要です。</span><span class="sxs-lookup"><span data-stu-id="29811-141">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="29811-142"> Unity 2017.2 またはそれ以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="29811-142"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="29811-143">解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。</span><span class="sxs-lookup"><span data-stu-id="29811-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="29811-144">をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)します。</span><span class="sxs-lookup"><span data-stu-id="29811-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="29811-145">正誤表と注意事項</span><span class="sxs-lookup"><span data-stu-id="29811-145">Errata and Notes</span></span>

* <span data-ttu-id="29811-146">「マイ コードのみ」を Visual Studio では、する必要がある無効 (オフ) ツール オプション-> コードにブレークポイントをヒットするにはデバッグ-> です。</span><span class="sxs-lookup"><span data-stu-id="29811-146">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="29811-147">第 1 章 - Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="29811-147">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="29811-148">目標</span><span class="sxs-lookup"><span data-stu-id="29811-148">Objectives</span></span>

* <span data-ttu-id="29811-149">HoloLens の開発のためには、Unity を最適化します。</span><span class="sxs-lookup"><span data-stu-id="29811-149">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="29811-150">アセットをインポートして、シーンをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="29811-150">Import assets and setup the scene.</span></span>
* <span data-ttu-id="29811-151">HoloLens、飛行士を表示します。</span><span class="sxs-lookup"><span data-stu-id="29811-151">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="29811-152">手順</span><span class="sxs-lookup"><span data-stu-id="29811-152">Instructions</span></span>

1. <span data-ttu-id="29811-153">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="29811-153">Start Unity.</span></span>
2. <span data-ttu-id="29811-154">選択**新しいプロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="29811-154">Select **New Project**.</span></span>
3. <span data-ttu-id="29811-155">プロジェクトに名前を**ModelExplorer**します。</span><span class="sxs-lookup"><span data-stu-id="29811-155">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="29811-156">として場所を入力、**視線**フォルダー アーカイブされた以前のことです。</span><span class="sxs-lookup"><span data-stu-id="29811-156">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="29811-157">必ず、プロジェクトに設定されて**3D**します。</span><span class="sxs-lookup"><span data-stu-id="29811-157">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="29811-158">クリックして**プロジェクトを作成する**します。</span><span class="sxs-lookup"><span data-stu-id="29811-158">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="29811-159">HoloLens の unity の設定</span><span class="sxs-lookup"><span data-stu-id="29811-159">Unity settings for HoloLens</span></span>

<span data-ttu-id="29811-160">Unity をエクスポートしようとしましたが、アプリが作成することを把握できるようにする必要があります、[没入型ビュー](app-views.md) 2D ビューではなく。</span><span class="sxs-lookup"><span data-stu-id="29811-160">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="29811-161">そのために、HoloLens を仮想現実デバイスとして追加します。</span><span class="sxs-lookup"><span data-stu-id="29811-161">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="29811-162">移動して**編集 > プロジェクトの設定 > Player**します。</span><span class="sxs-lookup"><span data-stu-id="29811-162">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="29811-163">**インスペクター パネル**Player の設定の選択、 **Windows ストア**アイコン。</span><span class="sxs-lookup"><span data-stu-id="29811-163">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="29811-164">展開、 **XR 設定**グループ。</span><span class="sxs-lookup"><span data-stu-id="29811-164">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="29811-165">**レンダリング** セクションで、チェック、**仮想現実サポート**新しいを追加するチェック ボックスをオン**仮想現実 Sdk**一覧。</span><span class="sxs-lookup"><span data-stu-id="29811-165">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="29811-166">いることを確認**Windows Mixed Reality**一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="29811-166">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="29811-167">そうでない場合は、選択、 **+** 一覧の下部にあるボタンをクリックし、選択**Windows Holographic**します。</span><span class="sxs-lookup"><span data-stu-id="29811-167">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="29811-168">次に、.NET に、スクリプトのバックエンドを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29811-168">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="29811-169">移動して**編集 > プロジェクトの設定 > Player** (する必要がありますもこれ前の手順から)。</span><span class="sxs-lookup"><span data-stu-id="29811-169">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="29811-170">**インスペクター パネル**Player の設定の選択、 **Windows ストア**アイコン。</span><span class="sxs-lookup"><span data-stu-id="29811-170">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="29811-171">**その他の設定**構成セクションで、必ず**Scripting バックエンド**に設定されている **.NET**</span><span class="sxs-lookup"><span data-stu-id="29811-171">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="29811-172">最後に、HoloLens の高速なパフォーマンスを実現するために、品質設定を更新します。</span><span class="sxs-lookup"><span data-stu-id="29811-172">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="29811-173">移動して**編集 > プロジェクトの設定 > 品質**します。</span><span class="sxs-lookup"><span data-stu-id="29811-173">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="29811-174">下向きの矢印をクリックして、**既定**Windows ストア アイコンの下の行。</span><span class="sxs-lookup"><span data-stu-id="29811-174">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="29811-175">選択**非常に低い**の**Windows ストア アプリ**します。</span><span class="sxs-lookup"><span data-stu-id="29811-175">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="29811-176">プロジェクトのアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="29811-176">Import project assets</span></span>

1. <span data-ttu-id="29811-177">右クリックして、**資産**フォルダーで、**プロジェクト**パネル。</span><span class="sxs-lookup"><span data-stu-id="29811-177">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="29811-178">をクリックして**パッケージ インポート > カスタム パッケージ**します。</span><span class="sxs-lookup"><span data-stu-id="29811-178">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="29811-179">ダウンロードしたプロジェクト ファイルに移動し、をクリックして**ModelExplorer.unitypackage**します。</span><span class="sxs-lookup"><span data-stu-id="29811-179">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="29811-180">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="29811-180">Click **Open**.</span></span>
5. <span data-ttu-id="29811-181">パッケージが読み込まれると後でをクリックして、**インポート**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="29811-181">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="29811-182">シーンのセットアップ</span><span class="sxs-lookup"><span data-stu-id="29811-182">Setup the scene</span></span>

1. <span data-ttu-id="29811-183">階層では、削除、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="29811-183">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="29811-184">**HoloToolkit**フォルダーを開き、**入力**フォルダーを開き、**プレハブ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="29811-184">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="29811-185">ドラッグ アンド ドロップ、 **MixedRealityCameraParent**からプレハブ、**プレハブ**フォルダーに、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="29811-185">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="29811-186">右クリックし、**指向性光**階層し、**削除**します。</span><span class="sxs-lookup"><span data-stu-id="29811-186">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="29811-187">**ホログラム**フォルダーにドラッグ アンド ドロップは次のアセットのルート、**階層**:</span><span class="sxs-lookup"><span data-stu-id="29811-187">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="29811-188">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="29811-188">**AstroMan**</span></span>
    * <span data-ttu-id="29811-189">**ライト**</span><span class="sxs-lookup"><span data-stu-id="29811-189">**Lights**</span></span>
    * <span data-ttu-id="29811-190">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="29811-190">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="29811-191">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="29811-191">**SpaceBackground**</span></span>
6. <span data-ttu-id="29811-192">開始**再生モード**▶、飛行士を表示します。</span><span class="sxs-lookup"><span data-stu-id="29811-192">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="29811-193">クリックして**再生モード**をもう一度 ▶**停止**します。</span><span class="sxs-lookup"><span data-stu-id="29811-193">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="29811-194">**ホログラム**フォルダー、検索、 **Fitbox**資産のルートにドラッグし、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="29811-194">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="29811-195">選択、 **Fitbox**で、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="29811-195">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="29811-196">ドラッグ、 **AstroMan**コレクションから、**階層**を**ホログラム コレクション**で Fitbox のプロパティ、**インスペクター**パネル。</span><span class="sxs-lookup"><span data-stu-id="29811-196">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="29811-197">プロジェクトを保存します</span><span class="sxs-lookup"><span data-stu-id="29811-197">Save the project</span></span>

1. <span data-ttu-id="29811-198">新しいシーンを保存します。**ファイル > としてシーンを保存**します。</span><span class="sxs-lookup"><span data-stu-id="29811-198">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="29811-199">クリックして**新しいフォルダー**フォルダーの名前と**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="29811-199">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="29811-200">ファイルに名前を"**ModelExplorer**"で保存し、**シーン**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="29811-200">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="29811-201">プロジェクトをビルドします</span><span class="sxs-lookup"><span data-stu-id="29811-201">Build the project</span></span>

1. <span data-ttu-id="29811-202">Unity では、次のように選択します。**ファイル > Build Settings**します。</span><span class="sxs-lookup"><span data-stu-id="29811-202">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="29811-203">をクリックして**開くシーンを追加**シーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="29811-203">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="29811-204">選択**ユニバーサル Windows プラットフォーム**で、**プラットフォーム**を一覧表示し、クリックして**スイッチ プラットフォーム**します。</span><span class="sxs-lookup"><span data-stu-id="29811-204">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="29811-205">具体的には、HoloLens の開発中、設定**ターゲット デバイス**に**HoloLens**します。</span><span class="sxs-lookup"><span data-stu-id="29811-205">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="29811-206">それ以外の場合、残して**任意のデバイス**します。</span><span class="sxs-lookup"><span data-stu-id="29811-206">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="29811-207">確認**ビルド タイプ**に設定されている**D3D**と**SDK**に設定されている**インストールされている最新**(16299 またはそれ以降の SDK がある必要があります)。</span><span class="sxs-lookup"><span data-stu-id="29811-207">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="29811-208">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="29811-208">Click **Build**.</span></span>
7. <span data-ttu-id="29811-209">作成、**新しいフォルダー** "App"という名前です。</span><span class="sxs-lookup"><span data-stu-id="29811-209">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="29811-210">1 回のクリック、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="29811-210">Single click the **App** folder.</span></span>
9. <span data-ttu-id="29811-211">キーを押して**フォルダーを選択します**します。</span><span class="sxs-lookup"><span data-stu-id="29811-211">Press **Select Folder**.</span></span>

<span data-ttu-id="29811-212">Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="29811-212">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="29811-213">開く、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="29811-213">Open the **App** folder.</span></span>
2. <span data-ttu-id="29811-214">開く、 **ModelExplorer Visual Studio ソリューション**します。</span><span class="sxs-lookup"><span data-stu-id="29811-214">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="29811-215">HoloLens へのデプロイ: 場合</span><span class="sxs-lookup"><span data-stu-id="29811-215">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="29811-216">デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x86**します。</span><span class="sxs-lookup"><span data-stu-id="29811-216">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="29811-217">ローカル コンピューター] ボタンの横の矢印のドロップダウンをクリックし、[**リモート マシン**します。</span><span class="sxs-lookup"><span data-stu-id="29811-217">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="29811-218">入力**HoloLens デバイスの IP アドレス**認証モードを設定および**ユニバーサル (暗号化されていないプロトコル)** します。</span><span class="sxs-lookup"><span data-stu-id="29811-218">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="29811-219">クリックして**選択**します。</span><span class="sxs-lookup"><span data-stu-id="29811-219">Click **Select**.</span></span> <span data-ttu-id="29811-220">デバイスの IP アドレスがわからない場合に参照**設定 > ネットワークとインターネット > 詳細オプション**します。</span><span class="sxs-lookup"><span data-stu-id="29811-220">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="29811-221">上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="29811-221">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="29811-222">最初に、デバイスに展開するには、する必要があります[Visual Studio をペアリング](using-visual-studio.md#pairing-your-device-hololens)します。</span><span class="sxs-lookup"><span data-stu-id="29811-222">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="29811-223">アプリが展開されると、消去、 **Fitbox**で、**ジェスチャ を選択**します。</span><span class="sxs-lookup"><span data-stu-id="29811-223">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="29811-224">場合は、イマーシブ ヘッドセットへのデプロイ。</span><span class="sxs-lookup"><span data-stu-id="29811-224">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="29811-225">デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x64**します。</span><span class="sxs-lookup"><span data-stu-id="29811-225">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="29811-226">必ず、配置ターゲットに設定されて**ローカル マシン**します。</span><span class="sxs-lookup"><span data-stu-id="29811-226">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="29811-227">上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="29811-227">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="29811-228">アプリが展開されると、消去、 **Fitbox**アニメーション コント ローラーで、トリガーを取得することによって。</span><span class="sxs-lookup"><span data-stu-id="29811-228">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="29811-229">第 2 章 – カーソルとターゲットのフィードバック</span><span class="sxs-lookup"><span data-stu-id="29811-229">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="29811-230">目標</span><span class="sxs-lookup"><span data-stu-id="29811-230">Objectives</span></span>

* <span data-ttu-id="29811-231">カーソルのビジュアル デ ザインと動作します。</span><span class="sxs-lookup"><span data-stu-id="29811-231">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="29811-232">視線入力ベースのカーソル フィードバック。</span><span class="sxs-lookup"><span data-stu-id="29811-232">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="29811-233">視線の先に基づくホログラム フィードバック。</span><span class="sxs-lookup"><span data-stu-id="29811-233">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="29811-234">つまり、何らかのカーソルの設計の原則に作業を基にいきます。</span><span class="sxs-lookup"><span data-stu-id="29811-234">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="29811-235">カーソルは、常に存在します。</span><span class="sxs-lookup"><span data-stu-id="29811-235">The cursor is always present.</span></span>
* <span data-ttu-id="29811-236">カーソルが小さすぎるかビッグを取得することはありません。</span><span class="sxs-lookup"><span data-stu-id="29811-236">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="29811-237">コンテンツの障害を回避します。</span><span class="sxs-lookup"><span data-stu-id="29811-237">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="29811-238">手順</span><span class="sxs-lookup"><span data-stu-id="29811-238">Instructions</span></span>

1. <span data-ttu-id="29811-239">**HoloToolkit\Input\Prefabs**フォルダー、検索、 **InputManager**資産。</span><span class="sxs-lookup"><span data-stu-id="29811-239">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="29811-240">ドラッグ アンド ドロップ、 **InputManager**上に、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="29811-240">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="29811-241">**HoloToolkit\Input\Prefabs**フォルダー、検索、**カーソル**資産。</span><span class="sxs-lookup"><span data-stu-id="29811-241">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="29811-242">ドラッグ アンド ドロップ、**カーソル**上に、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="29811-242">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="29811-243">選択、 **InputManager**オブジェクト、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="29811-243">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="29811-244">ドラッグ、**カーソル**オブジェクトから、**階層**InputManager に**SimpleSinglePointerSelector**の**カーソル**フィールドで、下部にある、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="29811-244">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![簡単な 1 つのポインターのセレクターのセットアップ](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="29811-246">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="29811-246">Build and Deploy</span></span>

1. <span data-ttu-id="29811-247">アプリをリビルド**ファイル > のビルド設定**します。</span><span class="sxs-lookup"><span data-stu-id="29811-247">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="29811-248">開く、**アプリ フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="29811-248">Open the **App folder**.</span></span>
3. <span data-ttu-id="29811-249">開く、 **ModelExplorer Visual Studio ソリューション**します。</span><span class="sxs-lookup"><span data-stu-id="29811-249">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="29811-250">クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="29811-250">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="29811-251">カーソルを描画する方法、およびホログラムに触れている場合に外観を変更にする方法を確認します。</span><span class="sxs-lookup"><span data-stu-id="29811-251">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="29811-252">手順</span><span class="sxs-lookup"><span data-stu-id="29811-252">Instructions</span></span>

1. <span data-ttu-id="29811-253">**階層**パネルで、展開、 **AstroMan**->**GEO_G**->**Back_Center**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="29811-253">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="29811-254">ダブルクリックします。 **Interactible.cs** Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="29811-254">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="29811-255">関数が呼び出される、 **IFocusable.OnFocusEnter()** と**IFocusable.OnFocusExit()** コールバック**Interactible.cs**します。</span><span class="sxs-lookup"><span data-stu-id="29811-255">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="29811-256">これらはフォーカス (か注視コント ローラーをポイント) を入力し、特定の GameObject のコライダーが終了したときに、Mixed Reality ツールキットの InputManager によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="29811-256">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
><span data-ttu-id="29811-257">使用して`EnableKeyword`と`DisableKeyword`上。</span><span class="sxs-lookup"><span data-stu-id="29811-257">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="29811-258">作成するには、Toolkit の標準的なシェーダーをアプリにこれらを使用して、従う必要があります、[スクリプトを介したマテリアルにアクセスするための Unity ガイドライン](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)。</span><span class="sxs-lookup"><span data-stu-id="29811-258">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="29811-259">この場合は、既に含まれています、[強調表示されているマテリアルの 3 つのバリエーション](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials)リソース フォルダー (の名前で強調表示された 3 つの資料を参照) が必要です。</span><span class="sxs-lookup"><span data-stu-id="29811-259">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="29811-260">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="29811-260">Build and Deploy</span></span>

1. <span data-ttu-id="29811-261">同様に、プロジェクトをビルドし、HoloLens を展開します。</span><span class="sxs-lookup"><span data-stu-id="29811-261">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="29811-262">オブジェクト、視線の先を目的としたときの動作を確認し、ない場合。</span><span class="sxs-lookup"><span data-stu-id="29811-262">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="29811-263">第 3 章の手法を対象とします。</span><span class="sxs-lookup"><span data-stu-id="29811-263">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="29811-264">目標</span><span class="sxs-lookup"><span data-stu-id="29811-264">Objectives</span></span>

* <span data-ttu-id="29811-265">ターゲット ホログラムを容易にします。</span><span class="sxs-lookup"><span data-stu-id="29811-265">Make it easier to target holograms.</span></span>
* <span data-ttu-id="29811-266">頭の自然な動きを安定化します。</span><span class="sxs-lookup"><span data-stu-id="29811-266">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="29811-267">手順</span><span class="sxs-lookup"><span data-stu-id="29811-267">Instructions</span></span>

1. <span data-ttu-id="29811-268">**階層**パネルで、 **InputManager**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="29811-268">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="29811-269">**インスペクター**パネルで、検索、**視線の安定板**スクリプト。</span><span class="sxs-lookup"><span data-stu-id="29811-269">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="29811-270">確認する場合 をクリックして Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="29811-270">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="29811-271">このスクリプトでは、Raycast データのサンプルを反復処理し、有効桁数が対象とする場合、ユーザーの視線の先を安定化に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="29811-271">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="29811-272">**インスペクター**、編集することができます、**安定性のサンプルの格納されている**値。</span><span class="sxs-lookup"><span data-stu-id="29811-272">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="29811-273">この値は、安定した値を計算する、安定板が反復処理するサンプルの数を表します。</span><span class="sxs-lookup"><span data-stu-id="29811-273">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="29811-274">第 4 章 - 方向インジケーター</span><span class="sxs-lookup"><span data-stu-id="29811-274">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="29811-275">目標</span><span class="sxs-lookup"><span data-stu-id="29811-275">Objectives</span></span>

* <span data-ttu-id="29811-276">ホログラムが見つけやすくカーソルに方向インジケーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="29811-276">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="29811-277">手順</span><span class="sxs-lookup"><span data-stu-id="29811-277">Instructions</span></span>

<span data-ttu-id="29811-278">使用して、 **DirectionIndicator.cs**されるファイル。</span><span class="sxs-lookup"><span data-stu-id="29811-278">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="29811-279">ユーザーが、ホログラムで gazing しないかどうかに方向インジケーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="29811-279">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="29811-280">ユーザーが、ホログラムで gazing する場合は、方向インジケーターを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="29811-280">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="29811-281">ホログラムを指す方向インジケーターを更新します。</span><span class="sxs-lookup"><span data-stu-id="29811-281">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="29811-282">それでは始めましょう。</span><span class="sxs-lookup"><span data-stu-id="29811-282">Let's get started.</span></span>

1. <span data-ttu-id="29811-283">をクリックして、 **AstroMan**オブジェクト、**階層**パネルと**矢印をクリックして**を展開します。</span><span class="sxs-lookup"><span data-stu-id="29811-283">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="29811-284">**階層**パネルで、 **DirectionalIndicator**オブジェクト**AstroMan**します。</span><span class="sxs-lookup"><span data-stu-id="29811-284">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="29811-285">**インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="29811-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="29811-286">メニューで、検索ボックスに入力**方向インジケーター**します。</span><span class="sxs-lookup"><span data-stu-id="29811-286">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="29811-287">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="29811-287">Select the search result.</span></span>
5. <span data-ttu-id="29811-288">**階層**パネルにドラッグ アンド ドロップ、**カーソル**オブジェクト、**カーソル**プロパティ、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="29811-288">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="29811-289">**プロジェクト** パネルで、**ホログラム**フォルダー、ドラッグ アンド ドロップ、 **DirectionalIndicator**上に資産、**方向インジケーター**プロパティ、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="29811-289">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="29811-290">ビルドして、アプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="29811-290">Build and deploy the app.</span></span>
8. <span data-ttu-id="29811-291">方向インジケーター オブジェクトは、「宇宙飛行士を検索する方法をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="29811-291">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="29811-292">第 5 章「ビルボード処理</span><span class="sxs-lookup"><span data-stu-id="29811-292">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="29811-293">目標</span><span class="sxs-lookup"><span data-stu-id="29811-293">Objectives</span></span>

* <span data-ttu-id="29811-294">ホログラムが常に手前に直面するには、ビルボード処理を使用します。</span><span class="sxs-lookup"><span data-stu-id="29811-294">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="29811-295">使用する、 **Billboard.cs**指向するよう、常に、ユーザーが直面しているが GameObject を保持するファイル。</span><span class="sxs-lookup"><span data-stu-id="29811-295">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="29811-296">**階層**パネルで、 **AstroMan**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="29811-296">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="29811-297">**インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="29811-297">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="29811-298">メニューで、検索ボックスに入力**ビルボード**します。</span><span class="sxs-lookup"><span data-stu-id="29811-298">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="29811-299">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="29811-299">Select the search result.</span></span>
4. <span data-ttu-id="29811-300">**インスペクター**設定、**回転軸**に**Y**します。</span><span class="sxs-lookup"><span data-stu-id="29811-300">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="29811-301">お試しください。</span><span class="sxs-lookup"><span data-stu-id="29811-301">Try it!</span></span> <span data-ttu-id="29811-302">ビルドし、前に、アプリとして展開します。</span><span class="sxs-lookup"><span data-stu-id="29811-302">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="29811-303">どのビュー ポイントを変更する方法に関係なくのビルボード オブジェクト直面するを参照してください。</span><span class="sxs-lookup"><span data-stu-id="29811-303">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="29811-304">スクリプトを削除、 **AstroMan**今のところです。</span><span class="sxs-lookup"><span data-stu-id="29811-304">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="29811-305">第 6 章 – Tag-Along</span><span class="sxs-lookup"><span data-stu-id="29811-305">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="29811-306">目標</span><span class="sxs-lookup"><span data-stu-id="29811-306">Objectives</span></span>

* <span data-ttu-id="29811-307">Tag-Along を使用して、室内をフォロー、ホログラムが付いてください。</span><span class="sxs-lookup"><span data-stu-id="29811-307">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="29811-308">この問題に取り組んでいます次の設計上の制約によって示されます。</span><span class="sxs-lookup"><span data-stu-id="29811-308">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="29811-309">コンテンツは常にすぐ概要。</span><span class="sxs-lookup"><span data-stu-id="29811-309">Content should always be a glance away.</span></span>
* <span data-ttu-id="29811-310">コンテンツは、ようにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="29811-310">Content should not be in the way.</span></span>
* <span data-ttu-id="29811-311">コンテンツの先頭のロックが快適ではありません。</span><span class="sxs-lookup"><span data-stu-id="29811-311">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="29811-312">ここで使用するソリューションでは、"tag-along"アプローチを使用します。</span><span class="sxs-lookup"><span data-stu-id="29811-312">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="29811-313">Tag-along オブジェクトは、完全には、ユーザーのビューを残します。</span><span class="sxs-lookup"><span data-stu-id="29811-313">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="29811-314">考えることができ、ユーザーの頭にラバー バンドでのオブジェクトとしての tag-along にアタッチされています。</span><span class="sxs-lookup"><span data-stu-id="29811-314">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="29811-315">ユーザーが移動すると、コンテンツが完全を離れることがなく、ビューの端をスライドして、簡単な概要内で維持されます。</span><span class="sxs-lookup"><span data-stu-id="29811-315">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="29811-316">ときに、ユーザーは gazes tag-along オブジェクトの方向より完全に入ったビュー。</span><span class="sxs-lookup"><span data-stu-id="29811-316">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="29811-317">使用して、 **SimpleTagalong.cs**されるファイル。</span><span class="sxs-lookup"><span data-stu-id="29811-317">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="29811-318">Tag-Along オブジェクトがカメラの境界内にあるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="29811-318">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="29811-319">指定しない場合、視錐台に視錐台内で部分的に Tag-Along を配置します。</span><span class="sxs-lookup"><span data-stu-id="29811-319">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="29811-320">それ以外の場合、ユーザーの既定の距離を Tag-Along を配置します。</span><span class="sxs-lookup"><span data-stu-id="29811-320">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="29811-321">これを行うには、まず変更、 **Interactible.cs**スクリプトを呼び出す、 **TagalongAction**します。</span><span class="sxs-lookup"><span data-stu-id="29811-321">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="29811-322">編集**Interactible.cs**コーディングを完了して 6.a (コメント解除行 84 に 87) を実行します。</span><span class="sxs-lookup"><span data-stu-id="29811-322">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="29811-323">**InteractibleAction.cs**と組み合わせてスクリプト**Interactible.cs**ホログラムでタップすると、カスタム アクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="29811-323">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="29811-324">この場合、tag-along に具体的には 1 つ使用します。</span><span class="sxs-lookup"><span data-stu-id="29811-324">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="29811-325">**スクリプト**フォルダーをクリックします**TagalongAction.cs**資産を Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="29811-325">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="29811-326">コーディングの練習を行うか、これに変更します。</span><span class="sxs-lookup"><span data-stu-id="29811-326">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="29811-327">上部にある、**階層**、検索バーの種類で**ChestButton_Center**結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="29811-327">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="29811-328">**インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="29811-328">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="29811-329">メニューで、検索ボックスに入力**末尾アクション**します。</span><span class="sxs-lookup"><span data-stu-id="29811-329">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="29811-330">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="29811-330">Select the search result.</span></span>
  * <span data-ttu-id="29811-331">**ホログラム**フォルダーの検索、**末尾**資産。</span><span class="sxs-lookup"><span data-stu-id="29811-331">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="29811-332">選択、 **ChestButton_Center**オブジェクト、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="29811-332">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="29811-333">ドラッグ アンド ドロップ、**末尾**オブジェクトから、**プロジェクト**パネル、**インスペクター**に、**オブジェクトに末尾**プロパティ。</span><span class="sxs-lookup"><span data-stu-id="29811-333">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="29811-334">ドラッグ、**末尾アクション**オブジェクトから、**インスペクター**に、 **Interactible アクション**フィールドに、 **Interactible**スクリプト。</span><span class="sxs-lookup"><span data-stu-id="29811-334">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="29811-335">ダブルクリックして、 **TagalongAction**スクリプトを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="29811-335">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interactible のセットアップ](images/holograms210-interactible.png)

<span data-ttu-id="29811-337">次を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29811-337">We need to add the following:</span></span>

* <span data-ttu-id="29811-338">PerformAction 関数 (InteractibleAction から継承) TagalongAction スクリプトの機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="29811-338">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="29811-339">Gazed 時にオブジェクトをするためのビルボードを追加し、回転軸をお客様 xy のところに設定します。</span><span class="sxs-lookup"><span data-stu-id="29811-339">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="29811-340">単純な Tag-Along をオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="29811-340">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="29811-341">ここで、ソリューションが**TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="29811-341">Here's our solution, from **TagalongAction.cs**:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* <span data-ttu-id="29811-342">お試しください。</span><span class="sxs-lookup"><span data-stu-id="29811-342">Try it!</span></span> <span data-ttu-id="29811-343">ビルドして、アプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="29811-343">Build and deploy the app.</span></span>
* <span data-ttu-id="29811-344">コンテンツが、視線入力ポイントの中心を追跡する方法を見ることをブロックすることがなくが、および継続的にします。</span><span class="sxs-lookup"><span data-stu-id="29811-344">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
