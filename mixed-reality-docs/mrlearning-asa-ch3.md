---
title: Azure Spatial Anchors チュートリアル - 3. Azure Spatial Anchors のフィードバックの表示
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 62ce1151837a345dea1bea4a8bea275cc851b9bd
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866902"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="e648a-105">3.Azure Spatial Anchors のフィードバックの表示</span><span class="sxs-lookup"><span data-stu-id="e648a-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="e648a-106">このチュートリアルでは、Azure Spatial Anchors (ASA) を使用する場合のアンカーの検出、イベント、および状態に関するフィードバックをユーザーに提供する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e648a-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="e648a-107">目標</span><span class="sxs-lookup"><span data-stu-id="e648a-107">Objectives</span></span>

* <span data-ttu-id="e648a-108">現在の ASA セッションに関する重要な情報を表示する UI パネルを設定する方法を理解する</span><span class="sxs-lookup"><span data-stu-id="e648a-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="e648a-109">ASA SDK によってユーザーに提供されるフィードバック要素を理解および確認する</span><span class="sxs-lookup"><span data-stu-id="e648a-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="e648a-110">ASA フィードバック UI パネルの設定</span><span class="sxs-lookup"><span data-stu-id="e648a-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="e648a-111">[Hierarchy]\(階層\) ウィンドウで、 **[Instructions]\(指示\)**  >  **[TextContent]** オブジェクトを右クリックし、 **[3D Object]\(3D オブジェクト\)**  >  **[Text - TextMeshPro]\(テキスト - TextMeshPro\)** を選択して、[Instructions]\(指示\) > [TextContent] オブジェクトの子として TextMeshPro テキスト オブジェクトを作成し、適切な名前 (**Feedback** など) を付けます。</span><span class="sxs-lookup"><span data-stu-id="e648a-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="e648a-113">シーンを簡単に操作できるようにするには、ParentAnchor オブジェクトの左側にある目のアイコンをクリックして、そのオブジェクトの<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">シーンの可視性</a>をオフに設定します。</span><span class="sxs-lookup"><span data-stu-id="e648a-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="e648a-114">これにより、ゲーム中の可視性を変更することなく、[Scene]\(シーン\) ウィンドウ内のオブジェクトが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="e648a-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="e648a-115">**Feedback** オブジェクトを引き続き選択した状態で、[Inspector]\(インスペクター\) ウィンドウでその位置とサイズを変更して、指示テキストの下に配置されるようにします。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e648a-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="e648a-116">[Rect Transform]\(四角形の変換\) の **[Pos Y]\(位置 Y\)** を -0.24 に変更する</span><span class="sxs-lookup"><span data-stu-id="e648a-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="e648a-117">[Rect Transform]\(四角形の変換\) の **[幅]** を 0.555 に変更する</span><span class="sxs-lookup"><span data-stu-id="e648a-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="e648a-118">[Rect Transform]\(四角形の変換\) の **[高さ]** を 0.1 に変更する</span><span class="sxs-lookup"><span data-stu-id="e648a-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="e648a-119">次に、テキスト領域内にテキストがうまく適合するように、フォントのプロパティを選択します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e648a-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="e648a-120">Text Mesh Pro (Script) の **[Font Style]\(フォント スタイル\)** を太字に変更する</span><span class="sxs-lookup"><span data-stu-id="e648a-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="e648a-121">Text Mesh Pro (Script) の **[Font Size]\(フォント サイズ\)** を 0.17 に変更する</span><span class="sxs-lookup"><span data-stu-id="e648a-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="e648a-122">Text Mesh Pro (Script) の **[Alignment]\(配置\)** を中央揃え中央に変更する</span><span class="sxs-lookup"><span data-stu-id="e648a-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="e648a-124">**Feedback** オブジェクトを引き続き選択した状態で、[Inspector]\(インスペクター\) ウィンドウの **[Add Component]\(コンポーネントの追加\)** ボタンを使用して **Anchor Feedback Script (Script)** コンポーネントを Feedback オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="e648a-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="e648a-126">**Feedback** オブジェクト自体を **Anchor Feedback Script (Script)** コンポーネントの **[Feedback Text]\(フィードバック テキスト\)** フィールドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e648a-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="e648a-128">結論</span><span class="sxs-lookup"><span data-stu-id="e648a-128">Congratulations</span></span>

<span data-ttu-id="e648a-129">このチュートリアルでは、ユーザーにリアルタイムのフィードバックを提供するために、Azure Spatial Anchors エクスペリエンスの現在の状態を表示する UI パネルを作成する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="e648a-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>

[<span data-ttu-id="e648a-130">次のレッスン:4.Android と iOS 用の Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e648a-130">Next Lesson: 4. Azure Spatial Anchors for Android and iOS</span></span>](mrlearning-asa-ch4.md)
