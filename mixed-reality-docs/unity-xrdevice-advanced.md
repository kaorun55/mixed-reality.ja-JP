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
# <a name="mixed-reality-native-objects-in-unity"></a>Unity の Mixed Reality ネイティブオブジェクト

[HolographicSpace を取得](getting-a-holographicspace.md)することは、カメラデータの受信とフレームのレンダリングを開始する前に、すべての Mixed Reality アプリで実行されます。 Unity では、エンジンはこれらの手順を自動的に処理し、レンダリングループの一部として Holographic オブジェクトと更新を内部的に処理します。

ただし、高度なシナリオでは、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>や現在の<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>など、基になるネイティブオブジェクトへのアクセスが必要になる場合があります。 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">Unityengine. XR. XRDevice</a>は、これらのネイティブオブジェクトへのアクセスを提供します。

## <a name="xrdevice"></a>XRDevice 

**名前空間:** *UnityEngine.XR*<br>
**種類:** *XRDevice*

*XRDevice*型を使用すると、<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">表示 ptr</a>メソッドを使用して、基になるネイティブオブジェクトにアクセスできます。 Getによって返される値は、プラットフォームによって異なります。 ユニバーサル Windows プラットフォームで、Windows Mixed Reality XR SDK を対象とする場合、XRDevice は次の構造にポインター (IntPtr) を返します。 

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
Marshal.ptrtostructure メソッドを使用して HolographicFrameNativeData に変換できます。
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr**は、unmanagedtype.bool としてマーシャリングされた IntPtr の配列であり、長さは MaxNumberOfCameras と同じです。* 


### <a name="using-holographicframenativedata"></a>HolographicFrameNativeData の使用

> [!NOTE]
> HolographicFrameNativeData を使用して受信したネイティブオブジェクトの状態を変更すると、予期しない動作やレンダリングアーティファクトが発生する可能性があります。また、Unity でも同じ状態が理由である場合は特にそうです  たとえば、HolographicFrame を呼び出さないでください。そうしないと、Unity がそのフレームでレンダリングする原因が、Windows が期待するようなものと同期しなくなります。これにより、[ホログラムの安定性](hologram-stability.md)が低下します。

ネイティブのプラグインまたはC#コードで、ネイティブインターフェイスへのアクセスが必要な場合は、HolographicFrameNativeData からのデータを使用できます。 

HolographicFrameNativeData を使用して、photon 時間の現在のフレームの予測を取得する方法の例を次に示します。 
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

## <a name="see-also"></a>関連項目
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [DirectX でのレンダリング](rendering-in-directx.md)
