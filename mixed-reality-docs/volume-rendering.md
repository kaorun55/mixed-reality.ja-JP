---
title: ボリュームの表示
description: 帯域幅消費型のイメージには、不透明度とサーフェスとして簡単に表現できないボリューム全体での色の豊富な情報が含まれます。 Windows Mixed Reality 内での帯域幅消費型のイメージを効率的にレンダリングする方法について説明します。
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: 帯域幅消費型のイメージ、ボリュームの表示、パフォーマンス、複合現実
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604098"
---
# <a name="volume-rendering"></a><span data-ttu-id="0aae6-105">ボリュームの表示</span><span class="sxs-lookup"><span data-stu-id="0aae6-105">Volume rendering</span></span>

<span data-ttu-id="0aae6-106">医療 MRI またはボリュームをエンジニア リングを参照してください。 [Wikipedia でボリュームのレンダリング](https://en.wikipedia.org/wiki/Volume_rendering)します。</span><span class="sxs-lookup"><span data-stu-id="0aae6-106">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="0aae6-107">これらの '帯域幅消費型イメージ' には、不透明度と簡単に表現できないサーフェスとしてなど、ボリューム全体での色の豊富な情報が含まれて[多角形のメッシュ](https://en.wikipedia.org/wiki/Polygon_mesh)します。</span><span class="sxs-lookup"><span data-stu-id="0aae6-107">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="0aae6-108">パフォーマンスを向上させる重要なソリューション</span><span class="sxs-lookup"><span data-stu-id="0aae6-108">Key solutions to improve performance</span></span>
1. <span data-ttu-id="0aae6-109">正しくありません。未熟なアプローチ。ボリューム全体を表示する、通常は遅く実行</span><span class="sxs-lookup"><span data-stu-id="0aae6-109">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="0aae6-110">よし：Cutting 平面。ボリュームの 1 つのスライスのみを表示します。</span><span class="sxs-lookup"><span data-stu-id="0aae6-110">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="0aae6-111">よし：Cutting サブ ボリューム:ボリュームのいくつかのレイヤーのみを表示します。</span><span class="sxs-lookup"><span data-stu-id="0aae6-111">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="0aae6-112">よし：ボリュームのレンダリングの解像度を下げる (' 混合解決シーンのレンダリング ' を参照してください)</span><span class="sxs-lookup"><span data-stu-id="0aae6-112">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="0aae6-113">アプリケーションから、特定のフレームでは、画面に転送できる情報の特定の量だけが、これは、メモリの合計帯域幅。</span><span class="sxs-lookup"><span data-stu-id="0aae6-113">There is only a certain amount of information that can be transferred from the application to the screen in any particular frame, this is the total memory bandwidth.</span></span> <span data-ttu-id="0aae6-114">プレゼンテーションについては、そのデータを変換するために必要なすべての処理 (または '網掛け') も時間も必要です。</span><span class="sxs-lookup"><span data-stu-id="0aae6-114">Also any processing (or 'shading') required to transform that data for presentation also requires time.</span></span> <span data-ttu-id="0aae6-115">ボリュームのレンダリングを実施する際に、主な考慮がそのためには。</span><span class="sxs-lookup"><span data-stu-id="0aae6-115">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="0aae6-116">画面幅 \* 画面の高さ \* 画面数 \* ボリューム レイヤーで-こと-ピクセルの = 合計-ボリュームのサンプル-フレームごと</span><span class="sxs-lookup"><span data-stu-id="0aae6-116">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="0aae6-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%)(完全な res ボリューム: 多くのサンプル)</span><span class="sxs-lookup"><span data-stu-id="0aae6-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="0aae6-118">1028 \* 720 \* 2 \* 1 = 1480320 (完全 0.3%) (薄いスライス。1 ピクセルあたり 1 つのサンプルがスムーズに実行されます)</span><span class="sxs-lookup"><span data-stu-id="0aae6-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="0aae6-119">1028 \* 720 \* 2 \* 10 = 14803200 (完全 3.9%) (サブ ボリューム スライス。1 ピクセルあたり 10 個のサンプルでは、順調に実行、次の 3 d)</span><span class="sxs-lookup"><span data-stu-id="0aae6-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (sub-volume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="0aae6-120">200 \* 200 \* 2 \* 256 = 20480000 (全 5%) (res の音量を下げる: ピクセルの数、フル ボリュームは、次の 3 d が少し blury)</span><span class="sxs-lookup"><span data-stu-id="0aae6-120">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blury)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="0aae6-121">3D テクスチャを表す</span><span class="sxs-lookup"><span data-stu-id="0aae6-121">Representing 3D Textures</span></span>

<span data-ttu-id="0aae6-122">CPU:</span><span class="sxs-lookup"><span data-stu-id="0aae6-122">On the CPU:</span></span>

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

<span data-ttu-id="0aae6-123">GPU:</span><span class="sxs-lookup"><span data-stu-id="0aae6-123">On the GPU:</span></span>

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

## <a name="shading-and-gradients"></a><span data-ttu-id="0aae6-124">網掛けとグラデーション</span><span class="sxs-lookup"><span data-stu-id="0aae6-124">Shading and Gradients</span></span>

<span data-ttu-id="0aae6-125">わかりやすく視覚化の MRI などのボリュームの網掛けを表示する方法。</span><span class="sxs-lookup"><span data-stu-id="0aae6-125">How to shade an volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="0aae6-126">プライマリのメソッドが '強度ウィンドウ' (min と max)、強度を参照してくださいし、黒と白の濃さを表示するには、その領域に単に拡張することです。</span><span class="sxs-lookup"><span data-stu-id="0aae6-126">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="0aae6-127">色パレットをその範囲内の値に適用し、および、テクスチャとして格納されるため、輝度スペクトルのさまざまな部分は網掛けのさまざまな色を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0aae6-127">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="0aae6-128">多くの生の輝度値とセグメント化インデックスの両方に、ボリュームの保存、アプリケーション (など、さまざまな部分を分割するスキンとボーン、これらのセグメント通常によって作成されますの専用ツールの専門家)。</span><span class="sxs-lookup"><span data-stu-id="0aae6-128">In many our applications we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone, these segments are generally created by experts in dedicated tools).</span></span> <span data-ttu-id="0aae6-129">これは、別の色、またはセグメントのインデックスごとに異なる色ごとの傾斜増加を配置する前に示した方法で結合できます。</span><span class="sxs-lookup"><span data-stu-id="0aae6-129">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="0aae6-130">シェーダーでスライス ボリューム</span><span class="sxs-lookup"><span data-stu-id="0aae6-130">Volume Slicing in a Shader</span></span>

<span data-ttu-id="0aae6-131">優れた最初の手順が「スライス プレーン」を作成するには、ボリュームを移動することのできる 'スライス'、および各ポイントで、スキャンの値します。</span><span class="sxs-lookup"><span data-stu-id="0aae6-131">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="0aae6-132">これにより、ボリュームが、ポイントを配置するための参照として使用できる、ワールド空間内にある表す 'VolumeSpace' キューブがあることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="0aae6-132">This assumes that there is a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="0aae6-133">シェーダーでボリュームのトレース</span><span class="sxs-lookup"><span data-stu-id="0aae6-133">Volume Tracing in Shaders</span></span>

<span data-ttu-id="0aae6-134">GPU を使用して、サブのボリュームのトレース (歩くが、いくつか voxels ディープしレイヤー データ バックアップから最前面へ移動) を実行する方法。</span><span class="sxs-lookup"><span data-stu-id="0aae6-134">How to use the GPU to do sub-volume tracing (walks a few voxels deep then layers on the data from back to front):</span></span>

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

## <a name="whole-volume-rendering"></a><span data-ttu-id="0aae6-135">ボリューム全体のレンダリング</span><span class="sxs-lookup"><span data-stu-id="0aae6-135">Whole Volume Rendering</span></span>

<span data-ttu-id="0aae6-136">上記のコードでサブ ボリュームの変更が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0aae6-136">Modifying the sub-volume code above we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="0aae6-137">混合解決シーンのレンダリング</span><span class="sxs-lookup"><span data-stu-id="0aae6-137">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="0aae6-138">低解像度のシーンの一部をレンダリングし、元の場所に配置する方法。</span><span class="sxs-lookup"><span data-stu-id="0aae6-138">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="0aae6-139">次の各フレームを更新する目ごとに 1 つ、2 つのオフスクリーン カメラをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="0aae6-139">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="0aae6-140">2 つの低解像度の設定ではレンダー ターゲット (たとえば 200 x 200 ごと) にカメラをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="0aae6-140">Setup two low-resolution render targets (say 200x200 each), that the cameras render into</span></span>
3. <span data-ttu-id="0aae6-141">ユーザーの前に移動するクアッドをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="0aae6-141">Setup a quad that moves in front of the user</span></span>

<span data-ttu-id="0aae6-142">各フレームには:</span><span class="sxs-lookup"><span data-stu-id="0aae6-142">Each Frame:</span></span>
1. <span data-ttu-id="0aae6-143">低解像度で目ごとにレンダー ターゲットの描画 (データのボリューム、高価なシェーダーなど)</span><span class="sxs-lookup"><span data-stu-id="0aae6-143">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, etc.)</span></span>
2. <span data-ttu-id="0aae6-144">フル解像度として通常シーンを描画 (メッシュ、UI など)。</span><span class="sxs-lookup"><span data-stu-id="0aae6-144">Draw the scene normally as full resolution (meshes, UI, etc.)</span></span>
3. <span data-ttu-id="0aae6-145">シーンの上に、ユーザーの前に、クアッドを描画し、低解像度のレンダリングに投影します。</span><span class="sxs-lookup"><span data-stu-id="0aae6-145">Draw a quad in front of the user, over the scene, and project the low-res renders onto that.</span></span>
4. <span data-ttu-id="0aae6-146">低解像度が高密度のボリューム データを持つフル解像度の要素の結果: ビジュアルの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="0aae6-146">Result: visual combination of full-resolution elements with low-resolution but high-density volume data.</span></span>
