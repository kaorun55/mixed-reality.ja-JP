---
title: 入門チュートリアル - 7. 月着陸船サンプル アプリケーションの作成
description: このレッスンでは、前のレッスンで学習した複数の概念を組み合わせて固有のサンプル エクスペリエンスを作成します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031550"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="69ff5-105">7.月着陸船サンプル アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="69ff5-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="69ff5-106">このチュートリアルでは、前のレッスンの複数の概念を組み合わせて固有のサンプル エクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="69ff5-107">ユーザーが追跡対象の手を使用して部品を選択し、月着陸船の組み立てを試みる必要がある部品アセンブリ アプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="69ff5-108">押しボタンを使用して、配置のヒントのオン/オフを切り替えたり、エクスペリエンスをリセットしたり、月着陸船を宇宙に発射したりします。</span><span class="sxs-lookup"><span data-stu-id="69ff5-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="69ff5-109">今後のチュートリアルでは、空間的な位置合わせのために Azure Spatial Anchors を利用する強力なマルチユーザー ユースケースを含め、このエクスペリエンスを基に構築していきます。</span><span class="sxs-lookup"><span data-stu-id="69ff5-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="69ff5-110">目標</span><span class="sxs-lookup"><span data-stu-id="69ff5-110">Objectives</span></span>

