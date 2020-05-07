---
title: Unreal でのハンドトラッキング
description: Unreal でハンドトラッキングを使用する方法について説明します。
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、ハンドトラッキング
ms.openlocfilehash: 3f7f4dd1eb62cb707eaaf8632a2ba3c280a4ac31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835445"
---
# <a name="hand-tracking"></a>ハンドトラッキング

ハンドトラッキングシステムは、個人のてのひらとフィンガーを入力として使用します。 開発者は、すべての指の位置と回転、palm 全体、さらに独自のコードで使用するためのジェスチャを取得できます。 

## <a name="hand-pose"></a>手の形

開発者は、手を使用して、アクティブなユーザーの手と指を入力として追跡できます。 このシステムは、ブループリントと C++ の両方で公開されています。 技術的な詳細は、対応する WinRT クラスの[ウィンドウ](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose)に含まれています。この UNREAL API は、unreal の座標系の形式でデータを提供し、ティックは Unreal Engine と同期しています。

### <a name="enum"></a>列挙型

Ewmr引き渡す Keypoint は、手のボーン階層について説明します。 

建築

![ハンドキーポイント BP](images/unreal/hand-keypoint-bp.png)
 
C++: 
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

![手スケルトン](images/hand-skeleton.png)

数値は、 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)テーブルにあります。これは、
 
### <a name="functions"></a>関数

ブループリントで手作業の追跡関数を使用するには、"手作業の追跡/Windows Mixed Reality" を開きます。

![ハンドトラッキング BP](images/unreal/hand-tracking-bp.png)

C++ 関数の場合は、"WindowsMixedRealityHandTrackingFunctionLibrary .h" を含めます。

BP

![ハンドトラッキング BP のサポート](images/unreal/supports-hand-tracking-bp.png)
 
C++: 
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

デバイスで手動追跡がサポートされている場合は true を返し、ハンドトラッキングが使用できない場合は false を返します。

BP

![ハンドジョイント変換の取得](images/unreal/get-hand-joint-transform.png)
 
C++: 
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

この関数は、手の空間データを返します。 データは、フレーム内のすべてのフレームを更新し、返された値はキャッシュされます。 パフォーマンス上の理由から、この関数では大きなロジックを使用しないことをお勧めします。 

* ユーザー**の手が**左または右にある場合があります
* **Keypoint** –ハンドのボーンです。 
* **Transform** –ボーンの基本の座標と向きを調整します。 ボーンの末尾の変換データを取得するには、次のボーンのベースが要求される必要があります。 特別なヒントのボーンは、distal の終わりを示します。 
* **Radius** : ボーンのベースの半径。
* **戻り値**-ボーンがこのフレームを追跡している場合は true、ボーンが追跡されていない場合は false。

## <a name="hand-live-link-animation"></a>ハンドライブリンクアニメーション
Live Link プラグインを使用して、手の形でアニメーションに公開されます。 プラグインのドキュメントは[こちら](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)です

Windows Mixed Reality とライブリンクプラグインが有効になっている場合は、[**ウィンドウ > ライブリンク]** にアクセスして、[ライブリンクエディター] ウィンドウを開きます。 [ **+ ソース] ボタン**をクリックし、[Windows Mixed Reality ハンドトラッキングソース] を有効にします。

![ライブリンクのソース](images/unreal/live-link-source.png)
 
ソースを有効にし、任意のアニメーションアセットを開くと、アニメーションの [シーンのプレビュー] タブには次の追加オプションが表示されます (詳細は、プレリリースのライブリンクドキュメントに含まれています。プラグインがベータ版であるため、プロセスは後で変更される可能性があります)。

![ライブリンクアニメーション](images/unreal/live-link-animation.png)
 
ハンドアニメーションの階層は、Ewmrのキーポイントと同じです。 アニメーションは WindowsMixedRealityHandTrackingLiveLinkRemapAsset を使用して再ターゲットできます。 

![ライブリンクアニメーション2](images/unreal/live-link-animation2.png)
 
エディターでサブクラス化できます。

