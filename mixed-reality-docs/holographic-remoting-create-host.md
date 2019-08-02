---
title: Holographic Remoting ホストアプリの作成
description: リモートコンピューター上にレンダリングされる Holographic Remoting host アプリのリモートコンテンツを作成することによって、HoloLens 2 にストリーミングできます。 この記事では、これを実現する方法について説明します。
author: bethau
ms.author: bethau
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: 95cf98504f26e2362b3c4fd38e7d9228350798f3
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718066"
---
# <a name="writing-a-holographic-remoting-host-app"></a>Holographic Remoting ホストアプリの作成

>[!IMPORTANT]
>このドキュメントでは、HoloLens 2 用のホストアプリケーションの作成について説明します。 **HoloLens 1**用のホストアプリケーションでは、NuGet**パッケージバージョン 1.x**を使用する必要があります。 これは、HoloLens 2 用に作成されたホストアプリケーションが HoloLens 1 と互換性がないことを意味します。 HoloLens 1 のドキュメントについては、[こちら](add-holographic-remoting.md)を参照してください。

Holographic リモート処理ホストアプリケーションを作成することにより、リモートコンピューター上にレンダリングされるリモートコンテンツを HoloLens 2 にストリーミングできます。 この記事では、これを実現する方法について説明します。 このページのすべてのコードと作業中のプロジェクトは、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)にあります。

Holographic リモート処理を使用すると、アプリは、デスクトップ PC 上でホストされている Holographic コンテンツ、または Xbox One などの UWP デバイスで、HoloLens 2 をターゲットにすることができます。これにより、より多くのシステムリソースにアクセスし、リモートの[イマーシブビュー](app-views.md)を既存のものに統合することが可能になります。デスクトップ PC ソフトウェア。 リモートホストアプリは HoloLens 2 から入力データストリームを受け取り、仮想イマーシブビューでコンテンツをレンダリングし、コンテンツフレームを HoloLens 2 にストリームバックします。 接続は標準の Wi-fi を使用して行われます。 Holographic リモート処理は、NuGet パケット経由でデスクトップまたは UWP アプリに追加されます。 接続を処理し、イマーシブビューでレンダリングする追加のコードが必要です。

一般的なリモート処理接続では、待機時間が50ミリ秒に抑えられます。 プレーヤーアプリは、リアルタイムで待機時間を報告できます。

## <a name="prerequisites"></a>必須コンポーネント

開始点として、Windows Mixed Reality API を対象とする、動作する DirectX ベースのデスクトップまたは UWP アプリを使用することをお勧めします。 詳細については、「 [DirectX 開発の概要](directx-development-overview.md)」を参照してください。 [ C++ Holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)は、出発点として適しています。

>[!IMPORTANT]
>Holographic リモート処理を使用するすべてのアプリは、[マルチスレッドアパートメント](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)を使用するように作成する必要があります。 [シングルスレッドアパートメント](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments)の使用はサポートされていますが、パフォーマンスが低下し、再生中に途切れが生じる可能性があります。 /Winrt C++ [winrt:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started)を使用すると、マルチスレッドアパートメントが既定値になります。



## <a name="get-the-holographic-remoting-nuget-package"></a>Holographic リモート処理 NuGet パッケージを取得する

Visual Studio で NuGet パッケージをプロジェクトに追加するには、次の手順を実行する必要があります。
1. Visual Studio でプロジェクトを開きます。
2. プロジェクトノードを右クリックし、 **[NuGet パッケージの管理...]** を選択します。
3. 表示されるパネルで、 **[参照]** をクリックし、"Holographic Remoting" を検索します。
4. **[Holographic]** を選択し **、最新の**2.x バージョンを選択して **[インストール]** をクリックします。
5. **[プレビュー]** ダイアログが表示されたら、 **[OK]** をクリックします。
6. 次に表示されるダイアログは、使用許諾契約書です。 [**同意**する] をクリックして、使用許諾契約書に同意します。

>[!NOTE]
>HoloLens 1 を対象とする開発者は、NuGet パッケージ**のバージョン 1.x**を引き続き利用できます。 詳細については、「 [Add Holographic Remoting (HoloLens 1)](add-holographic-remoting.md)」を参照してください。

## <a name="create-the-remote-context"></a>リモートコンテキストを作成する

最初の手順として、アプリケーションでリモートコンテキストを作成する必要があります。

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
>Holographic リモート処理は、Windows の一部である Windows Mixed Reality ランタイムをリモート処理固有のランタイムに置き換えることによって機能します。 これは、リモートコンテキストの作成時に実行されます。 そのため、リモートコンテキストを作成する前に Windows Mixed Reality API を呼び出すと、予期しない動作が発生する可能性があります。 推奨される方法は、混合の現実 API と対話する前に、できるだけ早くリモートコンテキストを作成することです。 Windows Mixed Reality API を使用して作成または取得したオブジェクトを、後で作成または取得したオブジェクトと共に使用することは避けてください。

