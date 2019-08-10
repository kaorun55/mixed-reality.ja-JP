---
title: シーンを理解する SDK
description: シーンについて理解する SDK のプログラミングガイド
author: szymons
ms.author: szymons
ms.date: 07/08/19
ms.topic: article
keywords: シーンの理解、空間マッピング、Windows Mixed Reality、Unity
ms.openlocfilehash: 88138622987800ff86a24d05e1308e694e2dd2b1
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2019
ms.locfileid: "68941239"
---
## <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="57ad8-104">シーンについて SDK の概要</span><span class="sxs-lookup"><span data-stu-id="57ad8-104">Scene Understanding SDK Overview</span></span>

<span data-ttu-id="57ad8-105">シーンを理解することは、Mixed Reality デバイスによってキャプチャされた非構造化環境センサーデータを変換し、を直感的かつ簡単に開発できる強力で抽象化された表現に変換することです。</span><span class="sxs-lookup"><span data-stu-id="57ad8-105">The goal of Scene Understanding is to transform the un-structured environment sensor data that your Mixed Reality device captures and to convert it into a powerful but abstracted representation that is intuitive and easy to develop for.</span></span> <span data-ttu-id="57ad8-106">SDK は、アプリケーションとシーンのランタイムを理解するための通信レイヤーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="57ad8-107">3d 表現の3d シーングラフや2d アプリケーション用の2D 四角形/パネルなど、既存の標準構成要素を模倣することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="57ad8-107">It's aimed to mimic existing standard constructs such as 3d scene graphs for 3d representations and 2D rectangles/panels for 2d applications.</span></span> <span data-ttu-id="57ad8-108">シーン認識の模倣は、使用する可能性のある具象フレームワークにマップされますが、一般に SceneUnderstanding はフレームワークに依存しないため、相互にやり取りする多様なフレームワーク間の相互運用が可能です。</span><span class="sxs-lookup"><span data-stu-id="57ad8-108">While the constructs Scene Understanding mimics will map to concrete frameworks you may use, in general SceneUnderstanding is framework agnostic allowing for interop between varied frameworks that interact with it.</span></span> <span data-ttu-id="57ad8-109">シーンを理解することは、SDK の役割を進化させることで、新しい表現と機能が統合されたフレームワーク内で引き続き公開されるようにしています。</span><span class="sxs-lookup"><span data-stu-id="57ad8-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="57ad8-110">このドキュメントでは、まず、開発環境や使用状況について理解を深め、特定のクラスと構成要素に関するより詳細なドキュメントを提供するための概要を紹介します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-110">In this document we will first introduce high level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="57ad8-111">SDK はどこで入手できますか?</span><span class="sxs-lookup"><span data-stu-id="57ad8-111">Where do I get the SDK?</span></span>

<span data-ttu-id="57ad8-112">SceneUnderstanding SDK は NuGet を使用してダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="57ad8-113">SceneUnderstanding SDK</span><span class="sxs-lookup"><span data-stu-id="57ad8-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="57ad8-114">開始する前に、SDK が UWP 上で実行されており、Windows SDK バージョン18362以降が必要であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="57ad8-114">Before you begin please note that the SDK runs on top of the UWP, and requires Windows SDK version 18362 or higher.</span></span> 

### <a name="the-scene"></a><span data-ttu-id="57ad8-115">シーン</span><span class="sxs-lookup"><span data-stu-id="57ad8-115">The Scene</span></span>

<span data-ttu-id="57ad8-116">混合の現実のデバイスは、環境内で認識されている内容に関する情報を常に統合しています。</span><span class="sxs-lookup"><span data-stu-id="57ad8-116">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="57ad8-117">シーンは、これらすべてのデータソースをじょうごし、1つのまとまりを持つ抽象化を生成します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-117">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="57ad8-118">シーンを理解すると、1つの物のインスタンスを表す[SceneObjects](scene-understanding-SDK.md#sceneobjects)の構成であるシーンが生成されます。シーンオブジェクト自体は、この SceneObject を構成する粒度の細かい部分を表す[SceneComponents](scene-understanding-SDK.md#scenecomponents)の合成です。</span><span class="sxs-lookup"><span data-stu-id="57ad8-118">Scene Understanding generates Scenes which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (e.g. a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents](scene-understanding-SDK.md#scenecomponents) which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="57ad8-119">コンポーネントの例としては、四角形やメッシュなどがありますが、将来的には、境界ボックス、衝突 mehses、メタデータなどを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-119">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision mehses, metadata etc...</span></span>

