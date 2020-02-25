---
title: Unity の空間サウンド
description: Unity シーン内の特定の3D ポイントから空間サウンドを再生します。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity、空間サウンド、HRTF、部屋サイズ
ms.openlocfilehash: 6720eac30c69ebfcd0f003cf131f60295818d676
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553700"
---
# <a name="spatial-sound-in-unity"></a>Unity の空間サウンド

このページでは、Unity の空間サウンドのリソースにリンクしています。

## <a name="spatializer-options"></a>Spatializer オプション
Mixed reality アプリケーションの Spatializer オプションは次のとおりです。
* *MS HRTF Spatializer*。 Unity は、これを*Windows Mixed Reality*のオプションパッケージの一部として提供します。
  * これは、高コストの ' 単一ソース ' アーキテクチャの CPU 上で実行されます。
  * これは、元の HoloLens アプリケーションとの下位互換性のために用意されています。
* *Microsoft Spatializer*。 これは、 [Microsoft Spatializer GitHub リポジトリ](https://github.com/microsoft/spatialaudio-unity)から入手できます。
  * これは、低コストの ' マルチソース ' アーキテクチャを使用します。
  * HoloLens 2 では、これはハードウェアアクセラレータにオフロードされます。

新しいアプリケーションの場合は、 *Microsoft Spatializer*をお勧めします。

## <a name="enable-spatialization"></a>Spatialization を有効にする

[Unity の NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)を使用して_SpatialAudio_をインストールし、プロジェクトのオーディオ設定で**microsoft Spatializer**を選択します。 次のようになります。
* 階層内のオブジェクトに**オーディオソース**をアタッチする
* **[Enable spatialization]** チェックボックスをオンにします。
* **空間ブレンド**スライダーを ' 1 ' に移動します
* 開発者ワークステーションで空間オーディオが有効になっていることを確認します。 これを有効にするには、タスクバーのボリュームアイコンを右クリックし、[空間サウンド] が "オフ" 以外に設定されていることを確認します。 HoloLens 2 で聞く内容を最適に表示するには、 **[ヘッドホン用 Windows Sonic]** を選択します。

詳細については、次を参照してください。
* [Microsoft spatializer GitHub リポジトリ](https://github.com/microsoft/spatialaudio-unity)
* [Microsoft の spatializer チュートリアル](unity-spatial-audio-ch1.md)
* [Unity のオーディオソースドキュメント](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Unity の spatializer のドキュメント](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>距離ベースの減衰
Unity の既定の距離ベースの減衰には、最小距離は1メーター、最大距離は500メートル、対数のロールアウトがあります。 これらの設定は、シナリオによっては機能する場合があります。また、ソースが急激に増加したり、遅くなったりする場合もあります。 詳細については、次を参照してください。
* 推奨設定のための[混合現実のサウンドデザイン](spatial-sound-design.md)。
* これらの曲線を設定する方法については、 [Unity のオーディオソースドキュメント](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)を参照してください。

## <a name="reverb"></a>ほど
_Microsoft Spatializer_は、既定で Spatializer 効果を無効にします。 Spatialized ソースに対してリバーブとその他の効果を有効にするには:
* 各ソースに**Room 効果の送信レベル**コンポーネントをアタッチする
* 各ソースの送信レベル曲線を調整して、エフェクト処理のためにグラフに返されるオーディオのゲインを制御します。

詳細について[は、spatializer チュートリアルの第5章](unity-spatial-audio-ch5.md)を参照してください。

## <a name="unity-spatial-sound-examples"></a>Unity の空間サウンドの例
Unity の空間サウンドの例については、次を参照してください。
* [MRTK デモ](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Microsoft Spatializer サンプルプロジェクト](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-steps"></a>次のステップ:
* [混合現実におけるサウンドのデザイン](spatial-sound-design.md)
* [Microsoft の spatializer チュートリアル](unity-spatial-audio-ch1.md)

