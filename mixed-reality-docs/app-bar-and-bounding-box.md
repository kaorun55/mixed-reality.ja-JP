---
title: アプリ バー、境界ボックス
description: アプリ バーは、一連のホログラムの範囲の下端に表示されるボタンを含むオブジェクト レベルのメニューです。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality アプリ バー、境界ボックス
ms.openlocfilehash: ab472e1c988e6bdfb0a69d90e90280082b3db759
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813859"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="911e6-104">境界ボックスと、アプリ バー</span><span class="sxs-lookup"><span data-stu-id="911e6-104">Bounding box and App bar</span></span>
![境界は、複合現実でのオブジェクトの操作の標準的なインターフェイスです。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="911e6-106">境界ボックスとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="911e6-106">What is the Bounding box?</span></span>

<span data-ttu-id="911e6-107">境界は、複合現実でのオブジェクトの操作の標準的なインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="911e6-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="911e6-108">オブジェクトが現在調整可能である、アフォー ダンス、ユーザーを提供します。</span><span class="sxs-lookup"><span data-stu-id="911e6-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="911e6-109">角に丸みオブジェクトが拡張できるもユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="911e6-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="911e6-110">この visual アフォー ダンスでは、調整モードの外部で表示されていない場合でも、ユーザーが – オブジェクトの合計領域に表示します。</span><span class="sxs-lookup"><span data-stu-id="911e6-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="911e6-111">これは、機能は、別のオブジェクトまたは画面を基準としてスナップされます。 オブジェクトが動作であることを周囲のスペースがあったかのように見えるがなかった場合ため特に重要です。</span><span class="sxs-lookup"><span data-stu-id="911e6-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="911e6-112">HoloLens 2 は、境界ボックスは、直接手操作と連携し、ユーザーの指の近くに応答します。</span><span class="sxs-lookup"><span data-stu-id="911e6-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="911e6-113">オブジェクトからの距離を認識するユーザーを支援する視覚的なフィードバックが表示されます。</span><span class="sxs-lookup"><span data-stu-id="911e6-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="911e6-114">![HoloLens ビューがポイントの境界ボックスを使用してオブジェクトのスケーリング](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="911e6-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="911e6-115">*境界ボックスを使用してオブジェクトのスケーリング*</span><span class="sxs-lookup"><span data-stu-id="911e6-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="911e6-116">境界ボックスの角のハンドルでは、スケールを調整するために広く理解されているパターンに従います。</span><span class="sxs-lookup"><span data-stu-id="911e6-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="911e6-117">![HoloLens ビューがポイントの境界ボックスを使用してオブジェクトを回転します。](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="911e6-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="911e6-118">*境界ボックスを使用して、オブジェクトの回転*</span><span class="sxs-lookup"><span data-stu-id="911e6-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="911e6-119">![近接の手の形で視覚的なフィードバック](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="911e6-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="911e6-120">*近接度に基づいて視覚的なフィードバック*</span><span class="sxs-lookup"><span data-stu-id="911e6-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="911e6-121">境界ボックスの端に垂直方向の長方形アフォーとは、回転のインジケーターです。</span><span class="sxs-lookup"><span data-stu-id="911e6-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="911e6-122">これにより、ユーザーは、配置されたホログラム経由で細かい調整をできるようにします。</span><span class="sxs-lookup"><span data-stu-id="911e6-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="911e6-123">だけでなく、調整およびできます、スケールしますが、も回転させるようになりました。</span><span class="sxs-lookup"><span data-stu-id="911e6-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="911e6-124">Unity アプリ開発では、次を参照してください[Mixed Reality Toolkit Unity での境界ボックス。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="911e6-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="911e6-125">アプリ バーとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="911e6-125">What is the App bar?</span></span>

<span data-ttu-id="911e6-126">アプリ バーは、一連のホログラムの範囲の下端に表示されるボタンを含むオブジェクト レベルのメニューです。</span><span class="sxs-lookup"><span data-stu-id="911e6-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="911e6-127">このパターンは、通常ユーザーを削除し、ホログラムを調整できるように使用されます。</span><span class="sxs-lookup"><span data-stu-id="911e6-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="911e6-128">このパターンはユーザーがオブジェクトの周囲に移動すると、ロックされている世界であるオブジェクトで使用されるため、アプリ バーは、ユーザーに最も近いオブジェクトの側で常に表示されます。</span><span class="sxs-lookup"><span data-stu-id="911e6-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="911e6-129">結果は同じ効果的にこのいないビルボード処理中に実現します。ユーザーの位置がや各自の環境内の別の場所から使用されないようにブロックの機能を防止します。</span><span class="sxs-lookup"><span data-stu-id="911e6-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="911e6-130">![ホログラムを歩きします。</span><span class="sxs-lookup"><span data-stu-id="911e6-130">![Walking around a hologram.</span></span> <span data-ttu-id="911e6-131">アプリ バーに従います。](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="911e6-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="911e6-132">*ホログラムを歩きながら、アプリ バーに依存します。*</span><span class="sxs-lookup"><span data-stu-id="911e6-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="911e6-133">アプリ バーは、主にユーザーの環境で配置されたオブジェクトを管理する手段として設計されています。</span><span class="sxs-lookup"><span data-stu-id="911e6-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="911e6-134">境界ボックスと組み合わせて、ユーザーは、複合現実でのオブジェクトを指向場所と方法を完全に制御を持ちます。</span><span class="sxs-lookup"><span data-stu-id="911e6-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="911e6-135">Unity アプリ開発では、次を参照してください[Mixed Reality Toolkit Unity でのアプリ バー。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="911e6-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="911e6-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="911e6-136">See also</span></span>
* [<span data-ttu-id="911e6-137">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="911e6-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="911e6-138">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="911e6-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="911e6-139">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="911e6-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="911e6-140">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="911e6-140">Displaying progress</span></span>](progress.md)
