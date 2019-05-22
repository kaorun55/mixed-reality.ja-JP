---
title: MR 基本 101E のエミュレーターを使用した完全なプロジェクト
description: このコーディング holographic アプリケーションの基礎を習得する Unity、Visual Studio および HoloLens のエミュレーターの使用に関するチュートリアルに従います。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、複合現実、ホログラム、academy、チュートリアル、エミュレーター
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599404"
---
>[!NOTE]
><span data-ttu-id="4b2ac-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="4b2ac-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="4b2ac-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="4b2ac-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="4b2ac-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="4b2ac-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="4b2ac-110">MR 基礎 101E:エミュレーターを使用した完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="4b2ac-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="4b2ac-111">このチュートリアルでは、HoloLens などのコア Windows Mixed Reality 機能を示すには、Unity でビルドされた完全なプロジェクトを通じて[視線](gaze.md)、[ジェスチャ](gestures.md)、[音声入力](voice-input.md)、[空間サウンド](spatial-sound.md)と[空間マッピング](spatial-mapping.md)します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="4b2ac-112">このチュートリアルを完了するには約 1 時間になります。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="4b2ac-113">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="4b2ac-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4b2ac-114">コース</span><span class="sxs-lookup"><span data-stu-id="4b2ac-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="4b2ac-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="4b2ac-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="4b2ac-116"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="4b2ac-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="4b2ac-117">MR 基礎 101E:エミュレーターを使用した完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="4b2ac-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="4b2ac-118">✔️</span><span class="sxs-lookup"><span data-stu-id="4b2ac-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="4b2ac-119">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="4b2ac-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="4b2ac-120">前提条件</span><span class="sxs-lookup"><span data-stu-id="4b2ac-120">Prerequisites</span></span>

* <span data-ttu-id="4b2ac-121">正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="4b2ac-122">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="4b2ac-122">Project files</span></span>

* <span data-ttu-id="4b2ac-123">ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)プロジェクトに必要です。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="4b2ac-124"> Unity 2017.2 またはそれ以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="4b2ac-125">Unity 5.6 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="4b2ac-126">Unity 5.5 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="4b2ac-127">Unity 5.4 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="4b2ac-128">解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="4b2ac-129">フォルダー名として保持**Origami**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="4b2ac-130">をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="4b2ac-131">第 1 章 -"Holo"world</span><span class="sxs-lookup"><span data-stu-id="4b2ac-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="4b2ac-132">この章で、最初の Unity プロジェクトとビルド手順のセットアップがされプロセスを展開します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="4b2ac-133">目標</span><span class="sxs-lookup"><span data-stu-id="4b2ac-133">Objectives</span></span>

* <span data-ttu-id="4b2ac-134">Holographic 開発のために、Unity を設定します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="4b2ac-135">ホログラムを確認します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-135">Make a hologram.</span></span>
* <span data-ttu-id="4b2ac-136">行ったホログラムを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="4b2ac-137">手順</span><span class="sxs-lookup"><span data-stu-id="4b2ac-137">Instructions</span></span>

* <span data-ttu-id="4b2ac-138">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-138">Start Unity.</span></span>
* <span data-ttu-id="4b2ac-139">**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-139">Select **Open**.</span></span>
* <span data-ttu-id="4b2ac-140">として場所を入力、 **Origami**フォルダー アーカイブされた以前のことです。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="4b2ac-141">選択**Origami**クリック**フォルダーの選択**。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="4b2ac-142">新しいシーンを保存します。**ファイル** / **としてシーンを保存**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="4b2ac-143">シーンという名前を**Origami**キーを押すと、**保存**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="4b2ac-144">メイン カメラのセットアップ</span><span class="sxs-lookup"><span data-stu-id="4b2ac-144">Setup the main camera</span></span>

