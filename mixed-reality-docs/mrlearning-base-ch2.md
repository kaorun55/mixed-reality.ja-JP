---
title: 入門チュートリアル-3. ユーザーインターフェイスを作成し、Mixed Reality Toolkit を構成する
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: f0a54bb591479dbe8ffa719cb5e6a9d846f67f9e
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539740"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="2a311-105">3. ユーザーインターフェイスを作成し、Mixed Reality Toolkit を構成する</span><span class="sxs-lookup"><span data-stu-id="2a311-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>

<span data-ttu-id="2a311-106">前のレッスンでは、HoloLens 2 の最初のアプリケーションを開始することで、Mixed Reality Toolkit (MRTK) が提供する必要のある機能について説明しました。</span><span class="sxs-lookup"><span data-stu-id="2a311-106">In the previous lesson, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="2a311-107">次のレッスンでは、UI テキストパネルと共にボタンを作成および整理し、既定の対話機能 (タッチ) を使用して各ボタンを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a311-107">In this next lesson you'll learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="2a311-108">また、オブジェクトのサイズ、音、色の変更など、単純なアクションや効果の追加も調査します。</span><span class="sxs-lookup"><span data-stu-id="2a311-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="2a311-109">このモジュールでは、[空間マッピング](spatial-mapping.md)メッシュの視覚化を無効にしてから、MRTK プロファイルの変更に関する基本的な概念を紹介します。</span><span class="sxs-lookup"><span data-stu-id="2a311-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="2a311-110">目標</span><span class="sxs-lookup"><span data-stu-id="2a311-110">Objectives</span></span>

* <span data-ttu-id="2a311-111">Mixed Reality ツールキット プロファイルをカスタマイズおよび構成する</span><span class="sxs-lookup"><span data-stu-id="2a311-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="2a311-112">UI 要素とボタンを使用したホログラムとの対話</span><span class="sxs-lookup"><span data-stu-id="2a311-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="2a311-113">基本的な手の追跡の入力と操作</span><span class="sxs-lookup"><span data-stu-id="2a311-113">Basic hand-tracking input and interactions</span></span>

## <a name="instructions"></a><span data-ttu-id="2a311-114">手順</span><span class="sxs-lookup"><span data-stu-id="2a311-114">Instructions</span></span>

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="2a311-115">Mixed Reality Toolkit プロファイルを構成する方法 (空間認識表示オプションの変更)</span><span class="sxs-lookup"><span data-stu-id="2a311-115">How to Configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>

<span data-ttu-id="2a311-116">このセクションでは、空間認識メッシュの表示オプションを調整して、既定の MRTK プロファイルをカスタマイズおよび構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a311-116">In this section, you'll learn how to customize and configure the default MRTK profiles by adjusting the display option of the spatial awareness mesh.</span></span> <span data-ttu-id="2a311-117">MRTK プロファイル内の設定または値を調整するには、次の同じ原則に従うことができます。</span><span class="sxs-lookup"><span data-stu-id="2a311-117">You may follow these same principles for adjusting any settings or values in the MRTK profiles.</span></span>

