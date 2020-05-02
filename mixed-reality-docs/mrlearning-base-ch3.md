---
title: 入門チュートリアル - 4. 動的なコンテンツの配置とソルバーの使用
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 8a85ab560d0e6b36b589970b4d5b8a441ed2bbe2
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "80362039"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="178a1-105">4.動的なコンテンツの配置とソルバーの使用</span><span class="sxs-lookup"><span data-stu-id="178a1-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="178a1-106">ホログラムは HoloLens 2 で現実のものとなります。ホログラムは直感的にユーザーを追跡し、滑らかで洗練された操作ができるように物理環境に配置されます。</span><span class="sxs-lookup"><span data-stu-id="178a1-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="178a1-107">このチュートリアルでは、複雑な空間配置シナリオを解決するために、「ソルバー」として知られる MRTK で使用できる配置ツールを使用して、ホログラムを動的に配置する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="178a1-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="178a1-108">MRTK では、ソルバーとは、UI 要素がシーン内で、あなた、ユーザー、他のゲーム オブジェクトを追跡できるようにするために使用される、スクリプトと動作のシステムです。</span><span class="sxs-lookup"><span data-stu-id="178a1-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="178a1-109">また、特定の場所にすばやくスナップして、アプリケーションをさらに直感的にするために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="178a1-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="178a1-110">目標</span><span class="sxs-lookup"><span data-stu-id="178a1-110">Objectives</span></span>

