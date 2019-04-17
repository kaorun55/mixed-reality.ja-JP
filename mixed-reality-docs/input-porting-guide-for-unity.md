---
title: Unity のガイドの移植の入力
description: Unity での Windows Mixed Reality の入力を処理する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 入力、unity、移植
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602791"
---
# <a name="input-porting-guide-for-unity"></a><span data-ttu-id="8d525-104">Unity のガイドの移植の入力</span><span class="sxs-lookup"><span data-stu-id="8d525-104">Input porting guide for Unity</span></span>

<span data-ttu-id="8d525-105">Windows Mixed Reality を使用して、複数のプラットフォーム全体にわたる Unity の一般的な Input.GetButton/GetAxis Api または Windows 固有 XR の 2 つのアプローチの 1 つに、入力のロジックを移植することができます。WSA します。アニメーション コント ローラーと HoloLens 手を具体的には豊富なデータを提供する Api を入力します。</span><span class="sxs-lookup"><span data-stu-id="8d525-105">You can port your input logic to Windows Mixed Reality using one of two approaches, Unity's general Input.GetButton/GetAxis APIs that span across multiple platforms, or the Windows-specific XR.WSA.Input APIs that offer richer data specifically for motion controllers and HoloLens hands.</span></span>

## <a name="general-inputgetbuttongetaxis-apis"></a><span data-ttu-id="8d525-106">[全般] Input.GetButton/GetAxis Api</span><span class="sxs-lookup"><span data-stu-id="8d525-106">General Input.GetButton/GetAxis APIs</span></span>

<span data-ttu-id="8d525-107">入力を公開する、その全般 Input.GetButton/Input.GetAxis Api を現在使用して unity [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)と[OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)します。</span><span class="sxs-lookup"><span data-stu-id="8d525-107">Unity currently uses its general Input.GetButton/Input.GetAxis APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) and [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html).</span></span> <span data-ttu-id="8d525-108">Windows Mixed Reality でモーションのコント ローラーをサポートするための最も簡単なパスは既に、アプリは、これらの Api を使用して、入力は場合、: ボタンと Input Manager での軸を再マップする必要があるだけです。</span><span class="sxs-lookup"><span data-stu-id="8d525-108">If your apps are already using these APIs for input, this is the easiest path for supporting motion controllers in Windows Mixed Reality: you should just need to remap buttons and axes in the Input Manager.</span></span>

<span data-ttu-id="8d525-109">詳細については、次を参照してください。、 [Unity ボタン/軸マッピング テーブル](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)と[一般的な Unity Api の概要](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)します。</span><span class="sxs-lookup"><span data-stu-id="8d525-109">For more information, see the [Unity button/axis mapping table](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) and the [overview of the common Unity APIs](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).</span></span>

## <a name="windows-specific-xrwsainput-apis"></a><span data-ttu-id="8d525-110">Windows に固有のダンプします。WSA します。入力 Api</span><span class="sxs-lookup"><span data-stu-id="8d525-110">Windows-specific XR.WSA.Input APIs</span></span>

<span data-ttu-id="8d525-111">アプリが既に各プラットフォーム用のカスタム入力ロジックをビルドする場合は、Windows に固有の空間入力 Api を使用することもできます、 **UnityEngine.XR.WSA.Input**名前空間。</span><span class="sxs-lookup"><span data-stu-id="8d525-111">If your app already builds custom input logic for each platform, you can choose to use the Windows-specific spatial input APIs under the **UnityEngine.XR.WSA.Input** namespace.</span></span> <span data-ttu-id="8d525-112">位置の精度などの追加情報または HoloLens の手と離れているコント ローラーを指示することができます、ソースの種類にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8d525-112">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart on HoloLens.</span></span>

