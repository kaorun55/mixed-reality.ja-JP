---
title: HolographicSpace を取得します。
description: HolographicSpace API、holographic のレンダリングと空間的な入力のコア概念について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HolographicSpace、CoreWindow、空間入力、表示、スワップ チェーン、holographic フレーム、update ループ、ゲーム ループの基準枠、locatability、サンプル コード、チュートリアル
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605081"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="9c471-104">HolographicSpace を取得します。</span><span class="sxs-lookup"><span data-stu-id="9c471-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="9c471-105"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>クラスは、ポータル、holographic の世界にします。</span><span class="sxs-lookup"><span data-stu-id="9c471-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="9c471-106">没入型のレンダリングを制御、カメラのデータを提供し、空間的な裏付けとなる Api へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9c471-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="9c471-107">UWP アプリの 1 つは作成<a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a>または Win32 アプリケーションの HWND。</span><span class="sxs-lookup"><span data-stu-id="9c471-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="9c471-108">Holographic の領域を設定します。</span><span class="sxs-lookup"><span data-stu-id="9c471-108">Set up the holographic space</span></span>

<span data-ttu-id="9c471-109">Windows Mixed Reality アプリを作成する最初の手順は、holographic 領域オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9c471-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="9c471-110">従来の Windows アプリは、アプリケーション ビューの中核となるウィンドウ用に作成された Direct3D スワップ チェーンにレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="9c471-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="9c471-111">このスワップ チェーンがスレート holographic の ui に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c471-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="9c471-112">アプリケーションのビューを 2D スレートではなく holographic させるには、スワップ チェーンではなく、中核となるウィンドウの holographic の領域を作成します。</span><span class="sxs-lookup"><span data-stu-id="9c471-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="9c471-113">全画面表示モードにアプリを配置するこの holographic 領域によって作成される holographic のフレームを表示します。</span><span class="sxs-lookup"><span data-stu-id="9c471-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="9c471-114">**UWP アプリ**[から始まる、 *Holographic DirectX 11 アプリ (ユニバーサル Windows) テンプレート*](creating-a-holographic-directx-project.md)でこのコードを探して、 **SetWindow**AppView.cpp メソッド:</span><span class="sxs-lookup"><span data-stu-id="9c471-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="9c471-115">**Win32 アプリ**[から始まる、 *BasicHologram* Win32 サンプル](creating-a-holographic-directx-project.md#creating-a-win32-project)、見て**App::CreateWindowAndHolographicSpace**用、HWND を作成し、関連付けを作成して没入型の HWND に変換する方法の例<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span><span class="sxs-lookup"><span data-stu-id="9c471-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

<span data-ttu-id="9c471-116">UWP CoreWindow または Win32 HWND のいずれかの HolographicSpace を入手できた holographic のカメラの処理、座標系を作成および holographic のレンダリングを行うその HolographicSpace を使用します。</span><span class="sxs-lookup"><span data-stu-id="9c471-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="9c471-117">現在の holographic 領域は、DirectX テンプレートでの複数の場所で使用されます。</span><span class="sxs-lookup"><span data-stu-id="9c471-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="9c471-118">**DeviceResources**クラスは、Direct3D デバイスを作成するには、HolographicSpace オブジェクトから一部の情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c471-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="9c471-119">これは、holographic のディスプレイに関連付けられている DXGI アダプター ID です。</span><span class="sxs-lookup"><span data-stu-id="9c471-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="9c471-120"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>クラスでは、アプリの direct3d11 のデバイスを使用して作成し、各 holographic のカメラのバック バッファーなどのデバイス ベースのリソースを管理します。</span><span class="sxs-lookup"><span data-stu-id="9c471-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="9c471-121">この関数では、内部で何を表示する場合は、DeviceResources.cpp で検索します。</span><span class="sxs-lookup"><span data-stu-id="9c471-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="9c471-122">関数は、 **DeviceResources::InitializeUsingHolographicSpace**アダプターを取得する方法を示します LUID – と優先するアダプターが指定されていない場合、既定のアダプターを選択する方法を参照しています。</span><span class="sxs-lookup"><span data-stu-id="9c471-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="9c471-123">アプリのメイン クラスから holographic の領域を使用して**AppView::SetWindow**または**App::CreateWindowAndHolographicSpace**の更新プログラムとレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="9c471-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="9c471-124">以下のセクションには、テンプレートの関数名が言うまでもなど**AppView::SetWindow** holographic の UWP アプリ テンプレートから開始することは、表示のコード スニペットは、UWP と Win32 アプリ間で均等に適用されますを前提としています。</span><span class="sxs-lookup"><span data-stu-id="9c471-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="9c471-125">セットアップに次に、について説明する処理**SetHolographicSpace** AppMain クラスで担当します。</span><span class="sxs-lookup"><span data-stu-id="9c471-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="9c471-126">カメラのイベントにサブスクライブして、作成、およびカメラのリソースの削除</span><span class="sxs-lookup"><span data-stu-id="9c471-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="9c471-127">アプリの holographic コンテンツでは、その holographic の領域に在住し、風景をさまざまなパースペクティブを表す 1 つまたは複数の holographic カメラを使用して表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c471-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="9c471-128">Holographic の領域がある場合は、できた、holographic カメラのデータを受信することができます。</span><span class="sxs-lookup"><span data-stu-id="9c471-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="9c471-129">対応するアプリで必要な**CameraAdded**バック バッファーのレンダー ターゲット ビューなど、すべてのリソースを作成してイベントがそのカメラを特定します。</span><span class="sxs-lookup"><span data-stu-id="9c471-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="9c471-130">このコードを確認できます、 **DeviceResources::SetHolographicSpace**によって呼び出される関数**AppView::SetWindow**アプリは、すべての holographic フレームを作成する前に。</span><span class="sxs-lookup"><span data-stu-id="9c471-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="9c471-131">アプリでに応答することも必要な**CameraRemoved**そのカメラ用に作成されたリソースを解放することによってイベント。</span><span class="sxs-lookup"><span data-stu-id="9c471-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="9c471-132">**DeviceResources::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="9c471-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="9c471-133">イベント ハンドラーは、フローを円滑に holographic のレンダリングに保つためにいくつか作業を完了する必要があり、アプリがまったくレンダリングできるようにします。</span><span class="sxs-lookup"><span data-stu-id="9c471-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="9c471-134">コードと詳細については、コメントを読めない: 探すことができます**OnCameraAdded**と**OnCameraRemoved**を理解するのには、メイン クラスにする方法、 **m_cameraResources**マップは、によって処理される**DeviceResources**します。</span><span class="sxs-lookup"><span data-stu-id="9c471-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="9c471-135">現在のところ、AppMain と holographic カメラについて知っておくアプリを有効にするのにはそれがセットアップに重点的に取り組んでいます。</span><span class="sxs-lookup"><span data-stu-id="9c471-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="9c471-136">これを踏まえてが次の 2 つの要件を記録するために重要です。</span><span class="sxs-lookup"><span data-stu-id="9c471-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="9c471-137">**CameraAdded**イベント ハンドラーでは、アプリ作業できます非同期的にリソースを作成して、新しい holographic カメラの資産の読み込みを完了します。</span><span class="sxs-lookup"><span data-stu-id="9c471-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="9c471-138">この作業が完了するは、複数のフレームを実行するアプリが、遅延を要求し、非同期的に読み込み後に、遅延を完了する必要があります。[PPL タスク](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl)非同期作業を行うために使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c471-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="9c471-139">アプリは、イベント ハンドラーが終了したとき、または遅延の完了時にすぐにそのカメラにレンダリングする準備ができたことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c471-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="9c471-140">イベント ハンドラーの終了または完了、遅延、アプリが含まれているそのカメラで holographic フレームを受信する準備ができなことをシステムに指示します。</span><span class="sxs-lookup"><span data-stu-id="9c471-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="9c471-141">アプリが受信すると、 **CameraRemoved**イベント、バック バッファーと終了関数がすぐに右へのすべての参照を解放にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c471-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="9c471-142">レンダー ターゲット ビュー、および他のリソースへの参照を保持する可能性がありますが含まれます、 [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)します。</span><span class="sxs-lookup"><span data-stu-id="9c471-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="9c471-143">アプリを確認しますバック バッファーがレンダー ターゲットとしてアタッチされていないことのように**CameraResources::ReleaseResourcesForBackBuffer**します。</span><span class="sxs-lookup"><span data-stu-id="9c471-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="9c471-144">に沿って作業速度を上げるのために、アプリがバック バッファーを解放し、し、非同期的にそのカメラを破棄するために必要なその他の作業を完了するタスクを起動できます。</span><span class="sxs-lookup"><span data-stu-id="9c471-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="9c471-145">Holographic アプリ テンプレートには、この目的のために使用できる PPL タスクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9c471-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="9c471-146">追加または削除されたカメラを使用して、フレームで示してときを判断する場合、 **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras)と[RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras)プロパティ。</span><span class="sxs-lookup"><span data-stu-id="9c471-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="9c471-147">Holographic コンテンツ フレームの参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="9c471-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="9c471-148">アプリのコンテンツを配置する必要があります、[空間座標系](coordinate-systems-in-directx.md)HolographicSpace でレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="9c471-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="9c471-149">システムは、ホログラムの座標系を確立するために使用できる 2 つのプライマリ フレームの参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="9c471-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="9c471-150">Windows Holographic の参照フレームの 2 種類があります。 フレームは、デバイスに接続されていると、デバイスは、ユーザーの環境を移動すると、静止参照フレームを参照します。</span><span class="sxs-lookup"><span data-stu-id="9c471-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="9c471-151">Holographic アプリ テンプレートでは、既定では、静止した基準枠を使用します。これは、世界ロック ホログラムを表示するために最も簡単な方法のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="9c471-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="9c471-152">デバイスの現在の場所の近くの位置を安定化には、静止した基準枠が設計されています。</span><span class="sxs-lookup"><span data-stu-id="9c471-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="9c471-153">つまり、デバイスからの座標のように、デバイスが学習の詳細については、周囲のスペースは、ユーザーの環境に関して若干ドリフトが許可されています。</span><span class="sxs-lookup"><span data-stu-id="9c471-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="9c471-154">静止した基準枠を作成する 2 つの方法があります: から座標系を取得、[空間ステージ](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)、既定値を使用して、または<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>します。</span><span class="sxs-lookup"><span data-stu-id="9c471-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="9c471-155">推奨される開始点は、イマーシブ ヘッドセット用の Windows Mixed Reality アプリを作成する場合、[空間ステージ](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)、また、プレイヤーが装着イマーシブ ヘッドセットの機能についての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="9c471-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="9c471-156">ここでは、既定値を使用する方法を紹介<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>します。</span><span class="sxs-lookup"><span data-stu-id="9c471-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="9c471-157">空間ロケーターは、Windows Mixed Reality デバイスを表しますと、デバイスの動きを追跡し、座標システムの場所を基準と見なすことができますを提供します。</span><span class="sxs-lookup"><span data-stu-id="9c471-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="9c471-158">**AppMain::OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="9c471-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="9c471-159">アプリを起動するときは、静止した基準枠を 1 回作成します。</span><span class="sxs-lookup"><span data-stu-id="9c471-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="9c471-160">これは、アプリを起動するときに、デバイスの位置に配置する配信元とワールド座標系の定義に似ています。</span><span class="sxs-lookup"><span data-stu-id="9c471-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="9c471-161">この参照フレームは、デバイスに移動しません。</span><span class="sxs-lookup"><span data-stu-id="9c471-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="9c471-162">**AppMain::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="9c471-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="9c471-163">すべての参照フレームは、重力は、配置、ユーザーの環境に関して「を」y 軸を指していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9c471-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="9c471-164">Windows では、「右手」座標系を使用するため、z 軸の方向は、参照フレームが作成されるときに、デバイスが直面している"forward"方向と一致します。</span><span class="sxs-lookup"><span data-stu-id="9c471-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="9c471-165">使用して、アプリには、個々 のホログラムの正確な配置が必要とする場合、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>に現実の世界での位置に個々 のホログラムを固定します。</span><span class="sxs-lookup"><span data-stu-id="9c471-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="9c471-166">たとえば、ユーザーには、特別な関心のある点が示されている場合は、空間アンカーを使用します。</span><span class="sxs-lookup"><span data-stu-id="9c471-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="9c471-167">アンカー位置でユーザーがずれされませんが、調整することができます。</span><span class="sxs-lookup"><span data-stu-id="9c471-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="9c471-168">既定では、アンカーを調整すると、容易の位置に次のいくつかのフレームを修正が行われた後です。</span><span class="sxs-lookup"><span data-stu-id="9c471-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="9c471-169">アプリケーションによっては、これが発生した場合 (例: ホログラムが非表示になるまでに遅延) を別の方法で調整を処理するためにすることがあります。</span><span class="sxs-lookup"><span data-stu-id="9c471-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="9c471-170"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a>プロパティと<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a>イベントは、これらのカスタマイズを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9c471-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="9c471-171">Locatability 変更イベントに応答するには</span><span class="sxs-lookup"><span data-stu-id="9c471-171">Respond to locatability changed events</span></span>

