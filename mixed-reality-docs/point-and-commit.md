---
title: 手を使ったポイントとコミット
description: ポイントとコミットの入力モデルの概要
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 対話, 設計, hololens, 手, 遠隔, ポイントとコミット
ms.openlocfilehash: 4e19a7fd95bac42283ce3e3176a1363afda8f220
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414537"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="38994-104">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="38994-104">Point and commit with hands</span></span>
<span data-ttu-id="38994-105">手を使ったポイントとコミットは、ユーザーが遠くにある 2D コンテンツや 3D オブジェクトをターゲットに設定したり、選択したり、操作したりすることを可能にする入力モデルです。</span><span class="sxs-lookup"><span data-stu-id="38994-105">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects in the distance.</span></span> <span data-ttu-id="38994-106">この「遠隔」対話技術は Mixed Reality に固有のものであり、人間が現実の世界と自然に対話するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="38994-106">This "far" interaction technique is unique to mixed reality, and is not a way humans naturally intereact with the real world.</span></span> <span data-ttu-id="38994-107">たとえば、スーパー ヒーロー映画 *X-Men* のキャラクター [Magneto ](https://en.wikipedia.org/wiki/Magneto_(comics)) は、遠くにある物体に手を伸ばして操作することができます。</span><span class="sxs-lookup"><span data-stu-id="38994-107">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="38994-108">こうしたことは現実世界では行えません。</span><span class="sxs-lookup"><span data-stu-id="38994-108">This is not something humans can do in reality.</span></span> <span data-ttu-id="38994-109">HoloLens (AR) と Mixed Reality (MR) を使用することで、この魔法の力をユーザーに付与してホログラフィック コンテンツをただ楽しむだけでなく、ユーザーの対話をより効果的かつ効率的にするために現実世界の物理的制約を打ち破ることができます。</span><span class="sxs-lookup"><span data-stu-id="38994-109">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power, breaking the physical constraint of the real world, not only to have a fun experience with holographic contents but also to make user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="38994-110">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="38994-110">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="38994-111"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="38994-111"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="38994-112"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="38994-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="38994-113"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="38994-113"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="38994-114"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="38994-114"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="38994-115">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="38994-115">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="38994-116">❌ サポート外</span><span class="sxs-lookup"><span data-stu-id="38994-116">❌ Not supported</span></span></td>
     <td><span data-ttu-id="38994-117">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="38994-117">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="38994-118">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="38994-118">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="38994-119">ポイントとコミットは、ハンズ ファーと呼ばれることもあります。これは、新しい多関節ハンド トラッキング システムを利用した新機能の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="38994-119">Point and commit, also known as hands far, is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="38994-120">この入力モデルは、モーション コントローラーを使用したイマーシブ ヘッドセットの主要な入力モデルでもあります。</span><span class="sxs-lookup"><span data-stu-id="38994-120">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

## <a name="hand-rays"></a><span data-ttu-id="38994-121">手の光線</span><span class="sxs-lookup"><span data-stu-id="38994-121">Hand rays</span></span>

<span data-ttu-id="38994-122">HoloLens 2 では、ユーザーの手のひらの中心から放出される手の光線を考案しました。</span><span class="sxs-lookup"><span data-stu-id="38994-122">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="38994-123">この光線は、手の延長と見なされます。</span><span class="sxs-lookup"><span data-stu-id="38994-123">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="38994-124">光線がターゲット オブジェクトと交わる場所を示すために、光線の終端にドーナツ型のカーソルが取り付けられています。</span><span class="sxs-lookup"><span data-stu-id="38994-124">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="38994-125">カーソルが届いているオブジェクトは、手から出されるジェスチャ コマンドを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="38994-125">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="38994-126">この基本的なジェスチャ コマンドは、親指と人差し指を使ってエアタップ アクションを実行してトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="38994-126">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="38994-127">手の光線を使用してポイントし、エアタップを使用してコミットすることで、ユーザーはボタンまたはハイパーリンクを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="38994-127">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="38994-128">ユーザーは、より複合的なジェスチャを使うことで、Web コンテンツをナビゲートしたり、遠くから 3D オブジェクトを操作したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="38994-128">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="38994-129">以下に説明および図示されているように、手の光線の視覚的なデザインも、これらのポイントとコミット状態に合わせて変化します。</span><span class="sxs-lookup"><span data-stu-id="38994-129">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

* <span data-ttu-id="38994-130">*ポイント*状態の光線は破線で表され、カーソルはドーナツ型になります。</span><span class="sxs-lookup"><span data-stu-id="38994-130">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
* <span data-ttu-id="38994-131">*コミット*状態になると光線は実線に変わり、カーソルは小さくなってドットになります。</span><span class="sxs-lookup"><span data-stu-id="38994-131">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>

<span data-ttu-id="38994-132">![手の光線のポインティングとコミットの状態](images/Hand-Rays-720px.jpg)</span><span class="sxs-lookup"><span data-stu-id="38994-132">![Pointing and commit states for hand rays](images/Hand-Rays-720px.jpg)</span></span><br>
<span data-ttu-id="38994-133">*手の光線のポインティング (左) とコミット (右) の状態*</span><span class="sxs-lookup"><span data-stu-id="38994-133">*Pointing (left) and commit (right) states for hand rays*</span></span>

## <a name="transition-between-near-and-far"></a><span data-ttu-id="38994-134">近くと遠くの切り替え</span><span class="sxs-lookup"><span data-stu-id="38994-134">Transition between near and far</span></span>

<span data-ttu-id="38994-135">「人差し指で指す」ことで光線を方向付けるなどの特定のジェスチャを使用する代わりに、手のひらの中心から光線が出るように設計しました。これにより、5 本の指を解放して、より操作的なジェスチャ (ピンチやグラブなど) を行うために取っておくことができます。</span><span class="sxs-lookup"><span data-stu-id="38994-135">Instead of using specific gestures, such as "pointing with index finger", to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="38994-136">この設計では、メンタル モデルを 1 つだけ作りました。これにより、近くでも遠くでもまったく同じ一連の手のジェスチャで対話することができます。</span><span class="sxs-lookup"><span data-stu-id="38994-136">With this design, we create only one mental model, supporting exactly the same set of hand gestures for both near and far interaction.</span></span> <span data-ttu-id="38994-137">同じグラブ ジェスチャで、距離が異なるオブジェクトを操作できます。</span><span class="sxs-lookup"><span data-stu-id="38994-137">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="38994-138">光線の呼び出しは、次のように近さに基づいて自動で行われます。</span><span class="sxs-lookup"><span data-stu-id="38994-138">The invocation of the rays is automatic and proximity based as follows:</span></span>

*  <span data-ttu-id="38994-139">腕の長さ (約 50 cm) の範囲内にオブジェクトが入ると光線は自動的に消え、近接の対話が勧められます。</span><span class="sxs-lookup"><span data-stu-id="38994-139">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
*  <span data-ttu-id="38994-140">オブジェクトとの距離が 50 cm を超えると、光線が点灯します。</span><span class="sxs-lookup"><span data-stu-id="38994-140">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="38994-141">切り替えはスムーズかつシームレスに行われます。</span><span class="sxs-lookup"><span data-stu-id="38994-141">The transition should be smooth and seamless.</span></span>

<span data-ttu-id="38994-142">![近くでも遠くでも同じ一連の手のジェスチャが使用されます](images/Transition-Between-Near-And-Far-720px.jpg)</span><span class="sxs-lookup"><span data-stu-id="38994-142">![The same set of hand gestures are used for both near and far interaction](images/Transition-Between-Near-And-Far-720px.jpg)</span></span><br>
<span data-ttu-id="38994-143">*近くでも遠くでも同じ一連の手のジェスチャが使用されます。*</span><span class="sxs-lookup"><span data-stu-id="38994-143">*The same set of hand gestures are used for both near and far interaction.*</span></span>

## <a name="2d-slate-interaction"></a><span data-ttu-id="38994-144">2D スレートとの対話</span><span class="sxs-lookup"><span data-stu-id="38994-144">2D slate interaction</span></span>

<span data-ttu-id="38994-145">2D スレートは、Web ブラウザーなどの 2D アプリ コンテンツをホストするホログラフィック コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="38994-145">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="38994-146">2D スレートとの遠隔対話の設計概念は、手の光線を使ってターゲット設定し、エアタップで選択するというものです。</span><span class="sxs-lookup"><span data-stu-id="38994-146">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="38994-147">手の光線でターゲット設定した後、ユーザーはエアタップしてハイパーリンクまたはボタンをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="38994-147">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="38994-148">片手で「エアタップ アンド ドラッグ」して、スレートのコンテンツを上下にスクロールすることができます。</span><span class="sxs-lookup"><span data-stu-id="38994-148">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="38994-149">両手を使ってエアタップ アンド ドラッグするという相対的な動きにより、スレートのコンテンツを拡大縮小することができます。</span><span class="sxs-lookup"><span data-stu-id="38994-149">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="38994-150">手の光線を隅や端にターゲット設定すると、最も近くにある操作アフォーダンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="38994-150">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="38994-151">ユーザーは操作アフォーダンスを「グラブ アンド ドラッグ」することで、隅のアフォーダンスによって均等に拡大縮小したり、端のアフォーダンスによってスレートをリフローしたりできます。</span><span class="sxs-lookup"><span data-stu-id="38994-151">By "grab and drag" manipulation affordances, users can perform uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="38994-152">2D スレートの上部にあるホロバーをグラブ アンド ドラッグすることで、ユーザーはスレート全体を移動できます。</span><span class="sxs-lookup"><span data-stu-id="38994-152">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

![2D スレートとの対話](images/2D-Slate-Interaction-Far-720px.jpg)

<span data-ttu-id="38994-154">2D スレートの操作方法は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="38994-154">For manipulating the 2D slate:</span></span><br>

* <span data-ttu-id="38994-155">ユーザーは、手の光線を隅または端にポイントして、最も近くにある操作アフォーダンスを表示します。</span><span class="sxs-lookup"><span data-stu-id="38994-155">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="38994-156">アフォーダンスに操作ジェスチャを適用すれば、ユーザーは隅のアフォーダンスによって均等に拡大縮小したり、端のアフォーダンスによってスレートをリフローしたりできます。</span><span class="sxs-lookup"><span data-stu-id="38994-156">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="38994-157">2D スレートの上部にあるホロバーに操作ジェスチャを適用することで、ユーザーはスレート全体を移動できます。</span><span class="sxs-lookup"><span data-stu-id="38994-157">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>

<br>

## <a name="3d-object-manipulation"></a><span data-ttu-id="38994-158">3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="38994-158">3D object manipulation</span></span>

<span data-ttu-id="38994-159">直接操作では、ユーザーは、アフォーダンスをベースとする操作とアフォーダンスをベースとしない操作の 2 つの方法で 3D オブジェクトを操作できます。</span><span class="sxs-lookup"><span data-stu-id="38994-159">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="38994-160">ポイントとコミットのモデルでは、ユーザーは手の光線を使ってまったく同じ作業を行えます。</span><span class="sxs-lookup"><span data-stu-id="38994-160">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="38994-161">学ばなければならないことは他にありません。</span><span class="sxs-lookup"><span data-stu-id="38994-161">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="38994-162">アフォーダンスをベースとする操作</span><span class="sxs-lookup"><span data-stu-id="38994-162">Affordance-based manipulation</span></span>
<span data-ttu-id="38994-163">ユーザーは手の光線を使用して、境界ボックスと操作アフォーダンスをポイントし、表示します。</span><span class="sxs-lookup"><span data-stu-id="38994-163">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="38994-164">ユーザーは操作ジェスチャを境界ボックスに適用してオブジェクト全体を移動したり、端のアフォーダンスに適用して回転させたり、隅のアフォーダンスに適用して均等に拡大縮小したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="38994-164">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

![アフォーダンスをベースとする操作](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="38994-166">アフォーダンスをベースとしない操作</span><span class="sxs-lookup"><span data-stu-id="38994-166">Non-affordance based manipulation</span></span>
<span data-ttu-id="38994-167">ユーザーは手の光線を使ってポイントし、境界ボックスを表示した後、直接操作ジェスチャを適用します。</span><span class="sxs-lookup"><span data-stu-id="38994-167">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="38994-168">片手を使用する場合、オブジェクトの移動と回転は手の動きと向きに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="38994-168">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="38994-169">ユーザーが両手を使用すると、両手の相対的な動きに応じてそれを移動、拡大縮小、回転できます。</span><span class="sxs-lookup"><span data-stu-id="38994-169">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

## <a name="instinctual-gestures"></a><span data-ttu-id="38994-170">本能的なジェスチャ</span><span class="sxs-lookup"><span data-stu-id="38994-170">Instinctual gestures</span></span>
<span data-ttu-id="38994-171">ポイントとコミットについての本能的なジェスチャの概念は、[手による直接操作](direct-manipulation.md)の概念と似ています。</span><span class="sxs-lookup"><span data-stu-id="38994-171">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="38994-172">ユーザーが 3D オブジェクトに対して実行するジェスチャは、UI アフォーダンスの設計によって導かれます。</span><span class="sxs-lookup"><span data-stu-id="38994-172">The gestures users perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="38994-173">たとえば、小さな制御点の場合にはユーザーは親指と人差し指でピンチするよう誘導されるのに対し、大きなオブジェクトの場合は 5 本の指すべてを使ってつかむかもしれません。</span><span class="sxs-lookup"><span data-stu-id="38994-173">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all five fingers.</span></span>

![本能的なジェスチャ](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="38994-175">手と 6 DoF コントローラーの間の対称設計</span><span class="sxs-lookup"><span data-stu-id="38994-175">Symmetric design between hands and 6 DoF controller</span></span> 
<span data-ttu-id="38994-176">遠くにあるものと対話する場合のポイントとコミットの概念は当初、Mixed Reality ポータル (MRP) 向けに考案され、定義されました。MRP では、ユーザーはイマーシブ ヘッドセットを装着し、モーション コントローラーを介して 3D オブジェクトとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="38994-176">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP) where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="38994-177">モーション コントローラーは、遠くにあるオブジェクトをポイントして操作するために光線を放ちます。</span><span class="sxs-lookup"><span data-stu-id="38994-177">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="38994-178">コントローラーにはボタンがあって、さまざまな操作をさらにコミットします。</span><span class="sxs-lookup"><span data-stu-id="38994-178">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="38994-179">光線の対話モデルを利用して、それを両手で利用することにしました。</span><span class="sxs-lookup"><span data-stu-id="38994-179">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="38994-180">この対称設計により、MRP に精通しているユーザーは HoloLens 2 を使用するとき、遠くにあるものをポイントして操作するための別の対話モデルを学ぶ必要がなくなります (逆も同様です)。</span><span class="sxs-lookup"><span data-stu-id="38994-180">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

![手と 6 DoF コントローラーの間の対称設計](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a><span data-ttu-id="38994-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="38994-182">See also</span></span>
* [<span data-ttu-id="38994-183">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="38994-183">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="38994-184">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="38994-184">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="38994-185">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="38994-185">Instinctual interactions</span></span>](interaction-fundamentals.md)

