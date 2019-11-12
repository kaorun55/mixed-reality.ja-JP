---
title: Azure 空間アンカーチュートリアル-3. Azure 空間アンカーフィードバックの表示
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 9f57cb9874aade2d6b19d0c061fd83eb04b9ef11
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2019
ms.locfileid: "73914379"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="4a998-105">3. Azure 空間アンカーのフィードバックを表示する</span><span class="sxs-lookup"><span data-stu-id="4a998-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="4a998-106">このレッスンでは、Azure 空間アンカーを使用する場合のアンカー検出、イベント、および状態に関するフィードバックをユーザーに提供する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4a998-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="4a998-107">目標</span><span class="sxs-lookup"><span data-stu-id="4a998-107">Objectives</span></span>

* <span data-ttu-id="4a998-108">現在の ASA セッションに関する重要な情報を表示する UI パネルを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4a998-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="4a998-109">ASA SDK によってユーザーに提供されるフィードバック要素について理解し、調査する</span><span class="sxs-lookup"><span data-stu-id="4a998-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="4a998-110">手順</span><span class="sxs-lookup"><span data-stu-id="4a998-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="4a998-111">ASA フィードバック UI パネルを設定する</span><span class="sxs-lookup"><span data-stu-id="4a998-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="4a998-112">このレッスンでは、"SaveAnchorToDisk" と "" ボタンを使用していないので、両方のボタンを選択し、次に示すようにインスペクターパネルのチェックボックスをオフにして、これらのボタンを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="4a998-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="4a998-114">命令パネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="4a998-114">Create the instruction panel.</span></span> <span data-ttu-id="4a998-115">まず、[命令] ボタンを右クリックし、[3D オブジェクト] の上にマウスポインターを移動して、[textmeshpro-text] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4a998-115">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="4a998-117">シーン内の指示と一致するように、テキストのスケールと配置を調整します。</span><span class="sxs-lookup"><span data-stu-id="4a998-117">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="4a998-118">また、すべてのテキストの配置が中央揃えになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4a998-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="4a998-119">次の図に示すように、テキストエディターからサンプルテキストを削除します。</span><span class="sxs-lookup"><span data-stu-id="4a998-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="4a998-121">TextMeshPro オブジェクトの名前を「フィードバックパネル」に変更します。</span><span class="sxs-lookup"><span data-stu-id="4a998-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="4a998-123">ASA_feedback 階層で "フィードバックパネル" のテキストが選択されていることを確認し、[コンポーネントの追加] をクリックして、アンカーフィードバックスクリプトを検索し、表示されたらそれを選択して追加します。</span><span class="sxs-lookup"><span data-stu-id="4a998-123">Ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

6. <span data-ttu-id="4a998-125">次の図に示すように、ASA_Feedback 階層の "フィードバックパネル" テキストオブジェクトを、スクリプトの下の空のスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4a998-125">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="4a998-127">結論</span><span class="sxs-lookup"><span data-stu-id="4a998-127">Congratulations</span></span>

<span data-ttu-id="4a998-128">このレッスンでは、リアルタイムのフィードバックをユーザーに提供するために、Azure 空間アンカーエクスペリエンスの現在の状態を表示する UI パネルを作成する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="4a998-128">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>