* <span data-ttu-id="4b2ac-145">**階層パネル**、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="4b2ac-146">**インスペクター**にトランス フォームの位置を設定**0,0,0**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="4b2ac-147">検索、**フラグをクリア**プロパティ、ドロップダウン リストからの変更と**スカイ ボックス**に**純色**。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="4b2ac-148">をクリックして、**バック グラウンド**フィールドをカラー ピッカーを開きます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="4b2ac-149">設定**R、G、B、および A**に**0**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="4b2ac-150">シーンのセットアップ</span><span class="sxs-lookup"><span data-stu-id="4b2ac-150">Setup the scene</span></span>

* <span data-ttu-id="4b2ac-151">**階層パネル**、 をクリックして**作成**と**空アイテムの作成**です。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="4b2ac-152">新しい右クリックして**GameObject**名前の変更を選択します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="4b2ac-153">GameObject の名前を変更**OrigamiCollection**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="4b2ac-154">**ホログラム**フォルダーで、**プロジェクト パネル**:</span><span class="sxs-lookup"><span data-stu-id="4b2ac-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="4b2ac-155">ドラッグ**ステージ**の子に階層に**OrigamiCollection**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="4b2ac-156">ドラッグ**Sphere1**の子に階層に**OrigamiCollection**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="4b2ac-157">ドラッグ**Sphere2**の子に階層に**OrigamiCollection**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="4b2ac-158">右クリックし、**指向性光**内のオブジェクト、**階層パネル**選択と**削除**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="4b2ac-159">**ホログラム**フォルダー、ドラッグ**ライト**のルートに、**階層パネル**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="4b2ac-160">**階層**を選択、 **OrigamiCollection**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="4b2ac-161">**インスペクター**、変換の位置を設定**0、-0.5、2.0**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="4b2ac-162">キーを押して、**再生**ホログラムをプレビューする Unity でボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="4b2ac-163">プレビュー ウィンドウの Origami オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="4b2ac-164">キーを押して**再生**をもう一度プレビュー モードを停止します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="4b2ac-165">Visual Studio Unity からプロジェクトにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="4b2ac-166">Unity の select で**ファイル > Build Settings**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="4b2ac-167">選択**Windows ストア**で、**プラットフォーム**を一覧表示し、をクリックして**スイッチ プラットフォーム**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="4b2ac-168">設定**SDK**に**ユニバーサル 10**と**ビルドの種類**に**D3D**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="4b2ac-169">確認**UnityC#プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="4b2ac-170">をクリックして**開くシーンを追加**シーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="4b2ac-171">クリックして**プレーヤー設定しています.**.</span><span class="sxs-lookup"><span data-stu-id="4b2ac-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="4b2ac-172">Inspector パネルの選択で、 **Windows ストア ロゴ**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="4b2ac-173">選び**公開設定**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="4b2ac-174">**機能**セクションで、**マイク**と**SpatialPerception**機能します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="4b2ac-175">ビルドの詳細設定 ウィンドウに戻り**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="4b2ac-176">作成、**新しいフォルダー** "App"という名前です。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="4b2ac-177">1 回のクリック、**アプリ フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="4b2ac-178">キーを押して**フォルダーを選択します**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="4b2ac-179">Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="4b2ac-180">開く、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-180">Open the **App** folder.</span></span>
* <span data-ttu-id="4b2ac-181">開く、 **Origami Visual Studio ソリューション**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="4b2ac-182">デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**X86**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="4b2ac-183">デバイスのボタンの横の矢印をクリックし、 **HoloLens のエミュレーター**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="4b2ac-184">クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="4b2ac-185">しばらくエミュレーター折り紙プロジェクトで開始されます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="4b2ac-186">最初に起動するときに、[エミュレーター](using-the-hololens-emulator.md)エミュレーターが起動までに 15 分の時間がかかることができます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="4b2ac-187">起動した場合は閉じないでください。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="4b2ac-188">第 2 章 – 視線入力</span><span class="sxs-lookup"><span data-stu-id="4b2ac-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="4b2ac-189">この章で、最初の対話の 3 つの方法を紹介するつもりが、ホログラム--で[視線](gaze.md)します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="4b2ac-190">目標</span><span class="sxs-lookup"><span data-stu-id="4b2ac-190">Objectives</span></span>

