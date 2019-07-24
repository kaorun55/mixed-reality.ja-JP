---
title: 視線入力
description: 見つめは入力の最初の形式であり、mixed reality 内でターゲットを設定する主な形式です。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed reality、宝石、相互作用、設計
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414371"
---
# <a name="gaze"></a><span data-ttu-id="d6982-104">視線入力</span><span class="sxs-lookup"><span data-stu-id="d6982-104">Gaze</span></span>

<span data-ttu-id="d6982-105">**見つめ**は入力の最初の形式であり、mixed reality 内でターゲットを設定する主な形式です。</span><span class="sxs-lookup"><span data-stu-id="d6982-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="d6982-106">宝石は、ユーザーが世界中のどこを見ているかを示し、その意図を判断することができます。</span><span class="sxs-lookup"><span data-stu-id="d6982-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="d6982-107">実世界では、通常、対話するオブジェクトを見ていきます。</span><span class="sxs-lookup"><span data-stu-id="d6982-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="d6982-108">これは、宝石と同じです。</span><span class="sxs-lookup"><span data-stu-id="d6982-108">This is the same with gaze.</span></span>

<span data-ttu-id="d6982-109">Mixed reality ヘッドセットでは、ユーザーの頭の位置と向きを使用して、頭を見つめたベクトルを決定します。</span><span class="sxs-lookup"><span data-stu-id="d6982-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="d6982-110">このベクトルは、ユーザーの目の間で直接のレーザーポインターと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="d6982-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="d6982-111">ユーザーが部屋を見ていくと、アプリケーションはこの射線と独自のホログラムを持つことができ、[空間マッピング](spatial-mapping.md)メッシュを使用して、ユーザーが見ている仮想オブジェクトや実世界オブジェクトを判断できます。</span><span class="sxs-lookup"><span data-stu-id="d6982-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="d6982-112">HoloLens 2 では、ユーザーの頭部、視線、またはほぼ手動の相互作用によって相互作用を対象にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d6982-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="d6982-113">HoloLens (第1世代) では、通常、ユーザーの顔からターゲットを導き出す必要があります。これは、ユーザーの位置を直接レンダリングしたり操作したりすることではありません。</span><span class="sxs-lookup"><span data-stu-id="d6982-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="d6982-114">相互作用が開始されたら、[操作やナビゲーション](gestures.md#composite-gestures)ジェスチャと同様に、ハンドの相対的な動きを使って[ジェスチャ](gestures.md)を制御できます。</span><span class="sxs-lookup"><span data-stu-id="d6982-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="d6982-115">イマーシブヘッドセットを使用すると、ヘッド見つめまたはポイント対応の[モーションコントローラー](motion-controllers.md)を使用してターゲットを調整できます。</span><span class="sxs-lookup"><span data-stu-id="d6982-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="d6982-116">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="d6982-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d6982-117"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="d6982-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="d6982-118"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="d6982-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="d6982-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="d6982-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="d6982-120"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="d6982-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d6982-121">頭を見つめます</span><span class="sxs-lookup"><span data-stu-id="d6982-121">Head gaze</span></span></td>
        <td><span data-ttu-id="d6982-122">✔️</span><span class="sxs-lookup"><span data-stu-id="d6982-122">✔️</span></span></td>
        <td><span data-ttu-id="d6982-123">✔️</span><span class="sxs-lookup"><span data-stu-id="d6982-123">✔️</span></span></td>
        <td><span data-ttu-id="d6982-124">✔️</span><span class="sxs-lookup"><span data-stu-id="d6982-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d6982-125">視線</span><span class="sxs-lookup"><span data-stu-id="d6982-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="d6982-126">❌</span><span class="sxs-lookup"><span data-stu-id="d6982-126">❌</span></span></td>
        <td><span data-ttu-id="d6982-127">✔️</span><span class="sxs-lookup"><span data-stu-id="d6982-127">✔️</span></span></td>
        <td><span data-ttu-id="d6982-128">❌</span><span class="sxs-lookup"><span data-stu-id="d6982-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="d6982-129">HoloLens 2 に固有のその他のガイダンスは[近日対応予定](index.md#news-and-notes)です。</span><span class="sxs-lookup"><span data-stu-id="d6982-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="d6982-130">見つめの使用</span><span class="sxs-lookup"><span data-stu-id="d6982-130">Uses of gaze</span></span>

<span data-ttu-id="d6982-131">Mixed reality の開発者として、ヘッドまたは目を見つめながら、さまざまなことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d6982-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="d6982-132">アプリは、ユーザーの注意がどこであるかを判断するために、シーン内のホログラムとの間で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d6982-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="d6982-133">アプリでは、ユーザーの宝石に基づいてジェスチャとコントローラーの押下をターゲットにして、ユーザーによる選択、アクティブ化、グラブ、スクロール、またはその他のホログラムとの対話を可能にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d6982-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="d6982-134">アプリを使用すると、空間マッピングメッシュを使用して、宝石を実際の表面に配置できます。</span><span class="sxs-lookup"><span data-stu-id="d6982-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="d6982-135">アプリでは、ユーザーが重要なオブジェクトの方向を確認し*ていない*ことを知ることができます。これにより、アプリは、そのオブジェクトに対して視覚的な合図やオーディオの手掛かりを与えることができます。</span><span class="sxs-lookup"><span data-stu-id="d6982-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="d6982-136">カーソル</span><span class="sxs-lookup"><span data-stu-id="d6982-136">Cursor</span></span>

<span data-ttu-id="d6982-137">ヘッドを見つめする場合は、ほとんどのアプリで[カーソル](cursors.md)(またはその他の聴覚/視覚表示) を使用して、ユーザーが対話しようとしている内容に自信を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6982-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="d6982-138">通常、このカーソルを世界中に配置して、頭の中線が1つ目のオブジェクトと交差するようにします。これは、ホログラムや実際の表面です。</span><span class="sxs-lookup"><span data-stu-id="d6982-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="d6982-139">![宝石を示すビジュアルカーソルの例](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="d6982-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="d6982-140">*宝石を示すビジュアルカーソルの例*</span><span class="sxs-lookup"><span data-stu-id="d6982-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="d6982-141">目を見つめて、通常はカーソルを表示し*ない*ことをお勧めします。これは、ユーザーにとって煩雑で面倒になるためです。</span><span class="sxs-lookup"><span data-stu-id="d6982-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="d6982-142">代わりに、視覚的なターゲットを微妙に強調表示するか、非常に薄い目のカーソルを使用して、ユーザーが何を操作しようとしているかについて自信を持っています。</span><span class="sxs-lookup"><span data-stu-id="d6982-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="d6982-143">詳細については、HoloLens 2 での[目に基づく入力の設計ガイダンスを](eye-tracking.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6982-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="d6982-144">ユーザーの宝石にアクションを与える</span><span class="sxs-lookup"><span data-stu-id="d6982-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="d6982-145">ユーザーが宝石を使用してホログラムまたは実際のオブジェクトを対象にしたら、次にそのオブジェクトに対してアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="d6982-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="d6982-146">ユーザーがアクションを実行する主な方法は、[ジェスチャ](gestures.md)、[モーションコントローラー](motion-controllers.md) 、[音声](voice-input.md)を使用することです。</span><span class="sxs-lookup"><span data-stu-id="d6982-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d6982-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6982-147">See also</span></span>
* [<span data-ttu-id="d6982-148">MR 入力 210:頭を見つめます</span><span class="sxs-lookup"><span data-stu-id="d6982-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="d6982-149">DirectX でのヘッド視線入力とアイ視線入力</span><span class="sxs-lookup"><span data-stu-id="d6982-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="d6982-150">Unity の頭を見つめます</span><span class="sxs-lookup"><span data-stu-id="d6982-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="d6982-151">HoloLens 2 での視線</span><span class="sxs-lookup"><span data-stu-id="d6982-151">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="d6982-152">Mixed Reality Toolkit を使用した Unity での視線</span><span class="sxs-lookup"><span data-stu-id="d6982-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
