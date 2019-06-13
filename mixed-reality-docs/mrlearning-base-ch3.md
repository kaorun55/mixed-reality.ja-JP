---
title: MR 学習ベース モジュール - ダイナミック コンテンツの配置とソルバー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, チュートリアル, hololens
ms.openlocfilehash: 6f05b2cecd388b1b2f13e7e5228bc90091eee3bd
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66270399"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a><span data-ttu-id="1ca78-104">MR 学習ベース モジュール - ダイナミック コンテンツの配置とソルバー</span><span class="sxs-lookup"><span data-stu-id="1ca78-104">MR Learning Base Module - Dynamic Content Placement and Solvers</span></span>

<span data-ttu-id="1ca78-105">ホログラムは HoloLens 2 で現実のものとなります。ホログラムは直感的にユーザーを追跡し、滑らかで洗練された操作ができるように物理環境に配置されます。</span><span class="sxs-lookup"><span data-stu-id="1ca78-105">Holograms come to life in the HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="1ca78-106">レッスン 3 では、「ソルバー」として知られる MRTK で使用できる配置ツールを使用して、ホログラムを動的に配置する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-106">In Lesson 3, we will explore ways to dynamically place holograms using the MRTK’s available placement tools, known as "solvers."</span></span> <span data-ttu-id="1ca78-107">「ソルバー」と呼ばれているのは、複雑な空間配置アルゴリズムを解決することができるからです。</span><span class="sxs-lookup"><span data-stu-id="1ca78-107">They are known as "solvers" for the way they solve complex spatial placement algorithms.</span></span> <span data-ttu-id="1ca78-108">MRTK では、ソルバーとは、UI 要素がシーン内で自分、ユーザー、他のゲーム オブジェクトを追跡できるようにするために使用する、スクリプトと動作のシステムです。</span><span class="sxs-lookup"><span data-stu-id="1ca78-108">In the MRTK, solvers are a system of scripts and behaviors that we use to be able to allow UI elements to follow you, the user or other game objects in the scene.</span></span> <span data-ttu-id="1ca78-109">また、特定の場所にすばやくスナップして、アプリケーションをさらに直感的にするために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1ca78-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span> 

## <a name="objectives"></a><span data-ttu-id="1ca78-110">目標</span><span class="sxs-lookup"><span data-stu-id="1ca78-110">Objectives</span></span>

* <span data-ttu-id="1ca78-111">MRTK ソルバーの紹介</span><span class="sxs-lookup"><span data-stu-id="1ca78-111">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="1ca78-112">ソルバーを使用して、ボタン コレクションにユーザーを追跡させる</span><span class="sxs-lookup"><span data-stu-id="1ca78-112">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="1ca78-113">ソルバーを使用して、追跡されているユーザーの手をゲーム オブジェクトに追跡させる</span><span class="sxs-lookup"><span data-stu-id="1ca78-113">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="1ca78-114">手順</span><span class="sxs-lookup"><span data-stu-id="1ca78-114">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="1ca78-115">MRTK でのソルバーの場所</span><span class="sxs-lookup"><span data-stu-id="1ca78-115">Location of solvers in the MRTK</span></span>
 <span data-ttu-id="1ca78-116">自分のプロジェクト内で利用できるソルバーを見つけるには、次の図に示されているように、MRTK SDK フォルダー ([MixedRealityToolkit.SDK] フォルダー) の [Utilities] (ユーティリティ) フォルダー内の [Solvers] (ソルバー) フォルダーを確認します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-116">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder), then under the utilities folder you will see the solvers folder, as shown in the image below.</span></span>

![ソルバー](images/lesson3_chapter1_step1im.PNG)

><span data-ttu-id="1ca78-118">注:このレッスンでは、"Orbital" ソルバーと "RadialView" ソルバーのみの実装について説明します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-118">Note: In this lesson we will only go over implementation of the "Orbital" solver and the "RadialView" solver.</span></span> <span data-ttu-id="1ca78-119">MRTK で利用できるすべてのソルバーについて学ぶには、次を参照してください。 https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span><span class="sxs-lookup"><span data-stu-id="1ca78-119">To learn more about the full range of solvers available in the MRTK, please visit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="1ca78-120">ソルバーを使用してユーザーを追跡する</span><span class="sxs-lookup"><span data-stu-id="1ca78-120">Use a Solver to Follow the User</span></span>
<span data-ttu-id="1ca78-121">この章の目標は、ユーザーの視線の方向を追跡するものとして以前に作成したボタン コレクションを強化することです。</span><span class="sxs-lookup"><span data-stu-id="1ca78-121">The goal of this chapter is to enhance the button collection we previously created such that it follows the user’s gaze direction.</span></span> <span data-ttu-id="1ca78-122">以前のバージョンの MRTK と HoloToolkit では、"taglong" 機能と呼ばれていました。</span><span class="sxs-lookup"><span data-stu-id="1ca78-122">In previous version of the MRTK and HoloToolkit, this was referred to as a "taglong" functionality.</span></span>

