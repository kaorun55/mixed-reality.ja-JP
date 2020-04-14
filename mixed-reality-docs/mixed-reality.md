---
title: Mixed Reality とは
description: この記事では、複合現実について定義し、複合現実の範囲における単純な AR デバイスや VR デバイス、および Microsoft HoloLens や Windows Mixed Reality イマーシブ ヘッドセットなどの Windows Mixed Reality デバイスの位置づけについて説明します。
author: brandonbray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: 複合現実, ホログラフィック, ar, vr, mr, xr, 拡張現実, 仮想現実, 説明
ms.localizationpriority: high
ms.openlocfilehash: 7b0dcbdb88f880d4c1632fae874ba6a610f023fb
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278050"
---
# <a name="what-is-mixed-reality"></a><span data-ttu-id="64212-104">Mixed Reality とは</span><span class="sxs-lookup"><span data-stu-id="64212-104">What is mixed reality?</span></span>

![HoloLens 2 での手を使ったポイントとコミット](images/02_MixedRealitySlashMixedReality.png)

<span data-ttu-id="64212-106">Mixed Reality は現実世界とデジタル世界を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="64212-106">Mixed reality is the result of blending the physical world with the digital world.</span></span> <span data-ttu-id="64212-107">Mixed Reality は、人間、コンピューター、および環境の相互作用における次の進化であり、これまでは想像することしかできなかった可能性が実現されます。</span><span class="sxs-lookup"><span data-stu-id="64212-107">Mixed reality is the next evolution in human, computer, and environment interaction and unlocks possibilities that before now were restricted to our imaginations.</span></span> <span data-ttu-id="64212-108">これは、コンピューター ビジョン、グラフィカル処理能力、ディスプレイ テクノロジ、および入力システムの進歩によって可能になります。</span><span class="sxs-lookup"><span data-stu-id="64212-108">It is made possible by advancements in computer vision, graphical processing power, display technology, and input systems.</span></span> <span data-ttu-id="64212-109">"*複合現実*" という用語は、ポール・ミルグラムと岸野文郎による 1994 年の論文『[複合現実のビジュアル表示の分類](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)』で初めて紹介されました。</span><span class="sxs-lookup"><span data-stu-id="64212-109">The term *mixed reality* was originally introduced in a 1994 paper by Paul Milgram and Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)."</span></span> <span data-ttu-id="64212-110">この論文では、"*仮想現実連続体*" の概念が導入され、表示への分類法のカテゴリの適用方法に焦点が当てられていました。</span><span class="sxs-lookup"><span data-stu-id="64212-110">Their paper introduced the concept of the *virtuality continuum*, and focused on how the categorization of taxonomy applied to displays.</span></span> <span data-ttu-id="64212-111">それ以降、複合現実の応用は表示の範囲を超えるものになっています。</span><span class="sxs-lookup"><span data-stu-id="64212-111">Since then, the application of mixed reality goes beyond displays.</span></span> <span data-ttu-id="64212-112">環境入力、空間サウンド、場所も含まれるようになっています。</span><span class="sxs-lookup"><span data-stu-id="64212-112">It also includes environmental input, spatial sound, and location.</span></span>

<span data-ttu-id="64212-113">![複合現実の範囲](images/mixedrealityspectrum-worlds.png)</span><span class="sxs-lookup"><span data-stu-id="64212-113">![The mixed reality spectrum](images/mixedrealityspectrum-worlds.png)</span></span><br>
<span data-ttu-id="64212-114">*図: 複合現実は現実世界とデジタル世界を組み合わせたものです。*</span><span class="sxs-lookup"><span data-stu-id="64212-114">*Image: Mixed reality is the result of blending the physical world with the digital world.*</span></span>

<br>

---

## <a name="environmental-input-and-perception"></a><span data-ttu-id="64212-115">環境の入力と認識</span><span class="sxs-lookup"><span data-stu-id="64212-115">Environmental input and perception</span></span>

