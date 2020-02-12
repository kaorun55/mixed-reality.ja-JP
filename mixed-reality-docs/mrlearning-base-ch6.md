---
title: 入門チュートリアル-7. 旧暦モジュールサンプルアプリケーションの作成
description: このレッスンでは、前のレッスンで学習した複数の概念を組み合わせて、独自のサンプルエクスペリエンスを作成します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: b5b1bd0115822449bd6098f78cfc94d909169737
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129452"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="5b9c1-105">7. 旧暦モジュールサンプルアプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="5b9c1-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="5b9c1-106">このチュートリアルでは、前のレッスンとの複数の概念を組み合わせて、独自のサンプルエクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="5b9c1-107">パートアセンブリアプリケーションを作成する方法を学習します。このアプリケーションでは、ユーザーが追跡したハンドを使用して部品を取り出し、旧暦モジュールを組み立てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="5b9c1-108">Pressable ボタンを使用して、配置ヒントのオンとオフを切り替えたり、エクスペリエンスをリセットしたり、旧暦モジュールをスペースで起動したりします。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="5b9c1-109">今後のチュートリアルでは、このエクスペリエンスの構築を継続します。これには、空間の配置に Azure 空間アンカーを利用する強力なマルチユーザーのユースケースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="5b9c1-110">目標</span><span class="sxs-lookup"><span data-stu-id="5b9c1-110">Objectives</span></span>

