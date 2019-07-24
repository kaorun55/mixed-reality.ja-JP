---
title: HoloLens 用アプリを取得する
description: Microsoft Store とサイドローディングを使用して、HoloLens 用のアプリをインストールする方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: サイドロード、サイドロード、サイドロード、ストア、uwp、アプリ、インストール
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522541"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="d6d16-104">HoloLens 用アプリを取得する</span><span class="sxs-lookup"><span data-stu-id="d6d16-104">Get apps for HoloLens</span></span>

<span data-ttu-id="d6d16-105">Windows 10 デバイスとして、HoloLens は、アプリストアからの多くの既存の UWP アプリケーションだけでなく、HoloLens 専用に構築された新しいアプリもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d6d16-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="d6d16-106">これらに加えて、独自のアプリや友人のアプリを[開発](development-overview.md)してインストールすることが必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="d6d16-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="d6d16-107">アプリのインストール</span><span class="sxs-lookup"><span data-stu-id="d6d16-107">Installing Apps</span></span>

<span data-ttu-id="d6d16-108">HoloLens に新しいアプリをインストールするには、次の3つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="d6d16-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="d6d16-109">主要な方法は、Windows ストアから新しいアプリケーションをインストールすることです。</span><span class="sxs-lookup"><span data-stu-id="d6d16-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="d6d16-110">ただし、デバイスポータルを使用するか、Visual Studio から展開することで、独自のアプリケーションをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d6d16-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="d6d16-111">Microsoft Store から</span><span class="sxs-lookup"><span data-stu-id="d6d16-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="d6d16-112">[ブルーム](gestures.md#bloom)ジェスチャを実行して [[スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)を開きます。</span><span class="sxs-lookup"><span data-stu-id="d6d16-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="d6d16-113">ストアアプリを選択し、タップして、このタイルを世界に配置します。</span><span class="sxs-lookup"><span data-stu-id="d6d16-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="d6d16-114">ストアアプリが開いたら、検索バーを使用して目的のアプリケーションを探します。</span><span class="sxs-lookup"><span data-stu-id="d6d16-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="d6d16-115">アプリケーションのページで **[取得]** または **[インストール]** を選択します (購入が必要な場合があります)。</span><span class="sxs-lookup"><span data-stu-id="d6d16-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="d6d16-116">デバイスポータルを使用したアプリケーションパッケージのインストール</span><span class="sxs-lookup"><span data-stu-id="d6d16-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="d6d16-117">[デバイスポータル](using-the-windows-device-portal.md)からターゲット HoloLens への接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="d6d16-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="d6d16-118">左側のナビゲーションで、 **[アプリ]** ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="d6d16-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="d6d16-119">**[アプリパッケージ]** の下で、アプリケーションに関連付けられている .appx ファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="d6d16-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="d6d16-120">関連する依存関係および証明書ファイルを必ず参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6d16-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="d6d16-121">**[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6d16-121">Click **Go**.</span></span>

<span data-ttu-id="d6d16-122">![Microsoft HoloLens の Windows デバイスポータルでアプリフォームをインストールする](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="d6d16-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="d6d16-123">Windows デバイスポータルを使用して HoloLens にアプリをインストールする</span><span class="sxs-lookup"><span data-stu-id="d6d16-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="d6d16-124">Microsoft Visual Studio 2015 からの展開</span><span class="sxs-lookup"><span data-stu-id="d6d16-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="d6d16-125">アプリの Visual Studio ソリューション (.sln ファイル) を開きます。</span><span class="sxs-lookup"><span data-stu-id="d6d16-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="d6d16-126">プロジェクトの**プロパティ**を開きます。</span><span class="sxs-lookup"><span data-stu-id="d6d16-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="d6d16-127">次のビルド構成を選択します。マスター/x86/リモートコンピューター。</span><span class="sxs-lookup"><span data-stu-id="d6d16-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="d6d16-128">[リモートコンピューター] を選択した場合:</span><span class="sxs-lookup"><span data-stu-id="d6d16-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="d6d16-129">アドレスが HoloLens の WiFi IP アドレスを指していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d6d16-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="d6d16-130">認証を Universal (暗号化されていないプロトコル) に設定します。</span><span class="sxs-lookup"><span data-stu-id="d6d16-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="d6d16-131">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="d6d16-131">Build your solution.</span></span>
6. <span data-ttu-id="d6d16-132">**[リモートコンピューター]** ボタンをクリックして、開発用 PC から HoloLens にアプリをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="d6d16-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="d6d16-133">HoloLens に既存のビルドが既に存在する場合は、[はい] を選択して、この新しいバージョンを再インストールします。</span><span class="sxs-lookup"><span data-stu-id="d6d16-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="d6d16-134">![Visual Studio でのアプリの Microsoft HoloLens へのリモートコンピューターの展開](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="d6d16-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="d6d16-135">アプリケーションが HoloLens にインストールされ、自動的に起動します。</span><span class="sxs-lookup"><span data-stu-id="d6d16-135">The application will install and auto launch on your HoloLens.</span></span>
