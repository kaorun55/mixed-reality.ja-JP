---
title: ターゲットを見つめます
description: すべての操作は、入力モードに関係なく、ユーザーが操作したい要素をターゲットに設定できることに基づいて成り立っています。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality、宝石、宝石のターゲット、相互作用、設計
ms.openlocfilehash: eddc832456b2ba0c6bc8955157d2c8e1a268e893
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829843"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="232c4-104">熟考</span><span class="sxs-lookup"><span data-stu-id="232c4-104">Gaze and dwell</span></span>
<span data-ttu-id="232c4-105">_音声_や_ハンドジェスチャ_との組み合わせなどの_コミット_を確認するには、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="232c4-105">There are lots of different ways to confirm a _commit_ such as combining gaze with _voice_ or _hand gestures_.</span></span>
<span data-ttu-id="232c4-106">ただし、ユーザーの手が混み合っている場合や、ユーザーが追跡できない場合 (たとえば、大規模な関税グローブを使用しているファクトリワーカー) には、いくつかのユーザーシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="232c4-106">There are several user scenarios though, in which users' hands may either be busy or cannot be tracked (e.g., factory workers with oversized heavy duty gloves).</span></span> <span data-ttu-id="232c4-107">ユーザー設定、ソーシャルコンテキスト、または大きな環境が原因で、音声入力を使用できない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="232c4-107">Voice input may also not be available due to user preferences, social context or loud environments.</span></span>
<span data-ttu-id="232c4-108">フォールバックソリューションとして、_コミット_を実行するもう1つのオプションは、_熟考_と呼ばれる UI 要素を使用したままにすることです。</span><span class="sxs-lookup"><span data-stu-id="232c4-108">As a fallback solution another option to perform a _commit_ is simply to keep staring at a UI element which we refer to as _dwell_.</span></span>
<span data-ttu-id="232c4-109">_熟考_は、ヘッドまたは視線で実行できます。</span><span class="sxs-lookup"><span data-stu-id="232c4-109">A _dwell_ can be performed with either head or eye gaze.</span></span> <span data-ttu-id="232c4-110">考え方は単純で、次のフェーズで分類できます。</span><span class="sxs-lookup"><span data-stu-id="232c4-110">The idea is simple and can be broken down in the following phases:</span></span> 
1. <span data-ttu-id="232c4-111">Holographic ボタンでユーザーが起動を開始する</span><span class="sxs-lookup"><span data-stu-id="232c4-111">User starts gazing at a holographic button</span></span>

2. <span data-ttu-id="232c4-112">短い待機時間 (150 ミリ秒など) の後に、一部のビジュアルフィードバックアニメーションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="232c4-112">After a brief onset delay (e.g., 150 ms) some visual feedback animation is started.</span></span> <span data-ttu-id="232c4-113">遅延時間は、即座にフィードバックをすぐにポップアップすることによってユーザーの過負荷を避けるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="232c4-113">The onset delay is used to avoid overwhelming the user by immediately popping up feedback all the time.</span></span>
    - <span data-ttu-id="232c4-114">_目を見つめ_た場合は、次のことをお勧めします。これは、visual 熟考のフィードバックの設計に関するものです。</span><span class="sxs-lookup"><span data-stu-id="232c4-114">For _eye gaze_, we recommend the following for the design of the visual dwell feedback:</span></span>
      - <span data-ttu-id="232c4-115">**Blend**:最初から見えないものから完全に不透明なフィードバックをスムーズに blend します。</span><span class="sxs-lookup"><span data-stu-id="232c4-115">**Blend it**: Smoothly blend in the feedback from barely visible at first to fully opaque.</span></span> <span data-ttu-id="232c4-116">これにより、ユーザーが本当にこのボタンを使用していることがシステムによって overwhleming されるという安心感が得られます。</span><span class="sxs-lookup"><span data-stu-id="232c4-116">This makes the feedback less distracting and overwhleming and nicely aligns with the confidence that the system has that the user really wants to engage with this button.</span></span>
      - <span data-ttu-id="232c4-117">**プル**する:視覚的なフィードバックは、サイズを小さくしてターゲットの中心に向かって移動し、ユーザーの視覚的な注意を引くことで作成します。</span><span class="sxs-lookup"><span data-stu-id="232c4-117">**Pull it in**: Create a visual feedback than decreases in size and moves towards the center of the target, pulling in the user's visual attention.</span></span> 

