---
title: Azure 空間アンカーチュートリアル-1. Azure 空間アンカーの概要
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, チュートリアル, hololens
ms.openlocfilehash: e62d3626ec6f2dbf8b66378212afab7db2f56422
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334449"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="a802f-105">1. Azure 空間アンカーの概要</span><span class="sxs-lookup"><span data-stu-id="a802f-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="a802f-106">概要</span><span class="sxs-lookup"><span data-stu-id="a802f-106">Overview</span></span>

<span data-ttu-id="a802f-107">2番目のシリーズの HoloLens 2 チュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="a802f-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="a802f-108">この3部構成のチュートリアルシリーズでは、Azure 空間アンカーの基礎について説明します。</span><span class="sxs-lookup"><span data-stu-id="a802f-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="a802f-109">この最初のチュートリアル「 [Azure 空間アンカーの概要](mrlearning-asa-ch1.md)」では、azure セッションを開始および停止し、1つのデバイスで azure アンカーを作成、アップロード、およびダウンロードするために必要なさまざまな手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="a802f-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="a802f-110">2番目のチュートリアル「 [Azure 空間アンカーの保存、取得、および共有](mrlearning-asa-ch2.md)」では、複数のアプリセッションにわたって Azure 空間アンカーを保存する方法について説明します。これは、HoloLens 2 のストレージにアンカー情報を保存し、このアンカー情報を複数デバイスのアンカーの配置用に他のデバイスに共有する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a802f-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="a802f-111">3番目のチュートリアル「 [Azure 空間アンカーフィードバックの表示](mrlearning-asa-ch3.md)」では、azure 空間アンカーを使用する場合のアンカーイベントと状態に関するフィードバックをユーザーに提供する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a802f-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="a802f-112">目標</span><span class="sxs-lookup"><span data-stu-id="a802f-112">Objectives</span></span>

* <span data-ttu-id="a802f-113">HoloLens 2 用の Azure 空間アンカーを使用した開発の基礎について説明します。</span><span class="sxs-lookup"><span data-stu-id="a802f-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="a802f-114">空間アンカーを作成、アップロード、ダウンロードする</span><span class="sxs-lookup"><span data-stu-id="a802f-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a802f-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="a802f-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="a802f-116">[概要チュートリアル](mrlearning-base.md)シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a802f-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="a802f-117">適切な[ツールがインストール](install-the-tools.md)されている WINDOWS 10 PC</span><span class="sxs-lookup"><span data-stu-id="a802f-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="a802f-118">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="a802f-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="a802f-119">基本的なC#プログラミング機能</span><span class="sxs-lookup"><span data-stu-id="a802f-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="a802f-120">[開発用に構成され](using-visual-studio.md#enabling-developer-mode)た HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="a802f-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="a802f-121">「[クイックスタート: Azure 空間アンカーを使用した Unity HoloLens アプリの作成](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)」チュートリアルの「[空間アンカーリソースの作成](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクションを完了します。</span><span class="sxs-lookup"><span data-stu-id="a802f-121">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

>[!IMPORTANT]
><span data-ttu-id="a802f-122">このチュートリアルシリーズでは<a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019.1</a>が必要であり、推奨されるバージョンは unity 2019.1.14 です。</span><span class="sxs-lookup"><span data-stu-id="a802f-122">This tutorial series requires <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019.1</a> and the recommended version is Unity 2019.1.14.</span></span> <span data-ttu-id="a802f-123">これは、前にリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="a802f-123">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="a802f-124">Unity プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="a802f-124">Creating the Unity project</span></span>

<span data-ttu-id="a802f-125">このセクションでは、新しい Unity プロジェクトを作成し、Windows Mixed Reality 用に構成します。</span><span class="sxs-lookup"><span data-stu-id="a802f-125">In this section, you will create a new Unity project and configure it for Windows Mixed Reality.</span></span>

1. <span data-ttu-id="a802f-126">Unity プロジェクトを作成し、 _Azure 空間アンカーチュートリアル_などの適切な名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="a802f-126">Create a Unity project and give it a suitable name, for example, _Azure Spatial Anchors tutorial_.</span></span>

2. <span data-ttu-id="a802f-127">Windows Mixed Reality の Unity プロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="a802f-127">Configure the Unity project for Windows Mixed Reality.</span></span>

    >[!TIP]
    ><span data-ttu-id="a802f-128">Unity プロジェクトを作成し、Windows Mixed Reality 用に構成する方法について[は、「](mrlearning-base-ch1.md#create-new-unity-project)プロジェクトの初期化」と「最初のアプリケーションのチュートリアル[」シリーズの](mrlearning-base.md)「プロジェクトの初期化」と「[最初のアプリケーション](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1)の[構成](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a802f-128">For a reminder on how to create a Unity project and configure it for Windows Mixed Reality, you can refer to the [Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and the [Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="a802f-129">組み込み Unity パッケージの追加</span><span class="sxs-lookup"><span data-stu-id="a802f-129">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="a802f-130">このセクションでは、プロジェクトで使用するツールキットと Sdk に必要な組み込みの Unity アセットとパッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="a802f-130">In this section, you will add inbuilt Unity assets and packages required by the toolkits and SDKs you will be using in the project.</span></span>

1. <span data-ttu-id="a802f-131">TMP の重要なリソースをインポートします。</span><span class="sxs-lookup"><span data-stu-id="a802f-131">Import TMP Essential Resources.</span></span>

    >[!NOTE]
    ><span data-ttu-id="a802f-132">このパッケージは、Mixed Reality Toolkit によって要求されているため、追加しています。</span><span class="sxs-lookup"><span data-stu-id="a802f-132">We are adding this package because it is required by the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="a802f-133">Unity メニューで、[ **Window** > **TextMeshPro** ] を選択し > **TMP 必須リソースをインポート**します。</span><span class="sxs-lookup"><span data-stu-id="a802f-133">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.1.png)

    <span data-ttu-id="a802f-135">Unity パッケージのインポート ポップアップウィンドウで、まず **すべて** をクリックしてすべてのアセットを選択し、**インポート** ボタンをクリックしてアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="a802f-135">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.2.png)

