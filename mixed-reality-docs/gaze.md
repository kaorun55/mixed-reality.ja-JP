---
title: 視線入力
description: 視線の先は、入力の最初のフォームでの複合現実内で対象とする主な形式です。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 設計、実際には、視線の先、相互作用を混在
ms.openlocfilehash: 9e50067f9dfeacf3dce5ea9a928990d1b142e4d0
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453709"
---
# <a name="gaze"></a><span data-ttu-id="15d69-104">視線入力</span><span class="sxs-lookup"><span data-stu-id="15d69-104">Gaze</span></span>

<span data-ttu-id="15d69-105">**視線**入力の最初のフォームは、複合現実内で対象とするの主な形式です。</span><span class="sxs-lookup"><span data-stu-id="15d69-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="15d69-106">視線の先では、ユーザーが世界中を検索していると、その目的を決定することができますを指示します。</span><span class="sxs-lookup"><span data-stu-id="15d69-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="15d69-107">現実の世界ではする通常と対話するオブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="15d69-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="15d69-108">これは、視線入力と同じです。</span><span class="sxs-lookup"><span data-stu-id="15d69-108">This is the same with gaze.</span></span>

<span data-ttu-id="15d69-109">Mixed reality ヘッドセットでは、位置とユーザーの頭の向きを使用して、そのヘッド視線入力ベクトルを決定します。</span><span class="sxs-lookup"><span data-stu-id="15d69-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="15d69-110">このベクトルは、ユーザーの目の間で直接からまっすぐレーザー ポインタとして考えることができます。</span><span class="sxs-lookup"><span data-stu-id="15d69-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="15d69-111">アプリケーションことができます独自ホログラムとでこの射線が交差するように、ユーザーは、部屋は、[空間マッピング](spatial-mapping.md)メッシュがどのようなユーザーが表示されます仮想または実際のオブジェクトを決定します。</span><span class="sxs-lookup"><span data-stu-id="15d69-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="15d69-112">HoloLens 2 は、相互作用はユーザーのヘッド視線入力、目視線の先の対象となることができます、近くまでまたはまたは相互作用をはるかに渡します。</span><span class="sxs-lookup"><span data-stu-id="15d69-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="15d69-113">HoloLens で (第 1 世代)、そのユーザーの視線入力ヘッドからターゲットではなくしようとしてレンダリングまたはして手のアイコンの場所に直接対話の相互作用の派生一般にします。</span><span class="sxs-lookup"><span data-stu-id="15d69-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="15d69-114">コントロールに手の相対的な動きを使用可能性があります相互作用が開始されたら、[ジェスチャ](gestures.md)と同様、[操作やナビゲーション](gestures.md#composite-gestures)ジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="15d69-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="15d69-115">イマーシブ ヘッドセットとを対象にできますかヘッド視線の先を使用してポイント対応または[コント ローラーのモーション](motion-controllers.md)します。</span><span class="sxs-lookup"><span data-stu-id="15d69-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="15d69-116">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="15d69-116">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="15d69-117">機能</span><span class="sxs-lookup"><span data-stu-id="15d69-117">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="15d69-118"><a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></span><span class="sxs-lookup"><span data-stu-id="15d69-118"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="15d69-119">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="15d69-119">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="15d69-120"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="15d69-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="15d69-121">Head 視線入力</span><span class="sxs-lookup"><span data-stu-id="15d69-121">Head gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="15d69-122">✔️</span><span class="sxs-lookup"><span data-stu-id="15d69-122">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="15d69-123">✔️</span><span class="sxs-lookup"><span data-stu-id="15d69-123">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="15d69-124">✔️</span><span class="sxs-lookup"><span data-stu-id="15d69-124">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="15d69-125">目の視線入力</span><span class="sxs-lookup"><span data-stu-id="15d69-125">Eye gaze</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="15d69-126">✔️</span><span class="sxs-lookup"><span data-stu-id="15d69-126">✔️</span></span></td><td></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="15d69-127">HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。</span><span class="sxs-lookup"><span data-stu-id="15d69-127">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="15d69-128">視線の先の使用</span><span class="sxs-lookup"><span data-stu-id="15d69-128">Uses of gaze</span></span>