1. <span data-ttu-id="1ca78-123">以前のレッスンから、[Button Collection] (ボタン コレクション) 親オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-123">Select the Button Collection parent object from the previous lesson.</span></span>

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="1ca78-125">[Inspector] (インスペクター) パネルで、[Add Component] (コンポーネントの追加) ボタンをクリックして、「orbital」を検索します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-125">In the inspector panel, click the "add component" button and search for "orbital."</span></span> <span data-ttu-id="1ca78-126">[Orbital] コンポーネントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ca78-126">The orbital component should appear.</span></span> <span data-ttu-id="1ca78-127">これを選択して、[Button Collection] (ボタン コレクション) ゲーム オブジェクトに [Orbital] コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-127">Select it to add the orbital component to the Button Collection game object.</span></span>

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

><span data-ttu-id="1ca78-129">注:コンポーネントを追加すると、システムにより [Inspector] (インスペクター) タブに [Orbital (Script)] と [Solver Handler (Script)] が追加されます。これは必須コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="1ca78-129">Note: When you add the component you will notice that the system adds the orbital script and the solver handler script in the inspector tab, which is a required component.</span></span> 

3. <span data-ttu-id="1ca78-130">ユーザーを追跡するようボタン コレクションを構成するには、以下の調整を実装する必要があります (下の図も参照してください)。</span><span class="sxs-lookup"><span data-stu-id="1ca78-130">In order to configure the button collection to follow the user, we need to implement the following adjustments (please also refer to the image below):</span></span>
- <span data-ttu-id="1ca78-131">[Orbital (Script)] で、[Orientation Type] (向きタイプ) ドロップダウン リストを [Yaw Only] (ヨーのみ) に設定します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-131">In the Orbital script, set the "orientation type" drop-down list to "Yaw Only."</span></span> <span data-ttu-id="1ca78-132">これを設定するのは、ユーザーを追跡する際にオブジェクトの 1 つの軸だけが回転するようにするためです。</span><span class="sxs-lookup"><span data-stu-id="1ca78-132">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
- <span data-ttu-id="1ca78-133">すべての軸で [Local Offset] (ローカル オフセット) を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-133">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="1ca78-134">[World Offset] (ワールド オフセット) を、x = 0、y = -0.1、z = 0.6 に設定します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-134">Set the World Offset to x = 0, y = -0.1 and z = 0.6.</span></span> <span data-ttu-id="1ca78-135">こうすることでオブジェクトの動きを次のように固定できます。つまり、ユーザーが高さを変えると、オブジェクトは物理環境内で固定された高さにとどまりながら、ユーザーが環境内で移動する際にユーザーを追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="1ca78-135">This locks movement of the object such that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="1ca78-136">これらの値を調整して、さまざまな動作を実現できます。</span><span class="sxs-lookup"><span data-stu-id="1ca78-136">These values may be adjusted to achieve a wide range of behaviors.</span></span>
- <span data-ttu-id="1ca78-137">ユーザーが頭を大きく回転させた後、ボタンがユーザーの視界だけを追跡する動作の場合、[Use Angle Stepping for world offset] (ワールド オフセットに角度のステップを使用する) チェックボックスを選択できます (注意: 次の図と同じように、画面によってはこのテキストは一部表示されません)。たとえば、オブジェクトに 90 度ごとにユーザーを追跡させるには、ステップの数を 4 に設定します (左の例で緑の矢印で示されている)。</span><span class="sxs-lookup"><span data-stu-id="1ca78-137">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the "Use Angle Stepping for world offset" checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example to the left).</span></span> 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="1ca78-139">オブジェクトに追跡対象の手を追跡させる</span><span class="sxs-lookup"><span data-stu-id="1ca78-139">Enabling Objects to Follow Tracked Hands</span></span>

