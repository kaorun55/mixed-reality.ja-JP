---
title: ボリュームレンダリング
description: 容量イメージには、表面として簡単に表すことができない不透明度と色の豊富な情報が含まれています。 Windows Mixed Reality 内で容量イメージを効率的にレンダリングする方法について説明します。
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: 容量イメージ, ボリュームレンダリング, パフォーマンス, mixed reality
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548630"
---
# <a name="volume-rendering"></a><span data-ttu-id="000b7-105">ボリュームレンダリング</span><span class="sxs-lookup"><span data-stu-id="000b7-105">Volume rendering</span></span>

<span data-ttu-id="000b7-106">医療 MRI またはエンジニアリングボリュームについては、 [Wikipedia のボリュームレンダリング](https://en.wikipedia.org/wiki/Volume_rendering)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="000b7-106">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="000b7-107">これらの ' 容量 images ' には、[多角形メッシュ](https://en.wikipedia.org/wiki/Polygon_mesh)などの表面として簡単には表現できない、ボリューム全体の不透明度と色を含む豊富な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="000b7-107">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="000b7-108">パフォーマンスを向上させるための主要ソリューション</span><span class="sxs-lookup"><span data-stu-id="000b7-108">Key solutions to improve performance</span></span>
1. <span data-ttu-id="000b7-109">不良単純なアプローチ:ボリューム全体を表示します。通常は、実行速度が低下します</span><span class="sxs-lookup"><span data-stu-id="000b7-109">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="000b7-110">よし：カット平面:ボリュームのスライスを1つだけ表示する</span><span class="sxs-lookup"><span data-stu-id="000b7-110">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="000b7-111">よし：サブボリュームの切り取り:ボリュームのいくつかのレイヤーのみを表示する</span><span class="sxs-lookup"><span data-stu-id="000b7-111">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="000b7-112">よし：ボリュームレンダリングの解像度を下げます (「混合解像度シーンレンダリング」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="000b7-112">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="000b7-113">アプリケーションから特定のフレームの画面に転送できる情報は一定量だけです。これは合計メモリ帯域幅です。</span><span class="sxs-lookup"><span data-stu-id="000b7-113">There is only a certain amount of information that can be transferred from the application to the screen in any particular frame, this is the total memory bandwidth.</span></span> <span data-ttu-id="000b7-114">また、プレゼンテーション用にデータを変換するために必要な処理 (または "網掛け") も、時間が必要です。</span><span class="sxs-lookup"><span data-stu-id="000b7-114">Also any processing (or 'shading') required to transform that data for presentation also requires time.</span></span> <span data-ttu-id="000b7-115">ボリュームレンダリングを行う際の主な考慮事項は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="000b7-115">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="000b7-116">画面の幅 \* 画面の高さ \* 画面-カウント \* ボリューム-ピクセルあたりのサイズ = 合計-ボリューム-サンプル-フレームあたり</span><span class="sxs-lookup"><span data-stu-id="000b7-116">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="000b7-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%)(フル res ボリューム: サンプル数が多すぎます)</span><span class="sxs-lookup"><span data-stu-id="000b7-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="000b7-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (シンスライス:1ピクセルあたり1サンプルがスムーズに実行されます)</span><span class="sxs-lookup"><span data-stu-id="000b7-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="000b7-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (サブボリュームスライス:1ピクセルあたり10個のサンプルが非常にスムーズに実行され、3d が見られます。</span><span class="sxs-lookup"><span data-stu-id="000b7-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (sub-volume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="000b7-120">200 \* 200 \* 2 \* 256 = 2048万 (フルの 5%) (小さい res ボリューム: 少ないピクセル、フルボリューム、3d は blury)</span><span class="sxs-lookup"><span data-stu-id="000b7-120">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blury)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="000b7-121">3D テクスチャの表現</span><span class="sxs-lookup"><span data-stu-id="000b7-121">Representing 3D Textures</span></span>

<span data-ttu-id="000b7-122">CPU:</span><span class="sxs-lookup"><span data-stu-id="000b7-122">On the CPU:</span></span>

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

<span data-ttu-id="000b7-123">GPU の場合:</span><span class="sxs-lookup"><span data-stu-id="000b7-123">On the GPU:</span></span>

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a><span data-ttu-id="000b7-124">網掛けとグラデーション</span><span class="sxs-lookup"><span data-stu-id="000b7-124">Shading and Gradients</span></span>

<span data-ttu-id="000b7-125">便利な視覚化のために、MRI などのボリュームを網掛けする方法。</span><span class="sxs-lookup"><span data-stu-id="000b7-125">How to shade an volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="000b7-126">主要な方法としては、輝度を表示する "濃度ウィンドウ" (最小値と最大値) を設定し、その領域を拡大して、黒と白の輝度を表示します。</span><span class="sxs-lookup"><span data-stu-id="000b7-126">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="000b7-127">次に、"カラーランプ" をその範囲内の値に適用し、テクスチャとして保存することで、照度スペクトルのさまざまな部分に影の異なる色を設定できます。</span><span class="sxs-lookup"><span data-stu-id="000b7-127">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="000b7-128">多くのアプリケーションでは、未加工の輝度値と ' セグメンテーションインデックス ' の両方をボリュームに格納しています (スキンやボーンなどのさまざまな部分を分割するために、これらのセグメントは一般に専用ツールの専門家によって作成されています)。</span><span class="sxs-lookup"><span data-stu-id="000b7-128">In many our applications we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone, these segments are generally created by experts in dedicated tools).</span></span> <span data-ttu-id="000b7-129">これを上記の方法と組み合わせて、セグメントインデックスごとに異なる色または異なるカラーランプを作成できます。</span><span class="sxs-lookup"><span data-stu-id="000b7-129">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="000b7-130">シェーダーでのボリュームスライス</span><span class="sxs-lookup"><span data-stu-id="000b7-130">Volume Slicing in a Shader</span></span>

<span data-ttu-id="000b7-131">最初の優れた手順は、"スライス平面" を作成することです。これは、ボリューム間を移動し、"スライスする" と、各ポイントでのスキャン値を指定します。</span><span class="sxs-lookup"><span data-stu-id="000b7-131">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="000b7-132">これは、ワールド空間におけるボリュームの場所を表す "VolumeSpace" キューブがあることを前提としています。これは、ポイントを配置するための参照として使用できます。</span><span class="sxs-lookup"><span data-stu-id="000b7-132">This assumes that there is a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="000b7-133">シェーダーのボリュームトレース</span><span class="sxs-lookup"><span data-stu-id="000b7-133">Volume Tracing in Shaders</span></span>

<span data-ttu-id="000b7-134">GPU を使用してサブボリュームのトレースを実行する方法 (いくつかの操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="000b7-134">How to use the GPU to do sub-volume tracing (walks a few voxels deep then layers on the data from back to front):</span></span>

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a><span data-ttu-id="000b7-135">ボリューム全体のレンダリング</span><span class="sxs-lookup"><span data-stu-id="000b7-135">Whole Volume Rendering</span></span>

<span data-ttu-id="000b7-136">上記のサブボリュームコードを変更すると、次のことが得られます。</span><span class="sxs-lookup"><span data-stu-id="000b7-136">Modifying the sub-volume code above we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="000b7-137">混合解像度シーンのレンダリング</span><span class="sxs-lookup"><span data-stu-id="000b7-137">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="000b7-138">低解像度でシーンの一部をレンダリングして、その場を戻す方法:</span><span class="sxs-lookup"><span data-stu-id="000b7-138">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="000b7-139">2つのスクリーンカメラ (各フレームを更新するために1つずつ) を設定します。</span><span class="sxs-lookup"><span data-stu-id="000b7-139">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="000b7-140">2つの低解像度のレンダーターゲット (それぞれ 200 x 200 など) を設定して、カメラがレンダリングされるようにします。</span><span class="sxs-lookup"><span data-stu-id="000b7-140">Setup two low-resolution render targets (say 200x200 each), that the cameras render into</span></span>
3. <span data-ttu-id="000b7-141">ユーザーの前に移動するクワッドをセットアップする</span><span class="sxs-lookup"><span data-stu-id="000b7-141">Setup a quad that moves in front of the user</span></span>

<span data-ttu-id="000b7-142">各フレーム:</span><span class="sxs-lookup"><span data-stu-id="000b7-142">Each Frame:</span></span>
1. <span data-ttu-id="000b7-143">各視点のレンダーターゲットを低解像度 (ボリュームデータ、負荷の高いシェーダーなど) で描画します。</span><span class="sxs-lookup"><span data-stu-id="000b7-143">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, etc.)</span></span>
2. <span data-ttu-id="000b7-144">シーンを完全な解像度 (メッシュや UI など) として通常どおり描画します。</span><span class="sxs-lookup"><span data-stu-id="000b7-144">Draw the scene normally as full resolution (meshes, UI, etc.)</span></span>
3. <span data-ttu-id="000b7-145">ユーザーの前に四角形を描画し、その上に低 res のレンダリングを投影します。</span><span class="sxs-lookup"><span data-stu-id="000b7-145">Draw a quad in front of the user, over the scene, and project the low-res renders onto that.</span></span>
4. <span data-ttu-id="000b7-146">結果: 低解像度で高密度ボリュームデータを持つ完全解決要素のビジュアルな組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="000b7-146">Result: visual combination of full-resolution elements with low-resolution but high-density volume data.</span></span>
