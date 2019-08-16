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
# <a name="head-gaze-in-unity"></a><span data-ttu-id="0929e-104">Unity の頭を見つめます</span><span class="sxs-lookup"><span data-stu-id="0929e-104">Head gaze in Unity</span></span>

<span data-ttu-id="0929e-105">アプリが[混合現実](mixed-reality.md)で作成する[ホログラム](hologram.md)をユーザーが対象にする主な方法は、[宝石](gaze.md)です。</span><span class="sxs-lookup"><span data-stu-id="0929e-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="0929e-106">ヘッド見つめの実装</span><span class="sxs-lookup"><span data-stu-id="0929e-106">Implementing head gaze</span></span>

<span data-ttu-id="0929e-107">概念的には、ヘッドセットが接続されているユーザーのヘッドから光を投影し、その射線がどのように衝突しているかを判断することによって、[宝石](gaze.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="0929e-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="0929e-108">Unity では、ユーザーの head 位置と方向は、Unity のメイン[カメラ](camera-in-unity.md)(具体的には[unityengine](http://docs.unity3d.com/ScriptReference/Camera-main.html)) を介して公開されます。[transform](http://docs.unity3d.com/ScriptReference/Transform-forward.html)と[Unityengine. Camera. main](http://docs.unity3d.com/ScriptReference/Camera-main.html)を変換します。[transform. position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="0929e-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="0929e-109">[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) を呼び出すと、衝突が発生した3D ポイントや、宝石が競合ししている他のオブジェクトなど、衝突に関する情報を含む [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) 構造体が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0929e-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="0929e-110">例:ヘッド見つめを実装する</span><span class="sxs-lookup"><span data-stu-id="0929e-110">Example: Implement head gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="0929e-111">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="0929e-111">Best Practices</span></span>

<span data-ttu-id="0929e-112">上の例では、更新ループで1つの raycast を実行して、宝石のターゲットを見つける方法を示していますが、gazed するオブジェクトに関係する可能性のあるオブジェクトではなく、1つのオブジェクトでこの操作を行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0929e-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="0929e-113">これにより、各フレームに1つの raycast を加えるだけで、アプリの処理を保存できます。</span><span class="sxs-lookup"><span data-stu-id="0929e-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="0929e-114">視覚化 (宝石を)</span><span class="sxs-lookup"><span data-stu-id="0929e-114">Visualizing Gaze</span></span>

<span data-ttu-id="0929e-115">マウスポインターを使用してコンテンツをターゲットにして操作するデスクトップと同様に、ユーザーの宝石を表す[カーソル](cursors.md)を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0929e-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="0929e-116">これにより、ユーザーが操作しようとしている内容に自信を持っています。</span><span class="sxs-lookup"><span data-stu-id="0929e-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="0929e-117">Mixed Reality Toolkit v2 での宝石</span><span class="sxs-lookup"><span data-stu-id="0929e-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="0929e-118">MRTK v2 の[入力マネージャー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)から宝石にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0929e-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="0929e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0929e-119">See also</span></span>
* [<span data-ttu-id="0929e-120">カメラ</span><span class="sxs-lookup"><span data-stu-id="0929e-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="0929e-121">見つめ入力</span><span class="sxs-lookup"><span data-stu-id="0929e-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="0929e-122">カーソル</span><span class="sxs-lookup"><span data-stu-id="0929e-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="0929e-123">視線入力ターゲット設定</span><span class="sxs-lookup"><span data-stu-id="0929e-123">Gaze targeting</span></span>](gaze-targeting.md)
