---
title: ホログラムの安定性
description: HoloLens は、ホログラムを自動的に安定化しますが、開発者はさらにホログラムの安定性を向上させることができます。
author: thetuvix
ms.author: alexturn
ms.date: 07/08/2020
ms.topic: article
keywords: ホログラム、安定性、hololens
appliesto:
- HoloLens
ms.openlocfilehash: 4a489c923138808e3afb545097c314f354b5ad2a
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408210"
---
# <a name="hologram-stability"></a>ホログラムの安定性

## <a name="overview"></a>概要

安定したホログラムを実現するために、HoloLens にはイメージ安定化パイプラインが組み込まれています。 安定化パイプラインはバックグラウンドで自動的に動作するため、有効にするための追加の手順を実行する必要はありません。 ただし、ホログラムの安定性を向上させ、安定性を低下させるシナリオを回避する手法を使用する必要があります。

## <a name="hologram-quality-terminology"></a>ホログラムの品質に関する用語

ホログラムの品質は、優れた環境と優れたアプリ開発の結果となります。 HoloLens が周囲を追跡できる環境で、1秒あたりの定数60フレームで実行されるアプリは、ホログラムと照合座標系が同期されていることを保証します。ユーザーの観点からは、静止するホログラムは環境に対して相対的に移動しません。

