---
title: 3D アプリランチャーの設計ガイダンス
description: 3D アプリランチャーは、アプリを起動するために選択できる、ユーザーの mixed reality ハウスの "物理" オブジェクトです。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 設計, 3D アプリランチャー, イマーシブヘッドセット, ライブキューブ
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63517682"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="13c24-104">3D アプリランチャーの設計ガイダンス</span><span class="sxs-lookup"><span data-stu-id="13c24-104">3D app launcher design guidance</span></span>

<span data-ttu-id="13c24-105">Windows Mixed Reality イマーシブ (VR) ヘッドセットを使用する場合は、山と水で囲まれた崖に家として視覚化された Windows Mixed Reality ホームを入力します (ただし、[他の環境を選択して独自に作成](add-custom-home-environments.md)することもできます)。</span><span class="sxs-lookup"><span data-stu-id="13c24-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="13c24-106">このホームの領域内では、ユーザーは、必要に応じて、必要な3D オブジェクトとアプリを自由に配置して整理することができます。</span><span class="sxs-lookup"><span data-stu-id="13c24-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="13c24-107">**3d アプリランチャー**は、アプリを起動するために選択できる、ユーザーの mixed reality ハウスの "物理" オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="13c24-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="13c24-108">![例:Floaty 鳥3D アプリランチャー](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13c24-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="13c24-109">*Floaty 鳥3D アプリランチャーの例 (架空のアプリ)*</span><span class="sxs-lookup"><span data-stu-id="13c24-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="13c24-110">3D アプリランチャー作成プロセス</span><span class="sxs-lookup"><span data-stu-id="13c24-110">3D app launcher creation process</span></span>

<span data-ttu-id="13c24-111">3D アプリランチャーを作成するには、次の3つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="13c24-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="13c24-112">設計と concepting (この記事)</span><span class="sxs-lookup"><span data-stu-id="13c24-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="13c24-113">モデリングとエクスポート</span><span class="sxs-lookup"><span data-stu-id="13c24-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="13c24-114">アプリケーションに統合します。</span><span class="sxs-lookup"><span data-stu-id="13c24-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="13c24-115">UWP アプリ</span><span class="sxs-lookup"><span data-stu-id="13c24-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="13c24-116">Win32 アプリ</span><span class="sxs-lookup"><span data-stu-id="13c24-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="13c24-117">設計の概念</span><span class="sxs-lookup"><span data-stu-id="13c24-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="13c24-118">非常になじみのあるすばらしい</span><span class="sxs-lookup"><span data-stu-id="13c24-118">Fantastic yet familiar</span></span>

<span data-ttu-id="13c24-119">アプリランチャーが存在する Windows Mixed Reality 環境は、パート fantastical/sci です。</span><span class="sxs-lookup"><span data-stu-id="13c24-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="13c24-120">最適なランチャーは、この世界の規則に従います。</span><span class="sxs-lookup"><span data-stu-id="13c24-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="13c24-121">アプリから使い慣れた代表的なオブジェクトを取得しながら、実際の現実のルールの一部を曲げられる方法を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="13c24-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="13c24-122">マジックが生成されます。</span><span class="sxs-lookup"><span data-stu-id="13c24-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="13c24-123">にくい</span><span class="sxs-lookup"><span data-stu-id="13c24-123">Intuitive</span></span>

