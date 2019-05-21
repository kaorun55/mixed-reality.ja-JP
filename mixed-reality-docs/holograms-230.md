---
title: MR 空間 230 - 空間マッピング
description: このコーディング空間マッピングの概念の詳細については、Unity、Visual Studio および HoloLens の使用に関するチュートリアルに従います。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit unity、academy、チュートリアル、空間マッピング、画面の再構築、メッシュ
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993559"
---
>[!NOTE]
><span data-ttu-id="7beef-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7beef-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7beef-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="7beef-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7beef-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="7beef-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7beef-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="7beef-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7beef-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="7beef-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="7beef-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="7beef-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="7beef-110">MR 空間 230:空間マッピング</span><span class="sxs-lookup"><span data-stu-id="7beef-110">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="7beef-111">[空間マッピング](spatial-mapping.md)ホログラム環境に関する指示することによって、現実の世界と仮想世界をまとめて結合します。</span><span class="sxs-lookup"><span data-stu-id="7beef-111">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="7beef-112">MR 空間 230 (プロジェクト プラネタリウム用) で説明する方法。</span><span class="sxs-lookup"><span data-stu-id="7beef-112">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="7beef-113">開発用コンピューターに、HoloLens の環境と転送データをスキャンします。</span><span class="sxs-lookup"><span data-stu-id="7beef-113">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="7beef-114">シェーダーを調査し、自分のスペースを視覚化するために使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7beef-114">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="7beef-115">メッシュの処理を使用して単純な平面に部屋メッシュに分解します。</span><span class="sxs-lookup"><span data-stu-id="7beef-115">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="7beef-116">学習した配置の手法よりも高度[MR 基本 101](holograms-101.md)ホログラムを環境に配置できる場所についてのフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="7beef-116">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="7beef-117">遮蔽効果、探索、ホログラムが現実世界のオブジェクトの背後にあると、表示できるようにも、x 線画像のビジョンを!</span><span class="sxs-lookup"><span data-stu-id="7beef-117">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="7beef-118">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="7beef-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7beef-119">コース</span><span class="sxs-lookup"><span data-stu-id="7beef-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7beef-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7beef-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7beef-121"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="7beef-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="7beef-122">MR 空間 230:空間マッピング</span><span class="sxs-lookup"><span data-stu-id="7beef-122">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="7beef-123">✔️</span><span class="sxs-lookup"><span data-stu-id="7beef-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="7beef-124">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="7beef-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="7beef-125">前提条件</span><span class="sxs-lookup"><span data-stu-id="7beef-125">Prerequisites</span></span>

* <span data-ttu-id="7beef-126">正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="7beef-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="7beef-127">基本的なC#プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="7beef-127">Some basic C# programming ability.</span></span>
* <span data-ttu-id="7beef-128">完了する必要があります[MR 基本 101](holograms-101.md)します。</span><span class="sxs-lookup"><span data-stu-id="7beef-128">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="7beef-129">HoloLens デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。</span><span class="sxs-lookup"><span data-stu-id="7beef-129">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="7beef-130">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="7beef-130">Project files</span></span>

* <span data-ttu-id="7beef-131">ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip)プロジェクトに必要です。</span><span class="sxs-lookup"><span data-stu-id="7beef-131">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="7beef-132"> Unity 2017.2 またはそれ以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="7beef-132"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="7beef-133">Unity 5.6 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)します。</span><span class="sxs-lookup"><span data-stu-id="7beef-133">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="7beef-134">Unity 5.5 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)します。</span><span class="sxs-lookup"><span data-stu-id="7beef-134">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="7beef-135">Unity 5.4 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)します。</span><span class="sxs-lookup"><span data-stu-id="7beef-135">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="7beef-136">解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。</span><span class="sxs-lookup"><span data-stu-id="7beef-136">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="7beef-137">をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)します。</span><span class="sxs-lookup"><span data-stu-id="7beef-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="7beef-138">メモ</span><span class="sxs-lookup"><span data-stu-id="7beef-138">Notes</span></span>