<span data-ttu-id="1ca78-140">このセクションでは、RadialView ソルバーを使用してユーザーの追跡対象の手を追跡するために、以前に作成した cube ゲーム オブジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-140">In this section, we will configure the cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="1ca78-141">[BaseScene] 階層内で [Cube] オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-141">Select the cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="1ca78-142">[Inspector] (インスペクター) パネルで、[Add Component] (コンポーネントの追加) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ca78-142">Click "add component" in the inspector panel.</span></span> 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. <span data-ttu-id="1ca78-144">検索ボックスで「RadialView」と入力し、[RadialView] コンポーネントを選択して cube に追加します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-144">Type in "RadialView" in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="1ca78-145">[Solver Handler] コンポーネントも自動で cube に追加されます。</span><span class="sxs-lookup"><span data-stu-id="1ca78-145">The solver handler component will also be automatically added to the cube.</span></span>

3. <span data-ttu-id="1ca78-146">ラジアル ビューを、頭ではなく左手を追跡するように変更します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-146">Change the radial view to not follow the head but follow the left hand.</span></span> <span data-ttu-id="1ca78-147">[tracked object to reference] (参照する追跡対象オブジェクト) オプションの隣にあるドロップダウン メニューを選択します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-147">Select the dropdown menu next to the "tracked object to reference" option.</span></span> <span data-ttu-id="1ca78-148">メニューから [Hand Joint Left] (左手の関節) を選択します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-148">Then select "hand joint left" from the menu.</span></span>

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. <span data-ttu-id="1ca78-150">手の関節を選択したら、cube に追跡させる手の部分を選択できます。</span><span class="sxs-lookup"><span data-stu-id="1ca78-150">Once you select the hand joint, you can choose which part of the hand you want the cube to follow.</span></span> <span data-ttu-id="1ca78-151">この例では、手首を使います。</span><span class="sxs-lookup"><span data-stu-id="1ca78-151">For this example, we are going to use the wrist.</span></span> <span data-ttu-id="1ca78-152">[tracked hand joint] (追跡対象の手の関節) オプションの隣にあるドロップダウン メニューから、[wrist] (手首) を選択します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-152">Next to the option "tracked hand joint" select the dropdown menu and select wrist.</span></span> 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. <span data-ttu-id="1ca78-154">cube とユーザーの手首との間隔がなくなるように、最小距離と最大距離を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="1ca78-154">Set the maximum and minimum distances to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="1ca78-155">設定すると、cube は完全に手首を追従するようになります。</span><span class="sxs-lookup"><span data-stu-id="1ca78-155">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="1ca78-156">また、[Reference Direction] (リファレンスの方向) フィールドを調整して、cube の方向付けに関する動作を調整することもできます (たとえば、ユーザーの手首に合わせてオブジェクトを回転させる場合、リファレンスの方向を [Orient with Tracked Object] (追跡対象オブジェクトに合わせて方向付け) に設定します)。</span><span class="sxs-lookup"><span data-stu-id="1ca78-156">You may also adjust the "Reference Direction" field to adjust the behavior of how the cube is oriented (e.g., if you would like to allow the object to rotate with the user's wrist, set the reference direction to "Orient with Tracked Object")</span></span>

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a><span data-ttu-id="1ca78-158">結論</span><span class="sxs-lookup"><span data-stu-id="1ca78-158">Congratulations</span></span>
<span data-ttu-id="1ca78-159">これで終了です。</span><span class="sxs-lookup"><span data-stu-id="1ca78-159">Congratulations!</span></span> <span data-ttu-id="1ca78-160">このレッスンでは、MRTK ソルバーを使用して UI に直感的にユーザーを追跡させる方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="1ca78-160">In this lesson, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="1ca78-161">また、ソルバーをゲーム オブジェクト (cube) に追加して、ユーザーの追跡対象の手を追跡させる方法についても学びました。</span><span class="sxs-lookup"><span data-stu-id="1ca78-161">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="1ca78-162">MRTK に含まれるこれらのソルバーや他のソルバーについて学ぶには、[MRTK ソルバーに関するドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ca78-162">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="1ca78-163">次のレッスン:3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="1ca78-163">Next Lesson: 3D Object Interaction</span></span>](mrlearning-base-ch4.md)

