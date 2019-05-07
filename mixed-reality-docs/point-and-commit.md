---
title: ポイントとコミット
description: ポイントとコミットの入力モデルの概要
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
keywords: 複合現実との対話を設計します。
ms.openlocfilehash: e0e9c97053734ac0125fce40be7ffe9afbd2dd68
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581312"
---
# <a name="point-and-commit"></a><span data-ttu-id="9443d-104">ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="9443d-104">Point and commit</span></span>
<span data-ttu-id="9443d-105">ポイントとコミットは、対象に選択し、2D のコンテンツとの距離を 3D オブジェクトを操作の入力モデル有効ユーザーです。</span><span class="sxs-lookup"><span data-stu-id="9443d-105">Point and commit is an input model enables users to target, select and manipulate 2D contents and 3D objects in a distance.</span></span> <span data-ttu-id="9443d-106">この"Far"操作方法は、人間が現実の世界と毎日の対話中には、navel 対話型エクスペリエンスです。</span><span class="sxs-lookup"><span data-stu-id="9443d-106">This "Far" interaction technique is a navel interactive experience that human being didn't really have during their daily interaction with the real world.</span></span> <span data-ttu-id="9443d-107">たとえば、スーパー ヒーローのビデオでは、磁気が問い合わせると、距離に手を使用して相手側のオブジェクトを操作できるが、人間が実際に行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="9443d-107">For example, in a super hero movie, Magneto is capable of reaching out and manipulating a far object via hands in a distance, but human can't do it in reality.</span></span> <span data-ttu-id="9443d-108">Microsoft HoloLens (AR) と Microsoft 複合現実 (VR) の両方で装備ユーザーこの魔法の電源の対話をより有効にするが、すばらしい経験 holographic の内容があるだけでなく、実際の物理的な制約を中断し、効率的です。</span><span class="sxs-lookup"><span data-stu-id="9443d-108">In both Microsoft HoloLens (AR) and Microsoft Mixed Reality (VR), we equip users this magical power, breaking the physical constraint of real world not only to have delightful experience with holographic contents but to make the interaction more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="9443d-109">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="9443d-109">Device support</span></span>
<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9443d-110"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="9443d-110"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="9443d-111"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="9443d-111"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="9443d-112"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="9443d-112"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="9443d-113"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9443d-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9443d-114">ポイントとコミット (ここまでの手による操作)</span><span class="sxs-lookup"><span data-stu-id="9443d-114">Point and commit (far hand interaction)</span></span></td>
        <td><span data-ttu-id="9443d-115">❌ がサポートされていません</span><span class="sxs-lookup"><span data-stu-id="9443d-115">❌ Not supported</span></span></td>
        <td><span data-ttu-id="9443d-116">推奨 ✔️</span><span class="sxs-lookup"><span data-stu-id="9443d-116">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="9443d-117">推奨 ✔️</span><span class="sxs-lookup"><span data-stu-id="9443d-117">✔️ Recommended</span></span></td>
    </tr>
</table>
<br>
<span data-ttu-id="9443d-118">HoloLens 2 で、新しいを思い起こさせます手動追跡システムを利用して、プライマリ入力モデルの 1 つされたポイントとコミットします。</span><span class="sxs-lookup"><span data-stu-id="9443d-118">Point and commit has been one of the primary input models on HoloLens 2, utilizing the new articulated hand tracking system.</span></span> <span data-ttu-id="9443d-119">この入力モデルもアニメーション コント ローラーを使用してイマーシブ ヘッドセットでプライマリ入力モデル。</span><span class="sxs-lookup"><span data-stu-id="9443d-119">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span> <span data-ttu-id="9443d-120">ヘッド視線を置換することを推奨する入力モデルをポイントし、コミットは HoloLens でコミットし、(第 1 世代)。</span><span class="sxs-lookup"><span data-stu-id="9443d-120">Point and Commit is the input model that we suggest to replace the Head Gaze and Commit on HoloLens (1st gen).</span></span> 

