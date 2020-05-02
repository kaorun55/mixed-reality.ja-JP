---
title: Azure Spatial Anchors チュートリアル - 2. Azure Spatial Anchors の保存、取得、および共有
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 36f25229469e848a3f0612a5971cc8e9381262f5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "80362009"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="1cd2a-105">2.Azure Spatial Anchors の保存、取得、および共有</span><span class="sxs-lookup"><span data-stu-id="1cd2a-105">2. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="1cd2a-106">このチュートリアルでは、HoloLens 2 のストレージにアンカー ID を保存することにより、複数のアプリ セッションにわたって Azure Spatial Anchors を保存する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-106">In this tutorial, you will learn how to save Azure Spatial Anchors across multiple app sessions by saving the anchor ID to the HoloLens 2's storage.</span></span> <span data-ttu-id="1cd2a-107">また、このアンカー ID を他のデバイスと共有して、複数デバイスのアンカーの位置合わせ行う方法についても学習します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-107">You will also learn how to share this anchor ID to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="1cd2a-108">目標</span><span class="sxs-lookup"><span data-stu-id="1cd2a-108">Objectives</span></span>

* <span data-ttu-id="1cd2a-109">アプリ セッション間で永続化するために、Azure Spatial Anchor ID を HoloLens 2 ローカル ディスクに保存したり、そこから取得したりする方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-109">Learn how to save and retrieve Azure Spatial Anchor IDs to and from the HoloLens 2 local disk, for persistence between app sessions</span></span>
* <span data-ttu-id="1cd2a-110">マルチデバイス シナリオで、Azure Spatial Anchor ID をユーザー間で共有する方法について学習します</span><span class="sxs-lookup"><span data-stu-id="1cd2a-110">Learn how to share Azure Spatial Anchor IDs between users in a multi-device scenario</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="1cd2a-111">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="1cd2a-111">Preparing the scene</span></span>

<span data-ttu-id="1cd2a-112">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.AzureSpatialAnchors]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-112">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="1cd2a-113">Ctrl ボタンを押したまま、 **[ButtonParent_SaveAnchorId]** および **[ButtonParent_ShareAnchorId]** をクリックして 2 つのプレハブを選択し、これらを [Hierarchy]\(階層\) ウィンドウにドラッグしてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-113">While holding down the CTRL button, click on **ButtonParent_SaveAnchorId** and **ButtonParent_ShareAnchorId** to select the two prefabs, then drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="1cd2a-115">アプリ セッション間で Azure Anchors を永続化する - アンカー ID をディスクに保存する</span><span class="sxs-lookup"><span data-stu-id="1cd2a-115">Persist Azure Anchors between app sessions - Save anchor ID to disk</span></span>
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

<span data-ttu-id="1cd2a-116">このセクションでは、Azure Anchor ID を HoloLens 2 ローカル ディスクに保存したり、そこから取得したりするについて学習します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-116">In this section, you will learn how to save and retrieve the Azure Anchor ID to and from the HoloLens 2 local disk.</span></span> <span data-ttu-id="1cd2a-117">これにより、Azure に対して、異なるアプリ セッション間で同じアンカー ID をクエリできるため、固定されたホログラムを前のアプリ セッションと同じ場所に配置できます。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-117">This will allow you to query Azure for the same anchor ID between different app sessions, allowing the anchored holograms to be position at the same location as in the previous app session.</span></span>

<span data-ttu-id="1cd2a-118">[Hierarchy]\(階層\) ウィンドウで、Azure Anchor ID を HoloLens 2 ストレージに保存するためのボタンと、保存された ID をディスクから取得するためのボタンの 2 つのボタンを含む **[ButtonParent_SaveAnchorId]** オブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-118">In the Hierarchy window, expand the **ButtonParent_SaveAnchorId** object which contains two buttons, one button for saving the Azure Anchor ID to the HoloLens 2 storage and another for retrieving the saved ID from the disk:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

