---
title: DirectX でのレンダリング
description: For Mixed Reality を Windows holographic のレンダリングについて説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、レンダリング、3 D グラフィックス、HolographicFrame、レンダリング ループ、update ループ、チュートリアル、サンプル コード
ms.openlocfilehash: fd35f971af4c3c9dfd7f21ee396c92216b3246e9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605161"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="a44d5-104">DirectX でのレンダリング</span><span class="sxs-lookup"><span data-stu-id="a44d5-104">Rendering in DirectX</span></span>

<span data-ttu-id="a44d5-105">Windows Mixed Reality が豊富なを生成するために DirectX 上に構築された、ユーザー エクスペリエンスを 3D グラフィック。</span><span class="sxs-lookup"><span data-stu-id="a44d5-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="a44d5-106">レンダリングの抽象化は DirectX のすぐ上に配置でき、アプリ理由については、位置と、システムによって予測されたとしての holographic のシーンのオブザーバーを 1 つまたは複数の向きです。</span><span class="sxs-lookup"><span data-stu-id="a44d5-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="a44d5-107">開発者場所を確認できます、ホログラム各カメラでは、基準としたアプリのように、ユーザーが移動これらホログラムでさまざまな空間座標系を表示できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="a44d5-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="a44d5-108">現在のフレームの更新</span><span class="sxs-lookup"><span data-stu-id="a44d5-108">Update for the current frame</span></span>

<span data-ttu-id="a44d5-109">ホログラムのアプリケーションの状態を更新するには、1 回、アプリのフレームごとには。</span><span class="sxs-lookup"><span data-stu-id="a44d5-109">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="a44d5-110">取得、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>表示の管理システムからです。</span><span class="sxs-lookup"><span data-stu-id="a44d5-110">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="a44d5-111">レンダリングが完了したときに、カメラ ビューのある現在の予測では、シーンを更新します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-111">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="a44d5-112">Holographic のシーンの 1 つ以上のカメラがありますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a44d5-112">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="a44d5-113">Holographic のカメラのビューにレンダリング、1 回、アプリのフレームごとには。</span><span class="sxs-lookup"><span data-stu-id="a44d5-113">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="a44d5-114">各カメラでは、システムからカメラの表示および投影マトリックスを使用して、現在のフレーム シーンをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="a44d5-114">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="a44d5-115">新しい holographic フレームを作成し、その予測を取得</span><span class="sxs-lookup"><span data-stu-id="a44d5-115">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="a44d5-116"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>を更新し、現在のフレームをレンダリングするために、アプリが必要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a44d5-116">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="a44d5-117">アプリが呼び出すことによって新しいフレームを開始、 **CreateNextFrame**メソッド。</span><span class="sxs-lookup"><span data-stu-id="a44d5-117">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="a44d5-118">このメソッドが呼び出されると、予測は、使用可能なでカプセル化された最新のセンサー データを使用して行われます**CurrentPrediction**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a44d5-118">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="a44d5-119">レンダリングされた各フレームのみ有効ですが瞬間の時間内に、新しいフレーム オブジェクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-119">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="a44d5-120">**CurrentPrediction**プロパティには、カメラの位置などの情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a44d5-120">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="a44d5-121">情報を推定して、正確な時点に、フレームがユーザーに表示される予定です。</span><span class="sxs-lookup"><span data-stu-id="a44d5-121">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="a44d5-122">次のコードからの抜粋です**AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-122">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="a44d5-123">プロセスのカメラの更新</span><span class="sxs-lookup"><span data-stu-id="a44d5-123">Process camera updates</span></span>

