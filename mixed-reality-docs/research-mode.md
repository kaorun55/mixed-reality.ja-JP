---
title: HoloLens Research モード
description: HoloLens で Research モードを使用すると、アプリケーションは主要なデバイスセンサーストリーム (深さ、環境追跡、および赤外線反射) にアクセスできます。
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: research モード, cv, rs4, コンピュータービジョン, 研究, HoloLens
ms.openlocfilehash: 307df0c226221422f13af09d8f4944c22ead3865
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438308"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="19280-104">HoloLens Research モード</span><span class="sxs-lookup"><span data-stu-id="19280-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="19280-105">この機能は、HoloLens 用の[Windows 10 April 2018 更新プログラム](release-notes-april-2018.md)の一部として追加されたものであり、以前のリリースでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="19280-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="19280-106">Research モードは、デバイス上のキーセンサーへのアプリケーションアクセスを提供する HoloLens の新機能です。</span><span class="sxs-lookup"><span data-stu-id="19280-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="19280-107">次のようなクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="19280-107">These include:</span></span>
- <span data-ttu-id="19280-108">マップの構築とヘッド追跡のためにシステムで使用される4つの環境追跡カメラ。</span><span class="sxs-lookup"><span data-stu-id="19280-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="19280-109">深度カメラデータの2つのバージョン (高周波数 (30 FPS) のほぼ詳細な検出、通常は手動での追跡で使用)、および空間マッピングで現在使用されている低頻度 (1-5 FPS) の詳細な検出用</span><span class="sxs-lookup"><span data-stu-id="19280-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1-5 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="19280-110">IR 反射反射ストリームの2つのバージョン。 HoloLens では深度を計算するために使用されますが、これらのイメージは HoloLens から照らされ、アンビエントライトによって適度に影響を受けないという利点があります。</span><span class="sxs-lookup"><span data-stu-id="19280-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="19280-111">![Research モードアプリのスクリーンショット](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="19280-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="19280-112">*リサーチモードで使用可能な8個のセンサーストリームを表示するテストアプリケーションの mixed reality キャプチャ*</span><span class="sxs-lookup"><span data-stu-id="19280-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="19280-113">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="19280-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="19280-114"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="19280-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="19280-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="19280-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="19280-116"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="19280-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="19280-117">リサーチモード</span><span class="sxs-lookup"><span data-stu-id="19280-117">Research mode</span></span></td>
        <td><span data-ttu-id="19280-118">✔️</span><span class="sxs-lookup"><span data-stu-id="19280-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="19280-119">調査モードを使用する前に</span><span class="sxs-lookup"><span data-stu-id="19280-119">Before using Research mode</span></span>

<span data-ttu-id="19280-120">リサーチモードは、"Computer Vision" と "ロボット" のフィールドの新しいアイデアを試す教育機関および産業用の研究者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="19280-120">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="19280-121">リサーチモードは、企業全体に展開されるか、Microsoft Store で利用可能になるアプリケーションを対象としたものではありません。</span><span class="sxs-lookup"><span data-stu-id="19280-121">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="19280-122">その理由は、リサーチモードはデバイスのセキュリティを低下させ、通常の操作よりもはるかに多くのバッテリ電源を消費するためです。</span><span class="sxs-lookup"><span data-stu-id="19280-122">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="19280-123">今後のデバイスでは、このモードのサポートに対するコミットは行われません。</span><span class="sxs-lookup"><span data-stu-id="19280-123">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="19280-124">そのため、新しいアイデアを開発してテストするために使用することをお勧めします。ただし、リサーチモードを使用するアプリケーションを広く展開することはできません。また、将来のハードウェアでも引き続き動作することが保証されています。</span><span class="sxs-lookup"><span data-stu-id="19280-124">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="19280-125">リサーチモードを有効にする</span><span class="sxs-lookup"><span data-stu-id="19280-125">Enabling Research mode</span></span>

<span data-ttu-id="19280-126">リサーチモードは、開発者モードのサブモードです。</span><span class="sxs-lookup"><span data-stu-id="19280-126">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="19280-127">まず、設定アプリで開発者モードを有効にする必要があります (**開発者向け & セキュリティ > の設定 > 更新**)。</span><span class="sxs-lookup"><span data-stu-id="19280-127">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="19280-128">[開発機能の使用] を **[オン**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="19280-128">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="19280-129">[デバイスポータルを有効にする] を **[オン**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="19280-129">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="19280-130">次に、HoloLens と同じ Wi-fi ネットワークに接続されている web ブラウザーを使用して、HoloLens の IP アドレスに移動します (**設定 > network & Internet > wi-fi > ハードウェアプロパティ**)。</span><span class="sxs-lookup"><span data-stu-id="19280-130">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="19280-131">これは[デバイスポータル](using-the-windows-device-portal.md)であり、ポータルの [システム] セクションに "リサーチモード" ページがあります。</span><span class="sxs-lookup"><span data-stu-id="19280-131">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="19280-132">HoloLens デバイスポータルの ![リサーチモード] タブ](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="19280-132">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="19280-133">*HoloLens デバイスポータルでのリサーチモード*</span><span class="sxs-lookup"><span data-stu-id="19280-133">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="19280-134">[**センサーストリームへのアクセスを許可**する] を選択した後、HoloLens を再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19280-134">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="19280-135">これを行うには、デバイスポータルのページ上部にある [Power] (電源) メニュー項目を使用します。</span><span class="sxs-lookup"><span data-stu-id="19280-135">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="19280-136">デバイスが再起動されると、デバイスポータルから読み込まれたアプリケーションは、リサーチモードのストリームにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="19280-136">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="19280-137">アプリでセンサーデータを使用する</span><span class="sxs-lookup"><span data-stu-id="19280-137">Using sensor data in your apps</span></span>

<span data-ttu-id="19280-138">アプリケーションは、写真/ビデオカメラストリームにアクセスするのとまったく同じ方法で[メディアファンデーション](https://msdn.microsoft.com/library/windows/desktop/ms694197)ストリームを開くことによって、センサーストリームデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="19280-138">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="19280-139">HoloLens 開発に使用できるすべての Api は、リサーチモードでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="19280-139">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="19280-140">特に、アプリケーションは、各センサーフレームのキャプチャ時間において HoloLens が6つの領域にある場所を正確に把握できます。</span><span class="sxs-lookup"><span data-stu-id="19280-140">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="19280-141">さまざまなリサーチモードのストリームにアクセスする方法、組み込みと extrを使用する方法、およびストリームを記録する方法を示すサンプルアプリケーションは、 [HoloLensForCV GitHub リポジトリ](https://github.com/Microsoft/HoloLensForCV)で入手できます。</span><span class="sxs-lookup"><span data-stu-id="19280-141">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="19280-142">既知の問題</span><span class="sxs-lookup"><span data-stu-id="19280-142">Known issues</span></span>

<span data-ttu-id="19280-143">HoloLensForCV リポジトリの[問題トラッカー](https://github.com/Microsoft/HololensForCV/issues)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="19280-143">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="19280-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="19280-144">See also</span></span>

* [<span data-ttu-id="19280-145">Microsoft メディア ファンデーション</span><span class="sxs-lookup"><span data-stu-id="19280-145">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="19280-146">HoloLensForCV GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="19280-146">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="19280-147">Windows Device Portal を使用する</span><span class="sxs-lookup"><span data-stu-id="19280-147">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
