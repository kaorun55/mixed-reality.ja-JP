---
title: 対話型のオブジェクト
description: ボタンには、2 D 抽象世界でイベントをトリガーに使用されるメタファが長年です。 3 次元の複合現実の世界では、この抽象化はもはやの世界に限定しました必要はありません。
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality、コントロール、相互作用、ui、ux
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415298"
---
# <a name="interactable-object"></a><span data-ttu-id="50be9-105">対話型のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="50be9-105">Interactable object</span></span>

<span data-ttu-id="50be9-106">ボタンには、2 D 抽象世界でイベントをトリガーに使用されるメタファが長年です。</span><span class="sxs-lookup"><span data-stu-id="50be9-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="50be9-107">3 次元の複合現実の世界では、この抽象化はもはやの世界に限定しました必要はありません。</span><span class="sxs-lookup"><span data-stu-id="50be9-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="50be9-108">何もすることができます、**対話型のオブジェクト**イベントをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="50be9-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="50be9-109">対話型のオブジェクトは、そのテーブルに、コーヒー カップから空中に浮かんでバルーンをものとして表現できます。</span><span class="sxs-lookup"><span data-stu-id="50be9-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="50be9-110">引き続き行うことで特定の状況はダイアログの UI などの従来のボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="50be9-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="50be9-111">ボタンの視覚的表現は、コンテキストによって異なります。</span><span class="sxs-lookup"><span data-stu-id="50be9-111">The visual representation of the button depends on the context.</span></span>

