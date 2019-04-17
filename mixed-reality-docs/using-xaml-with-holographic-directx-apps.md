---
title: Holographic の DirectX アプリでの XAML の使用
description: 2D の XAML ビューと XAML ビューとビューの没入型の両方の効率的に使用する方法と、DirectX アプリで没入型のビューの切り替えの影響について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: windows mixed reality、UWP、アプリを表示、管理、xaml、キーボード チュートリアルでは、DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598684"
---
# <a name="using-xaml-with-holographic-directx-apps"></a><span data-ttu-id="04885-104">Holographic の DirectX アプリでの XAML の使用</span><span class="sxs-lookup"><span data-stu-id="04885-104">Using XAML with holographic DirectX apps</span></span>

<span data-ttu-id="04885-105">このトピックでは、間の切り替えの影響を説明します。 [2D の XAML ビューとビューの没入型](app-views.md)、DirectX アプリでの XAML ビューと没入型のビューの両方を効率的に使用する方法。</span><span class="sxs-lookup"><span data-stu-id="04885-105">This topic explains the impact of switching between [2D XAML views and immersive views](app-views.md) in your DirectX app, and how to make efficient use of both a XAML view and immersive view.</span></span>

## <a name="xaml-view-switching-overview"></a><span data-ttu-id="04885-106">XAML ビューの概要の切り替え</span><span class="sxs-lookup"><span data-stu-id="04885-106">XAML view switching overview</span></span>

<span data-ttu-id="04885-107">、HoloLens の通常没入型のアプリが 2D の XAML ビューを後で表示される場合はその XAML ビューを最初に初期化し、そこから、没入型のビューをすぐに切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="04885-107">On HoloLens, a generally immersive app that may later display a 2D XAML view must initialize that XAML view first and immediately switch to an immersive view from there.</span></span> <span data-ttu-id="04885-108">つまり、XAML は、アプリが操作を実行する前に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="04885-108">This means XAML will load before your app can do anything.</span></span> <span data-ttu-id="04885-109">その結果、起動時間を少し増やすがあり、XAML は引き続きバック グラウンド; であるときに、アプリのプロセスのメモリ領域を占有ネイティブ ビューに切り替える前に XAML は量起動時の遅延とメモリ使用量はどのようなアプリによって異なります。</span><span class="sxs-lookup"><span data-stu-id="04885-109">As a result, there will be a small increase in your startup time, and XAML will continue to occupy memory space in your app process while it resides in the background; the amount of startup delay and memory usage depends on what your app does with XAML before switching to the native view.</span></span> <span data-ttu-id="04885-110">Nothing は、XAML スタートアップ、没入型の表示の開始点を除いて、最初のコードでは、影響はマイナーになります。</span><span class="sxs-lookup"><span data-stu-id="04885-110">If you do nothing in your XAML start up code at first except start your immersive view, the impact should be minor.</span></span> <span data-ttu-id="04885-111">また、没入型のビューに直接、holographic、レンダリングが行われるために、そのレンダリングに XAML に関連する制限を適用が済みます。</span><span class="sxs-lookup"><span data-stu-id="04885-111">Also, because your holographic rendering is done directly to the immersive view, you will avoid any XAML-related restrictions on that rendering.</span></span>

<span data-ttu-id="04885-112">CPU と GPU の両方のメモリ使用量をカウントすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="04885-112">Note that the memory usage counts for both CPU and GPU.</span></span> <span data-ttu-id="04885-113">Direct3d11 が仮想のグラフィック メモリとスワップできるが、XAML の GPU のリソースの一部またはすべてを入れ替えることができない可能性があり、顕著なパフォーマンスに影響がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="04885-113">Direct3D 11 is able to swap virtual graphics memory, but it might not be able to swap out some or all of the XAML GPU resources, and there might be a noticeable performance hit.</span></span> <span data-ttu-id="04885-114">どちらの方法でも、XAML の機能が読み込まれていませんしない必要があります、アプリの複数の部屋のままにして優れたエクスペリエンスを実現します。</span><span class="sxs-lookup"><span data-stu-id="04885-114">Either way, not loading any XAML features you don't need will leave more room for your app and provide a better experience.</span></span>

