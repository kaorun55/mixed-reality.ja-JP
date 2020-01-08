---
title: MRTK 101-基本的な対話に Mixed Reality Toolkit Unity を使用する方法 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)
description: 基本的な対話に Mixed Reality Toolkit Unity を使用する方法 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens、MRTK、Mixed Reality Toolkit、Windows Mixed Reality、design、sample app、controls
ms.openlocfilehash: ad9d2755522c2610ae051fa61f96605e49404d2d
ms.sourcegitcommit: 5054f5c23965ce56599cb29ac9d9c6e48812dabd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623505"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="b6b83-104">MRTK 101: 基本的な対話に Mixed Reality Toolkit Unity を使用する方法 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)</span><span class="sxs-lookup"><span data-stu-id="b6b83-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="b6b83-106">MRTK を使用して、mixed reality で最も広く使用されている一般的な相互作用パターンを実現する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6b83-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="b6b83-107">Unity エディターで入力の相互作用をシミュレートする方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="b6b83-108">オブジェクトを取得および移動する方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-108">How to grab and move an object?</span></span>
- <span data-ttu-id="b6b83-109">オブジェクトのサイズを変更する方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-109">How to resize an object?</span></span>
- <span data-ttu-id="b6b83-110">有効桁数を使用してオブジェクトを移動または回転する方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="b6b83-111">オブジェクトを入力イベントに応答させる方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="b6b83-112">視覚的フィードバックを追加する方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-112">How to add visual feedback?</span></span>
- <span data-ttu-id="b6b83-113">オーディオフィードバックを追加する方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-113">How to add audio feedback?</span></span>
- <span data-ttu-id="b6b83-114">HoloLens 2 スタイルボタン prefabs の使用方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="b6b83-115">オブジェクトをフォローする方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-115">How to make an object follow you?</span></span>
- <span data-ttu-id="b6b83-116">オブジェクトをどのように表示するか</span><span class="sxs-lookup"><span data-stu-id="b6b83-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="b6b83-117">Unity エディターで入力の相互作用をシミュレートする方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="b6b83-118">MRTK は、エディター内入力のシミュレーションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b6b83-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="b6b83-119">Unity の [再生] ボタンをクリックしてシーンを実行するだけです。</span><span class="sxs-lookup"><span data-stu-id="b6b83-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="b6b83-120">入力をシミュレートするには、これらのキーを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6b83-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="b6b83-121">W、A、S、D キーを押して、カメラを移動します。</span><span class="sxs-lookup"><span data-stu-id="b6b83-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="b6b83-122">マウスの右ボタンを押したまま、マウスを動かして移動します。</span><span class="sxs-lookup"><span data-stu-id="b6b83-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="b6b83-123">シミュレートされたハンドを表示するには、スペースバー (右側) または左 Shift キー (左側) を押して、シミュレートされたハンドを保持します。 T キーまたは Y キーを押して、シミュレートされたハンドを回転します。</span><span class="sxs-lookup"><span data-stu-id="b6b83-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="b6b83-124">MRTK のドキュメントで入力シミュレーションの詳細を確認する</span><span class="sxs-lookup"><span data-stu-id="b6b83-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="b6b83-125">オブジェクトを取得および移動する方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-125">How to grab and move an object?</span></span>
<span data-ttu-id="b6b83-126">オブジェクトを grabbable にするには、次の2つのスクリプトを割り当てます。 ManipulationHandler.cs と NearInteractionGrabbable (トレーラー型の追跡入力を使用した直接グラブ) では、near と far の相互作用の両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b6b83-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="b6b83-127">オブジェクトを取得および移動するには、HoloLens 2 の手による追跡入力 (near)、ハンドレイ (遠く)、モーションコントローラーのビーム (遠く)、HoloLens を見つめたカーソル & エアタップ (遠く) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b6b83-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="b6b83-128">オブジェクトのサイズを変更する方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-128">How to resize an object?</span></span>
<span data-ttu-id="b6b83-129">ManipulationHandler.cs は、2つのを持つスケール/回転をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b6b83-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="b6b83-130">これは、HoloLens 2 の手入力、HoloLens 1 の宝石となるジェスチャ入力、Windows Mixed Reality のイマーシブヘッドセットのモーションコントローラー入力など、さまざまな入力の種類で機能します。</span><span class="sxs-lookup"><span data-stu-id="b6b83-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="b6b83-131">操作ハンドラーの詳細については、MRTK のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6b83-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="b6b83-132">有効桁数を使用してオブジェクトを移動または回転する方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="b6b83-133">BoundingBox.cs をオブジェクトに割り当てて、オブジェクトを拡大縮小および回転するためのインターフェイスである境界ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6b83-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="b6b83-134">既定では、HoloLens 1 スタイルの青いハンドルとワイヤが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="b6b83-135">HoloLens 2 のスタイル近接に基づくアニメーションハンドルを使用するには、prefabs と素材を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6b83-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="b6b83-136">構成の詳細については、[境界ボックスのドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)と BoundingBoxExamples シーンを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6b83-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="b6b83-137">詳細については、MRTK のドキュメントの境界ボックスに関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6b83-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="b6b83-138">オブジェクトを入力イベントに応答させる方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="b6b83-139">PointerHandler.cs をオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="b6b83-140">インスペクターでは、イベント Onポインタ Down ()、Onポインタ Up ()、Onポインターをクリックした ()、Onポインターをドラッグして ()、スクリプトでこれらのイベントを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="b6b83-141">入力システムの詳細については、MRTK のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6b83-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="b6b83-142">視覚的フィードバックを追加する方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-142">How to add visual feedback?</span></span>
<span data-ttu-id="b6b83-143">Interactable.cs をオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="b6b83-144">インスペクターで、新しいテーマを作成します。</span><span class="sxs-lookup"><span data-stu-id="b6b83-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="b6b83-145">対話型のテーマプロファイルを使用すると、利用可能なすべての入力対話状態に視覚的フィードバックを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="b6b83-146">対話型には、シェーダーのテーマを含むさまざまな種類のテーマが用意されています。これにより、相互作用状態ごとにシェーダーのプロパティを制御できます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="b6b83-147">対話型の詳細については、MRTK のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6b83-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="b6b83-148">視覚的なフィードバックのためのもう1つの重要な構成要素は、MRTK Standard Shader です。</span><span class="sxs-lookup"><span data-stu-id="b6b83-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="b6b83-149">MRTK Standard Shader を使用すると、ホバー光や近接光などの視覚的なフィードバック効果を簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="b6b83-150">MRTK Standard shader では Unity Standard shader よりも計算が大幅に減少するため、パフォーマンスに優れたエクスペリエンスを実現できます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="b6b83-151">新しい素材を作成し、シェーダー ' Mixed Reality Toolkit > Standard ' を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6b83-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="b6b83-152">または、MRTK Standard Shader を使用する既存のマテリアルの1つを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="b6b83-153">Mrtk のドキュメントの MRTK Standard Shader の詳細については、こちらを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6b83-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="b6b83-154">オーディオフィードバックを追加する方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-154">How to add audio feedback?</span></span>
<span data-ttu-id="b6b83-155">AudioSource をオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="b6b83-155">Add AudioSource to an object.</span></span> <span data-ttu-id="b6b83-156">次に、入力イベントを公開するスクリプト (例: Interactable.cs または PointerHandler.cs) で、オブジェクトをイベントに割り当て、AudioSource. PlayOneShot () を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6b83-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="b6b83-157">オーディオクリップを使用するか、MRTK のオーディオアセットから1つを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="b6b83-158">HoloLens 2 スタイルボタン prefabs の使用方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="b6b83-159">MRTK には、さまざまな種類の HoloLens 2 のシェル (OS) スタイルボタンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b6b83-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="b6b83-160">これにより、近接光、フィードバックの圧縮、ボタン画面に対する ripple 効果などの洗練されたビジュアルが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="b6b83-161">HoloLens 2 style pressable button prefab の1つをシーンにドラッグアンドドロップするだけです。</span><span class="sxs-lookup"><span data-stu-id="b6b83-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="b6b83-162">Prefab は、上記で導入された Interactable.cs を使用します。</span><span class="sxs-lookup"><span data-stu-id="b6b83-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="b6b83-163">対話型の OnClick () などの公開されたイベントを使用して、アクションをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="b6b83-164">詳細については、MRTK のドキュメントのボタン prefabs に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6b83-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="b6b83-165">オブジェクトをフォローする方法</span><span class="sxs-lookup"><span data-stu-id="b6b83-165">How to make an object follow you?</span></span>
<span data-ttu-id="b6b83-166">RadialView.cs スクリプトをオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="b6b83-167">これは、3D 空間でさまざまな種類のオブジェクトの配置を実現するための、ソルバースクリプトシリーズの一部です。</span><span class="sxs-lookup"><span data-stu-id="b6b83-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="b6b83-168">SolverHandler.cs が自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="b6b83-169">次に示すのは、HoloLens シェルの [スタート] メニューと同じように、"遅延した後の" タグの動作を実現するための、放射 Alview 構成の例です。</span><span class="sxs-lookup"><span data-stu-id="b6b83-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="b6b83-170">最小/最大距離および最小/最大ビューの角度を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="b6b83-171">次の例では、オブジェクトを 0.4 m と 0.8 m の範囲の15°以内に配置しています。</span><span class="sxs-lookup"><span data-stu-id="b6b83-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="b6b83-172">Lerp 時刻値を調整して、位置指定更新を高速または低速にします。</span><span class="sxs-lookup"><span data-stu-id="b6b83-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="b6b83-173">詳細については、MRTK のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6b83-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="b6b83-174">オブジェクトをどのように表示するか</span><span class="sxs-lookup"><span data-stu-id="b6b83-174">How to make an object face you?</span></span>
<span data-ttu-id="b6b83-175">Billboard.cs スクリプトをオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="b6b83-176">位置に関係なく、常に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="b6b83-177">[ピボット軸] オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b6b83-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="b6b83-178">Mixed reality のすばらしいエクスペリエンスを作成する準備はできましたか?</span><span class="sxs-lookup"><span data-stu-id="b6b83-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="b6b83-179">MRTK と mixed reality の詳細については、以下のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6b83-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="b6b83-180">執筆者紹介</span><span class="sxs-lookup"><span data-stu-id="b6b83-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="b6b83-181"><b>駐車中</b></span><span class="sxs-lookup"><span data-stu-id="b6b83-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="b6b83-182">UX デザイナーの @Microsoft</span><span class="sxs-lookup"><span data-stu-id="b6b83-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="b6b83-183">「</span><span class="sxs-lookup"><span data-stu-id="b6b83-183">See also</span></span>

* [<span data-ttu-id="b6b83-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="b6b83-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="b6b83-185">MRTK ドキュメントポータル</span><span class="sxs-lookup"><span data-stu-id="b6b83-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="b6b83-186">MRTK でのはじめに</span><span class="sxs-lookup"><span data-stu-id="b6b83-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="b6b83-187">HoloToolkit to MRTK 移植ガイドライン</span><span class="sxs-lookup"><span data-stu-id="b6b83-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
