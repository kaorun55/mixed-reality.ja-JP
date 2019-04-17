---
title: Unity 内のテキスト
description: Unity では、テキストを表示するには、2 種類のテキストのコンポーネントを使用することができますが、UI テキストとテキストを 3D メッシュです。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、制御、フォント、文字体裁、ui、ux
ms.openlocfilehash: 02f282ab80a44190d21d2dadefeb7a624c862d04
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603674"
---
# <a name="text-in-unity"></a><span data-ttu-id="bcd4d-104">Unity 内のテキスト</span><span class="sxs-lookup"><span data-stu-id="bcd4d-104">Text in Unity</span></span>

<span data-ttu-id="bcd4d-105">テキストでは、holographic アプリで最も重要なコンポーネントの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="bcd4d-106">Unity では、テキストを表示するには、2 種類のテキストのコンポーネントを使用することができますが、UI テキストとテキストを 3D メッシュです。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-106">To display text in Unity, there are two types of text components you can use — UI Text and 3D Text Mesh.</span></span> <span data-ttu-id="bcd4d-107">既定では、ぼやけて表示されが大きすぎます。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-107">By default they appear blurry and are too big.</span></span> <span data-ttu-id="bcd4d-108">HoloLens で管理しやすいサイズがシャープな高品質のテキストを取得するいくつかの変数を調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-108">You need to tweak a few variables to get sharp, high-quality text that has a manageable size in HoloLens.</span></span> <span data-ttu-id="bcd4d-109">UI テキストとテキストのメッシュの 3D のコンポーネントを使用する場合は、適切なサイズを取得するスケール ファクターを適用すると、レンダリングの品質が向上を実現できます。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-109">By applying scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components, you can achieve better rendering quality.</span></span>

