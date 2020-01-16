---
title: 手で直接操作
description: 直接操作入力モデルの概要
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 視線入力, 視線入力ターゲット設定, 対話, 設計, 手に近い, HoloLens
ms.openlocfilehash: 6811fe0b09ecff1ddc76d9df9ddc440f9c934ce3
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723251"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="0b961-104">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="0b961-104">Direct manipulation with hands</span></span>

![ボタン](images/UX/UX_Hero_Manipulation.jpg)

<span data-ttu-id="0b961-106">直接操作は、ホログラムに手で直接触れる入力モデルです。</span><span class="sxs-lookup"><span data-stu-id="0b961-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="0b961-107">この概念の背景にある考え方は、オブジェクトを現実の世界と同じように動かすことです。</span><span class="sxs-lookup"><span data-stu-id="0b961-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="0b961-108">ボタンを押してオンにしたり、オブジェクトをつかんで手に取ったりできます。2D コンテンツは仮想タッチスクリーンのように動作します。</span><span class="sxs-lookup"><span data-stu-id="0b961-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="0b961-109">このため、直接操作はユーザーにとって学びやすく、楽しくもあります。</span><span class="sxs-lookup"><span data-stu-id="0b961-109">This makes direct manipulation easy for users to learn, and fun.</span></span> <span data-ttu-id="0b961-110">直接操作は、"近接" 入力モデルと考えられており、手の届く範囲にあるコンテンツの操作に最適です。</span><span class="sxs-lookup"><span data-stu-id="0b961-110">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

<span data-ttu-id="0b961-111">直接操作はアフォーダンスをベースとしているので、操作が簡単です。</span><span class="sxs-lookup"><span data-stu-id="0b961-111">Direct manipulation is affordance-based, meaning it's user friendly.</span></span> <span data-ttu-id="0b961-112">ユーザーは象徴的なジェスチャを学ぶ必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0b961-112">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="0b961-113">すべての対話は、触ったりつかんだりできる視覚的要素を中心に構築されています。</span><span class="sxs-lookup"><span data-stu-id="0b961-113">All interactions are built around a visual element that you can touch or grab.</span></span>

## <a name="device-support"></a><span data-ttu-id="0b961-114">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="0b961-114">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="0b961-115"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="0b961-115"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="0b961-116"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="0b961-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="0b961-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="0b961-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="0b961-118"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="0b961-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="0b961-119">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="0b961-119">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="0b961-120">❌ サポート対象外</span><span class="sxs-lookup"><span data-stu-id="0b961-120">❌ Not supported</span></span></td>
     <td><span data-ttu-id="0b961-121">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="0b961-121">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="0b961-122">➕ 別の選択肢である<a href="point-and-commit.md">手を使ったポイントとコミット</a>を推奨。</span><span class="sxs-lookup"><span data-stu-id="0b961-122">➕ An alternative, <a href="point-and-commit.md">point and commit with hands</a> is recommended.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="0b961-123">直接操作は HoloLens 2 の主要な入力モデルであり、新しい多関節ハンド トラッキング システムを使用します。</span><span class="sxs-lookup"><span data-stu-id="0b961-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="0b961-124">この入力モデルは、イマーシブ ヘッドセットでもモーション コントローラー経由で利用できますが、オブジェクト操作以外の対話の主要な手段としてはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="0b961-124">The input model is also available on immersive headsets through the use of motion controllers, but is not recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="0b961-125">HoloLens (第 1 世代) では直接操作を利用できません。</span><span class="sxs-lookup"><span data-stu-id="0b961-125">Direct manipulation is not available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="0b961-126">接触可能な指先</span><span class="sxs-lookup"><span data-stu-id="0b961-126">Collidable fingertip</span></span>

