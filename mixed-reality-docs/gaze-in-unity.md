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
# <a name="gaze-in-unity"></a><span data-ttu-id="cb271-104">これで Unity</span><span class="sxs-lookup"><span data-stu-id="cb271-104">Gaze in Unity</span></span>

<span data-ttu-id="cb271-105">[視線](gaze.md)対象とするユーザーの主な方法は、[ホログラム](hologram.md)にアプリを作成します[複合現実](mixed-reality.md)します。</span><span class="sxs-lookup"><span data-stu-id="cb271-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [mixed reality](mixed-reality.md).</span></span>

## <a name="implementing-gaze"></a><span data-ttu-id="cb271-106">視線の先を実装します。</span><span class="sxs-lookup"><span data-stu-id="cb271-106">Implementing Gaze</span></span>

<span data-ttu-id="cb271-107">概念的には、[視線](gaze.md)に接続するの決定は、順方向に、ヘッドセットが、ユーザーのヘッドから光線を投影することによって実装されますと射線が競合する内容。</span><span class="sxs-lookup"><span data-stu-id="cb271-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="cb271-108">Unity では、ユーザーのヘッドの位置および方向が、メインの Unity を介して公開される[カメラ](camera-in-unity.md)、特に[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html)と[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)します。</span><span class="sxs-lookup"><span data-stu-id="cb271-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="cb271-109">呼び出す[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)で結果を[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)衝突が発生した 3D ポイントなどの競合とその他の GameObject 注視レイに関する情報を格納する構造体競合しています。</span><span class="sxs-lookup"><span data-stu-id="cb271-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-gaze"></a><span data-ttu-id="cb271-110">以下に例を示します。実装の視線入力</span><span class="sxs-lookup"><span data-stu-id="cb271-110">Example: Implement Gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="cb271-111">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="cb271-111">Best Practices</span></span>

<span data-ttu-id="cb271-112">上記の例では、視線の先のターゲットを検索する update ループに 1 つ raycast を行う方法を示します、中には、これで gazed されているオブジェクトに関心が可能性のある任意のオブジェクトでこれを行うのではなく視線の先を管理する 1 つのオブジェクトで実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cb271-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="cb271-113">これにより、アプリのフレームごとに 1 つだけの視線の先 raycast を実行して処理を保存できます。</span><span class="sxs-lookup"><span data-stu-id="cb271-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="cb271-114">視線の先を視覚化します。</span><span class="sxs-lookup"><span data-stu-id="cb271-114">Visualizing Gaze</span></span>

<span data-ttu-id="cb271-115">実装する必要がありますを使用するマウス ポインターをターゲットと対話するコンテンツを含む、デスクトップと同様、[カーソル](cursors.md)ユーザーの視線の先を表します。</span><span class="sxs-lookup"><span data-stu-id="cb271-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="cb271-116">これにより、何で、ユーザーの信頼度と対話しようとしています。</span><span class="sxs-lookup"><span data-stu-id="cb271-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit"></a><span data-ttu-id="cb271-117">これで、Mixed Reality ツールキット</span><span class="sxs-lookup"><span data-stu-id="cb271-117">Gaze in Mixed Reality Toolkit</span></span>
<span data-ttu-id="cb271-118">インポートするときに[MRTK が Unity パッケージをリリース](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)からプロジェクトを複製するか、 [GitHub リポジトリ](https://github.com/Microsoft/MixedRealityToolkit-Unity)Unity で新しいメニュー ' Mixed Reality Toolkit' を検索します。</span><span class="sxs-lookup"><span data-stu-id="cb271-118">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="cb271-119">[構成] メニューで、' Mixed Reality シーン設定の適用 ' メニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb271-119">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="cb271-120">既定のカメラを削除し、基本コンポーネントを追加します。 これをクリックすると [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)、 [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)、および[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)します。</span><span class="sxs-lookup"><span data-stu-id="cb271-120">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="cb271-121">![シーンのセットアップの MRTK メニュー](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="cb271-121">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="cb271-122">*シーンのセットアップの MRTK メニュー*</span><span class="sxs-lookup"><span data-stu-id="cb271-122">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="cb271-123">![MRTK で自動シーンのセットアップ](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="cb271-123">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="cb271-124">*MRTK で自動シーンのセットアップ*</span><span class="sxs-lookup"><span data-stu-id="cb271-124">*Automatic scene setup in MRTK*</span></span>

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a><span data-ttu-id="cb271-125">視線 Mixed Reality ツールキットに関連するスクリプト</span><span class="sxs-lookup"><span data-stu-id="cb271-125">Gaze related scripts in Mixed Reality Toolkit</span></span>
<span data-ttu-id="cb271-126">実際にはツールキットの混合 InputManager プレハブが含まれています[GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs)と[視線の安定板](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs)します。</span><span class="sxs-lookup"><span data-stu-id="cb271-126">Mixed Reality Toolkit's InputManager prefab includes [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) and [Gaze Stabilizer](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span></span> <span data-ttu-id="cb271-127">[SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs)、カスタム カーソルを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="cb271-127">Under [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), you can assign your custom Cursor.</span></span> <span data-ttu-id="cb271-128">既定では、アニメーション化[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="cb271-128">In default, animated [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) is assigned.</span></span>

<span data-ttu-id="cb271-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor)と[CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor)カーソルを使用して、視線の先を視覚化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cb271-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) and [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) shows you how to visualize your Gaze using Cursors.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb271-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb271-130">See also</span></span>
* [<span data-ttu-id="cb271-131">カメラ</span><span class="sxs-lookup"><span data-stu-id="cb271-131">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="cb271-132">視線入力</span><span class="sxs-lookup"><span data-stu-id="cb271-132">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="cb271-133">カーソル</span><span class="sxs-lookup"><span data-stu-id="cb271-133">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="cb271-134">視線の先を対象とします。</span><span class="sxs-lookup"><span data-stu-id="cb271-134">Gaze targeting</span></span>](gaze-targeting.md)
