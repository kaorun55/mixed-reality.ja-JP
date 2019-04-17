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
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>ケース スタディの性能の異なるデバイス間でスケーリング Datascape

Datascape は、社内で開発されたマイクロソフトの地形のデータの上に気象データを表示する処理に重点を置いた Windows Mixed Reality アプリケーションです。 アプリケーションは、holographic のデータの視覚化を持つユーザーで囲むと、複合現実でデータを検出からのユーザーが独自の洞察を説明します。

Datascape まで Windows Mixed Reality のイマーシブ ヘッドセットを Microsoft HoloLens とハイエンド GPU を搭載した最新の Pc に低電力の Pc から別のハードウェア機能を備えたさまざまなプラットフォームを対象とする場合。 主な課題は、高のフレーム レートでの実行中に視覚に訴える必要に応じてまったく異なるグラフィックス機能を備えたデバイス上で、シーンを表示でした。

このケース スタディは、プロセスおよびより多くの GPU 集中システムが発生しました。 問題とその克服する方法を説明するを作成するために使用する手法について説明します。

## <a name="transparency-and-overdraw"></a>透明度を描画できますと

透過性は、GPU で高価なできるため、メインのレンダリングの問題は、透明度を処理します。

ソリッド ジオメトリには、そのピクセルは破棄されてからの背後にある将来の (ピクセル) を停止、深度バッファーへの書き込み中にバックアップする前を表示できます。 これは非表示のピクセルがピクセル シェーダーは、プロセスを大幅に高速化を実行することを防ぎます。 Geometry が最適に並べ替えられる場合、画面上の各ピクセルは 1 回だけ描画されます。

並べ替えられるジオメトリの透過的なニーズの前面にバックアップし、描画画面上の現在のピクセルをピクセル シェーダーの出力に依存しています。 これは、結果、描画されているを複数回描画できますと呼ばれる、フレームごとに、画面上の各ピクセル。

HoloLens とメインの Pc では、画面のみ入力できる回数は、いくつか問題のあるレンダリング透過的です。

## <a name="introduction-to-datascape-scene-components"></a>Datascape シーンのコンポーネントの概要

今回のシーンを 3 つの主要なコンポーネントがありました**UI マップ**、および**気象**します。 わかって早い段階で、UI と、アルファブレンディングを削減する方法で地形を意図的に設計するために、天気の効果ができる、すべての GPU 時間に必要なことです。

UI を複数回に手直しを最小限に抑えるの量に描画できますが生成されます。 発光ボタンとマップの概要などのコンポーネントの互いの上にオーバーレイの透明なアートではなくより複雑なジオメトリの横にあるであったします。

マップのカスタムのシェーダーは影や複雑なライティングなどの標準の Unity 機能を削除する単純な単一 sun の照明モデルとカスタム霧計算で置き換えることを使用します。 これは、簡単なピクセル シェーダーを作成し、GPU のサイクルを解放します。

取得する、UI と、マップの表示に予算が不要だった; ハードウェアに応じてそれらへの変更の管理ただし、特にクラウド レンダリング、天気、視覚エフェクトは大きな課題であることが!

## <a name="background-on-cloud-data"></a>クラウドのデータの背景

