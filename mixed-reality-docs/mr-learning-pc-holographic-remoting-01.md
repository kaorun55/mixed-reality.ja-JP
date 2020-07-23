---
title: PC Holographic Remoting のチュートリアル - 1. PC Holographic Remoting の概要
description: このコースを完了すると、Mixed Reality エクスペリエンスを PC から HoloLens 2 にリモート処理する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/19/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: cbbad9548abeb1b8392b99d187b5b051d5b4ddd4
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306733"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a><span data-ttu-id="578e9-105">1.PC Holographic Remoting の概要</span><span class="sxs-lookup"><span data-stu-id="578e9-105">1. Getting started with PC Holographic Remoting</span></span>

## <a name="overview"></a><span data-ttu-id="578e9-106">概要</span><span class="sxs-lookup"><span data-stu-id="578e9-106">Overview</span></span>

  <span data-ttu-id="578e9-107">HoloLens 2 のチュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="578e9-107">Welcome to the HoloLens 2 tutorials.</span></span> <span data-ttu-id="578e9-108">2 部構成のこのチュートリアル シリーズでは、Mixed Reality エクスペリエンスのデモンストレーションを作成する方法と、Holographic Remoting 用の PC アプリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="578e9-108">In this two-part tutorial series, you will learn how to create a mixed reality experience demonstration and how to create a PC app for Holographic Remoting.</span></span>

   <span data-ttu-id="578e9-109">[Mixed Reality エクスペリエンスの作成](mr-learning-pc-holographic-remoting-01.md)に関するこのチュートリアルでは、Mixed Reality エクスペリエンスの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="578e9-109">In this tutorial, [Create mixed reality experience](mr-learning-pc-holographic-remoting-01.md), you will learn how to create a mixed reality experience.</span></span> <span data-ttu-id="578e9-110">このチュートリアルでは、UI 要素、3D モデルの操作、モデルのクリッピング、および視線追跡機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="578e9-110">It will demonstrate UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span>

  <span data-ttu-id="578e9-111">[Holographic Remoting アプリケーションの作成](mr-learning-pc-holographic-remoting-02.md)に関する 2 番目のチュートリアルでは、Holographic Remoting 用の PC アプリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="578e9-111">In the second tutorial, [Create a Holographic Remoting application](mr-learning-pc-holographic-remoting-02.md), you will learn how to create a PC app for Holographic Remoting.</span></span> <span data-ttu-id="578e9-112">また、いつでも HoloLens 2 に接続して、Mixed Reality で 3D コンテンツを視覚化する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="578e9-112">And connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="578e9-113">目標</span><span class="sxs-lookup"><span data-stu-id="578e9-113">Objectives</span></span>

* <span data-ttu-id="578e9-114">アセットをインポートし、シーンをセットアップする</span><span class="sxs-lookup"><span data-stu-id="578e9-114">Import assets and set up the scene</span></span>
* <span data-ttu-id="578e9-115">UI 要素とボタンを使用してホログラムを操作する</span><span class="sxs-lookup"><span data-stu-id="578e9-115">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="578e9-116">クリッピング機能のために 3D オブジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="578e9-116">Configure 3D objects for the clipping feature</span></span>
* <span data-ttu-id="578e9-117">視線追跡を使用したヒントのアクティブ化について理解する</span><span class="sxs-lookup"><span data-stu-id="578e9-117">Learn about activating tooltips with eye-tracking</span></span>

## <a name="prerequisites"></a><span data-ttu-id="578e9-118">前提条件</span><span class="sxs-lookup"><span data-stu-id="578e9-118">Prerequisites</span></span>