<span data-ttu-id="64212-116">過去数十年にわたり、人間とコンピューター入力の関係は十分に研究されてきました。</span><span class="sxs-lookup"><span data-stu-id="64212-116">Over the past several decades, the relationship between human and computer input has been well explored.</span></span> <span data-ttu-id="64212-117">また、"*人間とコンピューターの相互作用*" (HCI) と呼ばれる、広く研究されている分野もあります。</span><span class="sxs-lookup"><span data-stu-id="64212-117">It even has a widely studied discipline known as *human computer interaction* or HCI.</span></span> <span data-ttu-id="64212-118">人間の入力は、キーボード、マウス、タッチ、インク、音声、さらには Kinect の骨格追跡など、さまざまな方法で行われます。</span><span class="sxs-lookup"><span data-stu-id="64212-118">Human input happens through a variety of means, including keyboards, mice, touch, ink, voice, and even Kinect skeletal tracking.</span></span>

<span data-ttu-id="64212-119">センサーと処理の進歩は、環境からのコンピューター入力の新しい領域を生み出しています。</span><span class="sxs-lookup"><span data-stu-id="64212-119">Advancements in sensors and processing are giving rise to a new area of computer input from environments.</span></span> <span data-ttu-id="64212-120">コンピューターと環境の間の相互作用とは、実質的に、環境を理解または "*認識*" することです。</span><span class="sxs-lookup"><span data-stu-id="64212-120">The interaction between computers and environments is effectively environmental understanding or *perception*.</span></span> <span data-ttu-id="64212-121">そのため、環境情報を公開する Windows の API は、[認識 API](https://docs.microsoft.com/uwp/api/Windows.Perception) と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="64212-121">Hence the API names in Windows that reveal environmental information are called the [perception APIs](https://docs.microsoft.com/uwp/api/Windows.Perception).</span></span> <span data-ttu-id="64212-122">環境入力では、世界での人の位置 ([頭の追跡](coordinate-systems.md)など)、表面と境界 ([空間マッピング](spatial-mapping.md)や[シーンの理解](scene-understanding.md)など)、環境光、環境音、オブジェクト認識、場所などがキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="64212-122">Environmental input captures things like a person's position in the world (e.g. [head tracking](coordinate-systems.md)), surfaces and boundaries (e.g. [spatial mapping](spatial-mapping.md) and [scene understanding](scene-understanding.md)), ambient lighting, environmental sound, object recognition, and location.</span></span>

<br>

<span data-ttu-id="64212-123">![コンピューター、人間、環境間の相互作用を示すベン図](images/mixed-reality-venn-diagram-300px.png)</span><span class="sxs-lookup"><span data-stu-id="64212-123">![Venn diagram showing interactions between computers, humans and environments](images/mixed-reality-venn-diagram-300px.png)</span></span><br><span data-ttu-id="64212-124"> \
*図: コンピューター、人間、環境の間の相互作用。*</span><span class="sxs-lookup"><span data-stu-id="64212-124"> \
*Image: The interactions between between computers, humans and environments.*</span></span>

<br>

<span data-ttu-id="64212-125">ここで、**コンピューター処理、人間入力、環境入力**の 3 つすべての組み合わせにより、真の複合現実エクスペリエンスを作成する機会が得られます。</span><span class="sxs-lookup"><span data-stu-id="64212-125">Now, the combination of all three--**computer processing, human input, and environmental input**--sets the opportunity to create true mixed reality experiences.</span></span> <span data-ttu-id="64212-126">物理的な世界内の移動は、デジタル世界での動きに変換できます。</span><span class="sxs-lookup"><span data-stu-id="64212-126">Movement through the physical world can translate to movement in the digital world.</span></span> <span data-ttu-id="64212-127">物理的な世界の境界は、デジタル環境でのゲーム プレイなどのアプリケーション エクスペリエンスに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="64212-127">Boundaries in the physical world can influence application experiences, such as game play, in the digital world.</span></span> <span data-ttu-id="64212-128">環境入力がないと、エクスペリエンスで物理的な現実とデジタル的な現実を組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="64212-128">Without environmental input, experiences cannot blend between physical and digital realities.</span></span><br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a><span data-ttu-id="64212-129">複合現実の範囲</span><span class="sxs-lookup"><span data-stu-id="64212-129">The mixed reality spectrum</span></span>

<span data-ttu-id="64212-130">複合現実では物理世界とデジタル世界の両方が融合されるため、これらの 2 つの現実によって、仮想現実連続体と呼ばれる範囲の両端が定義されます。</span><span class="sxs-lookup"><span data-stu-id="64212-130">Since mixed reality blends both physical and digital worlds, these two realities define the polar ends of a spectrum known as the virtuality continuum.</span></span> <span data-ttu-id="64212-131">わかりやすくするため、これを "*複合現実の範囲*" と呼ぶことにします。</span><span class="sxs-lookup"><span data-stu-id="64212-131">For simplicity, we refer to this as the *mixed reality spectrum*.</span></span> <span data-ttu-id="64212-132">左側には、人間が存在する物理的な現実があります。右側には、対応するデジタル的な現実があります。</span><span class="sxs-lookup"><span data-stu-id="64212-132">On the left-hand side we have physical reality in which we, humans, exist; on the right-hand side we have the corresponding digital reality.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a><span data-ttu-id="64212-133">拡張現実と仮想現実</span><span class="sxs-lookup"><span data-stu-id="64212-133">Augmented vs. virtual reality</span></span>

<span data-ttu-id="64212-134">現在市場にあるほとんどの携帯電話には、環境を理解する機能はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="64212-134">Most mobile phones on the market today have little to no environmental understanding capabilities.</span></span> <span data-ttu-id="64212-135">そのため、これらによって提供されるエクスペリエンスでは、物理現実とデジタル現実を混在させることはできません。</span><span class="sxs-lookup"><span data-stu-id="64212-135">Thus the experiences they offer cannot mix between physical and digital realities.</span></span> <span data-ttu-id="64212-136">物理的な世界のビデオ ストリームにグラフィックを重ね合わせるエクスペリエンスは、"*拡張現実*" です。</span><span class="sxs-lookup"><span data-stu-id="64212-136">The experiences that overlay graphics on video streams of the physical world are *augmented reality*.</span></span> <span data-ttu-id="64212-137">人の視野を遮ってデジタル エクスペリエンスを提供するエクスペリエンスは、"*仮想現実*" です。</span><span class="sxs-lookup"><span data-stu-id="64212-137">The experiences that occlude your view to present a digital experience are *virtual reality*.</span></span> <span data-ttu-id="64212-138">ご覧のように、これら 2 つの極端の間で可能になるエクスペリエンスが、"*複合現実*" です。</span><span class="sxs-lookup"><span data-stu-id="64212-138">As you can see, the experiences enabled between these two extremes is *mixed reality*:</span></span>
* <span data-ttu-id="64212-139">物理的な世界から始まって、ホログラムなどのデジタル オブジェクトが、実際に存在しているかのように配置されます。</span><span class="sxs-lookup"><span data-stu-id="64212-139">Starting with the physical world, placing a digital object, such as a hologram, as if it was really there.</span></span>
* <span data-ttu-id="64212-140">物理的な世界から始まって、別の人のデジタル表現 (アバター) を使用して、ノートを離れるときに立っていた場所が示されます。</span><span class="sxs-lookup"><span data-stu-id="64212-140">Starting with the physical world, a digital representation of another person--an avatar--shows the location where they were standing when leaving notes.</span></span> <span data-ttu-id="64212-141">つまり、異なる時点での非同期コラボレーションを表すエクスペリエンスです。</span><span class="sxs-lookup"><span data-stu-id="64212-141">In other words, experiences that represent asynchronous collaboration at different points in time.</span></span>
* <span data-ttu-id="64212-142">デジタル世界から始まって、壁や家具など、物理的な世界の物理的な境界が、ユーザーが物理的なオブジェクトを回避できるように、エクスペリエンス内にデジタルで表示されます。</span><span class="sxs-lookup"><span data-stu-id="64212-142">Starting with a digital world, physical boundaries from the physical world, such as walls and furniture, appear digitally within the experience to help users avoid physical objects.</span></span>


<br>

<span data-ttu-id="64212-143">![複合現実の範囲](images/mixedrealityspectrum.png)</span><span class="sxs-lookup"><span data-stu-id="64212-143">![The mixed reality spectrum](images/mixedrealityspectrum.png)</span></span><br>
<span data-ttu-id="64212-144">*図: 複合現実の範囲*</span><span class="sxs-lookup"><span data-stu-id="64212-144">*Image: The mixed reality spectrum*</span></span>

<br>

<span data-ttu-id="64212-145">現在利用可能なほとんどの拡張現実および仮想現実の製品は、この範囲のごく一部を表しています。</span><span class="sxs-lookup"><span data-stu-id="64212-145">Most augmented reality and virtual reality offerings available today represent a very small part of this spectrum.</span></span> <span data-ttu-id="64212-146">ただし、それらはより大きな複合現実の範囲のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="64212-146">They are, however, subsets of the larger mixed reality spectrum.</span></span> <span data-ttu-id="64212-147">Windows 10 は、範囲全体を念頭に置いて構築されており、人間、場所、物のデジタル表現を現実の世界と融合できます。</span><span class="sxs-lookup"><span data-stu-id="64212-147">Windows 10 is built with the entire spectrum in mind, and allows blending digital representations of people, places, and things with the real world.</span></span>




## <a name="devices-and-experiences"></a><span data-ttu-id="64212-148">デバイスとエクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="64212-148">Devices and experiences</span></span>


<span data-ttu-id="64212-149">Windows Mixed Reality のエクスペリエンスを提供するデバイスには、主に次の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="64212-149">There are two main types of devices that deliver Windows Mixed Reality experiences:</span></span>
1. <span data-ttu-id="64212-150">**ホログラフィック デバイス。**</span><span class="sxs-lookup"><span data-stu-id="64212-150">**Holographic devices.**</span></span> <span data-ttu-id="64212-151">これらのデバイスの特徴は、実際にそこに存在するかのように、デジタル コンテンツを現実の世界に配置できることです。</span><span class="sxs-lookup"><span data-stu-id="64212-151">These are characterized by the device's ability to place digital content in the real world as if it were really there.</span></span>
2. <span data-ttu-id="64212-152">**イマーシブ デバイス。**</span><span class="sxs-lookup"><span data-stu-id="64212-152">**Immersive devices.**</span></span> <span data-ttu-id="64212-153">これらのデバイスの特徴は、物理的な世界を隠し、デジタル エクスペリエンスで置き換えることによって、"存在感" を作成できることです。</span><span class="sxs-lookup"><span data-stu-id="64212-153">These are characterized by the device's ability to create a sense of "presence"--hiding the physical world, and replacing it with a digital experience.</span></span>

<table>
<tr>
<th width="30%"> <span data-ttu-id="64212-154">特性</span><span class="sxs-lookup"><span data-stu-id="64212-154">Characteristic</span></span></th><th width="35%"> <span data-ttu-id="64212-155">ホログラフィック デバイス</span><span class="sxs-lookup"><span data-stu-id="64212-155">Holographic devices</span></span></th><th width="35%"> <span data-ttu-id="64212-156">イマーシブ デバイス</span><span class="sxs-lookup"><span data-stu-id="64212-156">Immersive devices</span></span></th>
</tr><tr>
<td><span data-ttu-id="64212-157"><strong>デバイスの例</strong></span><span class="sxs-lookup"><span data-stu-id="64212-157"><strong>Example device</strong></span></span></td><td> <span data-ttu-id="64212-158">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="64212-158">Microsoft HoloLens</span></span><br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> <span data-ttu-id="64212-159">Samsung HMD Odyssey+</span><span class="sxs-lookup"><span data-stu-id="64212-159">Samsung HMD Odyssey+</span></span><br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><span data-ttu-id="64212-160"><strong>Display</strong></span><span class="sxs-lookup"><span data-stu-id="64212-160"><strong>Display</strong></span></span></td><td> <span data-ttu-id="64212-161">シースルー ディスプレイ。</span><span class="sxs-lookup"><span data-stu-id="64212-161">See-through display.</span></span> <span data-ttu-id="64212-162">ユーザーはヘッドセットを装着している間も物理環境を見ることができます。</span><span class="sxs-lookup"><span data-stu-id="64212-162">Allows user to see the physical environment while wearing the headset.</span></span></td><td> <span data-ttu-id="64212-163">非透過ディスプレイ。</span><span class="sxs-lookup"><span data-stu-id="64212-163">Opaque display.</span></span> <span data-ttu-id="64212-164">ユーザーはヘッドセットを装着している間は物理環境を見ることができません。</span><span class="sxs-lookup"><span data-stu-id="64212-164">Blocks out the physical environment while wearing the headset.</span></span></td>
</tr><tr>
<td><span data-ttu-id="64212-165"><strong>移動</strong></span><span class="sxs-lookup"><span data-stu-id="64212-165"><strong>Movement</strong></span></span></td><td> <span data-ttu-id="64212-166">回転と平行移動の両方で、6 自由度の完全な移動。</span><span class="sxs-lookup"><span data-stu-id="64212-166">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td><td> <span data-ttu-id="64212-167">回転と平行移動の両方で、6 自由度の完全な移動。</span><span class="sxs-lookup"><span data-stu-id="64212-167">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td>
</tr>
</table>



<span data-ttu-id="64212-168">デバイスが (USB ケーブルまたは Wi-Fi 経由で) 別の PC に接続されているか、または自己完結型 (非接続) であるかは、デバイスがホログラフィックかイマーシブかに影響しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="64212-168">Note, whether a device is connected to or tethered to a separate PC (via USB cable or Wi-Fi) or self-contained (untethered) does not reflect whether a device is holographic or immersive.</span></span> <span data-ttu-id="64212-169">確かに、モビリティ向上機能によってエクスペリエンスは向上し、ホログラフィック デバイスとイマーシブ デバイスはどちらも接続式または非接続式にできます。</span><span class="sxs-lookup"><span data-stu-id="64212-169">Certainly, features that improve mobility lead to better experiences, and both holographic and immersive devices could be tethered or untethered.</span></span>


<span data-ttu-id="64212-170">技術的な進歩によって、複合現実エクスペリエンスは可能になりました。</span><span class="sxs-lookup"><span data-stu-id="64212-170">Technological advancement is what has enabled mixed reality experiences.</span></span> <span data-ttu-id="64212-171">現在、すべての範囲でエクスペリエンスを実行できるデバイスはありません。</span><span class="sxs-lookup"><span data-stu-id="64212-171">There are no devices today that can run experiences across the entire spectrum.</span></span> <span data-ttu-id="64212-172">ただし、Windows 10 では、デバイスの製造元と開発者の両方に共通の複合現実プラットフォームが提供されています。</span><span class="sxs-lookup"><span data-stu-id="64212-172">However, Windows 10 provides a common mixed reality platform for both device manufacturers and developers.</span></span> <span data-ttu-id="64212-173">今日のデバイスでは、混合現実の範囲内の特定の範囲をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="64212-173">Devices today can support a specific range within the mixed reality spectrum.</span></span> <span data-ttu-id="64212-174">時間の経過と共に、新しいデバイスによってその範囲が広がります。</span><span class="sxs-lookup"><span data-stu-id="64212-174">Over time, new devices will expand that range.</span></span> <span data-ttu-id="64212-175">将来、ホログラフィック デバイスはよりイマーシブになり、イマーシブ デバイスはよりホログラフィックになります。</span><span class="sxs-lookup"><span data-stu-id="64212-175">In the future, holographic devices will become more immersive, and immersive devices will become more holographic.</span></span>

<br>

<span data-ttu-id="64212-176">![混合現実の範囲におけるデバイスの種類](images/Final_WhatIsMixedReality07.png)</span><span class="sxs-lookup"><span data-stu-id="64212-176">![Device types in the mixed reality spectrum](images/Final_WhatIsMixedReality07.png)</span></span><br>
<span data-ttu-id="64212-177">*図: 混合現実の範囲におけるデバイスの位置づけ*</span><span class="sxs-lookup"><span data-stu-id="64212-177">*Image: Where devices exist on the mixed reality spectrum*</span></span>

<span data-ttu-id="64212-178">多くの場合、アプリケーションまたはゲームの開発者が作成しようとしているエクスペリエンスの種類を考えることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="64212-178">Often, it is best to think what type of experience an application or game developer wants to create.</span></span> <span data-ttu-id="64212-179">エクスペリエンスは、通常、範囲の特定の点または部分を対象としています。</span><span class="sxs-lookup"><span data-stu-id="64212-179">The experiences will typically target a specific point or part on the spectrum.</span></span> <span data-ttu-id="64212-180">次に、開発者は、対象とするデバイスの機能を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64212-180">Then, developers should consider the capabilities of devices they want to target.</span></span> <span data-ttu-id="64212-181">たとえば、物理的な世界に依存するエクスペリエンスは、HoloLens で実行するのが最善です。</span><span class="sxs-lookup"><span data-stu-id="64212-181">For example, experiences that rely on the physical world will run best on HoloLens.</span></span>
* <span data-ttu-id="64212-182">**左に向かう (物理的な現実に近づく)。**</span><span class="sxs-lookup"><span data-stu-id="64212-182">**Towards the left (near physical reality).**</span></span> <span data-ttu-id="64212-183">ユーザーは、物理的な環境内に存在していて、その環境を離れたと信じさせられることはありません。</span><span class="sxs-lookup"><span data-stu-id="64212-183">Users remain present in their physical environment and are never made to believe they have left that environment.</span></span>
* <span data-ttu-id="64212-184">**中央 (完全な複合現実)。**</span><span class="sxs-lookup"><span data-stu-id="64212-184">**In the middle (fully mixed reality).**</span></span> <span data-ttu-id="64212-185">これらのエクスペリエンスでは、現実世界とデジタル世界が融合されています。</span><span class="sxs-lookup"><span data-stu-id="64212-185">These experiences blend the real world and the digital world.</span></span> <span data-ttu-id="64212-186">映画『[ジュマンジ](https://en.wikipedia.org/wiki/Jumanji)』を見た人なら、物語が展開する家の物理的な構造と、ジャングルの環境がどのようにブレンドされていたかわかります。</span><span class="sxs-lookup"><span data-stu-id="64212-186">Viewers who have seen the movie [Jumanji](https://en.wikipedia.org/wiki/Jumanji) can reconcile how the physical structure of the house where the story took place was blended with a jungle environment.</span></span>
* <span data-ttu-id="64212-187">**右に向かう (デジタル的な現実に近づく)。**</span><span class="sxs-lookup"><span data-stu-id="64212-187">**Towards the right (near digital reality).**</span></span> <span data-ttu-id="64212-188">ユーザーは、完全なデジタル環境を体験し、自分の周りの物理的な環境で起こっていることは認識しません。</span><span class="sxs-lookup"><span data-stu-id="64212-188">Users experience a completely digital environment, and are unaware of what occurs in the physical environment around them.</span></span>


## <a name="see-also"></a><span data-ttu-id="64212-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="64212-189">See also</span></span>

* [<span data-ttu-id="64212-190">ホログラムとは</span><span class="sxs-lookup"><span data-stu-id="64212-190">What is a hologram?</span></span>](hologram.md)
* [<span data-ttu-id="64212-191">Mixed Reality の基本を理解する</span><span class="sxs-lookup"><span data-stu-id="64212-191">Understand the basics of mixed reality</span></span>](index.md#understand-the-basics)
* [<span data-ttu-id="64212-192">作成とプロトタイプ作成を始める</span><span class="sxs-lookup"><span data-stu-id="64212-192">Start creating and prototyping</span></span>](design.md)
* [<span data-ttu-id="64212-193">ツールとアーキテクチャについて学習する</span><span class="sxs-lookup"><span data-stu-id="64212-193">Learn the tools and architecture</span></span>](development.md)

