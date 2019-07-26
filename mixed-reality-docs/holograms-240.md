---
title: MR 共有 240-複数の HoloLens デバイス
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、ホログラムの共有の詳細を確認してください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、共有、ネットワーク、academy、チュートリアル
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522334"
---
>[!NOTE]
><span data-ttu-id="3b771-104">Mixed Reality Academy チュートリアルは、HoloLens (第1世代) と Mixed Reality イマーシブヘッドセットを念頭に置いて設計されています。</span><span class="sxs-lookup"><span data-stu-id="3b771-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="3b771-105">そのため、これらのデバイスの開発に関するガイダンスをまだ探している開発者には、これらのチュートリアルを残しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="3b771-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="3b771-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="3b771-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="3b771-107">サポートされているデバイスでの作業を続行するために管理されます。</span><span class="sxs-lookup"><span data-stu-id="3b771-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="3b771-108">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="3b771-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="3b771-109">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="3b771-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="3b771-110">MR 共有 240:複数の HoloLens デバイス</span><span class="sxs-lookup"><span data-stu-id="3b771-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="3b771-111">ホログラムは、領域内での移動によって、世界中に残されています。</span><span class="sxs-lookup"><span data-stu-id="3b771-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="3b771-112">HoloLens は、さまざまな[座標](coordinate-systems.md)系を使用して、オブジェクトの位置と向きを追跡することで、ホログラムを保持します。</span><span class="sxs-lookup"><span data-stu-id="3b771-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="3b771-113">これらの座標系をデバイス間で共有すると、共有された holographic 世界に参加するための共有エクスペリエンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3b771-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="3b771-114">このチュートリアルでは、次のことについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3b771-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="3b771-115">共有エクスペリエンスのためにネットワークをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="3b771-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="3b771-116">HoloLens デバイス間でホログラムを共有します。</span><span class="sxs-lookup"><span data-stu-id="3b771-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="3b771-117">共有 holographic 世界の他のメンバーを発見します。</span><span class="sxs-lookup"><span data-stu-id="3b771-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="3b771-118">他のプレーヤーをターゲットにして projectiles を起動できる、共有のインタラクティブなエクスペリエンスを作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="3b771-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="3b771-119">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="3b771-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="3b771-120">まで</span><span class="sxs-lookup"><span data-stu-id="3b771-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="3b771-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="3b771-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="3b771-122"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="3b771-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="3b771-123">MR 共有 240:複数の HoloLens デバイス</span><span class="sxs-lookup"><span data-stu-id="3b771-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="3b771-124">✔️</span><span class="sxs-lookup"><span data-stu-id="3b771-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="3b771-125">開始前の準備</span><span class="sxs-lookup"><span data-stu-id="3b771-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="3b771-126">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3b771-126">Prerequisites</span></span>

* <span data-ttu-id="3b771-127">インターネットアクセスを使用して適切な[ツールがインストール](install-the-tools.md)されている WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="3b771-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="3b771-128">[開発用に構成された](using-visual-studio.md#enabling-developer-mode)少なくとも2つの HoloLens デバイス。</span><span class="sxs-lookup"><span data-stu-id="3b771-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="3b771-129">プロジェクトファイル</span><span class="sxs-lookup"><span data-stu-id="3b771-129">Project files</span></span>

