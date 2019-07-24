---
title: MR 学習ベース モジュール - 月着陸船アセンブリのサンプル エクスペリエンス
description: このレッスンでは、前のレッスンから学習した複数の概念を組み合わせて固有のサンプル エクスペリエンスを作成します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 79f2d3a4a3224533761ea2e4a7e73dc3d4d5e53e
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387685"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="1af2b-104">7.旧暦モジュールサンプルアプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="1af2b-104">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="1af2b-105">このチュートリアルでは、前のレッスンで説明した複数の概念を組み合わせて、独自のサンプルエクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-105">In this tutorial, we combine multiple concepts presented in the previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="1af2b-106">旧暦モジュールアセンブリアプリケーションを作成します。このアプリケーションでは、ユーザーが追跡したハンドを使用して旧暦モジュールパーツを取得し、旧暦モジュールを組み立てるようにします。</span><span class="sxs-lookup"><span data-stu-id="1af2b-106">We will create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts, and attempt to assemble a lunar module.</span></span> <span data-ttu-id="1af2b-107">Pressable ボタンを使用して配置ヒントを切り替え、エクスペリエンスをリセットして、旧暦モジュールをスペースで起動します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-107">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="1af2b-108">今後のチュートリアルでは、このエクスペリエンスの構築を続けています。これには、空間アラインメントに Azure 空間アンカーを利用する強力なマルチユーザーユースケースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-108">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="1af2b-109">目的</span><span class="sxs-lookup"><span data-stu-id="1af2b-109">Objectives</span></span>

- <span data-ttu-id="1af2b-110">前のレッスンの複数の概念を組み合わせて固有のエクスペリエンスを作成する</span><span class="sxs-lookup"><span data-stu-id="1af2b-110">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="1af2b-111">オブジェクトを切り替える方法を学習する</span><span class="sxs-lookup"><span data-stu-id="1af2b-111">Learn how to toggle objects</span></span>
- <span data-ttu-id="1af2b-112">押しボタンを使用して複雑なイベントをトリガーする</span><span class="sxs-lookup"><span data-stu-id="1af2b-112">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="1af2b-113">剛体の物理学と力を使用する</span><span class="sxs-lookup"><span data-stu-id="1af2b-113">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="1af2b-114">ヒントの使用を調査する</span><span class="sxs-lookup"><span data-stu-id="1af2b-114">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="1af2b-115">手順</span><span class="sxs-lookup"><span data-stu-id="1af2b-115">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="1af2b-116">月着陸船の構成</span><span class="sxs-lookup"><span data-stu-id="1af2b-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="1af2b-117">このセクションでは、サンプルエクスペリエンスを作成するために必要なさまざまなコンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-117">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="1af2b-118">基本シーンに旧暦モジュールアセンブリ prefab を追加します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-118">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="1af2b-119">これを行うには、[プロジェクト] タブで、ロケット Launcher_Tutorial を検索します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-119">To do this, from the Project tab, search for Rocket Launcher_Tutorial.</span></span> 
<span data-ttu-id="1af2b-120">「Assets-> BaseModuleAssets-> Prefabs」で prefab を見つけます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-120">Find the prefab in Assets->BaseModuleAssets->Prefabs.</span></span> <span data-ttu-id="1af2b-121">また、2つのロケットランチャー prefabs も表示されます。1つは "チュートリアル" という名前で、もう1つは "complete" という名前です。</span><span class="sxs-lookup"><span data-stu-id="1af2b-121">You'll also see two rocket launcher prefabs; one with the name "tutorial" and the other with the name "complete".</span></span> <span data-ttu-id="1af2b-122">ロケット Launcher_Tutorial prefab を基本シーンにドラッグし、必要に応じて位置を移動します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-122">Drag the Rocket Launcher_Tutorial prefab to your base scene, and position as you wish.</span></span>
   <span data-ttu-id="1af2b-123">注:ロケット Launcher_Complete prefab は、参照用に用意された、完成したランチャーです。</span><span class="sxs-lookup"><span data-stu-id="1af2b-123">Note: The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="1af2b-125">階層内でロケット Launcher_Tutorial game オブジェクトを展開し、さらに太陰暦モジュールオブジェクトをさらに展開すると、"x 射線" という名前の素材を持ついくつかの子オブジェクトが見つかります。</span><span class="sxs-lookup"><span data-stu-id="1af2b-125">If you expand the Rocket Launcher_Tutorial game object in your hierarchy, and further expand the Lunar Module object, you find several child objects that have a material called, "x-ray."</span></span> <span data-ttu-id="1af2b-126">"X 射線" のマテリアルでは、ユーザーの配置ヒントとして使用する半透明色を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-126">The "x-ray" material allows for a slightly translucent color that we will use as placement hints for the user.</span></span> 

