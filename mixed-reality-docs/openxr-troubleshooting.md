---
title: OpenXR トラブルシューティング
description: OpenXR アプリケーションの問題をトラブルシューティングします。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア、トラブルシューティング
ms.openlocfilehash: 269982596ed6162d9c2f1ec999a446bcecd6ba2a
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228007"
---
# <a name="openxr-troubleshooting"></a><span data-ttu-id="6c61c-104">OpenXR トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6c61c-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="6c61c-105">Windows Mixed Reality OpenXR Runtime を使用して OpenXR アプリを開発する際のトラブルシューティングのヒントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6c61c-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="6c61c-106"><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 の仕様</a>に関して他に質問がある場合は、 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR フォーラム</a>または<a href="https://khr.io/slack" target="_blank">余裕期間 #openxr チャネル</a>にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="6c61c-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, please visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="6c61c-107">X86 アプリでの現在の Windows Mixed Reality OpenXR ランタイムには既知の問題があります。</span><span class="sxs-lookup"><span data-stu-id="6c61c-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="6c61c-108">現時点では、x64 用のデスクトップ OpenXR アプリを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c61c-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="6c61c-109">OpenXR app が Windows Mixed Reality を開始しない</span><span class="sxs-lookup"><span data-stu-id="6c61c-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="6c61c-110">実行時に OpenXR アプリが Windows Mixed Reality を起動していない場合は、Windows Mixed Reality OpenXR ランタイムがアクティブなランタイムとして設定されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6c61c-110">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span>  <span data-ttu-id="6c61c-111">前の手順に従って、 [Windows Mixed Reality ヘッドセットの OpenXR を使用](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets)してランタイムをアクティブにしてください。</span><span class="sxs-lookup"><span data-stu-id="6c61c-111">Be sure to follow the instructions above for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to make the runtime active.</span></span>

<span data-ttu-id="6c61c-112">また、 [Windows Mixed Reality OpenXR 開発者ツール](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools)を実行して、システム上の Windows Mixed Reality OpenXR ランタイムの状態に関する追加のトラブルシューティングを行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="6c61c-112">You can also run the [Windows Mixed Reality OpenXR Developer Tools](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) for additional troubleshooting help around the state of the Windows Mixed Reality OpenXR Runtime on your system.</span></span>

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a><span data-ttu-id="6c61c-113">Mixed Reality ポータルに [OpenXR の設定] メニュー項目が表示されない</span><span class="sxs-lookup"><span data-stu-id="6c61c-113">Mixed Reality Portal not showing "Set up OpenXR" menu item</span></span>

<span data-ttu-id="6c61c-114">少なくとも Windows 10 10 月2018更新プログラム (1809) を実行していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6c61c-114">Be sure you are running at least the Windows 10 October 2018 Update (1809).</span></span>  <span data-ttu-id="6c61c-115">以前のバージョンの Windows 10 を使用している場合は、 [windows 10 Update Assistant](https://www.microsoft.com//software-download/windows10)を使用して、2019年5月の更新プログラム (1903) にアップグレードすることができます。</span><span class="sxs-lookup"><span data-stu-id="6c61c-115">If you're on an earlier version of Windows 10, you can upgrade to the May 2019 Update (1903) using the [Windows 10 Update Assistant](https://www.microsoft.com//software-download/windows10).</span></span>

<span data-ttu-id="6c61c-116">以前のバージョンの Mixed Reality ポータルアプリを使用している場合は、[OpenXR の設定] メニュー項目を使用できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="6c61c-116">The "Set up OpenXR" menu item may not be available if you have an older version of the Mixed Reality Portal app.</span></span>  <span data-ttu-id="6c61c-117">[Mixed Reality ポータルアプリの更新プログラム](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m)を確認して、最新バージョンがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6c61c-117">Check for a [Mixed Reality Portal app update](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) to ensure you have the latest version.</span></span>

<span data-ttu-id="6c61c-118">Windows Mixed Reality OpenXR Runtime が既にインストールされ、アクティブになっている場合は、[OpenXR の設定] メニュー項目が表示されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6c61c-118">Note that the "Set up OpenXR" menu item will not show up if the Windows Mixed Reality OpenXR Runtime is already installed and active.</span></span>  <span data-ttu-id="6c61c-119">[Windows Mixed Reality OpenXR 開発者ツール](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools)をインストールして、システム上の OpenXR ランタイムの現在の状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="6c61c-119">You can install the [Windows Mixed Reality OpenXR Developer Tools](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) to determine the current status of the OpenXR runtime on your system.</span></span>