<span data-ttu-id="0b961-127">HoloLens 2 では、ユーザーの手が、左右の手の骨格モデルとして認識および解釈されます。</span><span class="sxs-lookup"><span data-stu-id="0b961-127">On HoloLens 2, the user's hands are recognized and interpreted as left and right hand skeletal models.</span></span> <span data-ttu-id="0b961-128">ホログラムに直接手で触れるという概念を実現するためには、それぞれの手の骨格モデルの 5 本の指先に 5 つのコライダーを取り付けることが理想的と考えられました。</span><span class="sxs-lookup"><span data-stu-id="0b961-128">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="0b961-129">しかし、触覚的フィードバックがないため、10 本の接触可能な指先とホログラムとの間で、期待に反する予測不可能な衝突が発生してしまいました。</span><span class="sxs-lookup"><span data-stu-id="0b961-129">However, due to the lack of tactile feedback, ten collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="0b961-130">このため、両方の人差し指だけにコライダーを付けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0b961-130">Hence, we suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="0b961-131">それでも、接触可能な人差し指の指先は、下の画像に示すように、他の指を含むさまざまなタッチ ジェスチャのアクティブ タッチ ポイントとして機能します。たとえば、指 1 本で押す、指 1 本でタップ、指 2 本で押す、指 5 本で押すなどです。</span><span class="sxs-lookup"><span data-stu-id="0b961-131">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers, such as One-finger press, One-finger tap, Two-finger press and Five-finger press, as shown in the image below.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0b961-132">![接触可能な指先](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-132">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="0b961-133">**接触可能な指先**</span><span class="sxs-lookup"><span data-stu-id="0b961-133">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-134">![指 1 本で押す](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-134">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="0b961-135">**指 1 本で押す**</span><span class="sxs-lookup"><span data-stu-id="0b961-135">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-136">![指 1 本でタップ](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-136">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="0b961-137">**指 1 本でタップ**</span><span class="sxs-lookup"><span data-stu-id="0b961-137">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-138">![指 5 本で押す](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-138">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="0b961-139">**指 5 本で押す**</span><span class="sxs-lookup"><span data-stu-id="0b961-139">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="0b961-140">スフィア コライダー</span><span class="sxs-lookup"><span data-stu-id="0b961-140">Sphere collider</span></span>

<span data-ttu-id="0b961-141">ランダムな汎用シェイプを使用する代わりに、スフィア コライダーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0b961-141">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="0b961-142">そのようにすれば、スフィアを視覚的にレンダリングして、近接ターゲット設定のためのより優れた手掛かりにできます。</span><span class="sxs-lookup"><span data-stu-id="0b961-142">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="0b961-143">タッチ精度を上げるには、スフィアの直径を人差し指の太さに合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="0b961-143">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="0b961-144">hand API を呼び出すことで、指の太さの変数を簡単に取得できます。</span><span class="sxs-lookup"><span data-stu-id="0b961-144">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="0b961-145">指先カーソル</span><span class="sxs-lookup"><span data-stu-id="0b961-145">Fingertip cursor</span></span>

<span data-ttu-id="0b961-146">人差し指の指先に接触可能なスフィアをレンダリングすることに加え、高度な指先カーソルも作成されました。これにより、近接ターゲット設定のエクスペリエンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="0b961-146">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to interactively achieve a better near-targeting experience.</span></span> <span data-ttu-id="0b961-147">これは、人差し指に付随するドーナツ型のカーソルです。</span><span class="sxs-lookup"><span data-stu-id="0b961-147">It is a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="0b961-148">これは距離に応じて対象に反応して向きやサイズが変化します。詳しくは、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0b961-148">According to proximity, it dynamically reacts to a target in terms of orientation and size as detailed below:</span></span>

* <span data-ttu-id="0b961-149">人差し指をホログラムに近づけると、カーソルは常にホログラムの表面と平行になり、近づくにつれて徐々にサイズが小さくなります。</span><span class="sxs-lookup"><span data-stu-id="0b961-149">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size accordingly.</span></span>
* <span data-ttu-id="0b961-150">指が表面に触れるとカーソルは直ちにドットにまで縮小し、タッチ イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="0b961-150">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="0b961-151">次に示されているように、ユーザーは、対話型のフィードバックによって、ハイパーリンクのトリガーやボタンの押下など、高い精度で近接ターゲット設定のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0b961-151">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="0b961-152">![指先カーソル (遠い)](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-152">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="0b961-153">**指先カーソル (遠い)**</span><span class="sxs-lookup"><span data-stu-id="0b961-153">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-154">![指先カーソル (近い)](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-154">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="0b961-155">**指先カーソル (近い)**</span><span class="sxs-lookup"><span data-stu-id="0b961-155">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-156">![指先カーソル (接触)](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-156">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="0b961-157">**指先カーソル (接触)**</span><span class="sxs-lookup"><span data-stu-id="0b961-157">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="0b961-158">近接シェーダーを備えた境界ボックス</span><span class="sxs-lookup"><span data-stu-id="0b961-158">Bounding box with proximity shader</span></span>

