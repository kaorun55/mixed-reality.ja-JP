---
title: 境界ボックスとアプリバー
description: アプリバーは、ホログラムの境界の下端に表示される一連のボタンを含むオブジェクトレベルのメニューです。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality、アプリバー、境界ボックス
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829678"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="54de6-104">境界ボックスとアプリバー</span><span class="sxs-lookup"><span data-stu-id="54de6-104">Bounding box and App bar</span></span>
![境界は、混合現実のオブジェクト操作の標準インターフェイスです。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="54de6-106">境界ボックスとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="54de6-106">What is the Bounding box?</span></span>

<span data-ttu-id="54de6-107">境界は、混合現実のオブジェクト操作の標準インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="54de6-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="54de6-108">これにより、オブジェクトが現在調整可能であることを示す affordance がユーザーに提供されます。</span><span class="sxs-lookup"><span data-stu-id="54de6-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="54de6-109">コーナーは、オブジェクトのスケールも可能であることをユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="54de6-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="54de6-110">このビジュアル affordance は、オブジェクトの合計領域をユーザーに表示します (調整モード以外では表示されません)。</span><span class="sxs-lookup"><span data-stu-id="54de6-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="54de6-111">これは特に重要です。存在しない場合は、別のオブジェクトまたはサーフェイスにスナップされたオブジェクトが、そこに存在しない領域があるかのように動作しているように見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="54de6-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="54de6-112">HoloLens 2 では、境界ボックスはダイレクト操作と連動し、ユーザーの finger's 近接に応答します。</span><span class="sxs-lookup"><span data-stu-id="54de6-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="54de6-113">これは、ユーザーがオブジェクトからの距離を認識するのに役立つ視覚的フィードバックを示しています。</span><span class="sxs-lookup"><span data-stu-id="54de6-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="54de6-114">![境界ボックスを使用したオブジェクトのスケーリングの HoloLens ポイント](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="54de6-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="54de6-115">*境界ボックスを使用したオブジェクトのスケーリング*</span><span class="sxs-lookup"><span data-stu-id="54de6-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="54de6-116">境界ボックスの隅にあるハンドルは、スケールを調整するために広く理解されているパターンに従います。</span><span class="sxs-lookup"><span data-stu-id="54de6-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="54de6-117">![境界ボックスを使用してオブジェクトを回転するための HoloLens のポイント](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="54de6-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="54de6-118">*境界ボックスを使用したオブジェクトの回転*</span><span class="sxs-lookup"><span data-stu-id="54de6-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="54de6-119">![手書きの視覚的フィードバック](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="54de6-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="54de6-120">*近接度に基づくビジュアルフィードバック*</span><span class="sxs-lookup"><span data-stu-id="54de6-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="54de6-121">境界ボックスの端の垂直四角形 affordances は回転インジケーターです。</span><span class="sxs-lookup"><span data-stu-id="54de6-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="54de6-122">これにより、ユーザーは、配置されたホログラムをより細かく調整できます。</span><span class="sxs-lookup"><span data-stu-id="54de6-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="54de6-123">調整と拡大縮小だけでなく、回転も可能になりました。</span><span class="sxs-lookup"><span data-stu-id="54de6-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="54de6-124">Unity アプリの開発については、「 [Mixed Reality Toolkit の境界ボックス-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54de6-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="54de6-125">アプリバーとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="54de6-125">What is the App bar?</span></span>

<span data-ttu-id="54de6-126">アプリバーは、ホログラムの境界の下端に表示される一連のボタンを含むオブジェクトレベルのメニューです。</span><span class="sxs-lookup"><span data-stu-id="54de6-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="54de6-127">このパターンは、ユーザーがホログラムを削除して調整できるようにするためによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="54de6-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="54de6-128">このパターンは、世界でロックされているオブジェクトで使用されるため、ユーザーがオブジェクトの周りを移動すると、アプリバーは常にユーザーに最も近いオブジェクトの側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="54de6-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="54de6-129">これは billboarding ではありませんが、実質的に同じ結果を実現します。環境内の別の場所から使用できるようにするために、ユーザーの位置を occlude またはブロックすることを防止します。</span><span class="sxs-lookup"><span data-stu-id="54de6-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="54de6-130">![ホログラムの周りを歩いています。</span><span class="sxs-lookup"><span data-stu-id="54de6-130">![Walking around a hologram.</span></span> <span data-ttu-id="54de6-131">アプリバーは次のようになります。](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="54de6-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="54de6-132">*ホログラムの周りをたどると、アプリバーは次のようになります。*</span><span class="sxs-lookup"><span data-stu-id="54de6-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="54de6-133">アプリバーは、主にユーザーの環境で配置されたオブジェクトを管理する方法として設計されました。</span><span class="sxs-lookup"><span data-stu-id="54de6-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="54de6-134">境界ボックスと組み合わせて使用すると、ユーザーはどこでも、どのようにオブジェクトが混合現実に向いているかを完全に制御できます。</span><span class="sxs-lookup"><span data-stu-id="54de6-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="54de6-135">Unity アプリの開発については、「 [Mixed Reality Toolkit のアプリバー-unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54de6-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="54de6-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="54de6-136">See also</span></span>
* [<span data-ttu-id="54de6-137">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="54de6-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="54de6-138">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="54de6-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="54de6-139">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="54de6-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="54de6-140">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="54de6-140">Displaying progress</span></span>](progress.md)
