---
title: タイポグラフィ
description: テキストは、アプリのエクスペリエンスに情報を提供するための重要な要素です。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、デザイン、スタイル、フォント、タイポグラフィ、ui、ux
ms.openlocfilehash: cc8e25e9cd7ba41bed179328fe7198e935e65d76
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830012"
---
# <a name="typography"></a><span data-ttu-id="bf7a1-104">タイポグラフィ</span><span class="sxs-lookup"><span data-stu-id="bf7a1-104">Typography</span></span>

<span data-ttu-id="bf7a1-105">テキストは、アプリのエクスペリエンスに情報を提供するための重要な要素です。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-105">Text is an important element for delivering information in your app experience.</span></span> <span data-ttu-id="bf7a1-106">2D 画面のタイポグラフィと同じように、目標は明確で読みやすくすることです。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-106">Just like typography on 2D screens, the goal is to be clear and readable.</span></span> <span data-ttu-id="bf7a1-107">混合現実の3次元の側面により、テキストと全体的なユーザーエクスペリエンスをさらに大きくすることができます。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-107">With the three-dimensional aspect of mixed reality, there is an opportunity to affect the text and the overall user experience in an even greater way.</span></span>

<span data-ttu-id="bf7a1-108">![HoloLens でのタイポグラフィの例](images/typography-cover.png)</span><span class="sxs-lookup"><span data-stu-id="bf7a1-108">![Typography example in HoloLens](images/typography-cover.png)</span></span><br>
<span data-ttu-id="bf7a1-109">*HoloLens でのタイポグラフィの例*</span><span class="sxs-lookup"><span data-stu-id="bf7a1-109">*Typography example in HoloLens*</span></span>

<span data-ttu-id="bf7a1-110">3D で型について話をするときは、押し出し、容量の3D テキストを考えてみる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-110">When we talk about type in 3D, we tend to think extruded, volumetric 3D text.</span></span> <span data-ttu-id="bf7a1-111">一部ののロゴデザインやその他の限られたアプリケーションを除き、押し出しテキストはテキストの読みやすさを低下させる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-111">Except for some logotype designs and a few other limited applications, extruded text tends to degrade the readability of the text.</span></span> <span data-ttu-id="bf7a1-112">3D のエクスペリエンスを設計する場合でも、読みやすく、読みやすくなるため、型に2D を使用します。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-112">Even though we are designing experiences for 3D, we use 2D for the type because it is more legible and easier to read.</span></span>

