---
title: 文字体裁
description: テキストは、アプリのエクスペリエンスで情報を提供する重要な要素です。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、デザイン、スタイル、フォント、文字体裁、ui、ux
ms.openlocfilehash: cc8e25e9cd7ba41bed179328fe7198e935e65d76
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830012"
---
# <a name="typography"></a><span data-ttu-id="b8cd2-104">文字体裁</span><span class="sxs-lookup"><span data-stu-id="b8cd2-104">Typography</span></span>

<span data-ttu-id="b8cd2-105">テキストは、アプリのエクスペリエンスで情報を提供する重要な要素です。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-105">Text is an important element for delivering information in your app experience.</span></span> <span data-ttu-id="b8cd2-106">2D 画面に文字体裁と同じようには、目的が明確で読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-106">Just like typography on 2D screens, the goal is to be clear and readable.</span></span> <span data-ttu-id="b8cd2-107">複合現実の 3 次元の側面には、テキストと全体的なユーザーに影響する機会をさらに優れた方法でのエクスペリエンス。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-107">With the three-dimensional aspect of mixed reality, there is an opportunity to affect the text and the overall user experience in an even greater way.</span></span>

<span data-ttu-id="b8cd2-108">![HoloLens の文字体裁の例](images/typography-cover.png)</span><span class="sxs-lookup"><span data-stu-id="b8cd2-108">![Typography example in HoloLens](images/typography-cover.png)</span></span><br>
<span data-ttu-id="b8cd2-109">*HoloLens の文字体裁の例*</span><span class="sxs-lookup"><span data-stu-id="b8cd2-109">*Typography example in HoloLens*</span></span>

<span data-ttu-id="b8cd2-110">3D での型について話すとき押し出された、帯域幅消費型の 3D テキストを考える傾向があります。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-110">When we talk about type in 3D, we tend to think extruded, volumetric 3D text.</span></span> <span data-ttu-id="b8cd2-111">一部のロゴのデザインと他のいくつかの制限付きアプリケーションを除く押し出されたテキストは、テキストの読みやすさが低下する傾向があります。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-111">Except for some logotype designs and a few other limited applications, extruded text tends to degrade the readability of the text.</span></span> <span data-ttu-id="b8cd2-112">場合でも、私たちは 3D のエクスペリエンスを設計して、2 D 型のため、使用がより読みやすく、読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-112">Even though we are designing experiences for 3D, we use 2D for the type because it is more legible and easier to read.</span></span>

