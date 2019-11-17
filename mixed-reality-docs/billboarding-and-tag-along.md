---
title: Billboarding とタグに沿って
description: Billboarding を使用するオブジェクトは、常にユーザーに顔を合わせて向きます。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、billboarding、タグ
ms.openlocfilehash: ff2b1ce20174b1b9aecbb90b1d1dc3e8896b3761
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143131"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="961da-104">Billboarding とタグに沿って</span><span class="sxs-lookup"><span data-stu-id="961da-104">Billboarding and tag-along</span></span>

<br>

<img src="images/UX/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="961da-105">Billboarding とは</span><span class="sxs-lookup"><span data-stu-id="961da-105">What is billboarding?</span></span>

<span data-ttu-id="961da-106">Billboarding は、混合現実のオブジェクトに適用できる動作の概念です。</span><span class="sxs-lookup"><span data-stu-id="961da-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="961da-107">Billboarding を使用するオブジェクトは、常にユーザーに顔を合わせて向きます。</span><span class="sxs-lookup"><span data-stu-id="961da-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="961da-108">これは、ユーザーが移動した場合に、ユーザーの環境に配置されている静的オブジェクト (ワールドロック) が隠されたり、読み取り不可能になったりするテキストおよび menuing システムに特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="961da-108">This is especially helpful with text and menuing systems where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable if a user were to move around.</span></span>

<span data-ttu-id="961da-109">Billboarding が有効になっているオブジェクトは、ユーザーの環境で自由に回転できます。</span><span class="sxs-lookup"><span data-stu-id="961da-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="961da-110">また、設計上の考慮事項に応じて、1つの軸に制限することもできます。</span><span class="sxs-lookup"><span data-stu-id="961da-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="961da-111">Billboarded オブジェクトは、他のオブジェクトに近すぎるか、または HoloLens によってスキャンされたサーフェイスが終了した場合に、自身をクリップまたは occlude することができます。</span><span class="sxs-lookup"><span data-stu-id="961da-111">Keep in mind, billboarded objects may clip or occlude themselves if they are placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="961da-112">これを回避するには、billboarding に対して有効にした軸で回転したときにオブジェクトが生成する総フットプリントを考えてください。</span><span class="sxs-lookup"><span data-stu-id="961da-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="961da-113">タグとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="961da-113">What is a tag-along?</span></span>