<span data-ttu-id="bf7a1-113">HoloLens では、加法色システムに基づいた光を使用したホログラムで型が構築されます。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-113">In HoloLens, type is constructed with holograms using light based on the additive color system.</span></span> <span data-ttu-id="bf7a1-114">他のホログラムと同じように、type を実際の環境に配置して、世界中でロックし、任意の角度から観察することができます。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-114">Just like other holograms, type can be placed in the actual environment where it can be world locked and observed from any angle.</span></span> <span data-ttu-id="bf7a1-115">型と環境の間の[視差](https://en.wikipedia.org/wiki/Parallax)効果によっても、エクスペリエンスの深さが向上します。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-115">The [parallax](https://en.wikipedia.org/wiki/Parallax) effect between the type and the environment also adds depth to the experience.</span></span>

## <a name="typography-in-mixed-reality"></a><span data-ttu-id="bf7a1-116">Mixed reality でのタイポグラフィ</span><span class="sxs-lookup"><span data-stu-id="bf7a1-116">Typography in mixed reality</span></span>

<span data-ttu-id="bf7a1-117">混合現実の表記規則は、他の場所とは異なります。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-117">Typographic rules in mixed reality are no different from anywhere else.</span></span> <span data-ttu-id="bf7a1-118">物理的な世界と仮想環境の両方のテキストは、読みやすく、読みやすいものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-118">Text in both the physical world and the virtual world needs to be legible and readable.</span></span> <span data-ttu-id="bf7a1-119">テキストは、壁上にあるか、物理オブジェクトに重ねて表示されます。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-119">Text could be on a wall or superimposed on a physical object.</span></span> <span data-ttu-id="bf7a1-120">デジタルユーザーインターフェイスと共に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-120">It could be floating along with a digital user interface.</span></span> <span data-ttu-id="bf7a1-121">文脈に関係なく、読み取りと認識に対して同じタイポグラフィルールを適用します。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-121">Regardless of the context, we apply the same typographic rules for reading and recognition.</span></span>

### <a name="create-clear-hierarchy"></a><span data-ttu-id="bf7a1-122">明確階層の作成</span><span class="sxs-lookup"><span data-stu-id="bf7a1-122">Create clear hierarchy</span></span>

<span data-ttu-id="bf7a1-123">さまざまな種類のサイズと重みを使用して、コントラストと階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-123">Build contrast and hierarchy by using different type sizes and weights.</span></span> <span data-ttu-id="bf7a1-124">アプリのエクスペリエンス全体で型の傾斜を定義し、それに従うことで、一貫性のある情報階層で優れたユーザーエクスペリエンスを実現できます。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-124">Defining a type ramp and following it throughout the app experience will provide a great user experience with consistent information hierarchy.</span></span>

<span data-ttu-id="bf7a1-125">![型の傾斜の例](images/typography-ramp-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bf7a1-125">![Type ramp examples](images/typography-ramp-1000px.jpg)</span></span><br>
<span data-ttu-id="bf7a1-126">*アプリケーションエクスペリエンス全体で、型の傾斜を定義し、それに従う*</span><span class="sxs-lookup"><span data-stu-id="bf7a1-126">*Define your type ramp and follow it throughout the app experience*</span></span>

### <a name="limit-your-fonts"></a><span data-ttu-id="bf7a1-127">フォントを制限する</span><span class="sxs-lookup"><span data-stu-id="bf7a1-127">Limit your fonts</span></span>

<span data-ttu-id="bf7a1-128">1つのコンテキストで2つ以上の異なるフォントファミリを使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-128">Avoid using more than two different font families in a single context.</span></span> <span data-ttu-id="bf7a1-129">これにより、お客様のエクスペリエンスのハーモニーと一貫性が損なわれ、情報を使用することが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-129">This will break the harmony and consistency of your experience and make it harder to consume information.</span></span> <span data-ttu-id="bf7a1-130">HoloLens では、情報は物理環境の上に重なっているため、使用するフォントスタイルが多すぎるとエクスペリエンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-130">In HoloLens, since the information is overlaid on top of the physical environment, using too many font styles will degrade the experience.</span></span> <span data-ttu-id="bf7a1-131">Segoe UI は、すべての Microsoft デジタルデザインのフォントです。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-131">Segoe UI is the font for all Microsoft digital designs.</span></span> <span data-ttu-id="bf7a1-132">Windows Mixed Reality シェルでは一貫して使用されます。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-132">It is used consistently in the Windows Mixed Reality shell.</span></span> <span data-ttu-id="bf7a1-133">Segoe UI フォントファイルは、 [Windows design toolkit のページ](https://docs.microsoft.com/windows/uwp/design-downloads/)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-133">You can download the Segoe UI font file from the [Windows design toolkit page](https://docs.microsoft.com/windows/uwp/design-downloads/).</span></span>

[<span data-ttu-id="bf7a1-134">Segoe UI タイプフェイスに関する詳細情報</span><span class="sxs-lookup"><span data-stu-id="bf7a1-134">More information about the Segoe UI typeface</span></span>](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a><span data-ttu-id="bf7a1-135">細いフォントの太さを避ける</span><span class="sxs-lookup"><span data-stu-id="bf7a1-135">Avoid thin font weights</span></span>

<span data-ttu-id="bf7a1-136">細い垂直線はバイブレーションになり、読みにくくなるため、42 pt 未満の型サイズに対しては薄いまたは semilight のフォントの重みを使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-136">Avoid using light or semilight font weights for type sizes under 42pt since thin vertical strokes will vibrate and degrade legibility.</span></span> <span data-ttu-id="bf7a1-137">ストロークの太さが十分にある最新のフォントがうまく機能します。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-137">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="bf7a1-138">たとえば、Helvetica, と Arial は、標準または太字の重みを使用して HoloLens で非常に読みやすくなっています。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-138">For example, Helvetica and Arial are very legible in HoloLens using regular or bold weights.</span></span>

### <a name="color"></a><span data-ttu-id="bf7a1-139">色</span><span class="sxs-lookup"><span data-stu-id="bf7a1-139">Color</span></span>

<span data-ttu-id="bf7a1-140">HoloLens では、ホログラムは加法の光源システムを使用して構築されるため、白のテキストは非常に読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-140">In HoloLens, since the holograms are constructed with an additive light system, white text is highly legible.</span></span> <span data-ttu-id="bf7a1-141">ホワイトテキストの例については、[スタート] メニューとアプリバーを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-141">You can find examples of white text on the Start menu and the App bar.</span></span> <span data-ttu-id="bf7a1-142">HoloLens でバックプレートを使用しなくても白のテキストは適切に機能しますが、複雑な物理的背景によって型が読みづらくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-142">Even though white text works well without a back plate on HoloLens, a complex physical background could make the type difficult to read.</span></span> <span data-ttu-id="bf7a1-143">ユーザーのフォーカスを改善し、物理的な背景からの邪魔を最小限に抑えるには、濃い色または色付きの背景色で白いテキストを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-143">To improve the user's focus and minimize the distraction from a physical background, we recommend using white text on a dark or colored back plate.</span></span>

<br>


<span data-ttu-id="bf7a1-144">![ダークカラーまたは色付きの背景プレートでは、白いテキストを使用することをお勧めします。*ダークカラーまたは色付きの背景プレートの白いテキストの例。* ](images/typography-whiteonblack2-1000px.jpg)
</span><span class="sxs-lookup"><span data-stu-id="bf7a1-144">![We recommend using white text on a dark or colored back plate.](images/typography-whiteonblack2-1000px.jpg)
*Examples of white text on a dark or colored back plate.*</span></span>
<br>

<span data-ttu-id="bf7a1-145">ダークテキストを使用するには、明るい背景プレートを使用して読み取り可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-145">To use dark text, you should use a bright back plate to make it readable.</span></span> <span data-ttu-id="bf7a1-146">加法色のシステムでは、黒は透明として表示されます。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-146">In additive color systems, black is displayed as transparent.</span></span> <span data-ttu-id="bf7a1-147">これは、色付きの背景プレートを使用せずに黒のテキストを表示できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-147">This means you will not be able to see the black text without a colored back plate.</span></span>

<span data-ttu-id="bf7a1-148">![黒のテキストの例](images/typography-whiteonblack.png)
</span><span class="sxs-lookup"><span data-stu-id="bf7a1-148">![Black text examples](images/typography-whiteonblack.png)
</span></span><br><span data-ttu-id="bf7a1-149">*白の場合の白の例と白のテキストの黒*</span><span class="sxs-lookup"><span data-stu-id="bf7a1-149">*Examples of white on back and black on white text*</span></span>


<span data-ttu-id="bf7a1-150">![黒のテキストの例](images/640px-typography-blackonwhite.jpg)
</span><span class="sxs-lookup"><span data-stu-id="bf7a1-150">![Black text examples](images/640px-typography-blackonwhite.jpg)
</span></span><br><span data-ttu-id="bf7a1-151">*システムアプリの黒いテキストの例-ストアと設定*</span><span class="sxs-lookup"><span data-stu-id="bf7a1-151">*Examples of black text in the system apps - Store and Settings*</span></span>

## <a name="recommended-font-size"></a><span data-ttu-id="bf7a1-152">推奨されるフォントサイズ</span><span class="sxs-lookup"><span data-stu-id="bf7a1-152">Recommended font size</span></span>

<span data-ttu-id="bf7a1-153">ご想像のとおり、PC またはタブレットデバイスで使用する種類のサイズ (通常は 12 ~ 32pt) は2メートルの距離で非常に小さくなります。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-153">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="bf7a1-154">これは、各フォントの特性によって異なりますが、一般的には、ユーザー研究の研究に基づいて、推奨される最小の表示角度と、読みやすくするためのフォントの高さは、0.35 °-0.4 °/12.21-13.97mm にあります。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-154">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="bf7a1-155">[Unity ページのテキスト](text-in-unity.md)で導入されたスケールファクターを使用して、約 35 ~ 40pt です。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-155">It is about 35-40pt with the scaling factor introduced in [Text in Unity](text-in-unity.md) page.</span></span> 

<span data-ttu-id="bf7a1-156">0\.45 m (45cm) でのほぼ相互作用の場合、フォントの表示角度と高さの最小値は0.4 °-0.5 °/3.14 – 3.9 mm です。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-156">For the near interaction at 0.45m(45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="bf7a1-157">これは、 [Unity のテキスト](text-in-unity.md)で導入されたスケールファクターを使用した12ポイントです。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-157">It is about 9-12pt with the scaling factor introduced in [Text in Unity](text-in-unity.md).</span></span>

<span data-ttu-id="bf7a1-158">![近距離および遠くの相互作用範囲*のコンテンツとほぼの相互作用範囲*](images/typography-distance-1000px.jpg)
</span><span class="sxs-lookup"><span data-stu-id="bf7a1-158">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="bf7a1-159">最小のフォントサイズの最小値</span><span class="sxs-lookup"><span data-stu-id="bf7a1-159">The minimum legible font size</span></span>
| <span data-ttu-id="bf7a1-160">単位</span><span class="sxs-lookup"><span data-stu-id="bf7a1-160">Distance</span></span> | <span data-ttu-id="bf7a1-161">表示角度</span><span class="sxs-lookup"><span data-stu-id="bf7a1-161">Viewing angle</span></span> | <span data-ttu-id="bf7a1-162">テキストの高さ</span><span class="sxs-lookup"><span data-stu-id="bf7a1-162">Text height</span></span> | <span data-ttu-id="bf7a1-163">フォントサイズ \* \*</span><span class="sxs-lookup"><span data-stu-id="bf7a1-163">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="bf7a1-164">45cm (直接操作距離)</span><span class="sxs-lookup"><span data-stu-id="bf7a1-164">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="bf7a1-165">0.4 °-0.5 °</span><span class="sxs-lookup"><span data-stu-id="bf7a1-165">0.4°-0.5°</span></span> | <span data-ttu-id="bf7a1-166">3.14 ~ 3.9 mm</span><span class="sxs-lookup"><span data-stu-id="bf7a1-166">3.14–3.9mm</span></span> | <span data-ttu-id="bf7a1-167">8.9 – 11.13 pt</span><span class="sxs-lookup"><span data-stu-id="bf7a1-167">8.9–11.13pt</span></span> |
| <span data-ttu-id="bf7a1-168">2分</span><span class="sxs-lookup"><span data-stu-id="bf7a1-168">2m</span></span> | <span data-ttu-id="bf7a1-169">0.35 °-0.4 °</span><span class="sxs-lookup"><span data-stu-id="bf7a1-169">0.35°-0.4°</span></span> | <span data-ttu-id="bf7a1-170">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="bf7a1-170">12.21–13.97mm</span></span> | <span data-ttu-id="bf7a1-171">34.63-39.58 pt</span><span class="sxs-lookup"><span data-stu-id="bf7a1-171">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="bf7a1-172">判読しやすいフォントサイズ</span><span class="sxs-lookup"><span data-stu-id="bf7a1-172">The comfortably legible font size</span></span>
| <span data-ttu-id="bf7a1-173">単位</span><span class="sxs-lookup"><span data-stu-id="bf7a1-173">Distance</span></span> | <span data-ttu-id="bf7a1-174">表示角度</span><span class="sxs-lookup"><span data-stu-id="bf7a1-174">Viewing angle</span></span> | <span data-ttu-id="bf7a1-175">テキストの高さ</span><span class="sxs-lookup"><span data-stu-id="bf7a1-175">Text height</span></span> | <span data-ttu-id="bf7a1-176">フォントサイズ \* \*</span><span class="sxs-lookup"><span data-stu-id="bf7a1-176">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="bf7a1-177">45cm (直接操作距離)</span><span class="sxs-lookup"><span data-stu-id="bf7a1-177">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="bf7a1-178">0.65 °-0.8 °</span><span class="sxs-lookup"><span data-stu-id="bf7a1-178">0.65°-0.8°</span></span> | <span data-ttu-id="bf7a1-179">5.1-6.3 mm</span><span class="sxs-lookup"><span data-stu-id="bf7a1-179">5.1-6.3mm</span></span> | <span data-ttu-id="bf7a1-180">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="bf7a1-180">14.47-17.8pt</span></span> |
| <span data-ttu-id="bf7a1-181">2分</span><span class="sxs-lookup"><span data-stu-id="bf7a1-181">2m</span></span> | <span data-ttu-id="bf7a1-182">0.6 °-0.75 °</span><span class="sxs-lookup"><span data-stu-id="bf7a1-182">0.6°-0.75°</span></span> | <span data-ttu-id="bf7a1-183">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="bf7a1-183">20.9-26.2mm</span></span> | <span data-ttu-id="bf7a1-184">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="bf7a1-184">59.4-74.2pt</span></span> |


<span data-ttu-id="bf7a1-185">Segoe UI (Windows の既定のフォント) は、ほとんどの場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-185">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="bf7a1-186">ただし、薄い垂直方向のストロークはバイブレーションので、読みやすさが低下するので、小さいサイズの明るいフォントや半明るいフォントファミリは使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-186">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="bf7a1-187">ストロークの太さが十分にある最新のフォントがうまく機能します。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-187">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="bf7a1-188">たとえば、Helvetica, と Arial は、通常または太字の重みを使用して HoloLens で非常に読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-188">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="bf7a1-189">\* \* Unity でのテキストサイズの計算の詳細については、 [unity のページテキスト](text-in-unity.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf7a1-189">\*\*For more detailed information about text size calculation in Unity, please refer to the page [Text in Unity](text-in-unity.md)</span></span>

<span data-ttu-id="bf7a1-190">![角度](images/Text_In_Unity_ViewingAngle.jpg)
*表示距離、角度、およびテキストの高さ*を表示する</span><span class="sxs-lookup"><span data-stu-id="bf7a1-190">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="resources"></a><span data-ttu-id="bf7a1-191">リソース</span><span class="sxs-lookup"><span data-stu-id="bf7a1-191">Resources</span></span>
* [<span data-ttu-id="bf7a1-192">Yu gothic フォント</span><span class="sxs-lookup"><span data-stu-id="bf7a1-192">Segoe fonts</span></span>](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [<span data-ttu-id="bf7a1-193">HoloLens フォント</span><span class="sxs-lookup"><span data-stu-id="bf7a1-193">HoloLens font</span></span>](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

<span data-ttu-id="bf7a1-194">![HoloLens フォントは、Windows Mixed Reality で使用される記号のグリフを提供します。](images/300px-hololensmdl2symbols.jpg)
</span><span class="sxs-lookup"><span data-stu-id="bf7a1-194">![The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality](images/300px-hololensmdl2symbols.jpg)
</span></span><br><span data-ttu-id="bf7a1-195">*HoloLens フォントは、Windows Mixed Reality で使用される記号のグリフを提供します。*</span><span class="sxs-lookup"><span data-stu-id="bf7a1-195">*The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality.*</span></span>

## <a name="see-also"></a><span data-ttu-id="bf7a1-196">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf7a1-196">See also</span></span>
* [<span data-ttu-id="bf7a1-197">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="bf7a1-197">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="bf7a1-198">色、ライト、マテリアル</span><span class="sxs-lookup"><span data-stu-id="bf7a1-198">Color, light and materials</span></span>](color,-light-and-materials.md)
