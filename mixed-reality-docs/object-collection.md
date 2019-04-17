---
title: オブジェクトのコレクション
description: オブジェクトのコレクションは、定義済みの 3 次元の図形内のオブジェクトの配列をレイアウトできるレイアウト コントロールです。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、コントロールのデザイン
ms.openlocfilehash: 88ab0359d5083d43d5d6312ef1185f67ca0caa7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605011"
---
# <a name="object-collection"></a><span data-ttu-id="c386a-104">オブジェクトのコレクション</span><span class="sxs-lookup"><span data-stu-id="c386a-104">Object collection</span></span>

<span data-ttu-id="c386a-105">オブジェクトのコレクションは、定義済みの 3 次元の図形内のオブジェクトの配列をレイアウトできるレイアウト コントロールです。</span><span class="sxs-lookup"><span data-stu-id="c386a-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="c386a-106">-4 つの異なる画面スタイルがサポートしている**平面、円柱、球体**と**散布図**します。</span><span class="sxs-lookup"><span data-stu-id="c386a-106">It supports four different surface styles - **plane, cylinder, sphere** and **scatter**.</span></span> <span data-ttu-id="c386a-107">Radius およびオブジェクトとそれらの間の領域のサイズを調整できます。</span><span class="sxs-lookup"><span data-stu-id="c386a-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="c386a-108">オブジェクトのコレクションには、Unity の 2D および 3D の両方から任意のオブジェクトがサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c386a-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="c386a-109"> **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)*\*、Unity スクリプトを作成しましたと[例シーン](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity)を使用するとオブジェクトのコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="c386a-109">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**, we have created Unity script and [example scene](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity) that will help you create an object collection.</span></span>

<span data-ttu-id="c386a-110">![要素のアプリの定期的テーブルで使用されるオブジェクト コレクション](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c386a-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="c386a-111">*要素のサンプル アプリの定期的テーブルで使用されるオブジェクトのコレクション*</span><span class="sxs-lookup"><span data-stu-id="c386a-111">*Object collection used in the Periodic Table of the Elements sample app*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="c386a-112">オブジェクトのコレクションの例</span><span class="sxs-lookup"><span data-stu-id="c386a-112">Object collection examples</span></span>

<span data-ttu-id="c386a-113">[要素のテーブルを定期的](periodic-table-of-the-elements.md)オブジェクトのコレクションのしくみを示すサンプル アプリです。</span><span class="sxs-lookup"><span data-stu-id="c386a-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="c386a-114">3D の化学物質要素のボックスでさまざまな図形をレイアウトするオブジェクトのコレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="c386a-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="c386a-115">![要素のアプリの定期的表に示したオブジェクト コレクションのサンプル](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c386a-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="c386a-116">*要素のサンプル アプリの定期的表に示したオブジェクト コレクションのサンプル*</span><span class="sxs-lookup"><span data-stu-id="c386a-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="c386a-117">3D オブジェクト</span><span class="sxs-lookup"><span data-stu-id="c386a-117">3D objects</span></span>

<span data-ttu-id="c386a-118">オブジェクトのコレクションを使用して、インポートされた 3D オブジェクトをレイアウトすることができます。</span><span class="sxs-lookup"><span data-stu-id="c386a-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="c386a-119">次の例では、平面と、3 D の椅子のオブジェクトの円柱のレイアウトを示します。</span><span class="sxs-lookup"><span data-stu-id="c386a-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="c386a-120">![平面と 3D オブジェクトの円柱のレイアウトの例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c386a-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="c386a-121">*平面と 3D オブジェクトの円柱のレイアウトの例*</span><span class="sxs-lookup"><span data-stu-id="c386a-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="c386a-122">2D オブジェクト</span><span class="sxs-lookup"><span data-stu-id="c386a-122">2D objects</span></span>

<span data-ttu-id="c386a-123">オブジェクトのコレクションを使用して、2 D 画像を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c386a-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="c386a-124">次の例で示す方法 2 D 画像をグリッドに表示されることができます。</span><span class="sxs-lookup"><span data-stu-id="c386a-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![オブジェクトのコレクションを使用して、2 D 画像の例](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="c386a-126">![オブジェクトのコレクションを使用して、2 D 画像の例](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="c386a-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="c386a-127">*オブジェクトのコレクションを使用して、2 D 画像の例*</span><span class="sxs-lookup"><span data-stu-id="c386a-127">*Examples of 2D images with object collection*</span></span>

## <a name="see-also"></a><span data-ttu-id="c386a-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="c386a-128">See also</span></span>
* [<span data-ttu-id="c386a-129">スクリプトと GitHub の混在の現実 toolkit オブジェクトのコレクションのプレハブ</span><span class="sxs-lookup"><span data-stu-id="c386a-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)
* [<span data-ttu-id="c386a-130">対話型のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="c386a-130">Interactable object</span></span>](interactable-object.md)
