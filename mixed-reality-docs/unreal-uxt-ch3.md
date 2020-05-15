---
title: 3. Mixed Reality のプロジェクト設定
description: Unreal Engine 4 と Mixed Reality Toolkit UX Tools プラグインを使用して簡単なチェス アプリを構築するチュートリアルのパート 3
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality,、チュートリアル, はじめに, mrtk, uxt, UX Tools, ドキュメント
ms.openlocfilehash: b5b5e2de787279602341e60f2bfa29aa05ea9b31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840621"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="8f3d6-104">3.Mixed Reality のプロジェクト設定</span><span class="sxs-lookup"><span data-stu-id="8f3d6-104">3. Setting up your project for mixed reality</span></span>

<span data-ttu-id="8f3d6-105">このセクションでは、Mixed Reality 開発用にアプリを構成するプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-105">This section walks you through the process of configuring your app for mixed reality development.</span></span> 

## <a name="objectives"></a><span data-ttu-id="8f3d6-106">目標</span><span class="sxs-lookup"><span data-stu-id="8f3d6-106">Objectives</span></span>

* <span data-ttu-id="8f3d6-107">ARSessionConfig、ポーン、GameMode を使用して Mixed Reality プロジェクトを設定する方法について説明する</span><span class="sxs-lookup"><span data-stu-id="8f3d6-107">Understand how to set up a mixed reality project with ARSessionConfig, Pawn, and GameMode</span></span>

## <a name="configure-the-session"></a><span data-ttu-id="8f3d6-108">セッションを構成する</span><span class="sxs-lookup"><span data-stu-id="8f3d6-108">Configure the Session</span></span>

1. <span data-ttu-id="8f3d6-109">コンテンツ ブラウザーで、**Content** フォルダーに戻ります。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-109">In the Content Browser, navigate back to the **Content** folder.</span></span> <span data-ttu-id="8f3d6-110">**[新規追加] > [その他] > [Data Asset]\(データ資産\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-110">Click **Add New > Miscellaneous > Data Asset**.</span></span> 

