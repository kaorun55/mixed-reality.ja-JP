---
title: 3. Mixed Reality のプロジェクト設定
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 3
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: d22c3d8c9048f53171298642768877d7bcdcb972
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330297"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="212d6-104">3.Mixed Reality のプロジェクト設定</span><span class="sxs-lookup"><span data-stu-id="212d6-104">3. Setting up your project for mixed reality</span></span>

## <a name="overview"></a><span data-ttu-id="212d6-105">概要</span><span class="sxs-lookup"><span data-stu-id="212d6-105">Overview</span></span>

<span data-ttu-id="212d6-106">前のチュートリアルでは、チェス アプリ プロジェクトの設定に時間を費やしました。</span><span class="sxs-lookup"><span data-stu-id="212d6-106">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="212d6-107">このセクションでは、Mixed Reality 開発用にアプリを設定する手順について説明します。これは、AR セッションを追加することを意味します。</span><span class="sxs-lookup"><span data-stu-id="212d6-107">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="212d6-108">このタスクには ARSessionConfig データ資産を使用します。この資産には、空間マッピングやオクルージョンなどの便利な AR 設定が多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="212d6-108">You'll be using an ARSessionConfig data asset for this task, which has a lot of useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="212d6-109">さらに詳しく知りたい場合は、Unreal Engine のドキュメントに、[ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) 資産と [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) クラスの詳細が記載されています。</span><span class="sxs-lookup"><span data-stu-id="212d6-109">If you want to dive deeper, the Unreal Engine documentation has more details on the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class.</span></span>

