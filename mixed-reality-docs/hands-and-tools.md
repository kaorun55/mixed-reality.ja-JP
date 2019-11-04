---
title: ハンドコントローラーとモーションコントローラー
description: ハンドアンドモーションコントローラーの相互作用の概要
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 混合現実、ハンド、モーションコントローラー、相互作用、設計
ms.openlocfilehash: 395862fe987244e2af70bb6794caa91e243cd076
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435153"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="a7a9e-104">ハンドコントローラーとモーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="a7a9e-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="a7a9e-105">シナリオ</span><span class="sxs-lookup"><span data-stu-id="a7a9e-105">Scenarios</span></span>
<span data-ttu-id="a7a9e-106">[相互作用の概要](interaction-fundamentals.md)を読み取った後にこの相互作用モデルを採用することを選択した場合は、ユーザーが holographic 世界と対話するために2人のユーザーを使用する必要があるアプリケーションを開発していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="a7a9e-106">If you choose to adopt this interaction model after reading the [interaction overview](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="a7a9e-107">アプリケーションは、仮想と物理の間の境界を削除するという目標を達成します。</span><span class="sxs-lookup"><span data-stu-id="a7a9e-107">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="a7a9e-108">次のようなシナリオが考えられます。</span><span class="sxs-lookup"><span data-stu-id="a7a9e-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="a7a9e-109">UI affordances を使用してインフォメーションワーカーの2D 仮想スクリーンを提供し、コンテンツの表示と制御を行う</span><span class="sxs-lookup"><span data-stu-id="a7a9e-109">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="a7a9e-110">ファクトリアセンブリラインのためのファーストラインワーカーのチュートリアルとガイドの提供</span><span class="sxs-lookup"><span data-stu-id="a7a9e-110">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="a7a9e-111">医療プロフェッショナルを支援および教育するためのプロフェッショナルなツールの開発</span><span class="sxs-lookup"><span data-stu-id="a7a9e-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="a7a9e-112">3D 仮想オブジェクトを使用して実際の世界を装飾する、または第2の世界を作成する</span><span class="sxs-lookup"><span data-stu-id="a7a9e-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="a7a9e-113">現実世界を背景とした場所ベースのサービスとゲームの作成</span><span class="sxs-lookup"><span data-stu-id="a7a9e-113">Creating location based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="a7a9e-114">ハンドアンドモーションコントローラー感覚様相</span><span class="sxs-lookup"><span data-stu-id="a7a9e-114">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="a7a9e-115">[ハンドを使用した ![直接操作](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="a7a9e-115">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsdirect-manipulationmdbr"></a>[<span data-ttu-id="a7a9e-116">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="a7a9e-116">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="a7a9e-117">これは、ユーザーがホログラムを直接操作したり操作したりできるようにするための、手の力を活用したモダリティです。</span><span class="sxs-lookup"><span data-stu-id="a7a9e-117">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="a7a9e-118">日常的な経験を活用し、適切な視覚的 affordances を提供することにより、ユーザーは、実際のオブジェクトを操作するのと同じ方法を使用して仮想マシンとやり取りすることができます。</span><span class="sxs-lookup"><span data-stu-id="a7a9e-118">By leveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a7a9e-119">[![ポイントし、ハンドでコミットする](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="a7a9e-119">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handspoint-and-commitmdbr"></a>[<span data-ttu-id="a7a9e-120">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="a7a9e-120">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="a7a9e-121">このモダリティによって、ユーザーは距離内でホログラムを操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a7a9e-121">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="a7a9e-122">これにより、ユーザーは周囲を最大限に活用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a7a9e-122">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="a7a9e-123">ユーザーは、ホログラムをどこにでも配置でき、任意の距離からそれらにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a7a9e-123">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="a7a9e-124">2D および3D ホログラムの制御と操作を行うためのメンタルモデルとジェスチャは、直接操作のものと非常に同期されています。</span><span class="sxs-lookup"><span data-stu-id="a7a9e-124">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a7a9e-125">[![モーションコントローラー](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="a7a9e-125">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersmotion-controllersmdbr"></a>[<span data-ttu-id="a7a9e-126">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="a7a9e-126">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="a7a9e-127">モーションコントローラーは、ユーザーの物理的な機能を拡張するツールであり、1つまたは両方のハンズを使用しながら、広範囲の距離にわたる正確な対話を実現します。</span><span class="sxs-lookup"><span data-stu-id="a7a9e-127">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="a7a9e-128">これらのハードウェアアクセサリは、一般的に使用される多くの対話にショートカットを提供し、さまざまなアクションに対して tactile のフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="a7a9e-128">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="a7a9e-129">現在、モーションコントローラーは、Windows Mixed Reality (WMR) シナリオでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7a9e-129">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="a7a9e-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7a9e-130">See also</span></span>
* [<span data-ttu-id="a7a9e-131">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="a7a9e-131">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="a7a9e-132">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="a7a9e-132">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="a7a9e-133">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="a7a9e-133">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a7a9e-134">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="a7a9e-134">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="a7a9e-135">ハンズフリー</span><span class="sxs-lookup"><span data-stu-id="a7a9e-135">Hands-free</span></span>](hands-free.md)
