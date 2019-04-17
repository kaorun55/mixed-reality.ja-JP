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
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>導入事例 - 複合現実での galaxy の作成

Microsoft HoloLens が出荷する前によく寄せられる開発者コミュニティ アプリの種類扱おうとする新しいデバイスのビルド経験の内部チームを参照してください。 5,000 を超えるアイディアが共有されていたし、24 時間 Twitter のポーリング、優勝者がというアイデア[Galaxy エクスプ ローラー](galaxy-explorer.md)します。

Andy Zibits、プロジェクト、アート潜在顧客と Karim Luccin、エンジニア リング チームのグラフィックス、アートと Galaxy エクスプ ローラーでミルキー方法 galaxy の正確な対話型の表現を作成する原因となったエンジニア リングとの間の共同作業の詳細について説明します。

## <a name="the-tech"></a>技術者

[私たちのチーム](galaxy-explorer.md#meet-the-team)の 2 つのデザイナー、開発者 3 人による、4 つのアーティスト、プロデューサー、および 1 つのテスト担当者を作成する - -6 週間について学び、広大とミルキー方法、Galaxy の美しさの調査に人々 ができるように完全に機能アプリを構築する必要があります。

HoloLens、現実的な見栄え galaxy 人が閉じるズームインを個々 の星を参照できるでしょうそれぞれに独自の軌道を作成したいので、生活空間で直接 3D オブジェクトを表示するために機能を最大限に活用します.

開発の第 1 週にそうと、いくつかの目標ミルキー方法 Galaxy の表現の。必要がある深さ、移動、および帯域幅消費型の操作性がある — 星 galaxy の図形を作成できるのです。

星の数十億個含まれていたアニメーションの galaxy の作成に関する問題は、更新の必要な 1 つの要素の膨大な数を過大 HoloLens、CPU を使用してアニメーション化するフレームごとになることでした。 このソリューションには、技術および科学の複雑な組み合わせが含まれています。

## <a name="behind-the-scenes"></a>しくみ

個々 の星を探索できるように、最初は私たちを一度に表示できるパーティクルの数を把握するでした。

### <a name="rendering-particles"></a>パーティクルのレンダリング

現在の Cpu がシリアル タスクの処理と、いくつか並列タスクを一度に (コア数に応じてに)、最大すばらしいが、Gpu が何千もの操作を並列に処理効率。 ただし、通常、CPU と同じメモリは共有されません、ため、CPU 金曜日 GPU データを交換することができます簡単にボトルネックになります。 ソリューションは、GPU 上で、galaxy することでしたし、GPU 上に存在する完全にする必要があります。

何千ものさまざまなパターンでポイント パーティクル ストレス テストを始めました。 作業内容と不満を表示する HoloLens で galaxy を取得できました。

### <a name="creating-the-position-of-the-stars"></a>星の位置を作成します。

私たちのチーム メンバーのいずれかが既に書き込まれて、C#その初期位置にある星を生成するコードです。 星が楕円の上にあり、によってそれらの位置を記述できます (**curveOffset**、 **ellipseSize**、**昇格**)、 **curveOffset**に沿って楕円形、星形の角度は、 **ellipseSize** X に沿って楕円のディメンションは、Z、および昇格 galaxy 内で、星の適切な昇格します。 そのため、バッファーを生み出すことができます ([Unity の ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) 星型の各属性を使用して初期化を残りの環境のどこが GPU に送信します。 このバッファーを描画するために使用して[Unity の DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html)できるシェーダー (コード、GPU 上で) を実行している任意のポイントのセットで galaxy を表す実際のメッシュはありません。

**CPU:**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU:**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

何千ものパーティクルの生の循環パターンと開始されています。 これにより、実証必要でした。 galaxy の全体的な形に満足が多くのパーティクルの管理や、パフォーマンスの高い速度で実行可能性があります。 図形を向上させるのには、さまざまなパターンとパーティクル システムで、回転しようとしました。 これらは、パーティクルとパフォーマンスの数はまだ一貫性のあるが中央近くにある図形が破綻し、表面上はない現実的な星印が生成されたため、最初に有望です。 出力を時間を操作し、現実的には、移動、パーティクルがあるようにするために必要なループ、galaxy の中央に近いこと。

![ここでは、さまざまなパターンと回転には、上記のようなパーティクル システムしようとしました。](images/galaxy-patterns-500px.png)

ここでは、さまざまなパターンと回転には、上記のようなパーティクル システムしようとしました。

私たちのチームが方法銀河系関数の詳細については、いくつか調査を行ったし、パーティクルに基づいて省略記号に移ることができるように、具体的には、galaxy のカスタムのパーティクル システムを行いました"[wave 理論上は密度](https://en.wikipedia.org/wiki/Density_wave_theory)、"この theorizes の腕をgalaxy とは、交通渋滞などの定数 flux でも高密度の領域です。 安定性と、実線が表示されますが、それぞれの省略記号に沿って移動する場合に、腕との間、星が実際に動いています。 システムは、パーティクル決して上に存在、CPU、カードを生成し、向きを設定して、GPU 上ですべてため、システム全体は、単に初期状態 + 時間。 これは、このような進行。

![GPU レンダリングでは、パーティクル システムの進行状況](images/spiral-galaxy-arms-500px.jpg)

GPU レンダリングでは、パーティクル システムの進行状況


十分な省略記号が追加され、回転に設定されて、フォームの星の動きが収束させる「腕」に、銀河系が開始されました。 各楕円のモーション パスに沿って星の間隔は、いくつかランダム性が指定されたとそれぞれの星の追加位置指定のランダム ビット。 これにより、移動、および arm の星のはるかに自然な探し求めているディストリビューションが作成されます。 最後に、機能は、center からの距離に基づいてドライブの色を追加しました。

### <a name="creating-the-motion-of-the-stars"></a>星のアニメーションを作成します。

一般的なスター モーションをアニメーション化するには、各フレームの定数の角度を追加して、省略記号定数放射状速度で進める星を取得する必要でした。 これを使用するための主な理由は、 **curveOffset**します。 これは長、省略記号の横にある星を高速移動されますが、一般的な動きが良いと感じて、厳密には正しくありません。

![星は、エッジ実行速度が遅く、長い円弧の高速に移動します。](images/ellipse-movement.jpg)

星は、エッジ実行速度が遅く、長い円弧の高速に移動します。


各スターに完全で説明されていることを (**curveOffset**、 **ellipseSize**、**昇格**、**年齢**)、**年齢**は、シーンが読み込まれてから経過した合計時間の累積が発生します。




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

アプリケーションの開始時に 1 回の星の数万の生成できましたし、確立された曲線に沿って星の単一のセットをアニメーション化します。 すべてのものは、GPU であるため、システムは、CPU に並列的にコストなしですべての星をアニメーション化できます。

![白い四角形を描画時の表示内容を次に示します。](images/drawing-white-quads-300px.jpg)

白い四角形を描画時の表示内容を次に示します。



クアッドの顔ごとに、カメラをするには、ジオメトリ シェーダーを使用して、星のテクスチャを含む画面で 2D の四角形に各スターの位置を変換します。

![四角形ではなくひし形。](images/drawing-white-quads-300px.jpg)

四角形ではなくひし形。


(1 ピクセルが処理される回数)、アルファブレンディングを限定するため、可能な限り回転、クワッド少ないが重複しているようにします。

### <a name="adding-clouds"></a>クラウドの追加

帯域幅消費型のパーティクルに気を取得する方法はたくさんあります-クラウドをシミュレートするためにできるだけ多くのパーティクルを描画するボリュームの内部で marching レイから。 Marching リアルタイム光線になっても高価で、作成者にハード メソッドを使用して、ゲーム内のレンダリングのフォレストのなりすましシステム構築を試してみました: 2 D 画像、カメラに接続するツリーの多数の。 ゲームではこの作業を行う、私たちのテクスチャの周り、それらすべてのイメージの場合は、保存、およびビルボード カードごとの実行時に回転するカメラから表示されるツリーのビューの向きに一致するイメージを選択できます。 イメージがホログラムはもこの機能しません。 左目と適切な見た目の違い、そのように見えますフラット、エイリアス、そうしないと、量、高解像度にする必要がありますまたは繰り返し発生します。

2 つ目の試行では、できるだけ多くのパーティクルを持つしようとしました。 最適なビジュアルは、された炎のパーティクルを描画して、シーンに追加する前にあいまいに達成されました。 その方法に関する一般的な問題が 1 つずつ描きますでした数に関連するパーティクル 60 fps を維持しながら、対象となる領域をどの程度画面とします。 このクラウドの気分を取得する結果のイメージがぼかし効果が非常にコストの高い操作一般的でした。

![テクスチャ、なし、クラウドがどのような 2% の不透明度になります。](images/clouds-without-texture-300px.jpg)

テクスチャ、なし、クラウドがどのような 2% の不透明度になります。



される加法とそれらの多くを持つことになります、互いの上に四角形をいくつかの同一のピクセルを繰り返し網掛けを意味します。 Galaxy のセンターで同じピクセルが何百もの互いの上に四角形と全画面表示が行われている場合は、膨大なコストがこのありました。

全画面表示のクラウドを行い、ぼかしにしようとしていましたは良いアイデアでそのため、私たちの作業を実行するハードウェアを使用することにしました。

### <a name="a-bit-of-context-first"></a>コンテキストのビットが先頭 A

ゲームでテクスチャを使用する場合、テクスチャのサイズで使用する領域を一致ことはほとんどありませんが、別の種類のテクスチャ、テクスチャのピクセルから色の補間にグラフィック カードを取得するフィルタ リングを使用できます ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx))。 ご興味のあるフィルターは、[双一次フィルター](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx)する最近隣 4 を使用して任意のピクセルの値が計算されます。