* <span data-ttu-id="4b2ac-191">世界中ロックされているカーソルを使用して、視線の先を視覚化します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="4b2ac-192">手順</span><span class="sxs-lookup"><span data-stu-id="4b2ac-192">Instructions</span></span>

* <span data-ttu-id="4b2ac-193">Unity プロジェクトに戻るしがまだ開いている場合は、ビルドの詳細設定 ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="4b2ac-194">選択、**ホログラム**フォルダーで、**プロジェクト パネル**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="4b2ac-195">ドラッグ、**カーソル**オブジェクトを**階層パネル**ルート レベルにします。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="4b2ac-196">ダブルクリックして、**カーソル**について詳しく見てを実行するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="4b2ac-197">右クリックし、**スクリプト**プロジェクト パネル内のフォルダー。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="4b2ac-198">をクリックして、**作成** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="4b2ac-199">選択**C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-199">Select **C# Script**.</span></span>
* <span data-ttu-id="4b2ac-200">スクリプトの名前**WorldCursor**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="4b2ac-201">注:この名前では、大文字と小文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="4b2ac-202">.Cs 拡張子を追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="4b2ac-203">選択、**カーソル**オブジェクト、**階層パネル**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="4b2ac-204">ドラッグ アンド ドロップ、 **WorldCursor**にスクリプト、**インスペクター パネル**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="4b2ac-205">ダブルクリックして、 **WorldCursor**スクリプトを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="4b2ac-206">このコードをコピーして**WorldCursor.cs**と**すべて保存**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

            // Move thecursor to the point where the raycast hit.
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

* <span data-ttu-id="4b2ac-207">アプリをリビルド**ファイル > のビルド設定**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="4b2ac-208">以前はエミュレーターにデプロイするために使用する Visual Studio ソリューションに戻ります。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="4b2ac-209">'すべて再読み込み' が表示されたら選択します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="4b2ac-210">クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="4b2ac-211">Xbox コント ローラーを使用して、シーンを中心になります。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="4b2ac-212">カーソルがオブジェクトの形状と対話する方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="4b2ac-213">第 3 章 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="4b2ac-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="4b2ac-214">この章では、サポートを追加します[ジェスチャ](gestures.md)します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="4b2ac-215">ユーザーは、ホワイト ペーパーの球体を選択するときに、Unity の物理運動エンジンを使用して重力を有効にして分類、球体にしましょう。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="4b2ac-216">目標</span><span class="sxs-lookup"><span data-stu-id="4b2ac-216">Objectives</span></span>

* <span data-ttu-id="4b2ac-217">ジェスチャに、ホログラムを制御します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="4b2ac-218">手順</span><span class="sxs-lookup"><span data-stu-id="4b2ac-218">Instructions</span></span>

<span data-ttu-id="4b2ac-219">選択ジェスチャを検出できるよりもスクリプトの作成から始めます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="4b2ac-220">**スクリプト**フォルダー、という名前のスクリプト作成**GazeGestureManager**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="4b2ac-221">ドラッグ、 **GazeGestureManager**にスクリプト、 **OrigamiCollection**階層内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="4b2ac-222">開く、 **GazeGestureManager** Visual Studio でスクリプトを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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
    void Start()
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

* <span data-ttu-id="4b2ac-223">Scripts フォルダーでは、という名前のこの時点で別のスクリプトを作成**SphereCommands**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="4b2ac-224">展開、 **OrigamiCollection**階層ビュー内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="4b2ac-225">ドラッグ、 **SphereCommands**にスクリプト、 **Sphere1**階層パネル内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="4b2ac-226">ドラッグ、 **SphereCommands**にスクリプト、 **Sphere2**階層パネル内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="4b2ac-227">編集に関しては、Visual Studio でスクリプトを開くし、この既定のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="4b2ac-228">エクスポートし、ビルド、HoloLens のエミュレーターにアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="4b2ac-229">シーン、少し調べてみるし、球の 1 つの中央します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="4b2ac-230">キーを押して、 **A** Xbox コント ローラーでボタンをクリックしてまたは選択ジェスチャをシミュレートするために Space キーを押します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="4b2ac-231">第 4 章 - 音声</span><span class="sxs-lookup"><span data-stu-id="4b2ac-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="4b2ac-232">この章では、2 つのサポートを追加します[音声コマンド](voice-input.md):"リセット world"には、元の場所にドロップされた球体と"ドロップ sphere"を返します、球体を分類します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="4b2ac-233">目標</span><span class="sxs-lookup"><span data-stu-id="4b2ac-233">Objectives</span></span>

