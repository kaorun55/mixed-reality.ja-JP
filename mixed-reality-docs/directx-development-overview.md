---
title: DirectX の開発の概要
description: Windows Mixed Reality Api を直接使用複合現実の DirectX ベース エンジンを構築します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX、holographic レンダリング、ネイティブなネイティブ アプリ、WinRT、WinRT アプリでは、プラットフォーム Api、カスタム エンジンは、ミドルウェア
ms.openlocfilehash: da6beae6e256fef49481b581395e507b3f2acd04
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414381"
---
# <a name="directx-development-overview"></a><span data-ttu-id="9644f-104">DirectX の開発の概要</span><span class="sxs-lookup"><span data-stu-id="9644f-104">DirectX development overview</span></span>


<span data-ttu-id="9644f-105">Windows Mixed Reality アプリケーションを使用して、 [holographic レンダリング](rendering.md)、[視線](gaze.md)、[ジェスチャ](gestures.md)、[モーションのコント ローラー](motion-controllers.md)、 [音声](voice-input.md)と[空間マッピング](spatial-mapping.md)Api を構築する[複合現実](mixed-reality.md)HoloLens とイマーシブ ヘッドセットで発生します。</span><span class="sxs-lookup"><span data-stu-id="9644f-105">Windows Mixed Reality applications use the [holographic rendering](rendering.md), [gaze](gaze.md), [gesture](gestures.md), [motion controller](motion-controllers.md), [voice](voice-input.md), and [spatial mapping](spatial-mapping.md) APIs to build [mixed reality](mixed-reality.md) experiences for HoloLens and immersive headsets.</span></span> <span data-ttu-id="9644f-106">の 3D エンジンを使用して複合現実のアプリケーションを作成する[Unity](unity-development-overview.md)、または DirectX 11 または DirectX 12 を使用して Windows 混合現実 Api に対して直接コーディングすることができます。</span><span class="sxs-lookup"><span data-stu-id="9644f-106">You can create mixed reality applications using a 3D engine, such as [Unity](unity-development-overview.md), or you can directly code to the Windows Mixed Reality APIs using DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="9644f-107">場合は、プラットフォームを直接活用している、本質的に作成する独自のミドルウェアまたはフレームワーク。</span><span class="sxs-lookup"><span data-stu-id="9644f-107">If you are leveraging the platform directly, you'll essentially be building your own middleware or framework.</span></span> <span data-ttu-id="9644f-108">Windows Api サポートの両方で記述されたアプリケーションC++とC#します。</span><span class="sxs-lookup"><span data-stu-id="9644f-108">The Windows APIs support applications written in both C++ and C#.</span></span> <span data-ttu-id="9644f-109">使用する場合C#をアプリケーションを利用することができます、 [SharpDX](http://sharpdx.org/)オープン ソース ソフトウェア ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="9644f-109">If you choose to use C#, your application can leverage the [SharpDX](http://sharpdx.org/) open source software library.</span></span>


