---
title: 入門チュートリアル-5. 3D オブジェクトとの対話
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 8c60d8291ede123817c93458fff003891169840c
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105973"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="e275a-104">5. 3D オブジェクトとの対話</span><span class="sxs-lookup"><span data-stu-id="e275a-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="e275a-105">このチュートリアルでは、基本的な3D コンテンツとユーザーエクスペリエンスについて学習します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e275a-105">In this tutorial, you will learn about basic 3D content and user experience, such as:</span></span>

* <span data-ttu-id="e275a-106">コレクションの一部としての3D オブジェクトの整理</span><span class="sxs-lookup"><span data-stu-id="e275a-106">Organizing 3D objects as part of a collection</span></span>
* <span data-ttu-id="e275a-107">基本操作のための境界ボックス</span><span class="sxs-lookup"><span data-stu-id="e275a-107">Bounding boxes for basic manipulation</span></span>
* <span data-ttu-id="e275a-108">Near と far の相互作用</span><span class="sxs-lookup"><span data-stu-id="e275a-108">Near and far interaction</span></span>
* <span data-ttu-id="e275a-109">ハンドトラッキングを使用したタッチジェスチャとグラブジェスチャ</span><span class="sxs-lookup"><span data-stu-id="e275a-109">Touch and grab gestures with hand tracking</span></span>

## <a name="objectives"></a><span data-ttu-id="e275a-110">目標</span><span class="sxs-lookup"><span data-stu-id="e275a-110">Objectives</span></span>

* <span data-ttu-id="e275a-111">MRTK の grid オブジェクトコレクションで3D コンテンツを整理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e275a-111">Learn how to organize 3D content with MRTK's grid object collection</span></span>
* <span data-ttu-id="e275a-112">境界ボックスを実装する</span><span class="sxs-lookup"><span data-stu-id="e275a-112">Implement bounding boxes</span></span>
* <span data-ttu-id="e275a-113">基本的な操作のための3D オブジェクトの構成--移動、回転、およびスケール</span><span class="sxs-lookup"><span data-stu-id="e275a-113">Configure 3D objects for basic manipulation--move, rotate, and scale</span></span>
* <span data-ttu-id="e275a-114">近距離操作と遠距離操作について確認する</span><span class="sxs-lookup"><span data-stu-id="e275a-114">Explore near and far interaction</span></span>
* <span data-ttu-id="e275a-115">グラブやタッチなど、その他のハンドトラッキングジェスチャについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e275a-115">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="instructions"></a><span data-ttu-id="e275a-116">手順</span><span class="sxs-lookup"><span data-stu-id="e275a-116">Instructions</span></span>

### <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="e275a-117">3D オブジェクトをコレクションに整理する</span><span class="sxs-lookup"><span data-stu-id="e275a-117">Organizing 3D Objects in a Collection</span></span>

1. <span data-ttu-id="e275a-118">階層を右クリックし、[空の作成] を選択して空の game オブジェクトを作成し、名前を3DObjectCollection に変更して、x = 0、y = 0、z = 0 に配置されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e275a-118">Right-click on your hierarchy and select Create Empty to create an empty game object, rename it to 3DObjectCollection, and make sure it is positioned at x = 0, y = 0, and z = 0.</span></span>

    ![mrlearning-base-ch4-1-step1](images/mrlearning-base-ch4-1-step1.png)

2. <span data-ttu-id="e275a-120">Unity パッケージ HoloLens2 をダウンロードし、[レッスン1から](mrlearning-base-ch1.md)に記載されているカスタムパッケージをインポートする場合と同じ手順を使用して[2.1.0.0](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)をインポートします。</span><span class="sxs-lookup"><span data-stu-id="e275a-120">Download the Unity package [Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) and import it using the same instructions to import custom packages outlined in [Lesson1](mrlearning-base-ch1.md).</span></span> <span data-ttu-id="e275a-121">このパッケージには、このチュートリアル全体で使用される3D モデルとその他の便利なアセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e275a-121">This package includes 3D models and other useful assets that are used throughout this tutorial.</span></span>

3. <span data-ttu-id="e275a-122">[プロジェクト] パネルで、[資産 > BaseModuleAssets] > ベースモジュール Prefabs に移動し、"不完全" を検索します。これらの Prefabs の一部を使用します。</span><span class="sxs-lookup"><span data-stu-id="e275a-122">In the Project panel, navigate to Assets > BaseModuleAssets > Base Module Prefabs and search for "incomplete", we will use some of these prefabs.</span></span>

    ![mrlearning-base-ch4-1-step3](images/mrlearning-base-ch4-1-step3.png)

4. <span data-ttu-id="e275a-124">コーヒーカップを手順 1. の 3DObjectCollection game オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e275a-124">Drag the coffee cup into the 3DObjectCollection game object from Step 1.</span></span> <span data-ttu-id="e275a-125">これでコーヒー カップはコレクションの子になりました。</span><span class="sxs-lookup"><span data-stu-id="e275a-125">The coffee cup is now a child of the collection.</span></span>

    ![mrlearning-base-ch4-1-step4](images/mrlearning-base-ch4-1-step4.png)

