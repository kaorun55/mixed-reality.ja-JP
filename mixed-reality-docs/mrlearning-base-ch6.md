---
title: 入門チュートリアル-7. 旧暦モジュールサンプルアプリケーションの作成
description: このレッスンでは、前のレッスンから学習した複数の概念を組み合わせて固有のサンプル エクスペリエンスを作成します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: f45aa7e2f07a8a67cd56f0aae140de3a68afc918
ms.sourcegitcommit: e9a55528965048ce34f8247ef6e544f9f432ee37
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69559893"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="4f485-105">7.旧暦モジュールサンプルアプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="4f485-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="4f485-106">このチュートリアルでは、前のレッスンで説明した複数の概念を組み合わせて、独自のサンプルエクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f485-106">In this tutorial, we combine multiple concepts presented in the previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="4f485-107">旧暦モジュールアセンブリアプリケーションを作成します。このアプリケーションでは、ユーザーが追跡したハンドを使用して旧暦モジュールパーツを取得し、旧暦モジュールを組み立てるようにします。</span><span class="sxs-lookup"><span data-stu-id="4f485-107">We will create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts, and attempt to assemble a lunar module.</span></span> <span data-ttu-id="4f485-108">Pressable ボタンを使用して配置ヒントを切り替え、エクスペリエンスをリセットして、旧暦モジュールをスペースで起動します。</span><span class="sxs-lookup"><span data-stu-id="4f485-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="4f485-109">今後のチュートリアルでは、このエクスペリエンスの構築を続けています。これには、空間アラインメントに Azure 空間アンカーを利用する強力なマルチユーザーユースケースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4f485-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="4f485-110">目的</span><span class="sxs-lookup"><span data-stu-id="4f485-110">Objectives</span></span>

- <span data-ttu-id="4f485-111">前のレッスンの複数の概念を組み合わせて固有のエクスペリエンスを作成する</span><span class="sxs-lookup"><span data-stu-id="4f485-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="4f485-112">オブジェクトを切り替える方法を学習する</span><span class="sxs-lookup"><span data-stu-id="4f485-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="4f485-113">押しボタンを使用して複雑なイベントをトリガーする</span><span class="sxs-lookup"><span data-stu-id="4f485-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="4f485-114">剛体の物理学と力を使用する</span><span class="sxs-lookup"><span data-stu-id="4f485-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="4f485-115">ヒントの使用を調査する</span><span class="sxs-lookup"><span data-stu-id="4f485-115">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="4f485-116">手順</span><span class="sxs-lookup"><span data-stu-id="4f485-116">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="4f485-117">月着陸船の構成</span><span class="sxs-lookup"><span data-stu-id="4f485-117">Configuring the Lunar Module</span></span>

<span data-ttu-id="4f485-118">このセクションでは、サンプルエクスペリエンスを作成するために必要なさまざまなコンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4f485-118">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="4f485-119">基本シーンに旧暦モジュールアセンブリ prefab を追加します。</span><span class="sxs-lookup"><span data-stu-id="4f485-119">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="4f485-120">これを行うには、[プロジェクト] タブで、ロケット Launcher_Tutorial を検索します。</span><span class="sxs-lookup"><span data-stu-id="4f485-120">To do this, from the Project tab, search for Rocket Launcher_Tutorial.</span></span> 
<span data-ttu-id="4f485-121">「Assets-> BaseModuleAssets-> Prefabs」で prefab を見つけます。</span><span class="sxs-lookup"><span data-stu-id="4f485-121">Find the prefab in Assets->BaseModuleAssets->Prefabs.</span></span> <span data-ttu-id="4f485-122">また、2つのロケットランチャー prefabs も表示されます。1つは "チュートリアル" という名前で、もう1つは "complete" という名前です。</span><span class="sxs-lookup"><span data-stu-id="4f485-122">You'll also see two rocket launcher prefabs; one with the name "tutorial" and the other with the name "complete".</span></span> <span data-ttu-id="4f485-123">ロケット Launcher_Tutorial prefab を基本シーンにドラッグし、必要に応じて位置を移動します。</span><span class="sxs-lookup"><span data-stu-id="4f485-123">Drag the Rocket Launcher_Tutorial prefab to your base scene, and position as you wish.</span></span>
   <span data-ttu-id="4f485-124">注:ロケット Launcher_Complete prefab は、参照用に用意された、完成したランチャーです。</span><span class="sxs-lookup"><span data-stu-id="4f485-124">Note: The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="4f485-126">階層内でロケット Launcher_Tutorial game オブジェクトを展開し、さらに太陰暦モジュールオブジェクトをさらに展開すると、"x 射線" という名前の素材を持ついくつかの子オブジェクトが見つかります。</span><span class="sxs-lookup"><span data-stu-id="4f485-126">If you expand the Rocket Launcher_Tutorial game object in your hierarchy, and further expand the Lunar Module object, you find several child objects that have a material called, "x-ray."</span></span> <span data-ttu-id="4f485-127">"X 射線" のマテリアルでは、ユーザーの配置ヒントとして使用する半透明色を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4f485-127">The "x-ray" material allows for a slightly translucent color that we will use as placement hints for the user.</span></span> 

