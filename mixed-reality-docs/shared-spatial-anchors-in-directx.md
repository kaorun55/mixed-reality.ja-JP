---
title: DirectX の共有空間アンカー
description: 空間アンカーを共有することで、2つの HoloLens デバイスを同期する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, 同期, 空間アンカー, 転送, マルチプレイヤー, ビュー, シナリオ, チュートリアル, サンプルコード, Azure, Azure 空間アンカー, ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516870"
---
# <a name="shared-experiences-in-directx"></a><span data-ttu-id="10771-104">DirectX での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="10771-104">Shared experiences in DirectX</span></span>

<span data-ttu-id="10771-105">共有エクスペリエンスとは、各ユーザーが独自の HoloLens、iOS、または Android デバイスを持つ複数のユーザーをまとめて表示し、空間内の固定ポイントに配置されている同じホログラムと対話することです。</span><span class="sxs-lookup"><span data-stu-id="10771-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="10771-106">これは、空間アンカーの共有によって実現されます。</span><span class="sxs-lookup"><span data-stu-id="10771-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="10771-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="10771-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="10771-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、持続性のあるクラウドベースの空間アンカーを作成できます。これにより、アプリは複数の HoloLens、IOS、Android デバイスで検索できます。</span><span class="sxs-lookup"><span data-stu-id="10771-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="10771-109">複数のデバイスで共通の空間アンカーを共有することにより、各ユーザーは、同じ物理的な場所でそのアンカーを基準としてレンダリングされたコンテンツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="10771-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="10771-110">これにより、リアルタイム共有エクスペリエンスを実現できます。</span><span class="sxs-lookup"><span data-stu-id="10771-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="10771-111"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して HoloLens、iOS および Android デバイスの間で非同期ホログラム永続化を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="10771-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="10771-112">永続的なクラウド空間アンカーを共有すると、永続化した同じホログラムを長時間にわたって複数のデバイスに表示できます。これらのデバイスが同じ時間と場所に居合わせていなくても問題ありません。</span><span class="sxs-lookup"><span data-stu-id="10771-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="10771-113">HoloLens アプリでの共有エクスペリエンスの構築を開始するには、5分間の<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空間アンカー HoloLens クイックスタート</a>をお試しください。</span><span class="sxs-lookup"><span data-stu-id="10771-113">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="10771-114">Azure 空間アンカーを使用して実行すると、 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens でアンカーを作成して検索</a>できます。</span><span class="sxs-lookup"><span data-stu-id="10771-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="10771-115">チュートリアルは<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android と iOS</a>でも使用できます。これにより、すべてのデバイスで同じアンカーを共有できるようになります。</span><span class="sxs-lookup"><span data-stu-id="10771-115">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="10771-116">ローカルアンカー転送</span><span class="sxs-lookup"><span data-stu-id="10771-116">Local anchor transfers</span></span>

<span data-ttu-id="10771-117">Azure 空間アンカーを使用できない場合、[ローカルアンカー転送](local-anchor-transfers-in-directx.md)では、1つの hololens デバイスが2つ目の hololens デバイスによってインポートされるアンカーをエクスポートできるようにします。</span><span class="sxs-lookup"><span data-stu-id="10771-117">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](local-anchor-transfers-in-directx.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="10771-118">このアプローチでは、Azure 空間アンカーよりも堅牢なアンカーの再呼び出しが可能であり、iOS デバイスと Android デバイスはこの方法ではサポートされていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="10771-118">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="10771-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="10771-119">See also</span></span>
* [<span data-ttu-id="10771-120">複合現実での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="10771-120">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="10771-121"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="10771-121"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="10771-122"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">HoloLens 用 Azure 空間アンカー SDK</a></span><span class="sxs-lookup"><span data-stu-id="10771-122"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK for HoloLens</a></span></span>