---
title: マルチユーザー機能のチュートリアル - 5. Azure Spatial Anchors の共有エクスペリエンスへの統合
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604973"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="f6908-105">4.Azure Spatial Anchors の共有エクスペリエンスへの統合</span><span class="sxs-lookup"><span data-stu-id="f6908-105">4. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="f6908-106">このチュートリアルでは、Azure Spatial Anchors (ASA) を共有エクスペリエンスに統合する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="f6908-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="f6908-107">ASA により複数のデバイスが現実の世界への共通の参照を持てるようになり、ユーザーは互いの姿をその現実の物理的な位置に見たり、共有エクスペリエンスを同じ場所で見たりすることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="f6908-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="f6908-108">目標</span><span class="sxs-lookup"><span data-stu-id="f6908-108">Objectives</span></span>

* <span data-ttu-id="f6908-109">ASA を共有エクスペリエンスに統合し、複数デバイスで位置合わせする</span><span class="sxs-lookup"><span data-stu-id="f6908-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="f6908-110">ASA がローカル共有エクスペリエンスのコンテキストでどのように機能するかについての基本を学ぶ</span><span class="sxs-lookup"><span data-stu-id="f6908-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="f6908-111">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="f6908-111">Preparing the scene</span></span>

<span data-ttu-id="f6908-112">[Hierarchy]\(ヒエラルキー\) ウィンドウで **SharedPlayground** オブジェクトを展開し、**TableAnchor** オブジェクトを展開してその子オブジェクトを公開します。</span><span class="sxs-lookup"><span data-stu-id="f6908-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