5. <span data-ttu-id="e275a-127">次に、前の手順と同じプロセスに従って、3D オブジェクトをシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="e275a-127">Next, you'll add more 3D objects into our scene by following the same process as in the previous step.</span></span> <span data-ttu-id="e275a-128">この例で追加するオブジェクトの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e275a-128">Below is a list of objects to add in this example.</span></span> <span data-ttu-id="e275a-129">オブジェクトを追加すると、さまざまなサイズのシーンにオブジェクトが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="e275a-129">As you add the objects, you might find they appear in your scene in various sizes.</span></span> <span data-ttu-id="e275a-130">[インスペクター] パネルの [変換の設定] で、各3D モデルのスケールを調整します。</span><span class="sxs-lookup"><span data-stu-id="e275a-130">Adjust the scale of each 3D model under Transform settings in the Inspector panel.</span></span> <span data-ttu-id="e275a-131">この例で推奨される調整とそのオブジェクトを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="e275a-131">Recommended adjustments for this example are listed with the objects below.</span></span>

    * <span data-ttu-id="e275a-132">Cheese_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="e275a-132">Cheese_BaseModuleIncomplete.</span></span> <span data-ttu-id="e275a-133">Scale: x = 0.05、y = 0.05、z = 0.05。</span><span class="sxs-lookup"><span data-stu-id="e275a-133">Scale: x = 0.05, y = 0.05, z = 0.05.</span></span>
    * <span data-ttu-id="e275a-134">CoffeeCup_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="e275a-134">CoffeeCup_BaseModuleIncomplete.</span></span> <span data-ttu-id="e275a-135">Scale: x = 0.1、y = 0.1、z = 0.1。</span><span class="sxs-lookup"><span data-stu-id="e275a-135">Scale: x = 0.1, y = 0.1, z = 0.1.</span></span>
    * <span data-ttu-id="e275a-136">EarthCore_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="e275a-136">EarthCore_BaseModuleIncomplete.</span></span> <span data-ttu-id="e275a-137">Scale: x = 50.0 y = 50.0、z = 50.0。</span><span class="sxs-lookup"><span data-stu-id="e275a-137">Scale: x = 50.0 y = 50.0, z = 50.0.</span></span>
    * <span data-ttu-id="e275a-138">Model_Platonic_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="e275a-138">Model_Platonic_BaseModuleIncomplete.</span></span> <span data-ttu-id="e275a-139">Scale: x = 0.13、y = 0.13、z = 0.13。</span><span class="sxs-lookup"><span data-stu-id="e275a-139">Scale: x = 0.13, y = 0.13, z = 0.13.</span></span>
    * <span data-ttu-id="e275a-140">Octa_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="e275a-140">Octa_BaseModuleIncomplete.</span></span> <span data-ttu-id="e275a-141">Scale: x = 0.13。</span><span class="sxs-lookup"><span data-stu-id="e275a-141">Scale: x = 0.13.</span></span> <span data-ttu-id="e275a-142">y = 0.13、z =0.13 に設定します。</span><span class="sxs-lookup"><span data-stu-id="e275a-142">y = 0.13, z =0.13.</span></span>
    * <span data-ttu-id="e275a-143">TheModule_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="e275a-143">TheModule_BaseModuleIncomplete.</span></span> <span data-ttu-id="e275a-144">Scale: x = 0.03、y = 0.03、z = 0.03。</span><span class="sxs-lookup"><span data-stu-id="e275a-144">Scale: x = 0.03, y = 0.03, z = 0.03.</span></span>

    ![mrlearning-base-ch4-1-step5](images/mrlearning-base-ch4-1-step5.png)

6. <span data-ttu-id="e275a-146">シーンに3つのキューブを追加します。</span><span class="sxs-lookup"><span data-stu-id="e275a-146">Add three cubes into your scene.</span></span> <span data-ttu-id="e275a-147">3DObjectCollection オブジェクトを右クリックし、[3D オブジェクト]、[キューブ] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-147">Right-click the 3DObjectCollection object, select 3D Object, then select Cube.</span></span> <span data-ttu-id="e275a-148">スケールを x = 0.14、y = 0.14、z = 0.14 に設定します。</span><span class="sxs-lookup"><span data-stu-id="e275a-148">Set the scale to x = 0.14, y = 0.14, and z = 0.14.</span></span> <span data-ttu-id="e275a-149">合計3つのキューブを作成するには、この手順をさらに2回繰り返します。</span><span class="sxs-lookup"><span data-stu-id="e275a-149">Repeat this step two additional times to create a total of three cubes.</span></span> <span data-ttu-id="e275a-150">または、キューブを合計3つのキューブに対して2回複製することもできます。</span><span class="sxs-lookup"><span data-stu-id="e275a-150">Alternatively, you can duplicate the cube twice for a total of three cubes.</span></span> <span data-ttu-id="e275a-151">また、[アセット] > [BaseModuleAssets] > [ベース モジュール プレハブ] から用意されている 3 つの立方体のプレハブを使用し、GreenCube_BaseModuleIncomplete、BlueCube_BaseModuleIncomplete、および OrangeCube_BaseModuleIncomplete を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="e275a-151">You may also choose to use the three prepared cube prefabs from Assets>BaseModuleAssets>Base Module Prefabs and select GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete and OrangeCube_BaseModuleIncomplete.</span></span>

    ![mrlearning-base-ch4-1-step6](images/mrlearning-base-ch4-1-step6.png)