![元のフィルター処理する前に](images/texture-1.png)

![フィルター処理後になります](images/texture-2.png)

このプロパティを使用して、表示されて ことビッグ、倍の領域にテクスチャを描画するたびにそれをぼかします結果。

全画面表示の表示と、他のオブジェクトに費やす可能性がありますこれらの貴重なミリ秒を失うこと、代わりには、小さなバージョンの画面にレンダリングします。 その後、このテクスチャをコピーし、何回か 2 の要素によって伸縮が返されますを全画面表示中に、ぼかし、プロセス内のコンテンツ。

![x3 は、フル解像度に拡大します。](images/galaxy-resolutions-300px.png)

x3 は、フル解像度に拡大します。



元のコストの一部のみをクラウドの部分を取得できました。 完全な解像度に、ここ 1/ピクセルの 64 分とだけで、ペイントは、フル解像度にテクスチャを拡大クラウドを追加する代わりにします。

![左側の高級 1 に、フル解像度に 8/高級の 3 と 2 の累乗を使用します。](images/stars-upscaled-300px.jpg)

左側の高級 1 に、フル解像度に 8/高級の 3 と 2 の累乗を使用します。


1 から移動しようとしたことに注意してください。 サイズを、完全な 64 分グラフィック カード使用して 4 ピクセルでの設定をさらに大きな領域に影を付けると、アイテムが表示され始めますサイズで 1 つの go にまったく異なるなります。

