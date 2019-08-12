---
title: Holographic DirectX プロジェクトの作成
description: Windows Mixed Reality アプリテンプレートに基づいて新しい holographic アプリを作成する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holographic アプリ, 新しいアプリ, UWP アプリ, テンプレートアプリ, ホログラム, 新しいプロジェクト, チュートリアル, ダウンロード, サンプルコード
ms.openlocfilehash: 24f217021cd448f19a744696de42f580f139f76f
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387617"
---
# <a name="creating-a-holographic-directx-project"></a><span data-ttu-id="86e71-104">Holographic DirectX プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="86e71-104">Creating a holographic DirectX project</span></span>

<span data-ttu-id="86e71-105">HoloLens 用に作成した holographic アプリは、<a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">ユニバーサル Windows プラットフォーム (UWP) アプリ</a>になります。</span><span class="sxs-lookup"><span data-stu-id="86e71-105">A holographic app you create for a HoloLens will be a <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">Universal Windows Platform (UWP) app</a>.</span></span>  <span data-ttu-id="86e71-106">デスクトップ Windows Mixed Reality ヘッドセットを対象とする場合は、UWP アプリまたは Win32 アプリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="86e71-106">If targeting desktop Windows Mixed Reality headsets, you can create a UWP app or a Win32 app.</span></span>

<span data-ttu-id="86e71-107">DirectX 11 holographic UWP アプリテンプレートは DirectX 11 UWP アプリテンプレートとよく似ています。これには、プログラムループ (または "ゲームループ")、Direct3D デバイスとコンテキストを管理するための**DeviceResources**クラス、および簡略化されたコンテンツレンダラークラスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="86e71-107">The DirectX 11 holographic UWP app template is much like the DirectX 11 UWP app template; it includes a program loop (or "game loop"), a **DeviceResources** class to manage the Direct3D device and context, and a simplified content renderer class.</span></span> <span data-ttu-id="86e71-108">他の UWP アプリと同じように、 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>もあります。</span><span class="sxs-lookup"><span data-stu-id="86e71-108">It also has an <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, just like any other UWP app.</span></span>

<span data-ttu-id="86e71-109">ただし、mixed reality アプリには、一般的な Direct3D 11 UWP アプリには存在しないいくつかの追加機能があります。</span><span class="sxs-lookup"><span data-stu-id="86e71-109">The mixed reality app, however, has some additional capabilities that aren't present in a typical Direct3D 11 UWP app.</span></span> <span data-ttu-id="86e71-110">Windows Holographic アプリケーションテンプレートでは、次のことができます。</span><span class="sxs-lookup"><span data-stu-id="86e71-110">The Windows Holographic app template is able to:</span></span>
* <span data-ttu-id="86e71-111">Holographic カメラに関連付けられている Direct3D デバイスリソースを処理します。</span><span class="sxs-lookup"><span data-stu-id="86e71-111">Handle Direct3D device resources associated with holographic cameras.</span></span>
* <span data-ttu-id="86e71-112">システムからカメラバックバッファーを取得します。</span><span class="sxs-lookup"><span data-stu-id="86e71-112">Retrieve camera back buffers from the system.</span></span>
* <span data-ttu-id="86e71-113">[見つめ](gaze.md)入力を処理し、簡単な[ジェスチャ](gestures.md)を認識します。</span><span class="sxs-lookup"><span data-stu-id="86e71-113">Handle [gaze](gaze.md) input, and recognize a simple [gesture](gestures.md).</span></span>
* <span data-ttu-id="86e71-114">全画面表示のステレオレンダリングモードに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="86e71-114">Go into full-screen stereo rendering mode.</span></span>

## <a name="how-do-i-get-started"></a><span data-ttu-id="86e71-115">操作方法開始しますか?</span><span class="sxs-lookup"><span data-stu-id="86e71-115">How do I get started?</span></span>

