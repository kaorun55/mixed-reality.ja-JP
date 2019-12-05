---
title: Spectator View
description: 複合現実エクスペリエンスを外部ディスプレイでデモンストレーションしたり録画したりする手段として、外部デバイスからのホログラムを視覚化します。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, カメラ, ARKit, HoloLens, 複合現実, MixedRealityToolkit, デモ, 記録
ms.openlocfilehash: 9bc1c2809c7d780d439d9efb58f464b41de3dccd
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491165"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="62cff-104">HoloLens および HoloLens 2 向けの Spectator View</span><span class="sxs-lookup"><span data-stu-id="62cff-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="62cff-106">概要</span><span class="sxs-lookup"><span data-stu-id="62cff-106">Overview</span></span>

<span data-ttu-id="62cff-107">HoloLens を装着していると、自分が体験している素晴らしい世界を、HoloLens を装着していない人は見ることができないことをしばしば忘れてしまいます。</span><span class="sxs-lookup"><span data-stu-id="62cff-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="62cff-108">Spectator View を使用すれば、HoloLens ユーザーが見ている世界を他のユーザーが 2D 画面で見ることができます。</span><span class="sxs-lookup"><span data-stu-id="62cff-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="62cff-109">Spectator View は、モバイル デバイスを使用して HD でホログラムを記録するための高速で手頃な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="62cff-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="62cff-110">さらに、ビデオ カメラを使用したホログラムのプロ品質の録画も提供します。</span><span class="sxs-lookup"><span data-stu-id="62cff-110">It also offers a professional quality recording of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="62cff-111">重要なリソース</span><span class="sxs-lookup"><span data-stu-id="62cff-111">Key Resources</span></span>

