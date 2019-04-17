---
title: 要素の定期処理テーブル
description: 要素のテーブルを定期的では、Microsoft の混合現実デザイン ラボ オブジェクトのコレクションを使用して、さまざまな表面型で、3 D 空間内のオブジェクトの配列をレイアウトする方法を学びますからオープン ソースのサンプル アプリです。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、サンプル アプリ、コントロール
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604114"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="34b34-104">要素の定期処理テーブル</span><span class="sxs-lookup"><span data-stu-id="34b34-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="34b34-105">この資料で説明した調査用のサンプル、[混合現実デザイン Labs](https://github.com/Microsoft/MRDesignLabs_Unity)、について学習したことを共有の場所とに関する推奨事項は、現実アプリ開発を混在させます。</span><span class="sxs-lookup"><span data-stu-id="34b34-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="34b34-106">新しい検出を行ったときは、デザインに関連する記事とコードも進化します。</span><span class="sxs-lookup"><span data-stu-id="34b34-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="34b34-107">[要素のテーブルを定期的](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)は Microsoft の混合現実デザイン ラボからオープン ソースのサンプル アプリです。</span><span class="sxs-lookup"><span data-stu-id="34b34-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="34b34-108">このプロジェクトのさまざまなサーフェイスのタイプを使用して 3D 空間でオブジェクトの配列を配置する方法を学びます、 **[オブジェクト コレクション](object-collection.md)** します。</span><span class="sxs-lookup"><span data-stu-id="34b34-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="34b34-109">HoloLens からの標準入力に応答する対話型のオブジェクトを作成する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="34b34-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="34b34-110">実際にはアプリのエクスペリエンスを混合独自に作成する、このプロジェクトのコンポーネントを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="34b34-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![要素のアプリの期間のテーブル](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="34b34-112">アプリの詳細について</span><span class="sxs-lookup"><span data-stu-id="34b34-112">About the app</span></span>

<span data-ttu-id="34b34-113">要素の周期の表は、化学の要素とそのプロパティを 3D 空間での各は視覚化します。</span><span class="sxs-lookup"><span data-stu-id="34b34-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="34b34-114">HoloLens の注視しエア タップなどの基本的な対話が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="34b34-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="34b34-115">ユーザーは、アニメーションの 3D モデルの要素について学習できます。</span><span class="sxs-lookup"><span data-stu-id="34b34-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="34b34-116">要素の electron シェルであり、その中核は-protons と neutrons で構成されますが、視覚的に理解できます。</span><span class="sxs-lookup"><span data-stu-id="34b34-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="34b34-117">背景</span><span class="sxs-lookup"><span data-stu-id="34b34-117">Background</span></span>

<span data-ttu-id="34b34-118">HoloLens をまずが発生した後、周期表アプリは、複合現実で実験したいことがわかってアイデアをしました。</span><span class="sxs-lookup"><span data-stu-id="34b34-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="34b34-119">各要素には、テキストで表示されるデータ ポイントの数があるのでを 3D 空間での文字体裁の合成を探索するための優れた主題になると考えました。</span><span class="sxs-lookup"><span data-stu-id="34b34-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="34b34-120">要素の電子モデルを視覚化することがこのプロジェクトの別の興味深い部分です。</span><span class="sxs-lookup"><span data-stu-id="34b34-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="34b34-121">設計</span><span class="sxs-lookup"><span data-stu-id="34b34-121">Design</span></span>

<span data-ttu-id="34b34-122">定期テーブルの既定のビューの各要素の電子モデルが含まれる 3 次元のボックスは想像していた。</span><span class="sxs-lookup"><span data-stu-id="34b34-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="34b34-123">ユーザーが要素のボリュームの大まかに理解をすることができるように、各ボックスの画面は半透明なります。</span><span class="sxs-lookup"><span data-stu-id="34b34-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="34b34-124">視線入力や air をタップして、ユーザーは各要素の詳細なビューを開くでした。</span><span class="sxs-lookup"><span data-stu-id="34b34-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="34b34-125">テーブルのビューと詳細ビュー間の遷移をスムーズかつ自然にするには、しました、現実の世界を開く ボックスの物理的な相互作用に似ています。</span><span class="sxs-lookup"><span data-stu-id="34b34-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="34b34-126">![設計のスケッチ](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="34b34-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="34b34-127">*設計のスケッチ*</span><span class="sxs-lookup"><span data-stu-id="34b34-127">*Design sketches*</span></span>

<span data-ttu-id="34b34-128">詳細ビューで 3D 空間で美しく表示されるテキストの各要素の情報を視覚化することを考えました。</span><span class="sxs-lookup"><span data-stu-id="34b34-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="34b34-129">アニメーション化された 3D electron モデルでは、中央の領域に表示され、さまざまな角度から表示できます。</span><span class="sxs-lookup"><span data-stu-id="34b34-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![操作](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="34b34-131">![プロトタイプ](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="34b34-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="34b34-132">*プロトタイプの対話*</span><span class="sxs-lookup"><span data-stu-id="34b34-132">*Interaction prototypes*</span></span>

<span data-ttu-id="34b34-133">ユーザーは、テーブルの下部にあるボタンをタップして air によってサーフェスのタイプを変更することができます - プレーン、円柱、球、散布図を切り替えることができます、します。</span><span class="sxs-lookup"><span data-stu-id="34b34-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="34b34-134">一般的なコントロールとこのアプリで使用されるパターン</span><span class="sxs-lookup"><span data-stu-id="34b34-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="34b34-135">対話型のオブジェクト (ボタン)</span><span class="sxs-lookup"><span data-stu-id="34b34-135">Interactable object (button)</span></span>

<span data-ttu-id="34b34-136">[対話型のオブジェクト](interactable-object.md)HoloLens の基本的な入力に応答できるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="34b34-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="34b34-137">これは、任意のオブジェクトを簡単に適用できるプレハブ/スクリプトとして提供されます。</span><span class="sxs-lookup"><span data-stu-id="34b34-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="34b34-138">たとえば、こと、シーン内のコーヒー カップを対話型し、視線の先、エア タップ、移動および操作のジェスチャなどの入力に応答できます。</span><span class="sxs-lookup"><span data-stu-id="34b34-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="34b34-139">詳細情報</span><span class="sxs-lookup"><span data-stu-id="34b34-139">Learn more</span></span>](interactable-object.md)

![nteractable オブジェクト](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="34b34-141">オブジェクトのコレクション</span><span class="sxs-lookup"><span data-stu-id="34b34-141">Object collection</span></span>

<span data-ttu-id="34b34-142">[オブジェクト コレクション](object-collection.md)オブジェクトは、さまざまな図形で複数のオブジェクトをレイアウトするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="34b34-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="34b34-143">平面、円柱、球、散布図をサポートします。</span><span class="sxs-lookup"><span data-stu-id="34b34-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="34b34-144">Radius、行との間隔の数などの追加プロパティを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="34b34-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="34b34-145">詳細情報</span><span class="sxs-lookup"><span data-stu-id="34b34-145">Learn more</span></span>](object-collection.md)

![オブジェクトのコレクション](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="34b34-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="34b34-147">Fitbox</span></span>

<span data-ttu-id="34b34-148">既定では、ホログラムをユーザーが gazing は場所に配置するが、現時点では、アプリケーションが起動します。</span><span class="sxs-lookup"><span data-stu-id="34b34-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="34b34-149">これは、ホログラム壁の背後にある、またはテーブルの中央に配置されているなどの望ましくない結果にもつながります。</span><span class="sxs-lookup"><span data-stu-id="34b34-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="34b34-150">Fitbox 視線の先を使用して、ホログラムを配置する場所を決定することができます。</span><span class="sxs-lookup"><span data-stu-id="34b34-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="34b34-151">これは、独自のイメージや 3D オブジェクトを簡単にカスタマイズ可能な単純な PNG イメージ テクスチャで作成されます。</span><span class="sxs-lookup"><span data-stu-id="34b34-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="34b34-153">技術的な詳細</span><span class="sxs-lookup"><span data-stu-id="34b34-153">Technical details</span></span>

<span data-ttu-id="34b34-154">見つかりますスクリプトとプレハブ要素アプリの定期的テーブルで、 [Mixed Reality デザイン Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)します。</span><span class="sxs-lookup"><span data-stu-id="34b34-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="34b34-155">アプリケーションの例</span><span class="sxs-lookup"><span data-stu-id="34b34-155">Application examples</span></span>

<span data-ttu-id="34b34-156">ここではこのプロジェクト内のコンポーネントを活用することで作成する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="34b34-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="34b34-157">株価データ視覚化アプリ</span><span class="sxs-lookup"><span data-stu-id="34b34-157">Stock data visualization app</span></span>

<span data-ttu-id="34b34-158">要素のサンプルの定期テーブルとしては、同じコントロールと対話モデルを使用して、株式市場データを視覚化するアプリを構築できます。</span><span class="sxs-lookup"><span data-stu-id="34b34-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="34b34-159">この例では、オブジェクトのコレクションのコントロールを使用して球を図形の株価データをレイアウトします。</span><span class="sxs-lookup"><span data-stu-id="34b34-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="34b34-160">詳細ビューが興味深い方法で各株式に関する追加情報を表示でしたを想像できます。</span><span class="sxs-lookup"><span data-stu-id="34b34-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![アプリケーションの例:Finance (1/3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![アプリケーションの例:Finance (2/3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="34b34-163">![アプリケーションの例:Finance (3/3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="34b34-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="34b34-164">*要素のサンプル アプリの定期的テーブルで使用されるオブジェクトのコレクションを財務アプリで使用する方法の例*</span><span class="sxs-lookup"><span data-stu-id="34b34-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="34b34-165">スポーツ アプリ</span><span class="sxs-lookup"><span data-stu-id="34b34-165">Sports app</span></span>

<span data-ttu-id="34b34-166">これは、オブジェクトのコレクションと要素のサンプル アプリの定期的テーブルからその他のコンポーネントを使用して、スポーツ データの視覚化の例です。</span><span class="sxs-lookup"><span data-stu-id="34b34-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![アプリケーションの例:スポーツ (1/3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![アプリケーションの例:スポーツ (2/3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="34b34-169">![アプリケーションの例:スポーツ (3/3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="34b34-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="34b34-170">*要素のサンプル appcould の周期の表ではオブジェクトのコレクションを使用する方法の例は、スポーツ アプリで使用します。*</span><span class="sxs-lookup"><span data-stu-id="34b34-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="34b34-171">執筆者紹介</span><span class="sxs-lookup"><span data-stu-id="34b34-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="34b34-172"><b>ドン Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="34b34-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="34b34-173">UX デザイナー @Microsoft</span><span class="sxs-lookup"><span data-stu-id="34b34-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="34b34-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="34b34-174">See also</span></span>

* [<span data-ttu-id="34b34-175">対話型のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="34b34-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="34b34-176">オブジェクトのコレクション</span><span class="sxs-lookup"><span data-stu-id="34b34-176">Object collection</span></span>](object-collection.md)
