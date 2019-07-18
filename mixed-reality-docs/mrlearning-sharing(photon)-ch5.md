---
title: HoloLens 2 用 MR Learning 共有モジュール
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 1ae880208e79e2e045bd5e7298db260b7f0b2232
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293627"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="4e757-104">Azure 空間アンカーと共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="4e757-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="4e757-105">このレッスンでは、Azure 空間アンカー (ASA) を共有エクスペリエンスに統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4e757-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="4e757-106">ASA を使用すると、複数の併置されたデバイスは、物理環境で仮想エクスペリエンスを固定して、すべての参加者が同じ物理的な場所にオブジェクトを表示するようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="4e757-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="4e757-107">このレッスンに進む前に、asa learning モジュールを完成させる必要があります。 asa の基本、Azure アカウントとリソースの作成、および asa を共有エクスペリエンスに統合する前に必要なその他の基本的なビルディングブロックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4e757-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="4e757-108">事項</span><span class="sxs-lookup"><span data-stu-id="4e757-108">Objectives:</span></span>

- <span data-ttu-id="4e757-109">ASA を複数デバイスのアラインメントの共有エクスペリエンスに統合します。</span><span class="sxs-lookup"><span data-stu-id="4e757-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
- <span data-ttu-id="4e757-110">ASA がローカル共有エクスペリエンスのコンテキストでどのように機能するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4e757-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

### <a name="instructions"></a><span data-ttu-id="4e757-111">手順</span><span class="sxs-lookup"><span data-stu-id="4e757-111">Instructions</span></span>

1. <span data-ttu-id="4e757-112">前のレッスン (コントロール + S) からプロジェクトを保存し、必要なときに簡単に見つけられるように "HLSharedProjectMainPart5" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="4e757-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="4e757-113">MixedRealityPlayspace 親オブジェクトの下にある TableAnchor prefab を選択し、削除します。</span><span class="sxs-lookup"><span data-stu-id="4e757-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  <span data-ttu-id="4e757-115">[プロジェクト] ビューで、[資産-> Resources-> Prefabs] に移動し、SharedPlayground オブジェクトの上に TableAnchor prefab をドラッグして子にします。</span><span class="sxs-lookup"><span data-stu-id="4e757-115">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="4e757-116">MixedRealityPlayspace 親オブジェクト TableAnchor オブジェクトを展開し、[ボタン] オブジェクトも展開します。</span><span class="sxs-lookup"><span data-stu-id="4e757-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="4e757-118">ここで、階層内で [ShareAzureAnchorButton] を選択し、注意を Inaspector パネルに移動します。</span><span class="sxs-lookup"><span data-stu-id="4e757-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="4e757-119">下の画像に表示されているドロップダウンメニューまで下にスクロールし、[AnchorModuleScript] を選択して、[ShareAnchorNetework ()] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e757-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="4e757-121">[GetAzureAnchorButton] (手順4を参照) を選択し、[インスペクター] パネルに注意を移動します。</span><span class="sxs-lookup"><span data-stu-id="4e757-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="4e757-122">下の画像に表示されているドロップダウンメニューまで下にスクロールし、[AnchorModuleScript] を選択し、[GetSharedAnchorNetwork ()] をクリックして保存します。</span><span class="sxs-lookup"><span data-stu-id="4e757-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="4e757-124">共有モジュールをテストするには、[Azure ASA セッションの開始] ボタンをクリックして azure 空間アンカーセッションを開始し、[Azure アンカーの作成] ボタンをクリックして azure アンカーを作成します。 azure アンカーが作成されるまでしばらく待ちます。</span><span class="sxs-lookup"><span data-stu-id="4e757-124">To test the sharing module, click on the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button and wait for sometime for the azure anchor to get created.</span></span> <span data-ttu-id="4e757-125">Azure アンカーが作成されたら、[Azure Anchor を共有する] ボタンをクリックして、作成した azure アンカーを HoloLens から共有します。</span><span class="sxs-lookup"><span data-stu-id="4e757-125">Once the azure anchor is created then click on the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

7. <span data-ttu-id="4e757-126">別の HoloLens で共有 azure アンカーを受信するには、[Azure ASA セッションの開始] をクリックして、現在の ASA セッションを開始し、[Azure アンカーの取得] ボタンをクリックして、他の HoloLens から共有 azure アンカーを取得します。</span><span class="sxs-lookup"><span data-stu-id="4e757-126">To recieve the shared azure anchor in another HoloLens, click on the "Start Azure ASA Session" to start and get in to the current ASA session and click on "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

   > <span data-ttu-id="4e757-127">注:[デバッグ] ウィンドウには、個々のボタンに対応するアクションの詳細がすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e757-127">Note: All details of the corresponding actions on the individual buttons will be displayed in the debug window.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4e757-128">結論</span><span class="sxs-lookup"><span data-stu-id="4e757-128">Congratulations</span></span>

<span data-ttu-id="4e757-129">このレッスンでは、Azure の強力な新しい空間アンカーを統合して、共有された環境に併置されたデバイスを配置する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="4e757-129">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="4e757-130">このレッスンでは、共有モジュールについても説明します。</span><span class="sxs-lookup"><span data-stu-id="4e757-130">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="4e757-131">新しい Photon アカウントを設定し、Photon とさしあたっを新しい Unity アプリケーションに統合し、アバターと共有オブジェクトを構成し、最後に ASA を使用して複数の参加要素を整列する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="4e757-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

