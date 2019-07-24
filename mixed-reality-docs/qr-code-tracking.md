---
title: QR コードの追跡
description: Windows Mixed Reality イマーシブ (VR) ヘッドセットの QR コード追跡をオンにして、その機能を VR アプリに実装する方法について説明します。
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: vr、lbe、位置情報ベースのエンターテインメント、vr アーケード、アーケード、イマーシブ、qr、qr コード
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829982"
---
# <a name="qr-code-tracking"></a>QR コードの追跡

QR コードの追跡は、Windows Mixed Reality driver for イマーシブ (VR) ヘッドセットに実装されています。 ヘッドセットドライバーで QR コードトラッカーを有効にすることで、ヘッドセットは QR コードをスキャンし、関心のあるアプリに報告します。 この機能は、 [Windows 10 10 月2018更新プログラム (RS5 とも呼ば](release-notes-october-2018.md)れます) の時点でのみ使用できます。

>[!NOTE]
>この記事のコードスニペットでは、現在、 C++ [ C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用されてC++いる C + c++ 17 準拠の/WinRT ではなく、/cx の使用方法を示しています。  これらの概念は、プロジェクトC++の場合と同じですが、コードを変換する必要があります。

## <a name="device-support"></a>デバイスのサポート

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>QR コードの追跡</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>ヘッドセットの QR コード追跡の有効化と無効化
注:このセクションは、 [Windows 10 10 月2018更新プログラム (RS5 とも呼ば](release-notes-october-2018.md)れます) に対してのみ有効です。 19h1 ビルド以降、これを行う必要はありません。
QR コード追跡を活用する mixed reality アプリを開発している場合でも、これらのアプリのいずれかのお客様の場合も、ヘッドセットのドライバーで QR コードの追跡を手動で有効にする必要があります。

イマーシブ (VR) ヘッドセットの**QR コード追跡を有効**にするには、次のようにします。

1. PC で Mixed Reality ポータルアプリを閉じます。
2. PC からヘッドセットを取り外します。
3. コマンドプロンプトで次のスクリプトを実行します。<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. ヘッドセットを PC に再接続します。

イマーシブ (VR) ヘッドセットの**QR コード追跡を無効**にするには、次のようにします。

1. PC で Mixed Reality ポータルアプリを閉じます。
2. PC からヘッドセットを取り外します。
3. コマンドプロンプトで次のスクリプトを実行します。<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. ヘッドセットを PC に再接続します。 これにより、検出された QR コードが "検出不可能" になります。

## <a name="printing-codes"></a>印刷コード

まず、 [qr コードの仕様](https://www.qrcode.com/en/howto/code.html)によれば、qr コードの仕様には、使用するための余白または "quiet ゾーン" が必要です。 余白は、何も印刷されないシンボルの周りの明確な領域です。 QR コードでは、記号の両側に4つのモジュールのワイドマージンが必要です。 " これは、モジュールのサイズの4倍の幅を持つ必要があります。コードの1つの黒い四角形です。 [仕様] ページには、QR コードを印刷する方法に関するアドバイスと、特定のサイズの QR コードを作成するために必要な領域が表示されます。

現在 QR コード検出の品質は、さまざまな照明と背景に影響を受けます。 これに対処するには、照明をメモして、適切なコードを出力します。 特に明るい照明を持つシーンでは、グレーの背景に黒のコードを印刷します。 低光のシーンでは、黒の白で動作します。 同様に、コードの背景が特に暗い場合は、検出率が低い場合はグレーのコードでブラックを試します。 それ以外の場合、背景が薄い場合は、通常のコードが正常に動作します。

## <a name="qrtracking-api"></a>QRTracking API

QRTracking プラグインは、QR コード追跡用の Api を公開します。 プラグインを使用するには、 *Qrcodestrackerplugin*名前空間の次の型を使用する必要があります。

```cs
 // QRTracker plugin namespace
 namespace QRCodesTrackerPlugin
 {
    // Encapsulates information about a labeled QR code element.
    public class QRCode
    {        
        // Unique id that identifies this QR code for this session.
        public Guid Id { get; private set; }
           
        // Version of this QR code.
        public Int32 Version { get; private set; }
        
        // PhysicalSizeMeters of this QR code.
        public float PhysicalSizeMeters { get; private set; }
        
        // QR code Data.
        public string Code { get; private set; }
        
        // QR code DataStream this is the error corrected data stream
        public Byte[] CodeStream { get; private set; }
        
        // QR code last detected QPC ticks.
        public Int64 LastDetectedQPCTicks { get; private set; }
    };
    
    // The type of a QR Code added event.
    public class QRCodeAddedEventArgs
    {   
        // Gets the QR Code that was added
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code removed event.
    public class QRCodeRemovedEventArgs
    {
        // Gets the QR Code that was removed.
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code updated event.
    public class QRCodeUpdatedEventArgs
    {
        // Gets the QR Code that was updated.
        public QRCode Code { get; private set; }
    };
    
    // A callback for handling the QR Code added event.
    public delegate void QRCodeAddedHandler(QRCodeAddedEventArgs args);
    
    // A callback for handling the QR Code removed event.
    public delegate void QRCodeRemovedHandler(QRCodeRemovedEventArgs args);
    
    // A callback for handling the QR Code updated event.
    public delegate void QRCodeUpdatedHandler(QRCodeUpdatedEventArgs args);
    
    // Enumerates the possible results of a start of QRTracker.
    public enum QRTrackerStartResult
    {
        // The start has succeeded.
        Success = 0,
        
        //  The currently no device is connected.
        DeviceNotConnected = 1,
        
        // The QRTracking Feature is not supported by the current HMD driver
        // systems
        FeatureNotSupported = 2,
        
        // The access is denide. Administrator needs to enable QR tracker feature.
        AccessDenied = 3,
    };
    
    // QRTracker
    public class QRTracker
    {
        // Constructs a new QRTracker.
        public QRTracker(){}
        
        // Gets the QRTracker.
        public static QRTracker Get()
        {
            return new QRTracker();
        }
        
        // Start the QRTracker. Returns QRTrackerStartResult.
        public QRTrackerStartResult Start()
        {
            throw new NotImplementedException();
        }
        
        // Stops tracking QR codes.
        public void Stop() {}

        // Not Implemented
        Windows.Foundation.Collections.IVector<QRCode> GetList() { throw new NotImplementedException(); }
        
        // Event representing the addition of a QR Code.
        public event QRCodeAddedHandler Added = delegate { };
        
        // Event representing the removal of a QR Code.
        public event QRCodeRemovedHandler Removed = delegate { };
        
        // Event representing the update of a QR Code.
        public event QRCodeUpdatedHandler Updated = delegate { };
    };
}
```

## <a name="implementing-qr-code-tracking-in-unity"></a>Unity で QR コード追跡を実装する

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>MRTK の Unity シーンのサンプル (Mixed Reality ツールキット)

QR 追跡 API の使用方法の例については、「Mixed Reality Toolkit [GitHub サイト](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)」を参照してください。

MRTK には、QR 追跡の使用状況を簡略化するために必要なスクリプトが実装されています。 QR 追跡アプリの開発に必要なすべての資産は、"QRTracker" フォルダーにあります。 2つのシーンがあります。1つ目は、検出された QR コードの詳細を表示するサンプルです。2つ目は、QR コードにアタッチされた座標系を使用してホログラムを表示する方法を示しています。
Prefab "QRScanner" を使用すると、必要なすべてのスクリプトをバックグラウンドに追加して Qrscanner を使用できます。 スクリプト QRCodeManager は、QRCode API を実装するシングルトンクラスです。 これはシーンに追加する必要があります。 スクリプト "AttachToQRCode" は、ホログラムを QR コードの座標系に接続するために使用されます。このスクリプトは、どのホログラムにでも追加できます。 "SpatialGraphCoordinateSystem" は、QRCode 座標系の使用方法を示しています。 これらのスクリプトは、プロジェクトシーンでそのまま使用することも、前に説明したように、プラグインを使用して直接作成することもできます。

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>MRTK を使用せずに Unity で QR コード追跡を実装する

MRTK に依存せずに、Unity で QR 追跡 API を使用することもできます。 API を使用するには、次の指示に従ってプロジェクトを準備する必要があります。

1. Unity プロジェクトの assets フォルダーに、次の名前で新しいフォルダーを作成します。"プラグイン"。
2. [このフォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins)のすべての必要なファイルを、先ほど作成したローカルの "プラグイン" フォルダーにコピーします。
3. [Mrtk scripts フォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts)内の QR 追跡スクリプトを使用することも、独自に作成することもできます。
注:これらのプラグインは、 [Windows 10 10 月2018更新プログラム (RS5 とも呼ば](release-notes-october-2018.md)れます) のビルドに対してのみ使用できます。 プラグインは、次の windows リリースで更新されます。 現在のプラグインは試験段階であり、今後のバージョンの windows では機能しません。 新しいプラグインは発行されます。このプラグインは、次の windows リリースから使用でき、後方互換性ではなく、RS5 では動作しません)。

## <a name="implementing-qr-code-tracking-in-directx"></a>DirectX での QR コード追跡の実装

Visual Studio で QRTrackingPlugin を使用するには、winmd に QRTrackingPlugin の参照を追加する必要があります。 [サポートされているプラットフォームに必要なファイルについ](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)ては、こちらを参照してください。

```cpp
// MyClass.h
public ref class MyClass
{
    private:
      QRCodesTrackerPlugin::QRTracker^ m_qrtracker;
      // Handlers
      void OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args);
      void OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args);
      void OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args);
    ..
};
```

```cpp
// MyClass.cpp
MyClass::MyClass()
{
    // Create the tracker and register the callbacks
    m_qrtracker = ref new QRCodesTrackerPlugin::QRTracker();
    m_qrtracker->Added += ref new QRCodesTrackerPlugin::QRCodeAddedHandler(this, &OnAddedQRCode);
    m_qrtracker->Updated += ref new QRCodesTrackerPlugin::QRCodeUpdatedHandler(this, &OnUpdatedQRCode);
    m_qrtracker->Removed += ref new QRCodesTrackerPlugin::QRCodeRemovedHandler(this, &QOnRemovedQRCode);

    // Start the tracker
    if (m_qrtracker->Start() != QRCodesTrackerPlugin::QRTrackerStartResult::Success)
    {
      // Handle the failure
      // It can fail for multiple reasons and can be handled properly 
    }
}

void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    // use args->Code add to own list  
}

void MyClass::OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args)
{
    // use args->Code update the existing one with the new one in own list 
}

void MyClass::OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args)
{
    // use args->Code remove from own list.
}
```

## <a name="getting-a-coordinate-system"></a>座標系を取得する

上の左にある高速検出の四角形の左上隅にある QR コードに合わせて、右側の座標系を定義します。 座標系は次のようになります。 Z 軸は用紙を指しています (図には示されていません) が、Unity では、z 軸は紙でも左手でもありません。

SpatialCoordinateSystem は、示されているように定義されています。 この座標系は、API *Windows::P erception:: 空間::P review:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*を使用してプラットフォームから取得できます。

![QR コードの座標系](images/Qr-coordinatesystem.png) 

QRCode ^ Code オブジェクトから、次のコードは、四角形を作成して QR 座標系に配置する方法を示しています。

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0,  0, 0 };
    vertices[1] = { width,  0, 0 };
    vertices[2] = { width,  height, 0 };
    vertices[3] = { 0,  height, 0 };

    return vertices;
}
```

次のように、物理的なサイズを使用して QR 四角形を作成できます。

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

座標系は、QR コードを描画したり、場所にホログラムをアタッチしたりするために使用できます。

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

*Qrcodestrackerplugin:: QRCodeAddedHandler*は次のようになります。

```cpp
void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->Id);
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

