---
title: Unity 内のテキスト
description: Unity では、テキストを表示するには、2 種類のテキストのコンポーネントを使用することができますが、UI テキストとテキストを 3D メッシュです。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、制御、フォント、文字体裁、ui、ux
ms.openlocfilehash: a601ab5ab5168f286a0935ca06eeec13022e1eee
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692335"
---
# <a name="text-in-unity"></a><span data-ttu-id="7411f-104">Unity 内のテキスト</span><span class="sxs-lookup"><span data-stu-id="7411f-104">Text in Unity</span></span>

<span data-ttu-id="7411f-105">テキストでは、holographic アプリで最も重要なコンポーネントの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="7411f-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="7411f-106">Unity では、テキストを表示するには、3 種類のテキストのコンポーネントを使用することができますが、UI テキスト、テキストを 3D メッシュ、およびテキスト メッシュ Pro します。</span><span class="sxs-lookup"><span data-stu-id="7411f-106">To display text in Unity, there are three types of text components you can use — UI Text, 3D Text Mesh, and Text Mesh Pro.</span></span> <span data-ttu-id="7411f-107">既定ではぼやけて表示される UI テキストとテキストを 3D メッシュし、が大きすぎます。</span><span class="sxs-lookup"><span data-stu-id="7411f-107">By default UI Text and 3D Text Mesh appear blurry and are too big.</span></span> <span data-ttu-id="7411f-108">HoloLens で管理しやすいサイズがシャープな高品質のテキストを取得するいくつかの変数を調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7411f-108">You need to tweak a few variables to get sharp, high-quality text that has a manageable size in HoloLens.</span></span> <span data-ttu-id="7411f-109">UI テキストとテキストのメッシュの 3D のコンポーネントを使用する場合は、適切なサイズを取得するスケール ファクターを適用すると、レンダリングの品質が向上を実現できます。</span><span class="sxs-lookup"><span data-stu-id="7411f-109">By applying scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components, you can achieve better rendering quality.</span></span>

