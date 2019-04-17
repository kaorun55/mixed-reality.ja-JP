---
title: これで Unity
description: 視線の先は、複合現実でアプリを作成しますホログラムを対象とするユーザーの主な方法です。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 複合現実、視線の先、unity、ホログラム
ms.openlocfilehash: 09915479a9eef95c5ce4533371e113ab6191a331
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604801"
---
# <a name="gaze-in-unity"></a>これで Unity

[視線](gaze.md)対象とするユーザーの主な方法は、[ホログラム](hologram.md)にアプリを作成します[複合現実](mixed-reality.md)します。

## <a name="implementing-gaze"></a>視線の先を実装します。

概念的には、[視線](gaze.md)に接続するの決定は、順方向に、ヘッドセットが、ユーザーのヘッドから光線を投影することによって実装されますと射線が競合する内容。 Unity では、ユーザーのヘッドの位置および方向が、メインの Unity を介して公開される[カメラ](camera-in-unity.md)、特に[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html)と[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)します。

呼び出す[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)で結果を[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)衝突が発生した 3D ポイントなどの競合とその他の GameObject 注視レイに関する情報を格納する構造体競合しています。

### <a name="example-implement-gaze"></a>以下に例を示します。実装の視線入力

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>ベスト プラクティス

上記の例では、視線の先のターゲットを検索する update ループに 1 つ raycast を行う方法を示します、中には、これで gazed されているオブジェクトに関心が可能性のある任意のオブジェクトでこれを行うのではなく視線の先を管理する 1 つのオブジェクトで実行することをお勧めします。 これにより、アプリのフレームごとに 1 つだけの視線の先 raycast を実行して処理を保存できます。

## <a name="visualizing-gaze"></a>視線の先を視覚化します。

実装する必要がありますを使用するマウス ポインターをターゲットと対話するコンテンツを含む、デスクトップと同様、[カーソル](cursors.md)ユーザーの視線の先を表します。 これにより、何で、ユーザーの信頼度と対話しようとしています。

## <a name="gaze-in-mixed-reality-toolkit"></a>これで、Mixed Reality ツールキット
インポートするときに[MRTK が Unity パッケージをリリース](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)からプロジェクトを複製するか、 [GitHub リポジトリ](https://github.com/Microsoft/MixedRealityToolkit-Unity)Unity で新しいメニュー ' Mixed Reality Toolkit' を検索します。 [構成] メニューで、' Mixed Reality シーン設定の適用 ' メニューが表示されます。 既定のカメラを削除し、基本コンポーネントを追加します。 これをクリックすると [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)、 [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)、および[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)します。

![シーンのセットアップの MRTK メニュー](images/MRTK_Input_Menu.png)<br>
*シーンのセットアップの MRTK メニュー*

![MRTK で自動シーンのセットアップ](images/MRTK_HowTo_Input1.png)<br>
*MRTK で自動シーンのセットアップ*

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a>視線 Mixed Reality ツールキットに関連するスクリプト
実際にはツールキットの混合 InputManager プレハブが含まれています[GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs)と[視線の安定板](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs)します。 [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs)、カスタム カーソルを割り当てることができます。 既定では、アニメーション化[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)が割り当てられます。

[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor)と[CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor)カーソルを使用して、視線の先を視覚化する方法を示します。

## <a name="see-also"></a>関連項目
* [カメラ](camera-in-unity.md)
* [視線入力](gaze.md)
* [カーソル](cursors.md)
* [視線の先を対象とします。](gaze-targeting.md)
