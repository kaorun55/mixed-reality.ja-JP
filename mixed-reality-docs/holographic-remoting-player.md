---
title: リモート処理の holographic プレーヤー
description: リモート処理の Holographic のプレイヤーとは、Holographic のリモート処理をサポートする PC のアプリおよびゲームに接続するコンパニオン アプリです。 Holographic のリモート処理で、Microsoft HoloLens を PC から holographic のコンテンツをストリーム リアルタイム、Wi-fi 接続を使用します。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、リモート処理、Holographic のリモート処理
ms.openlocfilehash: 16add6c72b594822cacbef6c92ce196ab9b13429
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605001"
---
# <a name="holographic-remoting-player"></a><span data-ttu-id="9c069-105">リモート処理の holographic プレーヤー</span><span class="sxs-lookup"><span data-stu-id="9c069-105">Holographic Remoting Player</span></span>

<span data-ttu-id="9c069-106">リモート処理の Holographic のプレイヤーとは、Holographic のリモート処理をサポートする PC のアプリおよびゲームに接続するコンパニオン アプリです。</span><span class="sxs-lookup"><span data-stu-id="9c069-106">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="9c069-107">Holographic のリモート処理で、Microsoft HoloLens を PC から holographic のコンテンツをストリーム リアルタイム、Wi-fi 接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="9c069-107">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection.</span></span>

<span data-ttu-id="9c069-108">Holographic のリモート処理 Player は、Holographic のリモート処理をサポートするために作られた PC のアプリでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c069-108">The Holographic Remoting Player can only be used with PC apps that are specifically designed to support Holographic Remoting.</span></span>

> [!NOTE]
> <span data-ttu-id="9c069-109">HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。</span><span class="sxs-lookup"><span data-stu-id="9c069-109">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="connecting-to-the-holographic-remoting-player"></a><span data-ttu-id="9c069-110">リモート処理の Holographic プレーヤーへの接続</span><span class="sxs-lookup"><span data-stu-id="9c069-110">Connecting to the Holographic Remoting Player</span></span>

<span data-ttu-id="9c069-111">Holographic のリモート処理 Player に接続するアプリの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="9c069-111">Follow your app's instructions to connect to the Holographic Remoting Player.</span></span> <span data-ttu-id="9c069-112">リモート処理のプレイヤーのメイン画面上の「次のように、HoloLens デバイスの IP アドレスを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c069-112">You will need to enter the IP address of your HoloLens device, which you can see on the Remoting Player's main screen as follows:</span></span>

![リモート処理の holographic プレーヤー](images/holographicremotingplayer.png)

<span data-ttu-id="9c069-114">メイン画面が表示されるたびに、接続されているアプリがないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="9c069-114">Whenever you see the main screen, you will know that you do not have an app connected.</span></span>

<span data-ttu-id="9c069-115">Holographic のリモート処理接続は**暗号化されていない**します。</span><span class="sxs-lookup"><span data-stu-id="9c069-115">Note that the holographic remoting connection is **not encrypted**.</span></span> <span data-ttu-id="9c069-116">Holographic のリモート処理は、信頼できるセキュリティで保護された Wi-fi 接続経由で常に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c069-116">You should always use Holographic Remoting over a secure Wi-Fi connection that you trust.</span></span>

## <a name="quality-and-performance"></a><span data-ttu-id="9c069-117">品質とパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="9c069-117">Quality and Performance</span></span>

<span data-ttu-id="9c069-118">品質およびパフォーマンスのエクスペリエンスの 3 つの要因に基づいて異なります。</span><span class="sxs-lookup"><span data-stu-id="9c069-118">The quality and performance of your experience will vary based on three factors:</span></span>
* <span data-ttu-id="9c069-119">**ホログラフィック操作を実行している**-高速の PC またはワイヤレス接続を高速、高解像度または詳細なコンテンツを表示するアプリは必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c069-119">**The holographic experience you're running** - Apps that render high-resolution or highly-detailed content may require a faster PC or faster wireless connection.</span></span>
* <span data-ttu-id="9c069-120">**お客様の PC のハードウェア**-PC を実行し、1 秒あたり 60 フレームで、ホログラフィック操作をエンコードすることができる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c069-120">**Your PC's hardware** - Your PC needs to be able to run and encode your holographic experience at 60 frames per second.</span></span> <span data-ttu-id="9c069-121">グラフィックス カードは、一般的な推奨 GeForce GTX 970 または AMD Radeon R9 290 またはそれ以上。</span><span class="sxs-lookup"><span data-stu-id="9c069-121">For a graphics card, we generally recommend a GeForce GTX 970 or AMD Radeon R9 290 or better.</span></span> <span data-ttu-id="9c069-122">ここでも、特定のエクスペリエンスには、上位または下位のカードが必要です。</span><span class="sxs-lookup"><span data-stu-id="9c069-122">Again, your particular experience may require a higher or lower-end card.</span></span>
* <span data-ttu-id="9c069-123">**Wi-fi 接続**-Wi-fi 経由で、ホログラフィック操作がストリーミングされます。</span><span class="sxs-lookup"><span data-stu-id="9c069-123">**Your Wi-Fi connection** - Your holographic experience is streamed over Wi-Fi.</span></span> <span data-ttu-id="9c069-124">低輻輳で品質を最大限に高速ネットワークを使用します。</span><span class="sxs-lookup"><span data-stu-id="9c069-124">Use a fast network with low congestion to maximize quality.</span></span> <span data-ttu-id="9c069-125">イーサネット ケーブルを介して接続されている PC を使用して、Wi-fi ではなく向上にも品質。</span><span class="sxs-lookup"><span data-stu-id="9c069-125">Using a PC that is connected over an Ethernet cable, rather than Wi-Fi, may also improve quality.</span></span>

