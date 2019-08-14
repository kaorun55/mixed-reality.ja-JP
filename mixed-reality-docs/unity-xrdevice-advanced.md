---
title: Unity の Mixed Reality ネイティブオブジェクト
description: Unity の基になる Holographic ネイティブオブジェクトへのアクセスを取得します。
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: unity、mixed reality、native、xrdevice、spatialcoordinatesystem、holographicframe、holographiccamera、ispatialcoordinatesystem、iholographicframe、iholographiccamera、get ptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942098"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="53dc9-104">Unity の Mixed Reality ネイティブオブジェクト</span><span class="sxs-lookup"><span data-stu-id="53dc9-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="53dc9-105">[HolographicSpace を取得](getting-a-holographicspace.md)することは、カメラデータの受信とフレームのレンダリングを開始する前に、すべての Mixed Reality アプリで実行されます。</span><span class="sxs-lookup"><span data-stu-id="53dc9-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="53dc9-106">Unity では、エンジンはこれらの手順を自動的に処理し、レンダリングループの一部として Holographic オブジェクトと更新を内部的に処理します。</span><span class="sxs-lookup"><span data-stu-id="53dc9-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="53dc9-107">ただし、高度なシナリオでは、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>や現在の<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>など、基になるネイティブオブジェクトへのアクセスが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="53dc9-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="53dc9-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">Unityengine. XR. XRDevice</a>は、これらのネイティブオブジェクトへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="53dc9-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="53dc9-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="53dc9-109">XRDevice</span></span> 

<span data-ttu-id="53dc9-110">**名前空間:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="53dc9-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="53dc9-111">**種類:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="53dc9-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="53dc9-112">*XRDevice*型を使用すると、<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">表示 ptr</a>メソッドを使用して、基になるネイティブオブジェクトにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="53dc9-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="53dc9-113">Getによって返される値は、プラットフォームによって異なります。</span><span class="sxs-lookup"><span data-stu-id="53dc9-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="53dc9-114">ユニバーサル Windows プラットフォームで、Windows Mixed Reality XR SDK を対象とする場合、XRDevice は次の構造にポインター (IntPtr) を返します。</span><span class="sxs-lookup"><span data-stu-id="53dc9-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame 
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
<span data-ttu-id="53dc9-115">Marshal.ptrtostructure メソッドを使用して HolographicFrameNativeData に変換できます。</span><span class="sxs-lookup"><span data-stu-id="53dc9-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="53dc9-116">***IHolographicCameraPtr** は、unmanagedtype.bool としてマーシャリングされた IntPtr の配列であり、長さは MaxNumberOfCameras と同じです。*</span><span class="sxs-lookup"><span data-stu-id="53dc9-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="53dc9-117">HolographicFrameNativeData の使用</span><span class="sxs-lookup"><span data-stu-id="53dc9-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="53dc9-118">HolographicFrameNativeData を使用して受信したネイティブオブジェクトの状態を変更すると、予期しない動作やレンダリングアーティファクトが発生する可能性があります。また、Unity でも同じ状態が理由である場合は特にそうです</span><span class="sxs-lookup"><span data-stu-id="53dc9-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="53dc9-119">たとえば、HolographicFrame を呼び出さないでください。そうしないと、Unity がそのフレームでレンダリングする原因が、Windows が期待するようなものと同期しなくなります。これにより、[ホログラムの安定性](hologram-stability.md)が低下します。</span><span class="sxs-lookup"><span data-stu-id="53dc9-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="53dc9-120">ネイティブのプラグインまたはC#コードで、ネイティブインターフェイスへのアクセスが必要な場合は、HolographicFrameNativeData からのデータを使用できます。</span><span class="sxs-lookup"><span data-stu-id="53dc9-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="53dc9-121">HolographicFrameNativeData を使用して、photon 時間の現在のフレームの予測を取得する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="53dc9-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a><span data-ttu-id="53dc9-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="53dc9-122">See Also</span></span>
* <span data-ttu-id="53dc9-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="53dc9-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="53dc9-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="53dc9-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="53dc9-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="53dc9-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="53dc9-126">DirectX でのレンダリング</span><span class="sxs-lookup"><span data-stu-id="53dc9-126">Rendering in DirectX</span></span>](rendering-in-directx.md)