<span data-ttu-id="57ad8-120">生のセンサーデータをシーンに変換するプロセスは、非常に大きなスペース (~ 10x10m) が非常に大きい場合 (~ 50x50m)、デバイスによって計算されているものではない場合に、時間がかかります。アプリケーション要求。</span><span class="sxs-lookup"><span data-stu-id="57ad8-120">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for very large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="57ad8-121">代わりに、必要に応じて、アプリケーションによってシーン生成がトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-121">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="57ad8-122">SceneObserver クラスには、シーンを計算または逆シリアル化できる静的メソッドがあります。このメソッドを使用して、列挙および操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-122">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="57ad8-123">"Compute" アクションは要求時に実行され、CPU ではなく、別のプロセス (Mixed Reality ドライバー) で実行されます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-123">The "Compute" action is executed on-demand and executes on the CPU but in a seperate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="57ad8-124">ただし、別のプロセスで計算を行う場合、結果として得られるシーンデータは、アプリケーションのシーンオブジェクトに格納され、保持されます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-124">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="57ad8-125">このプロセスフローを示す図を以下に示します。また、2つのアプリケーションの例を示します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-125">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![プロセス図](images/SU-ProcessFlow.png)

<span data-ttu-id="57ad8-127">左側には、常にオンで、独自のプロセスで実行されている mixed reality ランタイムの図があります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-127">On the left hand side is a diagram of the mixed reality runtime which is always on and running in its own process.</span></span> <span data-ttu-id="57ad8-128">このランタイムは、デバイスの追跡、表面の再構築、およびシーンを理解するために使用されるその他の操作の実行を担当します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-128">This runtime is responsible for performing device tracking, surface reconstruction, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="57ad8-129">図の右側には、シーンの理解を活用する2つの理論的なアプリケーションが示されています。</span><span class="sxs-lookup"><span data-stu-id="57ad8-129">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="57ad8-130">最初のアプリケーションは、シーンを理解する SDK を使用する MRTK を使用して、2つの sepereate シーンインスタンスを計算して使用します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-130">The first application interfaces with MRTK which uses the Scene Understanding SDK internally, the second app computes and uses two sepereate scene instances.</span></span> <span data-ttu-id="57ad8-131">この図の3つのすべてのシーンでは、個別のインスタンスが生成されます。ドライバーは、アプリケーション間で共有されるグローバル状態を追跡しません。また、1つのシーンのシーンオブジェクトが別のシーンで見つからないことを示します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-131">All 3 Scenes in this diagram generate distinct instances of the scenes, the driver is not tracking global state that is shared between applications and Scene Objects in one scene are not found in another.</span></span> <span data-ttu-id="57ad8-132">シーンを理解することは、時間の経過と共に追跡するメカニズムを提供しますが、これは SDK とコードを使用して行われます。この追跡を実行するコードは、アプリのプロセスで SDK で実行されます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-132">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK and code the code that performs this tracking is running in the SDK in your app's process.</span></span>

<span data-ttu-id="57ad8-133">各シーンでは、アプリケーションのメモリ領域にデータが格納されるため、シーンオブジェクトまたはその内部データのすべての関数がアプリケーションのプロセスで常に実行されると想定できます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-133">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

#### <a name="layout"></a><span data-ttu-id="57ad8-134">レイアウト</span><span class="sxs-lookup"><span data-stu-id="57ad8-134">Layout</span></span>

