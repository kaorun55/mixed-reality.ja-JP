---
title: 開発者向けの実際のキャプチャの混在
description: 開発者の複合現実のベスト プラクティスをキャプチャします。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、写真、ビデオ、キャプチャ、カメラ
ms.openlocfilehash: c2d98baf16b2ea724247224aabadc1e2ca533ec1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599454"
---
# <a name="mixed-reality-capture-for-developers"></a>開発者向けの実際のキャプチャの混在

> [!NOTE]
> HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。 

参照してください[アプリで有効にする MRC](#enabling-mrc-in-your-app)下 HoloLens 2 のガイダンスについては新しい MRC 機能。

ユーザーがかかる場合がありますので、[実際のキャプチャを混合](mixed-reality-capture.md)(MRC) 写真またはビデオをいつでも、いくつか点が、アプリケーションを開発するときに点に注意する必要があります。 これには、MRC 画質と MRCs をキャプチャ中にシステムの変更に応答するためのベスト プラクティスが含まれます。

開発者は、それぞれのアプリに、複合現実のキャプチャと挿入を統合できますもシームレスにします。

MRC HoloLens (第 1 世代) では、ビデオをサポートしており、720 p、最大の写真を MRC HoloLens 2 の 4 K 解像度を最大 1080p と写真のビデオをサポートします。

## <a name="the-importance-of-quality-mrc"></a>品質 MRC の重要性

複合現実にキャプチャされた写真とビデオが初めてユーザーがアプリの必要があります。 Microsoft Store のページで、またはソーシャル ネットワーク上で MRCs を共有する他のユーザーから複合現実のスクリーン ショットとしてかどうか。 MRC を使用するには、アプリのデモ、ユーザーを教育する、その混合世界の相互作用を共有するユーザーに促すユーザー調査および問題を解決します。

## <a name="how-mrc-impacts-your-app"></a>MRC がアプリに与える影響

### <a name="enabling-mrc-in-your-app"></a>アプリで MRC を有効にします。

既定では、アプリは複合現実のキャプチャを実行するユーザーを有効にする何もありません。 ただし、HoloLens 2 の設計では、写真/ビデオ (PV) カメラと画面間の距離を増加するためを導入することの PV カメラに配置されたサード カメラ レンダリングを生成するために新しいオプション**HoloLens 2**します。 

第 3 のカメラをで選択するとレンダリング HoloLens 2 プランの次の機能強化既定 MRC のエクスペリエンス。
* ホログラム位置は、物理環境と (ほぼ相互作用) を手にする必要があります正確なすべてのではなくオフセット距離で他にも、距離、[フォーカス ポイント](focus-point-in-unity.md)既定 MRC でわかる場合があります。
* MRC 出力ホログラムを表示するために使用されないよう、ヘッドセットで適切な目を侵害されるは。

### <a name="disabling-mrc-in-your-app"></a>アプリで MRC を無効にします。

2D アプリを使用する場合[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx)または[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx)を適切に構成されたスワップ チェーンを持つ保護されたコンテンツを表示するには、アプリのビジュアル コンテンツになります複合現実のキャプチャの実行中に隠されて自動的にします。

### <a name="knowing-when-mrc-is-active"></a>MRC がアクティブな場合を知る

[AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx)クラスは、(オーディオまたはビデオ) の実際のキャプチャを混在システムを実行する場合を把握するアプリで使用できます。

>[!NOTE]
>AppCapture の[GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx)デバイスの実際のキャプチャを混合する場合は null を使用できない API を返すことができます。 CapturingChanged イベントが中断されると、アプリの登録を解除しても、それ以外の場合 MRC がブロックされた状態を取得できます。

### <a name="best-practices-hololens-specific"></a>ベスト プラクティス (HoloLens 固有)

開発者から、追加の作業なしで動作する MRC が必要ですが、アプリの最適な複合現実キャプチャ エクスペリエンスを提供する注意すべきいくつかの点があります。

**MRC ブレンドするホログラムのアルファ チャネルを使用して、[カメラ](locatable-camera.md)画像**

最も重要な手順では、アプリが不透明な黒にオフになったときではなく透明な黒色にクリアするかどうかを確認します。 Unity では、既定では、MixedRealityToolkit これは、非 Unity で開発している場合は、1 つの行を変更する必要があります。

場合は、アプリが透明な黒を消去しないで MRC で見成果物の一部を次に示します。

**例エラー**:エッジ (透明な黒色に失敗した) コンテンツの周囲の黒

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**例エラー**:ホログラムのシーン全体の背景が黒で表示されます。 黒の背景で結果が 1 のバック グラウンドのアルファ値を設定

![黒の背景で結果が 1 のバック グラウンドのアルファ値を設定](images/clearopaqueblack-300px.png)

**予想される結果**:ホログラムが現実 (透明な黒色に消去する場合に予期される結果) を組み合わせた正しく表示されます。

![透明な黒色に消去する場合、予期される結果](images/cleartransparentblack-300px.png)

**解決方法**:
* アルファ値は 0 不透明な黒で表示されている任意のコンテンツを変更します。
* アプリが透明な黒色にクリアすることを確認します。
* Unity をオフに ID3D11DeiceContext::ClearRenderTargetView() で使用される色を変更する必要があります以外 Unity アプリの場合は、MixedRealityToolkit で自動的に既定値です。 不透明な黒 (0,0,0,1) ではなく、透明な黒 (0,0,0,0) をオフにすることを確認するには。

資産のアルファ値を調整できるは、場合に、通常にする必要はありませんようになりました。 ほとんどの場合、MRCs を適切にすぐに表示されます。 MRC には、前乗算されたアルファが想定しています。 アルファ値は、MRC キャプチャのみ影響します。

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>HoloLens で MRC が有効な場合の注意点

次と両方に適用 HoloLens (第 1 世代) HoloLens 2 では、それ以外の場合に記載されていない場合。

* システム 30 Hz レンダリングするアプリケーションが調整されます。 これによって MRC、アプリは、定数の予算の予約を保持する必要があるために実行する余地が作成され、30 fps の MRC レコードのビデオ フレーム レートとも一致
* 記録/ストリーミング時に"sparkle"に、デバイスの適切な目でホログラム内容が表示 MRC: テキストが読みにくくなる可能性があり、ホログラム端のギザギザよりが表示される (第 3 のカメラをで選択すると、上でレンダリング**HoloLens 2**を回避できますこのセキュリティの侵害)
* MRC 写真やビデオをアプリケーションの尊重[フォーカス ポイント](focus-point-in-unity.md)場合、アプリケーションが有効になっている、ホログラムを確認するために役立つ正確に配置します。 ビデオ、ホログラムが緩やかに変化にドリフト フォーカス ポイントの深さが大幅に変更された場合に表示されるように、フォーカス ポイントが滑らかです。 フォーカス ポイントから別の深さではホログラムが現実の世界を参照してください以下の例をフォーカス ポイントが 2 つのメートル単位で設定がホログラムが 1 m に配置されてからオフセット表示されます。

![世界中に完全に登録されている 2 m 離れたでホログラムが表示されます。 閉じる、またはここまでの距離でホログラムを少しずらして可能性があります。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>アプリ内から MRC 機能の統合

複合現実アプリは MRC 写真や、アプリ内からビデオのキャプチャを開始できるし、キャプチャされたコンテンツが格納されることがなく、アプリを使用できる、デバイスの「カメラ ロールです」を。 カスタム MRC レコーダーを作成したり、組み込みのカメラ キャプチャ UI を利用することができます。 

### <a name="mrc-with-built-in-camera-ui"></a>組み込みのカメラ UI で MRC

開発者が使用できる、 *[カメラ キャプチャ UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 複合現実のユーザーにキャプチャされた写真またはほんの数行のコードでビデオを取得します。

この API は、組み込み MRC カメラ元となる、ユーザーが写真やビデオにかかるし、アプリにキャプチャされたを返しますの UI を起動します。  か、独自のカメラ UI を作成する必要がある下位レベル キャプチャ ストリームへのアクセス、Mixed Reality キャプチャのカスタム recorder を作成することができます。

### <a name="creating-a-custom-mrc-recorder"></a>カスタム MRC レコーダーを作成します。

ユーザーが写真をトリガーできる常にまたはシステムを使用してビデオ MRC キャプチャ サービス、カスタム カメラ アプリの構築がホログラム MRC と同じように、カメラのストリームに含めるアプリケーションもかまいません。 これにより、ユーザーの代理としてキャプチャを開始、カスタムの記録、UI をビルドまたは MRC 設定例をいくつかの名前をカスタマイズするアプリケーションです。

**HoloStudio は、MRC 効果を使用してカスタム MRC カメラを追加します**

![HoloStudio は、MRC 効果を使用してカスタム MRC カメラを追加します](images/cameraiconholostudio-300px.jpg)

Unity アプリケーションを参照する必要があります[Locatable_camera_in_Unity](locatable-camera-in-unity.md)ホログラムを有効にするプロパティ。

他のアプリケーションを使用してこれを行うことができます、 [Windows メディア キャプチャ Api](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)をカメラを制御し、仮想ホログラムおよびアプリケーションのオーディオ静止画と動画に含める MRC ビデオおよびオーディオ効果を追加します。

アプリケーションでは、効果を追加する 2 つのオプションがあります。
* 古い API:[Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)
* 新しい Microsoft は、API (動的プロパティを操作できるように、オブジェクトを返します) をお勧めします。[Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) の独自の実装を作成、アプリが必要な[IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx)と[IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx)します。 サンプルの使用法の MRC 効果のサンプルを参照してください。

(これらの名前空間は、Visual Studio によって認識されませんが、文字列がまだ有効なことに注意してください)

MRC ビデオ特殊効果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  プロパティ名  |  種類  |  既定値  |  説明 | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))  |  1 (VideoRecord)  |  この効果を使用するキャプチャ ストリームについて説明します。 オーディオは、ご利用いただけません。 | 
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  有効またはホログラム ビデオのキャプチャを無効にするフラグします。 | 
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  有効またはホログラム キャプチャ中に画面の記録のインジケーターを無効にするフラグします。 | 
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  有効または、HoloLens の追跡ツールを搭載したビデオ安定化を無効にするフラグします。 | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  ビデオ安定化の使用は履歴フレームの数を設定します。 0 は、待機時間が 0 と能力とパフォーマンスの観点から「無料」ほぼです。 (待機時間とメモリの 15 フレーム) が最高品質には、15 を使用することをお勧めします。 | 
|  GlobalOpacityCoefficient  |  FLOAT  |  0.9 (HoloLens) 1.0 (イマーシブ ヘッドセット)  |  グローバルの不透明度の係数ホログラムの範囲内で 0.0 (完全に透明) から 1.0 に設定 (完全に不透明)。 | 
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  有効または 2d の UWP アプリの表示が保護されたコンテンツがある場合は、空のフレームを返すことを無効にするフラグします。 このフラグが false と 2d の UWP アプリの場合は保護されている表示をコンテンツの 2d の UWP アプリは、複合現実のキャプチャとヘッドセットの両方で保護されたコンテンツ テクスチャによって置き換えられます。 |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  有効または無効 holographic のカメラの非表示の領域のメッシュを表示して、隣接するコンテンツにフラグを設定します。 |

MRC オーディオ効果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>プロパティ名</th>
<th>種類</th>
<th>既定値</th>
<th>説明</th>
</tr>
<tr>
<td>MixerMode</td>
<td>UINT32</td>
<td>2</td>
<td>
<ul>
<li>0 :マイクのオーディオのみ</li>
<li>1 :システム オーディオのみ</li>
<li>2 :Mic およびシステム オーディオ</li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a>同時 MRC の制限事項

MRC にアクセスすると同時に複数のアプリに関する制限があります。

#### <a name="photovideo-camera-access"></a>写真/ビデオ カメラへのアクセス

写真/ビデオのカメラは、同時にアクセスできるプロセスの数に制限されます。 プロセスを記録中にビデオやその他のプロセスの写真の撮影写真とビデオのカメラの取得に失敗します。 (これは混合の実際のキャプチャと標準のフォトとビデオのキャプチャの両方に適用されます)

Windows 10 April 2018 Update では、この制限は適用されません組み込み MRC カメラ UI を使用する写真とビデオのカメラを使用して、アプリが開始した後に、写真やビデオを実行する場合。 この場合、解像度と組み込みの MRC カメラ UI のフレーム レートが標準値から低下する可能性です。

Windows 10 年 2018年 10 月 Update では、この制限は適用されません Miracast を介して MRC をストリーミングします。

#### <a name="mrc-access"></a>MRC アクセス

Windows 10 April 2018 Update が複数のアプリ (ただし、写真とビデオのカメラへのアクセスをまだ制限) MRC ストリームへのアクセスを制限します。

前に、Windows 10 April 2018 Update、アプリのカスタム MRC レコーダーでは、システム MRC (写真をキャプチャ、キャプチャするビデオ、または、Windows Device Portal からのストリーミング) で相互に排他的です。

## <a name="see-also"></a>関連項目
* [複合現実のキャプチャ](mixed-reality-capture.md)
* [Spectator ビュー](spectator-view.md)
