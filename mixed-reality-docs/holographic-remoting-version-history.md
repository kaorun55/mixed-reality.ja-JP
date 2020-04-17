---
title: Holographic リモート処理のバージョン履歴
description: HoloLens 2 での Holographic リモート処理のバージョン履歴。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: cd6d076c00fd21ca6fa60cafb94eb9d89796825a
ms.sourcegitcommit: 48456c607a2d0dcf035a77e8ba67615396b0a211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484302"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="ea049-104">Holographic リモート処理のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="ea049-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea049-105">このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="ea049-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="version-212-april-5-2020"></a><span data-ttu-id="ea049-106">バージョン 2.1.2 (2020 年4月5日)<a name="v2.1.2"></a></span><span class="sxs-lookup"><span data-stu-id="ea049-106">Version 2.1.2 (April 5, 2020) <a name="v2.1.2"></a></span></span>
* <span data-ttu-id="ea049-107">最新の Holographic リモート処理プレーヤーと2.1.0 より小さいバージョンを使用したリモートアプリとの間で、オーディオの下位互換性の問題を修正した。</span><span class="sxs-lookup"><span data-stu-id="ea049-107">Fixed audio backwards compatibility issue between latest Holographic Remoting player and remote apps using version smaller than 2.1.0.</span></span>
* <span data-ttu-id="ea049-108">Holographic リモート処理プレーヤーを予期せず閉じた空間アンカーの問題を修正しました。</span><span class="sxs-lookup"><span data-stu-id="ea049-108">Fixed spatial anchor issue which unexpectedly closed the Holographic Remoting player.</span></span> <span data-ttu-id="ea049-109">この問題は、カスタムプレーヤーにも影響します。</span><span class="sxs-lookup"><span data-stu-id="ea049-109">This issue also affects custom players.</span></span>

## <a name="version-211-march-20-2020"></a><span data-ttu-id="ea049-110">バージョン 2.1.1 (2020 年3月20日)<a name="v2.1.1"></a></span><span class="sxs-lookup"><span data-stu-id="ea049-110">Version 2.1.1 (March 20, 2020) <a name="v2.1.1"></a></span></span>
* <span data-ttu-id="ea049-111">AMD Gpu を使用する場合のリモートアプリのビデオエンコードに関する問題を修正します。</span><span class="sxs-lookup"><span data-stu-id="ea049-111">Fixed video encoding issue with remote apps when using AMD GPUs.</span></span>
* <span data-ttu-id="ea049-112">Holographic リモート処理プレーヤーのパフォーマンスが向上しました。</span><span class="sxs-lookup"><span data-stu-id="ea049-112">Holographic Remoting Player performance improvements.</span></span>

