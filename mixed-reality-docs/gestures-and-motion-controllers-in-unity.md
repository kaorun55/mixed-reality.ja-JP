---
title: ジェスチャと Unity のアニメーション コント ローラー
description: Unity、手のジェスチャとアニメーション コント ローラーで、視線の先に対処する 2 つの主要な方法があります。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 視線入力、入力、ジェスチャ、アニメーション コント ローラー、unity
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597654"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>ジェスチャと Unity のアニメーション コント ローラー

アクションを実行する 2 つの主要な方法がある、 [Unity で視線](gaze-in-unity.md)、[ジェスチャを渡す](gestures.md)と[コント ローラーのモーション](motion-controllers.md)します。 空間の入力の両方のソースのデータにアクセスするには Unity で同じ Api を使用します。

Unity は、Windows Mixed Reality、共通の空間の入力データにアクセスする 2 つの主な方法を提供します*Input.GetButton/Input.GetAxis*複数の Unity XR Sdk 間で機能する Api と*InteractionManager/。GestureRecognizer* API の使用可能な空間の入力データの完全なセットを公開する Windows Mixed Reality を特定します。

## <a name="unity-buttonaxis-mapping-table"></a>Unity ボタン/軸マッピング テーブル

次の表に、ボタンと軸の Id には、Windows Mixed Reality モーションのコント ローラーによる用 Unity の入力マネージャーではサポートされて、 *Input.GetButton/GetAxis* Api、「Windows MR 固有」列は、プロパティにはオフの使用可能な*InteractionSourceState*型。 これらの各 Api については、以下のセクションで詳しく説明します。

Windows Mixed Reality をボタン/軸 ID のマッピングには、Oculus ボタン/軸 Id 一般と一致します。

Windows Mixed Reality をボタン/軸 ID のマッピングは、2 つの方法で OpenVR のマッピングによって異なります。
1. マッピングは、サムスティックおよびタッチパッドの両方のコント ローラーをサポートするために個別のサムスティックからいるタッチパッド Id を使用します。
2. マッピングは、A と X ボタン物理 ABXY ボタンの使用可能なもののままにする Id、メニュー ボタンのオーバー ロードを回避できます。

<table>
<tr>
<th rowspan="2">入力 </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">一般的な Unity Api</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR に固有の入力 API</a><br />(ダンプします。WSA します。入力)</th>
</tr><tr>
<th> 左側にあります。 </th><th> 右側にあります。</th>
</tr><tr>
<td> 押された選択のトリガー </td><td> 9 = 1.0 の軸 </td><td> 10 = 1.0 の軸 </td><td> selectPressed</td>
</tr><tr>
<td> トリガーのアナログ値を選択します。 </td><td> 軸 9 </td><td> 軸 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> 部分的に押された選択のトリガー </td><td> ボタンの 14 <i>(ゲームパッド互換性)</i> </td><td> ボタンの 15 <i>(ゲームパッド互換性)</i> </td><td> selectPressedAmount &gt; 0.0</td>
</tr><tr>
<td> 押されたメニュー ボタン </td><td> ボタンの 6 * </td><td> ボタンの 7 * </td><td> menuPressed</td>
</tr><tr>
<td> グリップ ボタンが押されました。 </td><td> 軸 11 = 1.0 (アナログ値なし)<br />ボタン 4 <i>(ゲームパッド互換性)</i> </td><td> 軸 12 = 1.0 (アナログ値なし)<br />ボタン 5 <i>(ゲームパッド互換性)</i> </td><td> 文章</td>
</tr><tr>
<td> スティック X <i>(左:-1.0、適切な。1.0)</i> </td><td> 軸 1 </td><td> 軸 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> スティック Y <i>(top:-1.0、下部にあります。1.0)</i> </td><td> 軸 2 </td><td> 軸 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> 押されたスティック </td><td> ボタンの 8 </td><td> ボタンの 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> タッチパッド X <i>(左:-1.0、適切な。1.0)</i> </td><td> 軸 17 * </td><td> 軸 19 * </td><td> touchpadPosition.x</td>
</tr><tr>
<td> タッチパッド Y <i>(top:-1.0、下部にあります。1.0)</i> </td><td> 軸 18 * </td><td> 軸 20 * </td><td> touchpadPosition.y</td>
</tr><tr>
<td> タッチ タッチパッド </td><td> ボタンの 18 * </td><td> ボタンの 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> 押されたタッチパッド </td><td> ボタンの 16 * </td><td> ボタンの 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6 dof グリップ姿勢またはポインター姿勢 </td><td colspan="2"> <i>グリップ</i>のみ発生します。<a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></td><td> 渡す<i>グリップ</i>または<i>ポインター</i>を引数として: sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> 状態の追跡 </td><td colspan="2"> <i>位置の精度とソース消失のリスクを MR に固有の API を介してのみ使用できます。</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>このボタン/軸 Id は、ゲームパッド、Oculus タッチと OpenVR で使用されるマッピングの競合による OpenVR に Unity を使用する Id によって異なります。

