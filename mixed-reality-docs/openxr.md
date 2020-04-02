---
title: OpenXR
description: ポータブル OpenXR API 標準を使用してエンジンをビルドし、Windows Mixed Reality と HoloLens 2 ヘッドセットに展開します。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア
ms.openlocfilehash: 04b2404889dc74f191543466beb7ae1e516d0d42
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549374"
---
# <a name="openxr"></a>OpenXR

OpenXR は、 <a href="https://www.khronos.org/" target="_blank">Khronos</a>のオープンなロイヤリティフリー API 標準です。これにより、さまざまなベンダーの幅広いデバイスにエンジンがネイティブでアクセスできるようになり、[混合現実](mixed-reality.md)の範囲を超えています。

デスクトップ上の HoloLens 2 または Windows Mixed Reality の OpenXR を使用して開発することができます。  ヘッドセットへのアクセス権がない場合は、代わりに HoloLens 2 エミュレーターまたは Windows Mixed Reality シミュレーターを使用できます。

## <a name="why-openxr"></a>OpenXR の理由

OpenXR を使用すると、holographic デバイス (HoloLens 2 など) の両方を対象とするエンジンを構築できます。これにより、実際の世界にデジタルコンテンツを配置し、イマーシブデバイス (デスクトップ Pc 用の Windows Mixed Reality ヘッドセットなど) を物理的に隠すことができます。それをデジタル体験に置き換えることができます。  OpenXR を使用すると、さまざまなハードウェアプラットフォームで移植可能なコードを一度記述できます。

OpenXR API は、アプリケーションをヘッドセットのネイティブプラットフォームサポートに直接接続するローダーを使用します。  これにより、エンドユーザーは、Windows Mixed Reality ヘッドセットとその他のヘッドセットのどちらを使用しているかにかかわらず、最大のパフォーマンスと最小待機時間を実現できます。

## <a name="what-is-openxr"></a>OpenXR とは

OpenXR API は、コアの予測、フレームのタイミング、および空間入力の機能を提供します。これは、HoloLens 2 のような holographic デバイスと、Windows Mixed Reality ヘッドセットのようなイマーシブデバイスの両方を対象とするエンジンを構築するために必要です。

OpenXR API の詳細については、OpenXR 1.0<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">仕様</a>、 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API リファレンス</a>、および<a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">クイックリファレンスガイド</a>を参照してください。  詳細については、 <a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR のページ</a>を参照してください。

