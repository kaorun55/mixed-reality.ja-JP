---
title: Button
description: ''
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Mixed Reality、コントロール、対話、ui、ux
ms.openlocfilehash: c3fed3b7301c907a657796da7fc83bab146e2df1
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143160"
---
# <a name="button"></a><span data-ttu-id="58719-103">Button</span><span class="sxs-lookup"><span data-stu-id="58719-103">Button</span></span>

![Button](images/UX/UX_Hero_Button.jpg)

<span data-ttu-id="58719-105">ボタンは、特定の操作を直ちに実行する方法をユーザーに与えます。</span><span class="sxs-lookup"><span data-stu-id="58719-105">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="58719-106">これは、mixed reality の最も基本的なコンポーネントの1つです。</span><span class="sxs-lookup"><span data-stu-id="58719-106">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="58719-107">HoloLens 2 では、ボタンには多くの視覚的な手掛かりと affordances があり、対話に対するユーザーの信頼度が高くなります。</span><span class="sxs-lookup"><span data-stu-id="58719-107">In HoloLens 2, button has many visual cues and affordances to increase the user's confidence on interaction.</span></span> 


:::row:::
    :::column:::
       <span data-ttu-id="58719-108">![移動](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="58719-108">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="58719-109">**近接光**</span><span class="sxs-lookup"><span data-stu-id="58719-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="58719-110">![回転](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="58719-110">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="58719-111">**フォーカスの強調表示**</span><span class="sxs-lookup"><span data-stu-id="58719-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="58719-112">![移動](images/UX/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="58719-112">![Move](images/UX/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="58719-113">**ケージの圧縮**</span><span class="sxs-lookup"><span data-stu-id="58719-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="58719-114">![回転](images/UX/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="58719-114">![Rotate](images/UX/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="58719-115">**トリガーのパルス**</span><span class="sxs-lookup"><span data-stu-id="58719-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>


---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="58719-116">Unity の MRTK (Mixed Reality Toolkit) のボタン</span><span class="sxs-lookup"><span data-stu-id="58719-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="58719-117">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、さまざまな種類のボタン prefabs が用意されています。</span><span class="sxs-lookup"><span data-stu-id="58719-117">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs.</span></span> <span data-ttu-id="58719-118">HoloLens 2 および HoloLens 第1世代のシェルスタイルのボタンと、カスタマイズされた例を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="58719-118">You can find shell-style buttons for HoloLens 2 and HoloLens 1st gen as well as customized examples.</span></span> <span data-ttu-id="58719-119">HoloLens 2 ボタン prefab には、ユーザーの信頼度を向上させる詳細な affordances が多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="58719-119">HoloLens 2 button prefab contains a lot of detailed affordances that improves user's confidence.</span></span> <span data-ttu-id="58719-120">これには、近接度ベースの強調表示、フロントケージの圧縮、トリガーのパルス効果が含まれます。</span><span class="sxs-lookup"><span data-stu-id="58719-120">It includes proximity-based highlight, compressing front cage, and the pulse effect on trigger.</span></span>

* [<span data-ttu-id="58719-121">MRTK-ボタン</span><span class="sxs-lookup"><span data-stu-id="58719-121">MRTK - Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)



<br>

---


## <a name="see-also"></a><span data-ttu-id="58719-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="58719-122">See also</span></span>

* [<span data-ttu-id="58719-123">カーソル</span><span class="sxs-lookup"><span data-stu-id="58719-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="58719-124">ハンドレイ</span><span class="sxs-lookup"><span data-stu-id="58719-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="58719-125">ボタン</span><span class="sxs-lookup"><span data-stu-id="58719-125">Button</span></span>](button.md)
* [<span data-ttu-id="58719-126">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="58719-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="58719-127">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="58719-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="58719-128">操作性</span><span class="sxs-lookup"><span data-stu-id="58719-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="58719-129">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="58719-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="58719-130">Near メニュー</span><span class="sxs-lookup"><span data-stu-id="58719-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="58719-131">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="58719-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="58719-132">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="58719-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="58719-133">キーボード</span><span class="sxs-lookup"><span data-stu-id="58719-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="58719-134">ボタン</span><span class="sxs-lookup"><span data-stu-id="58719-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="58719-135">翻訳</span><span class="sxs-lookup"><span data-stu-id="58719-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="58719-136">スライダー</span><span class="sxs-lookup"><span data-stu-id="58719-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="58719-137">シェーダー</span><span class="sxs-lookup"><span data-stu-id="58719-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="58719-138">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="58719-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="58719-139">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="58719-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="58719-140">表面の吸着</span><span class="sxs-lookup"><span data-stu-id="58719-140">Surface magnetism</span></span>](surface-magnetism.md)
