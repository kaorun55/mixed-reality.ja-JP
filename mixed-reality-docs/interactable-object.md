---
title: 対話型のオブジェクト
description: ボタンには、2 D 抽象世界でイベントをトリガーに使用されるメタファが長年です。 3 次元の複合現実の世界では、この抽象化はもはやの世界に限定しました必要はありません。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality、コントロール、相互作用、ui、ux
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601181"
---
# <a name="interactable-object"></a><span data-ttu-id="d6e7a-105">対話型のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="d6e7a-105">Interactable object</span></span>

<span data-ttu-id="d6e7a-106">ボタンには、2 D 抽象世界でイベントをトリガーに使用されるメタファが長年です。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="d6e7a-107">3 次元の複合現実の世界では、この抽象化はもはやの世界に限定しました必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="d6e7a-108">何もすることができます、**対話型のオブジェクト**イベントをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-108">Anything can be an **Interactable object** that triggers an event.</span></span> <span data-ttu-id="d6e7a-109">対話型のオブジェクトは、そのテーブルに、コーヒー カップから空中に浮かんでバルーンをものとして表現できます。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="d6e7a-110">引き続き行うことで特定の状況はダイアログの UI などの従来のボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="d6e7a-111">ボタンの視覚的表現は、コンテキストによって異なります。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-111">The visual representation of the button depends on the context.</span></span>

![Interactible オブジェクト ヒーローのイメージ](images/640px-interactibleobject-hero-640px.jpg)


<span data-ttu-id="d6e7a-113"> **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 一連の Unity のスクリプトを作成したとする際に役立つプレハブは、対話型のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-113">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, we have created a series of Unity scripts and prefabs that will help you create Interactable objects.</span></span> <span data-ttu-id="d6e7a-114">これらを使用して、これらの標準的な対話状態を使用すると、対話できるユーザー オブジェクトの任意の型を作成することができます: 監視、対象となる状態および押されています。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-114">You can use these to create any type of object that the user can interact with, using these standard interaction states: observation, targeted and pressed.</span></span> <span data-ttu-id="d6e7a-115">独自の資産とビジュアル デザインを簡単にカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-115">You can easily customize the visual design with your own assets.</span></span> <span data-ttu-id="d6e7a-116">詳細なアニメーションを作成して、Unity のアニメーション コント ローラーでの操作状態の対応するアニメーション クリップの割り当てまたはオフセットとスケールを使用していずれかによってカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-116">Detailed animations can be customized by either creating and assigning corresponding animation clips for the interaction states in the Unity's animation controller or using offset and scale.</span></span> 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a><span data-ttu-id="d6e7a-117">さまざまな入力の対話操作の状態の視覚的なフィードバック</span><span class="sxs-lookup"><span data-stu-id="d6e7a-117">Visual feedback for the different input interaction states</span></span>

<span data-ttu-id="d6e7a-118">複合現実で holographic オブジェクトは、実際の環境とが混在しているため困難になることな対話型のオブジェクトを理解します。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-118">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="d6e7a-119">お客様のエクスペリエンスで対話型のオブジェクトの状態を各入力に差別化された視覚的なフィードバックを提供する重要なは。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-119">For any interactable objects in your experience, it is important to provide differentiated visual feedback for each input state.</span></span> <span data-ttu-id="d6e7a-120">これにより、ユーザーのエクスペリエンスの部分が対話型と一貫性のある相互作用方式で確実に、ユーザーは、理解できます。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-120">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

<span data-ttu-id="d6e7a-121">任意のオブジェクトにそのユーザーが操作できるをお勧めするこれら 3 つの入力の状態のさまざまな視覚的なフィードバックがあります。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-121">For any objects that user can interact with, we recommended to have different visual feedback for these three input states:</span></span>
* <span data-ttu-id="d6e7a-122">**監視**:オブジェクトの既定のアイドル状態です。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-122">**Observation**: Default idle state of the object.</span></span>
* <span data-ttu-id="d6e7a-123">**対象となる**:オブジェクトは視線の先のカーソルにターゲットになると、本の指近接やアニメーション コント ローラーのポインター。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-123">**Targeted**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="d6e7a-124">**押された**:オブジェクトをエア タップ ジェスチャや指キーを押してモーション コント ローラーの [選択] ボタンを押したときにします。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="d6e7a-125">![Holographic ボタン](images/640px-interactibleobject-holographicbutton-650px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d6e7a-125">![Holographic button](images/640px-interactibleobject-holographicbutton-650px.jpg)</span></span><br>
<span data-ttu-id="d6e7a-126">*状態、状態、対象となるおよびれた押された状態の監視*</span><span class="sxs-lookup"><span data-stu-id="d6e7a-126">*Observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="d6e7a-127">Windows Mixed Reality では、[スタート] メニューおよびアプリ バー ボタンのさまざまな入力の状態を視覚化の例が見つかります。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-127">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> <span data-ttu-id="d6e7a-128">強調表示機能やスケーリングなどの手法を使用すると、ユーザーの入力の状態を視覚的なフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-128">You can use techniques such as highlighting or scaling to provide visual feedback to the user’s input states.</span></span>

<span data-ttu-id="d6e7a-129">HoloLens 2 で絶対手の形が、入力の追跡をサポートしているので提供できます、手の近接度に基づいて追加アフォー。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-129">In HoloLens 2, since it supports fully articulated hand tracking input, we can provide additional affordances based on the proximity to the hands.</span></span> <span data-ttu-id="d6e7a-130">[HoloLens 2 ボタン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)この例を示します。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-130">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows this example.</span></span>

