---
title: 手で直接操作
description: 直接操作入力モデルの概要
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 視線入力, 視線入力ターゲット設定, 対話, 設計, 手に近い, HoloLens
ms.openlocfilehash: 8047d7549309d293b805dc43e44da99f9139e5c6
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414444"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="450af-104">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="450af-104">Direct manipulation with hands</span></span>
<span data-ttu-id="450af-105">直接操作は、ホログラムに手で直接触れる入力モデルです。</span><span class="sxs-lookup"><span data-stu-id="450af-105">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="450af-106">直接操作の背景にある考え方は、オブジェクトを現実の世界と同じように動かすことです。</span><span class="sxs-lookup"><span data-stu-id="450af-106">The idea behind direct manipulation is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="450af-107">ボタンを押してオンにしたり、オブジェクトをつかんで手に取ったりできます。2D コンテンツは仮想タッチスクリーンのように動作します。</span><span class="sxs-lookup"><span data-stu-id="450af-107">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="450af-108">このため、直接操作はユーザーにとって学びやすく、楽しくもあります。</span><span class="sxs-lookup"><span data-stu-id="450af-108">This makes direct manipulation is easy for users to learn, and fun.</span></span> <span data-ttu-id="450af-109">直接操作は、「近接」入力モデルと考えられており、手の届く範囲にあるコンテンツとの対話に最適です。</span><span class="sxs-lookup"><span data-stu-id="450af-109">Direct manipulation is considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

<span data-ttu-id="450af-110">直接操作はアフォーダンスをベースとしているので、操作が簡単です。</span><span class="sxs-lookup"><span data-stu-id="450af-110">Direct manipulation is affordance-based, meaning it's user friendly.</span></span> <span data-ttu-id="450af-111">ユーザーは象徴的なジェスチャを学ぶ必要はありません。</span><span class="sxs-lookup"><span data-stu-id="450af-111">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="450af-112">すべての対話は、触ったりつかんだりできる視覚的要素を中心に構築されています。</span><span class="sxs-lookup"><span data-stu-id="450af-112">All interactions are built around a visual element that you can touch or grab.</span></span>

## <a name="device-support"></a><span data-ttu-id="450af-113">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="450af-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="450af-114"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="450af-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="450af-115"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="450af-115"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="450af-116"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="450af-116"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="450af-117"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="450af-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="450af-118">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="450af-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="450af-119">❌ サポート外</span><span class="sxs-lookup"><span data-stu-id="450af-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="450af-120">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="450af-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="450af-121">➕ 別の選択肢である<a href="point-and-commit.md">手を使ったポイントとコミット</a>を推奨。</span><span class="sxs-lookup"><span data-stu-id="450af-121">➕ An alternative, <a href="point-and-commit.md">point and commit with hands</a> is recommended.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="450af-122">直接操作は HoloLens 2 の主要な入力モデルであり、新しい多関節ハンド トラッキング システムを利用しています。</span><span class="sxs-lookup"><span data-stu-id="450af-122">Direct manipulation is a primary input model on HoloLens 2, and utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="450af-123">この入力モデルは、イマーシブ ヘッドセットでもモーション コントローラー経由で利用できますが、オブジェクト操作以外の対話の主要な手段としてはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="450af-123">The input model is also available on immersive headsets through the use of motion controllers, but is not recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="450af-124">HoloLens (第 1 世代) では直接操作を利用できません。</span><span class="sxs-lookup"><span data-stu-id="450af-124">Direct manipluation is not available on HoloLens (1st gen).</span></span>


## <a name="collidable-fingertip"></a><span data-ttu-id="450af-125">接触可能な指先</span><span class="sxs-lookup"><span data-stu-id="450af-125">Collidable fingertip</span></span>

