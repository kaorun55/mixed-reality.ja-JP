---
title: Holographic Remoting ホストアプリの作成
description: リモートコンピューター上にレンダリングされる Holographic Remoting host アプリのリモートコンテンツを作成することによって、HoloLens 2 にストリーミングできます。 この記事では、これを実現する方法について説明します。
author: bethau
ms.author: bethau
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: 6b0f92fce1099ec98d87100e015de9442bff6bd2
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122031"
---
# <a name="writing-a-holographic-remoting-host-app"></a><span data-ttu-id="a8afd-105">Holographic Remoting ホストアプリの作成</span><span class="sxs-lookup"><span data-stu-id="a8afd-105">Writing a Holographic Remoting host app</span></span>

>[!IMPORTANT]
><span data-ttu-id="a8afd-106">このドキュメントでは、HoloLens 2 用のホストアプリケーションの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-106">This document describes the creation of a host application for HoloLens 2.</span></span> <span data-ttu-id="a8afd-107">HoloLens のホストアプリケーション **(第1世代)** では、NuGetパッケージバージョン1.x を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8afd-107">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="a8afd-108">これは、HoloLens 2 用に作成されたホストアプリケーションが HoloLens 1 と互換性がないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-108">This implies that host applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="a8afd-109">HoloLens 1 のドキュメントについては、[こちら](add-holographic-remoting.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8afd-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="a8afd-110">Holographic リモート処理ホストアプリケーションを作成することにより、リモートコンピューター上にレンダリングされるリモートコンテンツを HoloLens 2 にストリーミングできます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-110">By creating a Holographic Remoting host app remote content that is rendered on a remote machine can be streamed to HoloLens 2.</span></span> <span data-ttu-id="a8afd-111">この記事では、これを実現する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="a8afd-112">このページのすべてのコードと作業中のプロジェクトは、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)にあります。</span><span class="sxs-lookup"><span data-stu-id="a8afd-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="a8afd-113">Holographic リモート処理を使用すると、アプリは、デスクトップ PC 上でホストされている Holographic コンテンツ、または Xbox One などの UWP デバイスで、HoloLens 2 をターゲットにすることができます。これにより、より多くのシステムリソースにアクセスし、リモートの[イマーシブビュー](app-views.md)を既存のものに統合することが可能になります。デスクトップ PC ソフトウェア。</span><span class="sxs-lookup"><span data-stu-id="a8afd-113">Holographic remoting allows an app to target HoloLens 2 with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="a8afd-114">リモートホストアプリは HoloLens 2 から入力データストリームを受け取り、仮想イマーシブビューでコンテンツをレンダリングし、コンテンツフレームを HoloLens 2 にストリームバックします。</span><span class="sxs-lookup"><span data-stu-id="a8afd-114">A remoting host app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="a8afd-115">接続は標準の Wi-fi を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="a8afd-116">Holographic リモート処理は、NuGet パケット経由でデスクトップまたは UWP アプリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="a8afd-117">接続を処理し、イマーシブビューでレンダリングする追加のコードが必要です。</span><span class="sxs-lookup"><span data-stu-id="a8afd-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="a8afd-118">一般的なリモート処理接続では、待機時間が50ミリ秒に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="a8afd-119">プレーヤーアプリは、リアルタイムで待機時間を報告できます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8afd-120">前提条件</span><span class="sxs-lookup"><span data-stu-id="a8afd-120">Prerequisites</span></span>

