---
title: ルームのスキャンの視覚化
description: 空間マッピング データが必要なアプリケーションでは、時間の経過と共に自動的にこのデータを収集するデバイスに依存し、ユーザーとセッション間で、アクティブなデバイスと、環境を説明します。 します。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、アプリのパターン、設計、HoloLens、部屋のスキャン、空間が再構築を画面のマッピングをメッシュ
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829916"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="249da-104">ルームのスキャンの視覚化</span><span class="sxs-lookup"><span data-stu-id="249da-104">Room scan visualization</span></span>

<span data-ttu-id="249da-105">空間マッピング データが必要なアプリケーションでは、時間の経過と共に自動的にこのデータを収集するデバイスに依存し、ユーザーとセッション間で、アクティブなデバイスと、環境を説明します。 します。</span><span class="sxs-lookup"><span data-stu-id="249da-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="249da-106">完全を期すため、このデータの品質は、さまざまなユーザーが行った探索の量、探索からどれ時間だけが経過や、デバイス、領域をスキャンするので家具や扉などのオブジェクトが移動するかどうかなどの要因に依存します。</span><span class="sxs-lookup"><span data-stu-id="249da-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="249da-107">便利な空間のマッピング データを確認するには、アプリケーション開発者では、いくつかのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="249da-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="249da-108">どのような場合がありますが既に収集されたに依存します。</span><span class="sxs-lookup"><span data-stu-id="249da-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="249da-109">このデータが不完全である最初にします。</span><span class="sxs-lookup"><span data-stu-id="249da-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="249da-110">ブルーム ジェスチャを使用してホーム Windows Mixed Reality を取得し、結果を得るために使用する領域を調査し、ユーザーに確認します。</span><span class="sxs-lookup"><span data-stu-id="249da-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="249da-111">デバイスに必要なすべての領域が既知であることを確認するのにエア タップを使用できます。</span><span class="sxs-lookup"><span data-stu-id="249da-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="249da-112">独自のアプリケーションでカスタム探索エクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="249da-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="249da-113">システムによってこのような場合、探索中に収集される実際のデータが格納されているアプリケーションはこれを行う必要はないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="249da-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="249da-114">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="249da-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="249da-115"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="249da-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="249da-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="249da-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="249da-117"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="249da-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="249da-118">ルームのスキャンの視覚化</span><span class="sxs-lookup"><span data-stu-id="249da-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="249da-119">✔️</span><span class="sxs-lookup"><span data-stu-id="249da-119">✔️</span></span></td>
        <td><span data-ttu-id="249da-120">❌</span><span class="sxs-lookup"><span data-stu-id="249da-120">❌</span></span></td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="249da-121">カスタム スキャン エクスペリエンスの構築</span><span class="sxs-lookup"><span data-stu-id="249da-121">Building a custom scanning experience</span></span>

<span data-ttu-id="249da-122">アプリケーションは、ユーザーの完全性と品質を向上させるために追加の手順を実行するかどうかを判断するエクスペリエンスの先頭に空間マッピング データを分析することができます。</span><span class="sxs-lookup"><span data-stu-id="249da-122">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="249da-123">分析では、品質を改善する必要が示されている場合、開発者は、オーバーレイを示すために、世界中の視覚エフェクトを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="249da-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="249da-124">エクスペリエンスの一部である必要があるユーザー近傍の合計ボリュームの量</span><span class="sxs-lookup"><span data-stu-id="249da-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="249da-125">データを向上させるために、ユーザーが参照してください。</span><span class="sxs-lookup"><span data-stu-id="249da-125">Where the user should go to improve data</span></span>

<span data-ttu-id="249da-126">ユーザーは「良い」のスキャンが不明です。</span><span class="sxs-lookup"><span data-stu-id="249da-126">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="249da-127">表示されるかなどのスキャン – 平坦度、実際の壁からの距離を評価するように依頼している場合に検索するべきかを指示する必要があります。開発者は、空間マッピング データの探索またはスキャン フェーズ中に更新を含むフィードバック ループを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="249da-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="249da-128">多くの場合に必要な内容の操作を行います (例: を見て、ceiling 見て家具の背後にある)、ユーザーに伝えるための最適な場合があります、スキャンのために必要な品質を取得するためにします。</span><span class="sxs-lookup"><span data-stu-id="249da-128">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="249da-129">継続的な空間のマッピングとキャッシュ</span><span class="sxs-lookup"><span data-stu-id="249da-129">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="249da-130">空間マッピング データは、データ ソースのアプリケーションが使用できる最も高い重みです。</span><span class="sxs-lookup"><span data-stu-id="249da-130">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="249da-131">フレームのドロップなどのパフォーマンスの問題を回避するために途切れ、このデータの消費量が実行することも慎重にします。</span><span class="sxs-lookup"><span data-stu-id="249da-131">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="249da-132">両方の利点または有害なでき、作業中のアクティブなスキャン、開発者が経験に基づいて、使用する方法を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="249da-132">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="249da-133">キャッシュされた空間マッピング</span><span class="sxs-lookup"><span data-stu-id="249da-133">Cached spatial mapping</span></span>

