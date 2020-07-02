---
title: 6. デバイスまたはエミュレーターへのパッケージ化とデプロイ
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 6
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: 99407a4069f914bf077e6323dde3e12978f6b765
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345692"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="ccc84-104">6.デバイスまたはエミュレーターへのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="ccc84-104">6. Packaging & deploying to device or emulator</span></span>

## <a name="overview"></a><span data-ttu-id="ccc84-105">概要</span><span class="sxs-lookup"><span data-stu-id="ccc84-105">Overview</span></span>

<span data-ttu-id="ccc84-106">前のチュートリアルでは、チェスの駒を元の位置にリセットする簡単なボタンを追加しました。</span><span class="sxs-lookup"><span data-stu-id="ccc84-106">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="ccc84-107">この最後のセクションでは、アプリを HoloLens 2 またはエミュレーターで実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ccc84-107">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="ccc84-108">HoloLens 2 をお持ちの場合は、コンピューターからストリーミングするか、アプリをパッケージ化してデバイス上で直接実行することができます。</span><span class="sxs-lookup"><span data-stu-id="ccc84-108">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="ccc84-109">デバイスがない場合は、エミュレーターで実行するアプリをパッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="ccc84-109">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="ccc84-110">このセクションを完了するまでに、対話式操作と UI を備えた、再生可能な Mixed Reality アプリがデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="ccc84-110">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="ccc84-111">目標</span><span class="sxs-lookup"><span data-stu-id="ccc84-111">Objectives</span></span>

* <span data-ttu-id="ccc84-112">[デバイスのみ] ホログラフィック アプリのリモート処理によって HoloLens 2 にストリーミングする</span><span class="sxs-lookup"><span data-stu-id="ccc84-112">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="ccc84-113">アプリをパッケージ化して HoloLens 2 のデバイスまたはエミュレーターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="ccc84-113">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="ccc84-114">[デバイスのみ] ストリーミング</span><span class="sxs-lookup"><span data-stu-id="ccc84-114">[Device Only] Streaming</span></span>
<span data-ttu-id="ccc84-115">この場合、[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) は、チャネルを切り替えるのではなく、PC またはスタンドアロンの UWP デバイスから HoloLens 2 にデータをストリーミングすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="ccc84-115">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) in this case means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="ccc84-116">これは、リモート処理ホスト アプリが HoloLens から入力データ ストリームを受け取り、仮想イマーシブ ビューでコンテンツをレンダリングし、Wi-Fi 経由でコンテンツ フレームを HoloLens にストリームするという仕組みになっています。</span><span class="sxs-lookup"><span data-stu-id="ccc84-116">The way this works is a remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="ccc84-117">ストリーミングを使用すると、リモートのイマーシブ ビューを既存のデスクトップ PC ソフトウェアに追加し、より多くのシステム リソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ccc84-117">Streaming allows you to add remote immersive views into existing desktop PC software and has access to more system resources.</span></span> 

<span data-ttu-id="ccc84-118">チェス アプリでこのルートを使用する場合は、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccc84-118">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="ccc84-119">Microsoft Store から **Holographic Remoting Player** を HoloLens 2 にインストールし、アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="ccc84-119">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span>

2.  <span data-ttu-id="ccc84-120">**[編集] > [プロジェクトの設定]** に移動し、 **[Holographic Remoting]** セクションで **[リモート処理を有効にする]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="ccc84-120">Go to **Edit > Project Settings** and check **enable remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="ccc84-121">エディターを再起動し、[デバイスの IP アドレスを検索](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi)して入力し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ccc84-121">Restart the editor, [find your device's IP address](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi) and enter it, then click **Connect**.</span></span>

