---
title: Spectator ビュー
description: 外部ディスプレイで mixed reality エクスペリエンスをデモンストレーションする手段として、または mixed reality エクスペリエンスのビデオを録画する手段として、外部デバイスからホログラムを視覚化します。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator View、iPhone、iOS、iPad、OpenCV、カメラ、ARKit、HoloLens、Mixed Reality、MixedRealityToolkit、demo、record
ms.openlocfilehash: 135a566456f1000669d2033edcf0d0b4649ccdf3
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387669"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="437c7-104">HoloLens および HoloLens 用 Spectator ビュー2</span><span class="sxs-lookup"><span data-stu-id="437c7-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="437c7-106">概要</span><span class="sxs-lookup"><span data-stu-id="437c7-106">Overview</span></span>

<span data-ttu-id="437c7-107">HoloLens を装着すると、それを持っていない人は、可能な偉大なる象徴を体験することができなくなります。</span><span class="sxs-lookup"><span data-stu-id="437c7-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="437c7-108">Spectator View を使用すると、他のユーザーは、世界で HoloLens ユーザーに表示される2D 画面で見ることができます。</span><span class="sxs-lookup"><span data-stu-id="437c7-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="437c7-109">Spectator View は、モバイルデバイスで HD のホログラムを記録するための、高速で手頃な価格のアプローチを提供します。</span><span class="sxs-lookup"><span data-stu-id="437c7-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="437c7-110">また、ビデオカメラを使用したホログラムの高品質記録も提供します。</span><span class="sxs-lookup"><span data-stu-id="437c7-110">It also offers a professional quality recording of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="437c7-111">主要リソース</span><span class="sxs-lookup"><span data-stu-id="437c7-111">Key Resources</span></span>

