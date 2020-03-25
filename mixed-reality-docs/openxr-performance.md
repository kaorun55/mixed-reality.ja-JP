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
# <a name="openxr-performance"></a>OpenXR のパフォーマンス

HoloLens 2 では、`xrEndFrame` を使用してコンポジションデータを送信する方法が多数あり、その結果、パフォーマンスが大幅に低下する後処理が発生します。
パフォーマンス penalities を回避するには、次の特性を持つ[1 つの `XrCompositionProjectionLayer`を送信](openxr-best-practices.md#use-a-single-projection-layer)します。
* [テクスチャ配列のスワップチェーンを使用する](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [プライマリ色のスワップチェーン形式を使用する](openxr-best-practices.md#select-a-swapchain-format)
* [推奨ビューディメンションを使用する](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` フラグを設定しない
* `XrCompositionLayerDepthInfoKHR` `minDepth` を 0.0 f に、`maxDepth` を 1.0 f に設定します

その他の考慮事項により、パフォーマンスが向上します。
* [16ビット深度形式を使用する](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [インスタンス化描画呼び出しを作成する](openxr-best-practices.md#render-with-texture-array-and-vprt)
