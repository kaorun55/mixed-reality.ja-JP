---
title: MR 入力213
description: Unity、Visual Studio、およびイマーシブヘッドセットを使用したこのコーディングチュートリアルに従って、モーションコントローラーの詳細を学習してください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、イマーシブ、motion controller、academy、チュートリアル
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516381"
---
>[!NOTE]
><span data-ttu-id="e3a9c-104">Mixed Reality Academy チュートリアルは、HoloLens (第1世代) と Mixed Reality イマーシブヘッドセットを念頭に置いて設計されています。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="e3a9c-105">そのため、これらのデバイスの開発に関するガイダンスをまだ探している開発者には、これらのチュートリアルを残しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="e3a9c-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="e3a9c-107">サポートされているデバイスでの作業を続行するために管理されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="e3a9c-108">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="e3a9c-109">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="e3a9c-110">MR 入力 213:モーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="e3a9c-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="e3a9c-111">混合現実世界のモーションコントローラーは、別のレベルの対話機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="e3a9c-112">[モーションコントローラー](motion-controllers.md)を使用すると、リアルタイムでの物理的な相互作用と同様に、オブジェクトをより自然な方法で直接やり取りし、アプリのエクスペリエンスの immersion と満足させるを増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="e3a9c-113">MR 入力213では、単純な空間描画エクスペリエンスを作成することによって、モーションコントローラーの入力イベントを調査します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="e3a9c-114">このアプリでは、ユーザーはさまざまな種類のブラシや色を使用して3次元空間で塗りつぶすことができます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="e3a9c-115">このチュートリアルで説明するトピック</span><span class="sxs-lookup"><span data-stu-id="e3a9c-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="e3a9c-119">**コントローラーの視覚化**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-119">**Controller visualization**</span></span>|<span data-ttu-id="e3a9c-120">**コントローラーの入力イベント**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-120">**Controller input events**</span></span>|<span data-ttu-id="e3a9c-121">**カスタムコントローラーと UI**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="e3a9c-122">Unity のゲームモードとランタイムでモーションコントローラーモデルをレンダリングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="e3a9c-123">さまざまな種類のボタンイベントとそのアプリケーションを理解します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="e3a9c-124">コントローラー上に UI 要素を重ね合わせる方法、または UI 要素を完全にカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="e3a9c-125">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="e3a9c-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e3a9c-126">まで</span><span class="sxs-lookup"><span data-stu-id="e3a9c-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="e3a9c-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="e3a9c-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="e3a9c-128"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="e3a9c-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="e3a9c-129">MR 入力 213:モーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="e3a9c-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="e3a9c-130">✔️</span><span class="sxs-lookup"><span data-stu-id="e3a9c-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="e3a9c-131">開始前の準備</span><span class="sxs-lookup"><span data-stu-id="e3a9c-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="e3a9c-132">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e3a9c-132">Prerequisites</span></span>

<span data-ttu-id="e3a9c-133">[このページ](install-the-tools.md)の「イマーシブヘッドセットのインストールチェックリスト」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="e3a9c-134">このチュートリアルには[Unity 2017.2.1 p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)が必要です</span><span class="sxs-lookup"><span data-stu-id="e3a9c-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="e3a9c-135">プロジェクトファイル</span><span class="sxs-lookup"><span data-stu-id="e3a9c-135">Project files</span></span>

