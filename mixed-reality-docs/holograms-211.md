---
title: MR 入力 211-ジェスチャ
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、ジェスチャの概念の詳細を確認してください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、academy、チュートリアル、ジェスチャ
ms.openlocfilehash: 694f51f1b56588e100d6d2676a8194d7e9936133
ms.sourcegitcommit: e9a55528965048ce34f8247ef6e544f9f432ee37
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69559878"
---
>[!NOTE]
><span data-ttu-id="1aea3-104">Mixed Reality Academy チュートリアルは、HoloLens (第1世代) と Mixed Reality イマーシブヘッドセットを念頭に置いて設計されています。</span><span class="sxs-lookup"><span data-stu-id="1aea3-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1aea3-105">そのため、これらのデバイスの開発に関するガイダンスをまだ探している開発者には、これらのチュートリアルを残しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="1aea3-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1aea3-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1aea3-107">サポートされているデバイスでの作業を続行するために管理されます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1aea3-108">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="1aea3-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1aea3-109">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="1aea3-110">MR 入力 211:ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="1aea3-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="1aea3-111">[ジェスチャ](gestures.md)によって、ユーザーの意図が動作するようになります。</span><span class="sxs-lookup"><span data-stu-id="1aea3-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="1aea3-112">ジェスチャを使用すると、ユーザーはホログラムを操作できます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="1aea3-113">このコースでは、ユーザーの手を追跡し、ユーザー入力に応答して、手動による状態と場所に基づいてユーザーにフィードバックを送る方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="1aea3-114">[MR 基本 101](holograms-101.md)では、単純なエアタップジェスチャを使用して、ホログラムを操作していました。</span><span class="sxs-lookup"><span data-stu-id="1aea3-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="1aea3-115">ここでは、エアタップのジェスチャを超えて、次のような新しい概念を見ていきます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="1aea3-116">ユーザーの手が追跡されていることを検出し、ユーザーにフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="1aea3-117">ナビゲーションジェスチャを使用して、ホログラムを回転させます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="1aea3-118">ユーザーの手が消えようとしているときにフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="1aea3-119">操作イベントを使用して、ユーザーが自分でホログラムを移動できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="1aea3-120">このコースでは、 [MR 入力 210](holograms-210.md)で構築した Unity プロジェクト**モデルエクスプローラー**について説明します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="1aea3-121">Astronaut の友人は、これらの新しいジェスチャの概念をご紹介します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="1aea3-122">以下の各章に埋め込まれているビデオは、古いバージョンの Unity と Mixed Reality Toolkit を使用して記録されています。</span><span class="sxs-lookup"><span data-stu-id="1aea3-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="1aea3-123">ステップバイステップの手順は正確であり、最新のものですが、最新ではない対応するビデオにスクリプトとビジュアルが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="1aea3-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="1aea3-124">ビデオはために含まれています。ここで説明する概念は引き続き適用されます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="1aea3-125">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="1aea3-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1aea3-126">まで</span><span class="sxs-lookup"><span data-stu-id="1aea3-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1aea3-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1aea3-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1aea3-128"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="1aea3-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="1aea3-129">MR 入力 211:ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="1aea3-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="1aea3-130">✔️</span><span class="sxs-lookup"><span data-stu-id="1aea3-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1aea3-131">✔️</span><span class="sxs-lookup"><span data-stu-id="1aea3-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="1aea3-132">開始前の準備</span><span class="sxs-lookup"><span data-stu-id="1aea3-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1aea3-133">前提条件</span><span class="sxs-lookup"><span data-stu-id="1aea3-133">Prerequisites</span></span>

