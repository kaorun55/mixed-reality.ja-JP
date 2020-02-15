---
title: Azure 空間アンカーチュートリアル-1. Azure 空間アンカーの概要
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 21883e95e92f8808bcf270e6d8091f31933ab6fa
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250867"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="e5248-105">1. Azure 空間アンカーの概要</span><span class="sxs-lookup"><span data-stu-id="e5248-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="e5248-106">概要</span><span class="sxs-lookup"><span data-stu-id="e5248-106">Overview</span></span>

<span data-ttu-id="e5248-107">2番目のシリーズの HoloLens 2 チュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="e5248-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="e5248-108">この3部構成のチュートリアルシリーズでは、Azure 空間アンカーの基礎について説明します。</span><span class="sxs-lookup"><span data-stu-id="e5248-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="e5248-109">この最初のチュートリアル「 [Azure 空間アンカーの概要](mrlearning-asa-ch1.md)」では、azure セッションを開始および停止し、1つのデバイスで azure アンカーを作成、アップロード、およびダウンロードするために必要なさまざまな手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="e5248-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="e5248-110">2番目のチュートリアル「 [Azure 空間アンカーの保存、取得、および共有](mrlearning-asa-ch2.md)」では、複数のアプリセッションにわたって Azure 空間アンカーを保存する方法について説明します。これは、HoloLens 2 のストレージにアンカー情報を保存し、このアンカー情報を複数デバイスのアンカーの配置用に他のデバイスに共有する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="e5248-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="e5248-111">3番目のチュートリアル「 [Azure 空間アンカーフィードバックの表示](mrlearning-asa-ch3.md)」では、azure 空間アンカーを使用する場合のアンカーイベントと状態に関するフィードバックをユーザーに提供する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e5248-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="e5248-112">目標</span><span class="sxs-lookup"><span data-stu-id="e5248-112">Objectives</span></span>

