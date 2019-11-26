---
title: 対話型オブジェクト
description: ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。 3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality、コントロール、対話、ui、ux
ms.openlocfilehash: 73c8a3ce9e01f580ecbae23f2178871642c4540e
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143258"
---
# <a name="interactable-object"></a><span data-ttu-id="ed7a9-105">対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="ed7a9-105">Interactable object</span></span>

![Interactible オブジェクト](images/UX/UX_Hero_Interactable.jpg)

<span data-ttu-id="ed7a9-107">ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="ed7a9-108">3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="ed7a9-109">イベントをトリガーする**対話型オブジェクト**を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="ed7a9-110">対話型オブジェクトは、テーブル上のコーヒーカップの任意のものとして、無線でバルーンに表示できます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-110">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="ed7a9-111">ダイアログ UI などの特定の状況では、従来のボタンを引き続き使用します。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="ed7a9-112">ボタンのビジュアル表現は、コンテキストによって異なります。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-112">The visual representation of the button depends on the context.</span></span>

<br>

---


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="ed7a9-113">対話型オブジェクトの重要なプロパティ</span><span class="sxs-lookup"><span data-stu-id="ed7a9-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="ed7a9-114">視覚的な合図</span><span class="sxs-lookup"><span data-stu-id="ed7a9-114">Visual cues</span></span>

<span data-ttu-id="ed7a9-115">視覚的な手掛かりとは、光の形で見てきた sensory キューであり、視覚認識中にビジュアルシステムによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="ed7a9-116">ビジュアルシステムは多くの人、特に人間にとって最も重要であるため、視覚的な手掛かりは、世界の知覚に関する情報源です。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="ed7a9-117">Holographic オブジェクトは、mixed reality の実際の環境とブレンドされるため、対話できるオブジェクトを理解するのが困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="ed7a9-118">対話型オブジェクトについては、各入力状態の視覚的な手掛かりを区別することが重要です。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-118">For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="ed7a9-119">これにより、ユーザーは、エクスペリエンスのどの部分が対話型されているかを理解し、一貫性のある対話方式を使用してユーザーの信頼を得られるようになります。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="ed7a9-120">遠くのやり取り</span><span class="sxs-lookup"><span data-stu-id="ed7a9-120">Far interactions</span></span>