![Interactible オブジェクト](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="50be9-113">対話型のオブジェクトの重要なプロパティ</span><span class="sxs-lookup"><span data-stu-id="50be9-113">Important properties of the interactable object</span></span>

### <a name="visual-cue"></a><span data-ttu-id="50be9-114">視覚的な合図</span><span class="sxs-lookup"><span data-stu-id="50be9-114">Visual cue</span></span>

<span data-ttu-id="50be9-115">視覚的な手掛かりは、ライトの形式で目によって受信され、視覚認識の中に visual システムによって処理される感覚的な手掛かりです。</span><span class="sxs-lookup"><span data-stu-id="50be9-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="50be9-116">Species 多く、特にの人間では、ビジュアルのシステムから視覚的な手掛かりは、世界を認識する方法の情報の大規模な源です。</span><span class="sxs-lookup"><span data-stu-id="50be9-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="50be9-117">複合現実で holographic オブジェクトは、実際の環境とが混在しているため困難になることな対話型のオブジェクトを理解します。</span><span class="sxs-lookup"><span data-stu-id="50be9-117">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="50be9-118">お客様のエクスペリエンスで対話型のオブジェクトの状態を各入力に差別化された視覚的な合図を提供する重要なは。</span><span class="sxs-lookup"><span data-stu-id="50be9-118">For any interactable objects in your experience, it is important to provide differentiated visual cue for each input state.</span></span> <span data-ttu-id="50be9-119">これにより、ユーザーのエクスペリエンスの部分が対話型と一貫性のある相互作用方式で確実に、ユーザーは、理解できます。</span><span class="sxs-lookup"><span data-stu-id="50be9-119">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

#### <a name="far-interactions"></a><span data-ttu-id="50be9-120">ここまでの相互作用</span><span class="sxs-lookup"><span data-stu-id="50be9-120">Far interactions</span></span>

<span data-ttu-id="50be9-121">任意のオブジェクトにそのユーザーおよび操作できます視線の先、手の形のレイ モーション コント ローラーのレイをお勧めこれら 3 つの入力の状態の別の視覚的に。</span><span class="sxs-lookup"><span data-stu-id="50be9-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>
* <span data-ttu-id="50be9-122">**既定 (監視)** :オブジェクトの既定のアイドル状態です。</span><span class="sxs-lookup"><span data-stu-id="50be9-122">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="50be9-123">**対象となる (ホバー)** :オブジェクトは視線の先のカーソルにターゲットになると、本の指近接やアニメーション コント ローラーのポインター。</span><span class="sxs-lookup"><span data-stu-id="50be9-123">**Targeted (Hover)**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="50be9-124">**押された**:オブジェクトをエア タップ ジェスチャや指キーを押してモーション コント ローラーの [選択] ボタンを押したときにします。</span><span class="sxs-lookup"><span data-stu-id="50be9-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="50be9-125">強調表示機能やスケーリングなどの手法を使用すると、ユーザーの入力の状態を視覚的な合図を提供します。</span><span class="sxs-lookup"><span data-stu-id="50be9-125">You can use techniques such as highlighting or scaling to provide visual cue to the user’s input states.</span></span> <span data-ttu-id="50be9-126">Windows Mixed Reality では、[スタート] メニューおよびアプリ バー ボタンのさまざまな入力の状態を視覚化の例が見つかります。</span><span class="sxs-lookup"><span data-stu-id="50be9-126">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> 

<span data-ttu-id="50be9-127">![監視状態を視覚化するための例は、状態、対象とし、状態の押されました。](images/640px-interactibleobject-states.png)</span><span class="sxs-lookup"><span data-stu-id="50be9-127">![Example of visualizing observation state, targeted state, and pressed state](images/640px-interactibleobject-states.png)</span></span><br>
<span data-ttu-id="50be9-128">*監視状態を視覚化するための例は、状態、対象とし、状態の押されました。*</span><span class="sxs-lookup"><span data-stu-id="50be9-128">*Example of visualizing observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="50be9-129">![監視の状態、状態、対象となるおよび holographic ボタンの状態を押した](images/MRTK_InteractableState.png)</span><span class="sxs-lookup"><span data-stu-id="50be9-129">![Observation state, targeted state, and pressed state on holographic button](images/MRTK_InteractableState.png)</span></span><br>
<span data-ttu-id="50be9-130">*監視の状態、状態、対象となるおよび holographic ボタンの状態を押した*</span><span class="sxs-lookup"><span data-stu-id="50be9-130">*Observation state, targeted state, and pressed state on holographic button*</span></span>

#### <a name="neardirect-interactions"></a><span data-ttu-id="50be9-131">Near(direct) 相互作用</span><span class="sxs-lookup"><span data-stu-id="50be9-131">Near(direct) interactions</span></span>

<span data-ttu-id="50be9-132">HoloLens 2 には、追跡オブジェクトと対話できる入力関節手がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="50be9-132">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="50be9-133">Haptic フィードバックや完璧な深さ perception もなしはオブジェクトからの手がどれほど離れてか接触するかどうかを判断することができます。</span><span class="sxs-lookup"><span data-stu-id="50be9-133">Without haptic feedback and perfect depth perception sometimes it can be hard to tell how far away your hand is from an object, or whether you are touching.</span></span> <span data-ttu-id="50be9-134">特に手ホログラムに関連するのと、オブジェクトの状態を通信するために十分な視覚的手掛かりを提供する重要です。</span><span class="sxs-lookup"><span data-stu-id="50be9-134">It is important to provide enough visual cues to communicate the state of the object and in particular of your hands in relation to holograms.</span></span>

<span data-ttu-id="50be9-135">次の通信に視覚的なフィードバックを使用します。</span><span class="sxs-lookup"><span data-stu-id="50be9-135">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="50be9-136">**既定 (監視)** :オブジェクトの既定のアイドル状態です。</span><span class="sxs-lookup"><span data-stu-id="50be9-136">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="50be9-137">**マウス ポインターを移動**:手の形の場合は、ほぼホログラム、手札を通信するためにビジュアルを変更すると、ホログラムが対象とします。</span><span class="sxs-lookup"><span data-stu-id="50be9-137">**Hover**: When hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="50be9-138">**相互作用のポイントとの距離**: 手が近づくホログラム、指は、オブジェクトから遠く離れた方法と、操作の射影されたポイントの通信にフィードバックをデザインします。</span><span class="sxs-lookup"><span data-stu-id="50be9-138">**Distance and point of interaction**: As hand approaches hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="50be9-139">**Begin にお問い合わせください**:そのタッチを通信するためのビジュアルの変更 (色、光) が発生しました</span><span class="sxs-lookup"><span data-stu-id="50be9-139">**Contact Begin**: Change visuals (light, color) to communicate that touch has occured</span></span>
* <span data-ttu-id="50be9-140">**文章**:変更 (色、光) のビジュアル オブジェクトを見せるとき。</span><span class="sxs-lookup"><span data-stu-id="50be9-140">**Grasped**: Change visuals (light, color) when the object is grasped.</span></span>
* <span data-ttu-id="50be9-141">**最後にお問い合わせください**:変更 (色、光) ビジュアル タッチが終了したとき。</span><span class="sxs-lookup"><span data-stu-id="50be9-141">**Contact End**: Change visuals (light, color) when touch has ended.</span></span>

<span data-ttu-id="50be9-142">![操作の状態の近くの視覚化の例](images/640px-interactibleobject-states-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="50be9-142">![Example of visualizing near interaction states](images/640px-interactibleobject-states-near.jpg)</span></span><br>
<span data-ttu-id="50be9-143">*操作の状態の近くの視覚化の例*</span><span class="sxs-lookup"><span data-stu-id="50be9-143">*Example of visualizing near interaction states*</span></span>

<span data-ttu-id="50be9-144">[HoloLens 2 ボタン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)さまざまな入力の対話操作の状態を視覚化の例を示します。</span><span class="sxs-lookup"><span data-stu-id="50be9-144">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows the example of visualizing different input interaction states.</span></span>

<span data-ttu-id="50be9-145">![HoloLens 2 pressable ボタンの例](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span><span class="sxs-lookup"><span data-stu-id="50be9-145">![Example of pressable button in HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span></span><br>
<span data-ttu-id="50be9-146">*HoloLens 2 pressable ボタンの例*</span><span class="sxs-lookup"><span data-stu-id="50be9-146">*Example of pressable button in HoloLens 2*</span></span>

<span data-ttu-id="50be9-147">HoloLens の 2 を深さ perception でユーザーの信頼度を向上させるその他の視覚的があります。</span><span class="sxs-lookup"><span data-stu-id="50be9-147">In HoloLens 2, there is an additional visual cue which improves the user's confidence on the depth perception.</span></span> <span data-ttu-id="50be9-148">指のリングでは、表示し、指がオブジェクトに近づくようにスケール ダウンします。</span><span class="sxs-lookup"><span data-stu-id="50be9-148">The ring on the fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="50be9-149">リングは、キーを押して状態でドットに最終的に収束します。</span><span class="sxs-lookup"><span data-stu-id="50be9-149">The ring eventually converges into a dot on press state.</span></span> <span data-ttu-id="50be9-150">この visual アフォー ダンスでは、ユーザーがオブジェクトからの距離を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="50be9-150">This visual affordance helps the user understand the distance from the object.</span></span>

<span data-ttu-id="50be9-151">![指先リングの視覚化](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span><span class="sxs-lookup"><span data-stu-id="50be9-151">![Fingertip ring visualization](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span></span><br>
<span data-ttu-id="50be9-152">*HoloLens 2 では、指先リングの視覚エフェクト*</span><span class="sxs-lookup"><span data-stu-id="50be9-152">*Fingertip ring visualization in HoloLens 2*</span></span>

<span data-ttu-id="50be9-153">![近接の手の形で視覚的なフィードバック](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="50be9-153">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="50be9-154">*境界ボックスの近接度に基づいて視覚的なフィードバックの例*</span><span class="sxs-lookup"><span data-stu-id="50be9-154">*Example of visual feedback based on the proximity - Bounding box*</span></span>


### <a name="audio-cue"></a><span data-ttu-id="50be9-155">オーディオ キュー</span><span class="sxs-lookup"><span data-stu-id="50be9-155">Audio cue</span></span>
<span data-ttu-id="50be9-156">直接手の相互作用の適切なオーディオをフィードバックはユーザー エクスペリエンスを大幅に向上することができます。</span><span class="sxs-lookup"><span data-stu-id="50be9-156">For the direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="50be9-157">次の通信にオーディオをフィードバックを使用します。</span><span class="sxs-lookup"><span data-stu-id="50be9-157">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="50be9-158">**連絡先の開始**:タッチの開始時にサウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="50be9-158">**Contact begin**: Play sound when touch begins</span></span>
* <span data-ttu-id="50be9-159">**連絡先の終了**:タッチ エンドでサウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="50be9-159">**Contact end**: Play sound on touch end</span></span>
* <span data-ttu-id="50be9-160">**グラブ開始**:グラブの開始時にサウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="50be9-160">**Grab begin**: Play sound when grab starts</span></span>
* <span data-ttu-id="50be9-161">**最後に取得**:グラブ エンドでサウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="50be9-161">**Grab end**: Play sound on grab end</span></span>

### <a name="voice-command"></a><span data-ttu-id="50be9-162">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="50be9-162">Voice command</span></span>
<span data-ttu-id="50be9-163">対話型のオブジェクトが別の相互作用オプションをサポートするために重要です。</span><span class="sxs-lookup"><span data-stu-id="50be9-163">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="50be9-164">既定では、対話型である任意のオブジェクトの音声コマンドをサポートすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="50be9-164">In default, it is recommended to support voice command for any objects that are interactable.</span></span> <span data-ttu-id="50be9-165">探索可能性を向上させるのには、ホバー状態のツールヒントを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="50be9-165">To improve the discoverability, you can provide tooltip on hover state.</span></span>

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="音声コマンドのツールヒント" width="350"><br/><span data-ttu-id="50be9-167">*音声コマンドのツールヒント*</span><span class="sxs-lookup"><span data-stu-id="50be9-167">*Tooltip for the voice command*</span></span>

## <a name="sizing"></a><span data-ttu-id="50be9-168">サイズ変更</span><span class="sxs-lookup"><span data-stu-id="50be9-168">Sizing</span></span>
<span data-ttu-id="50be9-169">ように対話型のすべてのオブジェクトは、ユーザーが簡単に触れることができます、確認することをお勧めします。 対話型の対応最小サイズ (多くの場合、ビジュアルの円弧の角度の単位 visual 角度)、距離に基づいて、ユーザーからファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="50be9-169">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="50be9-170">ビジュアルの角度は、ユーザーの目とオブジェクト間の距離に基づいておりは一定のまま、ターゲットの物理サイズがユーザーの変更からの距離として変更可能性があります。</span><span class="sxs-lookup"><span data-stu-id="50be9-170">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="50be9-171">ユーザーからの距離に基づくオブジェクトのために必要な物理サイズを決定するには、visual 角度計算ツールを使用してお試し[この](http://elvers.us/perception/visualAngle/)します。</span><span class="sxs-lookup"><span data-stu-id="50be9-171">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](http://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="50be9-172">対話型コンテンツの最小サイズの推奨事項を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="50be9-172">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="50be9-173">直接手の相互作用の目標サイズ</span><span class="sxs-lookup"><span data-stu-id="50be9-173">Target size for direct hand interaction</span></span>
| <span data-ttu-id="50be9-174">距離</span><span class="sxs-lookup"><span data-stu-id="50be9-174">Distance</span></span> | <span data-ttu-id="50be9-175">表示角度</span><span class="sxs-lookup"><span data-stu-id="50be9-175">Viewing angle</span></span> | <span data-ttu-id="50be9-176">サイズ</span><span class="sxs-lookup"><span data-stu-id="50be9-176">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="50be9-177">45 cm</span><span class="sxs-lookup"><span data-stu-id="50be9-177">45cm</span></span>  | <span data-ttu-id="50be9-178">2 度以上</span><span class="sxs-lookup"><span data-stu-id="50be9-178">no smaller than 2°</span></span> | <span data-ttu-id="50be9-179">1.6 × 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="50be9-179">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="50be9-180">![直接手の相互作用の目標サイズ](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="50be9-180">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="50be9-181">*直接手の相互作用の目標サイズ*</span><span class="sxs-lookup"><span data-stu-id="50be9-181">*Target size for direct hand interaction*</span></span>

<span data-ttu-id="50be9-182">確認して 3.2 x 3.2 cm の大規模な最小サイズは、アイコンを格納するための十分な領域、可能性のあるいくつかテキスト \* \* をお勧めの直接の対話のボタンを作成する場合</span><span class="sxs-lookup"><span data-stu-id="50be9-182">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text\*\*</span></span>

| <span data-ttu-id="50be9-183">距離</span><span class="sxs-lookup"><span data-stu-id="50be9-183">Distance</span></span> | <span data-ttu-id="50be9-184">最小サイズ</span><span class="sxs-lookup"><span data-stu-id="50be9-184">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="50be9-185">45 cm</span><span class="sxs-lookup"><span data-stu-id="50be9-185">45cm</span></span>  | <span data-ttu-id="50be9-186">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="50be9-186">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="50be9-187">![ターゲット サイズのボタン](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="50be9-187">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="50be9-188">*ターゲット サイズのボタン*</span><span class="sxs-lookup"><span data-stu-id="50be9-188">*Target size for the buttons*</span></span>


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="50be9-189">ターゲット光線の手の形のサイズまたは相互作用の視線</span><span class="sxs-lookup"><span data-stu-id="50be9-189">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="50be9-190">距離</span><span class="sxs-lookup"><span data-stu-id="50be9-190">Distance</span></span> | <span data-ttu-id="50be9-191">表示角度</span><span class="sxs-lookup"><span data-stu-id="50be9-191">Viewing angle</span></span> | <span data-ttu-id="50be9-192">サイズ</span><span class="sxs-lookup"><span data-stu-id="50be9-192">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="50be9-193">2 分</span><span class="sxs-lookup"><span data-stu-id="50be9-193">2m</span></span>  | <span data-ttu-id="50be9-194">1 度以上</span><span class="sxs-lookup"><span data-stu-id="50be9-194">no smaller than 1°</span></span> | <span data-ttu-id="50be9-195">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="50be9-195">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="50be9-196">![ターゲット光線の手の形のサイズまたは相互作用の視線](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="50be9-196">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="50be9-197">*ターゲット光線の手の形のサイズまたは相互作用の視線*</span><span class="sxs-lookup"><span data-stu-id="50be9-197">*Target size for hand ray or gaze interaction*</span></span>

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="50be9-198">Mixed Reality Toolkit (MRTK) との対話型のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="50be9-198">Creating interactable object with Mixed Reality Toolkit (MRTK)</span></span>

<span data-ttu-id="50be9-199">**[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 対話型のオブジェクトを作成する際に役立つプレハブ、一連の Unity のスクリプトを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="50be9-199">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can find the series of Unity scripts and prefabs that will help you create interactable objects.</span></span> <span data-ttu-id="50be9-200">これらは、オブジェクトのさまざまな種類の入力の対話操作の状態に応答を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="50be9-200">You can use these to make objects respond to various types of input interaction states.</span></span>

* [<span data-ttu-id="50be9-201">対話型</span><span class="sxs-lookup"><span data-stu-id="50be9-201">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="50be9-202">ボタン</span><span class="sxs-lookup"><span data-stu-id="50be9-202">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="50be9-203">手の形の相互作用の例のシーン</span><span class="sxs-lookup"><span data-stu-id="50be9-203">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="50be9-204">MixedRealityToolkit の標準的なシェーダーがなどのさまざまなオプションを提供します**近接 light**を視覚的およびオーディオを作成できます。</span><span class="sxs-lookup"><span data-stu-id="50be9-204">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="50be9-205">MRTK 標準シェーダー</span><span class="sxs-lookup"><span data-stu-id="50be9-205">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a><span data-ttu-id="50be9-206">関連項目</span><span class="sxs-lookup"><span data-stu-id="50be9-206">See also</span></span>

* [<span data-ttu-id="50be9-207">境界ボックス</span><span class="sxs-lookup"><span data-stu-id="50be9-207">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="50be9-208">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="50be9-208">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="50be9-209">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="50be9-209">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)