<span data-ttu-id="15d69-129">開発者は、複合現実で行えること多くヘッドまたは目視線の先。</span><span class="sxs-lookup"><span data-stu-id="15d69-129">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="15d69-130">アプリには、ユーザーの注意の場所を確認すると、シーン内ホログラム視線の先が交差することができます。</span><span class="sxs-lookup"><span data-stu-id="15d69-130">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="15d69-131">ジェスチャとコント ローラーの押下の選択、アクティブ化、取得、スクロールして、またはそれ以外の場合、ホログラムとの対話をユーザーに知らせて、ユーザーの視線入力に基づいて、アプリの対象に。</span><span class="sxs-lookup"><span data-stu-id="15d69-131">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="15d69-132">アプリでは、空間マッピング メッシュでその注視射線が交差するで現実世界のサーフェスにホログラムを配置するユーザーをさせることができます。</span><span class="sxs-lookup"><span data-stu-id="15d69-132">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="15d69-133">アプリは、ユーザーが場合を知ることが*いない*、そのオブジェクトに有効にするビジュアルおよびオーディオの手掛かりを提供するアプリにつながることが重要なオブジェクトの方向に検索します。</span><span class="sxs-lookup"><span data-stu-id="15d69-133">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="15d69-134">カーソル</span><span class="sxs-lookup"><span data-stu-id="15d69-134">Cursor</span></span>

<span data-ttu-id="15d69-135">ヘッド視線の先、ほとんどのアプリを使用する必要があります、[カーソル](cursors.md)(またはその他の聴覚的/visual indication) と対話しようとしている内容でユーザーの信頼を付与します。</span><span class="sxs-lookup"><span data-stu-id="15d69-135">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="15d69-136">通常、そのヘッド注視レイ ホログラムまたは実際の画面がある、オブジェクトが交差する最初の世界では、このカーソルを置きます。</span><span class="sxs-lookup"><span data-stu-id="15d69-136">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="15d69-137">![視線の先を表示する例を visual カーソル](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="15d69-137">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="15d69-138">*視線の先を表示する例を visual カーソル*</span><span class="sxs-lookup"><span data-stu-id="15d69-138">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="15d69-139">目の視線の一般的な推奨*いない*をシステムとユーザーの面倒をすぐにこのことができます、カーソルを表示します。</span><span class="sxs-lookup"><span data-stu-id="15d69-139">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="15d69-140">代わりに微妙ビジュアル ターゲットを強調表示またはが対話するユーザーの信頼性を提供する非常に薄い目のカーソルを使用します。</span><span class="sxs-lookup"><span data-stu-id="15d69-140">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="15d69-141">詳細についてを参照してください、[目に基づく入力の設計ガイダンス](eye-tracking.md)HoloLens 2 にします。</span><span class="sxs-lookup"><span data-stu-id="15d69-141">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="15d69-142">ユーザーの視線の先へアクションの提供</span><span class="sxs-lookup"><span data-stu-id="15d69-142">Giving action to the user's gaze</span></span>

<span data-ttu-id="15d69-143">ホログラムまたは、視線の先を使用して実際のオブジェクトの対象に、ユーザーが後、次の手順が、そのオブジェクトに対してアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="15d69-143">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="15d69-144">ユーザーがアクションを実行するための主な方法は[ジェスチャ](gestures.md)、[コント ローラーのモーション](motion-controllers.md)と[音声](voice-input.md)します。</span><span class="sxs-lookup"><span data-stu-id="15d69-144">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15d69-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="15d69-145">See also</span></span>
* [<span data-ttu-id="15d69-146">MR 入力 210:Head 視線入力</span><span class="sxs-lookup"><span data-stu-id="15d69-146">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="15d69-147">DirectX でのヘッド視線入力とアイ視線入力</span><span class="sxs-lookup"><span data-stu-id="15d69-147">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="15d69-148">Unity で Head 視線入力</span><span class="sxs-lookup"><span data-stu-id="15d69-148">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="15d69-149">HoloLens 2 の視線</span><span class="sxs-lookup"><span data-stu-id="15d69-149">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="15d69-150">Mixed Reality Toolkit を使用して Unity で目視線入力</span><span class="sxs-lookup"><span data-stu-id="15d69-150">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
