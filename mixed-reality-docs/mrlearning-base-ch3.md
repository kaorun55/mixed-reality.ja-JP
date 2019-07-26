---
title: MR 学習ベース モジュール - ダイナミック コンテンツの配置とソルバー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 401c667ef80042da9182b7f4e065dfd6884cf061
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485690"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="6f01d-104">4。動的なコンテンツの配置とソルバーの使用</span><span class="sxs-lookup"><span data-stu-id="6f01d-104">4. Placing dynamic content and using solvers</span></span>

<span data-ttu-id="6f01d-105">ホログラムは HoloLens 2 で現実のものとなります。ホログラムは直感的にユーザーを追跡し、滑らかで洗練された操作ができるように物理環境に配置されます。</span><span class="sxs-lookup"><span data-stu-id="6f01d-105">Holograms come to life in the HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="6f01d-106">このチュートリアルでは、複雑な空間配置のシナリオを解決するために、ソルバーと呼ばれる MRTK の利用可能な配置ツールを使用して、ホログラムを動的に配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-106">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools, known as solvers for the way they solve complex spatial placement scenarios.</span></span> <span data-ttu-id="6f01d-107">MRTK では、ソルバーはスクリプトと動作のシステムであり、UI 要素がシーン内のユーザー、ユーザー、またはその他のゲームオブジェクトに従うことを許可するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6f01d-107">In the MRTK, solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="6f01d-108">また、特定の場所にすばやくスナップして、アプリケーションをさらに直感的にするために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="6f01d-108">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span> 

## <a name="objectives"></a><span data-ttu-id="6f01d-109">目的</span><span class="sxs-lookup"><span data-stu-id="6f01d-109">Objectives</span></span>

* <span data-ttu-id="6f01d-110">MRTK ソルバーの紹介</span><span class="sxs-lookup"><span data-stu-id="6f01d-110">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="6f01d-111">ソルバーを使用して、ボタン コレクションにユーザーを追跡させる</span><span class="sxs-lookup"><span data-stu-id="6f01d-111">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="6f01d-112">ソルバーを使用して、追跡されているユーザーの手をゲーム オブジェクトに追跡させる</span><span class="sxs-lookup"><span data-stu-id="6f01d-112">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="6f01d-113">手順</span><span class="sxs-lookup"><span data-stu-id="6f01d-113">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="6f01d-114">MRTK でのソルバーの場所</span><span class="sxs-lookup"><span data-stu-id="6f01d-114">Location of solvers in the MRTK</span></span>
 <span data-ttu-id="6f01d-115">自分のプロジェクト内で利用できるソルバーを見つけるには、次の図に示されているように、MRTK SDK フォルダー ([MixedRealityToolkit.SDK] フォルダー) の [Utilities] (ユーティリティ) フォルダー内の [Solvers] (ソルバー) フォルダーを確認します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-115">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder), then under the utilities folder you will see the solvers folder, as shown in the image below.</span></span>

![ソルバー](images/lesson3_chapter1_step1im.PNG)

><span data-ttu-id="6f01d-117">注:このレッスンでは、回転ソルバーと放射 Alview ソルバーの実装についてのみ説明します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-117">Note: In this lesson we will only go over the implementation of the Orbital solver and the RadialView solver.</span></span> <span data-ttu-id="6f01d-118">MRTK で利用できるすべてのソルバーについて学ぶには、次を参照してください。 https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span><span class="sxs-lookup"><span data-stu-id="6f01d-118">To learn more about the full range of solvers available in the MRTK, please visit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="6f01d-119">ソルバーを使用してユーザーを追跡する</span><span class="sxs-lookup"><span data-stu-id="6f01d-119">Use a Solver to Follow the User</span></span>
<span data-ttu-id="6f01d-120">この章の目的は、以前に作成されたボタンコレクションを拡張して、ユーザーの見つめ方向に従うようにすることです。</span><span class="sxs-lookup"><span data-stu-id="6f01d-120">The goal of this chapter is to enhance the button collection that was previously created so that it follows the user’s gaze direction.</span></span> <span data-ttu-id="6f01d-121">MRTK と HoloToolkit の以前のバージョンでは、これは tagalong いう機能と呼ばれていました。</span><span class="sxs-lookup"><span data-stu-id="6f01d-121">In previous version of the MRTK and HoloToolkit, this was referred to as a tagalong functionality.</span></span>

