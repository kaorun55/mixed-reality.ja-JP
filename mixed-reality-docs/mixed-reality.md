---
title: Mixed Reality とは
description: この記事では、mixed reality を定義し、単純な AR デバイスと VR デバイス、および Microsoft HoloLens や Windows Mixed Reality イマーシブヘッドセットなどの Windows Mixed Reality デバイスと、混合現実の範囲について説明します。
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: mixed reality、holographic、ar、vr、mr、xr、強化現実、仮想現実、説明
ms.openlocfilehash: 65588902565ee0c5a1710f823311ccdecc23230e
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539557"
---
# <a name="what-is-mixed-reality"></a><span data-ttu-id="28c45-104">Mixed Reality とは</span><span class="sxs-lookup"><span data-stu-id="28c45-104">What is mixed reality?</span></span>

![ハンズオンを使用したポイントとコミット (HoloLens 2)](images/02_MixedRealitySlashMixedReality.png)

<span data-ttu-id="28c45-106">Mixed Reality は現実世界とデジタル世界を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="28c45-106">Mixed reality is the result of blending the physical world with the digital world.</span></span> <span data-ttu-id="28c45-107">Mixed Reality は、人間、コンピューター、および環境の相互作用における次の進化であり、これまでは想像することしかできなかった可能性が実現されます。</span><span class="sxs-lookup"><span data-stu-id="28c45-107">Mixed reality is the next evolution in human, computer, and environment interaction and unlocks possibilities that before now were restricted to our imaginations.</span></span> <span data-ttu-id="28c45-108">これは、コンピュータービジョン、グラフィカル処理能力、表示テクノロジ、および入力システムの機能強化によって可能になります。</span><span class="sxs-lookup"><span data-stu-id="28c45-108">It is made possible by advancements in computer vision, graphical processing power, display technology, and input systems.</span></span> <span data-ttu-id="28c45-109">*Mixed reality*という用語は、当初、Paul ミルグラムと Fumio Kishino によって[1994 のホワイト](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)ペーパーに導入されました。</span><span class="sxs-lookup"><span data-stu-id="28c45-109">The term *mixed reality* was originally introduced in a 1994 paper by Paul Milgram and Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)."</span></span> <span data-ttu-id="28c45-110">このホワイトペーパーでは、 *virtuality 連続性*の概念を紹介し、分類の分類がどのように表示されるかに焦点を絞っています。</span><span class="sxs-lookup"><span data-stu-id="28c45-110">Their paper introduced the concept of the *virtuality continuum*, and focused on how the categorization of taxonomy applied to displays.</span></span> <span data-ttu-id="28c45-111">そのため、混合現実のアプリケーションは表示されません。</span><span class="sxs-lookup"><span data-stu-id="28c45-111">Since then, the application of mixed reality goes beyond displays.</span></span> <span data-ttu-id="28c45-112">また、環境の入力、空間サウンド、場所も含まれます。</span><span class="sxs-lookup"><span data-stu-id="28c45-112">It also includes environmental input, spatial sound, and location.</span></span>

<span data-ttu-id="28c45-113">混合現実のスペクトルを ![](images/MixedRealitySpectrum-worlds.jpg)</span><span class="sxs-lookup"><span data-stu-id="28c45-113">![The mixed reality spectrum](images/MixedRealitySpectrum-worlds.jpg)</span></span><br>
<span data-ttu-id="28c45-114">*Mixed reality は、物理的な世界とデジタルの世界をブレンドした結果です。*</span><span class="sxs-lookup"><span data-stu-id="28c45-114">*Mixed reality is the result of blending the physical world with the digital world.*</span></span>

<br>

---

## <a name="environmental-input-and-perception"></a><span data-ttu-id="28c45-115">環境の入力と認識</span><span class="sxs-lookup"><span data-stu-id="28c45-115">Environmental input and perception</span></span>

