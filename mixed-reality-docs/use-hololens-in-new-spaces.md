---
title: 新しいスペースでの HoloLens の使用
description: HoloLens は、時間の経過と共にどのようなスペースが見えるかを学習します。 ユーザーは、特定の方法で HoloLens をスペースを介して移動することで、このプロセスを容易にすることができます。
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Windows Mixed Reality、設計、空間マッピング、HoloLens、surface 再構築、メッシュ、ヘッド追跡、マッピング
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566021"
---
# <a name="use-hololens-in-new-spaces"></a><span data-ttu-id="687dd-105">新しいスペースでの HoloLens の使用</span><span class="sxs-lookup"><span data-stu-id="687dd-105">Use HoloLens in New Spaces</span></span>

<span data-ttu-id="687dd-106">HoloLensは、ユーザーがスペースを移動するときに、その環境に関する情報を学習します。</span><span class="sxs-lookup"><span data-stu-id="687dd-106">HoloLens *maps*, or learns information about, its environment as the user moves around a space.</span></span> <span data-ttu-id="687dd-107">時間の経過と共に、HoloLens は、監視されている環境のすべての部分の*空間マップ*を構築します。</span><span class="sxs-lookup"><span data-stu-id="687dd-107">Over time, the HoloLens builds up a *spatial map* of all parts of the environment that have been observed.</span></span> <span data-ttu-id="687dd-108">HoloLens は、環境内の変更が検出されたときにマップを更新します。</span><span class="sxs-lookup"><span data-stu-id="687dd-108">HoloLens updates the map as changes in the environment are observed.</span></span> <span data-ttu-id="687dd-109">このスキャンは、アプリの起動間に自動的に保持されます。</span><span class="sxs-lookup"><span data-stu-id="687dd-109">This scan will automatically persist between app launches.</span></span>

<span data-ttu-id="687dd-110">HoloLens は、デバイスがオンになっていて、ユーザーがログインしている限り、マップを作成および更新します。</span><span class="sxs-lookup"><span data-stu-id="687dd-110">HoloLens will create and update maps as long as the device is on and a user is logged in.</span></span> <span data-ttu-id="687dd-111">カメラがスペースで指されているデバイスを押さえたり、磨耗したりすると、デバイスはその領域をマップしようとします。</span><span class="sxs-lookup"><span data-stu-id="687dd-111">If you hold or wear the device with the cameras pointed at a space, the device will try to map the area.</span></span> <span data-ttu-id="687dd-112">HoloLens は、時間の経過と共に自然に領域を取得しますが、スペースをより迅速かつ効率的にマップするためのヒントとテクニックが用意されています。</span><span class="sxs-lookup"><span data-stu-id="687dd-112">While the HoloLens will learn a space naturally over time, there are tips and tricks available to map the space faster and more efficiently.</span></span> 

<span data-ttu-id="687dd-113">HoloLens がスペースをマップできない場合、または調整されていない場合は、制限モードになることがあります。</span><span class="sxs-lookup"><span data-stu-id="687dd-113">If your HoloLens can’t map your space or is out of calibration, you may enter Limited mode.</span></span> <span data-ttu-id="687dd-114">制限モードでは、ホログラムを周囲に配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="687dd-114">In Limited mode, you won’t be able to place holograms in your surroundings.</span></span>

## <a name="tips-and-tricks-for-mapping-spaces"></a><span data-ttu-id="687dd-115">スペースのマッピングに関するヒントとテクニック</span><span class="sxs-lookup"><span data-stu-id="687dd-115">Tips and tricks for mapping spaces</span></span>

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a><span data-ttu-id="687dd-116">混合現実のために領域が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="687dd-116">Make sure the space is set up for mixed reality</span></span>

<span data-ttu-id="687dd-117">環境内の機能によって、HoloLens がスペースを解釈するのが困難になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="687dd-117">Features in an environment can make it difficult for the HoloLens to interpret a space.</span></span> <span data-ttu-id="687dd-118">ライトレベル、空間内の素材、オブジェクトのレイアウトなどはすべて、HoloLens が領域をマップする方法に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="687dd-118">Light levels, materials in the space, the layout of objects, and more can all affect how HoloLens maps an area.</span></span>