2. <span data-ttu-id="a802f-137">AR Foundation をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a802f-137">Install AR Foundation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="a802f-138">このパッケージは Azure 空間アンカー SDK で必要とされるため、追加しています。</span><span class="sxs-lookup"><span data-stu-id="a802f-138">We are adding this package because it is required by the Azure Spatial Anchors SDK.</span></span>

    <span data-ttu-id="a802f-139">Unity メニューで、[**ウィンドウ** > **パッケージマネージャー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a802f-139">In the Unity menu, select **Window** > **Package Manager**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.1.png)

    <span data-ttu-id="a802f-141">パッケージマネージャー ウィンドウで、 **AR Foundation** を選択し、**インストール** ボタンをクリックしてパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="a802f-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button.</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="a802f-142">この一覧には、AR Foundation パッケージが表示されるまでに数秒かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="a802f-142">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="a802f-144">チュートリアル資産のインポート</span><span class="sxs-lookup"><span data-stu-id="a802f-144">Importing the tutorial assets</span></span>

<span data-ttu-id="a802f-145">このセクションでは、すべてのチュートリアル資産をダウンロードしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="a802f-145">In this section, you will download and import all the tutorial assets.</span></span>

1. <span data-ttu-id="a802f-146">アセットをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="a802f-146">Download the assets.</span></span>

    * <span data-ttu-id="a802f-147">[AzureSpatialAnchors unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (バージョン 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="a802f-147">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>
    * [<span data-ttu-id="a802f-148">MixedReality. 2.1.0. unitypackage のようになります。</span><span class="sxs-lookup"><span data-stu-id="a802f-148">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [<span data-ttu-id="a802f-149">MRTK。HoloLens2. 2.1.0.1. unitypackage を実行します。</span><span class="sxs-lookup"><span data-stu-id="a802f-149">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [<span data-ttu-id="a802f-150">MRTK。HoloLens2. AzureSpatialAnchors. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="a802f-150">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. <span data-ttu-id="a802f-151">アセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="a802f-151">Import the assets.</span></span>

    <span data-ttu-id="a802f-152">Unity メニューで、[ **Assets** > **Import Package** > **カスタムパッケージ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a802f-152">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.1.png)

    <span data-ttu-id="a802f-154">Import package... (パッケージのインポート)...ポップアップウィンドウで、 **AzureSpatialAnchors unitypackage**を選択し、**開く** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a802f-154">In the Import package... pop-up window, select the **AzureSpatialAnchors.unitypackage** and click the **Open** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.2.png)

    <span data-ttu-id="a802f-156">Unity パッケージのインポート ポップアップウィンドウで、まず **すべて** をクリックしてすべてのアセットを選択し、**インポート** ボタンをクリックしてアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="a802f-156">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.3.png)

    <span data-ttu-id="a802f-158">残りのアセットパッケージをインポートするには、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="a802f-158">Repeat these steps to import the remaining asset packages.</span></span> <span data-ttu-id="a802f-159">完了すると、Unity プロジェクトの**Assets**フォルダーにこれらのサブフォルダーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a802f-159">Once complete, your Unity project's **Assets** folder should contain these sub-folders.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="a802f-161">シーンの作成と準備</span><span class="sxs-lookup"><span data-stu-id="a802f-161">Creating and preparing the scene</span></span>

<span data-ttu-id="a802f-162">このセクションでは、Mixed Reality Toolkit といくつかのチュートリアル prefabs を追加して、シーンの作成と準備を行います。</span><span class="sxs-lookup"><span data-stu-id="a802f-162">In this section, you will create and prepare the scene by adding the Mixed Reality Toolkit and some of the tutorial prefabs.</span></span>

1. <span data-ttu-id="a802f-163">新しいシーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="a802f-163">Create a new scene.</span></span>

    <span data-ttu-id="a802f-164">Unity メニューで、[**ファイル** > **新しいシーン**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a802f-164">In the Unity menu, select **File** > **New Scene**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.1.png)

    <span data-ttu-id="a802f-166">Unity メニューで、[**ファイル** > **名前を付けて保存...** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a802f-166">In the Unity menu, select **File** > **Save As...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.2.png)

    <span data-ttu-id="a802f-168">シーンの保存 ポップアップウィンドウで、プロジェクトの **シーン** フォルダーに移動し、シーンに適切な名前 ( _ASATutorialScene_など) を付けて、**保存** ボタンをクリックしてシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="a802f-168">In the Save Scene pop-up window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _ASATutorialScene_, and save the scene by clicking the **Save** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    ><span data-ttu-id="a802f-170">シーンは、プロジェクトの Assets フォルダー内にある限り、任意の場所に保存できます。</span><span class="sxs-lookup"><span data-stu-id="a802f-170">You can save the scene anywhere you like as long as it is inside the project's Assets folder.</span></span> <span data-ttu-id="a802f-171">ただし、プロジェクトを整理し続けるには、通常、プロジェクトの [シーン] フォルダーに保存することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a802f-171">However, to keep your project organized, it's generally recommended to save it in the project's Scenes folder.</span></span>

2. <span data-ttu-id="a802f-172">Mixed Reality Toolkit を追加します。</span><span class="sxs-lookup"><span data-stu-id="a802f-172">Add the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="a802f-173">Unity メニューで、 **[Mixed Reality Toolkit]** を選択し > [**シーンに追加] と [構成...** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a802f-173">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.1.png)

    <span data-ttu-id="a802f-175">[Select MixedRealityToolkitConfigurationProfile] ポップアップウィンドウで、 **DefaultHoloLens2ConfigurationProfile**をクリックして、シーンの MRTK 構成プロファイルとして設定します。</span><span class="sxs-lookup"><span data-stu-id="a802f-175">In the Select MixedRealityToolkitConfigurationProfile pop-up window, click the **DefaultHoloLens2ConfigurationProfile** to set it as the scene's MRTK configuration profile.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.2.png)

    <span data-ttu-id="a802f-177">Unity メニューで、[**ファイル** > **保存**] を選択してシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="a802f-177">In the Unity menu, select **File** > **Save** to save the scene.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    ><span data-ttu-id="a802f-179">このチュートリアルで作業するときに、キーボードショートカットの CTRL + S (macOS のコマンド + S) を使用して、シーンをすばやく保存できます。</span><span class="sxs-lookup"><span data-stu-id="a802f-179">You can use the keyboard shortcut CTRL+S (command + S on macOS) to quickly save your scene as you are working through this tutorial.</span></span>

3. <span data-ttu-id="a802f-180">チュートリアル prefabs を追加します。</span><span class="sxs-lookup"><span data-stu-id="a802f-180">Add the tutorial prefabs.</span></span>

    <span data-ttu-id="a802f-181">[プロジェクト] パネルで、[**アセット** > **mrtk] に移動します。AzureSpatialAnchors** > **Prefabs**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="a802f-181">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="a802f-182">CTRL ボタンを押したまま (macOS の場合はコマンド)、 **[Buttonparent]** 、 **[debugwindow]** 、および **[parentanchor]** をクリックして、3つの prefabs を選択します。</span><span class="sxs-lookup"><span data-stu-id="a802f-182">While holding down the CTRL button (command on macOS), click on **ButtonParent**, **DebugWindow**, and **ParentAnchor** to select the three prefabs.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.1.png)

    <span data-ttu-id="a802f-184">3つの prefabs を選択したまま、[階層] パネルにドラッグしてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="a802f-184">With the three prefabs still selected, drag them into the Hierarchy panel to add them to the scene.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.2.png)

    <span data-ttu-id="a802f-186">シーン内のオブジェクトに焦点を当てるには、ParentAnchor オブジェクトをダブルクリックして、もう一度もう一度ズームします。</span><span class="sxs-lookup"><span data-stu-id="a802f-186">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    ><span data-ttu-id="a802f-188">シーンに大きいアイコンが見られる場合 (たとえば、大きなフレーム \ ' アイコンが煩雑である場合)、ギズモを off の位置に<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">切り替える</a>ことによって、これらを非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a802f-188">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="a802f-189">シーンを操作するためのボタンの構成</span><span class="sxs-lookup"><span data-stu-id="a802f-189">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="a802f-190">このセクションでは、prefabs とスクリプトをシーンに追加して、アプリケーションでローカルアンカーと Azure 空間アンカーの両方が動作する方法の基礎を示す一連のボタンを作成します。</span><span class="sxs-lookup"><span data-stu-id="a802f-190">In this section, you will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

1. <span data-ttu-id="a802f-191">Pressable Button Holo レンズ 2 (スクリプト) コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="a802f-191">Configure the Pressable Button Holo Lens 2 (script) component.</span></span>

    <span data-ttu-id="a802f-192">[階層] パネルで、 **Buttonparent**オブジェクトを展開し、 **StartAzureSession**という名前の最初の子オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="a802f-192">In the Hierarchy panel, expand the **ButtonParent** object and select the first child object named **StartAzureSession**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.1.png)

    <span data-ttu-id="a802f-194">[インスペクター] パネルで、[ **Pressable] ボタン Holo レンズ 2 (script)** コンポーネントまで下にスクロールし、[ **+** ] アイコンをクリックして、**ボタン押下 ()** イベントに新しいイベントリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="a802f-194">In the Inspector panel, scroll down to the **Pressable Button Holo Lens 2 (script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.2.png)

    <span data-ttu-id="a802f-196">階層 パネルで StartAzureSession オブジェクトを選択した状態で、階層 パネルから**Parentanchor**オブジェクトをクリックして、追加したイベントリスナーの空の**なし (オブジェクト)**  フィールドに移動します。これにより、このボタンからボタンの押されたイベントを、parentanchor オブジェクトがリッスンするようになります。</span><span class="sxs-lookup"><span data-stu-id="a802f-196">With the StartAzureSession object still selected in the Hierarchy panel, click-and-drag the **ParentAnchor** object from the Hierarchy panel into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.3.png)

    <span data-ttu-id="a802f-198">同じイベントリスナーの **[関数なし]** ドロップダウンをクリックし、[ **AnchorModuleScript** > **StartAzureSession ()** ] を選択して、このボタンからボタンを押したイベントが発生したときにトリガーされるアクションとして StartAzureSession () 関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="a802f-198">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.4.png)

2. <span data-ttu-id="a802f-200">対話型 (スクリプト) コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="a802f-200">Configure the Interactable (script) component.</span></span>

    <span data-ttu-id="a802f-201">階層 パネルで StartAzureSession オブジェクトを選択した状態で、インスペクター パネルの **対話型 (スクリプト)** コンポーネントまで下にスクロールし、**OnClick ()** イベントに対して上記の手順1と同じ手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="a802f-201">With the StartAzureSession object still selected in the Hierarchy panel, in the Inspector panel, scroll down to the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-2.1.png)

3. <span data-ttu-id="a802f-203">残りのボタンを構成する</span><span class="sxs-lookup"><span data-stu-id="a802f-203">Configure the remaining buttons</span></span>

    <span data-ttu-id="a802f-204">残りの各ボタンについて、上記の手順 1. と 2. で説明したプロセスを完了して、次のボタンが押された () イベントと OnClick () イベントの両方に関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a802f-204">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the Button Pressed () and OnClick () events following:</span></span>

    * <span data-ttu-id="a802f-205">**Stopazuresession**オブジェクトの場合は、 **stopazuresession ()** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a802f-205">For the **StopAzureSession** object, assign the **StopAzureSession()** function.</span></span>
    * <span data-ttu-id="a802f-206">**Createanchor**オブジェクトの場合は、 **createazureanchor ()** 関数を割り当ててから、 **Parentanchor**を [空の**なし (ゲームオブジェクト)** ] フィールドにもう一度ドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a802f-206">For the **CreateAnchor** object, assign the **CreateAzureAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
    * <span data-ttu-id="a802f-207">アンカーオブジェクト**の検索を開始**するには、 **findazureanchor ()** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a802f-207">For the **Start Looking for Anchor** object, assign the **FindAzureAnchor()** function.</span></span>
    * <span data-ttu-id="a802f-208">**Delete Azure anchor**オブジェクトの場合は、 **deleteazureanchor ()** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a802f-208">For the **Delete Azure Anchor** object, assign the **DeleteAzureAnchor()** function.</span></span>
    * <span data-ttu-id="a802f-209">**Delete Local anchor**オブジェクトの場合は、 **removelocalanchor ()** 関数を割り当ててから、 **Parentanchor**を [空の**なし (ゲームオブジェクト)** ] フィールドにもう一度ドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a802f-209">For the **Delete Local Anchor** object, assign the **RemoveLocalAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>

4. <span data-ttu-id="a802f-210">シーンを Azure リソースに接続する</span><span class="sxs-lookup"><span data-stu-id="a802f-210">Connect the scene to the Azure resource</span></span>

    <span data-ttu-id="a802f-211">階層 パネルで**parentanchor**オブジェクトを選択し、インスペクター パネルで **空間アンカーマネージャー (スクリプト)** コンポーネントまでスクロールします。</span><span class="sxs-lookup"><span data-stu-id="a802f-211">In the Hierarchy panel, select the **ParentAnchor** object and in the Inspector panel, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

    <span data-ttu-id="a802f-212">次に、 **[資格情報]** セクションで、空間アンカーアカウント Id とキーを、対応する**空間アンカーアカウント Id**と**空間アンカーアカウントキー**フィールドに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a802f-212">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields.</span></span>

    >[!NOTE]
    ><span data-ttu-id="a802f-213">このチュートリアルの[前提条件](mrlearning-asa-ch1.md#prerequisites)の一部として、空間アンカーアカウント Id とキーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="a802f-213">You created your Spatial Anchors Account Id and Key as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites).</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    ><span data-ttu-id="a802f-215">シーンを保存していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a802f-215">Make sure you save your scene.</span></span>

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="a802f-216">Azure 空間アンカーの基本的な動作を試す</span><span class="sxs-lookup"><span data-stu-id="a802f-216">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="a802f-217">これで、Azure 空間アンカーの基本を示すようにシーンが構成されたので、Azure 空間アンカーじを体験できるようにアプリをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="a802f-217">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

1. <span data-ttu-id="a802f-218">必要な機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="a802f-218">Add additional required capabilities.</span></span>

    <span data-ttu-id="a802f-219">[Unity] メニューの [**プロジェクト設定**の > **編集**] を選択して、[プレーヤーの設定] パネルを開きます。</span><span class="sxs-lookup"><span data-stu-id="a802f-219">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings panel.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.1.png)

    <span data-ttu-id="a802f-221">プレーヤーの 設定 パネルで、**プレーヤー**、**設定の発行** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="a802f-221">In the Player Settings panel, select **Player** and then **Publishing Settings**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.2.png)

    <span data-ttu-id="a802f-223">**[発行の設定]** で、 **[機能]** セクションまで下にスクロールし、チュートリアルの最初にプロジェクトを作成したときに有効にした**SpatialPerception**が有効になっていることを再度確認します。</span><span class="sxs-lookup"><span data-stu-id="a802f-223">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that **SpatialPerception**, which you enabled when you created the project at the beginning of the tutorial, is enabled.</span></span> <span data-ttu-id="a802f-224">次に、 **Internetclient**、 **internetclientserver**、 **PrivateNetworkClientServer**、 **Removablestorage**、 **Webcam**、および**マイク**機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="a802f-224">Then, enabled the **InternetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **Webcam**, and **Microphone** capabilities.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.3.png)

2. <span data-ttu-id="a802f-226">アプリを HoloLens 2 にデプロイします。</span><span class="sxs-lookup"><span data-stu-id="a802f-226">Deploy the app to your HoloLens 2.</span></span>

    >[!TIP]
    ><span data-ttu-id="a802f-227">HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、「[入門チュートリアル](mrlearning-base.md)」シリーズの一部である「[プロジェクトの初期化」および「最初のアプリケーション](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1)のチュートリアル」の「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a802f-227">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

3. <span data-ttu-id="a802f-228">アプリを実行し、アプリ内の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="a802f-228">Run the app and follow the in-app instructions.</span></span>

    >[!CAUTION]
    ><span data-ttu-id="a802f-229">Azure 空間アンカーは、インターネットを使用してアンカーデータを保存して読み込みます。そのため、デバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a802f-229">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

    <span data-ttu-id="a802f-230">アプリケーションがデバイスで実行されている場合は、 **Azure 空間アンカーモジュール**の [命令] パネルに表示される画面の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="a802f-230">When the application is running on your device, follow the on-screen instructions displayed on the **Azure Spatial Anchor Module Instructions** panel.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="a802f-232">エクスペリエンスを固定する</span><span class="sxs-lookup"><span data-stu-id="a802f-232">Anchoring an experience</span></span>

<span data-ttu-id="a802f-233">前のセクションでは、Azure 空間アンカーの基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="a802f-233">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="a802f-234">キューブを使用して、アタッチされたアンカーで親ゲームオブジェクトを表現し、視覚化しています。</span><span class="sxs-lookup"><span data-stu-id="a802f-234">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="a802f-235">このセクションでは、ParentAnchor オブジェクトの子として配置することで、エクスペリエンス全体を固定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a802f-235">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

1. <span data-ttu-id="a802f-236">ロケットランチャーエクスペリエンスを追加します。</span><span class="sxs-lookup"><span data-stu-id="a802f-236">Add the Rocket Launcher experience.</span></span>

    <span data-ttu-id="a802f-237">[プロジェクト] パネルで、[**アセット** > **mrtk] に移動します。チュートリアル。 GettingStarted** **Prefabs**フォルダーを起動し、**ロケット Launcher_Complete** prefab を選択します。</span><span class="sxs-lookup"><span data-stu-id="a802f-237">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder and select the **Rocket Launcher_Complete** prefab.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.1.png)

    <span data-ttu-id="a802f-239">ロケット Launcher_Complete prefab を選択したまま、[階層] パネルの**Parentanchor**オブジェクトの上にドラッグして、parentanchor オブジェクトの子にします。</span><span class="sxs-lookup"><span data-stu-id="a802f-239">With the Rocket Launcher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy panel to make it a child of the ParentAnchor object.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.2.png)

