---
title: MR 基本 101 - デバイスでの完全なプロジェクト
description: Unity、Visual Studio および HoloLens を使用して、Windows Mixed Reality の基本を学習するこのコーディング チュートリアルに従ってください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 実際には、Windows Mixed Reality、HoloLens、混合ホログラム, academy, チュートリアル
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599361"
---
>[!NOTE]
><span data-ttu-id="dceec-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="dceec-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="dceec-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="dceec-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="dceec-106">これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="dceec-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="dceec-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="dceec-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="dceec-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="dceec-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="dceec-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="dceec-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="dceec-110">MR 基礎 101:デバイスとの完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="dceec-110">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="dceec-111">このチュートリアルでは、HoloLens などのコア Windows Mixed Reality 機能を示すには、Unity でビルドされた完全なプロジェクトを通じて[視線](gaze.md)、[ジェスチャ](gestures.md)、[音声入力](voice-input.md)、[空間サウンド](spatial-sound.md)と[空間マッピング](spatial-mapping.md)します。</span><span class="sxs-lookup"><span data-stu-id="dceec-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="dceec-112">このチュートリアルを完了するには約 1 時間になります。</span><span class="sxs-lookup"><span data-stu-id="dceec-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="dceec-113">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="dceec-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="dceec-114">コース</span><span class="sxs-lookup"><span data-stu-id="dceec-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="dceec-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="dceec-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="dceec-116"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="dceec-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="dceec-117">MR 基礎 101:デバイスとの完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="dceec-117">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="dceec-118">✔️</span><span class="sxs-lookup"><span data-stu-id="dceec-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="dceec-119">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="dceec-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="dceec-120">前提条件</span><span class="sxs-lookup"><span data-stu-id="dceec-120">Prerequisites</span></span>

* <span data-ttu-id="dceec-121">正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="dceec-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="dceec-122">HoloLens デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。</span><span class="sxs-lookup"><span data-stu-id="dceec-122">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="dceec-123">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="dceec-123">Project files</span></span>

* <span data-ttu-id="dceec-124">ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)プロジェクトに必要です。</span><span class="sxs-lookup"><span data-stu-id="dceec-124">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="dceec-125"> Unity 2017.2 またはそれ以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="dceec-125"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="dceec-126">Unity 5.6 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)します。</span><span class="sxs-lookup"><span data-stu-id="dceec-126">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="dceec-127">Unity 5.5 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)します。</span><span class="sxs-lookup"><span data-stu-id="dceec-127">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="dceec-128">Unity 5.4 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)します。</span><span class="sxs-lookup"><span data-stu-id="dceec-128">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="dceec-129">解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。</span><span class="sxs-lookup"><span data-stu-id="dceec-129">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="dceec-130">フォルダー名として保持**Origami**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-130">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="dceec-131">をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)します。</span><span class="sxs-lookup"><span data-stu-id="dceec-131">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="dceec-132">第 1 章 -"Holo"world</span><span class="sxs-lookup"><span data-stu-id="dceec-132">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="dceec-133">この章で、最初の Unity プロジェクトとビルド手順のセットアップがされプロセスを展開します。</span><span class="sxs-lookup"><span data-stu-id="dceec-133">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="dceec-134">目標</span><span class="sxs-lookup"><span data-stu-id="dceec-134">Objectives</span></span>

* <span data-ttu-id="dceec-135">Holographic 開発のために、Unity を設定します。</span><span class="sxs-lookup"><span data-stu-id="dceec-135">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="dceec-136">ホログラムを確認します。</span><span class="sxs-lookup"><span data-stu-id="dceec-136">Make a hologram.</span></span>
* <span data-ttu-id="dceec-137">行ったホログラムを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dceec-137">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="dceec-138">手順</span><span class="sxs-lookup"><span data-stu-id="dceec-138">Instructions</span></span>

