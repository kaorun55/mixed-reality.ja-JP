---
title: Holographic DirectX プロジェクトを作成します。
description: Windows Mixed Reality アプリ テンプレートに基づく新しい holographic アプリを作成する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、holographic アプリ、新しいアプリ、UWP アプリ、テンプレートのアプリ、ホログラム、新しいプロジェクト、チュートリアル、ダウンロード、サンプル コード
ms.openlocfilehash: a7eac9d8056fe5f7bcc442d6441f71331fa96cf6
ms.sourcegitcommit: 19c9bff21061d485821b61c9f3498daef8fa8235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "65828119"
---
# <a name="creating-a-holographic-directx-project"></a><span data-ttu-id="bb596-104">Holographic DirectX プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="bb596-104">Creating a holographic DirectX project</span></span>

<span data-ttu-id="bb596-105">HoloLens を作成する holographic アプリ、<a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">ユニバーサル Windows プラットフォーム (UWP) アプリ</a>します。</span><span class="sxs-lookup"><span data-stu-id="bb596-105">A holographic app you create for a HoloLens will be a <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">Universal Windows Platform (UWP) app</a>.</span></span>  <span data-ttu-id="bb596-106">デスクトップの Windows Mixed Reality ヘッドセットを対象とする場合は、UWP アプリまたは Win32 アプリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="bb596-106">If targeting desktop Windows Mixed Reality headsets, you can create a UWP app or a Win32 app.</span></span>

<span data-ttu-id="bb596-107">DirectX 11 holographic UWP アプリ テンプレートとよく似ています、DirectX 11 の UWP アプリ テンプレートこれはプログラム ループ (または「ゲーム ループ」) が含まれます。、 **DeviceResources** Direct3D デバイスと、コンテキストを管理するクラスと簡略化されたコンテンツ レンダラー クラス。</span><span class="sxs-lookup"><span data-stu-id="bb596-107">The DirectX 11 holographic UWP app template is much like the DirectX 11 UWP app template; it includes a program loop (or "game loop"), a **DeviceResources** class to manage the Direct3D device and context, and a simplified content renderer class.</span></span> <span data-ttu-id="bb596-108">また、 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>他の UWP アプリと同様、します。</span><span class="sxs-lookup"><span data-stu-id="bb596-108">It also has an <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, just like any other UWP app.</span></span>

<span data-ttu-id="bb596-109">Mixed reality アプリには、一般的な Direct3D 11 の UWP アプリではないいくつかの追加機能ただしがあります。</span><span class="sxs-lookup"><span data-stu-id="bb596-109">The mixed reality app, however, has some additional capabilities that aren't present in a typical Direct3D 11 UWP app.</span></span> <span data-ttu-id="bb596-110">Windows Holographic のアプリ テンプレートができます。</span><span class="sxs-lookup"><span data-stu-id="bb596-110">The Windows Holographic app template is able to:</span></span>
* <span data-ttu-id="bb596-111">Holographic カメラに関連付けられている Direct3D デバイス リソースを処理します。</span><span class="sxs-lookup"><span data-stu-id="bb596-111">Handle Direct3D device resources associated with holographic cameras.</span></span>
* <span data-ttu-id="bb596-112">システムからカメラのバック バッファーを取得します。</span><span class="sxs-lookup"><span data-stu-id="bb596-112">Retrieve camera back buffers from the system.</span></span>
* <span data-ttu-id="bb596-113">処理[視線](gaze.md)入力、および単純な認識[ジェスチャ](gestures.md)します。</span><span class="sxs-lookup"><span data-stu-id="bb596-113">Handle [gaze](gaze.md) input, and recognize a simple [gesture](gestures.md).</span></span>
* <span data-ttu-id="bb596-114">ステレオのレンダリングを全画面表示モードに移動します。</span><span class="sxs-lookup"><span data-stu-id="bb596-114">Go into full-screen stereo rendering mode.</span></span>

## <a name="how-do-i-get-started"></a><span data-ttu-id="bb596-115">どのように始めればよいですか。</span><span class="sxs-lookup"><span data-stu-id="bb596-115">How do I get started?</span></span>

