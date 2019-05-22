---
title: QR コードの追跡
description: QR コードを Windows Mixed Reality 没入型 (VR) ヘッドセットの追跡を有効にする方法について説明し、VR アプリで機能を実装します。
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: vr、lbe、場所ベースのエンターテイメント、vr アーケード ゲームのイマーシブなアーケード ゲーム qr、qr コード
ms.openlocfilehash: e6588552c0cfa8bffa19ac2be5c247c5f73dc19c
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974898"
---
# <a name="qr-code-tracking"></a>QR コードの追跡

QR コードの追跡は、没入型の (VR) ヘッドセットの Windows Mixed Reality ドライバーに実装されます。 ヘッドセット ドライバーで QR コードの追跡ツールを有効にすると、ヘッドセットは QR コードのスキャンし、目的のアプリに報告されます。 この機能としての使用のみ、 [Windows 10 年 2018年 10 月 Update (RS5 とも呼ばれます)](release-notes-october-2018.md)します。

>[!NOTE]
>この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。  概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>機能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> QR コードの追跡</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>有効/無効の QR コードの追跡、ヘッドセットを
注:このセクションではのみ有効です[Windows 10 年 2018年 10 月 Update (RS5 とも呼ばれます)](release-notes-october-2018.md)します。 19 h 1 ビルド以降からこれを行うことはありません。
追跡するには、QR コードを利用する mixed reality アプリを開発している場合も、これらのアプリのいずれかのお客様は、QR コードの履歴をヘッドセットのドライバーを手動で有効にする必要があります。

**QR コードの履歴を有効にする**没入型の (VR) ヘッドセットの。

1. お使いの PC で複合現実のポータル アプリを閉じます。
2. お使いの PC からヘッドセットを取り外します。
3. コマンド プロンプトで次のスクリプトを実行します。<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. Pc、ヘッドセットを再接続します。

**QR コードの追跡をオフに**没入型の (VR) ヘッドセットの。

1. お使いの PC で複合現実のポータル アプリを閉じます。
2. お使いの PC からヘッドセットを取り外します。
3. コマンド プロンプトで次のスクリプトを実行します。<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. Pc、ヘッドセットを再接続します。 これにより、検出された、QR コード「以外の場所を特定できる」

## <a name="printing-codes"></a>印刷コード

何よりもまず、 [QR コードの spec](https://www.qrcode.com/en/howto/code.html)という"QR コード シンボルの領域が必要です、余白または「quiet ゾーン」を使用するのには、します。 余白は、何も出力されませんシンボルに関する明確領域です。 QR コードが必要です、シンボルのすべての辺に 4 モジュール優勢。" これは、モジュールのコードに黒い四角を 1 つのサイズの 4 倍の各側で、幅がある必要があります。 仕様のページには、QR コードを印刷し、特定サイズの QR コードのために必要な領域を把握する方法に関するアドバイスが含まれています。

現在 QR コードの品質の検出は、さまざまな照明と背景を受けやすくなります。 この、照明に注意してくださいし、適切なコードを印刷します。 特に明るい光のシーンでは、グレーの背景の上に黒のコードを印刷します。 で、光量不足シーン、白のしくみは黒です。 同様に、コードに背景が特にダークの場合は、お試しください灰色のコードには黒を検出、レートが低い場合。 それ以外の場合、背景が明るいの場合は、正規のコードは問題なく機能する必要があります。

## <a name="qrtracking-api"></a>QRTracking API

QRTracking プラグインでは、QR コードを追跡するための Api を公開します。 プラグインを使用する次の種類を使用する必要があります、 *QRCodesTrackerPlugin*名前空間。

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

## <a name="implementing-qr-code-tracking-in-unity"></a>Unity での追跡、QR コードを実装します。

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>Unity シーン MRTK (Mixed Reality Toolkit) のサンプルします。

Mixed Reality toolkit QR 追跡 API を使用する方法の例が見つかります[GitHub サイト](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)します。

MRTK では、使用状況の追跡 QR simpilify に必要なスクリプトを実装しました。 QR 追跡アプリを開発するために必要なすべての資産は、"QRTracker"フォルダーには。 2 つのシーンがある: 1 つ目が検出され、2 つ目は QR コードにアタッチされている座標系を使用して、ホログラムを表示する方法を示します、単に QR コードの詳細を表示するサンプルに示します。
Prefab"QRScanner"QRCodes を使用する処理に必要なすべてのスクリプトを追加します。 QRCodeManager スクリプトは、QRCode API を実装するシングルトン クラスです。 これは、シーンに追加する必要があります。 スクリプト"AttachToQRCode"を使用して、QR コードの座標系にホログラムをアタッチする、このスクリプトは、ホログラムのいずれかに追加できます。 "SpatialGraphCoordinateSystem"は、QRCode 座標系を使用する方法を示します。 としてこれらのスクリプトを使用できるのプロジェクトでシーンまたは書き込める独自直接プラグインを使用して、前述のようです。

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>QR コードが Unity MRTK なしで追跡を実装します。

MRTK に依存することがなく、Unity で QR 追跡 API を使用することもできます。 API を使用するためには、次の命令を使用してプロジェクトを準備する必要があります。

1. 名前の unity プロジェクトの assets フォルダーに新しいフォルダーを作成します。「プラグイン」されます。
2. すべての必要なファイル コピー[このフォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins)作成したローカルの「プラグイン」フォルダーにします。
3. スクリプトを追跡する QR を使用することができます、 [MRTK scripts フォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts)または独自に作成します。
注:これらのプラグインは、専用です[Windows 10 年 2018年 10 月 Update (RS5 とも呼ばれます)](release-notes-october-2018.md)をビルドします。 プラグインは、次の windows リリースで更新されます。 実験的な現在のプラグイン、windows の将来のバージョンに対しては機能しません。 次の windows リリースから使用できる新しいプラグインが発行されますれされません下位互換および RS5 では動作しません)。