* <span data-ttu-id="dceec-139">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="dceec-139">Start Unity.</span></span>
* <span data-ttu-id="dceec-140">**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dceec-140">Select **Open**.</span></span>
* <span data-ttu-id="dceec-141">として場所を入力、 **Origami**フォルダー アーカイブされた以前のことです。</span><span class="sxs-lookup"><span data-stu-id="dceec-141">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="dceec-142">選択**Origami**クリック**フォルダーの選択**。</span><span class="sxs-lookup"><span data-stu-id="dceec-142">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="dceec-143">以降、 **Origami**プロジェクトに空の既定のシーンを使用して新しいファイルに保存、シーンが含まれていません。**ファイル** / **としてシーンを保存**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-143">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="dceec-144">新しいシーンを名前**Origami**キーを押すと、**保存**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dceec-144">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="dceec-145">メインの仮想のカメラのセットアップ</span><span class="sxs-lookup"><span data-stu-id="dceec-145">Setup the main virtual camera</span></span>

* <span data-ttu-id="dceec-146">**階層パネル**、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-146">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="dceec-147">**インスペクター**にトランス フォームの位置を設定**0,0,0**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-147">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="dceec-148">検索、**フラグをクリア**プロパティ、ドロップダウン リストからの変更と**スカイ ボックス**に**純色**。</span><span class="sxs-lookup"><span data-stu-id="dceec-148">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="dceec-149">をクリックして、**バック グラウンド**フィールドをカラー ピッカーを開きます。</span><span class="sxs-lookup"><span data-stu-id="dceec-149">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="dceec-150">設定**R、G、B、および A**に**0**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-150">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="dceec-151">シーンのセットアップ</span><span class="sxs-lookup"><span data-stu-id="dceec-151">Setup the scene</span></span>

* <span data-ttu-id="dceec-152">**階層パネル**、 をクリックして**作成**と**空アイテムの作成**です。</span><span class="sxs-lookup"><span data-stu-id="dceec-152">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="dceec-153">新しい右クリックして**GameObject**名前の変更を選択します。</span><span class="sxs-lookup"><span data-stu-id="dceec-153">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="dceec-154">GameObject の名前を変更**OrigamiCollection**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-154">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="dceec-155">**ホログラム**プロジェクト パネル内のフォルダー (資産の展開しホログラムを選択します。 または [プロジェクト] パネルでホログラム フォルダーをダブルクリックします)。</span><span class="sxs-lookup"><span data-stu-id="dceec-155">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="dceec-156">ドラッグ**ステージ**の子に階層に**OrigamiCollection**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-156">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="dceec-157">ドラッグ**Sphere1**の子に階層に**OrigamiCollection**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-157">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="dceec-158">ドラッグ**Sphere2**の子に階層に**OrigamiCollection**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-158">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="dceec-159">右クリックし、**指向性光**内のオブジェクト、**階層パネル**選択と**削除**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-159">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="dceec-160">**ホログラム**フォルダー、ドラッグ**ライト**のルートに、**階層パネル**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-160">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="dceec-161">**階層**を選択、 **OrigamiCollection**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-161">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="dceec-162">**インスペクター**、変換の位置を設定**0、-0.5、2.0**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-162">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="dceec-163">キーを押して、**再生**ホログラムをプレビューする Unity でボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dceec-163">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="dceec-164">プレビュー ウィンドウの Origami オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dceec-164">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="dceec-165">キーを押して**再生**をもう一度プレビュー モードを停止します。</span><span class="sxs-lookup"><span data-stu-id="dceec-165">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="dceec-166">Visual Studio Unity からプロジェクトにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="dceec-166">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="dceec-167">Unity の select で**ファイル > Build Settings**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-167">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="dceec-168">選択**ユニバーサル Windows プラットフォーム**で、**プラットフォーム**を一覧表示し、クリックして**スイッチ プラットフォーム**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-168">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="dceec-169">設定**SDK**に**ユニバーサル 10**と**ビルドの種類**に**D3D**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-169">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="dceec-170">確認**UnityC#プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-170">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="dceec-171">をクリックして**開くシーンを追加**シーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="dceec-171">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="dceec-172">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dceec-172">Click **Build**.</span></span>
* <span data-ttu-id="dceec-173">ファイル エクスプ ローラー ウィンドウが表示されますが、作成、**新しいフォルダー** "App"という名前です。</span><span class="sxs-lookup"><span data-stu-id="dceec-173">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="dceec-174">1 回のクリック、**アプリ フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-174">Single click the **App Folder**.</span></span>
* <span data-ttu-id="dceec-175">キーを押して**フォルダーを選択します**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-175">Press **Select Folder**.</span></span>
* <span data-ttu-id="dceec-176">Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dceec-176">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="dceec-177">開く、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="dceec-177">Open the **App** folder.</span></span>
* <span data-ttu-id="dceec-178">開く (ダブルクリック) **Origami.sln**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-178">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="dceec-179">デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**X86**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-179">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="dceec-180">デバイスのボタンの横の矢印をクリックし、**リモート マシン**Wi-fi 経由で展開します。</span><span class="sxs-lookup"><span data-stu-id="dceec-180">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="dceec-181">設定、**アドレス**HoloLens の IP アドレス、名前にします。</span><span class="sxs-lookup"><span data-stu-id="dceec-181">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="dceec-182">デバイスの IP アドレスがわからない場合に参照**設定 > ネットワークとインターネット > 詳細オプション**Cortana に質問してまたは **」「コルタナさん自分の IP アドレスは何ですか?**</span><span class="sxs-lookup"><span data-stu-id="dceec-182">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="dceec-183">代わりに選択しますが、HoloLens が USB 経由で接続されている場合**デバイス**USB 経由で展開します。</span><span class="sxs-lookup"><span data-stu-id="dceec-183">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="dceec-184">ままに、**認証モード**設定**ユニバーサル**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-184">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="dceec-185">クリックして**を選択します**</span><span class="sxs-lookup"><span data-stu-id="dceec-185">Click **Select**</span></span>