<span data-ttu-id="7411f-110">![鋭いと美しいテキストを取得する方法](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="7411f-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="7411f-111">*Unity でぼやけての既定のテキスト*</span><span class="sxs-lookup"><span data-stu-id="7411f-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a><span data-ttu-id="7411f-112">Unity の 3D テキスト (テキスト メッシュ) と UI テキスト操作</span><span class="sxs-lookup"><span data-stu-id="7411f-112">Working with Unity's 3D Text(Text Mesh) and UI Text</span></span>

<span data-ttu-id="7411f-113">Unity では、シーンに追加されたすべての新しい要素が 1 の Unity 単位のサイズ、または 100% の変換スケールは、HoloLens に約 1 メートルに変換を前提としています。</span><span class="sxs-lookup"><span data-stu-id="7411f-113">Unity assumes all new elements added to a scene are 1 Unity Unit in size, or 100% transform scale, which translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="7411f-114">場合は、フォント 3D TextMesh の境界ボックスは既定では約 1 メートルの高さ。</span><span class="sxs-lookup"><span data-stu-id="7411f-114">In the case of fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="7411f-115">![Unity でのフォントを操作します。](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="7411f-115">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="7411f-116">*既定の Unity 3D テキスト (テキスト メッシュ) が占める 1 メートルである 1 の Unity ユニット*</span><span class="sxs-lookup"><span data-stu-id="7411f-116">*Default Unity 3D Text (Text Mesh) occupies 1 Unity Unit which is 1 meter*</span></span>

<br>
<span data-ttu-id="7411f-117">ほとんどのビジュアル デザイナーは、現実の世界でフォント サイズを定義するのにポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7411f-117">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="7411f-118">約 2835 (2,834.645666399962) がある 1 メートルのポイント。</span><span class="sxs-lookup"><span data-stu-id="7411f-118">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="7411f-119">1 m と Unity の既定のテキストのメッシュのフォント サイズ 13 からポイント システムへの変換に基づき、2835 equals 0.0046 (正確に 0.004586111116) で割った値 13 の単純な算術を提供する優れた標準スケールで開始する (一部は、0.005 に丸めるにすることがあります)。</span><span class="sxs-lookup"><span data-stu-id="7411f-119">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="7411f-120">テキスト オブジェクトまたはこれらの値にコンテナーをスケーリングのみを許可しませんフォントの 1 対 1 の変換は、デザイン プログラムのサイズもお客様のエクスペリエンス全体で一貫性を維持するために、標準を提供します。</span><span class="sxs-lookup"><span data-stu-id="7411f-120">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your experience.</span></span>

<span data-ttu-id="7411f-121">![別のフォント サイズである unity 3D テキスト メッシュ](images/Text_In_Unity_Measurements1.png)</span><span class="sxs-lookup"><span data-stu-id="7411f-121">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements1.png)</span></span><br>
<span data-ttu-id="7411f-122">*Unity 3D テキストと UI のテキストの値をスケーリング*</span><span class="sxs-lookup"><span data-stu-id="7411f-122">*Scaling values for the Unity 3D Text and UI Text*</span></span>

<span data-ttu-id="7411f-123">![別のフォント サイズである unity 3D テキスト メッシュ](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7411f-123">![Unity 3D Text Mesh with different font sizes](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="7411f-124">*最適化された値である unity 3D テキスト メッシュ*</span><span class="sxs-lookup"><span data-stu-id="7411f-124">*Unity 3D Text Mesh with optimized values*</span></span>

<br>
<span data-ttu-id="7411f-125">引き続き UI またはキャンバス ベースのテキストの要素をシーンに追加する際にサイズのような違いが大きいです。</span><span class="sxs-lookup"><span data-stu-id="7411f-125">When adding a UI or canvas based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="7411f-126">2 つのサイズの相違点が約 1000% を 0.00046 (正確に 0.0004586111116) に基づいた UI テキスト コンポーネントのスケール ファクターがもたらされるまたは 0.0005 の丸められた値。</span><span class="sxs-lookup"><span data-stu-id="7411f-126">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="7411f-127">![Unity の UI テキスト単位の値ごとに異なる複数の動的なピクセルを](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7411f-127">![Unity UI Text with different dynamic pixels per unit values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="7411f-128">*最適化された値を持つ unity UI テキスト*</span><span class="sxs-lookup"><span data-stu-id="7411f-128">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="7411f-129">任意のフォントの既定値は、そのフォントまたはフォントが Unity にインポートする方法のテクスチャのサイズによって影響可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7411f-129">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="7411f-130">これらのテストは、Unity では、既定の Arial フォントおよびその他のインポートされた 1 つのフォントにベースで実行されました。</span><span class="sxs-lookup"><span data-stu-id="7411f-130">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="working-with-text-mesh-pro"></a><span data-ttu-id="7411f-131">テキストの操作の Mesh Pro</span><span class="sxs-lookup"><span data-stu-id="7411f-131">Working with Text Mesh Pro</span></span>

<span data-ttu-id="7411f-132">Unity のテキストをメッシュ Pro で、テキストのレンダリング品質をセキュリティで保護することができます。</span><span class="sxs-lookup"><span data-stu-id="7411f-132">With Unity's Text Mesh Pro, you can secure the text rendering quality.</span></span> <span data-ttu-id="7411f-133">使用して、距離に関係なく鮮明なテキストのアウトラインがサポートしている、 [SDF (署名済み距離フィールド)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf)手法です。</span><span class="sxs-lookup"><span data-stu-id="7411f-133">It supports crisp text outline regardless of the distance using the [SDF(Signed Distance Field)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) technique.</span></span> <span data-ttu-id="7411f-134">UI テキストとテキストを 3D メッシュの上に使用した同じ計算メソッドを使用して、見つかったら従来的なタイポグラフィのポイントを使用する適切なスケーリングの値。</span><span class="sxs-lookup"><span data-stu-id="7411f-134">Using the same calculation method that we used above for the 3D Text Mesh and UI Text, we can find proper scaling values to use conventional typographic Point.</span></span> <span data-ttu-id="7411f-135">36 のサイズを既定の 3D テキスト メッシュ Pro フォントは、2.5 Unity Unit(2.5m) の境界を示しています、ため、ポイントのサイズを使用するのにスケールの値を 0.005 を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7411f-135">Since the default 3D Text Mesh Pro font with the size 36 shows the bounding of 2.5 Unity Unit(2.5m), we can use scaling value 0.005 to use the Point size.</span></span> <span data-ttu-id="7411f-136">既定のサイズの 25 の Unity Unit(25m) の境界が、テキスト メッシュ Pro [UI] メニューの。</span><span class="sxs-lookup"><span data-stu-id="7411f-136">The Text Mesh Pro under UI menu has the default bounding size of 25 Unity Unit(25m).</span></span> <span data-ttu-id="7411f-137">これにより 0.0005 のスケーリングの値。</span><span class="sxs-lookup"><span data-stu-id="7411f-137">This gives us 0.0005 for the scaling value.</span></span>

<span data-ttu-id="7411f-138">![別のフォント サイズである unity 3D テキスト メッシュ](images/Text_In_Unity_Measurements2.png)</span><span class="sxs-lookup"><span data-stu-id="7411f-138">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements2.png)</span></span><br>
<span data-ttu-id="7411f-139">*Unity 3D テキストと UI のテキストの値をスケーリング*</span><span class="sxs-lookup"><span data-stu-id="7411f-139">*Scaling values for the Unity 3D Text and UI Text*</span></span>

## <a name="recommended-text-size"></a><span data-ttu-id="7411f-140">推奨されるテキストのサイズ</span><span class="sxs-lookup"><span data-stu-id="7411f-140">Recommended text size</span></span>
<span data-ttu-id="7411f-141">予想されることができますの 2 m 離れた距離にある非常に小さく、PC またはタブレット デバイス (通常は 12: 32 ポイント) 間を参照してくださいで使用するサイズを入力します。</span><span class="sxs-lookup"><span data-stu-id="7411f-141">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="7411f-142">各フォントの特性によって異なりますが、一般に角度と読みやすさのフォントの高さを表示する推奨される最小値は、ユーザー調査研究に基づく 0.35°-0.4°/12.21-13.97mm の周囲にあります。</span><span class="sxs-lookup"><span data-stu-id="7411f-142">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="7411f-143">上で導入されたスケール ファクターで 35 40 pt を以下のです。</span><span class="sxs-lookup"><span data-stu-id="7411f-143">It is about 35-40pt with the scaling factor introduced above.</span></span> 

<span data-ttu-id="7411f-144">0.45m(45cm) でほぼ相互作用は、読みやすいフォントの最小の表示の角度と高さは 0.4 °-mm 0.5 °/3.14 – 3.9 です。</span><span class="sxs-lookup"><span data-stu-id="7411f-144">For the near interaction at 0.45m(45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="7411f-145">上で導入されたスケール ファクターでの 9-12 pt です。</span><span class="sxs-lookup"><span data-stu-id="7411f-145">It is about 9-12pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="7411f-146">![ここまでの相互作用範囲](images/typography-distance-1000px.jpg)
*の近くにあるコンテンツとの相互作用の範囲*</span><span class="sxs-lookup"><span data-stu-id="7411f-146">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="7411f-147">読みやすいフォントの最小サイズ</span><span class="sxs-lookup"><span data-stu-id="7411f-147">The minimum legible font size</span></span>
| <span data-ttu-id="7411f-148">距離</span><span class="sxs-lookup"><span data-stu-id="7411f-148">Distance</span></span> | <span data-ttu-id="7411f-149">表示角度</span><span class="sxs-lookup"><span data-stu-id="7411f-149">Viewing angle</span></span> | <span data-ttu-id="7411f-150">テキストの高さ</span><span class="sxs-lookup"><span data-stu-id="7411f-150">Text height</span></span> | <span data-ttu-id="7411f-151">フォント サイズ</span><span class="sxs-lookup"><span data-stu-id="7411f-151">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="7411f-152">45 cm (直接操作までの距離)</span><span class="sxs-lookup"><span data-stu-id="7411f-152">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="7411f-153">0.4°-0.5°</span><span class="sxs-lookup"><span data-stu-id="7411f-153">0.4°-0.5°</span></span> | <span data-ttu-id="7411f-154">3.14 – 3.9 mm</span><span class="sxs-lookup"><span data-stu-id="7411f-154">3.14–3.9mm</span></span> | <span data-ttu-id="7411f-155">8.9 – 11.13pt</span><span class="sxs-lookup"><span data-stu-id="7411f-155">8.9–11.13pt</span></span> |
| <span data-ttu-id="7411f-156">2 分</span><span class="sxs-lookup"><span data-stu-id="7411f-156">2m</span></span> | <span data-ttu-id="7411f-157">0.35°-0.4°</span><span class="sxs-lookup"><span data-stu-id="7411f-157">0.35°-0.4°</span></span> | <span data-ttu-id="7411f-158">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="7411f-158">12.21–13.97mm</span></span> | <span data-ttu-id="7411f-159">34.63-39.58pt</span><span class="sxs-lookup"><span data-stu-id="7411f-159">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="7411f-160">快適に読みやすいフォント サイズ</span><span class="sxs-lookup"><span data-stu-id="7411f-160">The comfortably legible font size</span></span>
| <span data-ttu-id="7411f-161">距離</span><span class="sxs-lookup"><span data-stu-id="7411f-161">Distance</span></span> | <span data-ttu-id="7411f-162">表示角度</span><span class="sxs-lookup"><span data-stu-id="7411f-162">Viewing angle</span></span> | <span data-ttu-id="7411f-163">テキストの高さ</span><span class="sxs-lookup"><span data-stu-id="7411f-163">Text height</span></span> | <span data-ttu-id="7411f-164">フォント サイズ</span><span class="sxs-lookup"><span data-stu-id="7411f-164">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="7411f-165">45 cm (直接操作までの距離)</span><span class="sxs-lookup"><span data-stu-id="7411f-165">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="7411f-166">0.65°-0.8°</span><span class="sxs-lookup"><span data-stu-id="7411f-166">0.65°-0.8°</span></span> | <span data-ttu-id="7411f-167">5.1-6.3 mm</span><span class="sxs-lookup"><span data-stu-id="7411f-167">5.1-6.3mm</span></span> | <span data-ttu-id="7411f-168">14.47-17.8pt</span><span class="sxs-lookup"><span data-stu-id="7411f-168">14.47-17.8pt</span></span> |
| <span data-ttu-id="7411f-169">2 分</span><span class="sxs-lookup"><span data-stu-id="7411f-169">2m</span></span> | <span data-ttu-id="7411f-170">0.6°-0.75°</span><span class="sxs-lookup"><span data-stu-id="7411f-170">0.6°-0.75°</span></span> | <span data-ttu-id="7411f-171">20.9 mm-26.2</span><span class="sxs-lookup"><span data-stu-id="7411f-171">20.9-26.2mm</span></span> | <span data-ttu-id="7411f-172">59.4-74.2pt</span><span class="sxs-lookup"><span data-stu-id="7411f-172">59.4-74.2pt</span></span> |

<span data-ttu-id="7411f-173">Segoe UI (Windows の既定のフォント) では、ほとんどの場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="7411f-173">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="7411f-174">ただし、振動シンの垂直線と読みやすさが低下するために、小さなサイズでライトまたは半の明るいフォント ファミリを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7411f-174">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="7411f-175">十分なストロークの太さで最新のフォントがうまく機能します。</span><span class="sxs-lookup"><span data-stu-id="7411f-175">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="7411f-176">たとえば、Helvetica と Arial すばらしい外観になります、通常または太字の重みを持つ、HoloLens で非常に判読可能。</span><span class="sxs-lookup"><span data-stu-id="7411f-176">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>


<span data-ttu-id="7411f-177">![角度を表示する](images/Text_In_Unity_ViewingAngle.jpg)
*距離、角度、およびテキストの高さを表示します。*</span><span class="sxs-lookup"><span data-stu-id="7411f-177">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="7411f-178">適切なディメンションとテキストのレンダリング品質をシャープな</span><span class="sxs-lookup"><span data-stu-id="7411f-178">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="7411f-179">作成しましたこれらスケーリング要因に基づき、 [UI テキストとテキストを 3D メッシュとテキストのプレハブ](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)します。</span><span class="sxs-lookup"><span data-stu-id="7411f-179">Based on these scaling factors, we have created [text prefabs with UI Text and 3D Text Mesh](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text).</span></span> <span data-ttu-id="7411f-180">開発者は、これらプレハブを使用して、シャープなテキストと一貫性のあるフォント サイズを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="7411f-180">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="7411f-181">![適切なディメンションとテキストのレンダリング品質をシャープな](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7411f-181">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="7411f-182">*適切なディメンションとテキストのレンダリング品質をシャープな*</span><span class="sxs-lookup"><span data-stu-id="7411f-182">*Sharp text rendering quality with proper dimension*</span></span>

## <a name="shader-with-occlusion-support"></a><span data-ttu-id="7411f-183">シェーダー オクルー ジョン サポート</span><span class="sxs-lookup"><span data-stu-id="7411f-183">Shader with occlusion support</span></span>

<span data-ttu-id="7411f-184">Unity の既定のフォントの材料は、オクルー ジョンをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="7411f-184">Unity's default font material does not support occlusion.</span></span> <span data-ttu-id="7411f-185">このため、既定では、オブジェクトの背後にあるテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7411f-185">Because of this, you will see the text behind the objects by default.</span></span> <span data-ttu-id="7411f-186">シンプルな付属[、オクルー ジョンをサポートするシェーダー](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader)します。</span><span class="sxs-lookup"><span data-stu-id="7411f-186">We have included a simple [shader that supports the occlusion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader).</span></span> <span data-ttu-id="7411f-187">次の図は、既定のフォントのマテリアル (左) とテキストと適切なオクルー ジョン (右) を使用してテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="7411f-187">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="7411f-188">![シェーダー オクルー ジョン サポート](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7411f-188">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="7411f-189">*シェーダー オクルー ジョン サポート*</span><span class="sxs-lookup"><span data-stu-id="7411f-189">*Shader with occlusion support*</span></span>


## <a name="see-also"></a><span data-ttu-id="7411f-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="7411f-190">See also</span></span>
* [<span data-ttu-id="7411f-191">MRTK でテキストのプレハブ</span><span class="sxs-lookup"><span data-stu-id="7411f-191">Text Prefab in the MRTK</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [<span data-ttu-id="7411f-192">文字体裁</span><span class="sxs-lookup"><span data-stu-id="7411f-192">Typography</span></span>](typography.md)

 