* <span data-ttu-id="7beef-139">無効にする Visual Studio のニーズに「マイ コードのみを有効化」(*unchecked*) [ツール] > オプション >、コードにブレークポイントをヒットするためにデバッグします。</span><span class="sxs-lookup"><span data-stu-id="7beef-139">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="7beef-140">Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="7beef-140">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="7beef-141">開始**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-141">Start **Unity**.</span></span>
* <span data-ttu-id="7beef-142">選択**新規**新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7beef-142">Select **New** to create a new project.</span></span>
* <span data-ttu-id="7beef-143">プロジェクトに名前を**プラネタリウム用**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-143">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="7beef-144">いることを確認、 **3D**設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="7beef-144">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="7beef-145">クリックして**プロジェクトを作成する**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-145">Click **Create Project**.</span></span>
* <span data-ttu-id="7beef-146">Unity が起動したらに移動して**編集 > プロジェクトの設定 > Player**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-146">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="7beef-147">**インスペクター**パネルで検索し、緑色**Windows ストア**アイコン。</span><span class="sxs-lookup"><span data-stu-id="7beef-147">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="7beef-148">展開**他の設定**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-148">Expand **Other Settings**.</span></span>
* <span data-ttu-id="7beef-149">**レンダリング** セクションで、チェック、**仮想現実サポート**オプション。</span><span class="sxs-lookup"><span data-stu-id="7beef-149">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="7beef-150">いることを確認**Windows Holographic**の一覧に表示される**仮想現実 Sdk**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-150">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="7beef-151">そうでない場合は、選択、 **+** 一覧の下部にあるボタンをクリックし、選択**Windows Holographic**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-151">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="7beef-152">展開**公開設定**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-152">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="7beef-153">**機能**セクションで、次の設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="7beef-153">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="7beef-154">internetClientServer</span><span class="sxs-lookup"><span data-stu-id="7beef-154">InternetClientServer</span></span>
    * <span data-ttu-id="7beef-155">privateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="7beef-155">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="7beef-156">マイク</span><span class="sxs-lookup"><span data-stu-id="7beef-156">Microphone</span></span>
    * <span data-ttu-id="7beef-157">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="7beef-157">SpatialPerception</span></span>
