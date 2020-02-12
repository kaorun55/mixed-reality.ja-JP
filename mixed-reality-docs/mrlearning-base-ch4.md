---
title: 入門チュートリアル-5. 3D オブジェクトとの対話
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: a1b26d56b4693ef23f2d77ba53e0961693489a3a
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130283"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="5d9af-104">5. 3D オブジェクトとの対話</span><span class="sxs-lookup"><span data-stu-id="5d9af-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="5d9af-105">このチュートリアルでは、基本的な3D コンテンツとユーザーエクスペリエンスについて学習します。これには、コレクションの一部としての3D オブジェクトの整理、基本的な操作のための境界ボックス、近辺と遠くの対話、およびハンドトラッキングによるタッチやグラブのジェスチャなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5d9af-105">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="5d9af-106">目標</span><span class="sxs-lookup"><span data-stu-id="5d9af-106">Objectives</span></span>

* <span data-ttu-id="5d9af-107">他の学習目的に使用される3D オブジェクトのパネルを作成する</span><span class="sxs-lookup"><span data-stu-id="5d9af-107">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="5d9af-108">境界ボックスを実装する</span><span class="sxs-lookup"><span data-stu-id="5d9af-108">Implement bounding boxes</span></span>
* <span data-ttu-id="5d9af-109">移動、回転、拡大/縮小などの基本的な操作のために3D オブジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="5d9af-109">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="5d9af-110">近距離操作と遠距離操作について確認する</span><span class="sxs-lookup"><span data-stu-id="5d9af-110">Explore near and far interaction</span></span>
* <span data-ttu-id="5d9af-111">グラブやタッチなど、その他のハンドトラッキングジェスチャについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-111">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="5d9af-112">チュートリアル資産のインポート</span><span class="sxs-lookup"><span data-stu-id="5d9af-112">Importing the tutorial assets</span></span>

<span data-ttu-id="5d9af-113">Unity カスタムパッケージをダウンロードしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="5d9af-113">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="5d9af-114">MRTK。HoloLens2. 2.2.0.0. unitypackage を実行します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-114">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage)

<span data-ttu-id="5d9af-115">チュートリアルのアセットをインポートすると、プロジェクトウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5d9af-115">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="5d9af-117">Unity カスタムパッケージをインポートする方法については、「 [Mixed Reality Toolkit のインポート](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d9af-117">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="5d9af-118">シーンビューの Decluttering</span><span class="sxs-lookup"><span data-stu-id="5d9af-118">Decluttering the scene view</span></span>

<span data-ttu-id="5d9af-119">シーンを簡単に操作できるようにするには、オブジェクトの左側にある**目**のアイコンをクリックして、キューブおよび buttoncollection オブジェクトの**シーンの表示**をオフに設定します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-119">To make it easier to work with your scene, set the **scene visibility** for the Cube and ButtonCollection objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="5d9af-120">これにより、シーンウィンドウ内のオブジェクトが非表示になります。ゲーム中の可視性は変更されません。</span><span class="sxs-lookup"><span data-stu-id="5d9af-120">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="5d9af-122">シーンの可視性の制御とそれらを使用してシーンビューやワークフローを最適化する方法の詳細については、Unity の<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">シーンの可視性</a>に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d9af-122">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="5d9af-123">コレクション内の3D オブジェクトの整理</span><span class="sxs-lookup"><span data-stu-id="5d9af-123">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="5d9af-124">このセクションでは、このチュートリアルの次のセクションで3D オブジェクトを操作するさまざまな方法を調べるときに使用する、3D オブジェクトのパネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-124">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="5d9af-125">具体的には、3D オブジェクトが 3 x 3 グリッドに配置されるように構成します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-125">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="5d9af-126">[ボタンのパネルを作成](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)したときと同様に、これを実現するための主要な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5d9af-126">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="5d9af-127">親オブジェクトへの3D オブジェクトの親</span><span class="sxs-lookup"><span data-stu-id="5d9af-127">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="5d9af-128">Grid オブジェクトコレクション (スクリプト) コンポーネントの追加と構成</span><span class="sxs-lookup"><span data-stu-id="5d9af-128">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="5d9af-129">1. 3D オブジェクトを親オブジェクトに親します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-129">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="5d9af-130">[階層] ウィンドウで、**空のオブジェクトを作成**し、適切な名前 (たとえば、 **3DObjectCollection**) を指定し、適切な場所に配置します (例: X = 0、Y =-0.2、Z = 2)。</span><span class="sxs-lookup"><span data-stu-id="5d9af-130">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="5d9af-131">[プロジェクト] ウィンドウで、[**アセット** > **mrtk] に移動します。チュートリアル: GettingStarted** **Prefabs**を開始し、次の Prefabs を**3DObjectCollection**に**親**とします。 > </span><span class="sxs-lookup"><span data-stu-id="5d9af-131">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **Parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="5d9af-132">頭</span><span class="sxs-lookup"><span data-stu-id="5d9af-132">Cheese</span></span>
* <span data-ttu-id="5d9af-133">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="5d9af-133">CoffeeCup</span></span>
* <span data-ttu-id="5d9af-134">EarthCore</span><span class="sxs-lookup"><span data-stu-id="5d9af-134">EarthCore</span></span>
* <span data-ttu-id="5d9af-135">Octa</span><span class="sxs-lookup"><span data-stu-id="5d9af-135">Octa</span></span>
* <span data-ttu-id="5d9af-136">プラトニック</span><span class="sxs-lookup"><span data-stu-id="5d9af-136">Platonic</span></span>
* <span data-ttu-id="5d9af-137">モジュール</span><span class="sxs-lookup"><span data-stu-id="5d9af-137">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="5d9af-139">[階層] ウィンドウで、 **3DObjectCollection**の子オブジェクトとして**3 つのキューブを作成**し、変換の**スケール**を X = 0.15、Y = 0.15、Z = 0.15 に設定します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-139">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

