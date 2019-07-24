---
title: Unity のテキスト
description: Unity でテキストを表示するには、UI テキストと3D テキストメッシュという2種類のテキストコンポーネントを使用できます。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、デザイン、コントロール、フォント、タイポグラフィ、ui、ux
ms.openlocfilehash: f57b04c7d57219b7426793879004ef010d2b1ea8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415430"
---
# <a name="text-in-unity"></a><span data-ttu-id="e22e5-104">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="e22e5-104">Text in Unity</span></span>

<span data-ttu-id="e22e5-105">Text は、holographic アプリで最も重要なコンポーネントの1つです。</span><span class="sxs-lookup"><span data-stu-id="e22e5-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="e22e5-106">Unity でテキストを表示するには、UI テキスト、3D テキストメッシュ、およびテキストメッシュ Pro の3種類のテキストコンポーネントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-106">To display text in Unity, there are three types of text components you can use — UI Text, 3D Text Mesh, and Text Mesh Pro.</span></span> <span data-ttu-id="e22e5-107">既定では、UI テキストと3D テキストメッシュはぼやけて表示され、大きすぎます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-107">By default UI Text and 3D Text Mesh appear blurry and are too big.</span></span> <span data-ttu-id="e22e5-108">HoloLens で管理しやすいサイズのシャープで高品質なテキストを取得するには、いくつかの変数を微調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e22e5-108">You need to tweak a few variables to get sharp, high-quality text that has a manageable size in HoloLens.</span></span> <span data-ttu-id="e22e5-109">UI テキストと3D テキストメッシュコンポーネントの使用時にスケールファクターを適用して適切なディメンションを取得することで、表示品質を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-109">By applying scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components, you can achieve better rendering quality.</span></span>

<span data-ttu-id="e22e5-110">![シャープで美しいテキストを取得する方法](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="e22e5-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="e22e5-111">*Unity の既定のテキストがぼやけています*</span><span class="sxs-lookup"><span data-stu-id="e22e5-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a><span data-ttu-id="e22e5-112">Unity の3D テキスト (テキストメッシュ) と UI テキストの操作</span><span class="sxs-lookup"><span data-stu-id="e22e5-112">Working with Unity's 3D Text(Text Mesh) and UI Text</span></span>

<span data-ttu-id="e22e5-113">Unity では、シーンに追加されたすべての新しい要素のサイズが 1 Unity 単位であることを前提としています。また、100% の変換スケールは、HoloLens で約1メーターに変換されます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-113">Unity assumes all new elements added to a scene are 1 Unity Unit in size, or 100% transform scale, which translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="e22e5-114">フォントの場合、3D TextMesh の境界ボックスは、既定では約1メートルの高さになります。</span><span class="sxs-lookup"><span data-stu-id="e22e5-114">In the case of fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="e22e5-115">![Unity でのフォントの操作](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="e22e5-115">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="e22e5-116">*既定の Unity 3D テキスト (テキストメッシュ) は1つの Unity ユニット (1 メートル) を占有します*</span><span class="sxs-lookup"><span data-stu-id="e22e5-116">*Default Unity 3D Text (Text Mesh) occupies 1 Unity Unit which is 1 meter*</span></span>

<br>
<span data-ttu-id="e22e5-117">ほとんどのビジュアルデザイナーはポイントを使用して、実際の世界でのフォントサイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="e22e5-117">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="e22e5-118">1メートルには約 2835 (2, 834.645666399962) のポイントがあります。</span><span class="sxs-lookup"><span data-stu-id="e22e5-118">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="e22e5-119">ポイントシステムの1メーターへの変換と、Unity の既定のテキストメッシュのフォントサイズ13に基づき、13を2835で割った単純な数値は 0.0046 (正確には 0.004586111116) となり、最初は適切な標準スケールになります (一部は0.005 に丸めます)。</span><span class="sxs-lookup"><span data-stu-id="e22e5-119">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="e22e5-120">テキストオブジェクトまたはコンテナーをこれらの値に拡張すると、デザインプログラムでフォントサイズを1:1 変換できるだけでなく、エクスペリエンス全体の一貫性を維持するための標準も提供されます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-120">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your experience.</span></span>

<span data-ttu-id="e22e5-121">![フォントサイズが異なる Unity 3D テキストメッシュ](images/Text_In_Unity_Measurements1.png)</span><span class="sxs-lookup"><span data-stu-id="e22e5-121">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements1.png)</span></span><br>
<span data-ttu-id="e22e5-122">*Unity 3D テキストと UI テキストの値のスケーリング*</span><span class="sxs-lookup"><span data-stu-id="e22e5-122">*Scaling values for the Unity 3D Text and UI Text*</span></span>