* <span data-ttu-id="7beef-158">移動して**編集 > プロジェクトの設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="7beef-158">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="7beef-159">**インスペクター**パネルの [Windows ストア] アイコンの下の 'Default' の行の黒のドロップダウン矢印とする既定の設定を変更する**Very Low**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-159">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Very Low**.</span></span>
* <span data-ttu-id="7beef-160">移動して**資産 > パッケージのインポート > カスタム パッケージ**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-160">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="7beef-161">移動し、 **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="7beef-161">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="7beef-162">をクリックして**Planetarium.unitypackage**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-162">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="7beef-163">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7beef-163">Click **Open**.</span></span>
* <span data-ttu-id="7beef-164">**Unity パッケージのインポート**ウィンドウが表示されます をクリックして、**インポート**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7beef-164">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="7beef-165">このプロジェクトを完了する必要があります。 その資産のすべてをインポートする Unity を待ちます。</span><span class="sxs-lookup"><span data-stu-id="7beef-165">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="7beef-166">**階層**パネルで、削除、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-166">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="7beef-167">**プロジェクト**パネル、 **HoloToolkit-SpatialMapping-230\Utilities\Prefabs**フォルダー、検索、 **Main Camera**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7beef-167">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="7beef-168">ドラッグ アンド ドロップ、 **Main Camera**にプレハブ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="7beef-168">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7beef-169">**階層**パネルで、削除、**指向性光**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7beef-169">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="7beef-170">**プロジェクト**パネル、**ホログラム**フォルダー、検索、**カーソル**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7beef-170">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="7beef-171">ドラッグ アンド ドロップ、**カーソル**にプレハブ、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-171">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="7beef-172">**階層**パネルで、**カーソル**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7beef-172">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="7beef-173">**インスペクター**パネルで、をクリックして、**レイヤー**ドロップダウンを選択します**レイヤーを編集しています.**.</span><span class="sxs-lookup"><span data-stu-id="7beef-173">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="7beef-174">名前**ユーザー層 31**として"**SpatialMapping**"。</span><span class="sxs-lookup"><span data-stu-id="7beef-174">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="7beef-175">新しいシーンを保存します。**ファイル > としてシーンを保存しています.**</span><span class="sxs-lookup"><span data-stu-id="7beef-175">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="7beef-176">クリックして**新しいフォルダー**フォルダーの名前と**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-176">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="7beef-177">ファイルに名前を"**プラネタリウム用**"で保存し、**シーン**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="7beef-177">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="7beef-178">第 1 章 - スキャン</span><span class="sxs-lookup"><span data-stu-id="7beef-178">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="7beef-179">**目標**</span><span class="sxs-lookup"><span data-stu-id="7beef-179">**Objectives**</span></span>
* <span data-ttu-id="7beef-180">SurfaceObserver、および設定への影響を経験する方法とパフォーマンスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7beef-180">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="7beef-181">スキャンの部屋のメッシュを収集するエクスペリエンスのルームを作成します。</span><span class="sxs-lookup"><span data-stu-id="7beef-181">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="7beef-182">**手順**</span><span class="sxs-lookup"><span data-stu-id="7beef-182">**Instructions**</span></span>
* <span data-ttu-id="7beef-183">**プロジェクト**パネル**HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs**フォルダー、検索、 **SpatialMapping** prefab します。</span><span class="sxs-lookup"><span data-stu-id="7beef-183">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="7beef-184">ドラッグ アンド ドロップ、 **SpatialMapping**にプレハブ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="7beef-184">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="7beef-185">**ビルドおよび展開 (パート 1)**</span><span class="sxs-lookup"><span data-stu-id="7beef-185">**Build and Deploy (part 1)**</span></span>
* <span data-ttu-id="7beef-186">Unity では、次のように選択します。**ファイル > Build Settings**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-186">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="7beef-187">クリックして**開くシーンを追加**を追加する、**プラネタリウム用**シーンをビルドします。</span><span class="sxs-lookup"><span data-stu-id="7beef-187">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="7beef-188">選択**ユニバーサル Windows プラットフォーム**で、**プラットフォーム**を一覧表示し、クリックして**スイッチ プラットフォーム**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-188">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="7beef-189">設定**SDK**に**ユニバーサル 10**と**UWP ビルドの種類**に**D3D**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-189">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="7beef-190">確認**UnityC#プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-190">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="7beef-191">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7beef-191">Click **Build**.</span></span>
* <span data-ttu-id="7beef-192">作成、**新しいフォルダー** "App"という名前です。</span><span class="sxs-lookup"><span data-stu-id="7beef-192">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="7beef-193">1 回のクリック、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="7beef-193">Single click the **App** folder.</span></span>
* <span data-ttu-id="7beef-194">キーを押して、**フォルダーの選択**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7beef-194">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="7beef-195">Unity が完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7beef-195">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="7beef-196">ダブルクリックして、**アプリ**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="7beef-196">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="7beef-197">ダブルクリックして**Planetarium.sln** Visual Studio でプロジェクトを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="7beef-197">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="7beef-198">Visual Studio で、上部のツールバーを使用して構成を変更する**リリース**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-198">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="7beef-199">変更するためのプラットフォーム**x86**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-199">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="7beef-200">' ローカル コンピューター] の右側の下矢印をクリックし、[**リモート マシン**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-200">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="7beef-201">入力[デバイスの IP アドレス](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network)アドレス フィールドし、する認証モードを変更する**ユニバーサル (暗号化されていないプロトコル)** します。</span><span class="sxs-lookup"><span data-stu-id="7beef-201">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="7beef-202">クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-202">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="7beef-203">ウォッチ、**出力**パネルの Visual Studio でのビルドと配置状態。</span><span class="sxs-lookup"><span data-stu-id="7beef-203">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="7beef-204">アプリがデプロイされると、室内をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7beef-204">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="7beef-205">黒と白のワイヤー フレームのメッシュに覆わ周囲の画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7beef-205">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="7beef-206">環境をスキャンします。</span><span class="sxs-lookup"><span data-stu-id="7beef-206">Scan your surroundings.</span></span> <span data-ttu-id="7beef-207">必ず、壁、天井、フロアを見てください。</span><span class="sxs-lookup"><span data-stu-id="7beef-207">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="7beef-208">**ビルドおよび展開 (パート 2)**</span><span class="sxs-lookup"><span data-stu-id="7beef-208">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="7beef-209">これで空間マッピングに与える影響についてパフォーマンスを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="7beef-209">Now let's explore how Spatial Mapping can affect performance.</span></span>
* <span data-ttu-id="7beef-210">Unity では、次のように選択します。**ウィンドウ > Profiler**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-210">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="7beef-211">クリックして**Profiler の追加 > GPU**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-211">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="7beef-212">クリックして**Active Profiler > <Enter IP>** します。</span><span class="sxs-lookup"><span data-stu-id="7beef-212">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="7beef-213">入力、 **IP アドレス**HoloLens の。</span><span class="sxs-lookup"><span data-stu-id="7beef-213">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="7beef-214">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7beef-214">Click **Connect**.</span></span>
* <span data-ttu-id="7beef-215">フレームのレンダリングに GPU の所要時間をミリ秒数を確認します。</span><span class="sxs-lookup"><span data-stu-id="7beef-215">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="7beef-216">デバイスで実行されているアプリケーションを停止します。</span><span class="sxs-lookup"><span data-stu-id="7beef-216">Stop the application from running on the device.</span></span>
* <span data-ttu-id="7beef-217">Visual Studio に戻り、開く**SpatialMappingObserver.cs**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-217">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="7beef-218">これは、アセンブリ CSharp (ユニバーサル Windows) プロジェクトの HoloToolkit\SpatialMapping フォルダーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7beef-218">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="7beef-219">検索、 **Awake()** 関数は、し、次のコード行を追加します。**TrianglesPerCubicMeter 1200; を =**</span><span class="sxs-lookup"><span data-stu-id="7beef-219">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="7beef-220">お使いのデバイスにプロジェクトを再デプロイし、**プロファイラーを再接続**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-220">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="7beef-221">フレームのレンダリング時間 (ミリ秒) の数の変更を確認します。</span><span class="sxs-lookup"><span data-stu-id="7beef-221">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="7beef-222">デバイスで実行されているアプリケーションを停止します。</span><span class="sxs-lookup"><span data-stu-id="7beef-222">Stop the application from running on the device.</span></span>

