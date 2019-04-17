---
title: MR 基本 100 - Unity の概要
description: 最初の複合現実の基本的な"hello world"アプリケーションを作成する方法について説明します。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 複合現実では、Windows Mixed Reality、HoloLens、没入型、vr、mr はまず、ホログラム, academy, チュートリアル
ms.openlocfilehash: 1f4a5490383671fba694b386015ff6742d37241b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597561"
---
>[!NOTE]
><span data-ttu-id="df479-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="df479-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="df479-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="df479-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="df479-106">これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="df479-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="df479-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="df479-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="df479-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="df479-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="df479-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="df479-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="df479-110">MR 基礎 100:Unity の概要</span><span class="sxs-lookup"><span data-stu-id="df479-110">MR Basics 100: Getting started with Unity</span></span>

<span data-ttu-id="df479-111">このチュートリアルでは Unity でビルドされた基本的な複合現実アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="df479-111">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="df479-112">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="df479-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="df479-113">コース</span><span class="sxs-lookup"><span data-stu-id="df479-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="df479-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="df479-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="df479-115"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="df479-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="df479-116">MR 基礎 100:Unity の概要</span><span class="sxs-lookup"><span data-stu-id="df479-116">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="df479-117">✔️</span><span class="sxs-lookup"><span data-stu-id="df479-117">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="df479-118">✔️</span><span class="sxs-lookup"><span data-stu-id="df479-118">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="df479-119">前提条件</span><span class="sxs-lookup"><span data-stu-id="df479-119">Prerequisites</span></span>

* <span data-ttu-id="df479-120">正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="df479-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="df479-121">Chapter 1 - 新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="df479-121">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="df479-122">Unity を使用してアプリをビルドするには、まず、プロジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df479-122">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="df479-123">このプロジェクトは、いくつかのフォルダー、最も重要なものは、Assets フォルダーに編成されます。</span><span class="sxs-lookup"><span data-stu-id="df479-123">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="df479-124">これは、Maya、最大シネマ 4 D、Visual Studio または任意のコード エディターで作成するすべてのコードの Photoshop などのデジタル コンテンツの作成ツールからインポートするすべての資産を保持するフォルダーと任意の数と Unity が作成されるコンテンツのファイルのシーンを作成します。、アニメーションやその他のエディターで Unity の資産型。</span><span class="sxs-lookup"><span data-stu-id="df479-124">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="df479-125">ビルド、UWP アプリを展開し、Unity は、すべての必要な資産とコード ファイルを含む Visual Studio のソリューションとして、プロジェクトをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="df479-125">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="df479-126">Unity を開始します。</span><span class="sxs-lookup"><span data-stu-id="df479-126">Start Unity</span></span>
2. <span data-ttu-id="df479-127">選択**新規**</span><span class="sxs-lookup"><span data-stu-id="df479-127">Select **New**</span></span>
3. <span data-ttu-id="df479-128">プロジェクト名を入力します (例。"MixedRealityIntroduction")</span><span class="sxs-lookup"><span data-stu-id="df479-128">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="df479-129">プロジェクトを保存する場所を入力します。</span><span class="sxs-lookup"><span data-stu-id="df479-129">Enter a location to save your project</span></span>
5. <span data-ttu-id="df479-130">確認、 **3D**トグルが選択されています。</span><span class="sxs-lookup"><span data-stu-id="df479-130">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="df479-131">選択**プロジェクトの作成**</span><span class="sxs-lookup"><span data-stu-id="df479-131">Select **Create project**</span></span>

<span data-ttu-id="df479-132">おめでとうございますは、複合現実のカスタマイズを今すぐ開始するすべてのセットアップです。</span><span class="sxs-lookup"><span data-stu-id="df479-132">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="df479-133">第 2 章 – カメラのセットアップ</span><span class="sxs-lookup"><span data-stu-id="df479-133">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="df479-134">Unity の Main Camera は、ヘッドの追跡とステレオスコ ピック レンダリングを処理します。</span><span class="sxs-lookup"><span data-stu-id="df479-134">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="df479-135">複合現実を使用して、メイン カメラをするいくつかの変更があります。</span><span class="sxs-lookup"><span data-stu-id="df479-135">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>
1. <span data-ttu-id="df479-136">ファイルを選択 > 新しいシーン</span><span class="sxs-lookup"><span data-stu-id="df479-136">Select File > New Scene</span></span>