<span data-ttu-id="a8afd-121">開始点として、Windows Mixed Reality API を対象とする、動作する DirectX ベースのデスクトップまたは UWP アプリを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a8afd-121">A good starting point is a working DirectX based Desktop or UWP app which targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="a8afd-122">詳細については、「 [DirectX 開発の概要](directx-development-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8afd-122">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="a8afd-123">[ C++ Holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)は、出発点として適しています。</span><span class="sxs-lookup"><span data-stu-id="a8afd-123">The [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="a8afd-124">Holographic リモート処理を使用するすべてのアプリは、[マルチスレッドアパートメント](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)を使用するように作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8afd-124">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="a8afd-125">[シングルスレッドアパートメント](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments)の使用はサポートされていますが、パフォーマンスが低下し、再生中に途切れが生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a8afd-125">The use of a [single-threaded apartment](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="a8afd-126">/Winrt C++ [winrt:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started)を使用すると、マルチスレッドアパートメントが既定値になります。</span><span class="sxs-lookup"><span data-stu-id="a8afd-126">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="a8afd-127">Holographic リモート処理 NuGet パッケージを取得する</span><span class="sxs-lookup"><span data-stu-id="a8afd-127">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="a8afd-128">Visual Studio で NuGet パッケージをプロジェクトに追加するには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8afd-128">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="a8afd-129">Visual Studio でプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-129">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="a8afd-130">プロジェクトノードを右クリックし、 **[NuGet パッケージの管理...]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-130">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="a8afd-131">表示されるパネルで、 **[参照]** をクリックし、"Holographic Remoting" を検索します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-131">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="a8afd-132">**[Holographic]** を選択し、最新の2.x バージョンを選択して **[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8afd-132">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="a8afd-133">**[プレビュー]** ダイアログが表示されたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8afd-133">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="a8afd-134">次に表示されるダイアログは、使用許諾契約書です。</span><span class="sxs-lookup"><span data-stu-id="a8afd-134">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="a8afd-135">[**同意**する] をクリックして、使用許諾契約書に同意します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-135">Click on **I Accept** to accept the license agreement.</span></span>

>[!NOTE]
><span data-ttu-id="a8afd-136">HoloLens 1 を対象とする開発者は、NuGet パッケージのバージョン1.x を引き続き利用できます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="a8afd-137">詳細については、「 [Add Holographic Remoting (HoloLens (第1世代))](add-holographic-remoting.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8afd-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="a8afd-138">リモートコンテキストを作成する</span><span class="sxs-lookup"><span data-stu-id="a8afd-138">Create the remote context</span></span>

<span data-ttu-id="a8afd-139">最初の手順として、アプリケーションでリモートコンテキストを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8afd-139">As a first step the application should create a remote context.</span></span>

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
><span data-ttu-id="a8afd-140">Holographic リモート処理は、Windows の一部である Windows Mixed Reality ランタイムをリモート処理固有のランタイムに置き換えることによって機能します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="a8afd-141">これは、リモートコンテキストの作成時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-141">This is done during the creation of the remote context.</span></span> <span data-ttu-id="a8afd-142">そのため、リモートコンテキストを作成する前に Windows Mixed Reality API を呼び出すと、予期しない動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a8afd-142">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="a8afd-143">推奨される方法は、混合の現実 API と対話する前に、できるだけ早くリモートコンテキストを作成することです。</span><span class="sxs-lookup"><span data-stu-id="a8afd-143">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="a8afd-144">Windows Mixed Reality API を使用して作成または取得したオブジェクトを、後で作成または取得したオブジェクトと共に使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="a8afd-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="a8afd-145">次に、holographic 領域を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8afd-145">Next the holographic space needs to be created.</span></span> <span data-ttu-id="a8afd-146">CoreWindow の指定は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="a8afd-146">Specifying a CoreWindow is not required.</span></span> <span data-ttu-id="a8afd-147">CoreWindow を持たないデスクトップアプリは、のみを```nullptr```渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-147">Desktop apps that do not have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="a8afd-148">デバイスへの接続</span><span class="sxs-lookup"><span data-stu-id="a8afd-148">Connect to the device</span></span>

<span data-ttu-id="a8afd-149">ホストアプリがコンテンツをレンダリングする準備ができたら、デバイスへの接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-149">Once the host app is ready for rendering content a connection to the device can be established.</span></span>

<span data-ttu-id="a8afd-150">接続は、次の2つの方法のいずれかで実行できます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-150">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="a8afd-151">ホストアプリは、デバイスで実行されているプレーヤーに接続します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-151">The host app connects to the player running on the device.</span></span>
2) <span data-ttu-id="a8afd-152">デバイスで実行されているプレーヤーは、ホストアプリに接続します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-152">The player running on the device connects to the host app.</span></span>

<span data-ttu-id="a8afd-153">ホストアプリから HoloLens 2 への接続を確立するには```Connect``` 、ホスト名とポートを指定して、リモートコンテキストでメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-153">To establish a connection from the host app to HoloLens 2 call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="a8afd-154">Holographic リモート処理プレーヤーによって使用されるポートは**8265**です。</span><span class="sxs-lookup"><span data-stu-id="a8afd-154">The port used by the Holographic Remoting Player is **8265**.</span></span>

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
><span data-ttu-id="a8afd-155">任意C++の/winrt API ```Connect```と同様に、処理する必要がある winrt:: hresult_error をスローする場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8afd-155">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="a8afd-156">[ C++/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/)言語のプロジェクションを使用しない```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h```ようにするには、Holographic リモート処理 NuGet パッケージ内にあるファイルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-156">To avoid using [C++/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="a8afd-157">これには、基になる COM インターフェイスの宣言が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-157">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="a8afd-158">ただし、 C++/WinRT を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a8afd-158">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="a8afd-159">ホストアプリでの着信接続のリッスンは、 ```Listen```メソッドを呼び出すことによって行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-159">Listening for incoming connections on the host app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="a8afd-160">この呼び出しでは、ハンドシェイクポートとトランスポートポートの両方を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-160">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="a8afd-161">ハンドシェイクポートは、初期ハンドシェイクに使用されます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-161">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="a8afd-162">データは、トランスポートポートを介して送信されます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-162">The data is then send over the transport port.</span></span> <span data-ttu-id="a8afd-163">既定では、 **8265**および**8266**が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-163">By default **8265** and **8266** are used.</span></span>

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
><span data-ttu-id="a8afd-164">NuGet ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```パッケージ内には、Holographic Remoting によって公開される API に関する詳細なドキュメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a8afd-164">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="a8afd-165">リモート処理固有のイベントの処理</span><span class="sxs-lookup"><span data-stu-id="a8afd-165">Handling Remoting specific events</span></span>

<span data-ttu-id="a8afd-166">リモートコンテキストは、接続の状態を監視するために重要な3つのイベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-166">The remote context exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="a8afd-167">OnConnected:デバイスへの接続が正常に確立されたときにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-167">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="a8afd-168">OnDisconnected:確立された接続が閉じられた場合、または接続が確立できなかった場合にトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-168">OnDisconnected: Triggered if an established connection is closed or a connection could not be established.</span></span>
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
3) <span data-ttu-id="a8afd-169">OnListening:受信接続のリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-169">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="a8afd-170">さらに、リモートコンテキストの```ConnectionState```プロパティを使用して接続状態を照会することもできます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-170">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="a8afd-171">音声イベントの処理</span><span class="sxs-lookup"><span data-stu-id="a8afd-171">Handling speech events</span></span>

<span data-ttu-id="a8afd-172">リモート音声インターフェイスを使用すると、音声トリガーを HoloLens 2 に登録し、それらをホストアプリケーションにリモート処理することができます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-172">Using the remote speech interface it is possible to register speech triggers with HoloLens 2 and have them remoted to the host application.</span></span>

<span data-ttu-id="a8afd-173">この追加のメンバーは、リモート音声の状態を追跡するために必要です。</span><span class="sxs-lookup"><span data-stu-id="a8afd-173">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="a8afd-174">まず、リモート音声インターフェイスを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8afd-174">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="a8afd-175">非同期ヘルパーメソッドを使用すると、リモート音声を初期化できます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-175">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="a8afd-176">初期化にはかなりの時間がかかる場合があるため、非同期的に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8afd-176">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="a8afd-177">[/WinRT を使用しC++た同時実行と非同期操作](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)では、 C++/winrtを使用して非同期関数を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-177">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

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

<span data-ttu-id="a8afd-178">認識する語句を指定する方法は2つあります。</span><span class="sxs-lookup"><span data-stu-id="a8afd-178">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="a8afd-179">音声文法 xml ファイル内の仕様。</span><span class="sxs-lookup"><span data-stu-id="a8afd-179">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="a8afd-180">詳細について[は、「基本的な XML 文法を作成する方法](https://docs.microsoft.com/en-us/previous-versions/office/developer/speech-technologies/hh361658(v=office.14))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8afd-180">See [How to create a basic XML Grammar](https://docs.microsoft.com/en-us/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="a8afd-181">を指定するには、をディクショナリベクター ```ApplyParameters```内に渡します。</span><span class="sxs-lookup"><span data-stu-id="a8afd-181">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="a8afd-182">On認識された音声コールバック内で、音声イベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-182">Inside the OnRecognizedSpeech callback the speech events can then be processed:</span></span>

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

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="a8afd-183">ストリーミングされるコンテンツをローカルでプレビューする</span><span class="sxs-lookup"><span data-stu-id="a8afd-183">Preview streamed content locally</span></span>

<span data-ttu-id="a8afd-184">デバイスに送信されるホストアプリで同じコンテンツを表示するには、 ```OnSendFrame```リモートコンテキストのイベントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-184">To display the same content in the host app that is send to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="a8afd-185">```OnSendFrame```イベントは、Holographic リモート処理ライブラリが現在のフレームをリモートデバイスに送信するたびにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-185">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="a8afd-186">これは、コンテンツを撮影し、デスクトップや UWP ウィンドウに array.blit するのに最適な時間です。</span><span class="sxs-lookup"><span data-stu-id="a8afd-186">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

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

## <a name="optional-custom-data-channels"></a><span data-ttu-id="a8afd-187">省略可能: カスタムデータチャネル</span><span class="sxs-lookup"><span data-stu-id="a8afd-187">Optional: Custom data channels</span></span>

<span data-ttu-id="a8afd-188">カスタムデータチャネルは、既に確立されているリモート処理接続を介してユーザーデータを送信するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8afd-188">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="a8afd-189">詳細については、「[カスタムデータチャネル](holographic-remoting-custom-data-channels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8afd-189">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8afd-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8afd-190">See Also</span></span>
* [<span data-ttu-id="a8afd-191">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="a8afd-191">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="a8afd-192">カスタムの Holographic Remoting データ チャネル</span><span class="sxs-lookup"><span data-stu-id="a8afd-192">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="a8afd-193">Holographic Remoting を使用したセキュリティで保護された接続の確立</span><span class="sxs-lookup"><span data-stu-id="a8afd-193">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="a8afd-194">Holographic リモート処理のトラブルシューティングと制限事項</span><span class="sxs-lookup"><span data-stu-id="a8afd-194">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="a8afd-195">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="a8afd-195">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="a8afd-196">Microsoft のプライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="a8afd-196">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
