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
# <a name="head-and-eye-gaze-in-directx"></a><span data-ttu-id="85a48-104">DirectX で Head、目の視線入力</span><span class="sxs-lookup"><span data-stu-id="85a48-104">Head and eye gaze in DirectX</span></span>

<span data-ttu-id="85a48-105">Windows Mixed Reality、視線入力を使用してに、ユーザーの必要な情報を決定します。</span><span class="sxs-lookup"><span data-stu-id="85a48-105">In Windows Mixed Reality, gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="85a48-106">これは、ドライブのように、プライマリの入力モデルを使用できます[された様子を確認し、コミット](gaze-and-commit.md)との相互作用の種類のコンテキストをしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="85a48-106">This can be used to drive primary input models such as [gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="85a48-107">API を介して使用可能なベクトルの 2 種類の視線の先がある: 注視し目視線の先に移動します。</span><span class="sxs-lookup"><span data-stu-id="85a48-107">There are two types of gaze vectors available through the API: head gaze and eye gaze.</span></span>  <span data-ttu-id="85a48-108">3 として両方に提供される次元光線の原点と方向。</span><span class="sxs-lookup"><span data-stu-id="85a48-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="85a48-109">そのシーンまたは実際には、アプリケーションに raycast できますし、ユーザーが対象とする内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="85a48-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="85a48-110">**Head 視線**でユーザーの頭が示される方向を表します。</span><span class="sxs-lookup"><span data-stu-id="85a48-110">**Head gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="85a48-111">位置と、デバイス自体の前方向と見なす、中心を表す位置を 2 つのディスプレイ間でポイントします。</span><span class="sxs-lookup"><span data-stu-id="85a48-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span>  <span data-ttu-id="85a48-112">Head 視線の先は、すべての複合現実デバイスで利用可能です。</span><span class="sxs-lookup"><span data-stu-id="85a48-112">Head gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="85a48-113">**目の視線入力**に対するユーザーの目を参照する方向を表します。</span><span class="sxs-lookup"><span data-stu-id="85a48-113">**Eye gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="85a48-114">原点は、ユーザーの目の間にあります。</span><span class="sxs-lookup"><span data-stu-id="85a48-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="85a48-115">システムの視線を含む複合現実デバイスで利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="85a48-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="85a48-116">Head と監視の両方の視線の先光線がからアクセスできる、 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API。</span><span class="sxs-lookup"><span data-stu-id="85a48-116">Both head and eye gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="85a48-117">呼び出すだけで[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 、指定したタイムスタンプで新しい SpatialPointerPose オブジェクトを受信して[座標系](coordinate-systems-in-directx.md)します。</span><span class="sxs-lookup"><span data-stu-id="85a48-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to recieve a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="85a48-118">この SpatialPointerPose には、ヘッドの視線の原点と方向が含まれています。</span><span class="sxs-lookup"><span data-stu-id="85a48-118">This SpatialPointerPose contains a head gaze origin and direction.</span></span> <span data-ttu-id="85a48-119">それも含まれています目視線の先の原点と方向視線が使用可能な場合。</span><span class="sxs-lookup"><span data-stu-id="85a48-119">It also contains an eye gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="85a48-120">ヘッド視線の先を使用します。</span><span class="sxs-lookup"><span data-stu-id="85a48-120">Using head gaze</span></span>

<span data-ttu-id="85a48-121">ヘッド視線の先にアクセスするには、呼び出すことによって開始[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)新しい SpatialPointerPose オブジェクトを受信します。</span><span class="sxs-lookup"><span data-stu-id="85a48-121">To access the head gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to recieve a new SpatialPointerPose object.</span></span> <span data-ttu-id="85a48-122">次のパラメーターを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="85a48-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="85a48-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)ヘッド視線の先の目的の座標系を表します。</span><span class="sxs-lookup"><span data-stu-id="85a48-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head gaze.</span></span> <span data-ttu-id="85a48-124">これは、 *coordinateSystem*次のコードに変数。</span><span class="sxs-lookup"><span data-stu-id="85a48-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="85a48-125">詳細については、次を参照してください。 この[座標系](coordinate-systems-in-directx.md)開発者ガイド。</span><span class="sxs-lookup"><span data-stu-id="85a48-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="85a48-126">A[タイムスタンプ](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp)要求ヘッド姿勢の正確な時間を表します。</span><span class="sxs-lookup"><span data-stu-id="85a48-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="85a48-127">通常は、現在のフレームの表示される場合の時間に対応するタイムスタンプを使用します。</span><span class="sxs-lookup"><span data-stu-id="85a48-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="85a48-128">この予測された表示のタイムスタンプから取得できます、 [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)オブジェクトは、現在からアクセスできる[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)。</span><span class="sxs-lookup"><span data-stu-id="85a48-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="85a48-129">この HolographicFramePrediction オブジェクトとして表されます、*予測*次のコードに変数。</span><span class="sxs-lookup"><span data-stu-id="85a48-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="85a48-130">有効な SpatialPointerPose したら、ヘッドの位置と順方向はプロパティとしてアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="85a48-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="85a48-131">次のコードでは、それらにアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="85a48-131">The following code  shows how to access them.</span></span>

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

