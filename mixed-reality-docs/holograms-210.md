---
title: MR 入力 210-宝石
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、宝石の概念の詳細を学習してください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、academy、チュートリアル、宝石
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993552"
---
>[!NOTE]
><span data-ttu-id="9548f-104">Mixed Reality Academy チュートリアルは、HoloLens (第1世代) と Mixed Reality イマーシブヘッドセットを念頭に置いて設計されています。</span><span class="sxs-lookup"><span data-stu-id="9548f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="9548f-105">そのため、これらのデバイスの開発に関するガイダンスをまだ探している開発者には、これらのチュートリアルを残しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="9548f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="9548f-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="9548f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="9548f-107">サポートされているデバイスでの作業を続行するために管理されます。</span><span class="sxs-lookup"><span data-stu-id="9548f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="9548f-108">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="9548f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="9548f-109">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="9548f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="9548f-110">MR 入力 210:視線入力</span><span class="sxs-lookup"><span data-stu-id="9548f-110">MR Input 210: Gaze</span></span>

<span data-ttu-id="9548f-111">[見つめ](gaze.md)は入力の最初の形式であり、ユーザーの意図と認識を明らかにします。</span><span class="sxs-lookup"><span data-stu-id="9548f-111">[Gaze](gaze.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="9548f-112">MR 入力 210 (プロジェクトエクスプローラーとも呼ばれます) は、Windows Mixed Reality 向けの、宝石に関連する概念について詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="9548f-112">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="9548f-113">私たちは、カーソルとホログラムにコンテキスト認識を追加し、アプリがユーザーの宝石について認識していることを最大限に活用します。</span><span class="sxs-lookup"><span data-stu-id="9548f-113">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="9548f-114">ここでは、宝石の概念を理解するのに役立つわかりやすい astronaut を用意しています。</span><span class="sxs-lookup"><span data-stu-id="9548f-114">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="9548f-115">[MR 基本 101](holograms-101.md)では、簡単なカーソルを使用して、宝石を見つめます。</span><span class="sxs-lookup"><span data-stu-id="9548f-115">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="9548f-116">現在、単純なカーソルを超えてステップを移動しています。</span><span class="sxs-lookup"><span data-stu-id="9548f-116">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="9548f-117">カーソルとホログラムを見つめています。どちらも、ユーザーが探している場所またはユーザーが探し*ていない*場所に基づいて変化します。</span><span class="sxs-lookup"><span data-stu-id="9548f-117">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="9548f-118">これにより、コンテキスト対応になります。</span><span class="sxs-lookup"><span data-stu-id="9548f-118">This makes them context-aware.</span></span>
* <span data-ttu-id="9548f-119">カーソルとホログラムにフィードバックを追加して、対象となっている内容についてユーザーにより多くのコンテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="9548f-119">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="9548f-120">このフィードバックは、オーディオとビジュアルにすることができます。</span><span class="sxs-lookup"><span data-stu-id="9548f-120">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="9548f-121">ここでは、ユーザーがより小さなターゲットをヒットするのを支援するための手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9548f-121">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="9548f-122">方向性のあるインジケーターを使用して、ユーザーの注意をホログラムに描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9548f-122">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="9548f-123">ここでは、ユーザーが世界中に移動するときに、ホログラムを使用する手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9548f-123">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="9548f-124">以下の各章に埋め込まれているビデオは、古いバージョンの Unity と Mixed Reality Toolkit を使用して記録されています。</span><span class="sxs-lookup"><span data-stu-id="9548f-124">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="9548f-125">ステップバイステップの手順は正確であり、最新のものですが、最新ではない対応するビデオにスクリプトとビジュアルが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="9548f-125">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="9548f-126">ビデオはために含まれています。ここで説明する概念は引き続き適用されます。</span><span class="sxs-lookup"><span data-stu-id="9548f-126">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="9548f-127">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="9548f-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9548f-128">まで</span><span class="sxs-lookup"><span data-stu-id="9548f-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="9548f-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9548f-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9548f-130"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="9548f-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="9548f-131">MR 入力 210:視線入力</span><span class="sxs-lookup"><span data-stu-id="9548f-131">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="9548f-132">✔️</span><span class="sxs-lookup"><span data-stu-id="9548f-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="9548f-133">✔️</span><span class="sxs-lookup"><span data-stu-id="9548f-133">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="9548f-134">開始前の準備</span><span class="sxs-lookup"><span data-stu-id="9548f-134">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9548f-135">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9548f-135">Prerequisites</span></span>

* <span data-ttu-id="9548f-136">適切な[ツールがインストール](install-the-tools.md)された WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="9548f-136">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="9548f-137">基本的なC#プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="9548f-137">Some basic C# programming ability.</span></span>
* <span data-ttu-id="9548f-138">[MR の基本 101](holograms-101.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="9548f-138">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="9548f-139">[開発用に構成され](using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。</span><span class="sxs-lookup"><span data-stu-id="9548f-139">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="9548f-140">プロジェクトファイル</span><span class="sxs-lookup"><span data-stu-id="9548f-140">Project files</span></span>

* <span data-ttu-id="9548f-141">プロジェクトに必要な[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9548f-141">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="9548f-142"> Unity 2017.2 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="9548f-142"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="9548f-143">ファイルをデスクトップまたはその他の簡単な場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="9548f-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="9548f-144">ダウンロードする前にソースコードを確認する場合は、GitHub から[入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)ます。</span><span class="sxs-lookup"><span data-stu-id="9548f-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="9548f-145">エラッタとメモ</span><span class="sxs-lookup"><span data-stu-id="9548f-145">Errata and Notes</span></span>

* <span data-ttu-id="9548f-146">Visual Studio で、コード内のブレークポイントにヒットするには、[ツール]-[> オプション] >-[デバッグ] の下にある [マイコードのみ] を無効 (オフ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9548f-146">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="9548f-147">章 1-Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="9548f-147">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="9548f-148">目的</span><span class="sxs-lookup"><span data-stu-id="9548f-148">Objectives</span></span>

* <span data-ttu-id="9548f-149">HoloLens 用 Unity の開発を最適化する。</span><span class="sxs-lookup"><span data-stu-id="9548f-149">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="9548f-150">アセットをインポートし、シーンをセットアップする。</span><span class="sxs-lookup"><span data-stu-id="9548f-150">Import assets and setup the scene.</span></span>
* <span data-ttu-id="9548f-151">HoloLens で astronaut を表示します。</span><span class="sxs-lookup"><span data-stu-id="9548f-151">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="9548f-152">手順</span><span class="sxs-lookup"><span data-stu-id="9548f-152">Instructions</span></span>

1. <span data-ttu-id="9548f-153">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="9548f-153">Start Unity.</span></span>
2. <span data-ttu-id="9548f-154">**[新しいプロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-154">Select **New Project**.</span></span>
3. <span data-ttu-id="9548f-155">プロジェクトに**Modelexplorer**という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9548f-155">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="9548f-156">以前にアーカイブしていない、場所を**見つめ**フォルダーとして入力します。</span><span class="sxs-lookup"><span data-stu-id="9548f-156">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="9548f-157">プロジェクトが **[3D]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9548f-157">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="9548f-158">**[プロジェクトの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-158">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="9548f-159">HoloLens の Unity 設定</span><span class="sxs-lookup"><span data-stu-id="9548f-159">Unity settings for HoloLens</span></span>

<span data-ttu-id="9548f-160">エクスポートしようとしているアプリが2D ビューではなく[イマーシブビュー](app-views.md)を作成する必要があることを Unity に知らせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9548f-160">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="9548f-161">これを行うには、HoloLens を仮想現実デバイスとして追加します。</span><span class="sxs-lookup"><span data-stu-id="9548f-161">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="9548f-162">**[Edit > Project Settings > Player]** にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9548f-162">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="9548f-163">[プレーヤー設定] の [**インスペクター] パネル**で、 **[Windows ストア]** アイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-163">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="9548f-164">**[XR Settings]** グループを展開します。</span><span class="sxs-lookup"><span data-stu-id="9548f-164">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="9548f-165">**[表示]** セクションで、 **[サポートされている仮想現実]** チェックボックスをオンにして、新しい**仮想現実の sdk**リストを追加します。</span><span class="sxs-lookup"><span data-stu-id="9548f-165">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="9548f-166">**[Windows Mixed Reality]** が一覧に表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9548f-166">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="9548f-167">表示されてい **+** ない場合は、一覧の下部にあるボタンを選択し、 **[Windows Holographic]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-167">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="9548f-168">次に、スクリプトバックエンドを .NET に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9548f-168">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="9548f-169">**Edit > Project Settings > Player** (これは前の手順のままである場合があります) に進みます。</span><span class="sxs-lookup"><span data-stu-id="9548f-169">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="9548f-170">[プレーヤー設定] の [**インスペクター] パネル**で、 **[Windows ストア]** アイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-170">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="9548f-171">**[その他の設定]** 構成セクションで、 **[スクリプトバックエンド]** が **[.net]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9548f-171">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="9548f-172">最後に、HoloLens で高速なパフォーマンスを実現するために品質設定を更新します。</span><span class="sxs-lookup"><span data-stu-id="9548f-172">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="9548f-173">編集 **> プロジェクトの設定** 品質 > にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9548f-173">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="9548f-174">Windows ストアアイコンの下の**既定**の行で、下向き矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-174">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="9548f-175">**Windows ストアアプリ**の場合は **[低]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-175">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="9548f-176">プロジェクト資産のインポート</span><span class="sxs-lookup"><span data-stu-id="9548f-176">Import project assets</span></span>

1. <span data-ttu-id="9548f-177">**[プロジェクト]** パネルの **[アセット]** フォルダーを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-177">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="9548f-178">**[パッケージのインポート > カスタムパッケージ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-178">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="9548f-179">ダウンロードしたプロジェクトファイルに移動し、 **Modelexplorer. unitypackage**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-179">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="9548f-180">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-180">Click **Open**.</span></span>
5. <span data-ttu-id="9548f-181">パッケージが読み込まれたら、 **[インポート]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-181">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="9548f-182">シーンを設定する</span><span class="sxs-lookup"><span data-stu-id="9548f-182">Setup the scene</span></span>

1. <span data-ttu-id="9548f-183">階層で、**メインカメラ**を削除します。</span><span class="sxs-lookup"><span data-stu-id="9548f-183">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="9548f-184">**HoloToolkit**フォルダーで、 **Input**フォルダーを開き、 **Prefabs**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="9548f-184">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="9548f-185">**MixedRealityCameraParent** Prefab を**Prefabs**フォルダーから**階層**にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="9548f-185">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="9548f-186">階層内の**指向性ライト**を右クリックし、 **[削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-186">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="9548f-187">**[ホログラム]** フォルダーで、次のアセットを**階層**のルートにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="9548f-187">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="9548f-188">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="9548f-188">**AstroMan**</span></span>
    * <span data-ttu-id="9548f-189">**ライト**</span><span class="sxs-lookup"><span data-stu-id="9548f-189">**Lights**</span></span>
    * <span data-ttu-id="9548f-190">**Space Audiosource**</span><span class="sxs-lookup"><span data-stu-id="9548f-190">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="9548f-191">**スペースの背景**</span><span class="sxs-lookup"><span data-stu-id="9548f-191">**SpaceBackground**</span></span>
6. <span data-ttu-id="9548f-192">Astronaut を表示するには、**再生モード**を開始▶します。</span><span class="sxs-lookup"><span data-stu-id="9548f-192">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="9548f-193">**再生モード**▶もう一度クリックして**停止**します。</span><span class="sxs-lookup"><span data-stu-id="9548f-193">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="9548f-194">**ホログラム**フォルダーで、[ **fitbox]** 資産を見つけて、**階層**のルートにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9548f-194">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="9548f-195">**階層** パネルで  **Fitbox チェックボックス**をオンにします。</span><span class="sxs-lookup"><span data-stu-id="9548f-195">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="9548f-196">**AstroMan**コレクションを**階層**から、 **[インスペクター]** パネルの Fitbox ボックスの **[ホログラムコレクション]** プロパティにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9548f-196">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="9548f-197">プロジェクトを保存する</span><span class="sxs-lookup"><span data-stu-id="9548f-197">Save the project</span></span>

1. <span data-ttu-id="9548f-198">新しいシーンを保存します。**ファイル > シーンを名前を付けて保存**します。</span><span class="sxs-lookup"><span data-stu-id="9548f-198">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="9548f-199">**[新しいフォルダー]** をクリックし、フォルダーに「**シーン**」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9548f-199">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="9548f-200">ファイルに "**Modelexplorer**" という名前を付け、 **[シーン]** フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="9548f-200">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="9548f-201">プロジェクトをビルドする</span><span class="sxs-lookup"><span data-stu-id="9548f-201">Build the project</span></span>

1. <span data-ttu-id="9548f-202">Unity で、 **[ファイル > ビルド設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-202">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="9548f-203">シーンを追加するには、[開いている**シーンの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-203">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="9548f-204">**[プラットフォーム]** ボックスの一覧の **[ユニバーサル Windows プラットフォーム]** を選択し、 **[プラットフォームの切り替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-204">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="9548f-205">HoloLens 向けに特に開発している場合は、**ターゲットデバイス**を**hololens**に設定します。</span><span class="sxs-lookup"><span data-stu-id="9548f-205">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="9548f-206">それ以外の場合は、**任意のデバイス**に残しておきます。</span><span class="sxs-lookup"><span data-stu-id="9548f-206">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="9548f-207">**ビルドの種類**が **[D3D]** に設定され、 **[sdk]** が **[最新のインストール済み]** に設定されていることを確認します (sdk 16299 以降である必要があります)。</span><span class="sxs-lookup"><span data-stu-id="9548f-207">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="9548f-208">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-208">Click **Build**.</span></span>
7. <span data-ttu-id="9548f-209">"App" という名前の**新しいフォルダー**を作成します。</span><span class="sxs-lookup"><span data-stu-id="9548f-209">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="9548f-210">**アプリ**フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-210">Single click the **App** folder.</span></span>
9. <span data-ttu-id="9548f-211">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-211">Press **Select Folder**.</span></span>

<span data-ttu-id="9548f-212">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9548f-212">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="9548f-213">**アプリ**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="9548f-213">Open the **App** folder.</span></span>
2. <span data-ttu-id="9548f-214">**Modelexplorer Visual Studio ソリューション**を開きます。</span><span class="sxs-lookup"><span data-stu-id="9548f-214">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="9548f-215">HoloLens に展開する場合:</span><span class="sxs-lookup"><span data-stu-id="9548f-215">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="9548f-216">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから**リリース**に変更し、ARM から**x86**に変更します。</span><span class="sxs-lookup"><span data-stu-id="9548f-216">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="9548f-217">ローカルコンピューター ボタンの横にあるドロップダウン矢印をクリックし、**リモートコンピューター** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-217">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="9548f-218">**HoloLens デバイスの IP アドレス**を入力し、[認証モード] を [**ユニバーサル (暗号化**されていないプロトコル)] に設定します。</span><span class="sxs-lookup"><span data-stu-id="9548f-218">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="9548f-219">**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-219">Click **Select**.</span></span> <span data-ttu-id="9548f-220">デバイスの IP アドレスがわからない場合は、**設定 Network & Internet > 詳細オプション >** 確認してください。</span><span class="sxs-lookup"><span data-stu-id="9548f-220">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="9548f-221">上部のメニューバーで、デバッグ、**デバッグなしで開始** の順にクリック >、Ctrl キーを押し**ながら F5**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9548f-221">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="9548f-222">初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](using-visual-studio.md#pairing-your-device-hololens)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9548f-222">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="9548f-223">アプリが展開されたら、 **select ジェスチャ**を使用して、 **[fitbox]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="9548f-223">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="9548f-224">イマーシブヘッドセットに展開する場合:</span><span class="sxs-lookup"><span data-stu-id="9548f-224">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="9548f-225">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから**リリース**に、ARM から**x64**に変更します。</span><span class="sxs-lookup"><span data-stu-id="9548f-225">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="9548f-226">配置ターゲットが**ローカルコンピューター**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9548f-226">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="9548f-227">上部のメニューバーで、デバッグ、**デバッグなしで開始** の順にクリック >、Ctrl キーを押し**ながら F5**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9548f-227">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="9548f-228">アプリがデプロイされたら、モーションコントローラーでトリガーをプルして、 **Fitbox ボックス**を閉じます。</span><span class="sxs-lookup"><span data-stu-id="9548f-228">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="9548f-229">第2章-カーソルとターゲットのフィードバック</span><span class="sxs-lookup"><span data-stu-id="9548f-229">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="9548f-230">目的</span><span class="sxs-lookup"><span data-stu-id="9548f-230">Objectives</span></span>

* <span data-ttu-id="9548f-231">カーソルの視覚的なデザインと動作。</span><span class="sxs-lookup"><span data-stu-id="9548f-231">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="9548f-232">見つめ based のカーソルフィードバック。</span><span class="sxs-lookup"><span data-stu-id="9548f-232">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="9548f-233">宝石によるホログラムフィードバック。</span><span class="sxs-lookup"><span data-stu-id="9548f-233">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="9548f-234">ここでは、いくつかのカーソルデザインの原則に基づいて作業を行います。</span><span class="sxs-lookup"><span data-stu-id="9548f-234">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="9548f-235">カーソルは常に存在します。</span><span class="sxs-lookup"><span data-stu-id="9548f-235">The cursor is always present.</span></span>
* <span data-ttu-id="9548f-236">カーソルが小さすぎるか、または大きくならないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="9548f-236">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="9548f-237">Obstructing コンテンツは避けてください。</span><span class="sxs-lookup"><span data-stu-id="9548f-237">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="9548f-238">手順</span><span class="sxs-lookup"><span data-stu-id="9548f-238">Instructions</span></span>

1. <span data-ttu-id="9548f-239">**HoloToolkit\Input\Prefabs**フォルダーで、 **inputmanager**資産を見つけます。</span><span class="sxs-lookup"><span data-stu-id="9548f-239">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="9548f-240">**Inputmanager**を**階層**にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="9548f-240">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="9548f-241">**HoloToolkit\Input\Prefabs**フォルダーで、**カーソル**アセットを見つけます。</span><span class="sxs-lookup"><span data-stu-id="9548f-241">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="9548f-242">**カーソル**を**階層**にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="9548f-242">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="9548f-243">**階層**内の**inputmanager**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-243">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="9548f-244">**インスペクター**の下部にある**カーソルオブジェクトを**、**階層**から Inputmanager の**simplesingleポインタセレクター**の**cursor**フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9548f-244">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![単純な単一ポインターセレクターの設定](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="9548f-246">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="9548f-246">Build and Deploy</span></span>

1. <span data-ttu-id="9548f-247">**ファイル > ビルド設定**からアプリをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="9548f-247">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="9548f-248">**アプリフォルダー**を開きます。</span><span class="sxs-lookup"><span data-stu-id="9548f-248">Open the **App folder**.</span></span>
3. <span data-ttu-id="9548f-249">**Modelexplorer Visual Studio ソリューション**を開きます。</span><span class="sxs-lookup"><span data-stu-id="9548f-249">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="9548f-250">[**デバッグ]、[デバッグなしで開始] の順にクリック >** 、Ctrl キーを押し**ながら F5**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9548f-250">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="9548f-251">カーソルの描画方法と、ホログラムに触れている場合の外観の変化を確認します。</span><span class="sxs-lookup"><span data-stu-id="9548f-251">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="9548f-252">手順</span><span class="sxs-lookup"><span data-stu-id="9548f-252">Instructions</span></span>

1. <span data-ttu-id="9548f-253">**[階層]** パネルで、[ **AstroMan**->**GEO_G**->**Back_Center** ] オブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="9548f-253">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="9548f-254">**Interactible.cs**をダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="9548f-254">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="9548f-255">**Interactible.cs**の**OnFocusEnter ()** および**OnFocusExit ()** コールバックの行をコメント解除します。</span><span class="sxs-lookup"><span data-stu-id="9548f-255">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="9548f-256">これらは、(宝石またはコントローラーをポイントすることによって) フォーカスが特定のオブジェクトの collider を出入りするときに、Mixed Reality Toolkit の InputManager によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9548f-256">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

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
><span data-ttu-id="9548f-257">以上を`EnableKeyword`使用`DisableKeyword`しています。</span><span class="sxs-lookup"><span data-stu-id="9548f-257">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="9548f-258">ツールキットの標準シェーダーを使用して独自のアプリでこれらを使用するには、スクリプトを使用して[マテリアルにアクセスするための Unity ガイドライン](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="9548f-258">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="9548f-259">この例では、リソースフォルダーに必要な、強調表示された[3 つの素材](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials)が既に含まれています (名前に強調表示された3つの素材を探します)。</span><span class="sxs-lookup"><span data-stu-id="9548f-259">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="9548f-260">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="9548f-260">Build and Deploy</span></span>

1. <span data-ttu-id="9548f-261">前と同様に、プロジェクトをビルドし、HoloLens にデプロイします。</span><span class="sxs-lookup"><span data-stu-id="9548f-261">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="9548f-262">1つのオブジェクトを対象としていて、そうでない場合はどうなるかを観察します。</span><span class="sxs-lookup"><span data-stu-id="9548f-262">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="9548f-263">章 3-ターゲット手法</span><span class="sxs-lookup"><span data-stu-id="9548f-263">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="9548f-264">目的</span><span class="sxs-lookup"><span data-stu-id="9548f-264">Objectives</span></span>

* <span data-ttu-id="9548f-265">ホログラムを簡単にターゲット設定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9548f-265">Make it easier to target holograms.</span></span>
* <span data-ttu-id="9548f-266">自然な移動を安定化します。</span><span class="sxs-lookup"><span data-stu-id="9548f-266">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="9548f-267">手順</span><span class="sxs-lookup"><span data-stu-id="9548f-267">Instructions</span></span>

1. <span data-ttu-id="9548f-268">**[階層]** パネルで、 **inputmanager**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-268">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="9548f-269">**[インスペクター]** パネルで、**宝石**のスクリプトを見つけます。</span><span class="sxs-lookup"><span data-stu-id="9548f-269">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="9548f-270">表示する場合は、これをクリックして Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="9548f-270">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="9548f-271">このスクリプトは、Raycast データのサンプルに対して反復処理を行い、精度のターゲット設定のためにユーザーの宝石を安定化するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9548f-271">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="9548f-272">**インスペクター**では、 **[保存された安定性のサンプル]** の値を編集できます。</span><span class="sxs-lookup"><span data-stu-id="9548f-272">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="9548f-273">この値は、安定板が、安定値を計算するために反復処理するサンプルの数を表します。</span><span class="sxs-lookup"><span data-stu-id="9548f-273">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="9548f-274">Chapter 4 方向インジケーター</span><span class="sxs-lookup"><span data-stu-id="9548f-274">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="9548f-275">目的</span><span class="sxs-lookup"><span data-stu-id="9548f-275">Objectives</span></span>

* <span data-ttu-id="9548f-276">ホログラムの検索に役立つように、カーソルに方向インジケーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="9548f-276">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="9548f-277">手順</span><span class="sxs-lookup"><span data-stu-id="9548f-277">Instructions</span></span>

<span data-ttu-id="9548f-278">**DirectionIndicator.cs**ファイルを次のように使用します。</span><span class="sxs-lookup"><span data-stu-id="9548f-278">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="9548f-279">ユーザーがホログラムを見ていない場合は、方向インジケーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="9548f-279">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="9548f-280">ユーザーがホログラムでの表示を切り替えている場合は、方向インジケーターを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="9548f-280">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="9548f-281">ホログラムをポイントするように方向インジケーターを更新します。</span><span class="sxs-lookup"><span data-stu-id="9548f-281">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="9548f-282">では、始めましょう。</span><span class="sxs-lookup"><span data-stu-id="9548f-282">Let's get started.</span></span>

1. <span data-ttu-id="9548f-283">**階層**パネルで**AstroMan**オブジェクトをクリックし、**矢印をクリック**して展開します。</span><span class="sxs-lookup"><span data-stu-id="9548f-283">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="9548f-284">**[階層]** パネルで、[ **AstroMan**] の [方向] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-284">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="9548f-285">**[インスペクター]** パネルで、 **[コンポーネントの追加]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="9548f-286">メニューで、検索ボックスの**方向インジケーター**を入力します。</span><span class="sxs-lookup"><span data-stu-id="9548f-286">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="9548f-287">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-287">Select the search result.</span></span>
5. <span data-ttu-id="9548f-288">**[階層]** パネルで、 **Cursor**オブジェクトを**インスペクター**の**cursor**プロパティにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="9548f-288">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="9548f-289">**[プロジェクト]** パネルの **[ホログラム]** フォルダーで、 **Direction Alindicator**資産を**インスペクター**の**指向性インジケーター**プロパティにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="9548f-289">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="9548f-290">アプリをビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="9548f-290">Build and deploy the app.</span></span>
8. <span data-ttu-id="9548f-291">ディレクショナルインジケーターオブジェクトを使用して astronaut を見つける方法をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9548f-291">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="9548f-292">章 5-Billboarding</span><span class="sxs-lookup"><span data-stu-id="9548f-292">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="9548f-293">目的</span><span class="sxs-lookup"><span data-stu-id="9548f-293">Objectives</span></span>

* <span data-ttu-id="9548f-294">Billboarding を使用して、ホログラムが常に直面するようにします。</span><span class="sxs-lookup"><span data-stu-id="9548f-294">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="9548f-295">**Billboard.cs**ファイルを使用して、ユーザーに常に接続されていることを示すために、そのオブジェクトの向きを維持します。</span><span class="sxs-lookup"><span data-stu-id="9548f-295">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="9548f-296">**[階層]** パネルで、 **AstroMan**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-296">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="9548f-297">**[インスペクター]** パネルで、 **[コンポーネントの追加]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-297">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="9548f-298">メニューで、[検索] ボックスに「**ビルボード**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9548f-298">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="9548f-299">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-299">Select the search result.</span></span>
4. <span data-ttu-id="9548f-300">**インスペクター**で、**ピボット軸**を**Y**に設定します。</span><span class="sxs-lookup"><span data-stu-id="9548f-300">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="9548f-301">お試しください。</span><span class="sxs-lookup"><span data-stu-id="9548f-301">Try it!</span></span> <span data-ttu-id="9548f-302">以前と同じように、アプリをビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="9548f-302">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="9548f-303">ビルボードオブジェクトがどのように視点を変更するかに関係なく、どのように表示されるかを確認します。</span><span class="sxs-lookup"><span data-stu-id="9548f-303">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="9548f-304">ここでは、 **AstroMan**からスクリプトを削除します。</span><span class="sxs-lookup"><span data-stu-id="9548f-304">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="9548f-305">Chapter 6-タグに沿って</span><span class="sxs-lookup"><span data-stu-id="9548f-305">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="9548f-306">目的</span><span class="sxs-lookup"><span data-stu-id="9548f-306">Objectives</span></span>

* <span data-ttu-id="9548f-307">タグを使用して、ホログラムが部屋の周りをたどるようにします。</span><span class="sxs-lookup"><span data-stu-id="9548f-307">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="9548f-308">この問題に対処する際には、次の設計上の制約があります。</span><span class="sxs-lookup"><span data-stu-id="9548f-308">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="9548f-309">コンテンツは常に一目でわかるはずです。</span><span class="sxs-lookup"><span data-stu-id="9548f-309">Content should always be a glance away.</span></span>
* <span data-ttu-id="9548f-310">コンテンツは使用できません。</span><span class="sxs-lookup"><span data-stu-id="9548f-310">Content should not be in the way.</span></span>
* <span data-ttu-id="9548f-311">ヘッドロックコンテンツは不快になります。</span><span class="sxs-lookup"><span data-stu-id="9548f-311">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="9548f-312">ここで使用するソリューションでは、"タグに沿った" 方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="9548f-312">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="9548f-313">タグに沿ったオブジェクトは、ユーザーのビューを完全に離れることができません。</span><span class="sxs-lookup"><span data-stu-id="9548f-313">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="9548f-314">タグは、ユーザーの先頭にラバーバンドでアタッチされたオブジェクトであると考えることができます。</span><span class="sxs-lookup"><span data-stu-id="9548f-314">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="9548f-315">ユーザーが移動すると、完全に離れることなく、ビューの端に向かってスライドします。</span><span class="sxs-lookup"><span data-stu-id="9548f-315">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="9548f-316">ユーザーがタグに沿って gazes すると、より完全に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9548f-316">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="9548f-317">**SimpleTagalong.cs**ファイルを次のように使用します。</span><span class="sxs-lookup"><span data-stu-id="9548f-317">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="9548f-318">タグに沿ったオブジェクトがカメラの境界内にあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="9548f-318">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="9548f-319">視錐ビュー内にない場合は、タグを、視錐のビュー内で部分的に配置します。</span><span class="sxs-lookup"><span data-stu-id="9548f-319">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="9548f-320">それ以外の場合は、ユーザーからの既定の距離にタグを配置します。</span><span class="sxs-lookup"><span data-stu-id="9548f-320">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="9548f-321">これを行うには、まず、 **Interactible.cs**スクリプトを変更して**TagalongAction**を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="9548f-321">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="9548f-322">コード演習 6. a (コメント解除行 84 ~ 87) を実行して**Interactible.cs**を編集します。</span><span class="sxs-lookup"><span data-stu-id="9548f-322">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="9548f-323">**InteractibleAction.cs**スクリプトは、 **Interactible.cs**と組み合わせて、ホログラムをタップしたときにカスタムアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="9548f-323">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="9548f-324">この例では、タグに対して特に使用します。</span><span class="sxs-lookup"><span data-stu-id="9548f-324">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="9548f-325">**Scripts**フォルダーで、[ **TagalongAction.cs** asset] をクリックして Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="9548f-325">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="9548f-326">コーディングの演習を完了するか、次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="9548f-326">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="9548f-327">**階層**の最上位にある検索バーに「 **ChestButton_Center** 」と入力し、結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-327">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="9548f-328">**[インスペクター]** パネルで、 **[コンポーネントの追加]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9548f-328">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="9548f-329">メニューの [検索 **] ボックスに**、「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9548f-329">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="9548f-330">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-330">Select the search result.</span></span>
  * <span data-ttu-id="9548f-331">[**ホログラム**フォルダー] で、資産の**タグ**を検索します。</span><span class="sxs-lookup"><span data-stu-id="9548f-331">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="9548f-332">**階層**内の**ChestButton_Center**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="9548f-332">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="9548f-333">**プロジェクト** パネルの  **tagalong**オブジェクトを、プロパティ  にある **オブジェクト** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="9548f-333">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="9548f-334">**インスペクター**の**tagalong アクション**オブジェクトを、 **Interactible**スクリプトの**Interactible action**フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9548f-334">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="9548f-335">**TagalongAction**スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="9548f-335">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interactible のセットアップ](images/holograms210-interactible.png)

<span data-ttu-id="9548f-337">次のものを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9548f-337">We need to add the following:</span></span>

* <span data-ttu-id="9548f-338">TagalongAction スクリプトの実行時関数に機能を追加します (InteractibleAction から継承)。</span><span class="sxs-lookup"><span data-stu-id="9548f-338">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="9548f-339">Billboarding を gazed オブジェクトに追加し、pivot 軸を XY に設定します。</span><span class="sxs-lookup"><span data-stu-id="9548f-339">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="9548f-340">次に、単純なタグをオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="9548f-340">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="9548f-341">**TagalongAction.cs**のソリューションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9548f-341">Here's our solution, from **TagalongAction.cs**:</span></span>

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

* <span data-ttu-id="9548f-342">お試しください。</span><span class="sxs-lookup"><span data-stu-id="9548f-342">Try it!</span></span> <span data-ttu-id="9548f-343">アプリをビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="9548f-343">Build and deploy the app.</span></span>
* <span data-ttu-id="9548f-344">コンテンツが注視点の中心に沿っているかどうかを監視しますが、継続的にはブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="9548f-344">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
