---
title: オブジェクトのコレクション
description: オブジェクトのコレクションは、定義済みの 3 次元の図形内のオブジェクトの配列をレイアウトできるレイアウト コントロールです。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、コントロールのデザイン
ms.openlocfilehash: 7c3bbd82ec909b5a2e3c81f122366be564934f4d
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813890"
---
# <a name="object-collection"></a><span data-ttu-id="bba9c-104">オブジェクトのコレクション</span><span class="sxs-lookup"><span data-stu-id="bba9c-104">Object collection</span></span>

<span data-ttu-id="bba9c-105">オブジェクトのコレクションは、定義済みの 3 次元の図形内のオブジェクトの配列をレイアウトできるレイアウト コントロールです。</span><span class="sxs-lookup"><span data-stu-id="bba9c-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="bba9c-106">画面のさまざまなスタイルのサポート**平面、円柱、球体**と**放射状**します。</span><span class="sxs-lookup"><span data-stu-id="bba9c-106">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="bba9c-107">Radius およびオブジェクトとそれらの間の領域のサイズを調整できます。</span><span class="sxs-lookup"><span data-stu-id="bba9c-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="bba9c-108">オブジェクトのコレクションには、Unity の 2D および 3D の両方から任意のオブジェクトがサポートしています。</span><span class="sxs-lookup"><span data-stu-id="bba9c-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="bba9c-109">**[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** 、Unity スクリプトを作成したとする際に役立つ例がオブジェクトのコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="bba9c-109">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

<span data-ttu-id="bba9c-110">![要素のアプリの定期的テーブルで使用されるオブジェクト コレクション](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bba9c-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="bba9c-111">*オブジェクトのコレクションを使用する例*</span><span class="sxs-lookup"><span data-stu-id="bba9c-111">*Examples of using object collection*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="bba9c-112">オブジェクトのコレクションの例</span><span class="sxs-lookup"><span data-stu-id="bba9c-112">Object collection examples</span></span>

<span data-ttu-id="bba9c-113">[要素のテーブルを定期的](periodic-table-of-the-elements.md)オブジェクトのコレクションのしくみを示すサンプル アプリです。</span><span class="sxs-lookup"><span data-stu-id="bba9c-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="bba9c-114">3D の化学物質要素のボックスでさまざまな図形をレイアウトするオブジェクトのコレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="bba9c-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="bba9c-115">![要素のアプリの定期的表に示したオブジェクト コレクションのサンプル](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bba9c-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="bba9c-116">*要素のサンプル アプリの定期的表に示したオブジェクト コレクションのサンプル*</span><span class="sxs-lookup"><span data-stu-id="bba9c-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="bba9c-117">3D オブジェクト</span><span class="sxs-lookup"><span data-stu-id="bba9c-117">3D objects</span></span>

<span data-ttu-id="bba9c-118">オブジェクトのコレクションを使用して、インポートされた 3D オブジェクトをレイアウトすることができます。</span><span class="sxs-lookup"><span data-stu-id="bba9c-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="bba9c-119">次の例では、平面と、3 D の椅子のオブジェクトの円柱のレイアウトを示します。</span><span class="sxs-lookup"><span data-stu-id="bba9c-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="bba9c-120">![平面と 3D オブジェクトの円柱のレイアウトの例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bba9c-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="bba9c-121">*平面と 3D オブジェクトの円柱のレイアウトの例*</span><span class="sxs-lookup"><span data-stu-id="bba9c-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="bba9c-122">2D オブジェクト</span><span class="sxs-lookup"><span data-stu-id="bba9c-122">2D objects</span></span>

<span data-ttu-id="bba9c-123">オブジェクトのコレクションを使用して、2 D 画像を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="bba9c-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="bba9c-124">次の例で示す方法 2 D 画像をグリッドに表示されることができます。</span><span class="sxs-lookup"><span data-stu-id="bba9c-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![オブジェクトのコレクションを使用して、2 D 画像の例](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="bba9c-126">![オブジェクトのコレクションを使用して、2 D 画像の例](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="bba9c-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="bba9c-127">*2D イメージ オブジェクトのコレクションの使用例*</span><span class="sxs-lookup"><span data-stu-id="bba9c-127">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="bba9c-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="bba9c-128">See also</span></span>
* [<span data-ttu-id="bba9c-129">スクリプトと GitHub の混在の現実 toolkit オブジェクトのコレクションのプレハブ</span><span class="sxs-lookup"><span data-stu-id="bba9c-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="bba9c-130">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="bba9c-130">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="bba9c-131">境界ボックス</span><span class="sxs-lookup"><span data-stu-id="bba9c-131">Bounding Box</span></span>](app-bar-and-bounding-box.md)