<!-- TODO: Finish -->
> [!TIP]
> <span data-ttu-id="5d9af-141">上記の手順を実行する方法については、「[ユーザーインターフェイスの作成」および「Mixed Reality Toolkit の構成](mrlearning-base-ch2.md)」のチュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d9af-141">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="5d9af-142">各キューブを表示できるように、キューブの位置を変更します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-142">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="5d9af-144">[プロジェクト] ウィンドウで、[**資産** > **MixedRealityToolkit** > **standardassets** > **マテリアル**] に移動し、mrtk で提供されている素材を確認します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-144">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="5d9af-145">次の例のように、適切な素材を各キューブのメッシュ**レンダラーの**要素0プロパティに**ドラッグ**アンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="5d9af-145">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="5d9af-146">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="5d9af-146">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="5d9af-147">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="5d9af-147">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="5d9af-148">MRTK_Standard_Green:</span><span class="sxs-lookup"><span data-stu-id="5d9af-148">MRTK_Standard_Green:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="5d9af-150">2. Grid オブジェクトコレクション (スクリプト) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="5d9af-150">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="5d9af-151">**Grid オブジェクトコレクション (スクリプト)** コンポーネントを3DObjectCollection オブジェクトに追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-151">Add a **Grid Object Collection (Script)** component to the 3DObjectCollection object, and configure it as follows:</span></span>

* <span data-ttu-id="5d9af-152">子オブジェクトが親オブジェクトの下に配置された順序で並べ替えられるようにするには、**並べ替えの種類** を 子の順序 に変更します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-152">Change **Sort Type** to Child Order to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="5d9af-153">次に、 **[コレクションの更新]** ボタンをクリックして、新しい構成を適用します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-153">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="5d9af-155">3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="5d9af-155">Manipulating 3D objects</span></span>

