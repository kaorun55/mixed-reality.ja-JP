---
title: 動的なコンテンツの配置とソルバー MR Learning ベース モジュール
description: このコースでは、複合現実のアプリケーション内で Azure の顔認識機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 複合現実、unity、チュートリアル、hololens
ms.openlocfilehash: b212812beeff54bb1f92ccbcc923ab9c301945b7
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929556"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a><span data-ttu-id="43c7a-104">動的なコンテンツの配置とソルバー MR Learning ベース モジュール</span><span class="sxs-lookup"><span data-stu-id="43c7a-104">MR Learning Base Module - Dynamic Content Placement and Solvers</span></span>

<span data-ttu-id="43c7a-105">ホログラム、生きるように、HoloLens 2 で直感的に、ユーザーをフォローし、相互作用は、シームレスかつ洗練された方法で、物理環境に配置されます。</span><span class="sxs-lookup"><span data-stu-id="43c7a-105">Holograms come to life in the HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="43c7a-106">レッスン 3 では「ソルバー」と呼ばれる MRTK の使用可能な配置ツールを使用してホログラムを動的に配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-106">In Lesson 3, we will explore ways to dynamically place holograms using the MRTK’s available placement tools, known as "solvers."</span></span> <span data-ttu-id="43c7a-107">これらは、複雑な空間配置アルゴリズムを解決する方法を「ソルバー」と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="43c7a-107">They are known as "solvers" for the way they solve complex spatial placement algorithms.</span></span> <span data-ttu-id="43c7a-108">MRTK ソルバーは、システムのスクリプトと動作をフォローして、ユーザーまたはその他のゲーム オブジェクト、シーン内の UI 要素を許可するようにするために使用します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-108">In the MRTK, solvers are a system of scripts and behaviors that we use to be able to allow UI elements to follow you, the user or other game objects in the scene.</span></span> <span data-ttu-id="43c7a-109">こともできますを迅速に特定の位置にスナップより直感的なアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span> 

## <a name="objectives"></a><span data-ttu-id="43c7a-110">目標</span><span class="sxs-lookup"><span data-stu-id="43c7a-110">Objectives</span></span>

* <span data-ttu-id="43c7a-111">MRTK のソルバーを紹介します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-111">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="43c7a-112">ボタンのコレクションにソルバーを使用して、ユーザーをフォローします。</span><span class="sxs-lookup"><span data-stu-id="43c7a-112">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="43c7a-113">ゲーム オブジェクトを持つソルバーを使用して次のユーザーの追跡対象の手</span><span class="sxs-lookup"><span data-stu-id="43c7a-113">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="43c7a-114">手順</span><span class="sxs-lookup"><span data-stu-id="43c7a-114">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="43c7a-115">MRTK ソルバーの場所</span><span class="sxs-lookup"><span data-stu-id="43c7a-115">Location of solvers in the MRTK</span></span>
 <span data-ttu-id="43c7a-116">次の図に示すように、プロジェクトで使用可能なソルバーを検索、utilities フォルダーの下で、MRTK SDK フォルダー (MixedRealityToolkit.SDK フォルダー) で検索するには、ソルバー フォルダーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="43c7a-116">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder), then under the utilities folder you will see the solvers folder, as shown in the image below.</span></span>

![ソルバー](images/lesson3_chapter1_step1im.PNG)

><span data-ttu-id="43c7a-118">注:このレッスンでは、「回転のこぎり」ソルバーおよび"RadialView"ソルバーの実装を上回ることが変わりますのみ。</span><span class="sxs-lookup"><span data-stu-id="43c7a-118">Note: In this lesson we will only go over implementation of the "Orbital" solver and the "RadialView" solver.</span></span> <span data-ttu-id="43c7a-119">ソルバー、MRTK で使用できるさまざまなについての詳細についてには、以下を参照してください。 https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span><span class="sxs-lookup"><span data-stu-id="43c7a-119">To learn more about the full range of solvers available in the MRTK, please visit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="43c7a-120">問題を解くプログラムを使用して、ユーザーをフォローするには</span><span class="sxs-lookup"><span data-stu-id="43c7a-120">Use a Solver to Follow the User</span></span>
<span data-ttu-id="43c7a-121">この章の目的は、ように、ユーザーの視線方向続くに以前に作成したボタンのコレクションを強化するためにです。</span><span class="sxs-lookup"><span data-stu-id="43c7a-121">The goal of this chapter is to enhance the button collection we previously created such that it follows the user’s gaze direction.</span></span> <span data-ttu-id="43c7a-122">MRTK と HoloToolkit の以前のバージョンでこの、"taglong"機能としてに呼ばれていました。</span><span class="sxs-lookup"><span data-stu-id="43c7a-122">In previous version of the MRTK and HoloToolkit, this was referred to as a "taglong" functionality.</span></span>