1. <span data-ttu-id="2a311-118">BaseScene 階層から Mixed-Reality Toolkit (MRTK) を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a311-118">Select Mixed-Reality Toolkit (MRTK) from the BaseScene hierarchy.</span></span> <span data-ttu-id="2a311-119">[インスペクター] パネルで、次の図に示すように、Mixed Reality Toolkit スクリプトを探し、アクティブなプロファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2a311-119">In the inspector panel, look for the Mixed Reality Toolkit Script and select the active profile as shown in the figure below.</span></span> <span data-ttu-id="2a311-120">ダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="2a311-120">Double-click to open it.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step1.png)

    >[!NOTE]
    ><span data-ttu-id="2a311-122">既定では、MRTK プロファイルは編集できません。</span><span class="sxs-lookup"><span data-stu-id="2a311-122">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="2a311-123">これらは既定のプロファイルテンプレートで、コピーしてカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="2a311-123">These are default profile templates that you can copy and customize.</span></span> <span data-ttu-id="2a311-124">カスタマイズとプロファイルには、いくつかのレイヤーがあります。</span><span class="sxs-lookup"><span data-stu-id="2a311-124">There are several layers of customization and profiles.</span></span> <span data-ttu-id="2a311-125">そのため、1つまたは複数の設定を構成するときに、いくつかのプロファイルをコピーしてカスタマイズするのは標準的な方法です。</span><span class="sxs-lookup"><span data-stu-id="2a311-125">So, it is standard practice to copy and customize several profiles when configuring one or more settings.</span></span>
    >
    ><span data-ttu-id="2a311-126">MRTK プロファイルとそのアーキテクチャの詳細については、 [Mrtk のドキュメント](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a311-126">To discover more about MRTK profiles and their architecture, visit the [MRTK documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>).</span></span>

2. <span data-ttu-id="2a311-127">既定のプロファイルのコピーを作成し、それをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="2a311-127">Create a copy of the default profile to customize it.</span></span> <span data-ttu-id="2a311-128">**[コピー & カスタマイズ]** をクリックして開始します。</span><span class="sxs-lookup"><span data-stu-id="2a311-128">Start by clicking **Copy & Customize**.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2a.png)

    <span data-ttu-id="2a311-130">これにより、[*複製プロファイル*] ポップアップウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="2a311-130">This will open the *Clone Profile* popup window.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2b.png)

    <span data-ttu-id="2a311-132">**[複製]** をクリックして、MRTK プロファイルのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="2a311-132">Click **Clone** to create a copy of the MRTK profile.</span></span> <span data-ttu-id="2a311-133">MRTK プロファイルの独自のコピーを使用して、このプロファイルの設定をカスタマイズできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="2a311-133">With your own copy of the MRTK profile, you now have the ability to customize any settings in this profile.</span></span> <span data-ttu-id="2a311-134">また、後の手順で説明するように、このプロファイルの下に入れ子になっている追加のプロファイルについても、[コピーとカスタマイズ] ステップを繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a311-134">You will also need to repeat the copy and customize step for any additional profiles nested under this profile as described in the subsequent steps.</span></span>

3. <span data-ttu-id="2a311-135">空間認識メッシュの可視性を無効にします。</span><span class="sxs-lookup"><span data-stu-id="2a311-135">Disable the visibility of the spatial awareness mesh.</span></span> <span data-ttu-id="2a311-136">これを行うには、次の図に示すように、空間認識システムの設定を見つけます。</span><span class="sxs-lookup"><span data-stu-id="2a311-136">To do this, find Spatial Awareness system settings as shown in the image below.</span></span> <span data-ttu-id="2a311-137">**[空間認識システムを有効にする]** オプションがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2a311-137">Make sure the **Enable Spatial Awareness System** option is checked.</span></span> <span data-ttu-id="2a311-138">空間認識システム プロファイルの右側にある **複製** ボタンをクリックして、既定のプロファイルをカスタマイズ可能なコピーに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2a311-138">Click the **Clone** button to the right of the Spatial Awareness System Profile to replace the default profile with a customizable copy.</span></span> <span data-ttu-id="2a311-139">次の2番目の図に示すように、表示されたポップアップウィンドウで、 **[複製]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a311-139">In the pop-up window that appears, press the **Clone** button, as shown in the second image below.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3a.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3b.png)

4. <span data-ttu-id="2a311-142">既定の Mixed Reality 空間メッシュ オブザーバーのカスタム コピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="2a311-142">Create a custom copy of the Default Mixed Reality Spatial Mesh Observer.</span></span> <span data-ttu-id="2a311-143">[Windows Mixed Reality 空間メッシュオブザーバー] の横にある下矢印をクリックすると、追加のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a311-143">Click the down arrow next to Windows Mixed Reality Spatial Mesh Observer to see additional options.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4a.png)

    <span data-ttu-id="2a311-145">これらのオプションでは、既定の Mixed Reality 空間メッシュオブザーバー (編集不可) がグレーで表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a311-145">In these options, you will see the Default Mixed Reality Spatial Mesh Observer that is greyed-out (not editable).</span></span> <span data-ttu-id="2a311-146">この既定のプロファイルをカスタマイズ可能なコピーに置き換えて編集できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a311-146">You must replace this default profile with a customizable copy so you can edit it.</span></span> <span data-ttu-id="2a311-147">前に行ったように、 **[複製]** ボタンをクリックし、表示されたポップアップウィンドウで、下の2番目の図に示すように、 **[複製]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a311-147">As you did earlier, click the **Clone** button and then, in the pop-up window that appears, press the **Clone** button, as shown in the second image below.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4b.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4c.png)

