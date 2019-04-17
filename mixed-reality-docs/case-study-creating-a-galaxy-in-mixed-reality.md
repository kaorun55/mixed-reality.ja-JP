---
title: 導入事例 - 複合現実での galaxy の作成
description: Microsoft HoloLens が出荷する前によく寄せられる開発者コミュニティ アプリの種類扱おうとする新しいデバイスのビルド経験の内部チームを参照してください。 5,000 を超えるアイデアが共有され、24 時間 Twitter のポーリング、優勝者が"Galaxy Explorer"と呼ばれる考え方
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy エクスプ ローラー、HoloLens、Windows Mixed Reality、アイデアを共有する、ケース スタディ
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604831"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="bcb37-105">導入事例 - 複合現実での galaxy の作成</span><span class="sxs-lookup"><span data-stu-id="bcb37-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="bcb37-106">Microsoft HoloLens が出荷する前によく寄せられる開発者コミュニティ アプリの種類扱おうとする新しいデバイスのビルド経験の内部チームを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcb37-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="bcb37-107">5,000 を超えるアイディアが共有されていたし、24 時間 Twitter のポーリング、優勝者がというアイデア[Galaxy エクスプ ローラー](galaxy-explorer.md)します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="bcb37-108">Andy Zibits、プロジェクト、アート潜在顧客と Karim Luccin、エンジニア リング チームのグラフィックス、アートと Galaxy エクスプ ローラーでミルキー方法 galaxy の正確な対話型の表現を作成する原因となったエンジニア リングとの間の共同作業の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="bcb37-109">技術者</span><span class="sxs-lookup"><span data-stu-id="bcb37-109">The Tech</span></span>

