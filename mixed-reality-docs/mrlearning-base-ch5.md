---
title: 入門チュートリアル-6. 詳細な入力オプションの調査
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: aaa02ce118fd051d94311e837b143affc96ff72b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554256"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="2d8cb-105">6. 詳細な入力オプションを調査する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="2d8cb-106">このチュートリアルでは、HoloLens 2 の高度な入力オプションをいくつか紹介します。これには、音声コマンド、パンジェスチャ、および視線追跡の使用が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="2d8cb-107">目標</span><span class="sxs-lookup"><span data-stu-id="2d8cb-107">Objectives</span></span>

* <span data-ttu-id="2d8cb-108">音声コマンドとキーワードを使用してイベントをトリガーする</span><span class="sxs-lookup"><span data-stu-id="2d8cb-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="2d8cb-109">追跡したハンドを使用して、追跡したハンドでテクスチャと3D オブジェクトをパンする</span><span class="sxs-lookup"><span data-stu-id="2d8cb-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="2d8cb-110">HoloLens 2 の監視機能を活用してオブジェクトを選択する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="2d8cb-111">音声コマンドの有効化</span><span class="sxs-lookup"><span data-stu-id="2d8cb-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="2d8cb-112">このセクションでは、speech コマンドを実装して、ユーザーが Octa オブジェクトでサウンドを再生できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="2d8cb-113">このためには、新しい speech コマンドを作成し、speech コマンドキーワードが話されたときに目的のアクションをトリガーするようにイベントを構成します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="2d8cb-114">これを実現するには、主に次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="2d8cb-115">既定の入力システムプロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="2d8cb-116">既定の Speech コマンドプロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="2d8cb-117">新しい speech コマンドを作成する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-117">Create a new speech command</span></span>
4. <span data-ttu-id="2d8cb-118">音声入力ハンドラー (スクリプト) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="2d8cb-119">Speech コマンドの応答イベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="2d8cb-120">1. 既定の入力システムプロファイルを複製します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="2d8cb-121">階層 ウィンドウで**MixedRealityToolkit**オブジェクトを選択し、インスペクター ウィンドウで **入力** タブを選択し、 **DefaultHoloLens2InputSystemProfile**を複製して独自のカスタマイズ可能な**入力システムプロファイル**に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="2d8cb-123">MRTK プロファイルの複製方法に関する注意事項については、「 [Mixed Reality Toolkit プロファイルの構成方法](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="2d8cb-124">2. 既定の Speech コマンドプロファイルを複製します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="2d8cb-125">**Speech**セクションを展開し、 **DefaultMixedRealitySpeechCommandsProfile**を複製して、カスタマイズ可能な独自の**Speech コマンドプロファイル**に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="2d8cb-127">3. 新しい speech コマンドを作成する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-127">3. Create a new speech command</span></span>

<span data-ttu-id="2d8cb-128">**[音声コマンド]** セクションで、 **[+ 新しい音声]** コマンドの追加 ボタンをクリックして、既存の音声コマンドの一覧の一番下に新しい speech コマンドを追加します。次に、 **[キーワード]** フィールドに適切な単語または語句を入力します。たとえば、 **[音楽の再生]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="2d8cb-130">コンピューターにマイクが搭載されていない場合に、エディター内のシミュレーションを使用して音声コマンドをテストするには、キーコードを speech コマンドに割り当てることができます。これにより、対応するキーが押されたときに、トリガーを起動することができます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="2d8cb-131">4. 音声入力ハンドラー (スクリプト) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="2d8cb-132">[階層] ウィンドウで、 **Octa**オブジェクトを選択し、 **Speech 入力ハンドラー (スクリプト)** コンポーネントを octa オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="2d8cb-133">次に、 **[フォーカスが必要]** チェックボックスをオフにして、ユーザーが speech コマンドをトリガーするために octa オブジェクトを確認する必要がないようにします。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="2d8cb-135">5. speech コマンドの応答イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="2d8cb-136">[音声入力ハンドラー (スクリプト)] コンポーネントで、[小さい **+** ] ボタンをクリックし、キーワードの一覧にキーワード要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword element to the list of keywords:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

<span data-ttu-id="2d8cb-138">新しく作成した**要素 0**をクリックして展開し、 **[キーワード]** ドロップダウンから、前の手順で作成した**Play Music**キーワードを選択します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-138">Click the newly created **Element 0** to expand it, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> <span data-ttu-id="2d8cb-140">キーワードドロップダウンのキーワードは、Speech コマンドのプロファイルにある音声コマンドリストで定義されているキーワードに基づいて設定されます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-140">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="2d8cb-141">新しい**Response ()** イベントを作成し、イベントを受信するように**octa**オブジェクトを構成し、トリガーするアクションとして**PlayOneShot**を定義し **、オーディオクリップフィールドに**適切なオーディオクリップ (たとえば、MRTK_Gem オーディオクリップ) を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-141">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> <span data-ttu-id="2d8cb-143">イベントの実装方法とオーディオクリップの割り当て方法に関する注意事項については、「[タッチ開始イベントの実装](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-143">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="2d8cb-144">パン ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="2d8cb-144">The Pan Gesture</span></span>

<span data-ttu-id="2d8cb-145">パンジェスチャは、指またはハンドを使用してコンテンツをスクロールすることでスクロールする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-145">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="2d8cb-146">この例では、まず 2D UI をスクロールし、それを展開して、3D オブジェクトのコレクションをスクロールできるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-146">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="2d8cb-147">これを実現するには、主に次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="2d8cb-148">パンに使用できるクワッドオブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-148">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="2d8cb-149">Near 相互作用 Touchable (スクリプト) コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-149">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="2d8cb-150">ハンドインタラクションのパンズーム (スクリプト) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-150">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="2d8cb-151">スクロールする2D コンテンツを追加する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-151">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="2d8cb-152">スクロールする3D コンテンツを追加する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-152">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="2d8cb-153">Move With Pan (スクリプト) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-153">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="2d8cb-154">Move With Pan (スクリプト) コンポーネントは、MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-154">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="2d8cb-155">このチュートリアルでは、このチュートリアルのアセットを提供しました。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-155">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="2d8cb-156">1. パンに使用できるクワッドオブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-156">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="2d8cb-157">[階層] ウィンドウで、空の領域を右クリックし、[ **3D オブジェクト** > **クワッド**] を選択して、四角形をシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-157">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="2d8cb-158">適切な名前 (たとえば、「 **Pangesture**) を指定し、適切な場所に配置します (例: X = 0、Y =-0.2、Z = 2)。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-158">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="2d8cb-160">3D quad などの Unity プリミティブをシーンに追加する方法については、「[キューブをシーンに追加](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene)する」の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-160">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="2d8cb-161">他の対話と同様に、パンジェスチャにも collider が必要です。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-161">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="2d8cb-162">既定では、クワッドにはメッシュ collider があります。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-162">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="2d8cb-163">ただし、メッシュ collider は非常に薄いため、理想的ではありません。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-163">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="2d8cb-164">ユーザーが collider との対話を容易にするために、メッシュ collider を box collider に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-164">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="2d8cb-165">PanGesture が選択された状態で、**メッシュ collider**コンポーネントの**設定**アイコンをクリックし、 **[コンポーネントの削除]** を選択してメッシュ Collider を削除します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-165">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="2d8cb-167">インスペクター ウィンドウで、**コンポーネントの追加** ボタンを使用して**box collider**を追加し、box の collider **Size** Z を0.15 に変更して box collider の太さを増やします。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-167">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="2d8cb-169">2. Near 相互作用 Touchable (スクリプト) コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-169">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="2d8cb-170">**Pangesture**オブジェクトが選択された状態で、 **Near 相互作用 Touchable (スクリプト)** コンポーネントを pangesture に追加します。次に、 **[境界の修正]** と センターの **[修正]** ボタンをクリックして、Near 相互作用 Touchable (スクリプト) のローカルの中心と境界のプロパティを boxcollider と一致するように更新します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-170">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="2d8cb-172">3. ハンドインタラクションのパンズーム (スクリプト) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-172">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="2d8cb-173">**Pangesture**オブジェクトが選択された状態で、**ハンドインタラクションのパンズーム (スクリプト)** コンポーネントを pangesture に追加し、[**水平**方向にロック] チェックボックスをオンにして垂直スクロールのみを許可します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-173">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="2d8cb-175">4. スクロールする2D コンテンツを追加する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-175">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="2d8cb-176">[プロジェクト] パネルで、 **Pancontent**の素材を検索し、[-] をクリックして、 **Pangesture**オブジェクトのメッシュレンダラー**マテリアル**0 プロパティにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-176">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="2d8cb-178">[インスペクター] ウィンドウで、新しく追加した**Pancontent**マテリアルコンポーネントを展開し、 **[タイル]** の Y 値を0.5 に変更します。これにより X 値が一致し、タイルが正方形で表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-178">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="2d8cb-180">ここでゲームモードに入ると、エディター内のシミュレーションでパンジェスチャを使用して、2D コンテンツのスクロールをテストできます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-180">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="2d8cb-182">5. スクロールする3D コンテンツを追加する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-182">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="2d8cb-183">[階層] ウィンドウで、 **Pangesture**オブジェクトの子オブジェクトとして**4 つのキューブを作成**し、その変換の**スケール**を X = 0.15、Y = 0.15、Z = 0.15 に設定します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-183">In the Hierarchy window, **create four cubes** as a child objects of the **PanGesture** object and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="2d8cb-185">キューブの間隔を均等にし、時間を節約するには、 **Grid オブジェクトコレクション (スクリプト)** コンポーネントをキューブの親オブジェクト (つまり、 **pangesture** ) に追加し、次のようにグリッドオブジェクトコレクション (スクリプト) を構成します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-185">To space the cubes out evenly, and save some time, add the **Grid Object Collection (Script)** component, to the cubes' parent object, i.e. the **PanGesture** object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="2d8cb-186">すべてのキューブが1つの行にアラインメントされるようにするには、 **Num Rows**を1に変更します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-186">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="2d8cb-187">**セルの幅**を0.25 に変更して、行内のキューブを空白にします。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-187">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="2d8cb-188">次に、 **[コレクションの更新]** ボタンをクリックして、新しい構成を適用します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-188">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="2d8cb-190">6. Pan (スクリプト) コンポーネントでの移動を追加する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-190">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="2d8cb-191">階層 ウィンドウで、すべての**キューブ子オブジェクト**を選択します。次に、インスペクター ウィンドウで **コンポーネントの追加** ボタンを使用して、 **Move With Pan (スクリプト)** コンポーネントをすべてのキューブに追加します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-191">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="2d8cb-193">[階層] ウィンドウで複数のオブジェクトを選択する方法に関する注意事項については、「[操作ハンドラーを追加する (スクリプト) コンポーネントをすべてのオブジェクトの命令に追加](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-193">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="2d8cb-194">すべてのキューブが選択された状態で、 **Pangesture**をクリックして、 **[パン入力ソース]** フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-194">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="2d8cb-196">各キューブの [Move With Pan (スクリプト)] コンポーネントでは、前の手順で [パン] 入力ソースとして割り当てた PanGesture の [Paninteractionpanzoom (スクリプト)] コンポーネントによって送信されたパン更新イベントをリッスンし、各キューブの位置を更新します。適切.</span><span class="sxs-lookup"><span data-stu-id="2d8cb-196">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="2d8cb-197">階層 ウィンドウで、 **Pangesture**オブジェクトを選択し、インスペクター で**メッシュレンダラー**の**チェック**ボックスをオフにして、メッシュレンダラーコンポーネントを無効にします。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-197">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="2d8cb-199">ゲームモードに入ると、エディター内のシミュレーションでパンジェスチャを使用して、3D コンテンツのスクロールをテストできます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-199">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="2d8cb-201">視線追跡</span><span class="sxs-lookup"><span data-stu-id="2d8cb-201">Eye Tracking</span></span>

<span data-ttu-id="2d8cb-202">このセクションでは、プロジェクトでアイトラッキングを有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-202">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="2d8cb-203">この例では、ユーザーの視点で見ている間に、3DObjectCollection の各オブジェクトの回転速度を低下させる機能を実装します。また、参照しているオブジェクトがエアタップまたは音声コマンドによって選択されたときにブリップが発生効果をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-203">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="2d8cb-204">これを実現するには、主に次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-204">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="2d8cb-205">すべての対象オブジェクトにアイ Tracking ターゲット (スクリプト) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-205">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="2d8cb-206">すべてのターゲットオブジェクトにアイトラッキングチュートリアルのデモ (スクリプト) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-206">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="2d8cb-207">ターゲットイベントの参照中にを実装します</span><span class="sxs-lookup"><span data-stu-id="2d8cb-207">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="2d8cb-208">選択したイベントにを実装します</span><span class="sxs-lookup"><span data-stu-id="2d8cb-208">Implement the On Selected event</span></span>
5. <span data-ttu-id="2d8cb-209">エディター内のシミュレーションのシミュレートされた目の追跡を有効にする</span><span class="sxs-lookup"><span data-stu-id="2d8cb-209">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="2d8cb-210">Visual Studio プロジェクトのアプリ機能での、宝石による入力を有効にする</span><span class="sxs-lookup"><span data-stu-id="2d8cb-210">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="2d8cb-211">1. すべてのターゲットオブジェクトにアイ Tracking ターゲット (スクリプト) コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-211">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="2d8cb-212">階層 ウィンドウで、 **3DObjectCollection**オブジェクトを展開し、すべての**子オブジェクト**を選択します。次に、インスペクター ウィンドウで **コンポーネントの追加** ボタンを使用して、すべての子オブジェクトに**視線追跡ターゲット (スクリプト)** コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-212">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="2d8cb-214">すべての**子オブジェクト**が選択された状態で、次のように**視線追跡ターゲット (スクリプト)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-214">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="2d8cb-215">選択**操作**の選択を変更**し、この**オブジェクトのエアタップアクションを select として定義します</span><span class="sxs-lookup"><span data-stu-id="2d8cb-215">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="2d8cb-216">**[音声の選択]** を展開し、[音声コマンド一覧の**サイズ**] を1に設定します。次に、表示される新しい要素の一覧で、[**要素 0** **] を [選択**] に変更し、このオブジェクトの音声コマンドアクションを [選択] として定義します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-216">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="2d8cb-218">2. すべてのターゲットオブジェクトにアイトラッキングチュートリアルのデモ (スクリプト) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-218">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="2d8cb-219">すべての**子オブジェクト**がまだ選択されている状態で、 **[コンポーネントの追加]** ボタンを使用して、すべての子オブジェクトに**アイトラッキングチュートリアルのデモ (スクリプト)** コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-219">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="2d8cb-221">アイ Tracking のターゲット (スクリプト) コンポーネントは、MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-221">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="2d8cb-222">このチュートリアルでは、このチュートリアルのアセットを提供しました。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-222">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="2d8cb-223">3. ターゲットイベントの参照中にを実装します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-223">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="2d8cb-224">階層 ウィンドウで、**チーズ** オブジェクトを選択し、 **Target ()** イベントを参照して新しいを作成します。次に、イベントを受信するように**チーズ**オブジェクトを構成し、トリガーするアクションとして**EyeTrackingTutorialDemo**を定義します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-224">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="2d8cb-226">3DObjectCollection 内の各子オブジェクトに対して、この**手順を繰り返し**ます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-226">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="2d8cb-227">イベントの実装方法に関する注意事項については、「[ハンドトラッキングジェスチャ」と「対話型 buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-227">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="2d8cb-228">4. 選択したイベントにを実装する</span><span class="sxs-lookup"><span data-stu-id="2d8cb-228">4. Implement the On Selected event</span></span>

<span data-ttu-id="2d8cb-229">階層 ウィンドウで、**チーズ** オブジェクトを選択し、**選択された**イベントを新規に作成 () イベントを作成します。次に、イベントを受信するように**チーズ**オブジェクトを構成し、トリガーされるアクションとして**EyeTrackingTutorialDemo**を定義します。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-229">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.BlipTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="2d8cb-231">3DObjectCollection 内の各子オブジェクトに対して、この**手順を繰り返し**ます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-231">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="2d8cb-232">5. エディター内のシミュレーションのシミュレートされた目の追跡を有効にする</span><span class="sxs-lookup"><span data-stu-id="2d8cb-232">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="2d8cb-233">階層] ウィンドウで **[MixedRealityToolkit]** オブジェクトを選択し、[インスペクター ウィンドウで [入力 **] タブ**を選択します。次に、入力 **[データプロバイダー]** セクションを展開し、 **[入力シミュレーションサービス]** セクションを展開し、 **DefaultMixedRealityInputSimulationProfile**を複製して独自のカスタマイズ可能な**入力シミュレーションプロファイル**に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-233">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="2d8cb-235">MRTK プロファイルの複製方法に関する注意事項については、「 [Mixed Reality Toolkit プロファイルの構成方法](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-235">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="2d8cb-236">**[目のシミュレーション]** セクションで、目の **[位置をシミュレート]** する チェックボックスをオンにして、視線追跡シミュレーションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-236">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="2d8cb-238">ゲームモードに入ると、次のようにビューを調整することで、実装したスピンとブリップが発生の効果をテストできます。これにより、カーソルがオブジェクトの1つにヒットし、手動操作または音声コマンドを使用してオブジェクトを選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-238">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="2d8cb-240">DefaultHoloLens2ConfigurationProfile を使用してカスタマイズ可能な MRTK 構成プロファイルを複製しなかった場合は、「 [Mixed Reality Toolkit の構成](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)」の手順で説明したように、プロジェクトで目の追跡が有効にならないため、有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-240">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="2d8cb-241">詳細については、「 [MRTK の監視](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)の概要」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-241">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="2d8cb-242">6. Visual Studio プロジェクトのアプリ機能で、入力を見つめて有効にする</span><span class="sxs-lookup"><span data-stu-id="2d8cb-242">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="2d8cb-243">アプリをビルドして、Visual Studio からデバイスにデプロイする前に、プロジェクトのアプリの機能で、お客様のアプリの入力が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-243">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="2d8cb-244">これには、 [HoloLens 2 命令での Unity アプリのテスト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)に従うことができます。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-244">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2d8cb-245">結論</span><span class="sxs-lookup"><span data-stu-id="2d8cb-245">Congratulations</span></span>

<span data-ttu-id="2d8cb-246">これで、アプリケーションに基本的な監視機能が追加されました。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-246">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="2d8cb-247">これらの操作は、視線追跡が持つ可能性のほんの一部にすぎません。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-247">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="2d8cb-248">このチュートリアルでは、音声コマンドやパンジェスチャなど、その他の高度な入力機能についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="2d8cb-248">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="2d8cb-249">次のレッスン: 7. 旧暦モジュールサンプルアプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="2d8cb-249">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
