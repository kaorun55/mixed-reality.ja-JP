---
title: 6. デバイスまたはエミュレーターへのパッケージ化とデプロイ
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアルのパート 6
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519970"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="eb952-104">6.デバイスまたはエミュレーターへのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="eb952-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="eb952-105">このセクションでは、HoloLens 2 のデバイスまたはエミュレーターで実行するようにアプリを準備する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb952-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="eb952-106">デバイスをお持ちの場合は、コンピューターからデバイスにストリーミングするか、アプリをパッケージ化してデバイス上で直接実行することができます。</span><span class="sxs-lookup"><span data-stu-id="eb952-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="eb952-107">デバイスがない場合は、アプリをパッケージ化してエミュレーターで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb952-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="eb952-108">目標</span><span class="sxs-lookup"><span data-stu-id="eb952-108">Objectives</span></span>

* <span data-ttu-id="eb952-109">[デバイスのみ] アプリのホログラフィック リモート処理によってアプリを HoloLens 2 にストリーミングする</span><span class="sxs-lookup"><span data-stu-id="eb952-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="eb952-110">アプリをパッケージ化して HoloLens 2 のデバイスまたはエミュレーターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="eb952-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="eb952-111">[デバイスのみ] ストリーミング</span><span class="sxs-lookup"><span data-stu-id="eb952-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="eb952-112">Microsoft Store から **Holographic Remoting Player** を HoloLens 2 にインストールし、アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="eb952-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="eb952-113">**[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\)** に移動します。</span><span class="sxs-lookup"><span data-stu-id="eb952-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="eb952-114">[Holographic Remoting]\(ホログラフィック リモート処理\) セクションで、チェック ボックスをオンにしてリモート処理を有効にし、エディターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="eb952-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="eb952-115">デバイスの IP アドレスを入力し、[Connect]\(接続\) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb952-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="eb952-116">接続後、UE4 エディターで [Play]\(再生\) ボタンの右側にあるドロップダウン矢印をクリックし、[VR Preview]\(VR プレビュー\) を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb952-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="eb952-117">アプリのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="eb952-117">Package and deploy your app</span></span> 

>[!NOTE]
><span data-ttu-id="eb952-118">HoloLens 用の Unreal アプリを初めてパッケージ化する場合は、Epic Launcher からサポート ファイルをダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb952-118">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span> <span data-ttu-id="eb952-119">これを行うには、Epic Games Launcher の **[ライブラリ]** タブに移動します。</span><span class="sxs-lookup"><span data-stu-id="eb952-119">To do so, go to the **Library** tab in the Epic Games Launcher.</span></span> <span data-ttu-id="eb952-120">**[起動]** の横にあるドロップダウン矢印を選択し、 **[オプション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb952-120">Select the dropdown arrow next to **Launch** and select **Options**.</span></span> <span data-ttu-id="eb952-121">**[対応プラットフォーム]** で、 **[HoloLens 2]** を選択し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb952-121">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span> 
><span data-ttu-id="eb952-122">![プロジェクト設定 - 説明](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="eb952-122">![Project Settings - Description](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="eb952-123">**[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\)** に移動します。</span><span class="sxs-lookup"><span data-stu-id="eb952-123">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="eb952-124">**[Project]\(プロジェクト\) > [Description]\(説明\) > [About]\(情報\) > [Project Name]\(プロジェクト名\)** で、プロジェクトに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="eb952-124">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="eb952-125">**[Project]\(プロジェクト\) > [Description]\(説明\) > [Publisher]\(パブリッシャー\) > [Company Distinguished Name]\(企業識別名\)** に「CN={INSERT COMPANY NAME}」を入力します。</span><span class="sxs-lookup"><span data-stu-id="eb952-125">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="eb952-126">これらのフィールドのいずれかを空白のままにすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="eb952-126">Leaving either of these fields blank will result in an error.</span></span> 

![プロジェクト設定 - 説明](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="eb952-128">**[Platforms]\(プラットフォーム\) > [HoloLens]** で、どれをターゲットにするかに応じて [Emulation]\(エミュレーション\)、[Device]\(デバイス\)、またはその両方を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb952-128">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="eb952-129">**[Packaging]\(パッケージ化\)** セクションの **[Signing Certificate]\(証明書に署名\)** で、 **[Generate new]\(新規生成\)** ボタンをクリックして新しい署名証明書を生成します。</span><span class="sxs-lookup"><span data-stu-id="eb952-129">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="eb952-130">メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="eb952-130">Return to the Main window.</span></span>

![プロジェクト設定 - プラットフォーム - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="eb952-132">**[File]\(ファイル\) > [Package Project]\(プロジェクトをパッケージ化\)** に移動し、 **[HoloLens]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb952-132">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="eb952-133">パッケージを保存する新しいフォルダーを作成し、 **[Select Folder]\(フォルダーの選択\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb952-133">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="eb952-134">アプリが正常にパッケージ化されたら、**Windows デバイス ポータル**を開き、 **[ビュー] > [アプリ]** に移動して、 **[Deploy apps]\(アプリの展開\)** セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="eb952-134">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="eb952-135">**[参照]** をクリックし、**ChessApp.appxbundle** ファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="eb952-135">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="eb952-136">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb952-136">Click **Open**.</span></span> 

    * <span data-ttu-id="eb952-137">デバイスに初めてアプリをインストールする場合は、 **[Allow me to select framework packages]\(フレームワーク パッケージを選択できるようにする\)** の横のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="eb952-137">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="eb952-138">次のダイアログで、適切な VCLibs appx ファイルを組み込みます (デバイスの場合は arm64、エミュレーターの場合は x64)。</span><span class="sxs-lookup"><span data-stu-id="eb952-138">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="eb952-139">**[Install]** (インストール) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb952-139">Click **Install**</span></span>

<span data-ttu-id="eb952-140">このチュートリアルを終了していただき、ありがとうございます。</span><span class="sxs-lookup"><span data-stu-id="eb952-140">Congratulations on finishing this tutorial!</span></span>  