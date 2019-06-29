---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465203"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="ed802-104">Azure の空間アンカーおよび共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="ed802-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="ed802-105">このレッスンでは、共有の経験に Azure 空間アンカー (ASA) を統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed802-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="ed802-106">ASA では、一般的な参照がある、物理環境があるすべての参加要素は、同じ物理的な場所にオブジェクトを参照してくださいにアンカー仮想体験する場合に併置されている複数のデバイスを許可します。</span><span class="sxs-lookup"><span data-stu-id="ed802-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="ed802-107">このレッスンを続行する前に、ASA 基本、Azure アカウントとリソースの作成と、共有のエクスペリエンスに統合できます ASA 前に必要な他の基本的なビルディング ブロックはカバー ASA ラーニング モジュールを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed802-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="ed802-108">目標:</span><span class="sxs-lookup"><span data-stu-id="ed802-108">Objectives:</span></span>

- <span data-ttu-id="ed802-109">ASA をマルチ デバイスの配置の共有エクスペリエンスに統合します。</span><span class="sxs-lookup"><span data-stu-id="ed802-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="ed802-110">ローカルの共有エクスペリエンスの観点で ASA のしくみの基礎を学習します。</span><span class="sxs-lookup"><span data-stu-id="ed802-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="ed802-111">手順</span><span class="sxs-lookup"><span data-stu-id="ed802-111">Instructions</span></span>

1. <span data-ttu-id="ed802-112">(コントロール + S) は、前のレッスンからプロジェクトを保存して、もう一度必要なときを見つけやすいように"HLSharedProjectMainPart5.unity"という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="ed802-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="ed802-113">MixedRealityPlayspace 親オブジェクトの下にある TableAnchor プレハブを選択し、それを削除します。</span><span class="sxs-lookup"><span data-stu-id="ed802-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  <span data-ttu-id="ed802-115">資産に移動して、プロジェクト ビューではリソース]-> [プレハブを -> し、子 SharedPlayground オブジェクト上に TableAnchor プレハブをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ed802-115">In the Project view go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="ed802-116">MixedRealityPlayspace の親オブジェクト、TableAnchor のオブジェクトを展開しもボタン オブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="ed802-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="ed802-118">今すぐ階層では、ShareAzureAnchorButton を選択し、Inaspector パネルに、注意を移動します。</span><span class="sxs-lookup"><span data-stu-id="ed802-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="ed802-119">、次の図に示すように、ドロップ ダウン メニューまで下へスクロールし、AnchorModuleScript ShareAnchorNetework() をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed802-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="ed802-121">GetAzureAnchorButton を選択します (手順 4 を参照)、し、[Inspector] パネルに、注意を移動します。</span><span class="sxs-lookup"><span data-stu-id="ed802-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="ed802-122">、次の図に示すように、ドロップ ダウン メニューまで下へスクロール選択 AnchorModuleScript、GetSharedAnchorNetwork()、 をクリックし、保存します。</span><span class="sxs-lookup"><span data-stu-id="ed802-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="ed802-124">結論</span><span class="sxs-lookup"><span data-stu-id="ed802-124">Congratulations</span></span>

<span data-ttu-id="ed802-125">このレッスンでは、Azure の強力な新しい空間アンカー共有エクスペリエンスに併置されているデバイスに合わせてを統合する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="ed802-125">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="ed802-126">このレッスンでは、共有モジュールも終了です。</span><span class="sxs-lookup"><span data-stu-id="ed802-126">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="ed802-127">アバターと共有オブジェクトを構成して、最後に ASA を使用して複数の参加要素のアラインメントは、新しい Photon アカウントを設定する、Photon とだじゃれを新しい Unity アプリケーションに統合する方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="ed802-127">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

