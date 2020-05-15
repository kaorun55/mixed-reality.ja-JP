---
title: Unreal での空間アンカー
description: Unreal で空間アンカーを使用するためのガイド
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, 空間アンカー
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840141"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="21ca9-104">Unreal での空間アンカー</span><span class="sxs-lookup"><span data-stu-id="21ca9-104">Spatial Anchors in Unreal</span></span>

<span data-ttu-id="21ca9-105">空間アンカーは、アプリケーション セッション間で現実世界の空間にホログラムを保持するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="21ca9-105">Spatial anchors are used to persist holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="21ca9-106">これは、Unreal では ARPin として示され、今後のセッションで読み込まれるように HoloLens のアンカー ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="21ca9-106">This gets surfaced through Unreal as ARPins and gets saved in the HoloLens’ anchor store to be loaded in future sessions.</span></span> 

<span data-ttu-id="21ca9-107">アンカーを保存または読み込む前に、まずアンカー ストアの準備ができていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="21ca9-107">Before saving or loading anchors, first check that the anchor store is ready.</span></span>  <span data-ttu-id="21ca9-108">アンカー ストアの準備が整う前に、いずれかの HoloLens アンカー関数を呼び出そうとすると、失敗します。</span><span class="sxs-lookup"><span data-stu-id="21ca9-108">Attempting to call any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![空間アンカー ストア準備完了](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a><span data-ttu-id="21ca9-110">アンカーの保存</span><span class="sxs-lookup"><span data-stu-id="21ca9-110">Save Anchors</span></span>

<span data-ttu-id="21ca9-111">アプリケーションにコンポーネントがあり、それをワールドに固定する必要がある場合は、次のシーケンスを使用してアンカー ストアに保存できます。</span><span class="sxs-lookup"><span data-stu-id="21ca9-111">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![空間アンカーの保存](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="21ca9-113">ここでは、既知の位置にアクターを生成し、ARPin を (その位置と、アクターのクラスに基づいた名前を使用して) 作成します。そのアクターを ARPin に追加し、ピンを HoloLens アンカー ストアに保存します。</span><span class="sxs-lookup"><span data-stu-id="21ca9-113">Here, we are spawning an actor at a known location, creating an ARPin with that location and a name based on the actor’s class, adding the actor to the ARPin, and saving the pin to the HoloLens anchor store.</span></span>  <span data-ttu-id="21ca9-114">選択するアンカー名は一意である必要があるため、この例では現在のタイムスタンプを追加します。</span><span class="sxs-lookup"><span data-stu-id="21ca9-114">The anchor name we choose must be unique, so in this example we append the current timestamp.</span></span>  <span data-ttu-id="21ca9-115">アンカーがアンカー ストアに正常に保存された場合、HoloLens デバイス ポータルの [システム] > [Map manager]\(マップ マネージャー\) > [Anchor Files Saved On Device]\(デバイスに保存されたアンカー ファイル\) でそのアンカーを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="21ca9-115">If the anchor successfully saves to the anchor store, it can be inspected in the HoloLens device portal under System > Map manager > Anchor Files Saved On Device.</span></span> 

## <a name="load-anchors"></a><span data-ttu-id="21ca9-116">アンカーの読み込み</span><span class="sxs-lookup"><span data-stu-id="21ca9-116">Load Anchors</span></span>

<span data-ttu-id="21ca9-117">アプリケーションが起動すると、次のブループリントを呼び出して、コンポーネントをアンカー位置に復元できます。</span><span class="sxs-lookup"><span data-stu-id="21ca9-117">When an application starts, the following blueprint can be called to restore components to their anchor locations:</span></span>

![空間アンカーの読み込み](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="21ca9-119">この例では、アンカー ストア内のすべてのアンカーを反復処理し、ID に対してアクターを生成し、そのアクターをアンカー ストアから ARPin にピン留めします。</span><span class="sxs-lookup"><span data-stu-id="21ca9-119">In this example, we iterate over all of the anchors in the anchor store, spawn an actor at identity, and pin that actor to the ARPin from the anchor store.</span></span>  <span data-ttu-id="21ca9-120">アンカーは、保存された位置に基づいてワールドにホログラムを再配置する必要があるため、ID に対してアクターを生成することが重要です。そのため、ここで追加した変換によってアンカーにオフセットが追加されます。</span><span class="sxs-lookup"><span data-stu-id="21ca9-120">It is important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved, so any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="21ca9-121">アンカーの保存された名前によって異なるアクターを生成できるように、アンカー ID も照会されます。</span><span class="sxs-lookup"><span data-stu-id="21ca9-121">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="remove-anchors"></a><span data-ttu-id="21ca9-122">アンカーの削除</span><span class="sxs-lookup"><span data-stu-id="21ca9-122">Remove Anchors</span></span> 

<span data-ttu-id="21ca9-123">アンカーを使い終わったら、アンカー ストア全体をクリアするか、アンカー ストアから個々のアンカーを削除して、後続のセッションに含まれないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="21ca9-123">When done with an anchor, the entire anchor store can be cleared, or individual anchors can be removed from the anchor store so they are not included in future sessions:</span></span> 

![空間アンカーの削除](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a><span data-ttu-id="21ca9-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="21ca9-125">See also</span></span>
* [<span data-ttu-id="21ca9-126">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="21ca9-126">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="21ca9-127">座標系</span><span class="sxs-lookup"><span data-stu-id="21ca9-127">Coordinate systems</span></span>](coordinate-systems.md)
