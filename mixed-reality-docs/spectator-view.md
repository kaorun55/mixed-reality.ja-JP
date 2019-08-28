---
title: Spectator ビュー
description: 外部ディスプレイで mixed reality エクスペリエンスをデモンストレーションする手段として、または mixed reality エクスペリエンスのビデオを録画する手段として、外部デバイスからホログラムを視覚化します。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator View、iPhone、iOS、iPad、OpenCV、カメラ、ARKit、HoloLens、Mixed Reality、MixedRealityToolkit、demo、record
ms.openlocfilehash: 708ed694af3769f16d5dce0595e026f9a348d754
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047174"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="d9b5b-104">HoloLens および HoloLens 用 Spectator ビュー2</span><span class="sxs-lookup"><span data-stu-id="d9b5b-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="d9b5b-106">概要</span><span class="sxs-lookup"><span data-stu-id="d9b5b-106">Overview</span></span>

<span data-ttu-id="d9b5b-107">HoloLens を装着すると、それを持っていない人は、可能な偉大なる象徴を体験することができなくなります。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="d9b5b-108">Spectator View を使用すると、他のユーザーは、世界で HoloLens ユーザーに表示される2D 画面で見ることができます。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="d9b5b-109">Spectator View は、モバイルデバイスで HD のホログラムを記録するための、高速で手頃な価格のアプローチを提供します。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="d9b5b-110">また、ビデオカメラを使用したホログラムの高品質記録も提供します。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-110">It also offers a professional quality recording of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="d9b5b-111">主要リソース</span><span class="sxs-lookup"><span data-stu-id="d9b5b-111">Key Resources</span></span>

