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
# <a name="hand-tracking"></a><span data-ttu-id="7d8d5-104">ハンドトラッキング</span><span class="sxs-lookup"><span data-stu-id="7d8d5-104">Hand Tracking</span></span>

<span data-ttu-id="7d8d5-105">ハンドトラッキングシステムは、個人のてのひらとフィンガーを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-105">The hand tracking system uses a person’s palms and fingers as input to Unreal.</span></span> <span data-ttu-id="7d8d5-106">開発者は、すべての指の位置と回転、palm 全体、さらに独自のコードで使用するためのジェスチャを取得できます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-106">A developer can get every finger’s position and rotation, the entire palm, and even hand gestures to use in their own code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="7d8d5-107">手の形</span><span class="sxs-lookup"><span data-stu-id="7d8d5-107">Hand Pose</span></span>

<span data-ttu-id="7d8d5-108">開発者は、手を使用して、アクティブなユーザーの手と指を入力として追跡できます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-108">Using the hand pose, developers can track the hands and fingers of the active user as input.</span></span> <span data-ttu-id="7d8d5-109">このシステムは、ブループリントと C++ の両方で公開されています。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-109">This system is exposed through both Blueprints and C++.</span></span> <span data-ttu-id="7d8d5-110">技術的な詳細は、対応する WinRT クラスの[ウィンドウ](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose)に含まれています。この UNREAL API は、unreal の座標系の形式でデータを提供し、ティックは Unreal Engine と同期しています。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-110">Technical details are in the corresponding WinRT class [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) This Unreal API provides the data in the format of Unreal’s coordinate system and ticks are synchronised with the Unreal Engine.</span></span>

### <a name="enum"></a><span data-ttu-id="7d8d5-111">列挙型</span><span class="sxs-lookup"><span data-stu-id="7d8d5-111">Enum</span></span>

<span data-ttu-id="7d8d5-112">Ewmr引き渡す Keypoint は、手のボーン階層について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-112">EWMRHandKeypoint describes the Hand’s bone hierarchy.</span></span> 

<span data-ttu-id="7d8d5-113">建築</span><span class="sxs-lookup"><span data-stu-id="7d8d5-113">Blueprint:</span></span>

![ハンドキーポイント BP](images/unreal/hand-keypoint-bp.png)
 
<span data-ttu-id="7d8d5-115">C++: </span><span class="sxs-lookup"><span data-stu-id="7d8d5-115">C++:</span></span>
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