<span data-ttu-id="1af2b-127">![Lesson6 chapter1.txt](images/Lesson6_Chapter1_noteaim.PNG)については、次の図に示すように、ユーザーが対話する、太陰暦モジュールに5つの部分があります。</span><span class="sxs-lookup"><span data-stu-id="1af2b-127">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user will interact with as shown in the image below:</span></span>

1.  <span data-ttu-id="1af2b-128">探査車格納庫</span><span class="sxs-lookup"><span data-stu-id="1af2b-128">The Rover Enclosure</span></span>
2.  <span data-ttu-id="1af2b-129">燃料タンク</span><span class="sxs-lookup"><span data-stu-id="1af2b-129">The Fuel Tank</span></span>
3.  <span data-ttu-id="1af2b-130">エネルギー セル</span><span class="sxs-lookup"><span data-stu-id="1af2b-130">The Energy Cell</span></span>
4.  <span data-ttu-id="1af2b-131">ドッキング ポータル</span><span class="sxs-lookup"><span data-stu-id="1af2b-131">The Docking Portal</span></span> 
5.  <span data-ttu-id="1af2b-132">外部センサー</span><span class="sxs-lookup"><span data-stu-id="1af2b-132">The External sensor</span></span>

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="1af2b-134">注:基本のシーン階層に表示されるゲームオブジェクト名は、シーン内のオブジェクトの名前に対応していません。</span><span class="sxs-lookup"><span data-stu-id="1af2b-134">Note: The Game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="1af2b-135">手順 2:月着陸船にオーディオ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-135">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="1af2b-136">基本のシーン階層で旧暦モジュールが選択されていることを確認し、[コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1af2b-136">Make sure the lunar module is selected in your base scene hierarchy, and click Add Component.</span></span> <span data-ttu-id="1af2b-137">オーディオソースを検索し、それをオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-137">Search for Audio Source, and add it to the object.</span></span> <span data-ttu-id="1af2b-138">今は空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="1af2b-138">Leave it blank for now.</span></span> <span data-ttu-id="1af2b-139">これは、後で発射音を再生するために使用します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-139">We will use this to play the launching sound later.</span></span>

 ![Lesson6 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)  
<span data-ttu-id="1af2b-141">手順 3:スクリプトを追加し、配置ヒントを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-141">Step 3: Add the script, Toggle Placement Hints.</span></span> <span data-ttu-id="1af2b-142">[コンポーネントの追加] をクリックし、[配置ヒントの切り替え] を検索します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-142">Click Add Component, and search for Toggle Placement Hints.</span></span> <span data-ttu-id="1af2b-143">これは、前に説明した半透明なヒント (x 線を持つオブジェクト) のオンとオフを切り替えることができるカスタムスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="1af2b-143">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span>  
![Lesson6 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)  
<span data-ttu-id="1af2b-145">手順 4:5つのオブジェクトがあるため、game オブジェクトの配列サイズとして「5」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-145">Step 4: Since we have five objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="1af2b-146">5つの新しい要素が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-146">You'll then see five new elements appear.</span></span>  


