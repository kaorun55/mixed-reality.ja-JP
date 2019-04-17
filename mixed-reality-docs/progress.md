---
title: 進行状況の表示
description: プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、コントロール、ui、ux
ms.openlocfilehash: 9edddc7800f0d7334d1ceba97b9a06fd6d4580ac
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603213"
---
# <a name="displaying-progress"></a><span data-ttu-id="56471-104">進行状況の表示</span><span class="sxs-lookup"><span data-stu-id="56471-104">Displaying progress</span></span>

<span data-ttu-id="56471-105">プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。</span><span class="sxs-lookup"><span data-stu-id="56471-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="56471-106">使用されているインジケーターに応じて、進行状況インジケーターが表示されているときはユーザーはアプリを操作できないことを知らせたり、待ち時間の長さを示したりできます。</span><span class="sxs-lookup"><span data-stu-id="56471-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="56471-107">![HoloLens の進行状況リングの例](images/640px-progress-hero.jpg)</span><span class="sxs-lookup"><span data-stu-id="56471-107">![Progress ring example in HoloLens](images/640px-progress-hero.jpg)</span></span><br>
<span data-ttu-id="56471-108">*HoloLens の進行状況リングの例*</span><span class="sxs-lookup"><span data-stu-id="56471-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="56471-109">プログレス コントロールの種類</span><span class="sxs-lookup"><span data-stu-id="56471-109">Types of progress</span></span>

<span data-ttu-id="56471-110">ユーザーが何が起こっているかに関する情報を提供する重要です。</span><span class="sxs-lookup"><span data-stu-id="56471-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="56471-111">複合現実でユーザーことができますが簡単に気を取られる物理環境またはオブジェクトの場合、アプリはありませんで適切な視覚的なフィードバック。</span><span class="sxs-lookup"><span data-stu-id="56471-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="56471-112">数秒かかる場合、データの読み込み時にこのようなまたはシーンを更新、視覚インジケータを表示することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="56471-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="56471-113">操作が進行中 – ですが、ユーザーを表示する 2 つのオプションがあります、**進行状況バー**または**進行状況リング**します。</span><span class="sxs-lookup"><span data-stu-id="56471-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="56471-114">進行状況バー</span><span class="sxs-lookup"><span data-stu-id="56471-114">Progress bar</span></span>

![HoloLens で進行状況バーの例](images/640px-progressbar.jpg)

<span data-ttu-id="56471-116">進行状況バーは、タスクの完了率を示しています。</span><span class="sxs-lookup"><span data-stu-id="56471-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="56471-117">ある期間がわかっている (不確定)、操作中にために使用する必要がありますが、進行状況は、アプリでのユーザーの操作をブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="56471-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="56471-118">進行状況リング</span><span class="sxs-lookup"><span data-stu-id="56471-118">Progress ring</span></span>

![HoloLens の進行状況リングの例](images/640px-progressring.jpg)

<span data-ttu-id="56471-120">進行状況リングは、中間の状態がのみと、操作が完了するまで、さらに、ユーザーの操作がブロックされたときに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56471-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="56471-121">カスタム オブジェクトでの進行状況</span><span class="sxs-lookup"><span data-stu-id="56471-121">Progress with a custom object</span></span>

![HoloLens でカスタムのメッシュの例での進行状況](images/640px-progresscustom.jpg)

<span data-ttu-id="56471-123">カスタム 2d/3d オブジェクトで進行状況コントロールをカスタマイズすることで、アプリのパーソナリティとブランド id に追加できます。</span><span class="sxs-lookup"><span data-stu-id="56471-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="56471-124">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="56471-124">Best practices</span></span>
* <span data-ttu-id="56471-125">密に結合[ビルボード処理または tag-along](billboarding-and-tag-along.md)を簡単にユーザーは自分の頭を空の領域に移動し、コンテキストが失われるため、進行状況の表示にします。</span><span class="sxs-lookup"><span data-stu-id="56471-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="56471-126">アプリがクラッシュした場合は、ユーザーが何も表示できないように見える場合があります。</span><span class="sxs-lookup"><span data-stu-id="56471-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="56471-127">Billboarding と tag-along は、進行状況のプレハブに組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="56471-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="56471-128">ユーザーに何が起こっているかに関する状態情報を提供することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="56471-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="56471-129">進行状況のプレハブは、状態を提供するための Windows リング型の標準的な進行状況を含む、さまざまな視覚スタイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="56471-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="56471-130">場合は、アプリのブランドに合わせるために、進行状況のスタイルは、アニメーションがカスタム メッシュを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="56471-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="56471-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="56471-131">See also</span></span>
* [<span data-ttu-id="56471-132">スクリプトや Mixed Reality Toolkit の進行状況のプレハブ</span><span class="sxs-lookup"><span data-stu-id="56471-132">Scripts and prefabs for Progress on Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ProgressExample.md)
* [<span data-ttu-id="56471-133">対話型のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="56471-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="56471-134">オブジェクトのコレクション</span><span class="sxs-lookup"><span data-stu-id="56471-134">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="56471-135">ビルボード処理と tag-along</span><span class="sxs-lookup"><span data-stu-id="56471-135">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