<span data-ttu-id="7d8d5-117">数値は、 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)テーブルにあります。これは、</span><span class="sxs-lookup"><span data-stu-id="7d8d5-117">The numerical values can be found in the table [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span></span>
 
### <a name="functions"></a><span data-ttu-id="7d8d5-118">関数</span><span class="sxs-lookup"><span data-stu-id="7d8d5-118">Functions</span></span>

<span data-ttu-id="7d8d5-119">ブループリントで手作業の追跡関数を使用するには、"手作業の追跡/Windows Mixed Reality" を開きます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-119">To use hand tracking functions in Blueprints, open "Hand Tracking/Windows Mixed Reality"</span></span>

![ハンドトラッキング BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="7d8d5-121">C++ 関数の場合は、"WindowsMixedRealityHandTrackingFunctionLibrary .h" を含めます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-121">For C++ functions, include "WindowsMixedRealityHandTrackingFunctionLibrary.h"</span></span>

<span data-ttu-id="7d8d5-122">BP</span><span class="sxs-lookup"><span data-stu-id="7d8d5-122">BP:</span></span>

![ハンドトラッキング BP のサポート](images/unreal/supports-hand-tracking-bp.png)
 
<span data-ttu-id="7d8d5-124">C++: </span><span class="sxs-lookup"><span data-stu-id="7d8d5-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

<span data-ttu-id="7d8d5-125">デバイスで手動追跡がサポートされている場合は true を返し、ハンドトラッキングが使用できない場合は false を返します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-125">Returns true if hand tracking is supported on the device, false if hand tracking is not available.</span></span>

<span data-ttu-id="7d8d5-126">BP</span><span class="sxs-lookup"><span data-stu-id="7d8d5-126">BP:</span></span>

![ハンドジョイント変換の取得](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="7d8d5-128">C++: </span><span class="sxs-lookup"><span data-stu-id="7d8d5-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="7d8d5-129">この関数は、手の空間データを返します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-129">This function returns spatial data of the hand.</span></span> <span data-ttu-id="7d8d5-130">データは、フレーム内のすべてのフレームを更新し、返された値はキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-130">The data updates every frame, inside a frame the returned values are cached.</span></span> <span data-ttu-id="7d8d5-131">パフォーマンス上の理由から、この関数では大きなロジックを使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-131">It is not recommended to have heavy logic on this function for performance reasons.</span></span> 

* <span data-ttu-id="7d8d5-132">ユーザー**の手が**左または右にある場合があります</span><span class="sxs-lookup"><span data-stu-id="7d8d5-132">**Hand** – hand of the user, may be left or right</span></span>
* <span data-ttu-id="7d8d5-133">**Keypoint** –ハンドのボーンです。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-133">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="7d8d5-134">**Transform** –ボーンの基本の座標と向きを調整します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-134">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="7d8d5-135">ボーンの末尾の変換データを取得するには、次のボーンのベースが要求される必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-135">To get the transform data for the end of a bone, the base of the next bone should be requested.</span></span> <span data-ttu-id="7d8d5-136">特別なヒントのボーンは、distal の終わりを示します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-136">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="7d8d5-137">**Radius** : ボーンのベースの半径。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-137">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="7d8d5-138">**戻り値**-ボーンがこのフレームを追跡している場合は true、ボーンが追跡されていない場合は false。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-138">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="7d8d5-139">ハンドライブリンクアニメーション</span><span class="sxs-lookup"><span data-stu-id="7d8d5-139">Hand Live Link Animation</span></span>
<span data-ttu-id="7d8d5-140">Live Link プラグインを使用して、手の形でアニメーションに公開されます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-140">Hand poses are exposed to Animation using the Live Link plugin.</span></span> <span data-ttu-id="7d8d5-141">プラグインのドキュメントは[こちら](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)です</span><span class="sxs-lookup"><span data-stu-id="7d8d5-141">The plugin documentation is [here](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span></span>

<span data-ttu-id="7d8d5-142">Windows Mixed Reality とライブリンクプラグインが有効になっている場合は、[**ウィンドウ > ライブリンク]** にアクセスして、[ライブリンクエディター] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-142">If the Windows Mixed Reality and Live Link plugins are enabled, go to **Window > Live Link** to open the Live Link editor window.</span></span> <span data-ttu-id="7d8d5-143">[ **+ ソース] ボタン**をクリックし、[Windows Mixed Reality ハンドトラッキングソース] を有効にします。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-143">Click the **+ Source button** and enable Windows Mixed Reality Hand Tracking Source</span></span>

![ライブリンクのソース](images/unreal/live-link-source.png)
 
<span data-ttu-id="7d8d5-145">ソースを有効にし、任意のアニメーションアセットを開くと、アニメーションの [シーンのプレビュー] タブには次の追加オプションが表示されます (詳細は、プレリリースのライブリンクドキュメントに含まれています。プラグインがベータ版であるため、プロセスは後で変更される可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-145">After you enable the source and open any animation asset, the Preview Scene tab of Animation will have the following additional options (the details are in Unreal’s Live Link documentation- as the plugin is in beta, the process may change later)</span></span>

![ライブリンクアニメーション](images/unreal/live-link-animation.png)
 
<span data-ttu-id="7d8d5-147">ハンドアニメーションの階層は、Ewmrのキーポイントと同じです。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-147">The hand animation hierarchy is the same as in EWMRHandKeypoint.</span></span> <span data-ttu-id="7d8d5-148">アニメーションは WindowsMixedRealityHandTrackingLiveLinkRemapAsset を使用して再ターゲットできます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-148">Animation can be retargeted using WindowsMixedRealityHandTrackingLiveLinkRemapAsset.</span></span> 

![ライブリンクアニメーション2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="7d8d5-150">エディターでサブクラス化できます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-150">It can be subclassed in the editor</span></span>

![ライブリンクの再マップ](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a><span data-ttu-id="7d8d5-152">手動メッシュ</span><span class="sxs-lookup"><span data-stu-id="7d8d5-152">Hand Mesh</span></span>
<span data-ttu-id="7d8d5-153">ユーザーハンドを表すメッシュ。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-153">Mesh representing the user hands.</span></span> 

![手動メッシュ](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a><span data-ttu-id="7d8d5-155">有効化および構成する方法</span><span class="sxs-lookup"><span data-stu-id="7d8d5-155">How to enable and configure</span></span>

<span data-ttu-id="7d8d5-156">開発者は、独自の目的でメッシュに直接アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-156">Developers can get direct access to hand meshes for their own purposes.</span></span> <span data-ttu-id="7d8d5-157">ARSessionConfig でこのアクセスを有効にする必要があります: AR 設定-> ワールドマッピング-> 追跡されたジオメトリからメッシュデータを生成します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-157">This access must be enabled in ARSessionConfig: AR Settings -> World Mapping -> Generate Mesh Data from Tracked Geometry.</span></span> 

<span data-ttu-id="7d8d5-158">メッシュの既定のパラメーターを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-158">Here are the default parameters for meshes:</span></span>

1.  <span data-ttu-id="7d8d5-159">遮蔽にメッシュデータを使用する</span><span class="sxs-lookup"><span data-stu-id="7d8d5-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="7d8d5-160">メッシュデータの競合を生成する</span><span class="sxs-lookup"><span data-stu-id="7d8d5-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="7d8d5-161">メッシュデータの Nav メッシュを生成します</span><span class="sxs-lookup"><span data-stu-id="7d8d5-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="7d8d5-162">ワイヤーフレームでメッシュデータをレンダリングする–生成されたメッシュを示すデバッグパラメーター</span><span class="sxs-lookup"><span data-stu-id="7d8d5-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="7d8d5-163">混合現実プロジェクトの場合、これらのパラメーター値は空間マッピングメッシュと手動メッシュの既定値として使用されます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-163">For mixed reality projects, these parameter values will be used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="7d8d5-164">開発者は、特定のメッシュの BP またはコードでそれらを変更できます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-164">Developers can change them in BP or code for any particular mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="7d8d5-165">C++ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="7d8d5-165">C++ API Reference</span></span> 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

<span data-ttu-id="7d8d5-166">この値は、すべての追跡可能なオブジェクト間のハンドメッシュです。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-166">This value is the hand mesh among all trackable objects.</span></span>

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

<span data-ttu-id="7d8d5-167">これらのデリゲートは、システムが手動メッシュを含む追跡可能なオブジェクトを検出したときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-167">These delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
<span data-ttu-id="7d8d5-168">デリゲートへのハンドラーは、次のシグネチャを持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-168">Handlers to the delegates should have the following signature:</span></span>
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

<span data-ttu-id="7d8d5-169">メッシュデータには、`UARTrackedGeometry::GetUnderlyingMesh`</span><span class="sxs-lookup"><span data-stu-id="7d8d5-169">Mesh data can be accessed by `UARTrackedGeometry::GetUnderlyingMesh`</span></span>

### <a name="blueprint-api-reference"></a><span data-ttu-id="7d8d5-170">ブループリント API リファレンス</span><span class="sxs-lookup"><span data-stu-id="7d8d5-170">Blueprint API Reference</span></span>

<span data-ttu-id="7d8d5-171">開発者は、ブループリントアクターに AR Trackable 通知コンポーネントを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-171">Developers should add an AR Trackable Notify Component to a Blueprint actor</span></span>

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)
 
<span data-ttu-id="7d8d5-173">次に、コンポーネントの詳細にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-173">Then go to the component’s details</span></span> 

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)
 
<span data-ttu-id="7d8d5-175">次のようなコードを使用して、[追跡ジオメトリの追加/更新/削除] を上書きします。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-175">And overwrite On Add/Update/Remove Tracked Geometry with code like the below:</span></span>

![ARTrackable 通知で](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="7d8d5-177">手の線</span><span class="sxs-lookup"><span data-stu-id="7d8d5-177">Hand Rays</span></span>

<span data-ttu-id="7d8d5-178">開発者は、ハンドレイをポインティングデバイスとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-178">Developers can use a hand ray as a pointing device.</span></span> <span data-ttu-id="7d8d5-179">システムは、C++ およびブループリントで使用できます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-179">The system is available in C++ and Blueprint.</span></span> <span data-ttu-id="7d8d5-180">技術的には、 [SpatialPointerInteractionSourcePose を](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)公開します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-180">Technically it exposes [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span></span>

<span data-ttu-id="7d8d5-181">すべての関数の結果がすべてのフレームに変更されるため、すべての関数が呼び出し可能になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-181">It’s important to mention that since the results of all the functions changes every frame, they are all made callable.</span></span> <span data-ttu-id="7d8d5-182">純粋[な](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)vs 純粋でないまたは呼び出し可能関数の詳細については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-182">For more information about pure vs impure or callable functions, see [that](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="7d8d5-183">ブループリントが "Windows Mixed Reality HMD" を開く場合</span><span class="sxs-lookup"><span data-stu-id="7d8d5-183">For Blueprint open “Windows Mixed Reality HMD”</span></span>

![ハンド光線 BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="7d8d5-185">C++ の場合は、"WindowsMixedRealityFunctionLibrary .h" を使用します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-185">For C++ include "WindowsMixedRealityFunctionLibrary.h"</span></span>

### <a name="enum"></a><span data-ttu-id="7d8d5-186">列挙型</span><span class="sxs-lookup"><span data-stu-id="7d8d5-186">Enum</span></span>

![入力コントローラーボタン](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* <span data-ttu-id="7d8d5-188">**Select** -–ユーザーがトリガーした選択イベント。 HoloLens のタップまたは宝石とコミットによって HoloLens 2 でトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-188">**Select** -– User triggered Select event, which can be triggered in HoloLens 2 by airtap or gaze and commit.</span></span> <span data-ttu-id="7d8d5-189">このイベントをトリガーするもう1つの方法は、"Select" と言います。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-189">Another way to trigger this event is to say “Select”.</span></span> 
* <span data-ttu-id="7d8d5-190">[ユーザーによってトリガーされるイベントを**把握**する]: ホログラムでユーザーの指を閉じることで、HoloLens 2 でトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-190">**Grasp** -– User triggered Grasp event, which is triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* <span data-ttu-id="7d8d5-191">**Nottracked** –-ハンドは表示されません</span><span class="sxs-lookup"><span data-stu-id="7d8d5-191">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="7d8d5-192">**追跡**–ハンドは完全に追跡されます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-192">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="7d8d5-193">構造体</span><span class="sxs-lookup"><span data-stu-id="7d8d5-193">Struct</span></span>

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
* <span data-ttu-id="7d8d5-195">**Origin** –ハンドオリジン</span><span class="sxs-lookup"><span data-stu-id="7d8d5-195">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="7d8d5-196">**方向**–ハンドの方向</span><span class="sxs-lookup"><span data-stu-id="7d8d5-196">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="7d8d5-197">**アップ**(手動)</span><span class="sxs-lookup"><span data-stu-id="7d8d5-197">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="7d8d5-198">**方向**-方向の四元数</span><span class="sxs-lookup"><span data-stu-id="7d8d5-198">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="7d8d5-199">**ステータスの追跡**-現在の追跡状態</span><span class="sxs-lookup"><span data-stu-id="7d8d5-199">**Tracking Status** – current tracking status</span></span>

### <a name="functions"></a><span data-ttu-id="7d8d5-200">関数</span><span class="sxs-lookup"><span data-stu-id="7d8d5-200">Functions</span></span>

<span data-ttu-id="7d8d5-201">すべての関数は、継続的な監視のためにすべてのフレームで呼び出し可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-201">All the functions should be callable on every frame for continuous monitoring.</span></span> 

![ポインターの表示情報の取得](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
<span data-ttu-id="7d8d5-203">関数は、このフレームのハンドレイの方向に関する完全な情報を返します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-203">The function returns the full information about the hand ray direction in this frame.</span></span> 

![Grasped BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
<span data-ttu-id="7d8d5-205">このフレームに手が grasped 場合に true を返します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-205">Returns true if the hand is grasped in this frame.</span></span> 

![選択された BP (BP)](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
<span data-ttu-id="7d8d5-207">ユーザーがこのフレームで Select をトリガーした場合に true を返します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-207">Returns true if the user triggered Select in this frame.</span></span>

![ボタンが BP をクリックしました](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
<span data-ttu-id="7d8d5-209">このフレームでイベント/ボタンがトリガーされた場合に true を返します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-209">Returns true if the event/button is triggered in this frame.</span></span>

![コントローラー追跡ステータス BP の取得](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
<span data-ttu-id="7d8d5-211">このフレームの追跡ステータスを返します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-211">Returns the tracking status in this frame.</span></span>

## <a name="gestures"></a><span data-ttu-id="7d8d5-212">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="7d8d5-212">Gestures</span></span>

<span data-ttu-id="7d8d5-213">Hololens 2 では、空間ジェスチャを追跡できます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-213">The Hololens 2 can track spatial gestures.</span></span> <span data-ttu-id="7d8d5-214">これらのジェスチャの詳細について[は、開発](https://docs.microsoft.com/hololens/hololens2-basic-usage)者が混合現実アプリケーションの入力としてキャプチャすることができます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-214">Details about these gestures are [here](https://docs.microsoft.com/hololens/hololens2-basic-usage) A developer can capture them as input to their mixed reality application.</span></span> 

<span data-ttu-id="7d8d5-215">C++ 関数は、"WindowsMixedRealitySpatialInputFunctionLibrary" にあります。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-215">The C++ function is in "WindowsMixedRealitySpatialInputFunctionLibrary.h"</span></span>

<span data-ttu-id="7d8d5-216">ブループリント関数は、Windows Mixed Reality 空間入力に含まれています</span><span class="sxs-lookup"><span data-stu-id="7d8d5-216">The Blueprint function is in Windows Mixed Reality Spatial Input</span></span>

![キャプチャジェスチャ](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="7d8d5-218">列挙型</span><span class="sxs-lookup"><span data-stu-id="7d8d5-218">Enum</span></span>

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
<span data-ttu-id="7d8d5-220">この列挙型は、空間軸のジェスチャを表します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-220">This enum describes spatial axis gestures.</span></span> <span data-ttu-id="7d8d5-221">詳細については、こちらを参照して[ください](holograms-211.md)。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-221">You can read about them [here](holograms-211.md)</span></span>

### <a name="function"></a><span data-ttu-id="7d8d5-222">関数</span><span class="sxs-lookup"><span data-stu-id="7d8d5-222">Function</span></span>

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
<span data-ttu-id="7d8d5-224">関数は、ジェスチャのキャプチャを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-224">The function enables and disables capturing of gestures.</span></span> <span data-ttu-id="7d8d5-225">有効なジェスチャは、入力イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-225">The enabled gestures fire input events.</span></span> <span data-ttu-id="7d8d5-226">ジェスチャキャプチャが成功した場合は true を返し、エラーが発生した場合は false を返します。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-226">It returns true if enabling gesture capture succeeded and false if there's an error.</span></span>
<span data-ttu-id="7d8d5-227">主要イベント</span><span class="sxs-lookup"><span data-stu-id="7d8d5-227">Key Events</span></span>

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
<span data-ttu-id="7d8d5-230">ジェスチャが有効になっている場合は、イベントの発生が開始されます。</span><span class="sxs-lookup"><span data-stu-id="7d8d5-230">If the gesture is enabled, the events begin firing.</span></span> 