<span data-ttu-id="687dd-119">HoloLens とその他の mixed reality デバイス用の領域を設定するためのヒントについては、「 [hololens の環境に関する考慮事項](environment-considerations-for-hololens.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="687dd-119">Tips for setting up your space for HoloLens and other mixed reality devices can be found in [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

### <a name="understand-the-scenarios-for-the-area"></a><span data-ttu-id="687dd-120">領域のシナリオを理解する</span><span class="sxs-lookup"><span data-stu-id="687dd-120">Understand the scenarios for the area</span></span>

<span data-ttu-id="687dd-121">HoloLens を使用する最も時間をかけて、マップが関連性と完全なものになるようにすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="687dd-121">It is important to spend the most time where you will be using the HoloLens so that the map is relevant and complete.</span></span> 

<span data-ttu-id="687dd-122">たとえば、HoloLens のユーザーシナリオで、ポイント A からポイント B への移行が必要な場合、そのパスを 2 ~ 3 回進めます。移動すると、すべての方向が表示されます。</span><span class="sxs-lookup"><span data-stu-id="687dd-122">For example, if a user scenario for HoloLens involves moving from Point A to Point B, walk that path two to three times, looking in all directions as you move.</span></span> 

### <a name="walk-slowly-around-the-space"></a><span data-ttu-id="687dd-123">領域をゆっくりと処理する</span><span class="sxs-lookup"><span data-stu-id="687dd-123">Walk slowly around the space</span></span>

<span data-ttu-id="687dd-124">この領域を簡単に説明すると、HoloLens がマッピング領域を見逃してしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="687dd-124">If you walk too quickly around the area, it's likely that the HoloLens will miss mapping areas.</span></span> <span data-ttu-id="687dd-125">領域をゆっくりとしていき、5-8 フィートごとに停止して、周囲の部分を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="687dd-125">Walk slowly around the space, stopping every 5-8 feet to look around at your surroundings.</span></span>

<span data-ttu-id="687dd-126">Smooth 移動は、HoloLens map より多くの effeciently にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="687dd-126">Smooth movements also help the HoloLens map more effeciently.</span></span>

### <a name="look-in-all-directions"></a><span data-ttu-id="687dd-127">すべての方向を検索</span><span class="sxs-lookup"><span data-stu-id="687dd-127">Look in all directions</span></span>

<span data-ttu-id="687dd-128">空間をマップする際には、1つの HoloLens が互いに相対的な場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="687dd-128">Looking around as you map the space gives the HoloLens more data on where points are relative to each other.</span></span> 

<span data-ttu-id="687dd-129">たとえば、検索しない場合、たとえば、1つの部屋の天井がどこにあるかを HoloLens が認識できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="687dd-129">If you don't look up, for example, the HoloLens may not know where the ceiling in a room is.</span></span> 

<span data-ttu-id="687dd-130">スペースをマップする際には、必ずフロアを見てください。</span><span class="sxs-lookup"><span data-stu-id="687dd-130">Don't forget to look down at the floor as you map the space.</span></span>

### <a name="cover-key-areas-multiple-times"></a><span data-ttu-id="687dd-131">主要領域を複数回カバーする</span><span class="sxs-lookup"><span data-stu-id="687dd-131">Cover key areas multiple times</span></span>

<span data-ttu-id="687dd-132">1つの区分を複数回移動すると、最初のチュートリアルでは見つからなかった機能を選択できます。</span><span class="sxs-lookup"><span data-stu-id="687dd-132">Moving through an area multiple times will help pick up features you may have missed on the first walkthrough.</span></span> <span data-ttu-id="687dd-133">理想的なマップを作成するために、2 ~ 3 回の領域を走査します。</span><span class="sxs-lookup"><span data-stu-id="687dd-133">Try traversing an area two to three times to build an ideal map.</span></span>

<span data-ttu-id="687dd-134">可能であれば、これらの移動を繰り返しながら、1つの方向の領域をたどる時間をかけて、前に戻ってみてください。</span><span class="sxs-lookup"><span data-stu-id="687dd-134">If possible, while repeating these movements, spend time walking through an area in one direction, then turn around and walk back the way you came.</span></span>

### <a name="take-your-time-mapping-the-area"></a><span data-ttu-id="687dd-135">時間を取って領域をマッピングする</span><span class="sxs-lookup"><span data-stu-id="687dd-135">Take your time mapping the area</span></span>

<span data-ttu-id="687dd-136">HoloLens が完全にマップされ、その周囲に調整されるまでに 15 ~ 20 分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="687dd-136">It can take between 15 and 20 minutes for the HoloLens to fully map and adjust itself to its surroundings.</span></span> <span data-ttu-id="687dd-137">HoloLens を頻繁に使用する予定がある場合は、この時間を使用して領域をマップすると、後で問題が発生しなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="687dd-137">If you have a space in which you plan to use a HoloLens frequently, taking that time up front to map the space can prevent issues later on.</span></span> 

## <a name="possible-errors-in-the-spatial-map"></a><span data-ttu-id="687dd-138">空間マップで発生する可能性のあるエラー</span><span class="sxs-lookup"><span data-stu-id="687dd-138">Possible errors in the spatial map</span></span>

<span data-ttu-id="687dd-139">空間マッピングデータのエラーは、次の3つのカテゴリのいずれかに分類されます。</span><span class="sxs-lookup"><span data-stu-id="687dd-139">Errors in spatial mapping data fall into one of three categories:</span></span>

* <span data-ttu-id="687dd-140">*穴*:空間マッピングデータに実際のサーフェイスがありません。</span><span class="sxs-lookup"><span data-stu-id="687dd-140">*Holes*: Real-world surfaces are missing from the spatial mapping data.</span></span>
* <span data-ttu-id="687dd-141">*Hallucinations*:サーフェイスは、実際の環境に存在しない空間マッピングデータに存在します。</span><span class="sxs-lookup"><span data-stu-id="687dd-141">*Hallucinations*: Surfaces exist in the spatial mapping data that do not exist in the real world.</span></span>
* <span data-ttu-id="687dd-142">*Wormholes*:HoloLens ' は、マップの別の部分にあるとしても、実際の値とは異なる部分にあると考えて、空間マップの一部を失います。</span><span class="sxs-lookup"><span data-stu-id="687dd-142">*Wormholes*: HoloLens 'loses' part of the spatial map by thinking it is in a different part of the map than it actually is.</span></span>
* <span data-ttu-id="687dd-143">*バイアス*:空間マッピングデータ内のサーフェイスは、実際のサーフェイスに固定されていて、プッシュまたはプルされます。</span><span class="sxs-lookup"><span data-stu-id="687dd-143">*Bias*: Surfaces in the spatial mapping data are imperfectly aligned with real-world surfaces, either pushed in or pulled out.</span></span>

<span data-ttu-id="687dd-144">これらのエラーの多くは、[ホログラムを削除](environment-considerations-for-hololens.md)してスペースを再マップすることによって軽減できます。</span><span class="sxs-lookup"><span data-stu-id="687dd-144">Many of these errors can be mitigated by [deleting your holograms](environment-considerations-for-hololens.md) and re-mapping the space.</span></span>