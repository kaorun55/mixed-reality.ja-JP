---
title: OpenXR
description: ポータブル OpenXR API 標準を使用してエンジンをビルドし、Windows Mixed Reality と HoloLens 2 ヘッドセットに展開します。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、Mixed Reality OpenXR 開発者ポータル、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア
ms.openlocfilehash: aa91918e20b4276b7453bae1a05ad18df9d8ab0e
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491138"
---
# <a name="openxr"></a>OpenXR

OpenXR は、 <a href="https://www.khronos.org/" target="_blank">Khronos</a>のオープンなロイヤリティフリー API 標準です。これにより、さまざまなベンダーの幅広いデバイスにエンジンがネイティブでアクセスできるようになり、[混合現実](mixed-reality.md)の範囲を超えています。

デスクトップ上の HoloLens 2 または Windows Mixed Reality の OpenXR を使用して開発することができます。  ヘッドセットへのアクセス権がない場合は、代わりに HoloLens 2 エミュレーターまたは Windows Mixed Reality シミュレーターを使用できます。

## <a name="why-openxr"></a>OpenXR の理由

OpenXR を使用すると、holographic デバイス (HoloLens 2 など) の両方を対象とするエンジンを構築できます。これにより、実際の世界にデジタルコンテンツを配置し、イマーシブデバイス (デスクトップ Pc 用の Windows Mixed Reality ヘッドセットなど) を物理的に隠すことができます。それをデジタル体験に置き換えることができます。  OpenXR を使用すると、さまざまなハードウェアプラットフォームで移植可能なコードを一度記述できます。

OpenXR API は、アプリケーションをヘッドセットのネイティブプラットフォームサポートに直接接続するローダーを使用します。  これにより、エンドユーザーは、Windows Mixed Reality ヘッドセットとその他のヘッドセットのどちらを使用しているかにかかわらず、最大のパフォーマンスと最小待機時間を実現できます。

## <a name="what-is-openxr"></a>OpenXR とは

Core OpenXR 1.0 API は、HoloLens 2、Windows Mixed Reality ヘッドセットなどのイマーシブデバイスの両方を対象とするエンジンを構築するために必要な基本機能を提供します。
* システム + セッション
* 参照スペース (view、local、stage)
* 構成の表示 (mono、ステレオ)
* スワップチェーン + フレームのタイミング
* コンポジションレイヤー
* Input および haptics
* グラフィックス API + プラットフォーム統合

OpenXR API の詳細については、OpenXR 1.0<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">仕様</a>、 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API リファレンス</a>、および<a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">クイックリファレンスガイド</a>を参照してください。  詳細については、 <a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR のページ</a>を参照してください。

