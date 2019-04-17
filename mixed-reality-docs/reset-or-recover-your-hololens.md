---
title: リセットするか、HoloLens の回復
description: 再起動またはリセット、HoloLens の基本および詳細の両方の手順です。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: ハウツー、再起動、リセット、回復、ハード リセット、ソフト リセット、電源を入れ、HoloLens、シャット ダウン
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599881"
---
# <a name="reset-or-recover-your-hololens"></a><span data-ttu-id="6c5ac-104">リセットするか、HoloLens の回復</span><span class="sxs-lookup"><span data-stu-id="6c5ac-104">Reset or recover your HoloLens</span></span>

<span data-ttu-id="6c5ac-105">再起動をお試したい場合があります、HoloLens の問題が発生した場合は、リセット、またはもデバイスの復旧を再フラッシュします。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-105">If you’re experiencing problems with your HoloLens you may want to try a restart, reset, or even re-flash with device recovery.</span></span> <span data-ttu-id="6c5ac-106">このドキュメントで連続して推奨される手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-106">This document will guide you through the recommended steps in succession.</span></span>

## <a name="perform-a-device-reboot"></a><span data-ttu-id="6c5ac-107">デバイスの再起動を実行します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-107">Perform a device reboot</span></span>

<span data-ttu-id="6c5ac-108">場合、HoloLens の問題が発生している、またはが応答していない場合は、いずれかを使用してそれを再起動してみます最初に、以下のメソッド。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-108">If your HoloLens is experiencing issues or is unresponsive, first try rebooting it via one of the below methods.</span></span>

### <a name="perform-a-safe-reboot-via-cortana"></a><span data-ttu-id="6c5ac-109">Cortana を使用して安全な再起動を実行します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-109">Perform a safe reboot via Cortana</span></span>

<span data-ttu-id="6c5ac-110">HoloLens を再起動する最も安全な方法は、Cortana を使用してです。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-110">The safest way to reboot the HoloLens is via Cortana.</span></span> <span data-ttu-id="6c5ac-111">これは、HoloLens の問題が発生しているときに優れた最初の手順では一般に。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-111">This is generally a great first-step when experiencing an issue with HoloLens:</span></span>
1. <span data-ttu-id="6c5ac-112">デバイス上に配置します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-112">Put on your device</span></span>
2. <span data-ttu-id="6c5ac-113">電源を入れ、ユーザーがログインし、デバイスがロックを解除するパスワードを待機していないようにします。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-113">Make sure it’s powered on, a user is logged in, and the device is not waiting for a password to unlock it.</span></span>
3. <span data-ttu-id="6c5ac-114">「コルタナさん、再起動や"「コルタナさん、再起動します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-114">Say “Hey Cortana, reboot” or "Hey Cortana, restart."</span></span>
4. <span data-ttu-id="6c5ac-115">彼女が確認されるときに彼女は要求を確認します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-115">When she acknowledges she will ask you for confirmation.</span></span> <span data-ttu-id="6c5ac-116">彼女が完了した後、自分の質問に彼女がリッスンしていることを示すを再生するサウンドをちょっと待ってくださいし、言い、"Yes"</span><span class="sxs-lookup"><span data-stu-id="6c5ac-116">Wait a second for a sound to play after she has finished her question, indicating she is listening to you and then say “Yes.”</span></span>
5. <span data-ttu-id="6c5ac-117">デバイスは今すぐ再起動/再起動します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-117">The device will now reboot/restart.</span></span>

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a><span data-ttu-id="6c5ac-118">Windows Device Portal 経由で安全な再起動を実行します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-118">Perform a safe reboot via Windows Device Portal</span></span>

<span data-ttu-id="6c5ac-119">使用してデバイスを再起動しようとすることができます、上記でうまくいかない場合[Windows Device Portal](using-the-windows-device-portal.md)します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-119">If the above doesn't work, you can try to reboot the device via [Windows Device Portal](using-the-windows-device-portal.md).</span></span> <span data-ttu-id="6c5ac-120">右上隅のオプションがある再起動またはシャット ダウンするデバイス。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-120">In the upper right corner, there is an option to restart/shutdown the device.</span></span>

### <a name="perform-a-safe-reboot-via-the-power-button"></a><span data-ttu-id="6c5ac-121">[電源] ボタンを使用して安全な再起動を実行します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-121">Perform a safe reboot via the power button</span></span>

<span data-ttu-id="6c5ac-122">場合は、デバイスを再起動することはできませんが、電源ボタンを使用して、再起動を発行しようとすることができます。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-122">If you still can't reboot your device, you can try to issue a reboot via the power button:</span></span>
1. <span data-ttu-id="6c5ac-123">5 秒間の電源ボタンを長押しし</span><span class="sxs-lookup"><span data-stu-id="6c5ac-123">Press and hold the power button for 5 seconds</span></span>
   1. <span data-ttu-id="6c5ac-124">1 秒後に、緩やかに変化をオフに右から左に、5 つのすべての Led 照射が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-124">After 1 second, you will see all 5 LEDs illuminate, then slowly turn off from right to left</span></span>
   2. <span data-ttu-id="6c5ac-125">5 秒後にすべての Led はオフに、シャット ダウン コマンドが正常に実行されたことを示す</span><span class="sxs-lookup"><span data-stu-id="6c5ac-125">After 5 seconds, all LEDs will be off, indicating the shutdown command was issued successfully</span></span>
   3. <span data-ttu-id="6c5ac-126">ただし、すべての Led がオフにした直後にボタンを押してを停止することが重要</span><span class="sxs-lookup"><span data-stu-id="6c5ac-126">Note, it’s important to stop pressing the button immediately after all the LEDs have turned off</span></span>
