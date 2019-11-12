---
title: 入門チュートリアル-7. 旧暦モジュールサンプルアプリケーションの作成
description: このレッスンでは、前のレッスンで学習した複数の概念を組み合わせて、独自のサンプルエクスペリエンスを作成します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: b033e4f9a379fb1778da3d94da70262e073d141b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926519"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="c64fd-105">7. 旧暦モジュールサンプルアプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="c64fd-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="c64fd-106">このチュートリアルでは、前のレッスンとの複数の概念を組み合わせて、独自のサンプルエクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="c64fd-107">旧暦モジュールアセンブリアプリケーションを作成する方法について学習します。ユーザーは、追跡したハンドを使用して旧暦モジュールパーツを取得し、旧暦モジュールを組み立てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c64fd-107">You will learn how to create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="c64fd-108">Pressable ボタンを使用して配置ヒントを切り替え、エクスペリエンスをリセットして、旧暦モジュールをスペースで起動します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="c64fd-109">今後のチュートリアルでは、このエクスペリエンスの構築を続けています。これには、空間アラインメントに Azure 空間アンカーを利用する強力なマルチユーザーユースケースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="c64fd-110">目標</span><span class="sxs-lookup"><span data-stu-id="c64fd-110">Objectives</span></span>

- <span data-ttu-id="c64fd-111">前のレッスンの複数の概念を組み合わせて固有のエクスペリエンスを作成する</span><span class="sxs-lookup"><span data-stu-id="c64fd-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="c64fd-112">オブジェクトを切り替える方法を学習する</span><span class="sxs-lookup"><span data-stu-id="c64fd-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="c64fd-113">押しボタンを使用して複雑なイベントをトリガーする</span><span class="sxs-lookup"><span data-stu-id="c64fd-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="c64fd-114">剛体の物理学と力を使用する</span><span class="sxs-lookup"><span data-stu-id="c64fd-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="c64fd-115">ヒントの使用を調査する</span><span class="sxs-lookup"><span data-stu-id="c64fd-115">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="c64fd-116">手順</span><span class="sxs-lookup"><span data-stu-id="c64fd-116">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="c64fd-117">月着陸船の構成</span><span class="sxs-lookup"><span data-stu-id="c64fd-117">Configuring the Lunar Module</span></span>

