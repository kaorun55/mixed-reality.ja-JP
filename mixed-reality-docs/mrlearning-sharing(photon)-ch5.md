---
title: 複数ユーザー機能のチュートリアル-5. Azure 空間アンカーを共有エクスペリエンスに統合する
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: b83c7ac39d522fc2b799591fa02608d5fc5cc930
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437569"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="b0631-105">5. Azure 空間アンカーを共有エクスペリエンスに統合する</span><span class="sxs-lookup"><span data-stu-id="b0631-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="b0631-106">このレッスンでは、Azure 空間アンカー (ASA) を共有エクスペリエンスに統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b0631-106">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="b0631-107">ASA を使用すると、複数の併置されたデバイスは、物理環境で仮想エクスペリエンスを固定して、すべての参加者が同じ物理的な場所にオブジェクトを表示するようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="b0631-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="b0631-108">このレッスンに進む前に、asa learning モジュールを完成させる必要があります。 asa の基本、Azure アカウントとリソースの作成、および asa を共有エクスペリエンスに統合する前に必要なその他の基本的なビルディングブロックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b0631-108">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="b0631-109">事項</span><span class="sxs-lookup"><span data-stu-id="b0631-109">Objectives:</span></span>

- <span data-ttu-id="b0631-110">ASA を複数デバイスのアラインメントの共有エクスペリエンスに統合します。</span><span class="sxs-lookup"><span data-stu-id="b0631-110">Integrate ASA into a shared experience for multi-device alignment.</span></span>
- <span data-ttu-id="b0631-111">ASA がローカル共有エクスペリエンスのコンテキストでどのように機能するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b0631-111">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0631-112">手順</span><span class="sxs-lookup"><span data-stu-id="b0631-112">Instructions</span></span>

1. <span data-ttu-id="b0631-113">前のレッスン (コントロール + S) からプロジェクトを保存し、必要なときに簡単に見つけられるように "HLSharedProjectMainPart5" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="b0631-113">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="b0631-114">MixedRealityPlayspace 親オブジェクトの下にある TableAnchor prefab を選択し、削除します。</span><span class="sxs-lookup"><span data-stu-id="b0631-114">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  <span data-ttu-id="b0631-116">[プロジェクト] ビューで、[資産-> Resources-> Prefabs] に移動し、SharedPlayground オブジェクトの上に TableAnchor prefab をドラッグして子にします。</span><span class="sxs-lookup"><span data-stu-id="b0631-116">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="b0631-117">MixedRealityPlayspace 親オブジェクト TableAnchor オブジェクトを展開し、[ボタン] オブジェクトも展開します。</span><span class="sxs-lookup"><span data-stu-id="b0631-117">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="b0631-119">ここで、階層内で [ShareAzureAnchorButton] を選択し、注意を Inaspector パネルに移動します。</span><span class="sxs-lookup"><span data-stu-id="b0631-119">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="b0631-120">下の画像に表示されているドロップダウンメニューまで下にスクロールし、[AnchorModuleScript] を選択して、[ShareAnchorNetework ()] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0631-120">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="b0631-122">[GetAzureAnchorButton] (手順4を参照) を選択して、注意をインスペクターパネルに移動します。</span><span class="sxs-lookup"><span data-stu-id="b0631-122">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="b0631-123">下の画像に表示されているドロップダウンメニューまで下にスクロールし、[AnchorModuleScript] を選択し、[GetSharedAnchorNetwork ()] をクリックして保存します。</span><span class="sxs-lookup"><span data-stu-id="b0631-123">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="b0631-125">共有モジュールをテストするには、[Azure ASA セッションの開始] ボタンをクリックして azure 空間アンカーセッションを開始し、[Azure アンカーの作成] ボタンをクリックして azure アンカーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b0631-125">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="b0631-126">Azure アンカーが作成されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="b0631-126">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="b0631-127">Azure アンカーが作成されたら、[Azure アンカーを共有する] ボタンをクリックして、作成した azure アンカーを HoloLens から共有します。</span><span class="sxs-lookup"><span data-stu-id="b0631-127">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

7. <span data-ttu-id="b0631-128">別の HoloLens で共有 azure アンカーを受信するには、[Azure ASA セッションを開始します] をクリックして開始し、現在の ASA セッションにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="b0631-128">To recieve the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

8. <span data-ttu-id="b0631-129">[Get Azure Anchor] \ (Azure アンカーの取得 \) ボタンをクリックして、他の HoloLens から共有 azure アンカーを取得します。</span><span class="sxs-lookup"><span data-stu-id="b0631-129">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

   > <span data-ttu-id="b0631-130">注: [デバッグ] ウィンドウには、個々のボタンに対応するアクションの詳細がすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0631-130">Note: All details of the corresponding actions on the individual buttons will be displayed in the debug window.</span></span>

## <a name="congratulations"></a><span data-ttu-id="b0631-131">結論</span><span class="sxs-lookup"><span data-stu-id="b0631-131">Congratulations</span></span>

<span data-ttu-id="b0631-132">このレッスンでは、Azure の強力な新しい空間アンカーを統合して、共有された環境に併置されたデバイスを配置する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="b0631-132">In this lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="b0631-133">これにより、共有モジュールも終了します。</span><span class="sxs-lookup"><span data-stu-id="b0631-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="b0631-134">新しい Photon アカウントを設定し、Photon とさしあたっを新しい Unity アプリケーションに統合し、アバターと共有オブジェクトを構成し、最後に ASA を使用して複数の参加者を配置する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="b0631-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span> 

