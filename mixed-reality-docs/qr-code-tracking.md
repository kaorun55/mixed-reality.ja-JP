---
title: QR コードの追跡
description: HoloLens 2 で QR コードを検出する方法について説明します。
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: vr, lbe, 位置情報ベースのエンターテインメント, vr アーケード, アーケード, イマーシブ, qr, qr コード, hololens2
ms.openlocfilehash: 736ab265db2145dd784c435e525059ed3a2fcbbb
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047167"
---
# <a name="qr-code-tracking"></a>QR コードの追跡

HoloLens 2 では、ヘッドセット周辺の環境内の QR コードを検出し、各コードの実際の場所で座標系を確立します。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>機能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> QR コードの検出</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">注を参照</td>
</tr>
</table>

>[!NOTE]
>デスクトップ Pc でのイマーシブ Windows Mixed Reality ヘッドセットのサポートは、現在、次の NuGet パッケージではサポートされていません。  デスクトップサポートで更新プログラムを引き続きご利用ください。

## <a name="getting-the-qr-package"></a>QR パッケージの取得
QR コード検出用の NuGet パッケージは[こちら](https://github.com/dorreneb/mixed-reality/releases)からダウンロードできます。

このパッケージの将来のバージョンは、パブリック NuGet パッケージリポジトリから入手できます。

## <a name="detecting-qr-codes"></a>QR コードの検出

### <a name="adding-the-webcam-capability"></a>Web カメラ機能の追加
QR コードを検出するには`webcam` 、マニフェストに機能を追加する必要があります。 この機能は、ユーザーの環境で検出されたコード内のデータに機密情報が含まれている場合に必要です。

アクセス許可を要求するに`QRCodeWatcher.RequestAccessAsync()`は、次のように呼び出します。

_C#:_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++:_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

QRCodeWatcher オブジェクトを構築する前に、アクセス許可を要求する必要があります。

QR コードの検出には`webcam`機能が必要ですが、検出はデバイスの追跡カメラを使用して行われます。 これにより、デバイスの写真/ビデオ (PV) カメラとの検出と比較して、より広範な検出とバッテリ寿命が提供されます。

### <a name="detecting-qr-codes-in-unity"></a>Unity での QR コードの検出

Unity の QR コード検出 API は、MRTK に依存せずに使用できます。 これを行うには、次の操作を行う必要があります。

1. 名前が*プラグイン*の unity プロジェクトの assets フォルダーに新しいフォルダーを作成します。
2. このフォルダーのすべての必要なファイルを、先ほど作成したローカルの "プラグイン" フォルダーにコピーします。

サンプル Unity アプリには、QR コードに holographic 二乗と、関連するデータ (GUID、物理サイズ、タイムスタンプ、デコードされたデータなど) が表示されます。 このアプリは、に https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes あります。

### <a name="detecting-qr-codes-in-c"></a>検出 (QR コードを)C++

>[!NOTE]
>このC++記事のコードスニペットでは、 C++ [ C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用される C + c++ 17 準拠C++の/WinRT ではなく、/cx を使用することを現在説明しています。 これらの概念は、コードC++を変換する必要がある場合でも、1つのプロジェクトに相当します。

```
using namespace Microsoft.MixedReality.QR;

    public ref class QRListHelper sealed
    {
    public:
        QRListHelper()
        {

        }

        void setApp(SpatialStageManager* pStage)
        {
            m_pStage = pStage;
        }

        void SetUpQRCodes()
        {
            if (QRCodeWatcher::IsSupported())
            {
                auto operation = QRCodeWatcher::RequestAccessAsync();

                WeakReference weakThis(this);

                operation->Completed = ref new AsyncOperationCompletedHandler<QRCodeWatcherAccessStatus>(
                    [weakThis](IAsyncOperation< QRCodeWatcherAccessStatus>^ operaion, AsyncStatus status)
                {
                    QRListHelper^ QRListHelper = weakThis.Resolve<QRListHelper>();
                    if (status == AsyncStatus::Completed)
                    {
                        QRListHelper->InitializeQR( operaion->GetResults());
                    }
                }
                );
            }
        }

    private:
        void OnAddedQRCode(Object^, QRCodeAddedEventArgs ^args)
        {
            m_pStage->OnAddedQRCode(args);
        }
        void OnUpdatedQRCode(Object^, QRCodeUpdatedEventArgs ^args)
        {
            m_pStage->OnUpdatedQRCode(args);
        }
        void OnEnumerationComplete(Object^, Object^)
        {
            m_pStage->OnEnumerationComplete();
        }

        SpatialStageManager* m_pStage;
        QRCodeWatcher^ m_qrWatcher;



        void InitializeQR(QRCodeWatcherAccessStatus status)
        {
            if (status == QRCodeWatcherAccessStatus::Allowed)
            {
                m_qrWatcher = ref new QRCodeWatcher();

                m_qrWatcher->Added += ref new EventHandler<Object^, QRCodeAddedEventArgs^>(this, &QRListHelper::OnAddedQRCode);
                m_qrWatcher->Updated += ref new EventHandler<Object^, QRCodeUpdatedEventArgs^>(this, &QRListHelper::OnUpdatedQRCode);
                m_qrWatcher->EnumerationCompleted += ref new EventHandler<Object^, Object^>(this, &QRListHelper::OnEnumerationComplete);
                try
                {
                    m_qrWatcher->Start();
                }
                catch (...)
                {

                }
            }
            else
            {
                // Permission denied by system or user
                // Handle the failures
            }
        }
    }; 
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>QR コードの座標系を取得する

検出された各 QR コードは、次に示すように、左上の高速検出四角形の左上隅にある QR コードに一致する[空間座標システム](coordinate-systems.md)を公開します。  QR SDK を直接使用している場合、Z 軸は用紙を指しています (図には示されていません)。 Unity 座標に変換されると、Z 軸は用紙から外れ、左手で示されます。

QR コードの SpatialCoordinateSystem が表示されます。 この座標系は、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a>を呼び出し、コードの SpatialGraphNodeId を渡すことによって、プラットフォームから取得できます。

![QR コードの座標系](images/Qr-coordinatesystem.png) 

QRCode オブジェクトの場合、次C++の/cx コードは、QR コードの座標系を使用して四角形を作成して配置する方法を示しています。

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

次のように、物理的なサイズを使用して QR 四角形を作成できます。

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

座標系は、QR コードを描画したり、場所にホログラムをアタッチしたりするために使用できます。

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->SpatialGraphNodeId);
```

*Qrcodewatcher:: QRCodeAddedHandler*は、次のようになります。

```cpp
void MyClass::OnAddedQRCode(Object ^sender, QRCodeWatcher::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->SpatialGraphNodeId);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a>QR コードの検出のベストプラクティス

### <a name="quiet-zones-around-qr-codes"></a>QR コードに関する非表示のゾーン

QR コードを正しく読み取るには、コードのすべての辺の周りに余白が必要です。 この余白には、印刷されたコンテンツを含めることはできません。また、4つのモジュール (コード内の1つの黒い四角形) にする必要があります。 

[QR 仕様](https://www.qrcode.com/en/howto/code.html)には、非表示ゾーンに関する詳細情報が含まれています。

### <a name="lighting-and-backdrop"></a>照明と背景
QR コード検出の品質は、さまざまな照明と背景に影響します。 

特に明るい照明を持つシーンでは、グレーの背景に黒のコードを印刷します。 それ以外の場合は、黒の QR コードを白い背景に印刷します。

コードの背景が特に暗い場合は、検出率が低い場合はグレーのコードで黒を試してみてください。 背景が比較的薄い場合は、通常のコードが正常に動作します。

### <a name="size-of-qr-codes"></a>QR コードのサイズ
Windows Mixed Reality デバイスは、それぞれ 5 cm 未満の QR コードでは機能しません。

5から 10 cm の長さの辺までの QR コードの場合、コードを検出するには非常に近い必要があります。 また、このサイズでコードを検出するのにも時間がかかります。 

コードを正確に検出するための正確な時間は、QR コードのサイズだけでなく、コードから離れた場所までの距離に依存します。 コードに近づけると、サイズの問題を相殺するのに役立ちます。

### <a name="distance-and-angular-position-from-the-qr-code"></a>QR コードからの距離と角度の位置
追跡カメラは、特定のレベルの詳細のみを検出できます。 実際に小さいコードの場合は、< 10cm を横に配置する必要があります。 バージョン1の QR コードが 10 ~ 25 cm 幅を超える場合、最小検出距離は0.15 メートルから0.5 メートルの範囲内です。 

サイズの検出距離は直線的に増加します。 

QR 検出は、角度の範囲 (+ = 45deg) で動作します。 これは、コードを検出するための適切な解決策があることを確認するためのものです。

### <a name="qr-codes-with-logos"></a>ロゴ付き QR コード
ロゴ付きの QR コードはテストされていないため、現在サポートされていません。

### <a name="managing-qr-code-data"></a>QR コードデータの管理
Windows Mixed Reality デバイスは、ドライバーのシステムレベルで QR コードを検出します。 デバイスが再起動されると、検出された QR コードは失われ、次に新しいオブジェクトとして再検出されます。

特定のタイムスタンプよりも古い QR コードを無視するようにアプリを構成することをお勧めします。 現時点では、API は QR コード履歴のクリアをサポートしていません。

### <a name="qr-code-placement-in-a-space"></a>スペースでの QR コードの配置
QR コードを配置する場所と方法に関する推奨事項については、「 [HoloLens の環境に関する考慮事項](environment-considerations-for-hololens.md)」を参照してください。

## <a name="qr-api-reference"></a>QR API リファレンス

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and 41-44 are Micro QR code formats 1-4.
        /// </summary>
        public VersionInfo Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum VersionInfo
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a>関連項目
* [座標系](coordinate-systems.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>