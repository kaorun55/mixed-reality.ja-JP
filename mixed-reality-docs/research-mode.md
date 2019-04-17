---
title: HoloLens 研究モード
description: HoloLens の研究モードを使用して、アプリケーションは、主要なデバイス センサー ストリーム (深さ、追跡、環境および IR 反射) にアクセスできます。
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: モード、cv、rs4、コンピューター ビジョン研究、HoloLens を調査します。
ms.openlocfilehash: 5feda021bd6a1a90fd98c751b1cea768eed980af
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597511"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="190a9-104">HoloLens 研究モード</span><span class="sxs-lookup"><span data-stu-id="190a9-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="190a9-105">この機能は、の一部として追加された、 [Windows 10 April 2018 Update](release-notes-april-2018.md) HoloLens のと、以前のリリースでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="190a9-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="190a9-106">研究モードは、デバイスにアプリケーション キーのセンサーへのアクセスを提供する HoloLens の新しい機能です。</span><span class="sxs-lookup"><span data-stu-id="190a9-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="190a9-107">次のようなクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="190a9-107">These include:</span></span>
- <span data-ttu-id="190a9-108">4 つのマップの構築と head の追跡、システムで使用されるカメラを追跡する環境。</span><span class="sxs-lookup"><span data-stu-id="190a9-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="190a9-109">深度カメラ データ – 高頻度 (30 FPS) 深さの近くの検知、一般的に使用される追跡と低頻度 (1 FPS) 深さまで検出用の 2 つのバージョンは、空間のマッピングによって現在使用</span><span class="sxs-lookup"><span data-stu-id="190a9-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="190a9-110">これらのイメージ、HoloLens から明るいとある程度周辺光による影響を受けるは、深さが価値ある独自の権限でのコンピューティングするために使用、HoloLens、IR 反射ストリームの 2 つのバージョン。</span><span class="sxs-lookup"><span data-stu-id="190a9-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="190a9-111">![Research モードのアプリのスクリーン ショット](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="190a9-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="190a9-112">*Research モードで使用可能な 8 つのセンサー ストリームを表示するテスト アプリケーションの複合現実のキャプチャ*</span><span class="sxs-lookup"><span data-stu-id="190a9-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="190a9-113">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="190a9-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="190a9-114">機能</span><span class="sxs-lookup"><span data-stu-id="190a9-114">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="190a9-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="190a9-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="190a9-116"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="190a9-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="190a9-117">研究モード</span><span class="sxs-lookup"><span data-stu-id="190a9-117">Research mode</span></span></td><td style="text-align: center;"> <span data-ttu-id="190a9-118">✔️</span><span class="sxs-lookup"><span data-stu-id="190a9-118">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="190a9-119">調査モードを使用する前に</span><span class="sxs-lookup"><span data-stu-id="190a9-119">Before using Research mode</span></span>

<span data-ttu-id="190a9-120">という名前の研究モード: コンピューター ビジョンとロボット工学のフィールドに新しいアイデアを試す学術的および産業の研究者に適しています。</span><span class="sxs-lookup"><span data-stu-id="190a9-120">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="190a9-121">研究モードは、企業全体に展開または Microsoft Store で使用できるアプリケーションのものではありません。</span><span class="sxs-lookup"><span data-stu-id="190a9-121">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="190a9-122">この理由は、研究モードは、デバイスのセキュリティを削減し、通常の操作よりもはるかに多くのバッテリ電力を消費です。</span><span class="sxs-lookup"><span data-stu-id="190a9-122">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="190a9-123">Microsoft は、将来のデバイスでこのモードをサポートしていないコミットしています。</span><span class="sxs-lookup"><span data-stu-id="190a9-123">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="190a9-124">そのため、開発し、新しいアイデアをテストに使用する推奨します。ただし、広くは引き続き将来のハードウェアで動作する任意の保証、研究モードを使用して、またはアプリケーションをデプロイすることはできません。</span><span class="sxs-lookup"><span data-stu-id="190a9-124">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="190a9-125">調査モードを有効にします。</span><span class="sxs-lookup"><span data-stu-id="190a9-125">Enabling Research mode</span></span>

