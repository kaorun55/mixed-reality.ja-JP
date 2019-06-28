---
title: 表示
description: Holographic レンダリングにより、ユーザーの世界で正確な場所でホログラムを描画するために、アプリ、または作成した仮想領域内で、物理世界で正確に配置するかどうか。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: レンダリング、ホログラム
ms.openlocfilehash: 45713fd7a30fc55a799da7e89ef52aff8f7eec46
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415411"
---
# <a name="rendering"></a>表示

Holographic レンダリングにより、ユーザーの世界で正確な場所でホログラムを描画するために、アプリケーション、または作成した仮想領域内で、物理世界で正確に配置するかどうか。 [ホログラム](hologram.md)のサウンドと光のオブジェクトします。 レンダリングは、ライトを追加する、applicaition を使用できます。

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

HoloLens ユーザーが現実の世界と、ホログラムの両方をまとめて--表示できるように透過表示をブロックする Windows Mixed Reality イマーシブ ヘッドセットなどの非透過の表示をレンダリングするかどうか把握キー holographic の表示にすることです。世界です。

使用してデバイス**透かしが表示されます**など、 [HoloLens](hololens-hardware-details.md)、世界中に光を追加します。 黒ピクセルは明るいピクセルはますます不透明な完全に透明です。 ディスプレイから光は、現実世界から光に追加するため、白いピクセルはやや半透明です。

ステレオスコ ピック レンダリング、ホログラムの深さの 1 つのキューには、追加[効果の接地](interaction-fundamentals.md)より簡単にどのような画面ホログラムが近くのユーザーを支援できます。 1 つの接地手法では、近くにあるサーフェイスでは、光彩ホログラムの周囲を追加し、この光彩に対して影をレンダリングします。 この方法では、環境から光を減算する、シャドウが表示されます。 [空間サウンド](spatial-sound.md)ユーザー ホログラムの相対的な場所との距離を判断できるようにすること、もう 1 つの非常に重要な深さキューです。

使用してデバイス**不透明な表示**と同様に、 [Windows Mixed Reality イマーシブ ヘッドセット](immersive-headset-hardware-details.md)世界をブロックします。 黒ピクセルは黒一色、およびその他の任意の色は、ユーザーにその色として表示されます。 アプリケーションは、レンダリングのすべてのユーザーが表示されます。 これにより、ユーザーがある快適なエクスペリエンスをできるように、定数のリフレッシュ レートを維持するためにさらに重要です。

## <a name="predicted-rendering-parameters"></a>予測表示パラメーター

Mixed reality ヘッドセット (HoloLens とイマーシブ ヘッドセット) とその周囲の基準としたユーザーの頭の向きを継続的に追跡します。 その次のフレームの準備、アプリケーションの開始時、ユーザーの頭がされる将来的に、フレームがディスプレイに表示される正確な時点で、システムを予測します。 この予測に基づいて、システムは、そのフレームを使用するビューおよび射影変換を計算します。 アプリケーション**正しい結果を生成するために、これらの変換を使用する必要があります**システム提供の変換を使用しない場合は、結果のイメージの現実の世界では、ユーザーの不安を先頭の位置が合いません。

正確に予測、新しいフレームがディスプレイに到達すると、システムが常に、有効なエンド ツー エンド待機時間の計測、アプリケーションのレンダリング パイプラインに注意してください。 システムが調整されて、レンダリング パイプラインの長さ、中には、できるだけ短くするパイプラインを保持することでホログラム安定性を向上できます。

システムの予測を強化する高度な手法を使用するアプリケーションでは、システム ビューおよび射影変換をオーバーライドできます。 これらのアプリケーションする必要があります使用する必要がありますシステム提供の変換、カスタムの変換のための基礎として意味のある結果を生成するためにします。

## <a name="other-rendering-parameters"></a>その他の表示パラメーター

フレームをレンダリングするときに、システムは、アプリケーションの描画に使用する必要がありますバック バッファーのビューポートを指定します。 このビューポートは完全なフレーム バッファーのサイズより小さいがよくあります。 ビューポートのサイズに関係なく、アプリケーションでフレームをレンダリングすると、システムは、ディスプレイの全体を入力するイメージを upscales します。

検索自体、必要な更新料金を表示できません。 アプリケーションの[システム表示パラメーターを構成する](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)メモリ不足と増加のピクセルのエイリアスがレンダリング コストを削減します。 バック バッファー形式変更することも、メモリ帯域幅とピクセルのスループットを向上させるために役立つことがいくつかのアプリのことができます。

レンダリングの視錐台、解決、および表示するために、アプリが求められるフレーム レートが、フレームを変更する可能性があり、左および右の目の間で異なる場合があります。 たとえばときに、[実際のキャプチャを混在](mixed-reality-capture.md)(MRC) がアクティブと[写真/ビデオ カメラ ビューの構成](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)選択は大きく FOV または解像度で 1 つ目を表示する場合があります。

