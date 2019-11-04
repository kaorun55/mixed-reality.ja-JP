---
title: ハンドメニュー
description: メニューを使用すると、ユーザーは頻繁に使用される関数のための直接の UI をすぐに表示できます。 これらは、メニューのベストプラクティスと推奨事項です。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: ハンド、メニュー、ボタン、クイックアクセス、レイアウト
ms.openlocfilehash: ee958806ac462535b33164bb4faa4bf1aa29e709
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439253"
---
# <a name="hand-menu"></a><span data-ttu-id="fad7c-105">ハンドメニュー</span><span class="sxs-lookup"><span data-stu-id="fad7c-105">Hand menu</span></span>

![Ulnar side location](images/MRTK_UX_HandMenu.png)

<span data-ttu-id="fad7c-107">メニューを使用すると、ユーザーは頻繁に使用される関数のための直接の UI をすぐに表示できます。</span><span class="sxs-lookup"><span data-stu-id="fad7c-107">Hand menus allow users to quickly bring up hand-attached UI for frequently used functions.</span></span> 

<span data-ttu-id="fad7c-108">メニューについては、以下のベストプラクティスをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fad7c-108">Below are the best practices we have found for hand menus.</span></span> <span data-ttu-id="fad7c-109">また、 [Mrtk](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)の手の形を示すシーンの例も見つかります。</span><span class="sxs-lookup"><span data-stu-id="fad7c-109">You can also find an example scene demonstrating the hand menu in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span></span>

<br>

---

## <a name="behavior-best-practices"></a><span data-ttu-id="fad7c-110">動作のベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="fad7c-110">Behavior best practices</span></span>
<span data-ttu-id="fad7c-111">**A. ボタンの数を小さく**します。ハンドロックされたメニューと目の間の距離が近づいているため、またはユーザーが比較的小さな視覚面に焦点を当てる傾向がある場合 (attentional コーンは約10度)、お勧めします。ボタンの数を小さくします。</span><span class="sxs-lookup"><span data-stu-id="fad7c-111">**A. Keep the number of buttons small:** Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="fad7c-112">この探索に基づいて、3つのボタンがある1つの列は、ユーザーが視界の中央に移動した場合でも、ビューのフィールド (視界) 内のすべてのコンテンツを保持することで効果的に機能します。</span><span class="sxs-lookup"><span data-stu-id="fad7c-112">Based on our exploration, one column with three buttons work well by keeping all the content within the field of view (FOV) even when users move their hands to the center of the FOV.</span></span> 

<span data-ttu-id="fad7c-113">**B. 迅速な対処のために手のメニューを使用**します。 arm を持ち上げて位置を維持すると、arm の疲労が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="fad7c-113">**B. Utilize hand menu for quick action:** Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="fad7c-114">短い対話を必要とするメニューには、ハンドロックされたメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="fad7c-114">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="fad7c-115">メニューが複雑で、対話時間の延長が必要な場合は、代わりにワールドロックまたは本体ロックを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="fad7c-115">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="fad7c-116">**C. ボタン/パネルアングル:** メニューは、両端が反対のショルダーと真ん中を持つようにする必要があります。これにより、自然な移動は反対の手でメニューと対話し、タッチするときに不快または不快な針を避けることができます。83'7b.</span><span class="sxs-lookup"><span data-stu-id="fad7c-116">**C. Button / Panel angle:** Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="fad7c-117">**D. ワンきき操作またはハンズフリー操作のサポートを検討する:** 両方のユーザーが常に使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="fad7c-117">**D. Consider supporting one-handed or hands-free operation:** Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="fad7c-118">一方または両方のハンズオンが使用できない場合は、さまざまなコンテキストを検討し、そのような状況に合わせて設計アカウントを確認します。</span><span class="sxs-lookup"><span data-stu-id="fad7c-118">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="fad7c-119">片手メニューをサポートするには、手動でロックしたときに、メニューの配置を手動でロックしてみてください。</span><span class="sxs-lookup"><span data-stu-id="fad7c-119">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="fad7c-120">ハンドフリーのシナリオでは、音声コマンドを使用して、メニューボタンを起動することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="fad7c-120">For hands-free scenarios, consider using a voice command to invoke the hand menu buttons.</span></span>

