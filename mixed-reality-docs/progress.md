---
title: 進行状況の表示
description: プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、コントロール、ui、ux
ms.openlocfilehash: 43b4802e7c821c98c847509ace950f381da12f95
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437541"
---
# <a name="displaying-progress"></a><span data-ttu-id="145e9-104">進行状況の表示</span><span class="sxs-lookup"><span data-stu-id="145e9-104">Displaying progress</span></span>

<br>

<img src="images/HoloLens2_Loader.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="145e9-105">プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。</span><span class="sxs-lookup"><span data-stu-id="145e9-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="145e9-106">使用されているインジケーターに応じて、進行状況インジケーターが表示されているときはユーザーはアプリを操作できないことを知らせたり、待ち時間の長さを示したりできます。</span><span class="sxs-lookup"><span data-stu-id="145e9-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="145e9-107">プログレス コントロールの種類</span><span class="sxs-lookup"><span data-stu-id="145e9-107">Types of progress</span></span>

<span data-ttu-id="145e9-108">何が起こっているかについてユーザー情報を提供することが重要です。</span><span class="sxs-lookup"><span data-stu-id="145e9-108">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="145e9-109">混合環境では、アプリから視覚的なフィードバックが得られない場合、ユーザーは物理環境またはオブジェクトによって簡単に気にすることができます。</span><span class="sxs-lookup"><span data-stu-id="145e9-109">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="145e9-110">データが読み込まれたりシーンが更新されたりするなど、数秒かかる状況では、視覚的なインジケーターを表示することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="145e9-110">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="145e9-111">操作が進行しているユーザーを表示するには、**進行状況バー**または**進行状況のリング**の2つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="145e9-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="145e9-112">進行状況バー</span><span class="sxs-lookup"><span data-stu-id="145e9-112">Progress bar</span></span><br>
        <span data-ttu-id="145e9-113">進行状況バーには、タスクの完了率が表示されます。</span><span class="sxs-lookup"><span data-stu-id="145e9-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="145e9-114">このメソッドは、期間が既知 (有限) の操作中に使用する必要がありますが、進行中のユーザーとアプリとの対話をブロックすることはできません。</span><span class="sxs-lookup"><span data-stu-id="145e9-114">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="145e9-115">*イメージ: HoloLens での進行状況バーの例*</span><span class="sxs-lookup"><span data-stu-id="145e9-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="145e9-116">![領域](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="145e9-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="145e9-117">HoloLens](images/640px-progressbar.jpg) の進行状況バーの例 ![</span><span class="sxs-lookup"><span data-stu-id="145e9-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="145e9-118">進行状況リング</span><span class="sxs-lookup"><span data-stu-id="145e9-118">Progress ring</span></span><br>
        <span data-ttu-id="145e9-119">進行状況のリングは不確定な状態であるため、操作が完了するまで他のユーザー操作がブロックされたときに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="145e9-119">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="145e9-120">*イメージ: HoloLens での進行状況リングの例*</span><span class="sxs-lookup"><span data-stu-id="145e9-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="145e9-121">![領域](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="145e9-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="145e9-122">HoloLens](images/640px-progressring.jpg) での ![の進行状況リングの例</span><span class="sxs-lookup"><span data-stu-id="145e9-122">![Progress ring example in HoloLens](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="145e9-123">カスタムオブジェクトの進行状況</span><span class="sxs-lookup"><span data-stu-id="145e9-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="145e9-124">独自のカスタム 2D/3D オブジェクトを使用して進行状況の制御をカスタマイズすることで、アプリの個性とブランド id に追加できます。</span><span class="sxs-lookup"><span data-stu-id="145e9-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="145e9-125">*イメージ: HoloLens でのカスタムメッシュの例の進行状況*</span><span class="sxs-lookup"><span data-stu-id="145e9-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="145e9-126">![領域](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="145e9-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="145e9-127">HoloLens](images/640px-progresscustom.jpg) でカスタムメッシュの例を使用して進行状況を ![</span><span class="sxs-lookup"><span data-stu-id="145e9-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="145e9-128">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="145e9-128">Best practices</span></span>
* <span data-ttu-id="145e9-129">ユーザーが簡単にヘッドを空の領域に移動してコンテキストを失うことがあるため、 [billboarding またはタグ](billboarding-and-tag-along.md)を進行状況の表示に密に結合します。</span><span class="sxs-lookup"><span data-stu-id="145e9-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="145e9-130">ユーザーが何も表示できない場合、アプリがクラッシュしたように見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="145e9-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="145e9-131">Billboarding とタグは、進行状況の prefab に組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="145e9-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="145e9-132">ユーザーに対して何が起こっているかに関するステータス情報を常に提供するのが適切です。</span><span class="sxs-lookup"><span data-stu-id="145e9-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="145e9-133">Progress prefab には、状態を提供するための Windows 標準のリングの種類の進行状況など、さまざまな視覚スタイルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="145e9-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="145e9-134">また、進行状況のスタイルをアプリのブランドに合わせる必要がある場合は、アニメーションでカスタムメッシュを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="145e9-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="145e9-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="145e9-135">See also</span></span>
* [<span data-ttu-id="145e9-136">Mixed Reality Toolkit での進行状況スクリプトと prefabs</span><span class="sxs-lookup"><span data-stu-id="145e9-136">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="145e9-137">境界ボックス</span><span class="sxs-lookup"><span data-stu-id="145e9-137">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="145e9-138">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="145e9-138">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="145e9-139">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="145e9-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="145e9-140">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="145e9-140">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
