---
title: DirectX でのお持ちのカメラ
description: HoloLens アプリでのビューポイント (POV) カメラの使用方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、特定のカメラ、ポイント/視点、POV、unporoject media foundation、MF、カスタムシンク、チュートリアル、サンプルコード
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516868"
---
# <a name="locatable-camera-in-directx"></a>DirectX でのお持ちのカメラ

このトピックでは、DirectX アプリで[カメラ](locatable-camera.md)にアクセスするための[メディアファンデーション](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx)パイプラインを設定する方法について説明します。これには、実際の世界で作成されたイメージを検索するためのフレームメタデータも含まれます。

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a>Windows Media Capture とメディアファンデーションの開発:IMFAttributes

各イメージフレームには、座標系、および2つの重要な変換[が含まれ](locatable-camera.md#images-with-coordinate-systems)ます。 "表示" 変換は、指定された座標系からカメラにマップされ、"投影" はカメラからイメージ内のピクセルにマップされます。 座標系と2つの変換は、メディアファンデーションの[Imfattributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)を通じて、すべてのイメージフレームにメタデータとして埋め込まれます。

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a>MF カスタムシンクを使用して属性を読み取り、プロジェクションを実行するサンプルの使用例

カスタム MF のシンクシンクストリーム ([Imfstreamsink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)) では、サンプル属性を使用して[imfsample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx)を取得できます。

WinRT ベースのコードには、次の MediaExtensions を定義する必要があります。

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

これらの属性に WinRT Api からアクセスすることはできませんが、 [Imftransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (有効な場合) または[Imfmediasink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx)と[Imfstreamsink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (カスタムシンクの場合) のメディア拡張機能の実装が必要です。 Imftransform でこの拡張機能のサンプルを処理する場合[::P roて input (](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/)[imftransform::P roて output (](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) ) または[imfstreamsink::P roて sample ()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx)の場合は、次のサンプルのように属性をクエリできます。

```
ComPtr<IUnknown> spUnknown;
ComPtr<Windows::Perception::Spatial::ISpatialCoordinateSystem> spSpatialCoordinateSystem;
ComPtr<Windows::Foundation::IReference<Windows::Foundation::Numerics::Matrix4x4>> spTransformRef;
Windows::Foundation::Numerics::Matrix4x4 worldToCameraMatrix;
Windows::Foundation::Numerics::Matrix4x4 viewMatrix;
Windows::Foundation::Numerics::Matrix4x4 projectionMatrix;
UINT32 cbBlobSize = 0;
hr = pSample->GetUnknown(MFSampleExtension_Spatial_CameraCoordinateSystem, IID_PPV_ARGS(&spUnknown));
if (SUCCEEDED(hr))
{
    hr = spUnknown.As(&spSpatialCoordinateSystem);
    if (FAILED(hr))
    {
        return hr;
    }
    hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraViewTransform,
                          (UINT8*)(&viewMatrix),
                          sizeof(viewMatrix),
                          &cbBlobSize);
    if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
    {
        hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraProjectionTransform,
                              (UINT8*)(&projectionMatrix),
                              sizeof(projectionMatrix),
                              &cbBlobSize);
        if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
        {
            // Assume m_spCurrentCoordinateSystem is representing
            // world coordinate system application is using
            hr = m_spCurrentCoordinateSystem->TryGetTransformTo(spSpatialCoordinateSystem.Get(),
                                                                &spTransformRef);
            if (FAILED(hr))
            {
                return hr;
            }
            hr = spTransformRef->get_Value(&worldToCameraMatrix);
            if (FAILED(hr))
            {
                return hr;
            }
        }
    }
}
```

カメラからテクスチャにアクセスするには、カメラフレームテクスチャを作成する同じ D3D デバイスが必要です。 この D3D デバイスは、キャプチャパイプラインの[Imfdxgidevicemanager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx)にあります。 メディアキャプチャから DXGI デバイスマネージャーを取得するには、 [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx)および[Iadvanced Mediacapの設定](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx)インターフェイスを使用できます。

```
Microsoft::WRL::ComPtr<IAdvancedMediaCapture> spAdvancedMediaCapture;
Microsoft::WRL::ComPtr<IAdvancedMediaCaptureSettings> spAdvancedMediaCaptureSettings;
Microsoft::WRL::ComPtr<IMFDXGIDeviceManager> spDXGIDeviceManager;
// Assume mediaCapture is Windows::Media::Capture::MediaCapture and initialized
if (SUCCEEDED(((IUnknown *)(mediaCapture))->QueryInterface(IID_PPV_ARGS(&spAdvancedMediaCapture))))
{
    if (SUCCEEDED(spAdvancedMediaCapture->GetAdvancedMediaCaptureSettings(&spAdvancedMediaCaptureSettings)))
    {
        spAdvancedMediaCaptureSettings->GetDirectxDeviceManager(&spDXGIDeviceManager);
    }
}
```

Windows Mixed Reality アプリのオプションの入力方法として、マウスおよびキーボード入力を有効にすることもできます。 これは、HoloLens などのデバイスの優れたデバッグ機能であり、Pc に接続されたイマーシブヘッドセットで実行される mixed reality アプリでのユーザー入力に適している場合もあります。
