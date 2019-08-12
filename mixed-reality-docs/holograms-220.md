---
title: MR 空間 220-空間サウンド
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、空間サウンドの概念の詳細を確認してください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、academy、チュートリアル、空間サウンド
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526924"
---
>[!NOTE]
><span data-ttu-id="68ec2-104">Mixed Reality Academy チュートリアルは、HoloLens (第1世代) と Mixed Reality イマーシブヘッドセットを念頭に置いて設計されています。</span><span class="sxs-lookup"><span data-stu-id="68ec2-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="68ec2-105">そのため、これらのデバイスの開発に関するガイダンスをまだ探している開発者には、これらのチュートリアルを残しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="68ec2-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="68ec2-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="68ec2-107">サポートされているデバイスでの作業を続行するために管理されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="68ec2-108">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="68ec2-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="68ec2-109">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="68ec2-110">MR 空間 220:立体音響</span><span class="sxs-lookup"><span data-stu-id="68ec2-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="68ec2-111">[空間サウンド](spatial-sound.md)はホログラムに breathes し、世界中に存在します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="68ec2-112">ホログラムは、ライトとサウンドの両方で構成されています。ホログラムが見えなくなった場合は、空間サウンドを使用して見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="68ec2-113">空間サウンドは、無線で聞くことができる一般的なサウンドとは異なり、3D 空間に配置されています。</span><span class="sxs-lookup"><span data-stu-id="68ec2-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="68ec2-114">空間サウンドを使用すると、ユーザーの背後、または自分の頭にいるかのように、ホログラムを鳴らすことができます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="68ec2-115">このコースでは、次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="68ec2-115">In this course, you will:</span></span>

* <span data-ttu-id="68ec2-116">Microsoft の空間サウンドを使用するように開発環境を構成します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="68ec2-117">相互作用を強化するには、空間サウンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="68ec2-118">空間のマッピングと共に空間サウンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="68ec2-119">サウンドのデザインとベストプラクティスの混在を理解します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="68ec2-120">音を使用して特殊効果を向上させ、ユーザーを混合現実の世界に持ち込むことができます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="68ec2-121">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="68ec2-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="68ec2-122">まで</span><span class="sxs-lookup"><span data-stu-id="68ec2-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="68ec2-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="68ec2-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="68ec2-124"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="68ec2-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="68ec2-125">MR 空間 220:立体音響</span><span class="sxs-lookup"><span data-stu-id="68ec2-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="68ec2-126">✔️</span><span class="sxs-lookup"><span data-stu-id="68ec2-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="68ec2-127">✔️</span><span class="sxs-lookup"><span data-stu-id="68ec2-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="68ec2-128">開始前の準備</span><span class="sxs-lookup"><span data-stu-id="68ec2-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="68ec2-129">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="68ec2-129">Prerequisites</span></span>

