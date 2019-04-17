---
title: DirectX の座標系
description: Windows Mixed Reality 空間ロケーター、参照フレーム、空間的なアンカーは、座標系を使用する方法、SpatialStage を使用する方法、追跡の損失を処理する方法、保存し、表現のアンカーを読み込む方法、および画像安定化する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 空間ロケーター、空間参照フレーム、空間座標系、空間ステージでは、実際には、混合コード、イメージの安定化、空間アンカー、空間アンカー ストア、追跡の損失、チュートリアルをサンプルします。
ms.openlocfilehash: c8cdb39cbf4634edb4ed0a595381fc70f1388ce4
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605151"
---
# <a name="coordinate-systems-in-directx"></a>DirectX の座標系

[座標系](coordinate-systems.md)空間については、Windows Mixed Reality Api によって提供されるは、基礎を形成します。

今日の取り付け VR または、単一ルーム VR デバイスは、追跡対象のスペースを表す 1 つのプライマリ座標システムを確立します。 Windows Mixed Reality デバイスなど、HoloLens が定義されていない大規模な環境で使用するために設計されたデバイスを検出して、ユーザーとしてその周囲のものについて学習について説明しますの周り。 これにより、継続的に向上に合わせて、デバイス、ユーザーのルームが互いに、アプリの有効期間の関係を変更する座標システムでの結果に関する知識。 Windows Mixed Reality は、幅広いデバイス、イマーシブ ヘッドセットが取り付けられていないから世界に接続された参照フレームまでをサポートします。

>[!NOTE]
>この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。  概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。

## <a name="spatial-coordinate-systems-in-windows"></a>Windows では、空間座標系

Windows では、実際の座標系を判断するために使用する主要なタイプは、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>します。 この型のインスタンスは、任意の座標系を表し、それぞれの詳細を理解することがなく 2 つの座標システム間で変換に使用できる変換行列を取得するメソッドを提供します。

ポイント、線などで、またはユーザーの環境でボリュームとして表される空間の情報を返すメソッドが返されるこれらの座標に最も役立つ座標系を決定できるように SpatialCoordinateSystem パラメーターを受け入れます。 これらの座標の単位がメートル単位で常になります。

SpatialCoordinateSystem には、デバイスの位置を表すものも含め、他の座標システムと動的な関係があります。 任意の時点で、デバイスは一部の座標システムなどを検索することにあります。 ほとんどの座標システムでは、アプリを配置できません期間を処理できる必要があります。

アプリケーションを作成しないでください SpatialCoordinateSystems 直接 - ではなく認識 Api を使用して使用する必要があります。 認識 Api で座標システムの 3 つのプライマリ ソースがあるで説明されている概念へのマップの各、[座標系](coordinate-systems.md)ページ。
* 静止した基準枠を取得するには、作成、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a>現在から 1 つを取得または<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>します。
* 空間のアンカーを取得するには、作成、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>します。
* 添付のフレームの参照を取得するには、作成、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>します。

これらのオブジェクトによって返される座標システムのすべてが右利きで、+ 右に、+ x、y と + z 内を後方に向かってします。 方向正の x 方向の左側または右側のいずれかの本の指をポイントし、それらを正の y 方向に curling の正の z 軸点に注意することができます。 親指が指している方向は、自身に向かうかまたは離れる方向のいずれかとなり、その座標系の z 軸の正の向きが指す方向となります。 次の図は、これらの 2 つの座標系を示しています。

![左辺と右辺座標系](images/left-hand-right-hand.gif)<br>
*左辺と右辺座標系*

HoloLens の位置に基づいて SpatialCoordinateSystem にブートス トラップを使用して、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>以下のセクションで説明されているか、添付または静止フレームの参照を作成するクラス。

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>空間のステージを使用して、世界中の配置ホログラム

Windows Mixed Reality イマーシブ ヘッドセットを非透過の座標系は、静的なを使用してアクセス<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a>プロパティ。 この API には、座標系、については、プレーヤーが取り付けられているかどうかについてや、モバイル、安全な領域の境界の場合は、プレーヤーは、モバイル、歩き回るとかどうかを示す値、ヘッドセットは方向。 空間のステージに更新プログラムのイベント ハンドラーもあります。