<span data-ttu-id="bb596-116">最初[ツールをインストールする](install-the-tools.md)、次の Visual Studio 2017 のダウンロードについてと Microsoft HoloLens のエミュレーター。</span><span class="sxs-lookup"><span data-stu-id="bb596-116">First [install the tools](install-the-tools.md), following the instructions on downloading Visual Studio 2017 and the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="bb596-117">Microsoft HoloLens のエミュレーターと同じインストーラーには、holographic アプリ テンプレートが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb596-117">The holographic app templates are included in the same installer as the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="bb596-118">また、インストールする前に、テンプレートをインストールするオプションが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb596-118">Also ensure that the option to install the templates is selected before installing.</span></span>

<span data-ttu-id="bb596-119">これで、DirectX 11 Windows Mixed Reality アプリを作成する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="bb596-119">Now you're ready to create your DirectX 11 Windows Mixed Reality app!</span></span> <span data-ttu-id="bb596-120">ただし、サンプルの内容を削除するには、コメント アウト、 **DRAW_SAMPLE_CONTENT**プリプロセッサ ディレクティブで*pch.h*。</span><span class="sxs-lookup"><span data-stu-id="bb596-120">Note, to remove the sample content, comment out the **DRAW_SAMPLE_CONTENT** preprocessor directive in *pch.h*.</span></span>

## <a name="creating-a-uwp-project"></a><span data-ttu-id="bb596-121">UWP プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="bb596-121">Creating a UWP project</span></span>

<span data-ttu-id="bb596-122">1 回、[ツールがインストールされている](install-the-tools.md)holographic DirectX UWP プロジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="bb596-122">Once the [tools are installed](install-the-tools.md) you can then create a holographic DirectX UWP project.</span></span>

