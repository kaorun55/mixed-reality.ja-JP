---
title: Unity でのカメラ
description: Unity のメイン カメラ用 Windows Mixed Reality 開発を使用して、holographic のレンダリングを実行する方法
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit unity、holographic レンダリング、holographic、没入型、フォーカス ポイント、深度バッファー、方向専用、位置指定、非透過、透過的な場合は、クリップ
ms.openlocfilehash: 8ea5a1f53351faab1b2863a0afac74e958b4b1a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597781"
---
# <a name="camera-in-unity"></a>Unity でのカメラ

Mixed reality ヘッドセットを着用する holographic 世界の中心になります。 Unity[カメラ](http://docs.unity3d.com/Manual/class-Camera.html)コンポーネント ステレオスコ ピック レンダリングは自動的に処理し、は、ヘッドの移動と回転するときに従う、プロジェクトで「仮想現実はサポートされて」"Windows Mixed Reality"で選択されている (デバイスとしてその他の設定 セクションの Windows ストアのプレーヤー設定)。 これは、以前のバージョンの Unity で"Windows Holographic"として表示可能性があります。

ただし、表示品質を最適化して[ホログラム安定性](hologram-stability.md)カメラの設定を以下に説明を設定する必要があります。

>[!NOTE]
>これらの設定は、アプリの各シーンでカメラに適用する必要があります。
>
>既定では、Unity では、新しいシーンを作成するときにカメラのコンポーネントが含まれていますが正しく適用されている以下の設定はありませんが、階層内のメイン カメラ GameObject が格納されます。

## <a name="holographic-vs-immersive-headsets"></a>イマーシブ ヘッドセットとホログラフィック

Unity のカメラのコンポーネントの既定の設定では、現実の世界があるないために、スカイ ボックスのような背景を必要とする従来の 3D アプリケーションです。
* 実行されているときに、 **[イマーシブ ヘッドセット](immersive-headset-hardware-details.md)**、ユーザーに表示される、すべてのものをレンダリングして、したがって、スカイ ボックスを保持する必要あります可能性があります。
* ただしで実行されているときに、 **holographic ヘッドセット**など[HoloLens](hololens-hardware-details.md)、現実の世界がレンダリングすべてカメラの背後に表示されます。 これを行うには、HoloLens、透明色としてレンダリングを黒) の「透過的カメラ背景を設定するスカイ ボックス テクスチャではなく。
    1. 階層ウィンドウで、メイン カメラを選択します。
    2. Inspector パネルで、カメラのコンポーネントを検索し、スカイ ボックスのフラグをクリア ドロップダウンを純色に変更します。
    3. バック グラウンドのカラー ピッカーを選択し、(0, 0、0, 0) に、RGBA 値を変更します。

実行時にチェックしてが、没入型か holographic にヘッドセットかどうかを判断するスクリプト コードを使用する[HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)します。


## <a name="positioning-the-camera"></a>カメラの位置

(X: として、ユーザーの開始位置を想定している場合、アプリのレイアウトに簡単になります0、Y:0、Z:0). Main Camera は、ユーザーの頭の動きを追跡は、ために、Main Camera の開始位置を設定して、ユーザーの開始位置を設定できます。
1. 階層ウィンドウでメイン カメラを選択します。
2. Inspector パネルで、変換コンポーネントを検索し、(x: から位置を変更します。0、Y:1、z:-10) には、(x:0、Y:0、Z:0)

   ![インスペクター ウィンドウの Unity でのカメラ](images/maincamera-350px.png)<br>
   *インスペクター ウィンドウの Unity でのカメラ*

## <a name="clip-planes"></a>クリップ面

