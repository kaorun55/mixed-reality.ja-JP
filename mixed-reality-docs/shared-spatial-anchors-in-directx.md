---
title: DirectX のアンカー空間の共有
description: 空間のアンカーを共有することで 2 つの HoloLens デバイスを同期する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、同期、空間アンカー、転送、マルチ プレーヤー、ビュー、シナリオ、チュートリアル、サンプル コード、Azure、Azure の空間アンカー、ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605061"
---
# <a name="shared-experiences-in-directx"></a><span data-ttu-id="97bc6-104">DirectX での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="97bc6-104">Shared experiences in DirectX</span></span>

<span data-ttu-id="97bc6-105">共有エクスペリエンスは、複数のユーザーがそれぞれに独自の HoloLens、iOS または Android デバイスで、まとめて表示および対話が空間の固定位置に配置されている同じホログラムです。</span><span class="sxs-lookup"><span data-stu-id="97bc6-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="97bc6-106">これは、空間アンカーを共有することによって実現されます。</span><span class="sxs-lookup"><span data-stu-id="97bc6-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="97bc6-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="97bc6-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="97bc6-108">使用することができます<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>アンカーを作成する永続的なクラウド バックアップ空間、アプリが複数の HoloLens、iOS や Android デバイスで見つけることができますし、これです。</span><span class="sxs-lookup"><span data-stu-id="97bc6-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="97bc6-109">各ユーザーは複数のデバイスで共通の空間アンカーを共有することで、同じ物理的な場所でそのアンカーの基準としたコンテンツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="97bc6-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="97bc6-110">これにより、リアルタイムのエクスペリエンスを共有します。</span><span class="sxs-lookup"><span data-stu-id="97bc6-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="97bc6-111">使用することも<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a> HoloLens、iOS および Android デバイスの間で非同期ホログラム永続化します。</span><span class="sxs-lookup"><span data-stu-id="97bc6-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="97bc6-112">持続性のあるクラウド空間アンカーを共有することで複数のデバイスはこれらのデバイスがまとめてと同時に存在しない場合でも、時間の経過と共に同じ永続化されたホログラムを確認できます。</span><span class="sxs-lookup"><span data-stu-id="97bc6-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="97bc6-113">5 分間試して、HoloLens のアプリで共有のエクスペリエンスの構築を開始する、<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">空間アンカー HoloLens の Azure クイック スタート</a>します。</span><span class="sxs-lookup"><span data-stu-id="97bc6-113">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="97bc6-114">空間のアンカーを Azure で稼働しているを開発したとして、<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">を作成し、HoloLens でアンカーを見つける</a>します。</span><span class="sxs-lookup"><span data-stu-id="97bc6-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="97bc6-115">チュートリアルに利用<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android および iOS</a>同様に、すべてのデバイスで同じアンカーを共有できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="97bc6-115">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="97bc6-116">ローカルのアンカーの転送</span><span class="sxs-lookup"><span data-stu-id="97bc6-116">Local anchor transfers</span></span>

<span data-ttu-id="97bc6-117">Azure の空間アンカーを使用することはできませんの状況で[ローカル アンカー転送](local-anchor-transfers-in-directx.md)2 番目の HoloLens デバイスによってインポートされるアンカーをエクスポートする 1 つの HoloLens デバイスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="97bc6-117">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](local-anchor-transfers-in-directx.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="97bc6-118">このアプローチは、Azure の空間アンカーよりも堅牢性のアンカー再現率を提供し、iOS および Android デバイスは、このアプローチではサポートされていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="97bc6-118">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="97bc6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="97bc6-119">See also</span></span>
* [<span data-ttu-id="97bc6-120">複合現実での経験を共有</span><span class="sxs-lookup"><span data-stu-id="97bc6-120">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="97bc6-121"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure の空間アンカー</a></span><span class="sxs-lookup"><span data-stu-id="97bc6-121"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="97bc6-122"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure 空間アンカー HoloLens の SDK</a></span><span class="sxs-lookup"><span data-stu-id="97bc6-122"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK for HoloLens</a></span></span>