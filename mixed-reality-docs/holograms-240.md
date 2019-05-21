---
title: MR 240 - 複数の HoloLens デバイスの共有
description: このコーディング ホログラムの共有の詳細については、Unity、Visual Studio および HoloLens の使用に関するチュートリアルに従います。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit、mixedrealitytoolkit unity、共有、ネットワーク、academy, チュートリアル
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601391"
---
>[!NOTE]
><span data-ttu-id="83718-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="83718-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="83718-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="83718-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="83718-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="83718-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="83718-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="83718-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="83718-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="83718-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="83718-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="83718-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="83718-110">MR 240 の共有:複数の HoloLens デバイス</span><span class="sxs-lookup"><span data-stu-id="83718-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="83718-111">ホログラムには、場所に残りの領域で移動によって、世界でのプレゼンスが与えられます。</span><span class="sxs-lookup"><span data-stu-id="83718-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="83718-112">HoloLens の場所でさまざまなを使用してホログラムを保持する[座標系](coordinate-systems.md)オブジェクトの向きと場所を追跡します。</span><span class="sxs-lookup"><span data-stu-id="83718-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="83718-113">私たちは、デバイス間でこれらの座標システムを共有する場合、共有 holographic 世界に参加できるようにする共有のエクスペリエンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="83718-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="83718-114">このチュートリアルでご紹介します。</span><span class="sxs-lookup"><span data-stu-id="83718-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="83718-115">共有のエクスペリエンスのためのネットワークをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="83718-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="83718-116">HoloLens デバイス間でホログラムを共有します。</span><span class="sxs-lookup"><span data-stu-id="83718-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="83718-117">共有の holographic 世界の他のユーザーを検出します。</span><span class="sxs-lookup"><span data-stu-id="83718-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="83718-118">-その他のプレーヤーの対象を何々 弾丸を起動できる共有の対話型エクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="83718-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="83718-119">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="83718-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="83718-120">コース</span><span class="sxs-lookup"><span data-stu-id="83718-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="83718-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="83718-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="83718-122"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="83718-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="83718-123">MR 240 の共有:複数の HoloLens デバイス</span><span class="sxs-lookup"><span data-stu-id="83718-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="83718-124">✔️</span><span class="sxs-lookup"><span data-stu-id="83718-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="83718-125">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="83718-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="83718-126">前提条件</span><span class="sxs-lookup"><span data-stu-id="83718-126">Prerequisites</span></span>

* <span data-ttu-id="83718-127">正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)インターネットにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="83718-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="83718-128">少なくとも 2 つの HoloLens デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。</span><span class="sxs-lookup"><span data-stu-id="83718-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="83718-129">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="83718-129">Project files</span></span>

* <span data-ttu-id="83718-130">ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip)プロジェクトに必要です。</span><span class="sxs-lookup"><span data-stu-id="83718-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="83718-131">Unity 2017.2 またはそれ以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="83718-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="83718-132">Unity 5.6 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)します。</span><span class="sxs-lookup"><span data-stu-id="83718-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="83718-133">Unity 5.5 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)します。</span><span class="sxs-lookup"><span data-stu-id="83718-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="83718-134">Unity 5.4 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)します。</span><span class="sxs-lookup"><span data-stu-id="83718-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="83718-135">解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。</span><span class="sxs-lookup"><span data-stu-id="83718-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="83718-136">フォルダー名として保持**SharedHolograms**します。</span><span class="sxs-lookup"><span data-stu-id="83718-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="83718-137">をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)します。</span><span class="sxs-lookup"><span data-stu-id="83718-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="83718-138">第 1 章 - Holo 世界</span><span class="sxs-lookup"><span data-stu-id="83718-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="83718-139">この章で、最初の Unity プロジェクトとビルド手順のセットアップがされプロセスを展開します。</span><span class="sxs-lookup"><span data-stu-id="83718-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="83718-140">目標</span><span class="sxs-lookup"><span data-stu-id="83718-140">Objectives</span></span>

