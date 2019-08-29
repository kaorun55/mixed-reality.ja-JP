---
title: Unity での宝石
description: アプリが混合現実で作成するホログラムをユーザーが対象にする主な方法は、宝石です。
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: 視線、頭を見つめ、unity、ホログラム、mixed reality
ms.openlocfilehash: 43e643bac00e3c889b14000331d2ed95014fdcc5
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122035"
---
# <a name="head-gaze-in-unity"></a>Unity でのヘッドを見つめます

アプリが[混合現実](mixed-reality.md)で作成する[ホログラム](hologram.md)をユーザーが対象にする主な方法は、[宝石](gaze.md)です。


## <a name="implementing-head-gaze"></a>ヘッド見つめを実装する

概念的には、ヘッド・[宝石](gaze.md)は、ヘッドセットがあるユーザーのヘッドから、接続している前方方向に、射線がどのように衝突しているかを判断することによって実装されます。 Unity では、ユーザーの head 位置と方向は、Unity のメイン[カメラ](camera-in-unity.md)(具体的には[unityengine](http://docs.unity3d.com/ScriptReference/Camera-main.html)) を介して公開されます。[transform](http://docs.unity3d.com/ScriptReference/Transform-forward.html)と[Unityengine. Camera. main](http://docs.unity3d.com/ScriptReference/Camera-main.html)を変換します。[transform. position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

[RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)を呼び出すと、衝突が発生した3d ポイントや、その他の競合しがを使用している他のオブジェクトを含む、衝突に関する情報を含む[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)構造が生成されます。

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

上記の例では、更新ループで1つの raycast を実行して、ユーザーのヘッドポイントの対象を見つける方法を示していますが、オブジェクトに関心を持つ可能性のあるオブジェクトではなく、ヘッドを監視する1つのオブジェクトでこれを行うことをお勧めします。t は gazed していません。 これにより、各フレームに1つのヘッドを raycast するだけで、アプリの処理を保存できます。

## <a name="visualizing-head-gaze"></a>ヘッドを視覚化する

マウスポインターを使用してコンテンツをターゲットにして操作するデスクトップと同様に、ユーザーの顔を示す[カーソル](cursors.md)を実装する必要があります。 これにより、ユーザーが操作しようとしている内容に自信を持っています。

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>Mixed Reality Toolkit v2 でのヘッドを見つめます
MRTK v2 の[入力マネージャー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)から、ヘッドを使用してアクセスできます。

## <a name="see-also"></a>関連項目
* [カメラ](camera-in-unity.md)
* [カーソル](cursors.md)
* [見つめ入力](gaze.md)
* [視線入力ターゲット設定](gaze-targeting.md)
