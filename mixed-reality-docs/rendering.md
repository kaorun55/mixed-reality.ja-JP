---
title: 表示
description: Holographic レンダリングにより、ユーザーの世界で正確な場所でホログラムを描画するために、アプリ、または作成した仮想領域内で、物理世界で正確に配置するかどうか。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: レンダリング、ホログラム
ms.openlocfilehash: 5271e94521b99e76998c2cbb43475a5f3f847917
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829903"
---
# <a name="rendering"></a>表示

Holographic レンダリングにより、ユーザーの世界で正確な場所でホログラムを描画するために、アプリ、または作成した仮想領域内で、物理世界で正確に配置するかどうか。 [ホログラム](hologram.md)サウンドと光のオブジェクトが作成および表示に光を追加するアプリができるようにします。

## <a name="device-support"></a>デバイスのサポート

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>表示</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Holographic のレンダリング

現実の世界と、ホログラムの両方を一緒に表示できるように、HoloLens のように透過表示または Windows Mixed Reality イマーシブ ヘッドセットの場合は、そのブロックのような非透過の画面にレンダリングするかどうか把握キー holographic の表示にすることです。世界を。

使用してデバイス**透かしが表示されます**と同様に、 [HoloLens](hololens-hardware-details.md)、世界中に光を追加します。 黒ピクセルは明るいピクセルがますます不透明が完全に透明になります。 ディスプレイから光は、現実世界から光に追加するためも白いピクセルが半透明ややです。

ステレオスコ ピック レンダリング、ホログラムの深さの 1 つのキューには、追加[効果の接地](interaction-fundamentals.md)より簡単にどのような画面ホログラムが近くのユーザーを支援できます。 1 つの接地手法では、近くにあるサーフェイス ホログラム周囲光彩 () を追加し、に対してこの光彩のシャドウをレンダリングです。 この方法では、環境から光を減算する、シャドウが表示されます。 [空間サウンド](spatial-sound.md)ユーザー ホログラムの相対的な場所との距離を判断できるようにすること、もう 1 つの非常に重要な深さキューを指定できます。

使用してデバイス**不透明な表示**と同様に、 [Windows Mixed Reality イマーシブ ヘッドセット](immersive-headset-hardware-details.md)世界をブロックします。 黒ピクセルは黒一色になり、その他の任意の色は、ユーザーにその色として表示されます。 アプリがので、ユーザーがある快適なエクスペリエンスをできるように、定数のリフレッシュ レートを維持するためにさらに重要なすべてのユーザーが表示されるレンダリングを担当します。

## <a name="predicted-rendering-parameters"></a>予測表示パラメーター

Mixed reality ヘッドセット (HoloLens とイマーシブ ヘッドセット) とその周囲の基準としたユーザーの頭の向きを継続的に追跡します。 その次のフレームの準備、アプリの開始時、ユーザーの頭がされる将来のディスプレイ上、フレームが表示される正確な時点で、システムを予測します。 この予測に基づいて、システムは、そのフレームを使用するビューおよび射影変換を計算します。 アプリケーション**正しい結果を生成するために、これらの変換を使用する必要があります**システム提供の変換を使用しない場合は、結果のイメージの現実の世界では、ユーザーの不安を先頭の位置が合いません。

正確に予測、新しいフレームがディスプレイに到達すると、システムが常に、有効なエンド ツー エンド待機時間の計測、アプリのレンダリング パイプラインに注意してください。 システムは、レンダリング パイプラインの長さに調整は、中には、できるだけ短くするパイプラインを保持することでさらにホログラム安定性を改善できます。

システムの予測を強化する高度な手法を使用するアプリケーションでは、システム ビューおよび射影変換をオーバーライドできます。 これらのアプリする必要があります使用する必要がありますシステム提供の変換、カスタムの変換のための基礎として意味のある結果を生成するためにします。

## <a name="other-rendering-parameters"></a>その他の表示パラメーター

フレームをレンダリングするときに、システムは、アプリケーションの描画に使用する必要がありますバック バッファーのビューポートを指定します。 このビューポートは、多くの場合、完全なフレーム バッファーのサイズより小さくなります。 ビューポートのサイズに関係なく、アプリケーションで、フレームがレンダリングされた後、システムが拡大表示の全体を入力するイメージ。

検索自体、必要な更新料金を表示できません。 アプリケーションの[システム表示パラメーターを構成する](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)メモリ不足や増加のピクセルのエイリアスがレンダリング コストを削減します。 バック バッファー形式変更することも、メモリ帯域幅とピクセルのスループットを向上させるために役立つことがいくつかのアプリのことができます。

レンダリングの視錐台、解決、および表示するために、アプリが求められるフレーム レートがフレーム間を変更することも、左および右の目の間で異なる場合があります。 たとえばときに、[実際のキャプチャを混在](mixed-reality-capture.md)(MRC) がアクティブと[写真/ビデオ カメラ ビューの構成](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)が選択に、1 つ目は、大きく FOV または解像度で表示する場合があります。

