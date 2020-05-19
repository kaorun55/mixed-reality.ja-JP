---
title: Unreal での QR コード
description: Unreal で QR コードを使用するためのガイド
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, QR コード
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342660"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="46440-104">Unreal での QR コード</span><span class="sxs-lookup"><span data-stu-id="46440-104">QR codes in Unreal</span></span>

<span data-ttu-id="46440-105">HoloLens では、空間上の QR コードを見つけて、現実世界の既知の位置にホログラムをレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="46440-105">HoloLens can locate QR codes in world space to render holograms at known positions in the real world.</span></span>  <span data-ttu-id="46440-106">これは、エクスペリエンスを共有するために、同じ場所にある複数のデバイスでホログラムをレンダリングするためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="46440-106">This can also be used to render holograms on multiple devices in the same location to create a shared experience.</span></span> 

<span data-ttu-id="46440-107">HoloLens で QR の検出を有効にするには、[プロジェクト設定] > [プラットフォーム] > [HoloLens] > [機能] の下にある Unreal エディターで、"Web カメラ" 機能を確実にオンにします。</span><span class="sxs-lookup"><span data-stu-id="46440-107">To enable QR detection on HoloLens, ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="46440-108">StartARSession 関数を使用して ARSession を開始することにより、Unreal で QR コード追跡を使用することをオプトインします。</span><span class="sxs-lookup"><span data-stu-id="46440-108">Opt into using QR code tracking in Unreal by starting an ARSession with the StartARSession function.</span></span> 

<span data-ttu-id="46440-109">QR コードは、追跡対象のイメージとして、Unreal の AR で追跡されたジオメトリ システムによって表示されます。</span><span class="sxs-lookup"><span data-stu-id="46440-109">QR Codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span>  <span data-ttu-id="46440-110">これを使用するには、ブループリント アクターに AR Trackable Notify コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="46440-110">To use this, add an AR Trackable Notify component to a Blueprint actor:</span></span> 

![QR の AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="46440-112">次に、コンポーネントの詳細にアクセスし、監視するイベントの緑色の [+] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="46440-112">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span>  

![QR のイベント](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="46440-114">ここでは、OnUpdateTrackedImage をサブスクライブして、QR コードの中心にポイントをレンダリングし、QR コードのエンコードされたデータを出力しています。</span><span class="sxs-lookup"><span data-stu-id="46440-114">Here, we have subscribed to OnUpdateTrackedImage to render a point in the center of a QR Code and print the QR code’s encoded data.</span></span> 

![QR のレンダリングの例](images/unreal-qr-render.PNG)

<span data-ttu-id="46440-116">最初に、追跡したイメージを ARTrackedQRCode にキャストして、現在の更新されたイメージが QR コードであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="46440-116">First cast the tracked image to an ARTrackedQRCode to verify that the current updated image is a QR code.</span></span>  <span data-ttu-id="46440-117">これで、QRCode 変数を使用して、エンコードされたデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="46440-117">Then the encoded data can be retrieved with the QRCode variable.</span></span>  <span data-ttu-id="46440-118">QR コードの左上は、GetLocalToWorldTransform の場所から取得できます。</span><span class="sxs-lookup"><span data-stu-id="46440-118">The top-left of the QR code can be retrieved from the location of GetLocalToWorldTransform.</span></span>  <span data-ttu-id="46440-119">次元は GetEstimateSize で取得できます。</span><span class="sxs-lookup"><span data-stu-id="46440-119">The dimensions can be retrieved with GetEstimateSize.</span></span> 

<span data-ttu-id="46440-120">すべての QR コードに独自の GUID があります。</span><span class="sxs-lookup"><span data-stu-id="46440-120">Every QR code also has a unique guid ID:</span></span> 

![QR の GUID](images/unreal-qr-guid.PNG)

## <a name="see-also"></a><span data-ttu-id="46440-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="46440-122">See also</span></span>
* [<span data-ttu-id="46440-123">QR コードの追跡</span><span class="sxs-lookup"><span data-stu-id="46440-123">QR code tracking</span></span>](qr-code-tracking.md)