* <span data-ttu-id="dceec-186">クリックして**デバッグ > デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-186">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="dceec-187">最初に、デバイスに展開するには、する必要があります[Visual Studio をペアリング](using-visual-studio.md#pairing-your-device-hololens-(1st-gen))します。</span><span class="sxs-lookup"><span data-stu-id="dceec-187">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span></span>

* <span data-ttu-id="dceec-188">折り紙プロジェクトは今すぐ、HoloLens を展開してビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="dceec-188">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="dceec-189">HoloLens にで、新しいホログラムを探します。</span><span class="sxs-lookup"><span data-stu-id="dceec-189">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="dceec-190">第 2 章 – 視線入力</span><span class="sxs-lookup"><span data-stu-id="dceec-190">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="dceec-191">この章で、最初の対話の 3 つの方法を紹介するつもりが、ホログラム--で[視線](gaze.md)します。</span><span class="sxs-lookup"><span data-stu-id="dceec-191">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="dceec-192">目標</span><span class="sxs-lookup"><span data-stu-id="dceec-192">Objectives</span></span>

* <span data-ttu-id="dceec-193">世界中ロックされているカーソルを使用して、視線の先を視覚化します。</span><span class="sxs-lookup"><span data-stu-id="dceec-193">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="dceec-194">手順</span><span class="sxs-lookup"><span data-stu-id="dceec-194">Instructions</span></span>

