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
# <a name="head-gaze-in-unity"></a><span data-ttu-id="442a8-104">Unity で Head 視線入力</span><span class="sxs-lookup"><span data-stu-id="442a8-104">Head gaze in Unity</span></span>

<span data-ttu-id="442a8-105">[視線](gaze.md)対象とするユーザーの主な方法は、[ホログラム](hologram.md)にアプリを作成します[Mixed Reality](mixed-reality.md)します。</span><span class="sxs-lookup"><span data-stu-id="442a8-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="442a8-106">ヘッド視線の先を実装します。</span><span class="sxs-lookup"><span data-stu-id="442a8-106">Implementing head gaze</span></span>

<span data-ttu-id="442a8-107">概念的には、[視線](gaze.md)に接続するの決定は、順方向に、ヘッドセットが、ユーザーのヘッドから光線を投影することによって実装されますと射線が競合する内容。</span><span class="sxs-lookup"><span data-stu-id="442a8-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="442a8-108">Unity では、ユーザーのヘッドの位置および方向が、メインの Unity を介して公開される[カメラ](camera-in-unity.md)、特に[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html)と[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)します。</span><span class="sxs-lookup"><span data-stu-id="442a8-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="442a8-109">呼び出す[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)で結果を[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)衝突が発生した 3D ポイントなどの競合とその他の GameObject 注視レイに関する情報を格納する構造体競合しています。</span><span class="sxs-lookup"><span data-stu-id="442a8-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="442a8-110">以下に例を示します。実装ヘッド視線入力</span><span class="sxs-lookup"><span data-stu-id="442a8-110">Example: Implement head gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="442a8-111">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="442a8-111">Best Practices</span></span>

<span data-ttu-id="442a8-112">上記の例では、視線の先のターゲットを検索する update ループに 1 つ raycast を行う方法を示します、中には、これで gazed されているオブジェクトに関心が可能性のある任意のオブジェクトでこれを行うのではなく視線の先を管理する 1 つのオブジェクトで実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="442a8-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="442a8-113">これにより、アプリのフレームごとに 1 つだけの視線の先 raycast を実行して処理を保存できます。</span><span class="sxs-lookup"><span data-stu-id="442a8-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="442a8-114">視線の先を視覚化します。</span><span class="sxs-lookup"><span data-stu-id="442a8-114">Visualizing Gaze</span></span>

<span data-ttu-id="442a8-115">実装する必要がありますを使用するマウス ポインターをターゲットと対話するコンテンツを含む、デスクトップと同様、[カーソル](cursors.md)ユーザーの視線の先を表します。</span><span class="sxs-lookup"><span data-stu-id="442a8-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="442a8-116">これにより、何で、ユーザーの信頼度と対話しようとしています。</span><span class="sxs-lookup"><span data-stu-id="442a8-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="442a8-117">これで、Mixed Reality Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="442a8-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="442a8-118">視線の先へのアクセス、[入力マネージャー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) MRTK v2 でします。</span><span class="sxs-lookup"><span data-stu-id="442a8-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="442a8-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="442a8-119">See also</span></span>
* [<span data-ttu-id="442a8-120">カメラ</span><span class="sxs-lookup"><span data-stu-id="442a8-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="442a8-121">視線入力</span><span class="sxs-lookup"><span data-stu-id="442a8-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="442a8-122">カーソル</span><span class="sxs-lookup"><span data-stu-id="442a8-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="442a8-123">視線入力ターゲット設定</span><span class="sxs-lookup"><span data-stu-id="442a8-123">Gaze targeting</span></span>](gaze-targeting.md)