2. <span data-ttu-id="6c5ac-127">1 分をクリーンに正常にシャット ダウンを待機します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-127">Wait 1 minute for the shutdown to cleanly succeed.</span></span> <span data-ttu-id="6c5ac-128">ディスプレイがオフになっている場合でも、シャット ダウンがありますので注意が進行中であります。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-128">Note that the shutdown may still be in progress even if the displays are off</span></span>
3. <span data-ttu-id="6c5ac-129">1 秒間の電源ボタンを押したまま、もう一度デバイスの電源</span><span class="sxs-lookup"><span data-stu-id="6c5ac-129">Power on the device again by pressing and holding the power button for 1 second</span></span>

### <a name="perform-an-unsafe-forced-reboot"></a><span data-ttu-id="6c5ac-130">安全でないの強制再起動を実行します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-130">Perform an unsafe forced reboot</span></span>

<span data-ttu-id="6c5ac-131">上記のメソッドのいずれも正常にデバイスを再起動することが、再起動を強制することができます。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-131">If none of the above methods are able to successfully reboot your device, you can force a reboot.</span></span> <span data-ttu-id="6c5ac-132">このメソッドは、HoloLens から、バッテリのプルと等価であり、そのため、破損状態で、デバイスをしまう可能性がありますが、危険な操作には注意してください。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-132">Note that this method is equivalent to pulling the battery from the HoloLens, and as such, is a dangerous operation which may leave your device in a corrupt state.</span></span> 

>[!WARNING]
><span data-ttu-id="6c5ac-133">これは害を及ぼす可能性のあるメソッドであり、上記のメソッドのいずれでも、イベントにのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-133">This is a potentially harmful method and should only be used in the event none of the above methods work.</span></span>

1. <span data-ttu-id="6c5ac-134">少なくとも 10 秒間の電源ボタンを長押しし</span><span class="sxs-lookup"><span data-stu-id="6c5ac-134">Press and hold the power button for at least 10 seconds</span></span>
   * <span data-ttu-id="6c5ac-135">10 秒より長くのボタンを保持するためにも問題ありません。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-135">It’s okay to hold the button for longer than 10 seconds</span></span>
   * <span data-ttu-id="6c5ac-136">それは、led を無視して</span><span class="sxs-lookup"><span data-stu-id="6c5ac-136">It’s safe to ignore any LED activity</span></span>
2. <span data-ttu-id="6c5ac-137">ボタンを放すし、2 ~ 3 秒間の待機</span><span class="sxs-lookup"><span data-stu-id="6c5ac-137">Release the button and wait 2-3 seconds</span></span>
3. <span data-ttu-id="6c5ac-138">1 秒間の電源ボタンを押したまま、もう一度デバイスの電源</span><span class="sxs-lookup"><span data-stu-id="6c5ac-138">Power on the device again by pressing and holding the power button for 1 second</span></span>

## <a name="reset-the-device-to-a-factory-clean-state"></a><span data-ttu-id="6c5ac-139">デバイスを工場出荷時のクリーンな状態にリセットします。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-139">Reset the device to a factory clean state</span></span>

