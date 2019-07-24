---
title: HoloLens をリセットまたは復旧する
description: HoloLens を再起動またはリセットするための基本および詳細な手順です。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 操作方法、再起動、リセット、回復、ハードリセット、ソフトリセット、電源サイクル、HoloLens、シャットダウン
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524034"
---
# <a name="reset-or-recover-your-hololens"></a><span data-ttu-id="ff9da-104">HoloLens をリセットまたは復旧する</span><span class="sxs-lookup"><span data-stu-id="ff9da-104">Reset or recover your HoloLens</span></span>

<span data-ttu-id="ff9da-105">HoloLens で問題が発生している場合は、再起動、リセット、またはデバイスの回復を再度実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="ff9da-105">If you’re experiencing problems with your HoloLens you may want to try a restart, reset, or even re-flash with device recovery.</span></span> <span data-ttu-id="ff9da-106">このドキュメントでは、推奨される手順を順番に説明します。</span><span class="sxs-lookup"><span data-stu-id="ff9da-106">This document will guide you through the recommended steps in succession.</span></span>

## <a name="perform-a-device-reboot"></a><span data-ttu-id="ff9da-107">デバイスの再起動を実行する</span><span class="sxs-lookup"><span data-stu-id="ff9da-107">Perform a device reboot</span></span>

<span data-ttu-id="ff9da-108">HoloLens で問題が発生しているか、応答しない場合は、まず次のいずれかの方法で再起動してみてください。</span><span class="sxs-lookup"><span data-stu-id="ff9da-108">If your HoloLens is experiencing issues or is unresponsive, first try rebooting it via one of the below methods.</span></span>

### <a name="perform-a-safe-reboot-via-cortana"></a><span data-ttu-id="ff9da-109">Cortana を使用して安全な再起動を実行する</span><span class="sxs-lookup"><span data-stu-id="ff9da-109">Perform a safe reboot via Cortana</span></span>

<span data-ttu-id="ff9da-110">HoloLens を再起動する最も安全な方法は、Cortana を使用することです。</span><span class="sxs-lookup"><span data-stu-id="ff9da-110">The safest way to reboot the HoloLens is via Cortana.</span></span> <span data-ttu-id="ff9da-111">これは、通常、HoloLens で問題が発生した場合の最初の手順です。</span><span class="sxs-lookup"><span data-stu-id="ff9da-111">This is generally a great first-step when experiencing an issue with HoloLens:</span></span>
1. <span data-ttu-id="ff9da-112">デバイスに配置する</span><span class="sxs-lookup"><span data-stu-id="ff9da-112">Put on your device</span></span>
2. <span data-ttu-id="ff9da-113">電源が入っていること、ユーザーがログインしていること、デバイスがパスワードのロック解除を待機していないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ff9da-113">Make sure it’s powered on, a user is logged in, and the device is not waiting for a password to unlock it.</span></span>
3. <span data-ttu-id="ff9da-114">「Cortana、reboot」、または「Cortana の再起動」と言ってください。</span><span class="sxs-lookup"><span data-stu-id="ff9da-114">Say “Hey Cortana, reboot” or "Hey Cortana, restart."</span></span>
4. <span data-ttu-id="ff9da-115">確認すると、確認を求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff9da-115">When she acknowledges she will ask you for confirmation.</span></span> <span data-ttu-id="ff9da-116">質問が終了した後、サウンドが再生されるのを待ってから、自分の声を聞いて、"はい" と言うことを示します。</span><span class="sxs-lookup"><span data-stu-id="ff9da-116">Wait a second for a sound to play after she has finished her question, indicating she is listening to you and then say “Yes.”</span></span>
5. <span data-ttu-id="ff9da-117">デバイスが再起動または再起動されます。</span><span class="sxs-lookup"><span data-stu-id="ff9da-117">The device will now reboot/restart.</span></span>

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a><span data-ttu-id="ff9da-118">Windows デバイスポータルを使用して安全な再起動を実行する</span><span class="sxs-lookup"><span data-stu-id="ff9da-118">Perform a safe reboot via Windows Device Portal</span></span>