<span data-ttu-id="a44d5-124">バック バッファーには、フレーム間を変更できます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-124">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="a44d5-125">バックアップを検証するアプリケーションのニーズは、各カメラでは、バッファーしリリースを必要に応じて、リソース ビューと深度バッファーを作成し直します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-125">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="a44d5-126">予測のポーズのセットが現在のフレームで使用されているカメラの優先する一覧に注目してください。</span><span class="sxs-lookup"><span data-stu-id="a44d5-126">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="a44d5-127">通常、この一覧を使用するカメラのセットを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-127">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="a44d5-128">**AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-128">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="a44d5-129">**DeviceResources::EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-129">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="a44d5-130">レンダリングの基盤として使用する座標系を取得します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-130">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="a44d5-131">Windows Mixed Reality により、アプリを作成するさまざまな[座標系](coordinate-systems-in-directx.md)現実の世界での場所を追跡する必要に応じて、アタッチされた参照フレームや静止した基準枠など。</span><span class="sxs-lookup"><span data-stu-id="a44d5-131">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="a44d5-132">アプリは、ホログラム各フレームをレンダリングする場所についての理由をこれらの座標システムを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-132">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="a44d5-133">常にで渡す API からの座標を要求するときに、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>内を表現するには、その座標を決定します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-133">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="a44d5-134">**AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-134">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="a44d5-135">これらの座標系は、シーン内のコンテンツを表示するときに、ステレオの view 行列を生成する使用できます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-135">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="a44d5-136">**CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-136">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="a44d5-137">プロセスの視線入力および入力ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="a44d5-137">Process gaze and gesture input</span></span>

