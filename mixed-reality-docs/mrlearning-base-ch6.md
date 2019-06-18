---
title: MR 学習ベース モジュール - 月着陸船アセンブリのサンプル エクスペリエンス
description: このレッスンでは、前のレッスンから学習した複数の概念を組み合わせて固有のサンプル エクスペリエンスを作成します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730845"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a><span data-ttu-id="5a2bc-104">MR 学習ベース モジュール - 月着陸船アセンブリのサンプル エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="5a2bc-104">MR Learning Base Module - Lunar Module Assembly Sample Experience</span></span>

<span data-ttu-id="5a2bc-105">このレッスンでは、前のレッスンから学習した複数の概念を組み合わせて固有のサンプル エクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-105">In this lesson, we will combine multiple concepts learned from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="5a2bc-106">ユーザーが追跡対象の手を使用して月着陸船の部品を持ち上げ、月着陸船の組み立てを試みる必要がある月着陸船アセンブリ アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-106">We will create a lunar module assembly application whereby a user will need to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="5a2bc-107">押しボタンを使用して、配置のヒントを切り替えたり、エクスペリエンスをリセットしたり、月着陸船を宇宙に発射したりします。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-107">We will use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="5a2bc-108">将来のチュートリアルでは、空間的整合のために Azure Spatial Anchors を利用する強力なマルチユーザー ユースケースを含め、引き続きこのエクスペリエンスの上に構築します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-108">In future tutorials, we will continue to build upon this experience, including powerful multi-user use-cases that leverages Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="5a2bc-109">目標</span><span class="sxs-lookup"><span data-stu-id="5a2bc-109">Objectives</span></span>

- <span data-ttu-id="5a2bc-110">前のレッスンの複数の概念を組み合わせて固有のエクスペリエンスを作成する</span><span class="sxs-lookup"><span data-stu-id="5a2bc-110">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="5a2bc-111">オブジェクトを切り替える方法を学習する</span><span class="sxs-lookup"><span data-stu-id="5a2bc-111">Learn how to toggle objects</span></span>
- <span data-ttu-id="5a2bc-112">押しボタンを使用して複雑なイベントをトリガーする</span><span class="sxs-lookup"><span data-stu-id="5a2bc-112">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="5a2bc-113">剛体の物理学と力を使用する</span><span class="sxs-lookup"><span data-stu-id="5a2bc-113">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="5a2bc-114">ヒントの使用を調査する</span><span class="sxs-lookup"><span data-stu-id="5a2bc-114">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="5a2bc-115">手順</span><span class="sxs-lookup"><span data-stu-id="5a2bc-115">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="5a2bc-116">月着陸船の構成</span><span class="sxs-lookup"><span data-stu-id="5a2bc-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="5a2bc-117">この章では、サンプル エクスペリエンスを作成するために必要なさまざまなコンポーネントを導入します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-117">In this chapter, we will be introduced to the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="5a2bc-118">月着陸船アセンブリ プレハブを [Base Scene] に追加します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-118">Add the lunar module assembly prefab to your Base Scene.</span></span> <span data-ttu-id="5a2bc-119">これを行うには、プロジェクト タブで [Rocket Launcher_Tutorial] を検索します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-119">To do this, in your project tab, search for "Rocket Launcher_Tutorial."</span></span> <span data-ttu-id="5a2bc-120">このプレハブは、[アセット]>[BaseModuleAssets]>[プレハブ] で見つけることもできます。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-120">You may also find the prefab in Assets>BaseModuleAssets>Prefabs.</span></span> <span data-ttu-id="5a2bc-121">2 つのロケット発射台プレハブが表示されます。1 つは [チュートリアル] という名前であり、もう 1 つは [完成] という名前です。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-121">You may see two rocket launcher prefabs; one with the name "tutorial" and another with the name "complete."</span></span> <span data-ttu-id="5a2bc-122">[Rocket Launcher_Tutorial] プレハブを [Base Scene] にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-122">Drag the "Rocket Launcher_Tutorial" prefab to your Base Scene.</span></span> <span data-ttu-id="5a2bc-123">プレハブの位置をシーン内に自由に配置してください。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-123">Feel free to position the placement of the prefab in your scene.</span></span>
   <span data-ttu-id="5a2bc-124">注:[Rocket Launcher_Complete] プレハブは、参考のために提供されている完成した発射台です。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-124">Note: The "Rocket Launcher_Complete" prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="5a2bc-126">階層内で [Rocket Launcher_Tutorial] ゲーム オブジェクトを展開し、さらに [月着陸船] オブジェクトを展開すると、[X 線] という名前の素材を持ついくつかの子オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-126">If you expand the "Rocket Launcher_Tutorial" game object in your hierarchy, and further expand the "Lunar Module" object, you will see several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="5a2bc-127">[X 線] 素材では、ユーザーへの配置のヒントとして使用する、わずかに半透明な色が可能になります。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-127">The "x-ray" material allows for a slightly translucent color which we will use as placement hints for the user.</span></span> 

