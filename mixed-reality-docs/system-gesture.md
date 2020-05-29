---
title: 開始ジェスチャ
description: スタートメニューを呼び出す開始ジェスチャ。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 混合現実、ジェスチャ、相互作用、設計
ms.openlocfilehash: 84088156d0c9cdacc421985b922d5e9370f6a87e
ms.sourcegitcommit: fd606e87e3c4785d3ca2a26632be3bb580e39afb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2020
ms.locfileid: "84152513"
---
# <a name="start-gesture"></a><span data-ttu-id="76997-104">開始ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="76997-104">Start gesture</span></span>

<span data-ttu-id="76997-105">Start ジェスチャは、[スタート] メニューを呼び出すために使用するハンドジェスチャです。</span><span class="sxs-lookup"><span data-stu-id="76997-105">The Start gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="76997-106">これは、キーボードの Windows キー、Xbox コントローラーの Xbox ボタン、またはイマーシブヘッドセットモーションコントローラーの Windows ボタンを押すことに相当します。</span><span class="sxs-lookup"><span data-stu-id="76997-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="76997-107">相互作用を設計するときの競合を防ぐため、各 Mixed Reality デバイスでシステム用に予約されているジェスチャを理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="76997-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="76997-108">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="76997-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="76997-109"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="76997-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="76997-110"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="76997-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="76997-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="76997-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="76997-112"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="76997-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="76997-113">Bloom (ブルーム)</span><span class="sxs-lookup"><span data-stu-id="76997-113">Bloom</span></span></td>
        <td><span data-ttu-id="76997-114">✔️</span><span class="sxs-lookup"><span data-stu-id="76997-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="76997-115">手首ボタン</span><span class="sxs-lookup"><span data-stu-id="76997-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="76997-116">✔️</span><span class="sxs-lookup"><span data-stu-id="76997-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="76997-117">視線とパームアップのピンチ</span><span class="sxs-lookup"><span data-stu-id="76997-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="76997-118">✔️</span><span class="sxs-lookup"><span data-stu-id="76997-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="76997-119">Bloom (ブルーム)</span><span class="sxs-lookup"><span data-stu-id="76997-119">Bloom</span></span>
<span data-ttu-id="76997-120">HoloLens (第1世代) の [スタート] メニューを表示するには、"ブルーム" を設計しました。これは、花開花を模倣したシンボリックジェスチャです。</span><span class="sxs-lookup"><span data-stu-id="76997-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="76997-121">これは、簡単に操作できるようにするためのものであり、簡単に実行でき、簡単に再現できます。</span><span class="sxs-lookup"><span data-stu-id="76997-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="76997-122">HoloLens (第1世代) でブルームジェスチャを実行するには、手を手に入れてすぐに手に入れ、指を押しながら手を開けます。</span><span class="sxs-lookup"><span data-stu-id="76997-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="76997-123">![ブルーム close](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="76997-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="76997-124">**手順 1: すぐに使用することができます。**</span><span class="sxs-lookup"><span data-stu-id="76997-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="76997-125">![ブルームを開く](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="76997-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="76997-126">**手順 2: すぐに使えるパームアップ**</span><span class="sxs-lookup"><span data-stu-id="76997-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="76997-127">開始ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="76997-127">Start gesture</span></span>
<span data-ttu-id="76997-128">HoloLens 2 では、ブルームジェスチャを仮想手首ボタンに置き換えました。これにより、追加の教育を必要としない instinctual の対話が可能になります。</span><span class="sxs-lookup"><span data-stu-id="76997-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="76997-129">手首にユーザーを表示することにより、ユーザーは直感的に接続して、もう一方の手で押すことができます。</span><span class="sxs-lookup"><span data-stu-id="76997-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="76997-130">![手首ボタンの準備完了](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="76997-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="76997-131">**手順 1: パームアップ: 手首ボタンを表示する**</span><span class="sxs-lookup"><span data-stu-id="76997-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="76997-132">![手首ボタンの押下](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="76997-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="76997-133">**手順 2: 手首ボタンを押す**</span><span class="sxs-lookup"><span data-stu-id="76997-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a><span data-ttu-id="76997-134">ワンきき開始ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="76997-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="76997-135">ワンきき開始ジェスチャを機能させるには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="76997-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="76997-136">2019年11月の更新プログラム (ビルド 18363.1039) 以降に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76997-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="76997-137">視線追跡が正常に機能するように、デバイスで目を調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76997-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="76997-138">[Start] \ (開始 \) アイコンを見たときに orbiting のドットが表示されない場合は、デバイス上で目が調整されていません。</span><span class="sxs-lookup"><span data-stu-id="76997-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="76997-139">開始ジェスチャは、ワンハンドでのみ実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="76997-139">You can also perform the Start gesture with only one hand.</span></span> <span data-ttu-id="76997-140">これを行うには、パームに接続したままにして、内部の手首の [**開始] アイコン**を見てください。</span><span class="sxs-lookup"><span data-stu-id="76997-140">To do this, hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="76997-141">**アイコンを見たまま**にして、親指と人差し指を一緒にピンチします。</span><span class="sxs-lookup"><span data-stu-id="76997-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="76997-142">![手首ボタンの準備完了](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="76997-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="76997-143">**手順 1: パームアップ: 手首ボタンを表示する**</span><span class="sxs-lookup"><span data-stu-id="76997-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="76997-144">![手首ボタンのピンチ](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="76997-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="76997-145">**手順 2: ボタンをクリックしてからピンチする**</span><span class="sxs-lookup"><span data-stu-id="76997-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="76997-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="76997-146">See also</span></span>

* [<span data-ttu-id="76997-147">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="76997-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="76997-148">アイ視線入力</span><span class="sxs-lookup"><span data-stu-id="76997-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="76997-149">音声入力</span><span class="sxs-lookup"><span data-stu-id="76997-149">Voice input</span></span>](voice-input.md)
