---
title: 2. プロジェクトと最初のアプリケーションの初期化
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリをビルドするためのチュートリアルのパート 2
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, 機能, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: fc85f011ff3b186f3b4b5449b4f8ec49f0b6418f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851576"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="1d740-104">2.プロジェクトと最初のアプリケーションの初期化</span><span class="sxs-lookup"><span data-stu-id="1d740-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="1d740-105">このセクションでは、HoloLens 2 用の新しい Unreal アプリケーションの作成を開始します。</span><span class="sxs-lookup"><span data-stu-id="1d740-105">This section gets you started with creating a new Unreal application for HoloLens 2.</span></span> 

## <a name="objectives"></a><span data-ttu-id="1d740-106">目標</span><span class="sxs-lookup"><span data-stu-id="1d740-106">Objectives</span></span>

* <span data-ttu-id="1d740-107">HoloLens 開発用に Unreal を構成する</span><span class="sxs-lookup"><span data-stu-id="1d740-107">Configure Unreal for HoloLens development</span></span>
* <span data-ttu-id="1d740-108">アセットをインポートし、シーンをセットアップする</span><span class="sxs-lookup"><span data-stu-id="1d740-108">Import assets and set up the scene</span></span>

## <a name="create-a-new-unreal-project"></a><span data-ttu-id="1d740-109">新しい Unreal プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="1d740-109">Create a new Unreal project</span></span>

1. <span data-ttu-id="1d740-110">Unreal Engine を起動します。</span><span class="sxs-lookup"><span data-stu-id="1d740-110">Launch Unreal Engine</span></span>

