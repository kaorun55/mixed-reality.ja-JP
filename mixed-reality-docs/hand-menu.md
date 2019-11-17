---
title: ハンドメニュー
description: メニューを使用すると、ユーザーは頻繁に使用される関数のための直接の UI をすぐに表示できます。 これらは、メニューのベストプラクティスと推奨事項です。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: ハンド、メニュー、ボタン、クイックアクセス、レイアウト
ms.openlocfilehash: c53fdc4ea6f3243cf906ee1916a9c234d0fce6ca
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143176"
---
# <a name="hand-menu"></a><span data-ttu-id="9eca4-105">ハンドメニュー</span><span class="sxs-lookup"><span data-stu-id="9eca4-105">Hand menu</span></span>

![Ulnar side location](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="9eca4-107">メニューを使用すると、ユーザーは頻繁に使用される関数のための直接の UI をすぐに表示できます。</span><span class="sxs-lookup"><span data-stu-id="9eca4-107">Hand menus allow users to quickly bring up hand-attached UI for frequently used functions.</span></span> 

<span data-ttu-id="9eca4-108">メニューについては、以下のベストプラクティスをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9eca4-108">Below are the best practices we have found for hand menus.</span></span> <span data-ttu-id="9eca4-109">また、 [Mrtk](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)の手の形を示すシーンの例も見つかります。</span><span class="sxs-lookup"><span data-stu-id="9eca4-109">You can also find an example scene demonstrating the hand menu in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span></span>

<br>

---

## <a name="behavior-best-practices"></a><span data-ttu-id="9eca4-110">動作のベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="9eca4-110">Behavior best practices</span></span>
<span data-ttu-id="9eca4-111">**A. ボタンの数を小さく**します。ハンドロックされたメニューと目の間の距離が近づいているため、またはユーザーが比較的小さな視覚面に焦点を当てる傾向がある場合 (attentional コーンは約10度)、お勧めします。ボタンの数を小さくします。</span><span class="sxs-lookup"><span data-stu-id="9eca4-111">**A. Keep the number of buttons small:** Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="9eca4-112">この探索に基づいて、3つのボタンがある1つの列は、ユーザーが視界の中央に移動した場合でも、ビューのフィールド (視界) 内のすべてのコンテンツを保持することで効果的に機能します。</span><span class="sxs-lookup"><span data-stu-id="9eca4-112">Based on our exploration, one column with three buttons work well by keeping all the content within the field of view (FOV) even when users move their hands to the center of the FOV.</span></span> 

<span data-ttu-id="9eca4-113">**B. 迅速な対処のために手のメニューを使用**します。 arm を持ち上げて位置を維持すると、arm の疲労が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="9eca4-113">**B. Utilize hand menu for quick action:** Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="9eca4-114">短い対話を必要とするメニューには、ハンドロックされたメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9eca4-114">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="9eca4-115">メニューが複雑で、対話時間の延長が必要な場合は、代わりにワールドロックまたは本体ロックを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="9eca4-115">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="9eca4-116">**C. ボタン/パネルアングル:** メニューは、両端が反対のショルダーと真ん中を持つようにする必要があります。これにより、自然な移動は反対の手でメニューと対話し、タッチするときに不快または不快な針を避けることができます。83'7b.</span><span class="sxs-lookup"><span data-stu-id="9eca4-116">**C. Button / Panel angle:** Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="9eca4-117">**D. ワンきき操作またはハンズフリー操作のサポートを検討する:** 両方のユーザーが常に使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="9eca4-117">**D. Consider supporting one-handed or hands-free operation:** Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="9eca4-118">一方または両方のハンズオンが使用できない場合は、さまざまなコンテキストを検討し、そのような状況に合わせて設計アカウントを確認します。</span><span class="sxs-lookup"><span data-stu-id="9eca4-118">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="9eca4-119">片手メニューをサポートするには、手動でロックしたときに、メニューの配置を手動でロックしてみてください。</span><span class="sxs-lookup"><span data-stu-id="9eca4-119">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="9eca4-120">ハンドフリーのシナリオでは、音声コマンドを使用して、メニューボタンを起動することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="9eca4-120">For hands-free scenarios, consider using a voice command to invoke the hand menu buttons.</span></span>

<span data-ttu-id="9eca4-121">**E. 2 段階の呼び出し:** ポップアップをイベントとして使用する場合は、不要になったときに誤って表示されることがあります (偽陽性)。これは、人が意図的に (通信とオブジェクトの操作のために) 自分を多く移動するためです。意図せずに。</span><span class="sxs-lookup"><span data-stu-id="9eca4-121">**E. Two-step invocation:** If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands a lot both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="9eca4-122">アプリで誤検知が発生した場合は、完全に開いた指などの手のメニューを呼び出すために、パームアップイベント以外に追加の手順を追加することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="9eca4-122">If you experience false-positives in your app, consider adding an additional step besides the palm-up event to invoke the hand menu such as fully opened fingers.</span></span>

<span data-ttu-id="9eca4-123">**F. 手首 (システムホームボタン) の近くにボタンを追加しないよう**にします。メニューボタンが [ホーム] ボタンの近くにある場合、メニューを操作しているときに誤ってトリガーされることがあります。</span><span class="sxs-lookup"><span data-stu-id="9eca4-123">**F. Avoid adding buttons near the wrist (system home button):** If the hand menu buttons are placed too close to the home button, it may get accidentally triggered while interacting with the hand menu.</span></span>

<span data-ttu-id="9eca4-124">**G. テスト、テスト、テスト:** 人間は、快適で不快感のためにさまざまなしきい値を持つさまざまな本体を持っています。設計をでテストし、さまざまなユーザーからフィードバックを受け取るようにしてください。</span><span class="sxs-lookup"><span data-stu-id="9eca4-124">**G. Test, test, test:** People have different bodies, with different thresholds for comfort and discomfort, etc. Be sure to test out your design on and get feedback from a variety of people.</span></span>

<br>

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="9eca4-125">手動によるメニューの配置のベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="9eca4-125">Hand menu placement best practices</span></span>

<span data-ttu-id="9eca4-126">人間の構造では、ulnar は ulnar のボーンの近くで実行されます。</span><span class="sxs-lookup"><span data-stu-id="9eca4-126">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="9eca4-127">Ulna は、l 肘から最小の指まで伸縮する長い骨の中にあります。</span><span class="sxs-lookup"><span data-stu-id="9eca4-127">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="9eca4-128">次に、探索に基づく2つの推奨される配置を示します。</span><span class="sxs-lookup"><span data-stu-id="9eca4-128">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="9eca4-129">![Ulnar side location](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="9eca4-129">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="9eca4-130">**Palm 内部の Ulnar**</span><span class="sxs-lookup"><span data-stu-id="9eca4-130">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="9eca4-131">この位置は、両手が互いに重ならないため、信頼性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="9eca4-131">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="9eca4-132">これは、正確な手動検出と追跡に不可欠です。</span><span class="sxs-lookup"><span data-stu-id="9eca4-132">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9eca4-133">![Ulnar side location](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="9eca4-133">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="9eca4-134">**B. Ulnar (手動)**</span><span class="sxs-lookup"><span data-stu-id="9eca4-134">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="9eca4-135">この場所はユーザーにとって使いやすいものです。ユーザーは arm を起動して、手のメニューと対話する必要がないからです。</span><span class="sxs-lookup"><span data-stu-id="9eca4-135">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="9eca4-136">メニュー **13cm**をパームの上に配置し、ボタンを ulnar palm の内側に配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9eca4-136">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="9eca4-137">最適なボタンサイズの詳細を確認する</span><span class="sxs-lookup"><span data-stu-id="9eca4-137">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="9eca4-138">技術的な理由により、この場所は1つの必須の実装にすることをお勧めします。開発者は、ユーザーの反対側がこのメニューを操作するために終了した後で、メニューを固定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9eca4-138">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="9eca4-139">これにより、jitteriness が重複しないようにすることができ、ボタンをより高速にターゲット設定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9eca4-139">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="9eca4-140">HoloLens 2 カメラは、互いに独立しているときに正確に識別します。</span><span class="sxs-lookup"><span data-stu-id="9eca4-140">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="9eca4-141">両手が重なると、メニューがアンカー位置から離れてしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9eca4-141">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="9eca4-142">推奨されないメニュー位置</span><span class="sxs-lookup"><span data-stu-id="9eca4-142">Menu positions that are not recommended</span></span>
<span data-ttu-id="9eca4-143">さまざまなメニューのレイアウトや場所を使用したユーザーの調査を行っていますが、次のメニューの場所は推奨されて**いません**。以下の各研究の欠点を確認してください。</span><span class="sxs-lookup"><span data-stu-id="9eca4-143">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="9eca4-144">arm](images/AboveArm.gif) 上の ![</span><span class="sxs-lookup"><span data-stu-id="9eca4-144">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="9eca4-145">**Arm の上**</span><span class="sxs-lookup"><span data-stu-id="9eca4-145">**Above the arm**</span></span><br>
        <span data-ttu-id="9eca4-146">1-適切な追跡を維持することが困難</span><span class="sxs-lookup"><span data-stu-id="9eca4-146">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="9eca4-147">2-不自然な位置が原因でユーザーの疲労が発生する</span><span class="sxs-lookup"><span data-stu-id="9eca4-147">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9eca4-148">![指](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="9eca4-148">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="9eca4-149">**上の指**</span><span class="sxs-lookup"><span data-stu-id="9eca4-149">**Above fingers**</span></span><br>
        <span data-ttu-id="9eca4-150">長い時間を保持することによる1手の疲労</span><span class="sxs-lookup"><span data-stu-id="9eca4-150">1 - Hand fatigue due to holding hand for long time</span></span><br>
        <span data-ttu-id="9eca4-151">インデックスとミドルフィンガーでの2ハンドトラッキングの問題</span><span class="sxs-lookup"><span data-stu-id="9eca4-151">2 - Hand tracking issues on index and middle finger</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="9eca4-152">中央の](images/handCenter.gif) の ![</span><span class="sxs-lookup"><span data-stu-id="9eca4-152">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="9eca4-153">**上-中央のパーム**</span><span class="sxs-lookup"><span data-stu-id="9eca4-153">**Above-center palm**</span></span><br>
        <span data-ttu-id="9eca4-154">両手が重なっているために問題を追跡する</span><span class="sxs-lookup"><span data-stu-id="9eca4-154">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="9eca4-155">メニューと対話するためにハンドを長時間保持することによる2ハンドの疲労</span><span class="sxs-lookup"><span data-stu-id="9eca4-155">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9eca4-156">top**指先**の ![top 指先](images/TopFingerTip.gif)</span><span class="sxs-lookup"><span data-stu-id="9eca4-156">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="9eca4-157">1ハンドトラッキングの問題</span><span class="sxs-lookup"><span data-stu-id="9eca4-157">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="9eca4-158">標準の姿勢を超える2ハンドの疲労</span><span class="sxs-lookup"><span data-stu-id="9eca4-158">2 - Hand fatigue holding hand above normal posture</span></span><br>
        <span data-ttu-id="9eca4-159">3-指間のスペースが限られているために偶発的に他の指でボタンを押す問題</span><span class="sxs-lookup"><span data-stu-id="9eca4-159">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="9eca4-160">Arm](images/BackOfTheArm.gif) の ![戻します。</span><span class="sxs-lookup"><span data-stu-id="9eca4-160">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="9eca4-161">**Arm の背面**</span><span class="sxs-lookup"><span data-stu-id="9eca4-161">**Back of the arm**</span></span><br>
        <span data-ttu-id="9eca4-162">1-事故によってホームボタンをトリガーできる</span><span class="sxs-lookup"><span data-stu-id="9eca4-162">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="9eca4-163">2-ユーザーに自然な、または使いやすい位置</span><span class="sxs-lookup"><span data-stu-id="9eca4-163">2 - Not a natural or comfortable position for users</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="9eca4-164">Unity の MRTK (Mixed Reality Toolkit) の手の形のメニュー</span><span class="sxs-lookup"><span data-stu-id="9eca4-164">Hand menu in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="9eca4-165">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、ハンドメニューのスクリプトとサンプルシーンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9eca4-165">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="9eca4-166">HandConstraintPalmUp ソルバースクリプトを使用すると、さまざまな構成可能なオプションを使用して、任意のオブジェクトを簡単にアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="9eca4-166">HandConstraintPalmUp solver script allows you easily attach any objects to the hands with various configurable options.</span></span>

* [<span data-ttu-id="9eca4-167">HandConstraintPalmUp を使用した MRTK ハンドメニュー</span><span class="sxs-lookup"><span data-stu-id="9eca4-167">MRTK - Hand Menu with HandConstraint and HandConstraintPalmUp </span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)


<br>

---


## <a name="see-also"></a><span data-ttu-id="9eca4-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="9eca4-168">See also</span></span>

* [<span data-ttu-id="9eca4-169">カーソル</span><span class="sxs-lookup"><span data-stu-id="9eca4-169">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="9eca4-170">ハンドレイ</span><span class="sxs-lookup"><span data-stu-id="9eca4-170">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="9eca4-171">ボタン</span><span class="sxs-lookup"><span data-stu-id="9eca4-171">Button</span></span>](button.md)
* [<span data-ttu-id="9eca4-172">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="9eca4-172">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="9eca4-173">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="9eca4-173">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="9eca4-174">操作性</span><span class="sxs-lookup"><span data-stu-id="9eca4-174">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9eca4-175">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="9eca4-175">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="9eca4-176">Near メニュー</span><span class="sxs-lookup"><span data-stu-id="9eca4-176">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="9eca4-177">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="9eca4-177">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="9eca4-178">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="9eca4-178">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="9eca4-179">キーボード</span><span class="sxs-lookup"><span data-stu-id="9eca4-179">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="9eca4-180">ボタン</span><span class="sxs-lookup"><span data-stu-id="9eca4-180">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="9eca4-181">翻訳</span><span class="sxs-lookup"><span data-stu-id="9eca4-181">Slate</span></span>](slate.md)
* [<span data-ttu-id="9eca4-182">スライダー</span><span class="sxs-lookup"><span data-stu-id="9eca4-182">Slider</span></span>](slider.md)
* [<span data-ttu-id="9eca4-183">シェーダー</span><span class="sxs-lookup"><span data-stu-id="9eca4-183">Shader</span></span>](shader.md)
* [<span data-ttu-id="9eca4-184">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="9eca4-184">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="9eca4-185">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="9eca4-185">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="9eca4-186">表面の吸着</span><span class="sxs-lookup"><span data-stu-id="9eca4-186">Surface magnetism</span></span>](surface-magnetism.md)
