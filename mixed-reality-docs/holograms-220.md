---
title: MR 空間 220 - 空間のサウンド
description: サウンドの空間の概念の詳細については、Unity、Visual Studio は、HoloLens を使用してこのコーディング チュートリアルに従ってください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit unity、academy、チュートリアル、サウンドの空間
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599014"
---
>[!NOTE]
><span data-ttu-id="15c0f-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="15c0f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="15c0f-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="15c0f-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="15c0f-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="15c0f-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="15c0f-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="15c0f-110">MR 空間 220:立体音響</span><span class="sxs-lookup"><span data-stu-id="15c0f-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="15c0f-111">[空間サウンド](spatial-sound.md)ホログラムに人生を増し、世界でのプレゼンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="15c0f-112">ホログラムがのライトとサウンド の両方で構成され、ホログラムを出す場合は、空間のサウンドに役立つにあります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="15c0f-113">空間のサウンドが、一般的なサウンドはラジオのように、3 D 空間に配置されたサウンドです。</span><span class="sxs-lookup"><span data-stu-id="15c0f-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="15c0f-114">空間のサウンドを行うことができますホログラム サウンドの横にある、または頭の中であっても、背後にあるようです。</span><span class="sxs-lookup"><span data-stu-id="15c0f-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="15c0f-115">このコースでは。</span><span class="sxs-lookup"><span data-stu-id="15c0f-115">In this course, you will:</span></span>

* <span data-ttu-id="15c0f-116">Microsoft は、空間のサウンドを使用する開発環境を構成します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="15c0f-117">相互作用を強化するために、サウンドの空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="15c0f-118">空間マッピングと共に空間のサウンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="15c0f-119">サウンドのデザインやベスト プラクティスを理解します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="15c0f-120">特殊効果を強化し、複合現実の世界にユーザーを表示するには、サウンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="15c0f-121">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="15c0f-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="15c0f-122">コース</span><span class="sxs-lookup"><span data-stu-id="15c0f-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="15c0f-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="15c0f-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="15c0f-124"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="15c0f-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="15c0f-125">MR 空間 220:立体音響</span><span class="sxs-lookup"><span data-stu-id="15c0f-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="15c0f-126">✔️</span><span class="sxs-lookup"><span data-stu-id="15c0f-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="15c0f-127">✔️</span><span class="sxs-lookup"><span data-stu-id="15c0f-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="15c0f-128">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="15c0f-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="15c0f-129">前提条件</span><span class="sxs-lookup"><span data-stu-id="15c0f-129">Prerequisites</span></span>

* <span data-ttu-id="15c0f-130">正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="15c0f-131">基本的なC#プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="15c0f-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="15c0f-132">完了する必要があります[MR 基本 101](holograms-101.md)します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="15c0f-133">HoloLens デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="15c0f-134">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="15c0f-134">Project files</span></span>

* <span data-ttu-id="15c0f-135">ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip)プロジェクトに必要です。</span><span class="sxs-lookup"><span data-stu-id="15c0f-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="15c0f-136"> Unity 2017.2 またはそれ以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="15c0f-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="15c0f-137">Unity 5.6 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="15c0f-138">このリリースは、最新の状態できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="15c0f-139">Unity 5.5 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="15c0f-140"> このリリースは、最新の状態できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="15c0f-141">Unity 5.4 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="15c0f-142"> このリリースは、最新の状態できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="15c0f-143">解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。</span><span class="sxs-lookup"><span data-stu-id="15c0f-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="15c0f-144">をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="15c0f-145">正誤表と注意事項</span><span class="sxs-lookup"><span data-stu-id="15c0f-145">Errata and Notes</span></span>

* <span data-ttu-id="15c0f-146">「マイ コードのみを有効にする」無効にする必要があります (*unchecked*) -> ツールの Visual Studio でのオプションには、デバッグ、コードにブレークポイントをヒットするには-> です。</span><span class="sxs-lookup"><span data-stu-id="15c0f-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="15c0f-147">第 1 章 - Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="15c0f-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="15c0f-148">目標</span><span class="sxs-lookup"><span data-stu-id="15c0f-148">Objectives</span></span>

* <span data-ttu-id="15c0f-149">Microsoft は、空間音を使って Unity のサウンドの構成を変更します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="15c0f-150">Unity 内のオブジェクトに 3D サウンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="15c0f-151">手順</span><span class="sxs-lookup"><span data-stu-id="15c0f-151">Instructions</span></span>

