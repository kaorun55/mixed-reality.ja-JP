---
title: HoloLens Research モード
description: HoloLens で Research モードを使用すると、アプリケーションは主要なデバイスセンサーストリーム (深さ、環境追跡、および赤外線反射) にアクセスできます。
author: hferrone
ms.author: v-haferr
ms.date: 05/03/2018
ms.topic: article
keywords: research モード, cv, rs4, コンピュータービジョン, 研究, HoloLens, HoloLens 2
ms.openlocfilehash: ec6f7b73a1f25932f10c10a7f0daaf78e536c0c4
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533104"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="6d5c4-104">HoloLens Research モード</span><span class="sxs-lookup"><span data-stu-id="6d5c4-104">HoloLens Research mode</span></span>

## <a name="overview"></a><span data-ttu-id="6d5c4-105">概要</span><span class="sxs-lookup"><span data-stu-id="6d5c4-105">Overview</span></span>

<span data-ttu-id="6d5c4-106">Research モードは、デバイス上の主要センサーへのアクセスを提供するために、1世代の HoloLens で導入されました。特に、展開を意図していない研究アプリケーションを対象としています。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-106">Research mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="6d5c4-107">次の入力からデータを収集できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-107">You can now gather data from the following inputs:</span></span>

* <span data-ttu-id="6d5c4-108">**可視性の低い環境の追跡カメラ**-システムでヘッドの追跡とマップの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-108">**Visible Light Environment Tracking Cameras** - Used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="6d5c4-109">**深度カメラ**–2つのモードで動作します。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-109">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="6d5c4-110">[ハンドトラッキング](interaction-fundamentals.md)で使用される短いスロー、高頻度 (30 FPS) のほぼ詳細な検出</span><span class="sxs-lookup"><span data-stu-id="6d5c4-110">Short-throw, high-frequency (30 FPS) near-depth sensing used for [Hand Tracking](interaction-fundamentals.md)</span></span>
    + <span data-ttu-id="6d5c4-111">Long throw、低頻度 (1-5 FPS)、[空間マッピング](spatial-mapping.md)で使用される深い深さの検出</span><span class="sxs-lookup"><span data-stu-id="6d5c4-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>
* <span data-ttu-id="6d5c4-112">**IR 反射率ストリームの2つのバージョン**。 HoloLens が計算に使用します。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="6d5c4-113">これらのイメージは赤外線によって照らされ、アンビエントに見える光の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="6d5c4-114">HoloLens 2 を使用している場合は、次の入力にアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-114">If you're using a HoloLens 2 you will also be able to access the following inputs:</span></span>

* <span data-ttu-id="6d5c4-115">**加速度計**–システムによって使用され、X 軸、Y 軸、Z 軸、重力に沿った線形加速度を決定します。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="6d5c4-116">**ジャイロ**–回転を決定するためにシステムによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="6d5c4-117">**磁力計**–絶対方向を推定するためにシステムによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