## <a name="version-210-march-11-2020"></a><span data-ttu-id="ea049-113">バージョン 2.1.0 (2020 年3月11日)<a name="v2.1.0"></a></span><span class="sxs-lookup"><span data-stu-id="ea049-113">Version 2.1.0 (March 11, 2020) <a name="v2.1.0"></a></span></span>
* <span data-ttu-id="ea049-114">UDP 経由で[RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol)を使用するようにネットワークトランスポートを切り替えました。</span><span class="sxs-lookup"><span data-stu-id="ea049-114">Switched network transport to use [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP.</span></span> <span data-ttu-id="ea049-115">セキュリティで保護された接続では、 [Srtp](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol)を使用します。</span><span class="sxs-lookup"><span data-stu-id="ea049-115">Secure connections use [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) now.</span></span> <span data-ttu-id="ea049-116">[Holographic リモート処理プレーヤー](holographic-remoting-player.md)は、以前にリリースされたすべての Holographic リモート処理バージョンと互換性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ea049-116">Note, the [Holographic Remoting Player](holographic-remoting-player.md) is still compatible with all previously release Holographic Remoting versions.</span></span> <span data-ttu-id="ea049-117">新しいネットワークトランスポートの利点を活用するには、Holographic リモート処理プレーヤーと、問題のリモートアプリの両方でバージョン2.1.0 を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea049-117">To benefit from the new network transport both, the Holographic Remoting Player and the remote app in question, have to use version 2.1.0.</span></span>
* <span data-ttu-id="ea049-118">[CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)のサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="ea049-118">Added support for [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span> 

## <a name="version-2020-february-2-2020"></a><span data-ttu-id="ea049-119">バージョン2.0.20 以降 (2020 年2月2日)<a name="v2.0.20"></a></span><span class="sxs-lookup"><span data-stu-id="ea049-119">Version 2.0.20 (February 2, 2020) <a name="v2.0.20"></a></span></span>
* <span data-ttu-id="ea049-120">クラッシュの原因となるさまざまなバグが修正されています。</span><span class="sxs-lookup"><span data-stu-id="ea049-120">Fixed various bugs that lead to crashes.</span></span>

## <a name="version-2018-december-17-2019"></a><span data-ttu-id="ea049-121">バージョン 2.0.18 (2019 年12月17日)<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="ea049-121">Version 2.0.18 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="ea049-122">[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)のサポートを追加しました</span><span class="sxs-lookup"><span data-stu-id="ea049-122">Added support for [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)</span></span>
* <span data-ttu-id="ea049-123">クラッシュの原因となるさまざまなバグが修正されています。</span><span class="sxs-lookup"><span data-stu-id="ea049-123">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="ea049-124">HolographicCamera が受け入れられ、HolographicFrame に追加されたカメラとして表示されるために HolographicSpace CameraAdded コールバックが必要なバグを修正しました。</span><span class="sxs-lookup"><span data-stu-id="ea049-124">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HolographicFrame.</span></span>

## <a name="version-2016-november-11-2019"></a><span data-ttu-id="ea049-125">バージョン 2.0.16 (2019 年11月11日)<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="ea049-125">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="ea049-126">QR コードの追跡でデッドロックを修正します。</span><span class="sxs-lookup"><span data-stu-id="ea049-126">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="ea049-127">メインスレッドでの待機をブロックしているため、固定されていない例外を修正しています。</span><span class="sxs-lookup"><span data-stu-id="ea049-127">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <a name="version-2014-october-26-2019"></a><span data-ttu-id="ea049-128">バージョン 2.0.14 (2019 年10月26日)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="ea049-128">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="ea049-129">New PerceptionDevice Api のサポート (Windows 10 11 月2019更新プログラム)。</span><span class="sxs-lookup"><span data-stu-id="ea049-129">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="ea049-130">SpatialGestureRecognizer によって保留中のジェスチャイベントがトリガーされない問題を修正しました。</span><span class="sxs-lookup"><span data-stu-id="ea049-130">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="ea049-131">SpatialSurfaceObserver を使用する場合のスレッド処理の問題を修正します。 SetBoundingVolume。</span><span class="sxs-lookup"><span data-stu-id="ea049-131">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <a name="version-2012-october-18-2019"></a><span data-ttu-id="ea049-132">バージョン 2.0.12 (2019 年10月18日)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="ea049-132">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="ea049-133">NavigationRail (X/Y/Z) を使用するときの SpatialGestureRecognizer のクラッシュを修正します。</span><span class="sxs-lookup"><span data-stu-id="ea049-133">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <a name="version-2010-october-10-2019"></a><span data-ttu-id="ea049-134">バージョン 2.0.10 (2019 年10月10日)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="ea049-134">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="ea049-135">VR コントローラーの [トリガー] ボタンを使用するときのクラッシュを修正します。</span><span class="sxs-lookup"><span data-stu-id="ea049-135">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="ea049-136">Holographic リモート処理はコントローラーを完全にサポートしていません。 HoloLens 2 とペアになっている場合は、[トリガー] ボタンと [Windows] ボタンのみが動作します。</span><span class="sxs-lookup"><span data-stu-id="ea049-136">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <a name="version-209-september-19-2019"></a><span data-ttu-id="ea049-137">バージョン 2.0.9 (2019 年9月19日)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="ea049-137">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="ea049-138">[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)のサポートを追加しました</span><span class="sxs-lookup"><span data-stu-id="ea049-138">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="ea049-139">次のメンバーを提供する新しいインターフェイス ```IPlayerContext2``` (```PlayerContext```によって実装されます) を追加しました。</span><span class="sxs-lookup"><span data-stu-id="ea049-139">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="ea049-140">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)プロパティ。</span><span class="sxs-lookup"><span data-stu-id="ea049-140">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="ea049-141">```Failed_RemoteFrameTooOld``` 値を ```BlitResult``` に追加しました</span><span class="sxs-lookup"><span data-stu-id="ea049-141">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="ea049-142">安定性と信頼性の向上</span><span class="sxs-lookup"><span data-stu-id="ea049-142">Stability and reliability improvements</span></span>

## <a name="version-208-august-20-2019"></a><span data-ttu-id="ea049-143">バージョン 2.0.8 (2019 年8月20日)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="ea049-143">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="ea049-144">[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as パラメーターを指定して[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)を呼び出すときのクラッシュを修正します。</span><span class="sxs-lookup"><span data-stu-id="ea049-144">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="ea049-145">安定性と信頼性の向上</span><span class="sxs-lookup"><span data-stu-id="ea049-145">Stability and reliability improvements</span></span>

## <a name="version-207-july-26-2019"></a><span data-ttu-id="ea049-146">バージョン 2.0.7 (2019 年7月26日)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="ea049-146">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="ea049-147">HoloLens 2 の Holographic リモート処理の最初のパブリックリリース。</span><span class="sxs-lookup"><span data-stu-id="ea049-147">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea049-148">参照</span><span class="sxs-lookup"><span data-stu-id="ea049-148">See Also</span></span>
* [<span data-ttu-id="ea049-149">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="ea049-149">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="ea049-150">Holographic Remoting ホストアプリの作成</span><span class="sxs-lookup"><span data-stu-id="ea049-150">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="ea049-151">Holographic リモート処理のトラブルシューティングと制限事項</span><span class="sxs-lookup"><span data-stu-id="ea049-151">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="ea049-152">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="ea049-152">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="ea049-153">Microsoft のプライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="ea049-153">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
