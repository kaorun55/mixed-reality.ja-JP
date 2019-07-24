---
title: HoloLens で Wi-fi に接続する
description: HoloLens を使用してワイヤレスインターネットに接続する方法と、デバイスの IP アドレスを識別する方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens、wifi、ワイヤレス、インターネット、ip、ip アドレス
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670114"
---
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="aa180-104">HoloLens で Wi-fi に接続する</span><span class="sxs-lookup"><span data-stu-id="aa180-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="aa180-105">HoloLens には、802.11 ac 対応、2x2 Wi-fi 無線が搭載されています。</span><span class="sxs-lookup"><span data-stu-id="aa180-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="aa180-106">HoloLens を Wi-fi ネットワークに接続することは、Windows 10 デスクトップまたはモバイルデバイスを Wi-fi ネットワークに接続することと似ています。</span><span class="sxs-lookup"><span data-stu-id="aa180-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![HoloLens Wi-fi 設定](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="aa180-108">HoloLens で Wi-fi ネットワークに接続する</span><span class="sxs-lookup"><span data-stu-id="aa180-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="aa180-109">**[スタート]** メニューに[ブルーム](gestures.md#bloom)ます。</span><span class="sxs-lookup"><span data-stu-id="aa180-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="aa180-110">スタート メニューまたは スタート メニューの右側にある **すべてのアプリ** の一覧から、**設定** アプリを選択します。</span><span class="sxs-lookup"><span data-stu-id="aa180-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="aa180-111">**設定**アプリが自動的に前面に配置されます。</span><span class="sxs-lookup"><span data-stu-id="aa180-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="aa180-112">**[ネットワーク & インターネット]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aa180-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="aa180-113">Wi-Fi がオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="aa180-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="aa180-114">一覧から Wi-fi ネットワークを選択します。</span><span class="sxs-lookup"><span data-stu-id="aa180-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="aa180-115">Wi-fi ネットワークパスワードを入力します (必要な場合)。</span><span class="sxs-lookup"><span data-stu-id="aa180-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="aa180-116">HoloLens で Wi-fi を無効にする</span><span class="sxs-lookup"><span data-stu-id="aa180-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="aa180-117">HoloLens で設定アプリを使用する</span><span class="sxs-lookup"><span data-stu-id="aa180-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="aa180-118">**[スタート]** メニューに[ブルーム](gestures.md#bloom)ます。</span><span class="sxs-lookup"><span data-stu-id="aa180-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="aa180-119">スタート メニューまたは スタート メニューの右側にある **すべてのアプリ** の一覧から、**設定** アプリを選択します。</span><span class="sxs-lookup"><span data-stu-id="aa180-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="aa180-120">**設定**アプリが自動的に前面に配置されます。</span><span class="sxs-lookup"><span data-stu-id="aa180-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="aa180-121">**[ネットワーク & インターネット]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aa180-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="aa180-122">Wi-fi スライダースイッチを選択して、"Off" の位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="aa180-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="aa180-123">これにより、Wi-fi ラジオの RF コンポーネントがオフになり、HoloLens の Wi-fi 機能がすべて無効になります。</span><span class="sxs-lookup"><span data-stu-id="aa180-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="aa180-124">HoloLens は、Wi-fi ラジオが無効になっている場合、[スペース](environment-considerations-for-hololens.md#WiFi fingerprint considerations)を自動的に読み込むことができません。</span><span class="sxs-lookup"><span data-stu-id="aa180-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#WiFi fingerprint considerations) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="aa180-125">スライダースイッチを "オン" の位置に移動して Wi-fi ラジオをオンにし、Wi-fi 機能を Microsoft HoloLens に復元します。</span><span class="sxs-lookup"><span data-stu-id="aa180-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="aa180-126">選択した Wi-fi 無線の状態 ("オフ") は、再起動後も保持されます。</span><span class="sxs-lookup"><span data-stu-id="aa180-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="aa180-127">Wi-fi ネットワークに接続していることを確認する方法</span><span class="sxs-lookup"><span data-stu-id="aa180-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="aa180-128">[ブルーム](gestures.md#bloom)を開き、 **[スタート]** メニューを表示します。</span><span class="sxs-lookup"><span data-stu-id="aa180-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="aa180-129">Wi-fi ステータスの [スタート] メニューの左上を確認します。</span><span class="sxs-lookup"><span data-stu-id="aa180-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="aa180-130">Wi-fi の状態と、接続されているネットワークの SSID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa180-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="aa180-131">Wi-fi ネットワーク上の HoloLens の IP アドレスを識別する</span><span class="sxs-lookup"><span data-stu-id="aa180-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="aa180-132">設定アプリの使用</span><span class="sxs-lookup"><span data-stu-id="aa180-132">Using the Settings app</span></span>

1. <span data-ttu-id="aa180-133">**[スタート]** メニューに[ブルーム](gestures.md#bloom)ます。</span><span class="sxs-lookup"><span data-stu-id="aa180-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="aa180-134">スタート メニューまたは スタート メニューの右側にある **すべてのアプリ** の一覧から、**設定** アプリを選択します。</span><span class="sxs-lookup"><span data-stu-id="aa180-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="aa180-135">**設定**アプリが自動的に前面に配置されます。</span><span class="sxs-lookup"><span data-stu-id="aa180-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="aa180-136">**[ネットワーク & インターネット]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aa180-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="aa180-137">使用可能な Wi-fi ネットワークの一覧の下までスクロールし、 **[ハードウェアのプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aa180-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Wi-fi 設定のハードウェアプロパティ](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="aa180-139">IP アドレスは**IPv4 アドレス**の横に表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa180-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="aa180-140">Cortana の使用</span><span class="sxs-lookup"><span data-stu-id="aa180-140">Using Cortana</span></span>

<span data-ttu-id="aa180-141">「*Cortana さん、私の IP アドレスを教えてください*」と言います。</span><span class="sxs-lookup"><span data-stu-id="aa180-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="aa180-142">また、Cortana によって IP アドレスが表示され、読み取られます。</span><span class="sxs-lookup"><span data-stu-id="aa180-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="aa180-143">Windows デバイスポータルの使用</span><span class="sxs-lookup"><span data-stu-id="aa180-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="aa180-144">PC の web ブラウザーで[デバイスポータル](using-the-windows-device-portal.md#networking)を開きます。</span><span class="sxs-lookup"><span data-stu-id="aa180-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="aa180-145">**[ネットワーク]** セクションに移動します。</span><span class="sxs-lookup"><span data-stu-id="aa180-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="aa180-146">IP アドレスとその他のネットワーク情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa180-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="aa180-147">この方法では、開発用 PC に IP アドレスを簡単にコピーして貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="aa180-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
