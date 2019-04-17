---
title: DirectX での空間のマッピング
description: DirectX アプリで空間マッピングを実装する方法について説明します。 これには、ユニバーサル Windows プラットフォーム SDK に含まれている空間マッピングのサンプル アプリケーションの詳細な説明が含まれます。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: 実際には、空間マッピング、環境、相互作用、directx、winrt、api、サンプルのコードを混在 Windows UWP, SDK, チュートリアル
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605138"
---
# <a name="spatial-mapping-in-directx"></a>DirectX での空間のマッピング

このトピックでは、実装する方法を説明します[空間マッピング](spatial-mapping.md)DirectX アプリでします。 これには、ユニバーサル Windows プラットフォーム SDK に含まれている空間マッピングのサンプル アプリケーションの詳細な説明が含まれます。

このトピックではコードを使用、 [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP のコード サンプル。

>[!NOTE]
>この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。  概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。

## <a name="directx-development-overview"></a>DirectX の開発の概要

空間マッピング用のネイティブ アプリケーションの開発は、Api を使用して、 [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)名前空間。 これらの Api は空間マッピングによって公開される Api を直接と同様の方法では、空間マッピング機能のフル コントロールを提供[Unity](spatial-mapping-in-unity.md)します。

### <a name="perception-apis"></a>認識 Api

空間マッピングの開発用の主な種類は次のとおりです。
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) SpatialSurfaceInfo オブジェクトの形式で、ユーザーの近くの領域のアプリケーションで指定されたリージョンでの画面について説明します。
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)単一既存空間のサーフェス、一意の ID を含む、境界のボリュームと最終変更時刻をについて説明します。 要求時に非同期的の SpatialSurfaceMesh が提供されます。
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) SpatialSurfaceInfo から要求された SpatialSurfaceMesh オブジェクトのカスタマイズに使用されるパラメーターが含まれています。
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)メッシュ データを 1 つの空間サーフェスを表します。 頂点の位置、頂点の法線と三角形のインデックスのデータは、メンバー SpatialSurfaceMeshBuffer オブジェクトに含まれます。
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx)メッシュのデータの 1 つの型をラップします。

これらの Api を使用してアプリケーションを開発する場合は、(以下で説明するサンプル アプリケーションで説明します)、このよう基本的なプログラム フローが表示されます。
- **設定する、SpatialSurfaceObserver**
  - 呼び出す[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)ユーザーがデバイスの空間のマッピング機能を使用するアプリケーションのアクセス許可を割り当てられているようにしてください。
  - SpatialSurfaceObserver オブジェクトをインスタンス化します。
  - 呼び出す[SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx)空間サーフェスに関する情報を挿入するスペースの領域を指定します。 もう一度この関数を呼び出すだけで、将来これらのリージョンを変更することがあります。 使用して各リージョンを指定する[SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)します。
  - 登録、 [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx)イベントで、新しい情報が指定した領域のリージョン内の空間のサーフェスについて利用可能なときに起動されます。
