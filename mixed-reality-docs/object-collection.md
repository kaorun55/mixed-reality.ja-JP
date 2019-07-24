---
title: オブジェクトコレクション
description: オブジェクトコレクションは、定義済みの3次元図形内のオブジェクトの配列をレイアウトするのに役立つレイアウトコントロールです。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、コントロール、デザイン
ms.openlocfilehash: 7c3bbd82ec909b5a2e3c81f122366be564934f4d
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813890"
---
# <a name="object-collection"></a><span data-ttu-id="e5709-104">オブジェクトコレクション</span><span class="sxs-lookup"><span data-stu-id="e5709-104">Object collection</span></span>

<span data-ttu-id="e5709-105">オブジェクトコレクションは、定義済みの3次元図形内のオブジェクトの配列をレイアウトするのに役立つレイアウトコントロールです。</span><span class="sxs-lookup"><span data-stu-id="e5709-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="e5709-106">さまざまな表面スタイル (**平面、円柱、球**、**放射状**) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e5709-106">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="e5709-107">オブジェクトの半径とサイズ、およびそれらの間の間隔を調整できます。</span><span class="sxs-lookup"><span data-stu-id="e5709-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="e5709-108">オブジェクトコレクションでは、Unity からのすべてのオブジェクト (2D と3D の両方) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e5709-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="e5709-109">**[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** では、オブジェクトコレクションの作成に役立つ Unity スクリプトと例を作成しました。</span><span class="sxs-lookup"><span data-stu-id="e5709-109">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

<span data-ttu-id="e5709-110">![Elements アプリの定期テーブルで使用されるオブジェクトコレクション](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e5709-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="e5709-111">*オブジェクトコレクションの使用例*</span><span class="sxs-lookup"><span data-stu-id="e5709-111">*Examples of using object collection*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="e5709-112">オブジェクトコレクションの例</span><span class="sxs-lookup"><span data-stu-id="e5709-112">Object collection examples</span></span>

<span data-ttu-id="e5709-113">[要素の周期](periodic-table-of-the-elements.md)的な表は、オブジェクトコレクションのしくみを示すサンプルアプリです。</span><span class="sxs-lookup"><span data-stu-id="e5709-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="e5709-114">オブジェクトコレクションを使用して、さまざまな形状の3D 化学要素ボックスをレイアウトします。</span><span class="sxs-lookup"><span data-stu-id="e5709-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="e5709-115">![Elements アプリの定期テーブルに表示されるオブジェクトコレクションの例](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e5709-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="e5709-116">*Elements サンプルアプリの定期的な表に示されているオブジェクトコレクションの例*</span><span class="sxs-lookup"><span data-stu-id="e5709-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="e5709-117">3D オブジェクト</span><span class="sxs-lookup"><span data-stu-id="e5709-117">3D objects</span></span>

<span data-ttu-id="e5709-118">オブジェクトコレクションを使用すると、インポートされた3D オブジェクトをレイアウトできます。</span><span class="sxs-lookup"><span data-stu-id="e5709-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="e5709-119">次の例では、一部の3D 椅子オブジェクトの平面および円柱レイアウトを示しています。</span><span class="sxs-lookup"><span data-stu-id="e5709-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="e5709-120">![3D オブジェクトの平面レイアウトと円柱レイアウトの例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e5709-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="e5709-121">*3D オブジェクトの平面レイアウトと円柱レイアウトの例*</span><span class="sxs-lookup"><span data-stu-id="e5709-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="e5709-122">2D オブジェクト</span><span class="sxs-lookup"><span data-stu-id="e5709-122">2D objects</span></span>

<span data-ttu-id="e5709-123">オブジェクトコレクションと共に2D イメージを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e5709-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="e5709-124">次の例では、グリッドに2D イメージを表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e5709-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![オブジェクトコレクションを含む2D イメージの例](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="e5709-126">![オブジェクトコレクションを含む2D イメージの例](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="e5709-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="e5709-127">*2D イメージでオブジェクトコレクションを使用する例*</span><span class="sxs-lookup"><span data-stu-id="e5709-127">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="e5709-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5709-128">See also</span></span>
* [<span data-ttu-id="e5709-129">GitHub の Mixed Reality Toolkit でのオブジェクトコレクションのためのスクリプトと prefabs</span><span class="sxs-lookup"><span data-stu-id="e5709-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="e5709-130">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="e5709-130">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e5709-131">境界ボックス</span><span class="sxs-lookup"><span data-stu-id="e5709-131">Bounding Box</span></span>](app-bar-and-bounding-box.md)