* <span data-ttu-id="83718-141">Holographic アプリを開発する Unity をセットアップします。</span><span class="sxs-lookup"><span data-stu-id="83718-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="83718-142">ホログラムを参照してください。</span><span class="sxs-lookup"><span data-stu-id="83718-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="83718-143">手順</span><span class="sxs-lookup"><span data-stu-id="83718-143">Instructions</span></span>

* <span data-ttu-id="83718-144">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="83718-144">Start Unity.</span></span>
* <span data-ttu-id="83718-145">**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="83718-145">Select **Open**.</span></span>
* <span data-ttu-id="83718-146">として場所を入力、 **SharedHolograms**フォルダーの以前にアーカイブ解除します。</span><span class="sxs-lookup"><span data-stu-id="83718-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="83718-147">選択**プロジェクト名**クリック**フォルダーの選択**。</span><span class="sxs-lookup"><span data-stu-id="83718-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="83718-148">**階層**を右クリックし、 **Main Camera**選択**削除**します。</span><span class="sxs-lookup"><span data-stu-id="83718-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="83718-149">**HoloToolkit 共有-240/プレハブ/カメラ**フォルダー、検索、 **Main Camera** prefab します。</span><span class="sxs-lookup"><span data-stu-id="83718-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="83718-150">ドラッグ アンド ドロップ、 **Main Camera**に、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="83718-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="83718-151">**階層**、 をクリックして**作成**と**空アイテムの作成**です。</span><span class="sxs-lookup"><span data-stu-id="83718-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="83718-152">新しい右クリックして**GameObject**選択**の名前を変更**します。</span><span class="sxs-lookup"><span data-stu-id="83718-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="83718-153">GameObject の名前を変更**HologramCollection**します。</span><span class="sxs-lookup"><span data-stu-id="83718-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="83718-154">選択、 **HologramCollection**オブジェクト、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="83718-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="83718-155">**インスペクター**設定、**位置を変換**に。**X:0、Y:-0.25、Z:2**.</span><span class="sxs-lookup"><span data-stu-id="83718-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="83718-156">**ホログラム**フォルダーで、**プロジェクト パネル**、検索、 **EnergyHub**資産。</span><span class="sxs-lookup"><span data-stu-id="83718-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="83718-157">ドラッグ アンド ドロップ、 **EnergyHub**オブジェクトから、**プロジェクト パネル**を**階層**として、 **HologramCollection の子**します。</span><span class="sxs-lookup"><span data-stu-id="83718-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="83718-158">選択**ファイル > としてシーンを保存しています.**</span><span class="sxs-lookup"><span data-stu-id="83718-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="83718-159">名前をシーン**SharedHolograms**  をクリック**保存**します。</span><span class="sxs-lookup"><span data-stu-id="83718-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="83718-160">キーを押して、**再生**ホログラムをプレビューする Unity でボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="83718-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="83718-161">キーを押して**再生**をもう一度プレビュー モードを停止します。</span><span class="sxs-lookup"><span data-stu-id="83718-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="83718-162">**Visual Studio Unity からプロジェクトにエクスポートします。**</span><span class="sxs-lookup"><span data-stu-id="83718-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="83718-163">Unity の select で**ファイル > Build Settings**します。</span><span class="sxs-lookup"><span data-stu-id="83718-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="83718-164">をクリックして**開くシーンを追加**シーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="83718-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="83718-165">選択**ユニバーサル Windows プラットフォーム**で、**プラットフォーム**を一覧表示し、クリックして**スイッチ プラットフォーム**します。</span><span class="sxs-lookup"><span data-stu-id="83718-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="83718-166">設定**SDK**に**ユニバーサル 10**します。</span><span class="sxs-lookup"><span data-stu-id="83718-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="83718-167">設定**ターゲット デバイス**に**HoloLens**と**UWP ビルド タイプ**に**D3D**します。</span><span class="sxs-lookup"><span data-stu-id="83718-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="83718-168">確認**UnityC#プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="83718-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="83718-169">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83718-169">Click **Build**.</span></span>
* <span data-ttu-id="83718-170">ファイル エクスプ ローラー ウィンドウが表示されますが、作成、**新しいフォルダー** "App"という名前です。</span><span class="sxs-lookup"><span data-stu-id="83718-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="83718-171">1 回のクリック、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="83718-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="83718-172">キーを押して**フォルダーを選択します**します。</span><span class="sxs-lookup"><span data-stu-id="83718-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="83718-173">Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83718-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="83718-174">開く、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="83718-174">Open the **App** folder.</span></span>
* <span data-ttu-id="83718-175">開いている**SharedHolograms.sln** Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="83718-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="83718-176">デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**X86**します。</span><span class="sxs-lookup"><span data-stu-id="83718-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="83718-177">ローカル コンピューターの横にあるドロップダウン矢印をクリックし、**リモート デバイス**します。</span><span class="sxs-lookup"><span data-stu-id="83718-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="83718-178">設定、**アドレス**HoloLens の IP アドレス、名前にします。</span><span class="sxs-lookup"><span data-stu-id="83718-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="83718-179">デバイスの IP アドレスがわからない場合に参照**設定 > ネットワークとインターネット > 詳細オプション**Cortana に質問してまたは **」「コルタナさん自分の IP アドレスは何ですか?**</span><span class="sxs-lookup"><span data-stu-id="83718-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="83718-180">ままに、**認証モード**設定**ユニバーサル**します。</span><span class="sxs-lookup"><span data-stu-id="83718-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="83718-181">クリックして**を選択します**</span><span class="sxs-lookup"><span data-stu-id="83718-181">Click **Select**</span></span>
* <span data-ttu-id="83718-182">クリックして**デバッグ > デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="83718-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="83718-183">最初に、デバイスに展開するには、する必要があります[Visual Studio をペアリング](using-visual-studio.md#pairing-your-device-hololens)します。</span><span class="sxs-lookup"><span data-stu-id="83718-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="83718-184">EnergyHub ホログラム、HoloLens の配置を見つけてください。</span><span class="sxs-lookup"><span data-stu-id="83718-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="83718-185">第 2 章 – 相互作用</span><span class="sxs-lookup"><span data-stu-id="83718-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="83718-186">この章で、ホログラムを操作します。</span><span class="sxs-lookup"><span data-stu-id="83718-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="83718-187">最初に、視覚化するためのカーソルが追加、[視線](gaze.md)します。</span><span class="sxs-lookup"><span data-stu-id="83718-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="83718-188">次に、追加します[ジェスチャ](gestures.md)手の形を使用して、ホログラムを領域に配置するとします。</span><span class="sxs-lookup"><span data-stu-id="83718-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="83718-189">目標</span><span class="sxs-lookup"><span data-stu-id="83718-189">Objectives</span></span>

