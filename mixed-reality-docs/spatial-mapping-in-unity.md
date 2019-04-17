---
title: Unity での空間のマッピング
description: レンダリングして、Unity で周囲の実際のジオメトリとの衝突とします。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、空間マッピング、レンダラー、コライダー、メッシュ、スキャン、コンポーネント
ms.openlocfilehash: f938f5921cb2c06342a9ebcd376d690c10584df9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605158"
---
# <a name="spatial-mapping-in-unity"></a>Unity での空間のマッピング

このトピックでは、使用する方法を説明します[空間マッピング](spatial-mapping.md)Unity プロジェクトで、配置、オクルー ジョン、部屋の分析などの HoloLens デバイスの世界でサーフェスを表す三角形メッシュを取得します。

Unity には、次の方法で開発者に公開される空間マッピングは、完全にサポートが含まれています。
1. 空間マッピング、MixedRealityToolkit で利用可能なコンポーネントが便利で高速のパスを指定空間マッピングの概要
2. 下位の空間マッピング Api では、完全に提供する制御しより高度なアプリケーション固有のカスタマイズを有効にします。

空間マッピングを使用して、アプリで、spatialPerception 機能は、AppxManifest で設定する必要があります。

## <a name="setting-the-spatialperception-capability"></a>SpatialPerception 機能の設定

アプリ データを空間マッピングを使用するためには、SpatialPerception 機能を有効にする必要があります。

SpatialPerception 機能を有効にする方法。
1. Unity エディターで開き、 **「プレーヤー設定」** ウィンドウ (編集 > プロジェクトの設定 > Player)
2. をクリックして、 **"Windows Store"**  タブ
3. 展開 **「発行の設定」** を確認し、 **"SpatialPerception"** 機能、 **「機能」** 一覧

Visual Studio ソリューションに既に Unity プロジェクトをエクスポートした場合でも、新しいフォルダーに手動でまたはいずれかのエクスポートする必要がする[Visual Studio で AppxManifest でこの機能を設定](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)します。

空間マッピングには、少なくとも 10.0.10586.0 の MaxVersionTested も必要です。
1. Visual Studio で右クリック**Package.appxmanifest**クリックし、ソリューション エクスプ ローラーで**コードの表示**
2. 行を指定するように検索**TargetDeviceFamily**変更と**MaxVersionTested =「10.0.10240.0」** に**MaxVersionTested「=10.0.10586.0」**
3. **保存**Package.appxmanifest します。

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Unity の組み込みの空間マッピング コンポーネントの概要

Unity は、アプリを簡単に空間マッピングを追加するための 2 つのコンポーネントを提供**空間マッピング レンダラー**と**空間マッピング Collider**します。

### <a name="spatial-mapping-renderer"></a>空間マッピングのレンダラー

空間マッピング レンダラーでは、空間マッピング メッシュの視覚化ができます。