<span data-ttu-id="5d9af-156">このセクションでは、前のセクションで作成したパネル内のすべての3D オブジェクトを操作する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-156">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="5d9af-157">さらに、prefab オブジェクトの場合は、ユーザーが追跡したハンドを使用してこれらのオブジェクトを取得して取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5d9af-157">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="5d9af-158">次に、オブジェクトに適用できるいくつかの操作の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-158">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="5d9af-159">これを実現するには、主に次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-159">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="5d9af-160">すべてのオブジェクトに操作ハンドラー (スクリプト) コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-160">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="5d9af-161">Near 相互作用 Grabbable (スクリプト) コンポーネントを prefab オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-161">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="5d9af-162">操作ハンドラー (スクリプト) コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="5d9af-162">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d9af-163">**オブジェクトを操作**できるようにするには、オブジェクトに次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="5d9af-163">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="5d9af-164">**Collider**コンポーネント (Box collider など)</span><span class="sxs-lookup"><span data-stu-id="5d9af-164">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="5d9af-165">**操作ハンドラー (スクリプト)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5d9af-165">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="5d9af-166">**追跡したハンドを使用**してオブジェクトを**操作**および取得できるようにするには、オブジェクトに次のコンポーネントが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d9af-166">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="5d9af-167">**Collider**コンポーネント (Box collider など)</span><span class="sxs-lookup"><span data-stu-id="5d9af-167">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="5d9af-168">**操作ハンドラー (スクリプト)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5d9af-168">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="5d9af-169">**Near 相互作用 Grabbable (スクリプト)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5d9af-169">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="5d9af-170">1. 操作ハンドラー (スクリプト) コンポーネントをすべてのオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-170">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="5d9af-171">階層 ウィンドウで、**チーズ** オブジェクトを選択し、 **shift**キーを押したまま**Cube ()** オブジェクトを選択して、**操作ハンドラー (スクリプト)** コンポーネントをすべてのオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-171">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube ()** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="5d9af-173">このチュートリアルでは、colliders が既に prefabs に追加されています。</span><span class="sxs-lookup"><span data-stu-id="5d9af-173">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="5d9af-174">キューブオブジェクトなどの Unity プリミティブの場合、オブジェクトの作成時に Collider コンポーネントが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="5d9af-174">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="5d9af-175">上の図では、colliders は緑色のアウトラインで表されています。</span><span class="sxs-lookup"><span data-stu-id="5d9af-175">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="5d9af-176">Colliders の詳細については、Unity の<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a>のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d9af-176">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="5d9af-177">2. Near の相互作用 Grabbable (スクリプト) コンポーネントを prefab オブジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="5d9af-177">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="5d9af-178">階層 ウィンドウで、**チーズ** オブジェクトを選択し、 **shift**キーを押したまま、**モジュール** オブジェクトを選択し、 **Near インタラクション Grabbable (スクリプト)** コンポーネントをすべてのオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-178">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="5d9af-180">3. 操作ハンドラー (スクリプト) コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="5d9af-180">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="5d9af-181">既定の操作</span><span class="sxs-lookup"><span data-stu-id="5d9af-181">Default manipulation</span></span>

<span data-ttu-id="5d9af-182">既定の操作動作を実行するには、**キューブ**オブジェクトに対して、すべてのプロパティを既定のままにします。</span><span class="sxs-lookup"><span data-stu-id="5d9af-182">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="5d9af-184">コンポーネントを既定値にリセットするには、コンポーネントの設定アイコンを選択し、[リセット] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-184">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="5d9af-185">操作をスケールのみに制限する</span><span class="sxs-lookup"><span data-stu-id="5d9af-185">Restrict manipulation to scale only</span></span>

<span data-ttu-id="5d9af-186">**Cube (1)** オブジェクトの場合は、 **2 つのきき操作の種類**を Scale に変更し、ユーザーがオブジェクトのサイズを変更できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5d9af-186">For the **Cube (1)** object, change **Two Handed Manipulation Type** to Scale to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="5d9af-188">ユーザーからの固定距離への移動を制限する</span><span class="sxs-lookup"><span data-stu-id="5d9af-188">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="5d9af-189">**Cube (2)** オブジェクトの場合は、移動時**に制約**を変更して、オブジェクトが移動されたときに、ユーザーからの距離を維持したままにします。</span><span class="sxs-lookup"><span data-stu-id="5d9af-189">For the **Cube (2)** object, change **Constraint On Movement** to Fix Distance From Head so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="5d9af-191">既定の grabbable 操作</span><span class="sxs-lookup"><span data-stu-id="5d9af-191">Default grabbable manipulation</span></span>

<span data-ttu-id="5d9af-192">**チーズ**、 **CoffeCup**、および**EarthCore**オブジェクトの場合は、既定ですべてのプロパティをそのままにして、既定の grabbable 操作動作を体験します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-192">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="5d9af-194">遠くの操作の機能を削除する</span><span class="sxs-lookup"><span data-stu-id="5d9af-194">Remove the ability of far manipulation</span></span>

<span data-ttu-id="5d9af-195">**Octa**オブジェクトの場合は、[**遠隔操作を許可**する] チェックボックスをオフにして、ユーザーが追跡したハンドを使用して直接オブジェクトと対話できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5d9af-195">For the **Octa** object, uncheck the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="5d9af-197">オブジェクトを中央に回転させる</span><span class="sxs-lookup"><span data-stu-id="5d9af-197">Make an object rotate around its center</span></span>

<span data-ttu-id="5d9af-198">**プラトニック**オブジェクトの場合は、一方の**手の回転モードの近く**と1つの手回転モードを**遠く**に回転させます。これにより、ユーザーがオブジェクトを1つ回転させると、オブジェクトの中心を中心に回転します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-198">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to Rotate About Object Center to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="prevent-movement-after-object-is-released"></a><span data-ttu-id="5d9af-200">オブジェクトが解放された後の移動を禁止する</span><span class="sxs-lookup"><span data-stu-id="5d9af-200">Prevent movement after object is released</span></span>

