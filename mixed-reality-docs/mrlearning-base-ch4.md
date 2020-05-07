---
title: 入門チュートリアル - 5. 3D オブジェクトの操作
description: 3D オブジェクトの整理や基本操作のための境界ボックスなど、基本的な 3D コンテンツとユーザー エクスペリエンスについて説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: b807ac7e51e4009d2c44d3b7c67fbdf3488ccbd9
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604993"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="87dbb-105">5.3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="87dbb-105">5. Interacting with 3D objects</span></span>

<span data-ttu-id="87dbb-106">このチュートリアルでは、コレクションの一部としての 3D オブジェクトの整理、基本操作のための境界ボックス、近距離操作と遠距離操作、手の追跡によるタッチやグラブ ジェスチャなど、基本的な 3D コンテンツとユーザー エクスペリエンスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-106">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="87dbb-107">目標</span><span class="sxs-lookup"><span data-stu-id="87dbb-107">Objectives</span></span>

* <span data-ttu-id="87dbb-108">他の学習目的に使用される 3D オブジェクトのパネルを作成する</span><span class="sxs-lookup"><span data-stu-id="87dbb-108">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="87dbb-109">境界ボックスを実装する</span><span class="sxs-lookup"><span data-stu-id="87dbb-109">Implement bounding boxes</span></span>
* <span data-ttu-id="87dbb-110">移動、回転、拡大縮小などの基本操作のための 3D オブジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="87dbb-110">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="87dbb-111">近距離操作と遠距離操作について確認する</span><span class="sxs-lookup"><span data-stu-id="87dbb-111">Explore near and far interaction</span></span>
* <span data-ttu-id="87dbb-112">グラブやタッチなどのその他の手の追跡のジェスチャについて学習する</span><span class="sxs-lookup"><span data-stu-id="87dbb-112">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="87dbb-113">チュートリアルのアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="87dbb-113">Importing the tutorial assets</span></span>

<span data-ttu-id="87dbb-114">Unity カスタム パッケージをダウンロードしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-114">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="87dbb-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="87dbb-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)

