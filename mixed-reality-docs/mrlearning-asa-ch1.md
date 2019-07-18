---
title: MR Learning ASA モジュール Azure 空間アンカー (HoloLens 2)
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 690ece3a02aeefd598db18baa66de3ddabfa43eb
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293820"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="24eb2-104">1. Azure 空間アンカーの概要</span><span class="sxs-lookup"><span data-stu-id="24eb2-104">1. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="24eb2-105">HoloLens 2 チュートリアルの2番目のモジュールへようこそ。</span><span class="sxs-lookup"><span data-stu-id="24eb2-105">Welcome to the second module of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="24eb2-106">作業を開始する前に、すべての[前提条件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)が満たされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="24eb2-106">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="24eb2-107">最初の[ベースモジュール](mrlearning-base.md)をまだ完了していない場合は、最初にそのモジュールを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-107">If you have not completed the first, [Base module](mrlearning-base.md) yet, it's recommended that you complete that module first.</span></span> <span data-ttu-id="24eb2-108">新しい Unity プロジェクトから開始する場合は、[ベースモジュール](mrlearning-base.md)の新しいプロジェクト作成手順に従います。</span><span class="sxs-lookup"><span data-stu-id="24eb2-108">If you are starting from a new Unity project, follow the new project creation steps in the [Base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="24eb2-109">目的</span><span class="sxs-lookup"><span data-stu-id="24eb2-109">Objectives</span></span>

* <span data-ttu-id="24eb2-110">HoloLens 2 を使用した Azure 空間アンカーを使用した開発の基礎について説明します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-110">Learn the fundamentals of developing with Azure Spatial Anchors with HoloLens 2</span></span>

* <span data-ttu-id="24eb2-111">空間アンカーを作成、アップロード、ダウンロードする</span><span class="sxs-lookup"><span data-stu-id="24eb2-111">Create, upload, and download spatial anchors</span></span>

## <a name="instructions"></a><span data-ttu-id="24eb2-112">手順</span><span class="sxs-lookup"><span data-stu-id="24eb2-112">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="24eb2-113">アセットのダウンロードとインポート</span><span class="sxs-lookup"><span data-stu-id="24eb2-113">Downloading and importing assets</span></span>
<span data-ttu-id="24eb2-114">開始する前に、次のアセットをダウンロードしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-114">Before beginning, download and import the following assets:</span></span>