<span data-ttu-id="7beef-223">**保存して Unity で読み込む**</span><span class="sxs-lookup"><span data-stu-id="7beef-223">**Save and load in Unity**</span></span>

<span data-ttu-id="7beef-224">最後に、みましょう、部屋のメッシュを保存し、Unity に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="7beef-224">Finally, let's save our room mesh and load it into Unity.</span></span>
* <span data-ttu-id="7beef-225">Visual Studio に戻り、削除、 **TrianglesPerCubicMeter**で追加した行、 **Awake()** 前のセクションの中に機能します。</span><span class="sxs-lookup"><span data-stu-id="7beef-225">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="7beef-226">デバイスにプロジェクトを再デプロイします。</span><span class="sxs-lookup"><span data-stu-id="7beef-226">Redeploy the project to your device.</span></span> <span data-ttu-id="7beef-227">私たちは現在実行されてで**500**立方メーターごとの三角形です。</span><span class="sxs-lookup"><span data-stu-id="7beef-227">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="7beef-228">ブラウザーを開きに移動する、HoloLens の ip アドレスの入力、 **Windows Device Portal**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-228">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="7beef-229">選択、 **3D 表示**左側のパネルのオプション。</span><span class="sxs-lookup"><span data-stu-id="7beef-229">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="7beef-230">**再構築のサーフェス**選択、**更新**ボタン。</span><span class="sxs-lookup"><span data-stu-id="7beef-230">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="7beef-231">表示ウィンドウに表示される、HoloLens のスキャンが完了する領域をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7beef-231">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="7beef-232">部屋のスキャンを保存するキーを押して、**保存**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7beef-232">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="7beef-233">開く、**ダウンロード**ルームが保存されたモデルを見つけてフォルダー **SRMesh.obj**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-233">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="7beef-234">コピー **SRMesh.obj**を**資産**Unity プロジェクトのフォルダー。</span><span class="sxs-lookup"><span data-stu-id="7beef-234">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="7beef-235">Unity では、選択、 **SpatialMapping**オブジェクト、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="7beef-235">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7beef-236">検索、**オブジェクトのサーフェイスのオブザーバー (スクリプト)** コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="7beef-236">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="7beef-237">右側に円をクリックして、**ルーム モデル**プロパティ。</span><span class="sxs-lookup"><span data-stu-id="7beef-237">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="7beef-238">検索し、選択、 **SRMesh**オブジェクトし、ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7beef-238">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="7beef-239">いることを確認、**ルーム モデル**プロパティ、**インスペクター**パネルに設定されています**SRMesh**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-239">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="7beef-240">キーを押して、**再生**Unity のプレビュー モードを開始するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7beef-240">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="7beef-241">SpatialMapping コンポーネントは、Unity で使用することができます、部屋の保存されたモデルから、メッシュを読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="7beef-241">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="7beef-242">切り替える**シーン**ワイヤー フレーム シェーダーで表示されるルーム モデルのすべてを表示するビュー。</span><span class="sxs-lookup"><span data-stu-id="7beef-242">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="7beef-243">キーを押して、**再生**プレビュー モードを終了するには、もう一度ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7beef-243">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="7beef-244">**注:** Unity では、プレビュー モードを入力すること、次回保存ルーム メッシュ既定で読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="7beef-244">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="7beef-245">第 2 章 - 視覚エフェクト</span><span class="sxs-lookup"><span data-stu-id="7beef-245">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="7beef-246">**目標**</span><span class="sxs-lookup"><span data-stu-id="7beef-246">**Objectives**</span></span>
* <span data-ttu-id="7beef-247">シェーダーの基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="7beef-247">Learn the basics of shaders.</span></span>
* <span data-ttu-id="7beef-248">環境を視覚化します。</span><span class="sxs-lookup"><span data-stu-id="7beef-248">Visualize your surroundings.</span></span>

