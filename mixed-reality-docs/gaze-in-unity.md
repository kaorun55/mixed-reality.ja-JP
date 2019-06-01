---
title: これで Unity
description: 視線の先は、複合現実でアプリを作成しますホログラムを対象とするユーザーの主な方法です。
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: 複合現実、視線の先、unity、ホログラム
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453717"
---
# <a name="head-gaze-in-unity"></a>Unity で Head 視線入力

[視線](gaze.md)対象とするユーザーの主な方法は、[ホログラム](hologram.md)にアプリを作成します[Mixed Reality](mixed-reality.md)します。


## <a name="implementing-head-gaze"></a>ヘッド視線の先を実装します。

概念的には、[視線](gaze.md)に接続するの決定は、順方向に、ヘッドセットが、ユーザーのヘッドから光線を投影することによって実装されますと射線が競合する内容。 Unity では、ユーザーのヘッドの位置および方向が、メインの Unity を介して公開される[カメラ](camera-in-unity.md)、特に[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html)と[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)します。

呼び出す[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)で結果を[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)衝突が発生した 3D ポイントなどの競合とその他の GameObject 注視レイに関する情報を格納する構造体競合しています。

### <a name="example-implement-head-gaze"></a>以下に例を示します。実装ヘッド視線入力

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

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>これで、Mixed Reality Toolkit v2
視線の先へのアクセス、[入力マネージャー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) MRTK v2 でします。

## <a name="see-also"></a>関連項目
* [カメラ](camera-in-unity.md)
* [視線入力](gaze.md)
* [カーソル](cursors.md)
* [視線入力ターゲット設定](gaze-targeting.md)