## <a name="grip-pose-vs-pointing-pose"></a>グリップの姿勢ポインティング ポーズとの比較

Windows Mixed Reality は、さまざまなフォーム ファクターでモーションのコント ローラーをサポートしている、各コント ローラーの設計と、ユーザーの手の形の位置とそのアプリの方向を「転送」自然の間の関係の違いポイントを表示するときに使用する必要があります、コント ローラー。

これらのコント ローラーをより適切に表すには、2 種類の各相互作用ソースを調査することができますが発生、**グリップ姿勢**と**ポインター姿勢**します。 グリップ ポーズとポインター姿勢の両方の座標はグローバルの Unity ワールド座標内のすべての Unity Api で表されます。

### <a name="grip-pose"></a>グリップの姿勢

**グリップ姿勢**HoloLens、によって検出された手の形の palm またはアニメーション コント ローラーを保持している片手で行うことのいずれかの場所を表します。

レンダリングに使用最適グリップ姿勢でイマーシブ ヘッドセット、**ユーザーの手**または**オブジェクトは、ユーザーの手の形で保持されている**剣ガンなど、します。 グリップの姿勢は、として、アニメーション コント ローラーを視覚化するときにも使用、**レンダリング可能なモデル**運動の Windows で、コント ローラーは、送信元と回転の中心としてグリップ姿勢を使用して指定します。

グリップ姿勢が具体的には次のように定義されています。
* **位置を握って**:Palm 重心当然ながら、コント ローラーを保持しているときに、左または右中央にグリップ内の位置を調整します。 Windows Mixed Reality アニメーション コント ローラーで、この位置は把握ボタンで一般に揃えて配置します。
* **向きの適切な軸を握って**:5 本の指フラットな姿勢を形成する完全に開くと、射線は、palm に通常 (順方向から左 palm、適切な palm から旧バージョンとの)
* **向きの順方向軸を握って**:部分的に (場合と同様、コント ローラーを保持している) の手の閉じるときに、"forward"チューブを通じて非 thumb 指によって形成されるポイントの半径。
* **軸の向きを握って**:右と前方参照の定義が含まれるアップ軸。

グリップの姿勢をベンダー間入力のいずれかの Unity の API を通じてアクセスできます (*[XR します。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)します。GetLocalPosition/Rotation*) または Windows MR 固有 API (*sourceState.sourcePose.TryGetPosition/Rotation*、データを要求して発生し得る、**グリップ**ノード)。

### <a name="pointer-pose"></a>ポインターの姿勢

**ポインター姿勢**フォワード指し示すコント ローラーの先端を表します。

システム指定のポインターの姿勢はしたら、最適な raycast に使用**コント ローラー モデル自体のレンダリング**します。 仮想の銃など、コント ローラーの代わりにその他の仮想オブジェクトをレンダリングする場合は光線ガンのアプリで定義されたモデルの軸に沿って移動するなど、その仮想オブジェクトの最も自然なレイでポイントする必要があります。 仮想オブジェクトと物理のコント ローラーではないユーザーが表示できるため、仮想オブジェクトでポイントがあります、アプリを使用してこれらのより自然です。