2. <span data-ttu-id="1d740-111">**[New Project Categories]\(新規プロジェクトのカテゴリ\)** で、 **[ゲーム]** を選択して [次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-111">Under **New Project Categories**, select **Games** and click Next.</span></span> <span data-ttu-id="1d740-112">**[Blank]\(空のプロジェクト\)** テンプレートを選択して [次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-112">Select a **Blank** Template and click Next.</span></span> 

![[Blank]\(空のプロジェクト\) テンプレートを選択する](images/unreal-uxt/2-template.PNG)

3. <span data-ttu-id="1d740-114">[Project Settings]\(プロジェクト設定\) で、 **[C++]、[Scalable 3D or 2D]\(3D または 2D に拡張可能\)、[Mobile / Tablet]\(モバイル/タブレット\)** 、 **[No Starter Content]\(スターター コンテンツを有効にしない\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1d740-114">In Project Settings, choose **C++, Scalable 3D or 2D, Mobile / Tablet**, and **No Starter Content**.</span></span> <span data-ttu-id="1d740-115">プロジェクトを保存する場所を選択して、 **[Create Project]\(プロジェクトを作成\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-115">Select a location for your project to be saved and click **Create Project**.</span></span> <span data-ttu-id="1d740-116">これにより、Visual Studio プロジェクト内の C++ ファイルと Unreal エディターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d740-116">This will open up your C++ files in a Visual Studio project and the Unreal editor.</span></span> 

![最初のプロジェクト設定](images/unreal-uxt/2-project-settings.PNG)

4. <span data-ttu-id="1d740-118">左上隅の **[編集] > [プラグイン]** に移動します。</span><span class="sxs-lookup"><span data-stu-id="1d740-118">In the top left-hand corner, go to **Edit > Plugins**.</span></span> <span data-ttu-id="1d740-119">[Augmented Reality]\(拡張現実\) で、 **[HoloLens]** プラグインを有効にするボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1d740-119">Under Augmented Reality, check the box to enable the **HoloLens** plugin.</span></span> <span data-ttu-id="1d740-120">[Virtual Reality]\(仮想現実\) セクションまで下にスクロールして、 **[Microsoft Windows Mixed Reality]** プラグインを有効にするボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1d740-120">Scroll down to the Virtual Reality section and check the box to enable the **Microsoft Windows Mixed Reality** plugin.</span></span> <span data-ttu-id="1d740-121">HoloLens 2 の開発には、両方のプラグインが必要です。</span><span class="sxs-lookup"><span data-stu-id="1d740-121">Both plugins are required for HoloLens 2 development.</span></span> <span data-ttu-id="1d740-122">エディターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="1d740-122">Restart your editor.</span></span> 

![プラグイン](images/unreal-uxt/2-plugins.PNG)

5. <span data-ttu-id="1d740-124">左上隅の **[ファイル] > [New Level]\(新規レベル\)** に移動します。</span><span class="sxs-lookup"><span data-stu-id="1d740-124">In the top left-hand corner, go to **File > New Level**.</span></span> <span data-ttu-id="1d740-125">**[Empty Level]\(空のレベル\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1d740-125">Select **Empty Level**.</span></span> <span data-ttu-id="1d740-126">この時点では、ビューポートの既定のシーンは空です。</span><span class="sxs-lookup"><span data-stu-id="1d740-126">The default scene in the viewport should now be empty.</span></span>

6. <span data-ttu-id="1d740-127">左側の [モード] パネルの [基本] タブにある PlayerStart をドラッグ アンド ドロップします。アプリの起動時にユーザーを原点から開始させるために、右側の [詳細] パネルで、位置を X = 0、Y = 0、Z = 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="1d740-127">Drag PlayerStart and drop PlayerStart from the Modes panel on the left, located in the Basic tab. In the Details panel on the right, set the location to X = 0, Y = 0, Z = 0 in order to have the user start at the origin when the app stars.</span></span>

![PlayerStart を表示したビューポート](images/unreal-uxt/2-playerstart.PNG)

7. <span data-ttu-id="1d740-129">**[Cube]\(キューブ\)** を [モード] パネルの [基本] タブからビューポートにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1d740-129">Drag a **Cube** from the Basic tab of the Modes panel into the viewport.</span></span> <span data-ttu-id="1d740-130">[詳細] パネルで、位置を X = 50、Y = 0、Z = 0 に設定して、キューブをプレーヤーの開始位置から 50 cm 離して配置します。</span><span class="sxs-lookup"><span data-stu-id="1d740-130">In the Details panel, set the location to X = 50, Y = 0, Z = 0 to set the cube to 50 cm away from the player at start time.</span></span> <span data-ttu-id="1d740-131">既定のキューブは非常に大きいため、キューブの [Scale]\(スケール\) を (0.2, 0.2, 0.2) に変更します。</span><span class="sxs-lookup"><span data-stu-id="1d740-131">Since the default cube is quite large, change the Scale of the cube to (0.2, 0.2, 0.2).</span></span> 

8. <span data-ttu-id="1d740-132">シーンにライトを追加しない限り、キューブを表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="1d740-132">You won’t be able to see the cube unless you add a light to your scene.</span></span> <span data-ttu-id="1d740-133">[モード] パネルの **[Lights]\(ライト\)** タブに切り替えて、**Directional Light** をシーンの PlayerStart の上にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1d740-133">Switch to the **Lights** tab on the Modes panel and drag a **Directional Light** into the scene, above the PlayerStart.</span></span>

![ライトが追加されたビューポート](images/unreal-uxt/2-light.PNG)

9.  <span data-ttu-id="1d740-135">ツールバーの **[Play]\(プレイ\)** ボタンを押して、ビューポートにキューブを表示します。</span><span class="sxs-lookup"><span data-stu-id="1d740-135">Press the **Play** button on the toolbar to see your cube in the viewport!</span></span> <span data-ttu-id="1d740-136">**Esc** キーを押して、レベルを停止します。</span><span class="sxs-lookup"><span data-stu-id="1d740-136">Press **Esc** to stop the level.</span></span> 

![ビューポート内のキューブ](images/unreal-uxt/2-cube.PNG)

10. <span data-ttu-id="1d740-138">レベルを保存しましょう。</span><span class="sxs-lookup"><span data-stu-id="1d740-138">Let’s save your level.</span></span> <span data-ttu-id="1d740-139">左上隅の **[ファイル] > [Save Current]\(現在のレベルを保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-139">In the top left corner, click on **File > Save Current**.</span></span> <span data-ttu-id="1d740-140">レベルに "Main" という名前を付けて、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-140">Name your level "Main" and click **Save**.</span></span> 

## <a name="set-up-a-chess-scene"></a><span data-ttu-id="1d740-141">チェス シーンを設定する</span><span class="sxs-lookup"><span data-stu-id="1d740-141">Set up a chess scene</span></span>

1. <span data-ttu-id="1d740-142">コンテンツ ブラウザーで、[Add New]\(新規追加\) の下にあるアイコンをクリックして、ソース パネルを表示します。</span><span class="sxs-lookup"><span data-stu-id="1d740-142">In your Content Browser, click icon under Add New to show the sources panel.</span></span> <span data-ttu-id="1d740-143">**[Add New]\(新規追加\) > [New Folder]\(新規フォルダ\)** をクリックして、フォルダーに "ChessAssets" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="1d740-143">Then click on **Add New > New Folder** and name the folder “ChessAssets”.</span></span> <span data-ttu-id="1d740-144">このフォルダーをダブルクリックして、移動します。</span><span class="sxs-lookup"><span data-stu-id="1d740-144">Double-click this folder to navigate in.</span></span> <span data-ttu-id="1d740-145">ここに、チェス セットの 3D アセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="1d740-145">This is where we’ll import the 3D assets for our chess set.</span></span>

![ソース パネルの表示と非表示](images/unreal-uxt/2-showhidesources.PNG)

2. <span data-ttu-id="1d740-147">アセットの zip ファイルを [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) からダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="1d740-147">Download the zip file of assets from [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z).</span></span> <span data-ttu-id="1d740-148">このファイルには、チェス盤とチェス セットの 3D モデルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1d740-148">This file contains the 3D models for a chess board and chess set.</span></span> <span data-ttu-id="1d740-149">このファイルを解凍します。</span><span class="sxs-lookup"><span data-stu-id="1d740-149">Unzip this file.</span></span>

3. <span data-ttu-id="1d740-150">コンテンツ ブラウザーの上部にある **[インポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-150">At the top of the Content Browser, click on **Import**.</span></span> <span data-ttu-id="1d740-151">解凍したばかりのフォルダーに移動して、その中のすべての項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="1d740-151">Navigate to the folder that you just unzipped and select all the items within.</span></span> <span data-ttu-id="1d740-152">このフォルダーには、チェス盤とチェスの駒の 3D オブジェクト メッシュである FBX ファイルと、チェス盤と駒のマテリアルの作成に使用するテクスチャ マップである TGA ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1d740-152">This folder contains FBX files which are the 3D object meshes for our chess board and pieces, as well as TGA files which are the texture maps we’ll use to create materials for our board and pieces.</span></span> <span data-ttu-id="1d740-153">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-153">Click **Open**.</span></span> 

4. <span data-ttu-id="1d740-154">[FBX Import Options]\(FBX インポート オプション\) ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d740-154">An FBX Import Options window will pop up.</span></span> <span data-ttu-id="1d740-155">**[Material]\(マテリアル\)** セクションで、 **[Material Import Method]\(マテリアルのインポート方法\)** を **[Do Not Create Material]\(マテリアルを作成しない\)** に変更します。</span><span class="sxs-lookup"><span data-stu-id="1d740-155">In the **Material** section, change the **Material Import Method** to **Do Not Create Material**.</span></span> <span data-ttu-id="1d740-156">次に、 **[Import All]\(すべてインポート\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-156">Then, click **Import All**.</span></span>

![FBX インポート オプション](images/unreal-uxt/2-nocreatemat.PNG)

5. <span data-ttu-id="1d740-158">[コンテンツ] フォルダーに戻って、**Blueprints** という名前の新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d740-158">Back in your Content folder, create a new folder called **Blueprints**.</span></span> <span data-ttu-id="1d740-159">ここに、すべてのブループリントを格納します。ブループリントは、新しい種類のアクターやスクリプト レベルのイベントを作成するためのノードベースのインターフェイスを提供する特別なアセットです。</span><span class="sxs-lookup"><span data-stu-id="1d740-159">This is where we will store all our blueprints, which are special assets that provide a node-based interface to create new types of Actors and script level events.</span></span> 

6. <span data-ttu-id="1d740-160">**[Blueprints]\(ブループリント\)** フォルダーをダブルクリックして、内部に移動し、[Content Browser]\(コンテンツ ブラウザー\) を右クリックして、 **[Blueprint Class]\(ブループリント クラス\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1d740-160">Double click the **Blueprints** folder to navigate inside, then right click in your Content Browser and select **Blueprint Class**.</span></span> <span data-ttu-id="1d740-161">**[Actor]\(アクター\)** をクリックして、新しいブループリントに "Board" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="1d740-161">Click on **Actor** and name the new blueprint “Board”.</span></span> <span data-ttu-id="1d740-162">Board をダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="1d740-162">Double click Board to open it.</span></span> 

![ブループリントの親クラスを選択する](images/unreal-uxt/2-bpparent.PNG)

![新しい Board ブループリント](images/unreal-uxt/2-bpboard.PNG)

7. <span data-ttu-id="1d740-165">ブループリント エディターで、[コンポーネント] パネルに移動し、 **[Add Component]\(コンポーネントの追加\) > [シーン]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-165">In the Blueprint editor, navigate to the Components panel and click **Add Component > Scene**.</span></span> <span data-ttu-id="1d740-166">新しく作成したシーンに "Root" という名前を付け、Root をクリックして、DefaultSceneRoot の上にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1d740-166">Name the newly created scene “Root”, and then click and drag Root over the DefaultSceneRoot.</span></span> <span data-ttu-id="1d740-167">これにより、既定のシーンがルートに置き換えられて、ビューポートで球が削除されます。</span><span class="sxs-lookup"><span data-stu-id="1d740-167">This will replace the default scene root and get rid of the sphere in the viewport.</span></span> 

![ルートを置き換える](images/unreal-uxt/2-root.PNG)

8. <span data-ttu-id="1d740-169">**[Add Component]\(コンポーネントの追加\)** を再度クリックし、今度は **[Static Mesh]\(スタティック メッシュ\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1d740-169">Click **Add Component** again, and this time choose **Static Mesh**.</span></span> <span data-ttu-id="1d740-170">新しいスタティック メッシュに "SM_Board" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="1d740-170">Name the new static mesh “SM_Board”.</span></span> 

![スタティック メッシュの追加](images/unreal-uxt/2-sm-board.PNG)

9. <span data-ttu-id="1d740-172">**[詳細]** パネルで **[Static Mesh]\(スタティック メッシュ\)** セクションを見つけて、ドロップダウンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-172">In the **Details** panel, locate the **Static Mesh** section and click the dropdown.</span></span> <span data-ttu-id="1d740-173">**ChessBoard** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1d740-173">Select **ChessBoard**.</span></span> 

![ビューポート内のボード メッシュ](images/unreal-uxt/2-sm-board-view.PNG)

10. <span data-ttu-id="1d740-175">**[詳細]** パネルのままで、 **[Materials]\(マテリアル\)** セクションを見つけて、ドロップダウンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-175">Still in the **Details** panel, locate the **Materials** section and click the dropdown.</span></span> <span data-ttu-id="1d740-176">**[Create New Asset]\(アセットの新規作成\)** で、 **[Material]\(マテリアル\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1d740-176">Under **Create New Asset**, select **Material**.</span></span> <span data-ttu-id="1d740-177">このアセットに **M_ChessBoard** という名前を付けて、**ChessAssets**フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="1d740-177">Name this asset **M_ChessBoard** and save it in the **ChessAssets** folder.</span></span> 

![新しいマテリアルを作成する](images/unreal-uxt/2-newmat.PNG)

11. <span data-ttu-id="1d740-179">M_ChessBoard ドロップダウンの横に表示された四角形をダブルクリックして、新しく作成した M_ChessBoard マテリアルを開きます。</span><span class="sxs-lookup"><span data-stu-id="1d740-179">Double click the square next to M_ChessBoard dropdown to open your newly created M_ChessBoard material.</span></span> <span data-ttu-id="1d740-180">マテリアル エディターで右クリックして、 **[Texture Sample]\(テクスチャ サンプル\)** ノードを検索します。</span><span class="sxs-lookup"><span data-stu-id="1d740-180">In the Material Editor, right click and search for the **Texture Sample** node.</span></span> <span data-ttu-id="1d740-181">**[詳細]** パネルの **[Material Expression Texture Base]\(マテリアル式テクスチャ ベース\)** セクションでドロップダウンをクリックして、**ChessBoard_Albedo** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1d740-181">In the **Details** panel under the **Material Expression Texture Base** section, click the dropdown and select **ChessBoard_Albedo**.</span></span> <span data-ttu-id="1d740-182">最後に、 **[RGB]** 出力ピンを **M_ChessBoard** の [Base Color]\(基本色\) ピンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1d740-182">Finally, drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![基本色を設定する](images/unreal-uxt/2-boardalbedomat.PNG)

12. <span data-ttu-id="1d740-184">同じ手順をさらに 4 回実行して、**ChessBoard_AO** テクスチャ サンプルを **[Ambient Occlusion]\(アンビエント オクルージョン\)** ピンに、**ChessBoard_Metal** テクスチャ サンプルを **[Metallic]\(メタリック\)** ピンに、**ChessBoard_Normal** テクスチャ サンプルを **[Normal]\(ノーマル\)** ピンに、**ChessBoard_Rough** テクスチャ サンプルを **[Roughness]\(ラフネス\)** ピンにリンクします。</span><span class="sxs-lookup"><span data-stu-id="1d740-184">Do the same four more times, linking the **ChessBoard_AO** Texture Sample to the **Ambient Occlusion** pin, the **ChessBoard_Metal** Texture Sample to the **Metallic** pin, the **ChessBoard_Normal** Texture Sample to the **Normal** pin, and the **ChessBoard_Rough** Texture Sample to the **Roughness** pin.</span></span> <span data-ttu-id="1d740-185">**[Save]** (保存) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-185">Click **Save**.</span></span> 

![残りのテクスチャを接続する](images/unreal-uxt/2-boardmat.PNG)

13. <span data-ttu-id="1d740-187">**Board** ブループリントに戻ります。</span><span class="sxs-lookup"><span data-stu-id="1d740-187">Return to your **Board** Blueprint.</span></span> <span data-ttu-id="1d740-188">作成したばかりのマテリアルがブループリントに適用されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="1d740-188">You should see that the material you just created has been applied to your Blueprint.</span></span> <span data-ttu-id="1d740-189">チェス盤をシーンに配置した後、それが適切なサイズで適切な位置に配置されるようにするには、チェス盤の **[Scale]\(スケール\)** を (0.05, 0.05, 0.05) に変更し、 **[回転]** を Z = 90 に変更します。</span><span class="sxs-lookup"><span data-stu-id="1d740-189">To ensure the board is at a reasonable size and position once we place it in our scene, change the **Scale** of the board to (0.05, 0.05, 0.05) and the **Rotation** to Z = 90.</span></span> <span data-ttu-id="1d740-190">上部のツールバーで **[コンパイル]** 、 **[保存]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-190">In the toolbar at the top, click **Compile**, then **Save**.</span></span> <span data-ttu-id="1d740-191">メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="1d740-191">Return to your Main window.</span></span> 

![マテリアルが適用されたチェス盤](images/unreal-uxt/2-chessboard.PNG)

14. <span data-ttu-id="1d740-193">次に、キューブを削除して、それを新しく作成した Board アクターに置き換えましょう。</span><span class="sxs-lookup"><span data-stu-id="1d740-193">Let’s now delete the cube and replace it with your newly created Board actor.</span></span> <span data-ttu-id="1d740-194">**[World Outliner]\(ワールド アウトライナー\)** で、 **[Cube]\(キューブ\) を右クリックして、[編集]、[削除]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d740-194">In the **World Outliner**, right click your **Cube > Edit > Delete**.</span></span> <span data-ttu-id="1d740-195">Board をコンテンツ ブラウザーからビューポートにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1d740-195">Drag Board from your Content Browser into the viewport.</span></span> <span data-ttu-id="1d740-196">チェス盤の位置を X = 80、Y = 0、Z = -20 に設定します。</span><span class="sxs-lookup"><span data-stu-id="1d740-196">Set the location of the board to X = 80, Y = 0, Z = -20.</span></span> 

15. <span data-ttu-id="1d740-197">**[Play]\(プレイ\)** ボタンをクリックして、新しいチェス盤をレベルに表示します。</span><span class="sxs-lookup"><span data-stu-id="1d740-197">Click the **Play** button to view your new board in your level.</span></span> <span data-ttu-id="1d740-198">**Esc** キーを押してエディターに戻ります。</span><span class="sxs-lookup"><span data-stu-id="1d740-198">Press **Esc** to return to the editor.</span></span> 

16. <span data-ttu-id="1d740-199">次に、チェス盤の作成と同じ手順に従って、チェスの駒を作成します。ただし、今度は、チェスの駒のメッシュとマテリアルを選択します。</span><span class="sxs-lookup"><span data-stu-id="1d740-199">Now we’ll follow the same steps to create a chess piece as we did with the board, this time selecting the mesh and material for the chess piece:</span></span>

    <span data-ttu-id="1d740-200">a) コンテンツ ブラウザーの [ブループリント] フォルダーに移動して、アクター型の新しいブループリント クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d740-200">a) Navigate to the Blueprints folder in the Content Browser and create a new Blueprint class of type Actor.</span></span> <span data-ttu-id="1d740-201">このアクターに "WhiteKing" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="1d740-201">Name this actor “WhiteKing”.</span></span>

    <span data-ttu-id="1d740-202">b) WhiteKing をダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="1d740-202">b) Double click WhiteKing to open it.</span></span> <span data-ttu-id="1d740-203">"Root" という名前の新しいシーンを追加し、それを使用して DefaultSceneRoot を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1d740-203">Add a new Scene component named “Root” and use it to replace DefaultSceneRoot.</span></span> 

    <span data-ttu-id="1d740-204">c) "SM_King" という名前の新しいスタティック メッシュ コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="1d740-204">c) Add a new Static Mesh component named “SM_King”.</span></span> <span data-ttu-id="1d740-205">[詳細] パネルで、 **[Static Mesh]\(スタティック メッシュ\)** を **Chess_King** に設定し、 **[Material]\(マテリアル\)** を、**M_ChessWhite**という名前の新しいマテリアルに設定します。</span><span class="sxs-lookup"><span data-stu-id="1d740-205">In the Details panel, set the **Static Mesh** to **Chess_King** and the **Material** to a new Material called **M_ChessWhite**.</span></span> 

    <span data-ttu-id="1d740-206">d) 新しい **M_ChessWhite**マテリアルを開いて、関連テクスチャをその対応するマテリアル入力に接続します。</span><span class="sxs-lookup"><span data-stu-id="1d740-206">d) Open the new **M_ChessWhite** Material and hook up the relevant textures to their corresponding material inputs.</span></span> 

    ![チェスのキングのマテリアルを作成する](images/unreal-uxt/2-chesskingmat.PNG)

    <span data-ttu-id="1d740-208">e) **WhiteKing** ブループリントに戻って、 **[Scale]\(スケール\)** を (0.05, 0.05, 0.05) に、 **[回転]** を Z = 90 に変更します。</span><span class="sxs-lookup"><span data-stu-id="1d740-208">e) Back in your **WhiteKing** Blueprint, change the **Scale** to (0.05, 0.05, 0.05) and **Rotation** to Z = 90.</span></span>

    <span data-ttu-id="1d740-209">f) ブループリントをコンパイルして保存した後、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="1d740-209">f) Compile and save your blueprint, then navigate back to your main window.</span></span> 

