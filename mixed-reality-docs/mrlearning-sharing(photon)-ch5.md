---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 9f4a0c0cc37ab097a60c44891d56fa65f6032418
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327767"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="6b942-104">Azure の空間アンカーおよび共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="6b942-104">Azure Spatial Anchors and Shared Experiences</span></span>

<span data-ttu-id="6b942-105">このレッスンでは、Azure 空間アンカー (ASA) を共有のエクスペリエンスに統合する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="6b942-105">In this lesson, we will learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="6b942-106">ASA では、共通理解があるすべての参加要素が同じ物理的な場所にオブジェクトを表示するように仮想を固定するには、物理環境が発生した場合に併置されている複数のデバイスを許可します。</span><span class="sxs-lookup"><span data-stu-id="6b942-106">ASA allows multiple co-located devices to have a common understanding if their physical environment in order to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="6b942-107">このレッスンを続行する前に、ASA の基礎、Azure アカウントとリソースの作成と、共有のエクスペリエンスに統合できます ASA 前に必要な他の基本的なビルディング ブロックについては説明、ASA ラーニング モジュールを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b942-107">Before proceeding with this lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="6b942-108">目標:</span><span class="sxs-lookup"><span data-stu-id="6b942-108">Objectives:</span></span>

- <span data-ttu-id="6b942-109">ASA をマルチ デバイスの配置の共有エクスペリエンスに統合します。</span><span class="sxs-lookup"><span data-stu-id="6b942-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="6b942-110">ローカルの共有エクスペリエンスの観点で ASA のしくみの基礎を学習します。</span><span class="sxs-lookup"><span data-stu-id="6b942-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="6b942-111">手順</span><span class="sxs-lookup"><span data-stu-id="6b942-111">Instructions</span></span>

1. <span data-ttu-id="6b942-112">(コントロール + S) は、前のレッスンからプロジェクトを保存して、もう一度必要なときを見つけやすいように"HLSharedProjectMainPart5.unity"という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="6b942-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="6b942-113">"MixedRealityPlayspace"の親オブジェクトの下にある TableAnchor プレハブを選択し、それを削除します。</span><span class="sxs-lookup"><span data-stu-id="6b942-113">Select the TableAnchor prefab underneath  the "MixedRealityPlayspace" parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3. <span data-ttu-id="6b942-115">前のレッスン、一部のようにインポートすれば、新しいカスタム パッケージを[ここです。](placeholderlink)</span><span class="sxs-lookup"><span data-stu-id="6b942-115">Just like some of the previous lessons, import a new custom package that you can get [here.](placeholderlink)</span></span>

![Module3Chapter5step3im](images/module3chapter5step3im.PNG)

4. <span data-ttu-id="6b942-117">インポートされたら、[プロジェクト] パネルで「プレハブ」フォルダーから (インポート前の手順で unity パッケージ) から新しく更新されたテーブルのアンカーを取得し、親オブジェクトの"MixedRealityPlayspace"にドロップ</span><span class="sxs-lookup"><span data-stu-id="6b942-117">Once it's imported, grab the newly updated table anchor (from the unity package imported in the previous step) from the "prefabs" folder in the project panel and drop it into the parent object "MixedRealityPlayspace."</span></span>

![Module3hapter5step4im](images/module3chapter5step4im.PNG)

5. <span data-ttu-id="6b942-119">展開し、"MixedRealityPlayspace"の親オブジェクトでは、"TableAnchor"オブジェクトを展開しも「ボタン」のオブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="6b942-119">Expand the "MixedRealityPlayspace" parent object, then the "TableAnchor" object, and expand the "buttons" object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

6. <span data-ttu-id="6b942-121">今すぐ階層では、"ShareAzureAnchorButton"を選択し、inspector パネルに、注意を移動します。</span><span class="sxs-lookup"><span data-stu-id="6b942-121">Now in the hierarchy, select the "ShareAzureAnchorButton" and move your attention to the inspector panel.</span></span> <span data-ttu-id="6b942-122">、次の図に示すように、ドロップダウン メニューまでスクロールし、"AnchorModuleScript"を選択し、"ShareAnchorNetework()。"をクリックしてください</span><span class="sxs-lookup"><span data-stu-id="6b942-122">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "ShareAnchorNetework()."</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

7. <span data-ttu-id="6b942-124">手順 6 と同様に"GetAzureAnchorButton"を選択し、[inspector] パネルに、注意します。</span><span class="sxs-lookup"><span data-stu-id="6b942-124">Much like step 6, select the "GetAzureAnchorButton" and move your attention back to the inspector panel.</span></span> <span data-ttu-id="6b942-125">、次の図に示すように、ドロップダウン メニューまでスクロールし、"AnchorModuleScript"を選択し、"GetSharedAnchorNetwork()。"をクリックしてください</span><span class="sxs-lookup"><span data-stu-id="6b942-125">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "GetSharedAnchorNetwork()."</span></span> <span data-ttu-id="6b942-126">保存します。</span><span class="sxs-lookup"><span data-stu-id="6b942-126">Then save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="6b942-128">結論</span><span class="sxs-lookup"><span data-stu-id="6b942-128">Congratulations</span></span>

<span data-ttu-id="6b942-129">このレッスンでは、Azure の強力な新しい空間アンカー共有エクスペリエンスに併置されているデバイスに合わせてを統合する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="6b942-129">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="6b942-130">このレッスンでは、共有モジュールも終了です。</span><span class="sxs-lookup"><span data-stu-id="6b942-130">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="6b942-131">アバターと共有オブジェクトを構成して、最後に ASA を使用して複数の参加要素のアラインメントは、新しい Photon アカウントを設定する、Photon とだじゃれを新しい Unity アプリケーションに統合する方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="6b942-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

