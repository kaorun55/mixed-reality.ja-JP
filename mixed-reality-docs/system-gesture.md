---
title: システムジェスチャ
description: '[スタート] メニューを呼び出すシステムジェスチャ。'
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 混合現実、ジェスチャ、相互作用、設計
ms.openlocfilehash: 417811fff9d98e459dc0047d46ea065acfced4ef
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064237"
---
# <a name="system-gesture"></a><span data-ttu-id="48a25-104">システムジェスチャ</span><span class="sxs-lookup"><span data-stu-id="48a25-104">System gesture</span></span>

<span data-ttu-id="48a25-105">システムジェスチャは、[スタート] メニューを呼び出すために使用するハンドジェスチャです。</span><span class="sxs-lookup"><span data-stu-id="48a25-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="48a25-106">これは、キーボードの Windows キー、Xbox コントローラーの Xbox ボタン、またはイマーシブヘッドセットモーションコントローラーの Windows ボタンを押すことに相当します。</span><span class="sxs-lookup"><span data-stu-id="48a25-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="48a25-107">相互作用を設計するときの競合を防ぐため、各 Mixed Reality デバイスでシステム用に予約されているジェスチャを理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="48a25-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="48a25-108">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="48a25-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="48a25-109"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="48a25-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="48a25-110"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="48a25-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="48a25-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="48a25-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="48a25-112"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="48a25-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="48a25-113">ブルーム</span><span class="sxs-lookup"><span data-stu-id="48a25-113">Bloom</span></span></td>
        <td><span data-ttu-id="48a25-114">✔️</span><span class="sxs-lookup"><span data-stu-id="48a25-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="48a25-115">手首ボタン</span><span class="sxs-lookup"><span data-stu-id="48a25-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="48a25-116">✔️</span><span class="sxs-lookup"><span data-stu-id="48a25-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="48a25-117">視線とパームアップのピンチ</span><span class="sxs-lookup"><span data-stu-id="48a25-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="48a25-118">✔️</span><span class="sxs-lookup"><span data-stu-id="48a25-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="48a25-119">ブルーム</span><span class="sxs-lookup"><span data-stu-id="48a25-119">Bloom</span></span>
<span data-ttu-id="48a25-120">HoloLens (第1世代) の [スタート] メニューを表示するには、"ブルーム" を設計しました。これは、花開花を模倣したシンボリックジェスチャです。</span><span class="sxs-lookup"><span data-stu-id="48a25-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="48a25-121">これは、簡単に操作できるようにするためのものであり、簡単に実行でき、簡単に再現できます。</span><span class="sxs-lookup"><span data-stu-id="48a25-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="48a25-122">HoloLens (第1世代) でブルームジェスチャを実行するには、手を手に入れてすぐに手に入れ、指を押しながら手を開けます。</span><span class="sxs-lookup"><span data-stu-id="48a25-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="48a25-123">![ブルーム close](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="48a25-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="48a25-124">**手順 1: すぐに使用することができます。**</span><span class="sxs-lookup"><span data-stu-id="48a25-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="48a25-125">![ブルーム open](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="48a25-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="48a25-126">**手順 2: すぐに使えるパームアップ**</span><span class="sxs-lookup"><span data-stu-id="48a25-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a><span data-ttu-id="48a25-127">手首ボタン</span><span class="sxs-lookup"><span data-stu-id="48a25-127">Wrist button</span></span>
<span data-ttu-id="48a25-128">HoloLens 2 では、ブルームジェスチャを仮想手首ボタンに置き換えました。これにより、追加の教育を必要としない instinctual の対話が可能になります。</span><span class="sxs-lookup"><span data-stu-id="48a25-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="48a25-129">手首にユーザーを表示することにより、ユーザーは直感的に接続して、もう一方の手で押すことができます。</span><span class="sxs-lookup"><span data-stu-id="48a25-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="48a25-130">![手首ボタンの準備完了](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="48a25-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="48a25-131">**手順 1: パームアップ: 手首ボタンを表示する**</span><span class="sxs-lookup"><span data-stu-id="48a25-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="48a25-132">![手首ボタンを押し](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="48a25-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="48a25-133">**手順 2: 手首ボタンを押す**</span><span class="sxs-lookup"><span data-stu-id="48a25-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a><span data-ttu-id="48a25-134">視線とパームアップのピンチ</span><span class="sxs-lookup"><span data-stu-id="48a25-134">Eye-gaze and palm up pinch</span></span>
<span data-ttu-id="48a25-135">また、HoloLens 2 でのアクセスを容易にするための1つのソリューションを設計しました。</span><span class="sxs-lookup"><span data-stu-id="48a25-135">We have also designed a one-handed solution for ease of access in HoloLens 2.</span></span> <span data-ttu-id="48a25-136">このジェスチャを使用するには、ユーザーが手首ボタンをクリックし、同じ手で親指とインデックスの指を使用して、パームアップピンチを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48a25-136">This gesture requires users to eye gaze at the wrist button, then use the same hand to perform a palm up pinch using their thumb and index finger.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="48a25-137">![手首ボタンの準備完了](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="48a25-137">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="48a25-138">**手順 1: パームアップ: 手首ボタンを表示する**</span><span class="sxs-lookup"><span data-stu-id="48a25-138">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="48a25-139">![手首ボタンのピンチ](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="48a25-139">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="48a25-140">**手順 2: ボタンをクリックしてからピンチする**</span><span class="sxs-lookup"><span data-stu-id="48a25-140">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="48a25-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="48a25-141">See also</span></span>

* [<span data-ttu-id="48a25-142">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="48a25-142">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="48a25-143">アイ視線入力</span><span class="sxs-lookup"><span data-stu-id="48a25-143">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="48a25-144">音声入力</span><span class="sxs-lookup"><span data-stu-id="48a25-144">Voice input</span></span>](voice-input.md)
