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
# <a name="add-holographic-remoting"></a><span data-ttu-id="616e2-104">Holographic のリモート処理を追加します。</span><span class="sxs-lookup"><span data-stu-id="616e2-104">Add holographic remoting</span></span>

> [!NOTE]
> <span data-ttu-id="616e2-105">HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。</span><span class="sxs-lookup"><span data-stu-id="616e2-105">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="616e2-106">Holographic のリモート処理をデスクトップまたは UWP アプリに追加します。</span><span class="sxs-lookup"><span data-stu-id="616e2-106">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="616e2-107">このページには、デスクトップまたは UWP アプリに Holographic のリモート処理を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="616e2-107">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="616e2-108">Holographic のリモート処理により、アプリ、デスクトップ PC または Xbox One、多くのシステム リソースへのアクセス許可とにできるように統合リモートなどの UWP デバイスでホスト holographic のコンテンツを含む、HoloLens をターゲットに[没入型のビュー](app-views.md)に既存のデスクトップ PC のソフトウェア。</span><span class="sxs-lookup"><span data-stu-id="616e2-108">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="616e2-109">リモート処理ホストのアプリ、HoloLens から、入力データ ストリームを受信するには、仮想の没入型ビューでコンテンツをレンダリングおよびコンテンツ フレームは、HoloLens をストリームします。</span><span class="sxs-lookup"><span data-stu-id="616e2-109">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="616e2-110">標準の Wi-fi を使用して接続が確立します。</span><span class="sxs-lookup"><span data-stu-id="616e2-110">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="616e2-111">リモート処理を使用して、するには、NuGet パッケージを使用して、デスクトップまたは UWP アプリに holographic のリモート処理を追加し、接続を処理し、没入型のビューで表示するためにコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="616e2-111">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="616e2-112">デバイスの接続を処理するタスクを簡略化するコード サンプルでは、ヘルパー ライブラリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="616e2-112">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="616e2-113">一般的なリモート処理接続が 50 ミリ秒の待機時間と低い必要があります。</span><span class="sxs-lookup"><span data-stu-id="616e2-113">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="616e2-114">プレーヤー アプリは、リアルタイムでの待機時間を報告できます。</span><span class="sxs-lookup"><span data-stu-id="616e2-114">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="616e2-115">この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。</span><span class="sxs-lookup"><span data-stu-id="616e2-115">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="616e2-116">概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="616e2-116">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="616e2-117">NuGet パッケージのリモート処理の取得します。</span><span class="sxs-lookup"><span data-stu-id="616e2-117">Get the remoting NuGet packages</span></span>