* <span data-ttu-id="4b2ac-234">バック グラウンドでは、常にリッスンする音声コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="4b2ac-235">音声コマンドに応答するホログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="4b2ac-236">手順</span><span class="sxs-lookup"><span data-stu-id="4b2ac-236">Instructions</span></span>

* <span data-ttu-id="4b2ac-237">**スクリプト**フォルダー、という名前のスクリプト作成**SpeechManager**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="4b2ac-238">ドラッグ、 **SpeechManager**にスクリプト、 **OrigamiCollection**階層内のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="4b2ac-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="4b2ac-239">開く、 **SpeechManager** Visual Studio でのスクリプト。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="4b2ac-240">このコードをコピーして**SpeechManager.cs**と**すべて保存**:</span><span class="sxs-lookup"><span data-stu-id="4b2ac-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="4b2ac-241">開く、 **SphereCommands** Visual Studio でのスクリプト。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="4b2ac-242">次のようにスクリプトを更新します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="4b2ac-243">エクスポートし、ビルド、HoloLens のエミュレーターにアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="4b2ac-244">エミュレーターを PC のマイクをサポートし、音声応答: 球体のいずれかの上にカーソルが、表示を調整し、"ドロップ Sphere"。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="4b2ac-245">たとえば"**世界のリセット**"最初の位置に戻すにします。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="4b2ac-246">第 5 章 - 空間のサウンド</span><span class="sxs-lookup"><span data-stu-id="4b2ac-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="4b2ac-247">この章で、アプリに音楽を追加し、特定のアクションでのサウンド効果をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="4b2ac-248">使用する[空間サウンド](spatial-sound.md)サウンド 3D 空間で特定の場所を提供します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="4b2ac-249">目標</span><span class="sxs-lookup"><span data-stu-id="4b2ac-249">Objectives</span></span>

* <span data-ttu-id="4b2ac-250">世界でホログラムお話しします。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="4b2ac-251">手順</span><span class="sxs-lookup"><span data-stu-id="4b2ac-251">Instructions</span></span>

* <span data-ttu-id="4b2ac-252">上部のメニューから Unity の選択で**編集 > プロジェクトの設定 > オーディオ**</span><span class="sxs-lookup"><span data-stu-id="4b2ac-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="4b2ac-253">検索、**立体音場プラグイン**設定および  **MS HRTF 立体音場**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="4b2ac-254">**ホログラム**フォルダー、ドラッグ、**アンビエンス**オブジェクト、 **OrigamiCollection**階層パネル内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="4b2ac-255">選択**OrigamiCollection**を見つけて、**オーディオ ソース**コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="4b2ac-256">これらのプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-256">Change these properties:</span></span>
  * <span data-ttu-id="4b2ac-257">チェック、 **Spatialize**プロパティ。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="4b2ac-258">チェック、**起動状態で再生**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="4b2ac-259">変更**空間 Blend**に**3D**に右側のスライダーをドラッグしています。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="4b2ac-260">チェック、**ループ**プロパティ。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="4b2ac-261">展開**3D サウンド設定**、入力と**0.1**の**ドップラー レベル**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="4b2ac-262">設定**ボリューム ロールオフ**に**対数ロールオフ**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="4b2ac-263">設定**最大距離**に**20**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="4b2ac-264">**スクリプト**フォルダー、という名前のスクリプト作成**SphereSounds**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="4b2ac-265">ドラッグ**SphereSounds**を**Sphere1**と**Sphere2**階層内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="4b2ac-266">開いている**SphereSounds** Visual Studio で、次のコードを更新および**すべて保存**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="4b2ac-267">スクリプトを保存し、Unity に戻ります。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="4b2ac-268">エクスポートし、ビルド、HoloLens のエミュレーターにアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="4b2ac-269">完全な効果を取得し、サウンドを変更するステージから離れたと緊密に移動、ヘッドホンを着用します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="4b2ac-270">第 6 章 - 空間のマッピング</span><span class="sxs-lookup"><span data-stu-id="4b2ac-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="4b2ac-271">ここでは、使用する[空間マッピング](spatial-mapping.md)現実の世界での実際のオブジェクトにゲーム ボードを配置します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="4b2ac-272">目標</span><span class="sxs-lookup"><span data-stu-id="4b2ac-272">Objectives</span></span>