次に、フル解像度の星を小さいカードを追加した場合、完全な galaxy れます。

![ほぼの galaxy レンダリングがフル解像度の星を使用して最終的な結果](images/full-galaxy-500px.png)

図形を正しく追跡でした後、は、クラウド、スワップ アウト、Photoshop で描画し、いくつか追加の色を追加すると一時的なドットのレイヤーを追加しました。 結果がミルキー方法 Galaxy、アートと良くと感じてエンジニア リング チームが両方と深さ、ボリューム、およびモーションの目標を満たす、CPU をかけずにすべて。

![この最終的なミルキー方法 Galaxy 3D でします。](images/final-galaxy-500px.jpg)

この最終的なミルキー方法 Galaxy 3D でします。


### <a name="more-to-explore"></a>さらなる応用

利用できるようにし、Galaxy エクスプ ローラー アプリのコードをオープン ソース化しました[GitHub](https://github.com/Microsoft/GalaxyExplorer)で構築する開発者向け。

Galaxy エクスプ ローラーの開発プロセスの詳細を知ることに関心があるでしょうか。 チェック アウト、過去プロジェクトの更新がすべて、 [Microsoft HoloLens の YouTube チャンネル](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)します。

## <a name="about-the-authors"></a>著者について

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b>ソフトウェア エンジニア リングと高度なビジュアルの愛好家です。 Galaxy エクスプ ローラーのグラフィックス エンジニアでした。</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b> Galaxy エクスプ ローラーの 3D モデリング チームを管理し、さらに多くのパーティクルの試合アートの潜在顧客と領域のファンがいます。</td>
</tr>
</table>


## <a name="see-also"></a>関連項目
* [GitHub の Galaxy エクスプ ローラー](https://github.com/Microsoft/GalaxyExplorer)
* [YouTube の Galaxy エクスプ ローラーのプロジェクトの更新](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