* <span data-ttu-id="15c0f-152">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-152">Start Unity.</span></span>
* <span data-ttu-id="15c0f-153">**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-153">Select **Open**.</span></span>
* <span data-ttu-id="15c0f-154">移動し、デスクトップと検索フォルダー アーカイブされた以前のします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="15c0f-155">をクリックして、 **Starting\Decibel**フォルダーを押してから、**フォルダーの選択**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="15c0f-156">プロジェクトの Unity で読み込みを待機します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="15c0f-157"> *\*プロジェクト*\*パネル*\*Scenes\Decibel.unity*\*します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="15c0f-158">**階層**パネルで、展開**HologramCollection**選択**P0LY**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="15c0f-159">設定で、展開**AudioSource**があることを確認しない**Spatialize**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="15c0f-160">既定では、Unity では、立体音場プラグインは読み込まれません。</span><span class="sxs-lookup"><span data-stu-id="15c0f-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="15c0f-161">次の手順では、プロジェクトで空間サウンドを有効になります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="15c0f-162">Unity の上部のメニューに移動**編集 > プロジェクトの設定 > オーディオ**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="15c0f-163">検索、**立体音場プラグイン**ドロップダウンで、選択および**MS HRTF 立体音場**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="15c0f-164">**階層**パネルで、 **HologramCollection > P0LY**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="15c0f-165">**インスペクター**パネルで、検索、**オーディオ ソース**コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="15c0f-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="15c0f-166">チェック、 **Spatialize**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="15c0f-167">ドラッグ、**空間 Blend**スライダーに至る**3D**、または入力**1**編集ボックス。</span><span class="sxs-lookup"><span data-stu-id="15c0f-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="15c0f-168">Unity でプロジェクトをビルドし、Visual Studio でソリューションを構成することはようになりました。</span><span class="sxs-lookup"><span data-stu-id="15c0f-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="15c0f-169">Unity では、次のように選択します。**ファイル > Build Settings**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="15c0f-170">をクリックして**開くシーンを追加**シーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="15c0f-171">選択**ユニバーサル Windows プラットフォーム**で、**プラットフォーム**を一覧表示し、クリックして**スイッチ プラットフォーム**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="15c0f-172">具体的には、HoloLens の開発中、設定**ターゲット デバイス**に**HoloLens**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="15c0f-173">それ以外の場合、残して**任意のデバイス**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="15c0f-174">確認**ビルド タイプ**に設定されている**D3D**と**SDK**に設定されている**インストールされている最新**(16299 またはそれ以降の SDK がある必要があります)。</span><span class="sxs-lookup"><span data-stu-id="15c0f-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="15c0f-175">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-175">Click **Build**.</span></span>
7. <span data-ttu-id="15c0f-176">作成、**新しいフォルダー** "App"という名前です。</span><span class="sxs-lookup"><span data-stu-id="15c0f-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="15c0f-177">1 回のクリック、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="15c0f-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="15c0f-178">キーを押して**フォルダーを選択します**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-178">Press **Select Folder**.</span></span>

