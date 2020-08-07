---
title: Unreal でのローカル空間アンカー
description: Unreal で空間アンカーを使用するためのガイド
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, 空間アンカー
ms.openlocfilehash: b102d506b1d670291c3b97ca34d277e2597af043
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376050"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="88313-104">Unreal でのローカル空間アンカー</span><span class="sxs-lookup"><span data-stu-id="88313-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="88313-105">概要</span><span class="sxs-lookup"><span data-stu-id="88313-105">Overview</span></span>

<span data-ttu-id="88313-106">空間アンカーは、アプリケーション セッション間で現実世界の空間にホログラムを保存するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="88313-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="88313-107">これらは、Unreal では **ARPin** として示され、今後のセッションで読み込まれるように HoloLens のアンカー ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="88313-107">These get surfaced through Unreal as **ARPin**s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="88313-108">ローカル アンカーは、インターネット接続がない場合のフォールバックとして理想的です。</span><span class="sxs-lookup"><span data-stu-id="88313-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88313-109">ローカル アンカーはデバイスに格納されますが、Azure 空間アンカーはクラウドに格納されます。</span><span class="sxs-lookup"><span data-stu-id="88313-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="88313-110">アンカーを格納するために Azure クラウド サービスを使用することをご検討の場合は、[Azure Spatial Anchors](unreal-azure-spatial-anchors.md) を統合する方法について説明したドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="88313-110">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="88313-111">また、ローカル アンカーと Azure のアンカーは、競合することなく同じプロジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="88313-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="88313-112">アンカー ストアの確認</span><span class="sxs-lookup"><span data-stu-id="88313-112">Checking the anchor store</span></span>

<span data-ttu-id="88313-113">アンカーを保存または読み込む前に、アンカー ストアの準備ができているかどうか確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88313-113">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="88313-114">アンカー ストアの準備が整う前に、いずれかの HoloLens アンカー関数を呼び出すと、失敗します。</span><span class="sxs-lookup"><span data-stu-id="88313-114">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![空間アンカー ストア準備完了](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="88313-116">アンカーの保存</span><span class="sxs-lookup"><span data-stu-id="88313-116">Saving anchors</span></span>

<span data-ttu-id="88313-117">アプリケーションにコンポーネントがあり、それをワールドに固定する必要がある場合は、次のシーケンスを使用してアンカー ストアに保存できます。</span><span class="sxs-lookup"><span data-stu-id="88313-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![空間アンカーの保存](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="88313-119">次のように分類されます。</span><span class="sxs-lookup"><span data-stu-id="88313-119">Breaking this down:</span></span>
1. <span data-ttu-id="88313-120">既知の場所でアクターを生成します。</span><span class="sxs-lookup"><span data-stu-id="88313-120">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="88313-121">その場所とアクターのクラスに基づく名前を使用して、**ARPin** を作成します。</span><span class="sxs-lookup"><span data-stu-id="88313-121">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="88313-122">アクターを **ARPin** に追加し、そのピンを HoloLens アンカー ストアに保存します。</span><span class="sxs-lookup"><span data-stu-id="88313-122">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="88313-123">選択するアンカー名は一意である必要があります。この例では現在のタイムスタンプを使用します。</span><span class="sxs-lookup"><span data-stu-id="88313-123">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="88313-124">アンカーがアンカー ストアに正常に保存された場合、HoloLens デバイス ポータルの **[システム] > [Map manager]\(マップ マネージャー\) > [Anchor Files Saved On Device]\(デバイスに保存されたアンカー ファイル\)** でそのアンカーを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="88313-124">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="88313-125">アンカーの読み込み</span><span class="sxs-lookup"><span data-stu-id="88313-125">Loading anchors</span></span>

<span data-ttu-id="88313-126">アプリケーションが起動すると、次のブループリントを使用して、コンポーネントをアンカー位置に復元できます。</span><span class="sxs-lookup"><span data-stu-id="88313-126">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![空間アンカーの読み込み](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="88313-128">次のように分類されます。</span><span class="sxs-lookup"><span data-stu-id="88313-128">Breaking this down:</span></span>
1. <span data-ttu-id="88313-129">アンカー ストア内のすべてのアンカーを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="88313-129">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="88313-130">ID でアクターを生成します。</span><span class="sxs-lookup"><span data-stu-id="88313-130">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="88313-131">そのアクターをアンカー ストアから **ARPin** にピン留めします。</span><span class="sxs-lookup"><span data-stu-id="88313-131">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="88313-132">アンカーは、保存された位置に基づいてワールドにホログラムを再配置する必要があるため、ID に対してアクターを生成することが重要です。</span><span class="sxs-lookup"><span data-stu-id="88313-132">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="88313-133">ここで追加した変換によってアンカーにオフセットが追加されます。</span><span class="sxs-lookup"><span data-stu-id="88313-133">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="88313-134">アンカーの保存された名前によって異なるアクターを生成できるように、アンカー ID も照会されます。</span><span class="sxs-lookup"><span data-stu-id="88313-134">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="88313-135">アンカーの削除</span><span class="sxs-lookup"><span data-stu-id="88313-135">Removing anchors</span></span> 

<span data-ttu-id="88313-136">アンカーが終了したら、**Remove ARPin from WMRAnchor Store** および **Remove All ARPins from WMRAnchor Store** コンポーネントを使用して個々のアンカーまたはアンカー ストア全体を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="88313-136">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![空間アンカーの削除](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="88313-138">Spatial Anchors はまだベータ版であるため、最新の情報と機能を確認してください。</span><span class="sxs-lookup"><span data-stu-id="88313-138">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="88313-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="88313-139">See also</span></span>
* [<span data-ttu-id="88313-140">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="88313-140">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="88313-141">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="88313-141">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="88313-142">座標系</span><span class="sxs-lookup"><span data-stu-id="88313-142">Coordinate systems</span></span>](coordinate-systems.md)
