---
title: 入門チュートリアル-6. 詳細な入力オプションの調査
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 5599fe48f62a35d1dc02ce30fb7858fd74e87685
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926533"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="48452-105">6. 詳細な入力オプションを調査する</span><span class="sxs-lookup"><span data-stu-id="48452-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="48452-106">このチュートリアルでは、音声コマンド、パンジェスチャ、および視線追跡の使用を含む、HoloLens 2 の高度な入力オプションをいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="48452-106">In this tutorial, several advanced input options for HoloLens 2 are explored, including the use of voice commands, panning gesture, and eye tracking.</span></span> 

## <a name="objectives"></a><span data-ttu-id="48452-107">目標</span><span class="sxs-lookup"><span data-stu-id="48452-107">Objectives</span></span>

- <span data-ttu-id="48452-108">音声コマンドとキーワードを使用してイベントをトリガーする</span><span class="sxs-lookup"><span data-stu-id="48452-108">Trigger events using voice commands and keywords</span></span>
- <span data-ttu-id="48452-109">追跡したハンドを使用して、追跡したハンドでテクスチャと3D オブジェクトをパンする</span><span class="sxs-lookup"><span data-stu-id="48452-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
- <span data-ttu-id="48452-110">HoloLens 2 の監視機能を活用してオブジェクトを選択する</span><span class="sxs-lookup"><span data-stu-id="48452-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="instructions"></a><span data-ttu-id="48452-111">手順</span><span class="sxs-lookup"><span data-stu-id="48452-111">Instructions</span></span>

### <a name="enabling-voice-commands"></a><span data-ttu-id="48452-112">音声コマンドの有効化</span><span class="sxs-lookup"><span data-stu-id="48452-112">Enabling Voice Commands</span></span>

<span data-ttu-id="48452-113">このセクションでは、2つの音声コマンドが実装されています。</span><span class="sxs-lookup"><span data-stu-id="48452-113">In this section, two voice commands are implemented.</span></span> <span data-ttu-id="48452-114">まず、[診断の切り替え] を表示することによって、フレームレート診断パネルを切り替える機能が導入されました。</span><span class="sxs-lookup"><span data-stu-id="48452-114">First, the ability to toggle the frame rate diagnostics panel is introduced by saying "toggle diagnostics".</span></span> <span data-ttu-id="48452-115">次に、音声コマンドでサウンドを再生する機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="48452-115">Second, the ability to play a sound with a voice command is explored.</span></span> <span data-ttu-id="48452-116">まず、音声コマンドの構成を担当する MRTK プロファイルと設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="48452-116">The MRTK profiles and settings responsible for configuring voice commands is reviewed first.</span></span>

1. <span data-ttu-id="48452-117">[BaseScene] 階層で、[MixedRealityToolkit] を選択します。</span><span class="sxs-lookup"><span data-stu-id="48452-117">In the BaseScene hierarchy, select MixedRealityToolkit.</span></span> <span data-ttu-id="48452-118">次に、[インスペクター] パネルで [入力] を選択し、DefaultMixedRealityInputSystemProfile の左側にある小さい [複製] ボタンをクリックして、[複製プロファイル] ポップアップを開きます。</span><span class="sxs-lookup"><span data-stu-id="48452-118">Then, in the Inspector panel, select Input and click the small Clone button to the left of the DefaultMixedRealityInputSystemProfile to open the Clone Profile popup.</span></span> <span data-ttu-id="48452-119">ポップアップで [複製] をクリックして、新しいプロファイル MixedRealityInputSystemProfile を作成します。</span><span class="sxs-lookup"><span data-stu-id="48452-119">In the popup click Clone to create a new profile MixedRealityInputSystemProfile.</span></span>

    ![mrlearning-base-ch5-1-step1a](images/mrlearning-base-ch5-1-step1a.png)

    <span data-ttu-id="48452-121">これにより、新しく作成された MixedRealityInputSystemProfile で MixedRealityToolkitConfigurationProfile が自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="48452-121">This will also auto-populate the MixedRealityToolkitConfigurationProfile with the newly created MixedRealityInputSystemProfile.</span></span>

    ![mrlearning-base-ch5-1-step1b](images/mrlearning-base-ch5-1-step1b.png)

