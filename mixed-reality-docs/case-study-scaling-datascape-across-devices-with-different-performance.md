---
title: ケース スタディの性能の異なるデバイス間でスケーリング Datascape
description: このケース スタディは、マイクロソフトの開発者がさまざまなパフォーマンスの機能を持つデバイスで魅力的なエクスペリエンスを実現する Datascape アプリを最適化する方法に関する洞察を提供します。
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: イマーシブ ヘッドセット、パフォーマンスの最適化、VR、ケース スタディ
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604871"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="f35d9-104">ケース スタディの性能の異なるデバイス間でスケーリング Datascape</span><span class="sxs-lookup"><span data-stu-id="f35d9-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="f35d9-105">Datascape は、社内で開発されたマイクロソフトの地形のデータの上に気象データを表示する処理に重点を置いた Windows Mixed Reality アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="f35d9-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="f35d9-106">アプリケーションは、holographic のデータの視覚化を持つユーザーで囲むと、複合現実でデータを検出からのユーザーが独自の洞察を説明します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="f35d9-107">Datascape まで Windows Mixed Reality のイマーシブ ヘッドセットを Microsoft HoloLens とハイエンド GPU を搭載した最新の Pc に低電力の Pc から別のハードウェア機能を備えたさまざまなプラットフォームを対象とする場合。</span><span class="sxs-lookup"><span data-stu-id="f35d9-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="f35d9-108">主な課題は、高のフレーム レートでの実行中に視覚に訴える必要に応じてまったく異なるグラフィックス機能を備えたデバイス上で、シーンを表示でした。</span><span class="sxs-lookup"><span data-stu-id="f35d9-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="f35d9-109">このケース スタディは、プロセスおよびより多くの GPU 集中システムが発生しました。 問題とその克服する方法を説明するを作成するために使用する手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="f35d9-110">透明度を描画できますと</span><span class="sxs-lookup"><span data-stu-id="f35d9-110">Transparency and overdraw</span></span>

<span data-ttu-id="f35d9-111">透過性は、GPU で高価なできるため、メインのレンダリングの問題は、透明度を処理します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="f35d9-112">ソリッド ジオメトリには、そのピクセルは破棄されてからの背後にある将来の (ピクセル) を停止、深度バッファーへの書き込み中にバックアップする前を表示できます。</span><span class="sxs-lookup"><span data-stu-id="f35d9-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="f35d9-113">これは非表示のピクセルがピクセル シェーダーは、プロセスを大幅に高速化を実行することを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="f35d9-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="f35d9-114">Geometry が最適に並べ替えられる場合、画面上の各ピクセルは 1 回だけ描画されます。</span><span class="sxs-lookup"><span data-stu-id="f35d9-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="f35d9-115">並べ替えられるジオメトリの透過的なニーズの前面にバックアップし、描画画面上の現在のピクセルをピクセル シェーダーの出力に依存しています。</span><span class="sxs-lookup"><span data-stu-id="f35d9-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="f35d9-116">これは、結果、描画されているを複数回描画できますと呼ばれる、フレームごとに、画面上の各ピクセル。</span><span class="sxs-lookup"><span data-stu-id="f35d9-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="f35d9-117">HoloLens とメインの Pc では、画面のみ入力できる回数は、いくつか問題のあるレンダリング透過的です。</span><span class="sxs-lookup"><span data-stu-id="f35d9-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="f35d9-118">Datascape シーンのコンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="f35d9-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="f35d9-119">今回のシーンを 3 つの主要なコンポーネントがありました**UI マップ**、および**気象**します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="f35d9-120">わかって早い段階で、UI と、アルファブレンディングを削減する方法で地形を意図的に設計するために、天気の効果ができる、すべての GPU 時間に必要なことです。</span><span class="sxs-lookup"><span data-stu-id="f35d9-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="f35d9-121">UI を複数回に手直しを最小限に抑えるの量に描画できますが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f35d9-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="f35d9-122">発光ボタンとマップの概要などのコンポーネントの互いの上にオーバーレイの透明なアートではなくより複雑なジオメトリの横にあるであったします。</span><span class="sxs-lookup"><span data-stu-id="f35d9-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="f35d9-123">マップのカスタムのシェーダーは影や複雑なライティングなどの標準の Unity 機能を削除する単純な単一 sun の照明モデルとカスタム霧計算で置き換えることを使用します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="f35d9-124">これは、簡単なピクセル シェーダーを作成し、GPU のサイクルを解放します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="f35d9-125">取得する、UI と、マップの表示に予算が不要だった; ハードウェアに応じてそれらへの変更の管理ただし、特にクラウド レンダリング、天気、視覚エフェクトは大きな課題であることが!</span><span class="sxs-lookup"><span data-stu-id="f35d9-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="f35d9-126">クラウドのデータの背景</span><span class="sxs-lookup"><span data-stu-id="f35d9-126">Background on cloud data</span></span>

