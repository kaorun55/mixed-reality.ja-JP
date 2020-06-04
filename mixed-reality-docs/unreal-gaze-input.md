---
title: Unreal の入力を見つめます
description: HoloLens および Unreal Engine 用の宝石入力の設定に関するチュートリアル
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、HoloLens 2、視線追跡、宝石入力、ヘッドマウントディスプレイ、Unreal engine
ms.openlocfilehash: c77e33df2a1dfffdb5ea55e685d30af3fc2a22da
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330624"
---
# <a name="gaze-input"></a><span data-ttu-id="75361-104">見つめ入力</span><span class="sxs-lookup"><span data-stu-id="75361-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="75361-105">概要</span><span class="sxs-lookup"><span data-stu-id="75361-105">Overview</span></span>

<span data-ttu-id="75361-106">[Windows Mixed Reality プラグイン](https://docs.unrealengine.com/Platforms/VR/WMR/index.html)には、入力を見つめするための組み込み関数が用意されていませんが、HoloLens 2 では視線追跡がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="75361-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="75361-107">実際の追跡機能は、Unreal のマウントされた**ディスプレイ**と**視点の追跡**api によって提供され、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="75361-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="75361-108">デバイス情報</span><span class="sxs-lookup"><span data-stu-id="75361-108">Device information</span></span>
- <span data-ttu-id="75361-109">センサーの追跡</span><span class="sxs-lookup"><span data-stu-id="75361-109">Tracking sensors</span></span>
- <span data-ttu-id="75361-110">向きと位置</span><span class="sxs-lookup"><span data-stu-id="75361-110">Orientation and position</span></span>
- <span data-ttu-id="75361-111">クリップペイン</span><span class="sxs-lookup"><span data-stu-id="75361-111">Clipping panes</span></span>
- <span data-ttu-id="75361-112">データと追跡情報を見つめます</span><span class="sxs-lookup"><span data-stu-id="75361-112">Gaze data and tracking information</span></span>

<span data-ttu-id="75361-113">機能の完全な一覧については、Unreal の「マウントされた[ディスプレイ](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html)と[視点の追跡](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html)」ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75361-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span> 

<span data-ttu-id="75361-114">Unreal Api に加えて、HoloLens 2 の[視線に基づく相互作用](eye-gaze-interaction.md)に関するドキュメントを参照し、 [hololens 2 の視線追跡](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)がどのように動作するかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="75361-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="75361-115">視線追跡は、HoloLens 2 でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="75361-115">Eye tracking is only supported on HoloLens 2.</span></span> 

## <a name="enabling-eye-tracking"></a><span data-ttu-id="75361-116">目の追跡を有効にする</span><span class="sxs-lookup"><span data-stu-id="75361-116">Enabling eye tracking</span></span>
<span data-ttu-id="75361-117">Unreal の Api を使用するには、HoloLens の入力を HoloLens プロジェクト設定で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="75361-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="75361-118">アプリケーションが起動すると、次のスクリーンショットに同意プロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="75361-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="75361-119">[**はい**] を選択してアクセス許可を設定し、宝石入力のアクセス権を取得します。</span><span class="sxs-lookup"><span data-stu-id="75361-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="75361-120">この設定をいつでも変更する必要がある場合は、**設定**アプリで見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="75361-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![アイ入力のアクセス許可](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="75361-122">ステレオスコピックの追跡に必要な2つの光線はサポートされていないため、Unreal の HoloLens の追跡では、両方の目に1つの宝石があります。</span><span class="sxs-lookup"><span data-stu-id="75361-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="75361-123">これで、HoloLens の入力を HoloLens 2 のアプリに Unreal に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75361-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="75361-124">より簡単な入力と、それが混合現実のユーザーに与える影響の詳細については、以下のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75361-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="75361-125">対話型エクスペリエンスを構築するときは、これらのことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="75361-125">Be sure to think about these when building your interactive experiences.</span></span> 

## <a name="see-also"></a><span data-ttu-id="75361-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="75361-126">See also</span></span>
* [<span data-ttu-id="75361-127">調整</span><span class="sxs-lookup"><span data-stu-id="75361-127">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="75361-128">快適性</span><span class="sxs-lookup"><span data-stu-id="75361-128">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="75361-129">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="75361-129">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="75361-130">音声入力</span><span class="sxs-lookup"><span data-stu-id="75361-130">Voice input</span></span>](voice-design.md)