<span data-ttu-id="57ad8-135">シーンを理解するには、ランタイムが論理的および物理的にコンポーネントを表す方法を理解し、理解しておくことが重要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-135">To work with Scene Understanding it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="57ad8-136">シーンは、主要な改訂を必要とせずに将来の要件を満たすように pliable された、基になる構造を維持しながら、単純なレイアウトを持つデータを表します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-136">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="57ad8-137">このシーンでは、すべてのコンポーネント (すべてのシーンオブジェクトの構成要素) をフラットリストに格納し、特定のコンポーネントが他のコンポーネントを参照する参照を使用して階層とコンポジションを定義します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-137">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="57ad8-138">次に、フラットフォームと論理形式の両方で構造体の例を示します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-138">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="57ad8-139">論理レイアウト</span><span class="sxs-lookup"><span data-stu-id="57ad8-139">Logical Layout</span></span></th><th><span data-ttu-id="57ad8-140">物理的なレイアウト</span><span class="sxs-lookup"><span data-stu-id="57ad8-140">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="57ad8-141">登場</span><span class="sxs-lookup"><span data-stu-id="57ad8-141">Scene</span></span>
  <ul>
  <li><span data-ttu-id="57ad8-142">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="57ad8-142">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="57ad8-143">Mesh_1</span><span class="sxs-lookup"><span data-stu-id="57ad8-143">Mesh_1</span></span></li>
      <li><span data-ttu-id="57ad8-144">Quad_1</span><span class="sxs-lookup"><span data-stu-id="57ad8-144">Quad_1</span></span></li>
      <li><span data-ttu-id="57ad8-145">Quad_2</span><span class="sxs-lookup"><span data-stu-id="57ad8-145">Quad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="57ad8-146">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="57ad8-146">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="57ad8-147">Quad_1</span><span class="sxs-lookup"><span data-stu-id="57ad8-147">Quad_1</span></span></li>
      <li><span data-ttu-id="57ad8-148">Quad_3</span><span class="sxs-lookup"><span data-stu-id="57ad8-148">Quad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="57ad8-149">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="57ad8-149">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="57ad8-150">Mesh_3</span><span class="sxs-lookup"><span data-stu-id="57ad8-150">Mesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="57ad8-151">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="57ad8-151">SceneObject_1</span></span></li>
  <li><span data-ttu-id="57ad8-152">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="57ad8-152">SceneObject_2</span></span></li>
  <li><span data-ttu-id="57ad8-153">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="57ad8-153">SceneObject_3</span></span></li>
  <li><span data-ttu-id="57ad8-154">Quad_1</span><span class="sxs-lookup"><span data-stu-id="57ad8-154">Quad_1</span></span></li>
  <li><span data-ttu-id="57ad8-155">Quad_2</span><span class="sxs-lookup"><span data-stu-id="57ad8-155">Quad_2</span></span></li>
  <li><span data-ttu-id="57ad8-156">Quad_3</span><span class="sxs-lookup"><span data-stu-id="57ad8-156">Quad_3</span></span></li>
  <li><span data-ttu-id="57ad8-157">Mesh_1</span><span class="sxs-lookup"><span data-stu-id="57ad8-157">Mesh_1</span></span></li>
  <li><span data-ttu-id="57ad8-158">Mesh_2</span><span class="sxs-lookup"><span data-stu-id="57ad8-158">Mesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="57ad8-159">この図は、シーンの物理的レイアウトと論理的レイアウトの違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="57ad8-159">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="57ad8-160">右側には、シーンを列挙するときにアプリケーションに表示されるデータの階層型レイアウトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-160">On the right we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="57ad8-161">左側には、必要に応じて個別にアクセスできる12個の個別のコンポーネントで構成されているシーンがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-161">On the left we see that the scene is actually comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="57ad8-162">新しいシーンを処理する場合、アプリケーションはこの階層を論理的にウォークすることを想定していますが、シーンの更新間を追跡する場合、一部のアプリケーションは、2つのシーン間で共有される特定のコンポーネントを対象にするだけでよい場合があります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-162">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

### <a name="high-level-overview"></a><span data-ttu-id="57ad8-163">概要</span><span class="sxs-lookup"><span data-stu-id="57ad8-163">High-level Overview</span></span>

<span data-ttu-id="57ad8-164">次のセクションでは、シーンについて理解するための構造の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-164">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="57ad8-165">このセクションを読むと、シーンの表現方法や、さまざまなコンポーネントがどのように使用されるかについて理解できます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-165">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="57ad8-166">次のセクションでは、具体的なコード例と、この概要でここしている追加の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-166">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

#### <a name="scenecomponents"></a><span data-ttu-id="57ad8-167">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="57ad8-167">SceneComponents</span></span>

<span data-ttu-id="57ad8-168">これで、背後の論理的なレイアウトを理解できるようになったので、SceneComponents の概念と、それらを使用して階層を構築する方法を提示できます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-168">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they are used to compose hierarchy.</span></span> <span data-ttu-id="57ad8-169">SceneComponents は、メッシュ、クワッド、境界ボックスなど、1つのコアを表す SceneUnderstanding の最も詳細な decompositions です。</span><span class="sxs-lookup"><span data-stu-id="57ad8-169">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, e.g. a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="57ad8-170">SceneComponents は、独立して更新でき、他の SceneComponents が参照できるものです。したがって、この種の追跡/参照メカニズムを可能にする一意の Id を持つ単一のグローバルプロパティを持つことになります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-170">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique Id, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="57ad8-171">Id は、シーン階層の論理構成およびオブジェクトの永続化 (あるシーンを別のシーンに更新する操作) に使用されます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-171">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="57ad8-172">新しく計算されたすべてのシーンを個別として処理し、その中のすべてのデータを列挙するだけで、Id は主に透過的になります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-172">If you are treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="57ad8-173">ただし、複数の更新プログラムでコンポーネントの追跡を計画している場合は、これらの Id を使用して、シーンオブジェクト間の SceneComponents のインデックス作成と検索を行います。</span><span class="sxs-lookup"><span data-stu-id="57ad8-173">However, if you are planning to track components over several updates you will use the Ids to index and find SceneComponents between Scene objects.</span></span>

