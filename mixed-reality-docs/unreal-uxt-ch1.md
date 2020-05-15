---
title: 1. はじめに
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリをビルドするためのチュートリアルのパート 1
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: 3ca47cfe7bb0a733932f3777cc8b531ef9df8e71
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840131"
---
# <a name="1-getting-started"></a><span data-ttu-id="23eac-104">1.はじめに</span><span class="sxs-lookup"><span data-stu-id="23eac-104">1. Getting started</span></span>

<span data-ttu-id="23eac-105">このチュートリアルでは、Unreal Engine 4 を使用して、対話型の HoloLens 2 チェス アプリをビルドする方法をステップバイステップで説明します。</span><span class="sxs-lookup"><span data-stu-id="23eac-105">This is a step by step tutorial that will show you how to build an interactive HoloLens 2 chess app using Unreal Engine 4.</span></span> <span data-ttu-id="23eac-106">また、Unreal 向け Mixed Reality ツールキットの UX ツール プラグインを使用して、開発を高速化する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="23eac-106">You will also learn how to use the UX Tools plugin from the Mixed Reality Toolkit for Unreal to speed up development.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="23eac-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="23eac-107">Prerequisites</span></span>

* <span data-ttu-id="23eac-108">Windows 10 1809 以降</span><span class="sxs-lookup"><span data-stu-id="23eac-108">Windows 10 1809 or later</span></span>
* <span data-ttu-id="23eac-109">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="23eac-109">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="23eac-110">Unreal Engine 4.25 以降</span><span class="sxs-lookup"><span data-stu-id="23eac-110">Unreal Engine 4.25 or later</span></span>
* <span data-ttu-id="23eac-111">[開発用に構成された](using-visual-studio.md#enabling-developer-mode) Microsoft HoloLens 2 デバイスまたはエミュレーター</span><span class="sxs-lookup"><span data-stu-id="23eac-111">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="23eac-112">Visual Studio 2019 (以下のワークロードとコンポーネントを含む)</span><span class="sxs-lookup"><span data-stu-id="23eac-112">Visual Studio 2019 (with below workloads and components)</span></span>

### <a name="installing-visual-studio-2019-workloads-and-components"></a><span data-ttu-id="23eac-113">Visual Studio 2019、ワークロード、コンポーネントのインストール</span><span class="sxs-lookup"><span data-stu-id="23eac-113">Installing Visual Studio 2019, workloads, and components</span></span>
1. <span data-ttu-id="23eac-114">最新バージョンの Visual Studio 2019 のインストールまたは更新</span><span class="sxs-lookup"><span data-stu-id="23eac-114">Install or and update to the latest version of Visual Studio 2019</span></span>
* [<span data-ttu-id="23eac-115">Visual Studio 2019 をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="23eac-115">Download Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/)
2. <span data-ttu-id="23eac-116">次のワークロードをインストールします。</span><span class="sxs-lookup"><span data-stu-id="23eac-116">Install the following workloads:</span></span>
* <span data-ttu-id="23eac-117">C++ によるデスクトップ開発</span><span class="sxs-lookup"><span data-stu-id="23eac-117">Desktop development with C++</span></span>
* <span data-ttu-id="23eac-118">.NET デスクトップ開発</span><span class="sxs-lookup"><span data-stu-id="23eac-118">.NET desktop development</span></span>
* <span data-ttu-id="23eac-119">ユニバーサル Windows プラットフォームの開発</span><span class="sxs-lookup"><span data-stu-id="23eac-119">Universal Windows Platform development</span></span>
3. <span data-ttu-id="23eac-120">次の個々のコンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="23eac-120">Install the following individual components:</span></span>
* <span data-ttu-id="23eac-121">コンパイラ、ビルド ツール、ランタイム > MSVC v142 - VS 2019 C++ ARM64 ビルド ツール (最新バージョン)</span><span class="sxs-lookup"><span data-stu-id="23eac-121">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

[<span data-ttu-id="23eac-122">次のセクション: 2.プロジェクトと最初のアプリケーションの初期化</span><span class="sxs-lookup"><span data-stu-id="23eac-122">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)