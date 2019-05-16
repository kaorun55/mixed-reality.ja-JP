---
title: ポイントとの手でコミット
description: ポイントとコミットの入力モデルの概要
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 実際には、相互作用、デザイン、hololens、手を混在までは、ポイントし、コミット
ms.openlocfilehash: e69c8ff2091beff7d8fbbde4e6f24d909302290a
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730809"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="79c5e-104">ポイントとの手でコミット</span><span class="sxs-lookup"><span data-stu-id="79c5e-104">Point and commit with hands</span></span>
<span data-ttu-id="79c5e-105">ポイントとコミットの手では、ユーザーが対象に選択し、距離の 2D のコンテンツと 3D オブジェクトを操作できる入力モデルです。</span><span class="sxs-lookup"><span data-stu-id="79c5e-105">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects in the distance.</span></span> <span data-ttu-id="79c5e-106">この「まで」操作方法は、複合現実に固有と方法の人間は必然的は、実世界と intereact します。</span><span class="sxs-lookup"><span data-stu-id="79c5e-106">This "far" interaction technique is unique to mixed reality and is not a way humans naturally intereact with the real world.</span></span> <span data-ttu-id="79c5e-107">スーパー ヒーロー ムービーなどで*X-men*、文字[磁気](https://en.wikipedia.org/wiki/Magneto_(comics))問い合わせるおよびの手で距離の相手側のオブジェクトを操作できます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-107">For example, in the super hero movie *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="79c5e-108">これは何か実際には人間が行うことができます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-108">This is not something humans can do in reality.</span></span> <span data-ttu-id="79c5e-109">HoloLens (AR) および複合現実 (VR) のどちらも、holographic の内容のすばらしい経験だけでなく、効率的かつ効果的に相互作用するもの実際の物理的な制約の重大なこの魔法のような電力で、ユーザーがについて説明します。</span><span class="sxs-lookup"><span data-stu-id="79c5e-109">In both HoloLens (AR) and Mixed Reality (VR), we equip users with this magical power, breaking the physical constraint of the real world not only to have a delightful experience with holographic contents but also to make the interaction more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="79c5e-110">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="79c5e-110">Device support</span></span>

<span data-ttu-id="79c5e-111">入力モデル</span><span class="sxs-lookup"><span data-stu-id="79c5e-111">Input model</span></span> | [<span data-ttu-id="79c5e-112">HoloLens (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="79c5e-112">HoloLens (1st gen)</span></span>](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | <span data-ttu-id="79c5e-113">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="79c5e-113">HoloLens 2</span></span> | [<span data-ttu-id="79c5e-114">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="79c5e-114">Immersive headsets</span></span>](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
<span data-ttu-id="79c5e-115">ポイントとコミット (ここまでの手による操作)</span><span class="sxs-lookup"><span data-stu-id="79c5e-115">Point and commit (far hand interaction)</span></span> | <span data-ttu-id="79c5e-116">❌ がサポートされていません</span><span class="sxs-lookup"><span data-stu-id="79c5e-116">❌ Not supported</span></span> | <span data-ttu-id="79c5e-117">推奨 ✔️</span><span class="sxs-lookup"><span data-stu-id="79c5e-117">✔️ Recommended</span></span> | <span data-ttu-id="79c5e-118">推奨 ✔️</span><span class="sxs-lookup"><span data-stu-id="79c5e-118">✔️ Recommended</span></span>

<span data-ttu-id="79c5e-119">ポイント、コミットとも呼ばれます手までは新しい関節手動追跡システムを利用する新しい機能の 1 つ。</span><span class="sxs-lookup"><span data-stu-id="79c5e-119">Point and commit, also known as hands far, is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="79c5e-120">この入力モデルもアニメーション コント ローラーを使用してイマーシブ ヘッドセットでプライマリ入力モデル。</span><span class="sxs-lookup"><span data-stu-id="79c5e-120">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

## <a name="hand-rays"></a><span data-ttu-id="79c5e-121">光線の手の形</span><span class="sxs-lookup"><span data-stu-id="79c5e-121">Hand rays</span></span>

<span data-ttu-id="79c5e-122">HoloLens の 2、palm の中心からがシュートする手光線を作成しました。</span><span class="sxs-lookup"><span data-stu-id="79c5e-122">On HoloLens 2, we created a hand ray that shoots out from the center of a palm.</span></span> <span data-ttu-id="79c5e-123">この射線は、手の形の拡張機能として扱われます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-123">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="79c5e-124">ドーナツ型のカーソルは、ターゲット オブジェクトと射線が交差する場所を示す光線の最後にアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-124">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="79c5e-125">カーソルにアクセスしたオブジェクトは、手のジェスチャー コマンドを受信できます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-125">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="79c5e-126">親指と人差し指をエア タップ アクションを実行するを使用して、この基本的なジェスチャー コマンドがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-126">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="79c5e-127">ハンド レイ エア タップしてコミットし、使用すると、ユーザーはボタンやハイパーリンクを web コンテンツをアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-127">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink on a web content.</span></span> <span data-ttu-id="79c5e-128">複数の複合ジェスチャでは、ユーザーは web コンテンツを移動し、離れた位置から 3D オブジェクトの操作の対応です。</span><span class="sxs-lookup"><span data-stu-id="79c5e-128">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="79c5e-129">手光線のビジュアル デ ザインは、下記の説明に従ってこれらポイントとコミットの状態にも対処すべき。</span><span class="sxs-lookup"><span data-stu-id="79c5e-129">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

* <span data-ttu-id="79c5e-130">*ポイント*射線は破線とドーナツ図形にカーソルが、状態します。</span><span class="sxs-lookup"><span data-stu-id="79c5e-130">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
* <span data-ttu-id="79c5e-131">*コミット*状態では、実線に射線がなり、ドットにカーソルが縮小されます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-131">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a><span data-ttu-id="79c5e-132">ほぼとの間で移行します。</span><span class="sxs-lookup"><span data-stu-id="79c5e-132">Transition between near and far</span></span>

<span data-ttu-id="79c5e-133">「人差し指を指す」などの特定のジェスチャを使用する代わりに光線を指示するアウトを解放し、詳細の manipulative ジェスチャの 5 本の指の予約、palm の中心からなどによるピンチ ジェスチャと取得に送信される光線を設計しました。</span><span class="sxs-lookup"><span data-stu-id="79c5e-133">Instead of using specific gesture, such as "pointing with index finger" to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="79c5e-134">この設計では、作成メンタル モデルを 1 つだけ、近距離と相手側の両方の相互作用をまったく手のジェスチャの同じセットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="79c5e-134">With this design, we create only one mental model, supporting exactly the same set of hand gestures for both near and far interaction.</span></span> <span data-ttu-id="79c5e-135">同じグラブ ジェスチャを使用して、さまざまな距離でオブジェクトを操作することができます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-135">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="79c5e-136">光線の呼び出しは、自動および近接のベースには。</span><span class="sxs-lookup"><span data-stu-id="79c5e-136">The invocation of the rays is automatic and proximity based:</span></span>

*  <span data-ttu-id="79c5e-137">arm の距離 (約 50 cm) に達しました内のオブジェクトは、光線がほぼ相互作用の促進に自動的にオフになります。</span><span class="sxs-lookup"><span data-stu-id="79c5e-137">When an object is within arm reached distance (roughly 50 cm), the rays are turned off automatically encouraging for near interaction.</span></span>
*  <span data-ttu-id="79c5e-138">オブジェクトは、50 cm 偏が、光線はオンにします。</span><span class="sxs-lookup"><span data-stu-id="79c5e-138">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="79c5e-139">移行が円滑かつシームレスな必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c5e-139">The transition should be smooth and seamless.</span></span>

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a><span data-ttu-id="79c5e-140">2D のスレートの相互作用</span><span class="sxs-lookup"><span data-stu-id="79c5e-140">2D slate interaction</span></span>

<span data-ttu-id="79c5e-141">2D スレートは、web ブラウザーなどの 2D アプリのコンテンツをホストしている holographic コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="79c5e-141">A 2D Slate is a holographic container hosting 2D app contents, such as web browser.</span></span> <span data-ttu-id="79c5e-142">2D スレートと対話するまでのデザインの概念をターゲットとエア タップに手光線を使用して、選択です。</span><span class="sxs-lookup"><span data-stu-id="79c5e-142">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="79c5e-143">手光線を対象とした後は、ユーザーはエア タップして、ハイパーリンクやボタンをトリガーになれます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-143">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="79c5e-144">1 つの手を使用して、「エア タップ アンド ドラッグ」スレートのコンテンツを上下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="79c5e-144">They can use one hand to "air tap and drag" to scroll a slate content up and down.</span></span> <span data-ttu-id="79c5e-145">相対的な動きを 2 つの手を使用して、エア タップし、ドラッグするには、in および out スレートのコンテンツを拡大できます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-145">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="79c5e-146">角や辺で手光線を対象とするには、最も近い操作アフォー ダンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-146">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="79c5e-147">「グラブしてドラッグ」操作アフォー、ユーザーが実行できる uniform 上隅にあるアフォーでスケーリングとエッジ アフォー経由でスレートをリフローすることができます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-147">By "grab and drag" the manipulation affordances, users can perform uniform scaling through the corner affordances and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="79c5e-148">グラブしてドラッグ、holobar 2D のスレートの上部にあるユーザーは全体のスレートを移動できます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-148">Grabbing and dragging the holobar at the top of the 2D slate can users move the whole slate.</span></span>

![](images/2D-Slate-Interaction-Far-720px.jpg)

<span data-ttu-id="79c5e-149">2D を操作するためには、それ自体をスレートします。</span><span class="sxs-lookup"><span data-stu-id="79c5e-149">For manipulating the 2D slate itself:</span></span><br>

* <span data-ttu-id="79c5e-150">ユーザーは、コーナーまたはエッジに最も近い操作アフォー ダンスを明らかに手光線をポイントします。</span><span class="sxs-lookup"><span data-stu-id="79c5e-150">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="79c5e-151">操作のジェスチャをアフォー ダンスに適用すると、ユーザーは上隅にあるアフォー ダンスで統一されたスケーリングを実行でき、edge アフォー ダンス経由でスレートをリフローすることができます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-151">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="79c5e-152">操作のジェスチャを 2D のスレートの上部にある holobar に適用すると、ユーザーは、全体のスレートを移動できます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-152">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the whole slate.</span></span><br>

<br>

## <a name="3d-object-manipulation"></a><span data-ttu-id="79c5e-153">3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="79c5e-153">3D object manipulation</span></span>

<span data-ttu-id="79c5e-154">直接の操作はユーザー 3 D オブジェクト、アフォー ダンスに基づく操作および非アフォー ダンスに基づいて操作を操作するための 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="79c5e-154">In direct manipulation, there are two ways for users to manipulate 3D object, affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="79c5e-155">ポイントとコミットのモデルでは、ユーザーが手光線を正確に同じタスクを実現可能です。</span><span class="sxs-lookup"><span data-stu-id="79c5e-155">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="79c5e-156">その他の学習は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="79c5e-156">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="79c5e-157">アフォー ダンス ベースの操作</span><span class="sxs-lookup"><span data-stu-id="79c5e-157">Affordance-based manipulation</span></span>
<span data-ttu-id="79c5e-158">ユーザーは、ポイントし、境界ボックスと操作アフォーを明らかに手光線を使用します。</span><span class="sxs-lookup"><span data-stu-id="79c5e-158">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="79c5e-159">ユーザーは、オブジェクト全体を移動する、境界ボックス、回転するエッジ アフォーおよびの操作のジェスチャに適用できます、coner アフォーを一様にスケールします。</span><span class="sxs-lookup"><span data-stu-id="79c5e-159">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate and on the coner affordances to scale uniformly.</span></span> <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="79c5e-160">非アフォー ダンス ベースの操作</span><span class="sxs-lookup"><span data-stu-id="79c5e-160">Non-affordance based manipulation</span></span>
<span data-ttu-id="79c5e-161">ユーザーは、境界ボックスを表示し、直接操作のジェスチャ適用手光線をポイントします。</span><span class="sxs-lookup"><span data-stu-id="79c5e-161">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="79c5e-162">1 つの手で平行移動とオブジェクトの回転は、モーション センサーとして手のアイコンの向きに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-162">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="79c5e-163">ユーザーが変換できます両手には、スケールし、2 つのハンドの動作を相対に従って回転します。</span><span class="sxs-lookup"><span data-stu-id="79c5e-163">With two hands, users can translate, scale and rotate it according to relative motions of two hands.</span></span><br>

<br>

## <a name="instinctual-gesturers"></a><span data-ttu-id="79c5e-164">Instinctual gesturers</span><span class="sxs-lookup"><span data-stu-id="79c5e-164">Instinctual gesturers</span></span>
<span data-ttu-id="79c5e-165">ポイントおよびコミット instinctual ジェスチャの概念は、直接操作する場合に似ています。</span><span class="sxs-lookup"><span data-stu-id="79c5e-165">The concept of instinctual gestures for point and commit is similar to that for direct manipulation.</span></span> <span data-ttu-id="79c5e-166">3D オブジェクトに対して実行すると、ユーザー ジェスチャには UI アフォーの設計によって示されます。</span><span class="sxs-lookup"><span data-stu-id="79c5e-166">The gestures users are suppose to perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="79c5e-167">たとえば、小さなコントロール ポイントでは、ユーザーは、すべて 5 本の指による大規模なオブジェクトを取得するときに、親指と人差し指でピンチにユーザーをきっかけ。</span><span class="sxs-lookup"><span data-stu-id="79c5e-167">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all 5 fingers.</span></span>

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="79c5e-168">ハンドと 6 の自由度のコント ローラー間の対称のデザイン</span><span class="sxs-lookup"><span data-stu-id="79c5e-168">Symmetric design between hands and 6 DoF controller</span></span> 
<span data-ttu-id="79c5e-169">ポイントとの対話の相手側のコミットの概念が最初に作成されの混合現実ポータル (MRP)、ユーザーが、イマーシブ ヘッドセットを帽し、アニメーション コント ローラーを使用して 3D オブジェクトの対話を定義します。</span><span class="sxs-lookup"><span data-stu-id="79c5e-169">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP), where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="79c5e-170">アニメーション コント ローラーは、ポイントと、相手側のオブジェクトの操作を行う光線を撮影してください。</span><span class="sxs-lookup"><span data-stu-id="79c5e-170">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="79c5e-171">さらにさまざまな操作をコミットするためのコント ローラーでは、ボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="79c5e-171">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="79c5e-172">光線の相互作用モデルを利用し、両手にそれらをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="79c5e-172">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="79c5e-173">この対称の設計では、MRP に慣れているユーザーが HoloLen 2 を使用するときにまでポイント、および操作のもう 1 つの相互作用モデルを学習する必要はありませんし、その逆です。</span><span class="sxs-lookup"><span data-stu-id="79c5e-173">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a><span data-ttu-id="79c5e-174">Instinctual ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="79c5e-174">Instinctual gestures</span></span>

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a><span data-ttu-id="79c5e-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="79c5e-175">See also</span></span>
* [<span data-ttu-id="79c5e-176">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="79c5e-176">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="79c5e-177">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="79c5e-177">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="79c5e-178">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="79c5e-178">Instinctual interactions</span></span>](interaction-fundamentals.md)