* <span data-ttu-id="dceec-195">Unity プロジェクトに戻るしがまだ開いている場合は、ビルドの詳細設定 ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="dceec-195">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="dceec-196">選択、**ホログラム**フォルダーで、**プロジェクト パネル**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-196">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="dceec-197">ドラッグ、**カーソル**オブジェクトを**階層パネル**ルート レベルにします。</span><span class="sxs-lookup"><span data-stu-id="dceec-197">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="dceec-198">ダブルクリックして、**カーソル**について詳しく見てを実行するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dceec-198">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="dceec-199">右クリックし、**スクリプト**プロジェクト パネル内のフォルダー。</span><span class="sxs-lookup"><span data-stu-id="dceec-199">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="dceec-200">をクリックして、**作成** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dceec-200">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="dceec-201">選択**C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-201">Select **C# Script**.</span></span>
* <span data-ttu-id="dceec-202">スクリプトの名前**WorldCursor**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-202">Name the script **WorldCursor**.</span></span> <span data-ttu-id="dceec-203">注:この名前では、大文字と小文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="dceec-203">Note: The name is case-sensitive.</span></span> <span data-ttu-id="dceec-204">.Cs 拡張子を追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dceec-204">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="dceec-205">選択、**カーソル**オブジェクト、**階層パネル**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-205">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="dceec-206">ドラッグ アンド ドロップ、 **WorldCursor**にスクリプト、**インスペクター パネル**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-206">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="dceec-207">ダブルクリックして、 **WorldCursor**スクリプトを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="dceec-207">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="dceec-208">このコードをコピーして**WorldCursor.cs**と**すべて保存**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-208">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* <span data-ttu-id="dceec-209">アプリをリビルド**ファイル > のビルド設定**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-209">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="dceec-210">以前、HoloLens を展開するために使用する Visual Studio ソリューションに戻ります。</span><span class="sxs-lookup"><span data-stu-id="dceec-210">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="dceec-211">'すべて再読み込み' が表示されたら選択します。</span><span class="sxs-lookup"><span data-stu-id="dceec-211">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="dceec-212">クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-212">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="dceec-213">ここでシーンを中心になり、カーソルがオブジェクトの形状と対話する方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="dceec-213">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="dceec-214">第 3 章 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="dceec-214">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="dceec-215">この章では、サポートを追加します[ジェスチャ](gestures.md)します。</span><span class="sxs-lookup"><span data-stu-id="dceec-215">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="dceec-216">ユーザーは、ホワイト ペーパーの球体を選択するときに、Unity の物理運動エンジンを使用して重力を有効にして分類、球体にしましょう。</span><span class="sxs-lookup"><span data-stu-id="dceec-216">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="dceec-217">目標</span><span class="sxs-lookup"><span data-stu-id="dceec-217">Objectives</span></span>

* <span data-ttu-id="dceec-218">ジェスチャに、ホログラムを制御します。</span><span class="sxs-lookup"><span data-stu-id="dceec-218">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="dceec-219">手順</span><span class="sxs-lookup"><span data-stu-id="dceec-219">Instructions</span></span>

<span data-ttu-id="dceec-220">スクリプトの作成から始めます続いて選択ジェスチャを検出することができます。</span><span class="sxs-lookup"><span data-stu-id="dceec-220">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="dceec-221">**スクリプト**フォルダー、という名前のスクリプト作成**GazeGestureManager**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-221">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="dceec-222">ドラッグ、 **GazeGestureManager**にスクリプト、 **OrigamiCollection**階層内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dceec-222">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="dceec-223">開く、 **GazeGestureManager** Visual Studio でスクリプトを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="dceec-223">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* <span data-ttu-id="dceec-224">Scripts フォルダーでは、という名前のこの時点で別のスクリプトを作成**SphereCommands**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-224">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="dceec-225">展開、 **OrigamiCollection**階層ビュー内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dceec-225">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="dceec-226">ドラッグ、 **SphereCommands**にスクリプト、 **Sphere1**階層パネル内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dceec-226">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="dceec-227">ドラッグ、 **SphereCommands**にスクリプト、 **Sphere2**階層パネル内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dceec-227">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="dceec-228">編集に関しては、Visual Studio でスクリプトを開くし、この既定のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dceec-228">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* <span data-ttu-id="dceec-229">エクスポートし、ビルド、HoloLens にアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="dceec-229">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="dceec-230">球体は一層のいずれかを確認します。</span><span class="sxs-lookup"><span data-stu-id="dceec-230">Look at one of the spheres.</span></span>
* <span data-ttu-id="dceec-231">選択ジェスチャを実行し、次の画面にドロップ球を確認します。</span><span class="sxs-lookup"><span data-stu-id="dceec-231">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="dceec-232">第 4 章 - 音声</span><span class="sxs-lookup"><span data-stu-id="dceec-232">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="dceec-233">この章では、2 つのサポートを追加します[音声コマンド](voice-input.md):"リセット world"には、元の場所にドロップされた球体を返し、「球体をドロップ」分類球を作成します。</span><span class="sxs-lookup"><span data-stu-id="dceec-233">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="dceec-234">目標</span><span class="sxs-lookup"><span data-stu-id="dceec-234">Objectives</span></span>

* <span data-ttu-id="dceec-235">バック グラウンドでは、常にリッスンする音声コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="dceec-235">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="dceec-236">音声コマンドに応答するホログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="dceec-236">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="dceec-237">手順</span><span class="sxs-lookup"><span data-stu-id="dceec-237">Instructions</span></span>