<span data-ttu-id="9c471-172">世界ロック ホログラムをレンダリングするには、自体の世界で見つけることができるデバイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="9c471-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="9c471-173">これができるとは限りません環境の条件が原因と、ユーザーの中断時間の追跡を視覚可能性があります予想そうである場合。</span><span class="sxs-lookup"><span data-stu-id="9c471-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="9c471-174">この視覚的は、定常世界にではなく、デバイスに接続されている参照フレームを使用してレンダリングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c471-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="9c471-175">アプリは、追跡が何らかの理由で中断された場合に通知を要求できます。</span><span class="sxs-lookup"><span data-stu-id="9c471-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="9c471-176">検出する LocatabilityChanged イベント自体を世界中の変更で検索するデバイスの機能に登録します。</span><span class="sxs-lookup"><span data-stu-id="9c471-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="9c471-177">**AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="9c471-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="9c471-178">このイベントを使用して、決定ホログラムが静止している世界中に表示されることはできません。</span><span class="sxs-lookup"><span data-stu-id="9c471-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c471-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c471-179">See also</span></span>
* [<span data-ttu-id="9c471-180">DirectX でのレンダリング</span><span class="sxs-lookup"><span data-stu-id="9c471-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="9c471-181">DirectX の座標系</span><span class="sxs-lookup"><span data-stu-id="9c471-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