<span data-ttu-id="4f485-128">![Lesson6 chapter1.txt](images/Lesson6_Chapter1_noteaim.PNG)については、次の図に示すように、ユーザーが対話する、太陰暦モジュールに5つの部分があります。</span><span class="sxs-lookup"><span data-stu-id="4f485-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user will interact with as shown in the image below:</span></span>

1.  <span data-ttu-id="4f485-129">探査車格納庫</span><span class="sxs-lookup"><span data-stu-id="4f485-129">The Rover Enclosure</span></span>
2.  <span data-ttu-id="4f485-130">燃料タンク</span><span class="sxs-lookup"><span data-stu-id="4f485-130">The Fuel Tank</span></span>
3.  <span data-ttu-id="4f485-131">エネルギー セル</span><span class="sxs-lookup"><span data-stu-id="4f485-131">The Energy Cell</span></span>
4.  <span data-ttu-id="4f485-132">ドッキング ポータル</span><span class="sxs-lookup"><span data-stu-id="4f485-132">The Docking Portal</span></span> 
5.  <span data-ttu-id="4f485-133">外部センサー</span><span class="sxs-lookup"><span data-stu-id="4f485-133">The External sensor</span></span>

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="4f485-135">注:基本のシーン階層に表示されるゲームオブジェクト名は、シーン内のオブジェクトの名前に対応していません。</span><span class="sxs-lookup"><span data-stu-id="4f485-135">Note: The Game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="4f485-136">手順 2:月着陸船にオーディオ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f485-136">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="4f485-137">基本のシーン階層で旧暦モジュールが選択されていることを確認し、[コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f485-137">Make sure the lunar module is selected in your base scene hierarchy, and click Add Component.</span></span> <span data-ttu-id="4f485-138">オーディオソースを検索し、それをオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="4f485-138">Search for Audio Source, and add it to the object.</span></span> <span data-ttu-id="4f485-139">ここでは空白のままにしておいてください。ただし、[Spatialize] チェックボックスをオンにして、空間オーディオを有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="4f485-139">Leave it blank for now, but make sure to click the "Spatialize" checkbox to enable spatial audio.</span></span> <span data-ttu-id="4f485-140">これは、後で発射音を再生するために使用します。</span><span class="sxs-lookup"><span data-stu-id="4f485-140">We will use this to play the launching sound later.</span></span>

 ![Lesson6 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)  