5. <span data-ttu-id="2a311-150">次に、表示オプションの設定を [オクルージョン] が表示されるように調整します。</span><span class="sxs-lookup"><span data-stu-id="2a311-150">Next, you will adjust the settings for the display option to say “occlusion.”</span></span> <span data-ttu-id="2a311-151">これにより、空間マッピングメッシュは非表示になりますが、空間マッピングメッシュの背後にあるゲームオブジェクトは、遮蔽とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2a311-151">This makes the spatial mapping mesh invisible, but still hides game objects behind the spatial mapping mesh, also known as occlusion.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step5.png)

    >[!NOTE]
    ><span data-ttu-id="2a311-153">注: 空間マッピングメッシュは表示されていませんが、まだ存在しているので、操作できます。</span><span class="sxs-lookup"><span data-stu-id="2a311-153">Note: While the spatial mapping mesh is not visible, it is still present and you can interact with it.</span></span> <span data-ttu-id="2a311-154">空間マッピングメッシュの背後にあるホログラム (表示されているウォールの背後にあるホログラムなど) は、遮蔽の設定により表示されません。</span><span class="sxs-lookup"><span data-stu-id="2a311-154">Any holograms behind the spatial mapping mesh, such as a hologram behind your visible wall, will not be visible because of the occlusion setting.</span></span>

<span data-ttu-id="2a311-155">これで終了です。</span><span class="sxs-lookup"><span data-stu-id="2a311-155">Congratulations!</span></span> <span data-ttu-id="2a311-156">ここまで、MRTK プロファイル内の設定を変更する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="2a311-156">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="2a311-157">見てわかるように、MRTK の設定を変更するには、既定のプロファイルのコピーを作成して編集できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a311-157">As you can see, in order to modify MRTK settings you need to create copies of the default profiles so that you can edit them.</span></span> <span data-ttu-id="2a311-158">新しい設定でプロファイルを作成する場合、または既定のプロファイルを参照する場合は、既定のプロファイル (編集不可) が常に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a311-158">You will always have the default profiles, which are not editable, to go back to if you wanted to create a profile with new settings or you can refer back to the default profiles.</span></span> <span data-ttu-id="2a311-159">調整できる設定には多くのものがあります。</span><span class="sxs-lookup"><span data-stu-id="2a311-159">There are numerous settings that you can adjust.</span></span> <span data-ttu-id="2a311-160">MRTK プロファイル設定の完全な参照については、MRTK のドキュメントを参照してください: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)</span><span class="sxs-lookup"><span data-stu-id="2a311-160">For full reference to MRTK profile settings, refer to the MRTK documentation here: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)</span></span>

### <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="2a311-161">手の追跡のジェスチャと操作可能なボタン</span><span class="sxs-lookup"><span data-stu-id="2a311-161">Hand Tracking Gestures and Interactable buttons</span></span>

<span data-ttu-id="2a311-162">このセクションでは、ハンドトラッキングを使用して pressable ボタンを押す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a311-162">In this section, you will learn how to use hand tracking to press a pressable button.</span></span>

1. <span data-ttu-id="2a311-163">Projects フォルダーから Assets を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a311-163">Select Assets from the projects folder.</span></span>

2. <span data-ttu-id="2a311-164">検索バーに「PressableButtonHoloLens2」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2a311-164">Type "PressableButtonHoloLens2" in the search bar.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step2.png)

3. <span data-ttu-id="2a311-166">"PressableButtonHoloLens2" という名前の prefab (青いボックスで表されます) を階層にドラッグし、position 値を x = 0、y = 0 および z = 0.2 に設定して、ボタンがカメラの前にあるように設定します。</span><span class="sxs-lookup"><span data-stu-id="2a311-166">Drag the prefab (represented by a blue box) named "PressableButtonHoloLens2" into your hierarchy and set set the position values to x = 0, y = 0 and z = 0.2 so the button is in front of the camera.</span></span> <span data-ttu-id="2a311-167">(カメラは元の位置に配置されています)。</span><span class="sxs-lookup"><span data-stu-id="2a311-167">(The camera is positioned at origin).</span></span>

    >[!NOTE]
    ><span data-ttu-id="2a311-168">"TMP Essentials をインポートしています" というメッセージが表示された場合は、この時点でインポートします。</span><span class="sxs-lookup"><span data-stu-id="2a311-168">If you get a message about “importing TMP Essentials”, import it at this time.</span></span> <span data-ttu-id="2a311-169">TMP Essentials がプロジェクトの一部ではない場合は、TMP Essentials をインポートした後にこの手順を繰り返す必要がある場合があります。それ以外の場合は、ボタンテキストが表示されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="2a311-169">If TMP Essentials was not already part of your project, you might need to repeat this step after importing TMP Essentials, otherwise button text may not appear.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step3.png)

