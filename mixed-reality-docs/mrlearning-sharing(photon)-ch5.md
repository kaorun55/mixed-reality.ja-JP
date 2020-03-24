---
title: マルチユーザー機能のチュートリアル - 5. Azure Spatial Anchors の共有エクスペリエンスへの統合
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031685"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="10950-105">5.Azure Spatial Anchors の共有エクスペリエンスへの統合</span><span class="sxs-lookup"><span data-stu-id="10950-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="10950-106">このレッスンでは、Azure Spatial Anchors (ASA) を共有エクスペリエンスに統合する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="10950-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="10950-107">ASA を使用すると、併置された複数のデバイスは、その物理的環境が仮想エクスペリエンスを支えてすべての参加者が同じ物理的な場所でオブジェクトを見るようにする場合、共通参照を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="10950-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="10950-108">目標</span><span class="sxs-lookup"><span data-stu-id="10950-108">Objectives</span></span>

* <span data-ttu-id="10950-109">ASA をマルチデバイス配置の共有エクスペリエンスに統合する。</span><span class="sxs-lookup"><span data-stu-id="10950-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="10950-110">ASA がローカル共有エクスペリエンスのコンテキストでどのように機能するかについての基本を学ぶ。</span><span class="sxs-lookup"><span data-stu-id="10950-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="10950-111">手順</span><span class="sxs-lookup"><span data-stu-id="10950-111">Instructions</span></span>

1. <span data-ttu-id="10950-112">MixedRealityPlayspace 親オブジェクトの下にある TableAnchor プレハブを選択し、削除します。</span><span class="sxs-lookup"><span data-stu-id="10950-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="10950-114">[Project]\(プロジェクト\) ビューで、[Assets]\(アセット\) -> [Resources]\(リソース\) -> [Prefabs]\(プレハブ\) の順に移動し、TableAnchor プレハブを SharedPlayground オブジェクトの上にドラッグして子にします。</span><span class="sxs-lookup"><span data-stu-id="10950-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="10950-115">MixedRealityPlayspace 親オブジェクト、TableAnchor オブジェクトを展開し、Buttons オブジェクトも展開します。</span><span class="sxs-lookup"><span data-stu-id="10950-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="10950-117">次に、階層内で [ShareAzureAnchorButton] を選択し、[Inspector]\(インスペクター\) パネルに注目します。</span><span class="sxs-lookup"><span data-stu-id="10950-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="10950-118">下にスクロールして、次の図に示されているドロップダウン メニューまで移動し、[AnchorModuleScript] を選択して、[ShareAnchorNetwork()] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10950-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="10950-120">[GetAzureAnchorButton] (手順 4 を参照) を選択し、再び [Inspector]\(インスペクター\) パネルに注目します。</span><span class="sxs-lookup"><span data-stu-id="10950-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="10950-121">下にスクロールして、次の図に示されているドロップダウン メニューまで移動し、[AnchorModuleScript] を選択して、[ShareAnchorNetwork()] をクリックし、保存します。</span><span class="sxs-lookup"><span data-stu-id="10950-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="10950-123">手順 4 を繰り返して、StartAzureSession () 関数を StartAzureSessionButton にフックします。</span><span class="sxs-lookup"><span data-stu-id="10950-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="10950-124">手順 4 を繰り返して、CreateAzureAnchor () 関数を CreateAzureAnchorButton にフックし、TableAnchor オブジェクトが関数のパラメーター "Game Object" フィールドに割り当てられていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="10950-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="10950-125">「[シーンを Azure リソースに接続する](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource)」の手順に従って、Azure Spatial Anchors サービスの資格情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="10950-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="10950-126">共有モジュールをテストするには、[Start Azure ASA Session]\(Azure ASA セッションの開始\) ボタンをクリックして Azure Spatial Anchors セッションを開始し、次に、[Create Azure Anchor]\(Azure アンカーの作成\) ボタンをクリックして Azure アンカーを作成します。</span><span class="sxs-lookup"><span data-stu-id="10950-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="10950-127">Azure アンカーが作成されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="10950-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="10950-128">Azure アンカーが作成されたら、[Share Azure Anchor]\(Azure アンカーの共有\) ボタンをクリックして、作成した Azure アンカーを HoloLens から共有します。</span><span class="sxs-lookup"><span data-stu-id="10950-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="10950-129">別の HoloLens で共有 Azure アンカーを受け取るには、[Start Azure ASA Session]\(Azure ASA セッションの開始\) をクリックして、現在の ASA セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="10950-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="10950-130">[Get Azure Anchor]\(Azure アンカーの取得\) ボタンをクリックして、もう一方の HoloLens から共有 Azure アンカーを取得します。</span><span class="sxs-lookup"><span data-stu-id="10950-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="10950-131">結論</span><span class="sxs-lookup"><span data-stu-id="10950-131">Congratulations</span></span>

<span data-ttu-id="10950-132">このレッスンでは、Azure の強力で新しい Spatial Anchors を統合して、併置されたデバイスを共有エクスペリエンスに配置する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="10950-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="10950-133">これにより、共有モジュールも完了しました。</span><span class="sxs-lookup"><span data-stu-id="10950-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="10950-134">新しい Photon アカウントを設定し、Photon と PUN を新しい Unity アプリケーションに統合し、アバターと共有オブジェクトを構成し、最後に ASA を使用して複数の参加者を配置する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="10950-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>