コンテンツのレンダリングに近すぎるユーザーできます複合現実で使いやすい。 調整することができます、[近く、はるかにクリップ平面](hologram-stability.md#hologram-render-distances)カメラ コンポーネント。
1. 階層ウィンドウで、メイン カメラを選択します。
2. Inspector パネルで、カメラ コンポーネント クリッピング平面を見つけて.85 0.3 からほぼテキスト ボックスに変更します。 もっと近づきレンダリングされたコンテンツがユーザーの不安につながるとあたりしないで、[距離のガイドラインをレンダリング](hologram-stability.md#hologram-render-distances)。

## <a name="multiple-cameras"></a>複数のカメラ

シーンでカメラの複数のコンポーネントがある場合は、Unity ステレオスコ ピックのレンダリングに使用するには、どのカメラを知っているし、どの GameObject をチェックしてヘッドの追跡が MainCamera タグ。

## <a name="recentering-a-seated-experience"></a>取り付けられていないエクスペリエンス中

構築する場合、[取り付けられているスケール エクスペリエンス](coordinate-systems.md)、呼び出すことによって、ユーザーの現在のヘッドの位置に戻しますの Unity の世界配信元ことができます、 **[XR します。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** メソッド。

## <a name="reprojection-modes"></a>Reprojection モード

HoloLens とイマーシブ ヘッドセットの両方には、各フレームの光子が出力されるときに、ユーザーの実際のヘッドの位置の misprediction の調整を表示するため、アプリが reproject されます。

既定では。

* **イマーシブ ヘッドセット**位置指定 reprojection、アプリは、特定のフレームの深度バッファーを提供する場合、ホログラムの位置と向きの両方で misprediction を調整することを実行します。  深度バッファーが指定されていない場合、システムはキャッシュミス方向にのみ修正します。
* **Holographic ヘッドセット**かどうか、アプリが、深度バッファーを提供するかどうか、HoloLens の位置指定 reprojection は実行するようにします。  レンダリングは、現実の世界で提供される、安定したバック グラウンドではスパースでは多くの場合、位置指定 reprojection は深度バッファー HoloLens のない可能性があります。

作成することがわかっている場合、[方向のみのエクスペリエンス](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)剛体本文-ロックされているコンテンツ (例: 360 度のビデオ コンテンツ) のみで印刷の向きを reprojection モードを明示的に設定できます[HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html)に[HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)します。

## <a name="sharing-your-depth-buffers-with-windows"></a>Windows と、深度バッファーの共有

共有を Windows の各フレームは、アプリ 2 つの要因の 1 つでホログラム安定性、ヘッドセットの種類に基づいて、アプリの深度バッファーのレンダリングしています。
* **イマーシブ ヘッドセット**深度バッファーが指定の位置と向きの両方で misprediction、ホログラムを調整する場合に、位置指定 reprojection を実行できます。
* **Holographic ヘッドセット**HoloLens が自動的に選択されているように、[フォーカス ポイント](focus-point-in-unity.md)深度バッファーが提供されている場合は、最もコンテンツと交差する面に沿ったホログラム安定性を最適化します。

Unity アプリは Windows に深度バッファーを提供するかどうかを設定するには。
1. 移動して**編集** > **プロジェクト設定** > **Player** > **ユニバーサル Windows プラットフォーム タブ**  >  **XR 設定**します。
2. 展開、 **Windows Mixed Reality SDK**項目。
3. オンまたはオフにして、**深度バッファーの共有を有効にする**チェック ボックスをオンします。  これは、アップグレードされた古いプロジェクトに対して既定でこの機能が Unity に追加された、オフになりますのでを作成した新しいプロジェクトで既定でチェックされます。

Windows に深度バッファーを提供することにより、Windows 正確にマップできます、深度バッファー内のピクセルごとの正規化された深度値メートル単位の距離にメイン カメラの Unity で設定したのとほぼ平面を使用している限り、表示品質が向上します。  レンダリングがハンドルの深さをパスした場合、一般的な方法で値おく必要がある一般的にここでは、半透明のレンダリングは、既存透けて表示されるときに、深度バッファーに書き込みを渡しますが色ピクセル混乱することが、reprojection 問題ありません。  レンダリング パスが不正確な深さの値を持つ、最終的な深さピクセルの多くにままがわかっている場合は共有することでオフ"を有効にする深度バッファー"表示品質を向上させる可能性があります。

## <a name="mixed-reality-toolkits-automatic-scenesetup"></a>Mixed Reality Toolkit の自動シーンのセットアップ
インポートするときに[MRTK が Unity パッケージをリリース](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)からプロジェクトを複製するか、 [GitHub リポジトリ](https://github.com/Microsoft/MixedRealityToolkit-Unity)Unity で新しいメニュー ' Mixed Reality Toolkit' を検索します。 [構成] メニューで、' Mixed Reality シーン設定の適用 ' メニューが表示されます。 既定のカメラを削除し、基本コンポーネントを追加します。 これをクリックすると [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)、 [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)、および[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)します。

![シーンのセットアップの MRTK メニュー](images/MRTK_Input_Menu.png)<br>
*シーンのセットアップの MRTK メニュー*

![MRTK で自動シーンのセットアップ](images/MRTK_HowTo_Input1.png)<br>
*MRTK で自動シーンのセットアップ*

## <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera プレハブ
これらのプロジェクト パネルから手動で追加できます。 プレハブとしてこれらのコンポーネントを見つけることができます。 検索する場合に**MixedRealityCamera**、2 つの異なるカメラ プレハブを表示することができます。 違いは、 **MixedRealityCamera**はカメラのみプレハブは、 **MixedRealityCameraParent** Teleportation、モーションなどイマーシブ ヘッドセットの追加のコンポーネントが含まれていますコント ローラーと、境界。

![MRTK でカメラのプレハブ](images/MRTK_HowTo_Input2.png)<br>
*MRTK でカメラのプレハブ*

**MixedRealtyCamera** HoloLens とイマーシブ ヘッドセットの両方をサポートします。 デバイスの種類を検出し、フラグをクリアし、スカイ ボックスなどのプロパティを最適化します。 以下、アニメーション コント ローラー モデルでは、カスタムのカーソルなどをカスタマイズでき、Floor、便利なプロパティの一部を見つけることができます。

![カーソルと床面、モーションのコント ローラーのプロパティ](images/MRTK_HowTo_Input3.png)<br>
*カーソルと床面、モーションのコント ローラーのプロパティ*

## <a name="see-also"></a>関連項目
* [ホログラム安定性](hologram-stability.md)
* [MixedRealityToolkit Main Camera.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
