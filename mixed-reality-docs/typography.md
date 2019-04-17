---
title: 文字体裁
description: テキストは、アプリのエクスペリエンスで情報を提供する重要な要素です。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、スタイル、フォント、文字体裁、ui、ux
ms.openlocfilehash: b4bac35cbc412ec7102748350c2f5c1e236c2f7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603250"
---
# <a name="typography"></a><span data-ttu-id="2448a-104">文字体裁</span><span class="sxs-lookup"><span data-stu-id="2448a-104">Typography</span></span>

<span data-ttu-id="2448a-105">テキストは、アプリのエクスペリエンスで情報を提供する重要な要素です。</span><span class="sxs-lookup"><span data-stu-id="2448a-105">Text is an important element for delivering information in your app experience.</span></span> <span data-ttu-id="2448a-106">2D 画面に文字体裁と同じようには、目的が明確で読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="2448a-106">Just like typography on 2D screens, the goal is to be clear and readable.</span></span> <span data-ttu-id="2448a-107">複合現実の 3 次元の側面には、テキストと全体的なユーザーに影響する機会をさらに優れた方法でのエクスペリエンス。</span><span class="sxs-lookup"><span data-stu-id="2448a-107">With the three-dimensional aspect of mixed reality, there is an opportunity to affect the text and the overall user experience in an even greater way.</span></span>

<span data-ttu-id="2448a-108">![HoloLens の文字体裁の例](images/640px-typography-hero2.jpg)</span><span class="sxs-lookup"><span data-stu-id="2448a-108">![Typography example in HoloLens](images/640px-typography-hero2.jpg)</span></span><br>
<span data-ttu-id="2448a-109">*HoloLens の文字体裁の例*</span><span class="sxs-lookup"><span data-stu-id="2448a-109">*Typography example in HoloLens*</span></span>

<span data-ttu-id="2448a-110">3D での型について話すとき押し出された、帯域幅消費型の 3D テキストを考える傾向があります。</span><span class="sxs-lookup"><span data-stu-id="2448a-110">When we talk about type in 3D, we tend to think extruded, volumetric 3D text.</span></span> <span data-ttu-id="2448a-111">一部のロゴのデザインと他のいくつかの制限付きアプリケーションを除く押し出されたテキストは、テキストの読みやすさが低下する傾向があります。</span><span class="sxs-lookup"><span data-stu-id="2448a-111">Except for some logotype designs and a few other limited applications, extruded text tends to degrade the readability of the text.</span></span> <span data-ttu-id="2448a-112">場合でも、私たちは 3D のエクスペリエンスを設計して、2 D 型のため、使用がより読みやすく、読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="2448a-112">Even though we are designing experiences for 3D, we use 2D for the type because it is more legible and easier to read.</span></span>

