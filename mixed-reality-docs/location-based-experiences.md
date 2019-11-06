---
title: Windows Mixed Reality を使用した場所ベースのエンターテインメント
description: Unity の基になる Holographic ネイティブオブジェクトへのアクセスを取得します。
author: jessemcculloch
ms.author: ishitak
ms.date: 08/22/2019
ms.topic: article
keywords: mixed reality、vr、lbe、場所
ms.openlocfilehash: de9cfdaca77574bbbbec96c2e94fddeaa2712c33
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437935"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a><span data-ttu-id="e20c1-104">Windows Mixed Reality を使用した場所ベースのエンターテインメント</span><span class="sxs-lookup"><span data-stu-id="e20c1-104">Location Based Entertainment with Windows Mixed Reality</span></span>

<span data-ttu-id="e20c1-105">ここ数年で、場所ベースのエンターテインメントカテゴリにおいて非常に多くの成長とイノベーションを促進ました。</span><span class="sxs-lookup"><span data-stu-id="e20c1-105">In the last couple of years, we have witnessed an incredible amount of growth and innovation in the Location Based Entertainment category.</span></span> <span data-ttu-id="e20c1-106">テーマの公園や theatres などの従来の会場は、既存のサービスやインストールに対する優れたエクスペリエンスとして、イマーシブ、マルチプレーヤーエクスペリエンスを提供するようになりました。</span><span class="sxs-lookup"><span data-stu-id="e20c1-106">Traditional venues like theme parks and theatres have started offering immersive, multi-player experiences as complimentary experiences to existing rides and installations.</span></span> <span data-ttu-id="e20c1-107">新しいオペレーターと会場は、一意のマルチ sensorial、マルチプレーヤーエクスペリエンスを、大量に魅力的な価格でもたらします。</span><span class="sxs-lookup"><span data-stu-id="e20c1-107">New operators and venues are bringing unique multi-sensorial, multi-player experiences at an attractive price to the masses.</span></span> <span data-ttu-id="e20c1-108">これらのすべてのエクスペリエンスでは、mixed reality でできることについて、エンベロープをプッシュしています。</span><span class="sxs-lookup"><span data-stu-id="e20c1-108">All of these experiences are pushing the envelope for what’s possible with mixed reality.</span></span>

<span data-ttu-id="e20c1-109">このドキュメントは、[場所ベースのエンターテインメント] カテゴリで Windows Mixed Reality の使用を開始するためのガイドです。</span><span class="sxs-lookup"><span data-stu-id="e20c1-109">This document is a guide to get started with Windows Mixed Reality in the Location Based Entertainment category.</span></span> <span data-ttu-id="e20c1-110">以下のガイダンスは、トレーニング、製品設計、またはその他のユースケースなど、エンターテインメント以外の場所ベースのエクスペリエンスにも適用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-110">The guidance below may additionally be applicable to location-based experiences beyond entertainment such as training, product design or other use cases.</span></span>

## <a name="engineering-faq"></a><span data-ttu-id="e20c1-111">エンジニアリングに関する FAQ</span><span class="sxs-lookup"><span data-stu-id="e20c1-111">Engineering FAQ</span></span>

### <a name="hardware"></a><span data-ttu-id="e20c1-112">ハードウェア</span><span class="sxs-lookup"><span data-stu-id="e20c1-112">Hardware</span></span>

<span data-ttu-id="e20c1-113">**Q: Microsoft とそのパートナーがセットアップで使用できるハードウェアはどのようなものですか。**</span><span class="sxs-lookup"><span data-stu-id="e20c1-113">**Q: What hardware is available from Microsoft and its partners that I can use in my setup?**</span></span>

<span data-ttu-id="e20c1-114">A: Microsoft とその OEM パートナーは、ニーズに応じて選択する、説得力のあるデバイスのポートフォリオを提供します。</span><span class="sxs-lookup"><span data-stu-id="e20c1-114">A: Microsoft and its OEM partners offer a compelling portfolio of devices to choose from depending on your needs.</span></span>  

<span data-ttu-id="e20c1-115">お客様に提供しているエクスペリエンスで仮想現実のヘッドセットが必要な場合は、HP、Samsung、および Acer の次の市場にあるヘッドセットが非常に適しています。</span><span class="sxs-lookup"><span data-stu-id="e20c1-115">If the experiences you’re providing to your customers require virtual reality headsets, the following in-market headsets from HP, Samsung and Acer are a great fit.</span></span> <span data-ttu-id="e20c1-116">各ヘッドセットには独自の区別された属性があります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-116">Each headset has their own differentiated attributes.</span></span> <span data-ttu-id="e20c1-117">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e20c1-117">More details on each below.</span></span>