<span data-ttu-id="28c45-116">過去数年にわたり、人間とコンピューターの両方の入力の関係が十分に調査されました。</span><span class="sxs-lookup"><span data-stu-id="28c45-116">Over the past several decades, the relationship between human and computer input has been well explored.</span></span> <span data-ttu-id="28c45-117">また、*人間のコンピューターの操作*や HCI と呼ばれる、広く研究されている分野もあります。</span><span class="sxs-lookup"><span data-stu-id="28c45-117">It even has a widely studied discipline known as *human computer interaction* or HCI.</span></span> <span data-ttu-id="28c45-118">人間の入力は、キーボード、マウス、タッチ、インク、音声、さらには Kinect の骨格追跡など、さまざまな方法で行われます。</span><span class="sxs-lookup"><span data-stu-id="28c45-118">Human input happens through a variety of means, including keyboards, mice, touch, ink, voice, and even Kinect skeletal tracking.</span></span>

<span data-ttu-id="28c45-119">センサーと処理の進歩は、環境からのコンピューター入力の新しい領域に大きくなります。</span><span class="sxs-lookup"><span data-stu-id="28c45-119">Advancements in sensors and processing are giving rise to a new area of computer input from environments.</span></span> <span data-ttu-id="28c45-120">コンピューターと環境の間の相互作用は、実質的には環境の理解または*認識*です。</span><span class="sxs-lookup"><span data-stu-id="28c45-120">The interaction between computers and environments is effectively environmental understanding or *perception*.</span></span> <span data-ttu-id="28c45-121">そのため、環境情報を公開する Windows の API 名は、[認識 api](https://docs.microsoft.com/uwp/api/Windows.Perception)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="28c45-121">Hence the API names in Windows that reveal environmental information are called the [perception APIs](https://docs.microsoft.com/uwp/api/Windows.Perception).</span></span> <span data-ttu-id="28c45-122">環境入力では、世界中の人の位置 ([ヘッドトラッキング](coordinate-systems.md)など)、表面と境界 ([空間マッピング](spatial-mapping.md)と[シーンの理解](scene-understanding.md)など)、アンビエント照明、環境サウンド、オブジェクト認識などがキャプチャされます。との場所。</span><span class="sxs-lookup"><span data-stu-id="28c45-122">Environmental input captures things like a person's position in the world (e.g. [head tracking](coordinate-systems.md)), surfaces and boundaries (e.g. [spatial mapping](spatial-mapping.md) and [scene understanding](scene-understanding.md)), ambient lighting, environmental sound, object recognition, and location.</span></span>

<br>



:::row:::
    :::column:::
        <span data-ttu-id="28c45-123">ここで、3つの**コンピューターの処理、人間による入力、および環境入力**のすべてを組み合わせて、真の mixed reality エクスペリエンスを作成する機会を設定します。</span><span class="sxs-lookup"><span data-stu-id="28c45-123">Now, the combination of all three--**computer processing, human input, and environmental input**--sets the opportunity to create true mixed reality experiences.</span></span> <span data-ttu-id="28c45-124">物理的な世界への移動は、デジタル世界での動きにつながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="28c45-124">Movement through the physical world can translate to movement in the digital world.</span></span> <span data-ttu-id="28c45-125">物理的な世界の境界は、デジタル環境でのゲームプレイなどのアプリケーションエクスペリエンスに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="28c45-125">Boundaries in the physical world can influence application experiences, such as game play, in the digital world.</span></span> <span data-ttu-id="28c45-126">環境情報を入力しないと、経験によって物理的な現実とデジタルの現実とを組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="28c45-126">Without environmental input, experiences cannot blend between physical and digital realities.</span></span><br>
        <br>
        <span data-ttu-id="28c45-127">*イメージ: コンピューター、人間、環境の間の相互作用。*</span><span class="sxs-lookup"><span data-stu-id="28c45-127">*Image: The interactions between between computers, humans and environments.*</span></span>
    :::column-end:::
        :::column:::
       ![コンピューター、人間、および環境間の相互作用を示すベン図](images/mixed-reality-venn-diagram-300px.png)<br> 
    :::column-end:::
:::row-end:::

<br>

---


## <a name="the-mixed-reality-spectrum"></a><span data-ttu-id="28c45-129">混合現実のスペクトラム</span><span class="sxs-lookup"><span data-stu-id="28c45-129">The mixed reality spectrum</span></span>

<span data-ttu-id="28c45-130">Mixed reality は物理的な世界とデジタルの両方の面を融合しているため、これらの2つの現実は、virtuality の連続性と呼ばれるスペクトルの極端を定義しています。</span><span class="sxs-lookup"><span data-stu-id="28c45-130">Since mixed reality blends both physical and digital worlds, these two realities define the polar ends of a spectrum known as the virtuality continuum.</span></span> <span data-ttu-id="28c45-131">わかりやすくするために、これを*混合現実のスペクトラム*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="28c45-131">For simplicity, we refer to this as the *mixed reality spectrum*.</span></span> <span data-ttu-id="28c45-132">左側には、人間が存在する物理的な現実があります。右側には、対応するデジタル現実があります。</span><span class="sxs-lookup"><span data-stu-id="28c45-132">On the left-hand side we have physical reality in which we, humans, exist; on the right-hand side we have the corresponding digital reality.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a><span data-ttu-id="28c45-133">拡張と仮想現実の比較</span><span class="sxs-lookup"><span data-stu-id="28c45-133">Augmented vs. virtual reality</span></span>

<span data-ttu-id="28c45-134">現在市場にあるほとんどの携帯電話では、環境を理解する機能はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="28c45-134">Most mobile phones on the market today have little to no environmental understanding capabilities.</span></span> <span data-ttu-id="28c45-135">そのため、これらのエクスペリエンスでは、物理的な現実とデジタルの現実を混在させることはできません。</span><span class="sxs-lookup"><span data-stu-id="28c45-135">Thus the experiences they offer cannot mix between physical and digital realities.</span></span> <span data-ttu-id="28c45-136">物理的な世界のビデオストリームにグラフィックスを重ね合わせるというエクスペリエンスが、*現実*に拡張されています。</span><span class="sxs-lookup"><span data-stu-id="28c45-136">The experiences that overlay graphics on video streams of the physical world are *augmented reality*.</span></span> <span data-ttu-id="28c45-137">デジタルエクスペリエンスを提供するためにビューを occlude するエクスペリエンスは、*仮想現実*です。</span><span class="sxs-lookup"><span data-stu-id="28c45-137">The experiences that occlude your view to present a digital experience are *virtual reality*.</span></span> <span data-ttu-id="28c45-138">ご覧のように、これら2つの極端な間で有効になっているエクスペリエンスは*mixed reality*です。</span><span class="sxs-lookup"><span data-stu-id="28c45-138">As you can see, the experiences enabled between these two extremes is *mixed reality*:</span></span>
* <span data-ttu-id="28c45-139">物理的な世界から、ホログラムなどのデジタルオブジェクトを実際に存在しているかのように配置します。</span><span class="sxs-lookup"><span data-stu-id="28c45-139">Starting with the physical world, placing a digital object, such as a hologram, as if it was really there.</span></span>
* <span data-ttu-id="28c45-140">物理的な世界から、別の人のデジタル表現 (アバター) を使用して、ノートを離れるときの場所を示しています。</span><span class="sxs-lookup"><span data-stu-id="28c45-140">Starting with the physical world, a digital representation of another person--an avatar--shows the location where they were standing when leaving notes.</span></span> <span data-ttu-id="28c45-141">つまり、さまざまな時点での非同期コラボレーションを表すエクスペリエンスです。</span><span class="sxs-lookup"><span data-stu-id="28c45-141">In other words, experiences that represent asynchronous collaboration at different points in time.</span></span>
* <span data-ttu-id="28c45-142">デジタル環境では、壁や家具など、物理的な世界の物理的な境界は、ユーザーが物理的なオブジェクトを回避するのに役立つように、エクスペリエンス内にデジタルで表示されます。</span><span class="sxs-lookup"><span data-stu-id="28c45-142">Starting with a digital world, physical boundaries from the physical world, such as walls and furniture, appear digitally within the experience to help users avoid physical objects.</span></span>


<br>

<span data-ttu-id="28c45-143">混合現実のスペクトルを ![](images/MixedRealitySpectrum.jpg)</span><span class="sxs-lookup"><span data-stu-id="28c45-143">![The mixed reality spectrum](images/MixedRealitySpectrum.jpg)</span></span><br>
<span data-ttu-id="28c45-144">*混合現実のスペクトラム*</span><span class="sxs-lookup"><span data-stu-id="28c45-144">*The mixed reality spectrum*</span></span>

<br>

<span data-ttu-id="28c45-145">現在利用可能なほとんどの拡張現実および仮想現実のオファリングは、この範囲のごく一部を表しています。</span><span class="sxs-lookup"><span data-stu-id="28c45-145">Most augmented reality and virtual reality offerings available today represent a very small part of this spectrum.</span></span> <span data-ttu-id="28c45-146">ただし、より大きな混合現実の範囲のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="28c45-146">They are, however, subsets of the larger mixed reality spectrum.</span></span> <span data-ttu-id="28c45-147">Windows 10 は、すべての点を念頭に置いて構築されており、人間、場所、および物のデジタル表現を実際の世界にブレンドできます。</span><span class="sxs-lookup"><span data-stu-id="28c45-147">Windows 10 is built with the entire spectrum in mind, and allows blending digital representations of people, places, and things with the real world.</span></span>




## <a name="devices-and-experiences"></a><span data-ttu-id="28c45-148">デバイスとエクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="28c45-148">Devices and experiences</span></span>


<span data-ttu-id="28c45-149">Windows Mixed Reality エクスペリエンスを提供するデバイスには、主に次の2種類があります。</span><span class="sxs-lookup"><span data-stu-id="28c45-149">There are two main types of devices that deliver Windows Mixed Reality experiences:</span></span>
1. <span data-ttu-id="28c45-150">**Holographic デバイス。**</span><span class="sxs-lookup"><span data-stu-id="28c45-150">**Holographic devices.**</span></span> <span data-ttu-id="28c45-151">これらの特性は、デバイスが実際に存在しているかのように、実際の世界にデジタルコンテンツを配置する機能によって特徴付けられています。</span><span class="sxs-lookup"><span data-stu-id="28c45-151">These are characterized by the device's ability to place digital content in the real world as if it were really there.</span></span>
2. <span data-ttu-id="28c45-152">**イマーシブデバイス。**</span><span class="sxs-lookup"><span data-stu-id="28c45-152">**Immersive devices.**</span></span> <span data-ttu-id="28c45-153">これらは、物理的な世界を隠し、デジタル体験で置き換えることによって、デバイスの機能によって特徴付けられています。</span><span class="sxs-lookup"><span data-stu-id="28c45-153">These are characterized by the device's ability to create a sense of "presence"--hiding the physical world, and replacing it with a digital experience.</span></span>

<table>
<tr>
<th width="20%"> <span data-ttu-id="28c45-154">特性</span><span class="sxs-lookup"><span data-stu-id="28c45-154">Characteristic</span></span></th><th width="40%"> <span data-ttu-id="28c45-155">Holographic デバイス</span><span class="sxs-lookup"><span data-stu-id="28c45-155">Holographic Devices</span></span></th><th width="40%"> <span data-ttu-id="28c45-156">イマーシブデバイス</span><span class="sxs-lookup"><span data-stu-id="28c45-156">Immersive Devices</span></span></th>
</tr><tr>
<td> <span data-ttu-id="28c45-157">デバイスの例</span><span class="sxs-lookup"><span data-stu-id="28c45-157">Example Device</span></span></td><td> <span data-ttu-id="28c45-158">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="28c45-158">Microsoft HoloLens</span></span><br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> <span data-ttu-id="28c45-159">Acer Windows Mixed Reality Development Edition</span><span class="sxs-lookup"><span data-stu-id="28c45-159">Acer Windows Mixed Reality Development Edition</span></span><br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> <span data-ttu-id="28c45-160">[ディスプレイ]</span><span class="sxs-lookup"><span data-stu-id="28c45-160">Display</span></span></td><td> <span data-ttu-id="28c45-161"><i>「」を参照してください。</i></span><span class="sxs-lookup"><span data-stu-id="28c45-161"><i>See-through display.</i></span></span> <span data-ttu-id="28c45-162">ヘッドセットを装着しているときに、ユーザーが物理環境を確認できるようにします。</span><span class="sxs-lookup"><span data-stu-id="28c45-162">Allows user to see the physical environment while wearing the headset.</span></span></td><td> <span data-ttu-id="28c45-163"><i>非透過ディスプレイ。</i></span><span class="sxs-lookup"><span data-stu-id="28c45-163"><i>Opaque display.</i></span></span> <span data-ttu-id="28c45-164">ヘッドセットの装着中に物理環境をブロックします。</span><span class="sxs-lookup"><span data-stu-id="28c45-164">Blocks out the physical environment while wearing the headset.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="28c45-165">動かす</span><span class="sxs-lookup"><span data-stu-id="28c45-165">Movement</span></span></td><td> <span data-ttu-id="28c45-166">回転と翻訳の両方で、完全に6度の自由な移動。</span><span class="sxs-lookup"><span data-stu-id="28c45-166">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td><td> <span data-ttu-id="28c45-167">回転と翻訳の両方で、完全に6度の自由な移動。</span><span class="sxs-lookup"><span data-stu-id="28c45-167">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td>
</tr>
</table>

<span data-ttu-id="28c45-168">デバイスが別の PC に接続されているかどうか (USB ケーブルまたは Wi-fi 経由)、または自己完結型 (ならでは) であるかどうかは、デバイスが holographic かイマーシブかは反映されません。</span><span class="sxs-lookup"><span data-stu-id="28c45-168">Note, whether a device is connected to or tethered to a separate PC (via USB cable or Wi-Fi) or self-contained (untethered) does not reflect whether a device is holographic or immersive.</span></span> <span data-ttu-id="28c45-169">確かに、モビリティを向上させる機能によりエクスペリエンスが向上し、holographic デバイスとイマーシブデバイスの両方がテザリングさまたはならではになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="28c45-169">Certainly, features that improve mobility lead to better experiences, and both holographic and immersive devices could be tethered or untethered.</span></span>


<span data-ttu-id="28c45-170">技術的な進歩は、mixed reality エクスペリエンスを有効にしたものです。</span><span class="sxs-lookup"><span data-stu-id="28c45-170">Technological advancement is what has enabled mixed reality experiences.</span></span> <span data-ttu-id="28c45-171">現在、すべての範囲でエクスペリエンスを実行できるデバイスはありません。</span><span class="sxs-lookup"><span data-stu-id="28c45-171">There are no devices today that can run experiences across the entire spectrum.</span></span> <span data-ttu-id="28c45-172">ただし、Windows 10 では、デバイスの製造元と開発者の両方に共通の mixed reality プラットフォームが提供されます。</span><span class="sxs-lookup"><span data-stu-id="28c45-172">However, Windows 10 provides a common mixed reality platform for both device manufacturers and developers.</span></span> <span data-ttu-id="28c45-173">現在のデバイスは、混合現実の範囲内の特定の範囲をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="28c45-173">Devices today can support a specific range within the mixed reality spectrum.</span></span> <span data-ttu-id="28c45-174">時間の経過と共に、新しいデバイスによってその範囲が拡張されます。</span><span class="sxs-lookup"><span data-stu-id="28c45-174">Over time, new devices will expand that range.</span></span> <span data-ttu-id="28c45-175">将来、holographic デバイスはよりイマーシブになり、イマーシブデバイスはより holographic になります。</span><span class="sxs-lookup"><span data-stu-id="28c45-175">In the future, holographic devices will become more immersive, and immersive devices will become more holographic.</span></span>

<br>

<span data-ttu-id="28c45-176">混合現実スペクトルでのデバイスの種類の ![](images/MixedRealitySpectrum-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="28c45-176">![Device types in the mixed reality spectrum](images/MixedRealitySpectrum-devices.jpg)</span></span><br>
<span data-ttu-id="28c45-177">*混合現実のスペクトラムにデバイスが存在する場合*</span><span class="sxs-lookup"><span data-stu-id="28c45-177">*Where devices exist on the mixed reality spectrum*</span></span>

<span data-ttu-id="28c45-178">多くの場合、アプリケーションまたはゲーム開発者が作成しようとしているエクスペリエンスの種類を考えることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="28c45-178">Often, it is best to think what type of experience an application or game developer wants to create.</span></span> <span data-ttu-id="28c45-179">エクスペリエンスは、通常、特定のポイントまたは部分を対象としています。</span><span class="sxs-lookup"><span data-stu-id="28c45-179">The experiences will typically target a specific point or part on the spectrum.</span></span> <span data-ttu-id="28c45-180">次に、開発者は、対象とするデバイスの機能を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="28c45-180">Then, developers should consider the capabilities of devices they want to target.</span></span> <span data-ttu-id="28c45-181">たとえば、物理的な世界に依存するエクスペリエンスは、HoloLens で最高のパフォーマンスを発揮します。</span><span class="sxs-lookup"><span data-stu-id="28c45-181">For example, experiences that rely on the physical world will run best on HoloLens.</span></span>
* <span data-ttu-id="28c45-182">**左側 (ほぼ物理的な現実)。**</span><span class="sxs-lookup"><span data-stu-id="28c45-182">**Towards the left (near physical reality).**</span></span> <span data-ttu-id="28c45-183">ユーザーは、物理的な環境内に存在していて、その環境が離れていると信じられることはありません。</span><span class="sxs-lookup"><span data-stu-id="28c45-183">Users remain present in their physical environment and are never made to believe they have left that environment.</span></span>
* <span data-ttu-id="28c45-184">**中央に (完全に混在する現実)。**</span><span class="sxs-lookup"><span data-stu-id="28c45-184">**In the middle (fully mixed reality).**</span></span> <span data-ttu-id="28c45-185">これらのエクスペリエンスでは、現実世界とデジタル世界を融合しています。</span><span class="sxs-lookup"><span data-stu-id="28c45-185">These experiences blend the real world and the digital world.</span></span> <span data-ttu-id="28c45-186">映画の[Jumanji](https://en.wikipedia.org/wiki/Jumanji)を見た閲覧者は、ストーリーがどこで行われたかについて、その家の物理的な構造を調整して、ジャングル環境と連携させることができます。</span><span class="sxs-lookup"><span data-stu-id="28c45-186">Viewers who have seen the movie [Jumanji](https://en.wikipedia.org/wiki/Jumanji) can reconcile how the physical structure of the house where the story took place was blended with a jungle environment.</span></span>
* <span data-ttu-id="28c45-187">**右側に (デジタル現実に近い)。**</span><span class="sxs-lookup"><span data-stu-id="28c45-187">**Towards the right (near digital reality).**</span></span> <span data-ttu-id="28c45-188">ユーザーは、完全なデジタル環境を体験し、物理的な環境で何が起こっているかを認識していません。</span><span class="sxs-lookup"><span data-stu-id="28c45-188">Users experience a completely digital environment, and are unaware of what occurs in the physical environment around them.</span></span>


## <a name="see-also"></a><span data-ttu-id="28c45-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="28c45-189">See also</span></span>

* [<span data-ttu-id="28c45-190">ホログラムとは</span><span class="sxs-lookup"><span data-stu-id="28c45-190">What is a hologram?</span></span>](hologram.md)
* [<span data-ttu-id="28c45-191">Mixed reality の基本を理解する</span><span class="sxs-lookup"><span data-stu-id="28c45-191">Understand the basics of mixed reality</span></span>](index.md#understand-the-basics)
* [<span data-ttu-id="28c45-192">作成とプロトタイプ作成を開始する</span><span class="sxs-lookup"><span data-stu-id="28c45-192">Start creating and prototyping</span></span>](design.md)
* [<span data-ttu-id="28c45-193">ツールとアーキテクチャについて学習する</span><span class="sxs-lookup"><span data-stu-id="28c45-193">Learn the tools and architecture</span></span>](development.md)

