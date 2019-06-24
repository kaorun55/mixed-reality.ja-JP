---
title: MR Learning ASA モジュール HoloLens 2 での Azure 空間アンカー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 7843e4de014fe14d7c40b5e6d68f72ea45b4df9e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326892"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a><span data-ttu-id="880d9-104">HoloLens 2 で空間アンカーを Azure の概要</span><span class="sxs-lookup"><span data-stu-id="880d9-104">Getting Started with Azure Spatial Anchors on HoloLens 2</span></span>

<span data-ttu-id="880d9-105">2 番目のモジュールの HoloLens 2 のチュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="880d9-105">Welcome to the second module of the HoloLens 2 Tutorial!</span></span> <span data-ttu-id="880d9-106">始める前に、必ずすべての[の前提条件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)が完了します。</span><span class="sxs-lookup"><span data-stu-id="880d9-106">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="880d9-107">まず、完了していない場合[ベース モジュール](mrlearning-base.md)まだ、強くお勧めその最初が完了することです。</span><span class="sxs-lookup"><span data-stu-id="880d9-107">If you have not completed the first, [base module](mrlearning-base.md) yet, we highly recommend that you complete that first.</span></span> <span data-ttu-id="880d9-108">新しい unity プロジェクトから開始する場合は 新しいプロジェクトの作成手順に従ってください、[ベース モジュール](mrlearning-base.md)します。</span><span class="sxs-lookup"><span data-stu-id="880d9-108">If you are starting from a new unity project, follow the new project creation steps in the [base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="880d9-109">目標</span><span class="sxs-lookup"><span data-stu-id="880d9-109">Objectives</span></span>

* <span data-ttu-id="880d9-110">HoloLens 2 Azure 空間アンカーを使用した開発の基礎を学習します。</span><span class="sxs-lookup"><span data-stu-id="880d9-110">Learn the fundamentals of developing with Azure Spatial Anchors with the HoloLens 2</span></span>

* <span data-ttu-id="880d9-111">作成、アップロード、および空間アンカーのダウンロード</span><span class="sxs-lookup"><span data-stu-id="880d9-111">Create, Upload, and Download Spatial Anchors</span></span>

  

## <a name="instructions"></a><span data-ttu-id="880d9-112">手順</span><span class="sxs-lookup"><span data-stu-id="880d9-112">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="880d9-113">ダウンロードとアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="880d9-113">Downloading and Importing Assets</span></span>
<span data-ttu-id="880d9-114">始める前は、ダウンロードして、次のアセットをインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="880d9-114">Before beginning, you must download and import the following assets:</span></span>

[<span data-ttu-id="880d9-115">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="880d9-115">Azure Spatial Anchors</span></span>](https://github.com/azure/azure-spatial-anchors-samples/releases)

[<span data-ttu-id="880d9-116">資産パックの MR ベース モジュール</span><span class="sxs-lookup"><span data-stu-id="880d9-116">MR Base module Asset Pack</span></span>](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[<span data-ttu-id="880d9-117">ASA モジュール資産パック</span><span class="sxs-lookup"><span data-stu-id="880d9-117">ASA module Asset Pack</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[<span data-ttu-id="880d9-118">Mixed Reality ツールキット</span><span class="sxs-lookup"><span data-stu-id="880d9-118">Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> <span data-ttu-id="880d9-119">注: Azure 空間アンカー、MR ベース モジュール資産パックの具体的な手順について、手順 6、および Mixed Reality Toolkit の具体的な手順について、手順 3 ~ 4 をインポートする方法の具体的な手順については、手順 5 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="880d9-119">Note: see step 5 for specific instructions on how to import the Azure Spatial Anchors, step 6 for specific instructions on the MR Base module Asset Pack, and steps 3-4 for specific instructions on the Mixed Reality Toolkit.</span></span>

1. <span data-ttu-id="880d9-120">プロジェクトに新しいシーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="880d9-120">create a new scene in your project.</span></span> <span data-ttu-id="880d9-121">シーンのフォルダーを右クリックして、「作成、」シーンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="880d9-121">Right click your scene folder, click "create," then scene.</span></span> <span data-ttu-id="880d9-122">名前を新しいシーン"ASALearningmodule"</span><span class="sxs-lookup"><span data-stu-id="880d9-122">Name the new scene "ASALearningmodule."</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="880d9-124">"ASALearningmodule"をダブルクリック、新しいシーンと共に表示されるいくつか事前定義済みの項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="880d9-124">Double click "ASALearningmodule" to see some pre-defined items appear along with the new scene.</span></span> 
3. <span data-ttu-id="880d9-125">複合現実の開発のシーンを構成します。</span><span class="sxs-lookup"><span data-stu-id="880d9-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="880d9-127">注:示すポップアップが表示されます、「ファイルは Mixed Reality ツールキットを選択する必要があります」します。</span><span class="sxs-lookup"><span data-stu-id="880d9-127">Note: You will see a pop-up that says, "you must choose a file for the Mixed Reality Toolkit."</span></span> <span data-ttu-id="880d9-128">[Ok] の順にクリックでは、手順 4 に表示されます。</span><span class="sxs-lookup"><span data-stu-id="880d9-128">Clicking "ok" will bring you to step 4.</span></span>

4. <span data-ttu-id="880d9-129">Mixed Reality Toolkit のファイルを選択するときに選択して、"DefaultMixedRealityToolkitConfigurationProfile"</span><span class="sxs-lookup"><span data-stu-id="880d9-129">When choosing a file for the Mixed Reality Toolkit, select, "DefaultMixedRealityToolkitConfigurationProfile."</span></span>

   > <span data-ttu-id="880d9-130">注:独自の構成プロファイルを自由に代わりに使用する場合は。</span><span class="sxs-lookup"><span data-stu-id="880d9-130">Note: If you have your own configuration profile feel free to use that instead.</span></span>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="880d9-132">シーンを複合現実用に構成されました。</span><span class="sxs-lookup"><span data-stu-id="880d9-132">Now the scene is configured for mixed reality.</span></span> <span data-ttu-id="880d9-133">シーンを保存してください (どちらのコントロールで行う/コマンド + S、またはファイルをクリックします をクリックして保存) します。</span><span class="sxs-lookup"><span data-stu-id="880d9-133">Make sure you save your scene (do this with either control/command+S, or click on file, then click on save).</span></span> 

5. <span data-ttu-id="880d9-134">インポート、 [Azure 空間アンカー](https://github.com/azure/azure-spatial-anchors-samples/releases)します。</span><span class="sxs-lookup"><span data-stu-id="880d9-134">Import the [Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases).</span></span> <span data-ttu-id="880d9-135">空間アンカーを使用するには、このアセットをインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="880d9-135">In order to use spatial anchors, you must import this asset.</span></span> <span data-ttu-id="880d9-136">そのため、上記のリンクをクリックし、"AzureSpatialAnchors.unitypackage"を右クリックしてください</span><span class="sxs-lookup"><span data-stu-id="880d9-136">So, click on the link above and right click on "AzureSpatialAnchors.unitypackage."</span></span> <span data-ttu-id="880d9-137">"ターゲット"の保存と保存をコンピューターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="880d9-137">Click on "save target as" and save it to your computer.</span></span> 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   <span data-ttu-id="880d9-139">次に保存した後、unity に戻り、[アセット、"パッケージのインポート"、"まで移動では、「カスタム パッケージ...」] をクリックしてコンピューターのファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="880d9-139">Then, after it's saved, go back into unity, click "assets," go down to "import package," then click "custom package..." Your computer files will open up.</span></span> <span data-ttu-id="880d9-140">1 回の操作を行いますが、Azure 空間アンカー パッケージを保存した検索および選択します。</span><span class="sxs-lookup"><span data-stu-id="880d9-140">Once they do, find where you saved the Azure Spatial Anchors package and select it.</span></span> <span data-ttu-id="880d9-141">クリックして「を開きます」</span><span class="sxs-lookup"><span data-stu-id="880d9-141">Then click "open."</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   <span data-ttu-id="880d9-143">今すぐ与える一連のツールと設定をインポートするように求めるポップアップがあります。</span><span class="sxs-lookup"><span data-stu-id="880d9-143">Now there will be a popup giving a list of tools and settings, asking you what to import.</span></span> <span data-ttu-id="880d9-144">選択***すべて***"使用可能なオプションのインポート をクリックします。</span><span class="sxs-lookup"><span data-stu-id="880d9-144">Select ***all*** of the options available, then click "import."</span></span>

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > <span data-ttu-id="880d9-146">注: インポートする場合に、これには数分かかります待ちください。</span><span class="sxs-lookup"><span data-stu-id="880d9-146">note: it will take a few minutes to import, so please be patient.</span></span> 

   6. <span data-ttu-id="880d9-147">インポート[MR ベース モジュール資産パック](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)[次へ]。</span><span class="sxs-lookup"><span data-stu-id="880d9-147">Import [MR Base module Asset Pack](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) next.</span></span> <span data-ttu-id="880d9-148">手順 5 と同じように上記のリンクをクリックして、"BasemoduleAssetsV1 1.unitypackage"を右クリックして、コンピューターに"ターゲット"の保存と保存をクリックします。</span><span class="sxs-lookup"><span data-stu-id="880d9-148">Much like step 5, click the link above, then right click "BasemoduleAssetsV1 1.unitypackage" and click "save target as" and save it to your computer.</span></span>

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > <span data-ttu-id="880d9-150">ヒント:簡単に見つけにアクセスできるように、同じフォルダーにこれらすべての資産を保存します。</span><span class="sxs-lookup"><span data-stu-id="880d9-150">Tip: Save all these assets in the same folder so that they are easier to find and have access to.</span></span> <span data-ttu-id="880d9-151">便利で、構成されたすべてのものが維持されます。</span><span class="sxs-lookup"><span data-stu-id="880d9-151">It will keep everything nice and organized!</span></span>

   <span data-ttu-id="880d9-152">手順に戻り、unity に移動して、5 と同じようには、「資産」、「パッケージのインポート」にマウスをクリックし、「カスタム パッケージ.」をクリックします。もう一度、コンピューターのファイルが表示されますので資産パックのベース モジュールを格納した場所に移動され、選択。</span><span class="sxs-lookup"><span data-stu-id="880d9-152">Just like step 5, go back in to unity, click "assets," hover over "import package" then click "custom package..." Your computer files should appear again, so go to where you stored the Base module Asset Pack and select it.</span></span> <span data-ttu-id="880d9-153">クリックして「を開きます」</span><span class="sxs-lookup"><span data-stu-id="880d9-153">Then click "open."</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > <span data-ttu-id="880d9-155">注: がこのモジュールで後で必要な複数のアセットがあります。</span><span class="sxs-lookup"><span data-stu-id="880d9-155">Note: there may be more assets needed later in this module.</span></span> <span data-ttu-id="880d9-156">この時点で説明されているすべてのアセットをインポートする次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="880d9-156">Follow these steps to import any assets mentioned from this point on.</span></span> 

7. <span data-ttu-id="880d9-157">ASA モジュールの以前のパッケージのインポートと同じアプローチを使用してパックをインポートします。</span><span class="sxs-lookup"><span data-stu-id="880d9-157">Import the ASA module Pack using the same approach as importing the previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="880d9-158">シーンの構成</span><span class="sxs-lookup"><span data-stu-id="880d9-158">Configuring your scene</span></span>

<span data-ttu-id="880d9-159">このセクションで追加される予定プレハブとスクリプトの一連のアプリケーションでのローカルのアンカーと空間アンカーを Azure の両方の動作方法の基礎を説明するボタンを作成するシーンに。</span><span class="sxs-lookup"><span data-stu-id="880d9-159">In this section, we will be adding prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

7. <span data-ttu-id="880d9-160">「プロジェクト」 タブで、アセット フォルダーの下に、"ASAmoduleAssets。"をクリックします。</span><span class="sxs-lookup"><span data-stu-id="880d9-160">In the "project" tab, underneath the "assets" folder, click on "ASAmoduleAssets."</span></span> <span data-ttu-id="880d9-161">選択したら、"ButtonParent"と"ParentAnchor"の 2 つのプレハブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="880d9-161">Once selected you will see 2 prefabs, "ButtonParent" and "ParentAnchor."</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. <span data-ttu-id="880d9-163">シーンのプレハブの両方にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="880d9-163">Drag both of the prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. <span data-ttu-id="880d9-165">親のアンカーをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="880d9-165">Double click on the parent anchor to select it.</span></span> <span data-ttu-id="880d9-166">シーン全体を参照してください、そのため、必要に応じて、シーンを調整する表示を調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="880d9-166">You may need to adjust your view to see the entire scene, so adjust your scene as needed.</span></span>

    <span data-ttu-id="880d9-167">ParentAnchor プレハブを理解します。</span><span class="sxs-lookup"><span data-stu-id="880d9-167">Familiarize yourself with the ParentAnchor prefab.</span></span> <span data-ttu-id="880d9-168">現時点では、"ParentAnchor"という名前のゲーム オブジェクトには、デモンストレーション用の色付きのキューブです。</span><span class="sxs-lookup"><span data-stu-id="880d9-168">Currently, the game object named "ParentAnchor" is a colored cube, for demonstration purposes.</span></span> <span data-ttu-id="880d9-169">最終的には、キューブを非表示にはされ、ParentAnchor の子として、コンテンツを配置します。</span><span class="sxs-lookup"><span data-stu-id="880d9-169">Eventually, we will hide the cube and place our content as a child of the ParentAnchor.</span></span> <span data-ttu-id="880d9-170">このプレハブには、(ASA SDK に含まれる) AzureSpatialAnchorsDemoWrapper.cs スクリプトと ParentAnchor オブジェクトに ASAmoduleScript.cs スクリプト (このモジュールの一部として含まれています) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="880d9-170">This prefab includes the AzureSpatialAnchorsDemoWrapper.cs script (included with the ASA SDK) and the ASAmoduleScript.cs script (included as part of this module) to the ParentAnchor object.</span></span> 

10. <span data-ttu-id="880d9-171">ボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="880d9-171">Configure Buttons.</span></span> <span data-ttu-id="880d9-172">ParentAnchor プレハブ、いくつかのラベルの付いたボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="880d9-172">Under the ParentAnchor prefab, you will notice several labeled buttons.</span></span> <span data-ttu-id="880d9-173">これらのボタンは、MRTK の PressableButton のプレハブから作成されます。</span><span class="sxs-lookup"><span data-stu-id="880d9-173">These buttons are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="880d9-174">Pressable ボタンを作成する方法について説明します、[ベース モジュール](mrlearning-base-ch2.md)します。</span><span class="sxs-lookup"><span data-stu-id="880d9-174">Learn more about how to create Pressable Buttons from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="880d9-175">各ボタンを押すか、以下の一覧に従ってボタンを選択したときにトリガーされるイベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="880d9-175">For each button, add an event that will be triggered when the user presses or selects the button according to the list below.</span></span> 

- <span data-ttu-id="880d9-176">"StartAzureSession"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="880d9-176">For the Button named "StartAzureSession", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="880d9-177">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StartAzureSession() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="880d9-177">Drag the ParentAnchor object into the empty field, and assign the StartAzureSession() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="880d9-181">"StopAzureSession"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="880d9-181">For the Button named "StopAzureSession", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="880d9-182">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StopAzureSession() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="880d9-182">Drag the ParentAnchor object into the empty field, and assign the StopAzureSession() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="880d9-183">"CreateAnchor"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="880d9-183">For the Button named "CreateAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="880d9-184">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから CreateAzureAnchor() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="880d9-184">Drag the ParentAnchor object into the empty field, and assign the CreateAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="880d9-185">「開始お探しのアンカー」をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="880d9-185">For the Button named "Start Looking For Anchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="880d9-186">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから FindAzureAnchor() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="880d9-186">Drag the ParentAnchor object into the empty field, and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="880d9-187">"DeleteAzureAnchor"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="880d9-187">For the Button named "DeleteAzureAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="880d9-188">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから DeleteAzureAnchor() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="880d9-188">Drag the ParentAnchor object into the empty field, and assign the DeleteAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="880d9-189">「ローカル アンカーの削除」をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="880d9-189">For the Button named "Delete Local Anchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="880d9-190">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから RemoveLocalAnchor() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="880d9-190">Drag the ParentAnchor object into the empty field, and assign the RemoveLocalAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="880d9-191">ビルドし、ベース アプリケーションのデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="880d9-191">Build and Demonstrate Base Application</span></span>

<span data-ttu-id="880d9-192">これで、シーンは Azure 空間アンカーの基本について説明する構成は作成し、Azure 空間アンカーの基本的な動作を示します。</span><span class="sxs-lookup"><span data-stu-id="880d9-192">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="880d9-193">前のセクションで [ビルド設定] ウィンドウを閉じた場合は、[ファイル] > [ビルド設定] の順に移動して [ビルド設定] ウィンドウを再度開きます。</span><span class="sxs-lookup"><span data-stu-id="880d9-193">If you closed the Build Settings window from the previous sections, open the build settings window again by going to File>Build Settings.</span></span>
    <span data-ttu-id="880d9-194">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="880d9-194">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span></span>

2. <span data-ttu-id="880d9-195">[開いているシーンの追加] ボタンをクリックして、試したいシーンが [ビルド内のシーン] リストに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="880d9-195">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>

3. <span data-ttu-id="880d9-196">[ビルド] ボタンを押して、ビルド プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="880d9-196">Press the Build button to begin the build process.</span></span>
    <span data-ttu-id="880d9-197">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="880d9-197">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span></span>

4. <span data-ttu-id="880d9-198">アプリケーション用の新しいフォルダーを作成して、名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="880d9-198">Create and name a new folder for your application.</span></span> <span data-ttu-id="880d9-199">下の図では、アプリケーションを含めるために [App] という名前のフォルダーが作成されています。</span><span class="sxs-lookup"><span data-stu-id="880d9-199">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="880d9-200">[フォルダーの選択] をクリックして、新しく作成したフォルダーへのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="880d9-200">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="880d9-201">ビルドが完了したら、Unity の [ビルド設定] ウィンドウを閉じてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="880d9-201">After the build has completed, you may close the "Build Settings" window in Unity.</span></span> 
    <span data-ttu-id="880d9-202">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="880d9-202">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span></span>

  > <span data-ttu-id="880d9-203">注: ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。</span><span class="sxs-lookup"><span data-stu-id="880d9-203">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="880d9-204">エラー:CS0246 = tyoe または名前空間の名前が"XX"が見つかりませんでした (が存在することを使用して、ディレクティブまたはアセンブリ参照か)"、をインストールする必要がありますし、 [Windows 10 SDK (10.0.18362.0)。](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="880d9-204">If you see an error such as "Error: CS0246 = The tyoe or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", then you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span> 
  >

5. <span data-ttu-id="880d9-205">ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="880d9-205">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="880d9-206">[MixedRealityBase.sln] ソリューション (または、プロジェクトの代替名を使用した場合は対応する名前) をダブルクリックして、Visual Studio でソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="880d9-206">Double click on the “MixedRealityBase.sln” solution (or the corresponding name, if you used an alternative name for your project) to open the solution file in Visual Studio.</span></span>

  > <span data-ttu-id="880d9-207">注:必ず、新しく作成したフォルダー (つまり、前の手順で名前付け規則に従っている場合は、[App] フォルダー) を開いてください。そのフォルダーの外部に同じような名前の .sln ファイルがあり、ビルド フォルダー内の .sln ファイルと混同してはならないためです。</span><span class="sxs-lookup"><span data-stu-id="880d9-207">Note: Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > <span data-ttu-id="880d9-209">注:Visual studio の新しいコンポーネントをインストールする場合、ご協力くださいにすべての前提条件となるコンポーネントがインストールされていることを確認します具体的に["ツールをインストールする ページ。](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="880d9-209">Note: If visual studio asks to install new components, please take a moment to ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span> 

6. <span data-ttu-id="880d9-210">USB ケーブルを使って HoloLens 2 を PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="880d9-210">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="880d9-211">レッスンの手順では、HoloLens 2 デバイスでのテスト、デプロイする前提としています、中にすることもできますを展開する、 [HoloLens 2 エミュレーター](using-the-hololens-emulator.md)を作成することも、[サイドローディング用アプリ パッケージ](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="880d9-211">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="880d9-212">デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="880d9-212">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="880d9-213">HoloLens 2 に初めてデプロイする場合は、Visual Studio により、PIN を使用して HoloLens 2 をペアリングするよう求められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="880d9-213">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="880d9-214">開発者モードを有効にするか、Visual Studio とペアリングする必要がある場合は、[こちらの手順](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="880d9-214">Please follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="880d9-215">[リリース] 構成と [ARM] アーキテクチャを選択して、HoloLens 2 へのビルド用に Visual Studio を構成します。</span><span class="sxs-lookup"><span data-stu-id="880d9-215">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>
    <span data-ttu-id="880d9-216">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span><span class="sxs-lookup"><span data-stu-id="880d9-216">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span></span>
    
9. <span data-ttu-id="880d9-217">最後に、デバッグを選択して、デバイスにビルド > デバッグなしで開始します。</span><span class="sxs-lookup"><span data-stu-id="880d9-217">The final Step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="880d9-218">[デバッグなしで開始] を選択すると、ビルドが成功した時点でアプリケーションがデバイスですぐに起動しますが、Visual Studio にデバッグ情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="880d9-218">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="880d9-219">これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。</span><span class="sxs-lookup"><span data-stu-id="880d9-219">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="880d9-220">また、[ビルド] > [ソリューションの配置] を選択することで、アプリケーションを自動的に起動せずにデバイスに配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="880d9-220">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>
    <span data-ttu-id="880d9-221">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span><span class="sxs-lookup"><span data-stu-id="880d9-221">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span></span>
    
10. <span data-ttu-id="880d9-222">アプリケーションは、デバイスで実行中は、次の画面に表示される手順。</span><span class="sxs-lookup"><span data-stu-id="880d9-222">When the application is running on your device, please follow the on-screen instructions.</span></span> <span data-ttu-id="880d9-223">次の手順に対応するシーン ボタンを押してください。</span><span class="sxs-lookup"><span data-stu-id="880d9-223">Please press the scene buttons corresponding to the Steps below.</span></span>
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="880d9-225">Azure の空間アンカー セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="880d9-225">Start the Azure spatial anchors session.</span></span>
    
    2. <span data-ttu-id="880d9-226">キューブは、別の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="880d9-226">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="880d9-227">キューブの位置にある Azure 空間アンカーを保存します。</span><span class="sxs-lookup"><span data-stu-id="880d9-227">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="880d9-228">Azure の空間アンカー セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="880d9-228">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="880d9-229">ユーザーがキューブに移動を許可するキューブ上でローカルのアンカーを削除します。</span><span class="sxs-lookup"><span data-stu-id="880d9-229">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    6. <span data-ttu-id="880d9-230">キューブの別の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="880d9-230">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="880d9-231">Azure の空間アンカー セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="880d9-231">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="880d9-232">Azure の空間アンカーを検索します。</span><span class="sxs-lookup"><span data-stu-id="880d9-232">Find Azure spatial anchors.</span></span>
    <span data-ttu-id="880d9-233">(キューブが元の場所に戻るにはこれで配置することが、アンカーを作成したときに)。</span><span class="sxs-lookup"><span data-stu-id="880d9-233">(now cube should go back to the original place you put it when you created the anchor).</span></span>
    9. <span data-ttu-id="880d9-234">Azure の空間アンカーを削除します。</span><span class="sxs-lookup"><span data-stu-id="880d9-234">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="880d9-235">Azure のセッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="880d9-235">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="880d9-236">アンカーのエクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="880d9-236">Anchoring an experience</span></span>

<span data-ttu-id="880d9-237">前のセクションでは、空間のアンカーを Azure の基礎について説明しました。</span><span class="sxs-lookup"><span data-stu-id="880d9-237">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="880d9-238">表し、添付のアンカーを持つ親ゲーム オブジェクトを視覚化するキューブを使用しています。</span><span class="sxs-lookup"><span data-stu-id="880d9-238">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="880d9-239">このセクションでは、wiill するは、ParentAnchor オブジェクトの子として配置することによって、エクスペリエンス全体を固定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="880d9-239">In this section, you wiill learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="880d9-240">この例では、中に作成された旧暦モジュール アセンブリのデモ アプリを使用しますが[レッスン 6 のベース モジュール](mrlearning-base-ch6.md)します。</span><span class="sxs-lookup"><span data-stu-id="880d9-240">For this example, we will use the Lunar module Assembly demo app that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="880d9-241">旧暦モジュール アセンブリの完全なプレハブを検索し、ドラッグ、階層に AnchorParent の gameobject の子として次の図に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="880d9-241">Search for the Lunar module Assembly Complete prefab and drag it into your heirarchy as a child of the AnchorParent gameobject, as shown in the image below.</span></span>

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="880d9-243">次の図に示すように、このような方法をキューブがまだ公開されることでモジュール アセンブリのエクスペリエンスを配置します。</span><span class="sxs-lookup"><span data-stu-id="880d9-243">Position the module assembly experience in such a way that the cube is still exposed, as shown in the image below.</span></span> <span data-ttu-id="880d9-244">アプリケーションでは、ユーザーは、全体のエクスペリエンスをキューブに移動することによって再配置することができます。</span><span class="sxs-lookup"><span data-stu-id="880d9-244">In the application, users may reposition the entire experience by moving the cube.</span></span> 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > <span data-ttu-id="880d9-246">注:さまざまなユーザー エクスペリエンスのフローを経験を囲む境界ボックスを切り替え、位置と回転ギズモの使用を (この手順で使用)、キューブなどの再配置オブジェクトを使用するボタンの使用など、エクスペリエンスを再配置します。、など。</span><span class="sxs-lookup"><span data-stu-id="880d9-246">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="880d9-247">結論</span><span class="sxs-lookup"><span data-stu-id="880d9-247">Congratulations</span></span>
<span data-ttu-id="880d9-248">このレッスンでは、空間のアンカーを Azure の基礎について説明しました。</span><span class="sxs-lookup"><span data-stu-id="880d9-248">In this Lesson, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="880d9-249">このレッスンは、いくつかのボタンを起動し、Azure のセッションを停止するために必要なさまざまな手順の詳細し作成、アップロード、および 1 つのデバイスでの azure のアンカーをダウンロードすることができますを提供します。</span><span class="sxs-lookup"><span data-stu-id="880d9-249">This Lesson provided you with several buttons allowing you to explore the various steps required to start and stop an Azure session, and create, upload, and download azure anchors on a single device.</span></span> <span data-ttu-id="880d9-250">次のレッスンでは、アプリケーションの再起動後も、HoloLens の 2 を取得するために Azure のアンカー Id を保存する方法説明します。</span><span class="sxs-lookup"><span data-stu-id="880d9-250">In the next Lesson, we'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="880d9-251">シリーズの中には、空間の配置を実現するために複数のデバイス間にアンカー Id を転送する方法についても説明し、最終的に複数のユーザーが共有セッション (近日公開予定のモジュールを共有の一部として。) について説明します</span><span class="sxs-lookup"><span data-stu-id="880d9-251">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment, and eventually learn about multi-user shared sessions (forthcoming as part of sharing module.)</span></span>

[<span data-ttu-id="880d9-252">次のレッスン:ASA Lesson 2</span><span class="sxs-lookup"><span data-stu-id="880d9-252">Next Lesson: ASA Lesson 2</span></span>](mrlearning-asa-ch2.md)