<span data-ttu-id="1cd2a-120">前のチュートリアルの[シーンを操作するためのボタンの構成](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)と同じ手順に従い、**Pressable Button Holo Lens 2 (Script)** コンポーネントと **Interactable (Script)** コンポーネントを次の 2 つのボタンそれぞれに対して構成します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-120">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="1cd2a-121">**[SaveAzureAnchorIdToDisk]** オブジェクトの場合、[AnchorModuleScript] > **[SaveAzureAnchorIdToDisk ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-121">For the **SaveAzureAnchorIdToDisk** object, assign the AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** function.</span></span>
* <span data-ttu-id="1cd2a-122">**[GetAzureAnchorIdFromDisk]** オブジェクトの場合、[AnchorModuleScript] > **[GetAzureAnchorIdFromDisk ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-122">For the **GetAzureAnchorIdFromDisk** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** function.</span></span>

<span data-ttu-id="1cd2a-123">更新されたアプリケーションを HoloLens にビルドすると、Azure Anchor ID を保存することで、アプリ セッション間で Azure Spatial Anchors を永続化できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-123">If you build the updated application to your HoloLens, you can now persist Azure Spatial Anchors between app sessions by saving the Azure Anchor ID.</span></span> <span data-ttu-id="1cd2a-124">これをテストするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-124">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="1cd2a-125">ロケット発射台エクスペリエンスを目的の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-125">Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="1cd2a-126">Azure セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-126">Start Azure Session.</span></span>
3. <span data-ttu-id="1cd2a-127">Azure Anchor を作成します (ロケット発射台エクスペリエンスの場所にアンカーを作成します)。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-127">Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="1cd2a-128">Azure Anchor ID をディスクに保存します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-128">Save Azure Anchor ID to Disk.</span></span>
5. <span data-ttu-id="1cd2a-129">アプリケーションを再起動します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-129">Restart the application.</span></span>
6. <span data-ttu-id="1cd2a-130">ディスクから Azure Anchor を取得します (保存したアンカー ID を読み込みます)。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-130">Get Azure Anchor from Disk (loads the anchor ID you just saved).</span></span>
7. <span data-ttu-id="1cd2a-131">Azure セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-131">Start Azure Session.</span></span>
8. <span data-ttu-id="1cd2a-132">Azure Anchor を見つけます (手順 3 の場所にロケット発射台エクスペリエンスを配置します)。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-132">Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

> [!NOTE]
> <span data-ttu-id="1cd2a-133">アプリケーションを完全に再起動するには、イマーシブ アプリ ビューを終了した後、[スタート] メニューからアプリケーションを再起動する前に、Mixed Reality ホームのアプリ ウィンドウを閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-133">To fully restart the application, after exiting the immersive app view, the app window in the mixed reality home needs to be closed before relaunching the application from the Start menu.</span></span> <span data-ttu-id="1cd2a-134">詳細については、「[HoloLens でアプリを使用する](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens)」のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-134">For additional details, you can refer to the [Using apps on HoloLens](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens) documentation.</span></span>

## <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="1cd2a-135">複数のデバイス間で Azure Anchor を共有する</span><span class="sxs-lookup"><span data-stu-id="1cd2a-135">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="1cd2a-136">このセクションでは、複数のデバイス間で Azure Anchor ID を共有する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-136">In this section, you will learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="1cd2a-137">これにより、複数のデバイスが同じアンカー ID を Azure に対してクエリできるようになり、固定されたホログラムを空間的に位置合わせできるようになります。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-137">This will allow multiple devices to query Azure for the same anchor ID, allowing the anchored holograms to be spatially aligned.</span></span> <span data-ttu-id="1cd2a-138">空間的な位置合わせ、つまり複数のデバイス間で同じ物理的な場所に同じホログラムを表示できることは、HoloLens 2 のローカル共有エクスペリエンスにとって重要です。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-138">Spatial alignment, i.e. seeing the same holograms in the same physical location between multiple devices, is key to local shared experiences in the HoloLens 2.</span></span>

<span data-ttu-id="1cd2a-139">Azure Anchor ID をデバイス間で転送するには、[マルチユーザー機能のチュートリアル](mrlearning-sharing(photon)-ch1.md) シリーズで説明されている方法など、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-139">There are many ways to transfer Azure Anchor IDs between devices, including methods outlined in the the [Multi-user capabilities tutorials](mrlearning-sharing(photon)-ch1.md) series.</span></span> <span data-ttu-id="1cd2a-140">この例では、デバイス間でアンカー ID をアップロードおよびダウンロードする単純な Web サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-140">In this example, you will use a simple web service to upload and download anchor IDs between devices.</span></span>

<span data-ttu-id="1cd2a-141">[Hierarchy]\(階層\) ウィンドウで、 Azure Anchor ID を Web サーバーにアップロードするためのボタンと、ID を Web サーバーからダウンロードするためのボタンの 2 つのボタンを含む **[ButtonParent_ShareAnchorId]** オブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-141">In the Hierarchy window, expand the **ButtonParent_ShareAnchorId** object which contains two buttons; one button for uploading the Azure Anchor ID to the web server, and another for downloading the ID from the web server:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

<span data-ttu-id="1cd2a-143">前のチュートリアルの[シーンを操作するためのボタンの構成](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)と同じ手順に従い、**Pressable Button Holo Lens 2 (Script)** コンポーネントと **Interactable (Script)** コンポーネントを次の 2 つのボタンそれぞれに対して構成します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-143">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="1cd2a-144">**[ShareAzureAnchorIdToNetwork]** オブジェクトの場合は、[AnchorModuleScript] > **[ShareAzureAnchorIdToNetwork ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-144">For the **ShareAzureAnchorIdToNetwork** object, assign the AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** function.</span></span>
* <span data-ttu-id="1cd2a-145">**[GetAzureAnchorIdFromNetwork]** オブジェクトの場合は、[AnchorModuleScript] > **[GetAzureAnchorIdFromNetwork ()]** 関数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-145">For the **GetAzureAnchorIdFromNetwork** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** function.</span></span>

<span data-ttu-id="1cd2a-146">更新されたアプリケーションを 2 つの HoloLens デバイスにビルドすると、Azure Anchor ID を共有することで、デバイス間で空間的な位置合わせを実現できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-146">If you build the updated application to two HoloLens devices, you can now achieve spatial alignment between them by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="1cd2a-147">これをテストするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-147">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="1cd2a-148">HoloLens デバイス 1 で次のようにします。ロケット発射台エクスペリエンスを目的の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-148">On HoloLens device 1: Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="1cd2a-149">HoloLens デバイス 1 で次のようにします。Azure セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-149">On HoloLens device 1: Start Azure Session.</span></span>
3. <span data-ttu-id="1cd2a-150">HoloLens デバイス 1 で次のようにします。Azure Anchor を作成します (ロケット発射台エクスペリエンスの場所にアンカーを作成します)。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-150">On HoloLens device 1: Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="1cd2a-151">HoloLens デバイス 1 で次のようにします。Azure Anchor ID をネットワークに共有します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-151">On HoloLens device 1: Share Azure Anchor ID to Network.</span></span>
5. <span data-ttu-id="1cd2a-152">HoloLens デバイス 2 で次のようにします。アプリケーションを開始します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-152">On HoloLens device 2: Start the application.</span></span>
6. <span data-ttu-id="1cd2a-153">HoloLens デバイス 2 で次のようにします。ネットワークから共有アンカー ID を取得します (HoloLens デバイス 1 から共有されたアンカー ID を取得します)。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-153">On HoloLens device 2: Get Shared Anchor ID from Network (fetches the anchor ID just shared from HoloLens device 1).</span></span>
7. <span data-ttu-id="1cd2a-154">HoloLens デバイス 2 で次のようにします。Azure セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-154">On HoloLens device 2: Start Azure Session.</span></span>
8. <span data-ttu-id="1cd2a-155">HoloLens デバイス 2 で次のようにします。Azure Anchor を見つけます (手順 3 の場所にロケット発射台エクスペリエンスを配置します)。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-155">On HoloLens device 2: Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

> [!TIP]
> <span data-ttu-id="1cd2a-156">HoloLens が 1 つしかない場合でも、2 つ目の HoloLens デバイスを使用する代わりにアプリケーションを再起動することで、機能をテストできます。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-156">If you only have one HoloLens, you can still test the functionality by restarting the application instead of using a second HoloLens device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="1cd2a-157">結論</span><span class="sxs-lookup"><span data-stu-id="1cd2a-157">Congratulations</span></span>

<span data-ttu-id="1cd2a-158">このチュートリアルでは、Azure Spatial Anchor ID を HoloLens のローカル ディスクに保存することで、アプリケーションのセッションとアプリケーションの再起動を通して Azure Spatial Anchors を永続化する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-158">In this tutorial you learned how to persist Azure Spatial Anchors between application sessions and application restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens.</span></span> <span data-ttu-id="1cd2a-159">また、Azure Spatial Anchors を複数のデバイス間で共有し、基本的なマルチユーザーの静的ホログラム共有エクスペリエンスを実現する方法についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-159">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="1cd2a-160">次のチュートリアルでは、リアルタイムのフィードバックをユーザーに提供する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-160">In the next tutorial you will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="1cd2a-161">このフィードバックには、アンカーの作成、環境の品質についての理解、および Azure セッションの状態に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-161">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="1cd2a-162">フィードバックがなければ、アンカーが Azure に正常にアップロードされたかどうか、環境の品質がアンカーの作成に十分であるかどうか、または現在の状態をユーザーが知ることができません。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-162">Without feedback, users may not know whether an anchor has successfully been uploaded to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="1cd2a-163">次のレッスン:3.Azure Spatial Anchors フィードバックの表示</span><span class="sxs-lookup"><span data-stu-id="1cd2a-163">Next Lesson: 3. Displaying Azure Spatial Anchor feedback</span></span>](mrlearning-asa-ch3.md)
