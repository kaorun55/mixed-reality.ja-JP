---
title: Azure 空間アンカーチュートリアル-3. Azure 空間アンカーフィードバックの表示
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 45a71cada97dff4a2fb32f2eaf7700816f2e0d42
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702030"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="15165-105">3.Azure 空間アンカーフィードバックの表示</span><span class="sxs-lookup"><span data-stu-id="15165-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="15165-106">このレッスンでは、Azure 空間アンカーを使用するときに、アンカー検出、イベント、および状態に関するフィードバックをユーザーに提供する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="15165-106">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="15165-107">目的</span><span class="sxs-lookup"><span data-stu-id="15165-107">Objectives</span></span>

* <span data-ttu-id="15165-108">現在の ASA セッションに関する重要な情報を表示する UI パネルを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="15165-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="15165-109">ASA SDK によってユーザーに提供されるフィードバック要素について理解し、調査する</span><span class="sxs-lookup"><span data-stu-id="15165-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="15165-110">手順</span><span class="sxs-lookup"><span data-stu-id="15165-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="15165-111">ASA フィードバック UI パネルを設定する</span><span class="sxs-lookup"><span data-stu-id="15165-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="15165-112">このレッスンでは、"SaveAnchorToDisk" と "" ボタンを使用していないので、これらのボタンを非表示にするには、両方のボタンを選択し、[インスペクター] パネルのチェックボックスをオフにします (次の図を参照)。</span><span class="sxs-lookup"><span data-stu-id="15165-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="15165-114">次に、命令パネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="15165-114">Next, create the instruction panel.</span></span> <span data-ttu-id="15165-115">まず、[命令] ボタンを右クリックし、[3D オブジェクト] の上にマウスポインターを移動して、[textmeshpro-text] を選択します。</span><span class="sxs-lookup"><span data-stu-id="15165-115">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="15165-117">シーンの指示と一致するように、スケールとテキストの配置を調整します。</span><span class="sxs-lookup"><span data-stu-id="15165-117">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="15165-118">また、すべてのテキストの配置が中央揃えになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="15165-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="15165-119">次の図に示すように、テキストエディターからサンプルテキストを削除します。</span><span class="sxs-lookup"><span data-stu-id="15165-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="15165-121">TextMeshPro オブジェクトの名前を「フィードバックパネル」に変更します。</span><span class="sxs-lookup"><span data-stu-id="15165-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="15165-123">[プロジェクト] パネルで、[資産] を選択して右クリックし、[エクスプローラーで表示] を選択します。</span><span class="sxs-lookup"><span data-stu-id="15165-123">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="15165-125">ここで、[ここ](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)をクリックして、次のいくつかの手順で必要なファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="15165-125">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="15165-126">エクスプローラーが開いたら、assets フォルダー、"ASAmodulesAssets" フォルダーの順に選択し、アンカーフィードバックスクリプトとアンカーモジュールスクリプトファイルをフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="15165-126">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="15165-128">注: 古いものを上書きするか、古いものを保持するかを確認するポップアップが表示された場合は、[上書き] を選択してください。</span><span class="sxs-lookup"><span data-stu-id="15165-128">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="15165-129">次に、Assets フォルダーに戻ります。</span><span class="sxs-lookup"><span data-stu-id="15165-129">Now return to the Assets folder.</span></span> <span data-ttu-id="15165-130">次に、"AzureSpatialAnchorsPlugin" フォルダーにアクセスし、[例] フォルダーをクリックし、最後に scripts フォルダーを選択して、Azure 空間アンカーデモラッパーをそのフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="15165-130">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="15165-132">ファイルがアップロードされたので、ASA_feedback 階層で "フィードバックパネル" というテキストが選択されていることを確認し、[コンポーネントの追加] をクリックしてアンカーフィードバックスクリプトを検索し、表示されたらそれを選択して追加します。</span><span class="sxs-lookup"><span data-stu-id="15165-132">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="15165-134">次の図に示すように、ASA_Feedback 階層の "フィードバックパネル" テキストオブジェクトを、スクリプトの下の空のスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="15165-134">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="15165-136">結論</span><span class="sxs-lookup"><span data-stu-id="15165-136">Congratulations</span></span>

<span data-ttu-id="15165-137">このレッスンでは、ユーザーにリアルタイムのフィードバックを提供するための Azure 空間アンカーエクスペリエンスの現在の状態を表示する UI パネルを作成する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="15165-137">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