<span data-ttu-id="e22e5-123">![フォントサイズが異なる Unity 3D テキストメッシュ](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e22e5-123">![Unity 3D Text Mesh with different font sizes](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="e22e5-124">*最適化された値を持つ Unity 3D テキストメッシュ*</span><span class="sxs-lookup"><span data-stu-id="e22e5-124">*Unity 3D Text Mesh with optimized values*</span></span>

<br>
<span data-ttu-id="e22e5-125">UI またはキャンバスベースのテキスト要素をシーンに追加すると、サイズの不均衡が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="e22e5-125">When adding a UI or canvas based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="e22e5-126">2つのサイズの違いは約 1000% です。これにより、UI ベースのテキストコンポーネントのスケールファクターが 0.00046 (正確には 0.0004586111116) または0.0005 値のになります。</span><span class="sxs-lookup"><span data-stu-id="e22e5-126">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="e22e5-127">![ユニット値ごとに異なる動的ピクセルを持つ Unity UI テキスト](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e22e5-127">![Unity UI Text with different dynamic pixels per unit values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="e22e5-128">*最適化された値を含む Unity UI テキスト*</span><span class="sxs-lookup"><span data-stu-id="e22e5-128">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="e22e5-129">フォントの既定値は、そのフォントのテクスチャサイズ、またはフォントが Unity にインポートされた方法によって影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e22e5-129">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="e22e5-130">これらのテストは、Unity の既定の Arial フォントおよびその他のインポートされたフォントに基づいて実行されました。</span><span class="sxs-lookup"><span data-stu-id="e22e5-130">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="working-with-text-mesh-pro"></a><span data-ttu-id="e22e5-131">Text メッシュ Pro の操作</span><span class="sxs-lookup"><span data-stu-id="e22e5-131">Working with Text Mesh Pro</span></span>

<span data-ttu-id="e22e5-132">Unity のテキストメッシュ Pro を使用すると、テキストの表示品質を保護できます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-132">With Unity's Text Mesh Pro, you can secure the text rendering quality.</span></span> <span data-ttu-id="e22e5-133">これは、 [.sdf (符号付き距離フィールド)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf)手法を使用した距離に関係なく、鮮明なテキストアウトラインをサポートします。</span><span class="sxs-lookup"><span data-stu-id="e22e5-133">It supports crisp text outline regardless of the distance using the [SDF(Signed Distance Field)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) technique.</span></span> <span data-ttu-id="e22e5-134">上記で3D テキストメッシュと UI テキストに使用したのと同じ計算方法を使用して、通常のタイポグラフィポイントを使用するための適切なスケーリング値を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-134">Using the same calculation method that we used above for the 3D Text Mesh and UI Text, we can find proper scaling values to use conventional typographic Point.</span></span> <span data-ttu-id="e22e5-135">サイズ36の既定の3D テキストメッシュ Pro フォントは 2.5 Unity ユニット (2.5 m) の外を示しているため、スケール値0.005 を使用してポイントサイズを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-135">Since the default 3D Text Mesh Pro font with the size 36 shows the bounding of 2.5 Unity Unit(2.5m), we can use scaling value 0.005 to use the Point size.</span></span> <span data-ttu-id="e22e5-136">UI メニューのテキストメッシュ Pro の既定の境界サイズは 25 Unity Unit (25m) です。</span><span class="sxs-lookup"><span data-stu-id="e22e5-136">The Text Mesh Pro under UI menu has the default bounding size of 25 Unity Unit(25m).</span></span> <span data-ttu-id="e22e5-137">これにより、0.0005 のスケーリング値が得られます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-137">This gives us 0.0005 for the scaling value.</span></span>

<span data-ttu-id="e22e5-138">![フォントサイズが異なる Unity 3D テキストメッシュ](images/Text_In_Unity_Measurements2.png)</span><span class="sxs-lookup"><span data-stu-id="e22e5-138">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements2.png)</span></span><br>
<span data-ttu-id="e22e5-139">*Unity 3D テキストと UI テキストの値のスケーリング*</span><span class="sxs-lookup"><span data-stu-id="e22e5-139">*Scaling values for the Unity 3D Text and UI Text*</span></span>

## <a name="recommended-text-size"></a><span data-ttu-id="e22e5-140">推奨されるテキストのサイズ</span><span class="sxs-lookup"><span data-stu-id="e22e5-140">Recommended text size</span></span>
<span data-ttu-id="e22e5-141">ご想像のとおり、PC またはタブレットデバイスで使用する種類のサイズ (通常は 12 ~ 32pt) は2メートルの距離で非常に小さくなります。</span><span class="sxs-lookup"><span data-stu-id="e22e5-141">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="e22e5-142">これは、各フォントの特性によって異なりますが、一般的には、ユーザー研究の研究に基づいて、推奨される最小の表示角度と、読みやすくするためのフォントの高さは、0.35 °-0.4 °/12.21-13.97mm にあります。</span><span class="sxs-lookup"><span data-stu-id="e22e5-142">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="e22e5-143">これは、上で導入されたスケールファクターを使用した約 35 ~ 40pt です。</span><span class="sxs-lookup"><span data-stu-id="e22e5-143">It is about 35-40pt with the scaling factor introduced above.</span></span> 

<span data-ttu-id="e22e5-144">0\.45 m (45cm) でのほぼ相互作用の場合、フォントの表示角度と高さの最小値は0.4 °-0.5 °/3.14 – 3.9 mm です。</span><span class="sxs-lookup"><span data-stu-id="e22e5-144">For the near interaction at 0.45m(45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="e22e5-145">これは、前に紹介したスケールファクターを使用した12ポイントです。</span><span class="sxs-lookup"><span data-stu-id="e22e5-145">It is about 9-12pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="e22e5-146">![近距離および遠くの相互作用範囲*のコンテンツとほぼの相互作用範囲*](images/typography-distance-1000px.jpg)
</span><span class="sxs-lookup"><span data-stu-id="e22e5-146">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="e22e5-147">最小のフォントサイズの最小値</span><span class="sxs-lookup"><span data-stu-id="e22e5-147">The minimum legible font size</span></span>
| <span data-ttu-id="e22e5-148">単位</span><span class="sxs-lookup"><span data-stu-id="e22e5-148">Distance</span></span> | <span data-ttu-id="e22e5-149">表示角度</span><span class="sxs-lookup"><span data-stu-id="e22e5-149">Viewing angle</span></span> | <span data-ttu-id="e22e5-150">テキストの高さ</span><span class="sxs-lookup"><span data-stu-id="e22e5-150">Text height</span></span> | <span data-ttu-id="e22e5-151">Font Size</span><span class="sxs-lookup"><span data-stu-id="e22e5-151">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="e22e5-152">45cm (直接操作距離)</span><span class="sxs-lookup"><span data-stu-id="e22e5-152">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="e22e5-153">0.4 °-0.5 °</span><span class="sxs-lookup"><span data-stu-id="e22e5-153">0.4°-0.5°</span></span> | <span data-ttu-id="e22e5-154">3.14 ~ 3.9 mm</span><span class="sxs-lookup"><span data-stu-id="e22e5-154">3.14–3.9mm</span></span> | <span data-ttu-id="e22e5-155">8.9 – 11.13 pt</span><span class="sxs-lookup"><span data-stu-id="e22e5-155">8.9–11.13pt</span></span> |
| <span data-ttu-id="e22e5-156">2分</span><span class="sxs-lookup"><span data-stu-id="e22e5-156">2m</span></span> | <span data-ttu-id="e22e5-157">0.35 °-0.4 °</span><span class="sxs-lookup"><span data-stu-id="e22e5-157">0.35°-0.4°</span></span> | <span data-ttu-id="e22e5-158">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="e22e5-158">12.21–13.97mm</span></span> | <span data-ttu-id="e22e5-159">34.63-39.58 pt</span><span class="sxs-lookup"><span data-stu-id="e22e5-159">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="e22e5-160">判読しやすいフォントサイズ</span><span class="sxs-lookup"><span data-stu-id="e22e5-160">The comfortably legible font size</span></span>
| <span data-ttu-id="e22e5-161">単位</span><span class="sxs-lookup"><span data-stu-id="e22e5-161">Distance</span></span> | <span data-ttu-id="e22e5-162">表示角度</span><span class="sxs-lookup"><span data-stu-id="e22e5-162">Viewing angle</span></span> | <span data-ttu-id="e22e5-163">テキストの高さ</span><span class="sxs-lookup"><span data-stu-id="e22e5-163">Text height</span></span> | <span data-ttu-id="e22e5-164">Font Size</span><span class="sxs-lookup"><span data-stu-id="e22e5-164">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="e22e5-165">45cm (直接操作距離)</span><span class="sxs-lookup"><span data-stu-id="e22e5-165">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="e22e5-166">0.65 °-0.8 °</span><span class="sxs-lookup"><span data-stu-id="e22e5-166">0.65°-0.8°</span></span> | <span data-ttu-id="e22e5-167">5.1-6.3 mm</span><span class="sxs-lookup"><span data-stu-id="e22e5-167">5.1-6.3mm</span></span> | <span data-ttu-id="e22e5-168">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="e22e5-168">14.47-17.8pt</span></span> |
| <span data-ttu-id="e22e5-169">2分</span><span class="sxs-lookup"><span data-stu-id="e22e5-169">2m</span></span> | <span data-ttu-id="e22e5-170">0.6 °-0.75 °</span><span class="sxs-lookup"><span data-stu-id="e22e5-170">0.6°-0.75°</span></span> | <span data-ttu-id="e22e5-171">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="e22e5-171">20.9-26.2mm</span></span> | <span data-ttu-id="e22e5-172">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="e22e5-172">59.4-74.2pt</span></span> |

<span data-ttu-id="e22e5-173">Segoe UI (Windows の既定のフォント) は、ほとんどの場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="e22e5-173">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="e22e5-174">ただし、薄い垂直方向のストロークはバイブレーションので、読みやすさが低下するので、小さいサイズの明るいフォントや半明るいフォントファミリは使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="e22e5-174">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="e22e5-175">ストロークの太さが十分にある最新のフォントがうまく機能します。</span><span class="sxs-lookup"><span data-stu-id="e22e5-175">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="e22e5-176">たとえば、Helvetica, と Arial は、通常または太字の重みを使用して HoloLens で非常に読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="e22e5-176">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>


<span data-ttu-id="e22e5-177">![角度](images/Text_In_Unity_ViewingAngle.jpg)
*表示距離、角度、およびテキストの高さ*を表示する</span><span class="sxs-lookup"><span data-stu-id="e22e5-177">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="e22e5-178">適切なディメンションを使用した鋭いテキストレンダリング品質</span><span class="sxs-lookup"><span data-stu-id="e22e5-178">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="e22e5-179">これらのスケールファクターに基づき、 [UI テキストと3D テキストメッシュを使用してテキスト prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)を作成しました。</span><span class="sxs-lookup"><span data-stu-id="e22e5-179">Based on these scaling factors, we have created [text prefabs with UI Text and 3D Text Mesh](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text).</span></span> <span data-ttu-id="e22e5-180">開発者は、これらの prefabs を使用して、鋭いテキストと一貫したフォントサイズを取得できます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-180">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="e22e5-181">![適切なディメンションを使用した鋭いテキストレンダリング品質](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e22e5-181">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="e22e5-182">*適切なディメンションを使用した鋭いテキストレンダリング品質*</span><span class="sxs-lookup"><span data-stu-id="e22e5-182">*Sharp text rendering quality with proper dimension*</span></span>

## <a name="shader-with-occlusion-support"></a><span data-ttu-id="e22e5-183">オクルージョンサポート付きのシェーダー</span><span class="sxs-lookup"><span data-stu-id="e22e5-183">Shader with occlusion support</span></span>

<span data-ttu-id="e22e5-184">Unity の既定のフォントマテリアルでは、オクルージョンはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e22e5-184">Unity's default font material does not support occlusion.</span></span> <span data-ttu-id="e22e5-185">このため、既定ではオブジェクトの背後にテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-185">Because of this, you will see the text behind the objects by default.</span></span> <span data-ttu-id="e22e5-186">[遮蔽をサポートする](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader)単純なシェーダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e22e5-186">We have included a simple [shader that supports the occlusion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader).</span></span> <span data-ttu-id="e22e5-187">次の画像は、既定のフォントマテリアル (左側) が付いたテキストと、適切な遮蔽 (right) のテキストを示しています。</span><span class="sxs-lookup"><span data-stu-id="e22e5-187">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="e22e5-188">![オクルージョンサポート付きのシェーダー](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e22e5-188">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="e22e5-189">*オクルージョンサポート付きのシェーダー*</span><span class="sxs-lookup"><span data-stu-id="e22e5-189">*Shader with occlusion support*</span></span>


## <a name="see-also"></a><span data-ttu-id="e22e5-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="e22e5-190">See also</span></span>
* [<span data-ttu-id="e22e5-191">MRTK のテキスト Prefab</span><span class="sxs-lookup"><span data-stu-id="e22e5-191">Text Prefab in the MRTK</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [<span data-ttu-id="e22e5-192">文字体裁</span><span class="sxs-lookup"><span data-stu-id="e22e5-192">Typography</span></span>](typography.md)

 
