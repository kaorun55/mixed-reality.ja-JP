---
title: Unreal でのストリーミング
description: Unreal での HoloLens 2 へのストリーミングに関するガイド
author: suwu
ms.author: suwu
ms.date: 6/8/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, ストリーミング, PC, ホログラフィック アプリのリモート処理, Holographic Remoting Player, ドキュメント
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 78a019f5b74b254c1f32ec85dc639df47648555f
ms.sourcegitcommit: ff0e89b07d0b4a945967d64c5b8845a21dc5f476
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84888913"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="86ec8-104">Unreal でのストリーミング</span><span class="sxs-lookup"><span data-stu-id="86ec8-104">Streaming in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="86ec8-105">概要</span><span class="sxs-lookup"><span data-stu-id="86ec8-105">Overview</span></span>
<span data-ttu-id="86ec8-106">PC から HoloLens にストリーミングを行うことには、次の 2 つの大きな利点があります。</span><span class="sxs-lookup"><span data-stu-id="86ec8-106">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="86ec8-107">Mixed Reality アプリで PC の演算性能を活用できる。</span><span class="sxs-lookup"><span data-stu-id="86ec8-107">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="86ec8-108">開発のイテレーション時間を短縮できる。</span><span class="sxs-lookup"><span data-stu-id="86ec8-108">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="86ec8-109">最初に、[Holographic Remoting Player](holographic-remoting-player.md) を HoloLens デバイスにダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86ec8-109">To get started, you'll need to download the [Holographic Remoting Player](holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="86ec8-110">これにより、アプリを使って、次のソースから HoloLens 上のリモート処理プレーヤーに直接ストリーミングできるようになります。</span><span class="sxs-lookup"><span data-stu-id="86ec8-110">This allows your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="86ec8-111">Unreal Engine エディター</span><span class="sxs-lookup"><span data-stu-id="86ec8-111">The Unreal Engine editor</span></span>
* <span data-ttu-id="86ec8-112">パッケージ化された Windows 実行可能ファイル</span><span class="sxs-lookup"><span data-stu-id="86ec8-112">A packaged Windows executable</span></span> 

