---
title: カスタム Holographic リモート処理プレーヤーの作成
description: カスタム Holographic リモート処理プレーヤーアプリを作成することにより、リモートコンピューター上にレンダリングされたコンテンツを HoloLens 2 に表示できるカスタムアプリケーションを作成できます。 この記事では、これを実現する方法について説明します。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: 982a3f42014d8f5eb9ba181247fee9825fb78371
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434312"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>カスタム Holographic リモート処理プレーヤーアプリの作成

>[!IMPORTANT]
>このドキュメントでは、HoloLens 2 用のカスタムプレーヤーアプリケーションの作成について説明します。 HoloLens 2 向けに作成されたカスタムプレーヤーは、HoloLens 1 用に記述されたホストアプリケーションと互換性がありません。 これは、両方のアプリケーションが NuGet**パッケージバージョン 2.x**を使用する必要があることを意味します。

カスタム Holographic リモート処理プレーヤーアプリを作成することにより、HoloLens 2 のリモートコンピューター上のから[イマーシブビュー](app-views.md)を表示できるカスタムアプリケーションを作成できます。 この記事では、これを実現する方法について説明します。 このページのすべてのコードと作業中のプロジェクトは、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)にあります。

Holographic リモート処理プレーヤーを使用すると、アプリは、デスクトップ PC または、Xbox One などの UWP デバイスで[レンダリング](rendering.md)された Holographic コンテンツを表示して、より多くのシステムリソースにアクセスできるようになります。 Holographic Remoting player アプリは、入力データを Holographic Remoting ホストアプリケーションにストリームし、ビデオとオーディオストリームとしてイマーシブビューを受信します。 接続は標準の Wi-fi を使用して行われます。 プレーヤーアプリを作成するには、NuGet パッケージを使用して Holographic Remoting を UWP アプリに追加し、接続を処理し、イマーシブビューを表示するコードを記述します。 

## <a name="prerequisites"></a>前提条件

開始点としては、既に Windows Mixed Reality API を対象としている、動作する DirectX ベースの UWP アプリを使用することをお勧めします。 詳細については、「 [DirectX 開発の概要](directx-development-overview.md)」を参照してください。 既存のアプリがなく、ゼロから開始する場合は、 [ C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)を使用することをお勧めします。

>[!IMPORTANT]
>Holographic リモート処理を使用するすべてのアプリは、[マルチスレッドアパートメント](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)を使用するように作成する必要があります。 [シングルスレッドのアパートメント](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments)使用はサポートされていますが、パフォーマンスが低下し、再生中に途切れが生じる可能性があります。 /Winrt C++ [winrt:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started)を使用すると、マルチスレッドアパートメントが既定値になります。

## <a name="get-the-holographic-remoting-nuget-package"></a>Holographic リモート処理 NuGet パッケージを取得する

Visual Studio で NuGet パッケージをプロジェクトに追加するには、次の手順を実行する必要があります。
1. Visual Studio でプロジェクトを開きます。
2. プロジェクトノードを右クリックし、 **[NuGet パッケージの管理...]** を選択します。
3. 表示されるパネルで、 **[参照]** をクリックし、"Holographic Remoting" を検索します。
4. **[Holographic]** を選択し **、最新の**2.x バージョンを選択して **[インストール]** をクリックします。
5. **[プレビュー]** ダイアログが表示されたら、 **[OK]** をクリックします。
6. 次に表示されるダイアログは、使用許諾契約書です。 [**同意**する] をクリックして、使用許諾契約書に同意します。

