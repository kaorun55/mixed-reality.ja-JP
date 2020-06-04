---
title: Azure Spatial Anchors チュートリアル - 1. Azure Spatial Anchors をお使いになる前に
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 2a171d601d094375a56734e8d7890c9d3e17c887
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866912"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="8b139-105">1.Azure Spatial Anchors をお使いになる前に</span><span class="sxs-lookup"><span data-stu-id="8b139-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="8b139-106">概要</span><span class="sxs-lookup"><span data-stu-id="8b139-106">Overview</span></span>

<span data-ttu-id="8b139-107">HoloLens 2 チュートリアルのシリーズ 2 へようこそ。</span><span class="sxs-lookup"><span data-stu-id="8b139-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="8b139-108">この 4 部構成のチュートリアル シリーズでは、Azure Spatial Anchors の基礎について学習します。</span><span class="sxs-lookup"><span data-stu-id="8b139-108">In this four-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="8b139-109">この最初のチュートリアル「[Azure Spatial Anchors をお使いになる前に](mrlearning-asa-ch1.md)」では、Azure セッションの開始と停止、単一のデバイス上での Azure アンカーの作成、アップロード、ダウンロードに必要なさまざまな手順を学習します。</span><span class="sxs-lookup"><span data-stu-id="8b139-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="8b139-110">2 番目のチュートリアル「[Azure Spatial Anchors の保存、取得、および共有](mrlearning-asa-ch2.md)」では、HoloLens 2 のストレージにアンカー情報を保存することで、複数のアプリ セッションにわたって Azure Spatial Anchors を保存する方法と、このアンカー情報を他のデバイスと共有して複数のデバイスのアンカー位置合わせを行う方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="8b139-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="8b139-111">3 番目のチュートリアル「[Azure Spatial Anchors フィードバックの表示](mrlearning-asa-ch3.md)」では、Azure Spatial Anchors を使用する際のアンカーのイベントと状態に関するフィードバックをユーザーに提供する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="8b139-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="8b139-112">4 番目のチュートリアル「[Android と iOS 用の Azure Spatial Anchors](mrlearning-asa-ch4.md)」では、プロジェクトをビルドして、Android デバイスや iOS デバイス用にデプロイする方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="8b139-112">In the fourth tutorial, [Azure Spatial Anchors for Android and iOS](mrlearning-asa-ch4.md), you will learn how to build and deploy your project to Android and iOS devices.</span></span>

## <a name="objectives"></a><span data-ttu-id="8b139-113">目標</span><span class="sxs-lookup"><span data-stu-id="8b139-113">Objectives</span></span>

