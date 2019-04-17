---
title: 視線の先を対象とします。
description: すべての対話は、ユーザーの入力モードに関係なく、対話する要素を対象とする機能に基づいて構築します。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 実際には、視線の先、対象とする操作、視線の先を混合の設計します。
ms.openlocfilehash: c3225e27331f8afcda65469eb84fe5470bf6ee8c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600681"
---
# <a name="gaze-targeting"></a><span data-ttu-id="4c254-104">視線の先を対象とします。</span><span class="sxs-lookup"><span data-stu-id="4c254-104">Gaze targeting</span></span>

<span data-ttu-id="4c254-105">すべての対話は、ユーザーの入力モードに関係なく、対話する要素を対象とする機能に基づいて構築します。</span><span class="sxs-lookup"><span data-stu-id="4c254-105">All interactions are built upon the ability of a user to target the element they want to interact with, regardless of the input modality.</span></span> <span data-ttu-id="4c254-106">Windows Mixed Reality でこれは、一般に、ユーザーの視線の先を使用します。</span><span class="sxs-lookup"><span data-stu-id="4c254-106">In Windows Mixed Reality, this is generally done using the user's gaze.</span></span>

<span data-ttu-id="4c254-107">エクスペリエンスを正常に使用するユーザーを有効にするには、ユーザーの目的、およびユーザーの実際のインテントのシステムの計算については、できる限り忠実に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c254-107">To enable a user to work with an experience successfully, the system's calculated understanding of a user's intent, and the user's actual intent, must align as closely as possible.</span></span> <span data-ttu-id="4c254-108">程度にシステムがユーザーの意図した操作を解釈する正しく、満足度が増えるとパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="4c254-108">To the degree that the system interprets the user's intended actions correctly, satisfaction increases and performance improves.</span></span>

## <a name="device-support"></a><span data-ttu-id="4c254-109">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="4c254-109">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4c254-110">機能</span><span class="sxs-lookup"><span data-stu-id="4c254-110">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="4c254-111"><a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></span><span class="sxs-lookup"><span data-stu-id="4c254-111"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="4c254-112">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4c254-112">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="4c254-113"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="4c254-113"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="4c254-114">視線の先を対象とします。</span><span class="sxs-lookup"><span data-stu-id="4c254-114">Gaze targeting</span></span></td><td style="text-align: center;"> <span data-ttu-id="4c254-115">✔️</span><span class="sxs-lookup"><span data-stu-id="4c254-115">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="4c254-116">✔️</span><span class="sxs-lookup"><span data-stu-id="4c254-116">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="4c254-117">✔️</span><span class="sxs-lookup"><span data-stu-id="4c254-117">✔️</span></span> </td>
</tr><tr>
<td> <span data-ttu-id="4c254-118">監視対象とします。</span><span class="sxs-lookup"><span data-stu-id="4c254-118">Eye targeting</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"> <span data-ttu-id="4c254-119">✔️</span><span class="sxs-lookup"><span data-stu-id="4c254-119">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="4c254-120">HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。</span><span class="sxs-lookup"><span data-stu-id="4c254-120">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="4c254-121">ターゲットのサイズ変更とフィードバック</span><span class="sxs-lookup"><span data-stu-id="4c254-121">Target sizing and feedback</span></span>

<span data-ttu-id="4c254-122">視線入力ベクトルは正しく対象とするために使用するのには繰り返し示されていますが、gross ターゲット (取得若干大きくターゲット) に最も適した多くの場合。</span><span class="sxs-lookup"><span data-stu-id="4c254-122">The gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting (acquiring somewhat larger targets).</span></span> <span data-ttu-id="4c254-123">1.5 に 1 度の最小のターゲットのサイズは、3 度のターゲットが多くの場合より高速化を使用する場合、ほとんどのシナリオで成功したユーザーの操作を許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c254-123">Minimum target sizes of 1 to 1.5 degrees should allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="4c254-124">注いる対象ユーザーは 3D 要素の場合でも 2D 領域では効果的にサイズどのプロジェクションが直面する、ターゲット設定可能な領域があります。</span><span class="sxs-lookup"><span data-stu-id="4c254-124">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="4c254-125">要素が「アクティブ」(こと、ユーザーが対象にすること) があるいくつかの注目すべきキューが非常に役立つ - これを含めることができますを提供する処理などの表示「ホバー」効果やオーディオのハイライト、 をクリックまたは要素を使用してカーソルの配置をオフにします。</span><span class="sxs-lookup"><span data-stu-id="4c254-125">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful - this can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="4c254-126">![2 つのメーター距離にある最適なターゲット サイズ](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c254-126">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="4c254-127">*2 つのメーター距離にある最適なターゲット サイズ*</span><span class="sxs-lookup"><span data-stu-id="4c254-127">*Optimal target size at 2 meter distance*</span></span>

