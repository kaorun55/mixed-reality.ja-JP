---
title: 境界ボックスとアプリバー
description: アプリバーは、ホログラムの境界の下端に表示される一連のボタンを含むオブジェクトレベルのメニューです。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality、アプリバー、境界ボックス
ms.openlocfilehash: f09187bc2a3969a8f844711052e15433f5449d6d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437052"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="698d8-104">境界ボックスとアプリバー</span><span class="sxs-lookup"><span data-stu-id="698d8-104">Bounding box and App bar</span></span>
![境界は、混合現実のオブジェクト操作の標準インターフェイスです。](images/640px-boundingbox-hero.jpg)<br>

<br>

---

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="698d8-106">境界ボックスとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="698d8-106">What is the Bounding box?</span></span>

<span data-ttu-id="698d8-107">境界は、混合現実のオブジェクト操作の標準インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="698d8-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="698d8-108">これにより、オブジェクトが現在調整可能であることを示す affordance がユーザーに提供されます。</span><span class="sxs-lookup"><span data-stu-id="698d8-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="698d8-109">HoloLens 2 では、境界ボックスはダイレクト操作と連動し、ユーザーの finger's 近接に応答します。</span><span class="sxs-lookup"><span data-stu-id="698d8-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="698d8-110">これは、ユーザーがオブジェクトからの距離を認識するのに役立つ視覚的フィードバックを示しています。</span><span class="sxs-lookup"><span data-stu-id="698d8-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="698d8-111">オブジェクトのスケーリング</span><span class="sxs-lookup"><span data-stu-id="698d8-111">Scaling an object</span></span><br>
        <span data-ttu-id="698d8-112">境界ボックスのコーナーは、オブジェクトを拡張できることをユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="698d8-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="698d8-113">ハンドルは、スケールを調整するために広く理解されているパターンに従います。</span><span class="sxs-lookup"><span data-stu-id="698d8-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="698d8-114">このビジュアル affordance は、オブジェクトの合計領域をユーザーに表示します (調整モード以外では表示されません)。</span><span class="sxs-lookup"><span data-stu-id="698d8-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="698d8-115">これは特に重要です。存在しない場合は、別のオブジェクトまたはサーフェイスにスナップされたオブジェクトが、そこに存在しない領域があるかのように動作しているように見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="698d8-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="698d8-116">*ビデオループ: 境界ボックスを使用したオブジェクトのスケーリング*</span><span class="sxs-lookup"><span data-stu-id="698d8-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="698d8-117">![領域](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="698d8-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="698d8-118">境界ボックスを使用してオブジェクトをスケーリングする ![HoloLens ポイント](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="698d8-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="698d8-119">オブジェクトの回転</span><span class="sxs-lookup"><span data-stu-id="698d8-119">Rotating an object</span></span><br>
        <span data-ttu-id="698d8-120">境界ボックスの端の垂直四角形 affordances は回転インジケーターです。</span><span class="sxs-lookup"><span data-stu-id="698d8-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="698d8-121">これにより、ユーザーは、配置されたホログラムをより細かく調整できます。</span><span class="sxs-lookup"><span data-stu-id="698d8-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="698d8-122">調整と拡大縮小だけでなく、回転も可能になりました。</span><span class="sxs-lookup"><span data-stu-id="698d8-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="698d8-123">*ビデオループ: 境界ボックスを使用したオブジェクトの回転*</span><span class="sxs-lookup"><span data-stu-id="698d8-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="698d8-124">![領域](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="698d8-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="698d8-125">境界ボックスを使用してオブジェクトを回転する ![HoloLens ポイント](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="698d8-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="698d8-126">HoloLens 2 での視覚的フィードバック (手動による)</span><span class="sxs-lookup"><span data-stu-id="698d8-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="698d8-127">HoloLens 2 では、ユーザーが深さを認識できるようにするための視覚的な手掛かりが追加されています。</span><span class="sxs-lookup"><span data-stu-id="698d8-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="698d8-128">指先がオブジェクトに近づいたときに、指先の近くにあるリングが表示され、スケールダウンされます。</span><span class="sxs-lookup"><span data-stu-id="698d8-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="698d8-129">このリングは、押された状態に達したときに、最終的にドットに収束します。</span><span class="sxs-lookup"><span data-stu-id="698d8-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="698d8-130">このビジュアル affordance は、オブジェクトからの距離をユーザーが理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="698d8-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="698d8-131">*ビデオループ: 境界ボックスとの近接度に基づくビジュアルフィードバックの例*</span><span class="sxs-lookup"><span data-stu-id="698d8-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="698d8-132">![領域](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="698d8-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="698d8-133">](images/HoloLens2_Proximity.gif) における視覚的フィードバックの ![</span><span class="sxs-lookup"><span data-stu-id="698d8-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="698d8-134">**Unity アプリの開発については、 [Mixed Reality Toolkit の「境界ボックス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)」を参照してください。**</span><span class="sxs-lookup"><span data-stu-id="698d8-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="698d8-135">アプリバーとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="698d8-135">What is the App bar?</span></span>

<span data-ttu-id="698d8-136">アプリバーは、ホログラムの境界の下端に表示される一連のボタンを含むオブジェクトレベルのメニューです。</span><span class="sxs-lookup"><span data-stu-id="698d8-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="698d8-137">このパターンは、ユーザーがホログラムを削除して調整できるようにするためによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="698d8-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span> <span data-ttu-id="698d8-138">アプリバーは、主にユーザーの環境で配置されたオブジェクトを管理する方法として設計されました。</span><span class="sxs-lookup"><span data-stu-id="698d8-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="698d8-139">境界ボックスと組み合わせて使用すると、ユーザーはどこでも、どのようにオブジェクトが混合現実に向いているかを完全に制御できます。</span><span class="sxs-lookup"><span data-stu-id="698d8-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="698d8-140">アプリバーはユーザーに従います</span><span class="sxs-lookup"><span data-stu-id="698d8-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="698d8-141">このパターンは、世界でロックされているオブジェクトで使用されるため、ユーザーがオブジェクトの周りを移動すると、アプリバーは常にユーザーに最も近いオブジェクトの側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="698d8-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="698d8-142">これは billboarding ではありませんが、実質的に同じ結果を実現します。環境内の別の場所から使用できるようにするために、ユーザーの位置を occlude またはブロックすることを防止します。</span><span class="sxs-lookup"><span data-stu-id="698d8-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="698d8-143">*ビデオループ: ホログラムの周りをたどると、アプリバーが次のようになります。*</span><span class="sxs-lookup"><span data-stu-id="698d8-143">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="698d8-144">![領域](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="698d8-144">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="698d8-145">ホログラムの周りを ![。</span><span class="sxs-lookup"><span data-stu-id="698d8-145">![Walking around a hologram.</span></span> <span data-ttu-id="698d8-146">アプリバーは次のようになります。](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="698d8-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>



<span data-ttu-id="698d8-147">**Unity アプリの開発については、「 [Mixed Reality Toolkit-Unity のアプリバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) 」を参照してください。**</span><span class="sxs-lookup"><span data-stu-id="698d8-147">**For Unity app development, see [App bar in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)**</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="698d8-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="698d8-148">See also</span></span>
* [<span data-ttu-id="698d8-149">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="698d8-149">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="698d8-150">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="698d8-150">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="698d8-151">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="698d8-151">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="698d8-152">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="698d8-152">Displaying progress</span></span>](progress.md)
