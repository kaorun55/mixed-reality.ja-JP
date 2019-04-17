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
# <a name="locatable-camera-in-directx"></a><span data-ttu-id="78726-104">DirectX の場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="78726-104">Locatable camera in DirectX</span></span>

<span data-ttu-id="78726-105">このトピックでは、設定する方法を説明します、[メディア ファンデーション](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx)パイプラインへのアクセスを[カメラ](locatable-camera.md)DirectX アプリで、イメージを配置することを許可するフレームのメタデータを含む、現実の世界で生成されました。</span><span class="sxs-lookup"><span data-stu-id="78726-105">This topic describes how to set up a [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) pipeline to access the [camera](locatable-camera.md) in a DirectX app, including the frame metadata that will allow you to locate the images produced in the real world.</span></span>

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a><span data-ttu-id="78726-106">Windows Media のキャプチャおよび Media Foundation 開発:IMFAttributes</span><span class="sxs-lookup"><span data-stu-id="78726-106">Windows Media Capture and Media Foundation Development: IMFAttributes</span></span>

<span data-ttu-id="78726-107">各イメージ フレーム[座標システムを含む](locatable-camera.md#images-with-coordinate-systems)、2 つの重要な変換とします。</span><span class="sxs-lookup"><span data-stu-id="78726-107">Each image frame [includes a coordinate system](locatable-camera.md#images-with-coordinate-systems) , as well as two important transforms.</span></span> <span data-ttu-id="78726-108">"View"は、カメラに指定された座標システムからのマップおよびイメージのピクセルにカメラからの「射影」マップを変換します。</span><span class="sxs-lookup"><span data-stu-id="78726-108">The "view" transform maps from the provided coordinate system to the camera, and the "projection" maps from the camera to pixels in the image.</span></span> <span data-ttu-id="78726-109">メディア ファンデーションを使用してイメージ フレームごとに、座標系と 2 つの変換は、メタデータとして埋め込まれている[IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)します。</span><span class="sxs-lookup"><span data-stu-id="78726-109">The coordinate system and the 2 transforms are embedded as metadata in every image frame via Media Foundation's [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).</span></span>

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a><span data-ttu-id="78726-110">MF カスタム シンクを持つ属性の読み取りとプロジェクションの実行の使用例</span><span class="sxs-lookup"><span data-stu-id="78726-110">Sample usage of reading attributes with MF custom sink and doing projection</span></span>

<span data-ttu-id="78726-111">カスタム MF シンク ストリームで ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx))、取得、 [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx)サンプル属性を持つ。</span><span class="sxs-lookup"><span data-stu-id="78726-111">In your custom MF Sink stream ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), you will get [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) with sample attributes:</span></span>

<span data-ttu-id="78726-112">WinRT ベースのコードの次 MediaExtensions を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78726-112">The following MediaExtensions must be defined for WinRT based code:</span></span>

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

<span data-ttu-id="78726-113">メディア拡張機能の実装が必要ですが、WinRT Api からこれらの属性にアクセスできない[IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (影響) 用または[IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx)と[IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (カスタム シンク)。</span><span class="sxs-lookup"><span data-stu-id="78726-113">You can't access these attributes from WinRT APIs, but requires Media Extension implementation of [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (for Effect) or [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) and [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (for Custom Sink).</span></span> <span data-ttu-id="78726-114">いずれかのサンプルでは、この拡張機能を処理する場合に[IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx)または[IMFStreamSink::ProcessSample()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx)、この例のように属性を照会することができます。</span><span class="sxs-lookup"><span data-stu-id="78726-114">When you process the sample in this extension either in [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) or [IMFStreamSink::ProcessSample()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), you can query attributes like this sample.</span></span>

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

<span data-ttu-id="78726-115">カメラからのテクスチャにアクセスするには、同じの D3D デバイスのカメラ枠のテクスチャを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78726-115">To access the texture from the camera, you need same D3D device which creates camera frame texture.</span></span> <span data-ttu-id="78726-116">この D3D デバイスが[IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx)キャプチャ パイプライン。</span><span class="sxs-lookup"><span data-stu-id="78726-116">This D3D device is in [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) in the capture pipeline.</span></span> <span data-ttu-id="78726-117">メディアのキャプチャを使用することから、DXGI デバイス マネージャーを取得する[IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx)と[IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx)インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="78726-117">To get the DXGI Device manager from Media Capture you can use [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) and [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) interfaces.</span></span>

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

<span data-ttu-id="78726-118">マウスとキーボードの Windows Mixed Reality アプリの省略可能な入力メソッドとして入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="78726-118">You can also enable mouse and keyboard input as optional input methods for your Windows Mixed Reality app.</span></span> <span data-ttu-id="78726-119">これは、HoloLens などのデバイス用の優れたデバッグ機能をすることもでき、Pc に接続されている、イマーシブ ヘッドセットで実行されている複合現実アプリでのユーザー入力のことが望ましい場合があります。</span><span class="sxs-lookup"><span data-stu-id="78726-119">This can also be a great debugging feature for devices such as HoloLens, and may be desirable for user input in mixed reality apps running in immersive headsets attached to PCs.</span></span>