## <a name="hand-rays"></a><span data-ttu-id="9443d-121">光線の手の形</span><span class="sxs-lookup"><span data-stu-id="9443d-121">Hand rays</span></span>
<span data-ttu-id="9443d-122">HoloLens の 2、palm の中心から撮影手光線を作成します。</span><span class="sxs-lookup"><span data-stu-id="9443d-122">On HoloLens 2, we create a hand ray shooting out from the center of a palm.</span></span> <span data-ttu-id="9443d-123">射線が、手の形の拡張機能として扱われます。</span><span class="sxs-lookup"><span data-stu-id="9443d-123">The ray is treated as an extension of the hand.</span></span> <span data-ttu-id="9443d-124">ドーナツの形状カーソルは、hitted オブジェクトと射線が交差する場所を意味する光線の最後にアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="9443d-124">A donut shape cursor is attached at the end of the ray to imply the location where the ray intersects with a hitted object.</span></span> <span data-ttu-id="9443d-125">カーソルがアクセスしたオブジェクトでは、コマンドのジェスチャーをして手のアイコンから受け取ります。</span><span class="sxs-lookup"><span data-stu-id="9443d-125">The object that the cursor lands will receive gestural commands from the hand.</span></span> 

<span data-ttu-id="9443d-126">親指と人差し指をエア タップのジェスチャを実行するを使用して、非常に基本的なジェスチャー コマンドがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="9443d-126">The very basic gestural command is triggered by using thumb and index finger to perform air tap gesture.</span></span> <span data-ttu-id="9443d-127">ハンド レイ エア タップしてコミットし、使用すると、ユーザーはボタンやハイパーリンクを web コンテンツをアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="9443d-127">By using hand ray to point and air tap to commit, users can activate a button or a hyperlink on a web content.</span></span> <span data-ttu-id="9443d-128">複数の複合ジェスチャでは、ユーザーは web コンテンツを移動して、距離で 3D オブジェクトの操作の対応です。</span><span class="sxs-lookup"><span data-stu-id="9443d-128">With more composite gestures, users are capable of navigating the web content and manipulating 3D objects in a distance.</span></span> <span data-ttu-id="9443d-129">手光線のビジュアル デ ザインをポイントし、状態をコミットも反応。</span><span class="sxs-lookup"><span data-stu-id="9443d-129">The visual design of the hand ray should also react to point and commit states:</span></span> <br>
* <span data-ttu-id="9443d-130">ポインティングの状態に射線がインライン化、dash とドーナツ図形にカーソルが。</span><span class="sxs-lookup"><span data-stu-id="9443d-130">In the pointing state, the ray is dash lined, and the cursor is a donut shape.</span></span>
* <span data-ttu-id="9443d-131">コミットの状態で、ray が、実線に変わります、ドットにカーソルが縮小されます。</span><span class="sxs-lookup"><span data-stu-id="9443d-131">in the committing state, the ray turns into a solid line, and the cursor shrinks to a dot.</span></span><br><br>
![](images/Hand-Rays-720px.jpg)<br>

## <a name="transition-between-near-and-far"></a><span data-ttu-id="9443d-132">ほぼとの間で移行します。</span><span class="sxs-lookup"><span data-stu-id="9443d-132">Transition between near and far</span></span>
<span data-ttu-id="9443d-133">光線に出力するための人差し指を指すなど、特定のジェスチャを使用する代わりに解放および詳細のジェスチャー操作 5 本の指を予約に、palm の中心から伸びる射線をデザインします。</span><span class="sxs-lookup"><span data-stu-id="9443d-133">Instead of using specific gestures, such as pointing with index finger to direct the ray, we design the ray coming out from the center of the palm, releasing and reserving the five fingers for more gestural manipulations.</span></span> <span data-ttu-id="9443d-134">そのため、HoloLens 2 では、近距離と相手側の両方の相互作用をまったく手のジェスチャの同じセットをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9443d-134">Therefore, HoloLens 2 supports exactly the same set of hand gestures for both near and far interaction.</span></span> <span data-ttu-id="9443d-135">ユーザーはここまでの間のやり取りの近くにある、またはその逆の移行時に、その他の学習は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9443d-135">No additional learning is needed when users transit from near to far interactions, and vice versa.</span></span> <span data-ttu-id="9443d-136">ユーザーは、同じグラブ ジェスチャを使用して、さまざまな距離でオブジェクトを操作することができます。</span><span class="sxs-lookup"><span data-stu-id="9443d-136">Users can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="9443d-137">光線の呼び出しは、自動および近接のベースには。</span><span class="sxs-lookup"><span data-stu-id="9443d-137">The invocation of the rays is automatic and proximity based:</span></span> <br>
* <span data-ttu-id="9443d-138">arm の距離 (約 50 cm) に達しました内のオブジェクトは、光線がほぼ相互作用の促進に自動的にオフになります。</span><span class="sxs-lookup"><span data-stu-id="9443d-138">when an object is within arm reached distance (roughly 50 cm), the rays are turned off automatically encouraging for near interaction.</span></span> 
* <span data-ttu-id="9443d-139">オブジェクトは、50 cm 偏が、光線はオンにします。</span><span class="sxs-lookup"><span data-stu-id="9443d-139">When the object is farther than 50 cm, the rays are turned on.</span></span>

