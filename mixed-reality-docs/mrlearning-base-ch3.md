---
title: 入門チュートリアル-4. 動的なコンテンツの配置とソルバーの使用
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, チュートリアル, hololens
ms.openlocfilehash: e08de0bc769ceda493eafe40158b6aeed87751c7
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334360"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="f4883-105">4. 動的なコンテンツを配置し、ソルバーを使用する</span><span class="sxs-lookup"><span data-stu-id="f4883-105">4. Placing dynamic content and using solvers</span></span>

<span data-ttu-id="f4883-106">ホログラムは、ユーザーに直感的に従うことができ、シームレスで洗練された方法で物理的な環境に配置されると、HoloLens 2 で有効になります。</span><span class="sxs-lookup"><span data-stu-id="f4883-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="f4883-107">このチュートリアルでは、複雑な空間配置シナリオを解決するために、MRTK の利用可能な配置ツール (ソルバー) を使用して、ホログラムを動的に配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4883-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools (known as solvers) to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="f4883-108">MRTK では、ソルバーはスクリプトと動作のシステムであり、UI 要素がシーン内のユーザー、ユーザー、またはその他のゲームオブジェクトに従うことを許可するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4883-108">In the MRTK, solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="f4883-109">また、特定の場所にすばやくスナップして、アプリケーションをさらに直感的にするために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f4883-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="f4883-110">目標</span><span class="sxs-lookup"><span data-stu-id="f4883-110">Objectives</span></span>

* <span data-ttu-id="f4883-111">MRTK ソルバーの紹介</span><span class="sxs-lookup"><span data-stu-id="f4883-111">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="f4883-112">ソルバーを使用して、ボタン コレクションにユーザーを追跡させる</span><span class="sxs-lookup"><span data-stu-id="f4883-112">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="f4883-113">ソルバーを使用して、追跡されているユーザーの手をゲーム オブジェクトに追跡させる</span><span class="sxs-lookup"><span data-stu-id="f4883-113">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="f4883-114">MRTK でのソルバーの場所</span><span class="sxs-lookup"><span data-stu-id="f4883-114">Location of solvers in the MRTK</span></span>

 <span data-ttu-id="f4883-115">プロジェクトで使用可能なソルバーを見つけるには、MRTK SDK フォルダー (MixedRealityToolkit フォルダー) を探します。</span><span class="sxs-lookup"><span data-stu-id="f4883-115">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder).</span></span> <span data-ttu-id="f4883-116">次の図に示すように、utilities フォルダーの下に、ソルバーフォルダーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4883-116">Under the utilities folder, you will see the solvers folder, as shown in the image below.</span></span>

![ソルバー](images/lesson3_chapter1_step1im.PNG)

>[!NOTE]
><span data-ttu-id="f4883-118">このレッスンでは、回転ソルバーと放射 Alview ソルバーの実装についてのみ説明します。</span><span class="sxs-lookup"><span data-stu-id="f4883-118">In this lesson, we will only review the implementation of the Orbital solver and the RadialView solver.</span></span> <span data-ttu-id="f4883-119">MRTK で利用可能なすべての種類のソルバーの詳細については、次のページを参照してください: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)</span><span class="sxs-lookup"><span data-stu-id="f4883-119">To learn more about the full range of solvers available in the MRTK, visit: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="f4883-120">ソルバーを使用してユーザーを追跡する</span><span class="sxs-lookup"><span data-stu-id="f4883-120">Use a Solver to Follow the User</span></span>

<span data-ttu-id="f4883-121">この章の目的は、以前に作成されたボタンコレクションを拡張して、ユーザーの見つめ方向に従うようにすることです。</span><span class="sxs-lookup"><span data-stu-id="f4883-121">The goal of this chapter is to enhance the button collection that was previously created so that it follows the user’s gaze direction.</span></span> <span data-ttu-id="f4883-122">以前のバージョンの MRTK と HoloToolkit では、これは tagalong いう機能と呼ばれていました。</span><span class="sxs-lookup"><span data-stu-id="f4883-122">In the previous version of the MRTK and HoloToolkit, this was referred to as a tagalong functionality.</span></span>