* [<span data-ttu-id="d9b5b-112">**GitHub の Spectator ビュー**</span><span class="sxs-lookup"><span data-stu-id="d9b5b-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="d9b5b-113">**Spectator View のドキュメント**</span><span class="sxs-lookup"><span data-stu-id="d9b5b-113">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="d9b5b-114">**Spectator ビューのサンプル**</span><span class="sxs-lookup"><span data-stu-id="d9b5b-114">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="d9b5b-115">ユース ケース</span><span class="sxs-lookup"><span data-stu-id="d9b5b-115">Use Cases</span></span>
* <span data-ttu-id="d9b5b-116">IPhone または Android デバイスを使用して、mixed reality エクスペリエンスを記録できます。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-116">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="d9b5b-117">フル HD で記録し、ホログラムと偶数の影にアンチエイリアシングを適用します。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-117">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="d9b5b-118">これは、ホログラムのビデオをキャプチャする費用効果が高く、迅速な方法です。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-118">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="d9b5b-119">ライブ mixed reality エクスペリエンスを iPhone または iPad から直接 Apple TV にストリーミングし、すぐに利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-119">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="d9b5b-120">ゲストとのエクスペリエンスを共有します。非 HoloLens ユーザーが自分の電話やタブレットから直接ホログラムを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-120">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="d9b5b-121">現在の機能</span><span class="sxs-lookup"><span data-stu-id="d9b5b-121">Current Features</span></span>

* <span data-ttu-id="d9b5b-122">ホログラムの空間同期によって、すべてのユーザーが同じ場所でホログラムを確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-122">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="d9b5b-123">iOS (ARKit 対応デバイス) と Android (Arkit 対応デバイス) はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-123">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="d9b5b-124">複数の iOS ゲスト。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-124">Multiple iOS guests.</span></span>
<span data-ttu-id="d9b5b-125">ビデオ + ホログラム + アンビエントサウンド + ホログラムサウンドの記録。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-125">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="d9b5b-126">ビデオを保存したり、電子メールで送信したり、他のサポートアプリと共有したりできるように、シートを共有します。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-126">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="d9b5b-127">![](images/SpecViewPhoneDemo.jpg)
マーカーマーカー![マーカー](images/hololensspectatorview-500px.jpg) ![](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="d9b5b-127">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="d9b5b-128">次の表は、Spectator ビューのさまざまな機能とその機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-128">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="d9b5b-129">ビデオ記録のニーズに最適なオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-129">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="d9b5b-130">携帯</span><span class="sxs-lookup"><span data-stu-id="d9b5b-130">Mobile</span></span>                  |                    <span data-ttu-id="d9b5b-131">ビデオカメラ</span><span class="sxs-lookup"><span data-stu-id="d9b5b-131">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="d9b5b-132">HD 品質</span><span class="sxs-lookup"><span data-stu-id="d9b5b-132">HD quality</span></span>                           |         <span data-ttu-id="d9b5b-133">フル HD</span><span class="sxs-lookup"><span data-stu-id="d9b5b-133">Full HD</span></span>         |        <span data-ttu-id="d9b5b-134">Professional quality 撮影 (ビデオカメラによって決定)</span><span class="sxs-lookup"><span data-stu-id="d9b5b-134">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="d9b5b-135">カメラの移動を簡単に</span><span class="sxs-lookup"><span data-stu-id="d9b5b-135">Easy camera movement</span></span>                 |            <span data-ttu-id="d9b5b-136">✔</span><span class="sxs-lookup"><span data-stu-id="d9b5b-136">✔</span></span>            |                      <span data-ttu-id="d9b5b-137">✔</span><span class="sxs-lookup"><span data-stu-id="d9b5b-137">✔</span></span>                      |
| <span data-ttu-id="d9b5b-138">3人のユーザービュー</span><span class="sxs-lookup"><span data-stu-id="d9b5b-138">Third-person view</span></span>                    |            <span data-ttu-id="d9b5b-139">✔</span><span class="sxs-lookup"><span data-stu-id="d9b5b-139">✔</span></span>            |                      <span data-ttu-id="d9b5b-140">✔</span><span class="sxs-lookup"><span data-stu-id="d9b5b-140">✔</span></span>                      |
| <span data-ttu-id="d9b5b-141">画面にストリームできます</span><span class="sxs-lookup"><span data-stu-id="d9b5b-141">Can be streamed to screens</span></span>           |            <span data-ttu-id="d9b5b-142">✔</span><span class="sxs-lookup"><span data-stu-id="d9b5b-142">✔</span></span>            |                      <span data-ttu-id="d9b5b-143">✔</span><span class="sxs-lookup"><span data-stu-id="d9b5b-143">✔</span></span>                      |
| <span data-ttu-id="d9b5b-144">移植性があります。</span><span class="sxs-lookup"><span data-stu-id="d9b5b-144">Portable</span></span>                             |            <span data-ttu-id="d9b5b-145">✔</span><span class="sxs-lookup"><span data-stu-id="d9b5b-145">✔</span></span>            |                                             |
| <span data-ttu-id="d9b5b-146">ワイヤレス</span><span class="sxs-lookup"><span data-stu-id="d9b5b-146">Wireless</span></span>                             |            <span data-ttu-id="d9b5b-147">✔</span><span class="sxs-lookup"><span data-stu-id="d9b5b-147">✔</span></span>            |                                             |
| <span data-ttu-id="d9b5b-148">追加の必要なハードウェア</span><span class="sxs-lookup"><span data-stu-id="d9b5b-148">Additional required hardware</span></span>         |     <span data-ttu-id="d9b5b-149">Android フォン、iPhone</span><span class="sxs-lookup"><span data-stu-id="d9b5b-149">Android phone, iPhone</span></span>    | <span data-ttu-id="d9b5b-150">HoloLens + テストマシン + 三脚 + ビデオカメラ + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="d9b5b-150">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="d9b5b-151">ハードウェア投資</span><span class="sxs-lookup"><span data-stu-id="d9b5b-151">Hardware investment</span></span>                  |           <span data-ttu-id="d9b5b-152">Low</span><span class="sxs-lookup"><span data-stu-id="d9b5b-152">Low</span></span>            |                     <span data-ttu-id="d9b5b-153">高</span><span class="sxs-lookup"><span data-stu-id="d9b5b-153">High</span></span>                    |
| <span data-ttu-id="d9b5b-154">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="d9b5b-154">Cross-platform</span></span>                       |           <span data-ttu-id="d9b5b-155">Android、iOS</span><span class="sxs-lookup"><span data-stu-id="d9b5b-155">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="d9b5b-156">同期されたコンテンツ</span><span class="sxs-lookup"><span data-stu-id="d9b5b-156">Synchronized content</span></span>                 |            <span data-ttu-id="d9b5b-157">✔</span><span class="sxs-lookup"><span data-stu-id="d9b5b-157">✔</span></span>            |                      <span data-ttu-id="d9b5b-158">✔</span><span class="sxs-lookup"><span data-stu-id="d9b5b-158">✔</span></span>                      |
| <span data-ttu-id="d9b5b-159">ランタイムのセットアップ期間</span><span class="sxs-lookup"><span data-stu-id="d9b5b-159">Runtime setup duration</span></span>               |         <span data-ttu-id="d9b5b-160">リプレイ</span><span class="sxs-lookup"><span data-stu-id="d9b5b-160">Instant</span></span>          |                     <span data-ttu-id="d9b5b-161">スロー (低速)</span><span class="sxs-lookup"><span data-stu-id="d9b5b-161">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="d9b5b-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9b5b-162">See also</span></span>

* [<span data-ttu-id="d9b5b-163">複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="d9b5b-163">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="d9b5b-164">開発者向け複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="d9b5b-164">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="d9b5b-165">複合現実での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="d9b5b-165">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