## <a name="implementing-qr-code-tracking-in-directx"></a>QR コードを DirectX での追跡を実装します。

使用するには、QRTrackingPlugin Visual Studio では、.winmd に、QRTrackingPlugin の参照を追加する必要があります。 検索することができます、[ファイルにサポートされているプラットフォームをここで必要な](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)します。

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

## <a name="getting-a-coordinate-system"></a>座標系を取得します。

左上の高速検出正方形の左上隅にある QR コードに揃えて配置右手座標系を定義します。 座標系は、以下に示します。 (非表示)、ホワイト ペーパーには z 軸が指しているが、Unity、z 軸は、用紙と左手座標系。

示すように配置される、SpatialCoordinateSystem が定義されます。 この座標系は、API を使用して、プラットフォームから取得できます*Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*します。

![QR コードの座標系](images/Qr-coordinatesystem.png) 

QRCode から ^ コード オブジェクトを次のコードは、四角形を作成して QR 座標系に配置する方法を示します。

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

物理サイズを使用すると、QR 四角形を作成します。

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

座標系は、QR コードを描画するか、場所にホログラムをアタッチを使用できます。

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

*QRCodesTrackerPlugin::QRCodeAddedHandler*は次のようになります。

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

## <a name="troubleshooting-and-faq"></a>トラブルシューティングとよく寄せられる質問

**一般的なトラブルシューティング**

* Windows を実行しているは 10 年 2018年 10 月の更新ですか?
* レジストリ キーを設定するか。 その後、デバイスを再起動しますか。
* QR コードのバージョンのサポートされているバージョンですか。 QR コードのバージョンの 20 まで現在の API のサポート。 バージョン 5 を使用して一般的な使用をお勧めします。 
* QR コードに近づけるか。 近ければ近いほど、カメラは QR コードには、大きいほど、QR コードのバージョン、API をサポートできます。  

**近いか、QR コードを検出する必要があるのでしょうか。**

これは、QR コードのサイズに依存し、またどのようなバージョンが。 25 cm 辺を 5 cm 側からのさまざまなバージョン 1 の QR コードでは、最小検出間隔は 0.15 メーターから 0.5 m 範囲です。 最も遠い離れたから検出されたこれら小さい QR コードのターゲットの約 0.3 メーターからに移動の規模が大きいほど 1.4 メーターします。 QR コードをよりも大きく、次を見積もることができます。サイズの検出間隔が直線的に増加します。 当社の追跡ツールでは機能しません辺の QR コード 5 cm より小さい。

**ロゴの作業で QR コードを実行しますか。**

ロゴの QR コードがテストされていないは現在サポートされていません。

**クリアする方法は QR コード アプリからそれらが維持されないためですか。**

* QR コードは、ブート セッションでのみ保存されます。 再起動 (または再起動するドライバー) 後になったし、新しいオブジェクトの [次へ] の時刻として検出されます。
* QR コードの履歴はドライバー セッションで、システム レベルで保存されますが、QR コードの特定のタイムスタンプよりも古いを無視する場合に、アプリを構成することができます。 現在、API で複数のアプリは、データの利用可能性があるクリアリング QR コードの履歴をサポートするは。

**RS5 および将来のバージョンのプラグインがないプレリリース**RS5 バージョンのプラグインが RS5 に対してのみ機能し、将来のバージョンは機能しません。 Expermental プラグインでは、実際のプラグインで置き換えられるしを使って、今後のバージョン、windows のものである必要があります。