* <span data-ttu-id="dceec-238">**スクリプト**フォルダー、という名前のスクリプト作成**SpeechManager**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-238">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="dceec-239">ドラッグ、 **SpeechManager**にスクリプト、 **OrigamiCollection**階層内のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="dceec-239">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="dceec-240">開く、 **SpeechManager** Visual Studio でのスクリプト。</span><span class="sxs-lookup"><span data-stu-id="dceec-240">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="dceec-241">このコードをコピーして**SpeechManager.cs**と**すべて保存**:</span><span class="sxs-lookup"><span data-stu-id="dceec-241">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* <span data-ttu-id="dceec-242">開く、 **SphereCommands** Visual Studio でのスクリプト。</span><span class="sxs-lookup"><span data-stu-id="dceec-242">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="dceec-243">次のようにスクリプトを更新します。</span><span class="sxs-lookup"><span data-stu-id="dceec-243">Update the script to read as follows:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* <span data-ttu-id="dceec-244">エクスポートし、ビルド、HoloLens にアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="dceec-244">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="dceec-245">球体のいずれかを確認し、"**球のドロップ**"。</span><span class="sxs-lookup"><span data-stu-id="dceec-245">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="dceec-246">たとえば"**世界のリセット**"最初の位置に戻すにします。</span><span class="sxs-lookup"><span data-stu-id="dceec-246">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="dceec-247">第 5 章 - 空間のサウンド</span><span class="sxs-lookup"><span data-stu-id="dceec-247">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="dceec-248">この章で、アプリに音楽を追加し、特定のアクションでのサウンド効果をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="dceec-248">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="dceec-249">使用する[空間サウンド](spatial-sound.md)サウンド 3D 空間で特定の場所を提供します。</span><span class="sxs-lookup"><span data-stu-id="dceec-249">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="dceec-250">目標</span><span class="sxs-lookup"><span data-stu-id="dceec-250">Objectives</span></span>

* <span data-ttu-id="dceec-251">世界でホログラムお話しします。</span><span class="sxs-lookup"><span data-stu-id="dceec-251">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="dceec-252">手順</span><span class="sxs-lookup"><span data-stu-id="dceec-252">Instructions</span></span>

* <span data-ttu-id="dceec-253">上部のメニューから選択する Unity で**編集 > プロジェクトの設定 > オーディオ**</span><span class="sxs-lookup"><span data-stu-id="dceec-253">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="dceec-254">右側にある Inspector パネルで、検索、**立体音場プラグイン**設定および  **MS HRTF 立体音場**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-254">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="dceec-255">**ホログラム**プロジェクト パネルで、フォルダーをドラッグ、**アンビエンス**オブジェクト、 **OrigamiCollection**階層パネル内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dceec-255">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="dceec-256">選択**OrigamiCollection**を見つけて、**オーディオ ソース**インスペクター パネルの コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="dceec-256">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="dceec-257">これらのプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="dceec-257">Change these properties:</span></span>
  * <span data-ttu-id="dceec-258">チェック、 **Spatialize**プロパティ。</span><span class="sxs-lookup"><span data-stu-id="dceec-258">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="dceec-259">チェック、**起動状態で再生**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-259">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="dceec-260">変更**空間 Blend**に**3D**に右側のスライダーをドラッグしています。</span><span class="sxs-lookup"><span data-stu-id="dceec-260">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="dceec-261">値は、スライダーを移動するときに 0 から 1 に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dceec-261">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="dceec-262">チェック、**ループ**プロパティ。</span><span class="sxs-lookup"><span data-stu-id="dceec-262">Check the **Loop** property.</span></span>
  * <span data-ttu-id="dceec-263">展開**3D サウンド設定**、入力と**0.1**の**ドップラー レベル**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-263">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="dceec-264">設定**ボリューム ロールオフ**に**対数ロールオフ**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-264">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="dceec-265">設定**最大距離**に**20**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-265">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="dceec-266">**スクリプト**フォルダー、という名前のスクリプト作成**SphereSounds**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-266">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="dceec-267">ドラッグ アンド ドロップ**SphereSounds**を**Sphere1**と**Sphere2**階層内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dceec-267">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="dceec-268">開いている**SphereSounds** Visual Studio で、次のコードを更新および**すべて保存**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-268">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* <span data-ttu-id="dceec-269">スクリプトを保存し、Unity に戻ります。</span><span class="sxs-lookup"><span data-stu-id="dceec-269">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="dceec-270">エクスポートし、ビルド、HoloLens にアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="dceec-270">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="dceec-271">近いとステージからかけ離れていますに移動し、サウンドを変更する並列を有効にします。</span><span class="sxs-lookup"><span data-stu-id="dceec-271">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="dceec-272">第 6 章 - 空間のマッピング</span><span class="sxs-lookup"><span data-stu-id="dceec-272">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="dceec-273">ここでは、使用する[空間マッピング](spatial-mapping.md)現実の世界での実際のオブジェクトにゲーム ボードを配置します。</span><span class="sxs-lookup"><span data-stu-id="dceec-273">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="dceec-274">目標</span><span class="sxs-lookup"><span data-stu-id="dceec-274">Objectives</span></span>