* <span data-ttu-id="178a1-111">MRTK ソルバーの紹介</span><span class="sxs-lookup"><span data-stu-id="178a1-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="178a1-112">ソルバーを使用して、ボタン コレクションにユーザーを追跡させる</span><span class="sxs-lookup"><span data-stu-id="178a1-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="178a1-113">ソルバーを使用して、ユーザーの追跡対象の手をゲーム オブジェクトに追跡させる</span><span class="sxs-lookup"><span data-stu-id="178a1-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="178a1-114">MRTK でのソルバーの場所</span><span class="sxs-lookup"><span data-stu-id="178a1-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="178a1-115">MRTK のソルバーは、MRTK SDK フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="178a1-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="178a1-116">プロジェクトで使用可能なソルバーを表示するには、[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MixedRealityToolkit.SDK]**  >  **[Features]\(機能\)**  >  **[Utilities]\(ユーティリティ\)**  >  **[Solvers]\(ソルバー\)** に移動します。</span><span class="sxs-lookup"><span data-stu-id="178a1-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="178a1-118">このチュートリアルでは、Orbital ソルバーと Radial View ソルバーの実装について説明します。</span><span class="sxs-lookup"><span data-stu-id="178a1-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="178a1-119">MRTK で利用可能なすべてのソルバーの詳細については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[ソルバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)に関するガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="178a1-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="178a1-120">ソルバーを使用してユーザーを追跡する</span><span class="sxs-lookup"><span data-stu-id="178a1-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="178a1-121">このセクションでは、前のチュートリアルで作成したボタン コレクションを拡張して、ユーザーの視線の方向に従うようにします。</span><span class="sxs-lookup"><span data-stu-id="178a1-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user's gaze direction.</span></span> <span data-ttu-id="178a1-122">さらに、ボタン コレクションが常に次のようになるようにソルバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="178a1-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="178a1-123">左から右への自然な読み取りのために、ユーザーの読み取り方向に対して平行に回転する</span><span class="sxs-lookup"><span data-stu-id="178a1-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="178a1-124">ユーザーの水平の視線の向きより下に配置することで、このチュートリアルの後の方で追加する他のオブジェクトを妨げないようにする</span><span class="sxs-lookup"><span data-stu-id="178a1-124">Positioned below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="178a1-125">ボタンを押しやすくするために、ユーザーからおよそ腕半分の距離に配置する</span><span class="sxs-lookup"><span data-stu-id="178a1-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="178a1-126">このためには、参照オブジェクトから、指定された位置とオフセットにオブジェクトをロックする **Orbital ソルバー**を使用します。</span><span class="sxs-lookup"><span data-stu-id="178a1-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="178a1-127">1.Orbital ソルバーを追加する</span><span class="sxs-lookup"><span data-stu-id="178a1-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="178a1-128">[Hierarchy]\(階層\) ウィンドウで、 **[ButtonCollection]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Orbital (Script)** コンポーネントを ButtonCollection オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="178a1-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="178a1-129">ソルバー (この場合は Orbital (Script) コンポーネント) を追加すると、ソルバーで必要になる Solver Handler (Script) コンポーネントが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="178a1-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="178a1-130">2.Orbital ソルバーを構成する</span><span class="sxs-lookup"><span data-stu-id="178a1-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="178a1-131">**Solver Handler (Script)** コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="178a1-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="178a1-132">**[Tracked Target Type]\(追跡対象の種類\)** が **[Head]\(頭\)** に設定されていることを確認します</span><span class="sxs-lookup"><span data-stu-id="178a1-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="178a1-133">**Orbital (Script)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="178a1-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="178a1-134">**[Orientation Type]\(向きの種類\)** が **[Follow Tracked Object]\(追跡対象オブジェクトに従う\)** に設定されていることを確認します</span><span class="sxs-lookup"><span data-stu-id="178a1-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="178a1-135">**[Local Offset]\(ローカル オフセット\)** を X = 0、Y = 0、Z = 0 にリセットします</span><span class="sxs-lookup"><span data-stu-id="178a1-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="178a1-136">**[World Offset]\(ワールド オフセット\)** を X = 0、Y = -0.4、Z = 0.3 に変更します</span><span class="sxs-lookup"><span data-stu-id="178a1-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="178a1-138">3.エディター内シミュレーションを使用して Orbital ソルバーをテストする</span><span class="sxs-lookup"><span data-stu-id="178a1-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="178a1-139">[Play]\(再生\) ボタンを押してゲーム モードに入り、マウスの右ボタンを押したままにして視線方向を回転させます。次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="178a1-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="178a1-140">ButtonCollection の変換位置が、ソルバーの設定によって決定されるようになりました</span><span class="sxs-lookup"><span data-stu-id="178a1-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="178a1-141">ソルバーの影響を受けない Cube は同じ位置のままになります</span><span class="sxs-lookup"><span data-stu-id="178a1-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="178a1-143">シーン ウィンドウにカメラの光線が表示されない場合は、ギズモ メニューが有効になっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="178a1-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="178a1-144">ギズモ メニューと、それを使用してシーン ビューを最適化する方法の詳細については、Unity の <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">ギズモ メニュー</a>に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="178a1-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="178a1-145">上の図に示されているようにシーンとゲーム ウィンドウを並べて表示するには、ゲーム ウィンドウをシーン ウィンドウの右側にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="178a1-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="178a1-146">ワークスペースのカスタマイズの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">ワークスペースのカスタマイズ</a>に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="178a1-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="178a1-147">オブジェクトに追跡対象の手を追跡させる</span><span class="sxs-lookup"><span data-stu-id="178a1-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="178a1-148">このセクションでは、前のチュートリアルで作成した Cube オブジェクトを、ユーザーの追跡対象の手 (特に右手の手首) を追跡するように構成します。</span><span class="sxs-lookup"><span data-stu-id="178a1-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user's tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="178a1-149">さらに、キューブが常に次のようになるようにソルバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="178a1-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="178a1-150">ユーザーの手の回転に合わせて向きを変える</span><span class="sxs-lookup"><span data-stu-id="178a1-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="178a1-151">ユーザーの手首の位置に移動する</span><span class="sxs-lookup"><span data-stu-id="178a1-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="178a1-152">このためには、参照オブジェクトによって投影されるビュー円錐内にオブジェクトを維持する **Radial View ソルバー**を使用します。</span><span class="sxs-lookup"><span data-stu-id="178a1-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="178a1-153">1.Radial View ソルバーを追加する</span><span class="sxs-lookup"><span data-stu-id="178a1-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="178a1-154">[Hierarchy]\(階層\) ウィンドウで、 **[Cube]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Radial View (Script)** コンポーネントを Cube オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="178a1-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="178a1-155">2.Radial View ソルバーを構成する</span><span class="sxs-lookup"><span data-stu-id="178a1-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="178a1-156">**Solver Handler (Script)** コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="178a1-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="178a1-157">**[Tracked Target Type]\(追跡対象の種類\)** を **[Hand Joint]\(手の関節\)** に変更します</span><span class="sxs-lookup"><span data-stu-id="178a1-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="178a1-158">**[Tracked Handness]\(追跡対象の手\)** を **[Right]\(右\)** に変更します</span><span class="sxs-lookup"><span data-stu-id="178a1-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="178a1-159">**[Tracked Hand Joint]\(追跡対象の手の関節\)** を **[Wrist]\(手首\)** に変更します</span><span class="sxs-lookup"><span data-stu-id="178a1-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="178a1-160">**Radial View (Script)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="178a1-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="178a1-161">**[Reference Direction]\(参照方向\)** を **[Object Oriented]\(オブジェクトの向き\)** に変更してから、 **[Orient To Reference Direction]\(参照方向に向ける\)** チェックボックスをオンにします</span><span class="sxs-lookup"><span data-stu-id="178a1-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="178a1-162">**[Min Distance]\(最小距離\)** および **[Max Distance]\(最大距離\)** を 0 に変更します</span><span class="sxs-lookup"><span data-stu-id="178a1-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="178a1-164">3.エディター内シミュレーションを使用して Radial View ソルバーをテストする</span><span class="sxs-lookup"><span data-stu-id="178a1-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="178a1-165">[Play]\(再生\) ボタンを押してゲーム モードに入り、スペースキーを押して保持することで手を表示します。</span><span class="sxs-lookup"><span data-stu-id="178a1-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="178a1-166">マウス カーソルを移動して手を動かし、マウスの左ボタンを押したままにして手を回転させます。</span><span class="sxs-lookup"><span data-stu-id="178a1-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="178a1-168">結論</span><span class="sxs-lookup"><span data-stu-id="178a1-168">Congratulations</span></span>

<span data-ttu-id="178a1-169">このチュートリアルでは、MRTK ソルバーを使用して UI に直感的にユーザーを追跡させる方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="178a1-169">In this tutorial, you learned how to use the MRTK's solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="178a1-170">また、ソルバーをオブジェクト (cube) に追加して、ユーザーの追跡対象の手を追跡させる方法についても学びました。</span><span class="sxs-lookup"><span data-stu-id="178a1-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user's tracked hands.</span></span> <span data-ttu-id="178a1-171">MRTK に含まれるこれらのソルバーや他のソルバーについて学ぶには、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[ソルバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) に関するガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="178a1-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="178a1-172">次のチュートリアル:5.3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="178a1-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