<span data-ttu-id="616e2-118">Holographic のリモート処理用の NuGet パッケージを取得する次の手順に従ってし、プロジェクトからの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="616e2-118">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="616e2-119">Visual Studio でプロジェクトに移動します。</span><span class="sxs-lookup"><span data-stu-id="616e2-119">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="616e2-120">プロジェクト ノードを右クリックして**NuGet パッケージの管理.**</span><span class="sxs-lookup"><span data-stu-id="616e2-120">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="616e2-121">表示されるパネル で、**参照**し、「Holographic リモート処理」を検索します。</span><span class="sxs-lookup"><span data-stu-id="616e2-121">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="616e2-122">選択**Microsoft.Holographic.Remoting**クリック**インストール**します。</span><span class="sxs-lookup"><span data-stu-id="616e2-122">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="616e2-123">場合、**プレビュー**ダイアログが表示されたら、をクリックして**OK**します。</span><span class="sxs-lookup"><span data-stu-id="616e2-123">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="616e2-124">表示される次のダイアログ ボックスでは、使用許諾契約書です。</span><span class="sxs-lookup"><span data-stu-id="616e2-124">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="616e2-125">をクリックして**同意**ライセンス契約に同意します。</span><span class="sxs-lookup"><span data-stu-id="616e2-125">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="616e2-126">作成、HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="616e2-126">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="616e2-127">最初に、インスタンス HolographicStreamerHelpers の必要があります。</span><span class="sxs-lookup"><span data-stu-id="616e2-127">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="616e2-128">これは、リモート処理を処理するクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="616e2-128">Add this to the class that will be handling remoting.</span></span>

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="616e2-129">また、接続状態を追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="616e2-129">You'll also need to track connection state.</span></span> <span data-ttu-id="616e2-130">プレビューを表示する場合にコピーするテクスチャをする必要があります。</span><span class="sxs-lookup"><span data-stu-id="616e2-130">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="616e2-131">また、接続状態のロック、HoloLens の IP アドレスを格納する何らかの方法など、いくつかのものが必要し、など。</span><span class="sxs-lookup"><span data-stu-id="616e2-131">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="616e2-132">HolographicStreamerHelpers を初期化し、HoloLens への接続</span><span class="sxs-lookup"><span data-stu-id="616e2-132">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="616e2-133">HoloLens デバイスに接続するには、HolographicStreamerHelpers のインスタンスを作成し、ターゲット IP アドレスに接続します。</span><span class="sxs-lookup"><span data-stu-id="616e2-133">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="616e2-134">Holographic のリモート処理ライブラリが正確に一致するようにエンコーダーとデコーダーの解決策が必要ですので、HoloLens の表示幅と高さに合わせてビデオ フレーム サイズを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="616e2-134">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

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

<span data-ttu-id="616e2-135">デバイスの接続は非同期です。</span><span class="sxs-lookup"><span data-stu-id="616e2-135">The device connection is asynchronous.</span></span> <span data-ttu-id="616e2-136">Connect で、イベント ハンドラーを提供するアプリのニーズが接続解除、およびイベントをフレームに送信します。</span><span class="sxs-lookup"><span data-stu-id="616e2-136">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="616e2-137">OnConnected イベントは、UI を更新のレンダリングを開始および具合です。</span><span class="sxs-lookup"><span data-stu-id="616e2-137">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="616e2-138">デスクトップのコード サンプルで、「接続済み」のメッセージ ウィンドウのタイトルを更新します。</span><span class="sxs-lookup"><span data-stu-id="616e2-138">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="616e2-139">OnDisconnected イベントには、再接続や UI の更新を処理できます。</span><span class="sxs-lookup"><span data-stu-id="616e2-139">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="616e2-140">この例では、一時的な障害が発生した場合を再接続します。</span><span class="sxs-lookup"><span data-stu-id="616e2-140">In this example, we reconnect if there is a transient failure.</span></span>

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

<span data-ttu-id="616e2-141">リモート処理コンポーネントのフレームを送信する準備ができたら、アプリには、SendFrameEvent にそのコピーを作成する機会が提供されます。</span><span class="sxs-lookup"><span data-stu-id="616e2-141">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="616e2-142">ここでは、コピー、フレーム スワップ チェーンにプレビュー ウィンドウに表示されることができるようにします。</span><span class="sxs-lookup"><span data-stu-id="616e2-142">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

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

### <a name="render-holographic-content"></a><span data-ttu-id="616e2-143">Holographic のコンテンツをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="616e2-143">Render holographic content</span></span>

<span data-ttu-id="616e2-144">コンテンツを表示するためにリモート処理を使用して、デスクトップまたは UWP アプリ内で仮想 IFrameworkView を設定および処理するリモート処理から holographic フレーム。</span><span class="sxs-lookup"><span data-stu-id="616e2-144">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="616e2-145">すべての Windows Holographic Api と同じ方法で、このビューがわずかに異なる設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="616e2-145">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="616e2-146">を作成する代わりに自分では、holographic 領域と音声のコンポーネントは、HolographicRemotingHelpers クラスから取得されます。</span><span class="sxs-lookup"><span data-stu-id="616e2-146">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="616e2-147">Run メソッドの内部で、更新プログラムのループを使用する代わりに、デスクトップまたは UWP アプリのメイン ループからのティックの更新プログラムを提供します。</span><span class="sxs-lookup"><span data-stu-id="616e2-147">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="616e2-148">デスクトップやメッセージの処理のコントロール内に存続する UWP アプリで利用できます。</span><span class="sxs-lookup"><span data-stu-id="616e2-148">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="616e2-149">Holographic アプリ ビューの Tick() メソッドは、更新、描画、存在するループの 1 つのイテレーションを完了します。</span><span class="sxs-lookup"><span data-stu-id="616e2-149">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

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