#### <a name="sceneobjects"></a><span data-ttu-id="57ad8-174">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="57ad8-174">SceneObjects</span></span>

<span data-ttu-id="57ad8-175">SceneObject は、"物" のインスタンスを表す SceneComponent です。たとえば、壁、床、天井、などです。Kind プロパティで表されます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-175">A SceneObject is a SceneComponent that represents an instance of a "thing" e.g. a wall, a floor, a ceiling, etc... expressed by their Kind property.</span></span> <span data-ttu-id="57ad8-176">SceneObjects は幾何学的であるため、空間内の場所を表す関数とプロパティがありますが、ジオメトリックや論理構造は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="57ad8-176">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="57ad8-177">代わりに、SceneObjects は、システムでサポートされているさまざまな表現を提供する他の SceneComponents、特に SceneQuads と SceneMeshes を参照します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-177">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads and SceneMeshes which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="57ad8-178">新しいシーンが計算されると、ほとんどの場合、アプリケーションは、目的の内容を処理するためにシーンの SceneObjects を列挙します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-178">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="57ad8-179">SceneObjects は、次のいずれかを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-179">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="57ad8-180">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="57ad8-180">SceneObjectKind</span></span></th> <th><span data-ttu-id="57ad8-181">説明</span><span class="sxs-lookup"><span data-stu-id="57ad8-181">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="57ad8-182">背景情報</span><span class="sxs-lookup"><span data-stu-id="57ad8-182">Background</span></span></td><td><span data-ttu-id="57ad8-183">SceneObject は、他の認識された種類のシーンオブジェクトの1つでは<b>ない</b>ことがわかっています。</span><span class="sxs-lookup"><span data-stu-id="57ad8-183">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="57ad8-184">このクラスは不明と混同しないでください。背景が壁、床、天井などではないことがわかっています。不明なカテゴリはまだ分類されていません。</span><span class="sxs-lookup"><span data-stu-id="57ad8-184">This class should not be confused with Unknown where Background is known not to be wall/floor/ceiling etc... while unknown is not yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="57ad8-185">電話</span><span class="sxs-lookup"><span data-stu-id="57ad8-185">Wall</span></span></td><td><span data-ttu-id="57ad8-186">物理的な壁面。</span><span class="sxs-lookup"><span data-stu-id="57ad8-186">A physical wall.</span></span> <span data-ttu-id="57ad8-187">壁面は、移動可能な環境構造であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-187">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="57ad8-188">階数</span><span class="sxs-lookup"><span data-stu-id="57ad8-188">Floor</span></span></td><td><span data-ttu-id="57ad8-189">床は、どのような面でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-189">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="57ad8-190">注: 階段はフロアではありません。</span><span class="sxs-lookup"><span data-stu-id="57ad8-190">Note: stairs are not floors.</span></span> <span data-ttu-id="57ad8-191">また、このフロアは、明らかになる可能性があるため、1つの床面を明確に示すものではないことにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="57ad8-191">Also note, that floors assume any walkable surface and therefore there is no explicit assumption of a singular floor.</span></span> <span data-ttu-id="57ad8-192">複数レベルの構造、傾斜などすべてが floor として分類される必要があります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-192">Multi-level structures, ramps etc... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="57ad8-193">切り上げ</span><span class="sxs-lookup"><span data-stu-id="57ad8-193">Ceiling</span></span></td><td><span data-ttu-id="57ad8-194">部屋の上面。</span><span class="sxs-lookup"><span data-stu-id="57ad8-194">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="57ad8-195">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57ad8-195">Platform</span></span></td><td><span data-ttu-id="57ad8-196">ホログラムを配置できる大きな平らなサーフェイス。</span><span class="sxs-lookup"><span data-stu-id="57ad8-196">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="57ad8-197">これらは、テーブル、countertops、およびその他の大きな水平サーフェスを表す傾向があります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-197">These tend to represent tables, countertops and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="57ad8-198">World</span><span class="sxs-lookup"><span data-stu-id="57ad8-198">World</span></span></td><td><span data-ttu-id="57ad8-199">ラベル付けに依存しないジオメトリックデータ用に予約されたラベル。</span><span class="sxs-lookup"><span data-stu-id="57ad8-199">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="57ad8-200">EnableWorldMesh update フラグを設定することによって生成されるメッシュは、"世界" として分類されます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-200">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="57ad8-201">Unknown</span><span class="sxs-lookup"><span data-stu-id="57ad8-201">Unknown</span></span></td><td><span data-ttu-id="57ad8-202">このシーンオブジェクトはまだ分類されていないため、種類が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="57ad8-202">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="57ad8-203">これは、背景と混同しないようにしてください。このオブジェクトは何でもかまいません。システムは、十分な量の十分な分類を持っているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="57ad8-203">This should not be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