* <span data-ttu-id="dceec-275">仮想世界に、現実の世界を表示します。</span><span class="sxs-lookup"><span data-stu-id="dceec-275">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="dceec-276">ここが最も重要なホログラムを配置します。</span><span class="sxs-lookup"><span data-stu-id="dceec-276">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="dceec-277">手順</span><span class="sxs-lookup"><span data-stu-id="dceec-277">Instructions</span></span>

* <span data-ttu-id="dceec-278">Unity では、クリックして、**ホログラム**プロジェクト パネル内のフォルダー。</span><span class="sxs-lookup"><span data-stu-id="dceec-278">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="dceec-279">ドラッグ、**空間マッピング**のルートに資産、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-279">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="dceec-280">をクリックして、**空間マッピング**階層内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dceec-280">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="dceec-281">**インスペクター パネル**、次のプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="dceec-281">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="dceec-282">チェック、 **Visual メッシュの描画**ボックス。</span><span class="sxs-lookup"><span data-stu-id="dceec-282">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="dceec-283">検索**描画マテリアル**右側の円をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dceec-283">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="dceec-284">型"**ワイヤー フレーム**"上部にある検索フィールドにします。</span><span class="sxs-lookup"><span data-stu-id="dceec-284">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="dceec-285">[結果] をクリックし、ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="dceec-285">Click on the result and then close the window.</span></span> <span data-ttu-id="dceec-286">これを行うときに、描画マテリアルの値は、ワイヤー フレームに設定を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dceec-286">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="dceec-287">エクスポートし、ビルド、HoloLens にアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="dceec-287">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="dceec-288">アプリを実行すると、ワイヤー フレーム メッシュは、現実の世界をオーバーレイします。</span><span class="sxs-lookup"><span data-stu-id="dceec-288">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="dceec-289">この段階では、オフと床のローリング球はフォールバックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dceec-289">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="dceec-290">現在、OrigamiCollection を新しい場所に移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dceec-290">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="dceec-291">**スクリプト**フォルダー、という名前のスクリプト作成**TapToPlaceParent**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-291">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="dceec-292">**階層**、展開、 **OrigamiCollection**を選択し、**ステージ**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dceec-292">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="dceec-293">ドラッグ、 **TapToPlaceParent**ステージ オブジェクトのスクリプト。</span><span class="sxs-lookup"><span data-stu-id="dceec-293">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="dceec-294">開く、 **TapToPlaceParent** Visual Studio でスクリプトを作成し、次に更新します。</span><span class="sxs-lookup"><span data-stu-id="dceec-294">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* <span data-ttu-id="dceec-295">ビルドをエクスポート、およびアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="dceec-295">Export, build and deploy the app.</span></span>
* <span data-ttu-id="dceec-296">今すぐに gazing、選択ジェスチャを使用して、新しい場所に移動しもう一度選択ジェスチャを使用して、特定の場所にゲームを配置できる必要がありますなります。</span><span class="sxs-lookup"><span data-stu-id="dceec-296">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="dceec-297">第 7 章 – Holographic 楽しい</span><span class="sxs-lookup"><span data-stu-id="dceec-297">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="dceec-298">目標</span><span class="sxs-lookup"><span data-stu-id="dceec-298">Objectives</span></span>

