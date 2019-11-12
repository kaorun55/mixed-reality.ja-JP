---
title: カスタム Holographic リモート処理プレーヤーの作成
description: カスタム Holographic リモート処理プレーヤーアプリを作成することにより、リモートコンピューター上にレンダリングされたコンテンツを HoloLens 2 に表示できるカスタムアプリケーションを作成できます。 この記事では、これを実現する方法について説明します。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: 1f8a0cbe0f6da88c0c5e5a695737d8694020635c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926655"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="0921d-105">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="0921d-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="0921d-106">このドキュメントでは、HoloLens 2 用のカスタムプレーヤーアプリケーションの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="0921d-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="0921d-107">HoloLens 2 向けに作成されたカスタムプレーヤーは、HoloLens 1 用に記述されたホストアプリケーションと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="0921d-107">Custom players written for HoloLens 2 are not compatible with host applications written for HoloLens 1.</span></span> <span data-ttu-id="0921d-108">これは、両方のアプリケーションが NuGet**パッケージバージョン 2.x**を使用する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0921d-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="0921d-109">カスタム Holographic リモート処理プレーヤーアプリを作成することにより、HoloLens 2 のリモートコンピューター上のから[イマーシブビュー](app-views.md)を表示できるカスタムアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0921d-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="0921d-110">この記事では、これを実現する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0921d-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="0921d-111">このページのすべてのコードと作業中のプロジェクトは、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)にあります。</span><span class="sxs-lookup"><span data-stu-id="0921d-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="0921d-112">Holographic リモート処理プレーヤーを使用すると、アプリは、デスクトップ PC または、Xbox One などの UWP デバイスで[レンダリング](rendering.md)された Holographic コンテンツを表示して、より多くのシステムリソースにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="0921d-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="0921d-113">Holographic Remoting player アプリは、入力データを Holographic Remoting ホストアプリケーションにストリームし、ビデオとオーディオストリームとしてイマーシブビューを受信します。</span><span class="sxs-lookup"><span data-stu-id="0921d-113">A Holographic Remoting player app streams input data to a Holographic Remoting host application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="0921d-114">接続は標準の Wi-fi を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="0921d-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="0921d-115">プレーヤーアプリを作成するには、NuGet パッケージを使用して Holographic Remoting を UWP アプリに追加し、接続を処理し、イマーシブビューを表示するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="0921d-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="0921d-116">前提条件</span><span class="sxs-lookup"><span data-stu-id="0921d-116">Prerequisites</span></span>

