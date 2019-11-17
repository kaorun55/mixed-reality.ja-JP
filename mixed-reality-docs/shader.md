---
title: シェーダー
description: ''
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Mixed Reality、コントロール、対話、ui、ux
ms.openlocfilehash: 23371ae5d70e5e792415fd25c0d58def0a7cefbb
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143272"
---
# <a name="shader"></a><span data-ttu-id="544c9-103">シェーダー</span><span class="sxs-lookup"><span data-stu-id="544c9-103">Shader</span></span>

![シェーダー](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="544c9-105">Holographic オブジェクトは環境内の物理的なオブジェクトと混在するため、ビジュアルキューを用意することは、mixed reality では重要です。</span><span class="sxs-lookup"><span data-stu-id="544c9-105">Since holographic objects are mixed with the physical ones in the environment, providing visual cue is important in mixed reality.</span></span> <span data-ttu-id="544c9-106">MRTK Standard shader には、ホログラムで使用できるさまざまな種類の視覚効果が用意されています。</span><span class="sxs-lookup"><span data-stu-id="544c9-106">MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="544c9-107">MRTK 標準シェーディングシステムでは、Unity の標準シェーダーに似た視覚エフェクトを実現し、Fluent 設計システムの原則を実装し、mixed reality デバイスでパフォーマンスを維持できる、単一の柔軟なシェーダーを利用しています。</span><span class="sxs-lookup"><span data-stu-id="544c9-107">MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implement Fluent Design System principles, and remain performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="544c9-108">MRTK Standard shader を使用した視覚効果の例</span><span class="sxs-lookup"><span data-stu-id="544c9-108">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="544c9-109">![移動](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="544c9-109">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="544c9-110">**近接光**</span><span class="sxs-lookup"><span data-stu-id="544c9-110">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="544c9-111">![回転](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="544c9-111">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="544c9-112">**罫線 (細)**</span><span class="sxs-lookup"><span data-stu-id="544c9-112">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

---

## <a name="mrtk-standard-shader-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="544c9-113">MRTK の MRTK Standard shader (Mixed Reality Toolkit) (Unity 用)</span><span class="sxs-lookup"><span data-stu-id="544c9-113">MRTK Standard shader in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="544c9-114">MRTK-標準シェーダー</span><span class="sxs-lookup"><span data-stu-id="544c9-114">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="544c9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="544c9-115">See also</span></span>

* [<span data-ttu-id="544c9-116">カーソル</span><span class="sxs-lookup"><span data-stu-id="544c9-116">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="544c9-117">ハンドレイ</span><span class="sxs-lookup"><span data-stu-id="544c9-117">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="544c9-118">ボタン</span><span class="sxs-lookup"><span data-stu-id="544c9-118">Button</span></span>](button.md)
* [<span data-ttu-id="544c9-119">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="544c9-119">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="544c9-120">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="544c9-120">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="544c9-121">操作性</span><span class="sxs-lookup"><span data-stu-id="544c9-121">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="544c9-122">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="544c9-122">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="544c9-123">Near メニュー</span><span class="sxs-lookup"><span data-stu-id="544c9-123">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="544c9-124">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="544c9-124">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="544c9-125">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="544c9-125">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="544c9-126">キーボード</span><span class="sxs-lookup"><span data-stu-id="544c9-126">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="544c9-127">ボタン</span><span class="sxs-lookup"><span data-stu-id="544c9-127">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="544c9-128">翻訳</span><span class="sxs-lookup"><span data-stu-id="544c9-128">Slate</span></span>](slate.md)
* [<span data-ttu-id="544c9-129">スライダー</span><span class="sxs-lookup"><span data-stu-id="544c9-129">Slider</span></span>](slider.md)
* [<span data-ttu-id="544c9-130">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="544c9-130">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="544c9-131">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="544c9-131">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="544c9-132">表面の吸着</span><span class="sxs-lookup"><span data-stu-id="544c9-132">Surface magnetism</span></span>](surface-magnetism.md)