<span data-ttu-id="190a9-126">研究モードは、開発者モードのサブ モードです。</span><span class="sxs-lookup"><span data-stu-id="190a9-126">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="190a9-127">まず、設定アプリで開発者モードを有効にする必要があります (**設定 > 更新とセキュリティ > 開発者向け**)。</span><span class="sxs-lookup"><span data-stu-id="190a9-127">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="190a9-128">「開発者向けの機能を使用して、」を設定**で**</span><span class="sxs-lookup"><span data-stu-id="190a9-128">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="190a9-129">「デバイスのポータルを有効にする」を設定**で**</span><span class="sxs-lookup"><span data-stu-id="190a9-129">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="190a9-130">HoloLens の IP アドレスに移動し、HoloLens と同じ Wi-fi ネットワークに接続されている web ブラウザーを使用して (経由で取得した**設定 > ネットワークとインターネット > Wi-fi > ハードウェア プロパティ**)。</span><span class="sxs-lookup"><span data-stu-id="190a9-130">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="190a9-131">これは、[デバイス ポータル](using-the-windows-device-portal.md)、およびポータルの"System"セクションでは「Research モード」ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="190a9-131">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="190a9-132">![HoloLens デバイス ポータルの [モード] タブを調査します。](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="190a9-132">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="190a9-133">*HoloLens デバイスのポータルでの研究モード*</span><span class="sxs-lookup"><span data-stu-id="190a9-133">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="190a9-134">選択した後**センサー ストリームへのアクセスを許可する**HoloLens を再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="190a9-134">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="190a9-135">これは、ページの上部にある"Power"のメニュー項目で、デバイス ポータルから行うことができます。</span><span class="sxs-lookup"><span data-stu-id="190a9-135">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="190a9-136">デバイスの再起動後デバイス ポータルから読み込まれているアプリケーションは Research モードのストリームにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="190a9-136">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="190a9-137">アプリでのセンサー データの使用</span><span class="sxs-lookup"><span data-stu-id="190a9-137">Using sensor data in your apps</span></span>

<span data-ttu-id="190a9-138">アプリケーションは開くことでセンサー データのストリームにアクセスできます[メディア ファンデーション](https://msdn.microsoft.com/library/windows/desktop/ms694197)写真とビデオのカメラのストリームにアクセスする、まったく同じ方法でストリーム。</span><span class="sxs-lookup"><span data-stu-id="190a9-138">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="190a9-139">HoloLens の開発に使用できるすべての Api も調査モードで使用できます。</span><span class="sxs-lookup"><span data-stu-id="190a9-139">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="190a9-140">具体的には、アプリケーションは正確に場所がわかっている HoloLens 6 dof 領域で各センサーのフレームのキャプチャ時にします。</span><span class="sxs-lookup"><span data-stu-id="190a9-140">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="190a9-141">さまざまな調査モードのストリームにアクセスする方法、組み込みおよび extrinsics を使用する方法、およびストリームを記録する方法を示すサンプル アプリケーションが表示されます、 [HoloLensForCV GitHub リポジトリ](https://github.com/Microsoft/HoloLensForCV)します。</span><span class="sxs-lookup"><span data-stu-id="190a9-141">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="190a9-142">既知の問題</span><span class="sxs-lookup"><span data-stu-id="190a9-142">Known issues</span></span>

<span data-ttu-id="190a9-143">参照してください、 [issue トラッカー](https://github.com/Microsoft/HololensForCV/issues) HoloLensForCV リポジトリにします。</span><span class="sxs-lookup"><span data-stu-id="190a9-143">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="190a9-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="190a9-144">See also</span></span>

* [<span data-ttu-id="190a9-145">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="190a9-145">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="190a9-146">HoloLensForCV GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="190a9-146">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="190a9-147">Windows Device Portal のを使用</span><span class="sxs-lookup"><span data-stu-id="190a9-147">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
