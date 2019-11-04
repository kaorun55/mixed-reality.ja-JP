---
title: オブジェクトコレクション
description: オブジェクトコレクションは、定義済みの3次元図形内のオブジェクトの配列をレイアウトするのに役立つレイアウトコントロールです。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、コントロール、デザイン
ms.openlocfilehash: 8f3629c6d9465383efc901ed784a3719cd6fdfb2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438168"
---
# <a name="object-collection"></a><span data-ttu-id="d4f3a-104">オブジェクトコレクション</span><span class="sxs-lookup"><span data-stu-id="d4f3a-104">Object collection</span></span>

![Elements アプリの定期テーブルで使用されるオブジェクトコレクション](images/640px-objectcollection-hero-640px.jpg)<br>


<span data-ttu-id="d4f3a-106">オブジェクトコレクションは、定義済みの3次元図形内のオブジェクトの配列をレイアウトするのに役立つレイアウトコントロールです。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="d4f3a-107">さまざまな表面スタイル (**平面、円柱、球**、**放射状**) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="d4f3a-108">オブジェクトの半径とサイズ、およびそれらの間の間隔を調整できます。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="d4f3a-109">オブジェクトコレクションでは、Unity からのすべてのオブジェクト (2D と3D の両方) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="d4f3a-110">**[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** では、オブジェクトコレクションの作成に役立つ Unity スクリプトと例を作成しました。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="d4f3a-111">オブジェクトコレクションの例</span><span class="sxs-lookup"><span data-stu-id="d4f3a-111">Object collection examples</span></span>

<span data-ttu-id="d4f3a-112">[要素の周期](periodic-table-of-the-elements.md)的な表は、オブジェクトコレクションのしくみを示すサンプルアプリです。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-112">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="d4f3a-113">オブジェクトコレクションを使用して、さまざまな形状の3D 化学要素ボックスをレイアウトします。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="d4f3a-114">要素アプリの定期的なテーブルに表示される ![オブジェクトコレクションの例](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d4f3a-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="d4f3a-115">*Elements サンプルアプリの定期的な表に示されているオブジェクトコレクションの例*</span><span class="sxs-lookup"><span data-stu-id="d4f3a-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="d4f3a-116">3D オブジェクト</span><span class="sxs-lookup"><span data-stu-id="d4f3a-116">3D objects</span></span>

<span data-ttu-id="d4f3a-117">オブジェクトコレクションを使用すると、インポートされた3D オブジェクトをレイアウトできます。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="d4f3a-118">次の例では、一部の3D 椅子オブジェクトの平面および円柱レイアウトを示しています。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="d4f3a-119">3D オブジェクトの平面レイアウトおよび円柱レイアウトの ![例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d4f3a-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="d4f3a-120">*3D オブジェクトの平面レイアウトと円柱レイアウトの例*</span><span class="sxs-lookup"><span data-stu-id="d4f3a-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="d4f3a-121">2D オブジェクト</span><span class="sxs-lookup"><span data-stu-id="d4f3a-121">2D objects</span></span>

<span data-ttu-id="d4f3a-122">オブジェクトコレクションと共に2D イメージを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="d4f3a-123">次の例では、グリッドに2D イメージを表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![オブジェクトコレクションを含む2D イメージの例](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="d4f3a-125">オブジェクトコレクションを含む2D イメージの例を ![](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="d4f3a-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="d4f3a-126">*2D イメージでオブジェクトコレクションを使用する例*</span><span class="sxs-lookup"><span data-stu-id="d4f3a-126">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="d4f3a-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4f3a-127">See also</span></span>
* [<span data-ttu-id="d4f3a-128">GitHub の Mixed Reality Toolkit でのオブジェクトコレクションのためのスクリプトと prefabs</span><span class="sxs-lookup"><span data-stu-id="d4f3a-128">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="d4f3a-129">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="d4f3a-129">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d4f3a-130">境界ボックス</span><span class="sxs-lookup"><span data-stu-id="d4f3a-130">Bounding Box</span></span>](app-bar-and-bounding-box.md)