1. <span data-ttu-id="6f01d-122">以前のレッスンから、[Button Collection] (ボタン コレクション) 親オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-122">Select the Button Collection parent object from the previous lesson.</span></span>

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="6f01d-124">[インスペクター] パネルで [コンポーネントの追加] ボタンをクリックし、回転を検索します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-124">In the Inspector panel, click the Add Component button and search for orbital.</span></span> <span data-ttu-id="6f01d-125">[Orbital] コンポーネントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f01d-125">The orbital component should appear.</span></span> <span data-ttu-id="6f01d-126">これを選択して、[Button Collection] (ボタン コレクション) ゲーム オブジェクトに [Orbital] コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-126">Select it to add the orbital component to the Button Collection game object.</span></span>

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

><span data-ttu-id="6f01d-128">注:コンポーネントを追加すると、システムにより [Inspector] (インスペクター) タブに [Orbital (Script)] と [Solver Handler (Script)] が追加されます。これは必須コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="6f01d-128">Note: When you add the component you will notice that the system adds the orbital script and the solver handler script in the inspector tab, which is a required component.</span></span> 

3. <span data-ttu-id="6f01d-129">ユーザーに従うようにボタンコレクションを構成するには、次の調整を実装する必要があります (以下の図を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="6f01d-129">In order to configure the button collection to follow the user, we need to implement the following adjustments (refer to the image below):</span></span>
- <span data-ttu-id="6f01d-130">回転スクリプトで、[方向の種類] ボックスの一覧を [ヨーのみ] に設定します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-130">In the Orbital script, set the Orientation Type drop-down list to Yaw Only.</span></span> <span data-ttu-id="6f01d-131">これを設定するのは、ユーザーを追跡する際にオブジェクトの 1 つの軸だけが回転するようにするためです。</span><span class="sxs-lookup"><span data-stu-id="6f01d-131">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
- <span data-ttu-id="6f01d-132">すべての軸で [Local Offset] (ローカル オフセット) を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-132">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="6f01d-133">[World Offset] (ワールド オフセット) を、x = 0、y = -0.1、z = 0.6 に設定します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-133">Set the World Offset to x = 0, y = -0.1 and z = 0.6.</span></span> <span data-ttu-id="6f01d-134">こうすることでオブジェクトの動きを次のように固定できます。つまり、ユーザーが高さを変えると、オブジェクトは物理環境内で固定された高さにとどまりながら、ユーザーが環境内で移動する際にユーザーを追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="6f01d-134">This locks movement of the object such that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="6f01d-135">これらの値を調整して、さまざまな動作を実現できます。</span><span class="sxs-lookup"><span data-stu-id="6f01d-135">These values may be adjusted to achieve a wide range of behaviors.</span></span>
- <span data-ttu-id="6f01d-136">ユーザーが自分のヘッドの位置を十分に変えた後に、ボタンがユーザーのビューにのみ表示されるようにするための動作については、[ワールドオフセットの角度をステップ実行する] チェックボックスをオンにすることができます (注:次の図と同じように、画面によってはこのテキストは一部表示されません)。たとえば、オブジェクトに 90 度ごとにユーザーを追跡させるには、ステップの数を 4 に設定します (左の例で緑の矢印で示されている)。</span><span class="sxs-lookup"><span data-stu-id="6f01d-136">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the Use Angle Stepping for world offset checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example to the left).</span></span> 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="6f01d-138">追跡したハンドに従ってオブジェクトを有効にする</span><span class="sxs-lookup"><span data-stu-id="6f01d-138">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="6f01d-139">このセクションでは、RadialView ソルバーを使用してユーザーの追跡対象の手を追跡するために、以前に作成した cube ゲーム オブジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-139">In this section, we will configure the cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="6f01d-140">[BaseScene] 階層内で [Cube] オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-140">Select the cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="6f01d-141">[インスペクター] パネルの [コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f01d-141">Click Add Component in the Inspector panel.</span></span> 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. <span data-ttu-id="6f01d-143">検索ボックスに「」と入力し、[放射型] コンポーネントを選択してキューブに追加します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-143">Type in RadialView in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="6f01d-144">[Solver Handler] コンポーネントも自動で cube に追加されます。</span><span class="sxs-lookup"><span data-stu-id="6f01d-144">The solver handler component will also be automatically added to the cube.</span></span>

3. <span data-ttu-id="6f01d-145">ラジアル ビューを、頭ではなく左手を追跡するように変更します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-145">Change the radial view to not follow the head but follow the left hand.</span></span> <span data-ttu-id="6f01d-146">[参照するオブジェクトの追跡] オプションの横にあるドロップダウンメニューを選択します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-146">Select the dropdown menu next to the Tracked Object to Reference option.</span></span> <span data-ttu-id="6f01d-147">メニューから [手の接合] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-147">Then select Hand Joint Left from the menu.</span></span>

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. <span data-ttu-id="6f01d-149">手の関節を選択したら、cube に追跡させる手の部分を選択できます。</span><span class="sxs-lookup"><span data-stu-id="6f01d-149">Once you select the hand joint, you can choose which part of the hand you want the cube to follow.</span></span> <span data-ttu-id="6f01d-150">この例では、手首を使います。</span><span class="sxs-lookup"><span data-stu-id="6f01d-150">For this example, we are going to use the wrist.</span></span> <span data-ttu-id="6f01d-151">[追跡されたハンドジョイント] オプションの横にあるドロップダウンメニューを選択し、[手首] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-151">Next to the option Tracked Hand Joint select the dropdown menu and select Wrist.</span></span> 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. <span data-ttu-id="6f01d-153">cube とユーザーの手首との間隔がなくなるように、最小距離と最大距離を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-153">Set the maximum and minimum distances to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="6f01d-154">設定すると、cube は完全に手首を追従するようになります。</span><span class="sxs-lookup"><span data-stu-id="6f01d-154">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="6f01d-155">また、[参照方向] フィールドを調整して、キューブの向きの動作を調整することもできます。たとえば、オブジェクトをユーザーの手首で回転できるようにする場合は、参照の方向を [追跡対象オブジェクト] に設定します。</span><span class="sxs-lookup"><span data-stu-id="6f01d-155">You might also adjust the Reference Direction field to adjust the behavior of how the cube is oriented, such as if you want to allow the object to rotate with the user's wrist by setting the reference direction to Orient with Tracked Object.</span></span>

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

## <a name="congratulations"></a><span data-ttu-id="6f01d-157">結論</span><span class="sxs-lookup"><span data-stu-id="6f01d-157">Congratulations</span></span>
<span data-ttu-id="6f01d-158">このチュートリアルでは、MRTK のソルバーを使用して、UI を直感的にユーザーに従う方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="6f01d-158">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="6f01d-159">また、ソルバーをゲーム オブジェクト (cube) に追加して、ユーザーの追跡対象の手を追跡させる方法についても学びました。</span><span class="sxs-lookup"><span data-stu-id="6f01d-159">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="6f01d-160">MRTK に含まれるこれらのソルバーや他のソルバーについて学ぶには、[MRTK ソルバーに関するドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f01d-160">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="6f01d-161">次のレッスン:5。  3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="6f01d-161">Next Lesson: 5.    Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)

