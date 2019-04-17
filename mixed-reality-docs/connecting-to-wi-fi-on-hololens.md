---
title: HoloLens の Wi-fi に接続します。
description: HoloLens でワイヤレス インターネットに接続する方法とデバイスの IP アドレスを識別する方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, wifi, wireless, internet, ip, ip address
ms.openlocfilehash: 0440c3dad48d73db51e7d730e79d6eb1e74a5694
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604109"
---
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="e2133-104">HoloLens の Wi-fi に接続します。</span><span class="sxs-lookup"><span data-stu-id="e2133-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="e2133-105">HoloLens には、802.11 ac が含まれています-対応、2 倍の 2 つの Wi-fi ラジオします。</span><span class="sxs-lookup"><span data-stu-id="e2133-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="e2133-106">HoloLens の Wi-fi ネットワークに接続することは、Windows 10 デスクトップまたはモバイル デバイスの Wi-fi ネットワークに接続に似ています。</span><span class="sxs-lookup"><span data-stu-id="e2133-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![HoloLens の Wi-fi 設定](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="e2133-108">HoloLens の Wi-fi ネットワークに接続します。</span><span class="sxs-lookup"><span data-stu-id="e2133-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="e2133-109">[「Bloom](gestures.md#bloom)を、**開始**メニュー。</span><span class="sxs-lookup"><span data-stu-id="e2133-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="e2133-110">選択、**設定**または開始からアプリ、**すべてのアプリ**スタート メニューの右側の一覧。</span><span class="sxs-lookup"><span data-stu-id="e2133-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="e2133-111">**設定**アプリは自動的に配置する前になります。</span><span class="sxs-lookup"><span data-stu-id="e2133-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="e2133-112">選択**ネットワークとインターネット**します。</span><span class="sxs-lookup"><span data-stu-id="e2133-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="e2133-113">Wi-Fi がオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e2133-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="e2133-114">Wi-fi ネットワークを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="e2133-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="e2133-115">(必要に応じて)、Wi-fi ネットワーク パスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="e2133-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="e2133-116">HoloLens で Wi-fi を無効にします。</span><span class="sxs-lookup"><span data-stu-id="e2133-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="e2133-117">HoloLens で、設定アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="e2133-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="e2133-118">[「Bloom](gestures.md#bloom)を、**開始**メニュー。</span><span class="sxs-lookup"><span data-stu-id="e2133-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="e2133-119">選択、**設定**または開始からアプリ、**すべてのアプリ**スタート メニューの右側の一覧。</span><span class="sxs-lookup"><span data-stu-id="e2133-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="e2133-120">**設定**アプリは自動的に配置する前になります。</span><span class="sxs-lookup"><span data-stu-id="e2133-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="e2133-121">選択**ネットワークとインターネット**します。</span><span class="sxs-lookup"><span data-stu-id="e2133-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="e2133-122">[オフ] の位置に移動する Wi-fi スライダー スイッチを選択します。</span><span class="sxs-lookup"><span data-stu-id="e2133-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="e2133-123">Wi-fi ラジオの RF コンポーネントをオフにされ HoloLens ですべての Wi-fi 機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="e2133-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="e2133-124">HoloLens を自動的にロードすることにすることはできません、[スペース](environment-considerations-for-hololens.md#spaces)Wi-fi オプションが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="e2133-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#spaces) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="e2133-125">スライダーのスイッチを Wi-fi オプションをオンにし、Microsoft HoloLens で Wi-fi 機能を復元"On"の位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="e2133-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="e2133-126">選択した Wi-fi ラジオ状態 (「オン」の"Off") が再起動後も保持されます。</span><span class="sxs-lookup"><span data-stu-id="e2133-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="e2133-127">Wi-fi ネットワークに接続していることを確認する方法</span><span class="sxs-lookup"><span data-stu-id="e2133-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="e2133-128">[「Bloom](gestures.md#bloom)を起動、**開始**メニュー。</span><span class="sxs-lookup"><span data-stu-id="e2133-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="e2133-129">上部で、Wi-fi の状態の [スタート] メニューのままにします。</span><span class="sxs-lookup"><span data-stu-id="e2133-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="e2133-130">状態の Wi Fi と接続されたネットワークの SSID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e2133-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="e2133-131">HoloLens、Wi-fi ネットワーク上の IP アドレスを識別します。</span><span class="sxs-lookup"><span data-stu-id="e2133-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="e2133-132">[設定] アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="e2133-132">Using the Settings app</span></span>

1. <span data-ttu-id="e2133-133">[「Bloom](gestures.md#bloom)を、**開始**メニュー。</span><span class="sxs-lookup"><span data-stu-id="e2133-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="e2133-134">選択、**設定**または開始からアプリ、**すべてのアプリ**スタート メニューの右側の一覧。</span><span class="sxs-lookup"><span data-stu-id="e2133-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="e2133-135">**設定**アプリは自動的に配置する前になります。</span><span class="sxs-lookup"><span data-stu-id="e2133-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="e2133-136">選択**ネットワークとインターネット**します。</span><span class="sxs-lookup"><span data-stu-id="e2133-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="e2133-137">使用可能な Wi-fi ネットワークの一覧の下まで下へスクロールし、選択**ハードウェア プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="e2133-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Wi-fi 設定のハードウェア プロパティ](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="e2133-139">IP アドレスが横に表示される**IPv4 アドレス**します。</span><span class="sxs-lookup"><span data-stu-id="e2133-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="e2133-140">Cortana を使ってください。</span><span class="sxs-lookup"><span data-stu-id="e2133-140">Using Cortana</span></span>

<span data-ttu-id="e2133-141">たとえば"*Hey Cortana、自分の IP アドレスは何ですか?*"</span><span class="sxs-lookup"><span data-stu-id="e2133-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="e2133-142">Cortana が表示され、IP アドレスを読み取る。</span><span class="sxs-lookup"><span data-stu-id="e2133-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="e2133-143">Windows Device Portal を使用します。</span><span class="sxs-lookup"><span data-stu-id="e2133-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="e2133-144">開く、[デバイス ポータル](using-the-windows-device-portal.md#networking)PC の web ブラウザーでします。</span><span class="sxs-lookup"><span data-stu-id="e2133-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="e2133-145">移動し、**ネットワーク**セクション。</span><span class="sxs-lookup"><span data-stu-id="e2133-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="e2133-146">自分の IP アドレスとその他のネットワークの情報が表示されますがあります。</span><span class="sxs-lookup"><span data-stu-id="e2133-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="e2133-147">このメソッドは、簡単なコピーと、開発 PC 上の IP アドレスの貼り付けをできます。</span><span class="sxs-lookup"><span data-stu-id="e2133-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
