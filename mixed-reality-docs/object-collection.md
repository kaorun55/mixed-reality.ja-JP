---
title: オブジェクトコレクション
description: オブジェクトコレクションは、定義済みの3次元図形内のオブジェクトの配列をレイアウトするのに役立つレイアウトコントロールです。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、コントロール、デザイン
ms.openlocfilehash: 9a111fcbe4c49972cc5ef22fb647f89544188af5
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143146"
---
# <a name="object-collection"></a><span data-ttu-id="a0c06-104">オブジェクトコレクション</span><span class="sxs-lookup"><span data-stu-id="a0c06-104">Object collection</span></span>

![Elements アプリの定期テーブルで使用されるオブジェクトコレクション](images/UX/UX_Hero_ObjectCollection.jpg)<br>


<span data-ttu-id="a0c06-106">オブジェクトコレクションは、定義済みの3次元図形内のオブジェクトの配列をレイアウトするのに役立つレイアウトコントロールです。</span><span class="sxs-lookup"><span data-stu-id="a0c06-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="a0c06-107">さまざまな表面スタイル (**平面、円柱、球**、**放射状**) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="a0c06-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="a0c06-108">オブジェクトの半径とサイズ、およびそれらの間の間隔を調整できます。</span><span class="sxs-lookup"><span data-stu-id="a0c06-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="a0c06-109">オブジェクトコレクションでは、Unity からのすべてのオブジェクト (2D と3D の両方) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a0c06-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="a0c06-110">**[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** では、オブジェクトコレクションの作成に役立つ Unity スクリプトと例を作成しました。</span><span class="sxs-lookup"><span data-stu-id="a0c06-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="a0c06-111">オブジェクトコレクションの例</span><span class="sxs-lookup"><span data-stu-id="a0c06-111">Object collection examples</span></span>

<span data-ttu-id="a0c06-112">[要素の周期](periodic-table-of-the-elements.md)的な表は、オブジェクトコレクションのしくみを示すサンプルアプリです。</span><span class="sxs-lookup"><span data-stu-id="a0c06-112">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="a0c06-113">オブジェクトコレクションを使用して、さまざまな形状の3D 化学要素ボックスをレイアウトします。</span><span class="sxs-lookup"><span data-stu-id="a0c06-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="a0c06-114">要素アプリの定期的なテーブルに表示される ![オブジェクトコレクションの例](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a0c06-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="a0c06-115">*Elements サンプルアプリの定期的な表に示されているオブジェクトコレクションの例*</span><span class="sxs-lookup"><span data-stu-id="a0c06-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="a0c06-116">3D オブジェクト</span><span class="sxs-lookup"><span data-stu-id="a0c06-116">3D objects</span></span>

<span data-ttu-id="a0c06-117">オブジェクトコレクションを使用すると、インポートされた3D オブジェクトをレイアウトできます。</span><span class="sxs-lookup"><span data-stu-id="a0c06-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="a0c06-118">次の例では、一部の3D 椅子オブジェクトの平面および円柱レイアウトを示しています。</span><span class="sxs-lookup"><span data-stu-id="a0c06-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="a0c06-119">3D オブジェクトの平面レイアウトおよび円柱レイアウトの ![例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a0c06-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="a0c06-120">*3D オブジェクトの平面レイアウトと円柱レイアウトの例*</span><span class="sxs-lookup"><span data-stu-id="a0c06-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="a0c06-121">2D オブジェクト</span><span class="sxs-lookup"><span data-stu-id="a0c06-121">2D objects</span></span>

<span data-ttu-id="a0c06-122">オブジェクトコレクションと共に2D イメージを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a0c06-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="a0c06-123">次の例では、グリッドに2D イメージを表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a0c06-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![オブジェクトコレクションを含む2D イメージの例](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="a0c06-125">オブジェクトコレクションを含む2D イメージの例を ![](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="a0c06-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="a0c06-126">*2D イメージでオブジェクトコレクションを使用する例*</span><span class="sxs-lookup"><span data-stu-id="a0c06-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="a0c06-127">Unity 用の MRTK (Mixed Reality Toolkit) のオブジェクトコレクション</span><span class="sxs-lookup"><span data-stu-id="a0c06-127">Object collection in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="a0c06-128">MRTK-オブジェクトコレクション</span><span class="sxs-lookup"><span data-stu-id="a0c06-128">MRTK - Object collection</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="a0c06-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0c06-129">See also</span></span>

* [<span data-ttu-id="a0c06-130">カーソル</span><span class="sxs-lookup"><span data-stu-id="a0c06-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="a0c06-131">ハンドレイ</span><span class="sxs-lookup"><span data-stu-id="a0c06-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="a0c06-132">ボタン</span><span class="sxs-lookup"><span data-stu-id="a0c06-132">Button</span></span>](button.md)
* [<span data-ttu-id="a0c06-133">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="a0c06-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a0c06-134">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="a0c06-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="a0c06-135">操作性</span><span class="sxs-lookup"><span data-stu-id="a0c06-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a0c06-136">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="a0c06-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="a0c06-137">Near メニュー</span><span class="sxs-lookup"><span data-stu-id="a0c06-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="a0c06-138">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="a0c06-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="a0c06-139">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="a0c06-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="a0c06-140">キーボード</span><span class="sxs-lookup"><span data-stu-id="a0c06-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="a0c06-141">ボタン</span><span class="sxs-lookup"><span data-stu-id="a0c06-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="a0c06-142">翻訳</span><span class="sxs-lookup"><span data-stu-id="a0c06-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="a0c06-143">スライダー</span><span class="sxs-lookup"><span data-stu-id="a0c06-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="a0c06-144">シェーダー</span><span class="sxs-lookup"><span data-stu-id="a0c06-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="a0c06-145">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="a0c06-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="a0c06-146">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="a0c06-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="a0c06-147">表面の吸着</span><span class="sxs-lookup"><span data-stu-id="a0c06-147">Surface magnetism</span></span>](surface-magnetism.md)