* <span data-ttu-id="83718-190">カーソルを制御する入力視線の先を使用します。</span><span class="sxs-lookup"><span data-stu-id="83718-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="83718-191">ホログラムと対話する入力ジェスチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="83718-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="83718-192">手順</span><span class="sxs-lookup"><span data-stu-id="83718-192">Instructions</span></span>

<span data-ttu-id="83718-193">**視線入力**</span><span class="sxs-lookup"><span data-stu-id="83718-193">**Gaze**</span></span>
* <span data-ttu-id="83718-194">**階層パネル**選択、 **HologramCollection**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="83718-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="83718-195">**インスペクター パネル** をクリックして、**コンポーネントの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="83718-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="83718-196">メニューで、検索ボックスに入力**視線 Manager**します。</span><span class="sxs-lookup"><span data-stu-id="83718-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="83718-197">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="83718-197">Select the search result.</span></span>
* <span data-ttu-id="83718-198">**HoloToolkit 共有 240\Prefabs\Input**フォルダー、検索、**カーソル**資産。</span><span class="sxs-lookup"><span data-stu-id="83718-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="83718-199">ドラッグ アンド ドロップ、**カーソル**上に資産、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="83718-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="83718-200">**ジェスチャ**</span><span class="sxs-lookup"><span data-stu-id="83718-200">**Gesture**</span></span>
* <span data-ttu-id="83718-201">**階層パネル**選択、 **HologramCollection**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="83718-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="83718-202">をクリックして**コンポーネントの追加**と種類**ジェスチャ マネージャー**検索フィールドにします。</span><span class="sxs-lookup"><span data-stu-id="83718-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="83718-203">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="83718-203">Select the search result.</span></span>
* <span data-ttu-id="83718-204">**階層パネル**、展開**HologramCollection**します。</span><span class="sxs-lookup"><span data-stu-id="83718-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="83718-205">子を選択**EnergyHub**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="83718-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="83718-206">**インスペクター パネル** をクリックして、**コンポーネントの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="83718-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="83718-207">メニューで、検索ボックスに入力**ホログラム配置**します。</span><span class="sxs-lookup"><span data-stu-id="83718-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="83718-208">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="83718-208">Select the search result.</span></span>
* <span data-ttu-id="83718-209">シーンを選択して保存**ファイル > Save Scene**します。</span><span class="sxs-lookup"><span data-stu-id="83718-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="83718-210">**展開し、利用**</span><span class="sxs-lookup"><span data-stu-id="83718-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="83718-211">構築し、前の章の手順を使用して、HoloLens にデプロイします。</span><span class="sxs-lookup"><span data-stu-id="83718-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="83718-212">アプリが起動して、HoloLens、頭の中を移動、EnergyHub が、視線の先を追跡する方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="83718-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="83718-213">カーソルの場合、ホログラム時にこれが表示されますおよびホログラムでない gazing とポイント ライトに変更確認します。</span><span class="sxs-lookup"><span data-stu-id="83718-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="83718-214">ホログラムを配置するエア タップを実行します。</span><span class="sxs-lookup"><span data-stu-id="83718-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="83718-215">プロジェクト内のこの時点でのみホログラムを 1 回 (もう一度お試しに再デプロイ) を配置することができます。</span><span class="sxs-lookup"><span data-stu-id="83718-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="83718-216">第 3 章 - 共有座標します。</span><span class="sxs-lookup"><span data-stu-id="83718-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="83718-217">楽しくホログラムで表示し、操作するですが、さらに見ていきましょう。</span><span class="sxs-lookup"><span data-stu-id="83718-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="83718-218">最初共有経験にまとめて確認できるホログラムを設定します。</span><span class="sxs-lookup"><span data-stu-id="83718-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="83718-219">目標</span><span class="sxs-lookup"><span data-stu-id="83718-219">Objectives</span></span>