* <span data-ttu-id="5b9c1-111">前のレッスンの複数の概念を組み合わせて固有のエクスペリエンスを作成する</span><span class="sxs-lookup"><span data-stu-id="5b9c1-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="5b9c1-112">オブジェクトを切り替える方法を学習する</span><span class="sxs-lookup"><span data-stu-id="5b9c1-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="5b9c1-113">押しボタンを使用して複雑なイベントをトリガーする</span><span class="sxs-lookup"><span data-stu-id="5b9c1-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="5b9c1-114">剛体の物理学と力を使用する</span><span class="sxs-lookup"><span data-stu-id="5b9c1-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="5b9c1-115">ヒントの使用を調査する</span><span class="sxs-lookup"><span data-stu-id="5b9c1-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="5b9c1-116">旧暦モジュールパーツの概要</span><span class="sxs-lookup"><span data-stu-id="5b9c1-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="5b9c1-117">このセクションでは、簡単なパートアセンブリチャレンジを作成します。ユーザーの目標は、テーブルに展開される5つの部分を太陰暦モジュールの正しい位置に配置することです。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="5b9c1-118">これを実現するには、主に次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="5b9c1-119">ロケットランチャー prefab をシーンに追加する</span><span class="sxs-lookup"><span data-stu-id="5b9c1-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="5b9c1-120">すべての部分に対してオブジェクトの操作を有効にする</span><span class="sxs-lookup"><span data-stu-id="5b9c1-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="5b9c1-121">パーツアセンブリのデモ (スクリプト) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="5b9c1-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="5b9c1-122">パートアセンブリデモ (スクリプト) コンポーネントは、MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="5b9c1-123">このチュートリアルでは、このチュートリアルのアセットを提供しました。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="5b9c1-124">1. ロケットランチャー prefab をシーンに追加する</span><span class="sxs-lookup"><span data-stu-id="5b9c1-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="5b9c1-125">プロジェクト ウィンドウで、**アセット** >  **mrtk に移動します。チュートリアル: GettingStarted** **Prefabs** > **RocketLauncher**フォルダーに移動し、 **RocketLauncher** prefab を 階層 ウィンドウにドラッグしてシーンに追加した後、適切な場所に配置します。次に例を示します。 > </span><span class="sxs-lookup"><span data-stu-id="5b9c1-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="5b9c1-126">変換位置 X = 1.5、Y =-0.4、Z = 0 の場合、ユーザーの右側にウェスト height で配置されます。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="5b9c1-127">変換の回転 X = 0、Y = 180、Z = 0、エクスペリエンスの主な機能はユーザーにとって</span><span class="sxs-lookup"><span data-stu-id="5b9c1-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="5b9c1-129">2. すべての部分に対してオブジェクトの操作を有効にします。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="5b9c1-130">[階層] ウィンドウで、RocketLauncher > **Lunarmoduleparts**オブジェクトを見つけてすべての**子オブジェクト**を選択し、**操作ハンドラー (スクリプト)** コンポーネントと**Near Grabbable (スクリプト**) コンポーネントを追加して、操作ハンドラー (スクリプト) を次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="5b9c1-131">**2 つのきき操作の種類**を移動回転に変更して、スケーリングが無効になるようにします。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-131">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>
* <span data-ttu-id="5b9c1-132">[**遠隔操作を許可**する] チェックボックスをオフにして、ほぼ対話のみを許可します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-132">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="5b9c1-134">オブジェクトの操作を実装する方法に関する詳細な手順については、「 [3D オブジェクトの操作](mrlearning-base-ch4.md#manipulating-3d-objects)」の指示を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="5b9c1-135">3. パーツアセンブリのデモ (スクリプト) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="5b9c1-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="5b9c1-136">すべての LunarModuleParts 子オブジェクトを選択したまま、**オーディオソース**コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="5b9c1-137">適切なオーディオクリップを**audioclip**フィールドに割り当てます (たとえば、MRKT_Scale_Start</span><span class="sxs-lookup"><span data-stu-id="5b9c1-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="5b9c1-138">シーンの読み込み時にオーディオクリップが自動的に再生されないように、 **[スリープ状態で再生]** チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="5b9c1-139">空間**Blend**を1に変更して、空間オーディオを有効にする</span><span class="sxs-lookup"><span data-stu-id="5b9c1-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="5b9c1-141">すべての LunarModuleParts 子オブジェクトがまだ選択されている状態で、 **Part Assembly Demo (スクリプト)** コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="5b9c1-143">[階層] ウィンドウで、 **Roverenclosure クロージャ**オブジェクトを選択し、その**パートアセンブリデモ (スクリプト)** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="5b9c1-144">フィールドを**配置するオブジェクト**に対して、オブジェクト自体 (この場合は**roverenclosure クロージャ**オブジェクト) を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-144">To the **Object To Place** field, assign the object itself, in this case, the **RoverEnclosure** object</span></span>
* <span data-ttu-id="5b9c1-145">**[場所]** フィールドに、対応する PlacementHints オブジェクト (この例では**RoverEnclosure_PlacementHints**オブジェクト) を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-145">To the **Location To Place** field, assign the corresponding PlacementHints object, in this case, the **RoverEnclosure_PlacementHints** object</span></span>
* <span data-ttu-id="5b9c1-146">**ツールヒントオブジェクト**フィールドに、対応する ToolTipObject (この例では**RoverEnclosure_ToolTip**オブジェクト) を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-146">To the **Tool Tip Object** field, assign the corresponding ToolTipObject, in this case, the **RoverEnclosure_ToolTip** object</span></span>
* <span data-ttu-id="5b9c1-147">**[オーディオソース]** フィールドに、オブジェクト自体 (この場合は**roverenclosure クロージャ**オブジェクト) を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-147">To the **Audio Source** field, assign the object itself, in this case, the **RoverEnclosure** object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="5b9c1-149">他のすべての LunarModuleParts 子オブジェクト (つまり、Futex、EnergyCell、DockingPortal、ExternalSensor) に対して**繰り返し**ます。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="5b9c1-150">ここでゲームモードに入り、' オブジェクト ' を移動して、それに対応する ' Location ' の位置に近い場所に配置すると、次のことがわかります。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="5b9c1-151">オブジェクトが配置され、LunarModule オブジェクトの親になります。これにより、オブジェクトが旧暦モジュールの一部になります。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="5b9c1-152">オブジェクトのオーディオソースは、オブジェクトの位置で割り当てられたオーディオクリップを再生します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="5b9c1-153">対応するツールヒントオブジェクトは非表示になります</span><span class="sxs-lookup"><span data-stu-id="5b9c1-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="5b9c1-155">エディター内入力シミュレーションの使用方法に関する注意事項については、「エディターでの入力シミュレーションを使用して、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)でシーンガイドを[テストする](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="5b9c1-156">月着陸船の構成</span><span class="sxs-lookup"><span data-stu-id="5b9c1-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="5b9c1-157">このセクションでは、ユーザーが次のことができるように、ロケットランチャーアプリケーションに機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="5b9c1-158">旧暦モジュールとの対話</span><span class="sxs-lookup"><span data-stu-id="5b9c1-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="5b9c1-159">旧暦モジュールをスペースで起動し、起動時にサウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="5b9c1-160">旧暦モジュールとすべての部分が元の位置に戻されるようにアプリケーションをリセットします。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-160">Reset the application so the Lunar Module and all the part are placed back to their original position</span></span>
* <span data-ttu-id="5b9c1-161">パーツアセンブリのチャレンジをより困難にするために配置ヒントを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="5b9c1-162">これを実現するには、主に次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="5b9c1-163">オブジェクトの操作を有効にする</span><span class="sxs-lookup"><span data-stu-id="5b9c1-163">Enable object manipulation</span></span>
2. <span data-ttu-id="5b9c1-164">物理を有効にする</span><span class="sxs-lookup"><span data-stu-id="5b9c1-164">Enable physics</span></span>
3. <span data-ttu-id="5b9c1-165">オーディオソースコンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="5b9c1-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="5b9c1-166">Launch 旧暦モジュール (スクリプト) コンポーネントの追加と構成</span><span class="sxs-lookup"><span data-stu-id="5b9c1-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="5b9c1-167">配置ヒントの切り替え (スクリプト) コンポーネントの追加と構成</span><span class="sxs-lookup"><span data-stu-id="5b9c1-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="5b9c1-168">[旧暦モジュール (スクリプト)] コンポーネントと [配置ヒントの切り替え (スクリプト)] コンポーネントは、MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="5b9c1-169">これらは、このチュートリアルの資産で提供されています。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="5b9c1-170">1. オブジェクトの操作を有効にする</span><span class="sxs-lookup"><span data-stu-id="5b9c1-170">1. Enable object manipulation</span></span>

<span data-ttu-id="5b9c1-171">[階層] ウィンドウで、RocketLauncher > **Lunarmodule**オブジェクトを選択し、**操作ハンドラー (スクリプト)** コンポーネントと**Near Grabbable (スクリプト)** コンポーネントを追加して、操作ハンドラー (スクリプト) を次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="5b9c1-172">**2 つのきき操作の種類**を移動回転に変更して、スケーリングが無効になるようにします。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-172">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>
* <span data-ttu-id="5b9c1-173">[**遠隔操作を許可**する] チェックボックスをオフにして、ほぼ対話のみを許可します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-173">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="5b9c1-175">2. 物理を有効にする</span><span class="sxs-lookup"><span data-stu-id="5b9c1-175">2. Enable physics</span></span>

<span data-ttu-id="5b9c1-176">RocketLauncher > **Lunarmodule**オブジェクトを選択したまま、Rigidbody コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-176">With the RocketLauncher > **LunarModule** object still selected, add a Rigidbody component and then configure it as follows:</span></span>

* <span data-ttu-id="5b9c1-177">**[重力を使用する]** チェックボックスをオフにして、太陰暦モジュールが重力の影響を受けないようにします。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="5b9c1-178">**[Is キネマティック]** チェックボックスをオンにします。これにより、旧暦モジュールは、physic の強制による影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="5b9c1-180">3. オーディオソースコンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="5b9c1-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="5b9c1-181">RocketLauncher > **Lunarmodule**オブジェクトを選択したまま、**オーディオソース**コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="5b9c1-182">空間**Blend**を1に変更して空間オーディオを有効にする</span><span class="sxs-lookup"><span data-stu-id="5b9c1-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="5b9c1-184">4. Launch Module (スクリプト) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="5b9c1-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="5b9c1-185">RocketLauncher > **Lunarmodule**オブジェクトを選択した状態で、 **Launch 旧暦モジュール (スクリプト)** コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="5b9c1-186">**推力**の値を変更して、旧暦を起動したときに (たとえば、0.01 に)、旧暦のモジュールが適切に表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="5b9c1-188">5. 配置ヒントの切り替え (スクリプト) コンポーネントを追加および構成する</span><span class="sxs-lookup"><span data-stu-id="5b9c1-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="5b9c1-189">RocketLauncher > **Lunarmodule**オブジェクトを選択したまま、 **[配置ヒント (スクリプト) の切り替え]** コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="5b9c1-190">Game オブジェクトの配列**サイズ**プロパティを5に設定します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="5b9c1-191">**PlacementHints**オブジェクトの各**子オブジェクト**を、Game オブジェクト配列の**要素**フィールドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-191">Assign each of the **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="5b9c1-193">[起動] ボタンの構成</span><span class="sxs-lookup"><span data-stu-id="5b9c1-193">Configuring the Launch button</span></span>

<span data-ttu-id="5b9c1-194">[階層] ウィンドウで、[> RocketLauncher] ボタン > **launchbutton**オブジェクトを選択し、[ **Pressable] ボタン (スクリプト)** コンポーネントで新しい**ボタン押された ()** イベントを作成して、イベントを受信するための**lunarmodule**オブジェクトを構成し、トリガーするアクションとして**launchlunarStartThruster**を定義します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="5b9c1-196">イベントの実装方法に関する注意事項については、「[ハンドトラッキングジェスチャ」と「対話型 buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="5b9c1-197">RocketLauncher > ボタン > **launchbutton**オブジェクトが選択された状態で、[ **Pressable] ボタン (スクリプト)** コンポーネントで、新しい**Button 押された ()** イベントを作成し、イベントを受信するように**lunarmodule**オブジェクトを構成し、トリガーするアクションとして**audiosource. PlayOneShot**を定義し **、オーディオクリップフィールドに**適切 MRTK_Gem なオーディオクリップを割り当てます</span><span class="sxs-lookup"><span data-stu-id="5b9c1-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="5b9c1-199">RocketLauncher > ボタン > **launchbutton**オブジェクトが選択された状態で、[ **Pressable] ボタン (スクリプト)** コンポーネントで新しい**タッチ終了 ()** イベントを作成し、イベントを受信するように**lunarmodule**オブジェクトを構成して、トリガーされるアクションとして**launchlunarmodule. StopThruster**を定義します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch Ended ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="5b9c1-201">これでゲームモードに入り、[起動] ボタンを押すと、オーディオクリップが再生されます。また、[起動] ボタンを1秒以上押したままにすると、旧暦モジュールがスペースで起動していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="5b9c1-203">[リセット] ボタンの構成</span><span class="sxs-lookup"><span data-stu-id="5b9c1-203">Configuring the Reset button</span></span>

<span data-ttu-id="5b9c1-204">[階層] ウィンドウで、[RocketLauncher >] ボタン > **Resetbutton**オブジェクトを選択し、[ **Pressable] ボタン (スクリプト)** コンポーネントで新しい**Button 押された ()** イベントを作成します。次に、イベントを受信するための**lunarmodule**オブジェクトを構成し、トリガーするアクションとして**launchlunarmodule. resetbutton**を定義します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="5b9c1-206">RocketLauncher > のボタン > **resetbutton**オブジェクトを選択したまま、[ **Pressable] ボタン (スクリプト)** コンポーネントで、新しい**Button 押された ()** イベントを作成し、イベントを受信するように**RocketLauncher**オブジェクトを構成し、トリガーするアクションとして**BroadcastMessage**を定義し、メッセージフィールドに**resetbutton**を入力します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="5b9c1-208">BroadcastMessage アクションは、ResetPlacement メッセージを RocketLauncher オブジェクトからすべての子オブジェクトに送信します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="5b9c1-209">すべての LunarModuleParts 子オブジェクトに追加したパーツアセンブリデモ (スクリプト) コンポーネントで定義されている ResetPlacement 関数を持つ子オブジェクトは、その子オブジェクトの配置をリセットする ResetPlacement 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="5b9c1-210">これでゲームモードに入り、[リセット] ボタンを押すと、再生中のオーディオクリップが表示され、スペースで開かれている旧暦が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-210">If you now enter Game mode and press the Reset button you will hear the audio clip being played and see the Lunar Module being launched into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="5b9c1-212">配置ヒントボタンの構成</span><span class="sxs-lookup"><span data-stu-id="5b9c1-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="5b9c1-213">[階層] ウィンドウで、[RocketLauncher > ボタン > **Hintsbutton]** オブジェクトを選択し、[ **Pressable] ボタン (スクリプト)** コンポーネントで新しい**ボタン押された ()** イベントを作成します。次に、イベントを受信するための**lunarmodule**オブジェクトを構成し、トリガーされるアクションを**TogglePlacementHints**に定義します。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="5b9c1-215">これでゲームモードに入ると、半透明の配置ヒントが既定で無効になっていることがわかりますが、ヒントボタンを押すことによって、オンとオフを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="5b9c1-217">結論</span><span class="sxs-lookup"><span data-stu-id="5b9c1-217">Congratulations</span></span>

<span data-ttu-id="5b9c1-218">このアプリケーションは完全に構成されています。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-218">You have fully configured this application.</span></span> <span data-ttu-id="5b9c1-219">これで、アプリケーションでは、ユーザーが旧暦モジュールを完全に組み立て、旧暦モジュールを起動し、ヒントを切り替えることができるようになりました。また、アプリケーションをリセットして再起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="5b9c1-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