HoloLens 2 の全機能セットを対象にするには、クロスベンダおよびベンダー固有の OpenXR 拡張機能を使用します。これにより、OpenXR 1.0 コア以外の追加機能が可能になります。これには、トレーラーによる追跡、視線追跡、空間マッピング、空間アンカーなどがあります。  今年の後半に登場する拡張機能の詳細については、後の[「ロードマップ」セクション](#roadmap)を参照してください。

OpenXR は、それ自体が mixed reality エンジンではないことに注意してください。  代わりに、OpenXR では、Unity や Unreal などのエンジンがポータブルコードを一度記述できるようになります。これにより、そのプラットフォームを構築したベンダーに関係なく、ユーザーの holographic またはイマーシブデバイスのネイティブプラットフォーム機能にアクセスできます。

## <a name="roadmap"></a>ロードマップ

OpenXR 仕様では、ランタイム実装者が<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Base OpenXR 1.0 仕様</a>で定義されている[コア機能](#what-is-openxr)以外の機能を公開できるようにする拡張機構を定義しています。

OpenXR 拡張機能には、次の3種類があります。
* **ベンダ拡張機能 (例: `MSFT`):** ハードウェアまたはソフトウェアの機能でベンダーごとのイノベーションを実現します。  任意のランタイムベンダは、いつでもベンダ拡張機能を導入および出荷できます。
  * **試験的なベンダーの拡張機能 (`MSFT_preview`など):** フィードバックを収集するためにプレビューされている試験的なベンダーの拡張機能。  `MSFT_preview` の拡張機能は開発者向けデバイスのみを対象としており、実際の拡張機能が出荷されると削除されます。  試してみるには、[開発者デバイスでプレビュー拡張機能を有効に](openxr-getting-started.md#using-preview-extensions)します。
* **クロスベンダ `EXT` 拡張機能:** 複数の企業が定義および実装するクロスベンダーの拡張機能。  関心のある企業のグループは、いつでも拡張機能を導入できます。
* **公式の `KHR` 拡張機能:** Khronos の公式拡張機能は、コア仕様リリースの一部として批准されています。  KHR 拡張機能は、コア仕様自体と同じライセンスによってカバーされます。

Windows Mixed Reality OpenXR ランタイムは、2020年7月に、一連の `MSFT` と `EXT` の拡張機能をサポートします。これにより、すべての HoloLens 2 の機能がアプリケーションの OpenXR に適用されます。

| Feature area (機能領域) | 拡張機能の可用性 |
|--------------|------------------------|
| システム + セッション | **OpenXR 1.0 コア仕様:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>、 <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>、 <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [参照スペース (view、local、stage)](coordinate-systems.md) | **OpenXR 1.0 コア仕様:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| 構成の表示 (mono、ステレオ) | **OpenXR 1.0 コア仕様:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [フレームのタイミング](understanding-performance-for-mixed-reality.md) + [swapchains](rendering.md) | **OpenXR 1.0 コア仕様:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| コンポジションレイヤー<br />(プロジェクション、クワッド) | **OpenXR 1.0 コア仕様:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Input および haptics](interaction-fundamentals.md) | **OpenXR 1.0 コア仕様:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Direct3D 11 の統合 | **正式な `KHR` 拡張機能がリリースされました:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code><br /> |
| Direct3D 12 の統合 | **正式な `KHR` 拡張機能が定義されています:** *(まだサポートされていません)*<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code><br /><p>**プレビューのサポート**: 2020 年4月 *(計画済)*</p><p>**フルサポート**: 5 月 2020 *(計画済み)*</p> |
| [無制限の参照空間<br />(ワールドスケールエクスペリエンス)](coordinate-systems.md#building-a-world-scale-experience) | **リリースされた `MSFT` 拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [空間アンカー](spatial-anchors.md) | **リリースされた `MSFT` 拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [ハンドインタラクション<br />(グリップ/aim、エアタップ、つかみ)](hands-and-tools.md) | **使用可能な拡張機能 `MSFT_preview`:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_interaction_preview">XR_MSFT_hand_interaction_preview</a></code><p>**`MSFT` リリース**: 2020 年4月 *(計画)*</p> |
| [手 articulation + 手メッシュ](hands-and-tools.md) | **使用可能な拡張機能 `MSFT_preview`:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_preview">XR_MSFT_hand_tracking_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_mesh_preview">XR_MSFT_hand_tracking_mesh_preview</a></code><p>**`MSFT` リリース**: 5 月 2020 *(計画済み)*</p> |
| 他の HoloLens Sdk との相互運用 ( [QR](qr-code-tracking.md)など) | **使用可能な拡張機能 `MSFT_preview`:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_spatial_graph_bridge_preview">XR_MSFT_spatial_graph_bridge_preview</a></code><p>**`MSFT` リリース**: 5 月 2020 *(計画済み)*</p> |
| [目の視線入力](eye-tracking.md) | <p>**定義されている拡張機能`EXT`** : *(まだサポートされていません)*<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code><p>**プレビューのサポート**: 2020 年4月 *(計画済)*</p><p>**フルサポート**: 5 月 2020 *(計画済み)*</p> |
| [Mixed Reality Capture<br />(PV カメラからの3番目のレンダリング)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) | **使用可能な拡張機能 `MSFT_preview`:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_secondary_view_configuration_preview">XR_MSFT_secondary_view_configuration_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_first_person_observer_preview">XR_MSFT_first_person_observer_preview</a></code><br /><p>**`MSFT` リリース**: 6 月 2020 *(計画済み)*</p> |
| [モーションコントローラーレンダリングモデル](motion-controllers.md#rendering-the-motion-controller-model) | <p>**`MSFT_preview`** : 2020 年4月 *(計画済)*</p><p>**`MSFT` リリース**: 2020 年7月 *(計画)*</p> |
| [シーンの理解 (平面、メッシュ)](scene-understanding.md) | <p>**`MSFT_preview`** : 2020 年5月 *(計画)*</p><p>**`MSFT` リリース**: 2020 年7月 *(計画)*</p> |

これらの拡張機能の一部はベンダー固有の `MSFT` 拡張機能として開始される場合がありますが、Microsoft およびその他の OpenXR runtime ベンダーは、これらの機能領域の多くに対して、クロスベンダーの `EXT` または `KHR` 拡張機能を設計するために連携しています。  これにより、コア仕様と同様に、これらの機能用に記述したコードをランタイムベンダー間で移植可能にすることができます。

## <a name="get-started-with-openxr"></a>OpenXR を使ってみる

デスクトップ上の HoloLens 2 または Windows Mixed Reality の OpenXR を使用して開発することができます。  ヘッドセットへのアクセス権がない場合は、代わりに HoloLens 2 エミュレーターまたは Windows Mixed Reality シミュレーターを使用できます。

HoloLens 2 またはイマーシブ Windows Mixed Reality ヘッドセットの OpenXR アプリケーションの開発を開始するには、「 [OpenXR development の使用を開始する方法](openxr-getting-started.md)」を参照してください。

## <a name="see-also"></a>参照

* <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR の詳細情報</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 仕様</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API リファレンス</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 クイックリファレンスガイド</a>
