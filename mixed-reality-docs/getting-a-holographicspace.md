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
# <a name="getting-a-holographicspace"></a>HolographicSpace を取得します。

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>クラスは、ポータル、holographic の世界にします。 没入型のレンダリングを制御、カメラのデータを提供し、空間的な裏付けとなる Api へのアクセスを提供します。 UWP アプリの 1 つは作成<a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a>または Win32 アプリケーションの HWND。

## <a name="set-up-the-holographic-space"></a>Holographic の領域を設定します。

Windows Mixed Reality アプリを作成する最初の手順は、holographic 領域オブジェクトを作成します。 従来の Windows アプリは、アプリケーション ビューの中核となるウィンドウ用に作成された Direct3D スワップ チェーンにレンダリングします。 このスワップ チェーンがスレート holographic の ui に表示されます。 アプリケーションのビューを 2D スレートではなく holographic させるには、スワップ チェーンではなく、中核となるウィンドウの holographic の領域を作成します。 全画面表示モードにアプリを配置するこの holographic 領域によって作成される holographic のフレームを表示します。

**UWP アプリ**[から始まる、 *Holographic DirectX 11 アプリ (ユニバーサル Windows) テンプレート*](creating-a-holographic-directx-project.md)でこのコードを探して、 **SetWindow**AppView.cpp メソッド:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

**Win32 アプリ**[から始まる、 *BasicHologram* Win32 サンプル](creating-a-holographic-directx-project.md#creating-a-win32-project)、見て**App::CreateWindowAndHolographicSpace**用、HWND を作成し、関連付けを作成して没入型の HWND に変換する方法の例<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:
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

UWP CoreWindow または Win32 HWND のいずれかの HolographicSpace を入手できた holographic のカメラの処理、座標系を作成および holographic のレンダリングを行うその HolographicSpace を使用します。 現在の holographic 領域は、DirectX テンプレートでの複数の場所で使用されます。
* **DeviceResources**クラスは、Direct3D デバイスを作成するには、HolographicSpace オブジェクトから一部の情報を取得する必要があります。 これは、holographic のディスプレイに関連付けられている DXGI アダプター ID です。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>クラスでは、アプリの direct3d11 のデバイスを使用して作成し、各 holographic のカメラのバック バッファーなどのデバイス ベースのリソースを管理します。 この関数では、内部で何を表示する場合は、DeviceResources.cpp で検索します。
* 関数は、 **DeviceResources::InitializeUsingHolographicSpace**アダプターを取得する方法を示します LUID – と優先するアダプターが指定されていない場合、既定のアダプターを選択する方法を参照しています。
* アプリのメイン クラスから holographic の領域を使用して**AppView::SetWindow**または**App::CreateWindowAndHolographicSpace**の更新プログラムとレンダリングします。

>[!NOTE]
>以下のセクションには、テンプレートの関数名が言うまでもなど**AppView::SetWindow** holographic の UWP アプリ テンプレートから開始することは、表示のコード スニペットは、UWP と Win32 アプリ間で均等に適用されますを前提としています。

セットアップに次に、について説明する処理**SetHolographicSpace** AppMain クラスで担当します。

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>カメラのイベントにサブスクライブして、作成、およびカメラのリソースの削除

アプリの holographic コンテンツでは、その holographic の領域に在住し、風景をさまざまなパースペクティブを表す 1 つまたは複数の holographic カメラを使用して表示されます。 Holographic の領域がある場合は、できた、holographic カメラのデータを受信することができます。

対応するアプリで必要な**CameraAdded**バック バッファーのレンダー ターゲット ビューなど、すべてのリソースを作成してイベントがそのカメラを特定します。 このコードを確認できます、 **DeviceResources::SetHolographicSpace**によって呼び出される関数**AppView::SetWindow**アプリは、すべての holographic フレームを作成する前に。

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

アプリでに応答することも必要な**CameraRemoved**そのカメラ用に作成されたリソースを解放することによってイベント。

**DeviceResources::SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

イベント ハンドラーは、フローを円滑に holographic のレンダリングに保つためにいくつか作業を完了する必要があり、アプリがまったくレンダリングできるようにします。 コードと詳細については、コメントを読めない: 探すことができます**OnCameraAdded**と**OnCameraRemoved**を理解するのには、メイン クラスにする方法、 **m_cameraResources**マップは、によって処理される**DeviceResources**します。

現在のところ、AppMain と holographic カメラについて知っておくアプリを有効にするのにはそれがセットアップに重点的に取り組んでいます。 これを踏まえてが次の 2 つの要件を記録するために重要です。

1. **CameraAdded**イベント ハンドラーでは、アプリ作業できます非同期的にリソースを作成して、新しい holographic カメラの資産の読み込みを完了します。 この作業が完了するは、複数のフレームを実行するアプリが、遅延を要求し、非同期的に読み込み後に、遅延を完了する必要があります。[PPL タスク](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl)非同期作業を行うために使用できます。 アプリは、イベント ハンドラーが終了したとき、または遅延の完了時にすぐにそのカメラにレンダリングする準備ができたことを確認する必要があります。 イベント ハンドラーの終了または完了、遅延、アプリが含まれているそのカメラで holographic フレームを受信する準備ができなことをシステムに指示します。

2. アプリが受信すると、 **CameraRemoved**イベント、バック バッファーと終了関数がすぐに右へのすべての参照を解放にする必要があります。 レンダー ターゲット ビュー、および他のリソースへの参照を保持する可能性がありますが含まれます、 [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)します。 アプリを確認しますバック バッファーがレンダー ターゲットとしてアタッチされていないことのように**CameraResources::ReleaseResourcesForBackBuffer**します。 に沿って作業速度を上げるのために、アプリがバック バッファーを解放し、し、非同期的にそのカメラを破棄するために必要なその他の作業を完了するタスクを起動できます。 Holographic アプリ テンプレートには、この目的のために使用できる PPL タスクが含まれています。

>[!NOTE]
>追加または削除されたカメラを使用して、フレームで示してときを判断する場合、 **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras)と[RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras)プロパティ。

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Holographic コンテンツ フレームの参照を作成します。