* <span data-ttu-id="8b139-114">HoloLens 2 用の Azure Spatial Anchors を使用した開発の基礎について学習する</span><span class="sxs-lookup"><span data-stu-id="8b139-114">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="8b139-115">空間アンカーを作成、アップロード、ダウンロードする</span><span class="sxs-lookup"><span data-stu-id="8b139-115">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8b139-116">前提条件</span><span class="sxs-lookup"><span data-stu-id="8b139-116">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="8b139-117">[入門チュートリアル](mrlearning-base.md) シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8b139-117">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="8b139-118">正しい[ツールがインストールされている](install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="8b139-118">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="8b139-119">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="8b139-119">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="8b139-120">基本的な C# プログラミング能力</span><span class="sxs-lookup"><span data-stu-id="8b139-120">Some basic C# programming ability</span></span>
* <span data-ttu-id="8b139-121">[開発用に構成された](using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="8b139-121">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="8b139-122">Unity 2019.2.X がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="8b139-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="8b139-123">「[Spatial Anchors リソースを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクション ([クイック スタート:Azure Spatial Anchors を使用する Unity HoloLens アプリを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) チュートリアルにあります) を完了します。</span><span class="sxs-lookup"><span data-stu-id="8b139-123">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="8b139-124">Android 用にデプロイする場合</span><span class="sxs-lookup"><span data-stu-id="8b139-124">If you intend to deploy to Android</span></span>
    * <span data-ttu-id="8b139-125">Windows コンピューターか macOS コンピューターに USB 接続された、<a href="https://developer.android.com/studio/debug/dev-options" target="_blank">開発者向けオプションが有効</a>に設定された <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 対応</a>の Android デバイス</span><span class="sxs-lookup"><span data-stu-id="8b139-125">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
    * <span data-ttu-id="8b139-126">Unity 2019.2.X がインストールされ、Android ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="8b139-126"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Android Build Support module added</span></span>
* <span data-ttu-id="8b139-127">iOS 用にデプロイする場合</span><span class="sxs-lookup"><span data-stu-id="8b139-127">If you intend to deploy to iOS</span></span>
    * <span data-ttu-id="8b139-128"><a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> および <a href="https://cocoapods.org" target="_blank">CocoaPods</a> の最新バージョンがインストールされた macOS コンピューター</span><span class="sxs-lookup"><span data-stu-id="8b139-128">A macOS computer with the the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
    * <span data-ttu-id="8b139-129">macOS コンピューターに USB 接続された、<a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 互換</a> iOS デバイス</span><span class="sxs-lookup"><span data-stu-id="8b139-129">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
    * <span data-ttu-id="8b139-130">Unity 2019.2.X がインストールされ、iOS ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="8b139-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the iOS Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b139-131">このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.2.X です。</span><span class="sxs-lookup"><span data-stu-id="8b139-131">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="8b139-132">これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="8b139-132">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="8b139-133">Unity プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="8b139-133">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

<span data-ttu-id="8b139-134">このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備します。</span><span class="sxs-lookup"><span data-stu-id="8b139-134">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="8b139-135">このためには、まず「[プロジェクトと最初のアプリケーションの初期化](mrlearning-base-ch1.md)」に従ってください (「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」の手順は除く)。これには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8b139-135">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="8b139-136">[新しい Unity プロジェクトを作成](mrlearning-base-ch1.md#create-new-unity-project)して、適切な名前を付ける (たとえば、*MRTK Tutorials*)</span><span class="sxs-lookup"><span data-stu-id="8b139-136">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="8b139-137">Windows Mixed Reality 用に Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="8b139-137">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="8b139-138">TextMesh Pro の Essential Resources (重要なリソース) をインポートする</span><span class="sxs-lookup"><span data-stu-id="8b139-138">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="8b139-139">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="8b139-139">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="8b139-140">Mixed Reality Toolkit 用に Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="8b139-140">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="8b139-141">[Mixed Reality Toolkit を Unity シーンに追加](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)し、シーンに適切な名前を付ける (たとえば、*AzureSpatialAnchors*)</span><span class="sxs-lookup"><span data-stu-id="8b139-141">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="8b139-142">次に、「[Mixed Reality Toolkit プロファイルを構成する方法 (空間認識表示オプションの変更)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)」の手順に従って、シーンの MRTK 構成プロファイルを **[DefaultHoloLens2ConfigurationProfile]** に変更し、空間認識メッシュの表示オプションを **[Occlusion]\(オクルージョン\)** に変更します。</span><span class="sxs-lookup"><span data-stu-id="8b139-142">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="8b139-143">上のリンクの「[Mixed Reality Toolkit 用に Unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)」の手順で述べられているように、MSBuild for Unity を有効にしないことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8b139-143">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="8b139-144">組み込み Unity パッケージの追加</span><span class="sxs-lookup"><span data-stu-id="8b139-144">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="8b139-145">このセクションでは、Unity の組み込み AR Foundation パッケージをインストールします。これは、次のセクションでインポートする Azure Spatial Anchors SDK で必要になるためです。</span><span class="sxs-lookup"><span data-stu-id="8b139-145">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="8b139-146">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8b139-146">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="8b139-148">AR Foundation パッケージが一覧に表示されるまでに数秒かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="8b139-148">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="8b139-149">[Package Manager]\(パッケージ マネージャー\) ウィンドウで、 **[AR Foundation]** を選択し、 **[Install]\(インストール\)** ボタンをクリックしてパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="8b139-149">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="8b139-151">チュートリアルのアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="8b139-151">Importing the tutorial assets</span></span>

<span data-ttu-id="8b139-152">次の Unity カスタム パッケージを、**記載されている順で**ダウンロードして**インポート**します。</span><span class="sxs-lookup"><span data-stu-id="8b139-152">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="8b139-153">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (バージョン 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="8b139-153">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="8b139-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="8b139-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="8b139-155">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="8b139-155">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)

> [!TIP]
> <span data-ttu-id="8b139-156">Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b139-156">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="8b139-157">チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8b139-157">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="8b139-159">シーンの作成と準備</span><span class="sxs-lookup"><span data-stu-id="8b139-159">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="8b139-160">このセクションでは、チュートリアルのプレハブをいくつか追加してシーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="8b139-160">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="8b139-161">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.AzureSpatialAnchors]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="8b139-161">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="8b139-162">Ctrl ボタンを押したまま、 **[ButtonParent]** 、 **[DebugWindow]** 、 **[Instructions]** 、および **[ParentAnchor]** をクリックして 4 つのプレハブを選択します。</span><span class="sxs-lookup"><span data-stu-id="8b139-162">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="8b139-164">4 つのプレハブを選択したまま、[Hierarchy]\(階層\) ウィンドウにドラッグしてこれらをシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="8b139-164">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="8b139-166">シーン内のオブジェクトに焦点を合わせるには、ParentAnchor オブジェクトをダブルクリックして、もう一度少しズームアウトします。</span><span class="sxs-lookup"><span data-stu-id="8b139-166">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="8b139-168">シーンに大きいアイコンが表示されている場合 (たとえば、大きいフレームの 'T' アイコンが邪魔になる場合)、<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">ギズモをオフに切り替える</a>ことによってこれらを非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="8b139-168">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="8b139-169">シーンを操作するためのボタンの構成</span><span class="sxs-lookup"><span data-stu-id="8b139-169">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="8b139-170">このセクションでは、スクリプトをシーンに追加して、ローカル アンカーと Azure Spatial Anchors の両方がアプリケーションでどのように動作するかの基本を示す一連のボタン イベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="8b139-170">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="8b139-171">1.Pressable Button Holo Lens 2 (Script) コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="8b139-171">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="8b139-172">[Hierarchy]\(階層\) ウィンドウで **[ButtonParent]** オブジェクトを展開し、 **[StartAzureSession]** という名前の最初の子オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="8b139-172">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="8b139-174">[Inspector]\(インスペクター\) ウィンドウで **Pressable Button Holo Lens 2 (Script)** コンポーネントを見つけ、 **+** アイコンをクリックして、**Button Pressed ()** イベントに新しいイベント リスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="8b139-174">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="8b139-176">[Hierarchy]\(階層\) ウィンドウで [StartAzureSession] オブジェクトを選択した状態で、[Hierarchy]\(階層\) ウィンドウの **[ParentAnchor]** オブジェクトをクリックして、先ほど追加したイベント リスナーの空の **[None (Object)]\(なし (オブジェクト)\)** フィールドにドラッグして、このボタンで押されたボタン イベントを ParentAnchor オブジェクトがリッスンするようにします。</span><span class="sxs-lookup"><span data-stu-id="8b139-176">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="8b139-178">同じイベント リスナーの **[No Function]\(関数なし\)** ドロップダウンをクリックし、 **[AnchorModuleScript]**  >  **[StartAzureSession ()]** を選択して、このボタンで押されたボタン イベントが発生したときにトリガーされるアクションとして StartAzureSession () 関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="8b139-178">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="8b139-180">2.Interactable (Script) コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="8b139-180">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="8b139-181">[Hierarchy]\(階層\) ウィンドウで [StartAzureSession] オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを見つけ、**OnClick ()** イベントについて上記の手順 1 と同じプロセス繰り返します。</span><span class="sxs-lookup"><span data-stu-id="8b139-181">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="8b139-183">3.残りのボタンを構成する</span><span class="sxs-lookup"><span data-stu-id="8b139-183">3. Configure the remaining buttons</span></span>

<span data-ttu-id="8b139-184">残りの各ボタンについて、上記の手順 1 と手順 2 で説明したプロセスを完了して、**Button Pressed ()** と **OnClick ()** イベントの両方に関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8b139-184">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="8b139-185">**[StopAzureSession]** オブジェクトについては、[AnchorModuleScript] > **[StopAzureSession ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8b139-185">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="8b139-186">**[CreateAzureAnchor]** オブジェクトについては、[AnchorModuleScript] > **[CreateAzureAnchor ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8b139-186">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="8b139-187">次に、 **[ParentAnchor]** を空の **[None (Game Object)]\(なし (ゲーム オブジェクト)\)** フィールドにもう一度ドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8b139-187">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="8b139-188">**[RemoveLocalAnchor]** オブジェクトについては、[AnchorModuleScript] > **[RemoveLocalAnchor ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8b139-188">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="8b139-189">次に、 **[ParentAnchor]** を空の **[None (Game Object)]\(なし (ゲーム オブジェクト)\)** フィールドにもう一度ドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8b139-189">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="8b139-190">**[FindAzureAnchor]** オブジェクトについては、[AnchorModuleScript] > **[FindAzureAnchor ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8b139-190">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="8b139-191">**[DeleteAzureAnchor]** オブジェクトについては、[AnchorModuleScript] > **[DeleteAzureAnchor ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8b139-191">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="8b139-192">4.シーンを Azure リソースに接続する</span><span class="sxs-lookup"><span data-stu-id="8b139-192">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="8b139-193">[Hierarchy]\(階層\) ウィンドウで **[ParentAnchor]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Spatial Anchor Manager (Script)** コンポーネントまでスクロールします。</span><span class="sxs-lookup"><span data-stu-id="8b139-193">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="8b139-194">次に、 **[Credentials]\(資格情報\)** セクションで、このチュートリアルの[前提条件](mrlearning-asa-ch1.md#prerequisites)の一部として作成した Spatial Anchors Account ID とキーを、対応する **[Spatial Anchors Account Id]\(Spatial Anchors アカウント ID\)** と **[Spatial Anchors Account Key]\(Spatial Anchors アカウント キー\)** フィールドに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8b139-194">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="8b139-196">Azure Spatial Anchors の基本的な動作を試す</span><span class="sxs-lookup"><span data-stu-id="8b139-196">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="8b139-197">これで、Azure Spatial Anchors の基本を示すようにシーンが構成されたので、今度はアプリをデプロイして、Azure Spatial Anchors を直接体験できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8b139-197">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="8b139-198">1.必要な機能をさらに追加する</span><span class="sxs-lookup"><span data-stu-id="8b139-198">1. Add additional required capabilities</span></span>

<span data-ttu-id="8b139-199">Unity メニューで、 **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクト設定...\)** を選択し、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="8b139-199">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="8b139-201">[Player Settings]\(プレーヤーの設定\) ウィンドウで、 **[Player]\(プレーヤー\)** **[Publishing Settings]\(公開の設定\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="8b139-201">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="8b139-203">**[Publishing Settings]\(公開の設定\)** で、 **[Capabilities]\(機能\)** セクションまで下にスクロールして、チュートリアルの開始時にプロジェクトを作成したときに有効にした **InternetClient**、**Microphone**、および **SpatialPerception** の機能が有効になっていることを再確認します。</span><span class="sxs-lookup"><span data-stu-id="8b139-203">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="8b139-204">次に、**InternetClientServer**、**PrivateNetworkClientServer**、 **RemovableStorage**、および **Webcam** の機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="8b139-204">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="8b139-206">2.HoloLens 2 にアプリをデプロイする</span><span class="sxs-lookup"><span data-stu-id="8b139-206">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="8b139-207">Azure Spatial Anchors は Unity では実行できないため、Azure Spatial Anchors の機能をテストするには、プロジェクトをお使いのデバイスにデプロイする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b139-207">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="8b139-208">HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b139-208">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="8b139-209">3.HoloLens 2 でアプリを実行し、アプリ内の指示に従う</span><span class="sxs-lookup"><span data-stu-id="8b139-209">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="8b139-210">Azure Spatial Anchors は、インターネットを使用してアンカー データの保存と読み込みを行うため、お使いのデバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8b139-210">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="8b139-211">お使いのデバイスでアプリケーションが実行されているときに、Azure Spatial Anchor チュートリアルの手順パネルに表示される画面の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="8b139-211">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="8b139-213">エクスペリエンスの固定</span><span class="sxs-lookup"><span data-stu-id="8b139-213">Anchoring an experience</span></span>

<span data-ttu-id="8b139-214">前のセクションでは、Azure Spatial Anchors の基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="8b139-214">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="8b139-215">キューブを使用して、アンカーがアタッチされた親のゲーム オブジェクトを表現および視覚化しました。</span><span class="sxs-lookup"><span data-stu-id="8b139-215">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="8b139-216">このセクションでは、エクスペリエンス全体を、ParentAnchor オブジェクトの子として配置して固定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8b139-216">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="8b139-217">1.ロケット発射台エクスペリエンスを追加する</span><span class="sxs-lookup"><span data-stu-id="8b139-217">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="8b139-218">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)**  >  **[RocketLauncher]** フォルダーに移動し、 **[RocketLauncher_Complete]** プレハブを選択します。</span><span class="sxs-lookup"><span data-stu-id="8b139-218">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="8b139-220">[RocketLauncher_Complete] プレハブを選択したまま、[Hierarchy]\(階層\) ウィンドウの **ParentAnchor** オブジェクトの上にドラッグして、ParentAnchor オブジェクトの子にします。</span><span class="sxs-lookup"><span data-stu-id="8b139-220">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="8b139-222">2.ロケット発射台エクスペリエンスの位置を変更する</span><span class="sxs-lookup"><span data-stu-id="8b139-222">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="8b139-223">**[RocketLauncher_Complete]** オブジェクトが適切なスケールと向きになるように配置、回転、拡大縮小しながら、**ParentAnchor** オブジェクトが引き続き表示されていることを確認します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8b139-223">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="8b139-224">[Transform]\(変換\) の **[Position]\(位置\)** X = 0、Y = 0、Z = 3.75</span><span class="sxs-lookup"><span data-stu-id="8b139-224">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="8b139-225">[Transform]\(変換\) の **[Rotation]\(回転\)** X = 0、Y = 90、Z = 0</span><span class="sxs-lookup"><span data-stu-id="8b139-225">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="8b139-226">[Transform]\(変換\) の **[Scale]\(スケール\)** X = 10、Y = 10、Z = 10</span><span class="sxs-lookup"><span data-stu-id="8b139-226">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="8b139-228">アプリケーションでは、ユーザーがキューブを移動して、ロケット発射台エクスペリエンス全体を再配置できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8b139-228">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="8b139-229">エクスペリエンスの再配置には、再配置オブジェクト (このチュートリアルで使用するキューブなど) の使用、エクスペリエンスを囲む境界ボックスを切り替えるボタンの使用、位置と回転のギズモの使用など、さまざまなユーザー エクスペリエンス フローがあります。</span><span class="sxs-lookup"><span data-stu-id="8b139-229">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="8b139-230">結論</span><span class="sxs-lookup"><span data-stu-id="8b139-230">Congratulations</span></span>

<span data-ttu-id="8b139-231">このチュートリアルでは、Azure Spatial Anchors の基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="8b139-231">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="8b139-232">このチュートリアルでは、Azure Spatial Anchors セッションの開始と停止、単一のデバイス上での Azure Spatial Anchors の作成、アップロード、ダウンロードに必要なさまざまな手順を試すことができるいくつかのボタンが提供されました。</span><span class="sxs-lookup"><span data-stu-id="8b139-232">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="8b139-233">次のレッスンでは、Azure アンカー ID を HoloLens 2 に保存して (アプリケーションを再起動した後であっても) 取得できるようにする方法と、アンカー ID を複数のデバイス間で転送して空間的な位置合わせ行う方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="8b139-233">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="8b139-234">次のレッスン:2.Azure Spatial Anchors の保存、取得、および共有</span><span class="sxs-lookup"><span data-stu-id="8b139-234">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
