---
title: ネイティブ開発の概要
description: Windows Mixed Reality Api を直接使用して、DirectX ベースの mixed reality エンジンをビルドします。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, holographic レンダリング, ネイティブ, ネイティブアプリ, WinRT, WinRT アプリ, プラットフォーム Api, カスタムエンジン, ミドルウェア
ms.openlocfilehash: 5c61739ea6c90b4547c5c9927cf2129304650926
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80159998"
---
# <a name="native-development-overview"></a><span data-ttu-id="5b194-104">ネイティブ開発の概要</span><span class="sxs-lookup"><span data-stu-id="5b194-104">Native development overview</span></span>

<span data-ttu-id="5b194-105">Windows Mixed Reality アプリケーションは、次の Api を使用して、HoloLens とその他のイマーシブヘッドセットの[Mixed Reality](mixed-reality.md)エクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="5b194-105">Windows Mixed Reality applications use the following APIs to build [mixed-reality](mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

 - [<span data-ttu-id="5b194-106">ホログラフィック レンダリング</span><span class="sxs-lookup"><span data-stu-id="5b194-106">Holographic rendering</span></span>](rendering.md)
 - [<span data-ttu-id="5b194-107">視線入力</span><span class="sxs-lookup"><span data-stu-id="5b194-107">Gaze</span></span>](gaze-and-commit.md)
 - [<span data-ttu-id="5b194-108">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="5b194-108">Gesture</span></span>](gaze-and-commit.md#composite-gestures)
 - [<span data-ttu-id="5b194-109">モーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="5b194-109">Motion controller</span></span>](motion-controllers.md)
 - [<span data-ttu-id="5b194-110">音声</span><span class="sxs-lookup"><span data-stu-id="5b194-110">Voice</span></span>](voice-input.md)
 - [<span data-ttu-id="5b194-111">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="5b194-111">Spatial mapping</span></span>](spatial-mapping.md)

<span data-ttu-id="5b194-112">[Unity](unity-development-overview.md)などの3d エンジンを使用して、mixed reality アプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="5b194-112">You can create mixed reality applications by using a 3D engine, such as [Unity](unity-development-overview.md).</span></span> <span data-ttu-id="5b194-113">または、DirectX 11 または DirectX 12 を使用して、Windows Mixed Reality Api に直接コードを記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="5b194-113">Or you can directly code to the Windows Mixed Reality APIs by using DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="5b194-114">プラットフォームを直接利用する場合は、基本的に独自のミドルウェアまたはフレームワークを構築します。</span><span class="sxs-lookup"><span data-stu-id="5b194-114">If you leverage the platform directly, you essentially build your own middleware or framework.</span></span> <span data-ttu-id="5b194-115">Windows Api は、とC++ C#の両方で記述されたアプリケーションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="5b194-115">The Windows APIs support applications that are written in both C++ and C#.</span></span> <span data-ttu-id="5b194-116">を使用C#する場合、アプリケーションは[SharpDX](https://sharpdx.org/)オープンソースソフトウェアライブラリを利用できます。</span><span class="sxs-lookup"><span data-stu-id="5b194-116">If you use C#, your application can leverage the [SharpDX](https://sharpdx.org/) open source software library.</span></span>

<span data-ttu-id="5b194-117">Windows Mixed Reality は[、次の2種類のアプリを](app-views.md)サポートしています。</span><span class="sxs-lookup"><span data-stu-id="5b194-117">Windows Mixed Reality supports [two kinds of apps](app-views.md):</span></span>
* <span data-ttu-id="5b194-118">[HOLOGRAPHICSPACE api](getting-a-holographicspace.md)または[OpenXR api](openxr.md)を使用して、ヘッドセットの表示を満たすユーザーに[イマーシブビュー](app-views.md)をレンダリングする**Mixed reality アプリケーション**(UWP または Win32)</span><span class="sxs-lookup"><span data-stu-id="5b194-118">**Mixed-reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](app-views.md) to the user that fills the headset display</span></span>
* <span data-ttu-id="5b194-119">DirectX、XAML、または別のフレームワークを使用して、Windows Mixed Reality ホームのスレートに[2d ビュー](app-views.md#2d-views)をレンダリングする**2d アプリ**(UWP)</span><span class="sxs-lookup"><span data-stu-id="5b194-119">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="5b194-120">[2d ビューとイマーシブビュー](app-views.md)の DirectX 開発の違いは、主に holographic のレンダリングと空間入力に関係しています。</span><span class="sxs-lookup"><span data-stu-id="5b194-120">The differences between DirectX development for [2D views and immersive views](app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="5b194-121">UWP アプリケーションの[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)または Win32 アプリケーションの HWND が必要であり、ほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="5b194-121">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="5b194-122">アプリで使用できる WinRT Api にも同じことが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="5b194-122">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="5b194-123">ただし、holographic 機能を利用するには、これらの Api の異なるサブセットを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b194-123">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="5b194-124">たとえば、存在するスワップチェーンと frame は、holographic アプリケーション用にシステムによって管理されます。これにより、予測可能なフレームループが有効になります。</span><span class="sxs-lookup"><span data-stu-id="5b194-124">For example, the swapchain and frame present is managed by the system for holographic applications in order to enable a pose-predicted frame loop.</span></span>

## <a name="get-started-with-openxr"></a><span data-ttu-id="5b194-125">OpenXR を使ってみる</span><span class="sxs-lookup"><span data-stu-id="5b194-125">Get started with OpenXR</span></span>

<span data-ttu-id="5b194-126">デスクトップ上の HoloLens 2 または Windows Mixed Reality の OpenXR を使用して開発することができます。</span><span class="sxs-lookup"><span data-stu-id="5b194-126">You can develop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset on the desktop.</span></span>  <span data-ttu-id="5b194-127">ヘッドセットへのアクセス権がない場合は、代わりに HoloLens 2 エミュレーターまたは Windows Mixed Reality シミュレーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5b194-127">If you don't have access to a headset, you can use the HoloLens 2 Emulator or the Windows Mixed Reality Simulator instead.</span></span>

<span data-ttu-id="5b194-128">HoloLens 2 またはイマーシブ Windows Mixed Reality ヘッドセットの OpenXR アプリケーションの開発を開始するには、「 [OpenXR development の使用を開始する方法](openxr-getting-started.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b194-128">To start developing OpenXR applications for HoloLens 2 or immersive Windows Mixed Reality headsets, see [how to get started with OpenXR development](openxr-getting-started.md).</span></span>

## <a name="get-started-with-winrt"></a><span data-ttu-id="5b194-129">WinRT を使ってみる</span><span class="sxs-lookup"><span data-stu-id="5b194-129">Get started with WinRT</span></span>

<span data-ttu-id="5b194-130">イマーシブアプリケーションの開発を開始するには:</span><span class="sxs-lookup"><span data-stu-id="5b194-130">To begin developing immersive applications:</span></span>
* <span data-ttu-id="5b194-131">**Uwp アプリ**の場合は、Visual Studio のテンプレートを使用して、[新しい UWP プロジェクトを作成](creating-a-holographic-directx-project.md)します。</span><span class="sxs-lookup"><span data-stu-id="5b194-131">For **UWP apps**, [use the templates in Visual Studio to create a new UWP project](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="5b194-132">お使いの言語、ビジュアルC++ 、またC#はビジュアルに基づいて、 **WINDOWS Universal** > **Holographic**の UWP テンプレートを見つけます。</span><span class="sxs-lookup"><span data-stu-id="5b194-132">Based on your language, Visual C++ or Visual C#, find the UWP templates under **Windows Universal** > **Holographic**.</span></span>
* <span data-ttu-id="5b194-133">**Win32 アプリケーション**の場合は、 [ *basichologram* Win32 サンプルから開始](creating-a-holographic-directx-project.md#creating-a-win32-project)します。</span><span class="sxs-lookup"><span data-stu-id="5b194-133">For **Win32 applications**, [start from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project).</span></span>

<span data-ttu-id="5b194-134">この手順は、既存のアプリケーションまたはエンジンに holographic のレンダリングサポートを追加するために必要なコードを取得するための優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="5b194-134">This step is a great way to get the code that you need to add holographic rendering support to an existing application or engine.</span></span> <span data-ttu-id="5b194-135">コードと概念は、リアルタイムの対話型ソフトウェアの開発者にとって使い慣れた方法でテンプレートに記載されています。</span><span class="sxs-lookup"><span data-stu-id="5b194-135">The code and concepts are presented in the template in a way that's familiar to any developer of real-time interactive software.</span></span>

<span data-ttu-id="5b194-136">次のトピックでは、Windows Mixed Reality サポートを DirectX ベースのミドルウェアに追加する際の基本要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="5b194-136">The following topics describe the base requirements when you add Windows Mixed Reality support to DirectX-based middleware.</span></span>

* <span data-ttu-id="5b194-137">[Holographic DirectX プロジェクトを作成](creating-a-holographic-directx-project.md)する: holographic アプリケーションテンプレートとドキュメントを組み合わせると、使用しているものと比較した場合の相違点が示されます。</span><span class="sxs-lookup"><span data-stu-id="5b194-137">[Create a holographic DirectX project](creating-a-holographic-directx-project.md): The holographic application template coupled with the documentation shows the differences compared to what you're used to.</span></span> <span data-ttu-id="5b194-138">また、ヘッドに置いて機能するように設計されているデバイスの特別な要件についても説明します。</span><span class="sxs-lookup"><span data-stu-id="5b194-138">It also describes the special requirements for a device that's designed to function while resting on your head.</span></span>
* <span data-ttu-id="5b194-139">[HolographicSpace の取得](getting-a-holographicspace.md): 最初に、レンダリングする各ヘッドの位置を表す HolographicFrame オブジェクトのシーケンスをアプリケーションに提供する HolographicSpace を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b194-139">[Get a HolographicSpace](getting-a-holographicspace.md): You first need to create a HolographicSpace that gives your application the sequence of HolographicFrame objects that represent each head position from which you'll render.</span></span>
* <span data-ttu-id="5b194-140">[DirectX でのレンダリング](rendering-in-directx.md): holographic スワップチェーンには2つのレンダーターゲットがあるため、アプリのレンダリング方法にいくつかの変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b194-140">[Render in DirectX](rendering-in-directx.md): Because a holographic swapchain has two render targets, you must make some changes to the way your app renders.</span></span>
* <span data-ttu-id="5b194-141">[DirectX でのシステムの調整](coordinate-systems-in-directx.md): Windows Mixed Reality は、ユーザーが説明しているとおりに世界の理解を深め、更新します。</span><span class="sxs-lookup"><span data-stu-id="5b194-141">[Coordinate systems in DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality learns and updates its understanding of the world as the user walks around.</span></span> <span data-ttu-id="5b194-142">これにより、空間アンカーやユーザーが定義した空間ステージなど、ユーザーの環境についての理由にアプリケーションが使用する空間座標系が提供されます。</span><span class="sxs-lookup"><span data-stu-id="5b194-142">This provides spatial coordinate systems that applications use to reason about the user's surroundings, including spatial anchors and the user's defined spatial stage.</span></span>

## <a name="add-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="5b194-143">Mixed reality の機能と入力を追加する</span><span class="sxs-lookup"><span data-stu-id="5b194-143">Add mixed reality capabilities and inputs</span></span>

<span data-ttu-id="5b194-144">イマーシブアプリのユーザーに最適なエクスペリエンスを提供するには、次の主要な構成要素をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b194-144">To provide the best possible experience for users of your immersive app, you should support the following key building blocks:</span></span>

* [<span data-ttu-id="5b194-145">DirectX でのヘッド視線入力とアイ視線入力</span><span class="sxs-lookup"><span data-stu-id="5b194-145">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="5b194-146">DirectX での手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="5b194-146">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="5b194-147">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="5b194-147">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="5b194-148">立体音響</span><span class="sxs-lookup"><span data-stu-id="5b194-148">Spatial sound</span></span>](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [<span data-ttu-id="5b194-149">DirectX の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="5b194-149">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)

<span data-ttu-id="5b194-150">これらは、多くのイマーシブアプリケーションが DirectX アプリケーションにも公開する主な機能です。</span><span class="sxs-lookup"><span data-stu-id="5b194-150">These are other key features that many immersive applications use that are also exposed to DirectX applications:</span></span>

* [<span data-ttu-id="5b194-151">DirectX での共有された空間アンカー</span><span class="sxs-lookup"><span data-stu-id="5b194-151">Shared spatial anchors in DirectX</span></span>](shared-spatial-anchors-in-directx.md)
* [<span data-ttu-id="5b194-152">DirectX でのキーボード、マウス、およびコントローラー入力</span><span class="sxs-lookup"><span data-stu-id="5b194-152">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard-mouse-and-controller-input-in-directx.md)

## <a name="see-also"></a><span data-ttu-id="5b194-153">参照</span><span class="sxs-lookup"><span data-stu-id="5b194-153">See also</span></span>
* [<span data-ttu-id="5b194-154">アプリ モデル</span><span class="sxs-lookup"><span data-stu-id="5b194-154">App model</span></span>](app-model.md)
* [<span data-ttu-id="5b194-155">アプリ ビュー</span><span class="sxs-lookup"><span data-stu-id="5b194-155">App views</span></span>](app-views.md)
