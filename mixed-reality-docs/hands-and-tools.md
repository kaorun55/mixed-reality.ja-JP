---
title: 手およびモーションのコント ローラー
description: 手およびモーション コント ローラーの相互作用の概要
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: 複合現実、手、アニメーション コント ローラーとの対話の設計します。
ms.openlocfilehash: 4f4231dd816dc71e42d16aca1b518ad03440116e
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629025"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="8b7b4-104">手およびモーションのコント ローラー</span><span class="sxs-lookup"><span data-stu-id="8b7b4-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="8b7b4-105">シナリオ</span><span class="sxs-lookup"><span data-stu-id="8b7b4-105">Scenarios</span></span>
<span data-ttu-id="8b7b4-106">読み取り時にこの対話モデルを採用する場合、[デザイン ガイドライン](interaction-fundamentals.md)、holographic の世界とのやり取りに 2 つの手を使用するユーザーを必要とするアプリケーションを開発していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="8b7b4-107">アプリケーションが仮想および物理の間の境界の削除の目標を達成しようとしています。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="8b7b4-108">特定のシナリオは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="8b7b4-109">情報ワーカーの 2D 仮想画面と Ui を表示および内容の制御を提供します。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="8b7b4-110">最初の行のワーカーのチュートリアルと factory の組み立てラインのガイドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="8b7b4-111">支援と医療専門家の指導の本格的なツールの開発</span><span class="sxs-lookup"><span data-stu-id="8b7b4-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="8b7b4-112">仮想の 3D オブジェクトを使用して現実の世界を修飾する、または 2 つ目の世界を作成するには</span><span class="sxs-lookup"><span data-stu-id="8b7b4-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="8b7b4-113">サービスと現実の世界を背景としてを使用してゲームに基づく場所を作成します。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="8b7b4-114">手およびモーション コント ローラーのモダリティ</span><span class="sxs-lookup"><span data-stu-id="8b7b4-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="8b7b4-115">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="8b7b4-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="8b7b4-116">これは、ユーザーが手を加えることと、ホログラムを直接操作できる、手の機能を活用モダリティです。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="8b7b4-117">Leaveraging 日常業務のエクスペリエンスし、適切な visual アフォーを提供するには、ユーザーは仮想のものと対話する実際のオブジェクトを操作するための同じ方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world obejcts to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="8b7b4-118">ポイントとの手でコミット</span><span class="sxs-lookup"><span data-stu-id="8b7b4-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="8b7b4-119">このモードでは、距離でホログラムと対話するユーザーを支援します。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="8b7b4-120">環境を最大限に利用できます。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="8b7b4-121">ユーザーは、ホログラムを任意の場所に配置でき、それらの距離からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="8b7b4-122">メンタル モデルおよびジェスチャを制御すると、2 D および 3D ホログラムの操作が高と同期の直接操作します。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="8b7b4-123">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="8b7b4-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="8b7b4-124">アニメーション コント ローラーは、手の 1 つまたは両方を使用しているときに、大規模な距離の範囲にわたって正確な相互作用を提供することで、ユーザーの物理的な機能を拡張するツールです。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="8b7b4-125">これらのハードウェア製品では、さまざまな操作の多く一般的に使用されるの相互作用し、surefooted、触るフィードバックへのショートカットを提供します。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="8b7b4-126">現時点では、モーションのコント ローラーでは、のみ WMR シナリオの使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b7b4-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="8b7b4-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b7b4-127">See also</span></span>
* [<span data-ttu-id="8b7b4-128">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="8b7b4-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="8b7b4-129">(近くに手の形の相互作用) を直接操作</span><span class="sxs-lookup"><span data-stu-id="8b7b4-129">Direct manipulation (Near hand interaction)</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8b7b4-130">ポイントとコミット (Far 手の形の相互作用)</span><span class="sxs-lookup"><span data-stu-id="8b7b4-130">Point and commit (Far hand interaction)</span></span>](point-and-commit.md)
* [<span data-ttu-id="8b7b4-131">ハンズフリー</span><span class="sxs-lookup"><span data-stu-id="8b7b4-131">Hands-free</span></span>](hands-free.md)
* [<span data-ttu-id="8b7b4-132">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="8b7b4-132">Gaze and dwell</span></span>](gaze-targeting.md)