4. <span data-ttu-id="2a311-171">シーンにキューブを追加します。</span><span class="sxs-lookup"><span data-stu-id="2a311-171">Add a cube to the scene.</span></span> <span data-ttu-id="2a311-172">[階層] 領域を右クリックし、3D オブジェクトを選択してから、[キューブ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a311-172">Right-click on the hierarchy area, select a 3D object, then click on Cube.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6a.png)

    <span data-ttu-id="2a311-174">ここで、キューブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a311-174">Now, a cube should be in your display.</span></span> <span data-ttu-id="2a311-175">非常に大きいように見えます。</span><span class="sxs-lookup"><span data-stu-id="2a311-175">It will appear very large.</span></span> <span data-ttu-id="2a311-176">サイズを縮小するには、[階層] 領域で [キューブ] を選択した状態で、座標を調整します。</span><span class="sxs-lookup"><span data-stu-id="2a311-176">You can adjust the coordinates (while Cube is still selected in the hierarchy area) to decrease the size.</span></span> <span data-ttu-id="2a311-177">小数点以下桁数の値を x = 0.02、y = 0.02、z = 0.02 に設定します。</span><span class="sxs-lookup"><span data-stu-id="2a311-177">Set the scale values to x = 0.02, y = 0.02 and z = 0.02.</span></span> <span data-ttu-id="2a311-178">キューブは、ボタンの近くのシーンに配置してください。ただし、重なっていないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="2a311-178">Be sure to position the cube in your scene near the button, but not overlapping with it.</span></span> <span data-ttu-id="2a311-179">次の図では、キューブの位置は x = 0、y = 0.4、z = 0.2 です。</span><span class="sxs-lookup"><span data-stu-id="2a311-179">In the image below, the cube’s position is x = 0, y = 0.4, and z = 0.2.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6b.png)

    >[!NOTE]
    ><span data-ttu-id="2a311-181">一般に、Unity の 1 ユニットは現実の世界のほぼ 1 m に相当します。</span><span class="sxs-lookup"><span data-stu-id="2a311-181">In general, 1 unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="2a311-182">これには例外があります。たとえば、オブジェクトがスケーリングされたオブジェクトの子である場合などです。</span><span class="sxs-lookup"><span data-stu-id="2a311-182">There are exceptions to this; for example, when objects are children of scaled objects.</span></span>

5. <span data-ttu-id="2a311-183">PressableButtonHoloLens2 game オブジェクトを選択した状態で、インスペクターの下部にスクロールして、対話型 (スクリプト) コンポーネントのイベントセクションを探します。</span><span class="sxs-lookup"><span data-stu-id="2a311-183">With the PressableButtonHoloLens2 game object selected, scroll towards the bottom in the Inspector to locate the Events section of the Interactable (Script) component.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step4.png)

6. <span data-ttu-id="2a311-185">プッシュ時に応答するイベントをボタンに与えるように、既存のイベントを変更します。</span><span class="sxs-lookup"><span data-stu-id="2a311-185">We will modify the existing event to give the button an event to respond to when pushed.</span></span> <span data-ttu-id="2a311-186">ご覧のように、イベントレシーバーの種類は InteractableOnPressReceiver に設定されています。</span><span class="sxs-lookup"><span data-stu-id="2a311-186">As you can see, the Event Receiver Type is set to InteractableOnPressReceiver.</span></span> <span data-ttu-id="2a311-187">これにより、このボタンは、追跡対象の手がボタンを押したら押されたイベントに応答できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2a311-187">This allows the button to respond to a pressed event when a tracked hand presses the button.</span></span> <span data-ttu-id="2a311-188">この時点で、相互作用フィルターも Near と Far に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a311-188">At this point, you should also change the Interaction Filter to Near and Far.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step5.png)

