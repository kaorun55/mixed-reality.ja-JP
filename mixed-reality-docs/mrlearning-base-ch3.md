---
title: 入門チュートリアル-4. 動的なコンテンツの配置とソルバーの使用
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 8275d5a97d7827d34ed3926cabe4032cc7f4cfac
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129333"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="8dd0e-105">4. 動的なコンテンツを配置し、ソルバーを使用する</span><span class="sxs-lookup"><span data-stu-id="8dd0e-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="8dd0e-106">ホログラムは、ユーザーに直感的に従うことができ、シームレスで洗練された方法で物理的な環境に配置されると、HoloLens 2 で有効になります。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="8dd0e-107">このチュートリアルでは、複雑な空間配置シナリオを解決するために、ソルバーと呼ばれる MRTK の利用可能な配置ツールを使用して、ホログラムを動的に配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="8dd0e-108">MRTK では、ソルバーはスクリプトと動作のシステムであり、UI 要素がシーン内のユーザー、ユーザー、またはその他のゲームオブジェクトに従うことを許可するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="8dd0e-109">また、特定の場所にすばやくスナップして、アプリケーションをさらに直感的にするために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="8dd0e-110">目標</span><span class="sxs-lookup"><span data-stu-id="8dd0e-110">Objectives</span></span>

* <span data-ttu-id="8dd0e-111">MRTK のソルバーを導入する</span><span class="sxs-lookup"><span data-stu-id="8dd0e-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="8dd0e-112">ソルバーを使用して、ユーザーに続くボタンのコレクションを作成します</span><span class="sxs-lookup"><span data-stu-id="8dd0e-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="8dd0e-113">ソルバーを使用して、ユーザーの追跡対象に従うゲームオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="8dd0e-114">MRTK でのソルバーの場所</span><span class="sxs-lookup"><span data-stu-id="8dd0e-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="8dd0e-115">MRTK のソルバーは、MRTK SDK フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="8dd0e-116">プロジェクトで使用可能なソルバーを表示するには、プロジェクト ウィンドウで、**資産** >   > **機能**  >  > **ユーティリティ** **ソルバー** の順に**移動します**。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="8dd0e-118">このチュートリアルでは、回転ソルバーと放射状ビューのソルバーの実装について説明します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="8dd0e-119">MRTK で利用可能なすべてのソルバーの詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の「[ソルバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)ガイド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="8dd0e-120">ソルバーを使用してユーザーをフォローする</span><span class="sxs-lookup"><span data-stu-id="8dd0e-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="8dd0e-121">このセクションでは、前のチュートリアルで作成したボタンコレクションを拡張して、ユーザーの見つめ方向に従うようにします。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user’s gaze direction.</span></span> <span data-ttu-id="8dd0e-122">さらに、ボタンコレクションが常にであるように、ソルバーも構成します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="8dd0e-123">自然な左から右への読み取りのために、ユーザーの読み取り方向に並列に回転</span><span class="sxs-lookup"><span data-stu-id="8dd0e-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="8dd0e-124">このチュートリアルの後半では、ユーザーの横方向の水平方向の向きを少しずらして配置します。そのため、このチュートリアルの後半で追加するオブジェクトは obstructing ません。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-124">Positioned slightly below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="8dd0e-125">ユーザーに対して約半分の arm の長さが配置されているため、ボタンを簡単に押すことができます。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="8dd0e-126">このためには、**回転ソルバー**を使用します。これにより、オブジェクトが、参照先のオブジェクトから指定した位置とオフセットにロックされます。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="8dd0e-127">1. 回転ソルバーを追加する</span><span class="sxs-lookup"><span data-stu-id="8dd0e-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="8dd0e-128">階層 ウィンドウで、 **buttoncollection**オブジェクトを選択し、インスペクター ウィンドウで **コンポーネントの追加** ボタンを使用して、**回転 (スクリプト)** コンポーネントを buttoncollection オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="8dd0e-129">ソルバー (この場合は回転 (スクリプト) コンポーネント) を追加すると、ソルバーで必要になるため、ソルバーハンドラー (スクリプト) コンポーネントが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="8dd0e-130">2. 回転ソルバーを構成する</span><span class="sxs-lookup"><span data-stu-id="8dd0e-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="8dd0e-131">**ソルバーハンドラー (スクリプト)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="8dd0e-132">**追跡対象のターゲットの種類**が**Head**に設定されていることを確認する</span><span class="sxs-lookup"><span data-stu-id="8dd0e-132">Verify that **Tracked Target Type**  is set to **Head**</span></span>

