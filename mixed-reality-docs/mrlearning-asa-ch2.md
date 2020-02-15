---
title: Azure 空間アンカーチュートリアル-2. Azure 空間アンカーの保存、取得、共有
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 7b19233a9634e2568200476c9483464bbf9dd3c8
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250745"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="684b3-105">2. Azure 空間アンカーを保存、取得、共有する</span><span class="sxs-lookup"><span data-stu-id="684b3-105">2. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="684b3-106">このチュートリアルでは、HoloLens 2 のストレージにアンカー ID を保存することにより、複数のアプリセッションにわたって Azure 空間アンカーを保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="684b3-106">In this tutorial, you will learn how to save Azure Spatial Anchors across multiple app sessions by saving the anchor ID to the HoloLens 2's storage.</span></span> <span data-ttu-id="684b3-107">また、このアンカー ID を他のデバイスと共有して、複数デバイスのアンカーの配置を行う方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="684b3-107">You will also learn how to share this anchor ID to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="684b3-108">目標</span><span class="sxs-lookup"><span data-stu-id="684b3-108">Objectives</span></span>

* <span data-ttu-id="684b3-109">アプリセッション間の永続化のために、HoloLens 2 ローカルディスクとの間で Azure 空間アンカー Id を保存および取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="684b3-109">Learn how to save and retrieve Azure Spatial Anchor IDs to and from the HoloLens 2 local disk, for persistence between app sessions</span></span>
* <span data-ttu-id="684b3-110">マルチデバイスシナリオでユーザー間で Azure 空間アンカー Id を共有する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="684b3-110">Learn how to share Azure Spatial Anchor IDs between users in a multi-device scenario</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="684b3-111">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="684b3-111">Preparing the scene</span></span>

<span data-ttu-id="684b3-112">[プロジェクト] ウィンドウで、[**アセット** > **mrtk] に移動します。AzureSpatialAnchors** > **Prefabs**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="684b3-112">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="684b3-113">CTRL ボタンを押したまま、 **ButtonParent_SaveAnchorId**をクリックして**ButtonParent_ShareAnchorId** 2 つの prefabs を選択し、階層 ウィンドウにドラッグしてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="684b3-113">While holding down the CTRL button, click on **ButtonParent_SaveAnchorId** and **ButtonParent_ShareAnchorId** to select the two prefabs, then drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="684b3-115">アプリセッション間で Azure のアンカーを保持する-アンカー ID をディスクに保存する</span><span class="sxs-lookup"><span data-stu-id="684b3-115">Persist Azure Anchors between app sessions - Save anchor ID to disk</span></span>
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

<span data-ttu-id="684b3-116">このセクションでは、HoloLens 2 ローカルディスクとの間で Azure Anchor ID を保存および取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="684b3-116">In this section, you will learn how to save and retrieve the Azure Anchor ID to and from the HoloLens 2 local disk.</span></span> <span data-ttu-id="684b3-117">これにより、異なるアプリセッション間で同じアンカー ID の Azure に対してクエリを実行できるため、固定されたホログラムを前のアプリセッションと同じ場所に配置できます。</span><span class="sxs-lookup"><span data-stu-id="684b3-117">This will allow you to query Azure for the same anchor ID between different app sessions, allowing the anchored holograms to be position at the same location as in the previous app session.</span></span>

<span data-ttu-id="684b3-118">[階層] ウィンドウで、2つのボタンが含まれている**ButtonParent_SaveAnchorId**オブジェクトを展開します。1つは、AZURE Anchor ID を HoloLens 2 ストレージに保存するためのボタンで、もう1つは、保存された id をディスクから取得するためのボタンです。</span><span class="sxs-lookup"><span data-stu-id="684b3-118">In the Hierarchy window, expand the **ButtonParent_SaveAnchorId** object which contains two buttons, one button for saving the Azure Anchor ID to the HoloLens 2 storage and another for retrieving the saved ID from the disk:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

<span data-ttu-id="684b3-120">前のチュートリアルの「[シーンの指示を操作するためのボタンの構成](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)」の手順に従って、 **Pressable Button Holo レンズ 2 (スクリプト)** コンポーネントと**対話型 (スクリプト)** コンポーネントを次の2つのボタンにそれぞれ構成します。</span><span class="sxs-lookup"><span data-stu-id="684b3-120">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="684b3-121">**SaveAzureAnchorIdToDisk**オブジェクトの場合は、AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="684b3-121">For the **SaveAzureAnchorIdToDisk** object, assign the AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** function.</span></span>
* <span data-ttu-id="684b3-122">**GetAzureAnchorIdFromDisk**オブジェクトの場合は、AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="684b3-122">For the **GetAzureAnchorIdFromDisk** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** function.</span></span>

