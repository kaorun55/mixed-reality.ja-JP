---
title: Holographic のリモート処理を追加します。
description: Holographic のリモート処理を使用して、ネットワーク経由で、HoloLens にホログラムをレンダリングする方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、holographic のリモート処理、リモート レンダリング、ネットワークの表示、HoloLens、リモート ホログラム
ms.openlocfilehash: 4726c6af43fe1b89fc8298e459a1af9dfa5fc667
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605128"
---
# <a name="add-holographic-remoting"></a>Holographic のリモート処理を追加します。

> [!NOTE]
> HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Holographic のリモート処理をデスクトップまたは UWP アプリに追加します。

このページには、デスクトップまたは UWP アプリに Holographic のリモート処理を追加する方法について説明します。

Holographic のリモート処理により、アプリ、デスクトップ PC または Xbox One、多くのシステム リソースへのアクセス許可とにできるように統合リモートなどの UWP デバイスでホスト holographic のコンテンツを含む、HoloLens をターゲットに[没入型のビュー](app-views.md)に既存のデスクトップ PC のソフトウェア。 リモート処理ホストのアプリ、HoloLens から、入力データ ストリームを受信するには、仮想の没入型ビューでコンテンツをレンダリングおよびコンテンツ フレームは、HoloLens をストリームします。 標準の Wi-fi を使用して接続が確立します。 リモート処理を使用して、するには、NuGet パッケージを使用して、デスクトップまたは UWP アプリに holographic のリモート処理を追加し、接続を処理し、没入型のビューで表示するためにコードを記述します。 デバイスの接続を処理するタスクを簡略化するコード サンプルでは、ヘルパー ライブラリが含まれます。

一般的なリモート処理接続が 50 ミリ秒の待機時間と低い必要があります。 プレーヤー アプリは、リアルタイムでの待機時間を報告できます。

>[!NOTE]
>この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。  概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。

### <a name="get-the-remoting-nuget-packages"></a>NuGet パッケージのリモート処理の取得します。

Holographic のリモート処理用の NuGet パッケージを取得する次の手順に従ってし、プロジェクトからの参照を追加します。
1. Visual Studio でプロジェクトに移動します。
2. プロジェクト ノードを右クリックして**NuGet パッケージの管理.**
3. 表示されるパネル で、**参照**し、「Holographic リモート処理」を検索します。
4. 選択**Microsoft.Holographic.Remoting**クリック**インストール**します。
5. 場合、**プレビュー**ダイアログが表示されたら、をクリックして**OK**します。
6. 表示される次のダイアログ ボックスでは、使用許諾契約書です。 をクリックして**同意**ライセンス契約に同意します。

### <a name="create-the-holographicstreamerhelpers"></a>作成、HolographicStreamerHelpers

最初に、インスタンス HolographicStreamerHelpers の必要があります。 これは、リモート処理を処理するクラスを追加します。

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

また、接続状態を追跡する必要があります。 プレビューを表示する場合にコピーするテクスチャをする必要があります。 また、接続状態のロック、HoloLens の IP アドレスを格納する何らかの方法など、いくつかのものが必要し、など。

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>HolographicStreamerHelpers を初期化し、HoloLens への接続

HoloLens デバイスに接続するには、HolographicStreamerHelpers のインスタンスを作成し、ターゲット IP アドレスに接続します。 Holographic のリモート処理ライブラリが正確に一致するようにエンコーダーとデコーダーの解決策が必要ですので、HoloLens の表示幅と高さに合わせてビデオ フレーム サイズを設定する必要があります。

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

デバイスの接続は非同期です。 Connect で、イベント ハンドラーを提供するアプリのニーズが接続解除、およびイベントをフレームに送信します。

OnConnected イベントは、UI を更新のレンダリングを開始および具合です。 デスクトップのコード サンプルで、「接続済み」のメッセージ ウィンドウのタイトルを更新します。

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

OnDisconnected イベントには、再接続や UI の更新を処理できます。 この例では、一時的な障害が発生した場合を再接続します。

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

リモート処理コンポーネントのフレームを送信する準備ができたら、アプリには、SendFrameEvent にそのコピーを作成する機会が提供されます。 ここでは、コピー、フレーム スワップ チェーンにプレビュー ウィンドウに表示されることができるようにします。

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

### <a name="render-holographic-content"></a>Holographic のコンテンツをレンダリングします。

コンテンツを表示するためにリモート処理を使用して、デスクトップまたは UWP アプリ内で仮想 IFrameworkView を設定および処理するリモート処理から holographic フレーム。 すべての Windows Holographic Api と同じ方法で、このビューがわずかに異なる設定を使用します。

を作成する代わりに自分では、holographic 領域と音声のコンポーネントは、HolographicRemotingHelpers クラスから取得されます。

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Run メソッドの内部で、更新プログラムのループを使用する代わりに、デスクトップまたは UWP アプリのメイン ループからのティックの更新プログラムを提供します。 デスクトップやメッセージの処理のコントロール内に存続する UWP アプリで利用できます。

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Holographic アプリ ビューの Tick() メソッドは、更新、描画、存在するループの 1 つのイテレーションを完了します。

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

Holographic アプリ ビューを更新して、レンダリング、および存在のループはまったく同じときも HoloLens - で実行されているが、デスクトップ PC で量より多くのシステム リソースへのアクセスがあります。 多くの複数の三角形を表示、複数の描画パスがある、詳細物理学と x64 を使用してプロセスを必要とするコンテンツの読み込みに複数の 2 GB の RAM を実行できます。

### <a name="disconnect-and-end-the-remote-session"></a>切断して、リモート セッションを終了します。

-切断するための UI ボタンをクリックするなど、切断するには、HolographicStreamerHelpers で Disconnect() を呼び出すし、オブジェクトを解放します。

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

## <a name="get-the-remoting-player"></a>リモート処理のプレーヤーを取得します。

Windows Holographic のリモート処理 player は、リモート処理ホストのアプリに接続するためのエンドポイントとして、Windows アプリ ストアで提供されます。 Windows Holographic のリモート処理のプレーヤーを取得するには、HoloLens、リモート処理、検索から Windows アプリ ストアにアクセスし、アプリをダウンロードします。 リモート処理のプレーヤーには、リモート処理ホストのアプリをデバッグするときに役に立ちますが、画面上の統計情報を表示する機能が含まれています。

## <a name="notes-and-resources"></a>ノートとリソース

Holographic アプリ ビューからホログラフィック領域を初期化するために使用する必要があります、Direct3D デバイスを持つアプリを指定する方法の必要があります。 アプリは、この Direct3D デバイスを使用して、コピーして、プレビュー フレームを表示する必要があります。

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**コード サンプル:** Holographic のリモート処理の完全なコード サンプルは、リモート処理とリモート デスクトップの Win32、UWP の DirectX および XAML での UWP プロジェクトをホストと互換性がある holographic アプリケーション ビューが含まれています。 取得するには、ここで参照してください。
* [リモート処理用の Windows Holographic のコード サンプル](https://github.com/Microsoft/HoloLensCompanionKit/)

**デバッグに注意してください。** Holographic のリモート処理ライブラリでは、初回の例外をスローします。 これらの例外は、デバッグ時にアクティブになっている Visual Studio 例外設定によって、セッションで表示される可能性があります。 これらの例外は無視して Holographic のリモート処理ライブラリによって内部的にキャッチされます。
