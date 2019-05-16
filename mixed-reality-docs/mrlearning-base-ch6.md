---
title: MR Learning ベース モジュール - 旧暦モジュール アセンブリ サンプル エクスペリエンス
description: このレッスンでは、一意のサンプルのエクスペリエンスを作成する前のレッスンから学習した複数の概念を結合します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 複合現実、unity、チュートリアル、hololens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730845"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a><span data-ttu-id="eb7ac-104">MR Learning ベース モジュール - 旧暦モジュール アセンブリ サンプル エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="eb7ac-104">MR Learning Base Module - Lunar Module Assembly Sample Experience</span></span>

<span data-ttu-id="eb7ac-105">このレッスンでは、一意のサンプルのエクスペリエンスを作成する前のレッスンから学習した複数の概念を結合します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-105">In this lesson, we will combine multiple concepts learned from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="eb7ac-106">ユーザーの必要があります旧暦モジュールのパーツを取得する追跡対象の手を使用して、旧暦モジュールをアセンブルしようとしています。 これにより旧暦モジュール アセンブリのアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-106">We will create a lunar module assembly application whereby a user will need to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="eb7ac-107">Pressable ボタンを使用して、経験をリセットする領域に、旧暦モジュールを起動して、配置ヒントを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-107">We will use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="eb7ac-108">今後のチュートリアルでは、いく予定に強力なマルチ ユーザーのユース ケースの空間配置 Azure 空間アンカーを利用しているを含む、このエクスペリエンスに基づいています。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-108">In future tutorials, we will continue to build upon this experience, including powerful multi-user use-cases that leverages Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="eb7ac-109">目標</span><span class="sxs-lookup"><span data-stu-id="eb7ac-109">Objectives</span></span>

- <span data-ttu-id="eb7ac-110">一意のエクスペリエンスを作成する前のレッスンから複数の概念を組み合わせる</span><span class="sxs-lookup"><span data-stu-id="eb7ac-110">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="eb7ac-111">オブジェクトを切り替える方法について説明します</span><span class="sxs-lookup"><span data-stu-id="eb7ac-111">Learn how to toggle objects</span></span>
- <span data-ttu-id="eb7ac-112">Pressable ボタンを使用して複雑なイベントをトリガー</span><span class="sxs-lookup"><span data-stu-id="eb7ac-112">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="eb7ac-113">Rigidbody 物理学や強制を使用して、</span><span class="sxs-lookup"><span data-stu-id="eb7ac-113">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="eb7ac-114">ツール ヒントの使用法を調べる</span><span class="sxs-lookup"><span data-stu-id="eb7ac-114">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="eb7ac-115">手順</span><span class="sxs-lookup"><span data-stu-id="eb7ac-115">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="eb7ac-116">構成</span><span class="sxs-lookup"><span data-stu-id="eb7ac-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="eb7ac-117">この章では、私たちは、サンプルのエクスペリエンスを作成するために必要なさまざまなコンポーネントに導入されます。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-117">In this chapter, we will be introduced to the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="eb7ac-118">旧暦モジュール アセンブリのプレハブは、基本シーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-118">Add the lunar module assembly prefab to your Base Scene.</span></span> <span data-ttu-id="eb7ac-119">これを行うには、[プロジェクト] タブに、"Rocket Launcher_Tutorial"を検索します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-119">To do this, in your project tab, search for "Rocket Launcher_Tutorial."</span></span> <span data-ttu-id="eb7ac-120">アセットのプレハブを検索することも可能性があります。 > BaseModuleAssets > プレハブします。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-120">You may also find the prefab in Assets>BaseModuleAssets>Prefabs.</span></span> <span data-ttu-id="eb7ac-121">可能性があります。 2 つのロケット ランチャー プレハブを参照してください。名前「チュートリアル」のいずれかと別の名前を「完了します。」</span><span class="sxs-lookup"><span data-stu-id="eb7ac-121">You may see two rocket launcher prefabs; one with the name "tutorial" and another with the name "complete."</span></span> <span data-ttu-id="eb7ac-122">"Rocket Launcher_Tutorial"プレハブは、基本シーンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-122">Drag the "Rocket Launcher_Tutorial" prefab to your Base Scene.</span></span> <span data-ttu-id="eb7ac-123">自由に、シーンのプレハブの配置を配置できます。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-123">Feel free to position the placement of the prefab in your scene.</span></span>
   <span data-ttu-id="eb7ac-124">注:"Rocket Launcher_Complete"プレハブは、完了した、起動、参照用ツールです。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-124">Note: The "Rocket Launcher_Complete" prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 第 1 章 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="eb7ac-126">階層内の"Rocket Launcher_Tutorial"ゲーム オブジェクトを展開し、さらに「旧暦モジュール」オブジェクトを拡張する場合は、「x 線」と呼ばれるマテリアルをいくつかの子オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-126">If you expand the "Rocket Launcher_Tutorial" game object in your hierarchy, and further expand the "Lunar Module" object, you will see several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="eb7ac-127">「X 線画像」マテリアルは、ユーザーの配置のヒントとして使用する少し半透明の色になります。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-127">The "x-ray" material allows for a slightly translucent color which we will use as placement hints for the user.</span></span> 