<span data-ttu-id="684b3-123">更新されたアプリケーションを HoloLens にビルドすると、Azure アンカー ID を保存することで、アプリセッション間で Azure 空間アンカーを永続化できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="684b3-123">If you build the updated application to your HoloLens, you can now persist Azure Spatial Anchors between app sessions by saving the Azure Anchor ID.</span></span> <span data-ttu-id="684b3-124">テストするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="684b3-124">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="684b3-125">ロケットランチャーエクスペリエンスを目的の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="684b3-125">Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="684b3-126">Azure セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="684b3-126">Start Azure Session.</span></span>
3. <span data-ttu-id="684b3-127">Azure Anchor を作成します (ロケットランチャーエクスペリエンスの場所にアンカーを作成します)。</span><span class="sxs-lookup"><span data-stu-id="684b3-127">Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="684b3-128">Azure Anchor ID をディスクに保存します。</span><span class="sxs-lookup"><span data-stu-id="684b3-128">Save Azure Anchor ID to Disk.</span></span>
5. <span data-ttu-id="684b3-129">アプリケーションを再起動します。</span><span class="sxs-lookup"><span data-stu-id="684b3-129">Restart the application.</span></span>
6. <span data-ttu-id="684b3-130">ディスクから Azure アンカーを取得します (保存したアンカー ID が読み込まれます)。</span><span class="sxs-lookup"><span data-stu-id="684b3-130">Get Azure Anchor from Disk (loads the anchor ID you just saved).</span></span>
7. <span data-ttu-id="684b3-131">Azure セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="684b3-131">Start Azure Session.</span></span>
8. <span data-ttu-id="684b3-132">Azure Anchor を探します (手順 3. の場所にロケットランチャーエクスペリエンスを配置します)。</span><span class="sxs-lookup"><span data-stu-id="684b3-132">Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

## <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="684b3-133">複数のデバイス間で Azure アンカーを共有する</span><span class="sxs-lookup"><span data-stu-id="684b3-133">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="684b3-134">このセクションでは、複数のデバイス間で Azure Anchor ID を共有する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="684b3-134">In this section, you will learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="684b3-135">これにより、複数のデバイスが同じアンカー ID に対して Azure に対してクエリを実行できるようになり、固定されたホログラムを空間的に配置できるようになります。</span><span class="sxs-lookup"><span data-stu-id="684b3-135">This will allow multiple devices to query Azure for the same anchor ID, allowing the anchored holograms to be spatially aligned.</span></span> <span data-ttu-id="684b3-136">空間の配置。つまり、複数のデバイス間で同じ物理的な場所に同じホログラムがある場合は、HoloLens 2 のローカル共有エクスペリエンスが重要になります。</span><span class="sxs-lookup"><span data-stu-id="684b3-136">Spatial alignment, i.e. seeing the same holograms in the same physical location between multiple devices, is key to local shared experiences in the HoloLens 2.</span></span>

<span data-ttu-id="684b3-137">[複数ユーザー機能のチュートリアル](mrlearning-sharing(photon)-ch1.md)シリーズに記載されている方法を含め、デバイス間で Azure Anchor id を転送する方法は多数あります。</span><span class="sxs-lookup"><span data-stu-id="684b3-137">There are many ways to transfer Azure Anchor IDs between devices, including methods outlined in the the [Multi-user capabilities tutorials](mrlearning-sharing(photon)-ch1.md) series.</span></span> <span data-ttu-id="684b3-138">この例では、単純な web サービスを使用して、デバイス間でアンカー Id をアップロードしてダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="684b3-138">In this example, you will use a simple web service to upload and download anchor IDs between devices.</span></span>

<span data-ttu-id="684b3-139">[階層] ウィンドウで、2つのボタンを含む**ButtonParent_ShareAnchorId**オブジェクトを展開します。Azure Anchor ID を web サーバーにアップロードするためのボタンと、web サーバーから ID をダウンロードするためのボタンの1つです。</span><span class="sxs-lookup"><span data-stu-id="684b3-139">In the Hierarchy window, expand the **ButtonParent_ShareAnchorId** object which contains two buttons; one button for uploading the Azure Anchor ID to the web server, and another for downloading the ID from the web server:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

