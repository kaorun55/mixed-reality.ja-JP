---
title: マルチユーザー機能のチュートリアル - 1。 Photon Unity Networking の設定
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610712"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="4a81c-105">1.Photon Unity Networking の設定</span><span class="sxs-lookup"><span data-stu-id="4a81c-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="4a81c-106">概要</span><span class="sxs-lookup"><span data-stu-id="4a81c-106">Overview</span></span>

<span data-ttu-id="4a81c-107">このチュートリアルでは、Photon Unity Networking (PUN) を使用して共有エクスペリエンスの作成準備をする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-107">In this tutorial, you will learn how to prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="4a81c-108">Photon は、Mixed Reality の開発者が共有エクスペリエンスを作成するために使用できるいくつかのネットワーク オプションの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="4a81c-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="4a81c-109">Photon PUN アプリケーションの作成方法、Photon PUN アセットの Unity プロジェクトへのインポート方法、Unity プロジェクトの Photon PUN アプリケーションへの接続方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-109">You will learn how to create a Photon PUN application, import Photon PUN assets into your Unity project, and connect your Unity project to the Photon PUN application.</span></span>

## <a name="objectives"></a><span data-ttu-id="4a81c-110">目標</span><span class="sxs-lookup"><span data-stu-id="4a81c-110">Objectives</span></span>