1. <span data-ttu-id="f4883-123">以前のレッスンから、[Button Collection] (ボタン コレクション) 親オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="f4883-123">Select the Button Collection parent object from the previous lesson.</span></span>

    ![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="f4883-125">[インスペクター] パネルで [コンポーネントの追加] ボタンをクリックし、回転を検索します。</span><span class="sxs-lookup"><span data-stu-id="f4883-125">In the Inspector panel, click the Add Component button and search for orbital.</span></span> <span data-ttu-id="f4883-126">回転コンポーネントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4883-126">The Orbital component should appear.</span></span> <span data-ttu-id="f4883-127">これを選択して、回転コンポーネントをボタンコレクションゲームオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="f4883-127">Select it to add the Orbital component to the Button Collection game object.</span></span>

    ![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

    >[!NOTE]
    ><span data-ttu-id="f4883-129">回転コンポーネントを追加すると、システムによって、必要なコンポーネントである、"要素の追加" コンポーネントも追加されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="f4883-129">When you add the Orbital component you will notice that the system also adds the SolverHandler component, which is a required component.</span></span>

3. <span data-ttu-id="f4883-130">ユーザーに従うようにボタンコレクションを構成するには、次の調整を実装する必要があります (以下の図を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="f4883-130">In order to configure the Button Collection to follow the user, we need to implement the following adjustments (refer to the image below):</span></span>

    * <span data-ttu-id="f4883-131">回転スクリプトで、[方向の種類] ボックスの一覧を [ヨーのみ] に設定します。</span><span class="sxs-lookup"><span data-stu-id="f4883-131">In the Orbital script, set the Orientation Type drop-down list to Yaw Only.</span></span> <span data-ttu-id="f4883-132">これを設定するのは、ユーザーを追跡する際にオブジェクトの 1 つの軸だけが回転するようにするためです。</span><span class="sxs-lookup"><span data-stu-id="f4883-132">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
    * <span data-ttu-id="f4883-133">すべての軸で [Local Offset] (ローカル オフセット) を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="f4883-133">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="f4883-134">ワールドオフセットを x = 0、y =-0.1、z = 0.6 に設定します。</span><span class="sxs-lookup"><span data-stu-id="f4883-134">Set the World Offset to x = 0, y = -0.1, and z = 0.6.</span></span> <span data-ttu-id="f4883-135">これにより、オブジェクトの移動がロックされるため、ユーザーが高さを変更したときに、ユーザーが環境について移動したときにユーザーの操作を継続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f4883-135">This locks movement of the object so that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="f4883-136">これらの値を調整して、さまざまな動作を実現できます。</span><span class="sxs-lookup"><span data-stu-id="f4883-136">These values may be adjusted to achieve a wide range of behaviors.</span></span>
    * <span data-ttu-id="f4883-137">ユーザーが十分に離れたところでボタンがユーザーのビューに従うようにするには、次のように、[ワールドオフセットの角度をステップ実行する] チェックボックスをオンにします (注: このタイトルは、次の図のように、一部の画面では切り捨てられる場合があります)。たとえば、オブジェクトが90度ごとにユーザーにのみ従うようにするには、ステップ数を4に設定します (下の例では緑色の矢印でマークされています)。</span><span class="sxs-lookup"><span data-stu-id="f4883-137">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the Use Angle Stepping For World Offset checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example below).</span></span>

    ![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="f4883-139">追跡したハンドに従ってオブジェクトを有効にする</span><span class="sxs-lookup"><span data-stu-id="f4883-139">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="f4883-140">このセクションでは、前に作成したキューブゲームオブジェクトを構成して、ユーザーの追跡対象ユーザーに対して、放射 Alview ソルバーを使用します。</span><span class="sxs-lookup"><span data-stu-id="f4883-140">In this section, we will configure the Cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="f4883-141">BaseScene 階層内のキューブオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="f4883-141">Select the Cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="f4883-142">[インスペクター] パネルの [コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4883-142">Click Add Component in the Inspector panel.</span></span> <span data-ttu-id="f4883-143">検索ボックスに「」と入力し、[放射型] コンポーネントを選択してキューブに追加します。</span><span class="sxs-lookup"><span data-stu-id="f4883-143">Type in RadialView in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="f4883-144">また、このキューブには、パーティションコンポーネントが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="f4883-144">The SolverHandler component will also be automatically added to the cube.</span></span>

    ![mrlearning-base-ch3-3-step3](images/mrlearning-base-ch3-3-step1.png)

2. <span data-ttu-id="f4883-146">ヘッドではなく手の形になるように放射 Alview を変更するには、[追跡対象の種類] オプションの横にあるドロップダウンメニューを選択し、メニューから [手の接合] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f4883-146">To change the RadialView to follow a hand instead of the head, select the dropdown menu next to the Tracked Target Type option and select Hand Joint from the menu.</span></span>

    ![mrlearning-base-ch3-3-step2](images/mrlearning-base-ch3-3-step2a.png)

    <span data-ttu-id="f4883-148">これで、2つの新しいオプションである [追跡された人の種類] と [追跡された手の継手] が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4883-148">You will now see two new options, Tracked Handness Type and Tracked Hand Joint.</span></span> <span data-ttu-id="f4883-149">この例では、次の図に示すように、左側の手首に従います。</span><span class="sxs-lookup"><span data-stu-id="f4883-149">For this example, you will have the RadialView follow the wrist of the left hand as shown in the image below.</span></span>

    ![mrlearning-base-ch3-3-step2b](images/mrlearning-base-ch3-3-step2b.png)

3. <span data-ttu-id="f4883-151">放射状ビューの最大距離と最小距離を0に設定します。これにより、キューブがユーザーの手首と同じ距離になることはありません。</span><span class="sxs-lookup"><span data-stu-id="f4883-151">Set the maximum and minimum distances of the Radial View to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="f4883-152">設定すると、cube は完全に手首を追従するようになります。</span><span class="sxs-lookup"><span data-stu-id="f4883-152">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="f4883-153">また、[参照方向] フィールドを調整して、キューブの向きの動作を調整することもできます。たとえば、オブジェクトをオブジェクト指向に設定することによって、ユーザーの手首でオブジェクトを回転できるようにする場合などです。</span><span class="sxs-lookup"><span data-stu-id="f4883-153">You might also adjust the Reference Direction field to adjust the behavior of how the cube is oriented, such as if you want to allow the object to rotate with the user's wrist by setting the Reference Direction to Object Oriented.</span></span>

    ![mrlearning-base-ch3-3-step3](images/mrlearning-base-ch3-3-step3.png)

## <a name="congratulations"></a><span data-ttu-id="f4883-155">結論</span><span class="sxs-lookup"><span data-stu-id="f4883-155">Congratulations</span></span>

<span data-ttu-id="f4883-156">このチュートリアルでは、MRTK のソルバーを使用して、UI を直感的にユーザーに従う方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="f4883-156">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="f4883-157">また、ソルバーをゲーム オブジェクト (cube) に追加して、ユーザーの追跡対象の手を追跡させる方法についても学びました。</span><span class="sxs-lookup"><span data-stu-id="f4883-157">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="f4883-158">MRTK に含まれるこれらのソルバーや他のソルバーについて学ぶには、[MRTK ソルバーに関するドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4883-158">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="f4883-159">次のレッスン: 5. 3D オブジェクトとの対話</span><span class="sxs-lookup"><span data-stu-id="f4883-159">Next Lesson: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