2. <span data-ttu-id="48452-123">入力システムプロファイルには、さまざまな設定があります。</span><span class="sxs-lookup"><span data-stu-id="48452-123">In the input system profile, there are a variety of settings.</span></span> <span data-ttu-id="48452-124">音声コマンドの場合は、[音声] セクションを展開し、前の手順と同じ手順を実行して DefaultMixedRealitySpeechCommandsProfile を複製し、独自の編集可能なコピーに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="48452-124">For voice commands, expand the Speech section and follow the same process as in the previous step to clone the DefaultMixedRealitySpeechCommandsProfile and replace it with your own editable copy.</span></span>

    ![mrlearning-base-ch5-1-step2](images/mrlearning-base-ch5-1-step2.png)

    <span data-ttu-id="48452-126">Speech コマンドプロファイルでは、さまざまな設定がわかります。</span><span class="sxs-lookup"><span data-stu-id="48452-126">In the speech command profile, you’ll notice a range of settings.</span></span> <span data-ttu-id="48452-127">これらの設定の詳細については、 [Mrtk speech のドキュメント](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48452-127">For a full description of these settings, refer to the [MRTK speech documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>).</span></span>

    <span data-ttu-id="48452-128">既定では、一般の動作は [Auto Start] (自動で開始) です。</span><span class="sxs-lookup"><span data-stu-id="48452-128">By default, the general behavior is auto-start.</span></span> <span data-ttu-id="48452-129">必要に応じて、これを手動で開始するように変更できます。</span><span class="sxs-lookup"><span data-stu-id="48452-129">This can be changed to manual-start, if desired.</span></span> <span data-ttu-id="48452-130">ただし、この例では、[自動開始] のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="48452-130">But for this example, keep it on auto-start.</span></span> <span data-ttu-id="48452-131">MRTK には、メニュー、診断の切り替え、プロファイラーの切り替えなど、いくつかの既定の音声コマンドが付属しています。</span><span class="sxs-lookup"><span data-stu-id="48452-131">The MRTK comes with several default voice commands, such as menu, toggle diagnostics and toggle profiler.</span></span> <span data-ttu-id="48452-132">診断フレームカウントカウンターをオンまたはオフにするために、キーワード "診断の切り替え" を使用します。</span><span class="sxs-lookup"><span data-stu-id="48452-132">We will use the keyword “toggle diagnostics,” in order to turn on and off the diagnostics framerate counter.</span></span> <span data-ttu-id="48452-133">また、以下のステップで新しい音声コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-133">We will also add a new voice command in the steps below.</span></span>

3. <span data-ttu-id="48452-134">新しい音声コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-134">Add a new voice command.</span></span> <span data-ttu-id="48452-135">これを行うには、[+ 新しい音声の追加] コマンドボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="48452-135">To do this, click the + Add a New Speech Command button.</span></span> <span data-ttu-id="48452-136">既存の音声コマンドの一覧の下に新しい行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="48452-136">You'll see a new line that appears below the list of existing voice commands.</span></span> <span data-ttu-id="48452-137">使用する音声コマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="48452-137">Type the voice command you want to use.</span></span> <span data-ttu-id="48452-138">この例では、"play music" コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="48452-138">In this example, use the command “play music".</span></span>

    ![mrlearning-base-ch5-1-step3](images/mrlearning-base-ch5-1-step3.png)

    >[!NOTE]
    ><span data-ttu-id="48452-140">また、音声認識コマンドのキーコードを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="48452-140">You can also set a keycode for speech commands.</span></span> <span data-ttu-id="48452-141">これにより、音声コマンドを使用して、キーボードキーを押したときにイベントをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="48452-141">This allows for voice commands to trigger events upon the press of a keyboard key.</span></span>

4. <span data-ttu-id="48452-142">音声コマンドに応答する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-142">Add the ability to respond to voice commands.</span></span> <span data-ttu-id="48452-143">MixedRealityPlayspace game オブジェクトなど、他の入力スクリプトがアタッチされていない BaseScene 階層内のオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="48452-143">Select any object in the BaseScene hierarchy that does not have any other input scripts attached to it, for example, the MixedRealityPlayspace game object.</span></span> <span data-ttu-id="48452-144">[インスペクター] パネルで [コンポーネントの追加] をクリックし、[音声] を検索して、[音声入力ハンドラー] スクリプトを選択します。</span><span class="sxs-lookup"><span data-stu-id="48452-144">In the Inspector panel, click Add Component, search for "speech", and select the Speech Input Handler script.</span></span>

    ![mrlearning-base-ch5-1-step4](images/mrlearning-base-ch5-1-step4.png)

    <span data-ttu-id="48452-146">既定では、2つのチェックボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="48452-146">By default, you will see two checkboxes.</span></span> <span data-ttu-id="48452-147">1つは [フォーカスが必要] チェックボックスです。</span><span class="sxs-lookup"><span data-stu-id="48452-147">One is the Is Focus Required checkbox.</span></span> <span data-ttu-id="48452-148">そのため、光を見つめ、ヘッドを見つめ、コントローラーを見つめ、または手動でオブジェクトをポイントしている限り、音声コマンドがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="48452-148">So, as long as you are pointing at the object with a ray-eye-gaze, head-gaze, controller-gaze, or hand-gaze, the voice command will be triggered.</span></span> <span data-ttu-id="48452-149">ユーザーが音声コマンドを使用するためにオブジェクトを確認する必要がないように、このチェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="48452-149">Uncheck this checkbox so that the user does not have to look at the object to use the voice command.</span></span>

5. <span data-ttu-id="48452-150">音声コマンドに応答する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-150">Add the ability to respond to a voice command.</span></span> <span data-ttu-id="48452-151">これを行うには、音声入力ハンドラーにある [+] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="48452-151">To do this, click the + button that’s in the Speech Input Handler.</span></span>

    ![mrlearning-base-ch5-1-step5](images/mrlearning-base-ch5-1-step5.png)

6. <span data-ttu-id="48452-153">[キーワード] の横に、ドロップダウンメニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="48452-153">Next to Keyword, you'll see a dropdown menu.</span></span> <span data-ttu-id="48452-154">[診断の切り替え] を選択すると、ユーザーが "診断の切り替え" という語句が表示されるたびに、アクションがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="48452-154">Select Toggle Diagnostics so that whenever the user says the phrase “toggle diagnostics”, it triggers an action.</span></span> <span data-ttu-id="48452-155">要素0を展開するには、その横にある矢印を押す必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="48452-155">Note that you might need to expand Element 0 by pressing the arrow next to it.</span></span>

    ![mrlearning-base-ch5-1-step6](images/mrlearning-base-ch5-1-step6.png)

    >[!NOTE]
    ><span data-ttu-id="48452-157">これらのキーワードは、手順 3. で編集したプロファイルに基づいて設定されます。</span><span class="sxs-lookup"><span data-stu-id="48452-157">These keywords are populated, based on the profile you edited in the step 3.</span></span>

7. <span data-ttu-id="48452-158">診断システムの音声制御スクリプトを追加して、フレームレートカウンターの診断のオンとオフを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="48452-158">Add the Diagnostics System Voice Controls script to toggle the framerate counter diagnostic on and off.</span></span> <span data-ttu-id="48452-159">これを行うには、[コンポーネントの追加] をクリックし、[Diagnostics System Voice Controls script] を検索して、メニューから追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-159">To do this, press Add Component, search for Diagnostics System Voice Controls script and add it from the menu.</span></span> <span data-ttu-id="48452-160">このスクリプトは任意のオブジェクトに追加できますが、わかりやすさのため、[Speech Input Handler] (音声入力ハンドラー) と同じオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-160">This script can be added to any object, but for simplicity, we will add it to the same object as the speech input handler.</span></span>

    ![mrlearning-base-ch5-1-step7](images/mrlearning-base-ch5-1-step7.png)

8. <span data-ttu-id="48452-162">音声入力ハンドラーに新しい応答を追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-162">Add a new response in the speech input handler.</span></span> <span data-ttu-id="48452-163">これを行うには、[+] アイコンをクリックして、応答の一覧に新しい応答を追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-163">To do this, click the "+" icon to add a new response to the response list.</span></span>

    ![mrlearning-base-ch5-1-step8](images/mrlearning-base-ch5-1-step8.png)

9. <span data-ttu-id="48452-165">Diagnostics System Voice Controls スクリプトを含むオブジェクトを、前の手順で作成した新しい応答にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="48452-165">Drag the object that has the Diagnostics System Voice Controls script to the new response you just created in the previous step.</span></span>

    ![mrlearning-base-ch5-1-step9](images/mrlearning-base-ch5-1-step9.png)

10. <span data-ttu-id="48452-167">関数のドロップダウンをクリックし ([関数なし] と表示されます)、診断システムの音声コントロールを選択し、診断をオンまたはオフに切り替える ToggleDiagnostics () 関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="48452-167">Click the function dropdown (where it says No Function), then Diagnostics System Voice Controls, and select the ToggleDiagnostics () function which toggles your diagnostics on and off.</span></span>

    ![mrlearning-base-ch5-1-step10](images/mrlearning-base-ch5-1-step10.png)

    >[!IMPORTANT]
    > <span data-ttu-id="48452-169">デバイスにビルドする前に、mic 設定を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="48452-169">Before building to your device, you need to enable mic settings.</span></span> <span data-ttu-id="48452-170">これを行うには、[ファイル] をクリックし、[ビルドの設定]、[プレーヤーの設定] の順にクリックし、マイクの機能が設定されていることを確認します</span><span class="sxs-lookup"><span data-stu-id="48452-170">To do this, click File and go to Build Settings, Player Settings and ensure that the microphone capability is set.</span></span>

    <span data-ttu-id="48452-171">次に、Octa オブジェクトを使用して音声コマンドからオーディオファイルを再生する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-171">Next, add the ability to play an audio file from voice command using the Octa object.</span></span> <span data-ttu-id="48452-172">[レッスン 4](mrlearning-base-ch4.md)から、オーディオクリップを再生して、octa オブジェクトにタッチする機能が追加されたことを思い出してください。</span><span class="sxs-lookup"><span data-stu-id="48452-172">Recall from [lesson 4](mrlearning-base-ch4.md) that the ability to play an audio clip from touching the Octa object was added.</span></span> <span data-ttu-id="48452-173">この同じオーディオ ソースを、ミュージック音声コマンドでも活用します。</span><span class="sxs-lookup"><span data-stu-id="48452-173">We will leverage this same audio source for our music voice command.</span></span>

11. <span data-ttu-id="48452-174">BaseScene 階層内の Octa オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="48452-174">Select the Octa object in the BaseScene hierarchy.</span></span>

12. <span data-ttu-id="48452-175">別の音声入力ハンドラーを追加します (手順4と5を繰り返します)。ただし、octa オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="48452-175">Add another speech input handler (repeat Steps 4 and 5), but with the octa object.</span></span>

13. <span data-ttu-id="48452-176">手順6の [診断の切り替え] コマンドを追加するのではなく、次の図に示すように、[音楽音声の再生] コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-176">Instead of adding the Toggle Diagnostics voice command from step 6, add the Play Music voice command as shown in the image below.</span></span>

    ![mrlearning-base-ch5-1-step13](images/mrlearning-base-ch5-1-step13.png)

14. <span data-ttu-id="48452-178">手順 8. と 9. と同様に、新しい応答を追加し、診断システムの音声制御スクリプトを持つオブジェクトである Octa オブジェクトを空の応答スロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="48452-178">As with Steps 8 and 9, add a new response and drag the Octa object, the object that has the Diagnostics System Voice Controls script on it, to the empty response slot.</span></span>

15. <span data-ttu-id="48452-179">[関数なし] というドロップダウンメニューを選択します。</span><span class="sxs-lookup"><span data-stu-id="48452-179">Select the dropdown menu that says No Function.</span></span> <span data-ttu-id="48452-180">次に、[オーディオソース]、[PlayOneShot (AudioClip)] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="48452-180">Then select Audio Source, followed by PlayOneShot (AudioClip).</span></span>

    ![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. <span data-ttu-id="48452-182">この例では、[レッスン 4](mrlearning-base-ch4.md)と同じオーディオクリップを使用します。</span><span class="sxs-lookup"><span data-stu-id="48452-182">For this example, we are going to use the same audio clip from [Lesson 4](mrlearning-base-ch4.md).</span></span> <span data-ttu-id="48452-183">プロジェクトパネルに移動し、"MRTK_Gem" オーディオクリップを検索して、次の図に示すようにオーディオソーススロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="48452-183">Go into your Project panel, search for “MRTK_Gem” audio clip and drag it into the audio source slot as shown in the image below.</span></span> <span data-ttu-id="48452-184">これで、アプリケーションは音声コマンド "トグル診断" に応答して、フレームレートカウンターパネルを切り替え、音楽を再生して MRTK_Gem 楽曲を再生します。</span><span class="sxs-lookup"><span data-stu-id="48452-184">Now your application will respond to the voice commands “toggle diagnostics” to toggle the Frame Rate Counter panel and Play Music to play the MRTK_Gem song.</span></span>

    ![Lesson5 Chapter1.txt Step16im](images/Lesson5_chapter1_step16im.PNG)

### <a name="the-pan-gesture"></a><span data-ttu-id="48452-186">パン ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="48452-186">The Pan Gesture</span></span>

<span data-ttu-id="48452-187">このセクションでは、パンジェスチャの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="48452-187">In this section, you will learn how to use the pan gesture.</span></span> <span data-ttu-id="48452-188">これは、指またはハンドを使用してコンテンツをスクロールすることでスクロールする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="48452-188">This is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="48452-189">また、パンジェスチャを使用して、オブジェクトの回転、3D オブジェクトのコレクションの反復処理、または 2D UI のスクロールを行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="48452-189">You can also use the pan gesture to rotate objects, cycle through a collection of 3D objects, or even to scroll a 2D UI.</span></span> <!--TMP You will also learn how to use the pan gesture to warp a texture, and how to move a collection of 3D objects.-->

1. <span data-ttu-id="48452-190">quad を作成します。</span><span class="sxs-lookup"><span data-stu-id="48452-190">Create a quad.</span></span> <span data-ttu-id="48452-191">BaseScene 階層で、右クリックし、[3D オブジェクト] を選択し、次にクワッドを選択します。</span><span class="sxs-lookup"><span data-stu-id="48452-191">In your BaseScene hierarchy, right-click, select "3D Object" followed by Quad.</span></span>

    ![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. <span data-ttu-id="48452-193">必要に応じて、クワッドの位置を変更します。</span><span class="sxs-lookup"><span data-stu-id="48452-193">Reposition the quad, as appropriate.</span></span> <span data-ttu-id="48452-194">この例では、HoloLens 2 から快適に使用できるように、x = 0、y = 0、z = 1.5 をカメラから離れた位置に設定します。</span><span class="sxs-lookup"><span data-stu-id="48452-194">For our example, we set the x = 0, the y = 0 and the z = 1.5 away from the camera for a comfortable position from HoloLens 2.</span></span>

    >[!NOTE]
    ><span data-ttu-id="48452-195">4つのブロックまたは前のレッスンの内容の前にある場合は、他のオブジェクトをブロックしないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="48452-195">If the quad blocks or is in front of any content from the previous lessons, be sure to move it so that it doesn’t block any of the other objects.</span></span>

3. <span data-ttu-id="48452-196">素材を quad に適用します。</span><span class="sxs-lookup"><span data-stu-id="48452-196">Apply a material to the quad.</span></span> <span data-ttu-id="48452-197">この資料では、パンジェスチャを使用してスクロールします。</span><span class="sxs-lookup"><span data-stu-id="48452-197">This material will be what we will be scrolling through with the pan gesture.</span></span>

    ![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. <span data-ttu-id="48452-199">[プロジェクト] パネルで、検索ボックスに「コンテンツのパン」と入力します。</span><span class="sxs-lookup"><span data-stu-id="48452-199">In your Projects panel, type “pan content” in the Search box.</span></span> <span data-ttu-id="48452-200">その素材をシーンのクワッドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="48452-200">Drag that material onto the quad in your scene.</span></span>

    >[!NOTE]
    ><span data-ttu-id="48452-201">Pan コンテンツマテリアルは MRTK には含まれていませんが、前のレッスンでインポートしたように、このモジュールの資産パッケージのアセットに含まれています。</span><span class="sxs-lookup"><span data-stu-id="48452-201">The Pan Content material is not included in the MRTK, but an asset in this module's asset package as imported in previous lessons.</span></span>

    >[!NOTE]
    ><span data-ttu-id="48452-202">パン コンテンツを追加すると、引き伸ばされたように見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="48452-202">When you add the pan content, it may look stretched.</span></span> <span data-ttu-id="48452-203">これを修正するには、quad のサイズの x、y、z 値を希望する大きさになるまで調整します。</span><span class="sxs-lookup"><span data-stu-id="48452-203">You can fix this by adjusting the values x, y and z values of the size of the quad until you are satisfied with the way it looks.</span></span>

    <span data-ttu-id="48452-204">パン ジェスチャを使用するには、オブジェクト上のコライダーが必要です。</span><span class="sxs-lookup"><span data-stu-id="48452-204">To use the pan gesture, you will need a collider on your object.</span></span> <span data-ttu-id="48452-205">場合によっては、quad には既にメッシュ コライダーがあります。</span><span class="sxs-lookup"><span data-stu-id="48452-205">You may see the quad already has a mesh collider.</span></span> <span data-ttu-id="48452-206">ただし、メッシュ コライダーは極めて薄く、選択するのが容易ではないため理想的ではありません。</span><span class="sxs-lookup"><span data-stu-id="48452-206">However, the mesh collider is not ideal, because it is extremely thin and difficult to select.</span></span> <span data-ttu-id="48452-207">メッシュ コライダーをボックス コライダーに置き換えることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="48452-207">We suggest replacing the mesh collider with a box collider.</span></span>

5. <span data-ttu-id="48452-208">[インスペクター] パネルから、クワッド上のメッシュ collider を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="48452-208">Right-click the mesh collider that’s on the quad from the Inspector panel.</span></span> <span data-ttu-id="48452-209">次に、[コンポーネントの削除] をクリックして削除します。</span><span class="sxs-lookup"><span data-stu-id="48452-209">Then remove it by clicking Remove Component.</span></span>

    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. <span data-ttu-id="48452-211">次に、[コンポーネントの追加] をクリックして box collider を追加し、"box collider" を検索します。</span><span class="sxs-lookup"><span data-stu-id="48452-211">Now add the box collider by clicking Add Component and searching “box collider”.</span></span> <span data-ttu-id="48452-212">既定で追加された box collider はまだ薄くなっているため、[Collider の編集] ボタンをクリックして編集します。</span><span class="sxs-lookup"><span data-stu-id="48452-212">The default added box collider is still too thin, so click the Edit Collider button to edit.</span></span> <span data-ttu-id="48452-213">ボタンを押すと、x、y、z の値を使用して、またはシーン エディターの要素を使用してサイズを調整できます。</span><span class="sxs-lookup"><span data-stu-id="48452-213">When it’s pressed in, you can adjust the size using the x, y and z values or the elements in the scene editor.</span></span> <span data-ttu-id="48452-214">この例では、ボックス コライダーを quad の少し後ろまで拡張します。</span><span class="sxs-lookup"><span data-stu-id="48452-214">For our example, we want to extend the box collider a little behind the quad.</span></span> <span data-ttu-id="48452-215">シーン エディターで、ボックス コライダーを後ろから外側にドラッグします (下の図を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="48452-215">In the scene editor, drag the box collider from the back, outwards (see the image below).</span></span> <span data-ttu-id="48452-216">これにより、ユーザーは指を使用するだけでなく、スクロールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="48452-216">This lets the user not only use their finger, but their entire hand to scroll.</span></span>

    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)

7. <span data-ttu-id="48452-218">操作ができるようにします。</span><span class="sxs-lookup"><span data-stu-id="48452-218">Make it interactive.</span></span> <span data-ttu-id="48452-219">このモジュールを直接操作する必要があるので、ここではレッスン4で、Octa オブジェクトから音楽を再生するために使用した Near インタラクション Touchable コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="48452-219">Since we want to interact with the quad directly, we want to use the Near Interaction Touchable component that we used this in Lesson 4 for playing music from the Octa object.</span></span> <span data-ttu-id="48452-220">[コンポーネントの追加] をクリックし、次の図に示すように "near インタラクション touchable" を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="48452-220">Click Add Component, search for “near interaction touchable” and select it as shown in the images below.</span></span>

    ![mrlearning-base-ch5-2-step7a](images/mrlearning-base-ch5-2-step7a.png)

    <span data-ttu-id="48452-222">境界や中心が BoxCollider のサイズや中心に一致しないという警告が黄色で表示されている場合は、[境界の修正] ボタンまたは [修正センター] ボタンをクリックして、中心と境界の値を更新します。</span><span class="sxs-lookup"><span data-stu-id="48452-222">If you see a yellow warning about bounds and/or center not matching the BoxCollider's size and/or center, click the Fix Bounds and/or Fix Center buttons to update the center and bounds values.</span></span>

    ![mrlearning-base-ch5-2-step7b](images/mrlearning-base-ch5-2-step7b.png)

8. <span data-ttu-id="48452-224">パン ジェスチャを認識する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-224">Add the ability to recognize the pan gesture.</span></span> <span data-ttu-id="48452-225">[コンポーネントの追加] をクリックし、検索フィールドに「手動での相互作用」と入力して、ハンドインタラクションのパンズームスクリプトコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-225">Click Add Component, type “hand interaction” in the search field and add the Hand Interaction Pan Zoom script component.</span></span>

    ![mrlearning-base-ch5-2-step8a](images/mrlearning-base-ch5-2-step8a.png)

    <span data-ttu-id="48452-227">これにより、パン対応のクワッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="48452-227">And with that, you have a pan-enabled quad.</span></span>

    <span data-ttu-id="48452-228">ご覧のように、ハンド対話のパンズームコンポーネントには、オプションの演習としてさまざまな設定があり、自由に再生することができます。</span><span class="sxs-lookup"><span data-stu-id="48452-228">As you can see, the Hand Interaction Pan Zoom component has various setting, as an optional exercise, feel free to play around with them.</span></span>

    ![mrlearning-base-ch5-2-step8b](images/mrlearning-base-ch5-2-step8b.png)

<!--TMP
   Next, we will learn how to pan 3D objects. 

10. Right-click the quad object, select 3D object and click Cube. Scale the cube so that it’s roughly x = 0.1, y = 0.1 and z = 0.1. Copy that cube three times by right-clicking the cube and pressing duplicate, or by pressing control/command D. Space them out evenly. Your scene should look similar to the image below.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)

11. Select the quad again and under the hand interaction pan script, set the pan actions to each of the cubes. Under Pan Event Receivers, we want to specify the number of objects receiving the event. Since there are four cubes, type “4” and press Enter. Four empty fields should appear.

![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)

12. Drag each of the cubes into each of the empty element slots.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Add the Move with Pan script to all of the cubes by pressing and holding control/command and select each object. From the Inspector panel, click Add Component and search for “move with pan.” Click the script and it is added to each cube. Now the 3D objects will move with your pan gesture. If you remove the mesh render on your quad, you should now have an invisible quad where you can pan through a list of 3D objects.
-->

### <a name="eye-tracking"></a><span data-ttu-id="48452-230">視線追跡</span><span class="sxs-lookup"><span data-stu-id="48452-230">Eye Tracking</span></span>

<span data-ttu-id="48452-231">このセクションでは、デモで目の追跡を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="48452-231">In this section, we will explore how to enable eye tracking in our demo.</span></span> <span data-ttu-id="48452-232">3D メニュー項目が目の gazed になったときに、その項目をゆっくりと回転させます。</span><span class="sxs-lookup"><span data-stu-id="48452-232">We will slowly spin our 3D menu items when they are being gazed upon with your eye gaze.</span></span> <span data-ttu-id="48452-233">また、見つめられた項目が選択されると、楽しい効果がトリガーされるようにします。</span><span class="sxs-lookup"><span data-stu-id="48452-233">We will also trigger a fun effect when the gazed-upon item is selected.</span></span>

1. <span data-ttu-id="48452-234">MRTK プロファイルが視線追跡用に適切に構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="48452-234">Ensure the MRTK profiles are properly configured for eye tracking.</span></span> <span data-ttu-id="48452-235">これを行うには、「 [MRTK での目の追跡](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)の概要」の手順に進み、「視線[追跡ステップバイステップの設定](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step)」セクションの手順を確認して、目の追跡が適切に構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="48452-235">To do this, go to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions and verify that eye tracking is properly configured by reviewing the steps in the [Setting up eye tracking step-by-step](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step) section.</span></span> <span data-ttu-id="48452-236">ドキュメントの残りの手順をすべて完了します。</span><span class="sxs-lookup"><span data-stu-id="48452-236">Complete any remaining steps in the documentation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="48452-237">「 [Mixed Reality Toolkit の構成](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit)」のレッスンで説明されているように、DefaultHoloLens2InputSystemProfile を使用してカスタム MRTK 構成プロファイルを複製する場合、unity プロジェクトではアイ tracking が既定で有効になりますが、unity エディターの視線追跡シミュレーションを設定し、ビルドの目の追跡を許可するように Visual Studio を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48452-237">If you used the DefaultHoloLens2InputSystemProfile, as instructed in the [Configure the Mixed Reality Toolkit](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit) lesson, to clone your custom MRTK configuration profile, eye tracking is enabled by default in the Unity project but you will still have to set up eye tracking simulation for the Unity editor and configure Visual Studio to allow eye tracking for the build.</span></span>

    <span data-ttu-id="48452-238">上記のリンクでは、以下の点についての簡潔な指示があります。</span><span class="sxs-lookup"><span data-stu-id="48452-238">The link above provides brief instructions for:</span></span>

    - <span data-ttu-id="48452-239">MRTK プロファイルで使用するために Windows Mixed Reality の視線 Data Provider を作成する</span><span class="sxs-lookup"><span data-stu-id="48452-239">Creating the Windows Mixed Reality Eye Gaze Data Provider for use in the MRTK profile</span></span>
    - <span data-ttu-id="48452-240">カメラに接続されている宝石プロバイダーの目の追跡を有効にする</span><span class="sxs-lookup"><span data-stu-id="48452-240">Enabling eye tracking in the Gaze Provider attached to the camera</span></span>
    - <span data-ttu-id="48452-241">Unity エディターでの目の追跡シミュレーションの設定</span><span class="sxs-lookup"><span data-stu-id="48452-241">Setting up an eye tracking simulation in the Unity editor</span></span>
    - <span data-ttu-id="48452-242">Visual Studio ソリューションの機能を編集して、ビルド済みアプリケーションで視線追跡できるようにする</span><span class="sxs-lookup"><span data-stu-id="48452-242">Editing the Visual Studio solution's capabilities to allow eye tracking in the built application</span></span>

2. <span data-ttu-id="48452-243">[Eye Tracking Target] (視線追跡ターゲット) コンポーネントをターゲット オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-243">Add the Eye Tracking Target component to target objects.</span></span> <span data-ttu-id="48452-244">オブジェクトが視線イベントに応答できるようにするには、視線を使用して操作する各オブジェクトに EyeTrackingTarget コンポーネントを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48452-244">To allow an object to respond to eye gaze events, we'll need to add the EyeTrackingTarget component on each object that we want to interact with by using eye gaze.</span></span> <span data-ttu-id="48452-245">このコンポーネントを、グリッド コレクションの一部である 9 つの 3D オブジェクトそれぞれに追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-245">Add this component to each of the nine 3D objects that are part of the grid collection.</span></span>

    >[!TIP]
    ><span data-ttu-id="48452-246">Shift キーまたは ctrl キーを使用してシーン階層内の複数の項目を選択し、EyeTrackingTarget コンポーネントを一括して追加することができます。</span><span class="sxs-lookup"><span data-stu-id="48452-246">You can use the shift and/or ctrl keys to select multiple items in the scene hierarchy and then bulk-add the EyeTrackingTarget component.</span></span>

    ![Lesson5 Chapter3 のステップごとのステップ](images/Lesson5Chapter3Step2.JPG)

3. <span data-ttu-id="48452-248">次に、いくつかの魅力的な対話用に EyeTrackingTutorialDemo スクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-248">Next, we will add the EyeTrackingTutorialDemo script for some exciting interactions.</span></span> <span data-ttu-id="48452-249">EyeTrackingTutorialDemo スクリプトは、このチュートリアルシリーズリポジトリの一部として含まれています。</span><span class="sxs-lookup"><span data-stu-id="48452-249">The EyeTrackingTutorialDemo script is included as part of this tutorial series repository.</span></span> <span data-ttu-id="48452-250">混合 Reality ツールキットには、既定では含まれていません。</span><span class="sxs-lookup"><span data-stu-id="48452-250">It is not included by default with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="48452-251">Grid コレクション内の3D オブジェクトごとに、[コンポーネントの追加] メニューでコンポーネントを検索して、EyeTrackingTutorialDemo スクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-251">For each 3D object in the grid collection, add the EyeTrackingTutorialDemo script by searching for the component in the Add Component menu.</span></span>

   ![Lesson5 Chapter3 手順3](images/Lesson5Chapter3Step3.JPG)

4. <span data-ttu-id="48452-253">ターゲットを見つめている間、オブジェクトを回転させます。</span><span class="sxs-lookup"><span data-stu-id="48452-253">Spin the object while looking at the target.</span></span> <span data-ttu-id="48452-254">3D オブジェクトを見ながらスピンするように構成したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="48452-254">We want to configure our 3D objects to spin while we are looking at them.</span></span> <span data-ttu-id="48452-255">これを行うには、次の図に示すように、EyeTrackingTarget コンポーネントの Target () セクションを参照しながら、に新しいフィールドを挿入します。</span><span class="sxs-lookup"><span data-stu-id="48452-255">To do this, insert a new field in the While Looking At Target() section of the EyeTrackingTarget component, as shown in the image below.</span></span>

    ![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)

    <span data-ttu-id="48452-257">新しく作成されたフィールドで、次の図に示すように、現在の Game オブジェクトを空のフィールドに追加し、EyeTrackingTutorialDemo > RotateTarget () を選択します。</span><span class="sxs-lookup"><span data-stu-id="48452-257">In the newly-created field, add the current Game Object to the empty field, and select EyeTrackingTutorialDemo>RotateTarget(), as shown in the image below.</span></span> <span data-ttu-id="48452-258">これで、視線追跡により、3D オブジェクトを見つめると回転するように構成できました。</span><span class="sxs-lookup"><span data-stu-id="48452-258">Now the 3D object is configured to spin when it is being gazed upon with eye tracking.</span></span>

    ![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)

5. <span data-ttu-id="48452-260">エアタップによって、または "select" と言ったときに、選択時に gazed される "ブリップが発生 target" の機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="48452-260">Add in the ability to “blip target” that is being gazed at upon select by air-tap or saying “select”.</span></span> <span data-ttu-id="48452-261">手順4と同様に、次の図に示すように、EyeTrackingTarget コンポーネントの game オブジェクトの Select () フィールドに割り当てることによって、EyeTrackingTutorialDemo > をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="48452-261">Similar to Step 4, we want to trigger EyeTrackingTutorialDemo>BlipTarget() by assigning it to the game object’s Select() field of the EyeTrackingTarget component, as shown in the figure below.</span></span> <span data-ttu-id="48452-262">これで構成が完了すると、エアタップや音声コマンドの "select" などの選択アクションをトリガーするたびに、game オブジェクトにわずかなブリップが発生が見られます。</span><span class="sxs-lookup"><span data-stu-id="48452-262">With this now configured, you will notice a slight blip in the game object whenever you trigger a select action, such as air-tap or the voice command “select”.</span></span>

    ![Lesson5 Chapter3 手順5](images/Lesson5Chapter3Step5.JPG)

6. <span data-ttu-id="48452-264">HoloLens 2 向けにビルドする前に、視線追跡機能が適切に構成されていることを確かめます。</span><span class="sxs-lookup"><span data-stu-id="48452-264">Ensure eye tracking capabilities are properly configured before building to HoloLens 2.</span></span> <span data-ttu-id="48452-265">このドキュメントの執筆時点では、Unity には、視線追跡機能に対して、宝石入力を設定する機能がまだありません。</span><span class="sxs-lookup"><span data-stu-id="48452-265">As of this writing, Unity does not yet have the ability to set the gaze input for eye tracking capabilities.</span></span> <span data-ttu-id="48452-266">この機能の設定は、監視が HoloLens 2 で動作するために必要です。</span><span class="sxs-lookup"><span data-stu-id="48452-266">Setting this capability is required for eye tracking to work in HoloLens 2.</span></span> <span data-ttu-id="48452-267">「 [HoloLens 2 での Unity アプリのテスト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)」の手順に従って、宝石入力機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="48452-267">Follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions to enable the gaze input capability.</span></span>

## <a name="congratulations"></a><span data-ttu-id="48452-268">結論</span><span class="sxs-lookup"><span data-stu-id="48452-268">Congratulations</span></span>

<span data-ttu-id="48452-269">アプリケーションに基本的な監視機能が正常に追加されました。</span><span class="sxs-lookup"><span data-stu-id="48452-269">You’ve successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="48452-270">これらの操作は、視線追跡が持つ可能性のほんの一部にすぎません。</span><span class="sxs-lookup"><span data-stu-id="48452-270">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="48452-271">また、レッスン5では、音声コマンド、パンジェスチャ、視線追跡などの高度な入力機能について学習しました。</span><span class="sxs-lookup"><span data-stu-id="48452-271">This chapter also concludes Lesson 5, where we learned about advanced input functionality, such as voice commands, panning gestures, and eye tracking.</span></span>

[<span data-ttu-id="48452-272">次のレッスン: 7. 旧暦モジュールサンプルアプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="48452-272">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
