---
title: Unreal での空間アンカー
description: Unreal で空間アンカーを使用するためのガイド
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, 空間アンカー
ms.openlocfilehash: 58394f4e27aff5070d55ed5f0d62cd81ff579d1f
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720318"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="9380e-104">Unreal での空間アンカー</span><span class="sxs-lookup"><span data-stu-id="9380e-104">Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="9380e-105">概要</span><span class="sxs-lookup"><span data-stu-id="9380e-105">Overview</span></span>

<span data-ttu-id="9380e-106">空間アンカーは、アプリケーション セッション間で現実世界の空間にホログラムを保存するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9380e-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="9380e-107">これらは、Unreal では **ARPin** として示され、今後のセッションで読み込まれるように HoloLens のアンカー ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="9380e-107">These get surfaced through Unreal as **ARPin**s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> 

## <a name="checking-the-anchor-store"></a><span data-ttu-id="9380e-108">アンカー ストアの確認</span><span class="sxs-lookup"><span data-stu-id="9380e-108">Checking the anchor store</span></span>

<span data-ttu-id="9380e-109">アンカーを保存または読み込む前に、アンカー ストアの準備ができているかどうか確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9380e-109">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="9380e-110">アンカー ストアの準備が整う前に、いずれかの HoloLens アンカー関数を呼び出すと、失敗します。</span><span class="sxs-lookup"><span data-stu-id="9380e-110">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![空間アンカー ストア準備完了](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="9380e-112">アンカーの保存</span><span class="sxs-lookup"><span data-stu-id="9380e-112">Saving anchors</span></span>

<span data-ttu-id="9380e-113">アプリケーションにコンポーネントがあり、それをワールドに固定する必要がある場合は、次のシーケンスを使用してアンカー ストアに保存できます。</span><span class="sxs-lookup"><span data-stu-id="9380e-113">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![空間アンカーの保存](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="9380e-115">次のように分類されます。</span><span class="sxs-lookup"><span data-stu-id="9380e-115">Breaking this down:</span></span>
1. <span data-ttu-id="9380e-116">既知の場所でアクターを生成します。</span><span class="sxs-lookup"><span data-stu-id="9380e-116">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="9380e-117">その場所とアクターのクラスに基づく名前を使用して、**ARPin** を作成します。</span><span class="sxs-lookup"><span data-stu-id="9380e-117">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="9380e-118">アクターを **ARPin** に追加し、そのピンを HoloLens アンカー ストアに保存します。</span><span class="sxs-lookup"><span data-stu-id="9380e-118">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="9380e-119">選択するアンカー名は一意である必要があります。この例では現在のタイムスタンプを使用します。</span><span class="sxs-lookup"><span data-stu-id="9380e-119">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="9380e-120">アンカーがアンカー ストアに正常に保存された場合、HoloLens デバイス ポータルの **[システム] > [Map manager]\(マップ マネージャー\) > [Anchor Files Saved On Device]\(デバイスに保存されたアンカー ファイル\)** でそのアンカーを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="9380e-120">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="9380e-121">アンカーの読み込み</span><span class="sxs-lookup"><span data-stu-id="9380e-121">Loading anchors</span></span>

<span data-ttu-id="9380e-122">アプリケーションが起動すると、次のブループリントを使用して、コンポーネントをアンカー位置に復元できます。</span><span class="sxs-lookup"><span data-stu-id="9380e-122">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![空間アンカーの読み込み](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="9380e-124">次のように分類されます。</span><span class="sxs-lookup"><span data-stu-id="9380e-124">Breaking this down:</span></span>
1. <span data-ttu-id="9380e-125">アンカー ストア内のすべてのアンカーを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="9380e-125">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="9380e-126">ID でアクターを生成します。</span><span class="sxs-lookup"><span data-stu-id="9380e-126">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="9380e-127">そのアクターをアンカー ストアから **ARPin** にピン留めします。</span><span class="sxs-lookup"><span data-stu-id="9380e-127">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="9380e-128">アンカーは、保存された位置に基づいてワールドにホログラムを再配置する必要があるため、ID に対してアクターを生成することが重要です。</span><span class="sxs-lookup"><span data-stu-id="9380e-128">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="9380e-129">ここで追加した変換によってアンカーにオフセットが追加されます。</span><span class="sxs-lookup"><span data-stu-id="9380e-129">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="9380e-130">アンカーの保存された名前によって異なるアクターを生成できるように、アンカー ID も照会されます。</span><span class="sxs-lookup"><span data-stu-id="9380e-130">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="9380e-131">アンカーの削除</span><span class="sxs-lookup"><span data-stu-id="9380e-131">Removing anchors</span></span> 

<span data-ttu-id="9380e-132">アンカーが終了したら、**Remove ARPin from WMRAnchor Store** および **Remove All ARPins from WMRAnchor Store** コンポーネントを使用して個々のアンカーまたはアンカー ストア全体を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="9380e-132">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![空間アンカーの削除](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="9380e-134">Spatial Anchors はまだベータ版であるため、最新の情報と機能を確認してください。</span><span class="sxs-lookup"><span data-stu-id="9380e-134">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="9380e-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="9380e-135">See also</span></span>
* [<span data-ttu-id="9380e-136">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="9380e-136">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="9380e-137">座標系</span><span class="sxs-lookup"><span data-stu-id="9380e-137">Coordinate systems</span></span>](coordinate-systems.md)
