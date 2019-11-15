---
title: Button
description: ''
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Mixed Reality、コントロール、対話、ui、ux
ms.openlocfilehash: f0fa69239ec1b20938b679a4a04549f8f8ef900a
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2019
ms.locfileid: "74106081"
---
# <a name="button"></a><span data-ttu-id="d564e-103">Button</span><span class="sxs-lookup"><span data-stu-id="d564e-103">Button</span></span>

![Button](images/UX/UX_Hero_Button.jpg)

<span data-ttu-id="d564e-105">ボタンは、特定の操作を直ちに実行する方法をユーザーに与えます。</span><span class="sxs-lookup"><span data-stu-id="d564e-105">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="d564e-106">これは、mixed reality の最も基本的なコンポーネントの1つです。</span><span class="sxs-lookup"><span data-stu-id="d564e-106">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="d564e-107">HoloLens 2 では、ボタンには多くの視覚的な手掛かりと affordances があり、対話に対するユーザーの信頼度が高くなります。</span><span class="sxs-lookup"><span data-stu-id="d564e-107">In HoloLens 2, button has many visual cues and affordances to increase the user's confidence on interaction.</span></span> 


:::row:::
    :::column:::
       <span data-ttu-id="d564e-108">![移動](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="d564e-108">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="d564e-109">**近接光**</span><span class="sxs-lookup"><span data-stu-id="d564e-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d564e-110">![回転](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="d564e-110">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="d564e-111">**フォーカスの強調表示**</span><span class="sxs-lookup"><span data-stu-id="d564e-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="d564e-112">![移動](images/UX/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="d564e-112">![Move](images/UX/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="d564e-113">**ケージの圧縮**</span><span class="sxs-lookup"><span data-stu-id="d564e-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d564e-114">![回転](images/UX/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="d564e-114">![Rotate](images/UX/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="d564e-115">**トリガーのパルス**</span><span class="sxs-lookup"><span data-stu-id="d564e-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>


---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="d564e-116">Unity の MRTK (Mixed Reality Toolkit) のボタン</span><span class="sxs-lookup"><span data-stu-id="d564e-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="d564e-117">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、さまざまな種類のボタン prefabs が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d564e-117">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs.</span></span> <span data-ttu-id="d564e-118">HoloLens 2 および HoloLens 第1世代のシェルスタイルのボタンと、カスタマイズされた例を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="d564e-118">You can find shell-style buttons for HoloLens 2 and HoloLens 1st gen as well as customized examples.</span></span> <span data-ttu-id="d564e-119">HoloLens 2 ボタン prefab には、ユーザーの信頼度を向上させる詳細な affordances が多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="d564e-119">HoloLens 2 button prefab contains a lot of detailed affordances that improves user's confidence.</span></span> <span data-ttu-id="d564e-120">これには、近接度ベースの強調表示、フロントケージの圧縮、トリガーのパルス効果が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d564e-120">It includes proximity-based highlight, compressing front cage, and the pulse effect on trigger.</span></span>

* [<span data-ttu-id="d564e-121">MRTK-ボタン</span><span class="sxs-lookup"><span data-stu-id="d564e-121">MRTK - Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)



<br>

---


## <a name="see-also"></a><span data-ttu-id="d564e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="d564e-122">See also</span></span>

* [<span data-ttu-id="d564e-123">カーソル</span><span class="sxs-lookup"><span data-stu-id="d564e-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d564e-124">ハンドレイ</span><span class="sxs-lookup"><span data-stu-id="d564e-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="d564e-125">ボタン</span><span class="sxs-lookup"><span data-stu-id="d564e-125">Button</span></span>](button.md)
* [<span data-ttu-id="d564e-126">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="d564e-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d564e-127">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="d564e-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="d564e-128">操作性</span><span class="sxs-lookup"><span data-stu-id="d564e-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d564e-129">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="d564e-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="d564e-130">Near メニュー</span><span class="sxs-lookup"><span data-stu-id="d564e-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="d564e-131">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="d564e-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="d564e-132">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="d564e-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="d564e-133">キーボード</span><span class="sxs-lookup"><span data-stu-id="d564e-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="d564e-134">ボタン</span><span class="sxs-lookup"><span data-stu-id="d564e-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="d564e-135">翻訳</span><span class="sxs-lookup"><span data-stu-id="d564e-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="d564e-136">スライダー</span><span class="sxs-lookup"><span data-stu-id="d564e-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="d564e-137">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="d564e-137">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="d564e-138">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="d564e-138">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="d564e-139">表面の吸着</span><span class="sxs-lookup"><span data-stu-id="d564e-139">Surface magnetism</span></span>](surface-magnetism.md)