<span data-ttu-id="961da-114">タグに加えて、ホログラムに追加できる動作の概念です。</span><span class="sxs-lookup"><span data-stu-id="961da-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="961da-115">タグに沿ったオブジェクトは、ユーザーが快適に対話できる範囲内を維持しようとします。</span><span class="sxs-lookup"><span data-stu-id="961da-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="961da-116">![HoloLens の pin パネルは、タグに沿って動作するしくみの好例](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="961da-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="961da-117">*HoloLens の [スタート] メニューは、タグに沿った動作の優れた例です。*</span><span class="sxs-lookup"><span data-stu-id="961da-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="961da-118">タグに沿ったオブジェクトには、動作を微調整できるパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="961da-118">Tag-along objects have parameters which can fine-tune the way they behave.</span></span> <span data-ttu-id="961da-119">コンテンツは、ユーザーの環境内を移動しながら、必要に応じてユーザーの視野を越えることができます。</span><span class="sxs-lookup"><span data-stu-id="961da-119">Content can be in or out of the user’s line of sight as desired while the user moves around their environment.</span></span> <span data-ttu-id="961da-120">ユーザーが移動すると、コンテンツは、ユーザーの移動速度によって、コンテンツが一時的に非表示になる可能性があることによって、ユーザーの周囲の内側に置かれます。</span><span class="sxs-lookup"><span data-stu-id="961da-120">As the user moves, the content will attempt to stay within the user’s periphery by sliding towards the edge of the view, depending on how quickly a user moves may leave the content temporarily out of view.</span></span> <span data-ttu-id="961da-121">ユーザーがタグに沿って gazes すると、より完全に表示されます。</span><span class="sxs-lookup"><span data-stu-id="961da-121">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="961da-122">コンテンツは常に "一目でわかる" と考えられるので、ユーザーがコンテンツの方向を忘れないようにします。</span><span class="sxs-lookup"><span data-stu-id="961da-122">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="961da-123">追加のパラメーターを使用すると、タグに沿ってオブジェクトをラバーバンドでユーザーの頭部に接続することができます。</span><span class="sxs-lookup"><span data-stu-id="961da-123">Additional parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="961da-124">ダンパーの加速または減速により、オブジェクトに対して重みが与えられ、物理的に存在するようになります。</span><span class="sxs-lookup"><span data-stu-id="961da-124">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="961da-125">この spring behavior は、ユーザーがタグを操作する方法の正確なメンタルモデルを作成するのに役立つ affordance です。</span><span class="sxs-lookup"><span data-stu-id="961da-125">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="961da-126">オーディオは、ユーザーがタグに沿ってオブジェクトを持っている場合に、追加の affordances を提供するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="961da-126">Audio helps provide additional affordances for when users have objects in tag-along mode.</span></span> <span data-ttu-id="961da-127">オーディオは移動速度を強調する必要があります。ファーストヘッドターンでは、自然な速度での再生では、効果がある場合は最小限のオーディオを使用します。</span><span class="sxs-lookup"><span data-stu-id="961da-127">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect while walking at a natural speed should have minimal audio if any effects at all.</span></span>

<span data-ttu-id="961da-128">実際にヘッドにロックされたコンテンツと同様に、タグに沿ってオブジェクトを使用すると、ユーザーのビューで非常に大きな動きがあるか、またはばねが非常に大きくなると、非常に多くのことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="961da-128">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="961da-129">ユーザーが見てすぐに停止すると、それらが停止したことがわかります。</span><span class="sxs-lookup"><span data-stu-id="961da-129">As a user looks around and then quickly stop, their senses tell them they have stopped.</span></span> <span data-ttu-id="961da-130">これらのバランスによって、ヘッドが旋回を停止したことが通知され、その構想によって世界が停止していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="961da-130">Their balance informs them that their head has stopped turning as well as their vision sees the world stop turning.</span></span> <span data-ttu-id="961da-131">ただし、ユーザーが停止したときにタグに沿って移動し続けると、その状態が混乱する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="961da-131">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="961da-132">Billboarding とタグ-Unity の MRTK (Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="961da-132">Billboarding and Tag-along in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="961da-133">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、Billboarding とタグに沿った動作のスクリプトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="961da-133">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and Tag-along behavior.</span></span> <span data-ttu-id="961da-134">Billboard.cs スクリプトを任意のオブジェクトに割り当てて、billboarding の動作を追加し、オブジェクトが常に顔になるようにします。</span><span class="sxs-lookup"><span data-stu-id="961da-134">Simply assign Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="961da-135">タグに沿った動作を追加するには、RadialView.cs スクリプトを使用します。</span><span class="sxs-lookup"><span data-stu-id="961da-135">To add tag-along behavior, use RadialView.cs script.</span></span> <span data-ttu-id="961da-136">Lerping time、distance、次数などのさまざまなオプションを調整できます。</span><span class="sxs-lookup"><span data-stu-id="961da-136">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="961da-137">MRTK-放射状ビューのソルバー</span><span class="sxs-lookup"><span data-stu-id="961da-137">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="961da-138">MRTK-ビルボードスクリプト</span><span class="sxs-lookup"><span data-stu-id="961da-138">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="961da-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="961da-139">See also</span></span>

* [<span data-ttu-id="961da-140">カーソル</span><span class="sxs-lookup"><span data-stu-id="961da-140">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="961da-141">ハンドレイ</span><span class="sxs-lookup"><span data-stu-id="961da-141">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="961da-142">ボタン</span><span class="sxs-lookup"><span data-stu-id="961da-142">Button</span></span>](button.md)
* [<span data-ttu-id="961da-143">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="961da-143">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="961da-144">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="961da-144">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="961da-145">操作性</span><span class="sxs-lookup"><span data-stu-id="961da-145">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="961da-146">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="961da-146">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="961da-147">Near メニュー</span><span class="sxs-lookup"><span data-stu-id="961da-147">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="961da-148">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="961da-148">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="961da-149">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="961da-149">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="961da-150">キーボード</span><span class="sxs-lookup"><span data-stu-id="961da-150">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="961da-151">ボタン</span><span class="sxs-lookup"><span data-stu-id="961da-151">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="961da-152">翻訳</span><span class="sxs-lookup"><span data-stu-id="961da-152">Slate</span></span>](slate.md)
* [<span data-ttu-id="961da-153">スライダー</span><span class="sxs-lookup"><span data-stu-id="961da-153">Slider</span></span>](slider.md)
* [<span data-ttu-id="961da-154">シェーダー</span><span class="sxs-lookup"><span data-stu-id="961da-154">Shader</span></span>](shader.md)
* [<span data-ttu-id="961da-155">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="961da-155">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="961da-156">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="961da-156">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="961da-157">表面の吸着</span><span class="sxs-lookup"><span data-stu-id="961da-157">Surface magnetism</span></span>](surface-magnetism.md)