- **ObservedSurfacesChanged イベントを処理します。**
  - イベント ハンドラーで呼び出す[GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) SpatialSurfaceInfo オブジェクトのマップを受信します。 このマップを使用して、空間サーフェスのレコードを更新することができます[、ユーザーの環境に存在](spatial-mapping.md#mesh-caching)します。
  - 照会することがあります、SpatialSurfaceInfo オブジェクトごとに[TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx)で表される、サーフェイス上の空間のエクステントを判断する、[空間座標系](coordinate-systems.md)独自の。
  - 空間画面用のメッシュを要求する場合は、呼び出す[TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)します。 三角形の目的、密度とメッシュが返されるデータの形式を指定するオプションを指定することがあります。
- **受信および処理メッシュ**
  - TryComputeLatestMeshAsync は aysnchronously に対する各呼び出しは、1 つの SpatialSurfaceMesh オブジェクトを返します。
  - このオブジェクトから三角形のインデックス、頂点の位置にアクセスするには含まれている SpatialSurfaceMeshBuffer オブジェクトにアクセスすることができます (要求) 場合、メッシュの頂点の法線。 このデータは直接互換性のある形式になります、 [direct3d11 の Api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx)メッシュの描画に使用します。
  - ここから、アプリケーションは必要に応じて分析を実行または[処理](spatial-mapping.md#mesh-processing)メッシュのデータの使用と[レンダリング](spatial-mapping.md#rendering)と物理法則[レイキャストと衝突](spatial-mapping.md#raycasting-and-collision)。
  - 注意する 1 つの重要な詳細は、(たとえば、メッシュをレンダリングするために使用される頂点シェーダー) にメッシュの頂点の位置に、スケールを適用する必要があります、それらが格納されている、バッファー内に最適化された整数単位からそれらを変換するための新旧従量課金のことです。 このスケールを取得するには呼び出すことによって[VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)します。

### <a name="troubleshooting"></a>トラブルシューティング
* によって返されるスケールを使用して、頂点シェーダーでメッシュの頂点の位置をスケールすることを忘れないでください[SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>空間マッピングのコード サンプルのチュートリアル

[Holographic 空間マッピング](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)コード サンプルには、管理するためのインフラストラクチャを含む、アプリへの表面メッシュの読み込みを開始する際し、レンダリング サーフェイス メッシュ コードが含まれています。

次に、DirectX アプリに画面のマップ機能を追加する手順について説明します。 このコードを追加することができます、[アプリ テンプレートを Windows Holographic](creating-a-holographic-directx-project.md)上記で説明したコード サンプルを参照して、プロジェクト、またはするに従うことができます。 このコード サンプルは、Windows Holographic のアプリ テンプレートに基づきます。

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>SpatialPerception 機能を使用するアプリをセットアップします。

アプリは、空間のマッピング機能を使用できる必要があります。 これは、機能は、空間メッシュ プライベート データを検討できるユーザーの環境の表現であるため、必要です。 アプリの package.appxmanifest ファイルでこの機能を宣言します。 次に例を示します。

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

機能に由来します**uap2**名前空間。 マニフェストでこの名前空間へのアクセスを取得するには、それを含める、 *xlmns*属性、&lt;パッケージ > 要素。 次に例を示します。

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>空間マッピング機能のサポートを確認します。

Windows Mixed Reality は、さまざまな空間マッピングがサポートされていないデバイスを含め、デバイスをサポートします。 アプリは、空間のマッピングを使用することができますまたは機能を提供する空間のマッピングを使用する必要があります、これを使用する前に、空間マッピングがサポートされているかどうかを確認ください。 たとえば、空間マッピングは、mixed reality アプリで必要な場合メッセージが表示、それに対応するユーザーは、空間のマッピングがないデバイスで実行しようとするとします。 または、アプリがユーザーの環境では、空間マッピングが使用可能な場合に何が起こるようなエクスペリエンスを提供する代わりに、独自の仮想環境を表示することができます。 いずれの場合も、この API といない空間マッピング データを取得し、適切な方法で応答を認識するため、アプリを使用できます。

空間マッピング サポートを現在のデバイスを確認するには、最初に、UWP のコントラクトは、4 以上のレベルで確認してから SpatialSurfaceObserver::IsSupported() を呼び出します。 コンテキストで実行するには、 [Holographic 空間マッピング](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)コード サンプル。 サポートは、アクセスを要求する前にチェックされます。

SpatialSurfaceObserver::IsSupported() API では、SDK バージョン 15063 以降で使用できます。 必要に応じて、この API を使用する前にプラットフォームのバージョン 15063 プロジェクトの再ターゲットします。

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

ある UWP コントラクトがレベル 4 より小さい場合は、アプリを続行する、デバイスは空間マッピング処理を実行できるように注意してください。

### <a name="request-access-to-spatial-mapping-data"></a>空間マッピング データへのアクセスを要求します。

アプリは、任意の画面のオブザーバーを作成する前に、空間マッピングのデータにアクセスする許可を要求する必要があります。 詳細については後でこのページで提供されると、画面のマッピング コード サンプルに基づく例を次に示します。

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a>画面のオブザーバーを作成します。

**Windows::Perception::Spatial::Surfaces**名前空間が含まれています、 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)クラスで指定した 1 つまたは複数のボリュームの監視、 [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)します。 使用して、 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)なる表面メッシュをリアルタイムでデータにアクセスするインスタンス。

**AppMain.h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

前述の前のセクションは、アプリで使用できる前に、空間マッピング データへのアクセスを要求する必要があります。 このアクセスは、HoloLens で自動的に付与されます。

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

次に、境界の特定のボリュームを観察する表面のオブザーバーを構成する必要があります。 ここでは、20 x 20 x 5 メーター、座標系の原点を中心とするボックスを確認します。

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

複数の外接するボリュームを代わりに設定できることに注意してください。

*これは、擬似コードです。*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

ビューの視錐台などの他の外接する図形を使用することもまたはは軸ではない境界ボックスが配置されます。

*これは、擬似コードです。*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

場合に応答するコードを記述することができますが異なる方法で何も行うサーフェスのマッピング データが利用できない場合、アプリが必要な場合で、 [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx)でない**許可**- たとえば、できなく Pc で没入型のデバイスをそれらのデバイスは空間マッピングのハードウェアがあるないため、接続されているとします。 これらのデバイスの代わりに、空間ステージについては、ユーザーの環境とデバイスの構成に依存する必要があります。

### <a name="initialize-and-update-the-surface-mesh-collection"></a>初期化し、なる表面メッシュ コレクションの更新

Surface のオブザーバーが正常に作成すると場合、は、表面メッシュ コレクションを初期化するために進むことができます。 ここでは、監視対象のサーフェスの現在のセットをすぐに取得するのに、プル モデルの API を使用します。

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

表面メッシュのデータの取得に使用可能なプッシュ モデルもあります。 自由にアプリを設計する場合をポーリングするデータを頻繁に、選択した場合、プル モデルのみを使用すると答えると、または特定の期間中に、フレームごとに 1 回など、ゲームのセットアップ中にします。 そうである場合、上記のコードは必要なものには。

コード サンプルでは、教育目的では、両方のモデルの使用を示すために選択しました。 ここでは、システムは、変更を認識するたびに、表面メッシュを最新の状態データを受信するイベントに定期受信します。

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

コード サンプルは、これらのイベントに応答することも構成されます。 その方法を見てみましょう。

**注:** これによって、メッシュのデータを処理するアプリの最も効率的な方法ができない可能性があります。 このコードでは、わかりやすくするためが書き込まれ、最適化されていません。

読み取り専用マップを格納する表面メッシュのデータが提供される[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)オブジェクトを使用して[Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx)キー値として。

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

このデータを処理するには、コレクション内ではないキー値の最初の項目について説明します。 このサンプル アプリでデータを格納する方法の詳細については、このトピックの「表示されます。

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

また、表面メッシュ、表面メッシュ コレクション内にあるが、今後のシステム コレクションにないを削除する必要があります。 これを行うにはここで紹介を追加すると、メッシュ; の更新の反対のようなもの必要があります。アプリのコレクションを確認する場合にループ処理、 **Guid**があるがシステム コレクション内にします。 システム コレクションにない場合は都合から削除します。

AppMain.cpp でイベント ハンドラー: から

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

RealtimeSurfaceMeshRenderer.cpp でメッシュの排除の実装:

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>取得し、なる表面メッシュ データ バッファーの使用

表面メッシュ情報を取得することは、データ コレクションを取得し、そのコレクションの更新の処理と同じくらい簡単でした。 ここで詳しく説明します詳細データを使用する方法。

このコード例では、レンダリングの表面メッシュを使用する選択しました。 これは、現実世界のサーフェスの背後にあるホログラムが他の一般的なシナリオです。 メッシュをレンダリングまたは処理されたバージョンを表示できますが、ルームがのどの領域をユーザーに表示するアプリやゲームの機能の提供を開始する前にスキャンされます。

コード サンプルは、前のセクションで説明したイベント ハンドラーからなる表面メッシュの更新プログラムを受信したときに、プロセスを開始します。 この関数のコードの重要な行は、サーフェイスを更新する呼び出し*メッシュ*: この時点までが既に処理されたメッシュの情報とに応じて、使用するため、頂点とインデックスのデータを取得しようとしています。

RealtimeSurfaceMeshRenderer.cpp: から

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

サンプル コードが設計されていますように、データ クラス**SurfaceMesh**、ハンドル メッシュのデータ処理および表示します。 これらのメッシュはどのような**RealtimeSurfaceMeshRenderer**のマップを実際に保持します。 1 つずつは送信元 SpatialSurfaceMesh への参照を備え、メッシュの頂点またはインデックス バッファーにアクセスしたり、メッシュの変換を取得する必要がある任意の時間を使用します。 ここで、更新プログラムを必要とすると、メッシュをフラグです。

SurfaceMesh.cpp: から

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

次回、メッシュが自身を描画するように求めは、フラグまず確認します。 更新プログラムが必要な場合は、GPU で頂点とインデックス バッファーが更新されます。

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

最初に、生データ バッファーを取得します。

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

次に、Direct3D デバイス バッファーを作成、HoloLens によって提供されるメッシュ データ。

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

**注:** 前のスニペットで使用される、CreateDirectXBuffer ヘルパー関数では、画面のマッピングのコード サンプルを参照してください。SurfaceMesh.cpp、GetDataFromIBuffer.h します。 これで、デバイス リソースの作成が完了して、メッシュが読み込まれ、更新プログラムの準備をして、表示すると見なされます。

### <a name="update-and-render-surface-meshes"></a>更新し、表面メッシュをレンダリングします。

SurfaceMesh クラスでは、特殊化された update 関数があります。 各[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)独自の変換を備え、サンプルの現在の座標系を使用する、 **SpatialStationaryReferenceFrame**変換を取得します。 GPU 上でモデルの定数バッファーを更新します。

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

表面メッシュをレンダリングするときは、ときに、コレクションを表示する前に、いくつかの準備作業を行います。 現在の表示構成のシェーダーのパイプラインを設定し、入力アセンブラー ステージを設定します。 なお、holographic カメラ ヘルパー クラス**CameraResources.cpp**  /ビューのプロジェクション定数バッファーをここまでで既に設定が。

**RealtimeSurfaceMeshRenderer::Render**:

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

これが完了すると、メッシュにループを自体を描画するために 1 つずつに伝えます。 **注:** 何らかの視錐台カリングを使用するこのサンプル コードが最適化されていないが、アプリでこの機能を含める必要があります。

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

個々 のメッシュは、頂点とインデックス バッファー、stride、およびモデル変換定数バッファーを設定します。 同様に、Windows Holographic のアプリケーション テンプレートで回転するキューブ、インスタンス化を使用してステレオスコ ピックのバッファーを表示します。

**SurfaceMesh::Draw**:

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a>画面のマッピングの選択肢を表示

画面のマッピングのコード サンプルには、表面メッシュのデータのレンダリングをオクルー ジョン専用となる表面メッシュのデータの表示が画面に表示されるコードが用意されています。 パスを選ぶかまたは両方がアプリケーションに依存します。 このドキュメントで両方の構成を説明します。

**Holographic 効果のレンダリング オクルー ジョン バッファー**

現在、仮想カメラのレンダー ターゲット ビューをオフにして開始します。

AppMain.cpp: から

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

これは、「プリレンダ リング」パスです。 ここでは、深さのみを表示するために、メッシュ レンダラーを要求することによって、オクルー ジョン バッファーを作成します。 この構成では、レンダー ターゲット ビューを接続せず、メッシュ レンダラーでは、ピクセル シェーダーのステージを設定**nullptr**ピクセルを描画するために、GPU をわざわざしないようにします。 ジオメトリを深度バッファーにラスタライズして、グラフィックス パイプラインの停止があります。

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

ホログラムとオクルー ジョンのマッピングの画面バッファーに対する追加の深度テスト描画できます。 このコード サンプルでレンダリング キューブ上のピクセルを別の色、画面の背面にある場合。

AppMain.cpp: から

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

SpecialEffectPixelShader.hlsl からコードに基づいています。

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

**注:** **GatherDepthLess**ルーチン、画面のマッピングのコード サンプルを参照してください。SpecialEffectPixelShader.hlsl します。

**表示になる表面メッシュ データのレンダリング**

表面メッシュだけでもステレオ表示バッファーに描画できます。 ライティング、完全な面を描画することにしましたが、自由ワイヤー フレームを描画、レンダリングの前にメッシュの処理、テクスチャ マップでは、適用および具合にします。

ここでは、コード サンプルは、コレクションを描画するために、メッシュ レンダラーを指示します。 この時間ピクセル シェーダーをアタッチし、現在の仮想のカメラの指定したターゲットを使用してレンダリング パイプラインを完了するため、深さのみのパスの場合を指定しますはありません。

```cpp
// SR mesh rendering pass: Draw SR mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>関連項目
* [Holographic DirectX プロジェクトを作成します。](creating-a-holographic-directx-project.md)
* [Windows.Perception.Spatial API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
