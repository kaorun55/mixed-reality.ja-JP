---
title: DirectX での空間のサウンド
description: 空間のサウンドを XAudio2 と xAPO オーディオ ライブラリを使用して DirectX に基づく Windows Mixed Reality アプリに追加します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows xAPO、オーディオ ライブラリ、チュートリアルでは、DirectX が実際には、空間のサウンド、アプリ、XAudio2、低レベルの混在
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605141"
---
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="f183f-104">DirectX での空間のサウンド</span><span class="sxs-lookup"><span data-stu-id="f183f-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="f183f-105">使用して DirectX に基づく Windows Mixed Reality アプリ空間のサウンドを追加、 [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx)と[xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx)オーディオ ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="f183f-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="f183f-106">このトピックでは、HolographicHRTFAudioSample からのサンプル コードを使用します。</span><span class="sxs-lookup"><span data-stu-id="f183f-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="f183f-107">この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。</span><span class="sxs-lookup"><span data-stu-id="f183f-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="f183f-108">概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f183f-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="f183f-109">Head 相対空間サウンドの概要</span><span class="sxs-lookup"><span data-stu-id="f183f-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="f183f-110">空間のサウンドとして実装されている、**オーディオ処理オブジェクト (APO)** を使用して、**ヘッド転送関数 (HRTF) に関連**をフィルター処理*spatialize*通常のオーディオ ストリーム。</span><span class="sxs-lookup"><span data-stu-id="f183f-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="f183f-111">Pch.h オーディオ Api にアクセスするには、これらのヘッダー ファイルを含めます。</span><span class="sxs-lookup"><span data-stu-id="f183f-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="f183f-112">XAudio2.h</span><span class="sxs-lookup"><span data-stu-id="f183f-112">XAudio2.h</span></span>
* <span data-ttu-id="f183f-113">xapo.h</span><span class="sxs-lookup"><span data-stu-id="f183f-113">xapo.h</span></span>
* <span data-ttu-id="f183f-114">hrtfapoapi.h</span><span class="sxs-lookup"><span data-stu-id="f183f-114">hrtfapoapi.h</span></span>

<span data-ttu-id="f183f-115">サウンドの空間を設定します。</span><span class="sxs-lookup"><span data-stu-id="f183f-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="f183f-116">呼び出す[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) HRTF オーディオ新しい APO を初期化します。</span><span class="sxs-lookup"><span data-stu-id="f183f-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="f183f-117">割り当てる、 [HRTF パラメーター](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx)と[HRTF 環境](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx)空間サウンド APO の音響の特性を定義します。</span><span class="sxs-lookup"><span data-stu-id="f183f-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="f183f-118">HRTF 処理 XAudio2 エンジンを設定します。</span><span class="sxs-lookup"><span data-stu-id="f183f-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="f183f-119">作成、 [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx)オブジェクトと呼び出し[開始](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)します。</span><span class="sxs-lookup"><span data-stu-id="f183f-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="f183f-120">DirectX アプリで HRTF とサウンドの空間を実装します。</span><span class="sxs-lookup"><span data-stu-id="f183f-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="f183f-121">HRTF APO をさまざまなパラメーターと環境を構成することによって、さまざまな効果を実現できます。</span><span class="sxs-lookup"><span data-stu-id="f183f-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="f183f-122">次のコードを使用して、可能性を追求します。</span><span class="sxs-lookup"><span data-stu-id="f183f-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="f183f-123">ここからユニバーサル Windows プラットフォームのコード サンプルをダウンロードします。[サウンドの空間のサンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="f183f-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="f183f-124">ヘルパー型は、これらのファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f183f-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="f183f-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp):Media Foundation を使用してオーディオ ファイルを読み込み、 [IMFSourceReader インターフェイス](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx)します。</span><span class="sxs-lookup"><span data-stu-id="f183f-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="f183f-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h):実装、 **SetupXAudio2** HRTF 処理 XAudio2 を初期化します。</span><span class="sxs-lookup"><span data-stu-id="f183f-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="f183f-127">全方向のソースの空間のサウンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="f183f-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="f183f-128">いくつかホログラム、ユーザーの環境では、全方向に均等にサウンドを出力します。</span><span class="sxs-lookup"><span data-stu-id="f183f-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="f183f-129">次のコードでは、全方向サウンドを出力する、APO を初期化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f183f-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="f183f-130">この例でこの概念に適用、回転するキューブ Windows Holographic のアプリ テンプレートから。</span><span class="sxs-lookup"><span data-stu-id="f183f-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="f183f-131">完全なコード一覧は、次を参照してください。 [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp)します。</span><span class="sxs-lookup"><span data-stu-id="f183f-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="f183f-132">**ウィンドウの空間サウンド エンジンでは、48 k samplerate が再生のみサポートされます。Unity のように、ミドルウェアのほとんどのプログラムは目的の形式にサウンド ファイルを自動的に変換します。 が、これはクラッシュまたはなどの望ましくない動作を防ぐために非常に重要な場合は、オーディオ システムまたは独自に行うより低いレベルで試行錯誤を開始します。HRTF システムに失敗しました。**</span><span class="sxs-lookup"><span data-stu-id="f183f-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="f183f-133">まず、APO を初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f183f-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="f183f-134">選択したら、これを実行する、holographic サンプル アプリで、 **HolographicSpace**します。</span><span class="sxs-lookup"><span data-stu-id="f183f-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="f183f-135">*HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="f183f-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="f183f-136">初期化、実装から*OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="f183f-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

