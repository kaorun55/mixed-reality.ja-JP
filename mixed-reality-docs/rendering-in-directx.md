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
# <a name="rendering-in-directx"></a>DirectX でのレンダリング

Windows Mixed Reality が豊富なを生成するために DirectX 上に構築された、ユーザー エクスペリエンスを 3D グラフィック。 レンダリングの抽象化は DirectX のすぐ上に配置でき、アプリ理由については、位置と、システムによって予測されたとしての holographic のシーンのオブザーバーを 1 つまたは複数の向きです。 開発者場所を確認できます、ホログラム各カメラでは、基準としたアプリのように、ユーザーが移動これらホログラムでさまざまな空間座標系を表示できるようにすることです。

## <a name="update-for-the-current-frame"></a>現在のフレームの更新

ホログラムのアプリケーションの状態を更新するには、1 回、アプリのフレームごとには。
* 取得、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>表示の管理システムからです。
* レンダリングが完了したときに、カメラ ビューのある現在の予測では、シーンを更新します。 Holographic のシーンの 1 つ以上のカメラがありますに注意してください。

Holographic のカメラのビューにレンダリング、1 回、アプリのフレームごとには。
* 各カメラでは、システムからカメラの表示および投影マトリックスを使用して、現在のフレーム シーンをレンダリングします。

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>新しい holographic フレームを作成し、その予測を取得

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>を更新し、現在のフレームをレンダリングするために、アプリが必要な情報が含まれています。 アプリが呼び出すことによって新しいフレームを開始、 **CreateNextFrame**メソッド。 このメソッドが呼び出されると、予測は、使用可能なでカプセル化された最新のセンサー データを使用して行われます**CurrentPrediction**オブジェクト。

レンダリングされた各フレームのみ有効ですが瞬間の時間内に、新しいフレーム オブジェクトを使用する必要があります。 **CurrentPrediction**プロパティには、カメラの位置などの情報が含まれています。 情報を推定して、正確な時点に、フレームがユーザーに表示される予定です。

次のコードからの抜粋です**AppMain::Update**:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>プロセスのカメラの更新

バック バッファーには、フレーム間を変更できます。 バックアップを検証するアプリケーションのニーズは、各カメラでは、バッファーしリリースを必要に応じて、リソース ビューと深度バッファーを作成し直します。 予測のポーズのセットが現在のフレームで使用されているカメラの優先する一覧に注目してください。 通常、この一覧を使用するカメラのセットを反復処理します。

**AppMain::Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

**DeviceResources::EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>レンダリングの基盤として使用する座標系を取得します。

Windows Mixed Reality により、アプリを作成するさまざまな[座標系](coordinate-systems-in-directx.md)現実の世界での場所を追跡する必要に応じて、アタッチされた参照フレームや静止した基準枠など。 アプリは、ホログラム各フレームをレンダリングする場所についての理由をこれらの座標システムを使用できます。 常にで渡す API からの座標を要求するときに、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>内を表現するには、その座標を決定します。

**AppMain::Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

これらの座標系は、シーン内のコンテンツを表示するときに、ステレオの view 行列を生成する使用できます。

**CameraResources::UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>プロセスの視線入力および入力ジェスチャ

[視線](gaze.md)と[ジェスチャ](gestures.md)入力時間ベースでないし、そのために更新する必要はありません、 **StepTimer**関数。 ただし[この入力](gaze,-gestures,-and-motion-controllers-in-directx.md)アプリは、各フレームを確認する必要があるものです。

### <a name="process-time-based-updates"></a>プロセスの時間ベースの更新プログラム

任意のリアルタイム レンダリング アプリには、時間ベースの更新を処理する手段は必要があります。これを使用して Windows Holographic のアプリ テンプレートで実行する方法を提供しています、 **StepTimer**実装します。 これは、機能は、DirectX 11 の UWP アプリ テンプレートでため既に検索でそのテンプレート場合おく必要がある慣れた土壌にかかわるで提供される、StepTimer に似ています。 この StepTimer サンプルのヘルパー クラスは、変数の時間ステップの更新プログラムと同様に、固定の時間ステップの更新プログラムを提供することと、既定のモードは変数の時間ステップ。