<span data-ttu-id="5d9af-201">**モジュール**オブジェクトの場合は、**リリース動作**を何も変更しないでください。これにより、オブジェクトがユーザーの手から解放されると、移動は続行されません。</span><span class="sxs-lookup"><span data-stu-id="5d9af-201">For the **TheModule** object, change **Release Behavior** to Nothing so that once the object is released from the user's hand, it doesn’t continue to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="5d9af-203">操作ハンドラーコンポーネントとそれに関連付けられているプロパティの詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[操作ハンドラー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)ガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d9af-203">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="5d9af-204">境界ボックスの追加</span><span class="sxs-lookup"><span data-stu-id="5d9af-204">Adding bounding boxes</span></span>

<span data-ttu-id="5d9af-205">境界ボックスを使用すると、拡大縮小および回転に使用できるハンドルを提供することによって、近距離および遠くの相互作用のために、オブジェクトを簡単かつ直感的に操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="5d9af-205">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="5d9af-206">この例では、EarthCore オブジェクトに境界ボックスを追加します。これにより、前のセクションで構成したオブジェクト操作を使用して、境界ボックスハンドルを使用してスケールおよび回転することで、このオブジェクトと対話できるようになります。</span><span class="sxs-lookup"><span data-stu-id="5d9af-206">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d9af-207">**境界ボックス**を使用できるようにするには、オブジェクトに次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="5d9af-207">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="5d9af-208">**Collider**コンポーネント (Box collider など)</span><span class="sxs-lookup"><span data-stu-id="5d9af-208">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="5d9af-209">**境界ボックス (スクリプト)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5d9af-209">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="5d9af-210">1. 境界ボックス (スクリプト) コンポーネントを EarthCore オブジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="5d9af-210">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="5d9af-211">[インスペクター] ウィンドウで、 **EarthCore**オブジェクトを選択し、**境界ボックス (スクリプト)** コンポーネントを EarthCore オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-211">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="5d9af-213">境界ボックスの視覚エフェクトは実行時に作成されるため、ゲームモードに入る前には表示されません。</span><span class="sxs-lookup"><span data-stu-id="5d9af-213">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="5d9af-214">2. エディター内シミュレーションを使用して境界ボックスを視覚化およびテストする</span><span class="sxs-lookup"><span data-stu-id="5d9af-214">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="5d9af-215">再生ボタンを押してゲームモードに入ります。</span><span class="sxs-lookup"><span data-stu-id="5d9af-215">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="5d9af-216">次に、space キーを押して手を置き、マウスを使用して境界ボックスと対話します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-216">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="5d9af-218">境界ボックスコンポーネントとそれに関連付けられているプロパティの詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[境界ボックス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)ガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d9af-218">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="5d9af-219">タッチ効果の追加</span><span class="sxs-lookup"><span data-stu-id="5d9af-219">Adding touch effects</span></span>