* <span data-ttu-id="83718-220">共有のエクスペリエンスのためのネットワークをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="83718-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="83718-221">一般的な参照ポイントを確立します。</span><span class="sxs-lookup"><span data-stu-id="83718-221">Establish a common reference point.</span></span>
* <span data-ttu-id="83718-222">座標系は、デバイス間で共有します。</span><span class="sxs-lookup"><span data-stu-id="83718-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="83718-223">すべてのユーザーには、同じホログラムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83718-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="83718-224">**InternetClientServer**と**PrivateNetworkClientServer**共有サーバーに接続するアプリの機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83718-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="83718-225">これを行うことを既にホログラム 240 が独自のプロジェクトに注意してください。 保存しておきます。</span><span class="sxs-lookup"><span data-stu-id="83718-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="83718-226">Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」に移動して、player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="83718-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="83718-227">"Windows Store" タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="83718-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="83718-228">「発行の設定 > 機能」セクションでは、確認、 **InternetClientServer**機能と**PrivateNetworkClientServer**機能</span><span class="sxs-lookup"><span data-stu-id="83718-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="83718-229">手順</span><span class="sxs-lookup"><span data-stu-id="83718-229">Instructions</span></span>

* <span data-ttu-id="83718-230">**プロジェクト パネル**に移動し、 **HoloToolkit 共有 240\Prefabs\Sharing**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="83718-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="83718-231">ドラッグ アンド ドロップ、**共有**にプレハブ、**階層パネル**します。</span><span class="sxs-lookup"><span data-stu-id="83718-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="83718-232">次に、共有サービスを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83718-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="83718-233">のみ**1 台の PC**共有で発生するこの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83718-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="83718-234">Unity - の上のメニューの選択、 **HoloToolkit 共有 240 メニュー**します。</span><span class="sxs-lookup"><span data-stu-id="83718-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="83718-235">選択、**共有サービスの起動**ドロップダウン リスト内の項目。</span><span class="sxs-lookup"><span data-stu-id="83718-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="83718-236">チェック、**プライベート ネットワーク**オプションを選択し、をクリックして**アクセスを許可する**ファイアウォール プロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83718-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="83718-237">共有サービスのコンソール ウィンドウに表示される IPv4 アドレスをメモします。</span><span class="sxs-lookup"><span data-stu-id="83718-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="83718-238">これは、上、サービスが実行されているマシンと同じ ip アドレスです。</span><span class="sxs-lookup"><span data-stu-id="83718-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="83718-239">残りの手順に従って、**すべての Pc**共有エクスペリエンスに参加します。</span><span class="sxs-lookup"><span data-stu-id="83718-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="83718-240">**階層**を選択、**共有**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="83718-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="83718-241">**インスペクター**の**共有ステージ**コンポーネント、変更、**サーバー アドレス**SharingService.exe を実行しているコンピューターの IPv4 アドレスに 'localhost' から。</span><span class="sxs-lookup"><span data-stu-id="83718-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="83718-242">**階層**選択、 **HologramCollection**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="83718-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="83718-243">**インスペクター**クリックして、**コンポーネントの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="83718-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="83718-244">検索ボックスに「**インポート エクスポート アンカー マネージャー**します。</span><span class="sxs-lookup"><span data-stu-id="83718-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="83718-245">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="83718-245">Select the search result.</span></span>
* <span data-ttu-id="83718-246">**プロジェクト パネル**に移動し、**スクリプト**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="83718-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="83718-247">ダブルクリックして、 **HologramPlacement**スクリプトを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="83718-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="83718-248">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="83718-248">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="83718-249">Unity でバックアップを選択、 **HologramCollection**で、**階層パネル**します。</span><span class="sxs-lookup"><span data-stu-id="83718-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="83718-250">**インスペクター パネル** をクリックして、**コンポーネントの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="83718-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="83718-251">メニューで、検索ボックスに入力**アプリ状態マネージャー**します。</span><span class="sxs-lookup"><span data-stu-id="83718-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="83718-252">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="83718-252">Select the search result.</span></span>

