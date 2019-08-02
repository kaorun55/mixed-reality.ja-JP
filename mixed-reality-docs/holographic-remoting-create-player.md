---
title: カスタム Holographic リモート処理プレーヤーの作成
description: カスタム Holographic リモート処理プレーヤーアプリを作成することにより、リモートコンピューター上にレンダリングされたコンテンツを HoloLens 2 に表示できるカスタムアプリケーションを作成できます。 この記事では、これを実現する方法について説明します。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: fdc3d3bbd72d0812377d6a70c975f2111e1a2224
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718096"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>カスタム Holographic リモート処理プレーヤーアプリの作成

>[!IMPORTANT]
>このドキュメントでは、HoloLens 2 用のカスタムプレーヤーアプリケーションの作成について説明します。 HoloLens 2 向けに作成されたカスタムプレーヤーは、HoloLens 1 用に記述されたホストアプリケーションと互換性がありません。 これは、両方のアプリケーションが NuGet**パッケージバージョン 2.x**を使用する必要があることを意味します。

カスタム Holographic リモート処理プレーヤーアプリを作成することにより、HoloLens 2 のリモートコンピューター上のから[イマーシブビュー](app-views.md)を表示できるカスタムアプリケーションを作成できます。 この記事では、これを実現する方法について説明します。 このページのすべてのコードと作業中のプロジェクトは、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)にあります。

Holographic リモート処理プレーヤーを使用すると、アプリは、デスクトップ PC または、Xbox One などの UWP デバイスで[レンダリング](rendering.md)された Holographic コンテンツを表示して、より多くのシステムリソースにアクセスできるようになります。 Holographic Remoting player アプリは、入力データを Holographic Remoting ホストアプリケーションにストリームし、ビデオとオーディオストリームとしてイマーシブビューを受信します。 接続は標準の Wi-fi を使用して行われます。 プレーヤーアプリを作成するには、NuGet パッケージを使用して Holographic Remoting を UWP アプリに追加し、接続を処理し、イマーシブビューを表示するコードを記述します。 

## <a name="prerequisites"></a>必須コンポーネント

開始点としては、既に Windows Mixed Reality API を対象としている、動作する DirectX ベースの UWP アプリを使用することをお勧めします。 詳細については、「 [DirectX 開発の概要](directx-development-overview.md)」を参照してください。 既存のアプリがなく、ゼロから開始する場合は、 [ C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)を使用することをお勧めします。

>[!IMPORTANT]
>Holographic リモート処理を使用するすべてのアプリは、[マルチスレッドアパートメント](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)を使用するように作成する必要があります。 [シングルスレッドのアパートメント](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments)使用はサポートされていますが、パフォーマンスが低下し、再生中に途切れが生じる可能性があります。 /Winrt C++ [winrt:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started)を使用すると、マルチスレッドアパートメントが既定値になります。

## <a name="get-the-holographic-remoting-nuget-package"></a>Holographic リモート処理 NuGet パッケージを取得する

Visual Studio で NuGet パッケージをプロジェクトに追加するには、次の手順を実行する必要があります。
1. Visual Studio でプロジェクトを開きます。
2. プロジェクトノードを右クリックし、 **[NuGet パッケージの管理...]** を選択します。
3. 表示されるパネルで、 **[参照]** をクリックし、"Holographic Remoting" を検索します。
4. **[Holographic]** を選択し **、最新の**2.x バージョンを選択して **[インストール]** をクリックします。
5. **[プレビュー]** ダイアログが表示されたら、 **[OK]** をクリックします。
6. 次に表示されるダイアログは、使用許諾契約書です。 [**同意**する] をクリックして、使用許諾契約書に同意します。