<span data-ttu-id="4f485-142">手順 3:スクリプトを追加し、配置ヒントを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="4f485-142">Step 3: Add the script, Toggle Placement Hints.</span></span> <span data-ttu-id="4f485-143">[コンポーネントの追加] をクリックし、[配置ヒントの切り替え] を検索します。</span><span class="sxs-lookup"><span data-stu-id="4f485-143">Click Add Component, and search for Toggle Placement Hints.</span></span> <span data-ttu-id="4f485-144">これは、前に説明した半透明なヒント (x 線を持つオブジェクト) のオンとオフを切り替えることができるカスタムスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="4f485-144">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span>  
![Lesson6 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)  
<span data-ttu-id="4f485-146">手順 4:5つのオブジェクトがあるため、game オブジェクトの配列サイズとして「5」と入力します。</span><span class="sxs-lookup"><span data-stu-id="4f485-146">Step 4: Since we have five objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="4f485-147">5つの新しい要素が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f485-147">You'll then see five new elements appear.</span></span>  


![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="4f485-149">各半透明オブジェクトを [すべての名前 (Game Obect)] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4f485-149">Drag each of the translucent objects into all the Name (Game Obect) boxes.</span></span>
<span data-ttu-id="4f485-150">[Base Scene] の月着陸船の次のオブジェクトをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4f485-150">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="4f485-151">•   Backpack</span><span class="sxs-lookup"><span data-stu-id="4f485-151">•   Backpack</span></span>

<span data-ttu-id="4f485-152">•   GasTank</span><span class="sxs-lookup"><span data-stu-id="4f485-152">•   GasTank</span></span>

<span data-ttu-id="4f485-153">•   Topleftbody</span><span class="sxs-lookup"><span data-stu-id="4f485-153">•   Topleftbody</span></span>

<span data-ttu-id="4f485-154">•   Nose</span><span class="sxs-lookup"><span data-stu-id="4f485-154">•   Nose</span></span>

<span data-ttu-id="4f485-155">•   LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="4f485-155">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="4f485-157">これで、配置ヒントの切り替えスクリプトが構成されました。</span><span class="sxs-lookup"><span data-stu-id="4f485-157">Now the Toggle Placement Hints script is configured.</span></span> <span data-ttu-id="4f485-158">これにより、ヒントを有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="4f485-158">This allow us to turn hints on and off.</span></span>

<span data-ttu-id="4f485-159">手順 5:Launch 旧暦モジュールスクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f485-159">Step 5: Add the Launch Lunar Module script.</span></span> <span data-ttu-id="4f485-160">[コンポーネントの追加] ボタンをクリックし、"launch 旧暦モジュール" を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="4f485-160">Click the Add Component button, search for "launch lunar module", and select it.</span></span> <span data-ttu-id="4f485-161">このスクリプトは、旧暦モジュールを起動します。</span><span class="sxs-lookup"><span data-stu-id="4f485-161">This script launches the lunar module.</span></span> <span data-ttu-id="4f485-162">構成されたボタンを押したときに、旧暦モジュールの固定本文コンポーネントに上位の力を追加し、モジュールを上方に起動します。</span><span class="sxs-lookup"><span data-stu-id="4f485-162">When we press a configured button, it adds an upward force to the lunar module's rigid body component, and causes the module to launch upwards.</span></span> <span data-ttu-id="4f485-163">屋内にいる場合は、月着陸船が天井メッシュに当たってクラッシュする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f485-163">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="4f485-164">ただし、屋外にいる場合は、宇宙をいつまでも飛行します。</span><span class="sxs-lookup"><span data-stu-id="4f485-164">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="4f485-166">手順 6:月着陸船が正常に上に向かって飛行するように [推進力] を調整します。</span><span class="sxs-lookup"><span data-stu-id="4f485-166">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="4f485-167">0\.01 の値を試してください。</span><span class="sxs-lookup"><span data-stu-id="4f485-167">Try a value of 0.01.</span></span> <span data-ttu-id="4f485-168">[Rb] フィールドは空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="4f485-168">Leave the "Rb" field blank.</span></span> <span data-ttu-id="4f485-169">Rb は剛体を表し、このフィールドは実行時に自動的にデータが入力されます。</span><span class="sxs-lookup"><span data-stu-id="4f485-169">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="4f485-171">旧暦モジュールパーツの概要</span><span class="sxs-lookup"><span data-stu-id="4f485-171">Lunar Module Parts overview</span></span>
<span data-ttu-id="4f485-172">旧暦モジュールパーツの親オブジェクトは、ユーザーが操作するオブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="4f485-172">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="4f485-173">Paretheses に名前が付いているシーンを含む Game オブジェクト名は、次の一覧に示されています。</span><span class="sxs-lookup"><span data-stu-id="4f485-173">The Game object names, with scene labeled names in paretheses, are provided in the list below:</span></span>

- <span data-ttu-id="4f485-174">Backpack (燃料タンク)</span><span class="sxs-lookup"><span data-stu-id="4f485-174">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="4f485-175">GasTank (エネルギー セル)</span><span class="sxs-lookup"><span data-stu-id="4f485-175">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="4f485-176">TopLeftBody (探査車格納庫)</span><span class="sxs-lookup"><span data-stu-id="4f485-176">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="4f485-177">Nose (ドッキング ポータル)</span><span class="sxs-lookup"><span data-stu-id="4f485-177">Nose (Docking Portal)</span></span>
- <span data-ttu-id="4f485-178">LeftTwirler (外部センサー)</span><span class="sxs-lookup"><span data-stu-id="4f485-178">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="4f485-179">これらの各オブジェクトには、レッスン4で説明した操作ハンドラーがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4f485-179">Notice that each of these objects has a manipulation handler as discussed in Lesson 4.</span></span> <span data-ttu-id="4f485-180">操作ハンドラーを使用すると、ユーザーはオブジェクトを取得して操作できます。</span><span class="sxs-lookup"><span data-stu-id="4f485-180">With the manipulation handler, users can grab and manipulate the object.</span></span> <span data-ttu-id="4f485-181">また、設定 [2 つのきき操作の種類] が [移動と回転] に設定されていることにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="4f485-181">Also note that the setting, Two Handed Manipulation Type is set to Move and Rotate.</span></span> <span data-ttu-id="4f485-182">これにより、ユーザーはオブジェクトを移動することしかできず、サイズは変更できません。これは、アセンブリ アプリケーションには望ましい機能です。</span><span class="sxs-lookup"><span data-stu-id="4f485-182">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="4f485-183">さらに、モジュールパーツを直接やり取りするためだけに、遠くの操作はオフになっています。</span><span class="sxs-lookup"><span data-stu-id="4f485-183">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="4f485-185">部分アセンブリデモスクリプト (上図参照) は、ユーザーがユーザーによってユーザーが旧暦モジュールに配置するオブジェクトを管理するスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="4f485-185">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span> 

<span data-ttu-id="4f485-186">フィールドを配置するオブジェクトは、上の図に示すように選択されている変換です。これは、接続先のオブジェクトに関連付けられている backpack/燃料タンクです。</span><span class="sxs-lookup"><span data-stu-id="4f485-186">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span> 

<span data-ttu-id="4f485-187">近距離距離と遠く距離の設定によって、どのパーツがどこに配置されているか、または解放できるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="4f485-187">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="4f485-188">たとえば、backpack/燃料タンクは、位置に合わせる前に、旧暦モジュールから離れた0.1 単位である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f485-188">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="4f485-189">[遠くの距離] 設定では、オブジェクトが旧暦モジュールからデタッチできるようになる位置が設定されます。</span><span class="sxs-lookup"><span data-stu-id="4f485-189">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="4f485-190">この場合、ユーザーの手は Backpack/燃料タンクをつかみ、再度はめ込まれないように取り外すには月着陸船から 0.2 ユニット離れた場所に引く必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f485-190">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="4f485-191">ツールヒントオブジェクトはシーンのツールヒントラベルです。</span><span class="sxs-lookup"><span data-stu-id="4f485-191">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="4f485-192">オブジェクトが所定の位置にスナップされると、ラベルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="4f485-192">When the objects are snapped in place, the label is disabled.</span></span> 

<span data-ttu-id="4f485-193">オーディオソースが自動的にグラブされます。</span><span class="sxs-lookup"><span data-stu-id="4f485-193">The Audio Source is automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="4f485-194">配置ヒントボタン</span><span class="sxs-lookup"><span data-stu-id="4f485-194">Placement Hints buttons</span></span>
<span data-ttu-id="4f485-195">[レッスン 2](mrlearning-base-ch2.md) では、項目の色を変更したり、押されたら音を再生したりするなどの操作を実行するためのボタンを配置および構成する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="4f485-195">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="4f485-196">ここでは配置のヒントを切り替えるためのボタンを構成するため、これらの原則を引き続き使用します。</span><span class="sxs-lookup"><span data-stu-id="4f485-196">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="4f485-197">目標は、ユーザーが配置ヒントボタンを押すたびに、半透明の配置ヒントが表示されるように、ボタンを構成することです。</span><span class="sxs-lookup"><span data-stu-id="4f485-197">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="4f485-198">手順 1:基本のシーン階層で配置ヒントオブジェクトが選択されている間、[インスペクター] パネルの空のランタイムのみのスロットに旧暦モジュールを移動します。</span><span class="sxs-lookup"><span data-stu-id="4f485-198">Step 1: Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="4f485-199">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 手順 2:次に、[関数なし] ドロップダウンリストをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f485-199">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the No Function dropdown list.</span></span> <span data-ttu-id="4f485-200">TogglePlacementHints に移動し、そのメニューの [ToggleGameObjects ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4f485-200">Go down to TogglePlacementHints, and under that menu select ToggleGameObjects ().</span></span> <span data-ttu-id="4f485-201">ToggleGameObjects () は、ボタンが押されるたびに表示または非表示になるように配置ヒントのオンとオフを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="4f485-201">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>  
 <span data-ttu-id="4f485-202">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="4f485-202">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="4f485-203">[リセット] ボタンの構成</span><span class="sxs-lookup"><span data-stu-id="4f485-203">Configuring the Reset button</span></span>

<span data-ttu-id="4f485-204">ユーザーが間違っている場合や、誤ってオブジェクトを破棄した場合や、エクスペリエンスをリセットしたい場合があります。</span><span class="sxs-lookup"><span data-stu-id="4f485-204">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to reset the experience.</span></span> <span data-ttu-id="4f485-205">[リセット] ボタンをクリックすると、エクスペリエンスを再起動する機能が追加されます。</span><span class="sxs-lookup"><span data-stu-id="4f485-205">The Reset button adds the ability to restart the experience.</span></span> 

<span data-ttu-id="4f485-206">手順 1:[リセット] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="4f485-206">Step 1: Select the Reset button.</span></span> <span data-ttu-id="4f485-207">基本シーンでは、ResetRoundButton という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="4f485-207">In the base scene, it’s named, ResetRoundButton.</span></span> 

<span data-ttu-id="4f485-208">手順 2:[インスペクター] パネルの [Button] の下にある空のスロットに、[基本シーン] 階層から旧暦モジュールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4f485-208">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed the inspector panel.</span></span>
 <span data-ttu-id="4f485-209">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="4f485-209">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="4f485-210">手順 3:[関数なし] ドロップダウンメニューを選択し、LaunchLunarModule の上にポインターを合わせ、resetModule () を選択します。</span><span class="sxs-lookup"><span data-stu-id="4f485-210">Step 3: Select the No Function dropdown menu, and hover over LaunchLunarModule,  select resetModule ().</span></span>

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="4f485-212">注:既定では、BroadcastMessage は ResetPlacement に構成されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4f485-212">Note: Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="4f485-213">これにより、RocketLauncher_Tutorial のすべての子オブジェクトに対する ResetPlacement というメッセージがブロードキャストされます。</span><span class="sxs-lookup"><span data-stu-id="4f485-213">This broadcasts a message called, ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="4f485-214">ResetPlacement () のメソッドを持つオブジェクトは、位置をリセットすることによって、そのメッセージに応答します。</span><span class="sxs-lookup"><span data-stu-id="4f485-214">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="4f485-215">旧暦モジュールを起動しています</span><span class="sxs-lookup"><span data-stu-id="4f485-215">Launching the lunar module</span></span>
<span data-ttu-id="4f485-216">このセクションでは、起動ボタンの構成方法を explaings します。</span><span class="sxs-lookup"><span data-stu-id="4f485-216">This section explaings how to configure the Launch button.</span></span> <span data-ttu-id="4f485-217">これにより、ユーザーはボタンを押して、旧暦モジュールをスペースで起動できます。</span><span class="sxs-lookup"><span data-stu-id="4f485-217">This permits the user to press the button and launch the lunar module into space.</span></span>

<span data-ttu-id="4f485-218">手順 1:[起動] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="4f485-218">Step 1: Select the Launch button.</span></span> <span data-ttu-id="4f485-219">それが呼び出される基本シーンでは、LaunchRoundButton になります。</span><span class="sxs-lookup"><span data-stu-id="4f485-219">In the base scene it’s called, LaunchRoundButton.</span></span> <span data-ttu-id="4f485-220">[インスペクター] パネルの [タッチエンド] の下にある空のスロットに、旧暦モジュールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4f485-220">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>
 <span data-ttu-id="4f485-221">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 手順 2:[関数なし] ドロップダウンメニューを選択し、LaunchLunarModule の上にマウスポインターを移動し、[StopThruster ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4f485-221">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the No Function dropdown menu, and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="4f485-222">これにより、ユーザーが旧暦モジュールに与える推力の量が制御されます。</span><span class="sxs-lookup"><span data-stu-id="4f485-222">This controls how much thrust the user wants to give to the lunar module.</span></span> 
 <span data-ttu-id="4f485-223">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="4f485-223">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span></span>  
<span data-ttu-id="4f485-224">手順 3:ButtonPressed れた () の下で、空のスロットに旧暦モジュール (クリック、ホールド、ドラッグ) を追加します。</span><span class="sxs-lookup"><span data-stu-id="4f485-224">Step 3: Under ButtonPressed(), add the lunar module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="4f485-225">手順 4:[関数なし] ドロップダウンメニューをクリックし、LaunchLunarModule の上にマウスポインターを移動し、[StartThruster ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4f485-225">Step 4: Click the No function dropdown menu, and hover over LaunchLunarModule, and select StartThruster ().</span></span> 
 <span data-ttu-id="4f485-226">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span><span class="sxs-lookup"><span data-stu-id="4f485-226">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span></span>  
<span data-ttu-id="4f485-227">手順 5:音楽がロケットの撮影時に再生されるように、旧暦モジュールに音楽を追加します。</span><span class="sxs-lookup"><span data-stu-id="4f485-227">Step 5: Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="4f485-228">これを行うには、[] ボタンが押された状態の次の空のスロット () に旧暦モジュールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4f485-228">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

<span data-ttu-id="4f485-229">手順 6:[関数なし] ドロップダウンメニューを選択し、AudioSource の上にマウスポインターを移動して、[PlayOneShot (Audiosource)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4f485-229">Step 6: Select the No Function dropdown menu, hover over AudioSource, and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="4f485-230">MRTK に含まれているさまざまな音から自由に選択してください。</span><span class="sxs-lookup"><span data-stu-id="4f485-230">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="4f485-231">この例では、"MRTK_Gem" を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f485-231">For this example, we'll use "MRTK_Gem."</span></span>
 <span data-ttu-id="4f485-232">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="4f485-232">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="4f485-233">結論</span><span class="sxs-lookup"><span data-stu-id="4f485-233">Congratulations</span></span> 
<span data-ttu-id="4f485-234">このアプリケーションは完全に構成されています。</span><span class="sxs-lookup"><span data-stu-id="4f485-234">You have fully configured this application.</span></span> <span data-ttu-id="4f485-235">ここで、[再生] をクリックすると、旧暦モジュールを完全に組み立て、ヒントを切り替えることができます。さらに、旧暦モジュールを起動してリセットし、再起動してもう一度開始します。</span><span class="sxs-lookup"><span data-stu-id="4f485-235">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module, and reset it to start all over again.</span></span>