<span data-ttu-id="86e71-116">まず、Visual Studio 2019 と Microsoft HoloLens emulator のダウンロードに関する説明に従って、[ツールをインストール](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="86e71-116">First [install the tools](install-the-tools.md), following the instructions on downloading Visual Studio 2019 and the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="86e71-117">Holographic アプリテンプレートは、Microsoft HoloLens エミュレーターと同じインストーラーに含まれています。</span><span class="sxs-lookup"><span data-stu-id="86e71-117">The holographic app templates are included in the same installer as the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="86e71-118">また、インストールする前に、テンプレートをインストールするオプションが選択されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="86e71-118">Also ensure that the option to install the templates is selected before installing.</span></span>

<span data-ttu-id="86e71-119">これで、DirectX 11 Windows Mixed Reality アプリを作成する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="86e71-119">Now you're ready to create your DirectX 11 Windows Mixed Reality app!</span></span> <span data-ttu-id="86e71-120">サンプルコンテンツを削除するには、 *pch*の**DRAW_SAMPLE_CONTENT**プリプロセッサディレクティブをコメントアウトします。</span><span class="sxs-lookup"><span data-stu-id="86e71-120">Note, to remove the sample content, comment out the **DRAW_SAMPLE_CONTENT** preprocessor directive in *pch.h*.</span></span>

## <a name="creating-a-uwp-project"></a><span data-ttu-id="86e71-121">UWP プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="86e71-121">Creating a UWP project</span></span>

<span data-ttu-id="86e71-122">[ツールがインストールさ](install-the-tools.md)れたら、HOLOGRAPHIC DirectX UWP プロジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="86e71-122">Once the [tools are installed](install-the-tools.md) you can then create a holographic DirectX UWP project.</span></span>

<span data-ttu-id="86e71-123">新しいプロジェクトを作成するには:</span><span class="sxs-lookup"><span data-stu-id="86e71-123">To create a new project:</span></span>
1. <span data-ttu-id="86e71-124">**Visual Studio**を起動します。</span><span class="sxs-lookup"><span data-stu-id="86e71-124">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="86e71-125">[**ファイル**] メニューの [**新規作成**] をポイントし、コンテキストメニューの [**プロジェクト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="86e71-125">From the **File** menu, point to **New** and select **Project** from the context menu.</span></span> <span data-ttu-id="86e71-126">[**新しいプロジェクト**] ダイアログボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="86e71-126">The **New Project** dialog opens.</span></span>
3. <span data-ttu-id="86e71-127">左側にある [**インストール済み**] を展開し、[**ビジュアルC++** 言語] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="86e71-127">Expand **Installed** on the left and expand the **Visual C++** language node.</span></span>
4. <span data-ttu-id="86e71-128">[ **Windows Universal > Holographic** ] ノードに移動し、[ **Holographic DirectX 11 App (Universal WindowsC++) (/WinRT)** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="86e71-128">Navigate to the **Windows Universal > Holographic** node and select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   <span data-ttu-id="86e71-129">![Visual Studio の Holographic DirectX 11 C++/WinRT UWP アプリプロジェクトテンプレートのスクリーンショット](images/holographic-directx-app-cpp-new-project.png)</span><span class="sxs-lookup"><span data-stu-id="86e71-129">![Screenshot of the Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio](images/holographic-directx-app-cpp-new-project.png)</span></span><br>
   <span data-ttu-id="86e71-130">*Visual Studio でC++の Holographic DirectX 11/WinRT UWP アプリプロジェクトテンプレート*</span><span class="sxs-lookup"><span data-stu-id="86e71-130">*Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="86e71-131">プロジェクトテンプレートの名前に "(C++/WinRT)" が含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="86e71-131">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="86e71-132">それ以外の場合は、古いバージョンの holographic プロジェクトテンプレートがインストールされています。</span><span class="sxs-lookup"><span data-stu-id="86e71-132">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="86e71-133">最新のプロジェクトテンプレートを入手するには、[最新の HoloLens エミュレーターをインストール](using-the-hololens-emulator.md)します。</span><span class="sxs-lookup"><span data-stu-id="86e71-133">To get the latest project templates, [install the latest HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
5. <span data-ttu-id="86e71-134">[**名前**] と [**場所**] のテキストボックスに入力し、[ **OK**] をクリックまたはタップします。</span><span class="sxs-lookup"><span data-stu-id="86e71-134">Fill in the **Name** and **Location** text boxes, and click or tap **OK**.</span></span> <span data-ttu-id="86e71-135">Holographic app プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="86e71-135">The holographic app project is created.</span></span>
6. <span data-ttu-id="86e71-136">HoloLens 2 のみを対象とする開発では、**ターゲットバージョン**と**最小バージョン**が**Windows 10 バージョン 1903**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="86e71-136">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="86e71-137">HoloLens (第1世代) またはデスクトップ Windows Mixed Reality ヘッドセットも対象としている場合は、代わりに、[**最小バージョン**] を**Windows 10 バージョン 1809**に設定できます。ただし、これには、新しいを使用するときに、コードにいくつかの<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">バージョンのアダプティブチェック</a>が必要になります。HoloLens 2 の機能。</span><span class="sxs-lookup"><span data-stu-id="86e71-137">If you are also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809** instead, although this will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adaptive checks</a> in your code when using new features of HoloLens 2.</span></span>
   <span data-ttu-id="86e71-138">![ターゲットバージョンと最小バージョンとして Windows 10 バージョン1903を設定するスクリーンショット](images/new-uwp-project.png)</span><span class="sxs-lookup"><span data-stu-id="86e71-138">![Screenshot of setting Windows 10, version 1903 as the target and minimum versions](images/new-uwp-project.png)</span></span><br>
   <span data-ttu-id="86e71-139">*ターゲットバージョンと最小バージョンとして**Windows 10 バージョン1903を**設定する*</span><span class="sxs-lookup"><span data-stu-id="86e71-139">*Setting **Windows 10, version 1903** as the target and minimum versions*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="86e71-140">オプションとして**windows 10 バージョン 1903**が表示されない場合は、最新の WINDOWS 10 SDK がインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="86e71-140">If you do not see **Windows 10, version 1903** as an option, you do not have the latest Windows 10 SDK installed.</span></span>  <span data-ttu-id="86e71-141">このオプションを表示するに<a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">は、Windows 10 SDK のバージョン10.0.18362.0 以降をインストール</a>します。</span><span class="sxs-lookup"><span data-stu-id="86e71-141">To get this option to appear, <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">install version 10.0.18362.0 or later of the Windows 10 SDK</a>.</span></span>

<span data-ttu-id="86e71-142">このテンプレートは、標準に準拠している c++ 17 コンパイラをサポートする Windows ランタイム api の c++ 17 言語プロジェクションである<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>を使用してプロジェクトを生成します。</span><span class="sxs-lookup"><span data-stu-id="86e71-142">The template generates a project using <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="86e71-143">このプロジェクトは、ユーザーから2メートル離れたワールドロックキューブを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="86e71-143">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="86e71-144">ユーザーは、コントローラー上のボタンを使用して、ユーザーの[宝石](gaze.md)によって指定された別の位置にキューブを[配置できます](gestures.md#air-tap)。</span><span class="sxs-lookup"><span data-stu-id="86e71-144">The user can [air-tap](gestures.md#air-tap) or press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="86e71-145">このプロジェクトを変更して、mixed reality アプリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="86e71-145">You can modify this project to create any mixed reality app.</span></span>

<span data-ttu-id="86e71-146">または、SharpDX に基づく**Visual C#**  holographic プロジェクトテンプレートを使用して、新しいプロジェクトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="86e71-146">Alternatively, you can create a new project using the **Visual C#** holographic project template, which is based on SharpDX.</span></span>  <span data-ttu-id="86e71-147">Holographic C#プロジェクトが windows holographic アプリテンプレートから開始されなかった場合は、Windows Mixed Reality C#テンプレートプロジェクトから ms. fxcompile .targets ファイルをコピーして、HLSL ファイルにインポートして HLSL をコンパイルする必要があります。プロジェクトに追加するファイル。</span><span class="sxs-lookup"><span data-stu-id="86e71-147">If your holographic C# project did not start from the Windows Holographic app template, you will need to copy the ms.fxcompile.targets file from a Windows Mixed Reality C# template project and import it in your .csproj file in order to compile HLSL files that you add to your project.</span></span>

<span data-ttu-id="86e71-148">[「Visual Studio を使用してデプロイとデバッグ](using-visual-studio.md)を行う」で、HoloLens、PC にデバイスが接続されている PC、またはエミュレーターにサンプルを構築してデプロイする方法について確認します。</span><span class="sxs-lookup"><span data-stu-id="86e71-148">Review [Using Visual Studio to deploy and debug](using-visual-studio.md) for information on how to build and deploy the sample to your HoloLens, PC with immersive device attached, or an emulator.</span></span>

<span data-ttu-id="86e71-149">次の手順の残りの部分では、を使用C++してアプリをビルドすることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="86e71-149">The rest of the instructions below will assume that you are using C++ to build your app.</span></span>

### <a name="uwp-app-entry-point"></a><span data-ttu-id="86e71-150">UWP アプリのエントリポイント</span><span class="sxs-lookup"><span data-stu-id="86e71-150">UWP app entry point</span></span>

<span data-ttu-id="86e71-151">Holographic UWP アプリは、AppView .cpp の**Wwinmain**関数で開始されます。</span><span class="sxs-lookup"><span data-stu-id="86e71-151">Your holographic UWP app starts in the **wWinMain** function in AppView.cpp.</span></span> <span data-ttu-id="86e71-152">**Wwinmain**関数は、アプリの<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>を作成し、それを使用して<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a>を開始します。</span><span class="sxs-lookup"><span data-stu-id="86e71-152">The **wWinMain** function creates the app's <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> and starts the <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> with it.</span></span>

<span data-ttu-id="86e71-153">**Appview .cpp**から:</span><span class="sxs-lookup"><span data-stu-id="86e71-153">From **AppView.cpp**:</span></span>

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

<span data-ttu-id="86e71-154">この時点から、AppView クラスは、Windows 基本入力イベント、CoreWindow イベントとメッセージングなどとの対話を処理します。</span><span class="sxs-lookup"><span data-stu-id="86e71-154">From that point on, the AppView class handles interaction with Windows basic input events, CoreWindow events and messaging, and so on.</span></span> <span data-ttu-id="86e71-155">また、アプリで使用される HolographicSpace も作成されます。</span><span class="sxs-lookup"><span data-stu-id="86e71-155">It will also create the HolographicSpace used by your app.</span></span>

## <a name="creating-a-win32-project"></a><span data-ttu-id="86e71-156">Win32 プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="86e71-156">Creating a Win32 project</span></span>

<span data-ttu-id="86e71-157">Win32 holographic プロジェクトの構築を開始する最も簡単な方法は、 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *basichologram* win32 サンプル</a>を調整することです。</span><span class="sxs-lookup"><span data-stu-id="86e71-157">The easiest way to get started building a Win32 holographic project is to adapt the <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">*BasicHologram* Win32 sample</a>.</span></span>

<span data-ttu-id="86e71-158">この Win32 サンプルでは、標準に準拠している c++ 17 コンパイラをサポートする Windows ランタイム api の c++ 17 言語プロジェクションである<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>を使用します。</span><span class="sxs-lookup"><span data-stu-id="86e71-158">This Win32 sample uses <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="86e71-159">このプロジェクトは、ユーザーから2メートル離れたワールドロックキューブを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="86e71-159">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="86e71-160">ユーザーは、コントローラー上のボタンをクリックして、ユーザーの[宝石](gaze.md)によって指定された別の位置にキューブを配置できます。</span><span class="sxs-lookup"><span data-stu-id="86e71-160">The user can press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="86e71-161">このプロジェクトを変更して、mixed reality アプリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="86e71-161">You can modify this project to create any mixed reality app.</span></span>

### <a name="win32-app-entry-point"></a><span data-ttu-id="86e71-162">Win32 アプリのエントリポイント</span><span class="sxs-lookup"><span data-stu-id="86e71-162">Win32 app entry point</span></span>

<span data-ttu-id="86e71-163">Holographic Win32 アプリは、AppMain の**Wwinmain**関数で開始されます。</span><span class="sxs-lookup"><span data-stu-id="86e71-163">Your holographic Win32 app starts in the **wWinMain** function in AppMain.cpp.</span></span> <span data-ttu-id="86e71-164">**Wwinmain**関数は、アプリの HWND を作成し、そのメッセージループを開始します。</span><span class="sxs-lookup"><span data-stu-id="86e71-164">The **wWinMain** function creates the app's HWND and starts its message loop.</span></span>

<span data-ttu-id="86e71-165">**Appmain .cpp**から:</span><span class="sxs-lookup"><span data-stu-id="86e71-165">From **AppMain.cpp**:</span></span>

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

<span data-ttu-id="86e71-166">この時点から、AppMain クラスは基本的なウィンドウメッセージとの対話を処理します。</span><span class="sxs-lookup"><span data-stu-id="86e71-166">From that point on, the AppMain class handles interaction with basic window messages, and so on.</span></span> <span data-ttu-id="86e71-167">また、アプリで使用される HolographicSpace も作成されます。</span><span class="sxs-lookup"><span data-stu-id="86e71-167">It will also create the HolographicSpace used by your app.</span></span>

## <a name="render-holographic-content"></a><span data-ttu-id="86e71-168">Holographic コンテンツのレンダリング</span><span class="sxs-lookup"><span data-stu-id="86e71-168">Render holographic content</span></span>

<span data-ttu-id="86e71-169">プロジェクトの**コンテンツ**フォルダーには、 [holographic 空間](getting-a-holographicspace.md)にホログラムをレンダリングするためのクラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="86e71-169">The project's **Content** folder contains classes for rendering holograms in the [holographic space](getting-a-holographicspace.md).</span></span> <span data-ttu-id="86e71-170">テンプレートの既定のホログラムは、ユーザーから2メートル離れた位置にある回転する立方体です。</span><span class="sxs-lookup"><span data-stu-id="86e71-170">The default hologram in the template is a spinning cube that's placed two meters away from the user.</span></span> <span data-ttu-id="86e71-171">このキューブの描画は、次の主要なメソッドを含む SpinningCubeRenderer に実装されてい**ます**。</span><span class="sxs-lookup"><span data-stu-id="86e71-171">Drawing this cube is implemented in **SpinningCubeRenderer.cpp**, which has these key methods:</span></span>

|  <span data-ttu-id="86e71-172">メソッド</span><span class="sxs-lookup"><span data-stu-id="86e71-172">Method</span></span>  |  <span data-ttu-id="86e71-173">説明</span><span class="sxs-lookup"><span data-stu-id="86e71-173">Explanation</span></span> | 
|----------|----------|
|  `CreateDeviceDependentResources` |  <span data-ttu-id="86e71-174">シェーダーを読み込み、キューブメッシュを作成します。</span><span class="sxs-lookup"><span data-stu-id="86e71-174">Loads shaders and creates the cube mesh.</span></span> | 
|  `PositionHologram` |  <span data-ttu-id="86e71-175">指定した<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>によって指定された場所にホログラムを配置します。</span><span class="sxs-lookup"><span data-stu-id="86e71-175">Places the hologram at the location specified by the provided <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span></span> | 
|  `Update` |  <span data-ttu-id="86e71-176">キューブを回転させ、モデルマトリックスを設定します。</span><span class="sxs-lookup"><span data-stu-id="86e71-176">Rotates the cube, and sets the model matrix.</span></span> | 
|  `Render` |  <span data-ttu-id="86e71-177">頂点シェーダーとピクセルシェーダーを使用してフレームをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="86e71-177">Renders a frame using the vertex and pixel shaders.</span></span> | 

<span data-ttu-id="86e71-178">**シェーダー**サブフォルダーには、4つの既定のシェーダー実装が含まれています。</span><span class="sxs-lookup"><span data-stu-id="86e71-178">The **Shaders** subfolder contains four default shader implementations:</span></span>

|  <span data-ttu-id="86e71-179">シェーダー</span><span class="sxs-lookup"><span data-stu-id="86e71-179">Shader</span></span>  |  <span data-ttu-id="86e71-180">説明</span><span class="sxs-lookup"><span data-stu-id="86e71-180">Explanation</span></span> | 
|----------|----------|
|  `GeometryShader.hlsl` |  <span data-ttu-id="86e71-181">ジオメトリを変更せずに残すパススルー。</span><span class="sxs-lookup"><span data-stu-id="86e71-181">A pass-through that leaves the geometry unmodified.</span></span> | 
|  `PixelShader.hlsl` |  <span data-ttu-id="86e71-182">カラーデータを通過します。</span><span class="sxs-lookup"><span data-stu-id="86e71-182">Passes through the color data.</span></span> <span data-ttu-id="86e71-183">色データが補間され、ラスタライズの手順でピクセルに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="86e71-183">The color data is interpolated and assigned to a pixel at the rasterization step.</span></span> | 
|  `VertexShader.hlsl` |  <span data-ttu-id="86e71-184">GPU で頂点処理を行うための単純なシェーダー。</span><span class="sxs-lookup"><span data-stu-id="86e71-184">Simple shader to do vertex processing on the GPU.</span></span> | 
|  `VPRTVertexShader.hlsl` |  <span data-ttu-id="86e71-185">Windows Mixed Reality ステレオレンダリング用に最適化された、GPU で頂点処理を行うための単純なシェーダー。</span><span class="sxs-lookup"><span data-stu-id="86e71-185">Simple shader to do vertex processing on the GPU, that is optimized for Windows Mixed Reality stereo rendering.</span></span> | 

<span data-ttu-id="86e71-186">`VertexShaderShared.hlsl`との間で`VertexShader.hlsl`共有される共通のコードを`VPRTVertexShader.hlsl`格納します。</span><span class="sxs-lookup"><span data-stu-id="86e71-186">`VertexShaderShared.hlsl` contains common code shared between `VertexShader.hlsl` and `VPRTVertexShader.hlsl`.</span></span>

<span data-ttu-id="86e71-187">シェーダーは、プロジェクトのビルド時にコンパイルされ、 **SpinningCubeRenderer:: CreateDeviceDependentResources**メソッドに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="86e71-187">The shaders are compiled when the project is built, and they're loaded in the **SpinningCubeRenderer::CreateDeviceDependentResources** method.</span></span>

## <a name="interact-with-your-holograms"></a><span data-ttu-id="86e71-188">ホログラムを操作する</span><span class="sxs-lookup"><span data-stu-id="86e71-188">Interact with your holograms</span></span>

<span data-ttu-id="86e71-189">ユーザー入力は**SpatialInputHandler**クラスで処理されます。このクラスは<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a>インスタンスを取得し、 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">sourcepressed</a>イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="86e71-189">User input is processed in the **SpatialInputHandler** class, which gets a <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> instance and subscribes to the <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> event.</span></span> <span data-ttu-id="86e71-190">これにより、エアタップジェスチャとその他の空間入力イベントを検出できるようになります。</span><span class="sxs-lookup"><span data-stu-id="86e71-190">This enables detecting the air-tap gesture and other spatial input events.</span></span>

## <a name="update-holographic-content"></a><span data-ttu-id="86e71-191">Holographic コンテンツの更新</span><span class="sxs-lookup"><span data-stu-id="86e71-191">Update holographic content</span></span>

<span data-ttu-id="86e71-192">混合 reality アプリの更新は、既定ではの`AppMain.cpp` **Update**メソッドに実装されているゲームループで更新されます。</span><span class="sxs-lookup"><span data-stu-id="86e71-192">Your mixed reality app updates in a game loop, which by default is implemented in the **Update** method in `AppMain.cpp`.</span></span> <span data-ttu-id="86e71-193">**Update**メソッドは、回転するキューブなどのシーンオブジェクトを更新し、最新のビューおよび射影マトリックスを取得して、スワップチェーンを表示するために使用される<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="86e71-193">The **Update** method updates scene objects, like the spinning cube, and returns a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> object that is used to get up-to-date view and projection matrices and to present the swap chain.</span></span>

<span data-ttu-id="86e71-194">の `AppMain.cpp` Render メソッドは、現在のアプリと空間ポジショニングの状態に従って、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>を受け取り、現在のフレームを各 holographic カメラにレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="86e71-194">The **Render** method in `AppMain.cpp` takes the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> and renders the current frame to each holographic camera, according to the current app and spatial positioning state.</span></span>

## <a name="see-also"></a><span data-ttu-id="86e71-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="86e71-195">See also</span></span>
* [<span data-ttu-id="86e71-196">HolographicSpace を入手する</span><span class="sxs-lookup"><span data-stu-id="86e71-196">Getting a HolographicSpace</span></span>](getting-a-holographicspace.md)
* <span data-ttu-id="86e71-197"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span><span class="sxs-lookup"><span data-stu-id="86e71-197"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span></span>
* [<span data-ttu-id="86e71-198">DirectX でのレンダリング</span><span class="sxs-lookup"><span data-stu-id="86e71-198">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="86e71-199">Visual Studio を使用してデプロイおよびデバッグする</span><span class="sxs-lookup"><span data-stu-id="86e71-199">Using Visual Studio to deploy and debug</span></span>](using-visual-studio.md)
* [<span data-ttu-id="86e71-200">HoloLens のエミュレーターを使用する</span><span class="sxs-lookup"><span data-stu-id="86e71-200">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="86e71-201">XAML とホログラフィック DirectX アプリの使用</span><span class="sxs-lookup"><span data-stu-id="86e71-201">Using XAML with holographic DirectX apps</span></span>](using-xaml-with-holographic-directx-apps.md)
