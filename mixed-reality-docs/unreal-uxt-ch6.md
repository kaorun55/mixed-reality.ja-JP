---
title: 6. デバイスまたはエミュレーターへのパッケージ化とデプロイ
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 6
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: 99c431920c72cf85fed5a0eec6fc72ddf9fb112c
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330241"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="f2b07-104">6.デバイスまたはエミュレーターへのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="f2b07-104">6. Packaging & deploying to device or emulator</span></span>

## <a name="overview"></a><span data-ttu-id="f2b07-105">概要</span><span class="sxs-lookup"><span data-stu-id="f2b07-105">Overview</span></span>

<span data-ttu-id="f2b07-106">前のチュートリアルでは、チェスの駒を元の位置にリセットする簡単なボタンを追加しました。</span><span class="sxs-lookup"><span data-stu-id="f2b07-106">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="f2b07-107">この最後のセクションでは、アプリを HoloLens 2 またはエミュレーターで実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f2b07-107">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="f2b07-108">HoloLens 2 をお持ちの場合は、コンピューターからストリーミングするか、アプリをパッケージ化してデバイス上で直接実行することができます。</span><span class="sxs-lookup"><span data-stu-id="f2b07-108">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="f2b07-109">デバイスがない場合は、エミュレーターで実行するアプリをパッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="f2b07-109">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="f2b07-110">このセクションを完了するまでに、対話式操作と UI を備えた、再生可能な Mixed Reality アプリがデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="f2b07-110">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="f2b07-111">目標</span><span class="sxs-lookup"><span data-stu-id="f2b07-111">Objectives</span></span>

* <span data-ttu-id="f2b07-112">[デバイスのみ] ホログラフィック アプリのリモート処理によって HoloLens 2 にストリーミングする</span><span class="sxs-lookup"><span data-stu-id="f2b07-112">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="f2b07-113">アプリをパッケージ化して HoloLens 2 のデバイスまたはエミュレーターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="f2b07-113">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="f2b07-114">[デバイスのみ] ストリーミング</span><span class="sxs-lookup"><span data-stu-id="f2b07-114">[Device Only] Streaming</span></span>
<span data-ttu-id="f2b07-115">この場合、[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) は、チャネルを切り替えるのではなく、PC またはスタンドアロンの UWP デバイスから HoloLens 2 にデータをストリーミングすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="f2b07-115">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) in this case means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="f2b07-116">これは、リモート処理ホスト アプリが HoloLens から入力データ ストリームを受け取り、仮想イマーシブ ビューでコンテンツをレンダリングし、Wi-Fi 経由でコンテンツ フレームを HoloLens にストリームするという仕組みになっています。</span><span class="sxs-lookup"><span data-stu-id="f2b07-116">The way this works is a remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="f2b07-117">ストリーミングを使用すると、リモートのイマーシブ ビューを既存のデスクトップ PC ソフトウェアに追加し、より多くのシステム リソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f2b07-117">Streaming allows you to add remote immersive views into existing desktop PC software and has access to more system resources.</span></span> 

<span data-ttu-id="f2b07-118">チェス アプリでこのルートを使用する場合は、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2b07-118">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="f2b07-119">Microsoft Store から **Holographic Remoting Player** を HoloLens 2 にインストールし、アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="f2b07-119">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span>

2.  <span data-ttu-id="f2b07-120">**[編集] > [プロジェクトの設定]** に移動し、 **[Holographic Remoting]** セクションで **[リモート処理を有効にする]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="f2b07-120">Go to **Edit > Project Settings** and check **enable remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="f2b07-121">エディターを再起動し、[デバイスの IP アドレスを検索](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi)して入力し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2b07-121">Restart the editor, [find your device's IP address](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi) and enter it, then click **Connect**.</span></span>