![Unity での空間マッピング レンダラー](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>空間マッピング Collider

空間マッピング Collider で holographic コンテンツ (または文字) は、空間マッピングのメッシュと物理学などの対話します。

![Unity での空間マッピング Collider](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>空間マッピングの組み込みコンポーネントを使用します。

視覚化して、物理画面と対話したい場合は、アプリに両方のコンポーネントを追加できます。

Unity のアプリでは、これら 2 つのコンポーネントを使用します。
1. 空間表面メッシュを検出するために領域を中心の GameObject を選択します。
2. Inspector ウィンドウで、**コンポーネントの追加** > **XR** > **空間マッピング Collider** または**空間マッピング レンダラー**します。

これらのコンポーネントを使用する方法の詳細についての詳細を確認することができます、 <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity ドキュメント サイト</a>します。

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>組み込みの空間マッピング コンポーネントの先を行く

これらのコンポーネントようにドラッグ アンド ドロップ簡単空間マッピングを開始します。  さらに移動する場合は、2 つのメイン パスを探索するがあります。
* 下位レベルのメッシュ処理を行うには、低レベルの空間マッピング スクリプト API の詳細については、以下のセクションを参照してください。
* メッシュのより高度な分析で SpatialUnderstanding ライブラリの詳細については、以下のセクションを参照してください。 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>します。

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>API を使用して、低レベル Unity 空間マッピング

空間マッピングのレンダラーと空間マッピング コライダー コンポーネントから取得するよりも詳細に制御が必要な場合は、低レベルの空間マッピング スクリプト Api を使用できます。

**名前空間:***UnityEngine.XR.WSA*<br>
**型**:*SurfaceObserver*、 *SurfaceChange*、 *SurfaceData*、 *SurfaceId*

空間マッピング Api を使用するアプリケーションの推奨されるフローの概要を次に示します。

### <a name="set-up-the-surfaceobservers"></a>設定する、SurfaceObserver(s)

空間のマッピング データが必要な領域をアプリケーションで定義された地域ごとに 1 つの SurfaceObserver オブジェクトをインスタンス化します。

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

各 SurfaceObserver オブジェクトは SetVolumeAsSphere、SetVolumeAsAxisAlignedBox、SetVolumeAsOrientedBox、または SetVolumeAsFrustum を呼び出すことでのデータを提供する領域の領域を指定します。 これらのメソッドのいずれかをもう一度呼び出すだけで、将来の領域の領域を再定義できます。

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

SurfaceObserver.Update() を呼び出すときに、各空間のサーフェス空間マッピング システムが新しい情報の領域の SurfaceObserver のリージョンでのハンドラーを提供する必要があります。 このハンドラーは、空間の 1 つの画面には。

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>画面の変更の処理

処理するためにいくつかの主要な場合があります。 追加 (&) 同じが使用できる更新コードのパスおよび削除します。
* 例では、更新 (&)、追加された場合は、追加または取得ディクショナリからメッシュを必要なコンポーネントで SurfaceData 構造体を作成し、GameObject にメッシュのデータを設定する RequestMeshDataAsync を呼び出しますこの GameObject 表すこととシーンに配置します。
* 削除済みの場合は、ディクショナリからこのメッシュを表す GameObject を削除し、それを破棄します。

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a>処理データの準備完了

OnDataReady ハンドラーは、SurfaceData オブジェクトを受け取ります。 WorldAnchor、MeshFilter および (必要に応じて) MeshCollider オブジェクトが含まれている、関連付けられている空間画面の最新の状態を反映します。 必要に応じて分析を実行または[処理](spatial-mapping.md#mesh-processing)MeshFilter オブジェクトのメッシュのメンバーにアクセスしてメッシュ データ。 最新のメッシュに空間サーフェイスを描画して、(必要に応じて) 物理衝突と raycasts に使用します。 SurfaceData の内容が null でないことを確認するのには重要です。

### <a name="start-processing-on-updates"></a>更新プログラムの処理を開始します。

SurfaceObserver.Update() は、遅延、すべてのフレームに呼び出す必要があります。

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>高度なメッシュ分析:SpatialUnderstanding

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> holographic Unity Api に基づいて構築された holographic の開発のための便利なユーティリティ コードのコレクションです。

### <a name="spatial-understanding"></a>空間の理解

現実の世界でホログラムを配置するときに、空間のマッピングを超えるメッシュし、平面の画面を移動することが望ましいは多くの場合です。 配置が完了したら手続きより高いレベルの環境の理解をお勧めします。 通常、このエラーは、floor、ceiling、および壁についての決定が必要です。 さらに、holographic オブジェクトの最も望ましいの物理的な場所を確認する配置の制約のセットに対して最適化するために機能します。

、Young Conker とフラグメントの開発中に、この目的のルーム問題を解くプログラムの開発には、この問題ヘッドが Asobo スタジオに直面しています。 これらのゲームのゲームの特定のニーズがテクノロジの空間についてのコアを共有しています。 配置するには、文字と、多種多様な空間についての他のクエリを識別するとすばやく検索空白には、壁、オブジェクトの切り上げを配置することができます。 このテクノロジがライブラリにカプセル化します HoloToolkit.SpatialUnderstanding が配置されます。

すべてのソース コードは、ニーズに合わせてカスタマイズし、改善をコミュニティで共有することができます、含まれています。 コードをC++ソルバーが UWP dll にラップされの場合は、MixedRealityToolkit 内に含まれるプレハブを Unity に公開します。

### <a name="understanding-modules"></a>モジュールについて

モジュールによって公開される 3 つのプライマリ インターフェイスがあります。 単純な画面と空間クエリ、オブジェクト検出では、図形、および制約ベースの配置オブジェクトのセットのオブジェクト配置のソルバーのトポロジ。 これらのそれぞれについて、次に示します。 3 つのプライマリ モジュール インターフェイスに加えて、ray キャスト インターフェイスを使用して、タグが付けられたサーフェイスのタイプを取得することし、カスタムのような厳重な playspace メッシュをコピーすることができます。

### <a name="ray-casting"></a>光線のキャスト

ルームをスキャンされ、完了した後、ラベルは floor、ceiling、壁のようなサーフェイス内部的に生成されます。 "RaycastResult"の形式で表示される情報、"PlayspaceRaycast"関数が光線に受け取り、ray が既知の画面と競合している場合であればを返します。

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

内部的には、playspace の計算の 8 cm cubed voxel 表現に対して、raycast が計算されます。 各 voxel には、一連画面要素に処理されたトポロジのデータ (surfels とも呼ばれます) にはが含まれています。 Voxel が交差するセル内に含まれる surfels が比較され、最も一致するトポロジ情報を検索するために使用します。 このトポロジのデータを含む"SurfaceTypes"列挙型のフォームと交差する画面の表面領域で返される、ラベル付けします。

Unity のサンプルでは、カーソルは各フレームに伸びる射線をキャストします。 Unity のコライダーに対して最初に。 Understanding モジュールの世界の表現に対して第 2 に。 最後に、もう一度 UI 要素。 このアプリケーションで UI は、理解の結果と Unity のコライダーの最後に、次に、優先順位を取得します。 カーソルの横にあるテキストとして、SurfaceType が報告されます。

![画面の種類のカーソルの横にあるラベルは](images/su-raycastresults-300px.jpg)<br>
*画面の種類のカーソルの横にあるラベルは*

### <a name="topology-queries"></a>トポロジのクエリ

DLL 内では、トポロジのマネージャーは、環境のラベル付けを処理します。 前述のように、surfels、voxel ボリューム内に含まれるデータの多く格納されます。 さらに、"PlaySpaceInfos"構造を使用して、世界中の配置 (詳細については後述)、floor、ceiling 高さなど、playspace についての情報を格納します。 ヒューリスティックは、floor、ceiling、壁を決定するために使用されます。 たとえば、1 m2 のサーフェス領域よりも大きいと、最大および最小の水平方向の画面は、床面と見なされます。 スキャン プロセス中にカメラのパスがこのプロセスで使用されるもことに注意してください。

トポロジのマネージャーによって公開されているクエリのサブセットは、出力 dll を介して公開されます。 公開されているトポロジのクエリは次のとおりです。

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

各クエリは、クエリの種類に固有のパラメーターのセットがあります。 次の例では、ユーザーは、高さの最小値と最小の配置、フロア、クリアランスの前に、ボリュームの最小量の高さ、目的のボリュームの幅を指定します。 すべての測定値では、メートル単位で。

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

これらの各クエリは、事前に割り当てられた"TopologyResult"構造体の配列を受け取る。 "LocationCount"パラメーターには、渡された配列の長さを指定します。 戻り値は、返される位置の数を報告します。 この数値が渡されたを超えることはありません"locationCount"パラメーターにします。

"TopologyResult"には、返されるボリュームに接続する方向 (つまり標準)、および検索の領域の大きさの中央の位置が含まれています。

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

Unity のサンプルでは、これらの各クエリがリンクされている仮想 UI パネルのボタンに注意してください。 ハードのサンプル コードは妥当な値にこれらのクエリの各パラメーター。 例については、サンプル コードでは、SpaceVisualizer.cs を参照してください。

### <a name="shape-queries"></a>Shape クエリ

Dll 内では、図形アナライザー ("ShapeAnalyzer_W") は、ユーザーが定義したカスタム図形と照合するトポロジ アナライザーを使用します。 Unity のサンプルでは、図形のセットを定義し、アプリ内のクエリ メニューの 図形 タブ内からの結果を生成を公開します。ユーザーが独自オブジェクト図形のクエリを定義しを加えることは、アプリケーションの必要に応じて、それらの使用します。

形状の分析が水平方向のサーフェスのみで機能するに注意してください。 たとえば、ソファーは、戻るカウチのフラットの上端とフラット seat 画面によって定義されます。 Shape クエリは、特定のサイズ、高さ、および縦横範囲の配置し、接続されている 2 つのサーフェスの 2 つのサーフェスを探します。 Api の用語を使用するには、ソファ シートとバック上部は、図形のコンポーネントと、アラインメント要件は次の図形のコンポーネントの制約。

"Sittable"オブジェクトの Unity サンプル (ShapeDefinition.cs) で定義されているクエリの例は次のとおりです。

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

各図形のクエリは、一連の図形コンポーネントは、それぞれに、一連のコンポーネントの制約と、一連の図形の制約によって定義されるコンポーネント間の依存関係を一覧表示します。 この例には、(1 つだけのコンポーネントであるため)、1 つのコンポーネントの定義とコンポーネント間で制約のない図形で次の 3 つの制約が含まれます。

これに対し、ソファ図形は、2 つのコンポーネントの図形と図形の 4 つの制約をが。 コンポーネントが (0 からこの例では 1) のユーザーのコンポーネントの一覧で、インデックスで識別されることに注意してください。

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

ラッパー関数は、カスタム図形の定義を簡単に作成の Unity モジュールで提供されます。 コンポーネントと図形の制約の完全な一覧は、"SpatialUnderstandingDll.cs"、"ShapeComponentConstraint"および"ShapeConstraint"構造内で確認できます。

![四角形がこの画面で見つかった](images/su-shapequery-300px.jpg)<br>
*四角形がこの画面で見つかった*

### <a name="object-placement-solver"></a>オブジェクト配置のソルバー

オブジェクトの配置を対象としてプログラムは、オブジェクトを配置する物理的な部屋に理想的な場所を識別するために使用できます。 オブジェクトの規則と制約を指定した位置に最適なソルバーが見つかります。 さらに、オブジェクト クエリは、"Solver_RemoveObject"により、オブジェクトが削除されますか、複数のオブジェクトの配置の制約付き"Solver_RemoveAllObjects"呼び出しを許可するまで保持されます。 オブジェクト配置のクエリは、3 つの部分で構成されています: パラメーター、一連の規則、制約のリストと配置の種類。 クエリを実行するには、次の API を使用します。

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

この関数は、オブジェクトの名前、配置の定義と規則と制約の一覧を受け取ります。 C#ラッパーは構築の規則と制約の構築を簡単にヘルパー関数を提供します。 配置の定義には、次の 1 つは、クエリの種類 – が含まれています。

```cpp
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

パラメーターの型に固有の各配置の種類があります。 "ObjectPlacementDefinition"構造体には、これらの定義を作成するための静的なヘルパー関数のセットが含まれています。 たとえば、床の上にオブジェクトを配置する場所を検索するには、次の関数を使用できます。 パブリック静的 ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) でさらに、配置の種類を一連の規則と制約を行うことができます。 規則に違反することはできません。 型とルールに適合するような配置場所は、最適な配置場所を選択するには、一連の制約に対して最適化されています。 指定された静的作成関数によって各規則と制約を作成できます。 規則と制約の構築関数の例を以下に示します。

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

オブジェクトの下の配置のクエリは、画面の端に半分メーター キューブを配置から他のオブジェクトを配置前およびルームの中央の近くの場所を確保検索します。

```cs
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

成功した場合、配置の位置を含む"ObjectPlacementResult"構造体のサイズや方向が返されます。 さらに、配置は、配置されたオブジェクトの dll の内部一覧に追加されます。 後続の配置のクエリ アカウントにこのオブジェクトになります。 Unity のサンプルでは、"LevelSolver.cs"ファイルより多くの例のクエリが含まれています。

![オブジェクトの配置の結果](images/su-objectplacement-1000px.jpg)<br>
*図 3:青いボックスでカメラの位置の規則から床の上の 3 つの場所からの結果のクエリ*

レベルまたはアプリケーションのシナリオに必要な複数のオブジェクトの配置場所を解決するときに最初に、領域に含まれる確率を最大化するための順序で欠かせないと大きなオブジェクトを解決します。 配置の順序が重要です。 オブジェクトへの配置が見つからない場合は、あまりに制約付きの構成をお試しください。 フォールバック構成のセットは、ルーム構成で多くの機能をサポートしているに不可欠です。

### <a name="room-scanning-process"></a>ルームのスキャン プロセス

あらゆる問題領域のニーズを満たすのに十分なジェネリック、HoloLens によって提供される空間マッピング ソリューションを設計中に、空間理解モジュールは、2 つの特定のゲームのニーズをサポートするために構築されました。 そのソリューションは、特定のプロセスと前提条件、以下の集計のセットを中心に構成されます。

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

ユーザー駆動 playspace「描画」– スキャン フェーズでは、ユーザーが移動し、ペースの再生に関する次の必要があります領域を効果的に描画します。 生成したメッシュは、このフェーズ中にユーザーからのフィードバックを提供する必要があります。 屋内ホームまたは office セットアップ – 関数がフラット サーフェスと直角に交わって壁を中心に設計されたクエリ。 これは、ソフト制限です。 ただし、スキャン フェーズでは、プライマリ軸の分析がメジャーおよびマイナーの軸に沿ったメッシュ テセレーションを最適化するために完了します。 インクルード SpatialUnderstanding.cs ファイルは、スキャン フェーズの処理を管理します。 次の関数を呼び出します。

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

"SpatialUnderstanding"動作によって、スキャンのフローは、各フレーム InitScan、し UpdateScan を呼び出します。 統計情報のクエリが妥当なカバレッジを報告したとき、ユーザーは、スキャン フェーズの終了を示す RequestFinish を呼び出す airtap にできます。 UpdateScan の継続が戻り値になるまでに呼び出される値は、dll の処理が完了したことを示します。

### <a name="understanding-mesh"></a>Understanding メッシュ

Understanding dll は、サイズ 8 cm voxel キューブのグリッドとして、playspace を内部的に格納します。 スキャンの初期段階では、部屋の軸を決定する主要なコンポーネントの分析が完了しました。 内部的には、これらの軸に配置されたその voxel 領域を格納します。 メッシュには、voxel ボリュームからアイソサーフェスを抽出することによって毎秒約が生成されます。 

![Voxel ボリュームから生成したメッシュが生成されます。](images/su-custommesh.jpg)<br>
*Voxel ボリュームから生成したメッシュが生成されます。*

## <a name="troubleshooting"></a>トラブルシューティング
* 設定することを確認、 [SpatialPerception](#setting-the-spatialperception-capability)機能
* 追跡が失われると、次の OnSurfaceChanged イベントはすべてのメッシュを削除します。

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Mixed Reality toolkit 空間マッピング
空間マッピングを使用して、Mixed Reality Toolkit v2 での詳細については、次を参照してください。、<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">空間認識セクション</a>MRTK docs の。

## <a name="see-also"></a>関連項目
* [MR 空間 230:空間マッピング](holograms-230.md)
* [座標系](coordinate-systems.md)
* [Unity の座標系](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>