<span data-ttu-id="9443d-140">このメカニズムは、円滑かつシームレスに移行をより。</span><span class="sxs-lookup"><span data-stu-id="9443d-140">This mechanism makes the transition smooth and seamless.</span></span><br>
![](images/Transition-Between-Near-And-Far-720px.jpg)<br>

## <a name="2d-slate-interaction"></a><span data-ttu-id="9443d-141">2D のスレートの相互作用</span><span class="sxs-lookup"><span data-stu-id="9443d-141">2D slate interaction</span></span>
<span data-ttu-id="9443d-142">2D スレートは、web ブラウザーなどの 2D アプリのコンテンツをホストしている holographic コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="9443d-142">A 2D slate is a holographic container hosting 2D app contents, such as web browser.</span></span> <span data-ttu-id="9443d-143">エア タップしてコミットし、手動光線を使用することまで 2D スレートと対話するための設計概念です。</span><span class="sxs-lookup"><span data-stu-id="9443d-143">The design concept for far interacting with a 2D slate is to use hand rays to point and air tap to commit.</span></span><br>

<span data-ttu-id="9443d-144">スレートの定数を操作します。</span><span class="sxs-lookup"><span data-stu-id="9443d-144">For interacting with the slate contant:</span></span><br>

* <span data-ttu-id="9443d-145">ユーザーは、ハイパーリンクやボタンをアクティブにし、エア タップ ポイントできます。</span><span class="sxs-lookup"><span data-stu-id="9443d-145">Users can point at a hyperlink or a button, then air tap to activate it.</span></span> 
* <span data-ttu-id="9443d-146">ユーザーは、スレートのコンテンツを上下にスクロールするのにナビゲーション ジェスチャを実行するのに 1 つの手を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9443d-146">Users can use one hand to perform a navigation gesture to scroll a slate content up and down.</span></span> 
* <span data-ttu-id="9443d-147">ユーザーは、in および out スレートのコンテンツを拡大するのにナビゲーションのジェスチャを実行するのに 2 つの手を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9443d-147">Users can use two hands to perform navigation gestures to zoom in and out the slate content.</span></span><br><br>

![](images/2D-Slate-Interaction-Far-720px.jpg)<br>

<span data-ttu-id="9443d-148">2D を操作するためには、それ自体をスレートします。</span><span class="sxs-lookup"><span data-stu-id="9443d-148">For manipulating the 2D slate itself:</span></span><br>

* <span data-ttu-id="9443d-149">ユーザーは、コーナーまたはエッジに最も近い操作アフォー ダンスを明らかに手光線をポイントします。</span><span class="sxs-lookup"><span data-stu-id="9443d-149">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="9443d-150">操作のジェスチャをアフォー ダンスに適用すると、ユーザーは上隅にあるアフォー ダンスで統一されたスケーリングを実行でき、edge アフォー ダンス経由でスレートをリフローすることができます。</span><span class="sxs-lookup"><span data-stu-id="9443d-150">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="9443d-151">操作のジェスチャを 2D のスレートの上部にある holobar に適用すると、ユーザーは、全体のスレートを移動できます。</span><span class="sxs-lookup"><span data-stu-id="9443d-151">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the whole slate.</span></span><br>

<br>