<span data-ttu-id="450af-126">HoloLens 2 では、ユーザーの手が、左右の手の骨格モデルとして認識および解釈されます。</span><span class="sxs-lookup"><span data-stu-id="450af-126">On HoloLens 2, the user's hands are recognized and interpreted as left and right hand skeletal models.</span></span> <span data-ttu-id="450af-127">ホログラムに直接手で触れるという概念を実現するためには、それぞれの手の骨格モデルの 5 本の指先に 5 つのコライダーを取り付けることが理想的と考えられました。</span><span class="sxs-lookup"><span data-stu-id="450af-127">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="450af-128">しかし、触覚的フィードバックがないため、10 本の接触可能な指先とホログラムとの間で、期待に反する予測不可能な衝突が発生してしまいました。</span><span class="sxs-lookup"><span data-stu-id="450af-128">However, due to the lack of tactile feedback, ten collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="450af-129">そこで、両方の人差し指だけにコライダーを付けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="450af-129">Hence, we suggest to only put a collider on each index finger.</span></span> <span data-ttu-id="450af-130">それでも、接触可能な人差し指の指先は、下の画像に示すように、他の指を含むさまざまなタッチ ジェスチャのアクティブ タッチ ポイントとして機能します。たとえば、指 1 本の押し、指 1 本のタップ、指 2 本の押し、指 5 本の押しなどです。</span><span class="sxs-lookup"><span data-stu-id="450af-130">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers, such as 1-finger press, 1-finger tap, 2-finger press and 5-finger press, as shown in the image below.</span></span>

