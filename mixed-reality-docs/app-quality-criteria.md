---
title: アプリの品質基準
description: このドキュメントでは、複合現実アプリの品質に影響を与える主な理由について説明します。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: アプリの品質基準、実際には、混合 mixed reality アプリ
ms.openlocfilehash: 756bc148f290aa3406c9ac8bb7003d463c62772c
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974749"
---
# <a name="app-quality-criteria"></a>アプリの品質基準

このドキュメントでは、複合現実アプリの品質に影響を与える主な理由について説明します。 次の情報を提供する各要素について
* 概要 – の品質要因と重要な理由の簡単な説明です。
* デバイスによる影響 - Mixed Reality をウィンドウのデバイスの種類は影響を受けます。
* 品質基準 – の品質要因を評価する方法。
* – メソッドに、問題を計測 (またはエクスペリエンス) を測定する方法。
* 推奨事項のより優れたユーザー エクスペリエンスを提供する方法の概要。
* リソース-関連する開発者とアプリのより優れたエクスペリエンスを作成すると便利であるデザイン リソース

## <a name="frame-rate"></a>フレーム レート

フレーム レートはホログラムの安定性とユーザーの快適性の最初の柱です。 推奨されるターゲットの下のフレーム レートには、ホログラムちらついたり、エクスペリエンスの信憑性に悪影響を与えると、目の疲労が発生する可能性を表示することがあります。 Windows Mixed Reality イマーシブ ヘッドセットでのユーザー エクスペリエンスのターゲット フレーム レートは、60 Hz またはサポートする Windows Mixed Reality 互換性のある Pc に応じて 90 Hz のいずれかになります。 HoloLens 先のフレーム レートは 60 Hz です。

### <a name="device-impact"></a>デバイスへの影響

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  満たす |  失敗 |
--- | --- | ---
| アプリでは、一貫してターゲット デバイスの 2 つ目の (FPS) 目標あたりのフレーム数を満たしています。HoloLens; に 60 fps90 超 Pc; fpsメイン ストリームの Pc で 60 fps します。 | アプリは、コア エクスペリエンスを妨げていない断続的なフレームのドロップまたは、FPS は一貫して目標より低いが、アプリのエクスペリエンスを妨げるありません。 | アプリには、フレーム レートの平均が 10 秒ごとに以下のドロップが発生しました。 |

### <a name="how-to-measure"></a>測定する方法

