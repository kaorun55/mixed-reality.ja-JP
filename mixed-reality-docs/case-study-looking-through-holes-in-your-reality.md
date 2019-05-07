---
title: 導入事例 - 実際には、セキュリティ ホールを見る
description: このケース スタディでは、ユーザーが、床下と実際の環境内の仮想の開口部には壁の後ろに表示できるように、HoloLens の「マジック ウィンドウ」効果を実装する方法について説明します。
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、マジックのウィンドウで、視差効果
ms.openlocfilehash: 945a09614fbc77400825b524f4e0b591bf7b1f6b
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873935"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a><span data-ttu-id="932c1-104">導入事例 - 実際には、セキュリティ ホールを見る</span><span class="sxs-lookup"><span data-stu-id="932c1-104">Case study - Looking through holes in your reality</span></span>

<span data-ttu-id="932c1-105">ユーザーは、複合現実と Microsoft HoloLens で実行できることを考えて、ときに、通常を引き続き使用質問などの「オブジェクト、ルームに追加できますか」。</span><span class="sxs-lookup"><span data-stu-id="932c1-105">When people think about mixed reality and what they can do with Microsoft HoloLens, they usually stick to questions like "What objects can I add to my room?"</span></span> <span data-ttu-id="932c1-106">または「どのようなことはレイヤー自分のスペースの上にでしょうか。」</span><span class="sxs-lookup"><span data-stu-id="932c1-106">or “What can I layer on top of my space?"</span></span> <span data-ttu-id="932c1-107">検討するもう 1 つの部分を強調表示したい-基本的にマジック — にまたは周囲の実際の物理オブジェクトを検索するのと同じテクノロジを使用して。</span><span class="sxs-lookup"><span data-stu-id="932c1-107">I’d like to highlight another area you can consider—essentially a magic trick—using the same technology to look into or through real physical objects around you.</span></span>

## <a name="the-tech"></a><span data-ttu-id="932c1-108">技術者</span><span class="sxs-lookup"><span data-stu-id="932c1-108">The tech</span></span>

<span data-ttu-id="932c1-109">壁面を克服するように、エイリアンした試合かどうか **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**、壁に安全にロックを解除**[フラグメント](case-study-creating-an-immersive-experience-in-fragments.md)**、運が発生しました。UNSC 無限大格納庫を表示する、  **[E3 2015 で Halo 5 経験](https://www.youtube.com/watch?v=QDw5QjDtFy8)**、話の内容を見ています。</span><span class="sxs-lookup"><span data-stu-id="932c1-109">If you've fought aliens as they break through your walls in **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, unlocked a wall safe in **[Fragments](case-study-creating-an-immersive-experience-in-fragments.md)**, or were lucky enough to see the UNSC Infinity hangar in the **[Halo 5 experience at E3 in 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, then you've seen what I'm talking about.</span></span> <span data-ttu-id="932c1-110">想像力に応じて、drywall に一時的なセキュリティ ホールを配置するか、loose floorboard 下の世界を非表示に、このビジュアルのトリックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="932c1-110">Depending on your imagination, this visual trick can be used to put temporary holes in your drywall or to hide worlds under a loose floorboard.</span></span>

![3 次元のパイプとその他の構造は、壁、侵入者を克服するように作成されたホールによってのみ表示 RoboRaid を追加します。](images/roboraid-640px.png)

<span data-ttu-id="932c1-112">3 次元のパイプとその他の構造は、壁、侵入者を克服するように作成されたホールによってのみ表示 RoboRaid を追加します。</span><span class="sxs-lookup"><span data-stu-id="932c1-112">RoboRaid adds three-dimensional pipes and other structure behind your walls, visible only through holes created as the invaders break through.</span></span>

<span data-ttu-id="932c1-113">HoloLens の一意のホログラムはこれらのいずれかを使用して、アプリは、同様の現実は実際のウィンドウを表示しますまたは、床、壁の背後にあるコンテンツの錯覚を提供できます。</span><span class="sxs-lookup"><span data-stu-id="932c1-113">Using one of these unique holograms on HoloLens, an app can provide the illusion of content behind your walls or through your floor in the same way that reality presents itself through an actual window.</span></span> <span data-ttu-id="932c1-114">左、自分で移動しが右側にあるを参照してください。</span><span class="sxs-lookup"><span data-stu-id="932c1-114">Move yourself left, and you can see whatever is on the right side.</span></span> <span data-ttu-id="932c1-115">、近づくし、すべての複数のビットを確認できます。</span><span class="sxs-lookup"><span data-stu-id="932c1-115">Get closer, and you can see a bit more of everything.</span></span> <span data-ttu-id="932c1-116">主な違いは、実際の穴ことが許可される、を通じて、フロアがシリアルすることはできません holographic 魔法のようなコンテンツに上昇中です。</span><span class="sxs-lookup"><span data-stu-id="932c1-116">The major difference is that real holes allow you through, while your floor stubbornly won't let you climb through to that magical holographic content.</span></span> <span data-ttu-id="932c1-117">(は、タスク バックログを追加します、。)</span><span class="sxs-lookup"><span data-stu-id="932c1-117">(I'll add a task to the backlog.)</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="932c1-118">しくみ</span><span class="sxs-lookup"><span data-stu-id="932c1-118">Behind the scenes</span></span>

