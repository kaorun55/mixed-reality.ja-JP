---
title: Azure 空間アンカーチュートリアル-1. Azure 空間アンカーの概要
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: fb7074849c5a07a95b370b5bfa75228fac36ba5b
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105959"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="2c870-105">1. Azure 空間アンカーの概要</span><span class="sxs-lookup"><span data-stu-id="2c870-105">1. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="2c870-106">HoloLens 2 チュートリアルの2番目のモジュールへようこそ。</span><span class="sxs-lookup"><span data-stu-id="2c870-106">Welcome to the second module of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="2c870-107">作業を開始する前に、すべての[前提条件](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens)が満たされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2c870-107">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="2c870-108">最初の[ベースモジュール](mrlearning-base.md)をまだ完了していない場合は、最初にそのモジュールを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2c870-108">If you have not completed the first, [Base module](mrlearning-base.md) yet, it's recommended that you complete that module first.</span></span> <span data-ttu-id="2c870-109">新しい Unity プロジェクトから開始する場合は、[ベースモジュール](mrlearning-base.md)の新しいプロジェクト作成手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2c870-109">If you are starting from a new Unity project, follow the new project creation steps in the [Base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="2c870-110">目標</span><span class="sxs-lookup"><span data-stu-id="2c870-110">Objectives</span></span>

* <span data-ttu-id="2c870-111">HoloLens 2 を使用した Azure 空間アンカーを使用した開発の基礎について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c870-111">Learn the fundamentals of developing with Azure Spatial Anchors with HoloLens 2</span></span>

* <span data-ttu-id="2c870-112">空間アンカーを作成、アップロード、ダウンロードする</span><span class="sxs-lookup"><span data-stu-id="2c870-112">Create, upload, and download spatial anchors</span></span>

## <a name="instructions"></a><span data-ttu-id="2c870-113">手順</span><span class="sxs-lookup"><span data-stu-id="2c870-113">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="2c870-114">アセットのダウンロードとインポート</span><span class="sxs-lookup"><span data-stu-id="2c870-114">Downloading and importing assets</span></span>
<span data-ttu-id="2c870-115">開始する前に、次のアセットをダウンロードしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="2c870-115">Before beginning, download and import the following assets:</span></span>

[<span data-ttu-id="2c870-116">Azure 空間アンカー v 1.1.0</span><span class="sxs-lookup"><span data-stu-id="2c870-116">Azure Spatial Anchors v1.1.0</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[<span data-ttu-id="2c870-117">HoloLens2. 2.1.0.0. unitypackage を実行します。</span><span class="sxs-lookup"><span data-stu-id="2c870-117">Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

[<span data-ttu-id="2c870-118">HoloLens2. AzureSpatialAnchor. 2.1.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="2c870-118">Unity.HoloLens2.AzureSpatialAnchor.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchor-v2.1.0.0/Unity.HoloLens2.AzureSpatialAnchor.Tutorials.Asset.2.1.0.0.unitypackage)

[<span data-ttu-id="2c870-119">Mixed Reality Toolkit Foundation パッケージ2.1.0</span><span class="sxs-lookup"><span data-stu-id="2c870-119">Mixed Reality Toolkit  Foundation Package 2.1.0</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.1.0)

1. <span data-ttu-id="2c870-120">プロジェクトに新しいシーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c870-120">Create a new scene in your project.</span></span> <span data-ttu-id="2c870-121">シーンフォルダーを右クリックし、[作成]、[シーン] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c870-121">Right click your Scene folder, click Create, then Scene.</span></span> <span data-ttu-id="2c870-122">新しいシーンに "ASALearningModule" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="2c870-122">Name the new scene as "ASALearningModule".</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="2c870-124">[ASALearningmodule] シーンをダブルクリックすると、新しいシーンと共に表示される定義済みの項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c870-124">Double click "ASALearningmodule" scene to see some pre-defined items to appear along with the new scene.</span></span> 
3. <span data-ttu-id="2c870-125">混合現実開発のシーンを構成します。</span><span class="sxs-lookup"><span data-stu-id="2c870-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="2c870-127">注: [Mixed Reality Toolkit のプロファイル](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)を選択するためのポップアップダイアログボックスが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c870-127">Note: You may see a pop-up dialog box for selecting a [profile for the Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span></span> <span data-ttu-id="2c870-128">*DefaultHoloLens2ConfigurationProfile*という名前のプロファイルをダブルクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="2c870-128">Choose the profile named *DefaultHoloLens2ConfigurationProfile* by double-clicking it.</span></span>

4. <span data-ttu-id="2c870-129">MRTK のファイルを選択する場合は、[DefaultMixedRealityToolkitConfigurationProfile] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2c870-129">When choosing a file for the MRTK, select, DefaultMixedRealityToolkitConfigurationProfile.</span></span>

> <span data-ttu-id="2c870-130">注: 独自の構成プロファイルがある場合は、代わりに自由に使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c870-130">Note: If you have your own configuration profile, feel free to use that instead.</span></span>
>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="2c870-132">これで、シーンが混合現実用に構成されました。</span><span class="sxs-lookup"><span data-stu-id="2c870-132">Now the scene is configured for mixed reality.</span></span> <span data-ttu-id="2c870-133">シーンを保存していることを確認します (これを行うには、control/command + S を使用するか、[ファイル] をクリックして、[保存] をクリックします)。</span><span class="sxs-lookup"><span data-stu-id="2c870-133">Make sure you save your scene (do this with either control/command+S or click on file, then click on Save).</span></span> 

5. <span data-ttu-id="2c870-134">手順 1. でダウンロードした[Azure 空間アンカー v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) unity パッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="2c870-134">Import the [Azure Spatial Anchors v1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) unity package, that we downloaded in step 1.</span></span> <span data-ttu-id="2c870-135">その場合は、[資産] をクリックし、[パッケージのインポート] に移動します。</span><span class="sxs-lookup"><span data-stu-id="2c870-135">For that, click Assets, go down to Import Package.</span></span> <span data-ttu-id="2c870-136">[カスタムパッケージ] をクリックします。コンピューターのファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="2c870-136">Then click Custom Package... Your computer files will open.</span></span> <span data-ttu-id="2c870-137">その場合は、Azure 空間アンカーパッケージを保存した場所を見つけて、それを選択します。</span><span class="sxs-lookup"><span data-stu-id="2c870-137">When they do, find where you saved the Azure Spatial Anchors package, and select it.</span></span> <span data-ttu-id="2c870-138">[開く] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c870-138">Then click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

<span data-ttu-id="2c870-140">ポップアップが表示され、ツールと設定の一覧が表示され、インポートする内容を確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c870-140">A pop-up appears, providing a list of tools and settings, and asking you what to import.</span></span> <span data-ttu-id="2c870-141">使用可能な***すべて***のオプションを選択し、[インポート] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c870-141">Select ***all*** of the options available, then click Import.</span></span>

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> <span data-ttu-id="2c870-143">メモ: しばらくお待ちください。インポートには数分かかります。</span><span class="sxs-lookup"><span data-stu-id="2c870-143">Note: Be patient, it will take a few minutes to import.</span></span> 

6. <span data-ttu-id="2c870-144">[HoloLens2. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) next. をインポートします。</span><span class="sxs-lookup"><span data-stu-id="2c870-144">Import [Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) next.</span></span> <span data-ttu-id="2c870-145">手順 5. と同じように、Unity に戻り、[アセット] をクリックして、[インポートパッケージ] にカーソルを合わせます。</span><span class="sxs-lookup"><span data-stu-id="2c870-145">Much like Step 5, go back in to Unity, click Assets, and hover over Import Package.</span></span> <span data-ttu-id="2c870-146">[カスタムパッケージ] をクリックします。コンピューターのファイルが再び表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c870-146">Click Custom Package... Your computer files will appear again.</span></span> <span data-ttu-id="2c870-147">Base module Asset Pack を格納した場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="2c870-147">Go to where you stored the Base module Asset Pack.</span></span> <span data-ttu-id="2c870-148">を選択します。</span><span class="sxs-lookup"><span data-stu-id="2c870-148">and select it.</span></span> <span data-ttu-id="2c870-149">[開く] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c870-149">Click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> <span data-ttu-id="2c870-151">注: このモジュールでは、後で必要となる資産が増える場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c870-151">Note: There might be more assets needed later in this module.</span></span> <span data-ttu-id="2c870-152">ここで説明したアセットをインポートするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2c870-152">Follow these steps to import any assets mentioned from this point on.</span></span> 

7. <span data-ttu-id="2c870-153">他のパッケージをインポートする場合と同じ手順を使用して、 [ASA module pack 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage)をインポートします。</span><span class="sxs-lookup"><span data-stu-id="2c870-153">Import the [ASA module pack 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage) using the same steps as importing the other previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="2c870-154">シーンの構成</span><span class="sxs-lookup"><span data-stu-id="2c870-154">Configuring your scene</span></span>

<span data-ttu-id="2c870-155">このセクションでは、prefabs とスクリプトをシーンに追加して、アプリケーションでローカルアンカーと Azure 空間アンカーの両方が動作する方法の基礎を示す一連のボタンを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c870-155">In this section, we will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

8. <span data-ttu-id="2c870-156">[プロジェクト] タブの [アセット] フォルダーの下で、[ASAmoduleAssets] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c870-156">In the Project tab, underneath the Assets folder, click on ASAmoduleAssets.</span></span> <span data-ttu-id="2c870-157">選択すると、2つの prefabs: ButtonParent と ParentAnchor が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c870-157">Once selected, you will see two prefabs: ButtonParent and ParentAnchor.</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. <span data-ttu-id="2c870-159">両方の prefabs をシーンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2c870-159">Drag both prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

<span data-ttu-id="2c870-161">注: ButtonParent をシーンに追加すると、TMP アセットをインポートするように求めるポップアップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c870-161">Note: After adding the ButtonParent into the scene, a popup will appear asking you to import TMP assets.</span></span> <span data-ttu-id="2c870-162">"TMP Essentials" をインポートします。</span><span class="sxs-lookup"><span data-stu-id="2c870-162">Import the "TMP Essentials".</span></span> <span data-ttu-id="2c870-163">その後、シーンに大きなフォントテキストが表示された場合は、ButtonParent オブジェクトを削除し、ASAmoduleAssets フォルダーからもう一度追加します。</span><span class="sxs-lookup"><span data-stu-id="2c870-163">After this, If you see any large font text in the scene, delete the ButtonParent object and add it again from the ASAmoduleAssets folder.</span></span>

<span data-ttu-id="2c870-164">注: HoloLens のデバッグログを確認する場合は、</span><span class="sxs-lookup"><span data-stu-id="2c870-164">Note: If you want to check the debug logs in the HoloLens.</span></span> <span data-ttu-id="2c870-165">DebugWindow prefab を ASAModuleAssets フォルダーからシーンにドラッグアンドドロップできます。</span><span class="sxs-lookup"><span data-stu-id="2c870-165">You can drag and drop the DebugWindow prefab from ASAModuleAssets folder into the scene.</span></span> <span data-ttu-id="2c870-166">DebugWindow inspector パネルで DebugWindowMessaging スクリプトをアタッチし、[デバッグウィンドウを有効にする] オプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="2c870-166">Attach the DebugWindowMessaging script in the DebugWindow inspector panel and enable the Debug Window Enabled option.</span></span> <span data-ttu-id="2c870-167">その後、DebugWindow prefab を Debugwindow 空のフィールドにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="2c870-167">After that, drag  and drop the DebugWindow prefab into DebugText empty field.</span></span> <span data-ttu-id="2c870-168">また、必要に応じて、DebugWindow の位置を調整することもできます。</span><span class="sxs-lookup"><span data-stu-id="2c870-168">You can also adjust the DebugWindow position wherever appropriate for you.</span></span>

10. <span data-ttu-id="2c870-169">シーンを拡大するには、階層内の親アンカーをダブルクリックし、必要に応じてシーン全体を表示するようにビューを調整します。</span><span class="sxs-lookup"><span data-stu-id="2c870-169">In order to zoom in to the scene, double click on the parent anchor in the hierarchy and adjust your view to see the entire scene as needed.</span></span> <span data-ttu-id="2c870-170">現在、ParentAnchor は、デモンストレーションのみを目的として使用される色付きのキューブです。</span><span class="sxs-lookup"><span data-stu-id="2c870-170">Currently, ParentAnchor is a colored cube used for only demonstration purpose.</span></span> <span data-ttu-id="2c870-171">最終的には、キューブを非表示にして、コンテンツを ParentAnchor の子として配置します。</span><span class="sxs-lookup"><span data-stu-id="2c870-171">Eventually, we will hide the cube and place our content as a child of the ParentAnchor.</span></span> 

11. <span data-ttu-id="2c870-172">次に、シーンを操作するためのボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="2c870-172">Now lets configure the buttons for operating the scene.</span></span> <span data-ttu-id="2c870-173">そのためには、ButtonParent prefab を展開し、ラベルの付いたボタンをいくつか確認します。</span><span class="sxs-lookup"><span data-stu-id="2c870-173">For that, expand the ButtonParent prefab, and notice several labeled buttons.</span></span> <span data-ttu-id="2c870-174">これらのボタンは、MRTK の PressableButton prefabs から作成されます。</span><span class="sxs-lookup"><span data-stu-id="2c870-174">These buttons are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="2c870-175">[基本モジュール](mrlearning-base-ch2.md)から PressableButton を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c870-175">Learn more about how to create PressableButton from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="2c870-176">これらのボタンを操作するには、ユーザーが個々のボタンを押したとき、または選択したときにトリガーされるイベントを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c870-176">For these buttons to operate, we need to add an event which will be triggered when the user presses or selects the individual buttons.</span></span> 

- <span data-ttu-id="2c870-177">StartAzureSession という名前のボタンについては、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c870-177">For the Button named, StartAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="2c870-178">ParentAnchor オブジェクトを空のフィールドにドラッグし、次のスクリーンショットに示すように、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StartAzureSession () メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2c870-178">Drag the ParentAnchor object into the empty field, and assign the StartAzureSession() method from the ParentAnchor object's ASAmoduleScript component as shown in the below screenshot.</span></span>
- ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="2c870-182">ボタン名として [StopAzureSession] をクリックし、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c870-182">For the Button name, StopAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="2c870-183">ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StopAzureSession () メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2c870-183">Drag the ParentAnchor object into the empty field, and assign the StopAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="2c870-184">[CreateAnchor] という名前のボタンに対して、ボタン押されたイベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c870-184">For the Button named, CreateAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="2c870-185">ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから CreateAzureAnchor () メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2c870-185">Drag the ParentAnchor object into the empty field, and assign the CreateAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>  <span data-ttu-id="2c870-186">**その後、ParentAnchor を次の空の [Game Object] \ (ゲームオブジェクト \) フィールドにもう一度ドラッグします。**</span><span class="sxs-lookup"><span data-stu-id="2c870-186">**After this, drag the ParentAnchor again into the next empty "Game Object" field.**</span></span>

- <span data-ttu-id="2c870-187">という名前のボタンについては、アンカーの検索を開始し、Click Click イベントトリガーと On Click イベントトリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c870-187">For the Button named, Start Looking For Anchor, create a new event under the Button Press" event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="2c870-188">ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから FindAzureAnchor () メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2c870-188">Drag the ParentAnchor object into the empty field, and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="2c870-189">[DeleteAzureAnchor] という名前のボタンに対して、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c870-189">For the Button named, DeleteAzureAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="2c870-190">ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから DeleteAzureAnchor () メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2c870-190">Drag the ParentAnchor object into the empty field, and assign the DeleteAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>  

- <span data-ttu-id="2c870-191">[ローカルアンカーの削除] という名前のボタンに対して、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c870-191">For the Button named, Delete Local Anchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="2c870-192">ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから RemoveLocalAnchor () メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2c870-192">Drag the ParentAnchor object into the empty field, and assign the RemoveLocalAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span> <span data-ttu-id="2c870-193">**その後、ParentAnchor オブジェクトを、次の空の [Game Object] \ (ゲームオブジェクト \) フィールドにもう一度ドラッグします。**</span><span class="sxs-lookup"><span data-stu-id="2c870-193">**After this, drag the ParentAnchor object again into the next empty "Game Object" field.**</span></span>

12. <span data-ttu-id="2c870-194">Azure 空間アンカーを設定するには、assets フォルダー内の AzureSpatialAnchorsPlugin フォルダーに移動し、[例-> Resources-> AzureSpatialAnchorsDemoConfig file] に移動します。</span><span class="sxs-lookup"><span data-stu-id="2c870-194">To set up Azure spatial anchors, go to AzureSpatialAnchorsPlugin folder in assets folder and then navigate to Examples -> Resources->AzureSpatialAnchorsDemoConfig file.</span></span> <span data-ttu-id="2c870-195">[インスペクター] パネルで、先ほど作成した Azure アカウント ID とアカウントキーを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c870-195">In the inspector panel add the Azure Account ID and Account Key created earlier.</span></span> <span data-ttu-id="2c870-196">まだ作成していない場合、または所有していない場合は、[前提条件](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="2c870-196">If you haven't created or don't have the them, please follow the [Prerequisites](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span></span> 

  ![module2chapter1step13im](images/module2chapter1step13im.PNG)

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="2c870-198">基本アプリケーションのビルドとデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="2c870-198">Build and demonstrate Base Application</span></span>

<span data-ttu-id="2c870-199">ここでは、Azure 空間アンカーの基本を示すためにシーンが構成されたので、Azure 空間アンカーの基本的な動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c870-199">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="2c870-200">[ファイル > ビルドの設定] に移動して、[ビルドの設定] ウィンドウを再び開きます。</span><span class="sxs-lookup"><span data-stu-id="2c870-200">Open the build settings window again by going to File>Build Settings.</span></span>
    <span data-ttu-id="2c870-201">![mrlearning-ch1--ステップごとの](images/mrlearning-asa-ch1-3-step1.jpg)</span><span class="sxs-lookup"><span data-stu-id="2c870-201">![mrlearning-asa-ch1-3-step1](images/mrlearning-asa-ch1-3-step1.jpg)</span></span>
2. <span data-ttu-id="2c870-202">[開いているシーンを追加] ボタンをクリックして、目的のシーンがビルドリストのシーンにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2c870-202">Ensure the scene you want to try is in the Scenes in build list by clicking on the Add Open Scenes button.</span></span>
3. <span data-ttu-id="2c870-203">プラットフォームがユニバーサル Windows プラットフォームに設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2c870-203">Verify the Platform is set to Universal Windows Platform.</span></span> <span data-ttu-id="2c870-204">そうでない場合は、同じに設定してください。</span><span class="sxs-lookup"><span data-stu-id="2c870-204">If not, please set it to the same.</span></span>
4. <span data-ttu-id="2c870-205">[プレーヤーの設定] ボタンをクリックし、[発行の設定] にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2c870-205">Press the Player Settings button and go to Publishing Settings.</span></span> <span data-ttu-id="2c870-206">[機能] で、[インターネット]、[インターネットクライアントサーバー]、[プライベートネットワーククライアントサーバー]、[リムーバブル記憶域]、[Webcam]、[マイクと空間認識] を有効にします。</span><span class="sxs-lookup"><span data-stu-id="2c870-206">Under Capabilities, enable: Internet, Internet Client Server, Private Network Client Server, Removable Storage, Webcam, Microphone and Spatial Perception.</span></span>
5. <span data-ttu-id="2c870-207">同じプレーヤー設定で、XR settings にアクセスして、でサポートされている仮想現実を選択します。</span><span class="sxs-lookup"><span data-stu-id="2c870-207">In the same Player Settings, go to XR settings  and select the Virtual Reality Supported to ON.</span></span>
6. <span data-ttu-id="2c870-208">[ビルド] ボタンを押して、ビルド プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="2c870-208">Press the Build button to begin the build process.</span></span>
   <span data-ttu-id="2c870-209">![mrlearning-ch1-手順 6](images/mrlearning-asa-ch1-3-step6.jpg)</span><span class="sxs-lookup"><span data-stu-id="2c870-209">![mrlearning-asa-ch1-3-step6](images/mrlearning-asa-ch1-3-step6.jpg)</span></span>
7. <span data-ttu-id="2c870-210">アプリケーション用の新しいフォルダーを作成して、名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="2c870-210">Create and name a new folder for your application.</span></span> <span data-ttu-id="2c870-211">次の図では、アプリケーションを格納するために、App という名前のフォルダーが作成されています。</span><span class="sxs-lookup"><span data-stu-id="2c870-211">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="2c870-212">[フォルダーの選択] をクリックして、新しく作成したフォルダーへのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="2c870-212">Click Select Folder to begin building to the newly created folder.</span></span> <span data-ttu-id="2c870-213">ビルドが完了したら、Unity の [ビルドの設定] ウィンドウを閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="2c870-213">After the build has completed, you may close the Build Setting" window in Unity.</span></span>

    ![mrlearning-ch1-step7](images/mrlearning-asa-ch1-3-step7.jpg)

    > <span data-ttu-id="2c870-215">注: ビルドに失敗した場合は、もう一度ビルドするか、Unity を再起動して、もう一度ビルドしてみてください。</span><span class="sxs-lookup"><span data-stu-id="2c870-215">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="2c870-216">"エラー: CS0246 = 型または名前空間の名前" XX "が見つからないというエラーが表示された場合は、using ディレクティブまたはアセンブリ参照が不足しています。</span><span class="sxs-lookup"><span data-stu-id="2c870-216">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="2c870-217">[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)のインストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c870-217">You might need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span></span> 


8. <span data-ttu-id="2c870-218">ビルドが正常に完了した後でも、次のようにエラーが発生する可能性がありますが、ビルドが成功した場合は無視して次の手順に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="2c870-218">Even after a successful build you might get some errors as shown below but if the build is successful you can ignore them and proceed with next steps.</span></span>

    ![mrlearning-ch1-step7B](images/mrlearning-asa-ch1-3-step7B.png)

    

9. <span data-ttu-id="2c870-220">ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="2c870-220">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="2c870-221">"MixedRealityBase" ソリューションまたは対応する名前をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c870-221">Double click on the“MixedRealityBase.sln" solution or the corresponding name.</span></span> <span data-ttu-id="2c870-222">プロジェクトに代替名を使用して、Visual Studio でソリューションファイルを開く場合。</span><span class="sxs-lookup"><span data-stu-id="2c870-222">if you used an alternative name for your project to open the solution file in Visual Studio.</span></span>

    > <span data-ttu-id="2c870-223">メモ: 新しく作成されたフォルダー (つまり、前の手順の名前付け規則に従っている場合は、アプリフォルダー) を必ず開いてください。これは、ビルドフォルダー内の .sln ファイルと混同しないように、同じ名前の .sln ファイルがそのフォルダーの外部に存在するためです。</span><span class="sxs-lookup"><span data-stu-id="2c870-223">Note: Be sure to open the newly created folder (i.e., the App folder, if following the naming conventions from the previous steps because there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span>

    ![mrlearning-ch1-step8](images/mrlearning-asa-ch1-3-step8.jpg)

    > <span data-ttu-id="2c870-225">注: Visual Studio で新しいコンポーネントのインストールを求められた場合は、 [[ツールのインストール] ページ](install-the-tools.md)で、前提条件となるすべてのコンポーネントが特定のコンポーネントとしてインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2c870-225">Note: If Visual Studio asks to install new components, please take a moment to ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span>


9. <span data-ttu-id="2c870-226">USB ケーブルを使って HoloLens 2 を PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="2c870-226">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="2c870-227">これらのレッスンの手順では、HoloLens 2 デバイスでテストをデプロイすることを想定していますが、 [hololens 2 エミュレーター](using-the-hololens-emulator.md)にデプロイするか、[サイドローディング用のアプリパッケージの](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)作成を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="2c870-227">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

10. <span data-ttu-id="2c870-228">デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2c870-228">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="2c870-229">HoloLens 2 に初めてデプロイする場合は、Visual Studio により、PIN を使用して HoloLens 2 をペアリングするよう求められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c870-229">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="2c870-230">開発者モードを有効にする必要がある場合、または Visual Studio と組み合わせて使用する場合は、[次の手順](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)に従います。</span><span class="sxs-lookup"><span data-stu-id="2c870-230">Follow [these instructions](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

11. <span data-ttu-id="2c870-231">リリース構成と ARM アーキテクチャを選択して、HoloLens 2 にビルドするように Visual Studio を構成します。</span><span class="sxs-lookup"><span data-stu-id="2c870-231">Configure Visual Studio for building to your HoloLens 2 by selecting the Release configuration as well as the ARM architecture.</span></span>

    ![mrlearning-ch1-step11](images/mrlearning-asa-ch1-3-step11.jpg)


12. <span data-ttu-id="2c870-233">最後の手順は、デバッグ > デバッグなしで開始 を選択してデバイスにビルドすることです。</span><span class="sxs-lookup"><span data-stu-id="2c870-233">The final Step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="2c870-234">[デバッグなしで開始] を選択すると、Visual Studio にデバッグ情報が表示されずにビルドが成功したときに、アプリケーションがすぐにデバイスで起動します。</span><span class="sxs-lookup"><span data-stu-id="2c870-234">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="2c870-235">これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。</span><span class="sxs-lookup"><span data-stu-id="2c870-235">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="2c870-236">また、[ビルド > デプロイ] を選択して、アプリケーションを自動的に起動せずにデバイスにデプロイすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2c870-236">You might also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

    ![mrlearning-ch1-step12](images/mrlearning-asa-ch1-3-step12.jpg)

><span data-ttu-id="2c870-238">注: Azure 空間アンカーは、インターネットを使用してアンカーデータを保存して読み込みます。そのため、ASA アプリをテストする前に、デバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2c870-238">Note: The Azure spatial anchors uses the internet to save and load the anchor data so make sure your device is connected to internet before testing the ASA app.</span></span>

13. <span data-ttu-id="2c870-239">画面の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="2c870-239">Follow the instructions.</span></span> 
    <span data-ttu-id="2c870-240">デバイスでアプリケーションが実行されている場合は、画面の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="2c870-240">When the application is running on your device, follow the on-screen instructions.</span></span> <span data-ttu-id="2c870-241">次の手順に対応するシーンボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="2c870-241">Press the Scene buttons corresponding to the Steps below.</span></span> <span data-ttu-id="2c870-242">前の手順で説明したようにデバッグウィンドウを追加した場合は、個々のボタンの押下に関するフィードバックと、Azure 空間アンカーに関連する個々の操作の進行状況を確認できます。</span><span class="sxs-lookup"><span data-stu-id="2c870-242">If you added the debug window as mentioned in the previous steps you can see the feedback for individual button press and the progress of individual operations related to Azure spatial anchors.</span></span>

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="2c870-244">空間アンカーセッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="2c870-244">Start the spatial anchors session.</span></span>
    
    2. <span data-ttu-id="2c870-245">キューブを別の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="2c870-245">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="2c870-246">キューブの場所に Azure 空間アンカーを保存します。</span><span class="sxs-lookup"><span data-stu-id="2c870-246">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="2c870-247">Azure 空間アンカーセッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="2c870-247">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="2c870-248">キューブのローカルアンカーを削除して、ユーザーがキューブを移動できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2c870-248">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    
    6. <span data-ttu-id="2c870-249">キューブを別の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="2c870-249">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="2c870-250">Azure 空間アンカーセッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="2c870-250">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="2c870-251">Azure 空間アンカーを検索します。</span><span class="sxs-lookup"><span data-stu-id="2c870-251">Find Azure Spatial Anchors.</span></span> 
    <span data-ttu-id="2c870-252">アンカーを作成したときに、元の場所に戻ります。</span><span class="sxs-lookup"><span data-stu-id="2c870-252">You should go back to the original place you put it when you created the anchor.</span></span>
    
    9. <span data-ttu-id="2c870-253">Azure 空間アンカーを削除します。</span><span class="sxs-lookup"><span data-stu-id="2c870-253">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="2c870-254">Azure セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="2c870-254">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="2c870-255">エクスペリエンスを固定する</span><span class="sxs-lookup"><span data-stu-id="2c870-255">Anchoring an experience</span></span>

<span data-ttu-id="2c870-256">前のセクションでは、Azure 空間アンカーの基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="2c870-256">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="2c870-257">キューブを使用して、アタッチされたアンカーで親ゲームオブジェクトを表現し、視覚化しました。</span><span class="sxs-lookup"><span data-stu-id="2c870-257">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="2c870-258">このセクションでは、ParentAnchor オブジェクトの子として配置することで、エクスペリエンス全体を固定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c870-258">In this section, you learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="2c870-259">この例では、「[基本モジュールレッスン 6](mrlearning-base-ch6.md)」で作成した旧暦モジュールアセンブリデモンストレーションアプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c870-259">For this example, we use the lunar module Assembly demonstration application that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="2c870-260">"ロケットランチャー Complete" prefab を検索し、次の図に示すように、オブジェクトの子として階層にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2c870-260">Search for the "Rocket Launcher Complete" prefab, and drag it into your hierarchy as a child of the object as shown in the image below.</span></span>

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="2c870-262">次の図に示すように、モジュールのアセンブリエクスペリエンスを配置して、キューブが引き続き公開されるようにします。</span><span class="sxs-lookup"><span data-stu-id="2c870-262">Position the module assembly experience so that the cube is still exposed as shown in the image below.</span></span> <span data-ttu-id="2c870-263">アプリケーションでは、ユーザーはキューブを移動することで、エクスペリエンス全体を再配置できます。</span><span class="sxs-lookup"><span data-stu-id="2c870-263">In the application, users may reposition the entire experience by moving the cube.</span></span> 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> <span data-ttu-id="2c870-265">注: エクスペリエンスを再配置するためのさまざまなユーザーエクスペリエンスフローがあります。たとえば、ボタンを使用して、操作を囲む境界ボックスの切り替え、オブジェクトの再配置 (この手順で使用されるキューブなど)、位置と回転の使用などがあります。ギズモなど。</span><span class="sxs-lookup"><span data-stu-id="2c870-265">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2c870-266">結論</span><span class="sxs-lookup"><span data-stu-id="2c870-266">Congratulations</span></span>
<span data-ttu-id="2c870-267">このチュートリアルでは、Azure 空間アンカーの基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="2c870-267">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="2c870-268">このレッスンでは、Azure セッションを開始および停止するために必要なさまざまな手順を説明し、1つのデバイスで azure のアンカーを作成、アップロード、ダウンロードするためのボタンをいくつか紹介しました。</span><span class="sxs-lookup"><span data-stu-id="2c870-268">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session, and create, upload, and download azure anchors on a single device.</span></span> <span data-ttu-id="2c870-269">次のレッスンでは、アプリケーションを再起動した後でも、Azure anchor Id を HoloLens 2 に保存して取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c870-269">In the next lesson, we'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="2c870-270">このシリーズでは、空間アラインメントを実現するために複数のデバイス間でアンカー Id を転送する方法や、マルチユーザー共有セッションについて学習する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="2c870-270">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment, and learn about multi-user shared sessions, forthcoming as part of Sharing tutorial.</span></span>

[<span data-ttu-id="2c870-271">次のレッスン: 2. Azure 空間アンカーの保存、取得、共有</span><span class="sxs-lookup"><span data-stu-id="2c870-271">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)

