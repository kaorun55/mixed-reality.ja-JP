---
title: MR 基本 101-デバイスを含む完全なプロジェクト
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、Windows Mixed Reality の基本を学習してください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: mixed reality、Windows Mixed Reality、HoloLens、ホログラム、academy、チュートリアル
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524026"
---
>[!NOTE]
><span data-ttu-id="acb06-104">Mixed Reality Academy チュートリアルは、HoloLens (第1世代) と Mixed Reality イマーシブヘッドセットを念頭に置いて設計されています。</span><span class="sxs-lookup"><span data-stu-id="acb06-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="acb06-105">そのため、これらのデバイスの開発に関するガイダンスをまだ探している開発者には、これらのチュートリアルを残しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="acb06-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="acb06-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="acb06-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="acb06-107">サポートされているデバイスでの作業を続行するために管理されます。</span><span class="sxs-lookup"><span data-stu-id="acb06-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="acb06-108">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="acb06-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="acb06-109">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="acb06-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="acb06-110">MR 基本 101:デバイスを含む完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="acb06-110">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="acb06-111">このチュートリアルでは、Unity でビルドされた完全なプロジェクトについて説明します。これは、[宝石](gaze.md)、[ジェスチャ](gestures.md)、[音声入力](voice-input.md)、[空間サウンド](spatial-sound.md)、[空間マッピング](spatial-mapping.md)など、HoloLens のコア Windows Mixed Reality 機能を示しています.</span><span class="sxs-lookup"><span data-stu-id="acb06-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="acb06-112">このチュートリアルの完了には約1時間かかります。</span><span class="sxs-lookup"><span data-stu-id="acb06-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="acb06-113">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="acb06-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="acb06-114">まで</span><span class="sxs-lookup"><span data-stu-id="acb06-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="acb06-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="acb06-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="acb06-116"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="acb06-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="acb06-117">MR 基本 101:デバイスを含む完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="acb06-117">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="acb06-118">✔️</span><span class="sxs-lookup"><span data-stu-id="acb06-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="acb06-119">開始前の準備</span><span class="sxs-lookup"><span data-stu-id="acb06-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="acb06-120">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="acb06-120">Prerequisites</span></span>

* <span data-ttu-id="acb06-121">適切な[ツールがインストール](install-the-tools.md)された WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="acb06-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="acb06-122">[開発用に構成され](using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。</span><span class="sxs-lookup"><span data-stu-id="acb06-122">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="acb06-123">プロジェクトファイル</span><span class="sxs-lookup"><span data-stu-id="acb06-123">Project files</span></span>