* <span data-ttu-id="4b2ac-273">仮想世界に、現実の世界を表示します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="4b2ac-274">ここが最も重要なホログラムを配置します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="4b2ac-275">手順</span><span class="sxs-lookup"><span data-stu-id="4b2ac-275">Instructions</span></span>

* <span data-ttu-id="4b2ac-276">をクリックして、**ホログラム**プロジェクト パネル内のフォルダー。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="4b2ac-277">ドラッグ、**空間マッピング**のルートに資産、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="4b2ac-278">をクリックして、**空間マッピング**階層内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="4b2ac-279">**インスペクター パネル**、次のプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="4b2ac-280">チェック、 **Visual メッシュの描画**ボックス。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="4b2ac-281">検索**描画マテリアル**右側の円をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="4b2ac-282">型"**ワイヤー フレーム**"上部にある検索フィールドにします。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="4b2ac-283">[結果] をクリックし、ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="4b2ac-284">エクスポートし、ビルド、HoloLens のエミュレーターにアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="4b2ac-285">アプリの実行時に以前スキャンされた実際のリビング ルームのメッシュをワイヤー フレームでレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="4b2ac-286">この段階では、オフと床のローリング球はフォールバックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="4b2ac-287">現在、OrigamiCollection を新しい場所に移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="4b2ac-288">**スクリプト**フォルダー、という名前のスクリプト作成**TapToPlaceParent**します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="4b2ac-289">**階層**、展開、 **OrigamiCollection**を選択し、**ステージ**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="4b2ac-290">ドラッグ、 **TapToPlaceParent**ステージ オブジェクトのスクリプト。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="4b2ac-291">開く、 **TapToPlaceParent** Visual Studio でスクリプトを作成し、次に更新します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="4b2ac-292">ビルドをエクスポート、およびアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="4b2ac-293">Gazing ことによって、特定の場所にゲームを配置できるようになりましたに、ここでは選択ジェスチャを使用して (**A**または space キーを押す)、新しい場所に移動して、もう一度選択ジェスチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="4b2ac-294">最後です</span><span class="sxs-lookup"><span data-stu-id="4b2ac-294">The end</span></span>

<span data-ttu-id="4b2ac-295">このチュートリアルは終わりです。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="4b2ac-296">学習内容。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-296">You learned:</span></span>

* <span data-ttu-id="4b2ac-297">Unity で holographic アプリを作成する方法。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="4b2ac-298">作成する方法の視線、ジェスチャ、音声、サウンド、および空間マッピングを使用します。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="4b2ac-299">ビルドして、Visual Studio を使用してアプリをデプロイする方法。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="4b2ac-300">Holographic アプリの作成を開始する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="4b2ac-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="4b2ac-301">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b2ac-301">See also</span></span>

* [<span data-ttu-id="4b2ac-302">MR 基礎 101:デバイスとの完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="4b2ac-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="4b2ac-303">視線入力</span><span class="sxs-lookup"><span data-stu-id="4b2ac-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="4b2ac-304">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="4b2ac-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="4b2ac-305">音声入力</span><span class="sxs-lookup"><span data-stu-id="4b2ac-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="4b2ac-306">空間のサウンド</span><span class="sxs-lookup"><span data-stu-id="4b2ac-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="4b2ac-307">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="4b2ac-307">Spatial mapping</span></span>](spatial-mapping.md)