<span data-ttu-id="4c254-128">![視線の先の対象となるオブジェクトを強調表示の例](images/gazetargeting-highlighting-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c254-128">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-640px.jpg)</span></span><br>
<span data-ttu-id="4c254-129">*視線の先の対象となるオブジェクトを強調表示の例*</span><span class="sxs-lookup"><span data-stu-id="4c254-129">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="4c254-130">ターゲットの配置</span><span class="sxs-lookup"><span data-stu-id="4c254-130">Target placement</span></span>

<span data-ttu-id="4c254-131">ユーザーは、多くの場合、(通常は約監視レベル) にフォーカスがメインの周囲の領域で、注意のほとんどに重点を置いて、視野で非常に高または非常に低配置されている UI 要素を検索する失敗します。</span><span class="sxs-lookup"><span data-stu-id="4c254-131">Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level).</span></span> <span data-ttu-id="4c254-132">目のレベルによって適切なバンドでほとんどのターゲットを配置することができます。</span><span class="sxs-lookup"><span data-stu-id="4c254-132">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="4c254-133">ユーザーの傾向を与え、比較的小さな視覚的な領域 (ビジョンの attentional コーンは 10 度では約) いつでも、概念的に関連している度合いをまとめて UI 要素をグループに重点を活用できますから注意順行連鎖の動作項目のユーザーとして領域を通じて、視線の先に移動します。</span><span class="sxs-lookup"><span data-stu-id="4c254-133">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="4c254-134">UI を設計するときは、HoloLens、イマーシブ ヘッドセットとビューのフィールドに潜在的な大規模なバリエーションに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4c254-134">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="4c254-135">![Galaxy エクスプ ローラーで対象とする簡単視線の先のグループ化された UI 要素の例](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c254-135">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="4c254-136">*Galaxy エクスプ ローラーで対象とする簡単視線の先のグループ化された UI 要素の例*</span><span class="sxs-lookup"><span data-stu-id="4c254-136">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="4c254-137">ターゲットの動作の向上</span><span class="sxs-lookup"><span data-stu-id="4c254-137">Improving targeting behaviors</span></span>

<span data-ttu-id="4c254-138">何かを対象とするユーザーの意図を確認 (または密接に近似)、「ニアミス」が正しくを対象としていた場合と同様の対話に試行を受け入れるように非常に便利ですができます。</span><span class="sxs-lookup"><span data-stu-id="4c254-138">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept "near miss" attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="4c254-139">複合現実エクスペリエンスに組み込むことが成功したメソッドのいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="4c254-139">There are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="gaze-stabilization-gravity-wells"></a><span data-ttu-id="4c254-140">視線入力安定化 ("重力 wells")</span><span class="sxs-lookup"><span data-stu-id="4c254-140">Gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="4c254-141">これが有効にする時間のほとんどまたはすべて。</span><span class="sxs-lookup"><span data-stu-id="4c254-141">This should be turned on most/all of the time.</span></span> <span data-ttu-id="4c254-142">この手法は、自然な head/ネック ジッター可能性のあるユーザーを削除します。</span><span class="sxs-lookup"><span data-stu-id="4c254-142">This technique removes the natural head/neck jitters that users may have.</span></span> <span data-ttu-id="4c254-143">検索読み上げの動作が原因も移動します。</span><span class="sxs-lookup"><span data-stu-id="4c254-143">Also movement due to looking/speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="4c254-144">最も近いリンク アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4c254-144">Closest link algorithms</span></span>