## <a name="using-eye-gaze"></a><span data-ttu-id="85a48-132">目視線の先を使用します。</span><span class="sxs-lookup"><span data-stu-id="85a48-132">Using eye gaze</span></span>

<span data-ttu-id="85a48-133">目の視線の先の API は、ヘッド視線の先によく似ています。</span><span class="sxs-lookup"><span data-stu-id="85a48-133">The eye gaze API is very similar to head gaze.</span></span>  <span data-ttu-id="85a48-134">使用して同じ[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API で、原点と方向が、シーンに対して raycast ことに伸びる射線を提供します。</span><span class="sxs-lookup"><span data-stu-id="85a48-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="85a48-135">唯一の違いは、アクセスを要求して使用する前に視線を明示的に有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="85a48-135">The only difference is you need to explicitly enable eye tracking before using it by requesting access.</span></span>

### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="85a48-136">宣言、*視線入力*機能</span><span class="sxs-lookup"><span data-stu-id="85a48-136">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="85a48-137">Appxmanifest ファイルをダブルクリックします*ソリューション エクスプ ローラー*します。</span><span class="sxs-lookup"><span data-stu-id="85a48-137">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="85a48-138">移動し、*機能*セクションし、確認、*視線入力*機能します。</span><span class="sxs-lookup"><span data-stu-id="85a48-138">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![視線入力機能](images/gaze-input-capability.png)

<span data-ttu-id="85a48-140">次の行を追加、*パッケージ*appxmanifest ファイルのセクション。</span><span class="sxs-lookup"><span data-stu-id="85a48-140">This adds the following lines to the *Package* section in the  appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="requesting-access-to-gaze-input"></a><span data-ttu-id="85a48-141">視線入力へのアクセスを要求します。</span><span class="sxs-lookup"><span data-stu-id="85a48-141">Requesting access to gaze input</span></span>
<span data-ttu-id="85a48-142">アプリが起動するときに呼び出す[EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)目追跡へのアクセスを要求します。</span><span class="sxs-lookup"><span data-stu-id="85a48-142">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="85a48-143">システムが必要な場合、ユーザーに確認し、返す[GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus)アクセスが許可されているとします。</span><span class="sxs-lookup"><span data-stu-id="85a48-143">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="85a48-144">これは、少し余分な管理のための非同期呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="85a48-144">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="85a48-145">次の例のスピンアップと呼ばれるメンバー変数に格納するいると、結果を待つデタッチ std::thread *m_isEyeTrackingEnabled*します。</span><span class="sxs-lookup"><span data-stu-id="85a48-145">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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

<span data-ttu-id="85a48-146">非同期呼び出しを処理するための 1 つのオプションは、デタッチ スレッドを開始します。</span><span class="sxs-lookup"><span data-stu-id="85a48-146">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="85a48-147">またはを使って新しい[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)でサポートされる機能C++/WinRT です。</span><span class="sxs-lookup"><span data-stu-id="85a48-147">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="85a48-148">目の視線の先光線を取得します。</span><span class="sxs-lookup"><span data-stu-id="85a48-148">Getting the eye gaze ray</span></span>

<span data-ttu-id="85a48-149">ET へのアクセスを受け取った後は自由に目注視光線にすべてのフレームを取得します。</span><span class="sxs-lookup"><span data-stu-id="85a48-149">Once you have recieved access to ET, you are free to grab the eye gaze ray every frame.</span></span>  <span data-ttu-id="85a48-150">ヘッドの視線入力と同様に、取得、 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose)呼び出して[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)目的のタイムスタンプと座標系を使用します。</span><span class="sxs-lookup"><span data-stu-id="85a48-150">Just as with head gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="85a48-151">含まれています、SpatialPointerPose、 [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose)オブジェクト、[目](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)プロパティ。</span><span class="sxs-lookup"><span data-stu-id="85a48-151">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="85a48-152">これは、目の追跡が有効になっている場合にのみ null 以外です。</span><span class="sxs-lookup"><span data-stu-id="85a48-152">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="85a48-153">そこから、デバイスでユーザーが監視の調整を呼び出すことで追跡を確認できます[EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)します。</span><span class="sxs-lookup"><span data-stu-id="85a48-153">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="85a48-154">次に、使用、[視線](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)を取得するプロパティの[SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing 目視線の位置および方向。</span><span class="sxs-lookup"><span data-stu-id="85a48-154">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye gaze position and direction.</span></span> <span data-ttu-id="85a48-155">視線入力プロパティは、null にすることがあります、これを必ずこれを確認します。</span><span class="sxs-lookup"><span data-stu-id="85a48-155">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="85a48-156">このことができますでは、行われる調整したユーザーが自分以外を一時的に閉じるかどうかです。</span><span class="sxs-lookup"><span data-stu-id="85a48-156">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="85a48-157">次のコードでは、目の視線の先光線にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="85a48-157">The following code shows how to access the eye gaze ray.</span></span>

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

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="85a48-158">その他の入力と視線の先の関連付け</span><span class="sxs-lookup"><span data-stu-id="85a48-158">Correlating gaze with other inputs</span></span>

<span data-ttu-id="85a48-159">必要があることもあります、 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)過去のイベントに対応します。</span><span class="sxs-lookup"><span data-stu-id="85a48-159">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="85a48-160">たとえば、ユーザーは、エア タップを実行する場合、アプリ可能性がありますを探していたを知りたいとします。</span><span class="sxs-lookup"><span data-stu-id="85a48-160">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="85a48-161">そのために、次を使用して単に[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)フレームの予測と時間が不正確にシステムの入力の処理と表示時間の間の待機時間のためです。</span><span class="sxs-lookup"><span data-stu-id="85a48-161">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span>