<span data-ttu-id="f35d9-127">NOAA サーバーからダウンロードされたクラウド データ (http://nomads.ncep.noaa.gov/) 3 つの独立した 2D 層で、それぞれ、グリッドのセルごとに、クラウドの密度と同様に、クラウドの上端と下端の高さに付属していたとします。</span><span class="sxs-lookup"><span data-stu-id="f35d9-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="f35d9-128">データは、GPU 上で簡単にアクセスのテクスチャの赤、緑、および青のコンポーネントで各コンポーネントが格納されているクラウド情報テクスチャに処理があります。</span><span class="sxs-lookup"><span data-stu-id="f35d9-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="f35d9-129">ジオメトリのクラウド</span><span class="sxs-lookup"><span data-stu-id="f35d9-129">Geometry clouds</span></span>

<span data-ttu-id="f35d9-130">低電力コンピューターで開始することにしました、クラウドを表示できるかどうかを確認するには、を最小限に抑えるソリッド ジオメトリを使用するアプローチを描画できます。</span><span class="sxs-lookup"><span data-stu-id="f35d9-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="f35d9-131">クラウド情報テクスチャ頂点ごとの radius を使用して、図形を生成する各レイヤーの solid 高さマップのメッシュを生成することによってクラウドの作成を最初にしようとしました。</span><span class="sxs-lookup"><span data-stu-id="f35d9-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="f35d9-132">ジオメトリ シェーダーは、両方にしっかりとしたクラウドの図形を生成する、クラウドの上下の頂点を生成するために使用しました。</span><span class="sxs-lookup"><span data-stu-id="f35d9-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="f35d9-133">暗い色の詳細の密度の高いクラウドでのクラウドの色、テクスチャから density の値を使用しました。</span><span class="sxs-lookup"><span data-stu-id="f35d9-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="f35d9-134">**頂点を作成するためのシェーダー:**</span><span class="sxs-lookup"><span data-stu-id="f35d9-134">**Shader for creating the vertices:**</span></span>

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

<span data-ttu-id="f35d9-135">実際のデータの上に詳細情報を表示する小さなノイズ パターンが導入されています。</span><span class="sxs-lookup"><span data-stu-id="f35d9-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="f35d9-136">Round クラウドの端を生成するためにクリップ ピクセル ピクセル シェーダー補間の半径の値をゼロに近い値を破棄のしきい値にヒットしたとき。</span><span class="sxs-lookup"><span data-stu-id="f35d9-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![ジオメトリのクラウド](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="f35d9-138">クラウドは、信頼性の高い geometry であるため、地形のフレーム レートをさらに向上させるために下にある高価なマップ (ピクセル) を非表示にする前に、表示できます。</span><span class="sxs-lookup"><span data-stu-id="f35d9-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="f35d9-139">このソリューションは、ソリッド ジオメトリのレンダリング方法が原因と、HoloLens、ハイエンドなグラフィックス カードに min 仕様からすべてのグラフィックス カードでもを実行します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="f35d9-140">Solid パーティクル クラウド</span><span class="sxs-lookup"><span data-stu-id="f35d9-140">Solid particle clouds</span></span>

<span data-ttu-id="f35d9-141">今すぐ、当社のクラウド データの適切な表現を生成し、"wow"要素で少し悩みの種でしたが、ハイエンドのマシンに帯域幅消費型の外観は与えられませんでしたするバックアップ ソリューションがありました。</span><span class="sxs-lookup"><span data-stu-id="f35d9-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="f35d9-142">次の手順をより自然で帯域幅消費型の参照を生成するために約 10万台のパーティクルを表すことによって、クラウドの作成されました。</span><span class="sxs-lookup"><span data-stu-id="f35d9-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="f35d9-143">パーティクルが常に純前から後ろを並べ替える場合引き続き利用できるレンダリングされた以前のパーティクルの背後にあるピクセルの深度バッファー カリング、アルファブレンディングを減らすこと。</span><span class="sxs-lookup"><span data-stu-id="f35d9-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="f35d9-144">また、パーティクル ベースのソリューションでは、別のハードウェアをターゲットに使用されるパーティクルの量を変更しましたできます。</span><span class="sxs-lookup"><span data-stu-id="f35d9-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="f35d9-145">ただし、すべてのピクセルでは、深度テスト、追加のオーバーヘッドで結果にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f35d9-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="f35d9-146">最初の起動時に、エクスペリエンスの中心点を中心粒子の位置を作成します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="f35d9-147">密度を中心パーティクルを配布しましたの距離は小さいためです。</span><span class="sxs-lookup"><span data-stu-id="f35d9-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="f35d9-148">最も近いパーティクルは最初に表示されるように、センターからのすべてのパーティクルを背面へ移動事前並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="f35d9-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="f35d9-149">計算シェーダーに適切な高さと、密度をに基づいて色を各粒子の位置にクラウド情報テクスチャ サンプリングを行います。</span><span class="sxs-lookup"><span data-stu-id="f35d9-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="f35d9-150">使用して*DrawProcedural*パーティクル データの GPU 上で常にすべてのパーティクルごとのクアッドを表示するためにタイムアウトします。</span><span class="sxs-lookup"><span data-stu-id="f35d9-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="f35d9-151">各パーティクルには、半径と高さの両方が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f35d9-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="f35d9-152">高さは、クラウドのデータをクラウド情報テクスチャからサンプリングに基づきますが、半径は、その最も近い隣接ノードを水平方向の距離を格納する計算は最初の配布に基づいていた。</span><span class="sxs-lookup"><span data-stu-id="f35d9-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="f35d9-153">このデータ、四角形は自体とユーザーから見ても水平方向にように高さによって角度の回転を使用して、高さに表示されるとその近隣ノード間の領域を対象には、上から下にあるユーザーを検索する場合。</span><span class="sxs-lookup"><span data-stu-id="f35d9-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![パーティクルの図形](images/particle-shape-700px.png)

<span data-ttu-id="f35d9-155">**シェーダーの分布を示すコード。**</span><span class="sxs-lookup"><span data-stu-id="f35d9-155">**Shader code showing the distribution:**</span></span>

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

<span data-ttu-id="f35d9-156">背面へ--正面にあるパーティクルを並べ替えて、クリップ (blend ではない) の透明なピクセル solid スタイル シェーダーを引き続き使用しましたので、この手法は驚くほどパーティクル、低電力コンピューター上であってもコストがかかるの過剰な描画を回避するを処理します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="f35d9-157">透過的なパーティクルのクラウド</span><span class="sxs-lookup"><span data-stu-id="f35d9-157">Transparent particle clouds</span></span>

<span data-ttu-id="f35d9-158">Solid のパーティクルを適切な動きが、クラウドの図形にはまだクラウドの fluffiness を販売するために必要な。</span><span class="sxs-lookup"><span data-stu-id="f35d9-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="f35d9-159">透明度を導入できるハイエンドなグラフィックス カードのカスタム ソリューションを試すことにしました。</span><span class="sxs-lookup"><span data-stu-id="f35d9-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="f35d9-160">これを行うにパーティクルの初期の並べ替え順序を切り替えるし、テクスチャ アルファを使用するシェーダーを変更します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Fluffy クラウド](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="f35d9-162">発生数百回の画面上の各ピクセルをレンダリングするための最も困難なマシンでもが重すぎるなることが判明しましたすばらしい!</span><span class="sxs-lookup"><span data-stu-id="f35d9-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="f35d9-163">低解像度でオフスクリーン レンダリングします。</span><span class="sxs-lookup"><span data-stu-id="f35d9-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="f35d9-164">四半期の解像度のバッファー (画面と比較して) でのレンダリングを開始した、クラウドでレンダリングされるピクセルの数を減らすためには、し、すべてのパーティクルが描画された後、画面上をバックアップ、最終的な結果を拡大します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="f35d9-165">これは、当社が約 4 倍の高速化が、いくつかの注意事項に付属しています。</span><span class="sxs-lookup"><span data-stu-id="f35d9-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="f35d9-166">**オフスクリーン レンダリングするコード:**</span><span class="sxs-lookup"><span data-stu-id="f35d9-166">**Code for rendering off-screen:**</span></span>

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

<span data-ttu-id="f35d9-167">最初に、オフスクリーン バッファーにデータを表示するとき情報が失われたすべての深さ、メインのシーンから山の背後にあるパーティクル山の上にレンダリングになります。</span><span class="sxs-lookup"><span data-stu-id="f35d9-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="f35d9-168">次に、解像度の変更が顕著なクラウドの端に成果物を導入、バッファーを拡張します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="f35d9-169">次の 2 つのセクションでは、これらの問題を解決した方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="f35d9-170">パーティクル深度バッファー</span><span class="sxs-lookup"><span data-stu-id="f35d9-170">Particle depth buffer</span></span>

<span data-ttu-id="f35d9-171">Mountain またはオブジェクトがその背後にあるパーティクルをカバーでしたをするために、環境内ジオメトリと共存パーティクルをメインのシーンのジオメトリを含む深度バッファーによってオフスクリーン バッファーが設定されます。</span><span class="sxs-lookup"><span data-stu-id="f35d9-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="f35d9-172">このような深度バッファーを作成するを作成し、2 つ目のカメラ、実線のジオメトリとシーンの深さをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="f35d9-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="f35d9-173">使用して新しいテクスチャで、クラウドのピクセル シェーダーがピクセルです。</span><span class="sxs-lookup"><span data-stu-id="f35d9-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="f35d9-174">同じテクスチャを使用して、クラウドのピクセルの背後にあるジオメトリの距離を計算しました。</span><span class="sxs-lookup"><span data-stu-id="f35d9-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="f35d9-175">その距離を使用して、ピクセルのアルファに適用することで、効果のパーティクルと地形を満たすクラウドと、地形の近くにフェードアウト、任意のハード傷口を削除するようになりましたが。</span><span class="sxs-lookup"><span data-stu-id="f35d9-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![クラウドの地形にブレンド](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="f35d9-177">エッジがシャープ</span><span class="sxs-lookup"><span data-stu-id="f35d9-177">Sharpening the edges</span></span>

<span data-ttu-id="f35d9-178">伸縮をクラウドでは、パーティクルの中央に通常のサイズのクラウドとほぼ同じ検索またはクラウドの端にある一部のアイテムが示しましたの重なっている場合。</span><span class="sxs-lookup"><span data-stu-id="f35d9-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="f35d9-179">それ以外の場合鋭いエッジがぼやけてし、エイリアス効果は、カメラの移動時に導入されました。</span><span class="sxs-lookup"><span data-stu-id="f35d9-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="f35d9-180">これを解決しました大きな変化 (1) が発生した一方をオフスクリーン バッファーで単純なシェーダーを実行しています。</span><span class="sxs-lookup"><span data-stu-id="f35d9-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="f35d9-181">新しいステンシル バッファー (2) に大きな変更でピクセルを格納します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="f35d9-182">使用してマスクにステンシル バッファーこれらハイ コントラストの領域をオフスクリーン バッファーを画面に適用する場合、クラウド (3) の周囲の穴にします。</span><span class="sxs-lookup"><span data-stu-id="f35d9-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="f35d9-183">ここに表示されるすべてのパーティクルもう一度全画面表示モードで、今度は、すべての情報をマスクするステンシル バッファーを使用がピクセルの最小限のセットでその結果、エッジは、(4) をであっても。</span><span class="sxs-lookup"><span data-stu-id="f35d9-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="f35d9-184">コマンド バッファーは、パーティクルを既に作成されてからもう一度新しいカメラにレンダリングすると、単に必要があります。</span><span class="sxs-lookup"><span data-stu-id="f35d9-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![クラウドの端のレンダリングの進行状況](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="f35d9-186">最終的な結果は、低コスト センターのセクションでは、クラウドのエッジをシャープでした。</span><span class="sxs-lookup"><span data-stu-id="f35d9-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="f35d9-187">これがレンダリングよりもはるかに高速ですべてのパーティクルが画面を完全なコストが膨大な量の範囲もようにに対して、ステンシル バッファーのピクセルのテストに関連するコストが付属してまだがあります。</span><span class="sxs-lookup"><span data-stu-id="f35d9-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="f35d9-188">パーティクルを選別しています</span><span class="sxs-lookup"><span data-stu-id="f35d9-188">Culling particles</span></span>

<span data-ttu-id="f35d9-189">風効果風の多くの wisp を作成する、世界では、計算シェーダーの三角形ストリップ時間の長いを生成しました。</span><span class="sxs-lookup"><span data-stu-id="f35d9-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="f35d9-190">風の効果が生成される幅の狭いストリップのためのフィル レートの負荷は高くでないときに、何百もの何千もの頂点、頂点シェーダーの結果として負荷が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f35d9-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="f35d9-191">紹介を描画する風のストリップのサブセットをフィードする計算シェーダーのバッファーを追加します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="f35d9-192">ロジックを含むいくつか単純なビューの視錐台カリング計算シェーダーで、ストリップがカメラ ビュー外かどうかを判断でしたし、プッシュ バッファーに追加されないようにします。</span><span class="sxs-lookup"><span data-stu-id="f35d9-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="f35d9-193">これは、ストリップの量を大幅に削減、GPU 上でいくつか必要なサイクルを解放します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="f35d9-194">**コードは、追加のバッファーのデモ:**</span><span class="sxs-lookup"><span data-stu-id="f35d9-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="f35d9-195">*計算シェーダー。*</span><span class="sxs-lookup"><span data-stu-id="f35d9-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="f35d9-196">*C#コード:*</span><span class="sxs-lookup"><span data-stu-id="f35d9-196">*C# code:*</span></span>

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

<span data-ttu-id="f35d9-197">計算シェーダーでそれらの数を減らしますあり、のみ表示される表示のパーティクルをプッシュしましたが、クラウド パーティクルで同じ手法を使用してみました。</span><span class="sxs-lookup"><span data-stu-id="f35d9-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="f35d9-198">この手法実際に保存していない私たち GPU にあまりにおける最大のボトルネックが、画面と頂点の計算コストいないにレンダリングされる量ピクセルであったためです。</span><span class="sxs-lookup"><span data-stu-id="f35d9-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="f35d9-199">この方法では、他の問題は、その性質上に並列化されたコンピューティング rted されていない、ちらつきのクラウドのパーティクルにする並べ替えられたパーティクルの原因、パーティクルのランダムな順序で追加のバッファーが設定されているでした。</span><span class="sxs-lookup"><span data-stu-id="f35d9-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="f35d9-200">プッシュ バッファーを並べ替える方法はありますが、いないこの最適化を追求することにしましたは限られた量のパーティクルをカリングから入手したパフォーマンス向上のための追加の並べ替えをオフセットするは可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f35d9-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="f35d9-201">アダプティブ レンダリング</span><span class="sxs-lookup"><span data-stu-id="f35d9-201">Adaptive rendering</span></span>

<span data-ttu-id="f35d9-202">曇り vs などの条件を明確に表示のレンダリングをさまざまなアプリで安定したフレーム レートが確実に、アプリにアダプティブ レンダリングを導入しました。</span><span class="sxs-lookup"><span data-stu-id="f35d9-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="f35d9-203">アダプティブ レンダリングの最初の手順では、GPU を測定します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="f35d9-204">先頭と末尾のレンダリングされたフレームの GPU コマンド バッファーにカスタム コードを挿入することで、これを行った、両方をキャプチャ左と右目の画面時間。</span><span class="sxs-lookup"><span data-stu-id="f35d9-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="f35d9-205">測定することによってレンダリングと比較して、必要な更新レートでしたフレームの欠落を閉じる方法を把握できましたにかかった時間。</span><span class="sxs-lookup"><span data-stu-id="f35d9-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="f35d9-206">フレームを削除するには、近い場合は、レンダリング時間を短縮適合させます。</span><span class="sxs-lookup"><span data-stu-id="f35d9-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="f35d9-207">適合させる 1 つの簡単な方法は、描画するには、小さいピクセルを必要とする、画面のビューポートのサイズに変更されます。</span><span class="sxs-lookup"><span data-stu-id="f35d9-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="f35d9-208">使用して*UnityEngine.XR.XRSettings.renderViewportScale*システムは、対象のビューポートの縮小し、サイズに合わせて画面へのバックアップ結果を自動的に拡大します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="f35d9-209">スケールをわずかに変更が環境内のジオメトリにかろうじて気付くと 0.7 のスケール ファクターがレンダリングされるピクセルの大きさの半分が必要です。</span><span class="sxs-lookup"><span data-stu-id="f35d9-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70% のスケール、半分のピクセル](images/datascape-scaling-700px.jpg)

<span data-ttu-id="f35d9-211">固定の数値で小数点以下桁数を削減し、向上させるフレームのドロップしようとしていることを検出したとき、十分な速さをもう一度実行しているときにバックアップします。</span><span class="sxs-lookup"><span data-stu-id="f35d9-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="f35d9-212">時間がないを使用するには、どのようなクラウド手法では、起動時に、ハードウェアの機能をグラフィックスに基づいたしました、システムが時間が長く、低解像度に滞在するを防ぐために、GPU の測定値からデータを基にすることができますが、これは、 Datascape で調査します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="f35d9-213">まとめ</span><span class="sxs-lookup"><span data-stu-id="f35d9-213">Final thoughts</span></span>

<span data-ttu-id="f35d9-214">さまざまなハードウェアを対象とするが困難にし、計画を立てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f35d9-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="f35d9-215">問題の領域に慣れるし、すべてのマシンで実行されるバックアップ ソリューションを開発する低電力コンピューターを対象とする機能を開始することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f35d9-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="f35d9-216">ピクセルは、最も貴重なリソースになるために念頭に置いてのフィル レートでソリューションを設計します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="f35d9-217">透過性経由でターゲット ソリッド ジオメトリ。</span><span class="sxs-lookup"><span data-stu-id="f35d9-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="f35d9-218">バックアップ ソリューションでは、ハイ エンド マシン複雑で階層化を開始したり、おそらくだけバックアップ ソリューションの解像度を向上できます。</span><span class="sxs-lookup"><span data-stu-id="f35d9-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="f35d9-219">、最悪のシナリオを設計し、おそらくアダプティブ レンダリングを使用して、負荷の高い状況を検討します。</span><span class="sxs-lookup"><span data-stu-id="f35d9-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="f35d9-220">著者について</span><span class="sxs-lookup"><span data-stu-id="f35d9-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="f35d9-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="f35d9-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="f35d9-222">ソフトウェア エンジニア @Microsoft</span><span class="sxs-lookup"><span data-stu-id="f35d9-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="f35d9-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="f35d9-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="f35d9-224">ソフトウェア エンジニア @Microsoft</span><span class="sxs-lookup"><span data-stu-id="f35d9-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="f35d9-225">関連項目</span><span class="sxs-lookup"><span data-stu-id="f35d9-225">See also</span></span>
* [<span data-ttu-id="f35d9-226">複合現実のパフォーマンスを理解</span><span class="sxs-lookup"><span data-stu-id="f35d9-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="f35d9-227">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="f35d9-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 