3. <span data-ttu-id="232c4-118">定義済みの熟考 duration (たとえば、800ミリ秒) が経過すると、熟考が完了し、関連付けられたイベントがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="232c4-118">After a pre-defined dwell duration (e.g., 800 ms), the dwell completes and an associated event is triggered.</span></span>
    - <span data-ttu-id="232c4-119">現在、項目が選択されていることを実際にホームにするために、最終聴覚や視覚的なフィードバックを提供しています。</span><span class="sxs-lookup"><span data-stu-id="232c4-119">Provide some finalizing auditory or visual feedback to really bring home that the item got selected now.</span></span>

![熟考の状態](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a><span data-ttu-id="232c4-121">ターゲットを見つめます</span><span class="sxs-lookup"><span data-stu-id="232c4-121">Gaze targeting</span></span>

<span data-ttu-id="232c4-122">すべての操作は、入力モードに関係なく、ユーザーが操作したい要素をターゲットに設定できることに基づいて成り立っています。</span><span class="sxs-lookup"><span data-stu-id="232c4-122">All interactions are built upon the ability of a user to target the element they want to interact with, regardless of the input modality.</span></span> <span data-ttu-id="232c4-123">Windows Mixed Reality では、これは、通常はユーザーの視線入力を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="232c4-123">In Windows Mixed Reality, this is generally done using the user's gaze.</span></span>

<span data-ttu-id="232c4-124">ユーザーがエクスペリエンスを正常に使用できるようにするには、ユーザーの意図に対する計算されたシステムの理解と、ユーザーの実際の意図に、できる限り忠実に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="232c4-124">To enable a user to work with an experience successfully, the system's calculated understanding of a user's intent, and the user's actual intent, must align as closely as possible.</span></span> <span data-ttu-id="232c4-125">システムがユーザーの意図したアクションを正しく解釈するレベルまで、満足度が高くなりパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="232c4-125">To the degree that the system interprets the user's intended actions correctly, satisfaction increases and performance improves.</span></span>

## <a name="device-support"></a><span data-ttu-id="232c4-126">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="232c4-126">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="232c4-127"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="232c4-127"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="232c4-128"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="232c4-128"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="232c4-129"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="232c4-129"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="232c4-130"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="232c4-130"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="232c4-131">ターゲットを見つめます</span><span class="sxs-lookup"><span data-stu-id="232c4-131">Gaze targeting</span></span></td>
        <td><span data-ttu-id="232c4-132">✔️</span><span class="sxs-lookup"><span data-stu-id="232c4-132">✔️</span></span></td>
        <td><span data-ttu-id="232c4-133">✔️</span><span class="sxs-lookup"><span data-stu-id="232c4-133">✔️</span></span></td>
        <td><span data-ttu-id="232c4-134">✔️</span><span class="sxs-lookup"><span data-stu-id="232c4-134">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="232c4-135">視点をターゲットにする</span><span class="sxs-lookup"><span data-stu-id="232c4-135">Eye targeting</span></span></td>
        <td><span data-ttu-id="232c4-136">❌</span><span class="sxs-lookup"><span data-stu-id="232c4-136">❌</span></span></td>
        <td><span data-ttu-id="232c4-137">✔️</span><span class="sxs-lookup"><span data-stu-id="232c4-137">✔️</span></span></td>
        <td><span data-ttu-id="232c4-138">❌</span><span class="sxs-lookup"><span data-stu-id="232c4-138">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="232c4-139">HoloLens 2 に固有のその他のガイダンスは[近日対応予定](index.md)です。</span><span class="sxs-lookup"><span data-stu-id="232c4-139">More guidance specific to HoloLens 2 [coming soon](index.md).</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="232c4-140">ターゲットのサイズ設定とフィードバック</span><span class="sxs-lookup"><span data-stu-id="232c4-140">Target sizing and feedback</span></span>

<span data-ttu-id="232c4-141">視線入力ベクトルは、細かいターゲット設定はできなくても大まかなターゲット設定 (若干大きめのターゲットの取得) には最適であることは、繰り返し示されています。</span><span class="sxs-lookup"><span data-stu-id="232c4-141">The gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting (acquiring somewhat larger targets).</span></span> <span data-ttu-id="232c4-142">ターゲットのサイズが最小 1 ～ 1.5 度では、ほとんどのシナリオでユーザーのアクションが成功するはずですが、3 度のターゲットでは、多くの場合、速度がより速いことが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="232c4-142">Minimum target sizes of 1 to 1.5 degrees should allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="232c4-143">ユーザーがターゲットに設定するサイズは、3D 要素であっても実質的に 2D 領域であり、それが面しているどの投影もターゲット設定可能な領域になるはずです。</span><span class="sxs-lookup"><span data-stu-id="232c4-143">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="232c4-144">要素が "アクティブ" である (ユーザーがそれをターゲットにしている) という目立った合図を示すことは非常に役に立ちます。これには、目に見える "ホバー" 効果、音声のハイライトやクリック、要素へのカーソルの明確な配置などの処理が含まれます。</span><span class="sxs-lookup"><span data-stu-id="232c4-144">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful - this can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="232c4-145">![2 m の距離での最適なターゲット サイズ](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="232c4-145">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="232c4-146">*2 m の距離での最適なターゲット サイズ*</span><span class="sxs-lookup"><span data-stu-id="232c4-146">*Optimal target size at 2 meter distance*</span></span>

<span data-ttu-id="232c4-147">![視線入力のターゲットとなるオブジェクトの強調表示の例](images/gazetargeting-highlighting-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="232c4-147">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-640px.jpg)</span></span><br>
<span data-ttu-id="232c4-148">*視線入力のターゲットとなるオブジェクトの強調表示の例*</span><span class="sxs-lookup"><span data-stu-id="232c4-148">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="232c4-149">ターゲットの配置</span><span class="sxs-lookup"><span data-stu-id="232c4-149">Target placement</span></span>

<span data-ttu-id="232c4-150">ユーザーは、自分の視野内の非常に高い位置や非常に低い位置にある UI 要素を見つけられないことが多く、ユーザーの意識は主に焦点が合っている部分 (通常はほぼ目の高さ) に集中しています。</span><span class="sxs-lookup"><span data-stu-id="232c4-150">Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level).</span></span> <span data-ttu-id="232c4-151">ほとんどのターゲットは目の高さあたりの適正な帯域に配置すると効果的です。</span><span class="sxs-lookup"><span data-stu-id="232c4-151">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="232c4-152">ユーザーは常に比較的小さい視覚野に焦点を合わせる傾向があることを考慮すると (注意の視円錐は約 10 度)、UI 要素を概念的に関連性のある度数にグループ化すれば、ユーザーが視線入力で領域内を移動する場合に、項目から項目への注意の連鎖動作を活用できます。</span><span class="sxs-lookup"><span data-stu-id="232c4-152">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="232c4-153">UI を設計する際は、HoloLens とイマーシブ ヘッドセットでは視野内に潜在的な大きなバリエーションがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="232c4-153">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="232c4-154">![Galaxy Explorer で視線入力のターゲット設定を容易にするためにグループ化された UI 要素の例](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="232c4-154">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="232c4-155">*Galaxy Explorer で視線入力のターゲット設定を容易にするためにグループ化された UI 要素の例*</span><span class="sxs-lookup"><span data-stu-id="232c4-155">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="232c4-156">ターゲット設定動作の向上</span><span class="sxs-lookup"><span data-stu-id="232c4-156">Improving targeting behaviors</span></span>

<span data-ttu-id="232c4-157">何かをターゲットにするというユーザーの意図を判断できる場合は (または、ほぼ間違いないと思われる場合は)、正しくターゲットに設定されているかのように、操作で "ニアミス" の試行を受け入れると非常に便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="232c4-157">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept "near miss" attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="232c4-158">Mixed Reality エクスペリエンスに組み込むことができる、成功する方法がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="232c4-158">There are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="gaze-stabilization-gravity-wells"></a><span data-ttu-id="232c4-159">宝石安定化 ("重心")</span><span class="sxs-lookup"><span data-stu-id="232c4-159">Gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="232c4-160">これは、ほとんど、または常にオンにしておくべきです。</span><span class="sxs-lookup"><span data-stu-id="232c4-160">This should be turned on most/all of the time.</span></span> <span data-ttu-id="232c4-161">この手法は、ユーザーに起こることのある頭や首の自然な小刻みな揺れを取り除きます。</span><span class="sxs-lookup"><span data-stu-id="232c4-161">This technique removes the natural head/neck jitters that users may have.</span></span> <span data-ttu-id="232c4-162">また、見たり話したりする動作による動きも取り除きます。</span><span class="sxs-lookup"><span data-stu-id="232c4-162">Also movement due to looking/speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="232c4-163">最も近いリンク アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="232c4-163">Closest link algorithms</span></span>

<span data-ttu-id="232c4-164">これらは対話型コンテンツが少ない領域で最大の効果を発揮します。</span><span class="sxs-lookup"><span data-stu-id="232c4-164">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="232c4-165">ユーザーが何を操作しようとしていたのかを判断できる可能性が高い場合は、ある程度の意図を想定するだけで、ターゲット設定機能を補完できます。</span><span class="sxs-lookup"><span data-stu-id="232c4-165">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by simply assuming some level of intent.</span></span>

### <a name="backdatingpostdating-actions"></a><span data-ttu-id="232c4-166">アクションをさかのぼって有効にする/後で有効にする</span><span class="sxs-lookup"><span data-stu-id="232c4-166">Backdating/postdating actions</span></span>

<span data-ttu-id="232c4-167">このメカニズムは、速度が必要なタスクに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="232c4-167">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="232c4-168">ユーザーが一連のターゲット/アクティブ化の処理を高速化する際には、何らかのインテントを想定し、ユーザーが tap の直前または少しの間にフォーカスを移動していたターゲットに対して (50 ミリ秒前/後に)*操作を実行*できないようにすることができます。初期テストで効果的です)。</span><span class="sxs-lookup"><span data-stu-id="232c4-168">When a user is moving through a series of targeting/activation maneuvers at speed, it can be useful to assume some intent and allow *missed steps* to act upon targets which the user had in focus slightly before or slightly after the tap (50ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="232c4-169">スムージング</span><span class="sxs-lookup"><span data-stu-id="232c4-169">Smoothing</span></span>

<span data-ttu-id="232c4-170">このメカニズムはパス設定の動きで役に立ち、自然な頭の動きの特性によるわずかな小刻みな揺れやぐらつきを減らします。</span><span class="sxs-lookup"><span data-stu-id="232c4-170">This mechanism is useful for pathing movements, reducing the slight jitter/wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="232c4-171">パス設定の動きをスムーズにするときは、時間の経過と共にではなく、動きのサイズ/距離によってスムーズにしてください。</span><span class="sxs-lookup"><span data-stu-id="232c4-171">When smoothing over pathing motions, smooth by size/distance of movements rather than over time</span></span>

### <a name="magnetism"></a><span data-ttu-id="232c4-172">磁性</span><span class="sxs-lookup"><span data-stu-id="232c4-172">Magnetism</span></span>

<span data-ttu-id="232c4-173">このメカニズムは、"最も近いリンク" アルゴリズムのより一般的なバージョンと考えることができます。つまり、ユーザーの意図に近づくために対話型レイアウトに関する知識を活用して、ユーザーがターゲットに近づくにつれてターゲットに向かってカーソルを描画したり、単にヒットボックスを増やしたりします。</span><span class="sxs-lookup"><span data-stu-id="232c4-173">This mechanism can be thought of as a more general version of "Closest link" algorithms - drawing a cursor toward a target, or simply increasing hitboxes (whether visibly or not) as users approach likely targets, using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="232c4-174">これは、小さいターゲットの場合は特に効果を発揮する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="232c4-174">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="232c4-175">焦点の持続性</span><span class="sxs-lookup"><span data-stu-id="232c4-175">Focus stickiness</span></span>

<span data-ttu-id="232c4-176">近くにあるどの対話型要素に焦点を合わせるかを判断するときは、現在焦点が合っている要素にバイアスを提供します。</span><span class="sxs-lookup"><span data-stu-id="232c4-176">When determining which nearby interactive elements to give focus to, provide a bias to the element that is currently focused.</span></span> <span data-ttu-id="232c4-177">これは、自然なノイズを含む 2 つの要素間の中間でさまよっているときの、焦点の不規則な切り替え動作を減らすのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="232c4-177">This will help reduce erratic focus switching behaviours when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="232c4-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="232c4-178">See also</span></span>
* [<span data-ttu-id="232c4-179">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="232c4-179">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="232c4-180">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="232c4-180">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="232c4-181">カーソル</span><span class="sxs-lookup"><span data-stu-id="232c4-181">Cursors</span></span>](cursors.md)