* [<span data-ttu-id="437c7-112">**GitHub の Spectator ビュー**</span><span class="sxs-lookup"><span data-stu-id="437c7-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="437c7-113">**構造**</span><span class="sxs-lookup"><span data-stu-id="437c7-113">**Architecture**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Architecture.md)
* [<span data-ttu-id="437c7-114">**Samples**</span><span class="sxs-lookup"><span data-stu-id="437c7-114">**Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)
* [<span data-ttu-id="437c7-115">**モバイルセットアップの手順**</span><span class="sxs-lookup"><span data-stu-id="437c7-115">**Mobile Setup Instructions**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.md)
* [<span data-ttu-id="437c7-116">**ビデオカメラのセットアップ手順**</span><span class="sxs-lookup"><span data-stu-id="437c7-116">**Video Camera Setup Instructions**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.VideoCamera.md)

## <a name="use-cases"></a><span data-ttu-id="437c7-117">ユース ケース</span><span class="sxs-lookup"><span data-stu-id="437c7-117">Use Cases</span></span>
* <span data-ttu-id="437c7-118">IPhone または Android デバイスを使用して、mixed reality エクスペリエンスを記録できます。</span><span class="sxs-lookup"><span data-stu-id="437c7-118">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="437c7-119">フル HD で記録し、ホログラムと偶数の影にアンチエイリアシングを適用します。</span><span class="sxs-lookup"><span data-stu-id="437c7-119">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="437c7-120">これは、ホログラムのビデオをキャプチャする費用効果が高く、迅速な方法です。</span><span class="sxs-lookup"><span data-stu-id="437c7-120">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="437c7-121">ライブ mixed reality エクスペリエンスを iPhone または iPad から直接 Apple TV にストリーミングし、すぐに利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="437c7-121">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="437c7-122">ゲストとのエクスペリエンスを共有します。非 HoloLens ユーザーが自分の電話やタブレットから直接ホログラムを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="437c7-122">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="437c7-123">現在の機能</span><span class="sxs-lookup"><span data-stu-id="437c7-123">Current Features</span></span>

* <span data-ttu-id="437c7-124">ホログラムの空間同期によって、すべてのユーザーが同じ場所でホログラムを確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="437c7-124">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="437c7-125">iOS (ARKit 対応デバイス) と Android (Arkit 対応デバイス) はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="437c7-125">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="437c7-126">複数の iOS ゲスト。</span><span class="sxs-lookup"><span data-stu-id="437c7-126">Multiple iOS guests.</span></span>
<span data-ttu-id="437c7-127">ビデオ + ホログラム + アンビエントサウンド + ホログラムサウンドの記録。</span><span class="sxs-lookup"><span data-stu-id="437c7-127">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="437c7-128">ビデオを保存したり、電子メールで送信したり、他のサポートアプリと共有したりできるように、シートを共有します。</span><span class="sxs-lookup"><span data-stu-id="437c7-128">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="437c7-129">![](images/SpecViewPhoneDemo.jpg)
マーカーマーカー![マーカー](images/hololensspectatorview-500px.jpg) ![](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="437c7-129">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="437c7-130">次の表は、Spectator ビューのさまざまな機能とその機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="437c7-130">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="437c7-131">ビデオ記録のニーズに最適なオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="437c7-131">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="437c7-132">携帯</span><span class="sxs-lookup"><span data-stu-id="437c7-132">Mobile</span></span>                  |                    <span data-ttu-id="437c7-133">ビデオカメラ</span><span class="sxs-lookup"><span data-stu-id="437c7-133">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="437c7-134">HD 品質</span><span class="sxs-lookup"><span data-stu-id="437c7-134">HD quality</span></span>                           |         <span data-ttu-id="437c7-135">フル HD</span><span class="sxs-lookup"><span data-stu-id="437c7-135">Full HD</span></span>         |        <span data-ttu-id="437c7-136">Professional quality 撮影 (ビデオカメラによって決定)</span><span class="sxs-lookup"><span data-stu-id="437c7-136">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="437c7-137">カメラの移動を簡単に</span><span class="sxs-lookup"><span data-stu-id="437c7-137">Easy camera movement</span></span>                 |            <span data-ttu-id="437c7-138">✔</span><span class="sxs-lookup"><span data-stu-id="437c7-138">✔</span></span>            |                      <span data-ttu-id="437c7-139">✔</span><span class="sxs-lookup"><span data-stu-id="437c7-139">✔</span></span>                      |
| <span data-ttu-id="437c7-140">3人のユーザービュー</span><span class="sxs-lookup"><span data-stu-id="437c7-140">Third-person view</span></span>                    |            <span data-ttu-id="437c7-141">✔</span><span class="sxs-lookup"><span data-stu-id="437c7-141">✔</span></span>            |                      <span data-ttu-id="437c7-142">✔</span><span class="sxs-lookup"><span data-stu-id="437c7-142">✔</span></span>                      |
| <span data-ttu-id="437c7-143">画面にストリームできます</span><span class="sxs-lookup"><span data-stu-id="437c7-143">Can be streamed to screens</span></span>           |            <span data-ttu-id="437c7-144">✔</span><span class="sxs-lookup"><span data-stu-id="437c7-144">✔</span></span>            |                      <span data-ttu-id="437c7-145">✔</span><span class="sxs-lookup"><span data-stu-id="437c7-145">✔</span></span>                      |
| <span data-ttu-id="437c7-146">移植性があります。</span><span class="sxs-lookup"><span data-stu-id="437c7-146">Portable</span></span>                             |            <span data-ttu-id="437c7-147">✔</span><span class="sxs-lookup"><span data-stu-id="437c7-147">✔</span></span>            |                                             |
| <span data-ttu-id="437c7-148">ワイヤレス</span><span class="sxs-lookup"><span data-stu-id="437c7-148">Wireless</span></span>                             |            <span data-ttu-id="437c7-149">✔</span><span class="sxs-lookup"><span data-stu-id="437c7-149">✔</span></span>            |                                             |
| <span data-ttu-id="437c7-150">追加の必要なハードウェア</span><span class="sxs-lookup"><span data-stu-id="437c7-150">Additional required hardware</span></span>         |     <span data-ttu-id="437c7-151">Android フォン、iPhone</span><span class="sxs-lookup"><span data-stu-id="437c7-151">Android phone, iPhone</span></span>    | <span data-ttu-id="437c7-152">HoloLens + テストマシン + 三脚 + ビデオカメラ + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="437c7-152">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="437c7-153">ハードウェア投資</span><span class="sxs-lookup"><span data-stu-id="437c7-153">Hardware investment</span></span>                  |           <span data-ttu-id="437c7-154">Low</span><span class="sxs-lookup"><span data-stu-id="437c7-154">Low</span></span>            |                     <span data-ttu-id="437c7-155">高</span><span class="sxs-lookup"><span data-stu-id="437c7-155">High</span></span>                    |
| <span data-ttu-id="437c7-156">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="437c7-156">Cross-platform</span></span>                       |           <span data-ttu-id="437c7-157">Android、iOS</span><span class="sxs-lookup"><span data-stu-id="437c7-157">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="437c7-158">同期されたコンテンツ</span><span class="sxs-lookup"><span data-stu-id="437c7-158">Synchronized content</span></span>                 |            <span data-ttu-id="437c7-159">✔</span><span class="sxs-lookup"><span data-stu-id="437c7-159">✔</span></span>            |                      <span data-ttu-id="437c7-160">✔</span><span class="sxs-lookup"><span data-stu-id="437c7-160">✔</span></span>                      |
| <span data-ttu-id="437c7-161">ランタイムのセットアップ期間</span><span class="sxs-lookup"><span data-stu-id="437c7-161">Runtime setup duration</span></span>               |         <span data-ttu-id="437c7-162">リプレイ</span><span class="sxs-lookup"><span data-stu-id="437c7-162">Instant</span></span>          |                     <span data-ttu-id="437c7-163">スロー (低速)</span><span class="sxs-lookup"><span data-stu-id="437c7-163">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="437c7-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="437c7-164">See also</span></span>

* [<span data-ttu-id="437c7-165">複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="437c7-165">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="437c7-166">開発者向け複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="437c7-166">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="437c7-167">複合現実での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="437c7-167">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