<span data-ttu-id="7beef-249">**手順**</span><span class="sxs-lookup"><span data-stu-id="7beef-249">**Instructions**</span></span>
* <span data-ttu-id="7beef-250">Unity の**階層**パネルで、 **SpatialMapping**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7beef-250">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="7beef-251">**インスペクター**パネルで、検索、**空間マッピング マネージャー (スクリプト)** コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="7beef-251">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="7beef-252">右側に円をクリックして、**画面マテリアル**プロパティ。</span><span class="sxs-lookup"><span data-stu-id="7beef-252">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="7beef-253">検索し、選択、 **BlueLinesOnWalls**マテリアルと、ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7beef-253">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="7beef-254">**プロジェクト**パネル**シェーダー**フォルダーをダブルクリックして、 **BlueLinesOnWalls**を Visual Studio でシェーダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="7beef-254">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="7beef-255">これは、簡単なピクセル (頂点のフラグメントを)、次のタスクを実行するには、シェーダー。</span><span class="sxs-lookup"><span data-stu-id="7beef-255">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="7beef-256">ワールド空間には、頂点の位置を変換します。</span><span class="sxs-lookup"><span data-stu-id="7beef-256">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="7beef-257">頂点の通常ピクセルが垂直方向であるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="7beef-257">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="7beef-258">レンダリングのピクセルの色を設定します。</span><span class="sxs-lookup"><span data-stu-id="7beef-258">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="7beef-259">**構築し、デプロイ**</span><span class="sxs-lookup"><span data-stu-id="7beef-259">**Build and Deploy**</span></span>
* <span data-ttu-id="7beef-260">Unity とキーを押してに戻る**再生**プレビュー モードを入力します。</span><span class="sxs-lookup"><span data-stu-id="7beef-260">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="7beef-261">青い線は、ルーム メッシュ (これは、保存済みのスキャン データから自動的に読み込まれます) のすべての垂直画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="7beef-261">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="7beef-262">切り替えて、**シーン** タブを部屋の表示を調整および Unity での部屋全体、メッシュの表示方法を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7beef-262">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="7beef-263">**プロジェクト**パネルで、検索、**資料**フォルダーと選択、 **BlueLinesOnWalls**マテリアル。</span><span class="sxs-lookup"><span data-stu-id="7beef-263">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="7beef-264">一部のプロパティを変更して、Unity エディターで変更の表示方法を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7beef-264">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="7beef-265">**インスペクター**パネルで、調整、 **LineScale**線が太くまたは幅が狭いほどを表示するのには値。</span><span class="sxs-lookup"><span data-stu-id="7beef-265">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="7beef-266">**インスペクター**パネルで、調整、 **LinesPerMeter**各壁に表示される行の数を変更する値。</span><span class="sxs-lookup"><span data-stu-id="7beef-266">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="7beef-267">クリックして**再生**プレビュー モードを終了するには、もう一度です。</span><span class="sxs-lookup"><span data-stu-id="7beef-267">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="7beef-268">ビルド、HoloLens に展開し、実際のサーフェスにレンダリング シェーダーを表示する方法を確認します。</span><span class="sxs-lookup"><span data-stu-id="7beef-268">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="7beef-269">Unity は、素材のプレビューの良い仕事をするが、常に、デバイスでのレンダリングをチェック アウトすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7beef-269">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="7beef-270">第 3 章 - 処理</span><span class="sxs-lookup"><span data-stu-id="7beef-270">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="7beef-271">**目標**</span><span class="sxs-lookup"><span data-stu-id="7beef-271">**Objectives**</span></span>
* <span data-ttu-id="7beef-272">アプリケーションで使用するための空間マッピング データを処理するための手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7beef-272">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="7beef-273">平面を見つけて、三角形を削除する空間のマッピング データを分析します。</span><span class="sxs-lookup"><span data-stu-id="7beef-273">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="7beef-274">ホログラムを配置するためには、平面を使用します。</span><span class="sxs-lookup"><span data-stu-id="7beef-274">Use planes for hologram placement.</span></span>

<span data-ttu-id="7beef-275">**手順**</span><span class="sxs-lookup"><span data-stu-id="7beef-275">**Instructions**</span></span>
* <span data-ttu-id="7beef-276">Unity の**プロジェクト**パネル、**ホログラム**フォルダー、検索、 **SpatialProcessing**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7beef-276">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="7beef-277">ドラッグ アンド ドロップ、 **SpatialProcessing**オブジェクトを**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="7beef-277">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="7beef-278">SpatialProcessing プレハブには、空間のマッピング データを処理するためのコンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7beef-278">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="7beef-279">**SurfaceMeshesToPlanes.cs**見つけて平面空間マッピング データに基づいて生成されます。</span><span class="sxs-lookup"><span data-stu-id="7beef-279">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="7beef-280">平面を壁、フロア、シーリングを表すアプリケーションで使用します。</span><span class="sxs-lookup"><span data-stu-id="7beef-280">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="7beef-281">このプレハブも含まれています。 **RemoveSurfaceVertices.cs**空間マッピング メッシュから頂点を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="7beef-281">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="7beef-282">これは、メッシュ内の穴を作成または削除 (平面は、代わりに使用できる) ためには必要なくなりましたされる余分な三角形に使用できます。</span><span class="sxs-lookup"><span data-stu-id="7beef-282">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>
* <span data-ttu-id="7beef-283">Unity の**プロジェクト**パネル、**ホログラム**フォルダー、検索、 **SpaceCollection**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7beef-283">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="7beef-284">ドラッグ アンド ドロップ、 **SpaceCollection**オブジェクトを**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="7beef-284">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7beef-285">**階層**パネルで、 **SpatialProcessing**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7beef-285">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="7beef-286">**インスペクター**パネルで、検索、**プレイ領域マネージャー (スクリプト)** コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="7beef-286">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="7beef-287">ダブルクリックして**PlaySpaceManager.cs** Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="7beef-287">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="7beef-288">PlaySpaceManager.cs には、アプリケーション固有のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7beef-288">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="7beef-289">機能は、次の動作を有効にするには、このスクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="7beef-289">We will add functionality to this script to enable the following behavior:</span></span>
1. <span data-ttu-id="7beef-290">スキャンの時間制限 (10 秒) を超えた後空間マッピング データの収集を停止します。</span><span class="sxs-lookup"><span data-stu-id="7beef-290">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="7beef-291">空間マッピング データを処理します。</span><span class="sxs-lookup"><span data-stu-id="7beef-291">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="7beef-292">平面 (壁、フロア、シーリングなど) として、世界中の単純な表現を作成するのにには、SurfaceMeshesToPlanes を使用します。</span><span class="sxs-lookup"><span data-stu-id="7beef-292">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="7beef-293">RemoveSurfaceVertices を使用すると、面の境界内にある表面の三角形を削除します。</span><span class="sxs-lookup"><span data-stu-id="7beef-293">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="7beef-294">世界でホログラムのコレクションを生成し、ユーザーに近い壁面と床面の平面上に配置します。</span><span class="sxs-lookup"><span data-stu-id="7beef-294">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="7beef-295">PlaySpaceManager.cs でマークされているコーディングの練習を完了またはスクリプトを次の完成版ソリューションを置き換え。</span><span class="sxs-lookup"><span data-stu-id="7beef-295">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

