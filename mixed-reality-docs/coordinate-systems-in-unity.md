---
title: Unity の座標系
description: ルーム スケールと世界規模では、Unity での実際のエクスペリエンスを混在、取り付けられていない、お待ちを構築する方法を学習します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 座標系、空間座標系、方向専用、取り付けられているスケール、永続的なスケール、ルーム規模、世界規模、360 度は、取り付け、継続、ルーム、世界、スケール、位置、向き、Unity、アンカー、空間アンカー、世界にロックされている、世界のアンカー世界、ロックや本文-ロックされている本文のロック、損失、locatability、境界、戻しますの追跡
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605051"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="b8780-104">Unity の座標系</span><span class="sxs-lookup"><span data-stu-id="b8780-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="b8780-105">Windows Mixed Reality において広い範囲のアプリをサポートする[スケールが発生する](coordinate-systems.md)、ルーム スケール アプリを使用する方向専用、および取り付けられているスケールのアプリから。</span><span class="sxs-lookup"><span data-stu-id="b8780-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="b8780-106">HoloLens では、さらにおよび、フロアの建物や他の製品全体の探索にユーザーが 5 の m を超える説明できる世界規模のアプリをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="b8780-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="b8780-107">Unity での複合現実エクスペリエンスを構築する最初の手順を判断するためには[スケールが発生する](coordinate-systems.md)アプリが対象です。</span><span class="sxs-lookup"><span data-stu-id="b8780-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="b8780-108">方向専用、または取り付けられているスケールのエクスペリエンスの構築</span><span class="sxs-lookup"><span data-stu-id="b8780-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="b8780-109">\**名前空間:\*\*\*UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="b8780-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b8780-110">\**種類:\*\*\*XRDevice*</span><span class="sxs-lookup"><span data-stu-id="b8780-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="b8780-111">構築する、**向き専用**または**取り付けられているスケール エクスペリエンス**領域の種類を追跡、定常に Unity を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8780-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="b8780-112">追跡するために Unity のワールド座標系を設定、[フレームの静止した基準](coordinate-systems.md#spatial-coordinate-systems)します。</span><span class="sxs-lookup"><span data-stu-id="b8780-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="b8780-113">カメラの既定の場所の前に、エディターで、静止した追跡モードでコンテンツが配置されます (フォワードは ~ Z)、アプリの起動時にも、ユーザーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8780-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="b8780-114">\**名前空間:\*\*\*UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="b8780-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b8780-115">\**種類:\*\*\*InputTracking*</span><span class="sxs-lookup"><span data-stu-id="b8780-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="b8780-116">純粋な**方向のみのエクスペリエンス**(場所ヘッド位置指定の更新プログラムは支障をきたすように見えます)、360 度のビデオ ビューアーなどを設定できます[XR します。InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html)を true にします。</span><span class="sxs-lookup"><span data-stu-id="b8780-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="b8780-117">**取り付けられているスケール エクスペリエンス**、ユーザーに後で戻します取り付けられていない配信元を呼び出すことができます、 [XR します。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)メソッド。</span><span class="sxs-lookup"><span data-stu-id="b8780-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="b8780-118">永続的なスケールやルーム スケール エクスペリエンスの構築</span><span class="sxs-lookup"><span data-stu-id="b8780-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="b8780-119">\**名前空間:\*\*\*UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="b8780-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b8780-120">\**種類:\*\*\*XRDevice*</span><span class="sxs-lookup"><span data-stu-id="b8780-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="b8780-121">**継続スケール**または**ルーム スケール エクスペリエンス**フロアの基準としたコンテンツを配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8780-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="b8780-122">ユーザーの理解を使用して floor、 **[空間ステージ](coordinate-systems.md#spatial-coordinate-systems)**、現場レベルの配信元と省略可能な領域の境界を表す、ユーザーの定義、初回実行時に設定します。</span><span class="sxs-lookup"><span data-stu-id="b8780-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="b8780-123">Floor レベルでの世界の座標系と Unity が動作しているためには、領域の種類を追跡 RoomScale に Unity を設定およびセットが成功したことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b8780-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* <span data-ttu-id="b8780-124">Unity が追跡するために、世界の座標系を正常に切り替え SetTrackingSpaceType が true を返す場合、[ステージ座標系](coordinate-systems.md#spatial-coordinate-systems)します。</span><span class="sxs-lookup"><span data-stu-id="b8780-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="b8780-125">SetTrackingSpaceType false を返す場合、Unity は床面にも、環境内でのユーザーが設定されていないため、ステージの基準枠、可能性の高いに切り替えるにはできませんでした。</span><span class="sxs-lookup"><span data-stu-id="b8780-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="b8780-126">これは一般的ではありませんが、ステージが別の部屋に設定し、ユーザーの新しいステージを設定せず、現在の部屋にデバイスが移動された場合に発生することができます。</span><span class="sxs-lookup"><span data-stu-id="b8780-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="b8780-127">アプリが正常に RoomScale の空間型で、y に、コンテンツの追跡を設定すると、0、床の上にプレーンが表示されますを = です。</span><span class="sxs-lookup"><span data-stu-id="b8780-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="b8780-128">原点 (0, 0, 0) は、特定の場所 - セットアップ時に直面していましたが、順方向を表す Z で部屋のセットアップ中に、ユーザー縦位置、床の上になります。</span><span class="sxs-lookup"><span data-stu-id="b8780-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="b8780-129">\**名前空間:\*\*\*UnityEngine.Experimental.XR*</span><span class="sxs-lookup"><span data-stu-id="b8780-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="b8780-130">\**種類:\*\*\*境界*</span><span class="sxs-lookup"><span data-stu-id="b8780-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="b8780-131">スクリプトのコードでできますを TryGetGeometry メソッドを呼び出している、境界の多角形を取得する UnityEngine.Experimental.XR.Boundary 型 TrackedArea の境界の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="b8780-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="b8780-132">ユーザーに (戻る頂点のリスト) の境界が定義されている場合、配信するには、安全ではわかって、**ルーム スケール エクスペリエンス**をユーザーに場所がシーンを中心ご説明を作成します。</span><span class="sxs-lookup"><span data-stu-id="b8780-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="b8780-133">エントリのユーザーがそれに近づくと、システムは境界がレンダリングに自動的に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b8780-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="b8780-134">アプリは、それ自体の境界を表示するためにこの多角形を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b8780-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="b8780-135">ただし、この境界の多角形を使用して、ユーザーが teleporting せず、それらのオブジェクトを物理的に到達することを確認する、シーン オブジェクトをレイアウトすることができます。</span><span class="sxs-lookup"><span data-stu-id="b8780-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="b8780-136">世界規模のエクスペリエンスの構築</span><span class="sxs-lookup"><span data-stu-id="b8780-136">Building a world-scale experience</span></span>

<span data-ttu-id="b8780-137">\**名前空間:\*\*\*UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="b8780-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="b8780-138">\**種類:\*\*\*WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="b8780-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="b8780-139">True の**世界規模で**ユーザーが 5 m を超える歩き回り HoloLens、ルーム スケール エクスペリエンスのために使用するもの以外の新しい手法必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8780-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="b8780-140">1 つの主要なテクニックを使用して、作成する、[空間アンカー](coordinate-systems.md#spatial-anchors)ホログラム正確には、ユーザーのローミング距離に関係なく、物理世界の場所でのクラスターをロックし[後でもう一度これらホログラムを見つけるセッション](coordinate-systems.md#spatial-anchor-persistence)します。</span><span class="sxs-lookup"><span data-stu-id="b8780-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="b8780-141">Unity では、追加することで、空間アンカーを作成する、 **WorldAnchor**を GameObject に Unity コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="b8780-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="b8780-142">世界のアンカーを追加します。</span><span class="sxs-lookup"><span data-stu-id="b8780-142">Adding a World Anchor</span></span>

<span data-ttu-id="b8780-143">世界のアンカーを追加するには、呼び出す AddComponent<WorldAnchor>現実の世界で固定する変換を使用して、ゲーム オブジェクトに ()。</span><span class="sxs-lookup"><span data-stu-id="b8780-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="b8780-144">以上で作業は終了です。</span><span class="sxs-lookup"><span data-stu-id="b8780-144">That's it!</span></span> <span data-ttu-id="b8780-145">このゲーム オブジェクトが、物理世界の現在の場所に固定されるようになりました - その物理的な整合性を確認します時間の経過と共に若干調整の Unity ワールド座標が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8780-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="b8780-146">使用[永続化](persistence-in-unity.md)これを特定するには、今後、アプリのセッションでもう一度の場所を固定します。</span><span class="sxs-lookup"><span data-stu-id="b8780-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="b8780-147">世界のアンカーを削除します。</span><span class="sxs-lookup"><span data-stu-id="b8780-147">Removing a World Anchor</span></span>

<span data-ttu-id="b8780-148">場合は不要になった、GameObject を現実世界の場所にロックして、このフレームを移動することを意図せず、世界のアンカー コンポーネントで破棄だけ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b8780-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="b8780-149">このフレームの GameObject を移動する場合は、DestroyImmediate を呼び出す代わりにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8780-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="b8780-150">GameObject を固定する世界を移動</span><span class="sxs-lookup"><span data-stu-id="b8780-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="b8780-151">GameObject は、世界アンカーが中に移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="b8780-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="b8780-152">このフレームの GameObject を移動する必要がある場合は、する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8780-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="b8780-153">DestroyImmediate World アンカー コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b8780-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="b8780-154">GameObject を移動します。</span><span class="sxs-lookup"><span data-stu-id="b8780-154">Move the GameObject</span></span>
3. <span data-ttu-id="b8780-155">新しい世界アンカー コンポーネントを GameObject に追加します。</span><span class="sxs-lookup"><span data-stu-id="b8780-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="b8780-156">Locatability 変更の処理</span><span class="sxs-lookup"><span data-stu-id="b8780-156">Handling Locatability Changes</span></span>

<span data-ttu-id="b8780-157">WorldAnchor にない可能性が場所を特定できる時点で、物理世界の時間。</span><span class="sxs-lookup"><span data-stu-id="b8780-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="b8780-158">発生する場合は、Unity が固定オブジェクトの変換を更新していませんが。</span><span class="sxs-lookup"><span data-stu-id="b8780-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="b8780-159">これは、変更することも、アプリの実行中にします。</span><span class="sxs-lookup"><span data-stu-id="b8780-159">This also can change while an app is running.</span></span> <span data-ttu-id="b8780-160">Locatability で変更の処理に失敗する、世界中で適切な物理的な場所に表示されないオブジェクトになります。</span><span class="sxs-lookup"><span data-stu-id="b8780-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="b8780-161">Locatability 変更通知を受けます。</span><span class="sxs-lookup"><span data-stu-id="b8780-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="b8780-162">OnTrackingChanged イベントをサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="b8780-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="b8780-163">イベントを処理します</span><span class="sxs-lookup"><span data-stu-id="b8780-163">Handle the event</span></span>

<span data-ttu-id="b8780-164">**OnTrackingChanged**イベントが基になる空間アンカーがされていない場所を特定できると場所を特定できる中の状態の間で変更されるたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b8780-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="b8780-165">そのイベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="b8780-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="b8780-166">場合によってアンカーは、すぐにあります。</span><span class="sxs-lookup"><span data-stu-id="b8780-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="b8780-167">アンカーの場合は、このいけませんプロパティを設定する場合に true の例では、AddComponent<WorldAnchor>() を返します。</span><span class="sxs-lookup"><span data-stu-id="b8780-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="b8780-168">その結果、OnTrackingChanged イベントはトリガーされません。</span><span class="sxs-lookup"><span data-stu-id="b8780-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="b8780-169">クリーンなパターンは、アンカーをアタッチした後はいけませんの初期状態で OnTrackingChanged ハンドラーを呼び出してになります。</span><span class="sxs-lookup"><span data-stu-id="b8780-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="b8780-170">アンカーのデバイス間で共有</span><span class="sxs-lookup"><span data-stu-id="b8780-170">Sharing anchors across devices</span></span>

<span data-ttu-id="b8780-171">使用することができます<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>ローカル WorldAnchor、アプリが複数の HoloLens、iOS や Android デバイスで見つけることができますし、これから、持続性のあるクラウド アンカーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b8780-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="b8780-172">各ユーザーは複数のデバイスで共通の空間アンカーを共有することで、同じ物理的な場所でそのアンカーの基準としたコンテンツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="b8780-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="b8780-173">これにより、リアルタイムのエクスペリエンスを共有します。</span><span class="sxs-lookup"><span data-stu-id="b8780-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="b8780-174">5 分間試して、Unity での共有エクスペリエンスの構築を開始、<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">空間アンカー Unity の Azure クイック スタート</a>します。</span><span class="sxs-lookup"><span data-stu-id="b8780-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="b8780-175">空間のアンカーを Azure で稼働しているを開発したとして、<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">を作成し、Unity 内でアンカーを検索</a>します。</span><span class="sxs-lookup"><span data-stu-id="b8780-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8780-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8780-176">See Also</span></span>
* [<span data-ttu-id="b8780-177">エクスペリエンスのスケール</span><span class="sxs-lookup"><span data-stu-id="b8780-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="b8780-178">空間ステージ</span><span class="sxs-lookup"><span data-stu-id="b8780-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="b8780-179">損失の Unity での追跡</span><span class="sxs-lookup"><span data-stu-id="b8780-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="b8780-180">空間のアンカー</span><span class="sxs-lookup"><span data-stu-id="b8780-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="b8780-181">Unity で永続化</span><span class="sxs-lookup"><span data-stu-id="b8780-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="b8780-182">Unity での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="b8780-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="b8780-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure の空間アンカー</a></span><span class="sxs-lookup"><span data-stu-id="b8780-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="b8780-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー Unity 用の SDK</a></span><span class="sxs-lookup"><span data-stu-id="b8780-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>