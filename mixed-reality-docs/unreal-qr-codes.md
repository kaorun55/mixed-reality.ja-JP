---
title: Unreal での QR コード
description: Unreal で QR コードを使用するためのガイド
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, QR コード
ms.openlocfilehash: a53fad14ab76136f1da419379dd39eca3a29701a
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376104"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="2807e-104">Unreal での QR コード</span><span class="sxs-lookup"><span data-stu-id="2807e-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="2807e-105">概要</span><span class="sxs-lookup"><span data-stu-id="2807e-105">Overview</span></span>

<span data-ttu-id="2807e-106">HoloLens 2 では、Web カメラを使用してワールド空間の QR コードを表示できます。これにより、各コードの実際の位置の座標系を使用して、QR コードをホログラムとしてレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="2807e-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="2807e-107">HoloLens 2 は、単一の QR コードに加えて、複数のデバイスの同じ場所にホログラムをレンダリングして、エクスペリエンスを共有することもできます。</span><span class="sxs-lookup"><span data-stu-id="2807e-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="2807e-108">アプリケーションに QR コードを追加するためのベスト プラクティスに従っていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2807e-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="2807e-109">サイレント ゾーン</span><span class="sxs-lookup"><span data-stu-id="2807e-109">Quiet zones</span></span>
- <span data-ttu-id="2807e-110">照明と背景</span><span class="sxs-lookup"><span data-stu-id="2807e-110">Lighting and backdrop</span></span>
- <span data-ttu-id="2807e-111">サイズ、距離、および角度の位置</span><span class="sxs-lookup"><span data-stu-id="2807e-111">Size, distance, and angular position</span></span>

<span data-ttu-id="2807e-112">QR コードがアプリに配置されている場合、[環境への配慮](environment-considerations-for-hololens.md)に特に注意してください。</span><span class="sxs-lookup"><span data-stu-id="2807e-112">Pay special attention to the [environment considerations](environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="2807e-113">これらの各トピックの詳細と、必要な NuGet パッケージをダウンロードする方法の手順については、メインの [QR コードの追跡](qr-code-tracking.md)ドキュメントをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2807e-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](qr-code-tracking.md) document.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="2807e-114">QR 検出の有効化</span><span class="sxs-lookup"><span data-stu-id="2807e-114">Enabling QR detection</span></span>
<span data-ttu-id="2807e-115">HoloLens 2 で QR コードを表示するには Web カメラを使用する必要があるため、プロジェクトの設定で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2807e-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="2807e-116">**[編集] > [プロジェクトの設定]** を開いて、 **[プラットフォーム]** セクションまでスクロールし、 **[HoloLens]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2807e-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="2807e-117">**[機能]** セクションを展開し、 **[Web カメラ]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="2807e-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="2807e-118">[ARSessionConfig アセットを追加する](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)ことによって、QR コードの追跡をオプトインする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="2807e-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

<span data-ttu-id="2807e-119">使用する前に、`UHoloLensARFunctionLibrary::StartQRCodeCapture()` を呼び出して、追跡を手動で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2807e-119">Right before the usage, you should manually enable the tracking by calling `UHoloLensARFunctionLibrary::StartQRCodeCapture()`.</span></span> <span data-ttu-id="2807e-120">QR コードの追跡を終了したら、デバイス リソースを保存するために、`UHoloLensARFunctionLibrary::StopCameraCapture()` で追跡を無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2807e-120">After ending the QR code tracking, you should disable it by `UHoloLensARFunctionLibrary::StopCameraCapture()` to save the device resources.</span></span> 

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="2807e-121">追跡対象のイメージの設定</span><span class="sxs-lookup"><span data-stu-id="2807e-121">Setting up a tracked image</span></span>

<span data-ttu-id="2807e-122">QR コードは、追跡対象のイメージとして、Unreal の AR で追跡されたジオメトリ システムによって表示されます。</span><span class="sxs-lookup"><span data-stu-id="2807e-122">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="2807e-123">これを利用するには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="2807e-123">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="2807e-124">ブループリントを作成し、**ARTrackableNotify** コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="2807e-124">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![QR の AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="2807e-126">**ARTrackableNotify** を選択し、 **[詳細]** パネルの **[イベント]** セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="2807e-126">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span> 

![QR のイベント](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="2807e-128">**[On Add Tracked Geometry]** の横にある **+** をクリックして、ノードをイベント グラフに追加します。</span><span class="sxs-lookup"><span data-stu-id="2807e-128">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="2807e-129">イベントの完全な一覧については、[UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) コンポーネント API を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2807e-129">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

![QR のレンダリングの例](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="2807e-131">追跡対象のイメージの使用</span><span class="sxs-lookup"><span data-stu-id="2807e-131">Using a tracked image</span></span>
<span data-ttu-id="2807e-132">次の画像のイベント グラフは、QR コードの中心にポイントをレンダリングし、そのデータを出力するために使用される **OnUpdateTrackedImage** イベントを示しています。</span><span class="sxs-lookup"><span data-stu-id="2807e-132">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span> 

![QR のレンダリングの例](images/unreal-qr-render.PNG)

<span data-ttu-id="2807e-134">流れについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2807e-134">Here's what's going on:</span></span>
1. <span data-ttu-id="2807e-135">最初に、追跡したイメージが **ARTrackedQRCode** にキャストされ、現在の更新されたイメージが QR コードであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2807e-135">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="2807e-136">エンコードされたデータは **QRCode** 変数から取得されます。</span><span class="sxs-lookup"><span data-stu-id="2807e-136">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="2807e-137">**GetLocalToWorldTransform** の位置と **GetEstimateSize** のディメンションから QR コードの左上を取得できます。</span><span class="sxs-lookup"><span data-stu-id="2807e-137">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span> 

<span data-ttu-id="2807e-138">また、コードで [QR コードの座標系を取得する](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)こともできます。</span><span class="sxs-lookup"><span data-stu-id="2807e-138">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="2807e-139">一意の ID の検索</span><span class="sxs-lookup"><span data-stu-id="2807e-139">Finding the unique ID</span></span>
<span data-ttu-id="2807e-140">すべての QR コードには、一意の GUID ID があります。これは、次の方法で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="2807e-140">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="2807e-141">**As ARTracked QRCode** ピンをドラッグ アンド ドロップして、**Get Unique ID** を検索します。</span><span class="sxs-lookup"><span data-stu-id="2807e-141">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![QR の GUID](images/unreal-qr-guid.PNG)

<span data-ttu-id="2807e-143">QR コードを使用してバックグラウンドで多くの処理が行われているため、これで終わりというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="2807e-143">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="2807e-144">内部的な処理の詳細については、次のリンクを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2807e-144">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="see-also"></a><span data-ttu-id="2807e-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="2807e-145">See also</span></span>
* [<span data-ttu-id="2807e-146">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="2807e-146">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="2807e-147">ホログラム</span><span class="sxs-lookup"><span data-stu-id="2807e-147">Holograms</span></span>](hologram.md)
* [<span data-ttu-id="2807e-148">座標系</span><span class="sxs-lookup"><span data-stu-id="2807e-148">Coordinate systems</span></span>](coordinate-systems.md)