次に、holographic 領域を作成する必要があります。 CoreWindow の指定は必要ありません。 CoreWindow を持たないデスクトップアプリは、のみを```nullptr```渡すことができます。

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>デバイスへの接続

ホストアプリがコンテンツをレンダリングする準備ができたら、デバイスへの接続を確立できます。

接続は、次の2つの方法のいずれかで実行できます。
1) ホストアプリは、デバイスで実行されているプレーヤーに接続します。
2) デバイスで実行されているプレーヤーは、ホストアプリに接続します。

ホストアプリから HoloLens 2 への接続を確立するには```Connect``` 、ホスト名とポートを指定して、リモートコンテキストでメソッドを呼び出します。 Holographic リモート処理プレーヤーによって使用されるポートは**8265**です。

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>任意C++の/winrt API ```Connect```と同様に、処理する必要がある winrt:: hresult_error をスローする場合があります。

>[!TIP]
>[ C++/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/)言語のプロジェクションを使用しない```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h```ようにするには、Holographic リモート処理 NuGet パッケージ内にあるファイルを含めることができます。 これには、基になる COM インターフェイスの宣言が含まれます。 ただし、 C++/WinRT を使用することをお勧めします。

ホストアプリでの着信接続のリッスンは、 ```Listen```メソッドを呼び出すことによって行うことができます。 この呼び出しでは、ハンドシェイクポートとトランスポートポートの両方を指定できます。 ハンドシェイクポートは、初期ハンドシェイクに使用されます。 データは、トランスポートポートを介して送信されます。 既定では、 **8265**および**8266**が使用されます。

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>NuGet ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```パッケージ内には、Holographic Remoting によって公開される API に関する詳細なドキュメントが含まれています。

## <a name="handling-remoting-specific-events"></a>リモート処理固有のイベントの処理

リモートコンテキストは、接続の状態を監視するために重要な3つのイベントを公開します。
1) OnConnected:デバイスへの接続が正常に確立されたときにトリガーされます。
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnected:確立された接続が閉じられた場合、または接続が確立できなかった場合にトリガーされます。
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) OnListening:受信接続のリッスンを開始します。
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

さらに、リモートコンテキストの```ConnectionState```プロパティを使用して接続状態を照会することもできます。
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>音声イベントの処理

リモート音声インターフェイスを使用すると、音声トリガーを HoloLens 2 に登録し、それらをホストアプリケーションにリモート処理することができます。

この追加のメンバーは、リモート音声の状態を追跡するために必要です。

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

まず、リモート音声インターフェイスを取得する必要があります。

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

非同期ヘルパーメソッドを使用すると、リモート音声を初期化できます。 初期化にはかなりの時間がかかる場合があるため、非同期的に実行する必要があります。 [/WinRT を使用しC++た同時実行と非同期操作](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)では、 C++/winrtを使用して非同期関数を作成する方法について説明します。

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleHostMain> sampleHostMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleHostMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleHostMain = sampleHostMainWeak.lock())
            {
                sampleHostMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"en-US", grammarFile, dictionary);
}
```

認識する語句を指定する方法は2つあります。
1) 音声文法 xml ファイル内の仕様。 詳細について[は、「基本的な XML 文法を作成する方法](https://docs.microsoft.com/en-us/previous-versions/office/developer/speech-technologies/hh361658(v=office.14))」を参照してください。
2) を指定するには、をディクショナリベクター ```ApplyParameters```内に渡します。

On認識された音声コールバック内で、音声イベントを処理できます。

```cpp
void SampleHostMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a>ストリーミングされるコンテンツをローカルでプレビューする

デバイスに送信されるホストアプリで同じコンテンツを表示するには、 ```OnSendFrame```リモートコンテキストのイベントを使用できます。 ```OnSendFrame```イベントは、Holographic リモート処理ライブラリが現在のフレームをリモートデバイスに送信するたびにトリガーされます。 これは、コンテンツを撮影し、デスクトップや UWP ウィンドウに array.blit するのに最適な時間です。

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="optional-custom-data-channels"></a>省略可能: カスタムデータチャネル

カスタムデータチャネルは、既に確立されているリモート処理接続を介してユーザーデータを送信するために使用できます。 詳細については、「[カスタムデータチャネル](holographic-remoting-custom-data-channels.md)」を参照してください。

## <a name="see-also"></a>関連項目
* [カスタム Holographic リモート処理プレーヤーアプリの作成](holographic-remoting-create-player.md)
* [カスタム Holographic リモート処理データチャネル](holographic-remoting-custom-data-channels.md)
* [Holographic Remoting を使用したセキュリティで保護された接続の確立](holographic-remoting-secure-connection.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic リモート処理ソフトウェアライセンス条項](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)