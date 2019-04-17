---
title: Unity では、ローカルのアンカー転送
description: アンカーは、Unity アプリケーションで複数の HoloLens デバイス間で転送します。
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: 共有、アンカー、WorldAnchor、MR 共有 250、WorldAnchorTransferBatch、SpatialPerception、転送、ローカルのアンカーの転送、アンカーのエクスポート、アンカーのインポート
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605058"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="25dd8-104">Unity では、ローカルのアンカー転送</span><span class="sxs-lookup"><span data-stu-id="25dd8-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="25dd8-105">使用できない状況で<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>、ローカルのアンカーの転送には、2 番目の HoloLens デバイスによってインポートされるアンカーをエクスポートする 1 つの HoloLens デバイスが有効にします。</span><span class="sxs-lookup"><span data-stu-id="25dd8-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="25dd8-106">ローカルのアンカー転送よりも堅牢性のアンカー再現率を提供する<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>、iOS および Android デバイスは、このアプローチではサポートされていないとします。</span><span class="sxs-lookup"><span data-stu-id="25dd8-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="25dd8-107">SpatialPerception 機能の設定</span><span class="sxs-lookup"><span data-stu-id="25dd8-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="25dd8-108">空間のアンカーを転送するアプリのために、 *SpatialPerception*機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="25dd8-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="25dd8-109">有効にする方法、 *SpatialPerception*機能。</span><span class="sxs-lookup"><span data-stu-id="25dd8-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="25dd8-110">Unity エディターで開き、 **「プレーヤー設定」** ウィンドウ (編集 > プロジェクトの設定 > Player)</span><span class="sxs-lookup"><span data-stu-id="25dd8-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="25dd8-111">をクリックして、 **"Windows Store"**  タブ</span><span class="sxs-lookup"><span data-stu-id="25dd8-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="25dd8-112">展開 **「発行の設定」** を確認し、 **"SpatialPerception"** 機能、 **「機能」** 一覧</span><span class="sxs-lookup"><span data-stu-id="25dd8-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="25dd8-113">Visual Studio ソリューションに既に Unity プロジェクトをエクスポートした場合は、新しいフォルダーをまたは手動でいずれかのエクスポートする必要があります。 [Visual Studio で AppxManifest でこの機能を設定](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)します。</span><span class="sxs-lookup"><span data-stu-id="25dd8-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="25dd8-114">アンカーの転送</span><span class="sxs-lookup"><span data-stu-id="25dd8-114">Anchor Transfer</span></span>

<span data-ttu-id="25dd8-115">\**名前空間:\*\*\*UnityEngine.XR.WSA.Sharing*</span><span class="sxs-lookup"><span data-stu-id="25dd8-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="25dd8-116">**種類**:*WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="25dd8-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="25dd8-117">転送する、 [WorldAnchor](coordinate-systems-in-unity.md)、1 つの送信をアンカーを確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25dd8-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="25dd8-118">HoloLens の 1 つのユーザーは各自の環境をスキャンし、手動またはプログラムでは、領域を共有のエクスペリエンスのアンカーでポイントを選択します。</span><span class="sxs-lookup"><span data-stu-id="25dd8-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="25dd8-119">この点を表すデータをシリアル化、およびエクスペリエンスで共有している他のデバイスに送信します。</span><span class="sxs-lookup"><span data-stu-id="25dd8-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="25dd8-120">各デバイスに、アンカーのデータをシリアル化解除し、領域内でそのポイントを検索しようとしています。</span><span class="sxs-lookup"><span data-stu-id="25dd8-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="25dd8-121">作業にアンカーを転送するためは、アンカーによって表されるポイントを識別できるように、環境を十分に各デバイスをスキャンしてする必要があります。</span><span class="sxs-lookup"><span data-stu-id="25dd8-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="25dd8-122">セットアップ</span><span class="sxs-lookup"><span data-stu-id="25dd8-122">Setup</span></span>

<span data-ttu-id="25dd8-123">このページのサンプル コードでは、初期化する必要のあるいくつかのフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="25dd8-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="25dd8-124">*GameObject rootGameObject*は、 *GameObject*が Unity で、 *WorldAnchor*のコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="25dd8-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="25dd8-125">共有のエクスペリエンスの 1 人のユーザーには、この配置は*GameObject*およびその他のユーザーにデータをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="25dd8-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="25dd8-126">*WorldAnchor gameRootAnchor*は、 *UnityEngine.XR.WSA.WorldAnchor*です*rootGameObject*します。</span><span class="sxs-lookup"><span data-stu-id="25dd8-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="25dd8-127">*バイト [importedData*は各クライアントがネットワーク経由で受け取るシリアル化されたアンカーのバイト配列です。</span><span class="sxs-lookup"><span data-stu-id="25dd8-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a><span data-ttu-id="25dd8-128">エクスポートします。</span><span class="sxs-lookup"><span data-stu-id="25dd8-128">Exporting</span></span>

<span data-ttu-id="25dd8-129">エクスポートするだけ、 *WorldAnchor*はいわゆるがある場合、受信側のアプリを把握するとします。</span><span class="sxs-lookup"><span data-stu-id="25dd8-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="25dd8-130">共有のエクスペリエンスで 1 つのクライアントでは、共有のアンカーをエクスポートするこれらの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="25dd8-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="25dd8-131">作成、 *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="25dd8-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="25dd8-132">追加、 *WorldAnchors*を転送するには</span><span class="sxs-lookup"><span data-stu-id="25dd8-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="25dd8-133">エクスポートを開始します。</span><span class="sxs-lookup"><span data-stu-id="25dd8-133">Begin the export</span></span>
4. <span data-ttu-id="25dd8-134">処理、 *OnExportDataAvailable*データとしてイベントが使用可能になります</span><span class="sxs-lookup"><span data-stu-id="25dd8-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="25dd8-135">処理、 *OnExportComplete*イベント</span><span class="sxs-lookup"><span data-stu-id="25dd8-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="25dd8-136">作成、 *WorldAnchorTransferBatch*何をカプセル化するには、転送してバイトにエクスポートしは。</span><span class="sxs-lookup"><span data-stu-id="25dd8-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="25dd8-137">データが使用可能なデータのセグメントが使用可能で、クライアントまたはバッファーにバイトを送信し、必要な手段を通じて送信。</span><span class="sxs-lookup"><span data-stu-id="25dd8-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="25dd8-138">エクスポートが完了すると、転送されてデータとシリアル化が失敗した場合は、データを破棄するクライアントに指示します。</span><span class="sxs-lookup"><span data-stu-id="25dd8-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="25dd8-139">シリアル化に成功した場合をクライアントに指示するすべてのデータが転送され、インポートを開始できます。</span><span class="sxs-lookup"><span data-stu-id="25dd8-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a><span data-ttu-id="25dd8-140">インポートします。</span><span class="sxs-lookup"><span data-stu-id="25dd8-140">Importing</span></span>

<span data-ttu-id="25dd8-141">すべてのバイトを受信、送信側から後、にデータをインポートできます、 *WorldAnchorTransferBatch*と物理的に同じ場所に、ルートのゲーム オブジェクトをロックします。</span><span class="sxs-lookup"><span data-stu-id="25dd8-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="25dd8-142">注: インポートは一時的に場合によっては失敗し、再試行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25dd8-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

<span data-ttu-id="25dd8-143">後に、 *GameObject*経由でロックされている、 *LockObject*の呼び出しを*WorldAnchor*する世界では、同じ物理的な位置に維持されますが、可能性がある、Unity で別の場所は、他のユーザーよりも容量を調整します。</span><span class="sxs-lookup"><span data-stu-id="25dd8-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

