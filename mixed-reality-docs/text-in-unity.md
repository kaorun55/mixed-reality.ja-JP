---
title: Unity 内のテキスト
description: Unity では、テキストを表示するには、2 種類のテキストのコンポーネントを使用することができますが、UI テキストとテキストを 3D メッシュです。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、デザイン、制御、フォント、文字体裁、ui、ux
ms.openlocfilehash: 7d40db2e0571e835e28e444c7921e1a086800936
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829970"
---
# <a name="text-in-unity"></a>Unity 内のテキスト

テキストでは、holographic アプリで最も重要なコンポーネントの 1 つです。 Unity では、テキストを表示するには、3 種類のテキストのコンポーネントを使用することができますが、UI テキスト、テキストを 3D メッシュ、およびテキスト メッシュ Pro します。 既定ではぼやけて表示される UI テキストとテキストを 3D メッシュし、が大きすぎます。 HoloLens で管理しやすいサイズがシャープな高品質のテキストを取得するいくつかの変数を調整する必要があります。 UI テキストとテキストのメッシュの 3D のコンポーネントを使用する場合は、適切なサイズを取得するスケール ファクターを適用すると、レンダリングの品質が向上を実現できます。

![鋭いと美しいテキストを取得する方法](images/hug-text-02-640px.png)<br>
*Unity でぼやけての既定のテキスト*

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a>Unity の 3D テキスト (テキスト メッシュ) と UI テキスト操作

Unity では、シーンに追加されたすべての新しい要素が 1 の Unity 単位のサイズ、または 100% の変換スケールは、HoloLens に約 1 メートルに変換を前提としています。 場合は、フォント 3D TextMesh の境界ボックスは既定では約 1 メートルの高さ。

![Unity でのフォントを操作します。](images/640px-hug-text-03.png)<br>
*既定の Unity 3D テキスト (テキスト メッシュ) が占める 1 メートルである 1 の Unity ユニット*

<br>
ほとんどのビジュアル デザイナーは、現実の世界でフォント サイズを定義するのにポイントを使用します。 約 2835 (2,834.645666399962) がある 1 メートルのポイント。 1 m と Unity の既定のテキストのメッシュのフォント サイズ 13 からポイント システムへの変換に基づき、2835 equals 0.0046 (正確に 0.004586111116) で割った値 13 の単純な算術を提供する優れた標準スケールで開始する (一部は、0.005 に丸めるにすることがあります)。 テキスト オブジェクトまたはこれらの値にコンテナーをスケーリングのみを許可しませんフォントの 1 対 1 の変換は、デザイン プログラムのサイズもお客様のエクスペリエンス全体で一貫性を維持するために、標準を提供します。

![別のフォント サイズである unity 3D テキスト メッシュ](images/Text_In_Unity_Measurements1.png)<br>
*Unity 3D テキストと UI のテキストの値をスケーリング*

![別のフォント サイズである unity 3D テキスト メッシュ](images/hug-text-05-1000px.png)<br>
*最適化された値である unity 3D テキスト メッシュ*

<br>
引き続き UI またはキャンバス ベースのテキストの要素をシーンに追加する際にサイズのような違いが大きいです。 2 つのサイズの相違点が約 1000% を 0.00046 (正確に 0.0004586111116) に基づいた UI テキスト コンポーネントのスケール ファクターがもたらされるまたは 0.0005 の丸められた値。

![Unity の UI テキスト単位の値ごとに異なる複数の動的なピクセルを](images/hug-text-04-1000px.png)<br>
*最適化された値を持つ unity UI テキスト*

<br>

>[!NOTE]
>任意のフォントの既定値は、そのフォントまたはフォントが Unity にインポートする方法のテクスチャのサイズによって影響可能性があります。 これらのテストは、Unity では、既定の Arial フォントおよびその他のインポートされた 1 つのフォントにベースで実行されました。

## <a name="working-with-text-mesh-pro"></a>テキストの操作の Mesh Pro