* <span data-ttu-id="578e9-119">正しい[ツールがインストールされている](install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="578e9-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="578e9-120">C# プログラミングの基本知識</span><span class="sxs-lookup"><span data-stu-id="578e9-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="578e9-121">[開発用に構成された](using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="578e9-121">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="578e9-122">Unity 2019.3.X がマウントされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="578e9-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.X mounted, and the Universal Windows Platform Build Support module added</span></span>

><span data-ttu-id="578e9-123">[強く推奨] 入門チュートリアル シリーズを完了しているか、Unity および MRTK の基本操作に関する以前の経験</span><span class="sxs-lookup"><span data-stu-id="578e9-123">[!STRONGLY RECOMMENDED] Completed the Getting started tutorials series or some basic prior experience with Unity and MRTK</span></span>

> [!IMPORTANT]
> <span data-ttu-id="578e9-124">このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.3.X です。</span><span class="sxs-lookup"><span data-stu-id="578e9-124">The recommended Unity version for this tutorial series is Unity 2019.3.X.</span></span> <span data-ttu-id="578e9-125">これは、上でリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="578e9-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="578e9-126">Unity プロジェクトの作成と準備</span><span class="sxs-lookup"><span data-stu-id="578e9-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="578e9-127">このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備をします。</span><span class="sxs-lookup"><span data-stu-id="578e9-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="578e9-128">このためには、まず「[プロジェクトと最初のアプリケーションの初期化](mr-learning-base-02.md)」に従ってください (「[デバイスへのアプリケーションのビルド](mr-learning-base-02.md#building-your-application-to-your-hololens-2)」の手順は除く)。これには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="578e9-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="578e9-129">[Unity プロジェクトを作成](mr-learning-base-02.md#creating-the-unity-project)し、"*MRTK チュートリアル*" などの適切な名前を付ける</span><span class="sxs-lookup"><span data-stu-id="578e9-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="578e9-130">ビルド プラットフォームを切り替える</span><span class="sxs-lookup"><span data-stu-id="578e9-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="578e9-131">TextMeshPro の重要なリソースをインポートする</span><span class="sxs-lookup"><span data-stu-id="578e9-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="578e9-132">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="578e9-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="578e9-133">Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="578e9-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="578e9-134">[シーンを作成して設定](mr-learning-base-02.md#creating-and-configuring-the-scene)し、シーンに **PC Holographic Remoting** などの適切な名前を付ける</span><span class="sxs-lookup"><span data-stu-id="578e9-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, **PC Holographic Remoting**</span></span>

<span data-ttu-id="578e9-135">次に、「[空間認識表示オプションの変更](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)」の手順に従って、シーンの MRTK 構成プロファイルを **DefaultHoloLens2ConfigurationProfile** に変更します。</span><span class="sxs-lookup"><span data-stu-id="578e9-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile**.</span></span> <span data-ttu-id="578e9-136">空間認識メッシュの表示オプションを **[オクルージョン]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="578e9-136">Change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="578e9-137">チュートリアルのアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="578e9-137">Importing the tutorial assets</span></span>

<span data-ttu-id="578e9-138">[MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage) をダウンロードして**インポート**します。</span><span class="sxs-lookup"><span data-stu-id="578e9-138">Download and **import** the [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).</span></span>

>[!TIP]
> <span data-ttu-id="578e9-139">Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="578e9-139">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="578e9-140">チュートリアル アセットをインポートすると、[プロジェクト] ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="578e9-140">After importing the tutorial assets, your Project window should look similar to this:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a><span data-ttu-id="578e9-142">シーンの構成と準備</span><span class="sxs-lookup"><span data-stu-id="578e9-142">Configuring and preparing the scene</span></span>

<span data-ttu-id="578e9-143">このセクションでは、チュートリアルのプレハブをいくつか追加してシーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="578e9-143">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="578e9-144">[プロジェクト] ウィンドウで、 **[アセット]**  >  **[MRTK.Tutorials.PCHolograhicRemoting]**  >  **[Prefabs]\(プレハブ\)** フォルダーの順に移動します。</span><span class="sxs-lookup"><span data-stu-id="578e9-144">In the Project window, navigate to **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder.</span></span> <span data-ttu-id="578e9-145">CTRL ボタンを押したまま、次の 6 つのプレハブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="578e9-145">While holding down the CTRL button, click on the below six prefabs.</span></span>

* <span data-ttu-id="578e9-146">ButtonParent</span><span class="sxs-lookup"><span data-stu-id="578e9-146">ButtonParent</span></span>
* <span data-ttu-id="578e9-147">ClippingObjects</span><span class="sxs-lookup"><span data-stu-id="578e9-147">ClippingObjects</span></span>
* <span data-ttu-id="578e9-148">HandSpatialMapButton</span><span class="sxs-lookup"><span data-stu-id="578e9-148">HandSpatialMapButton</span></span>
* <span data-ttu-id="578e9-149">手順</span><span class="sxs-lookup"><span data-stu-id="578e9-149">Instructions</span></span>
* <span data-ttu-id="578e9-150">ModelParent</span><span class="sxs-lookup"><span data-stu-id="578e9-150">ModelParent</span></span>
* <span data-ttu-id="578e9-151">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="578e9-151">Platform</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

<span data-ttu-id="578e9-153">これらのモデルを、[Prefabs]\(プレハブ\) フォルダーから **[階層] ウィンドウ**にドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="578e9-153">Drag-and-drop these models from the prefabs folder into the **Hierarchy window**.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

<span data-ttu-id="578e9-155">シーン内のオブジェクトに焦点を合わせるには、**ModelParent** オブジェクトをダブルクリックして、もう一度少しズームインします。</span><span class="sxs-lookup"><span data-stu-id="578e9-155">To focus in on the objects in the scene, you can double-click on the **ModelParent** object, and then zoom slightly in again:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> <span data-ttu-id="578e9-157">シーンに大きいアイコンが表示されている場合 (大きいフレームの 'T' アイコンが邪魔になる場合など)、<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">ギズモをオフに切り替える</a>ことによってこれらを非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="578e9-157">If you find the large icons in your scene, such as, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="578e9-158">シーンを操作するためのボタンの構成</span><span class="sxs-lookup"><span data-stu-id="578e9-158">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="578e9-159">このセクションでは、シーンにスクリプトを追加して、モデルの切り替えとクリッピング機能の基礎をデモンストレーションするボタン イベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="578e9-159">In this section, you will add scripts into the scene to create button events demonstrating the fundamentals of model switching and clipping functionality.</span></span>

### <a name="1-configuring-the-interactable-script-component"></a><span data-ttu-id="578e9-160">1.Interactable (Script) コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="578e9-160">1. Configuring the Interactable (Script) component</span></span>

<span data-ttu-id="578e9-161">[階層] ウィンドウで、**ButtonParent** オブジェクトを展開し、**NextButton** を選択します。</span><span class="sxs-lookup"><span data-stu-id="578e9-161">In the Hierarchy window, expand the **ButtonParent** object and select the **NextButton**.</span></span> <span data-ttu-id="578e9-162">[インスペクター] ウィンドウで、**Interactable (Script)** コンポーネントを見つけて、**OnClick ()** イベントの下にある **+** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="578e9-162">In the Inspector window, locate the **Interactable (Script)** component and click on **+** icon under **OnClick ()** event.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

<span data-ttu-id="578e9-164">[階層] ウィンドウで **NextButton** オブジェクトを選択したまま、**ButtonParent** オブジェクトを [階層] ウィンドウから、先ほど追加した空の **[None (Object)]\(なし(オブジェクト)\)** フィールドにドラッグして、このボタンをクリックすることによって発生するボタン クリック イベントを ButtonParent オブジェクトがリッスンするようにします。</span><span class="sxs-lookup"><span data-stu-id="578e9-164">With the **NextButton** object still selected in the Hierarchy window, click-and-drag the **ButtonParent** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

<span data-ttu-id="578e9-166">同じイベントの **[No Function]\(関数なし\)** ドロップダウンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="578e9-166">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="578e9-167">次に、**ViewButtonControl** > **NextModel ()** の順に選択して、このボタンを押すことでボタン イベントが発生するときにトリガーされるアクションとして、**NextModel ()** 関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="578e9-167">Then select **ViewButtonControl** > **NextModel ()** to set the **NextModel ()** function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a><span data-ttu-id="578e9-169">2.残りのボタンの構成</span><span class="sxs-lookup"><span data-stu-id="578e9-169">2. Configuring the remaining buttons</span></span>

<span data-ttu-id="578e9-170">残りの各ボタンについて、上記の手順を完了して、**OnClick ()** イベントに関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="578e9-170">For each of the remaining buttons, complete the process outlined above to assign functions to the **OnClick ()** events:</span></span>

* <span data-ttu-id="578e9-171">PreviousButton オブジェクトについては、**ViewButtonControl** > **PreviousModel ()** 関数の順に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="578e9-171">For PreviousButton object, assign the **ViewButtonContro**l > **PreviousModel ()** function.</span></span>

* <span data-ttu-id="578e9-172">ClippingButton については、**ToggleButton** > **ToggleClipping ()** 関数の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="578e9-172">For ClippingButton select **ToggleButton** > **ToggleClipping ()** function.</span></span>

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a><span data-ttu-id="578e9-173">3.View Button Control (Script) および Toggle Button (Script) コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="578e9-173">3. Configuring the View Button Control (Script)  and Toggle Button (Script) components</span></span>

<span data-ttu-id="578e9-174">これで、モデルの切り替えとクリッピング機能をデモンストレーションできるようにボタンが構成されました。</span><span class="sxs-lookup"><span data-stu-id="578e9-174">Now your buttons are configured to demonstrate the model switching and clipping functionality.</span></span> <span data-ttu-id="578e9-175">次に、3D モデルとクリッピング オブジェクトをスクリプトに追加します。</span><span class="sxs-lookup"><span data-stu-id="578e9-175">It is time to add 3D models and the clipping objects to the script.</span></span>

<span data-ttu-id="578e9-176">デモンストレーション用に 6 つの異なる 3D モデルが用意されています。***ModelParentobject*** を展開して、これらの 3D モデルを表示します。</span><span class="sxs-lookup"><span data-stu-id="578e9-176">We have provided six different 3D models for demonstration, expand the ***ModelParentobject*** to expose these 3D models.</span></span>

<span data-ttu-id="578e9-177">[階層] ウィンドウで ButtonParent オブジェクトを選択したまま、[インスペクター] ウィンドウで、**View Button Control (Script)** コンポーネントを見つけて、**Models** 変数を展開します。</span><span class="sxs-lookup"><span data-stu-id="578e9-177">With the ButtonParent object still selected in the Hierarchy window, in the Inspector window, locate the **View Button Control (Script)** component and expand the **Models** variable.</span></span>

<span data-ttu-id="578e9-178">**[サイズ]** フィールドに、シーンに含める 3D モデルの数を入力します。</span><span class="sxs-lookup"><span data-stu-id="578e9-178">In the **Size** field, enter the number of 3D models you would like to have in your scene.</span></span> <span data-ttu-id="578e9-179">この例では、6 を入力します。</span><span class="sxs-lookup"><span data-stu-id="578e9-179">In this case, it would be six.</span></span> <span data-ttu-id="578e9-180">これで、新しい 3D モデルを追加するためのフィールドが作成されます。</span><span class="sxs-lookup"><span data-stu-id="578e9-180">It will create fields for adding new 3D models.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

<span data-ttu-id="578e9-182">ModelParent オブジェクトの子オブジェクトを、これらのフィールドにそれぞれドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="578e9-182">Drag and drop each child object of ModelParent Object into these fields.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

<span data-ttu-id="578e9-184">**ClippingObjects** オブジェクトを、[階層] ウィンドウから **Toggle Button (Script)** コンポーネントの **[Clipping Object]\(クリッピング オブジェクト\)** フィールドにドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="578e9-184">Drag and drop the  **ClippingObjects** object from the Hierarchy window to the  **Toggle Button (Script)** component **Clipping Object** field.</span></span>
>[!NOTE]
><span data-ttu-id="578e9-185">ボタンの親オブジェクトから移動しないようにします。</span><span class="sxs-lookup"><span data-stu-id="578e9-185">Stay in button parent object only.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

<span data-ttu-id="578e9-187">[階層] ウィンドウで **ClippingObjects** プレハブを選択して、[インスペクター] ウィンドウでそれを有効にし、そのクリッピング オブジェクトをオンにします。</span><span class="sxs-lookup"><span data-stu-id="578e9-187">In the Hierarchy window, select the **ClippingObjects** prefab and enable it in the Inspector window to turn on the Clipping objects.</span></span>

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a><span data-ttu-id="578e9-188">クリッピング機能を有効にするためのクリッピング オブジェクトの構成</span><span class="sxs-lookup"><span data-stu-id="578e9-188">Configuring the clipping objects to enable clipping feature</span></span>

<span data-ttu-id="578e9-189">このセクションでは、MarsCuriosityRover オブジェクトの子オブジェクト レンダラーを各クリッピング オブジェクトに追加して、MarsCuriosityRover モデルのクリッピングをデモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="578e9-189">In this section, you will add MarsCuriosityRover object's child objects renderer into an individual clipping object to demonstrate the clipping of the MarsCuriosityRover model.</span></span>

<span data-ttu-id="578e9-190">[階層] ウィンドウで、**ClippingObjects** オブジェクトを展開して、このプロジェクトで使用する 3 つの異なるクリッピング オブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="578e9-190">In the Hierarchy window, expand the **ClippingObjects** object to expose the three different clipping objects that you will be using in this project.</span></span>

<span data-ttu-id="578e9-191">**ClippingSphere** オブジェクトを構成するため、このオブジェクトをクリックし、[インスペクター] ウィンドウで **Clipping Sphere (Script)** コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="578e9-191">To configure the **ClippingSphere** object, click on it, and in the Inspector window, locate the **Clipping Sphere (Script)** component.</span></span> <span data-ttu-id="578e9-192">[サイズ] フィールドに、3D モデルに追加する必要があるレンダラーの数を入力します。</span><span class="sxs-lookup"><span data-stu-id="578e9-192">Enter the number of renderers in the size field that you need to add for your 3D model.</span></span> <span data-ttu-id="578e9-193">この場合は、MarsCuriosityRover 子オブジェクト用に 10 個追加します。</span><span class="sxs-lookup"><span data-stu-id="578e9-193">In this case, add 10 for MarsCuriosityRover child objects.</span></span> <span data-ttu-id="578e9-194">これで、レンダラーを追加するためのフィールドが作成されます。MarsCuriosityRover オブジェクトの子モデル オブジェクトをこれらのフィールドにドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="578e9-194">It will create fields for adding renderers, drag and drop MarsCuriosityRover Object's child model objects into these fields.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

<span data-ttu-id="578e9-196">同じプロセスに従って、MarsCuriosityRover の子オブジェクト レンダラーを **ClippingBox** および **ClippingPlane** オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="578e9-196">Follow the same process and add MarsCuriosityRover's child objects renderers to the **ClippingBox** and **ClippingPlane** objects.</span></span>

<span data-ttu-id="578e9-197">このチュートリアルでは、クリッピング機能のデモンストレーションに MarsCuriosityRover モデルのみを使用します。</span><span class="sxs-lookup"><span data-stu-id="578e9-197">In this tutorial, only the MarsCuriosityRover model will be used for demonstrating the clipping feature.</span></span> <span data-ttu-id="578e9-198">クリッピング機能を他のモデルに追加し、レンダラーのサイズを大きくし、それぞれのメッシュ レンダラーを追加してきました。</span><span class="sxs-lookup"><span data-stu-id="578e9-198">They were adding clipping features to more models, increasing the size of the renderer, and adding their individual mesh renderers.</span></span>

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a><span data-ttu-id="578e9-199">ヒントを強調表示するための視線追跡の構成</span><span class="sxs-lookup"><span data-stu-id="578e9-199">Configuring eye-tracking to highlight tooltips</span></span>

<span data-ttu-id="578e9-200">このセクションでは、プロジェクトで視線追跡を有効にする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="578e9-200">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="578e9-201">たとえば、MarsCuriosityRover のパーツに関連付けられているヒントを、それらのパーツに視線を向けている時は強調表示し、視線を外すと非表示にする機能を実装できます。</span><span class="sxs-lookup"><span data-stu-id="578e9-201">For example, you will implement the functionality to highlight tooltips attached to MarsCuriosityRover's parts while looking at them and hiding them, while you are looking away from them.</span></span>

### <a name="1-identify-target-objects-and-associated-tooltips"></a><span data-ttu-id="578e9-202">1.ターゲット オブジェクトと関連するヒントを特定する</span><span class="sxs-lookup"><span data-stu-id="578e9-202">1. Identify target objects and associated tooltips.</span></span>

<span data-ttu-id="578e9-203">[階層] ウィンドウで、ModelParent オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="578e9-203">In the Hierarchy window, select the ModelParent object.</span></span> <span data-ttu-id="578e9-204">***[MarsCuriosity] -> [Rover]*** の順に展開し、MarsCuriosityRover の 5 つのメイン パーツである、**POI-Camera**、**POI-Wheels**、**POI-Antena**、**POI-Spectrometer**、**POI-RUHF Antenna** を表示します。</span><span class="sxs-lookup"><span data-stu-id="578e9-204">Expand the ***MarsCuriosity -> Rover*** to find five main parts of the MarsCuriosityRover: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span></span>

* <span data-ttu-id="578e9-205">[階層] ウィンドウで、MarsCuriosityRover パーツに関連付けられている、対応する 5 つのヒント オブジェクトを確認します。</span><span class="sxs-lookup"><span data-stu-id="578e9-205">Observe five corresponding tooltip objects associated with MarsCuriosityRover parts in the Hierarchy window.</span></span> 
* <span data-ttu-id="578e9-206">これらの MarsCuriosityRover パーツに視線を向けたときにそのエクスペリエンスを強調表示するように、これらのオブジェクトを構成していきます。</span><span class="sxs-lookup"><span data-stu-id="578e9-206">You will be configuring these objects to highlight the experience when you look at the MarsCuriosityRover parts.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a><span data-ttu-id="578e9-208">2.While Looking At Target () および On Look Away () イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="578e9-208">2. Implement While Looking At Target ()  &  On Look Away () events</span></span>

<span data-ttu-id="578e9-209">[階層] ウィンドウで、***POI-Camera*** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="578e9-209">In the Hierarchy window, select the ***POI-Camera*** object.</span></span> <span data-ttu-id="578e9-210">[インスペクター] ウィンドウで、**Eye Tracking Target (Script)** コンポーネントを見つけて、次のように **While Looking At Target ()**  & **On Look Away ()** イベントを構成します。</span><span class="sxs-lookup"><span data-stu-id="578e9-210">In the Inspector window, locate the **Eye Tracking Target (Script)** component and configure the **While Looking At Target ()** & **On Look Away ()** events as follows:</span></span>

* <span data-ttu-id="578e9-211">**[None (Object)]\(なし (オブジェクト)\)** フィールドに、**POI-Camera ToolTip** オブジェクトを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="578e9-211">To **None (Object)** field, assign the **POI-Camera ToolTip** object</span></span>
* <span data-ttu-id="578e9-212">**While Looking At Target ()** イベントの **[No Function]\(関数なし\)** ドロップダウンから、**GameObject** > **SetActive (bool)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="578e9-212">From **No Function** dropdown of **While Looking At Target ()** event, select **GameObject** > **SetActive (bool).**</span></span> <span data-ttu-id="578e9-213">その下にある**チェックボックス**をオンにして、ターゲット オブジェクトに視線を向けたときにトリガーされるアクションとしてそのヒントが強調表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="578e9-213">Select the **Checkbox** under it to highlight the tooltip as the action that is triggered when you look at the target object.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* <span data-ttu-id="578e9-215">同じプロセスに従い、**On Look Away ()** イベント リスナーの **[No Function]\(関数なし\)** ドロップダウンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="578e9-215">Follow the same process and click on the **No Function** dropdown of the **On Look Away ()** event listener.</span></span> <span data-ttu-id="578e9-216">次に、**GameObject** > **SetActive (bool)** の順に選択し、**チェックボックス**はオフのままにしておいて、ターゲット オブジェクトから視線を外したときにトリガーされるアクションとしてそのヒントが非表示になるようにします。</span><span class="sxs-lookup"><span data-stu-id="578e9-216">Then select **GameObject** > **SetActive (bool**) and leave the **Checkbox** empty to hide the tooltip as the action that is triggered when you look away from the target object.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

<span data-ttu-id="578e9-218">同じプロセスに従い、同じ **MarsCuriosityRover** パーツの **While Looking At Target ()**  & **On Look Away ()** イベントに、それぞれのヒント オブジェクトを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="578e9-218">Follow the same process and assign respective tooltip objects to their same **MarsCuriosityRover** parts **While Looking At Target ()** & **On Look Away ()** events.</span></span>

<span data-ttu-id="578e9-219">視線追跡を有効にするには、こちらの[ガイドライン](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="578e9-219">To enable eye tracking, please follow these [guidelines](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span></span>

## <a name="congratulations"></a><span data-ttu-id="578e9-220">結論</span><span class="sxs-lookup"><span data-stu-id="578e9-220">Congratulations</span></span>

<span data-ttu-id="578e9-221">このチュートリアルでは、UI 要素、3D モデルの操作、モデルのクリッピング、および視線追跡機能をデモンストレーションする Mixed Reality エクスペリエンスを構築する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="578e9-221">In this tutorial, you learned to build a mixed reality experience demonstrating UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span> <span data-ttu-id="578e9-222">このチュートリアルで説明した NextButton および PreviousButton で、3D モデルのビューアー エクスペリエンスを実際に試しました。</span><span class="sxs-lookup"><span data-stu-id="578e9-222">The tutorial provided you with NextButton and PreviousButton that let you explore the 3D model viewer experience.</span></span> <span data-ttu-id="578e9-223">ClippingObjectButton を使用して、クリッピング オブジェクトをオンにし、クリッピング機能を体験しました。</span><span class="sxs-lookup"><span data-stu-id="578e9-223">The ClippingObjectButton made you turn on clipping objects and experience clipping feature.</span></span> <span data-ttu-id="578e9-224">このチュートリアルでは、エクスペリエンスでのヒントの強調表示を可能にする視線追跡要素についても説明しました。</span><span class="sxs-lookup"><span data-stu-id="578e9-224">The tutorial also provided you with an eye-tracking element to enable highlighting the tooltips in the experience.</span></span>

<span data-ttu-id="578e9-225">次のレッスンでは、いつでも HoloLens 2 に接続できる PC 用の Holographic Remoting アプリケーションを作成し、Mixed Reality で 3D コンテンツを視覚化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="578e9-225">In the next lesson, you will learn how to create a Holographic Remoting application for PC to connect HoloLens 2 at any point, providing a way to Visualize 3D content in mixed reality.</span></span>

[<span data-ttu-id="578e9-226">次のレッスン:2.Holographic Remoting アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="578e9-226">Next Lesson: 2. Create Holographic Remoting application</span></span>](mr-learning-pc-holographic-remoting-02.md)
