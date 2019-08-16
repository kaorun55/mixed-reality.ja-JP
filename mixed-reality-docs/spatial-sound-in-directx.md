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
# <a name="spatial-sound-in-directx"></a>DirectX の空間サウンド

[XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx)および[xapo](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx)オーディオライブラリを使用して、DirectX に基づく Windows Mixed Reality アプリに空間サウンドを追加します。

このトピックでは、HolographicHRTFAudioSample のサンプルコードを使用します。

>[!NOTE]
>この記事のコードスニペットでは、現在、 C++ [ C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用されてC++いる C + c++ 17 準拠の/WinRT ではなく、/cx の使用方法を示しています。  これらの概念は、プロジェクトC++の場合と同じですが、コードを変換する必要があります。

## <a name="overview-of-head-relative-spatial-sound"></a>ヘッド相対空間サウンドの概要

空間サウンドは、通常のオーディオストリームを*spatialize*するために**head 関連の転送関数 (HRTF)** フィルターを使用する**オーディオ処理オブジェクト (APO)** として実装されます。

次のヘッダーファイルを pch に含めて、オーディオ Api にアクセスします。
* XAudio2
* xapo. h
* hrtfアポストロフィ api .h

空間サウンドを設定するには:
1. [Createhrtfapo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)を呼び出して、HRTF audio の新しい APO を初期化します。
2. [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx)と[HRTF 環境](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx)を割り当てて、空間サウンド APO の音響特性を定義します。
3. XAudio2 engine を HRTF 処理用に設定します。
4. [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx)オブジェクトを作成し、 [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)を呼び出します。

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>DirectX アプリに HRTF と空間サウンドを実装する

異なるパラメーターと環境で HRTF APO を構成することによって、さまざまな効果を実現できます。 次のコードを使用して、可能性を調査します。 ここからユニバーサル Windows プラットフォームコードサンプルをダウンロードします。[空間サウンドのサンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

ヘルパーの種類は、次のファイルで使用できます。
* [AudioFileReader](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp):メディアファンデーションと[IMFSourceReader インターフェイス](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx)を使用してオーディオファイルを読み込みます。
* [XAudio2Helpers](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h):**SetupXAudio2**関数を実装して、HRTF Processing の XAudio2 を初期化します。

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>無指向性ソースの空間サウンドを追加する

ユーザーの周囲の一部のホログラムは、すべての方向に同じようにサウンドを出力します。 次のコードは、APO を初期化して全方向音を出力する方法を示しています。 この例では、この概念を Windows Holographic アプリテンプレートからスピンするキューブに適用します。 完全なコードリストについては、「 [OmnidirectionalSound](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp)」を参照してください。

**ウィンドウの空間サウンドエンジンは、再生用に 48 k samplerate のみをサポートしています。Unity などのほとんどのミドルウェアプログラムは、サウンドファイルを目的の形式に自動的に変換しますが、オーディオシステムの低レベルで考察を開始する場合や、独自の動作を行う場合は、次のようなクラッシュや望ましくない動作を防ぐために注意することが非常に重要です。HRTF システムエラー。**

まず、APO を初期化する必要があります。 この holographic サンプルアプリでは、 **HolographicSpace**を用意した後にこれを行うことを選択します。

From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

*OmnidirectionalSound*からの Initialize の実装:

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

HRTF に対して APO が構成されたら、ソース音声で[Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)を呼び出してオーディオを再生します。 このサンプルアプリでは、キューブからのサウンドを引き続き再生できるように、ループに配置します。

From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

*OmnidirectionalSound*から:

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

ここで、フレームを更新するたびに、デバイス自体に対するホログラムの位置を更新する必要があります。 これは、HRTF の位置は常にユーザーの先頭に対して相対的に表されます。これは、head 位置と向きを含みます。

HolographicSpace でこれを行うには、SpatialStationaryFrameOfReference 座標系から、デバイス自体に固定されている座標系に変換行列を構築する必要があります。

*HolographicHrtfAudioSampleMain:: Update ()* から:

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

HRTF position は、OmnidirectionalSound helper クラスによって、そのサウンドが APO に直接適用されます。

*OmnidirectionalSound:: OnUpdate*から:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

これで完了です。 HRTF audio と Windows Holographic でできることの詳細については、「」を参照してください。

### <a name="initialize-spatial-sound-for-a-directional-source"></a>方向変換元の空間サウンドを初期化する

ユーザーの周囲の一部のホログラムは、主に一方向にサウンドを出力します。 このサウンドパターンは、漫画のように見えるため、 *cardioid*という名前になります。 次のコードは、APO を初期化して指向性音を出力する方法を示しています。 完全なコードリストについては、「 [CardioidSound](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) 」を参照してください。

HRTF に対して APO が構成されたら、ソース音声で[Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)を呼び出してオーディオを再生します。

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

### <a name="implement-custom-decay"></a>カスタムの減衰を実装する

空間サウンドがどの程度の距離になるか、または完全に外に出てくる距離を上書きすることができます。 空間サウンドにカスタムの減衰動作を実装するには、 [HrtfDistanceDecay 構造体](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx)を設定し、それを[Hrtfアポストロフィ init 構造体](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx)の**distanceDecay**フィールドに代入してから、 [createhrtfapo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)関数に渡します。

前に示した**Initialize**メソッドに次のコードを追加して、カスタムの減衰動作を指定します。 完全なコードリストについては、「[CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp)」を参照してくださいを参照してください。

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