<span data-ttu-id="85a48-162">このシナリオを処理する方法の 1 つは、する追加の呼び出しを行うには[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)、入力イベントに対応する履歴のタイムスタンプを使用します。</span><span class="sxs-lookup"><span data-stu-id="85a48-162">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  <span data-ttu-id="85a48-163">ただし、SpatialInteractionManager を介してルーティングを入力する場合を簡単があります。</span><span class="sxs-lookup"><span data-stu-id="85a48-163">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="85a48-164">[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)が非常に独自[TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)関数。</span><span class="sxs-lookup"><span data-stu-id="85a48-164">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="85a48-165">完全に相関を提供する通話[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)せず、当て推量を排除します。</span><span class="sxs-lookup"><span data-stu-id="85a48-165">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="85a48-166">SpatialInteractionSourceStates の操作方法の詳細についてを参照してください、[手および DirectX でモーション コント ローラー](hands-and-motion-controllers-in-directx.md)ドキュメント。</span><span class="sxs-lookup"><span data-stu-id="85a48-166">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="85a48-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="85a48-167">See also</span></span>
* [<span data-ttu-id="85a48-168">手および DirectX でモーション コント ローラー</span><span class="sxs-lookup"><span data-stu-id="85a48-168">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="85a48-169">DirectX の座標系</span><span class="sxs-lookup"><span data-stu-id="85a48-169">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="85a48-170">入力モデルを注視とコミット</span><span class="sxs-lookup"><span data-stu-id="85a48-170">Gaze and commit input model</span></span>](gaze-and-commit.md)