<span data-ttu-id="b8cd2-113">HoloLens では、種類はホログラム加法色のシステムに基づく light を使用してで構築されます。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-113">In HoloLens, type is constructed with holograms using light based on the additive color system.</span></span> <span data-ttu-id="b8cd2-114">他のホログラムと同じように型配置できる実際の環境で世界がロックされており、あらゆる角度から観察されたこと。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-114">Just like other holograms, type can be placed in the actual environment where it can be world locked and observed from any angle.</span></span> <span data-ttu-id="b8cd2-115">[視差](https://en.wikipedia.org/wiki/Parallax)型と、環境の間の効果の深さをエクスペリエンスにも追加します。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-115">The [parallax](https://en.wikipedia.org/wiki/Parallax) effect between the type and the environment also adds depth to the experience.</span></span>

## <a name="typography-in-mixed-reality"></a><span data-ttu-id="b8cd2-116">複合現実での文字体裁</span><span class="sxs-lookup"><span data-stu-id="b8cd2-116">Typography in mixed reality</span></span>

<span data-ttu-id="b8cd2-117">複合現実での文字体裁の規則はありませんから任意の場所です。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-117">Typographic rules in mixed reality are no different from anywhere else.</span></span> <span data-ttu-id="b8cd2-118">物理環境と仮想環境の両方のテキストを読みやすく、読み取り可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-118">Text in both the physical world and the virtual world needs to be legible and readable.</span></span> <span data-ttu-id="b8cd2-119">テキストは、壁に可能性があります。 または物理オブジェクト上に重ねて表示します。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-119">Text could be on a wall or superimposed on a physical object.</span></span> <span data-ttu-id="b8cd2-120">デジタルのユーザー インターフェイスと共に浮動でした。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-120">It could be floating along with a digital user interface.</span></span> <span data-ttu-id="b8cd2-121">コンテキストに関係なく、読み取りと認識と同じ表記規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-121">Regardless of the context, we apply the same typographic rules for reading and recognition.</span></span>

### <a name="create-clear-hierarchy"></a><span data-ttu-id="b8cd2-122">明確な階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-122">Create clear hierarchy</span></span>

<span data-ttu-id="b8cd2-123">さまざまなサイズと重みを使用して、コントラスト、および階層をビルドします。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-123">Build contrast and hierarchy by using different type sizes and weights.</span></span> <span data-ttu-id="b8cd2-124">種類ごとの傾斜増加を定義して、アプリのエクスペリエンス全体で一貫性のある情報の階層で優れたユーザー エクスペリエンスを送りします。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-124">Defining a type ramp and following it throughout the app experience will provide a great user experience with consistent information hierarchy.</span></span>

<span data-ttu-id="b8cd2-125">![種類ごとの傾斜増加の例](images/typography-ramp-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8cd2-125">![Type ramp examples](images/typography-ramp-1000px.jpg)</span></span><br>
<span data-ttu-id="b8cd2-126">*種類ごとの傾斜増加を定義し、そのアプリのエクスペリエンス全体で*</span><span class="sxs-lookup"><span data-stu-id="b8cd2-126">*Define your type ramp and follow it throughout the app experience*</span></span>

### <a name="limit-your-fonts"></a><span data-ttu-id="b8cd2-127">フォントを制限します。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-127">Limit your fonts</span></span>

<span data-ttu-id="b8cd2-128">1 つのコンテキストで 2 つ以上の別のフォント ファミリを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-128">Avoid using more than two different font families in a single context.</span></span> <span data-ttu-id="b8cd2-129">調和と整合性のエクスペリエンスの中断を困難に情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-129">This will break the harmony and consistency of your experience and make it harder to consume information.</span></span> <span data-ttu-id="b8cd2-130">HoloLens で、情報が、物理環境の上に重なって表示ためが多すぎるのフォント スタイルを使用してが低下経験します。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-130">In HoloLens, since the information is overlaid on top of the physical environment, using too many font styles will degrade the experience.</span></span> <span data-ttu-id="b8cd2-131">Segoe UI は、すべての Microsoft デジタル設計フォントです。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-131">Segoe UI is the font for all Microsoft digital designs.</span></span> <span data-ttu-id="b8cd2-132">Windows Mixed Reality シェルで一貫して使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-132">It is used consistently in the Windows Mixed Reality shell.</span></span> <span data-ttu-id="b8cd2-133">Segoe UI フォント ファイルをダウンロードすることができます、 [Windows デザイン ツールキット ページ](https://docs.microsoft.com/windows/uwp/design-downloads/)します。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-133">You can download the Segoe UI font file from the [Windows design toolkit page](https://docs.microsoft.com/windows/uwp/design-downloads/).</span></span>

[<span data-ttu-id="b8cd2-134">Segoe UI フォントの詳細について</span><span class="sxs-lookup"><span data-stu-id="b8cd2-134">More information about the Segoe UI typeface</span></span>](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a><span data-ttu-id="b8cd2-135">細いフォントの太さを回避します。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-135">Avoid thin font weights</span></span>

<span data-ttu-id="b8cd2-136">シンの垂直線はバイブレーションし、読みやすさが低下するために、42 pt 型のサイズの明るいまたは semilight のフォントの太さを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-136">Avoid using light or semilight font weights for type sizes under 42pt since thin vertical strokes will vibrate and degrade legibility.</span></span> <span data-ttu-id="b8cd2-137">十分なストロークの太さで最新のフォントがうまく機能します。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-137">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="b8cd2-138">たとえば、Helvetica と Arial は HoloLens で非常に判読または正規の太字の重みを使用してます。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-138">For example, Helvetica and Arial are very legible in HoloLens using regular or bold weights.</span></span>

### <a name="color"></a><span data-ttu-id="b8cd2-139">色</span><span class="sxs-lookup"><span data-stu-id="b8cd2-139">Color</span></span>

<span data-ttu-id="b8cd2-140">は、HoloLens、ホログラムが加法ライト システムで構築されているために、白いテキストは非常に読みやすいが。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-140">In HoloLens, since the holograms are constructed with an additive light system, white text is highly legible.</span></span> <span data-ttu-id="b8cd2-141">[スタート] メニューと、アプリ バーに白いテキストの例が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-141">You can find examples of white text on the Start menu and the App bar.</span></span> <span data-ttu-id="b8cd2-142">白いテキストは、HoloLens でバック プレートなしでも機能する場合でも複雑な物理背景でしたする種類読みにくくします。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-142">Even though white text works well without a back plate on HoloLens, a complex physical background could make the type difficult to read.</span></span> <span data-ttu-id="b8cd2-143">ユーザーのフォーカスを改善し、物理的なバック グラウンドからの邪魔を最小限に抑える、暗色または戻る色付きの版に白いテキストを使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-143">To improve the user's focus and minimize the distraction from a physical background, we recommend using white text on a dark or colored back plate.</span></span>

<br>


<span data-ttu-id="b8cd2-144">![濃いまたは色付きのバック版に白いテキストを使用することをお勧めします。](images/typography-whiteonblack2-1000px.jpg)
*暗色または色付きバック プレートに白いテキストの例を示します。*</span><span class="sxs-lookup"><span data-stu-id="b8cd2-144">![We recommend using white text on a dark or colored back plate.](images/typography-whiteonblack2-1000px.jpg)
*Examples of white text on a dark or colored back plate.*</span></span>
<br>

<span data-ttu-id="b8cd2-145">暗いテキストを使用するには、読み明るいバック皿を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-145">To use dark text, you should use a bright back plate to make it readable.</span></span> <span data-ttu-id="b8cd2-146">付加的な色のシステムでは黒が透明色として表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-146">In additive color systems, black is displayed as transparent.</span></span> <span data-ttu-id="b8cd2-147">つまり、プレートのバックアップを色なし、黒色のテキストを表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-147">This means you will not be able to see the black text without a colored back plate.</span></span>

<span data-ttu-id="b8cd2-148">![黒のテキストの例](images/typography-whiteonblack.png)
</span><span class="sxs-lookup"><span data-stu-id="b8cd2-148">![Black text examples](images/typography-whiteonblack.png)
</span></span><br><span data-ttu-id="b8cd2-149">*背面で白と白のテキストには黒を例を示します*</span><span class="sxs-lookup"><span data-stu-id="b8cd2-149">*Examples of white on back and black on white text*</span></span>


<span data-ttu-id="b8cd2-150">![黒のテキストの例](images/640px-typography-blackonwhite.jpg)
</span><span class="sxs-lookup"><span data-stu-id="b8cd2-150">![Black text examples](images/640px-typography-blackonwhite.jpg)
</span></span><br><span data-ttu-id="b8cd2-151">*システム アプリのストアと設定で黒のテキストの例*</span><span class="sxs-lookup"><span data-stu-id="b8cd2-151">*Examples of black text in the system apps - Store and Settings*</span></span>

## <a name="recommended-font-size"></a><span data-ttu-id="b8cd2-152">推奨のフォント サイズ</span><span class="sxs-lookup"><span data-stu-id="b8cd2-152">Recommended font size</span></span>

<span data-ttu-id="b8cd2-153">予想されることができますの 2 m 離れた距離にある非常に小さく、PC またはタブレット デバイス (通常は 12: 32 ポイント) 間を参照してくださいで使用するサイズを入力します。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-153">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="b8cd2-154">各フォントの特性によって異なりますが、一般に角度と読みやすさのフォントの高さを表示する推奨される最小値は、ユーザー調査研究に基づく 0.35°-0.4°/12.21-13.97mm の周囲にあります。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-154">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="b8cd2-155">35 40 pt を以下の詳細についてで導入されたスケール ファクター [Unity 内のテキスト](text-in-unity.md)ページ。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-155">It is about 35-40pt with the scaling factor introduced in [Text in Unity](text-in-unity.md) page.</span></span> 

<span data-ttu-id="b8cd2-156">0.45m(45cm) でほぼ相互作用は、読みやすいフォントの最小の表示の角度と高さは 0.4 °-mm 0.5 °/3.14 – 3.9 です。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-156">For the near interaction at 0.45m(45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="b8cd2-157">9-12 ポイントの詳細についてで導入されたスケール ファクター [Unity 内のテキスト](text-in-unity.md)します。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-157">It is about 9-12pt with the scaling factor introduced in [Text in Unity](text-in-unity.md).</span></span>

<span data-ttu-id="b8cd2-158">![ここまでの相互作用範囲](images/typography-distance-1000px.jpg)
*の近くにあるコンテンツとの相互作用の範囲*</span><span class="sxs-lookup"><span data-stu-id="b8cd2-158">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="b8cd2-159">読みやすいフォントの最小サイズ</span><span class="sxs-lookup"><span data-stu-id="b8cd2-159">The minimum legible font size</span></span>
| <span data-ttu-id="b8cd2-160">距離</span><span class="sxs-lookup"><span data-stu-id="b8cd2-160">Distance</span></span> | <span data-ttu-id="b8cd2-161">表示角度</span><span class="sxs-lookup"><span data-stu-id="b8cd2-161">Viewing angle</span></span> | <span data-ttu-id="b8cd2-162">テキストの高さ</span><span class="sxs-lookup"><span data-stu-id="b8cd2-162">Text height</span></span> | <span data-ttu-id="b8cd2-163">フォント サイズ \* \*</span><span class="sxs-lookup"><span data-stu-id="b8cd2-163">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="b8cd2-164">45 cm (直接操作までの距離)</span><span class="sxs-lookup"><span data-stu-id="b8cd2-164">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="b8cd2-165">0.4°-0.5°</span><span class="sxs-lookup"><span data-stu-id="b8cd2-165">0.4°-0.5°</span></span> | <span data-ttu-id="b8cd2-166">3.14 – 3.9 mm</span><span class="sxs-lookup"><span data-stu-id="b8cd2-166">3.14–3.9mm</span></span> | <span data-ttu-id="b8cd2-167">8.9 – 11.13pt</span><span class="sxs-lookup"><span data-stu-id="b8cd2-167">8.9–11.13pt</span></span> |
| <span data-ttu-id="b8cd2-168">2 分</span><span class="sxs-lookup"><span data-stu-id="b8cd2-168">2m</span></span> | <span data-ttu-id="b8cd2-169">0.35°-0.4°</span><span class="sxs-lookup"><span data-stu-id="b8cd2-169">0.35°-0.4°</span></span> | <span data-ttu-id="b8cd2-170">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="b8cd2-170">12.21–13.97mm</span></span> | <span data-ttu-id="b8cd2-171">34.63-39.58pt</span><span class="sxs-lookup"><span data-stu-id="b8cd2-171">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="b8cd2-172">快適に読みやすいフォント サイズ</span><span class="sxs-lookup"><span data-stu-id="b8cd2-172">The comfortably legible font size</span></span>
| <span data-ttu-id="b8cd2-173">距離</span><span class="sxs-lookup"><span data-stu-id="b8cd2-173">Distance</span></span> | <span data-ttu-id="b8cd2-174">表示角度</span><span class="sxs-lookup"><span data-stu-id="b8cd2-174">Viewing angle</span></span> | <span data-ttu-id="b8cd2-175">テキストの高さ</span><span class="sxs-lookup"><span data-stu-id="b8cd2-175">Text height</span></span> | <span data-ttu-id="b8cd2-176">フォント サイズ \* \*</span><span class="sxs-lookup"><span data-stu-id="b8cd2-176">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="b8cd2-177">45 cm (直接操作までの距離)</span><span class="sxs-lookup"><span data-stu-id="b8cd2-177">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="b8cd2-178">0.65°-0.8°</span><span class="sxs-lookup"><span data-stu-id="b8cd2-178">0.65°-0.8°</span></span> | <span data-ttu-id="b8cd2-179">5.1-6.3 mm</span><span class="sxs-lookup"><span data-stu-id="b8cd2-179">5.1-6.3mm</span></span> | <span data-ttu-id="b8cd2-180">14.47-17.8pt</span><span class="sxs-lookup"><span data-stu-id="b8cd2-180">14.47-17.8pt</span></span> |
| <span data-ttu-id="b8cd2-181">2 分</span><span class="sxs-lookup"><span data-stu-id="b8cd2-181">2m</span></span> | <span data-ttu-id="b8cd2-182">0.6°-0.75°</span><span class="sxs-lookup"><span data-stu-id="b8cd2-182">0.6°-0.75°</span></span> | <span data-ttu-id="b8cd2-183">20.9 mm-26.2</span><span class="sxs-lookup"><span data-stu-id="b8cd2-183">20.9-26.2mm</span></span> | <span data-ttu-id="b8cd2-184">59.4-74.2pt</span><span class="sxs-lookup"><span data-stu-id="b8cd2-184">59.4-74.2pt</span></span> |


<span data-ttu-id="b8cd2-185">Segoe UI (Windows の既定のフォント) では、ほとんどの場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-185">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="b8cd2-186">ただし、振動シンの垂直線と読みやすさが低下するために、小さなサイズでライトまたは半の明るいフォント ファミリを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-186">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="b8cd2-187">十分なストロークの太さで最新のフォントがうまく機能します。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-187">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="b8cd2-188">たとえば、Helvetica と Arial すばらしい外観になります、通常または太字の重みを持つ、HoloLens で非常に判読可能。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-188">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="b8cd2-189">\* \* の詳細については、Unity でテキスト サイズの計算は、ページを参照してください[Unity 内のテキスト](text-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="b8cd2-189">\*\*For more detailed information about text size calculation in Unity, please refer to the page [Text in Unity](text-in-unity.md)</span></span>

<span data-ttu-id="b8cd2-190">![角度を表示する](images/Text_In_Unity_ViewingAngle.jpg)
*距離、角度、およびテキストの高さを表示します。*</span><span class="sxs-lookup"><span data-stu-id="b8cd2-190">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="resources"></a><span data-ttu-id="b8cd2-191">参考資料</span><span class="sxs-lookup"><span data-stu-id="b8cd2-191">Resources</span></span>
* [<span data-ttu-id="b8cd2-192">Segoe フォント</span><span class="sxs-lookup"><span data-stu-id="b8cd2-192">Segoe fonts</span></span>](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [<span data-ttu-id="b8cd2-193">HoloLens のフォント</span><span class="sxs-lookup"><span data-stu-id="b8cd2-193">HoloLens font</span></span>](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

<span data-ttu-id="b8cd2-194">![HoloLens のフォントは、Windows Mixed Reality で使用されるシンボルのグリフを提供します。](images/300px-hololensmdl2symbols.jpg)
</span><span class="sxs-lookup"><span data-stu-id="b8cd2-194">![The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality](images/300px-hololensmdl2symbols.jpg)
</span></span><br><span data-ttu-id="b8cd2-195">*HoloLens のフォントでは、Windows Mixed Reality で使用されるシンボルのグリフを提供します。*</span><span class="sxs-lookup"><span data-stu-id="b8cd2-195">*The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b8cd2-196">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8cd2-196">See also</span></span>
* [<span data-ttu-id="b8cd2-197">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="b8cd2-197">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="b8cd2-198">色、ライト、マテリアル</span><span class="sxs-lookup"><span data-stu-id="b8cd2-198">Color, light and materials</span></span>](color,-light-and-materials.md)
