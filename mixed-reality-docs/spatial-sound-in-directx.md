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
# <a name="spatial-sound-in-directx"></a>DirectX での空間のサウンド

使用して DirectX に基づく Windows Mixed Reality アプリ空間のサウンドを追加、 [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx)と[xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx)オーディオ ライブラリ。

このトピックでは、HolographicHRTFAudioSample からのサンプル コードを使用します。

>[!NOTE]
>この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。  概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。

## <a name="overview-of-head-relative-spatial-sound"></a>Head 相対空間サウンドの概要

空間のサウンドとして実装されている、**オーディオ処理オブジェクト (APO)** を使用して、**ヘッド転送関数 (HRTF) に関連**をフィルター処理*spatialize*通常のオーディオ ストリーム。

Pch.h オーディオ Api にアクセスするには、これらのヘッダー ファイルを含めます。
* XAudio2.h
* xapo.h
* hrtfapoapi.h

サウンドの空間を設定します。
1. 呼び出す[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) HRTF オーディオ新しい APO を初期化します。
2. 割り当てる、 [HRTF パラメーター](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx)と[HRTF 環境](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx)空間サウンド APO の音響の特性を定義します。
3. HRTF 処理 XAudio2 エンジンを設定します。
4. 作成、 [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx)オブジェクトと呼び出し[開始](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)します。

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>DirectX アプリで HRTF とサウンドの空間を実装します。

HRTF APO をさまざまなパラメーターと環境を構成することによって、さまざまな効果を実現できます。 次のコードを使用して、可能性を追求します。 ここからユニバーサル Windows プラットフォームのコード サンプルをダウンロードします。[サウンドの空間のサンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

ヘルパー型は、これらのファイルで使用できます。
* [AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp):Media Foundation を使用してオーディオ ファイルを読み込み、 [IMFSourceReader インターフェイス](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx)します。
* [XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h):実装、 **SetupXAudio2** HRTF 処理 XAudio2 を初期化します。

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>全方向のソースの空間のサウンドを追加します。

いくつかホログラム、ユーザーの環境では、全方向に均等にサウンドを出力します。 次のコードでは、全方向サウンドを出力する、APO を初期化する方法を示します。 この例でこの概念に適用、回転するキューブ Windows Holographic のアプリ テンプレートから。 完全なコード一覧は、次を参照してください。 [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp)します。

**ウィンドウの空間サウンド エンジンでは、48 k samplerate が再生のみサポートされます。Unity のように、ミドルウェアのほとんどのプログラムは目的の形式にサウンド ファイルを自動的に変換します。 が、これはクラッシュまたはなどの望ましくない動作を防ぐために非常に重要な場合は、オーディオ システムまたは独自に行うより低いレベルで試行錯誤を開始します。HRTF システムに失敗しました。**

まず、APO を初期化する必要があります。 選択したら、これを実行する、holographic サンプル アプリで、 **HolographicSpace**します。

*HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

初期化、実装から*OmnidirectionalSound.cpp*:

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

HRTF で、APO が構成された後に呼び出す[開始](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)オーディオを再生するソース音声にします。 このサンプル アプリで、キューブから音が聞こえるように続行できるように、ループの配置を選択します。

*HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

*OmnidirectionalSound.cpp*:

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

ここで、フレームを更新するたびに、デバイス自体を基準とホログラムの位置を更新する必要があります。 HRTF 位置は常に、ユーザーの head、ヘッドの位置と向きを基準に表現するためです。

これを行うには、HolographicSpace に、SpatialStationaryFrameOfReference 座標システムから、デバイス自体に固定されている座標系に変換行列を構築する必要があります。

*HolographicHrtfAudioSampleMain::Update()*:

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

HRTF 位置は、OmnidirectionalSound ヘルパー クラスによってサウンド APO に直接適用されます。

*OmnidirectionalSound::OnUpdate*:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

以上で作業は終了です。 HRTF オーディオと Windows Holographic でにできることについての詳細は閲覧を続行します。

### <a name="initialize-spatial-sound-for-a-directional-source"></a>空間のサウンドを方向性のあるソースを初期化します。

いくつかホログラム、ユーザーの環境では、一方向でほとんどのサウンドを出力します。 このサウンドのパターンの名前は*cardioid*マンガ ハートが似ているためです。 次のコードは、サウンドの方向を出力する、APO を初期化する方法を示します。 完全なコード一覧は、次を参照してください。 [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp)します。

HRTF で、APO が構成された後に呼び出す[開始](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)オーディオを再生するソース音声にします。

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

### <a name="implement-custom-decay"></a>カスタムの減衰を実装します。

位置空間サウンドが距離れなくなったときや、どのような距離にあることをカットして完全にレートをオーバーライドできます。 空間のサウンドの減衰のカスタム動作を実装するには、設定、 [HrtfDistanceDecay 構造体](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx)に割り当てると、 **distanceDecay**フィールドに、 [HrtfApoInit 構造体](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx)渡す前に、 [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)関数。

次のコードを追加、**初期化**減衰のカスタム動作を指定する前に示したメソッド。 完全なコード一覧は、次を参照してください。 [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp)します。

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
