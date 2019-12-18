---
title: Holographic リモート処理のバージョン履歴
description: HoloLens 2 での Holographic リモート処理のバージョン履歴。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: f051dbf24cab550470a312933ffb99e1ba595257
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181962"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="090b0-104">Holographic リモート処理のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="090b0-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="090b0-105">このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="090b0-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="090b0-106">バージョン 2.0.18.0 (2019 年12月17日)<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="090b0-106">Version 2.0.18.0 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="090b0-107">HolographicViewConfiguration のサポートを追加しました: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span><span class="sxs-lookup"><span data-stu-id="090b0-107">Added support for HolographicViewConfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span></span>
* <span data-ttu-id="090b0-108">クラッシュの原因となるさまざまなバグが修正されています。</span><span class="sxs-lookup"><span data-stu-id="090b0-108">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="090b0-109">HolographicCamera が受け入れられ、HoloraphicFrame に追加されたカメラとして表示されるために HolographicSpace CameraAdded コールバックが必要なバグを修正しました。</span><span class="sxs-lookup"><span data-stu-id="090b0-109">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <span data-ttu-id="090b0-110">バージョン 2.0.16 (2019 年11月11日)<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="090b0-110">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="090b0-111">QR コードの追跡でデッドロックを修正します。</span><span class="sxs-lookup"><span data-stu-id="090b0-111">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="090b0-112">メインスレッドでの待機をブロックしているため、固定されていない例外を修正しています。</span><span class="sxs-lookup"><span data-stu-id="090b0-112">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <span data-ttu-id="090b0-113">バージョン 2.0.14 (2019 年10月26日)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="090b0-113">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="090b0-114">New PerceptionDevice Api のサポート (Windows 10 11 月2019更新プログラム)。</span><span class="sxs-lookup"><span data-stu-id="090b0-114">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="090b0-115">SpatialGestureRecognizer によって保留中のジェスチャイベントがトリガーされない問題を修正しました。</span><span class="sxs-lookup"><span data-stu-id="090b0-115">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="090b0-116">SpatialSurfaceObserver を使用する場合のスレッド処理の問題を修正します。 SetBoundingVolume。</span><span class="sxs-lookup"><span data-stu-id="090b0-116">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="090b0-117">バージョン 2.0.12 (2019 年10月18日)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="090b0-117">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="090b0-118">NavigationRail (X/Y/Z) を使用するときの SpatialGestureRecognizer のクラッシュを修正します。</span><span class="sxs-lookup"><span data-stu-id="090b0-118">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="090b0-119">バージョン 2.0.10 (2019 年10月10日)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="090b0-119">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="090b0-120">VR コントローラーの [トリガー] ボタンを使用するときのクラッシュを修正します。</span><span class="sxs-lookup"><span data-stu-id="090b0-120">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="090b0-121">Holographic リモート処理はコントローラーを完全にサポートしていません。 HoloLens 2 とペアになっている場合は、[トリガー] ボタンと [Windows] ボタンのみが動作します。</span><span class="sxs-lookup"><span data-stu-id="090b0-121">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="090b0-122">バージョン 2.0.9 (2019 年9月19日)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="090b0-122">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="090b0-123">[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)のサポートを追加しました</span><span class="sxs-lookup"><span data-stu-id="090b0-123">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="090b0-124">次のメンバーを提供する新しいインターフェイス ```IPlayerContext2``` (```PlayerContext```によって実装されます) を追加しました。</span><span class="sxs-lookup"><span data-stu-id="090b0-124">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="090b0-125">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)プロパティ。</span><span class="sxs-lookup"><span data-stu-id="090b0-125">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="090b0-126">```Failed_RemoteFrameTooOld``` 値を ```BlitResult``` に追加しました</span><span class="sxs-lookup"><span data-stu-id="090b0-126">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="090b0-127">安定性と信頼性の向上</span><span class="sxs-lookup"><span data-stu-id="090b0-127">Stability and reliability improvements</span></span>

## <span data-ttu-id="090b0-128">バージョン 2.0.8 (2019 年8月20日)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="090b0-128">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="090b0-129">[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as パラメーターを指定して[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)を呼び出すときのクラッシュを修正します。</span><span class="sxs-lookup"><span data-stu-id="090b0-129">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="090b0-130">安定性と信頼性の向上</span><span class="sxs-lookup"><span data-stu-id="090b0-130">Stability and reliability improvements</span></span>

## <span data-ttu-id="090b0-131">バージョン 2.0.7 (2019 年7月26日)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="090b0-131">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="090b0-132">HoloLens 2 の Holographic リモート処理の最初のパブリックリリース。</span><span class="sxs-lookup"><span data-stu-id="090b0-132">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="090b0-133">参照</span><span class="sxs-lookup"><span data-stu-id="090b0-133">See Also</span></span>
* [<span data-ttu-id="090b0-134">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="090b0-134">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="090b0-135">Holographic Remoting ホストアプリの作成</span><span class="sxs-lookup"><span data-stu-id="090b0-135">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="090b0-136">Holographic リモート処理のトラブルシューティングと制限事項</span><span class="sxs-lookup"><span data-stu-id="090b0-136">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="090b0-137">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="090b0-137">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="090b0-138">Microsoft プライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="090b0-138">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