<span data-ttu-id="fad7c-121">**E. 2 段階の呼び出し:** ポップアップをイベントとして使用する場合は、不要になったときに誤って表示されることがあります (偽陽性)。これは、人が意図的に (通信とオブジェクトの操作のために) 自分を多く移動するためです。意図せずに。</span><span class="sxs-lookup"><span data-stu-id="fad7c-121">**E. Two-step invocation:** If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands a lot both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="fad7c-122">アプリで誤検知が発生した場合は、完全に開いた指などの手のメニューを呼び出すために、パームアップイベント以外に追加の手順を追加することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="fad7c-122">If you experience false-positives in your app, consider adding an additional step besides the palm-up event to invoke the hand menu such as fully opened fingers.</span></span>

<span data-ttu-id="fad7c-123">**F. 手首 (システムホームボタン) の近くにボタンを追加しないよう**にします。メニューボタンが [ホーム] ボタンの近くにある場合、メニューを操作しているときに誤ってトリガーされることがあります。</span><span class="sxs-lookup"><span data-stu-id="fad7c-123">**F. Avoid adding buttons near the wrist (system home button):** If the hand menu buttons are placed too close to the home button, it may get accidentally triggered while interacting with the hand menu.</span></span>

<span data-ttu-id="fad7c-124">**G. テスト、テスト、テスト:** 人間は、快適で不快感のためにさまざまなしきい値を持つさまざまな本体を持っています。設計をでテストし、さまざまなユーザーからフィードバックを受け取るようにしてください。</span><span class="sxs-lookup"><span data-stu-id="fad7c-124">**G. Test, test, test:** People have different bodies, with different thresholds for comfort and discomfort, etc. Be sure to test out your design on and get feedback from a variety of people.</span></span>

<br>

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="fad7c-125">手動によるメニューの配置のベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="fad7c-125">Hand menu placement best practices</span></span>