<span data-ttu-id="13c24-124">アプリランチャーを確認するときは、アプリを起動する目的を明確にする必要があり、混乱を招くことはありません。</span><span class="sxs-lookup"><span data-stu-id="13c24-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="13c24-125">たとえば、décor が崖家の1つの部分と混同されないように、ランチャーが明らかであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="13c24-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="13c24-126">アプリランチャーは、ユーザーにタッチまたは選択を招待する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13c24-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="13c24-127">![例:新しいメモ3D アプリランチャー](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13c24-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="13c24-128">*新鮮ノート3D アプリランチャーの例 (架空のアプリ)*</span><span class="sxs-lookup"><span data-stu-id="13c24-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="13c24-129">ホームスケール</span><span class="sxs-lookup"><span data-stu-id="13c24-129">Home scale</span></span>

<span data-ttu-id="13c24-130">3D アプリランチャーは崖家に存在し、その既定のサイズは、空間内の他の "物理" オブジェクトと同じ意味になります。</span><span class="sxs-lookup"><span data-stu-id="13c24-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="13c24-131">家の植物や家具など、ランチャーを設置している場合は、自宅でも、サイズにも気が付いています。</span><span class="sxs-lookup"><span data-stu-id="13c24-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="13c24-132">開始点としては、どのように表示されるかを確認することをお勧めします。ただし、ユーザーが必要に応じてスケールアップまたはスケールダウンできることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="13c24-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="13c24-133">独自の機能</span><span class="sxs-lookup"><span data-stu-id="13c24-133">Own-able</span></span>

<span data-ttu-id="13c24-134">アプリランチャーは、ユーザーが自分のスペースにあるように感じられるオブジェクトのように感じます。</span><span class="sxs-lookup"><span data-stu-id="13c24-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="13c24-135">これらの機能は実質的にこのような処理を行っているので、ランチャーは、ユーザーが近くにいると思っていたようなものと考える必要があります。</span><span class="sxs-lookup"><span data-stu-id="13c24-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="13c24-136">![例:Astro ワープ3D アプリランチャー](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13c24-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="13c24-137">*Astro ワープ3D アプリランチャーの例 (架空のアプリ)*</span><span class="sxs-lookup"><span data-stu-id="13c24-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="13c24-138">認識可能な</span><span class="sxs-lookup"><span data-stu-id="13c24-138">Recognizable</span></span>

<span data-ttu-id="13c24-139">3D アプリランチャーは、"アプリのブランド" を表示している人にすぐに表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="13c24-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="13c24-140">アプリに星型の文字や特に識別可能なオブジェクトがある場合は、設計の大きな部分としてそれを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="13c24-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="13c24-141">現実の世界では、オブジェクトはロゴだけでなくユーザーからも関心を引くことができます。</span><span class="sxs-lookup"><span data-stu-id="13c24-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="13c24-142">認識可能なオブジェクトは、ブランドを迅速かつ明確に伝えることができます。</span><span class="sxs-lookup"><span data-stu-id="13c24-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="13c24-143">容量</span><span class="sxs-lookup"><span data-stu-id="13c24-143">Volumetric</span></span>

<span data-ttu-id="13c24-144">お客様のアプリは、ロゴを平面に配置して1日に呼び出すだけではありません。</span><span class="sxs-lookup"><span data-stu-id="13c24-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="13c24-145">ランチャーは、ユーザーの領域において、魅力的で3D な物理オブジェクトのように感じます。</span><span class="sxs-lookup"><span data-stu-id="13c24-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="13c24-146">アプリの Macy の感謝祭のパレードにバルーンを設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="13c24-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="13c24-147">だれかが言っている人は、どこにいるかということです。</span><span class="sxs-lookup"><span data-stu-id="13c24-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="13c24-148">すべての表示角度からはどのようになりますか。</span><span class="sxs-lookup"><span data-stu-id="13c24-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="13c24-149">優れた3D モデルのヒント</span><span class="sxs-lookup"><span data-stu-id="13c24-149">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="13c24-150">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="13c24-150">Best practices</span></span>
* <span data-ttu-id="13c24-151">アプリランチャーのディメンションを計画するときは、約30cm のキューブに対して撮影します。</span><span class="sxs-lookup"><span data-stu-id="13c24-151">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="13c24-152">そのため、1:1:1 のサイズ比率です。</span><span class="sxs-lookup"><span data-stu-id="13c24-152">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="13c24-153">モデルは1万ポリゴン以下である必要があります。</span><span class="sxs-lookup"><span data-stu-id="13c24-153">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="13c24-154">トライアングルの数と詳細レベルの詳細については、LODs を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13c24-154">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="13c24-155">可能な場合は、イマーシブヘッドセットでテストします。</span><span class="sxs-lookup"><span data-stu-id="13c24-155">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="13c24-156">可能な限りモデルのジオメトリに詳細をビルドします。詳細については、テクスチャに依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="13c24-156">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="13c24-157">"水のきつい" 閉じたジオメトリを構築します。</span><span class="sxs-lookup"><span data-stu-id="13c24-157">Build “water tight” closed geometry.</span></span> <span data-ttu-id="13c24-158">でモデル化されていない穴はありません。</span><span class="sxs-lookup"><span data-stu-id="13c24-158">No holes that are not modeled in.</span></span>
* <span data-ttu-id="13c24-159">オブジェクトで自然な素材を使用します。</span><span class="sxs-lookup"><span data-stu-id="13c24-159">Use natural materials in your object.</span></span> <span data-ttu-id="13c24-160">現実の世界に構築することを想像してください。</span><span class="sxs-lookup"><span data-stu-id="13c24-160">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="13c24-161">モデルの距離とサイズが異なることを確認します。</span><span class="sxs-lookup"><span data-stu-id="13c24-161">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="13c24-162">モデルの準備ができたら、「資産の[エクスポートに関するガイドライン](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13c24-162">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="13c24-163">![テクスチャの微妙な詳細情報を含むモデル](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13c24-163">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="13c24-164">*テクスチャの微妙な詳細情報を含むモデル*</span><span class="sxs-lookup"><span data-stu-id="13c24-164">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="13c24-165">回避すべき事項</span><span class="sxs-lookup"><span data-stu-id="13c24-165">What to avoid</span></span>
* <span data-ttu-id="13c24-166">ハイコントラストの詳細や、小さな、ビジーのパターン、テクスチャは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="13c24-166">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="13c24-167">シンジオメトリは使用しないでください。距離が適切ではなく、別名が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="13c24-167">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="13c24-168">モデルの一部が1:1:1 のサイズ比を超えて拡張されないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="13c24-168">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="13c24-169">スケーリングの問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="13c24-169">It will create scaling problems.</span></span>

<span data-ttu-id="13c24-170">![ハイコントラストの小さなビジーパターンを避ける](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13c24-170">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="13c24-171">*ハイコントラスト、小さい、ビジーパターンを避ける*</span><span class="sxs-lookup"><span data-stu-id="13c24-171">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="13c24-172">型を処理する方法</span><span class="sxs-lookup"><span data-stu-id="13c24-172">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="13c24-173">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="13c24-173">Best practices</span></span>
* <span data-ttu-id="13c24-174">種類は、アプリランチャーの約 1/3 (またはそれ以上) で構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="13c24-174">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="13c24-175">Type は、ランチャーが実際にランチャーであることをユーザーに知らせる主要な作業であり、非常に大きな場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="13c24-175">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="13c24-176">型を大きくするのは避けてください。アプリランチャーのコアディメンション (より多く以下) の範囲内に保持してください。</span><span class="sxs-lookup"><span data-stu-id="13c24-176">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="13c24-177">フラット型は機能しますが、特定の角度や特定の環境で表示するのが難しい場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="13c24-177">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="13c24-178">これを実現するには、それをソリッドオブジェクトまたは背景に配置することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="13c24-178">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="13c24-179">ディメンションを型に追加すると、3D では見栄えが良くなります。</span><span class="sxs-lookup"><span data-stu-id="13c24-179">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="13c24-180">種類の面の網掛けは、読みやすさを向上させるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="13c24-180">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


<span data-ttu-id="13c24-181">**機能する色を入力する**</span><span class="sxs-lookup"><span data-stu-id="13c24-181">**Type colors that work**</span></span>
* <span data-ttu-id="13c24-182">White</span><span class="sxs-lookup"><span data-stu-id="13c24-182">White</span></span>
* <span data-ttu-id="13c24-183">黒</span><span class="sxs-lookup"><span data-stu-id="13c24-183">Black</span></span>
* <span data-ttu-id="13c24-184">明るい半彩度の色</span><span class="sxs-lookup"><span data-stu-id="13c24-184">Bright semi-saturated color</span></span>

<span data-ttu-id="13c24-185">![機能する色を入力します。](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13c24-185">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="13c24-186">*機能する色を入力する*</span><span class="sxs-lookup"><span data-stu-id="13c24-186">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="13c24-187">回避すべき事項</span><span class="sxs-lookup"><span data-stu-id="13c24-187">What to avoid</span></span>

<span data-ttu-id="13c24-188">**問題の原因となる色を入力する**</span><span class="sxs-lookup"><span data-stu-id="13c24-188">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="13c24-189">ミッドトーン</span><span class="sxs-lookup"><span data-stu-id="13c24-189">Mid-tones</span></span>
* <span data-ttu-id="13c24-190">灰色</span><span class="sxs-lookup"><span data-stu-id="13c24-190">Gray</span></span>
* <span data-ttu-id="13c24-191">彩度が高い色または desaturated の色</span><span class="sxs-lookup"><span data-stu-id="13c24-191">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="13c24-192">![問題の原因となる色を入力します。](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13c24-192">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="13c24-193">*問題の原因となる色を入力する*</span><span class="sxs-lookup"><span data-stu-id="13c24-193">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="13c24-194">照明</span><span class="sxs-lookup"><span data-stu-id="13c24-194">Lighting</span></span>

<span data-ttu-id="13c24-195">アプリランチャーのライティングは、崖ハウス環境から取得されます。</span><span class="sxs-lookup"><span data-stu-id="13c24-195">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="13c24-196">ライトとシャドウの両方で適切に見えるように、家全体の複数の場所でランチャーをテストしてください。</span><span class="sxs-lookup"><span data-stu-id="13c24-196">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="13c24-197">このドキュメントに記載されている他の設計ガイダンスに従っている場合は、崖家のほとんどの照明に対してランチャーが非常に優れた形になっているはずです。</span><span class="sxs-lookup"><span data-stu-id="13c24-197">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="13c24-198">環境内のさまざまなライトをランチャーがどのように検索するのかをテストするのに適しているのは、テラス (芝生を使用した具体的な領域) の外側と背面のどこにあるかを問わず、Studio、メディアルームです。</span><span class="sxs-lookup"><span data-stu-id="13c24-198">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="13c24-199">もう1つの優れたテストは、それを半分のライトと半分に配置し、外観を確認することです。</span><span class="sxs-lookup"><span data-stu-id="13c24-199">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="13c24-200">![起動ツールがライトとシャドウの両方で適切であることを確認します。](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13c24-200">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="13c24-201">*起動ツールがライトとシャドウの両方で適切であることを確認します。*</span><span class="sxs-lookup"><span data-stu-id="13c24-201">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="13c24-202">テクスチャ</span><span class="sxs-lookup"><span data-stu-id="13c24-202">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="13c24-203">テクスチャの作成</span><span class="sxs-lookup"><span data-stu-id="13c24-203">Authoring your textures</span></span>

<span data-ttu-id="13c24-204">3D アプリランチャーの終了形式は、glb ファイルになります。これは、(物理的にベースになった) .PBR パイプラインを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="13c24-204">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="13c24-205">これは厄介なプロセスである可能性があります。すでにない場合は、技術的アーティストを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="13c24-205">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="13c24-206">勇気 DIY がある場合は、まず、情報を[調査して、.pbr の用語について学習](http://wiki.polycount.com/wiki/PBR)して、内部で何が起きているかを確認すると、よくある間違いを避けることができます。</span><span class="sxs-lookup"><span data-stu-id="13c24-206">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](http://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="13c24-207">![例:新しいノートアプリ](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="13c24-207">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="13c24-208">*新鮮ノート3D アプリランチャーの例 (架空のアプリ)*</span><span class="sxs-lookup"><span data-stu-id="13c24-208">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="13c24-209">**推奨 authoring tool**</span><span class="sxs-lookup"><span data-stu-id="13c24-209">**Recommended authoring tool**</span></span>

<span data-ttu-id="13c24-210">最終的なファイルを作成するには、Allegorithmic による[物質塗装](https://www.allegorithmic.com/products/substance-painter)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="13c24-210">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="13c24-211">物質コピーの作成に慣れていない場合は、次の[チュートリアル](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13c24-211">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="13c24-212">(また、 [3D コート](https://3dcoat.com/home/)、 [Quixel Suite 2](https://quixel.se/suite2/)、または[marmoset toolbag](https://www.marmoset.co/toolbag/)は、これらのいずれかを使い慣れている場合にも機能します)。</span><span class="sxs-lookup"><span data-stu-id="13c24-212">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="13c24-213">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="13c24-213">Best practices</span></span>

* <span data-ttu-id="13c24-214">アプリランチャーオブジェクトが .PBR 用に作成されている場合、そのオブジェクトを崖家環境に変換するのは非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="13c24-214">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="13c24-215">シェーダーは金属/粗さのフローを想定しています。 Unreal の .PBR シェーダーは、近いファクシミリです。</span><span class="sxs-lookup"><span data-stu-id="13c24-215">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="13c24-216">テクスチャをエクスポートするときは、推奨される[テクスチャのサイズ](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines)を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="13c24-216">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="13c24-217">次のように、リアルタイムライティング用にオブジェクトを構築してください。</span><span class="sxs-lookup"><span data-stu-id="13c24-217">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="13c24-218">影を描画しない (影を描画する)</span><span class="sxs-lookup"><span data-stu-id="13c24-218">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="13c24-219">テクスチャに含まれる光源を避けます</span><span class="sxs-lookup"><span data-stu-id="13c24-219">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="13c24-220">いずれかの .PBR マテリアル作成パッケージを使用して、シェーダー用に生成された適切なマップを取得します。</span><span class="sxs-lookup"><span data-stu-id="13c24-220">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="13c24-221">関連項目</span><span class="sxs-lookup"><span data-stu-id="13c24-221">See also</span></span>

* [<span data-ttu-id="13c24-222">Mixed reality ホームで使用する3D モデルを作成する</span><span class="sxs-lookup"><span data-stu-id="13c24-222">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="13c24-223">3D アプリ起動ツールの実装 (UWP アプリ)</span><span class="sxs-lookup"><span data-stu-id="13c24-223">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="13c24-224">3D アプリ起動ツールの実装 (Win32 アプリ)</span><span class="sxs-lookup"><span data-stu-id="13c24-224">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