#### <a name="scenemesh"></a><span data-ttu-id="57ad8-204">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="57ad8-204">SceneMesh</span></span>

<span data-ttu-id="57ad8-205">SceneMesh は、トライアングルリストを使用して任意のジオメトリックオブジェクトのジオメトリを近似する SceneComponent です。</span><span class="sxs-lookup"><span data-stu-id="57ad8-205">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="57ad8-206">SceneMeshes は、いくつかの異なるコンテキストで使用されます。 watertight セル構造のコンポーネントを表すことも、シーンに関連付けられた無制限のサーフェス再構築を表す WorldMesh として表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-206">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh which represents the unbounded Surface Reconstruction associated with the Scene.</span></span> <span data-ttu-id="57ad8-207">各メッシュで提供されるインデックスと頂点データは、すべての最新のレンダリング Api で三角形メッシュをレンダリングするために使用される[頂点およびインデックスバッファー](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx)と同じ使い慣れたレイアウトを使用します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-207">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="57ad8-208">シーンの理解では、メッシュは32ビットのインデックスを使用し、特定のレンダリングエンジンのチャンクに分割する必要がある場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="57ad8-208">Note that in Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="scenequad"></a><span data-ttu-id="57ad8-209">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="57ad8-209">SceneQuad</span></span>

<span data-ttu-id="57ad8-210">SceneQuad は、3d ワールドを占める2d 表面を表す SceneComponent です。</span><span class="sxs-lookup"><span data-stu-id="57ad8-210">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="57ad8-211">SceneQuads は ARKit Arkit Eanchor または Arkit プレーンと同様に使用できますが、フラットなアプリや拡張された UX で使用される2d キャンバスとして、より高度な機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-211">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="57ad8-212">2D 固有の Api は、配置とレイアウトを簡単に使用できるようにするための四角形、および (レンダリングを除く) 四角形での開発には3d メッシュよりも2d キャンバスの方が似ています。</span><span class="sxs-lookup"><span data-stu-id="57ad8-212">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

### <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="57ad8-213">シーンについて SDK の詳細とリファレンス</span><span class="sxs-lookup"><span data-stu-id="57ad8-213">Scene Understanding SDK Details and Reference</span></span>

#### <a name="sdk"></a><span data-ttu-id="57ad8-214">SDK</span><span class="sxs-lookup"><span data-stu-id="57ad8-214">SDK</span></span>

<span data-ttu-id="57ad8-215">次のセクションでは、SceneUnderstanding の基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-215">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="57ad8-216">このセクションでは、サンプルアプリケーションを参照して、SceneUnderstanding がどのように総合的に使用されているかを確認するのに十分なコンテキストがある点について説明します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-216">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

#### <a name="initialization"></a><span data-ttu-id="57ad8-217">初期化</span><span class="sxs-lookup"><span data-stu-id="57ad8-217">Initialization</span></span>