<span data-ttu-id="83718-253">**展開し、利用**</span><span class="sxs-lookup"><span data-stu-id="83718-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="83718-254">HoloLens デバイス プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="83718-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="83718-255">最初に展開する 1 つの HoloLens を指定します。</span><span class="sxs-lookup"><span data-stu-id="83718-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="83718-256">アンカー、EnergyHub を配置する前に、サービスにアップロードするを待機する必要があります (かかることが最大で 30 ~ 60 秒)。</span><span class="sxs-lookup"><span data-stu-id="83718-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="83718-257">アップロードが完了するまで、タップ ジェスチャは無視されます。</span><span class="sxs-lookup"><span data-stu-id="83718-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="83718-258">EnergyHub を配置した後の場所は、サービスにアップロードして、し、他のすべての HoloLens デバイスに展開することができます。</span><span class="sxs-lookup"><span data-stu-id="83718-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="83718-259">新しい HoloLens 最初に参加させるとき、セッション、EnergyHub の場所をそのデバイスに正しいできない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="83718-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="83718-260">ただし、アンカーと EnergyHub 場所をサービスからダウンロードすると、すぐ、EnergyHub は、新しい共有の場所にジャンプする必要があります。</span><span class="sxs-lookup"><span data-stu-id="83718-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="83718-261">30 ~ 60 内でこれが発生しない場合 (秒単位) は、複数の環境の手がかりを収集するためにアンカーを設定するときの元の HoloLens がについて説明します。</span><span class="sxs-lookup"><span data-stu-id="83718-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="83718-262">場所はロックしない場合、デバイスへの再デプロイします。</span><span class="sxs-lookup"><span data-stu-id="83718-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="83718-263">デバイスがすべて準備完了と、EnergyHub を探して、アプリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="83718-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="83718-264">ホログラムの場所に同意できるすべての方向、テキストが直面しているとしますか?</span><span class="sxs-lookup"><span data-stu-id="83718-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="83718-265">第 4 章 - 検出</span><span class="sxs-lookup"><span data-stu-id="83718-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="83718-266">同じホログラムを確認できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="83718-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="83718-267">ここでそれ以外の場合、共有 holographic 世界に接続されているすべてのユーザーを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="83718-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="83718-268">この章で、ヘッドの場所と同じ共有セッションで他のすべての HoloLens デバイスの回転角度を取得します。</span><span class="sxs-lookup"><span data-stu-id="83718-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="83718-269">目標</span><span class="sxs-lookup"><span data-stu-id="83718-269">Objectives</span></span>

