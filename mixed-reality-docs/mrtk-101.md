---
title: MRTK 101 - 基本的な対話式操作に Mixed Reality Toolkit Unity を使用する方法 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)
description: 基本的な対話式操作に Mixed Reality Toolkit Unity を使用する方法 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, 設計, サンプル アプリ, コントロール
ms.localizationpriority: high
ms.openlocfilehash: 4564e7a0c6a717452effacae2587461fe283cf0b
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "79028312"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="9ee71-104">MRTK 101: 基本的な対話式操作に Mixed Reality Toolkit Unity を使用する方法 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)</span><span class="sxs-lookup"><span data-stu-id="9ee71-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="9ee71-106">MRTK を使用して、Mixed Reality で最も広く使用されている一般的な対話式操作パターンを実現する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ee71-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="9ee71-107">Unity エディターで入力の対話式操作をシミュレートする方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="9ee71-108">オブジェクトをつかんで動かす方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-108">How to grab and move an object?</span></span>
- <span data-ttu-id="9ee71-109">オブジェクトのサイズを変更する方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-109">How to resize an object?</span></span>
- <span data-ttu-id="9ee71-110">正確にオブジェクトを動かしたり回転させたりする方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="9ee71-111">オブジェクトを入力イベントに応答させる方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="9ee71-112">視覚的なフィードバックを追加する方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-112">How to add visual feedback?</span></span>
- <span data-ttu-id="9ee71-113">音声によるフィードバックを追加する方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-113">How to add audio feedback?</span></span>
- <span data-ttu-id="9ee71-114">HoloLens 2 のスタイル ボタン プレハブを使用する方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="9ee71-115">オブジェクトが自分の後をついてくるようにする方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-115">How to make an object follow you?</span></span>
- <span data-ttu-id="9ee71-116">オブジェクトが自分の方を向くようにする方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="9ee71-117">Unity エディターで入力の対話式操作をシミュレートする方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="9ee71-118">MRTK では、エディター内入力シミュレーションがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9ee71-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="9ee71-119">単に、Unity の [Play]\(再生\) ボタンをクリックして、シーンを実行します。</span><span class="sxs-lookup"><span data-stu-id="9ee71-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="9ee71-120">入力をシミュレートするには、次のキーを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ee71-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="9ee71-121">カメラを動かすには、W、A、S、D のキーを押します。</span><span class="sxs-lookup"><span data-stu-id="9ee71-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="9ee71-122">周囲を見回すには、マウスの右ボタンを押したまま、マウスを動かします。</span><span class="sxs-lookup"><span data-stu-id="9ee71-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="9ee71-123">シミュレートされたハンドを表示するには、スペース キー (右手) または左側の Shift キー (左手) を押します。シミュレートされたハンドを表示したままにするには、T または Y キーを押します。シミュレートされたハンドを回転させるには、Q または E (水平方向)/R または F (垂直方向) を押します。</span><span class="sxs-lookup"><span data-stu-id="9ee71-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="9ee71-124">入力シミュレーションの詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="9ee71-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="9ee71-125">オブジェクトをつかんで動かす方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-125">How to grab and move an object?</span></span>
<span data-ttu-id="9ee71-126">オブジェクトをつかめるようにするには、次の 2 つのスクリプトを割り当てます。ManipulationHandler.cs と NearInteractionGrabbable.cs(多関節ハンド トラッキング入力を使用して直接つかむ)。ManipulationHandler では、近くと遠くの両方の対話式操作がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9ee71-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="9ee71-127">オブジェクトをつかんで動かすには、HoloLens 2 の多関節ハンド トラッキング入力 (近く)、ハンド レイ (遠く)、モーション コントローラーのビーム (遠く)、HoloLens の視線カーソルとエアタップ (遠く) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="9ee71-128">オブジェクトのサイズを変更する方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-128">How to resize an object?</span></span>
<span data-ttu-id="9ee71-129">ManipulationHandler.cs では、両手のスケーリング/回転がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9ee71-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="9ee71-130">これは、HoloLens 2 の多関節ハンド入力、HoloLens 1 の視線入力とジェスチャ入力、Windows Mixed Reality のイマーシブ ヘッドセットのモーション コントローラー入力など、さまざまな入力の種類で機能します。</span><span class="sxs-lookup"><span data-stu-id="9ee71-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="9ee71-131">操作ハンドラーの詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="9ee71-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="9ee71-132">正確にオブジェクトを動かしたり回転させたりする方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="9ee71-133">オブジェクトをスケーリングしたり回転させたりするためのインターフェイスである境界ボックスを使用するには、BoundingBox.cs をオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="9ee71-134">既定では、HoloLens 1 スタイルの青いハンドルとワイヤが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="9ee71-135">HoloLens 2 スタイルの近接度に基づくアニメーション ハンドルを使用するには、プレハブとマテリアルを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ee71-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="9ee71-136">構成の詳細については、[境界ボックスのドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)と BoundingBoxExamples.unity シーンを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ee71-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="9ee71-137">境界ボックスの詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="9ee71-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="9ee71-138">オブジェクトを入力イベントに応答させる方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="9ee71-139">PointerHandler.cs をオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="9ee71-140">インスペクターでは、OnPointerDown()、OnPointerUp()、OnPointerClicked()、OnPointerDragged() のイベントを使用できます。これらのイベントをスクリプトで使用するには、IMixedRealityPointerHandler を実装します。</span><span class="sxs-lookup"><span data-stu-id="9ee71-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="9ee71-141">入力システムの詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="9ee71-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="9ee71-142">視覚的なフィードバックを追加する方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-142">How to add visual feedback?</span></span>
<span data-ttu-id="9ee71-143">Interactable.cs をオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="9ee71-144">インスペクターで、新しいテーマを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ee71-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="9ee71-145">Interactable のテーマ プロファイルを使用すると、利用可能なすべての入力対話式操作状態に視覚的なフィードバックを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="9ee71-146">Interactable には、対話式操作状態ごとにシェーダーのプロパティを制御できるようにするシェーダー テーマを含め、さまざまな種類のテーマが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9ee71-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="9ee71-147">Interactable の詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="9ee71-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="9ee71-148">視覚的なフィードバックのもう 1 つの重要な構成要素は、MRTK 標準シェーダーです。</span><span class="sxs-lookup"><span data-stu-id="9ee71-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="9ee71-149">MRTK 標準シェーダーを使用すると、ホバー ライトや近接ライトなどの視覚的なフィードバック効果を簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="9ee71-150">MRTK 標準シェーダーで実行される計算は、Unity 標準シェーダーより大幅に少ないため、効率の良いエクスペリエンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="9ee71-151">新しいマテリアルを作成し、[Shader]\(シェーダー\) で [Mixed Reality Toolkit] > [Standard]\(標準\) の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="9ee71-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="9ee71-152">あるいは、MRTK 標準シェーダーを使用する既存のマテリアルのいずれかを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="9ee71-153">MRTK 標準シェーダーの詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="9ee71-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="9ee71-154">音声によるフィードバックを追加する方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-154">How to add audio feedback?</span></span>
<span data-ttu-id="9ee71-155">AudioSource をオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="9ee71-155">Add AudioSource to an object.</span></span> <span data-ttu-id="9ee71-156">次に、入力イベントを公開するスクリプト (例: Interactable.cs や PointerHandler.cs) で、オブジェクトをイベントに割り当て、AudioSource.PlayOneShot() を選択します。</span><span class="sxs-lookup"><span data-stu-id="9ee71-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="9ee71-157">自分のオーディオ クリップを使用することも、MRTK のオーディオ アセットのいずれかを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="9ee71-158">HoloLens 2 のスタイル ボタン プレハブを使用する方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="9ee71-159">MRTK には、さまざまな種類の HoloLens 2 のシェル (OS) スタイル ボタンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9ee71-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="9ee71-160">これは、近接ライト、圧縮ボックス、リップル効果などの洗練されたビジュアル フィードバックをボタン表面に提供します。</span><span class="sxs-lookup"><span data-stu-id="9ee71-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="9ee71-161">単純に、HoloLens 2 スタイル押しボタン プレハブをシーンにドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="9ee71-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="9ee71-162">プレハブでは、上記で導入された Interactable.cs が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="9ee71-163">Interactable で OnClick() などの公開されたイベントを使用してアクションをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="9ee71-164">Button プレハブの詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="9ee71-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="9ee71-165">オブジェクトが自分の後をついてくるようにする方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-165">How to make an object follow you?</span></span>
<span data-ttu-id="9ee71-166">RadialView.cs スクリプトをオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="9ee71-167">これは、Solver スクリプト シリーズの一部です。これを使用すると、3D 空間に配置されているさまざまな種類のオブジェクトを実現することができます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="9ee71-168">SolverHandler.cs は自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="9ee71-169">次に示すのは、HoloLens シェルの [スタート] メニューと同様に、"lazy follow" Tag-along 動作を実現する RadialView 構成の例です。</span><span class="sxs-lookup"><span data-stu-id="9ee71-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="9ee71-170">最小/最大の距離と最小/最大の表示角度を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="9ee71-171">次の例は、0.4m と 0.8m の範囲で 15°以内のオブジェクトの配置を示しています。</span><span class="sxs-lookup"><span data-stu-id="9ee71-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="9ee71-172">Lerp 時間の値を調整して、位置指定の更新を速くしたり遅くしたりします。</span><span class="sxs-lookup"><span data-stu-id="9ee71-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="9ee71-173">ソルバーの詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="9ee71-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="9ee71-174">オブジェクトが自分の方を向くようにする方法</span><span class="sxs-lookup"><span data-stu-id="9ee71-174">How to make an object face you?</span></span>
<span data-ttu-id="9ee71-175">Billboard.cs スクリプトをオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="9ee71-176">これは、ユーザーの位置に関係なく、常にユーザーの方を向きます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="9ee71-177">ピボット軸オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9ee71-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="9ee71-178">Mixed Reality の素晴らしいエクスペリエンスを作成する準備はできましたか。</span><span class="sxs-lookup"><span data-stu-id="9ee71-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="9ee71-179">MRTK と Mixed Reality の詳細については、以下のページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9ee71-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="9ee71-180">筆者について</span><span class="sxs-lookup"><span data-stu-id="9ee71-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="9ee71-181"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="9ee71-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="9ee71-182">UX デザイナー @Microsoft</span><span class="sxs-lookup"><span data-stu-id="9ee71-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="9ee71-183">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ee71-183">See also</span></span>

* [<span data-ttu-id="9ee71-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="9ee71-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="9ee71-185">MRTK ドキュメント ポータル</span><span class="sxs-lookup"><span data-stu-id="9ee71-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="9ee71-186">MRTK の概要</span><span class="sxs-lookup"><span data-stu-id="9ee71-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="9ee71-187">HoloToolkit から MRTK への移植ガイドライン</span><span class="sxs-lookup"><span data-stu-id="9ee71-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