![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="1af2b-148">各半透明オブジェクトを [すべての名前 (Game Obect)] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1af2b-148">Drag each of the translucent objects into all the Name (Game Obect) boxes.</span></span>
<span data-ttu-id="1af2b-149">[Base Scene] の月着陸船の次のオブジェクトをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1af2b-149">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="1af2b-150">•   Backpack</span><span class="sxs-lookup"><span data-stu-id="1af2b-150">•   Backpack</span></span>

<span data-ttu-id="1af2b-151">•   GasTank</span><span class="sxs-lookup"><span data-stu-id="1af2b-151">•   GasTank</span></span>

<span data-ttu-id="1af2b-152">•   Topleftbody</span><span class="sxs-lookup"><span data-stu-id="1af2b-152">•   Topleftbody</span></span>

<span data-ttu-id="1af2b-153">•   Nose</span><span class="sxs-lookup"><span data-stu-id="1af2b-153">•   Nose</span></span>

<span data-ttu-id="1af2b-154">•   LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="1af2b-154">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="1af2b-156">これで、配置ヒントの切り替えスクリプトが構成されました。</span><span class="sxs-lookup"><span data-stu-id="1af2b-156">Now the Toggle Placement Hints script is configured.</span></span> <span data-ttu-id="1af2b-157">これにより、ヒントを有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-157">This allow us to turn hints on and off.</span></span>

<span data-ttu-id="1af2b-158">手順 5:Launch 旧暦モジュールスクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-158">Step 5: Add the Launch Lunar Module script.</span></span> <span data-ttu-id="1af2b-159">[コンポーネントの追加] ボタンをクリックし、"launch 旧暦モジュール" を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-159">Click the Add Component button, search for "launch lunar module", and select it.</span></span> <span data-ttu-id="1af2b-160">このスクリプトは、旧暦モジュールを起動します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-160">This script launches the lunar module.</span></span> <span data-ttu-id="1af2b-161">構成されたボタンを押したときに、旧暦モジュールの固定本文コンポーネントに上位の力を追加し、モジュールを上方に起動します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-161">When we press a configured button, it adds an upward force to the lunar module's rigid body component, and causes the module to launch upwards.</span></span> <span data-ttu-id="1af2b-162">屋内にいる場合は、月着陸船が天井メッシュに当たってクラッシュする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1af2b-162">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="1af2b-163">ただし、屋外にいる場合は、宇宙をいつまでも飛行します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-163">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="1af2b-165">手順 6:月着陸船が正常に上に向かって飛行するように [推進力] を調整します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-165">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="1af2b-166">0\.01 の値を試してください。</span><span class="sxs-lookup"><span data-stu-id="1af2b-166">Try a value of 0.01.</span></span> <span data-ttu-id="1af2b-167">[Rb] フィールドは空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="1af2b-167">Leave the "Rb" field blank.</span></span> <span data-ttu-id="1af2b-168">Rb は剛体を表し、このフィールドは実行時に自動的にデータが入力されます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-168">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="1af2b-170">旧暦モジュールパーツの概要</span><span class="sxs-lookup"><span data-stu-id="1af2b-170">Lunar Module Parts overview</span></span>
<span data-ttu-id="1af2b-171">旧暦モジュールパーツの親オブジェクトは、ユーザーが操作するオブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="1af2b-171">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="1af2b-172">Paretheses に名前が付いているシーンを含む Game オブジェクト名は、次の一覧に示されています。</span><span class="sxs-lookup"><span data-stu-id="1af2b-172">The Game object names, with scene labeled names in paretheses, are provided in the list below:</span></span>

- <span data-ttu-id="1af2b-173">Backpack (燃料タンク)</span><span class="sxs-lookup"><span data-stu-id="1af2b-173">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="1af2b-174">GasTank (エネルギー セル)</span><span class="sxs-lookup"><span data-stu-id="1af2b-174">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="1af2b-175">TopLeftBody (探査車格納庫)</span><span class="sxs-lookup"><span data-stu-id="1af2b-175">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="1af2b-176">Nose (ドッキング ポータル)</span><span class="sxs-lookup"><span data-stu-id="1af2b-176">Nose (Docking Portal)</span></span>
- <span data-ttu-id="1af2b-177">LeftTwirler (外部センサー)</span><span class="sxs-lookup"><span data-stu-id="1af2b-177">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="1af2b-178">これらの各オブジェクトには、レッスン4で説明した操作ハンドラーがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1af2b-178">Notice that each of these objects has a manipulation handler as discussed in Lesson 4.</span></span> <span data-ttu-id="1af2b-179">操作ハンドラーを使用すると、ユーザーはオブジェクトを取得して操作できます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-179">With the manipulation handler, users can grab and manipulate the object.</span></span> <span data-ttu-id="1af2b-180">また、設定 [2 つのきき操作の種類] が [移動と回転] に設定されていることにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="1af2b-180">Also note that the setting, Two Handed Manipulation Type is set to Move and Rotate.</span></span> <span data-ttu-id="1af2b-181">これにより、ユーザーはオブジェクトを移動することしかできず、サイズは変更できません。これは、アセンブリ アプリケーションには望ましい機能です。</span><span class="sxs-lookup"><span data-stu-id="1af2b-181">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="1af2b-182">さらに、モジュールパーツを直接やり取りするためだけに、遠くの操作はオフになっています。</span><span class="sxs-lookup"><span data-stu-id="1af2b-182">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="1af2b-184">部分アセンブリデモスクリプト (上図参照) は、ユーザーがユーザーによってユーザーが旧暦モジュールに配置するオブジェクトを管理するスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="1af2b-184">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span> 

<span data-ttu-id="1af2b-185">フィールドを配置するオブジェクトは、上の図に示すように選択されている変換です。これは、接続先のオブジェクトに関連付けられている backpack/燃料タンクです。</span><span class="sxs-lookup"><span data-stu-id="1af2b-185">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span> 

<span data-ttu-id="1af2b-186">近距離距離と遠く距離の設定によって、どのパーツがどこに配置されているか、または解放できるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="1af2b-186">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="1af2b-187">たとえば、backpack/燃料タンクは、位置に合わせる前に、旧暦モジュールから離れた0.1 単位である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1af2b-187">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="1af2b-188">[遠くの距離] 設定では、オブジェクトが旧暦モジュールからデタッチできるようになる位置が設定されます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-188">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="1af2b-189">この場合、ユーザーの手は Backpack/燃料タンクをつかみ、再度はめ込まれないように取り外すには月着陸船から 0.2 ユニット離れた場所に引く必要があります。</span><span class="sxs-lookup"><span data-stu-id="1af2b-189">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="1af2b-190">ツールヒントオブジェクトはシーンのツールヒントラベルです。</span><span class="sxs-lookup"><span data-stu-id="1af2b-190">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="1af2b-191">オブジェクトが所定の位置にスナップされると、ラベルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="1af2b-191">When the objects are snapped in place, the label is disabled.</span></span> 

<span data-ttu-id="1af2b-192">オーディオソースが自動的にグラブされます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-192">The Audio Source is automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="1af2b-193">配置ヒントボタン</span><span class="sxs-lookup"><span data-stu-id="1af2b-193">Placement Hints buttons</span></span>
<span data-ttu-id="1af2b-194">[レッスン 2](mrlearning-base-ch2.md) では、項目の色を変更したり、押されたら音を再生したりするなどの操作を実行するためのボタンを配置および構成する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="1af2b-194">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="1af2b-195">ここでは配置のヒントを切り替えるためのボタンを構成するため、これらの原則を引き続き使用します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-195">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="1af2b-196">目標は、ユーザーが配置ヒントボタンを押すたびに、半透明の配置ヒントが表示されるように、ボタンを構成することです。</span><span class="sxs-lookup"><span data-stu-id="1af2b-196">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="1af2b-197">手順 1:基本のシーン階層で配置ヒントオブジェクトが選択されている間、[インスペクター] パネルの空のランタイムのみのスロットに旧暦モジュールを移動します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-197">Step 1: Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="1af2b-198">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 手順 2:次に、[関数なし] ドロップダウンリストをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1af2b-198">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the No Function dropdown list.</span></span> <span data-ttu-id="1af2b-199">TogglePlacementHints に移動し、そのメニューの [ToggleGameObjects ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-199">Go down to TogglePlacementHints, and under that menu select ToggleGameObjects ().</span></span> <span data-ttu-id="1af2b-200">ToggleGameObjects () は、ボタンが押されるたびに表示または非表示になるように配置ヒントのオンとオフを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-200">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>  
 <span data-ttu-id="1af2b-201">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="1af2b-201">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="1af2b-202">[リセット] ボタンの構成</span><span class="sxs-lookup"><span data-stu-id="1af2b-202">Configuring the Reset button</span></span>

<span data-ttu-id="1af2b-203">ユーザーが間違っている場合や、誤ってオブジェクトを破棄した場合や、エクスペリエンスをリセットしたい場合があります。</span><span class="sxs-lookup"><span data-stu-id="1af2b-203">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to reset the experience.</span></span> <span data-ttu-id="1af2b-204">[リセット] ボタンをクリックすると、エクスペリエンスを再起動する機能が追加されます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-204">The Reset button adds the ability to restart the experience.</span></span> 

<span data-ttu-id="1af2b-205">手順 1:[リセット] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-205">Step 1: Select the Reset button.</span></span> <span data-ttu-id="1af2b-206">基本シーンでは、ResetRoundButton という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-206">In the base scene, it’s named, ResetRoundButton.</span></span> 

<span data-ttu-id="1af2b-207">手順 2:[インスペクター] パネルの [Button] の下にある空のスロットに、[基本シーン] 階層から旧暦モジュールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1af2b-207">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed the inspector panel.</span></span>
 <span data-ttu-id="1af2b-208">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="1af2b-208">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="1af2b-209">手順 3:[関数なし] ドロップダウンメニューを選択し、LaunchLunarModule の上にポインターを合わせ、resetModule () を選択します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-209">Step 3: Select the No Function dropdown menu, and hover over LaunchLunarModule,  select resetModule ().</span></span>

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="1af2b-211">注:既定では、BroadcastMessage は ResetPlacement に構成されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1af2b-211">Note: Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="1af2b-212">これにより、RocketLauncher_Tutorial のすべての子オブジェクトに対する ResetPlacement というメッセージがブロードキャストされます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-212">This broadcasts a message called, ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="1af2b-213">ResetPlacement () のメソッドを持つオブジェクトは、位置をリセットすることによって、そのメッセージに応答します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-213">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="1af2b-214">旧暦モジュールを起動しています</span><span class="sxs-lookup"><span data-stu-id="1af2b-214">Launching the lunar module</span></span>
<span data-ttu-id="1af2b-215">このセクションでは、起動ボタンの構成方法を explaings します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-215">This section explaings how to configure the Launch button.</span></span> <span data-ttu-id="1af2b-216">これにより、ユーザーはボタンを押して、旧暦モジュールをスペースで起動できます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-216">This permits the user to press the button and launch the lunar module into space.</span></span>

<span data-ttu-id="1af2b-217">手順 1:[起動] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-217">Step 1: Select the Launch button.</span></span> <span data-ttu-id="1af2b-218">それが呼び出される基本シーンでは、LaunchRoundButton になります。</span><span class="sxs-lookup"><span data-stu-id="1af2b-218">In the base scene it’s called, LaunchRoundButton.</span></span> <span data-ttu-id="1af2b-219">[インスペクター] パネルの [タッチエンド] の下にある空のスロットに、旧暦モジュールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1af2b-219">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>
 <span data-ttu-id="1af2b-220">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 手順 2:[関数なし] ドロップダウンメニューを選択し、LaunchLunarModule の上にマウスポインターを移動し、[StopThruster ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-220">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the No Function dropdown menu, and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="1af2b-221">これにより、ユーザーが旧暦モジュールに与える推力の量が制御されます。</span><span class="sxs-lookup"><span data-stu-id="1af2b-221">This controls how much thrust the user wants to give to the lunar module.</span></span> 
 <span data-ttu-id="1af2b-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="1af2b-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span></span>  
<span data-ttu-id="1af2b-223">手順 3:ButtonPressed れた () の下で、空のスロットに旧暦モジュール (クリック、ホールド、ドラッグ) を追加します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-223">Step 3: Under ButtonPressed(), add the lunar module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="1af2b-224">手順 4:[関数なし] ドロップダウンメニューをクリックし、LaunchLunarModule の上にマウスポインターを移動し、[StartThruster ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-224">Step 4: Click the No function dropdown menu, and hover over LaunchLunarModule, and select StartThruster ().</span></span> 
 <span data-ttu-id="1af2b-225">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span><span class="sxs-lookup"><span data-stu-id="1af2b-225">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span></span>  
<span data-ttu-id="1af2b-226">手順 5:音楽がロケットの撮影時に再生されるように、旧暦モジュールに音楽を追加します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-226">Step 5: Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="1af2b-227">これを行うには、[] ボタンが押された状態の次の空のスロット () に旧暦モジュールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1af2b-227">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

<span data-ttu-id="1af2b-228">手順 6:[関数なし] ドロップダウンメニューを選択し、AudioSource の上にマウスポインターを移動して、[PlayOneShot (Audiosource)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-228">Step 6: Select the No Function dropdown menu, hover over AudioSource, and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="1af2b-229">MRTK に含まれているさまざまな音から自由に選択してください。</span><span class="sxs-lookup"><span data-stu-id="1af2b-229">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="1af2b-230">この例では、"MRTK_Gem" を使用します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-230">For this example, we'll use "MRTK_Gem."</span></span>
 <span data-ttu-id="1af2b-231">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="1af2b-231">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="1af2b-232">結論</span><span class="sxs-lookup"><span data-stu-id="1af2b-232">Congratulations</span></span> 
<span data-ttu-id="1af2b-233">このアプリケーションは完全に構成されています。</span><span class="sxs-lookup"><span data-stu-id="1af2b-233">You have fully configured this application.</span></span> <span data-ttu-id="1af2b-234">ここで、[再生] をクリックすると、旧暦モジュールを完全に組み立て、ヒントを切り替えることができます。さらに、旧暦モジュールを起動してリセットし、再起動してもう一度開始します。</span><span class="sxs-lookup"><span data-stu-id="1af2b-234">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module, and reset it to start all over again.</span></span>