<span data-ttu-id="ed7a9-121">ユーザーが、宝石、ハンドレイ、およびモーションコントローラーの射線と対話できるオブジェクトについては、次の3つの入力状態に対して異なる視覚的な合図を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="ed7a9-122">![interactibleobject-既定](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="ed7a9-123">**既定 (監視) の状態**</span><span class="sxs-lookup"><span data-stu-id="ed7a9-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="ed7a9-124">オブジェクトの既定のアイドル状態。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-124">Default idle state of the object.</span></span>
    <span data-ttu-id="ed7a9-125">カーソルがオブジェクト上にありません。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-125">The cursor is not on the object.</span></span> <span data-ttu-id="ed7a9-126">ハンドが検出されません。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-126">Hand is not detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ed7a9-127">![interactibleobject-対象](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="ed7a9-128">**ターゲット (ホバー) 状態**</span><span class="sxs-lookup"><span data-stu-id="ed7a9-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="ed7a9-129">オブジェクトが、見つめカーソル、指近接、またはモーションコントローラーのポインターの対象になっている場合。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="ed7a9-130">カーソルがオブジェクト上にあります。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-130">The cursor is on the object.</span></span> <span data-ttu-id="ed7a9-131">ハンドが検出され、準備が完了しました。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ed7a9-132">![interactibleobject-押された](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="ed7a9-133">**押された状態**</span><span class="sxs-lookup"><span data-stu-id="ed7a9-133">**Pressed state**</span></span><br>
        <span data-ttu-id="ed7a9-134">オブジェクトがエアタップジェスチャで押されたときに、指を押すか、モーションコントローラーの [選択] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="ed7a9-135">カーソルがオブジェクト上にあります。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-135">The cursor is on the object.</span></span> <span data-ttu-id="ed7a9-136">ハンドが検出されました。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="ed7a9-137">強調表示や拡大/縮小などの手法を使用して、ユーザーの入力状態を視覚的に示すことができます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="ed7a9-138">Mixed reality では、[スタート] メニューとアプリバーボタンを使用してさまざまな入力状態を視覚化する例を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-138">In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="ed7a9-139">**Holographic ボタン**では、次のような状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-139">Here is what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="ed7a9-140">![interactibleobject-既定](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="ed7a9-141">**既定 (監視) の状態**</span><span class="sxs-lookup"><span data-stu-id="ed7a9-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ed7a9-142">![interactibleobject-対象](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="ed7a9-143">**ターゲット (ホバー) 状態**</span><span class="sxs-lookup"><span data-stu-id="ed7a9-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ed7a9-144">![interactibleobject-押された](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="ed7a9-145">**押された状態**</span><span class="sxs-lookup"><span data-stu-id="ed7a9-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="ed7a9-146">Near 相互作用 (ダイレクト)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-146">Near interactions (direct)</span></span> 

<span data-ttu-id="ed7a9-147">HoloLens 2 では、オブジェクトを操作できるようにするための入力追跡入力がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-147">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="ed7a9-148">Haptic のフィードバックや完全な深さの認識がなければ、オブジェクトから手の外に出てきたことや、それに触れているかどうかを判断するのは難しい場合があります。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-148">Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it.</span></span> <span data-ttu-id="ed7a9-149">オブジェクトの状態と、特にそのオブジェクトに対する実際の状態を伝えるのに十分な視覚的な手掛かりを提供することが重要です。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-149">It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.</span></span>

<span data-ttu-id="ed7a9-150">視覚的フィードバックを使用して、次のことを伝えます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-150">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="ed7a9-151">**既定 (監視)** : オブジェクトの既定のアイドル状態。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-151">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="ed7a9-152">**ホバー**: 手がホログラムの近くにある場合は、ビジュアルを変更して、その手がホログラムをターゲットとしていることを伝えます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="ed7a9-153">**距離とポイントとの相互作用**: 手がホログラムに近づいたときに、投影された相互作用ポイントと、オブジェクトから指がどこまでの距離であるかを伝えるフィードバックをデザインします。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="ed7a9-154">**連絡先の開始**: ビジュアル (明るい色) を変更して、タッチが発生したことを通知します</span><span class="sxs-lookup"><span data-stu-id="ed7a9-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="ed7a9-155">**Grasped**: オブジェクトが Grasped の場合にビジュアル (明るい、色) を変更します。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-155">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="ed7a9-156">**連絡先の終了**: タッチが終了したときのビジュアル (明るい、色) を変更します</span><span class="sxs-lookup"><span data-stu-id="ed7a9-156">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="ed7a9-157">ホバー (遠く)](images/640px-interactibleobject-states-near-hover.jpg) ![</span><span class="sxs-lookup"><span data-stu-id="ed7a9-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="ed7a9-158">**ホバー (遠く)**</span><span class="sxs-lookup"><span data-stu-id="ed7a9-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="ed7a9-159">手書きの距離に基づいて強調表示します。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ed7a9-160">ホバー (Near)](images/640px-interactibleobject-states-near-hovernear.jpg) ![</span><span class="sxs-lookup"><span data-stu-id="ed7a9-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="ed7a9-161">**ホバー (Near)**</span><span class="sxs-lookup"><span data-stu-id="ed7a9-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="ed7a9-162">ハンドの距離に応じてサイズの変化を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="ed7a9-163">![タッチ/押し](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="ed7a9-164">**タッチ/押す**</span><span class="sxs-lookup"><span data-stu-id="ed7a9-164">**Touch / press**</span></span><br>
        <span data-ttu-id="ed7a9-165">ビジュアルとオーディオフィードバック。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ed7a9-166">](images/640px-interactibleobject-states-near-grasp.jpg) を把握 ![</span><span class="sxs-lookup"><span data-stu-id="ed7a9-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="ed7a9-167">**つかん**</span><span class="sxs-lookup"><span data-stu-id="ed7a9-167">**Grasp**</span></span><br>
        <span data-ttu-id="ed7a9-168">ビジュアルとオーディオフィードバック。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="ed7a9-169">[HoloLens 2 のボタン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)は、さまざまな入力相互作用状態を視覚化する方法の例です。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="ed7a9-170">![[Default]](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="ed7a9-171">**[Default]**</span><span class="sxs-lookup"><span data-stu-id="ed7a9-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ed7a9-172">ホバー](images/640px-interactibleobject-pressablebutton-hover.jpg) ![</span><span class="sxs-lookup"><span data-stu-id="ed7a9-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="ed7a9-173">**マウス**</span><span class="sxs-lookup"><span data-stu-id="ed7a9-173">**Hover**</span></span><br>
        <span data-ttu-id="ed7a9-174">距離に基づく光源効果を表示します。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="ed7a9-175">![タッチ](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="ed7a9-176">**タッチ**</span><span class="sxs-lookup"><span data-stu-id="ed7a9-176">**Touch**</span></span><br>
        <span data-ttu-id="ed7a9-177">Ripple 効果を表示します。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ed7a9-178">![押す](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <bpt id="p1">**</bpt>Press<ept id="p1">**</ept><br>
        <span data-ttu-id="ed7a9-180">前面プレートを移動します。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="ed7a9-181">HoloLens 2 の "リング" ビジュアルキュー</span><span class="sxs-lookup"><span data-stu-id="ed7a9-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="ed7a9-182">HoloLens 2 では、ユーザーが深さを認識できるようにするための視覚的な手掛かりが追加されています。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-182">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="ed7a9-183">指先がオブジェクトに近づいたときに、指先の近くにあるリングが表示され、スケールダウンされます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="ed7a9-184">このリングは、押された状態に達したときに、最終的にドットに収束します。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="ed7a9-185">このビジュアル affordance は、オブジェクトからの距離をユーザーが理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="ed7a9-186">*ビデオループ: 境界ボックスとの近接度に基づくビジュアルフィードバックの例*</span><span class="sxs-lookup"><span data-stu-id="ed7a9-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="ed7a9-187">![領域](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="ed7a9-188">](images/HoloLens2_Proximity.gif) における視覚的フィードバックの ![</span><span class="sxs-lookup"><span data-stu-id="ed7a9-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="ed7a9-189">オーディオキュー</span><span class="sxs-lookup"><span data-stu-id="ed7a9-189">Audio cues</span></span>

<span data-ttu-id="ed7a9-190">直接の対話では、適切なオーディオフィードバックによってユーザーエクスペリエンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="ed7a9-191">オーディオフィードバックを使用して、次のことを伝えます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-191">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="ed7a9-192">**連絡先の開始**: タッチの開始時にサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="ed7a9-192">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="ed7a9-193">**連絡先の終了**: タッチエンドでサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="ed7a9-193">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="ed7a9-194">**グラブの開始**: グラブの開始時にサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="ed7a9-194">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="ed7a9-195">**グラブ端**: グラブ終了時にサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="ed7a9-195">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="ed7a9-196">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="ed7a9-196">Voice commanding</span></span><br>
        <span data-ttu-id="ed7a9-197">対話型オブジェクトについては、代替の対話オプションをサポートすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-197">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="ed7a9-198">既定では、対話型されているすべてのオブジェクトに対して、[音声コマンド](voice-design.md)をサポートすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-198">By default, we recommend that [voice commanding](voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="ed7a9-199">見つけやすさを向上させるために、ホバー状態のときにツールヒントを提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="ed7a9-200">*イメージ: 音声コマンドのツールヒント*</span><span class="sxs-lookup"><span data-stu-id="ed7a9-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![音声によるコマンド](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="ed7a9-202">サイズ設定の推奨事項</span><span class="sxs-lookup"><span data-stu-id="ed7a9-202">Sizing recommendations</span></span> 

<span data-ttu-id="ed7a9-203">すべての対話型オブジェクトをユーザーが簡単に操作できるようにするには、ユーザーからの距離に基づいて、対話型が最小サイズ (視覚的な弧の角度で測定されることが多い) を満たしていることを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-203">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="ed7a9-204">視覚的な角度は、ユーザーの視点とオブジェクトの間の距離に基づいており、一定のままになります。一方、ターゲットの物理的なサイズは、ユーザーからの距離が変化すると変化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-204">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="ed7a9-205">ユーザーからの距離に基づいてオブジェクトの必要な物理サイズを判断するには、[この](https://elvers.us/perception/visualAngle/)ような視覚的な角度計算ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="ed7a9-206">対話型コンテンツの最小サイズに関する推奨事項を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="ed7a9-207">ダイレクトハンド操作のターゲットサイズ</span><span class="sxs-lookup"><span data-stu-id="ed7a9-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="ed7a9-208">単位</span><span class="sxs-lookup"><span data-stu-id="ed7a9-208">Distance</span></span> | <span data-ttu-id="ed7a9-209">表示角度</span><span class="sxs-lookup"><span data-stu-id="ed7a9-209">Viewing angle</span></span> | <span data-ttu-id="ed7a9-210">サイズ</span><span class="sxs-lookup"><span data-stu-id="ed7a9-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="ed7a9-211">45cm</span><span class="sxs-lookup"><span data-stu-id="ed7a9-211">45cm</span></span>  | <span data-ttu-id="ed7a9-212">2°未満</span><span class="sxs-lookup"><span data-stu-id="ed7a9-212">no smaller than 2°</span></span> | <span data-ttu-id="ed7a9-213">1.6 x 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="ed7a9-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="ed7a9-214">ダイレクトハンド操作の ![の目標サイズ](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="ed7a9-215">*ダイレクトハンド操作のターゲットサイズ*</span><span class="sxs-lookup"><span data-stu-id="ed7a9-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="ed7a9-216">ボタンのターゲットサイズ</span><span class="sxs-lookup"><span data-stu-id="ed7a9-216">Target size for buttons</span></span>

<span data-ttu-id="ed7a9-217">直接対話するためのボタンを作成する場合は、3.2 x 3.2 cm の最小サイズを大きくすることをお勧めします。これにより、アイコンと一部のテキストを格納するための十分な領域が確保されます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="ed7a9-218">単位</span><span class="sxs-lookup"><span data-stu-id="ed7a9-218">Distance</span></span> | <span data-ttu-id="ed7a9-219">最小サイズ</span><span class="sxs-lookup"><span data-stu-id="ed7a9-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="ed7a9-220">45cm</span><span class="sxs-lookup"><span data-stu-id="ed7a9-220">45cm</span></span>  | <span data-ttu-id="ed7a9-221">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="ed7a9-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="ed7a9-222">ボタンの目標サイズを ![](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="ed7a9-223">*ボタンのターゲットサイズ*</span><span class="sxs-lookup"><span data-stu-id="ed7a9-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="ed7a9-224">ハンドレイまたは宝石の相互作用の目標サイズ</span><span class="sxs-lookup"><span data-stu-id="ed7a9-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="ed7a9-225">単位</span><span class="sxs-lookup"><span data-stu-id="ed7a9-225">Distance</span></span> | <span data-ttu-id="ed7a9-226">表示角度</span><span class="sxs-lookup"><span data-stu-id="ed7a9-226">Viewing angle</span></span> | <span data-ttu-id="ed7a9-227">サイズ</span><span class="sxs-lookup"><span data-stu-id="ed7a9-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="ed7a9-228">2分</span><span class="sxs-lookup"><span data-stu-id="ed7a9-228">2m</span></span>  | <span data-ttu-id="ed7a9-229">1°未満</span><span class="sxs-lookup"><span data-stu-id="ed7a9-229">no smaller than 1°</span></span> | <span data-ttu-id="ed7a9-230">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="ed7a9-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="ed7a9-231">ハンドレイまたは宝石による相互作用の目標サイズ ![](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="ed7a9-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="ed7a9-232">*ハンドレイまたは宝石の相互作用の目標サイズ*</span><span class="sxs-lookup"><span data-stu-id="ed7a9-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtkmixed-reality-toolkit-for-unit"></a><span data-ttu-id="ed7a9-233">Unit 用の MRTK (Mixed Reality Toolkit) の対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="ed7a9-233">Interactable object in MRTK(Mixed Reality Toolkit) for Unit</span></span>

<span data-ttu-id="ed7a9-234">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** では、スクリプト[**対話型**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts)を使用して、オブジェクトがさまざまな種類の入力相互作用状態に応答するようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="ed7a9-235">さまざまな種類のテーマをサポートしており、色、サイズ、素材、シェーダーなどのオブジェクトプロパティを制御することにより、視覚的な状態を定義できます。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-235">It supports various types of themes that allows you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="ed7a9-236">対話型</span><span class="sxs-lookup"><span data-stu-id="ed7a9-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="ed7a9-237">Button</span><span class="sxs-lookup"><span data-stu-id="ed7a9-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="ed7a9-238">ハンド操作の例シーン</span><span class="sxs-lookup"><span data-stu-id="ed7a9-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="ed7a9-239">MixedRealityToolkit の標準シェーダーには、ビジュアルおよびオーディオキューを作成するのに役立つ**近接光**などのさまざまなオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ed7a9-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="ed7a9-240">MRTK 標準シェーダー</span><span class="sxs-lookup"><span data-stu-id="ed7a9-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="ed7a9-241">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed7a9-241">See also</span></span>

* [<span data-ttu-id="ed7a9-242">カーソル</span><span class="sxs-lookup"><span data-stu-id="ed7a9-242">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="ed7a9-243">ハンドレイ</span><span class="sxs-lookup"><span data-stu-id="ed7a9-243">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="ed7a9-244">Button</span><span class="sxs-lookup"><span data-stu-id="ed7a9-244">Button</span></span>](button.md)
* [<span data-ttu-id="ed7a9-245">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="ed7a9-245">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="ed7a9-246">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="ed7a9-246">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="ed7a9-247">操作性</span><span class="sxs-lookup"><span data-stu-id="ed7a9-247">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ed7a9-248">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="ed7a9-248">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="ed7a9-249">Near メニュー</span><span class="sxs-lookup"><span data-stu-id="ed7a9-249">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="ed7a9-250">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="ed7a9-250">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="ed7a9-251">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="ed7a9-251">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="ed7a9-252">キーボード</span><span class="sxs-lookup"><span data-stu-id="ed7a9-252">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="ed7a9-253">ボタン</span><span class="sxs-lookup"><span data-stu-id="ed7a9-253">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="ed7a9-254">翻訳</span><span class="sxs-lookup"><span data-stu-id="ed7a9-254">Slate</span></span>](slate.md)
* [<span data-ttu-id="ed7a9-255">スライダー</span><span class="sxs-lookup"><span data-stu-id="ed7a9-255">Slider</span></span>](slider.md)
* [<span data-ttu-id="ed7a9-256">シェーダー</span><span class="sxs-lookup"><span data-stu-id="ed7a9-256">Shader</span></span>](shader.md)
* [<span data-ttu-id="ed7a9-257">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="ed7a9-257">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="ed7a9-258">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="ed7a9-258">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="ed7a9-259">表面の吸着</span><span class="sxs-lookup"><span data-stu-id="ed7a9-259">Surface magnetism</span></span>](surface-magnetism.md)