![Pressable ボタン](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a><span data-ttu-id="d6e7a-132">対話型のオブジェクトのサンプル</span><span class="sxs-lookup"><span data-stu-id="d6e7a-132">Interactable object samples</span></span>

### <a name="mesh-button"></a><span data-ttu-id="d6e7a-133">メッシュのボタン</span><span class="sxs-lookup"><span data-stu-id="d6e7a-133">Mesh button</span></span>

![メッシュのボタン](images/640px-interactibleobject-meshbutton.jpg)

<span data-ttu-id="d6e7a-135">これらは、対話型のオブジェクトとしてプリミティブとインポートされた 3 D メッシュの使用例です。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-135">These are examples using primitives and imported 3D meshes as Interactable objects.</span></span> <span data-ttu-id="d6e7a-136">各入力の対話操作の状態に応答するさまざまな規模、オフセット、および色の値を簡単に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-136">You can easily assign different scale, offset and color values to respond to each input interaction state.</span></span>

### <a name="toolbar"></a><span data-ttu-id="d6e7a-137">ツール バー</span><span class="sxs-lookup"><span data-stu-id="d6e7a-137">Toolbar</span></span>

![ツール バー](images/640px-interactibleobject-toolbar.jpg)

<span data-ttu-id="d6e7a-139">ツールバーは、複合現実エクスペリエンスで広く使用されているパターンです。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-139">A toolbar is a widely used pattern in mixed reality experiences.</span></span> <span data-ttu-id="d6e7a-140">追加の動作とボタンの単純なコレクションなどが[Billboarding と tag-along](billboarding-and-tag-along.md)します。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-140">It is a simple collection of buttons with additional behaviors such as [Billboarding and tag-along](billboarding-and-tag-along.md).</span></span> <span data-ttu-id="d6e7a-141">この例、MixedRealityToolkit から Billboarding と tag-along スクリプトを使用します。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-141">This example uses a Billboarding and tag-along script from the MixedRealityToolkit.</span></span> <span data-ttu-id="d6e7a-142">速度としきい値の値の移動距離を含む詳細な動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-142">You can control detailed behaviors including distance, moving speed and threshold values.</span></span>

### <a name="traditional-button"></a><span data-ttu-id="d6e7a-143">従来のボタン</span><span class="sxs-lookup"><span data-stu-id="d6e7a-143">Traditional button</span></span>

![従来のボタン](images/640px-interactibleobject-traditionalbutton.jpg)

<span data-ttu-id="d6e7a-145">この例では、従来の 2D スタイル ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-145">This example shows a traditional 2D style button.</span></span> <span data-ttu-id="d6e7a-146">各入力の状態には、若干異なる深さとアニメーションのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-146">Each input state has a slightly different depth and animation property.</span></span>

### <a name="other-examples"></a><span data-ttu-id="d6e7a-147">その他の例</span><span class="sxs-lookup"><span data-stu-id="d6e7a-147">Other examples</span></span>

<span data-ttu-id="d6e7a-148">![プッシュ ボタン](images/640px-interactibleobject-pushbutton.jpg)</span><span class="sxs-lookup"><span data-stu-id="d6e7a-148">![Push button](images/640px-interactibleobject-pushbutton.jpg)</span></span><br>
<span data-ttu-id="d6e7a-149">*プッシュ ボタン*</span><span class="sxs-lookup"><span data-stu-id="d6e7a-149">*Push button*</span></span>
<br>
<span data-ttu-id="d6e7a-150">![実際の有効期間オブジェクト](images/640px-interactibleobject-reallifeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="d6e7a-150">![Real Life object](images/640px-interactibleobject-reallifeobject.jpg)</span></span><br>
<span data-ttu-id="d6e7a-151">*実際のオブジェクト*</span><span class="sxs-lookup"><span data-stu-id="d6e7a-151">*Real life object*</span></span>

<span data-ttu-id="d6e7a-152">HoloLens では、物理領域を利用できます。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-152">With HoloLens, you can leverage physical space.</span></span> <span data-ttu-id="d6e7a-153">物理的な壁に holographic プッシュ ボタンを想像してください。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-153">Imagine a holographic push button on a physical wall.</span></span> <span data-ttu-id="d6e7a-154">または、実際のテーブルでは、コーヒー カップについてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-154">Or how about a coffee cup on a real table?</span></span> <span data-ttu-id="d6e7a-155">ソフトウェアのモデリングからインポートした 3D モデルを使用して、実際のオブジェクトのような対話型のオブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-155">Using 3D models imported from modeling software, we can create an Interactable object that resembles real life object.</span></span> <span data-ttu-id="d6e7a-156">デジタル オブジェクトであるために魔法のような相互作用を追加できます。</span><span class="sxs-lookup"><span data-stu-id="d6e7a-156">Since it's a digital object, we can add magical interactions to it.</span></span>

## <a name="interactable-object-in-mixed-reality-toolkit"></a><span data-ttu-id="d6e7a-157">Mixed Reality Toolkit で対話型のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="d6e7a-157">Interactable object in Mixed Reality Toolkit</span></span>
<span data-ttu-id="d6e7a-158">検索することができます、 [Interactable の例については、Mixed Reality toolkit オブジェクト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span><span class="sxs-lookup"><span data-stu-id="d6e7a-158">You can find the [examples of Interactable object in Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span></span>


## <a name="see-also"></a><span data-ttu-id="d6e7a-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6e7a-159">See also</span></span>
* [<span data-ttu-id="d6e7a-160">Mixed Reality ツールキット - unity pressable ボタン</span><span class="sxs-lookup"><span data-stu-id="d6e7a-160">Pressable Button on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="d6e7a-161">オブジェクトのコレクション</span><span class="sxs-lookup"><span data-stu-id="d6e7a-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="d6e7a-162">ビルボード処理と tag-along</span><span class="sxs-lookup"><span data-stu-id="d6e7a-162">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
