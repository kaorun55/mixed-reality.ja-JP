---
title: 導入事例 - HoloLens の空間のマッピング機能を展開します。
description: Microsoft HoloLens の最初のアプリを作成するときにどの程度空間マッピングの境界デバイスにプッシュできますを参照してください。 一括でした。
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、空間マッピング
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602834"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>導入事例 - HoloLens の空間のマッピング機能を展開します。

Microsoft HoloLens の最初のアプリを作成するときにどの程度空間マッピングの境界デバイスにプッシュできますを参照してください。 一括でした。 Jeff Evertt、Microsoft Studios のソフトウェア エンジニアは、ユーザーの実際の環境でホログラムを配置する方法より詳細に制御の必要性からの新しいテクノロジが開発方法について説明します。

## <a name="watch-the-video"></a>ビデオを見る

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>空間マッピングを超える

作業中に[フラグメント](https://www.microsoft.com/p/fragments/9nblggh5ggm8)と[Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)2 つ、HoloLens の最初のゲームのわかりました、物理世界でホログラムの手続き型の配置を実行していた、ときに必要である上位のレベルユーザーの環境について理解します。 各ゲームでは、独自の特定の配置のニーズがありました。フラグメントでなどしたい異なるサーフェスを区別するためにできるように、床やテーブルなど — 手がかりを関連する場所に配置します。 など、ソファまたは椅子等身大 holographic 文字に座って、サーフェスを識別するためにできるようにすることも考えました。 Young の Conker で Conker と彼の対戦相手のプレイヤーの部屋で発生サーフェスをプラットフォームとして使用することができると考えました。

[Asobo スタジオ](http://www.asobostudio.com/index.html)、これらのゲームの開発パートナーが正面を向けたこの問題に直面し、HoloLens の空間のマッピング機能を拡張するテクノロジを作成します。 これを使用して、私たちとでしたプレイヤーのルームを分析し、壁、テーブル、椅子、フロアなどのサーフェスを識別します。 これもくれました holographic オブジェクトの最適な配置を決定する制約のセットに対して最適化する機能。

## <a name="the-spatial-understanding-code"></a>コードを空間の理解

Asobo の元のコードをこのテクノロジをカプセル化するライブラリを作成します。 Microsoft と Asobo これでこのコードをオープン ソース化されで利用できるように[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping)独自のプロジェクトで使用するためです。 すべてのソース コードが含まれて、ニーズに合わせてカスタマイズし、改善をコミュニティで共有することができます。 コードをC++ソルバーを UWP DLL にラップし、Unity に公開されている、 [MixedRealityToolkit 内に含まれるドロップイン プレハブ](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)します。

Unity のサンプルを壁の空白を検索、天井または床に大きなスペース上のオブジェクトを配置、場所に配置するには、文字と、多種多様な空間についての他のクエリを識別することが含まれている多くの便利なクエリがあります。

HoloLens によって提供される空間マッピング ソリューションを設計して、あらゆる問題領域のニーズを満たすのに十分なジェネリックにする、中に、空間理解モジュールは 2 つの特定のゲームのニーズをサポートするために構築されました。 そのため、特定のプロセスと前提条件のセットをそのソリューションが構成されています。
* **固定サイズ playspace**:ユーザーは、init 呼び出しで最大 playspace サイズを指定します。
* **1 回限りのスキャン プロセス**:プロセスが必要、個別スキャン フェーズの周囲、ユーザーがについて説明します、playspace を定義します。 スキャンが終了した後、クエリ関数はまで機能しなくなります。
* **ユーザー駆動 playspace「描画」**:スキャン フェーズでは、ユーザーが移動し、効果的に含まれるとして使用する領域を描画、playspace を検索します。 生成したメッシュは、このフェーズ中にユーザーからのフィードバックを提供する必要があります。
* **屋内自宅またはオフィスのセットアップ**:クエリ関数は、フラット サーフェスと直角に交わって壁を中心に設計されています。 これは、ソフト制限です。 ただし、スキャン フェーズでは、プライマリ軸の分析がメジャーおよびマイナーの軸に沿ったメッシュ テセレーションを最適化するために完了します。

### <a name="room-scanning-process"></a>ルームのスキャン プロセス

自分のスペースで使用可能なすべてのサーフェスをスキャンは、空間的に理解モジュールを読み込むときに、まず操作を行います: floor、ceiling、壁など — が特定され、ラベル付けします。 部屋を確認するスキャンの処理中に、"ペイント '、スキャンで含める必要がある領域です。

このフェーズ中に検出されたメッシュは、ユーザーがスキャンされるルームのどの部分を認識できるようにする視覚的なフィードバックの重要な要素です。 空間理解モジュールの DLL は、サイズ 8 cm voxel キューブのグリッドとして、playspace を内部的に格納します。 スキャンの初期段階では、部屋の軸を決定する主要なコンポーネントの分析が完了しました。 内部的には、これらの軸に配置されたその voxel 領域を格納します。 メッシュには、voxel ボリュームからアイソサーフェスを抽出することによって毎秒約が生成されます。

![白色のメッシュのマップを playspace を把握する空間が緑色でメッシュします。](images/spatial-mapping-500px.png)

白色のメッシュのマップを playspace を把握する空間が緑色でメッシュします。



インクルード SpatialUnderstanding.cs ファイルは、スキャン フェーズの処理を管理します。 次の関数を呼び出します。
* **SpatialUnderstanding_Init**:開始時に 1 回呼び出されます。
* **GeneratePlayspace_InitScan**:スキャンのフェーズを開始することを示します。
* **GeneratePlayspace_UpdateScan_DynamicScan**:スキャン プロセスを更新するには、各フレームで呼び出されます。 カメラの位置と向きに渡され、playspace 描画プロセスは、上記で説明したために使用します。
* **GeneratePlayspace_RequestFinish**:Playspace を最終処理と呼ばれます。 これを定義し、ロック、playspace スキャン フェーズ中に「描画」領域を使用します。 アプリケーションでは、スキャン フェーズと、ユーザーからのフィードバックを提供するためのカスタムのメッシュをクエリ中に、統計情報を照会できます。
* **Import_UnderstandingMesh**:スキャン中に、 **SpatialUnderstandingCustomMesh**モジュールによって提供されており、理解プレハブ上に配置の動作は、プロセスによって生成されるカスタムのメッシュを定期的にクエリします。 さらに、これはもう一度スキャンが終了した後です。

スキャンのフローによって、 **SpatialUnderstanding**動作呼び出し**InitScan**、し**UpdateScan**各フレーム。 統計情報のクエリが妥当なカバレッジを報告したときで、ユーザーを呼び出す airtap **RequestFinish**スキャン フェーズの終了を示す。 **UpdateScan**が戻り値になるまでに呼び出される継続値では、DLL の処理が完了したことを示します。

## <a name="the-queries"></a>クエリ

スキャンが完了すると、インターフェイス内のクエリの 3 つの異なる型にアクセスすることができます。
* **トポロジ クエリ**:これらは、スキャンした部屋のトポロジに基づいている高速なクエリです。
* **クエリの整形**:これらは、トポロジを定義したカスタム図形とよく一致する水平方向のサーフェスを検索するクエリの結果を利用します。
* **オブジェクト配置のクエリを**:これらは、一連のルールと、オブジェクトの制約に基づいて最適の場所を検索するより複雑なクエリです。

3 つの主要なクエリだけでなく、タグが付けられたサーフェイスのタイプを取得するために使用できるレイキャスト インターフェイスがあるし、カスタムのような厳重な部屋のメッシュをコピーすることができます。

### <a name="topology-queries"></a>トポロジのクエリ

DLL 内では、トポロジのマネージャーは、環境のラベル付けを処理します。 前述のとおり、surfels voxel ボリューム内に格納されているデータの多く格納されます。 さらに、 **PlaySpaceInfos**構造を使用して、世界中の配置 (詳細については後述)、floor、ceiling 高さなど、playspace に関する情報を格納します。

ヒューリスティックは、floor、ceiling、壁を決定するために使用されます。 たとえば、1 m2 のサーフェス領域よりも大きいと、最大および最小の水平方向の画面は、床面と見なされます。 スキャン プロセス中にカメラのパスがこのプロセスで使用されるもことに注意してください。

トポロジのマネージャーによって公開されているクエリのサブセットは、出力 DLL を介して公開されます。 公開されているトポロジのクエリは次のとおりです。
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

各クエリは、クエリの種類に固有のパラメーターのセットがあります。 次の例では、ユーザーは、高さの最小値と最小の配置、フロア、クリアランスの前に、ボリュームの最小量の高さ、目的のボリュームの幅を指定します。 すべての測定値では、メートル単位で。




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

これらの各クエリの事前に割り当てられた配列を取得する**TopologyResult**構造体。 **LocationCount**パラメーターが渡された配列の長さを指定します。 戻り値は、返される位置の数を報告します。 この数が、渡されたに超えることはありません**locationCount**パラメーター。

**TopologyResult**返されるボリュームに接続する方向 (つまり標準)、および検索の領域の大きさの中央の位置が含まれています。




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Unity のサンプルでは、これらの各クエリがリンクされている仮想 UI パネルのボタンに注意してください。 ハードのサンプル コードは妥当な値にこれらのクエリの各パラメーター。 参照してください*SpaceVisualizer.cs*例については、サンプル コード。

### <a name="shape-queries"></a>Shape クエリ

図形のアナライザー、DLL 内で (**ShapeAnalyzer_W**) トポロジのアナライザーを使用して、ユーザーが定義したカスタム図形に対して照合します。 Unity のサンプルでは、クエリ メニューの 図形 タブに示されている図形の定義済みセットがあります。

形状の分析が水平方向のサーフェスのみで機能するに注意してください。 たとえば、ソファーは、戻るカウチのフラットの上端とフラット seat 画面によって定義されます。 Shape クエリは、特定のサイズ、高さ、および縦横範囲の配置し、接続されている 2 つのサーフェスの 2 つのサーフェスを探します。 Api の用語を使用するには、ソファ クライアント数と、ソファーの後ろの上部は図形のコンポーネントと配置の要件は次の図形コンポーネントの制約。

Unity のサンプルで定義されているクエリの例 (**ShapeDefinition.cs**) は、"sittable"オブジェクトの次のようには。




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

各図形のクエリは、それぞれに、一連のコンポーネントの制約と、コンポーネント間の依存関係の一覧を表示する一連の図形の制約、図形のコンポーネントのセットによって定義されます。 この例には、(1 つだけのコンポーネントであるため)、1 つのコンポーネントの定義とコンポーネント間で制約のない図形で次の 3 つの制約が含まれます。

これに対し、ソファ図形は、2 つのコンポーネントの図形と図形の 4 つの制約をが。 コンポーネントが (0 からこの例では 1) のユーザーのコンポーネントの一覧で、インデックスで識別されることに注意してください。




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

ラッパー関数は、カスタム図形の定義を簡単に作成の Unity モジュールで提供されます。 コンポーネントと図形の制約の完全な一覧が記載されて**SpatialUnderstandingDll.cs**内、 **ShapeComponentConstraint**と**ShapeConstraint**構造体。

![青い四角形には、椅子の shape クエリの結果が強調表示されます。](images/chair-shape-query-500px.png)

青い四角形には、椅子の shape クエリの結果が強調表示されます。



### <a name="object-placement-solver"></a>オブジェクト配置のソルバー

オブジェクト配置のクエリは、オブジェクトを配置する物理的な部屋に理想的な場所を識別するために使用できます。 最適の場所オブジェクトの規則と制約ソルバーが見つかります。 オブジェクトが削除されるまでさらに、オブジェクト クエリを永続化**Solver_RemoveObject**または**Solver_RemoveAllObjects**呼び出しを許可する複数のオブジェクトの配置の制約します。

オブジェクト配置のクエリは、3 つの部分で構成されています: パラメーター、一連の規則、制約のリストと配置の種類。 クエリを実行するには、次の API を使用します。




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
この関数は、オブジェクトの名前、配置の定義と規則と制約の一覧を受け取ります。 C#ラッパーは構築規則と制約の構築を簡単にできるようにするヘルパー関数を提供します。 配置の定義には、クエリの種類が含まれています: は、次のいずれかの。




```
public enum PlacementType
                {
                    Place_OnFloor,
                    Place_OnWall,
                    Place_OnCeiling,
                    Place_OnShape,
                    Place_OnEdge,
                    Place_OnFloorAndCeiling,
                    Place_RandomInAir,
                    Place_InMidAir,
                    Place_UnderFurnitureEdge,
                };
```

パラメーターの型に固有の各配置の種類があります。 **ObjectPlacementDefinition**構造には、これらの定義を作成するための静的なヘルパー関数のセットが含まれています。 たとえば、床の上にオブジェクトを配置する場所を検索するには、次の関数を使用できます。 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

配置の種類だけでなく、一連の規則と制約を行うことができます。 規則に違反することはできません。 型とルールに適合するような配置場所は、最適な配置場所を選択する制約のセットに対して、最適化されています。 指定された静的作成関数によって各規則と制約を作成できます。 規則と制約の構築関数の例を以下に示します。




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

次のオブジェクト配置のクエリは、画面の端に半分メーター キューブを配置から他のオブジェクトを配置前、ルームの中心付近を場所探しています。




```
List<ObjectPlacementRule> rules = 
          new List<ObjectPlacementRule>() {
               ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
          };

     List<ObjectPlacementConstraint> constraints = 
          new List<ObjectPlacementConstraint> {
               ObjectPlacementConstraint.Create_NearCenter(),
          };

     Solver_PlaceObject(
          “MyCustomObject”,
          new ObjectPlacementDefinition.Create_OnEdge(
          new Vector3(0.25f, 0.25f, 0.25f), 
          new Vector3(0.25f, 0.25f, 0.25f)),
          rules.Count,
          UnderstandingDLL.PinObject(rules.ToArray()),
          constraints.Count,
          UnderstandingDLL.PinObject(constraints.ToArray()),
          UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

成功した場合、 **ObjectPlacementResult**配置位置、ディメンション、および印刷の向きを含む構造体が返されます。 さらに、配置は、配置されたオブジェクトの DLL の内部一覧に追加されます。 後続の配置のクエリ アカウントにこのオブジェクトになります。 **LevelSolver.cs** Unity サンプル内のファイルに複数のクエリ例にはが含まれています。

![青い四角形は、"離れたからカメラの位置"規則の 3 つの場所でフロア クエリから結果を表示します。](images/away-from-camera-position-500px.png)

青い四角形は、"離れたからカメラの位置"規則の 3 つの場所でフロア クエリから結果を表示します。


**ヒント:**
* レベルまたはアプリケーションのシナリオに必要な複数のオブジェクトの配置場所を解決するときに最初にスペースが含まれる確率を最大化に欠かせないや大規模なオブジェクトを解決します。
* 配置の順序が重要です。 オブジェクトへの配置が見つからない場合は、あまりに制約付きの構成をお試しください。 フォールバック構成のセットは、ルーム構成で多くの機能をサポートしているに不可欠です。

### <a name="ray-casting"></a>光線のキャスト

3 つの主要なクエリだけでなく、ray キャスト インターフェイスを使用してタグが付けられたサーフェイスのタイプを取得して、カスタムのような厳重な playspace メッシュをコピーすることができますを部屋がスキャンされ、ファイナライズ後ラベルが内部的に生成されるなどの表面に対して、floor、ceiling、および壁します。 **PlayspaceRaycast**関数光線受け取り射線が既知の画面と競合する場合とそうである場合に返されますの形式でその画面については、 **RaycastResult**します。 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

内部的には、playspace の計算の 8 cm cubed voxel 表現に対して、raycast が計算されます。 各 voxel には、一連画面要素に処理されたトポロジのデータ (surfels とも呼ばれます) にはが含まれています。 Voxel が交差するセル内に含まれる surfels が比較され、最も一致するトポロジ情報を検索するために使用します。 このトポロジのデータが含まれています、ラベル付けの形式で返される、 **SurfaceTypes**列挙型、交差する画面の表面領域とします。

Unity のサンプルでは、カーソルは各フレームに伸びる射線をキャストします。 Unity のコライダー; に対して最初に、understanding モジュールの世界の表現; に対して第 2 に、UI 要素に対して最後と。 このアプリケーションでは、UI は、優先度、し、理解の結果、および最後に、Unity のコライダーを取得します。 **SurfaceType**カーソルの横にあるテキストとしてレポートされます。

![Raycast 結果の床面との交差を報告します。](images/raycast-result-500px.jpg)

Raycast 結果の床面との交差を報告します。


## <a name="get-the-code"></a>コードを入手する

オープン ソース コードは[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)します。 知らせ、 [HoloLens デベロッパー フォーラム](https://forums.hololens.com/)プロジェクトでコードを使用する場合。 これで何を参照してください。 楽しみです。

## <a name="about-the-author"></a>執筆者紹介

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b> HoloLens の開発を体験する育成から、初期の段階から作業しているソフトウェア エンジニア リング リードです。 HoloLens、前に、Xbox Kinect にし、多様なプラットフォームやゲームのゲーム業界で働いていました。 Jeff はロボット工学、グラフィック、およびピカピカ ビープ音を移動することに熱心です。 彼の新機能を学習し、ソフトウェア、ハードウェア、および特に 2 つの交差領域の操作を楽しんでいます。</td>
</tr>
</table>



## <a name="see-also"></a>関連項目
* [空間マッピング](spatial-mapping.md)
* [空間マッピングの設計](spatial-mapping-design.md)
* [ルームのスキャンの視覚化](room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio:HoloLens の開発の最前線になってからの教訓](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
