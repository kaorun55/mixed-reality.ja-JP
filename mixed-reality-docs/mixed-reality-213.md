---
title: MR 入力 213
description: アニメーション コント ローラーの詳細については、Unity、Visual Studio およびイマーシブ ヘッドセットを使用してこのコーディング チュートリアルに従ってください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity のイマーシブなアニメーション コント ローラー、academy, チュートリアル
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604701"
---
>[!NOTE]
><span data-ttu-id="fda12-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fda12-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="fda12-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="fda12-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="fda12-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="fda12-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="fda12-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="fda12-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="fda12-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="fda12-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="fda12-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="fda12-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="fda12-110">MR 入力 213:アニメーション コント ローラー</span><span class="sxs-lookup"><span data-stu-id="fda12-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="fda12-111">複合現実の世界でのモーション コント ローラーは、別のレベルの対話機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="fda12-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="fda12-112">[コント ローラーのモーション](motion-controllers.md)、私たちできます直接オブジェクトで実際には、物理操作のようなより自然な方法で immersion を増やすと対話、アプリのエクスペリエンスに喜びを感じています。</span><span class="sxs-lookup"><span data-stu-id="fda12-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="fda12-113">MR 入力 213 では、アニメーション コント ローラーの入力イベントをについて説明を単純な空間ペイント エクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fda12-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="fda12-114">このアプリでは、ユーザーは、さまざまな種類のブラシと色の 3 次元空間で描画できます。</span><span class="sxs-lookup"><span data-stu-id="fda12-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="fda12-115">このチュートリアルで説明したトピック</span><span class="sxs-lookup"><span data-stu-id="fda12-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 トピック 2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="fda12-119">**コント ローラーの視覚化**</span><span class="sxs-lookup"><span data-stu-id="fda12-119">**Controller visualization**</span></span>|<span data-ttu-id="fda12-120">**コント ローラーの入力イベント**</span><span class="sxs-lookup"><span data-stu-id="fda12-120">**Controller input events**</span></span>|<span data-ttu-id="fda12-121">**カスタム コント ローラーと UI**</span><span class="sxs-lookup"><span data-stu-id="fda12-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="fda12-122">Unity のゲーム モードとランタイムの motion コント ローラー モデルをレンダリングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fda12-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="fda12-123">さまざまな種類のボタン イベントとそのアプリケーションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fda12-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="fda12-124">コント ローラー上に UI 要素を重ね合わせる、または完全にカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fda12-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="fda12-125">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="fda12-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="fda12-126">コース</span><span class="sxs-lookup"><span data-stu-id="fda12-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="fda12-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="fda12-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="fda12-128"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="fda12-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="fda12-129">MR 入力 213:アニメーション コント ローラー</span><span class="sxs-lookup"><span data-stu-id="fda12-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="fda12-130">✔️</span><span class="sxs-lookup"><span data-stu-id="fda12-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="fda12-131">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="fda12-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="fda12-132">前提条件</span><span class="sxs-lookup"><span data-stu-id="fda12-132">Prerequisites</span></span>

