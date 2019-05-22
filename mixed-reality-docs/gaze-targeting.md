---
title: 視線の先を対象とします。
description: すべての対話は、ユーザーの入力モードに関係なく、対話する要素を対象とする機能に基づいて構築します。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 実際には、視線の先、対象とする操作、視線の先を混合の設計します。
ms.openlocfilehash: bbacf9bc0039280b9944f2ad6616108d9ceae1cd
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974930"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="1d202-104">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="1d202-104">Gaze and dwell</span></span>
<span data-ttu-id="1d202-105">多くのことを確認するさまざまな方法がある、_コミット_視線の先との組み合わせなど_音声_または_ジェスチャを渡す_します。</span><span class="sxs-lookup"><span data-stu-id="1d202-105">There are lots of different ways to confirm a _commit_ such as combining gaze with _voice_ or _hand gestures_.</span></span>
<span data-ttu-id="1d202-106">あるいくつかのユーザー シナリオ、ユーザーの手がビジー状態か場合がありますまたは追跡することはできません (サイズの大きい頑丈 gloves でファクトリ ワーカーなど)。</span><span class="sxs-lookup"><span data-stu-id="1d202-106">There are several user scenarios though, in which users' hands may either be busy or cannot be tracked (e.g., factory workers with oversized heavy duty gloves).</span></span> <span data-ttu-id="1d202-107">音声入力できない場合がありますもユーザーの設定、ソーシャル コンテキストや騒々しい環境が原因です。</span><span class="sxs-lookup"><span data-stu-id="1d202-107">Voice input may also not be available due to user preferences, social context or loud environments.</span></span>
<span data-ttu-id="1d202-108">フォールバック ソリューションとして実行する別オプション、_コミット_見つめてと呼ばれる UI 要素を保持することだけが_について詳しく説明しません_します。</span><span class="sxs-lookup"><span data-stu-id="1d202-108">As a fallback solution another option to perform a _commit_ is simply to keep staring at a UI element which we refer to as _dwell_.</span></span>
<span data-ttu-id="1d202-109">A_熟考_ヘッドまたは目視線の先に実行できます。</span><span class="sxs-lookup"><span data-stu-id="1d202-109">A _dwell_ can be performed with either head or eye gaze.</span></span> <span data-ttu-id="1d202-110">考え方は単純で、次のフェーズに分けることができます。</span><span class="sxs-lookup"><span data-stu-id="1d202-110">The idea is simple and can be broken down in the following phases:</span></span> 
1. <span data-ttu-id="1d202-111">ユーザーが開始 gazing holographic ボタン</span><span class="sxs-lookup"><span data-stu-id="1d202-111">User starts gazing at a holographic button</span></span>

2. <span data-ttu-id="1d202-112">簡単な発症遅延 (たとえば、150 ミリ秒) 後にいくつかの視覚的なフィードバック アニメーションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="1d202-112">After a brief onset delay (e.g., 150 ms) some visual feedback animation is started.</span></span> <span data-ttu-id="1d202-113">開始されたときの遅延を使用して、すべての時間をフィードバックをすぐにポップアップで、ユーザーの混乱を回避します。</span><span class="sxs-lookup"><span data-stu-id="1d202-113">The onset delay is used to avoid overwhelming the user by immediately popping up feedback all the time.</span></span>
    - <span data-ttu-id="1d202-114">_目注視_ビジュアルのデザインは、次は、フィードバックを下げなければお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1d202-114">For _eye gaze_, we recommend the following for the design of the visual dwell feedback:</span></span>
      - <span data-ttu-id="1d202-115">**これを blend**:最初に完全に不透明で表示からのフィードバックでスムーズにブレンドします。</span><span class="sxs-lookup"><span data-stu-id="1d202-115">**Blend it**: Smoothly blend in the feedback from barely visible at first to fully opaque.</span></span> <span data-ttu-id="1d202-116">これによりより少ないシステムと overwhleming フィードバックは、システムでは、ユーザーが、このボタンと連絡を取るが本当に自信適切に揃えられます。</span><span class="sxs-lookup"><span data-stu-id="1d202-116">This makes the feedback less distracting and overwhleming and nicely aligns with the confidence that the system has that the user really wants to engage with this button.</span></span>
      - <span data-ttu-id="1d202-117">**プルすること**:サイズが低下し、ユーザーの visual 注意でプル、ターゲットの中心を目指して開発よりも、視覚的フィードバックを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d202-117">**Pull it in**: Create a visual feedback than decreases in size and moves towards the center of the target, pulling in the user's visual attention.</span></span> 

