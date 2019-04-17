---
title: アプリ バー、境界ボックス
description: アプリ バーは、一連のホログラムの範囲の下端に表示されるボタンを含むオブジェクト レベルのメニューです。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality アプリ バー、境界ボックス
ms.openlocfilehash: bdce92e00193230d1f7a487f11ef0487f1d6657c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602081"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="84a37-104">境界ボックスと、アプリ バー</span><span class="sxs-lookup"><span data-stu-id="84a37-104">Bounding box and App bar</span></span>
![境界は、複合現実でのオブジェクトの操作の標準的なインターフェイスです。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="84a37-106">境界ボックスとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="84a37-106">What is the Bounding box?</span></span>

<span data-ttu-id="84a37-107">境界は、複合現実でのオブジェクトの操作の標準的なインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="84a37-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="84a37-108">オブジェクトが現在調整可能である、アフォー ダンス、ユーザーを提供します。</span><span class="sxs-lookup"><span data-stu-id="84a37-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="84a37-109">角に丸みオブジェクトが拡張できるもユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="84a37-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="84a37-110">この visual アフォー ダンスでは、調整モードの外部で表示されていない場合でも、ユーザーが – オブジェクトの合計領域に表示します。</span><span class="sxs-lookup"><span data-stu-id="84a37-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="84a37-111">これは、機能は、別のオブジェクトまたは画面を基準としてスナップされます。 オブジェクトが動作であることを周囲のスペースがあったかのように見えるがなかった場合ため特に重要です。</span><span class="sxs-lookup"><span data-stu-id="84a37-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="84a37-112">HoloLens 2 では、境界ボックスは、ユーザーの指の近くに応答します。</span><span class="sxs-lookup"><span data-stu-id="84a37-112">On HoloLens 2, the bounding box responds to the user's finger's proximity.</span></span> <span data-ttu-id="84a37-113">オブジェクトからの距離を認識する視覚的なフィードバックが表示されます。</span><span class="sxs-lookup"><span data-stu-id="84a37-113">It shows visual feedback to help perceive the distance from the object.</span></span> 

<span data-ttu-id="84a37-114">![HoloLens ビューがポイントの境界ボックスを使用してオブジェクトのスケーリング](images/bounding-box-scale.gif)</span><span class="sxs-lookup"><span data-stu-id="84a37-114">![HoloLens point-of-view of scaling an object via bounding box](images/bounding-box-scale.gif)</span></span><br>
<span data-ttu-id="84a37-115">*境界ボックスを使用してオブジェクトのスケーリング*</span><span class="sxs-lookup"><span data-stu-id="84a37-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="84a37-116">境界ボックスのキューブのような角では、スケールを調整するために広く理解されているパターンに従います。</span><span class="sxs-lookup"><span data-stu-id="84a37-116">The cube-like corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="84a37-117">結合「調整モード」にオブジェクトを配置の明示的なアクションでできます両方オブジェクトの移動しますが、それぞれの環境でスケールも明らかです。</span><span class="sxs-lookup"><span data-stu-id="84a37-117">Coupled with the explicit action of putting an object into “adjust mode” it’s clear they can both move the object, but also scale it in their environment.</span></span>

<span data-ttu-id="84a37-118">![HoloLens ビューがポイントの境界ボックスを使用してオブジェクトを回転します。](images/bounding-box-rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="84a37-118">![HoloLens point-of-view of rotating an object via bounding box](images/bounding-box-rotate.gif)</span></span><br>
<span data-ttu-id="84a37-119">*境界ボックスを使用して、オブジェクトの回転*</span><span class="sxs-lookup"><span data-stu-id="84a37-119">*Rotating an object via bounding box*</span></span>

<span data-ttu-id="84a37-120">境界ボックスの端に球アフォーとは、回転のインジケーターです。</span><span class="sxs-lookup"><span data-stu-id="84a37-120">The spherical affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="84a37-121">これにより、ユーザーは、配置されたホログラム経由で細かい調整をできるようにします。</span><span class="sxs-lookup"><span data-stu-id="84a37-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="84a37-122">だけでなく、調整およびできます、スケールしますが、も回転させるようになりました。</span><span class="sxs-lookup"><span data-stu-id="84a37-122">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="84a37-123">Unity アプリ開発では、次を参照してください[Mixed Reality Toolkit Unity での境界ボックス。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="84a37-123">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>

## <a name="what-is-the-app-bar"></a><span data-ttu-id="84a37-124">アプリ バーとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="84a37-124">What is the App bar?</span></span>

<span data-ttu-id="84a37-125">アプリ バーは、一連のホログラムの範囲の下端に表示されるボタンを含むオブジェクト レベルのメニューです。</span><span class="sxs-lookup"><span data-stu-id="84a37-125">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="84a37-126">このパターンは、通常ユーザーを削除し、ホログラムを調整できるように使用されます。</span><span class="sxs-lookup"><span data-stu-id="84a37-126">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="84a37-127">このパターンはユーザーがオブジェクトの周囲に移動すると、ロックされている世界であるオブジェクトで使用されるため、アプリ バーは、ユーザーに最も近いオブジェクトの側で常に表示されます。</span><span class="sxs-lookup"><span data-stu-id="84a37-127">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="84a37-128">結果は同じ効果的にこのいないビルボード処理中に実現します。ユーザーの位置がや各自の環境内の別の場所から使用されないようにブロックの機能を防止します。</span><span class="sxs-lookup"><span data-stu-id="84a37-128">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="84a37-129">![ホログラムを歩きします。</span><span class="sxs-lookup"><span data-stu-id="84a37-129">![Walking around a hologram.</span></span> <span data-ttu-id="84a37-130">アプリ バーに従います。](images/holobar-followuser.gif)</span><span class="sxs-lookup"><span data-stu-id="84a37-130">The App bar follows.](images/holobar-followuser.gif)</span></span><br>
<span data-ttu-id="84a37-131">*ホログラムを歩きながら、アプリ バーに依存します。*</span><span class="sxs-lookup"><span data-stu-id="84a37-131">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="84a37-132">アプリ バーは、主にユーザーの環境で配置されたオブジェクトを管理する手段として設計されています。</span><span class="sxs-lookup"><span data-stu-id="84a37-132">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="84a37-133">境界ボックスと組み合わせて、ユーザーは、複合現実でのオブジェクトを指向場所と方法を完全に制御を持ちます。</span><span class="sxs-lookup"><span data-stu-id="84a37-133">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="84a37-134">Unity アプリ開発では、次を参照してください[Mixed Reality Toolkit Unity でのアプリ バー。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="84a37-134">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="84a37-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="84a37-135">See also</span></span>
* [<span data-ttu-id="84a37-136">境界ボックス Mixed Reality Toolkit Unity で</span><span class="sxs-lookup"><span data-stu-id="84a37-136">Bounding box on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)
* [<span data-ttu-id="84a37-137">アプリ バー Mixed Reality Toolkit Unity で</span><span class="sxs-lookup"><span data-stu-id="84a37-137">App bar on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)
* [<span data-ttu-id="84a37-138">対話型のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="84a37-138">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="84a37-139">Unity 内のテキスト</span><span class="sxs-lookup"><span data-stu-id="84a37-139">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="84a37-140">オブジェクトのコレクション</span><span class="sxs-lookup"><span data-stu-id="84a37-140">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="84a37-141">進行状況の表示</span><span class="sxs-lookup"><span data-stu-id="84a37-141">Displaying progress</span></span>](progress.md)
