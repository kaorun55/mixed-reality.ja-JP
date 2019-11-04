---
title: 熟考
description: (視線/ヘッド) の宝石と熟考入力モデルの一般的な概要
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality、宝石、熟考、相互作用、設計、視線追跡、ヘッドトラッキング
ms.openlocfilehash: d87406d0b2695cd86c40f27cb132af54ed525b25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435354"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="8f7a4-104">熟考</span><span class="sxs-lookup"><span data-stu-id="8f7a4-104">Gaze and dwell</span></span>

<span data-ttu-id="8f7a4-105">工具や部品で手がふさがっていると、ジェスチャは面倒であったりできなかったりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="8f7a4-106">また、音声コマンドは特定のコンテキストでは信頼できない場合もあります。たとえば、非常に大きな条件が発生した場合などです。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="8f7a4-107">宝石と熟考は、HoloLens でのヘッドアップとハンズフリーの作業を行うための使い慣れた、簡単なマスタメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="8f7a4-108">また、宝石と熟考は、運用環境でのノイズ干渉や無音の制約に依存しない優れたフォールバックです。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-108">Additionally, gaze and dwell is a great fallback which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="8f7a4-109">_熟考_と[熟考](gaze-and-dwell-head.md)の2つのバリエーションと、[視線と熟考](gaze-and-dwell-eyes.md)を区別しています。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="8f7a4-110">シナリオ</span><span class="sxs-lookup"><span data-stu-id="8f7a4-110">Scenarios</span></span>

<span data-ttu-id="8f7a4-111">熟考は、人間の手が他のタスクと共に忙しい場合や、環境や社会的な制約のためにボイスが 100% reliable or available ではない場合に威力を持っています。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="8f7a4-112">良い例は、車のエンジンの修理中に参考情報をオーバーレイするために HoloLens を付けている人です。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="8f7a4-113">その人がエンジンルームに身を乗り出すとき、その手は工具でふさがっているか体を支えています。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="8f7a4-114">ガレージのスペースは絶えず工具を打ちつける音やブーンという音がして騒々しいため、音声コマンドを使うのは困難です。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="8f7a4-115">熟考を使用すると、HoloLens を使用するユーザーは、ワークフローを中断することなく、参照資料を自信を持ってナビゲートできます。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="8f7a4-116">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="8f7a4-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8f7a4-117"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="8f7a4-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="8f7a4-118"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8f7a4-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="8f7a4-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="8f7a4-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="8f7a4-120"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="8f7a4-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8f7a4-121">頭の視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="8f7a4-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="8f7a4-122">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="8f7a4-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="8f7a4-123">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="8f7a4-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="8f7a4-124">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="8f7a4-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8f7a4-125">視線と熟考</span><span class="sxs-lookup"><span data-stu-id="8f7a4-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="8f7a4-126">❌ 使用できません</span><span class="sxs-lookup"><span data-stu-id="8f7a4-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="8f7a4-127">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="8f7a4-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="8f7a4-128">❌ 使用できません</span><span class="sxs-lookup"><span data-stu-id="8f7a4-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="8f7a4-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f7a4-129">See also</span></span>
* [<span data-ttu-id="8f7a4-130">視線に基づく対話</span><span class="sxs-lookup"><span data-stu-id="8f7a4-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="8f7a4-131">HoloLens 2 の目の追跡</span><span class="sxs-lookup"><span data-stu-id="8f7a4-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="8f7a4-132">宝石とコミットメント</span><span class="sxs-lookup"><span data-stu-id="8f7a4-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="8f7a4-133">ハンドダイレクト操作</span><span class="sxs-lookup"><span data-stu-id="8f7a4-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8f7a4-134">ハンドジェスチャ</span><span class="sxs-lookup"><span data-stu-id="8f7a4-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="8f7a4-135">ハンドポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="8f7a4-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="8f7a4-136">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="8f7a4-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="8f7a4-137">音声入力</span><span class="sxs-lookup"><span data-stu-id="8f7a4-137">Voice input</span></span>](voice-input.md)