* <span data-ttu-id="83718-270">共有の経験には、互いを検出します。</span><span class="sxs-lookup"><span data-stu-id="83718-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="83718-271">選択して、プレーヤーのアバターを共有します。</span><span class="sxs-lookup"><span data-stu-id="83718-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="83718-272">すべてのユーザーの頭の横にある player アバターをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="83718-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="83718-273">手順</span><span class="sxs-lookup"><span data-stu-id="83718-273">Instructions</span></span>

* <span data-ttu-id="83718-274">**プロジェクト パネル**に移動し、**ホログラム**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="83718-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="83718-275">ドラッグ アンド ドロップ、 **PlayerAvatarStore**に、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="83718-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="83718-276">**プロジェクト パネル**に移動し、**スクリプト**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="83718-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="83718-277">ダブルクリックして、 **AvatarSelector**スクリプトを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="83718-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="83718-278">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="83718-278">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="83718-279">**階層**選択、 **HologramCollection**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="83718-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="83718-280">**インスペクター**クリックして**コンポーネントの追加**します。</span><span class="sxs-lookup"><span data-stu-id="83718-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="83718-281">検索ボックスに「**ローカル Player Manager**します。</span><span class="sxs-lookup"><span data-stu-id="83718-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="83718-282">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="83718-282">Select the search result.</span></span>
* <span data-ttu-id="83718-283">**階層**選択、 **HologramCollection**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="83718-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="83718-284">**インスペクター**クリックして**コンポーネントの追加**します。</span><span class="sxs-lookup"><span data-stu-id="83718-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="83718-285">検索ボックスに「**リモート Player Manager**します。</span><span class="sxs-lookup"><span data-stu-id="83718-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="83718-286">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="83718-286">Select the search result.</span></span>
* <span data-ttu-id="83718-287">開く、 **HologramPlacement** Visual Studio でのスクリプト。</span><span class="sxs-lookup"><span data-stu-id="83718-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="83718-288">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="83718-288">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="83718-289">開く、 **AppStateManager** Visual Studio でのスクリプト。</span><span class="sxs-lookup"><span data-stu-id="83718-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="83718-290">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="83718-290">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="83718-291">**展開し、利用**</span><span class="sxs-lookup"><span data-stu-id="83718-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="83718-292">ビルドし、プロジェクト、HoloLens デバイスをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="83718-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="83718-293">Ping の音が聞こえるようにする場合は、選択メニューのアバターを見つけてエア タップ ジェスチャにアバターを選択します。</span><span class="sxs-lookup"><span data-stu-id="83718-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="83718-294">サービスと通信している場合、HoloLens、ライト、カーソルの周囲のポイントが別の色に場合は、ホログラムが表示されていません: (濃い紫) の初期化中、インポート/エクスポートの場所データ (黄)、アンカー (緑) のダウンロードアンカー (青) をアップロードしています。</span><span class="sxs-lookup"><span data-stu-id="83718-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="83718-295">カーソルの周囲のライト、ポイントが既定の色 (明るい紫) の場合は、セッションで他のプレーヤーと対話できる状態には!</span><span class="sxs-lookup"><span data-stu-id="83718-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="83718-296">他のユーザーを見て、領域 - に接続されているがある holographic ロボットの肩の上に浮動小数点と、ヘッドの動きを模倣します。</span><span class="sxs-lookup"><span data-stu-id="83718-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="83718-297">第 5 章 - 配置</span><span class="sxs-lookup"><span data-stu-id="83718-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="83718-298">この章では、アンカーの実際の画面に配置することをしましょう。</span><span class="sxs-lookup"><span data-stu-id="83718-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="83718-299">共有のエクスペリエンスに接続されているすべてのユーザーの間の中間点でそのアンカーを配置するのに共有の座標を使用します。</span><span class="sxs-lookup"><span data-stu-id="83718-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="83718-300">目標</span><span class="sxs-lookup"><span data-stu-id="83718-300">Objectives</span></span>