<span data-ttu-id="932c1-119">この方法は、2 つの効果の組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="932c1-119">This trick is a combination of two effects.</span></span> <span data-ttu-id="932c1-120">まず、holographic のコンテンツが「空間のアンカー」を使用して、世界中にピン留め</span><span class="sxs-lookup"><span data-stu-id="932c1-120">First, holographic content is pinned to the world using "spatial anchors."</span></span> <span data-ttu-id="932c1-121">アンカーを使用することでそのコンテンツを「world ロック」することで表示されているが視覚的にドリフト近くに、物理オブジェクトから移動した場合や、基になる空間マッピング システムの部屋の 3D モデルを更新してを意味します。</span><span class="sxs-lookup"><span data-stu-id="932c1-121">Using anchors to make that content "world-locked" means that what you're looking at doesn't visually drift away from the physical objects near it, even as you move or the underlying spatial mapping system updates its 3D model of your room.</span></span>

<span data-ttu-id="932c1-122">第二に、holographic コンテンツは、のみ、実際には、穴を確認できるように、非常に特定の領域に視覚的に制限されます。</span><span class="sxs-lookup"><span data-stu-id="932c1-122">Secondly, that holographic content is visually limited to a very specific space, so you can only see through the hole in your reality.</span></span> <span data-ttu-id="932c1-123">そのオクルー ジョン論理穴、ウィンドウ、または、トリックを販売するには、ドアを検索を要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="932c1-123">That occlusion is necessary to require looking through a logical hole, window, or doorway, which sells the trick.</span></span> <span data-ttu-id="932c1-124">ビューのほとんどをブロックしているものシークレット ジュラシック ディメンションへの領域でのクラック可能性があります適切に配置された恐竜のようになりますだけです。</span><span class="sxs-lookup"><span data-stu-id="932c1-124">Without something blocking most of the view, a crack in space to a secret Jurassic dimension might just look like a poorly placed dinosaur.</span></span>

![これはなく実際のスクリーン ショット、HoloLens 上 MR 基本 101 からシークレット黄泉の外観の例です。](images/origamiholecomposited-640px.png)

<span data-ttu-id="932c1-128">これはなく実際のスクリーン ショット、方法を示してからシークレット黄泉、 [MR 基本 101](holograms-101.md) HoloLens で検索します。</span><span class="sxs-lookup"><span data-stu-id="932c1-128">This is not an actual screenshot, but an illustration of how the secret underworld from the [MR Basics 101](holograms-101.md) looks on HoloLens.</span></span> <span data-ttu-id="932c1-129">黒のエンクロージャは表示しませんが、仮想穴経由でコンテンツを確認できます。</span><span class="sxs-lookup"><span data-stu-id="932c1-129">The black enclosure doesn’t show up, but you can see content through a virtual hole.</span></span> <span data-ttu-id="932c1-130">(実際のデバイスを検索、ときに、フロアに思えますがあっても存在しない場合、それ以上の距離にある対象に見られるので、さらに表示されなくなります。)</span><span class="sxs-lookup"><span data-stu-id="932c1-130">(When looking through an actual device, the floor would seem to disappear even more because your eyes focus at a further distance as if it’s not even there.)</span></span>