<span data-ttu-id="4c254-145">これらは、スパースの対話型コンテンツ領域に最適な機能します。</span><span class="sxs-lookup"><span data-stu-id="4c254-145">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="4c254-146">対話する試行がユーザーを決定することができます可能性が高い場合は、単に一定レベルのインテントを想定して、ターゲットの能力を補うことができます。</span><span class="sxs-lookup"><span data-stu-id="4c254-146">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by simply assuming some level of intent.</span></span>

### <a name="backdatingpostdating-actions"></a><span data-ttu-id="4c254-147">Backdating 遅延アクション</span><span class="sxs-lookup"><span data-stu-id="4c254-147">Backdating/postdating actions</span></span>

<span data-ttu-id="4c254-148">このメカニズムは、速度が必要なタスクに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4c254-148">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="4c254-149">ユーザーは、一連の対象とする、アクティブ化の最適経路の速度で移動が、いくつかの目的を想定し、許可すると便利できます*手順が実行されなかった*ユーザーがいたフォーカスで若干の前後に若干タップ (ターゲットに対して操作を実行するには50 ミリ秒の前に、/後が初期テストで有効になります)。</span><span class="sxs-lookup"><span data-stu-id="4c254-149">When a user is moving through a series of targeting/activation maneuvers at speed, it can be useful to assume some intent and allow *missed steps* to act upon targets which the user had in focus slightly before or slightly after the tap (50ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="4c254-150">スムージング</span><span class="sxs-lookup"><span data-stu-id="4c254-150">Smoothing</span></span>

<span data-ttu-id="4c254-151">このメカニズムは、パスの移動、ヘッドの移動を自然な特性のため若干のジッター/補助の削減に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4c254-151">This mechanism is useful for pathing movements, reducing the slight jitter/wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="4c254-152">パスのモーション、時間の経過と共にではなく、動きの距離のサイズでスムーズに円滑化するとき</span><span class="sxs-lookup"><span data-stu-id="4c254-152">When smoothing over pathing motions, smooth by size/distance of movements rather than over time</span></span>

### <a name="magnetism"></a><span data-ttu-id="4c254-153">磁力</span><span class="sxs-lookup"><span data-stu-id="4c254-153">Magnetism</span></span>

<span data-ttu-id="4c254-154">このメカニズムはターゲットに向かって、カーソルを描画するか、単に (視覚的またはない) かどうかに hitboxes を増やす「リンクでは最も近い」アルゴリズムの一般的なバージョンとして考えることができます可能性の高い目標を実現するユーザーに、使用する対話型のレイアウトの知識優れたアプローチ ユーザーのものです。</span><span class="sxs-lookup"><span data-stu-id="4c254-154">This mechanism can be thought of as a more general version of "Closest link" algorithms - drawing a cursor toward a target, or simply increasing hitboxes (whether visibly or not) as users approach likely targets, using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="4c254-155">これは、小規模のターゲットの非常に強力なことができます。</span><span class="sxs-lookup"><span data-stu-id="4c254-155">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="4c254-156">フォーカスの持続性</span><span class="sxs-lookup"><span data-stu-id="4c254-156">Focus stickiness</span></span>

<span data-ttu-id="4c254-157">フォーカスを移す対話型の要素の近くに判断する、現在フォーカスが要素に、バイアスを提供します。</span><span class="sxs-lookup"><span data-stu-id="4c254-157">When determining which nearby interactive elements to give focus to, provide a bias to the element that is currently focused.</span></span> <span data-ttu-id="4c254-158">これは自然なノイズを含む 2 つの要素間の中間に浮動小数点の動作の切り替えが不規則のフォーカスの削減に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4c254-158">This will help reduce erratic focus switching behaviours when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c254-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c254-159">See also</span></span>
* [<span data-ttu-id="4c254-160">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="4c254-160">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="4c254-161">音声のデザイン</span><span class="sxs-lookup"><span data-stu-id="4c254-161">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="4c254-162">カーソル</span><span class="sxs-lookup"><span data-stu-id="4c254-162">Cursors</span></span>](cursors.md)
