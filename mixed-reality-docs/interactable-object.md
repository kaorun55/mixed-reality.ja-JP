---
title: 対話型オブジェクト
description: ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。 3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality、コントロール、対話、ui、ux
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415298"
---
# <a name="interactable-object"></a><span data-ttu-id="52a99-105">対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="52a99-105">Interactable object</span></span>

<span data-ttu-id="52a99-106">ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。</span><span class="sxs-lookup"><span data-stu-id="52a99-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="52a99-107">3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="52a99-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="52a99-108">イベントをトリガーする**対話型オブジェクト**を指定できます。</span><span class="sxs-lookup"><span data-stu-id="52a99-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="52a99-109">対話型オブジェクトは、テーブル上のコーヒーカップの任意のものとして、無線でバルーンに表示できます。</span><span class="sxs-lookup"><span data-stu-id="52a99-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="52a99-110">ダイアログ UI などの特定の状況では、従来のボタンを引き続き使用します。</span><span class="sxs-lookup"><span data-stu-id="52a99-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="52a99-111">ボタンのビジュアル表現は、コンテキストによって異なります。</span><span class="sxs-lookup"><span data-stu-id="52a99-111">The visual representation of the button depends on the context.</span></span>

![Interactible オブジェクト](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="52a99-113">対話型オブジェクトの重要なプロパティ</span><span class="sxs-lookup"><span data-stu-id="52a99-113">Important properties of the interactable object</span></span>

### <a name="visual-cue"></a><span data-ttu-id="52a99-114">ビジュアルキュー</span><span class="sxs-lookup"><span data-stu-id="52a99-114">Visual cue</span></span>

<span data-ttu-id="52a99-115">視覚的な手掛かりとは、光の形で見てきた sensory キューであり、視覚認識中にビジュアルシステムによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="52a99-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="52a99-116">ビジュアルシステムは多くの人、特に人間にとって最も重要であるため、視覚的な手掛かりは、世界の知覚に関する情報源です。</span><span class="sxs-lookup"><span data-stu-id="52a99-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="52a99-117">Mixed reality では、holographic オブジェクトは実際の環境と混合されているため、どのオブジェクトが対話型されているかを理解するのは困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="52a99-117">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="52a99-118">対話型オブジェクトについては、各入力状態の視覚的な手掛かりを区別することが重要です。</span><span class="sxs-lookup"><span data-stu-id="52a99-118">For any interactable objects in your experience, it is important to provide differentiated visual cue for each input state.</span></span> <span data-ttu-id="52a99-119">これにより、ユーザーは、エクスペリエンスのどの部分が対話型されているかを理解し、一貫性のある対話方式をユーザーに確認することができます。</span><span class="sxs-lookup"><span data-stu-id="52a99-119">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

#### <a name="far-interactions"></a><span data-ttu-id="52a99-120">遠くのやり取り</span><span class="sxs-lookup"><span data-stu-id="52a99-120">Far interactions</span></span>

<span data-ttu-id="52a99-121">ユーザーが、宝石、ハンドレイ、およびモーションコントローラーの射線と対話できるオブジェクトについては、次の3つの入力状態に対して異なる視覚的な合図を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="52a99-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>
* <span data-ttu-id="52a99-122">**既定 (監視)** :オブジェクトの既定のアイドル状態。</span><span class="sxs-lookup"><span data-stu-id="52a99-122">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="52a99-123">**対象 (ホバー)** :オブジェクトが、見つめカーソル、指近接、またはモーションコントローラーのポインターの対象になっている場合。</span><span class="sxs-lookup"><span data-stu-id="52a99-123">**Targeted (Hover)**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="52a99-124">**押さ**れました:オブジェクトがエアタップジェスチャで押されている場合、指を押すか、モーションコントローラーの [選択] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="52a99-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="52a99-125">強調表示や拡大/縮小などの手法を使用して、ユーザーの入力状態を視覚的に示すことができます。</span><span class="sxs-lookup"><span data-stu-id="52a99-125">You can use techniques such as highlighting or scaling to provide visual cue to the user’s input states.</span></span> <span data-ttu-id="52a99-126">Windows Mixed Reality では、[スタート] メニューと [アプリバー] ボタンでさまざまな入力状態を視覚化する例を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="52a99-126">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> 

<span data-ttu-id="52a99-127">![監視状態、対象状態、および押された状態を視覚化する例](images/640px-interactibleobject-states.png)</span><span class="sxs-lookup"><span data-stu-id="52a99-127">![Example of visualizing observation state, targeted state, and pressed state](images/640px-interactibleobject-states.png)</span></span><br>
<span data-ttu-id="52a99-128">*監視状態、対象状態、および押された状態を視覚化する例*</span><span class="sxs-lookup"><span data-stu-id="52a99-128">*Example of visualizing observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="52a99-129">![Holographic ボタンでの監視状態、対象状態、および押された状態](images/MRTK_InteractableState.png)</span><span class="sxs-lookup"><span data-stu-id="52a99-129">![Observation state, targeted state, and pressed state on holographic button](images/MRTK_InteractableState.png)</span></span><br>
<span data-ttu-id="52a99-130">*Holographic ボタンでの監視状態、対象状態、および押された状態*</span><span class="sxs-lookup"><span data-stu-id="52a99-130">*Observation state, targeted state, and pressed state on holographic button*</span></span>

#### <a name="neardirect-interactions"></a><span data-ttu-id="52a99-131">Near (ダイレクト) 相互作用</span><span class="sxs-lookup"><span data-stu-id="52a99-131">Near(direct) interactions</span></span>

<span data-ttu-id="52a99-132">HoloLens 2 では、オブジェクトを操作できるようにするための入力追跡入力がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="52a99-132">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="52a99-133">Haptic のフィードバックや完璧な知識を持っていない場合、オブジェクトから手の外に出てくることや、タッチしているかどうかを判断するのは困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="52a99-133">Without haptic feedback and perfect depth perception sometimes it can be hard to tell how far away your hand is from an object, or whether you are touching.</span></span> <span data-ttu-id="52a99-134">オブジェクトの状態と、特に、ホログラムとの関係を伝えるために十分な視覚的な手掛かりを提供することが重要です。</span><span class="sxs-lookup"><span data-stu-id="52a99-134">It is important to provide enough visual cues to communicate the state of the object and in particular of your hands in relation to holograms.</span></span>

<span data-ttu-id="52a99-135">視覚的フィードバックを使用して、次のことを伝えます。</span><span class="sxs-lookup"><span data-stu-id="52a99-135">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="52a99-136">**既定 (監視)** :オブジェクトの既定のアイドル状態。</span><span class="sxs-lookup"><span data-stu-id="52a99-136">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="52a99-137">**ホバー**:手がホログラムの近くにある場合は、ビジュアルを変更して、その手がホログラムをターゲットにしていることを伝えます。</span><span class="sxs-lookup"><span data-stu-id="52a99-137">**Hover**: When hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="52a99-138">**距離と操作ポイント**: 手の形でのホログラムによる取り組みとして、投影された対話ポイントと、オブジェクトから指がどの程度離れているかを伝えるフィードバックをデザインします。</span><span class="sxs-lookup"><span data-stu-id="52a99-138">**Distance and point of interaction**: As hand approaches hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="52a99-139">**連絡先の開始**:視覚エフェクトが発生したことを通知するようにビジュアル (明るい色) を変更する</span><span class="sxs-lookup"><span data-stu-id="52a99-139">**Contact Begin**: Change visuals (light, color) to communicate that touch has occured</span></span>
* <span data-ttu-id="52a99-140">**Grasped**:オブジェクトが grasped されたときのビジュアル (明るい色) を変更します。</span><span class="sxs-lookup"><span data-stu-id="52a99-140">**Grasped**: Change visuals (light, color) when the object is grasped.</span></span>
* <span data-ttu-id="52a99-141">**連絡先の終了**:タッチが終了したときにビジュアル (明るい、色) を変更します。</span><span class="sxs-lookup"><span data-stu-id="52a99-141">**Contact End**: Change visuals (light, color) when touch has ended.</span></span>

<span data-ttu-id="52a99-142">![近くの対話状態を視覚化する例](images/640px-interactibleobject-states-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="52a99-142">![Example of visualizing near interaction states](images/640px-interactibleobject-states-near.jpg)</span></span><br>
<span data-ttu-id="52a99-143">*近くの対話状態を視覚化する例*</span><span class="sxs-lookup"><span data-stu-id="52a99-143">*Example of visualizing near interaction states*</span></span>

<span data-ttu-id="52a99-144">[HoloLens 2 のボタン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)は、さまざまな入力相互作用状態を視覚化する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="52a99-144">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows the example of visualizing different input interaction states.</span></span>

<span data-ttu-id="52a99-145">![HoloLens 2 の pressable ボタンの例](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span><span class="sxs-lookup"><span data-stu-id="52a99-145">![Example of pressable button in HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span></span><br>
<span data-ttu-id="52a99-146">*HoloLens 2 の pressable ボタンの例*</span><span class="sxs-lookup"><span data-stu-id="52a99-146">*Example of pressable button in HoloLens 2*</span></span>

<span data-ttu-id="52a99-147">HoloLens 2 では、追加の視覚的な手掛かりがあるので、ユーザーの信頼度が高くなります。</span><span class="sxs-lookup"><span data-stu-id="52a99-147">In HoloLens 2, there is an additional visual cue which improves the user's confidence on the depth perception.</span></span> <span data-ttu-id="52a99-148">指先がオブジェクトに近づいたときに、指先のリングが表示され、スケールダウンされます。</span><span class="sxs-lookup"><span data-stu-id="52a99-148">The ring on the fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="52a99-149">リングは、最終的には、押された状態のドットに収束します。</span><span class="sxs-lookup"><span data-stu-id="52a99-149">The ring eventually converges into a dot on press state.</span></span> <span data-ttu-id="52a99-150">このビジュアル affordance は、ユーザーがオブジェクトからの距離を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="52a99-150">This visual affordance helps the user understand the distance from the object.</span></span>

<span data-ttu-id="52a99-151">![指先リングの視覚化](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span><span class="sxs-lookup"><span data-stu-id="52a99-151">![Fingertip ring visualization](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span></span><br>
<span data-ttu-id="52a99-152">*HoloLens 2 での指先 ring の視覚化*</span><span class="sxs-lookup"><span data-stu-id="52a99-152">*Fingertip ring visualization in HoloLens 2*</span></span>

<span data-ttu-id="52a99-153">![手書きの視覚的フィードバック](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="52a99-153">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="52a99-154">*近接境界ボックスに基づくビジュアルフィードバックの例*</span><span class="sxs-lookup"><span data-stu-id="52a99-154">*Example of visual feedback based on the proximity - Bounding box*</span></span>


### <a name="audio-cue"></a><span data-ttu-id="52a99-155">オーディオキュー</span><span class="sxs-lookup"><span data-stu-id="52a99-155">Audio cue</span></span>
<span data-ttu-id="52a99-156">直接の対話では、適切なオーディオフィードバックによってユーザーエクスペリエンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="52a99-156">For the direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="52a99-157">オーディオフィードバックを使用して、次のことを伝えます。</span><span class="sxs-lookup"><span data-stu-id="52a99-157">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="52a99-158">**連絡先の開始**:タッチの開始時にサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="52a99-158">**Contact begin**: Play sound when touch begins</span></span>
* <span data-ttu-id="52a99-159">**連絡先の終了**:タッチエンドでサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="52a99-159">**Contact end**: Play sound on touch end</span></span>
* <span data-ttu-id="52a99-160">**グラブ開始**:グラブの開始時にサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="52a99-160">**Grab begin**: Play sound when grab starts</span></span>
* <span data-ttu-id="52a99-161">**グラブの終了**:グラブ終了時にサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="52a99-161">**Grab end**: Play sound on grab end</span></span>

### <a name="voice-command"></a><span data-ttu-id="52a99-162">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="52a99-162">Voice command</span></span>
<span data-ttu-id="52a99-163">対話型オブジェクトについては、代替の対話オプションをサポートすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="52a99-163">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="52a99-164">既定では、対話型されているすべてのオブジェクトに対して音声コマンドをサポートすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="52a99-164">In default, it is recommended to support voice command for any objects that are interactable.</span></span> <span data-ttu-id="52a99-165">検索性を向上させるために、ホバー状態のヒントを提供できます。</span><span class="sxs-lookup"><span data-stu-id="52a99-165">To improve the discoverability, you can provide tooltip on hover state.</span></span>

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="音声コマンドのツールヒント" width="350"><br/><span data-ttu-id="52a99-167">*音声コマンドのツールヒント*</span><span class="sxs-lookup"><span data-stu-id="52a99-167">*Tooltip for the voice command*</span></span>

## <a name="sizing"></a><span data-ttu-id="52a99-168">サイズ変更</span><span class="sxs-lookup"><span data-stu-id="52a99-168">Sizing</span></span>
<span data-ttu-id="52a99-169">すべての対話型オブジェクトをユーザーが簡単に操作できるようにするには、ユーザーからの距離に基づいて、対話型が最小サイズ (視覚的な弧の角度で測定されることが多い) を満たしていることを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="52a99-169">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="52a99-170">視覚的な角度は、ユーザーの視点とオブジェクトの間の距離に基づいており、一定のままになります。一方、ターゲットの物理的なサイズは、ユーザーからの距離が変化すると変化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="52a99-170">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="52a99-171">ユーザーからの距離に基づいてオブジェクトの必要な物理サイズを判断するには、[この](http://elvers.us/perception/visualAngle/)ような視覚的な角度計算ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="52a99-171">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](http://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="52a99-172">対話型コンテンツの最小サイズに関する推奨事項を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="52a99-172">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="52a99-173">ダイレクトハンド操作のターゲットサイズ</span><span class="sxs-lookup"><span data-stu-id="52a99-173">Target size for direct hand interaction</span></span>
| <span data-ttu-id="52a99-174">単位</span><span class="sxs-lookup"><span data-stu-id="52a99-174">Distance</span></span> | <span data-ttu-id="52a99-175">表示角度</span><span class="sxs-lookup"><span data-stu-id="52a99-175">Viewing angle</span></span> | <span data-ttu-id="52a99-176">サイズ</span><span class="sxs-lookup"><span data-stu-id="52a99-176">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="52a99-177">45cm</span><span class="sxs-lookup"><span data-stu-id="52a99-177">45cm</span></span>  | <span data-ttu-id="52a99-178">2°未満</span><span class="sxs-lookup"><span data-stu-id="52a99-178">no smaller than 2°</span></span> | <span data-ttu-id="52a99-179">1.6 x 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="52a99-179">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="52a99-180">![ダイレクトハンド操作のターゲットサイズ](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="52a99-180">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="52a99-181">*ダイレクトハンド操作のターゲットサイズ*</span><span class="sxs-lookup"><span data-stu-id="52a99-181">*Target size for direct hand interaction*</span></span>

<span data-ttu-id="52a99-182">直接対話するためのボタンを作成する場合は、3.2 x 3.2 cm の最小サイズを大きくすることをお勧めします。これにより、アイコンと、場合によってはテキスト \* \* を格納するのに十分な領域が確保されます。</span><span class="sxs-lookup"><span data-stu-id="52a99-182">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text\*\*</span></span>

| <span data-ttu-id="52a99-183">単位</span><span class="sxs-lookup"><span data-stu-id="52a99-183">Distance</span></span> | <span data-ttu-id="52a99-184">最小サイズ</span><span class="sxs-lookup"><span data-stu-id="52a99-184">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="52a99-185">45cm</span><span class="sxs-lookup"><span data-stu-id="52a99-185">45cm</span></span>  | <span data-ttu-id="52a99-186">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="52a99-186">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="52a99-187">![ボタンのターゲットサイズ](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="52a99-187">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="52a99-188">*ボタンのターゲットサイズ*</span><span class="sxs-lookup"><span data-stu-id="52a99-188">*Target size for the buttons*</span></span>


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="52a99-189">ハンドレイまたは宝石の相互作用の目標サイズ</span><span class="sxs-lookup"><span data-stu-id="52a99-189">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="52a99-190">単位</span><span class="sxs-lookup"><span data-stu-id="52a99-190">Distance</span></span> | <span data-ttu-id="52a99-191">表示角度</span><span class="sxs-lookup"><span data-stu-id="52a99-191">Viewing angle</span></span> | <span data-ttu-id="52a99-192">サイズ</span><span class="sxs-lookup"><span data-stu-id="52a99-192">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="52a99-193">2分</span><span class="sxs-lookup"><span data-stu-id="52a99-193">2m</span></span>  | <span data-ttu-id="52a99-194">1°未満</span><span class="sxs-lookup"><span data-stu-id="52a99-194">no smaller than 1°</span></span> | <span data-ttu-id="52a99-195">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="52a99-195">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="52a99-196">![ハンドレイまたは宝石の相互作用の目標サイズ](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="52a99-196">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="52a99-197">*ハンドレイまたは宝石の相互作用の目標サイズ*</span><span class="sxs-lookup"><span data-stu-id="52a99-197">*Target size for hand ray or gaze interaction*</span></span>

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="52a99-198">Mixed Reality Toolkit (MRTK) を使用した対話型オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="52a99-198">Creating interactable object with Mixed Reality Toolkit (MRTK)</span></span>

<span data-ttu-id="52a99-199">**[混合 Reality ツールキット](https://github.com/Microsoft/MixedRealityToolkit-Unity)** では、対話型オブジェクトの作成に役立つ一連の Unity スクリプトと prefabs を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="52a99-199">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can find the series of Unity scripts and prefabs that will help you create interactable objects.</span></span> <span data-ttu-id="52a99-200">これらを使用すると、さまざまな種類の入力相互作用状態にオブジェクトを応答させることができます。</span><span class="sxs-lookup"><span data-stu-id="52a99-200">You can use these to make objects respond to various types of input interaction states.</span></span>

* [<span data-ttu-id="52a99-201">対話型</span><span class="sxs-lookup"><span data-stu-id="52a99-201">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="52a99-202">Button</span><span class="sxs-lookup"><span data-stu-id="52a99-202">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="52a99-203">ハンド操作の例シーン</span><span class="sxs-lookup"><span data-stu-id="52a99-203">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="52a99-204">MixedRealityToolkit の標準シェーダーには、ビジュアルおよびオーディオキューを作成するのに役立つ**近接光**などのさまざまなオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="52a99-204">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="52a99-205">MRTK 標準シェーダー</span><span class="sxs-lookup"><span data-stu-id="52a99-205">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a><span data-ttu-id="52a99-206">関連項目</span><span class="sxs-lookup"><span data-stu-id="52a99-206">See also</span></span>

* [<span data-ttu-id="52a99-207">境界ボックス</span><span class="sxs-lookup"><span data-stu-id="52a99-207">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="52a99-208">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="52a99-208">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="52a99-209">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="52a99-209">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)