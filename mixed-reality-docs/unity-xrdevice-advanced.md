---
title: Unity で混合の実際のネイティブ オブジェクト
description: Unity では、基になる Holographic ネイティブ オブジェクトへのアクセスを取得します。
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: unity では、実際には、ネイティブ、xrdevice、spatialcoordinatesystem、holographicframe、holographiccamera、ispatialcoordinatesystem、iholographicframe、iholographiccamera、getnativeptr の混在
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942098"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="5fbca-104">Unity で混合の実際のネイティブ オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5fbca-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="5fbca-105">[取得、HolographicSpace](getting-a-holographicspace.md)はアプリがカメラのデータを受信して、レンダリングを開始する前にすべての複合現実のフレームします。</span><span class="sxs-lookup"><span data-stu-id="5fbca-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="5fbca-106">Unity では、エンジンのこれらの手順 Holographic オブジェクトを処理して、レンダリング ループの一部として内部的に更新できます。</span><span class="sxs-lookup"><span data-stu-id="5fbca-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="5fbca-107">ただし、高度なシナリオで必要があります、基になるネイティブ オブジェクトにアクセスするなど、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>と現在<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>します。</span><span class="sxs-lookup"><span data-stu-id="5fbca-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="5fbca-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a>はどのようなネイティブ オブジェクトへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5fbca-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="5fbca-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="5fbca-109">XRDevice</span></span> 

<span data-ttu-id="5fbca-110">**名前空間:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="5fbca-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="5fbca-111">**種類:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="5fbca-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="5fbca-112">*XRDevice*を使用して、基になるネイティブ オブジェクトへのアクセスを取得することができます、 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a>メソッド。</span><span class="sxs-lookup"><span data-stu-id="5fbca-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="5fbca-113">異なるプラットフォーム間で異なります GetNativePtr が返されます。</span><span class="sxs-lookup"><span data-stu-id="5fbca-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="5fbca-114">ユニバーサル Windows プラットフォームで、Windows Mixed Reality XR SDK を対象とする場合は、XRDevice.GetNativePtr は、次の構造へのポインター (IntPtr) を返します。</span><span class="sxs-lookup"><span data-stu-id="5fbca-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="5fbca-115">Marshal.PtrToStructure メソッドを使用して HolographicFrameNativeData に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="5fbca-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="5fbca-116">***IHolographicCameraPtr** IntPtr MaxNumberOfCameras を等しい長さの UnmanagedType.ByValArray としてマーシャ リングの配列です*</span><span class="sxs-lookup"><span data-stu-id="5fbca-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="5fbca-117">HolographicFrameNativeData を使用します。</span><span class="sxs-lookup"><span data-stu-id="5fbca-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="5fbca-118">HolographicFrameNativeData 経由で受信したネイティブ オブジェクトの状態を変更することがあります予測不可能な動作とレンダリング アーティファクト、特に Unity は、同じ状態に関しても理由します。</span><span class="sxs-lookup"><span data-stu-id="5fbca-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="5fbca-119">たとえば、HolographicFrame.UpdateCurrentPrediction を呼び出す必要はありませんそうしないと同期して Windows を指定してください、姿勢が削減されます Unity は、そのフレームをレンダリングするポーズ予測になります[ホログラム安定性](hologram-stability.md)。</span><span class="sxs-lookup"><span data-stu-id="5fbca-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="5fbca-120">HolographicFrameNativeData からデータを使用するには、ネイティブ インターフェイスへのアクセスがレンダリングまたはデバッグのためのネイティブのプラグインで、必要な場合またはC#コード。</span><span class="sxs-lookup"><span data-stu-id="5fbca-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="5fbca-121">Photon 時間の現在のフレームの予測を取得する HolographicFrameNativeData を使用する方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="5fbca-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="5fbca-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fbca-122">See Also</span></span>
* <span data-ttu-id="5fbca-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="5fbca-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="5fbca-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="5fbca-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="5fbca-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="5fbca-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="5fbca-126">DirectX でのレンダリング</span><span class="sxs-lookup"><span data-stu-id="5fbca-126">Rendering in DirectX</span></span>](rendering-in-directx.md)