## <a name="objectives"></a><span data-ttu-id="212d6-110">目標</span><span class="sxs-lookup"><span data-stu-id="212d6-110">Objectives</span></span>
* <span data-ttu-id="212d6-111">Unreal Engine の AR 設定の操作</span><span class="sxs-lookup"><span data-stu-id="212d6-111">Working with Unreal Engine's AR settings</span></span> 
* <span data-ttu-id="212d6-112">ARSessionConfig データ資産の使用</span><span class="sxs-lookup"><span data-stu-id="212d6-112">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="212d6-113">ポーンとゲーム モードの設定</span><span class="sxs-lookup"><span data-stu-id="212d6-113">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="212d6-114">セッション資産の追加</span><span class="sxs-lookup"><span data-stu-id="212d6-114">Adding the session asset</span></span>
<span data-ttu-id="212d6-115">Unreal の AR セッションは、それ自体では発生しません。</span><span class="sxs-lookup"><span data-stu-id="212d6-115">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="212d6-116">セッションを使用するには、次の作業として使用する ARSessionConfig データ資産が必要です。</span><span class="sxs-lookup"><span data-stu-id="212d6-116">To use a session you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="212d6-117">**[コンテンツ ブラウザー]** で、 **[新規追加] > [その他] > [Data Asset]\(データ資産\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="212d6-117">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="212d6-118">ルートの **[コンテンツ]** フォルダー レベルであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="212d6-118">Make sure you're at the root **Content** folder level.</span></span> 
    * <span data-ttu-id="212d6-119">**ARSessionConfig** を選択し、 **[選択]** をクリックして、アセットに **ARSessionConfig** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="212d6-119">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![データ資産を作成する](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="212d6-121">**ARSessionConfig** をダブルクリックして開き、既定の設定をすべてそのままにして、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="212d6-121">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="212d6-122">メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="212d6-122">Return to the Main window.</span></span> 

![AR セッション構成](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="212d6-124">これが完了したら、次のステップとして、レベルが読み込まれたときに AR セッションが開始されるようにします。</span><span class="sxs-lookup"><span data-stu-id="212d6-124">With that done, your next step is to make sure that the AR session starts when the level loads.</span></span> <span data-ttu-id="212d6-125">さいわい、Unreal には、**レベル ブループリント**と呼ばれる特別な種類のブループリントがあり、レベル全体のグローバル イベント グラフとして機能します。</span><span class="sxs-lookup"><span data-stu-id="212d6-125">Luckily, Unreal has a special kind of blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="212d6-126">**レベル ブループリント**で ARSessionConfig アセットを接続すると、ゲームの再生が開始されたときに AR セッションが正常に起動します。</span><span class="sxs-lookup"><span data-stu-id="212d6-126">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="212d6-127">エディタのツールバーから、 **[ブループリント] > [レベル ブループリントを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="212d6-127">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span> 

![オープン レベルのブループリント](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="212d6-129">実行ノード (左向き矢印アイコン) を **Event BeginPlay** からドラッグ アンド リリースします。</span><span class="sxs-lookup"><span data-stu-id="212d6-129">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release.</span></span> <span data-ttu-id="212d6-130">**AR セッションを開始する**を検索し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="212d6-130">Search for the **Start AR Session** and hit enter.</span></span>  
    * <span data-ttu-id="212d6-131">**[セッション構成]** の下にある **[アセットの選択]** ドロップダウンをクリックし、**ARSessionConfig** アセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="212d6-131">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span> 
    * <span data-ttu-id="212d6-132">**[コンパイル]** 、 **[保存]** をクリックして、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="212d6-132">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![AR セッションを開始する](images/unreal-uxt/3-start-ar-session.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="212d6-134">ポーンを作成する</span><span class="sxs-lookup"><span data-stu-id="212d6-134">Create a Pawn</span></span>
<span data-ttu-id="212d6-135">この時点では、プロジェクトにはまだプレーヤー オブジェクトが必要です。</span><span class="sxs-lookup"><span data-stu-id="212d6-135">At this point, the project still needs a player object.</span></span> <span data-ttu-id="212d6-136">Unreal では、**ポーン**はゲーム内のユーザーを表しますが、この場合は HoloLens 2 になります。</span><span class="sxs-lookup"><span data-stu-id="212d6-136">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="212d6-137">**[コンテンツ]** フォルダーで、 **[新規追加] > [ブループリント クラス]** をクリックし、下部にある **[すべてのクラス]** セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="212d6-137">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="212d6-138">**DefaultPawn** を検索し、 **[選択]** をクリックして、アセットをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="212d6-138">Search for **DefaultPawn**, click **Select** and double-click the asset to open.</span></span> 

![DefaultPawn から継承して新しいポーンを作成する](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> <span data-ttu-id="212d6-140">既定では、ポーンにはメッシュと衝突コンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="212d6-140">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="212d6-141">ほとんどの Unreal プロジェクトでは、ポーンは他のコンポーネントと競合する可能性のあるソリッド オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="212d6-141">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="212d6-142">ポーンとユーザーは Mixed Reality で同じであるため、衝突せずにホログラムを通過できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="212d6-142">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span> 

2. <span data-ttu-id="212d6-143">**[コンポーネント]** パネルから **CollisionComponent** を選択し、 **[詳細]** パネルの **[衝突]** セクションまでスクロールします。</span><span class="sxs-lookup"><span data-stu-id="212d6-143">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span> 
    * <span data-ttu-id="212d6-144">**[衝突プリセット]** ドロップダウンをクリックして、値を **NoCollision** に変更します。</span><span class="sxs-lookup"><span data-stu-id="212d6-144">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span> 
    * <span data-ttu-id="212d6-145">**MeshComponent** についても同じ操作を行い、ブループリントを**コンパイル**し、 **保存**します。</span><span class="sxs-lookup"><span data-stu-id="212d6-145">Do the same for the **MeshComponent**, then **Compile** and **Save** the Blueprint.</span></span> 

![ポーンの衝突プリセットを調整する](images/unreal-uxt/3-nocollision.PNG)

<span data-ttu-id="212d6-147">ここで作業を完了したら、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="212d6-147">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="212d6-148">ゲーム モードを作成する</span><span class="sxs-lookup"><span data-stu-id="212d6-148">Create a Game Mode</span></span>
<span data-ttu-id="212d6-149">Mixed Reality セットアップの最後のステップはゲーム モードです。</span><span class="sxs-lookup"><span data-stu-id="212d6-149">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="212d6-150">ゲーム モードでは、使用する既定のポーンなど、ゲームやエクスペリエンスのさまざまな設定を決定します。</span><span class="sxs-lookup"><span data-stu-id="212d6-150">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="212d6-151">**[コンテンツ]** フォルダーで、 **[新規追加] > [ブループリント クラス]** をクリックし、下部にある **[すべてのクラス]** セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="212d6-151">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="212d6-152">**Game Mode Base** を検索し、**MRGameMode** という名前を指定し、ダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="212d6-152">Search for **Game Mode Base**, name it **MRGameMode** and double-click to open.</span></span> 

![コンテンツ ブラウザー内の MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="212d6-154">**[詳細]** パネルの **[クラス]** セクションに移動し、 **[既定のポーン クラス]** を **MRPawn** に変更します。</span><span class="sxs-lookup"><span data-stu-id="212d6-154">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span> 
    * <span data-ttu-id="212d6-155">**[コンパイル]** 、 **[保存]** をクリックして、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="212d6-155">Hit **Compile**, then **Save** and return to the Main window.</span></span> 

![既定のポーン クラスを設定する](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="212d6-157">**[編集] > [プロジェクトの設定]** を選択し、左側のリストで **[マップとモード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="212d6-157">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span> 
    * <span data-ttu-id="212d6-158">**[既定モード]** を展開し、 **[既定のゲーム モード]** を **MRGameMode** に変更します。</span><span class="sxs-lookup"><span data-stu-id="212d6-158">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span> 
    * <span data-ttu-id="212d6-159">**[既定のマップ]** を展開し、**EditorStartupMap** と **GameDefaultMap** の両方を **[メイン]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="212d6-159">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="212d6-160">このようにして、エディターを閉じて再度開くか、ゲームをプレイしたときに、メイン マップが既定で選択されます。</span><span class="sxs-lookup"><span data-stu-id="212d6-160">This way when you close and reopen the editor, or play the game, the Main map will be selected by default.</span></span>

![プロジェクト設定 - マップ & モード](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="212d6-162">プロジェクトで Mixed Reality を完全にセットアップしたら、次のチュートリアルに進み、シーンにユーザー入力を追加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="212d6-162">With the project fully setup for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span> 

[<span data-ttu-id="212d6-163">次のセクション: 4.シーンを対話型にする</span><span class="sxs-lookup"><span data-stu-id="212d6-163">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)