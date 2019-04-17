---
title: 導入事例 - Lowe の台所からの教訓
description: HoloLens チーム Lowe の HoloLens のプロジェクトに由来するベスト プラクティスの一部を共有したいです。
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、Lowe の HoloLens、キッチン、ケース スタディ
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599844"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="f2841-104">導入事例 - Lowe の台所からの教訓</span><span class="sxs-lookup"><span data-stu-id="f2841-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="f2841-105">HoloLens チーム Lowe の HoloLens のプロジェクトに由来するベスト プラクティスの一部を共有したいです。</span><span class="sxs-lookup"><span data-stu-id="f2841-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="f2841-106">投影 Lowe の HoloLens のビデオは、Satya の 2016 Ignite の基調講演で以下は示されます。</span><span class="sxs-lookup"><span data-stu-id="f2841-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="f2841-107">Lowe の HoloLens のベスト プラクティスします。</span><span class="sxs-lookup"><span data-stu-id="f2841-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="f2841-108">2 つのビデオでは、2016 年 4 月以降の 2 つの Lowe のストアにきました Lowe の HoloLens のパイロットから派生されたベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f2841-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="f2841-109">重要なトピックは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f2841-109">The key topics are:</span></span>
* <span data-ttu-id="f2841-110">モバイル デバイスのパフォーマンスを最大化します。</span><span class="sxs-lookup"><span data-stu-id="f2841-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="f2841-111">完全な holographic フレームを使用して UX メソッドを作成 (第 2 のトーク)</span><span class="sxs-lookup"><span data-stu-id="f2841-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="f2841-112">有効桁数の配置 (第 2 のトーク)</span><span class="sxs-lookup"><span data-stu-id="f2841-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="f2841-113">Holographic エクスペリエンスを共有する (第 2 のトーク)</span><span class="sxs-lookup"><span data-stu-id="f2841-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="f2841-114">顧客と対話する (第 2 のトーク)</span><span class="sxs-lookup"><span data-stu-id="f2841-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="f2841-115">ビデオ 1</span><span class="sxs-lookup"><span data-stu-id="f2841-115">Video 1</span></span>

<span data-ttu-id="f2841-116">**モバイル デバイスのパフォーマンスを最大化**HoloLens は無制限のデバイス、デバイスで発生しているすべての処理をします。</span><span class="sxs-lookup"><span data-stu-id="f2841-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="f2841-117">これにより、モバイル プラットフォームを必要とされ、モバイル アプリケーションを作成するような考え方が必要です。</span><span class="sxs-lookup"><span data-stu-id="f2841-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="f2841-118">HoloLens アプリケーションが、ユーザーにおいしいエクスペリエンスを提供する 60 FPS を維持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f2841-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="f2841-119">低い FPS のことと、不安定なホログラムがあります。</span><span class="sxs-lookup"><span data-stu-id="f2841-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="f2841-120">資産最適化/デシメーション、カスタムのシェーダーを使用するには HoloLens で開発するときに確認する最も重要なもの (を無料で利用可能な[HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity))。</span><span class="sxs-lookup"><span data-stu-id="f2841-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="f2841-121">もう 1 つの重要な考慮事項では、プロジェクトの先頭からのフレーム レートを測定します。</span><span class="sxs-lookup"><span data-stu-id="f2841-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="f2841-122">によって、プロジェクトのアセットを表示する順序こともできます大規模な共同作成者</span><span class="sxs-lookup"><span data-stu-id="f2841-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="f2841-123">ビデオ 2</span><span class="sxs-lookup"><span data-stu-id="f2841-123">Video 2</span></span>

<span data-ttu-id="f2841-124">**UX メソッドを holographic の完全なフレームを使用して作成**ホログラム物理世界での配置を理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="f2841-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="f2841-125">Lowe の使用ユーザーながらホログラムの大規模な環境をエクスペリエンス ホログラムが閉じるに役立つさまざまな UX 方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2841-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="f2841-126">**有効桁数の配置**For the Lowe のシナリオでは、物理の台所に、ホログラムの有効桁数の配置にエクスペリエンスを非常に重要でした。</span><span class="sxs-lookup"><span data-stu-id="f2841-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="f2841-127">仕向け、物理環境が変更されたユーザー エクスペリエンスを高める方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2841-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="f2841-128">**Holographic エクスペリエンスを共有**カップルが Lowe のエクスペリエンスが使用される主な方法です。</span><span class="sxs-lookup"><span data-stu-id="f2841-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="f2841-129">1 人のユーザーが、カウンターを変更および変更を他の人が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2841-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="f2841-130">この「共有・ エクスペリエンス」と呼ばれていました。</span><span class="sxs-lookup"><span data-stu-id="f2841-130">We called this "shared experiences".</span></span>

<span data-ttu-id="f2841-131">**顧客との対話**Lowe のデザイナーは、HoloLens を使用していないが表示される、顧客を表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2841-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="f2841-132">UWP アプリケーションに、顧客が表示されるかをキャプチャする方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="f2841-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
