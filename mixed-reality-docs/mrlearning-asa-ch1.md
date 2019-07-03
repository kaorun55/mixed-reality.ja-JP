---
title: MR Learning ASA モジュール HoloLens 2 での Azure 空間アンカー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: fcca828fa228894e0e60986c6c7fd0053b210357
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523234"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="03fd5-104">1. 空間のアンカーを Azure の概要</span><span class="sxs-lookup"><span data-stu-id="03fd5-104">1. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="03fd5-105">HoloLens 2 のチュートリアルの 2 番目のモジュールへようこそ。</span><span class="sxs-lookup"><span data-stu-id="03fd5-105">Welcome to the second module of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="03fd5-106">始める前に、必ずすべての[の前提条件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)が完了します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-106">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="03fd5-107">まず、完了していない場合[ベース モジュール](mrlearning-base.md)モジュールを最初に完了することを勧めします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-107">If you have not completed the first, [Base module](mrlearning-base.md) yet, it's recommended that you complete that module first.</span></span> <span data-ttu-id="03fd5-108">新しい Unity プロジェクトから開始する場合は 新しいプロジェクトの作成手順に従ってください、[ベース モジュール](mrlearning-base.md)します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-108">If you are starting from a new Unity project, follow the new project creation steps in the [Base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="03fd5-109">目標</span><span class="sxs-lookup"><span data-stu-id="03fd5-109">Objectives</span></span>

* <span data-ttu-id="03fd5-110">HoloLens 2 Azure 空間アンカーを使用した開発の基礎を学習します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-110">Learn the fundamentals of developing with Azure Spatial Anchors with HoloLens 2</span></span>

* <span data-ttu-id="03fd5-111">作成、アップロード、および空間アンカーのダウンロード</span><span class="sxs-lookup"><span data-stu-id="03fd5-111">Create, upload, and download spatial anchors</span></span>

  

## <a name="instructions"></a><span data-ttu-id="03fd5-112">手順</span><span class="sxs-lookup"><span data-stu-id="03fd5-112">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="03fd5-113">ダウンロードとアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="03fd5-113">Downloading and importing assets</span></span>
<span data-ttu-id="03fd5-114">始める前に、ダウンロードし、次のアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-114">Before beginning, download and import the following assets:</span></span>

[<span data-ttu-id="03fd5-115">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="03fd5-115">Azure Spatial Anchors</span></span>](https://github.com/azure/azure-spatial-anchors-samples/releases)

[<span data-ttu-id="03fd5-116">資産パックの MR ベース モジュール</span><span class="sxs-lookup"><span data-stu-id="03fd5-116">MR Base module Asset Pack</span></span>](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[<span data-ttu-id="03fd5-117">ASA モジュール資産パック</span><span class="sxs-lookup"><span data-stu-id="03fd5-117">ASA module Asset Pack</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[<span data-ttu-id="03fd5-118">Mixed Reality ツールキット</span><span class="sxs-lookup"><span data-stu-id="03fd5-118">Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> <span data-ttu-id="03fd5-119">注:Azure 空間アンカー、MR ベース モジュール資産パックの詳細については、手順 6、および Mixed Reality ツールキット (MRKT) で、手順 3 ~ 4 具体的な手順についてをインポートする方法の具体的な手順については、手順 5 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03fd5-119">Note: See Step 5 for specific instructions on how to import Azure Spatial Anchors, Step 6 for specific instructions on the MR Base module Asset Pack, and steps 3 through 4 for specific instructions on the Mixed Reality Toolkit (MRKT).</span></span>

1. <span data-ttu-id="03fd5-120">プロジェクトに新しいシーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-120">Create a new scene in your project.</span></span> <span data-ttu-id="03fd5-121">シーンのフォルダーを右クリックして、シーンの作成をクリックします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-121">Right click your Scene folder, click Create, then Scene.</span></span> <span data-ttu-id="03fd5-122">新しいシーン ASALearningmodule の名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-122">Name the new scene ASALearningmodule.</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="03fd5-124">新しいシーンと共に表示されるいくつか事前定義された項目を表示する ASALearningmodule をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-124">Double click ASALearningmodule to see some pre-defined items appear along with the new scene.</span></span> 
3. <span data-ttu-id="03fd5-125">複合現実の開発のシーンを構成します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="03fd5-127">注:Mixed Reality Toolkit のファイルを選択する必要があります、というポップアップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-127">Note: You will see a pop-up that says, You must choose a file for the Mixed Reality Toolkit.</span></span> <span data-ttu-id="03fd5-128">[Ok] をクリックすると、手順 4 に表示されます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-128">Clicking Ok brings you to Step 4.</span></span>

4. <span data-ttu-id="03fd5-129">ときに、MRTK のファイルを選択すると、選択、DefaultMixedRealityToolkitConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="03fd5-129">When choosing a file for the MRTK, select, DefaultMixedRealityToolkitConfigurationProfile.</span></span>

   > <span data-ttu-id="03fd5-130">注:独自の構成プロファイルを用意する場合は、代わりに使用するかまいません。</span><span class="sxs-lookup"><span data-stu-id="03fd5-130">Note: If you have your own configuration profile, feel free to use that instead.</span></span>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="03fd5-132">シーンを複合現実用に構成されました。</span><span class="sxs-lookup"><span data-stu-id="03fd5-132">Now the scene is configured for mixed reality.</span></span> <span data-ttu-id="03fd5-133">シーンを保存するかどうかを確認 (どちらのコントロールでそれを行うコマンド + S またはファイルをクリックし、クリックして/保存時に)。</span><span class="sxs-lookup"><span data-stu-id="03fd5-133">Make sure you save your scene (do this with either control/command+S or click on file, then click on Save).</span></span> 

5. <span data-ttu-id="03fd5-134">インポート、 [Azure 空間アンカー](https://github.com/azure/azure-spatial-anchors-samples/releases)します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-134">Import the [Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases).</span></span> <span data-ttu-id="03fd5-135">空間アンカーを使用するには、このアセットをインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="03fd5-135">In order to use spatial anchors, you must import this asset.</span></span> <span data-ttu-id="03fd5-136">上記のリンクをクリックし、AzureSpatialAnchors.unitypackage を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-136">Click on the link above and right click on AzureSpatialAnchors.unitypackage.</span></span> <span data-ttu-id="03fd5-137">[ターゲットの名前を付けて保存] をクリックし、コンピューターに保存します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-137">Click on Save Target As and save it to your computer.</span></span> 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   <span data-ttu-id="03fd5-139">保存すると後、は、Unity に戻り、資産をクリックします。、パッケージのインポートに移動します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-139">After it's saved, go back into Unity, click Assets, go down to Import Package.</span></span> <span data-ttu-id="03fd5-140">カスタム パッケージをクリックしてください.コンピューターのファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-140">Then click Custom Package... Your computer files will open.</span></span> <span data-ttu-id="03fd5-141">場合の操作を行いますが、Azure 空間アンカー パッケージを保存した検索しを選択します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-141">When they do, find where you saved the Azure Spatial Anchors package, and select it.</span></span> <span data-ttu-id="03fd5-142">[開く] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-142">Then click Open.</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   <span data-ttu-id="03fd5-144">Providingg 一連のツールおよび設定、およびインポートするように求めるポップアップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-144">A pop-up appears, providingg a list of tools and settings, and asking you what to import.</span></span> <span data-ttu-id="03fd5-145">選択***すべて***使用可能なオプションのインポート をクリックします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-145">Select ***all*** of the options available, then click Import.</span></span>

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > <span data-ttu-id="03fd5-147">注:患者をすると、インポートするまで数分がかかります。</span><span class="sxs-lookup"><span data-stu-id="03fd5-147">Note: Be patient, it will take a few minutes to import.</span></span> 

   6. <span data-ttu-id="03fd5-148">インポート[MR ベース モジュール資産パック](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)[次へ]。</span><span class="sxs-lookup"><span data-stu-id="03fd5-148">Import [MR Base module Asset Pack](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) next.</span></span> <span data-ttu-id="03fd5-149">はるか手順 5 のような場合は、上記のリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-149">Much like Step 5, click the link above.</span></span> <span data-ttu-id="03fd5-150">BasemoduleAssetsV1 1.unitypackag を右クリックし、ターゲットとして保存 をクリックし、コンピューターに保存します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-150">Then right click BasemoduleAssetsV1 1.unitypackag, and click Save Target As, and save it to your computer.</span></span>

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > <span data-ttu-id="03fd5-152">ヒント:簡単に見つけにアクセスできるように、同じフォルダーにこれらすべての資産を保存します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-152">Tip: Save all these assets in the same folder so that they are easier to find and have access to.</span></span> <span data-ttu-id="03fd5-153">便利で、構成されたすべてのものを保持します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-153">It keeps everything nice and organized.</span></span>

   <span data-ttu-id="03fd5-154">手順 5 と同じようを Unity に、資産、 をクリックしてパッケージのインポートを合わせます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-154">Just like Step 5, go back in to Unity, click Assets, and hover over Import Package.</span></span> <span data-ttu-id="03fd5-155">カスタム パッケージをクリックします。コンピューターのファイルが再び表示されます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-155">Click Custom Package... Your computer files will appear again.</span></span> <span data-ttu-id="03fd5-156">資産パックのベース モジュールを格納した場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-156">Go to where you stored the Base module Asset Pack.</span></span> <span data-ttu-id="03fd5-157">選択します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-157">and select it.</span></span> <span data-ttu-id="03fd5-158">[開く] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-158">Click Open.</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > <span data-ttu-id="03fd5-160">注:このモジュールで後で必要な複数のアセットである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="03fd5-160">Note: There might be more assets needed later in this module.</span></span> <span data-ttu-id="03fd5-161">この時点で説明されているすべてのアセットをインポートする次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="03fd5-161">Follow these steps to import any assets mentioned from this point on.</span></span> 
                                                                                                                                                                                                                    
7. <span data-ttu-id="03fd5-162">前のパッケージのインポートと同じアプローチを使用して ASA モジュールの ack をインポートします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-162">Import the ASA module ack using the same approach as importing the previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="03fd5-163">シーンの構成</span><span class="sxs-lookup"><span data-stu-id="03fd5-163">Configuring your scene</span></span>

<span data-ttu-id="03fd5-164">このセクションで、シーンの一連のアプリケーションでのローカルのアンカーと空間アンカーを Azure の両方の動作方法の基礎を説明するボタンを作成するにプレハブとスクリプトは追加します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-164">In this section, we will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

7. <span data-ttu-id="03fd5-165">[プロジェクト] タブの Assets フォルダーの下にある ASAmoduleAssets をクリックします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-165">In the Project tab, underneath the Assets folder, click on ASAmoduleAssets.</span></span> <span data-ttu-id="03fd5-166">選択すると、2 つのプレハブが表示されます。ButtonParent ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="03fd5-166">Once selected, you will see two prefabs: ButtonParent and ParentAnchor.</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. <span data-ttu-id="03fd5-168">両方のプレハブをシーンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-168">Drag both prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. <span data-ttu-id="03fd5-170">親のアンカーをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-170">Double click on the parent anchor to select it.</span></span> <span data-ttu-id="03fd5-171">シーン全体を表示する表示を調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03fd5-171">You might need to adjust your view to see the entire scene.</span></span> <span data-ttu-id="03fd5-172">必要に応じて、シーンを調整します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-172">Adjust your scene as needed.</span></span>

    <span data-ttu-id="03fd5-173">ParentAnchor プレハブを理解します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-173">Familiarize yourself with the ParentAnchor prefab.</span></span> <span data-ttu-id="03fd5-174">現在、ParentAnchor、という名前のゲーム オブジェクトは、デモンストレーション用の立方体です。</span><span class="sxs-lookup"><span data-stu-id="03fd5-174">Currently, the game object named, ParentAnchor, is a colored cube for demonstration purposes.</span></span> <span data-ttu-id="03fd5-175">ここでは最終的には、'、ll、キューブを非表示にして、ParentAnchor の子として、コンテンツを配置します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-175">Eventually, we',ll hide the cube and place our content as a child of the ParentAnchor.</span></span> <span data-ttu-id="03fd5-176">このプレハブには、(ASA SDK に含まれる) AzureSpatialAnchorsDemoWrapper.cs スクリプト、および ParentAnchor オブジェクトには、このモジュールの一部として含まれる、ASAmoduleScript.cs スクリプトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-176">This prefab includes the AzureSpatialAnchorsDemoWrapper.cs script (included with the ASA SDK), and the ASAmoduleScript.cs script, included as part of this module to the ParentAnchor object.</span></span> 

10. <span data-ttu-id="03fd5-177">ボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-177">Configure buttons.</span></span> <span data-ttu-id="03fd5-178">ParentAnchor プレハブを下には、いくつかのラベルの付いたボタンに注目してください。</span><span class="sxs-lookup"><span data-stu-id="03fd5-178">Under the ParentAnchor prefab, notice several labeled buttons.</span></span> <span data-ttu-id="03fd5-179">これらのボタンは、MRTK の PressableButton のプレハブから作成されます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-179">These buttons are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="03fd5-180">Pressable ボタンを作成する方法について説明します、[ベース モジュール](mrlearning-base-ch2.md)します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-180">Learn more about how to create Pressable Buttons from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="03fd5-181">各ボタンを押すか、以下の一覧に従ってボタンを選択したときにトリガーされるイベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-181">For each button, add an event that will be triggered when the user presses or selects the button according to the list below.</span></span> 

- <span data-ttu-id="03fd5-182">名前付き、StartAzureSession、ボタンのクリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-182">For the Button named, StartAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="03fd5-183">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StartAzureSession() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-183">Drag the ParentAnchor object into the empty field, and assign the StartAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="03fd5-187">ボタン名、StopAzureSession、クリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-187">For the Button name, StopAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="03fd5-188">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StopAzureSession() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-188">Drag the ParentAnchor object into the empty field, and assign the StopAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="03fd5-189">名前付き、CreateAnchor、ボタンのクリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-189">For the Button named, CreateAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="03fd5-190">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから CreateAzureAnchor() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-190">Drag the ParentAnchor object into the empty field, and assign the CreateAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="03fd5-191">イベント トリガーの起動お探しのアンカーをという名前のボタンのボタン Presse の下に新しいイベントの作成"だけでなく、イベント トリガーのをクリックします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-191">For the Button named, Start Looking For Anchor, create a new event under the Button Presse" event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="03fd5-192">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから FindAzureAnchor() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-192">Drag the ParentAnchor object into the empty field, and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="03fd5-193">名前付き、DeleteAzureAnchor、ボタンのクリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-193">For the Button named, DeleteAzureAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="03fd5-194">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから DeleteAzureAnchor() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-194">Drag the ParentAnchor object into the empty field, and assign the DeleteAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="03fd5-195">名前付き、ローカルのアンカーの削除 ボタンのクリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-195">For the Button named, Delete Local Anchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="03fd5-196">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから RemoveLocalAnchor() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-196">Drag the ParentAnchor object into the empty field, and assign the RemoveLocalAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="03fd5-197">ビルドし、ベースのアプリケーションのデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="03fd5-197">Build and demonstrate Base Application</span></span>

<span data-ttu-id="03fd5-198">これで、シーンは Azure 空間アンカーの基本について説明する構成は作成し、Azure 空間アンカーの基本的な動作を示します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-198">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="03fd5-199">前のセクションで [ビルド設定] ウィンドウを閉じた場合は、[ファイル] > [ビルド設定] の順に移動して [ビルド設定] ウィンドウを再度開きます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-199">If you closed the Build Settings window from the previous sections, open the build settings window again by going to File>Build Settings.</span></span>
    <span data-ttu-id="03fd5-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="03fd5-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span></span>

2. <span data-ttu-id="03fd5-201">試したいシーンが開いているシーンの追加 ボタンをクリックしてビルド リスト内のシーンでは確認してください。</span><span class="sxs-lookup"><span data-stu-id="03fd5-201">Ensure the scene you want to try is in the Scenes in Build list by clicking on the Add Open Scenes button.</span></span>

3. <span data-ttu-id="03fd5-202">[ビルド] ボタンを押して、ビルド プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-202">Press the Build button to begin the build process.</span></span>
    <span data-ttu-id="03fd5-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="03fd5-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span></span>

4. <span data-ttu-id="03fd5-204">アプリケーション用の新しいフォルダーを作成して、名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-204">Create and name a new folder for your application.</span></span> <span data-ttu-id="03fd5-205">以下の図では、アプリの名前のフォルダーをアプリケーションを含めることが作成されました。</span><span class="sxs-lookup"><span data-stu-id="03fd5-205">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="03fd5-206">新しく作成したフォルダーにビルドを開始するには、[フォルダーの選択] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-206">Click Select Folder to begin building to the newly created folder.</span></span> <span data-ttu-id="03fd5-207">Unity でビルドが完了すると、ビルド設定を閉じることがあります"ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="03fd5-207">After the build has completed, you may close the Build Setting" window in Unity.</span></span> 
    <span data-ttu-id="03fd5-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="03fd5-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span></span>

  > <span data-ttu-id="03fd5-209">注: ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。</span><span class="sxs-lookup"><span data-stu-id="03fd5-209">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="03fd5-210">エラー:CS0246 = tyoe または名前空間の名前が"XX"が見つかりませんでした (が存在することを使用して、ディレクティブまたはアセンブリ参照か?)。</span><span class="sxs-lookup"><span data-stu-id="03fd5-210">If you see an error such as "Error: CS0246 = The tyoe or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="03fd5-211">インストールする必要があります[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="03fd5-211">You might need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span> 
  >

5. <span data-ttu-id="03fd5-212">ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-212">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="03fd5-213">The"MixedRealityBase.sln ソリューションまたは対応する名前をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-213">Double click on the“MixedRealityBase.sln solution or the corresponding name.</span></span> <span data-ttu-id="03fd5-214">場合は、プロジェクトの代替名を使用した Visual Studio でソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-214">if you used an alternative name for your project to open the solution file in Visual Studio.</span></span>

  > <span data-ttu-id="03fd5-215">注:開いて、新しく作成されたフォルダー (つまり、アプリ フォルダー、ビルド フォルダー内の .sln ファイルと混同しないように、そのフォルダーの外部で同様に名前付きの .sln ファイルがあるため、前の手順から名前付け規則に従う場合。</span><span class="sxs-lookup"><span data-stu-id="03fd5-215">Note: Be sure to open the newly created folder (i.e., the App folder, if following the naming conventions from the previous steps because there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > <span data-ttu-id="03fd5-217">注:Visual Studio の新しいコンポーネントをインストールする場合、ご協力くださいにすべての前提条件となるコンポーネントがインストールされていることを確認します具体的に["ツールをインストールする ページ。](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="03fd5-217">Note: If Visual Studio asks to install new components, please take a moment to ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span> 

6. <span data-ttu-id="03fd5-218">USB ケーブルを使って HoloLens 2 を PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-218">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="03fd5-219">レッスンの手順では、HoloLens 2 デバイスでのテスト、デプロイする前提としています、中にすることもできますを展開する、 [HoloLens 2 エミュレーター](using-the-hololens-emulator.md)を作成することも、[サイドローディング用アプリ パッケージ](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="03fd5-219">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="03fd5-220">デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="03fd5-220">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="03fd5-221">HoloLens 2 に初めてデプロイする場合は、Visual Studio により、PIN を使用して HoloLens 2 をペアリングするよう求められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="03fd5-221">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="03fd5-222">次の[手順](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)開発者モードを有効にするか、Visual Studio とペアリングする必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="03fd5-222">Follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="03fd5-223">RM アーキテクチャと同様に、リリース構成を選択して、HoloLens 2 を構築するための Visual Studio を構成します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-223">Configure Visual Studio for building to your HoloLens 2 by selecting the Release configuration as well as the RM architecture.</span></span>
    <span data-ttu-id="03fd5-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span><span class="sxs-lookup"><span data-stu-id="03fd5-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span></span>
   
9. <span data-ttu-id="03fd5-225">最後に、デバッグを選択して、デバイスにビルド > デバッグなしで開始します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-225">The final Step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="03fd5-226">デバッグなしの開始 を選択するとすぐに Visual Studio に表示されているビルドが成功した ithout デバッグ情報を基に、デバイスで開始するアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="03fd5-226">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build ithout Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="03fd5-227">これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-227">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="03fd5-228">ビルドを選択することも可能性があります。 > を自動的に起動するアプリケーションをしなくても、デバイスに展開するには、ソリューションの配置。</span><span class="sxs-lookup"><span data-stu-id="03fd5-228">You might also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>
    <span data-ttu-id="03fd5-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span><span class="sxs-lookup"><span data-stu-id="03fd5-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span></span>
    
<span data-ttu-id="03fd5-230">10. では、指示に従います。</span><span class="sxs-lookup"><span data-stu-id="03fd5-230">10.Follow the instructions.</span></span> <span data-ttu-id="03fd5-231">次のアプリケーションがデバイスで実行しているときに、画面に表示される手順。</span><span class="sxs-lookup"><span data-stu-id="03fd5-231">When the application is running on your device, follow the on-screen instructions.</span></span> <span data-ttu-id="03fd5-232">次の手順に対応するシーン ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-232">Press the Scene buttons corresponding to the Steps below.</span></span>
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="03fd5-233">空間アンカー セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-233">Start the spatial anchors session.</span></span>
    
    2. <span data-ttu-id="03fd5-234">キューブは、別の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-234">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="03fd5-235">キューブの位置にある Azure 空間アンカーを保存します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-235">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="03fd5-236">Azure の空間アンカー セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-236">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="03fd5-237">ユーザーがキューブに移動を許可するキューブ上でローカルのアンカーを削除します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-237">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    6. <span data-ttu-id="03fd5-238">キューブの別の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-238">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="03fd5-239">Azure の空間アンカー セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-239">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="03fd5-240">Azure の空間アンカーを検索します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-240">Find Azure Spatial Anchors.</span></span> 
    
    <span data-ttu-id="03fd5-241">」に戻ってください元の場所を e は、アンカーを作成したときに配置します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-241">e You should go back to the original place you put it when you created the anchor.</span></span>
    9. <span data-ttu-id="03fd5-242">Azure の空間アンカーを削除します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-242">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="03fd5-243">Azure のセッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-243">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="03fd5-244">アンカーのエクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="03fd5-244">Anchoring an experience</span></span>

<span data-ttu-id="03fd5-245">前のセクションでは、空間のアンカーを Azure の基礎について説明しました。</span><span class="sxs-lookup"><span data-stu-id="03fd5-245">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="03fd5-246">表し、添付のアンカーを持つ親ゲーム オブジェクトを視覚化するキューブを使用しています。</span><span class="sxs-lookup"><span data-stu-id="03fd5-246">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="03fd5-247">このセクションでは、ParentAnchor オブジェクトの子として配置することによって、エクスペリエンス全体を固定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-247">In this section, you learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="03fd5-248">この例では、使用旧暦モジュールの中に作成されたアセンブリのデモ アプリケーション[レッスン 6 のベース モジュール](mrlearning-base-ch6.md)します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-248">For this example, we use the lunar module Assembly demonstration application that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="03fd5-249">旧暦モジュール アセンブリの完全なのプレハブを検索し、ドラッグ、階層に AnchorParent gameobject の子として次の図に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="03fd5-249">Search for the Lunar Module Assembly Complete prefab, and drag it into your heirarchy as a child of the AnchorParent gameobject as shown in the image below.</span></span>

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="03fd5-251">次の図に示すように、キューブがまだ公開されているように、モジュール アセンブリの位置が発生します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-251">Position the module assembly experience so that the cube is still exposed as shown in the image below.</span></span> <span data-ttu-id="03fd5-252">アプリケーションでは、ユーザーは、全体のエクスペリエンスをキューブに移動することによって再配置することができます。</span><span class="sxs-lookup"><span data-stu-id="03fd5-252">In the application, users may reposition the entire experience by moving the cube.</span></span> 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > <span data-ttu-id="03fd5-254">注:さまざまなユーザー エクスペリエンスのフローを経験を囲む境界ボックスを切り替え、位置と回転ギズモの使用を (この手順で使用)、キューブなどの再配置オブジェクトを使用するボタンの使用など、エクスペリエンスを再配置します。、など。</span><span class="sxs-lookup"><span data-stu-id="03fd5-254">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="03fd5-255">結論</span><span class="sxs-lookup"><span data-stu-id="03fd5-255">Congratulations</span></span>
<span data-ttu-id="03fd5-256">このチュートリアルでは、空間のアンカーを Azure の基礎について説明しました。</span><span class="sxs-lookup"><span data-stu-id="03fd5-256">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="03fd5-257">このレッスンでは、開始し Azure のセッションを停止し、作成、アップロード、および 1 つのデバイスでの azure のアンカーをダウンロードするためのさまざまな手順を調査できるいくつかのボタンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="03fd5-257">This esson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session, and create, upload, and download azure anchors on a single device.</span></span> <span data-ttu-id="03fd5-258">次のレッスンでは、アプリケーションの再起動後も、HoloLens の 2 を取得するために Azure のアンカー Id を保存する方法説明します。</span><span class="sxs-lookup"><span data-stu-id="03fd5-258">In the next lesson, we'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="03fd5-259">シリーズの中には、空間配置を実現し、セッションを共有する複数のユーザーについて複数のデバイス間でアンカー Id を転送する方法も学習が共有のチュートリアルの一部として近日公開予定。</span><span class="sxs-lookup"><span data-stu-id="03fd5-259">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment, and learn about multi-user shared sessions, forthcoming as part of Sharing tutorial.</span></span>

[<span data-ttu-id="03fd5-260">次のレッスン:ASA Lesson 2</span><span class="sxs-lookup"><span data-stu-id="03fd5-260">Next Lesson: ASA Lesson 2</span></span>](mrlearning-asa-ch2.md)

