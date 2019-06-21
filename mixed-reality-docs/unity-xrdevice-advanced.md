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
# <a name="mixed-reality-native-objects-in-unity"></a>Unity で混合の実際のネイティブ オブジェクト

[取得、HolographicSpace](getting-a-holographicspace.md)はアプリがカメラのデータを受信して、レンダリングを開始する前にすべての複合現実のフレームします。 Unity では、エンジンのこれらの手順 Holographic オブジェクトを処理して、レンダリング ループの一部として内部的に更新できます。

ただし、高度なシナリオで必要があります、基になるネイティブ オブジェクトにアクセスするなど、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>と現在<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>します。 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a>はどのようなネイティブ オブジェクトへのアクセスを提供します。

## <a name="xrdevice"></a>XRDevice 

**名前空間:** *UnityEngine.XR*<br>
**種類:** *XRDevice*

*XRDevice*を使用して、基になるネイティブ オブジェクトへのアクセスを取得することができます、 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a>メソッド。 異なるプラットフォーム間で異なります GetNativePtr が返されます。 ユニバーサル Windows プラットフォームで、Windows Mixed Reality XR SDK を対象とする場合は、XRDevice.GetNativePtr は、次の構造へのポインター (IntPtr) を返します。 

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
Marshal.PtrToStructure メソッドを使用して HolographicFrameNativeData に変換することができます。
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** IntPtr MaxNumberOfCameras を等しい長さの UnmanagedType.ByValArray としてマーシャ リングの配列です* 


### <a name="using-holographicframenativedata"></a>HolographicFrameNativeData を使用します。

> [!NOTE]
> HolographicFrameNativeData 経由で受信したネイティブ オブジェクトの状態を変更することがあります予測不可能な動作とレンダリング アーティファクト、特に Unity は、同じ状態に関しても理由します。  たとえば、HolographicFrame.UpdateCurrentPrediction を呼び出す必要はありませんそうしないと同期して Windows を指定してください、姿勢が削減されます Unity は、そのフレームをレンダリングするポーズ予測になります[ホログラム安定性](hologram-stability.md)。

HolographicFrameNativeData からデータを使用するには、ネイティブ インターフェイスへのアクセスがレンダリングまたはデバッグのためのネイティブのプラグインで、必要な場合またはC#コード。 

Photon 時間の現在のフレームの予測を取得する HolographicFrameNativeData を使用する方法の例を示します。 
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
