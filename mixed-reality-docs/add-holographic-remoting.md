---
title: Holographic リモート処理の追加
description: Holographic Remoting を使用してネットワーク経由で HoloLens にホログラムを表示する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Windows Mixed Reality, ホログラム, holographic リモート処理, リモートレンダリング, ネットワークレンダリング, HoloLens, リモートホログラム
ms.openlocfilehash: 8d645f634ff0fc820893f5554fd602aa3a2f38e3
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829623"
---
# <a name="add-holographic-remoting"></a>Holographic リモート処理の追加

## <a name="hololens-2"></a>HoloLens 2

> [!NOTE]
> HoloLens 2 に固有のその他のガイダンスは[近日対応予定](index.md#news-and-notes)です。

Holographic リモート処理を使用する HoloLens 開発者は、HoloLens 2 との互換性を確保するためにアプリを更新する必要があります。  これには、まだ公開されていない Holographic リモート処理 NuGet パッケージの新しいバージョンが必要です。  HoloLens NuGet パッケージを使用しているアプリケーションが HoloLens 2 の Holographic リモート処理プレーヤーに接続しようとすると、接続は失敗します。  HoloLens 2 NuGet パッケージが利用可能になったら、このページで更新プログラムをご覧ください。

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Holographic remoting をデスクトップまたは UWP アプリに追加する

このページでは、Holographic リモート処理をデスクトップまたは UWP アプリに追加する方法について説明します。

Holographic リモート処理を使用すると、アプリはデスクトップ PC でホストされている Holographic コンテンツ、または Xbox One などの UWP デバイスでホストされている HoloLens を対象にすることができます。これにより、より多くのシステムリソースにアクセスし、リモートの[イマーシブビュー](app-views.md)を統合することが可能になります。既存のデスクトップ PC ソフトウェア。 リモート処理ホストアプリは、HoloLens から入力データストリームを受け取り、仮想イマーシブビューでコンテンツをレンダリングし、コンテンツフレームを HoloLens にストリームバックします。 接続は標準の Wi-fi を使用して行われます。 リモート処理を使用するには、NuGet パッケージを使用して、holographic リモート処理をデスクトップまたは UWP アプリに追加し、接続を処理し、イマーシブビューでレンダリングするコードを記述します。 ヘルパーライブラリは、デバイス接続を処理するタスクを簡略化するコードサンプルに含まれています。

一般的なリモート処理接続では、待機時間が50ミリ秒に抑えられます。 プレーヤーアプリは、リアルタイムで待機時間を報告できます。

>[!NOTE]
>この記事のコードスニペットでは、現在、 C++ [ C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用されてC++いる C + c++ 17 準拠の/WinRT ではなく、/cx の使用方法を示しています。  これらの概念は、プロジェクトC++の場合と同じですが、コードを変換する必要があります。

### <a name="get-the-remoting-nuget-packages"></a>リモート処理 NuGet パッケージを取得する

次の手順に従って、holographic リモート処理用の NuGet パッケージを取得し、プロジェクトから参照を追加します。
1. Visual Studio でプロジェクトにアクセスします。
2. プロジェクトノードを右クリックし、 **[NuGet パッケージの管理...]** を選択します。
3. 表示されるパネルで、 **[参照]** をクリックし、"Holographic Remoting" を検索します。
4. **Holographic**を選択し、 **[インストール]** をクリックします。
5. **[プレビュー]** ダイアログが表示されたら、 **[OK]** をクリックします。
6. 次に表示されるダイアログは、使用許諾契約書です。 [**同意**する] をクリックして、使用許諾契約書に同意します。

### <a name="create-the-holographicstreamerhelpers"></a>HolographicStreamerHelpers を作成する

まず、HolographicStreamerHelpers のインスタンスが必要です。 これをリモート処理を処理するクラスに追加します。

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

また、接続状態を追跡する必要もあります。 プレビューを表示する場合は、コピー先のテクスチャを用意する必要があります。 また、接続状態のロック、HoloLens の IP アドレスを格納する方法など、いくつかの方法も必要です。

```
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>HolographicStreamerHelpers を初期化して HoloLens に接続する

HoloLens デバイスに接続するには、HolographicStreamerHelpers のインスタンスを作成し、ターゲット IP アドレスに接続します。 Holographic リモート処理ライブラリでは、エンコーダーとデコーダーの解像度が正確に一致することを想定しているため、HoloLens の表示幅と高さに合わせてビデオフレームサイズを設定する必要があります。

```
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

デバイス接続は非同期です。 アプリは、接続、切断、フレーム送信イベントのイベントハンドラーを提供する必要があります。

OnConnected イベントは、UI を更新したり、レンダリングを開始したりすることができます。 デスクトップのコードサンプルでは、"connected" メッセージを使用してウィンドウタイトルを更新します。

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

OnDisconnected イベントは、再接続や UI の更新などを処理できます。 この例では、一時的なエラーが発生した場合に再接続します。

```
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

リモート処理コンポーネントがフレームを送信する準備ができたら、アプリは Sendframe イベントにそのコピーを作成する機会を提供します。 ここでは、プレビューウィンドウで表示できるように、フレームをスワップチェーンにコピーします。

```
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a>Holographic コンテンツのレンダリング

リモート処理を使用してコンテンツをレンダリングするには、デスクトップまたは UWP アプリ内に仮想 IFrameworkView を設定し、リモート処理から holographic フレームを処理します。 このビューでは、すべての Windows Holographic Api が同じ方法で使用されますが、設定は少し異なります。

自分で作成する代わりに、holographic space および speech コンポーネントは HolographicRemotingHelpers クラスから取得されます。

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Run メソッド内で更新ループを使用する代わりに、デスクトップまたは UWP アプリのメインループからティックの更新を提供します。 これにより、デスクトップや UWP アプリはメッセージ処理を制御できます。

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Holographic app ビューの Tick () メソッドは、update、draw、present ループの1回の繰り返しを完了します。

```
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

Holographic app view update、render、および present loop は、HoloLens で実行する場合とまったく同じです。ただし、デスクトップ PC 上のシステムリソースの量がはるかに多くなります。 多くの三角形をレンダリングしたり、描画パスを増やしたり、より多くの物理処理を行ったり、x64 プロセスを使用して 2 GB を超える RAM を必要とするコンテンツを読み込むことができます。

### <a name="disconnect-and-end-the-remote-session"></a>リモートセッションを切断して終了する

接続を切断する場合 (たとえば、ユーザーが UI ボタンをクリックして HolographicStreamerHelpers の切断 () を呼び出し、オブジェクトを解放する場合など)。

```
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a>リモート処理プレーヤーを取得する

Windows Holographic リモート処理プレーヤーは、接続先のリモートホストアプリのエンドポイントとして Windows アプリストアで提供されます。 Windows Holographic リモート処理プレーヤーを入手するには、HoloLens から Windows アプリストアにアクセスし、リモート処理を検索して、アプリをダウンロードします。 リモート処理プレーヤーには、統計を画面に表示する機能が含まれています。これは、リモート処理ホストアプリをデバッグするときに便利です。

## <a name="notes-and-resources"></a>メモとリソース

Holographic app ビューでは、holographic space を初期化するために使用する必要がある Direct3D デバイスをアプリに提供する方法が必要になります。 アプリでプレビューフレームをコピーして表示するには、この Direct3D デバイスを使用する必要があります。

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**コードサンプル:** 完全な Holographic Remoting コードサンプルが用意されています。これには、デスクトップ Win32、UWP DirectX、および XAML を使用した UWP 用のリモート処理ホストプロジェクトと互換性のある Holographic アプリケーションビューが含まれています。 取得するには、こちらを参照してください。
* [リモート処理のための Windows Holographic のコードサンプル](https://github.com/Microsoft/HoloLensCompanionKit/)

**デバッグに関する注意:** Holographic リモート処理ライブラリは、初回例外をスローできます。 これらの例外は、その時点でアクティブになっている Visual Studio の例外設定によっては、デバッグセッションで表示される場合があります。 これらの例外は、Holographic リモート処理ライブラリによって内部的にキャッチされ、無視することができます。
