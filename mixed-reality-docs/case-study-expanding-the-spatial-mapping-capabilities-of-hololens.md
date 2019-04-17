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
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="08783-104">導入事例 - HoloLens の空間のマッピング機能を展開します。</span><span class="sxs-lookup"><span data-stu-id="08783-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="08783-105">Microsoft HoloLens の最初のアプリを作成するときにどの程度空間マッピングの境界デバイスにプッシュできますを参照してください。 一括でした。</span><span class="sxs-lookup"><span data-stu-id="08783-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="08783-106">Jeff Evertt、Microsoft Studios のソフトウェア エンジニアは、ユーザーの実際の環境でホログラムを配置する方法より詳細に制御の必要性からの新しいテクノロジが開発方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="08783-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="08783-107">ビデオを見る</span><span class="sxs-lookup"><span data-stu-id="08783-107">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="08783-108">空間マッピングを超える</span><span class="sxs-lookup"><span data-stu-id="08783-108">Beyond spatial mapping</span></span>

<span data-ttu-id="08783-109">作業中に[フラグメント](https://www.microsoft.com/p/fragments/9nblggh5ggm8)と[Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)2 つ、HoloLens の最初のゲームのわかりました、物理世界でホログラムの手続き型の配置を実行していた、ときに必要である上位のレベルユーザーの環境について理解します。</span><span class="sxs-lookup"><span data-stu-id="08783-109">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="08783-110">各ゲームでは、独自の特定の配置のニーズがありました。フラグメントでなどしたい異なるサーフェスを区別するためにできるように、床やテーブルなど — 手がかりを関連する場所に配置します。</span><span class="sxs-lookup"><span data-stu-id="08783-110">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="08783-111">など、ソファまたは椅子等身大 holographic 文字に座って、サーフェスを識別するためにできるようにすることも考えました。</span><span class="sxs-lookup"><span data-stu-id="08783-111">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="08783-112">Young の Conker で Conker と彼の対戦相手のプレイヤーの部屋で発生サーフェスをプラットフォームとして使用することができると考えました。</span><span class="sxs-lookup"><span data-stu-id="08783-112">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="08783-113">[Asobo スタジオ](http://www.asobostudio.com/index.html)、これらのゲームの開発パートナーが正面を向けたこの問題に直面し、HoloLens の空間のマッピング機能を拡張するテクノロジを作成します。</span><span class="sxs-lookup"><span data-stu-id="08783-113">[Asobo Studios](http://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="08783-114">これを使用して、私たちとでしたプレイヤーのルームを分析し、壁、テーブル、椅子、フロアなどのサーフェスを識別します。</span><span class="sxs-lookup"><span data-stu-id="08783-114">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="08783-115">これもくれました holographic オブジェクトの最適な配置を決定する制約のセットに対して最適化する機能。</span><span class="sxs-lookup"><span data-stu-id="08783-115">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="08783-116">コードを空間の理解</span><span class="sxs-lookup"><span data-stu-id="08783-116">The spatial understanding code</span></span>

<span data-ttu-id="08783-117">Asobo の元のコードをこのテクノロジをカプセル化するライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="08783-117">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="08783-118">Microsoft と Asobo これでこのコードをオープン ソース化されで利用できるように[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping)独自のプロジェクトで使用するためです。</span><span class="sxs-lookup"><span data-stu-id="08783-118">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="08783-119">すべてのソース コードが含まれて、ニーズに合わせてカスタマイズし、改善をコミュニティで共有することができます。</span><span class="sxs-lookup"><span data-stu-id="08783-119">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="08783-120">コードをC++ソルバーを UWP DLL にラップし、Unity に公開されている、 [MixedRealityToolkit 内に含まれるドロップイン プレハブ](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)します。</span><span class="sxs-lookup"><span data-stu-id="08783-120">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="08783-121">Unity のサンプルを壁の空白を検索、天井または床に大きなスペース上のオブジェクトを配置、場所に配置するには、文字と、多種多様な空間についての他のクエリを識別することが含まれている多くの便利なクエリがあります。</span><span class="sxs-lookup"><span data-stu-id="08783-121">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="08783-122">HoloLens によって提供される空間マッピング ソリューションを設計して、あらゆる問題領域のニーズを満たすのに十分なジェネリックにする、中に、空間理解モジュールは 2 つの特定のゲームのニーズをサポートするために構築されました。</span><span class="sxs-lookup"><span data-stu-id="08783-122">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="08783-123">そのため、特定のプロセスと前提条件のセットをそのソリューションが構成されています。</span><span class="sxs-lookup"><span data-stu-id="08783-123">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="08783-124">**固定サイズ playspace**:ユーザーは、init 呼び出しで最大 playspace サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="08783-124">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="08783-125">**1 回限りのスキャン プロセス**:プロセスが必要、個別スキャン フェーズの周囲、ユーザーがについて説明します、playspace を定義します。</span><span class="sxs-lookup"><span data-stu-id="08783-125">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="08783-126">スキャンが終了した後、クエリ関数はまで機能しなくなります。</span><span class="sxs-lookup"><span data-stu-id="08783-126">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="08783-127">**ユーザー駆動 playspace「描画」**:スキャン フェーズでは、ユーザーが移動し、効果的に含まれるとして使用する領域を描画、playspace を検索します。</span><span class="sxs-lookup"><span data-stu-id="08783-127">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="08783-128">生成したメッシュは、このフェーズ中にユーザーからのフィードバックを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08783-128">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="08783-129">**屋内自宅またはオフィスのセットアップ**:クエリ関数は、フラット サーフェスと直角に交わって壁を中心に設計されています。</span><span class="sxs-lookup"><span data-stu-id="08783-129">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="08783-130">これは、ソフト制限です。</span><span class="sxs-lookup"><span data-stu-id="08783-130">This is a soft limitation.</span></span> <span data-ttu-id="08783-131">ただし、スキャン フェーズでは、プライマリ軸の分析がメジャーおよびマイナーの軸に沿ったメッシュ テセレーションを最適化するために完了します。</span><span class="sxs-lookup"><span data-stu-id="08783-131">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="08783-132">ルームのスキャン プロセス</span><span class="sxs-lookup"><span data-stu-id="08783-132">Room Scanning Process</span></span>

<span data-ttu-id="08783-133">自分のスペースで使用可能なすべてのサーフェスをスキャンは、空間的に理解モジュールを読み込むときに、まず操作を行います: floor、ceiling、壁など — が特定され、ラベル付けします。</span><span class="sxs-lookup"><span data-stu-id="08783-133">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="08783-134">部屋を確認するスキャンの処理中に、"ペイント '、スキャンで含める必要がある領域です。</span><span class="sxs-lookup"><span data-stu-id="08783-134">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="08783-135">このフェーズ中に検出されたメッシュは、ユーザーがスキャンされるルームのどの部分を認識できるようにする視覚的なフィードバックの重要な要素です。</span><span class="sxs-lookup"><span data-stu-id="08783-135">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="08783-136">空間理解モジュールの DLL は、サイズ 8 cm voxel キューブのグリッドとして、playspace を内部的に格納します。</span><span class="sxs-lookup"><span data-stu-id="08783-136">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="08783-137">スキャンの初期段階では、部屋の軸を決定する主要なコンポーネントの分析が完了しました。</span><span class="sxs-lookup"><span data-stu-id="08783-137">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="08783-138">内部的には、これらの軸に配置されたその voxel 領域を格納します。</span><span class="sxs-lookup"><span data-stu-id="08783-138">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="08783-139">メッシュには、voxel ボリュームからアイソサーフェスを抽出することによって毎秒約が生成されます。</span><span class="sxs-lookup"><span data-stu-id="08783-139">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![白色のメッシュのマップを playspace を把握する空間が緑色でメッシュします。](images/spatial-mapping-500px.png)

<span data-ttu-id="08783-141">白色のメッシュのマップを playspace を把握する空間が緑色でメッシュします。</span><span class="sxs-lookup"><span data-stu-id="08783-141">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="08783-142">インクルード SpatialUnderstanding.cs ファイルは、スキャン フェーズの処理を管理します。</span><span class="sxs-lookup"><span data-stu-id="08783-142">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="08783-143">次の関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="08783-143">It calls the following functions:</span></span>
* <span data-ttu-id="08783-144">**SpatialUnderstanding_Init**:開始時に 1 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="08783-144">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="08783-145">**GeneratePlayspace_InitScan**:スキャンのフェーズを開始することを示します。</span><span class="sxs-lookup"><span data-stu-id="08783-145">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="08783-146">**GeneratePlayspace_UpdateScan_DynamicScan**:スキャン プロセスを更新するには、各フレームで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="08783-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="08783-147">カメラの位置と向きに渡され、playspace 描画プロセスは、上記で説明したために使用します。</span><span class="sxs-lookup"><span data-stu-id="08783-147">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="08783-148">**GeneratePlayspace_RequestFinish**:Playspace を最終処理と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="08783-148">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="08783-149">これを定義し、ロック、playspace スキャン フェーズ中に「描画」領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="08783-149">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="08783-150">アプリケーションでは、スキャン フェーズと、ユーザーからのフィードバックを提供するためのカスタムのメッシュをクエリ中に、統計情報を照会できます。</span><span class="sxs-lookup"><span data-stu-id="08783-150">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="08783-151">**Import_UnderstandingMesh**:スキャン中に、 **SpatialUnderstandingCustomMesh**モジュールによって提供されており、理解プレハブ上に配置の動作は、プロセスによって生成されるカスタムのメッシュを定期的にクエリします。</span><span class="sxs-lookup"><span data-stu-id="08783-151">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="08783-152">さらに、これはもう一度スキャンが終了した後です。</span><span class="sxs-lookup"><span data-stu-id="08783-152">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="08783-153">スキャンのフローによって、 **SpatialUnderstanding**動作呼び出し**InitScan**、し**UpdateScan**各フレーム。</span><span class="sxs-lookup"><span data-stu-id="08783-153">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="08783-154">統計情報のクエリが妥当なカバレッジを報告したときで、ユーザーを呼び出す airtap **RequestFinish**スキャン フェーズの終了を示す。</span><span class="sxs-lookup"><span data-stu-id="08783-154">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="08783-155">**UpdateScan**が戻り値になるまでに呼び出される継続値では、DLL の処理が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="08783-155">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="08783-156">クエリ</span><span class="sxs-lookup"><span data-stu-id="08783-156">The queries</span></span>

<span data-ttu-id="08783-157">スキャンが完了すると、インターフェイス内のクエリの 3 つの異なる型にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="08783-157">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="08783-158">**トポロジ クエリ**:これらは、スキャンした部屋のトポロジに基づいている高速なクエリです。</span><span class="sxs-lookup"><span data-stu-id="08783-158">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="08783-159">**クエリの整形**:これらは、トポロジを定義したカスタム図形とよく一致する水平方向のサーフェスを検索するクエリの結果を利用します。</span><span class="sxs-lookup"><span data-stu-id="08783-159">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="08783-160">**オブジェクト配置のクエリを**:これらは、一連のルールと、オブジェクトの制約に基づいて最適の場所を検索するより複雑なクエリです。</span><span class="sxs-lookup"><span data-stu-id="08783-160">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="08783-161">3 つの主要なクエリだけでなく、タグが付けられたサーフェイスのタイプを取得するために使用できるレイキャスト インターフェイスがあるし、カスタムのような厳重な部屋のメッシュをコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="08783-161">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="08783-162">トポロジのクエリ</span><span class="sxs-lookup"><span data-stu-id="08783-162">Topology queries</span></span>

<span data-ttu-id="08783-163">DLL 内では、トポロジのマネージャーは、環境のラベル付けを処理します。</span><span class="sxs-lookup"><span data-stu-id="08783-163">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="08783-164">前述のとおり、surfels voxel ボリューム内に格納されているデータの多く格納されます。</span><span class="sxs-lookup"><span data-stu-id="08783-164">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="08783-165">さらに、 **PlaySpaceInfos**構造を使用して、世界中の配置 (詳細については後述)、floor、ceiling 高さなど、playspace に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="08783-165">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="08783-166">ヒューリスティックは、floor、ceiling、壁を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="08783-166">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="08783-167">たとえば、1 m2 のサーフェス領域よりも大きいと、最大および最小の水平方向の画面は、床面と見なされます。</span><span class="sxs-lookup"><span data-stu-id="08783-167">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="08783-168">スキャン プロセス中にカメラのパスがこのプロセスで使用されるもことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="08783-168">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="08783-169">トポロジのマネージャーによって公開されているクエリのサブセットは、出力 DLL を介して公開されます。</span><span class="sxs-lookup"><span data-stu-id="08783-169">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="08783-170">公開されているトポロジのクエリは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="08783-170">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="08783-171">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="08783-171">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="08783-172">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="08783-172">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="08783-173">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="08783-173">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="08783-174">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="08783-174">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="08783-175">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="08783-175">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="08783-176">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="08783-176">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="08783-177">各クエリは、クエリの種類に固有のパラメーターのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="08783-177">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="08783-178">次の例では、ユーザーは、高さの最小値と最小の配置、フロア、クリアランスの前に、ボリュームの最小量の高さ、目的のボリュームの幅を指定します。</span><span class="sxs-lookup"><span data-stu-id="08783-178">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="08783-179">すべての測定値では、メートル単位で。</span><span class="sxs-lookup"><span data-stu-id="08783-179">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="08783-180">これらの各クエリの事前に割り当てられた配列を取得する**TopologyResult**構造体。</span><span class="sxs-lookup"><span data-stu-id="08783-180">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="08783-181">**LocationCount**パラメーターが渡された配列の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="08783-181">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="08783-182">戻り値は、返される位置の数を報告します。</span><span class="sxs-lookup"><span data-stu-id="08783-182">The return value reports the number of returned locations.</span></span> <span data-ttu-id="08783-183">この数が、渡されたに超えることはありません**locationCount**パラメーター。</span><span class="sxs-lookup"><span data-stu-id="08783-183">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="08783-184">**TopologyResult**返されるボリュームに接続する方向 (つまり標準)、および検索の領域の大きさの中央の位置が含まれています。</span><span class="sxs-lookup"><span data-stu-id="08783-184">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="08783-185">Unity のサンプルでは、これらの各クエリがリンクされている仮想 UI パネルのボタンに注意してください。</span><span class="sxs-lookup"><span data-stu-id="08783-185">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="08783-186">ハードのサンプル コードは妥当な値にこれらのクエリの各パラメーター。</span><span class="sxs-lookup"><span data-stu-id="08783-186">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="08783-187">参照してください*SpaceVisualizer.cs*例については、サンプル コード。</span><span class="sxs-lookup"><span data-stu-id="08783-187">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="08783-188">Shape クエリ</span><span class="sxs-lookup"><span data-stu-id="08783-188">Shape queries</span></span>

<span data-ttu-id="08783-189">図形のアナライザー、DLL 内で (**ShapeAnalyzer_W**) トポロジのアナライザーを使用して、ユーザーが定義したカスタム図形に対して照合します。</span><span class="sxs-lookup"><span data-stu-id="08783-189">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="08783-190">Unity のサンプルでは、クエリ メニューの 図形 タブに示されている図形の定義済みセットがあります。</span><span class="sxs-lookup"><span data-stu-id="08783-190">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="08783-191">形状の分析が水平方向のサーフェスのみで機能するに注意してください。</span><span class="sxs-lookup"><span data-stu-id="08783-191">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="08783-192">たとえば、ソファーは、戻るカウチのフラットの上端とフラット seat 画面によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="08783-192">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="08783-193">Shape クエリは、特定のサイズ、高さ、および縦横範囲の配置し、接続されている 2 つのサーフェスの 2 つのサーフェスを探します。</span><span class="sxs-lookup"><span data-stu-id="08783-193">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="08783-194">Api の用語を使用するには、ソファ クライアント数と、ソファーの後ろの上部は図形のコンポーネントと配置の要件は次の図形コンポーネントの制約。</span><span class="sxs-lookup"><span data-stu-id="08783-194">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="08783-195">Unity のサンプルで定義されているクエリの例 (**ShapeDefinition.cs**) は、"sittable"オブジェクトの次のようには。</span><span class="sxs-lookup"><span data-stu-id="08783-195">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




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

<span data-ttu-id="08783-196">各図形のクエリは、それぞれに、一連のコンポーネントの制約と、コンポーネント間の依存関係の一覧を表示する一連の図形の制約、図形のコンポーネントのセットによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="08783-196">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="08783-197">この例には、(1 つだけのコンポーネントであるため)、1 つのコンポーネントの定義とコンポーネント間で制約のない図形で次の 3 つの制約が含まれます。</span><span class="sxs-lookup"><span data-stu-id="08783-197">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="08783-198">これに対し、ソファ図形は、2 つのコンポーネントの図形と図形の 4 つの制約をが。</span><span class="sxs-lookup"><span data-stu-id="08783-198">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="08783-199">コンポーネントが (0 からこの例では 1) のユーザーのコンポーネントの一覧で、インデックスで識別されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="08783-199">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="08783-200">ラッパー関数は、カスタム図形の定義を簡単に作成の Unity モジュールで提供されます。</span><span class="sxs-lookup"><span data-stu-id="08783-200">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="08783-201">コンポーネントと図形の制約の完全な一覧が記載されて**SpatialUnderstandingDll.cs**内、 **ShapeComponentConstraint**と**ShapeConstraint**構造体。</span><span class="sxs-lookup"><span data-stu-id="08783-201">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![青い四角形には、椅子の shape クエリの結果が強調表示されます。](images/chair-shape-query-500px.png)

<span data-ttu-id="08783-203">青い四角形には、椅子の shape クエリの結果が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="08783-203">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="08783-204">オブジェクト配置のソルバー</span><span class="sxs-lookup"><span data-stu-id="08783-204">Object placement solver</span></span>

<span data-ttu-id="08783-205">オブジェクト配置のクエリは、オブジェクトを配置する物理的な部屋に理想的な場所を識別するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="08783-205">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="08783-206">最適の場所オブジェクトの規則と制約ソルバーが見つかります。</span><span class="sxs-lookup"><span data-stu-id="08783-206">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="08783-207">オブジェクトが削除されるまでさらに、オブジェクト クエリを永続化**Solver_RemoveObject**または**Solver_RemoveAllObjects**呼び出しを許可する複数のオブジェクトの配置の制約します。</span><span class="sxs-lookup"><span data-stu-id="08783-207">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="08783-208">オブジェクト配置のクエリは、3 つの部分で構成されています: パラメーター、一連の規則、制約のリストと配置の種類。</span><span class="sxs-lookup"><span data-stu-id="08783-208">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="08783-209">クエリを実行するには、次の API を使用します。</span><span class="sxs-lookup"><span data-stu-id="08783-209">To run a query, use the following API:</span></span>




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
<span data-ttu-id="08783-210">この関数は、オブジェクトの名前、配置の定義と規則と制約の一覧を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="08783-210">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="08783-211">C#ラッパーは構築規則と制約の構築を簡単にできるようにするヘルパー関数を提供します。</span><span class="sxs-lookup"><span data-stu-id="08783-211">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="08783-212">配置の定義には、クエリの種類が含まれています: は、次のいずれかの。</span><span class="sxs-lookup"><span data-stu-id="08783-212">The placement definition contains the query type — that is, one of the following:</span></span>




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

<span data-ttu-id="08783-213">パラメーターの型に固有の各配置の種類があります。</span><span class="sxs-lookup"><span data-stu-id="08783-213">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="08783-214">**ObjectPlacementDefinition**構造には、これらの定義を作成するための静的なヘルパー関数のセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="08783-214">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="08783-215">たとえば、床の上にオブジェクトを配置する場所を検索するには、次の関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="08783-215">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="08783-216">配置の種類だけでなく、一連の規則と制約を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="08783-216">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="08783-217">規則に違反することはできません。</span><span class="sxs-lookup"><span data-stu-id="08783-217">Rules cannot be violated.</span></span> <span data-ttu-id="08783-218">型とルールに適合するような配置場所は、最適な配置場所を選択する制約のセットに対して、最適化されています。</span><span class="sxs-lookup"><span data-stu-id="08783-218">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="08783-219">指定された静的作成関数によって各規則と制約を作成できます。</span><span class="sxs-lookup"><span data-stu-id="08783-219">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="08783-220">規則と制約の構築関数の例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="08783-220">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="08783-221">次のオブジェクト配置のクエリは、画面の端に半分メーター キューブを配置から他のオブジェクトを配置前、ルームの中心付近を場所探しています。</span><span class="sxs-lookup"><span data-stu-id="08783-221">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




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

<span data-ttu-id="08783-222">成功した場合、 **ObjectPlacementResult**配置位置、ディメンション、および印刷の向きを含む構造体が返されます。</span><span class="sxs-lookup"><span data-stu-id="08783-222">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="08783-223">さらに、配置は、配置されたオブジェクトの DLL の内部一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="08783-223">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="08783-224">後続の配置のクエリ アカウントにこのオブジェクトになります。</span><span class="sxs-lookup"><span data-stu-id="08783-224">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="08783-225">**LevelSolver.cs** Unity サンプル内のファイルに複数のクエリ例にはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="08783-225">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![青い四角形は、"離れたからカメラの位置"規則の 3 つの場所でフロア クエリから結果を表示します。](images/away-from-camera-position-500px.png)

<span data-ttu-id="08783-227">青い四角形は、"離れたからカメラの位置"規則の 3 つの場所でフロア クエリから結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="08783-227">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="08783-228">**ヒント:**</span><span class="sxs-lookup"><span data-stu-id="08783-228">**Tips:**</span></span>
* <span data-ttu-id="08783-229">レベルまたはアプリケーションのシナリオに必要な複数のオブジェクトの配置場所を解決するときに最初にスペースが含まれる確率を最大化に欠かせないや大規模なオブジェクトを解決します。</span><span class="sxs-lookup"><span data-stu-id="08783-229">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="08783-230">配置の順序が重要です。</span><span class="sxs-lookup"><span data-stu-id="08783-230">Placement order is important.</span></span> <span data-ttu-id="08783-231">オブジェクトへの配置が見つからない場合は、あまりに制約付きの構成をお試しください。</span><span class="sxs-lookup"><span data-stu-id="08783-231">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="08783-232">フォールバック構成のセットは、ルーム構成で多くの機能をサポートしているに不可欠です。</span><span class="sxs-lookup"><span data-stu-id="08783-232">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="08783-233">光線のキャスト</span><span class="sxs-lookup"><span data-stu-id="08783-233">Ray casting</span></span>

<span data-ttu-id="08783-234">3 つの主要なクエリだけでなく、ray キャスト インターフェイスを使用してタグが付けられたサーフェイスのタイプを取得して、カスタムのような厳重な playspace メッシュをコピーすることができますを部屋がスキャンされ、ファイナライズ後ラベルが内部的に生成されるなどの表面に対して、floor、ceiling、および壁します。</span><span class="sxs-lookup"><span data-stu-id="08783-234">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="08783-235">**PlayspaceRaycast**関数光線受け取り射線が既知の画面と競合する場合とそうである場合に返されますの形式でその画面については、 **RaycastResult**します。</span><span class="sxs-lookup"><span data-stu-id="08783-235">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


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

<span data-ttu-id="08783-236">内部的には、playspace の計算の 8 cm cubed voxel 表現に対して、raycast が計算されます。</span><span class="sxs-lookup"><span data-stu-id="08783-236">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="08783-237">各 voxel には、一連画面要素に処理されたトポロジのデータ (surfels とも呼ばれます) にはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="08783-237">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="08783-238">Voxel が交差するセル内に含まれる surfels が比較され、最も一致するトポロジ情報を検索するために使用します。</span><span class="sxs-lookup"><span data-stu-id="08783-238">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="08783-239">このトポロジのデータが含まれています、ラベル付けの形式で返される、 **SurfaceTypes**列挙型、交差する画面の表面領域とします。</span><span class="sxs-lookup"><span data-stu-id="08783-239">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="08783-240">Unity のサンプルでは、カーソルは各フレームに伸びる射線をキャストします。</span><span class="sxs-lookup"><span data-stu-id="08783-240">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="08783-241">Unity のコライダー; に対して最初に、understanding モジュールの世界の表現; に対して第 2 に、UI 要素に対して最後と。</span><span class="sxs-lookup"><span data-stu-id="08783-241">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="08783-242">このアプリケーションでは、UI は、優先度、し、理解の結果、および最後に、Unity のコライダーを取得します。</span><span class="sxs-lookup"><span data-stu-id="08783-242">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="08783-243">**SurfaceType**カーソルの横にあるテキストとしてレポートされます。</span><span class="sxs-lookup"><span data-stu-id="08783-243">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Raycast 結果の床面との交差を報告します。](images/raycast-result-500px.jpg)