<span data-ttu-id="5d9af-220">この例では、手の形でオブジェクトを操作したときにイベントがトリガーされるようにします。</span><span class="sxs-lookup"><span data-stu-id="5d9af-220">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="5d9af-221">具体的には、ユーザーが操作したときにサウンド効果を再生するように、Octa オブジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-221">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="5d9af-222">これを実現するには、主に次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-222">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="5d9af-223">オーディオソースコンポーネントをオブジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="5d9af-223">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="5d9af-224">Near 相互作用 Touchable (スクリプト) コンポーネントをオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-224">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="5d9af-225">オブジェクトにハンドインタラクションタッチ (スクリプト) コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-225">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="5d9af-226">タッチ開始イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="5d9af-226">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="5d9af-227">エディター内シミュレーションを使用したタッチ操作のテスト</span><span class="sxs-lookup"><span data-stu-id="5d9af-227">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d9af-228">**タッチイベントをトリガー**できるようにするには、オブジェクトに次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="5d9af-228">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="5d9af-229">**Collider**コンポーネント (可能であれば Box Collider)</span><span class="sxs-lookup"><span data-stu-id="5d9af-229">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="5d9af-230">**Near 相互作用 Touchable (スクリプト)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5d9af-230">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="5d9af-231">**ハンドインタラクションタッチ (スクリプト)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5d9af-231">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="5d9af-232">手書き操作タッチ (スクリプト) コンポーネントは、MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="5d9af-232">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="5d9af-233">このチュートリアルのアセットと共にインポートされ、もともとは MixedReality Toolkit Unity の例に含まれています。</span><span class="sxs-lookup"><span data-stu-id="5d9af-233">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="5d9af-234">1. オーディオソースコンポーネントをオブジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="5d9af-234">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="5d9af-235">[階層] ウィンドウで、 **Octa**オブジェクトを選択し、**オーディオソース**コンポーネントを octa オブジェクトに追加します。次に、空間**ブレンド**を1に変更して、空間オーディオを有効にします。</span><span class="sxs-lookup"><span data-stu-id="5d9af-235">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="5d9af-237">2. Near 相互作用 Touchable (スクリプト) コンポーネントをオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-237">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="5d9af-238">**Octa**オブジェクトを選択した状態で、 **Touchable (スクリプト)** コンポーネントを octa オブジェクトに追加します。次に、 **[境界の修正]** と センターの **[修正]** ボタンをクリックして、Near 相互作用 Touchable (スクリプト) のローカルの中央および境界のプロパティを boxcollider と一致するように更新します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-238">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="5d9af-240">3. ハンドインタラクションタッチ (スクリプト) コンポーネントをオブジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="5d9af-240">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="5d9af-241">**Octa**オブジェクトを選択した状態で、次のように、**手動インタラクションタッチ (スクリプト)** コンポーネントを octa オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-241">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="5d9af-243">4. タッチ開始イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="5d9af-243">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="5d9af-244">手書き入力タッチ (スクリプト) コンポーネントで、小さい **+** アイコンをクリックし**て、タッチ開始 ()** イベントの新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-244">On the Hand Interaction Touch (Script) component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="5d9af-245">次に、イベントを受信するように**Octa**オブジェクトを構成し、トリガーされるアクションとして**PlayOneShot**を定義します。</span><span class="sxs-lookup"><span data-stu-id="5d9af-245">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="5d9af-247">**[アセット]**  > [ **> > ]** に移動して、mrtk で提供されているオーディオクリップを表示し、適切なオーディオクリップを**オーディオクリップ**フィールド (たとえば、MRTK_Gem オーディオクリップ) に**割り当てます。**</span><span class="sxs-lookup"><span data-stu-id="5d9af-247">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="5d9af-249">イベントの実装方法に関する注意事項については、「[ハンドトラッキングジェスチャ」と「対話型 buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d9af-249">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="5d9af-250">5. エディター内のシミュレーションを使用してタッチ操作をテストする</span><span class="sxs-lookup"><span data-stu-id="5d9af-250">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="5d9af-251">再生ボタンを押してゲームモードに入ります。</span><span class="sxs-lookup"><span data-stu-id="5d9af-251">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="5d9af-252">次に、space キーを押して手を置き、マウスを使用して Octa オブジェクトにタッチし、サウンド効果をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="5d9af-252">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="5d9af-254">タッチ操作のテスト時に見たように、上の図に示すように、処理されたときに、Octa オブジェクトの色が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5d9af-254">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="5d9af-255">この効果は、前述の手順で完了したイベント構成の結果ではなく、ハンドインタラクションタッチ (スクリプト) コンポーネントにハードコーディングされます。</span><span class="sxs-lookup"><span data-stu-id="5d9af-255">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="5d9af-256">この効果を無効にする場合は、たとえばコメントアウトまたは行 32 ' TargetRenderer = GetComponentInChildren<Renderer>(); ' を指定すると、TargetRenderer が null になり、色はません。</span><span class="sxs-lookup"><span data-stu-id="5d9af-256">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="5d9af-257">結論</span><span class="sxs-lookup"><span data-stu-id="5d9af-257">Congratulations</span></span>

<span data-ttu-id="5d9af-258">このチュートリアルでは、グリッドコレクション内の3D オブジェクトを整理する方法と、近くの操作 (追跡したハンドを使用した直接グラブ) と遠くの相互作用 (宝石を使用した、または光線を使用) を使用して、これらのオブジェクトを操作する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="5d9af-258">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="5d9af-259">また、3D オブジェクトの周囲に境界ボックスを配置する方法と、境界ボックスでハンドルを使用およびカスタマイズする方法についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="5d9af-259">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="5d9af-260">最後に、オブジェクトにタッチしたときにイベントをトリガーする方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="5d9af-260">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="5d9af-261">次のレッスン: 6. 詳細な入力オプションの調査</span><span class="sxs-lookup"><span data-stu-id="5d9af-261">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
