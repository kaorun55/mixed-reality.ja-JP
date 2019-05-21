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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605058"
---
# <a name="local-anchor-transfers-in-unity"></a>Unity では、ローカルのアンカー転送

使用できない状況で<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>、ローカルのアンカーの転送には、2 番目の HoloLens デバイスによってインポートされるアンカーをエクスポートする 1 つの HoloLens デバイスが有効にします。

>[!NOTE]
>ローカルのアンカー転送よりも堅牢性のアンカー再現率を提供する<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>、iOS および Android デバイスは、このアプローチではサポートされていないとします。

### <a name="setting-the-spatialperception-capability"></a>SpatialPerception 機能の設定

空間のアンカーを転送するアプリのために、 *SpatialPerception*機能を有効にする必要があります。

有効にする方法、 *SpatialPerception*機能。
1. Unity エディターで開き、 **「プレーヤー設定」** ウィンドウ (編集 > プロジェクトの設定 > Player)
2. をクリックして、 **"Windows Store"**  タブ
3. 展開 **「発行の設定」** を確認し、 **"SpatialPerception"** 機能、 **「機能」** 一覧

>[!NOTE]
>Visual Studio ソリューションに既に Unity プロジェクトをエクスポートした場合は、新しいフォルダーをまたは手動でいずれかのエクスポートする必要があります。 [Visual Studio で AppxManifest でこの機能を設定](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)します。

### <a name="anchor-transfer"></a>アンカーの転送

**名前空間:**  *UnityEngine.XR.WSA.Sharing*<br>
**種類**:*WorldAnchorTransferBatch*

転送する、 [WorldAnchor](coordinate-systems-in-unity.md)、1 つの送信をアンカーを確立する必要があります。 HoloLens の 1 つのユーザーは各自の環境をスキャンし、手動またはプログラムでは、領域を共有のエクスペリエンスのアンカーでポイントを選択します。 この点を表すデータをシリアル化、およびエクスペリエンスで共有している他のデバイスに送信します。 各デバイスに、アンカーのデータをシリアル化解除し、領域内でそのポイントを検索しようとしています。 作業にアンカーを転送するためは、アンカーによって表されるポイントを識別できるように、環境を十分に各デバイスをスキャンしてする必要があります。

### <a name="setup"></a>セットアップ

このページのサンプル コードでは、初期化する必要のあるいくつかのフィールドがあります。
1. *GameObject rootGameObject*は、 *GameObject*が Unity で、 *WorldAnchor*のコンポーネント。 共有のエクスペリエンスの 1 人のユーザーには、この配置は*GameObject*およびその他のユーザーにデータをエクスポートします。
2. *WorldAnchor gameRootAnchor*は、 *UnityEngine.XR.WSA.WorldAnchor*です*rootGameObject*します。
3. *バイト [importedData*は各クライアントがネットワーク経由で受け取るシリアル化されたアンカーのバイト配列です。

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

### <a name="exporting"></a>エクスポートします。

エクスポートするだけ、 *WorldAnchor*はいわゆるがある場合、受信側のアプリを把握するとします。 共有のエクスペリエンスで 1 つのクライアントでは、共有のアンカーをエクスポートするこれらの手順を実行します。
1. 作成、 *WorldAnchorTransferBatch*
2. 追加、 *WorldAnchors*を転送するには
3. エクスポートを開始します。
4. 処理、 *OnExportDataAvailable*データとしてイベントが使用可能になります
5. 処理、 *OnExportComplete*イベント

作成、 *WorldAnchorTransferBatch*何をカプセル化するには、転送してバイトにエクスポートしは。

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

データが使用可能なデータのセグメントが使用可能で、クライアントまたはバッファーにバイトを送信し、必要な手段を通じて送信。

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

エクスポートが完了すると、転送されてデータとシリアル化が失敗した場合は、データを破棄するクライアントに指示します。 シリアル化に成功した場合をクライアントに指示するすべてのデータが転送され、インポートを開始できます。

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

### <a name="importing"></a>インポートします。

すべてのバイトを受信、送信側から後、にデータをインポートできます、 *WorldAnchorTransferBatch*と物理的に同じ場所に、ルートのゲーム オブジェクトをロックします。 注: インポートは一時的に場合によっては失敗し、再試行する必要があります。

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

後に、 *GameObject*経由でロックされている、 *LockObject*の呼び出しを*WorldAnchor*する世界では、同じ物理的な位置に維持されますが、可能性がある、Unity で別の場所は、他のユーザーよりも容量を調整します。

