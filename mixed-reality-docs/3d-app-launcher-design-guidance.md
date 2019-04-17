---
title: 3D アプリ起動ツールの設計ガイダンス
description: 3D アプリ起動ツールは、アプリの起動を選択できるユーザーの複合現実の家の「物理」オブジェクトです。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、3D アプリ起動ツール、イマーシブ ヘッドセット、ライブのキューブ
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598551"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="f56f1-104">3D アプリ起動ツールの設計ガイダンス</span><span class="sxs-lookup"><span data-stu-id="f56f1-104">3D app launcher design guidance</span></span>

<span data-ttu-id="f56f1-105">山と水で囲まれた cliff に存在する家として視覚化されます、ホーム Windows Mixed Reality を入力する没入型 (VR) Windows Mixed Reality ヘッドセットに配置するときに (こともできます[他の環境を選択し、自作](add-custom-home-environments.md)).</span><span class="sxs-lookup"><span data-stu-id="f56f1-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="f56f1-106">この領域内で、ユーザーは無料、3 D オブジェクトとどのように、関心のあるアプリを整理します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="f56f1-107">A **3D アプリ起動ツール**「物理」のオブジェクトでは、ユーザーがアプリを起動するを選択することを実際に家を混在です。</span><span class="sxs-lookup"><span data-stu-id="f56f1-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="f56f1-108">![例:フローティング Bird 3D アプリ起動ツール](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f56f1-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="f56f1-109">*フローティング Bird 3D アプリ ランチャー例 (架空のアプリ)*</span><span class="sxs-lookup"><span data-stu-id="f56f1-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="f56f1-110">3D アプリ起動ツールの作成プロセス</span><span class="sxs-lookup"><span data-stu-id="f56f1-110">3D app launcher creation process</span></span>

<span data-ttu-id="f56f1-111">3D アプリ起動ツールを作成する 3 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="f56f1-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="f56f1-112">デザインと concepting (この記事)</span><span class="sxs-lookup"><span data-stu-id="f56f1-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="f56f1-113">モデリングとエクスポート</span><span class="sxs-lookup"><span data-stu-id="f56f1-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="f56f1-114">アプリケーションに統合します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="f56f1-115">UWP アプリ</span><span class="sxs-lookup"><span data-stu-id="f56f1-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="f56f1-116">Win32 アプリ</span><span class="sxs-lookup"><span data-stu-id="f56f1-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="f56f1-117">設計概念</span><span class="sxs-lookup"><span data-stu-id="f56f1-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="f56f1-118">空想まだ理解しています。</span><span class="sxs-lookup"><span data-stu-id="f56f1-118">Fantastic yet familiar</span></span>

<span data-ttu-id="f56f1-119">アプリ起動ツールが存在する Windows Mixed Reality 環境では、一部使いやすく、パーツ ファンタジック/sci-fi です。</span><span class="sxs-lookup"><span data-stu-id="f56f1-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="f56f1-120">最適なランチャーでは、この世界の規則に従います。</span><span class="sxs-lookup"><span data-stu-id="f56f1-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="f56f1-121">使い慣れた、代表的なオブジェクトをアプリから実行しますが、実際には実際の規則のいくつか曲げないように方法と考えてください。</span><span class="sxs-lookup"><span data-stu-id="f56f1-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="f56f1-122">マジックが発生します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="f56f1-123">直感的です</span><span class="sxs-lookup"><span data-stu-id="f56f1-123">Intuitive</span></span>

<span data-ttu-id="f56f1-124">アプリ起動ツールを確認して - アプリを起動する目的で明確にする必要があります、混乱が生じることはできません。</span><span class="sxs-lookup"><span data-stu-id="f56f1-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="f56f1-125">たとえば、ランチャーがも親しみやすく、Cliff の家のについて混乱しないこと、アプリの明らかなのに十分なの代表であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="f56f1-126">アプリ起動ツールには、タッチとその選択に人を招待する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f56f1-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="f56f1-127">![例:最新の注 3D アプリ起動ツール](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f56f1-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="f56f1-128">*新しいメモ 3D アプリ ランチャー例 (架空のアプリ)*</span><span class="sxs-lookup"><span data-stu-id="f56f1-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="f56f1-129">ホーム スケール</span><span class="sxs-lookup"><span data-stu-id="f56f1-129">Home scale</span></span>

<span data-ttu-id="f56f1-130">Cliff 家に住んで 3D アプリ ランチャーと、既定のサイズが、領域の「物理」の他のオブジェクトを使用する意味を確認してください。</span><span class="sxs-lookup"><span data-stu-id="f56f1-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="f56f1-131">場合は、横にある、ランチャーを配置すると、たとえば、家の工場またはいくつかの家具、ように思われる size-wise、自宅で。</span><span class="sxs-lookup"><span data-stu-id="f56f1-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="f56f1-132">出発点として適していますが、30 の立方センチメートルで外観を確認が、ユーザーことができます、スケール アップまたはスケール ダウン必要な場合に注意してください。</span><span class="sxs-lookup"><span data-stu-id="f56f1-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="f56f1-133">所有できません。</span><span class="sxs-lookup"><span data-stu-id="f56f1-133">Own-able</span></span>

<span data-ttu-id="f56f1-134">アプリ起動ツールと感じる人が自分のスペースであることを嬉しく思いますなりますオブジェクト必要があります。</span><span class="sxs-lookup"><span data-stu-id="f56f1-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="f56f1-135">ある事実上を囲む自体これらの点では、ランチャーように思われるもののようにユーザーと考えることが望ましい探そうとして、近くに保つため。</span><span class="sxs-lookup"><span data-stu-id="f56f1-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="f56f1-136">![例:3.5. コンフィグレーション Warp の 3D アプリ起動ツール](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f56f1-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="f56f1-137">*3.5. コンフィグレーション Warp 3D アプリ起動ツールの例 (架空のアプリ)*</span><span class="sxs-lookup"><span data-stu-id="f56f1-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="f56f1-138">認識可能です</span><span class="sxs-lookup"><span data-stu-id="f56f1-138">Recognizable</span></span>

<span data-ttu-id="f56f1-139">3D アプリ起動ツールは、それを表示してユーザーを「アプリのブランド」を express 瞬時にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f56f1-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="f56f1-140">アプリにスター文字または特にを特定できるオブジェクトがある、設計の大きな部分として使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f56f1-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="f56f1-141">複合現実の世界では、オブジェクトは単独でロゴだけよりもユーザーから注目を描画します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="f56f1-142">認識可能なオブジェクトは、迅速かつ明確にブランドを通信します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="f56f1-143">帯域幅消費型</span><span class="sxs-lookup"><span data-stu-id="f56f1-143">Volumetric</span></span>

<span data-ttu-id="f56f1-144">平面にロゴを配置して、つもりだけでは、アプリが必要です。</span><span class="sxs-lookup"><span data-stu-id="f56f1-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="f56f1-145">ユーザーの領域で、物理魅力的な 3D オブジェクトのように、ランチャーように思われる。</span><span class="sxs-lookup"><span data-stu-id="f56f1-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="f56f1-146">アプリこれは、バルーン Macy の感謝祭続々 と登場するを想像することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f56f1-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="f56f1-147">自問何がうなら人沿いになるようですか。</span><span class="sxs-lookup"><span data-stu-id="f56f1-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="f56f1-148">どの優れたすべて表示する角度からでしょうか。</span><span class="sxs-lookup"><span data-stu-id="f56f1-148">What would look great from all viewing angles?</span></span>


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


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="f56f1-149">適切な 3D モデルのヒント</span><span class="sxs-lookup"><span data-stu-id="f56f1-149">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="f56f1-150">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="f56f1-150">Best practices</span></span>
* <span data-ttu-id="f56f1-151">を、アプリ起動ツールの寸法を計画するときは、約 30 cm キューブの撮影してください。</span><span class="sxs-lookup"><span data-stu-id="f56f1-151">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="f56f1-152">これは、1:1:1 の比率。</span><span class="sxs-lookup"><span data-stu-id="f56f1-152">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="f56f1-153">モデルには、10,000 多角形を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f56f1-153">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="f56f1-154">三角形の数とレベル (Lod) の詳細の詳細については</span><span class="sxs-lookup"><span data-stu-id="f56f1-154">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="f56f1-155">可能であれば、イマーシブ ヘッドセットをテストします。</span><span class="sxs-lookup"><span data-stu-id="f56f1-155">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="f56f1-156">可能な限りビルド詳細をモデルのジオメトリ – 詳細のテクスチャに依存しないようにします。</span><span class="sxs-lookup"><span data-stu-id="f56f1-156">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="f56f1-157">"Water 緊密な"閉じられたジオメトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-157">Build “water tight” closed geometry.</span></span> <span data-ttu-id="f56f1-158">モデル化されていない穴なしにします。</span><span class="sxs-lookup"><span data-stu-id="f56f1-158">No holes that are not modeled in.</span></span>
* <span data-ttu-id="f56f1-159">オブジェクトの自然なマテリアルを使用します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-159">Use natural materials in your object.</span></span> <span data-ttu-id="f56f1-160">現実の世界での作成を想像してください。</span><span class="sxs-lookup"><span data-stu-id="f56f1-160">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="f56f1-161">さまざまな距離とサイズにも、モデルを読み取りを確認します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-161">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="f56f1-162">モデルは、準備ができましたが、読み取られたとき、[資産のガイドラインをエクスポートする](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-162">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="f56f1-163">![テクスチャの微妙な細部を使用するモデルします。](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f56f1-163">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="f56f1-164">*テクスチャの微妙な細部を使用するモデルします。*</span><span class="sxs-lookup"><span data-stu-id="f56f1-164">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="f56f1-165">避けるべきこと</span><span class="sxs-lookup"><span data-stu-id="f56f1-165">What to avoid</span></span>
* <span data-ttu-id="f56f1-166">ハイ コントラストの詳細または小さな、ビジー状態のパターンとテクスチャを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f56f1-166">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="f56f1-167">シン ジオメトリを使用しないでください – 距離はうまく動作しはエイリアスが正しくないことができます。</span><span class="sxs-lookup"><span data-stu-id="f56f1-167">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="f56f1-168">モデルの部分に拡張しないように、1 を超える多すぎる: 1:1 の比率。</span><span class="sxs-lookup"><span data-stu-id="f56f1-168">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="f56f1-169">スケーリングの問題が作成されます。</span><span class="sxs-lookup"><span data-stu-id="f56f1-169">It will create scaling problems.</span></span>

<span data-ttu-id="f56f1-170">![ハイ コントラスト、小規模のビジー状態のパターンを避ける](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f56f1-170">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="f56f1-171">*ハイ コントラスト、小さな、ビジー状態のパターンを避ける*</span><span class="sxs-lookup"><span data-stu-id="f56f1-171">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="f56f1-172">型を処理する方法</span><span class="sxs-lookup"><span data-stu-id="f56f1-172">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="f56f1-173">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="f56f1-173">Best practices</span></span>
* <span data-ttu-id="f56f1-174">型は、アプリ起動ツール (以上) の約 1/3 を構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f56f1-174">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="f56f1-175">種類は、人、ランチャーは、実際には、非常に多くの場合は便利なので、ランチャーでアイデアを提供することです。</span><span class="sxs-lookup"><span data-stu-id="f56f1-175">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="f56f1-176">Super ワイド型しないように – ようにするアプリケーション ランチャーの範囲内でコア ディメンション (増減) お試しください。</span><span class="sxs-lookup"><span data-stu-id="f56f1-176">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="f56f1-177">フラットな型は、作業できますが、ことは、特定の角度からと特定の環境に表示する時間が難しいことができますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f56f1-177">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="f56f1-178">ソリッド オブジェクトまたはこれを支援することの背景を配置することを検討する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f56f1-178">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="f56f1-179">追加のディメンションの種類を感じる 3D での改善。</span><span class="sxs-lookup"><span data-stu-id="f56f1-179">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="f56f1-180">型の側面を網掛け別、暗い色は読みやすさの役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f56f1-180">Shading the sides of the type a different, darker color can help with readability.</span></span>


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


<span data-ttu-id="f56f1-181">**作業の種類の色**</span><span class="sxs-lookup"><span data-stu-id="f56f1-181">**Type colors that work**</span></span>
* <span data-ttu-id="f56f1-182">White</span><span class="sxs-lookup"><span data-stu-id="f56f1-182">White</span></span>
* <span data-ttu-id="f56f1-183">黒</span><span class="sxs-lookup"><span data-stu-id="f56f1-183">Black</span></span>
* <span data-ttu-id="f56f1-184">度の低い彩度の色を明るい</span><span class="sxs-lookup"><span data-stu-id="f56f1-184">Bright semi-saturated color</span></span>

<span data-ttu-id="f56f1-185">![作業の色を入力します。](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f56f1-185">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="f56f1-186">*作業の種類の色*</span><span class="sxs-lookup"><span data-stu-id="f56f1-186">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="f56f1-187">避けるべきこと</span><span class="sxs-lookup"><span data-stu-id="f56f1-187">What to avoid</span></span>

<span data-ttu-id="f56f1-188">**問題を引き起こす種類の色**</span><span class="sxs-lookup"><span data-stu-id="f56f1-188">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="f56f1-189">中間トーン</span><span class="sxs-lookup"><span data-stu-id="f56f1-189">Mid-tones</span></span>
* <span data-ttu-id="f56f1-190">灰色</span><span class="sxs-lookup"><span data-stu-id="f56f1-190">Gray</span></span>
* <span data-ttu-id="f56f1-191">彩度が過剰または再度が下げられた色</span><span class="sxs-lookup"><span data-stu-id="f56f1-191">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="f56f1-192">![問題を引き起こす色を入力します。](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f56f1-192">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="f56f1-193">*問題を引き起こす種類の色*</span><span class="sxs-lookup"><span data-stu-id="f56f1-193">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="f56f1-194">照明</span><span class="sxs-lookup"><span data-stu-id="f56f1-194">Lighting</span></span>

<span data-ttu-id="f56f1-195">アプリ起動ツールのライティング、Cliff 家環境に由来します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-195">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="f56f1-196">光と影の両方で問題がなくなるため、家全体で複数の場所で、ランチャーをテストすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-196">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="f56f1-197">良い知らせは、このドキュメントでその他の設計ガイダンスに従った場合、ランチャー、Cliff 家でほとんどの照明の形をとても良いです。</span><span class="sxs-lookup"><span data-stu-id="f56f1-197">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="f56f1-198">テスト環境でさまざまなライトで、ランチャーの外観に適した場所は、メディアのルーム、外側の任意の場所と、戻すテラス (芝生の上の具体的な領域) に、Studio です。</span><span class="sxs-lookup"><span data-stu-id="f56f1-198">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="f56f1-199">別の適切なテストでは、半分の光と影の半分に配置し、どのように見えるを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f56f1-199">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="f56f1-200">![光と影の両方で、ランチャーが問題を確認します。](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f56f1-200">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="f56f1-201">*光と影の両方で、ランチャーが問題かどうかを確認します。*</span><span class="sxs-lookup"><span data-stu-id="f56f1-201">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="f56f1-202">テクスチャ リング</span><span class="sxs-lookup"><span data-stu-id="f56f1-202">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="f56f1-203">テクスチャの作成</span><span class="sxs-lookup"><span data-stu-id="f56f1-203">Authoring your textures</span></span>

<span data-ttu-id="f56f1-204">3D アプリ起動ツールの終了の形式を PBR (物理的に基づくレンダリング) パイプラインを使用して作成された .glb ファイルとなります。</span><span class="sxs-lookup"><span data-stu-id="f56f1-204">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="f56f1-205">これは、厄介なプロセスでは、まだ行っていない場合は、技術的なアーティストを採用する良い機会です。</span><span class="sxs-lookup"><span data-stu-id="f56f1-205">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="f56f1-206">場合は、勇敢な DIY-er、時間をかけて[調査および PBR 用語について説明します](http://wiki.polycount.com/wiki/PBR)と何が起こっているか、内部で開始する前にする際に役立つ一般的なミスを回避します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-206">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](http://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="f56f1-207">![例:新しいメモ アプリ](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="f56f1-207">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="f56f1-208">*新しいメモ 3D アプリ ランチャー例 (架空のアプリ)*</span><span class="sxs-lookup"><span data-stu-id="f56f1-208">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="f56f1-209">**オーサリング ツールをお勧めします**</span><span class="sxs-lookup"><span data-stu-id="f56f1-209">**Recommended authoring tool**</span></span>

<span data-ttu-id="f56f1-210">使用することをお勧めします。[物質のコピー/貼り付け](https://www.allegorithmic.com/products/substance-painter)Allegorithmic、最終的なファイルを作成しています。</span><span class="sxs-lookup"><span data-stu-id="f56f1-210">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="f56f1-211">物質ペインタ、ここで PBR シェーダーの作成に詳しくない場合、[チュートリアル](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-211">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="f56f1-212">(または[3D Coat](https://3dcoat.com/home/)、 [Quixel Suite 2](https://quixel.se/suite2/)、または[Marmoset Toolbag](https://www.marmoset.co/toolbag/)これらのいずれかの経験がある場合のように動作します)。</span><span class="sxs-lookup"><span data-stu-id="f56f1-212">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="f56f1-213">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="f56f1-213">Best practices</span></span>

* <span data-ttu-id="f56f1-214">PBR のアプリ ランチャー オブジェクトが作成された場合、は、Cliff 家環境に変換する非常に簡単ですがあります。</span><span class="sxs-lookup"><span data-stu-id="f56f1-214">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="f56f1-215">シェーダーが金属/粗さ作業の流れを指定してください:、Unreal PBR シェーダーが閉じる複製。</span><span class="sxs-lookup"><span data-stu-id="f56f1-215">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="f56f1-216">保持、テクスチャをエクスポートするときに、[推奨されるテクスチャ サイズ](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines)に注意してください。</span><span class="sxs-lookup"><span data-stu-id="f56f1-216">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="f56f1-217">リアルタイムの光、オブジェクトを構築することを確認、つまり。</span><span class="sxs-lookup"><span data-stu-id="f56f1-217">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="f56f1-218">ベークド shadows – や影を描画しないように</span><span class="sxs-lookup"><span data-stu-id="f56f1-218">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="f56f1-219">テクスチャでベークド照明を回避します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-219">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="f56f1-220">パッケージを作成する PBR 材料の 1 つを使用して、シェーダーの生成された適切なマップを取得するには</span><span class="sxs-lookup"><span data-stu-id="f56f1-220">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="f56f1-221">関連項目</span><span class="sxs-lookup"><span data-stu-id="f56f1-221">See also</span></span>

* [<span data-ttu-id="f56f1-222">複合現実を自宅で使用するための 3D モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-222">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="f56f1-223">3D アプリ ランチャー (UWP アプリ) の実装します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-223">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="f56f1-224">3D アプリ ランチャー (Win32 アプリ) の実装します。</span><span class="sxs-lookup"><span data-stu-id="f56f1-224">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