## <a name="3d-object-manipulation"></a><span data-ttu-id="9443d-152">3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="9443d-152">3D object manipulation</span></span>
<span data-ttu-id="9443d-153">直接の操作はアフォー ダンス ベースの操作と非 affordnace ベースの操作、3 D オブジェクトを操作するユーザーの 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="9443d-153">In direct manipulation, there are two ways for users to manipulate 3D object, Affordance Based Manipulation and Non-affordnace Based Manipulation.</span></span> <span data-ttu-id="9443d-154">ポイントとコミットのモデルでは、ユーザーが手光線を正確に同じタスクを実現可能です。</span><span class="sxs-lookup"><span data-stu-id="9443d-154">In point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="9443d-155">その他の学習は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9443d-155">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="9443d-156">アフォー ダンス ベースの操作</span><span class="sxs-lookup"><span data-stu-id="9443d-156">Affordance based manipulation</span></span>
<span data-ttu-id="9443d-157">ユーザーは、ポイントし、境界ボックスと操作アフォーを明らかに手光線を使用します。</span><span class="sxs-lookup"><span data-stu-id="9443d-157">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="9443d-158">ユーザーは、オブジェクト全体を移動する、境界ボックス、回転するエッジ アフォーおよびの操作のジェスチャに適用できます、coner アフォーを一様にスケールします。</span><span class="sxs-lookup"><span data-stu-id="9443d-158">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate and on the coner affordances to scale uniformly.</span></span> <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="9443d-159">非アフォー ダンス ベースの操作</span><span class="sxs-lookup"><span data-stu-id="9443d-159">Non-affordance based manipulation</span></span>
<span data-ttu-id="9443d-160">ユーザーは、境界ボックスを表示し、直接操作のジェスチャ適用手光線をポイントします。</span><span class="sxs-lookup"><span data-stu-id="9443d-160">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="9443d-161">1 つの手で平行移動とオブジェクトの回転は、モーション センサーとして手のアイコンの向きに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="9443d-161">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="9443d-162">ユーザーが変換できます両手には、スケールし、2 つのハンドの動作を相対に従って回転します。</span><span class="sxs-lookup"><span data-stu-id="9443d-162">With two hands, users can translate, scale and rotate it according to relative motions of two hands.</span></span><br>

<br>

## <a name="instinctual-gesturers"></a><span data-ttu-id="9443d-163">Instinctual gesturers</span><span class="sxs-lookup"><span data-stu-id="9443d-163">Instinctual gesturers</span></span>
<span data-ttu-id="9443d-164">ポイントおよびコミット instinctual ジェスチャの概念は、同期を直接操作する場合です。</span><span class="sxs-lookup"><span data-stu-id="9443d-164">The concept of instinctual gestures for point and commit is in sync with that for direct manipulation.</span></span> <span data-ttu-id="9443d-165">3D オブジェクトに対して実行するジェスチャのユーザーであるとしますには UI アフォーの設計によって示されます。</span><span class="sxs-lookup"><span data-stu-id="9443d-165">What gestures users suppose to perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="9443d-166">小さなコントロール ポイントは、ユーザーが、大きなオブジェクトを使用する 5 つの人差し指を取得するユーザーは、親指と人差し指でピンチを起こさは。</span><span class="sxs-lookup"><span data-stu-id="9443d-166">A small control point would motivate users to pinch with thumb and index finger, while a large object makes users to grab with 5 finger.</span></span>

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="9443d-167">ハンドと 6 の自由度のコント ローラー間の対称のデザイン</span><span class="sxs-lookup"><span data-stu-id="9443d-167">Symmetric design between hands and 6 DoF controller</span></span> 
<span data-ttu-id="9443d-168">まず、相手側の対話のポイントとコミット モデルの概念が作成されの Mixed Reality ポータル (MRP)、ユーザーが、イマーシブ ヘッドセットを摩耗し、アニメーション コント ローラーを使用して、3 d オブジェクトとの対話を定義します。</span><span class="sxs-lookup"><span data-stu-id="9443d-168">The concept of point and commit model for far interaction is firstly created and defined for the Mixed Reality Portal (MRP), where users wear an immersive headset and interact with the 3d object via motion controllers.</span></span> <span data-ttu-id="9443d-169">アニメーション コント ローラーは、ポイントと、相手側のオブジェクトの操作を行う光線を撮影してください。</span><span class="sxs-lookup"><span data-stu-id="9443d-169">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="9443d-170">さまざまな機能をさらにコミットするためのコント ローラーでは、ボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="9443d-170">There are buttons on the controllers for further committing different functionalities.</span></span> <span data-ttu-id="9443d-171">光線の相互作用モデルを利用し、両手でそれらを接続します。</span><span class="sxs-lookup"><span data-stu-id="9443d-171">We leverage the interaction model of rays and attach them on both hands.</span></span> <span data-ttu-id="9443d-172">この対称の設計では、MRP に慣れているユーザーはポイントまでに、初めて HoloLen 2 を使用して、操作をもう 1 つの相互作用モデルを確認する必要はありませんし、その逆です。</span><span class="sxs-lookup"><span data-stu-id="9443d-172">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation while first time using HoloLen 2, and vice versa.</span></span>    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a><span data-ttu-id="9443d-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="9443d-173">See also</span></span>
* [<span data-ttu-id="9443d-174">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="9443d-174">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="9443d-175">直接操作</span><span class="sxs-lookup"><span data-stu-id="9443d-175">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9443d-176">操作の基礎</span><span class="sxs-lookup"><span data-stu-id="9443d-176">Interaction fundamentals</span></span>](interaction-fundamentals.md)