<span data-ttu-id="0b961-159">触覚的フィードバックがないことを補うため、ホログラム自体にも視覚および音声の両方のフィードバックを提供する機能が必要です。</span><span class="sxs-lookup"><span data-stu-id="0b961-159">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="0b961-160">そこで、近接シェーダーを備えた境界ボックスという概念が考案されました。</span><span class="sxs-lookup"><span data-stu-id="0b961-160">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="0b961-161">境界ボックスは、3D オブジェクトを囲む最小の立体領域です。</span><span class="sxs-lookup"><span data-stu-id="0b961-161">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="0b961-162">境界ボックスには、近接シェーダーと呼ばれる対話的なレンダリング メカニズムがあります。</span><span class="sxs-lookup"><span data-stu-id="0b961-162">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="0b961-163">近接シェーダーは次のように動作します。</span><span class="sxs-lookup"><span data-stu-id="0b961-163">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0b961-164">![視覚的なフィードバックのホバー (遠い)](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-164">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="0b961-165">**ホバー (遠い)**</span><span class="sxs-lookup"><span data-stu-id="0b961-165">**Hover (far)**</span></span><br>
       <span data-ttu-id="0b961-166">人差し指が一定範囲内にある場合、指先スポットライトが境界ボックスの表面に投影されます。</span><span class="sxs-lookup"><span data-stu-id="0b961-166">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-167">![視覚的なフィードバックのホバー (近い)](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-167">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="0b961-168">**ホバー (近い)**</span><span class="sxs-lookup"><span data-stu-id="0b961-168">**Hover (near)**</span></span><br>
        <span data-ttu-id="0b961-169">指先が表面に近づくと、距離に応じてスポットライトが縮小します。</span><span class="sxs-lookup"><span data-stu-id="0b961-169">When the fingertip gets closer to the surface, the spotlight shrinks accordingly.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-170">![接触開始](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-170">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="0b961-171">**接触開始**</span><span class="sxs-lookup"><span data-stu-id="0b961-171">**Contact begins**</span></span><br>
       <span data-ttu-id="0b961-172">指先が表面に触れると直ちに、境界ボックス全体の色が変わったり、視覚的効果が生じたりして、タッチ状態が反映されます。</span><span class="sxs-lookup"><span data-stu-id="0b961-172">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-173">![接触終了](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-173">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="0b961-174">**接触終了**</span><span class="sxs-lookup"><span data-stu-id="0b961-174">**Contact ends**</span></span><br>
       <span data-ttu-id="0b961-175">また、効果音が鳴るようにしてタッチの視覚的フィードバックを増強できます。</span><span class="sxs-lookup"><span data-stu-id="0b961-175">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="0b961-176">押しボタン</span><span class="sxs-lookup"><span data-stu-id="0b961-176">Pressable button</span></span>