## <a name="troubleshooting-and-faq"></a>トラブルシューティングと FAQ

**一般的なトラブルシューティング**

* PC は2018年10月の更新プログラムを実行していますか?
* Reg キーを設定していますか? その後、デバイスを再起動しましたか?
* QR コードのバージョンはサポートされているバージョンですか。 現在の API では、最大 QR コードバージョン20がサポートされています。 一般的な使用には、バージョン5を使用することをお勧めします。 
* QR コードに十分に近づいていますか? カメラが QR コードに近いほど、API がサポートできる QR コードバージョンが大きくなります。  

**それを検出するには、QR コードにとってどのようにする必要がありますか。**

これは、QR コードのサイズと、そのバージョンによって異なります。 5 cm の辺から 25 cm の辺まで、バージョン1の QR コードの場合、最小検出距離は0.15 メートルから0.5 メートルの範囲内です。 最も遠いものは、より小さい QR コードターゲットの場合は約0.3 メートルから、それより大きい場合は1.4 メートルまでとなります。 これよりも大きな QR コードの場合、を推定することができます。サイズの検出距離は直線的に増加します。 トラッカーは、5 cm よりも小さい側の QR コードでは機能しません。

**ロゴ付きの QR コードを使用しますか?**

ロゴ付きの QR コードはテストされていないため、現在サポートされていません。

**アプリから QR コードを消去して永続化操作方法には、**

* QR コードは、ブートセッションでのみ保持されます。 再起動 (またはドライバーの再起動) が完了すると、次に新しいオブジェクトとして検出されます。
* QR コードの履歴は、ドライバーセッションのシステムレベルで保存されますが、必要に応じて、特定のタイムスタンプよりも古い QR コードを無視するようにアプリを構成することができます。 現在、API では、複数のアプリがデータに関心を持っている可能性があるため、QR コードの履歴のクリアをサポートしています。

**RS5 および将来のバージョンのプラグインは互換性ません**。RS5 バージョンのプラグインは RS5 に対してのみ機能し、今後のバージョンでは機能しません。 Expermental プラグインは実際のプラグインに置き換えられ、今後のバージョンの windows で使用できるようになります。