<span data-ttu-id="8d525-113">詳細については、次を参照してください。、 [UnityEngine.XR.WSA.Input Api の概要](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)します。</span><span class="sxs-lookup"><span data-stu-id="8d525-113">For more information, see the [overview of the UnityEngine.XR.WSA.Input APIs](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="8d525-114">グリップの姿勢ポインティング ポーズとの比較</span><span class="sxs-lookup"><span data-stu-id="8d525-114">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="8d525-115">Windows Mixed Reality は、さまざまなフォーム ファクターでモーションのコント ローラーをサポートしている、各コント ローラーの設計と、ユーザーの手の形の位置とそのアプリの方向を「転送」自然の間の関係の違いポイントを表示するときに使用する必要があります、コント ローラー。</span><span class="sxs-lookup"><span data-stu-id="8d525-115">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="8d525-116">これらのコント ローラーをより適切に表すには、各操作のソースを調査することができますが発生 2 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="8d525-116">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>

* <span data-ttu-id="8d525-117">**グリップ姿勢**、片手で行うことによって、HoloLens、検出された手の形のまたはアニメーション コント ローラーを保持している片手で行うことのいずれかの場所を表します。</span><span class="sxs-lookup"><span data-stu-id="8d525-117">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="8d525-118">イマーシブ ヘッドセットは、この姿勢が最適な表示に使用**ユーザーの手**または**オブジェクトは、ユーザーの手の形で保持されている**剣やガンなど。</span><span class="sxs-lookup"><span data-stu-id="8d525-118">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="8d525-119">**位置を握って**:Palm 重心当然ながら、コント ローラーを保持しているときに、左または右中央にグリップ内の位置を調整します。</span><span class="sxs-lookup"><span data-stu-id="8d525-119">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="8d525-120">**向きの適切な軸を握って**:5 本の指フラットな姿勢を形成する完全に開くと、射線は、palm に通常 (順方向から左 palm、適切な palm から旧バージョンとの)</span><span class="sxs-lookup"><span data-stu-id="8d525-120">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="8d525-121">**向きの順方向軸を握って**:部分的に (場合と同様、コント ローラーを保持している) の手の閉じるときに、"forward"チューブを通じて非 thumb 指によって形成されるポイントの半径。</span><span class="sxs-lookup"><span data-stu-id="8d525-121">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="8d525-122">**軸の向きを握って**:右と前方参照の定義が含まれるアップ軸。</span><span class="sxs-lookup"><span data-stu-id="8d525-122">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="8d525-123">グリップの姿勢をベンダー間入力のいずれかの Unity の API を通じてアクセスできます (**[XR します。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)します。GetLocalPosition/Rotation**) または Windows 固有 API (**sourceState.sourcePose.TryGetPosition/Rotation**、グリップ姿勢を要求する)。</span><span class="sxs-lookup"><span data-stu-id="8d525-123">You can access the grip pose through either Unity's cross-vendor input API (**[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation**) or through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Grip pose).</span></span>
* <span data-ttu-id="8d525-124">**ポインター姿勢**、フォワード指し示すコント ローラーのヒントを表します。</span><span class="sxs-lookup"><span data-stu-id="8d525-124">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="8d525-125">この姿勢が raycast に適してとき**UI をポイント**コント ローラー モデル自体をレンダリングする場合。</span><span class="sxs-lookup"><span data-stu-id="8d525-125">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="8d525-126">現時点では、ポインターの姿勢は、Windows 固有 API を通じてしか利用できません (**sourceState.sourcePose.TryGetPosition/Rotation**ポインターの姿勢を要求する)。</span><span class="sxs-lookup"><span data-stu-id="8d525-126">Currently, the pointer pose is available only through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Pointer pose).</span></span>

<span data-ttu-id="8d525-127">これらの姿勢座標がすべて Unity ワールド座標で表されます。</span><span class="sxs-lookup"><span data-stu-id="8d525-127">These pose coordinates are all expressed in Unity world coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d525-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d525-128">See also</span></span>
* [<span data-ttu-id="8d525-129">アニメーション コント ローラー</span><span class="sxs-lookup"><span data-stu-id="8d525-129">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="8d525-130">ジェスチャと Unity のアニメーション コント ローラー</span><span class="sxs-lookup"><span data-stu-id="8d525-130">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="8d525-131">UnityEngine.XR.WSA.Input</span><span class="sxs-lookup"><span data-stu-id="8d525-131">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="8d525-132">UnityEngine.XR.InputTracking</span><span class="sxs-lookup"><span data-stu-id="8d525-132">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="8d525-133">移植のガイド</span><span class="sxs-lookup"><span data-stu-id="8d525-133">Porting guides</span></span>](porting-guides.md)