* [<span data-ttu-id="62cff-112">**Spectator View (GitHub)** </span><span class="sxs-lookup"><span data-stu-id="62cff-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="62cff-113">**Spectator View のドキュメント**</span><span class="sxs-lookup"><span data-stu-id="62cff-113">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="62cff-114">**Spectator View のサンプル**</span><span class="sxs-lookup"><span data-stu-id="62cff-114">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="62cff-115">使用事例</span><span class="sxs-lookup"><span data-stu-id="62cff-115">Use Cases</span></span>
* <span data-ttu-id="62cff-116">iPhone または Android デバイスを使用して、複合現実エクスペリエンスを記録できます。</span><span class="sxs-lookup"><span data-stu-id="62cff-116">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="62cff-117">フル HD で記録し、ホログラムだけでなく、影にもアンチエイリアシングを適用します。</span><span class="sxs-lookup"><span data-stu-id="62cff-117">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="62cff-118">それは、ホログラムの動画をキャプチャするための費用対効果が高く、簡単に実行できる方法です。</span><span class="sxs-lookup"><span data-stu-id="62cff-118">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="62cff-119">複合現実エクスペリエンスを、iPhone または iPad から直接 Apple TV にライブ ストリーミングします。遅延は発生しません。</span><span class="sxs-lookup"><span data-stu-id="62cff-119">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="62cff-120">ゲストとエクスペリエンスを共有します。非 HoloLens ユーザーが各自の電話やタブレットから直接ホログラムを体験できるようにします。</span><span class="sxs-lookup"><span data-stu-id="62cff-120">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="62cff-121">現在の機能</span><span class="sxs-lookup"><span data-stu-id="62cff-121">Current Features</span></span>

* <span data-ttu-id="62cff-122">ホログラムの空間同期。これにより、すべてのユーザーが同じ場所でホログラムを確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="62cff-122">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="62cff-123">iOS (ARKit 対応デバイス) と Android (ARCore 対応デバイス) のサポート。</span><span class="sxs-lookup"><span data-stu-id="62cff-123">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="62cff-124">複数の iOS ゲスト。</span><span class="sxs-lookup"><span data-stu-id="62cff-124">Multiple iOS guests.</span></span>
<span data-ttu-id="62cff-125">動画 + ホログラム + 周囲の音 + ホログラムの音の記録。</span><span class="sxs-lookup"><span data-stu-id="62cff-125">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="62cff-126">シートを共有して、動画を保存したり、電子メールで送信したり、他のサポート アプリと共有したりできるようにします。</span><span class="sxs-lookup"><span data-stu-id="62cff-126">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="62cff-127">![マーカー](images/SpecViewPhoneDemo.jpg)
![マーカー](images/hololensspectatorview-500px.jpg) ![マーカー](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="62cff-127">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="62cff-128">次の表に、Spectator View のさまざまな機能を示します。</span><span class="sxs-lookup"><span data-stu-id="62cff-128">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="62cff-129">ご自分の録画のニーズに最適なオプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="62cff-129">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="62cff-130">モバイル</span><span class="sxs-lookup"><span data-stu-id="62cff-130">Mobile</span></span>                  |                    <span data-ttu-id="62cff-131">ビデオ カメラ</span><span class="sxs-lookup"><span data-stu-id="62cff-131">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="62cff-132">HD 品質</span><span class="sxs-lookup"><span data-stu-id="62cff-132">HD quality</span></span>                           |         <span data-ttu-id="62cff-133">フル HD</span><span class="sxs-lookup"><span data-stu-id="62cff-133">Full HD</span></span>         |        <span data-ttu-id="62cff-134">プロ品質の撮影 (ビデオ カメラによって決定される)</span><span class="sxs-lookup"><span data-stu-id="62cff-134">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="62cff-135">カメラの容易な移動</span><span class="sxs-lookup"><span data-stu-id="62cff-135">Easy camera movement</span></span>                 |            <span data-ttu-id="62cff-136">✔</span><span class="sxs-lookup"><span data-stu-id="62cff-136">✔</span></span>            |                      <span data-ttu-id="62cff-137">✔</span><span class="sxs-lookup"><span data-stu-id="62cff-137">✔</span></span>                      |
| <span data-ttu-id="62cff-138">第三者の視点</span><span class="sxs-lookup"><span data-stu-id="62cff-138">Third-person view</span></span>                    |            <span data-ttu-id="62cff-139">✔</span><span class="sxs-lookup"><span data-stu-id="62cff-139">✔</span></span>            |                      <span data-ttu-id="62cff-140">✔</span><span class="sxs-lookup"><span data-stu-id="62cff-140">✔</span></span>                      |
| <span data-ttu-id="62cff-141">画面にストリーム可能</span><span class="sxs-lookup"><span data-stu-id="62cff-141">Can be streamed to screens</span></span>           |            <span data-ttu-id="62cff-142">✔</span><span class="sxs-lookup"><span data-stu-id="62cff-142">✔</span></span>            |                      <span data-ttu-id="62cff-143">✔</span><span class="sxs-lookup"><span data-stu-id="62cff-143">✔</span></span>                      |
| <span data-ttu-id="62cff-144">移植性があります。</span><span class="sxs-lookup"><span data-stu-id="62cff-144">Portable</span></span>                             |            <span data-ttu-id="62cff-145">✔</span><span class="sxs-lookup"><span data-stu-id="62cff-145">✔</span></span>            |                                             |
| <span data-ttu-id="62cff-146">ワイヤレス</span><span class="sxs-lookup"><span data-stu-id="62cff-146">Wireless</span></span>                             |            <span data-ttu-id="62cff-147">✔</span><span class="sxs-lookup"><span data-stu-id="62cff-147">✔</span></span>            |                                             |
| <span data-ttu-id="62cff-148">必要な追加のハードウェア</span><span class="sxs-lookup"><span data-stu-id="62cff-148">Additional required hardware</span></span>         |     <span data-ttu-id="62cff-149">Android フォン、iPhone</span><span class="sxs-lookup"><span data-stu-id="62cff-149">Android phone, iPhone</span></span>    | <span data-ttu-id="62cff-150">HoloLens + リグ + 三脚 + ビデオ カメラ + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="62cff-150">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="62cff-151">ハードウェア投資</span><span class="sxs-lookup"><span data-stu-id="62cff-151">Hardware investment</span></span>                  |           <span data-ttu-id="62cff-152">低</span><span class="sxs-lookup"><span data-stu-id="62cff-152">Low</span></span>            |                     <span data-ttu-id="62cff-153">高</span><span class="sxs-lookup"><span data-stu-id="62cff-153">High</span></span>                    |
| <span data-ttu-id="62cff-154">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="62cff-154">Cross-platform</span></span>                       |           <span data-ttu-id="62cff-155">Android、iOS</span><span class="sxs-lookup"><span data-stu-id="62cff-155">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="62cff-156">同期されるコンテンツ</span><span class="sxs-lookup"><span data-stu-id="62cff-156">Synchronized content</span></span>                 |            <span data-ttu-id="62cff-157">✔</span><span class="sxs-lookup"><span data-stu-id="62cff-157">✔</span></span>            |                      <span data-ttu-id="62cff-158">✔</span><span class="sxs-lookup"><span data-stu-id="62cff-158">✔</span></span>                      |
| <span data-ttu-id="62cff-159">ランタイムのセットアップ期間</span><span class="sxs-lookup"><span data-stu-id="62cff-159">Runtime setup duration</span></span>               |         <span data-ttu-id="62cff-160">即時</span><span class="sxs-lookup"><span data-stu-id="62cff-160">Instant</span></span>          |                     <span data-ttu-id="62cff-161">スロー (低速)</span><span class="sxs-lookup"><span data-stu-id="62cff-161">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="62cff-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="62cff-162">See also</span></span>

* [<span data-ttu-id="62cff-163">複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="62cff-163">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="62cff-164">開発者向け複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="62cff-164">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="62cff-165">複合現実での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="62cff-165">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