![接触可能な指先の画像](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a><span data-ttu-id="450af-132">スフィア コライダー</span><span class="sxs-lookup"><span data-stu-id="450af-132">Sphere collider</span></span>

<span data-ttu-id="450af-133">ランダムな汎用シェイプを使用する代わりに、スフィア コライダーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="450af-133">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="450af-134">次に、これを視覚的にレンダリングすることで、近接ターゲット設定のためにより優れた手掛かりを与えます。</span><span class="sxs-lookup"><span data-stu-id="450af-134">Then visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="450af-135">タッチ精度を上げるには、スフィアの直径を人差し指の太さに合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="450af-135">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="450af-136">hand API を呼び出すことで、指の太さの変数を簡単に取得できます。</span><span class="sxs-lookup"><span data-stu-id="450af-136">It easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="450af-137">指先カーソル</span><span class="sxs-lookup"><span data-stu-id="450af-137">Fingertip cursor</span></span>

<span data-ttu-id="450af-138">人差し指の指先に接触可能なスフィアをレンダリングすることに加え、高度な指先カーソルも作成されました。これにより、近接ターゲット設定のエクスペリエンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="450af-138">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to interactively achieve a better near-targeting experience.</span></span> <span data-ttu-id="450af-139">これは、人差し指に付随するドーナツ型のカーソルです。</span><span class="sxs-lookup"><span data-stu-id="450af-139">It is a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="450af-140">これは距離に応じて対象に反応して向きやサイズが変化します。詳しくは、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="450af-140">According to proximity, it dynamically reacts to a target in terms of orientation and size as detailed below:</span></span>

* <span data-ttu-id="450af-141">人差し指をホログラムに近づけると、カーソルは常にホログラムの表面と平行になり、近づくにつれて徐々にサイズが小さくなります。</span><span class="sxs-lookup"><span data-stu-id="450af-141">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size accordingly.</span></span>
* <span data-ttu-id="450af-142">指が表面に触れるとカーソルは直ちにドットにまで縮小し、タッチ イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="450af-142">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="450af-143">次に示されているように、ユーザーは、対話型のフィードバックによって、ハイパーリンクのトリガーやボタンの押下など、高い精度で近接ターゲット設定のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="450af-143">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

![指先カーソルの画像](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="450af-145">近接シェーダーを備えた境界ボックス</span><span class="sxs-lookup"><span data-stu-id="450af-145">Bounding box with proximity shader</span></span>

<span data-ttu-id="450af-146">触覚的フィードバックがないことを補うため、ホログラム自体にも視覚および音声の両方のフィードバックを提供する機能が必要です。</span><span class="sxs-lookup"><span data-stu-id="450af-146">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="450af-147">そこで、近接シェーダーを備えた境界ボックスという概念が考案されました。</span><span class="sxs-lookup"><span data-stu-id="450af-147">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="450af-148">境界ボックスは、3D オブジェクトを囲む最小の立体領域です。</span><span class="sxs-lookup"><span data-stu-id="450af-148">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="450af-149">境界ボックスには、近接シェーダーと呼ばれる対話的なレンダリング メカニズムがあります。</span><span class="sxs-lookup"><span data-stu-id="450af-149">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="450af-150">近接シェーダーは次のように動作します。</span><span class="sxs-lookup"><span data-stu-id="450af-150">The proximity shader behaves:</span></span>

* <span data-ttu-id="450af-151">人差し指が一定範囲内にある場合、指先スポットライトが境界ボックスの表面に投影されます。</span><span class="sxs-lookup"><span data-stu-id="450af-151">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
* <span data-ttu-id="450af-152">指先が表面に近づくと、距離に応じてスポットライトが縮小します。</span><span class="sxs-lookup"><span data-stu-id="450af-152">When the fingertip gets closer to the surface, the spotlight shrinks accordingly.</span></span>
* <span data-ttu-id="450af-153">指先が表面に触れると直ちに、境界ボックス全体の色が変わったり、視覚的効果が生じたりして、タッチ状態が反映されます。</span><span class="sxs-lookup"><span data-stu-id="450af-153">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
* <span data-ttu-id="450af-154">また、効果音が鳴るようにしてタッチの視覚的フィードバックを増強できます。</span><span class="sxs-lookup"><span data-stu-id="450af-154">A sound effect can also be activated to enhance the visual touch feedback.</span></span>

![近接シェーダーを備えた境界ボックスの画像](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a><span data-ttu-id="450af-156">押しボタン</span><span class="sxs-lookup"><span data-stu-id="450af-156">Pressable button</span></span>

<span data-ttu-id="450af-157">ユーザーは接触可能な指先で、押しボタンなど基本的なホログラフィック UI コンポーネントと対話できます。</span><span class="sxs-lookup"><span data-stu-id="450af-157">With a collidable fingertip, users are now ready to interact with the fundamental holographic UI component, sucha as a pressable button.</span></span> <span data-ttu-id="450af-158">押しボタンは、直接指で押せるように調整されたホログラフィック ボタンです。</span><span class="sxs-lookup"><span data-stu-id="450af-158">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="450af-159">押しボタンの場合もそれを押したときの感覚がないので、触覚フィードバックに関連した問題を処理するためのメカニズムがいくつか備えられています。</span><span class="sxs-lookup"><span data-stu-id="450af-159">Again, due to the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="450af-160">1 つ目のメカニズムは、近接シェーダーを備えた境界ボックスです。これについては、前のセクションで詳しく説明しました。</span><span class="sxs-lookup"><span data-stu-id="450af-160">The first mechanism is a bounding box with a proximity shader, which isdetailed in the previous section.</span></span> <span data-ttu-id="450af-161">これにより、ユーザーがボタンに近づいて接触するとき、接近の感覚が向上します。</span><span class="sxs-lookup"><span data-stu-id="450af-161">It give users a better sense of proximity when as approach and make contact with a button.</span></span>
* <span data-ttu-id="450af-162">2 つ目のメカニズムは、押し下げの感覚です。</span><span class="sxs-lookup"><span data-stu-id="450af-162">The second mechanism is depression.</span></span> <span data-ttu-id="450af-163">押し下げの感覚により、指先がボタンに接触した後、押し下げるという感覚が生まれます。</span><span class="sxs-lookup"><span data-stu-id="450af-163">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="450af-164">指先と一緒に、深さ軸に沿って、重みを伴ってボタンが動くメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="450af-164">The mechanism is that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="450af-165">指定された深さに達したとき (トリガー時) か、その深さを超えた後で離したとき (リリース時) にボタンをトリガーすることができます。</span><span class="sxs-lookup"><span data-stu-id="450af-165">The button can be triggered when it reaches a designated depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="450af-166">ボタンがトリガーされたときに効果音が鳴るようにしてフィードバックを増強する必要があります。</span><span class="sxs-lookup"><span data-stu-id="450af-166">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

![押しボタンの画像](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a><span data-ttu-id="450af-168">2D スレートとの対話</span><span class="sxs-lookup"><span data-stu-id="450af-168">2D slate interaction</span></span>

<span data-ttu-id="450af-169">2D スレートは、Web ブラウザーなどの 2D アプリ コンテンツをホストするホログラフィック コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="450af-169">A 2D slate is a holographic container hosting 2D app contents, such as web browser.</span></span> <span data-ttu-id="450af-170">直接操作による 2D スレートとの対話の設計概念は、物理的なタッチ画面との対話という概念的モデルを利用するというものです。</span><span class="sxs-lookup"><span data-stu-id="450af-170">The design concept for interacting with a 2D slate via direct manipulation is to leverage the mental model of interacting with a physical touch screen.</span></span>

<span data-ttu-id="450af-171">スレートとの接触による対話は、次のように行います。</span><span class="sxs-lookup"><span data-stu-id="450af-171">To interact with the slate contact:</span></span>

* <span data-ttu-id="450af-172">人差し指を使ってハイパーリンクまたはボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="450af-172">Use an index finger to press a hyperlink or a button.</span></span>
* <span data-ttu-id="450af-173">人差し指を使ってスレート コンテンツを上下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="450af-173">Use an index finger to scroll a slate content up and down.</span></span>
* <span data-ttu-id="450af-174">ユーザーは 2 本の人差し指を使用して、指の相対的な動きに応じてスレートのコンテンツを拡大縮小します。</span><span class="sxs-lookup"><span data-stu-id="450af-174">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>

![2D スレートの画像](images/2D-Slate-Interaction-720px.jpg)

<span data-ttu-id="450af-176">2D スレート本体の操作方法は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="450af-176">For manipulating the 2D slate itself:</span></span>

* <span data-ttu-id="450af-177">隅や端に手に近づけて、一番近くにある操作アフォーダンスを表示します。</span><span class="sxs-lookup"><span data-stu-id="450af-177">Approach your hands toward corners and edges to reveal the closest manipulation affordances.</span></span>
* <span data-ttu-id="450af-178">操作アフォーダンスをつかみ、均等に拡大縮小する場合は隅のアフォーダンスを、リフローを行う場合は端のアフォーダンスをつかみます。</span><span class="sxs-lookup"><span data-stu-id="450af-178">Grab the manipulation affordances, and perform uniform scaling through the corner affordances, and reflow via the edge affordances.</span></span>
* <span data-ttu-id="450af-179">2D スレートの上部にあるホロバーをつかむことで、スレート全体を動かすことができます。</span><span class="sxs-lookup"><span data-stu-id="450af-179">Grab the holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>

![スレート操作の画像](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a><span data-ttu-id="450af-181">3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="450af-181">3D object manipulation</span></span>

<span data-ttu-id="450af-182">HoloLens 2 では、各 3D オブジェクトに境界ボックスを適用することで、ユーザーが 3D ホログラフィック オブジェクトを手で直接操作することができます。</span><span class="sxs-lookup"><span data-stu-id="450af-182">HoloLens 2 lets lets users enable their hands to direct manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="450af-183">境界ボックスは、その近接シェーダーによって奥行きを感知しやすくします。</span><span class="sxs-lookup"><span data-stu-id="450af-183">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="450af-184">境界ボックスには、3D オブジェクト操作のための 2 つの設計アプローチがあります。</span><span class="sxs-lookup"><span data-stu-id="450af-184">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="450af-185">アフォーダンスをベースとする操作</span><span class="sxs-lookup"><span data-stu-id="450af-185">Affordance-based manipulation</span></span>

<span data-ttu-id="450af-186">アフォーダンスをベースとする操作により、境界ボックスとその周囲の操作アフォーダンスを通じて 3D オブジェクトを操作できます。</span><span class="sxs-lookup"><span data-stu-id="450af-186">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> <span data-ttu-id="450af-187">ユーザーの手が 3D オブジェクトに近づくと直ちに、境界ボックスおよび最も近いアフォーダンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="450af-187">As soon as a user's hand is close to a 3D object, the bounding box and the nearest affordance are revealed.</span></span> <span data-ttu-id="450af-188">ユーザーは、境界ボックスをつかんでオブジェクト全体を移動したり、端のアフォーダンスをつかんで回転させたり、隅のアフォーダンスをつかんで均等に拡大縮小したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="450af-188">Users can grab the bounding box to move the whole object, the edge affordances to rotate and the corner affordances to scale uniformly.</span></span>

![3D オブジェクト操作の画像](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="450af-190">アフォーダンスをベースとしない操作</span><span class="sxs-lookup"><span data-stu-id="450af-190">Non-affordance based manipulation</span></span>

<span data-ttu-id="450af-191">アフォーダンスをベースとしない操作では、アフォーダンスは境界ボックスにアタッチされません。</span><span class="sxs-lookup"><span data-stu-id="450af-191">Non-affordance-based manipulation does not attach affordance to the bounding box.</span></span> <span data-ttu-id="450af-192">ユーザーが行えるのは、境界ボックスを表示した後、直接対話することだけです。</span><span class="sxs-lookup"><span data-stu-id="450af-192">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="450af-193">境界ボックスを片手でつかむと、オブジェクトの移動と回転は手の動きと向きに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="450af-193">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="450af-194">ユーザーがオブジェクトを両手でつかむと、両手の相対的な動きに応じてそのオブジェクトを移動、拡大縮小、回転できます。</span><span class="sxs-lookup"><span data-stu-id="450af-194">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="450af-195">特定の操作では正確さが求められます。</span><span class="sxs-lookup"><span data-stu-id="450af-195">Specific manipulation requires precision.</span></span> <span data-ttu-id="450af-196">**アフォーダンスをベースとする操作**を使用することをお勧めします。細かい調整を行うことができるためです。</span><span class="sxs-lookup"><span data-stu-id="450af-196">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="450af-197">融通が利く操作の場合は、**アフォーダンスをベースとしない操作**を使用することをお勧めします。即興性のある、遊び心を加えたエクスペリエンスが許されるためです。</span><span class="sxs-lookup"><span data-stu-id="450af-197">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

## <a name="instinctual-gestures"></a><span data-ttu-id="450af-198">本能的なジェスチャ</span><span class="sxs-lookup"><span data-stu-id="450af-198">Instinctual gestures</span></span>

<span data-ttu-id="450af-199">HoloLens (第 1 世代) では、ブルームやエアタップなど、いくつかの定義済みジェスチャをユーザーが学ぶ必要がありました。</span><span class="sxs-lookup"><span data-stu-id="450af-199">With HoloLens (1st Gen), we taught users a couple predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="450af-200">HoloLens 2 では、ユーザーが象徴的なジェスチャを覚える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="450af-200">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="450af-201">ユーザーがホログラムやコンテンツと対話するときに必要とされるユーザー ジェスチャは、どれも本能的なものです。</span><span class="sxs-lookup"><span data-stu-id="450af-201">All required user gestures--where users need to interact with holograms and content--are instinctual.</span></span> <span data-ttu-id="450af-202">本能的なジェスチャを実現するには、ユーザーがジェスチャを実行するよう、UI アフォーダンスのデザインを通して支援するという方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="450af-202">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="450af-203">たとえば、2 本の指でピンチしてオブジェクトまたは制御点をつかむようユーザーに促す場合、オブジェクトまたは制御点は小さいはずです。</span><span class="sxs-lookup"><span data-stu-id="450af-203">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="450af-204">5 本の指でつかむようユーザーに促す場合、オブジェクトまたは制御点は比較的大きいはずです。</span><span class="sxs-lookup"><span data-stu-id="450af-204">If we want the user to perform five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="450af-205">ボタンも同様です。小さいボタンならユーザーは 1 本の指でしか押せませんが、大きなボタンならユーザーは手のひらで押すよう促されます。</span><span class="sxs-lookup"><span data-stu-id="450af-205">Similar to buttons, a tiny button would limit users to press it with a single finger; a large button would encourage users to press it with their palms.</span></span>

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="450af-206">手と 6 DoF コントローラーの間の対称設計</span><span class="sxs-lookup"><span data-stu-id="450af-206">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="450af-207">AR の手と VR のモーション コントローラーとの間には、対話の類似点があることにお気付きかもしれません。</span><span class="sxs-lookup"><span data-stu-id="450af-207">You may have noticed that there are interaction parallels that we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="450af-208">どちらの入力も、それぞれの環境で直接操作をトリガーするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="450af-208">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="450af-209">HoloLens 2 で近くのものを手でグラブ アンド ドラッグする操作は、WMR のモーション コントローラーのグラブ ボタンによる実行内容とほとんど同じです。</span><span class="sxs-lookup"><span data-stu-id="450af-209">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="450af-210">こうしてユーザーは、2 つのプラットフォームの間の操作に習熟することができます。この知識は、アプリケーションを一方から他方に移植する場合に役立つ可能性があります。</span><span class="sxs-lookup"><span data-stu-id="450af-210">This provides users with interaction familiarity between the two platforms, and might prove useful should you ever decide to port your application from one to the other.</span></span>

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="450af-211">視線追跡の使用による最適化</span><span class="sxs-lookup"><span data-stu-id="450af-211">Optimize with eye tracking</span></span>

<span data-ttu-id="450af-212">直接操作が思い通りに機能する場合は魅力的に感じられるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="450af-212">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="450af-213">しかし、手をどこに動かしても意図に反してホログラムがトリガーされるばかりになると、即座にフラストレーションの元となります。</span><span class="sxs-lookup"><span data-stu-id="450af-213">But can also quickly become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="450af-214">視線追跡は、ユーザーの意図をより的確に識別するうえで役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="450af-214">Eye tracking can potentially help in better identifying what the user’s intent is.</span></span>

* <span data-ttu-id="450af-215">**いつ**:意図に反して操作応答がトリガーされることが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="450af-215">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="450af-216">視線追跡により、ユーザーの現在の関心事を理解しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="450af-216">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="450af-217">たとえば、ホログラフィック テキスト (説明書) を読んでいるときに、現実世界の仕事道具を取るために手を伸ばしたとします。</span><span class="sxs-lookup"><span data-stu-id="450af-217">For example, imagine you are reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="450af-218">そのときうっかり、それまでは気付いてさえいなかったいくつかの対話型ホログラフィック ボタンを横切って手を動かしてしまいました (おそらく、ユーザーの視野 (FOV) にさえ入っていなかったのかもしれません)。</span><span class="sxs-lookup"><span data-stu-id="450af-218">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before (maybe it even was outside of the user's field-of-view (FoV)).</span></span>

  <span data-ttu-id="450af-219">つまり:ユーザーがしばらくの間ホログラムを見ていないにもかかわらず、それに対するタッチ イベントまたはグリップ イベントが検出された場合、ユーザーは実際にはそのホログラムと対話するつもりはなかった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="450af-219">Long story short: If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, it is likely that the user wasn't actually intending to interact with that hologram.</span></span>

* <span data-ttu-id="450af-220">**どちら**:アクティブ化の誤検知への対応以外に、つかんだり突いたりするホログラムを識別しやすくなるという別の例もあります。特にいくつかのホログラムが互いに近接して配置されている場合、こちらの視点から正確な交点がはっきりと見えない場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="450af-220">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="450af-221">HoloLens 2 の視線追跡には、目の視線入力を識別する精度にある程度の限界はありますが、手入力で対話する際は、奥行きの差により、近接の対話に非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="450af-221">While eye tracking on HoloLens 2 has a certain limitation on how accurately it can determine you eye gaze, this can still be very helpful for near interactions due to depth disparity when interacting with hand input.</span></span> <span data-ttu-id="450af-222">このことは、たとえば操作ウィジェットをつかむときに手がホログラムの後ろにあるのか前にあるのかを判断するのが難しい場合があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="450af-222">This means that it is sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="450af-223">**どこ**:クイック スロー ジェスチャで、ユーザーの視線に関する情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="450af-223">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="450af-224">ホログラムをつかみ、目標とする場所のだいたいの方角に向かって放り投げたとします。</span><span class="sxs-lookup"><span data-stu-id="450af-224">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="450af-225">これでうまくいくこともあるかもしれませんが、ジェスチャの手の動きが速いと、目標とする場所が極めて不正確になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="450af-225">While this sometimes works, quickly performing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="450af-226">このシナリオでは、視線追跡を含めることでジェスチャの精度を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="450af-226">In this scenario including eye tracking could improve the accuracy of the gesture.</span></span>

## <a name="see-also"></a><span data-ttu-id="450af-227">関連項目</span><span class="sxs-lookup"><span data-stu-id="450af-227">See also</span></span>

* [<span data-ttu-id="450af-228">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="450af-228">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="450af-229">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="450af-229">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="450af-230">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="450af-230">Instinctual interactions</span></span>](interaction-fundamentals.md)