2. <span data-ttu-id="8f3d6-111">クラスに **ARSessionConfig** を選択し、 **[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-111">Pick **ARSessionConfig** as the class and click **Select**.</span></span> <span data-ttu-id="8f3d6-112">資産に "ARSessionConfig" という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-112">Name the asset “ARSessionConfig”.</span></span>

![データ資産を作成する](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="8f3d6-114">ARSessionConfig をダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-114">Double click ARSessionConfig to open it.</span></span> <span data-ttu-id="8f3d6-115">ARSessionConfig データ資産には、空間マッピングやオクルージョンなど、便利な AR 設定が多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-115">An ARSessionConfig data asset contains a number of useful AR settings including spatial mapping and occlusion.</span></span> <span data-ttu-id="8f3d6-116">ARSessionConfig の詳細については、Unreal Engine の [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-116">For more details on ARSessionConfig, take a look at Unreal Engine’s documentation on [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).</span></span> <span data-ttu-id="8f3d6-117">このチェス アプリでは、設定を変更する必要がないため、 **[保存]** をクリックして、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-117">For our chess app, we won’t need to modify any settings, so just hit **Save** and return to the Main window.</span></span> 

![AR セッション構成](images/unreal-uxt/3-arsessionconfig.PNG)

4. <span data-ttu-id="8f3d6-119">ビューポートの上のツールバーで、 **[Blueprints]\(ブループリント\) > [Open Level Blueprint]\(レベル ブループリントを開く\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-119">On the toolbar above the viewport, click **Blueprints > Open Level Blueprint**.</span></span> <span data-ttu-id="8f3d6-120">レベル ブループリントは、レベル全体のグローバル イベント グラフとして機能する特別なブループリントです。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-120">The Level Blueprint is a special Blueprint that acts as a level-wide global event graph.</span></span> <span data-ttu-id="8f3d6-121">ここで AR セッションを開始して、設定した AR セッション構成がレベルの開始時に適用されるようにします。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-121">We’re going to start an AR session here, so that our AR session configuration is applied at the start of the level.</span></span>  

5. <span data-ttu-id="8f3d6-122">実行ノードを **Event BeginPlay** からドラッグ アンド リリースします。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-122">Drag the execution node off **Event BeginPlay** and release.</span></span> <span data-ttu-id="8f3d6-123">**Start AR Session** ノードを検索します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-123">Search for the **Start AR Session** node.</span></span> <span data-ttu-id="8f3d6-124">**[Session Config]\(セッション構成\)** をクリックし、新しく作成した **ARSessionConfig** 資産を選択します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-124">Click on **Session Config** and select your newly created **ARSessionConfig** asset.</span></span> <span data-ttu-id="8f3d6-125">**[コンパイル]** 、 **[保存]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-125">Hit **Compile**, then **Save**.</span></span> <span data-ttu-id="8f3d6-126">メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-126">Return to the Main window.</span></span>

![AR セッションを開始する](images/unreal-uxt/3-startarsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="8f3d6-128">ポーンを作成する</span><span class="sxs-lookup"><span data-stu-id="8f3d6-128">Create a Pawn</span></span>

1.  <span data-ttu-id="8f3d6-129">Content フォルダーで、**DefaultPawn** から継承して新しいブループリントを作成します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-129">In the Content folder, create a new Blueprint that inherits from **DefaultPawn**.</span></span> <span data-ttu-id="8f3d6-130">Unreal では、ポーンはゲーム内のユーザーを表します。この場合は HoloLens 2 を使います。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-130">In Unreal, a Pawn represents the user in the game, or in this case, the HoloLens 2 experience.</span></span> <span data-ttu-id="8f3d6-131">新しいポーンの名前を "MRPawn" に変更し、MRPawn をダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-131">Rename your new Pawn “MRPawn” and double click on MRPawn to open it.</span></span> 

![DefaultPawn から継承して新しいポーンを作成する](images/unreal-uxt/3-defaultpawn.PNG)

2.  <span data-ttu-id="8f3d6-133">既定では、ポーンにメッシュ コンポーネントと衝突コンポーネントが含まれています。これは、ほとんどの Unreal プロジェクトで、ユーザーに制御されるポーンは、他のコンポーネントと衝突するソリッド オブジェクトであるからです。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-133">By default, the Pawn has a mesh component and a collision component, since in most Unreal projects, Pawns controlled by the user are solid objects that collides with other components.</span></span> <span data-ttu-id="8f3d6-134">今回の状況では、ユーザーがポーンであるため、衝突を起こさずにホログラムを通過できるようにしたいと考えています。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-134">In this situation, since the user is the Pawn, we want to be able to pass through holograms without generating collisions.</span></span> <span data-ttu-id="8f3d6-135">[コンポーネント] パネルで、**CollisionComponent** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-135">In the Components panel, select the **CollisionComponent**.</span></span> <span data-ttu-id="8f3d6-136">[詳細] パネルで、[Collision]\(衝突\) セクションまで下にスクロールし、[Collision Presets]\(衝突のプリセット\) の横にあるドロップダウンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-136">In the Details panel, scroll down to the Collision section and click the dropdown next to Collision Presets.</span></span> <span data-ttu-id="8f3d6-137">これをポーンから **[NoCollision]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-137">Change this from Pawn to **NoCollision**.</span></span> <span data-ttu-id="8f3d6-138">**MeshComponent** に対しても同じ操作を行います。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-138">Do the same for the **MeshComponent**.</span></span> <span data-ttu-id="8f3d6-139">ブループリントを**コンパイル**してから、**保存**します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-139">**Compile**, then **Save** the Blueprint.</span></span> <span data-ttu-id="8f3d6-140">メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-140">Return to the Main window.</span></span> 

![ポーンの衝突プリセットを調整する](images/unreal-uxt/3-nocollision.PNG)

## <a name="create-a-game-mode"></a><span data-ttu-id="8f3d6-142">ゲーム モードを作成する</span><span class="sxs-lookup"><span data-stu-id="8f3d6-142">Create a Game Mode</span></span>

1.  <span data-ttu-id="8f3d6-143">コンテンツ ブラウザーの Content フォルダーで、親が **Game Mode Base** の新しいブループリントを作成します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-143">In the Content folder in the Content Browser, create a new Blueprint with the parent **Game Mode Base**.</span></span> <span data-ttu-id="8f3d6-144">MRGameMode という名前を指定し、ダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-144">Name it MRGameMode and double click to open.</span></span> <span data-ttu-id="8f3d6-145">Unreal では、ゲーム モードで、使用する既定のポーンなど、ゲームやエクスペリエンスのさまざまな設定を決定します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-145">In Unreal, the Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span> 

![コンテンツ ブラウザー内の MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="8f3d6-147">[詳細] パネルで、[クラス] セクションを探します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-147">In the Details panel, locate the Classes section.</span></span> <span data-ttu-id="8f3d6-148">[Default Pawn Class]\(既定のポーン クラス\) を DefaultPawn から、先ほど作成した **MRPawn** に変更します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-148">Change the Default Pawn Class from DefaultPawn to the **MRPawn** you just created.</span></span> <span data-ttu-id="8f3d6-149">**[コンパイル]** 、 **[保存]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-149">Hit **Compile**, then **Save**.</span></span> <span data-ttu-id="8f3d6-150">メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-150">Return to the Main window.</span></span> 

![既定のポーン クラスを設定する](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="8f3d6-152">プロジェクト設定の最後の手順では、Unreal で MRGameMode を既定値に設定します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-152">The last step in setting up your project is to tell Unreal to default to MRGameMode.</span></span> <span data-ttu-id="8f3d6-153">**[編集] > [Projects Settings]\(プロジェクト設定\) > [Maps & Modes]\(マップ & モード\)** ([プロジェクト] セクション内) にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-153">Go to **Edit > Projects Settings > Maps & Modes** (in the Projects) section.</span></span> <span data-ttu-id="8f3d6-154">[Default Modes] \(既定のモード\) セクションで、ドロップダウンをクリックし、 **[MRGameMode]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-154">In the Default Modes section, click the dropdown and choose **MRGameMode**.</span></span> <span data-ttu-id="8f3d6-155">その下の [Default Maps]\(既定のマップ\) セクションで、 **[EditorStartupMap]** と **[GameDefaultMap]** を **[メイン]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-155">In the Default Maps section right below, change both the **EditorStartupMap** and the **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="8f3d6-156">これにより、エディターを閉じて再度開くと、メイン マップが既定で選択されます。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-156">This way when you close the editor and reopen it, the Main map will be selected by default.</span></span> <span data-ttu-id="8f3d6-157">同様に、ゲームのプレイ時は、メイン マップが、開始されるレベルになります。</span><span class="sxs-lookup"><span data-stu-id="8f3d6-157">Similarly, when you play the game, the Main map will be the level that is started.</span></span> 

![プロジェクト設定 - マップ & モード](images/unreal-uxt/3-mapsandmodes.PNG)

[<span data-ttu-id="8f3d6-159">次のセクション:4.シーンを対話型にする</span><span class="sxs-lookup"><span data-stu-id="8f3d6-159">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)