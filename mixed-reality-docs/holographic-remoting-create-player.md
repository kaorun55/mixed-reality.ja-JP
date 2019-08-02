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
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="e2c4f-105">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="e2c4f-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="e2c4f-106">このドキュメントでは、HoloLens 2 用のカスタムプレーヤーアプリケーションの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="e2c4f-107">HoloLens 2 向けに作成されたカスタムプレーヤーは、HoloLens 1 用に記述されたホストアプリケーションと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-107">Custom players written for HoloLens 2 are not compatible with host applications written for HoloLens 1.</span></span> <span data-ttu-id="e2c4f-108">これは、両方のアプリケーションが NuGet**パッケージバージョン 2.x**を使用する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="e2c4f-109">カスタム Holographic リモート処理プレーヤーアプリを作成することにより、HoloLens 2 のリモートコンピューター上のから[イマーシブビュー](app-views.md)を表示できるカスタムアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="e2c4f-110">この記事では、これを実現する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="e2c4f-111">このページのすべてのコードと作業中のプロジェクトは、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)にあります。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="e2c4f-112">Holographic リモート処理プレーヤーを使用すると、アプリは、デスクトップ PC または、Xbox One などの UWP デバイスで[レンダリング](rendering.md)された Holographic コンテンツを表示して、より多くのシステムリソースにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="e2c4f-113">Holographic Remoting player アプリは、入力データを Holographic Remoting ホストアプリケーションにストリームし、ビデオとオーディオストリームとしてイマーシブビューを受信します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-113">A Holographic Remoting player app streams input data to a Holographic Remoting host application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="e2c4f-114">接続は標準の Wi-fi を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="e2c4f-115">プレーヤーアプリを作成するには、NuGet パッケージを使用して Holographic Remoting を UWP アプリに追加し、接続を処理し、イマーシブビューを表示するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="e2c4f-116">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e2c4f-116">Prerequisites</span></span>