<span data-ttu-id="57ad8-218">SceneUnderstanding を操作するための最初の手順は、アプリケーションが Scene オブジェクトへの参照を取得することです。</span><span class="sxs-lookup"><span data-stu-id="57ad8-218">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="57ad8-219">これは、2つの方法のいずれかで実行できます。シーンはドライバーによって計算されるか、過去に計算された既存のシーンを逆シリアル化することができます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-219">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="57ad8-220">後者は、開発時に SceneUnderstanding を使用する場合に特に便利です。この場合、アプリケーションとエクスペリエンスは、mixed reality デバイスなしで簡単にプロトタイプを作成できます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-220">The latter is particularly useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="57ad8-221">シーンは SceneObserver を使用して計算されます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-221">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="57ad8-222">シーンを作成する前に、アプリケーションがデバイスを照会して、SceneUnderstanding をサポートしていることを確認し、SceneUnderstanding が必要とする情報に対するユーザーアクセスを要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-222">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="57ad8-223">RequestAccessAsync () が呼び出されていない場合、新しいシーンを計算することはできません。</span><span class="sxs-lookup"><span data-stu-id="57ad8-223">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="57ad8-224">次に、Mixed Reality ヘッドセットを中心とした新しいシーンを計算し、10個の測定半径を持ちます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-224">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10 meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.Compute(querySettings, 10.0f);
```

#### <a name="initialization-from-data-aka-the-pc-path"></a><span data-ttu-id="57ad8-225">データからの初期化 (別名、</span><span class="sxs-lookup"><span data-stu-id="57ad8-225">Initialization from Data (aka.</span></span> <span data-ttu-id="57ad8-226">PC パス)</span><span class="sxs-lookup"><span data-stu-id="57ad8-226">the PC Path)</span></span>

<span data-ttu-id="57ad8-227">直接消費するためのシーンは計算できますが、後で使用できるようにシリアル化された形式で計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-227">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="57ad8-228">これは、開発者がデバイスを使用しなくてもシーンの理解を深めることができるように、開発に非常に役立つことが実証されています。</span><span class="sxs-lookup"><span data-stu-id="57ad8-228">This has proven to be very useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="57ad8-229">シーンをシリアル化する操作は、それを計算することとほぼ同じです。データは、SDK によってローカルで逆シリアル化されるのではなく、アプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-229">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="57ad8-230">その後、自分で逆シリアル化したり、将来使用するために保存したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-230">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneUnderstanding.QuerySettings querySettings;

// Compute a scene but serialized as a byte array
byte[] newSceneBlob = SceneObserver.ComputeSerialized(querySettings, 10.0f);

// If we want to use it immediatley we can de-serialize the scene ourselves
Scene mySceneDeSerialized = Scene.Deserialize(newSceneBlob);

// Save newSceneBlob for later
```

#### <a name="sceneobject-enumeration"></a><span data-ttu-id="57ad8-231">SceneObject 列挙型</span><span class="sxs-lookup"><span data-stu-id="57ad8-231">SceneObject Enumeration</span></span>

<span data-ttu-id="57ad8-232">アプリケーションにシーンが作成されたので、アプリケーションは SceneObjects と対話します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-232">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="57ad8-233">これを行うには、 **SceneObjects**プロパティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="57ad8-233">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

#### <a name="component-update-and-re-finding-components"></a><span data-ttu-id="57ad8-234">コンポーネントの更新とコンポーネントの再検出</span><span class="sxs-lookup"><span data-stu-id="57ad8-234">Component update and re-finding components</span></span>