## <a name="diagnostics"></a><span data-ttu-id="9c069-126">診断</span><span class="sxs-lookup"><span data-stu-id="9c069-126">Diagnostics</span></span>

<span data-ttu-id="9c069-127">接続の品質を測定するには、たとえば **「診断を有効にする」** Holographic のリモート処理のプレイヤーのメイン画面にします。</span><span class="sxs-lookup"><span data-stu-id="9c069-127">To measure the quality of your connection, say **"enable diagnostics"** while on the main screen of the Holographic Remoting Player.</span></span> <span data-ttu-id="9c069-128">診断を有効にするアプリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c069-128">When diagnostics are enabled, the app will show you:</span></span>
* <span data-ttu-id="9c069-129">**FPS** - レンダリングされたフレームの数の平均値、リモート処理のプレーヤーを受け取って 1 秒あたりのレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="9c069-129">**FPS** - The average number of rendered frames the remoting player is receiving and rendering per second.</span></span> <span data-ttu-id="9c069-130">理想では、60 FPS です。</span><span class="sxs-lookup"><span data-stu-id="9c069-130">The ideal is 60 FPS.</span></span>
* <span data-ttu-id="9c069-131">**待機時間**-お使いの PC から、HoloLens に移動するためのフレームにかかる平均時間。</span><span class="sxs-lookup"><span data-stu-id="9c069-131">**Latency** - The average amount of time it takes for a frame to go from your PC to the HoloLens.</span></span> <span data-ttu-id="9c069-132">小さいほど良いです。</span><span class="sxs-lookup"><span data-stu-id="9c069-132">The lower the better.</span></span> <span data-ttu-id="9c069-133">これは、Wi-fi ネットワークに大きく依存します。</span><span class="sxs-lookup"><span data-stu-id="9c069-133">This is largely dependent on your Wi-Fi network.</span></span>

<span data-ttu-id="9c069-134">メインの画面で言うことができる **「診断を無効にする」** 診断をオフにします。</span><span class="sxs-lookup"><span data-stu-id="9c069-134">While on the main screen, you can say **"disable diagnostics"** to turn off diagnostics.</span></span>

## <a name="pc-system-requirements"></a><span data-ttu-id="9c069-135">PC のシステム要件</span><span class="sxs-lookup"><span data-stu-id="9c069-135">PC System Requirements</span></span>
* <span data-ttu-id="9c069-136">お使いの PC**する必要があります**Windows 10 Anniversary Update を実行します。</span><span class="sxs-lookup"><span data-stu-id="9c069-136">Your PC **must** be running the Windows 10 Anniversary Update.</span></span>
* <span data-ttu-id="9c069-137">GeForce GTX 970 または AMD Radeon R9 290 または改善のグラフィックス カードをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9c069-137">We recommend a GeForce GTX 970 or AMD Radeon R9 290 or better graphics card.</span></span>
* <span data-ttu-id="9c069-138">お使いの PC をワイヤレス ホップの数を減らすイーサネット経由でネットワークに接続することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9c069-138">We recommend you connect your PC to your network via ethernet to reduce the number of Wireless hops.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c069-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c069-139">See Also</span></span>
* [<span data-ttu-id="9c069-140">ソフトウェア ライセンス条項の holographic のリモート処理</span><span class="sxs-lookup"><span data-stu-id="9c069-140">Holographic remoting software license terms</span></span>](microsoft-holographic-remoting-software-license-terms.md)
* [<span data-ttu-id="9c069-141">Microsoft プライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="9c069-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
