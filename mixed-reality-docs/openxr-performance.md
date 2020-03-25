---
title: OpenXR のパフォーマンス
description: OpenXR アプリケーションの GPU パフォーマンスをデバッグします。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア、パフォーマンス、最適化、GPU デバッグ、RenderDoc、PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163346"
---
# <a name="openxr-performance"></a><span data-ttu-id="30e6e-104">OpenXR のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="30e6e-104">OpenXR performance</span></span>

<span data-ttu-id="30e6e-105">HoloLens 2 では、`xrEndFrame` を使用してコンポジションデータを送信する方法が多数あり、その結果、パフォーマンスが大幅に低下する後処理が発生します。</span><span class="sxs-lookup"><span data-stu-id="30e6e-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame` which will result in post-processing that will have a noticeable performance penalty.</span></span>
<span data-ttu-id="30e6e-106">パフォーマンス penalities を回避するには、次の特性を持つ[1 つの `XrCompositionProjectionLayer`を送信](openxr-best-practices.md#use-a-single-projection-layer)します。</span><span class="sxs-lookup"><span data-stu-id="30e6e-106">To avoid performance penalities, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="30e6e-107">テクスチャ配列のスワップチェーンを使用する</span><span class="sxs-lookup"><span data-stu-id="30e6e-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="30e6e-108">プライマリ色のスワップチェーン形式を使用する</span><span class="sxs-lookup"><span data-stu-id="30e6e-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="30e6e-109">推奨ビューディメンションを使用する</span><span class="sxs-lookup"><span data-stu-id="30e6e-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="30e6e-110">`XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` フラグを設定しない</span><span class="sxs-lookup"><span data-stu-id="30e6e-110">Do not set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="30e6e-111">`XrCompositionLayerDepthInfoKHR` `minDepth` を 0.0 f に、`maxDepth` を 1.0 f に設定します</span><span class="sxs-lookup"><span data-stu-id="30e6e-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="30e6e-112">その他の考慮事項により、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="30e6e-112">Additional considerations will result in better performance:</span></span>
* [<span data-ttu-id="30e6e-113">16ビット深度形式を使用する</span><span class="sxs-lookup"><span data-stu-id="30e6e-113">Use the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="30e6e-114">インスタンス化描画呼び出しを作成する</span><span class="sxs-lookup"><span data-stu-id="30e6e-114">Make instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