<span data-ttu-id="eb7ac-128">![Lesson6 第 1 章 Noteaim](images/Lesson6_Chapter1_noteaim.PNG)は次の図に示すように、対話するユーザーが移動する旧暦モジュールに 5 つの部分があります。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user is going to interact with, as shown in the image below:</span></span>

1.  <span data-ttu-id="eb7ac-129">Rover エンクロージャ</span><span class="sxs-lookup"><span data-stu-id="eb7ac-129">The Rover Enclosure</span></span>
2.  <span data-ttu-id="eb7ac-130">タンク燃料</span><span class="sxs-lookup"><span data-stu-id="eb7ac-130">The Fuel Tank</span></span>
3.  <span data-ttu-id="eb7ac-131">エネルギー セル</span><span class="sxs-lookup"><span data-stu-id="eb7ac-131">The Energy Cell</span></span>
4.  <span data-ttu-id="eb7ac-132">ドッキング ポータル</span><span class="sxs-lookup"><span data-stu-id="eb7ac-132">The Docking Portal</span></span> 
5.  <span data-ttu-id="eb7ac-133">外部センサー</span><span class="sxs-lookup"><span data-stu-id="eb7ac-133">The External sensor</span></span>

![Lesson6 第 1 章 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="eb7ac-135">注:シーン内のオブジェクトの名前には、基本のシーンの階層構造で表示されるゲーム オブジェクト名は対応していません。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-135">Note: The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="eb7ac-136">手順 2:オーディオのソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-136">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="eb7ac-137">基本のシーンの階層構造が選択されているかどうかを確認し、"コンポーネントの追加 をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-137">Make sure the lunar module is selected in your base scene hierarchy and click "Add Component."</span></span> <span data-ttu-id="eb7ac-138">「オーディオ ソース」を検索し、オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-138">Search for "Audio Source" and add it to the object.</span></span> <span data-ttu-id="eb7ac-139">空白のままに今のところです。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-139">Leave it blank for now.</span></span> <span data-ttu-id="eb7ac-140">後で起動したサウンドを再生するのにこれを使用します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-140">We will use this to play the launching sound later.</span></span>
 <span data-ttu-id="eb7ac-141">![Lesson6 第 1 章 Step2im](images/Lesson6_Chapter1_step2im.PNG)手順 3。"切り替えの配置ヒントの"スクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) Step 3: Add the script "toggle placement hints."</span></span> <span data-ttu-id="eb7ac-142">「コンポーネントの追加」と「切り替え配置ヒント」を検索 をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-142">Click "Add Component" and search for "Toggle Placement Hints."</span></span> <span data-ttu-id="eb7ac-143">これは、オンとオフは、前に説明した、半透明のヒント (x 線画像資料オブジェクト) を有効にするカスタム スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-143">This is a custom script that allows you to turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span> 
<span data-ttu-id="eb7ac-144">![Lesson6 第 1 章 Step3im](images/Lesson6_Chapter1_step3im.PNG)手順 4。5 つのオブジェクトがあるため、ゲーム オブジェクト配列のサイズの「5」で入力します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) Step 4: Since we have 5 objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="eb7ac-145">5 つの新しい要素を含めるを表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-145">Then you should see 5 new elements appear.</span></span> 