<span data-ttu-id="2448a-113">HoloLens では、種類はホログラム加法色のシステムに基づく light を使用してで構築されます。</span><span class="sxs-lookup"><span data-stu-id="2448a-113">In HoloLens, type is constructed with holograms using light based on the additive color system.</span></span> <span data-ttu-id="2448a-114">他のホログラムと同じように型配置できる実際の環境で世界がロックされており、あらゆる角度から観察されたこと。</span><span class="sxs-lookup"><span data-stu-id="2448a-114">Just like other holograms, type can be placed in the actual environment where it can be world locked and observed from any angle.</span></span> <span data-ttu-id="2448a-115">[視差](https://en.wikipedia.org/wiki/Parallax)型と、環境の間の効果の深さをエクスペリエンスにも追加します。</span><span class="sxs-lookup"><span data-stu-id="2448a-115">The [parallax](https://en.wikipedia.org/wiki/Parallax) effect between the type and the environment also adds depth to the experience.</span></span>

## <a name="typography-in-mixed-reality"></a><span data-ttu-id="2448a-116">複合現実での文字体裁</span><span class="sxs-lookup"><span data-stu-id="2448a-116">Typography in mixed reality</span></span>

<span data-ttu-id="2448a-117">複合現実での文字体裁の規則はありませんから任意の場所です。</span><span class="sxs-lookup"><span data-stu-id="2448a-117">Typographic rules in mixed reality are no different from anywhere else.</span></span> <span data-ttu-id="2448a-118">物理環境と仮想環境の両方のテキストを読みやすく、読み取り可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2448a-118">Text in both the physical world and the virtual world needs to be legible and readable.</span></span> <span data-ttu-id="2448a-119">テキストは、壁に可能性があります。 または物理オブジェクト上に重ねて表示します。</span><span class="sxs-lookup"><span data-stu-id="2448a-119">Text could be on a wall or superimposed on a physical object.</span></span> <span data-ttu-id="2448a-120">デジタルのユーザー インターフェイスと共に浮動でした。</span><span class="sxs-lookup"><span data-stu-id="2448a-120">It could be floating along with a digital user interface.</span></span> <span data-ttu-id="2448a-121">コンテキストに関係なく、読み取りと認識と同じ表記規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="2448a-121">Regardless of the context, we apply the same typographic rules for reading and recognition.</span></span>

### <a name="create-clear-hierarchy"></a><span data-ttu-id="2448a-122">明確な階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="2448a-122">Create clear hierarchy</span></span>

<span data-ttu-id="2448a-123">さまざまなサイズと重みを使用して、コントラスト、および階層をビルドします。</span><span class="sxs-lookup"><span data-stu-id="2448a-123">Build contrast and hierarchy by using different type sizes and weights.</span></span> <span data-ttu-id="2448a-124">種類ごとの傾斜増加を定義して、アプリのエクスペリエンス全体で一貫性のある情報の階層で優れたユーザー エクスペリエンスを送りします。</span><span class="sxs-lookup"><span data-stu-id="2448a-124">Defining a type ramp and following it throughout the app experience will provide a great user experience with consistent information hierarchy.</span></span>

<span data-ttu-id="2448a-125">![種類ごとの傾斜増加の例](images/typography-ramp-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2448a-125">![Type ramp examples](images/typography-ramp-1000px.jpg)</span></span><br>
<span data-ttu-id="2448a-126">*種類ごとの傾斜増加の例*</span><span class="sxs-lookup"><span data-stu-id="2448a-126">*Type ramp examples*</span></span>

### <a name="limit-your-fonts"></a><span data-ttu-id="2448a-127">フォントを制限します。</span><span class="sxs-lookup"><span data-stu-id="2448a-127">Limit your fonts</span></span>

<span data-ttu-id="2448a-128">1 つのコンテキストで 2 つ以上の別のフォント ファミリを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="2448a-128">Avoid using more than two different font families in a single context.</span></span> <span data-ttu-id="2448a-129">調和と整合性のエクスペリエンスの中断を困難に情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="2448a-129">This will break the harmony and consistency of your experience and make it harder to consume information.</span></span> <span data-ttu-id="2448a-130">HoloLens で、情報が、物理環境の上に重なって表示ためが多すぎるのフォント スタイルを使用してが低下経験します。</span><span class="sxs-lookup"><span data-stu-id="2448a-130">In HoloLens, since the information is overlaid on top of the physical environment, using too many font styles will degrade the experience.</span></span> <span data-ttu-id="2448a-131">Segoe UI は、すべての Microsoft デジタル設計フォントです。</span><span class="sxs-lookup"><span data-stu-id="2448a-131">Segoe UI is the font for all Microsoft digital designs.</span></span> <span data-ttu-id="2448a-132">Windows Mixed Reality シェルで一貫して使用されます。</span><span class="sxs-lookup"><span data-stu-id="2448a-132">It is used consistently in the Windows Mixed Reality shell.</span></span> <span data-ttu-id="2448a-133">Segoe UI フォント ファイルをダウンロードすることができます、 [Windows デザイン ツールキット ページ](https://docs.microsoft.com/windows/uwp/design-downloads/)します。</span><span class="sxs-lookup"><span data-stu-id="2448a-133">You can download the Segoe UI font file from the [Windows design toolkit page](https://docs.microsoft.com/windows/uwp/design-downloads/).</span></span>

[<span data-ttu-id="2448a-134">Segoe UI フォントの詳細について</span><span class="sxs-lookup"><span data-stu-id="2448a-134">More information about the Segoe UI typeface</span></span>](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a><span data-ttu-id="2448a-135">細いフォントの太さを回避します。</span><span class="sxs-lookup"><span data-stu-id="2448a-135">Avoid thin font weights</span></span>

<span data-ttu-id="2448a-136">シンの垂直線はバイブレーションし、読みやすさが低下するために、42 pt 型のサイズの明るいまたは semilight のフォントの太さを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="2448a-136">Avoid using light or semilight font weights for type sizes under 42pt since thin vertical strokes will vibrate and degrade legibility.</span></span> <span data-ttu-id="2448a-137">十分なストロークの太さで最新のフォントがうまく機能します。</span><span class="sxs-lookup"><span data-stu-id="2448a-137">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="2448a-138">たとえば、Helvetica と Arial は HoloLens で非常に判読または正規の太字の重みを使用してます。</span><span class="sxs-lookup"><span data-stu-id="2448a-138">For example, Helvetica and Arial are very legible in HoloLens using regular or bold weights.</span></span>

### <a name="color"></a><span data-ttu-id="2448a-139">色</span><span class="sxs-lookup"><span data-stu-id="2448a-139">Color</span></span>

<span data-ttu-id="2448a-140">は、HoloLens、ホログラムが加法ライト システムで構築されているために、白いテキストは非常に読みやすいが。</span><span class="sxs-lookup"><span data-stu-id="2448a-140">In HoloLens, since the holograms are constructed with an additive light system, white text is highly legible.</span></span> <span data-ttu-id="2448a-141">[スタート] メニューと、アプリ バーに白いテキストの例が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2448a-141">You can find examples of white text on the Start menu and the App bar.</span></span> <span data-ttu-id="2448a-142">白いテキストは、HoloLens でバック プレートなしでも機能する場合でも複雑な物理背景でしたする種類読みにくくします。</span><span class="sxs-lookup"><span data-stu-id="2448a-142">Even though white text works well without a back plate on HoloLens, a complex physical background could make the type difficult to read.</span></span> <span data-ttu-id="2448a-143">ユーザーのフォーカスを改善し、物理的なバック グラウンドからの邪魔を最小限に抑える、暗色または戻る色付きの版に白いテキストを使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2448a-143">To improve the user's focus and minimize the distraction from a physical background, we recommend using white text on a dark or colored back plate.</span></span>

<br>


![濃いまたは色付きのバック版に白いテキストを使用することをお勧めします。](images/typography-whiteonblack2-1000px.jpg)

<span data-ttu-id="2448a-145">濃いまたは色付きのバック版に白いテキストを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2448a-145">We recommend using white text on a dark or colored back plate.</span></span>

<br>


![黒のテキストの例](images/640px-typography-textcolors.jpg)

<span data-ttu-id="2448a-147">暗いテキストを使用するには、読み明るいバック皿を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2448a-147">To use dark text, you should use a bright back plate to make it readable.</span></span> <span data-ttu-id="2448a-148">付加的な色のシステムでは黒が透明色として表示されます。</span><span class="sxs-lookup"><span data-stu-id="2448a-148">In additive color systems, black is displayed as transparent.</span></span> <span data-ttu-id="2448a-149">つまり、プレートのバックアップを色なし、黒色のテキストを表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="2448a-149">This means you will not be able to see the black text without a colored back plate.</span></span>

<br>


![黒のテキストの例](images/640px-typography-blackonwhite.jpg)

<span data-ttu-id="2448a-151">UWP アプリ ストアなどの設定では、黒のテキストの例が見つかります。</span><span class="sxs-lookup"><span data-stu-id="2448a-151">You can find examples of black text in UWP apps such as the Store or Settings.</span></span>

## <a name="recommended-font-size"></a><span data-ttu-id="2448a-152">推奨のフォント サイズ</span><span class="sxs-lookup"><span data-stu-id="2448a-152">Recommended font size</span></span>

![2 つのメーターは、テキストを表示するための最適な距離です。](images/typography-distance-1000px.jpg)

<span data-ttu-id="2448a-154">2 つのメーターは、テキストを表示するための最適な距離です。</span><span class="sxs-lookup"><span data-stu-id="2448a-154">Two meters is the optimal distance for displaying text.</span></span>

<span data-ttu-id="2448a-155">複合現実には、3 次元の深さが含まれているので簡単ではありません常にフォントのサイズを通信するためにします。</span><span class="sxs-lookup"><span data-stu-id="2448a-155">Since mixed reality involves three-dimensional depth, it is not always easy to communicate the size of the font.</span></span> <span data-ttu-id="2448a-156">ユーザーの快適性、2 つのメーターはホログラムを配置するための最適な距離です。</span><span class="sxs-lookup"><span data-stu-id="2448a-156">For the user's comfort, two meters is the optimal distance for placing holograms.</span></span> <span data-ttu-id="2448a-157">この距離、最適なフォント サイズを確認するのに基礎として使用できます。</span><span class="sxs-lookup"><span data-stu-id="2448a-157">We can use this distance as a basis to find the optimal font size.</span></span>

<span data-ttu-id="2448a-158">予想されることができますの 2 m 離れた距離にある非常に小さく、PC またはタブレット デバイス (通常は 12: 32 ポイント) 間を参照してくださいで使用するサイズを入力します。</span><span class="sxs-lookup"><span data-stu-id="2448a-158">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="2448a-159">各フォントの特性によって異なりますが、一般に、ストロークの振動ことがなく読みやすいように推奨される最小値の型のサイズには約 30 pt。</span><span class="sxs-lookup"><span data-stu-id="2448a-159">It depends on the characteristics of each font, but in general, the recommended minimum type size for legibility without stroke vibration is around 30pt.</span></span> <span data-ttu-id="2448a-160">アプリは、近い距離に使用することになって、比較的小さなサイズの型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2448a-160">If your app is supposed to be used at a closer distance, smaller type sizes could be used.</span></span> <span data-ttu-id="2448a-161">**ポイントのサイズは、Unity のテキストを 3D メッシュと UI テキストに基づきます。詳細なメトリックとスケール ファクターを参照してください[Unity 内のテキスト](text-in-unity.md)します。**</span><span class="sxs-lookup"><span data-stu-id="2448a-161">**The point size is based on the Unity's 3D Text Mesh and UI Text. For the detailed metrics and scaling factors, please refer to [Text in Unity](text-in-unity.md).**</span></span>

## <a name="resources"></a><span data-ttu-id="2448a-162">参考資料</span><span class="sxs-lookup"><span data-stu-id="2448a-162">Resources</span></span>
* [<span data-ttu-id="2448a-163">Segoe フォント</span><span class="sxs-lookup"><span data-stu-id="2448a-163">Segoe fonts</span></span>](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [<span data-ttu-id="2448a-164">HoloLens のフォント</span><span class="sxs-lookup"><span data-stu-id="2448a-164">HoloLens font</span></span>](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

![HoloLens のフォントは、Windows Mixed Reality で使用されるシンボルのグリフを提供します。](images/300px-hololensmdl2symbols.jpg)

<span data-ttu-id="2448a-166">HoloLens のフォントでは、Windows Mixed Reality で使用されるシンボルのグリフを提供します。</span><span class="sxs-lookup"><span data-stu-id="2448a-166">The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality.</span></span>

## <a name="see-also"></a><span data-ttu-id="2448a-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="2448a-167">See also</span></span>
* [<span data-ttu-id="2448a-168">Unity 内のテキスト</span><span class="sxs-lookup"><span data-stu-id="2448a-168">Text in Unity</span></span>](http://holodocsfuture/index.php?title=Text_in_Unity&action=edit&redlink=1)
* [<span data-ttu-id="2448a-169">色、ライト、マテリアル</span><span class="sxs-lookup"><span data-stu-id="2448a-169">Color, light and materials</span></span>](color,-light-and-materials.md)
