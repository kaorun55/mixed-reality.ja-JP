---
title: Azure 空間アンカーチュートリアル-3. Azure 空間アンカーフィードバックの表示
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 77d639a88d8b4c71dc5fbe1c78565c4c3f91d36c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438416"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="d718c-105">3. Azure 空間アンカーのフィードバックを表示する</span><span class="sxs-lookup"><span data-stu-id="d718c-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="d718c-106">このレッスンでは、Azure 空間アンカーを使用する場合のアンカー検出、イベント、および状態に関するフィードバックをユーザーに提供する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d718c-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="d718c-107">目標</span><span class="sxs-lookup"><span data-stu-id="d718c-107">Objectives</span></span>

* <span data-ttu-id="d718c-108">現在の ASA セッションに関する重要な情報を表示する UI パネルを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d718c-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="d718c-109">ASA SDK によってユーザーに提供されるフィードバック要素について理解し、調査する</span><span class="sxs-lookup"><span data-stu-id="d718c-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="d718c-110">手順</span><span class="sxs-lookup"><span data-stu-id="d718c-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="d718c-111">ASA フィードバック UI パネルを設定する</span><span class="sxs-lookup"><span data-stu-id="d718c-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="d718c-112">このレッスンでは、"SaveAnchorToDisk" と "" ボタンを使用していないので、両方のボタンを選択し、次に示すようにインスペクターパネルのチェックボックスをオフにして、これらのボタンを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="d718c-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="d718c-114">命令パネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d718c-114">Create the instruction panel.</span></span> <span data-ttu-id="d718c-115">まず、[命令] ボタンを右クリックし、[3D オブジェクト] の上にマウスポインターを移動して、[textmeshpro-text] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d718c-115">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="d718c-117">シーン内の指示と一致するように、テキストのスケールと配置を調整します。</span><span class="sxs-lookup"><span data-stu-id="d718c-117">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="d718c-118">また、すべてのテキストの配置が中央揃えになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d718c-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="d718c-119">次の図に示すように、テキストエディターからサンプルテキストを削除します。</span><span class="sxs-lookup"><span data-stu-id="d718c-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="d718c-121">TextMeshPro オブジェクトの名前を「フィードバックパネル」に変更します。</span><span class="sxs-lookup"><span data-stu-id="d718c-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="d718c-123">[プロジェクト] パネルで、[資産] を選択して右クリックし、[エクスプローラーで表示] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d718c-123">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="d718c-125">次のいくつかの手順で必要なファイルをダウンロードするには、[ここ](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="d718c-125">Click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="d718c-126">エクスプローラーが開いたら、Assets フォルダーを選択し、"ASAmodulesAssets" フォルダーを選択して、アンカーフィードバックスクリプトとアンカーモジュールスクリプトファイルをフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="d718c-126">Once Explorer opens, select the Assets folder, then the "ASAmodulesAssets" folder and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="d718c-128">注: 古いものを上書きするか古いままにするかを確認するポップアップメッセージが表示された場合は、[上書き] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d718c-128">note: if you get a pop-up message asking if you to overwrite the old or keep the old, select overwrite.</span></span>

7. <span data-ttu-id="d718c-129">Assets フォルダーに戻ります。</span><span class="sxs-lookup"><span data-stu-id="d718c-129">Return to the Assets folder.</span></span> <span data-ttu-id="d718c-130">次に、"AzureSpatialAnchorsPlugin" フォルダーにアクセスし、[例] フォルダーを選択して、最後に Scripts フォルダーを入力します。</span><span class="sxs-lookup"><span data-stu-id="d718c-130">Then, go into the "AzureSpatialAnchorsPlugin" folder, followed by the Examples folder and finally the Scripts folder.</span></span> <span data-ttu-id="d718c-131">次に、Azure 空間アンカーデモラッパーをそのフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="d718c-131">Then copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="d718c-133">ファイルがアップロードされたので、ASA_feedback 階層で "フィードバックパネル" というテキストが選択されていることを確認し、[コンポーネントの追加] をクリックしてアンカーフィードバックスクリプトを検索し、表示されたらそれを選択して追加します。</span><span class="sxs-lookup"><span data-stu-id="d718c-133">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="d718c-135">次の図に示すように、ASA_Feedback 階層の "フィードバックパネル" テキストオブジェクトを、スクリプトの下の空のスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d718c-135">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="d718c-137">結論</span><span class="sxs-lookup"><span data-stu-id="d718c-137">Congratulations</span></span>

<span data-ttu-id="d718c-138">このレッスンでは、リアルタイムのフィードバックをユーザーに提供するために、Azure 空間アンカーエクスペリエンスの現在の状態を表示する UI パネルを作成する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="d718c-138">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>