Holographic のレンダリングの場合に、タイマー関数には多すぎるを保存しない具体的には選択しました。 一定の時間ステップを構成することができる場合 – フレームごとまたはまったくないいくつかのフレームは複数回呼び出す取得可能性があります、holographic データ更新は、フレームごとに 1 回発生するためです。


**AppMain::Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>位置と、座標系で回転ホログラム

テンプレートは、1 つの座標システムで動作している場合、 **SpatialStationaryReferenceFrame**、このプロセスがいる場合は異なる 3D グラフィックを使用します。 キューブを回転ここでは、静止した座標系内の位置を基準としたモデル マトリックスを設定します。

**SpinningCubeRenderer::Update**:

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

**高度なシナリオについて注意してください。** 回転キューブは、1 つの参照フレーム内のホログラムを配置する方法の非常に単純な例です。 することも[複数 SpatialCoordinateSystems を使用して、](coordinate-systems-in-directx.md)で同時に、同じレンダリングされたフレーム。

### <a name="update-constant-buffer-data"></a>定数バッファーのデータを更新します。

コンテンツ モデルの変換は、通常どおりに更新されます。 ここまででレンダリングする座標系の有効な変換を計算がされます。

**SpinningCubeRenderer::Update**:

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

ビューおよび射影変換について説明します。 最良の結果を前にこれらに、描画呼び出しのほぼ準備ができましたまで待機します。

## <a name="render-the-current-frame"></a>現在のフレームをレンダリングします。

Windows Mixed Reality でのレンダリングは 2D の mono 表示でのレンダリングからほぼ同じですが、注意する必要があるいくつか違いがあります。
* Holographic フレームの予測は重要です。 近ければ近いほど、予測には、フレームが表示されたら、ほど、ホログラムになります。
* Windows Mixed Reality は、カメラのビューを制御します。 Holographic のフレームを表示することが後であるために、それぞれにレンダリングする必要があります。
* ステレオのレンダリングがレンダー ターゲットの配列をインスタンス化された描画を使用して行うことをお勧めします。 Holographic アプリ テンプレート上にレンダー ターゲット ビューを使用して、レンダー ターゲット配列のインスタンス化された描画の推奨されるアプローチを使用して、 **Texture2DArray**します。
* ステレオ インスタンス化を使用せずに表示するには、(目ごとに 1 つ) 2 つの非配列の RenderTargetViews のうち、2 つのいずれかの各参照でスライスするを作成する必要があります、 **Texture2DArray**システムから、アプリに提供します。 これは、ようなインスタンス化を使用するよりもはるかに低速では通常、いないお勧めします。

### <a name="get-an-updated-holographicframe-prediction"></a>更新の HolographicFrame 予測を取得します。

フレームの予測を更新して、イメージの安定化の有効性を強化、ホログラム、予測、フレームが、ユーザーに表示されるまでの短い時間のためのより正確な位置を指定できます。 理想的なレンダリングの直前に、フレームの予測を更新します。

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>各カメラにレンダリングします。

カメラことで、予測のセットをループし、このセット内の各カメラをレンダリングします。

**レンダリング パスを設定します。**

Windows Mixed Reality ステレオスコ ピック レンダリング、奥行を強化するためと使用しながら行います、表示するために左側と右側の表示の両方がアクティブであるためです。 ステレオスコ ピック レンダリングのオフセットの間は 2 つの表示は、実際の深さとして脳を調整できます。 このセクションについて説明しますステレオスコ ピック レンダリングに、Windows Holographic のアプリケーション テンプレートからコードを使用して、インスタンス化を使用します。

