---
title: Unreal での空間マッピング
description: Unreal で空間マッピングを使用するためのガイド
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, 空間マッピング
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840081"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="94a29-104">Unreal での空間マッピング</span><span class="sxs-lookup"><span data-stu-id="94a29-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="94a29-105">HoloLens で空間マッピングを有効にするには、[プロジェクト設定] > [プラットフォーム] > [HoloLens] > [機能] の下にある Unreal エディターで、"空間認識" 機能を確実にオンにします。</span><span class="sxs-lookup"><span data-stu-id="94a29-105">To enable spatial mapping on HoloLens, ensure that the “Spatial Perception” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="94a29-106">HoloLens ゲームで空間マッピングの使用をオプトインするには、ARSessionConfig で [Generate Mesh Data from Tracked Geometry]\(追跡されたジオメトリからメッシュ データを生成する\) を有効にします。</span><span class="sxs-lookup"><span data-stu-id="94a29-106">To opt into using spatial mapping in a HoloLens game, enable the “Generate Mesh Data from Tracked Geometry” in the ARSessionConfig.</span></span>  <span data-ttu-id="94a29-107">これで、HoloLens プラグインが、空間マッピング データを非同期的に取得し、MRMesh を介してそのデータを Unreal に表示します。</span><span class="sxs-lookup"><span data-stu-id="94a29-107">The HoloLens plugin will then asynchronously get spatial mapping data and surface it to Unreal through the MRMesh.</span></span> 

![空間アンカー ストア準備完了](images/unreal-spatialmapping-arsettings.PNG)

<span data-ttu-id="94a29-109">空間マッピング メッシュのデバッグ視覚エフェクトを表示するには、ARSessionConfig の [Render Mesh Data in Wireframe]\(ワイヤーフレームでメッシュ データをレンダリングする\) チェックボックスをオンにして、MRMesh 内のすべての三角形の白いワイヤーフレームのアウトラインを表示します。</span><span class="sxs-lookup"><span data-stu-id="94a29-109">To see a debug visualization of the spatial mapping mesh, enable the “Render Mesh Data in Wireframe” checkbox in the ARSessionConfig to see a white wireframe outline of every triangle in the MRMesh.</span></span> 

<span data-ttu-id="94a29-110">[プロジェクト設定] > [プラットフォーム] > [HoloLens] > [空間マッピング] で、次のパラメーターを変更すると、空間マッピングの実行時の動作を更新できます。</span><span class="sxs-lookup"><span data-stu-id="94a29-110">In Project Settings > Platform > HoloLens > Spatial Mapping, the following parameters can be modified to update spatial mapping’s runtime behavior:</span></span> 

![空間アンカーのプロジェクト設定](images/unreal-spatialmapping-projectsettings.PNG)

<span data-ttu-id="94a29-112">[Max Triangles Per Cubic Meter]\(立方メートルあたりの最大三角形数\) で、空間マッピング メッシュの三角形の密度が更新されます。</span><span class="sxs-lookup"><span data-stu-id="94a29-112">Max Triangles Per Cubic Meter will update the density of the triangles in the spatial mapping mesh.</span></span>  <span data-ttu-id="94a29-113">[Spatial Meshing Volume Size]\(空間メッシュのボリューム サイズ\) は、空間マッピング データをレンダリングおよび更新するための、プレーヤー周りのキューブのサイズを示します。</span><span class="sxs-lookup"><span data-stu-id="94a29-113">Spatial Meshing Volume Size indicates the size of the cube around the player to render and update spatial mapping data.</span></span>  <span data-ttu-id="94a29-114">予想されるアプリケーションの実行時環境が大きくなると思われる場合は、このフィールドを現実世界のスペースに合わせて大きくしなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="94a29-114">If the expected application runtime environment is expected to be large, this field may need to be large to match the real-world space.</span></span>  <span data-ttu-id="94a29-115">逆に、アプリケーションでユーザーの周囲の表面にホログラムを配置するだけであれば、このフィールドを小さくすることができます。</span><span class="sxs-lookup"><span data-stu-id="94a29-115">Conversely, if the application only needs to place holograms on surfaces immediately around the user, this field can be smaller.</span></span>  <span data-ttu-id="94a29-116">ユーザーが移動するにつれて、空間マッピングのボリュームも移動します。</span><span class="sxs-lookup"><span data-stu-id="94a29-116">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

<span data-ttu-id="94a29-117">実行時に MRMesh にアクセスするには、最初に、ブループリント アクターに AR Trackable Notify コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="94a29-117">To get access to the MRMesh at runtime, first add an AR Trackable Notify Component to a Blueprint actor:</span></span> 

![空間アンカーの AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="94a29-119">次に、コンポーネントの詳細にアクセスし、監視するイベントの緑色の [+] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="94a29-119">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span> 

![空間アンカーのイベント](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="94a29-121">この場合は、[On Add Tracked Geometry]\(追跡ジオメトリの追加\) のイベントを監視し、空間マッピング データに対応する有効なワールド メッシュを探し、メッシュの素材を変更します。</span><span class="sxs-lookup"><span data-stu-id="94a29-121">In this case we monitor the On Add Tracked Geometry event looking for valid world meshes which correspond to spatial mapping data, and change the mesh’s material:</span></span> 

![空間アンカーの例](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="94a29-123">C++ では、OnTrackableAdded デリゲートをサブスクライブして、使用可能になったらすぐに ARTrackedGeometry を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="94a29-123">In C++, we can subscribe to the OnTrackableAdded delegate to get the ARTrackedGeometry as soon as it is available.</span></span>  <span data-ttu-id="94a29-124">更新および削除されたイベントでも、類似のデリゲートがあります。AddOnTrackableUpdatedDelegate_Handle と AddOnTrackableRemovedDelegate_Handle です。</span><span class="sxs-lookup"><span data-stu-id="94a29-124">There are similar delegates for updated and removed events: AddOnTrackableUpdatedDelegate_Handle and AddOnTrackableRemovedDelegate_Handle.</span></span> 

![空間アンカーの例の C++ コード](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="94a29-126">"ARBlueprintLibrary.h" および "MRMesh" をインクルードして MRMesh の UARTrackedGeometry コンポーネントを検査するには、プロジェクトの build.cs に、PublicDependencyModuleNames リストの "AugmentedReality" が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="94a29-126">The project’s build.cs must have “AugmentedReality” in the PublicDependencyModuleNames list to include “ARBlueprintLibrary.h” and “MRMesh” to inspect the MRMesh component of the UARTrackedGeometry.</span></span> 

<span data-ttu-id="94a29-127">空間マッピングは、ARTrackedGeometries によって表示される唯一の種類のデータではないので、まずは、EARObjectClassification が World であることを確認します。これは、それが空間マッピング ジオメトリであることを示します。</span><span class="sxs-lookup"><span data-stu-id="94a29-127">Spatial mapping is not the only type of data that gets surfaced through ARTrackedGeometries, so we first check that the EARObjectClassification is World, which indicates that this is spatial mapping geometry.</span></span> 

## <a name="see-also"></a><span data-ttu-id="94a29-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="94a29-128">See also</span></span>
* [<span data-ttu-id="94a29-129">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="94a29-129">Spatial mapping</span></span>](spatial-mapping.md)