* <span data-ttu-id="69ff5-111">前のレッスンの複数の概念を組み合わせて固有のエクスペリエンスを作成する</span><span class="sxs-lookup"><span data-stu-id="69ff5-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="69ff5-112">オブジェクトを切り替える方法を学習する</span><span class="sxs-lookup"><span data-stu-id="69ff5-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="69ff5-113">押しボタンを使用して複雑なイベントをトリガーする</span><span class="sxs-lookup"><span data-stu-id="69ff5-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="69ff5-114">剛体の物理学と力を使用する</span><span class="sxs-lookup"><span data-stu-id="69ff5-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="69ff5-115">ヒントの使用を調査する</span><span class="sxs-lookup"><span data-stu-id="69ff5-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="69ff5-116">月着陸船部品の概要</span><span class="sxs-lookup"><span data-stu-id="69ff5-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="69ff5-117">このセクションでは、テーブル上に配置されている 5 つの部品を月着陸船の正しい位置に配置することをユーザーの目標とする、簡単な部品アセンブリの課題を作成します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="69ff5-118">これを実現するための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="69ff5-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="69ff5-119">ロケット発射台プレハブをシーンに追加する</span><span class="sxs-lookup"><span data-stu-id="69ff5-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="69ff5-120">すべての部品のオブジェクト操作を有効にする</span><span class="sxs-lookup"><span data-stu-id="69ff5-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="69ff5-121">Part Assembly Demo (Script) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="69ff5-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="69ff5-122">Part Assembly Demo (Script) コンポーネントは、MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="69ff5-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="69ff5-123">このチュートリアルのアセットと共に提供されました。</span><span class="sxs-lookup"><span data-stu-id="69ff5-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="69ff5-124">1.ロケット発射台プレハブをシーンに追加する</span><span class="sxs-lookup"><span data-stu-id="69ff5-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="69ff5-125">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)**  >  **[RocketLauncher]** フォルダーに移動し、 **[RocketLauncher]** プレハブを [Hierarchy]\(階層\) ウィンドウにドラッグしてシーンに追加し、適切な場所に配置します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="69ff5-126">[Transform]\(変換\) の [Position]\(位置\) X = 1.5、Y = -0.4、Z = 0。これにより、ユーザーの右側に腰の高さで配置されます</span><span class="sxs-lookup"><span data-stu-id="69ff5-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="69ff5-127">[Transform]\(変換\) の [Rotation]\(回転\) X = 0、Y = 180、Z = 0。これにより、エクスペリエンスの主な機能がユーザーに向けられます</span><span class="sxs-lookup"><span data-stu-id="69ff5-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="69ff5-129">2.すべての部品のオブジェクト操作を有効にする</span><span class="sxs-lookup"><span data-stu-id="69ff5-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="69ff5-130">[Hierarchy]\(階層\) ウィンドウで、[RocketLauncher] > **[LunarModuleParts]** オブジェクトを見つけて、すべての**子オブジェクト**を選択します。次に、**Manipulation Handler (Script)** コンポーネントおよび **Near Interaction Grabbable (Script)** コンポーネントを追加し、Manipulation Handler (Script) を次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="69ff5-131">**[Allow Far Manipulation]\(遠距離操作を許可\)** チェックボックスをオフにして、近距離操作のみを許可するようにします</span><span class="sxs-lookup"><span data-stu-id="69ff5-131">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="69ff5-132">**[Two Handed Manipulation Type]\(両手を使った操作の種類\)** を **[Move Rotate]\(移動回転\)** に変更して、拡大縮小を無効にします</span><span class="sxs-lookup"><span data-stu-id="69ff5-132">Change **Two Handed Manipulation Type** to **Move Rotate** so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="69ff5-134">オブジェクトの操作を実装する方法の詳細な手順については、「[3D オブジェクトの操作](mrlearning-base-ch4.md#manipulating-3d-objects)」の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69ff5-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="69ff5-135">3.Part Assembly Demo (Script) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="69ff5-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="69ff5-136">[LunarModuleParts] 子オブジェクトをすべて選択したまま、**Audio Source** コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="69ff5-137">適切なオーディオ クリップ (たとえば MRKT_Scale_Start) を **[AudioClip]** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="69ff5-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="69ff5-138">**[Play On Awake]\(起動時に再生\)** チェックボックスをオフにして、シーンの読み込み時にオーディオ クリップが自動的に再生されないようにします</span><span class="sxs-lookup"><span data-stu-id="69ff5-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="69ff5-139">**[Spatial Blend]\(空間ブレンド\)** を 1 に変更して、空間オーディオを有効にします</span><span class="sxs-lookup"><span data-stu-id="69ff5-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="69ff5-141">[LunarModuleParts] 子オブジェクトがすべて選択された状態で、**Part Assembly Demo  (Script)** コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="69ff5-143">[Hierarchy]\(階層\) ウィンドウで **[RoverEnclosure]** オブジェクトを選択し、**Part Assembly Demo (Script)** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="69ff5-144">**[Object To Place]\(配置するオブジェクト\)** フィールドに、オブジェクト**自体** (この場合は RoverEnclosure オブジェクト) を割り当てます</span><span class="sxs-lookup"><span data-stu-id="69ff5-144">To the **Object To Place** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>
* <span data-ttu-id="69ff5-145">**[Location To Place]\(配置する場所\)** フィールドに、対応する **[PlacementHints]** オブジェクト (この場合は RoverEnclosure_PlacementHint オブジェクト) を割り当てます</span><span class="sxs-lookup"><span data-stu-id="69ff5-145">To the **Location To Place** field, assign the corresponding **PlacementHints** object, in this case, the RoverEnclosure_PlacementHint object</span></span>
* <span data-ttu-id="69ff5-146">**[Tool Tip Object]\(ヒント オブジェクト\)** フィールドに、対応する **[ToolTip]** (この場合は RoverEnclosure_ToolTip オブジェクト) を割り当てます</span><span class="sxs-lookup"><span data-stu-id="69ff5-146">To the **Tool Tip Object** field, assign the corresponding **ToolTip**, in this case, the RoverEnclosure_ToolTip object</span></span>
* <span data-ttu-id="69ff5-147">**[Audio Source]\(オーディオ ソース\)** フィールドに、オブジェクト**自体** (この場合は RoverEnclosure オブジェクト) を割り当てます</span><span class="sxs-lookup"><span data-stu-id="69ff5-147">To the **Audio Source** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="69ff5-149">他のすべての LunarModuleParts 子オブジェクト (つまり、FuelTank、EnergyCell、DockingPortal、ExternalSensor) についても同じ手順を**繰り返します**。</span><span class="sxs-lookup"><span data-stu-id="69ff5-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="69ff5-150">ここでゲーム モードに入り、[Object To Place]\(配置するオブジェクト\) をそれに対応する [Location To Place]\(配置する場所\) の近くに配置すると、次のことが起こります。</span><span class="sxs-lookup"><span data-stu-id="69ff5-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="69ff5-151">オブジェクトが所定の位置にはめ込まれ、LunarModule オブジェクトの下にペアレント化されて月着陸船の一部になります</span><span class="sxs-lookup"><span data-stu-id="69ff5-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="69ff5-152">オブジェクトのオーディオ ソースは、オブジェクトの位置で割り当てられたオーディオ クリップを再生します</span><span class="sxs-lookup"><span data-stu-id="69ff5-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="69ff5-153">対応する Tool Tip オブジェクトは非表示になります</span><span class="sxs-lookup"><span data-stu-id="69ff5-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="69ff5-155">エディター内入力シミュレーションを使用する方法については、[MRTK ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) の[エディター内の手の入力シミュレーションを使用したシーンのテスト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)に関するガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="69ff5-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="69ff5-156">月着陸船の構成</span><span class="sxs-lookup"><span data-stu-id="69ff5-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="69ff5-157">このセクションでは、ロケット発射台アプリケーションに機能を追加して、ユーザーが次のことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="69ff5-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="69ff5-158">月着陸船を操作する</span><span class="sxs-lookup"><span data-stu-id="69ff5-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="69ff5-159">月着陸船を宇宙に打ち上げ、打ち上げ時にサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="69ff5-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="69ff5-160">アプリケーションをリセットして、月着陸船とすべての部品を元の位置に戻す</span><span class="sxs-lookup"><span data-stu-id="69ff5-160">Reset the application so the Lunar Module and all the parts are placed back to their original position</span></span>
* <span data-ttu-id="69ff5-161">配置ヒントを非表示にして、部品アセンブリの課題をより難しくする。</span><span class="sxs-lookup"><span data-stu-id="69ff5-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="69ff5-162">これを実現するための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="69ff5-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="69ff5-163">オブジェクトの操作を有効にする</span><span class="sxs-lookup"><span data-stu-id="69ff5-163">Enable object manipulation</span></span>
2. <span data-ttu-id="69ff5-164">物理的処理を有効にする</span><span class="sxs-lookup"><span data-stu-id="69ff5-164">Enable physics</span></span>
3. <span data-ttu-id="69ff5-165">Audio Source コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="69ff5-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="69ff5-166">Launch Lunar Module (Script) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="69ff5-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="69ff5-167">Toggle Placement Hints (Script) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="69ff5-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="69ff5-168">Launch Lunar Module (Script) コンポーネントと Toggle Placement Hints (Script) コンポーネントは MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="69ff5-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="69ff5-169">これらはこのチュートリアルのアセットと共に提供されました。</span><span class="sxs-lookup"><span data-stu-id="69ff5-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="69ff5-170">1.オブジェクトの操作を有効にする</span><span class="sxs-lookup"><span data-stu-id="69ff5-170">1. Enable object manipulation</span></span>

<span data-ttu-id="69ff5-171">[Hierarchy]\(階層\) ウィンドウで、[RocketLauncher] > **[LunarModule]** オブジェクトを選択します。次に、**Manipulation Handler (Script)** コンポーネントおよび **Near Interaction Grabbable (Script)** コンポーネントを追加し、Manipulation Handler (Script) を次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="69ff5-172">**[Allow Far Manipulation]\(遠距離操作を許可\)** チェックボックスをオフにして、近距離操作のみを許可するようにします</span><span class="sxs-lookup"><span data-stu-id="69ff5-172">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="69ff5-173">**[Two Handed Manipulation Type]\(両手を使った操作の種類\)** を [Move Rotate]\(移動回転\) に変更して、拡大縮小を無効にします</span><span class="sxs-lookup"><span data-stu-id="69ff5-173">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="69ff5-175">2.物理的処理を有効にする</span><span class="sxs-lookup"><span data-stu-id="69ff5-175">2. Enable physics</span></span>

<span data-ttu-id="69ff5-176">[RocketLauncher] > **[LunarModule]** オブジェクトを選択したまま、**Rigidbody** コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-176">With the RocketLauncher > **LunarModule** object still selected, add a **Rigidbody** component and then configure it as follows:</span></span>

* <span data-ttu-id="69ff5-177">**[Use Gravity]\(重力を使用\)** チェックボックスをオフにして、月着陸船が重力の影響を受けないようにします</span><span class="sxs-lookup"><span data-stu-id="69ff5-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="69ff5-178">**[Is Kinematic]\(キネマティック\)** チェックボックスをオンにして、月着陸船が最初は物理的な力の影響を受けないようにします</span><span class="sxs-lookup"><span data-stu-id="69ff5-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="69ff5-180">3.Audio Source コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="69ff5-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="69ff5-181">[RocketLauncher] > **[LunarModule]** オブジェクトを選択したまま、**Audio Source** コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="69ff5-182">**[Spatial Blend]\(空間ブレンド\)** を 1 に変更して、空間オーディオを有効にします</span><span class="sxs-lookup"><span data-stu-id="69ff5-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="69ff5-184">4.Launch Lunar Module (Script) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="69ff5-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="69ff5-185">[RocketLauncher] > **[LunarModule]** オブジェクトを選択したまま、**Launch Lunar Module (Script)** コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="69ff5-186">**[Thrust]\(推力\)** の値を変更して、月着陸船が打ち上げ時に滑らかに上昇するようにします (たとえば、0.01)。</span><span class="sxs-lookup"><span data-stu-id="69ff5-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="69ff5-188">5.Toggle Placement Hints (Script) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="69ff5-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="69ff5-189">[RocketLauncher] > **[LunarModule]** オブジェクトを選択したまま、**Toggle Placement Hints (Script)** コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="69ff5-190">ゲーム オブジェクト配列の **[Size]\(サイズ\)** プロパティを 5 に設定します</span><span class="sxs-lookup"><span data-stu-id="69ff5-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="69ff5-191">次のように、[RocketLauncher] > [LunarModule] > **[PlacementHints]** オブジェクトの**子オブジェクト**をゲーム オブジェクト配列の **[Element]\(要素\)** フィールドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="69ff5-191">Assign each of the RocketLauncher > LunarModule > **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="69ff5-193">発射ボタンの構成</span><span class="sxs-lookup"><span data-stu-id="69ff5-193">Configuring the Launch button</span></span>

<span data-ttu-id="69ff5-194">[Hierarchy]\(階層\) ウィンドウで、[RocketLauncher] > [Buttons] > **[LaunchButton]** オブジェクトを選択し、**Pressable Button (Script)** コンポーネントで、新しい **Button Pressed ()** イベントを作成し、イベントを受信するように **[LunarModule]** オブジェクトを構成して、トリガーするアクションとして **LaunchLunarModule.StartThruster** を定義します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="69ff5-196">イベントを実装する方法については、「[手の追跡のジェスチャと操作可能なボタン](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)」の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69ff5-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="69ff5-197">[RocketLauncher] > [Buttons] > **[LaunchButton]** オブジェクトを選択したまま、**Pressable Button (Script)** コンポーネントで、新しい **Button Pressed ()** イベントを作成し、イベントを受信するように **[LunarModule]** オブジェクトを構成し、トリガーするアクションとして **AudioSource.PlayOneShot** を定義し、適切なオーディオ クリップ (MRTK_Gem オーディオ クリップなど) を **[Audio Clip]\(オーディオ クリップ\)** フィールドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="69ff5-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="69ff5-199">[RocketLauncher] > [Buttons] > **[LaunchButton]** オブジェクトを選択したまま、**Pressable Button (Script)** コンポーネントで、新しい **Touch End ()** イベントを作成し、イベントを受信するように **[LunarModule]** オブジェクトを構成して、トリガーするアクションとして **LaunchLunarModule.StopThruster** を定義します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch End ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="69ff5-201">ここでゲーム モードに入り、[Launch]\(発射\) ボタンを押すと、オーディオ クリップが再生されます。また、[Launch]\(発射\) ボタンを 1 秒以上押し続けると、月着陸船が宇宙に打ち上げられます。</span><span class="sxs-lookup"><span data-stu-id="69ff5-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="69ff5-203">リセット ボタンの構成</span><span class="sxs-lookup"><span data-stu-id="69ff5-203">Configuring the Reset button</span></span>

<span data-ttu-id="69ff5-204">[Hierarchy]\(階層\) ウィンドウで、[RocketLauncher] > [Buttons] > **[ResetButton]** オブジェクトを選択し、**Pressable Button (Script)** コンポーネントで、新しい **Button Pressed ()** イベントを作成し、イベントを受信するように **[LunarModule]** オブジェクトを構成して、トリガーするアクションとして **LaunchLunarModule.ResetModule** を定義します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="69ff5-206">[RocketLauncher] > [Buttons] > **[ResetButton]** オブジェクトを選択したまま、**Pressable Button (Script)** コンポーネントで、新しい **Button Pressed ()** イベントを作成し、イベントを受信するように **[RocketLauncher]** オブジェクトを構成して、トリガーするアクションとして **GameObject.BroadcastMessage** を定義し、メッセージ フィールドに **ResetPlacement** と入力します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="69ff5-208">GameObject.BroadcastMessage アクションは、RocketLauncher オブジェクトからそのすべての子オブジェクトに ResetPlacement メッセージを 送信します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="69ff5-209">すべての LunarModuleParts 子オブジェクトに追加した Part Assembly Demo (Script) コンポーネントで定義されている ResetPlacement 関数を持つすべての子オブジェクトは、その子オブジェクトの配置をリセットする ResetPlacement 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="69ff5-210">ここでゲーム モードに入り、部品を移動するか月着陸船を発射してから [Reset]\(リセット\) ボタンを押すと、部品または月着陸船は元の位置にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="69ff5-210">If you now enter Game mode, move some parts and/or launch the Lunar Module, and then press the Reset button you will see the parts and/or the Lunar Module being reset to their original position:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="69ff5-212">配置のヒント ボタンの構成</span><span class="sxs-lookup"><span data-stu-id="69ff5-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="69ff5-213">[Hierarchy]\(階層\) ウィンドウで、[RocketLauncher] > [Buttons] > **[HintsButton]** オブジェクトを選択し、**Pressable Button (Script)** コンポーネントで、新しい **Button Pressed ()** イベントを作成し、イベントを受信するように **[LunarModule]** オブジェクトを構成して、トリガーするアクションとして **TogglePlacementHints.ToggleGameObjects** を定義します。</span><span class="sxs-lookup"><span data-stu-id="69ff5-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="69ff5-215">ここでゲーム モードに入ると、半透明の配置ヒントは既定で無効になっていますが、[Hints]\(ヒント\) ボタンを押すことによって、オンとオフを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="69ff5-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="69ff5-217">結論</span><span class="sxs-lookup"><span data-stu-id="69ff5-217">Congratulations</span></span>

<span data-ttu-id="69ff5-218">このアプリケーションが完全に構成されました。</span><span class="sxs-lookup"><span data-stu-id="69ff5-218">You have fully configured this application.</span></span> <span data-ttu-id="69ff5-219">これでユーザーは、このアプリケーションを使用して月着陸船を完全に組み立て、月着陸船を発射し、ヒントを切り替え、アプリケーションをリセットして再び開始することができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="69ff5-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
