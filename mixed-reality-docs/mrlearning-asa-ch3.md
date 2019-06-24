---
title: MR Learning ASA モジュール HoloLens 2 での Azure 空間アンカー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327369"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="92275-104">Azure の空間アンカーからのフィードバックを表示します。</span><span class="sxs-lookup"><span data-stu-id="92275-104">Displaying Azure Spatial Anchor Feedback</span></span>

<span data-ttu-id="92275-105">このレッスンでは、Azure 空間アンカーを使用する場合、アンカーの検出、イベント、およびステータスに関するフィードバックをユーザーに提供する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="92275-105">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="92275-106">目標:</span><span class="sxs-lookup"><span data-stu-id="92275-106">Objectives:</span></span>

* <span data-ttu-id="92275-107">ASA の現在のセッションに関する重要な情報を表示する UI パネルを設定する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="92275-107">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="92275-108">理解し、調査をユーザーに、ASA SDK が利用できるようにするフィードバック要素</span><span class="sxs-lookup"><span data-stu-id="92275-108">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

  

## <a name="instructions"></a><span data-ttu-id="92275-109">手順</span><span class="sxs-lookup"><span data-stu-id="92275-109">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="92275-110">ASA フィードバック UI パネルを設定します。</span><span class="sxs-lookup"><span data-stu-id="92275-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="92275-111">このレッスンでは、"SaveAnchorToDisk"を使用していないことと"ShareAnchor"ボタンは、そのため両方のボタンを選択し、(下図参照) とインスペクター パネル内のチェック ボックスをオフにこれらのボタンを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="92275-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="92275-113">次に、命令のパネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="92275-113">Next, create the instruction panel.</span></span> <span data-ttu-id="92275-114">"Instruction"ボタンを右クリックして開始し、"3 D Object"と「textmeshpro-テキストを選択します」合わせ、</span><span class="sxs-lookup"><span data-stu-id="92275-114">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. <span data-ttu-id="92275-116">スケールと手順については、シーン内で一致するよう、テキストの配置を調整します。</span><span class="sxs-lookup"><span data-stu-id="92275-116">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="92275-117">また、すべてのテキストの配置の中心を確認します。</span><span class="sxs-lookup"><span data-stu-id="92275-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="92275-118">下の画像に示すように、テキスト エディターからサンプル テキストを削除します。</span><span class="sxs-lookup"><span data-stu-id="92275-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="92275-120">TextMeshPro オブジェクトの名前を"FeedbackPanel。"に変更します。</span><span class="sxs-lookup"><span data-stu-id="92275-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. <span data-ttu-id="92275-122">プロジェクト パネルで、アセット を選択し、右クリックし、「エクスプ ローラーで表示します。」を選択します。</span><span class="sxs-lookup"><span data-stu-id="92275-122">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="92275-124">をクリックして[ここ](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)ファイルをダウンロードするために必要な次のいくつかの手順。</span><span class="sxs-lookup"><span data-stu-id="92275-124">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="92275-125">エクスプ ローラーが開いたら、assets フォルダー、"ASAmodulesAssets"フォルダーを選択し、アンカーのフィードバック スクリプトとアンカー モジュール スクリプト ファイルをフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="92275-125">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="92275-127">注: 古いを上書きするか、古いを保持する場合を確認する上書きを選択するかをたずねるポップアップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="92275-127">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="92275-128">Assets フォルダーに戻るようになりました。</span><span class="sxs-lookup"><span data-stu-id="92275-128">Now return to the Assets folder.</span></span> <span data-ttu-id="92275-129">次に、"AzureSpatialAnchorsPlugin"フォルダー、し、フォルダー、および最後に、scripts フォルダーに移動し、Azure 空間アンカー デモのラッパーをそのフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="92275-129">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="92275-131">ファイルをアップロードすると、これでは、ASA_feedback 階層で、"feedbackpanel"テキストを選択することを確認し、"コンポーネントの追加 をクリックします。 検索し、選択することが表示されたら、アンカーのフィードバック スクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="92275-131">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="92275-133">次の図に示すように、スクリプトの下に空のスロットに ASA_Feedback 階層から"feedbackPanel"テキスト オブジェクトをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="92275-133">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a><span data-ttu-id="92275-135">結論</span><span class="sxs-lookup"><span data-stu-id="92275-135">Congratulations</span></span>

<span data-ttu-id="92275-136">このレッスンでは、ユーザーをリアルタイムのフィードバックを提供するための Azure 空間アンカー エクスペリエンスの現在の状態を表示する UI パネルを作成する方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="92275-136">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