<span data-ttu-id="9644f-110">Windows Mixed Reality サポート[2 つの種類のアプリ](app-views.md):</span><span class="sxs-lookup"><span data-stu-id="9644f-110">Windows Mixed Reality supports [two kinds of apps](app-views.md):</span></span>
* <span data-ttu-id="9644f-111">**実際のアプリケーションを混合**(UWP または Win32) を使用する、 [HolographicSpace API](getting-a-holographicspace.md)表示するために、[没入型のビュー](app-views.md)ヘッドセット表示の入力をユーザーにします。</span><span class="sxs-lookup"><span data-stu-id="9644f-111">**Mixed reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) to render an [immersive view](app-views.md) to the user that fills the headset display.</span></span>
* <span data-ttu-id="9644f-112">**2D アプリ**(UWP) を使用して、DirectX、XAML、またはその他のフレームワークをレンダリングする[2D ビュー](app-views.md#2d-views)ホーム Windows Mixed Reality でスレートをします。</span><span class="sxs-lookup"><span data-stu-id="9644f-112">**2D apps** (UWP) that use DirectX, XAML, or other frameworks to render [2D views](app-views.md#2d-views) on slates in the Windows Mixed Reality home.</span></span>


<span data-ttu-id="9644f-113">DirectX の開発の間の相違点[2D のビューとビューの没入型](app-views.md)holographic に関連するレンダリングと空間的な入力は、主にします。</span><span class="sxs-lookup"><span data-stu-id="9644f-113">The differences between DirectX development for [2D views and immersive views](app-views.md) are primarily related to holographic rendering and spatial input.</span></span> <span data-ttu-id="9644f-114">UWP アプリケーションの[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)または Win32 アプリケーションの HWND が必要なままとほとんど同じですが、アプリケーションで利用できる WinRT Api と同様です。</span><span class="sxs-lookup"><span data-stu-id="9644f-114">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required, and remain largely the same, as do the WinRT APIs available to your application.</span></span> <span data-ttu-id="9644f-115">ただし、holographic の機能を活用するために、これらの Api のさまざまなサブセットを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9644f-115">However, you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="9644f-116">たとえば、スワップ チェーンは、holographic appslications のシステムによって管理されます。</span><span class="sxs-lookup"><span data-stu-id="9644f-116">For example, the swap chain is managed by the system for holographic appslications.</span></span> <span data-ttu-id="9644f-117">DXGI にではなく、HolographicSpace API を使用する[フレームを提示](rendering-in-directx.md)します。</span><span class="sxs-lookup"><span data-stu-id="9644f-117">You work with the HolographicSpace API rather than DXGI to [present frames](rendering-in-directx.md).</span></span>

<span data-ttu-id="9644f-118">没入型アプリケーションを開発するには。</span><span class="sxs-lookup"><span data-stu-id="9644f-118">To begin developing immersive applications:</span></span>
* <span data-ttu-id="9644f-119">**UWP アプリ**、 [Visual Studio でテンプレートを使用して新しい UWP プロジェクトを作成する](creating-a-holographic-directx-project.md)します。</span><span class="sxs-lookup"><span data-stu-id="9644f-119">For **UWP apps**, [create a new UWP project using the templates in Visual Studio](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="9644f-120">言語に基づく**Visual C++** または**Visual C#** で UWP テンプレートを見つける**Windows ユニバーサル** >  **Holographic**します。</span><span class="sxs-lookup"><span data-stu-id="9644f-120">Based on your language, **Visual C++** or **Visual C#**, you can find the UWP templates under **Windows Universal** > **Holographic**.</span></span>
* <span data-ttu-id="9644f-121">**Win32 アプリケーション**、[からを起動、 *BasicHologram* Win32 サンプル](creating-a-holographic-directx-project.md#creating-a-win32-project)します。</span><span class="sxs-lookup"><span data-stu-id="9644f-121">For **Win32 applications**, [start from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project).</span></span>

<span data-ttu-id="9644f-122">これは、既存のアプリケーションまたはエンジンに holographic のレンダリングのサポートを追加する必要のあるコードを取得する優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="9644f-122">This is a great way to get the code that you need to add holographic rendering support to an existing application or engine.</span></span> <span data-ttu-id="9644f-123">リアルタイムの対話型ソフトウェアの開発者にとってなじみのある方法で、テンプレートでは、コードと概念が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9644f-123">Code and concepts are presented in the template in a way that's familiar to any developer of real-time interactive software.</span></span>


## <a name="getting-started"></a><span data-ttu-id="9644f-124">概要</span><span class="sxs-lookup"><span data-stu-id="9644f-124">Getting started</span></span>

<span data-ttu-id="9644f-125">次のトピックでは、DirectX ベースのミドルウェアに Windows Mixed Reality サポートを追加する基本的な要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="9644f-125">The following topics discuss the base requirements of adding Windows Mixed Reality support to DirectX-based middleware:</span></span>

* <span data-ttu-id="9644f-126">[Holographic DirectX プロジェクトを作成する](creating-a-holographic-directx-project.md):ドキュメントと組み合わせて、holographic アプリケーション テンプレートを使用しているだけでなく、頭の上に、動作するように設計がデバイスによって導入された特別な要件の違いを示します。</span><span class="sxs-lookup"><span data-stu-id="9644f-126">[Creating a holographic DirectX project](creating-a-holographic-directx-project.md): The holographic application template coupled with the documentation shows you the differences between what you're used to as well as the special requirements introduced by a device that's designed to function while resting on your head.</span></span>
* <span data-ttu-id="9644f-127">[取得、HolographicSpace](getting-a-holographicspace.md):最初に、アプリケーションにレンダリングするが各ヘッドの位置を表す HolographicFrame オブジェクトのシーケンスを提供する HolographicSpace を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9644f-127">[Getting a HolographicSpace](getting-a-holographicspace.md): You'll first need to create a HolographicSpace That will provide your application the sequence of HolographicFrame objects that represent each head position from which you'll render.</span></span>
* <span data-ttu-id="9644f-128">[DirectX でレンダリング](rendering-in-directx.md):Holographic スワップ チェーンには、2 つのレンダー ターゲットがあるので、アプリケーションの表示方法にいくつかの変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="9644f-128">[Rendering in DirectX](rendering-in-directx.md): Since a holographic swap chain has two render targets, you'll need to make some changes to the way your application renders.</span></span>
* <span data-ttu-id="9644f-129">[DirectX の座標系](coordinate-systems-in-directx.md):Windows Mixed Reality は、学習し、更新プログラムのように、ユーザーの周囲を歩き、世界中の理解します。</span><span class="sxs-lookup"><span data-stu-id="9644f-129">[Coordinate systems in DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality learns and updates its understanding of the world as the user walks around.</span></span> <span data-ttu-id="9644f-130">これは、アプリケーション空間のアンカーを含むユーザーの環境について推論を使用して、ユーザーの空間ステージを定義する空間座標系を提供します。</span><span class="sxs-lookup"><span data-stu-id="9644f-130">This provides spatial coordinate systems that applications use to reason about the user's surroundings, including spatial anchors and the user's defined spatial stage.</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="9644f-131">複合現実の機能および入力の追加</span><span class="sxs-lookup"><span data-stu-id="9644f-131">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="9644f-132">没入型 appslication のユーザーの最良のエクスペリエンスを有効にするために、次のキー構成要素をサポートするために。</span><span class="sxs-lookup"><span data-stu-id="9644f-132">To enable the best possible experience for users of your immersive appslication, you'll want to support the following key building blocks:</span></span>

* [<span data-ttu-id="9644f-133">DirectX でのヘッド視線入力とアイ視線入力</span><span class="sxs-lookup"><span data-stu-id="9644f-133">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="9644f-134">DirectX での手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="9644f-134">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="9644f-135">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="9644f-135">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="9644f-136">DirectX の立体音響</span><span class="sxs-lookup"><span data-stu-id="9644f-136">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="9644f-137">DirectX の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="9644f-137">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)


<span data-ttu-id="9644f-138">その他の主要機能は、多くの没入型アプリケーションを使用する DirectX アプリケーションにも公開されているがあります。</span><span class="sxs-lookup"><span data-stu-id="9644f-138">There are other key features that many immersive applications will want to use that are also exposed to DirectX applicaitons:</span></span>

* [<span data-ttu-id="9644f-139">DirectX での共有された空間アンカー</span><span class="sxs-lookup"><span data-stu-id="9644f-139">Shared spatial anchors in DirectX</span></span>](shared-spatial-anchors-in-directx.md)
* [<span data-ttu-id="9644f-140">DirectX での場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="9644f-140">Locatable camera in DirectX</span></span>](locatable-camera-in-directx.md)
* [<span data-ttu-id="9644f-141">DirectX でのキーボード、マウス、およびコントローラー入力</span><span class="sxs-lookup"><span data-stu-id="9644f-141">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a><span data-ttu-id="9644f-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="9644f-142">See also</span></span>
* [<span data-ttu-id="9644f-143">アプリ モデル</span><span class="sxs-lookup"><span data-stu-id="9644f-143">App model</span></span>](app-model.md)
* [<span data-ttu-id="9644f-144">アプリ ビュー</span><span class="sxs-lookup"><span data-stu-id="9644f-144">App views</span></span>](app-views.md)
