---
title: Unity での宝石
description: アプリが混合現実で作成するホログラムをユーザーが対象にする主な方法は、宝石です。
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: 宝石、unity、ホログラム、mixed reality
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453717"
---
# <a name="head-gaze-in-unity"></a>Unity の頭を見つめます

アプリが[混合現実](mixed-reality.md)で作成する[ホログラム](hologram.md)をユーザーが対象にする主な方法は、[宝石](gaze.md)です。


## <a name="implementing-head-gaze"></a>ヘッド見つめの実装

概念的には、ヘッドセットが接続されているユーザーのヘッドから光を投影し、その射線がどのように衝突しているかを判断することによって、[宝石](gaze.md)を実装します。 Unity では、ユーザーの head 位置と方向は、Unity のメイン[カメラ](camera-in-unity.md)(具体的には[unityengine](http://docs.unity3d.com/ScriptReference/Camera-main.html)) を介して公開されます。[transform](http://docs.unity3d.com/ScriptReference/Transform-forward.html)と[Unityengine. Camera. main](http://docs.unity3d.com/ScriptReference/Camera-main.html)を変換します。[transform. position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) を呼び出すと、衝突が発生した3D ポイントや、宝石が競合ししている他のオブジェクトなど、衝突に関する情報を含む [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) 構造体が生成されます。

### <a name="example-implement-head-gaze"></a>例:ヘッド見つめを実装する

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

上の例では、更新ループで1つの raycast を実行して、宝石のターゲットを見つける方法を示していますが、gazed するオブジェクトに関係する可能性のあるオブジェクトではなく、1つのオブジェクトでこの操作を行うことをお勧めします。 これにより、各フレームに1つの raycast を加えるだけで、アプリの処理を保存できます。

## <a name="visualizing-gaze"></a>視覚化 (宝石を)

マウスポインターを使用してコンテンツをターゲットにして操作するデスクトップと同様に、ユーザーの宝石を表す[カーソル](cursors.md)を実装する必要があります。 これにより、ユーザーが操作しようとしている内容に自信を持っています。

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>Mixed Reality Toolkit v2 での宝石
MRTK v2 の[入力マネージャー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)から宝石にアクセスできます。

## <a name="see-also"></a>関連項目
* [カメラ](camera-in-unity.md)
* [見つめ入力](gaze.md)
* [カーソル](cursors.md)
* [視線入力ターゲット設定](gaze-targeting.md)