7. <span data-ttu-id="e275a-153">「[レッスン 2](mrlearning-base-ch2.md)」で説明されている手順に従って、オブジェクトのコレクションを整理してグリッドを形成します。</span><span class="sxs-lookup"><span data-stu-id="e275a-153">Organize your collection of objects to form a grid, via the procedure described in [Lesson 2](mrlearning-base-ch2.md), using the MRTK’s Grid Object Collection.</span></span> <span data-ttu-id="e275a-154">3 x 3 グリッドでオブジェクトを構成する例については、次の図を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e275a-154">Refer to the image below, for an example of configuring the objects in a 3x3 grid.</span></span>

    ![mrlearning-base-ch4-1-step7](images/mrlearning-base-ch4-1-step7.png)

    >[!NOTE]
    ><span data-ttu-id="e275a-156">上の図のように、一部のオブジェクトはセンター外にあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="e275a-156">You might notice that some of the objects are off-center, such as the objects in the image above.</span></span> <span data-ttu-id="e275a-157">これは、プレハブまたはオブジェクトに整列していない子オブジェクトが含まれている可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="e275a-157">This is because prefabs or objects may have child objects that are not aligned.</span></span> <span data-ttu-id="e275a-158">オブジェクトの位置や子オブジェクトの位置に必要な調整を自由に加えることで、グリッドを適切に整列させることができます。</span><span class="sxs-lookup"><span data-stu-id="e275a-158">Feel free to make any necessary adjustments to object positions or child object positions to achieve a well-aligned grid.</span></span>

### <a name="manipulating-3d-objects"></a><span data-ttu-id="e275a-159">3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="e275a-159">Manipulating 3D Objects</span></span>