* <span data-ttu-id="dceec-299">Holographic 黄泉の入り口を明らかになります。</span><span class="sxs-lookup"><span data-stu-id="dceec-299">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="dceec-300">手順</span><span class="sxs-lookup"><span data-stu-id="dceec-300">Instructions</span></span>

<span data-ttu-id="dceec-301">これを holographic 黄泉を明らかにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dceec-301">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="dceec-302">**ホログラム**プロジェクト パネル内のフォルダー。</span><span class="sxs-lookup"><span data-stu-id="dceec-302">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="dceec-303">ドラッグ**黄泉**の子に階層に**OrigamiCollection**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-303">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="dceec-304">**スクリプト**フォルダー、という名前のスクリプト作成**HitTarget**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-304">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="dceec-305">**階層**、展開、 **OrigamiCollection**します。</span><span class="sxs-lookup"><span data-stu-id="dceec-305">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="dceec-306">展開、**ステージ**オブジェクトし、選択、**ターゲット**オブジェクト (青の展開)。</span><span class="sxs-lookup"><span data-stu-id="dceec-306">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="dceec-307">ドラッグ、 **HitTarget**にスクリプト、**ターゲット**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dceec-307">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="dceec-308">開く、 **HitTarget** Visual Studio でスクリプトを作成し、次に更新します。</span><span class="sxs-lookup"><span data-stu-id="dceec-308">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* <span data-ttu-id="dceec-309">Unity では、選択、**ターゲット**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dceec-309">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="dceec-310">2 つのパブリック プロパティに表示されます、**ヒット ターゲット**コンポーネントと、シーン内のオブジェクトを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dceec-310">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="dceec-311">ドラッグ**黄泉**から、**階層**パネル、**黄泉**プロパティを**ヒット ターゲット**コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="dceec-311">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="dceec-312">ドラッグ**ステージ**から、**階層**パネル、**オブジェクトを非表示にする**プロパティを**ヒット ターゲット**コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="dceec-312">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="dceec-313">ビルドをエクスポート、およびアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="dceec-313">Export, build and deploy the app.</span></span>
* <span data-ttu-id="dceec-314">Origami コレクションをフロアに置き、選択ジェスチャを使用してドロップ球にします。</span><span class="sxs-lookup"><span data-stu-id="dceec-314">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="dceec-315">球に達すると、ターゲット (青の展開)、展開が発生します。</span><span class="sxs-lookup"><span data-stu-id="dceec-315">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="dceec-316">コレクションを非表示にして、黄泉に穴が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dceec-316">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="dceec-317">最後です</span><span class="sxs-lookup"><span data-stu-id="dceec-317">The end</span></span>

<span data-ttu-id="dceec-318">このチュートリアルは終わりです。</span><span class="sxs-lookup"><span data-stu-id="dceec-318">And that's the end of this tutorial!</span></span>

<span data-ttu-id="dceec-319">学習内容。</span><span class="sxs-lookup"><span data-stu-id="dceec-319">You learned:</span></span>

* <span data-ttu-id="dceec-320">Unity で holographic アプリを作成する方法。</span><span class="sxs-lookup"><span data-stu-id="dceec-320">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="dceec-321">作成する方法、視線、ジェスチャ、音声、サウンドの使用と空間マッピング。</span><span class="sxs-lookup"><span data-stu-id="dceec-321">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="dceec-322">ビルドして、Visual Studio を使用してアプリをデプロイする方法。</span><span class="sxs-lookup"><span data-stu-id="dceec-322">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="dceec-323">独自のホログラフィック操作の作成を開始する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="dceec-323">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="dceec-324">関連項目</span><span class="sxs-lookup"><span data-stu-id="dceec-324">See also</span></span>

* [<span data-ttu-id="dceec-325">MR 基礎 101E:エミュレーターを使用した完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="dceec-325">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="dceec-326">視線入力</span><span class="sxs-lookup"><span data-stu-id="dceec-326">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="dceec-327">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="dceec-327">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="dceec-328">音声入力</span><span class="sxs-lookup"><span data-stu-id="dceec-328">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="dceec-329">空間のサウンド</span><span class="sxs-lookup"><span data-stu-id="dceec-329">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="dceec-330">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="dceec-330">Spatial mapping</span></span>](spatial-mapping.md)