>[!IMPORTANT]
><a name="idl"></a>NuGet パッケージ内の ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` には、Holographic Remoting によって公開される API に関する詳細なドキュメントが含まれています。

## <a name="modify-the-packageappxmanifest-of-the-application"></a>アプリケーションの package.appxmanifest を変更する

NuGet パッケージによって追加された Holographic をアプリケーションに認識させるには、プロジェクトで次の手順を実行する必要があります。

1. ソリューションエクスプローラーで**package.appxmanifest**ファイルを右クリックし、 **[プログラムから開く]** を選択します。
2. **XML (テキスト) エディター**を選択し、[OK] をクリックします。
3. 次の行をファイルに追加して保存します。
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>プレーヤーのコンテキストを作成する

最初の手順として、アプリケーションでプレーヤーコンテキストを作成する必要があります。

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting host and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>Holographic リモート処理は、Windows の一部である Windows Mixed Reality ランタイムをリモート処理固有のランタイムに置き換えることによって機能します。 これは、プレーヤーのコンテキストの作成時に実行されます。 そのため、プレーヤーコンテキストを作成する前に Windows Mixed Reality API を呼び出すと、予期しない動作が発生する可能性があります。 推奨される方法は、任意の混合 Reality API と対話する前に、可能な限り早くプレーヤーコンテキストを作成することです。 Windows Mixed Reality API を使用して作成または取得したオブジェクトを、を呼び出す前に、その後に作成または取得したオブジェクトに ```PlayerContext::Create()``` 混在させないでください。

次に、 [HolographicSpace](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)を呼び出して、HolographicSpace を作成します。

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a>ホストに接続する

プレーヤーアプリがコンテンツを表示できる状態になったら、ホストへの接続を確立できます。

接続は、次のいずれかの方法で確立できます。
1) HoloLens 2 で実行されているプレーヤーアプリは、ホストアプリに接続します。
2) ホストアプリは、HoloLens 2 で実行されているプレーヤーアプリに接続します。

プレーヤーアプリからホストに接続するには、プレーヤーコンテキストでホスト名とポートを指定して ```Connect``` メソッドを呼び出します。 既定のポートは**8265**です。

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>任意C++の HRESULT_ERROR ```Connect``` API と同様に、処理する必要がある winrt:: がスローされる場合があります。

プレーヤーアプリで着信接続をリッスンするには、```Listen``` メソッドを呼び出します。 この呼び出しでは、ハンドシェイクポートとトランスポートポートの両方を指定できます。 ハンドシェイクポートは、初期ハンドシェイクに使用されます。 データは、トランスポートポートを介して送信されます。 既定では、ポート番号**8265**と**8266**が使用されます。

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>接続関連のイベントの処理

この ```PlayerContext``` は、接続の状態を監視するために3つのイベントを公開します。
1) OnConnected: ホストへの接続が正常に確立されたときにトリガーされます。
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected: 確立された接続が終了した場合、または接続を確立できなかった場合にトリガーされます。
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>使用可能な ```ConnectionFailureReason``` 値は、```Microsoft.Holographic.AppRemoting.idl```[ファイル](#idl)に記載されています。

3) OnListening: 受信接続のリッスンが開始されます。
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

さらに、プレーヤーのコンテキストで ```ConnectionState``` プロパティを使用して接続状態を照会することもできます。
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>リモートで描画されたフレームを表示する

リモートでレンダリングされるコンテンツを表示するには、 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)のレンダリング中に ```PlayerContext::BlitRemoteFrame()``` を呼び出します。 

```BlitRemoteFrame()``` では、現在の HolographicFrame のバックバッファーがレンダーターゲットとしてバインドされている必要があります。 バックバッファーは、 [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)プロパティを介して[HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)から受け取ることができます。

```BlitRemoteFrame()``` 呼び出されると、ホストアプリケーションから最後に受信したフレームが HolographicFrame の BackBuffer にコピーされます。 さらに、リモートアプリケーションがリモートフレームのレンダリング中にフォーカスポイントを指定している場合は、フォーカスポイントが設定されます。

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame()``` により、現在のフレームのフォーカスポイントが上書きされる可能性があります。 
>- フォールバックフォーカスポイントを指定するには、```PlayerContext::BlitRemoteFrame()```する前に[HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)を呼び出します。 
>- リモートフォーカスポイントを上書きするには、```PlayerContext::BlitRemoteFrame()```後に[HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)を呼び出します。

成功した場合、```BlitRemoteFrame()``` は ```BlitResult::Success_Color```を返します。 それ以外の場合は、エラーの理由を返します。
- ```BlitResult::Failed_NoRemoteFrameAvailable```: 使用可能なリモートフレームがないため、失敗しました。
- ```BlitResult::Failed_NoCamera```: カメラが存在しないために失敗しました。
- ```BlitResult::Failed_RemoteFrameTooOld```: リモートフレームが古すぎるため失敗しました (PlayerContext:: BlitRemoteFrameTimeout プロパティを参照してください)。

## 省略可能: Set BlitRemoteFrameTimeout<a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimout``` は、バージョン[2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。 

```PlayerContext::BlitRemoteFrameTimeout``` プロパティは、新しいリモートフレームが受信されなかった場合に、リモートフレームが再利用される時間を指定します。 

一般的なユースケースでは、一定の時間、新しいフレームが受信されなかった場合に、BlitRemoteFrame timeout で空の画面が表示されるようにします。 有効にすると、```BlitRemoteFrame``` メソッドの戻り値の型を使用して、ローカルに表示されるフォールバックコンテンツに切り替えることもできます。 

タイムアウトを有効にするには、プロパティ値を100ミリ秒以上の期間に設定します。 タイムアウトを無効にするには、プロパティをゼロ期間に設定します。 タイムアウトが有効になっていて、設定した期間にリモートフレームを受信しなかった場合、BlitRemoteFrame は失敗し、新しいリモートフレームが受信されるまで ```Failed_RemoteFrameTooOld``` が返されます。

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>省略可能: 最後のリモートフレームに関する統計を取得する

パフォーマンスまたはネットワークの問題を診断するには、```PlayerContext::LastFrameStatistics``` プロパティを使用して最後のリモートフレームに関する統計情報を取得できます。 統計は[HolographicFrame::P](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)の呼び出し中に更新されます。 current予測。

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

詳細については、```Microsoft.Holographic.AppRemoting.idl```[ファイル](#idl)の ```PlayerFrameStatistics``` のドキュメントを参照してください。

## <a name="optional-custom-data-channels"></a>省略可能: カスタムデータチャネル

カスタムデータチャネルは、既に確立されているリモート処理接続を介してユーザーデータを送信するために使用できます。 詳細については、「[カスタムデータチャネル](holographic-remoting-custom-data-channels.md)」を参照してください。

## <a name="see-also"></a>参照
* [Holographic Remoting ホストアプリの作成](holographic-remoting-create-host.md)
* [カスタムの Holographic Remoting データ チャネル](holographic-remoting-custom-data-channels.md)
* [Holographic Remoting を使用したセキュリティで保護された接続の確立](holographic-remoting-secure-connection.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic Remoting ソフトウェア ライセンス条項](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