```
// Initializes an APO that emits sound equally in all directions.
HRESULT OmnidirectionalSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        // Passing in nullptr as the first arg for HrtfApoInit initializes the APO with defaults of
        // omnidirectional sound with natural distance decay behavior.
        // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( nullptr, &xapo );
    }

    if ( SUCCEEDED( hr ) )
    {
        // _hrtfParams is of type ComPtr<IXAPOHrtfParameters>.
        hr = xapo.As( &_hrtfParams );
    }

    // Set the default environment.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice.
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;

        // _sourceVoice is of type IXAudio2SourceVoice*.
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

<span data-ttu-id="f183f-137">HRTF で、APO が構成された後に呼び出す[開始](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)オーディオを再生するソース音声にします。</span><span class="sxs-lookup"><span data-stu-id="f183f-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="f183f-138">このサンプル アプリで、キューブから音が聞こえるように続行できるように、ループの配置を選択します。</span><span class="sxs-lookup"><span data-stu-id="f183f-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="f183f-139">*HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="f183f-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="f183f-140">*OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="f183f-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="f183f-141">ここで、フレームを更新するたびに、デバイス自体を基準とホログラムの位置を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f183f-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="f183f-142">HRTF 位置は常に、ユーザーの head、ヘッドの位置と向きを基準に表現するためです。</span><span class="sxs-lookup"><span data-stu-id="f183f-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="f183f-143">これを行うには、HolographicSpace に、SpatialStationaryFrameOfReference 座標システムから、デバイス自体に固定されている座標系に変換行列を構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f183f-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="f183f-144">*HolographicHrtfAudioSampleMain::Update()*:</span><span class="sxs-lookup"><span data-stu-id="f183f-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

```
m_spinningCubeRenderer->Update(m_timer);

SpatialPointerPose^ currentPose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
if (currentPose != nullptr)
{
    // Use a coordinate system built from a pointer pose.
    SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
    if (pose != nullptr)
    {
        float3 headPosition = pose->Head->Position;
        float3 headUp = pose->Head->UpDirection;
        float3 headDirection = pose->Head->ForwardDirection;

        // To construct a rotation matrix, we need three vectors that are mutually orthogonal.
        // The first vector is the gaze vector.
        float3 negativeZAxis = normalize(headDirection);

        // The second vector should end up pointing away from the horizontal plane of the device.
        // We first guess by using the head "up" direction.
        float3 positiveYAxisGuess = normalize(headUp);

        // The third vector completes the set by being orthogonal to the other two.
        float3 positiveXAxis = normalize(cross(negativeZAxis, positiveYAxisGuess));

        // Now, we can correct our "up" vector guess by redetermining orthogonality.
        float3 positiveYAxis = normalize(cross(negativeZAxis, positiveXAxis));

        // The rotation matrix is formed as a standard basis rotation.
        float4x4 rotationTransform =
            {
            positiveXAxis.x, positiveYAxis.x, negativeZAxis.x, 0.f,
            positiveXAxis.y, positiveYAxis.y, negativeZAxis.y, 0.f,
            positiveXAxis.z, positiveYAxis.z, negativeZAxis.z, 0.f,
            0.f, 0.f, 0.f, 1.f,
            };

        // The translate transform can be constructed using the Windows::Foundation::Numerics API.
        float4x4 translationTransform = make_float4x4_translation(-headPosition);

        // Now, we have a basis transform from our spatial coordinate system to a device-relative
        // coordinate system.
        float4x4 coordinateSystemTransform = translationTransform * rotationTransform;

        // Reinterpret the cube position in the device's coordinate system.
        float3 cubeRelativeToHead = transform(m_spinningCubeRenderer->GetPosition(), coordinateSystemTransform);

        // Note that at (0, 0, 0) exactly, the HRTF audio will simply pass through audio. We can use a minimal offset
        // to simulate a zero distance when the hologram position vector is exactly at the device origin in order to
        // allow HRTF to continue functioning in this edge case.
        float distanceFromHologramToHead = length(cubeRelativeToHead);
        static const float distanceMin = 0.00001f;
        if (distanceFromHologramToHead < distanceMin)
        {
            cubeRelativeToHead = float3(0.f, distanceMin, 0.f);
        }

        // Position the spatial sound source on the hologram.
        m_omnidirectionalSound.OnUpdate(cubeRelativeToHead);

        // For debugging, it can be interesting to observe the distance in the debugger.
        /*
        std::wstring distanceString = L"Distance from hologram to head: ";
        distanceString += std::to_wstring(distanceFromHologramToHead);
        distanceString += L"\n";
        OutputDebugStringW(distanceString.c_str());
        */
    }
}
```

<span data-ttu-id="f183f-145">HRTF 位置は、OmnidirectionalSound ヘルパー クラスによってサウンド APO に直接適用されます。</span><span class="sxs-lookup"><span data-stu-id="f183f-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="f183f-146">*OmnidirectionalSound::OnUpdate*:</span><span class="sxs-lookup"><span data-stu-id="f183f-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="f183f-147">以上で作業は終了です。</span><span class="sxs-lookup"><span data-stu-id="f183f-147">That's it!</span></span> <span data-ttu-id="f183f-148">HRTF オーディオと Windows Holographic でにできることについての詳細は閲覧を続行します。</span><span class="sxs-lookup"><span data-stu-id="f183f-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="f183f-149">空間のサウンドを方向性のあるソースを初期化します。</span><span class="sxs-lookup"><span data-stu-id="f183f-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="f183f-150">いくつかホログラム、ユーザーの環境では、一方向でほとんどのサウンドを出力します。</span><span class="sxs-lookup"><span data-stu-id="f183f-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="f183f-151">このサウンドのパターンの名前は*cardioid*マンガ ハートが似ているためです。</span><span class="sxs-lookup"><span data-stu-id="f183f-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="f183f-152">次のコードは、サウンドの方向を出力する、APO を初期化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f183f-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="f183f-153">完全なコード一覧は、次を参照してください。 [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp)します。</span><span class="sxs-lookup"><span data-stu-id="f183f-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="f183f-154">HRTF で、APO が構成された後に呼び出す[開始](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)オーディオを再生するソース音声にします。</span><span class="sxs-lookup"><span data-stu-id="f183f-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

```
// Initializes an APO that emits directional sound.
HRESULT CardioidSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );
    if ( SUCCEEDED( hr ) )
    {
        // Initialize with "Scaling" fully directional and "Order" with broad radiation pattern.
        // As the order goes higher, the cardioid directivity region becomes narrower.
        // Any direct path signal outside of the directivity region will be attenuated based on the scaling factor.
        // For example, if scaling is set to 1 (fully directional) the direct path signal outside of the directivity
        // region will be fully attenuated and only the reflections from the environment will be audible.
        hr = ConfigureApo( 1.0f, 4.0f );
    }
    return hr;
}