<span data-ttu-id="08783-245">Raycast 結果の床面との交差を報告します。</span><span class="sxs-lookup"><span data-stu-id="08783-245">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="08783-246">コードを入手する</span><span class="sxs-lookup"><span data-stu-id="08783-246">Get the code</span></span>

<span data-ttu-id="08783-247">オープン ソース コードは[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)します。</span><span class="sxs-lookup"><span data-stu-id="08783-247">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="08783-248">知らせ、 [HoloLens デベロッパー フォーラム](https://forums.hololens.com/)プロジェクトでコードを使用する場合。</span><span class="sxs-lookup"><span data-stu-id="08783-248">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="08783-249">これで何を参照してください。 楽しみです。</span><span class="sxs-lookup"><span data-stu-id="08783-249">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="08783-250">執筆者紹介</span><span class="sxs-lookup"><span data-stu-id="08783-250">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="08783-251"><b>Jeff Evertt</b> HoloLens の開発を体験する育成から、初期の段階から作業しているソフトウェア エンジニア リング リードです。</span><span class="sxs-lookup"><span data-stu-id="08783-251"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="08783-252">HoloLens、前に、Xbox Kinect にし、多様なプラットフォームやゲームのゲーム業界で働いていました。</span><span class="sxs-lookup"><span data-stu-id="08783-252">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="08783-253">Jeff はロボット工学、グラフィック、およびピカピカ ビープ音を移動することに熱心です。</span><span class="sxs-lookup"><span data-stu-id="08783-253">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="08783-254">彼の新機能を学習し、ソフトウェア、ハードウェア、および特に 2 つの交差領域の操作を楽しんでいます。</span><span class="sxs-lookup"><span data-stu-id="08783-254">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="08783-255">関連項目</span><span class="sxs-lookup"><span data-stu-id="08783-255">See also</span></span>
* [<span data-ttu-id="08783-256">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="08783-256">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="08783-257">空間マッピングの設計</span><span class="sxs-lookup"><span data-stu-id="08783-257">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="08783-258">ルームのスキャンの視覚化</span><span class="sxs-lookup"><span data-stu-id="08783-258">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="08783-259">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="08783-259">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="08783-260">Asobo Studio:HoloLens の開発の最前線になってからの教訓</span><span class="sxs-lookup"><span data-stu-id="08783-260">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
