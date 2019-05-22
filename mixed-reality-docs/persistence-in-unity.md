---
title: Unity で永続化
description: 永続化には、ユーザー、および後で使用、アプリの多くで期待される場所を探してな場所は、個々 のホログラムまたはワークスペースをピン留めことができます。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、Unity の永続化
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605078"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="9d4de-104">Unity で永続化</span><span class="sxs-lookup"><span data-stu-id="9d4de-104">Persistence in Unity</span></span>

<span data-ttu-id="9d4de-105">**名前空間:** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="9d4de-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="9d4de-106">**クラス:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="9d4de-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="9d4de-107">WorldAnchorStore は、アプリケーションのインスタンス間で特定の実際の位置にホログラムまま、holographic エクスペリエンスを作成するキーです。</span><span class="sxs-lookup"><span data-stu-id="9d4de-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="9d4de-108">これにより、ユーザーは個々 のホログラムまたはワークスペースを固定後は、し、検索後で、アプリのさまざまな用途で期待される場所。</span><span class="sxs-lookup"><span data-stu-id="9d4de-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="9d4de-109">ホログラムをセッション間で永続化する方法</span><span class="sxs-lookup"><span data-stu-id="9d4de-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="9d4de-110">WorldAnchorStore はセッション間での WorldAnchor の場所を保持できます。</span><span class="sxs-lookup"><span data-stu-id="9d4de-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="9d4de-111">セッション間で保持ホログラムが実際には個別に追跡する特定の世界のアンカーを使用する、Gameobject 必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d4de-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="9d4de-112">多くの場合、理にかなって world アンカーを持つ GameObject ルートを作成し、子を持つローカルの位置のオフセットによってホログラムが固定されています。</span><span class="sxs-lookup"><span data-stu-id="9d4de-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="9d4de-113">前のセッションからホログラムを読み込めません。</span><span class="sxs-lookup"><span data-stu-id="9d4de-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="9d4de-114">WorldAnchorStore を取得します。</span><span class="sxs-lookup"><span data-stu-id="9d4de-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="9d4de-115">世界のアンカーの id を提供する世界アンカーに関連するアプリ データの読み込み</span><span class="sxs-lookup"><span data-stu-id="9d4de-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="9d4de-116">その id から世界アンカーを読み込む</span><span class="sxs-lookup"><span data-stu-id="9d4de-116">Load a world anchor from its id</span></span>

<span data-ttu-id="9d4de-117">今後のセッション ホログラムを保存します。</span><span class="sxs-lookup"><span data-stu-id="9d4de-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="9d4de-118">WorldAnchorStore を取得します。</span><span class="sxs-lookup"><span data-stu-id="9d4de-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="9d4de-119">Id を指定する世界アンカーを保存します。</span><span class="sxs-lookup"><span data-stu-id="9d4de-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="9d4de-120">Id と共に世界アンカーに関連するアプリのデータを保存します。</span><span class="sxs-lookup"><span data-stu-id="9d4de-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="9d4de-121">WorldAnchorStore を取得します。</span><span class="sxs-lookup"><span data-stu-id="9d4de-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="9d4de-122">操作を実行すると移動する準備ができましたがわかるように、周り WorldAnchorStore への参照を保持します。</span><span class="sxs-lookup"><span data-stu-id="9d4de-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="9d4de-123">呼び出すしたいので、これは、非同期呼び出し、可能性のある開始とすぐ、</span><span class="sxs-lookup"><span data-stu-id="9d4de-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="9d4de-124">StoreLoaded は、ここで、WorldAnchorStore の読み込みが完了すると、ハンドラーを示します。</span><span class="sxs-lookup"><span data-stu-id="9d4de-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="9d4de-125">保存および特定の世界のアンカーの読み込みに使用する WorldAnchorStore への参照があるようになりました。</span><span class="sxs-lookup"><span data-stu-id="9d4de-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="9d4de-126">WorldAnchor を保存しています</span><span class="sxs-lookup"><span data-stu-id="9d4de-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="9d4de-127">を保存するには、だけに保存していること確認し、保存する場合、選択する前に先ほど WorldAnchor で渡しますの名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d4de-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="9d4de-128">注: (ストアが失敗は、同じ文字列に 2 つのアンカーを保存しようとしています。保存は false を返します)。</span><span class="sxs-lookup"><span data-stu-id="9d4de-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="9d4de-129">新しいものを保存する前に、前の保存を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d4de-129">You need to Delete the previous save before saving the new one:</span></span>

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a><span data-ttu-id="9d4de-130">WorldAnchor の読み込み</span><span class="sxs-lookup"><span data-stu-id="9d4de-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="9d4de-131">読み込めません。</span><span class="sxs-lookup"><span data-stu-id="9d4de-131">And to load:</span></span>

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

<span data-ttu-id="9d4de-132">さらにストアを使用できます。以前保存したアンカーを削除する Delete() とストア。Clear() 以前に保存したすべてのデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="9d4de-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="9d4de-133">既存のアンカーを列挙します。</span><span class="sxs-lookup"><span data-stu-id="9d4de-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="9d4de-134">以前に保存されたアンカーを検出するには、GetAllIds を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9d4de-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="9d4de-135">複数のデバイスの永続化するホログラム</span><span class="sxs-lookup"><span data-stu-id="9d4de-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="9d4de-136">使用することができます<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>をローカル WorldAnchor、それらのデバイスが同じ一緒に存在しない場合でも、アプリが複数の HoloLens、iOS、Android デバイス間で検索しできますから永続的なクラウド アンカーを作成するには時間です。</span><span class="sxs-lookup"><span data-stu-id="9d4de-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="9d4de-137">クラウド アンカーが永続的なので、時間の経過と共に複数のデバイスできます各を参照してください同じ物理的な場所でそのアンカーに対して相対的にレンダリングされたコンテンツ。</span><span class="sxs-lookup"><span data-stu-id="9d4de-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="9d4de-138">5 分間試して、Unity での共有エクスペリエンスの構築を開始、<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">空間アンカー Unity の Azure クイック スタート</a>します。</span><span class="sxs-lookup"><span data-stu-id="9d4de-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="9d4de-139">空間のアンカーを Azure で稼働しているを開発したとして、<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">を作成し、Unity 内でアンカーを検索</a>します。</span><span class="sxs-lookup"><span data-stu-id="9d4de-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d4de-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d4de-140">See Also</span></span>
* [<span data-ttu-id="9d4de-141">空間アンカーの永続化</span><span class="sxs-lookup"><span data-stu-id="9d4de-141">Spatial anchor persistence</span></span>](coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="9d4de-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure の空間アンカー</a></span><span class="sxs-lookup"><span data-stu-id="9d4de-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="9d4de-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー Unity 用の SDK</a></span><span class="sxs-lookup"><span data-stu-id="9d4de-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