<span data-ttu-id="c64fd-118">このセクションでは、サンプルエクスペリエンスを作成するために必要なさまざまなコンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-118">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="c64fd-119">基本シーンに旧暦モジュールアセンブリ prefab を追加します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-119">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="c64fd-120">これを行うには、プロジェクト タブで > BaseModuleAssets > Prefabs に移動します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-120">To do this, in the Project tab navigate to Assets > BaseModuleAssets > Prefabs.</span></span> <span data-ttu-id="c64fd-121">2つのロケットランチャー prefabs が表示され、ロケット Launcher_Tutorial prefab をシーンにドラッグし、必要に応じて配置します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-121">You will see two rocket launcher prefabs, drag the Rocket Launcher_Tutorial prefab into your scene, and position as you wish.</span></span>

    >[!NOTE]
    ><span data-ttu-id="c64fd-122">ロケット Launcher_Complete prefab は、参照用に提供された、完成したランチャーです。</span><span class="sxs-lookup"><span data-stu-id="c64fd-122">The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span>

    ![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

    <span data-ttu-id="c64fd-124">階層内でロケット Launcher_Tutorial game オブジェクトを展開し、旧暦モジュールオブジェクトをさらに展開すると、"x 射線" という素材を持ついくつかの子オブジェクトが検索されます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-124">If you expand the Rocket Launcher_Tutorial game object in your hierarchy and further expand the Lunar Module object, you find several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="c64fd-125">"X 射線" のマテリアルでは、ユーザーの配置ヒントとして使用される半透明色を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-125">The "x-ray" material allows for a slightly translucent color that will be used as placement hints for the user.</span></span> 

    ![Lesson6 Chapter1.txt のターゲット](images/Lesson6_Chapter1_noteaim.PNG)

    <span data-ttu-id="c64fd-127">次の図に示すように、ユーザーが操作する旧暦モジュールには5つの部分があります。</span><span class="sxs-lookup"><span data-stu-id="c64fd-127">There are five parts to the lunar module that the user will interact with, as shown in the image below:</span></span>

    1. <span data-ttu-id="c64fd-128">探査車格納庫</span><span class="sxs-lookup"><span data-stu-id="c64fd-128">The Rover Enclosure</span></span>
    2. <span data-ttu-id="c64fd-129">燃料タンク</span><span class="sxs-lookup"><span data-stu-id="c64fd-129">The Fuel Tank</span></span>
    3. <span data-ttu-id="c64fd-130">エネルギー セル</span><span class="sxs-lookup"><span data-stu-id="c64fd-130">The Energy Cell</span></span>
    4. <span data-ttu-id="c64fd-131">ドッキング ポータル</span><span class="sxs-lookup"><span data-stu-id="c64fd-131">The Docking Portal</span></span>
    5. <span data-ttu-id="c64fd-132">外部センサー</span><span class="sxs-lookup"><span data-stu-id="c64fd-132">The External sensor</span></span>

    ![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    ><span data-ttu-id="c64fd-134">[Base Scene] 階層に表示されるゲーム オブジェクト名は、シーン内のオブジェクトの名前に対応していません。</span><span class="sxs-lookup"><span data-stu-id="c64fd-134">The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

2. <span data-ttu-id="c64fd-135">オーディオソースを LunarModule ゲームオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-135">Add an audio source to the LunarModule game object.</span></span> <span data-ttu-id="c64fd-136">シーン階層で LunarModule が選択されていることを確認し、[コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c64fd-136">Make sure the LunarModule is selected in your scene hierarchy and click Add Component.</span></span> <span data-ttu-id="c64fd-137">オーディオソースを検索し、game オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-137">Search for Audio Source and add it to the game object.</span></span> <span data-ttu-id="c64fd-138">ここでは、[AudioClip] フィールドを空白のままにします。ただし、[特殊な Blend] 設定を0から1に変更して、空間オーディオを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c64fd-138">Leave the AudioClip field blank for now, but change the Special Blend setting from 0 to 1 so to enable spatial audio.</span></span> <span data-ttu-id="c64fd-139">後でサウンドを再生するには、このオーディオソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-139">You will use this audio source to play the launching sound later.</span></span>

    ![Lesson6 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. <span data-ttu-id="c64fd-141">スクリプトの切り替えの配置ヒントを追加します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-141">Add the script Toggle Placement Hints.</span></span> <span data-ttu-id="c64fd-142">[コンポーネントの追加] をクリックし、[配置ヒントの切り替え] を検索します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-142">Click Add Component and search for Toggle Placement Hints.</span></span> <span data-ttu-id="c64fd-143">これは、前に説明したように半透明のヒント (x 線を持つオブジェクト) をオンまたはオフにできるカスタムスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="c64fd-143">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material), as mentioned earlier.</span></span>

    ![Lesson6 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. <span data-ttu-id="c64fd-145">5つのオブジェクトがあるため、game オブジェクトの配列サイズとして「5」と入力します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-145">Since we have five objects, type "5" for the game object array size.</span></span> <span data-ttu-id="c64fd-146">5つの新しい要素が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-146">You will then see five new elements appear.</span></span>

    ![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

    <span data-ttu-id="c64fd-148">各半透明オブジェクトを [すべての名前 (ゲームオブジェクト)] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c64fd-148">Drag each of the translucent objects into all the Name (Game Object) boxes.</span></span> <span data-ttu-id="c64fd-149">上の図に示すように、シーンの旧暦モジュールから次のオブジェクトをオブジェクト配列のフィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c64fd-149">Drag the following objects from the lunar module in your scene into the object array fields as shown in the image above:</span></span>

    ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

    <span data-ttu-id="c64fd-151">[配置ヒントの切り替え] スクリプトが構成され、ヒントをオンまたはオフにできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c64fd-151">The Toggle Placement Hints script is now configured, which allows us to turn hints on and off.</span></span>

5. <span data-ttu-id="c64fd-152">Launch 旧暦モジュールスクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-152">Add the Launch Lunar Module script.</span></span> <span data-ttu-id="c64fd-153">[コンポーネントの追加] ボタンをクリックし、[旧暦モジュールの起動] を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-153">Click the Add Component button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="c64fd-154">このスクリプトは、旧暦モジュールを起動します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-154">This script launches the lunar module.</span></span> <span data-ttu-id="c64fd-155">構成されたボタンを押したときに、旧暦モジュールの固定本文コンポーネントに上位の力が追加され、モジュールが上に起動します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-155">When we press a configured button, it adds an upward force to the lunar module's rigid body component and causes the module to launch upwards.</span></span> <span data-ttu-id="c64fd-156">屋内にいる場合は、月着陸船が天井メッシュに当たってクラッシュする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c64fd-156">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="c64fd-157">雲の高低がある領域にいる場合、旧暦モジュールはスペースを無制限に飛びます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-157">If you are in an area with high ceilings or no ceilings, the lunar module will fly into space indefinitely.</span></span>

    ![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

6. <span data-ttu-id="c64fd-159">月着陸船が正常に上に向かって飛行するように [推進力] を調整します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-159">Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="c64fd-160">0\.01 の値を試してください。</span><span class="sxs-lookup"><span data-stu-id="c64fd-160">Try a value of 0.01.</span></span> <span data-ttu-id="c64fd-161">[Rb] フィールドは空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="c64fd-161">Leave the "Rb" field blank.</span></span> <span data-ttu-id="c64fd-162">Rb は固定の本体を表し、このフィールドは実行時に自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-162">Rb stands for Rigid body and this field will be automatically populated during runtime.</span></span>

    ![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="c64fd-164">旧暦モジュールパーツの概要</span><span class="sxs-lookup"><span data-stu-id="c64fd-164">Lunar Module Parts overview</span></span>

<span data-ttu-id="c64fd-165">旧暦モジュールパーツの親オブジェクトは、ユーザーが操作するオブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="c64fd-165">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="c64fd-166">シーンがかっこで囲まれた Game オブジェクト名は、次の一覧に示されています。</span><span class="sxs-lookup"><span data-stu-id="c64fd-166">The Game object names with scene labeled names in parentheses, are provided in the list below:</span></span>

- <span data-ttu-id="c64fd-167">Backpack (エネルギーセル)</span><span class="sxs-lookup"><span data-stu-id="c64fd-167">Backpack (Energy Cell)</span></span>
- <span data-ttu-id="c64fd-168">GasTank (燃料タンク)</span><span class="sxs-lookup"><span data-stu-id="c64fd-168">GasTank (Fuel Tank)</span></span>
- <span data-ttu-id="c64fd-169">TopLeftBody (探査車格納庫)</span><span class="sxs-lookup"><span data-stu-id="c64fd-169">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="c64fd-170">Nose (ドッキング ポータル)</span><span class="sxs-lookup"><span data-stu-id="c64fd-170">Nose (Docking Portal)</span></span>
- <span data-ttu-id="c64fd-171">LeftTwirler (外部センサー)</span><span class="sxs-lookup"><span data-stu-id="c64fd-171">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="c64fd-172">レッスン4で説明されているように、これらの各オブジェクトには操作ハンドラーがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c64fd-172">Notice that each of these objects has a manipulation handler, as explained in Lesson 4.</span></span> <span data-ttu-id="c64fd-173">この機能を使用すると、ユーザーはオブジェクトを取得して操作できます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-173">This feature enables users to grab and manipulate the object.</span></span> <span data-ttu-id="c64fd-174">また、設定の2つのきき操作の種類が移動と回転に設定されていることにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="c64fd-174">Also note that the setting, Two Handed Manipulation Type, is set to Move and Rotate.</span></span> <span data-ttu-id="c64fd-175">このオプションは、オブジェクトの移動だけを許可し、アセンブリアプリケーションに必要な機能であるサイズを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="c64fd-175">This option only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="c64fd-176">さらに、モジュールパーツを直接やり取りするためだけに、遠くの操作はオフになっています。</span><span class="sxs-lookup"><span data-stu-id="c64fd-176">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="c64fd-178">部分アセンブリデモスクリプト (上図参照) は、ユーザーがユーザーによってユーザーが旧暦モジュールに配置するオブジェクトを管理するスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="c64fd-178">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span>

<span data-ttu-id="c64fd-179">フィールドを配置するオブジェクトは、上の図に示すように選択されている変換です。これは、接続先のオブジェクトに関連付けられている backpack/燃料タンクです。</span><span class="sxs-lookup"><span data-stu-id="c64fd-179">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span>

<span data-ttu-id="c64fd-180">近距離距離と遠く距離の設定によって、どのパーツがどこに配置されているか、または解放できるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="c64fd-180">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="c64fd-181">たとえば、backpack/燃料タンクは、位置に合わせる前に、旧暦モジュールから離れた0.1 単位である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c64fd-181">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="c64fd-182">[遠くの距離] 設定では、オブジェクトが旧暦モジュールからデタッチできるようになる位置が設定されます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-182">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="c64fd-183">この場合、ユーザーの手は Backpack/燃料タンクをつかみ、再度はめ込まれないように取り外すには月着陸船から 0.2 ユニット離れた場所に引く必要があります。</span><span class="sxs-lookup"><span data-stu-id="c64fd-183">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="c64fd-184">ツールヒントオブジェクトはシーンのツールヒントラベルです。</span><span class="sxs-lookup"><span data-stu-id="c64fd-184">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="c64fd-185">オブジェクトが所定の位置にスナップされると、ラベルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="c64fd-185">When the objects are snapped in place, the label is disabled.</span></span>

<span data-ttu-id="c64fd-186">オーディオソースが自動的にグラブされます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-186">The Audio Source is automatically grabbed.</span></span>

### <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="c64fd-187">配置ヒントボタンの構成</span><span class="sxs-lookup"><span data-stu-id="c64fd-187">Configuring the Placement Hints button</span></span>

<span data-ttu-id="c64fd-188">[レッスン 2](mrlearning-base-ch2.md)では、項目の色を変更したり、プッシュ時に音を鳴らすようにしたりするためのボタンを配置および構成する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="c64fd-188">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when pushed.</span></span> <span data-ttu-id="c64fd-189">ここでは配置のヒントを切り替えるためのボタンを構成するため、これらの原則を引き続き使用します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-189">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span>

<span data-ttu-id="c64fd-190">目標は、ユーザーが配置ヒントボタンを押すたびに、半透明の配置ヒントが表示されるように、ボタンを構成することです。</span><span class="sxs-lookup"><span data-stu-id="c64fd-190">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span>

1. <span data-ttu-id="c64fd-191">基本のシーン階層で配置ヒントオブジェクトが選択されている間、[インスペクター] パネルの空のランタイムのみのスロットに旧暦モジュールを移動します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-191">Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span>

    ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. <span data-ttu-id="c64fd-193">[関数なし] ドロップダウンリストをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c64fd-193">Click the No Function dropdown list.</span></span> <span data-ttu-id="c64fd-194">TogglePlacementHints に移動し、そのメニューの下にある ToggleGameObjects () を選択します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-194">Go down to TogglePlacementHints and select ToggleGameObjects () under that menu.</span></span> <span data-ttu-id="c64fd-195">ToggleGameObjects () は、ボタンが押されるたびに表示または非表示になるように配置ヒントのオンとオフを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-195">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>

    ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a><span data-ttu-id="c64fd-197">[リセット] ボタンの構成</span><span class="sxs-lookup"><span data-stu-id="c64fd-197">Configuring the Reset button</span></span>

<span data-ttu-id="c64fd-198">ユーザーが誤ってオブジェクトを破棄したり、エクスペリエンスをリセットしたりする場合があります。</span><span class="sxs-lookup"><span data-stu-id="c64fd-198">There will be situations where the user makes a mistake, accidentally throws the object away or just wants to reset the experience.</span></span> <span data-ttu-id="c64fd-199">[リセット] ボタンをクリックすると、エクスペリエンスを再起動する機能が追加されます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-199">The Reset button adds the ability to restart the experience.</span></span>

1. <span data-ttu-id="c64fd-200">[リセット] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-200">Select the Reset button.</span></span> <span data-ttu-id="c64fd-201">基本シーンでは、ResetRoundButton という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-201">In the base scene, it’s named ResetRoundButton.</span></span>

2. <span data-ttu-id="c64fd-202">[インスペクター] パネルの [Button] の下にある空のスロットに、[基本のシーン] 階層から旧暦モジュールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c64fd-202">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed on the inspector panel.</span></span>

    ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. <span data-ttu-id="c64fd-204">[関数なし] ドロップダウンメニューを選択し、LaunchLunarModule の上にマウスポインターを移動し、[resetModule ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-204">Select the No Function dropdown menu and hover over LaunchLunarModule, then select resetModule ().</span></span>

    ![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="c64fd-206">既定では、BroadcastMessage は ResetPlacement に構成されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c64fd-206">Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="c64fd-207">これにより、RocketLauncher_Tutorial のすべての子オブジェクトに対して ResetPlacement という名前のメッセージがブロードキャストされます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-207">This broadcasts a message named ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="c64fd-208">ResetPlacement () のメソッドを持つオブジェクトは、位置をリセットすることによって、そのメッセージに応答します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-208">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span>

### <a name="configuring-the-launch-button"></a><span data-ttu-id="c64fd-209">[起動] ボタンの構成</span><span class="sxs-lookup"><span data-stu-id="c64fd-209">Configuring the Launch button</span></span>

<span data-ttu-id="c64fd-210">ここでは、[起動] ボタンを構成する方法について説明します。このボタンを使用すると、ユーザーはボタンをクリックして、スペースで旧暦モジュールを起動することができます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-210">This section explains how to configure the Launch button, which permits the user to press the button and launch the lunar module into space.</span></span>

1. <span data-ttu-id="c64fd-211">[起動] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-211">Select the Launch button.</span></span> <span data-ttu-id="c64fd-212">基本シーンでは、LaunchRoundButton と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-212">In the base scene, it’s called LaunchRoundButton.</span></span> <span data-ttu-id="c64fd-213">[インスペクター] パネルの [タッチエンド] の下にある空のスロットに、旧暦モジュールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c64fd-213">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>

    ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. <span data-ttu-id="c64fd-215">[関数なし] ドロップダウンメニューを選択し、LaunchLunarModule の上にマウスポインターを移動し、[StopThruster ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-215">Select the No Function dropdown menu and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="c64fd-216">これにより、ユーザーが旧暦モジュールに与える推力の量が制御されます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-216">This controls how much thrust the user wants to give to the lunar module.</span></span>

    ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. <span data-ttu-id="c64fd-218">[インスペクター] パネルの [Button] の下にある空のスロットに、[基本のシーン] 階層から旧暦モジュールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c64fd-218">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed in the inspector panel.</span></span>

4. <span data-ttu-id="c64fd-219">[関数なし] ドロップダウンメニューをクリックし、[LaunchLunarModule] をクリックして、[StartThruster ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-219">Click the No function dropdown menu and then on LaunchLunarModule and select StartThruster ().</span></span>

    ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. <span data-ttu-id="c64fd-221">音楽がロケットの撮影時に再生されるように、旧暦モジュールに音楽を追加します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-221">Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="c64fd-222">これを行うには、[] ボタンが押された状態の次の空のスロット () に旧暦モジュールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c64fd-222">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

6. <span data-ttu-id="c64fd-223">[関数なし] ドロップダウンメニューを選択し、AudioSource の上にマウスポインターを移動して、[PlayOneShot (Audiosource)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-223">Select the No Function dropdown menu, hover over AudioSource and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="c64fd-224">MRTK に含まれているさまざまな音から自由に選択してください。</span><span class="sxs-lookup"><span data-stu-id="c64fd-224">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="c64fd-225">この例では、"MRTK_Gem" を使用します。</span><span class="sxs-lookup"><span data-stu-id="c64fd-225">In this example, we'll use "MRTK_Gem."</span></span>

    ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

### <a name="congratulations"></a><span data-ttu-id="c64fd-227">結論</span><span class="sxs-lookup"><span data-stu-id="c64fd-227">Congratulations</span></span>

<span data-ttu-id="c64fd-228">このアプリケーションは完全に構成されています。</span><span class="sxs-lookup"><span data-stu-id="c64fd-228">You have fully configured this application.</span></span> <span data-ttu-id="c64fd-229">ここで、[再生] をクリックすると、旧暦モジュールを完全に組み立て、ヒントを切り替えることができます。また、旧暦モジュールを起動してリセットし、再起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="c64fd-229">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module and reset it to start again.</span></span>
