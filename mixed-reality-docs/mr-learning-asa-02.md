---
title: Azure Spatial Anchors チュートリアル - 2. Azure Spatial Anchors をお使いになる前に
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure Spatial Anchors を実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: a24b6b03ce75a57db49b3d0c875d123ea87c8162
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305102"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="85f3f-105">2.Azure Spatial Anchors をお使いになる前に</span><span class="sxs-lookup"><span data-stu-id="85f3f-105">2. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="85f3f-106">概要</span><span class="sxs-lookup"><span data-stu-id="85f3f-106">Overview</span></span>

<span data-ttu-id="85f3f-107">このチュートリアルでは、Azure Spatial Anchors セッションの開始と停止、および単一のデバイス上での Azure Spatial Anchors の作成、アップロード、ダウンロードに必要なさまざまな手順を学習します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-107">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="85f3f-108">目標</span><span class="sxs-lookup"><span data-stu-id="85f3f-108">Objectives</span></span>

* <span data-ttu-id="85f3f-109">HoloLens 2 用の Azure Spatial Anchors を使用した開発の基礎について学習する</span><span class="sxs-lookup"><span data-stu-id="85f3f-109">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="85f3f-110">Spatial Anchors を作成し、それらを Azure からフェッチする方法を学習する</span><span class="sxs-lookup"><span data-stu-id="85f3f-110">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="85f3f-111">Unity プロジェクトの作成と準備</span><span class="sxs-lookup"><span data-stu-id="85f3f-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="85f3f-112">このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="85f3f-113">このためには、まず「[プロジェクトの初期化と最初のアプリケーションの配置](mr-learning-base-02.md)」に従ってください ([デバイスにアプリケーションをビルドする](mr-learning-base-02.md#building-your-application-to-your-hololens-2)手順は除きます)。これには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="85f3f-113">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="85f3f-114">[Unity プロジェクトを作成](mr-learning-base-02.md#creating-the-unity-project)し、"*MRTK チュートリアル*" などの適切な名前を付ける</span><span class="sxs-lookup"><span data-stu-id="85f3f-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="85f3f-115">ビルド プラットフォームを切り替える</span><span class="sxs-lookup"><span data-stu-id="85f3f-115">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="85f3f-116">TextMeshPro の重要なリソースをインポートする</span><span class="sxs-lookup"><span data-stu-id="85f3f-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="85f3f-117">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="85f3f-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="85f3f-118">Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="85f3f-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="85f3f-119">[シーンを作成して構成](mr-learning-base-02.md#creating-and-configuring-the-scene)し、シーンに *AzureSpatialAnchors* などの適切な名前を付ける</span><span class="sxs-lookup"><span data-stu-id="85f3f-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="85f3f-120">次に、「[空間認識表示オプションの変更](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)」の指示に従い、次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="85f3f-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="85f3f-121">**MRTK 構成プロファイル**を **DefaultHoloLens2ConfigurationProfile** に変更します</span><span class="sxs-lookup"><span data-stu-id="85f3f-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="85f3f-122">**空間認識メッシュ表示オプション**を **[Occlusion]\(オクルージョン\)** に変更します</span><span class="sxs-lookup"><span data-stu-id="85f3f-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="85f3f-123">組み込みの Unity パッケージのインストール</span><span class="sxs-lookup"><span data-stu-id="85f3f-123">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="85f3f-124">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** の順に選択して、[Package Manager]\(パッケージ マネージャー\) ウィンドウを開きます。次に、 **[AR Foundation]** を選択し、 **[Install]\(インストール\)** ボタンをクリックしてパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="85f3f-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="85f3f-126">Azure Spatial Anchors SDK で必要になるため、AR Foundation パッケージをインストールします。これは、次のセクションでインポートします。</span><span class="sxs-lookup"><span data-stu-id="85f3f-126">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="85f3f-127">チュートリアルのアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="85f3f-127">Importing the tutorial assets</span></span>

