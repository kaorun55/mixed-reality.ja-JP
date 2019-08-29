---
title: DirectX でのヘッドと視線
description: ネイティブ DirectX アプリでのヘッド見つめと目の追跡を使用するための開発者ガイド。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 視線、ヘッド見つめ、ヘッドトラッキング、視線追跡、directx、入力、ホログラム
ms.openlocfilehash: 2197f0ba3ecb77188d532d77ba29595c380a039d
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122058"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>DirectX でのヘッドと視線の入力

Windows Mixed Reality では、ユーザーがどのようなことを確認しているかを判断するために、目と下の見つめ入力が使用されます。 これを使用すると、[ヘッドを見つめたりコミット](gaze-and-commit.md)したりする主な入力モデルを利用したり、相互作用の種類のコンテキストを提供したりすることもできます。 API を介して使用できる2種類の宝石ベクトルがあります。ヘッド宝石と視線  どちらも、原点と方向を持つ3次元射線として提供されます。 その後、アプリケーションは、それらのシーンや現実の世界に raycast し、ユーザーの対象を特定できます。

**頭を見つめ**ているのは、ユーザーの頭がポイントされている方向を示しています。 これは、デバイス自体の位置と方向であり、2つのディスプレイの間の中心点を表す位置であると考えてください。 ヘッド宝石は、すべての Mixed Reality デバイスで使用できます。

**視線**は、ユーザーの目が見ている方向を表します。 原点はユーザーの目の間にあります。  これは、視線追跡システムを含む Mixed Reality デバイスで使用できます。

ヘッドと視線の両方には、 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API を使用してアクセスできます。 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を呼び出して、指定されたタイムスタンプと[座標系](coordinate-systems-in-directx.md)で新しい SpatialPointerPose オブジェクトを受け取るだけです。 この SpatialPointerPose には、中心と方向があります。 また、視線追跡が利用可能な場合は、視線の原点と方向も含まれています。

## <a name="using-head-gaze"></a>ヘッドの使用

ヘッド宝石にアクセスするには、まず[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を呼び出して、新しい SpatialPointerPose オブジェクトを受け取ります。 次のパラメーターを渡す必要があります。
 - ヘッド見つめの目的の座標系を表す[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 。 これは、次のコードの*coordinateSystem*変数によって表されます。 詳細については、「[コーディネート系](coordinate-systems-in-directx.md)開発者ガイド」を参照してください。
 - 要求されたヘッドポーズの正確な時刻を表す[タイムスタンプ](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp)。  通常は、現在のフレームが表示される時刻に対応するタイムスタンプを使用します。 この予測された表示タイムスタンプは、現在の[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)からアクセスできる[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)オブジェクトから取得できます。  この HolographicFramePrediction オブジェクトは、次のコードの*予測*変数によって表されます。

 有効な SpatialPointerPose を作成すると、head 位置と前方方向にプロパティとしてアクセスできるようになります。  次のコードは、これらのアクセス方法を示しています。

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>視線を使用する

目を見つめた API は、頭を見つめているのとよく似ています。  これは、同じ[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API を使用します。これは、シーンに対して raycast できる射線 origin と direction を提供します。  唯一の違いは、使用前に視線追跡を明示的に有効にする必要があることです。 そのためには、次の2つの手順を実行する必要があります。
1. アプリでアイ tracking を使用するためのアクセス許可をユーザーに要求します。
2. パッケージマニフェストで "宝石入力" 機能を有効にします。

### <a name="requesting-access-to-eye-gaze-input"></a>視線入力へのアクセスを要求しています
アプリが起動したら、 [EyesPose:: RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)を呼び出して、視線追跡へのアクセスを要求します。 必要に応じてユーザーにプロンプトが表示され、アクセス権が付与されると[GazeInputAccessStatus:: Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus)が返されます。 これは非同期呼び出しであるため、追加の管理が必要になります。 次の例では、デタッチされた std:: thread をスピンアップして、結果を待機します。これは、 *m_isEyeTrackingEnabled*という名前のメンバー変数に格納されます。

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
デタッチされたスレッドの開始は、非同期呼び出しを処理するためのオプションの1つにすぎません。  または、/winrtで C++サポートされている新しい [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) 機能を使用することもできます。
ユーザーのアクセス許可を要求するもう1つの例を次に示します。
-   EyesPose:: IsSupported () を使用すると、アプリケーションは、視線トラッカーがある場合にのみアクセス許可ダイアログをトリガーできます。
-   GazeInputAccessStatus m_gazeInputAccessStatus;これは、アクセス許可プロンプトが何度も表示されないようにするためです。

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```


### <a name="declaring-the-gaze-input-capability"></a>*宝石入力*機能の宣言

*ソリューションエクスプローラー*で package.appxmanifest ファイルをダブルクリックします。  次に、[*機能*] セクションに移動して、[*宝石入力*] 機能を確認します。 

![見つめ入力機能](images/gaze-input-capability.png)

これにより、package.appxmanifest ファイルの*Package*セクションに次の行が追加されます。
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>視線を見つめます
にアクセスした後は、すべてのフレームに対して視線を自由に取得できます。
ヘッドを見つめた場合と同様に、目的のタイムスタンプと座標系を使用して[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を呼び出すことによって[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose)を取得します。 SpatialPointerPose には、[視線](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)プロパティを通じて[EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose)オブジェクトが含まれています。 この値は、視線追跡が有効になっている場合にのみ null です。 そこから、 [EyesPose:: IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)を呼び出すことによって、デバイスのユーザーが監視の調整を行っているかどうかを確認できます。  次に、[見つめ](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)プロパティを使用して、 [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing を視線の位置と方向に移動します。 "宝石" プロパティは null になることがあるため、必ず確認してください。 これは、調整されたユーザーが一時的にその目を閉じる場合に発生する可能性があります。

次のコードは、視線光線にアクセスする方法を示しています。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a>と他の入力との相関関係

場合によっては、過去のイベントに対応する[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)が必要になることがあります。 たとえば、ユーザーがエアタップを実行した場合、アプリはどのような情報を探しているかを知る必要があります。 このため、 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を予測されたフレーム時間と共に使用することは、システムの入力処理と表示時間の間の待機時間が原因で不正確になることがあります。 さらに、ターゲットのために視線を使用している場合、この目はコミットアクションを終了する前にも移動する傾向があります。 これは、単純なエアタップの場合の問題にはなりませんが、長い音声コマンドと高速な動きを組み合わせると、より重要になります。 このシナリオを処理する方法の1つとして、入力イベントに対応する履歴タイムスタンプを使用して、 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を追加で呼び出すことができます。  

ただし、SpatialInteractionManager を経由した入力については、簡単な方法があります。 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)には、独自の[Trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)関数があります。 を呼び出すと、完全に相関した[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)が推測されずに提供されます。 SpatialInteractionSourceStates の使用方法の詳細については、DirectX のドキュメント[のハンズオンコントローラーとモーションコントローラー](hands-and-motion-controllers-in-directx.md)を参照してください。

## <a name="see-also"></a>関連項目
* [ヘッドを見つめ、コミットする入力モデル](gaze-and-commit.md)
* [HoloLens 2 での視線](eye-tracking.md)
* [調整](calibration.md)
* [DirectX の座標系](coordinate-systems-in-directx.md)
* [DirectX での音声入力](voice-input-in-directx.md)
* [DirectX での手とモーション コントローラー](hands-and-motion-controllers-in-directx.md)