1. <span data-ttu-id="43c7a-123">前のレッスンからボタン コレクションの親オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-123">Select the Button Collection parent object from the previous lesson.</span></span>

![Lesson3 第 2 章 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="43c7a-125">Inspector パネルで、「させます。」の検索と"コンポーネントの追加 ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="43c7a-125">In the inspector panel, click the "add component" button and search for "orbital."</span></span> <span data-ttu-id="43c7a-126">回転のこぎりコンポーネントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="43c7a-126">The orbital component should appear.</span></span> <span data-ttu-id="43c7a-127">回転のこぎりコンポーネントをボタン コレクションのゲーム オブジェクトに追加することを選択します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-127">Select it to add the orbital component to the Button Collection game object.</span></span>

![Lesson3 第 2 章 Step2im](images/Lesson3_Chapter2_step2im.PNG)

><span data-ttu-id="43c7a-129">注:コンポーネントを追加すると、システムが inspector タブで、必要なコンポーネントである、回転のこぎりスクリプトおよびソルバー ハンドラー スクリプトを追加することがわかります。</span><span class="sxs-lookup"><span data-stu-id="43c7a-129">Note: When you add the component you will notice that the system adds the orbital script and the solver handler script in the inspector tab, which is a required component.</span></span> 

3. <span data-ttu-id="43c7a-130">次の調整を実装するのユーザーをフォローするボタンのコレクションを構成するには (くださいは次の図も参照)。</span><span class="sxs-lookup"><span data-stu-id="43c7a-130">In order to configure the button collection to follow the user, we need to implement the following adjustments (please also refer to the image below):</span></span>
- <span data-ttu-id="43c7a-131">回転のこぎりのスクリプトでは、「ヨーのみです。」を「向きの種類」のドロップダウン リストを設定します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-131">In the Orbital script, set the "orientation type" drop-down list to "Yaw Only."</span></span> <span data-ttu-id="43c7a-132">これにより、ユーザーを次のように、オブジェクトの 1 つだけその軸が回転するため。</span><span class="sxs-lookup"><span data-stu-id="43c7a-132">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
- <span data-ttu-id="43c7a-133">すべての軸で、ローカルのオフセットを 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-133">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="43c7a-134">X に世界中のオフセットを設定 = 0、y =-0.1 と z = 0.6 です。</span><span class="sxs-lookup"><span data-stu-id="43c7a-134">Set the World Offset to x = 0, y = -0.1 and z = 0.6.</span></span> <span data-ttu-id="43c7a-135">これにより、オブジェクトは、環境に関するユーザーが移動すると、ユーザーに従うことを許可する一方で、物理環境、高さを固定する引き続き高さを変更するときなど、オブジェクトの移動がロックされます。</span><span class="sxs-lookup"><span data-stu-id="43c7a-135">This locks movement of the object such that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="43c7a-136">Wade 一連の動作を実現するために、これらの値を調整することがあります。</span><span class="sxs-lookup"><span data-stu-id="43c7a-136">These values may be adjusted to achieve a wade range of behaviors.</span></span>
- <span data-ttu-id="43c7a-137">これにより、ボタンのみ後で次のユーザーのビュー、ユーザーが自分の頭が十分にに従って動作するためには、「の世界のオフセット角度ステップを使用して」チェック ボックスをオン可能性があります (注。このタイトル可能性がありますに切り捨てる一部の画面では、下の画像であるためです。)たとえば、ユーザー-90 にのみ、オブジェクトには、設定ステップ数 (左側の例では、緑色の矢印でマークされた) 4 に等しい。</span><span class="sxs-lookup"><span data-stu-id="43c7a-137">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the "Use Angle Stepping for world offset" checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example to the left).</span></span> 