<span data-ttu-id="ff9da-119">上記の問題が解決しない場合は、 [Windows デバイスポータル](using-the-windows-device-portal.md)を使用してデバイスの再起動を試みることができます。</span><span class="sxs-lookup"><span data-stu-id="ff9da-119">If the above doesn't work, you can try to reboot the device via [Windows Device Portal](using-the-windows-device-portal.md).</span></span> <span data-ttu-id="ff9da-120">右上隅には、デバイスを再起動またはシャットダウンするオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="ff9da-120">In the upper right corner, there is an option to restart/shutdown the device.</span></span>

### <a name="perform-a-safe-reboot-via-the-power-button"></a><span data-ttu-id="ff9da-121">電源ボタンを使用して安全な再起動を実行する</span><span class="sxs-lookup"><span data-stu-id="ff9da-121">Perform a safe reboot via the power button</span></span>

<span data-ttu-id="ff9da-122">それでもデバイスを再起動できない場合は、電源ボタンを使用して再起動を試みることができます。</span><span class="sxs-lookup"><span data-stu-id="ff9da-122">If you still can't reboot your device, you can try to issue a reboot via the power button:</span></span>
1. <span data-ttu-id="ff9da-123">5秒間、電源ボタンを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="ff9da-123">Press and hold the power button for 5 seconds</span></span>
   1. <span data-ttu-id="ff9da-124">1秒後に、5個の Led すべてが点灯し、右から左へと徐々にオフになります。</span><span class="sxs-lookup"><span data-stu-id="ff9da-124">After 1 second, you will see all 5 LEDs illuminate, then slowly turn off from right to left</span></span>
   2. <span data-ttu-id="ff9da-125">5秒後、すべての Led はオフになり、シャットダウンコマンドが正常に発行されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="ff9da-125">After 5 seconds, all LEDs will be off, indicating the shutdown command was issued successfully</span></span>
   3. <span data-ttu-id="ff9da-126">すべての Led がオフになった直後にボタンを押すことが重要です。</span><span class="sxs-lookup"><span data-stu-id="ff9da-126">Note, it’s important to stop pressing the button immediately after all the LEDs have turned off</span></span>
2. <span data-ttu-id="ff9da-127">シャットダウンが正常に完了するまで1分間待機します。</span><span class="sxs-lookup"><span data-stu-id="ff9da-127">Wait 1 minute for the shutdown to cleanly succeed.</span></span> <span data-ttu-id="ff9da-128">ディスプレイがオフの場合でも、シャットダウンがまだ進行中である可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ff9da-128">Note that the shutdown may still be in progress even if the displays are off</span></span>
3. <span data-ttu-id="ff9da-129">1秒間電源ボタンを押したままデバイスの電源を再度オンにする</span><span class="sxs-lookup"><span data-stu-id="ff9da-129">Power on the device again by pressing and holding the power button for 1 second</span></span>

### <a name="perform-an-unsafe-forced-reboot"></a><span data-ttu-id="ff9da-130">安全でない強制再起動の実行</span><span class="sxs-lookup"><span data-stu-id="ff9da-130">Perform an unsafe forced reboot</span></span>

<span data-ttu-id="ff9da-131">上記のいずれの方法でもデバイスを正常に再起動できない場合は、強制的に再起動することができます。</span><span class="sxs-lookup"><span data-stu-id="ff9da-131">If none of the above methods are able to successfully reboot your device, you can force a reboot.</span></span> <span data-ttu-id="ff9da-132">この方法は、HoloLens からバッテリを取り出すことと同じです。そのため、デバイスが破損した状態のままになる危険性のある操作です。</span><span class="sxs-lookup"><span data-stu-id="ff9da-132">Note that this method is equivalent to pulling the battery from the HoloLens, and as such, is a dangerous operation which may leave your device in a corrupt state.</span></span> 

>[!WARNING]
><span data-ttu-id="ff9da-133">これは有害な可能性があるメソッドであり、上記の方法のいずれも動作しない場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="ff9da-133">This is a potentially harmful method and should only be used in the event none of the above methods work.</span></span>