2. <span data-ttu-id="a802f-241">ロケットランチャーエクスペリエンスの位置を変更します。</span><span class="sxs-lookup"><span data-stu-id="a802f-241">Reposition the Rocket Launcher experience.</span></span>

    <span data-ttu-id="a802f-242">**Parentanchor** (キューブ) が引き続き公開されるように、モジュールの**ロケット Launcher_Complete**オブジェクトを移動します。</span><span class="sxs-lookup"><span data-stu-id="a802f-242">Move module **Rocket Launcher_Complete** object so that the **ParentAnchor** (the cube) is still exposed.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-2.1.png)

    <span data-ttu-id="a802f-244">アプリケーションでは、ユーザーがキューブを移動して、ロケットランチャーエクスペリエンス全体を再配置できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a802f-244">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

    >[!TIP]
    ><span data-ttu-id="a802f-245">再配置オブジェクト (このチュートリアルで使用されるキューブなど) の使用、エクスペリエンスを示すボタンの使用、画面の位置と回転の使用など、さまざまな操作を行うためのさまざまなユーザーエクスペリエンスフローがあります。ギズモなど。</span><span class="sxs-lookup"><span data-stu-id="a802f-245">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a802f-246">結論</span><span class="sxs-lookup"><span data-stu-id="a802f-246">Congratulations</span></span>

<span data-ttu-id="a802f-247">このチュートリアルでは、Azure 空間アンカーの基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="a802f-247">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="a802f-248">このレッスンでは、Azure セッションを開始および停止するために必要なさまざまな手順を説明し、1つのデバイスに azure のアンカーを作成、アップロード、ダウンロードするためのボタンをいくつか紹介しました。</span><span class="sxs-lookup"><span data-stu-id="a802f-248">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session and create, upload and download azure anchors on a single device.</span></span>

<span data-ttu-id="a802f-249">次のレッスンでは、アプリケーションを再起動した後でも、Azure anchor Id を HoloLens 2 に保存し、複数のデバイス間でアンカー Id を転送して空間アラインメントを実現する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a802f-249">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="a802f-250">次のレッスン: 2. Azure 空間アンカーの保存、取得、共有</span><span class="sxs-lookup"><span data-stu-id="a802f-250">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