* リアルタイムのフレーム レートのグラフがを通じてによって提供される、 [Windows Device Portal](using-the-windows-device-portal.md#system-performance) 「システムのパフォーマンス」の下。
* 開発のデバッグには、アプリにフレーム レートの診断カウンターを追加します。 サンプルのカウンターは、リソースを参照してください。
* フレーム レートの低下は、頭を左右に移動することによって、アプリの実行中に、デバイスで発生することができます。 ホログラムちらつく移動の予期しない場合は、フレーム レートが低い、または安定性の面が原因である可能性があります。

### <a name="recommendations"></a>推奨事項

* 開発作業の開始時に、フレーム レート カウンターを追加します。
* フレーム レートの低下が発生する変更を評価して、パフォーマンス バグとして適切に解決する必要があります。

### <a name="resources"></a>参考資料

#### <a name="documentation"></a>ドキュメント

* [複合現実のパフォーマンスを理解](understanding-performance-for-mixed-reality.md)
* [ホログラム安定性とフレーム レート](hologram-stability.md#frame-rate)
* [資産のパフォーマンスの予算](asset-creation-process.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [MRToolkit、FPS カウンターの表示](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit、シェーダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>外部参照

* [Unity では、モバイル アプリケーションの最適化](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>ホログラム安定性

安定したホログラムは、使いやすさと、アプリの信憑性を向上し、ユーザーの使いやすい表示エクスペリエンスを作成します。 ホログラム安定性の品質が適切なアプリの開発と (追跡) を理解するデバイスの機能の結果をその環境。 フレーム レートが安定性の最初の柱の中、その他の要因の安定性を含む影響を与えることができます。

* 安定化平面の使用
* 空間アンカーまでの距離
* Tracking

### <a name="device-impact"></a>デバイスへの影響

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  満たす |  失敗 |
--- | --- | ---
|  ホログラムが一貫して安定したが表示されます。 | セカンダリのコンテンツは予期しない動きです。または、予期しない動きが全体的なアプリ エクスペリエンスを妨げるありません。 | フレームで主要なコンテンツには、予期せぬ動作が発生します。 |

### <a name="how-to-measure"></a>測定する方法

While ソックスを着けずに、デバイスと、エクスペリエンスを表示します。

* サイド バイ サイドに頭を移動、ホログラムが予期しない動きを表示する場合、フレーム レートが低いまたは焦点面に安定性の面の不適切なアラインメントは考えられる原因になります。
* ホログラムや環境を移動、スイムレーンと jumpiness などの動作を探します。 この種類のアニメーションは、空間アンカーに環境、または距離を追跡しないデバイスによる可能性があります。
* 大規模な場合、または複数ホログラムがフレームでは、安定化平面に起因揺れの可能性がありますが表示された場合、並列で、ヘッドの位置を移動中に、さまざまな深さでホログラム動作を観察します。

### <a name="recomendations"></a>Recomendations

* 開発作業の開始時、フレーム レート カウンターを追加します。
* 安定化平面を使用します。
* 常に、アンカーの 3 つのメートル単位でアンカー ホログラムをレンダリングします。
* 環境の適切な追跡のためのセットアップを確認します。
* フレーム内でさまざまな焦点の深さのレベルでホログラムを回避するために、エクスペリエンスをデザインします。

### <a name="resources"></a>参考資料

#### <a name="documentation"></a>ドキュメント

* [ホログラム安定性とフレーム レート](hologram-stability.md#frame-rate)
* [安定化平面を使用して、ケース スタディ](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [複合現実のパフォーマンスを理解](understanding-performance-for-mixed-reality.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)
* [空間アンカー](spatial-anchors.md)
* [追跡エラーの処理](coordinate-systems.md#handling-tracking-errors)
* [フレームの静止した基準](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [MR コンパニオン キット、Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>実際の画面上の位置をホログラム

物理オブジェクト相互の関連配置するためのもの) であればホログラムのずれは、ホログラムと実際の非結合の明確に示しています。 配置の精度が、シナリオのニーズを基準とする必要があります。たとえば、一般的な表面の配置は、空間のマップを使用できますより正確な配置マーカーおよび調整のいくつかの使用が必要になります。

### <a name="device-impact"></a>デバイスへの影響

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  満たす |  失敗 |
--- | --- | ---
| ホログラムは、通常は、センチメートルでインチの範囲の画面に揃えます。 精度が向上する必要がある場合、アプリは、必要なアプリ仕様内のコラボレーションの効率的な方法を提供する必要があります。 | 該当なし | サーフェスの平面互換性に影響するか、float、画面から離れた場所に表示される、ホログラムが物理的なターゲット オブジェクトにアラインされていない表示されます。 精度が必要な場合、ホログラムはシナリオの近接仕様を満たす必要があります。 | 

### <a name="how-to-measure"></a>測定する方法

* ホログラム空間のマップに配置されている必要がありますが大幅に float、画面の上下には表示されません。
* ホログラム正確な配置を必要とするには、何らかの形のマーカーと調整システム シナリオの要件に正確である必要があります。

### <a name="recommendations"></a>推奨事項

* 空間のマップは、有効桁数が必要なサーフェスでオブジェクトを配置するために便利です。
* 最適な精度では、マーカーまたはポスターを最終的な調整をホログラムと Xbox コント ローラー (または一部手動の配置メカニズム) を設定するのに使用します。
* 論理部分に非常に大規模なホログラムを分割し、画面には、各部分の配置を検討してください。
* 不適切なセット interpupilary 距離 (IPD) にホログラム配置も影響することができます。 常に、ユーザーの IPD に HoloLens を構成します。

### <a name="resources"></a>参考資料

#### <a name="documentation"></a>ドキュメント

* [空間マッピングの配置](spatial-mapping.md#placement)
* [スキャン処理ルーム](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [空間アンカーのベスト プラクティス](spatial-anchors.md#best-practices)
* [追跡エラーの処理](coordinate-systems.md#handling-tracking-errors)
* [Unity の空間マッピング](spatial-mapping-in-unity.md)
* [Vuforia 開発の概要](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [MR 空間 230:空間マッピング](holograms-230.md)
* [MR Toolkit、空間マッピング ライブラリ](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR コンパニオン キット、ポスターの調整のサンプル](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [MR コンパニオン キット、Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>外部参照

* [Lowes ケース スタディ、有効桁数の配置](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>快適性のゾーンの表示

アプリ開発者のコントロールはコンテンツとホログラムをさまざまな深さで配置することでユーザーの目が収束できます。 HoloLens ソックスを着けずにユーザーは、2.0 m 鮮明な画像は HoloLens に表示されるため、光学距離約 2.0 m ユーザーから離れた場所に固定は維持するために常に可能になります。 不適切なコンテンツの階層レベルは、visual 不安や疲労につながることができます。

### <a name="device-impact"></a>デバイスへの影響

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>品質基準

<table>
<tr>
<td> 最高 </td><td><ul>
<li>2 分には、コンテンツを配置します。</li><li>ホログラムは 2 m に配置されることはできず、収束と宿泊施設間の競合を回避することはできません、ホログラムを配置するための最適なゾーンが 1.25 m と 5 分間は。</li><li>すべてのケースでは、デザイナーがコンテンツを 1 以上の対話をユーザーに促すことを構成する必要がありますメートル離れた場所 (例: コンテンツのサイズを調整して、既定の配置パラメーター)。</li><li>具体的にはないシナリオで必要に応じて、しない限り、クリッピング平面が 1 m で始まる fadeout と実装にあります。</li><li>ようにホログラムの近くの監視が必要な場合は、コンテンツの 50 cm よりも近いしない場合があります。</li>
</ul></td>
</tr><tr>
<td> 満たす</td><td> コンテンツは、内で、表示およびモーションのガイダンスが、不適切な使用またはクリップの平面は使用されていません。</td>
</tr><tr>
<td> 失敗 </td><td> コンテンツの表示が近すぎる (通常&lt;1.25 m、または&lt;50 cm 静止ホログラムを詳しく監視を必要とするのです)。</td>
</tr>
</table>

### <a name="how-to-measure"></a>測定する方法

* コンテンツ通常は 2 m、退席中、1.25 または 5 分よりもさらにより近いいいえ。
* いくつかの例外を除き、HoloLens クリッピング レンダリングまでの距離を .85CM に fadeout 1 m からコンテンツを設定してください。 コンテンツのアプローチし、クリッピング平面の影響に注意してください。
* 静止しているコンテンツを 50 cm 離れたよりも近いすることはできません。

### <a name="recommendations"></a>推奨事項

* 2 分の最適な表示距離のコンテンツをデザインします。
* コンテンツが 1 m で始まる fadeout と 85 cm クリッピング レンダリングまでの距離を設定します。
* 近い場所を表示する必要がある静止ホログラム、30 cm 以内にないはクリップの面で、fadeout は少なくとも 10 cm クリッピング平面からを起動する必要があります。

### <a name="resources"></a>参考資料

* [距離をレンダリングします。](hologram-stability.md#hologram-render-distances)
* [Unity でのフォーカス ポイント](focus-point-in-unity.md)
* [スケールみる](scale.md#experimenting-with-scale)
* [テキスト、フォント サイズの推奨](typography.md#recommended-font-size)

## <a name="depth-switching"></a>深さの切り替え

快適性の問題のゾーンを表示に関係なくほぼし、oculomotor の疲労と一般的な不安をする可能性があります (ホログラムと実際のコンテンツを含む) までの焦点のオブジェクト間や頻繁にすばやくを切り替えるユーザーを要求します。

### <a name="device-impact"></a>デバイスへの影響

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  満たす |  失敗 |
--- | --- | ---
|  切り替えを限定的または自然の深さが原因で、ユーザーが膨らみます不自然しません。 | これはコアであり、アプリのエクスペリエンスに組み込むの突然の深さスイッチ、または実際の予期しないコンテンツによって発生した突然深さスイッチ。 | 一貫性のある深さスイッチ、または深さの突然の切り替えは必要のないまたは core アプリのエクスペリエンスをします。 | 

### <a name="how-to-measure"></a>測定する方法

* アプリが一貫してや突然の深さのフォーカスを変更するユーザーが必要な場合は、問題の切り替えの深さです。

### <a name="recommendations"></a>推奨事項

* 一貫性のある焦点面で主要なコンテンツを保持し、安定化の平面が焦点面と一致するかどうかを確認します。 Oculomotor 疲労と予期しないホログラム移動が軽減されます。

### <a name="resources"></a>参考資料

* [距離をレンダリングします。](hologram-stability.md#hologram-render-distances)
* [Unity でのフォーカス ポイント](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>空間のサウンドの使用

Windows Mixed Reality では、オーディオ エンジンは、3 D の方向、距離、および環境のシミュレーションを使用してサウンドをシミュレートすることで、複合現実エクスペリエンスの聴覚的なコンポーネントを提供します。 アプリケーションでサウンドの空間を使用すると、ユーザーを囲むが 3 次元空間 (球) でサウンドを配置する開発者ができます。 それらのサウンドは、実際の物理オブジェクトまたはユーザーの環境での複合現実ホログラムから送信されるがまるでようですが。 サウンドの空間は、immersion、アクセシビリティ、および複合現実のアプリケーションでの UX デザインの強力なツールです。

### <a name="device-impact"></a>デバイスへの影響

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  満たす |  失敗 |
--- | --- | ---
|  サウンドが spatialized は論理的にし、適切に、UX はオブジェクトの検出とユーザーのフィードバックを支援するサウンドを使用します。 サウンドがシナリオ全体であり自然なオブジェクトに関連する正規化されました。 | 空間オーディオは、信憑性で適切に使用されますが、ユーザーからのフィードバックと見つけやすさを支援するための手段として存在します。 | 予想どおり、サウンドが spatialized いないや UX 内のユーザーを支援するために、サウンドの欠如 または空間オーディオがないと見なされますまたはシナリオの設計で使用されます。 | 

### <a name="how-to-measure"></a>測定する方法

* 一般に、関連するサウンドがターゲット ホログラムから出力する必要があります (例:、holographic dog から見かけサウンド。)。
* フィードバックや認識 holographic フレーム外のアクションのユーザーを支援するためには、ユーザー エクスペリエンス全体でサウンド キューを使用してください。

### <a name="recommendations"></a>推奨事項

* 空間オーディオを使用して、オブジェクトの検出とユーザー インターフェイスを支援します。
* サウンドの実際の作業が合成または不自然なサウンドよりも優れています。
* ほとんどのサウンドを spatialized する必要があります。
* 発信機を非表示をしないようにします。
* 空間のマスクを回避します。
* すべてのサウンドを正規化します。

### <a name="resources"></a>参考資料

#### <a name="documentation"></a>ドキュメント

* [立体音響](spatial-sound.md)
* [立体音響の設計](spatial-sound-design.md)
* [Unity の立体音響](spatial-sound-in-unity.md)
* [ケース スタディ、HoloTour のサウンドの空間](case-study-spatial-sound-design-for-holotour.md)
* [RoboRaid でサウンドの空間を使用して、ケース スタディ](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [MR 空間 220:立体音響](holograms-220.md)
* [MRToolkit、空間オーディオ](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Holographic フレーム (FOV) の境界に集中します。

適切に設計されたユーザー エクスペリエンスを作成し、仮想環境、ユーザーの周りを拡張するのに便利なコンテキストを維持できます。 コンテンツのスケールとコンテキストの親切なデザイン FOV 境界の影響を軽減する必要があります、空間オーディオ、ガイダンスのシステムとユーザーの位置を使用します。 場合、ユーザーは快適なアプリ エクスペリエンスをことができますが、FOV 境界によって損なわれる小さいを感じです。

### <a name="device-impact"></a>デバイスへの影響

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  満たす |  失敗 |
--- | --- | ---
|  ユーザー コンテキストを失うことは、表示する使いやすい。 ラージ オブジェクトのコンテキストのサポートが提供されます。 フレームの外側のオブジェクトの見つけやすさとガイダンスの表示が提供されます。 一般に、モーションの設計と、ホログラムの小数点以下桁数は、快適な表示エクスペリエンスに適しています。 | ユーザーには、コンテキストが失われることが、余分の足部の動きを限られた状況で必要があります。 限られた状況では、スケールはホログラム ホログラムを表示するには、いくつかネック モーションの原因と垂直方向または水平方向のフレームのいずれかを中断するとします。 | ホログラムを表示するには、ユーザーのコンテキストや首部分の一貫性のあるモーションが失われる可能性がありますが必要です。 なし、見つけやすさのガイダンスについては、または縦ホログラム フレームの外側に失われやすくオブジェクトの移動、holographic ラージ オブジェクトのコンテキストのガイダンスには、正規の足部の動きを表示する必要ありません。 | 

### <a name="how-to-measure"></a>測定する方法

* (大) ホログラムのコンテキストが紛失または境界にクリップされているため認識されません。
* ホログラムの場所は、注意取締役や holographic のフレームとの間にすばやく移動できるコンテンツがないのために見つけにくくします。
* 正規表現での足部の疲労ホログラムを完全に表示するヘッド モーションを上下に反復的なシナリオが必要です。

### <a name="recommendations"></a>推奨事項

* 視界に合わせて、大きなバージョンを視覚的に移行し、小さなオブジェクトをエクスペリエンスを開始します。
* 空間のオーディオおよび注意ディレクターを使用して、ヘルプ、視界の外にあるユーザーの検索コンテンツ。
* 垂直方向にクリップの視界ホログラムが、できる限り多くしないでください。
* 適切に場所を表示するアプリでのガイダンスをユーザーに提供します。

### <a name="resources"></a>参考資料

#### <a name="documentation"></a>ドキュメント

* [ホログラフィック フレーム](holographic-frame.md)
* [ケース スタディ、HoloStudio UI および相互作用のデザインの学習](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [オブジェクトおよび環境のスケール](scale.md)
* [カーソル、視覚的な合図](cursors.md#visual-cues)

#### <a name="external-references"></a>外部参照

* [Ado の利用、FOV](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>コンテンツがユーザーの位置に対応します。

ホログラムは、「実際の」オブジェクトと同じ方法ほぼ内のユーザーの位置に対応する必要があります。 注目すべき設計の考慮事項は、ユーザーの位置を想定できません必ずしも UI 要素が静止していると、ユーザーの動きに合わせては。 ユーザーの位置に正しく対応するアプリをデザインよりかぎりエクスペリエンスの作成し、使いやすきます。

### <a name="device-impact"></a>デバイスへの影響

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>品質基準

<table>
<tr>
<td> 最高 </td><td> コンテンツと UI は、自然の想定されるユーザーの移動のスコープ内のコンテンツと対話するユーザーを許可するユーザーの位置に適応します。</td>
</tr><tr>
<td> 満たす </td><td> UI は、ユーザーの位置に対応しますが、それらの位置を調整するユーザーを必要とするキーのコンテンツの表示を妨げる可能性が。</td>
</tr><tr>
<td> 失敗 </td><td><ol>
<li>UI 要素が紛失または、移動の原因となるユーザー コントロールを不自然に戻ります (または見つける) 中にロックされています。</li><li>UI 要素は、主要なコンテンツの表示を制限します。</li><li>特に、運動量との距離を表示するため UI の動きが最適化されていない<a href="billboarding-and-tag-along.md">tag-along</a> UI 要素。</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>測定する方法

* すべての測定値は、シナリオの妥当な範囲内で行う必要があります。 ユーザーの移動はによって異なりますが、極端なユーザーの移動は、アプリをください。
* UI 要素、関連するコントロールをユーザーの移動に関係なく利用してください。 たとえば、ユーザーが表示とズームを使用して 3D マップを歩きながら、ズーム コントロールが場所に関係なく、ユーザーにすぐに使用できる必要があります。

### <a name="recommendations"></a>推奨事項

* ユーザーは、カメラであり、動作を制御します。 ドライブにできるようにします。
* テキストのためのビルボードを検討してくださいされ帰りシステム world ロックや非表示になる場合、ユーザー、それ以外の場合に移動します。
* 前に新機能については、ユーザーを許可する一方、ユーザーをフォローする必要があるコンテンツの tag-along を使用します。

### <a name="resources"></a>参考資料

#### <a name="documentation"></a>ドキュメント

* [対話デザイン](hologram.md)
* [色、光、および資料](color,-light-and-materials.md)
* [Billboard と Tag-along](billboarding-and-tag-along.md)
* [本能的な操作](interaction-fundamentals.md)
* [自己モーションとユーザー locomotion](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [MR 入力 210:視線入力](holograms-210.md)

## <a name="input-interaction-clarity"></a>入力の相互作用をわかりやすくするため

入力の相互作用をわかりやすくするためは、アプリの有用性に重大な入力の整合性、未成熟、見つけやすさの相互作用の方法が含まれています。 ユーザーは、再確認せずにプラットフォーム全体にわたる一般的な相互作用を使用できる必要があります。 アプリにカスタムの入力がある場合が明確に伝達し、説明する必要があります。

### <a name="device-impact"></a>デバイスへの影響

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  満たす |  失敗 |
--- | --- | ---
|  入力の対話操作のメソッドは提供されている Windows Mixed Reality で一貫性のある[ガイダンス](interaction-fundamentals.md)します。 任意のカスタム入力標準入力 (使用して標準的な対話ではなく) と重複することはできません必要があります明確に伝達およびユーザーに示されています。 | 同様に最適ですがカスタムの入力は、標準入力方式を冗長です。 ユーザーの目標とアプリ エクスペリエンスの進行状況を実現できます。 | 入力メソッドまたはボタンのマッピングを理解するのには困難です。 入力が大きくカスタマイズされて、なしの手順については、標準の入力をサポートしていませんまたは疲労と快適性の問題が発生する可能性があります。 | 

### <a name="how-to-measure"></a>測定する方法

* アプリで使用する一貫性のある[標準入力方式。](interaction-fundamentals.md)
* アプリにカスタムの入力がある場合は、それを明確にを通じてを伝達します。
* 最初の実行エクスペリエンス
* 概要画面
* ヒント
* 手動指導者
* ヘルプ セクション
* ボイス オーバー

### <a name="recommendations"></a>推奨事項

* 可能な限り標準の入力メソッドを使用します。
* 標準以外の入力方法のデモ、チュートリアル、およびツールヒントを提供します。
* アプリ全体で一貫性のある相互作用モデルを使用します。

### <a name="resources"></a>参考資料

#### <a name="documentation"></a>ドキュメント

* [本能的な操作](interaction-fundamentals.md)
* [対話型のオブジェクト](interactable-object.md)
* [ヘッド視線入力とドウェル](gaze-and-dwell.md)
* [カーソル](cursors.md)
* [快適性と視線入力](comfort.md#gaze-direction)
* [ジェスチャ](gestures.md)
* [音声入力](voice-input.md)
* [音声コマンド](voice-design.md)
* [モーション コントローラー](motion-controllers.md)
* [Unity 用入力移植ガイド](input-porting-guide-for-unity.md)
* [Unity でのキーボード入力](keyboard-input-in-unity.md)
* [Unity の視線入力](gaze-in-unity.md)
* [Unity でのジェスチャとモーション コントローラー](gestures-and-motion-controllers-in-unity.md)
* [Unity の音声入力](voice-input-in-unity.md)
* [DirectX でのキーボード、マウス、およびコントローラー入力](keyboard,-mouse,-and-controller-input-in-directx.md)
* [DirectX でのヘッド視線入力とアイ視線入力](gaze-in-directx.md)
* [DirectX での手とモーション コントローラー](hands-and-motion-controllers-in-directx.md)
* [DirectX の音声入力](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [ケース スタディ:複数のパーソナル コンピューティングのフォロー アップ](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [調査をキャストします。HoloStudio UI との対話デザインの学習内容](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [サンプル アプリ:要素の定期処理テーブル](periodic-table-of-the-elements.md)
* [サンプル アプリ:旧暦モジュール](lunar-module.md)
* [MR 入力 210:視線入力](holograms-210.md)
* [MR 入力 211:ジェスチャ](holograms-211.md)
* [MR 入力 212:音声](holograms-212.md)

## <a name="interactable-objects"></a>対話型のオブジェクト

ボタンには、2 D 抽象世界でイベントをトリガーに使用されるメタファが長年です。 3 次元の複合現実の世界では、この抽象化はもはやの世界に限定しました必要はありません。 イベントをトリガーする対話型のオブジェクトを何も指定できます。 対話型のオブジェクトは、そのテーブルに、コーヒー カップから空中に浮かんでバルーンをものとして表現できます。 形式に関係なく対話型のオブジェクトを視覚的およびオーディオをユーザーが明確に認識できる必要があります。

### <a name="device-impact"></a>デバイスへの影響

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  満たす |  失敗 |
--- | --- | ---
|  3 つの状態の間で視覚的およびオーディオを認識できるものは対話型のオブジェクト、形式に関係なく: アイドル状態をターゲットとして、選択します。 「に言ってを参照してください」がオフで、一貫した使用エクスペリエンスのあらゆる場所。 オブジェクトは拡大縮小され、エラーを対象とする無料のために分散します。 | ユーザーできますオーディオまたはビデオのフィードバックを通じた対話型としてオブジェクトを認識およびできますターゲットし、オブジェクトをアクティブ化します。 | ビジュアルやオーディオ キューを指定しない場合は、ユーザーは対話型のオブジェクトを認識できません。 相互作用は、間違いやすくオブジェクト スケールまたはオブジェクト間の距離が原因です。 | 

### <a name="how-to-measure"></a>測定する方法

* 対話型のオブジェクトが '対話型'; として認識できます。特定のボタン、メニューのおよびアプリのコンテンツを含むです。 経験則として必要がありますビジュアルおよびオーディオ キュー対話型のオブジェクトを対象とする場合。

### <a name="recommendations"></a>推奨事項

* 相互作用のビジュアルおよびオーディオのフィードバックを使用します。
* それぞれの入力 (アイドル状態、対象となる、選択した) の状態の視覚的なフィードバックを区別する必要があります。
* 対話型のオブジェクトを拡張し、エラーを対象とする無料の配置する必要があります。
* (メニュー バーやリスト) グループ化された対話型のオブジェクトには、適切な間隔を対象とする必要があります。
* 音声コマンドをサポートするボタンとメニューは、キーワードのコマンドのテキスト ラベルを指定する必要があります (「表示, に言って」)

### <a name="resources"></a>参考資料

#### <a name="documentation"></a>ドキュメント

* [対話可能なオブジェクト](interactable-object.md)
* [Unity のテキスト](text-in-unity.md)
* [アプリ バーと境界ボックス](app-bar-and-bounding-box.md)
* [音声コマンド](voice-design.md)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [Mixed Reality Toolkit - UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>ルームのスキャン

空間マッピング データを必要とするアプリでは、時間の経過と共に自動的にこのデータを収集するデバイスに依存しており、ユーザーとセッション間でアクティブなデバイスでの環境について説明します。 完全を期すため、このデータの品質は、さまざまなユーザーが行った探索の量、探索からどれ時間だけが経過や、デバイス、領域をスキャンするので家具や扉などのオブジェクトが移動するかどうかなどの要因に依存します。 多くのアプリでは、ユーザーが、完全を期すためと、空間のマップの品質を向上させるために追加の手順を実行する必要があるかどうかを判断するエクスペリエンスの先頭に空間マッピング データを分析します。 場合は、ユーザーが、スキャン時にガイダンスが提供される必要があります明確、環境をスキャンするために必要です。

### <a name="device-impact"></a>デバイスへの影響

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  満たす |  失敗 |
--- | --- | ---
|  空間メッシュの視覚化は、ユーザーのスキャンが進行中に伝えます。 ユーザーは、対処方法と、スキャンが開始し、停止に明確に認識しています。 | 空間のメッシュの視覚エフェクトが提供されますが、ユーザーが明確に対処できないを行うと進行状況に関する情報は提供されません。 | メッシュの視覚表現はありません。 ガイダンスの情報を探すには、where 句またはときに、スキャンを開始または停止についてユーザーに提供します。 |

### <a name="how-to-measure"></a>測定する方法

* 必要なルーム スキャン中に、検索する場所を開始して停止のスキャンを示すビジュアルおよびオーディオのガイダンスが提供されます。

### <a name="recommendations"></a>推奨事項

* エクスペリエンスの一部である必要があるユーザーの近くの合計ボリュームの量を指定します。
* スキャンが開始され、進行状況インジケーターなどを停止すると通信します。
* スキャン中に、メッシュの視覚エフェクトを使用します。
* 検索し、ルーム内を移動するユーザーを促すビジュアルおよびオーディオの手掛かりを提供します。
* データを向上させるために移動する場所をユーザーに通知します。 多くの場合に必要な内容の操作を行います (例: を見て、ceiling 見て家具の背後にある)、ユーザーに伝えるための最適な場合があります、スキャンのために必要な品質を取得するためにします。

### <a name="resources"></a>参考資料

#### <a name="documentation"></a>ドキュメント

* [部屋のスキャンの可視化](room-scan-visualization.md)
* [ケース スタディ:HoloLens の空間のマッピング機能を展開します。](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [ケース スタディ:空間 HoloTour の設計](case-study-spatial-sound-design-for-holotour.md)
* [ケース スタディ:フラグメントで魅力的なエクスペリエンスを作成します。](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [Mixed Reality Toolkit - UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>方向インジケーター

Mixed reality アプリでは、コンテンツは、ビューのフィールドの外側にありますか、現実世界のオブジェクトによってオクルー ジョンします。 適切に設計されたアプリは簡単に表示されているコンテンツを検索するユーザー。 方向インジケーターは、重要なコンテンツをユーザーに警告し、ユーザーの位置を基準としたコンテンツへのガイダンスを提供します。 非表示のコンテンツへのガイダンスには、サウンドのエミッタ、方向矢印、または直接の視覚的な手掛かりのフォームを実行できます。

### <a name="device-impact"></a>デバイスへの影響

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  満たす |  失敗 |
--- | --- | ---
|  ビジュアルおよびオーディオ キューは、ビューのフィールドの外側の関連するコンテンツに直接ユーザーを説明します。 | 矢印またはコンテンツの全体的な方向性で、ユーザーを示すいくつかのインジケーター。 | 関連するコンテンツが視野、外部と低いか、ユーザーに場所のガイダンスは提供されません。 | 

### <a name="how-to-measure"></a>測定する方法

* ビューのユーザー フィールドの外部で関連するコンテンツでは、ビジュアルおよびオーディオ キューを検出します。

### <a name="recommendations"></a>推奨事項

* 関連するコンテンツは、外部のユーザーのフィールドの表示が、コンテンツにユーザーをガイドするのに方向インジケーターとオーディオ キューを使用します。 多くの場合、直接 visual ガイドことをお勧め方向矢印にします。
* 方向インジケーターは、カーソルに組み込まないようにする必要があります。

### <a name="resources"></a>参考資料

* [ホログラフィック フレーム](holographic-frame.md)

## <a name="data-loading"></a>データの読み込み

プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。 ユーザーは、進行状況インジケーターが表示されると、待機時間はどれくらいの時間ありますを示すことも、アプリで操作できないことを意味します。

### <a name="device-impact"></a>デバイスへの影響

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  満たす |  失敗 |
--- | --- | ---
|  進行状況バーや任意のデータの読み込みまたは処理中に進行状況を示すリングの形式で、視覚的なインジケーターをアニメーション化します。 視覚インジケータは、どのくらいの時間待機する可能性がありますにガイダンスを提供します。 | データの読み込みが進行中ではどのくらいの時間、待機できることを示す値はありませんが、ユーザーが通知されます。 | データの読み込みまたはプロセスのインジケーターを 5 秒以上かかったタスクがありません。 |

### <a name="how-to-measure"></a>測定する方法

* データの読み込み中には、5 秒以上の空の状態はありませんを確認します。

### <a name="recommendations"></a>推奨事項

* ユーザーがこのアプリが停止しているか、クラッシュするを感じる可能性がある場合に、どのような状況で進行状況を示すデータ読み込み animator を提供します。 妥当な経験則は、'ロード' アクティビティで 5 秒以上かかる場合があります。

### <a name="resources"></a>参考資料

* [進行状況を表示する](progress.md)
