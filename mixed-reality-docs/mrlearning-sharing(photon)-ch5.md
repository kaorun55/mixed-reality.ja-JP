---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 941bdc64ed614d5ce71f58f05585d0dfc86c3bb7
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415933"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="8bb36-104">Azure の空間アンカーおよび共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="8bb36-104">Azure Spatial Anchors and Shared Experiences</span></span>

<span data-ttu-id="8bb36-105">このレッスンでは、Azure 空間アンカー (ASA) を共有のエクスペリエンスに統合する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="8bb36-105">In this lesson, we will learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="8bb36-106">ASA では、共通理解があるすべての参加要素が同じ物理的な場所にオブジェクトを表示するように仮想を固定するには、物理環境が発生した場合に併置されている複数のデバイスを許可します。</span><span class="sxs-lookup"><span data-stu-id="8bb36-106">ASA allows multiple co-located devices to have a common understanding if their physical environment in order to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="8bb36-107">このレッスンを続行する前に、ASA の基礎、Azure アカウントとリソースの作成と、共有のエクスペリエンスに統合できます ASA 前に必要な他の基本的なビルディング ブロックについては説明、ASA ラーニング モジュールを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8bb36-107">Before proceeding with this lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="8bb36-108">目標:</span><span class="sxs-lookup"><span data-stu-id="8bb36-108">Objectives:</span></span>

- <span data-ttu-id="8bb36-109">ASA をマルチ デバイスの配置の共有エクスペリエンスに統合します。</span><span class="sxs-lookup"><span data-stu-id="8bb36-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="8bb36-110">ローカルの共有エクスペリエンスの観点で ASA のしくみの基礎を学習します。</span><span class="sxs-lookup"><span data-stu-id="8bb36-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="8bb36-111">手順</span><span class="sxs-lookup"><span data-stu-id="8bb36-111">Instructions</span></span>

1. <span data-ttu-id="8bb36-112">(コントロール + S) は、前のレッスンからプロジェクトを保存して、もう一度必要なときを見つけやすいように"HLSharedProjectMainPart5.unity"という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="8bb36-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="8bb36-113">"MixedRealityPlayspace"の親オブジェクトの下にある TableAnchor プレハブを選択し、それを削除します。</span><span class="sxs-lookup"><span data-stu-id="8bb36-113">Select the TableAnchor prefab underneath  the "MixedRealityPlayspace" parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  <span data-ttu-id="8bb36-115">プロジェクト ビューでは、資産へ移動 > リソース > プレハブとドラッグ、TableAnchor prefab 子 SharedPlayground オブジェクト上にします。</span><span class="sxs-lookup"><span data-stu-id="8bb36-115">In the Project view go to Assets > Resources > Prefabs and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="8bb36-116">展開し、"MixedRealityPlayspace"の親オブジェクトでは、"TableAnchor"オブジェクトを展開しも「ボタン」のオブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="8bb36-116">Expand the "MixedRealityPlayspace" parent object, then the "TableAnchor" object, and expand the "buttons" object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="8bb36-118">今すぐ階層では、"ShareAzureAnchorButton"を選択し、inspector パネルに、注意を移動します。</span><span class="sxs-lookup"><span data-stu-id="8bb36-118">Now in the hierarchy, select the "ShareAzureAnchorButton" and move your attention to the inspector panel.</span></span> <span data-ttu-id="8bb36-119">、次の図に示すように、ドロップダウン メニューまでスクロールし、"AnchorModuleScript"を選択し、"ShareAnchorNetework()。"をクリックしてください</span><span class="sxs-lookup"><span data-stu-id="8bb36-119">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "ShareAnchorNetework()."</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="8bb36-121">手順 4 と同じように"GetAzureAnchorButton"を選択し、inspector パネルに、注意を移動します。</span><span class="sxs-lookup"><span data-stu-id="8bb36-121">Much like step 4, select the "GetAzureAnchorButton" and move your attention back to the inspector panel.</span></span> <span data-ttu-id="8bb36-122">、次の図に示すように、ドロップダウン メニューまでスクロールし、"AnchorModuleScript"を選択し、"GetSharedAnchorNetwork()。"をクリックしてください</span><span class="sxs-lookup"><span data-stu-id="8bb36-122">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "GetSharedAnchorNetwork()."</span></span> <span data-ttu-id="8bb36-123">保存します。</span><span class="sxs-lookup"><span data-stu-id="8bb36-123">Then save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="8bb36-125">結論</span><span class="sxs-lookup"><span data-stu-id="8bb36-125">Congratulations</span></span>

<span data-ttu-id="8bb36-126">このレッスンでは、Azure の強力な新しい空間アンカー共有エクスペリエンスに併置されているデバイスに合わせてを統合する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="8bb36-126">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="8bb36-127">このレッスンでは、共有モジュールも終了です。</span><span class="sxs-lookup"><span data-stu-id="8bb36-127">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="8bb36-128">アバターと共有オブジェクトを構成して、最後に ASA を使用して複数の参加要素のアラインメントは、新しい Photon アカウントを設定する、Photon とだじゃれを新しい Unity アプリケーションに統合する方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="8bb36-128">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