特定のフレーム、アプリの*する必要があります*ビューの変換、projection 変換、およびシステムによって提供されるビューポート解像度を使用して表示します。 さらに、アプリケーションでは、任意の表示/表示パラメーターはフレーム単位から固定する必要があります考えないでください。 Unity などのエンジンは、物理的に移動、ユーザーとシステムの状態が常に尊重するようこれらすべての変換をする、独自のカメラ オブジェクトで処理します。 さらに、アプリは、(、ゲームパッドでは、スティックを使用など) の世界をユーザーの仮想の移動を許可している場合、ユーザーの両方の仮想および物理運動を反映するようにカメラの原因を移動カメラの上の親「装置」オブジェクトに追加できます。 呼び出して、適切なシステムに通知すべき場合は、アプリは、ビューの変換、projection 変換、またはシステムによって提供されるビューポートのディメンションを変更、 [API のオーバーライド](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)します。

Holographic、レンダリングの安定性を強化するためにアプリする必要があります提供 Windows に各フレーム、深度バッファーのレンダリングに使用します。 アプリが深度バッファーを提供している場合、カメラからのメートル単位で表される深さの一貫した深さの値が必要です。 これによりより若干予測の場所からのオフセット ユーザーの頭が終了した場合にコンテンツを安定化にピクセルあたりの深さデータを使用するシステムです。 深度バッファーを提供されない場合が代わりに、フォーカス ポイントと指定 normal、コンテンツのほとんどは、切断する平面を定義します。 深度バッファーとフォーカス プレーンの両方を指定しない場合、システムは両方を使用できます。 具体的には、深度バッファーと、アプリが動いているホログラムを表示するときの速度ベクターを含むフォーカス ポイントの両方を指定すると便利ができます。

詳細についてはすべて、低レベルここで、チェック アウト、 [DirectX でレンダリング](rendering-in-directx.md)記事。

## <a name="holographic-cameras"></a>Holographic カメラ

Windows Mixed Reality の概念を紹介する、 **holographic カメラ**します。 Holographic のカメラは 3D グラフィックスのテキストにある従来のカメラに似ています: 両方外部定義 (位置と向き) と組み込みのカメラのプロパティ (例: フィールドからビューの) 仮想 3D シーンを表示するために使用します。 従来の 3D カメラとは異なり、アプリケーションは位置、向き、およびカメラの固有のプロパティのコントロールにありませんが。 代わりに、位置と holographic のカメラの向きに暗黙的にによって制御されます、ユーザーの移動。 ユーザーの移動は、ビューの変換を使用してフレームごとに、アプリケーションに中継されます。 同様に、カメラの固有のプロパティは、デバイスの調整されたレンズによって定義され、projection 変換を使用してフレームごとのリレー型します。

一般に、アプリを表示して、ステレオのカメラは 1 つが。 ただし、堅牢なレンダリング ループは、複数のカメラをサポートする必要があります、mono とステレオの両方のカメラをサポートする必要があります。 システムを要求するユーザーなどの機能をアクティブにしたときに、代替の観点から表示するために、アプリなど、[実際のキャプチャを混在](mixed-reality-capture.md)(MRC) 該当ヘッドセットの形状に応じて。 によって複数のカメラをサポートできるアプリを取得して[オプトインで](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)を[種類](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)のカメラをサポートできるようにします。

## <a name="volume-rendering"></a>ボリュームの表示

医療を表示するときに MRI または 3d でボリュームをエンジニア リング[ボリューム レンダリング](volume-rendering.md)手法がよく使用されます。 これらの手法は、ユーザー自然で表示できますこのようなボリュームをキーの角度から自分の頭を移動するだけで、複合現実で特に興味深いで指定できます。

## <a name="supported-resolutions-on-hololens-1st-gen"></a>HoloLens で解像度をサポートされています (第 1 世代)
> [!NOTE]
> この記事には今後に予定するその他の更新があります。 [更新プログラムの一覧を表示します。](release-notes-april-2018.md)

* 現在、最大のサポートされている解像度のプロパティ、[ビュー構成](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)します。 HoloLens は、既定では、720 p (1268 x 720) には、最大解像度に設定されます。
* ビューポートがサポートされる最小サイズは、360 p (634 x 360) が 720p の 50% です。 HoloLens、これは 0.5 の ViewportScaleFactor です。
* 540 p はより低い場合何も**しないで**visual の低下が原因がピクセルのフィル レートでの bottle 突き止めるを識別するために使用できます。

## <a name="supported-resolutions-on-hololens-2"></a>HoloLens 2 でサポートされている解決策

> [!NOTE]
> HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。


## <a name="see-also"></a>関連項目
* [ホログラムの安定性](hologram-stability.md)
* [DirectX でのレンダリング](rendering-in-directx.md)