* <span data-ttu-id="3b771-130">プロジェクトに必要な[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="3b771-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="3b771-131">Unity 2017.2 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="3b771-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="3b771-132">引き続き Unity 5.6 のサポートが必要な場合は、[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="3b771-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="3b771-133">引き続き Unity 5.5 のサポートが必要な場合は、[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="3b771-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="3b771-134">引き続き Unity 5.4 のサポートが必要な場合は、[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="3b771-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="3b771-135">ファイルをデスクトップまたはその他の簡単な場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="3b771-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="3b771-136">フォルダー名を**Sharedholograms**として保持します。</span><span class="sxs-lookup"><span data-stu-id="3b771-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="3b771-137">ダウンロードする前にソースコードを確認する場合は、GitHub から[入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)ます。</span><span class="sxs-lookup"><span data-stu-id="3b771-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="3b771-138">Chapter 1-Holo World</span><span class="sxs-lookup"><span data-stu-id="3b771-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="3b771-139">この章では、最初の Unity プロジェクトをセットアップし、ビルドとデプロイのプロセスをステップ実行します。</span><span class="sxs-lookup"><span data-stu-id="3b771-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="3b771-140">目的</span><span class="sxs-lookup"><span data-stu-id="3b771-140">Objectives</span></span>

* <span data-ttu-id="3b771-141">Unity をセットアップして、holographic アプリを開発します。</span><span class="sxs-lookup"><span data-stu-id="3b771-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="3b771-142">ホログラムをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3b771-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="3b771-143">手順</span><span class="sxs-lookup"><span data-stu-id="3b771-143">Instructions</span></span>

* <span data-ttu-id="3b771-144">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-144">Start Unity.</span></span>
* <span data-ttu-id="3b771-145">**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-145">Select **Open**.</span></span>
* <span data-ttu-id="3b771-146">以前に unarchived した**Sharedholograms**フォルダーとして場所を入力します。</span><span class="sxs-lookup"><span data-stu-id="3b771-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="3b771-147">[**プロジェクト名**] を選択し、[**フォルダーの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="3b771-148">**階層**で、**メインカメラ**を右クリックし、[**削除**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="3b771-149">**HoloToolkit-240/Prefabs/カメラ**フォルダーで、**メインカメラ**の事前 fab を見つけます。</span><span class="sxs-lookup"><span data-stu-id="3b771-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="3b771-150">**メインカメラ**を**階層**にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="3b771-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="3b771-151">**階層**で、[**作成**] をクリックし、[**空の作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="3b771-152">新しい [作成]**オブジェクト**を右クリックし、[**名前の変更**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="3b771-153">**HologramCollection**オブジェクトの名前を「」に変更します。</span><span class="sxs-lookup"><span data-stu-id="3b771-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="3b771-154">**階層**内の**HologramCollection**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="3b771-155">**インスペクター**で、**変換位置**を次のように設定します。**閉じる0、Y:-0.25、Z:2**.</span><span class="sxs-lookup"><span data-stu-id="3b771-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="3b771-156">[**プロジェクト] パネル**の [**ホログラム**] フォルダーで、 **EnergyHub**資産を見つけます。</span><span class="sxs-lookup"><span data-stu-id="3b771-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="3b771-157">[**プロジェクト] パネル**から、 **EnergyHub**オブジェクトを**HologramCollection の子**として**階層**にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="3b771-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="3b771-158">[**ファイル] > 選択してシーンを保存...**</span><span class="sxs-lookup"><span data-stu-id="3b771-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="3b771-159">シーンに**Sharedholograms**という名前を付け、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="3b771-160">Unity の [**再生**] ボタンをクリックして、ホログラムをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="3b771-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="3b771-161">プレビューモードを停止するには、もう一度**Play**を押します。</span><span class="sxs-lookup"><span data-stu-id="3b771-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="3b771-162">**Unity から Visual Studio にプロジェクトをエクスポートする**</span><span class="sxs-lookup"><span data-stu-id="3b771-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="3b771-163">Unity で、[**ファイル > ビルド設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="3b771-164">シーンを追加するには、[開いている**シーンの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="3b771-165">[**プラットフォーム**] ボックスの一覧の [**ユニバーサル Windows プラットフォーム**] を選択し、[**プラットフォームの切り替え**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="3b771-166">**SDK**を**Universal 10**に設定します。</span><span class="sxs-lookup"><span data-stu-id="3b771-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="3b771-167">**ターゲットデバイス**を**HoloLens**に設定し、 **UWP ビルドの種類**を**D3D**に設定します。</span><span class="sxs-lookup"><span data-stu-id="3b771-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="3b771-168">**Unity C#プロジェクト**を確認します。</span><span class="sxs-lookup"><span data-stu-id="3b771-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="3b771-169">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-169">Click **Build**.</span></span>
* <span data-ttu-id="3b771-170">表示された [エクスプローラー] ウィンドウで、"App" という名前の**新しいフォルダー**を作成します。</span><span class="sxs-lookup"><span data-stu-id="3b771-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="3b771-171">**アプリ**フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="3b771-172">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="3b771-173">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3b771-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="3b771-174">**アプリ**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="3b771-174">Open the **App** folder.</span></span>
* <span data-ttu-id="3b771-175">**Sharedholograms**を開いて、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="3b771-176">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから**リリース**に変更し、ARM から**X86**に変更します。</span><span class="sxs-lookup"><span data-stu-id="3b771-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="3b771-177">[ローカルコンピューター] の横にあるドロップダウン矢印をクリックし、[**リモートデバイス**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="3b771-178">**アドレス**を HoloLens の名前または IP アドレスに設定します。</span><span class="sxs-lookup"><span data-stu-id="3b771-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="3b771-179">デバイスの IP アドレスがわからない場合は、設定 の **ネットワーク & Internet > 詳細オプション >** 確認するか、cortana**に "Cortana さん、どのような IP アドレスがあるか" を**確認してください。</span><span class="sxs-lookup"><span data-stu-id="3b771-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="3b771-180">**認証モード**(**ユニバーサル**) に設定したままにします。</span><span class="sxs-lookup"><span data-stu-id="3b771-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="3b771-181">[**選択] を**クリック</span><span class="sxs-lookup"><span data-stu-id="3b771-181">Click **Select**</span></span>
* <span data-ttu-id="3b771-182">[デバッグ] をクリックして [**デバッグなしで開始**] を >、Ctrl キーを押し**ながら F5**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="3b771-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="3b771-183">初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](using-visual-studio.md#pairing-your-device-hololens)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b771-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="3b771-184">HoloLens に配置し、EnergyHub ホログラムを見つけます。</span><span class="sxs-lookup"><span data-stu-id="3b771-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="3b771-185">Chapter 2-相互作用</span><span class="sxs-lookup"><span data-stu-id="3b771-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="3b771-186">この章では、ホログラムを操作します。</span><span class="sxs-lookup"><span data-stu-id="3b771-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="3b771-187">最初に、[見つめ](gaze.md)を視覚化するカーソルを追加します。</span><span class="sxs-lookup"><span data-stu-id="3b771-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="3b771-188">次に、[ジェスチャ](gestures.md)を追加し、手を使用してホログラムをスペースに配置します。</span><span class="sxs-lookup"><span data-stu-id="3b771-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="3b771-189">目的</span><span class="sxs-lookup"><span data-stu-id="3b771-189">Objectives</span></span>

* <span data-ttu-id="3b771-190">行方向の入力を使用してカーソルを制御します。</span><span class="sxs-lookup"><span data-stu-id="3b771-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="3b771-191">ジェスチャ入力を使用して、ホログラムを操作します。</span><span class="sxs-lookup"><span data-stu-id="3b771-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="3b771-192">手順</span><span class="sxs-lookup"><span data-stu-id="3b771-192">Instructions</span></span>

<span data-ttu-id="3b771-193">**視線入力**</span><span class="sxs-lookup"><span data-stu-id="3b771-193">**Gaze**</span></span>
* <span data-ttu-id="3b771-194">[**階層] パネル**で、 **HologramCollection**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3b771-195">[**インスペクター] パネル**で、[**コンポーネントの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="3b771-196">メニューの [検索] ボックスに「と入力し**てください」** と入力します。</span><span class="sxs-lookup"><span data-stu-id="3b771-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="3b771-197">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-197">Select the search result.</span></span>
* <span data-ttu-id="3b771-198">**HoloToolkit-Sharing-240\Prefabs\Input**フォルダーで、**カーソル**アセットを見つけます。</span><span class="sxs-lookup"><span data-stu-id="3b771-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="3b771-199">**カーソル**アセットを**階層**にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="3b771-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="3b771-200">**ジェスチャ**</span><span class="sxs-lookup"><span data-stu-id="3b771-200">**Gesture**</span></span>
* <span data-ttu-id="3b771-201">[**階層] パネル**で、 **HologramCollection**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3b771-202">[**コンポーネントの追加**] をクリックし、検索フィールドに「**ジェスチャマネージャー** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3b771-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="3b771-203">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-203">Select the search result.</span></span>
* <span data-ttu-id="3b771-204">[**階層] パネル**で、[ **HologramCollection**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="3b771-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="3b771-205">子**EnergyHub**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="3b771-206">[**インスペクター] パネル**で、[**コンポーネントの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="3b771-207">メニューで、検索ボックスの**ホログラムの配置**を入力します。</span><span class="sxs-lookup"><span data-stu-id="3b771-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="3b771-208">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-208">Select the search result.</span></span>
* <span data-ttu-id="3b771-209">**ファイル > シーンの保存** を選択してシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="3b771-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="3b771-210">**デプロイと活用**</span><span class="sxs-lookup"><span data-stu-id="3b771-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="3b771-211">前の章の指示に従って、HoloLens にビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="3b771-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="3b771-212">HoloLens でアプリが起動したら、頭を動かして、EnergyHub がどのようになっているかをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="3b771-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="3b771-213">ホログラムを見つめたときにカーソルがどのように表示されるかに注目してください。また、ホログラムで見られない場合はポイントライトに変わります。</span><span class="sxs-lookup"><span data-stu-id="3b771-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="3b771-214">エアタップを実行して、ホログラムを配置します。</span><span class="sxs-lookup"><span data-stu-id="3b771-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="3b771-215">この時点で、このプロジェクトでは、ホログラムを1回だけ配置できます (再デプロイしてもう一度試すことができます)。</span><span class="sxs-lookup"><span data-stu-id="3b771-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="3b771-216">第3章-共有座標</span><span class="sxs-lookup"><span data-stu-id="3b771-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="3b771-217">ホログラムを見て操作するのは楽しい作業ですが、さらに詳しく見ていきましょう。</span><span class="sxs-lookup"><span data-stu-id="3b771-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="3b771-218">最初の共有エクスペリエンスを設定します。すべてのユーザーが一緒に見ることができます。</span><span class="sxs-lookup"><span data-stu-id="3b771-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="3b771-219">目的</span><span class="sxs-lookup"><span data-stu-id="3b771-219">Objectives</span></span>

* <span data-ttu-id="3b771-220">共有エクスペリエンスのためにネットワークをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="3b771-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="3b771-221">共通の参照ポイントを確立します。</span><span class="sxs-lookup"><span data-stu-id="3b771-221">Establish a common reference point.</span></span>
* <span data-ttu-id="3b771-222">デバイス間で座標系を共有します。</span><span class="sxs-lookup"><span data-stu-id="3b771-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="3b771-223">全員が同じホログラムを見ることがあります。</span><span class="sxs-lookup"><span data-stu-id="3b771-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="3b771-224">アプリが共有サーバーに接続するには、 **Internetclientserver**と**PrivateNetworkClientServer**の機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b771-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="3b771-225">これは、既にホログラム240に含まれていますが、独自のプロジェクトでは考慮しておいてください。</span><span class="sxs-lookup"><span data-stu-id="3b771-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="3b771-226">Unity エディターで、[Edit > Project Settings > Player] の順に移動して、windows media player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="3b771-227">[Windows ストア] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="3b771-228">[発行の設定 > 機能] セクションで、 **Internetclientserver**の機能と**PrivateNetworkClientServer**機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="3b771-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="3b771-229">手順</span><span class="sxs-lookup"><span data-stu-id="3b771-229">Instructions</span></span>

* <span data-ttu-id="3b771-230">[**プロジェクト] パネル**で、 **HoloToolkit-Sharing-240\Prefabs\Sharing**フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="3b771-231">**共有**prefab を [**階層] パネル**にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="3b771-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="3b771-232">次に、共有サービスを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b771-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="3b771-233">この手順を実行する必要があるのは、共有エクスペリエンス内の**1 台の PC**だけです。</span><span class="sxs-lookup"><span data-stu-id="3b771-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="3b771-234">Unity で、上部のメニューの [ **HoloToolkit-240] メニュー**を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="3b771-235">ドロップダウンリストで [**共有サービスの起動**] 項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="3b771-236">[**プライベートネットワーク**] オプションをオンにし、[ファイアウォールプロンプトが表示されたら**アクセスを許可**する] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="3b771-237">共有サービスコンソールウィンドウに表示されている IPv4 アドレスをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="3b771-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="3b771-238">これは、サービスが実行されているコンピューターと同じ IP です。</span><span class="sxs-lookup"><span data-stu-id="3b771-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="3b771-239">共有エクスペリエンスに参加するすべての**pc**で、残りの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3b771-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="3b771-240">**階層**で、**共有**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="3b771-241">**インスペクター**の [**共有ステージ**] コンポーネントで、**サーバーのアドレス**を "localhost" から、sharingservice .exe を実行しているコンピューターの IPv4 アドレスに変更します。</span><span class="sxs-lookup"><span data-stu-id="3b771-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="3b771-242">**階層**で、 **HologramCollection**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3b771-243">**インスペクター**で [コンポーネントの**追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="3b771-244">検索ボックスに、「 **Import Export Anchor Manager**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3b771-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="3b771-245">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-245">Select the search result.</span></span>
* <span data-ttu-id="3b771-246">[**プロジェクト] パネル**で、 **Scripts**フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="3b771-247">**HologramPlacement**スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="3b771-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="3b771-248">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3b771-248">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="3b771-249">Unity に戻り、[**階層] パネル**で [ **HologramCollection** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="3b771-250">[**インスペクター] パネル**で、[**コンポーネントの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="3b771-251">メニューで、検索ボックスに「 **App State Manager**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3b771-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="3b771-252">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-252">Select the search result.</span></span>

<span data-ttu-id="3b771-253">**デプロイと活用**</span><span class="sxs-lookup"><span data-stu-id="3b771-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="3b771-254">HoloLens デバイス用のプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="3b771-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="3b771-255">1つの HoloLens を最初に展開するように指定します。</span><span class="sxs-lookup"><span data-stu-id="3b771-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="3b771-256">EnergyHub を配置する前に、アンカーがサービスにアップロードされるまで待機する必要があります (これには約30-60 秒かかることがあります)。</span><span class="sxs-lookup"><span data-stu-id="3b771-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="3b771-257">アップロードが完了するまで、タップジェスチャは無視されます。</span><span class="sxs-lookup"><span data-stu-id="3b771-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="3b771-258">EnergyHub が配置されると、その場所がサービスにアップロードされ、他のすべての HoloLens デバイスに展開できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3b771-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="3b771-259">新しい HoloLens が最初にセッションに参加したときに、そのデバイスで EnergyHub の場所が正しくない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3b771-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="3b771-260">ただし、アンカーと EnergyHub の場所がサービスからダウンロードされるとすぐに、EnergyHub は新しい共有の場所に移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b771-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="3b771-261">これが約30-60 秒以内に行われない場合は、アンカーを設定して、より多くの環境の手掛かりを収集するときに、元の HoloLens がどこにあったかを説明します。</span><span class="sxs-lookup"><span data-stu-id="3b771-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="3b771-262">その場所がまだロックされていない場合は、デバイスに再デプロイします。</span><span class="sxs-lookup"><span data-stu-id="3b771-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="3b771-263">デバイスの準備が完了し、アプリを実行している場合は、EnergyHub を探します。</span><span class="sxs-lookup"><span data-stu-id="3b771-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="3b771-264">ホログラムの場所とテキストがどの方向に接しているかについては、すべて同意できますか。</span><span class="sxs-lookup"><span data-stu-id="3b771-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="3b771-265">Chapter 4-検出</span><span class="sxs-lookup"><span data-stu-id="3b771-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="3b771-266">全員が同じホログラムを見ることができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="3b771-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="3b771-267">それでは、共有 holographic 世界に接続されているすべてのユーザーを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="3b771-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="3b771-268">この章では、同じ共有セッション内の他のすべての HoloLens デバイスの場所とローテーションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3b771-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="3b771-269">目的</span><span class="sxs-lookup"><span data-stu-id="3b771-269">Objectives</span></span>

* <span data-ttu-id="3b771-270">共有エクスペリエンスで互いを検出します。</span><span class="sxs-lookup"><span data-stu-id="3b771-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="3b771-271">プレーヤーアバターを選択して共有します。</span><span class="sxs-lookup"><span data-stu-id="3b771-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="3b771-272">すべてのユーザーのヘッドの横に、プレーヤーアバターを添付します。</span><span class="sxs-lookup"><span data-stu-id="3b771-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="3b771-273">手順</span><span class="sxs-lookup"><span data-stu-id="3b771-273">Instructions</span></span>

* <span data-ttu-id="3b771-274">[**プロジェクト] パネル**で、[**ホログラム**] フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="3b771-275">**PlayerAvatarStore**を**階層**にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="3b771-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="3b771-276">[**プロジェクト] パネル**で、 **Scripts**フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="3b771-277">**AvatarSelector**スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="3b771-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="3b771-278">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3b771-278">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* <span data-ttu-id="3b771-279">**階層**で、 **HologramCollection**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3b771-280">**インスペクター**で [**コンポーネントの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="3b771-281">検索ボックスに、「 **Local Player Manager**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3b771-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="3b771-282">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-282">Select the search result.</span></span>
* <span data-ttu-id="3b771-283">**階層**で、 **HologramCollection**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3b771-284">**インスペクター**で [**コンポーネントの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="3b771-285">検索ボックスに、「**リモートプレーヤーマネージャー**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3b771-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="3b771-286">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-286">Select the search result.</span></span>
* <span data-ttu-id="3b771-287">Visual Studio で**HologramPlacement**スクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="3b771-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="3b771-288">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3b771-288">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="3b771-289">Visual Studio で**AppStateManager**スクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="3b771-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="3b771-290">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3b771-290">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

<span data-ttu-id="3b771-291">**デプロイと活用**</span><span class="sxs-lookup"><span data-stu-id="3b771-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="3b771-292">プロジェクトをビルドし、HoloLens デバイスにデプロイします。</span><span class="sxs-lookup"><span data-stu-id="3b771-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="3b771-293">Ping 音が聞こえたら、アバター選択メニューを見つけて、エアタップジェスチャでアバターを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="3b771-294">ホログラムを見ていない場合、カーソルの周囲のポイントライトは、HoloLens がサービスと通信しているときに、(濃い紫の) 初期化、アンカーのダウンロード (緑)、場所データのインポート/エクスポート (黄) のときに、異なる色になります。アンカー (青) をアップロードしています。</span><span class="sxs-lookup"><span data-stu-id="3b771-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="3b771-295">カーソルの周囲のポイントライトが既定の色 (淡い紫) の場合は、セッション内の他のプレーヤーと対話する準備ができています。</span><span class="sxs-lookup"><span data-stu-id="3b771-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="3b771-296">スペースに接続されている他のユーザーを確認します。 holographic ロボットはショルダーの上にフローティングし、頭の動きを模倣しています。</span><span class="sxs-lookup"><span data-stu-id="3b771-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="3b771-297">章 5: 配置</span><span class="sxs-lookup"><span data-stu-id="3b771-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="3b771-298">この章では、アンカーを実際のサーフェイスに配置できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3b771-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="3b771-299">共有座標を使用して、共有エクスペリエンスに接続されているすべてのユーザー間の中間点にアンカーを配置します。</span><span class="sxs-lookup"><span data-stu-id="3b771-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="3b771-300">目的</span><span class="sxs-lookup"><span data-stu-id="3b771-300">Objectives</span></span>

* <span data-ttu-id="3b771-301">プレーヤーのヘッド位置に基づいて、空間マップにホログラムを配置します。</span><span class="sxs-lookup"><span data-stu-id="3b771-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="3b771-302">手順</span><span class="sxs-lookup"><span data-stu-id="3b771-302">Instructions</span></span>

* <span data-ttu-id="3b771-303">[**プロジェクト] パネル**で、[**ホログラム**] フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="3b771-304">**CustomSpatialMapping** Prefab を**階層**にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="3b771-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="3b771-305">[**プロジェクト] パネル**で、 **Scripts**フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="3b771-306">**AppStateManager**スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="3b771-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="3b771-307">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3b771-307">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* <span data-ttu-id="3b771-308">[**プロジェクト] パネル**で、 **Scripts**フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="3b771-309">**HologramPlacement**スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="3b771-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="3b771-310">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3b771-310">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

<span data-ttu-id="3b771-311">**デプロイと活用**</span><span class="sxs-lookup"><span data-stu-id="3b771-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="3b771-312">プロジェクトをビルドし、HoloLens デバイスにデプロイします。</span><span class="sxs-lookup"><span data-stu-id="3b771-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="3b771-313">アプリの準備が整ったら、サークルに EnergyHub て、すべてのユーザーの中央に表示されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3b771-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="3b771-314">タップして、EnergyHub を配置します。</span><span class="sxs-lookup"><span data-stu-id="3b771-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="3b771-315">音声コマンド ' Reset Target ' を使用して EnergyHub バックアップを選択し、グループとして連携して、ホログラムを新しい場所に移動してみてください。</span><span class="sxs-lookup"><span data-stu-id="3b771-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="3b771-316">第6章-実際の物理</span><span class="sxs-lookup"><span data-stu-id="3b771-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="3b771-317">この章では、現実世界の表面にバウンスするホログラムを追加します。</span><span class="sxs-lookup"><span data-stu-id="3b771-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="3b771-318">自分と友人の両方によって起動されたプロジェクトで、スペースを埋めることができます。</span><span class="sxs-lookup"><span data-stu-id="3b771-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="3b771-319">目的</span><span class="sxs-lookup"><span data-stu-id="3b771-319">Objectives</span></span>

* <span data-ttu-id="3b771-320">現実世界の表面にバウンドする projectiles を起動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="3b771-321">他のプレーヤーが見ることができるように、projectiles を共有します。</span><span class="sxs-lookup"><span data-stu-id="3b771-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="3b771-322">手順</span><span class="sxs-lookup"><span data-stu-id="3b771-322">Instructions</span></span>

* <span data-ttu-id="3b771-323">**階層**で、 **HologramCollection**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3b771-324">**インスペクター**で [**コンポーネントの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="3b771-325">[検索] ボックスに、「"" の種類の表示**ツール**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3b771-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="3b771-326">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-326">Select the search result.</span></span>

<span data-ttu-id="3b771-327">**デプロイと活用**</span><span class="sxs-lookup"><span data-stu-id="3b771-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="3b771-328">HoloLens デバイスにビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="3b771-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="3b771-329">アプリがすべてのデバイスで実行されている場合は、エアタップを実行して、実世界のサーフェイスで航空タイルを起動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="3b771-330">他のプレーヤーのアバターと競合している場合はどうなるかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3b771-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="3b771-331">第7章-グランドくくり</span><span class="sxs-lookup"><span data-stu-id="3b771-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="3b771-332">この章では、コラボレーションによってのみ検出できるポータルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3b771-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="3b771-333">目的</span><span class="sxs-lookup"><span data-stu-id="3b771-333">Objectives</span></span>

* <span data-ttu-id="3b771-334">連携して、秘密ポータルを見つけるために十分な projectiles をアンカーで立ち上げましょう。</span><span class="sxs-lookup"><span data-stu-id="3b771-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="3b771-335">手順</span><span class="sxs-lookup"><span data-stu-id="3b771-335">Instructions</span></span>

* <span data-ttu-id="3b771-336">[**プロジェクト] パネル**で、[**ホログラム**] フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="3b771-337">**HologramCollection の子**として、**黄泉**の資産をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="3b771-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="3b771-338">**HologramCollection**を選択した状態で、**インスペクター**の [**コンポーネントの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b771-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="3b771-339">メニューで、検索ボックスに「 **ExplodeTarget**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3b771-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="3b771-340">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b771-340">Select the search result.</span></span>
* <span data-ttu-id="3b771-341">**HologramCollection**を選択した状態で、**階層**から、 **EnergyHub**オブジェクトを**インスペクター**の [**ターゲット**] フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="3b771-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="3b771-342">**HologramCollection**を選択した状態で、**階層**から、**黄泉**のオブジェクトを**インスペクター**の [**黄泉**] フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="3b771-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="3b771-343">**デプロイと活用**</span><span class="sxs-lookup"><span data-stu-id="3b771-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="3b771-344">HoloLens デバイスにビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="3b771-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="3b771-345">アプリが起動したら、共同作業を行って、EnergyHub で projectiles を起動します。</span><span class="sxs-lookup"><span data-stu-id="3b771-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="3b771-346">黄泉の場所にいる場合は、黄泉のロボットロボットで projectiles を起動します (特別に楽しいようにロボットを3回押します)。</span><span class="sxs-lookup"><span data-stu-id="3b771-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
