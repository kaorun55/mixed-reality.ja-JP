---
title: 5. ボタンの追加およびピースの位置のリセット
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアルのパート 5
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: df5ea22e7097fdd3b788ec298bc1cd78c315b585
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840401"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="2497a-104">5.ボタンの追加およびピースの位置のリセット</span><span class="sxs-lookup"><span data-stu-id="2497a-104">5. Adding a button & resetting piece locations</span></span>

<span data-ttu-id="2497a-105">このセクションでは、Mixed Reality ツールキット UX ツール プラグインの機能のデモンストレーションと、チェス アプリの機能の構築について引き続き説明します。</span><span class="sxs-lookup"><span data-stu-id="2497a-105">This section continues demonstrating the capabilities of the Mixed Reality Toolkit UX Tools plugin and building out the features of your chess app.</span></span> <span data-ttu-id="2497a-106">新しい関数を作成し、使用しているレベルからアクターへの参照をブループリントに取り込む方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="2497a-106">You’ll create a new function and learn how to get references to Actors from your Level into a Blueprint.</span></span>

## <a name="objectives"></a><span data-ttu-id="2497a-107">目標</span><span class="sxs-lookup"><span data-stu-id="2497a-107">Objectives</span></span>

* <span data-ttu-id="2497a-108">プロジェクトにボタンを追加する</span><span class="sxs-lookup"><span data-stu-id="2497a-108">Add a button to your project</span></span>
* <span data-ttu-id="2497a-109">ピースを元の位置に戻す新しい "Reset Location" 関数を作成する</span><span class="sxs-lookup"><span data-stu-id="2497a-109">Create a new “Reset Location” function that sends a piece back to its original location</span></span>
* <span data-ttu-id="2497a-110">押されたときに新しく作成された関数をトリガーするボタンをフックする</span><span class="sxs-lookup"><span data-stu-id="2497a-110">Hook the button up to trigger the newly created function when pressed</span></span>

## <a name="create-a-function-to-reset-location"></a><span data-ttu-id="2497a-111">位置をリセットする関数を作成する</span><span class="sxs-lookup"><span data-stu-id="2497a-111">Create a function to reset location</span></span>

1.  <span data-ttu-id="2497a-112">**WhiteKing** を開きます。</span><span class="sxs-lookup"><span data-stu-id="2497a-112">Open **WhiteKing**.</span></span> <span data-ttu-id="2497a-113">**[My Blueprint]\(マイ ブループリント\)** パネルで、 **[Functions]\(関数\)** セクションの横の [+] ボタンをクリックして新しい関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="2497a-113">In the **My Blueprint** panel, click the “+” button next to the **Functions** section to create a new function.</span></span> <span data-ttu-id="2497a-114">この関数に "Reset Location" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="2497a-114">Name this function “Reset Location”.</span></span> 

2.  <span data-ttu-id="2497a-115">新しく作成した **Reset Location** ブループリントで、実行ピンをドラッグし、ブループリント グリッドの任意の場所でリリースして **SetActorRelativeTransform** ノードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2497a-115">In your newly created **Reset Location** Blueprint, drag the execution pin and release anywhere on the Blueprint grid to call a **SetActorRelativeTransform** node.</span></span> <span data-ttu-id="2497a-116">この関数では、アクターの親に対して相対的に変換 (位置、回転、スケール) を設定します。</span><span class="sxs-lookup"><span data-stu-id="2497a-116">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="2497a-117">この関数を使用すると、ボードが元の位置から移動した場合でもボード上のキングの位置がリセットされます。</span><span class="sxs-lookup"><span data-stu-id="2497a-117">We’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span> <span data-ttu-id="2497a-118">位置が X = -26、Y = 4、Z = 0 に設定された **Make Transform** ノードを作成し、新しい相対変換入力に接続します。</span><span class="sxs-lookup"><span data-stu-id="2497a-118">Create a **Make Transform** node with Location X = -26, Y = 4, Z = 0, and connect it to the New Relative Transform input.</span></span> 

![Reset Location (位置のリセット) 関数](images/unreal-uxt/5-function.PNG)

3.  <span data-ttu-id="2497a-120">**WhiteKing** をコンパイルして保存します。</span><span class="sxs-lookup"><span data-stu-id="2497a-120">Compile and Save **WhiteKing**.</span></span> <span data-ttu-id="2497a-121">メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="2497a-121">Return to the Main window.</span></span> 

## <a name="add-a-button"></a><span data-ttu-id="2497a-122">ボタンを追加する</span><span class="sxs-lookup"><span data-stu-id="2497a-122">Add a button</span></span>

1.  <span data-ttu-id="2497a-123">**Blueprints** フォルダーに、SimpleButton をサブクラス化する新しいブループリントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2497a-123">In your **Blueprints** folder, create a new Blueprint that subclasses SimpleButton.</span></span> <span data-ttu-id="2497a-124">SimpleButton は、UX ツール プラグインの一部として提供される 3D ボタンのブループリント アクターです。</span><span class="sxs-lookup"><span data-stu-id="2497a-124">SimpleButton is a 3D button Blueprint Actor that is provided as part of the UX Tools plugin.</span></span> <span data-ttu-id="2497a-125">このボタンに "ResetButton" という名前を付け、ダブルクリックしてブループリントを開きます。</span><span class="sxs-lookup"><span data-stu-id="2497a-125">Name this button “ResetButton” and double click to open the Blueprint.</span></span> 

![SimpleButton から新しいブループリントをサブクラス化する](images/unreal-uxt/5-subclass.PNG)

