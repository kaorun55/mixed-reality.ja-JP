---
title: 1. はじめに
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 1
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: c16671fc8f4233378dafa646786df1f7b5ae18e1
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330169"
---
# <a name="1-getting-started"></a><span data-ttu-id="24054-104">1.はじめに</span><span class="sxs-lookup"><span data-stu-id="24054-104">1. Getting started</span></span>

<span data-ttu-id="24054-105">Mixed Reality を初めて使用する場合でも、経験豊富なプロの方でも、[HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) と [Unreal Engine](https://www.unrealengine.com/en-US/) を使用して体験を始めることができます。</span><span class="sxs-lookup"><span data-stu-id="24054-105">Whether you're new to mixed reality or a seasoned pro, this is the place to start your journey with [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/).</span></span> <span data-ttu-id="24054-106">このチュートリアル シリーズでは、[Unreal 用 Mixed Reality ツールキット](https://github.com/microsoft/MixedRealityToolkit-Unreal)の一部である [UX ツール プラグイン](https://github.com/microsoft/MixedReality-UXTools-Unreal)を使用してインタラクティブなチェス アプリを構築する方法をステップごとに説明します。</span><span class="sxs-lookup"><span data-stu-id="24054-106">This tutorial series will give you a step by step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="24054-107">プラグインは、コード、ブループリント、例を使用してプロジェクトに一般的な UX 機能を追加するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="24054-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![ビューポートの終わりのシーン](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="24054-109">シリーズが完了するまでに、次のことを実際に体験できます。</span><span class="sxs-lookup"><span data-stu-id="24054-109">By the end of the series you'll have hands-on experience with:</span></span>
* <span data-ttu-id="24054-110">新しいプロジェクトの開始</span><span class="sxs-lookup"><span data-stu-id="24054-110">Starting a new project</span></span>
* <span data-ttu-id="24054-111">Mixed Reality 用の設定</span><span class="sxs-lookup"><span data-stu-id="24054-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="24054-112">ユーザー入力の操作</span><span class="sxs-lookup"><span data-stu-id="24054-112">Working with user input</span></span>
* <span data-ttu-id="24054-113">ボタンの追加</span><span class="sxs-lookup"><span data-stu-id="24054-113">Adding buttons</span></span>
* <span data-ttu-id="24054-114">エミュレーターまたはデバイスでの再生</span><span class="sxs-lookup"><span data-stu-id="24054-114">Playing on an emulator or device</span></span>

<span data-ttu-id="24054-115">ご不明な点がある場合は、[Unreal 開発の概要](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="24054-115">If you have any questions, check out our [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="24054-116">前提条件</span><span class="sxs-lookup"><span data-stu-id="24054-116">Prerequisites</span></span>
<span data-ttu-id="24054-117">ジャンプする前に、次の要件を満たしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="24054-117">Make sure you've met the following requirements before jumping in:</span></span>
* <span data-ttu-id="24054-118">Windows 10 1809 以降</span><span class="sxs-lookup"><span data-stu-id="24054-118">Windows 10 1809 or later</span></span>
* <span data-ttu-id="24054-119">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="24054-119">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="24054-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 以降</span><span class="sxs-lookup"><span data-stu-id="24054-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="24054-121">[開発用に構成された](using-visual-studio.md#enabling-developer-mode) Microsoft HoloLens 2 デバイスまたはエミュレーター</span><span class="sxs-lookup"><span data-stu-id="24054-121">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="24054-122">以下のワークロードを含む Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="24054-122">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="24054-123">Visual Studio 2019 のインストール</span><span class="sxs-lookup"><span data-stu-id="24054-123">Installing Visual Studio 2019</span></span>
<span data-ttu-id="24054-124">最後の手順は、次のように Visual Studio をセットアップすることです。</span><span class="sxs-lookup"><span data-stu-id="24054-124">The last step is to setup Visual Studio as follows:</span></span>
1. <span data-ttu-id="24054-125">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) の最新バージョンのインストール</span><span class="sxs-lookup"><span data-stu-id="24054-125">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="24054-126">次の[ワークロード](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="24054-126">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads):</span></span>
    * <span data-ttu-id="24054-127">C++ によるデスクトップ開発</span><span class="sxs-lookup"><span data-stu-id="24054-127">Desktop development with C++</span></span>
    * <span data-ttu-id="24054-128">.NET デスクトップ開発</span><span class="sxs-lookup"><span data-stu-id="24054-128">.NET desktop development</span></span>
    * <span data-ttu-id="24054-129">ユニバーサル Windows プラットフォームの開発</span><span class="sxs-lookup"><span data-stu-id="24054-129">Universal Windows Platform development</span></span>

3. <span data-ttu-id="24054-130">次の[コンポーネント](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="24054-130">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components):</span></span>
    * <span data-ttu-id="24054-131">コンパイラ、ビルド ツール、ランタイム > MSVC v142 - VS 2019 C++ ARM64 ビルド ツール (最新バージョン)</span><span class="sxs-lookup"><span data-stu-id="24054-131">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="24054-132">以上で作業は終了です。</span><span class="sxs-lookup"><span data-stu-id="24054-132">That's it!</span></span> <span data-ttu-id="24054-133">これで、チェス アプリ プロジェクトを開始するためのすべての設定が完了しました。</span><span class="sxs-lookup"><span data-stu-id="24054-133">You're all set to move on to starting the chess app project.</span></span>

[<span data-ttu-id="24054-134">次のセクション: 2.プロジェクトと最初のアプリケーションの初期化</span><span class="sxs-lookup"><span data-stu-id="24054-134">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)