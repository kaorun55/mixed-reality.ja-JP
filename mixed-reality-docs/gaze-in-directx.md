---
title: DirectX でのヘッドと視線
description: ネイティブ DirectX アプリでのヘッド見つめと目の追跡を使用するための開発者ガイド。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 視線、ヘッド見つめ、ヘッドトラッキング、視線追跡、directx、入力、ホログラム
ms.openlocfilehash: 664657b9ab01530a608e31091823e828cc99d0cd
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926561"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="37873-104">DirectX でのヘッドと視線の入力</span><span class="sxs-lookup"><span data-stu-id="37873-104">Head-gaze and eye-gaze input in DirectX</span></span>

<span data-ttu-id="37873-105">Windows Mixed Reality では、ユーザーがどのようなことを確認しているかを判断するために、目と下の見つめ入力が使用されます。</span><span class="sxs-lookup"><span data-stu-id="37873-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="37873-106">これを使用すると、[ヘッドを見つめたりコミット](gaze-and-commit.md)したりする主な入力モデルを利用したり、相互作用の種類のコンテキストを提供したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="37873-106">This can be used to drive primary input models such as [head-gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="37873-107">API を介して使用できる2種類の宝石ベクトルがあります。ヘッド宝石と視線</span><span class="sxs-lookup"><span data-stu-id="37873-107">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="37873-108">どちらも、原点と方向を持つ3次元射線として提供されます。</span><span class="sxs-lookup"><span data-stu-id="37873-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="37873-109">その後、アプリケーションは、それらのシーンや現実の世界に raycast し、ユーザーの対象を特定できます。</span><span class="sxs-lookup"><span data-stu-id="37873-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="37873-110">**頭を見つめ**ているのは、ユーザーの頭がポイントされている方向を示しています。</span><span class="sxs-lookup"><span data-stu-id="37873-110">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="37873-111">これは、デバイス自体の位置と方向であり、2つのディスプレイの間の中心点を表す位置であると考えてください。</span><span class="sxs-lookup"><span data-stu-id="37873-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span> <span data-ttu-id="37873-112">ヘッド宝石は、すべての Mixed Reality デバイスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="37873-112">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="37873-113">**視線**は、ユーザーの目が見ている方向を表します。</span><span class="sxs-lookup"><span data-stu-id="37873-113">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="37873-114">原点はユーザーの目の間にあります。</span><span class="sxs-lookup"><span data-stu-id="37873-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="37873-115">これは、視線追跡システムを含む Mixed Reality デバイスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="37873-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="37873-116">ヘッドと視線の両方には、 [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="37873-116">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="37873-117">[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を呼び出して、指定されたタイムスタンプと[座標系](coordinate-systems-in-directx.md)で新しい SpatialPointerPose オブジェクトを受け取るだけです。</span><span class="sxs-lookup"><span data-stu-id="37873-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="37873-118">この SpatialPointerPose には、中心と方向があります。</span><span class="sxs-lookup"><span data-stu-id="37873-118">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="37873-119">また、視線追跡が利用可能な場合は、視線の原点と方向も含まれています。</span><span class="sxs-lookup"><span data-stu-id="37873-119">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

### <a name="device-support"></a><span data-ttu-id="37873-120">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="37873-120">Device support</span></span>
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="37873-121"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="37873-121"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="37873-122"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="37873-122"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="37873-123"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="37873-123"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="37873-124"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="37873-124"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="37873-125">頭の視線入力</span><span class="sxs-lookup"><span data-stu-id="37873-125">Head-gaze</span></span></td>
     <td><span data-ttu-id="37873-126">✔️</span><span class="sxs-lookup"><span data-stu-id="37873-126">✔️</span></span></td>
     <td><span data-ttu-id="37873-127">✔️</span><span class="sxs-lookup"><span data-stu-id="37873-127">✔️</span></span></td>
     <td><span data-ttu-id="37873-128">✔️</span><span class="sxs-lookup"><span data-stu-id="37873-128">✔️</span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="37873-129">視線</span><span class="sxs-lookup"><span data-stu-id="37873-129">Eye-gaze</span></span></td>
     <td>❌</td>
     <td><span data-ttu-id="37873-130">✔️</span><span class="sxs-lookup"><span data-stu-id="37873-130">✔️</span></span></td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a><span data-ttu-id="37873-131">ヘッドの使用</span><span class="sxs-lookup"><span data-stu-id="37873-131">Using head-gaze</span></span>

<span data-ttu-id="37873-132">ヘッド宝石にアクセスするには、まず[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を呼び出して、新しい SpatialPointerPose オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="37873-132">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="37873-133">次のパラメーターを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="37873-133">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="37873-134">ヘッド見つめの目的の座標系を表す[SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) 。</span><span class="sxs-lookup"><span data-stu-id="37873-134">A [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head-gaze.</span></span> <span data-ttu-id="37873-135">これは、次のコードの*coordinateSystem*変数によって表されます。</span><span class="sxs-lookup"><span data-stu-id="37873-135">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="37873-136">詳細については、「[コーディネート系](coordinate-systems-in-directx.md)開発者ガイド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37873-136">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="37873-137">要求されたヘッドポーズの正確な時刻を表す[タイムスタンプ](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp)。</span><span class="sxs-lookup"><span data-stu-id="37873-137">A [Timestamp](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="37873-138">通常は、現在のフレームが表示される時刻に対応するタイムスタンプを使用します。</span><span class="sxs-lookup"><span data-stu-id="37873-138">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="37873-139">この予測された表示タイムスタンプは、現在の[HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)からアクセスできる[HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)オブジェクトから取得できます。</span><span class="sxs-lookup"><span data-stu-id="37873-139">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="37873-140">この HolographicFramePrediction オブジェクトは、次のコードの*予測*変数によって表されます。</span><span class="sxs-lookup"><span data-stu-id="37873-140">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="37873-141">有効な SpatialPointerPose を作成すると、head 位置と前方方向にプロパティとしてアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="37873-141">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="37873-142">次のコードは、これらのアクセス方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="37873-142">The following code  shows how to access them.</span></span>

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

## <a name="using-eye-gaze"></a><span data-ttu-id="37873-143">視線を使用する</span><span class="sxs-lookup"><span data-stu-id="37873-143">Using eye-gaze</span></span>

<span data-ttu-id="37873-144">ユーザーが視線入力を使用できるようにするには、各ユーザーが初めてデバイスを使用するときに、[視線追跡ユーザーの調整](calibration.md)を行う必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="37873-144">Please note that for your users to use eye-gaze input, each user has to go through an [eye tracking user calibration](calibration.md) the first time they use the device.</span></span> <span data-ttu-id="37873-145">目を見つめた API は、頭を見つめているのとよく似ています。</span><span class="sxs-lookup"><span data-stu-id="37873-145">The eye-gaze API is very similar to head-gaze.</span></span>
<span data-ttu-id="37873-146">これは、同じ[SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API を使用します。これは、シーンに対して raycast できる射線 origin と direction を提供します。</span><span class="sxs-lookup"><span data-stu-id="37873-146">It uses the same [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="37873-147">唯一の違いは、使用前に視線追跡を明示的に有効にする必要があることです。</span><span class="sxs-lookup"><span data-stu-id="37873-147">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="37873-148">そのためには、次の2つの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37873-148">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="37873-149">アプリでアイ tracking を使用するためのアクセス許可をユーザーに要求します。</span><span class="sxs-lookup"><span data-stu-id="37873-149">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="37873-150">パッケージマニフェストで "宝石入力" 機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="37873-150">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="37873-151">視線入力へのアクセスを要求しています</span><span class="sxs-lookup"><span data-stu-id="37873-151">Requesting access to eye-gaze input</span></span>
<span data-ttu-id="37873-152">アプリが起動したら、 [EyesPose:: RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)を呼び出して、視線追跡へのアクセスを要求します。</span><span class="sxs-lookup"><span data-stu-id="37873-152">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="37873-153">必要に応じてユーザーにプロンプトが表示され、アクセス権が付与されると[GazeInputAccessStatus:: Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus)が返されます。</span><span class="sxs-lookup"><span data-stu-id="37873-153">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="37873-154">これは非同期呼び出しであるため、追加の管理が必要になります。</span><span class="sxs-lookup"><span data-stu-id="37873-154">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="37873-155">次の例では、デタッチされた std:: thread をスピンアップして、結果を待機します。これは、 *m_isEyeTrackingEnabled*という名前のメンバー変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="37873-155">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="37873-156">デタッチされたスレッドの開始は、非同期呼び出しを処理するためのオプションの1つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="37873-156">Starting a detached thread is just one option for handling async calls.</span></span> <span data-ttu-id="37873-157">または、/winrtで C++サポートされている新しい [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) 機能を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="37873-157">Alternatively, you could use the new [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="37873-158">ユーザーのアクセス許可を要求するもう1つの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="37873-158">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="37873-159">EyesPose:: IsSupported () を使用すると、アプリケーションは、視線トラッカーがある場合にのみアクセス許可ダイアログをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="37873-159">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="37873-160">GazeInputAccessStatus m_gazeInputAccessStatus;これは、アクセス許可プロンプトが何度も表示されないようにするためです。</span><span class="sxs-lookup"><span data-stu-id="37873-160">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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

### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="37873-161">*宝石入力*機能の宣言</span><span class="sxs-lookup"><span data-stu-id="37873-161">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="37873-162">*ソリューションエクスプローラー*で package.appxmanifest ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="37873-162">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="37873-163">次に、[*機能*] セクションに移動して、[*宝石入力*] 機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="37873-163">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![見つめ入力機能](images/gaze-input-capability.png)

<span data-ttu-id="37873-165">これにより、package.appxmanifest ファイルの*Package*セクションに次の行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="37873-165">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="37873-166">視線を見つめます</span><span class="sxs-lookup"><span data-stu-id="37873-166">Getting the eye-gaze ray</span></span>
<span data-ttu-id="37873-167">にアクセスした後は、すべてのフレームに対して視線を自由に取得できます。</span><span class="sxs-lookup"><span data-stu-id="37873-167">Once you have received access to ET, you are free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="37873-168">ヘッドを見つめた場合と同様に、目的のタイムスタンプと座標系を使用して[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を呼び出すことによって[SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose)を取得します。</span><span class="sxs-lookup"><span data-stu-id="37873-168">Just as with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="37873-169">SpatialPointerPose には、[視線](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)プロパティを通じて[EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose)オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="37873-169">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="37873-170">この値は、視線追跡が有効になっている場合にのみ null です。</span><span class="sxs-lookup"><span data-stu-id="37873-170">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="37873-171">そこから、 [EyesPose:: IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)を呼び出すことによって、デバイスのユーザーが監視の調整を行っているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="37873-171">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="37873-172">次に、[見つめ](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)プロパティを使用して、視線位置と方向を含む[SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray)を取得します。</span><span class="sxs-lookup"><span data-stu-id="37873-172">Next, use the [Gaze](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) containing the eye-gaze position and direction.</span></span> <span data-ttu-id="37873-173">"宝石" プロパティは null になることがあるため、必ず確認してください。</span><span class="sxs-lookup"><span data-stu-id="37873-173">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="37873-174">これは、調整されたユーザーが一時的にその目を閉じる場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="37873-174">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="37873-175">次のコードは、視線光線にアクセスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="37873-175">The following code shows how to access the eye-gaze ray.</span></span>

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

## <a name="fallback-when-eye-tracking-is-not-available"></a><span data-ttu-id="37873-176">視線追跡が使用できない場合のフォールバック</span><span class="sxs-lookup"><span data-stu-id="37873-176">Fallback when eye tracking is not available</span></span>
<span data-ttu-id="37873-177">この記事で説明した[ように、](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available)開発者と開発者はどちらも、アプリで目の追跡データを使用できない可能性があるインスタンスがある可能性があることに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37873-177">As mentioned in our [eye tracking design docs](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available), both designers as well as developers should be aware that there may be instances in which eye tracking data may not be available to your app.</span></span>
<span data-ttu-id="37873-178">これには、ユーザーが調整されていないこと、ユーザーがアプリに対する目の追跡データへのアクセスを拒否した、または単に一時的な干渉 (HoloLens バイザーまたはヘア occluding のユーザーの目で見た汚れなど) へのアクセスが拒否されたなどのさまざまな理由があります。</span><span class="sxs-lookup"><span data-stu-id="37873-178">There are various reasons for this ranging from a user not being calibrated, the user having denied the app access to his/her eye tracking data or simply temporary interferences (such as smudges on the HoloLens visor or hair occluding the user's eyes).</span></span> <span data-ttu-id="37873-179">このドキュメントでは、いくつかの Api について既に説明しましたが、次の例では、クイックリファレンスとしてアイトラッキングを利用できることを検出する方法の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="37873-179">While some of the APIs have already been mentioned in this document, in the following, we provide a summary of how to detect that eye tracking is available as a quick reference:</span></span> 

* <span data-ttu-id="37873-180">システムが目の追跡をまったくサポートしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="37873-180">Check that the system supports eye tracking at all.</span></span> <span data-ttu-id="37873-181">次の*メソッド*を呼び出します。 [EyesPose ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)です。</span><span class="sxs-lookup"><span data-stu-id="37873-181">Call the following *method*: [Windows.Perception.People.EyesPose.IsSupported()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span></span>

* <span data-ttu-id="37873-182">ユーザーが調整されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="37873-182">Check that the user is calibrated.</span></span> <span data-ttu-id="37873-183">次の*プロパティ*を呼び出します。 [EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span><span class="sxs-lookup"><span data-stu-id="37873-183">Call the following *property*: [Windows.Perception.People.EyesPose.IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span></span> 

* <span data-ttu-id="37873-184">ユーザーが、視線追跡データを使用するためのアプリのアクセス許可を与えられていることを確認します。現在の _' GazeInputAccessStatus '_ を取得します。</span><span class="sxs-lookup"><span data-stu-id="37873-184">Check that the user has given your app permission to use their eye tracking data: Retrieve the current _'GazeInputAccessStatus'_.</span></span> <span data-ttu-id="37873-185">これを行う方法の例については、「[宝石入力へのアクセスの要求](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="37873-185">An example on how to do this is explained at [Requesting access to gaze input](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span></span>   

<span data-ttu-id="37873-186">さらに、次に説明するように、受信した視線追跡データの更新の間にタイムアウトを追加して、またはそれ以外の方法でヘッドから宝石にフォールバックすることで、目の追跡データが古くなっていないことを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="37873-186">In addition, you may want to check that your eye tracking data is not stale by adding a timeout between received eye tracking data updates and otherwise fallback to head-gaze as discussed below.</span></span>  
<span data-ttu-id="37873-187">詳細については、[フォールバック設計の考慮事項](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37873-187">Please visit our [fallback design considerations](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) for more information.</span></span>

<br>

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="37873-188">と他の入力との相関関係</span><span class="sxs-lookup"><span data-stu-id="37873-188">Correlating gaze with other inputs</span></span>
<span data-ttu-id="37873-189">場合によっては、過去のイベントに対応する[SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose)が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="37873-189">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="37873-190">たとえば、ユーザーがエアタップを実行した場合、アプリはどのような情報を探しているかを知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="37873-190">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="37873-191">このため、 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を予測されたフレーム時間と共に使用することは、システムの入力処理と表示時間の間の待機時間が原因で不正確になることがあります。</span><span class="sxs-lookup"><span data-stu-id="37873-191">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="37873-192">さらに、ターゲットのために視線を使用している場合、この目はコミットアクションを終了する前にも移動する傾向があります。</span><span class="sxs-lookup"><span data-stu-id="37873-192">In addition, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="37873-193">これは、単純なエアタップの場合の問題にはなりませんが、長い音声コマンドと高速な動きを組み合わせると、より重要になります。</span><span class="sxs-lookup"><span data-stu-id="37873-193">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="37873-194">このシナリオを処理する方法の1つとして、入力イベントに対応する履歴タイムスタンプを使用して、 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)を追加で呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="37873-194">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="37873-195">ただし、SpatialInteractionManager を経由した入力については、簡単な方法があります。</span><span class="sxs-lookup"><span data-stu-id="37873-195">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="37873-196">[SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)には、独自の[Trygetattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)関数があります。</span><span class="sxs-lookup"><span data-stu-id="37873-196">The [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="37873-197">を呼び出すと、完全に相関した[SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose)が推測されずに提供されます。</span><span class="sxs-lookup"><span data-stu-id="37873-197">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="37873-198">SpatialInteractionSourceStates の使用方法の詳細については、DirectX のドキュメント[のハンズオンコントローラーとモーションコントローラー](hands-and-motion-controllers-in-directx.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37873-198">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

<br>

## <a name="calibration"></a><span data-ttu-id="37873-199">目盛り</span><span class="sxs-lookup"><span data-stu-id="37873-199">Calibration</span></span>
<span data-ttu-id="37873-200">視線追跡を正確に機能させるには、各ユーザーが[視点を追跡](calibration.md)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37873-200">For eye tracking to work accurately, each user is required to go through an [eye tracking user calibration](calibration.md).</span></span> <span data-ttu-id="37873-201">これにより、デバイスはシステムを調整して、より快適で品質の高い閲覧エクスペリエンスをユーザーに提供し、同時に正確な視点を追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="37873-201">This allows the device to adjust the system for a more comfortable and higher quality viewing experience for the user and to ensure accurate eye tracking at the same time.</span></span> <span data-ttu-id="37873-202">開発者は、ユーザーの調整を管理するために、エンドユーザーの作業を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="37873-202">Developers don’t need to do anything on their end to manage user calibration.</span></span> <span data-ttu-id="37873-203">システムによって、次のような状況で、デバイスを調整するように求めるメッセージがユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="37873-203">The system will ensure that the user gets prompted to calibrate the device under the following circumstances:</span></span>
* <span data-ttu-id="37873-204">ユーザーが初めてデバイスを使用している</span><span class="sxs-lookup"><span data-stu-id="37873-204">The user is using the device for the first time</span></span>
* <span data-ttu-id="37873-205">ユーザーが以前に調整プロセスをオプトアウトした</span><span class="sxs-lookup"><span data-stu-id="37873-205">The user previously opted out of the calibration process</span></span>
* <span data-ttu-id="37873-206">ユーザーが最後にデバイスを使用したときに、調整プロセスが成功しませんでした</span><span class="sxs-lookup"><span data-stu-id="37873-206">The calibration process did not succeed the last time the user used the device</span></span>

<span data-ttu-id="37873-207">開発者は、視線追跡データが使用できない可能性のあるユーザーに対して十分なサポートを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37873-207">Developers should make sure to provide adequate support for users for whom eye tracking data may not be available.</span></span> <span data-ttu-id="37873-208">代替ソリューションに関する考慮事項の詳細については、「 [Hololens 2 での目の追跡](eye-tracking.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37873-208">Learn more about considerations for fallback solutions at [Eye tracking on Hololens 2](eye-tracking.md).</span></span>

<br>

## <a name="see-also"></a><span data-ttu-id="37873-209">関連項目</span><span class="sxs-lookup"><span data-stu-id="37873-209">See also</span></span>
* [<span data-ttu-id="37873-210">調整</span><span class="sxs-lookup"><span data-stu-id="37873-210">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="37873-211">DirectX の座標系</span><span class="sxs-lookup"><span data-stu-id="37873-211">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="37873-212">HoloLens 2 での視線</span><span class="sxs-lookup"><span data-stu-id="37873-212">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="37873-213">入力モデルの宝石とコミット</span><span class="sxs-lookup"><span data-stu-id="37873-213">Gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="37873-214">DirectX での手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="37873-214">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="37873-215">DirectX での音声入力</span><span class="sxs-lookup"><span data-stu-id="37873-215">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