7. <span data-ttu-id="2a311-190">この手順では、ボタンが押されたら色を変更するようにキューブを設定します。</span><span class="sxs-lookup"><span data-stu-id="2a311-190">In this step you will set up the cube to change color when your button is pressed.</span></span> <span data-ttu-id="2a311-191">BaseScene 階層で PressableButtonHoloLens2 を選択し、次の図に示すように、[キューブ] ゲームオブジェクトを [BaseScene] 階層から [ランタイムのみ] フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2a311-191">Select the PressableButtonHoloLens2 in the BaseScene hierarchy and drag the Cube game object from the BaseScene hierarchy into the Runtime Only field as shown in the image below.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7a.png)

    <span data-ttu-id="2a311-193">[関数なし] というドロップダウンリストをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a311-193">Click the drop-down list that says No Function.</span></span> <span data-ttu-id="2a311-194">[MeshRenderer] を選択し、[素材マテリアル] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a311-194">Select MeshRenderer, then select Material material.</span></span> <span data-ttu-id="2a311-195">これにより、ボタンが押されたときに素材を変更できます。</span><span class="sxs-lookup"><span data-stu-id="2a311-195">This lets you change the material when the button is pressed.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7b.png)

    <span data-ttu-id="2a311-197">[空の素材] フィールドの横にある円をクリックして、[素材の選択] ポップアップを開きます。</span><span class="sxs-lookup"><span data-stu-id="2a311-197">Click the circle next to the empty material field to open the Select Material popup.</span></span> <span data-ttu-id="2a311-198">MRTK には、選択する多くの素材と色が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2a311-198">The MRTK includes many materials and colors to choose from.</span></span> <span data-ttu-id="2a311-199">この例では、ポップアップ検索バーに「MRTK_Standard」と入力して検出された素材 MRTK_Standard_Cyan を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a311-199">For this example, you are going to use the material, MRTK_Standard_Cyan, found by typing in "MRTK_Standard" in the pop-up search bar.</span></span> <span data-ttu-id="2a311-200">素材フィールドを設定するには、MRTK_Standard_Cyan マテリアルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2a311-200">Select the MRTK_Standard_Cyan material to populate the material field.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7c.png)

    <span data-ttu-id="2a311-202">これで、このイベントは、ボタンが押されたら、指定された素材に基づいてキューブが色を変更するように設定されました。</span><span class="sxs-lookup"><span data-stu-id="2a311-202">The event is now set so that when the button is pressed, the cube will change color based on the material you specified.</span></span> <span data-ttu-id="2a311-203">この例では、キューブはシアン色に変更されます。</span><span class="sxs-lookup"><span data-stu-id="2a311-203">In this example, the cube will change to the cyan color.</span></span>