<span data-ttu-id="0b961-177">ユーザーは接触可能な指先で、押しボタンなど基本的なホログラフィック UI コンポーネントを操作できます。</span><span class="sxs-lookup"><span data-stu-id="0b961-177">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="0b961-178">押しボタンは、直接指で押せるように調整されたホログラフィック ボタンです。</span><span class="sxs-lookup"><span data-stu-id="0b961-178">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="0b961-179">押しボタンの場合もそれを押したときの感覚がないので、触覚フィードバックに関連した問題を処理するためのメカニズムがいくつか備えられています。</span><span class="sxs-lookup"><span data-stu-id="0b961-179">Again, due to the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="0b961-180">1 つ目のメカニズムは、近接シェーダーを備えた境界ボックスです。これについては、前のセクションで詳しく説明しました。</span><span class="sxs-lookup"><span data-stu-id="0b961-180">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="0b961-181">これにより、ユーザーがボタンに近づいて接触するとき、接近の感覚が向上します。</span><span class="sxs-lookup"><span data-stu-id="0b961-181">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="0b961-182">2 つ目のメカニズムは、押し下げの感覚です。</span><span class="sxs-lookup"><span data-stu-id="0b961-182">The second mechanism is depression.</span></span> <span data-ttu-id="0b961-183">押し下げの感覚により、指先がボタンに接触した後、押し下げるという感覚が生まれます。</span><span class="sxs-lookup"><span data-stu-id="0b961-183">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="0b961-184">このメカニズムは、指先と一緒に、深さ軸に沿って、重みを伴ってボタンが動くようにします。</span><span class="sxs-lookup"><span data-stu-id="0b961-184">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="0b961-185">指定された深さに達したとき (トリガー時) か、その深さを超えた後で離したとき (リリース時) にボタンをトリガーすることができます。</span><span class="sxs-lookup"><span data-stu-id="0b961-185">The button can be triggered when it reaches a designated depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="0b961-186">ボタンがトリガーされたときに効果音が鳴るようにしてフィードバックを増強する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0b961-186">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0b961-187">![押しボタン (遠い)](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-187">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="0b961-188">**指は遠く離れている**</span><span class="sxs-lookup"><span data-stu-id="0b961-188">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-189">![押しボタン (近い)](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-189">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="0b961-190">**指が近づく**</span><span class="sxs-lookup"><span data-stu-id="0b961-190">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-191">![押しボタン (接触開始)](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-191">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="0b961-192">**接触開始**</span><span class="sxs-lookup"><span data-stu-id="0b961-192">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-193">![押しボタン (押下)](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-193">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="0b961-194">**押し下げる**</span><span class="sxs-lookup"><span data-stu-id="0b961-194">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="0b961-195">2D スレートとの対話</span><span class="sxs-lookup"><span data-stu-id="0b961-195">2D slate interaction</span></span>

<span data-ttu-id="0b961-196">2D [スレート](slate.md)は、Web ブラウザーなどの 2D アプリ コンテンツをホストするホログラフィック コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="0b961-196">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="0b961-197">直接操作による 2D スレートとの対話の設計概念は、物理的なタッチ画面との対話という概念的モデルを利用するというものです。</span><span class="sxs-lookup"><span data-stu-id="0b961-197">The design concept for interacting with a 2D slate via direct manipulation is to leverage the mental model of interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="0b961-198">スレートとの接触は、次のように操作します。</span><span class="sxs-lookup"><span data-stu-id="0b961-198">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0b961-199">![タッチ](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-199">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="0b961-200">**タッチ**</span><span class="sxs-lookup"><span data-stu-id="0b961-200">**Touch**</span></span><br>
       <span data-ttu-id="0b961-201">人差し指を使ってハイパーリンクまたはボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="0b961-201">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-202">![スクロール](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-202">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="0b961-203">**スクロール**</span><span class="sxs-lookup"><span data-stu-id="0b961-203">**Scroll**</span></span><br>
        <span data-ttu-id="0b961-204">人差し指を使ってスレート コンテンツを上下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="0b961-204">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-205">![ズーム](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-205">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="0b961-206">**ズーム**</span><span class="sxs-lookup"><span data-stu-id="0b961-206">**Zoom**</span></span><br>
       <span data-ttu-id="0b961-207">ユーザーは 2 本の人差し指を使用して、指の相対的な動きに応じてスレートのコンテンツを拡大縮小します。</span><span class="sxs-lookup"><span data-stu-id="0b961-207">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="0b961-208">2D スレート本体の操作方法</span><span class="sxs-lookup"><span data-stu-id="0b961-208">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0b961-209">![移動](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-209">![Move](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="0b961-210">**移動**</span><span class="sxs-lookup"><span data-stu-id="0b961-210">**Move**</span></span><br>
       <span data-ttu-id="0b961-211">隅や端に手を動かして、一番近くにある操作アフォーダンスを表示します。</span><span class="sxs-lookup"><span data-stu-id="0b961-211">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="0b961-212">2D スレートの上部にあるホロバーをつかむことで、スレート全体を動かすことができます。</span><span class="sxs-lookup"><span data-stu-id="0b961-212">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-213">![スケール](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-213">![Scale](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="0b961-214">**スケール**</span><span class="sxs-lookup"><span data-stu-id="0b961-214">**Scale**</span></span><br>
        <span data-ttu-id="0b961-215">操作アフォーダンスをつかみ、隅のアフォーダンスで均等に拡大縮小します。</span><span class="sxs-lookup"><span data-stu-id="0b961-215">Grab the manipulation affordances and perform uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-216">![リフロー](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-216">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="0b961-217">**リフロー**</span><span class="sxs-lookup"><span data-stu-id="0b961-217">**Reflow**</span></span><br>
       <span data-ttu-id="0b961-218">操作アフォーダンスをつかみ、端のアフォーダンスでリフローを実行します。</span><span class="sxs-lookup"><span data-stu-id="0b961-218">Grab the manipulation affordances and perform reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="0b961-219">3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="0b961-219">3D object manipulation</span></span>

<span data-ttu-id="0b961-220">HoloLens 2 では、各 3D オブジェクトに境界ボックスを適用することで、ユーザーが 3D ホログラフィック オブジェクトを手で指示し、操作できます。</span><span class="sxs-lookup"><span data-stu-id="0b961-220">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="0b961-221">境界ボックスは、その近接シェーダーによって奥行きを感知しやすくします。</span><span class="sxs-lookup"><span data-stu-id="0b961-221">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="0b961-222">境界ボックスには、3D オブジェクト操作のための 2 つの設計アプローチがあります。</span><span class="sxs-lookup"><span data-stu-id="0b961-222">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="0b961-223">アフォーダンスをベースとする操作</span><span class="sxs-lookup"><span data-stu-id="0b961-223">Affordance-based manipulation</span></span>

<span data-ttu-id="0b961-224">アフォーダンスをベースとする操作により、境界ボックスとその周囲の操作アフォーダンスを通じて 3D オブジェクトを操作できます。</span><span class="sxs-lookup"><span data-stu-id="0b961-224">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="0b961-225">![移動](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-225">![Move](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="0b961-226">**移動**</span><span class="sxs-lookup"><span data-stu-id="0b961-226">**Move**</span></span><br>
       <span data-ttu-id="0b961-227">ユーザーの手が 3D オブジェクトに近づくと直ちに、境界ボックスおよび最も近いアフォーダンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0b961-227">As soon as a user's hand is close to a 3D object, the bounding box and the nearest affordance are revealed.</span></span> <span data-ttu-id="0b961-228">ユーザーは、境界ボックスをつかんでオブジェクト全体を移動できます。</span><span class="sxs-lookup"><span data-stu-id="0b961-228">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-229">![回転](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-229">![Rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="0b961-230">**回転**</span><span class="sxs-lookup"><span data-stu-id="0b961-230">**Rotate**</span></span><br>
        <span data-ttu-id="0b961-231">ユーザーは、端のアフォーダンスをつかんで回転できます。</span><span class="sxs-lookup"><span data-stu-id="0b961-231">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-232">![スケール](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-232">![Scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="0b961-233">**スケール**</span><span class="sxs-lookup"><span data-stu-id="0b961-233">**Scale**</span></span><br>
       <span data-ttu-id="0b961-234">ユーザーは、隅のアフォーダンスをつかんで均等に拡大縮小できます。</span><span class="sxs-lookup"><span data-stu-id="0b961-234">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="0b961-235">アフォーダンスをベースとしない操作</span><span class="sxs-lookup"><span data-stu-id="0b961-235">Non-affordance based manipulation</span></span>

<span data-ttu-id="0b961-236">アフォーダンスをベースとしない操作では、アフォーダンスは境界ボックスにアタッチされません。</span><span class="sxs-lookup"><span data-stu-id="0b961-236">Non-affordance-based manipulation does not attach affordance to the bounding box.</span></span> <span data-ttu-id="0b961-237">ユーザーが行えるのは、境界ボックスを表示した後、直接対話することだけです。</span><span class="sxs-lookup"><span data-stu-id="0b961-237">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="0b961-238">境界ボックスを片手でつかむと、オブジェクトの移動と回転は手の動きと向きに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="0b961-238">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="0b961-239">ユーザーがオブジェクトを両手でつかむと、両手の相対的な動きに応じてそのオブジェクトを移動、拡大縮小、回転できます。</span><span class="sxs-lookup"><span data-stu-id="0b961-239">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="0b961-240">特定の操作では正確さが求められます。</span><span class="sxs-lookup"><span data-stu-id="0b961-240">Specific manipulation requires precision.</span></span> <span data-ttu-id="0b961-241">**アフォーダンスをベースとする操作**を使用することをお勧めします。細かい調整を行うことができるためです。</span><span class="sxs-lookup"><span data-stu-id="0b961-241">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="0b961-242">融通が利く操作の場合は、**アフォーダンスをベースとしない操作**を使用することをお勧めします。即興性のある、遊び心を加えたエクスペリエンスが許されるためです。</span><span class="sxs-lookup"><span data-stu-id="0b961-242">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="0b961-243">本能的なジェスチャ</span><span class="sxs-lookup"><span data-stu-id="0b961-243">Instinctual gestures</span></span>

<span data-ttu-id="0b961-244">HoloLens (第 1 世代) では、ブルームやエアタップなど、いくつかの定義済みジェスチャをユーザーが学ぶ必要がありました。</span><span class="sxs-lookup"><span data-stu-id="0b961-244">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="0b961-245">HoloLens 2 では、ユーザーが象徴的なジェスチャを覚える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0b961-245">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="0b961-246">ユーザーがホログラムやコンテンツと対話するときに必要とされるユーザー ジェスチャは、どれも本能的なものです。</span><span class="sxs-lookup"><span data-stu-id="0b961-246">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="0b961-247">本能的なジェスチャを実現するには、ユーザーがジェスチャを実行するよう、UI アフォーダンスのデザインを通して支援するという方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="0b961-247">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="0b961-248">たとえば、2 本の指でピンチしてオブジェクトまたは制御点をつかむようユーザーに促す場合、オブジェクトまたは制御点は小さいはずです。</span><span class="sxs-lookup"><span data-stu-id="0b961-248">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="0b961-249">5 本の指でつかむようユーザーに促す場合、オブジェクトまたは制御点は比較的大きいはずです。</span><span class="sxs-lookup"><span data-stu-id="0b961-249">If we want the user to perform five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="0b961-250">ボタンも同様です。小さいボタンならユーザーは 1 本の指でしか押せませんが、大きなボタンならユーザーは手のひらで押すよう促されます。</span><span class="sxs-lookup"><span data-stu-id="0b961-250">Similar to buttons, a tiny button would limit users to press it with a single finger; a large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="0b961-251">![移動](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-251">![Move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="0b961-252">**小さなオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="0b961-252">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-253">![回転](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-253">![Rotate](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="0b961-254">**中程度のオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="0b961-254">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0b961-255">![スケール](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b961-255">![Scale](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="0b961-256">**大きなオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="0b961-256">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="0b961-257">手と 6 DoF コントローラーの間の対称設計</span><span class="sxs-lookup"><span data-stu-id="0b961-257">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="0b961-258">AR の手と VR のモーション コントローラーとの間には、操作に類似点があることにお気付きかもしれません。</span><span class="sxs-lookup"><span data-stu-id="0b961-258">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="0b961-259">どちらの入力も、それぞれの環境で直接操作をトリガーするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="0b961-259">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="0b961-260">HoloLens 2 で近くのものを手でグラブ アンド ドラッグする操作は、WMR のモーション コントローラーのグラブ ボタンによる実行内容とほとんど同じです。</span><span class="sxs-lookup"><span data-stu-id="0b961-260">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="0b961-261">これにより、ユーザーは、2 つのプラットフォームの間の操作に習熟することができます。この知識は、アプリケーションを一方から他方に移植する場合に役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="0b961-261">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application from one to the other.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="0b961-262">視線追跡の使用による最適化</span><span class="sxs-lookup"><span data-stu-id="0b961-262">Optimize with eye tracking</span></span>

<span data-ttu-id="0b961-263">直接操作が思い通りに機能する場合は魅力的に感じられるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="0b961-263">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="0b961-264">しかし、手をどこに動かしても意図に反してホログラムがトリガーされてしまうと、フラストレーションの元になりかねません。</span><span class="sxs-lookup"><span data-stu-id="0b961-264">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="0b961-265">視線追跡は、ユーザーの意図をより的確に識別するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0b961-265">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="0b961-266">**いつ**:意図に反して操作応答がトリガーされることが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="0b961-266">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="0b961-267">視線追跡により、ユーザーの現在の関心事を理解しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="0b961-267">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="0b961-268">たとえば、ホログラフィック テキスト (説明書) を読んでいるときに、現実世界の仕事道具を取るために手を伸ばしたとします。</span><span class="sxs-lookup"><span data-stu-id="0b961-268">For example, imagine you are reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="0b961-269">そのときうっかり、ユーザーの視野 (FOV) に入っていなかったなどの理由で、それまでは気付いてさえいなかったいくつかの対話型ホログラフィック ボタンを横切って手を動かしてしまいました。</span><span class="sxs-lookup"><span data-stu-id="0b961-269">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before (e.g. it  may be outside the user's field-of-view (FoV)).</span></span>

  <span data-ttu-id="0b961-270">つまり:ユーザーがしばらくの間ホログラムを見ていないにもかかわらず、それに対するタッチ イベントまたはグリップ イベントが検出された場合、ユーザーは実際にはそのホログラムと対話するつもりはなかった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0b961-270">Long story short: If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, it is likely that the user wasn't actually intending to interact with that hologram.</span></span>

* <span data-ttu-id="0b961-271">**どちら**:アクティブ化の誤検知への対応以外に、つかんだり突いたりするホログラムを識別しやすくなるという別の例もあります。特にいくつかのホログラムが互いに近接して配置されている場合、こちらの視点から正確な交点がはっきりと見えない場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="0b961-271">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="0b961-272">HoloLens 2 の視線追跡は、目の視線入力を識別する精度に基づく限界はありますが、奥行きの差により、手入力で操作する際の近くの操作に非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0b961-272">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be very helpful for near interactions due to depth disparity when interacting with hand input.</span></span> <span data-ttu-id="0b961-273">このことは、たとえば操作ウィジェットをつかむときに手がホログラムの後ろにあるのか前にあるのかを判断するのが難しい場合があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0b961-273">This means that it is sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="0b961-274">**どこ**:クイック スロー ジェスチャで、ユーザーの視線に関する情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="0b961-274">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="0b961-275">ホログラムをつかみ、目標とする場所のだいたいの方角に向かって放り投げたとします。</span><span class="sxs-lookup"><span data-stu-id="0b961-275">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="0b961-276">これでうまくいくこともあるかもしれませんが、ジェスチャの手の動きが速いと、目標とする場所が極めて不正確になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0b961-276">While this sometimes works, quickly performing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="0b961-277">しかし、視線追跡でジェスチャの精度を向上できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0b961-277">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="0b961-278">Unity 向け MRTK (Mixed Reality ツールキット) の操作</span><span class="sxs-lookup"><span data-stu-id="0b961-278">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="0b961-279">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** を使用すると、スクリプト **ManipulationHandler** を使って一般的な操作の動作を簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="0b961-279">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ManipulationHandler**.</span></span> <span data-ttu-id="0b961-280">ManipulationHandler を使用すると、手で直接またはハンド レイを使って、オブジェクトをつかんで移動させることができます。</span><span class="sxs-lookup"><span data-stu-id="0b961-280">With ManipulationHandler, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="0b961-281">また、オブジェクトのスケーリングおよび回転に対する両手の操作もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0b961-281">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="0b961-282">MRTK - 操作</span><span class="sxs-lookup"><span data-stu-id="0b961-282">MRTK - Manipulation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)


---

## <a name="see-also"></a><span data-ttu-id="0b961-283">「</span><span class="sxs-lookup"><span data-stu-id="0b961-283">See also</span></span>

* [<span data-ttu-id="0b961-284">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="0b961-284">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0b961-285">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="0b961-285">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="0b961-286">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="0b961-286">Instinctual interactions</span></span>](interaction-fundamentals.md)