<span data-ttu-id="6c5ac-140">場合は、HoloLens の再起動後、問題を解消は、工場出荷時のクリーンな状態にリセットもかまいません。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-140">If your HoloLens is still experiencing issues after rebooting, you can try resetting it to a factory clean state.</span></span> <span data-ttu-id="6c5ac-141">デバイスをリセットする場合は、すべての個人データ、アプリ、および設定が消去されます。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-141">If you reset your device, all your personal data, apps, and settings will be erased.</span></span> <span data-ttu-id="6c5ac-142">リセットすると、最新バージョンにインストールされているバージョンの Windows Holographic はのみインストールし、初期化の手順をすべて元に戻す必要があります (調整、WiFi に接続する、ユーザー アカウントを作成、アプリなどをダウンロードします.)。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-142">Resetting will only install the latest installed version of Windows Holographic and you will have to redo all the initialization steps (calibrate, connect to WiFi, create a user account, download apps, etc…).</span></span>
1. <span data-ttu-id="6c5ac-143">起動、**設定**アプリ]-> [ **Update** -> **リセット**</span><span class="sxs-lookup"><span data-stu-id="6c5ac-143">Launch the **Settings** app -> **Update** -> **Reset**</span></span>
2. <span data-ttu-id="6c5ac-144">選択、**リセット デバイス**オプションを選択し、確認のダイアログ ボックスの読み取り</span><span class="sxs-lookup"><span data-stu-id="6c5ac-144">Select the **Reset device** option and read the confirmation dialog</span></span>
3. <span data-ttu-id="6c5ac-145">デバイスをリセットすることに同意する場合、デバイスは再起動して、進行状況バーの歯車をスピンのセットを表示</span><span class="sxs-lookup"><span data-stu-id="6c5ac-145">If you agree to reset your device, the device will reboot and display a set of spinning gears with a progress bar</span></span>
4. <span data-ttu-id="6c5ac-146">このプロセスが完了するのに約 30 分の待機します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-146">Wait about 30 minutes for this process to complete</span></span>
5. <span data-ttu-id="6c5ac-147">リセットが完了し、エクスペリエンスの外にデバイスが再起動</span><span class="sxs-lookup"><span data-stu-id="6c5ac-147">The reset will complete and the device will reboot into the out of the box experience</span></span>

## <a name="perform-a-full-device-recovery"></a><span data-ttu-id="6c5ac-148">デバイスの完全回復を実行します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-148">Perform a full device recovery</span></span>

<span data-ttu-id="6c5ac-149">デバイスは、上記のオプションを実行する場合は、**まだ**凍結、応答しない場合、または発生している更新プログラムまたはソフトウェアの問題、Windows Device Recovery Tool を使用して回復することができます。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-149">If, after performing the above options, your device is **still** frozen, unresponsive, or experiencing update or software problems you can recover it using the Windows Device Recovery Tool.</span></span> <span data-ttu-id="6c5ac-150">デバイスを回復することは、アプリ、ゲーム、写真、ユーザー アカウント、および詳細を含む、デバイス上のすべてのユーザー コンテンツが消去されるという意味で再設定することに似ています。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-150">Recovering your device is similar to resetting it in the sense that it will erase all user content on the device, including apps, games, photos, user accounts, and more.</span></span> <span data-ttu-id="6c5ac-151">可能であれば、保持するすべての情報をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-151">If possible, backup any information you want to keep.</span></span>

<span data-ttu-id="6c5ac-152">HoloLens を完全に復旧するには。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-152">To fully recover your HoloLens:</span></span>
1. <span data-ttu-id="6c5ac-153">お使いの PC からすべての電話と Windows デバイスを切断します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-153">Disconnect all phones and Windows devices from your PC</span></span>
2. <span data-ttu-id="6c5ac-154">インストール、起動、 [Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) PC に</span><span class="sxs-lookup"><span data-stu-id="6c5ac-154">Install and launch the [Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) on your PC</span></span>
3. <span data-ttu-id="6c5ac-155">HoloLens を含まれていますが、マイクロ USB ケーブルを使用して PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-155">Connect your HoloLens to your PC using the micro-USB cable it came with</span></span>
   * <span data-ttu-id="6c5ac-156">等しいすべての USB ケーブルが作成されたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-156">Note that not all USB cables are created equal.</span></span> <span data-ttu-id="6c5ac-157">場合でも、使用した別のケーブルが正常に、このフローは、ケーブルをも実行しない可能性があります、新しい状態を公開します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-157">Even if you’ve been using another cable successfully, this flow will expose new states where the cable may not perform as well.</span></span> <span data-ttu-id="6c5ac-158">最適なと十分にテストされた最もオプションは、HoloLens に付属</span><span class="sxs-lookup"><span data-stu-id="6c5ac-158">The one your HoloLens came with is the best and most well tested option</span></span>
4. <span data-ttu-id="6c5ac-159">ツールは、デバイスを自動的に検出された場合は、HoloLens のタイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-159">If the tool automatically detects your device it will display a HoloLens tile.</span></span> <span data-ttu-id="6c5ac-160">それをクリックしてプロセスを完了する手順</span><span class="sxs-lookup"><span data-stu-id="6c5ac-160">Click it and follow the instructions to complete the process</span></span>

>[!NOTE]
><span data-ttu-id="6c5ac-161">WDRT は以前のバージョンの Windows Holographic; は、デバイスを復旧できます。点滅した後、更新プログラムをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-161">WDRT may recover your device to an older version of Windows Holographic; you may need to install updates after flashing</span></span>

<span data-ttu-id="6c5ac-162">ツールで、デバイスを自動的に検出することがない場合は、次の操作を再試行してください。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-162">If the tool is unable to detect your device automatically, try the following:</span></span>
1. <span data-ttu-id="6c5ac-163">(ほとんどの問題を修正) もう一度やり直すして PC を再起動します。</span><span class="sxs-lookup"><span data-stu-id="6c5ac-163">Reboot your PC and try again (this fixes most issues)</span></span>
2. <span data-ttu-id="6c5ac-164">をクリックして、**自分のデバイスは検出されませんでしたボタン**、選択**Microsoft HoloLens**画面に次の手順の残りの部分と</span><span class="sxs-lookup"><span data-stu-id="6c5ac-164">Click the **My device was not detected button**, choose **Microsoft HoloLens**, and follow the rest of the instructions on the screen</span></span>
