---
title: ハンドコントローラーとモーションコントローラー
description: ハンドアンドモーションコントローラーの相互作用の概要
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Mixed Reality、ハンズオン、motion コントローラー、対話、設計
ms.openlocfilehash: b6efb0a9651cad8eee9b80bb130aa1a85b9a9941
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507868"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="e7bd0-104">ハンドコントローラーとモーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="e7bd0-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="e7bd0-105">シナリオ</span><span class="sxs-lookup"><span data-stu-id="e7bd0-105">Scenarios</span></span>
<span data-ttu-id="e7bd0-106">[デザインガイドライン](interaction-fundamentals.md)を読み込んだ後にこの対話モデルを採用する場合は、ユーザーが holographic 世界と対話するために2人のユーザーを使用する必要があるアプリケーションを開発していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e7bd0-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="e7bd0-107">アプリケーションは、仮想と物理の間で boundry を削除するという目標を達成します。</span><span class="sxs-lookup"><span data-stu-id="e7bd0-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="e7bd0-108">次のようなシナリオが考えられます。</span><span class="sxs-lookup"><span data-stu-id="e7bd0-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="e7bd0-109">インフォメーションワーカーの2D バーチャル画面と Ui を提供してコンテンツを表示および制御する</span><span class="sxs-lookup"><span data-stu-id="e7bd0-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="e7bd0-110">工場出荷時の組み立てラインでのファーストラインワーカーのチュートリアルとガイドの提供</span><span class="sxs-lookup"><span data-stu-id="e7bd0-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="e7bd0-111">医療プロフェッショナルを支援および教育するためのプロフェッショナルなツールの開発</span><span class="sxs-lookup"><span data-stu-id="e7bd0-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="e7bd0-112">3D 仮想オブジェクトを使用して実際の世界を装飾する、または第2の世界を作成する</span><span class="sxs-lookup"><span data-stu-id="e7bd0-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="e7bd0-113">リアルワールドを背景として使用した場所ベースのサービスとゲームの作成</span><span class="sxs-lookup"><span data-stu-id="e7bd0-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="e7bd0-114">ハンドアンドモーションコントローラー感覚様相</span><span class="sxs-lookup"><span data-stu-id="e7bd0-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="e7bd0-115">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="e7bd0-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="e7bd0-116">これは、ユーザーがホログラムを直接操作したり操作したりできるようにするための、手の力を活用したモダリティです。</span><span class="sxs-lookup"><span data-stu-id="e7bd0-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="e7bd0-117">1日の有効期間を最小にして、適切な視覚的 affordances を提供することで、ユーザーは、実際のオブジェクトを操作するのと同じ方法を使用して仮想マシンとやり取りすることができます。</span><span class="sxs-lookup"><span data-stu-id="e7bd0-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="e7bd0-118">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="e7bd0-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="e7bd0-119">このモダリティによって、ユーザーは距離内でホログラムを操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e7bd0-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="e7bd0-120">これにより、ユーザーは周囲を最大限に活用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e7bd0-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="e7bd0-121">ユーザーは、ホログラムをどこにでも配置でき、任意の距離からそれらにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e7bd0-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="e7bd0-122">2D および3D ホログラムの制御と操作を行うためのメンタルモデルとジェスチャは、直接操作のものと非常に同期されています。</span><span class="sxs-lookup"><span data-stu-id="e7bd0-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="e7bd0-123">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="e7bd0-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="e7bd0-124">モーションコントローラーは、ユーザーの物理的な機能を拡張するツールであり、1つまたは両方のハンズを使用しながら、広範囲の距離にわたる正確な対話を実現します。</span><span class="sxs-lookup"><span data-stu-id="e7bd0-124">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="e7bd0-125">これらのハードウェアアクセサリは、一般的に使用される多くの対話にショートカットを提供し、さまざまなアクションに対して tactile のフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="e7bd0-125">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="e7bd0-126">現在、モーションコントローラーは、Windows Mixed Reality (WMR) シナリオでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e7bd0-126">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 

![ハンドコントローラーとモーションコントローラーの比較感覚様相](images/Hands-and-controllers-720px.jpg)<br>

<span data-ttu-id="e7bd0-128">*ハンドコントローラーとモーションコントローラーの比較感覚様相*</span><span class="sxs-lookup"><span data-stu-id="e7bd0-128">*Comparison of hands and motion controllers modalities*</span></span>

## <a name="see-also"></a><span data-ttu-id="e7bd0-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7bd0-129">See also</span></span>
* [<span data-ttu-id="e7bd0-130">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="e7bd0-130">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e7bd0-131">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="e7bd0-131">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="e7bd0-132">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="e7bd0-132">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e7bd0-133">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="e7bd0-133">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="e7bd0-134">ハンズフリー</span><span class="sxs-lookup"><span data-stu-id="e7bd0-134">Hands-free</span></span>](hands-free.md)