<span data-ttu-id="5a2bc-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) 次の図に示すように、月着陸船には、ユーザーが操作する 5 つの部品があります。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user is going to interact with, as shown in the image below:</span></span>

1.  <span data-ttu-id="5a2bc-129">探査車格納庫</span><span class="sxs-lookup"><span data-stu-id="5a2bc-129">The Rover Enclosure</span></span>
2.  <span data-ttu-id="5a2bc-130">燃料タンク</span><span class="sxs-lookup"><span data-stu-id="5a2bc-130">The Fuel Tank</span></span>
3.  <span data-ttu-id="5a2bc-131">エネルギー セル</span><span class="sxs-lookup"><span data-stu-id="5a2bc-131">The Energy Cell</span></span>
4.  <span data-ttu-id="5a2bc-132">ドッキング ポータル</span><span class="sxs-lookup"><span data-stu-id="5a2bc-132">The Docking Portal</span></span> 
5.  <span data-ttu-id="5a2bc-133">外部センサー</span><span class="sxs-lookup"><span data-stu-id="5a2bc-133">The External sensor</span></span>

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="5a2bc-135">注:[Base Scene] 階層に表示されるゲーム オブジェクト名は、シーン内のオブジェクトの名前に対応していません。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-135">Note: The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="5a2bc-136">手順 2:月着陸船にオーディオ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-136">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="5a2bc-137">[Base Scene] 階層で月着陸船が選択されていることを確認し、[コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-137">Make sure the lunar module is selected in your base scene hierarchy and click "Add Component."</span></span> <span data-ttu-id="5a2bc-138">[オーディオ ソース] を検索し、それをオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-138">Search for "Audio Source" and add it to the object.</span></span> <span data-ttu-id="5a2bc-139">今は空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-139">Leave it blank for now.</span></span> <span data-ttu-id="5a2bc-140">これは、後で発射音を再生するために使用します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-140">We will use this to play the launching sound later.</span></span>
 <span data-ttu-id="5a2bc-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) 手順 3:[配置のヒントを切り替える] スクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) Step 3: Add the script "toggle placement hints."</span></span> <span data-ttu-id="5a2bc-142">[コンポーネントの追加] をクリックし、[配置のヒントを切り替える] を検索します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-142">Click "Add Component" and search for "Toggle Placement Hints."</span></span> <span data-ttu-id="5a2bc-143">これは、先に説明した半透明なヒント (X 線素材を持つオブジェクト) のオンとオフを切り替えることができるカスタム スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-143">This is a custom script that allows you to turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span> 
<span data-ttu-id="5a2bc-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) 手順 4:5 つのオブジェクトがあるため、ゲーム オブジェクト配列のサイズに「5」と入力します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) Step 4: Since we have 5 objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="5a2bc-145">それにより、5 つの新しい要素が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-145">Then you should see 5 new elements appear.</span></span> 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="5a2bc-147">半透明な各オブジェクトを [なし (ゲーム オブジェクト)] が表示されたボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-147">Drag each of the translucent objects into the boxes that say "None (Game Object)."</span></span> <span data-ttu-id="5a2bc-148">[Base Scene] の月着陸船の次のオブジェクトをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-148">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="5a2bc-149">•   Backpack</span><span class="sxs-lookup"><span data-stu-id="5a2bc-149">•   Backpack</span></span>

<span data-ttu-id="5a2bc-150">•   GasTank</span><span class="sxs-lookup"><span data-stu-id="5a2bc-150">•   GasTank</span></span>

<span data-ttu-id="5a2bc-151">•   Topleftbody</span><span class="sxs-lookup"><span data-stu-id="5a2bc-151">•   Topleftbody</span></span>

<span data-ttu-id="5a2bc-152">•   Nose</span><span class="sxs-lookup"><span data-stu-id="5a2bc-152">•   Nose</span></span>

<span data-ttu-id="5a2bc-153">•   LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="5a2bc-153">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="5a2bc-155">これで、[配置のヒントを切り替える] スクリプトが構成されました。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-155">Now the "toggle placement hints" script is configured.</span></span> <span data-ttu-id="5a2bc-156">これにより、ヒントのオンとオフを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-156">This will allow us to turn the hints on and off.</span></span>

<span data-ttu-id="5a2bc-157">手順 5:[月着陸船を発射する] スクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-157">Step 5: Add the "launch lunar module" script.</span></span> <span data-ttu-id="5a2bc-158">[コンポーネントの追加] ボタンをクリックし、[月着陸船を発射する] を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-158">Click the "Add Component" button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="5a2bc-159">このスクリプトには、月着陸船を発射する役割があります。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-159">This script will be responsible for launching the lunar module.</span></span> <span data-ttu-id="5a2bc-160">構成されたボタンを押すと、月着陸船の剛体コンポーネントに上向きの力が加えられ、この月着陸船が上に向けて発射されます。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-160">When we press a configured button, it will add an upward force to the lunar module's rigid body component and will cause the module to launch upwards.</span></span> <span data-ttu-id="5a2bc-161">屋内にいる場合は、月着陸船が天井メッシュに当たってクラッシュする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-161">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="5a2bc-162">ただし、屋外にいる場合は、宇宙をいつまでも飛行します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-162">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="5a2bc-164">手順 6:月着陸船が正常に上に向かって飛行するように [推進力] を調整します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-164">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="5a2bc-165">0\.01 の値を試してください。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-165">Try a value of 0.01.</span></span> <span data-ttu-id="5a2bc-166">[Rb] フィールドは空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-166">Leave the "Rb" field blank.</span></span> <span data-ttu-id="5a2bc-167">Rb は剛体を表し、このフィールドは実行時に自動的にデータが入力されます。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-167">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="5a2bc-169">[月着陸船] 部品の概要</span><span class="sxs-lookup"><span data-stu-id="5a2bc-169">Lunar Module Parts Overview</span></span>
<span data-ttu-id="5a2bc-170">[月着陸船] 部品の親オブジェクトは、ユーザーが操作するオブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-170">The Lunar Module parts parent object is the collection of the objects that the user will interact with.</span></span> <span data-ttu-id="5a2bc-171">ゲーム オブジェクト名 (かっこ内はシーンのラベルが付いた名前) を次の一覧に示します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-171">The game object names (with scene labeled names in paretheses) are provided in the list below:</span></span>

- <span data-ttu-id="5a2bc-172">Backpack (燃料タンク)</span><span class="sxs-lookup"><span data-stu-id="5a2bc-172">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="5a2bc-173">GasTank (エネルギー セル)</span><span class="sxs-lookup"><span data-stu-id="5a2bc-173">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="5a2bc-174">TopLeftBody (探査車格納庫)</span><span class="sxs-lookup"><span data-stu-id="5a2bc-174">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="5a2bc-175">Nose (ドッキング ポータル)</span><span class="sxs-lookup"><span data-stu-id="5a2bc-175">Nose (Docking Portal)</span></span>
- <span data-ttu-id="5a2bc-176">LeftTwirler (外部センサー)</span><span class="sxs-lookup"><span data-stu-id="5a2bc-176">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="5a2bc-177">レッスン 4 で説明されているように、これらの各オブジェクトには操作ハンドラーかあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-177">Notice that each of these objects has the manipulation handler, as discussed in lesson 4.</span></span> <span data-ttu-id="5a2bc-178">操作ハンドラーを使用すると、ユーザーはオブジェクトをつかんで操作できます。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-178">With the manipulation handler, users are able to grab and manipulate the object.</span></span> <span data-ttu-id="5a2bc-179">また、[両手を使った操作の種類] 設定が [移動と回転] に設定されていることにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-179">Also note that the setting "two handed manipulation type" is set to "move and rotate."</span></span> <span data-ttu-id="5a2bc-180">これにより、ユーザーはオブジェクトを移動することしかできず、サイズは変更できません。これは、アセンブリ アプリケーションには望ましい機能です。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-180">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="5a2bc-181">さらに、月着陸船の部品の直接操作のみを許可するために、遠隔操作はオフになっています。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-181">In addition, far manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="5a2bc-183">部品アセンブリ デモ スクリプト (上に示されています) は、ユーザーによって月着陸船に配置されるオブジェクトを管理するスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-183">The part assembly demo script (shown above) is the scrip that manages the objects to be placed on to the lunar module by the user.</span></span> 

<span data-ttu-id="5a2bc-184">[配置するオブジェクト] フィールドは、接続できるオブジェクトと共に選択された変換 (前の図の場合は、Backpack/燃料タンク) です。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-184">The "Object To Place" field is the transform that is selected (n the case of the image above, the backpack/fuel tank) with the object that it can connect to.</span></span> 

<span data-ttu-id="5a2bc-185">[近距離] および [遠距離] 設定には、部品をはめ込んだり、取り外したりするときの近さを決定する役割があります。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-185">The "Near Distance" and "Far Distance" settings are responsible for determining the proximity to which parts will snap in place or be released.</span></span> <span data-ttu-id="5a2bc-186">たとえば、Backpack/燃料タンクは、はめ込むには月着陸船から 0.1 ユニット離れている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-186">For example, the backpack/fuel tank would need to be 0.1 units away from the lunar module to snap into place.</span></span> <span data-ttu-id="5a2bc-187">[遠距離] は、オブジェクトを月着陸船から取り外す必要がある場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-187">The "Far Distance" sets the location where the object needs to be to detach from the lunar module.</span></span> <span data-ttu-id="5a2bc-188">この場合、ユーザーの手は Backpack/燃料タンクをつかみ、再度はめ込まれないように取り外すには月着陸船から 0.2 ユニット離れた場所に引く必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-188">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="5a2bc-189">[ヒント オブジェクト] は、シーン内のヒント ラベルです。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-189">The "Tool Tip Object" is the tool tip label in the scene.</span></span> <span data-ttu-id="5a2bc-190">オブジェクトがはめ込まれると、ラベルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-190">When the objects are snapped in place, the label will be disabled.</span></span> 

<span data-ttu-id="5a2bc-191">オーディオ ソースは自動的に取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-191">The Audio Source will be automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="5a2bc-192">[配置のヒント] ボタン</span><span class="sxs-lookup"><span data-stu-id="5a2bc-192">Placement Hints Buttons</span></span>
<span data-ttu-id="5a2bc-193">[レッスン 2](mrlearning-base-ch2.md) では、項目の色を変更したり、押されたら音を再生したりするなどの操作を実行するためのボタンを配置および構成する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-193">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="5a2bc-194">ここでは配置のヒントを切り替えるためのボタンを構成するため、これらの原則を引き続き使用します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-194">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="5a2bc-195">目標は、ユーザーが [配置のヒント] ボタンを押すたびに、半透明な配置のヒントの可視性を切り替えるようにボタンを構成することです。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-195">The goal is to configure our button so that every time the user presses the placement hint button, it will toggle visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="5a2bc-196">手順 1:[Base Scene] 階層で [配置のヒント] オブジェクトが選択されているときに、[月着陸船] を [インスペクター] パネルの空の [ランタイムのみ] スロットに移動します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-196">Step 1: Move the Lunar Module to the empty "runtime only" slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="5a2bc-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 手順 2:ここで、[関数なし] が表示されたドロップダウン リストをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the dropdown list where it says, "no function."</span></span> <span data-ttu-id="5a2bc-198">下の方の [TogglePlacementHints] に移動し、そのメニューの下の [ToggleGameObjects ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-198">Go down to "TogglePlacementHints," and under that menu select "ToggleGameObjects ()."</span></span> <span data-ttu-id="5a2bc-199">ToggleGameObjects() は、配置のヒントのオンとオフを切り替えて、ボタンが押されるたびに表示または非表示になるようにします。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-199">ToggleGameObjects() will toggle the placement hints on and off so that they are visible or invisible every time the button is pressed.</span></span>
 <span data-ttu-id="5a2bc-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="5a2bc-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="5a2bc-201">リセット ボタンの構成</span><span class="sxs-lookup"><span data-stu-id="5a2bc-201">Configuring the Reset Button</span></span>

<span data-ttu-id="5a2bc-202">ユーザーが間違いを犯したり、オブジェクトを誤って捨てたり、単にエクスペリエンスを停止させたくなったりする状況が発生します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-202">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to rest the experience.</span></span> <span data-ttu-id="5a2bc-203">リセット ボタンにより、エクスペリエンスを再開する機能が追加されます。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-203">The reset button will add the ability to restart the experience.</span></span> 

<span data-ttu-id="5a2bc-204">手順 1:リセット ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-204">Step 1: Select the reset button.</span></span> <span data-ttu-id="5a2bc-205">[Base Scene] では [ResetRoundButton] という名前になっています。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-205">In the base scene, it’s named "ResetRoundButton."</span></span> 

<span data-ttu-id="5a2bc-206">手順 2:[Base Scene] 階層の [月着陸船] を、[インスペクター] パネルの [Button Pressed] の下の空のスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-206">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under "button pressed" the inspector panel.</span></span>
 <span data-ttu-id="5a2bc-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="5a2bc-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="5a2bc-208">手順 3:[関数なし] が表示されたドロップダウン メニューを選択し、[LaunchLunarModule] にマウス ポインターを置きます</span><span class="sxs-lookup"><span data-stu-id="5a2bc-208">Step 3: Select the dropdown menu that says, "no function" and hover over "LaunchLunarModule."</span></span> <span data-ttu-id="5a2bc-209">ここで [resetModule ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-209">Now select "resetModule ()."</span></span>

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="5a2bc-211">注:既定では、[GameObject.BroadcastMessage] が [ResetPlacement] に構成されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-211">Note: You will notice that by default the "GameObject.BroadcastMessage" is configured to "ResetPlacement."</span></span> <span data-ttu-id="5a2bc-212">これにより、RocketLauncher_Tutorial のすべての子オブジェクトに [ResetPlacement] という名前のメッセージがブロードキャストされます。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-212">This will broadcast a message called "ResetPlacement" for every child object of RocketLauncher_Tutorial.</span></span> <span data-ttu-id="5a2bc-213">[ResetPlacement()] 用のメソッドを持つオブジェクトはすべて、その位置をリセットすることによってそのメッセージに応答します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-213">Any object that has a method for "ResetPlacement()" will respond to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="5a2bc-214">月着陸船の発射</span><span class="sxs-lookup"><span data-stu-id="5a2bc-214">Launching the Lunar Module</span></span>
<span data-ttu-id="5a2bc-215">この章では、発射ボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-215">This chapter we will be configuring the launch button.</span></span> <span data-ttu-id="5a2bc-216">これにより、ユーザーはそのボタンを押して月着陸船を宇宙に発射することができます。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-216">This will permit the user to press the button and launch the Lunar Module into space.</span></span>

<span data-ttu-id="5a2bc-217">手順 1:発射ボタン ([Base Scene] では [LaunchRoundButton] という名前になっています) を選択します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-217">Step 1: Select the launch button (in the base scene it’s named "LaunchRoundButton").</span></span> <span data-ttu-id="5a2bc-218">[月着陸船] を [インスペクター] パネルの [タッチ終了] の下の空のスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-218">Drag the Lunar Module to the empty slot under "Touch End" in the inspector panel.</span></span>
 <span data-ttu-id="5a2bc-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 手順 2:[関数なし] が表示されたドロップダウン メニューを選択します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the dropdown menu that says, "no function."</span></span> <span data-ttu-id="5a2bc-220">[LaunchLunarModule] にマウス ポインターを置いて [StopThruster ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-220">Hover over "LaunchLunarModule" and select "StopThruster ()."</span></span> <span data-ttu-id="5a2bc-221">これにより、ユーザーが月着陸船にどれだけの推進力を与えるかが制御されます。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-221">This will control how much thrust the user wants to give to the Lunar Module.</span></span> 
 <span data-ttu-id="5a2bc-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) 手順 3:[ButtonPressed()] の下で、[月着陸船] を空のスロットに追加 (クリック、保持、ドラッグ) します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) Step 3: Under "ButtonPressed()", add the Lunar Module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="5a2bc-223">手順 4:[関数なし] が表示されたドロップダウン メニューをクリックし、[LaunchLunarModule] にマウス ポインターを置いて [StartThruster ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-223">Step 4: Click the dropdown menu that says, "no function" and hover over "LaunchLunarModule" and select "StartThruster ()."</span></span> 
 <span data-ttu-id="5a2bc-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) 手順 5:ロケットが発射したら音楽が再生されるように、月着陸船に音楽を追加します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) Step 5: Add music to the Lunar Module so that when the rocket takes off, the music will play.</span></span> <span data-ttu-id="5a2bc-225">これを行うには、[月着陸船] を [Button Pressed()] の下の次の空のスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-225">To do this, drag the Lunar Module to the next empty slot under "Button Pressed()".</span></span>

<span data-ttu-id="5a2bc-226">手順 6:[関数なし] が表示されたドロップダウン メニューを選択し、[AudioSource] にマウス ポインターを置いて [PlayOneShot (AudioClip)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-226">Step 6: Select the dropdown menu that says, "no function" and hover over "AudioSource" and select "PlayOneShot (AudioClip)."</span></span> <span data-ttu-id="5a2bc-227">MRTK に含まれているさまざまな音から自由に選択してください。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-227">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="5a2bc-228">この例では、[MRTK_Gem] を使用します。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-228">For this example, we are going to stick with "MRTK_Gem."</span></span>
 <span data-ttu-id="5a2bc-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="5a2bc-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="5a2bc-230">結論</span><span class="sxs-lookup"><span data-stu-id="5a2bc-230">Congratulations</span></span> 
<span data-ttu-id="5a2bc-231">このアプリケーションが完全に構成されました。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-231">You have fully configured this application!</span></span> <span data-ttu-id="5a2bc-232">これで [再生] を押せば、月着陸船を完全に組み立てたり、ヒントを切り替えたり、月着陸船を発射したり、始めからやり直すためにリセットしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="5a2bc-232">Now when you press play, you can fully assemble the Lunar Module, toggle hints, launch the Lunar Module, and reset it to do it all over again.</span></span>