* <span data-ttu-id="83718-301">プレーヤーのヘッドの位置に基づく空間マップ ホログラムを配置します。</span><span class="sxs-lookup"><span data-stu-id="83718-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="83718-302">手順</span><span class="sxs-lookup"><span data-stu-id="83718-302">Instructions</span></span>

* <span data-ttu-id="83718-303">**プロジェクト パネル**に移動し、**ホログラム**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="83718-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="83718-304">ドラッグ アンド ドロップ、 **CustomSpatialMapping**にプレハブ、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="83718-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="83718-305">**プロジェクト パネル**に移動し、**スクリプト**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="83718-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="83718-306">ダブルクリックして、 **AppStateManager**スクリプトを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="83718-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="83718-307">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="83718-307">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="83718-308">**プロジェクト パネル**に移動し、**スクリプト**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="83718-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="83718-309">ダブルクリックして、 **HologramPlacement**スクリプトを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="83718-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="83718-310">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="83718-310">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="83718-311">**展開し、利用**</span><span class="sxs-lookup"><span data-stu-id="83718-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="83718-312">ビルドし、プロジェクト、HoloLens デバイスをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="83718-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="83718-313">アプリの準備ができたら、円でし、EnergyHub がすべてのユーザーの中央に表示する方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="83718-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="83718-314">EnergyHub を配置する をタップします。</span><span class="sxs-lookup"><span data-stu-id="83718-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="83718-315">ホログラムを新しい場所に移動するには、音声コマンドをバックアップ、EnergyHub を選択し、グループとして連携して動作する 'ターゲットのリセット' を再試行してください。</span><span class="sxs-lookup"><span data-stu-id="83718-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="83718-316">第 6 章 - 実際の物理運動</span><span class="sxs-lookup"><span data-stu-id="83718-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="83718-317">この章では、現実世界のサーフェスから跳ね返りますホログラムを追加します。</span><span class="sxs-lookup"><span data-stu-id="83718-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="83718-318">プロジェクトを開始して、友人の両方でいっぱいに自分のスペースをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="83718-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="83718-319">目標</span><span class="sxs-lookup"><span data-stu-id="83718-319">Objectives</span></span>

