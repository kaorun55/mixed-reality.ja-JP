---
title: HoloLens 用アプリを入手します。
description: HoloLens、両方を Microsoft Store とのサイド ロード アプリ インストールについて説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: サイドロード、側の負荷、サイドローディング、ストア、uwp、アプリのインストール
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597554"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="92bf5-104">HoloLens 用アプリを入手します。</span><span class="sxs-lookup"><span data-stu-id="92bf5-104">Get apps for HoloLens</span></span>

<span data-ttu-id="92bf5-105">、、Windows 10 デバイスとしては、HoloLens は多くの既存の UWP アプリケーションから、アプリ ストアとして HoloLens 専用に構築された新しいアプリをサポートします。</span><span class="sxs-lookup"><span data-stu-id="92bf5-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="92bf5-106">これらの上にすることもできますを[開発](development-overview.md)独自のアプリ、または、友人のインストールと!</span><span class="sxs-lookup"><span data-stu-id="92bf5-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="92bf5-107">アプリのインストール</span><span class="sxs-lookup"><span data-stu-id="92bf5-107">Installing Apps</span></span>

<span data-ttu-id="92bf5-108">これには、HoloLens に新しいアプリをインストールする 3 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="92bf5-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="92bf5-109">プライマリのメソッドは、Windows ストアから新しいアプリケーションをインストールになります。</span><span class="sxs-lookup"><span data-stu-id="92bf5-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="92bf5-110">ただし、デバイス ポータルを使用して、独自のアプリケーション インストールもまたはして Visual Studio からデプロイすることです。</span><span class="sxs-lookup"><span data-stu-id="92bf5-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="92bf5-111">Microsoft Store から</span><span class="sxs-lookup"><span data-stu-id="92bf5-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="92bf5-112">実行、[ブルーム](gestures.md#bloom)ジェスチャを開く、 [[スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)します。</span><span class="sxs-lookup"><span data-stu-id="92bf5-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="92bf5-113">ストア アプリを選択し、世界中にこのタイルを配置する をタップします。</span><span class="sxs-lookup"><span data-stu-id="92bf5-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="92bf5-114">ストア アプリが開いたら、任意の必要なアプリケーションを検索する検索バーを使用します。</span><span class="sxs-lookup"><span data-stu-id="92bf5-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="92bf5-115">選択**取得**または**インストール**(購入が必要に可能性があります)、アプリケーションのページ。</span><span class="sxs-lookup"><span data-stu-id="92bf5-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="92bf5-116">デバイスのポータルを使用したアプリケーション パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="92bf5-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="92bf5-117">接続を確立[デバイス ポータル](using-the-windows-device-portal.md)HoloLens のターゲットにします。</span><span class="sxs-lookup"><span data-stu-id="92bf5-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="92bf5-118">移動し、**アプリ**左側のナビゲーション ページ。</span><span class="sxs-lookup"><span data-stu-id="92bf5-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="92bf5-119">**アプリ パッケージ**アプリケーションに関連付けられている .appx ファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="92bf5-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="92bf5-120">関連付けられているすべての依存関係と証明書ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="92bf5-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="92bf5-121">クリックして**移動**します。</span><span class="sxs-lookup"><span data-stu-id="92bf5-121">Click **Go**.</span></span>

<span data-ttu-id="92bf5-122">![Microsoft HoloLens で Windows Device Portal でアプリのフォームをインストールします。](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="92bf5-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="92bf5-123">Windows Device Portal を使用して、HoloLens にアプリをインストールするには</span><span class="sxs-lookup"><span data-stu-id="92bf5-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="92bf5-124">Microsoft Visual Studio 2015 からのデプロイ</span><span class="sxs-lookup"><span data-stu-id="92bf5-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="92bf5-125">アプリの Visual Studio ソリューション (.sln ファイル) を開きます。</span><span class="sxs-lookup"><span data-stu-id="92bf5-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="92bf5-126">プロジェクトの**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="92bf5-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="92bf5-127">次のビルド構成を選択します。マスター/x86/リモート マシン。</span><span class="sxs-lookup"><span data-stu-id="92bf5-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="92bf5-128">リモート コンピューターを選択するとします。</span><span class="sxs-lookup"><span data-stu-id="92bf5-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="92bf5-129">確認アドレス ポイント HoloLens の WiFi の IP アドレスにします。</span><span class="sxs-lookup"><span data-stu-id="92bf5-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="92bf5-130">ユニバーサル (暗号化されていないプロトコル) への認証を設定します。</span><span class="sxs-lookup"><span data-stu-id="92bf5-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="92bf5-131">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="92bf5-131">Build your solution.</span></span>
6. <span data-ttu-id="92bf5-132">をクリックして、**リモート マシン**HoloLens を開発用 PC からアプリをデプロイするボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="92bf5-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="92bf5-133">HoloLens の既存のビルドを既にがある場合は、この新しいバージョンを再インストールするには、[はい] を選択します。</span><span class="sxs-lookup"><span data-stu-id="92bf5-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="92bf5-134">![Visual Studio での Microsoft HoloLens にアプリをリモート マシンのデプロイ](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="92bf5-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="92bf5-135">アプリケーションはインストールし、自動、HoloLens で起動します。</span><span class="sxs-lookup"><span data-stu-id="92bf5-135">The application will install and auto launch on your HoloLens.</span></span>