<span data-ttu-id="8dd0e-133">**回転 (スクリプト)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="8dd0e-134">**追跡対象オブジェクトに従っ**て**向きの種類**を変更する</span><span class="sxs-lookup"><span data-stu-id="8dd0e-134">Change **Orientation Type** to **Follow Tracked Object**</span></span>
* <span data-ttu-id="8dd0e-135">**ローカルオフセット**を X = 0、Y = 0、Z = 0 にリセットします。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="8dd0e-136">**ワールドオフセット**を X = 0、Y =-0.4、Z = 0.3 に変更します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="8dd0e-138">3. エディター内シミュレーションを使用して回転ソルバーをテストする</span><span class="sxs-lookup"><span data-stu-id="8dd0e-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="8dd0e-139">再生ボタンを押してゲームモードに入り、マウスの右ボタンを押したままにして、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="8dd0e-140">ButtonCollection の変換位置が、ソルバーの設定によって決定されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="8dd0e-141">この場合、ソルバーの影響を受けないキューブは同じ位置に残ります。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="8dd0e-143">シーンウィンドウにカメラの射線が表示されない場合は、ギズモメニューが有効になっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="8dd0e-144">[ギズモ] メニューと、それを使用してシーンビューを最適化する方法の詳細については、Unity の<a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">ギズモメニュー</a>のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="8dd0e-145">上の図に示されているようにシーンとゲームウィンドウを並べて表示するには、[シーン] ウィンドウの右側にゲームウィンドウをドラッグするだけです。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="8dd0e-146">ワークスペースのカスタマイズの詳細については、「<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">ワークスペース</a>のドキュメントをカスタマイズする」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="8dd0e-147">追跡したハンドに従ってオブジェクトを有効にする</span><span class="sxs-lookup"><span data-stu-id="8dd0e-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="8dd0e-148">このセクションでは、前のチュートリアルで作成したキューブオブジェクトを構成して、ユーザーの追跡対象 (特に右側の手首) に従っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user’s tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="8dd0e-149">また、次のように、キューブにソルバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="8dd0e-150">ユーザーの手の回転で向きを変更します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="8dd0e-151">ユーザーの手首に位置指定</span><span class="sxs-lookup"><span data-stu-id="8dd0e-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="8dd0e-152">この場合は、参照先のオブジェクトによってキャストされたビューコーン内のオブジェクトを保持する**放射状ビューのソルバー**を使用します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="8dd0e-153">1. 放射状ビューのソルバーを追加する</span><span class="sxs-lookup"><span data-stu-id="8dd0e-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="8dd0e-154">階層 ウィンドウで、**キューブ**オブジェクトを選択し、インスペクター ウィンドウで **コンポーネントの追加** ボタンを使用して、**放射状ビュー (スクリプト)** コンポーネントキューブオブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="8dd0e-155">2. 放射状ビューのソルバーを構成する</span><span class="sxs-lookup"><span data-stu-id="8dd0e-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="8dd0e-156">**ソルバーハンドラー (スクリプト)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="8dd0e-157">**追跡対象のターゲットの種類**を**手動**に変更する</span><span class="sxs-lookup"><span data-stu-id="8dd0e-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="8dd0e-158">**追跡**した内容を**右**に変更する</span><span class="sxs-lookup"><span data-stu-id="8dd0e-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="8dd0e-159">追跡した**ハンドジョイント**を**手首**に変更する</span><span class="sxs-lookup"><span data-stu-id="8dd0e-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="8dd0e-160">**放射状ビュー (スクリプト)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="8dd0e-161">**参照の方向**を**オブジェクト指向**に変更し、 **[参照方向への向き]** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="8dd0e-162">**最小距離**と**最大距離**を0に変更します</span><span class="sxs-lookup"><span data-stu-id="8dd0e-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="8dd0e-164">3. エディター内シミュレーションを使用して放射状ビューのソルバーをテストする</span><span class="sxs-lookup"><span data-stu-id="8dd0e-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="8dd0e-165">再生ボタンを押してゲームモードに入り、space キーを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="8dd0e-166">マウスカーソルを移動して手を動かし、マウスの左ボタンを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="8dd0e-168">結論</span><span class="sxs-lookup"><span data-stu-id="8dd0e-168">Congratulations</span></span>

<span data-ttu-id="8dd0e-169">このチュートリアルでは、MRTK のソルバーを使用して、UI を直感的にユーザーに従う方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-169">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="8dd0e-170">また、オブジェクト (つまりキューブ) にソルバーをアタッチして、ユーザーの追跡対象に従う方法についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="8dd0e-171">MRTK に含まれるこれらの他のソルバーの詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の「[ソルバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)ガイド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dd0e-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="8dd0e-172">次のチュートリアル: 5. 3D オブジェクトとの対話</span><span class="sxs-lookup"><span data-stu-id="8dd0e-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