<span data-ttu-id="bcd4d-110">![鋭いと美しいテキストを取得する方法](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="bcd4d-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="bcd4d-111">*Unity でぼやけての既定のテキスト*</span><span class="sxs-lookup"><span data-stu-id="bcd4d-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-fonts-in-unity"></a><span data-ttu-id="bcd4d-112">Unity でのフォントを操作します。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-112">Working with fonts in Unity</span></span>

<span data-ttu-id="bcd4d-113">Unity では、シーンに追加されたすべての新しい要素が 1 の Unity 単位のサイズ、または 100% の変換スケールは、HoloLens に約 1 メートルに変換を前提としています。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-113">Unity assumes all new elements added to a scene are 1 Unity Unit in size, or 100% transform scale, which translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="bcd4d-114">場合は、フォント 3D TextMesh の境界ボックスは既定では約 1 メートルの高さ。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-114">In the case of fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="bcd4d-115">![Unity でのフォントを操作します。](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="bcd4d-115">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="bcd4d-116">*Unity の既定のテキストが占める 1 メートルである 1 の Unity ユニット*</span><span class="sxs-lookup"><span data-stu-id="bcd4d-116">*Default Unity text occupies 1 Unity Unit which is 1 meter*</span></span>

<br>
<span data-ttu-id="bcd4d-117">ほとんどのビジュアル デザイナーは、現実の世界でフォント サイズを定義するのにポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-117">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="bcd4d-118">約 2835 (2,834.645666399962) がある 1 メートルのポイント。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-118">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="bcd4d-119">1 m と Unity の既定のテキストのメッシュのフォント サイズ 13 からポイント システムへの変換に基づき、2835 equals 0.0046 (正確に 0.004586111116) で割った値 13 の単純な算術を提供する優れた標準スケールで開始する (一部は、0.005 に丸めるにすることがあります)。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-119">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="bcd4d-120">テキスト オブジェクトまたはこれらの値にコンテナーをスケーリングのみを許可しませんフォントの 1 対 1 の変換は、デザイン プログラムのサイズも、アプリケーションやゲーム全体で一貫性を維持するために、標準を提供します。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-120">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your application or game.</span></span>

<span data-ttu-id="bcd4d-121">![別のフォント サイズである unity 3D テキスト メッシュ](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="bcd4d-121">![Unity 3D Text Mesh with different font sizes](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="bcd4d-122">*最適化された値である unity 3D テキスト メッシュ*</span><span class="sxs-lookup"><span data-stu-id="bcd4d-122">*Unity 3D Text Mesh with optimized values*</span></span>

<br>
<span data-ttu-id="bcd4d-123">引き続き UI またはキャンバス ベースのテキストの要素をシーンに追加する際にサイズのような違いが大きいです。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-123">When adding a UI or canvas based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="bcd4d-124">2 つのサイズの相違点が約 1000% を 0.00046 (正確に 0.0004586111116) に基づいた UI テキスト コンポーネントのスケール ファクターがもたらされるまたは 0.0005 の丸められた値。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-124">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="bcd4d-125">![Unity の UI テキスト単位の値ごとに異なる複数の動的なピクセルを](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="bcd4d-125">![Unity UI Text with different dynamic pixels per unit values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="bcd4d-126">*最適化された値を持つ unity UI テキスト*</span><span class="sxs-lookup"><span data-stu-id="bcd4d-126">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="bcd4d-127">任意のフォントの既定値は、そのフォントまたはフォントが Unity にインポートする方法のテクスチャのサイズによって影響可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-127">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="bcd4d-128">これらのテストは、Unity では、既定の Arial フォントおよびその他のインポートされた 1 つのフォントにベースで実行されました。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-128">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="bcd4d-129">適切なディメンションとテキストのレンダリング品質をシャープな</span><span class="sxs-lookup"><span data-stu-id="bcd4d-129">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="bcd4d-130">作成しましたこれらスケーリング要因に基づき、[プレハブの 2 つの UI テキストとテキストを 3D メッシュ](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)します。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-130">Based on these scaling factors, we have created [two prefabs - UI Text and 3D Text Mesh](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs).</span></span> <span data-ttu-id="bcd4d-131">開発者は、これらプレハブを使用して、シャープなテキストと一貫性のあるフォント サイズを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-131">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="bcd4d-132">![適切なディメンションとテキストのレンダリング品質をシャープな](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="bcd4d-132">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="bcd4d-133">*適切なディメンションとテキストのレンダリング品質をシャープな*</span><span class="sxs-lookup"><span data-stu-id="bcd4d-133">*Sharp text rendering quality with proper dimension*</span></span>

## <a name="shader-with-occlusion-support"></a><span data-ttu-id="bcd4d-134">シェーダー オクルー ジョン サポート</span><span class="sxs-lookup"><span data-stu-id="bcd4d-134">Shader with occlusion support</span></span>

<span data-ttu-id="bcd4d-135">Unity の既定のフォントの材料は、オクルー ジョンをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-135">Unity's default font material does not support occlusion.</span></span> <span data-ttu-id="bcd4d-136">このため、既定では、オブジェクトの背後にあるテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-136">Because of this, you will see the text behind the objects by default.</span></span> <span data-ttu-id="bcd4d-137">シンプルな付属[、オクルー ジョンをサポートするシェーダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders)します。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-137">We have included a simple [shader that supports the occlusion](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders).</span></span> <span data-ttu-id="bcd4d-138">次の図は、既定のフォントのマテリアル (左) とテキストと適切なオクルー ジョン (右) を使用してテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-138">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="bcd4d-139">![シェーダー オクルー ジョン サポート](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="bcd4d-139">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="bcd4d-140">*シェーダー オクルー ジョン サポート*</span><span class="sxs-lookup"><span data-stu-id="bcd4d-140">*Shader with occlusion support*</span></span>

## <a name="recommended-type-size"></a><span data-ttu-id="bcd4d-141">推奨される型のサイズ</span><span class="sxs-lookup"><span data-stu-id="bcd4d-141">Recommended type size</span></span>

<span data-ttu-id="bcd4d-142">予想されることができますの 2 m 離れた距離にある非常に小さく、PC またはタブレット デバイス (通常は 12: 32 ポイント) 間を参照してくださいで使用するサイズを入力します。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-142">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="bcd4d-143">各フォントの特性によって異なりますが、一般にストローク振動ことがなく読みやすいように推奨される最小の型のサイズは上で導入されたスケール ファクターに基づく 30pt。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-143">It depends on the characteristics of each font, but in general the recommended minimum type size for legibility without stroke vibration is around 30pt, based on the scaling factor introduced above.</span></span> <span data-ttu-id="bcd4d-144">アプリは、近い距離に使用することになって、比較的小さなサイズの型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-144">If your app is supposed to be used at a closer distance, smaller type sizes could be used.</span></span> <span data-ttu-id="bcd4d-145">フォントの選択、Segoe UI (Windows の既定のフォント) は、ほとんどの場合でも機能します。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-145">For the font selection, Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="bcd4d-146">ただし、振動シンの垂直線と読みやすさが低下するために、42 pt 型のサイズの明るい光または半のフォントを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-146">However, avoid using light or semi light fonts for type sizes under 42pt since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="bcd4d-147">十分なストロークの太さで最新のフォントがうまく機能します。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-147">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="bcd4d-148">たとえば、Helvetica と Arial すばらしい外観になります、通常または太字の重みを持つ、HoloLens で非常に判読可能。</span><span class="sxs-lookup"><span data-stu-id="bcd4d-148">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="bcd4d-149">![推奨される型のサイズ](images/hug-text-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="bcd4d-149">![Recommended type size](images/hug-text-08-1000px.png)</span></span><br>
<span data-ttu-id="bcd4d-150">*種類ごとの傾斜増加の例*</span><span class="sxs-lookup"><span data-stu-id="bcd4d-150">*Type ramp example*</span></span>

## <a name="see-also"></a><span data-ttu-id="bcd4d-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcd4d-151">See also</span></span>
* [<span data-ttu-id="bcd4d-152">MixedRealityToolkit でテキストのプレハブ</span><span class="sxs-lookup"><span data-stu-id="bcd4d-152">Text Prefab in the MixedRealityToolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)
* [<span data-ttu-id="bcd4d-153">テキストのレイアウトのプレハブのサンプルやシーン</span><span class="sxs-lookup"><span data-stu-id="bcd4d-153">Sample text layout prefab and scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX/Scenes)
* [<span data-ttu-id="bcd4d-154">文字体裁</span><span class="sxs-lookup"><span data-stu-id="bcd4d-154">Typography</span></span>](typography.md)

 