![Lesson3 第 2 章 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="43c7a-139">追跡対象の手に従うオブジェクトの有効化</span><span class="sxs-lookup"><span data-stu-id="43c7a-139">Enabling Objects to Follow Tracked Hands</span></span>

<span data-ttu-id="43c7a-140">このセクションでは、以下の RadialView ソルバーを使用して、ユーザーの追跡対象の手に以前に作成したキューブのゲーム オブジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-140">In this section, we will configure the cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="43c7a-141">BaseScene 階層では、キューブ オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-141">Select the cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="43c7a-142">Inspector パネルの「コンポーネントの追加」をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43c7a-142">Click "add component" in the inspector panel.</span></span> 

![Lesson3 第 3 章 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. <span data-ttu-id="43c7a-144">"RadialView"検索ボックスに入力し、キューブに追加する RadialView コンポーネントを選択します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-144">Type in "RadialView" in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="43c7a-145">ソルバーのハンドラ コンポーネントは、キューブに自動的に追加もします。</span><span class="sxs-lookup"><span data-stu-id="43c7a-145">The solver handler component will also be automatically added to the cube.</span></span>

3. <span data-ttu-id="43c7a-146">ヘッドに従っていないが、以下の左側にある放射状のビューを変更します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-146">Change the radial view to not follow the head but follow the left hand.</span></span> <span data-ttu-id="43c7a-147">「参照するオブジェクトを追跡」オプションの横にあるドロップダウン メニューを選択します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-147">Select the dropdown menu next to the "tracked object to reference" option.</span></span> <span data-ttu-id="43c7a-148">メニューから「ジョイントが左を渡す」を選択します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-148">Then select "hand joint left" from the menu.</span></span>

![Lesson3 第 3 章 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. <span data-ttu-id="43c7a-150">ハンド ジョイントを選択すると、キューブにたいして手のアイコンのどの部分を選択できます。</span><span class="sxs-lookup"><span data-stu-id="43c7a-150">Once you select the hand joint, you can choose which part of the hand you want the cube to follow.</span></span> <span data-ttu-id="43c7a-151">この例では、手首を使用するでしょう。</span><span class="sxs-lookup"><span data-stu-id="43c7a-151">For this example, we are going to use the wrist.</span></span> <span data-ttu-id="43c7a-152">オプションの横にあるは、「追跡手ジョイント」は、ドロップダウン メニューを選択し、手首を選択します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-152">Next to the option "tracked hand joint" select the dropdown menu and select wrist.</span></span> 

![Lesson3 第 3 章 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. <span data-ttu-id="43c7a-154">キューブがユーザーのリストとの間の距離があるないように、最大および最小の距離を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-154">Set the maximum and minimum distances to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="43c7a-155">一度設定すると、キューブが一直線手首をします。</span><span class="sxs-lookup"><span data-stu-id="43c7a-155">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="43c7a-156">場合 (たとえば、ユーザーのリストでの回転、"回転と追跡 Object"への参照の方向を設定するオブジェクトを許可するには) キューブが方向にはどのように動作を調整する「参照方向」フィールドを調整することも可能性があります。</span><span class="sxs-lookup"><span data-stu-id="43c7a-156">You may also adjust the "Reference Direction" field to adjust the behavior of how the cube is oriented (e.g., if you would like to allow the object to rotate with the user's wrist, set the reference direction to "Orient with Tracked Object")</span></span>

![Lesson3 第 3 章 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a><span data-ttu-id="43c7a-158">おめでとうございます</span><span class="sxs-lookup"><span data-stu-id="43c7a-158">Congratulations</span></span>
<span data-ttu-id="43c7a-159">これで終了です。</span><span class="sxs-lookup"><span data-stu-id="43c7a-159">Congratulations!</span></span> <span data-ttu-id="43c7a-160">このレッスンでは、直感的に、ユーザーをフォロー ui MRTK のソルバーを使用する方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="43c7a-160">In this lesson, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="43c7a-161">次のユーザーの追跡対象の手をゲーム オブジェクト (つまり、キューブ) に問題を解くプログラムをアタッチする方法も学習しました。</span><span class="sxs-lookup"><span data-stu-id="43c7a-161">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="43c7a-162">これらの機能と、MRTK に含まれているその他のソルバーの詳細については、自由にアクセスしてください、 [MRTK ソルバー ドキュメント ページ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)します。</span><span class="sxs-lookup"><span data-stu-id="43c7a-162">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="43c7a-163">次のレッスン:3D オブジェクトの相互作用</span><span class="sxs-lookup"><span data-stu-id="43c7a-163">Next Lesson: 3D Object Interaction</span></span>](mrlearning-base-ch4.md)