<span data-ttu-id="7beef-296">**構築し、デプロイ**</span><span class="sxs-lookup"><span data-stu-id="7beef-296">**Build and Deploy**</span></span>
* <span data-ttu-id="7beef-297">キーを押して、HoloLens、展開する前に、**再生**再生モードに切り替わる Unity でボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7beef-297">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="7beef-298">ルーム メッシュがファイルから読み込まれた後は、空間マッピング メッシュで処理を開始する前に 10 秒間待機します。</span><span class="sxs-lookup"><span data-stu-id="7beef-298">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="7beef-299">処理が完了したら、面は床、壁、ceiling などを表す表示されます。</span><span class="sxs-lookup"><span data-stu-id="7beef-299">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="7beef-300">結局、平面の発見された、太陽系の床面のカメラの近くのテーブルに表示されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="7beef-300">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="7beef-301">2 つのポスターがすぎるの壁、カメラの近くに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7beef-301">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="7beef-302">切り替えて、**シーン**タブに表示されない場合**ゲーム**モード。</span><span class="sxs-lookup"><span data-stu-id="7beef-302">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="7beef-303">キーを押して、**再生**再生モードを終了するには、もう一度ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7beef-303">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="7beef-304">構築し、通常どおり、HoloLens にデプロイします。</span><span class="sxs-lookup"><span data-stu-id="7beef-304">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="7beef-305">スキャンおよび完了する空間のマッピング データの処理を待ちます。</span><span class="sxs-lookup"><span data-stu-id="7beef-305">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="7beef-306">平面が表示されたら、世界では、太陽系とポスターを見つけようとします。</span><span class="sxs-lookup"><span data-stu-id="7beef-306">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="7beef-307">第 4 章 - 配置</span><span class="sxs-lookup"><span data-stu-id="7beef-307">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="7beef-308">**目標**</span><span class="sxs-lookup"><span data-stu-id="7beef-308">**Objectives**</span></span>
* <span data-ttu-id="7beef-309">ホログラムがサーフェイス上に収まるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="7beef-309">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="7beef-310">ホログラムを画面に収まるできる/できない場合は、ユーザーにフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="7beef-310">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="7beef-311">**手順**</span><span class="sxs-lookup"><span data-stu-id="7beef-311">**Instructions**</span></span>
* <span data-ttu-id="7beef-312">Unity の**階層**パネルで、 **SpatialProcessing**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7beef-312">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="7beef-313">**インスペクター**パネルで、検索、**平面に表面メッシュ (スクリプト)** コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="7beef-313">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="7beef-314">変更、**描画面**プロパティを**Nothing**選択を解除します。</span><span class="sxs-lookup"><span data-stu-id="7beef-314">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="7beef-315">変更、**描画面**プロパティを**壁**、壁平面のみが表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="7beef-315">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="7beef-316">**プロジェクト**パネル、**スクリプト**フォルダーをダブルクリックして、 **Placeable.cs** Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="7beef-316">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="7beef-317">**Placeable**スクリプトは、平面の検索が完了した後に作成されるポスターとプロジェクションのボックスに既にアタッチされています。</span><span class="sxs-lookup"><span data-stu-id="7beef-317">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="7beef-318">すべてを行う必要がありますが、いくつかのコードをコメント解除し、このスクリプトは、以下を実現します。</span><span class="sxs-lookup"><span data-stu-id="7beef-318">All we need to do is uncomment some code, and this script will achieve the following:</span></span>
1. <span data-ttu-id="7beef-319">ホログラムが中心境界のキューブの 4 つの角からレイキャストによって、サーフェイス上に収まるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="7beef-319">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="7beef-320">サーフェスの法線でフラッシュ待つホログラムの十分な滑らかな判断を確認してください。</span><span class="sxs-lookup"><span data-stu-id="7beef-320">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="7beef-321">境界の周囲に配置されている中には、実際のサイズを表示するホログラム キューブを表示します。</span><span class="sxs-lookup"><span data-stu-id="7beef-321">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="7beef-322">シャドウ/背後の下に floor/壁に配置される場所を表示するホログラムをキャストします。</span><span class="sxs-lookup"><span data-stu-id="7beef-322">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="7beef-323">可能な場合、画面、または緑にホログラムを配置できませんがある場合は、赤、として影をレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="7beef-323">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="7beef-324">アフィニティを使用している画面の種類 (水平または垂直) と連携させるホログラムの向きを変更します。</span><span class="sxs-lookup"><span data-stu-id="7beef-324">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="7beef-325">ジャンプまたはスナップ動作を回避するために選択した画面で、ホログラムがスムーズに配置します。</span><span class="sxs-lookup"><span data-stu-id="7beef-325">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="7beef-326">コーディングの練習を下のすべてのコードのコメントを解除またはで完了したこのソリューションを使用して、 **Placeable.cs**:</span><span class="sxs-lookup"><span data-stu-id="7beef-326">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