<span data-ttu-id="bcb37-110">[私たちのチーム](galaxy-explorer.md#meet-the-team)の 2 つのデザイナー、開発者 3 人による、4 つのアーティスト、プロデューサー、および 1 つのテスト担当者を作成する - -6 週間について学び、広大とミルキー方法、Galaxy の美しさの調査に人々 ができるように完全に機能アプリを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcb37-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="bcb37-111">HoloLens、現実的な見栄え galaxy 人が閉じるズームインを個々 の星を参照できるでしょうそれぞれに独自の軌道を作成したいので、生活空間で直接 3D オブジェクトを表示するために機能を最大限に活用します.</span><span class="sxs-lookup"><span data-stu-id="bcb37-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="bcb37-112">開発の第 1 週にそうと、いくつかの目標ミルキー方法 Galaxy の表現の。必要がある深さ、移動、および帯域幅消費型の操作性がある — 星 galaxy の図形を作成できるのです。</span><span class="sxs-lookup"><span data-stu-id="bcb37-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="bcb37-113">星の数十億個含まれていたアニメーションの galaxy の作成に関する問題は、更新の必要な 1 つの要素の膨大な数を過大 HoloLens、CPU を使用してアニメーション化するフレームごとになることでした。</span><span class="sxs-lookup"><span data-stu-id="bcb37-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="bcb37-114">このソリューションには、技術および科学の複雑な組み合わせが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bcb37-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="bcb37-115">しくみ</span><span class="sxs-lookup"><span data-stu-id="bcb37-115">Behind the scenes</span></span>

<span data-ttu-id="bcb37-116">個々 の星を探索できるように、最初は私たちを一度に表示できるパーティクルの数を把握するでした。</span><span class="sxs-lookup"><span data-stu-id="bcb37-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="bcb37-117">パーティクルのレンダリング</span><span class="sxs-lookup"><span data-stu-id="bcb37-117">Rendering particles</span></span>

<span data-ttu-id="bcb37-118">現在の Cpu がシリアル タスクの処理と、いくつか並列タスクを一度に (コア数に応じてに)、最大すばらしいが、Gpu が何千もの操作を並列に処理効率。</span><span class="sxs-lookup"><span data-stu-id="bcb37-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="bcb37-119">ただし、通常、CPU と同じメモリは共有されません、ため、CPU 金曜日 GPU データを交換することができます簡単にボトルネックになります。</span><span class="sxs-lookup"><span data-stu-id="bcb37-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="bcb37-120">ソリューションは、GPU 上で、galaxy することでしたし、GPU 上に存在する完全にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcb37-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="bcb37-121">何千ものさまざまなパターンでポイント パーティクル ストレス テストを始めました。</span><span class="sxs-lookup"><span data-stu-id="bcb37-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="bcb37-122">作業内容と不満を表示する HoloLens で galaxy を取得できました。</span><span class="sxs-lookup"><span data-stu-id="bcb37-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="bcb37-123">星の位置を作成します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-123">Creating the position of the stars</span></span>

<span data-ttu-id="bcb37-124">私たちのチーム メンバーのいずれかが既に書き込まれて、C#その初期位置にある星を生成するコードです。</span><span class="sxs-lookup"><span data-stu-id="bcb37-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="bcb37-125">星が楕円の上にあり、によってそれらの位置を記述できます (**curveOffset**、 **ellipseSize**、**昇格**)、 **curveOffset**に沿って楕円形、星形の角度は、 **ellipseSize** X に沿って楕円のディメンションは、Z、および昇格 galaxy 内で、星の適切な昇格します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="bcb37-126">そのため、バッファーを生み出すことができます ([Unity の ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) 星型の各属性を使用して初期化を残りの環境のどこが GPU に送信します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="bcb37-127">このバッファーを描画するために使用して[Unity の DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html)できるシェーダー (コード、GPU 上で) を実行している任意のポイントのセットで galaxy を表す実際のメッシュはありません。</span><span class="sxs-lookup"><span data-stu-id="bcb37-127">To draw this buffer, we use [Unity’s DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="bcb37-128">**CPU:**</span><span class="sxs-lookup"><span data-stu-id="bcb37-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="bcb37-129">**GPU:**</span><span class="sxs-lookup"><span data-stu-id="bcb37-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="bcb37-130">何千ものパーティクルの生の循環パターンと開始されています。</span><span class="sxs-lookup"><span data-stu-id="bcb37-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="bcb37-131">これにより、実証必要でした。 galaxy の全体的な形に満足が多くのパーティクルの管理や、パフォーマンスの高い速度で実行可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcb37-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="bcb37-132">図形を向上させるのには、さまざまなパターンとパーティクル システムで、回転しようとしました。</span><span class="sxs-lookup"><span data-stu-id="bcb37-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="bcb37-133">これらは、パーティクルとパフォーマンスの数はまだ一貫性のあるが中央近くにある図形が破綻し、表面上はない現実的な星印が生成されたため、最初に有望です。</span><span class="sxs-lookup"><span data-stu-id="bcb37-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="bcb37-134">出力を時間を操作し、現実的には、移動、パーティクルがあるようにするために必要なループ、galaxy の中央に近いこと。</span><span class="sxs-lookup"><span data-stu-id="bcb37-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![ここでは、さまざまなパターンと回転には、上記のようなパーティクル システムしようとしました。](images/galaxy-patterns-500px.png)

<span data-ttu-id="bcb37-136">ここでは、さまざまなパターンと回転には、上記のようなパーティクル システムしようとしました。</span><span class="sxs-lookup"><span data-stu-id="bcb37-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="bcb37-137">私たちのチームが方法銀河系関数の詳細については、いくつか調査を行ったし、パーティクルに基づいて省略記号に移ることができるように、具体的には、galaxy のカスタムのパーティクル システムを行いました"[wave 理論上は密度](https://en.wikipedia.org/wiki/Density_wave_theory)、"この theorizes の腕をgalaxy とは、交通渋滞などの定数 flux でも高密度の領域です。</span><span class="sxs-lookup"><span data-stu-id="bcb37-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="bcb37-138">安定性と、実線が表示されますが、それぞれの省略記号に沿って移動する場合に、腕との間、星が実際に動いています。</span><span class="sxs-lookup"><span data-stu-id="bcb37-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="bcb37-139">システムは、パーティクル決して上に存在、CPU、カードを生成し、向きを設定して、GPU 上ですべてため、システム全体は、単に初期状態 + 時間。</span><span class="sxs-lookup"><span data-stu-id="bcb37-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="bcb37-140">これは、このような進行。</span><span class="sxs-lookup"><span data-stu-id="bcb37-140">It progressed like this:</span></span>

![GPU レンダリングでは、パーティクル システムの進行状況](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="bcb37-142">GPU レンダリングでは、パーティクル システムの進行状況</span><span class="sxs-lookup"><span data-stu-id="bcb37-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="bcb37-143">十分な省略記号が追加され、回転に設定されて、フォームの星の動きが収束させる「腕」に、銀河系が開始されました。</span><span class="sxs-lookup"><span data-stu-id="bcb37-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="bcb37-144">各楕円のモーション パスに沿って星の間隔は、いくつかランダム性が指定されたとそれぞれの星の追加位置指定のランダム ビット。</span><span class="sxs-lookup"><span data-stu-id="bcb37-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="bcb37-145">これにより、移動、および arm の星のはるかに自然な探し求めているディストリビューションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bcb37-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="bcb37-146">最後に、機能は、center からの距離に基づいてドライブの色を追加しました。</span><span class="sxs-lookup"><span data-stu-id="bcb37-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="bcb37-147">星のアニメーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-147">Creating the motion of the stars</span></span>

<span data-ttu-id="bcb37-148">一般的なスター モーションをアニメーション化するには、各フレームの定数の角度を追加して、省略記号定数放射状速度で進める星を取得する必要でした。</span><span class="sxs-lookup"><span data-stu-id="bcb37-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="bcb37-149">これを使用するための主な理由は、 **curveOffset**します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="bcb37-150">これは長、省略記号の横にある星を高速移動されますが、一般的な動きが良いと感じて、厳密には正しくありません。</span><span class="sxs-lookup"><span data-stu-id="bcb37-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![星は、エッジ実行速度が遅く、長い円弧の高速に移動します。](images/ellipse-movement.jpg)

<span data-ttu-id="bcb37-152">星は、エッジ実行速度が遅く、長い円弧の高速に移動します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="bcb37-153">各スターに完全で説明されていることを (**curveOffset**、 **ellipseSize**、**昇格**、**年齢**)、**年齢**は、シーンが読み込まれてから経過した合計時間の累積が発生します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




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

<span data-ttu-id="bcb37-154">アプリケーションの開始時に 1 回の星の数万の生成できましたし、確立された曲線に沿って星の単一のセットをアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="bcb37-155">すべてのものは、GPU であるため、システムは、CPU に並列的にコストなしですべての星をアニメーション化できます。</span><span class="sxs-lookup"><span data-stu-id="bcb37-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![白い四角形を描画時の表示内容を次に示します。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="bcb37-157">白い四角形を描画時の表示内容を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="bcb37-158">クアッドの顔ごとに、カメラをするには、ジオメトリ シェーダーを使用して、星のテクスチャを含む画面で 2D の四角形に各スターの位置を変換します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![四角形ではなくひし形。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="bcb37-160">四角形ではなくひし形。</span><span class="sxs-lookup"><span data-stu-id="bcb37-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="bcb37-161">(1 ピクセルが処理される回数)、アルファブレンディングを限定するため、可能な限り回転、クワッド少ないが重複しているようにします。</span><span class="sxs-lookup"><span data-stu-id="bcb37-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="bcb37-162">クラウドの追加</span><span class="sxs-lookup"><span data-stu-id="bcb37-162">Adding clouds</span></span>

<span data-ttu-id="bcb37-163">帯域幅消費型のパーティクルに気を取得する方法はたくさんあります-クラウドをシミュレートするためにできるだけ多くのパーティクルを描画するボリュームの内部で marching レイから。</span><span class="sxs-lookup"><span data-stu-id="bcb37-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="bcb37-164">Marching リアルタイム光線になっても高価で、作成者にハード メソッドを使用して、ゲーム内のレンダリングのフォレストのなりすましシステム構築を試してみました: 2 D 画像、カメラに接続するツリーの多数の。</span><span class="sxs-lookup"><span data-stu-id="bcb37-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="bcb37-165">ゲームではこの作業を行う、私たちのテクスチャの周り、それらすべてのイメージの場合は、保存、およびビルボード カードごとの実行時に回転するカメラから表示されるツリーのビューの向きに一致するイメージを選択できます。</span><span class="sxs-lookup"><span data-stu-id="bcb37-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="bcb37-166">イメージがホログラムはもこの機能しません。</span><span class="sxs-lookup"><span data-stu-id="bcb37-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="bcb37-167">左目と適切な見た目の違い、そのように見えますフラット、エイリアス、そうしないと、量、高解像度にする必要がありますまたは繰り返し発生します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="bcb37-168">2 つ目の試行では、できるだけ多くのパーティクルを持つしようとしました。</span><span class="sxs-lookup"><span data-stu-id="bcb37-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="bcb37-169">最適なビジュアルは、された炎のパーティクルを描画して、シーンに追加する前にあいまいに達成されました。</span><span class="sxs-lookup"><span data-stu-id="bcb37-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="bcb37-170">その方法に関する一般的な問題が 1 つずつ描きますでした数に関連するパーティクル 60 fps を維持しながら、対象となる領域をどの程度画面とします。</span><span class="sxs-lookup"><span data-stu-id="bcb37-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="bcb37-171">このクラウドの気分を取得する結果のイメージがぼかし効果が非常にコストの高い操作一般的でした。</span><span class="sxs-lookup"><span data-stu-id="bcb37-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![テクスチャ、なし、クラウドがどのような 2% の不透明度になります。](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="bcb37-173">テクスチャ、なし、クラウドがどのような 2% の不透明度になります。</span><span class="sxs-lookup"><span data-stu-id="bcb37-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="bcb37-174">される加法とそれらの多くを持つことになります、互いの上に四角形をいくつかの同一のピクセルを繰り返し網掛けを意味します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="bcb37-175">Galaxy のセンターで同じピクセルが何百もの互いの上に四角形と全画面表示が行われている場合は、膨大なコストがこのありました。</span><span class="sxs-lookup"><span data-stu-id="bcb37-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="bcb37-176">全画面表示のクラウドを行い、ぼかしにしようとしていましたは良いアイデアでそのため、私たちの作業を実行するハードウェアを使用することにしました。</span><span class="sxs-lookup"><span data-stu-id="bcb37-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="bcb37-177">コンテキストのビットが先頭 A</span><span class="sxs-lookup"><span data-stu-id="bcb37-177">A bit of context first</span></span>

<span data-ttu-id="bcb37-178">ゲームでテクスチャを使用する場合、テクスチャのサイズで使用する領域を一致ことはほとんどありませんが、別の種類のテクスチャ、テクスチャのピクセルから色の補間にグラフィック カードを取得するフィルタ リングを使用できます ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx))。</span><span class="sxs-lookup"><span data-stu-id="bcb37-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="bcb37-179">ご興味のあるフィルターは、[双一次フィルター](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx)する最近隣 4 を使用して任意のピクセルの値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="bcb37-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![元のフィルター処理する前に](images/texture-1.png)

![フィルター処理後になります](images/texture-2.png)

<span data-ttu-id="bcb37-182">このプロパティを使用して、表示されて ことビッグ、倍の領域にテクスチャを描画するたびにそれをぼかします結果。</span><span class="sxs-lookup"><span data-stu-id="bcb37-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="bcb37-183">全画面表示の表示と、他のオブジェクトに費やす可能性がありますこれらの貴重なミリ秒を失うこと、代わりには、小さなバージョンの画面にレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="bcb37-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="bcb37-184">その後、このテクスチャをコピーし、何回か 2 の要素によって伸縮が返されますを全画面表示中に、ぼかし、プロセス内のコンテンツ。</span><span class="sxs-lookup"><span data-stu-id="bcb37-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![x3 は、フル解像度に拡大します。](images/galaxy-resolutions-300px.png)

<span data-ttu-id="bcb37-186">x3 は、フル解像度に拡大します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="bcb37-187">元のコストの一部のみをクラウドの部分を取得できました。</span><span class="sxs-lookup"><span data-stu-id="bcb37-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="bcb37-188">完全な解像度に、ここ 1/ピクセルの 64 分とだけで、ペイントは、フル解像度にテクスチャを拡大クラウドを追加する代わりにします。</span><span class="sxs-lookup"><span data-stu-id="bcb37-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![左側の高級 1 に、フル解像度に 8/高級の 3 と 2 の累乗を使用します。](images/stars-upscaled-300px.jpg)

<span data-ttu-id="bcb37-190">左側の高級 1 に、フル解像度に 8/高級の 3 と 2 の累乗を使用します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="bcb37-191">1 から移動しようとしたことに注意してください。 サイズを、完全な 64 分グラフィック カード使用して 4 ピクセルでの設定をさらに大きな領域に影を付けると、アイテムが表示され始めますサイズで 1 つの go にまったく異なるなります。</span><span class="sxs-lookup"><span data-stu-id="bcb37-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="bcb37-192">次に、フル解像度の星を小さいカードを追加した場合、完全な galaxy れます。</span><span class="sxs-lookup"><span data-stu-id="bcb37-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![ほぼの galaxy レンダリングがフル解像度の星を使用して最終的な結果](images/full-galaxy-500px.png)

<span data-ttu-id="bcb37-194">図形を正しく追跡でした後、は、クラウド、スワップ アウト、Photoshop で描画し、いくつか追加の色を追加すると一時的なドットのレイヤーを追加しました。</span><span class="sxs-lookup"><span data-stu-id="bcb37-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="bcb37-195">結果がミルキー方法 Galaxy、アートと良くと感じてエンジニア リング チームが両方と深さ、ボリューム、およびモーションの目標を満たす、CPU をかけずにすべて。</span><span class="sxs-lookup"><span data-stu-id="bcb37-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![この最終的なミルキー方法 Galaxy 3D でします。](images/final-galaxy-500px.jpg)

<span data-ttu-id="bcb37-197">この最終的なミルキー方法 Galaxy 3D でします。</span><span class="sxs-lookup"><span data-stu-id="bcb37-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="bcb37-198">さらなる応用</span><span class="sxs-lookup"><span data-stu-id="bcb37-198">More to explore</span></span>

<span data-ttu-id="bcb37-199">利用できるようにし、Galaxy エクスプ ローラー アプリのコードをオープン ソース化しました[GitHub](https://github.com/Microsoft/GalaxyExplorer)で構築する開発者向け。</span><span class="sxs-lookup"><span data-stu-id="bcb37-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="bcb37-200">Galaxy エクスプ ローラーの開発プロセスの詳細を知ることに関心があるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="bcb37-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="bcb37-201">チェック アウト、過去プロジェクトの更新がすべて、 [Microsoft HoloLens の YouTube チャンネル](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)します。</span><span class="sxs-lookup"><span data-stu-id="bcb37-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="bcb37-202">著者について</span><span class="sxs-lookup"><span data-stu-id="bcb37-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="bcb37-203"><b>Karim Luccin</b>ソフトウェア エンジニア リングと高度なビジュアルの愛好家です。</span><span class="sxs-lookup"><span data-stu-id="bcb37-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="bcb37-204">Galaxy エクスプ ローラーのグラフィックス エンジニアでした。</span><span class="sxs-lookup"><span data-stu-id="bcb37-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="bcb37-205"><b>Andy Zibits</b> Galaxy エクスプ ローラーの 3D モデリング チームを管理し、さらに多くのパーティクルの試合アートの潜在顧客と領域のファンがいます。</span><span class="sxs-lookup"><span data-stu-id="bcb37-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="bcb37-206">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcb37-206">See also</span></span>
* [<span data-ttu-id="bcb37-207">GitHub の Galaxy エクスプ ローラー</span><span class="sxs-lookup"><span data-stu-id="bcb37-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="bcb37-208">YouTube の Galaxy エクスプ ローラーのプロジェクトの更新</span><span class="sxs-lookup"><span data-stu-id="bcb37-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