<span data-ttu-id="fad7c-126">人間の構造では、ulnar は ulnar のボーンの近くで実行されます。</span><span class="sxs-lookup"><span data-stu-id="fad7c-126">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="fad7c-127">Ulna は、l 肘から最小の指まで伸縮する長い骨の中にあります。</span><span class="sxs-lookup"><span data-stu-id="fad7c-127">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="fad7c-128">次に、探索に基づく2つの推奨される配置を示します。</span><span class="sxs-lookup"><span data-stu-id="fad7c-128">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="fad7c-129">![Ulnar side location](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="fad7c-129">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="fad7c-130">**Palm 内部の Ulnar**</span><span class="sxs-lookup"><span data-stu-id="fad7c-130">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="fad7c-131">この位置は、両手が互いに重ならないため、信頼性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="fad7c-131">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="fad7c-132">これは、正確な手動検出と追跡に不可欠です。</span><span class="sxs-lookup"><span data-stu-id="fad7c-132">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="fad7c-133">![Ulnar side location](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="fad7c-133">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="fad7c-134">**B. Ulnar (手動)**</span><span class="sxs-lookup"><span data-stu-id="fad7c-134">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="fad7c-135">この場所はユーザーにとって使いやすいものです。ユーザーは arm を起動して、手のメニューと対話する必要がないからです。</span><span class="sxs-lookup"><span data-stu-id="fad7c-135">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="fad7c-136">メニュー **13cm**をパームの上に配置し、ボタンを ulnar palm の内側に配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fad7c-136">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="fad7c-137">最適なボタンサイズの詳細を確認する</span><span class="sxs-lookup"><span data-stu-id="fad7c-137">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="fad7c-138">技術的な理由により、この場所は1つの必須の実装にすることをお勧めします。開発者は、ユーザーの反対側がこのメニューを操作するために終了した後で、メニューを固定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fad7c-138">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="fad7c-139">これにより、jitteriness が重複しないようにすることができ、ボタンをより高速にターゲット設定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="fad7c-139">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="fad7c-140">HoloLens 2 カメラは、互いに独立しているときに正確に識別します。</span><span class="sxs-lookup"><span data-stu-id="fad7c-140">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="fad7c-141">両手が重なると、メニューがアンカー位置から離れてしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fad7c-141">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="fad7c-142">推奨されないメニュー位置</span><span class="sxs-lookup"><span data-stu-id="fad7c-142">Menu positions that are not recommended</span></span>
<span data-ttu-id="fad7c-143">さまざまなメニューのレイアウトや場所を使用したユーザーの調査を行っていますが、次のメニューの場所は推奨されて**いません**。以下の各研究の欠点を確認してください。</span><span class="sxs-lookup"><span data-stu-id="fad7c-143">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="fad7c-144">arm](images/AboveArm.gif) 上の ![</span><span class="sxs-lookup"><span data-stu-id="fad7c-144">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="fad7c-145">**Arm の上**</span><span class="sxs-lookup"><span data-stu-id="fad7c-145">**Above the arm**</span></span><br>
        <span data-ttu-id="fad7c-146">1-適切な追跡を維持することが困難</span><span class="sxs-lookup"><span data-stu-id="fad7c-146">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="fad7c-147">2-不自然な位置が原因でユーザーの疲労が発生する</span><span class="sxs-lookup"><span data-stu-id="fad7c-147">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="fad7c-148">![指](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="fad7c-148">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="fad7c-149">**上の指**</span><span class="sxs-lookup"><span data-stu-id="fad7c-149">**Above fingers**</span></span><br>
        <span data-ttu-id="fad7c-150">長い時間を保持することによる1手の疲労</span><span class="sxs-lookup"><span data-stu-id="fad7c-150">1 - Hand fatigue due to holding hand for long time</span></span><br>
        <span data-ttu-id="fad7c-151">インデックスとミドルフィンガーでの2ハンドトラッキングの問題</span><span class="sxs-lookup"><span data-stu-id="fad7c-151">2 - Hand tracking issues on index and middle finger</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="fad7c-152">中央の](images/handCenter.gif) の ![</span><span class="sxs-lookup"><span data-stu-id="fad7c-152">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="fad7c-153">**上-中央のパーム**</span><span class="sxs-lookup"><span data-stu-id="fad7c-153">**Above-center palm**</span></span><br>
        <span data-ttu-id="fad7c-154">両手が重なっているために問題を追跡する</span><span class="sxs-lookup"><span data-stu-id="fad7c-154">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="fad7c-155">メニューと対話するためにハンドを長時間保持することによる2ハンドの疲労</span><span class="sxs-lookup"><span data-stu-id="fad7c-155">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="fad7c-156">top**指先**の ![top 指先](images/TopFingerTip.gif)</span><span class="sxs-lookup"><span data-stu-id="fad7c-156">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="fad7c-157">1ハンドトラッキングの問題</span><span class="sxs-lookup"><span data-stu-id="fad7c-157">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="fad7c-158">標準の姿勢を超える2ハンドの疲労</span><span class="sxs-lookup"><span data-stu-id="fad7c-158">2 - Hand fatigue holding hand above normal posture</span></span><br>
        <span data-ttu-id="fad7c-159">3-指間のスペースが限られているために偶発的に他の指でボタンを押す問題</span><span class="sxs-lookup"><span data-stu-id="fad7c-159">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="fad7c-160">Arm](images/BackOfTheArm.gif) の ![戻します。</span><span class="sxs-lookup"><span data-stu-id="fad7c-160">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="fad7c-161">**Arm の背面**</span><span class="sxs-lookup"><span data-stu-id="fad7c-161">**Back of the arm**</span></span><br>
        <span data-ttu-id="fad7c-162">1-事故によってホームボタンをトリガーできる</span><span class="sxs-lookup"><span data-stu-id="fad7c-162">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="fad7c-163">2-ユーザーに自然な、または使いやすい位置</span><span class="sxs-lookup"><span data-stu-id="fad7c-163">2 - Not a natural or comfortable position for users</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---


## <a name="see-also"></a><span data-ttu-id="fad7c-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="fad7c-164">See also</span></span>

* [<span data-ttu-id="fad7c-165">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="fad7c-165">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="fad7c-166">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="fad7c-166">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="fad7c-167">手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="fad7c-167">Hands and motion controllers</span></span>](hands-and-tools.md)