<span data-ttu-id="87dbb-116">チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="87dbb-116">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="87dbb-118">Unity カスタム パッケージをインポートする方法については、「[Mixed Reality ツールキットをインポートする](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87dbb-118">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="87dbb-119">シーン ビューの整理</span><span class="sxs-lookup"><span data-stu-id="87dbb-119">Decluttering the scene view</span></span>

<span data-ttu-id="87dbb-120">シーンを簡単に操作できるようにするには、 **Cube** および **ButtonCollection** オブジェクトの左側にある**目**のアイコンをクリックして、それらのオブジェクトの**シーンの可視性**をオフに設定します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-120">To make it easier to work with your scene, set the **scene visibility** for the **Cube** and **ButtonCollection** objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="87dbb-121">これにより、ゲーム中の可視性を変更することなく、[Scene]\(シーン\) ウィンドウ内のオブジェクトが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="87dbb-121">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="87dbb-123">シーンの可視性コントロールと、それらを使用してシーン ビューやワークフローを最適化する方法の詳細については、Unity の <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">シーンの可視性</a>に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="87dbb-123">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="87dbb-124">コレクション内の 3D オブジェクトを整理する</span><span class="sxs-lookup"><span data-stu-id="87dbb-124">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="87dbb-125">このセクションでは、このチュートリアルの後続のセクションで 3D オブジェクトを操作するさまざまな方法を調べるときに使用する、3D オブジェクトのパネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-125">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="87dbb-126">具体的には、3D オブジェクトが 3 x 3 グリッドに配置されるように構成します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-126">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="87dbb-127">[ボタンのパネルを作成した](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)ときと同様に、これを実現するための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="87dbb-127">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="87dbb-128">3D オブジェクトを親オブジェクトにペアレント化する</span><span class="sxs-lookup"><span data-stu-id="87dbb-128">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="87dbb-129">Grid Object Collection (Script) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="87dbb-129">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="87dbb-130">1.3D オブジェクトを親オブジェクトにペアレント化する</span><span class="sxs-lookup"><span data-stu-id="87dbb-130">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="87dbb-131">[Hierarchy]\(階層\) ウィンドウで **空のオブジェクトを作成**し、適切な名前 (たとえば、**3DObjectCollection**) を付け、適切な場所 (たとえば、X = 0、Y = -0.2、Z = 2) に配置します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-131">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="87dbb-132">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)** に移動し、次のプレハブを **3DObjectCollection** に**ペアレント化します**。</span><span class="sxs-lookup"><span data-stu-id="87dbb-132">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="87dbb-133">Cheese</span><span class="sxs-lookup"><span data-stu-id="87dbb-133">Cheese</span></span>
* <span data-ttu-id="87dbb-134">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="87dbb-134">CoffeeCup</span></span>
* <span data-ttu-id="87dbb-135">EarthCore</span><span class="sxs-lookup"><span data-stu-id="87dbb-135">EarthCore</span></span>
* <span data-ttu-id="87dbb-136">Octa</span><span class="sxs-lookup"><span data-stu-id="87dbb-136">Octa</span></span>
* <span data-ttu-id="87dbb-137">Platonic</span><span class="sxs-lookup"><span data-stu-id="87dbb-137">Platonic</span></span>
* <span data-ttu-id="87dbb-138">TheModule</span><span class="sxs-lookup"><span data-stu-id="87dbb-138">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="87dbb-140">[Hierarchy]\(階層\) ウィンドウで、**3DObjectCollection** の子オブジェクトとして **3 つのキューブを作成**し、[Transform]\(変換\) の **[Scale]\(スケール\)** を X = 0.15、Y = 0.15、Z = 0.15 に設定します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-140">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="87dbb-142">上記の手順を実行する方法については、「[ユーザー インターフェイスの作成と Mixed Reality ツールキットの構成](mrlearning-base-ch2.md)」チュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="87dbb-142">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="87dbb-143">各キューブが表示されるように、キューブを再配置します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-143">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="87dbb-145">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MixedRealityToolkit.SDK]**  >  **[StandardAssets]**  >  **[Materials]\(素材\)** に移動し、MRTK で提供されている素材を確認します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-145">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="87dbb-146">各キューブの [Mesh Renderer]\(メッシュ レンダラー\) の **[Materials]\(素材\)** の [Element 0]\(要素 0\) プロパティに適切な素材を**クリックしてドラッグします**。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-146">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="87dbb-147">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="87dbb-147">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="87dbb-148">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="87dbb-148">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="87dbb-149">MRTK_Standard_Green</span><span class="sxs-lookup"><span data-stu-id="87dbb-149">MRTK_Standard_Green</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="87dbb-151">2.Grid Object Collection (Script) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="87dbb-151">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="87dbb-152">**Grid Object Collection (Script)** コンポーネントを **3DObjectCollection** オブジェクトに追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-152">Add a **Grid Object Collection (Script)** component to the **3DObjectCollection** object, and configure it as follows:</span></span>

* <span data-ttu-id="87dbb-153">**[Sort Type]\(並べ替えの種類\)** を **[Child Order]\(子の順序\)** に変更して、子オブジェクトが、親オブジェクトの下に配置した順序で並べ替えられるようにします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-153">Change **Sort Type** to **Child Order** to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="87dbb-154">次に、 **[Update Collection]\(コレクションの更新\)** ボタンをクリックして、新しい構成を適用します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-154">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="87dbb-156">3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="87dbb-156">Manipulating 3D objects</span></span>