<span data-ttu-id="249da-134">キャッシュの空間マッピングの場合、アプリケーションは通常空間マッピング データのスナップショットを取得し、エクスペリエンスの継続時間はこのスナップショットを使用します。</span><span class="sxs-lookup"><span data-stu-id="249da-134">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="249da-135">**利点**</span><span class="sxs-lookup"><span data-stu-id="249da-135">**Benefits**</span></span>
* <span data-ttu-id="249da-136">負荷の減少、システムで、エクスペリエンスが大幅な電力、温度をリードするを実行するいると、cpu のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="249da-136">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="249da-137">空間データの変更が中断されないため、メインのエクスペリエンスの単純な実装です。</span><span class="sxs-lookup"><span data-stu-id="249da-137">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="249da-138">1 つの物理学、グラフィックスおよびその他の目的の空間データの任意の後処理のコストに 1 回です。</span><span class="sxs-lookup"><span data-stu-id="249da-138">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="249da-139">**欠点**</span><span class="sxs-lookup"><span data-stu-id="249da-139">**Drawbacks**</span></span>
* <span data-ttu-id="249da-140">現実世界のオブジェクトまたはユーザーの移動は、キャッシュされたデータでは反映されません。</span><span class="sxs-lookup"><span data-stu-id="249da-140">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="249da-141">例:</span><span class="sxs-lookup"><span data-stu-id="249da-141">E.g.</span></span> <span data-ttu-id="249da-142">今すぐに閉じる実際に、アプリケーションにはドアが開く可能性があります検討します。</span><span class="sxs-lookup"><span data-stu-id="249da-142">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="249da-143">キャッシュされたバージョンのデータを維持するために他のアプリケーションのメモリ。</span><span class="sxs-lookup"><span data-stu-id="249da-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="249da-144">このメソッドの適切なケースでは、制御された環境内や表 top ゲームです。</span><span class="sxs-lookup"><span data-stu-id="249da-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="249da-145">継続的な空間マッピング</span><span class="sxs-lookup"><span data-stu-id="249da-145">Continuous spatial mapping</span></span>

<span data-ttu-id="249da-146">特定のアプリケーションを利用できますで空間マッピング データを更新するスキャンが続行されます。</span><span class="sxs-lookup"><span data-stu-id="249da-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="249da-147">**利点**</span><span class="sxs-lookup"><span data-stu-id="249da-147">**Benefits**</span></span>
* <span data-ttu-id="249da-148">個別スキャンまたは探索エクスペリエンスを費用が不要で、アプリケーションを構築する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="249da-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="249da-149">いくつかの遅延時間では、ゲームで現実世界のオブジェクトの移動を反映できます。</span><span class="sxs-lookup"><span data-stu-id="249da-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="249da-150">**欠点**</span><span class="sxs-lookup"><span data-stu-id="249da-150">**Drawbacks**</span></span>
* <span data-ttu-id="249da-151">メインのエクスペリエンスの実装では複雑さの増加。</span><span class="sxs-lookup"><span data-stu-id="249da-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="249da-152">潜在的なオーバーヘッドのグラフィックや物理学の変化に応じて追加の処理は、これらのシステムによって段階的に取り込まれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="249da-152">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="249da-153">高い能力、温度と CPU への影響。</span><span class="sxs-lookup"><span data-stu-id="249da-153">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="249da-154">このメソッドの適切な場合は 1 つ、床の上のドライブが正しく、ドアが開いているか閉じているかどうかに応じてに遭遇することが holographic 車など、オブジェクトの移動と対話するホログラムが必要な場合です。</span><span class="sxs-lookup"><span data-stu-id="249da-154">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="249da-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="249da-155">See also</span></span>
* [<span data-ttu-id="249da-156">空間マッピングの設計</span><span class="sxs-lookup"><span data-stu-id="249da-156">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="249da-157">座標系</span><span class="sxs-lookup"><span data-stu-id="249da-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="249da-158">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="249da-158">Spatial sound design</span></span>](spatial-sound-design.md)