<span data-ttu-id="e2c4f-117">開始点としては、既に Windows Mixed Reality API を対象としている、動作する DirectX ベースの UWP アプリを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="e2c4f-118">詳細については、「 [DirectX 開発の概要](directx-development-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="e2c4f-119">既存のアプリがなく、ゼロから開始する場合は、 [ C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e2c4f-120">Holographic リモート処理を使用するすべてのアプリは、[マルチスレッドアパートメント](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)を使用するように作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="e2c4f-121">[シングルスレッドのアパートメント](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments)使用はサポートされていますが、パフォーマンスが低下し、再生中に途切れが生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-121">The use of a [single-threaded appartment](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="e2c4f-122">/Winrt C++ [winrt:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started)を使用すると、マルチスレッドアパートメントが既定値になります。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="e2c4f-123">Holographic リモート処理 NuGet パッケージを取得する</span><span class="sxs-lookup"><span data-stu-id="e2c4f-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="e2c4f-124">Visual Studio で NuGet パッケージをプロジェクトに追加するには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="e2c4f-125">Visual Studio でプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="e2c4f-126">プロジェクトノードを右クリックし、 **[NuGet パッケージの管理...]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="e2c4f-127">表示されるパネルで、 **[参照]** をクリックし、"Holographic Remoting" を検索します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="e2c4f-128">**[Holographic]** を選択し **、最新の**2.x バージョンを選択して **[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="e2c4f-129">**[プレビュー]** ダイアログが表示されたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="e2c4f-130">次に表示されるダイアログは、使用許諾契約書です。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="e2c4f-131">[**同意**する] をクリックして、使用許諾契約書に同意します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="e2c4f-132">NuGet ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```パッケージ内には、Holographic Remoting によって公開される API に関する詳細なドキュメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="e2c4f-133">アプリケーションの package.appxmanifest を変更する</span><span class="sxs-lookup"><span data-stu-id="e2c4f-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="e2c4f-134">NuGet パッケージによって追加された Holographic をアプリケーションに認識させるには、プロジェクトで次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="e2c4f-135">ソリューションエクスプローラーで**package.appxmanifest**ファイルを右クリックし、 **[プログラムから開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="e2c4f-136">**XML (テキスト) エディター**を選択し、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="e2c4f-137">次の行をファイルに追加して保存します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-137">Add the following lines to the file and save</span></span>
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
## <a name="create-the-player-context"></a><span data-ttu-id="e2c4f-138">プレーヤーのコンテキストを作成する</span><span class="sxs-lookup"><span data-stu-id="e2c4f-138">Create the player context</span></span>

<span data-ttu-id="e2c4f-139">最初の手順として、アプリケーションでプレーヤーコンテキストを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-139">As a first step the application should create a player context.</span></span>

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
><span data-ttu-id="e2c4f-140">Holographic リモート処理は、Windows の一部である Windows Mixed Reality ランタイムをリモート処理固有のランタイムに置き換えることによって機能します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="e2c4f-141">これは、プレーヤーのコンテキストの作成時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="e2c4f-142">そのため、プレーヤーコンテキストを作成する前に Windows Mixed Reality API を呼び出すと、予期しない動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="e2c4f-143">推奨される方法は、任意の混合 Reality API と対話する前に、可能な限り早くプレーヤーコンテキストを作成することです。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="e2c4f-144">Windows Mixed Reality API を使用して作成または取得したオブジェクトを```PlayerContext::Create()``` 、後で作成または取得したオブジェクトで混在させないでください。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create()``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="e2c4f-145">次に、 [HolographicSpace](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)を呼び出して、HolographicSpace を作成します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a><span data-ttu-id="e2c4f-146">ホストに接続する</span><span class="sxs-lookup"><span data-stu-id="e2c4f-146">Connect to the host</span></span>

<span data-ttu-id="e2c4f-147">プレーヤーアプリがコンテンツを表示できる状態になったら、ホストへの接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-147">Once the player app is ready for rendering content a connection to the host can be established.</span></span>

<span data-ttu-id="e2c4f-148">接続は、次のいずれかの方法で確立できます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-148">The connection can be established in one of the follwing ways:</span></span>
1) <span data-ttu-id="e2c4f-149">HoloLens 2 で実行されているプレーヤーアプリは、ホストアプリに接続します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-149">The player app running on HoloLens 2 connects to the host app.</span></span>
2) <span data-ttu-id="e2c4f-150">ホストアプリは、HoloLens 2 で実行されているプレーヤーアプリに接続します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-150">The host app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="e2c4f-151">プレーヤーアプリからホストに接続するには、プレーヤー ```Connect```コンテキストでホスト名とポートを指定してメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-151">To connect from the player app to the host call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="e2c4f-152">既定のポートは**8265**です。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-152">The default port is **8265**.</span></span>

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
><span data-ttu-id="e2c4f-153">任意C++の/winrt API ```Connect```と同様に、処理する必要がある winrt:: hresult_error をスローする場合があります。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="e2c4f-154">プレーヤーアプリで着信接続をリッスンするには、メソッドを```Listen```呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="e2c4f-155">この呼び出しでは、ハンドシェイクポートとトランスポートポートの両方を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="e2c4f-156">ハンドシェイクポートは、初期ハンドシェイクに使用されます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="e2c4f-157">データは、トランスポートポートを介して送信されます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-157">The data is then send over the transport port.</span></span> <span data-ttu-id="e2c4f-158">既定では、ポート番号**8265**と**8266**が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-158">By default port number **8265** and **8266** are used.</span></span>

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


## <a name="handling-connection-related-events"></a><span data-ttu-id="e2c4f-159">接続関連のイベントの処理</span><span class="sxs-lookup"><span data-stu-id="e2c4f-159">Handling connection related events</span></span>

<span data-ttu-id="e2c4f-160">は```PlayerContext``` 、接続の状態を監視するために3つのイベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="e2c4f-161">OnConnected:ホストへの接続が正常に確立されたときにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-161">OnConnected: Triggered when a connection to the host has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="e2c4f-162">OnDisconnected:確立された接続が終了した場合、または接続を確立できなかった場合にトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
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
><span data-ttu-id="e2c4f-163">指定```ConnectionFailureReason```できる値は、[ファイル](#idl)に記載されて```Microsoft.Holographic.AppRemoting.idl```います。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="e2c4f-164">OnListening:受信接続のリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="e2c4f-165">さらに、プレーヤーのコンテキストで```ConnectionState```プロパティを使用して接続状態を照会することもできます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="e2c4f-166">リモートで描画されたフレームを表示する</span><span class="sxs-lookup"><span data-stu-id="e2c4f-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="e2c4f-167">リモートでレンダリングされるコンテンツを表示```PlayerContext::BlitRemoteFrame()```するには、 [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)のレンダリング中にを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame()``` while rendering a [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="e2c4f-168">```BlitRemoteFrame()```現在の HolographicFrame のバックバッファーがレンダーターゲットとしてバインドされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-168">```BlitRemoteFrame()``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="e2c4f-169">バックバッファーは、 [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)プロパティを介して[HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)から受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="e2c4f-170">呼び出されると```BlitRemoteFrame()``` 、ホストアプリケーションからの最新の受信フレームを HolographicFrame の BackBuffer にコピーします。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-170">When called, ```BlitRemoteFrame()``` copies the latest received frame from the host application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="e2c4f-171">さらに、リモートアプリケーションがリモートフレームのレンダリング中にフォーカスポイントを指定している場合は、フォーカスポイントが設定されます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="e2c4f-172">```PlayerContext::BlitRemoteFrame()```現在のフレームのフォーカスポイントを上書きする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-172">```PlayerContext::BlitRemoteFrame()``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="e2c4f-173">フォールバックフォーカスポイントを指定するには、前に```PlayerContext::BlitRemoteFrame()``` [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-173">To specifiy a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame()```.</span></span> 
>- <span data-ttu-id="e2c4f-174">リモートフォーカスポイントを overrwrite するには、 [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame()```を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-174">To overrwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame()```.</span></span>

<span data-ttu-id="e2c4f-175">成功した```BlitRemoteFrame()```場合```BlitResult::Success_Color```、はを返します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-175">On success, ```BlitRemoteFrame()``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="e2c4f-176">それ以外の場合は、エラーの理由を返します。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="e2c4f-177">```BlitResult::Failed_NoRemoteFrameAvailable``` :使用可能なリモートフレームがないため、失敗しました。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="e2c4f-178">```BlitResult::Failed_NoCamera``` :カメラが存在しないために失敗しました。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="e2c4f-179">省略可能: 最後のリモートフレームに関する統計を取得します</span><span class="sxs-lookup"><span data-stu-id="e2c4f-179">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="e2c4f-180">パフォーマンスまたはネットワークの問題を診断するために、 ```PlayerContext::LastFrameStatistics```プロパティを使用して最後のリモートフレームに関する統計を取得できます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-180">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="e2c4f-181">統計は[HolographicFrame::P](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)の呼び出し中に更新されます。 current予測。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-181">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="e2c4f-182">詳細については、 ```PlayerFrameStatistics``` [ファイル](#idl)のドキュメント```Microsoft.Holographic.AppRemoting.idl```を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-182">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="e2c4f-183">省略可能: カスタムデータチャネル</span><span class="sxs-lookup"><span data-stu-id="e2c4f-183">Optional: Custom data channels</span></span>

<span data-ttu-id="e2c4f-184">カスタムデータチャネルは、既に確立されているリモート処理接続を介してユーザーデータを送信するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-184">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="e2c4f-185">詳細については、「[カスタムデータチャネル](holographic-remoting-custom-data-channels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-185">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2c4f-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2c4f-186">See Also</span></span>
* [<span data-ttu-id="e2c4f-187">Holographic Remoting ホストアプリの作成</span><span class="sxs-lookup"><span data-stu-id="e2c4f-187">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="e2c4f-188">カスタム Holographic リモート処理データチャネル</span><span class="sxs-lookup"><span data-stu-id="e2c4f-188">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="e2c4f-189">Holographic Remoting を使用したセキュリティで保護された接続の確立</span><span class="sxs-lookup"><span data-stu-id="e2c4f-189">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="e2c4f-190">Holographic リモート処理のトラブルシューティングと制限事項</span><span class="sxs-lookup"><span data-stu-id="e2c4f-190">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="e2c4f-191">Holographic リモート処理ソフトウェアライセンス条項</span><span class="sxs-lookup"><span data-stu-id="e2c4f-191">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="e2c4f-192">Microsoft のプライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="e2c4f-192">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)