<span data-ttu-id="ccc84-122">接続後、 **[Play]\(再生\)** ボタンの右側にあるドロップダウン矢印をクリックし、 **[VR Preview]\(VR プレビュー\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ccc84-122">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="ccc84-123">これにより、VR プレビュー ウィンドウでアプリが実行され、HoloLens ヘッドセットにストリーミングされます。</span><span class="sxs-lookup"><span data-stu-id="ccc84-123">This will run the app in the VR Preview Window, which is streamed to the HoloLens headset.</span></span> 

## <a name="packaging-and-deploying-the-app"></a><span data-ttu-id="ccc84-124">アプリのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="ccc84-124">Packaging and deploying the app</span></span> 

>[!NOTE]
><span data-ttu-id="ccc84-125">HoloLens 用の Unreal アプリを初めてパッケージ化する場合は、Epic Launcher からサポート ファイルをダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccc84-125">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span> 
>- <span data-ttu-id="ccc84-126">Epic Games Launcher の **[ライブラリ]** タブに移動し、 **[起動]** の横にあるドロップダウン矢印を選択して、 **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ccc84-126">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span> 
>- <span data-ttu-id="ccc84-127">**[対応プラットフォーム]** で、 **[HoloLens 2]** を選択し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ccc84-127">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span> 
><span data-ttu-id="ccc84-128">![プロジェクト設定 - 説明](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="ccc84-128">![Project Settings - Description](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="ccc84-129">**[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\)** に移動します。</span><span class="sxs-lookup"><span data-stu-id="ccc84-129">Go to **Edit > Project Settings**.</span></span> 
    * <span data-ttu-id="ccc84-130">**[Project]\(プロジェクト\) > [Description]\(説明\) > [About]\(情報\) > [Project Name]\(プロジェクト名\)** で、プロジェクト名を追加します。</span><span class="sxs-lookup"><span data-stu-id="ccc84-130">Add a project name under **Project > Description > About > Project Name**.</span></span> 
    * <span data-ttu-id="ccc84-131">**[Project]\(プロジェクト\) > [Description]\(説明\) > [Publisher]\(発行元\) > [Company Distinguished Name]\(企業識別名\)** で、「**CN=YourCompanyName**」を追加します。</span><span class="sxs-lookup"><span data-stu-id="ccc84-131">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ccc84-132">これらのフィールドのどちらかを空白のままにすると、手順 3 で新しい証明書を作成するときにエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ccc84-132">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="ccc84-133">発行元の名前は、[LADPv3 識別名形式](https://www.ietf.org/rfc/rfc2253.txt)である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccc84-133">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="ccc84-134">発行元の名前の形式が正しくないと、"署名キーが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="ccc84-134">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="ccc84-135">アプリをデジタル署名できませんでした。"</span><span class="sxs-lookup"><span data-stu-id="ccc84-135">The app could not be digitally signed."</span></span> <span data-ttu-id="ccc84-136">エラーがパッケージ化するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="ccc84-136">error upon packaging.</span></span>

![プロジェクト設定 - 説明](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="ccc84-138">**[プラットフォーム] > [HoloLens]** で **[HoloLens Emulation 用にビルド]** または **[HoloLens Device 用にビルド]** を有効にします。</span><span class="sxs-lookup"><span data-stu-id="ccc84-138">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="ccc84-139">**[パッケージ化]** セクション ( **[証明書に署名]** の横) の **[新規生成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ccc84-139">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ccc84-140">既に生成されている証明書を使用している場合、証明書の発行者名はアプリケーションの発行元名と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccc84-140">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="ccc84-141">同じでない場合は、"署名キーが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="ccc84-141">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="ccc84-142">アプリをデジタル署名できませんでした。"</span><span class="sxs-lookup"><span data-stu-id="ccc84-142">The app could not be digitally signed."</span></span> <span data-ttu-id="ccc84-143">エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ccc84-143">error.</span></span>

![プロジェクト設定 - プラットフォーム - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="ccc84-145">秘密キーのパスワードを作成するように求めるメッセージが表示されたら、テスト目的の場合は **[なし]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ccc84-145">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![新しい証明書の生成](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="ccc84-147">**[File]\(ファイル\) > [Package Project]\(プロジェクトをパッケージ化\)** に移動し、 **[HoloLens]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ccc84-147">Go to **File > Package Project** and select **HoloLens**.</span></span> 
    * <span data-ttu-id="ccc84-148">パッケージを保存する新しいフォルダーを作成し、 **[Select Folder]\(フォルダーの選択\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ccc84-148">Create a new folder to save your package in and click **Select Folder**.</span></span> 

6.  <span data-ttu-id="ccc84-149">アプリがパッケージ化されたら、[Windows デバイス ポータル](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)を開き、 **[ビュー] > [アプリ]** に移動して、 **[Deploy apps]\(アプリのデプロイ\)** セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="ccc84-149">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="ccc84-150">**[参照...]** をクリックし、**ChessApp.appxbundle** ファイルに移動して **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ccc84-150">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span> 

    * <span data-ttu-id="ccc84-151">デバイスに初めてアプリをインストールする場合は、 **[Allow me to select framework packages]\(フレームワーク パッケージを選択できるようにする\)** の横のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="ccc84-151">Check the box next to **Allow me to select framework packages** if this is the first time you're installing the app on your device.</span></span> 
    * <span data-ttu-id="ccc84-152">次のダイアログで、適切な **VCLibs** および **appx** ファイルを組み込みます (デバイスの場合は arm64、エミュレーターの場合は x64)。</span><span class="sxs-lookup"><span data-stu-id="ccc84-152">In the next dialogue, include the appropriate **VCLibs** and **appx** files (arm64 for device, x64 for emulator).</span></span> <span data-ttu-id="ccc84-153">これらのファイルは、パッケージを保存したフォルダー内の **HoloLens** にあります。</span><span class="sxs-lookup"><span data-stu-id="ccc84-153">You can find these under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="ccc84-154">**[Install]** (インストール) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ccc84-154">Click **Install**</span></span>
    * <span data-ttu-id="ccc84-155">これで、 **[すべてのアプリ]** に移動して、新しくインストールされたアプリをタップして実行するか、**Windows デバイス ポータル**から直接アプリを起動できます。</span><span class="sxs-lookup"><span data-stu-id="ccc84-155">You can now go to **All Apps** and tap the the newly installed app to run it, or you can start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="ccc84-156">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="ccc84-156">Congratulations!</span></span> <span data-ttu-id="ccc84-157">HoloLens Mixed Reality アプリケーションが完成し、準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="ccc84-157">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="ccc84-158">ただし、これは目的地ではありません。</span><span class="sxs-lookup"><span data-stu-id="ccc84-158">However, this isn't the end of the road.</span></span> <span data-ttu-id="ccc84-159">MRTK には、空間マッピング、視線入力および音声入力、さらには QR コードなど、プロジェクトに追加できるスタンドアロン機能が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="ccc84-159">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="ccc84-160">これらの機能の詳細については、[Unreal 開発の概要](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ccc84-160">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>