<span data-ttu-id="f2b07-122">接続後、 **[Play]\(再生\)** ボタンの右側にあるドロップダウン矢印をクリックし、 **[VR Preview]\(VR プレビュー\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f2b07-122">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="f2b07-123">これにより、VR プレビュー ウィンドウでアプリが実行され、HoloLens ヘッドセットにストリーミングされます。</span><span class="sxs-lookup"><span data-stu-id="f2b07-123">This will run the app in the VR Preview Window, which is streamed to the HoloLens headset.</span></span> 

## <a name="packaging-and-deploying-the-app"></a><span data-ttu-id="f2b07-124">アプリのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="f2b07-124">Packaging and deploying the app</span></span> 

>[!NOTE]
><span data-ttu-id="f2b07-125">HoloLens 用の Unreal アプリを初めてパッケージ化する場合は、Epic Launcher からサポート ファイルをダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2b07-125">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span> 
>- <span data-ttu-id="f2b07-126">Epic Games Launcher の **[ライブラリ]** タブに移動し、 **[起動]** の横にあるドロップダウン矢印を選択して、 **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2b07-126">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span> 
>- <span data-ttu-id="f2b07-127">**[対応プラットフォーム]** で、 **[HoloLens 2]** を選択し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2b07-127">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span> 
><span data-ttu-id="f2b07-128">![プロジェクト設定 - 説明](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="f2b07-128">![Project Settings - Description](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="f2b07-129">**[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\)** に移動します。</span><span class="sxs-lookup"><span data-stu-id="f2b07-129">Go to **Edit > Project Settings**.</span></span> 
    * <span data-ttu-id="f2b07-130">**[Project]\(プロジェクト\) > [Description]\(説明\) > [About]\(情報\) > [Project Name]\(プロジェクト名\)** で、プロジェクト名を追加します。</span><span class="sxs-lookup"><span data-stu-id="f2b07-130">Add a project name under **Project > Description > About > Project Name**.</span></span> 
    * <span data-ttu-id="f2b07-131">**[Project]\(プロジェクト\) > [Description]\(説明\) > [Publisher]\(パブリッシャー\) > [Company Distinguished Name]\(企業識別名\)** に「**CN={INSERT COMPANY NAME}** 」を追加します。</span><span class="sxs-lookup"><span data-stu-id="f2b07-131">Add **CN={INSERT COMPANY NAME}** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2b07-132">これらのフィールドのいずれかを空白のままにすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f2b07-132">Leaving either of these fields blank will result in an error.</span></span> 

![プロジェクト設定 - 説明](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="f2b07-134">**[プラットフォーム] > [HoloLens]** で **[HoloLens Emulation 用にビルド]** または **[HoloLens Device 用にビルド]** を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f2b07-134">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="f2b07-135">**[パッケージ化]** セクション ( **[証明書に署名]** の横) の **[新規生成]** をクリックし、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f2b07-135">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**), then return to the Main window.</span></span>

![プロジェクト設定 - プラットフォーム - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="f2b07-137">**[File]\(ファイル\) > [Package Project]\(プロジェクトをパッケージ化\)** に移動し、 **[HoloLens]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f2b07-137">Go to **File > Package Project** and select **HoloLens**.</span></span> 
    * <span data-ttu-id="f2b07-138">パッケージを保存する新しいフォルダーを作成し、 **[Select Folder]\(フォルダーの選択\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2b07-138">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="f2b07-139">アプリがパッケージ化されたら、[Windows デバイス ポータル](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)を開き、 **[ビュー] > [アプリ]** に移動して、 **[Deploy apps]\(アプリのデプロイ\)** セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="f2b07-139">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="f2b07-140">**[参照...]** をクリックし、**ChessApp.appxbundle** ファイルに移動して **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2b07-140">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span> 

    * <span data-ttu-id="f2b07-141">デバイスに初めてアプリをインストールする場合は、 **[Allow me to select framework packages]\(フレームワーク パッケージを選択できるようにする\)** の横のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f2b07-141">Check the box next to **Allow me to select framework packages** if this is the first time you're installing the app on your device.</span></span> 
    * <span data-ttu-id="f2b07-142">次のダイアログで、適切な **VCLibs** および **appx** ファイルを組み込みます (デバイスの場合は arm64、エミュレーターの場合は x64)。</span><span class="sxs-lookup"><span data-stu-id="f2b07-142">In the next dialogue, include the appropriate **VCLibs** and **appx** files (arm64 for device, x64 for emulator).</span></span> <span data-ttu-id="f2b07-143">これらのファイルは、パッケージを保存したフォルダー内の **HoloLens** にあります。</span><span class="sxs-lookup"><span data-stu-id="f2b07-143">You can find these under **HoloLens** inside the folder where you saved your package.</span></span>

7.  <span data-ttu-id="f2b07-144">**[Install]** (インストール) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2b07-144">Click **Install**</span></span>
    * <span data-ttu-id="f2b07-145">これで、 **[すべてのアプリ]** に移動して、新しくインストールされたアプリをタップして実行するか、**Windows デバイス ポータル**から直接アプリを起動できます。</span><span class="sxs-lookup"><span data-stu-id="f2b07-145">You can now go to **All Apps** and tap the the newly installed app to run it, or you can start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="f2b07-146">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="f2b07-146">Congratulations!</span></span> <span data-ttu-id="f2b07-147">HoloLens Mixed Reality アプリケーションが完成し、準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="f2b07-147">You're HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="f2b07-148">ただし、これは目的地ではありません。</span><span class="sxs-lookup"><span data-stu-id="f2b07-148">However, this isn't the end of the road.</span></span> <span data-ttu-id="f2b07-149">MRTK には、空間マッピング、視線入力および音声入力、さらには QR コードなど、プロジェクトに追加できるスタンドアロン機能が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="f2b07-149">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="f2b07-150">これらの機能の詳細については、[Unreal 開発の概要](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2b07-150">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>