2.  <span data-ttu-id="2497a-127">**[コンポーネント]** パネルで、 **[PressableButton (Inherited)]\(PressableButton (継承)\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2497a-127">In the **Components** panel, click on **PressableButton (Inherited)**.</span></span> <span data-ttu-id="2497a-128">[詳細] パネルで、 **[イベント]** セクションが表示されるまでスクロールします。</span><span class="sxs-lookup"><span data-stu-id="2497a-128">In the Details panel, scroll until you see the **Events** section.</span></span> <span data-ttu-id="2497a-129">**[On Button Pressed]\(ボタンが押されたとき\)** の横にある緑色のプラスのボタンをクリックします。これにより、ボタンが押されたときに呼び出される **[On Button Pressed]\(ボタンが押されたとき\)** イベントがイベント グラフに追加されます。</span><span class="sxs-lookup"><span data-stu-id="2497a-129">Click the green plus button next to **On Button Pressed**- this will add an **On Button Pressed** event to the Event Graph, which will be called when the button is pressed.</span></span> <span data-ttu-id="2497a-130">ここから、WhiteKing の Reset Location 関数を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2497a-130">From here, we’ll want to call our WhiteKing’s Reset Location function.</span></span> <span data-ttu-id="2497a-131">これを行うには、まず、このレベルでの WhiteKing アクターへの参照を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2497a-131">To do this, we’ll first need to get a reference to the WhiteKing Actor in our Level.</span></span> 

3.  <span data-ttu-id="2497a-132">**[My Blueprint]\(マイ ブループリント\)** パネルで、 **[変数]** セクションを見つけ、 **+** ボタンをクリックして新しい変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="2497a-132">In the **My Blueprint** panel, find the **Variables** section and click the **+** button to add a new variable.</span></span> <span data-ttu-id="2497a-133">この変数に "WhiteKing" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="2497a-133">Name this variable “WhiteKing”.</span></span> <span data-ttu-id="2497a-134">[Details]\(詳細\) パネルで、 **[Variable Type]\(変数の種類\)** の横にあるドロップダウンを選択し、"WhiteKing" を検索して、 **[Object Reference]\(オブジェクト参照\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2497a-134">In the Details panel, select the dropdown next to **Variable Type**, search for “WhiteKing”, and select the **Object Reference**.</span></span> <span data-ttu-id="2497a-135">最後に、 **[Instance Editable]\(インスタンス編集可能\)** の横のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2497a-135">Finally, check the box next to **Instance Editable**.</span></span> <span data-ttu-id="2497a-136">これにより、変数をメイン レベルから設定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2497a-136">This will allow the variable to be set from the Main Level.</span></span> 

![変数を作成する](images/unreal-uxt/5-var.PNG)

4.  <span data-ttu-id="2497a-138">WhiteKing 変数を **[My Blueprint]\(マイ ブループリント\) > [Variables]\(変数\)** から Simple Button イベント グラフにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2497a-138">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Simple Button Event Graph.</span></span> <span data-ttu-id="2497a-139">**[Get WhiteKing]\(WhiteKing の取得\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2497a-139">Choose **Get WhiteKing**.</span></span> 

5.  <span data-ttu-id="2497a-140">WhiteKing の出力ピンをドラッグしてリリースし、新しいノードを配置します。</span><span class="sxs-lookup"><span data-stu-id="2497a-140">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="2497a-141">**Reset Location** 関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="2497a-141">Select the **Reset Location** function.</span></span> <span data-ttu-id="2497a-142">最後に、 **[On Button Pressed]\(ボタンが押されたとき\)** から出力実行ピンを **[Reset Location]** の入力実行ピンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2497a-142">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="2497a-143">ResetButton ブループリントの **[Compile]\(コンパイル\)** と **[Save]\(保存\)** の後、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="2497a-143">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span> 

![On Button Pressed (ボタンが押されたとき) から Reset Location 関数を呼び出す](images/unreal-uxt/5-callresetloc.PNG)

6.  <span data-ttu-id="2497a-145">**SimpleButton** をビューポートにドラッグし、その位置を X = 50、Y = -25、Z = 10 に設定します。</span><span class="sxs-lookup"><span data-stu-id="2497a-145">Drag **SimpleButton** into the viewport and set its location to X = 50, Y = -25, Z = 10.</span></span> <span data-ttu-id="2497a-146">**[Default]\(既定\)** で、WhiteKing 変数の値を **WhiteKing** に設定します。</span><span class="sxs-lookup"><span data-stu-id="2497a-146">Under **Default**, set the value of the WhiteKing variable to **WhiteKing**.</span></span>

![変数の値を設定する](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="2497a-148">これで、グラブ可能なチェス ピースとボードを備えた Mixed Reality アプリと、押されたときにピースの位置をリセットする、完全に機能するボタンが完成しました。</span><span class="sxs-lookup"><span data-stu-id="2497a-148">You now have a mixed reality app with a grabbable chess piece and board, as well as a fully functioning button that will reset the piece’s location when pressed.</span></span> <span data-ttu-id="2497a-149">この時点まで完成したアプリを [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="2497a-149">The completed app up to this point can be found on [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp).</span></span> <span data-ttu-id="2497a-150">このチュートリアルをさらに進めて、ユーザーがボタンを押したときにボード全体がリセットされるように、チェスの残りのピースを設定してみてください。</span><span class="sxs-lookup"><span data-stu-id="2497a-150">Feel free to go beyond this tutorial and set up the remainder of the chess pieces, so that the entire board is reset when the user presses the button.</span></span>

![ビューポートの終わりのシーン](images/unreal-uxt/5-endscene.PNG)

[<span data-ttu-id="2497a-152">次のセクション: 6.デバイスまたはエミュレーターのパッケージ化およびデプロイ</span><span class="sxs-lookup"><span data-stu-id="2497a-152">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)