特定のフレーム、アプリの*する必要があります*ビューの変換、projection 変換、およびシステムによって提供されるビューポート解像度を使用して表示します。 さらに、アプリケーションでは、任意のレンダリングやビューのパラメーターはフレームから固定する必要があります考えないでください。 Unity などのエンジンは、物理的に移動、ユーザーとシステムの状態が常に尊重するようこれらすべての変換をする、独自のカメラ オブジェクトで処理します。 アプリケーションは、(、ゲームパッドでは、スティックを使用など) の世界をユーザーの仮想の移動を許可している場合は、その移動カメラの上の親リモート テスト マシン群オブジェクトを追加できます。 これにより、ユーザーの仮想および物理運動の両方を反映するようにカメラです。 呼び出して、適切なシステムに通知すべき場合は、アプリケーションでは、ビューの変換、projection 変換、またはシステムによって提供されるビューポートのディメンションを変更、 [API のオーバーライド](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)します。

Holographic、レンダリングの安定性を強化するためにアプリする必要があります提供 Windows に各フレーム、深度バッファーのレンダリングに使用します。 アプリが深度バッファーを提供している場合、カメラからのメートル単位で表される深さの一貫した深さの値が必要です。 これによりより若干予測の場所からのオフセット ユーザーの頭が終了した場合にコンテンツを安定化にピクセルあたりの深さデータを使用するシステムです。 深度バッファーを提供しない場合は、行うことができます、フォーカス ポイントと、通常、コンテンツのほとんどは、切断する平面を定義します。 深度バッファーとフォーカス プレーンの両方を指定しない場合、システムは、両方を使用可能性があります。 具体的には、深度バッファーと、アプリケーションが動いているホログラムを表示するときの速度ベクターを含むフォーカス ポイントの両方を提供することをお勧めします。

参照してください[DirectX でレンダリング](rendering-in-directx.md)彼のトピックに関する低レベルの詳細については、資料。

## <a name="holographic-cameras"></a>Holographic カメラ

Windows Mixed Reality の概念を紹介する、 **holographic カメラ**します。 Holographic のカメラは 3D グラフィックスのテキストにある従来のカメラに似ています。 両方外部定義 (位置と向き) と組み込みのカメラのプロパティ。 (例: 仮想 3D シーンを表示するビューのフィールドを使用します)。従来の 3D カメラとは異なり、アプリケーションは位置、向き、およびカメラの固有のプロパティのコントロールにありませんが。 代わりに、位置と holographic のカメラの向きに暗黙的にによって制御されます、ユーザーの移動。 ユーザーの移動は、ビューの変換を使用してフレームごとに、アプリケーションに中継されます。 同様に、カメラの固有のプロパティは、デバイスの調整されたレンズによって定義され、projection 変換を使用してフレームごとのリレー型します。

一般に、アプリケーションは、ステレオのカメラは 1 つのレンダリングされます。 ただし、堅牢なレンダリング ループは、複数のカメラをサポートし、mono とステレオの両方のカメラをサポートします。 たとえば、システムがユーザーなどの機能をアクティブにしたときに、代替の観点から表示するために、アプリケーションを求める場合があります[実際のキャプチャを混合](mixed-reality-capture.md)(MRC) 問題のヘッドセットの形状に応じて。 によって複数のカメラをサポートするアプリケーションを取得して[オプトインで](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)を[種類](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)のカメラをサポートできるようにします。

## <a name="volume-rendering"></a>ボリュームの表示

ときに医療 Mri をレンダリングまたは 3d でボリュームをエンジニア リング[ボリューム レンダリング](volume-rendering.md)手法がよく使用されます。 これらの手法は、ユーザー自然で表示できますこのようなボリュームをキーの角度から自分の頭を移動するだけで、複合現実で特に興味深いで指定できます。

## <a name="supported-resolutions-on-hololens-1st-gen"></a>HoloLens で解像度をサポートされています (第 1 世代)
> [!NOTE]
> 近日公開予定の更新が発生します。 [更新プログラムの一覧を表示します。](release-notes-april-2018.md)

* 現在、最大のサポートされている解像度のプロパティ、[ビュー構成](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)します。 HoloLens は、既定では、720 p (1268 x 720) には、最大解像度に設定されます。
* ビューポートがサポートされる最小サイズは、360 p (634 x 360) が 720p の 50% です。 HoloLens、これは 0.5 の ViewportScaleFactor です。
* 540 p はより低い場合何も**しないで**visual の低下が原因がピクセルのフィル レートでの bottle 突き止めるを識別するために使用できます。

## <a name="supported-resolutions-on-hololens-2"></a>HoloLens 2 でサポートされている解決策

> [!NOTE]
> HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。


## <a name="see-also"></a>関連項目
* [ホログラムの安定性](hologram-stability.md)
* [DirectX でのレンダリング](rendering-in-directx.md)