<span data-ttu-id="fda12-133">イマーシブ ヘッドセットのインストールのチェックリストを参照してください[このページ](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="fda12-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="fda12-134">このチュートリアルが必要です[Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="fda12-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="fda12-135">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="fda12-135">Project files</span></span>

* <span data-ttu-id="fda12-136">[ファイルをダウンロード](https://github.com/Microsoft/MixedReality213/archive/master.zip)プロジェクトに必要し、デスクトップにファイルを抽出します。</span><span class="sxs-lookup"><span data-stu-id="fda12-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="fda12-137">をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/MixedReality213)します。</span><span class="sxs-lookup"><span data-stu-id="fda12-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="fda12-138">Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="fda12-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="fda12-139">目標</span><span class="sxs-lookup"><span data-stu-id="fda12-139">Objectives</span></span>

* <span data-ttu-id="fda12-140">Windows for Mixed Reality の Unity 開発を最適化します。</span><span class="sxs-lookup"><span data-stu-id="fda12-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="fda12-141">複合現実のカメラをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="fda12-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="fda12-142">環境のセットアップ</span><span class="sxs-lookup"><span data-stu-id="fda12-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="fda12-143">手順</span><span class="sxs-lookup"><span data-stu-id="fda12-143">Instructions</span></span>

* <span data-ttu-id="fda12-144">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="fda12-144">Start Unity.</span></span>
* <span data-ttu-id="fda12-145">**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fda12-145">Select **Open**.</span></span>
* <span data-ttu-id="fda12-146">デスクトップおよび検索に移動し、 **MixedReality213 マスター**フォルダーの以前にアーカイブ解除します。</span><span class="sxs-lookup"><span data-stu-id="fda12-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="fda12-147">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda12-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="fda12-148">Unity では、プロジェクト ファイルの読み込みが完了すると、Unity エディターを表示できなきます。</span><span class="sxs-lookup"><span data-stu-id="fda12-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="fda12-149">Unity では、次のように選択します。**ファイル > Build Settings**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="fda12-151">選択**ユニバーサル Windows プラットフォーム**で、**プラットフォーム**を一覧表示し、をクリックして、**スイッチ プラットフォーム**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda12-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="fda12-152">ターゲット デバイスを設定**任意のデバイス**</span><span class="sxs-lookup"><span data-stu-id="fda12-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="fda12-153">ビルドの種類を設定**D3D**</span><span class="sxs-lookup"><span data-stu-id="fda12-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="fda12-154">SDK を設定**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="fda12-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="fda12-155">確認**UnityC#プロジェクト**</span><span class="sxs-lookup"><span data-stu-id="fda12-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="fda12-156">これにより、Unity プロジェクトをリビルドすることがなく、Visual Studio プロジェクト内のスクリプト ファイルを変更できます。</span><span class="sxs-lookup"><span data-stu-id="fda12-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="fda12-157">クリックして**プレーヤー設定**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="fda12-158">**インスペクター**パネルで、一番下までスクロール</span><span class="sxs-lookup"><span data-stu-id="fda12-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="fda12-159">XR の設定で確認**仮想現実のサポート**</span><span class="sxs-lookup"><span data-stu-id="fda12-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="fda12-160">仮想現実 Sdk では、次のように選択します**Windows Mixed Reality。**</span><span class="sxs-lookup"><span data-stu-id="fda12-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="fda12-162">閉じる**Build Settings**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="fda12-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="fda12-163">プロジェクトの構造</span><span class="sxs-lookup"><span data-stu-id="fda12-163">Project structure</span></span>

<span data-ttu-id="fda12-164">このチュートリアルでは **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** します。</span><span class="sxs-lookup"><span data-stu-id="fda12-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="fda12-165">リリースを確認できます[このページ](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)します。</span><span class="sxs-lookup"><span data-stu-id="fda12-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![構造](images/mr213-projectstructure-650px.png)

<span data-ttu-id="fda12-167">**参照用の完成したシーン**</span><span class="sxs-lookup"><span data-stu-id="fda12-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="fda12-168">下の 2 つの完成した Unity シーンが見つかります**シーン**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="fda12-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="fda12-169">**MixedReality213**:1 つのブラシで完了したシーン</span><span class="sxs-lookup"><span data-stu-id="fda12-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="fda12-170">**MixedReality213Advanced**:複数のブラシで高度なデザインにシーンが完了しました</span><span class="sxs-lookup"><span data-stu-id="fda12-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="fda12-171">**このチュートリアル用に新しいシーン設定**</span><span class="sxs-lookup"><span data-stu-id="fda12-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="fda12-172">Unity では、次のようにクリックします**ファイル > 新しいシーン。**</span><span class="sxs-lookup"><span data-stu-id="fda12-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="fda12-173">削除**メイン カメラ**と**指向性光**</span><span class="sxs-lookup"><span data-stu-id="fda12-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="fda12-174">**プロジェクト パネル**し、検索に次のプレハブをドラッグ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="fda12-175">資産/HoloToolkit/入力/プレハブ/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="fda12-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="fda12-176">資産/AppPrefabs/**環境**</span><span class="sxs-lookup"><span data-stu-id="fda12-176">Assets/AppPrefabs/**Environment**</span></span>

![カメラと環境](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="fda12-178">Mixed Reality toolkit カメラ プレハブを 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="fda12-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="fda12-179">**MixedRealityCamera.prefab**:カメラのみ</span><span class="sxs-lookup"><span data-stu-id="fda12-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="fda12-180">**MixedRealityCameraParent.prefab**:カメラ + Teleportation 境界</span><span class="sxs-lookup"><span data-stu-id="fda12-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="fda12-181">このチュートリアルでは使用**MixedRealityCamera** teleportation 機能なし。</span><span class="sxs-lookup"><span data-stu-id="fda12-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="fda12-182">このため、単純な追加**環境**プレハブを根拠と感じるユーザーを作成する基本的な床面が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fda12-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="fda12-183">詳細と teleportation については**MixedRealityCameraParent**を参照してください[設計 - Teleportation と locomotion の詳細](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="fda12-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="fda12-184">**スカイ ボックスのセットアップ**</span><span class="sxs-lookup"><span data-stu-id="fda12-184">**Skybox setup**</span></span>
* <span data-ttu-id="fda12-185">クリックして**ウィンドウ > 照明 > の設定**</span><span class="sxs-lookup"><span data-stu-id="fda12-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="fda12-186">右側にある円をクリックして、**スカイ ボックス素材フィールド**</span><span class="sxs-lookup"><span data-stu-id="fda12-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="fda12-187">'灰色' で入力し、選択**SkyboxGray**</span><span class="sxs-lookup"><span data-stu-id="fda12-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="fda12-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span><span class="sxs-lookup"><span data-stu-id="fda12-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![スカイ ボックスの設定](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="fda12-190">確認**スカイ ボックス**オプションを表示するのには、グレーのグラデーション スカイ ボックスを割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="fda12-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![トグル スカイ ボックスのオプション](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="fda12-192">MixedRealityCamera、環境、および灰色のスカイ ボックスのシーンは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fda12-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![MixedReality213 環境](images/mr213-environment-600px.jpg)
* <span data-ttu-id="fda12-194">クリックして**ファイル > としてシーンを保存**</span><span class="sxs-lookup"><span data-stu-id="fda12-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="fda12-195">**保存**任意の名前とシーンのフォルダーの下、シーン</span><span class="sxs-lookup"><span data-stu-id="fda12-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="fda12-196">第 1 章 - コント ローラーの視覚化</span><span class="sxs-lookup"><span data-stu-id="fda12-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="fda12-197">目標</span><span class="sxs-lookup"><span data-stu-id="fda12-197">Objectives</span></span>

* <span data-ttu-id="fda12-198">コント ローラー モデルおよび実行時の Unity のゲーム モードのアニメーションをレンダリングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fda12-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="fda12-199">Windows Mixed Reality は、コント ローラーの視覚エフェクトのアニメーション コント ローラー モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="fda12-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="fda12-200">これには、アプリにコント ローラーの視覚エフェクトに対して実行できるいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="fda12-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="fda12-201">既定値は変更しなくても既定のコント ローラーを使用します。</span><span class="sxs-lookup"><span data-stu-id="fda12-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="fda12-202">既定のコント ローラーを使用して、その要素の一部をカスタマイズする UI コンポーネントを重ねて表示したり、ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="fda12-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="fda12-203">置換 - 独自を使用して、コント ローラーの 3D モデルをカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="fda12-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="fda12-204">この章でこれらのコント ローラーのカスタマイズの例について説明します。</span><span class="sxs-lookup"><span data-stu-id="fda12-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="fda12-205">手順</span><span class="sxs-lookup"><span data-stu-id="fda12-205">Instructions</span></span>

* <span data-ttu-id="fda12-206">**プロジェクト**入力パネルで、 **MotionControllers**検索ボックスにします。</span><span class="sxs-lookup"><span data-stu-id="fda12-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="fda12-207">資産/HoloToolkit/入力/プレハブの下で検索することもできます/。</span><span class="sxs-lookup"><span data-stu-id="fda12-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="fda12-208">ドラッグ、 **MotionControllers**にプレハブ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fda12-209">をクリックして、 **MotionControllers**のプレハブ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="fda12-210">**MotionControllers プレハブ**</span><span class="sxs-lookup"><span data-stu-id="fda12-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="fda12-211">**MotionControllers**プレハブは、 **MotionControllerVisualizer**スロットを代わりのコント ローラー モデルを提供するスクリプト。</span><span class="sxs-lookup"><span data-stu-id="fda12-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="fda12-212">手の形や剣などお客様独自のカスタムの 3D モデルを割り当て、常に使用して代替左/右のモデル ' を確認して場合、は、既定のモデルではなく表示されます。</span><span class="sxs-lookup"><span data-stu-id="fda12-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="fda12-213">ブラシを使用して、コント ローラー モデルを置換するのに第 4 章では、このスロットを使用します。</span><span class="sxs-lookup"><span data-stu-id="fda12-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="fda12-215">**手順**</span><span class="sxs-lookup"><span data-stu-id="fda12-215">**Instructions**</span></span>
* <span data-ttu-id="fda12-216">**インスペクター**パネルをダブルクリックして**MotionControllerVisualizer** Visual Studio でコードを表示するスクリプト</span><span class="sxs-lookup"><span data-stu-id="fda12-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="fda12-217">**MotionControllerVisualizer スクリプト**</span><span class="sxs-lookup"><span data-stu-id="fda12-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="fda12-218">**MotionControllerVisualizer**と**MotionControllerInfo**クラスへのアクセスし、既定のコント ローラー モデルを変更するための手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="fda12-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="fda12-219">**MotionControllerVisualizer**をサブスクライブする Unity の**InteractionSourceDetected**イベントが見つかったときに、コント ローラー モデルを自動的にインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="fda12-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="fda12-220">コント ローラー モデルに従って配信[glTF 仕様](https://github.com/KhronosGroup/glTF)します。</span><span class="sxs-lookup"><span data-stu-id="fda12-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="fda12-221">送信および 3D アセットをアンパックの背後にあるプロセスを向上させながら、一般的な形式を提供するは、この形式が用意されています。</span><span class="sxs-lookup"><span data-stu-id="fda12-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="fda12-222">この場合を取得し、ユーザーのエクスペリエンスを可能な限りシームレスにようにするため、アニメーション コント ローラーのバージョン、ユーザーは使用する場合がありますとは限りません時に、コント ローラー モデルを読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="fda12-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="fda12-223">このコースでは、混合の現実 Toolkit を使用して、Khronos グループのバージョンを使用する[UnityGLTF プロジェクト](https://github.com/KhronosGroup/UnityGLTF)します。</span><span class="sxs-lookup"><span data-stu-id="fda12-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="fda12-224">スクリプトで使用できるコント ローラーが配信されると**MotionControllerInfo**自体位置は正しくできるように特定のコント ローラーの要素の変換が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="fda12-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="fda12-225">後の章では、これらのスクリプトを使用して、コント ローラーに UI 要素をアタッチする方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="fda12-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="fda12-226">*いくつかのスクリプトでは、コードのブロックを紹介します **#if!UNITY_EDITOR**または**UNITY_WSA**します。これらのコード ブロックは、Windows を展開するときに、UWP ランタイムのみで実行します。これは、Unity エディターと、UWP アプリのランタイムで使用される Api のセットが異なるためです。*</span><span class="sxs-lookup"><span data-stu-id="fda12-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="fda12-227">**保存**シーンとクリック、**再生**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda12-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="fda12-228">ヘッドセット内のモーション コント ローラーとシーンを表示できます。</span><span class="sxs-lookup"><span data-stu-id="fda12-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="fda12-229">ボタンのクリック、スティックの移動、およびタッチパッド タッチの強調表示の詳細なアニメーションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="fda12-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller 視覚エフェクトの既定値](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="fda12-231">第 2 章 – コント ローラーへの UI 要素</span><span class="sxs-lookup"><span data-stu-id="fda12-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="fda12-232">目標</span><span class="sxs-lookup"><span data-stu-id="fda12-232">Objectives</span></span>

* <span data-ttu-id="fda12-233">アニメーション コント ローラーの要素について説明します</span><span class="sxs-lookup"><span data-stu-id="fda12-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="fda12-234">オブジェクトのコント ローラーの特定の部分にアタッチする方法について説明します</span><span class="sxs-lookup"><span data-stu-id="fda12-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="fda12-235">この章では、ユーザーは簡単にアクセスし、いつでも操作コント ローラーにユーザー インターフェイス要素を追加する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="fda12-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="fda12-236">単純なカラー ピッカー入力タッチパッドを使用して UI を追加する方法も学習します。</span><span class="sxs-lookup"><span data-stu-id="fda12-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="fda12-237">手順</span><span class="sxs-lookup"><span data-stu-id="fda12-237">Instructions</span></span>

* <span data-ttu-id="fda12-238">**プロジェクト**パネルで、検索**MotionControllerInfo**スクリプト。</span><span class="sxs-lookup"><span data-stu-id="fda12-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="fda12-239">検索結果からダブル クリックして**MotionControllerInfo**スクリプトを Visual Studio でコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fda12-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="fda12-240">**MotionControllerInfo script**</span><span class="sxs-lookup"><span data-stu-id="fda12-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="fda12-241">最初の手順では、コント ローラーの要素にアタッチする UI をするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="fda12-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="fda12-242">これらの要素が定義されている**ControllerElementEnum**で**MotionControllerInfo.cs**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="fda12-244">**ホーム**</span><span class="sxs-lookup"><span data-stu-id="fda12-244">**Home**</span></span>
* <span data-ttu-id="fda12-245">**メニュー**</span><span class="sxs-lookup"><span data-stu-id="fda12-245">**Menu**</span></span>
* <span data-ttu-id="fda12-246">**理解**</span><span class="sxs-lookup"><span data-stu-id="fda12-246">**Grasp**</span></span>
* <span data-ttu-id="fda12-247">**スティック**</span><span class="sxs-lookup"><span data-stu-id="fda12-247">**Thumbstick**</span></span>
* <span data-ttu-id="fda12-248">**Select**</span><span class="sxs-lookup"><span data-stu-id="fda12-248">**Select**</span></span>
* <span data-ttu-id="fda12-249">**タッチパッド**</span><span class="sxs-lookup"><span data-stu-id="fda12-249">**Touchpad**</span></span>
* <span data-ttu-id="fda12-250">**ポインティングの姿勢**: この要素は、順方向を指すコント ローラーの先端を表します。</span><span class="sxs-lookup"><span data-stu-id="fda12-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="fda12-251">**手順**</span><span class="sxs-lookup"><span data-stu-id="fda12-251">**Instructions**</span></span>
* <span data-ttu-id="fda12-252">**プロジェクト**パネルで、検索**AttachToController**スクリプト。</span><span class="sxs-lookup"><span data-stu-id="fda12-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="fda12-253">検索結果からダブル クリックして**AttachToController**スクリプトを Visual Studio でコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fda12-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="fda12-254">**AttachToController スクリプト**</span><span class="sxs-lookup"><span data-stu-id="fda12-254">**AttachToController script**</span></span>

<span data-ttu-id="fda12-255">**AttachToController**スクリプトが指定されたコント ローラーの処理および要素をすべてのオブジェクトをアタッチする簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="fda12-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="fda12-256">In **AttachElementToController()**,</span><span class="sxs-lookup"><span data-stu-id="fda12-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="fda12-257">処理を使用して確認**MotionControllerInfo.Handedness**</span><span class="sxs-lookup"><span data-stu-id="fda12-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="fda12-258">コント ローラーを使用して、特定の要素を取得**MotionControllerInfo.TryGetElement()**</span><span class="sxs-lookup"><span data-stu-id="fda12-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="fda12-259">要素を取得した後、コント ローラー モデル、その下にあるオブジェクトの親から変換し、オブジェクトのローカルの位置と回転は 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="fda12-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

<span data-ttu-id="fda12-260">使用する最も簡単な方法は、 **AttachToController**の場合と、そこから継承するようにスクリプトは**ColorPickerWheel します。**</span><span class="sxs-lookup"><span data-stu-id="fda12-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="fda12-261">オーバーライドするだけで、 **OnAttachToController**と**OnDetatchFromController**セットアップを実行する関数//コント ローラーが検出されました。 切断されたときにブレーク ダウンします。</span><span class="sxs-lookup"><span data-stu-id="fda12-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="fda12-262">**手順**</span><span class="sxs-lookup"><span data-stu-id="fda12-262">**Instructions**</span></span>
* <span data-ttu-id="fda12-263">**プロジェクト**パネルで、検索ボックスに入力**ColorPickerWheel**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="fda12-264">資産/AppPrefabs で検索することもできます/。</span><span class="sxs-lookup"><span data-stu-id="fda12-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="fda12-265">ドラッグ**ColorPickerWheel**にプレハブ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fda12-266">をクリックして、 **ColorPickerWheel**のプレハブ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fda12-267">**インスペクター**パネルをダブルクリックして**ColorPickerWheel**スクリプトを Visual Studio でコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fda12-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel プレハブ](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="fda12-269">**ColorPickerWheel スクリプト**</span><span class="sxs-lookup"><span data-stu-id="fda12-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="fda12-270">**ColorPickerWheel**継承**AttachToController**、表示**処理**と**要素**で、 **Inspector**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="fda12-271">アタッチ、UI、左側のコント ローラーのタッチパッド要素にします。</span><span class="sxs-lookup"><span data-stu-id="fda12-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![ColorPickerWheel スクリプト](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="fda12-273">**ColorPickerWheel**オーバーライド、 **OnAttachToController**と**OnDetatchFromController**と色の選択の次の章で使用される入力イベントをサブスクライブするにはタッチパッドを入力します。</span><span class="sxs-lookup"><span data-stu-id="fda12-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```
* <span data-ttu-id="fda12-274">**保存**シーンとクリック、**再生**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda12-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="fda12-275">**コント ローラーにオブジェクトのアタッチの代替方法**</span><span class="sxs-lookup"><span data-stu-id="fda12-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="fda12-276">スクリプトがから継承することをお勧めします。 **AttachToController**オーバーライドと**OnAttachToController**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="fda12-277">ただし、これができるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="fda12-277">However, this may not always be possible.</span></span> <span data-ttu-id="fda12-278">代わりにでは、スタンドアロン コンポーネントとして使用します。</span><span class="sxs-lookup"><span data-stu-id="fda12-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="fda12-279">これは、スクリプトをリファクタリングすることがなく、コント ローラーを既存のプレハブをアタッチする場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="fda12-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="fda12-280">単に IsAttached に設定するまで待機する、クラスがある任意のセットアップを実行する前に true。</span><span class="sxs-lookup"><span data-stu-id="fda12-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="fda12-281">これを行う最も簡単な方法は、'Start ' のコルーチンを使用して、します。</span><span class="sxs-lookup"><span data-stu-id="fda12-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="fda12-282">第 3 章 - タッチパッドの入力</span><span class="sxs-lookup"><span data-stu-id="fda12-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="fda12-283">目標</span><span class="sxs-lookup"><span data-stu-id="fda12-283">Objectives</span></span>

* <span data-ttu-id="fda12-284">タッチパッド入力データのイベントを取得する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="fda12-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="fda12-285">アプリのエクスペリエンスにタッチパッド軸の位置に関する情報を使用する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="fda12-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="fda12-286">手順</span><span class="sxs-lookup"><span data-stu-id="fda12-286">Instructions</span></span>

* <span data-ttu-id="fda12-287">**階層**パネルで、をクリックして**ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="fda12-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="fda12-288">**インスペクター**パネルの**Animatior**、ダブルクリック**ColorPickerWheelController**</span><span class="sxs-lookup"><span data-stu-id="fda12-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="fda12-289">表示することができます**Animator**タブが開かれます</span><span class="sxs-lookup"><span data-stu-id="fda12-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="fda12-290">**Unity のアニメーション コント ローラーと UI を表示/非表示**</span><span class="sxs-lookup"><span data-stu-id="fda12-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="fda12-291">表示/非表示に、 **ColorPickerWheel**使用してアニメーションを使用して UI、 [Unity のアニメーション システム](https://docs.unity3d.com/Manual/AnimationOverview.html)します。</span><span class="sxs-lookup"><span data-stu-id="fda12-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="fda12-292">設定、 **ColorPickerWheel**の**Visible**プロパティを true または false のトリガー**表示**と**を非表示に**アニメーション トリガーします。</span><span class="sxs-lookup"><span data-stu-id="fda12-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="fda12-293">**表示**と**を非表示に**でパラメーターが定義されている、 **ColorPickerWheelController**アニメーション コント ローラー。</span><span class="sxs-lookup"><span data-stu-id="fda12-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Unity のアニメーション コント ローラー](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="fda12-295">**手順**</span><span class="sxs-lookup"><span data-stu-id="fda12-295">**Instructions**</span></span>
* <span data-ttu-id="fda12-296">**階層**パネルで、 **ColorPickerWheel**プレハブ</span><span class="sxs-lookup"><span data-stu-id="fda12-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="fda12-297">**インスペクター**パネルをダブルクリックして**ColorPickerWheel** Visual Studio でコードを表示するスクリプト</span><span class="sxs-lookup"><span data-stu-id="fda12-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="fda12-298">**ColorPickerWheel スクリプト**</span><span class="sxs-lookup"><span data-stu-id="fda12-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="fda12-299">**ColorPickerWheel**をサブスクライブする Unity の**InteractionSourceUpdated**タッチパッド イベントをリッスンするイベントです。</span><span class="sxs-lookup"><span data-stu-id="fda12-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="fda12-300">**InteractionSourceUpdated()**、ことを確認して、スクリプトが最初に確認します。</span><span class="sxs-lookup"><span data-stu-id="fda12-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="fda12-301">タッチパッド イベントでは実際には、(obj.state **。touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="fda12-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="fda12-302">左側のコント ローラーの発生元 (obj.state.source **。処理**)</span><span class="sxs-lookup"><span data-stu-id="fda12-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="fda12-303">タッチパッドの両方に該当する場合は位置 (obj.state **。touchpadPosition**) に割り当てられている**selectorPosition**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

<span data-ttu-id="fda12-304">**Update()** に基づいて、**表示**プロパティ、カラー ピッカーの animator コンポーネントでの表示と非表示のアニメーション トリガーでトリガーされます</span><span class="sxs-lookup"><span data-stu-id="fda12-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

<span data-ttu-id="fda12-305">**Update()**、 **selectorPosition** UV 位置を返しますカラー ホイールの mesh collider コライダーに伸びる射線をキャストするために使用します。</span><span class="sxs-lookup"><span data-stu-id="fda12-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="fda12-306">この位置は、ピクセル座標を見つけて、色のカラー ホイールのテクスチャの値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fda12-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="fda12-307">この値が他のスクリプトを使用してアクセスできる、 **SelectedColor**プロパティ。</span><span class="sxs-lookup"><span data-stu-id="fda12-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![カラー ピッカーのホイール レイキャスト](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="fda12-309">第 4 章 - コント ローラー モデルをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="fda12-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="fda12-310">目標</span><span class="sxs-lookup"><span data-stu-id="fda12-310">Objectives</span></span>

* <span data-ttu-id="fda12-311">カスタムの 3D モデルとコント ローラー モデルを上書きする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fda12-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="fda12-313">手順</span><span class="sxs-lookup"><span data-stu-id="fda12-313">Instructions</span></span>

* <span data-ttu-id="fda12-314">クリックして**MotionControllers**で、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fda12-315">右側にある円をクリックして、**代替の右側のコント ローラー**フィールド。</span><span class="sxs-lookup"><span data-stu-id="fda12-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="fda12-316">入力 **'BrushController**' し、結果から、プレハブを選択します。</span><span class="sxs-lookup"><span data-stu-id="fda12-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="fda12-317">資産/AppPrefabs 下で見つかります/**BrushController**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="fda12-318">確認**常に別の適切なモデルを使用して、**</span><span class="sxs-lookup"><span data-stu-id="fda12-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="fda12-320">**BrushController**プレハブは対象にする必要はありません、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="fda12-321">ただし、その子コンポーネントを確認します。</span><span class="sxs-lookup"><span data-stu-id="fda12-321">However, to check out its child components:</span></span>
* <span data-ttu-id="fda12-322">**プロジェクト**に入力パネルで、 **BrushController**ドラッグ**BrushController**にプレハブ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="fda12-324">検索は、**ヒント**コンポーネント**BrushController**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="fda12-325">開始/停止の線を描画するのに、変換を使用します。</span><span class="sxs-lookup"><span data-stu-id="fda12-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="fda12-326">削除、 **BrushController**から、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fda12-327">**保存**シーンとクリック、**再生**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda12-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="fda12-328">ブラシ モデルが右側のモーション コント ローラーを交換できるようにします。</span><span class="sxs-lookup"><span data-stu-id="fda12-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="fda12-329">第 5 章「選択の入力による塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="fda12-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="fda12-330">目標</span><span class="sxs-lookup"><span data-stu-id="fda12-330">Objectives</span></span>

* <span data-ttu-id="fda12-331">[選択] ボタンのイベントを使用して開始および線の描画を停止する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="fda12-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="fda12-332">手順</span><span class="sxs-lookup"><span data-stu-id="fda12-332">Instructions</span></span>

* <span data-ttu-id="fda12-333">検索**BrushController**のプレハブ、**プロジェクト**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="fda12-334">**インスペクター**パネルをダブルクリックして**BrushController**スクリプトを Visual Studio でコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fda12-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="fda12-335">**BrushController スクリプト**</span><span class="sxs-lookup"><span data-stu-id="fda12-335">**BrushController script**</span></span>

<span data-ttu-id="fda12-336">**BrushController** InteractionManager のサブスクライブ**InteractionSourcePressed**と**InteractionSourceReleased**イベント。</span><span class="sxs-lookup"><span data-stu-id="fda12-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="fda12-337">ときに**InteractionSourcePressed**イベントがトリガーされると、ブラシの**描画**プロパティがときに true **InteractionSourceReleased**イベントがトリガーされると、ブラシの**描画**プロパティが false に設定します。</span><span class="sxs-lookup"><span data-stu-id="fda12-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

<span data-ttu-id="fda12-338">中に**描画**に設定されている場合は true、ブラシが生成されますポイントをインスタンス化された Unity で**LineRenderer**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="fda12-339">ブラシにこのプレハブへの参照が保持される**ストローク Prefab**フィールド。</span><span class="sxs-lookup"><span data-stu-id="fda12-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

<span data-ttu-id="fda12-340">カラー ピッカー ホイール UI から現在選択されている色を使用する**BrushController**への参照が必要、 **ColorPickerWheel**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fda12-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="fda12-341">**BrushController**プレハブは、交換したコント ローラーとして実行時にインスタンス化、シーン内のオブジェクトへの参照が実行時に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fda12-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="fda12-342">ここで使用**GameObject.FindObjectOfType**を検索する、 **ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="fda12-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```
* <span data-ttu-id="fda12-343">**保存**シーンとクリック、**再生**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda12-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="fda12-344">線の描画し、ペイントの右側のコント ローラーの選択ボタンを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="fda12-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="fda12-345">第 6 章 - は入力オブジェクトの生成での選択</span><span class="sxs-lookup"><span data-stu-id="fda12-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="fda12-346">目標</span><span class="sxs-lookup"><span data-stu-id="fda12-346">Objectives</span></span>

* <span data-ttu-id="fda12-347">選択を使用する方法について説明し、ボタンの入力イベントを把握</span><span class="sxs-lookup"><span data-stu-id="fda12-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="fda12-348">オブジェクトをインスタンス化する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="fda12-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="fda12-349">手順</span><span class="sxs-lookup"><span data-stu-id="fda12-349">Instructions</span></span>

* <span data-ttu-id="fda12-350">**プロジェクト**入力パネルで、 **ObjectSpawner**検索ボックスにします。</span><span class="sxs-lookup"><span data-stu-id="fda12-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="fda12-351">資産/AppPrefabs で検索することもできます/</span><span class="sxs-lookup"><span data-stu-id="fda12-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="fda12-352">ドラッグ、 **ObjectSpawner**にプレハブ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fda12-353">クリックして**ObjectSpawner**で、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fda12-354">**ObjectSpawner**という名前のフィールドを持つ**色ソース**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="fda12-355">**階層**パネルで、ドラッグ、 **ColorPickerWheel**このフィールドへの参照。</span><span class="sxs-lookup"><span data-stu-id="fda12-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![オブジェクトの Spawner インスペクター](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="fda12-357">をクリックして、 **ObjectSpawner**のプレハブ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fda12-358">**インスペクター**パネルをダブルクリックして**ObjectSpawner**スクリプトを Visual Studio でコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fda12-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="fda12-359">**ObjectSpawner スクリプト**</span><span class="sxs-lookup"><span data-stu-id="fda12-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="fda12-360">**ObjectSpawner** (キューブ、球、円柱) プリミティブのメッシュのコピーを領域にインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="fda12-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="fda12-361">ときに、 **InteractionSourcePressed**処理を確認し、かどうかは、検出された、 **InteractionSourcePressType.Grasp**または**InteractionSourcePressType.Select**イベントです。</span><span class="sxs-lookup"><span data-stu-id="fda12-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="fda12-362">**持ち**イベント、現在のメッシュ型 (球体、キューブ、円柱) のインデックスの値が増加</span><span class="sxs-lookup"><span data-stu-id="fda12-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

<span data-ttu-id="fda12-363">**選択**イベントで、 **SpawnObject()**、新しいオブジェクトをインスタンス化された、親が設定されていない、世界中にリリースされました。</span><span class="sxs-lookup"><span data-stu-id="fda12-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="fda12-364">**ObjectSpawner**を使用して、 **ColorPickerWheel**表示オブジェクトの素材の色を設定します。</span><span class="sxs-lookup"><span data-stu-id="fda12-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="fda12-365">生成されたオブジェクトの色が保持されますが、この資料のインスタンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="fda12-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="fda12-366">**保存**シーンとクリック、**再生**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda12-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="fda12-367">理解 ボタンを持つオブジェクトを変更し、選択 ボタンを持つオブジェクトを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="fda12-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="fda12-368">ビルドしてアプリをデプロイする Mixed Reality ポータル</span><span class="sxs-lookup"><span data-stu-id="fda12-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="fda12-369">Unity では、次のように選択します。**ファイル > Build Settings**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="fda12-370">クリックして**開くシーンを追加**を現在のシーンを追加する、 **Scenes In Build**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="fda12-371">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda12-371">Click **Build**.</span></span>
* <span data-ttu-id="fda12-372">作成、**新しいフォルダー** "App"という名前です。</span><span class="sxs-lookup"><span data-stu-id="fda12-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="fda12-373">1 回のクリック、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="fda12-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="fda12-374">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda12-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="fda12-375">Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fda12-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="fda12-376">開く、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="fda12-376">Open the **App** folder.</span></span>
* <span data-ttu-id="fda12-377">ダブルクリック**YourSceneName.sln** Visual Studio ソリューション ファイル。</span><span class="sxs-lookup"><span data-stu-id="fda12-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="fda12-378">デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**X64**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="fda12-379">デバイスのボタンの横にあるドロップダウン矢印をクリックし、**ローカル マシン**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="fda12-380">クリックして**デバッグ]、[デバッグなしで開始**メニューまたはキーを押して**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="fda12-381">これでアプリがビルドし、Mixed Reality ポータルにインストールされています。</span><span class="sxs-lookup"><span data-stu-id="fda12-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="fda12-382">Mixed Reality ポータルで [スタート] メニューをもう一度起動できます。</span><span class="sxs-lookup"><span data-stu-id="fda12-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="fda12-383">高度なデザインのレイアウトとブラシ ツール</span><span class="sxs-lookup"><span data-stu-id="fda12-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="fda12-385">この章では、カスタム ブラシ ツール コレクションで、既定のモーション コント ローラー モデルを置換する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="fda12-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="fda12-386">参照用には、完了したシーンを見つけることができます**MixedReality213Advanced** **シーン**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="fda12-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="fda12-387">手順</span><span class="sxs-lookup"><span data-stu-id="fda12-387">Instructions</span></span>

* <span data-ttu-id="fda12-388">**プロジェクト**入力パネルで、 **BrushSelector**検索ボックスにします。</span><span class="sxs-lookup"><span data-stu-id="fda12-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="fda12-389">資産/AppPrefabs で検索することもできます/</span><span class="sxs-lookup"><span data-stu-id="fda12-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="fda12-390">ドラッグ、 **BrushSelector**にプレハブ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fda12-391">組織の作成と呼ばれる空の GameObject**ブラシ**</span><span class="sxs-lookup"><span data-stu-id="fda12-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="fda12-392">次のプレハブからドラッグして、**プロジェクト**にパネル**ブラシ**</span><span class="sxs-lookup"><span data-stu-id="fda12-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="fda12-393">資産/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="fda12-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="fda12-394">資産/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="fda12-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="fda12-395">資産/AppPrefabs/**消しゴム**</span><span class="sxs-lookup"><span data-stu-id="fda12-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="fda12-396">資産/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="fda12-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="fda12-397">資産/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="fda12-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="fda12-398">資産/AppPrefabs/**鉛筆**</span><span class="sxs-lookup"><span data-stu-id="fda12-398">Assets/AppPrefabs/**Pencil**</span></span>

![ブラシ](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="fda12-400">クリックして**MotionControllers**のプレハブ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fda12-401">**インスペクター**パネルをオフにします**常に代替権限モデルを使用する**上、**アニメーション コント ローラーのビジュアライザー**</span><span class="sxs-lookup"><span data-stu-id="fda12-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="fda12-402">**階層**パネルで、をクリックして**BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="fda12-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="fda12-403">**BrushSelector**という名前のフィールドを持つ**ColorPicker**</span><span class="sxs-lookup"><span data-stu-id="fda12-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="fda12-404">**階層**パネルで、ドラッグ、 **ColorPickerWheel**に**ColorPicker**フィールドに、**インスペクター**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![ブラシのセレクターを ColorPickerWheel を割り当てる](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="fda12-406">**階層**パネルの**BrushSelector**プレハブを選択、**メニュー**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fda12-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="fda12-407">**インスペクター**パネルの**LineObjectCollection**コンポーネント、オープン、**オブジェクト**ドロップダウンの配列。</span><span class="sxs-lookup"><span data-stu-id="fda12-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="fda12-408">6 は空きスロットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fda12-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="fda12-409">**階層**パネルで、各親の下のプレハブのドラッグ、**ブラシ**任意の順序でこれらのスロットに GameObject です。</span><span class="sxs-lookup"><span data-stu-id="fda12-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="fda12-410">(シーン、プロジェクト フォルダーのプレハブから、プレハブをドラッグしていることを確認してください。)</span><span class="sxs-lookup"><span data-stu-id="fda12-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![ブラシのセレクター](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="fda12-412">**BrushSelector プレハブ**</span><span class="sxs-lookup"><span data-stu-id="fda12-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="fda12-413">以降、 **BrushSelector**継承**AttachToController**、表示**処理**と**要素**オプション、 **Inspector**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="fda12-414">選択した**右**と**発生ポイント**順方向で右側にあるコント ローラーにブラシ ツールをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="fda12-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="fda12-415">**BrushSelector**の 2 つのユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="fda12-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="fda12-416">**楕円**: 楕円に沿った空間のポイントを生成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="fda12-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="fda12-417">**LineObjectCollection**: 任意の行クラス (例: 楕円) によって生成されたポイントを使用してオブジェクトを配布します。</span><span class="sxs-lookup"><span data-stu-id="fda12-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="fda12-418">これは、どのような使用する、ブラシに沿って楕円のシェイプを配置します。</span><span class="sxs-lookup"><span data-stu-id="fda12-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="fda12-419">組み合わせて使用すると、放射状メニューを作成するこれらのユーティリティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fda12-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="fda12-420">**LineObjectCollection スクリプト**</span><span class="sxs-lookup"><span data-stu-id="fda12-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="fda12-421">**LineObjectCollection**サイズ、位置の行に分散されていますオブジェクトの回転のコントロールがあります。</span><span class="sxs-lookup"><span data-stu-id="fda12-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="fda12-422">これは、ブラシのセレクターのような放射状のメニューを作成するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="fda12-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="fda12-423">外観を作成するブラシをスケールから近づいた場合は、選択したセンターの位置に何も、 **ObjectScale**オフ、エッジの中央と tapers のピークを曲線します。</span><span class="sxs-lookup"><span data-stu-id="fda12-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="fda12-424">**BrushSelector スクリプト**</span><span class="sxs-lookup"><span data-stu-id="fda12-424">**BrushSelector script**</span></span>

<span data-ttu-id="fda12-425">場合、 **BrushSelector**、手続き型のアニメーションを使用することにしました。</span><span class="sxs-lookup"><span data-stu-id="fda12-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="fda12-426">最初に、ブラシのモデルは、によって楕円で配布、 **LineObjectCollection**スクリプト。</span><span class="sxs-lookup"><span data-stu-id="fda12-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="fda12-427">各ブラシがその位置に基づいて、ユーザーの手の形での保守を担当し、その**DisplayMode**値で、選択内容に基づいて変更します。</span><span class="sxs-lookup"><span data-stu-id="fda12-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="fda12-428">手続き型の方法を選択したユーザーは、ブラシを選択すると、中断されているブラシの位置の遷移の可能性が高くため。</span><span class="sxs-lookup"><span data-stu-id="fda12-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="fda12-429">Mecanim アニメーションでは、中断を正常に処理できますが、単純な Lerp 操作よりも複雑にします。</span><span class="sxs-lookup"><span data-stu-id="fda12-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="fda12-430">**BrushSelector**両方の組み合わせを使用します。</span><span class="sxs-lookup"><span data-stu-id="fda12-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="fda12-431">タッチパッドの入力が検出されると、ブラシ オプションは表示されているようになり、放射状のメニューに沿ったスケール アップします。</span><span class="sxs-lookup"><span data-stu-id="fda12-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="fda12-432">(これは、ユーザーが選択を行うことを示します) タイムアウト期間後に、ブラシのオプションをスケール ダウン、もう一度選択したブラシのみを離れること。</span><span class="sxs-lookup"><span data-stu-id="fda12-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="fda12-433">**タッチパッドの入力を視覚化します。**</span><span class="sxs-lookup"><span data-stu-id="fda12-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="fda12-434">コント ローラー モデルが完全に置き換えられましたいる場合でも元のモデルの入力に入力を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="fda12-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="fda12-435">これにより、実際には、ユーザーのアクションを地上にします。</span><span class="sxs-lookup"><span data-stu-id="fda12-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="fda12-436">**BrushSelector**入力を受け取ったとき、タッチパッドを簡単に表示することにしました。</span><span class="sxs-lookup"><span data-stu-id="fda12-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="fda12-437">カスタム素材には、その素材を置き換えて、コント ローラーからタッチパッド要素を取得することによってこれは、入力を受信した最後の時間タッチパッドに基づいてその素材の色をグラデーションを適用します。</span><span class="sxs-lookup"><span data-stu-id="fda12-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }
            
    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

<span data-ttu-id="fda12-438">**タッチパッドの入力とブラシ ツールの選択**</span><span class="sxs-lookup"><span data-stu-id="fda12-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="fda12-439">タッチパッドの押された入力が検出されると、ブラシのセレクターを左または右がかどうかことを確認する入力の位置を確認します。</span><span class="sxs-lookup"><span data-stu-id="fda12-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="fda12-440">**ストロークの太さを selectPressedAmount**</span><span class="sxs-lookup"><span data-stu-id="fda12-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="fda12-441">代わりに、 **InteractionSourcePressType.Select**内のイベント、 **InteractionSourcePressed()**、押された状態の量をアナログ値を取得する**selectPressedAmount**.</span><span class="sxs-lookup"><span data-stu-id="fda12-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="fda12-442">この値を取得できる**InteractionSourceUpdated()** します。</span><span class="sxs-lookup"><span data-stu-id="fda12-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

<span data-ttu-id="fda12-443">**消しゴム スクリプト**</span><span class="sxs-lookup"><span data-stu-id="fda12-443">**Eraser script**</span></span>

<span data-ttu-id="fda12-444">**消しゴム**は特殊な種類の基本をオーバーライドするブラシ**ブラシ**の**DrawOverTime()** 関数。</span><span class="sxs-lookup"><span data-stu-id="fda12-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="fda12-445">描画が true の場合、消しゴムがそのヒントが、既存のブラシのストロークと交差するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="fda12-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="fda12-446">その場合を圧縮するキューに追加され削除します。</span><span class="sxs-lookup"><span data-stu-id="fda12-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="fda12-447">高度な設計 - Teleportation と locomotion</span><span class="sxs-lookup"><span data-stu-id="fda12-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="fda12-448">Teleportation スティックを使用して、シーン内を移動するには、使用できるようにする場合**MixedRealityCameraParent**の代わりに**MixedRealityCamera**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="fda12-449">追加する必要があります**InputManager**と**DefaultCusor**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="fda12-450">**MixedRealityCameraParent**が既に含まれて**MotionControllers**と**境界**、子コンポーネントとして既存を削除する必要があります**MotionControllers**と**環境**prefab します。</span><span class="sxs-lookup"><span data-stu-id="fda12-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="fda12-451">手順</span><span class="sxs-lookup"><span data-stu-id="fda12-451">Instructions</span></span>

* <span data-ttu-id="fda12-452">**階層**パネルで、削除**MixedRealityCamera**、**環境**と**MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="fda12-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="fda12-453">**プロジェクト パネル**し、検索に次のプレハブをドラッグ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="fda12-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="fda12-454">資産/AppPrefabs/入力/プレハブ/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="fda12-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="fda12-455">資産/AppPrefabs/入力/プレハブ/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="fda12-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="fda12-456">資産/AppPrefabs/入力/プレハブ/カーソル/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="fda12-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![複合現実のカメラの親](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="fda12-458">**階層**パネルで、をクリックして**入力マネージャー**</span><span class="sxs-lookup"><span data-stu-id="fda12-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="fda12-459">**インスペクター**パネルで、下へスクロールして、**単純な 1 つのポインターのセレクター**セクション</span><span class="sxs-lookup"><span data-stu-id="fda12-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="fda12-460">**階層**パネルで、ドラッグ**DefaultCursor**に**カーソル**フィールド</span><span class="sxs-lookup"><span data-stu-id="fda12-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![既定値のカーソルの割り当てください。](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="fda12-462">**保存**シーンとクリック、**再生**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda12-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="fda12-463">左/右またはテレポートを回転するスティックを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="fda12-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="fda12-464">最後です</span><span class="sxs-lookup"><span data-stu-id="fda12-464">The end</span></span>

<span data-ttu-id="fda12-465">このチュートリアルは終わりです。</span><span class="sxs-lookup"><span data-stu-id="fda12-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="fda12-466">学習内容。</span><span class="sxs-lookup"><span data-stu-id="fda12-466">You learned:</span></span>
* <span data-ttu-id="fda12-467">Unity のゲーム モードとランタイムの motion コント ローラー モデルを操作する方法。</span><span class="sxs-lookup"><span data-stu-id="fda12-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="fda12-468">さまざまな種類のボタン イベントとそのアプリケーションを使用する方法。</span><span class="sxs-lookup"><span data-stu-id="fda12-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="fda12-469">コント ローラー上に UI 要素を重ね合わせる、または完全にカスタマイズする方法。</span><span class="sxs-lookup"><span data-stu-id="fda12-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="fda12-470">アニメーション コント ローラーで、独自の没入型エクスペリエンスの作成を開始する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="fda12-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="fda12-471">完了したシーン</span><span class="sxs-lookup"><span data-stu-id="fda12-471">Completed scenes</span></span>

* <span data-ttu-id="fda12-472">Unity の**プロジェクト**パネル クリック、**シーン**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="fda12-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="fda12-473">2 つの Unity sceens 見つかります**MixedReality213**と**MixedReality213Advanced**します。</span><span class="sxs-lookup"><span data-stu-id="fda12-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="fda12-474">**MixedReality213**:1 つのブラシで完了したシーン</span><span class="sxs-lookup"><span data-stu-id="fda12-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="fda12-475">**MixedReality213Advanced**:[選択] ボタンを押して量例での複数のブラシで完了したシーン</span><span class="sxs-lookup"><span data-stu-id="fda12-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="fda12-476">関連項目</span><span class="sxs-lookup"><span data-stu-id="fda12-476">See also</span></span>

* [<span data-ttu-id="fda12-477">MR 入力 213 プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="fda12-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="fda12-478">混合現実 Toolkit - モーション コント ローラーのテスト シーン</span><span class="sxs-lookup"><span data-stu-id="fda12-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="fda12-479">Mixed Reality Toolkit - グラブのしくみ</span><span class="sxs-lookup"><span data-stu-id="fda12-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="fda12-480">アニメーション コント ローラーの開発のガイドライン</span><span class="sxs-lookup"><span data-stu-id="fda12-480">Motion controller development guidelines</span></span>](motion-controllers.md)