<span data-ttu-id="15c0f-179">Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="15c0f-180">開く、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="15c0f-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="15c0f-181">開く、**デシベル Visual Studio ソリューション**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="15c0f-182">HoloLens へのデプロイ: 場合</span><span class="sxs-lookup"><span data-stu-id="15c0f-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="15c0f-183">デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x86**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="15c0f-184">ローカル コンピューター] ボタンの横の矢印のドロップダウンをクリックし、[**リモート マシン**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="15c0f-185">入力**HoloLens デバイスの IP アドレス**認証モードを設定および**ユニバーサル (暗号化されていないプロトコル)** します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="15c0f-186">クリックして**選択**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-186">Click **Select**.</span></span> <span data-ttu-id="15c0f-187">デバイスの IP アドレスがわからない場合に参照**設定 > ネットワークとインターネット > 詳細オプション**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="15c0f-188">上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="15c0f-189">最初に、デバイスに展開するには、する必要があります[Visual Studio をペアリング](using-visual-studio.md#pairing-your-device---hololens-1st-gen)します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="15c0f-190">場合は、イマーシブ ヘッドセットへのデプロイ。</span><span class="sxs-lookup"><span data-stu-id="15c0f-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="15c0f-191">デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x64**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="15c0f-192">必ず、配置ターゲットに設定されて**ローカル マシン**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="15c0f-193">上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="15c0f-194">第 2 章 – 空間のサウンドと相互作用</span><span class="sxs-lookup"><span data-stu-id="15c0f-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="15c0f-195">目標</span><span class="sxs-lookup"><span data-stu-id="15c0f-195">Objectives</span></span>

* <span data-ttu-id="15c0f-196">サウンドを使用してホログラム リアリティを強化します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="15c0f-197">サウンドを使用して、ユーザーの視線の先を指示します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="15c0f-198">サウンドを使用してジェスチャのフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="15c0f-199">パート 1 - 強化よりリアル</span><span class="sxs-lookup"><span data-stu-id="15c0f-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="15c0f-200">主要概念</span><span class="sxs-lookup"><span data-stu-id="15c0f-200">Key Concepts</span></span>

* <span data-ttu-id="15c0f-201">ホログラム サウンドを spatialize します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="15c0f-202">サウンドのソースは、ホログラム上の適切な場所に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="15c0f-203">サウンドの適切な場所が、ホログラムに依存するしようとしています。</span><span class="sxs-lookup"><span data-stu-id="15c0f-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="15c0f-204">たとえば、ホログラムが人間の場合は、ほぼ口とフィートではなくサウンドのソースを配置してください。</span><span class="sxs-lookup"><span data-stu-id="15c0f-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="15c0f-205">手順</span><span class="sxs-lookup"><span data-stu-id="15c0f-205">Instructions</span></span>

<span data-ttu-id="15c0f-206">次の手順では、spatialized サウンドをホログラムにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="15c0f-207">**階層**パネルで、展開**HologramCollection**選択**P0LY**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="15c0f-208">**インスペクター**パネルの**AudioSource**、横に、円をクリックして**AudioClip**選択と**PolyHover**ポップアップから。</span><span class="sxs-lookup"><span data-stu-id="15c0f-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="15c0f-209">次に、円をクリックします**出力**選択**SoundEffects**ポップアップから。</span><span class="sxs-lookup"><span data-stu-id="15c0f-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="15c0f-210">Unity を使用するプロジェクト デシベル**AudioMixer**一連のサウンドの音量の調整を有効にするコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="15c0f-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="15c0f-211">グループ化、サウンドをこの方法では、それぞれのサウンドの相対的なボリュームを維持しながら全体的なボリュームを調整できます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="15c0f-212">**AudioSource**、展開**3D サウンド設定**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="15c0f-213">設定**ドップラー レベル**に**0**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="15c0f-214">ピッチのモーション (ホログラムまたはユーザーのいずれか) に起因ゼロを無効に変更をドップラー レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="15c0f-215">Doppler の典型的な例では、高速移動の車です。</span><span class="sxs-lookup"><span data-stu-id="15c0f-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="15c0f-216">車には、静止しているリスナーが近づく、エンジンのピッチよう増加します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="15c0f-217">リスナーを渡すときに、距離とピッチが低くなります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="15c0f-218">パート 2 - ユーザーの視線の先を指示します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="15c0f-219">主要概念</span><span class="sxs-lookup"><span data-stu-id="15c0f-219">Key Concepts</span></span>

* <span data-ttu-id="15c0f-220">サウンドを使用して、重要なホログラムに注意を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="15c0f-221">耳、目を検索する場所を直接に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="15c0f-222">脳に学習した試して期待しています</span><span class="sxs-lookup"><span data-stu-id="15c0f-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="15c0f-223">学習した予測の 1 つの例では、鳥が人間の頭の上、通常です。</span><span class="sxs-lookup"><span data-stu-id="15c0f-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="15c0f-224">ユーザーは、鳥のサウンドを聞くこと、その最初の反応を検索するは。</span><span class="sxs-lookup"><span data-stu-id="15c0f-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="15c0f-225">Bird クラス、ユーザーの下に配置することは、サウンドを検索する必要があることを期待に基づくホログラムを検索できないの正しい方向に接続することにつながります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="15c0f-226">手順</span><span class="sxs-lookup"><span data-stu-id="15c0f-226">Instructions</span></span>

<span data-ttu-id="15c0f-227">次の手順は、ホログラムを検索するサウンドを使用できるように、背後にある非表示にする P0LY を有効にします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="15c0f-228">**階層**パネルで、**マネージャー**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="15c0f-229">**インスペクター**パネルで、検索**音声入力ハンドラー**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="15c0f-230">**音声入力ハンドラー**、展開**非表示に移動して**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="15c0f-231">変更**関数**に**PolyActions.GoHide**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![キーワード:移動の非表示にします。](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="15c0f-233">パート 3 - ジェスチャのフィードバック</span><span class="sxs-lookup"><span data-stu-id="15c0f-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="15c0f-234">主要概念</span><span class="sxs-lookup"><span data-stu-id="15c0f-234">Key Concepts</span></span>

* <span data-ttu-id="15c0f-235">サウンドを使用して正のジェスチャの確認をユーザーに提供します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="15c0f-236">ユーザーの方法で get を過度に大きい音のサウンドを過されません。</span><span class="sxs-lookup"><span data-stu-id="15c0f-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="15c0f-237">最良のサウンドが微妙な作業は、エクスペリエンスを overshadow されません。</span><span class="sxs-lookup"><span data-stu-id="15c0f-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="15c0f-238">手順</span><span class="sxs-lookup"><span data-stu-id="15c0f-238">Instructions</span></span>

* <span data-ttu-id="15c0f-239">**階層**パネルで、展開**HologramCollection**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="15c0f-240">展開**EnergyHub**選択**ベース**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="15c0f-241">**インスペクター**パネルで、をクリックして**コンポーネントの追加**追加**ジェスチャ サウンド ハンドラー**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="15c0f-242">**ジェスチャ サウンド ハンドラー**、横に円をクリックして**ナビゲーション開始クリップ**と**ナビゲーション更新クリップ**選択と**RotateClick**両方のポップアップから。</span><span class="sxs-lookup"><span data-stu-id="15c0f-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="15c0f-243">Visual Studio で読み込むには、"GestureSoundHandler"をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="15c0f-244">サウンドのジェスチャ ハンドラーは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="15c0f-245">作成し、構成、 **AudioSource**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="15c0f-246">場所、 **AudioSource** 、適切な場所に**GameObject**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="15c0f-247">再生、 **AudioClip**ジェスチャに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="15c0f-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="15c0f-248">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="15c0f-248">Build and Deploy</span></span>

1. <span data-ttu-id="15c0f-249">Unity では、次のように選択します。**ファイル > Build Settings**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="15c0f-250">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-250">Click **Build**.</span></span>
3. <span data-ttu-id="15c0f-251">1 回のクリック、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="15c0f-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="15c0f-252">キーを押して**フォルダーを選択します**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-252">Press **Select Folder**.</span></span>

<span data-ttu-id="15c0f-253">ツールバーが「リリース」、"x86"または"x64"、および「リモート デバイス」ということを確認します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="15c0f-254">それ以外の場合は、これは、Visual Studio のコーディングのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="15c0f-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="15c0f-255">アプリ フォルダーからソリューションを開き直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="15c0f-256">メッセージが表示されたら、プロジェクト ファイルを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="15c0f-257">同様に、Visual Studio からデプロイします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="15c0f-258">後、アプリケーションがデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-258">After the application is deployed:</span></span>

* <span data-ttu-id="15c0f-259">P0LY 内を移動するように、サウンドがどのように変化するかを確認します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="15c0f-260">たとえば *「非表示に移動」* P0LY 背後の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="15c0f-261">サウンドを探します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-261">Find it by the sound.</span></span>
* <span data-ttu-id="15c0f-262">エネルギーのハブの底を見つめます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="15c0f-263">タップし、左または右に回転ホログラムとクリックのサウンドがジェスチャを確認する方法に注意してください。 をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="15c0f-264">注:Tag-along したのテキスト パネルがあります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="15c0f-265">これは、このコースで使用できる利用可能な音声コマンドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="15c0f-266">第 3 章 - 空間のサウンド、および空間マッピング</span><span class="sxs-lookup"><span data-stu-id="15c0f-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="15c0f-267">目標</span><span class="sxs-lookup"><span data-stu-id="15c0f-267">Objectives</span></span>

* <span data-ttu-id="15c0f-268">ホログラムとサウンドを使用して現実の世界との間の相互作用を確認します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="15c0f-269">現実の世界を使用してサウンドが。</span><span class="sxs-lookup"><span data-stu-id="15c0f-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="15c0f-270">パート 1 - 物理世界の相互作用</span><span class="sxs-lookup"><span data-stu-id="15c0f-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="15c0f-271">主要概念</span><span class="sxs-lookup"><span data-stu-id="15c0f-271">Key Concepts</span></span>

* <span data-ttu-id="15c0f-272">物理オブジェクトは、サーフェス、または別の発生すると一般に音を鳴らすオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="15c0f-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="15c0f-273">サウンドのエクスペリエンスで適切なコンテキストがあります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="15c0f-274">たとえば、テーブル杯の設定のメタルの岩を削除するよりも静か音を鳴らす必要があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="15c0f-275">手順</span><span class="sxs-lookup"><span data-stu-id="15c0f-275">Instructions</span></span>

* <span data-ttu-id="15c0f-276">**階層**パネルで、展開**HologramCollection**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="15c0f-277">展開**EnergyHub**、**ベース**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="15c0f-278">**インスペクター**パネルで、をクリックして**コンポーネントの追加**追加**サウンドでの場所をタップし、アクション**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="15c0f-279">**タップすると、サウンド、およびアクションで**:</span><span class="sxs-lookup"><span data-stu-id="15c0f-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="15c0f-280">確認**Tap に親を配置**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="15c0f-281">設定**配置サウンド**に**場所**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="15c0f-282">設定**Pickup サウンド**に**Pickup**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="15c0f-283">下部にある両方のすぐ下の + キーを押して**Pickup アクションで**と**配置アクションに**。</span><span class="sxs-lookup"><span data-stu-id="15c0f-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="15c0f-284">EnergyHub にシーンからドラッグして、 **None (オブジェクト)** フィールド。</span><span class="sxs-lookup"><span data-stu-id="15c0f-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="15c0f-285">[ **Pickup アクションで**、] をクリックして**いいえ関数** -> **EnergyHubBase** -> **ResetAnimation**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="15c0f-286">[**配置アクションに**、] をクリックして**いいえ関数** -> **EnergyHubBase** -> **OnSelect**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![タップすると、サウンド、およびアクションで](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="15c0f-288">パート 2 - サウンド オクルー ジョン</span><span class="sxs-lookup"><span data-stu-id="15c0f-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="15c0f-289">主要概念</span><span class="sxs-lookup"><span data-stu-id="15c0f-289">Key Concepts</span></span>

* <span data-ttu-id="15c0f-290">ライトのように、サウンドは、オクルー ジョンことができます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="15c0f-291">典型的な例では、コンサート ホールです。</span><span class="sxs-lookup"><span data-stu-id="15c0f-291">A classic example is a concert hall.</span></span> <span data-ttu-id="15c0f-292">Hall、ドアの外部でリスナーの基盤とするとが閉じているミュージックのこもった感じです。</span><span class="sxs-lookup"><span data-stu-id="15c0f-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="15c0f-293">通常のボリュームを削減することです。</span><span class="sxs-lookup"><span data-stu-id="15c0f-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="15c0f-294">ドアが開かれたときに万全なサウンドの実際のボリュームで音がします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="15c0f-295">高頻度のサウンドは低周波数を超える吸収一般にします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="15c0f-296">手順</span><span class="sxs-lookup"><span data-stu-id="15c0f-296">Instructions</span></span>

* <span data-ttu-id="15c0f-297">**階層**パネルで、展開**HologramCollection**選択**P0LY**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="15c0f-298">**インスペクター**パネルで、をクリックして**コンポーネントの追加**追加**オーディオ エミッタ**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="15c0f-299">オーディオ エミッタ クラスには、次の機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="15c0f-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="15c0f-300">ボリュームへの変更を復元、 **AudioSource**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="15c0f-301">実行、 **Physics.RaycastNonAlloc**の方向でのユーザーの位置から、 **GameObject**先、 **AudioEmitter**がアタッチされています。</span><span class="sxs-lookup"><span data-stu-id="15c0f-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="15c0f-302">RaycastNonAlloc メソッドは、返される結果の数と割り当てを制限するパフォーマンスの最適化として使用されます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="15c0f-303">各**IAudioInfluencer**呼び出しが発生した、 **ApplyEffect**メソッド。</span><span class="sxs-lookup"><span data-stu-id="15c0f-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="15c0f-304">各前**IAudioInfluencer**されなく発生した呼び出しは、 **RemoveEffect**メソッド。</span><span class="sxs-lookup"><span data-stu-id="15c0f-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="15c0f-305">AudioEmitter を更新する人間の時間のスケールではなくあたりのフレームごとに注意してください。</span><span class="sxs-lookup"><span data-stu-id="15c0f-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="15c0f-306">これには、人間が四半期ごと、または 2 つ目の半分よりも頻繁に更新する必要があると効果を十分に高速移動はされません一般的には行われます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="15c0f-307">ホログラム別に迅速に 1 つの場所からそのテレポート錯覚を中断できます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="15c0f-308">**階層**パネルで、展開**HologramCollection**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="15c0f-309">展開**EnergyHub**選択**BlobOutside**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="15c0f-310">**インスペクター**パネルで、をクリックして**コンポーネントの追加**追加**オーディオ Occluder**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="15c0f-311">**オーディオ Occluder**設定**カットオフ周波数**に**1500**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="15c0f-312">この設定は、1500 Hz に AudioSource 頻度を制限します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="15c0f-313">設定**ボリューム パススルー**に**0.9**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="15c0f-314">この設定は、現在のレベルの 90% を AudioSource の量を削減します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="15c0f-315">オーディオ Occluder に IAudioInfluencer を実装します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="15c0f-316">使用して遮蔽効果を適用、 **AudioLowPassFilter**にアタッチする、 **AudioSource**マネージ購入、 **AudioEmitter**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="15c0f-317">ボリュームの減衰を AudioSource に適用します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="15c0f-318">ニュートラル カットオフ周波数を設定して、フィルターを無効にすることにより、効果を無効にします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="15c0f-319">ニュートラルとして使用される頻度が 22 kHz (22000 Hz) できます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="15c0f-320">この頻度は、人間の耳、この加えないはっきりへの影響、音が聞こえる名目上の最大頻度の上になることにより選択されました。</span><span class="sxs-lookup"><span data-stu-id="15c0f-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="15c0f-321">**階層**パネルで、 **SpatialMapping**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="15c0f-322">**インスペクター**パネルで、をクリックして**コンポーネントの追加**追加**オーディオ Occluder**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="15c0f-323">**オーディオ Occluder**設定**カットオフ周波数**に**750**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="15c0f-324">複数の occluders がユーザーの間のパスの場合、 **AudioEmitter**、最も低い頻度は、フィルターに適用されます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="15c0f-325">設定**ボリューム パススルー**に**0.75**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="15c0f-326">複数 occluders がユーザーの間のパスの場合、 **AudioEmitter**、ボリューム パススルーが追加に適用します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="15c0f-327">**階層**パネルで、**マネージャー**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="15c0f-328">**インスペクター**パネルで、展開**音声入力ハンドラー**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="15c0f-329">**音声入力ハンドラー**、展開**移動料金**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="15c0f-330">変更**関数**に**PolyActions.GoCharge**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![キーワード:料金を参照してください。](images/gocharge.png)

* <span data-ttu-id="15c0f-332">展開**ここ**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="15c0f-333">変更**関数**に**PolyActions.ComeBack**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![キーワード:こちらへ来てください](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="15c0f-335">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="15c0f-335">Build and Deploy</span></span>

* <span data-ttu-id="15c0f-336">同様に、Unity でプロジェクトをビルドし、Visual Studio でデプロイします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="15c0f-337">後、アプリケーションがデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-337">After the application is deployed:</span></span>

* <span data-ttu-id="15c0f-338">たとえば *「移動の料金」* が P0LY エネルギー ハブを入力します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="15c0f-339">サウンドの変更に注意してください。</span><span class="sxs-lookup"><span data-stu-id="15c0f-339">Note the change in the sound.</span></span> <span data-ttu-id="15c0f-340">こもった感じ、少し静かのサウンドにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="15c0f-341">壁やエネルギー ハブとの間には、他のオブジェクトに自分で配置することは、現実の世界でオクルー ジョンによりサウンドのさらに消音がわかります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="15c0f-342">たとえば *「ここでは」* P0LY エネルギー ハブのままにし、自身をする前に配置します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="15c0f-343">P0LY エネルギー ハブを終了すると、サウンドの重なりが削除されたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="15c0f-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="15c0f-344">聴覚オクルー ジョンで引き続き場合 P0LY は現実の世界でオクルー ジョン可能性があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="15c0f-345">P0LY にクリア視野を確保する移動してみてください。</span><span class="sxs-lookup"><span data-stu-id="15c0f-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="15c0f-346">パート 3 - ルーム モデル</span><span class="sxs-lookup"><span data-stu-id="15c0f-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="15c0f-347">主要概念</span><span class="sxs-lookup"><span data-stu-id="15c0f-347">Key Concepts</span></span>

* <span data-ttu-id="15c0f-348">領域のサイズは、サウンドのローカライズに影響を与えるサブリミナル キューを提供します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="15c0f-349">ルームのモデルが 1 に設定されて、**AudioSource**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="15c0f-350">[For Unity MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)ルーム モデルを設定するためのコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="15c0f-351">複合現実エクスペリエンスでは、実際の領域に最適なルーム モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="15c0f-352">仮想現実のシナリオを作成する場合は、仮想環境に最適な部屋のモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="15c0f-353">第 4 章 - 設計</span><span class="sxs-lookup"><span data-stu-id="15c0f-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="15c0f-354">目標</span><span class="sxs-lookup"><span data-stu-id="15c0f-354">Objectives</span></span>

* <span data-ttu-id="15c0f-355">効果的な設計に関する考慮事項を理解します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="15c0f-356">混合の手法とガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="15c0f-357">パート 1 - のサウンドとエクスペリエンスのデザイン</span><span class="sxs-lookup"><span data-stu-id="15c0f-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="15c0f-358">このセクションでは、キーのサウンドとエクスペリエンスの設計に関する考慮事項とガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="15c0f-359">すべてのサウンドを正規化します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-359">Normalize all sounds</span></span>

<span data-ttu-id="15c0f-360">これは、サウンド、時間がかかる可能性があるごとのボリューム レベルを調整する特別な大文字と小文字のコードが不要でと、サウンド ファイルを簡単に更新する機能を制限します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="15c0f-361">無制限のエクスペリエンスの設計</span><span class="sxs-lookup"><span data-stu-id="15c0f-361">Design for an untethered experience</span></span>

<span data-ttu-id="15c0f-362">HoloLens とは、完全包含、無制限の holographic コンピューターです。</span><span class="sxs-lookup"><span data-stu-id="15c0f-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="15c0f-363">ユーザーの移動中にお客様のエクスペリエンスを使用しています。</span><span class="sxs-lookup"><span data-stu-id="15c0f-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="15c0f-364">歩き回ることによって、オーディオの組み合わせをテストすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="15c0f-365">サウンド、ホログラムで論理的な場所からの出力します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="15c0f-366">現実の世界で犬がその末尾からバークしないと、人間の音声が自分のフィートから発生しません。</span><span class="sxs-lookup"><span data-stu-id="15c0f-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="15c0f-367">サウンドが、ホログラムの予期しない部分から出力を必要があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="15c0f-368">小さなホログラム、サウンドのジオメトリの中心から生成するは適切です。</span><span class="sxs-lookup"><span data-stu-id="15c0f-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="15c0f-369">使い慣れたサウンドはローカライズ可能な最も</span><span class="sxs-lookup"><span data-stu-id="15c0f-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="15c0f-370">人間の声や音楽は、非常に簡単にローカライズされます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="15c0f-371">場合は、名前、呼び出しは、非常に正確に判断する方法と、音声が付属してどのような方向から離れたことができます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="15c0f-372">Short、未知のサウンドはローカライズするが難しいです。</span><span class="sxs-lookup"><span data-stu-id="15c0f-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="15c0f-373">ユーザーの期待の認識</span><span class="sxs-lookup"><span data-stu-id="15c0f-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="15c0f-374">有効期間のエクスペリエンスは、サウンドの場所を特定する上で役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="15c0f-375">これは、人間の声が特に簡単にローカライズする 1 つの理由です。</span><span class="sxs-lookup"><span data-stu-id="15c0f-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="15c0f-376">注意すべきユーザーの学習した予測のサウンドを配置するときに重要です。</span><span class="sxs-lookup"><span data-stu-id="15c0f-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="15c0f-377">たとえば、bird 曲がだれかと、一般を調べる、鳥は、視野 (飛行またはツリー) 上に配置する傾向があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="15c0f-378">これは、サウンドの正しい方向で有効にするが、誤ったの垂直方向に検索しホログラムを検索することがない場合は、混乱や不満になるユーザー珍しくありません。</span><span class="sxs-lookup"><span data-stu-id="15c0f-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="15c0f-379">非表示の発信機を避ける</span><span class="sxs-lookup"><span data-stu-id="15c0f-379">Avoid hidden emitters</span></span>

<span data-ttu-id="15c0f-380">現実の世界で、音が聞こえました場合一般にオブジェクトを識別できます、サウンドを生成します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="15c0f-381">これには、お客様のエクスペリエンスにも格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="15c0f-382">ユーザーが、音が聞こえるように、サウンドの発生元からの非常に混乱を招くでき、オブジェクトを表示することができません。</span><span class="sxs-lookup"><span data-stu-id="15c0f-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="15c0f-383">このガイドラインをいくつかの例外があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="15c0f-384">たとえば、フィールドの crickets などの環境音は表示されません必要があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="15c0f-385">ライフ エクスペリエンスにより、ソースを確認する必要はありませんこれらのサウンドの知識。</span><span class="sxs-lookup"><span data-stu-id="15c0f-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="15c0f-386">パート 2 - サウンドのミキシング</span><span class="sxs-lookup"><span data-stu-id="15c0f-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="15c0f-387">対象に、HoloLens の 70% のボリュームのバランス</span><span class="sxs-lookup"><span data-stu-id="15c0f-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="15c0f-388">複合現実エクスペリエンスでは、現実の世界において発生するホログラムを許可します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="15c0f-389">現実の世界音が聞こえるにも許可します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="15c0f-390">70% のボリュームのターゲットにより、ユーザー エクスペリエンスの音を鳴らしての世界をそれらにお待ちしております。</span><span class="sxs-lookup"><span data-stu-id="15c0f-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="15c0f-391">100% のボリュームでの HoloLens の外部サウンドを一覧から必要があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="15c0f-392">100% のボリューム レベルでは、仮想現実エクスペリエンスに似ています。</span><span class="sxs-lookup"><span data-stu-id="15c0f-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="15c0f-393">視覚的に、ユーザーはさまざまな環境に送信されます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="15c0f-394">同じが当てはまる音声で返すことです。</span><span class="sxs-lookup"><span data-stu-id="15c0f-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="15c0f-395">Unity AudioMixer を使用してサウンドのカテゴリを調整するには</span><span class="sxs-lookup"><span data-stu-id="15c0f-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="15c0f-396">バランスを設計するときに多くの場合をお勧めサウンドのカテゴリを作成し、そのボリュームの単位としてを増減する機能があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="15c0f-397">全体的なミックスに素早く簡単に変更しながら、それぞれのサウンドの相対的なレベルを保持します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="15c0f-398">一般的なカテゴリがあります。サウンド効果、アンビエンス、ボイス オーバーおよびバック グラウンド ミュージックします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="15c0f-399">ユーザーの視線の先に基づくサウンドをミキシングします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="15c0f-400">多くの場合、おくと便利です、サウンドのミックスを変更する場所に基づいて作業環境で、ユーザーが (またはない) を検索します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="15c0f-401">この手法の 1 つの一般的な用途では、前に、情報に注目するユーザーを容易にできるように Holographic フレーム外にあるホログラムのボリューム レベルを下げます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="15c0f-402">別の使用では、重要なイベントに、ユーザーの注目を集めるサウンドの音量を上げるです。</span><span class="sxs-lookup"><span data-stu-id="15c0f-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="15c0f-403">バランスの構築</span><span class="sxs-lookup"><span data-stu-id="15c0f-403">Building your mix</span></span>

<span data-ttu-id="15c0f-404">バランスを構築する場合は、エクスペリエンスのバック グラウンド オーディオから開始し、重要度に基づいてレイヤーを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="15c0f-405">多くの場合、この結果、各層は、以前よりも大きくします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="15c0f-406">反転じょうごグラフ、少なくとも重要度としてバランスを考えた (および通常静かサウンド) 次の図のようなバランスを構造体を下部で、推奨は。</span><span class="sxs-lookup"><span data-stu-id="15c0f-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![サウンドのミックス構造体](images/soundlevels.png)

<span data-ttu-id="15c0f-408">ボイス オーバーは、興味深いシナリオです。</span><span class="sxs-lookup"><span data-stu-id="15c0f-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="15c0f-409">ベースのエクスペリエンスを作成するには、(ローカライズされていない) のステレオ サウンドを持っているか、ボイス オーバーの spatialize をする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="15c0f-410">2 つの Microsoft エクスペリエンスを公開する各シナリオの優れた例について説明します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="15c0f-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87)を介してステレオの音声を使用します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="15c0f-412">ナレーターは、表示されている場所と記述して、サウンドが一貫性のある変わることはありません、ユーザーの位置で。</span><span class="sxs-lookup"><span data-stu-id="15c0f-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="15c0f-413">これにより、環境の spatialized サウンドからしないシーンを記述するナレーターができます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="15c0f-414">[フラグメント](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8)経由で、探偵の形式で spatialized 音声を使用します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="15c0f-415">探偵の音声は、ルームに実際の人間があった場合に重要な手掛かりをユーザーの注意を届けるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="15c0f-416">これにより、ミステリーを解決するのにエクスペリエンス immersion 感はさらに大きくなります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="15c0f-417">パート 3 - パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="15c0f-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="15c0f-418">CPU 使用率</span><span class="sxs-lookup"><span data-stu-id="15c0f-418">CPU usage</span></span>

<span data-ttu-id="15c0f-419">空間サウンドを使用する場合、10 ~ 12 の発信機は、CPU の約 12% を消費します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="15c0f-420">Stream の時間の長いオーディオ ファイル</span><span class="sxs-lookup"><span data-stu-id="15c0f-420">Stream long audio files</span></span>

<span data-ttu-id="15c0f-421">オーディオ データを共通のサンプル レート (44.1 と 48 kHz) では特に、大規模なことができます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="15c0f-422">一般的な規則は、アプリケーションのメモリ使用率を低減 5 ~ 10 秒より長いオーディオ ファイルをストリーミングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="15c0f-423">Unity では、ファイルのインポートの設定では、ストリーミングに対応するオーディオ ファイルをマークできます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![オーディオの読み込み設定](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="15c0f-425">第 5 章「特殊効果</span><span class="sxs-lookup"><span data-stu-id="15c0f-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="15c0f-426">目標</span><span class="sxs-lookup"><span data-stu-id="15c0f-426">Objectives</span></span>

* <span data-ttu-id="15c0f-427">"マジック Windows"には、深さを追加します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="15c0f-428">仮想世界にユーザーを表示します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="15c0f-429">マジック Windows</span><span class="sxs-lookup"><span data-stu-id="15c0f-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="15c0f-430">主要概念</span><span class="sxs-lookup"><span data-stu-id="15c0f-430">Key Concepts</span></span>

* <span data-ttu-id="15c0f-431">ビューを非表示の世界を作成することは、視覚的に説得力のあるです。</span><span class="sxs-lookup"><span data-stu-id="15c0f-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="15c0f-432">ホログラムまたはユーザーが非表示の世界に近い場合は、オーディオ効果を追加することで、リアリティを強化します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="15c0f-433">手順</span><span class="sxs-lookup"><span data-stu-id="15c0f-433">Instructions</span></span>

* <span data-ttu-id="15c0f-434">**階層**パネルで、展開**HologramCollection**選択**黄泉**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="15c0f-435">展開**黄泉**選択**VoiceSource**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="15c0f-436">**インスペクター**パネルで、をクリックして**コンポーネントの追加**追加**ユーザー音声エフェクト**。</span><span class="sxs-lookup"><span data-stu-id="15c0f-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="15c0f-437">**AudioSource**にコンポーネントを追加する**VoiceSource**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="15c0f-438">**AudioSource**設定**出力**に**UserVoice (Mixer)** します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="15c0f-439">チェック、 **Spatialize**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="15c0f-440">ドラッグ、**空間 Blend**スライダーに至る**3D**、または入力**1**編集ボックス。</span><span class="sxs-lookup"><span data-stu-id="15c0f-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="15c0f-441">展開**3D サウンド設定**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="15c0f-442">設定**ドップラー レベル**に**0**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="15c0f-443">**ユーザー音声エフェクト**設定**親オブジェクト**を**黄泉**シーンから。</span><span class="sxs-lookup"><span data-stu-id="15c0f-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="15c0f-444">設定**最大距離**に**1**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="15c0f-445">設定**最大距離**指示**ユーザー音声エフェクト**閉じる方法があります親オブジェクトに効果が有効にする前にします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="15c0f-446">**ユーザー音声エフェクト**、展開**コーラス パラメーター**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="15c0f-447">設定**深さ**に**0.1**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="15c0f-448">設定**ボリュームを 1 つをタップします**、 **2 のボリュームをタップ**と**3 つのボリュームをタップします**に**0.8**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="15c0f-449">設定**元音量**に**0.5**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="15c0f-450">以前の設定は、Unity のパラメーターを構成する**AudioChorusFilter**ユーザーの音声に豊富な機能を追加するために使用します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="15c0f-451">**ユーザー音声エフェクト**、展開**エコー パラメーター**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="15c0f-452">設定**遅延**に**300**</span><span class="sxs-lookup"><span data-stu-id="15c0f-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="15c0f-453">設定**比率を Decay**に**0.2**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="15c0f-454">設定**元音量**に**0**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="15c0f-455">以前の設定は、Unity のパラメーターを構成する**AudioEchoFilter**をエコーするユーザーの音声が発生するために使用します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="15c0f-456">ユーザー音声エフェクト スクリプトは担います。</span><span class="sxs-lookup"><span data-stu-id="15c0f-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="15c0f-457">ユーザーの間の距離を測定して、 **GameObject**スクリプトがアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="15c0f-458">ユーザーが直面しているかどうかを決定する、 **GameObject**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="15c0f-459">ユーザーが有効に有効にするために、距離に関係なく、GameObject 直面する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15c0f-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="15c0f-460">適用して、構成、 **AudioChorusFilter**と**AudioEchoFilter**を**AudioSource**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="15c0f-461">フィルターを無効にして、効果を無効にします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="15c0f-462">ユーザー ボイスの効果は、Mic Stream セレクター コンポーネントを使用してから、 [for Unity MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)を高品質の音声ストリームを選択し、Unity のオーディオ システムにルーティングします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="15c0f-463">**階層**パネルで、**マネージャー**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="15c0f-464">**インスペクター**パネルで、展開**音声入力ハンドラー**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="15c0f-465">**音声入力ハンドラー**、展開**表示黄泉**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="15c0f-466">変更**関数**に**UnderworldBase.OnEnable**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![キーワード:黄泉を表示します。](images/showunderworld.png)

* <span data-ttu-id="15c0f-468">展開**黄泉を非表示に**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="15c0f-469">変更**関数**に**UnderworldBase.OnDisable**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![キーワード:黄泉を非表示にします。](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="15c0f-471">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="15c0f-471">Build and Deploy</span></span>

* <span data-ttu-id="15c0f-472">同様に、Unity でプロジェクトをビルドし、Visual Studio でデプロイします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="15c0f-473">後、アプリケーションがデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-473">After the application is deployed:</span></span>

* <span data-ttu-id="15c0f-474">顔の画面 (壁、floor、テーブル) と say *「を表示する黄泉」* します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="15c0f-475">黄泉が表示され、他のすべてのホログラムは表示されません。</span><span class="sxs-lookup"><span data-stu-id="15c0f-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="15c0f-476">黄泉が表示されない場合は、実際の画面が発生したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="15c0f-477">1 メートル以内黄泉ホログラムのアプローチし、会話の開始。</span><span class="sxs-lookup"><span data-stu-id="15c0f-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="15c0f-478">自分の声に適用されるオーディオ効果はようになりました。</span><span class="sxs-lookup"><span data-stu-id="15c0f-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="15c0f-479">黄泉から有効にして、効果が適用されていない方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="15c0f-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="15c0f-480">たとえば *「非表示にする黄泉」* 黄泉を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="15c0f-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="15c0f-481">黄泉が非表示にして、以前に非表示のホログラムが再表示されます。</span><span class="sxs-lookup"><span data-stu-id="15c0f-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="15c0f-482">最後です</span><span class="sxs-lookup"><span data-stu-id="15c0f-482">The End</span></span>

<span data-ttu-id="15c0f-483">これで終了です。</span><span class="sxs-lookup"><span data-stu-id="15c0f-483">Congratulations!</span></span> <span data-ttu-id="15c0f-484">完了したので**MR 空間 220。空間サウンド**します。</span><span class="sxs-lookup"><span data-stu-id="15c0f-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="15c0f-485">世界をリッスンしてサウンドをお客様のエクスペリエンスを活用しましょう!</span><span class="sxs-lookup"><span data-stu-id="15c0f-485">Listen to the world and bring your experiences to life with sound!</span></span>