HRESULT CardioidSound::ConfigureApo( float scaling, float order )
{
    // Cardioid directivity configuration:
    // Directivity is specified at xAPO instance initialization and can't be changed per frame.
    // To change directivity, stop audio processing and reinitialize another APO instance with the new directivity.
    HrtfDirectivityCardioid cardioid;
    cardioid.directivity.type = HrtfDirectivityType::Cardioid;
    cardioid.directivity.scaling = scaling;
    cardioid.order = order;

    // APO intialization
    HrtfApoInit apoInit;
    apoInit.directivity = &cardioid.directivity;
    apoInit.distanceDecay = nullptr; // nullptr specifies natural distance decay behavior (simulates real world)

    // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
    ComPtr<IXAPO> xapo;
    auto hr = CreateHrtfApo( &apoInit, &xapo );

    if ( SUCCEEDED( hr ) )
    {
        hr = xapo.As( &_hrtfParams );
    }

    // Set the initial environment.
    // Environment settings configure the "distance cues" used to compute the early and late reverberations.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( _HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

### <a name="implement-custom-decay"></a><span data-ttu-id="f183f-155">カスタムの減衰を実装します。</span><span class="sxs-lookup"><span data-stu-id="f183f-155">Implement custom decay</span></span>

<span data-ttu-id="f183f-156">位置空間サウンドが距離れなくなったときや、どのような距離にあることをカットして完全にレートをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="f183f-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="f183f-157">空間のサウンドの減衰のカスタム動作を実装するには、設定、 [HrtfDistanceDecay 構造体](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx)に割り当てると、 **distanceDecay**フィールドに、 [HrtfApoInit 構造体](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx)渡す前に、 [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)関数。</span><span class="sxs-lookup"><span data-stu-id="f183f-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="f183f-158">次のコードを追加、**初期化**減衰のカスタム動作を指定する前に示したメソッド。</span><span class="sxs-lookup"><span data-stu-id="f183f-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="f183f-159">完全なコード一覧は、次を参照してください。 [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp)します。</span><span class="sxs-lookup"><span data-stu-id="f183f-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

```
HRESULT CustomDecaySound::Initialize( LPCWSTR filename )
{
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        HrtfDistanceDecay customDecay;
        customDecay.type = HrtfDistanceDecayType::CustomDecay;               // Custom decay behavior, we'll pass in the gain value on every frame.
        customDecay.maxGain = 0;                                             // 0dB max gain
        customDecay.minGain = -96.0f;                                        // -96dB min gain
        customDecay.unityGainDistance = HRTF_DEFAULT_UNITY_GAIN_DISTANCE;    // Default unity gain distance
        customDecay.cutoffDistance = HRTF_DEFAULT_CUTOFF_DISTANCE;           // Default cutoff distance

        // Setting the directivity to nullptr specifies omnidirectional sound.
        HrtfApoInit init;
        init.directivity = nullptr;
        init.distanceDecay = &customDecay;

        // CreateHrtfApo will fail with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( &init, &xapo );
    }
...
}
```