<span data-ttu-id="a44d5-138">[視線](gaze.md)と[ジェスチャ](gestures.md)入力時間ベースでないし、そのために更新する必要はありません、 **StepTimer**関数。</span><span class="sxs-lookup"><span data-stu-id="a44d5-138">[Gaze](gaze.md) and [gesture](gestures.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="a44d5-139">ただし[この入力](gaze,-gestures,-and-motion-controllers-in-directx.md)アプリは、各フレームを確認する必要があるものです。</span><span class="sxs-lookup"><span data-stu-id="a44d5-139">However [this input](gaze,-gestures,-and-motion-controllers-in-directx.md) is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="a44d5-140">プロセスの時間ベースの更新プログラム</span><span class="sxs-lookup"><span data-stu-id="a44d5-140">Process time-based updates</span></span>

<span data-ttu-id="a44d5-141">任意のリアルタイム レンダリング アプリには、時間ベースの更新を処理する手段は必要があります。これを使用して Windows Holographic のアプリ テンプレートで実行する方法を提供しています、 **StepTimer**実装します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-141">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="a44d5-142">これは、機能は、DirectX 11 の UWP アプリ テンプレートでため既に検索でそのテンプレート場合おく必要がある慣れた土壌にかかわるで提供される、StepTimer に似ています。</span><span class="sxs-lookup"><span data-stu-id="a44d5-142">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="a44d5-143">この StepTimer サンプルのヘルパー クラスは、変数の時間ステップの更新プログラムと同様に、固定の時間ステップの更新プログラムを提供することと、既定のモードは変数の時間ステップ。</span><span class="sxs-lookup"><span data-stu-id="a44d5-143">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="a44d5-144">Holographic のレンダリングの場合に、タイマー関数には多すぎるを保存しない具体的には選択しました。</span><span class="sxs-lookup"><span data-stu-id="a44d5-144">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="a44d5-145">一定の時間ステップを構成することができる場合 – フレームごとまたはまったくないいくつかのフレームは複数回呼び出す取得可能性があります、holographic データ更新は、フレームごとに 1 回発生するためです。</span><span class="sxs-lookup"><span data-stu-id="a44d5-145">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="a44d5-146">**AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-146">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="a44d5-147">位置と、座標系で回転ホログラム</span><span class="sxs-lookup"><span data-stu-id="a44d5-147">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="a44d5-148">テンプレートは、1 つの座標システムで動作している場合、 **SpatialStationaryReferenceFrame**、このプロセスがいる場合は異なる 3D グラフィックを使用します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-148">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="a44d5-149">キューブを回転ここでは、静止した座標系内の位置を基準としたモデル マトリックスを設定します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-149">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="a44d5-150">**SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-150">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

<span data-ttu-id="a44d5-151">**高度なシナリオについて注意してください。** 回転キューブは、1 つの参照フレーム内のホログラムを配置する方法の非常に単純な例です。</span><span class="sxs-lookup"><span data-stu-id="a44d5-151">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="a44d5-152">することも[複数 SpatialCoordinateSystems を使用して、](coordinate-systems-in-directx.md)で同時に、同じレンダリングされたフレーム。</span><span class="sxs-lookup"><span data-stu-id="a44d5-152">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="a44d5-153">定数バッファーのデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-153">Update constant buffer data</span></span>

<span data-ttu-id="a44d5-154">コンテンツ モデルの変換は、通常どおりに更新されます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-154">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="a44d5-155">ここまででレンダリングする座標系の有効な変換を計算がされます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-155">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="a44d5-156">**SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-156">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

<span data-ttu-id="a44d5-157">ビューおよび射影変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-157">What about view and projection transforms?</span></span> <span data-ttu-id="a44d5-158">最良の結果を前にこれらに、描画呼び出しのほぼ準備ができましたまで待機します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-158">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="a44d5-159">現在のフレームをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="a44d5-159">Render the current frame</span></span>

<span data-ttu-id="a44d5-160">Windows Mixed Reality でのレンダリングは 2D の mono 表示でのレンダリングからほぼ同じですが、注意する必要があるいくつか違いがあります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-160">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="a44d5-161">Holographic フレームの予測は重要です。</span><span class="sxs-lookup"><span data-stu-id="a44d5-161">Holographic frame predictions are important.</span></span> <span data-ttu-id="a44d5-162">近ければ近いほど、予測には、フレームが表示されたら、ほど、ホログラムになります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-162">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="a44d5-163">Windows Mixed Reality は、カメラのビューを制御します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-163">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="a44d5-164">Holographic のフレームを表示することが後であるために、それぞれにレンダリングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-164">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="a44d5-165">ステレオのレンダリングがレンダー ターゲットの配列をインスタンス化された描画を使用して行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a44d5-165">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="a44d5-166">Holographic アプリ テンプレート上にレンダー ターゲット ビューを使用して、レンダー ターゲット配列のインスタンス化された描画の推奨されるアプローチを使用して、 **Texture2DArray**します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-166">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="a44d5-167">ステレオ インスタンス化を使用せずに表示するには、(目ごとに 1 つ) 2 つの非配列の RenderTargetViews のうち、2 つのいずれかの各参照でスライスするを作成する必要があります、 **Texture2DArray**システムから、アプリに提供します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-167">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="a44d5-168">これは、ようなインスタンス化を使用するよりもはるかに低速では通常、いないお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a44d5-168">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="a44d5-169">更新の HolographicFrame 予測を取得します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-169">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="a44d5-170">フレームの予測を更新して、イメージの安定化の有効性を強化、ホログラム、予測、フレームが、ユーザーに表示されるまでの短い時間のためのより正確な位置を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-170">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="a44d5-171">理想的なレンダリングの直前に、フレームの予測を更新します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-171">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="a44d5-172">各カメラにレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="a44d5-172">Render to each camera</span></span>

<span data-ttu-id="a44d5-173">カメラことで、予測のセットをループし、このセット内の各カメラをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="a44d5-173">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="a44d5-174">**レンダリング パスを設定します。**</span><span class="sxs-lookup"><span data-stu-id="a44d5-174">**Set up your rendering pass**</span></span>

<span data-ttu-id="a44d5-175">Windows Mixed Reality ステレオスコ ピック レンダリング、奥行を強化するためと使用しながら行います、表示するために左側と右側の表示の両方がアクティブであるためです。</span><span class="sxs-lookup"><span data-stu-id="a44d5-175">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="a44d5-176">ステレオスコ ピック レンダリングのオフセットの間は 2 つの表示は、実際の深さとして脳を調整できます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-176">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="a44d5-177">このセクションについて説明しますステレオスコ ピック レンダリングに、Windows Holographic のアプリケーション テンプレートからコードを使用して、インスタンス化を使用します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-177">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="a44d5-178">各カメラでは、holographic の領域に独自レンダー ターゲット (バック バッファー) と表示および投影マトリックスがあります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-178">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="a44d5-179">アプリは、他のカメラに基づくリソース作成 - - 深度バッファーなどのカメラごとにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-179">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="a44d5-180">Windows Holographic のアプリ テンプレートでは、DX::CameraResources でこれらのリソースをバンドルするヘルパー クラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-180">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="a44d5-181">レンダー ターゲット ビューを設定して開始します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-181">Start by setting up the render target views:</span></span>

<span data-ttu-id="a44d5-182">**AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-182">From **AppMain::Render**:</span></span>

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

<span data-ttu-id="a44d5-183">**予測を使用して、カメラの表示および投影マトリックスを取得するには**</span><span class="sxs-lookup"><span data-stu-id="a44d5-183">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="a44d5-184">各 holographic のカメラの表示および投影マトリックスは、すべてのフレームで変更されます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-184">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="a44d5-185">各 holographic のカメラの定数バッファー内のデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-185">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="a44d5-186">このオプションは、予測を更新して、すべての描画がそのカメラの呼び出しを行う前に後に行います。</span><span class="sxs-lookup"><span data-stu-id="a44d5-186">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="a44d5-187">**AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-187">From **AppMain::Render**:</span></span>

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

<span data-ttu-id="a44d5-188">ここでは、カメラの姿勢から行列を取得する方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-188">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="a44d5-189">このプロセス中にも、カメラの現在のビューポートを取得します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-189">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="a44d5-190">座標系を提供する方法に注意してください。 これは、理解、視線の先を使用して同じ座標系と位置、回転するキューブを使用して 1 つと同じです。</span><span class="sxs-lookup"><span data-stu-id="a44d5-190">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="a44d5-191">**CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-191">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

<span data-ttu-id="a44d5-192">ビューポートには、各フレームを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-192">The viewport should be set each frame.</span></span> <span data-ttu-id="a44d5-193">頂点シェーダーは、(少なくとも)/ビューのプロジェクション データへのアクセスを必要が一般にあります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-193">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="a44d5-194">**CameraResources::AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-194">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

<span data-ttu-id="a44d5-195">**カメラのバック バッファーにレンダリングし、コミット、深度バッファー**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-195">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="a44d5-196">いることを確認することをお勧め**TryGetViewTransform**のため、ビューのプロジェクション/データを使用する前に成功しました座標システムのロケールがない場合 (例: 追跡中断されました) をして、アプリを表示できませんフレーム。</span><span class="sxs-lookup"><span data-stu-id="a44d5-196">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="a44d5-197">テンプレートのみを呼び出して**レンダリング**、回転するキューブの場合、 **CameraResources**クラスが正常に更新プログラムを示します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-197">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="a44d5-198">Windows Mixed Reality には維持するホログラム開発者やユーザーが格納して、世界中の機能が含まれています[イメージの安定化](hologram-stability.md)します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-198">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="a44d5-199">イメージの安定化により、ユーザー; holographic 最善のエクスペリエンスを確保するためのレンダリング パイプラインに固有の待機時間を非表示にします。イメージの安定化、さらに強化するために、フォーカス ポイントを指定する場合があります。 またはコンピューティングをリアルタイムでのイメージの安定化に最適化された深度バッファーを指定することがあります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-199">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="a44d5-200">使用して深度バッファー最良の結果をアプリが提供する必要があります、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API。</span><span class="sxs-lookup"><span data-stu-id="a44d5-200">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="a44d5-201">Windows Mixed Reality は、リアルタイムでのイメージの安定化を最適化するために、深度バッファーからの geometry の情報を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-201">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="a44d5-202">Windows Holographic のアプリ テンプレートでは、ホログラム安定性を最適化する際、既定で、アプリの深度バッファーをコミットします。</span><span class="sxs-lookup"><span data-stu-id="a44d5-202">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="a44d5-203">**AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-203">From **AppMain::Render**:</span></span>

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
><span data-ttu-id="a44d5-204">Windows は、深度バッファーをシェーダー リソースとして使用できる必要がありますので、GPU 上でテクスチャの深さを処理します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-204">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="a44d5-205">型指定されていない形式では作成した ID3D11Texture2D、シェーダー リソース ビューとしてバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-205">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="a44d5-206">イメージの安定化コミットできる深さテクスチャを作成する方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-206">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="a44d5-207">コードを**CommitDirect3D11DepthBuffer の深度バッファー リソースの作成**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-207">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

<span data-ttu-id="a44d5-208">**Holographic のコンテンツを描画します。**</span><span class="sxs-lookup"><span data-stu-id="a44d5-208">**Draw holographic content**</span></span>

<span data-ttu-id="a44d5-209">Windows Holographic のアプリ テンプレートでは、サイズが 2 の Texture2DArray をインスタンス化されたジオメトリの描画の推奨される方法を使用して、ステレオのコンテンツをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="a44d5-209">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="a44d5-210">これは、および Windows Mixed Reality でその動作のインスタンス化の一部を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="a44d5-210">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="a44d5-211">**SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-211">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

<span data-ttu-id="a44d5-212">各インスタンスでは、定数バッファーからさまざまなビューのプロジェクション マトリックスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="a44d5-212">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="a44d5-213">ここでは、定数バッファーの構造体は、マトリックスの 2 つの配列だけです。</span><span class="sxs-lookup"><span data-stu-id="a44d5-213">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="a44d5-214">**VertexShaderShared.hlsl**によって含まれる、 **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-214">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="a44d5-215">各ピクセルのレンダー ターゲットの配列インデックスを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-215">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="a44d5-216">次のスニペットでは output.viewId にマップされます、 **SV_RenderTargetArrayIndex**セマンティック。</span><span class="sxs-lookup"><span data-stu-id="a44d5-216">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="a44d5-217">これにより、レンダー ターゲットの配列インデックスをどのシェーダー ステージから設定するセマンティック、省略可能な Direct3D 11.3 機能のサポートが必要ですこのことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a44d5-217">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="a44d5-218">**VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-218">From **VPRTVertexShader.hlsl**:</span></span>

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

<span data-ttu-id="a44d5-219">**VertexShaderShared.hlsl**によって含まれる、 **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-219">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

<span data-ttu-id="a44d5-220">既存のインスタンスを使用する場合は、ステレオに描画するには、このメソッドを使用して描画手法のレンダリング先の配列、通常存在するインスタンスの数の 2 倍の描画が行う必要があるすべて。</span><span class="sxs-lookup"><span data-stu-id="a44d5-220">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="a44d5-221">シェーダーで分割**input.instId**を元のインスタンス ID を取得する 2 でオブジェクトごとのデータのバッファー (など) にインデックスことができます。 `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="a44d5-221">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="a44d5-222">HoloLens のステレオのコンテンツを表示する方法の重要な注意事項</span><span class="sxs-lookup"><span data-stu-id="a44d5-222">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="a44d5-223">Windows Mixed Reality; 任意のシェーダー ステージのレンダー ターゲットの配列インデックスを設定する機能をサポートしています通常、これは、ジオメトリ シェーダー ステージは、direct3d11 のセマンティックが定義された方法のためにのみ実行できるタスクです。</span><span class="sxs-lookup"><span data-stu-id="a44d5-223">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="a44d5-224">ここでは、頂点とピクセル シェーダーのステージ セットのみでレンダリング パイプラインを設定する方法の完全な例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-224">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="a44d5-225">シェーダー コードは、前述のようです。</span><span class="sxs-lookup"><span data-stu-id="a44d5-225">The shader code is as described above.</span></span>

<span data-ttu-id="a44d5-226">**SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-226">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="a44d5-227">非 HoloLens デバイスでのレンダリングに関する重要な注意事項</span><span class="sxs-lookup"><span data-stu-id="a44d5-227">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="a44d5-228">頂点シェーダーのレンダー ターゲットの配列インデックスを設定するには、オプションの Direct3D 11.3 機能、HoloLens をサポートして、グラフィックス ドライバーをサポートしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-228">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="a44d5-229">アプリが安全にだけ、レンダリングの手法を実装することができ、Microsoft HoloLens で実行されているすべての要件を満たすはします。</span><span class="sxs-lookup"><span data-stu-id="a44d5-229">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="a44d5-230">エミュレーターを使用する、HoloLens、holographic アプリのための強力な開発ツールと Windows 10 Pc に接続されている Windows Mixed Reality ヘッドセット没入型のデバイスをサポートするケースがあります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-230">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="a44d5-231">そのため、すべての Windows Mixed Reality - もに組み込まれている、Windows Holographic のアプリケーション テンプレートと HoloLens 非表示のパスのサポートします。</span><span class="sxs-lookup"><span data-stu-id="a44d5-231">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="a44d5-232">テンプレート コードでは、holographic アプリを開発用 PC に GPU 上で実行を有効にするコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-232">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="a44d5-233">ここでは、方法、 **DeviceResources**クラスのこの省略可能な機能のサポートを確認します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-233">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="a44d5-234">**DeviceResources::CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-234">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="a44d5-235">この省略可能な機能なしのレンダリングをサポートするために、アプリは、レンダー ターゲットの配列インデックスを設定するのにジオメトリ シェーダーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-235">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="a44d5-236">このスニペットを追加すると*後* **VSSetConstantBuffers**と*する前に* **PSSetShader**の前に示したコード例HoloLens のステレオのレンダリング方法を説明するセクション。</span><span class="sxs-lookup"><span data-stu-id="a44d5-236">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="a44d5-237">**SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-237">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

<span data-ttu-id="a44d5-238">**HLSL 注**:この場合、レンダー ターゲットの配列インデックスを常に許可シェーダー TEXCOORD0 などのセマンティックを使用してジオメトリ シェーダーに渡される少し変更を加えた頂点シェーダーも読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-238">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="a44d5-239">ジオメトリ シェーダーはすべての作業を実行する必要はありません。テンプレートのジオメトリ シェーダーは、レンダー ターゲットの配列インデックス、SV_RenderTargetArrayIndex のセマンティックを設定するために使用を除き、すべてのデータを通過します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-239">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="a44d5-240">アプリ テンプレートのコード**GeometryShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-240">App template code for **GeometryShader.hlsl**:</span></span>

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        rtvId   : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a><span data-ttu-id="a44d5-241">Present</span><span class="sxs-lookup"><span data-stu-id="a44d5-241">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="a44d5-242">スワップ チェーンを提示する holographic のフレームを有効にします。</span><span class="sxs-lookup"><span data-stu-id="a44d5-242">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="a44d5-243">Windows Mixed Reality では、システムは、スワップ チェーンを制御します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-243">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="a44d5-244">システムは、各 holographic カメラ、高品質なユーザー エクスペリエンスを実現するフレームの表示を管理します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-244">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="a44d5-245">提供ビューポートの update フレームごとに、イメージの安定化や Mixed Reality キャプチャなどのシステムの側面を最適化するために各カメラ。</span><span class="sxs-lookup"><span data-stu-id="a44d5-245">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="a44d5-246">そのため、DirectX を使用して holographic アプリが呼び出さない**存在**DXGI スワップ チェーンです。</span><span class="sxs-lookup"><span data-stu-id="a44d5-246">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="a44d5-247">代わりに、使用、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>クラスが完了したら、フレームのすべてのスワップを提示する描画します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-247">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="a44d5-248">**DeviceResources::Present**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-248">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="a44d5-249">既定では、この API は、フレームを返す前に完了を待ちます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-249">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="a44d5-250">Holographic アプリは、遅延を低減し、予測の holographic フレームからより良い結果では、このため、新しいフレームの作業を開始する前に完了する前のフレームを待機する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-250">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="a44d5-251">そうでは、ハードのルールおよびフレームを表示するために 1 つの画面のリフレッシュよりも長い時間がかかるが HolographicFramePresentWaitBehavior パラメーターを渡すことによってでこの待機を無効にできますがある場合<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-251">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="a44d5-252">この場合、GPU 上で継続的な負荷を維持するために、非同期のレンダリング スレッドを使用すると可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-252">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="a44d5-253">HoloLens デバイスのリフレッシュ レートは、60 hz、1 つのフレームが約 16 ミリ秒の期間を持つことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a44d5-253">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="a44d5-254">90 hz; 60 hz の範囲はイマーシブ ヘッドセット デバイス90 hz で表示を更新するときに、各フレームは約 11 ms の継続時間があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-254">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="a44d5-255">協力、HolographicFrame DeviceLost シナリオを処理します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-255">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="a44d5-256">DirectX 11 アプリは、通常 DXGI スワップ チェーンのによって返される HRESULT を確認する必要は**存在**関数があったかを**DeviceLost**エラー。</span><span class="sxs-lookup"><span data-stu-id="a44d5-256">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="a44d5-257"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>クラスでは、これを処理できます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-257">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="a44d5-258">検査、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a>をリリースして、Direct3D デバイスとデバイス ベースのリソースを再作成する必要があるかどうかを返します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-258">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

<span data-ttu-id="a44d5-259">Direct3D デバイスが失われた場合は、再作成した場合は、通知する必要があります、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>に新しいデバイスの使用を開始します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-259">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="a44d5-260">スワップ チェーンは、このデバイスの再作成されます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-260">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="a44d5-261">**DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-261">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="a44d5-262">フレームが表示されたら、メイン プログラム ループに戻りますし、次のフレームを続行することを許可できます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-262">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="a44d5-263">ハイブリッド グラフィック Pc や複合現実のアプリケーション</span><span class="sxs-lookup"><span data-stu-id="a44d5-263">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="a44d5-264">Windows 10 Creators Update の Pc で構成することがあります**両方**Gpu の不連続値と統合します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-264">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="a44d5-265">これらの種類のコンピューターで Windows は、アダプターに接続されている、ヘッドセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-265">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="a44d5-266">アプリケーションは、DirectX デバイスを作成しますが、同じアダプターを使用することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-266">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="a44d5-267">最も一般的な Direct3D サンプルのコードでは、可能性のあるハイブリッド システムのないヘッドセットで使ったものと同じ既定のハードウェア アダプターを使用して DirectX デバイスを作成するを示します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-267">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="a44d5-268">これが原因で問題を回避するには、使用、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a>いずれかから<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>します。PrimaryAdapterId() または<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>します。AdapterId() します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-268">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="a44d5-269">この 6 または 7 ですは IDXGIFactory4.EnumAdapterByLuid を使用して適切な DXGIAdapter を選択するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="a44d5-269">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="a44d5-270">**DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-270">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

<span data-ttu-id="a44d5-271">コードを**更新 DeviceResources::CreateDeviceResources IDXGIAdapter を使用するには**</span><span class="sxs-lookup"><span data-stu-id="a44d5-271">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

<span data-ttu-id="a44d5-272">**ハイブリッドのグラフィックスとメディア ファンデーション**</span><span class="sxs-lookup"><span data-stu-id="a44d5-272">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="a44d5-273">ハイブリッド システムで Media Foundation を使用すると、ビデオは表示されませんか、ビデオのテクスチャが破損している問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-273">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="a44d5-274">これは、既に説明したようにシステムの動作は既定ではメディア ファンデーションのために発生します。</span><span class="sxs-lookup"><span data-stu-id="a44d5-274">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="a44d5-275">一部のシナリオでは、個別 ID3D11Device を作成するマルチ スレッドをサポートし、フラグが設定されて正しい作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-275">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="a44d5-276">ID3D11Device を初期化するときに、D3D11_CREATE_DEVICE_VIDEO_SUPPORT フラグは、D3D11_CREATE_DEVICE_FLAG の一部として定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44d5-276">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="a44d5-277">デバイスとコンテキストが作成されると、呼び出す<a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a>有効にするマルチ スレッドです。</span><span class="sxs-lookup"><span data-stu-id="a44d5-277">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="a44d5-278">使用してデバイスを関連付ける、 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>を使用して、 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a>関数。</span><span class="sxs-lookup"><span data-stu-id="a44d5-278">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="a44d5-279">コードを **、ID3D11Device を関連付ける IMFDXGIDeviceManager**:</span><span class="sxs-lookup"><span data-stu-id="a44d5-279">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a><span data-ttu-id="a44d5-280">関連項目</span><span class="sxs-lookup"><span data-stu-id="a44d5-280">See also</span></span>
* [<span data-ttu-id="a44d5-281">DirectX の座標系</span><span class="sxs-lookup"><span data-stu-id="a44d5-281">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="a44d5-282">HoloLens のエミュレーターを使用する</span><span class="sxs-lookup"><span data-stu-id="a44d5-282">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
