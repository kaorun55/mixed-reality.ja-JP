---
title: Azure Spatial Anchors チュートリアル - 1. Azure Spatial Anchors をお使いになる前に
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: d0fd22ad6fbefc6889373b00847721cfc0655ce3
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2020
ms.locfileid: "82605003"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="fff6a-105">1.Azure Spatial Anchors をお使いになる前に</span><span class="sxs-lookup"><span data-stu-id="fff6a-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="fff6a-106">概要</span><span class="sxs-lookup"><span data-stu-id="fff6a-106">Overview</span></span>

<span data-ttu-id="fff6a-107">HoloLens 2 チュートリアルのシリーズ 2 へようこそ。</span><span class="sxs-lookup"><span data-stu-id="fff6a-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="fff6a-108">この 3 部構成のチュートリアル シリーズでは、Azure Spatial Anchors の基礎について学習します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="fff6a-109">この最初のチュートリアル「[Azure Spatial Anchors をお使いになる前に](mrlearning-asa-ch1.md)」では、Azure セッションの開始と停止、単一のデバイス上での Azure アンカーの作成、アップロード、ダウンロードに必要なさまざまな手順を学習します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="fff6a-110">2 番目のチュートリアル「[Azure Spatial Anchors の保存、取得、および共有](mrlearning-asa-ch2.md)」では、HoloLens 2 のストレージにアンカー情報を保存することで、複数のアプリ セッションにわたって Azure Spatial Anchors を保存する方法と、このアンカー情報を他のデバイスと共有して複数のデバイスのアンカー位置合わせを行う方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="fff6a-111">3 番目のチュートリアル「[Azure Spatial Anchors フィードバックの表示](mrlearning-asa-ch3.md)」では、Azure Spatial Anchors を使用する際のアンカーのイベントと状態に関するフィードバックをユーザーに提供する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="fff6a-112">目標</span><span class="sxs-lookup"><span data-stu-id="fff6a-112">Objectives</span></span>