<span data-ttu-id="57ad8-235">***Findcomponent***というシーン内のコンポーネントを取得する関数もあります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-235">There is another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="57ad8-236">この関数は、追跡オブジェクトを更新し、それを後続のシーンで検索する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="57ad8-236">This function is useful when updating tracking objects and finding them in subsequent scenes.</span></span> <span data-ttu-id="57ad8-237">次のコードでは、前のシーンに対して相対的な新しいシーンを計算し、新しいシーンでフロアを検索します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-237">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, but tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.Compute(querySettings, 10.0f, myScene);

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attatched to this floor transform
}
```

### <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="57ad8-238">シーンオブジェクトからのメッシュと四角形へのアクセス</span><span class="sxs-lookup"><span data-stu-id="57ad8-238">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="57ad8-239">SceneObjects が見つかると、通常、アプリケーションは、構成されている四角形/メッシュを含むデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="57ad8-239">Once SceneObjects have been found your application will most likely want to access the data that is contained n the quads/meshes that it is comprised of.</span></span> <span data-ttu-id="57ad8-240">このデータには、[***四角形***と***メッシュ***] プロパティを使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="57ad8-240">This data is accessed with the ***Quads*** and ***Meshes*** properties.</span></span> <span data-ttu-id="57ad8-241">次のコードは、floor オブジェクトのすべての四角形とメッシュを列挙します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-241">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the matrix for the SceneObject
System.Numerics.Matrix4x4 floorTransform = firstFloor.LocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="57ad8-242">これは、シーンオリジンに対する変換を含む SceneObject であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="57ad8-242">Notice that it is the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="57ad8-243">これは、SceneObject が "事柄" のインスタンスを表し、スペースで参照できるため、四角形とメッシュが親を基準として変換されるジオメトリを表しているためです。</span><span class="sxs-lookup"><span data-stu-id="57ad8-243">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="57ad8-244">個別の SceneObjects が同じ SceneMesh/SceneQuad SceneComponewnts を参照している可能性があります。また、SceneObject に複数の SceneMesh/SceneQuad がある可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-244">It is possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponewnts, and it is also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="57ad8-245">変換の処理</span><span class="sxs-lookup"><span data-stu-id="57ad8-245">Dealing with Transforms</span></span>

<span data-ttu-id="57ad8-246">シーンの理解により、変換を処理するときに、従来の3D シーン表現に合わせて意図的に配置しようとしました。</span><span class="sxs-lookup"><span data-stu-id="57ad8-246">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="57ad8-247">そのため、各シーンは、最も一般的な3D 環境表現と同じように、1つの座標系に限定されます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-247">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="57ad8-248">アプリケーションが、1つのオリジンが提供する機能の上限を広げることによって、SceneObjects を SpatialAnchors に固定したり、複数のシーンを生成して結合したりすることができますが、わかりやすくするために、watertight のシーンが独自のものであることを前提としています。シーン:: OriginSpatialGraphNodeId で定義された1つの NodeId でローカライズされたオリジン。</span><span class="sxs-lookup"><span data-stu-id="57ad8-248">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene::OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="57ad8-249">次の unity コードは、windows 認識と Unity Api を使用して座標系をまとめて配置する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="57ad8-249">The following unity code, for example, shows how to use windows perception and Unity APIs to align coordinate systems together:</span></span>


```cs
    public static System.Numerics.Matrix4x4? GetSceneToUnityTransform(Guid nodeId)
    {
        System.Numerics.Matrix4x4? sceneToUnityTransform; 
       
        SpatialCoordinateSystem sceneSpatialCoordinateSystem = Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(nodeId);
        SpatialCoordinateSystem unitySpatialCoordinateSystem = (SpatialCoordinateSystem)System.Runtime.InteropServices.Marshal.GetObjectForIUnknown(UnityEngine.XR.WSA.WorldManager.GetNativeISpatialCoordinateSystemPtr());

        sceneToUnityTransform = sceneSpatialCoordinateSystem.TryGetTransformTo(unitySpatialCoordinateSystem);

        if (sceneToUnityTransform != null)
        {
            sceneToUnityTransform = TransformUtils.ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
        }
        
        return sceneToUnityTransform;
    }

    // Converts from right-handed to left handed coordinates
    public System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 transformationMatrix)
    {
        transformationMatrix.M13 = -transformationMatrix.M13;
        transformationMatrix.M23 = -transformationMatrix.M23;
        transformationMatrix.M43 = -transformationMatrix.M43;

        transformationMatrix.M31 = -transformationMatrix.M31;
        transformationMatrix.M32 = -transformationMatrix.M32;
        transformationMatrix.M34 = -transformationMatrix.M34;

        return transformationMatrix;
    }
```

<span data-ttu-id="57ad8-250">次のコードは、この関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-250">And the following code calls this function:</span></span>

```cs
System.Numerics.Matrix4x4? sceneToUnityTransform = TransformUtils.GetSceneToUnityTransform(scene.OriginSpatialGraphNodeId);

// Set the root transform
Vector3 t;
Quaternion r;
Vector3 s;

