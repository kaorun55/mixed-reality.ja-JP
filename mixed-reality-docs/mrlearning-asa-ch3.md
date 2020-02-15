---
title: Azure 空間アンカーチュートリアル-3. Azure 空間アンカーフィードバックの表示
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: f4f609a71b05a52e8761e282763a540b42e9f7f5
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250701"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="403a9-105">3. Azure 空間アンカーのフィードバックを表示する</span><span class="sxs-lookup"><span data-stu-id="403a9-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="403a9-106">このチュートリアルでは、Azure 空間アンカー (ASA) を使用する場合のアンカー検出、イベント、および状態に関するフィードバックをユーザーに提供する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="403a9-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="403a9-107">目標</span><span class="sxs-lookup"><span data-stu-id="403a9-107">Objectives</span></span>

* <span data-ttu-id="403a9-108">現在の ASA セッションに関する重要な情報を表示する UI パネルを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="403a9-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="403a9-109">ASA SDK によってユーザーに提供されるフィードバック要素について理解し、調査する</span><span class="sxs-lookup"><span data-stu-id="403a9-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="403a9-110">ASA フィードバック UI パネルを設定する</span><span class="sxs-lookup"><span data-stu-id="403a9-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="403a9-111">[階層] ウィンドウで、 **Textcontent**オブジェクト > の**指示**を右クリックし、[ **3D オブジェクト** > **テキスト-TextMeshPro** ] を選択して、指示 > Textcontent オブジェクトの子として TextMeshPro Text オブジェクトを作成し、適切な名前 (たとえば、**フィードバック**) を指定します。</span><span class="sxs-lookup"><span data-stu-id="403a9-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="403a9-113">シーンを簡単に操作できるようにするには、オブジェクトの左側にある目のアイコンをクリックして、ParentAnchor オブジェクトの<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">シーンの表示</a>をオフに設定します。</span><span class="sxs-lookup"><span data-stu-id="403a9-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="403a9-114">これにより、シーンウィンドウ内のオブジェクトが非表示になります。ゲーム中の可視性は変更されません。</span><span class="sxs-lookup"><span data-stu-id="403a9-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="403a9-115">**フィードバック**オブジェクトを選択した状態で、[インスペクター] ウィンドウの位置とサイズを変更して、指示テキストの下に表示されるようにします。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="403a9-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="403a9-116">Rect 変換**Pos Y**を-0.24 に変更します。</span><span class="sxs-lookup"><span data-stu-id="403a9-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="403a9-117">四角形の変換**幅**を0.555 に変更します</span><span class="sxs-lookup"><span data-stu-id="403a9-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="403a9-118">四角形の変換の**高さ**を0.1 に変更します。</span><span class="sxs-lookup"><span data-stu-id="403a9-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="403a9-119">次に、テキスト領域内でテキストが適切に適合するように、[フォントのプロパティ] を選択します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="403a9-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="403a9-120">Text メッシュ Pro (スクリプト) の**フォントスタイル**を太字に変更する</span><span class="sxs-lookup"><span data-stu-id="403a9-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="403a9-121">Text メッシュ Pro (スクリプト) の**フォントサイズ**を0.17 に変更します。</span><span class="sxs-lookup"><span data-stu-id="403a9-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="403a9-122">Text メッシュ Pro (スクリプト) の**配置**を中央および中央に変更する</span><span class="sxs-lookup"><span data-stu-id="403a9-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="403a9-124">**フィードバック**オブジェクトを選択したまま、インスペクター ウィンドウで **コンポーネントの追加** ボタンを使用して、フィードバックオブジェクトに**アンカーフィードバックスクリプト (スクリプト)** コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="403a9-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="403a9-126">**フィードバック**オブジェクトを**アンカーフィードバックスクリプト (スクリプト)** コンポーネントの [フィードバック]**テキスト**フィールドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="403a9-126">Assign the **Feedback** object to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="403a9-128">結論</span><span class="sxs-lookup"><span data-stu-id="403a9-128">Congratulations</span></span>

<span data-ttu-id="403a9-129">このチュートリアルでは、ユーザーにリアルタイムのフィードバックを提供するための Azure 空間アンカーエクスペリエンスの現在の状態を表示する UI パネルを作成する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="403a9-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