<span data-ttu-id="684b3-141">前のチュートリアルの「[シーンの指示を操作するためのボタンの構成](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)」の手順に従って、 **Pressable Button Holo レンズ 2 (スクリプト)** コンポーネントと**対話型 (スクリプト)** コンポーネントを次の2つのボタンにそれぞれ構成します。</span><span class="sxs-lookup"><span data-stu-id="684b3-141">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="684b3-142">**ShareAzureAnchorIdToNetwork**オブジェクトの場合は、AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="684b3-142">For the **ShareAzureAnchorIdToNetwork** object, assign the AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** function.</span></span>
* <span data-ttu-id="684b3-143">**GetAzureAnchorIdFromNetwork**オブジェクトの場合は、AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="684b3-143">For the **GetAzureAnchorIdFromNetwork** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** function.</span></span>

<span data-ttu-id="684b3-144">更新されたアプリケーションを2つの HoloLens デバイスにビルドすると、Azure アンカー ID を共有することによって、それらの間で空間の配置を実現できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="684b3-144">If you build the updated application to two HoloLens devices, you can now achieve spatial alignment between them by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="684b3-145">テストするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="684b3-145">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="684b3-146">HoloLens デバイス 1: ロケットランチャーエクスペリエンスを目的の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="684b3-146">On HoloLens device 1: Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="684b3-147">HoloLens デバイス 1: Azure セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="684b3-147">On HoloLens device 1: Start Azure Session.</span></span>
3. <span data-ttu-id="684b3-148">HoloLens デバイス 1: Azure アンカーを作成します (ロケットランチャーエクスペリエンスの場所にアンカーを作成します)。</span><span class="sxs-lookup"><span data-stu-id="684b3-148">On HoloLens device 1: Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="684b3-149">HoloLens デバイス 1: Azure Anchor ID をネットワークに共有します。</span><span class="sxs-lookup"><span data-stu-id="684b3-149">On HoloLens device 1: Share Azure Anchor ID to Network.</span></span>
5. <span data-ttu-id="684b3-150">HoloLens デバイス 2: アプリケーションを再起動します。</span><span class="sxs-lookup"><span data-stu-id="684b3-150">On HoloLens device 2: Restart the application.</span></span>
6. <span data-ttu-id="684b3-151">HoloLens デバイス 2: ネットワークから共有アンカー ID を取得します (HoloLens デバイス1から共有されたアンカー ID をフェッチします)。</span><span class="sxs-lookup"><span data-stu-id="684b3-151">On HoloLens device 2: Get Shared Anchor ID from Network (fetches the anchor ID just shared from HoloLens device 1).</span></span>
7. <span data-ttu-id="684b3-152">HoloLens デバイス 2: Azure セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="684b3-152">On HoloLens device 2: Start Azure Session.</span></span>
8. <span data-ttu-id="684b3-153">HoloLens デバイス 2: Azure アンカーを検索します (手順 3. の場所でロケットランチャーエクスペリエンスを配置します)。</span><span class="sxs-lookup"><span data-stu-id="684b3-153">On HoloLens device 2: Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

> [!TIP]
> <span data-ttu-id="684b3-154">HoloLens が1つしかない場合でも、2つ目の HoloLens デバイスを使用する代わりにアプリケーションを再起動することで、機能をテストできます。</span><span class="sxs-lookup"><span data-stu-id="684b3-154">If you only have one HoloLens, you can still test the functionality by restarting the application instead of using a second HoloLens device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="684b3-155">結論</span><span class="sxs-lookup"><span data-stu-id="684b3-155">Congratulations</span></span>

<span data-ttu-id="684b3-156">このチュートリアルでは、azure 空間アンカー ID を HoloLens のローカルディスクに保存することで、アプリケーションセッションとアプリケーションの再起動の間で Azure 空間アンカーを永続化する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="684b3-156">In this tutorial you learned how to persist Azure Spatial Anchors between application sessions and application restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens.</span></span> <span data-ttu-id="684b3-157">また、複数のデバイス間で Azure 空間アンカーを共有し、基本的なマルチユーザーの静的なホログラム共有エクスペリエンスを実現する方法についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="684b3-157">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="684b3-158">次のチュートリアルでは、リアルタイムのフィードバックをユーザーに提供する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="684b3-158">In the next tutorial you will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="684b3-159">このフィードバックには、アンカーの作成、環境の理解の質、Azure セッションの状態に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="684b3-159">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="684b3-160">フィードバックがないと、アンカーが Azure に正常にアップロードされたかどうか、環境の品質がアンカーの作成に十分であるか、現在の状態であるかをユーザーが知ることができません。</span><span class="sxs-lookup"><span data-stu-id="684b3-160">Without feedback, users may not know whether an anchor has successfully been uploaded to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="684b3-161">次のレッスン: 3. Azure 空間アンカーフィードバックの表示</span><span class="sxs-lookup"><span data-stu-id="684b3-161">Next Lesson: 3. Displaying Azure Spatial Anchor feedback</span></span>](mrlearning-asa-ch3.md)
