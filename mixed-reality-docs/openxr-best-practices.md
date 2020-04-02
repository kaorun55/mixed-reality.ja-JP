---
title: OpenXR のベストプラクティス
description: OpenXR アプリケーションのビジュアル品質、安定性、およびパフォーマンスに関するベストプラクティスについて説明します。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア、ベストプラクティス、パフォーマンス、品質、安定性
ms.openlocfilehash: 0a0bbd37521be52ec328b4f32e53969c0ec7fef4
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549365"
---
# <a name="openxr-app-best-practices"></a>OpenXR アプリのベストプラクティス

以下のベストプラクティスの例については、 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>の OpenXRProgram ファイルを参照してください。 最初の Run () 関数は、初期化からイベントおよびレンダリングループへの一般的な OpenXR app コードフローをキャプチャします。

## <a name="best-practices-for-visual-quality-and-stability"></a>ビジュアルの品質と安定性に関するベストプラクティス

このセクションのベストプラクティスでは、OpenXR アプリケーションで最高の画質と安定性を実現する方法について説明します。

HoloLens 2 に固有のパフォーマンスの推奨事項については、後述の「 [hololens 2 のパフォーマンスに関するベストプラクティス](#best-practices-for-performance-on-hololens-2)」を参照してください。

### <a name="gamma-correct-rendering"></a>ガンマ-正しいレンダリング

レンダリングパイプラインのガンマが正しいことを確認する必要があります。 スワップチェーンにレンダリングする場合、レンダーターゲットビュー形式は、スワップチェーン形式 (スワップチェーン形式とレンダーターゲットビューの両方の `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` など) と一致する必要があります。
例外は、アプリのレンダリングパイプラインがシェーダーコード内で手動で srgb 変換を行う場合です。この場合、アプリは srgb スワップチェーン形式を要求しますが、レンダリングターゲットビューには線形形式を使用します (たとえば、要求 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` をスワップチェーン形式として使用し、`DXGI_FORMAT_B8G8R8A8_UNORM` をレンダーターゲットビューとして使用します)。

### <a name="submit-depth-buffer-for-projection-layers"></a>プロジェクションレイヤーの深度バッファーを送信します

`xrEndFrame`にフレームを送信する場合は、常に `XR_KHR_composition_layer_depth` 拡張機能を使用し、深度バッファーを投影レイヤーと一緒に送信します。
これにより、HoloLens 2 でハードウェアの深さの再投影を有効にすることで、ホログラムの安定性が向上します。

### <a name="choose-a-reasonable-depth-range"></a>適切な深さの範囲を選択してください

HoloLens でのホログラムの安定性を向上させるために、より狭い深さの範囲を使用して仮想コンテンツの範囲を絞り込みます。
たとえば、OpenXrProgram サンプルでは、0.1 ~ 20 メートルが使用されています。
より一貫した深さの解決には、[逆順-Z](https://developer.nvidia.com/content/depth-precision-visualized)を使用します。
HoloLens 2 では、推奨される `DXGI_FORMAT_D16_UNORM` 深度形式を使用すると、フレームレートとパフォーマンスが向上します。ただし、16ビット深度バッファーでは、24ビット深度バッファーよりも深さの解像度が低くなります。
そのため、これらのベストプラクティスに従って、その深さの解決を最大限に活用することが重要になります。

### <a name="prepare-for-different-environment-blend-modes"></a>さまざまな環境の blend モードを準備する

また、世界を完全にブロックするイマーシブヘッドセットでアプリケーションを実行する場合は、`xrEnumerateEnvironmentBlendModes` API を使用してサポートされている環境の blend モードを列挙し、それに応じてレンダリングコンテンツを準備してください。
たとえば、HoloLens などの `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` を搭載したシステムの場合、アプリでは透明色として透明を使用する必要があります。一方、`XR_ENVIRONMENT_BLEND_MODE_OPAQUE`のシステムの場合、アプリは不透明色または一部の仮想ルームをバックグラウンドでレンダリングする必要があります。

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>アプリケーションのルート領域として非バインド参照スペースを選択する

通常、アプリケーションは、ビュー、アクション、およびホログラムを連結するために、いくつかのルートワールド座標空間を確立します。
拡張機能を使用して[世界規模の座標系](coordinate-systems.md#building-a-world-scale-experience)を確立することがサポートされている場合は `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` を使用します。これにより、アプリの開始位置からユーザーが遠く (たとえば、5メートル離れた場所) に移動したときに望ましくないホログラムのずれが発生するのを防ぐことができます。
非バインド領域の拡張機能が存在しない場合は、フォールバックとして `XR_REFERENCE_SPACE_TYPE_LOCAL` を使用します。

### <a name="associate-hologram-with-spatial-anchor"></a>ホログラムを空間アンカーに関連付ける

バインドされていない参照空間を使用する場合、その参照空間に直接配置したホログラムは、遠くの部屋に移動した後に戻ったときに、[ずれを生じる可能性があり](coordinate-systems.md#building-a-world-scale-experience)ます。
ホログラムユーザーが世界中の個別の場所に配置されるようにするには、`xrCreateSpatialAnchorSpaceMSFT` 拡張機能を使用して[空間アンカーを作成](spatial-anchors.md#best-practices)し、その原点にホログラムを配置します。
これにより、そのホログラムは時間の経過と共に個別に安定した状態に保たれます

### <a name="support-mixed-reality-capture"></a>混合現実のキャプチャをサポートする

HoloLens 2 のプライマリディスプレイは加法の環境ブレンドを使用しますが、ユーザーが[mixed reality キャプチャ](mixed-reality-capture-for-developers.md)を開始すると、アプリのレンダリングコンテンツは環境のビデオストリームとアルファブレンドされます。
Mixed reality のキャプチャビデオで最高の画質を実現するには、投影レイヤーの `layerFlags`に `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` を設定することをお勧めします。

## <a name="best-practices-for-performance-on-hololens-2"></a>HoloLens 2 でのパフォーマンスに関するベストプラクティス

ハードウェアの再プロジェクションをサポートするモバイルデバイスとして、HoloLens 2 には最適なパフォーマンスを得るための厳しい要件があります。  `xrEndFrame` を使用してコンポジションデータを送信する方法は多数あります。その結果、パフォーマンスが大幅に低下する後処理が発生します。

### <a name="select-a-swapchain-format"></a>スワップチェーン形式を選択してください

常に `xrEnumerateSwapchainFormats`を使用してサポートされているピクセル形式を列挙し、アプリがサポートするランタイムから最初の色と深度のピクセル形式を選択します。これは、最適なパフォーマンスのためにランタイムが推奨するものであるためです。 HoloLens 2 では、通常、レンダリングのパフォーマンスを向上させるために、`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` と `DXGI_FORMAT_D16_UNORM` が最初に選択されます。 この設定は、デスクトップ PC で実行されている VR ヘッドセットでは異なっていてもかまいません。24ビットの深度バッファーでは、パフォーマンスへの影響が少なくなります。
  
**パフォーマンスの警告:** プライマリスワップチェーンカラー形式以外の形式を使用すると、パフォーマンスが大幅に低下するランタイム後処理が発生します。

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>推奨されるレンダリングパラメーターとフレームタイミングを使用したレンダリング

常に、推奨されるビュー構成の幅/高さ (`recommendedImageRectWidth` と `recommendedImageRectHeight` `XrViewConfigurationView`) でレンダリングします。また、表示する前に、常に `xrLocateViews` API を使用して、推奨されるビューの設定、視界、およびその他のレンダリングパラメーターのクエリを実行します。
ポーズとビューに対してクエリを実行する場合は、常に最新の `xrWaitFrame` 呼び出しの `XrFrameEndInfo.predictedDisplayTime` を使用します。
これにより、HoloLens は、HoloLens を装着しているユーザーに対してレンダリングを調整し、視覚品質を最適化することができます。

### <a name="use-a-single-projection-layer"></a>1つの投影レイヤーを使用する

HoloLens 2 では、アプリケーションがコンテンツをレンダリングするための GPU 機能が制限されており、単一の投影レイヤー用に最適化されたハードウェアコンポジターが使用されています。
常に1つの投影レイヤーを使用すると、アプリケーションのフレームレート、ホログラムの安定性、およびビジュアルの品質を向上させることができます。  
  
**パフォーマンスの警告:** 1つの保護レイヤーだけを送信すると、パフォーマンスが大幅に低下するランタイム後処理が発生します。

### <a name="render-with-texture-array-and-vprt"></a>テクスチャ配列と VPRT を使用したレンダリング

`arraySize=2` を使用して、色スワップチェーンに対して1つの `xrSwapchain` を作成し、1つを深さに対して作成します。
スライス0に左側を表示し、スライス1に目を入れます。
VPRT のシェーダーとインスタンス化された描画呼び出しのステレオスコピックレンダリングを使用して、GPU の負荷を最小限に抑えます。
これにより、ランタイムの最適化によって HoloLens 2 で最高のパフォーマンスを実現できます。
2つのテクスチャ配列を使用する代わりに、2倍のレンダリングや個別のスワップチェーンなどを使用する代わりに、パフォーマンスが大幅に低下するランタイム後処理が発生します。

### <a name="avoid-quad-layers"></a>クワッドレイヤーを避ける

`XrCompositionLayerQuad`を使用して構成レイヤーとしてクワッドレイヤーを送信するのではなく、クワッドコンテンツを射影 swapchain に直接レンダリングします。

**パフォーマンスの警告:** クワッドレイヤーなど、1つの投影レイヤーを超えて追加のレイヤーを提供すると、パフォーマンスが大幅に低下するランタイム後処理が発生します。