<span data-ttu-id="87dbb-157">このセクションでは、前のセクションで作成したパネル内のすべての 3D オブジェクトを操作する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-157">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="87dbb-158">またプレハブ オブジェクトの場合は、ユーザーが追跡対象の手を使用して、これらのオブジェクトに手を伸ばしてつかむことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-158">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="87dbb-159">次に、オブジェクトに適用できる操作動作をいくつか確認します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-159">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="87dbb-160">これを実現するための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="87dbb-160">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="87dbb-161">すべてのオブジェクトに Manipulation Handler (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="87dbb-161">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="87dbb-162">プレハブ オブジェクトに Near Interaction Grabbable (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="87dbb-162">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="87dbb-163">Manipulation Handler (Script) コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="87dbb-163">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="87dbb-164">**オブジェクトを操作**できるようにするには、オブジェクトに次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="87dbb-164">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="87dbb-165">**Collider** コンポーネント、たとえばボックス コライダー</span><span class="sxs-lookup"><span data-stu-id="87dbb-165">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="87dbb-166">**Manipulation Handler (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="87dbb-166">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="87dbb-167">オブジェクトを**操作**し、**追跡対象の手でオブジェクトをつかむ**ことができるようにするには、オブジェクトに次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="87dbb-167">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="87dbb-168">**Collider** コンポーネント、たとえばボックス コライダー</span><span class="sxs-lookup"><span data-stu-id="87dbb-168">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="87dbb-169">**Manipulation Handler (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="87dbb-169">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="87dbb-170">**Near Interaction Grabbable (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="87dbb-170">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="87dbb-171">1.すべてのオブジェクトに Manipulation Handler (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="87dbb-171">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="87dbb-172">[Hierarchy]\(階層\) ウィンドウで、 **[Cheese]** オブジェクトを選択し、**Shift** キーを押したまま **[Cube () 2]** オブジェクトを選択し、すべてのオブジェクトに **Manipulation Handler (Script)** コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-172">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube () 2** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="87dbb-174">このチュートリアルでは、コライダーが既にプレハブに追加されています。</span><span class="sxs-lookup"><span data-stu-id="87dbb-174">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="87dbb-175">Cube オブジェクトなどの Unity プリミティブの場合、オブジェクトが作成されるときに Collider コンポーネントが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="87dbb-175">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="87dbb-176">上の図では、コライダーは緑色のアウトラインで示されています。</span><span class="sxs-lookup"><span data-stu-id="87dbb-176">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="87dbb-177">コライダーの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">コライダー</a>に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="87dbb-177">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="87dbb-178">2.プレハブ オブジェクトに Near Interaction Grabbable (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="87dbb-178">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="87dbb-179">[Hierarchy]\(階層\) ウィンドウで、 **[Cheese]** オブジェクトを選択し、**Shift** キーを押したまま **[TheModule]** オブジェクトを選択し、すべてのオブジェクトに **Near Interaction Grabbable (Script)** コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-179">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="87dbb-181">3.Manipulation Handler (Script) コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="87dbb-181">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="87dbb-182">既定の操作</span><span class="sxs-lookup"><span data-stu-id="87dbb-182">Default manipulation</span></span>

<span data-ttu-id="87dbb-183">**Cube** オブジェクトについて、既定の操作の動作を実行するために、すべてのプロパティを既定のままにします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-183">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="87dbb-185">コンポーネントを既定値にリセットするには、コンポーネントの [Settings]\(設定\) アイコンを選択して [Reset]\(リセット\) を選択します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-185">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="87dbb-186">操作をスケールのみに制限する</span><span class="sxs-lookup"><span data-stu-id="87dbb-186">Restrict manipulation to scale only</span></span>