<span data-ttu-id="85f3f-128">次の Unity カスタム パッケージを、**記載されている順で**ダウンロードして**インポート**します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="85f3f-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (バージョン 2.2.1)</span><span class="sxs-lookup"><span data-stu-id="85f3f-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="85f3f-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="85f3f-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="85f3f-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="85f3f-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

<span data-ttu-id="85f3f-132">チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="85f3f-132">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="85f3f-134">Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85f3f-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="85f3f-135">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="85f3f-135">Preparing the scene</span></span>

<span data-ttu-id="85f3f-136">このセクションでは、チュートリアルのプレハブをいくつか追加してシーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-136">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="85f3f-137">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.AzureSpatialAnchors]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動し、次のプレハブを [Hierarchy]\(階層\) ウィンドウにドラッグしてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="85f3f-138">**ButtonParent** プレハブ</span><span class="sxs-lookup"><span data-stu-id="85f3f-138">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="85f3f-139">**DebugWindow** プレハブ</span><span class="sxs-lookup"><span data-stu-id="85f3f-139">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="85f3f-140">**Instructions** プレハブ</span><span class="sxs-lookup"><span data-stu-id="85f3f-140">**Instructions** prefabs</span></span>
* <span data-ttu-id="85f3f-141">**ParentAnchor** プレハブ</span><span class="sxs-lookup"><span data-stu-id="85f3f-141">**ParentAnchor** prefabs</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="85f3f-143">シーンに大きいアイコンが表示されている場合 (たとえば、大きいフレームの 'T' アイコンが邪魔になる場合など)、上の画像で示すように、<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">ギズモをオフに切り替える</a>ことによってこれらを非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="85f3f-143">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="85f3f-144">シーンを操作するためのボタンの構成</span><span class="sxs-lookup"><span data-stu-id="85f3f-144">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="85f3f-145">このセクションでは、スクリプトをシーンに追加して、アプリでのローカル アンカーと Azure Spatial Anchors の両方の基本的な動作を示す一連のボタン イベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-145">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="85f3f-146">[Hierarchy]\(階層\) ウィンドウで、 **[ButtonParent]** オブジェクトを展開し、**StartAzureSession** という名前の最初の子オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-146">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="85f3f-147">**ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="85f3f-147">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="85f3f-148">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[StartAzureSession ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="85f3f-148">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="85f3f-150">[Hierarchy]\(階層\) ウィンドウで、次の **StopAzureSession** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-150">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="85f3f-151">**ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="85f3f-151">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="85f3f-152">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[StopAzureSession ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="85f3f-152">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="85f3f-154">[Hierarchy]\(階層\) ウィンドウで、次の **CreateAzureAnchor** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-154">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="85f3f-155">**ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="85f3f-155">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="85f3f-156">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[CreateAzureAnchor ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="85f3f-156">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="85f3f-157">**[ParentAnchor]** オブジェクトを空の **[None (Game Object)]\(なし (ゲーム オブジェクト)\)** フィールドに割り当てて、CreateAzureAnchor () 関数の引数にします</span><span class="sxs-lookup"><span data-stu-id="85f3f-157">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="85f3f-159">[Hierarchy]\(階層\) ウィンドウで、次の **RemoveLocalAnchor** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-159">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="85f3f-160">**ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="85f3f-160">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="85f3f-161">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[RemoveLocalAnchor ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="85f3f-161">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="85f3f-162">**[ParentAnchor]** オブジェクトを空の **[None (Game Object)]\(なし (ゲーム オブジェクト)\)** フィールドに割り当てて、RemoveLocalAnchor () 関数の引数にします</span><span class="sxs-lookup"><span data-stu-id="85f3f-162">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="85f3f-164">[Hierarchy]\(階層\) ウィンドウで、次の **FindAzureAnchor** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-164">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="85f3f-165">**ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="85f3f-165">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="85f3f-166">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[FindAzureAnchor ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="85f3f-166">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="85f3f-168">[Hierarchy]\(階層\) ウィンドウで、次の **DeleteAzureAnchor** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-168">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="85f3f-169">**ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="85f3f-169">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="85f3f-170">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[DeleteAzureAnchor ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="85f3f-170">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="85f3f-172">シーンを Azure リソースに接続する</span><span class="sxs-lookup"><span data-stu-id="85f3f-172">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="85f3f-173">[Hierarchy]\(階層\) ウィンドウで **[ParentAnchor]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Spatial Anchor Manager (Script)** コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="85f3f-173">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="85f3f-174">このチュートリアル シリーズの「[前提条件](mr-learning-asa-01.md#prerequisites)」の一環として作成した Azure Spatial Anchors アカウントの資格情報を使用して、 **[Credentials]\(資格情報\)** セクションを構成します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-174">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="85f3f-175">**"Spatial Anchors Account ID"(Spatial Anchors アカウント ID)** フィールドに、Azure Spatial Anchors アカウントからの**アカウント ID** を貼り付ける</span><span class="sxs-lookup"><span data-stu-id="85f3f-175">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="85f3f-176">**"Spatial Anchors Account Key"(Spatial Anchors アカウント キー)** フィールドに、Azure Spatial Anchors アカウントからのプライマリまたはセカンダリ **アクセス キー** を貼り付ける</span><span class="sxs-lookup"><span data-stu-id="85f3f-176">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="85f3f-178">Azure Spatial Anchors の基本的な動作を試す</span><span class="sxs-lookup"><span data-stu-id="85f3f-178">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="85f3f-179">Azure Spatial Anchors は Unity では実行できないため、Azure Spatial Anchors の機能をテストするには、ご利用のデバイスにプロジェクトをビルドし、アプリをデプロイする必要があります。</span><span class="sxs-lookup"><span data-stu-id="85f3f-179">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="85f3f-180">HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、[HoloLens 2 にアプリをビルドする](mr-learning-base-02.md#building-your-application-to-your-hololens-2)手順に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="85f3f-180">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="85f3f-181">ご利用のデバイスでアプリケーションが実行されているときに、Azure Spatial Anchor チュートリアルの手順パネルに表示される画面の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="85f3f-181">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="85f3f-182">キューブを別の場所に移動します</span><span class="sxs-lookup"><span data-stu-id="85f3f-182">Move the cube to a different location</span></span>
1. <span data-ttu-id="85f3f-183">Azure セッションを開始します</span><span class="sxs-lookup"><span data-stu-id="85f3f-183">Start Azure Session</span></span>
1. <span data-ttu-id="85f3f-184">Azure Anchor を作成します (キューブの場所に Anchor を作成します)。</span><span class="sxs-lookup"><span data-stu-id="85f3f-184">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="85f3f-185">Azure セッションを停止します</span><span class="sxs-lookup"><span data-stu-id="85f3f-185">Stop Azure Session</span></span>
1. <span data-ttu-id="85f3f-186">ローカル アンカーを削除します (これにより、ユーザーはキューブを移動できます)</span><span class="sxs-lookup"><span data-stu-id="85f3f-186">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="85f3f-187">キューブを別の場所に移動します</span><span class="sxs-lookup"><span data-stu-id="85f3f-187">Move the cube somewhere else</span></span>
1. <span data-ttu-id="85f3f-188">Azure セッションを開始します</span><span class="sxs-lookup"><span data-stu-id="85f3f-188">Start Azure Session</span></span>
1. <span data-ttu-id="85f3f-189">Azure Anchor を見つけます (手順 3 の場所にキューブを配置します)</span><span class="sxs-lookup"><span data-stu-id="85f3f-189">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="85f3f-190">Azure Anchor を削除します</span><span class="sxs-lookup"><span data-stu-id="85f3f-190">Delete Azure Anchor</span></span>
1. <span data-ttu-id="85f3f-191">Azure セッションを停止します</span><span class="sxs-lookup"><span data-stu-id="85f3f-191">Stop Azure session</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="85f3f-193">Azure Spatial Anchors では、インターネットを使用してアンカー データの保存と読み込みを行うため、ご利用のデバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="85f3f-193">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="85f3f-194">エクスペリエンスの固定</span><span class="sxs-lookup"><span data-stu-id="85f3f-194">Anchoring an experience</span></span>

<span data-ttu-id="85f3f-195">前のセクションでは、Azure Spatial Anchors の基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="85f3f-195">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="85f3f-196">キューブを使用して、アンカーがアタッチされた親のゲーム オブジェクトを表現および視覚化しました。</span><span class="sxs-lookup"><span data-stu-id="85f3f-196">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="85f3f-197">このセクションでは、エクスペリエンス全体を、ParentAnchor オブジェクトの子として配置して固定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-197">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="85f3f-198">[Hierarchy]\(階層\) ウィンドウで、**ParentAnchor** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Transform** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-198">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="85f3f-199">**[Scale X]\(X 拡大縮小\)** を 1.1 に変更します</span><span class="sxs-lookup"><span data-stu-id="85f3f-199">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="85f3f-200">**[Scale Z]\(Z 拡大縮小\)** を 1.1 に変更します</span><span class="sxs-lookup"><span data-stu-id="85f3f-200">Change **Scale Z** to 1.1</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="85f3f-202">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)**  >  **[Rover]** フォルダーの順に移動し、**RoverExplorer_Complete** プレハブをクリックして [Hierarchy]\(階層\) ウィンドウにドラッグし、シーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-202">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="85f3f-204">新しく追加した RoverModule_Complete オブジェクトが [Hierarchy]\(階層\) ウィンドウで選択されたままの状態で、それを **ParentAnchor** オブジェクトにドラッグして、ParentAnchor オブジェクトの子にします。</span><span class="sxs-lookup"><span data-stu-id="85f3f-204">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="85f3f-206">ここでプロジェクトを再ビルドして、アプリをご利用のデバイスにデプロイすると、サイズ変更したキューブを移動して、Rover エクスプローラー エクスペリエンス全体を再配置できます。</span><span class="sxs-lookup"><span data-stu-id="85f3f-206">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="85f3f-207">エクスペリエンスの再配置には、再配置オブジェクト (このチュートリアルで使用するキューブなど) の使用、エクスペリエンスを囲む境界ボックスを切り替えるボタンの使用、位置と回転のギズモの使用など、さまざまなユーザー エクスペリエンス フローがあります。</span><span class="sxs-lookup"><span data-stu-id="85f3f-207">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="85f3f-208">結論</span><span class="sxs-lookup"><span data-stu-id="85f3f-208">Congratulations</span></span>

<span data-ttu-id="85f3f-209">このチュートリアルでは、Azure Spatial Anchors の基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="85f3f-209">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="85f3f-210">このチュートリアルでは、Azure Spatial Anchors セッションの開始と停止を行うため、および単一のデバイスで Azure Spatial Anchors の作成、アップロード、ダウンロードを行うために</span><span class="sxs-lookup"><span data-stu-id="85f3f-210">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="85f3f-211">必要なさまざまな手順を調べることができるいくつかのボタンについて説明しました。</span><span class="sxs-lookup"><span data-stu-id="85f3f-211">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="85f3f-212">次のチュートリアルでは、アプリを再起動した後でも取得できるように、Azure アンカー ID を HoloLens 2 に保存する方法と、アンカー ID を複数のデバイス間で転送して空間的な位置合わせを行う方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="85f3f-212">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="85f3f-213">次のチュートリアル:3.Azure Spatial Anchors の保存、取得、および共有</span><span class="sxs-lookup"><span data-stu-id="85f3f-213">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
