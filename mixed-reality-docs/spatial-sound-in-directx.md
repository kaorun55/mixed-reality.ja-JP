---
title: DirectX の空間サウンド
description: XAudio2 および xAPO オーディオライブラリを使用して、DirectX に基づく Windows Mixed Reality アプリに空間サウンドを追加します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixed reality、空間サウンド、アプリ、XAudio2、低レベル、xAPO、オーディオライブラリ、チュートリアル、DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550435"
---
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="f0f06-104">DirectX の空間サウンド</span><span class="sxs-lookup"><span data-stu-id="f0f06-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="f0f06-105">[XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx)および[xapo](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx)オーディオライブラリを使用して、DirectX に基づく Windows Mixed Reality アプリに空間サウンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="f0f06-106">このトピックでは、HolographicHRTFAudioSample のサンプルコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="f0f06-107">この記事のコードスニペットでは、現在、 C++ [ C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用されてC++いる C + c++ 17 準拠の/WinRT ではなく、/cx の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f0f06-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="f0f06-108">これらの概念は、プロジェクトC++の場合と同じですが、コードを変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0f06-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="f0f06-109">ヘッド相対空間サウンドの概要</span><span class="sxs-lookup"><span data-stu-id="f0f06-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="f0f06-110">空間サウンドは、通常のオーディオストリームを*spatialize*するために**head 関連の転送関数 (HRTF)** フィルターを使用する**オーディオ処理オブジェクト (APO)** として実装されます。</span><span class="sxs-lookup"><span data-stu-id="f0f06-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="f0f06-111">次のヘッダーファイルを pch に含めて、オーディオ Api にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="f0f06-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="f0f06-112">XAudio2</span><span class="sxs-lookup"><span data-stu-id="f0f06-112">XAudio2.h</span></span>
* <span data-ttu-id="f0f06-113">xapo. h</span><span class="sxs-lookup"><span data-stu-id="f0f06-113">xapo.h</span></span>
* <span data-ttu-id="f0f06-114">hrtfアポストロフィ api .h</span><span class="sxs-lookup"><span data-stu-id="f0f06-114">hrtfapoapi.h</span></span>

