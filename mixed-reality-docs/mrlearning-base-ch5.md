---
title: 入門チュートリアル - 6. 高度な入力オプションの探索
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 9a19ad59e520a2743aafd954910f43c6f51d6c8a
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441859"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="ae501-105">6.高度な入力オプションの探索</span><span class="sxs-lookup"><span data-stu-id="ae501-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="ae501-106">このチュートリアルでは、音声コマンド、パン ジェスチャ、視線追跡などを含む、HoloLens 2 でのいくつかの高度な入力オプションについて学習します。</span><span class="sxs-lookup"><span data-stu-id="ae501-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="ae501-107">目標</span><span class="sxs-lookup"><span data-stu-id="ae501-107">Objectives</span></span>

* <span data-ttu-id="ae501-108">音声コマンドとキーワードを使用してイベントをトリガーする</span><span class="sxs-lookup"><span data-stu-id="ae501-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="ae501-109">追跡対象の手を使用してテクスチャと 3D オブジェクトをパンする</span><span class="sxs-lookup"><span data-stu-id="ae501-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="ae501-110">HoloLens 2 の視線追跡機能を活用してオブジェクトを選択する</span><span class="sxs-lookup"><span data-stu-id="ae501-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="ae501-111">音声コマンドの有効化</span><span class="sxs-lookup"><span data-stu-id="ae501-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="ae501-112">このセクションでは、音声コマンドを実装して、ユーザーが Octa オブジェクトでサウンドを再生できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ae501-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="ae501-113">このためには、新しい音声コマンドを作成し、音声コマンドのキーワードが発話されたときに目的のアクションをトリガーするようにイベントを構成します。</span><span class="sxs-lookup"><span data-stu-id="ae501-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="ae501-114">これを実現するための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ae501-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="ae501-115">既定の入力システム プロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="ae501-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="ae501-116">既定の音声コマンド プロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="ae501-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="ae501-117">新しい音声コマンドを作成する</span><span class="sxs-lookup"><span data-stu-id="ae501-117">Create a new speech command</span></span>
4. <span data-ttu-id="ae501-118">Speech Input Handler (Script) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="ae501-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="ae501-119">音声コマンドの Response イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="ae501-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="ae501-120">1.既定の入力システム プロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="ae501-120">1. Clone the default Input System Profile</span></span>
<span data-ttu-id="ae501-121">[Hierarchy]\(階層\) ウィンドウで **[MixedRealityToolkit]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **[Input]\(入力\)** タブを選択し、 **[DefaultHoloLens2InputSystemProfile]** を複製して、カスタマイズ可能な独自の**入力システム プロファイル**に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ae501-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="ae501-123">MRTK 2.4.0 以降を使用している場合:</span><span class="sxs-lookup"><span data-stu-id="ae501-123">If you're using MRTK 2.4.0 or later:</span></span>
> * <span data-ttu-id="ae501-124">[階層] タブから **MixedRealityToolkit** オブジェクトを選択し、[インスペクター] ウィンドウの **[入力]** タブをクリックして、 **[ポインター]** セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="ae501-124">Select the **MixedRealityToolkit** object from the Hierarchy tab, then click the **Input** tab in the Inspector window and expand the **Pointers** section.</span></span> 
> * <span data-ttu-id="ae501-125">**DefaultMixedRealityInputPointerProfile** を複製し、カスタマイズ可能な独自の**入力ポインター プロファイル**に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ae501-125">Clone the **DefaultMixedRealityInputPointerProfile** and replace it with your own customizable **Input Pointer Profile**.</span></span>
> * <span data-ttu-id="ae501-126">**[Gaze Settings]\(視線入力設定\)** セクションで、 **[Is Eye Tracked Enabled]\(視線追跡の有効化\)** が true になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ae501-126">Check that **Is Eye Tracked Enabled** is true in the **Gaze Settings** section.</span></span> 