<span data-ttu-id="6d5c4-118">![Research モードアプリのスクリーンショット](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="6d5c4-118">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="6d5c4-119">*リサーチモードで使用可能な8個のセンサーストリームを表示するテストアプリケーションの mixed reality キャプチャ*</span><span class="sxs-lookup"><span data-stu-id="6d5c4-119">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

> [!NOTE]
> <span data-ttu-id="6d5c4-120">Research モード機能は、HoloLens 用の[Windows 10 April 2018 更新プログラム](release-notes-april-2018.md)の一部として追加されましたが、以前のリリースでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-120">The Research Mode feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

## <a name="usage"></a><span data-ttu-id="6d5c4-121">使用</span><span class="sxs-lookup"><span data-stu-id="6d5c4-121">Usage</span></span>

<span data-ttu-id="6d5c4-122">研究モードは、Computer Vision およびロボットのフィールドの新しいアイデアを調査する教育機関および産業用の研究者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-122">Research mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="6d5c4-123">これは、エンタープライズ環境に配置されているアプリケーションや、Microsoft Store またはその他の配布チャネルを通じて利用できるアプリケーションを対象としていません。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="6d5c4-124">さらに、Microsoft は、今後のハードウェアまたは OS の更新で、リサーチモードまたは同等の機能がサポートされることを保証しません。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-124">Additionally, Microsoft doesn't provide assurances that research mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="6d5c4-125">ただし、これによって、新しいアイデアの開発とテストには使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="6d5c4-126">セキュリティとパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="6d5c4-126">Security and performance</span></span>

<span data-ttu-id="6d5c4-127">リサーチモードを有効にすると、通常の状況下で HoloLens 2 を使用する場合よりも多くのバッテリ電源が使用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-127">Be aware that enabling research mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="6d5c4-128">これは、リサーチモード機能を使用しているアプリケーションが実行されていない場合でも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-128">This is true even if the application using the research mode features is not running.</span></span>  <span data-ttu-id="6d5c4-129">このモードを有効にすると、アプリケーションがセンサーデータを誤用する可能性があるため、デバイスの全体的なセキュリティを低下させることもできます。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="6d5c4-130">デバイスのセキュリティの詳細については、「 [HoloLens のセキュリティ](https://docs.microsoft.com/hololens/hololens-faq-security)に関する FAQ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  


## <a name="device-support"></a><span data-ttu-id="6d5c4-131">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="6d5c4-131">Device support</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><span data-ttu-id="6d5c4-132"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="6d5c4-132"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="6d5c4-133"><a href="hololens-hardware-details.md"><strong>HoloLens ファースト世代</strong></a></span><span class="sxs-lookup"><span data-stu-id="6d5c4-133"><a href="hololens-hardware-details.md"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td><span data-ttu-id="6d5c4-134">ヘッドトラッキングカメラ</span><span class="sxs-lookup"><span data-stu-id="6d5c4-134">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="6d5c4-135">✔️</span><span class="sxs-lookup"><span data-stu-id="6d5c4-135">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="6d5c4-136">IR カメラ & 深度</span><span class="sxs-lookup"><span data-stu-id="6d5c4-136">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="6d5c4-137">✔️</span><span class="sxs-lookup"><span data-stu-id="6d5c4-137">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="6d5c4-138">加速度計</span><span class="sxs-lookup"><span data-stu-id="6d5c4-138">Accelerometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="6d5c4-139">ジャイロスコープ</span><span class="sxs-lookup"><span data-stu-id="6d5c4-139">Gyroscope</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="6d5c4-140">磁力計</span><span class="sxs-lookup"><span data-stu-id="6d5c4-140">Magnetometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="6d5c4-141">HoloLens 2 のリサーチモードのサポートは、2020年7月にパブリックプレビューで提供される予定であり、上記のすべての機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-141">Research Mode support for HoloLens 2 is expected to be available in public preview in July 2020 and will include all the features listed above.</span></span> <span data-ttu-id="6d5c4-142">詳細については、もう一度確認してください。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-142">Please check back for more information.</span></span> 

## <a name="enabling-research-mode"></a><span data-ttu-id="6d5c4-143">リサーチモードを有効にする</span><span class="sxs-lookup"><span data-stu-id="6d5c4-143">Enabling Research mode</span></span>

<span data-ttu-id="6d5c4-144">リサーチモードは、開発者モードの拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-144">Research mode is an extension of Developer Mode.</span></span> <span data-ttu-id="6d5c4-145">開始する前に、デバイスの開発機能を有効にして、リサーチモードの設定にアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-145">Before starting, the developer features of the device need to be enabled to access the research mode settings:</span></span> 

* <span data-ttu-id="6d5c4-146">[**スタート] メニューを開き > 設定**を開き、[**更新プログラム**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-146">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="6d5c4-147">**開発者向けに**選択し、**開発者モード**を有効にします。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-147">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="6d5c4-148">下へスクロールし、**デバイスポータル**を有効にします。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-148">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="6d5c4-149">開発者機能が有効になったら、[デバイスポータルに接続](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens)して、リサーチモード機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-149">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the research mode features.</span></span>

<span data-ttu-id="6d5c4-150">*HoloLens ファースト世代*:</span><span class="sxs-lookup"><span data-stu-id="6d5c4-150">On *HoloLens 1st Gen*:</span></span>

* <span data-ttu-id="6d5c4-151">**デバイスポータル**で、**システム > リサーチモード**に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-151">Go to **System > Research mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="6d5c4-152">[**センサーストリームへのアクセスを許可する**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-152">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="6d5c4-153">ページの上部にある**電源**メニュー項目からデバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-153">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="6d5c4-154">デバイスを再起動すると、**デバイスポータル**から読み込まれたアプリケーションは、リサーチモードのストリームにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-154">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research mode streams.</span></span>

<span data-ttu-id="6d5c4-155">![HoloLens デバイスポータルの [リサーチモード] タブ](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="6d5c4-155">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="6d5c4-156">*HoloLens デバイスポータルの [リサーチモード] ウィンドウ*</span><span class="sxs-lookup"><span data-stu-id="6d5c4-156">*Research mode window in the HoloLens Device Portal*</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="6d5c4-157">アプリでセンサーデータを使用する</span><span class="sxs-lookup"><span data-stu-id="6d5c4-157">Using sensor data in your apps</span></span>

<span data-ttu-id="6d5c4-158">*HoloLens ファースト世代*</span><span class="sxs-lookup"><span data-stu-id="6d5c4-158">*HoloLens 1st Gen*</span></span>

<span data-ttu-id="6d5c4-159">アプリケーションは、[メディアファンデーション](https://msdn.microsoft.com/library/windows/desktop/ms694197)を使用して写真とビデオのカメラストリームにアクセスするのと同じ方法でセンサーストリームデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-159">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="6d5c4-160">HoloLens 開発に使用できるすべての Api は、リサーチモードでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-160">All APIs that work for HoloLens development are also available in Research mode.</span></span> <span data-ttu-id="6d5c4-161">具体的には、アプリケーションは、各センサーフレームのキャプチャ時間で HoloLens が6つの領域にあることを正確に把握しています。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-161">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="6d5c4-162">さまざまなリサーチモードのストリームにアクセスする方法、[組み込みと extrを](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)使用する方法、 [HoloLensForCV GitHub リポジトリ](https://github.com/Microsoft/HoloLensForCV)リポジトリにストリームを記録する方法に関するサンプルアプリケーションを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-162">You can find sample applications on how to access the various Research mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="6d5c4-163">現時点では、HoloLensForCV サンプルは HoloLens 2 では機能しません。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-163">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="known-issues"></a><span data-ttu-id="6d5c4-164">既知の問題</span><span class="sxs-lookup"><span data-stu-id="6d5c4-164">Known issues</span></span>

<span data-ttu-id="6d5c4-165">HoloLensForCV リポジトリの[問題トラッカー](https://github.com/Microsoft/HololensForCV/issues)を使用して、既知の問題に従うことができます。</span><span class="sxs-lookup"><span data-stu-id="6d5c4-165">You can use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to follow known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d5c4-166">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="6d5c4-166">See also</span></span>

* [<span data-ttu-id="6d5c4-167">Microsoft メディア ファンデーション</span><span class="sxs-lookup"><span data-stu-id="6d5c4-167">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="6d5c4-168">HoloLensForCV GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="6d5c4-168">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="6d5c4-169">Windows Device Portal を使用する</span><span class="sxs-lookup"><span data-stu-id="6d5c4-169">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