最初に、空間のステージを取得し、更新プログラムの定期受信します。 

コードを**空間ステージの初期化**

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

OnCurrentChanged メソッドでは、アプリは空間段階の検査し、プレーヤーのエクスペリエンスを適宜更新する必要があります。 この例では、ユーザーとビューのステージの範囲と移動プロパティの範囲で指定された開始位置と同様に、ステージの境界の視覚エフェクトを提供します。 私たちも場合にフォールバック独自静止座標系ステージを指定することはできません。


コードを**空間段階の更新**

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

時計回りの頂点のステージの境界を定義するセットが提供されます。 Windows Mixed Reality シェルでは、ユーザーがそれに近づくと、境界にフェンスを描画します。ウォークの領域を目的に合わせて triangularize たい場合があります。 Triangularize ステージには、次のアルゴリズムを使用できます。


コードを**空間ステージ triangularization**

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>静止した基準枠を使用して、世界中の配置ホログラム

[SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx)クラスのフレームを表しますが参照する[静止](coordinate-systems.md#stationary-frame-of-reference)周りを基準として、ユーザー、ユーザーの環境と移動します。 このフレームの参照では、デバイスの近くに安定したままの状態の座標で優先されます。 ホログラムを表示するときに、レンダリング エンジン内で基になるワールド座標系として機能すること、SpatialStationaryFrameOfReference の 1 つのキーの使用です。

SpatialStationaryFrameOfReference を取得する、 [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx)クラスと呼び出し[CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx)します。

Windows Holographic のアプリのテンプレート コード: から

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* 静止した基準枠は、領域全体の基準とした最適位置を提供する設計されています。 その参照フレーム内の個々 の位置は、ユーザーが少しのずれが許可されます。 これは、普通は、デバイスは環境についての詳細を学習します。
* ホログラムの個々 の正確な配置が必要な場合、SpatialAnchor を使用して、個々 のホログラム現実の世界での位置に固定する必要がある-たとえば、ポイントをユーザーことを示します特別な関心のあります。 アンカーの位置はないユーザーずれが修正できます。アンカー以降、次のフレームでは、修正が行われた後修正された位置が使用されます。

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>空間のアンカーを使用して、世界中の配置ホログラム

[空間アンカー](coordinate-systems.md#spatial-anchors)ホログラムを現実の世界での特定の場所に配置する優れた方法は、システム アンカーのことを確認する時間の経過と共にのままにします。 このトピックでは、アンカーのデータを操作する方法と作成して、アンカーを使用する方法について説明します。

任意の位置と、選択、SpatialCoordinateSystem 内向き、SpatialAnchor を作成できます。 デバイスは、現時点では、その座標系を検索できる必要があり、システムが空間アンカーの制限に達しましたのないでする必要がありますがします。

定義した後、SpatialAnchor の座標系は、正確な位置と向きの初期位置を保持する継続的に調整します。 この SpatialAnchor は、その正確な場所で、ユーザーの環境に固定表示されるホログラムを表示するために使用できます。

アンカーを維持する調整の効果を拡大するには、アンカーが増加からの距離として。 そのため、そのアンカーの配信元から複数の約 3 メートル アンカーの基準とした内容の表示を避ける必要があります。

[CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx)プロパティが、デバイス、アンカーの正確な場所を調整するときに適用されるイージングを使用する、アンカー ポイントからコンテンツを配置することができます、座標系を取得します。

使用して、 [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx)プロパティと、対応する[RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx)自分でこれらの調整を管理するイベントです。

### <a name="persist-and-share-spatial-anchors"></a>保存や共有空間アンカー

使用してローカル SpatialAnchor を永続化できる、 [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)クラスし、同じ HoloLens デバイスに将来のアプリのセッションに戻りを取得します。

使用して<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>から、ローカルな SpatialAnchor は、アプリが複数の HoloLens、iOS や Android デバイスで見つけることができますし、持続性のあるクラウド アンカーを作成できます。  各ユーザーは複数のデバイスで共通の空間アンカーを共有することで、同じ物理的な場所でそのアンカーの基準としたコンテンツを表示できます。  これにより、リアルタイムのエクスペリエンスを共有します。

使用することも<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a> HoloLens、iOS および Android デバイスの間で非同期ホログラム永続化します。  持続性のあるクラウド空間アンカーを共有することで複数のデバイスはこれらのデバイスがまとめてと同時に存在しない場合でも、時間の経過と共に同じ永続化されたホログラムを確認できます。

5 分間試して、HoloLens のアプリで共有のエクスペリエンスの構築を開始する、<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">空間アンカー HoloLens の Azure クイック スタート</a>します。

空間のアンカーを Azure で稼働しているを開発したとして、<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">を作成し、HoloLens でアンカーを見つける</a>します。  チュートリアルに利用<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android および iOS</a>同様に、すべてのデバイスで同じアンカーを共有できるようにすることです。

### <a name="create-spatialanchors-for-holographic-content"></a>SpatialAnchors を holographic のコンテンツを作成します。

このコード サンプルでは、変更後の Windows Holographic アプリ テンプレートの作成に固定する場合に、 **Pressed**ジェスチャが検出されました。 キューブは、レンダリング パス中に、アンカーに格納されます。

ヘルパー クラスでは、複数のアンカーがサポートされている、このコード サンプルを使用すると同数のキューブを配置できます。

アンカーの Id は、何か、アプリを制御することに注意してください。 この例では順次アンカーのアプリのコレクションに格納されているアンカーの数に基づく名前付けスキームを作成しました。

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>非同期的に読み込まれ、SpatialAnchorStore をキャッシュします。

この永続化、処理に役立つ SampleSpatialAnchorHelper クラスを作成する方法について説明を含みます。
* Platform::string キーによってインデックスが作成、メモリ内表現のアンカーのコレクションを格納します。
* アンカーは、システムの SpatialAnchorStore から読み込み、これは分離されますローカル メモリ内コレクションから。
* そのためには、アプリが選択したときに、SpatialAnchorStore にアンカーのローカル メモリ内コレクションを保存しています。

保存する方法を次に示します[SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)内のオブジェクト、 [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)します。

クラスは、起動時に、SpatialAnchorStore を非同期的に要求します。 システム I/O API は、アンカー ストアを読み込むし、I/O は非ブロッキングようにこの API は非同期されるようになります。

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

アンカーの保存に使用できる SpatialAnchorStore が与えられます。 これは、IMapView を関連付ける SpatialAnchors いるデータ値では文字列であるキーの値です。 サンプル コードで保存すれば、ヘルパー クラスのパブリック関数を通じてアクセスできるプライベート クラス メンバー変数にします。

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>忘れずに保存および読み込みアンカー ストア保留/再開イベントをフックします。

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>コンテンツをアンカー ストアに保存します。

システムでは、アプリが中断、ときに、空間、アンカーをアンカー ストアに保存する必要があります。 アプリの実装に必要であることを検索するには、アンカーのストアにその他の時間は、アンカーを保存することもできます。

SpatialAnchorStore をメモリ内のアンカーを保存してください準備ができたらは、コレクションをループ処理し、それぞれを保存しようとしています。

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>アンカー ストアからアプリを再開したときにコンテンツを読み込む

アプリの再開時、または implementaiton のアプリのために必要な他の任意の時点で、アンカー ストアの IMapView から SpatialAnchors の独自のメモリ内データベースに転送することによって、AnchorStore に以前に保存されたアンカーを戻すことができます。

SpatialAnchorStore から表現のアンカーを復元するには、互いをメモリ内コレクションに興味があるを復元します。

SpatialAnchors; の独自のメモリ内データベースを作成する必要があります。何らかの方法に文字列を作成する SpatialAnchors に関連付けます。 サンプル コードで選択、Windows::Foundation::Collections::IMap を使用して、アンカーを格納するしやすく、SpatialAnchorStore に同じキーとデータの値を使用します。

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>復元されるアンカーできない可能性があります場所を特定できるでしょうか。 たとえば、別の部屋にまたは、別の構築に完全にアンカーがあります。 使用する前に locatability、AnchorStore から取得したアンカーをテストする必要があります。

<br>

>[!NOTE]
>このコード例では、AnchorStore からすべてのアンカーを取得します。 これは要件ではありません。アプリと同様を選択アンカーの特定のサブセットを実装に意味のある文字列キー値を使用しています。

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>必要なときに、アンカー ストアをクリアします。

場合によっては、アプリの状態をオフにして新しいデータを書き込む必要があります。 その方法を次に示します、 [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)します。

ヘルパー クラスを使用する必要はありませんほぼをラップする関数をクリアします。 このヘルパー クラスが SpatialAnchorStore インスタンスを所有しているの役割を与えられているため、サンプルの実装では、そのために選択します。

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>以下に例を示します。アンカーの座標系に関連する静止した基準枠座標系

たとえば、アンカーがあり、その大部分の他のコンテンツを既に使用している SpatialStationaryReferenceFrame に関連するアンカーの座標システムで何かにするとします。 使用することができます[TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx)静止した基準枠のアンカーの座標系から変換を取得します。

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

このプロセスは、2 つの方法に便利です。
1. 2 つのフレームを参照する場合、相互に関連した認識できるように指示し、;
2. そのためが提供されている場合にもう 1 つの座標システムから直接移動する変換。

この情報は、2 つの参照フレーム間でオブジェクトの空間関係の理解しています。

レンダリングには、元の参照フレームまたはアンカーに従ってオブジェクトをグループ化して多くの場合より良い結果を取得できます。 グループごとに別個の描画パスを実行します。 View 行列は、最初に同一の座標系を使用して作成されるモデルの変換でオブジェクトをより正確なです。

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>デバイス接続の参照を使用してホログラムを作成します。

ホログラムを表示するために必要な場合があるを[がアタッチされたまま](coordinate-systems.md#attached-frame-of-reference)デバイスの場所、デバイスがその向きを決定することのみのときに、情報メッセージまたは情報メッセージをデバッグなどのパネルに、いない領域の位置。 これを行うには、接続されている基準を使用します。

SpatialLocatorAttachedFrameOfReference クラスは、現実世界ではなく、デバイスに対して相対的である座標系を定義します。 このフレームは、方向、ユーザーのポイントは、参照フレームが作成されたときに直面していましたが、ユーザーの環境の基準とした固定の見出しが。 このフレームのリファレンス内のすべての向きは、ユーザー、デバイスを回転しても、その固定の見出しを基準とは。

HoloLens、このフレームの座標系の原点は配置されているユーザーの頭の回転の中心に回転、ヘッドの位置が受けないようにします。 アプリには、このポイント ホログラムも、ユーザーの位置を基準としたオフセットを指定できます。

SpatialLocatorAttachedFrameOfReference を取得するには、SpatialLocator クラスを使用し、CreateAttachedFrameOfReferenceAtCurrentHeading を呼び出します。

これが全体の範囲の Windows Mixed Reality デバイスに適用されることに注意してください。

### <a name="use-a-reference-frame-attached-to-the-device"></a>デバイスに接続されている参照フレームを使用して、

これらのセクションでは、この API を使用してデバイスに接続されたフレームの参照を有効にする、Windows Holographic のアプリケーション テンプレートで変更点について説明します。 この「添付」ホログラムが固定または固定のホログラムに連動し、デバイスは、世界中でその位置を検索する一時的にできない場合にも使用される可能性がありますに注意してください。

最初に、SpatialStationaryFrameOfReference ではなく、SpatialLocatorAttachedFrameOfReference を格納するテンプレートを変更します。

**HolographicTagAlongSampleMain.h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

**HolographicTagAlongSampleMain.cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

更新中に今すぐフレーム予測使用から取得されたタイムスタンプの座標系を取得します。

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>空間ポインター姿勢を取得し、次のユーザーの視線入力

ユーザーのフォローを例ホログラムする[視線](gaze.md)と同様に、holographic シェルが、ユーザーの視線の先に従います。 これは、同じタイムスタンプから、SpatialPointerPose を取得する必要があります。

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

この SpatialPointerPose がに従ってホログラムを配置するための情報、[ユーザーの現在の針路](gaze,-gestures,-and-motion-controllers-in-directx.md)します。

快適性の理由から、時間の期間にわたって実行されるように、位置の変更を滑らかにするのに線形補間 ("lerp") を使用します。 これは、視線の先にホログラムのロックよりも、ユーザーに快適です。 Lerping tag-along ホログラムの位置では移動; をダンプしてホログラムを安定化することもできます。このダンプ私たちは、ユーザーに通常とは、ユーザーの頭の見えない動きと見なされますためジッター ホログラムと表示されます。

**StationaryQuadRenderer::PositionHologram**:

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>デバッグのパネルの場合、ビューが隠されることができるように、少し側にオフ ホログラム位置を変更することもできます。 次を行う方法の例に示します。

**StationaryQuadRenderer::PositionHologram**:

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>カメラに直面するホログラムを回転させる

単にクワッド; をこの例では、ホログラムを配置するには不十分です。ユーザーが直面するオブジェクトを回転する必要がありますもできます。 ビルボード処理のこの型では、ユーザーの環境の一部を維持するホログラムのため、ワールド空間で回転が発生することに注意してください。 ビュー空間ビルボード処理やわらげるできないためはホログラムが画面の向きをロックその場合は、ステレオのレンダリングが妨害しないビュー空間ビルボードのトランス フォームを取得するには左右の view 行列間を補間も必要があります。 ここでは、ユーザーが直面する X、Z 軸に回転させます。

**StationaryQuadRenderer::Update**:

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>アタッチされたホログラムをレンダリングします。

この例では、ホログラムを配置する場所は、SpatialLocatorAttachedReferenceFrame の座標システムでホログラムを表示するために選択もできます。 (別の座標系を使用して表示することにしましたが場合は、必要がありますをその座標系をデバイスに接続された参照フレームの座標システムからの変換を取得します。)

**HolographicTagAlongSampleMain::Render**:

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

以上で作業は終了です。 ホログラムはようになりました「追跡」ユーザーの視線入力方向の前に 2 つのメーターの位置。

>[!NOTE]
>この例は、またその他のコンテンツを読み込みます - StationaryQuadRenderer.cpp を参照してください。

## <a name="handling-tracking-loss"></a>処理の追跡が失われる

デバイスは、世界で自体を見つけられない、アプリで"追跡損失"が発生します。 Windows Mixed Reality アプリでは、位置指定の追跡システムには、このような中断を処理できる必要があります。 これらの中断が見られることと既定 SpatialLocator LocatabilityChanged イベントを使用して、応答を作成します。

**AppMain::SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

アプリが LocatabilityChanged イベントを受け取るときに、必要に応じて、動作を変更できます。 など PositionalTrackingInhibited 状態でアプリは通常の操作を一時停止し、レンダリング、 [tag-along ホログラム](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference)警告メッセージを表示します。

Windows Holographic のアプリ テンプレートが付属 LocatabilityChanged ハンドラーが既に自動的に作成します。 既定では、その警告が表示されます、デバッグ コンソールで位置指定の追跡が使用できない場合。 必要に応じて、アプリからの応答を提供するには、このハンドラーにコードを追加することができます。

**AppMain.cpp:**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>空間マッピング

[空間マッピング](spatial-mapping-in-directx.md)Api を使用する画面のメッシュのモデルの変換を取得する座標系を使用します。

## <a name="see-also"></a>関連項目
* [座標系](coordinate-systems.md)
* [空間のアンカー](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure の空間アンカー</a>
* [視線、ジェスチャ、および DirectX でモーション コント ローラー](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [DirectX での空間のマッピング](spatial-mapping-in-directx.md)