* <span data-ttu-id="e5248-113">HoloLens 2 用の Azure 空間アンカーを使用した開発の基礎について説明します。</span><span class="sxs-lookup"><span data-stu-id="e5248-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="e5248-114">空間アンカーを作成、アップロード、ダウンロードする</span><span class="sxs-lookup"><span data-stu-id="e5248-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e5248-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="e5248-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="e5248-116">[概要チュートリアル](mrlearning-base.md)シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e5248-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="e5248-117">適切な[ツールがインストール](install-the-tools.md)されている WINDOWS 10 PC</span><span class="sxs-lookup"><span data-stu-id="e5248-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="e5248-118">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="e5248-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="e5248-119">基本的なC#プログラミング機能</span><span class="sxs-lookup"><span data-stu-id="e5248-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="e5248-120">[開発用に構成され](using-visual-studio.md#enabling-developer-mode)た HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="e5248-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="e5248-121">Unity 2019.2 がインストールされ、ユニバーサル Windows プラットフォームビルドサポートモジュールが追加された<a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity ハブ</a></span><span class="sxs-lookup"><span data-stu-id="e5248-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="e5248-122">「[クイックスタート: Azure 空間アンカーを使用した Unity HoloLens アプリの作成](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)」チュートリアルの「[空間アンカーリソースの作成](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクションを完了します。</span><span class="sxs-lookup"><span data-stu-id="e5248-122">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5248-123">このチュートリアルシリーズで推奨されている Unity バージョンは Unity 2019.2 です。</span><span class="sxs-lookup"><span data-stu-id="e5248-123">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="e5248-124">これは、前にリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="e5248-124">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="e5248-125">Unity プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="e5248-125">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

<span data-ttu-id="e5248-126">このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発の準備をします。</span><span class="sxs-lookup"><span data-stu-id="e5248-126">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span> <span data-ttu-id="e5248-127">そのためには、「[プロジェクトと最初のアプリケーションの初期化](mrlearning-base-ch1.md)」に従ってください。これには、次の手順が含まれています。[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)の手順は除きます。</span><span class="sxs-lookup"><span data-stu-id="e5248-127">For this, please follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="e5248-128">[新しい Unity プロジェクトを作成](mrlearning-base-ch1.md#create-new-unity-project)し、適切な名前 ( *Mrtk チュートリアル*など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="e5248-128">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*.</span></span>

2. [<span data-ttu-id="e5248-129">Windows Mixed Reality 用に Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="e5248-129">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="e5248-130">TextMesh Pro の重要なリソースをインポートする</span><span class="sxs-lookup"><span data-stu-id="e5248-130">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="e5248-131">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="e5248-131">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="e5248-132">Mixed Reality Toolkit 用に Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="e5248-132">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="e5248-133">[Unity シーンに Mixed Reality Toolkit を追加](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)し、シーンに適切な名前を付けます (たとえば、 *AzureSpatialAnchors* )。</span><span class="sxs-lookup"><span data-stu-id="e5248-133">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

> [!CAUTION]
> <span data-ttu-id="e5248-134">前述のように、「 [Mixed Reality Toolkit の unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)」の手順で説明したように、MSBuild for unity は使用するすべての sdk をサポートしていない場合があり、有効にした後に無効にするのは困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e5248-134">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="e5248-135">そのため、Unity で MSBuild を有効にしないことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e5248-135">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="e5248-136">組み込み Unity パッケージの追加</span><span class="sxs-lookup"><span data-stu-id="e5248-136">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="e5248-137">このセクションでは、Unity の組み込みの AR パッケージをインストールします。これは、次のセクションでインポートする Azure 空間アンカー SDK で必要とされるためです。</span><span class="sxs-lookup"><span data-stu-id="e5248-137">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="e5248-138">Unity メニューで、[ **Window** > **Package Manager**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e5248-138">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="e5248-140">この一覧には、AR Foundation パッケージが表示されるまでに数秒かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="e5248-140">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="e5248-141">パッケージマネージャー ウィンドウで、 **AR Foundation** を選択し、**インストール** ボタンをクリックしてパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="e5248-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="e5248-143">チュートリアル資産のインポート</span><span class="sxs-lookup"><span data-stu-id="e5248-143">Importing the tutorial assets</span></span>

<span data-ttu-id="e5248-144">次の Unity カスタムパッケージをダウンロードし**て、一覧に記載さ**れている順序で**インポート**します。</span><span class="sxs-lookup"><span data-stu-id="e5248-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="e5248-145">[AzureSpatialAnchors unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (バージョン 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="e5248-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="e5248-146">MRTK。HoloLens2. 2.2.0.1. unitypackage を実行します。</span><span class="sxs-lookup"><span data-stu-id="e5248-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.1.unitypackage)
* [<span data-ttu-id="e5248-147">MRTK。HoloLens2. AzureSpatialAnchors. 2.2.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="e5248-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.2.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.2.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="e5248-148">Unity カスタムパッケージをインポートする方法については、「 [Mixed Reality Toolkit のインポート](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5248-148">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="e5248-149">チュートリアルのアセットをインポートすると、プロジェクトウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e5248-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="e5248-151">シーンの作成と準備</span><span class="sxs-lookup"><span data-stu-id="e5248-151">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="e5248-152">このセクションでは、チュートリアル prefabs の一部を追加してシーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="e5248-152">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="e5248-153">[プロジェクト] ウィンドウで、[**アセット** > **mrtk] に移動します。AzureSpatialAnchors** > **Prefabs**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="e5248-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="e5248-154">CTRL ボタンを押したまま、 **Buttonparent**、 **debugwindow**、**命令**、および**parentanchor**をクリックして、4つの prefabs を選択します。</span><span class="sxs-lookup"><span data-stu-id="e5248-154">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="e5248-156">4つの prefabs を選択したまま、[階層] ウィンドウにドラッグしてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="e5248-156">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="e5248-158">シーン内のオブジェクトに焦点を当てるには、ParentAnchor オブジェクトをダブルクリックして、もう一度もう一度ズームします。</span><span class="sxs-lookup"><span data-stu-id="e5248-158">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="e5248-160">シーンに大きいアイコンが見られる場合 (たとえば、大きなフレーム \ ' アイコンが煩雑である場合)、ギズモを off の位置に<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">切り替える</a>ことによって、これらを非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e5248-160">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="e5248-161">シーンを操作するためのボタンの構成</span><span class="sxs-lookup"><span data-stu-id="e5248-161">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="e5248-162">このセクションでは、スクリプトをシーンに追加して、アプリケーションでローカルアンカーと Azure 空間アンカーの両方が動作する方法の基礎を示す一連のボタンイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="e5248-162">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="e5248-163">1. Pressable Button Holo レンズ 2 (Script) コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="e5248-163">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="e5248-164">[階層] ウィンドウで、 **Buttonparent**オブジェクトを展開し、 **StartAzureSession**という名前の最初の子オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e5248-164">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="e5248-166">[インスペクター] ウィンドウで、 **Pressable Button Holo レンズ 2 (Script)** コンポーネントを見つけて、[ **+** ] アイコンをクリックして、ボタンが押された **()** イベントに新しいイベントリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="e5248-166">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="e5248-168">[階層] ウィンドウで StartAzureSession オブジェクトを選択した状態で、[階層] ウィンドウから**Parentanchor**オブジェクトをクリックして、追加したイベントリスナーの空の **[None (オブジェクト)** ] フィールドに移動します。このボタンをクリックすると、parentanchor オブジェクトがボタンの押されたイベントをリッスンするようになります。</span><span class="sxs-lookup"><span data-stu-id="e5248-168">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="e5248-170">同じイベントリスナーの **[関数なし]** ドロップダウンをクリックし、[ **AnchorModuleScript** > **StartAzureSession ()** ] を選択して、このボタンからボタンを押したイベントが発生したときにトリガーされるアクションとして StartAzureSession () 関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="e5248-170">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="e5248-172">2. 対話型 (スクリプト) コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="e5248-172">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="e5248-173">[階層] ウィンドウで StartAzureSession オブジェクトを選択した状態で、[インスペクター] ウィンドウで**対話型 (スクリプト)** コンポーネントを見つけ、 **[OnClick ()]** イベントについて上記の手順1と同じプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="e5248-173">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="e5248-175">3. 残りのボタンを構成する</span><span class="sxs-lookup"><span data-stu-id="e5248-175">3. Configure the remaining buttons</span></span>

<span data-ttu-id="e5248-176">残りの各ボタンについて、上記の手順 1. と 2. で説明したプロセスを完了して、 **Button 押された ()** イベントと**OnClick ()** イベントの両方に関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e5248-176">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="e5248-177">**Stopazuresession**オブジェクトの場合は、AnchorModuleScript > **stopazuresession ()** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e5248-177">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="e5248-178">**Createazureanchor**オブジェクトの場合は、AnchorModuleScript > **createazureanchor ()** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e5248-178">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="e5248-179">次に、 **Parentanchor**を [空の**なし (ゲームオブジェクト)** ] フィールドにもう一度ドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e5248-179">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="e5248-180">**Removelocalanchor**オブジェクトの場合は、AnchorModuleScript > **removelocalanchor ()** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e5248-180">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="e5248-181">次に、 **Parentanchor**を [空の**なし (ゲームオブジェクト)** ] フィールドにもう一度ドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e5248-181">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="e5248-182">**Findazureanchor**オブジェクトの場合は、AnchorModuleScript > **findazureanchor ()** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e5248-182">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="e5248-183">**Deleteazureanchor**オブジェクトの場合は、AnchorModuleScript > **deleteazureanchor ()** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e5248-183">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="e5248-184">4. シーンを Azure リソースに接続する</span><span class="sxs-lookup"><span data-stu-id="e5248-184">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="e5248-185">階層 ウィンドウで**parentanchor**オブジェクトを選択し、インスペクター ウィンドウで **空間アンカーマネージャー (スクリプト)** コンポーネントまでスクロールします。</span><span class="sxs-lookup"><span data-stu-id="e5248-185">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="e5248-186">次に、 **[資格情報]** セクションで、このチュートリアルの[前提条件](mrlearning-asa-ch1.md#prerequisites)の一部として作成した空間アンカーアカウント id とキーを、対応する**空間アンカーアカウント Id**と**空間アンカーアカウントキー**フィールドに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e5248-186">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="e5248-188">Azure 空間アンカーの基本的な動作を試す</span><span class="sxs-lookup"><span data-stu-id="e5248-188">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="e5248-189">これで、Azure 空間アンカーの基本を示すようにシーンが構成されたので、Azure 空間アンカーじを体験できるようにアプリをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="e5248-189">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="e5248-190">1. その他の必要な機能を追加する</span><span class="sxs-lookup"><span data-stu-id="e5248-190">1. Add additional required capabilities</span></span>

<span data-ttu-id="e5248-191">[Unity] メニューの [**プロジェクト設定**の > **編集**] を選択して、[プレーヤーの設定] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="e5248-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="e5248-193">プレーヤーの設定 ウィンドウで、**プレーヤー**、**発行の設定** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="e5248-193">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="e5248-195">発行の**設定**で、 **[機能]** セクションまで下にスクロールし、チュートリアルの冒頭でプロジェクトを作成したときに有効にした**Internetclient**、**マイク**、 **SpatialPerception**の機能が有効になっていることを再度確認します。</span><span class="sxs-lookup"><span data-stu-id="e5248-195">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="e5248-196">次に、 **Internetclientserver**、 **PrivateNetworkClientServer**、 **Removablestorage**、および**web カメラ**の機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e5248-196">Then, enabled the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="e5248-198">2. アプリを HoloLens 2 にデプロイする</span><span class="sxs-lookup"><span data-stu-id="e5248-198">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="e5248-199">Azure 空間アンカーは Unity では実行できません。そのため、Azure 空間アンカー機能をテストするには、プロジェクトをデバイスにデプロイする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5248-199">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="e5248-200">HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法に関する注意事項については、「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」の指示を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5248-200">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="e5248-201">3. アプリを HoloLens 2 で実行し、アプリ内の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="e5248-201">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="e5248-202">Azure 空間アンカーは、インターネットを使用してアンカーデータを保存して読み込みます。そのため、デバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e5248-202">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="e5248-203">アプリケーションがデバイスで実行されている場合は、Azure 空間アンカーチュートリアルの手順パネルに表示される画面の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="e5248-203">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="e5248-205">エクスペリエンスを固定する</span><span class="sxs-lookup"><span data-stu-id="e5248-205">Anchoring an experience</span></span>

<span data-ttu-id="e5248-206">前のセクションでは、Azure 空間アンカーの基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="e5248-206">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="e5248-207">キューブを使用して、アタッチされたアンカーで親ゲームオブジェクトを表現し、視覚化しています。</span><span class="sxs-lookup"><span data-stu-id="e5248-207">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="e5248-208">このセクションでは、ParentAnchor オブジェクトの子として配置することで、エクスペリエンス全体を固定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e5248-208">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="e5248-209">1. ロケットランチャーエクスペリエンスを追加する</span><span class="sxs-lookup"><span data-stu-id="e5248-209">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="e5248-210">プロジェクト ウィンドウで、**アセット** >  **mrtk に移動します。チュートリアル: GettingStarted** **Prefabs** > **RocketLauncher**フォルダーで、 **RocketLauncher_Complete** prefab を選択します。 > </span><span class="sxs-lookup"><span data-stu-id="e5248-210">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="e5248-212">RocketLauncher_Complete prefab を選択したまま、[階層] ウィンドウの**Parentanchor**オブジェクトの上にドラッグして、parentanchor オブジェクトの子にします。</span><span class="sxs-lookup"><span data-stu-id="e5248-212">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="e5248-214">2. ロケットランチャーエクスペリエンスの位置を変更する</span><span class="sxs-lookup"><span data-stu-id="e5248-214">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="e5248-215">次の例のように、 **RocketLauncher_Complete**オブジェクトを適切なスケールと方向に配置、回転、拡大縮小します。また、 **parentanchor**オブジェクトが引き続き公開されていることも確認します。</span><span class="sxs-lookup"><span data-stu-id="e5248-215">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="e5248-216">変換**位置**X = 1、Y = 0、Z = 3.75</span><span class="sxs-lookup"><span data-stu-id="e5248-216">Transform **Position** X = 1, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="e5248-217">変換の**回転**X = 0、Y = 90、Z = 0</span><span class="sxs-lookup"><span data-stu-id="e5248-217">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="e5248-218">変換**スケール**X = 10、Y = 10、Z = 10</span><span class="sxs-lookup"><span data-stu-id="e5248-218">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="e5248-220">アプリケーションでは、ユーザーがキューブを移動して、ロケットランチャーエクスペリエンス全体を再配置できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e5248-220">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="e5248-221">再配置オブジェクト (このチュートリアルで使用されるキューブなど) の使用、エクスペリエンスを示すボタンの使用、画面の位置と回転の使用など、さまざまな操作を行うためのさまざまなユーザーエクスペリエンスフローがあります。ギズモなど。</span><span class="sxs-lookup"><span data-stu-id="e5248-221">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e5248-222">結論</span><span class="sxs-lookup"><span data-stu-id="e5248-222">Congratulations</span></span>

<span data-ttu-id="e5248-223">このチュートリアルでは、Azure 空間アンカーの基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="e5248-223">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="e5248-224">このチュートリアルでは、Azure 空間アンカーセッションを開始および停止するために必要なさまざまな手順を説明し、1つのデバイスで Azure 空間アンカーを作成、アップロード、およびダウンロードするためのいくつかのボタンを紹介しました。</span><span class="sxs-lookup"><span data-stu-id="e5248-224">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="e5248-225">次のレッスンでは、アプリケーションを再起動した後でも、Azure anchor Id を HoloLens 2 に保存し、複数のデバイス間でアンカー Id を転送して空間アラインメントを実現する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e5248-225">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="e5248-226">次のレッスン: 2. Azure 空間アンカーの保存、取得、共有</span><span class="sxs-lookup"><span data-stu-id="e5248-226">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