<span data-ttu-id="e20c1-118">HP リバーブ:[詳細](https://hp.com/go/Reverbpro)</span><span class="sxs-lookup"><span data-stu-id="e20c1-118">HP Reverb: [Details](https://hp.com/go/Reverbpro)</span></span>

<span data-ttu-id="e20c1-119">Samsung Odyssey +: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span><span class="sxs-lookup"><span data-stu-id="e20c1-119">Samsung Odyssey+: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span></span>

<span data-ttu-id="e20c1-120">Acer:[詳細](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span><span class="sxs-lookup"><span data-stu-id="e20c1-120">Acer: [Details](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span></span>

<span data-ttu-id="e20c1-121">お客様の場所が、表示ヘッドセットの使用を必要とする、混合または拡張された現実のエクスペリエンスを専門としている場合は、Microsoft HoloLens 2 を調達することができます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-121">If your location specializes in mixed or augmented reality experiences requiring the use of a see-through headset, you can procure the Microsoft HoloLens 2 (now open for pre-order interest).</span></span>  

<span data-ttu-id="e20c1-122">HoloLens 2:[注文前の関心](https://www.microsoft.com//hololens/buy)</span><span class="sxs-lookup"><span data-stu-id="e20c1-122">HoloLens 2: [Pre-order interest](https://www.microsoft.com//hololens/buy)</span></span>

<span data-ttu-id="e20c1-123">高度なコンピュータービジョン、音声、および本文の追跡を必要とするエクスペリエンスを試している場合、ニーズに合わせて Azure Kinect DK を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-123">If you’re experimenting with experiences that require advanced computer vision, speech and body tracking, you may find the Azure Kinect DK a fit for your needs.</span></span>  

<span data-ttu-id="e20c1-124">Azure Kinect:[詳細](https://azure.microsoft.com//services/kinect-dk/)</span><span class="sxs-lookup"><span data-stu-id="e20c1-124">Azure Kinect: [Details](https://azure.microsoft.com//services/kinect-dk/)</span></span>

<span data-ttu-id="e20c1-125">**Q: PC-テザリングさ VR エクスペリエンスを実行するために使用できる backpack Pc のポートフォリオは何ですか。**</span><span class="sxs-lookup"><span data-stu-id="e20c1-125">**Q: What is the portfolio of backpack PCs I can use to run my PC-tethered VR experiences?**</span></span>

<span data-ttu-id="e20c1-126">PC-テザリングさ VR エクスペリエンスの場合、Oem は、ニーズに応じて正確に構築された backpack Pc を非常に優れた選択肢として提供しています。</span><span class="sxs-lookup"><span data-stu-id="e20c1-126">For PC-tethered VR experiences, our OEMs offer an incredible selection of backpack PCs built exactly for that need.</span></span>

<span data-ttu-id="e20c1-127">HP は HP VR backpack G2 を起動しました。これは、無料ローミングエクスペリエンスのために最適化された、現在のところ、RTX 2080 GPU では30% 向上しています。</span><span class="sxs-lookup"><span data-stu-id="e20c1-127">HP just launched their HP VR backpack G2, the world’s most powerful wearable PC – optimized for free-roam experiences, now with 30% more power with an RTX 2080 GPU inside.</span></span> [<span data-ttu-id="e20c1-128">詳細</span><span class="sxs-lookup"><span data-stu-id="e20c1-128">Details</span></span>](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a><span data-ttu-id="e20c1-129">[セットアップ]</span><span class="sxs-lookup"><span data-stu-id="e20c1-129">Setup</span></span>

<span data-ttu-id="e20c1-130">**Q: セットアップを簡単に構成し、LBE 用に Mixed Reality ポータルをカスタマイズするにはどうすればよいですか。**</span><span class="sxs-lookup"><span data-stu-id="e20c1-130">**Q: How can I more easily configure setup and customize the Mixed Reality Portal for LBE?**</span></span>

>[!NOTE]
><span data-ttu-id="e20c1-131">この機能には、バージョン2000.19061.1011.0 以上が必要です。</span><span class="sxs-lookup"><span data-stu-id="e20c1-131">This feature requires version 2000.19061.1011.0 or greater.</span></span>  

<span data-ttu-id="e20c1-132">アプリをキオスクまたはカスタマイズされたエクスペリエンスにデプロイするためにアプリで通常利用できるものよりも、混合の現実ポータルのカスタマイズが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-132">You may find that you need more customization of Mixed Reality Portal than is normally available through the app for deploying apps to kiosks or customized experiences.</span></span> <span data-ttu-id="e20c1-133">最新の7月の Mixed Reality ポータルの更新では、構成ファイルを使用して次の操作を行うことができるいくつかの詳細設定がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e20c1-133">The latest July update of Mixed Reality Portal supports several advanced settings that can be via a configuration file to do the following:</span></span>  

<span data-ttu-id="e20c1-134">[失敗したシステムチェックを許可する] –セットアップを完了する前に、セットアッププロセスによって、PC が Windows Mixed Reality との互換性を確認します。</span><span class="sxs-lookup"><span data-stu-id="e20c1-134">Allow failed system checks – normally the setup process checks the PC for compatibility with Windows Mixed Reality before completing setup.</span></span> <span data-ttu-id="e20c1-135">これを回避すると、互換性の問題がある場合に Windows Mixed Reality を実行しようとすると問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-135">Bypassing this may cause issues when trying to run Windows Mixed Reality if there are compatibility issues.</span></span>  

<span data-ttu-id="e20c1-136">デバイスコンパニオンアプリのスキップ– DCA は製造元によって提供されるヘッドセット固有のセットアップ手順を提供し、ヘッドセットのファームウェアを更新できます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-136">Skip Device Companion App – the DCA provides headset-specific setup steps provided by the manufacturer and allows for updating the headset’s firmware.</span></span>  

<span data-ttu-id="e20c1-137">ルームのセットアップをスキップする–部屋の境界を作成するように求めるメッセージが表示されるのではなく、固定モードまたはスタンバイモードのヘッドセットに直接進むことができます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-137">Skip room setup – instead of being prompted to create a room boundary, you can proceed directly into the headset in Seated/Standing mode.</span></span>  

<span data-ttu-id="e20c1-138">ストアからのアプリのインストールをスキップする-標準セットアップでは、3D ビューアーと Edge 360 ビューアーアドオンを含む、いくつかのストアアプリがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-138">Skip installing apps from the Store - normal setup installs several Store apps including 3D Viewer and the Edge 360 Viewer add-on.</span></span> <span data-ttu-id="e20c1-139">これにより、これらのアプリのインストールはスキップされますが、デバイスの機能が不足している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-139">This will skip the install of these apps, but you may be missing device functionality.</span></span>  

<span data-ttu-id="e20c1-140">全画面表示でプレビューを表示する: 混合 Reality ポータルでは、ヘッドセットが使用されている間、デスクトップ PC に全画面表示でヘッドセットのプレビューが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-140">Show preview in full screen – Mixed Reality Portal will default to showing the headset preview in full-screen on the desktop PC while the headset is in use.</span></span>  

<span data-ttu-id="e20c1-141">サイドパネルの [新規] を非表示にします。これにより、Mixed Reality ポータルの起動時にパネルの新しいが拡張されるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-141">Hide New for you side panel – this prevent the New for you panel from being expanded on launch of Mixed Reality Portal.</span></span>  

#### <a name="how-to-configure"></a><span data-ttu-id="e20c1-142">構成方法:</span><span class="sxs-lookup"><span data-stu-id="e20c1-142">How to configure:</span></span>  

<span data-ttu-id="e20c1-143">これらの構成のいずれかを設定するには、次のディレクトリに LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState という名前のファイルを作成する必要が_あります:_ _$env:\\_</span><span class="sxs-lookup"><span data-stu-id="e20c1-143">To set any of these configurations, you need to create a file called _UserConfig.json_ under this directory: _$env:LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="e20c1-144">ほとんどのユーザーにとって、これは_C:\Users\<username > \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState_のようになり\\</span><span class="sxs-lookup"><span data-stu-id="e20c1-144">For most users this will look like _C:\Users\<username>\AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="e20c1-145">JSON ファイルの内容は、有効にする上記の設定のいずれかに対して "true" が設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-145">The JSON file should have the below contents with “true” set for any of the above settings you want enabled:</span></span>  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
<span data-ttu-id="e20c1-146">**Q: playspace の構成についてのガイダンスはありますか。**</span><span class="sxs-lookup"><span data-stu-id="e20c1-146">**Q: Is there any guidance on configuring the playspace?**</span></span>

<span data-ttu-id="e20c1-147">A: playspace の構成は、コンシューマーのセットアップエクスペリエンスの場合と同じように行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-147">A: Configuring a playspace should be done as you would with a consumer setup experience.</span></span> <span data-ttu-id="e20c1-148">ルームのセットアッププロセスでは、部屋の境界を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-148">The Room Setup process will also let you define your room boundaries.</span></span> <span data-ttu-id="e20c1-149">ルーム境界の構成の詳細については、[こちら](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e20c1-149">More details on configuring room boundaries can be read [here](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="e20c1-150">上のドキュメントで説明したように、最大の適正な1座標の再生領域は5mx5m を中心にしています。</span><span class="sxs-lookup"><span data-stu-id="e20c1-150">As discussed in the above document the maximum reasonable single coordinate playspace is around 5mx5m.</span></span> <span data-ttu-id="e20c1-151">より大きな領域を作成する場合は、Windows Holographic API スタックで空間アンカー機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-151">If you want to have a larger area you can make use of the Spatial Anchors capability in the Windows Holographic API stack.</span></span> <span data-ttu-id="e20c1-152">この API を使用するには、生成するエクスペリエンスにカスタムエンジニアリングが必要です。</span><span class="sxs-lookup"><span data-stu-id="e20c1-152">Using this API will require custom engineering in the experiences you are producing.</span></span>  

<span data-ttu-id="e20c1-153">さまざまな領域サイズに合わせてコンテンツを最適化する方法の詳細については、[こちら](https://docs.microsoft.com//windows/mixed-reality/coordinate-systems)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e20c1-153">More details on how to optimize your content for different space sizes can be read [here](https://docs.microsoft.com//windows/mixed-reality/coordinate-systems).</span></span>
 

<span data-ttu-id="e20c1-154">**Q: 空間が大きすぎて、境界を使用して継続的なエクスペリエンスを設定しようとしたときにエラーが発生しています。大規模な無料のローミングエクスペリエンスを設定するにはどうすればよいですか。**</span><span class="sxs-lookup"><span data-stu-id="e20c1-154">**Q: My space is too large and I’m running into errors when I try to set up a Standing experience with boundaries. What should I do to setup my large free-roam experience work?**</span></span>

<span data-ttu-id="e20c1-155">A: ~ 18xft を超える領域をセットアップする場合、システムによって提供される境界を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="e20c1-155">A: To setup a larger space than ~18x18ft you won’t be able to use the boundary experience provided by the system.</span></span>  <span data-ttu-id="e20c1-156">境界システムは、1つの固定座標 "アンカー" を利用することに依存しています。これは、中央のステージアンカーから離れすぎていると不安定になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-156">The boundary systems relies on leveraging a single fixed coordinate “anchor”, which can become unstable when a user is too far from the center stage anchor.</span></span> 

<span data-ttu-id="e20c1-157">代わりに、"固定" モードを設定できます。このモードでは、境界が表示されず、ステージの境界や再生スペースも構成されません。</span><span class="sxs-lookup"><span data-stu-id="e20c1-157">Instead, you can setup “seated” mode, which will not display the boundary or configure a stage bounds or playspace.</span></span>  <span data-ttu-id="e20c1-158">次に、物理的な境界領域を参照するように、アプリ内に複数の空間アンカーを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-158">Then, you’ll need to configure multiple spatial anchors within the app to reference physical boundary areas.</span></span> 

<span data-ttu-id="e20c1-159">アプリケーション開発者は、ユーザーが物理的な環境と競合しないように、必要なセーフガードを表示する責任があります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-159">The application developer is responsible to display necessary safeguards so that users don’t collide with physical surroundings.</span></span>  <span data-ttu-id="e20c1-160">これらは、エクスペリエンス内のデジタル壁面や、カスタマイズされたゲームの境界ビジュアルです。</span><span class="sxs-lookup"><span data-stu-id="e20c1-160">These could be digital walls within the experience or a customized game boundary visual.</span></span> 

<span data-ttu-id="e20c1-161">WMR を使用したルーム境界の設定に関するガイダンスについては、[こちら](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e20c1-161">Guidance on setting up the room boundary with WMR can be found [here](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="e20c1-162">**Q: playspace の起点はどこですか。**</span><span class="sxs-lookup"><span data-stu-id="e20c1-162">**Q: Where is the origin of the playspace?**</span></span>

<span data-ttu-id="e20c1-163">A: playspace の原点は、セットアップ中にセンターボタンが押されたときに、ルームのセットアップエクスペリエンスによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-163">A: The origin of the playspace is determined by the Room Setup experience, more specifically the HMD position when the Center button is pressed during setup.</span></span> 

### <a name="multi-player-setup"></a><span data-ttu-id="e20c1-164">マルチプレーヤーセットアップ</span><span class="sxs-lookup"><span data-stu-id="e20c1-164">MULTI-PLAYER SETUP</span></span>

<span data-ttu-id="e20c1-165">**Q: 自分の会場で、マルチプレーヤーエクスペリエンスをデプロイしています。Windows Mixed Reality ではサポートされていますか。**</span><span class="sxs-lookup"><span data-stu-id="e20c1-165">**Q: I’m deploying a multi-player experience in at my venue. Is that supported on Windows Mixed Reality?**</span></span>

<span data-ttu-id="e20c1-166">A: Mixed Reality 空間データパッケージャーツールは、1台の PC から別の PC への空間データの移植を可能にすることで、同じ領域内で複数のプレーヤーをローカライズできるようにするベータ機能です。</span><span class="sxs-lookup"><span data-stu-id="e20c1-166">A: The Mixed Reality Spatial Data Packager tool is a beta feature that allows localizing multiple players in the same space by enabling porting of the spatial data from one PC to another.</span></span> <span data-ttu-id="e20c1-167">ツールにアクセスして、その詳細については、[こちら](mixedrealityspatialdatapackager.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e20c1-167">You can access the tool and learn more about it [here](mixedrealityspatialdatapackager.md).</span></span>

<span data-ttu-id="e20c1-168">( [Insider](https://docs.microsoft.com//windows-insider/at-home/get-started)プログラムを使用して) Windows 20H1 以降のビルドを選択すると、マップ共有用の新しいインターフェイスにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-168">If you opt into the Windows 20H1 or later builds (via our [Insider](https://docs.microsoft.com//windows-insider/at-home/get-started) program) you can access a new interface for map sharing.</span></span> <span data-ttu-id="e20c1-169">この新しい機能は、Windows デバイスポータルのマップマネージャーインターフェイスを使用して入手できます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-169">This new functionality is available via the Map Manager interface of the Windows Device portal.</span></span> <span data-ttu-id="e20c1-170">このツールを使用するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e20c1-170">To use this tool follow these steps:</span></span>
- <span data-ttu-id="e20c1-171">20H1 以降を選択していることを確認します (2019 年9月の時点では、Insider プログラムを使用しています)。</span><span class="sxs-lookup"><span data-stu-id="e20c1-171">Make sure you are opted into 20H1 or later (as of September 2019 this means using our Insider program)</span></span>
- <span data-ttu-id="e20c1-172">Windows デバイスポータル (WDP) を有効にします。手順については、[こちらをご覧ください](https://docs.microsoft.com//windows/uwp/debug-test-perf/device-portal-desktop)。</span><span class="sxs-lookup"><span data-stu-id="e20c1-172">Enable the Windows Device Portal (WDP), instructions are [here](https://docs.microsoft.com//windows/uwp/debug-test-perf/device-portal-desktop)</span></span>
- <span data-ttu-id="e20c1-173">既存のマップをダウンロードするか、新しいマップをインポートする Windows Mixed Reality HMD をプラグインします。</span><span class="sxs-lookup"><span data-stu-id="e20c1-173">Plug in a Windows Mixed Reality HMD that you wish to either download an existing map from or import a new map</span></span>
- <span data-ttu-id="e20c1-174">[設定] 画面で指定した URL を使用して、選択したブラウザーの WDP に移動します。</span><span class="sxs-lookup"><span data-stu-id="e20c1-174">Navigate to the WDP in your browser of choice using the URL provided in the settings screen.</span></span> 
  - <span data-ttu-id="e20c1-175">その後、"Mixed Reality" セクションに移動し、[マップマネージャー] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e20c1-175">Once there Navigate to the "Mixed Reality" section and select "Map Manager".</span></span> 
  - <span data-ttu-id="e20c1-176">[ダウンロード] ボタンを使用して、コンピューターから既存のマップをエクスポートできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e20c1-176">You can now use the "Download" button to export an existing map from the machine.</span></span> 
  - <span data-ttu-id="e20c1-177">[マップファイルのアップロード] ボタンを使用すると、以前のエクスポートからマップをインポートできます (おそらく、別のコンピューターにあります)。</span><span class="sxs-lookup"><span data-stu-id="e20c1-177">You can use the "Upload a map file" button to import an map from a previous export (perhaps on a different machine).</span></span> 
  - <span data-ttu-id="e20c1-178">"Import" を使用して、システムがこのコンピューター上のこの HMD に対してこのマップを使用できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-178">You can use "Import" to enable the system to use that map for this HMD on this machine.</span></span>
  
### <a name="tracking"></a><span data-ttu-id="e20c1-179">追跡</span><span class="sxs-lookup"><span data-stu-id="e20c1-179">TRACKING</span></span>

<span data-ttu-id="e20c1-180">Q: Windows Mixed Reality ヘッドセットの追跡テクノロジはどのように動作しますか。</span><span class="sxs-lookup"><span data-stu-id="e20c1-180">Q: How does the tracking technology in the Windows Mixed Reality headsets work?</span></span>  

<span data-ttu-id="e20c1-181">Mixed Reality は、HoloLens と同じ追跡テクノロジを共有します。</span><span class="sxs-lookup"><span data-stu-id="e20c1-181">Mixed Reality shares the same tracking technology as the HoloLens.</span></span> <span data-ttu-id="e20c1-182">内部アウト追跡システムの詳細については、[こちら](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/tracking-system)のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e20c1-182">To learn more about the inside-out tracking system, check out the documentation [here](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/tracking-system).</span></span>

<span data-ttu-id="e20c1-183">上位レベルの空間マッピングシステムの動作の詳細については、[こちらで](spatial-mapping.md)説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e20c1-183">For a description of how the higher-level spatial mapping system works you can read our description [here](spatial-mapping.md).</span></span>

<span data-ttu-id="e20c1-184">**Q: reliable tracking ボリュームを取得するためのベストプラクティスはありますか。**</span><span class="sxs-lookup"><span data-stu-id="e20c1-184">**Q: Are there any best practices for getting a reliable tracking volume?**</span></span>

<span data-ttu-id="e20c1-185">成功を追跡するために環境を最適に構成するには、この[投稿](environment-considerations-for-hololens.md)のベストプラクティスを読むことができます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-185">To best configure the environment for tracking success, you can read best practices in this [post](environment-considerations-for-hololens.md).</span></span>

<span data-ttu-id="e20c1-186">**Q: ウェアハウスでの追跡には特定の差異がありますか? スケールスペースや最適化を検討してください。**</span><span class="sxs-lookup"><span data-stu-id="e20c1-186">**Q: Are there any specific nuances with tracking in warehouse-scale spaces or optimizations to consider?**</span></span>

<span data-ttu-id="e20c1-187">A: 次のプラクティスは、より信頼性の高い追跡ボリュームを取得するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-187">A: The following practices can help with getting a more reliable tracking volume:</span></span>  

<span data-ttu-id="e20c1-188">複数の位置で重なり合ったさまざまな機能を部屋に用意することで、追跡システムの堅牢なロックを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-188">Providing a variety of features in the room that overlap at multiple positions will help the tracking system get a solid lock.</span></span> <span data-ttu-id="e20c1-189">単色の輪郭スタイルの線を使用するのではなく、ランダムな描画の splatters と陰影を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="e20c1-189">Think of random paint splatters and hatching rather than using solid contour style lines.</span></span> 

<span data-ttu-id="e20c1-190">可能な場合は、領域内の照明の動的範囲を最小化します。</span><span class="sxs-lookup"><span data-stu-id="e20c1-190">Minimize the dynamic range of lighting in your area where possible.</span></span> <span data-ttu-id="e20c1-191">混合現実 HMDs の追跡カメラは、HDR ではなく、AGC (自動利得) と AEC (自動露出) があるため、さまざまな照明を扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-191">The tracking cameras on our Mixed Reality HMDs are not HDR and have AGC (auto gain) and AEC (auto exposure) going in order to deal with different lighting.</span></span> <span data-ttu-id="e20c1-192">表面光、パターン、およびコントラストの分布によっては、AGC または AEC によって、ほぼすべての白または黒の部屋にいることがわかっている場合があります。これにより、反対の "色" の機能が薄く表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-192">Depending on the distribution of surface light, patterns and contrast, either AGC or AEC may conclude you’re in a pretty much all white or black room which can wash out your features that may be in the opposite “color”.</span></span> <span data-ttu-id="e20c1-193">明るい日光を持つ外部ウィンドウの前に内部の画像を撮影しようとしているときに、露出を調整して詳細を見ることができるようにした場合、内部のすべてのものは underexposed と黒色になります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-193">If you are trying to take an interior picture in front of an exterior window with bright daylight behind and you adjust exposure so you can see detail outside, then everything on the interior is underexposed and black.</span></span> <span data-ttu-id="e20c1-194">または、内に設定されている場合、以外のすべてが overexposed、すべて白になります。</span><span class="sxs-lookup"><span data-stu-id="e20c1-194">Or if set for inside, then everything outside is now overexposed and all white.</span></span>  

<span data-ttu-id="e20c1-195">トラックカメラの発生が、追跡カメラの AEC/AGC を混乱させる可能性がある場合に、表示される部屋 (オーバーヘッド) にスポットライト。</span><span class="sxs-lookup"><span data-stu-id="e20c1-195">Spotlights in a room (even overhead) that are in view if tracking cameras can sometimes be culprits which confuse the AEC/AGC of the tracking cameras.</span></span> <span data-ttu-id="e20c1-196">フラット/拡散照明が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-196">Flat/diffused lighting helps.</span></span>  

### <a name="mixed-reality-cloud-services-and-azure"></a><span data-ttu-id="e20c1-197">MIXED REALITY クラウドサービスと AZURE</span><span class="sxs-lookup"><span data-stu-id="e20c1-197">MIXED REALITY CLOUD SERVICES AND AZURE</span></span> 

<span data-ttu-id="e20c1-198">**Q: どのようにしてビジネススケールを Microsoft Azure できますか。**</span><span class="sxs-lookup"><span data-stu-id="e20c1-198">**Q: How can Microsoft Azure help my business scale?**</span></span>

<span data-ttu-id="e20c1-199">A: Azure ベースのオンサイトおよびリモート管理を使用すると、ビジネスをデータ主導にすることができ、運用コストが削減され、既存の場所と新しい場所でのデプロイをスケーリングできます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-199">A: Azure based onsite and remote management can help your business be data-driven, reduce operational costs and scale deployment across existing and new locations.</span></span> <span data-ttu-id="e20c1-200">Azure Storage、Azure Functions、App Service、Azure ネットワーク、IOT Hub などの azure クラウドサービスは、次のユースケースに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-200">Azure cloud services such as Azure Storage, Azure Functions, App Service, Azure Networking and IOT Hub can help with the following use cases:</span></span>  

<span data-ttu-id="e20c1-201">リモートデバイス展開 & 管理</span><span class="sxs-lookup"><span data-stu-id="e20c1-201">Remote Device Deployment & Management</span></span> 

<span data-ttu-id="e20c1-202">リアルタイムのオンサイト分析</span><span class="sxs-lookup"><span data-stu-id="e20c1-202">Real Time Onsite Analytics</span></span> 

<span data-ttu-id="e20c1-203">インテリジェントな適応性に優れたゲームプレイ</span><span class="sxs-lookup"><span data-stu-id="e20c1-203">Intelligent Adaptable LBE Gameplay</span></span> 

<span data-ttu-id="e20c1-204">LBE コンテンツのストリーミングとデプロイ</span><span class="sxs-lookup"><span data-stu-id="e20c1-204">LBE Content Streaming and Deployment</span></span> 

<span data-ttu-id="e20c1-205">LBE プレーヤーの基本設定ヒートマップ</span><span class="sxs-lookup"><span data-stu-id="e20c1-205">LBE Player Preference Heatmap</span></span> 

<span data-ttu-id="e20c1-206">LBE 予約と予約システム</span><span class="sxs-lookup"><span data-stu-id="e20c1-206">LBE Reservation and Booking System</span></span> 

<span data-ttu-id="e20c1-207">**Q: 空間 MMOG を開発して、大規模なフットプリントをデプロイしています。コンテンツとオブジェクトの永続化を管理するのに役立つすべてのサービス**</span><span class="sxs-lookup"><span data-stu-id="e20c1-207">**Q: I’m developing a spatial MMOG to deploy over a massive footprint. Any services that help me manage my content and object persistence?**</span></span>

<span data-ttu-id="e20c1-208">A: Azure 空間アンカーは、HoloLens、iOS、および Android デバイスで、複数のユーザーに対応し、空間的に対応した mixed reality エクスペリエンスを可能にする新しい Mixed Reality サービスです。</span><span class="sxs-lookup"><span data-stu-id="e20c1-208">A: Azure Spatial Anchors is a new Mixed Reality service that enables multi-user, spatially aware mixed reality experiences across HoloLens, iOS and Android devices.</span></span> <span data-ttu-id="e20c1-209">Azure 空間アンカーの詳細については、[こちら](https://azure.microsoft.com//services/spatial-anchors/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e20c1-209">You can learn more about Azure Spatial Anchors [here](https://azure.microsoft.com//services/spatial-anchors/).</span></span>

<span data-ttu-id="e20c1-210">**Q. この会場では、マルチプレーヤーエクスペリエンスを専門としており、開発時間をコンテンツやフロントエンド開発に専念させたいと考えています。バックエンド開発をブートストラップまたはオフロードするのに役立つサービスはありますか。**</span><span class="sxs-lookup"><span data-stu-id="e20c1-210">**Q. Our venue specializes in multi-player experiences and I’d like to focus our development time on content and front-end development. Are there offerings that can help me bootstrap or offload backend development?**</span></span>

<span data-ttu-id="e20c1-211">A: Azure PlayFab は、ライブゲーム用の完全なバックエンドプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="e20c1-211">A: Azure PlayFab is a complete backend platform for live games.</span></span> <span data-ttu-id="e20c1-212">詳細については、[こちら](https://playfab.com/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e20c1-212">You can learn more about it [here](https://playfab.com/).</span></span>

### <a name="misc"></a><span data-ttu-id="e20c1-213">その他</span><span class="sxs-lookup"><span data-stu-id="e20c1-213">Misc</span></span>

<span data-ttu-id="e20c1-214">**Q: SteamVR を使用して自分のエクスペリエンスをデプロイします。Windows Mixed Reality は SteamVR と連携しますか。**</span><span class="sxs-lookup"><span data-stu-id="e20c1-214">**Q: I use SteamVR to deploy my experiences. Does Windows Mixed Reality work with SteamVR?**</span></span>

<span data-ttu-id="e20c1-215">A: SteamVR の Windows Mixed Reality では、ユーザーは Windows Mixed Reality のイマーシブヘッドセットで SteamVR エクスペリエンスを実行できます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-215">A: Windows Mixed Reality for SteamVR allows users to run SteamVR experiences on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="e20c1-216">SteamVR と WMR の詳細について[は、こちら](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e20c1-216">Learn more about SteamVR with WMR [here](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).</span></span>

### <a name="support-and-community"></a><span data-ttu-id="e20c1-217">サポートとコミュニティ</span><span class="sxs-lookup"><span data-stu-id="e20c1-217">Support and community</span></span>  

<span data-ttu-id="e20c1-218">以下は、チームの分野の専門家と連携し、トラブルシューティングのサポートを受け、より広範な mixed reality 開発コミュニティに貢献するうえで役立つリソースです。</span><span class="sxs-lookup"><span data-stu-id="e20c1-218">Below are a few helpful resources to engage with subject matter experts on our team, get troubleshooting support, and contribute to the broader mixed reality dev community.</span></span>  

<span data-ttu-id="e20c1-219">公開されているすべての機能で問題が発生した場合は、フィードバックハブを使用してバグを報告してください。ガイダンスについては、この[ページ](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/filing-feedback)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e20c1-219">If you run into issues with any publicly released features, please file a bug using Feedback Hub.For guidance, please refer to this [page](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span>

<span data-ttu-id="e20c1-220">WMR のトラブルシューティングの詳細については、[サポート要求](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782)を提出して、カスタマーサポートチームにご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="e20c1-220">For additional troubleshooting help with WMR please get in touch with our customer support team by filing a [support request](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782).</span></span>

<span data-ttu-id="e20c1-221">HoloDevelopers の余裕期間チャネルに参加して、チームによる混合現実と分野の専門家に取り組んでいる開発者と提携してください。 [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span><span class="sxs-lookup"><span data-stu-id="e20c1-221">Join our HoloDevelopers Slack channel to engage with the developers working on mixed reality and subject matter experts from the team: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span></span>

<span data-ttu-id="e20c1-222">Twitter: ニュース、イベント、および更新については、Mixed Reality 開発者関係チームにご協力ください @MxdRealityDev</span><span class="sxs-lookup"><span data-stu-id="e20c1-222">Twitter: Follow our Mixed Reality Developer Relations team for news, events and updates @MxdRealityDev</span></span> 

<span data-ttu-id="e20c1-223">サンフランシスコにいる場合、Microsoft リアクターでは常に何かが行われています。</span><span class="sxs-lookup"><span data-stu-id="e20c1-223">If you happen to be in or around San Francisco, there’s always something going on at the Microsoft Reactor.</span></span> <span data-ttu-id="e20c1-224">イベントのカレンダーを[ここ](https://developer.microsoft.com//reactor/Location/San%20Francisco)に表示できます。</span><span class="sxs-lookup"><span data-stu-id="e20c1-224">You can see our calendar of events [here](https://developer.microsoft.com//reactor/Location/San%20Francisco).</span></span>