* <span data-ttu-id="68ec2-130">適切な[ツールがインストール](install-the-tools.md)された WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="68ec2-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="68ec2-131">基本的なC#プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="68ec2-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="68ec2-132">[MR の基本 101](holograms-101.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="68ec2-133">[開発用に構成され](using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。</span><span class="sxs-lookup"><span data-stu-id="68ec2-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="68ec2-134">プロジェクトファイル</span><span class="sxs-lookup"><span data-stu-id="68ec2-134">Project files</span></span>

* <span data-ttu-id="68ec2-135">プロジェクトに必要な[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="68ec2-136"> Unity 2017.2 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="68ec2-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="68ec2-137">引き続き Unity 5.6 のサポートが必要な場合は、[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="68ec2-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="68ec2-138">このリリースは最新ではなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="68ec2-139">引き続き Unity 5.5 のサポートが必要な場合は、[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="68ec2-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="68ec2-140"> このリリースは最新ではなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="68ec2-141">引き続き Unity 5.4 のサポートが必要な場合は、[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="68ec2-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="68ec2-142"> このリリースは最新ではなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="68ec2-143">ファイルをデスクトップまたはその他の簡単な場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="68ec2-144">ダウンロードする前にソースコードを確認する場合は、GitHub から[入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)ます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="68ec2-145">エラッタとメモ</span><span class="sxs-lookup"><span data-stu-id="68ec2-145">Errata and Notes</span></span>

* <span data-ttu-id="68ec2-146">コード内のブレークポイントにヒットするには、Visual Studio の ツール-> オプション-> デバッグ の下にある マイコードのみを有効にする を無効 (*オフ*) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="68ec2-147">章 1-Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="68ec2-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="68ec2-148">目的</span><span class="sxs-lookup"><span data-stu-id="68ec2-148">Objectives</span></span>

* <span data-ttu-id="68ec2-149">Microsoft の空間サウンドを使用するように Unity のサウンド構成を変更します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="68ec2-150">Unity のオブジェクトに3D サウンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="68ec2-151">手順</span><span class="sxs-lookup"><span data-stu-id="68ec2-151">Instructions</span></span>

* <span data-ttu-id="68ec2-152">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-152">Start Unity.</span></span>
* <span data-ttu-id="68ec2-153">**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-153">Select **Open**.</span></span>
* <span data-ttu-id="68ec2-154">デスクトップに移動し、以前にアーカイブしていないフォルダーを見つけます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="68ec2-155">**Starting\Decibel**フォルダーをクリックし、[フォルダーの**選択**] ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="68ec2-156">Unity にプロジェクトが読み込まれるのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="68ec2-157">[ **プロジェクト**] パネルで、[ **Scenes\Decibel.unity**] を開きます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="68ec2-158">[**階層**] パネルで、[ **HologramCollection** ] を展開し、[ **P0LY**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="68ec2-159">インスペクターで、[ **Audiosource** ] を展開し、[ **Spatialize** ] チェックボックスが表示されないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="68ec2-160">既定では、Unity は spatializer プラグインを読み込みません。</span><span class="sxs-lookup"><span data-stu-id="68ec2-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="68ec2-161">次の手順を実行すると、プロジェクトの空間サウンドが有効になります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="68ec2-162">Unity のトップメニューで、[ **Edit > Project Settings > Audio**] を開きます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="68ec2-163">**Spatializer プラグイン**のドロップダウンを見つけて、[ **MS HRTF Spatializer**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="68ec2-164">[**階層**] パネルで、[ **HologramCollection > P0LY**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="68ec2-165">[**インスペクター** ] パネルで、[**オーディオソース**] コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="68ec2-166">**Spatialize**チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="68ec2-167">[**空間 Blend** ] スライダーを**3d**にドラッグするか、編集ボックスに「 **1** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="68ec2-168">ここでは、Unity でプロジェクトをビルドし、Visual Studio でソリューションを構成します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="68ec2-169">Unity で、[**ファイル > ビルド設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="68ec2-170">シーンを追加するには、[開いている**シーンの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="68ec2-171">[**プラットフォーム**] ボックスの一覧の [**ユニバーサル Windows プラットフォーム**] を選択し、[**プラットフォームの切り替え**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="68ec2-172">HoloLens 向けに特に開発している場合は、**ターゲットデバイス**を**hololens**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="68ec2-173">それ以外の場合は、**任意のデバイス**に残しておきます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="68ec2-174">**ビルドの種類**が [ **D3D** ] に設定され、[ **sdk** ] が [**最新のインストール済み**] に設定されていることを確認します (sdk 16299 以降である必要があります)。</span><span class="sxs-lookup"><span data-stu-id="68ec2-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="68ec2-175">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-175">Click **Build**.</span></span>
7. <span data-ttu-id="68ec2-176">"App" という名前の**新しいフォルダー**を作成します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="68ec2-177">**アプリ**フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="68ec2-178">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-178">Press **Select Folder**.</span></span>

<span data-ttu-id="68ec2-179">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="68ec2-180">**アプリ**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="68ec2-181">**デシベル Visual Studio ソリューション**を開きます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="68ec2-182">HoloLens に展開する場合:</span><span class="sxs-lookup"><span data-stu-id="68ec2-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="68ec2-183">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから**リリース**に変更し、ARM から**x86**に変更します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="68ec2-184">[ローカルコンピューター] ボタンの横にあるドロップダウン矢印をクリックし、[**リモートコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="68ec2-185">**HoloLens デバイスの IP アドレス**を入力し、[認証モード] を [**ユニバーサル (暗号化**されていないプロトコル)] に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="68ec2-186">**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-186">Click **Select**.</span></span> <span data-ttu-id="68ec2-187">デバイスの IP アドレスがわからない場合は、**設定 Network & Internet > 詳細オプション >** 確認してください。</span><span class="sxs-lookup"><span data-stu-id="68ec2-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="68ec2-188">上部のメニューバーで、[デバッグ]、[**デバッグなしで開始**] の順にクリック >、Ctrl キーを押し**ながら F5**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="68ec2-189">初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](using-visual-studio.md#pairing-your-device---hololens-1st-gen)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="68ec2-190">イマーシブヘッドセットに展開する場合:</span><span class="sxs-lookup"><span data-stu-id="68ec2-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="68ec2-191">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから**リリース**に、ARM から**x64**に変更します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="68ec2-192">配置ターゲットが**ローカルコンピューター**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="68ec2-193">上部のメニューバーで、[デバッグ]、[**デバッグなしで開始**] の順にクリック >、Ctrl キーを押し**ながら F5**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="68ec2-194">第2章: 空間サウンドと相互作用</span><span class="sxs-lookup"><span data-stu-id="68ec2-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="68ec2-195">目的</span><span class="sxs-lookup"><span data-stu-id="68ec2-195">Objectives</span></span>

* <span data-ttu-id="68ec2-196">サウンドを使用して、ホログラムのリアリティを高めます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="68ec2-197">サウンドを使用して、ユーザーの宝石を誘導します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="68ec2-198">サウンドを使用してジェスチャに関するフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="68ec2-199">パート 1-リアリティの向上</span><span class="sxs-lookup"><span data-stu-id="68ec2-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="68ec2-200">主要概念</span><span class="sxs-lookup"><span data-stu-id="68ec2-200">Key Concepts</span></span>

* <span data-ttu-id="68ec2-201">Spatialize ホログラムサウンド。</span><span class="sxs-lookup"><span data-stu-id="68ec2-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="68ec2-202">サウンドソースは、ホログラムの適切な場所に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="68ec2-203">サウンドの適切な場所は、ホログラムに依存します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="68ec2-204">たとえば、ホログラムが人間の場合、サウンドソースは、脚ではなく口の近くに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="68ec2-205">手順</span><span class="sxs-lookup"><span data-stu-id="68ec2-205">Instructions</span></span>

<span data-ttu-id="68ec2-206">次の手順では、spatialized サウンドをホログラムにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="68ec2-207">[**階層**] パネルで、[ **HologramCollection** ] を展開し、[ **P0LY**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="68ec2-208">[**インスペクター** ] パネルの [ **audiosource**] で、[ **audiosource** ] の横にある円をクリックし、ポップアップから [ **PolyHover** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="68ec2-209">[**出力**] の横にある円をクリックし、ポップアップから [ **SoundEffects** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="68ec2-210">プロジェクトのデシベルは、Unity **Audiomixer**コンポーネントを使用して、サウンドグループのサウンドレベルを調整できるようにします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="68ec2-211">この方法でサウンドをグループ化することで、各サウンドの相対的なボリュームを維持しながら、全体的なボリュームを調整できます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="68ec2-212">**Audiosource**で、[ **3d サウンド設定**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="68ec2-213">**ドップラーレベル**を**0**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="68ec2-214">ドップラーレベルを0に設定すると、モーション (ホログラムまたはユーザーのいずれか) によるピッチの変更が無効になります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="68ec2-215">ドップラーの典型的な例は、高速移動車です。</span><span class="sxs-lookup"><span data-stu-id="68ec2-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="68ec2-216">車が静止リスナーに近づくにつれて、エンジンのピッチは上がります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="68ec2-217">リスナーがリスナーに渡されると、距離によってピッチが低下します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="68ec2-218">パート 2-ユーザーの宝石を誘導する</span><span class="sxs-lookup"><span data-stu-id="68ec2-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="68ec2-219">主要概念</span><span class="sxs-lookup"><span data-stu-id="68ec2-219">Key Concepts</span></span>

* <span data-ttu-id="68ec2-220">サウンドを使用して、重要なホログラムに注意してください。</span><span class="sxs-lookup"><span data-stu-id="68ec2-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="68ec2-221">耳は、目が見える場所に直接役立ちます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="68ec2-222">脳には、期待されることがあります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="68ec2-223">1つの例として、鳥は一般に人間の頭を超えています。</span><span class="sxs-lookup"><span data-stu-id="68ec2-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="68ec2-224">ユーザーが鳥のサウンドを聞くと、最初の反応が検索されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="68ec2-225">ユーザーの下に鳥を配置すると、それらのユーザーが正しい方向のサウンドを使用することになりますが、検索が必要になると予想されるホログラムを見つけることができません。</span><span class="sxs-lookup"><span data-stu-id="68ec2-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="68ec2-226">手順</span><span class="sxs-lookup"><span data-stu-id="68ec2-226">Instructions</span></span>

<span data-ttu-id="68ec2-227">次の手順を実行すると、P0LY を使用して、ホログラムを見つけることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="68ec2-228">[**階層**] パネルで、[**マネージャー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="68ec2-229">[**インスペクター** ] パネルで、[**音声入力ハンドラー**] を見つけます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="68ec2-230">**音声入力ハンドラー**で、 **[表示**しない] を展開します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="68ec2-231">**関数**を**PolyActions**に変更します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![キーワード[非表示にする]](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="68ec2-233">パート 3-ジェスチャに関するフィードバック</span><span class="sxs-lookup"><span data-stu-id="68ec2-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="68ec2-234">主要概念</span><span class="sxs-lookup"><span data-stu-id="68ec2-234">Key Concepts</span></span>

* <span data-ttu-id="68ec2-235">サウンドを使用してユーザーに正のジェスチャ確認を提供する</span><span class="sxs-lookup"><span data-stu-id="68ec2-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="68ec2-236">ユーザーに大きな音がかからないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="68ec2-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="68ec2-237">微妙なサウンドが最適であり、エクスペリエンスを過度に影にしない</span><span class="sxs-lookup"><span data-stu-id="68ec2-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="68ec2-238">手順</span><span class="sxs-lookup"><span data-stu-id="68ec2-238">Instructions</span></span>

* <span data-ttu-id="68ec2-239">[**階層**] パネルで、[ **HologramCollection**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="68ec2-240">[ **EnergyHub** ] を展開し、[ **Base**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="68ec2-241">[**インスペクター** ] パネルで、[**コンポーネントの追加**] をクリックし、[**ジェスチャサウンドハンドラー**の追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="68ec2-242">[**ジェスチャサウンドハンドラー**] で、[ナビゲーションの**開始] クリップ**と**ナビゲーション更新クリップ**の横にある円をクリックし、両方のポップアップから [ **RotateClick** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="68ec2-243">Visual Studio に読み込むには、"GestureSoundHandler" をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="68ec2-244">ジェスチャサウンドハンドラーは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="68ec2-245">**Audiosource**を作成および構成します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="68ec2-246">適切な**オブジェクト**の場所に**audiosource**を配置します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="68ec2-247">ジェスチャに関連付けられている**Audioclip**を再生します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="68ec2-248">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="68ec2-248">Build and Deploy</span></span>

1. <span data-ttu-id="68ec2-249">Unity で、[**ファイル > ビルド設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="68ec2-250">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-250">Click **Build**.</span></span>
3. <span data-ttu-id="68ec2-251">**アプリ**フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="68ec2-252">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-252">Press **Select Folder**.</span></span>

<span data-ttu-id="68ec2-253">ツールバーに "Release"、"x86"、"x64"、および "Remote Device" と表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="68ec2-254">それ以外の場合は、Visual Studio のコーディングインスタンスになります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="68ec2-255">場合によっては、アプリフォルダーからソリューションを再度開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="68ec2-256">メッセージが表示されたら、プロジェクトファイルを再度読み込みます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="68ec2-257">前と同様に、Visual Studio からデプロイします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="68ec2-258">アプリケーションが展開された後:</span><span class="sxs-lookup"><span data-stu-id="68ec2-258">After the application is deployed:</span></span>

* <span data-ttu-id="68ec2-259">P0LY の周りを移動すると、サウンドがどのように変化するかを観察します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="68ec2-260">*[非表示*にする] を指定すると、P0LY が自分の位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="68ec2-261">サウンドで検索します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-261">Find it by the sound.</span></span>
* <span data-ttu-id="68ec2-262">エネルギーハブのベースを見つめます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="68ec2-263">左または右にドラッグしてホログラムを回転させ、クリック音によってジェスチャが確認されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="68ec2-264">注:テキストパネルにはタグが付けられます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="68ec2-265">これには、このコース全体で使用できる音声コマンドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="68ec2-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="68ec2-266">第3章: 空間サウンドと空間マッピング</span><span class="sxs-lookup"><span data-stu-id="68ec2-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="68ec2-267">目的</span><span class="sxs-lookup"><span data-stu-id="68ec2-267">Objectives</span></span>

* <span data-ttu-id="68ec2-268">サウンドを使用して、ホログラムと実際の世界の間の相互作用を確認します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="68ec2-269">Occlude は、物理的な世界を使ってサウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="68ec2-270">パート 1-物理的な世界の相互作用</span><span class="sxs-lookup"><span data-stu-id="68ec2-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="68ec2-271">主要概念</span><span class="sxs-lookup"><span data-stu-id="68ec2-271">Key Concepts</span></span>

* <span data-ttu-id="68ec2-272">通常、物理オブジェクトは、サーフェイスや別のオブジェクトが検出したときに音を鳴らします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="68ec2-273">サウンドは、エクスペリエンスの中で適切なコンテキストである必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="68ec2-274">たとえば、テーブルのカップを設定すると、金属の一部で boulder を落とした場合よりも静かに聞こえます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="68ec2-275">手順</span><span class="sxs-lookup"><span data-stu-id="68ec2-275">Instructions</span></span>

* <span data-ttu-id="68ec2-276">[**階層**] パネルで、[ **HologramCollection**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="68ec2-277">[ **EnergyHub**] を展開し、[ **Base**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="68ec2-278">[**インスペクター** ] パネルで [**コンポーネントの追加**] をクリックし、[再生] を追加し**てサウンドとアクションを**設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="68ec2-279">**サウンドとアクションを使用して配置する場合**:</span><span class="sxs-lookup"><span data-stu-id="68ec2-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="68ec2-280">**タップ時に親を**確認します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="68ec2-281">配置の**サウンド**を**配置**するように設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="68ec2-282">**ピックアップ音**を**集配**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="68ec2-283">**Pickup アクション**と**配置アクション**の両方の下で、下の方の [+] を押します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="68ec2-284">シーンから EnergyHub **(オブジェクト)** フィールドに [] をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="68ec2-285">[**ピックアップアクション**] で、[ **No Function** -> **EnergyHubBase** -> **resetanimation**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="68ec2-286">[**配置アクション**] で、[ **No Function** -> **EnergyHubBase** -> **onselect**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![サウンドとアクションを使用して配置するには、タップしてください](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="68ec2-288">パート 2-サウンドオクルージョン</span><span class="sxs-lookup"><span data-stu-id="68ec2-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="68ec2-289">主要概念</span><span class="sxs-lookup"><span data-stu-id="68ec2-289">Key Concepts</span></span>

* <span data-ttu-id="68ec2-290">ライトのようなサウンドは、occluded にすることができます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="68ec2-291">従来の例としては、コンサートホールがあります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-291">A classic example is a concert hall.</span></span> <span data-ttu-id="68ec2-292">リスナーがホールの外部にあり、ドアが閉じている場合、音楽サウンドは muffled ます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="68ec2-293">また、通常はボリュームが減少しています。</span><span class="sxs-lookup"><span data-stu-id="68ec2-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="68ec2-294">ドアを開くと、実際のボリュームでサウンドの全範囲が聞こえます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="68ec2-295">高頻度のサウンドは、一般に低周波数よりも多く吸収されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="68ec2-296">手順</span><span class="sxs-lookup"><span data-stu-id="68ec2-296">Instructions</span></span>

* <span data-ttu-id="68ec2-297">[**階層**] パネルで、[ **HologramCollection** ] を展開し、[ **P0LY**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="68ec2-298">[**インスペクター** ] パネルで、[**コンポーネントの追加**] をクリックし、**オーディオエミッタ**を追加します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="68ec2-299">オーディオエミッタクラスは、次の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="68ec2-300">**Audiosource**のボリュームに対するすべての変更を復元します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="68ec2-301">**AudioEmitter**がアタッチされている、ユーザーの位置から、 **RaycastNonAlloc**を実行します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="68ec2-302">RaycastNonAlloc メソッドは、割り当てと返される結果の数を制限するために、パフォーマンスの最適化として使用されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="68ec2-303">検出された各**Iaudioinfluencer**ついて、は**applyeffect**メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="68ec2-304">以前に発生したすべての**Iaudioinfluencer**ついて、 **removeeffect**メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="68ec2-305">AudioEmitter は、フレームごとではなく、人間の時間単位で更新されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="68ec2-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="68ec2-306">この処理が行われるのは、一般に、影響をより頻繁に更新する必要があるほど高速ではないためです。</span><span class="sxs-lookup"><span data-stu-id="68ec2-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="68ec2-307">ある場所から別の場所に急速にテレポートするホログラムは、錯覚を壊す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="68ec2-308">[**階層**] パネルで、[ **HologramCollection**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="68ec2-309">**EnergyHub**を展開し、[ **bloboutside**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="68ec2-310">[**インスペクター** ] パネルで、[**コンポーネントの追加**] をクリックし、 **Audio Occluder**を追加します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="68ec2-311">**Audio Occluder**で、[**カットオフの頻度**] を**1500**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="68ec2-312">この設定により、AudioSource の周波数が 1500 Hz 以下に制限されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="68ec2-313">**ボリュームパススルー**を**0.9**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="68ec2-314">この設定により、AudioSource の音量が現在のレベルの 90% に減少します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="68ec2-315">Audio Occluder は、次のように IAudioInfluencer 有力企業を実装します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="68ec2-316">Audiosource に接続されている Audiolowpass Filter を使用して、遮蔽効果を適用します。この**フィルター**は、 **AudioEmitter**を購入します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="68ec2-317">オーディオソースにボリュームの減衰を適用します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="68ec2-318">ニュートラルカットオフ周波数を設定し、フィルターを無効にすることで、効果を無効にします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="68ec2-319">ニュートラルとして使用される頻度は 22 kHz (22000 Hz) です。</span><span class="sxs-lookup"><span data-stu-id="68ec2-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="68ec2-320">この頻度が選択されたのは、人間の耳によって聞こえる可能性のある最大周波数を超えているためです。これにより、サウンドへのはっきりの影響はありません。</span><span class="sxs-lookup"><span data-stu-id="68ec2-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="68ec2-321">[**階層**] パネルで、[ **SpatialMapping**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="68ec2-322">[**インスペクター** ] パネルで、[**コンポーネントの追加**] をクリックし、 **Audio Occluder**を追加します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="68ec2-323">**Audio Occluder**で、[**カットオフの頻度**] を**750**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="68ec2-324">ユーザーと**AudioEmitter**の間のパスに複数の occluders がある場合、最も低い頻度がフィルターに適用されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="68ec2-325">**ボリュームパススルー**を**0.75**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="68ec2-326">ユーザーと**AudioEmitter**の間のパスに複数の occluders がある場合、ボリュームパススルーが加算に適用されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="68ec2-327">[**階層**] パネルで、[**マネージャー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="68ec2-328">[**インスペクター** ] パネルで、[**音声入力ハンドラ**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="68ec2-329">**音声入力ハンドラー**で、 **[充電**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="68ec2-330">**関数**を**PolyActions**に変更します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![キーワード課金](images/gocharge.png)

* <span data-ttu-id="68ec2-332">展開**し**ます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="68ec2-333">**関数**を PolyActions に変更します。**カムバック**です。</span><span class="sxs-lookup"><span data-stu-id="68ec2-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![キーワードこちらへ来てください](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="68ec2-335">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="68ec2-335">Build and Deploy</span></span>

* <span data-ttu-id="68ec2-336">前と同様に、Unity でプロジェクトをビルドし、Visual Studio に配置します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="68ec2-337">アプリケーションが展開された後:</span><span class="sxs-lookup"><span data-stu-id="68ec2-337">After the application is deployed:</span></span>

* <span data-ttu-id="68ec2-338">*「充電」* と入力して、P0LY にエネルギーハブを入力します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="68ec2-339">サウンドの変更点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="68ec2-339">Note the change in the sound.</span></span> <span data-ttu-id="68ec2-340">Muffled と少し静かに聞こえます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="68ec2-341">自分とエネルギーハブの間に壁やその他のオブジェクトを配置できる場合は、現実の世界によって遮蔽されているため、さらに消音の音が発生します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="68ec2-342">*「ここ*に移動」と言うと、P0LY を使用してエネルギーハブを離れ、その前に配置します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="68ec2-343">P0LY がエネルギーハブを終了すると、サウンドオクルージョンが削除されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="68ec2-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="68ec2-344">引き続き P0LY が聞こえる場合は、現実世界によって occluded されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="68ec2-345">P0LY を明確に理解できるように、移動してみてください。</span><span class="sxs-lookup"><span data-stu-id="68ec2-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="68ec2-346">パート 3-部屋モデル</span><span class="sxs-lookup"><span data-stu-id="68ec2-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="68ec2-347">主要概念</span><span class="sxs-lookup"><span data-stu-id="68ec2-347">Key Concepts</span></span>

* <span data-ttu-id="68ec2-348">領域のサイズは、サウンドのローカライズに寄与する subliminal キューを提供します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="68ec2-349">Room モデルは、**Audiosource**ごとに設定されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="68ec2-350">[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)には、部屋モデルを設定するためのコードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="68ec2-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="68ec2-351">Mixed Reality エクスペリエンスの場合は、実際のワールド空間に最も適した部屋モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="68ec2-352">仮想現実のシナリオを作成する場合は、仮想環境に最も適した部屋モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="68ec2-353">第4章-サウンドのデザイン</span><span class="sxs-lookup"><span data-stu-id="68ec2-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="68ec2-354">目的</span><span class="sxs-lookup"><span data-stu-id="68ec2-354">Objectives</span></span>

* <span data-ttu-id="68ec2-355">効果的なサウンドデザインの考慮事項を理解します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="68ec2-356">さまざまな手法とガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="68ec2-357">パート 1-サウンドとエクスペリエンスの設計</span><span class="sxs-lookup"><span data-stu-id="68ec2-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="68ec2-358">このセクションでは、主要なサウンドとエクスペリエンスの設計に関する考慮事項とガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="68ec2-359">すべてのサウンドを正規化する</span><span class="sxs-lookup"><span data-stu-id="68ec2-359">Normalize all sounds</span></span>

<span data-ttu-id="68ec2-360">これにより、サウンドごとにボリュームレベルを調整する特殊なケースコードが不要になるため、サウンドファイルを簡単に更新できるようになります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="68ec2-361">ならではエクスペリエンスの設計</span><span class="sxs-lookup"><span data-stu-id="68ec2-361">Design for an untethered experience</span></span>

<span data-ttu-id="68ec2-362">HoloLens は、完全に包含されたならでは holographic コンピューターです。</span><span class="sxs-lookup"><span data-stu-id="68ec2-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="68ec2-363">ユーザーは移動中にエクスペリエンスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="68ec2-364">オーディオミックスをテストしてください。</span><span class="sxs-lookup"><span data-stu-id="68ec2-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="68ec2-365">ホログラムの論理位置からサウンドを生成します</span><span class="sxs-lookup"><span data-stu-id="68ec2-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="68ec2-366">現実の世界では、犬は尾からほえていません。人間の声は彼の足から来ていません。</span><span class="sxs-lookup"><span data-stu-id="68ec2-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="68ec2-367">ホログラムの予期しない部分からサウンドを生成しないようにします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="68ec2-368">小さいホログラムの場合は、ジオメトリの中心からサウンドを出力するのが妥当です。</span><span class="sxs-lookup"><span data-stu-id="68ec2-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="68ec2-369">使い慣れたサウンドが最もローカライズ可能</span><span class="sxs-lookup"><span data-stu-id="68ec2-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="68ec2-370">人間の声と音楽は、非常に簡単にローカライズできます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="68ec2-371">だれかがあなたの名前を呼び出すと、声が出た方向と、それまでの距離から、正確に判断できます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="68ec2-372">あまり知られていないサウンドをローカライズするのは困難です。</span><span class="sxs-lookup"><span data-stu-id="68ec2-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="68ec2-373">ユーザーの期待に cognizant</span><span class="sxs-lookup"><span data-stu-id="68ec2-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="68ec2-374">人生 experience は、サウンドの場所を特定する機能の一部を果たします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="68ec2-375">これは、人間の声が特に簡単にローカライズできる理由の1つです。</span><span class="sxs-lookup"><span data-stu-id="68ec2-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="68ec2-376">サウンドを配置する際には、ユーザーが学習した期待を把握しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="68ec2-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="68ec2-377">たとえば、他のユーザーが鳥の曲を聞いたときには、通常、鳥が見やすくなる傾向があります (飛行中またはツリー内)。</span><span class="sxs-lookup"><span data-stu-id="68ec2-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="68ec2-378">ユーザーは、サウンドの正しい方向を変えることは珍しくありませんが、間違った垂直方向では、ホログラムが見つからないときに混乱や不満を感じます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="68ec2-379">非表示の発信器を回避する</span><span class="sxs-lookup"><span data-stu-id="68ec2-379">Avoid hidden emitters</span></span>

<span data-ttu-id="68ec2-380">現実には、サウンドを聞くと、通常、サウンドを発しているオブジェクトを特定できます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="68ec2-381">また、エクスペリエンスにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="68ec2-382">ユーザーがサウンドを聞いたときに、音が聞こえ、オブジェクトを表示できないことを混乱ことがあります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="68ec2-383">このガイドラインにはいくつかの例外があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="68ec2-384">たとえば、フィールドの crickets などのアンビエントサウンドが表示されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="68ec2-385">生命経験により、これらのサウンドのソースについての知識を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="68ec2-386">パート 2-サウンドの混合</span><span class="sxs-lookup"><span data-stu-id="68ec2-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="68ec2-387">HoloLens で 70% のボリュームをターゲットにする</span><span class="sxs-lookup"><span data-stu-id="68ec2-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="68ec2-388">Mixed Reality エクスペリエンスでは、ホログラムを現実世界で見ることができます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="68ec2-389">また、現実世界のサウンドを聞くこともできます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="68ec2-390">70% のボリュームターゲットを使用すると、ユーザーは自分の体験を楽しむことができます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="68ec2-391">100% ボリュームの HoloLens は外部サウンドを drown 必要があります</span><span class="sxs-lookup"><span data-stu-id="68ec2-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="68ec2-392">ボリュームレベル 100% は、仮想現実のエクスペリエンスに似ています。</span><span class="sxs-lookup"><span data-stu-id="68ec2-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="68ec2-393">視覚的には、ユーザーは別の世界に転送されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="68ec2-394">同じものが true 音声でを保持している必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="68ec2-395">Unity AudioMixer を使用して、サウンドのカテゴリを調整する</span><span class="sxs-lookup"><span data-stu-id="68ec2-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="68ec2-396">ミックスを設計する場合、サウンドカテゴリを作成し、ボリュームを1つの単位として増減できることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="68ec2-397">これにより、各サウンドの相対レベルが維持され、全体的なミックスをすばやく簡単に変更できるようになります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="68ec2-398">一般的なカテゴリは次のとおりです。サウンド効果、アンビエント、ボイスオーバー、およびバックグラウンドミュージック。</span><span class="sxs-lookup"><span data-stu-id="68ec2-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="68ec2-399">ユーザーの宝石に基づいてサウンドをミキシングする</span><span class="sxs-lookup"><span data-stu-id="68ec2-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="68ec2-400">多くの場合、ユーザーが見ている (またはそうでない) 場所に基づいて、エクスペリエンスのサウンドミックスを変更すると便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="68ec2-401">この手法の一般的な用途の1つは、Holographic フレームの外側にあるホログラムのボリュームレベルを下げることです。これにより、ユーザーは前の情報に簡単に集中することができます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="68ec2-402">もう1つの用途は、ユーザーが重要なイベントに注意を向けるために、サウンドの音量を上げることです。</span><span class="sxs-lookup"><span data-stu-id="68ec2-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="68ec2-403">ミックスの構築</span><span class="sxs-lookup"><span data-stu-id="68ec2-403">Building your mix</span></span>

<span data-ttu-id="68ec2-404">ミックスを構築するときは、エクスペリエンスのバックグラウンドオーディオから始め、重要度に基づいてレイヤーを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="68ec2-405">多くの場合、これにより、各レイヤーは前のレイヤーよりも大きくなります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="68ec2-406">ミックスを反転したじょうごとして練りし、一番下に最も重要ではない (一般的に quietest の) サウンドを使用して、次の図のようなミックスを構築することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![サウンドミックスの構造](images/soundlevels.png)

<span data-ttu-id="68ec2-408">ボイスオーバーは興味深いシナリオです。</span><span class="sxs-lookup"><span data-stu-id="68ec2-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="68ec2-409">作成中のエクスペリエンスに基づいて、ステレオ (ローカライズされていない) サウンドを使用するか、またはボイスオーバーを spatialize することができます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="68ec2-410">Microsoft が発行した2つのエクスペリエンスは、各シナリオの優れた例を示しています。</span><span class="sxs-lookup"><span data-stu-id="68ec2-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="68ec2-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87)は、ステレオ音声を使用します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="68ec2-412">ナレーターが表示されている場所を記述する場合、サウンドは一貫しており、ユーザーの位置によって異なります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="68ec2-413">これにより、ナレーターは環境の spatialized 音から離れることなくシーンを記述できます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="68ec2-414">[フラグメント](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8)は、検出の形式で spatialized ボイスオーバーを利用します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="68ec2-415">検出の声は、実際の人間が部屋にいたかのように、ユーザーが重要な手掛かりに注意を向けるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="68ec2-416">これにより、謎を immersion ことができます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="68ec2-417">パート 3-パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="68ec2-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="68ec2-418">CPU 使用率</span><span class="sxs-lookup"><span data-stu-id="68ec2-418">CPU usage</span></span>

<span data-ttu-id="68ec2-419">空間サウンドを使用する場合、10-12 発信器は CPU の約 12% を消費します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="68ec2-420">長いオーディオファイルをストリーミングする</span><span class="sxs-lookup"><span data-stu-id="68ec2-420">Stream long audio files</span></span>

<span data-ttu-id="68ec2-421">オーディオデータは、特に一般的なサンプルレート (44.1 と 48 kHz) で大きくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="68ec2-422">一般的なルールとして、5-10 秒を超えるオーディオファイルは、アプリケーションのメモリ使用量を減らすためにストリーミングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="68ec2-423">Unity では、ファイルのインポート設定でストリーミング用にオーディオファイルをマークできます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![オーディオのインポート設定](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="68ec2-425">Chapter 5-特殊効果</span><span class="sxs-lookup"><span data-stu-id="68ec2-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="68ec2-426">目的</span><span class="sxs-lookup"><span data-stu-id="68ec2-426">Objectives</span></span>

* <span data-ttu-id="68ec2-427">"マジックウィンドウ" に奥行を追加します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="68ec2-428">ユーザーを仮想環境に移します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="68ec2-429">マジックウィンドウ</span><span class="sxs-lookup"><span data-stu-id="68ec2-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="68ec2-430">主要概念</span><span class="sxs-lookup"><span data-stu-id="68ec2-430">Key Concepts</span></span>

* <span data-ttu-id="68ec2-431">非表示の世界にビューを作成することは、視覚的に説得力のあるものです。</span><span class="sxs-lookup"><span data-stu-id="68ec2-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="68ec2-432">ホログラムやユーザーが非表示の世界に近づいたときにオーディオ効果を追加して、リアリティを高めます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="68ec2-433">手順</span><span class="sxs-lookup"><span data-stu-id="68ec2-433">Instructions</span></span>

* <span data-ttu-id="68ec2-434">[**階層**] パネルで、[ **HologramCollection** ] を展開し、[**黄泉**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="68ec2-435">[**黄泉**] を展開し、[ **VoiceSource**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="68ec2-436">[**インスペクター** ] パネルで、[**コンポーネントの追加**] をクリックし、ユーザーの**音声効果**を追加します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="68ec2-437">**Audiosource**コンポーネントが**VoiceSource**に追加されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="68ec2-438">**Audiosource**で、[**出力**] を**UserVoice (ミキサー)** に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="68ec2-439">**Spatialize**チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="68ec2-440">[**空間 Blend** ] スライダーを**3d**にドラッグするか、編集ボックスに「 **1** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="68ec2-441">**3D サウンド設定**を展開します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="68ec2-442">**ドップラーレベル**を**0**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="68ec2-443">[**ユーザーの声の効果**] で、[**親オブジェクト**] をシーンから**黄泉**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="68ec2-444">**Max Distance**を**1**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="68ec2-445">[**最大距離**の設定] を使用すると、**ユーザーの音声効果**は、ユーザーが親オブジェクトに対して、効果を有効にする前にどのように閉じる必要があるかを示します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="68ec2-446">[**ユーザーの音声効果**] で、[**コーラスパラメーター**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="68ec2-447">**深さ**を**0.1**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="68ec2-448">**タップ1ボリューム**を設定し、 **2 つのボリュームをタップ**して、 **3 つのボリューム**を**0.8**にタップします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="68ec2-449">**元のサウンドボリューム**を**0.5**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="68ec2-450">前の設定では、ユーザーの声に豊富な部分を追加するために使用される Unity **AudioChorusFilter**のパラメーターを構成しています。</span><span class="sxs-lookup"><span data-stu-id="68ec2-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="68ec2-451">[**ユーザーの音声効果**] で、[**エコーパラメーター**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="68ec2-452">**Delay**を**300**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="68ec2-453">**減衰率**を**0.2**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="68ec2-454">**元のサウンドボリューム**を**0**に設定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="68ec2-455">前の設定では、ユーザーの音声をエコーするために使用する Unity **AudioEchoFilter**のパラメーターを構成しています。</span><span class="sxs-lookup"><span data-stu-id="68ec2-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="68ec2-456">ユーザーの声効果スクリプトは、次のことを担当します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="68ec2-457">ユーザーと、スクリプトがアタッチされているユーザー**オブジェクト**との距離を測定します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="68ec2-458">ユーザーが接続**オブジェクト**を接続しているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="68ec2-459">ユーザーは、効果を有効にするために、距離に関係なく、接続オブジェクトに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="68ec2-460">**AudioChorusFilter**と**AudioEchoFilter**を**audiosource**に適用して構成します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="68ec2-461">フィルターを無効にして効果を無効にする。</span><span class="sxs-lookup"><span data-stu-id="68ec2-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="68ec2-462">ユーザーの音声効果では、 [MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)の Mic ストリームセレクターコンポーネントを使用して、高品質の音声ストリームを選択し、unity のオーディオシステムにルーティングします。</span><span class="sxs-lookup"><span data-stu-id="68ec2-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="68ec2-463">[**階層**] パネルで、[**マネージャー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="68ec2-464">[**インスペクター** ] パネルで、[**音声入力ハンドラ**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="68ec2-465">**音声入力ハンドラー**で、[**黄泉を表示する]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="68ec2-466">**関数**を**UnderworldBase**に変更します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![キーワード黄泉のショー](images/showunderworld.png)

* <span data-ttu-id="68ec2-468">[**黄泉の非表示**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="68ec2-469">**関数**を**UnderworldBase**に変更します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![キーワード黄泉の非表示](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="68ec2-471">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="68ec2-471">Build and Deploy</span></span>

* <span data-ttu-id="68ec2-472">前と同様に、Unity でプロジェクトをビルドし、Visual Studio に配置します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="68ec2-473">アプリケーションが展開された後:</span><span class="sxs-lookup"><span data-stu-id="68ec2-473">After the application is deployed:</span></span>

* <span data-ttu-id="68ec2-474">表面 (壁面、床、テーブル) に顔を置いて、"黄泉の顔を*表示する"* と言います。</span><span class="sxs-lookup"><span data-stu-id="68ec2-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="68ec2-475">黄泉のものが表示され、他のすべてのホログラムは非表示になります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="68ec2-476">黄泉の場所にいない場合は、実際の画面に接続していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="68ec2-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="68ec2-477">黄泉のホログラムの1メートル以内にアプローチし、話し始めます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="68ec2-478">音声にオーディオ効果が適用されました。</span><span class="sxs-lookup"><span data-stu-id="68ec2-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="68ec2-479">黄泉の場所から離れると、効果がどのように適用されるかがわかります。</span><span class="sxs-lookup"><span data-stu-id="68ec2-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="68ec2-480">*"黄泉の非表示" を "* 黄泉の人に隠す" と言います。</span><span class="sxs-lookup"><span data-stu-id="68ec2-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="68ec2-481">黄泉の場合は非表示になり、以前に非表示になったホログラムは再び表示されます。</span><span class="sxs-lookup"><span data-stu-id="68ec2-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="68ec2-482">最後です</span><span class="sxs-lookup"><span data-stu-id="68ec2-482">The End</span></span>

<span data-ttu-id="68ec2-483">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="68ec2-483">Congratulations!</span></span> <span data-ttu-id="68ec2-484">これで MR 空間**220 が完成しました。空間サウンド**。</span><span class="sxs-lookup"><span data-stu-id="68ec2-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="68ec2-485">世界を聞いて、ご意見をお待ちしております。</span><span class="sxs-lookup"><span data-stu-id="68ec2-485">Listen to the world and bring your experiences to life with sound!</span></span>
