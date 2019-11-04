---
title: ケーススタディ-mixed reality での galaxy の作成
description: Microsoft HoloLens を出荷する前に、開発者コミュニティに、新しいデバイスに対して経験豊富な内部チームビルドを表示するアプリの種類を尋ねました。 5000を超えるアイデアが共有されており、24時間の Twitter の投票の後、優勝者は "Galaxy エクスプローラ" という考え方でした。
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy エクスプローラー、HoloLens、Windows Mixed Reality、アイデアの共有、ケーススタディ
ms.openlocfilehash: 696662eb92371708389f8a128dcee6a61acf1816
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436880"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="16aa7-105">ケーススタディ-mixed reality での galaxy の作成</span><span class="sxs-lookup"><span data-stu-id="16aa7-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="16aa7-106">Microsoft HoloLens を出荷する前に、開発者コミュニティに、新しいデバイスに対して経験豊富な内部チームビルドを表示するアプリの種類を尋ねました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="16aa7-107">5000を超えるアイデアが共有されており、24時間の Twitter に投票した後、優勝者は[Galaxy エクスプローラ](galaxy-explorer.md)という考え方でした。</span><span class="sxs-lookup"><span data-stu-id="16aa7-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="16aa7-108">Andy Zibits、プロジェクトのアートリーダー、およびチームのグラフィックスエンジニアである Karim Luccin は、Galaxy エクスプローラーでの天の川向 galaxy の正確で対話的な表現を作成するための、アートとエンジニアリングの間の共同作業について説明しています。</span><span class="sxs-lookup"><span data-stu-id="16aa7-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="16aa7-109">技術</span><span class="sxs-lookup"><span data-stu-id="16aa7-109">The Tech</span></span>