1. <span data-ttu-id="e275a-160">立方体を操作する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="e275a-160">Add the ability to manipulate a cube.</span></span> <span data-ttu-id="e275a-161">3D オブジェクトを操作する機能を追加するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e275a-161">To add the ability to manipulate 3D objects, do the following:</span></span>
    * <span data-ttu-id="e275a-162">階層内で操作する3D オブジェクト (つまり、キューブの1つ) を選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-162">Select the 3D object you want to manipulate in your hierarchy (i.e. one of your cubes).</span></span>
    * <span data-ttu-id="e275a-163">[コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e275a-163">Click Add Component</span></span>
    * <span data-ttu-id="e275a-164">"操作" の検索</span><span class="sxs-lookup"><span data-stu-id="e275a-164">Search for "manipulation"</span></span>
    * <span data-ttu-id="e275a-165">操作ハンドラーの選択</span><span class="sxs-lookup"><span data-stu-id="e275a-165">Select Manipulation Handler</span></span>
    * <span data-ttu-id="e275a-166">3DObjectCollection オブジェクトの下にあるすべての3D オブジェクトに対して繰り返しますが、3DObjectCollection 自体は同じではありません。</span><span class="sxs-lookup"><span data-stu-id="e275a-166">Repeat for all 3D objects under the 3DObjectCollection object, but not the 3DObjectCollection itself.</span></span>
    * <span data-ttu-id="e275a-167">すべての3D オブジェクトに collider または box collider があることを確認します (コンポーネント > Box Collider を追加します)。</span><span class="sxs-lookup"><span data-stu-id="e275a-167">Ensure that all 3D objects have a collider or box collider (Add Component>Box Collider).</span></span>

    ![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

    >[!NOTE]
    ><span data-ttu-id="e275a-169">操作ハンドラーは、操作時にオブジェクトがどのように動作するかの設定を調整できるコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="e275a-169">The manipulation handler is a component that lets you adjust settings for how objects behave when manipulated.</span></span> <span data-ttu-id="e275a-170">これには、特定の軸での回転、拡大縮小、移動、制約の移動が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e275a-170">This includes rotation, scaling, moving, and constraining movement on a specific axis.</span></span>

2. <span data-ttu-id="e275a-171">1 つの立方体を、拡大縮小しかできないように制限します。</span><span class="sxs-lookup"><span data-stu-id="e275a-171">Restrict one cube so that it can only be scaled.</span></span> <span data-ttu-id="e275a-172">3DObjectCollection オブジェクトで1つのキューブを選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-172">Select one cube in the 3DObjectCollection object.</span></span> <span data-ttu-id="e275a-173">[インスペクター] パネルで、[2 つのきき操作の種類] の横にあるドロップダウンメニューをクリックし、[スケール] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-173">In the Inspector panel, next to Two Handed Manipulation Type, click the drop-down menu and select Scale.</span></span> <span data-ttu-id="e275a-174">これにより、ユーザーは立方体のサイズしか変更できなくなります。</span><span class="sxs-lookup"><span data-stu-id="e275a-174">This makes it so that the user can only change the cube’s size.</span></span>

    ![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. <span data-ttu-id="e275a-176">立方体を区別できるように、それぞれの色を変更します。</span><span class="sxs-lookup"><span data-stu-id="e275a-176">Change the color of each cube so that we can differentiate between them.</span></span>
    * <span data-ttu-id="e275a-177">[プロジェクト] パネルに移動し、MixedRealityToolkit が表示されるまで下にスクロールして、それを選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-177">Go to the Project panel and scroll down until you see MixedRealityToolkit.SDK, then select it.</span></span>
    * <span data-ttu-id="e275a-178">[Standard Assets] フォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-178">Select the Standard Assets folder.</span></span>
    * <span data-ttu-id="e275a-179">[素材] フォルダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e275a-179">Click the Materials folder.</span></span>
    * <span data-ttu-id="e275a-180">立方体のそれぞれに異なる素材をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e275a-180">Drag a different material onto each of your cubes.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e275a-181">立方体には任意の色を選択できます。</span><span class="sxs-lookup"><span data-stu-id="e275a-181">You can choose any color for your cubes.</span></span> <span data-ttu-id="e275a-182">この例では、glowingcyan、glowingorange、および green が使用されています。</span><span class="sxs-lookup"><span data-stu-id="e275a-182">For this example, glowingcyan, glowingorange and green are used.</span></span> <span data-ttu-id="e275a-183">さまざまな色を自由に試すことができます。</span><span class="sxs-lookup"><span data-stu-id="e275a-183">Feel free to experiment with different colors.</span></span> <span data-ttu-id="e275a-184">キューブに色を追加するには、変更するキューブをクリックし、その素材をキューブの [インスペクター] パネルのメッシュレンダラーの [素材] フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e275a-184">To add the color to the cube, click the cube you want to change, then drag the material to the mesh renderer's material field in the cube's Inspector panel.</span></span>

    ![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. <span data-ttu-id="e275a-186">3DObjectCollection オブジェクト内の別のキューブを選択し、その移動を先頭からの固定距離に制限するように設定します。</span><span class="sxs-lookup"><span data-stu-id="e275a-186">Select another cube in the 3DObjectCollection object and make it so that its movement is constrained to a fixed distance from the head.</span></span> <span data-ttu-id="e275a-187">この操作を行うには、[移動] ラベルの [制約] の右側にあるドロップダウンメニューをクリックし、[ヘッドからの距離を修正] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-187">To do this, to the right of Constraint on Movement label, click the drop-down menu and select Fix Distance from the Head.</span></span> <span data-ttu-id="e275a-188">これにより、キューブがビジョンのフィールド内になるように調整されます。</span><span class="sxs-lookup"><span data-stu-id="e275a-188">This adjusts the cube to be within their field of vision.</span></span>

    ![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

    <span data-ttu-id="e275a-190">次のいくつかの手順の目的は、3D オブジェクトをグラブして操作し、異なる操作設定を適用できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="e275a-190">The goal of the following few steps is to enable grabbing and interacting with our 3D objects and applying different manipulation settings.</span></span>

5. <span data-ttu-id="e275a-191">[チーズ] オブジェクトを選択し、[インスペクター] パネルの [コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e275a-191">Select the Cheese object, then click Add Component from the Inspector panel.</span></span>

6. <span data-ttu-id="e275a-192">[検索] ボックスで [Near インタラクション Grabbable] を検索し、スクリプトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-192">Search in the search box for Near Interaction Grabbable and select the script.</span></span> <span data-ttu-id="e275a-193">このコンポーネントを使用すると、ユーザーは追跡したハンドを使用してオブジェクトに接続し、オブジェクトを取得できます。</span><span class="sxs-lookup"><span data-stu-id="e275a-193">This component enables users to reach out and grab objects with tracked hands.</span></span> <span data-ttu-id="e275a-194">次の画像の緑色の円で示されているように、[Far 操作を許可する] チェックボックスをオフにしない限り、オブジェクトを距離から操作することもできます。</span><span class="sxs-lookup"><span data-stu-id="e275a-194">Objects can also be manipulated from a distance, unless the Allow Far Manipulation checkbox is unchecked as denoted by a green circle in the image below.</span></span>

    ![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. <span data-ttu-id="e275a-196">これらのオブジェクトに対して手順 5. と 6. を繰り返して、プラトニックオブジェクト、地球コア、旧暦モジュール、およびコーヒーカップに Near Grabbable を追加します。</span><span class="sxs-lookup"><span data-stu-id="e275a-196">Add Near Interaction Grabbable to the Octa object, Platonic object, Earth Core, Lunar Module, and Coffee Cup by repeating Steps 5 and 6 on those objects.</span></span>

8. <span data-ttu-id="e275a-197">Octa オブジェクトから遠距離操作ができないようにします。</span><span class="sxs-lookup"><span data-stu-id="e275a-197">Remove the ability of far manipulation from the Octa object.</span></span> <span data-ttu-id="e275a-198">これを行うには、階層内で Octa を選択し、[far 操作を許可する] チェックボックスをオフにします (緑色の円でマークされています)。</span><span class="sxs-lookup"><span data-stu-id="e275a-198">To do this, select the Octa in the hierarchy and uncheck the Allow far Manipulation checkbox (marked by a green circle).</span></span> <span data-ttu-id="e275a-199">これにより、ユーザーは追跡したハンドを使用して、octa だけを直接操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e275a-199">This makes it so users can only interact with the octa directly using tracked hands.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e275a-200">操作ハンドラーコンポーネントとそれに関連する設定の完全なドキュメントについては、 [Mrtk のドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e275a-200">For the full documentation of the manipulation handler component and it's associated settings, refer to the [MRTK Documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).</span></span>

9. <span data-ttu-id="e275a-201">Near の相互作用 Grabbable コンポーネントが、地球コア、太陰暦モジュール、およびコーヒーカップに追加されていることを確認します (手順7を参照)。</span><span class="sxs-lookup"><span data-stu-id="e275a-201">Ensure that the Near Interaction Grabbable component has been added to the earth core, the lunar module and the coffee cup (see Step 7).</span></span>

10. <span data-ttu-id="e275a-202">旧暦モジュールの場合は、次の図に示すように、操作ハンドラーの設定を変更して、オブジェクトの中心を前後の対話の両方で回転させます。</span><span class="sxs-lookup"><span data-stu-id="e275a-202">For the lunar module, change the Manipulation Handler settings so that it rotates around the object's center for both near and far interaction, as shown in the image below.</span></span>

    ![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11. <span data-ttu-id="e275a-204">地球コアの場合は、リリース動作を何も変更しません。</span><span class="sxs-lookup"><span data-stu-id="e275a-204">For the earth core, change the release behavior to nothing.</span></span> <span data-ttu-id="e275a-205">これにより、地球コアがユーザーのつかみから解放されると、移動は続行されません。</span><span class="sxs-lookup"><span data-stu-id="e275a-205">This makes it so that once the earth core is released from the user's grasp, it doesn’t continue to move.</span></span>

    ![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

    >[!NOTE]
    ><span data-ttu-id="e275a-207">この設定は、スローできるボールを作成するなどのシナリオに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e275a-207">This setting is useful for scenarios, such as creating a ball that you can throw.</span></span> <span data-ttu-id="e275a-208">適切なベロシティと角速度を維持して、ボールがリリースされた後も、そのボールがリリースされた速度で移動し続けます。物理的なボールの動作と似ています。</span><span class="sxs-lookup"><span data-stu-id="e275a-208">Keeping the appropriate velocity and angular velocity to ensure that once the ball is released, it will continue to move at the velocity it was released at; similar to how a physical ball would behave.</span></span>

### <a name="adding-bounding-boxes"></a><span data-ttu-id="e275a-209">境界ボックスの追加</span><span class="sxs-lookup"><span data-stu-id="e275a-209">Adding Bounding Boxes</span></span>

<span data-ttu-id="e275a-210">境界ボックスを使用すると、直接操作 (ほぼ相互作用) と射線ベースの操作 (遠くのやり取り) の両方で、オブジェクトを1つの手で操作することが簡単になり、直観的になります。境界ボックスは、特定の軸に沿ってオブジェクトを拡大縮小および回転するために取得できるハンドルを提供します。</span><span class="sxs-lookup"><span data-stu-id="e275a-210">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both direct manipulation (near interaction) and ray-based manipulation (far interaction.) Bounding boxes provide handles that can be grabbed for scaling and rotating objects along a specific axis.</span></span>

>[!NOTE]
><span data-ttu-id="e275a-211">オブジェクトに境界ボックスを追加するには、まず、このレッスンで前に説明したように、オブジェクト (box collider など) に collider を用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e275a-211">Before you can add a bounding box to an object, you first need to have a collider on the object (e.g., a box collider), as was covered previously in this lesson.</span></span> <span data-ttu-id="e275a-212">Colliders を追加するには、オブジェクトを選択し、オブジェクトの [インスペクター] パネルで [コンポーネントの追加 > Box Collider] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-212">Colliders can be added by selecting the object and in the object's inspector panel selecting Add Component>Box Collider.</span></span>

1. <span data-ttu-id="e275a-213">箱の collider を地球コアオブジェクトに追加します (まだ存在しない場合)。</span><span class="sxs-lookup"><span data-stu-id="e275a-213">Add a box collider to the Earth Core object if one does not already exist.</span></span> <span data-ttu-id="e275a-214">指定された指示に従って、ベースモジュールの Assets フォルダーに用意されている prefab を使用する場合、box の collider とセットアップは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="e275a-214">The box collider and setup are not required, if using the prefab provided in the Base Module Assets folder per the instructions given.</span></span> <span data-ttu-id="e275a-215">地球コアの場合、次の図に示すように、box collider を、、node_id30、地球コアの下にあるオブジェクトに追加しました。</span><span class="sxs-lookup"><span data-stu-id="e275a-215">In the case of the earth core, we added the box collider to the, node_id30, object underneath the earth core, as shown in the image below.</span></span> <span data-ttu-id="e275a-216">オブジェクトの [インスペクター] タブで [node_id30] を選択し、[コンポーネントの追加] をクリックして、box collider を検索します。</span><span class="sxs-lookup"><span data-stu-id="e275a-216">Select node_id30 from the object's Inspector tab, click Add Component, and search for box collider.</span></span>

    ![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

    ![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

    >[!NOTE]
    ><span data-ttu-id="e275a-219">Box collider のサイズを大きくしたり小さくしたりしないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="e275a-219">Make sure that you size the box collider so that it’s not too big or too small.</span></span> <span data-ttu-id="e275a-220">それが囲むオブジェクト (この例では地球の核) とほぼ同じサイズである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e275a-220">It should be roughly the same size as the object it’s surrounding (in this example, the earth core).</span></span> <span data-ttu-id="e275a-221">Box collider の [Collider の編集] オプションを選択して、必要に応じて box の collider を調整します。</span><span class="sxs-lookup"><span data-stu-id="e275a-221">Adjust the box collider as needed by selecting the Edit Collider option in the box collider.</span></span> <span data-ttu-id="e275a-222">X、y、z の値を変更するか、[エディターシーン] ウィンドウで境界ボックスハンドラーをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e275a-222">You can either changing the x, y, and z values or drag the bounding box handlers in the Editor Scene window.</span></span>

    ![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. <span data-ttu-id="e275a-224">アースコアの node_id30 オブジェクトに境界ボックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="e275a-224">Add a bounding box to the earth core's node_id30 object.</span></span> <span data-ttu-id="e275a-225">これを行うには、3DObjectCollection から node_id30 オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-225">To do this, select the node_id30 object from the 3DObjectCollection.</span></span> <span data-ttu-id="e275a-226">[インスペクター] タブで、[コンポーネントの追加] をクリックし、[境界ボックス] を検索します。</span><span class="sxs-lookup"><span data-stu-id="e275a-226">In the inspector tab, click Add Component, and search for bounding box.</span></span> <span data-ttu-id="e275a-227">境界ボックス、ボックス コライダー、および操作スクリプト (操作ハンドラー、近距離操作 - グラブ可能) がすべて同じゲーム オブジェクト上にあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e275a-227">Ensure that the bounding box, box collider, and manipulation scripts (manipulation handler, near interaction grabbable) are all on the same game object.</span></span>

3. <span data-ttu-id="e275a-228">境界ボックスの [動作] セクションで、[アクティブ化] ドロップダウンリストから [開始時にアクティブにする] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-228">In the bounding box's Behavior section, select Activate on Start from the Activation drop-down list.</span></span> <span data-ttu-id="e275a-229">さまざまなアクティブ化オプションおよびその他の境界ボックスオプションに関する詳細については、 [Mrtk の境界ボックスのドキュメント](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e275a-229">To review additional details regarding the various activation options and other bounding box options, see the [MRTK's bounding box documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)</span></span>

    <span data-ttu-id="e275a-230">*次のいくつかの手順では、既定のボックスマテリアル、グラブ中の素材、コーナーハンドルとサイドハンドルの視覚化を調整して、境界ボックスがどのように見えるかを変更します。MRTK には、境界ボックスをカスタマイズするためのオプションがいくつか含まれています。*</span><span class="sxs-lookup"><span data-stu-id="e275a-230">*In the next few steps, we will also change how the bounding box looks by adjusting the default box material, the material while it’s being grabbed as well as the visualization of the corner and side handles. The MRTK contains several options to customize the bounding box.*</span></span>

4. <span data-ttu-id="e275a-231">[プロジェクト] パネルで "boundingbox" を検索すると、次の図に示すように、検索結果に青い球で示される素材の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e275a-231">In the Project panel, search for "boundingbox" and you’ll see a list of materials denoted by a blue sphere in the search results as shown in the image below.</span></span>

5. <span data-ttu-id="e275a-232">Boundingbox マテリアルを、境界ボックスコンポーネントのボックス素材スロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e275a-232">Drag the boundingbox material into the box material slot on the bounding box component.</span></span> <span data-ttu-id="e275a-233">また、boundingboxgrabbed の素材を取得し、境界ボックスコンポーネントのボックスに挿入します。</span><span class="sxs-lookup"><span data-stu-id="e275a-233">Also grab the boundingboxgrabbed material and put that in the box grabbed material slot on the bounding box component.</span></span>

    ![mrlearning-base-ch4-3-step5](images/mrlearning-base-ch4-3-step5.png)

6. <span data-ttu-id="e275a-235">MRTK_BoundingBox_ScaleHandle prefab をスケールハンドル prefab スロットにドラッグし、MRTK_BoundingBox_RotateHandle prefab を結合ボックスコンポーネントの回転ハンドルスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e275a-235">Drag the MRTK_BoundingBox_ScaleHandle prefab into the scale handle prefab slot and the MRTK_BoundingBox_RotateHandle prefab into the rotation handle slot on the bonding box component.</span></span>

    ![mrlearning-base-ch4-3-step6](images/mrlearning-base-ch4-3-step6.png)

7. <span data-ttu-id="e275a-237">境界ボックスの正しいオブジェクトを対象としていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e275a-237">Make sure the bounding box is targeting the right object.</span></span> <span data-ttu-id="e275a-238">境界ボックスコンポーネントには、ターゲットオブジェクトと境界オーバーライドスクリプトがあります。</span><span class="sxs-lookup"><span data-stu-id="e275a-238">In the bounding box component, there is the target object and bounds override scripts.</span></span> <span data-ttu-id="e275a-239">境界ボックスを持つオブジェクトをこれらのスロットの両方にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e275a-239">Drag the object that has the bounding box around it to both of these slots.</span></span> <span data-ttu-id="e275a-240">この例では、次の図に示すように、これらのスロットの両方に node_id30 オブジェクトをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e275a-240">In this example, drag the node_id30 object to both of these slots, as shown in the image below.</span></span>

    ![mrlearning-base-ch4-3-step7](images/mrlearning-base-ch4-3-step7.png)

    >[!NOTE]
    ><span data-ttu-id="e275a-242">アプリケーションを起動または再生すると、オブジェクトは青いフレームで囲まれます。</span><span class="sxs-lookup"><span data-stu-id="e275a-242">When you start or play the application, your object will be surrounded by a blue frame.</span></span> <span data-ttu-id="e275a-243">そのフレームのコーナーをドラッグすると、オブジェクトのサイズを自由に変更できます。</span><span class="sxs-lookup"><span data-stu-id="e275a-243">You’re welcome to drag the corners of that frame to resize the object.</span></span> <span data-ttu-id="e275a-244">スケーリングハンドルと回転ハンドルのサイズを大きくして表示する場合は、既定の境界ボックスの設定を使用することをお勧めします (手順 4. ~ 6. を回避)。</span><span class="sxs-lookup"><span data-stu-id="e275a-244">If you want the scaling handles and the rotation handles to be larger and more visible, it is recommend using the default bounding box settings (avoiding Steps 4 -through 6.)</span></span>

8. <span data-ttu-id="e275a-245">既定の境界ボックスの視覚化に戻るには、境界ボックスのオブジェクトの [インスペクター] パネルで、回転ハンドル prefab を選択し、del キーを押して削除します。</span><span class="sxs-lookup"><span data-stu-id="e275a-245">To return to the default bounding box visualization, in the Inspector panel of the bounding box's object, select the rotation handle prefab and press delete to remove it.</span></span> <span data-ttu-id="e275a-246">再生モードに入ると、次の図のような境界ボックスの視覚エフェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e275a-246">When you enter play mode, wou will see a bounding box visualization similar to the image below.</span></span>

    ![mrlearning-base-ch4-3-step8](images/mrlearning-base-ch4-3-step8.png)

    >[!NOTE]
    ><span data-ttu-id="e275a-248">境界ボックスの視覚エフェクトは、再生モードの場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="e275a-248">The bounding box visualizations only appear when in play mode.</span></span>

### <a name="adding-touch-effects"></a><span data-ttu-id="e275a-249">タッチ効果の追加</span><span class="sxs-lookup"><span data-stu-id="e275a-249">Adding touch effects</span></span>

<span data-ttu-id="e275a-250">この例では、オブジェクトを手でタッチしたときに効果音が再生されるようにします。</span><span class="sxs-lookup"><span data-stu-id="e275a-250">In this example, we are going to play a sound effect when you touch an object with your hand.</span></span>

1. <span data-ttu-id="e275a-251">ゲーム オブジェクトにオーディオ ソース コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="e275a-251">Add an audio source component to your game object.</span></span> <span data-ttu-id="e275a-252">シーン階層で Octa オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-252">Select the Octa object in your scene hierarchy.</span></span> <span data-ttu-id="e275a-253">[インスペクター] パネルで [コンポーネントの追加] ボタンをクリックし、[オーディオソース] を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-253">In the inspector panel, click the Add Component button, search for and select audio source.</span></span> <span data-ttu-id="e275a-254">後の方の手順で、このオーディオ ソースを使用して効果音を再生します。</span><span class="sxs-lookup"><span data-stu-id="e275a-254">We’ll use this audio source to play a sound effect in a later step.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e275a-255">Octa オブジェクトに box collider があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e275a-255">Ensure that the Octa object has a box collider on it.</span></span>

2. <span data-ttu-id="e275a-256">Near 対話 Touchable コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="e275a-256">Add the Near Interaction Touchable component.</span></span> <span data-ttu-id="e275a-257">[インスペクター] パネルの [Add Component (コンポーネントの追加)] ボタンをクリックし、near インタラクション touchable を検索します。</span><span class="sxs-lookup"><span data-stu-id="e275a-257">Click the Add Component button in the Inspector panel and search for near interaction touchable.</span></span> <span data-ttu-id="e275a-258">選択してコンポーネントに追加します。</span><span class="sxs-lookup"><span data-stu-id="e275a-258">Select it to add the component.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e275a-259">以前は、grabbable の近くに追加しました。</span><span class="sxs-lookup"><span data-stu-id="e275a-259">Previously, we added near interaction grabbable.</span></span> <span data-ttu-id="e275a-260">この相互作用 touchable の違いは、grabbable の相互作用は、オブジェクトをグラブして操作することを意図しています。</span><span class="sxs-lookup"><span data-stu-id="e275a-260">The difference between this and near interaction touchable is that the grabbable interaction is intended for an object to be grabbed and interacted with.</span></span> <span data-ttu-id="e275a-261">Touchable コンポーネントは、タッチするオブジェクトを対象としています。</span><span class="sxs-lookup"><span data-stu-id="e275a-261">The touchable component is intended for the object to be touched.</span></span> <span data-ttu-id="e275a-262">操作を組み合わせるために両方のコンポーネントを一緒に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="e275a-262">Both components can be used together for a combination of interactions.</span></span>

    ![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. <span data-ttu-id="e275a-264">ハンドインタラクションタッチスクリプトにを追加します。</span><span class="sxs-lookup"><span data-stu-id="e275a-264">Add in the Hand Interaction Touch script.</span></span> <span data-ttu-id="e275a-265">前の手順と同じように、[コンポーネントの追加] をクリックして、追加するタッチ操作を検索します。</span><span class="sxs-lookup"><span data-stu-id="e275a-265">Just like the previous step, click Add Component and search for hand interaction touch to add it.</span></span>

    <span data-ttu-id="e275a-266">スクリプトには次の3つのオプションがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e275a-266">Notice that you have three options with the script:</span></span>
    * <span data-ttu-id="e275a-267">タッチ完了時: オブジェクトをタッチして解放するとトリガーされます</span><span class="sxs-lookup"><span data-stu-id="e275a-267">On Touch Completed: Triggers when you touch and release the object</span></span>
    * <span data-ttu-id="e275a-268">タッチ開始時: オブジェクトがタッチされたときにトリガーします</span><span class="sxs-lookup"><span data-stu-id="e275a-268">On Touch Started: Triggers when the object is touched</span></span>
    * <span data-ttu-id="e275a-269">タッチ更新時: ハンドがオブジェクトに接している間、定期的にトリガーします。</span><span class="sxs-lookup"><span data-stu-id="e275a-269">On Touch Updated: Triggers periodically while your hand is touching the object</span></span>

    <span data-ttu-id="e275a-270">この例では、[タッチによる開始] 設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="e275a-270">For this example, we will be working with the On Touch Started setting.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e275a-271">このスクリプトは、このチュートリアルの冒頭でインポートした BaseModuleAssets Unity パッケージに含まれており、元の MRTK には含まれていません。</span><span class="sxs-lookup"><span data-stu-id="e275a-271">This script is included with the BaseModuleAssets Unity package that you imported as at the beginning of this tutorial and it is not included in the original MRTK.</span></span>

4. <span data-ttu-id="e275a-272">[タッチ開始時] オプションの [+] ボタンをクリックし、[Octa] オブジェクトを空のフィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e275a-272">Click the + button on the On Touch Started option and drag the Octa object into the empty field.</span></span>

    ![mrlearning-base-ch4-4-step4](images/mrlearning-base-ch4-4-step4.png)

5. <span data-ttu-id="e275a-274">[関数がありません] というドロップダウンで、[AudioSource > PlayOneShot] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e275a-274">In the drop-down that says No Function, select AudioSource > PlayOneShot.</span></span> <span data-ttu-id="e275a-275">以下のコンセプトを元に、このフィールドにオーディオ クリップを追加します。</span><span class="sxs-lookup"><span data-stu-id="e275a-275">We will add an audio clip to this field using the concepts below:</span></span>

    * <span data-ttu-id="e275a-276">MRTK には、オーディオ クリップの小さいリストがあります。</span><span class="sxs-lookup"><span data-stu-id="e275a-276">The MRTK does provide a small list of audio clips.</span></span> <span data-ttu-id="e275a-277">これらは、プロジェクトパネルで自由に調べることができます。</span><span class="sxs-lookup"><span data-stu-id="e275a-277">Feel free to explore these in your Project panel.</span></span> <span data-ttu-id="e275a-278">これらのファイルは、[アセット > MixedRealityToolkit > Standard Assets > Audio フォルダー] の下にあります。</span><span class="sxs-lookup"><span data-stu-id="e275a-278">You will find them under the Assets > MixedRealityToolkit.SDK > Standard Assets > Audio folder.</span></span>
    * <span data-ttu-id="e275a-279">この例では、MRTK_Gem オーディオクリップを使用します。</span><span class="sxs-lookup"><span data-stu-id="e275a-279">For this example, we are going to use the MRTK_Gem audio clip.</span></span>
    * <span data-ttu-id="e275a-280">オーディオクリップを追加するには、目的のクリップを [プロジェクト] パネルから [PlayOneShot] フィールドにドラッグするだけです。</span><span class="sxs-lookup"><span data-stu-id="e275a-280">To add an audio clip, simply drag the clip you want from the project panel into the AudioSource.PlayOneShot field.</span></span>

    ![mrlearning-base-ch4-4-step5](images/mrlearning-base-ch4-4-step5.png)

   <span data-ttu-id="e275a-282">これで、ユーザーがに到達し、Octa オブジェクトに触れると、オーディオトラック MRTK_Gem が再生されます。</span><span class="sxs-lookup"><span data-stu-id="e275a-282">Now, when the user reaches out and touches the Octa object, the audio track MRTK_Gem will play.</span></span> <span data-ttu-id="e275a-283">また、ハンドインタラクションタッチスクリプトでは、オブジェクトの色も調整されます。</span><span class="sxs-lookup"><span data-stu-id="e275a-283">The Hand Interaction Touch script will also adjust the color of the object, when touched.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e275a-284">結論</span><span class="sxs-lookup"><span data-stu-id="e275a-284">Congratulations</span></span>

<span data-ttu-id="e275a-285">このチュートリアルでは、グリッドコレクション内の3D オブジェクトを整理する方法と、近くの操作 (追跡したハンドを使用した直接グラブ) と遠くの相互作用 (宝石を使用した、または光線を使用) を使用して、これらのオブジェクトを操作する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="e275a-285">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="e275a-286">また、3D オブジェクトの周囲に境界ボックスを配置する方法と、境界ボックスでギズモを使用およびカスタマイズする方法についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="e275a-286">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the gizmos on the bounding boxes.</span></span> <span data-ttu-id="e275a-287">最後に、オブジェクトにタッチしたときにイベントをトリガーする方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="e275a-287">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="e275a-288">次のレッスン: 6. 詳細な入力オプションの調査</span><span class="sxs-lookup"><span data-stu-id="e275a-288">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