1. <span data-ttu-id="ff9da-134">少なくとも10秒間、電源ボタンを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="ff9da-134">Press and hold the power button for at least 10 seconds</span></span>
   * <span data-ttu-id="ff9da-135">ボタンを10秒より長く保持できます。</span><span class="sxs-lookup"><span data-stu-id="ff9da-135">It’s okay to hold the button for longer than 10 seconds</span></span>
   * <span data-ttu-id="ff9da-136">LED アクティビティは無視しても安全です。</span><span class="sxs-lookup"><span data-stu-id="ff9da-136">It’s safe to ignore any LED activity</span></span>
2. <span data-ttu-id="ff9da-137">ボタンを離し、2-3 秒待機します。</span><span class="sxs-lookup"><span data-stu-id="ff9da-137">Release the button and wait 2-3 seconds</span></span>
3. <span data-ttu-id="ff9da-138">1秒間電源ボタンを押したままデバイスの電源を再度オンにする</span><span class="sxs-lookup"><span data-stu-id="ff9da-138">Power on the device again by pressing and holding the power button for 1 second</span></span>

## <a name="reset-the-device-to-a-factory-clean-state"></a><span data-ttu-id="ff9da-139">デバイスを工場出荷時の状態にリセットする</span><span class="sxs-lookup"><span data-stu-id="ff9da-139">Reset the device to a factory clean state</span></span>

<span data-ttu-id="ff9da-140">再起動後も HoloLens で問題が発生する場合は、工場出荷時の状態にリセットしてみてください。</span><span class="sxs-lookup"><span data-stu-id="ff9da-140">If your HoloLens is still experiencing issues after rebooting, you can try resetting it to a factory clean state.</span></span> <span data-ttu-id="ff9da-141">デバイスをリセットすると、すべての個人データ、アプリ、および設定が消去されます。</span><span class="sxs-lookup"><span data-stu-id="ff9da-141">If you reset your device, all your personal data, apps, and settings will be erased.</span></span> <span data-ttu-id="ff9da-142">リセットによってインストールされるのは、インストールされている最新バージョンの Windows Holographic のみであり、すべての初期化手順 ([調整]、[WiFi への接続]、[ユーザーアカウントの作成]、[アプリのダウンロード] など) を再実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff9da-142">Resetting will only install the latest installed version of Windows Holographic and you will have to redo all the initialization steps (calibrate, connect to WiFi, create a user account, download apps, etc…).</span></span>
1. <span data-ttu-id="ff9da-143">**設定**アプリの起動->**更新** -> の**リセット**</span><span class="sxs-lookup"><span data-stu-id="ff9da-143">Launch the **Settings** app -> **Update** -> **Reset**</span></span>
2. <span data-ttu-id="ff9da-144">**[デバイスのリセット]** オプションを選択し、確認ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="ff9da-144">Select the **Reset device** option and read the confirmation dialog</span></span>
3. <span data-ttu-id="ff9da-145">デバイスをリセットすることに同意すると、デバイスが再起動し、進行状況バーを含むスピン歯車のセットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff9da-145">If you agree to reset your device, the device will reboot and display a set of spinning gears with a progress bar</span></span>
4. <span data-ttu-id="ff9da-146">このプロセスが完了するまで約30分待ちます</span><span class="sxs-lookup"><span data-stu-id="ff9da-146">Wait about 30 minutes for this process to complete</span></span>
5. <span data-ttu-id="ff9da-147">リセットが完了し、すぐに使える状態でデバイスが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="ff9da-147">The reset will complete and the device will reboot into the out of the box experience</span></span>

## <a name="perform-a-full-device-recovery"></a><span data-ttu-id="ff9da-148">完全なデバイスの回復を実行する</span><span class="sxs-lookup"><span data-stu-id="ff9da-148">Perform a full device recovery</span></span>