<span data-ttu-id="df479-137">最初に、その開始位置として、ユーザーの場合、アプリのレイアウトをしやすくなります (**X**:0、 **Y**:0、 **Z**:0).</span><span class="sxs-lookup"><span data-stu-id="df479-137">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="df479-138">Main Camera は、ユーザーの頭の動きを追跡は、ために、Main Camera の開始位置を設定して、ユーザーの開始位置を設定できます。</span><span class="sxs-lookup"><span data-stu-id="df479-138">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>
1. <span data-ttu-id="df479-139">選択**Main Camera**で、**階層**パネル</span><span class="sxs-lookup"><span data-stu-id="df479-139">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="df479-140">**インスペクター**パネルで、検索、**変換**コンポーネントと変更、**位置**から (**X**:0、 **Y**:1、 **Z**:-10) に (**X**:0、 **Y**:0、 **Z**:0)</span><span class="sxs-lookup"><span data-stu-id="df479-140">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="df479-141">次に、既定のカメラの背景には、ある程度の配慮が必要があります。</span><span class="sxs-lookup"><span data-stu-id="df479-141">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="df479-142">**HoloLens アプリケーション**、現実の世界は、カメラのすべての後ろに表示されますがレンダリング、スカイ ボックス テクスチャではありません。</span><span class="sxs-lookup"><span data-stu-id="df479-142">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>
1. <span data-ttu-id="df479-143">**Main Camera**でオンのまま、**階層**パネルで、検索、**カメラ**コンポーネント、**インスペクター**パネルし、変更、**フラグをクリア**からドロップダウン**スカイ ボックス**に**単色**します。</span><span class="sxs-lookup"><span data-stu-id="df479-143">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="df479-144">選択、**バック グラウンド**カラー ピッカー、変更、 **RGBA**値 (0, 0、0, 0)</span><span class="sxs-lookup"><span data-stu-id="df479-144">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="df479-145">**イマーシブ ヘッドセットを対象となる複合現実のアプリケーションの**Unity が提供する既定のスカイ ボックス テクスチャを使用できます。</span><span class="sxs-lookup"><span data-stu-id="df479-145">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>
1. <span data-ttu-id="df479-146">**Main Camera**でオンのまま、**階層**パネルで、検索、**カメラ**コンポーネント、**インスペクター**パネルし、保持、**フラグをクリア**ドロップダウンを使用して**スカイ ボックス**します。</span><span class="sxs-lookup"><span data-stu-id="df479-146">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="df479-147">3 番目に、お知らせ Unity でほぼリップ面を考慮し、レンダリング近すぎる、ユーザーに目をユーザーに近づくオブジェクトまたはオブジェクトがユーザーに近づくようオブジェクトをできないようにします。</span><span class="sxs-lookup"><span data-stu-id="df479-147">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="df479-148">**HoloLens のアプリケーションの**に近いクリップ平面を設定することができます、[推奨 HoloLens](camera-in-unity.md#clip-planes) 0.85 のメーターです。</span><span class="sxs-lookup"><span data-stu-id="df479-148">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>
1. <span data-ttu-id="df479-149">**Main Camera**でオンのまま、**階層**パネルで、検索、**カメラ**コンポーネント、**インスペクター**パネルし、変更、**リップ面の近く**フィールドを既定値から**0.3**推奨 HoloLens に**0.85**します。</span><span class="sxs-lookup"><span data-stu-id="df479-149">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="df479-150">**イマーシブ ヘッドセットを対象となる複合現実のアプリケーションの**Unity が提供する既定の設定を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="df479-150">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>
1. <span data-ttu-id="df479-151">**Main Camera**でオンのまま、**階層**パネルで、検索、**カメラ**コンポーネント、**インスペクター**パネルし、保持、**リップ面の近く**フィールドを既定値に**0.3**します。</span><span class="sxs-lookup"><span data-stu-id="df479-151">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="df479-152">最後に、保存する進行状況これまでにします。</span><span class="sxs-lookup"><span data-stu-id="df479-152">Finally, let us save our progress so far.</span></span> <span data-ttu-id="df479-153">シーン変更を保存する次のように選択します。**ファイル > シーンに名前を付けて**、シーンを名前**Main**、を選択し**保存**します。</span><span class="sxs-lookup"><span data-stu-id="df479-153">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="df479-154">第 3 章 - セットアップ プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="df479-154">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="df479-155">この章で開発用の Windows Holographic SDK をターゲットにご協力をいくつかの Unity プロジェクトの設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="df479-155">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="df479-156">また、アプリケーションのいくつかの品質設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="df479-156">We will also set some quality settings for our application.</span></span> <span data-ttu-id="df479-157">最後はことが、ビルド ターゲットが Windows ストアに設定できます。</span><span class="sxs-lookup"><span data-stu-id="df479-157">Finally, we will ensure our build targets are set to Windows Store.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="df479-158">Unity のパフォーマンスと品質の設定</span><span class="sxs-lookup"><span data-stu-id="df479-158">Unity performance and quality settings</span></span>

<span data-ttu-id="df479-159">**HoloLens の unity の品質の設定**</span><span class="sxs-lookup"><span data-stu-id="df479-159">**Unity quality settings for HoloLens**</span></span>

![HoloLens の unity の品質の設定](images/qualitysettings.png) 

<span data-ttu-id="df479-161">HoloLens のハイ フレーム レートの維持が非常に重要なので、最速のパフォーマンス チューニングの品質設定します。</span><span class="sxs-lookup"><span data-stu-id="df479-161">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="df479-162">詳細なパフォーマンスについては、 [for Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)します。</span><span class="sxs-lookup"><span data-stu-id="df479-162">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>
1. <span data-ttu-id="df479-163">選択**編集 > プロジェクトの設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="df479-163">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="df479-164">選択、**ドロップダウン**下、 **Windows ストア**ロゴと選択**Very Low**します。</span><span class="sxs-lookup"><span data-stu-id="df479-164">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="df479-165">Windows ストアの列と最速の行のボックスが緑色で、設定を正しく適用することがわかります。</span><span class="sxs-lookup"><span data-stu-id="df479-165">You'll know the setting is applied correctly when the box in the Windows Store column and Fastest row is green.</span></span>

<span data-ttu-id="df479-166">**閉塞表示対象となる複合現実のアプリケーションの**、その既定値に品質設定しておくことができます。</span><span class="sxs-lookup"><span data-stu-id="df479-166">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="df479-167">対象の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="df479-167">Target Windows 10 SDK</span></span>

<span data-ttu-id="df479-168">**ターゲットの Windows Holographic SDK**</span><span class="sxs-lookup"><span data-stu-id="df479-168">**Target Windows Holographic SDK**</span></span>

![ターゲットの Windows Holographic SDK](images/xrsettings.png) 

<span data-ttu-id="df479-170">Unity をエクスポートしようとしましたが、アプリが作成することを把握できるようにする必要があります、[没入型ビュー](app-views.md) 2D ビューではなく。</span><span class="sxs-lookup"><span data-stu-id="df479-170">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="df479-171">そのために Unity での仮想現実のサポートを有効にすると、Windows 10 SDK をターゲットとします。</span><span class="sxs-lookup"><span data-stu-id="df479-171">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>
1. <span data-ttu-id="df479-172">移動して**編集 > プロジェクトの設定 > Player**します。</span><span class="sxs-lookup"><span data-stu-id="df479-172">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="df479-173">**インスペクター パネル**Player の設定の選択、 **Windows ストア**アイコン。</span><span class="sxs-lookup"><span data-stu-id="df479-173">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="df479-174">展開、 **XR 設定**グループ。</span><span class="sxs-lookup"><span data-stu-id="df479-174">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="df479-175">**レンダリング** セクションで、チェック、**仮想現実サポート**新しいを追加するチェック ボックスをオン**仮想現実 Sdk**一覧。</span><span class="sxs-lookup"><span data-stu-id="df479-175">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="df479-176">いることを確認**Windows Mixed Reality**一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="df479-176">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="df479-177">そうでない場合は、選択、 **+** 一覧の下部にあるボタンをクリックし、選択**Windows Mixed Reality**します。</span><span class="sxs-lookup"><span data-stu-id="df479-177">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="df479-178">表示されない場合、 **Windows ストア**アイコン、double、Windows ストア .NET スクリプト バックエンドをインストールする前に選択したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="df479-178">If you do not see the **Windows Store** icon, double check to make sure you selected the Windows Store .NET Scripting Backend prior to installation.</span></span> <span data-ttu-id="df479-179">それ以外の場合は、Unity を適切な Windows インストールを再インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="df479-179">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="df479-180">**.NET 構成を確認します。**</span><span class="sxs-lookup"><span data-stu-id="df479-180">**Verify .NET Configuration**</span></span>

![.NET 構成を確認します。](images/configoptions-375px.png)

1. <span data-ttu-id="df479-182">移動して**編集 > プロジェクトの設定 > Player** (する必要がありますもこれ前の手順から)。</span><span class="sxs-lookup"><span data-stu-id="df479-182">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="df479-183">**インスペクター パネル**Player の設定の選択、 **Windows ストア**アイコン。</span><span class="sxs-lookup"><span data-stu-id="df479-183">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="df479-184">**その他の設定**構成セクションで、必ず**Scripting バックエンド**に設定されている **.NET**</span><span class="sxs-lookup"><span data-stu-id="df479-184">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="df479-185">適用されるすべてのプロジェクト設定の取得で上出来でした。</span><span class="sxs-lookup"><span data-stu-id="df479-185">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="df479-186">次に、ホログラムを追加しましょう!</span><span class="sxs-lookup"><span data-stu-id="df479-186">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="df479-187">4 -」の章のキューブを作成します。</span><span class="sxs-lookup"><span data-stu-id="df479-187">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="df479-188">Unity プロジェクトでキューブを作成するには、Unity での他のオブジェクトの作成と同様です。</span><span class="sxs-lookup"><span data-stu-id="df479-188">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="df479-189">Unity の座標系が現実の世界では約 1 メートルの Unity での 1 つのメーターが現実の世界にマップされるので、ユーザーの前にキューブを配置することは簡単です。</span><span class="sxs-lookup"><span data-stu-id="df479-189">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>
1. <span data-ttu-id="df479-190">左上隅にある、**階層**パネルで、**作成**ドロップダウン選択**3D オブジェクト > キューブ**します。</span><span class="sxs-lookup"><span data-stu-id="df479-190">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="df479-191">新しく作成された選択**キューブ**で、**階層**パネル</span><span class="sxs-lookup"><span data-stu-id="df479-191">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="df479-192">**インスペクター**検索、**変換**コンポーネントと変更**位置**に (**X**:0、 **Y**:0、 **Z**:2).</span><span class="sxs-lookup"><span data-stu-id="df479-192">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="df479-193">*配置キューブ 2 m 離れた、ユーザーの開始位置の前にします。*</span><span class="sxs-lookup"><span data-stu-id="df479-193">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="df479-194">**変換**コンポーネント、変更**回転**に (**X**:45、 **Y**:45、 **Z**:45) を変更して**スケール**に (**X**:0.25、 **Y**:0.25、 **Z**:0.25).</span><span class="sxs-lookup"><span data-stu-id="df479-194">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="df479-195">*これは、0.25 メーターにキューブをスケーリングします。*</span><span class="sxs-lookup"><span data-stu-id="df479-195">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="df479-196">シーンの変更を保存する次のように選択します。**ファイル > Save Scene**します。</span><span class="sxs-lookup"><span data-stu-id="df479-196">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="df479-197">デバイスでの Unity エディターから 5 -」の章を確認します</span><span class="sxs-lookup"><span data-stu-id="df479-197">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="df479-198">これで、キューブを作成しました、デバイスで簡単なチェックの実行時間を勧めします。</span><span class="sxs-lookup"><span data-stu-id="df479-198">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="df479-199">Unity エディター内から直接これを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="df479-199">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="df479-200">初期セットアップ</span><span class="sxs-lookup"><span data-stu-id="df479-200">Initial setup</span></span>
1. <span data-ttu-id="df479-201">Unity では、開発用 PC、開き**ファイル > Build Settings**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="df479-201">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="df479-202">変更**プラットフォーム**に**ユニバーサル Windows プラットフォーム**クリック**スイッチ プラットフォーム**</span><span class="sxs-lookup"><span data-stu-id="df479-202">Change **Platform** to **Universal Windows Platform** and click **Switch Platfrom**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="df479-203">HoloLens の Unity のリモート処理を使用して、</span><span class="sxs-lookup"><span data-stu-id="df479-203">For HoloLens use Unity Remoting</span></span>
1. <span data-ttu-id="df479-204">HoloLens にインストールし、実行、 [Holographic のリモート処理 Player](holographic-remoting-player.md)、Windows ストアから入手できます。</span><span class="sxs-lookup"><span data-stu-id="df479-204">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="df479-205">デバイスで、アプリケーションを起動し、待機状態を入力し、デバイスの IP アドレスを表示します。</span><span class="sxs-lookup"><span data-stu-id="df479-205">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="df479-206">Ip アドレスをメモします。</span><span class="sxs-lookup"><span data-stu-id="df479-206">Note down the IP.</span></span>
2. <span data-ttu-id="df479-207">開いている**ウィンドウ > XR > Holographic エミュレーション**します。</span><span class="sxs-lookup"><span data-stu-id="df479-207">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="df479-208">変更**エミュレーション モード**から**None**に**デバイスにリモート**します。</span><span class="sxs-lookup"><span data-stu-id="df479-208">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="df479-209">**リモート マシン**、前に説明した、HoloLens の IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="df479-209">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="df479-210">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="df479-210">Click **Connect**.</span></span>
6. <span data-ttu-id="df479-211">確認、**接続状態**緑色に変わります**接続**します。</span><span class="sxs-lookup"><span data-stu-id="df479-211">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="df479-212">今すぐクリック**再生**Unity エディターでします。</span><span class="sxs-lookup"><span data-stu-id="df479-212">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="df479-213">デバイスでは、エディターでキューブを表示できるようになりましたできます。</span><span class="sxs-lookup"><span data-stu-id="df479-213">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="df479-214">一時停止、オブジェクトを検査、およびデバッグのため、何が起こっているかは基本的に、エディターでのアプリを実行しているのと同じようですが、ビデオ、オーディオ、およびデバイスの入力、ホスト コンピューターとデバイス間のネットワーク経由で前後に送信できます。</span><span class="sxs-lookup"><span data-stu-id="df479-214">You can pause, inspect objects, and debug just like you are running an app in the editor, because that’s essentially what’s happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="df479-215">サポートされているその他の複合現実のヘッドセット</span><span class="sxs-lookup"><span data-stu-id="df479-215">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="df479-216">開発用 PC の USB ケーブルと、HDMI を使用して、ヘッドセットを接続またはケーブルのポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="df479-216">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="df479-217">起動、 **Mixed Reality ポータル**し、初回の実行を完了したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="df479-217">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="df479-218">、Unity から再生 ボタンを今すぐキーを押すことができます。</span><span class="sxs-lookup"><span data-stu-id="df479-218">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="df479-219">キューブの表示、mixed reality ヘッドセットおよびエディターを表示できるようになりましたできます。</span><span class="sxs-lookup"><span data-stu-id="df479-219">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="df479-220">第 6 章 - ビルドし、Visual Studio からデバイスへの配置</span><span class="sxs-lookup"><span data-stu-id="df479-220">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="df479-221">今すぐ Visual Studio にプロジェクトをコンパイルし、ターゲット デバイスにデプロイする準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="df479-221">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="df479-222">Visual Studio ソリューションへのエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="df479-222">Export to the Visual Studio solution</span></span>
1.  <span data-ttu-id="df479-223">開いている**ファイル > Build Settings**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="df479-223">Open **File > Build Settings** window.</span></span>
2.  <span data-ttu-id="df479-224">をクリックして**開くシーンを追加**シーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="df479-224">Click **Add Open Scenes** to add the scene.</span></span>
3.  <span data-ttu-id="df479-225">変更**プラットフォーム**に**ユニバーサル Windows プラットフォーム**クリック**スイッチ プラットフォーム**します。</span><span class="sxs-lookup"><span data-stu-id="df479-225">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
4.  <span data-ttu-id="df479-226">**Windows ストア**の設定により、 **SDK**は**ユニバーサル 10**します。</span><span class="sxs-lookup"><span data-stu-id="df479-226">In **Windows Store** settings ensure, **SDK** is **Universal 10**.</span></span>
5.  <span data-ttu-id="df479-227">ターゲット デバイスを選択したままに**任意のデバイス**閉塞表示またはスイッチを**HoloLens**します。</span><span class="sxs-lookup"><span data-stu-id="df479-227">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
6.  <span data-ttu-id="df479-228">**UWP のビルド タイプ**べき**D3D**します。</span><span class="sxs-lookup"><span data-stu-id="df479-228">**UWP Build Type** should be **D3D**.</span></span>
7.  <span data-ttu-id="df479-229">**UWP SDK**に残る可能性があります**インストールされている最新**します。</span><span class="sxs-lookup"><span data-stu-id="df479-229">**UWP SDK** could be left at **Latest installed**.</span></span>
8.  <span data-ttu-id="df479-230">確認**UnityC#プロジェクト**デバッギング中にします。</span><span class="sxs-lookup"><span data-stu-id="df479-230">Check **Unity C# Projects** under Debugging.</span></span>
9.  <span data-ttu-id="df479-231">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="df479-231">Click **Build**.</span></span>
10. <span data-ttu-id="df479-232">ファイル エクスプ ローラーでクリックして**新しいフォルダー**フォルダーの名前と **"App"** します。</span><span class="sxs-lookup"><span data-stu-id="df479-232">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
11. <span data-ttu-id="df479-233">**アプリ**フォルダーを選択すると、クリックして、**フォルダーの選択**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="df479-233">With the **App** folder selected, click the **Select Folder** button.</span></span>
12. <span data-ttu-id="df479-234">Unity が完了すると、Windows エクスプ ローラー ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="df479-234">When Unity is done building, a Windows File Explorer window will appear.</span></span>
13. <span data-ttu-id="df479-235">開く、**アプリ**エクスプ ローラーでフォルダー。</span><span class="sxs-lookup"><span data-stu-id="df479-235">Open the **App** folder in file explorer.</span></span>
14. <span data-ttu-id="df479-236">生成された Visual Studio ソリューション (この例では MixedRealityIntroduction.sln) を開きます</span><span class="sxs-lookup"><span data-stu-id="df479-236">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="df479-237">Visual Studio ソリューションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="df479-237">Compile the Visual Studio solution</span></span>

<span data-ttu-id="df479-238">最後に、エクスポートされた Visual Studio ソリューションをコンパイル、展開、およびデバイスでやってみてくださいいますが。</span><span class="sxs-lookup"><span data-stu-id="df479-238">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>
1. <span data-ttu-id="df479-239">ターゲットを Visual Studio で、上部のツールバーを使用して変更**デバッグ**に**リリース**との間**ARM**に**X86**します。</span><span class="sxs-lookup"><span data-stu-id="df479-239">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="df479-240">エミュレーターとデバイスに展開するための手順が異なります。</span><span class="sxs-lookup"><span data-stu-id="df479-240">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="df479-241">設定に一致する手順に従います。</span><span class="sxs-lookup"><span data-stu-id="df479-241">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="df479-242">Wi-fi 経由での複合現実デバイスへの配置します。</span><span class="sxs-lookup"><span data-stu-id="df479-242">Deploy to mixed reality device over Wi-Fi</span></span>
1. <span data-ttu-id="df479-243">横にある矢印をクリックして、**ローカル マシン**ボタンをクリックし、配置ターゲットを変更**リモート マシン**します。</span><span class="sxs-lookup"><span data-stu-id="df479-243">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="df479-244">複合現実デバイスの IP アドレスを入力し、変更**認証モード**HoloLens のユニバーサル (暗号化されていないプロトコル) へと**Windows**その他のデバイス。</span><span class="sxs-lookup"><span data-stu-id="df479-244">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="df479-245">クリックして**デバッグ > デバッグなしで開始**します。</span><span class="sxs-lookup"><span data-stu-id="df479-245">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="df479-246">**HoloLens の**これが初めてである場合、デバイスに展開して、次のようにペアにする必要が[Visual Studio を使用して](using-visual-studio.md)します。</span><span class="sxs-lookup"><span data-stu-id="df479-246">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="df479-247">USB 経由での複合現実デバイスに展開します。</span><span class="sxs-lookup"><span data-stu-id="df479-247">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="df479-248">USB ケーブルでデバイスが接続されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="df479-248">Ensure you device is plugged in via the USB cable.</span></span>
1. <span data-ttu-id="df479-249">**HoloLens の**、横にある矢印をクリックして、**ローカル マシン**ボタンをクリックし、配置ターゲットを変更**デバイス**します。</span><span class="sxs-lookup"><span data-stu-id="df479-249">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="df479-250">**PC に接続されている閉塞デバイスを対象とする**、ローカル コンピューターに、設定を保持します。</span><span class="sxs-lookup"><span data-stu-id="df479-250">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="df479-251">あることを確認、 **Mixed Reality ポータル**を実行します。</span><span class="sxs-lookup"><span data-stu-id="df479-251">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="df479-252">クリックして**デバッグ > デバッグなしで開始**します。</span><span class="sxs-lookup"><span data-stu-id="df479-252">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="df479-253">エミュレーターへのデプロイします。</span><span class="sxs-lookup"><span data-stu-id="df479-253">Deploy to Emulator</span></span>
1. <span data-ttu-id="df479-254">横にある矢印をクリックして、**デバイス**ボタン、および選択ドロップダウンから**HoloLens のエミュレーター**します。</span><span class="sxs-lookup"><span data-stu-id="df479-254">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="df479-255">クリックして**デバッグ > デバッグなしで開始**します。</span><span class="sxs-lookup"><span data-stu-id="df479-255">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="df479-256">アプリを試す</span><span class="sxs-lookup"><span data-stu-id="df479-256">Try out your app</span></span>

<span data-ttu-id="df479-257">これで、アプリをデプロイするは、キューブをすべて移動してみてくださいをする前に、世界内に保持することを確認します。</span><span class="sxs-lookup"><span data-stu-id="df479-257">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="df479-258">関連項目</span><span class="sxs-lookup"><span data-stu-id="df479-258">See also</span></span>
* [<span data-ttu-id="df479-259">Unity 開発の概要</span><span class="sxs-lookup"><span data-stu-id="df479-259">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="df479-260">Unity と Visual Studio を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="df479-260">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="df479-261">MR 基本 101</span><span class="sxs-lookup"><span data-stu-id="df479-261">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="df479-262">MR 基本 101E</span><span class="sxs-lookup"><span data-stu-id="df479-262">MR Basics 101E</span></span>](holograms-101e.md)