次の用語は、環境に関する問題を特定している場合や、表示速度が一貫していない場合、またはその他の場合に役立ちます。
* **精度.** ホログラムが世界中にロックされ、実際の世界に配置されると、周囲の環境を基準とした相対的な場所を維持し、ユーザーの動きや小規模な環境の変化に依存しないようにする必要があります。 後でホログラムが予期しない場所に表示される場合は、*精度*の問題です。 このようなシナリオは、2つの異なるルームが同一である場合に発生する可能性があります。
* **ずれ.** ユーザーは、ぶれの高周波数のぶれとしてのジッターを観察します。これは、環境の追跡が低下した場合に発生する可能性があります。 ユーザーの場合、ソリューションは[センサーチューニング](sensor-tuning.md)を実行しています。
* **Judder.** レンダリング周波数が低いと、ホログラムの動きとダブルイメージが不均一になります。 Judder は、モーションを持つホログラムで特に顕著です。 開発者は、 [60 FPS の定数](hologram-stability.md#frame-rate)を維持する必要があります。
* **誤差.** ユーザーは、最初に配置された場所から離れるように、ホログラムがずれていることを確認します。 特に、完全にマップされていない環境の一部で、ホログラムが[空間アンカー](spatial-anchors.md)から遠く離れた場合に、誤差が発生します。 空間アンカーの近くにホログラムを作成すると、誤差の可能性が低くなります。
* **Jumpiness.** ホログラムが位置をときどき "ポップ" または "ジャンプ" するとき。 Jumpiness は、追跡によって、環境の最新の理解に一致するようにホログラムが調整されると発生する可能性があります。
* **スイム.** ユーザーの頭の動きに対応する、ホログラムが sway に表示されるとき。 スイムは、アプリケーションに再[プロジェクション](hologram-stability.md#reprojection)が完全に実装されていない場合、および HoloLens が現在のユーザーに対して[調整](calibration.md)されていない場合に発生します。 ユーザーは[調整](calibration.md)アプリケーションを再実行して問題を解決できます。 開発者は、安定化平面を更新して安定性をさらに向上させることができます。
* **色の分離。** HoloLens のディスプレイは色分けされています。これは、60 Hz (個々の色フィールドは 240 Hz で表示されます) の赤、緑、青、緑の点滅色チャネルです。 ユーザーが目の付いた可動ホログラムを追跡するたびに、そのホログラムの先頭および末尾のエッジは、その構成色で分離され、レインボー効果が生成されます。 分離の度合いは、ホログラムの速度に依存します。 場合によっては、固定されたホログラムを見ながら1頭を移動すると、*[色の分離](hologram-stability.md#color-separation)* と呼ばれるレインボー効果が得られることもあります。

## <a name="frame-rate"></a>フレーム レート

フレームレートは、ホログラムの安定性の最初の柱です。 ホログラムが世界中で安定して表示されるようにするには、ユーザーに表示される各イメージに、正しい位置にホログラムが描画されている必要があります。 では、HoloLens の更新時に240に1秒間隔で表示され、新たにレンダリングされたイメージごとに4つの色フィールドが表示されます。これにより、60 FPS (1 秒あたりのフレーム数) のユーザーエクスペリエンスが得られます。 アプリケーション開発者は、可能な限り最良の方法を提供するために、60 FPS を維持する必要があります。これにより、オペレーティングシステムに対して16ミリ秒ごとに新しいイメージが一貫して提供されます。

**60 FPS**ホログラムを実際の世界に座っているように描画するには、ユーザーの位置からイメージをレンダリングする必要があります。 イメージのレンダリングには時間がかかるため、ディスプレイに画像が表示されたときのユーザーの頭の位置が HoloLens によって予測されます。 ただし、この予測アルゴリズムは概数です。 HoloLens には、レンダリングされたイメージを調整して、予測されるヘッド位置と実際のヘッド位置との違いを考慮するハードウェアがあります。 この調整によって、ユーザーに表示される画像が、正しい位置から表示されるかのように見えるようになり、ホログラムは安定したものになります。 イメージの更新は、小さな変更によって最適に機能します。また、視差のようにレンダリングされたイメージ内の特定の項目を完全に修正することはできません。

60 FPS でレンダリングすることにより、安定したホログラムの作成に役立つ3つの作業を行います。
1. イメージのレンダリングと、そのイメージがユーザーに表示されるまでの全体的な待機時間を最小限に抑えます。 ロックステップで実行されているゲームとレンダースレッドを含むエンジンでは、30FPS で実行すると、33.3 ミリ秒の余分な待機時間が追加される可能性があります。 待機時間を減らすと、予測エラーが減少し、ホログラムの安定性が向上します。
2. これにより、すべてのイメージがユーザーの目に到達するまでの待機時間が一貫しています。 30 fps でレンダリングした場合でも、画像は 60 FPS で表示されます。つまり、同じ画像が1行に2回表示されます。 2番目のフレームには、最初のフレームよりも16.6 ミリ秒の待機時間があり、より顕著なエラーの数を修正する必要があります。 このようなエラーの大きさが不整合になると、60 Hz の望ましくない judder が発生する可能性があります。
3. 一様ではない動作と二重画像によって特徴付けられるジャダーの出現を減らします。 高速なホログラムの動きと低いレンダリング レートは、顕著なジャダーに関連しています。 常に 60 FPS を維持しておくことは、特定の可動ホログラムの judder を回避するのに役立ちます。

**フレームレートの一貫性**フレームレートの一貫性は、1秒あたりの高フレーム数と同様に重要です。 場合によっては、コンテンツが豊富なアプリケーションでフレームが破棄されることはありません。また、HoloLens は、不定期に発生した障害から復旧するための高度なアルゴリズムを実装します。 ただし、絶えず変動するフレームレートは、ユーザーにとって、より低いフレームレートで一貫して実行するよりもはるかに顕著です。 たとえば、5つのフレーム (これらの5つのフレームの間は 60 FPS) に対してスムーズにレンダリングし、次の10フレーム (10 フレームの間は 30 FPS) に対して他のフレームをすべてドロップするアプリケーションは、30 FPS で一貫してレンダリングされるアプリケーションよりも不安定になります。

関連する注意事項として、[混合の現実のキャプチャ](mixed-reality-capture.md)を実行しているときに、オペレーティングシステムによってアプリケーションが 30 FPS にスロットルされます。

**パフォーマンス分析**アプリケーションのフレームレートのベンチマークに使用できるツールには、次のような種類があります。
* GPUView
* Visual Studio Graphics Debugger
* Unity などの3D エンジンに組み込まれたプロファイラー

## <a name="hologram-render-distances"></a>ホログラムのレンダリング距離

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

人間のビジュアルシステムでは、オブジェクトを固定し、オブジェクトに焦点を当てたときに、複数の距離に依存する信号を統合します。
* [宿泊施設](https://en.wikipedia.org/wiki/Accommodation_%28eye%29)-個々の視点の焦点。
* [収束](https://en.wikipedia.org/wiki/Convergence_(eye))-オブジェクトの中心に向かって、または外側に移動する2つの目。
* [付い双眼鏡](https://en.wikipedia.org/wiki/Stereopsis)格差は、オブジェクトの距離に依存している、左側と右目の画像との間の距離を示します。
* 網掛け、相対角度のサイズ、およびその他の monocular (単一目) のキュー。

収束と特別設備は、目が変化して異なる距離でオブジェクトを認識する方法に関連する余分な網膜手掛かりによって一意になります。 自然な表示では、収束と設備がリンクされています。 目が近く (たとえば、鼻) で表示されている場合、目は交差し、近くに配置されます。 目が無限に表示されると、目は並列になり、目は無限大になります。 

Hololens がユーザーから約 2.0 m 離れた場所で固定されているため、HoloLens を装着したユーザーは、常に 2.0 m に対応して明確なイメージを維持します。 アプリ開発者は、さまざまな深度でコンテンツとホログラムを配置することで、ユーザーの目がどのようになるかを制御します。 ユーザーがさまざまな距離に対応して収束すると、2つのキュー間の自然なリンクが解除されます。これにより、特に競合の大きさが大きい場合に、visual 不快感や疲労が発生する可能性があります。 

Vergence は、収束コンテンツをできるだけ 2.0 m の近くに保持することによって、不快感の競合を回避または最小化できます (つまり、可能な場合は、最も多くの分野が m の2.0 近くに配置されているシーンで)。 コンテンツを 2.0 m の近くに配置することはできませんが、ユーザーの距離が異なる場合は、vergence の競合の不快感が最大になります。 言い換えると、時間の経過と共に移動するホログラム 50 cm を離れた状態で、50 cm のままになっている静止したホログラムを見た方がはるかに快適です。

2つのディスプレイがこの距離で完全に重複するように設計されているため、2.0 m にコンテンツを配置することも便利です。 この平面から離れた画像については、holographic フレームの辺から離れたときに、他の画面に表示されている間、1つのディスプレイから表示されます。 この付い双眼鏡 rivalry、holorgam の深さの知覚に悪影響を及ぼす可能性があります。

**ユーザーからホログラムを配置する位置までの最適な距離**

![ユーザーからホログラムを配置する位置までの最適な距離](images/distanceguiderendering-750px.png)

**クリッププレーン**最大限に快適にするために、1 m でコンテンツをフェードアウトして、85 cm でレンダリング距離をクリッピングすることをお勧めします。 ホログラムとユーザーの両方が静止しているアプリケーションでは、ホログラムを 50 cm の近くに表示できます。このような場合、アプリケーションでは、クリップ平面を 30 cm 以下にし、フェードアウトをクリッププレーンから少なくとも 10 cm 離れた位置に配置する必要があります。 コンテンツが 85 cm を超える場合は常に、ユーザーがホログラムから近い場所に移動したり、ホログラムから遠くに移動したりしないようにすることが重要です。このような状況では、vergence の競合から不快感が発生する可能性が高いためです。 コンテンツは、ユーザーからの 85 cm よりも近くの操作の必要性を最小限に抑えるように設計する必要がありますが、コンテンツが 85 cm より近い状態でレンダリングされる必要がある場合は、開発者にとっての経験則として、ユーザーやホログラムが25% 以上の時間で移動しないようなシナリオを設計します。

**ベストプラクティス**ホログラムを 2 m に配置できず、収束と宿泊の間の競合を回避できない場合、ホログラムの配置に最適なゾーンは 1.25 m ~ 5 m です。 どのような場合でも、デザイナーは、ユーザーが 1 + m を操作できるようにコンテンツを構成する必要があります (たとえば、コンテンツサイズと既定の配置パラメーターを調整します)。

## <a name="reprojection"></a>再プロジェクション
HoloLens は、reprojection と呼ばれる高度なハードウェア支援型の holographic 安定化手法を実行します。 シーンがアニメーション化され、ユーザーが頭を動かしたときに、再プロジェクションでは、視点 (CameraPose) の動きと変化が考慮されます。  アプリケーションでは、reprojection を最大限に活用するために、特定のアクションを実行する必要があります。


再プロジェクションには主に4種類あります。
* **深さの再投影:** アプリケーションの作業量を最小限に抑えて最適な結果を生成します。  レンダリングされたシーンのすべての部分は、ユーザーからの距離に基づいて、個別に安定化されます。  一部のレンダリングアイテムは、詳細な変更がある場所で表示される場合があります。  このオプションは、HoloLens 2 とイマーシブヘッドセットでのみ使用できます。
* **平面の再プロジェクション:** アプリケーションが安定化を厳密に制御できるようにします。  平面はアプリケーションによって設定され、その平面上のすべてのものがシーンの最も安定した部分になります。  さらに、ホログラムは平面から離れているので、安定性は低くなります。  このオプションは、すべての Windows MR プラットフォームで使用できます。
* **自動平面再プロジェクション:** システムは、深度バッファーの情報を使用して安定化平面を設定します。  このオプションは、HoloLens generation 1 および HoloLens 2 で使用できます。
* **なし:** アプリケーションが何も実行しない場合、平面の再投影は、2メートルで固定されている、ユーザーの頭部の方向に固定された安定化平面と共に使用されます。通常、サブ標準の結果が生成されます。

アプリケーションは、さまざまな種類の再プロジェクションを可能にするために、特定のアクションを実行する必要があります。
* **深さの再投影:** アプリケーションは、描画されたすべてのフレームの深度バッファーをシステムに送信します。  Unity では、[ **XR Plugin Management**] の下にある [ **Windows Mixed Reality の設定**] ウィンドウにある [**共有深度バッファー** ] オプションを使用して深さの再投影が行われます。  DirectX アプリは CommitDirect3D11DepthBuffer を呼び出します。  アプリケーションで SetFocusPoint を呼び出すことはできません。
* **平面の再プロジェクション:** すべてのフレームで、アプリケーションは、安定する平面の場所をシステムに伝えます。  Unity アプリケーションは SetFocusPointForFrame を呼び出し、**共有深度バッファー**を無効にする必要があります。  DirectX アプリは SetFocusPoint を呼び出しますが、CommitDirect3D11DepthBuffer を呼び出すことはできません。
* **自動平面再プロジェクション:** を有効にするには、アプリケーションが深さの再投影の場合と同じように、システムに深度バッファーを送信する必要があります。  HoloLens 2 では、アプリケーションは、すべてのフレームに対して0のポイント (0) を SetFocusPoint する必要があります。  HoloLens のジェネレーション1の場合、アプリケーションは SetFocusPoint を呼び出すことはできません。

### <a name="choosing-reprojection-technique"></a>再プロジェクション技法の選択

安定化の種類 |    イマーシブヘッドセット |    HoloLens の生成1 | HoloLens 2
--- | --- | --- | ---
深さの再投影 |    推奨 |   該当なし |   推奨<br/><br/>Unity アプリケーションでは、Unity 2018.4.12 以降または Unity 2019.3 以降を使用する必要があります。 それ以外の場合は、自動平面 Reprojection を使用します。
自動平面再プロジェクション | 該当なし |   推奨される既定値 |   深さの再プロジェクションで最適な結果が得られない場合に推奨<br/><br/>Unity アプリケーションは、Unity 2018.4.12 以降または Unity 2019.3 以降を使用することをお勧めします。  以前のバージョンの Unity は、わずかに低下した再プロジェクション結果で動作します。
平面の再プロジェクション |   推奨されません |   自動平面が最適な結果を得られない場合に推奨 | いずれの深さのオプションでも目的の結果が得られない場合は、を使用します。    

### <a name="verifying-depth-is-set-correctly"></a>深さが正しく設定されていることを確認しています
            
Reprojection メソッドが深度バッファーを使用する場合は、深度バッファーの内容がアプリケーションのレンダリングされたシーンを表すことを確認することが重要です。  さまざまな要因によって問題が発生する可能性があります。 たとえば、ユーザーインターフェイスのオーバーレイをレンダリングするために使用される2番目のカメラがある場合は、実際のビューからすべての深度情報が上書きされる可能性があります。  多くの場合、透明なオブジェクトは深さを設定しません。  一部のテキスト表示では、既定で深さが設定されません。  描画に表示される異常は、深度がレンダリングされたホログラムと一致しない場合に表示されます。
            
HoloLens 2 には、デバイスポータルから有効にできる深さと設定されていない場所を示すビジュアライザーがあります。  [**ビュー**の  >  **ホログラムの安定性**] タブで、[**ヘッドセットの深さの視覚エフェクトを表示**する] チェックボックスをオンにします。  深度が適切に設定されている領域は青色になります。  深度が設定されていないレンダリング項目は赤でマークされ、修正する必要があります。  

> [!NOTE]
> 詳細の視覚化は、Mixed Reality のキャプチャでは表示されません。  デバイスでのみ表示されます。
            
一部の GPU 表示ツールでは、深度バッファーを視覚化できます。  アプリケーション開発者は、これらのツールを使用して、深さが適切に設定されていることを確認できます。  アプリケーションのツールのドキュメントを参照してください。

### <a name="using-planar-reprojection"></a>平面の再プロジェクションの使用
> [!NOTE]
> デスクトップのイマーシブヘッドセットの場合、通常は安定化平面を設定します。これは、アプリの深度バッファーをシステムに提供してピクセル単位の深さベースの再プロジェクションを有効にするよりも、ビジュアルの品質が低下するためです。 HoloLens で実行しない限り、通常は安定化平面の設定を避ける必要があります。

![3D オブジェクトの安定化平面](images/stab-plane-500px.jpg)

デバイスは自動的にこの平面を選択しようとしますが、アプリケーションはシーンでフォーカスポイントを選択して支援する必要があります。 HoloLens で実行されている Unity アプリでは、シーンに基づいて最適なポイントを選択し、 [SetFocusPoint ()](focus-point-in-unity.md)に渡す必要があります。 DirectX でフォーカスポイントを設定する例は、既定のスピンキューブテンプレートに含まれています。

Unity は Windows に深度バッファーを送信し、デスクトップ PC に接続されたイマーシブヘッドセットでアプリを実行するときに、ピクセルごとの再プロジェクションを有効にします。これにより、アプリによる明示的な作業を必要とすることなく、より優れたイメージ品質が提供されます。 アプリが HoloLens で実行されている場合、またはピクセルごとの再プロジェクションがオーバーライドされる場合にのみ、フォーカスポイントを提供する必要があります。


```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

フォーカスポイントの配置は、多くの場合、ホログラムが見ている内容によって異なります。 アプリには、参照用の宝石ベクトルがあり、アプリデザイナーはユーザーに対して確認するコンテンツを認識します。

ホログラムを安定させるために開発者が実行できる最も重要な1つの点は、60 FPS でレンダリングすることです。 60 FPS を下回ると、安定化平面の最適化に関係なく、ホログラムの安定性が大幅に減少します。

**ベストプラクティス**安定化平面を設定するための汎用的な方法はなく、アプリに固有のものです。 主に、お客様のシナリオに最も適していることを試してみることをお勧めします。 ただし、この平面上のすべてのコンテンツが完全に安定しているため、できるだけ多くのコンテンツを安定化平面に揃えるようにしてください。

次に例を示します。
* 平面コンテンツ (アプリの読み取り、ビデオ再生アプリ) のみがある場合は、安定化平面をコンテンツを持つ平面に揃えます。
* 世界中にロックされている小さな球体が3つある場合は、ユーザーのビューに現在存在するすべての球体の中心を "切り取り" にします。
* シーンの深さが大きく異なる場合は、さらにオブジェクトを優先します。
* ユーザーが見ているホログラムと一致するように、すべてのフレームの安定化ポイントを調整してください。

**回避すべき**こと安定化平面は安定したホログラムを実現するための優れたツールですが、誤用されると、イメージが不安定になる可能性があります。
* "火災と忘れる" ことは避けてください。 最終的には、ユーザーの背後にある安定化面を使用したり、ユーザーのビューに存在しなくなったオブジェクトにアタッチしたりすることができます。 安定化平面の法線が反対のカメラに設定されていることを確認します (例:-camera. forward)
* 安定した平面を極端に逆方向に変更しない
* 安定化平面を固定距離/向きに設定したままにしない
* 安定化平面をユーザーに対して切り取ることを許可しない
* HoloLens ではなくデスクトップ PC で実行する場合は、フォーカスポイントを設定しないでください。代わりに、ピクセルごとの深度ベースの再プロジェクションに依存します。

## <a name="color-separation"></a>色の分離 

HoloLens ディスプレイの性質により、"カラー分離" と呼ばれるアーティファクトが認識されることがあります。 これは、個々の基本色 (赤、緑、および青) に分割するイメージとしてマニフェストを持ちます。 アイテムは、赤、緑、および青が非常に多いため、白いオブジェクトを表示するときに特に表示できます。 これは、ユーザーが holographic フレーム間を移動しているホログラムを高速で視覚的に追跡する場合に最も顕著になります。 アーティファクトでマニフェストを実行するもう1つの方法は、オブジェクトのワープ/変形です。 オブジェクトのコントラストやピュア色 (赤、緑、青など) が高い場合、色の分離は、オブジェクトのさまざまな部分のワープとして認識されます。

**ヘッドロックされた白いラウンドカーソルの色の分離の例は、ユーザーが頭を左右に回転させると、次のようになります。**

![ヘッドロックされた白いラウンドカーソルの色の分離の例は、ユーザーが頭を左右に回転させた場合のようになります。](images/colorseparationofroundwhitecursor-300px.png)

色の分離を完全に回避することは困難ですが、それを軽減するために使用できる手法がいくつかあります。

**色の分離は次のようになります。**
* [カーソル](cursors.md)などのヘッドロックオブジェクトを含む、すばやく移動するオブジェクト。
* [安定化平面](hologram-stability.md#reprojection)からかなり遠く離れたオブジェクト。

**色の分離の効果を弱めるには、次のようにします。**
* オブジェクトをユーザーの宝石にラグさせる。 これは、慣性があるかのように表示され、宝石の "スプリング" にアタッチされます。 この方法では、カーソルの速度が低下し (分離距離が短縮されます)、ユーザーの考えられるポイントの背後に配置されます。 ユーザーが宝石の移動を止めたときにすぐに追いつくのであれば、自然な感じです。
* ホログラムを移動する場合は、ユーザーが目を見ていくことが予想される場合は、移動速度を5°/秒未満にしてください。
* カーソルには、 *geometry*ではなく*light*を使用します。 見つめに接続されている仮想照明のソースは、対話型ポインターとして認識されますが、色の分離は行われません。
* ユーザーが行っているホログラムと一致するように安定化平面を調整します。
* オブジェクトを赤、緑、または青にします。
* ぼやけたバージョンのコンテンツに切り替えます。 たとえば、丸い白のカーソルを、動きの方向に少しぼやけた線に変更することができます。

前と同様に、60 FPS でのレンダリングと安定化平面の設定は、ホログラムの安定性を確保するための最も重要な手法です。 色の区別が目立つ場合は、まず、フレームレートが期待どおりであることを確認します。

## <a name="see-also"></a>関連項目
* [Mixed Reality のパフォーマンスについて](understanding-performance-for-mixed-reality.md)
* [色、ライト、素材](color,-light-and-materials.md)
* [本能的な操作](interaction-fundamentals.md)
* [MRTK ホログラム安定化](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html)