* <span data-ttu-id="83718-320">実際のサーフェスから跳ね返ります弾丸を起動します。</span><span class="sxs-lookup"><span data-stu-id="83718-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="83718-321">他のプレイヤーが確認できるように、弾丸を共有します。</span><span class="sxs-lookup"><span data-stu-id="83718-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="83718-322">手順</span><span class="sxs-lookup"><span data-stu-id="83718-322">Instructions</span></span>

* <span data-ttu-id="83718-323">**階層**選択、 **HologramCollection**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="83718-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="83718-324">**インスペクター**クリックして**コンポーネントの追加**します。</span><span class="sxs-lookup"><span data-stu-id="83718-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="83718-325">検索ボックスに「**の光線ランチャー**します。</span><span class="sxs-lookup"><span data-stu-id="83718-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="83718-326">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="83718-326">Select the search result.</span></span>

<span data-ttu-id="83718-327">**展開し、利用**</span><span class="sxs-lookup"><span data-stu-id="83718-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="83718-328">ビルドして、HoloLens デバイスに展開します。</span><span class="sxs-lookup"><span data-stu-id="83718-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="83718-329">アプリは、すべてのデバイスで実行中は、現実世界のサーフェスでの光線を起動するエア タップを実行します。</span><span class="sxs-lookup"><span data-stu-id="83718-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="83718-330">別のプレーヤーのアバターの光線競合したときの動作を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83718-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="83718-331">第 7 章 – フィナーレ</span><span class="sxs-lookup"><span data-stu-id="83718-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="83718-332">この章で、共同作業でのみ検出可能なポータルが明らかにします。</span><span class="sxs-lookup"><span data-stu-id="83718-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="83718-333">目標</span><span class="sxs-lookup"><span data-stu-id="83718-333">Objectives</span></span>

* <span data-ttu-id="83718-334">シークレットのポータルを明らかにするためのアンカーに十分な弾丸を起動するには、共同作業します。</span><span class="sxs-lookup"><span data-stu-id="83718-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="83718-335">手順</span><span class="sxs-lookup"><span data-stu-id="83718-335">Instructions</span></span>

* <span data-ttu-id="83718-336">**プロジェクト パネル**に移動し、**ホログラム**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="83718-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="83718-337">ドラッグ アンド ドロップ、**黄泉**資産として、 **HologramCollection の子**します。</span><span class="sxs-lookup"><span data-stu-id="83718-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="83718-338">**HologramCollection**選択すると、をクリックして、**コンポーネントの追加**ボタン、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="83718-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="83718-339">メニューで、検索ボックスに入力**ExplodeTarget**します。</span><span class="sxs-lookup"><span data-stu-id="83718-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="83718-340">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="83718-340">Select the search result.</span></span>
* <span data-ttu-id="83718-341">**HologramCollection**から、選択した、**階層**ドラッグ、 **EnergyHub**オブジェクトを**ターゲット**フィールドに、 **インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="83718-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="83718-342">**HologramCollection**から、選択した、**階層**ドラッグ、**黄泉**オブジェクトを**黄泉**フィールド**Inspector**します。</span><span class="sxs-lookup"><span data-stu-id="83718-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="83718-343">**展開し、利用**</span><span class="sxs-lookup"><span data-stu-id="83718-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="83718-344">ビルドして、HoloLens デバイスに展開します。</span><span class="sxs-lookup"><span data-stu-id="83718-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="83718-345">アプリの起動時に、EnergyHub 弾丸を起動する共同します。</span><span class="sxs-lookup"><span data-stu-id="83718-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="83718-346">黄泉が表示されたら、弾丸黄泉ロボット (ヒット、ロボットを 3 回の楽し) でを起動します。</span><span class="sxs-lookup"><span data-stu-id="83718-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
