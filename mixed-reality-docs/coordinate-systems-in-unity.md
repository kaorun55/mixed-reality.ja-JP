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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605051"
---
# <a name="coordinate-systems-in-unity"></a>Unity の座標系

Windows Mixed Reality において広い範囲のアプリをサポートする[スケールが発生する](coordinate-systems.md)、ルーム スケール アプリを使用する方向専用、および取り付けられているスケールのアプリから。 HoloLens では、さらにおよび、フロアの建物や他の製品全体の探索にユーザーが 5 の m を超える説明できる世界規模のアプリをビルドできます。

Unity での複合現実エクスペリエンスを構築する最初の手順を判断するためには[スケールが発生する](coordinate-systems.md)アプリが対象です。

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>方向専用、または取り付けられているスケールのエクスペリエンスの構築

**名前空間:**  *UnityEngine.XR*<br>
**種類:**  *XRDevice*

構築する、**向き専用**または**取り付けられているスケール エクスペリエンス**領域の種類を追跡、定常に Unity を設定する必要があります。 追跡するために Unity のワールド座標系を設定、[フレームの静止した基準](coordinate-systems.md#spatial-coordinate-systems)します。 カメラの既定の場所の前に、エディターで、静止した追跡モードでコンテンツが配置されます (フォワードは ~ Z)、アプリの起動時にも、ユーザーが表示されます。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**名前空間:**  *UnityEngine.XR*<br>
**種類:** *InputTracking*

純粋な**方向のみのエクスペリエンス**(場所ヘッド位置指定の更新プログラムは支障をきたすように見えます)、360 度のビデオ ビューアーなどを設定できます[XR します。InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html)を true にします。

```cs
InputTracking.disablePositionalTracking = true;
```

**取り付けられているスケール エクスペリエンス**、ユーザーに後で戻します取り付けられていない配信元を呼び出すことができます、 [XR します。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)メソッド。

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>永続的なスケールやルーム スケール エクスペリエンスの構築

**名前空間:**  *UnityEngine.XR*<br>
**種類:**  *XRDevice*

**継続スケール**または**ルーム スケール エクスペリエンス**フロアの基準としたコンテンツを配置する必要があります。 ユーザーの理解を使用して floor、 **[空間ステージ](coordinate-systems.md#spatial-coordinate-systems)**、現場レベルの配信元と省略可能な領域の境界を表す、ユーザーの定義、初回実行時に設定します。

Floor レベルでの世界の座標系と Unity が動作しているためには、領域の種類を追跡 RoomScale に Unity を設定およびセットが成功したことを確認できます。

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
* Unity が追跡するために、世界の座標系を正常に切り替え SetTrackingSpaceType が true を返す場合、[ステージ座標系](coordinate-systems.md#spatial-coordinate-systems)します。
* SetTrackingSpaceType false を返す場合、Unity は床面にも、環境内でのユーザーが設定されていないため、ステージの基準枠、可能性の高いに切り替えるにはできませんでした。 これは一般的ではありませんが、ステージが別の部屋に設定し、ユーザーの新しいステージを設定せず、現在の部屋にデバイスが移動された場合に発生することができます。

アプリが正常に RoomScale の空間型で、y に、コンテンツの追跡を設定すると、0、床の上にプレーンが表示されますを = です。 原点 (0, 0, 0) は、特定の場所 - セットアップ時に直面していましたが、順方向を表す Z で部屋のセットアップ中に、ユーザー縦位置、床の上になります。

**名前空間:** *UnityEngine.Experimental.XR*<br>
**種類:** *境界*

スクリプトのコードでできますを TryGetGeometry メソッドを呼び出している、境界の多角形を取得する UnityEngine.Experimental.XR.Boundary 型 TrackedArea の境界の種類を指定します。 ユーザーに (戻る頂点のリスト) の境界が定義されている場合、配信するには、安全ではわかって、**ルーム スケール エクスペリエンス**をユーザーに場所がシーンを中心ご説明を作成します。

エントリのユーザーがそれに近づくと、システムは境界がレンダリングに自動的に注意してください。 アプリは、それ自体の境界を表示するためにこの多角形を使用する必要はありません。 ただし、この境界の多角形を使用して、ユーザーが teleporting せず、それらのオブジェクトを物理的に到達することを確認する、シーン オブジェクトをレイアウトすることができます。

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>世界規模のエクスペリエンスの構築

**名前空間:**  *UnityEngine.XR.WSA*<br>
**種類:** *WorldAnchor*

True の**世界規模で**ユーザーが 5 m を超える歩き回り HoloLens、ルーム スケール エクスペリエンスのために使用するもの以外の新しい手法必要があります。 1 つの主要なテクニックを使用して、作成する、[空間アンカー](coordinate-systems.md#spatial-anchors)ホログラム正確には、ユーザーのローミング距離に関係なく、物理世界の場所でのクラスターをロックし[後でもう一度これらホログラムを見つけるセッション](coordinate-systems.md#spatial-anchor-persistence)します。

Unity では、追加することで、空間アンカーを作成する、 **WorldAnchor**を GameObject に Unity コンポーネント。

### <a name="adding-a-world-anchor"></a>世界のアンカーを追加します。

世界のアンカーを追加するには、呼び出す AddComponent<WorldAnchor>現実の世界で固定する変換を使用して、ゲーム オブジェクトに ()。

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

以上で作業は終了です。 このゲーム オブジェクトが、物理世界の現在の場所に固定されるようになりました - その物理的な整合性を確認します時間の経過と共に若干調整の Unity ワールド座標が表示されます。 使用[永続化](persistence-in-unity.md)これを特定するには、今後、アプリのセッションでもう一度の場所を固定します。

### <a name="removing-a-world-anchor"></a>世界のアンカーを削除します。

場合は不要になった、GameObject を現実世界の場所にロックして、このフレームを移動することを意図せず、世界のアンカー コンポーネントで破棄だけ呼び出すことができます。

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

このフレームの GameObject を移動する場合は、DestroyImmediate を呼び出す代わりにする必要があります。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>GameObject を固定する世界を移動

GameObject は、世界アンカーが中に移動することはできません。 このフレームの GameObject を移動する必要がある場合は、する必要があります。
1. DestroyImmediate World アンカー コンポーネント
2. GameObject を移動します。
3. 新しい世界アンカー コンポーネントを GameObject に追加します。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Locatability 変更の処理

WorldAnchor にない可能性が場所を特定できる時点で、物理世界の時間。 発生する場合は、Unity が固定オブジェクトの変換を更新していませんが。 これは、変更することも、アプリの実行中にします。 Locatability で変更の処理に失敗する、世界中で適切な物理的な場所に表示されないオブジェクトになります。

Locatability 変更通知を受けます。
1. OnTrackingChanged イベントをサブスクライブするには
2. イベントを処理します

**OnTrackingChanged**イベントが基になる空間アンカーがされていない場所を特定できると場所を特定できる中の状態の間で変更されるたびに呼び出されます。

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

そのイベントを処理します。

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

場合によってアンカーは、すぐにあります。 アンカーの場合は、このいけませんプロパティを設定する場合に true の例では、AddComponent<WorldAnchor>() を返します。 その結果、OnTrackingChanged イベントはトリガーされません。 クリーンなパターンは、アンカーをアタッチした後はいけませんの初期状態で OnTrackingChanged ハンドラーを呼び出してになります。

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>アンカーのデバイス間で共有

使用することができます<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>ローカル WorldAnchor、アプリが複数の HoloLens、iOS や Android デバイスで見つけることができますし、これから、持続性のあるクラウド アンカーを作成します。  各ユーザーは複数のデバイスで共通の空間アンカーを共有することで、同じ物理的な場所でそのアンカーの基準としたコンテンツを表示できます。  これにより、リアルタイムのエクスペリエンスを共有します。

5 分間試して、Unity での共有エクスペリエンスの構築を開始、<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">空間アンカー Unity の Azure クイック スタート</a>します。

空間のアンカーを Azure で稼働しているを開発したとして、<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">を作成し、Unity 内でアンカーを検索</a>します。

## <a name="see-also"></a>関連項目
* [エクスペリエンスのスケール](coordinate-systems.md#mixed-reality-experience-scales)
* [空間ステージ](coordinate-systems.md#stage-frame-of-reference)
* [損失の Unity での追跡](tracking-loss-in-unity.md)
* [空間のアンカー](spatial-anchors.md)
* [Unity で永続化](persistence-in-unity.md)
* [Unity での共有エクスペリエンス](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure の空間アンカー</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー Unity 用の SDK</a>