<span data-ttu-id="86ec8-113">ストリーミング時には、アプリケーションをデバイス上で実行する場合と同じ HoloLens の機能をほぼすべて利用できます。</span><span class="sxs-lookup"><span data-stu-id="86ec8-113">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="86ec8-114">これには、[ハンド ジョイント トラッキング](unreal-hand-tracking.md) (HoloLens 2 を使用している場合)、[空間マッピング](unreal-spatial-mapping.md)、[空間アンカー](unreal-spatial-anchors.md)などが含まれます。ただし、この[制限事項の一覧](holographic-remoting-troubleshooting.md)に記載されている機能は含まれません。</span><span class="sxs-lookup"><span data-stu-id="86ec8-114">This includes [hand joint tracking](unreal-hand-tracking.md) (if you're on a HoloLens 2), [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list of limitations](holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> <span data-ttu-id="86ec8-115">ストリーミング品質は、ユーザーの Wi-Fi ネットワークの強度に大きく依存します。</span><span class="sxs-lookup"><span data-stu-id="86ec8-115">Streaming quality is highly dependent on the strength of your wifi network.</span></span>

## <a name="device-support"></a><span data-ttu-id="86ec8-116">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="86ec8-116">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86ec8-117"><strong>ソース</strong></span><span class="sxs-lookup"><span data-stu-id="86ec8-117"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="86ec8-118"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="86ec8-118"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="86ec8-119"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="86ec8-119"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="86ec8-120"><strong>イマーシブ ヘッドセット</strong></span><span class="sxs-lookup"><span data-stu-id="86ec8-120"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86ec8-121">Unreal エディター</span><span class="sxs-lookup"><span data-stu-id="86ec8-121">Unreal editor</span></span></td>
        <td><span data-ttu-id="86ec8-122">✔</span><span class="sxs-lookup"><span data-stu-id="86ec8-122">✔</span></span></td>
        <td><span data-ttu-id="86ec8-123">✔️</span><span class="sxs-lookup"><span data-stu-id="86ec8-123">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="86ec8-124">Windows パッケージ</span><span class="sxs-lookup"><span data-stu-id="86ec8-124">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="86ec8-125">✔️</span><span class="sxs-lookup"><span data-stu-id="86ec8-125">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="86ec8-126">Unreal エディターからのストリーミング</span><span class="sxs-lookup"><span data-stu-id="86ec8-126">Streaming from the Unreal editor</span></span>

<span data-ttu-id="86ec8-127">開発者にとって、Unreal エディターから HoloLens デバイスへのストリーミングには、テスト時に大きなメリットがあります。更新プログラムをテストする前に、アプリのビルドとデプロイを待機する必要がなくなるからです。</span><span class="sxs-lookup"><span data-stu-id="86ec8-127">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides big benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="86ec8-128">[Unreal エディターからのストリーミング](unreal-uxt-ch6.md#device-only-streaming)については、Unreal の概要に関するチュートリアル シリーズの最後のセクションに詳細な説明があります。</span><span class="sxs-lookup"><span data-stu-id="86ec8-128">You can find detailed instructions on [streaming from the Unreal editor](unreal-uxt-ch6.md#device-only-streaming) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="86ec8-129">パッケージ化された Windows 実行可能ファイルからのストリーミング</span><span class="sxs-lookup"><span data-stu-id="86ec8-129">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="86ec8-130">Unreal 4.25.1 では、以下に示す手順で、パッケージ化された Windows 実行可能ファイルから HoloLens 2 デバイスにアプリをストリーミングできます。</span><span class="sxs-lookup"><span data-stu-id="86ec8-130">As of Unreal 4.25.1, you can stream your app to a HoloLens 2 device from a packaged Windows executable by following the steps below:</span></span> 

1. <span data-ttu-id="86ec8-131">エディター メニューで、 **[ファイル] > [パッケージ プロジェクト] > [Windows]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="86ec8-131">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="86ec8-132">パッケージを保存する場所を選択し、 **[Select Folder]\(フォルダーの選択\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="86ec8-132">Choose a location to save your package and click **Select Folder**.</span></span>

2. <span data-ttu-id="86ec8-133">パッケージのビルドが完了したら、HoloLens 2 で **Holographic Remoting Player** を開き、IP アドレスをメモします。</span><span class="sxs-lookup"><span data-stu-id="86ec8-133">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="86ec8-134">**Holographic Remoting Player** を開いたままにして、コマンド ライン プロンプトで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="86ec8-134">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="86ec8-135">cd を実行し、パッケージを保存したローカル ディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="86ec8-135">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="86ec8-136">次のコマンドを入力します。```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span><span class="sxs-lookup"><span data-stu-id="86ec8-136">Enter the following command: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span></span>

> [!NOTE]
> <span data-ttu-id="86ec8-137">プロジェクト設定に含まれるアプリケーション名が、Windows パッケージを作成するために自動的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="86ec8-137">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="86ec8-138">何らかの理由でこれらが異なる場合は、コマンド プロンプトで Windows 実行可能ファイル名を使用します。</span><span class="sxs-lookup"><span data-stu-id="86ec8-138">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="86ec8-139">Enter キーを押すと、アプリケーションのストリーミングが開始します。</span><span class="sxs-lookup"><span data-stu-id="86ec8-139">Hit enter and watch your application start streaming!</span></span>

## <a name="see-also"></a><span data-ttu-id="86ec8-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="86ec8-140">See also</span></span>
* [<span data-ttu-id="86ec8-141">Holographic リモート処理のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="86ec8-141">Holographic remoting version history</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="86ec8-142">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="86ec8-142">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="86ec8-143">Holographic Remoting を使用したセキュリティで保護された接続の確立</span><span class="sxs-lookup"><span data-stu-id="86ec8-143">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
