---
title: Unity での共有エクスペリエンス
description: Unity アプリケーションで複数のユーザーの間で同じホログラムを共有します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共有、アンカー、WorldAnchor、MR WorldAnchorTransferBatch、SpatialPerception、Azure、Azure の空間アンカー、ASA は 250 の共有
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605071"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="c0198-104">Unity での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="c0198-104">Shared experiences in Unity</span></span>

<span data-ttu-id="c0198-105">共有エクスペリエンスは、複数のユーザーがそれぞれに独自の HoloLens、iOS または Android デバイスで、まとめて表示および対話が空間の固定位置に配置されている同じホログラムです。</span><span class="sxs-lookup"><span data-stu-id="c0198-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="c0198-106">これは、空間アンカーを共有することによって実現されます。</span><span class="sxs-lookup"><span data-stu-id="c0198-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="c0198-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c0198-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="c0198-108">使用することができます<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>アンカーを作成する永続的なクラウド バックアップ空間、アプリが複数の HoloLens、iOS や Android デバイスで見つけることができますし、これです。</span><span class="sxs-lookup"><span data-stu-id="c0198-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="c0198-109">各ユーザーは複数のデバイスで共通の空間アンカーを共有することで、同じ物理的な場所でそのアンカーの基準としたコンテンツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="c0198-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="c0198-110">これにより、リアルタイムのエクスペリエンスを共有します。</span><span class="sxs-lookup"><span data-stu-id="c0198-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="c0198-111">使用することも<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a> HoloLens、iOS および Android デバイスの間で非同期ホログラム永続化します。</span><span class="sxs-lookup"><span data-stu-id="c0198-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="c0198-112">持続性のあるクラウド空間アンカーを共有することで複数のデバイスはこれらのデバイスがまとめてと同時に存在しない場合でも、時間の経過と共に同じ永続化されたホログラムを確認できます。</span><span class="sxs-lookup"><span data-stu-id="c0198-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="c0198-113">5 分間試して、Unity での共有エクスペリエンスの構築を開始、<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">空間アンカー Unity の Azure クイック スタート</a>します。</span><span class="sxs-lookup"><span data-stu-id="c0198-113">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="c0198-114">空間のアンカーを Azure で稼働しているを開発したとして、<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">を作成し、Unity 内でアンカーを検索</a>します。</span><span class="sxs-lookup"><span data-stu-id="c0198-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="c0198-115">ローカルのアンカーの転送</span><span class="sxs-lookup"><span data-stu-id="c0198-115">Local anchor transfers</span></span>

<span data-ttu-id="c0198-116">Azure の空間アンカーを使用することはできませんの状況で[ローカル アンカー転送](local-anchor-transfers-in-unity.md)2 番目の HoloLens デバイスによってインポートされるアンカーをエクスポートする 1 つの HoloLens デバイスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c0198-116">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="c0198-117">このアプローチは、Azure の空間アンカーよりも堅牢性のアンカー再現率を提供し、iOS および Android デバイスは、このアプローチではサポートされていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c0198-117">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0198-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0198-118">See also</span></span>
* [<span data-ttu-id="c0198-119">複合現実での経験を共有</span><span class="sxs-lookup"><span data-stu-id="c0198-119">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="c0198-120"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure の空間アンカー</a></span><span class="sxs-lookup"><span data-stu-id="c0198-120"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="c0198-121"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー Unity 用の SDK</a></span><span class="sxs-lookup"><span data-stu-id="c0198-121"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>