System.Numerics.Matrix4x4.Decompose(sceneToUnityTransform, out s, out r, out t);
SceneRoot.Transform.SetPositionAndRotation(t, r);
```

### <a name="quad"></a><span data-ttu-id="57ad8-251">Quad</span><span class="sxs-lookup"><span data-stu-id="57ad8-251">Quad</span></span>

<span data-ttu-id="57ad8-252">四角形は、2D の配置シナリオを容易にするように設計されており、2D キャンバス UX 要素の拡張機能と考える必要があります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-252">Quads were designed to facilitate 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="57ad8-253">四角形は SceneObjects のコンポーネントであり、3D でレンダリングできますが、クワッド Api 自体は、四角形が2D 構造体であると想定しています。</span><span class="sxs-lookup"><span data-stu-id="57ad8-253">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="57ad8-254">エクステントや形などの情報を提供し、配置のための Api を提供します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-254">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="57ad8-255">四角形は四角形のエクステントを持ちますが、任意の形の2d サーフェイスを表します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-255">Quads have rectangular extents, but they represent arbitrarily shaped 2d surfaces.</span></span> <span data-ttu-id="57ad8-256">3D 環境の四角形を操作するこれらの2D サーフェイス上の配置を有効にするには、この相互作用を可能にするユーティリティを提供します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-256">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="57ad8-257">現在、シーンの理解には、 **Findセンター**のほとんどの配置と**GetOcclusionMask**という2つの関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="57ad8-257">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetOcclusionMask**.</span></span> <span data-ttu-id="57ad8-258">Findセンターのほとんどの配置は、オブジェクトを配置できるクワッド上の位置を特定し、指定した境界ボックスが基になるサーフェイスに存在することを保証するオブジェクトの最適な位置を検索する、高レベルの API です。</span><span class="sxs-lookup"><span data-stu-id="57ad8-258">FindCentermostPlacement is a high level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will reside on the underlying surface.</span></span>

<span data-ttu-id="57ad8-259">次の例では、中央の最も配置可能な場所を検索し、クワッドにホログラムを固定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-259">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new node QuadTransformNode as a child of Root, and set the transform from quad[0].Transform
                // Step 2: Create your hologram and set it as a child of QuadTransformNode
                // Step 3: Set the QuadTransformNode tranform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="57ad8-260">手順1-3 は、特定のフレームワーク/実装に大きく依存しますが、テーマは類似している必要があります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-260">Steps 1-3 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="57ad8-261">クワッドは通常は使用されないことに注意してください。は、空間でローカライズされた境界2D 平面だけを表します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-261">It is important to note that the Quad is not usually intended to be, is just represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="57ad8-262">お使いのエンジンとフレームワークで、クワッドがどこにあるかを認識し、クワッドを基準としてオブジェクトをルート設定することにより、ホログラムが正しく配置されます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-262">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly.</span></span> <span data-ttu-id="57ad8-263">詳細については、特定の実装を示す四角形のサンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="57ad8-263">For more detailed information please see our samples on quads which show specific implementations.</span></span>

### <a name="mesh"></a><span data-ttu-id="57ad8-264">メッシュ</span><span class="sxs-lookup"><span data-stu-id="57ad8-264">Mesh</span></span>

<span data-ttu-id="57ad8-265">メッシュは、オブジェクトまたは環境の幾何学的表現を表します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-265">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="57ad8-266">[空間マッピング](spatial-mapping.md)と同様に、各空間サーフェスメッシュで提供されるメッシュインデックスと頂点データは、すべての最新のレンダリング api で三角形メッシュをレンダリングするために使用される頂点およびインデックスバッファーと同じ使い慣れたレイアウトを使用します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-266">Much like [spatial mapping](spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="57ad8-267">このデータを参照するために使用される特定の Api は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="57ad8-267">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(float[] vertices);
```

<span data-ttu-id="57ad8-268">\* \* 注:GetVertices は、浮動小数点値の3組がデカルト x、y、z 空間の1つの座標を表す頂点のリストを返します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-268">\*\*Note: GetVertices returns a list of vertices where every 3-tuple of floating point values represents a single coordinate in cartesian x,y and z space.</span></span>

<span data-ttu-id="57ad8-269">次のコードは、メッシュ構造から三角形リストを生成する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="57ad8-269">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
float[] positions = new float[mesh.VertexCount * 3];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="57ad8-270">インデックス/頂点バッファーは > = インデックスまたは頂点の数である必要がありますが、それ以外は任意にサイズを変更して、効率的なメモリの再利用を可能にすることができます。</span><span class="sxs-lookup"><span data-stu-id="57ad8-270">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory re-use.</span></span>

### <a name="developing-with-scene-understandings"></a><span data-ttu-id="57ad8-271">シーン異なればを使用した開発</span><span class="sxs-lookup"><span data-stu-id="57ad8-271">Developing with Scene Understandings</span></span>

<span data-ttu-id="57ad8-272">この時点で、ランタイムと SDK について理解しているシーンのコア構成要素について理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="57ad8-272">At this point you should understand the core building blocks of the Scene Understanding runtime and SDK.</span></span> <span data-ttu-id="57ad8-273">電力と複雑さの大部分は、アクセスパターン、3d フレームワークとの対話、およびこれらの Api の上に記述できるツールによって、空間プランニング、ルーム分析、ナビゲーション、物理などのより高度なタスクを実行できます。これらをサンプルでキャプチャして、シナリオを適切な方向に導くことができるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="57ad8-273">The bulk of the power and complexity lies in access patterns, interaction with 3d frameworks, and tools that can be written on top of these APIs to perform more advanced tasks like spatial planning, room analysis, navigation, physics etc... We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="57ad8-274">説明していないサンプルまたはシナリオがある場合は、お知らせください。必要なものをドキュメント化してプロトタイプを作成します。</span><span class="sxs-lookup"><span data-stu-id="57ad8-274">If there are samples/scenarios we are not addressing, please let us know and we will try to document/prototype what you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="57ad8-275">関連項目</span><span class="sxs-lookup"><span data-stu-id="57ad8-275">See also</span></span>

* [<span data-ttu-id="57ad8-276">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="57ad8-276">spatial mapping</span></span>](spatial-mapping.md)
