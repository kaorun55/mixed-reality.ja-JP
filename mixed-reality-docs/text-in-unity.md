---
title: Unity 内のテキスト
description: Unity では、テキストを表示するには、2 種類のテキストのコンポーネントを使用することができますが、UI テキストとテキストを 3D メッシュです。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、制御、フォント、文字体裁、ui、ux
ms.openlocfilehash: 45037f27f68a19478fd56a6edc940fbe45ae7671
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326300"
---
# <a name="text-in-unity"></a>Unity 内のテキスト

テキストでは、holographic アプリで最も重要なコンポーネントの 1 つです。 Unity では、テキストを表示するには、2 種類のテキストのコンポーネントを使用することができますが、UI テキストとテキストを 3D メッシュです。 既定では、ぼやけて表示されが大きすぎます。 HoloLens で管理しやすいサイズがシャープな高品質のテキストを取得するいくつかの変数を調整する必要があります。 UI テキストとテキストのメッシュの 3D のコンポーネントを使用する場合は、適切なサイズを取得するスケール ファクターを適用すると、レンダリングの品質が向上を実現できます。

![鋭いと美しいテキストを取得する方法](images/hug-text-02-640px.png)<br>
*Unity でぼやけての既定のテキスト*

## <a name="working-with-fonts-in-unity"></a>Unity でのフォントを操作します。

Unity では、シーンに追加されたすべての新しい要素が 1 の Unity 単位のサイズ、または 100% の変換スケールは、HoloLens に約 1 メートルに変換を前提としています。 場合は、フォント 3D TextMesh の境界ボックスは既定では約 1 メートルの高さ。

![Unity でのフォントを操作します。](images/640px-hug-text-03.png)<br>
*Unity の既定のテキストが占める 1 メートルである 1 の Unity ユニット*

<br>
ほとんどのビジュアル デザイナーは、現実の世界でフォント サイズを定義するのにポイントを使用します。 約 2835 (2,834.645666399962) がある 1 メートルのポイント。 1 m と Unity の既定のテキストのメッシュのフォント サイズ 13 からポイント システムへの変換に基づき、2835 equals 0.0046 (正確に 0.004586111116) で割った値 13 の単純な算術を提供する優れた標準スケールで開始する (一部は、0.005 に丸めるにすることがあります)。 テキスト オブジェクトまたはこれらの値にコンテナーをスケーリングのみを許可しませんフォントの 1 対 1 の変換は、デザイン プログラムのサイズも、アプリケーションやゲーム全体で一貫性を維持するために、標準を提供します。

![別のフォント サイズである unity 3D テキスト メッシュ](images/hug-text-05-1000px.png)<br>
*最適化された値である unity 3D テキスト メッシュ*

<br>
引き続き UI またはキャンバス ベースのテキストの要素をシーンに追加する際にサイズのような違いが大きいです。 2 つのサイズの相違点が約 1000% を 0.00046 (正確に 0.0004586111116) に基づいた UI テキスト コンポーネントのスケール ファクターがもたらされるまたは 0.0005 の丸められた値。

![Unity の UI テキスト単位の値ごとに異なる複数の動的なピクセルを](images/hug-text-04-1000px.png)<br>
*最適化された値を持つ unity UI テキスト*

<br>

>[!NOTE]
>任意のフォントの既定値は、そのフォントまたはフォントが Unity にインポートする方法のテクスチャのサイズによって影響可能性があります。 これらのテストは、Unity では、既定の Arial フォントおよびその他のインポートされた 1 つのフォントにベースで実行されました。

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>適切なディメンションとテキストのレンダリング品質をシャープな

作成しましたこれらスケーリング要因に基づき、 [UI テキストとテキストを 3D メッシュとテキストのプレハブ](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)します。 開発者は、これらプレハブを使用して、シャープなテキストと一貫性のあるフォント サイズを取得することができます。

![適切なディメンションとテキストのレンダリング品質をシャープな](images/hug-text-06-1000px.png)<br>
*適切なディメンションとテキストのレンダリング品質をシャープな*

## <a name="shader-with-occlusion-support"></a>シェーダー オクルー ジョン サポート

Unity の既定のフォントの材料は、オクルー ジョンをサポートしていません。 このため、既定では、オブジェクトの背後にあるテキストが表示されます。 シンプルな付属[、オクルー ジョンをサポートするシェーダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders)します。 次の図は、既定のフォントのマテリアル (左) とテキストと適切なオクルー ジョン (右) を使用してテキストを示します。

![シェーダー オクルー ジョン サポート](images/hug-text-07-1000px.png)<br>
*シェーダー オクルー ジョン サポート*

## <a name="recommended-type-size"></a>推奨される型のサイズ

予想されることができますの 2 m 離れた距離にある非常に小さく、PC またはタブレット デバイス (通常は 12: 32 ポイント) 間を参照してくださいで使用するサイズを入力します。 各フォントの特性によって異なりますが、一般にストローク振動ことがなく読みやすいように推奨される最小の型のサイズは上で導入されたスケール ファクターに基づく 30pt。 アプリは、近い距離に使用することになって、比較的小さなサイズの型を使用できます。 フォントの選択、Segoe UI (Windows の既定のフォント) は、ほとんどの場合でも機能します。 ただし、振動シンの垂直線と読みやすさが低下するために、42 pt 型のサイズの明るい光または半のフォントを使用しないでください。 十分なストロークの太さで最新のフォントがうまく機能します。 たとえば、Helvetica と Arial すばらしい外観になります、通常または太字の重みを持つ、HoloLens で非常に判読可能。

![推奨される型のサイズ](images/hug-text-08-1000px.png)<br>
*種類ごとの傾斜増加の例*

## <a name="see-also"></a>関連項目

* [MixedRealityToolkit でテキストのプレハブ](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)
* [テキストのレイアウトのプレハブのサンプルやシーン](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX/Scenes)
* [文字体裁](typography.md)

 