> [!TIP]
> <span data-ttu-id="ae501-127">MRTK プロファイルを複製する方法については、[Mixed Reality Toolkit プロファイルを構成する方法](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae501-127">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="ae501-128">2.既定の音声コマンド プロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="ae501-128">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="ae501-129">**[Speech]\(音声\)** セクションを展開し、 **[DefaultMixedRealitySpeechCommandsProfile]** を複製して、カスタマイズ可能な独自の**音声コマンド プロファイル**に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ae501-129">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="ae501-131">3.新しい音声コマンドを作成する</span><span class="sxs-lookup"><span data-stu-id="ae501-131">3. Create a new speech command</span></span>

<span data-ttu-id="ae501-132">**[Speech Commands]\(音声コマンド\)** セクションで、 **[+Add a New Speech Command]\(新しい音声コマンドの追加\)** ボタンをクリックして、既存の音声コマンドの一覧の一番下に新しい音声コマンドを追加します。次に、 **[Keyword]\(キーワード\)** フィールドに適切な単語または語句 (たとえば、**Play Music**) を入力します。</span><span class="sxs-lookup"><span data-stu-id="ae501-132">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="ae501-134">コンピューターにマイクがない場合に、エディター内のシミュレーションを使用して音声コマンドをテストするには、キーコードを音声コマンドに割り当て、対応するキーが押されたときにそれをトリガーすることができます。</span><span class="sxs-lookup"><span data-stu-id="ae501-134">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="ae501-135">4.Speech Input Handler (Script) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="ae501-135">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="ae501-136">[Hierarchy]\(階層\) ウィンドウで、 **[Octa]** オブジェクトを選択し、**Speech Input Handler (Script)** コンポーネントを Octa オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="ae501-136">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="ae501-137">次に、 **[Is Focus Required]\(フォーカスが必要\)** チェックボックスをオフにして、ユーザーが Octa オブジェクトを確認しなくても音声コマンドをトリガーできるようにします。</span><span class="sxs-lookup"><span data-stu-id="ae501-137">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="ae501-139">5.音声コマンドの Response イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="ae501-139">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="ae501-140">Speech Input Handler (Script) コンポーネントで、小さい **+** ボタンをクリックして、キーワードの一覧にキーワード要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="ae501-140">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword element to the list of keywords:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

<span data-ttu-id="ae501-142">新しく作成した **[Element 0]\(要素 0\)** をクリックして展開し、 **[Keyword]\(キーワード\)** ドロップダウンから、前に作成した **[Play Music]** キーワードを選択します。</span><span class="sxs-lookup"><span data-stu-id="ae501-142">Click the newly created **Element 0** to expand it, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> <span data-ttu-id="ae501-144">[Keyword]\(キーワード\) ドロップダウンのキーワードは、音声コマンド プロファイルにある音声コマンド リストで定義されているキーワードに基づいて設定されます。</span><span class="sxs-lookup"><span data-stu-id="ae501-144">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="ae501-145">新しい **Response ()** イベントを作成し、イベントを受信するように **Octa** オブジェクトを構成し、トリガーするアクションとして **AudioSource.PlayOneShot** を定義します。次に、適切なオーディオ クリップ (MRTK_Gem オーディオ クリップなど) を **[Audio Clip]\(オーディオ クリップ\)** フィールドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ae501-145">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> <span data-ttu-id="ae501-147">イベントを実装してオーディオ クリップを割り当てる方法については、「[On Touch Started イベントを実装する](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event)」の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae501-147">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="ae501-148">パン ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="ae501-148">The Pan Gesture</span></span>

<span data-ttu-id="ae501-149">パン ジェスチャは、指または手を使ってコンテンツをスクロールするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ae501-149">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="ae501-150">この例では、まず 2D UI をスクロールし、次にそれを展開して 3D オブジェクトのコレクションをスクロールできるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae501-150">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="ae501-151">これを実現するための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ae501-151">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="ae501-152">パンに使用できる Quad オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="ae501-152">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="ae501-153">Near Interaction Touchable (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-153">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="ae501-154">Hand Interaction Pan Zoom (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-154">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="ae501-155">スクロールする 2D コンテンツを追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-155">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="ae501-156">スクロールする 3D コンテンツを追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-156">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="ae501-157">Move With Pan (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-157">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="ae501-158">Move With Pan (Script) コンポーネントは、MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="ae501-158">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="ae501-159">このチュートリアルのアセットと共に提供されました。</span><span class="sxs-lookup"><span data-stu-id="ae501-159">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="ae501-160">1.パンに使用できる Quad オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="ae501-160">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="ae501-161">[Hierarchy]\(階層\) ウィンドウで、空の領域を右クリックし、 **[3D Object]\(3D オブジェクト\)**  >  **[Quad]** を選択して、Quad をシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="ae501-161">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="ae501-162">**PanGesture** のような適切な名前を付け、適切な場所に配置します (たとえば、X = 0、Y = - 0.2、Z = 2 など)。</span><span class="sxs-lookup"><span data-stu-id="ae501-162">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="ae501-164">Unity プリミティブ (3D quad など) をシーンに追加する方法については、「[キューブをシーンに追加する](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene)」の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae501-164">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="ae501-165">他の操作と同様に、パン ジェスチャにもコライダーが必要です。</span><span class="sxs-lookup"><span data-stu-id="ae501-165">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="ae501-166">既定では、Quad にはメッシュ コライダーがあります。</span><span class="sxs-lookup"><span data-stu-id="ae501-166">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="ae501-167">ただし、メッシュ コライダーは極めて薄いため、理想的ではありません。</span><span class="sxs-lookup"><span data-stu-id="ae501-167">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="ae501-168">ユーザーがコライダーを簡単に操作できるようにするために、メッシュ コライダーをボックス コライダーに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ae501-168">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="ae501-169">PanGesture オブジェクトを選択した状態で、**Mesh Collider** コンポーネントの **[Settings]\(設定\)** アイコンをクリックし、 **[Remove Component]\(コンポーネントの削除\)** を選択してメッシュ コライダーを削除します。</span><span class="sxs-lookup"><span data-stu-id="ae501-169">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="ae501-171">[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンを使用して**ボックス コライダー**を追加し、ボックス コライダーの **[Size]\(サイズ\)** Z を 0.15 に変更してボックス コライダーの厚みを増やします。</span><span class="sxs-lookup"><span data-stu-id="ae501-171">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="ae501-173">2.Near Interaction Touchable (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-173">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="ae501-174">**[PanGesture]** オブジェクトが選択された状態で、**Near Interaction Touchable (Script)** コンポーネントを PanGesture オブジェクトに追加します。次に、 **[Fix Bounds]\(境界の修正\)** および **[Fix Center]\(センターの修正\)** ボタンをクリックして、Near Interaction Touchable (Script) の [Local Center]\(ローカルのセンター\) および [Bounds]\(境界\) のプロパティを BoxCollider に一致するように更新します。</span><span class="sxs-lookup"><span data-stu-id="ae501-174">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="ae501-176">3.Hand Interaction Pan Zoom (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-176">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="ae501-177">**PanGesture** オブジェクトが選択された状態で、**Hand Interaction Pan Zoom (Script)** コンポーネントを PanGesture オブジェクトに追加し、次に **[Lock Horizontal]\(水平方向のロック\)** チェックボックスをオンにして、垂直スクロールのみを許可します。</span><span class="sxs-lookup"><span data-stu-id="ae501-177">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="ae501-179">4.スクロールする 2D コンテンツを追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-179">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="ae501-180">[Project]\(プロジェクト\) パネルで **PanContent** 素材を検索し、それをクリックして **PanGesture** オブジェクトのメッシュ レンダラー **[Materials]\(素材\)** の [Element 0]\(要素 0\) プロパティにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ae501-180">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="ae501-182">[Inspector]\(インスペクター\) ウィンドウで、新しく追加した **PanContent** 素材コンポーネントを展開します。次に、 **[Tiling]\(タイル表示\)** の Y 値を 0.5 に変更して X 値と一致させ、タイルを正方形で表示します。</span><span class="sxs-lookup"><span data-stu-id="ae501-182">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="ae501-184">ここでゲーム モードに入ると、エディター内のシミュレーションでパン ジェスチャを使用して、2D コンテンツのスクロールをテストできます。</span><span class="sxs-lookup"><span data-stu-id="ae501-184">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="ae501-186">5.スクロールする 3D コンテンツを追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-186">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="ae501-187">[Hierarchy]\(階層\) ウィンドウで、**PanGesture** オブジェクトの子オブジェクトとして **4 つのキューブを作成し**、[Transform]\(変換\) の **[Scale]\(スケール\)** を X = 0.15、Y = 0.15、Z = 0.15 に設定します。</span><span class="sxs-lookup"><span data-stu-id="ae501-187">In the Hierarchy window, **create four cubes** as a child objects of the **PanGesture** object and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="ae501-189">キューブを均等に配置して時間を節約するには、**Grid Object Collection (Script)** コンポーネントをキューブの親オブジェクト (**PanGesture** オブジェクト) に追加し、次のようにグリッド オブジェクト コレクション (スクリプト) を構成します。</span><span class="sxs-lookup"><span data-stu-id="ae501-189">To space the cubes out evenly, and save some time, add the **Grid Object Collection (Script)** component, to the cubes' parent object, i.e. the **PanGesture** object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="ae501-190">**[Num Rows]\(行数\)** を 1 に変更して、すべてのキューブを 1 行に整列させる</span><span class="sxs-lookup"><span data-stu-id="ae501-190">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="ae501-191">**[Cell Width]\(セル幅\)** を 0.25 に変更して、行内でキューブを一定間隔で並べる</span><span class="sxs-lookup"><span data-stu-id="ae501-191">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="ae501-192">次に、**Update Collection｣\(コレクションの更新\)** ボタンをクリックして、新しい構成を適用します。</span><span class="sxs-lookup"><span data-stu-id="ae501-192">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="ae501-194">6.Move With Pan (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-194">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="ae501-195">[Hierarchy]\(階層\) ウィンドウで、すべての**キューブ子オブジェクト**を選択してから、[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Move With Pan (Script)** コンポーネントをすべてのキューブに追加します。</span><span class="sxs-lookup"><span data-stu-id="ae501-195">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="ae501-197">[Hierarchy]\(階層\) ウィンドウで複数のオブジェクトを選択する方法については、[すべてのオブジェクトに Manipulation Handler (Script) コンポーネントを追加する](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)方法に関する説明 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae501-197">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="ae501-198">すべてのキューブが選択された状態で、**PanGesture** オブジェクトをクリックし、 **[Pan Input Source]\(パン入力ソース\)** フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ae501-198">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="ae501-200">各キューブの Move With Pan (Script) コンポーネントでは、前の手順でパン入力ソースとして割り当てた PanGesture オブジェクトの HandInteractionPanZoom (Script) コンポーネントによって送信される Pan Updated イベントをリッスンし、それに従って各キューブの位置を更新します。</span><span class="sxs-lookup"><span data-stu-id="ae501-200">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="ae501-201">[Hierarchy]\(階層\) ウィンドウで **[PanGesture]** オブジェクトを選択し、次にインスペクターで **[Mesh Renderer]\(メッシュ レンダラー\)** チェックボックスを**オフにして**、Mesh Renderer コンポーネントを無効にします。</span><span class="sxs-lookup"><span data-stu-id="ae501-201">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="ae501-203">ここでゲーム モードに入ると、エディター内のシミュレーションでパン ジェスチャを使用して、3D コンテンツのスクロールをテストできます。</span><span class="sxs-lookup"><span data-stu-id="ae501-203">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="ae501-205">視線追跡</span><span class="sxs-lookup"><span data-stu-id="ae501-205">Eye Tracking</span></span>

<span data-ttu-id="ae501-206">このセクションでは、プロジェクトで視線追跡を有効にする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="ae501-206">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="ae501-207">この例では、ユーザーが視線を向けている間、3DObjectCollection の各オブジェクトをゆっくり回転させるとともに、視線を向けているオブジェクトがエアタップまたは音声コマンドによって選択されたときにブリップ効果をトリガーする機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="ae501-207">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="ae501-208">これを実現するための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ae501-208">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="ae501-209">Eye Tracking Target (Script) コンポーネントをすべてのターゲット オブジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-209">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="ae501-210">Eye Tracking Tutorial Demo (Script) コンポーネントをすべてのターゲット オブジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-210">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="ae501-211">While Looking At Target イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="ae501-211">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="ae501-212">On Selected イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="ae501-212">Implement the On Selected event</span></span>
5. <span data-ttu-id="ae501-213">エディター内のシミュレーションでシミュレートされた視線追跡を有効にする</span><span class="sxs-lookup"><span data-stu-id="ae501-213">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="ae501-214">Visual Studio プロジェクトのアプリ機能で視線入力を有効にする</span><span class="sxs-lookup"><span data-stu-id="ae501-214">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="ae501-215">1.Eye Tracking Target (Script) コンポーネントをすべてのターゲット オブジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-215">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="ae501-216">[Hierarchy]\(階層\) ウィンドウで、 **[3DObjectCollection]** オブジェクトを展開し、すべての**子オブジェクト**を選択してから、[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Eye Tracking Target (Script)** コンポーネントをすべての子オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="ae501-216">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="ae501-218">すべての**子オブジェクト**が選択された状態で、**Eye Tracking Target (Script)** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="ae501-218">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="ae501-219">**[Select Action]\(アクションの選択\)** を **[Select]\(選択\)** に変更して、このオブジェクトのエアタップ アクションを [Select]\(選択\) として定義します</span><span class="sxs-lookup"><span data-stu-id="ae501-219">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="ae501-220">**[Voice Select]\(音声の選択\)** を展開し、音声コマンドの一覧の **[Size]\(サイズ\)** を 1 に設定し、表示される新しい要素の一覧で、 **[Element 0]\(要素 0\)** を **[Select]\(選択)** に変更して、このオブジェクトの音声コマンド アクションを [Select]\(選択) として定義します</span><span class="sxs-lookup"><span data-stu-id="ae501-220">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="ae501-222">2.Eye Tracking Tutorial Demo (Script) コンポーネントをすべてのターゲット オブジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="ae501-222">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="ae501-223">すべての**子オブジェクト**が選択された状態で、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Eye Tracking Tutorial Demo (Script)** コンポーネントをすべての子オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="ae501-223">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="ae501-225">Eye Tracking Target (Script) コンポーネントは、MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="ae501-225">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="ae501-226">このチュートリアルのアセットと共に提供されました。</span><span class="sxs-lookup"><span data-stu-id="ae501-226">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="ae501-227">3.While Looking At Target イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="ae501-227">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="ae501-228">[Hierarchy]\(階層\) ウィンドウで **[Cheese]** オブジェクトを選択してから、新しい **While Looking At Target ()** イベントを作成し、イベントを受信するように **[Cheese]** オブジェクトを構成し、トリガーされるアクションとして **EyeTrackingTutorialDemo.RotateTarget** を定義します。</span><span class="sxs-lookup"><span data-stu-id="ae501-228">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="ae501-230">3DObjectCollection 内のそれぞれの子オブジェクトに対して**繰り返します**。</span><span class="sxs-lookup"><span data-stu-id="ae501-230">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="ae501-231">イベントを実装する方法については、「[手の追跡のジェスチャと操作可能なボタン](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)」の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae501-231">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="ae501-232">4.On Selected イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="ae501-232">4. Implement the On Selected event</span></span>

<span data-ttu-id="ae501-233">[Hierarchy]\(階層\) ウィンドウで **[Cheese]** オブジェクトを選択し、新しい **On Selected ()** イベントを作成します。次に、イベントを受信するように **[Cheese]** オブジェクトを構成し、トリガーするアクションとして **EyeTrackingTutorialDemo.BlipTarget** を定義します。</span><span class="sxs-lookup"><span data-stu-id="ae501-233">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.BlipTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="ae501-235">3DObjectCollection 内のそれぞれの子オブジェクトに対して**繰り返します**。</span><span class="sxs-lookup"><span data-stu-id="ae501-235">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="ae501-236">5.エディター内のシミュレーションでシミュレートされた視線追跡を有効にする</span><span class="sxs-lookup"><span data-stu-id="ae501-236">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="ae501-237">[Hierarchy]\(階層\) ウィンドウで **[MixedRealityToolkit]** オブジェクトを選択し、次に [Inspector]\(インスペクター\) ウィンドウで **[Input]\(入力\)** タブを選択し、 **[Input Data Providers]\(入力データ プロバイダー)** セクションを展開して、 **[Input Simulation Service]\(入力シミュレーション サービス\)** セクションを展開し、 **DefaultMixedRealityInputSimulationProfile** を複製して、カスタマイズ可能な独自の **[Input Simulation Profile]\(入力シミュレーション プロファイル\)** に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ae501-237">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="ae501-239">MRTK プロファイルを複製する方法については、[Mixed Reality Toolkit プロファイルを構成する方法](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae501-239">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="ae501-240">**[Eye Simulation]\(目のシミュレーション\)** セクションで、 **[Simulate Eye Position]\(目の位置のシミュレート\)** チェックボックスをオンにし て、視線追跡シミュレーションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="ae501-240">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="ae501-242">ここでゲーム モードに入ると、カーソルがオブジェクトの 1 つに接触するようにビューを調整し、手の操作または音声コマンドを使用してオブジェクトを選択することによって、実装したスピンとブリップの効果をテストできます。</span><span class="sxs-lookup"><span data-stu-id="ae501-242">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="ae501-244">「[Mixed Reality ツールキットを構成する](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)」の手順に従って、DefaultHoloLens2ConfigurationProfile を使用して、カスタマイズ可能な MRTK 構成プロファイルを複製しなかった場合、視線追跡がプロジェクトで有効になっていない場合があり、有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae501-244">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="ae501-245">詳細については、「[MRTK での視線追跡の概要](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)」 の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae501-245">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="ae501-246">6.Visual Studio プロジェクトのアプリ機能で視線入力を有効にする</span><span class="sxs-lookup"><span data-stu-id="ae501-246">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="ae501-247">アプリをビルドして、Visual Studio からお使いのデバイスにデプロイする前に、プロジェクトのアプリの機能で視線入力が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae501-247">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="ae501-248">そのためには、 [HoloLens 2 の Unity アプリのテスト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)に関するページの手順を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ae501-248">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ae501-249">結論</span><span class="sxs-lookup"><span data-stu-id="ae501-249">Congratulations</span></span>

<span data-ttu-id="ae501-250">これで基本的な視線追跡機能をアプリケーションに追加することができました。</span><span class="sxs-lookup"><span data-stu-id="ae501-250">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="ae501-251">これらの操作は、視線追跡が持つ可能性のほんの一部にすぎません。</span><span class="sxs-lookup"><span data-stu-id="ae501-251">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="ae501-252">このチュートリアルでは、音声コマンドやパン ジェスチャなど、その他の高度な入力機能についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="ae501-252">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="ae501-253">次のレッスン:7.月着陸船サンプル アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="ae501-253">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
