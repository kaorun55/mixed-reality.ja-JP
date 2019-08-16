---
title: DirectX でのヘッドと視線
description: ネイティブ DirectX アプリでのヘッド見つめと目の追跡を使用するための開発者ガイド。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 見つめ、頭を見つめ、ヘッドトラッキング、視線追跡、directx、入力、ホログラム
ms.openlocfilehash: edf20a621178d76bfc97477f9f9b2eca200f1318
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414409"
---
# <a name="head-and-eye-gaze-input-in-directx"></a><span data-ttu-id="b74f1-104">DirectX でのヘッドと視線の入力</span><span class="sxs-lookup"><span data-stu-id="b74f1-104">Head and eye gaze input in DirectX</span></span>

<span data-ttu-id="b74f1-105">Windows Mixed Reality では、ユーザーがどのようなことを確認しているかを判断するために、目と下の見つめ入力が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="b74f1-106">この機能を使用して、ヘッドの移動[やコミット](gaze-and-commit.md)などの主要な入力モデルを駆動したり、相互作用の種類のコンテキストを提供したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-106">This can be used to drive primary input models such as [head gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="b74f1-107">API では、次の2種類の宝石ベクトルを利用できます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-107">There are two types of gaze vectors available through the API: head gaze and eye gaze.</span></span>  <span data-ttu-id="b74f1-108">どちらも、原点と方向を持つ3次元射線として提供されます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="b74f1-109">その後、アプリケーションは、それらのシーンや現実の世界に raycast し、ユーザーの対象を特定できます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="b74f1-110">**ヘッド見つめ**は、ユーザーの頭がポイントされている方向を表します。</span><span class="sxs-lookup"><span data-stu-id="b74f1-110">**Head gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="b74f1-111">これは、デバイス自体の位置と方向であり、2つのディスプレイの間の中心点を表す位置であると考えてください。</span><span class="sxs-lookup"><span data-stu-id="b74f1-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span>  <span data-ttu-id="b74f1-112">ヘッド見つめは、すべての Mixed Reality デバイスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-112">Head gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="b74f1-113">**目**の傾きは、ユーザーの目が見ている方向を表します。</span><span class="sxs-lookup"><span data-stu-id="b74f1-113">**Eye gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="b74f1-114">原点はユーザーの目の間にあります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="b74f1-115">これは、視線追跡システムを含む Mixed Reality デバイスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="b74f1-116">[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API を使用して、ヘッドとアイの両方の光線にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-116">Both head and eye gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="b74f1-117">[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を呼び出して、指定されたタイムスタンプと[座標系](coordinate-systems-in-directx.md)で新しい SpatialPointerPose オブジェクトを受け取るだけです。</span><span class="sxs-lookup"><span data-stu-id="b74f1-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="b74f1-118">この SpatialPointerPose には、頭を見つめた原点と方向が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b74f1-118">This SpatialPointerPose contains a head gaze origin and direction.</span></span> <span data-ttu-id="b74f1-119">また、視線追跡が利用可能な場合は、視線の原点と方向も含まれています。</span><span class="sxs-lookup"><span data-stu-id="b74f1-119">It also contains an eye gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="b74f1-120">ヘッド見つめの使用</span><span class="sxs-lookup"><span data-stu-id="b74f1-120">Using head gaze</span></span>

<span data-ttu-id="b74f1-121">ヘッド宝石にアクセスするには、まず[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を呼び出して、新しい SpatialPointerPose オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-121">To access the head gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="b74f1-122">次のパラメーターを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="b74f1-123">頭を見つめた場合に必要な座標系を表す[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 。</span><span class="sxs-lookup"><span data-stu-id="b74f1-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head gaze.</span></span> <span data-ttu-id="b74f1-124">これは、次のコードの*coordinateSystem*変数によって表されます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="b74f1-125">詳細については、「[コーディネート系](coordinate-systems-in-directx.md)開発者ガイド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b74f1-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="b74f1-126">要求されたヘッドポーズの正確な時刻を表す[タイムスタンプ](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp)。</span><span class="sxs-lookup"><span data-stu-id="b74f1-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="b74f1-127">通常は、現在のフレームが表示される時刻に対応するタイムスタンプを使用します。</span><span class="sxs-lookup"><span data-stu-id="b74f1-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="b74f1-128">この予測された表示タイムスタンプは、現在の[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)からアクセスできる[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)オブジェクトから取得できます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="b74f1-129">この HolographicFramePrediction オブジェクトは、次のコードの*予測*変数によって表されます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="b74f1-130">有効な SpatialPointerPose を作成すると、head 位置と前方方向にプロパティとしてアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="b74f1-131">次のコードは、これらのアクセス方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b74f1-131">The following code  shows how to access them.</span></span>

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

## <a name="using-eye-gaze"></a><span data-ttu-id="b74f1-132">視線を使用する</span><span class="sxs-lookup"><span data-stu-id="b74f1-132">Using eye gaze</span></span>

<span data-ttu-id="b74f1-133">目を見つめている API は、頭の見つめとよく似ています。</span><span class="sxs-lookup"><span data-stu-id="b74f1-133">The eye gaze API is very similar to head gaze.</span></span>  <span data-ttu-id="b74f1-134">これは、同じ[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API を使用します。これは、シーンに対して raycast できる射線 origin と direction を提供します。</span><span class="sxs-lookup"><span data-stu-id="b74f1-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="b74f1-135">唯一の違いは、使用前に視線追跡を明示的に有効にする必要があることです。</span><span class="sxs-lookup"><span data-stu-id="b74f1-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="b74f1-136">そのためには、次の2つの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="b74f1-137">アプリでアイ tracking を使用するためのアクセス許可をユーザーに要求します。</span><span class="sxs-lookup"><span data-stu-id="b74f1-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="b74f1-138">パッケージマニフェストで "宝石入力" 機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b74f1-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-gaze-input"></a><span data-ttu-id="b74f1-139">見つめ入力へのアクセスを要求しています</span><span class="sxs-lookup"><span data-stu-id="b74f1-139">Requesting access to gaze input</span></span>
<span data-ttu-id="b74f1-140">アプリが起動したら、 [EyesPose:: RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)を呼び出して、視線追跡へのアクセスを要求します。</span><span class="sxs-lookup"><span data-stu-id="b74f1-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="b74f1-141">必要に応じてユーザーにプロンプトが表示され、アクセス権が付与されると[GazeInputAccessStatus:: Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus)が返されます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="b74f1-142">これは非同期呼び出しであるため、追加の管理が必要になります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="b74f1-143">次の例では、デタッチされた std:: thread をスピンアップして、結果を待機します。これは、 *m_isEyeTrackingEnabled*という名前のメンバー変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="b74f1-144">デタッチされたスレッドの開始は、非同期呼び出しを処理するためのオプションの1つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="b74f1-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="b74f1-145">または、/winrtで C++サポートされている新しい [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) 機能を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="b74f1-146">ユーザーのアクセス許可を要求するもう1つの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b74f1-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="b74f1-147">EyesPose:: IsSupported () を使用すると、アプリケーションは、視線トラッカーがある場合にのみアクセス許可ダイアログをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="b74f1-148">GazeInputAccessStatus m_gazeInputAccessStatus;これは、アクセス許可プロンプトが何度も表示されないようにするためです。</span><span class="sxs-lookup"><span data-stu-id="b74f1-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="b74f1-149">*宝石入力*機能の宣言</span><span class="sxs-lookup"><span data-stu-id="b74f1-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="b74f1-150">*ソリューションエクスプローラー*で package.appxmanifest ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b74f1-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="b74f1-151">次に、[*機能*] セクションに移動して、[*宝石入力*] 機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="b74f1-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![見つめ入力機能](images/gaze-input-capability.png)

<span data-ttu-id="b74f1-153">これにより、package.appxmanifest ファイルの*Package*セクションに次の行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="b74f1-154">視線光線の取得</span><span class="sxs-lookup"><span data-stu-id="b74f1-154">Getting the eye gaze ray</span></span>
<span data-ttu-id="b74f1-155">にアクセスできるようになったら、すべてのフレームに目を見つめていくことができます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-155">Once you have received access to ET, you are free to grab the eye gaze ray every frame.</span></span>  <span data-ttu-id="b74f1-156">ヘッドを見つめた場合と同様に、目的のタイムスタンプと座標系を使用して[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を呼び出すことによって[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose)を取得します。</span><span class="sxs-lookup"><span data-stu-id="b74f1-156">Just as with head gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="b74f1-157">SpatialPointerPose には、[視線](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)プロパティを通じて[EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose)オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b74f1-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="b74f1-158">この値は、視線追跡が有効になっている場合にのみ null です。</span><span class="sxs-lookup"><span data-stu-id="b74f1-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="b74f1-159">そこから、 [EyesPose:: IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)を呼び出すことによって、デバイスのユーザーが監視の調整を行っているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="b74f1-160">次に、"[宝石](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)" プロパティを使用して、 [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing を視線の位置と方向に移動します。</span><span class="sxs-lookup"><span data-stu-id="b74f1-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye gaze position and direction.</span></span> <span data-ttu-id="b74f1-161">"宝石" プロパティは null になることがあるため、必ず確認してください。</span><span class="sxs-lookup"><span data-stu-id="b74f1-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="b74f1-162">これは、調整されたユーザーが一時的にその目を閉じる場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="b74f1-163">次のコードは、視線光線にアクセスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b74f1-163">The following code shows how to access the eye gaze ray.</span></span>

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

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="b74f1-164">と他の入力との相関関係</span><span class="sxs-lookup"><span data-stu-id="b74f1-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="b74f1-165">場合によっては、過去のイベントに対応する[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="b74f1-166">たとえば、ユーザーがエアタップを実行した場合、アプリはどのような情報を探しているかを知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="b74f1-167">このため、 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を予測されたフレーム時間と共に使用することは、システムの入力処理と表示時間の間の待機時間が原因で不正確になることがあります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="b74f1-168">さらに、ターゲットのために視線を使用している場合は、コミットアクションを終了する前でも、目は移動する傾向があります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-168">In addition, if using eye gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="b74f1-169">これは、単純なエアタップの場合の問題にはなりませんが、長い音声コマンドと高速な動きを組み合わせると、より重要になります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="b74f1-170">このシナリオを処理する方法の1つとして、入力イベントに対応する履歴タイムスタンプを使用して、 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を追加で呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="b74f1-171">ただし、SpatialInteractionManager を経由した入力については、簡単な方法があります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="b74f1-172">[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)には、独自の[Trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)関数があります。</span><span class="sxs-lookup"><span data-stu-id="b74f1-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="b74f1-173">を呼び出すと、完全に相関した[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)が推測されずに提供されます。</span><span class="sxs-lookup"><span data-stu-id="b74f1-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="b74f1-174">SpatialInteractionSourceStates の使用方法の詳細については、DirectX のドキュメント[のハンズオンコントローラーとモーションコントローラー](hands-and-motion-controllers-in-directx.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b74f1-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="b74f1-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="b74f1-175">See also</span></span>
* [<span data-ttu-id="b74f1-176">ヘッドを見つめ、コミット入力モデル</span><span class="sxs-lookup"><span data-stu-id="b74f1-176">Head gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="b74f1-177">HoloLens 2 での視線</span><span class="sxs-lookup"><span data-stu-id="b74f1-177">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="b74f1-178">DirectX の座標系</span><span class="sxs-lookup"><span data-stu-id="b74f1-178">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="b74f1-179">DirectX での音声入力</span><span class="sxs-lookup"><span data-stu-id="b74f1-179">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="b74f1-180">DirectX での手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="b74f1-180">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