3. <span data-ttu-id="1d202-118">事前に定義されたドウェル期間 (例: 800 ms) の後、ドウェルを完了し、に関連するイベントがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="1d202-118">After a pre-defined dwell duration (e.g., 800 ms), the dwell completes and an associated event is triggered.</span></span>
    - <span data-ttu-id="1d202-119">音声ファイナライズによって提供または視覚的なフィードバックを実際にホームを項目が選択されているようになりました。</span><span class="sxs-lookup"><span data-stu-id="1d202-119">Provide some finalizing auditory or visual feedback to really bring home that the item got selected now.</span></span>

![状態について詳しく説明しません](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a><span data-ttu-id="1d202-121">視線の先を対象とします。</span><span class="sxs-lookup"><span data-stu-id="1d202-121">Gaze targeting</span></span>

<span data-ttu-id="1d202-122">すべての対話は、ユーザーの入力モードに関係なく、対話する要素を対象とする機能に基づいて構築します。</span><span class="sxs-lookup"><span data-stu-id="1d202-122">All interactions are built upon the ability of a user to target the element they want to interact with, regardless of the input modality.</span></span> <span data-ttu-id="1d202-123">Windows Mixed Reality でこれは、一般に、ユーザーの視線の先を使用します。</span><span class="sxs-lookup"><span data-stu-id="1d202-123">In Windows Mixed Reality, this is generally done using the user's gaze.</span></span>

<span data-ttu-id="1d202-124">エクスペリエンスを正常に使用するユーザーを有効にするには、ユーザーの目的、およびユーザーの実際のインテントのシステムの計算については、できる限り忠実に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d202-124">To enable a user to work with an experience successfully, the system's calculated understanding of a user's intent, and the user's actual intent, must align as closely as possible.</span></span> <span data-ttu-id="1d202-125">程度にシステムがユーザーの意図した操作を解釈する正しく、満足度が増えるとパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="1d202-125">To the degree that the system interprets the user's intended actions correctly, satisfaction increases and performance improves.</span></span>

## <a name="device-support"></a><span data-ttu-id="1d202-126">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="1d202-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1d202-127">機能</span><span class="sxs-lookup"><span data-stu-id="1d202-127">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="1d202-128"><a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></span><span class="sxs-lookup"><span data-stu-id="1d202-128"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="1d202-129">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1d202-129">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="1d202-130"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="1d202-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1d202-131">視線の先を対象とします。</span><span class="sxs-lookup"><span data-stu-id="1d202-131">Gaze targeting</span></span></td><td style="text-align: center;"> <span data-ttu-id="1d202-132">✔️</span><span class="sxs-lookup"><span data-stu-id="1d202-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1d202-133">✔️</span><span class="sxs-lookup"><span data-stu-id="1d202-133">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="1d202-134">✔️</span><span class="sxs-lookup"><span data-stu-id="1d202-134">✔️</span></span> </td>
</tr><tr>
<td> <span data-ttu-id="1d202-135">監視対象とします。</span><span class="sxs-lookup"><span data-stu-id="1d202-135">Eye targeting</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"> <span data-ttu-id="1d202-136">✔️</span><span class="sxs-lookup"><span data-stu-id="1d202-136">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="1d202-137">HoloLens 2 に固有のガイダンスについて[近日](index.md)します。</span><span class="sxs-lookup"><span data-stu-id="1d202-137">More guidance specific to HoloLens 2 [coming soon](index.md).</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="1d202-138">ターゲットのサイズ変更とフィードバック</span><span class="sxs-lookup"><span data-stu-id="1d202-138">Target sizing and feedback</span></span>

<span data-ttu-id="1d202-139">視線入力ベクトルは正しく対象とするために使用するのには繰り返し示されていますが、gross ターゲット (取得若干大きくターゲット) に最も適した多くの場合。</span><span class="sxs-lookup"><span data-stu-id="1d202-139">The gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting (acquiring somewhat larger targets).</span></span> <span data-ttu-id="1d202-140">1.5 に 1 度の最小のターゲットのサイズは、3 度のターゲットが多くの場合より高速化を使用する場合、ほとんどのシナリオで成功したユーザーの操作を許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d202-140">Minimum target sizes of 1 to 1.5 degrees should allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="1d202-141">注いる対象ユーザーは 3D 要素の場合でも 2D 領域では効果的にサイズどのプロジェクションが直面する、ターゲット設定可能な領域があります。</span><span class="sxs-lookup"><span data-stu-id="1d202-141">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="1d202-142">要素が「アクティブ」(こと、ユーザーが対象にすること) があるいくつかの注目すべきキューが非常に役立つ - これを含めることができますを提供する処理などの表示「ホバー」効果やオーディオのハイライト、 をクリックまたは要素を使用してカーソルの配置をオフにします。</span><span class="sxs-lookup"><span data-stu-id="1d202-142">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful - this can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="1d202-143">![2 つのメーター距離にある最適なターゲット サイズ](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1d202-143">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="1d202-144">*2 つのメーター距離にある最適なターゲット サイズ*</span><span class="sxs-lookup"><span data-stu-id="1d202-144">*Optimal target size at 2 meter distance*</span></span>

<span data-ttu-id="1d202-145">![視線の先の対象となるオブジェクトを強調表示の例](images/gazetargeting-highlighting-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1d202-145">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-640px.jpg)</span></span><br>
<span data-ttu-id="1d202-146">*視線の先の対象となるオブジェクトを強調表示の例*</span><span class="sxs-lookup"><span data-stu-id="1d202-146">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="1d202-147">ターゲットの配置</span><span class="sxs-lookup"><span data-stu-id="1d202-147">Target placement</span></span>

<span data-ttu-id="1d202-148">ユーザーは、多くの場合、(通常は約監視レベル) にフォーカスがメインの周囲の領域で、注意のほとんどに重点を置いて、視野で非常に高または非常に低配置されている UI 要素を検索する失敗します。</span><span class="sxs-lookup"><span data-stu-id="1d202-148">Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level).</span></span> <span data-ttu-id="1d202-149">目のレベルによって適切なバンドでほとんどのターゲットを配置することができます。</span><span class="sxs-lookup"><span data-stu-id="1d202-149">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="1d202-150">ユーザーの傾向を与え、比較的小さな視覚的な領域 (ビジョンの attentional コーンは 10 度では約) いつでも、概念的に関連している度合いをまとめて UI 要素をグループに重点を活用できますから注意順行連鎖の動作項目のユーザーとして領域を通じて、視線の先に移動します。</span><span class="sxs-lookup"><span data-stu-id="1d202-150">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="1d202-151">UI を設計するときは、HoloLens、イマーシブ ヘッドセットとビューのフィールドに潜在的な大規模なバリエーションに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1d202-151">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="1d202-152">![Galaxy エクスプ ローラーで対象とする簡単視線の先のグループ化された UI 要素の例](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1d202-152">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="1d202-153">*Galaxy エクスプ ローラーで対象とする簡単視線の先のグループ化された UI 要素の例*</span><span class="sxs-lookup"><span data-stu-id="1d202-153">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="1d202-154">ターゲットの動作の向上</span><span class="sxs-lookup"><span data-stu-id="1d202-154">Improving targeting behaviors</span></span>

<span data-ttu-id="1d202-155">何かを対象とするユーザーの意図を確認 (または密接に近似)、「ニアミス」が正しくを対象としていた場合と同様の対話に試行を受け入れるように非常に便利ですができます。</span><span class="sxs-lookup"><span data-stu-id="1d202-155">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept "near miss" attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="1d202-156">複合現実エクスペリエンスに組み込むことが成功したメソッドのいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="1d202-156">There are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="gaze-stabilization-gravity-wells"></a><span data-ttu-id="1d202-157">視線入力安定化 ("重力 wells")</span><span class="sxs-lookup"><span data-stu-id="1d202-157">Gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="1d202-158">これが有効にする時間のほとんどまたはすべて。</span><span class="sxs-lookup"><span data-stu-id="1d202-158">This should be turned on most/all of the time.</span></span> <span data-ttu-id="1d202-159">この手法は、自然な head/ネック ジッター可能性のあるユーザーを削除します。</span><span class="sxs-lookup"><span data-stu-id="1d202-159">This technique removes the natural head/neck jitters that users may have.</span></span> <span data-ttu-id="1d202-160">検索読み上げの動作が原因も移動します。</span><span class="sxs-lookup"><span data-stu-id="1d202-160">Also movement due to looking/speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="1d202-161">最も近いリンク アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="1d202-161">Closest link algorithms</span></span>

<span data-ttu-id="1d202-162">これらは、スパースの対話型コンテンツ領域に最適な機能します。</span><span class="sxs-lookup"><span data-stu-id="1d202-162">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="1d202-163">対話する試行がユーザーを決定することができます可能性が高い場合は、単に一定レベルのインテントを想定して、ターゲットの能力を補うことができます。</span><span class="sxs-lookup"><span data-stu-id="1d202-163">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by simply assuming some level of intent.</span></span>

### <a name="backdatingpostdating-actions"></a><span data-ttu-id="1d202-164">Backdating 遅延アクション</span><span class="sxs-lookup"><span data-stu-id="1d202-164">Backdating/postdating actions</span></span>

<span data-ttu-id="1d202-165">このメカニズムは、速度が必要なタスクに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1d202-165">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="1d202-166">ユーザーは、一連の対象とする、アクティブ化の最適経路の速度で移動が、いくつかの目的を想定し、許可すると便利できます*手順が実行されなかった*ユーザーがいたフォーカスで若干の前後に若干タップ (ターゲットに対して操作を実行するには50 ミリ秒の前に、/後が初期テストで有効になります)。</span><span class="sxs-lookup"><span data-stu-id="1d202-166">When a user is moving through a series of targeting/activation maneuvers at speed, it can be useful to assume some intent and allow *missed steps* to act upon targets which the user had in focus slightly before or slightly after the tap (50ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="1d202-167">スムージング</span><span class="sxs-lookup"><span data-stu-id="1d202-167">Smoothing</span></span>

<span data-ttu-id="1d202-168">このメカニズムは、パスの移動、ヘッドの移動を自然な特性のため若干のジッター/補助の削減に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1d202-168">This mechanism is useful for pathing movements, reducing the slight jitter/wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="1d202-169">パスのモーション、時間の経過と共にではなく、動きの距離のサイズでスムーズに円滑化するとき</span><span class="sxs-lookup"><span data-stu-id="1d202-169">When smoothing over pathing motions, smooth by size/distance of movements rather than over time</span></span>

### <a name="magnetism"></a><span data-ttu-id="1d202-170">磁力</span><span class="sxs-lookup"><span data-stu-id="1d202-170">Magnetism</span></span>

<span data-ttu-id="1d202-171">このメカニズムはターゲットに向かって、カーソルを描画するか、単に (視覚的またはない) かどうかに hitboxes を増やす「リンクでは最も近い」アルゴリズムの一般的なバージョンとして考えることができます可能性の高い目標を実現するユーザーに、使用する対話型のレイアウトの知識優れたアプローチ ユーザーのものです。</span><span class="sxs-lookup"><span data-stu-id="1d202-171">This mechanism can be thought of as a more general version of "Closest link" algorithms - drawing a cursor toward a target, or simply increasing hitboxes (whether visibly or not) as users approach likely targets, using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="1d202-172">これは、小規模のターゲットの非常に強力なことができます。</span><span class="sxs-lookup"><span data-stu-id="1d202-172">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="1d202-173">フォーカスの持続性</span><span class="sxs-lookup"><span data-stu-id="1d202-173">Focus stickiness</span></span>

<span data-ttu-id="1d202-174">フォーカスを移す対話型の要素の近くに判断する、現在フォーカスが要素に、バイアスを提供します。</span><span class="sxs-lookup"><span data-stu-id="1d202-174">When determining which nearby interactive elements to give focus to, provide a bias to the element that is currently focused.</span></span> <span data-ttu-id="1d202-175">これは自然なノイズを含む 2 つの要素間の中間に浮動小数点の動作の切り替えが不規則のフォーカスの削減に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1d202-175">This will help reduce erratic focus switching behaviours when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d202-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d202-176">See also</span></span>
* [<span data-ttu-id="1d202-177">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="1d202-177">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="1d202-178">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="1d202-178">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="1d202-179">カーソル</span><span class="sxs-lookup"><span data-stu-id="1d202-179">Cursors</span></span>](cursors.md)