<span data-ttu-id="616e2-150">Holographic アプリ ビューを更新して、レンダリング、および存在のループはまったく同じときも HoloLens - で実行されているが、デスクトップ PC で量より多くのシステム リソースへのアクセスがあります。</span><span class="sxs-lookup"><span data-stu-id="616e2-150">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="616e2-151">多くの複数の三角形を表示、複数の描画パスがある、詳細物理学と x64 を使用してプロセスを必要とするコンテンツの読み込みに複数の 2 GB の RAM を実行できます。</span><span class="sxs-lookup"><span data-stu-id="616e2-151">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="616e2-152">切断して、リモート セッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="616e2-152">Disconnect and end the remote session</span></span>

<span data-ttu-id="616e2-153">-切断するための UI ボタンをクリックするなど、切断するには、HolographicStreamerHelpers で Disconnect() を呼び出すし、オブジェクトを解放します。</span><span class="sxs-lookup"><span data-stu-id="616e2-153">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

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

## <a name="get-the-remoting-player"></a><span data-ttu-id="616e2-154">リモート処理のプレーヤーを取得します。</span><span class="sxs-lookup"><span data-stu-id="616e2-154">Get the remoting player</span></span>

<span data-ttu-id="616e2-155">Windows Holographic のリモート処理 player は、リモート処理ホストのアプリに接続するためのエンドポイントとして、Windows アプリ ストアで提供されます。</span><span class="sxs-lookup"><span data-stu-id="616e2-155">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="616e2-156">Windows Holographic のリモート処理のプレーヤーを取得するには、HoloLens、リモート処理、検索から Windows アプリ ストアにアクセスし、アプリをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="616e2-156">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="616e2-157">リモート処理のプレーヤーには、リモート処理ホストのアプリをデバッグするときに役に立ちますが、画面上の統計情報を表示する機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="616e2-157">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="616e2-158">ノートとリソース</span><span class="sxs-lookup"><span data-stu-id="616e2-158">Notes and resources</span></span>

<span data-ttu-id="616e2-159">Holographic アプリ ビューからホログラフィック領域を初期化するために使用する必要があります、Direct3D デバイスを持つアプリを指定する方法の必要があります。</span><span class="sxs-lookup"><span data-stu-id="616e2-159">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="616e2-160">アプリは、この Direct3D デバイスを使用して、コピーして、プレビュー フレームを表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="616e2-160">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="616e2-161">**コード サンプル:** Holographic のリモート処理の完全なコード サンプルは、リモート処理とリモート デスクトップの Win32、UWP の DirectX および XAML での UWP プロジェクトをホストと互換性がある holographic アプリケーション ビューが含まれています。</span><span class="sxs-lookup"><span data-stu-id="616e2-161">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="616e2-162">取得するには、ここで参照してください。</span><span class="sxs-lookup"><span data-stu-id="616e2-162">To get it, go here:</span></span>
* [<span data-ttu-id="616e2-163">リモート処理用の Windows Holographic のコード サンプル</span><span class="sxs-lookup"><span data-stu-id="616e2-163">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="616e2-164">**デバッグに注意してください。** Holographic のリモート処理ライブラリでは、初回の例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="616e2-164">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="616e2-165">これらの例外は、デバッグ時にアクティブになっている Visual Studio 例外設定によって、セッションで表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="616e2-165">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="616e2-166">これらの例外は無視して Holographic のリモート処理ライブラリによって内部的にキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="616e2-166">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