<span data-ttu-id="ff9da-149">上記のオプションを実行した後**も**、デバイスがフリーズ、応答しない、または更新やソフトウェアの問題が発生した場合は、Windows デバイス回復ツールを使用して回復できます。</span><span class="sxs-lookup"><span data-stu-id="ff9da-149">If, after performing the above options, your device is **still** frozen, unresponsive, or experiencing update or software problems you can recover it using the Windows Device Recovery Tool.</span></span> <span data-ttu-id="ff9da-150">デバイスを回復することは、アプリ、ゲーム、写真、ユーザーアカウントなど、デバイス上のすべてのユーザーコンテンツが消去されるという意味でリセットすることと似ています。</span><span class="sxs-lookup"><span data-stu-id="ff9da-150">Recovering your device is similar to resetting it in the sense that it will erase all user content on the device, including apps, games, photos, user accounts, and more.</span></span> <span data-ttu-id="ff9da-151">可能な場合は、保持する情報をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="ff9da-151">If possible, backup any information you want to keep.</span></span>

<span data-ttu-id="ff9da-152">HoloLens を完全に回復するには:</span><span class="sxs-lookup"><span data-stu-id="ff9da-152">To fully recover your HoloLens:</span></span>
1. <span data-ttu-id="ff9da-153">PC からすべての電話と Windows デバイスを切断する</span><span class="sxs-lookup"><span data-stu-id="ff9da-153">Disconnect all phones and Windows devices from your PC</span></span>
2. <span data-ttu-id="ff9da-154">PC に[Windows デバイス回復ツール](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq)(wdrt) をインストールして起動する</span><span class="sxs-lookup"><span data-stu-id="ff9da-154">Install and launch the [Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) on your PC</span></span>
3. <span data-ttu-id="ff9da-155">付属のマイクロ USB ケーブルを使用して HoloLens を PC に接続する</span><span class="sxs-lookup"><span data-stu-id="ff9da-155">Connect your HoloLens to your PC using the micro-USB cable it came with</span></span>
   * <span data-ttu-id="ff9da-156">すべての USB ケーブルが同じように作成されるわけではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ff9da-156">Note that not all USB cables are created equal.</span></span> <span data-ttu-id="ff9da-157">別のケーブルを正常に使用している場合でも、このフローでは、ケーブルが動作しない可能性がある新しい状態が公開されます。</span><span class="sxs-lookup"><span data-stu-id="ff9da-157">Even if you’ve been using another cable successfully, this flow will expose new states where the cable may not perform as well.</span></span> <span data-ttu-id="ff9da-158">HoloLens が付属しているものが、最適かつ適切にテストされたオプションです。</span><span class="sxs-lookup"><span data-stu-id="ff9da-158">The one your HoloLens came with is the best and most well tested option</span></span>
4. <span data-ttu-id="ff9da-159">ツールがデバイスを自動的に検出した場合は、HoloLens タイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff9da-159">If the tool automatically detects your device it will display a HoloLens tile.</span></span> <span data-ttu-id="ff9da-160">それをクリックし、指示に従ってプロセスを完了します。</span><span class="sxs-lookup"><span data-stu-id="ff9da-160">Click it and follow the instructions to complete the process</span></span>

>[!NOTE]
><span data-ttu-id="ff9da-161">WDRT は、デバイスを古いバージョンの Windows Holographic に回復する場合があります。フラッシュ後に更新プログラムをインストールしなければならない場合があります</span><span class="sxs-lookup"><span data-stu-id="ff9da-161">WDRT may recover your device to an older version of Windows Holographic; you may need to install updates after flashing</span></span>

<span data-ttu-id="ff9da-162">ツールがデバイスを自動的に検出できない場合は、次の操作を試してください。</span><span class="sxs-lookup"><span data-stu-id="ff9da-162">If the tool is unable to detect your device automatically, try the following:</span></span>
1. <span data-ttu-id="ff9da-163">PC を再起動して、もう一度やり直してください (これにより、ほとんどの問題が修正されます)</span><span class="sxs-lookup"><span data-stu-id="ff9da-163">Reboot your PC and try again (this fixes most issues)</span></span>
2. <span data-ttu-id="ff9da-164">[**デバイスは検出されませんでした] ボタン**をクリックし、 **[Microsoft HoloLens]** を選択して、画面の残りの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ff9da-164">Click the **My device was not detected button**, choose **Microsoft HoloLens**, and follow the rest of the instructions on the screen</span></span>