[<span data-ttu-id="24eb2-115">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="24eb2-115">Azure Spatial Anchors</span></span>](https://github.com/azure/azure-spatial-anchors-samples/releases)

[<span data-ttu-id="24eb2-116">MR Base モジュールアセットパック</span><span class="sxs-lookup"><span data-stu-id="24eb2-116">MR Base module Asset Pack</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2)

[<span data-ttu-id="24eb2-117">ASA モジュールアセットパック</span><span class="sxs-lookup"><span data-stu-id="24eb2-117">ASA module Asset Pack</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1)

[<span data-ttu-id="24eb2-118">Mixed Reality ツールキット</span><span class="sxs-lookup"><span data-stu-id="24eb2-118">Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/)

> <span data-ttu-id="24eb2-119">注:Azure 空間アンカーをインポートする具体的な手順については、手順5を参照してください。 MR Base モジュール Asset Pack に関する具体的な手順については、手順6を参照してください。また、Mixed Reality Toolkit (MRKT) の具体的な手順については、手順 3 ~ 4 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24eb2-119">Note: See Step 5 for specific instructions on how to import Azure Spatial Anchors, Step 6 for specific instructions on the MR Base module Asset Pack, and steps 3 through 4 for specific instructions on the Mixed Reality Toolkit (MRKT).</span></span>

1. <span data-ttu-id="24eb2-120">プロジェクトに新しいシーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-120">Create a new scene in your project.</span></span> <span data-ttu-id="24eb2-121">シーンフォルダーを右クリックし、[作成]、[シーン] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-121">Right click your Scene folder, click Create, then Scene.</span></span> <span data-ttu-id="24eb2-122">新しいシーンに ASALearningmodule という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-122">Name the new scene ASALearningmodule.</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="24eb2-124">[ASALearningmodule] をダブルクリックすると、定義済みの項目の一部が新しいシーンと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-124">Double click ASALearningmodule to see some pre-defined items appear along with the new scene.</span></span> 
3. <span data-ttu-id="24eb2-125">混合現実開発のシーンを構成します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="24eb2-127">注:[Mixed Reality Toolkit] のファイルを選択する必要があるというポップアップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-127">Note: You will see a pop-up that says, You must choose a file for the Mixed Reality Toolkit.</span></span> <span data-ttu-id="24eb2-128">[Ok] をクリックすると、手順 4. が表示されます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-128">Clicking Ok brings you to Step 4.</span></span>

4. <span data-ttu-id="24eb2-129">MRTK のファイルを選択する場合は、[DefaultMixedRealityToolkitConfigurationProfile] を選択します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-129">When choosing a file for the MRTK, select, DefaultMixedRealityToolkitConfigurationProfile.</span></span>

> <span data-ttu-id="24eb2-130">注:独自の構成プロファイルがある場合は、それを自由に使用できます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-130">Note: If you have your own configuration profile, feel free to use that instead.</span></span>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="24eb2-132">これで、シーンが混合現実用に構成されました。</span><span class="sxs-lookup"><span data-stu-id="24eb2-132">Now the scene is configured for mixed reality.</span></span> <span data-ttu-id="24eb2-133">シーンを保存していることを確認します (これを行うには、control/command + S を使用するか、[ファイル] をクリックして、[保存] をクリックします)。</span><span class="sxs-lookup"><span data-stu-id="24eb2-133">Make sure you save your scene (do this with either control/command+S or click on file, then click on Save).</span></span> 

5. <span data-ttu-id="24eb2-134">[Azure 空間アンカー](https://github.com/azure/azure-spatial-anchors-samples/releases)をインポートします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-134">Import the [Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases).</span></span> <span data-ttu-id="24eb2-135">空間アンカーを使用するには、この資産をインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="24eb2-135">In order to use spatial anchors, you must import this asset.</span></span> <span data-ttu-id="24eb2-136">上のリンクをクリックし、AzureSpatialAnchors. unitypackage を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-136">Click on the link above and right click on AzureSpatialAnchors.unitypackage.</span></span> <span data-ttu-id="24eb2-137">[ターゲットに名前を付けて保存] をクリックし、コンピューターに保存します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-137">Click on Save Target As and save it to your computer.</span></span> 

![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

<span data-ttu-id="24eb2-139">保存した後、Unity に戻り、[アセット] をクリックして、[パッケージのインポート] に移動します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-139">After it's saved, go back into Unity, click Assets, go down to Import Package.</span></span> <span data-ttu-id="24eb2-140">[カスタムパッケージ] をクリックします。コンピューターのファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-140">Then click Custom Package... Your computer files will open.</span></span> <span data-ttu-id="24eb2-141">その場合は、Azure 空間アンカーパッケージを保存した場所を見つけて、それを選択します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-141">When they do, find where you saved the Azure Spatial Anchors package, and select it.</span></span> <span data-ttu-id="24eb2-142">[開く] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-142">Then click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

<span data-ttu-id="24eb2-144">ポップアップが表示され、ツールと設定の一覧が表示され、インポートする内容が尋ねられます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-144">A pop-up appears, providingg a list of tools and settings, and asking you what to import.</span></span> <span data-ttu-id="24eb2-145">使用可能な***すべて***のオプションを選択し、[インポート] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-145">Select ***all*** of the options available, then click Import.</span></span>

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> <span data-ttu-id="24eb2-147">注:しばらくお待ちください。インポートには数分かかります。</span><span class="sxs-lookup"><span data-stu-id="24eb2-147">Note: Be patient, it will take a few minutes to import.</span></span> 

6. <span data-ttu-id="24eb2-148">[MR Base module Asset Pack]https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) をインポートします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-148">Import [MR Base module Asset Pack]https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) next.</span></span> <span data-ttu-id="24eb2-149">手順 5. と同じように、上のリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-149">Much like Step 5, click the link above.</span></span> <span data-ttu-id="24eb2-150">次に、[BasemoduleAssetsV1 1. unitypackag] を右クリックし、[ターゲットを名前を付けて保存] をクリックして、コンピューターに保存します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-150">Then right click BasemoduleAssetsV1 1.unitypackag, and click Save Target As, and save it to your computer.</span></span>

![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

> <span data-ttu-id="24eb2-152">ヒント:これらのすべての資産を同じフォルダーに保存して、見つけやすく、アクセスしやすいようにします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-152">Tip: Save all these assets in the same folder so that they are easier to find and have access to.</span></span> <span data-ttu-id="24eb2-153">すべての問題を把握し、整理することができます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-153">It keeps everything nice and organized.</span></span>

<span data-ttu-id="24eb2-154">手順5と同じように、Unity に戻り、[アセット] をクリックして、[インポートパッケージ] にカーソルを合わせます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-154">Just like Step 5, go back in to Unity, click Assets, and hover over Import Package.</span></span> <span data-ttu-id="24eb2-155">[カスタムパッケージ] をクリックします。コンピューターのファイルが再び表示されます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-155">Click Custom Package... Your computer files will appear again.</span></span> <span data-ttu-id="24eb2-156">Base module Asset Pack を格納した場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-156">Go to where you stored the Base module Asset Pack.</span></span> <span data-ttu-id="24eb2-157">を選択します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-157">and select it.</span></span> <span data-ttu-id="24eb2-158">[開く] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-158">Click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> <span data-ttu-id="24eb2-160">注:このモジュールの後に必要な資産が増える場合があります。</span><span class="sxs-lookup"><span data-stu-id="24eb2-160">Note: There might be more assets needed later in this module.</span></span> <span data-ttu-id="24eb2-161">ここで説明したアセットをインポートするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="24eb2-161">Follow these steps to import any assets mentioned from this point on.</span></span> 

7. <span data-ttu-id="24eb2-162">以前のパッケージをインポートする場合と同じ方法を使用して[ASA モジュールパック](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1)をインポートします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-162">Import the [ASA module pack](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1) using the same approach as importing the previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="24eb2-163">シーンの構成</span><span class="sxs-lookup"><span data-stu-id="24eb2-163">Configuring your scene</span></span>

<span data-ttu-id="24eb2-164">このセクションでは、prefabs とスクリプトをシーンに追加して、アプリケーションでローカルアンカーと Azure 空間アンカーの両方が動作する方法の基礎を示す一連のボタンを作成します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-164">In this section, we will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

8. <span data-ttu-id="24eb2-165">[プロジェクト] タブの [アセット] フォルダーの下で、[ASAmoduleAssets] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-165">In the Project tab, underneath the Assets folder, click on ASAmoduleAssets.</span></span> <span data-ttu-id="24eb2-166">選択すると、2つの prefabs が表示されます。ButtonParent および ParentAnchor。</span><span class="sxs-lookup"><span data-stu-id="24eb2-166">Once selected, you will see two prefabs: ButtonParent and ParentAnchor.</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. <span data-ttu-id="24eb2-168">両方の prefabs をシーンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-168">Drag both prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

10. <span data-ttu-id="24eb2-170">親アンカーをダブルクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-170">Double click on the parent anchor to select it.</span></span> <span data-ttu-id="24eb2-171">場合によっては、シーン全体を表示するようにビューを調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24eb2-171">You might need to adjust your view to see the entire scene.</span></span> <span data-ttu-id="24eb2-172">必要に応じてシーンを調整します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-172">Adjust your scene as needed.</span></span>

<span data-ttu-id="24eb2-173">ParentAnchor prefab について理解を深めます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-173">Familiarize yourself with the ParentAnchor prefab.</span></span> <span data-ttu-id="24eb2-174">現在、ParentAnchor という名前のゲームオブジェクトは、デモを目的として色分けされたキューブです。</span><span class="sxs-lookup"><span data-stu-id="24eb2-174">Currently, the game object named, ParentAnchor, is a colored cube for demonstration purposes.</span></span> <span data-ttu-id="24eb2-175">最終的には、キューブを非表示にして、コンテンツを ParentAnchor の子として配置します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-175">Eventually, we',ll hide the cube and place our content as a child of the ParentAnchor.</span></span> <span data-ttu-id="24eb2-176">この事前 fab には、ASA SDK に含まれる AzureSpatialAnchorsDemoWrapper.cs スクリプトと ASAmoduleScript.cs スクリプトが含まれています。このスクリプトは、このモジュールの一部として ParentAnchor オブジェクトに含まれています。</span><span class="sxs-lookup"><span data-stu-id="24eb2-176">This prefab includes the AzureSpatialAnchorsDemoWrapper.cs script (included with the ASA SDK), and the ASAmoduleScript.cs script, included as part of this module to the ParentAnchor object.</span></span> 

11. <span data-ttu-id="24eb2-177">ボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-177">Configure buttons.</span></span> <span data-ttu-id="24eb2-178">ButtonParent prefab の下に、ラベル付きのボタンがいくつかあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-178">Under the ButtonParent prefab, notice several labeled buttons.</span></span> <span data-ttu-id="24eb2-179">これらのボタンは、MRTK の PressableButton prefabs から作成されます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-179">These buttons are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="24eb2-180">Pressable ボタンを作成する方法の詳細については、「[基本モジュール](mrlearning-base-ch2.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24eb2-180">Learn more about how to create Pressable Buttons from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="24eb2-181">各ボタンに対して、ユーザーが次の一覧に従ってボタンをクリックまたは選択したときにトリガーされるイベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-181">For each button, add an event that will be triggered when the user presses or selects the button according to the list below.</span></span> 

- <span data-ttu-id="24eb2-182">StartAzureSession という名前のボタンについては、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-182">For the Button named, StartAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="24eb2-183">ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StartAzureSession () メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-183">Drag the ParentAnchor object into the empty field, and assign the StartAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="24eb2-187">ボタン名として [StopAzureSession] をクリックし、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-187">For the Button name, StopAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="24eb2-188">ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StopAzureSession () メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-188">Drag the ParentAnchor object into the empty field, and assign the StopAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="24eb2-189">[CreateAnchor] という名前のボタンに対して、ボタン押されたイベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-189">For the Button named, CreateAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="24eb2-190">ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから CreateAzureAnchor () メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-190">Drag the ParentAnchor object into the empty field, and assign the CreateAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="24eb2-191">という名前のボタンについては、アンカーの検索を開始し、ボタン Presse "イベントトリガーと On Click イベントトリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-191">For the Button named, Start Looking For Anchor, create a new event under the Button Presse" event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="24eb2-192">ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから FindAzureAnchor () メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-192">Drag the ParentAnchor object into the empty field, and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="24eb2-193">[DeleteAzureAnchor] という名前のボタンに対して、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-193">For the Button named, DeleteAzureAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="24eb2-194">ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから DeleteAzureAnchor () メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-194">Drag the ParentAnchor object into the empty field, and assign the DeleteAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="24eb2-195">[ローカルアンカーの削除] という名前のボタンに対して、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-195">For the Button named, Delete Local Anchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="24eb2-196">ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから RemoveLocalAnchor () メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-196">Drag the ParentAnchor object into the empty field, and assign the RemoveLocalAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="24eb2-197">基本アプリケーションのビルドとデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="24eb2-197">Build and demonstrate Base Application</span></span>

<span data-ttu-id="24eb2-198">ここでは、Azure 空間アンカーの基本を示すためにシーンが構成されたので、Azure 空間アンカーの基本的な動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-198">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="24eb2-199">前のセクションで [ビルド設定] ウィンドウを閉じた場合は、[ファイル] > [ビルド設定] の順に移動して [ビルド設定] ウィンドウを再度開きます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-199">If you closed the Build Settings window from the previous sections, open the build settings window again by going to File>Build Settings.</span></span>
<span data-ttu-id="24eb2-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="24eb2-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span></span>

2. <span data-ttu-id="24eb2-201">[開いているシーンを追加] ボタンをクリックして、目的のシーンがビルドリストのシーンにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-201">Ensure the scene you want to try is in the Scenes in Build list by clicking on the Add Open Scenes button.</span></span>

3. <span data-ttu-id="24eb2-202">[ビルド] ボタンを押して、ビルド プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-202">Press the Build button to begin the build process.</span></span>
<span data-ttu-id="24eb2-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="24eb2-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span></span>

4. <span data-ttu-id="24eb2-204">アプリケーション用の新しいフォルダーを作成して、名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-204">Create and name a new folder for your application.</span></span> <span data-ttu-id="24eb2-205">次の図では、アプリケーションを格納するために、App という名前のフォルダーが作成されています。</span><span class="sxs-lookup"><span data-stu-id="24eb2-205">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="24eb2-206">[フォルダーの選択] をクリックして、新しく作成したフォルダーへのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-206">Click Select Folder to begin building to the newly created folder.</span></span> <span data-ttu-id="24eb2-207">ビルドが完了したら、Unity の [ビルドの設定] ウィンドウを閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-207">After the build has completed, you may close the Build Setting" window in Unity.</span></span> 
<span data-ttu-id="24eb2-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="24eb2-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span></span>

  > <span data-ttu-id="24eb2-209">注: ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。</span><span class="sxs-lookup"><span data-stu-id="24eb2-209">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="24eb2-210">エラー:CS0246 = tyoe または名前空間の名前 "XX" が見つかりませんでした。 using ディレクティブまたはアセンブリ参照が指定されていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="24eb2-210">If you see an error such as "Error: CS0246 = The tyoe or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="24eb2-211">[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)のインストールが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="24eb2-211">You might need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span> 
  >

5. <span data-ttu-id="24eb2-212">ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-212">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="24eb2-213">"MixedRealityBase ソリューションまたは対応する名前をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-213">Double click on the“MixedRealityBase.sln solution or the corresponding name.</span></span> <span data-ttu-id="24eb2-214">プロジェクトに代替名を使用して、Visual Studio でソリューションファイルを開く場合。</span><span class="sxs-lookup"><span data-stu-id="24eb2-214">if you used an alternative name for your project to open the solution file in Visual Studio.</span></span>

  > <span data-ttu-id="24eb2-215">注:新しく作成したフォルダー (つまり、前の手順の名前付け規則に従っている場合は、アプリフォルダー) を必ず開いてください。これは、ビルドフォルダー内の .sln ファイルと混同しないように、同じ名前の .sln ファイルがそのフォルダー外に存在するためです。</span><span class="sxs-lookup"><span data-stu-id="24eb2-215">Note: Be sure to open the newly created folder (i.e., the App folder, if following the naming conventions from the previous steps because there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

> <span data-ttu-id="24eb2-217">注:Visual Studio で新しいコンポーネントのインストールを求められた場合は、 [[ツールのインストール] ページ](install-the-tools.md)で、前提条件となるすべてのコンポーネントが特定のコンポーネントとしてインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="24eb2-217">Note: If Visual Studio asks to install new components, please take a moment to ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span> 

6. <span data-ttu-id="24eb2-218">USB ケーブルを使って HoloLens 2 を PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-218">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="24eb2-219">これらのレッスンの手順では、HoloLens 2 デバイスでテストをデプロイすることを想定していますが、 [hololens 2 エミュレーター](using-the-hololens-emulator.md)にデプロイするか、[サイドローディング用のアプリパッケージの](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)作成を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-219">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="24eb2-220">デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="24eb2-220">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="24eb2-221">HoloLens 2 に初めてデプロイする場合は、Visual Studio により、PIN を使用して HoloLens 2 をペアリングするよう求められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="24eb2-221">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="24eb2-222">開発者モードを有効にする必要がある場合、または Visual Studio と組み合わせて使用する場合は、[次の手順](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)に従います。</span><span class="sxs-lookup"><span data-stu-id="24eb2-222">Follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="24eb2-223">リリース構成と RM アーキテクチャを選択して、HoloLens 2 にビルドするように Visual Studio を構成します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-223">Configure Visual Studio for building to your HoloLens 2 by selecting the Release configuration as well as the RM architecture.</span></span>
<span data-ttu-id="24eb2-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span><span class="sxs-lookup"><span data-stu-id="24eb2-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span></span>
   
9. <span data-ttu-id="24eb2-225">最後の手順は、デバッグ > デバッグなしで開始 を選択してデバイスにビルドすることです。</span><span class="sxs-lookup"><span data-stu-id="24eb2-225">The final Step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="24eb2-226">[デバッグなしで開始] を選択すると、Visual Studio に表示されるビルド ithout デバッグ情報が正常に完了した時点で、アプリケーションがすぐにデバイスで開始されます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-226">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build ithout Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="24eb2-227">これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-227">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="24eb2-228">また、[ビルド > デプロイ] を選択して、アプリケーションを自動的に起動せずにデバイスにデプロイすることもできます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-228">You might also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>
<span data-ttu-id="24eb2-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span><span class="sxs-lookup"><span data-stu-id="24eb2-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span></span>
   
10. <span data-ttu-id="24eb2-230">画面の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="24eb2-230">Follow the instructions.</span></span> <span data-ttu-id="24eb2-231">デバイスでアプリケーションが実行されている場合は、画面の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="24eb2-231">When the application is running on your device, follow the on-screen instructions.</span></span> <span data-ttu-id="24eb2-232">次の手順に対応するシーンボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-232">Press the Scene buttons corresponding to the Steps below.</span></span>

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="24eb2-234">空間アンカーセッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-234">Start the spatial anchors session.</span></span>
    
    2. <span data-ttu-id="24eb2-235">キューブを別の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-235">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="24eb2-236">キューブの場所に Azure 空間アンカーを保存します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-236">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="24eb2-237">Azure 空間アンカーセッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-237">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="24eb2-238">キューブのローカルアンカーを削除して、ユーザーがキューブを移動できるようにします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-238">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    
    6. <span data-ttu-id="24eb2-239">キューブを別の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-239">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="24eb2-240">Azure 空間アンカーセッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-240">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="24eb2-241">Azure 空間アンカーを検索します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-241">Find Azure Spatial Anchors.</span></span> 
    <span data-ttu-id="24eb2-242">アンカーを作成したときに、元の場所に戻ります。</span><span class="sxs-lookup"><span data-stu-id="24eb2-242">You should go back to the original place you put it when you created the anchor.</span></span>
    
    9. <span data-ttu-id="24eb2-243">Azure 空間アンカーを削除します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-243">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="24eb2-244">Azure セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-244">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="24eb2-245">エクスペリエンスを固定する</span><span class="sxs-lookup"><span data-stu-id="24eb2-245">Anchoring an experience</span></span>

<span data-ttu-id="24eb2-246">前のセクションでは、Azure 空間アンカーの基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="24eb2-246">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="24eb2-247">キューブを使用して、アタッチされたアンカーで親ゲームオブジェクトを表現し、視覚化しました。</span><span class="sxs-lookup"><span data-stu-id="24eb2-247">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="24eb2-248">このセクションでは、ParentAnchor オブジェクトの子として配置することで、エクスペリエンス全体を固定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-248">In this section, you learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="24eb2-249">この例では、「[基本モジュールレッスン 6](mrlearning-base-ch6.md)」で作成した旧暦モジュールアセンブリデモンストレーションアプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-249">For this example, we use the lunar module Assembly demonstration application that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="24eb2-250">次の図に示すように、旧暦モジュールアセンブリの完全な prefab を検索し、AnchorParent のユーザーオブジェクトの子として階層にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-250">Search for the Lunar Module Assembly Complete prefab, and drag it into your heirarchy as a child of the AnchorParent gameobject as shown in the image below.</span></span>

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="24eb2-252">次の図に示すように、モジュールのアセンブリエクスペリエンスを配置して、キューブが引き続き公開されるようにします。</span><span class="sxs-lookup"><span data-stu-id="24eb2-252">Position the module assembly experience so that the cube is still exposed as shown in the image below.</span></span> <span data-ttu-id="24eb2-253">アプリケーションでは、ユーザーはキューブを移動することで、エクスペリエンス全体を再配置できます。</span><span class="sxs-lookup"><span data-stu-id="24eb2-253">In the application, users may reposition the entire experience by moving the cube.</span></span> 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> <span data-ttu-id="24eb2-255">注:エクスペリエンスを再配置するためのさまざまなユーザーエクスペリエンスフローがあります。たとえば、ボタンを使用して、操作を囲む境界ボックスの切り替え、オブジェクトの再配置 (この手順で使用するキューブなど)、位置と回転の使用などがあります。、その他。</span><span class="sxs-lookup"><span data-stu-id="24eb2-255">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="24eb2-256">結論</span><span class="sxs-lookup"><span data-stu-id="24eb2-256">Congratulations</span></span>
<span data-ttu-id="24eb2-257">このチュートリアルでは、Azure 空間アンカーの基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="24eb2-257">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="24eb2-258">ここでは、Azure セッションを開始および停止するために必要なさまざまな手順を説明し、1つのデバイスで azure のアンカーを作成、アップロード、ダウンロードするためのボタンをいくつか紹介しました。</span><span class="sxs-lookup"><span data-stu-id="24eb2-258">This esson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session, and create, upload, and download azure anchors on a single device.</span></span> <span data-ttu-id="24eb2-259">次のレッスンでは、アプリケーションを再起動した後でも、Azure anchor Id を HoloLens 2 に保存して取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-259">In the next lesson, we'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="24eb2-260">このシリーズでは、空間アラインメントを実現するために複数のデバイス間でアンカー Id を転送する方法や、マルチユーザー共有セッションについて学習する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="24eb2-260">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment, and learn about multi-user shared sessions, forthcoming as part of Sharing tutorial.</span></span>

[<span data-ttu-id="24eb2-261">次のレッスン:ASA レッスン2</span><span class="sxs-lookup"><span data-stu-id="24eb2-261">Next Lesson: ASA Lesson 2</span></span>](mrlearning-asa-ch2.md)