## <a name="xaml-view-switching-workflow"></a><span data-ttu-id="04885-115">XAML ビューのワークフローの切り替え</span><span class="sxs-lookup"><span data-stu-id="04885-115">XAML view switching workflow</span></span>

<span data-ttu-id="04885-116">ワークフローがあるイマーシブ モードに XAML から直接移動するアプリのようになります。</span><span class="sxs-lookup"><span data-stu-id="04885-116">The workflow for an app that goes directly from XAML to immersive mode is like so:</span></span>
* <span data-ttu-id="04885-117">2D の XAML ビューで、アプリの起動時します。</span><span class="sxs-lookup"><span data-stu-id="04885-117">The app starts up in the 2D XAML view.</span></span>
* <span data-ttu-id="04885-118">アプリの XAML の起動シーケンスでは、現在のシステムが holographic のレンダリングをサポートしているかを検出します。</span><span class="sxs-lookup"><span data-stu-id="04885-118">The app’s XAML startup sequence detects if the current system supports holographic rendering:</span></span>
* <span data-ttu-id="04885-119">そうである場合、アプリは没入型のビューを作成し、すぐ、前面に表示します。</span><span class="sxs-lookup"><span data-stu-id="04885-119">If so, the app creates the immersive view and brings it to the foreground right away.</span></span> <span data-ttu-id="04885-120">レンダリング クラスおよび XAML ビューで読み込まれる資産を含む、Windows Mixed Reality デバイス上の何もないために必要な XAML 読み込みがスキップされます。</span><span class="sxs-lookup"><span data-stu-id="04885-120">XAML loading is skipped for anything not necessary on Windows Mixed Reality devices, including any rendering classes and asset loading in the XAML view.</span></span> <span data-ttu-id="04885-121">アプリはキーボード入力の XAML を使用している場合は、その入力ページを作成もする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04885-121">If the app is using XAML for keyboard input, that input page should still be created.</span></span>
* <span data-ttu-id="04885-122">それ以外の場合は、XAML ビューが通常どおりの業務を続行できます。</span><span class="sxs-lookup"><span data-stu-id="04885-122">If not, the XAML view can proceed with business as usual.</span></span>

## <a name="tip-for-rendering-graphics-across-both-views"></a><span data-ttu-id="04885-123">両方のビューで、グラフィックのレンダリングをヒントします。</span><span class="sxs-lookup"><span data-stu-id="04885-123">Tip for rendering graphics across both views</span></span>

<span data-ttu-id="04885-124">を、アプリが Windows Mixed Reality で XAML ビューの DirectX で一定のレンダリングを実装する必要がある場合、最善の方法では、両方のビューで動作する 1 つのレンダラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="04885-124">If your app needs to implement some amount of rendering in DirectX for the XAML view in Windows Mixed Reality, your best bet is to create one renderer that can work with both views.</span></span> <span data-ttu-id="04885-125">レンダラーが両方のビューからアクセスできる 1 つのインスタンスにする必要があり、2 D および holographic の表示を切り替えることができるようにします。</span><span class="sxs-lookup"><span data-stu-id="04885-125">The renderer should be one instance that can be accessed from both views, and it should be able to switch between 2D and holographic rendering.</span></span> <span data-ttu-id="04885-126">読み込み時間、メモリへの影響、およびビューを切り替えるときにスワップするリソースの量を減少この GPU 資産は 1 回のみ読み込むようにします。</span><span class="sxs-lookup"><span data-stu-id="04885-126">That way GPU assets are only loaded once - this reduces load times, memory impact, and the amount of resources to be swapped when switching views.</span></span>
