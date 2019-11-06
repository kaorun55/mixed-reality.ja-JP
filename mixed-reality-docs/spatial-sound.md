---
title: 混合現実のオーディオ
description: 混合現実のオーディオを使用すると、UI インタラクションのユーザーの信頼を高め、ユーザーのエクスペリエンスをこちらことができます。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 空間サウンド、サラウンドサウンド、3d オーディオ、3d サウンド、空間オーディオ
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641115"
---
# <a name="audio-in-mixed-reality"></a>混合現実のオーディオ
オーディオは、混合現実の設計と生産性の重要な部分であり、次のことが可能です。
* ジェスチャと音声ベースの対話でユーザーの信頼度を高める
* ユーザーガイドの次の手順
* 仮想オブジェクトを実際の世界と効果的に組み合わせる

HoloLens を含む mixed reality ヘッドセットの待機時間の短いヘッドトラッキングでは、高品質の HRTF ベースの spatialization を使用できます。 アプリケーションの Spatializing オーディオは次のようになります。
* ビジュアル要素へのアテンション呼び出し
* ユーザーが実際の環境を認識できるようにする

Acoustics を追加すると、ホログラムが混合世界に接続され、環境とオブジェクトの状態に関する手掛かりを得ることができます。

オーディオを使用したデザインの詳細な例については、「[サウンドのデザイン](spatial-sound-design.md)」を参照してください。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>Spatialization</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Spatialization ハードウェアアクセラレーション</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="using-sounds-in-mixed-reality"></a>Mixed reality でのサウンドの使用
[Mixed reality でサウンドを使用](spatial-sound-design.md)する場合、タッチおよびキーボードおよびマウスアプリケーションとは別のアプローチが必要になることがあります。 サウンド設計の主な決定事項には、どのようなサウンドを spatialize し、どのような対話を sonify にするかが含まれます。 これらの決定は、ユーザーの自信、生産性、学習曲線に大きな影響を与える可能性があります。

### <a name="case-studies"></a>導入事例
HoloTour は事実上、世界中の tourist と歴史的なサイトにユーザーを移動させることになります。 次のケーススタディでは、HoloTour の HoloTour: [sound design](case-study-spatial-sound-design-for-holotour.md)のサウンドデザインについて説明します。 特殊なマイクとレンダリングのセットアップを使用して、サブジェクトスペースがキャプチャされました。

RoboRaid は、HoloLens の高エネルギー shooter です。 次のケーススタディでは、空間オーディオを最大限に利用するために使用されたデザインの選択について説明します。 [RoboRaid のサウンドデザイン](case-study-using-spatial-sound-in-roboraid.md)です。

## <a name="spatialization"></a>Spatialization
Spatialization は、空間オーディオの方向コンポーネントです。 7\.1 home シアターセットアップを使用する場合、spatialization は、スピーカー間のパンと同様に簡単です。 しかし、ヘッドホンが混在している場合は、正確さと快適さを実現するために HRTF ベースのテクノロジを使用することが不可欠です。 Windows には HRTF ベースの spatialization が用意されており、このサポートは HoloLens 2 でハードウェアアクセラレータを利用しています。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>Spatialize ですか。
Mixed reality アプリケーションの多くのサウンドには、リスナーの頭から音を spatialization、世界中に配置する、という利点があります。 アプリケーションで spatialization を最も効果的に使用するための推奨事項については、「[空間サウンドの設計](spatial-sound-design.md)」を参照してください。

### <a name="spatializer-personalization"></a>Spatializer のパーソナル化
HRTFs は、頻度の範囲内の耳間のレベルとフェーズの差を操作します。 これらは、物理的なモデルと、人間の頭、torso および ear 図形 (pinnae) の測定値に基づいています。 脳は、これらの違いに対応して、サウンドの方向を認識します。 

各個人には、独自の ear 図形、ヘッドサイズ、および耳の位置があります。したがって、最適な HRTFs は自分に準拠しているものです。 HoloLens では、ヘッドセットから pupilary distance (IPD) を使用して spatialization の精度が向上し、ヘッドサイズに対して HRTFs が調整されます。

### <a name="spatializer-platform-support"></a>Spatializer プラットフォームのサポート
Windows では、 [ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)を使用して、hrtfs などの spatialization を提供しています。 この API は、HoloLens 2 HRTF ハードウェアアクセラレーションをアプリケーションに公開します。

### <a name="spatializer-middleware-support"></a>Spatializer ミドルウェアのサポート
Windows の HRTFs のサポートは、一部のサードパーティのオーディオエンジンで利用できます。
* [Unity オーディオエンジン](spatial-sound-in-unity.md)プラグインは HRTF xapo を呼び出します。
* [Wwise なオーディオエンジンプラグイン](https://www.audiokinetic.com/products/plug-ins/msspatial/)は、ISpatialAudioClient API を呼び出します。

## <a name="acoustics"></a>Acoustics
空間オーディオは、方向よりも大きくなる可能性があります。 閉鎖、障害物、リバーブ、portalling、ソースモデリングなどの他のディメンションは、総称して "acoustics" と呼ばれます。 Acoustics を使用しない場合、spatialized サウンドには認識できない距離があります。

Acoustics の扱いは、単純なものから非常に複雑なものまでさまざまです。 任意のオーディオエンジンでサポートされているような単純なリバーブを使用すると、リスナーを囲む環境に spatialized サウンドをプッシュできます。 [プロジェクト acoustics](https://aka.ms/acoustics)などの acoustics システムから、より豊富で説得力のある acoustics 処理を利用できます。 Project Acoustics は、壁、ドア、およびその他のシーンジオメトリの効果をサウンドでモデル化できます。これは、開発時に関連するシーンジオメトリが既知の場合に有効なオプションです。