<span data-ttu-id="f0f06-115">空間サウンドを設定するには:</span><span class="sxs-lookup"><span data-stu-id="f0f06-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="f0f06-116">[Createhrtfapo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)を呼び出して、HRTF audio の新しい APO を初期化します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="f0f06-117">[HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx)と[HRTF 環境](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx)を割り当てて、空間サウンド APO の音響特性を定義します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="f0f06-118">XAudio2 engine を HRTF 処理用に設定します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="f0f06-119">[IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx)オブジェクトを作成し、 [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="f0f06-120">DirectX アプリに HRTF と空間サウンドを実装する</span><span class="sxs-lookup"><span data-stu-id="f0f06-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="f0f06-121">異なるパラメーターと環境で HRTF APO を構成することによって、さまざまな効果を実現できます。</span><span class="sxs-lookup"><span data-stu-id="f0f06-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="f0f06-122">次のコードを使用して、可能性を調査します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="f0f06-123">ここからユニバーサル Windows プラットフォームコードサンプルをダウンロードします。[空間サウンドのサンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="f0f06-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="f0f06-124">ヘルパーの種類は、次のファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f06-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="f0f06-125">[AudioFileReader](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp):メディアファンデーションと[IMFSourceReader インターフェイス](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx)を使用してオーディオファイルを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="f0f06-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="f0f06-126">[XAudio2Helpers](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h):**SetupXAudio2**関数を実装して、HRTF Processing の XAudio2 を初期化します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="f0f06-127">無指向性ソースの空間サウンドを追加する</span><span class="sxs-lookup"><span data-stu-id="f0f06-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="f0f06-128">ユーザーの周囲の一部のホログラムは、すべての方向に同じようにサウンドを出力します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="f0f06-129">次のコードは、APO を初期化して全方向音を出力する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f0f06-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="f0f06-130">この例では、この概念を Windows Holographic アプリテンプレートからスピンするキューブに適用します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="f0f06-131">完全なコードリストについては、「 [OmnidirectionalSound](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f06-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="f0f06-132">**ウィンドウの空間サウンドエンジンは、再生用に 48 k samplerate のみをサポートしています。Unity などのほとんどのミドルウェアプログラムは、サウンドファイルを目的の形式に自動的に変換しますが、オーディオシステムの低レベルで考察を開始する場合や、独自の動作を行う場合は、次のようなクラッシュや望ましくない動作を防ぐために注意することが非常に重要です。HRTF システムエラー。**</span><span class="sxs-lookup"><span data-stu-id="f0f06-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="f0f06-133">まず、APO を初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0f06-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="f0f06-134">この holographic サンプルアプリでは、 **HolographicSpace**を用意した後にこれを行うことを選択します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="f0f06-135">From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :</span><span class="sxs-lookup"><span data-stu-id="f0f06-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="f0f06-136">*OmnidirectionalSound*からの Initialize の実装:</span><span class="sxs-lookup"><span data-stu-id="f0f06-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

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

<span data-ttu-id="f0f06-137">HRTF に対して APO が構成されたら、ソース音声で[Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)を呼び出してオーディオを再生します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="f0f06-138">このサンプルアプリでは、キューブからのサウンドを引き続き再生できるように、ループに配置します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="f0f06-139">From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :</span><span class="sxs-lookup"><span data-stu-id="f0f06-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="f0f06-140">*OmnidirectionalSound*から:</span><span class="sxs-lookup"><span data-stu-id="f0f06-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="f0f06-141">ここで、フレームを更新するたびに、デバイス自体に対するホログラムの位置を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0f06-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="f0f06-142">これは、HRTF の位置は常にユーザーの先頭に対して相対的に表されます。これは、head 位置と向きを含みます。</span><span class="sxs-lookup"><span data-stu-id="f0f06-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="f0f06-143">HolographicSpace でこれを行うには、SpatialStationaryFrameOfReference 座標系から、デバイス自体に固定されている座標系に変換行列を構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0f06-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="f0f06-144">*HolographicHrtfAudioSampleMain:: Update ()* から:</span><span class="sxs-lookup"><span data-stu-id="f0f06-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

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

<span data-ttu-id="f0f06-145">HRTF position は、OmnidirectionalSound helper クラスによって、そのサウンドが APO に直接適用されます。</span><span class="sxs-lookup"><span data-stu-id="f0f06-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="f0f06-146">*OmnidirectionalSound:: OnUpdate*から:</span><span class="sxs-lookup"><span data-stu-id="f0f06-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="f0f06-147">これで完了です。</span><span class="sxs-lookup"><span data-stu-id="f0f06-147">That's it!</span></span> <span data-ttu-id="f0f06-148">HRTF audio と Windows Holographic でできることの詳細については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f06-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="f0f06-149">方向変換元の空間サウンドを初期化する</span><span class="sxs-lookup"><span data-stu-id="f0f06-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="f0f06-150">ユーザーの周囲の一部のホログラムは、主に一方向にサウンドを出力します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="f0f06-151">このサウンドパターンは、漫画のように見えるため、 *cardioid*という名前になります。</span><span class="sxs-lookup"><span data-stu-id="f0f06-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="f0f06-152">次のコードは、APO を初期化して指向性音を出力する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f0f06-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="f0f06-153">完全なコードリストについては、「 [CardioidSound](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f06-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="f0f06-154">HRTF に対して APO が構成されたら、ソース音声で[Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)を呼び出してオーディオを再生します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

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

### <a name="implement-custom-decay"></a><span data-ttu-id="f0f06-155">カスタムの減衰を実装する</span><span class="sxs-lookup"><span data-stu-id="f0f06-155">Implement custom decay</span></span>

<span data-ttu-id="f0f06-156">空間サウンドがどの程度の距離になるか、または完全に外に出てくる距離を上書きすることができます。</span><span class="sxs-lookup"><span data-stu-id="f0f06-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="f0f06-157">空間サウンドにカスタムの減衰動作を実装するには、 [HrtfDistanceDecay 構造体](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx)を設定し、それを[Hrtfアポストロフィ init 構造体](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx)の**distanceDecay**フィールドに代入してから、 [createhrtfapo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)関数に渡します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="f0f06-158">前に示した**Initialize**メソッドに次のコードを追加して、カスタムの減衰動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0f06-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="f0f06-159">完全なコードリストについては、「[CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp)」を参照してくださいを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f06-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

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
