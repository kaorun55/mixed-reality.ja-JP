---
title: DirectX の場所を特定できるカメラ
description: HoloLens のアプリでのポイントからビューの (ハット スイッチ) カメラを使用する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、カメラの場所を特定できる、ポイントの表示、ハット スイッチ、unporoject、メディア ファンデーション、MF、カスタム シンク、チュートリアル、サンプル コード
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602084"
---
# <a name="locatable-camera-in-directx"></a>DirectX の場所を特定できるカメラ

このトピックでは、設定する方法を説明します、[メディア ファンデーション](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx)パイプラインへのアクセスを[カメラ](locatable-camera.md)DirectX アプリで、イメージを配置することを許可するフレームのメタデータを含む、現実の世界で生成されました。

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a>Windows Media のキャプチャおよび Media Foundation 開発:IMFAttributes

各イメージ フレーム[座標システムを含む](locatable-camera.md#images-with-coordinate-systems)、2 つの重要な変換とします。 "View"は、カメラに指定された座標システムからのマップおよびイメージのピクセルにカメラからの「射影」マップを変換します。 メディア ファンデーションを使用してイメージ フレームごとに、座標系と 2 つの変換は、メタデータとして埋め込まれている[IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)します。

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a>MF カスタム シンクを持つ属性の読み取りとプロジェクションの実行の使用例

カスタム MF シンク ストリームで ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx))、取得、 [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx)サンプル属性を持つ。

WinRT ベースのコードの次 MediaExtensions を定義する必要があります。

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

メディア拡張機能の実装が必要ですが、WinRT Api からこれらの属性にアクセスできない[IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (影響) 用または[IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx)と[IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (カスタム シンク)。 いずれかのサンプルでは、この拡張機能を処理する場合に[IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx)または[IMFStreamSink::ProcessSample()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx)、この例のように属性を照会することができます。

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

カメラからのテクスチャにアクセスするには、同じの D3D デバイスのカメラ枠のテクスチャを作成する必要があります。 この D3D デバイスが[IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx)キャプチャ パイプライン。 メディアのキャプチャを使用することから、DXGI デバイス マネージャーを取得する[IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx)と[IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx)インターフェイス。

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

マウスとキーボードの Windows Mixed Reality アプリの省略可能な入力メソッドとして入力することもできます。 これは、HoloLens などのデバイス用の優れたデバッグ機能をすることもでき、Pc に接続されている、イマーシブ ヘッドセットで実行されている複合現実アプリでのユーザー入力のことが望ましい場合があります。