* <span data-ttu-id="e3a9c-136">プロジェクトに必要な[ファイルをダウンロード](https://github.com/Microsoft/MixedReality213/archive/master.zip)し、ファイルをデスクトップに抽出します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="e3a9c-137">ダウンロードする前にソースコードを確認する場合は、GitHub から[入手でき](https://github.com/Microsoft/MixedReality213)ます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="e3a9c-138">Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="e3a9c-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="e3a9c-139">目的</span><span class="sxs-lookup"><span data-stu-id="e3a9c-139">Objectives</span></span>

* <span data-ttu-id="e3a9c-140">Windows Mixed Reality 開発用に Unity を最適化する</span><span class="sxs-lookup"><span data-stu-id="e3a9c-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="e3a9c-141">Mixed Reality カメラの設定</span><span class="sxs-lookup"><span data-stu-id="e3a9c-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="e3a9c-142">環境のセットアップ</span><span class="sxs-lookup"><span data-stu-id="e3a9c-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="e3a9c-143">手順</span><span class="sxs-lookup"><span data-stu-id="e3a9c-143">Instructions</span></span>

* <span data-ttu-id="e3a9c-144">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-144">Start Unity.</span></span>
* <span data-ttu-id="e3a9c-145">**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-145">Select **Open**.</span></span>
* <span data-ttu-id="e3a9c-146">デスクトップに移動し、以前に unarchived した**MixedReality213**フォルダーを探します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="e3a9c-147">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="e3a9c-148">Unity がプロジェクトファイルの読み込みを完了すると、Unity エディターを表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="e3a9c-149">Unity で、[**ファイル > ビルド設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="e3a9c-151">[**プラットフォーム**] ボックスの一覧の [**ユニバーサル Windows プラットフォーム**] を選択し、[**プラットフォームの切り替え**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="e3a9c-152">ターゲットデバイスを**任意のデバイス**に設定する</span><span class="sxs-lookup"><span data-stu-id="e3a9c-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="e3a9c-153">ビルドの種類を**D3D**に設定</span><span class="sxs-lookup"><span data-stu-id="e3a9c-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="e3a9c-154">SDK を**最新のインストール済み**に設定する</span><span class="sxs-lookup"><span data-stu-id="e3a9c-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="e3a9c-155">**Unity C#プロジェクト**を確認する</span><span class="sxs-lookup"><span data-stu-id="e3a9c-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="e3a9c-156">これにより、Unity プロジェクトを再構築しなくても、Visual Studio プロジェクトでスクリプトファイルを変更できます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="e3a9c-157">[**プレーヤーの設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="e3a9c-158">[**インスペクター** ] パネルで、下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="e3a9c-159">XR の設定で、[ **Virtual Reality がサポートされる**] をオンにします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="e3a9c-160">[Virtual Reality Sdk] で、[ **Windows Mixed reality** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="e3a9c-162">**ビルドの設定**ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="e3a9c-163">プロジェクトの構造</span><span class="sxs-lookup"><span data-stu-id="e3a9c-163">Project structure</span></span>

<span data-ttu-id="e3a9c-164">このチュートリアルでは **[、Mixed Reality Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** を使用します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="e3a9c-165">リリースは[このページ](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="e3a9c-167">**参照のための完了したシーン**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="e3a9c-168">[**シーン**] フォルダーの下に2つの Unity シーンが完成していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="e3a9c-169">**MixedReality213**:ブラシが1つの完成したシーン</span><span class="sxs-lookup"><span data-stu-id="e3a9c-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="e3a9c-170">**MixedReality213Advanced**:複数のブラシを使用した高度なデザインのための完成したシーン</span><span class="sxs-lookup"><span data-stu-id="e3a9c-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="e3a9c-171">**チュートリアルの新しいシーンの設定**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="e3a9c-172">Unity で、[**ファイル > 新しいシーン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="e3a9c-173">**メインカメラ**と**指向性ライト**の削除</span><span class="sxs-lookup"><span data-stu-id="e3a9c-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="e3a9c-174">[**プロジェクト] パネル**で、次の prefabs を検索し、[**階層**] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="e3a9c-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="e3a9c-176">Assets/AppPrefabs/**Environment**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-176">Assets/AppPrefabs/**Environment**</span></span>

![カメラと環境](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="e3a9c-178">Mixed Reality Toolkit には、次の2つのカメラ prefabs があります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="e3a9c-179">**MixedRealityCamera**:カメラのみ</span><span class="sxs-lookup"><span data-stu-id="e3a9c-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="e3a9c-180">**MixedRealityCameraParent**:カメラ + テレと境界</span><span class="sxs-lookup"><span data-stu-id="e3a9c-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="e3a9c-181">このチュートリアルでは、 **MixedRealityCamera**機能を使用せずに、この機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="e3a9c-182">このため、基本的なフロアを含む単純な**環境**prefab を追加し、ユーザーが接地できるようにしました。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="e3a9c-183">**MixedRealityCameraParent**を使用した電話の詳細については、[上級設計と locomotion](#advanced-design---teleportation-and-locomotion)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="e3a9c-184">**スカイボックスのセットアップ**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-184">**Skybox setup**</span></span>
* <span data-ttu-id="e3a9c-185">[**ウィンドウ > 照明 > 設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="e3a9c-186">[**スカイボックス素材] フィールド**の右側にある円をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="e3a9c-187">「Gray」と入力し、 **SkyboxGray**を選択します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="e3a9c-188">(Assets/AppPrefabs/Support/マテリアル/SkyboxGray)</span><span class="sxs-lookup"><span data-stu-id="e3a9c-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![スカイボックスの設定](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="e3a9c-190">**スカイ**ボックスをチェックして、割り当てられている灰色のグラデーションスカイボックスを確認できるようにします</span><span class="sxs-lookup"><span data-stu-id="e3a9c-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![スカイボックスの切り替えオプション](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="e3a9c-192">MixedRealityCamera、Environment、および gray スカイボックスのシーンは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![MixedReality213 環境](images/mr213-environment-600px.jpg)
* <span data-ttu-id="e3a9c-194">[**ファイル > をクリックしてシーンを保存**]</span><span class="sxs-lookup"><span data-stu-id="e3a9c-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="e3a9c-195">シーンを任意の名前でシーンフォルダーに**保存**する</span><span class="sxs-lookup"><span data-stu-id="e3a9c-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="e3a9c-196">第1章-コントローラーの視覚化</span><span class="sxs-lookup"><span data-stu-id="e3a9c-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="e3a9c-197">目的</span><span class="sxs-lookup"><span data-stu-id="e3a9c-197">Objectives</span></span>

* <span data-ttu-id="e3a9c-198">Unity のゲームモードと実行時にモーションコントローラーモデルをレンダリングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="e3a9c-199">Windows Mixed Reality は、コントローラーを視覚化するためのアニメーションコントローラーモデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="e3a9c-200">アプリでコントローラーを視覚化するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="e3a9c-201">既定-変更せずに既定のコントローラーを使用する</span><span class="sxs-lookup"><span data-stu-id="e3a9c-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="e3a9c-202">ハイブリッド-既定のコントローラーを使用しますが、一部の要素または UI コンポーネントのオーバーレイをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="e3a9c-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="e3a9c-203">置換-コントローラー用にカスタマイズした独自の3D モデルを使用する</span><span class="sxs-lookup"><span data-stu-id="e3a9c-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="e3a9c-204">この章では、これらのコントローラーのカスタマイズの例について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="e3a9c-205">手順</span><span class="sxs-lookup"><span data-stu-id="e3a9c-205">Instructions</span></span>

* <span data-ttu-id="e3a9c-206">[**プロジェクト**] パネルで、検索ボックスに「 **motioncontrollers** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="e3a9c-207">また、Assets/HoloToolkit/Input/Prefabs/で見つけることもできます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="e3a9c-208">**Motioncontrollers** prefab を [**階層**] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="e3a9c-209">[**階層**] パネルで、 **motioncontrollers** prefab をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="e3a9c-210">**MotionControllers prefab**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="e3a9c-211">**Motioncontrollers** prefab には、代替コントローラーモデルのスロットを提供する**Motioncontrollers ビジュアライザー**スクリプトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="e3a9c-212">独自のカスタム3D モデル (手動または剣) を割り当て、[常に代替の左/右モデルを使用する] チェックボックスをオンにすると、既定のモデルの代わりにそれらが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="e3a9c-213">このスロットを4章で使用して、コントローラーモデルをブラシで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="e3a9c-215">**マニュアル**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-215">**Instructions**</span></span>
* <span data-ttu-id="e3a9c-216">[**インスペクター** ] パネルで、[ **Motionコントローラービジュアライザー**スクリプト] をダブルクリックして、Visual Studio のコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="e3a9c-217">**Motionコントローラービジュアライザースクリプト**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="e3a9c-218">**Motioncontroller ビジュアライザー**と**Motioncontroller info**クラスは、既定のコントローラーモデルにアクセス & 変更する手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="e3a9c-219">**Motioncontroller ビジュアライザー**は、Unity の**interactionsourcedetected**イベントをサブスクライブし、検出されたときにコントローラーモデルを自動的にインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="e3a9c-220">コントローラーモデルは、 [glTF 仕様](https://github.com/KhronosGroup/glTF)に従って配信されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="e3a9c-221">この形式は、一般的な形式を提供するために作成されており、3D アセットの送信とアンパックの背後にあるプロセスが改善されています。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="e3a9c-222">この場合、ユーザーの操作を可能な限りシームレスにするため、実行時にコントローラーモデルを取得して読み込む必要があります。また、ユーザーが使用しているモーションコントローラーのバージョンが保証されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="e3a9c-223">このコースでは、Mixed Reality Toolkit を使用して、Khronos グループの[Unitygltf プロジェクト](https://github.com/KhronosGroup/UnityGLTF)のバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="e3a9c-224">コントローラーが配信されると、スクリプトは**Motioncontroller info**を使用して特定のコントローラー要素の変換を見つけることができるため、適切に配置できます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="e3a9c-225">この後の章では、これらのスクリプトを使用して、UI 要素をコントローラーにアタッチする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="e3a9c-226">*スクリプトによっては、#if のあるコードブロックを見つけることができます **。UNITY_EDITOR**または**UNITY_WSA**。これらのコードブロックは、Windows に配置するときに UWP ランタイムでのみ実行されます。これは、Unity エディターと UWP アプリのランタイムで使用される Api のセットが異なるためです。*</span><span class="sxs-lookup"><span data-stu-id="e3a9c-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="e3a9c-227">シーンを**保存**し、[**再生**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="e3a9c-228">ヘッドセットには、モーションコントローラーを含むシーンを表示できます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="e3a9c-229">ボタンのクリック、サムスティックの移動、およびタッチパッドのタッチの強調表示に関する詳細なアニメーションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller 視覚化の既定値](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="e3a9c-231">第2章-UI 要素のコントローラーへのアタッチ</span><span class="sxs-lookup"><span data-stu-id="e3a9c-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="e3a9c-232">目的</span><span class="sxs-lookup"><span data-stu-id="e3a9c-232">Objectives</span></span>

* <span data-ttu-id="e3a9c-233">モーションコントローラーの要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="e3a9c-234">コントローラーの特定の部分にオブジェクトをアタッチする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="e3a9c-235">この章では、ユーザーがいつでも簡単にアクセスして操作できるコントローラーにユーザーインターフェイス要素を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="e3a9c-236">また、タッチパッド入力を使用して簡単なカラーピッカー UI を追加する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="e3a9c-237">手順</span><span class="sxs-lookup"><span data-stu-id="e3a9c-237">Instructions</span></span>

* <span data-ttu-id="e3a9c-238">[**プロジェクト**] パネルで、 **Motionコントローラー情報**スクリプトを検索します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="e3a9c-239">検索結果から [ **Motionコントローラー情報**スクリプト] をダブルクリックして、Visual Studio のコードを確認します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="e3a9c-240">**Motionコントローラー情報スクリプト**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="e3a9c-241">最初の手順は、UI をアタッチするコントローラーの要素を選択することです。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="e3a9c-242">これらの要素は、 **MotionControllerInfo.cs**の**コントローラー**で定義されています。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 Motionコントローラー要素](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="e3a9c-244">**Home**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-244">**Home**</span></span>
* <span data-ttu-id="e3a9c-245">**Menu**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-245">**Menu**</span></span>
* <span data-ttu-id="e3a9c-246">**つかん**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-246">**Grasp**</span></span>
* <span data-ttu-id="e3a9c-247">**スティック**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-247">**Thumbstick**</span></span>
* <span data-ttu-id="e3a9c-248">**Select**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-248">**Select**</span></span>
* <span data-ttu-id="e3a9c-249">**タッチパッド**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-249">**Touchpad**</span></span>
* <span data-ttu-id="e3a9c-250">**ポインティング**型: この要素は、方向をポイントするコントローラーの先端を表します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="e3a9c-251">**マニュアル**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-251">**Instructions**</span></span>
* <span data-ttu-id="e3a9c-252">[**プロジェクト**] パネルで、[ **attachtocontroller**スクリプト] を検索します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="e3a9c-253">検索結果から、[ **Attachtocontroller** script] をダブルクリックして Visual Studio のコードを確認します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="e3a9c-254">**AttachToController スクリプト**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-254">**AttachToController script**</span></span>

<span data-ttu-id="e3a9c-255">**Attachtocontroller**スクリプトを使用すると、任意のオブジェクトを、指定したコントローラーのききと要素に簡単にアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="e3a9c-256">**Attachelementtocontroller ()** で、</span><span class="sxs-lookup"><span data-stu-id="e3a9c-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="e3a9c-257">**Motionコントローラー**を使用してきき手をチェックする</span><span class="sxs-lookup"><span data-stu-id="e3a9c-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="e3a9c-258">**MotionTryGetElement ()** を使用して、コントローラーの特定の要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="e3a9c-259">コントローラーモデルから要素の変換を取得した後、その下にあるオブジェクトを親として設定し、オブジェクトのローカル位置 & 回転を0に設定します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

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

<span data-ttu-id="e3a9c-260">**Attachtocontroller**スクリプトを使用する最も簡単な方法は、ColorPickerWheel の場合と同様に、このスクリプトを継承することです **。**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="e3a9c-261">**Onattachtocontroller**関数と**OnDetatchFromController**関数をオーバーライドするだけで、コントローラーが検出または切断されたときにセットアップ/ブレークダウンを実行できます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="e3a9c-262">**マニュアル**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-262">**Instructions**</span></span>
* <span data-ttu-id="e3a9c-263">[**プロジェクト**] パネルで、検索ボックスに「 **ColorPickerWheel**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="e3a9c-264">[Assets/AppPrefabs/] の下にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="e3a9c-265">**ColorPickerWheel** prefab を [**階層**] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="e3a9c-266">[**階層**] パネルの [ **ColorPickerWheel** prefab] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="e3a9c-267">[**インスペクター** ] パネルで [ **ColorPickerWheel** Script] をダブルクリックして、Visual Studio でコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel prefab](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="e3a9c-269">**ColorPickerWheel スクリプト**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="e3a9c-270">**ColorPickerWheel**は**attachtocontroller**を継承するため 、Inspector と**要素**が**インスペクター**パネルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="e3a9c-271">左側のコントローラーのタッチパッド要素に UI をアタッチします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![ColorPickerWheel スクリプト](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="e3a9c-273">**ColorPickerWheel**は、 **Onattachtocontroller**と**OnDetatchFromController**をオーバーライドして入力イベントをサブスクライブします。これは、タッチパッド入力による色の選択の次の章で使用されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

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
* <span data-ttu-id="e3a9c-274">シーンを**保存**し、[**再生**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="e3a9c-275">**オブジェクトをコントローラーにアタッチするための別の方法**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="e3a9c-276">スクリプトは**attachtocontroller**から継承し、 **onattachtocontroller**をオーバーライドすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="e3a9c-277">ただし、これは常に可能であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-277">However, this may not always be possible.</span></span> <span data-ttu-id="e3a9c-278">別の方法として、スタンドアロンコンポーネントとして使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="e3a9c-279">これは、スクリプトをリファクタリングせずに既存の prefab をコントローラーにアタッチする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="e3a9c-280">セットアップを実行する前に、クラスで IsAttached が true に設定されるのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="e3a9c-281">これを行う最も簡単な方法は、' Start ' にコルーチンを使用することです。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="e3a9c-282">第3章: タッチパッド入力の操作</span><span class="sxs-lookup"><span data-stu-id="e3a9c-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="e3a9c-283">目的</span><span class="sxs-lookup"><span data-stu-id="e3a9c-283">Objectives</span></span>

* <span data-ttu-id="e3a9c-284">タッチパッド入力データイベントを取得する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="e3a9c-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="e3a9c-285">タッチパッドの軸の位置情報をアプリのエクスペリエンスに使用する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="e3a9c-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="e3a9c-286">手順</span><span class="sxs-lookup"><span data-stu-id="e3a9c-286">Instructions</span></span>

* <span data-ttu-id="e3a9c-287">[**階層**] パネルで、[ **ColorPickerWheel** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="e3a9c-288">[**インスペクター** ] パネルの [ **Animatior**] で、[ **ColorPickerWheelController** ] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="e3a9c-289">[**アニメーター** ] タブが開いていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="e3a9c-290">**Unity のアニメーションコントローラーを使用した UI の表示/非表示**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="e3a9c-291">アニメーションを使用して**ColorPickerWheel** UI の表示と非表示を切り替えるには、 [Unity のアニメーションシステム](https://docs.unity3d.com/Manual/AnimationOverview.html)を使用します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="e3a9c-292">**ColorPickerWheel**の**Visible**プロパティを true または false に設定すると、アニメーショントリガーの**表示**と**非表示が切り替え**られます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="e3a9c-293">**表示**と**非表示**のパラメーターは、 **ColorPickerWheelController** animation コントローラーで定義されています。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Unity アニメーションコントローラー](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="e3a9c-295">**マニュアル**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-295">**Instructions**</span></span>
* <span data-ttu-id="e3a9c-296">[**階層**] パネルで [ **ColorPickerWheel** prefab] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="e3a9c-297">[**インスペクター** ] パネルで [ **ColorPickerWheel** script] をダブルクリックして、Visual Studio でコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="e3a9c-298">**ColorPickerWheel スクリプト**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="e3a9c-299">**ColorPickerWheel**は、タッチパッドイベントをリッスンするために、Unity の**Interactionsourceupdated**イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="e3a9c-300">**Interactionsourceupdated ()** では、スクリプトはまず次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="e3a9c-301">は、実際にはタッチパッドイベント (obj. state.**touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="e3a9c-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="e3a9c-302">左のコントローラー (obj. state. source.**きき手**)</span><span class="sxs-lookup"><span data-stu-id="e3a9c-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="e3a9c-303">両方が true の場合、タッチパッドの位置 (obj.**touchpadPosition**) は**selectorPosition**に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

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

<span data-ttu-id="e3a9c-304">**Update ()** では、 **visible**プロパティに基づいて、カラーピッカーのアニメーターコンポーネントでアニメーショントリガーの表示と非表示をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

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

<span data-ttu-id="e3a9c-305">**Update ()** では、 **selectorPosition**を使用して、カラーホイールのメッシュ collider に射線をキャストします。これにより、UV 位置が返されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="e3a9c-306">この位置を使用して、カラーホイールのテクスチャのピクセル座標と色の値を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="e3a9c-307">この値は、 **Selectedcolor**プロパティを使用して他のスクリプトからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![カラーピッカーのホイール Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="e3a9c-309">Chapter 4-コントローラーモデルのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="e3a9c-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="e3a9c-310">目的</span><span class="sxs-lookup"><span data-stu-id="e3a9c-310">Objectives</span></span>

* <span data-ttu-id="e3a9c-311">カスタム3D モデルを使用してコントローラーモデルを上書きする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="e3a9c-313">手順</span><span class="sxs-lookup"><span data-stu-id="e3a9c-313">Instructions</span></span>

* <span data-ttu-id="e3a9c-314">[**階層**] パネルの [ **motioncontrollers** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="e3a9c-315">[**代替右コントローラー** ] フィールドの右側にある円をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="e3a9c-316">**「BrushController**」と入力し、結果から prefab を選択します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="e3a9c-317">これは Assets/AppPrefabs/**BrushController**にあります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="e3a9c-318">**常に代替右モデルを使用することを確認する**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="e3a9c-320">**BrushController** prefab は、**階層**パネルに含まれている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="e3a9c-321">ただし、子コンポーネントを確認するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-321">However, to check out its child components:</span></span>
* <span data-ttu-id="e3a9c-322">[**プロジェクト**] パネルで、「 **BrushController** 」と入力し、[ **BrushController** prefab] を [**階層**] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="e3a9c-324">**Tip**コンポーネントは**BrushController**にあります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="e3a9c-325">この変換を使用して、描画線を開始または停止します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="e3a9c-326">[**階層**] パネルから**BrushController**を削除します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="e3a9c-327">シーンを**保存**し、[**再生**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="e3a9c-328">ブラシモデルは、右側のモーションコントローラーに置き換えられていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="e3a9c-329">Chapter 5-Select 入力による塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="e3a9c-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="e3a9c-330">目的</span><span class="sxs-lookup"><span data-stu-id="e3a9c-330">Objectives</span></span>

* <span data-ttu-id="e3a9c-331">Select button イベントを使用して、線描画を開始および停止する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="e3a9c-332">手順</span><span class="sxs-lookup"><span data-stu-id="e3a9c-332">Instructions</span></span>

* <span data-ttu-id="e3a9c-333">[**プロジェクト**] パネルで**BrushController** prefab を検索します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="e3a9c-334">[**インスペクター** ] パネルで [ **BrushController** Script] をダブルクリックして、Visual Studio でコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="e3a9c-335">**BrushController スクリプト**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-335">**BrushController script**</span></span>

<span data-ttu-id="e3a9c-336">**BrushController**は、InteractionManager の**Interactionsource押さ**れたイベントと**InteractionSourceReleased**イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="e3a9c-337">**Interactionsourcepressed**れたイベントがトリガーされると、ブラシの**Draw**プロパティが true に設定されます。**InteractionSourceReleased**イベントがトリガーされると、ブラシの**Draw**プロパティが false に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

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

<span data-ttu-id="e3a9c-338">**描画**が true に設定されている場合、ブラシはインスタンス化された Unity **LineRenderer**内のポイントを生成します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="e3a9c-339">この prefab への参照は、ブラシの**ストローク prefab**フィールドに保持されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

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

<span data-ttu-id="e3a9c-340">カラーピッカーのホイール UI で現在選択されている色を使用するには、 **BrushController**が**ColorPickerWheel**オブジェクトへの参照を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="e3a9c-341">**BrushController** prefab は実行時に交換用コントローラーとしてインスタンス化されるため、シーン内のオブジェクトへの参照は実行時に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="e3a9c-342">この例では、 **FindObjectOfType**を使用して**ColorPickerWheel**を検索します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

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
* <span data-ttu-id="e3a9c-343">シーンを**保存**し、[**再生**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="e3a9c-344">右側のコントローラーの [選択] ボタンを使用して、線を描画し、塗りつぶすことができます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="e3a9c-345">Chapter 6-Select 入力を使用したオブジェクトの生成</span><span class="sxs-lookup"><span data-stu-id="e3a9c-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="e3a9c-346">目的</span><span class="sxs-lookup"><span data-stu-id="e3a9c-346">Objectives</span></span>

* <span data-ttu-id="e3a9c-347">選択ボタンと表示ボタンの入力イベントを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="e3a9c-348">オブジェクトをインスタンス化する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="e3a9c-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="e3a9c-349">手順</span><span class="sxs-lookup"><span data-stu-id="e3a9c-349">Instructions</span></span>

* <span data-ttu-id="e3a9c-350">[**プロジェクト**] パネルの [検索] ボックスに「 **ObjectSpawner** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="e3a9c-351">また、Assets/AppPrefabs の下にあります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="e3a9c-352">**ObjectSpawner** prefab を [**階層**] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="e3a9c-353">[**階層**] パネルの [ **ObjectSpawner** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="e3a9c-354">**ObjectSpawner**には、 **Color Source**という名前のフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="e3a9c-355">[**階層**] パネルで、 **ColorPickerWheel**参照をこのフィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![オブジェクト Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="e3a9c-357">[**階層**] パネルの [ **ObjectSpawner** prefab] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="e3a9c-358">[**インスペクター** ] パネルで [ **ObjectSpawner** Script] をダブルクリックして、Visual Studio でコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="e3a9c-359">**ObjectSpawner スクリプト**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="e3a9c-360">**ObjectSpawner**は、空間にプリミティブメッシュ (cube、球、シリンダ) のコピーをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="e3a9c-361">**Interactionsourcepressed**れたことが検出されると、きき者と、そのイベントが interactionsourcepresstype または**interactionsourcepresstype**であるかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="e3a9c-362">イベントを**把握**するために、現在のメッシュの種類 (球、cube、円柱) のインデックスをインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

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

<span data-ttu-id="e3a9c-363">**Select**イベントの場合、 **SpawnObject ()** では、新しいオブジェクトがインスタンス化され、親ではありません。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

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

<span data-ttu-id="e3a9c-364">**ObjectSpawner**は、 **ColorPickerWheel**を使用して、表示オブジェクトの素材の色を設定します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="e3a9c-365">生成されたオブジェクトには、その色が保持されるように、このマテリアルのインスタンスが与えられます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="e3a9c-366">シーンを**保存**し、[**再生**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="e3a9c-367">ボタンを使用してオブジェクトを変更し、[選択] ボタンを使用してオブジェクトを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="e3a9c-368">アプリをビルドし、Mixed Reality ポータルにデプロイする</span><span class="sxs-lookup"><span data-stu-id="e3a9c-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="e3a9c-369">Unity で、[**ファイル > ビルド設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="e3a9c-370">[**開い**ているシーンの追加] をクリックして、**ビルドのシーン**に現在のシーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="e3a9c-371">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-371">Click **Build**.</span></span>
* <span data-ttu-id="e3a9c-372">"App" という名前の**新しいフォルダー**を作成します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="e3a9c-373">**アプリ**フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="e3a9c-374">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="e3a9c-375">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="e3a9c-376">**アプリ**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-376">Open the **App** folder.</span></span>
* <span data-ttu-id="e3a9c-377">**YourSceneName** Visual Studio ソリューションファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="e3a9c-378">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから**リリース**に、ARM から**X64**に変更します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="e3a9c-379">[デバイス] ボタンの横にあるドロップダウン矢印をクリックし、[**ローカルコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="e3a9c-380">メニューで [デバッグ] **、[デバッグなしで開始**] の順にクリックする >、Ctrl キーを押し**ながら F5**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="e3a9c-381">これで、アプリがビルドされ、Mixed Reality ポータルにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="e3a9c-382">これは、Mixed Reality ポータルの [スタート] メニューを使用して再度起動することができます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="e3a9c-383">高度なデザイン-放射状レイアウトを使用したブラシツール</span><span class="sxs-lookup"><span data-stu-id="e3a9c-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="e3a9c-385">この章では、既定のモーションコントローラーモデルをカスタムブラシツールコレクションに置き換える方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="e3a9c-386">参考までに **、[シーン**] フォルダーの下の完成したシーン**MixedReality213Advanced**を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="e3a9c-387">手順</span><span class="sxs-lookup"><span data-stu-id="e3a9c-387">Instructions</span></span>

* <span data-ttu-id="e3a9c-388">[**プロジェクト**] パネルの [検索] ボックスに「 **BrushSelector** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="e3a9c-389">また、Assets/AppPrefabs の下にあります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="e3a9c-390">**BrushSelector** prefab を [**階層**] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="e3a9c-391">組織の場合は、**ブラシ**と呼ばれる空のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="e3a9c-392">[**プロジェクト**] パネルから [**ブラシ**] に次の prefabs をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="e3a9c-393">Assets/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="e3a9c-394">Assets/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="e3a9c-395">Assets/AppPrefabs/**消しゴム**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="e3a9c-396">Assets/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="e3a9c-397">Assets/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="e3a9c-398">Assets/AppPrefabs/**鉛筆**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-398">Assets/AppPrefabs/**Pencil**</span></span>

![ブラシ](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="e3a9c-400">[**階層**] パネルの [ **motioncontrollers** prefab] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="e3a9c-401">[**インスペクター** ] パネルの [**モーションコントローラービジュアライザー**で**常に代替モデルを使用する**] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="e3a9c-402">[**階層**] パネルで、[ **BrushSelector** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="e3a9c-403">**BrushSelector**に**colorpicker**という名前のフィールドがある</span><span class="sxs-lookup"><span data-stu-id="e3a9c-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="e3a9c-404">[**階層**] パネルで、[ **ColorPickerWheel** ] を [**インスペクター** ] パネルの [ **colorpicker** ] フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![ColorPickerWheel をブラシセレクターに割り当てる](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="e3a9c-406">[**階層**] パネルの [ **BrushSelector** Prefab] で、**メニュー**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="e3a9c-407">[**インスペクター** ] パネルの**lineobjectcollection**コンポーネントで、[**オブジェクト**配列] ドロップダウンを開きます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="e3a9c-408">6個の空のスロットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="e3a9c-409">[**階層**] パネルで、[**ブラシ**の prefabs] の下にある各親を、任意の順序でこれらのスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="e3a9c-410">(プロジェクトフォルダー内の prefabs ではなく、シーンから prefabs をドラッグしていることを確認してください)。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![ブラシセレクター](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="e3a9c-412">**BrushSelector prefab**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="e3a9c-413">**BrushSelector**は**attachtocontroller**を継承するため、[ **Inspector** ] パネルに**きき**と**要素**のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="e3a9c-414">**右**を選択し、[ポーズ] を**ポイント**して、右のコントローラーに [ブラシ] ツールを接続します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="e3a9c-415">**BrushSelector**は、次の2つのユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="e3a9c-416">**楕円**: 楕円形に沿って空間内のポイントを生成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="e3a9c-417">**Lineobjectcollection**: 任意の行クラスによって生成された点を使用してオブジェクトを分散します (例: 楕円)。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="e3a9c-418">ここでは、楕円の形状に沿ってブラシを配置するために使用します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="e3a9c-419">これらのユーティリティを組み合わせて使用すると、放射状メニューを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="e3a9c-420">**LineObjectCollection スクリプト**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="e3a9c-421">**Lineobjectcollection**には、その行に沿って分布するオブジェクトのサイズ、位置、および回転を制御します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="e3a9c-422">これは、ブラシセレクターのような放射状メニューを作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="e3a9c-423">中心が選択された位置に近づいたときに、何もスケールアップしないブラシの外観を作成するために、 **objectscale**曲線は中央にピークし、端に tapers ます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="e3a9c-424">**BrushSelector スクリプト**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-424">**BrushSelector script**</span></span>

<span data-ttu-id="e3a9c-425">**BrushSelector**の場合、手続き型アニメーションを使用することを選択しました。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="e3a9c-426">最初に、ブラシモデルは**Lineobjectcollection**スクリプトによって楕円で配分されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="e3a9c-427">次に、各ブラシは、選択内容に基づいて変化する**DisplayMode**値に基づいて、ユーザー側での位置を維持する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="e3a9c-428">ユーザーがブラシを選択したときにブラシの位置の切り替えが中断される可能性が高いため、手続き型の方法を選択しました。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="e3a9c-429">Mecanim アニメーションは中断を適切に処理できますが、単純な Lerp 操作よりも複雑になる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="e3a9c-430">**BrushSelector**は、両方の組み合わせを使用します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="e3a9c-431">タッチパッドの入力が検出されると、ブラシのオプションが表示され、放射状メニューに沿ってスケールアップされます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="e3a9c-432">タイムアウト期間が経過すると (ユーザーが選択を行ったことを示す)、ブラシのオプションが再度スケールダウンされ、選択したブラシだけが残ります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="e3a9c-433">**タッチパッド入力の視覚化**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="e3a9c-434">コントローラーモデルが完全に置き換えられている場合でも、元のモデル入力に入力を表示すると便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="e3a9c-435">これは、実際にユーザーの操作をグラウンドにするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="e3a9c-436">**BrushSelector**の場合、入力を受け取ったときにタッチパッドを短時間で表示するように選択しました。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="e3a9c-437">これを行うには、コントローラーからタッチパッド要素を取得し、そのマテリアルをカスタムマテリアルに置き換えて、タッチパッド入力を最後に受信したときに基づいてそのマテリアルの色にグラデーションを適用します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

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

<span data-ttu-id="e3a9c-438">**タッチパッド入力によるブラシツールの選択**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="e3a9c-439">ブラシセレクターがタッチパッドの押された入力を検出すると、入力の位置を調べて、左または右にあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="e3a9c-440">**SelectPressedAmount を使用したストロークの太さ**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="e3a9c-441">**Interactionsourcepresstype ()** 内の**Select**イベントの代わりに、 **selectPressedAmount**を使用して、押された量のアナログ値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="e3a9c-442">この値は、 **Interactionsourceupdated ()** で取得できます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

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

<span data-ttu-id="e3a9c-443">**消しゴムスクリプト**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-443">**Eraser script**</span></span>

<span data-ttu-id="e3a9c-444">**消しゴム**は、基本**ブラシ**の**drawovertime ()** 関数をオーバーライドする特殊な種類のブラシです。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="e3a9c-445">描画が true の場合、消しゴムは、そのチップが既存のブラシストロークと交差しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="e3a9c-446">存在する場合は、圧縮されて削除されるようにキューに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="e3a9c-447">高度な設計-電話と locomotion</span><span class="sxs-lookup"><span data-stu-id="e3a9c-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="e3a9c-448">ユーザーがサムスティックを使用して、ユーザーによるシーンの移動を許可する場合は、 **MixedRealityCamera**ではなく**MixedRealityCameraParent**を使用します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="e3a9c-449">**Inputmanager**と**DefaultCusor**も追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="e3a9c-450">**MixedRealityCameraParent**には既に**Motioncontrollers**と**境界**が子コンポーネントとして含まれているため、既存の**motioncontrollers**と**環境**prefab を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="e3a9c-451">手順</span><span class="sxs-lookup"><span data-stu-id="e3a9c-451">Instructions</span></span>

* <span data-ttu-id="e3a9c-452">[**階層**] パネルで、 **MixedRealityCamera**、 **Environment** 、 **motioncontrollers**を削除します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="e3a9c-453">[**プロジェクト] パネル**で、次の prefabs を検索し、[**階層**] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="e3a9c-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="e3a9c-455">Assets/AppPrefabs/Input/Prefabs/**Inputmanager**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="e3a9c-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**Defaultcursor**</span><span class="sxs-lookup"><span data-stu-id="e3a9c-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![Mixed Reality カメラの親](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="e3a9c-458">[**階層**] パネルで、[**入力マネージャー** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="e3a9c-459">[**インスペクター** ] パネルで、**単純な単一ポインターセレクター**セクションまで下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="e3a9c-460">[**階層**] パネルで、[ **Defaultcursor** ] を**カーソル**フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![DefaultCursor の割り当て](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="e3a9c-462">シーンを**保存**し、[**再生**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="e3a9c-463">サムスティックを使用して、左/右に回転したり、テレポートしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="e3a9c-464">最後です</span><span class="sxs-lookup"><span data-stu-id="e3a9c-464">The end</span></span>

<span data-ttu-id="e3a9c-465">これがこのチュートリアルの終わりです。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="e3a9c-466">学習した内容:</span><span class="sxs-lookup"><span data-stu-id="e3a9c-466">You learned:</span></span>
* <span data-ttu-id="e3a9c-467">Unity のゲームモードとランタイムでモーションコントローラーモデルを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="e3a9c-468">さまざまな種類のボタンイベントとそのアプリケーションを使用する方法。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="e3a9c-469">コントローラー上に UI 要素を重ね合わせる方法、または UI 要素を完全にカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="e3a9c-470">これで、モーションコントローラーで独自のイマーシブエクスペリエンスを作成する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="e3a9c-471">完成したシーン</span><span class="sxs-lookup"><span data-stu-id="e3a9c-471">Completed scenes</span></span>

* <span data-ttu-id="e3a9c-472">Unity の [**プロジェクト**] パネルで、[**シーン**] フォルダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="e3a9c-473">Unity sceens **MixedReality213**と**MixedReality213Advanced**が2つ見つかります。</span><span class="sxs-lookup"><span data-stu-id="e3a9c-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="e3a9c-474">**MixedReality213**:ブラシが1つの完成したシーン</span><span class="sxs-lookup"><span data-stu-id="e3a9c-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="e3a9c-475">**MixedReality213Advanced**:複数のブラシを使用した完成したシーンの選択ボタンの押す回数の例</span><span class="sxs-lookup"><span data-stu-id="e3a9c-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="e3a9c-476">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3a9c-476">See also</span></span>

* [<span data-ttu-id="e3a9c-477">MR 入力213プロジェクトファイル</span><span class="sxs-lookup"><span data-stu-id="e3a9c-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="e3a9c-478">Mixed Reality Toolkit-モーションコントローラーテストシーン</span><span class="sxs-lookup"><span data-stu-id="e3a9c-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="e3a9c-479">Mixed Reality Toolkit-グラブ機構</span><span class="sxs-lookup"><span data-stu-id="e3a9c-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="e3a9c-480">モーションコントローラーの開発ガイドライン</span><span class="sxs-lookup"><span data-stu-id="e3a9c-480">Motion controller development guidelines</span></span>](motion-controllers.md)
