---
title: Unity での手と視点の追跡
description: Unity、ハンドジェスチャ、およびモーションコントローラーでのアクションを実行するには、2つの主要な方法があります。
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: ジェスチャ、モーションコントローラー、unity、宝石、入力
ms.openlocfilehash: 13016879e47b3b61eb417ce9425e48ea56c1b726
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2019
ms.locfileid: "64580883"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Unity での手と視点の追跡

HoloLens 2 では、新しい魅力的な機能を導入しました。

Unity の新機能を利用する最も簡単な方法は、MRTK v2 を使用することです。 また、使用を開始する際に役立ついくつかのシーンもあります。 

* [MRTK v2 での手による作業の開始](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSystem/HandTracking.html)
* [MRTK v2 での視線追跡の概要](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)


# <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>MRTK v2 での手や目などをサポートするビルディングブロック

MRTK v2 には、開発を高速化するために役立つ一連の UI コントロールと構成要素が用意されています。 

|  [![ボタン](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) [ボタン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | 境界ボックスの[境界ボックス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) [ ![](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) | 操作ハンドラーの[操作ハンドラー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) [ ![](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| HoloLens2's を含むさまざまな入力メソッドをサポートするボタンコントロール | 3D 空間内のオブジェクトを操作するための標準 UI | 1人または2人の手でオブジェクトを操作するためのスクリプト |
|  [![スレート](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) [スレート](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | システムキーボードの[システムキーボード](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) [ ![](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | [![対話型](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) [対話型](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| 入力によるスクロールをサポートする2D スタイルプレーン | Unity でシステムキーボードを使用するサンプルスクリプト  | 視覚的な状態とテーマのサポートを使用してオブジェクトを対話型するためのスクリプト |
|  [![ソルバー](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) [ソルバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | オブジェクトコレクション[オブジェクトコレクション](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) [ ![](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | ツールヒントの[ツールヒント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) [ ![](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| タグに沿って、本文ロック、定数ビューサイズ、表面吸着などのさまざまなオブジェクトの配置動作 | 3次元図形内のオブジェクトの配列をレイアウトするためのスクリプト | モーションコントローラーとオブジェクトのラベル付けに使用できる柔軟なアンカー/ピボットシステムを使用した注釈 UI。 |
|  アプリバー[アプリバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) [ ![](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [![ポインター](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) [ポインター](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) | 指先ビジュアライゼーション指先の[視覚化](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) [ ![](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) |
| 境界ボックスの手動アクティブ化の UI | さまざまな種類のポインターについて | 指先での Visual affordance による直接的な相互作用の信頼性の向上 |
|  [![目の追跡:ターゲット選択](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) [の目の追跡:ターゲットの選択](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [![目の追跡:](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) ナビゲーション[の視点の追跡:領域](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [![目の追跡:ヒートマップ](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) [の視点の追跡:ヒートマップ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| 視点、音声、手入力を組み合わせてシーン全体のホログラムをすばやく簡単に選択する | 表示内容に基づいて、テキストを自動的にスクロールするか、フォーカスされているコンテンツにズームする方法について説明します。| アプリに表示されているユーザーのログ記録、読み込み、視覚化の例 |

# <a name="example-scenes"></a>シーンの例
[このシーンの例](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)では、MRTK のさまざまな種類の相互作用と UI コントロールについて説明します。

その他の例については、「 **Assets/MixedRealityToolkit/デモ**フォルダー」にある[Mixed Reality Toolkit GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)を参照してください。

[![シーンの例](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="see-also"></a>関連項目

* [ジェスチャ](gestures.md)
* [モーション コントローラー](motion-controllers.md)
* [UnityEngine. XR](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR 追跡](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
