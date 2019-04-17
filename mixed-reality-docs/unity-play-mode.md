---
title: Unity の再生モード
description: Unity エディターで再生モードを使用して、アプリを展開することがなく、デバイスで変更をプレビューします。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、リモート処理、holographic のリモート処理、プレーヤーの holographic のリモート処理
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597824"
---
# <a name="unity-play-mode"></a><span data-ttu-id="26e3e-104">Unity の再生モード</span><span class="sxs-lookup"><span data-stu-id="26e3e-104">Unity Play Mode</span></span>

<span data-ttu-id="26e3e-105">Unity プロジェクトの作業をする高速の方法では、「再生モード」を使用します。</span><span class="sxs-lookup"><span data-stu-id="26e3e-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="26e3e-106">これは、アプリを実行、ローカル Unity エディターで、PC に。</span><span class="sxs-lookup"><span data-stu-id="26e3e-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="26e3e-107">Unity では、Holographic のリモート処理を使用して、実際の HoloLens デバイスでコンテンツをプレビューする高速の方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="26e3e-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="26e3e-108">リモート処理で Holographic unity 再生モード</span><span class="sxs-lookup"><span data-stu-id="26e3e-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="26e3e-109">Holographic リモート処理では、Unity エディターで、PC で実行中、HoloLens でアプリが発生することができます。</span><span class="sxs-lookup"><span data-stu-id="26e3e-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="26e3e-110">視線、ジェスチャ、音声、および入力空間のマッピングは、お使いのコンピューター、HoloLens から送信されます。</span><span class="sxs-lookup"><span data-stu-id="26e3e-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="26e3e-111">レンダリングされたフレーム、HoloLens に送信されます。</span><span class="sxs-lookup"><span data-stu-id="26e3e-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="26e3e-112">これは、迅速に構築および完全なプロジェクトを展開することがなく、アプリをデバッグする優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="26e3e-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="26e3e-113">HoloLens に移動し、 **Microsoft Store**をインストールし、 **[Holographic のリモート処理 Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** アプリ。</span><span class="sxs-lookup"><span data-stu-id="26e3e-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="26e3e-114">HoloLens、起動、 **Holographic のリモート処理 Player**アプリ。</span><span class="sxs-lookup"><span data-stu-id="26e3e-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="26e3e-115">Unity に移動、**ウィンドウ**メニュー選択し、 **Holographic エミュレーション**します。</span><span class="sxs-lookup"><span data-stu-id="26e3e-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="26e3e-116">設定**エミュレーション モード**に**デバイスにリモート**します。</span><span class="sxs-lookup"><span data-stu-id="26e3e-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="26e3e-117">**リモート マシン**、HoloLens の IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="26e3e-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="26e3e-118">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26e3e-118">Click **Connect**.</span></span> <span data-ttu-id="26e3e-119">わかります**接続の状態**変更**接続済み**HoloLens で空白の画面が表示とします。</span><span class="sxs-lookup"><span data-stu-id="26e3e-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="26e3e-120">をクリックして、**再生**再生モードを開始し、HoloLens でアプリを体験するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="26e3e-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="26e3e-121">Holographic のリモート処理では、高速の PC と Wi-fi 接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="26e3e-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="26e3e-122">参照してください[Holographic のリモート処理 Player](holographic-remoting-player.md)の完全な詳細情報。</span><span class="sxs-lookup"><span data-stu-id="26e3e-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="26e3e-123">最良の結果をアプリが正しく設定を確認します、[フォーカス ポイント](focus-point-in-unity.md)します。</span><span class="sxs-lookup"><span data-stu-id="26e3e-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="26e3e-124">これにより、最適なワイヤレス接続の待機時間にシーンを適応させる Holographic のリモート処理ができます。</span><span class="sxs-lookup"><span data-stu-id="26e3e-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="26e3e-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="26e3e-125">See Also</span></span>
* [<span data-ttu-id="26e3e-126">リモート処理の holographic プレーヤー</span><span class="sxs-lookup"><span data-stu-id="26e3e-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)
