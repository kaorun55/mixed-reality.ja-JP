---
title: 6. デバイスまたはエミュレーターへのパッケージ化とデプロイ
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアルのパート 6
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: 35b18e4bb289438f94433827846e94d1014385db
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840381"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="90891-104">6.デバイスまたはエミュレーターへのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="90891-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="90891-105">このセクションでは、HoloLens 2 のデバイスまたはエミュレーターで実行するようにアプリを準備する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="90891-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="90891-106">デバイスをお持ちの場合は、コンピューターからデバイスにストリーミングするか、アプリをパッケージ化してデバイス上で直接実行することができます。</span><span class="sxs-lookup"><span data-stu-id="90891-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="90891-107">デバイスがない場合は、アプリをパッケージ化してエミュレーターで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90891-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="90891-108">目標</span><span class="sxs-lookup"><span data-stu-id="90891-108">Objectives</span></span>

* <span data-ttu-id="90891-109">[デバイスのみ] アプリのホログラフィック リモート処理によってアプリを HoloLens 2 にストリーミングする</span><span class="sxs-lookup"><span data-stu-id="90891-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="90891-110">アプリをパッケージ化して HoloLens 2 のデバイスまたはエミュレーターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="90891-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="90891-111">[デバイスのみ] ストリーミング</span><span class="sxs-lookup"><span data-stu-id="90891-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="90891-112">Microsoft Store から **Holographic Remoting Player** を HoloLens 2 にインストールし、アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="90891-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="90891-113">**[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\)** に移動します。</span><span class="sxs-lookup"><span data-stu-id="90891-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="90891-114">[Holographic Remoting]\(ホログラフィック リモート処理\) セクションで、チェック ボックスをオンにしてリモート処理を有効にし、エディターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="90891-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="90891-115">デバイスの IP アドレスを入力し、[Connect]\(接続\) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90891-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="90891-116">接続後、UE4 エディターで [Play]\(再生\) ボタンの右側にあるドロップダウン矢印をクリックし、[VR Preview]\(VR プレビュー\) を選択します。</span><span class="sxs-lookup"><span data-stu-id="90891-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="90891-117">アプリのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="90891-117">Package and deploy your app</span></span> 

1.  <span data-ttu-id="90891-118">**[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\)** に移動します。</span><span class="sxs-lookup"><span data-stu-id="90891-118">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="90891-119">**[Project]\(プロジェクト\) > [Description]\(説明\) > [About]\(情報\) > [Project Name]\(プロジェクト名\)** で、プロジェクトに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="90891-119">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="90891-120">**[Project]\(プロジェクト\) > [Description]\(説明\) > [Publisher]\(パブリッシャー\) > [Company Distinguished Name]\(企業識別名\)** に「CN={INSERT COMPANY NAME}」を入力します。</span><span class="sxs-lookup"><span data-stu-id="90891-120">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="90891-121">これらのフィールドのいずれかを空白のままにすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="90891-121">Leaving either of these fields blank will result in an error.</span></span> 

![プロジェクト設定 - 説明](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="90891-123">**[Platforms]\(プラットフォーム\) > [HoloLens]** で、どれをターゲットにするかに応じて [Emulation]\(エミュレーション\)、[Device]\(デバイス\)、またはその両方を選択します。</span><span class="sxs-lookup"><span data-stu-id="90891-123">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="90891-124">**[Packaging]\(パッケージ化\)** セクションの **[Signing Certificate]\(証明書に署名\)** で、 **[Generate new]\(新規生成\)** ボタンをクリックして新しい署名証明書を生成します。</span><span class="sxs-lookup"><span data-stu-id="90891-124">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="90891-125">メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="90891-125">Return to the Main window.</span></span>

![プロジェクト設定 - プラットフォーム - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="90891-127">**[File]\(ファイル\) > [Package Project]\(プロジェクトをパッケージ化\)** に移動し、 **[HoloLens]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="90891-127">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="90891-128">パッケージを保存する新しいフォルダーを作成し、 **[Select Folder]\(フォルダーの選択\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90891-128">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="90891-129">アプリが正常にパッケージ化されたら、**Windows デバイス ポータル**を開き、 **[ビュー] > [アプリ]** に移動して、 **[Deploy apps]\(アプリの展開\)** セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="90891-129">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="90891-130">**[参照]** をクリックし、**ChessApp.appxbundle** ファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="90891-130">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="90891-131">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90891-131">Click **Open**.</span></span> 

    * <span data-ttu-id="90891-132">デバイスに初めてアプリをインストールする場合は、 **[Allow me to select framework packages]\(フレームワーク パッケージを選択できるようにする\)** の横のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="90891-132">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="90891-133">次のダイアログで、適切な VCLibs appx ファイルを組み込みます (デバイスの場合は arm64、エミュレーターの場合は x64)。</span><span class="sxs-lookup"><span data-stu-id="90891-133">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="90891-134">**[Install]** (インストール) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90891-134">Click **Install**</span></span>

<span data-ttu-id="90891-135">このチュートリアルを終了していただき、ありがとうございます。</span><span class="sxs-lookup"><span data-stu-id="90891-135">Congratulations on finishing this tutorial!</span></span>  