>[!IMPORTANT]
><a name="idl"></a>NuGet ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```パッケージ内には、Holographic Remoting によって公開される API に関する詳細なドキュメントが含まれています。

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
>Holographic リモート処理は、Windows の一部である Windows Mixed Reality ランタイムをリモート処理固有のランタイムに置き換えることによって機能します。 これは、プレーヤーのコンテキストの作成時に実行されます。 そのため、プレーヤーコンテキストを作成する前に Windows Mixed Reality API を呼び出すと、予期しない動作が発生する可能性があります。 推奨される方法は、任意の混合 Reality API と対話する前に、可能な限り早くプレーヤーコンテキストを作成することです。 Windows Mixed Reality API を使用して作成または取得したオブジェクトを```PlayerContext::Create()``` 、後で作成または取得したオブジェクトで混在させないでください。

次に、 [HolographicSpace](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)を呼び出して、HolographicSpace を作成します。

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a>ホストに接続する

プレーヤーアプリがコンテンツを表示できる状態になったら、ホストへの接続を確立できます。

接続は、次のいずれかの方法で確立できます。
1) HoloLens 2 で実行されているプレーヤーアプリは、ホストアプリに接続します。
2) ホストアプリは、HoloLens 2 で実行されているプレーヤーアプリに接続します。

プレーヤーアプリからホストに接続するには、プレーヤー ```Connect```コンテキストでホスト名とポートを指定してメソッドを呼び出します。 既定のポートは**8265**です。

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
>任意C++の/winrt API ```Connect```と同様に、処理する必要がある winrt:: hresult_error をスローする場合があります。

プレーヤーアプリで着信接続をリッスンするには、メソッドを```Listen```呼び出します。 この呼び出しでは、ハンドシェイクポートとトランスポートポートの両方を指定できます。 ハンドシェイクポートは、初期ハンドシェイクに使用されます。 データは、トランスポートポートを介して送信されます。 既定では、ポート番号**8265**と**8266**が使用されます。

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

は```PlayerContext``` 、接続の状態を監視するために3つのイベントを公開します。
1) OnConnected:ホストへの接続が正常に確立されたときにトリガーされます。
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected:確立された接続が終了した場合、または接続を確立できなかった場合にトリガーされます。
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
>指定```ConnectionFailureReason```できる値は、[ファイル](#idl)に記載されて```Microsoft.Holographic.AppRemoting.idl```います。

3) OnListening:受信接続のリッスンを開始します。
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

さらに、プレーヤーのコンテキストで```ConnectionState```プロパティを使用して接続状態を照会することもできます。
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>リモートで描画されたフレームを表示する

リモートでレンダリングされるコンテンツを表示```PlayerContext::BlitRemoteFrame()```するには、 [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)のレンダリング中にを呼び出します。 

```BlitRemoteFrame()```現在の HolographicFrame のバックバッファーがレンダーターゲットとしてバインドされている必要があります。 バックバッファーは、 [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)プロパティを介して[HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)から受け取ることができます。

呼び出されると```BlitRemoteFrame()``` 、ホストアプリケーションからの最新の受信フレームを HolographicFrame の BackBuffer にコピーします。 さらに、リモートアプリケーションがリモートフレームのレンダリング中にフォーカスポイントを指定している場合は、フォーカスポイントが設定されます。

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame()```現在のフレームのフォーカスポイントを上書きする可能性があります。 
>- フォールバックフォーカスポイントを指定するには、前に```PlayerContext::BlitRemoteFrame()``` [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)を呼び出します。 
>- リモートフォーカスポイントを overrwrite するには、 [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame()```を呼び出します。

成功した```BlitRemoteFrame()```場合```BlitResult::Success_Color```、はを返します。 それ以外の場合は、エラーの理由を返します。
- ```BlitResult::Failed_NoRemoteFrameAvailable``` :使用可能なリモートフレームがないため、失敗しました。
- ```BlitResult::Failed_NoCamera``` :カメラが存在しないために失敗しました。

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>省略可能: 最後のリモートフレームに関する統計を取得します

パフォーマンスまたはネットワークの問題を診断するために、 ```PlayerContext::LastFrameStatistics```プロパティを使用して最後のリモートフレームに関する統計を取得できます。 統計は[HolographicFrame::P](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)の呼び出し中に更新されます。 current予測。

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

詳細については、 ```PlayerFrameStatistics``` [ファイル](#idl)のドキュメント```Microsoft.Holographic.AppRemoting.idl```を参照してください。

## <a name="optional-custom-data-channels"></a>省略可能: カスタムデータチャネル

カスタムデータチャネルは、既に確立されているリモート処理接続を介してユーザーデータを送信するために使用できます。 詳細については、「[カスタムデータチャネル](holographic-remoting-custom-data-channels.md)」を参照してください。

## <a name="see-also"></a>関連項目
* [Holographic Remoting ホストアプリの作成](holographic-remoting-create-host.md)
* [カスタム Holographic リモート処理データチャネル](holographic-remoting-custom-data-channels.md)
* [Holographic Remoting を使用したセキュリティで保護された接続の確立](holographic-remoting-secure-connection.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic リモート処理ソフトウェアライセンス条項](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)