<span data-ttu-id="7beef-327">**構築し、デプロイ**</span><span class="sxs-lookup"><span data-stu-id="7beef-327">**Build and Deploy**</span></span>
* <span data-ttu-id="7beef-328">同様に、プロジェクトをビルドし、HoloLens を展開します。</span><span class="sxs-lookup"><span data-stu-id="7beef-328">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="7beef-329">スキャンおよび完了する空間のマッピング データの処理を待ちます。</span><span class="sxs-lookup"><span data-stu-id="7beef-329">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="7beef-330">太陽系を確認したら、下にある投影ボックス見つめます、周囲に移動して選択ジェスチャを実行します。</span><span class="sxs-lookup"><span data-stu-id="7beef-330">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="7beef-331">プロジェクション ボックスを選択したら、外接するキューブは、プロジェクション ボックス表示にされます。</span><span class="sxs-lookup"><span data-stu-id="7beef-331">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="7beef-332">部屋に別の場所を見つめますにヘッドを移動します。</span><span class="sxs-lookup"><span data-stu-id="7beef-332">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="7beef-333">プロジェクションのボックスは、視線の先で従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="7beef-333">The projection box should follow your gaze.</span></span> <span data-ttu-id="7beef-334">プロジェクションのボックスの下の影が赤に変わり場合、は、その画面でホログラムを配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="7beef-334">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="7beef-335">プロジェクションのボックスの下の影が緑色に変わり場合、は、もう 1 つ選択ジェスチャを実行することによって、ホログラムを配置できます。</span><span class="sxs-lookup"><span data-stu-id="7beef-335">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="7beef-336">検索し、新しい場所に移動する壁 holographic のポスターのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="7beef-336">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="7beef-337">Floor、ceiling のポスターを配置することはできず、ラベルを保持する各壁を正しい方向を移動するように注意してください。</span><span class="sxs-lookup"><span data-stu-id="7beef-337">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="7beef-338">第 5 章 - 重なり</span><span class="sxs-lookup"><span data-stu-id="7beef-338">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="7beef-339">**目標**</span><span class="sxs-lookup"><span data-stu-id="7beef-339">**Objectives**</span></span>
* <span data-ttu-id="7beef-340">ホログラムが空間マッピング メッシュによってオクルー ジョンかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="7beef-340">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="7beef-341">楽しいを実現するために異なるオクルー ジョン手法を適用効果。</span><span class="sxs-lookup"><span data-stu-id="7beef-341">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="7beef-342">**手順**</span><span class="sxs-lookup"><span data-stu-id="7beef-342">**Instructions**</span></span>

