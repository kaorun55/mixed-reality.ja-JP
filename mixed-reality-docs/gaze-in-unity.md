---
title: Unity での宝石
description: アプリが混合現実で作成するホログラムをユーザーが対象にする主な方法は、宝石です。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 視線、頭を見つめ、unity、ホログラム、mixed reality
ms.openlocfilehash: 8222a5199cc1ea35429f21e7490e1eff49fcd1bc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435296"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="6e02d-104">Unity でのヘッドを見つめます</span><span class="sxs-lookup"><span data-stu-id="6e02d-104">Head-gaze in Unity</span></span>

<span data-ttu-id="6e02d-105">アプリが[混合現実](mixed-reality.md)で作成する[ホログラム](hologram.md)をユーザーが対象にする主な方法は、[宝石](gaze-and-commit.md)です。</span><span class="sxs-lookup"><span data-stu-id="6e02d-105">[Gaze](gaze-and-commit.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="6e02d-106">ヘッド見つめを実装する</span><span class="sxs-lookup"><span data-stu-id="6e02d-106">Implementing head-gaze</span></span>

<span data-ttu-id="6e02d-107">概念的には、ヘッド・[宝石](gaze-and-commit.md)は、ヘッドセットがあるユーザーのヘッドから、接続している前方方向に、射線がどのように衝突しているかを判断することによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="6e02d-107">Conceptually, [head-gaze](gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="6e02d-108">Unity では、ユーザーの head 位置と方向は、Unity のメイン[カメラ](camera-in-unity.md)(具体的には[unityengine](https://docs.unity3d.com/ScriptReference/Camera-main.html)) を介して公開されます。[transform](https://docs.unity3d.com/ScriptReference/Transform-forward.html)と[Unityengine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html)を変換します。[transform. position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="6e02d-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="6e02d-109">[RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html)を呼び出すと、衝突が発生した3d ポイントや、その他の競合しがを使用している他のオブジェクトを含む、衝突に関する情報を含む[RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html)構造が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6e02d-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="6e02d-110">例: ヘッドを見つめて実装する</span><span class="sxs-lookup"><span data-stu-id="6e02d-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="6e02d-111">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="6e02d-111">Best practices</span></span>

<span data-ttu-id="6e02d-112">上記の例では、更新ループで1つの raycast を実行して、ユーザーのヘッドポイントの対象を見つける方法を示していますが、オブジェクトに関心を持つ可能性のあるオブジェクトではなく、ヘッドを監視する1つのオブジェクトでこれを行うことをお勧めします。t は gazed していません。</span><span class="sxs-lookup"><span data-stu-id="6e02d-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="6e02d-113">これにより、各フレームに1つのヘッドを raycast するだけで、アプリの処理を保存できます。</span><span class="sxs-lookup"><span data-stu-id="6e02d-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="6e02d-114">ヘッドを視覚化する</span><span class="sxs-lookup"><span data-stu-id="6e02d-114">Visualizing head-gaze</span></span>

<span data-ttu-id="6e02d-115">マウスポインターを使用してコンテンツをターゲットにして操作するデスクトップと同様に、ユーザーの顔を示す[カーソル](cursors.md)を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e02d-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="6e02d-116">これにより、ユーザーが操作しようとしている内容に自信を持っています。</span><span class="sxs-lookup"><span data-stu-id="6e02d-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="6e02d-117">Mixed Reality Toolkit v2 でのヘッドを見つめます</span><span class="sxs-lookup"><span data-stu-id="6e02d-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="6e02d-118">MRTK v2 の[入力マネージャー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)から、ヘッドを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6e02d-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e02d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e02d-119">See also</span></span>
* [<span data-ttu-id="6e02d-120">カメラ</span><span class="sxs-lookup"><span data-stu-id="6e02d-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="6e02d-121">カーソル</span><span class="sxs-lookup"><span data-stu-id="6e02d-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="6e02d-122">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="6e02d-122">Head-gaze and commit</span></span>](gaze-and-commit.md)