* <span data-ttu-id="1aea3-134">適切な[ツールがインストール](install-the-tools.md)された WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="1aea3-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="1aea3-135">基本的なC#プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="1aea3-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="1aea3-136">[MR の基本 101](holograms-101.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="1aea3-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="1aea3-137">[MR 入力 210](holograms-210.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="1aea3-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="1aea3-138">[開発用に構成され](using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。</span><span class="sxs-lookup"><span data-stu-id="1aea3-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="1aea3-139">プロジェクトファイル</span><span class="sxs-lookup"><span data-stu-id="1aea3-139">Project files</span></span>

* <span data-ttu-id="1aea3-140">プロジェクトに必要な[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="1aea3-141"> Unity 2017.2 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="1aea3-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="1aea3-142">ファイルをデスクトップまたはその他の簡単な場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="1aea3-143">ダウンロードする前にソースコードを確認する場合は、GitHub から[入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)ます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="1aea3-144">エラッタとメモ</span><span class="sxs-lookup"><span data-stu-id="1aea3-144">Errata and Notes</span></span>

* <span data-ttu-id="1aea3-145">コード内のブレークポイントにヒットするには、Visual Studio の ツール-> オプション-> デバッグ の下にある マイコードのみを有効にする を無効 (*オフ*) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1aea3-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="1aea3-146">章 0-Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="1aea3-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="1aea3-147">手順</span><span class="sxs-lookup"><span data-stu-id="1aea3-147">Instructions</span></span>

1. <span data-ttu-id="1aea3-148">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-148">Start Unity.</span></span>
2. <span data-ttu-id="1aea3-149">**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-149">Select **Open**.</span></span>
3. <span data-ttu-id="1aea3-150">以前にアーカイブしていない**ジェスチャ**フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="1aea3-151">[**モデルエクスプローラー**の**開始**/] フォルダーを見つけて選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="1aea3-152">[**フォルダーの選択**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="1aea3-153">[**プロジェクト**] パネルで、[**シーン**] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="1aea3-154">[ **Modelexplorer**シーン] をダブルクリックして Unity に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="1aea3-155">ビルド</span><span class="sxs-lookup"><span data-stu-id="1aea3-155">Building</span></span>

1. <span data-ttu-id="1aea3-156">Unity で、[**ファイル > ビルド設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="1aea3-157">シーン **/ModelExplorer**が [**ビルド] の [シーン**] に表示されていない場合は、[開いているシーンの**追加**] をクリックしてシーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="1aea3-158">HoloLens 向けに特に開発している場合は、**ターゲットデバイス**を**hololens**に設定します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="1aea3-159">それ以外の場合は、**任意のデバイス**に残しておきます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="1aea3-160">**ビルドの種類**が [ **D3D** ] に設定され、[ **sdk** ] が [**最新のインストール済み**] に設定されていることを確認します (sdk 16299 以降である必要があります)。</span><span class="sxs-lookup"><span data-stu-id="1aea3-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="1aea3-161">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-161">Click **Build**.</span></span>
6. <span data-ttu-id="1aea3-162">"App" という名前の**新しいフォルダー**を作成します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="1aea3-163">**アプリ**フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="1aea3-164">**[フォルダーの選択]** をクリックすると、Unity によって Visual Studio のプロジェクトのビルドが開始されます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="1aea3-165">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="1aea3-166">**アプリ**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="1aea3-167">**Modelexplorer Visual Studio ソリューション**を開きます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="1aea3-168">HoloLens に展開する場合:</span><span class="sxs-lookup"><span data-stu-id="1aea3-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="1aea3-169">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから**リリース**に変更し、ARM から**x86**に変更します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="1aea3-170">[ローカルコンピューター] ボタンの横にあるドロップダウン矢印をクリックし、[**リモートコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="1aea3-171">**HoloLens デバイスの IP アドレス**を入力し、[認証モード] を [**ユニバーサル (暗号化**されていないプロトコル)] に設定します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="1aea3-172">**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-172">Click **Select**.</span></span> <span data-ttu-id="1aea3-173">デバイスの IP アドレスがわからない場合は、**設定 Network & Internet > 詳細オプション >** 確認してください。</span><span class="sxs-lookup"><span data-stu-id="1aea3-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="1aea3-174">上部のメニューバーで、[デバッグ]、[**デバッグなしで開始**] の順にクリック >、Ctrl キーを押し**ながら F5**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="1aea3-175">初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](using-visual-studio.md#pairing-your-device-hololens)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1aea3-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="1aea3-176">アプリが展開されたら、 **select ジェスチャ**を使用して、[ **fitbox** ] を閉じます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="1aea3-177">イマーシブヘッドセットに展開する場合:</span><span class="sxs-lookup"><span data-stu-id="1aea3-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="1aea3-178">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから**リリース**に、ARM から**x64**に変更します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="1aea3-179">配置ターゲットが**ローカルコンピューター**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="1aea3-180">上部のメニューバーで、[デバッグ]、[**デバッグなしで開始**] の順にクリック >、Ctrl キーを押し**ながら F5**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="1aea3-181">アプリがデプロイされたら、モーションコントローラーでトリガーをプルして、 **Fitbox ボックス**を閉じます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="1aea3-182">Visual Studio の [エラー] パネルに赤色のエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="1aea3-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="1aea3-183">無視しても安全です。</span><span class="sxs-lookup"><span data-stu-id="1aea3-183">It is safe to ignore them.</span></span> <span data-ttu-id="1aea3-184">実際のビルドの進行状況を表示するには、[出力] パネルに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="1aea3-185">[出力] パネルでエラーが発生した場合は、修正を行う必要があります (多くの場合、スクリプトの間違いが原因です)。</span><span class="sxs-lookup"><span data-stu-id="1aea3-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="1aea3-186">第1章でのフィードバックの検出</span><span class="sxs-lookup"><span data-stu-id="1aea3-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="1aea3-187">目的</span><span class="sxs-lookup"><span data-stu-id="1aea3-187">Objectives</span></span>

* <span data-ttu-id="1aea3-188">ハンドトラッキングイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="1aea3-189">カーソルのフィードバックを使用して、ユーザーを追跡しているときにユーザーを表示します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

>[!NOTE]
><span data-ttu-id="1aea3-190">HoloLens 2 では、両手が表示されると (指が指されているときだけではなく)、ハンド検出が発生します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-190">On HoloLens 2 , hands detected fires whenever hands are visible (not just when a finger is pointing up).</span></span>

### <a name="instructions"></a><span data-ttu-id="1aea3-191">手順</span><span class="sxs-lookup"><span data-stu-id="1aea3-191">Instructions</span></span>

* <span data-ttu-id="1aea3-192">[**階層**] パネルで、[ **inputmanager** ] オブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-192">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="1aea3-193">**GesturesInput**オブジェクトを探して選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-193">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="1aea3-194">**InteractionInputSource.cs**スクリプトは、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-194">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="1aea3-195">Interactionsourcedetected イベントと Interactionsourcedetected イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-195">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="1aea3-196">"ハンドラー検出" 状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-196">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="1aea3-197">Interactionsourcedetected イベントと Interactionsourcedetected イベントからアンサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-197">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="1aea3-198">次に、ユーザーの操作に応じてフィードバックが表示されるように、 [MR 入力 210](holograms-210.md)からカーソルをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-198">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="1aea3-199">[**階層**] パネルで、**カーソル**オブジェクトを選択して削除します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-199">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="1aea3-200">[**プロジェクト**] パネルで、[**カーソルとフィードバック**] を検索し、[**階層**] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-200">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="1aea3-201">[**階層**] パネルの [ **inputmanager** ] をクリックし 、[カーソル] を**選択**して、**階層**のカーソルの下にあるカーソルフィールドに**カーソル**をドラッグします。**インスペクター**。</span><span class="sxs-lookup"><span data-stu-id="1aea3-201">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="1aea3-202">**階層**内の**カーソル**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-202">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="1aea3-203">[**インスペクター** ] パネルで、**オブジェクトカーソル**スクリプトの [**カーソル状態データ**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-203">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="1aea3-204">**カーソル状態データ**は次のように動作します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-204">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="1aea3-205">**観察**状態は、何も検出されず、ユーザーが単に見ていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-205">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="1aea3-206">**対話**状態とは、手動またはコントローラーが検出されたことを意味します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-206">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="1aea3-207">**ホバー**状態は、ユーザーがホログラムを見ていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-207">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="1aea3-208">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="1aea3-208">Build and Deploy</span></span>

* <span data-ttu-id="1aea3-209">Unity では、**ファイル > ビルド設定**を使用して、アプリケーションをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-209">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="1aea3-210">**アプリ**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-210">Open the **App** folder.</span></span>
* <span data-ttu-id="1aea3-211">まだ開いていない場合は、 **Modelexplorer Visual Studio ソリューション**を開きます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-211">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="1aea3-212">(セットアップ時に Visual Studio でこのプロジェクトを既にビルドまたは展開している場合は、VS のインスタンスを開いて、メッセージが表示されたら [すべて再読み込み] をクリックします)。</span><span class="sxs-lookup"><span data-stu-id="1aea3-212">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="1aea3-213">Visual Studio で、[デバッグ]、[**デバッグなしで開始**] の順にクリック >、Ctrl キーを押し**ながら F5**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-213">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="1aea3-214">アプリケーションが HoloLens にデプロイされたら、エアタップジェスチャを使用して、fitbox ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-214">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="1aea3-215">手動での追跡を開始するには、自分をビューに移動して、インデックスの指を空にします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-215">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="1aea3-216">左、右、下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-216">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="1aea3-217">ハンドが検出され、ビューから失われたときに、カーソルがどのように変化するかを見てください。</span><span class="sxs-lookup"><span data-stu-id="1aea3-217">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="1aea3-218">イマーシブヘッドセットを使用している場合は、コントローラーに接続して接続を切断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1aea3-218">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="1aea3-219">接続されたコントローラーは常に "利用可能" になるため、このフィードバックはイマーシブデバイスではあまり興味がありません。</span><span class="sxs-lookup"><span data-stu-id="1aea3-219">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="1aea3-220">第2章-ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="1aea3-220">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="1aea3-221">目的</span><span class="sxs-lookup"><span data-stu-id="1aea3-221">Objectives</span></span>

* <span data-ttu-id="1aea3-222">Astronaut を回転させるには、ナビゲーションジェスチャイベントを使用します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-222">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="1aea3-223">手順</span><span class="sxs-lookup"><span data-stu-id="1aea3-223">Instructions</span></span>

<span data-ttu-id="1aea3-224">アプリでナビゲーションジェスチャを使用するには、 **GestureAction.cs**を編集して、ナビゲーションジェスチャが発生したときにオブジェクトを回転させます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-224">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="1aea3-225">また、ナビゲーションが利用可能になったときに表示されるように、カーソルにフィードバックを追加します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-225">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="1aea3-226">[**階層**] パネルで、[**カーソルとフィードバック**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-226">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="1aea3-227">**ホログラム**フォルダーで、 **scrollfeedback**資産を見つけます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-227">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="1aea3-228">**スクロールフィードバック**の Prefab を**階層**内の**カーソル**にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-228">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="1aea3-229">[**カーソル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-229">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="1aea3-230">[**インスペクター** ] パネルで、[**コンポーネントの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-230">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="1aea3-231">メニューで、検索ボックスに「カーソルの**フィードバック**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-231">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="1aea3-232">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-232">Select the search result.</span></span>
7. <span data-ttu-id="1aea3-233">**インスペクター**の [ **Cursor フィードバック**] コンポーネントの [**検出されたゲームオブジェクトをスクロール**] プロパティに、**階層**から**scrollfeedback**オブジェクトをドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-233">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="1aea3-234">[**階層**] パネルで、 **AstroMan**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-234">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="1aea3-235">[**インスペクター** ] パネルで、[**コンポーネントの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-235">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="1aea3-236">メニューで、[検索ボックスのジェスチャ]**アクション**を入力します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-236">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="1aea3-237">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-237">Select the search result.</span></span>

<span data-ttu-id="1aea3-238">次に、Visual Studio で**GestureAction.cs**を開きます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-238">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="1aea3-239">演習 2. c のコーディングで、スクリプトを編集して次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-239">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="1aea3-240">ナビゲーションジェスチャが実行されるたび**に、AstroMan オブジェクトを回転**します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-240">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="1aea3-241">**RotationFactor**を計算して、オブジェクトに適用される回転の量を制御します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-241">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="1aea3-242">ユーザーが手を左または右に移動したときに y 軸を中心に**オブジェクトを回転**します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-242">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="1aea3-243">スクリプトで演習 2. c のコーディングを完了するか、以下の完成したソリューションでコードを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-243">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

<span data-ttu-id="1aea3-244">他のナビゲーションイベントには、何らかの情報が既に入力されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="1aea3-244">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="1aea3-245">ユーザーは、ローテーションが開始されたときに、ユーザーが Astronaut にフォーカスを保持する必要がないように、このオブジェクトを Toolkit の InputSystem's モーダルスタックにプッシュします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-245">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="1aea3-246">同様に、ジェスチャが完了すると、そのオブジェクトはスタックからポップされます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-246">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="1aea3-247">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="1aea3-247">Build and Deploy</span></span>

1. <span data-ttu-id="1aea3-248">Unity でアプリケーションをリビルドし、Visual Studio からビルドしてデプロイし、HoloLens で実行します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-248">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="1aea3-249">Astronaut を見つめて、カーソルの両側に2つの矢印が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-249">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="1aea3-250">この新しいビジュアルは、astronaut を回転できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="1aea3-250">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="1aea3-251">HoloLens がハンドの追跡を開始するように、自分を準備完了の位置 (インデックスは空の指) に置きます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-251">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="1aea3-252">Astronaut を回転させるには、インデックスの指をピンチの位置に下げ、手を左または右に移動して NavigationX ジェスチャをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-252">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="1aea3-253">第3章-ガイダンス</span><span class="sxs-lookup"><span data-stu-id="1aea3-253">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="1aea3-254">目的</span><span class="sxs-lookup"><span data-stu-id="1aea3-254">Objectives</span></span>

* <span data-ttu-id="1aea3-255">ハンド**ガイダンススコア**を使用して、ハンドトラッキングがいつ失われるかを予測できます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-255">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="1aea3-256">ユーザーがカメラのビューの端に近づいたときに表示されるように **、カーソルに関するフィードバック**を提供します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-256">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="1aea3-257">手順</span><span class="sxs-lookup"><span data-stu-id="1aea3-257">Instructions</span></span>

1. <span data-ttu-id="1aea3-258">[**階層**] パネルで、[**カーソルとフィードバック**] オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-258">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="1aea3-259">[**インスペクター** ] パネルで、[**コンポーネントの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-259">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="1aea3-260">メニューの [検索] ボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-260">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="1aea3-261">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-261">Select the search result.</span></span>
4. <span data-ttu-id="1aea3-262">[**プロジェクト**] パネルの [**ホログラム**] フォルダーで、[ファイル] [ **guidguid] [フィードバック**] 資産を見つけます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-262">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="1aea3-263">[**インスペクター** ] パネルの [**ハンドガイダンスインジケーター** ] プロパティに、[ハンドラー] の [配布の**フィードバック**] 資産をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-263">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="1aea3-264">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="1aea3-264">Build and Deploy</span></span>

* <span data-ttu-id="1aea3-265">Unity でアプリケーションをリビルドし、Visual Studio からビルドしてデプロイし、HoloLens でアプリを体験します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-265">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="1aea3-266">手の形にして、インデックスの指を見て追跡します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-266">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="1aea3-267">ナビゲーションジェスチャを使用して astronaut の回転を開始します (インデックスの指とつまみを一緒にピンチします)。</span><span class="sxs-lookup"><span data-stu-id="1aea3-267">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="1aea3-268">左、右、上、下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-268">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="1aea3-269">ジェスチャフレームの端に近づくと、カーソルの横に矢印が表示され、ハンドトラッキングが失われることを警告します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-269">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="1aea3-270">矢印は、追跡が失われないようにするために、どの方向にハンドを移動するかを示します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-270">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="1aea3-271">章 4-操作</span><span class="sxs-lookup"><span data-stu-id="1aea3-271">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="1aea3-272">目的</span><span class="sxs-lookup"><span data-stu-id="1aea3-272">Objectives</span></span>

* <span data-ttu-id="1aea3-273">操作イベントを使用して、astronaut を自分の手に移動します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-273">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="1aea3-274">カーソルに関するフィードバックを提供して、操作を使用できるタイミングをユーザーに知らせます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-274">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="1aea3-275">手順</span><span class="sxs-lookup"><span data-stu-id="1aea3-275">Instructions</span></span>

<span data-ttu-id="1aea3-276">GestureManager.cs と AstronautManager.cs では、次のことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-276">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="1aea3-277">Speech キーワード "**Move Astronaut**" を使用して**操作**ジェスチャを有効にし、"**Rotate Astronaut**" を使用して無効にします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-277">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="1aea3-278">**操作ジェスチャレコグナイザー**に応答するように切り替えます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-278">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="1aea3-279">では、始めましょう。</span><span class="sxs-lookup"><span data-stu-id="1aea3-279">Let's get started.</span></span>

1. <span data-ttu-id="1aea3-280">[**階層**] パネルで、新しい空の作成オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-280">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="1aea3-281">"**AstronautManager**" という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-281">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="1aea3-282">[**インスペクター** ] パネルで、[**コンポーネントの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-282">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="1aea3-283">メニューで、検索ボックスに「 **Astronaut Manager**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-283">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="1aea3-284">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-284">Select the search result.</span></span>
4. <span data-ttu-id="1aea3-285">[**インスペクター** ] パネルで、[**コンポーネントの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="1aea3-286">メニューで、[検索] ボックスに「**音声入力ソース**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-286">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="1aea3-287">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-287">Select the search result.</span></span>

<span data-ttu-id="1aea3-288">ここで、astronaut の相互作用の状態を制御するために必要な音声コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-288">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="1aea3-289">**インスペクター**の [**キーワード**] セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-289">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="1aea3-290">右側に **+** あるをクリックして、新しいキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-290">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="1aea3-291">「 **Move Astronaut**」というキーワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-291">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="1aea3-292">必要に応じて、キーのショートカットを自由に追加できます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-292">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="1aea3-293">右側に **+** あるをクリックして、新しいキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-293">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="1aea3-294">「 **Rotate Astronaut**」というキーワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-294">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="1aea3-295">必要に応じて、キーのショートカットを自由に追加できます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-295">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="1aea3-296">対応するハンドラーコードは、 **GestureAction.cs**の**ISpeechHandler**ハンドラーにあります。</span><span class="sxs-lookup"><span data-stu-id="1aea3-296">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![第4章の音声入力ソースを設定する方法](images/holograms211-speech.png)

<span data-ttu-id="1aea3-298">次に、カーソルに対する操作に関するフィードバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-298">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="1aea3-299">[**プロジェクト**パネル] の [**ホログラム**] フォルダーで、 **pathingfeedback**資産を見つけます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-299">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="1aea3-300">**Pathingfeedback**の Prefab を**階層**内の**カーソル**にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-300">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="1aea3-301">[**階層**] パネルで、[**カーソル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-301">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="1aea3-302">**Pathingfeedback**オブジェクトを**階層**から、**インスペクター**の [ **Cursor フィードバック**] コンポーネントの [**パス検出されたゲームオブジェクト**] プロパティにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-302">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="1aea3-303">次のように、 **GestureAction.cs**にコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1aea3-303">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="1aea3-304">**IManipulationHandler**関数にコードを追加します。この関数は、**操作**ジェスチャが検出されたときに astronaut を移動します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-304">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="1aea3-305">**移動ベクター**を計算して、astronaut が手の位置に基づいて移動される場所を決定します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-305">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="1aea3-306">Astronaut を新しい位置に**移動**します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-306">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="1aea3-307">**GestureAction.cs**のコードを完全にコーディングするか、以下の完成したソリューションを使用します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-307">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="1aea3-308">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="1aea3-308">Build and Deploy</span></span>

* <span data-ttu-id="1aea3-309">Unity でリビルドし、Visual Studio からビルドしてデプロイし、HoloLens でアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-309">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="1aea3-310">HoloLens の前に手を置き、インデックスの指を上げて追跡できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-310">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="1aea3-311">Astronaut の上にカーソルを置きます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-311">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="1aea3-312">操作ジェスチャを使用して Astronaut を移動するには、「Move Astronaut」と言います。</span><span class="sxs-lookup"><span data-stu-id="1aea3-312">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="1aea3-313">カーソルの周囲に4つの矢印が表示され、プログラムが操作イベントに応答するようになったことを示します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-313">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="1aea3-314">インデックスを親指に下げて、pinched にしておきます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-314">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="1aea3-315">お客様の手を移動すると、astronaut も移動します (これは操作です)。</span><span class="sxs-lookup"><span data-stu-id="1aea3-315">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="1aea3-316">Astronaut の操作を停止するには、インデックスの指を上げます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-316">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="1aea3-317">注:手を動かす前に "Move Astronaut" と言うと、代わりにナビゲーションジェスチャが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-317">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="1aea3-318">"Rotate Astronaut" と言い、rotatable 状態に戻ります。</span><span class="sxs-lookup"><span data-stu-id="1aea3-318">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="1aea3-319">第5章-モデルの拡張</span><span class="sxs-lookup"><span data-stu-id="1aea3-319">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="1aea3-320">目的</span><span class="sxs-lookup"><span data-stu-id="1aea3-320">Objectives</span></span>

* <span data-ttu-id="1aea3-321">Astronaut モデルを、ユーザーが対話できる複数の小さなピースに拡張します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-321">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="1aea3-322">ナビゲーションと操作のジェスチャを使用して、各部分を個別に移動します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-322">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="1aea3-323">手順</span><span class="sxs-lookup"><span data-stu-id="1aea3-323">Instructions</span></span>

<span data-ttu-id="1aea3-324">このセクションでは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-324">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="1aea3-325">新しいキーワード "**Expand model**" を追加して、astronaut モデルを展開します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-325">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="1aea3-326">新しいキーワード "**Reset model**" を追加して、モデルを元の形式に戻します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-326">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="1aea3-327">これを行うには、前の章で説明した音声入力ソースに2つのキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-327">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="1aea3-328">また、認識イベントを処理する別の方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-328">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="1aea3-329">**インスペクター**の [Back on **AstronautManager** ] をクリックし、**インスペクター**の [**キーワード**] セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-329">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="1aea3-330">右側に **+** あるをクリックして、新しいキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-330">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="1aea3-331">[**モデルの展開**] としてキーワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-331">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="1aea3-332">必要に応じて、キーのショートカットを自由に追加できます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-332">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="1aea3-333">右側に **+** あるをクリックして、新しいキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-333">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="1aea3-334">「 **Reset Model**」というキーワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-334">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="1aea3-335">必要に応じて、キーのショートカットを自由に追加できます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-335">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="1aea3-336">[**インスペクター** ] パネルで、[**コンポーネントの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-336">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="1aea3-337">メニューで、[検索] ボックスに「**音声入力ハンドラー**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-337">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="1aea3-338">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-338">Select the search result.</span></span>
8. <span data-ttu-id="1aea3-339">これらのコマンドは、注目しているすべてのオブジェクトに関係なく動作するようにするため、**グローバルリスナーである**ことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1aea3-339">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="1aea3-340">ボタンをクリックし、[キーワード] ドロップダウンから [モデルの展開] を選択します。 **+**</span><span class="sxs-lookup"><span data-stu-id="1aea3-340">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="1aea3-341">[応答] の下をクリックし、 **AstronautManager**を**階層**から [**なし] (オブジェクト)** フィールドにドラッグします。 **+**</span><span class="sxs-lookup"><span data-stu-id="1aea3-341">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="1aea3-342">次に、[**関数なし**] ドロップダウンをクリックし、[ **AstronautManager**]、[ **expandmodelcommand**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-342">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="1aea3-343">音声入力ハンドラーの **+** ボタンをクリックし、[キーワード] ドロップダウンから [モデルの**リセット**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-343">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="1aea3-344">[応答] の下をクリックし、 **AstronautManager**を**階層**から [**なし] (オブジェクト)** フィールドにドラッグします。 **+**</span><span class="sxs-lookup"><span data-stu-id="1aea3-344">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="1aea3-345">次に、[**関数なし**] ドロップダウンをクリックし、[ **AstronautManager**]、[ **resetmodelcommand**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-345">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![第5章の音声入力ソースとハンドラーを設定する方法](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="1aea3-347">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="1aea3-347">Build and Deploy</span></span>

* <span data-ttu-id="1aea3-348">お試しください。</span><span class="sxs-lookup"><span data-stu-id="1aea3-348">Try it!</span></span> <span data-ttu-id="1aea3-349">アプリをビルドして HoloLens にデプロイします。</span><span class="sxs-lookup"><span data-stu-id="1aea3-349">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="1aea3-350">拡張された astronaut モデルを表示するには、[**モデルの展開**] を言います。</span><span class="sxs-lookup"><span data-stu-id="1aea3-350">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="1aea3-351">**ナビゲーション**を使用して、astronaut スーツの個々の要素を回転します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-351">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="1aea3-352">たとえば、 **Astronaut を移動**してから、**操作**を使用して Astronaut スーツの各部分を移動します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-352">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="1aea3-353">**Astronaut を回転**させて、ピースを再び回転させます。</span><span class="sxs-lookup"><span data-stu-id="1aea3-353">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="1aea3-354">Astronaut を元の形式に戻すには、 **Model をリセット**します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-354">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="1aea3-355">最後です</span><span class="sxs-lookup"><span data-stu-id="1aea3-355">The End</span></span>

<span data-ttu-id="1aea3-356">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="1aea3-356">Congratulations!</span></span> <span data-ttu-id="1aea3-357">これで MR 入力**211 が完了しました。ジェスチャ**。</span><span class="sxs-lookup"><span data-stu-id="1aea3-357">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="1aea3-358">ハンドトラッキング、ナビゲーション、操作のイベントを検出して対応する方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="1aea3-358">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="1aea3-359">ナビゲーションジェスチャと操作ジェスチャの違いを理解します。</span><span class="sxs-lookup"><span data-stu-id="1aea3-359">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="1aea3-360">カーソルを変更して、ハンドが検出されたとき、ハンドが失われるタイミング、およびオブジェクトが異なる相互作用 (ナビゲーションと操作) をサポートするタイミングについて視覚的にフィードバックを提供する方法を理解している。</span><span class="sxs-lookup"><span data-stu-id="1aea3-360">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