<span data-ttu-id="16aa7-110">[私たちのチーム](galaxy-explorer.md#meet-the-team)は、3つの開発者、3人のアーティスト、プロデューサー、1人のテスト担当者で構成されており、6週間で完全に機能するアプリを構築しました。これにより、天の川のような優れた方法を習得し、その結果を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="16aa7-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="16aa7-111">HoloLens の能力を最大限に活用して、お客様の生きた空間で3D オブジェクトを直接表示することを望んでいました。したがって、ユーザーが近くに拡大して個々の星を見ることができる現実的な外観の galaxy を作成することにしました.</span><span class="sxs-lookup"><span data-stu-id="16aa7-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="16aa7-112">開発の最初の週では、天の川方法の表記についていくつかの目標がありました。これは、高度、動き、および感覚容量を必要としています。これは、galaxy の形の作成に役立つ星です。</span><span class="sxs-lookup"><span data-stu-id="16aa7-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="16aa7-113">数十億の星を持つアニメーションの galaxy の作成に問題があるのは、更新が必要な1つの要素の数が、HoloLens が CPU を使用してアニメーション化するためのフレームごとに大きすぎるということでした。</span><span class="sxs-lookup"><span data-stu-id="16aa7-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="16aa7-114">このソリューションでは、アートとサイエンスが複雑に組み合わされていました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="16aa7-115">しくみ</span><span class="sxs-lookup"><span data-stu-id="16aa7-115">Behind the scenes</span></span>

<span data-ttu-id="16aa7-116">個々の星を調べることができるように、最初の手順は、一度にレンダリングできるパーティクルの数を調べることでした。</span><span class="sxs-lookup"><span data-stu-id="16aa7-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="16aa7-117">描画 (パーティクルを)</span><span class="sxs-lookup"><span data-stu-id="16aa7-117">Rendering particles</span></span>

<span data-ttu-id="16aa7-118">現在の Cpu は、直列タスクを処理し、同時にいくつかの並列タスクを (コア数に応じて) 処理する場合に適していますが、Gpu は、何千もの操作を並列処理するよりもはるかに効果的です。</span><span class="sxs-lookup"><span data-stu-id="16aa7-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="16aa7-119">ただし、通常は CPU と同じメモリを共有しないので、CPU < > GPU 間でデータを交換すると、すぐにボトルネックになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16aa7-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="16aa7-120">このソリューションでは、GPU 上に galaxy を作成し、GPU 上で完全に稼働させる必要がありました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="16aa7-121">さまざまなパターンで何千ものポイントパーティクルを使用してストレステストを開始しました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="16aa7-122">これにより、HoloLens で galaxy を取得して、動作した機能と失敗したことを確認することができました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="16aa7-123">星の位置の作成</span><span class="sxs-lookup"><span data-stu-id="16aa7-123">Creating the position of the stars</span></span>

<span data-ttu-id="16aa7-124">チームメンバーの1人が、最初のC#位置に星を生成するコードを既に作成しています。</span><span class="sxs-lookup"><span data-stu-id="16aa7-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="16aa7-125">星は楕円上にあり、その位置は (**curveoffset**、 **ellipseSize**、**標高**) で記述できます。 **curveoffset**は楕円に沿った星の角度で、 **ellipseSize**は楕円の次元です。X と Z に沿って、galaxy 内の星の適切な昇格が昇格します。</span><span class="sxs-lookup"><span data-stu-id="16aa7-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="16aa7-126">このため、各スター属性で初期化されるバッファー ([Unity の ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) を作成し、それを GPU に送信して、残りのエクスペリエンスに使用することができます。</span><span class="sxs-lookup"><span data-stu-id="16aa7-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="16aa7-127">このバッファーを描画するには、 [Unity の DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html)を使用します。これにより、galaxy を表す実際のメッシュがなくても、任意のポイントのセットに対してシェーダー (GPU 上のコード) を実行できます。</span><span class="sxs-lookup"><span data-stu-id="16aa7-127">To draw this buffer, we use [Unity’s DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="16aa7-128">**CPU**</span><span class="sxs-lookup"><span data-stu-id="16aa7-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="16aa7-129">**GPU**</span><span class="sxs-lookup"><span data-stu-id="16aa7-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="16aa7-130">私たちは、何千ものパーティクルを含む生の円形パターンから始めました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="16aa7-131">これにより、多数のパーティクルを管理し、パフォーマンスの高い速度で実行できるようにする必要があることが証明されましたが、galaxy の全体的な構造には満足できませんでした。</span><span class="sxs-lookup"><span data-stu-id="16aa7-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="16aa7-132">図形を改良するために、回転を使用してさまざまなパターンとパーティクルシステムを試しました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="16aa7-133">これらは、パーティクルとパフォーマンスの数が一貫していても、中心の近くにある形状が、現実的ではないとを発していたため、当初は実現されていました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="16aa7-134">時間を操作できるようにするための出力が必要でした。また、パーティクルは現実的に動き、galaxy の中心に近いループが発生します。</span><span class="sxs-lookup"><span data-stu-id="16aa7-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![このように、回転したさまざまなパターンとパーティクルシステムを試しました。](images/galaxy-patterns-500px.png)

<span data-ttu-id="16aa7-136">このように、回転したさまざまなパターンとパーティクルシステムを試しました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="16aa7-137">私たちのチームは、galaxies の機能についていくつかの調査を行ってきました。これは、"[密度の波理論](https://en.wikipedia.org/wiki/Density_wave_theory)" に基づいて楕円に対してパーティクルを移動できるようにするためのカスタムパーティクルシステムを作成しました。これにより、galaxy のアームは次の領域になります。密度は高くなりますが、トラフィックが詰まっているように一定の流束になります。</span><span class="sxs-lookup"><span data-stu-id="16aa7-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="16aa7-138">これは安定した安定したように見えますが、各星はそれぞれの楕円に沿って移動されるため、実際には腕に沿って移動します。</span><span class="sxs-lookup"><span data-stu-id="16aa7-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="16aa7-139">システムでは、パーティクルが CPU 上に存在することはありません。カードを生成し、GPU 上にすべてを回転させるので、システム全体が単に初期状態 + 時間になります。</span><span class="sxs-lookup"><span data-stu-id="16aa7-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="16aa7-140">次のように進行します。</span><span class="sxs-lookup"><span data-stu-id="16aa7-140">It progressed like this:</span></span>

![GPU レンダリングを使用したパーティクルシステムの進行状況](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="16aa7-142">GPU レンダリングを使用したパーティクルシステムの進行状況</span><span class="sxs-lookup"><span data-stu-id="16aa7-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="16aa7-143">いくつかの省略記号が追加され、回転するように設定されると、galaxies は、星の動きが収束する "腕" の形成を開始しました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="16aa7-144">各楕円パスに沿った星の間隔はランダムに指定されており、各星はランダムに追加されています。</span><span class="sxs-lookup"><span data-stu-id="16aa7-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="16aa7-145">これにより、スター移動と arm 図形のより自然な外観の分布が作成されました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="16aa7-146">最後に、中央からの距離に基づいて色を設定する機能を追加しました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="16aa7-147">星の動きの作成</span><span class="sxs-lookup"><span data-stu-id="16aa7-147">Creating the motion of the stars</span></span>

<span data-ttu-id="16aa7-148">一般的な星の動きをアニメーション化するには、各フレームに対して一定の角度を追加し、楕円を一定の放射状速度で移動させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="16aa7-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="16aa7-149">これは**Curveoffset**を使用する主な理由です。</span><span class="sxs-lookup"><span data-stu-id="16aa7-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="16aa7-150">これは技術的には適切ではありません。星が楕円の長い方に沿って速く移動しますが、一般的な動きは良いと感じます。</span><span class="sxs-lookup"><span data-stu-id="16aa7-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![星が長すぎるほど、エッジで速度が遅くなります。](images/ellipse-movement.jpg)

<span data-ttu-id="16aa7-152">星が長すぎるほど、エッジで速度が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="16aa7-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="16aa7-153">これにより、各星は (**Curveoffset**、 **ellipseSize**、**標高**、 **age**) によって完全に記述されます。 **age**は、シーンが読み込まれてから経過した合計時間を累積したものです。</span><span class="sxs-lookup"><span data-stu-id="16aa7-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

<span data-ttu-id="16aa7-154">これにより、アプリケーションの開始時に数十の星が生成され、確立された曲線に沿って単一の星のセットがアニメーション化されました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="16aa7-155">すべてが GPU 上にあるため、システムはすべての星を並行して CPU に対して無料でアニメーション化できます。</span><span class="sxs-lookup"><span data-stu-id="16aa7-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![白の四角形を描画すると、次のようになります。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="16aa7-157">白の四角形を描画すると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="16aa7-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="16aa7-158">各 quad をカメラにするために、ジオメトリシェーダーを使用して、星のテクスチャを含む画面上の2D 四角形にそれぞれの星の位置を変換します。</span><span class="sxs-lookup"><span data-stu-id="16aa7-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![四角形ではなくダイヤ。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="16aa7-160">四角形ではなくダイヤ。</span><span class="sxs-lookup"><span data-stu-id="16aa7-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="16aa7-161">できるだけ多くのオーバースペース (ピクセルが処理される回数) を制限するために、2つの四角形を回転させて重なりが小さくなるようにしました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="16aa7-162">クラウドの追加</span><span class="sxs-lookup"><span data-stu-id="16aa7-162">Adding clouds</span></span>

<span data-ttu-id="16aa7-163">1つのボリューム内の射線の回転から、クラウドをシミュレートするためにできるだけ多くのパーティクルを描画するなど、さまざまな方法で、容量の感覚を取得できます。</span><span class="sxs-lookup"><span data-stu-id="16aa7-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="16aa7-164">リアルタイムの光の回転はコストが高く、作成が困難になってきました。そのため、最初にゲームでフォレストをレンダリングするためのメソッドを使用してなりすましシステムを構築しようとしました。これは、カメラに面しているツリーの2D イメージを多数備えています。</span><span class="sxs-lookup"><span data-stu-id="16aa7-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="16aa7-165">ゲームでこの操作を行うと、カメラのテクスチャを描画して、回転させたり、すべてのイメージを保存したり、各ビルボードカードの実行時に、ビューの方向に一致する画像を選択したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="16aa7-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="16aa7-166">これは、イメージがホログラムである場合にも機能しません。</span><span class="sxs-lookup"><span data-stu-id="16aa7-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="16aa7-167">左目と右目の違いによって、より高い解像度が必要になるようになります。または、単純、エイリアス、または反復的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="16aa7-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="16aa7-168">2回目の試行では、できるだけ多くのパーティクルを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="16aa7-169">シーンに追加する前に、パーティクルを描画してぼかしを加算したときに最適なビジュアルが得られました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="16aa7-170">このアプローチに関する一般的な問題は、一度に描画できるパーティクルの数と、60 fps を維持しながらカバーされる画面領域の量に関連していました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="16aa7-171">このクラウドを実現するために生成されたイメージをぼかすことは、通常、非常にコストのかかる操作でした。</span><span class="sxs-lookup"><span data-stu-id="16aa7-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![テクスチャを使用しない場合、雲は2% の不透明度で表示されます。](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="16aa7-173">テクスチャを使用しない場合、雲は2% の不透明度で表示されます。</span><span class="sxs-lookup"><span data-stu-id="16aa7-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="16aa7-174">さらに多くのものが含まれているので、複数の四角形を相互に並べて、同じピクセルの網掛けを繰り返すことになります。</span><span class="sxs-lookup"><span data-stu-id="16aa7-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="16aa7-175">Galaxy の中央では、同じピクセルに何百もの四角形が含まれており、全画面表示が完了すると、非常にコストがかかりました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="16aa7-176">全画面表示のクラウドを使用して、その効果をぼかすことは、それほど問題にはなりませんでした。その代わりに、ハードウェアで私たちの作業を行うことにしました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="16aa7-177">最初は少しコンテキスト</span><span class="sxs-lookup"><span data-stu-id="16aa7-177">A bit of context first</span></span>

<span data-ttu-id="16aa7-178">ゲームでテクスチャを使用する場合、テクスチャサイズはそれを使用する領域とほとんど一致しませんが、さまざまな種類のテクスチャフィルターを使用して、グラフィックカードを取得し、テクスチャのピクセルから必要な色を補間することができます ([テクスチャフィルター](https://msdn.microsoft.com/library/dn642451.aspx))。</span><span class="sxs-lookup"><span data-stu-id="16aa7-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="16aa7-179">興味のあるフィルター処理は、近接している4つの近隣ノードを使用して任意のピクセルの値を計算する、[バイリニアフィルター](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="16aa7-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![フィルター処理前の元](images/texture-1.png)

![フィルター処理後の結果](images/texture-2.png)

<span data-ttu-id="16aa7-182">このプロパティを使用すると、テクスチャを領域に2倍の大きさで描画しようとするたびに、結果がぼかしられることがわかります。</span><span class="sxs-lookup"><span data-stu-id="16aa7-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="16aa7-183">全画面表示ではなく、貴重な時間を無駄にしてしまうのではなく、画面の小さなバージョンにレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="16aa7-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="16aa7-184">次に、このテクスチャをコピーして2倍の量で拡大することで、プロセスの内容をぼかしながら全画面表示に戻ります。</span><span class="sxs-lookup"><span data-stu-id="16aa7-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![x3 upscale を完全に解決します。](images/galaxy-resolutions-300px.png)

<span data-ttu-id="16aa7-186">x3 upscale を完全に解決します。</span><span class="sxs-lookup"><span data-stu-id="16aa7-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="16aa7-187">これにより、元のコストのほんの一部のみを使用してクラウドパーツを取得できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="16aa7-188">完全な解像度でクラウドを追加するのではなく、ピクセルの 1/64th のみを描画し、テクスチャを完全解像度に引き伸ばすだけです。</span><span class="sxs-lookup"><span data-stu-id="16aa7-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![左側には、1 ~ 8 の upscale があります。そして、3 upscale を使用すると、2の累乗が使用されます。](images/stars-upscaled-300px.jpg)

<span data-ttu-id="16aa7-190">左側には、1 ~ 8 の upscale があります。そして、3 upscale を使用すると、2の累乗が使用されます。</span><span class="sxs-lookup"><span data-stu-id="16aa7-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="16aa7-191">サイズの 1/64th から、1つの場所で完全なサイズに移行しようとしても、グラフィックカードではセットアップで4ピクセルが使用され、より大きな領域に影が付けられ、アイテムが表示されるようになるため、まったく異なる結果になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="16aa7-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="16aa7-192">次に、小さなカードを使用して完全な解像度の星を追加すると、完全な galaxy が得られます。</span><span class="sxs-lookup"><span data-stu-id="16aa7-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![完全解決星を使用した galaxy レンダリングの最終結果](images/full-galaxy-500px.png)

<span data-ttu-id="16aa7-194">図形を適切に追跡した後、クラウドのレイヤーを追加し、Photoshop で描画したものと一時的なドットを入れ替え、追加の色を追加しました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="16aa7-195">結果として、アートチームとエンジニアリングチームの両方が優れていることを天の川しています。これは、CPU に負担をかけることなく、深さ、ボリューム、および運動の目標を達成しました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![3D の最終的な天の川方法です。](images/final-galaxy-500px.jpg)

<span data-ttu-id="16aa7-197">3D の最終的な天の川方法です。</span><span class="sxs-lookup"><span data-stu-id="16aa7-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="16aa7-198">詳細を見る</span><span class="sxs-lookup"><span data-stu-id="16aa7-198">More to explore</span></span>

<span data-ttu-id="16aa7-199">Galaxy エクスプローラーアプリのコードをオープンソース化し、開発者向けに[GitHub](https://github.com/Microsoft/GalaxyExplorer)で利用できるようにしました。</span><span class="sxs-lookup"><span data-stu-id="16aa7-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="16aa7-200">Galaxy エクスプローラーの開発プロセスの詳細については、</span><span class="sxs-lookup"><span data-stu-id="16aa7-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="16aa7-201">[Microsoft HoloLens YouTube チャネル](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)で、過去のすべてのプロジェクト更新を確認してください。</span><span class="sxs-lookup"><span data-stu-id="16aa7-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="16aa7-202">作成者について</span><span class="sxs-lookup"><span data-stu-id="16aa7-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="16aa7-203"><b>Karim Luccin</b>は、ソフトウェアエンジニアや凝ったビジュアルです。</span><span class="sxs-lookup"><span data-stu-id="16aa7-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="16aa7-204">彼は、Galaxy エクスプローラーのグラフィックスエンジニアでした。</span><span class="sxs-lookup"><span data-stu-id="16aa7-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="16aa7-205"><b>Andy Zibits</b>は、さらに多くのパーティクルを対象として、Galaxy エクスプローラーと Fought の3d モデリングチームを管理している最先端のリードと宇宙です。</span><span class="sxs-lookup"><span data-stu-id="16aa7-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="16aa7-206">関連項目</span><span class="sxs-lookup"><span data-stu-id="16aa7-206">See also</span></span>
* [<span data-ttu-id="16aa7-207">GitHub の Galaxy エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="16aa7-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="16aa7-208">YouTube での Galaxy エクスプローラープロジェクトの更新</span><span class="sxs-lookup"><span data-stu-id="16aa7-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