HoloLens 2 の全機能セットを対象にするには、クロスベンダおよびベンダー固有の OpenXR 拡張機能を使用します。これにより、OpenXR 1.0 コア以外の追加機能が可能になります。これには、トレーラーによる追跡、視線追跡、空間マッピング、空間アンカーなどがあります。  今年後半に登場する拡張機能の詳細については、後の「[ロードマップ」セクション](openxr.md#roadmap)を参照してください。

OpenXR は、それ自体が mixed reality エンジンではないことに注意してください。  代わりに、OpenXR では、Unity や Unreal などのエンジンがポータブルコードを一度記述できるようになります。これにより、そのプラットフォームを構築したベンダーに関係なく、ユーザーの holographic またはイマーシブデバイスのネイティブプラットフォーム機能にアクセスできます。

## <a name="getting-started-with-openxr-for-hololens-2"></a>OpenXR for HoloLens 2 の概要

HoloLens 2 用の OpenXR アプリケーションの開発を開始するには:

1. HoloLens 2 をセットアップするか、「 [hololens 2 エミュレーターをインストール](using-the-hololens-emulator.md)するには」の手順に従います。
1. デバイスまたはエミュレーター内からストアアプリを起動し、すべてのアプリが更新されていることを確認します。  これにより、HoloLens の OpenXR ランタイムが OpenXR 1.0 に更新されます。  エミュレーターを使用する場合は、エミュレーターでのストアアプリの使用に役立つ[エミュレーターの入力手順](using-the-hololens-emulator.md#basic-emulator-input)を参照することをお勧めします。

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>OpenXR for Windows Mixed Reality ヘッドセットの概要

イマーシブ Windows Mixed Reality ヘッドセット用の OpenXR アプリケーションの開発を開始するには:

1. Windows 10 2019 更新プログラム (1903) を実行していることを確認してください。これは、Windows Mixed Reality エンドユーザーが OpenXR アプリケーションを実行するための最小要件です。  以前のバージョンの Windows 10 を使用している場合は、 <a href="https://www.microsoft.com//software-download/windows10" target="_blank">windows 10 Update Assistant</a>を使用して、2019年5月の更新プログラムにアップグレードできます。  PC を更新できない場合は、 [2018 年10月の更新プログラム (1809) を使用して OpenXR アプリを開発](openxr.md#developing-on-windows-10-october-2018-update)することもできますが、パフォーマンスが低下したり、その他の問題が発生する可能性があります。
2. Windows Mixed reality ヘッドセットを設定するか、指示に従って[Windows Mixed reality シミュレーターを有効](using-the-windows-mixed-reality-simulator.md)にします。  Windows Mixed reality を設定した後、Mixed Reality ポータルによって、Windows Mixed Reality OpenXR ランタイムが自動的にインストールされます。  その後、Microsoft Store によってランタイムが最新の状態に保たれます。
3. [スタート] メニューから Mixed Reality ポータルを起動し、[...] をクリックして、Windows Mixed Reality OpenXR ランタイムをアクティブにします。メニューをクリックし、[Set up OpenXR] を選択します。<br>
Mixed Reality ポータルで OpenXR を設定する ![](images/mixed-reality-portal-set-up-openxr.png)

Windows Mixed Reality OpenXR Runtime を再びアクティブにする必要がある場合は、手順 3. を繰り返します。

> [!NOTE]
> Windows mixed Reality OpenXR ランタイムは、Windows Mixed Reality のすべてのエンドユーザーに対して、間もなく自動的にセットアップされます。

## <a name="getting-the-mixed-reality-openxr-developer-portal"></a>Mixed Reality OpenXR 開発者ポータルを入手する

Windows Mixed Reality OpenXR ランタイムを試すには、 <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">[Mixed Reality OpenXR Developer ポータルアプリ</a>をインストールします。  このアプリは、OpenXR のさまざまな機能を、アクティブなランタイムと現在のヘッドセットに関する重要な情報を提供するシステムステータスページと共に実行するデモシーンを提供します。

![Mixed Reality OpenXR 開発者ポータルアプリ](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>サンプル OpenXR アプリのビルド

<a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>プロジェクトでは、2つの Visual Studio プロジェクトファイルを含む単純な OpenXR サンプルを示しています。1つは Win32 デスクトップアプリ用で、もう1つは UWP HoloLens 2 アプリ用です。  ソリューションには HoloLens UWP プロジェクトが含まれているため、Visual Studio にインストールされた[ユニバーサル Windows プラットフォームの開発ワークロード](install-the-tools.md#installation-checklist)を完全に開く必要があります。

Win32 と UWP のプロジェクトファイルは、パッケージ化と配置の違いによって分離されていますが、各プロジェクト内のアプリコード100は同じであることに注意してください。

OpenXR Win32 デスクトップを構築した後。EXE を使用して、OpenXR をサポートする任意の desktop VR プラットフォームの VR ヘッドセットと共に使用できます。これは、Windows Mixed Reality ヘッドセットであるか、他のヘッドセットであるかどうかによって異なります。

OpenXR UWP アプリケーションパッケージをビルドした後、[そのパッケージ](using-visual-studio.md)を hololens 2 デバイスまたは Hololens 2 エミュレーターにデプロイできます。

## <a name="openxr-app-best-practices-for-hololens-2"></a>HoloLens 2 の OpenXR app のベストプラクティス

以下のベストプラクティスの例については、BasicXrApp の[OpenXRProgram](https://github.com/microsoft/OpenXR-SDK-VisualStudio/blob/master/samples/BasicXrApp/OpenXrProgram.cpp)ファイルを参照してください。 最初の Run () 関数は、初期化からイベントおよびレンダリングループへの一般的な OpenXR app コードフローをキャプチャします。

### <a name="select-a-pixel-format"></a>ピクセル形式を選択してください

常に `xrEnumerateSwapchainFormats`を使用してサポートされているピクセル形式を列挙し、アプリがサポートするランタイムから最初の色と深度のピクセル形式を選択します。これは、ランタイムが推奨するものであるためです。 HoloLens 2 では、通常、レンダリングのパフォーマンスを向上させるために、`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` と `DXGI_FORMAT_D16_UNORM` が最初に選択されます。 この設定は、デスクトップ PC で実行されている VR ヘッドセットでは異なる場合があります。  
  
**パフォーマンスの警告:** プライマリスワップチェーンカラー形式以外の形式を使用すると、パフォーマンスが大幅に低下するランタイム後処理が発生します。

### <a name="gamma-correct-rendering"></a>ガンマ-正しいレンダリング

これはすべての OpenXR ランタイムに適用されますが、レンダリングパイプラインがガンマで正しいことを確認するために注意する必要があります。 スワップチェーンにレンダリングする場合、レンダーターゲットビュー形式は、スワップチェーン形式 (スワップチェーン形式とレンダーターゲットビューの両方の DXGI_FORMAT_B8G8R8A8_UNORM_SRGB など) と一致する必要があります。
例外は、アプリのレンダリングパイプラインがシェーダーコードで手動の sRGB 変換を行う場合です。この場合、アプリでは、sRGB スワップチェーン形式を要求しますが、レンダリングターゲットビューには線形形式を使用します (たとえば、要求 DXGI_FORMAT_B8G8R8A8_UNORM_SRGB をコンテンツがダブルガンマ補正されないようにするために、DXGI_FORMAT_B8G8R8A8_UNORM をレンダーターゲットビューとして使用します)。

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

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>推奨されるレンダリングパラメーターとフレームタイミングを使用したレンダリング

常に、推奨されるビュー構成の幅/高さ (`recommendedImageRectWidth` と `recommendedImageRectHeight` `XrViewConfigurationView`) でレンダリングします。また、表示する前に、常に `xrLocateViews` API を使用して、推奨されるビューの設定、視界、およびその他のレンダリングパラメーターのクエリを実行します。
ポーズとビューに対してクエリを実行する場合は、常に最新の `xrWaitFrame` 呼び出しの `XrFrameEndInfo.predictedDisplayTime` を使用します。
これにより、HoloLens は、HoloLens を装着しているユーザーに対してレンダリングを調整し、視覚品質を最適化することができます。

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

**パフォーマンスの警告:** 1つの投影レイヤーで `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` フラグを省略すると、パフォーマンスが大幅に低下するランタイム後処理が発生します。

### <a name="avoid-quad-layers"></a>クワッドレイヤーを避ける

`XrCompositionLayerQuad`を使用して構成レイヤーとしてクワッドレイヤーを送信するのではなく、クワッドコンテンツを射影 swapchain に直接レンダリングします。

**パフォーマンスの警告:** クワッドレイヤーなど、1つの投影レイヤーを超えて追加のレイヤーを提供すると、パフォーマンスが大幅に低下するランタイム後処理が発生します。

## <a name="openxr-app-performance-on-hololens-2"></a>HoloLens 2 での OpenXR アプリのパフォーマンス

HoloLens 2 では、`xrEndFrame` を使用してコンポジションデータを送信する方法が多数あり、その結果、パフォーマンスが大幅に低下する後処理が発生します。
パフォーマンス penalities を回避するには、次の特性を持つ[1 つの `XrCompositionProjectionLayer`を送信](#use-a-single-projection-layer)します。
* [テクスチャ配列のスワップチェーンを使用する](#render-with-texture-array-and-vprt)
* [プライマリ色のスワップチェーン形式を使用する](#select-a-pixel-format)
* [テクスチャソース-アルファブレンドフラグを設定する](#support-mixed-reality-capture)
* [推奨ビューディメンションを使用する](#render-with-recommended-rendering-parameters-and-frame-timing)
* `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` フラグを設定しない
* `XrCompositionLayerDepthInfoKHR` `minDepth` を 0.0 f に、`maxDepth` を 1.0 f に設定します

その他の考慮事項により、パフォーマンスが向上します。
* [16ビット深度形式を使用する](#choose-a-reasonable-depth-range)
* [インスタンス化描画呼び出しを作成する](#render-with-texture-array-and-vprt)

## <a name="roadmap"></a>ロードマップ

OpenXR 仕様では、ランタイム実装者が<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Base OpenXR 1.0 仕様</a>で定義されている[コア機能](openxr.md#what-is-openxr)以外の機能を公開できるようにする拡張機構を定義しています。

OpenXR 拡張機能には、次の3種類があります。
* **ベンダ拡張機能 (例: MSFT):** ハードウェアまたはソフトウェアの機能でベンダーごとのイノベーションを実現します。  任意のランタイムベンダは、いつでもベンダ拡張機能を導入および出荷できます。
* **拡張機能:** 複数の企業が定義および実装するクロスベンダーの拡張機能。  関心のある企業のグループは、いつでも拡張機能を導入できます。
* **Khr 拡張機能:** Khronos の公式拡張機能は、コア仕様リリースの一部として批准されています。  KHR 拡張機能は、コア仕様自体と同じライセンスによってカバーされます。

Windows Mixed Reality OpenXR Runtime は、年の終わりまでに、HoloLens 2 の機能の完全なセットを OpenXR アプリケーションに取り込む、MSFT と EXT の一連の拡張機能をサポートします。
* [無制限の参照スペース (ワールドスケールエクスペリエンス)](coordinate-systems.md#building-a-world-scale-experience)
* [空間アンカー + ストレージ](spatial-anchors.md)
* [手 articulation + 手メッシュ](hands-and-tools.md)
* [目の視線入力](eye-tracking.md)
* [セカンダリビューの構成 (Mixed Reality キャプチャ)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [シーンの理解](scene-understanding.md)
* Windows SDK Api との相互運用

これらの拡張機能の一部は、ベンダー固有の MSFT 拡張機能として開始される場合がありますが、Microsoft およびその他の OpenXR runtime ベンダーが連携して、これらの機能領域の多くについて、クロスベンダーの EXT または KHR 拡張機能を設計します。  これにより、コア仕様と同様に、これらの機能用に記述したコードをランタイムベンダー間で移植可能にすることができます。

## <a name="troubleshooting"></a>トラブルシューティング

Windows Mixed Reality OpenXR Runtime のトラブルシューティングのヒントを次に示します。  <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 の仕様</a>に関して他に質問がある場合は、 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR フォーラム</a>または<a href="https://khr.io/slack" target="_blank">余裕期間 #openxr チャネル</a>にアクセスしてください。

### <a name="developing-on-windows-10-october-2018-update"></a>Windows 10 10 月2018更新プログラムの開発

開発用 PC を2019年5月[の更新プログラムにアップグレード](https://www.microsoft.com//software-download/windows10)できない場合は、もう1つの手順に従って、Windows 10 10 月2018更新プログラム (1809) PC を開発用にセットアップできます。

1. 上記の手順に従って、デスクトップ PC で OpenXR を開始します。
1. Windows Mixed Reality OpenXR Runtime をシステムのアクティブな OpenXR ランタイムとして設定するには、 [Windows Mixed Reality OpenXR Developer Compatibility Pack](https://aka.ms/openxr-compat)をインストールします。

> [!NOTE]
> OpenXR アプリケーションを開発するときに Windows 10 10 月2018更新プログラム (1809) を使用できますが、windows 10 月2019更新プログラム (1903) は、エンドユーザーが Windows Mixed Reality で OpenXR を使用するための最小要件となります。  2018年10月の更新で OpenXR アプリを実行すると、パフォーマンスやその他の問題が発生する可能性があります。  開発用 PC を Windows 10 5 月2019更新プログラム (1903) にアップグレードすることを強くお勧めします。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR app が Windows Mixed Reality を開始しない

実行時に OpenXR アプリが Windows Mixed Reality を起動していない場合は、Windows Mixed Reality OpenXR ランタイムがアクティブなランタイムとして設定されていない可能性があります。  前の手順に従って、 [Windows Mixed Reality ヘッドセットの OpenXR を使用](#getting-started-with-openxr-for-windows-mixed-reality-headsets)してランタイムをアクティブにしてください。

また、 [Mixed Reality OpenXR 開発者ポータル](#getting-the-mixed-reality-openxr-developer-portal)を実行して、システム上の Windows Mixed Reality OpenXR ランタイムの状態に関する追加のトラブルシューティングを行うこともできます。

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>Mixed Reality ポータルに [OpenXR の設定] メニュー項目が表示されない

少なくとも Windows 10 10 月2018更新プログラム (1809) を実行していることを確認してください。  以前のバージョンの Windows 10 を使用している場合は、 [windows 10 Update Assistant](https://www.microsoft.com//software-download/windows10)を使用して、2019年5月の更新プログラム (1903) にアップグレードすることができます。

以前のバージョンの Mixed Reality ポータルアプリを使用している場合は、[OpenXR の設定] メニュー項目を使用できないことがあります。  [Mixed Reality ポータルアプリの更新プログラム](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m)を確認して、最新バージョンがあることを確認します。

Windows Mixed Reality OpenXR Runtime が既にインストールされ、アクティブになっている場合は、[OpenXR の設定] メニュー項目が表示されないことに注意してください。  [Mixed Reality OpenXR Developer Portal](#getting-the-mixed-reality-openxr-developer-portal)をインストールすると、システム上の OpenXR ランタイムの現在の状態を確認できます。

## <a name="see-also"></a>関連項目

* <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR の詳細情報</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 仕様</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API リファレンス</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 クイックリファレンスガイド</a>