各カメラでは、holographic の領域に独自レンダー ターゲット (バック バッファー) と表示および投影マトリックスがあります。 アプリは、他のカメラに基づくリソース作成 - - 深度バッファーなどのカメラごとにする必要があります。 Windows Holographic のアプリ テンプレートでは、DX::CameraResources でこれらのリソースをバンドルするヘルパー クラスを提供します。 レンダー ターゲット ビューを設定して開始します。

**AppMain::Render**:

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

**予測を使用して、カメラの表示および投影マトリックスを取得するには**

各 holographic のカメラの表示および投影マトリックスは、すべてのフレームで変更されます。 各 holographic のカメラの定数バッファー内のデータを更新します。 このオプションは、予測を更新して、すべての描画がそのカメラの呼び出しを行う前に後に行います。

**AppMain::Render**:

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

ここでは、カメラの姿勢から行列を取得する方法を紹介します。 このプロセス中にも、カメラの現在のビューポートを取得します。 座標系を提供する方法に注意してください。 これは、理解、視線の先を使用して同じ座標系と位置、回転するキューブを使用して 1 つと同じです。


**CameraResources::UpdateViewProjectionBuffer**:

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

ビューポートには、各フレームを設定する必要があります。 頂点シェーダーは、(少なくとも)/ビューのプロジェクション データへのアクセスを必要が一般にあります。


**CameraResources::AttachViewProjectionBuffer**:

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

**カメラのバック バッファーにレンダリングし、コミット、深度バッファー**:

いることを確認することをお勧め**TryGetViewTransform**のため、ビューのプロジェクション/データを使用する前に成功しました座標システムのロケールがない場合 (例: 追跡中断されました) をして、アプリを表示できませんフレーム。 テンプレートのみを呼び出して**レンダリング**、回転するキューブの場合、 **CameraResources**クラスが正常に更新プログラムを示します。

Windows Mixed Reality には維持するホログラム開発者やユーザーが格納して、世界中の機能が含まれています[イメージの安定化](hologram-stability.md)します。 イメージの安定化により、ユーザー; holographic 最善のエクスペリエンスを確保するためのレンダリング パイプラインに固有の待機時間を非表示にします。イメージの安定化、さらに強化するために、フォーカス ポイントを指定する場合があります。 またはコンピューティングをリアルタイムでのイメージの安定化に最適化された深度バッファーを指定することがあります。

使用して深度バッファー最良の結果をアプリが提供する必要があります、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API。 Windows Mixed Reality は、リアルタイムでのイメージの安定化を最適化するために、深度バッファーからの geometry の情報を使用できます。 Windows Holographic のアプリ テンプレートでは、ホログラム安定性を最適化する際、既定で、アプリの深度バッファーをコミットします。

**AppMain::Render**:

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
>Windows は、深度バッファーをシェーダー リソースとして使用できる必要がありますので、GPU 上でテクスチャの深さを処理します。 型指定されていない形式では作成した ID3D11Texture2D、シェーダー リソース ビューとしてバインドする必要があります。 イメージの安定化コミットできる深さテクスチャを作成する方法の例を示します。

コードを**CommitDirect3D11DepthBuffer の深度バッファー リソースの作成**:

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

**Holographic のコンテンツを描画します。**

Windows Holographic のアプリ テンプレートでは、サイズが 2 の Texture2DArray をインスタンス化されたジオメトリの描画の推奨される方法を使用して、ステレオのコンテンツをレンダリングします。 これは、および Windows Mixed Reality でその動作のインスタンス化の一部を見てみましょう。

**SpinningCubeRenderer::Render**:

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

各インスタンスでは、定数バッファーからさまざまなビューのプロジェクション マトリックスにアクセスします。 ここでは、定数バッファーの構造体は、マトリックスの 2 つの配列だけです。

**VertexShaderShared.hlsl**によって含まれる、 **VPRTVertexShader.hlsl**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

各ピクセルのレンダー ターゲットの配列インデックスを設定する必要があります。 次のスニペットでは output.viewId にマップされます、 **SV_RenderTargetArrayIndex**セマンティック。 これにより、レンダー ターゲットの配列インデックスをどのシェーダー ステージから設定するセマンティック、省略可能な Direct3D 11.3 機能のサポートが必要ですこのことに注意してください。