<span data-ttu-id="0921d-117">開始点としては、既に Windows Mixed Reality API を対象としている、動作する DirectX ベースの UWP アプリを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0921d-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="0921d-118">詳細については、「 [DirectX 開発の概要](directx-development-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0921d-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="0921d-119">既存のアプリがなく、ゼロから開始する場合は、 [ C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0921d-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="0921d-120">Holographic リモート処理を使用するすべてのアプリは、[マルチスレッドアパートメント](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)を使用するように作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0921d-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="0921d-121">[シングルスレッドのアパートメント](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments)使用はサポートされていますが、パフォーマンスが低下し、再生中に途切れが生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0921d-121">The use of a [single-threaded appartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="0921d-122">/Winrt C++ [winrt:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started)使用すると、マルチスレッドアパートメントが既定値になります。</span><span class="sxs-lookup"><span data-stu-id="0921d-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="0921d-123">Holographic リモート処理 NuGet パッケージを取得する</span><span class="sxs-lookup"><span data-stu-id="0921d-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="0921d-124">Visual Studio で NuGet パッケージをプロジェクトに追加するには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0921d-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="0921d-125">Visual Studio でプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="0921d-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="0921d-126">プロジェクトノードを右クリックし、 **[NuGet パッケージの管理...]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0921d-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="0921d-127">表示されるパネルで、 **[参照]** をクリックし、"Holographic Remoting" を検索します。</span><span class="sxs-lookup"><span data-stu-id="0921d-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="0921d-128">**[Holographic]** を選択し **、最新の**2.x バージョンを選択して **[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0921d-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="0921d-129">**[プレビュー]** ダイアログが表示されたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0921d-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="0921d-130">次に表示されるダイアログは、使用許諾契約書です。</span><span class="sxs-lookup"><span data-stu-id="0921d-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="0921d-131">[**同意**する] をクリックして、使用許諾契約書に同意します。</span><span class="sxs-lookup"><span data-stu-id="0921d-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="0921d-132">NuGet パッケージ内の ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` には、Holographic Remoting によって公開される API に関する詳細なドキュメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0921d-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="0921d-133">アプリケーションの package.appxmanifest を変更する</span><span class="sxs-lookup"><span data-stu-id="0921d-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="0921d-134">NuGet パッケージによって追加された Holographic をアプリケーションに認識させるには、プロジェクトで次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0921d-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="0921d-135">ソリューションエクスプローラーで**package.appxmanifest**ファイルを右クリックし、 **[プログラムから開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0921d-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="0921d-136">**XML (テキスト) エディター**を選択し、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0921d-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="0921d-137">次の行をファイルに追加して保存します。</span><span class="sxs-lookup"><span data-stu-id="0921d-137">Add the following lines to the file and save</span></span>
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
## <a name="create-the-player-context"></a><span data-ttu-id="0921d-138">プレーヤーのコンテキストを作成する</span><span class="sxs-lookup"><span data-stu-id="0921d-138">Create the player context</span></span>

<span data-ttu-id="0921d-139">最初の手順として、アプリケーションでプレーヤーコンテキストを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0921d-139">As a first step the application should create a player context.</span></span>

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
><span data-ttu-id="0921d-140">Holographic リモート処理は、Windows の一部である Windows Mixed Reality ランタイムをリモート処理固有のランタイムに置き換えることによって機能します。</span><span class="sxs-lookup"><span data-stu-id="0921d-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="0921d-141">これは、プレーヤーのコンテキストの作成時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="0921d-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="0921d-142">そのため、プレーヤーコンテキストを作成する前に Windows Mixed Reality API を呼び出すと、予期しない動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0921d-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="0921d-143">推奨される方法は、任意の混合 Reality API と対話する前に、可能な限り早くプレーヤーコンテキストを作成することです。</span><span class="sxs-lookup"><span data-stu-id="0921d-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="0921d-144">Windows Mixed Reality API を使用して作成または取得したオブジェクトを、を呼び出す前に、その後に作成または取得したオブジェクトに ```PlayerContext::Create()``` 混在させないでください。</span><span class="sxs-lookup"><span data-stu-id="0921d-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create()``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="0921d-145">次に、 [HolographicSpace](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)を呼び出して、HolographicSpace を作成します。</span><span class="sxs-lookup"><span data-stu-id="0921d-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a><span data-ttu-id="0921d-146">ホストに接続する</span><span class="sxs-lookup"><span data-stu-id="0921d-146">Connect to the host</span></span>

<span data-ttu-id="0921d-147">プレーヤーアプリがコンテンツを表示できる状態になったら、ホストへの接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="0921d-147">Once the player app is ready for rendering content a connection to the host can be established.</span></span>

<span data-ttu-id="0921d-148">接続は、次のいずれかの方法で確立できます。</span><span class="sxs-lookup"><span data-stu-id="0921d-148">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="0921d-149">HoloLens 2 で実行されているプレーヤーアプリは、ホストアプリに接続します。</span><span class="sxs-lookup"><span data-stu-id="0921d-149">The player app running on HoloLens 2 connects to the host app.</span></span>
2) <span data-ttu-id="0921d-150">ホストアプリは、HoloLens 2 で実行されているプレーヤーアプリに接続します。</span><span class="sxs-lookup"><span data-stu-id="0921d-150">The host app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="0921d-151">プレーヤーアプリからホストに接続するには、プレーヤーコンテキストでホスト名とポートを指定して ```Connect``` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0921d-151">To connect from the player app to the host call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="0921d-152">既定のポートは**8265**です。</span><span class="sxs-lookup"><span data-stu-id="0921d-152">The default port is **8265**.</span></span>

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
><span data-ttu-id="0921d-153">すべてC++の/winrt API ```Connect``` は、処理する必要がある WinRT:: hresult_error をスローすることがあります。</span><span class="sxs-lookup"><span data-stu-id="0921d-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="0921d-154">プレーヤーアプリで着信接続をリッスンするには、```Listen``` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0921d-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="0921d-155">この呼び出しでは、ハンドシェイクポートとトランスポートポートの両方を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0921d-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="0921d-156">ハンドシェイクポートは、初期ハンドシェイクに使用されます。</span><span class="sxs-lookup"><span data-stu-id="0921d-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="0921d-157">データは、トランスポートポートを介して送信されます。</span><span class="sxs-lookup"><span data-stu-id="0921d-157">The data is then send over the transport port.</span></span> <span data-ttu-id="0921d-158">既定では、ポート番号**8265**と**8266**が使用されます。</span><span class="sxs-lookup"><span data-stu-id="0921d-158">By default port number **8265** and **8266** are used.</span></span>

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


## <a name="handling-connection-related-events"></a><span data-ttu-id="0921d-159">接続関連のイベントの処理</span><span class="sxs-lookup"><span data-stu-id="0921d-159">Handling connection related events</span></span>

<span data-ttu-id="0921d-160">この ```PlayerContext``` は、接続の状態を監視するために3つのイベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="0921d-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="0921d-161">OnConnected: ホストへの接続が正常に確立されたときにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="0921d-161">OnConnected: Triggered when a connection to the host has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="0921d-162">OnDisconnected: 確立された接続が終了した場合、または接続を確立できなかった場合にトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="0921d-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
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
><span data-ttu-id="0921d-163">使用可能な ```ConnectionFailureReason``` 値は、```Microsoft.Holographic.AppRemoting.idl```[ファイル](#idl)に記載されています。</span><span class="sxs-lookup"><span data-stu-id="0921d-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="0921d-164">OnListening: 受信接続のリッスンが開始されます。</span><span class="sxs-lookup"><span data-stu-id="0921d-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="0921d-165">さらに、プレーヤーのコンテキストで ```ConnectionState``` プロパティを使用して接続状態を照会することもできます。</span><span class="sxs-lookup"><span data-stu-id="0921d-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="0921d-166">リモートで描画されたフレームを表示する</span><span class="sxs-lookup"><span data-stu-id="0921d-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="0921d-167">リモートでレンダリングされるコンテンツを表示するには、 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)のレンダリング中に ```PlayerContext::BlitRemoteFrame()``` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0921d-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame()``` while rendering a [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="0921d-168">```BlitRemoteFrame()``` では、現在の HolographicFrame のバックバッファーがレンダーターゲットとしてバインドされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0921d-168">```BlitRemoteFrame()``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="0921d-169">バックバッファーは、 [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)プロパティを介して[HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)から受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="0921d-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="0921d-170">```BlitRemoteFrame()``` 呼び出されると、ホストアプリケーションから最後に受信したフレームが HolographicFrame の BackBuffer にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="0921d-170">When called, ```BlitRemoteFrame()``` copies the latest received frame from the host application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="0921d-171">さらに、リモートアプリケーションがリモートフレームのレンダリング中にフォーカスポイントを指定している場合は、フォーカスポイントが設定されます。</span><span class="sxs-lookup"><span data-stu-id="0921d-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="0921d-172">```PlayerContext::BlitRemoteFrame()``` により、現在のフレームのフォーカスポイントが上書きされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0921d-172">```PlayerContext::BlitRemoteFrame()``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="0921d-173">フォールバックフォーカスポイントを指定するには、```PlayerContext::BlitRemoteFrame()```する前に[HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0921d-173">To specify a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame()```.</span></span> 
>- <span data-ttu-id="0921d-174">リモートフォーカスポイントを上書きするには、```PlayerContext::BlitRemoteFrame()```後に[HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0921d-174">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame()```.</span></span>

<span data-ttu-id="0921d-175">成功した場合、```BlitRemoteFrame()``` は ```BlitResult::Success_Color```を返します。</span><span class="sxs-lookup"><span data-stu-id="0921d-175">On success, ```BlitRemoteFrame()``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="0921d-176">それ以外の場合は、エラーの理由を返します。</span><span class="sxs-lookup"><span data-stu-id="0921d-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="0921d-177">```BlitResult::Failed_NoRemoteFrameAvailable```: 使用可能なリモートフレームがないため、失敗しました。</span><span class="sxs-lookup"><span data-stu-id="0921d-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="0921d-178">```BlitResult::Failed_NoCamera```: カメラが存在しないために失敗しました。</span><span class="sxs-lookup"><span data-stu-id="0921d-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="0921d-179">```BlitResult::Failed_RemoteFrameTooOld```: リモートフレームが古すぎるため失敗しました (PlayerContext:: BlitRemoteFrameTimeout プロパティを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="0921d-179">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

## <span data-ttu-id="0921d-180">省略可能: Set BlitRemoteFrameTimeout<a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="0921d-180">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="0921d-181">```PlayerContext::BlitRemoteFrameTimeout``` は、バージョン[2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0921d-181">```PlayerContext::BlitRemoteFrameTimeout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="0921d-182">```PlayerContext::BlitRemoteFrameTimeout``` プロパティは、新しいリモートフレームが受信されなかった場合に、リモートフレームが再利用される時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="0921d-182">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="0921d-183">一般的なユースケースでは、一定の時間、新しいフレームが受信されなかった場合に、BlitRemoteFrame timeout で空の画面が表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="0921d-183">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="0921d-184">有効にすると、```BlitRemoteFrame``` メソッドの戻り値の型を使用して、ローカルに表示されるフォールバックコンテンツに切り替えることもできます。</span><span class="sxs-lookup"><span data-stu-id="0921d-184">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="0921d-185">タイムアウトを有効にするには、プロパティ値を100ミリ秒以上の期間に設定します。</span><span class="sxs-lookup"><span data-stu-id="0921d-185">To enable the timeout, set the property value to a duration equal or greater than 100ms.</span></span> <span data-ttu-id="0921d-186">タイムアウトを無効にするには、プロパティをゼロ期間に設定します。</span><span class="sxs-lookup"><span data-stu-id="0921d-186">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="0921d-187">タイムアウトが有効になっていて、設定した期間にリモートフレームを受信しなかった場合、BlitRemoteFrame は失敗し、新しいリモートフレームが受信されるまで ```Failed_RemoteFrameTooOld``` が返されます。</span><span class="sxs-lookup"><span data-stu-id="0921d-187">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="0921d-188">省略可能: 最後のリモートフレームに関する統計を取得する</span><span class="sxs-lookup"><span data-stu-id="0921d-188">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="0921d-189">パフォーマンスまたはネットワークの問題を診断するには、```PlayerContext::LastFrameStatistics``` プロパティを使用して最後のリモートフレームに関する統計情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="0921d-189">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="0921d-190">統計は[HolographicFrame::P](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)の呼び出し中に更新されます。 current予測。</span><span class="sxs-lookup"><span data-stu-id="0921d-190">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="0921d-191">詳細については、```Microsoft.Holographic.AppRemoting.idl```[ファイル](#idl)の ```PlayerFrameStatistics``` のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0921d-191">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="0921d-192">省略可能: カスタムデータチャネル</span><span class="sxs-lookup"><span data-stu-id="0921d-192">Optional: Custom data channels</span></span>

<span data-ttu-id="0921d-193">カスタムデータチャネルは、既に確立されているリモート処理接続を介してユーザーデータを送信するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="0921d-193">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="0921d-194">詳細については、「[カスタムデータチャネル](holographic-remoting-custom-data-channels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0921d-194">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="0921d-195">参照</span><span class="sxs-lookup"><span data-stu-id="0921d-195">See Also</span></span>
* [<span data-ttu-id="0921d-196">Holographic Remoting ホストアプリの作成</span><span class="sxs-lookup"><span data-stu-id="0921d-196">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="0921d-197">カスタムの Holographic Remoting データ チャネル</span><span class="sxs-lookup"><span data-stu-id="0921d-197">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="0921d-198">Holographic Remoting を使用したセキュリティで保護された接続の確立</span><span class="sxs-lookup"><span data-stu-id="0921d-198">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="0921d-199">Holographic リモート処理のトラブルシューティングと制限事項</span><span class="sxs-lookup"><span data-stu-id="0921d-199">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="0921d-200">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="0921d-200">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="0921d-201">Microsoft のプライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="0921d-201">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