17. <span data-ttu-id="1d740-210">WhiteKing をビューポートにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1d740-210">Drag WhiteKing into your viewport.</span></span> <span data-ttu-id="1d740-211">**[World Outliner]\(ワールド アウトライナー\)** で、WhiteKing を Board にドラッグします。これにより、WhiteKing は Board の子になります。</span><span class="sxs-lookup"><span data-stu-id="1d740-211">In the **World Outliner**, drag WhiteKing onto Board so that WhiteKing is now a child of Board.</span></span> 

![[World Outliner]\(ワールド アウトライナー\)](images/unreal-uxt/2-child.PNG)

18. <span data-ttu-id="1d740-213">**[詳細]** パネルの **[Transform]\(トランスフォーム\)** で、WhiteKing の **[Location]\(位置\)** を X = -26、Y = 4、Z = 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="1d740-213">In the **Details** panel under **Transform**, set the **Location** of WhiteKing to X = -26, Y = 4, Z = 0</span></span>

19. <span data-ttu-id="1d740-214">**[Play]\(プレイ\)** をクリックして、レベルを表示します。</span><span class="sxs-lookup"><span data-stu-id="1d740-214">Click **Play** to see your level.</span></span> <span data-ttu-id="1d740-215">**Esc** キーを押して終了します。</span><span class="sxs-lookup"><span data-stu-id="1d740-215">Press **Esc** to exit.</span></span> 

[<span data-ttu-id="1d740-216">次のセクション: 3.Mixed Reality 用のプロジェクト設定</span><span class="sxs-lookup"><span data-stu-id="1d740-216">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)