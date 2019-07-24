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
# <a name="locatable-camera-in-directx"></a><span data-ttu-id="97e47-104">DirectX でのお持ちのカメラ</span><span class="sxs-lookup"><span data-stu-id="97e47-104">Locatable camera in DirectX</span></span>

<span data-ttu-id="97e47-105">このトピックでは、DirectX アプリで[カメラ](locatable-camera.md)にアクセスするための[メディアファンデーション](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx)パイプラインを設定する方法について説明します。これには、実際の世界で作成されたイメージを検索するためのフレームメタデータも含まれます。</span><span class="sxs-lookup"><span data-stu-id="97e47-105">This topic describes how to set up a [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) pipeline to access the [camera](locatable-camera.md) in a DirectX app, including the frame metadata that will allow you to locate the images produced in the real world.</span></span>

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a><span data-ttu-id="97e47-106">Windows Media Capture とメディアファンデーションの開発:IMFAttributes</span><span class="sxs-lookup"><span data-stu-id="97e47-106">Windows Media Capture and Media Foundation Development: IMFAttributes</span></span>

<span data-ttu-id="97e47-107">各イメージフレームには、座標系、および2つの重要な変換[が含まれ](locatable-camera.md#images-with-coordinate-systems)ます。</span><span class="sxs-lookup"><span data-stu-id="97e47-107">Each image frame [includes a coordinate system](locatable-camera.md#images-with-coordinate-systems) , as well as two important transforms.</span></span> <span data-ttu-id="97e47-108">"表示" 変換は、指定された座標系からカメラにマップされ、"投影" はカメラからイメージ内のピクセルにマップされます。</span><span class="sxs-lookup"><span data-stu-id="97e47-108">The "view" transform maps from the provided coordinate system to the camera, and the "projection" maps from the camera to pixels in the image.</span></span> <span data-ttu-id="97e47-109">座標系と2つの変換は、メディアファンデーションの[Imfattributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)を通じて、すべてのイメージフレームにメタデータとして埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="97e47-109">The coordinate system and the 2 transforms are embedded as metadata in every image frame via Media Foundation's [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).</span></span>

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a><span data-ttu-id="97e47-110">MF カスタムシンクを使用して属性を読み取り、プロジェクションを実行するサンプルの使用例</span><span class="sxs-lookup"><span data-stu-id="97e47-110">Sample usage of reading attributes with MF custom sink and doing projection</span></span>

<span data-ttu-id="97e47-111">カスタム MF のシンクシンクストリーム ([Imfstreamsink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)) では、サンプル属性を使用して[imfsample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx)を取得できます。</span><span class="sxs-lookup"><span data-stu-id="97e47-111">In your custom MF Sink stream ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), you will get [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) with sample attributes:</span></span>

<span data-ttu-id="97e47-112">WinRT ベースのコードには、次の MediaExtensions を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97e47-112">The following MediaExtensions must be defined for WinRT based code:</span></span>

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

<span data-ttu-id="97e47-113">これらの属性に WinRT Api からアクセスすることはできませんが、 [Imftransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (有効な場合) または[Imfmediasink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx)と[Imfstreamsink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (カスタムシンクの場合) のメディア拡張機能の実装が必要です。</span><span class="sxs-lookup"><span data-stu-id="97e47-113">You can't access these attributes from WinRT APIs, but requires Media Extension implementation of [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (for Effect) or [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) and [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (for Custom Sink).</span></span> <span data-ttu-id="97e47-114">Imftransform でこの拡張機能のサンプルを処理する場合[::P roて input (](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/)[imftransform::P roて output (](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) ) または[imfstreamsink::P roて sample ()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx)の場合は、次のサンプルのように属性をクエリできます。</span><span class="sxs-lookup"><span data-stu-id="97e47-114">When you process the sample in this extension either in [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) or [IMFStreamSink::ProcessSample()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), you can query attributes like this sample.</span></span>

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

<span data-ttu-id="97e47-115">カメラからテクスチャにアクセスするには、カメラフレームテクスチャを作成する同じ D3D デバイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="97e47-115">To access the texture from the camera, you need same D3D device which creates camera frame texture.</span></span> <span data-ttu-id="97e47-116">この D3D デバイスは、キャプチャパイプラインの[Imfdxgidevicemanager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx)にあります。</span><span class="sxs-lookup"><span data-stu-id="97e47-116">This D3D device is in [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) in the capture pipeline.</span></span> <span data-ttu-id="97e47-117">メディアキャプチャから DXGI デバイスマネージャーを取得するには、 [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx)および[Iadvanced Mediacapの設定](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx)インターフェイスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="97e47-117">To get the DXGI Device manager from Media Capture you can use [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) and [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) interfaces.</span></span>

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

<span data-ttu-id="97e47-118">Windows Mixed Reality アプリのオプションの入力方法として、マウスおよびキーボード入力を有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="97e47-118">You can also enable mouse and keyboard input as optional input methods for your Windows Mixed Reality app.</span></span> <span data-ttu-id="97e47-119">これは、HoloLens などのデバイスの優れたデバッグ機能であり、Pc に接続されたイマーシブヘッドセットで実行される mixed reality アプリでのユーザー入力に適している場合もあります。</span><span class="sxs-lookup"><span data-stu-id="97e47-119">This can also be a great debugging feature for devices such as HoloLens, and may be desirable for user input in mixed reality apps running in immersive headsets attached to PCs.</span></span>