8. <span data-ttu-id="2a311-204">次に、リリース時に、ボタンが既定の色に戻るようにリリースアクションを設定します。</span><span class="sxs-lookup"><span data-stu-id="2a311-204">Next, you are going to set up the release action so that upon release, the button will go back to its default color.</span></span> <span data-ttu-id="2a311-205">上記の手順 7. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="2a311-205">Repeat Step 7, above.</span></span> <span data-ttu-id="2a311-206">ただし、次の図に示すように、この時間は Onrelease MRTK_Standard_LightGray マテリアルではなく OnRelease イベントを使用しています。</span><span class="sxs-lookup"><span data-stu-id="2a311-206">However, this time with the OnRelease event instead of the OnPress MRTK_Standard_LightGray material as shown in the image below.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step8.png)

    <span data-ttu-id="2a311-208">これで、ボタンが押されたときに、新しい色に変わります。シアン.</span><span class="sxs-lookup"><span data-stu-id="2a311-208">Now when the button is pressed, it will change to a new color; cyan.</span></span> <span data-ttu-id="2a311-209">ボタンが離されると、指定した既定の色 (淡い灰色など) に戻ります。画面の上部にある [再生] ボタンをクリックして、エディターで試してみるか、HoloLens 2 に展開してテストします。</span><span class="sxs-lookup"><span data-stu-id="2a311-209">When the button is released, it will change back to the default color you specified (e.g., light gray.) Press the Play button on the top of the screen to try it out in the editor or deploy to your HoloLens 2, to test.</span></span> <span data-ttu-id="2a311-210">ハンドシミュレーションなど、エディター内のシミュレーションの詳細については、 [Mrtk のシミュレーションに関するドキュメントのページ](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a311-210">To learn more about in-editor simulation, including hand simulation, read the [MRTK's simulation documentation page](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>).</span></span>

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="2a311-211">MRTK のグリッド オブジェクト コレクションを使用したボタンのパネルの作成</span><span class="sxs-lookup"><span data-stu-id="2a311-211">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="2a311-212">このセクションでは、MRTK の GridObjectCollection ツールを使用して、複数のボタンを適切なユーザーインターフェイスに自動的に配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a311-212">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK’s GridObjectCollection tool.</span></span>

1. <span data-ttu-id="2a311-213">5つのボタンが表示されるまで、前のセクションのボタンを複製します。</span><span class="sxs-lookup"><span data-stu-id="2a311-213">Duplicate the button from the previous section until you have five buttons.</span></span> <span data-ttu-id="2a311-214">これを行うには、次の方法があります。ボタンを右クリックし、[コピー] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a311-214">There are several ways to do this: -Right-click on the button, and click Copy.</span></span> <span data-ttu-id="2a311-215">次に、ボタンの下に移動し、もう一度右クリックして、[貼り付け] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a311-215">Then go down to below the button and right-click again, then click Paste.</span></span>
    <span data-ttu-id="2a311-216">-ボタンを右クリックし、[複製] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a311-216">-Right-click on the button and click Duplicate.</span></span>
    <span data-ttu-id="2a311-217">-キューブをクリックし、キーボードの Ctrl D キーを押して、キーボードコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2a311-217">-Use the keyboard command by clicking on the cube, and pressing Ctrl D on your keyboard.</span></span>

    <span data-ttu-id="2a311-218">5つのボタンが表示されるまで、この手順を繰り返します。下の画像の5つの赤い矢印をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2a311-218">Repeat this until you have five buttons; see the five red arrows in image below.</span></span>

    ![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. <span data-ttu-id="2a311-220">ボタンを空の親ゲーム オブジェクトの下にグループ化します。</span><span class="sxs-lookup"><span data-stu-id="2a311-220">Group the buttons under an empty parent game object.</span></span> <span data-ttu-id="2a311-221">グリッドコレクション内のボタンを使用するには、共通の親オブジェクトの下にボタンをグループ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a311-221">In order to have the buttons in the grid collection, you need to group your buttons under a common parent object.</span></span> <span data-ttu-id="2a311-222">Hiを右クリックし、[空の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a311-222">Right-click in the hiearachy, and click Create Empty.</span></span> <span data-ttu-id="2a311-223">これにより、すべてのボタンを配置するための新しい空のゲーム オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2a311-223">This creates a new empty game object for you to put all the buttons in.</span></span> <span data-ttu-id="2a311-224">これは、"説明" オブジェクトとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a311-224">It shows up as gameObject.</span></span> <span data-ttu-id="2a311-225">右クリックして、[ButtonCollection] という名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="2a311-225">Right-click and rename it, ButtonCollection.</span></span>

    ![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. <span data-ttu-id="2a311-227">すべてのボタンを新しいコレクションに移動します。</span><span class="sxs-lookup"><span data-stu-id="2a311-227">Move all the buttons into the new collection.</span></span> <span data-ttu-id="2a311-228">これを行うには、階層内の5つのボタンオブジェクトをすべて選択し、次の図に示すように、[ButtonCollection game] オブジェクトの下にすべてをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2a311-228">Do this by selecting all five of the button objects in your heirarchy, and drag them all under ButtonCollection game object as shown in the image below.</span></span> <span data-ttu-id="2a311-229">ヒント: 複数の項目を選択するには、Ctrl キーを押しながら項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a311-229">Tip: select multiple items by holding the Ctrl key while selecting items.</span></span>

    ![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. <span data-ttu-id="2a311-231">MRTK の Grid オブジェクトコレクションコンポーネントをボタンコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="2a311-231">Add MRTK’s Grid Object Collection component to the button collection.</span></span> <span data-ttu-id="2a311-232">これを行うには、ButtonCollection 親オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="2a311-232">To do this, select the ButtonCollection parent object.</span></span> <span data-ttu-id="2a311-233">[インスペクター] パネルで、[コンポーネントの追加] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a311-233">From the Inspector panel, click the Add Component button.</span></span> <span data-ttu-id="2a311-234">検索バーで Grid オブジェクトコレクションを検索し、一覧に表示されたらそれを選択します。</span><span class="sxs-lookup"><span data-stu-id="2a311-234">Search for Grid Object Collection in the search bar, and select it when it appears in the list.</span></span>

    ![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3-step4.png)

    <span data-ttu-id="2a311-236">Grid オブジェクトコレクションコンポーネントを使用すると、適切な行、列、またはグリッド内のボタンまたはオブジェクトのセットを整理できます。</span><span class="sxs-lookup"><span data-stu-id="2a311-236">The Grid Object Collection component lets you organize buttons or any set of objects in a neat row, column, or grid.</span></span> <span data-ttu-id="2a311-237">これは、MRTK によって提供される構成要素の1つであり、魅力的ユーザーインターフェイスをすばやく簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="2a311-237">This is one of the building blocks provided by the MRTK that gives you a quick and easy way to create enticing user interfaces.</span></span>

5. <span data-ttu-id="2a311-238">グリッド オブジェクト コレクションを構成します。</span><span class="sxs-lookup"><span data-stu-id="2a311-238">Configure the grid object collection.</span></span> <span data-ttu-id="2a311-239">すべてのボタンがユーザーに面していることを確認するには、[回転の種類] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a311-239">To ensure all the buttons face the user, select Orient Type.</span></span> <span data-ttu-id="2a311-240">次の図に示すように、[親を前方に移動] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a311-240">Then select Face Parent Forward as shown in the image below.</span></span> <span data-ttu-id="2a311-241">次に、ボタンの間のスペースを設定するためにセル サイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="2a311-241">Next, change the cell size to set the space between your buttons.</span></span> <span data-ttu-id="2a311-242">次の図に示すように、セルの幅とセルの高さを0.05 単位で0.05 単位で開始します。</span><span class="sxs-lookup"><span data-stu-id="2a311-242">Start with 0.05 units by 0.05 units for the Cell Width and Cell Height, as shown in the image below.</span></span> <span data-ttu-id="2a311-243">Distance が0に設定され、Rows が1に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2a311-243">Make sure Distance is set to 0 and Rows is set to 1.</span></span> <span data-ttu-id="2a311-244">[コレクションの更新] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a311-244">Click Update Collection.</span></span> <span data-ttu-id="2a311-245">シーンは次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="2a311-245">The scene will look similar to the picture below.</span></span>

    ![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3-step5.png)

    >[!NOTE]
    ><span data-ttu-id="2a311-247">子オブジェクトまたは親オブジェクトの向きによっては、将来のプロジェクトで、向きの設定を異なった方法で調整することが必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2a311-247">Depending on the orientation of the child objects or parent object, you will likely need to adjust the orientation setting differently in future projects.</span></span> <span data-ttu-id="2a311-248">また、コレクション内のオブジェクトのサイズによっては、[セルの幅] や [セルの高さ] のフィールドも異なった方法で定義することが必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2a311-248">The Cell Width and the Cell Height fields may also need to be defined differently, depending on the size of the objects in your collection.</span></span>

### <a name="adding-text-into-your-scene"></a><span data-ttu-id="2a311-249">シーンへのテキストの追加</span><span class="sxs-lookup"><span data-stu-id="2a311-249">Adding Text into Your Scene</span></span>

<span data-ttu-id="2a311-250">このセクションでは、テキストを Mixed Reality エクスペリエンスに追加したり編集したりする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="2a311-250">In this section, you will learn how to add and edit text to your mixed reality experiences.</span></span> <span data-ttu-id="2a311-251">まだインストールしていない場合は、[ここ](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)に記載されている手順に従って、Unity で TextMeshPro が有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2a311-251">If you haven’t already, ensure you have TextMeshPro enabled in Unity by following the instructions [here](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).</span></span>

1. <span data-ttu-id="2a311-252">ButtonCollection 親オブジェクトを選択し、コレクションを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="2a311-252">Select the ButtonCollection parent object, and right-click the collection.</span></span> <span data-ttu-id="2a311-253">ドロップダウンメニューの [3D オブジェクト] を展開します。</span><span class="sxs-lookup"><span data-stu-id="2a311-253">Expand 3D object in the drop-down menu.</span></span> <span data-ttu-id="2a311-254">次に、[TextMeshPro] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a311-254">Then select TextMeshPro - Text.</span></span> <span data-ttu-id="2a311-255">次の図に示すように、ボタンコレクションの下に TextMeshPro オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a311-255">You should see a TextMeshPro object under the button collection as shown in the image below.</span></span>

    <span data-ttu-id="2a311-256">![レッスン 2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG) ![レッスン 2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span><span class="sxs-lookup"><span data-stu-id="2a311-256">![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG) ![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span></span>

2. <span data-ttu-id="2a311-257">テキストのサイズと位置を読みやすくするために、TextMeshPro コンポーネントの [フォントサイズ] フィールドを調整してフォントのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="2a311-257">To improve the text size and placement for readability, adjust the Font Size field in the TextMeshPro component to change the size of the font.</span></span> <span data-ttu-id="2a311-258">また、次の図に示すように、Rect の位置とスケールを調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a311-258">You will also need to adjust the Rect Transform position and scale as shown in the image below.</span></span> <span data-ttu-id="2a311-259">テキストの構成に使用される値については、以下の画像を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a311-259">See the images below for values used for our text configuration.</span></span> <span data-ttu-id="2a311-260">テキストフィールドのサイズと配置をさらに向上させるための出発点として、これらの値を自由に使用してください。</span><span class="sxs-lookup"><span data-stu-id="2a311-260">Feel free to use these values as a starting point to further improve the size and placement of your text field.</span></span>

    ![レッスン 2 Chapter4 手順3](images/mrlearning-base-ch2-4-step3.png)

3. <span data-ttu-id="2a311-262">次の図に示すように、[インスペクター] パネルの TextMeshPro コンポーネントの [テキスト] フィールドに「ボタンコレクションテキスト」と入力し、[配置] プロパティを [中央] と [上] に調整します。</span><span class="sxs-lookup"><span data-stu-id="2a311-262">In the TextMeshPro component’s text field in the Inspector panel, type in "Button Collection Text" and adjust the Alignment properties to be Center and Top, as shown in the image below.</span></span>

    ![レッスン 2 Chapter4 手順4](images/mrlearning-base-ch2-4-step4.png)

4. <span data-ttu-id="2a311-264">ボタンオブジェクトのテキスト値を変更するには、任意のボタンの横にある矢印をクリックして展開し、[参照] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a311-264">To modify the text values on the button objects, click the arrow next to any button to expand it and navigate to the SeeItSayItLabel object.</span></span> <span data-ttu-id="2a311-265">上の手順で説明したように、ボタンのテキストを編集するには、TextMeshPro に移動します。</span><span class="sxs-lookup"><span data-stu-id="2a311-265">Navigate to TextMeshPro, where you can edit the text to your buttons as described in the steps above.</span></span>

    ![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a><span data-ttu-id="2a311-267">結論</span><span class="sxs-lookup"><span data-stu-id="2a311-267">Congratulations</span></span>

<span data-ttu-id="2a311-268">このレッスンでは、MRTK プロファイル設定をコピー、カスタマイズ、構成する方法 (つまり、空間認識メッシュの可視性) について学習しました。また、HoloLens 2 で追跡されたユーザーを使用してイベントをトリガーするボタンを操作する方法についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="2a311-268">In this lesson, you learned how to copy, customize, and configure an MRTK profile setting (i.e., spatial awareness mesh visibility.) You also learned how to interact with a button to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="2a311-269">最後に、Unity のテキストメッシュ Pro と MRTK の Grid オブジェクトコレクションコンポーネントを使用して、簡単な UI インターフェイスを作成する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="2a311-269">Finally, you learned how to create a simple UI interface using Unity's Text Mesh Pro and the MRTK's Grid Object Collection component.</span></span>

[<span data-ttu-id="2a311-270">次のレッスン: 4. 動的なコンテンツを配置し、ソルバーを使用する</span><span class="sxs-lookup"><span data-stu-id="2a311-270">Next Lesson: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