**VPRTVertexShader.hlsl**:

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

**VertexShaderShared.hlsl**によって含まれる、 **VPRTVertexShader.hlsl**:

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

既存のインスタンスを使用する場合は、ステレオに描画するには、このメソッドを使用して描画手法のレンダリング先の配列、通常存在するインスタンスの数の 2 倍の描画が行う必要があるすべて。 シェーダーで分割**input.instId**を元のインスタンス ID を取得する 2 でオブジェクトごとのデータのバッファー (など) にインデックスことができます。 `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>HoloLens のステレオのコンテンツを表示する方法の重要な注意事項

Windows Mixed Reality; 任意のシェーダー ステージのレンダー ターゲットの配列インデックスを設定する機能をサポートしています通常、これは、ジオメトリ シェーダー ステージは、direct3d11 のセマンティックが定義された方法のためにのみ実行できるタスクです。 ここでは、頂点とピクセル シェーダーのステージ セットのみでレンダリング パイプラインを設定する方法の完全な例を紹介します。 シェーダー コードは、前述のようです。

**SpinningCubeRenderer::Render**:

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>非 HoloLens デバイスでのレンダリングに関する重要な注意事項

頂点シェーダーのレンダー ターゲットの配列インデックスを設定するには、オプションの Direct3D 11.3 機能、HoloLens をサポートして、グラフィックス ドライバーをサポートしている必要があります。 アプリが安全にだけ、レンダリングの手法を実装することができ、Microsoft HoloLens で実行されているすべての要件を満たすはします。

エミュレーターを使用する、HoloLens、holographic アプリのための強力な開発ツールと Windows 10 Pc に接続されている Windows Mixed Reality ヘッドセット没入型のデバイスをサポートするケースがあります。 そのため、すべての Windows Mixed Reality - もに組み込まれている、Windows Holographic のアプリケーション テンプレートと HoloLens 非表示のパスのサポートします。 テンプレート コードでは、holographic アプリを開発用 PC に GPU 上で実行を有効にするコードが表示されます。 ここでは、方法、 **DeviceResources**クラスのこの省略可能な機能のサポートを確認します。

**DeviceResources::CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

この省略可能な機能なしのレンダリングをサポートするために、アプリは、レンダー ターゲットの配列インデックスを設定するのにジオメトリ シェーダーを使用する必要があります。 このスニペットを追加すると*後* **VSSetConstantBuffers**と*する前に* **PSSetShader**の前に示したコード例HoloLens のステレオのレンダリング方法を説明するセクション。

**SpinningCubeRenderer::Render**:

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

**HLSL 注**:この場合、レンダー ターゲットの配列インデックスを常に許可シェーダー TEXCOORD0 などのセマンティックを使用してジオメトリ シェーダーに渡される少し変更を加えた頂点シェーダーも読み込む必要があります。 ジオメトリ シェーダーはすべての作業を実行する必要はありません。テンプレートのジオメトリ シェーダーは、レンダー ターゲットの配列インデックス、SV_RenderTargetArrayIndex のセマンティックを設定するために使用を除き、すべてのデータを通過します。

アプリ テンプレートのコード**GeometryShader.hlsl**:

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

## <a name="present"></a>Present

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>スワップ チェーンを提示する holographic のフレームを有効にします。

Windows Mixed Reality では、システムは、スワップ チェーンを制御します。 システムは、各 holographic カメラ、高品質なユーザー エクスペリエンスを実現するフレームの表示を管理します。 提供ビューポートの update フレームごとに、イメージの安定化や Mixed Reality キャプチャなどのシステムの側面を最適化するために各カメラ。 そのため、DirectX を使用して holographic アプリが呼び出さない**存在**DXGI スワップ チェーンです。 代わりに、使用、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>クラスが完了したら、フレームのすべてのスワップを提示する描画します。

**DeviceResources::Present**:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

既定では、この API は、フレームを返す前に完了を待ちます。 Holographic アプリは、遅延を低減し、予測の holographic フレームからより良い結果では、このため、新しいフレームの作業を開始する前に完了する前のフレームを待機する必要があります。 そうでは、ハードのルールおよびフレームを表示するために 1 つの画面のリフレッシュよりも長い時間がかかるが HolographicFramePresentWaitBehavior パラメーターを渡すことによってでこの待機を無効にできますがある場合<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>します。 この場合、GPU 上で継続的な負荷を維持するために、非同期のレンダリング スレッドを使用すると可能性があります。 HoloLens デバイスのリフレッシュ レートは、60 hz、1 つのフレームが約 16 ミリ秒の期間を持つことに注意してください。 90 hz; 60 hz の範囲はイマーシブ ヘッドセット デバイス90 hz で表示を更新するときに、各フレームは約 11 ms の継続時間があります。

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>協力、HolographicFrame DeviceLost シナリオを処理します。

DirectX 11 アプリは、通常 DXGI スワップ チェーンのによって返される HRESULT を確認する必要は**存在**関数があったかを**DeviceLost**エラー。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>クラスでは、これを処理できます。 検査、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a>をリリースして、Direct3D デバイスとデバイス ベースのリソースを再作成する必要があるかどうかを返します。

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

Direct3D デバイスが失われた場合は、再作成した場合は、通知する必要があります、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>に新しいデバイスの使用を開始します。 スワップ チェーンは、このデバイスの再作成されます。

**DeviceResources::InitializeUsingHolographicSpace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

フレームが表示されたら、メイン プログラム ループに戻りますし、次のフレームを続行することを許可できます。

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>ハイブリッド グラフィック Pc や複合現実のアプリケーション

Windows 10 Creators Update の Pc で構成することがあります**両方**Gpu の不連続値と統合します。 これらの種類のコンピューターで Windows は、アダプターに接続されている、ヘッドセットを選択します。 アプリケーションは、DirectX デバイスを作成しますが、同じアダプターを使用することを確認する必要があります。

最も一般的な Direct3D サンプルのコードでは、可能性のあるハイブリッド システムのないヘッドセットで使ったものと同じ既定のハードウェア アダプターを使用して DirectX デバイスを作成するを示します。

これが原因で問題を回避するには、使用、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a>いずれかから<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>します。PrimaryAdapterId() または<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>します。AdapterId() します。 この 6 または 7 ですは IDXGIFactory4.EnumAdapterByLuid を使用して適切な DXGIAdapter を選択するために使用できます。

**DeviceResources::InitializeUsingHolographicSpace**:

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

コードを**更新 DeviceResources::CreateDeviceResources IDXGIAdapter を使用するには**

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

**ハイブリッドのグラフィックスとメディア ファンデーション**

ハイブリッド システムで Media Foundation を使用すると、ビデオは表示されませんか、ビデオのテクスチャが破損している問題が発生する可能性があります。 これは、既に説明したようにシステムの動作は既定ではメディア ファンデーションのために発生します。 一部のシナリオでは、個別 ID3D11Device を作成するマルチ スレッドをサポートし、フラグが設定されて正しい作成する必要があります。

ID3D11Device を初期化するときに、D3D11_CREATE_DEVICE_VIDEO_SUPPORT フラグは、D3D11_CREATE_DEVICE_FLAG の一部として定義する必要があります。 デバイスとコンテキストが作成されると、呼び出す<a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a>有効にするマルチ スレッドです。 使用してデバイスを関連付ける、 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>を使用して、 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a>関数。

コードを **、ID3D11Device を関連付ける IMFDXGIDeviceManager**:

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

## <a name="see-also"></a>関連項目
* [DirectX の座標系](coordinate-systems-in-directx.md)
* [HoloLens のエミュレーターを使用する](using-the-hololens-emulator.md)