<span data-ttu-id="f6908-114">[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動して、**Buttons** プレハブを [Hierarchy]\(ヒエラルキー\) ウィンドウの **TableAnchor** 子オブジェクト上にドラッグし、TableAnchor オブジェクトの子としてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="f6908-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab on top of the **TableAnchor** child object in the Hierarchy window to add it to your scene as a child of the TableAnchor object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="f6908-116">シーンを操作するためのボタンの構成</span><span class="sxs-lookup"><span data-stu-id="f6908-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="f6908-117">このセクションでは一連のボタン イベントを構成して、Azure Spatial Anchors を使用して共有エクスペリエンスでの空間的な位置合わせを実現する方法の基本を示します。</span><span class="sxs-lookup"><span data-stu-id="f6908-117">In this section, you will configure a series of button events that demonstrate the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="f6908-118">[Hierarchy]\(ヒエラルキー\) ウィンドウで **Button** オブジェクトを展開し、**StartAzureSession** という名前の最初の子ボタン オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="f6908-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

<span data-ttu-id="f6908-120">[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探し、**OnClick ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="f6908-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="f6908-121">**"None (Object)"(なし (オブジェクト))** フィールドに、**TableAnchor** オブジェクトを割り当てる</span><span class="sxs-lookup"><span data-stu-id="f6908-121">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="f6908-122">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  > **StartAzureSession ()** 関数を選択する</span><span class="sxs-lookup"><span data-stu-id="f6908-122">From **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

<span data-ttu-id="f6908-124">[Hierarchy]\(ヒエラルキー\) ウィンドウで **CreateAzureAnchor** という名前の 2 番目の子ボタン オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探して **OnClick ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="f6908-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="f6908-125">**"None (Object)"(なし (オブジェクト))** フィールドに、**TableAnchor** オブジェクトを割り当てる</span><span class="sxs-lookup"><span data-stu-id="f6908-125">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="f6908-126">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  > **CreateAzureAnchor()** 関数を選択する</span><span class="sxs-lookup"><span data-stu-id="f6908-126">From **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="f6908-127">表示される新しい **"None (Game Object)"(なし (ゲーム オブジェクト))** フィールドに、**TableAnchor** オブジェクトを割り当てる</span><span class="sxs-lookup"><span data-stu-id="f6908-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

<span data-ttu-id="f6908-129">[Hierarchy]\(ヒエラルキー\) ウィンドウで **ShareAzureAnchor** という名前の 3 番目の子ボタン オブジェクトを選択して、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探して **OnClick ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="f6908-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="f6908-130">**"None (Object)"(なし (オブジェクト))** フィールドに、**TableAnchor** オブジェクトを割り当てる</span><span class="sxs-lookup"><span data-stu-id="f6908-130">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="f6908-131">**[No Function]** (関数なし) ドロップダウンから、 **[SharingModuleScript]**  > **ShareAzureAnchor()** 関数を選択する</span><span class="sxs-lookup"><span data-stu-id="f6908-131">From **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

<span data-ttu-id="f6908-133">[Hierarchy]\(ヒエラルキー\) ウィンドウで **GetAzureAnchor** という名前の 4 番目の子ボタン オブジェクトを選択して、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探して **OnClick ()** イベントを次のように構成します:</span><span class="sxs-lookup"><span data-stu-id="f6908-133">In the Hierarchy window, select the forth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="f6908-134">**"None (Object)"(なし (オブジェクト))** フィールドに、**TableAnchor** オブジェクトを割り当てる</span><span class="sxs-lookup"><span data-stu-id="f6908-134">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="f6908-135">**[No Function]** (関数なし) ドロップダウンから、 **[SharingModuleScript]**  > **GetAzureAnchor()** 関数を選択する</span><span class="sxs-lookup"><span data-stu-id="f6908-135">From **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="f6908-137">シーンを Azure リソースに接続する</span><span class="sxs-lookup"><span data-stu-id="f6908-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="f6908-138">[Hierarchy]\(ヒエラルキー\) ウィンドウで **SharedPlayground** オブジェクトを展開し、**TableAnchor** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="f6908-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span> <span data-ttu-id="f6908-139">[Inspector]\(インスペクター\) ウィンドウで **Spatial Anchor Manager (Script)** コンポーネントを探し、このチュートリアル シリーズの「[前提条件](mrlearning-sharing(photon)-ch1.md#prerequisites)」の部分で作成した Azure Spatial Anchors アカウントからの資格情報を使用して、 **[Credentials]\(資格情報\)** セクションを構成します。</span><span class="sxs-lookup"><span data-stu-id="f6908-139">Then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mrlearning-sharing(photon)-ch1.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="f6908-140">**"Spatial Anchors Account ID"(Spatial Anchors アカウント ID)** フィールドに、Azure Spatial Anchors アカウントからの**アカウント ID** を貼り付ける</span><span class="sxs-lookup"><span data-stu-id="f6908-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="f6908-141">**"Spatial Anchors Account Key"(Spatial Anchors アカウント キー)** フィールドに、Azure Spatial Anchors アカウントからのプライマリまたはセカンダリ **アクセス キー** を貼り付ける</span><span class="sxs-lookup"><span data-stu-id="f6908-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

<span data-ttu-id="f6908-143">**TableAnchor** オブジェクトを選択したまま、[Inspector]\(インスペクター\) ウィンドウですべてのスクリプト コンポーネントが有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f6908-143">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are enabled:</span></span>

* <span data-ttu-id="f6908-144">**Spatial Anchor Manager (Script)** コンポーネントの隣にあるチェックボックスをオンにして有効にする</span><span class="sxs-lookup"><span data-stu-id="f6908-144">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="f6908-145">**Anchor Module Script (Script)** コンポーネントの隣にあるチェックボックスをオンにして有効にする</span><span class="sxs-lookup"><span data-stu-id="f6908-145">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="f6908-146">**Sharing Module Script (Script)** コンポーネントの隣にあるチェックボックスをオンにして有効にする</span><span class="sxs-lookup"><span data-stu-id="f6908-146">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="f6908-148">空間的な位置合わせのエクスペリエンスを試す</span><span class="sxs-lookup"><span data-stu-id="f6908-148">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="f6908-149">Azure Spatial Anchors を Unity で実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="f6908-149">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="f6908-150">そのため、Azure Spatial Anchors の機能をテストするには、最低 2 台の HoloLens デバイスにプロジェクトを配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6908-150">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two HoloLens devices.</span></span>

<span data-ttu-id="f6908-151">Unity プロジェクトをビルドして 2 台の HoloLens デバイスに配置すると、Azure Anchor ID を共有してデバイス間で空間的な位置合わせを実現できます。</span><span class="sxs-lookup"><span data-stu-id="f6908-151">If you now build and deploy the Unity project to two HoloLens devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="f6908-152">これをテストするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f6908-152">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="f6908-153">HoloLens デバイス 1 で次のようにします。**アプリケーションを開始する** (Rocket Launcher のインスタンスが作成され、テーブルに配置されます)</span><span class="sxs-lookup"><span data-stu-id="f6908-153">On HoloLens device 1: **Start the application** (the Rocket Launcher is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="f6908-154">HoloLens デバイス 2 で次のようにします。**アプリケーションを開始する** (両方のユーザーが Rocket Launcher のあるテーブルを見ることができますが、テーブルは同じ場所には表示されず、ユーザー アバターはユーザーが実際にいるところに表示されません)</span><span class="sxs-lookup"><span data-stu-id="f6908-154">On HoloLens device 2: **Start the application** (both users see the table with the Rocket Launcher, however, the table does not appear in the same place and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="f6908-155">HoloLens デバイス 1 で次のようにします。 **[Start Azure Session]\(Azure セッションの開始\)** ボタンを押す</span><span class="sxs-lookup"><span data-stu-id="f6908-155">On HoloLens device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="f6908-156">HoloLens デバイス 1 で次のようにします。 **[Create Azure Anchor]\(Azure Anchor の作成\)** ボタンを押す (TableAnchor オブジェクトの場所にアンカーが作成され、アンカーの情報が Azure リソースに保存されます)。</span><span class="sxs-lookup"><span data-stu-id="f6908-156">On HoloLens device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="f6908-157">HoloLens デバイス 1 で次のようにします。 **[Share Azure Anchor]\(Azure Anchor の共有\)** ボタンを押す (他のユーザーとアンカー ID がリアルタイムで共有されます)</span><span class="sxs-lookup"><span data-stu-id="f6908-157">On HoloLens device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="f6908-158">HoloLens デバイス 2 で次のようにします。 **[Start Azure Session]\(Azure セッションの開始\)** ボタンを押す</span><span class="sxs-lookup"><span data-stu-id="f6908-158">On HoloLens device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="f6908-159">HoloLens デバイス 2 で次のようにします。 **[Get Azure Anchor]\(Azure Anchor の取得\)** を押す (Azure リソースに接続して共有アンカー ID のアンカー情報が取得され、TableAnchor オブジェクトは HoloLens デバイス 1 でアンカーを作成した場所に移動します)</span><span class="sxs-lookup"><span data-stu-id="f6908-159">On HoloLens device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the HoloLens device 1)</span></span>

## <a name="congratulations"></a><span data-ttu-id="f6908-160">結論</span><span class="sxs-lookup"><span data-stu-id="f6908-160">Congratulations</span></span>

<span data-ttu-id="f6908-161">このチュートリアルでは、Azure の強力な Spatial Anchors を統合して、複数のデバイスを共有エクスペリエンスの中に配置する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="f6908-161">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span> <span data-ttu-id="f6908-162">これでこのチュートリアル シリーズは終了となります。Photon アカウントとアプリケーションを設定し、Photon と PUN を Unity アプリケーションに統合し、ユーザー アバターと共有オブジェクトを構成し、最後に ASA を使用して複数の参加者を配置する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="f6908-162">This also concludes this tutorial series where you have learned how to set up a Photon account and application, integrate Photon and PUN into a Unity application, configure user avatars and shared objects, and finally align multiple participants using ASA.</span></span>