* <span data-ttu-id="fff6a-113">HoloLens 2 用の Azure Spatial Anchors を使用した開発の基礎について学習する</span><span class="sxs-lookup"><span data-stu-id="fff6a-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="fff6a-114">空間アンカーを作成、アップロード、ダウンロードする</span><span class="sxs-lookup"><span data-stu-id="fff6a-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fff6a-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="fff6a-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="fff6a-116">[入門チュートリアル](mrlearning-base.md) シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fff6a-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="fff6a-117">正しい[ツールがインストールされている](install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="fff6a-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="fff6a-118">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="fff6a-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="fff6a-119">基本的な C# プログラミング能力</span><span class="sxs-lookup"><span data-stu-id="fff6a-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="fff6a-120">[開発用に構成された](using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="fff6a-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="fff6a-121">Unity 2019.2.X がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="fff6a-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="fff6a-122">「[Spatial Anchors リソースを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクション ([クイック スタート:Azure Spatial Anchors を使用する Unity HoloLens アプリを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) チュートリアルにあります) を完了します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-122">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fff6a-123">このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.2.X です。</span><span class="sxs-lookup"><span data-stu-id="fff6a-123">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="fff6a-124">これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="fff6a-124">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="fff6a-125">Unity プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="fff6a-125">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

<span data-ttu-id="fff6a-126">このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-126">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="fff6a-127">このためには、まず「[プロジェクトと最初のアプリケーションの初期化](mrlearning-base-ch1.md)」に従ってください (「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」の手順は除く)。これには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fff6a-127">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="fff6a-128">[新しい Unity プロジェクトを作成](mrlearning-base-ch1.md#create-new-unity-project)して、適切な名前を付ける (たとえば、*MRTK Tutorials*)</span><span class="sxs-lookup"><span data-stu-id="fff6a-128">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="fff6a-129">Windows Mixed Reality 用に Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="fff6a-129">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="fff6a-130">TextMesh Pro の Essential Resources (重要なリソース) をインポートする</span><span class="sxs-lookup"><span data-stu-id="fff6a-130">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="fff6a-131">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="fff6a-131">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="fff6a-132">Mixed Reality Toolkit 用に Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="fff6a-132">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="fff6a-133">[Mixed Reality Toolkit を Unity シーンに追加](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)し、シーンに適切な名前を付ける (たとえば、*AzureSpatialAnchors*)</span><span class="sxs-lookup"><span data-stu-id="fff6a-133">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="fff6a-134">次に、「[Mixed Reality Toolkit プロファイルを構成する方法 (空間認識表示オプションの変更)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)」の手順に従って、シーンの MRTK 構成プロファイルを **[DefaultHoloLens2ConfigurationProfile]** に変更し、空間認識メッシュの表示オプションを **[Occlusion]\(オクルージョン\)** に変更します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-134">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="fff6a-135">上のリンクの「[Mixed Reality Toolkit 用に Unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)」の手順で述べられているように、MSBuild for Unity を有効にしないことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fff6a-135">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="fff6a-136">組み込み Unity パッケージの追加</span><span class="sxs-lookup"><span data-stu-id="fff6a-136">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="fff6a-137">このセクションでは、Unity の組み込み AR Foundation パッケージをインストールします。これは、次のセクションでインポートする Azure Spatial Anchors SDK で必要になるためです。</span><span class="sxs-lookup"><span data-stu-id="fff6a-137">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="fff6a-138">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-138">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="fff6a-140">AR Foundation パッケージが一覧に表示されるまでに数秒かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="fff6a-140">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="fff6a-141">[Package Manager]\(パッケージ マネージャー\) ウィンドウで、 **[AR Foundation]** を選択し、 **[Install]\(インストール\)** ボタンをクリックしてパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="fff6a-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="fff6a-143">チュートリアルのアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="fff6a-143">Importing the tutorial assets</span></span>

<span data-ttu-id="fff6a-144">次の Unity カスタム パッケージを、**記載されている順で**ダウンロードして**インポート**します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="fff6a-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (バージョン 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="fff6a-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="fff6a-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="fff6a-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="fff6a-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="fff6a-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)

> [!TIP]
> <span data-ttu-id="fff6a-148">Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fff6a-148">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="fff6a-149">チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fff6a-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="fff6a-151">シーンの作成と準備</span><span class="sxs-lookup"><span data-stu-id="fff6a-151">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="fff6a-152">このセクションでは、チュートリアルのプレハブをいくつか追加してシーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-152">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="fff6a-153">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.AzureSpatialAnchors]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="fff6a-154">Ctrl ボタンを押したまま、 **[ButtonParent]** 、 **[DebugWindow]** 、 **[Instructions]** 、および **[ParentAnchor]** をクリックして 4 つのプレハブを選択します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-154">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="fff6a-156">4 つのプレハブを選択したまま、[Hierarchy]\(階層\) ウィンドウにドラッグしてこれらをシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-156">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="fff6a-158">シーン内のオブジェクトに焦点を合わせるには、ParentAnchor オブジェクトをダブルクリックして、もう一度少しズームアウトします。</span><span class="sxs-lookup"><span data-stu-id="fff6a-158">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="fff6a-160">シーンに大きいアイコンが表示されている場合 (たとえば、大きいフレームの 'T' アイコンが邪魔になる場合)、<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">ギズモをオフに切り替える</a>ことによってこれらを非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="fff6a-160">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="fff6a-161">シーンを操作するためのボタンの構成</span><span class="sxs-lookup"><span data-stu-id="fff6a-161">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="fff6a-162">このセクションでは、スクリプトをシーンに追加して、ローカル アンカーと Azure Spatial Anchors の両方がアプリケーションでどのように動作するかの基本を示す一連のボタン イベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-162">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="fff6a-163">1.Pressable Button Holo Lens 2 (Script) コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="fff6a-163">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="fff6a-164">[Hierarchy]\(階層\) ウィンドウで **[ButtonParent]** オブジェクトを展開し、 **[StartAzureSession]** という名前の最初の子オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-164">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="fff6a-166">[Inspector]\(インスペクター\) ウィンドウで **Pressable Button Holo Lens 2 (Script)** コンポーネントを見つけ、 **+** アイコンをクリックして、**Button Pressed ()** イベントに新しいイベント リスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-166">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="fff6a-168">[Hierarchy]\(階層\) ウィンドウで [StartAzureSession] オブジェクトを選択した状態で、[Hierarchy]\(階層\) ウィンドウの **[ParentAnchor]** オブジェクトをクリックして、先ほど追加したイベント リスナーの空の **[None (Object)]\(なし (オブジェクト)\)** フィールドにドラッグして、このボタンで押されたボタン イベントを ParentAnchor オブジェクトがリッスンするようにします。</span><span class="sxs-lookup"><span data-stu-id="fff6a-168">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="fff6a-170">同じイベント リスナーの **[No Function]\(関数なし\)** ドロップダウンをクリックし、 **[AnchorModuleScript]**  >  **[StartAzureSession ()]** を選択して、このボタンで押されたボタン イベントが発生したときにトリガーされるアクションとして StartAzureSession () 関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-170">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="fff6a-172">2.Interactable (Script) コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="fff6a-172">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="fff6a-173">[Hierarchy]\(階層\) ウィンドウで [StartAzureSession] オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを見つけ、**OnClick ()** イベントについて上記の手順 1 と同じプロセス繰り返します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-173">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="fff6a-175">3.残りのボタンを構成する</span><span class="sxs-lookup"><span data-stu-id="fff6a-175">3. Configure the remaining buttons</span></span>

<span data-ttu-id="fff6a-176">残りの各ボタンについて、上記の手順 1 と手順 2 で説明したプロセスを完了して、**Button Pressed ()** と **OnClick ()** イベントの両方に関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="fff6a-176">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="fff6a-177">**[StopAzureSession]** オブジェクトについては、[AnchorModuleScript] > **[StopAzureSession ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="fff6a-177">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="fff6a-178">**[CreateAzureAnchor]** オブジェクトについては、[AnchorModuleScript] > **[CreateAzureAnchor ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="fff6a-178">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="fff6a-179">次に、 **[ParentAnchor]** を空の **[None (Game Object)]\(なし (ゲーム オブジェクト)\)** フィールドにもう一度ドラッグします。</span><span class="sxs-lookup"><span data-stu-id="fff6a-179">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="fff6a-180">**[RemoveLocalAnchor]** オブジェクトについては、[AnchorModuleScript] > **[RemoveLocalAnchor ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="fff6a-180">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="fff6a-181">次に、 **[ParentAnchor]** を空の **[None (Game Object)]\(なし (ゲーム オブジェクト)\)** フィールドにもう一度ドラッグします。</span><span class="sxs-lookup"><span data-stu-id="fff6a-181">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="fff6a-182">**[FindAzureAnchor]** オブジェクトについては、[AnchorModuleScript] > **[FindAzureAnchor ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="fff6a-182">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="fff6a-183">**[DeleteAzureAnchor]** オブジェクトについては、[AnchorModuleScript] > **[DeleteAzureAnchor ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="fff6a-183">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="fff6a-184">4.シーンを Azure リソースに接続する</span><span class="sxs-lookup"><span data-stu-id="fff6a-184">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="fff6a-185">[Hierarchy]\(階層\) ウィンドウで **[ParentAnchor]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Spatial Anchor Manager (Script)** コンポーネントまでスクロールします。</span><span class="sxs-lookup"><span data-stu-id="fff6a-185">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="fff6a-186">次に、 **[Credentials]\(資格情報\)** セクションで、このチュートリアルの[前提条件](mrlearning-asa-ch1.md#prerequisites)の一部として作成した Spatial Anchors Account ID とキーを、対応する **[Spatial Anchors Account Id]\(Spatial Anchors アカウント ID\)** と **[Spatial Anchors Account Key]\(Spatial Anchors アカウント キー\)** フィールドに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="fff6a-186">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="fff6a-188">Azure Spatial Anchors の基本的な動作を試す</span><span class="sxs-lookup"><span data-stu-id="fff6a-188">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="fff6a-189">これで、Azure Spatial Anchors の基本を示すようにシーンが構成されたので、今度はアプリをデプロイして、Azure Spatial Anchors を直接体験できるようにします。</span><span class="sxs-lookup"><span data-stu-id="fff6a-189">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="fff6a-190">1.必要な機能をさらに追加する</span><span class="sxs-lookup"><span data-stu-id="fff6a-190">1. Add additional required capabilities</span></span>

<span data-ttu-id="fff6a-191">Unity メニューで、 **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクト設定...\)** を選択し、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="fff6a-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="fff6a-193">[Player Settings]\(プレーヤーの設定\) ウィンドウで、 **[Player]\(プレーヤー\)** **[Publishing Settings]\(公開の設定\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-193">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="fff6a-195">**[Publishing Settings]\(公開の設定\)** で、 **[Capabilities]\(機能\)** セクションまで下にスクロールして、チュートリアルの開始時にプロジェクトを作成したときに有効にした **InternetClient**、**Microphone**、および **SpatialPerception** の機能が有効になっていることを再確認します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-195">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="fff6a-196">次に、**InternetClientServer**、**PrivateNetworkClientServer**、 **RemovableStorage**、および **Webcam** の機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fff6a-196">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="fff6a-198">2.HoloLens 2 にアプリをデプロイする</span><span class="sxs-lookup"><span data-stu-id="fff6a-198">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="fff6a-199">Azure Spatial Anchors は Unity では実行できないため、Azure Spatial Anchors の機能をテストするには、プロジェクトをお使いのデバイスにデプロイする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fff6a-199">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="fff6a-200">HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fff6a-200">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="fff6a-201">3.HoloLens 2 でアプリを実行し、アプリ内の指示に従う</span><span class="sxs-lookup"><span data-stu-id="fff6a-201">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="fff6a-202">Azure Spatial Anchors は、インターネットを使用してアンカー データの保存と読み込みを行うため、お使いのデバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fff6a-202">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="fff6a-203">お使いのデバイスでアプリケーションが実行されているときに、Azure Spatial Anchor チュートリアルの手順パネルに表示される画面の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="fff6a-203">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="fff6a-205">エクスペリエンスの固定</span><span class="sxs-lookup"><span data-stu-id="fff6a-205">Anchoring an experience</span></span>

<span data-ttu-id="fff6a-206">前のセクションでは、Azure Spatial Anchors の基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="fff6a-206">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="fff6a-207">キューブを使用して、アンカーがアタッチされた親のゲーム オブジェクトを表現および視覚化しました。</span><span class="sxs-lookup"><span data-stu-id="fff6a-207">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="fff6a-208">このセクションでは、エクスペリエンス全体を、ParentAnchor オブジェクトの子として配置して固定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-208">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="fff6a-209">1.ロケット発射台エクスペリエンスを追加する</span><span class="sxs-lookup"><span data-stu-id="fff6a-209">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="fff6a-210">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)**  >  **[RocketLauncher]** フォルダーに移動し、 **[RocketLauncher_Complete]** プレハブを選択します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-210">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="fff6a-212">[RocketLauncher_Complete] プレハブを選択したまま、[Hierarchy]\(階層\) ウィンドウの **ParentAnchor** オブジェクトの上にドラッグして、ParentAnchor オブジェクトの子にします。</span><span class="sxs-lookup"><span data-stu-id="fff6a-212">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="fff6a-214">2.ロケット発射台エクスペリエンスの位置を変更する</span><span class="sxs-lookup"><span data-stu-id="fff6a-214">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="fff6a-215">**[RocketLauncher_Complete]** オブジェクトが適切なスケールと向きになるように配置、回転、拡大縮小しながら、**ParentAnchor** オブジェクトが引き続き表示されていることを確認します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-215">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="fff6a-216">[Transform]\(変換\) の **[Position]\(位置\)** X = 0、Y = 0、Z = 3.75</span><span class="sxs-lookup"><span data-stu-id="fff6a-216">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="fff6a-217">[Transform]\(変換\) の **[Rotation]\(回転\)** X = 0、Y = 90、Z = 0</span><span class="sxs-lookup"><span data-stu-id="fff6a-217">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="fff6a-218">[Transform]\(変換\) の **[Scale]\(スケール\)** X = 10、Y = 10、Z = 10</span><span class="sxs-lookup"><span data-stu-id="fff6a-218">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="fff6a-220">アプリケーションでは、ユーザーがキューブを移動して、ロケット発射台エクスペリエンス全体を再配置できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="fff6a-220">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="fff6a-221">エクスペリエンスの再配置には、再配置オブジェクト (このチュートリアルで使用するキューブなど) の使用、エクスペリエンスを囲む境界ボックスを切り替えるボタンの使用、位置と回転のギズモの使用など、さまざまなユーザー エクスペリエンス フローがあります。</span><span class="sxs-lookup"><span data-stu-id="fff6a-221">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="fff6a-222">結論</span><span class="sxs-lookup"><span data-stu-id="fff6a-222">Congratulations</span></span>

<span data-ttu-id="fff6a-223">このチュートリアルでは、Azure Spatial Anchors の基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="fff6a-223">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="fff6a-224">このチュートリアルでは、Azure Spatial Anchors セッションの開始と停止、単一のデバイス上での Azure Spatial Anchors の作成、アップロード、ダウンロードに必要なさまざまな手順を試すことができるいくつかのボタンが提供されました。</span><span class="sxs-lookup"><span data-stu-id="fff6a-224">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="fff6a-225">次のレッスンでは、Azure アンカー ID を HoloLens 2 に保存して (アプリケーションを再起動した後であっても) 取得できるようにする方法と、アンカー ID を複数のデバイス間で転送して空間的な位置合わせ行う方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="fff6a-225">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="fff6a-226">次のレッスン:2.Azure Spatial Anchors の保存、取得、および共有</span><span class="sxs-lookup"><span data-stu-id="fff6a-226">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