<span data-ttu-id="7beef-343">最初に、ここでは現実の世界を occluding せず他ホログラムがメッシュの空間マッピングを許可します。</span><span class="sxs-lookup"><span data-stu-id="7beef-343">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>
* <span data-ttu-id="7beef-344">**階層**パネルで、 **SpatialProcessing**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7beef-344">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="7beef-345">**インスペクター**パネルで、検索、**プレイ領域マネージャー (スクリプト)** コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="7beef-345">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="7beef-346">右側に円をクリックして、**セカンダリ マテリアル**プロパティ。</span><span class="sxs-lookup"><span data-stu-id="7beef-346">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="7beef-347">検索し、選択、**オクルー ジョン**マテリアルと、ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7beef-347">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="7beef-348">次に、ここ、地球に特別な動作を追加する (sun) などの別のホログラムまたは空間マッピング メッシュ、オクルー ジョンなるたびに青い枠があるようにします。</span><span class="sxs-lookup"><span data-stu-id="7beef-348">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>
* <span data-ttu-id="7beef-349">**プロジェクト** パネルで、**ホログラム**フォルダー、展開、 **SolarSystem**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7beef-349">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="7beef-350">をクリックして**地球**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-350">Click on **Earth**.</span></span>
* <span data-ttu-id="7beef-351">**インスペクター**パネルで、地球の資料 (下部にあるコンポーネント)。</span><span class="sxs-lookup"><span data-stu-id="7beef-351">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="7beef-352">**シェーダー ドロップダウン**、シェーダーを変更**カスタム > OcclusionRim**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-352">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="7beef-353">地球の周りの青の強調表示は、別のオブジェクトによってオクルー ジョンはそのたびにこのレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="7beef-353">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="7beef-354">最後に、ここ、太陽系惑星の x 線画像視覚効果を有効にします。</span><span class="sxs-lookup"><span data-stu-id="7beef-354">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="7beef-355">編集する必要があります。 **PlanetOcclusion.cs** (Scripts\SolarSystem フォルダーにある)、次を実現するには。</span><span class="sxs-lookup"><span data-stu-id="7beef-355">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>
1. <span data-ttu-id="7beef-356">惑星が SpatialMapping レイヤー (ルーム メッシュと平面) によってオクルー ジョンかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="7beef-356">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="7beef-357">SpatialMapping レイヤーによってオクルー ジョンはそのたびに、惑星のワイヤー フレームの表現を表示します。</span><span class="sxs-lookup"><span data-stu-id="7beef-357">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="7beef-358">SpatialMapping 層によってブロックされていない場合は、惑星のワイヤー フレームの表現を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="7beef-358">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="7beef-359">PlanetOcclusion.cs でコーディングの練習に従うか、次のソリューションを使用します。</span><span class="sxs-lookup"><span data-stu-id="7beef-359">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

<span data-ttu-id="7beef-360">**構築し、デプロイ**</span><span class="sxs-lookup"><span data-stu-id="7beef-360">**Build and Deploy**</span></span>
* <span data-ttu-id="7beef-361">ビルドし、通常どおり、HoloLens をアプリケーションに展開します。</span><span class="sxs-lookup"><span data-stu-id="7beef-361">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="7beef-362">スキャンが完了する空間のマッピング データの処理を待機 (壁に表示される青い線が表示されます)。</span><span class="sxs-lookup"><span data-stu-id="7beef-362">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="7beef-363">太陽系の投影のボックスをオンにし、壁の横にある、またはカウンターの背後にあるボックスを設定します。</span><span class="sxs-lookup"><span data-stu-id="7beef-363">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="7beef-364">基本の重なりは、ポスターまたはプロジェクションのボックスにピアリングするサーフェスの背後にある非表示を表示できます。</span><span class="sxs-lookup"><span data-stu-id="7beef-364">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="7beef-365">地球を探して、別のホログラムまたは画面に移動するたびに、青の強調表示効果にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7beef-365">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="7beef-366">壁または部屋に他の面の背後にある惑星の移動を観察します。</span><span class="sxs-lookup"><span data-stu-id="7beef-366">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="7beef-367">X 線画像ビジョンなり、ワイヤー フレームのスケルトンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7beef-367">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="7beef-368">最後です</span><span class="sxs-lookup"><span data-stu-id="7beef-368">The End</span></span>

<span data-ttu-id="7beef-369">これで終了です。</span><span class="sxs-lookup"><span data-stu-id="7beef-369">Congratulations!</span></span> <span data-ttu-id="7beef-370">完了したので**MR 空間 230。空間マッピング**します。</span><span class="sxs-lookup"><span data-stu-id="7beef-370">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>
* <span data-ttu-id="7beef-371">Unity 環境と負荷の空間のマッピング、データをスキャンする方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="7beef-371">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="7beef-372">シェーダーとマテリアルを使用して、再世界を視覚化する方法の基本を理解します。</span><span class="sxs-lookup"><span data-stu-id="7beef-372">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="7beef-373">平面を検索およびメッシュから三角形を削除するための新しい処理手法の学習しました。</span><span class="sxs-lookup"><span data-stu-id="7beef-373">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="7beef-374">移動し、理にかなっているサーフェイスにホログラムを配置できました。</span><span class="sxs-lookup"><span data-stu-id="7beef-374">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="7beef-375">異なるオクルー ジョン手法が発生し、x 線画像のビジョンの電源が利用されています!</span><span class="sxs-lookup"><span data-stu-id="7beef-375">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>
