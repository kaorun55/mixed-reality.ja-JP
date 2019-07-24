---
title: Holographic リモート処理プレーヤー
description: Holographic Remoting Player は、Holographic リモート処理をサポートする PC アプリやゲームに接続するコンパニオンアプリです。 Holographic リモート処理では、Wi-fi 接続を使用して、PC から Microsoft HoloLens にコンテンツを Holographic します。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: b8354295f9752e73cc9b34c1769254e49808b63f
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813722"
---
# <a name="holographic-remoting-player"></a><span data-ttu-id="89921-105">Holographic リモート処理プレーヤー</span><span class="sxs-lookup"><span data-stu-id="89921-105">Holographic Remoting Player</span></span>

<span data-ttu-id="89921-106">Holographic Remoting Player は、Holographic リモート処理をサポートする PC アプリやゲームに接続するコンパニオンアプリです。</span><span class="sxs-lookup"><span data-stu-id="89921-106">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="89921-107">Holographic リモート処理では、Wi-fi 接続を使用して、PC から Microsoft HoloLens にコンテンツを Holographic します。</span><span class="sxs-lookup"><span data-stu-id="89921-107">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection.</span></span>

<span data-ttu-id="89921-108">Holographic リモート処理プレーヤーは、特に Holographic リモート処理をサポートするように設計された PC アプリでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="89921-108">The Holographic Remoting Player can only be used with PC apps that are specifically designed to support Holographic Remoting.</span></span>

<span data-ttu-id="89921-109">Holographic リモート処理プレーヤーは、HoloLens と HoloLens 2 の両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="89921-109">The Holographic Remoting Player is available for both HoloLens and HoloLens 2.</span></span>  <span data-ttu-id="89921-110">Hololens を使用した Holographic リモート処理をサポートする PC アプリは、HoloLens 2 で Holographic Remをサポートするように更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89921-110">PC apps that supported Holographic Remoting with HoloLens need to be updated to support Holographic Remtoing with HoloLens 2.</span></span>  <span data-ttu-id="89921-111">サポートされているバージョンについて不明な点がある場合は、アプリプロバイダーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="89921-111">Please contact your app provider if you have questions about which versions are supported.</span></span>

## <a name="connecting-to-the-holographic-remoting-player"></a><span data-ttu-id="89921-112">Holographic リモート処理プレーヤーに接続する</span><span class="sxs-lookup"><span data-stu-id="89921-112">Connecting to the Holographic Remoting Player</span></span>

<span data-ttu-id="89921-113">アプリの指示に従って、Holographic リモート処理プレーヤーに接続します。</span><span class="sxs-lookup"><span data-stu-id="89921-113">Follow your app's instructions to connect to the Holographic Remoting Player.</span></span> <span data-ttu-id="89921-114">HoloLens デバイスの IP アドレスを入力する必要があります。これは、次のように、リモート処理プレーヤーのメイン画面で確認できます。</span><span class="sxs-lookup"><span data-stu-id="89921-114">You will need to enter the IP address of your HoloLens device, which you can see on the Remoting Player's main screen as follows:</span></span>

![Holographic リモート処理プレーヤー](images/holographicremotingplayer.png)

<span data-ttu-id="89921-116">メイン画面が表示されるたびに、アプリが接続されていないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="89921-116">Whenever you see the main screen, you will know that you do not have an app connected.</span></span>

<span data-ttu-id="89921-117">Holographic remoting 接続は暗号化されて**いない**ことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="89921-117">Note that the holographic remoting connection is **not encrypted**.</span></span> <span data-ttu-id="89921-118">信頼できる Wi-fi 接続では、常に Holographic リモート処理を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89921-118">You should always use Holographic Remoting over a secure Wi-Fi connection that you trust.</span></span>

## <a name="quality-and-performance"></a><span data-ttu-id="89921-119">品質とパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="89921-119">Quality and Performance</span></span>

