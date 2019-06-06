---
title: 自宅で使用するための 3D モデルを作成します。
description: 資産の要件と 3D モデルで Windows Mixed Reality ホーム HoloLens と没入型の (VR) ヘッドセットの両方で使用するためのガイダンスを作成します。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: モデリングのガイダンスについては、資産の要件、ガイドライン、ランチャー、3 D ランチャー、テクスチャ、資料、複雑さ、三角形、メッシュ、多角形、polycount、オーサリング、3 D、モデリングの制限します。
ms.openlocfilehash: 73af40cf2915742cab612625c8243a36ee74d748
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692289"
---
# <a name="create-3d-models-for-use-in-the-home"></a>自宅で使用するための 3D モデルを作成します。

[Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)始めるユーザーがアプリケーションを起動する前に配置する場所です。 Windows Mixed Reality ヘッドセットを活用するためにアプリケーションを設計することができます、 [3D モデル、アプリ起動ツールとして](implementing-3d-app-launchers.md)できるようになり[Windows Mixed Reality ホームに配置するディープ リンクを 3D](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles)から、アプリ内で。 この記事では、Windows Mixed Reality ホームと互換性のある 3D モデルを作成するためのガイドラインについて説明します。

## <a name="asset-requirements-overview"></a>資産の必要条件の概要
Windows Mixed Reality を 3D モデルを作成する場合は、すべての資産が満たす必要のあるいくつかの要件があります。 
1. [エクスポート](#exporting-models)-.glb ファイル形式 (バイナリ glTF) で資産を配信する必要があります
2. [モデリング](#modeling-guidelines)-アセットが k 三角形が 10 未満にする必要があります、64 個のノードと LOD あたり 32 submeshes があります。
3. [素材](#material-guidelines)- テクスチャは 4096 x 4096 より大きくすることはできませんし、最小の mip マップをいずれかのディメンション上の 4 未満にする必要があります
4. [アニメーション](#animation-guidelines)のアニメーションは、30 FPS で 20 分より長くすることはできません (36,000 キーフレーム) 含める必要があります < = 8192 morph ターゲット頂点
5. [最適化](#optimizations)-を使用して資産を最適化する必要があります、 [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)します。 これは**の Windows OS バージョンに必要な < = 1709** Windows OS バージョンに推奨 > 1803 を =

この記事の残りの部分には、これらの要件だけでなく追加のガイドラインは、モデルは、home、Windows Mixed Reality でうまく動作させるの詳細な概要が含まれています。 

## <a name="detailed-guidance"></a>詳細なガイダンス

### <a name="exporting-models"></a>モデルのエクスポート

Windows Mixed Reality ホーム .glb ファイル形式を使用して、埋め込み画像やバイナリ データを送信する 3D アセットを期待します。 Glb ロイヤリティをある glTF 形式のバイナリ バージョンは、無料のオープン標準の 3D アセットの配信 Khronos グループによって管理されます。 Windows アプリおよびエクスペリエンスの間でマイクロソフトの形式のサポートする際の 3D コンテンツの相互運用可能な業界標準として glTF の進化に伴ってします。 検索するには、glTF 資産を作成していないかどうか、[サポートされているエクスポーターとコンバーターの一覧](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)glTF ワーキング グループの github ページ。  

### <a name="modeling-guidelines"></a>モデリングのガイドライン

Windows Mixed Reality ホーム環境との互換性を確保する、次のモデリングのガイドラインを使用して生成される資産が必要です。 任意のプログラムでモデリングの際に、次の推奨事項と制限事項に注意してください。
1. アップ軸は、"Y"に設定する必要があります。
2. 資産は、正の Z 軸方向に"forward"に直面する必要があります。
3. シーンの原点 (0,0,0) にある地上平面上のすべての資産をビルドします。
4. 世界規模で資産を作成できるように、メーターと資産を作業単位を設定する必要があります。
5. すべてのメッシュを結合する必要はありませんが、リソースが制限されたデバイスを対象としている場合をお勧め
6. メッシュは、すべてが設定全体の資産に使用されている 1 つだけのテクスチャと 1 のマテリアルを共有する必要があります。
7. Uv は 0 ~ 1 の正方形の配置でレイアウトする必要があります領域。 許可されているテクスチャを並べて表示しないようにします。
8. マルチ Uv はサポートされていません
9. 二重の両面印刷資料はサポートされていません

### <a name="triangle-counts-and-levels-of-detail-lods"></a>三角形の数とレベル (Lod) の詳細

Windows Mixed Reality ホームは 10,000 を超える三角形でモデルをサポートしていません。 この数が超過しないようにするエクスポートする前に、メッシュを三角することをお勧めします。 Windows MR には、高性能、高品質なエクスペリエンスを確認する詳細 (Lod) の省略可能なジオメトリ レベルもサポートしています。 [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)モデルの 3 つのバージョンを 1 つ .glb モデルに結合する際に役立ちます。 Windows では、表示する LOD は、モデルを使用して画面領域の量に基づく判断します。 LOD の数が 3 つのレベルは、三角形の数をお勧めします。 次のようにサポートされます。
<br>

|  LOD レベル  |  推奨される三角形の数  |  三角形の最大数 | 
|------|------|------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>ノードの数といるサブメッシュの場合の制限
Windows Mixed Reality ホームは 64 を超えるノードまたは 32 submeshes LOD ごとのモデルをサポートしていません。 ノードがの概念、 [glTF 仕様](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)シーン内のオブジェクトを定義します。 Submeshes がの配列で定義されている[プリミティブ](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)はメッシュ オブジェクトにします。 

|  機能 |  説明  |  最大サポート | ドキュメント |
|------|------|------|------|
|  ノード |  GlTF シーン内のオブジェクト |  LOD あたり 64 | [ここは](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  上のすべてのメッシュ プリミティブの合計 |  LOD あたり 32 | [ここは](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>素材のガイドライン

PBR 金属製の粗さワークフローを使用して、テクスチャを準備する必要があります。 まず Albedo、Normal、オクルー ジョン、金属のような粗さなどのテクスチャの完全なセットを作成します。 Windows Mixed Reality サポートのテクスチャの解像度では、512 x 512 に作成者をその推奨 4096 x 4096 にアップします。 さらに、エクスポートの手順を以下に示すでテクスチャを適用する圧縮形式の要件は、4 の倍数単位の解像度でテクスチャを作成する必要があります。 最後に、いつ gerating mip マップまたはテクスチャの最下位の mip は、最大 4 x 4 を指定する必要があります。
<br>

|  テクスチャのサイズをお勧めします。  |  最大テクスチャ サイズ | 最も低い Mip
|----|----|----|
|  512 x 512  |  4096 x 4096 | 最大 4 x 4|

### <a name="albedo-base-color-map"></a>Albedo (基本色) のマップ

生の色、照明情報はありません。 このマップも含まれています、反射率とメタル (メタリックのマップに白) および (メタリック マップで黒) インシュレータ サーフェスの拡散はそれぞれします。

### <a name="normal"></a>標準

接空間標準マップ

### <a name="roughness-map"></a>粗さマップ

オブジェクトの microsurface について説明します。 ホワイト 1.0 は大まかな黒 0.0 はスムーズです。 このマップでは、資産の文字では、最もように、画面本当にについて説明します。 例: 傷を付けたり、指紋、汚れ汚れなど。

### <a name="ambient-occlusion-map"></a>アンビエント オクルー ジョン マップ

閉塞光の反射をブロックするの領域を表す値縮尺のマップ

### <a name="metallic-map"></a>金属のマップ

何かがメタルかどうかをシェーダーに指示します。 生のメタル = 1.0 の白以外メタル = 0.0 黒です。 土などの生のメタルをカバーするものを示す過渡期の灰色の値が存在できますが、一般にこのマップは白と黒のみをする必要があります。

## <a name="optimizations"></a>最適化

Windows Mixed Reality ホームには、一連のカスタム拡張機能を使用して定義 core glTF の仕様の上に最適化が用意されています。 Windows のバージョンでこれらの最適化が必要です < = 1709 および Windows の新しいバージョンでお勧めします。 GlTF 2.0 モデルを使用して簡単に最適化できる、 [Windows Mixed Reality 資産コンバーター GitHub で入手できます](https://github.com/Microsoft/glTF-Toolkit/releases)します。 このツールは、適切なテクスチャのパッキングと最適化の以下のように実行されます。 一般的な使用をお勧め、WindowsMRAssetConverter を使用してが、エクスペリエンスをさらに制御を必要があり、最適化のパイプラインをビルドする場合を参照できる以下の詳細な仕様。  

### <a name="materials"></a>マテリアル

資産の読み込み Mixed Reality 環境 Windows MR で時間を向上させるためには、テクスチャのこのセクションで定義されたスキームのパッキングに従ってパック DDS テクスチャの圧縮のレンダリングをサポートしています。 DDS テクスチャを使用して参照、 [MSFT_texture_dds 拡張子](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds)します。 テクスチャを圧縮することを強くお勧めします。 

#### <a name="hololens"></a>HoloLens

HoloLens に基づく複合現実エクスペリエンスには、次のパッキング仕様を使用して 2 テクスチャ セットアップを使用してパックするテクスチャが想定されます。
<br>

|  glTF プロパティ  |  テクスチャ  |  パッキング スキーム | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  赤 (R)、緑 (G)、青 (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  標準 (RG)、(B) の粗さメタリック (A) | 


DDS テクスチャを圧縮するときは、各マップで、次の圧縮が予期される値します。
<br>

|  テクスチャ  |  必要な圧縮 | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>(VR) のイマーシブ ヘッドセット

(VR) のイマーシブ ヘッドセット PC ベースの Windows Mixed Reality のエクスペリエンスには、次のパッキング仕様を使用して 3 テクスチャ セットアップを使用してパックするテクスチャが想定されます。

##### <a name="windows-os--1803"></a>Windows OS > 1803 を =

<br>

|  glTF プロパティ  |  テクスチャ  |  パッキング スキーム | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  赤 (R)、緑 (G)、青 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Occlusion (R)、粗さ (G)、メタリック (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  標準 (RG) | 

DDS テクスチャを圧縮するときは、各マップで、次の圧縮が予期される値します。
<br>

|  テクスチャ  |  必要な圧縮 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture、occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows OS < 1709 を =
<br>

|  glTF プロパティ  |  テクスチャ  |  パッキング スキーム | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  赤 (R)、緑 (G)、青 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Roughness (R)、メタリック (G)、遮蔽 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  標準 (RG) | 

DDS テクスチャを圧縮するときは、各マップで、次の圧縮が予期される値します。
<br>

|  テクスチャ  |  必要な圧縮 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>追加のメッシュ Lod

Windows MR では、さまざまな画面カバレッジによって詳細レベルでの 3D モデルを表示するために geometry ノード Lod が使用されます。 この機能は技術的には必要ありません、すべての資産の強くお勧めします。 現在 Windows では、3 つのレベルの詳細をサポートしています。 LOD 既定値は、0、最高の品質を表します。 他 Lod は順番に番号は 1、2、および品質の段階的に下位の get など。 [Windows Mixed Reality 資産コンバーター](https://github.com/Microsoft/glTF-Toolkit/releases) glTF の複数のモデルに同意し、有効な LOD レベルで 1 つのアセットにマージするしてこの LOD 仕様を満たしている資産を生成します。 次の表では、予想される LOD 三角形の順序付けとターゲットを示します。
<br>

|  LOD レベル  |  推奨される三角形の数  |  三角形の最大数 | 
|-------|-------|-------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

Lod を常に使用する場合は、3 つの LOD レベルを指定します。 Lod 不足するいると、不足している LOD レベルに LOD システムのスイッチとして予期せず表示されないモデルが発生します。 glTF 2.0 では、Lod は現在は、core の仕様の一部としてサポートしません。使用して Lod を定義する必要がありますので、 [MSFT_LOD 拡張子](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)します。

### <a name="screen-coverage"></a>画面のカバレッジ

各 LOD 設定画面のカバレッジの値によって駆動システムに基づく Windows Mixed Reality Lod が表示されます。 現在、画面スペースの大きな部分を使用しているオブジェクトより高い LOD レベルで表示されます。 画面のカバレッジ core glTF 2.0 の仕様の一部ではないと MSFT_ScreenCoverage の「extras」セクションを使用して指定する必要があります、 [MSFT_lod 拡張子](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)します。
<br>

|  LOD レベル  |  推奨される範囲  |  既定の範囲 | 
|-------|-------|-------|
|  LOD 0  |  100% - 50% |  .5 | 
|  LOD 1 |  50% ~ 20%  |  .2 | 
|  LOD 2 |  20% ~ 1%  |  .01 | 
|  LOD 4  |  1% 未満  |  - | 

## <a name="animation-guidelines"></a>アニメーションのガイドライン

> [!NOTE]
> この機能は、の一部として追加された[Windows 10 April 2018 Update](release-notes-april-2018.md)します。 これらのアニメーションを再生しないが Windows の以前のバージョン、ただし、これらの読み込みが続行この記事のガイダンスに従って作成する場合。  

複合現実ホーム HoloLens と没入型の (VR) ヘッドセット glTF をアニメーション化されたオブジェクトをサポートします。 モデル上でアニメーションをトリガーする場合は、glTF 形式で、アニメーションのマップの拡張機能を使用する必要があります。 この拡張機能では、世界中のユーザーの有無に基づいて glTF モデルでのアニメーションをトリガー、たとえば、ユーザーがオブジェクトに近い、または確認するときにアニメーションをトリガーすることができます。 GlTF オブジェクト、アニメーションがトリガーが定義されていない場合、アニメーションは戻る再生できません。 以下のセクションでは、任意のアニメーション化された glTF オブジェクトにこれらのトリガーを追加するための 1 つのワークフローについて説明します。

### <a name="tools"></a>ツール
最初に、まだ持っていない場合は、次のツールをダウンロードします。 これらのツールは簡単に任意 glTF モデルを開く、プレビューして、変更、および glTF または .glb として元に戻すに保存します。
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [glTF Tools for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>開くと、モデルのプレビュー
.GlTF ファイルがエディター ウィンドウにドラッグすることにより、VSCode で glTF モデルを開くことで開始します。 .GlTF ファイルではなく、.glb がある場合にインポートできます、ダウンロードした glTF ツール アドインを使用した VSCode に注意してください。 "ビューでは、コマンド パレットを ->"に移動し、しコマンド パレットで"glTF"の入力を開始し、選択"glTF:インポート glb から"での .glb をインポートするためのファイル ピッカーが表示されます。 

GlTF モデルを開いたら、エディター ウィンドウで JSON が表示されます。 注 3 D のライブ ビューアーを使用して、モデルをプレビューすることも、ファイル名を右クリックしを選択すると、"glTF:3D モデルをプレビューするには"右クリック メニューからショートカットをコマンド。 

### <a name="adding-the-triggers"></a>トリガーを追加します。
アニメーションのトリガーは、glTF モデル、アニメーションのマップの拡張機能を使用して JSON に追加されます。 アニメーションのマップの拡張機能が公式に文書化[こちらの GitHub](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) (注。これは、ドラフトの拡張機能) です。 エディターで glTF ファイルの末尾には、モデルだけスクロールに、拡張機能を追加しがまだ存在しない場合、ファイルに"extensionsUsed"と"extensions"のブロックを追加します。 "ExtensionsUsed"セクションでは、"EXT_animation_map"拡張機能への参照を追加し、"extensions"ブロックでは、モデルのアニメーションをマッピングを追加します。

説明したように[仕様で](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md)アニメーション インデックスの配列である「アニメーション」の一覧で、「セマンティック」文字列を使用してアニメーションを何によってトリガーを定義します。 次の例で、ユーザーがオブジェクトで gazing 間を再生するアニメーションを指定しました。

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
次のアニメーション トリガー セマンティクスは、home、Windows Mixed Reality でサポートされます。  
* 「常時」:アニメーションの継続的にループします。
* 「保持」します。全体の期間内にループ オブジェクトが取得されます。
* 「注視」:オブジェクトを検索している間にループ処理
* 「近く」:ビューアーは、オブジェクトの近くにある間をループ処理
* 「ポイント」しています。オブジェクトで、ユーザーがポイント間をループ処理

### <a name="saving-and-exporting"></a>保存とエクスポート
GlTF として直接保存することができます、glTF モデルに変更を加えたかを右クリックし、エディターでファイルの名前を 1 回"glTF:GLB (バイナリ ファイル) へのエクスポート"を代わりに、.glb をエクスポートします。 

### <a name="restrictions"></a>制限
アニメーションは、20 分より長くすることはできず、複数の 36,000 キーフレーム (20 分、30 FPS) を含めることはできません。 さらに基づき、morph ターゲットを使用する場合のアニメーションに 8192 morph ターゲット頂点を超えないように以下。 これらの数は問題 Windows Mixed Reality 自宅でサポートされていないアニメーション化された資産を上回っています。 

|機能|[最大]|
|-----|-----|
|Duration|20 分|
|キーフレーム|36,000| 
|Morph ターゲット頂点|8192|

## <a name="gltf-implementation-notes"></a>glTF 実装に関する注意事項
Windows MR は負の値のスケールを使用してジオメトリをフリッピングをサポートしていません。 成果物を視覚的になる可能性がありますの負の値のスケールでジオメトリ。

GlTF 資産は、Windows MR によってをレンダリングするシーン属性を使用して既定のシーンをポイントする必要があります。 前のバージョンの Windows MR glTF ローダーさらに、 [Windows 10 April 2018 update](release-notes-april-2018.md) **必要**アクセサー。
* 最小値と最大値が必要です。
* スカラーの型は componentType UNSIGNED_SHORT (5123) または UNSIGNED_INT (5125) である必要があります。
* 型 VEC2 と VEC3 componentType FLOAT (5126) があります。

次の素材のプロパティは core glTF 2.0 仕様の使用しますが、必要ありません。
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture:Dds に格納されているテクスチャを指す必要があります。
* emissiveTexture:Dds に格納されているテクスチャを指す必要があります。
* emissiveFactor
* alphaMode

次の素材のプロパティは、core の仕様から無視されます。
* すべてのマルチ Uv
* metalRoughnessTexture:以下に定義された、最適化された Microsoft テクスチャ パッキングを代わりに使用する必要があります。
* normalTexture:以下に定義された、最適化された Microsoft テクスチャ パッキングを代わりに使用する必要があります。
* normalScale
* occlusionTexture:以下に定義された、最適化された Microsoft テクスチャ パッキングを代わりに使用する必要があります。
* occlusionStrength

Windows MR はプリミティブ モード線およびポイントをサポートしていません。 

1 つの UV 頂点属性のみがサポートされています。

## <a name="additional-resources"></a>その他の資料
* [glTF エクスポーターとコンバーター](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF ツールキット](https://github.com/Microsoft/glTF-Toolkit)
* [glTF 2.0 仕様](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft glTF LOD 拡張機能仕様](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [PC が実際にはテクスチャ パッキング拡張仕様の混在](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens 現実テクスチャ パッキング拡張仕様の混在](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS テクスチャ glTF 拡張機能仕様](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>関連項目

* [3D アプリ起動ツールの実装 (UWP アプリ)](implementing-3d-app-launchers.md)
* [3D アプリ起動ツールの実装 (Win32 アプリ)](implementing-3d-app-launchers-win32.md)
* [Windows Mixed Reality ホームのナビゲーション](navigating-the-windows-mixed-reality-home.md)
