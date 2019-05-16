---
title: DirectX で Head、目の視線入力
description: ヘッド視線の先、目がネイティブの DirectX アプリでの追跡を使用するための開発者ガイド。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 視線の先、ヘッドの視線入力、head の追跡、視線、directx、入力、ホログラム
ms.openlocfilehash: f9764132df0ca4ae2f02d8f9a5740530676eb4f5
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629615"
---
# <a name="head-and-eye-gaze-in-directx"></a>DirectX で Head、目の視線入力

Windows Mixed Reality、視線入力を使用してに、ユーザーの必要な情報を決定します。 これは、ドライブのように、プライマリの入力モデルを使用できます[された様子を確認し、コミット](gaze-and-commit.md)との相互作用の種類のコンテキストをしたりすることができます。 API を介して使用可能なベクトルの 2 種類の視線の先がある: 注視し目視線の先に移動します。  3 として両方に提供される次元光線の原点と方向。 そのシーンまたは実際には、アプリケーションに raycast できますし、ユーザーが対象とする内容を確認します。

**Head 視線**でユーザーの頭が示される方向を表します。 位置と、デバイス自体の前方向と見なす、中心を表す位置を 2 つのディスプレイ間でポイントします。  Head 視線の先は、すべての複合現実デバイスで利用可能です。

**目の視線入力**に対するユーザーの目を参照する方向を表します。 原点は、ユーザーの目の間にあります。  システムの視線を含む複合現実デバイスで利用可能になります。

Head と監視の両方の視線の先光線がからアクセスできる、 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API。 呼び出すだけで[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 、指定したタイムスタンプで新しい SpatialPointerPose オブジェクトを受信して[座標系](coordinate-systems-in-directx.md)します。 この SpatialPointerPose には、ヘッドの視線の原点と方向が含まれています。 それも含まれています目視線の先の原点と方向視線が使用可能な場合。

## <a name="using-head-gaze"></a>ヘッド視線の先を使用します。

ヘッド視線の先にアクセスするには、呼び出すことによって開始[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)新しい SpatialPointerPose オブジェクトを受信します。 次のパラメーターを渡す必要があります。
 - A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)ヘッド視線の先の目的の座標系を表します。 これは、 *coordinateSystem*次のコードに変数。 詳細については、次を参照してください。 この[座標系](coordinate-systems-in-directx.md)開発者ガイド。
 - A[タイムスタンプ](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp)要求ヘッド姿勢の正確な時間を表します。  通常は、現在のフレームの表示される場合の時間に対応するタイムスタンプを使用します。 この予測された表示のタイムスタンプから取得できます、 [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)オブジェクトは、現在からアクセスできる[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)。  この HolographicFramePrediction オブジェクトとして表されます、*予測*次のコードに変数。

 有効な SpatialPointerPose したら、ヘッドの位置と順方向はプロパティとしてアクセスできます。  次のコードでは、それらにアクセスする方法を示します。

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head gaze
}
```

## <a name="using-eye-gaze"></a>目視線の先を使用します。

目の視線の先の API は、ヘッド視線の先によく似ています。  使用して同じ[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API で、原点と方向が、シーンに対して raycast ことに伸びる射線を提供します。  唯一の違いは、アクセスを要求して使用する前に視線を明示的に有効にする必要があります。

### <a name="declaring-the-gaze-input-capability"></a>宣言、*視線入力*機能

Appxmanifest ファイルをダブルクリックします*ソリューション エクスプ ローラー*します。  移動し、*機能*セクションし、確認、*視線入力*機能します。 

![視線入力機能](images/gaze-input-capability.png)

次の行を追加、*パッケージ*appxmanifest ファイルのセクション。
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="requesting-access-to-gaze-input"></a>視線入力へのアクセスを要求します。
アプリが起動するときに呼び出す[EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)目追跡へのアクセスを要求します。 システムが必要な場合、ユーザーに確認し、返す[GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus)アクセスが許可されているとします。 これは、少し余分な管理のための非同期呼び出しです。 次の例のスピンアップと呼ばれるメンバー変数に格納するいると、結果を待つデタッチ std::thread *m_isEyeTrackingEnabled*します。

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

非同期呼び出しを処理するための 1 つのオプションは、デタッチ スレッドを開始します。  またはを使って新しい[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)でサポートされる機能C++/WinRT です。

### <a name="getting-the-eye-gaze-ray"></a>目の視線の先光線を取得します。

ET へのアクセスを受け取った後は自由に目注視光線にすべてのフレームを取得します。  ヘッドの視線入力と同様に、取得、 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose)呼び出して[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)目的のタイムスタンプと座標系を使用します。 含まれています、SpatialPointerPose、 [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose)オブジェクト、[目](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)プロパティ。 これは、目の追跡が有効になっている場合にのみ null 以外です。 そこから、デバイスでユーザーが監視の調整を呼び出すことで追跡を確認できます[EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)します。  次に、使用、[視線](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)を取得するプロパティの[SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing 目視線の位置および方向。 視線入力プロパティは、null にすることがあります、これを必ずこれを確認します。 このことができますでは、行われる調整したユーザーが自分以外を一時的に閉じるかどうかです。

次のコードでは、目の視線の先光線にアクセスする方法を示します。

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
            
            // Do something with the eye gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a>その他の入力と視線の先の関連付け

必要があることもあります、 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)過去のイベントに対応します。 たとえば、ユーザーは、エア タップを実行する場合、アプリ可能性がありますを探していたを知りたいとします。 そのために、次を使用して単に[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)フレームの予測と時間が不正確にシステムの入力の処理と表示時間の間の待機時間のためです。

このシナリオを処理する方法の 1 つは、する追加の呼び出しを行うには[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)、入力イベントに対応する履歴のタイムスタンプを使用します。  ただし、SpatialInteractionManager を介してルーティングを入力する場合を簡単があります。 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)が非常に独自[TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)関数。 完全に相関を提供する通話[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)せず、当て推量を排除します。 SpatialInteractionSourceStates の操作方法の詳細についてを参照してください、[手および DirectX でモーション コント ローラー](hands-and-motion-controllers-in-directx.md)ドキュメント。

## <a name="see-also"></a>関連項目
* [手および DirectX でモーション コント ローラー](hands-and-motion-controllers-in-directx.md)
* [DirectX の座標系](coordinate-systems-in-directx.md)
* [入力モデルを注視とコミット](gaze-and-commit.md)

