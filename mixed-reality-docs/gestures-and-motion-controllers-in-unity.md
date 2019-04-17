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
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="3da0b-104">ジェスチャと Unity のアニメーション コント ローラー</span><span class="sxs-lookup"><span data-stu-id="3da0b-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="3da0b-105">アクションを実行する 2 つの主要な方法がある、 [Unity で視線](gaze-in-unity.md)、[ジェスチャを渡す](gestures.md)と[コント ローラーのモーション](motion-controllers.md)します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](gestures.md) and [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="3da0b-106">空間の入力の両方のソースのデータにアクセスするには Unity で同じ Api を使用します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="3da0b-107">Unity は、Windows Mixed Reality、共通の空間の入力データにアクセスする 2 つの主な方法を提供します*Input.GetButton/Input.GetAxis*複数の Unity XR Sdk 間で機能する Api と*InteractionManager/。GestureRecognizer* API の使用可能な空間の入力データの完全なセットを公開する Windows Mixed Reality を特定します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="3da0b-108">Unity ボタン/軸マッピング テーブル</span><span class="sxs-lookup"><span data-stu-id="3da0b-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="3da0b-109">次の表に、ボタンと軸の Id には、Windows Mixed Reality モーションのコント ローラーによる用 Unity の入力マネージャーではサポートされて、 *Input.GetButton/GetAxis* Api、「Windows MR 固有」列は、プロパティにはオフの使用可能な*InteractionSourceState*型。</span><span class="sxs-lookup"><span data-stu-id="3da0b-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="3da0b-110">これらの各 Api については、以下のセクションで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="3da0b-111">Windows Mixed Reality をボタン/軸 ID のマッピングには、Oculus ボタン/軸 Id 一般と一致します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="3da0b-112">Windows Mixed Reality をボタン/軸 ID のマッピングは、2 つの方法で OpenVR のマッピングによって異なります。</span><span class="sxs-lookup"><span data-stu-id="3da0b-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="3da0b-113">マッピングは、サムスティックおよびタッチパッドの両方のコント ローラーをサポートするために個別のサムスティックからいるタッチパッド Id を使用します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="3da0b-114">マッピングは、A と X ボタン物理 ABXY ボタンの使用可能なもののままにする Id、メニュー ボタンのオーバー ロードを回避できます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="3da0b-115">入力</span><span class="sxs-lookup"><span data-stu-id="3da0b-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="3da0b-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">一般的な Unity Api</a></span><span class="sxs-lookup"><span data-stu-id="3da0b-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="3da0b-117">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="3da0b-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="3da0b-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR に固有の入力 API</a></span><span class="sxs-lookup"><span data-stu-id="3da0b-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="3da0b-119">(ダンプします。WSA します。入力)</span><span class="sxs-lookup"><span data-stu-id="3da0b-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="3da0b-120">左側にあります。</span><span class="sxs-lookup"><span data-stu-id="3da0b-120">Left hand</span></span> </th><th> <span data-ttu-id="3da0b-121">右側にあります。</span><span class="sxs-lookup"><span data-stu-id="3da0b-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="3da0b-122">押された選択のトリガー</span><span class="sxs-lookup"><span data-stu-id="3da0b-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="3da0b-123">9 = 1.0 の軸</span><span class="sxs-lookup"><span data-stu-id="3da0b-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="3da0b-124">10 = 1.0 の軸</span><span class="sxs-lookup"><span data-stu-id="3da0b-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="3da0b-125">selectPressed</span><span class="sxs-lookup"><span data-stu-id="3da0b-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-126">トリガーのアナログ値を選択します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="3da0b-127">軸 9</span><span class="sxs-lookup"><span data-stu-id="3da0b-127">Axis 9</span></span> </td><td> <span data-ttu-id="3da0b-128">軸 10</span><span class="sxs-lookup"><span data-stu-id="3da0b-128">Axis 10</span></span> </td><td> <span data-ttu-id="3da0b-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="3da0b-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-130">部分的に押された選択のトリガー</span><span class="sxs-lookup"><span data-stu-id="3da0b-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="3da0b-131">ボタンの 14 <i>(ゲームパッド互換性)</i> </span><span class="sxs-lookup"><span data-stu-id="3da0b-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="3da0b-132">ボタンの 15 <i>(ゲームパッド互換性)</i> </span><span class="sxs-lookup"><span data-stu-id="3da0b-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="3da0b-133">selectPressedAmount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="3da0b-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-134">押されたメニュー ボタン</span><span class="sxs-lookup"><span data-stu-id="3da0b-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="3da0b-135">ボタンの 6 \*</span><span class="sxs-lookup"><span data-stu-id="3da0b-135">Button 6\*</span></span> </td><td> <span data-ttu-id="3da0b-136">ボタンの 7 \*</span><span class="sxs-lookup"><span data-stu-id="3da0b-136">Button 7\*</span></span> </td><td> <span data-ttu-id="3da0b-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="3da0b-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-138">グリップ ボタンが押されました。</span><span class="sxs-lookup"><span data-stu-id="3da0b-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="3da0b-139">軸 11 = 1.0 (アナログ値なし)</span><span class="sxs-lookup"><span data-stu-id="3da0b-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="3da0b-140">ボタン 4 <i>(ゲームパッド互換性)</i> </span><span class="sxs-lookup"><span data-stu-id="3da0b-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="3da0b-141">軸 12 = 1.0 (アナログ値なし)</span><span class="sxs-lookup"><span data-stu-id="3da0b-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="3da0b-142">ボタン 5 <i>(ゲームパッド互換性)</i> </span><span class="sxs-lookup"><span data-stu-id="3da0b-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="3da0b-143">文章</span><span class="sxs-lookup"><span data-stu-id="3da0b-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-144">スティック X <i>(左:-1.0、適切な。1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="3da0b-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="3da0b-145">軸 1</span><span class="sxs-lookup"><span data-stu-id="3da0b-145">Axis 1</span></span> </td><td> <span data-ttu-id="3da0b-146">軸 4</span><span class="sxs-lookup"><span data-stu-id="3da0b-146">Axis 4</span></span> </td><td> <span data-ttu-id="3da0b-147">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="3da0b-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-148">スティック Y <i>(top:-1.0、下部にあります。1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="3da0b-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="3da0b-149">軸 2</span><span class="sxs-lookup"><span data-stu-id="3da0b-149">Axis 2</span></span> </td><td> <span data-ttu-id="3da0b-150">軸 5</span><span class="sxs-lookup"><span data-stu-id="3da0b-150">Axis 5</span></span> </td><td> <span data-ttu-id="3da0b-151">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="3da0b-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-152">押されたスティック</span><span class="sxs-lookup"><span data-stu-id="3da0b-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="3da0b-153">ボタンの 8</span><span class="sxs-lookup"><span data-stu-id="3da0b-153">Button 8</span></span> </td><td> <span data-ttu-id="3da0b-154">ボタンの 9</span><span class="sxs-lookup"><span data-stu-id="3da0b-154">Button 9</span></span> </td><td> <span data-ttu-id="3da0b-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="3da0b-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-156">タッチパッド X <i>(左:-1.0、適切な。1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="3da0b-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="3da0b-157">軸 17 \*</span><span class="sxs-lookup"><span data-stu-id="3da0b-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="3da0b-158">軸 19 \*</span><span class="sxs-lookup"><span data-stu-id="3da0b-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="3da0b-159">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="3da0b-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-160">タッチパッド Y <i>(top:-1.0、下部にあります。1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="3da0b-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="3da0b-161">軸 18 \*</span><span class="sxs-lookup"><span data-stu-id="3da0b-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="3da0b-162">軸 20 \*</span><span class="sxs-lookup"><span data-stu-id="3da0b-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="3da0b-163">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="3da0b-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-164">タッチ タッチパッド</span><span class="sxs-lookup"><span data-stu-id="3da0b-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="3da0b-165">ボタンの 18 \*</span><span class="sxs-lookup"><span data-stu-id="3da0b-165">Button 18\*</span></span> </td><td> <span data-ttu-id="3da0b-166">ボタンの 19 \*</span><span class="sxs-lookup"><span data-stu-id="3da0b-166">Button 19\*</span></span> </td><td> <span data-ttu-id="3da0b-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="3da0b-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-168">押されたタッチパッド</span><span class="sxs-lookup"><span data-stu-id="3da0b-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="3da0b-169">ボタンの 16 \*</span><span class="sxs-lookup"><span data-stu-id="3da0b-169">Button 16\*</span></span> </td><td> <span data-ttu-id="3da0b-170">ボタンの 17 \*</span><span class="sxs-lookup"><span data-stu-id="3da0b-170">Button 17\*</span></span> </td><td> <span data-ttu-id="3da0b-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="3da0b-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-172">6 dof グリップ姿勢またはポインター姿勢</span><span class="sxs-lookup"><span data-stu-id="3da0b-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="3da0b-173"><i>グリップ</i>のみ発生します。<a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="3da0b-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="3da0b-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="3da0b-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="3da0b-175">渡す<i>グリップ</i>または<i>ポインター</i>を引数として: sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="3da0b-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="3da0b-176">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="3da0b-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-177">状態の追跡</span><span class="sxs-lookup"><span data-stu-id="3da0b-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="3da0b-178"><i>位置の精度とソース消失のリスクを MR に固有の API を介してのみ使用できます。</i> </span><span class="sxs-lookup"><span data-stu-id="3da0b-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="3da0b-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="3da0b-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="3da0b-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="3da0b-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="3da0b-181">このボタン/軸 Id は、ゲームパッド、Oculus タッチと OpenVR で使用されるマッピングの競合による OpenVR に Unity を使用する Id によって異なります。</span><span class="sxs-lookup"><span data-stu-id="3da0b-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="3da0b-182">グリップの姿勢ポインティング ポーズとの比較</span><span class="sxs-lookup"><span data-stu-id="3da0b-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="3da0b-183">Windows Mixed Reality は、さまざまなフォーム ファクターでモーションのコント ローラーをサポートしている、各コント ローラーの設計と、ユーザーの手の形の位置とそのアプリの方向を「転送」自然の間の関係の違いポイントを表示するときに使用する必要があります、コント ローラー。</span><span class="sxs-lookup"><span data-stu-id="3da0b-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="3da0b-184">これらのコント ローラーをより適切に表すには、2 種類の各相互作用ソースを調査することができますが発生、**グリップ姿勢**と**ポインター姿勢**します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="3da0b-185">グリップ ポーズとポインター姿勢の両方の座標はグローバルの Unity ワールド座標内のすべての Unity Api で表されます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="3da0b-186">グリップの姿勢</span><span class="sxs-lookup"><span data-stu-id="3da0b-186">Grip pose</span></span>

<span data-ttu-id="3da0b-187">**グリップ姿勢**HoloLens、によって検出された手の形の palm またはアニメーション コント ローラーを保持している片手で行うことのいずれかの場所を表します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="3da0b-188">レンダリングに使用最適グリップ姿勢でイマーシブ ヘッドセット、**ユーザーの手**または**オブジェクトは、ユーザーの手の形で保持されている**剣ガンなど、します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="3da0b-189">グリップの姿勢は、として、アニメーション コント ローラーを視覚化するときにも使用、**レンダリング可能なモデル**運動の Windows で、コント ローラーは、送信元と回転の中心としてグリップ姿勢を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="3da0b-190">グリップ姿勢が具体的には次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="3da0b-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="3da0b-191">**位置を握って**:Palm 重心当然ながら、コント ローラーを保持しているときに、左または右中央にグリップ内の位置を調整します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="3da0b-192">Windows Mixed Reality アニメーション コント ローラーで、この位置は把握ボタンで一般に揃えて配置します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="3da0b-193">**向きの適切な軸を握って**:5 本の指フラットな姿勢を形成する完全に開くと、射線は、palm に通常 (順方向から左 palm、適切な palm から旧バージョンとの)</span><span class="sxs-lookup"><span data-stu-id="3da0b-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="3da0b-194">**向きの順方向軸を握って**:部分的に (場合と同様、コント ローラーを保持している) の手の閉じるときに、"forward"チューブを通じて非 thumb 指によって形成されるポイントの半径。</span><span class="sxs-lookup"><span data-stu-id="3da0b-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="3da0b-195">**軸の向きを握って**:右と前方参照の定義が含まれるアップ軸。</span><span class="sxs-lookup"><span data-stu-id="3da0b-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="3da0b-196">グリップの姿勢をベンダー間入力のいずれかの Unity の API を通じてアクセスできます (*[XR します。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)します。GetLocalPosition/Rotation*) または Windows MR 固有 API (*sourceState.sourcePose.TryGetPosition/Rotation*、データを要求して発生し得る、**グリップ**ノード)。</span><span class="sxs-lookup"><span data-stu-id="3da0b-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="3da0b-197">ポインターの姿勢</span><span class="sxs-lookup"><span data-stu-id="3da0b-197">Pointer pose</span></span>

<span data-ttu-id="3da0b-198">**ポインター姿勢**フォワード指し示すコント ローラーの先端を表します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="3da0b-199">システム指定のポインターの姿勢はしたら、最適な raycast に使用**コント ローラー モデル自体のレンダリング**します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="3da0b-200">仮想の銃など、コント ローラーの代わりにその他の仮想オブジェクトをレンダリングする場合は光線ガンのアプリで定義されたモデルの軸に沿って移動するなど、その仮想オブジェクトの最も自然なレイでポイントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3da0b-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="3da0b-201">仮想オブジェクトと物理のコント ローラーではないユーザーが表示できるため、仮想オブジェクトでポイントがあります、アプリを使用してこれらのより自然です。</span><span class="sxs-lookup"><span data-stu-id="3da0b-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="3da0b-202">現時点では、ポインターの姿勢は Windows MR 固有の API を介してのみで使用できる*sourceState.sourcePose.TryGetPosition/Rotation*で渡し*InteractionSourceNode.Pointer*として、引数。</span><span class="sxs-lookup"><span data-stu-id="3da0b-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="3da0b-203">コント ローラーの状態の追跡</span><span class="sxs-lookup"><span data-stu-id="3da0b-203">Controller tracking state</span></span>

<span data-ttu-id="3da0b-204">ヘッドセットなど、Windows Mixed Reality モーションのコント ローラーの外部の追跡のセンサーのセットアップは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="3da0b-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="3da0b-205">代わりに、コント ローラーは、ヘッドセット自体のセンサーによって追跡されます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="3da0b-206">場合は、ユーザーは、ヘッドセットのビューのフィールドからコント ローラーを移動、ほとんどの場合 Windows 引き続きコント ローラーの位置を推測し、アプリに提供されます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="3da0b-207">ときに、コント ローラーの位置を正確度のおおよその位置にドロップは、十分な時間のビジュアルの追跡、コント ローラーを失いました。</span><span class="sxs-lookup"><span data-stu-id="3da0b-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="3da0b-208">この時点では、システムは、本文ロックをコント ローラーをユーザーに、その内部方位センサーを使用して、コント ローラーの場合は true。 向きを引き続き公開中に移動する場合に、ユーザーの位置を追跡します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="3da0b-209">ポイントし、UI 要素をアクティブ化するコント ローラーを使用する多くのアプリが、ユーザーのルーティング グループおおよその精度で通常どおり操作できます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="3da0b-210">これを理解する最善の方法は、自分で試すです。</span><span class="sxs-lookup"><span data-stu-id="3da0b-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="3da0b-211">さまざまな追跡の状態の間でアニメーション コント ローラーで動作する没入型のコンテンツの例では、このビデオをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3da0b-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="3da0b-212">明示的に状態の追跡についての考え方</span><span class="sxs-lookup"><span data-stu-id="3da0b-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="3da0b-213">位置に応じて異なる状態の追跡を処理するアプリがさらに可能性がありなど、コント ローラーの状態のプロパティを検査*SourceLossRisk*と*PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="3da0b-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="3da0b-214">状態の追跡</span><span class="sxs-lookup"><span data-stu-id="3da0b-214">Tracking state</span></span> </th><th> <span data-ttu-id="3da0b-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="3da0b-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="3da0b-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="3da0b-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="3da0b-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="3da0b-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="3da0b-218"><b>高精度</b> </span><span class="sxs-lookup"><span data-stu-id="3da0b-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="3da0b-219">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="3da0b-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="3da0b-220">高</span><span class="sxs-lookup"><span data-stu-id="3da0b-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="3da0b-221">true</span><span class="sxs-lookup"><span data-stu-id="3da0b-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-222"><b>高精度 (損失の危険)</b> </span><span class="sxs-lookup"><span data-stu-id="3da0b-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="3da0b-223">== 1.0</span><span class="sxs-lookup"><span data-stu-id="3da0b-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="3da0b-224">高</span><span class="sxs-lookup"><span data-stu-id="3da0b-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="3da0b-225">true</span><span class="sxs-lookup"><span data-stu-id="3da0b-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-226"><b>おおよその精度</b> </span><span class="sxs-lookup"><span data-stu-id="3da0b-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="3da0b-227">== 1.0</span><span class="sxs-lookup"><span data-stu-id="3da0b-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="3da0b-228">Approximate</span><span class="sxs-lookup"><span data-stu-id="3da0b-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="3da0b-229">true</span><span class="sxs-lookup"><span data-stu-id="3da0b-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3da0b-230"><b>位置</b> </span><span class="sxs-lookup"><span data-stu-id="3da0b-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="3da0b-231">== 1.0</span><span class="sxs-lookup"><span data-stu-id="3da0b-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="3da0b-232">Approximate</span><span class="sxs-lookup"><span data-stu-id="3da0b-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="3da0b-233">false</span><span class="sxs-lookup"><span data-stu-id="3da0b-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="3da0b-234">これらのアニメーション コント ローラー追跡状態の定義は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3da0b-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="3da0b-235">**高精度は:** ヘッドセットのビューのフィールド内のモーション コント ローラーは、中には、高精度の位置、ビジュアルの追跡に基づく一般に提供します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="3da0b-236">注移動コント ローラーを一時的にビューのフィールドのままにヘッドセット センサーから一時的に隠されている (などによって、ユーザーの一方) を返すコント ローラーの慣性による追跡に基づく、短時間、高精度ポーズは引き続き自体。</span><span class="sxs-lookup"><span data-stu-id="3da0b-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="3da0b-237">**(データが失われる危険性) が高精度は:** ユーザーは、過去のヘッドセットの視野の edge モーション コント ローラーを移動したとき、ヘッドセットすぐにできなくコント ローラーの位置を視覚的に追跡するためにします。</span><span class="sxs-lookup"><span data-stu-id="3da0b-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="3da0b-238">アプリが、コント ローラーが達したらこの FOV 境界を見ることによって、 **SourceLossRisk** 1.0 に到達します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="3da0b-239">その時点では、アプリは、コント ローラーのジェスチャを非常に高品質なポーズの流れを必要とするを一時停止する選択できます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="3da0b-240">**近似精度は:** ときに、コント ローラーの位置を正確度のおおよその位置にドロップは、十分な時間のビジュアルの追跡、コント ローラーを失いました。</span><span class="sxs-lookup"><span data-stu-id="3da0b-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="3da0b-241">この時点では、システムは、本文ロックをコント ローラーをユーザーに、その内部方位センサーを使用して、コント ローラーの場合は true。 向きを引き続き公開中に移動する場合に、ユーザーの位置を追跡します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="3da0b-242">ポイントし、UI 要素をアクティブ化するコント ローラーを使用する多くのアプリは、ユーザーのルーティング グループおおよその精度で通常 while として動作できます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="3da0b-243">やや入力要件がアプリからこのドロップを理解することもできます**高**精度**Approximate**精度を調べることによって、 **PositionAccuracy**プロパティのこの期間中に画面外のターゲットについて、ユーザー寛大な hitbox を提供する例です。</span><span class="sxs-lookup"><span data-stu-id="3da0b-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="3da0b-244">**位置:** コント ローラーは、おおよその精度で長時間動作、中に場合があります、システムを知っていることも、本文ロック位置が意味のある現時点で。</span><span class="sxs-lookup"><span data-stu-id="3da0b-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="3da0b-245">など、コント ローラーだけを有効にする可能性がありますことはありませんされてまたは計測される視覚的に、ユーザーが、他のユーザーによってピックアップされるコント ローラーを設定します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="3da0b-246">これらのタイミングで、システムが提供しないアプリに任意の位置と*TryGetPosition*は false を返します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="3da0b-247">一般的な Unity Api (Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="3da0b-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="3da0b-248">\**名前空間:\*\*\*UnityEngine*, *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="3da0b-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="3da0b-249">**型**:*Input*, *XR.InputTracking*</span><span class="sxs-lookup"><span data-stu-id="3da0b-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="3da0b-250">Unity は、現在の [全般] を使用して*Input.GetButton/Input.GetAxis*の入力を公開する Api [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)、 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)と Windows Mixed Reality を含む手およびモーションのコント ローラー。</span><span class="sxs-lookup"><span data-stu-id="3da0b-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="3da0b-251">場合は、アプリでは、これらの Api を使用して、入力、Windows Mixed Reality を含め、複数の XR Sdk 間で簡単にアニメーション コント ローラーをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="3da0b-252">論理のボタンの押下状態の取得</span><span class="sxs-lookup"><span data-stu-id="3da0b-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="3da0b-253">一般的な Unity 入力 Api を使用する通常から始めますボタンと軸での論理名を接続、 [Unity 入力マネージャー](https://docs.unity3d.com/Manual/ConventionalGameInput.html)、ボタンまたは軸の Id をそれぞれの名前にバインドします。</span><span class="sxs-lookup"><span data-stu-id="3da0b-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="3da0b-254">そのボタン/軸の論理名を参照するコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="3da0b-255">たとえば、送信アクションを左側のモーション コント ローラーのトリガー ボタンをマップするに移動**編集 > プロジェクトの設定 > 入力**Unity 内で送信セクション 軸のプロパティ を展開します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="3da0b-256">変更、**正ボタン**または**Alt 正ボタン**プロパティを読み取る**ジョイスティック ボタン 14**、次のように。</span><span class="sxs-lookup"><span data-stu-id="3da0b-256">Change the **Postive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="3da0b-257">![Unity の InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="3da0b-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="3da0b-258">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="3da0b-258">*Unity InputManager*</span></span>

<span data-ttu-id="3da0b-259">送信アクションを使用して、スクリプトをチェックし、 *Input.GetButton*:</span><span class="sxs-lookup"><span data-stu-id="3da0b-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="3da0b-260">変更することより論理的ボタンを追加することができます、**サイズ**のプロパティの **軸**します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="3da0b-261">直接物理ボタンの押下状態の取得</span><span class="sxs-lookup"><span data-stu-id="3da0b-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="3da0b-262">アクセスすることもボタン手動で、その完全修飾名を使用して*Input.GetKey*:</span><span class="sxs-lookup"><span data-stu-id="3da0b-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="3da0b-263">手動またはモーション コント ローラーの姿勢を取得します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="3da0b-264">位置と、コント ローラーの回転にアクセスすることができますを使用して*XR します。InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="3da0b-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="3da0b-265">注 (ユーザーは、コント ローラーを保持) コント ローラーのグリップの姿勢を表すは剣またはユーザーの手の形、またはコント ローラー自体のモデルでガンをレンダリングするために便利です。</span><span class="sxs-lookup"><span data-stu-id="3da0b-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="3da0b-266">このグリップ ポーズと (コント ローラーのヒントを指している) ポインター姿勢間のリレーションシップは、コント ローラー間で異なる場合がありますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3da0b-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="3da0b-267">この時点で、コント ローラーのポインターの姿勢にアクセスする MR 固有の入力では、以下のセクションで説明されている API を通じて実現できる、のみできます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="3da0b-268">Windows 固有の Api (XR します。WSA します。入力)</span><span class="sxs-lookup"><span data-stu-id="3da0b-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="3da0b-269">\**名前空間:\*\*\*UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="3da0b-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="3da0b-270">**型**:*InteractionManager*、 *InteractionSourceState*、 *InteractionSource*、 *InteractionSourceProperties*、 *InteractionSourceKind*、 *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="3da0b-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="3da0b-271">Windows に固有の空間入力 Api を使用して選択できます (HoloLens) 用の Windows Mixed Reality 手入力およびモーションのコント ローラーの詳細情報を取得する、 *UnityEngine.XR.WSA.Input*名前空間。</span><span class="sxs-lookup"><span data-stu-id="3da0b-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="3da0b-272">位置の精度などの追加情報やハンドと離れているコント ローラーに指示することができます、ソースの種類にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="3da0b-273">手およびモーションのコント ローラーの状態のポーリング</span><span class="sxs-lookup"><span data-stu-id="3da0b-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="3da0b-274">各相互作用ソース (手動またはモーションのコント ローラー) を使用するため、このフレームの状態をポーリングすることができます、 *GetCurrentReading*メソッド。</span><span class="sxs-lookup"><span data-stu-id="3da0b-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="3da0b-275">各*InteractionSourceState*取得したバックアップは現在時点での相互作用ソースを表します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="3da0b-276">*InteractionSourceState*などの情報を公開します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="3da0b-277">これは、[種類押すの](motion-controllers.md)(選択/メニュー/理解/タッチパッド/スティック) が発生しています。</span><span class="sxs-lookup"><span data-stu-id="3da0b-277">Which [kinds of presses](motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="3da0b-278">アニメーション コント ローラー、このようなタッチパッド スティックの XY 座標やタッチされた状態に固有の他のデータ</span><span class="sxs-lookup"><span data-stu-id="3da0b-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* <span data-ttu-id="3da0b-279">かどうか、ソースは、手動またはモーション コント ローラーを把握する InteractionSourceKind</span><span class="sxs-lookup"><span data-stu-id="3da0b-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="3da0b-280">順方向予測レンダリング ポーズのポーリング</span><span class="sxs-lookup"><span data-stu-id="3da0b-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="3da0b-281">ハンドとコント ローラーからの相互作用のソース データのポーリングをするときに取得することはこのフレームの光子は、ユーザーの目に到達時間でしばらくの間、順方向予測ポーズにします。</span><span class="sxs-lookup"><span data-stu-id="3da0b-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="3da0b-282">これらの前方予測ポーズに適して**レンダリング**コント ローラーまたは、保持されているオブジェクトの各フレーム。</span><span class="sxs-lookup"><span data-stu-id="3da0b-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="3da0b-283">指定したキーを押してを対象とするまたはコント ローラーでリリースする場合は、履歴イベントを以下に示す Api を使用する場合、最も正確ながあります。</span><span class="sxs-lookup"><span data-stu-id="3da0b-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="3da0b-284">この現在のフレームの前方予測ヘッド姿勢を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="3da0b-285">ソース姿勢で、この場合に便利ですが**レンダリング**カーソルを指定したキーを押してやリリースを対象とする履歴イベントを以下に示す Api を使用する場合は、最も正確はできます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="3da0b-286">相互作用のソース イベントの処理</span><span class="sxs-lookup"><span data-stu-id="3da0b-286">Handling interaction source events</span></span>

<span data-ttu-id="3da0b-287">履歴姿勢の正確なデータが発生したときに、入力イベントを処理するためには、ポーリングではなく相互作用ソース イベントを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="3da0b-288">相互作用のソースのイベントを処理するには。</span><span class="sxs-lookup"><span data-stu-id="3da0b-288">To handle interaction source events:</span></span>
* <span data-ttu-id="3da0b-289">登録、 *InteractionManager*入力イベント。</span><span class="sxs-lookup"><span data-stu-id="3da0b-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="3da0b-290">興味のある操作イベントの種類ごとには、サブスクライブする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3da0b-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* <span data-ttu-id="3da0b-291">イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-291">Handle the event.</span></span> <span data-ttu-id="3da0b-292">相互作用のイベントにサブスクライブしていると該当する場合に、コールバックが返されます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="3da0b-293">*SourcePressed*例では、これになります、ソースが検出された後、リリースまたは紛失前にします。</span><span class="sxs-lookup"><span data-stu-id="3da0b-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="3da0b-294">イベントの処理を停止する方法</span><span class="sxs-lookup"><span data-stu-id="3da0b-294">How to stop handling an event</span></span>

<span data-ttu-id="3da0b-295">イベントに興味のある不要になったか、イベントにサブスクライブしているオブジェクトを破棄するときに、イベントの処理を停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3da0b-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="3da0b-296">イベントの処理を停止するには、購読を解除するイベントです。</span><span class="sxs-lookup"><span data-stu-id="3da0b-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="3da0b-297">相互作用のソース イベントの一覧</span><span class="sxs-lookup"><span data-stu-id="3da0b-297">List of interaction source events</span></span>

<span data-ttu-id="3da0b-298">ソース イベントの使用可能な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3da0b-298">The available interaction source events are:</span></span>
* <span data-ttu-id="3da0b-299">*InteractionSourceDetected* (ソースがアクティブになります)</span><span class="sxs-lookup"><span data-stu-id="3da0b-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="3da0b-300">*InteractionSourceLost* (非アクティブになります)</span><span class="sxs-lookup"><span data-stu-id="3da0b-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="3da0b-301">*InteractionSourcePressed* (タップ、ボタンの押下、または"Select"発音)</span><span class="sxs-lookup"><span data-stu-id="3da0b-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="3da0b-302">*InteractionSourceReleased* (タップして、ボタンが解放された、または"Select"発音の最後の終了)</span><span class="sxs-lookup"><span data-stu-id="3da0b-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="3da0b-303">*InteractionSourceUpdated* (移動またはいくつかの状態を変更するそれ以外の場合)</span><span class="sxs-lookup"><span data-stu-id="3da0b-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="3da0b-304">イベント キーを押してまたはリリースを最も正確に一致する履歴の対象とすることを</span><span class="sxs-lookup"><span data-stu-id="3da0b-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="3da0b-305">前に説明したポーリング Api では、順方向予測ポーズ アプリを提供します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="3da0b-306">これらの予測が発生は、コント ローラーまたは仮想のハンドヘルド オブジェクトのレンダリングに最適ですが、将来ポーズが対象とする、2 つの主な理由のために最適でないです。</span><span class="sxs-lookup"><span data-stu-id="3da0b-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="3da0b-307">ユーザーは、コント ローラー上のボタンを押すと、ありますワイヤレスの待機時間の約 20 ミリ秒遅らせます Bluetooth 経由で、システムは、キーを押してを受信する前に。</span><span class="sxs-lookup"><span data-stu-id="3da0b-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="3da0b-308">次を使用する場合前方予測の姿勢では、ある前方の予測のもう 1 つの 10-20 ミリ秒に適用される現在のフレームの光子は、ユーザーの目に到達する時間を対象します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="3da0b-309">つまり、ポーリングは、ソースの姿勢をまたはヘッドからユーザーの head と手実際にが、キーを押してまたはリリースが発生したときに 30 40 転送が発生します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="3da0b-310">HoloLens 手入力する場合、ワイヤレス通信の遅延はありませんは、キーを押してを検出するような処理の遅延です。</span><span class="sxs-lookup"><span data-stu-id="3da0b-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="3da0b-311">手動またはコント ローラーのキーを押してのユーザーの本来の目的に基づいてターゲット正確には、履歴ソース姿勢またはからヘッドの姿勢を使用する必要があります*InteractionSourcePressed*または*InteractionSourceReleased*入力イベント。</span><span class="sxs-lookup"><span data-stu-id="3da0b-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="3da0b-312">対象に、キーを押してまたはユーザーの頭またはそのコント ローラーからデータを履歴姿勢でリリースできます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="3da0b-313">ジェスチャまたはコント ローラーを押したときの時点でヘッド姿勢が発生したために使用できる**を対象とする**、ユーザーが何を確認する[gazing](gaze.md)で。</span><span class="sxs-lookup"><span data-stu-id="3da0b-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](gaze.md) at:</span></span>

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

* <span data-ttu-id="3da0b-314">アニメーション コント ローラーを押したときの時点でソース姿勢が発生したために使用できる**を対象とする**をどのようなユーザー指定のコント ローラーを決定します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="3da0b-315">これをキーを押してが発生したコント ローラーの状態となります。</span><span class="sxs-lookup"><span data-stu-id="3da0b-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="3da0b-316">コント ローラー自体をレンダリングする場合は、グリップ姿勢で、ユーザーが検討事項のコント ローラーを表示する自然なヒントからターゲット光線を撮影するではなく、ポインターの姿勢を要求できます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="3da0b-317">イベント ハンドラーの例</span><span class="sxs-lookup"><span data-stu-id="3da0b-317">Event handlers example</span></span>

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="3da0b-318">高度な複合 gesture Api (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="3da0b-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="3da0b-319">\**名前空間:\*\*\*UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="3da0b-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="3da0b-320">**型**:*GestureRecognizer*、 *GestureSettings*、 *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="3da0b-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="3da0b-321">アプリは、空間の入力ソース、タップ、保持、操作、およびナビゲーションのジェスチャのより高度な複合ジェスチャを認識することができますも。</span><span class="sxs-lookup"><span data-stu-id="3da0b-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="3da0b-322">両方でこれらの複合ジェスチャを認識できる[手](gestures.md)と[コント ローラーのモーション](motion-controllers.md)GestureRecognizer を使用します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-322">You can recognize these composite gestures across both [hands](gestures.md) and [motion controllers](motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="3da0b-323">GestureRecognizer 上の各ジェスチャ イベントは、イベントの時刻に、入力としてターゲット ヘッド レイ、SourceKind を提供します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="3da0b-324">いくつかのイベントは、追加のコンテキスト固有の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="3da0b-325">ジェスチャ レコグナイザーを使用するジェスチャをキャプチャするために必要ないくつかの手順のみがあります。</span><span class="sxs-lookup"><span data-stu-id="3da0b-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="3da0b-326">新しいジェスチャ レコグナイザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="3da0b-327">ウォッチするジェスチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="3da0b-328">これらのジェスチャのイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="3da0b-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="3da0b-329">ジェスチャのキャプチャを開始します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="3da0b-330">新しいジェスチャ レコグナイザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="3da0b-331">使用する、 *GestureRecognizer*、作成する必要があります、 *GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="3da0b-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="3da0b-332">ウォッチするジェスチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="3da0b-333">使用して興味があるジェスチャを指定*SetRecognizableGestures()*:</span><span class="sxs-lookup"><span data-stu-id="3da0b-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="3da0b-334">これらのジェスチャのイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="3da0b-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="3da0b-335">興味のあるジェスチャのイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="3da0b-335">Subscribe to events for the gestures you are interested in.</span></span>

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
><span data-ttu-id="3da0b-336">移動および操作のジェスチャのインスタンスで相互に排他的な*GestureRecognizer*します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="3da0b-337">ジェスチャのキャプチャを開始します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-337">Start capturing gestures</span></span>

<span data-ttu-id="3da0b-338">既定で、 *GestureRecognizer*まで入力を監視しません*StartCapturingGestures()* が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="3da0b-339">後に、ジェスチャ イベントを生成することことができます*StopCapturingGestures()* 入力は、フレーム前に実行されている場合に呼び出されますが、 *StopCapturingGestures()* が処理されました。</span><span class="sxs-lookup"><span data-stu-id="3da0b-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="3da0b-340">*GestureRecognizer*と覚えておいてくださいかどうかに、ジェスチャは実際に発生した、previou フレームの間にオンまたはオフをだとためが開始する信頼性の高いを対象とするこのフレームの視線の先に基づくジェスチャの監視を停止します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-340">The *GestureRecognizer* will remember whether it was on or off during the previou frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="3da0b-341">ジェスチャのキャプチャを停止します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-341">Stop capturing gestures</span></span>

<span data-ttu-id="3da0b-342">ジェスチャ認識を停止します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="3da0b-343">ジェスチャ レコグナイザーを削除します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="3da0b-344">破棄する前にサブスクライブされたイベントの登録を解除してください、 *GestureRecognizer*オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3da0b-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="3da0b-345">Unity でモーション コント ローラー モデルを表示</span><span class="sxs-lookup"><span data-stu-id="3da0b-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="3da0b-346">![アニメーション コント ローラー モデルと teleportation](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="3da0b-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="3da0b-347">*アニメーション コント ローラー モデルと teleportation*</span><span class="sxs-lookup"><span data-stu-id="3da0b-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="3da0b-348">物理コント ローラーを保持するいると、ユーザーおよびのさまざまなボタンが押されているように明確に一致するアプリでのモーション コントローラを表示するために使用することができます、 **MotionController プレハブ**で、 [Mixed Reality ツールキット](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="3da0b-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="3da0b-349">このプレハブは、システムのインストールされているアニメーション コント ローラー ドライバーから動的に実行時に正しい glTF モデルを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="3da0b-350">インポートして手動で、エディターで、アプリは、ユーザーに、現在および将来のコント ローラーの 3D モデルを物理的に正確に表示されるよう必要があるのではなくするこれらのモデルを動的に読み込むことが重要です。</span><span class="sxs-lookup"><span data-stu-id="3da0b-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="3da0b-351">に従って、 [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) Mixed Reality Toolkit をダウンロードして、Unity プロジェクトに追加する手順。</span><span class="sxs-lookup"><span data-stu-id="3da0b-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="3da0b-352">カメラを交換した場合、 *MixedRealityCameraParent* prefab 概要手順の一環として、する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="3da0b-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="3da0b-353">そのプレハブには、アニメーション コント ローラーの表示が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="3da0b-354">それ以外の場合、追加*Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab*プロジェクト ウィンドウからシーンにします。</span><span class="sxs-lookup"><span data-stu-id="3da0b-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="3da0b-355">親オブジェクトの子としてプレハブを使用することときに中心にカメラを移動する追加たい、シーン内でユーザー teleports コント ローラーがユーザーと共に取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3da0b-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="3da0b-356">アプリが teleporting を伴わない場合、シーンのルートにある、プレハブを追加します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="3da0b-357">オブジェクトをスローします。</span><span class="sxs-lookup"><span data-stu-id="3da0b-357">Throwing objects</span></span>

<span data-ttu-id="3da0b-358">困難な問題は、仮想現実でのオブジェクトをスローし、最初に見えるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="3da0b-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="3da0b-359">同様に物理的に最もベースの対話、予期しない方法でゲームの動作でスローするときに、それがすぐにわかる immersion を中断します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="3da0b-360">物理的に正しいのスロー動作を表し、当社のプラットフォームをお客様と共有したいに更新を有効になっているいくつかのガイドラインを思い付く方法について深く考える時間がいくつかを費やしてきました。</span><span class="sxs-lookup"><span data-stu-id="3da0b-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="3da0b-361">実装をスローすることをお勧めする方法の例が見つかります[ここ](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="3da0b-362">このサンプルでは、次の 4 つのガイドラインに従います。</span><span class="sxs-lookup"><span data-stu-id="3da0b-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="3da0b-363">**コント ローラーを使用して、 *velocity*位置ではなく**します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="3da0b-364">Windows の 11 月更新での動作が変更を導入しましたの場合に、 ['およそ ' の位置指定の追跡状態](motion-controllers.md#controller-tracking-state)します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="3da0b-365">、この状態のときに速度については、コント ローラーを高い精度で、位置が高精度よりも長くは多くの場合と考えています限りの報告されることを続けます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="3da0b-366">**組み込む、*角速度*コント ローラーの**します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="3da0b-367">このロジックはすべてに含まれる、`throwing.cs`ファイル、`GetThrownObjectVelAngVel`上のリンクから、パッケージ内の静的メソッド。</span><span class="sxs-lookup"><span data-stu-id="3da0b-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="3da0b-368">角度の速度を保護すると、スローされたオブジェクトとしてスローの時点では、同じ角度の速度を維持する必要があります。 `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="3da0b-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="3da0b-369">スローされたオブジェクトの重心はありませんがグリップ姿勢の原点とが異なる速度、コント ローラーのユーザーの参照のフレームで可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3da0b-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="3da0b-370">この方法で提供されたオブジェクトの速度の部分では、コント ローラーの原点の周囲にスローされたオブジェクトの重心の正接瞬間的な速度です。</span><span class="sxs-lookup"><span data-stu-id="3da0b-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="3da0b-371">この正接の速度は、コント ローラーの配信元とスローされるオブジェクトの重心の間の距離を表すベクトルで、コント ローラーの角度の速度のクロス積です。</span><span class="sxs-lookup"><span data-stu-id="3da0b-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. <span data-ttu-id="3da0b-372">スローされたオブジェクトの合計のベロシティは、コント ローラーの速度と考えたこの速度の合計ではそのためです。 `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="3da0b-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="3da0b-373">**特に注意、*時間*速度を適用する**します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="3da0b-374">ボタンが押されたときに、オペレーティング システムに Bluetooth を通じてバブルアップするには、そのイベントの最大 20 ミリ秒かかります。</span><span class="sxs-lookup"><span data-stu-id="3da0b-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="3da0b-375">つまりからコント ローラーの状態変更のポーリングが押されていない状態に押された状態またはその逆を取得するコント ローラーの姿勢情報は、この状態の変更の前になります実際に場合。</span><span class="sxs-lookup"><span data-stu-id="3da0b-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="3da0b-376">さらに、API、ポーリングによって提示されるコント ローラーの姿勢は、転送、フレームが表示されます、20 ミリ秒の詳細については、今後ある可能性がある時に可能性の高い姿勢を反映するように予測します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="3da0b-377">適しています。*レンダリング*、オブジェクトが保持されていますが、時間の問題をさらに大きく*を対象とする*オブジェクトのスローを離したよう、今のところ、軌道を計算します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="3da0b-378">さいわい、Unity のイベントのような場合は、11 月の更新で*InteractionSourcePressed*または*InteractionSourceReleased*送信されると、状態には、履歴の姿勢データが含まれていますから戻るときに、ボタン実際には、押された状態またはリリースしました。</span><span class="sxs-lookup"><span data-stu-id="3da0b-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="3da0b-379">最も正確なコント ローラーの表示とスロー時に対象とするコント ローラーを取得するには、適切なポーリングとをイベントを使用する必要があります正しく。</span><span class="sxs-lookup"><span data-stu-id="3da0b-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="3da0b-380">**コント ローラーのレンダリング**フレームごとに、アプリは、コント ローラーを配置する必要があります*GameObject*前方予測コント ローラーで、現在のフレームの photon 時間の発生し得る。</span><span class="sxs-lookup"><span data-stu-id="3da0b-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="3da0b-381">ポーリング Api などの Unity からこのデータを取得する*[XR します。InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* または *[XR します。WSA します。Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="3da0b-382">**コント ローラーを対象とする**キーを押してまたはリリース時に、アプリが raycast をする必要があり、そのキーを押すか、リリース イベントの履歴のコント ローラーの姿勢に基づく軌道を計算します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="3da0b-383">ように Unity イベント Api からこのデータを取得する *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="3da0b-384">**グリップの姿勢を使用して、** します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-384">**Use the grip pose**.</span></span> <span data-ttu-id="3da0b-385">グリップの姿勢、いないポインター姿勢を基準とした角度の速度と速度が報告されます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="3da0b-386">今後の Windows 更新プログラムを向上させるために引き続きをスローし、ことの詳細については、ここに検出されることができます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="accelerate-development-with-mixed-reality-toolkit"></a><span data-ttu-id="3da0b-387">Mixed Reality Toolkit を使用した開発を高速化します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-387">Accelerate development with Mixed Reality Toolkit</span></span>

<span data-ttu-id="3da0b-388">InputManager と Unity で MotionController に関する 2 つの例のシーンがあります。</span><span class="sxs-lookup"><span data-stu-id="3da0b-388">There are two example scenes about InputManager and MotionController in Unity.</span></span> <span data-ttu-id="3da0b-389">これらのシーンの中から MRTK の InputManager を使用して、アニメーション コント ローラー ボタンからデータ イベントの処理を活用する方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-389">Through these scenes, you can learn how to use MRTK's InputManager and access data handle events from the motion controller buttons.</span></span>

- [<span data-ttu-id="3da0b-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="3da0b-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [<span data-ttu-id="3da0b-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span><span class="sxs-lookup"><span data-stu-id="3da0b-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [<span data-ttu-id="3da0b-392">README ファイルの技術的な詳細</span><span class="sxs-lookup"><span data-stu-id="3da0b-392">Technical details README File</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

<span data-ttu-id="3da0b-393">![入力例 MRTK シーン](images/MRTK_ExampleScene_Input.png)</span><span class="sxs-lookup"><span data-stu-id="3da0b-393">![Input example scenes in MRTK](images/MRTK_ExampleScene_Input.png)</span></span><br>
<span data-ttu-id="3da0b-394">*入力例 MRTK シーン*</span><span class="sxs-lookup"><span data-stu-id="3da0b-394">*Input example scenes in MRTK*</span></span>

### <a name="automatic-scene-setup"></a><span data-ttu-id="3da0b-395">自動のシーンのセットアップ</span><span class="sxs-lookup"><span data-stu-id="3da0b-395">Automatic scene setup</span></span>

<span data-ttu-id="3da0b-396">インポートするときに[MRTK が Unity パッケージをリリース](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)からプロジェクトを複製するか、 [GitHub リポジトリ](https://github.com/Microsoft/MixedRealityToolkit-Unity)Unity で新しいメニュー ' Mixed Reality Toolkit' を検索します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-396">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="3da0b-397">[構成] メニューで、' Mixed Reality シーン設定の適用 ' メニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-397">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="3da0b-398">既定のカメラを削除し、基本コンポーネントを追加します。 これをクリックすると [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)、 [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)、および[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-398">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="3da0b-399">![シーンのセットアップの MRTK メニュー](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="3da0b-399">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="3da0b-400">*シーンのセットアップの MRTK メニュー*</span><span class="sxs-lookup"><span data-stu-id="3da0b-400">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="3da0b-401">![MRTK で自動シーンのセットアップ](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="3da0b-401">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="3da0b-402">*MRTK で自動シーンのセットアップ*</span><span class="sxs-lookup"><span data-stu-id="3da0b-402">*Automatic scene setup in MRTK*</span></span>

### <a name="mixedrealitycamera-prefab"></a><span data-ttu-id="3da0b-403">MixedRealityCamera プレハブ</span><span class="sxs-lookup"><span data-stu-id="3da0b-403">MixedRealityCamera prefab</span></span>

<span data-ttu-id="3da0b-404">これらのプロジェクト パネルから手動で追加できます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-404">You can also manually add these from the project panel.</span></span> <span data-ttu-id="3da0b-405">プレハブとしてこれらのコンポーネントを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-405">You can find these components as prefabs.</span></span> <span data-ttu-id="3da0b-406">検索する場合に**MixedRealityCamera**、2 つの異なるカメラ プレハブを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-406">When you search **MixedRealityCamera**, you will be able to see two different camera prefabs.</span></span> <span data-ttu-id="3da0b-407">違いは、 **MixedRealityCamera**はカメラのみプレハブは、 **MixedRealityCameraParent** Teleportation、モーションなどイマーシブ ヘッドセットの追加のコンポーネントが含まれていますコント ローラーと、境界。</span><span class="sxs-lookup"><span data-stu-id="3da0b-407">The difference is, **MixedRealityCamera** is the camera only prefab whereas, **MixedRealityCameraParent** includes additional components for the immersive headsets such as Teleportation, Motion Controller and, Boundary.</span></span>

<span data-ttu-id="3da0b-408">![MRTK でカメラのプレハブ](images/MRTK_HowTo_Input2.png)</span><span class="sxs-lookup"><span data-stu-id="3da0b-408">![Camera prefabs in MRTK](images/MRTK_HowTo_Input2.png)</span></span><br>
<span data-ttu-id="3da0b-409">*MRTK でカメラのプレハブ*</span><span class="sxs-lookup"><span data-stu-id="3da0b-409">*Camera prefabs in MRTK*</span></span>

<span data-ttu-id="3da0b-410">**MixedRealtyCamera** HoloLens とイマーシブ ヘッドセットの両方をサポートします。</span><span class="sxs-lookup"><span data-stu-id="3da0b-410">**MixedRealtyCamera** supports both HoloLens and immersive headset.</span></span> <span data-ttu-id="3da0b-411">デバイスの種類を検出し、フラグをクリアし、スカイ ボックスなどのプロパティを最適化します。</span><span class="sxs-lookup"><span data-stu-id="3da0b-411">It detects the device type and optimizes the properties such as clear flags and Skybox.</span></span> <span data-ttu-id="3da0b-412">以下、アニメーション コント ローラー モデルでは、カスタムのカーソルなどをカスタマイズでき、Floor、便利なプロパティの一部を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-412">Below you can find some of the useful properties you can customize such as custom Cursor, Motion Controller models, and Floor.</span></span>

<span data-ttu-id="3da0b-413">![カーソルと床面、モーションのコント ローラーのプロパティ](images/MRTK_HowTo_Input3.png)</span><span class="sxs-lookup"><span data-stu-id="3da0b-413">![Properties for the Motion controller, Cursor and Floor](images/MRTK_HowTo_Input3.png)</span></span><br>
<span data-ttu-id="3da0b-414">*カーソルと床面、モーションのコント ローラーのプロパティ*</span><span class="sxs-lookup"><span data-stu-id="3da0b-414">*Properties for the Motion controller, Cursor and Floor*</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="3da0b-415">チュートリアルの手順に従う</span><span class="sxs-lookup"><span data-stu-id="3da0b-415">Follow along with tutorials</span></span>

<span data-ttu-id="3da0b-416">ステップ バイ ステップのチュートリアルをより詳細なカスタマイズ例については、Mixed Reality Academy で使用できます。</span><span class="sxs-lookup"><span data-stu-id="3da0b-416">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="3da0b-417">MR 入力 211:ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="3da0b-417">MR Input 211: Gesture</span></span>](holograms-211.md)
- [<span data-ttu-id="3da0b-418">MR 入力 213:アニメーション コント ローラー</span><span class="sxs-lookup"><span data-stu-id="3da0b-418">MR Input 213: Motion controllers</span></span>](mixed-reality-213.md)

<span data-ttu-id="3da0b-419">[![MR 入力 213 - モーションのコント ローラー](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="3da0b-419">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="3da0b-420">*MR 入力 213 - モーションのコント ローラー*</span><span class="sxs-lookup"><span data-stu-id="3da0b-420">*MR Input 213 - Motion controller*</span></span>

## <a name="see-also"></a><span data-ttu-id="3da0b-421">関連項目</span><span class="sxs-lookup"><span data-stu-id="3da0b-421">See also</span></span>

* [<span data-ttu-id="3da0b-422">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="3da0b-422">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="3da0b-423">アニメーション コント ローラー</span><span class="sxs-lookup"><span data-stu-id="3da0b-423">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="3da0b-424">UnityEngine.XR.WSA.Input</span><span class="sxs-lookup"><span data-stu-id="3da0b-424">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="3da0b-425">UnityEngine.XR.InputTracking</span><span class="sxs-lookup"><span data-stu-id="3da0b-425">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="3da0b-426">MixedRealityToolkit Unity で InteractionInputSource.cs</span><span class="sxs-lookup"><span data-stu-id="3da0b-426">InteractionInputSource.cs in MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
