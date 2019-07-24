---
title: Unity での共有エクスペリエンス
description: Unity アプリケーションの複数のユーザー間で同じホログラムを共有します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共有、アンカー、WorldAnchor、MR 共有250、WorldAnchorTransferBatch、SpatialPerception、Azure、Azure 空間アンカー、ASA
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516794"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="c88af-104">Unity での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="c88af-104">Shared experiences in Unity</span></span>

<span data-ttu-id="c88af-105">共有エクスペリエンスとは、各ユーザーが独自の HoloLens、iOS、または Android デバイスを持つ複数のユーザーをまとめて表示し、空間内の固定ポイントに配置されている同じホログラムと対話することです。</span><span class="sxs-lookup"><span data-stu-id="c88af-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="c88af-106">これは、空間アンカーの共有によって実現されます。</span><span class="sxs-lookup"><span data-stu-id="c88af-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="c88af-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c88af-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="c88af-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、持続性のあるクラウドベースの空間アンカーを作成できます。これにより、アプリは複数の HoloLens、IOS、Android デバイスで検索できます。</span><span class="sxs-lookup"><span data-stu-id="c88af-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="c88af-109">複数のデバイスで共通の空間アンカーを共有することにより、各ユーザーは、同じ物理的な場所でそのアンカーを基準としてレンダリングされたコンテンツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="c88af-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="c88af-110">これにより、リアルタイム共有エクスペリエンスを実現できます。</span><span class="sxs-lookup"><span data-stu-id="c88af-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="c88af-111"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して HoloLens、iOS および Android デバイスの間で非同期ホログラム永続化を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="c88af-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="c88af-112">永続的なクラウド空間アンカーを共有すると、永続化した同じホログラムを長時間にわたって複数のデバイスに表示できます。これらのデバイスが同じ時間と場所に居合わせていなくても問題ありません。</span><span class="sxs-lookup"><span data-stu-id="c88af-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="c88af-113">Unity で共有エクスペリエンスの構築を開始するには、5分間の<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間アンカー unity クイックスタート</a>をお試しください。</span><span class="sxs-lookup"><span data-stu-id="c88af-113">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="c88af-114">Azure 空間アンカーを使用して実行した後は、 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity でアンカーを作成して見つける</a>ことができます。</span><span class="sxs-lookup"><span data-stu-id="c88af-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="c88af-115">ローカルアンカー転送</span><span class="sxs-lookup"><span data-stu-id="c88af-115">Local anchor transfers</span></span>

<span data-ttu-id="c88af-116">Azure 空間アンカーを使用できない場合、[ローカルアンカー転送](local-anchor-transfers-in-unity.md)では、1つの hololens デバイスが2つ目の hololens デバイスによってインポートされるアンカーをエクスポートできるようにします。</span><span class="sxs-lookup"><span data-stu-id="c88af-116">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="c88af-117">このアプローチでは、Azure 空間アンカーよりも堅牢なアンカーの再呼び出しが可能であり、iOS デバイスと Android デバイスはこの方法ではサポートされていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c88af-117">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="c88af-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c88af-118">See also</span></span>
* [<span data-ttu-id="c88af-119">複合現実での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="c88af-119">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="c88af-120"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="c88af-120"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="c88af-121"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー SDK for Unity</a></span><span class="sxs-lookup"><span data-stu-id="c88af-121"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>