* <span data-ttu-id="4a81c-111">Photon PUN アプリケーションを作成する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="4a81c-111">Learn how to create a Photon PUN application</span></span>
* <span data-ttu-id="4a81c-112">Photon PUN アセットを探してインポートする方法を学習する</span><span class="sxs-lookup"><span data-stu-id="4a81c-112">Learn how to find and import the Photon PUN assets</span></span>
* <span data-ttu-id="4a81c-113">Unity プロジェクトを Photon PUN アプリケーションに接続する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="4a81c-113">Learn how to connect your Unity project to the Photon PUN application</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4a81c-114">前提条件</span><span class="sxs-lookup"><span data-stu-id="4a81c-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="4a81c-115">[入門チュートリアル](mrlearning-base.md)と [Azure Spatial Anchors チュートリアル](mrlearning-asa-ch1.md)のチュートリアル シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4a81c-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="4a81c-116">正しい[ツールがインストールされている](install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="4a81c-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="4a81c-117">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="4a81c-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="4a81c-118">基本的な C# プログラミング能力</span><span class="sxs-lookup"><span data-stu-id="4a81c-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="4a81c-119">[開発用に構成された](using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="4a81c-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="4a81c-120">Unity 2019.2.X がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="4a81c-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="4a81c-121">「[Spatial Anchors リソースを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクション ([クイック スタート:Azure Spatial Anchors を使用する Unity HoloLens アプリを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) チュートリアルにあります) を完了します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-121">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a81c-122">このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.2.X です。</span><span class="sxs-lookup"><span data-stu-id="4a81c-122">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="4a81c-123">これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="4a81c-123">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="4a81c-124">Unity プロジェクトの作成と準備</span><span class="sxs-lookup"><span data-stu-id="4a81c-124">Creating and preparing the Unity project</span></span>

<span data-ttu-id="4a81c-125">このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備をします。</span><span class="sxs-lookup"><span data-stu-id="4a81c-125">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="4a81c-126">このためには、まず「[プロジェクトと最初のアプリケーションの初期化](mrlearning-base-ch1.md)」に従ってください (「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」の手順は除く)。これには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4a81c-126">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="4a81c-127">[新しい Unity プロジェクトを作成](mrlearning-base-ch1.md#create-new-unity-project)して、適切な名前を付ける (たとえば、*MRTK Tutorials*)</span><span class="sxs-lookup"><span data-stu-id="4a81c-127">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="4a81c-128">Windows Mixed Reality 用に Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="4a81c-128">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="4a81c-129">TextMesh Pro の Essential Resources (重要なリソース) をインポートする</span><span class="sxs-lookup"><span data-stu-id="4a81c-129">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="4a81c-130">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="4a81c-130">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="4a81c-131">Mixed Reality Toolkit 用に Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="4a81c-131">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="4a81c-132">[Mixed Reality Toolkit を Unity シーンに追加](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)し、シーンに適切な名前を付ける (たとえば、*MultiUserCapabilities*)</span><span class="sxs-lookup"><span data-stu-id="4a81c-132">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="4a81c-133">次に、「[Mixed Reality Toolkit プロファイルを構成する方法 (空間認識表示オプションの変更)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)」の手順に従って、シーンの MRTK 構成プロファイルを **[DefaultHoloLens2ConfigurationProfile]** に変更し、空間認識メッシュの表示オプションを **[Occlusion]\(オクルージョン\)** に変更します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-133">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="4a81c-134">上のリンクの「[Mixed Reality Toolkit 用に Unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)」の手順で述べられているように、MSBuild for Unity を有効にしないことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4a81c-134">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="4a81c-135">機能の構成</span><span class="sxs-lookup"><span data-stu-id="4a81c-135">Configuring the capabilities</span></span>

<span data-ttu-id="4a81c-136">Unity メニューで **[Edit]\(編集\)**  >  **[Project Settings]\(プロジェクトの設定\)** を選択して、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。次に、 **[Player]\(プレーヤー\)**  >   **[Publishing Settings]\(発行の設定\)** セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="4a81c-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

<span data-ttu-id="4a81c-138">**[Publishing Settings]\(公開の設定\)** で、 **[Capabilities]\(機能\)** セクションまで下にスクロールして、チュートリアルの開始時にプロジェクトを作成したときに有効にした **InternetClient**、**Microphone**、および **SpatialPerception** の機能が有効になっていることを再確認します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="4a81c-139">次に、**InternetClientServer**、**PrivateNetworkClientServer**、**RemovableStorage** の機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="4a81c-139">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **RemovableStorage** capabilities:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="4a81c-141">組み込み Unity パッケージの追加</span><span class="sxs-lookup"><span data-stu-id="4a81c-141">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="4a81c-142">このセクションでは、Unity の組み込み AR Foundation パッケージをインストールします。これは、次のセクションでインポートする Azure Spatial Anchors SDK で必要になるためです。</span><span class="sxs-lookup"><span data-stu-id="4a81c-142">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="4a81c-143">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-143">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="4a81c-145">AR Foundation パッケージが一覧に表示されるまでに数秒かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="4a81c-145">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="4a81c-146">[Package Manager]\(パッケージ マネージャー\) ウィンドウで、 **[AR Foundation]** を選択し、 **[Install]\(インストール\)** ボタンをクリックしてパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4a81c-146">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="4a81c-148">チュートリアルのアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="4a81c-148">Importing the tutorial assets</span></span>

<span data-ttu-id="4a81c-149">次の Unity カスタム パッケージを、**記載されている順で**ダウンロードして**インポート**します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-149">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="4a81c-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (バージョン 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="4a81c-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="4a81c-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="4a81c-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="4a81c-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="4a81c-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [<span data-ttu-id="4a81c-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="4a81c-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="4a81c-154">Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a81c-154">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="4a81c-155">チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4a81c-155">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="4a81c-157">MultiUserCapabilities チュートリアル アセット パッケージをインポートすると、型または名前空間が存在しないことを示すいくつかの [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) エラーが [Console]\(コンソール\) ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4a81c-157">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="4a81c-158">これは想定されているものであり、次のセクションで Photon アセットをインポートする際に解決されます。</span><span class="sxs-lookup"><span data-stu-id="4a81c-158">This is to be expected and will be resolved in the next section when you import the Photon assets.</span></span>

## <a name="importing-the-photon-assets"></a><span data-ttu-id="4a81c-159">Photon アセットをインポートする</span><span class="sxs-lookup"><span data-stu-id="4a81c-159">Importing the Photon assets</span></span>

<span data-ttu-id="4a81c-160">このセクションでは、Photon Unity Network (PUN) アセットを Unity のアセット ストアからインポートします。</span><span class="sxs-lookup"><span data-stu-id="4a81c-160">In this section, you will import the Photon Unity Network (PUN) assets from Unity's Asset Store.</span></span>

<span data-ttu-id="4a81c-161">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Asset Store]\(アセット ストア\)** を選択して [Asset Store]\(アセット ストア\) ウィンドウを開き、Exit Games から **[PUN 2 - FREE]** を検索して選択し、 **[Download]\(ダウンロード\)** ボタンをクリックしてアセット パッケージを自分の Unity アカウントにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4a81c-161">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, and then click the **Download** button to download the asset package to your Unity account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

<span data-ttu-id="4a81c-163">ダウンロードが完了したら、 **[Import]\(インポート\)** ボタンをクリックして [Import Unity Package]\(Unity パッケージのインポート\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="4a81c-163">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

<span data-ttu-id="4a81c-165">[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="4a81c-165">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

<span data-ttu-id="4a81c-167">Unity でインポート プロセスが完了したら、[Pun Wizard]\(Pun ウィザード\) ウィンドウが表示されて [PUN Setup]\(PUN 設定\) メニューが読み込まれます。今はこのウィンドウを無視するか、閉じて構いません。</span><span class="sxs-lookup"><span data-stu-id="4a81c-167">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a><span data-ttu-id="4a81c-169">Photon の設定</span><span class="sxs-lookup"><span data-stu-id="4a81c-169">Setting up Photon</span></span>

<span data-ttu-id="4a81c-170">このセクションでは、Photon アカウントを作成 (まだ作成していない場合) し、新しい PUN アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-170">In this section, you will create a Photon account, if you don't already have one, and create a new PUN application.</span></span>

<span data-ttu-id="4a81c-171">使用したいアカウントが既にある場合は Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">ダッシュボード</a> に移動してサインインします。なければ、 **[こちらから作成してください]** リンクをクリックして手順に従い、新しいアカウントを登録します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-171">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

<span data-ttu-id="4a81c-173">サインインしたら、 **[Create a New App]\(新しいアプリの作成\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4a81c-173">Once signed in, click the **Create a New App** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

<span data-ttu-id="4a81c-175">[Create a New Application]\(新しいアプリケーションの作成\) ページで、次の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-175">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="4a81c-176">[Photon Type]\(Photon の種別\) には、[Photon PUN] を選択します</span><span class="sxs-lookup"><span data-stu-id="4a81c-176">For Photon Type, select Photon PUN</span></span>
* <span data-ttu-id="4a81c-177">[Name]\(名前\) には、適切な名前 (_MRTK チュートリアル_ など) を入力します</span><span class="sxs-lookup"><span data-stu-id="4a81c-177">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="4a81c-178">[Description]\(説明\) には、必要に応じて適切な説明を入力します</span><span class="sxs-lookup"><span data-stu-id="4a81c-178">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="4a81c-179">"URL" フィールドは空のままにします</span><span class="sxs-lookup"><span data-stu-id="4a81c-179">For Url, leave the field empty</span></span>

<span data-ttu-id="4a81c-180">**[Create]\(作成する\)** をクリックして新しいアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-180">Then click the **Create** button to create the new application:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

<span data-ttu-id="4a81c-182">Photon で作成プロセスが完了すると、新しい PUN アプリケーションがダッシュボードに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4a81c-182">Once Photon has finished the creation process, the new PUN application will appear on your dashboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="4a81c-184">Unity プロジェクトを PUN アプリケーションに接続する</span><span class="sxs-lookup"><span data-stu-id="4a81c-184">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="4a81c-185">このセクションでは、Unity プロジェクトを前のセクションで作成した PUN アプリケーションに接続します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-185">In this section, you will connect your Unity project to the PUN application you created in the previous section.</span></span>

<span data-ttu-id="4a81c-186">Photon ダッシュボードで、 **"App ID"(アプリ ID)** フィールドをクリックしてアプリ ID を表示し、クリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="4a81c-186">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

<span data-ttu-id="4a81c-188">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Photon Unity Networking]**  >  **[PUN Wizard]\(PUN ウィザード\)** を選択して [Pun Wizard]\(Pun ウィザード\) ウィンドウを開き、 **[Setup Project]\(プロジェクトの設定\)** ボタンをクリックして [PUN Setup]\(PUN 設定\) メニューを開いて次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-188">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="4a81c-189">**"AppId or Email"(アプリ ID またはメール)** フィールドで、前のステップでコピーした PUN アプリ ID を貼り付けます</span><span class="sxs-lookup"><span data-stu-id="4a81c-189">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="4a81c-190">**[Setup Project]\(プロジェクトの設定\)** ボタンをクリックしてアプリ ID を適用します。</span><span class="sxs-lookup"><span data-stu-id="4a81c-190">Then click the **Setup Project** button to apply the app ID:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

<span data-ttu-id="4a81c-192">Unity で PUN 設定プロセスが完了すると、[PUN Setup]\(PUN 設定\) メニューに **[Done!]\(完了\)** というメッセージが表示され、</span><span class="sxs-lookup"><span data-stu-id="4a81c-192">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="4a81c-193">[Project]\(プロジェクト\) ウィンドウで **PhotonServerSettings** アセットが自動的に選択され、そのプロパティが [Inspector]\(インスペクター\) ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4a81c-193">and automatically select the **PhotonServerSettings** asset in the Project window so its properties are displayed in the Inspector window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="4a81c-195">結論</span><span class="sxs-lookup"><span data-stu-id="4a81c-195">Congratulations</span></span>

<span data-ttu-id="4a81c-196">Photon PUN アプリケーションを作成して、これを Unity プロジェクトに接続できました。</span><span class="sxs-lookup"><span data-stu-id="4a81c-196">You have successfully created a Photon PUN application and connected it to your Unity project.</span></span> <span data-ttu-id="4a81c-197">次の手順では、他のユーザーとの接続を許可して複数のユーザーが互いを見られるようにします。</span><span class="sxs-lookup"><span data-stu-id="4a81c-197">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

<span data-ttu-id="4a81c-198">[次のチュートリアル: 2.複数ユーザーの接続](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="4a81c-198">[Next tutorial: 2. Connecting multiple users](mrlearning-sharing(photon)-ch2.md)</span></span>