<span data-ttu-id="bb596-123">新しいプロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="bb596-123">To create a new project:</span></span>
1. <span data-ttu-id="bb596-124">開始**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="bb596-124">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="bb596-125">**ファイル**メニューで、**新規**選択**プロジェクト**コンテキスト メニュー。</span><span class="sxs-lookup"><span data-stu-id="bb596-125">From the **File** menu, point to **New** and select **Project** from the context menu.</span></span> <span data-ttu-id="bb596-126">**新しいプロジェクト**ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="bb596-126">The **New Project** dialog opens.</span></span>
3. <span data-ttu-id="bb596-127">展開**インストール済み**左側を展開し、 **Visual C++** 言語ノード。</span><span class="sxs-lookup"><span data-stu-id="bb596-127">Expand **Installed** on the left and expand the **Visual C++** language node.</span></span>
4. <span data-ttu-id="bb596-128">移動し、 **Windows ユニバーサル > Holographic**ノード**Holographic DirectX 11 アプリ (ユニバーサル Windows) (C++/WinRT)** します。</span><span class="sxs-lookup"><span data-stu-id="bb596-128">Navigate to the **Windows Universal > Holographic** node and select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   <span data-ttu-id="bb596-129">![Holographic の DirectX 11 のスクリーン ショットC++Visual Studio での WinRT UWP アプリ プロジェクト テンプレート](images/holographic-directx-app-cpp-new-project.png)</span><span class="sxs-lookup"><span data-stu-id="bb596-129">![Screenshot of the Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio](images/holographic-directx-app-cpp-new-project.png)</span></span><br>
   <span data-ttu-id="bb596-130">*DirectX 11 の holographic C++Visual Studio での WinRT UWP アプリ プロジェクト テンプレート*</span><span class="sxs-lookup"><span data-stu-id="bb596-130">*Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="bb596-131">プロジェクト テンプレートの名前が含まれているかどうかを必ず"(C++/WinRT)"。</span><span class="sxs-lookup"><span data-stu-id="bb596-131">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="bb596-132">有効でない場合は、以前のバージョンのインストールされている holographic プロジェクト テンプレートがあります。</span><span class="sxs-lookup"><span data-stu-id="bb596-132">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="bb596-133">最新のプロジェクト テンプレートを取得する[最新 HoloLens のエミュレーターをインストール](using-the-hololens-emulator.md)します。</span><span class="sxs-lookup"><span data-stu-id="bb596-133">To get the latest project templates, [install the latest HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
5. <span data-ttu-id="bb596-134">入力、**名前**と**場所**テキスト ボックス、およびクリックまたはタップします**OK**。</span><span class="sxs-lookup"><span data-stu-id="bb596-134">Fill in the **Name** and **Location** text boxes, and click or tap **OK**.</span></span> <span data-ttu-id="bb596-135">Holographic アプリ プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bb596-135">The holographic app project is created.</span></span>
6. <span data-ttu-id="bb596-136">開発のため、HoloLens 2 のみを対象とすることを確認、**ターゲット バージョン**と**最小バージョン**に設定されている**Windows 10、バージョンが 1903**。</span><span class="sxs-lookup"><span data-stu-id="bb596-136">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="bb596-137">HoloLens も対象とする場合 (第 1 世代) 設定するデスクトップの Windows Mixed Reality ヘッドセットまたは**最小バージョン**に**Windows 10、バージョンは 1809**代わりに、いくつかが必要ですが<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">バージョン アダプティブ チェック</a>HoloLens 2 の新機能を使用する場合、コードにします。</span><span class="sxs-lookup"><span data-stu-id="bb596-137">If you are also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809** instead, although this will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adaptive checks</a> in your code when using new features of HoloLens 2.</span></span>
   <span data-ttu-id="bb596-138">![Windows 10 バージョン 1903 ターゲットと最小バージョンとしての設定のスクリーン ショット](images/new-uwp-project.png)</span><span class="sxs-lookup"><span data-stu-id="bb596-138">![Screenshot of setting Windows 10, version 1903 as the target and minimum versions](images/new-uwp-project.png)</span></span><br>
   <span data-ttu-id="bb596-139">*設定**Windows 10、バージョンが 1903**ターゲットと最小バージョンとして*</span><span class="sxs-lookup"><span data-stu-id="bb596-139">*Setting **Windows 10, version 1903** as the target and minimum versions*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="bb596-140">表示されない場合**Windows 10、バージョンが 1903**オプションとしてがない最新の Windows 10 SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bb596-140">If you do not see **Windows 10, version 1903** as an option, you do not have the latest Windows 10 SDK installed.</span></span>  <span data-ttu-id="bb596-141">表示するには、このオプションを取得する<a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">10.0.18362.0 のバージョンをインストールまたはそれ以降、Windows 10 SDK の</a>します。</span><span class="sxs-lookup"><span data-stu-id="bb596-141">To get this option to appear, <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">install version 10.0.18362.0 or later of the Windows 10 SDK</a>.</span></span>

<span data-ttu-id="bb596-142">テンプレートを使用してプロジェクトを生成する<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>、標準に準拠した c++ 17 コンパイラをサポートする Windows ランタイム Api の c++ 17 の言語プロジェクションです。</span><span class="sxs-lookup"><span data-stu-id="bb596-142">The template generates a project using <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="bb596-143">プロジェクトでは、ユーザーからの 2 つのメーターが配置される世界ロックされているキューブを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bb596-143">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="bb596-144">ユーザーは[エア タップ](gestures.md#air-tap)でユーザーの指定された別の位置に、キューブを配置するコント ローラーのボタンを押してまたは[視線](gaze.md)します。</span><span class="sxs-lookup"><span data-stu-id="bb596-144">The user can [air-tap](gestures.md#air-tap) or press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="bb596-145">すべての複合現実アプリを作成するには、このプロジェクトを変更できます。</span><span class="sxs-lookup"><span data-stu-id="bb596-145">You can modify this project to create any mixed reality app.</span></span>

<span data-ttu-id="bb596-146">使用して新しいプロジェクトを作成する代わりに、 **Visual C#**  holographic プロジェクト テンプレート、SharpDX に基づいています。</span><span class="sxs-lookup"><span data-stu-id="bb596-146">Alternatively, you can create a new project using the **Visual C#** holographic project template, which is based on SharpDX.</span></span>  <span data-ttu-id="bb596-147">場合、holographic C# Windows Holographic のアプリ テンプレートからプロジェクトは開始されませんでした、Windows Mixed Reality から ms.fxcompile.targets ファイルをコピーする必要がありますC#HLSL をコンパイルするためにファイルで、.csproj プロジェクト テンプレートとインポートプロジェクトに追加するファイル。</span><span class="sxs-lookup"><span data-stu-id="bb596-147">If your holographic C# project did not start from the Windows Holographic app template, you will need to copy the ms.fxcompile.targets file from a Windows Mixed Reality C# template project and import it in your .csproj file in order to compile HLSL files that you add to your project.</span></span>

<span data-ttu-id="bb596-148">レビュー[を配置およびデバッグ Visual Studio を使用して](using-visual-studio.md)構築し、HoloLens、PC に接続されている、没入型のデバイスまたはエミュレーターにデプロイする方法についてはします。</span><span class="sxs-lookup"><span data-stu-id="bb596-148">Review [Using Visual Studio to deploy and debug](using-visual-studio.md) for information on how to build and deploy the sample to your HoloLens, PC with immersive device attached, or an emulator.</span></span>

<span data-ttu-id="bb596-149">以下の手順の残りの部分を使用するいると仮定してC++アプリをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="bb596-149">The rest of the instructions below will assume that you are using C++ to build your app.</span></span>

### <a name="uwp-app-entry-point"></a><span data-ttu-id="bb596-150">UWP アプリのエントリ ポイント</span><span class="sxs-lookup"><span data-stu-id="bb596-150">UWP app entry point</span></span>

<span data-ttu-id="bb596-151">Holographic UWP アプリケーションの起動時、 **wWinMain** AppView.cpp 内の関数。</span><span class="sxs-lookup"><span data-stu-id="bb596-151">Your holographic UWP app starts in the **wWinMain** function in AppView.cpp.</span></span> <span data-ttu-id="bb596-152">**WWinMain**関数は、アプリの作成<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>を開始し、 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a>とします。</span><span class="sxs-lookup"><span data-stu-id="bb596-152">The **wWinMain** function creates the app's <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> and starts the <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> with it.</span></span>

<span data-ttu-id="bb596-153">**AppView.cpp**:</span><span class="sxs-lookup"><span data-stu-id="bb596-153">From **AppView.cpp**:</span></span>

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

<span data-ttu-id="bb596-154">その時点からは、AppView クラスは、Windows の基本的な入力イベント、CoreWindow イベント メッセージング、およびなどとの対話を処理します。</span><span class="sxs-lookup"><span data-stu-id="bb596-154">From that point on, the AppView class handles interaction with Windows basic input events, CoreWindow events and messaging, and so on.</span></span> <span data-ttu-id="bb596-155">アプリで使用される HolographicSpace も作成されます。</span><span class="sxs-lookup"><span data-stu-id="bb596-155">It will also create the HolographicSpace used by your app.</span></span>

## <a name="creating-a-win32-project"></a><span data-ttu-id="bb596-156">Win32 プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="bb596-156">Creating a Win32 project</span></span>

<span data-ttu-id="bb596-157">適応 holographic プロジェクトは、Win32 の構築を開始する最も簡単な方法、 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 サンプル</a>します。</span><span class="sxs-lookup"><span data-stu-id="bb596-157">The easiest way to get started building a Win32 holographic project is to adapt the <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">*BasicHologram* Win32 sample</a>.</span></span>

<span data-ttu-id="bb596-158">この Win32 サンプルを使用して<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>、標準に準拠した c++ 17 コンパイラをサポートする Windows ランタイム Api の c++ 17 の言語プロジェクションです。</span><span class="sxs-lookup"><span data-stu-id="bb596-158">This Win32 sample uses <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="bb596-159">プロジェクトでは、ユーザーからの 2 つのメーターが配置される世界ロックされているキューブを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bb596-159">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="bb596-160">ユーザーがユーザーによって指定されている別の位置に、キューブを配置するコント ローラーのボタンを押す[視線](gaze.md)します。</span><span class="sxs-lookup"><span data-stu-id="bb596-160">The user can press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="bb596-161">すべての複合現実アプリを作成するには、このプロジェクトを変更できます。</span><span class="sxs-lookup"><span data-stu-id="bb596-161">You can modify this project to create any mixed reality app.</span></span>

### <a name="win32-app-entry-point"></a><span data-ttu-id="bb596-162">Win32 アプリのエントリ ポイント</span><span class="sxs-lookup"><span data-stu-id="bb596-162">Win32 app entry point</span></span>

<span data-ttu-id="bb596-163">Holographic Win32 アプリケーションの起動時、 **wWinMain** AppMain.cpp 内の関数。</span><span class="sxs-lookup"><span data-stu-id="bb596-163">Your holographic Win32 app starts in the **wWinMain** function in AppMain.cpp.</span></span> <span data-ttu-id="bb596-164">**WWinMain**関数し、メッセージ ループを開始するアプリケーションの HWND を作成します。</span><span class="sxs-lookup"><span data-stu-id="bb596-164">The **wWinMain** function creates the app's HWND and starts its message loop.</span></span>

<span data-ttu-id="bb596-165">**AppMain.cpp**:</span><span class="sxs-lookup"><span data-stu-id="bb596-165">From **AppMain.cpp**:</span></span>

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

<span data-ttu-id="bb596-166">その時点からは、AppMain クラスは、基本的なウィンドウのメッセージとの対話を処理します。</span><span class="sxs-lookup"><span data-stu-id="bb596-166">From that point on, the AppMain class handles interaction with basic window messages, and so on.</span></span> <span data-ttu-id="bb596-167">アプリで使用される HolographicSpace も作成されます。</span><span class="sxs-lookup"><span data-stu-id="bb596-167">It will also create the HolographicSpace used by your app.</span></span>

## <a name="render-holographic-content"></a><span data-ttu-id="bb596-168">Holographic のコンテンツをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="bb596-168">Render holographic content</span></span>

<span data-ttu-id="bb596-169">プロジェクトの**コンテンツ**フォルダーにはでレンダリング ホログラム用のクラスが含まれています、 [holographic 領域](getting-a-holographicspace.md)します。</span><span class="sxs-lookup"><span data-stu-id="bb596-169">The project's **Content** folder contains classes for rendering holograms in the [holographic space](getting-a-holographicspace.md).</span></span> <span data-ttu-id="bb596-170">テンプレートの既定ホログラムは、ユーザーからの 2 つのメーターが配置される、回転するキューブです。</span><span class="sxs-lookup"><span data-stu-id="bb596-170">The default hologram in the template is a spinning cube that's placed two meters away from the user.</span></span> <span data-ttu-id="bb596-171">このキューブの描画では実装されて**SpinningCubeRenderer.cpp**がこれらの主要メソッド。</span><span class="sxs-lookup"><span data-stu-id="bb596-171">Drawing this cube is implemented in **SpinningCubeRenderer.cpp**, which has these key methods:</span></span>

|  <span data-ttu-id="bb596-172">メソッド</span><span class="sxs-lookup"><span data-stu-id="bb596-172">Method</span></span>  |  <span data-ttu-id="bb596-173">説明</span><span class="sxs-lookup"><span data-stu-id="bb596-173">Explanation</span></span> | 
|----------|----------|
|  `CreateDeviceDependentResources` |  <span data-ttu-id="bb596-174">シェーダーの読み込みをキューブのメッシュを作成します。</span><span class="sxs-lookup"><span data-stu-id="bb596-174">Loads shaders and creates the cube mesh.</span></span> | 
|  `PositionHologram` |  <span data-ttu-id="bb596-175">提供されている指定された位置に、ホログラムが配置<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>します。</span><span class="sxs-lookup"><span data-stu-id="bb596-175">Places the hologram at the location specified by the provided <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span></span> | 
|  `Update` |  <span data-ttu-id="bb596-176">キューブを回転し、モデルの行列を設定します。</span><span class="sxs-lookup"><span data-stu-id="bb596-176">Rotates the cube, and sets the model matrix.</span></span> | 
|  `Render` |  <span data-ttu-id="bb596-177">頂点とピクセル シェーダーを使用してフレームをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="bb596-177">Renders a frame using the vertex and pixel shaders.</span></span> | 

<span data-ttu-id="bb596-178">**シェーダー**サブフォルダーには、次の 4 つの既定のシェーダー実装が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bb596-178">The **Shaders** subfolder contains four default shader implementations:</span></span>

|  <span data-ttu-id="bb596-179">シェーダー</span><span class="sxs-lookup"><span data-stu-id="bb596-179">Shader</span></span>  |  <span data-ttu-id="bb596-180">説明</span><span class="sxs-lookup"><span data-stu-id="bb596-180">Explanation</span></span> | 
|----------|----------|
|  `GeometryShader.hlsl` |  <span data-ttu-id="bb596-181">変更されていないジオメトリをパススルーします。</span><span class="sxs-lookup"><span data-stu-id="bb596-181">A pass-through that leaves the geometry unmodified.</span></span> | 
|  `PixelShader.hlsl` |  <span data-ttu-id="bb596-182">データの色を通過します。</span><span class="sxs-lookup"><span data-stu-id="bb596-182">Passes through the color data.</span></span> <span data-ttu-id="bb596-183">色のデータが補間し、ラスタライズ ステップでピクセルに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="bb596-183">The color data is interpolated and assigned to a pixel at the rasterization step.</span></span> | 
|  `VertexShader.hlsl` |  <span data-ttu-id="bb596-184">GPU で頂点処理を行う単純なシェーダー。</span><span class="sxs-lookup"><span data-stu-id="bb596-184">Simple shader to do vertex processing on the GPU.</span></span> | 
|  `VPRTVertexShader.hlsl` |  <span data-ttu-id="bb596-185">Windows Mixed Reality ステレオ レンダリング用に最適化された GPU で頂点処理を行う単純なシェーダー。</span><span class="sxs-lookup"><span data-stu-id="bb596-185">Simple shader to do vertex processing on the GPU, that is optimized for Windows Mixed Reality stereo rendering.</span></span> | 

<span data-ttu-id="bb596-186">`VertexShaderShared.hlsl` 間で共有される共通のコードを含む`VertexShader.hlsl`と`VPRTVertexShader.hlsl`します。</span><span class="sxs-lookup"><span data-stu-id="bb596-186">`VertexShaderShared.hlsl` contains common code shared between `VertexShader.hlsl` and `VPRTVertexShader.hlsl`.</span></span>

<span data-ttu-id="bb596-187">プロジェクトをビルドするとで読み込まれているときに、シェーダーがコンパイルされる、 **SpinningCubeRenderer::CreateDeviceDependentResources**メソッド。</span><span class="sxs-lookup"><span data-stu-id="bb596-187">The shaders are compiled when the project is built, and they're loaded in the **SpinningCubeRenderer::CreateDeviceDependentResources** method.</span></span>

## <a name="interact-with-your-holograms"></a><span data-ttu-id="bb596-188">ホログラムとの対話します。</span><span class="sxs-lookup"><span data-stu-id="bb596-188">Interact with your holograms</span></span>

<span data-ttu-id="bb596-189">ユーザー入力の処理で、 **SpatialInputHandler**クラスを取得、 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a>インスタンスし、サブスクライブする、 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a>イベント。</span><span class="sxs-lookup"><span data-stu-id="bb596-189">User input is processed in the **SpatialInputHandler** class, which gets a <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> instance and subscribes to the <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> event.</span></span> <span data-ttu-id="bb596-190">これにより、エア タップ ジェスチャとその他の空間の入力イベントを検出できます。</span><span class="sxs-lookup"><span data-stu-id="bb596-190">This enables detecting the air-tap gesture and other spatial input events.</span></span>

## <a name="update-holographic-content"></a><span data-ttu-id="bb596-191">Holographic のコンテンツを更新します。</span><span class="sxs-lookup"><span data-stu-id="bb596-191">Update holographic content</span></span>

<span data-ttu-id="bb596-192">既定で実装されているゲームのループで、複合現実アプリの更新プログラム、 **Update**メソッド`AppMain.cpp`します。</span><span class="sxs-lookup"><span data-stu-id="bb596-192">Your mixed reality app updates in a game loop, which by default is implemented in the **Update** method in `AppMain.cpp`.</span></span> <span data-ttu-id="bb596-193">**Update**メソッドは、回転するキューブのように、シーンのオブジェクトを更新しを返します、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>を最新の状態の表示および投影マトリックスを取得し、スワップ チェーンを表示するに使用されるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bb596-193">The **Update** method updates scene objects, like the spinning cube, and returns a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> object that is used to get up-to-date view and projection matrices and to present the swap chain.</span></span>

<span data-ttu-id="bb596-194">**レンダリング**メソッド`AppMain.cpp`は、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>し、現在のアプリと空間配置の状態に従って各 holographic カメラの現在のフレームをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="bb596-194">The **Render** method in `AppMain.cpp` takes the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> and renders the current frame to each holographic camera, according to the current app and spatial positioning state.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb596-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb596-195">See also</span></span>
* [<span data-ttu-id="bb596-196">HolographicSpace を入手する</span><span class="sxs-lookup"><span data-stu-id="bb596-196">Getting a HolographicSpace</span></span>](getting-a-holographicspace.md)
* <span data-ttu-id="bb596-197"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span><span class="sxs-lookup"><span data-stu-id="bb596-197"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span></span>
* [<span data-ttu-id="bb596-198">DirectX でのレンダリング</span><span class="sxs-lookup"><span data-stu-id="bb596-198">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="bb596-199">Visual Studio を使用してデプロイおよびデバッグする</span><span class="sxs-lookup"><span data-stu-id="bb596-199">Using Visual Studio to deploy and debug</span></span>](using-visual-studio.md)
* [<span data-ttu-id="bb596-200">HoloLens のエミュレーターを使用する</span><span class="sxs-lookup"><span data-stu-id="bb596-200">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="bb596-201">XAML とホログラフィック DirectX アプリの使用</span><span class="sxs-lookup"><span data-stu-id="bb596-201">Using XAML with holographic DirectX apps</span></span>](using-xaml-with-holographic-directx-apps.md)