![Lesson6 第 1 章 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="eb7ac-147">半透明オブジェクトの各を"None (ゲーム オブジェクト) です"というボックスにドラッグします</span><span class="sxs-lookup"><span data-stu-id="eb7ac-147">Drag each of the translucent objects into the boxes that say "None (Game Object)."</span></span> <span data-ttu-id="eb7ac-148">基本シーンで旧暦モジュールから、次のオブジェクトをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-148">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="eb7ac-149">• Backpack</span><span class="sxs-lookup"><span data-stu-id="eb7ac-149">•   Backpack</span></span>

<span data-ttu-id="eb7ac-150">•   GasTank</span><span class="sxs-lookup"><span data-stu-id="eb7ac-150">•   GasTank</span></span>

<span data-ttu-id="eb7ac-151">• Topleftbody</span><span class="sxs-lookup"><span data-stu-id="eb7ac-151">•   Topleftbody</span></span>

<span data-ttu-id="eb7ac-152">• 鼻</span><span class="sxs-lookup"><span data-stu-id="eb7ac-152">•   Nose</span></span>

<span data-ttu-id="eb7ac-153">• LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="eb7ac-153">•   LeftTwirler</span></span>

 ![Lesson6 第 1 章 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="eb7ac-155">「配置のヒントを切り替え」スクリプトが構成されているようになりました。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-155">Now the "toggle placement hints" script is configured.</span></span> <span data-ttu-id="eb7ac-156">これにより、ヒントを有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-156">This will allow us to turn the hints on and off.</span></span>

<span data-ttu-id="eb7ac-157">手順 5:「旧暦モジュールの起動」スクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-157">Step 5: Add the "launch lunar module" script.</span></span> <span data-ttu-id="eb7ac-158">「コンポーネントの追加」ボタンをクリックして、「起動旧暦モジュール」を検索し、それを選択します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-158">Click the "Add Component" button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="eb7ac-159">このスクリプトを起動するにはなります。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-159">This script will be responsible for launching the lunar module.</span></span> <span data-ttu-id="eb7ac-160">構成されているボタン キーを押すと、ときに旧暦モジュールの rigidbody コンポーネントに上向きの力を追加し、モジュール上で起動すると、します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-160">When we press a configured button, it will add an upward force to the lunar module's rigid body component and will cause the module to launch upwards.</span></span> <span data-ttu-id="eb7ac-161">室内にいる場合、ceiling メッシュに対してがクラッシュします。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-161">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="eb7ac-162">ただし、屋外場合は、その操縦領域を無制限にします。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-162">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![Lesson6 第 1 章 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="eb7ac-164">手順 6:正常に飛んでように、スロットルを調整します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-164">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="eb7ac-165">0.01 の値をお試しください。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-165">Try a value of 0.01.</span></span> <span data-ttu-id="eb7ac-166">"Rb"フィールドは空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-166">Leave the "Rb" field blank.</span></span> <span data-ttu-id="eb7ac-167">Rb の略剛体、および実行時にこのフィールドに自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-167">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![Lesson6 第 1 章 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="eb7ac-169">旧暦モジュールのパーツの概要</span><span class="sxs-lookup"><span data-stu-id="eb7ac-169">Lunar Module Parts Overview</span></span>
<span data-ttu-id="eb7ac-170">旧暦モジュールのパーツの親オブジェクトは、ユーザーが対話するオブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-170">The Lunar Module parts parent object is the collection of the objects that the user will interact with.</span></span> <span data-ttu-id="eb7ac-171">下の一覧では、(ラベル名を括弧でシーン) をゲーム オブジェクト名が用意されています。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-171">The game object names (with scene labeled names in paretheses) are provided in the list below:</span></span>

- <span data-ttu-id="eb7ac-172">Backpack (燃料タンク)</span><span class="sxs-lookup"><span data-stu-id="eb7ac-172">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="eb7ac-173">GasTank (エネルギー セル)</span><span class="sxs-lookup"><span data-stu-id="eb7ac-173">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="eb7ac-174">TopLeftBody (Rover エンクロージャ)</span><span class="sxs-lookup"><span data-stu-id="eb7ac-174">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="eb7ac-175">鼻 (ドッキング ポータル)</span><span class="sxs-lookup"><span data-stu-id="eb7ac-175">Nose (Docking Portal)</span></span>
- <span data-ttu-id="eb7ac-176">LeftTwirler (外部センサー)</span><span class="sxs-lookup"><span data-stu-id="eb7ac-176">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="eb7ac-177">レッスン 4 で説明したように操作ハンドラー、これらの各オブジェクトに注意してください。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-177">Notice that each of these objects has the manipulation handler, as discussed in lesson 4.</span></span> <span data-ttu-id="eb7ac-178">操作ハンドラー、ユーザーが取得して、オブジェクトを操作できます。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-178">With the manipulation handler, users are able to grab and manipulate the object.</span></span> <span data-ttu-id="eb7ac-179">設定の「2 つの操作が渡される型」が「移動および回転します」に設定されているにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-179">Also note that the setting "two handed manipulation type" is set to "move and rotate."</span></span> <span data-ttu-id="eb7ac-180">これには、オブジェクトを移動し、そのサイズは、アセンブリ、アプリケーションの目的の機能は、変更するユーザーのみが許可します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-180">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="eb7ac-181">さらに、相手側の操作は、モジュールのパーツの直接の対話のみを許可するチェックではありません。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-181">In addition, far manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="eb7ac-183">一部のアセンブリ デモ スクリプト (上記参照) をユーザーに配置するオブジェクトを管理するスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-183">The part assembly demo script (shown above) is the scrip that manages the objects to be placed on to the lunar module by the user.</span></span> 

<span data-ttu-id="eb7ac-184">「オブジェクトを場所」フィールドは、オブジェクトに接続できることを使用 (n 上の図 backpack/燃料タンクの大文字と小文字) を選択したの変換です。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-184">The "Object To Place" field is the transform that is selected (n the case of the image above, the backpack/fuel tank) with the object that it can connect to.</span></span> 

<span data-ttu-id="eb7ac-185">"近く Distance"および「までの距離」設定は、近接性をパーツにスナップされますまたは解放を判断する責任を負います。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-185">The "Near Distance" and "Far Distance" settings are responsible for determining the proximity to which parts will snap in place or be released.</span></span> <span data-ttu-id="eb7ac-186">たとえば、backpack/燃料タンクが 0.1 単位に揃えるに旧暦モジュールから必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-186">For example, the backpack/fuel tank would need to be 0.1 units away from the lunar module to snap into place.</span></span> <span data-ttu-id="eb7ac-187">「までの距離」は、オブジェクトからデタッチする必要がある場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-187">The "Far Distance" sets the location where the object needs to be to detach from the lunar module.</span></span> <span data-ttu-id="eb7ac-188">この場合、ユーザーの手は backpack/燃料タンクを取得し、所定の位置に戻すスナップから削除してから、0.2 の単位をプルすること必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-188">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="eb7ac-189">「ツール ヒントのオブジェクト」は、シーンのツール ヒント ラベルです。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-189">The "Tool Tip Object" is the tool tip label in the scene.</span></span> <span data-ttu-id="eb7ac-190">オブジェクトは、インプレース基準としてスナップされますが、ラベルが無効になります。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-190">When the objects are snapped in place, the label will be disabled.</span></span> 

<span data-ttu-id="eb7ac-191">オーディオ ソースは自動的に取得します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-191">The Audio Source will be automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="eb7ac-192">配置のボタンをヒントします。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-192">Placement Hints Buttons</span></span>
<span data-ttu-id="eb7ac-193">[レッスン 2](mrlearning-base-ch2.md)、配置して、アイテムの色の変更などを行うまたはにプッシュされるときにサウンドを再生ボタンを構成する方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-193">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="eb7ac-194">これらの原則を使用して、配置ヒントを切り替えるボタンを構成しましたにいく予定です。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-194">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="eb7ac-195">目標では、半透明の配置のヒントの表示を切り替えるは、ユーザーは、配置ヒント ボタンを押すと、毎回ように、ボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-195">The goal is to configure our button so that every time the user presses the placement hint button, it will toggle visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="eb7ac-196">手順 1:基本のシーンの階層構造で、配置ヒント オブジェクトが選択されている間をインスペクターのパネルで「ランタイムのみ」の空のスロットに移動します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-196">Step 1: Move the Lunar Module to the empty "runtime only" slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="eb7ac-197">![Lesson6 第 3 章 Step1im](images/Lesson6_Chapter3_step1im.PNG)手順 2。これで書かれている場所、「機能はありません」ドロップダウン リストをクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the dropdown list where it says, "no function."</span></span> <span data-ttu-id="eb7ac-198">"TogglePlacementHints、"とそのメニューの下に移動「ToggleGameObjects ()」を選択します</span><span class="sxs-lookup"><span data-stu-id="eb7ac-198">Go down to "TogglePlacementHints," and under that menu select "ToggleGameObjects ()."</span></span> <span data-ttu-id="eb7ac-199">ToggleGameObjects() オフが切り替わります、配置ヒント オン/オフ ボタンが押されるたびに、表示または非表示が、ように。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-199">ToggleGameObjects() will toggle the placement hints on and off so that they are visible or invisible every time the button is pressed.</span></span>
 <span data-ttu-id="eb7ac-200">![Lesson6 第 3 章 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="eb7ac-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="eb7ac-201">[リセット] ボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-201">Configuring the Reset Button</span></span>

<span data-ttu-id="eb7ac-202">ユーザーが誤り、または誤ってがスローされます、オブジェクト、または単したいと rest 操作を行う場合があります。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-202">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to rest the experience.</span></span> <span data-ttu-id="eb7ac-203">[リセット] ボタンは、エクスペリエンスを再起動する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-203">The reset button will add the ability to restart the experience.</span></span> 

<span data-ttu-id="eb7ac-204">手順 1:[リセット] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-204">Step 1: Select the reset button.</span></span> <span data-ttu-id="eb7ac-205">基本のシーンでは、"ResetRoundButton"という名前します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-205">In the base scene, it’s named "ResetRoundButton."</span></span> 

<span data-ttu-id="eb7ac-206">手順 2:「ボタンが押された」の下の空のスロットに基本のシーンの階層をドラッグして、[inspector] パネル。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-206">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under "button pressed" the inspector panel.</span></span>
 <span data-ttu-id="eb7ac-207">![Lesson6 第 4 章 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="eb7ac-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="eb7ac-208">手順 3:「機能はありません」と書かれたドロップダウン メニューを選択して、"LaunchLunarModule"ポインターを合わせる</span><span class="sxs-lookup"><span data-stu-id="eb7ac-208">Step 3: Select the dropdown menu that says, "no function" and hover over "LaunchLunarModule."</span></span> <span data-ttu-id="eb7ac-209">「ResetModule ()」を選択するようになりました</span><span class="sxs-lookup"><span data-stu-id="eb7ac-209">Now select "resetModule ()."</span></span>

![Lesson6 第 4 章 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="eb7ac-211">注:既定で"GameObject.BroadcastMessage"は"ResetPlacement"に構成が表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-211">Note: You will notice that by default the "GameObject.BroadcastMessage" is configured to "ResetPlacement."</span></span> <span data-ttu-id="eb7ac-212">これにより、RocketLauncher_Tutorial のすべての子オブジェクトの"ResetPlacement"と呼ばれるメッセージをブロードキャストします。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-212">This will broadcast a message called "ResetPlacement" for every child object of RocketLauncher_Tutorial.</span></span> <span data-ttu-id="eb7ac-213">"ResetPlacement()"のメソッドを持つ任意のオブジェクトは、位置をリセットすることでそのメッセージに応答します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-213">Any object that has a method for "ResetPlacement()" will respond to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="eb7ac-214">起動します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-214">Launching the Lunar Module</span></span>
<span data-ttu-id="eb7ac-215">この章では、起動ボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-215">This chapter we will be configuring the launch button.</span></span> <span data-ttu-id="eb7ac-216">これにより、ボタンを押すし、領域を起動するユーザーが許可されます。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-216">This will permit the user to press the button and launch the Lunar Module into space.</span></span>

<span data-ttu-id="eb7ac-217">手順 1:起動ボタンを選択します (基本シーンでという名前が"LaunchRoundButton")。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-217">Step 1: Select the launch button (in the base scene it’s named "LaunchRoundButton").</span></span> <span data-ttu-id="eb7ac-218">インスペクター ウィンドウを「タッチ エンド」の下の空のスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-218">Drag the Lunar Module to the empty slot under "Touch End" in the inspector panel.</span></span>
 <span data-ttu-id="eb7ac-219">![Lesson6 第 5 章 Step1im](images/Lesson6_Chapter5_step1im.PNG)手順 2。「機能はありません。」と書かれたドロップダウン メニューを選択します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the dropdown menu that says, "no function."</span></span> <span data-ttu-id="eb7ac-220">"LaunchLunarModule"ポインターを合わせるし、「StopThruster ()」を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-220">Hover over "LaunchLunarModule" and select "StopThruster ()."</span></span> <span data-ttu-id="eb7ac-221">これは、スロットルが、ユーザーを付与する量を制御します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-221">This will control how much thrust the user wants to give to the Lunar Module.</span></span> 
 <span data-ttu-id="eb7ac-222">![Lesson6 第 5 章 Step2im](images/Lesson6_Chapter5_step2im.PNG)手順 3。"ButtonPressed()"の下には、空のスロットに旧暦モジュール (クリック数、保留、およびドラッグ) を追加します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) Step 3: Under "ButtonPressed()", add the Lunar Module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="eb7ac-223">手順 4:「機能はありません」と書かれたドロップダウン メニューをクリックし、"LaunchLunarModule"をポイントし、「StartThruster ()」を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-223">Step 4: Click the dropdown menu that says, "no function" and hover over "LaunchLunarModule" and select "StartThruster ()."</span></span> 
 <span data-ttu-id="eb7ac-224">![Lesson6 第 5 章 Step4im](images/Lesson6_Chapter5_step4im.PNG)手順 5。音楽が再生されますが、ロケット、ときにするために、音楽を追加します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) Step 5: Add music to the Lunar Module so that when the rocket takes off, the music will play.</span></span> <span data-ttu-id="eb7ac-225">これを行うには、"ボタン Pressed()"の下で [次へ] の空のスロットをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-225">To do this, drag the Lunar Module to the next empty slot under "Button Pressed()".</span></span>

<span data-ttu-id="eb7ac-226">手順 6:「機能はありません」と書かれたドロップダウン メニューを選択し、"AudioSource"をポイントし、"PlayOneShot (AudioClip)"を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-226">Step 6: Select the dropdown menu that says, "no function" and hover over "AudioSource" and select "PlayOneShot (AudioClip)."</span></span> <span data-ttu-id="eb7ac-227">自由に、さまざまな、MRTK に含まれているサウンドを探索できます。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-227">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="eb7ac-228">この例では、ここでは"MRTK_Gem"を使用するには</span><span class="sxs-lookup"><span data-stu-id="eb7ac-228">For this example, we are going to stick with "MRTK_Gem."</span></span>
 <span data-ttu-id="eb7ac-229">![Lesson6 第 5 章 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="eb7ac-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="eb7ac-230">おめでとうございます</span><span class="sxs-lookup"><span data-stu-id="eb7ac-230">Congratulations</span></span> 
<span data-ttu-id="eb7ac-231">このアプリケーションを構成した完全に!</span><span class="sxs-lookup"><span data-stu-id="eb7ac-231">You have fully configured this application!</span></span> <span data-ttu-id="eb7ac-232">ようになりましたプレイを押すと、完全、アセンブル、ヒントを切り替える、旧暦モジュールを起動して、再度実行するをリセットできます。</span><span class="sxs-lookup"><span data-stu-id="eb7ac-232">Now when you press play, you can fully assemble the Lunar Module, toggle hints, launch the Lunar Module, and reset it to do it all over again.</span></span>