* <span data-ttu-id="acb06-124">プロジェクトに必要な[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="acb06-124">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="acb06-125"> Unity 2017.2 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="acb06-125"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="acb06-126">引き続き Unity 5.6 のサポートが必要な場合は、[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="acb06-126">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="acb06-127">引き続き Unity 5.5 のサポートが必要な場合は、[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="acb06-127">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="acb06-128">引き続き Unity 5.4 のサポートが必要な場合は、[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="acb06-128">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="acb06-129">ファイルをデスクトップまたはその他の簡単な場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="acb06-129">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="acb06-130">フォルダー名は**Origami**のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="acb06-130">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="acb06-131">ダウンロードする前にソースコードを確認する場合は、GitHub から[入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)ます。</span><span class="sxs-lookup"><span data-stu-id="acb06-131">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="acb06-132">Chapter 1-"Holo" ワールド</span><span class="sxs-lookup"><span data-stu-id="acb06-132">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="acb06-133">この章では、最初の Unity プロジェクトをセットアップし、ビルドとデプロイのプロセスをステップ実行します。</span><span class="sxs-lookup"><span data-stu-id="acb06-133">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="acb06-134">目的</span><span class="sxs-lookup"><span data-stu-id="acb06-134">Objectives</span></span>

* <span data-ttu-id="acb06-135">Holographic 開発用に Unity を設定します。</span><span class="sxs-lookup"><span data-stu-id="acb06-135">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="acb06-136">ホログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="acb06-136">Make a hologram.</span></span>
* <span data-ttu-id="acb06-137">作成したホログラムを確認します。</span><span class="sxs-lookup"><span data-stu-id="acb06-137">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="acb06-138">手順</span><span class="sxs-lookup"><span data-stu-id="acb06-138">Instructions</span></span>

* <span data-ttu-id="acb06-139">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="acb06-139">Start Unity.</span></span>
* <span data-ttu-id="acb06-140">**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-140">Select **Open**.</span></span>
* <span data-ttu-id="acb06-141">前にアーカイブしていない**Origami**フォルダーとして場所を入力します。</span><span class="sxs-lookup"><span data-stu-id="acb06-141">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="acb06-142">**[Origami]** を選択し、 **[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acb06-142">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="acb06-143">**Origami**プロジェクトにはシーンが含まれていないため、次を使用して空の既定のシーンを新しいファイルに保存します。ファイル / **を名前を付けて保存**します。</span><span class="sxs-lookup"><span data-stu-id="acb06-143">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="acb06-144">新しいシーンに**Origami**という名前を**付け**、[保存] ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="acb06-144">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="acb06-145">メインの仮想カメラをセットアップする</span><span class="sxs-lookup"><span data-stu-id="acb06-145">Setup the main virtual camera</span></span>

* <span data-ttu-id="acb06-146">[**階層] パネル**で、 **[メインカメラ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-146">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="acb06-147">**インスペクター**で、変換位置を**0、0、0**に設定します。</span><span class="sxs-lookup"><span data-stu-id="acb06-147">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="acb06-148">" **Clear Flags** " プロパティを見つけ、ドロップ**ダウンから [** **単色**] に変更します。</span><span class="sxs-lookup"><span data-stu-id="acb06-148">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="acb06-149">**[背景]** フィールドをクリックして、カラーピッカーを開きます。</span><span class="sxs-lookup"><span data-stu-id="acb06-149">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="acb06-150">**R、G、B、およびを** **0**に設定します。</span><span class="sxs-lookup"><span data-stu-id="acb06-150">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="acb06-151">シーンを設定する</span><span class="sxs-lookup"><span data-stu-id="acb06-151">Setup the scene</span></span>

* <span data-ttu-id="acb06-152">[**階層] パネル**で、 **[作成]** をクリックし、 **[空の作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acb06-152">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="acb06-153">新しい [作成]**オブジェクト**を右クリックし、[名前の変更] を選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-153">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="acb06-154">**OrigamiCollection**オブジェクトの名前を「」に変更します。</span><span class="sxs-lookup"><span data-stu-id="acb06-154">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="acb06-155">プロジェクト パネルの **ホログラム** フォルダーから (アセット を展開して ホログラム を選択するか、プロジェクト パネルで ホログラム フォルダーをダブルクリックします)。</span><span class="sxs-lookup"><span data-stu-id="acb06-155">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="acb06-156">**ステージ**を階層にドラッグして、 **OrigamiCollection**の子にします。</span><span class="sxs-lookup"><span data-stu-id="acb06-156">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="acb06-157">**Sphere1**を階層内にドラッグして、 **OrigamiCollection**の子にします。</span><span class="sxs-lookup"><span data-stu-id="acb06-157">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="acb06-158">**Sphere2**を階層内にドラッグして、 **OrigamiCollection**の子にします。</span><span class="sxs-lookup"><span data-stu-id="acb06-158">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="acb06-159">[**階層] パネル**で**指向性ライト**オブジェクトを右クリックし、 **[削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-159">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="acb06-160">**[ホログラム]** フォルダーから、[**階層] パネル**のルートに**ライト**をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acb06-160">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="acb06-161">**階層**で、 **OrigamiCollection**を選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-161">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="acb06-162">**インスペクター**で、変換位置を**0、-0.5、2.0**に設定します。</span><span class="sxs-lookup"><span data-stu-id="acb06-162">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="acb06-163">Unity の **[再生]** ボタンをクリックして、ホログラムをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="acb06-163">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="acb06-164">プレビューウィンドウに Origami オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acb06-164">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="acb06-165">プレビューモードを停止するには、もう一度**Play**を押します。</span><span class="sxs-lookup"><span data-stu-id="acb06-165">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="acb06-166">Unity から Visual Studio にプロジェクトをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="acb06-166">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="acb06-167">Unity で、 **[ファイル > ビルド設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-167">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="acb06-168">**[プラットフォーム]** ボックスの一覧の **[ユニバーサル Windows プラットフォーム]** を選択し、 **[プラットフォームの切り替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acb06-168">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="acb06-169">**SDK**を**Universal 10**に設定し、**ビルドの種類**を**D3D**に設定します。</span><span class="sxs-lookup"><span data-stu-id="acb06-169">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="acb06-170">**Unity C#プロジェクト**を確認します。</span><span class="sxs-lookup"><span data-stu-id="acb06-170">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="acb06-171">シーンを追加するには、[開いている**シーンの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acb06-171">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="acb06-172">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acb06-172">Click **Build**.</span></span>
* <span data-ttu-id="acb06-173">表示された [エクスプローラー] ウィンドウで、"App" という名前の**新しいフォルダー**を作成します。</span><span class="sxs-lookup"><span data-stu-id="acb06-173">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="acb06-174">**アプリフォルダー**をシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="acb06-174">Single click the **App Folder**.</span></span>
* <span data-ttu-id="acb06-175">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acb06-175">Press **Select Folder**.</span></span>
* <span data-ttu-id="acb06-176">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acb06-176">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="acb06-177">**アプリ**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="acb06-177">Open the **App** folder.</span></span>
* <span data-ttu-id="acb06-178">**Origami**を開きます (ダブルクリックします)。</span><span class="sxs-lookup"><span data-stu-id="acb06-178">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="acb06-179">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから**リリース**に変更し、ARM から**X86**に変更します。</span><span class="sxs-lookup"><span data-stu-id="acb06-179">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="acb06-180">デバイス ボタンの横にある矢印をクリックし、**リモートコンピューター** を選択して wi-fi 経由で展開します。</span><span class="sxs-lookup"><span data-stu-id="acb06-180">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="acb06-181">**アドレス**を HoloLens の名前または IP アドレスに設定します。</span><span class="sxs-lookup"><span data-stu-id="acb06-181">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="acb06-182">デバイスの IP アドレスがわからない場合は、設定 の **ネットワーク & Internet > 詳細オプション >** 確認するか、cortana**に "Cortana さん、どのような IP アドレスがあるか" を**確認してください。</span><span class="sxs-lookup"><span data-stu-id="acb06-182">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="acb06-183">HoloLens が USB 経由で接続されている場合は、代わりに **[デバイス]** を選択して usb 経由で展開することができます。</span><span class="sxs-lookup"><span data-stu-id="acb06-183">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="acb06-184">**認証モード**(**ユニバーサル**) に設定したままにします。</span><span class="sxs-lookup"><span data-stu-id="acb06-184">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="acb06-185">[**選択] を**クリック</span><span class="sxs-lookup"><span data-stu-id="acb06-185">Click **Select**</span></span>

* <span data-ttu-id="acb06-186">デバッグ をクリックして **デバッグなしで開始** を >、Ctrl キーを押し**ながら F5**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="acb06-186">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="acb06-187">初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](using-visual-studio.md#pairing-your-device-hololens-(1st-gen))する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acb06-187">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span></span>

* <span data-ttu-id="acb06-188">これで、Origami プロジェクトが作成され、HoloLens にデプロイされた後、が実行されます。</span><span class="sxs-lookup"><span data-stu-id="acb06-188">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="acb06-189">HoloLens に移動し、新しいホログラムを見てみてください。</span><span class="sxs-lookup"><span data-stu-id="acb06-189">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="acb06-190">第2章-宝石</span><span class="sxs-lookup"><span data-stu-id="acb06-190">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="acb06-191">この章では、最初に3つの方法を使用して、ホログラムと対話する方法を紹介[します。](gaze.md)</span><span class="sxs-lookup"><span data-stu-id="acb06-191">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="acb06-192">目的</span><span class="sxs-lookup"><span data-stu-id="acb06-192">Objectives</span></span>

* <span data-ttu-id="acb06-193">世界でロックされているカーソルを使用して、宝石を視覚化します。</span><span class="sxs-lookup"><span data-stu-id="acb06-193">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="acb06-194">手順</span><span class="sxs-lookup"><span data-stu-id="acb06-194">Instructions</span></span>

* <span data-ttu-id="acb06-195">Unity プロジェクトに戻り、[ビルドの設定] ウィンドウがまだ開いている場合は閉じます。</span><span class="sxs-lookup"><span data-stu-id="acb06-195">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="acb06-196">[**プロジェクト] パネル**で **[ホログラム]** フォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-196">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="acb06-197">**カーソル**オブジェクトをルートレベルの [**階層] パネル**にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acb06-197">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="acb06-198">**カーソル**オブジェクトをダブルクリックすると、詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="acb06-198">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="acb06-199">[プロジェクト] パネルの **[Scripts]** フォルダーを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="acb06-199">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="acb06-200">**[作成]** サブメニューをクリックします。</span><span class="sxs-lookup"><span data-stu-id="acb06-200">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="acb06-201">**[ C#スクリプト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-201">Select **C# Script**.</span></span>
* <span data-ttu-id="acb06-202">スクリプトに**WorldCursor**という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="acb06-202">Name the script **WorldCursor**.</span></span> <span data-ttu-id="acb06-203">注:この名前では、大文字と小文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="acb06-203">Note: The name is case-sensitive.</span></span> <span data-ttu-id="acb06-204">.Cs 拡張子を追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="acb06-204">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="acb06-205">[**階層] パネル**で**カーソル**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-205">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="acb06-206">**WorldCursor**スクリプトを [**インスペクター] パネル**にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="acb06-206">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="acb06-207">**WorldCursor**スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="acb06-207">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="acb06-208">このコードをコピーして**WorldCursor.cs**に貼り付け、**すべて保存**します。</span><span class="sxs-lookup"><span data-stu-id="acb06-208">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="acb06-209">**ファイル > ビルド設定**からアプリをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="acb06-209">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="acb06-210">以前に HoloLens にデプロイするために使用した Visual Studio ソリューションに戻ります。</span><span class="sxs-lookup"><span data-stu-id="acb06-210">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="acb06-211">メッセージが表示されたら、[すべて再読み込み] を選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-211">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="acb06-212">[**デバッグ]、[デバッグなしで開始] の順にクリック >** 、Ctrl キーを押し**ながら F5**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="acb06-212">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="acb06-213">次に、シーンを見て、カーソルがオブジェクトの形状とどのように対話するかを確認します。</span><span class="sxs-lookup"><span data-stu-id="acb06-213">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="acb06-214">第3章-ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="acb06-214">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="acb06-215">この章では、[ジェスチャ](gestures.md)のサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="acb06-215">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="acb06-216">ユーザーがペーパー球を選択すると、Unity の物理エンジンを使用して重力をオンにすることで、球がフォールされるようになります。</span><span class="sxs-lookup"><span data-stu-id="acb06-216">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="acb06-217">目的</span><span class="sxs-lookup"><span data-stu-id="acb06-217">Objectives</span></span>

* <span data-ttu-id="acb06-218">選択ジェスチャでホログラムを制御します。</span><span class="sxs-lookup"><span data-stu-id="acb06-218">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="acb06-219">手順</span><span class="sxs-lookup"><span data-stu-id="acb06-219">Instructions</span></span>

<span data-ttu-id="acb06-220">まず、スクリプトを作成してから、選択したジェスチャを検出できるようにします。</span><span class="sxs-lookup"><span data-stu-id="acb06-220">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="acb06-221">**Scripts**フォルダーで、 **GazeGestureManager**という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="acb06-221">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="acb06-222">**GazeGestureManager**スクリプトを階層内の**OrigamiCollection**オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acb06-222">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="acb06-223">Visual Studio で**GazeGestureManager**スクリプトを開き、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="acb06-223">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="acb06-224">Scripts フォルダーに、今度は**SphereCommands**という名前の別のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="acb06-224">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="acb06-225">[階層] ビューで **[OrigamiCollection]** オブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="acb06-225">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="acb06-226">**SphereCommands**スクリプトを、[階層] パネルの **[Sphere1]** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acb06-226">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="acb06-227">**SphereCommands**スクリプトを、[階層] パネルの **[Sphere2]** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acb06-227">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="acb06-228">編集するために Visual Studio でスクリプトを開き、既定のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="acb06-228">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="acb06-229">アプリのエクスポート、ビルド、および HoloLens へのデプロイを行います。</span><span class="sxs-lookup"><span data-stu-id="acb06-229">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="acb06-230">いずれかの球体を確認します。</span><span class="sxs-lookup"><span data-stu-id="acb06-230">Look at one of the spheres.</span></span>
* <span data-ttu-id="acb06-231">選択ジェスチャを実行し、球が下の画面にあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="acb06-231">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="acb06-232">第4章-音声</span><span class="sxs-lookup"><span data-stu-id="acb06-232">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="acb06-233">この章では、次の2つの[音声コマンド](voice-input.md)のサポートを追加します。"ワールドのリセット" を使用して、ドロップされた球体を元の場所に返し、"球を落下する" ようにします。</span><span class="sxs-lookup"><span data-stu-id="acb06-233">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="acb06-234">目的</span><span class="sxs-lookup"><span data-stu-id="acb06-234">Objectives</span></span>

* <span data-ttu-id="acb06-235">常にバックグラウンドで待機する音声コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="acb06-235">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="acb06-236">音声コマンドに反応するホログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="acb06-236">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="acb06-237">手順</span><span class="sxs-lookup"><span data-stu-id="acb06-237">Instructions</span></span>

* <span data-ttu-id="acb06-238">**Scripts**フォルダーで、 **SpeechManager**という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="acb06-238">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="acb06-239">**SpeechManager**スクリプトを階層内の**OrigamiCollection**オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acb06-239">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="acb06-240">Visual Studio で**SpeechManager**スクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="acb06-240">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="acb06-241">このコードをコピーして**SpeechManager.cs**に貼り付け、**すべてを保存**します。</span><span class="sxs-lookup"><span data-stu-id="acb06-241">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="acb06-242">Visual Studio で**SphereCommands**スクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="acb06-242">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="acb06-243">次のようにスクリプトを更新します。</span><span class="sxs-lookup"><span data-stu-id="acb06-243">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="acb06-244">アプリのエクスポート、ビルド、および HoloLens へのデプロイを行います。</span><span class="sxs-lookup"><span data-stu-id="acb06-244">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="acb06-245">球体の1つを見て、"**ドロップ球**" と言います。</span><span class="sxs-lookup"><span data-stu-id="acb06-245">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="acb06-246">"**世界のリセット**" と言うと、最初の位置に戻ります。</span><span class="sxs-lookup"><span data-stu-id="acb06-246">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="acb06-247">第5章-空間サウンド</span><span class="sxs-lookup"><span data-stu-id="acb06-247">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="acb06-248">この章では、アプリに音楽を追加し、特定のアクションに対してサウンド効果をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="acb06-248">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="acb06-249">[空間サウンド](spatial-sound.md)を使用して、3d 空間内の特定の位置にサウンドを与えます。</span><span class="sxs-lookup"><span data-stu-id="acb06-249">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="acb06-250">目的</span><span class="sxs-lookup"><span data-stu-id="acb06-250">Objectives</span></span>

* <span data-ttu-id="acb06-251">世界中のホログラムを聞くことができます。</span><span class="sxs-lookup"><span data-stu-id="acb06-251">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="acb06-252">手順</span><span class="sxs-lookup"><span data-stu-id="acb06-252">Instructions</span></span>

* <span data-ttu-id="acb06-253">Unity で、上部のメニューから **> プロジェクトの設定** オーディオの > の編集 の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-253">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="acb06-254">右側の [インスペクター] パネルで、 **Spatializer プラグイン**の設定を見つけて、 **[MS HRTF Spatializer]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-254">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="acb06-255">プロジェクト] パネルの **[ホログラム]** フォルダーから、 **[アンビエント]** オブジェクトを [階層 パネルの**OrigamiCollection**オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acb06-255">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="acb06-256">**OrigamiCollection** を選択し、インスペクター パネルで **オーディオソース** コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="acb06-256">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="acb06-257">次のプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="acb06-257">Change these properties:</span></span>
  * <span data-ttu-id="acb06-258">**Spatialize**プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="acb06-258">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="acb06-259">スリープ状態**になって**いることを確認します。</span><span class="sxs-lookup"><span data-stu-id="acb06-259">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="acb06-260">スライダーを右にドラッグして、**空間 Blend**を**3d**に変更します。</span><span class="sxs-lookup"><span data-stu-id="acb06-260">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="acb06-261">スライダーを移動すると、値は0から1に変更されます。</span><span class="sxs-lookup"><span data-stu-id="acb06-261">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="acb06-262">**Loop**プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="acb06-262">Check the **Loop** property.</span></span>
  * <span data-ttu-id="acb06-263">**[3D サウンド設定]** を展開し、**ドップラーレベル**に「 **0.1** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="acb06-263">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="acb06-264">**ボリュームのロール**アウトを**対数ロールオフ**に設定します。</span><span class="sxs-lookup"><span data-stu-id="acb06-264">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="acb06-265">**最大距離**を**20**に設定します。</span><span class="sxs-lookup"><span data-stu-id="acb06-265">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="acb06-266">**Scripts**フォルダーで、 **SphereSounds**という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="acb06-266">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="acb06-267">**SphereSounds**を、階層内の**Sphere1**オブジェクトと**Sphere2**オブジェクトにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="acb06-267">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="acb06-268">Visual Studio で**SphereSounds**を開き、次のコードを更新して**すべてを保存**します。</span><span class="sxs-lookup"><span data-stu-id="acb06-268">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="acb06-269">スクリプトを保存し、Unity に戻ります。</span><span class="sxs-lookup"><span data-stu-id="acb06-269">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="acb06-270">アプリのエクスポート、ビルド、および HoloLens へのデプロイを行います。</span><span class="sxs-lookup"><span data-stu-id="acb06-270">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="acb06-271">ステージからさらに近い場所に移動し、サウンドが変化するのを左右に並べて表示します。</span><span class="sxs-lookup"><span data-stu-id="acb06-271">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="acb06-272">Chapter 6-空間マッピング</span><span class="sxs-lookup"><span data-stu-id="acb06-272">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="acb06-273">ここでは、[空間マッピング](spatial-mapping.md)を使用して、ゲームボードを現実世界の実際のオブジェクトに配置します。</span><span class="sxs-lookup"><span data-stu-id="acb06-273">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="acb06-274">目的</span><span class="sxs-lookup"><span data-stu-id="acb06-274">Objectives</span></span>

* <span data-ttu-id="acb06-275">実際の世界を仮想環境に移します。</span><span class="sxs-lookup"><span data-stu-id="acb06-275">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="acb06-276">自分にとって最も重要な場所にホログラムを配置します。</span><span class="sxs-lookup"><span data-stu-id="acb06-276">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="acb06-277">手順</span><span class="sxs-lookup"><span data-stu-id="acb06-277">Instructions</span></span>

* <span data-ttu-id="acb06-278">Unity で、プロジェクト パネルの **ホログラム** フォルダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="acb06-278">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="acb06-279">**空間マッピング**資産を**階層**のルートにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acb06-279">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="acb06-280">階層内の**空間マッピング**オブジェクトをクリックします。</span><span class="sxs-lookup"><span data-stu-id="acb06-280">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="acb06-281">[**インスペクター] パネル**で、次のプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="acb06-281">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="acb06-282">**[ビジュアルメッシュの描画]** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="acb06-282">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="acb06-283">**[素材の描画]** を見つけ、右側にある円をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acb06-283">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="acb06-284">上部にある検索フィールドに「**ワイヤーフレーム**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="acb06-284">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="acb06-285">結果をクリックし、ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="acb06-285">Click on the result and then close the window.</span></span> <span data-ttu-id="acb06-286">これを行うと、描画マテリアルの値はワイヤーフレームに設定されます。</span><span class="sxs-lookup"><span data-stu-id="acb06-286">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="acb06-287">アプリのエクスポート、ビルド、および HoloLens へのデプロイを行います。</span><span class="sxs-lookup"><span data-stu-id="acb06-287">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="acb06-288">アプリを実行すると、ワイヤーフレームメッシュが実際の世界にオーバーレイされます。</span><span class="sxs-lookup"><span data-stu-id="acb06-288">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="acb06-289">ローリング球がステージとフロアにどのように分かれているかを見てください。</span><span class="sxs-lookup"><span data-stu-id="acb06-289">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="acb06-290">ここでは、OrigamiCollection を新しい場所に移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="acb06-290">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="acb06-291">**Scripts**フォルダーで、 **TapToPlaceParent**という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="acb06-291">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="acb06-292">**階層**で、 **OrigamiCollection**を展開し、 **[ステージ]** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-292">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="acb06-293">**TapToPlaceParent**スクリプトを Stage オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acb06-293">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="acb06-294">Visual Studio で**TapToPlaceParent**スクリプトを開き、次のように更新します。</span><span class="sxs-lookup"><span data-stu-id="acb06-294">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="acb06-295">アプリをエクスポート、ビルド、デプロイします。</span><span class="sxs-lookup"><span data-stu-id="acb06-295">Export, build and deploy the app.</span></span>
* <span data-ttu-id="acb06-296">これで、[選択] ジェスチャを使用して新しい場所に移動し、もう一度 Select ジェスチャを使用して、ゲームを特定の場所に配置できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="acb06-296">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="acb06-297">第7章-Holographic 楽しい</span><span class="sxs-lookup"><span data-stu-id="acb06-297">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="acb06-298">目的</span><span class="sxs-lookup"><span data-stu-id="acb06-298">Objectives</span></span>

* <span data-ttu-id="acb06-299">Holographic 黄泉の入口を公開します。</span><span class="sxs-lookup"><span data-stu-id="acb06-299">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="acb06-300">手順</span><span class="sxs-lookup"><span data-stu-id="acb06-300">Instructions</span></span>

<span data-ttu-id="acb06-301">次に、holographic 黄泉を発見する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="acb06-301">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="acb06-302">プロジェクト パネルの **ホログラム** フォルダーから次のようにします。</span><span class="sxs-lookup"><span data-stu-id="acb06-302">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="acb06-303">**OrigamiCollection**の子になるように、階層に**黄泉**をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acb06-303">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="acb06-304">**Scripts**フォルダーで、**ヒットターゲット**という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="acb06-304">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="acb06-305">**階層**で、 **OrigamiCollection**を展開します。</span><span class="sxs-lookup"><span data-stu-id="acb06-305">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="acb06-306">**ステージ**オブジェクトを展開し、**ターゲット**オブジェクト (青いファン) を選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-306">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="acb06-307">**ヒットターゲット**スクリプトを**ターゲット**オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acb06-307">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="acb06-308">Visual Studio で**ヒットするターゲット**スクリプトを開き、次のように更新します。</span><span class="sxs-lookup"><span data-stu-id="acb06-308">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="acb06-309">Unity で、**ターゲット**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="acb06-309">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="acb06-310">**ヒットターゲット**コンポーネントには、2つのパブリックプロパティが表示されるようになりました。シーン内のオブジェクトを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acb06-310">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="acb06-311">**[階層]** パネルから、**ヒットターゲット**コンポーネントの "**黄泉**" プロパティに **[黄泉]** をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acb06-311">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="acb06-312">**[階層]** パネルから **[ステージ]** をオブジェクトにドラッグして、**ヒットターゲット**コンポーネントのプロパティを**非表示に**します。</span><span class="sxs-lookup"><span data-stu-id="acb06-312">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="acb06-313">アプリをエクスポート、ビルド、デプロイします。</span><span class="sxs-lookup"><span data-stu-id="acb06-313">Export, build and deploy the app.</span></span>
* <span data-ttu-id="acb06-314">Origami コレクションを床に配置し、Select ジェスチャを使用して球をドロップします。</span><span class="sxs-lookup"><span data-stu-id="acb06-314">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="acb06-315">球がターゲット (青いファン) にヒットすると、爆発が発生します。</span><span class="sxs-lookup"><span data-stu-id="acb06-315">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="acb06-316">コレクションが非表示になり、黄泉の抜け穴が表示されます。</span><span class="sxs-lookup"><span data-stu-id="acb06-316">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="acb06-317">最後です</span><span class="sxs-lookup"><span data-stu-id="acb06-317">The end</span></span>

<span data-ttu-id="acb06-318">これがこのチュートリアルの終わりです。</span><span class="sxs-lookup"><span data-stu-id="acb06-318">And that's the end of this tutorial!</span></span>

<span data-ttu-id="acb06-319">学習した内容:</span><span class="sxs-lookup"><span data-stu-id="acb06-319">You learned:</span></span>

* <span data-ttu-id="acb06-320">Unity で holographic アプリを作成する方法。</span><span class="sxs-lookup"><span data-stu-id="acb06-320">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="acb06-321">見つめ、ジェスチャ、音声、サウンド、および空間マッピングを使用する方法。</span><span class="sxs-lookup"><span data-stu-id="acb06-321">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="acb06-322">Visual Studio を使用してアプリをビルドしてデプロイする方法。</span><span class="sxs-lookup"><span data-stu-id="acb06-322">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="acb06-323">これで、独自の holographic エクスペリエンスの作成を開始する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="acb06-323">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="acb06-324">関連項目</span><span class="sxs-lookup"><span data-stu-id="acb06-324">See also</span></span>

* [<span data-ttu-id="acb06-325">MR の基本 101E:エミュレーターを使用した完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="acb06-325">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="acb06-326">視線入力</span><span class="sxs-lookup"><span data-stu-id="acb06-326">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="acb06-327">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="acb06-327">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="acb06-328">音声入力</span><span class="sxs-lookup"><span data-stu-id="acb06-328">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="acb06-329">立体音響</span><span class="sxs-lookup"><span data-stu-id="acb06-329">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="acb06-330">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="acb06-330">Spatial mapping</span></span>](spatial-mapping.md)