### <a name="world-locking-holographic-content"></a><span data-ttu-id="932c1-131">Holographic のコンテンツを世界中のロック</span><span class="sxs-lookup"><span data-stu-id="932c1-131">World-locking holographic content</span></span>

<span data-ttu-id="932c1-132">Unity では、世界中のロックを維持する holographic のコンテンツの原因と WorldAnchor コンポーネントを追加するだけです。</span><span class="sxs-lookup"><span data-stu-id="932c1-132">In Unity, causing holographic content to stay world-locked is as easy as adding a WorldAnchor component:</span></span>

```
myObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="932c1-133">WorldAnchor コンポーネントは、位置と回転の GameObject (したがって、階層内には、そのオブジェクトの下のもの) の近くにある物理オブジェクトに対して相対的な安定に保つために絶えず調整します。</span><span class="sxs-lookup"><span data-stu-id="932c1-133">The WorldAnchor component will constantly adjust the position and rotation of its GameObject (and thus anything else under that object in the hierarchy) to keep it stable relative to nearby physical objects.</span></span> <span data-ttu-id="932c1-134">コンテンツを作成するときは、この仮想の穴に中央揃え、オブジェクトのルート ピボットされているように作成します。</span><span class="sxs-lookup"><span data-stu-id="932c1-134">When authoring your content, create it in such a way that the root pivot of your object is centered at this virtual hole.</span></span> <span data-ttu-id="932c1-135">(位置と回転に若干の調整は非常に顕著になるオブジェクトのピボットが壁の深い場所にある場合は、および穴は非常に安定した見えない可能性があります。)</span><span class="sxs-lookup"><span data-stu-id="932c1-135">(If your object's pivot is deep in the wall, its slight tweaks in position and rotation will be much more noticeable, and the hole may not look very stable.)</span></span>

### <a name="occluding-everything-but-the-virtual-hole"></a><span data-ttu-id="932c1-136">すべてが仮想の穴を occluding</span><span class="sxs-lookup"><span data-stu-id="932c1-136">Occluding everything but the virtual hole</span></span>

<span data-ttu-id="932c1-137">これは、さまざまな方法は、壁に何が非表示にビューを選択的にブロックします。</span><span class="sxs-lookup"><span data-stu-id="932c1-137">There are a variety of ways to selectively block the view to what is hidden in your walls.</span></span> <span data-ttu-id="932c1-138">最も簡単なものでは、HoloLens が完全に黒のオブジェクトが非表示に表示されることを意味する、付加的な表示を使用するという事実を利用します。</span><span class="sxs-lookup"><span data-stu-id="932c1-138">The simplest one takes advantage of the fact that HoloLens uses an additive display, which means that fully black objects appear invisible.</span></span> <span data-ttu-id="932c1-139">これを行う Unity で任意の特殊なシェーダーや材料コツを行わず、黒のマテリアルを作成し、コンテンツ ボックス オブジェクトに割り当てることだけです。</span><span class="sxs-lookup"><span data-stu-id="932c1-139">You can do this in Unity without doing any special shader or material tricks— just create a black material and assign it to an object that boxes in your content.</span></span> <span data-ttu-id="932c1-140">たくない場合 3D モデリングを行うように、いくつかの既定の 4 つのオブジェクトを使用し、それらを少し重複だけです。</span><span class="sxs-lookup"><span data-stu-id="932c1-140">If you don't feel like doing 3D modeling, just use a handful of default Quad objects and overlap them slightly.</span></span> <span data-ttu-id="932c1-141">このアプローチの欠点がいくつかが動作、ものを取得する最も簡単な方法は、後でそれをリファクタリングする可能性がある場合でも、優れたが低忠実度の作業の概念実証を取得します。</span><span class="sxs-lookup"><span data-stu-id="932c1-141">There are a number of drawbacks to this approach, but it is the fastest way to get something working, and getting a low-fidelity proof of concept working is great, even if you suspect you might want to refactor it later.</span></span>

<span data-ttu-id="932c1-142">前述の「ブラック_ボックス」アプローチを 1 つの主な欠点は、も写真しないことです。</span><span class="sxs-lookup"><span data-stu-id="932c1-142">One major drawback to the above "black box" approach is that it doesn't photograph well.</span></span> <span data-ttu-id="932c1-143">効果は、HoloLens の表示を最適に見える場合があります、床、壁の残ったものではなく黒の大きなオブジェクトが行うすべてのスクリーン ショットに表示されます。</span><span class="sxs-lookup"><span data-stu-id="932c1-143">While your effect might look perfect through the display of HoloLens, any screenshots you take will show a large black object instead of what remains of your wall or floor.</span></span> <span data-ttu-id="932c1-144">この理由は物理ハードウェアとスクリーン ショット複合ホログラムと現実が異なります。</span><span class="sxs-lookup"><span data-stu-id="932c1-144">The reason for this is that the physical hardware and screenshots composite holograms and reality differently.</span></span> <span data-ttu-id="932c1-145">偽のいくつかの計算には、少し迂回しましょう.</span><span class="sxs-lookup"><span data-stu-id="932c1-145">Let's detour for a moment into some fake math...</span></span>

<span data-ttu-id="932c1-146">*偽の数値演算警告!これらの番号と数式についてに何らかの正確なメトリックの要点を説明するものです。*</span><span class="sxs-lookup"><span data-stu-id="932c1-146">*Fake math alert! These numbers and formulas are meant to illustrate a point, not to be any sort of accurate metric!*</span></span>

<span data-ttu-id="932c1-147">表示される内容 HoloLens 経由。</span><span class="sxs-lookup"><span data-stu-id="932c1-147">What you see through HoloLens:</span></span>

```
( Reality * darkening_amount ) + Holograms
```

<span data-ttu-id="932c1-148">表示される内容のスクリーン ショットやビデオ。</span><span class="sxs-lookup"><span data-stu-id="932c1-148">What you see in screenshots and video:</span></span>

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

<span data-ttu-id="932c1-149">英語版。暗くなった現実 (サングラスを通じてなど) と任意の単純な組み合わせは、HoloLens を参照してくださいホログラム、アプリを表示することです。</span><span class="sxs-lookup"><span data-stu-id="932c1-149">In English: What you see through HoloLens is a simple combination of darkened reality (like through sunglasses) and whatever holograms the app wants to show.</span></span> <span data-ttu-id="932c1-150">スクリーン ショットを取得するとき、カメラの画像は、ピクセルあたりの透明度の値に従って、アプリのホログラムとブレンドされます。</span><span class="sxs-lookup"><span data-stu-id="932c1-150">But when you take a screenshot, the camera's image is blended with the app's holograms according to the per-pixel transparency value.</span></span>

<span data-ttu-id="932c1-151">この問題を回避する方法の 1 つでは、のみ、深度バッファーに書き込むし、その他のすべての非透過マテリアルに並べ替えを「ブラック_ボックス」マテリアルを変更します。</span><span class="sxs-lookup"><span data-stu-id="932c1-151">One way to get around this is to change the "black box" material to only write to the depth buffer, and sort with all the other opaque materials.</span></span> <span data-ttu-id="932c1-152">この例では、チェック アウト、 [GitHub、MixedRealityToolkit に WindowOcclusion.shader ファイル](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)します。</span><span class="sxs-lookup"><span data-stu-id="932c1-152">For an example of this, check out the [WindowOcclusion.shader file in the MixedRealityToolkit on GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader).</span></span> <span data-ttu-id="932c1-153">ここで、該当する行がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="932c1-153">The relevant lines are copied here:</span></span>

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

<span data-ttu-id="932c1-154">(「オフセット 50 で 100」に注意してください行が問題に対処する関連のない、おそらく合理的を除外するためです)。</span><span class="sxs-lookup"><span data-stu-id="932c1-154">(Note the "Offset 50, 100" line is to deal with unrelated issues, so it'd probably make sense to leave that out.)</span></span>

<span data-ttu-id="932c1-155">そのような非表示のオクルー ジョン マテリアルを実装すると、アプリは次の表示にし、複合現実のスクリーン ショットでは適切なボックスを描画します。</span><span class="sxs-lookup"><span data-stu-id="932c1-155">Implementing an invisible occlusion material like that will let your app draw a box that looks correct in the display and in mixed-reality screenshots.</span></span> <span data-ttu-id="932c1-156">ボーナス ポイントも非表示 (ピクセル単位) を描画するために巧妙な処理を実行して、さらにそのボックスのパフォーマンスを改善しようとすることができますが、雑草を実際に取得できるを通常は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="932c1-156">For bonus points, you can try to improve the performance of that box even further by doing clever things to draw even fewer invisible pixels, but that can really get into the weeds and usually won't be necessary.</span></span>

![Unity を描画し、他のボックスの外側の部分を除くここではシークレット黄泉 MR 基本 101 からです。](images/underworld-occluded-640px.png)

<span data-ttu-id="932c1-159">ここからシークレット黄泉[MR 基本 101](holograms-101.md) Unity を描画し、他のボックスの外側の部分を除く。</span><span class="sxs-lookup"><span data-stu-id="932c1-159">Here is the secret underworld from [MR Basics 101](holograms-101.md) as Unity draws it, except for the outer parts of the occluding box.</span></span> <span data-ttu-id="932c1-160">黄泉のピボットが穴の維持、ボックスの中央に、実際の現場の基準としたできるだけ安定に注意してください。</span><span class="sxs-lookup"><span data-stu-id="932c1-160">Note that the pivot for the underworld is at the center of the box, which helps keep the hole as stable as possible relative to your actual floor.</span></span>

## <a name="do-it-yourself"></a><span data-ttu-id="932c1-161">自分で行う</span><span class="sxs-lookup"><span data-stu-id="932c1-161">Do it yourself</span></span>

<span data-ttu-id="932c1-162">HoloLens があるし、自分の効果を試したいですか。</span><span class="sxs-lookup"><span data-stu-id="932c1-162">Have a HoloLens and want to try out the effect for yourself?</span></span> <span data-ttu-id="932c1-163">無料の 3D のビューアー アプリをインストールして読み込むに最も簡単な (コーディングは不要) を行うことができますが、[ダウンロード the.fbx ファイルが GitHub で紹介した](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow)の部屋で花 pot モデルを表示します。</span><span class="sxs-lookup"><span data-stu-id="932c1-163">The easiest thing you can do (no coding required) is to install the free 3D Viewer app and then load the [download the.fbx file I've provided on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) to view a flower pot model in your room.</span></span> <span data-ttu-id="932c1-164">HoloLens にロードすることと、職場で錯覚を確認できます。</span><span class="sxs-lookup"><span data-stu-id="932c1-164">Load it on HoloLens, and you can see the illusion at work.</span></span> <span data-ttu-id="932c1-165">小規模の穴にのみ表示できること、モデルの前にしたら、-他のすべては表示されません。</span><span class="sxs-lookup"><span data-stu-id="932c1-165">When you're in front of the model, you can only see into the small hole—everything else is invisible.</span></span> <span data-ttu-id="932c1-166">その他の任意の辺からモデルを見るし、それはまったく表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="932c1-166">Look at the model from any other side and it disappears entirely.</span></span> <span data-ttu-id="932c1-167">移動、回転、および 3D ビューアーのスケールのコントロールを使用して、いくつかのアイデアを生成する考えることができます、垂直方向の画面に対して仮想穴の位置します。</span><span class="sxs-lookup"><span data-stu-id="932c1-167">Use the movement, rotation, and scale controls of 3D Viewer to position the virtual hole against any vertical surface you can think of to generate some ideas!</span></span>

![Unity エディターでこのモデルの表示、flowerpot 周囲に大きな黒いボックスが表示されます。](images/magicwindowflowerpotineditor.png)

<span data-ttu-id="932c1-170">Unity エディターでこのモデルの表示、flowerpot 周囲に大きな黒いボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="932c1-170">Viewing this model in your Unity editor will show a large black box around the flowerpot.</span></span> <span data-ttu-id="932c1-171">HoloLens で、ボックスは表示されなくなります、マジック ウィンドウ有効する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="932c1-171">On HoloLens, the box disappears, giving way to a magic window effect.</span></span>

<span data-ttu-id="932c1-172">この手法を使用するアプリをビルドする場合は、チェック アウト、 [MR 基本の 101 チュートリアル](holograms-101.md)で、 [Mixed Reality チュートリアル](tutorials.md)します。</span><span class="sxs-lookup"><span data-stu-id="932c1-172">If you want to build an app that uses this technique, check out the [MR Basics 101 tutorial](holograms-101.md) in the [Mixed Reality tutorials](tutorials.md).</span></span> <span data-ttu-id="932c1-173">第 7 章では、(上記の絵) として非表示の黄泉を表示する、フロアが急増で終わります。</span><span class="sxs-lookup"><span data-stu-id="932c1-173">Chapter 7 ends with an explosion in your floor that reveals a hidden underworld (as pictured above).</span></span> <span data-ttu-id="932c1-174">誰のチュートリアルを退屈させる必要があるか。</span><span class="sxs-lookup"><span data-stu-id="932c1-174">Who said tutorials had to be boring?</span></span>

<span data-ttu-id="932c1-175">ここでは、実行できるこのアイデア [次へ] の。</span><span class="sxs-lookup"><span data-stu-id="932c1-175">Here are some ideas of where you can take this idea next:</span></span>
* <span data-ttu-id="932c1-176">仮想穴内で対話型コンテンツを作成する方法と考えてください。</span><span class="sxs-lookup"><span data-stu-id="932c1-176">Think of ways to make the content inside the virtual hole interactive.</span></span> <span data-ttu-id="932c1-177">壁のいくつかの影響を与えるユーザーのも無理はこの方法を提供できるという意味が実際に向上します。</span><span class="sxs-lookup"><span data-stu-id="932c1-177">Letting your users have some impact beyond their walls can really improve the sense of wonder that this trick can provide.</span></span>
* <span data-ttu-id="932c1-178">既知の領域にオブジェクトを表示する方法と考えてください。</span><span class="sxs-lookup"><span data-stu-id="932c1-178">Think of ways to see through objects back to known areas.</span></span> <span data-ttu-id="932c1-179">たとえば、方法する holographic 穴コーヒー テーブルをできます、フロアをその下にあるを参照してくださいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="932c1-179">For example, how can you put a holographic hole in your coffee table and see your floor beneath it?</span></span>

## <a name="about-the-author"></a><span data-ttu-id="932c1-180">執筆者紹介</span><span class="sxs-lookup"><span data-stu-id="932c1-180">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><span data-ttu-id="932c1-181"><b>Eric Rehmeyer</b></span><span class="sxs-lookup"><span data-stu-id="932c1-181"><b>Eric Rehmeyer</b></span></span><br><span data-ttu-id="932c1-182">シニア ソフトウェア エンジニア @Microsoft</span><span class="sxs-lookup"><span data-stu-id="932c1-182">Senior Software Engineer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="932c1-183">関連項目</span><span class="sxs-lookup"><span data-stu-id="932c1-183">See also</span></span>
* [<span data-ttu-id="932c1-184">MR の基本 101:デバイスを使用した完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="932c1-184">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="932c1-185">座標系</span><span class="sxs-lookup"><span data-stu-id="932c1-185">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="932c1-186">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="932c1-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="932c1-187">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="932c1-187">Spatial mapping</span></span>](spatial-mapping.md)
