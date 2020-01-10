---
title: Windows Mixed Reality と新しい Microsoft Edge
description: Windows Mixed Reality のドキュメントに投稿する方法。
author: mattzmsft
ms.author: mazeller
ms.date: 01/07/2020
ms.topic: article
keywords: edge、新規、イマーシブ web、microsoft edge、browser、vr
ms.openlocfilehash: cb0f96069ffaa8f7d40b64bae55ab2749f5f02c6
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75727049"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a><span data-ttu-id="ba61b-104">Windows Mixed Reality と新しい Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="ba61b-104">Windows Mixed Reality and the new Microsoft Edge</span></span>

<span data-ttu-id="ba61b-105">ご存知かもしれませんが、[新しい Microsoft Edge は近日公開されてい](https://blogs.windows.com/windowsexperience/2019/11/04/introducing-the-new-microsoft-edge-and-bing/)ます。</span><span class="sxs-lookup"><span data-stu-id="ba61b-105">As you may have heard, the [new Microsoft Edge is coming soon](https://blogs.windows.com/windowsexperience/2019/11/04/introducing-the-new-microsoft-edge-and-bing/)!</span></span> <span data-ttu-id="ba61b-106">2020年1月15日を対象とした一般提供では、Windows Mixed Reality VR ヘッドセットのお客様に、新しい Microsoft Edge からの期待内容を知らせ、Windows Mixed での web 閲覧エクスペリエンスを向上させる保留中の更新について通知します。実際.</span><span class="sxs-lookup"><span data-stu-id="ba61b-106">With general availability targeted for January 15, 2020, we wanted to let Windows Mixed Reality VR headset customers know what to expect from the new Microsoft Edge and inform you of some pending updates that will improve your web browsing experience in Windows Mixed Reality.</span></span>

## <a name="introducing-the-new-microsoft-edge"></a><span data-ttu-id="ba61b-107">新しい Microsoft Edge の紹介</span><span class="sxs-lookup"><span data-stu-id="ba61b-107">Introducing the new Microsoft Edge</span></span>

<span data-ttu-id="ba61b-108">新しい Microsoft Edge は、 [Chromium のオープンソースプロジェクト](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/)をデスクトップ上に採用しているため、より優れた web 互換性をユーザーに提供し、すべての web 開発者が web の断片化を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="ba61b-108">The new Microsoft Edge [adopts the Chromium open source project](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) on the desktop to create better web compatibility for customers and less fragmentation of the web for all web developers.</span></span> <span data-ttu-id="ba61b-109">また、WebVR の代わりに、VR ヘッドセット用のイマーシブ web エクスペリエンスを作成するための新しい標準である WebXR at launch もサポートします。</span><span class="sxs-lookup"><span data-stu-id="ba61b-109">It will also support WebXR at launch, the new standard for creating immersive web experiences for VR headsets, in place of WebVR.</span></span>

## <a name="getting-ready-for-the-new-microsoft-edge"></a><span data-ttu-id="ba61b-110">新しい Microsoft Edge の準備</span><span class="sxs-lookup"><span data-stu-id="ba61b-110">Getting ready for the new Microsoft Edge</span></span>

<span data-ttu-id="ba61b-111">Mixed reality ホームで新しい Microsoft Edge を使用する windows Mixed Reality VR ヘッドセットのお客様は、mixed reality ホームで**Win32 アプリケーション (新しい Microsoft edge など) をネイティブでサポートするために、windows 10 バージョン1903以降にアップグレード**する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba61b-111">Windows Mixed Reality VR headset customers who want to use the new Microsoft Edge in the mixed reality home should **upgrade to Windows 10 Version 1903 or later for native support of Win32 applications (like the new Microsoft Edge)** in the mixed reality home.</span></span> <span data-ttu-id="ba61b-112">Windows Update を確認[するか、Windows 10 の最新バージョンを手動でインストールして](https://www.microsoft.com/en-us/software-download/windows10)ください。</span><span class="sxs-lookup"><span data-stu-id="ba61b-112">Check Windows Update or [manually install the latest version of Windows 10](https://www.microsoft.com/en-us/software-download/windows10).</span></span>

<span data-ttu-id="ba61b-113">混合現実のホームで Microsoft Edge エクスペリエンスを最大限に活用するために、windows **10 バージョン 1903 (またはそれ以降) の2020-01 累積的な更新プログラムが適用された新しい Microsoft edge の Windows Mixed reality 最適化の主要**な部分を待機することもお勧めします。これは、1月の最後まで Windows Update で利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="ba61b-113">For the best possible Microsoft Edge experience in the mixed reality home, we also recommend waiting for **some key Windows Mixed Reality optimizations for the new Microsoft Edge arriving with the 2020-01 Cumulative update for Windows 10 Version 1903 (or later)**, which should be available in Windows Update by the end of January.</span></span>

>[!IMPORTANT]
><span data-ttu-id="ba61b-114">これらの更新を行う前に新しい Microsoft Edge をダウンロードすることを選択した場合は、Windows Mixed Reality でのその動作に関する既知の問題がいくつかあります (下記を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="ba61b-114">If you opt to download the new Microsoft Edge before taking these updates, there will be some known issues with its behavior in Windows Mixed Reality (which you can read about below).</span></span>

## <a name="known-issues"></a><span data-ttu-id="ba61b-115">既知の問題</span><span class="sxs-lookup"><span data-stu-id="ba61b-115">Known issues</span></span>

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a><span data-ttu-id="ba61b-116">Windows 10 バージョン 1903 (またはそれ以降) の2020-01 累積更新プログラムによって解決された既知の問題</span><span class="sxs-lookup"><span data-stu-id="ba61b-116">Known issues resolved by the 2020-01 Cumulative update for Windows 10 Version 1903 (or later)</span></span>

- <span data-ttu-id="ba61b-117">新しい Microsoft Edge を含む任意の Win32 アプリを起動すると、ヘッドセットの表示が短時間フリーズします。</span><span class="sxs-lookup"><span data-stu-id="ba61b-117">Launching any Win32 app, including the new Microsoft Edge, causes the headset display to briefly freeze.</span></span>
- <span data-ttu-id="ba61b-118">Microsoft Edge タイルは、Windows Mixed Reality の [スタート] メニューから消えます ("クラシックアプリ" フォルダーで見つけることができます)。</span><span class="sxs-lookup"><span data-stu-id="ba61b-118">The Microsoft Edge tile disappears from the Windows Mixed Reality Start menu (you can find it in the “Classic apps” folder).</span></span>
- <span data-ttu-id="ba61b-119">以前の Microsoft Edge からの Windows は、mixed reality ホームの周囲に配置されていますが、使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ba61b-119">Windows from the previous Microsoft Edge are still placed around the mixed reality home, but cannot be used.</span></span> <span data-ttu-id="ba61b-120">これらのウィンドウをアクティブ化しようとすると、デスクトップアプリ内で Edge が起動します。</span><span class="sxs-lookup"><span data-stu-id="ba61b-120">Attempting to activate those windows launches Edge inside of the Desktop app.</span></span>
- <span data-ttu-id="ba61b-121">Mixed reality ホームでハイパーリンクを選択すると、mixed reality ホームではなく、デスクトップで web ブラウザーが起動します。</span><span class="sxs-lookup"><span data-stu-id="ba61b-121">Selecting a hyperlink in the mixed reality home launches a web browser on the desktop instead of the mixed reality home.</span></span>
- <span data-ttu-id="ba61b-122">Webvr ショーケースアプリは、WebVR がサポートされなくなっても、mixed reality ホームに存在します。</span><span class="sxs-lookup"><span data-stu-id="ba61b-122">The WebVR Showcase app is present in the mixed reality home, despite WebVR no longer being supported.</span></span>
- <span data-ttu-id="ba61b-123">キーボード起動とビジュアルの全般的な機能強化。</span><span class="sxs-lookup"><span data-stu-id="ba61b-123">General improvements to keyboard launch and visuals.</span></span>

### <a name="additional-known-issues"></a><span data-ttu-id="ba61b-124">その他の既知の問題</span><span class="sxs-lookup"><span data-stu-id="ba61b-124">Additional known issues</span></span>

-   <span data-ttu-id="ba61b-125">Windows Mixed reality で開かれている web サイトは、Mixed reality ポータルが閉じたときに失われます。ただし、Microsoft Edge ウィンドウは、mixed reality ホームに配置された場所に残ります。</span><span class="sxs-lookup"><span data-stu-id="ba61b-125">Websites open in Windows Mixed Reality will be lost when Mixed Reality Portal closes, though the Microsoft Edge windows will remain where they were placed in the mixed reality home.</span></span>
-   <span data-ttu-id="ba61b-126">Microsoft Edge ウィンドウからのオーディオは spatialized ません。</span><span class="sxs-lookup"><span data-stu-id="ba61b-126">Audio from Microsoft Edge windows is not spatialized.</span></span>
-   <span data-ttu-id="ba61b-127">Windows Mixed Reality で YouTube から360ビデオを開くと、ヘッドセットでビデオがゆがんでしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba61b-127">Opening a 360 video from YouTube in Windows Mixed Reality may result in the video being distorted in the headset.</span></span> <span data-ttu-id="ba61b-128">YouTube ビデオのページを更新し、360ビデオを再起動すると、問題が解決されます。</span><span class="sxs-lookup"><span data-stu-id="ba61b-128">Refreshing the YouTube video’s page and relaunching the 360 video should fix the issue.</span></span>
-   <span data-ttu-id="ba61b-129">Windows Mixed Reality セッション中に、設定 の > システム > 表示に汎用物理モニターとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba61b-129">During Windows Mixed Reality sessions, virtual monitors will appear as generic physical monitors in Settings > System > Display.</span></span>