アプリのコンテンツを配置する必要があります、[空間座標系](coordinate-systems-in-directx.md)HolographicSpace でレンダリングされます。 システムは、ホログラムの座標系を確立するために使用できる 2 つのプライマリ フレームの参照を提供します。

Windows Holographic の参照フレームの 2 種類があります。 フレームは、デバイスに接続されていると、デバイスは、ユーザーの環境を移動すると、静止参照フレームを参照します。 Holographic アプリ テンプレートでは、既定では、静止した基準枠を使用します。これは、世界ロック ホログラムを表示するために最も簡単な方法のいずれかです。

デバイスの現在の場所の近くの位置を安定化には、静止した基準枠が設計されています。 つまり、デバイスからの座標のように、デバイスが学習の詳細については、周囲のスペースは、ユーザーの環境に関して若干ドリフトが許可されています。 静止した基準枠を作成する 2 つの方法があります: から座標系を取得、[空間ステージ](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)、既定値を使用して、または<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>します。 推奨される開始点は、イマーシブ ヘッドセット用の Windows Mixed Reality アプリを作成する場合、[空間ステージ](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)、また、プレイヤーが装着イマーシブ ヘッドセットの機能についての情報を提供します。 ここでは、既定値を使用する方法を紹介<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>します。

空間ロケーターは、Windows Mixed Reality デバイスを表しますと、デバイスの動きを追跡し、座標システムの場所を基準と見なすことができますを提供します。

**AppMain::OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

アプリを起動するときは、静止した基準枠を 1 回作成します。 これは、アプリを起動するときに、デバイスの位置に配置する配信元とワールド座標系の定義に似ています。 この参照フレームは、デバイスに移動しません。

**AppMain::SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

すべての参照フレームは、重力は、配置、ユーザーの環境に関して「を」y 軸を指していることを意味します。 Windows では、「右手」座標系を使用するため、z 軸の方向は、参照フレームが作成されるときに、デバイスが直面している"forward"方向と一致します。

>[!NOTE]
>使用して、アプリには、個々 のホログラムの正確な配置が必要とする場合、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>に現実の世界での位置に個々 のホログラムを固定します。 たとえば、ユーザーには、特別な関心のある点が示されている場合は、空間アンカーを使用します。 アンカー位置でユーザーがずれされませんが、調整することができます。 既定では、アンカーを調整すると、容易の位置に次のいくつかのフレームを修正が行われた後です。 アプリケーションによっては、これが発生した場合 (例: ホログラムが非表示になるまでに遅延) を別の方法で調整を処理するためにすることがあります。 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a>プロパティと<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a>イベントは、これらのカスタマイズを有効にします。

## <a name="respond-to-locatability-changed-events"></a>Locatability 変更イベントに応答するには

世界ロック ホログラムをレンダリングするには、自体の世界で見つけることができるデバイスが必要です。 これができるとは限りません環境の条件が原因と、ユーザーの中断時間の追跡を視覚可能性があります予想そうである場合。 この視覚的は、定常世界にではなく、デバイスに接続されている参照フレームを使用してレンダリングする必要があります。

アプリは、追跡が何らかの理由で中断された場合に通知を要求できます。 検出する LocatabilityChanged イベント自体を世界中の変更で検索するデバイスの機能に登録します。 **AppMain::SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

このイベントを使用して、決定ホログラムが静止している世界中に表示されることはできません。

## <a name="see-also"></a>関連項目
* [DirectX でのレンダリング](rendering-in-directx.md)
* [DirectX の座標系](coordinate-systems-in-directx.md)
