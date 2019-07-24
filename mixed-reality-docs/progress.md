---
title: 進行状況の表示
description: プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、コントロール、ui、ux
ms.openlocfilehash: 84853a23a73bbece30c1f96b83e586642f3ab762
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523255"
---
# <a name="displaying-progress"></a><span data-ttu-id="1c041-104">進行状況の表示</span><span class="sxs-lookup"><span data-stu-id="1c041-104">Displaying progress</span></span>

<span data-ttu-id="1c041-105">プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。</span><span class="sxs-lookup"><span data-stu-id="1c041-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="1c041-106">使用されているインジケーターに応じて、進行状況インジケーターが表示されているときはユーザーはアプリを操作できないことを知らせたり、待ち時間の長さを示したりできます。</span><span class="sxs-lookup"><span data-stu-id="1c041-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="1c041-107">![HoloLens での進行状況リングの例](images/HoloLens2_Loader.gif)</span><span class="sxs-lookup"><span data-stu-id="1c041-107">![Progress ring example in HoloLens](images/HoloLens2_Loader.gif)</span></span><br>
<span data-ttu-id="1c041-108">*HoloLens での進行状況リングの例*</span><span class="sxs-lookup"><span data-stu-id="1c041-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="1c041-109">プログレス コントロールの種類</span><span class="sxs-lookup"><span data-stu-id="1c041-109">Types of progress</span></span>

<span data-ttu-id="1c041-110">何が起こっているかについてユーザー情報を提供することが重要です。</span><span class="sxs-lookup"><span data-stu-id="1c041-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="1c041-111">混合環境では、アプリから視覚的なフィードバックが得られない場合、ユーザーは物理環境またはオブジェクトによって簡単に気にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1c041-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="1c041-112">データが読み込まれたりシーンが更新されたりするなど、数秒かかる状況では、視覚的なインジケーターを表示することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1c041-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="1c041-113">操作が進行しているユーザーを表示するには、**進行状況バー**または**進行状況のリング**の2つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="1c041-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="1c041-114">進行状況バー</span><span class="sxs-lookup"><span data-stu-id="1c041-114">Progress bar</span></span>

![HoloLens での進行状況バーの例](images/640px-progressbar.jpg)

<span data-ttu-id="1c041-116">進行状況バーには、タスクの完了率が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c041-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="1c041-117">このメソッドは、期間が既知 (有限) の操作中に使用する必要がありますが、進行中のユーザーとアプリとの対話をブロックすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1c041-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="1c041-118">進行状況リング</span><span class="sxs-lookup"><span data-stu-id="1c041-118">Progress ring</span></span>

![HoloLens での進行状況リングの例](images/640px-progressring.jpg)

<span data-ttu-id="1c041-120">進行状況のリングは不確定な状態であるため、操作が完了するまで他のユーザー操作がブロックされたときに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c041-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="1c041-121">カスタムオブジェクトの進行状況</span><span class="sxs-lookup"><span data-stu-id="1c041-121">Progress with a custom object</span></span>

![HoloLens でのカスタムメッシュの例の進行状況](images/640px-progresscustom.jpg)

<span data-ttu-id="1c041-123">独自のカスタム 2D/3D オブジェクトを使用して進行状況の制御をカスタマイズすることで、アプリの個性とブランド id に追加できます。</span><span class="sxs-lookup"><span data-stu-id="1c041-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="1c041-124">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="1c041-124">Best practices</span></span>
* <span data-ttu-id="1c041-125">ユーザーが簡単にヘッドを空の領域に移動してコンテキストを失うことがあるため、 [billboarding またはタグ](billboarding-and-tag-along.md)を進行状況の表示に密に結合します。</span><span class="sxs-lookup"><span data-stu-id="1c041-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="1c041-126">ユーザーが何も表示できない場合、アプリがクラッシュしたように見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="1c041-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="1c041-127">Billboarding とタグは、進行状況の prefab に組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="1c041-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="1c041-128">ユーザーに対して何が起こっているかに関するステータス情報を常に提供するのが適切です。</span><span class="sxs-lookup"><span data-stu-id="1c041-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="1c041-129">Progress prefab には、状態を提供するための Windows 標準のリングの種類の進行状況など、さまざまな視覚スタイルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1c041-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="1c041-130">また、進行状況のスタイルをアプリのブランドに合わせる必要がある場合は、アニメーションでカスタムメッシュを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1c041-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c041-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c041-131">See also</span></span>
* [<span data-ttu-id="1c041-132">Mixed Reality Toolkit での進行状況スクリプトと prefabs</span><span class="sxs-lookup"><span data-stu-id="1c041-132">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="1c041-133">境界ボックス</span><span class="sxs-lookup"><span data-stu-id="1c041-133">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="1c041-134">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="1c041-134">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="1c041-135">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="1c041-135">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="1c041-136">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="1c041-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