Unity のテキストをメッシュ Pro で、テキストのレンダリング品質をセキュリティで保護することができます。 使用して、距離に関係なく鮮明なテキストのアウトラインがサポートしている、 [SDF (署名済み距離フィールド)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf)手法です。 UI テキストとテキストを 3D メッシュの上に使用した同じ計算メソッドを使用して、見つかったら従来的なタイポグラフィのポイントを使用する適切なスケーリングの値。 36 のサイズを既定の 3D テキスト メッシュ Pro フォントは、2.5 Unity Unit(2.5m) の境界を示しています、ため、ポイントのサイズを使用するのにスケールの値を 0.005 を使用できます。 既定のサイズの 25 の Unity Unit(25m) の境界が、テキスト メッシュ Pro [UI] メニューの。 これにより 0.0005 のスケーリングの値。

![別のフォント サイズである unity 3D テキスト メッシュ](images/Text_In_Unity_Measurements2.png)<br>
*Unity 3D テキストと UI のテキストの値をスケーリング*

## <a name="recommended-text-size"></a>推奨されるテキストのサイズ
予想されることができますの 2 m 離れた距離にある非常に小さく、PC またはタブレット デバイス (通常は 12: 32 ポイント) 間を参照してくださいで使用するサイズを入力します。 各フォントの特性によって異なりますが、一般に角度と読みやすさのフォントの高さを表示する推奨される最小値は、ユーザー調査研究に基づく 0.35°-0.4°/12.21-13.97mm の周囲にあります。 上で導入されたスケール ファクターで 35 40 pt を以下のです。 

0.45m(45cm) でほぼ相互作用は、読みやすいフォントの最小の表示の角度と高さは 0.4 °-mm 0.5 °/3.14 – 3.9 です。 上で導入されたスケール ファクターでの 9-12 pt です。

![ここまでの相互作用範囲](images/typography-distance-1000px.jpg)
*の近くにあるコンテンツとの相互作用の範囲*

### <a name="the-minimum-legible-font-size"></a>読みやすいフォントの最小サイズ
| 距離 | 表示角度 | テキストの高さ | フォント サイズ |
|---------|---------|---------|---------|
| 45 cm (直接操作までの距離) | 0.4°-0.5° | 3.14 – 3.9 mm | 8.9 – 11.13pt |
| 2 分 | 0.35°-0.4° | 12.21 – 13.97 mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>快適に読みやすいフォント サイズ
| 距離 | 表示角度 | テキストの高さ | フォント サイズ |
|---------|---------|---------|---------|
| 45 cm (直接操作までの距離) | 0.65°-0.8° | 5.1-6.3 mm | 14.47-17.8pt |
| 2 分 | 0.6°-0.75° | 20.9 mm-26.2 | 59.4-74.2pt |

Segoe UI (Windows の既定のフォント) では、ほとんどの場合に適しています。 ただし、振動シンの垂直線と読みやすさが低下するために、小さなサイズでライトまたは半の明るいフォント ファミリを使用しないでください。 十分なストロークの太さで最新のフォントがうまく機能します。 たとえば、Helvetica と Arial すばらしい外観になります、通常または太字の重みを持つ、HoloLens で非常に判読可能。


![角度を表示する](images/Text_In_Unity_ViewingAngle.jpg)
*距離、角度、およびテキストの高さを表示します。*

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>適切なディメンションとテキストのレンダリング品質をシャープな

作成しましたこれらスケーリング要因に基づき、 [UI テキストとテキストを 3D メッシュとテキストのプレハブ](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)します。 開発者は、これらプレハブを使用して、シャープなテキストと一貫性のあるフォント サイズを取得することができます。

![適切なディメンションとテキストのレンダリング品質をシャープな](images/hug-text-06-1000px.png)<br>
*適切なディメンションとテキストのレンダリング品質をシャープな*

## <a name="shader-with-occlusion-support"></a>シェーダー オクルー ジョン サポート

Unity の既定のフォントの材料は、オクルー ジョンをサポートしていません。 このため、既定では、オブジェクトの背後にあるテキストが表示されます。 シンプルな付属[、オクルー ジョンをサポートするシェーダー](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader)します。 次の図は、既定のフォントのマテリアル (左) とテキストと適切なオクルー ジョン (右) を使用してテキストを示します。

![シェーダー オクルー ジョン サポート](images/hug-text-07-1000px.png)<br>
*シェーダー オクルー ジョン サポート*


## <a name="see-also"></a>関連項目
* [MRTK でテキストのプレハブ](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [文字体裁](typography.md)

 
