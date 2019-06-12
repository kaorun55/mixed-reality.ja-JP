---
title: カスタムのホーム環境を追加します。
description: 提供 Windows Mixed Reality ホーム環境、だけでなく、作成と使用、独自に実験できます。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、仮想現実、VR、MR、ホーム、カスタム環境、場所、cliff 家、skyloft、ユーザーの作成
ms.openlocfilehash: 8f5a3a1bdf5728260b0b7717c74a50f3356ca04a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829640"
---
# <a name="add-custom-home-environments"></a><span data-ttu-id="84a73-104">カスタムのホーム環境を追加します。</span><span class="sxs-lookup"><span data-stu-id="84a73-104">Add custom home environments</span></span>

>[!NOTE]
><span data-ttu-id="84a73-105">これは、試験的な機能です。</span><span class="sxs-lookup"><span data-stu-id="84a73-105">This is an experimental feature.</span></span> <span data-ttu-id="84a73-106">試してみてくださいと、楽しみが想定どおりすべて非常にうまくいかない場合も驚かないでください。</span><span class="sxs-lookup"><span data-stu-id="84a73-106">Give it a try and have fun with it, but don't be surprised if everything doesn't quite work as expected.</span></span> <span data-ttu-id="84a73-107">この機能とこれを使用して、関心の有効性を評価してについてお聞かせくださいエクスペリエンス (および見つかったバグ) で、[デベロッパー フォーラム](https://forums.hololens.com/categories/custom-home-environments)します。</span><span class="sxs-lookup"><span data-stu-id="84a73-107">We're evaluating the viability of this feature and interest in using it, so please tell us about your experience (and any bugs you've found) in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

<span data-ttu-id="84a73-108">以降では、 [Windows 10 April 2018 update](#release-notes-april-2018.md)、として使用するカスタム環境を ([スタート] メニューの) 場所の選択に追加することができます、試験的な機能を有効にしたこと、 [Windows Mixed Reality ホーム](#navigating-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="84a73-108">Starting with the [Windows 10 April 2018 update](#release-notes-april-2018.md), we've enabled an experimental feature that lets you add custom environments to the Places picker (on the Start menu) to use as the [Windows Mixed Reality home](#navigating-the-windows-mixed-reality-home.md).</span></span> <span data-ttu-id="84a73-109">Windows Mixed Reality は、2 つの既定の環境、Cliff 家と Skyloft、自宅として選択することができます。</span><span class="sxs-lookup"><span data-stu-id="84a73-109">Windows Mixed Reality has two default environments, Cliff House and Skyloft, that you can choose as your home.</span></span> <span data-ttu-id="84a73-110">カスタム環境を作成すると、独自の作成とその一覧を展開できます。</span><span class="sxs-lookup"><span data-stu-id="84a73-110">Creating custom environments allows you to expand that list with your own creations.</span></span> <span data-ttu-id="84a73-111">弊社が使用できるようにこの初期状態の作成者と開発者が関心を評価し、世界の種類を作成、およびさまざまなオーサリング ツールを操作する方法を理解するを参照してください。</span><span class="sxs-lookup"><span data-stu-id="84a73-111">We are making this available in an early state to evaluate interest from creators and developers, see what kinds of worlds you create, and understand how you work with different authoring tools.</span></span>

<span data-ttu-id="84a73-112">その teleporting わかりますカスタム環境を使用する場合、アプリと対話して、ホログラムを配置することは、Cliff 家と Skyloft で同様は機能します。</span><span class="sxs-lookup"><span data-stu-id="84a73-112">When using a custom environment you'll notice that teleporting, interacting with apps, and placing holograms works just like it does in the Cliff House and Skyloft.</span></span> <span data-ttu-id="84a73-113">ファンタジー ランドス ケープで web を参照するかと同じ市を塗りつぶすホログラム -、可能性は無限大です!</span><span class="sxs-lookup"><span data-stu-id="84a73-113">You can browse the web in a fantasy landscape or fill a futuristic city with holograms - the possibilities are endless!</span></span>

## <a name="device-support"></a><span data-ttu-id="84a73-114">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="84a73-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="84a73-115"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="84a73-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="84a73-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="84a73-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="84a73-117"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="84a73-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="84a73-118">カスタムのホーム環境</span><span class="sxs-lookup"><span data-stu-id="84a73-118">Custom home environments</span></span></td>
        <td><span data-ttu-id="84a73-119">❌</span><span class="sxs-lookup"><span data-stu-id="84a73-119">❌</span></span></td>
        <td><span data-ttu-id="84a73-120">✔️</span><span class="sxs-lookup"><span data-stu-id="84a73-120">✔️</span></span></td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a><span data-ttu-id="84a73-121">サンプル環境をしようとしてください。</span><span class="sxs-lookup"><span data-stu-id="84a73-121">Trying a sample environment</span></span>

<span data-ttu-id="84a73-122">カスタム ホーム環境の創造的な可能性のいくつかを示すサンプル環境を作成しました。</span><span class="sxs-lookup"><span data-stu-id="84a73-122">We've created a sample environment that shows off some of the creative possibilities of custom home environments.</span></span> <span data-ttu-id="84a73-123">試してみるにこれらの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="84a73-123">Follow these steps to try it out:</span></span>
1. <span data-ttu-id="84a73-124">[このサンプルのファンタジー島環境をダウンロード](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe)(自己解凍実行可能ファイルにリンクがポイント)。</span><span class="sxs-lookup"><span data-stu-id="84a73-124">[Download our sample Fantasy Island environment](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (link points to self-extracting executable).</span></span>

    <span data-ttu-id="84a73-125">![Fantasy 島サンプル環境](images/FantasyLand.jpg)</span><span class="sxs-lookup"><span data-stu-id="84a73-125">![Fantasy Island sample environment](images/FantasyLand.jpg)</span></span><br>
    <span data-ttu-id="84a73-126">*Fantasy 島サンプル環境*</span><span class="sxs-lookup"><span data-stu-id="84a73-126">*Fantasy Island sample environment*</span></span><br>

2. <span data-ttu-id="84a73-127">実行、 **Fantasy_Island.exe**ダウンロードしたファイル。</span><span class="sxs-lookup"><span data-stu-id="84a73-127">Run the **Fantasy_Island.exe** file you just downloaded.</span></span>

    > [!NOTE]
    > <span data-ttu-id="84a73-128">(次のような) web からダウンロードされると .exe ファイルを実行しようとすると、「Windows は、お使いの PC を保護」のポップアップが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="84a73-128">When attempting to run a .exe file downloaded from the web (like this one), you may encounter a "Windows protected your PC" pop-up.</span></span> <span data-ttu-id="84a73-129">このポップアップから Fantasy_Island.exe を実行する選択**詳細については**し**実行**します。</span><span class="sxs-lookup"><span data-stu-id="84a73-129">To run Fantasy_Island.exe from this pop-up, select **More info** and then **Run anyway**.</span></span> <span data-ttu-id="84a73-130">これを信頼したくないファイルのダウンロードを防ぐためにこのセキュリティ設定は、ファイルのソースを信頼するときに、のみこのオプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="84a73-130">This security setting is meant to protect you from downloading files you may not want to trust, so please only choose this option when you trust the source of the file.</span></span>

3. <span data-ttu-id="84a73-131">開いている**ファイル エクスプ ローラー** 、アドレス バーで、次を貼り付けることによって、環境フォルダーに移動します:`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`します。</span><span class="sxs-lookup"><span data-stu-id="84a73-131">Open **File Explorer** and navigate to the environments folder by pasting the following in the address bar: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.</span></span>
4. <span data-ttu-id="84a73-132">このフォルダーにダウンロードしたサンプル環境をコピーします。</span><span class="sxs-lookup"><span data-stu-id="84a73-132">Copy the sample environment that you downloaded into this folder.</span></span>
5. <span data-ttu-id="84a73-133">再起動**現実ポータルを混合**します。</span><span class="sxs-lookup"><span data-stu-id="84a73-133">Restart **Mixed Reality Portal**.</span></span> <span data-ttu-id="84a73-134">これにより、場所の選択で環境の一覧が更新されます。</span><span class="sxs-lookup"><span data-stu-id="84a73-134">This will refresh the list of environments in the Places picker.</span></span>
6. <span data-ttu-id="84a73-135">ヘッドセットに配置します。</span><span class="sxs-lookup"><span data-stu-id="84a73-135">Put on your headset.</span></span> <span data-ttu-id="84a73-136">自宅であなたを開く、 **[スタート] メニュー**コント ローラーの Windows を使用してボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="84a73-136">Once you're in the home, open the **Start menu** using the Windows button your controller.</span></span>
7. <span data-ttu-id="84a73-137">選択、**場所**ホーム環境を選択してピン留めされたアプリの一覧の上のアイコン。</span><span class="sxs-lookup"><span data-stu-id="84a73-137">Select the **Places** icon above the list of pinned apps to choose a home environment.</span></span>
8. <span data-ttu-id="84a73-138">場所の一覧でダウンロードしたファンタジー島環境が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84a73-138">You will find the Fantasy Island environment that you downloaded in your list of places.</span></span> <span data-ttu-id="84a73-139">選択**ファンタジー島**新しいカスタム ホーム環境を入力します。</span><span class="sxs-lookup"><span data-stu-id="84a73-139">Select **Fantasy Island** to enter your new custom home environment!</span></span>

## <a name="creating-your-own-custom-environment"></a><span data-ttu-id="84a73-140">独自のカスタム環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="84a73-140">Creating your own custom environment</span></span>

<span data-ttu-id="84a73-141">に加えて、サンプル環境を使用して、ソフトウェアの編集、お気に入りの 3D を使用して、独自のカスタム環境をエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="84a73-141">In addition to using our sample environments, you can export your own custom environments using your favorite 3D editing software.</span></span> 

### <a name="modeling-guidelines"></a><span data-ttu-id="84a73-142">モデリングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="84a73-142">Modeling guidelines</span></span>

<span data-ttu-id="84a73-143">お客様の環境をモデル化する場合は、次の推奨事項に注意してください。</span><span class="sxs-lookup"><span data-stu-id="84a73-143">When modeling your environment, keep the following recommendations in mind.</span></span> <span data-ttu-id="84a73-144">ユーザーを産み落とす believably 規模の世界で正しい向きにすることができます。</span><span class="sxs-lookup"><span data-stu-id="84a73-144">This will help ensure the user spawns in the correct orientation in a believably-sized world:</span></span>

1. <span data-ttu-id="84a73-145">ユーザーは、原点の周囲の生成に必要な場所に 0,0,0 は center で生成されます。</span><span class="sxs-lookup"><span data-stu-id="84a73-145">Users will spawn at 0,0,0 so center your desired spawn location around the origin.</span></span>
2. <span data-ttu-id="84a73-146">世界規模で資産を作成できるように、メーター作業単位を設定してください。</span><span class="sxs-lookup"><span data-stu-id="84a73-146">Working Units should be set to meters so that assets can be authored at world scale.</span></span>
3. <span data-ttu-id="84a73-147">アップ軸は、"Y"に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84a73-147">The Up axis should be set to “Y”.</span></span>
4. <span data-ttu-id="84a73-148">資産は、正の Z 軸方向に"forward"に直面する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84a73-148">The asset should face “forward” towards the positive Z axis.</span></span>
5. <span data-ttu-id="84a73-149">すべてのメッシュは、結合する必要はありませんが、リソースが限られたデバイスを対象としている場合をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="84a73-149">All meshes do not need to be combined, but it is recommended if you are targeting resource-constrained devices.</span></span>

### <a name="exporting-your-environment"></a><span data-ttu-id="84a73-150">お客様の環境をエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="84a73-150">Exporting your environment</span></span>

<span data-ttu-id="84a73-151">Windows Mixed Reality は、環境の資産の配信形式としてバイナリ glTF (.glb) に依存します。</span><span class="sxs-lookup"><span data-stu-id="84a73-151">Windows Mixed Reality relies on binary glTF (.glb) as the asset delivery format for environments.</span></span> <span data-ttu-id="84a73-152">glTF は、使用料無料のオープン標準の 3D アセットの配信 Khronos グループによって管理されます。</span><span class="sxs-lookup"><span data-stu-id="84a73-152">glTF is a royalty free open standard for 3D asset delivery maintained by the Khronos group.</span></span> <span data-ttu-id="84a73-153">Windows アプリおよびエクスペリエンスの間での形式については、マイクロソフトのサポートはため glTF の進化に伴って相互運用可能な 3D コンテンツの業界標準として、します。</span><span class="sxs-lookup"><span data-stu-id="84a73-153">As glTF evolves as an industry standard for interoperable 3D content, so will Microsoft’s support for the format across Windows apps and experiences.</span></span>

<span data-ttu-id="84a73-154">カスタムのホーム環境として使用するアセットをエクスポートする最初の手順は、glTF 2.0 モデルを生成しています。</span><span class="sxs-lookup"><span data-stu-id="84a73-154">The first step in exporting assets to be used as custom home environments is generating a glTF 2.0 model.</span></span> <span data-ttu-id="84a73-155">GlTF ワーキング グループの管理、[サポートされているエクスポーターとコンバーターの一覧](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)glTF 2.0 モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="84a73-155">The glTF working group maintains a [list of supported exporters and converters](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) to create a glTF 2.0 model.</span></span> <span data-ttu-id="84a73-156">最初に、このページに記載されているプログラムのいずれかを使用して作成し、glTF 2.0 モデルをエクスポートまたはサポートされているコンバーターのいずれかを使用して既存のモデルに変換します。</span><span class="sxs-lookup"><span data-stu-id="84a73-156">To get started, use one of the programs listed on this page to create and export a glTF 2.0 model, or convert an existing model using one of the supported converters.</span></span>

<span data-ttu-id="84a73-157">さらに、チェック アウト[この便利な記事](https://www.khronos.org/blog/art-pipeline-for-gltf)Blender や 3 ds から glTF モデルをエクスポートするため、アート ワークフローの概要を説明する直接 Max です。</span><span class="sxs-lookup"><span data-stu-id="84a73-157">Additionally, check out [this helpful article](https://www.khronos.org/blog/art-pipeline-for-gltf) which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.</span></span> 

### <a name="environment-limits"></a><span data-ttu-id="84a73-158">環境の制限</span><span class="sxs-lookup"><span data-stu-id="84a73-158">Environment limits</span></span>

<span data-ttu-id="84a73-159">すべての環境は、< 256 mb である必要があります。</span><span class="sxs-lookup"><span data-stu-id="84a73-159">All environments must be < 256 mbs.</span></span> <span data-ttu-id="84a73-160">256 mb を超える環境は、ユーザーを囲む既定スカイ ボックスだけで、空の世界にフォールバックを読み込みは失敗します。</span><span class="sxs-lookup"><span data-stu-id="84a73-160">Environments larger than 256 mbs will fail to load and fall back to an empty world with just the default skybox surrounding the user.</span></span> <span data-ttu-id="84a73-161">ください、モデルを作成するときに、このファイルのサイズ制限に注意してください。</span><span class="sxs-lookup"><span data-stu-id="84a73-161">Please keep this file size limit in mind when creating your models.</span></span> <span data-ttu-id="84a73-162">さらに、以下に示すように、WindowsMRAssetConverter を使用して環境を最適化する場合は、できなければ、オプティマイザー、大きなファイルサイズが読み込みも高速のテクスチャが作成されると、テクスチャのサイズが増加します。</span><span class="sxs-lookup"><span data-stu-id="84a73-162">Additionally, if you plan to optimize your environment using the WindowsMRAssetConverter as described below, be cognizant that the texture size will increase as the optimizer creates textures that have a larger file size, but load faster.</span></span> 

### <a name="optimizing-your-environment"></a><span data-ttu-id="84a73-163">お客様の環境を最適化します。</span><span class="sxs-lookup"><span data-stu-id="84a73-163">Optimizing your environment</span></span>

<span data-ttu-id="84a73-164">Windows Mixed Reality は、いくつかの環境の読み込み時間が大幅に低下する省略可能な最適化をサポートします。</span><span class="sxs-lookup"><span data-stu-id="84a73-164">Windows Mixed Reality supports a number of optional optimizations that will significantly reduce the load time of your environments.</span></span> <span data-ttu-id="84a73-165">これは、読み込み中にタイムアウトになる場合がありますが、多くのテクスチャでは、使用環境にとって特に重要です。</span><span class="sxs-lookup"><span data-stu-id="84a73-165">This can be especially important for environments with many textures, as they will sometimes time out while loading.</span></span> <span data-ttu-id="84a73-166">一般に、すべての資産に対してこの手順をお勧め、ただし、いくつか、または低解像度のテクスチャで小規模な環境常に必要としないことです。</span><span class="sxs-lookup"><span data-stu-id="84a73-166">In general, we recommend this step for all assets, however, smaller environments with few or low-resolution textures won't always require it.</span></span> 

<span data-ttu-id="84a73-167">このプロセスを簡単に作成しました、 [Windows Mixed Reality 資産コンバーター (GitHub で入手できます)](https://github.com/Microsoft/glTF-Toolkit/releases)最適化を実行します。</span><span class="sxs-lookup"><span data-stu-id="84a73-167">To make this process easier, we have created the [Windows Mixed Reality Asset Converter (available on GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) to perform your optimizations.</span></span> <span data-ttu-id="84a73-168">このツールは、追加のテクスチャのパッキング、圧縮および解像度のスケールを実行することによって、標準の 2.0 glTF や .glb を最適化するために、Microsoft glTF toolkit で使用可能なユーティリティのセットを使用します。</span><span class="sxs-lookup"><span data-stu-id="84a73-168">This tool uses a set of utilities available in the Microsoft glTF toolkit to optimize any standard 2.0 glTF or .glb by performing an additional texture packing, compression and resolution down-scaling.</span></span> 

<span data-ttu-id="84a73-169">コンバーターには、さまざまな最適化の正確な動作を調整するためのフラグがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="84a73-169">The converter currently supports a number of flags to tweak the exact behavior of the optimizations.</span></span> <span data-ttu-id="84a73-170">最良の結果を次のフラグ付きの実行をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="84a73-170">We recommend running with the following flags for best results:</span></span>

<span data-ttu-id="84a73-171">Flag</span><span class="sxs-lookup"><span data-stu-id="84a73-171">Flag</span></span>|<span data-ttu-id="84a73-172">推奨値</span><span class="sxs-lookup"><span data-stu-id="84a73-172">Recommended Value(s)</span></span>|<span data-ttu-id="84a73-173">説明</span><span class="sxs-lookup"><span data-stu-id="84a73-173">Description</span></span>
---|---|---
<span data-ttu-id="84a73-174">-max-texture-size</span><span class="sxs-lookup"><span data-stu-id="84a73-174">-max-texture-size</span></span>|<span data-ttu-id="84a73-175">1024 または 2048</span><span class="sxs-lookup"><span data-stu-id="84a73-175">1024 or 2048</span></span>| <span data-ttu-id="84a73-176">このテクスチャの品質を向上させるために調整、既定値は 512 x 512 します。</span><span class="sxs-lookup"><span data-stu-id="84a73-176">Tweak this to improve the quality of the textures, default is 512x512.</span></span> <span data-ttu-id="84a73-177">大きい値は、環境のファイル サイズに影響が大幅にことに注意してください。 保管しておいて、256 mb の制限に注意してください。</span><span class="sxs-lookup"><span data-stu-id="84a73-177">Note that a larger value will significantly impact the file size of the environment so keep the 256 mb limit in mind</span></span>
<span data-ttu-id="84a73-178">最小バージョン</span><span class="sxs-lookup"><span data-stu-id="84a73-178">-min-version</span></span>|<span data-ttu-id="84a73-179">1803</span><span class="sxs-lookup"><span data-stu-id="84a73-179">1803</span></span>|<span data-ttu-id="84a73-180">カスタム環境は windows のバージョンでのみサポートされます > 1803 を = です。</span><span class="sxs-lookup"><span data-stu-id="84a73-180">Custom environments are only supported on versions of windows >= 1803.</span></span> <span data-ttu-id="84a73-181">このフラグは以前のバージョンのテクスチャを削除して、最終的な資産のファイル サイズを縮小</span><span class="sxs-lookup"><span data-stu-id="84a73-181">This flag will remove textures for older versions and reduce the file size of the final asset</span></span>

<span data-ttu-id="84a73-182">例:</span><span class="sxs-lookup"><span data-stu-id="84a73-182">For example:</span></span>

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a><span data-ttu-id="84a73-183">環境をテストします。</span><span class="sxs-lookup"><span data-stu-id="84a73-183">Testing your environment</span></span>

<span data-ttu-id="84a73-184">最終的な .glb 環境を作成したら、ヘッドセットでテストを実行する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="84a73-184">Once you have your final .glb environment you're ready to test it out in the headset.</span></span> <span data-ttu-id="84a73-185">手順 2. で始まり、 [「サンプル環境をしようとした」](#trying-a-sample-environment)ホーム複合現実として、カスタム環境を使用するセクション。</span><span class="sxs-lookup"><span data-stu-id="84a73-185">Start at step 2 in the ["Trying a sample environment"](#trying-a-sample-environment) section to use your custom environment as the mixed reality home.</span></span> 

## <a name="feedback"></a><span data-ttu-id="84a73-186">Feedback</span><span class="sxs-lookup"><span data-stu-id="84a73-186">Feedback</span></span>

<span data-ttu-id="84a73-187">この実験的な機能を評価して、私たちは、バグが発生する可能性のカスタム環境を使用している方法に興味を持つと、機能方法を指定してください。</span><span class="sxs-lookup"><span data-stu-id="84a73-187">While we're evaluating this experimental feature, we're interested in learning how you're using custom environments, any bugs you may encounter, and how you like the feature.</span></span> <span data-ttu-id="84a73-188">作成すると、カスタム ホーム環境を使用して、あらゆるフィードバックを共有してください、[デベロッパー フォーラム](https://forums.hololens.com/categories/custom-home-environments)します。</span><span class="sxs-lookup"><span data-stu-id="84a73-188">Please share any and all feedback for creating and using custom home environments in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

## <a name="troubleshooting-and-tips"></a><span data-ttu-id="84a73-189">トラブルシューティングとヒント</span><span class="sxs-lookup"><span data-stu-id="84a73-189">Troubleshooting and tips</span></span>

### <a name="how-do-i-change-the-name-of-the-environment"></a><span data-ttu-id="84a73-190">環境の名前を変更する方法はありますか</span><span class="sxs-lookup"><span data-stu-id="84a73-190">How do I change the name of the environment?</span></span>

<span data-ttu-id="84a73-191">[環境] フォルダー内のファイル名は、場所の選択に適用されます。</span><span class="sxs-lookup"><span data-stu-id="84a73-191">The file name in the environments folder will be used in the Places picker.</span></span> <span data-ttu-id="84a73-192">環境の名前を変更するには、は、単に名前変更、環境は、ファイル名をし、し、Mixed Reality ポータルを再起動します。</span><span class="sxs-lookup"><span data-stu-id="84a73-192">To change the name of your environment simply rename the environment file name, and then restart Mixed Reality Portal.</span></span>

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a><span data-ttu-id="84a73-193">マイ プレース ピッカーからのカスタム環境を削除する方法</span><span class="sxs-lookup"><span data-stu-id="84a73-193">How do I remove custom environments from my Places picker?</span></span>

<span data-ttu-id="84a73-194">カスタム環境を削除するには、お使いの PC 上のフォルダーに環境を開きます (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) し、環境を削除します。</span><span class="sxs-lookup"><span data-stu-id="84a73-194">To remove a custom environment, open the environments folder on your PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) and delete the environment.</span></span> <span data-ttu-id="84a73-195">Mixed Reality ポータルを再起動するとこの環境は不要になった場所ピッカーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="84a73-195">Once you restart Mixed Reality Portal, this environment will no longer appear in the Places picker.</span></span> 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a><span data-ttu-id="84a73-196">私のお気に入りのカスタム環境を既定する方法は?</span><span class="sxs-lookup"><span data-stu-id="84a73-196">How do I default to my favorite custom environment?</span></span>

<span data-ttu-id="84a73-197">現在、既定の環境を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="84a73-197">You can't currently change the default environment.</span></span> <span data-ttu-id="84a73-198">混合の現実ポータルを再起動するたびに Cliff 家環境に返されるされます。</span><span class="sxs-lookup"><span data-stu-id="84a73-198">Each time you restart Mixed Reality Portal, you will be returned to the Cliff House environment.</span></span> 

### <a name="i-spawn-into-a-blank-space"></a><span data-ttu-id="84a73-199">空白の領域に生成します。</span><span class="sxs-lookup"><span data-stu-id="84a73-199">I spawn into a blank space</span></span>

<span data-ttu-id="84a73-200">Windows Mixed Reality [256 mb を超える環境をサポートしていない](#environment-limits)します。</span><span class="sxs-lookup"><span data-stu-id="84a73-200">Windows Mixed Reality [doesn't support environments that exceed 256 mb](#environment-limits).</span></span> <span data-ttu-id="84a73-201">環境では、この制限を超えているときに、モデルのない空のスカイ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="84a73-201">When an environment exceeds this limit, you will land in the empty sky box with no model.</span></span>

### <a name="it-takes-a-long-time-to-load-my-environment"></a><span data-ttu-id="84a73-202">自分の環境を読み込みに長い時間がかかる</span><span class="sxs-lookup"><span data-stu-id="84a73-202">It takes a long time to load my environment</span></span>

<span data-ttu-id="84a73-203">省略可能な最適化は、読み込みも高速にする環境に追加できます。</span><span class="sxs-lookup"><span data-stu-id="84a73-203">You can add optional optimizations to your environment to make it load faster.</span></span> <span data-ttu-id="84a73-204">参照してください[「環境の最適化」](#optimizing-your-environment)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="84a73-204">See ["Optimizing your environment"](#optimizing-your-environment) for details.</span></span>

### <a name="the-scale-of-my-environment-is-incorrect"></a><span data-ttu-id="84a73-205">自分の環境内の小数点以下桁数が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="84a73-205">The scale of my environment is incorrect</span></span>

<span data-ttu-id="84a73-206">Windows Mixed Reality 環境の読み込み時に 1 メートルに glTF 単位の平行移動します。</span><span class="sxs-lookup"><span data-stu-id="84a73-206">Windows Mixed Reality translates glTF units to 1 meter when loading environments.</span></span> <span data-ttu-id="84a73-207">環境内で、予期しないスケールを再確認することを確認する、エクスポーターが読み込まれる場合は、1 m 規模でモデル化をでしょう。</span><span class="sxs-lookup"><span data-stu-id="84a73-207">If your environment loads up an unexpected scale, double check your exporter to ensure that you're modeling at a 1 meter scale.</span></span> 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a><span data-ttu-id="84a73-208">私の環境での生成場所が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="84a73-208">The spawn location in my environment is incorrect</span></span>

<span data-ttu-id="84a73-209">既定の生成場所は、環境で 0,0,0 にあります。</span><span class="sxs-lookup"><span data-stu-id="84a73-209">The default spawn location is located at 0,0,0 in the environment.</span></span> <span data-ttu-id="84a73-210">その現在できない配信元の生成に必要なポイントに配置されると、環境をエクスポートすることによって、起動ポイントを変更する必要がありますので、この場所をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="84a73-210">Its not currently possible to customize this location, so you must modify the spawn point by exporting your environment with the origin positioned at the desired spawn point.</span></span>

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a><span data-ttu-id="84a73-211">環境内の適切なオーディオとは言えません</span><span class="sxs-lookup"><span data-stu-id="84a73-211">The audio doesn't sound correct in the environment</span></span>

<span data-ttu-id="84a73-212">カスタム環境を作成するときに作成した物理領域に一致しない音響学のレンダリング シミュレーション使用します。</span><span class="sxs-lookup"><span data-stu-id="84a73-212">When you create your custom environment, it will be using an acoustics rendering simulation that does not match the physical space you have created.</span></span> <span data-ttu-id="84a73-213">サウンドが間違った方向から取得したものし、思われるかもしれませんがこもった感じです。</span><span class="sxs-lookup"><span data-stu-id="84a73-213">Sound may come from the wrong directions and may sound muffled.</span></span> 

## <a name="see-also"></a><span data-ttu-id="84a73-214">関連項目</span><span class="sxs-lookup"><span data-stu-id="84a73-214">See also</span></span>
* [<span data-ttu-id="84a73-215">実際にはホームを混合するウィンドウを移動します。</span><span class="sxs-lookup"><span data-stu-id="84a73-215">Navigating the Windows Mixed Reality Home</span></span>](#navigating-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="84a73-216">Windows (GitHub 上) 資産コンバーターを現実の混在</span><span class="sxs-lookup"><span data-stu-id="84a73-216">Windows Mixed Reality Asset Converter (on GitHub)</span></span>](https://github.com/Microsoft/glTF-Toolkit/releases)