<span data-ttu-id="87dbb-187">**Cube (1)** オブジェクトについて、 **[Two Handed Manipulation Type]\(両手を使った操作の種類\)** を **[Scale]\(スケール\)** に変更し、ユーザーがオブジェクトのサイズのみを変更できるようにします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-187">For the **Cube (1)** object, change **Two Handed Manipulation Type** to **Scale** to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="87dbb-189">移動をユーザーから一定の距離に制限する</span><span class="sxs-lookup"><span data-stu-id="87dbb-189">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="87dbb-190">**Cube (2)** オブジェクトについて、 **[Constraint On Movement]\(動きの制限\)** を **[Fix Distance From Head]\(頭部から一定の距離\)** に変更して、オブジェクトを移動したときに、それがユーザーから同じ距離を保つようにします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-190">For the **Cube (2)** object, change **Constraint On Movement** to **Fix Distance From Head** so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="87dbb-192">既定のグラブ可能な操作</span><span class="sxs-lookup"><span data-stu-id="87dbb-192">Default grabbable manipulation</span></span>

<span data-ttu-id="87dbb-193">**Cheese**、**CoffeCup**、および **EarthCore** オブジェクトについて、すべてのプロパティを既定のままにして、既定のグラブ可能な操作の動作を実行します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-193">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="87dbb-195">遠距離操作機能を除去する</span><span class="sxs-lookup"><span data-stu-id="87dbb-195">Remove the ability of far manipulation</span></span>

<span data-ttu-id="87dbb-196">**Octa** オブジェクトについて、 **[Allow Far Manipulation]\(遠距離操作を許可\)** チェック ボックスをオフにして、ユーザーが追跡対象の手を使用した場合のみオブジェクトを直接操作できるようにします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-196">For the **Octa** object, un-check the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="87dbb-198">オブジェクトを中心を軸に回転させる</span><span class="sxs-lookup"><span data-stu-id="87dbb-198">Make an object rotate around its center</span></span>

<span data-ttu-id="87dbb-199">**Platonic** オブジェクトについて、 **[One Hand Rotation Mode Near]\(片手回転モード - 近距離\)** および **[One Hand Rotation Mode Far]\(片手回転モード - 遠距離\)** を **[Rotate About Object Center]\(オブジェクトの中心を軸に回転\)** に変更し、ユーザーがオブジェクトを 1 つの手で回転させたとき、オブジェクトが中心を軸に回転するようにします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-199">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to **Rotate About Object Center** to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a><span data-ttu-id="87dbb-201">オブジェクトを放した後も動作を続ける</span><span class="sxs-lookup"><span data-stu-id="87dbb-201">Keep movement after object is released</span></span>

<span data-ttu-id="87dbb-202">**TheModule** オブジェクトについて、**Rigidbody** コンポーネントを追加して物理的処理を有効にし、 **[Use Gravity]\(重力を使用\)** チェックボックスをオフにして、オブジェクトが重力の影響を受けないようにします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-202">For the **TheModule** object, add a **Rigidbody** component to enable physics, and then un-check the **Use Gravity** checkbox so the object is not affected by gravity:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="87dbb-204">Manipulation Handler (Script) コンポーネントに戻り、 **[Release Behavior]\(解放動作\)** が **[Keep Velocity]\(速度を維持\)** および **[Keep Angular Velocity]\(角速度を維持\)** の両方に設定されていることを確認し、オブジェクトがユーザーの手から離れた後も動き続けるようにします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-204">Back on the Manipulation Handler (Script) component, verify that the **Release Behavior** is set to both **Keep Velocity** and **Keep Angular Velocity** so that once the object is released from the user's hand, it continues to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