NOAA サーバーからダウンロードされたクラウド データ (http://nomads.ncep.noaa.gov/) 3 つの独立した 2D 層で、それぞれ、グリッドのセルごとに、クラウドの密度と同様に、クラウドの上端と下端の高さに付属していたとします。 データは、GPU 上で簡単にアクセスのテクスチャの赤、緑、および青のコンポーネントで各コンポーネントが格納されているクラウド情報テクスチャに処理があります。

## <a name="geometry-clouds"></a>ジオメトリのクラウド

低電力コンピューターで開始することにしました、クラウドを表示できるかどうかを確認するには、を最小限に抑えるソリッド ジオメトリを使用するアプローチを描画できます。

クラウド情報テクスチャ頂点ごとの radius を使用して、図形を生成する各レイヤーの solid 高さマップのメッシュを生成することによってクラウドの作成を最初にしようとしました。 ジオメトリ シェーダーは、両方にしっかりとしたクラウドの図形を生成する、クラウドの上下の頂点を生成するために使用しました。 暗い色の詳細の密度の高いクラウドでのクラウドの色、テクスチャから density の値を使用しました。

**頂点を作成するためのシェーダー:**

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

実際のデータの上に詳細情報を表示する小さなノイズ パターンが導入されています。 Round クラウドの端を生成するためにクリップ ピクセル ピクセル シェーダー補間の半径の値をゼロに近い値を破棄のしきい値にヒットしたとき。

![ジオメトリのクラウド](images/datascape-geometry-clouds-700px.jpg)

クラウドは、信頼性の高い geometry であるため、地形のフレーム レートをさらに向上させるために下にある高価なマップ (ピクセル) を非表示にする前に、表示できます。 このソリューションは、ソリッド ジオメトリのレンダリング方法が原因と、HoloLens、ハイエンドなグラフィックス カードに min 仕様からすべてのグラフィックス カードでもを実行します。

## <a name="solid-particle-clouds"></a>Solid パーティクル クラウド

今すぐ、当社のクラウド データの適切な表現を生成し、"wow"要素で少し悩みの種でしたが、ハイエンドのマシンに帯域幅消費型の外観は与えられませんでしたするバックアップ ソリューションがありました。

次の手順をより自然で帯域幅消費型の参照を生成するために約 10万台のパーティクルを表すことによって、クラウドの作成されました。

パーティクルが常に純前から後ろを並べ替える場合引き続き利用できるレンダリングされた以前のパーティクルの背後にあるピクセルの深度バッファー カリング、アルファブレンディングを減らすこと。 また、パーティクル ベースのソリューションでは、別のハードウェアをターゲットに使用されるパーティクルの量を変更しましたできます。 ただし、すべてのピクセルでは、深度テスト、追加のオーバーヘッドで結果にする必要があります。

最初の起動時に、エクスペリエンスの中心点を中心粒子の位置を作成します。 密度を中心パーティクルを配布しましたの距離は小さいためです。 最も近いパーティクルは最初に表示されるように、センターからのすべてのパーティクルを背面へ移動事前並べ替えます。

計算シェーダーに適切な高さと、密度をに基づいて色を各粒子の位置にクラウド情報テクスチャ サンプリングを行います。

使用して*DrawProcedural*パーティクル データの GPU 上で常にすべてのパーティクルごとのクアッドを表示するためにタイムアウトします。

各パーティクルには、半径と高さの両方が含まれています。 高さは、クラウドのデータをクラウド情報テクスチャからサンプリングに基づきますが、半径は、その最も近い隣接ノードを水平方向の距離を格納する計算は最初の配布に基づいていた。 このデータ、四角形は自体とユーザーから見ても水平方向にように高さによって角度の回転を使用して、高さに表示されるとその近隣ノード間の領域を対象には、上から下にあるユーザーを検索する場合。

![パーティクルの図形](images/particle-shape-700px.png)

**シェーダーの分布を示すコード。**

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

背面へ--正面にあるパーティクルを並べ替えて、クリップ (blend ではない) の透明なピクセル solid スタイル シェーダーを引き続き使用しましたので、この手法は驚くほどパーティクル、低電力コンピューター上であってもコストがかかるの過剰な描画を回避するを処理します。

## <a name="transparent-particle-clouds"></a>透過的なパーティクルのクラウド

Solid のパーティクルを適切な動きが、クラウドの図形にはまだクラウドの fluffiness を販売するために必要な。 透明度を導入できるハイエンドなグラフィックス カードのカスタム ソリューションを試すことにしました。

これを行うにパーティクルの初期の並べ替え順序を切り替えるし、テクスチャ アルファを使用するシェーダーを変更します。

![Fluffy クラウド](images/fluffy-clouds-700px.jpg)

発生数百回の画面上の各ピクセルをレンダリングするための最も困難なマシンでもが重すぎるなることが判明しましたすばらしい!

## <a name="render-off-screen-with-lower-resolution"></a>低解像度でオフスクリーン レンダリングします。

四半期の解像度のバッファー (画面と比較して) でのレンダリングを開始した、クラウドでレンダリングされるピクセルの数を減らすためには、し、すべてのパーティクルが描画された後、画面上をバックアップ、最終的な結果を拡大します。 これは、当社が約 4 倍の高速化が、いくつかの注意事項に付属しています。

**オフスクリーン レンダリングするコード:**

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

最初に、オフスクリーン バッファーにデータを表示するとき情報が失われたすべての深さ、メインのシーンから山の背後にあるパーティクル山の上にレンダリングになります。

次に、解像度の変更が顕著なクラウドの端に成果物を導入、バッファーを拡張します。 次の 2 つのセクションでは、これらの問題を解決した方法について説明します。

## <a name="particle-depth-buffer"></a>パーティクル深度バッファー

Mountain またはオブジェクトがその背後にあるパーティクルをカバーでしたをするために、環境内ジオメトリと共存パーティクルをメインのシーンのジオメトリを含む深度バッファーによってオフスクリーン バッファーが設定されます。 このような深度バッファーを作成するを作成し、2 つ目のカメラ、実線のジオメトリとシーンの深さをレンダリングします。

使用して新しいテクスチャで、クラウドのピクセル シェーダーがピクセルです。 同じテクスチャを使用して、クラウドのピクセルの背後にあるジオメトリの距離を計算しました。 その距離を使用して、ピクセルのアルファに適用することで、効果のパーティクルと地形を満たすクラウドと、地形の近くにフェードアウト、任意のハード傷口を削除するようになりましたが。

![クラウドの地形にブレンド](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>エッジがシャープ

伸縮をクラウドでは、パーティクルの中央に通常のサイズのクラウドとほぼ同じ検索またはクラウドの端にある一部のアイテムが示しましたの重なっている場合。 それ以外の場合鋭いエッジがぼやけてし、エイリアス効果は、カメラの移動時に導入されました。

これを解決しました大きな変化 (1) が発生した一方をオフスクリーン バッファーで単純なシェーダーを実行しています。 新しいステンシル バッファー (2) に大きな変更でピクセルを格納します。 使用してマスクにステンシル バッファーこれらハイ コントラストの領域をオフスクリーン バッファーを画面に適用する場合、クラウド (3) の周囲の穴にします。

ここに表示されるすべてのパーティクルもう一度全画面表示モードで、今度は、すべての情報をマスクするステンシル バッファーを使用がピクセルの最小限のセットでその結果、エッジは、(4) をであっても。 コマンド バッファーは、パーティクルを既に作成されてからもう一度新しいカメラにレンダリングすると、単に必要があります。

![クラウドの端のレンダリングの進行状況](images/cloud-steps-1-4-700px.jpg)

最終的な結果は、低コスト センターのセクションでは、クラウドのエッジをシャープでした。

これがレンダリングよりもはるかに高速ですべてのパーティクルが画面を完全なコストが膨大な量の範囲もようにに対して、ステンシル バッファーのピクセルのテストに関連するコストが付属してまだがあります。

## <a name="culling-particles"></a>パーティクルを選別しています

風効果風の多くの wisp を作成する、世界では、計算シェーダーの三角形ストリップ時間の長いを生成しました。 風の効果が生成される幅の狭いストリップのためのフィル レートの負荷は高くでないときに、何百もの何千もの頂点、頂点シェーダーの結果として負荷が生成されます。

紹介を描画する風のストリップのサブセットをフィードする計算シェーダーのバッファーを追加します。 ロジックを含むいくつか単純なビューの視錐台カリング計算シェーダーで、ストリップがカメラ ビュー外かどうかを判断でしたし、プッシュ バッファーに追加されないようにします。 これは、ストリップの量を大幅に削減、GPU 上でいくつか必要なサイクルを解放します。

**コードは、追加のバッファーのデモ:**

*計算シェーダー。*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#コード:*

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

計算シェーダーでそれらの数を減らしますあり、のみ表示される表示のパーティクルをプッシュしましたが、クラウド パーティクルで同じ手法を使用してみました。 この手法実際に保存していない私たち GPU にあまりにおける最大のボトルネックが、画面と頂点の計算コストいないにレンダリングされる量ピクセルであったためです。

この方法では、他の問題は、その性質上に並列化されたコンピューティング rted されていない、ちらつきのクラウドのパーティクルにする並べ替えられたパーティクルの原因、パーティクルのランダムな順序で追加のバッファーが設定されているでした。

プッシュ バッファーを並べ替える方法はありますが、いないこの最適化を追求することにしましたは限られた量のパーティクルをカリングから入手したパフォーマンス向上のための追加の並べ替えをオフセットするは可能性があります。

## <a name="adaptive-rendering"></a>アダプティブ レンダリング

曇り vs などの条件を明確に表示のレンダリングをさまざまなアプリで安定したフレーム レートが確実に、アプリにアダプティブ レンダリングを導入しました。

アダプティブ レンダリングの最初の手順では、GPU を測定します。 先頭と末尾のレンダリングされたフレームの GPU コマンド バッファーにカスタム コードを挿入することで、これを行った、両方をキャプチャ左と右目の画面時間。

測定することによってレンダリングと比較して、必要な更新レートでしたフレームの欠落を閉じる方法を把握できましたにかかった時間。

フレームを削除するには、近い場合は、レンダリング時間を短縮適合させます。 適合させる 1 つの簡単な方法は、描画するには、小さいピクセルを必要とする、画面のビューポートのサイズに変更されます。

使用して*UnityEngine.XR.XRSettings.renderViewportScale*システムは、対象のビューポートの縮小し、サイズに合わせて画面へのバックアップ結果を自動的に拡大します。 スケールをわずかに変更が環境内のジオメトリにかろうじて気付くと 0.7 のスケール ファクターがレンダリングされるピクセルの大きさの半分が必要です。

![70% のスケール、半分のピクセル](images/datascape-scaling-700px.jpg)

固定の数値で小数点以下桁数を削減し、向上させるフレームのドロップしようとしていることを検出したとき、十分な速さをもう一度実行しているときにバックアップします。

時間がないを使用するには、どのようなクラウド手法では、起動時に、ハードウェアの機能をグラフィックスに基づいたしました、システムが時間が長く、低解像度に滞在するを防ぐために、GPU の測定値からデータを基にすることができますが、これは、 Datascape で調査します。

## <a name="final-thoughts"></a>まとめ

さまざまなハードウェアを対象とするが困難にし、計画を立てる必要があります。

問題の領域に慣れるし、すべてのマシンで実行されるバックアップ ソリューションを開発する低電力コンピューターを対象とする機能を開始することをお勧めします。 ピクセルは、最も貴重なリソースになるために念頭に置いてのフィル レートでソリューションを設計します。 透過性経由でターゲット ソリッド ジオメトリ。

バックアップ ソリューションでは、ハイ エンド マシン複雑で階層化を開始したり、おそらくだけバックアップ ソリューションの解像度を向上できます。

、最悪のシナリオを設計し、おそらくアダプティブ レンダリングを使用して、負荷の高い状況を検討します。

## <a name="about-the-authors"></a>著者について

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Ferrese</b><br>ソフトウェア エンジニア @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>ソフトウェア エンジニア @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>関連項目
* [複合現実のパフォーマンスを理解](understanding-performance-for-mixed-reality.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)

 
