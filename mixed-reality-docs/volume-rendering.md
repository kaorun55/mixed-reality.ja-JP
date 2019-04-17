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
# <a name="volume-rendering"></a>ボリュームの表示

医療 MRI またはボリュームをエンジニア リングを参照してください。 [Wikipedia でボリュームのレンダリング](https://en.wikipedia.org/wiki/Volume_rendering)します。 これらの '帯域幅消費型イメージ' には、不透明度と簡単に表現できないサーフェスとしてなど、ボリューム全体での色の豊富な情報が含まれて[多角形のメッシュ](https://en.wikipedia.org/wiki/Polygon_mesh)します。

パフォーマンスを向上させる重要なソリューション
1. 正しくありません。未熟なアプローチ。ボリューム全体を表示する、通常は遅く実行
2. よし：Cutting 平面。ボリュームの 1 つのスライスのみを表示します。
3. よし：Cutting サブ ボリューム:ボリュームのいくつかのレイヤーのみを表示します。
4. よし：ボリュームのレンダリングの解像度を下げる (' 混合解決シーンのレンダリング ' を参照してください)

アプリケーションから、特定のフレームでは、画面に転送できる情報の特定の量だけが、これは、メモリの合計帯域幅。 プレゼンテーションについては、そのデータを変換するために必要なすべての処理 (または '網掛け') も時間も必要です。 ボリュームのレンダリングを実施する際に、主な考慮がそのためには。
* 画面幅 * 画面の高さ * 画面数 * ボリューム レイヤーで-こと-ピクセルの = 合計-ボリュームのサンプル-フレームごと
* 1028 * 720 * 2 * 256 = 378961920 (100%)(完全な res ボリューム: 多くのサンプル)
* 1028 * 720 * 2 * 1 = 1480320 (完全 0.3%) (薄いスライス。1 ピクセルあたり 1 つのサンプルがスムーズに実行されます)
* 1028 * 720 * 2 * 10 = 14803200 (完全 3.9%) (サブ ボリューム スライス。1 ピクセルあたり 10 個のサンプルでは、順調に実行、次の 3 d)
* 200 * 200 * 2 * 256 = 20480000 (全 5%) (res の音量を下げる: ピクセルの数、フル ボリュームは、次の 3 d が少し blury)

## <a name="representing-3d-textures"></a>3D テクスチャを表す

CPU:

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

GPU:

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

## <a name="shading-and-gradients"></a>網掛けとグラデーション

わかりやすく視覚化の MRI などのボリュームの網掛けを表示する方法。 プライマリのメソッドが '強度ウィンドウ' (min と max)、強度を参照してくださいし、黒と白の濃さを表示するには、その領域に単に拡張することです。 色パレットをその範囲内の値に適用し、および、テクスチャとして格納されるため、輝度スペクトルのさまざまな部分は網掛けのさまざまな色を指定できます。

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

多くの生の輝度値とセグメント化インデックスの両方に、ボリュームの保存、アプリケーション (など、さまざまな部分を分割するスキンとボーン、これらのセグメント通常によって作成されますの専用ツールの専門家)。 これは、別の色、またはセグメントのインデックスごとに異なる色ごとの傾斜増加を配置する前に示した方法で結合できます。

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>シェーダーでスライス ボリューム

優れた最初の手順が「スライス プレーン」を作成するには、ボリュームを移動することのできる 'スライス'、および各ポイントで、スキャンの値します。 これにより、ボリュームが、ポイントを配置するための参照として使用できる、ワールド空間内にある表す 'VolumeSpace' キューブがあることを前提としています。

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>シェーダーでボリュームのトレース

GPU を使用して、サブのボリュームのトレース (歩くが、いくつか voxels ディープしレイヤー データ バックアップから最前面へ移動) を実行する方法。

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

## <a name="whole-volume-rendering"></a>ボリューム全体のレンダリング

上記のコードでサブ ボリュームの変更が表示されます。

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>混合解決シーンのレンダリング

低解像度のシーンの一部をレンダリングし、元の場所に配置する方法。
1. 次の各フレームを更新する目ごとに 1 つ、2 つのオフスクリーン カメラをセットアップします。
2. 2 つの低解像度の設定ではレンダー ターゲット (たとえば 200 x 200 ごと) にカメラをレンダリングします。
3. ユーザーの前に移動するクアッドをセットアップします。

各フレームには:
1. 低解像度で目ごとにレンダー ターゲットの描画 (データのボリューム、高価なシェーダーなど)
2. フル解像度として通常シーンを描画 (メッシュ、UI など)。
3. シーンの上に、ユーザーの前に、クアッドを描画し、低解像度のレンダリングに投影します。
4. 低解像度が高密度のボリューム データを持つフル解像度の要素の結果: ビジュアルの組み合わせ。