現時点では、ポインターの姿勢は Windows MR 固有の API を介してのみで使用できる*sourceState.sourcePose.TryGetPosition/Rotation*で渡し*InteractionSourceNode.Pointer*として、引数。

## <a name="controller-tracking-state"></a>コント ローラーの状態の追跡

ヘッドセットなど、Windows Mixed Reality モーションのコント ローラーの外部の追跡のセンサーのセットアップは必要ありません。 代わりに、コント ローラーは、ヘッドセット自体のセンサーによって追跡されます。

場合は、ユーザーは、ヘッドセットのビューのフィールドからコント ローラーを移動、ほとんどの場合 Windows 引き続きコント ローラーの位置を推測し、アプリに提供されます。 ときに、コント ローラーの位置を正確度のおおよその位置にドロップは、十分な時間のビジュアルの追跡、コント ローラーを失いました。

この時点では、システムは、本文ロックをコント ローラーをユーザーに、その内部方位センサーを使用して、コント ローラーの場合は true。 向きを引き続き公開中に移動する場合に、ユーザーの位置を追跡します。 ポイントし、UI 要素をアクティブ化するコント ローラーを使用する多くのアプリが、ユーザーのルーティング グループおおよその精度で通常どおり操作できます。

これを理解する最善の方法は、自分で試すです。 さまざまな追跡の状態の間でアニメーション コント ローラーで動作する没入型のコンテンツの例では、このビデオをご覧ください。

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>明示的に状態の追跡についての考え方

位置に応じて異なる状態の追跡を処理するアプリがさらに可能性がありなど、コント ローラーの状態のプロパティを検査*SourceLossRisk*と*PositionAccuracy*:

<table>
<tr>
<th> 状態の追跡 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高精度</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>高精度 (損失の危険)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>おおよその精度</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>位置</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: orange"> false</td>
</tr>
</table>

これらのアニメーション コント ローラー追跡状態の定義は次のとおりです。
* **高精度は:** ヘッドセットのビューのフィールド内のモーション コント ローラーは、中には、高精度の位置、ビジュアルの追跡に基づく一般に提供します。 注移動コント ローラーを一時的にビューのフィールドのままにヘッドセット センサーから一時的に隠されている (などによって、ユーザーの一方) を返すコント ローラーの慣性による追跡に基づく、短時間、高精度ポーズは引き続き自体。
* **(データが失われる危険性) が高精度は:** ユーザーは、過去のヘッドセットの視野の edge モーション コント ローラーを移動したとき、ヘッドセットすぐにできなくコント ローラーの位置を視覚的に追跡するためにします。 アプリが、コント ローラーが達したらこの FOV 境界を見ることによって、 **SourceLossRisk** 1.0 に到達します。 その時点では、アプリは、コント ローラーのジェスチャを非常に高品質なポーズの流れを必要とするを一時停止する選択できます。
* **近似精度は:** ときに、コント ローラーの位置を正確度のおおよその位置にドロップは、十分な時間のビジュアルの追跡、コント ローラーを失いました。 この時点では、システムは、本文ロックをコント ローラーをユーザーに、その内部方位センサーを使用して、コント ローラーの場合は true。 向きを引き続き公開中に移動する場合に、ユーザーの位置を追跡します。 ポイントし、UI 要素をアクティブ化するコント ローラーを使用する多くのアプリは、ユーザーのルーティング グループおおよその精度で通常 while として動作できます。 やや入力要件がアプリからこのドロップを理解することもできます**高**精度**Approximate**精度を調べることによって、 **PositionAccuracy**プロパティのこの期間中に画面外のターゲットについて、ユーザー寛大な hitbox を提供する例です。
* **位置:** コント ローラーは、おおよその精度で長時間動作、中に場合があります、システムを知っていることも、本文ロック位置が意味のある現時点で。 など、コント ローラーだけを有効にする可能性がありますことはありませんされてまたは計測される視覚的に、ユーザーが、他のユーザーによってピックアップされるコント ローラーを設定します。 これらのタイミングで、システムが提供しないアプリに任意の位置と*TryGetPosition*は false を返します。

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>一般的な Unity Api (Input.GetButton/GetAxis)