<span data-ttu-id="87dbb-206">Manipulation Handler コンポーネントとその関連プロパティの詳細については、[MRTK ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[操作ハンドラー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)に関するガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="87dbb-206">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="87dbb-207">境界ボックスの追加</span><span class="sxs-lookup"><span data-stu-id="87dbb-207">Adding bounding boxes</span></span>

<span data-ttu-id="87dbb-208">境界ボックスには、拡大縮小および回転に使用できるハンドルが用意されているため、1 つの手で、近距離と遠距離の両方のオブジェクトを操作するのがより簡単かつ直感的になります。</span><span class="sxs-lookup"><span data-stu-id="87dbb-208">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="87dbb-209">この例では、EarthCore オブジェクトに境界ボックスを追加して、前のセクションで構成したオブジェクト操作、および境界ボックスのハンドルを使用した拡大縮小と回転を使用して、このオブジェクトを操作できるようにします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-209">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="87dbb-210">**境界ボックス**を使用できるようにするには、オブジェクトに次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="87dbb-210">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="87dbb-211">**Collider** コンポーネント、たとえばボックス コライダー</span><span class="sxs-lookup"><span data-stu-id="87dbb-211">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="87dbb-212">**Bounding Box (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="87dbb-212">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="87dbb-213">1.Bounding Box (Script) コンポーネントを EarthCore オブジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="87dbb-213">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="87dbb-214">[Inspector]\(インスペクター\) ウィンドウで **[EarthCore]** オブジェクトを選択し、**Bounding Box (Script)** コンポーネントを EarthCore オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-214">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="87dbb-216">境界ボックスの視覚エフェクトは実行時に作成されるため、ゲーム モードに入る前は表示されません。</span><span class="sxs-lookup"><span data-stu-id="87dbb-216">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="87dbb-217">2.エディター内のシミュレーションを使用して境界ボックスを視覚化およびテストする</span><span class="sxs-lookup"><span data-stu-id="87dbb-217">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="87dbb-218">[Play]\(再生\) ボタンを押してゲーム モードに入ります。</span><span class="sxs-lookup"><span data-stu-id="87dbb-218">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="87dbb-219">次に、スペースキーを押して保持することで手を表示し、マウスを使用して境界ボックスを操作します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-219">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="87dbb-221">Bounding Box コンポーネントとその関連プロパティの詳細については、[MRTK ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[境界ボックス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)に関するガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="87dbb-221">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="87dbb-222">タッチ エフェクトの追加</span><span class="sxs-lookup"><span data-stu-id="87dbb-222">Adding touch effects</span></span>

<span data-ttu-id="87dbb-223">この例では、手でオブジェクトに触れたときにイベントがトリガーされるようにします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-223">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="87dbb-224">具体的には、ユーザーが触れたときにサウンド エフェクトが再生されるように Octa オブジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-224">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="87dbb-225">これを実現するための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="87dbb-225">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="87dbb-226">オブジェクトに Audio Source コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="87dbb-226">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="87dbb-227">オブジェクトに Near Interaction Touchable (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="87dbb-227">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="87dbb-228">オブジェクトに Hand Interaction Touch (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="87dbb-228">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="87dbb-229">On Touch Started イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="87dbb-229">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="87dbb-230">エディター内のシミュレーションを使用してタッチ操作をテストする</span><span class="sxs-lookup"><span data-stu-id="87dbb-230">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="87dbb-231">**タッチ イベントをトリガー**できるようにするには、オブジェクトに次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="87dbb-231">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="87dbb-232">**Collider** コンポーネント、可能であればボックス コライダー</span><span class="sxs-lookup"><span data-stu-id="87dbb-232">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="87dbb-233">**Near Interaction Touchable (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="87dbb-233">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="87dbb-234">**Hand Interaction Touch (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="87dbb-234">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="87dbb-235">Hand Interaction Touch (Script) コンポーネントは MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="87dbb-235">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="87dbb-236">これはこのチュートリアルのアセットと共にインポートされ、もともとは Mixed Reality ツールキットの Unity の例の一部でした。</span><span class="sxs-lookup"><span data-stu-id="87dbb-236">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="87dbb-237">1.オブジェクトに Audio Source コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="87dbb-237">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="87dbb-238">[Hierarchy]\(階層\) ウィンドウで、 **[Octa]** オブジェクトを選択し、**Audio Source** コンポーネントを Octa オブジェクトに追加します。次に、 **[Spatial Blend]\(空間ブレンド\)** を 1 に変更して、空間オーディオを有効にします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-238">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="87dbb-240">2.オブジェクトに Near Interaction Touchable (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="87dbb-240">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="87dbb-241">**[Octa]** オブジェクトが選択された状態で、**Near Interaction Touchable (Script)** コンポーネントを Octa オブジェクトに追加します。次に、 **[Fix Bounds]\(境界の修正\)** および **[Fix Center]\(センターの修正\)** ボタンをクリックして、Near Interaction Touchable (Script) の [Local Center]\(ローカルのセンター\) および [Bounds]\(境界\) のプロパティを BoxCollider に一致するように更新します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-241">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="87dbb-243">3.オブジェクトに Hand Interaction Touch (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="87dbb-243">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="87dbb-244">**[Octa]** オブジェクトを選択した状態で、**Hand Interaction Touch (Script)** コンポーネントを Octa オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-244">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="87dbb-246">4.On Touch Started イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="87dbb-246">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="87dbb-247">**Hand Interaction Touch (Script)** コンポーネントで、小さい **+** アイコンをクリックして、新しい **On Touch Started ()** イベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-247">On the **Hand Interaction Touch (Script)** component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="87dbb-248">次に、イベントを受信するように **Octa** オブジェクトを構成し、トリガーされるアクションとして **AudioSource.PlayOneShot** を定義します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-248">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="87dbb-250">**[Assets]\(アセット\)**  >  **[MixedRealityToolkit.SDK]**  >  **[StandardAssets]**  >  **[Audio]\(オーディオ\)** に移動して、MRTK で提供されているオーディオ クリップを表示します。次に、適切なオーディオ クリップ (MRTK_Gem オーディオ クリップなど) を **[Audio Clip]\(オーディオ クリップ\)** フィールドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="87dbb-250">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Audio** to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="87dbb-252">イベントを実装する方法については、「[手の追跡のジェスチャと操作可能なボタン](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)」の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87dbb-252">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="87dbb-253">5.エディター内のシミュレーションを使用してタッチ操作をテストする</span><span class="sxs-lookup"><span data-stu-id="87dbb-253">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="87dbb-254">[Play]\(再生\) ボタンを押してゲーム モードに入ります。</span><span class="sxs-lookup"><span data-stu-id="87dbb-254">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="87dbb-255">次に、スペースキーを押して保持することで手を表示し、マウスを使用して Octa オブジェクトに触れてサウンド エフェクトをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="87dbb-255">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="87dbb-257">タッチ操作のテスト時に見られるように、また上の図に示すように、Octa オブジェクトに触れている間、その色は脈打つように変化します。</span><span class="sxs-lookup"><span data-stu-id="87dbb-257">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="87dbb-258">このエフェクトは、前述の手順で実行したイベント構成の結果ではなく、Hand Interaction Touch (Script) コンポーネントにハード コーディングされています。</span><span class="sxs-lookup"><span data-stu-id="87dbb-258">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="87dbb-259">このエフェクトを無効にする場合は、たとえば 32 行目の 'TargetRenderer = GetComponentInChildren<Renderer>();' をコメントアウトすると、TargetRenderer が null のままになり、色は脈打つように変化しません。</span><span class="sxs-lookup"><span data-stu-id="87dbb-259">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="87dbb-260">結論</span><span class="sxs-lookup"><span data-stu-id="87dbb-260">Congratulations</span></span>

<span data-ttu-id="87dbb-261">このチュートリアルでは、3D オブジェクトをグリッド コレクションに整理する方法と、近距離操作 (追跡対象の手で直接グラブ) と遠距離操作 (視線または手の光線を使用) を使用してこれらのオブジェクトを操作 (拡大縮小、回転、および移動) する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="87dbb-261">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="87dbb-262">また、3D オブジェクトの周りに境界ボックスを配置する方法と、境界ボックスのハンドルの使用とカスタマイズの方法についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="87dbb-262">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="87dbb-263">最後に、オブジェクトにタッチしたときにイベントをトリガーする方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="87dbb-263">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="87dbb-264">次のレッスン:6.高度な入力オプションの探索</span><span class="sxs-lookup"><span data-stu-id="87dbb-264">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