![ライブリンクの再マップ](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a>手動メッシュ
ユーザーハンドを表すメッシュ。 

![手動メッシュ](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a>有効化および構成する方法

開発者は、独自の目的でメッシュに直接アクセスできます。 ARSessionConfig でこのアクセスを有効にする必要があります: AR 設定-> ワールドマッピング-> 追跡されたジオメトリからメッシュデータを生成します。 

メッシュの既定のパラメーターを次に示します。

1.  遮蔽にメッシュデータを使用する
2.  メッシュデータの競合を生成する
3.  メッシュデータの Nav メッシュを生成します
4.  ワイヤーフレームでメッシュデータをレンダリングする–生成されたメッシュを示すデバッグパラメーター

混合現実プロジェクトの場合、これらのパラメーター値は空間マッピングメッシュと手動メッシュの既定値として使用されます。 開発者は、特定のメッシュの BP またはコードでそれらを変更できます。

### <a name="c-api-reference"></a>C++ API リファレンス 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

この値は、すべての追跡可能なオブジェクト間のハンドメッシュです。

```cpp
class FARSupportInterface 
{
public:
// other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

これらのデリゲートは、システムが手動メッシュを含む追跡可能なオブジェクトを検出したときに呼び出されます。 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
デリゲートへのハンドラーは、次のシグネチャを持つ必要があります。
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

メッシュデータには、`UARTrackedGeometry::GetUnderlyingMesh`

### <a name="blueprint-api-reference"></a>ブループリント API リファレンス

開発者は、ブループリントアクターに AR Trackable 通知コンポーネントを追加する必要があります。

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)
 
次に、コンポーネントの詳細にアクセスします。 

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)
 
次のようなコードを使用して、[追跡ジオメトリの追加/更新/削除] を上書きします。

![ARTrackable 通知で](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>手の線

開発者は、ハンドレイをポインティングデバイスとして使用できます。 システムは、C++ およびブループリントで使用できます。 技術的には、 [SpatialPointerInteractionSourcePose を](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)公開します。

すべての関数の結果がすべてのフレームに変更されるため、すべての関数が呼び出し可能になることに注意してください。 純粋[な](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)vs 純粋でないまたは呼び出し可能関数の詳細については、「」を参照してください。

ブループリントが "Windows Mixed Reality HMD" を開く場合

![ハンド光線 BP](images/unreal/hand-rays-bp.png)
 
C++ の場合は、"WindowsMixedRealityFunctionLibrary .h" を使用します。

### <a name="enum"></a>列挙型

![入力コントローラーボタン](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* **Select** -–ユーザーがトリガーした選択イベント。 HoloLens のタップまたは宝石とコミットによって HoloLens 2 でトリガーできます。 このイベントをトリガーするもう1つの方法は、"Select" と言います。 
* [ユーザーによってトリガーされるイベントを**把握**する]: ホログラムでユーザーの指を閉じることで、HoloLens 2 でトリガーされます。 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* **Nottracked** –-ハンドは表示されません
* **追跡**–ハンドは完全に追跡されます。

### <a name="struct"></a>構造体

![ポインターのポーズ情報 BP](images/unreal/pointer-pose-info-bp.png)
```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```
* **Origin** –ハンドオリジン
* **方向**–ハンドの方向
* **アップ**(手動)
* **方向**-方向の四元数 
* **ステータスの追跡**-現在の追跡状態

### <a name="functions"></a>関数

すべての関数は、継続的な監視のためにすべてのフレームで呼び出し可能である必要があります。 

![ポインターの表示情報の取得](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
関数は、このフレームのハンドレイの方向に関する完全な情報を返します。 

![Grasped BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
このフレームに手が grasped 場合に true を返します。 

![選択された BP (BP)](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
ユーザーがこのフレームで Select をトリガーした場合に true を返します。

![ボタンが BP をクリックしました](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
このフレームでイベント/ボタンがトリガーされた場合に true を返します。

![コントローラー追跡ステータス BP の取得](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
このフレームの追跡ステータスを返します。

## <a name="gestures"></a>ジェスチャ

Hololens 2 では、空間ジェスチャを追跡できます。 これらのジェスチャの詳細について[は、開発](https://docs.microsoft.com/hololens/hololens2-basic-usage)者が混合現実アプリケーションの入力としてキャプチャすることができます。 

C++ 関数は、"WindowsMixedRealitySpatialInputFunctionLibrary" にあります。

ブループリント関数は、Windows Mixed Reality 空間入力に含まれています

![キャプチャジェスチャ](images/unreal/capture-gestures.png)

### <a name="enum"></a>列挙型

![ジェスチャの種類](images/unreal/gesture-type.png)
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```
この列挙型は、空間軸のジェスチャを表します。 詳細については、こちらを参照して[ください](holograms-211.md)。

### <a name="function"></a>関数

![キャプチャジェスチャ BP](images/unreal/capture-gestures-bp.png)
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```
関数は、ジェスチャのキャプチャを有効または無効にします。 有効なジェスチャは、入力イベントを発生させます。 ジェスチャキャプチャが成功した場合は true を返し、エラーが発生した場合は false を返します。
主要イベント

![主要イベント](images/unreal/key-events.png)

![主要イベント2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```
ジェスチャが有効になっている場合は、イベントの発生が開始されます。 