**名前空間:***UnityEngine*, *UnityEngine.XR*<br>
**型**:*Input*, *XR.InputTracking*

Unity は、現在の [全般] を使用して*Input.GetButton/Input.GetAxis*の入力を公開する Api [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)、 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)と Windows Mixed Reality を含む手およびモーションのコント ローラー。 場合は、アプリでは、これらの Api を使用して、入力、Windows Mixed Reality を含め、複数の XR Sdk 間で簡単にアニメーション コント ローラーをサポートできます。

### <a name="getting-a-logical-buttons-pressed-state"></a>論理のボタンの押下状態の取得

一般的な Unity 入力 Api を使用する通常から始めますボタンと軸での論理名を接続、 [Unity 入力マネージャー](https://docs.unity3d.com/Manual/ConventionalGameInput.html)、ボタンまたは軸の Id をそれぞれの名前にバインドします。 そのボタン/軸の論理名を参照するコードを記述できます。

たとえば、送信アクションを左側のモーション コント ローラーのトリガー ボタンをマップするに移動**編集 > プロジェクトの設定 > 入力**Unity 内で送信セクション 軸のプロパティ を展開します。 変更、**正ボタン**または**Alt 正ボタン**プロパティを読み取る**ジョイスティック ボタン 14**、次のように。

![Unity の InputManager](images/unity-input-manager.png)<br>
*Unity InputManager*

送信アクションを使用して、スクリプトをチェックし、 *Input.GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
変更することより論理的ボタンを追加することができます、**サイズ**のプロパティの **軸**します。

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>直接物理ボタンの押下状態の取得

アクセスすることもボタン手動で、その完全修飾名を使用して*Input.GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>手動またはモーション コント ローラーの姿勢を取得します。

位置と、コント ローラーの回転にアクセスすることができますを使用して*XR します。InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

注 (ユーザーは、コント ローラーを保持) コント ローラーのグリップの姿勢を表すは剣またはユーザーの手の形、またはコント ローラー自体のモデルでガンをレンダリングするために便利です。

このグリップ ポーズと (コント ローラーのヒントを指している) ポインター姿勢間のリレーションシップは、コント ローラー間で異なる場合がありますに注意してください。 この時点で、コント ローラーのポインターの姿勢にアクセスする MR 固有の入力では、以下のセクションで説明されている API を通じて実現できる、のみできます。

## <a name="windows-specific-apis-xrwsainput"></a>Windows 固有の Api (XR します。WSA します。入力)

**名前空間:***UnityEngine.XR.WSA.Input*<br>
**型**:*InteractionManager*、 *InteractionSourceState*、 *InteractionSource*、 *InteractionSourceProperties*、 *InteractionSourceKind*、 *InteractionSourceLocation*

Windows に固有の空間入力 Api を使用して選択できます (HoloLens) 用の Windows Mixed Reality 手入力およびモーションのコント ローラーの詳細情報を取得する、 *UnityEngine.XR.WSA.Input*名前空間。 位置の精度などの追加情報やハンドと離れているコント ローラーに指示することができます、ソースの種類にアクセスできます。

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>手およびモーションのコント ローラーの状態のポーリング

各相互作用ソース (手動またはモーションのコント ローラー) を使用するため、このフレームの状態をポーリングすることができます、 *GetCurrentReading*メソッド。

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

各*InteractionSourceState*取得したバックアップは現在時点での相互作用ソースを表します。 *InteractionSourceState*などの情報を公開します。
* これは、[種類押すの](motion-controllers.md)(選択/メニュー/理解/タッチパッド/スティック) が発生しています。

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* アニメーション コント ローラー、このようなタッチパッド スティックの XY 座標やタッチされた状態に固有の他のデータ

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* かどうか、ソースは、手動またはモーション コント ローラーを把握する InteractionSourceKind

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>順方向予測レンダリング ポーズのポーリング

* ハンドとコント ローラーからの相互作用のソース データのポーリングをするときに取得することはこのフレームの光子は、ユーザーの目に到達時間でしばらくの間、順方向予測ポーズにします。  これらの前方予測ポーズに適して**レンダリング**コント ローラーまたは、保持されているオブジェクトの各フレーム。  指定したキーを押してを対象とするまたはコント ローラーでリリースする場合は、履歴イベントを以下に示す Api を使用する場合、最も正確ながあります。

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* この現在のフレームの前方予測ヘッド姿勢を取得することもできます。  ソース姿勢で、この場合に便利ですが**レンダリング**カーソルを指定したキーを押してやリリースを対象とする履歴イベントを以下に示す Api を使用する場合は、最も正確はできます。

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>相互作用のソース イベントの処理

履歴姿勢の正確なデータが発生したときに、入力イベントを処理するためには、ポーリングではなく相互作用ソース イベントを処理することができます。

相互作用のソースのイベントを処理するには。
* 登録、 *InteractionManager*入力イベント。 興味のある操作イベントの種類ごとには、サブスクライブする必要があります。

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* イベントを処理します。 相互作用のイベントにサブスクライブしていると該当する場合に、コールバックが返されます。 *SourcePressed*例では、これになります、ソースが検出された後、リリースまたは紛失前にします。

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>イベントの処理を停止する方法

イベントに興味のある不要になったか、イベントにサブスクライブしているオブジェクトを破棄するときに、イベントの処理を停止する必要があります。 イベントの処理を停止するには、購読を解除するイベントです。

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>相互作用のソース イベントの一覧

ソース イベントの使用可能な操作は次のとおりです。
* *InteractionSourceDetected* (ソースがアクティブになります)
* *InteractionSourceLost* (非アクティブになります)
* *InteractionSourcePressed* (タップ、ボタンの押下、または"Select"発音)
* *InteractionSourceReleased* (タップして、ボタンが解放された、または"Select"発音の最後の終了)
* *InteractionSourceUpdated* (移動またはいくつかの状態を変更するそれ以外の場合)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>イベント キーを押してまたはリリースを最も正確に一致する履歴の対象とすることを

前に説明したポーリング Api では、順方向予測ポーズ アプリを提供します。  これらの予測が発生は、コント ローラーまたは仮想のハンドヘルド オブジェクトのレンダリングに最適ですが、将来ポーズが対象とする、2 つの主な理由のために最適でないです。
* ユーザーは、コント ローラー上のボタンを押すと、ありますワイヤレスの待機時間の約 20 ミリ秒遅らせます Bluetooth 経由で、システムは、キーを押してを受信する前に。
* 次を使用する場合前方予測の姿勢では、ある前方の予測のもう 1 つの 10-20 ミリ秒に適用される現在のフレームの光子は、ユーザーの目に到達する時間を対象します。

つまり、ポーリングは、ソースの姿勢をまたはヘッドからユーザーの head と手実際にが、キーを押してまたはリリースが発生したときに 30 40 転送が発生します。  HoloLens 手入力する場合、ワイヤレス通信の遅延はありませんは、キーを押してを検出するような処理の遅延です。

手動またはコント ローラーのキーを押してのユーザーの本来の目的に基づいてターゲット正確には、履歴ソース姿勢またはからヘッドの姿勢を使用する必要があります*InteractionSourcePressed*または*InteractionSourceReleased*入力イベント。

対象に、キーを押してまたはユーザーの頭またはそのコント ローラーからデータを履歴姿勢でリリースできます。
* ジェスチャまたはコント ローラーを押したときの時点でヘッド姿勢が発生したために使用できる**を対象とする**、ユーザーが何を確認する[gazing](gaze.md)で。

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* アニメーション コント ローラーを押したときの時点でソース姿勢が発生したために使用できる**を対象とする**をどのようなユーザー指定のコント ローラーを決定します。  これをキーを押してが発生したコント ローラーの状態となります。  コント ローラー自体をレンダリングする場合は、グリップ姿勢で、ユーザーが検討事項のコント ローラーを表示する自然なヒントからターゲット光線を撮影するではなく、ポインターの姿勢を要求できます。

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>イベント ハンドラーの例

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>高度な複合 gesture Api (GestureRecognizer)

**名前空間:***UnityEngine.XR.WSA.Input*<br>
**型**:*GestureRecognizer*、 *GestureSettings*、 *InteractionSourceKind*

アプリは、空間の入力ソース、タップ、保持、操作、およびナビゲーションのジェスチャのより高度な複合ジェスチャを認識することができますも。 両方でこれらの複合ジェスチャを認識できる[手](gestures.md)と[コント ローラーのモーション](motion-controllers.md)GestureRecognizer を使用します。

GestureRecognizer 上の各ジェスチャ イベントは、イベントの時刻に、入力としてターゲット ヘッド レイ、SourceKind を提供します。 いくつかのイベントは、追加のコンテキスト固有の情報を提供します。

ジェスチャ レコグナイザーを使用するジェスチャをキャプチャするために必要ないくつかの手順のみがあります。
1. 新しいジェスチャ レコグナイザーを作成します。
2. ウォッチするジェスチャを指定します。
3. これらのジェスチャのイベントをサブスクライブします。
4. ジェスチャのキャプチャを開始します。

### <a name="create-a-new-gesture-recognizer"></a>新しいジェスチャ レコグナイザーを作成します。

使用する、 *GestureRecognizer*、作成する必要があります、 *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>ウォッチするジェスチャを指定します。

使用して興味があるジェスチャを指定*SetRecognizableGestures()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>これらのジェスチャのイベントをサブスクライブします。

興味のあるジェスチャのイベントをサブスクライブします。

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>移動および操作のジェスチャのインスタンスで相互に排他的な*GestureRecognizer*します。

### <a name="start-capturing-gestures"></a>ジェスチャのキャプチャを開始します。

既定で、 *GestureRecognizer*まで入力を監視しません*StartCapturingGestures()* が呼び出されます。 後に、ジェスチャ イベントを生成することことができます*StopCapturingGestures()* 入力は、フレーム前に実行されている場合に呼び出されますが、 *StopCapturingGestures()* が処理されました。 *GestureRecognizer*と覚えておいてくださいかどうかに、ジェスチャは実際に発生した、previou フレームの間にオンまたはオフをだとためが開始する信頼性の高いを対象とするこのフレームの視線の先に基づくジェスチャの監視を停止します。

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>ジェスチャのキャプチャを停止します。

ジェスチャ認識を停止します。

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>ジェスチャ レコグナイザーを削除します。

破棄する前にサブスクライブされたイベントの登録を解除してください、 *GestureRecognizer*オブジェクト。

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Unity でモーション コント ローラー モデルを表示

![アニメーション コント ローラー モデルと teleportation](images/motioncontrollertest-teleport-1000px.png)<br>
*アニメーション コント ローラー モデルと teleportation*

物理コント ローラーを保持するいると、ユーザーおよびのさまざまなボタンが押されているように明確に一致するアプリでのモーション コントローラを表示するために使用することができます、 **MotionController プレハブ**で、 [Mixed Reality ツールキット](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  このプレハブは、システムのインストールされているアニメーション コント ローラー ドライバーから動的に実行時に正しい glTF モデルを読み込みます。  インポートして手動で、エディターで、アプリは、ユーザーに、現在および将来のコント ローラーの 3D モデルを物理的に正確に表示されるよう必要があるのではなくするこれらのモデルを動的に読み込むことが重要です。

1. に従って、 [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) Mixed Reality Toolkit をダウンロードして、Unity プロジェクトに追加する手順。
2. カメラを交換した場合、 *MixedRealityCameraParent* prefab 概要手順の一環として、する準備が整いました。  そのプレハブには、アニメーション コント ローラーの表示が含まれます。  それ以外の場合、追加*Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab*プロジェクト ウィンドウからシーンにします。  親オブジェクトの子としてプレハブを使用することときに中心にカメラを移動する追加たい、シーン内でユーザー teleports コント ローラーがユーザーと共に取得できるようにします。  アプリが teleporting を伴わない場合、シーンのルートにある、プレハブを追加します。

## <a name="throwing-objects"></a>オブジェクトをスローします。

困難な問題は、仮想現実でのオブジェクトをスローし、最初に見えるかもしれません。 同様に物理的に最もベースの対話、予期しない方法でゲームの動作でスローするときに、それがすぐにわかる immersion を中断します。 物理的に正しいのスロー動作を表し、当社のプラットフォームをお客様と共有したいに更新を有効になっているいくつかのガイドラインを思い付く方法について深く考える時間がいくつかを費やしてきました。

実装をスローすることをお勧めする方法の例が見つかります[ここ](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)します。 このサンプルでは、次の 4 つのガイドラインに従います。
* **コント ローラーを使用して、 *velocity*位置ではなく**します。 Windows の 11 月更新での動作が変更を導入しましたの場合に、 ['およそ ' の位置指定の追跡状態](motion-controllers.md#controller-tracking-state)します。 、この状態のときに速度については、コント ローラーを高い精度で、位置が高精度よりも長くは多くの場合と考えています限りの報告されることを続けます。
* **組み込む、*角速度*コント ローラーの**します。 このロジックはすべてに含まれる、`throwing.cs`ファイル、`GetThrownObjectVelAngVel`上のリンクから、パッケージ内の静的メソッド。
   1. 角度の速度を保護すると、スローされたオブジェクトとしてスローの時点では、同じ角度の速度を維持する必要があります。 `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. スローされたオブジェクトの重心はありませんがグリップ姿勢の原点とが異なる速度、コント ローラーのユーザーの参照のフレームで可能性があります。 この方法で提供されたオブジェクトの速度の部分では、コント ローラーの原点の周囲にスローされたオブジェクトの重心の正接瞬間的な速度です。 この正接の速度は、コント ローラーの配信元とスローされるオブジェクトの重心の間の距離を表すベクトルで、コント ローラーの角度の速度のクロス積です。
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. スローされたオブジェクトの合計のベロシティは、コント ローラーの速度と考えたこの速度の合計ではそのためです。 `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **特に注意、*時間*速度を適用する**します。 ボタンが押されたときに、オペレーティング システムに Bluetooth を通じてバブルアップするには、そのイベントの最大 20 ミリ秒かかります。 つまりからコント ローラーの状態変更のポーリングが押されていない状態に押された状態またはその逆を取得するコント ローラーの姿勢情報は、この状態の変更の前になります実際に場合。 さらに、API、ポーリングによって提示されるコント ローラーの姿勢は、転送、フレームが表示されます、20 ミリ秒の詳細については、今後ある可能性がある時に可能性の高い姿勢を反映するように予測します。 適しています。*レンダリング*、オブジェクトが保持されていますが、時間の問題をさらに大きく*を対象とする*オブジェクトのスローを離したよう、今のところ、軌道を計算します。 さいわい、Unity のイベントのような場合は、11 月の更新で*InteractionSourcePressed*または*InteractionSourceReleased*送信されると、状態には、履歴の姿勢データが含まれていますから戻るときに、ボタン実際には、押された状態またはリリースしました。  最も正確なコント ローラーの表示とスロー時に対象とするコント ローラーを取得するには、適切なポーリングとをイベントを使用する必要があります正しく。
   * **コント ローラーのレンダリング**フレームごとに、アプリは、コント ローラーを配置する必要があります*GameObject*前方予測コント ローラーで、現在のフレームの photon 時間の発生し得る。  ポーリング Api などの Unity からこのデータを取得する*[XR します。InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* または *[XR します。WSA します。Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* します。
   * **コント ローラーを対象とする**キーを押してまたはリリース時に、アプリが raycast をする必要があり、そのキーを押すか、リリース イベントの履歴のコント ローラーの姿勢に基づく軌道を計算します。  ように Unity イベント Api からこのデータを取得する *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* します。
* **グリップの姿勢を使用して、** します。 グリップの姿勢、いないポインター姿勢を基準とした角度の速度と速度が報告されます。

今後の Windows 更新プログラムを向上させるために引き続きをスローし、ことの詳細については、ここに検出されることができます。

## <a name="accelerate-development-with-mixed-reality-toolkit"></a>Mixed Reality Toolkit を使用した開発を高速化します。

InputManager と Unity で MotionController に関する 2 つの例のシーンがあります。 これらのシーンの中から MRTK の InputManager を使用して、アニメーション コント ローラー ボタンからデータ イベントの処理を活用する方法を確認できます。

- [HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [README ファイルの技術的な詳細](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

![入力例 MRTK シーン](images/MRTK_ExampleScene_Input.png)<br>
*入力例 MRTK シーン*

### <a name="automatic-scene-setup"></a>自動のシーンのセットアップ

インポートするときに[MRTK が Unity パッケージをリリース](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)からプロジェクトを複製するか、 [GitHub リポジトリ](https://github.com/Microsoft/MixedRealityToolkit-Unity)Unity で新しいメニュー ' Mixed Reality Toolkit' を検索します。 [構成] メニューで、' Mixed Reality シーン設定の適用 ' メニューが表示されます。 既定のカメラを削除し、基本コンポーネントを追加します。 これをクリックすると [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)、 [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)、および[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)します。

![シーンのセットアップの MRTK メニュー](images/MRTK_Input_Menu.png)<br>
*シーンのセットアップの MRTK メニュー*

![MRTK で自動シーンのセットアップ](images/MRTK_HowTo_Input1.png)<br>
*MRTK で自動シーンのセットアップ*

### <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera プレハブ

これらのプロジェクト パネルから手動で追加できます。 プレハブとしてこれらのコンポーネントを見つけることができます。 検索する場合に**MixedRealityCamera**、2 つの異なるカメラ プレハブを表示することができます。 違いは、 **MixedRealityCamera**はカメラのみプレハブは、 **MixedRealityCameraParent** Teleportation、モーションなどイマーシブ ヘッドセットの追加のコンポーネントが含まれていますコント ローラーと、境界。

![MRTK でカメラのプレハブ](images/MRTK_HowTo_Input2.png)<br>
*MRTK でカメラのプレハブ*

**MixedRealtyCamera** HoloLens とイマーシブ ヘッドセットの両方をサポートします。 デバイスの種類を検出し、フラグをクリアし、スカイ ボックスなどのプロパティを最適化します。 以下、アニメーション コント ローラー モデルでは、カスタムのカーソルなどをカスタマイズでき、Floor、便利なプロパティの一部を見つけることができます。

![カーソルと床面、モーションのコント ローラーのプロパティ](images/MRTK_HowTo_Input3.png)<br>
*カーソルと床面、モーションのコント ローラーのプロパティ*

## <a name="follow-along-with-tutorials"></a>チュートリアルの手順に従う

ステップ バイ ステップのチュートリアルをより詳細なカスタマイズ例については、Mixed Reality Academy で使用できます。

- [MR 入力 211:ジェスチャ](holograms-211.md)
- [MR 入力 213:アニメーション コント ローラー](mixed-reality-213.md)

[![MR 入力 213 - モーションのコント ローラー](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*MR 入力 213 - モーションのコント ローラー*

## <a name="see-also"></a>関連項目

* [ジェスチャ](gestures.md)
* [アニメーション コント ローラー](motion-controllers.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [MixedRealityToolkit Unity で InteractionInputSource.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