<span data-ttu-id="89921-120">エクスペリエンスの品質とパフォーマンスは、次の3つの要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="89921-120">The quality and performance of your experience will vary based on three factors:</span></span>
* <span data-ttu-id="89921-121">実行している**holographic エクスペリエンス**-高解像度または高度なコンテンツをレンダリングするアプリでは、より高速な PC またはより高速なワイヤレス接続が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="89921-121">**The holographic experience you're running** - Apps that render high-resolution or highly-detailed content may require a faster PC or faster wireless connection.</span></span>
* <span data-ttu-id="89921-122">**Pc のハードウェア**-pc は、1秒あたり60のフレームで holographic エクスペリエンスを実行およびエンコードできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="89921-122">**Your PC's hardware** - Your PC needs to be able to run and encode your holographic experience at 60 frames per second.</span></span> <span data-ttu-id="89921-123">グラフィックスカードの場合は、一般に、GeForce GTX 970 または AMD Radeon R9 290 以上をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="89921-123">For a graphics card, we generally recommend a GeForce GTX 970 or AMD Radeon R9 290 or better.</span></span> <span data-ttu-id="89921-124">ここでも、特定のエクスペリエンスでは、より高いまたは低いカードが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="89921-124">Again, your particular experience may require a higher or lower-end card.</span></span>
* <span data-ttu-id="89921-125">Wi-fi**接続**-holographic エクスペリエンスは wi-fi 経由でストリーミングされます。</span><span class="sxs-lookup"><span data-stu-id="89921-125">**Your Wi-Fi connection** - Your holographic experience is streamed over Wi-Fi.</span></span> <span data-ttu-id="89921-126">低負荷の高速ネットワークを使用して、品質を最大化します。</span><span class="sxs-lookup"><span data-stu-id="89921-126">Use a fast network with low congestion to maximize quality.</span></span> <span data-ttu-id="89921-127">Wi-fi ではなくイーサネットケーブルで接続されている PC を使用すると、品質が向上する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="89921-127">Using a PC that is connected over an Ethernet cable, rather than Wi-Fi, may also improve quality.</span></span>

## <a name="diagnostics"></a><span data-ttu-id="89921-128">診断</span><span class="sxs-lookup"><span data-stu-id="89921-128">Diagnostics</span></span>

<span data-ttu-id="89921-129">接続の品質を測定するには、Holographic リモート処理プレーヤーのメイン画面で [**診断の有効化]** を言います。</span><span class="sxs-lookup"><span data-stu-id="89921-129">To measure the quality of your connection, say **"enable diagnostics"** while on the main screen of the Holographic Remoting Player.</span></span> <span data-ttu-id="89921-130">診断が有効になっている場合、アプリには次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="89921-130">When diagnostics are enabled, the app will show you:</span></span>
* <span data-ttu-id="89921-131">**FPS** -リモートプレーヤーが受信して1秒間にレンダリングするレンダリングフレームの平均数。</span><span class="sxs-lookup"><span data-stu-id="89921-131">**FPS** - The average number of rendered frames the remoting player is receiving and rendering per second.</span></span> <span data-ttu-id="89921-132">最適なは 60 FPS です。</span><span class="sxs-lookup"><span data-stu-id="89921-132">The ideal is 60 FPS.</span></span>
* <span data-ttu-id="89921-133">**[待機時間]** -フレームが PC から HoloLens に移動するまでにかかる平均時間。</span><span class="sxs-lookup"><span data-stu-id="89921-133">**Latency** - The average amount of time it takes for a frame to go from your PC to the HoloLens.</span></span> <span data-ttu-id="89921-134">精度が低下します。</span><span class="sxs-lookup"><span data-stu-id="89921-134">The lower the better.</span></span> <span data-ttu-id="89921-135">これは、Wi-fi ネットワークに大きく依存します。</span><span class="sxs-lookup"><span data-stu-id="89921-135">This is largely dependent on your Wi-Fi network.</span></span>

<span data-ttu-id="89921-136">メイン画面では、 **[診断を無効**にする] を使用して診断を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="89921-136">While on the main screen, you can say **"disable diagnostics"** to turn off diagnostics.</span></span>

## <a name="pc-system-requirements"></a><span data-ttu-id="89921-137">PC のシステム要件</span><span class="sxs-lookup"><span data-stu-id="89921-137">PC System Requirements</span></span>
* <span data-ttu-id="89921-138">お使いの PC では、Windows 10 の記念日更新以降が実行されている**必要があり**ます。</span><span class="sxs-lookup"><span data-stu-id="89921-138">Your PC **must** be running the Windows 10 Anniversary Update or newer.</span></span>
* <span data-ttu-id="89921-139">GeForce GTX 970 または AMD Radeon R9 290 以上のグラフィックスカードをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="89921-139">We recommend a GeForce GTX 970 or AMD Radeon R9 290 or better graphics card.</span></span>
* <span data-ttu-id="89921-140">ワイヤレスホップの数を減らすには、コンピューターをイーサネット経由でネットワークに接続することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="89921-140">We recommend you connect your PC to your network via ethernet to reduce the number of Wireless hops.</span></span>

## <a name="see-also"></a><span data-ttu-id="89921-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="89921-141">See Also</span></span>
* [<span data-ttu-id="89921-142">Holographic リモート ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="89921-142">Holographic remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="89921-143">Microsoft のプライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="89921-143">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
