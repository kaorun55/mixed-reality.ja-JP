---
title: DirectX では、ローカルのアンカー転送
description: 空間のアンカーを転送することによって 2 つの HoloLens デバイスを同期する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、同期、空間アンカー、転送、マルチプレイヤー シナリオ、チュートリアル、サンプル コード、転送、ローカル アンカー転送、アンカーのエクスポート、インポートのアンカーを表示
ms.openlocfilehash: 5d03f4bfa764b9948ec4718bce86127cfcc3e303
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605068"
---
# <a name="local-anchor-transfers-in-directx"></a><span data-ttu-id="4dd55-104">DirectX では、ローカルのアンカー転送</span><span class="sxs-lookup"><span data-stu-id="4dd55-104">Local anchor transfers in DirectX</span></span>

<span data-ttu-id="4dd55-105">使用できない状況で<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>、ローカルのアンカーの転送には、2 番目の HoloLens デバイスによってインポートされるアンカーをエクスポートする 1 つの HoloLens デバイスが有効にします。</span><span class="sxs-lookup"><span data-stu-id="4dd55-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="4dd55-106">ローカルのアンカー転送よりも堅牢性のアンカー再現率を提供する<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>、iOS および Android デバイスは、このアプローチではサポートされていないとします。</span><span class="sxs-lookup"><span data-stu-id="4dd55-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

>[!NOTE]
><span data-ttu-id="4dd55-107">この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="4dd55-108">概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dd55-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="transferring-spatial-anchors"></a><span data-ttu-id="4dd55-109">空間のアンカーを転送します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-109">Transferring spatial anchors</span></span>

<span data-ttu-id="4dd55-110">Windows Mixed Reality を使用してデバイス間で空間アンカーを転送することができます、 [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-110">You can transfer spatial anchors between Windows Mixed Reality devices by using the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="4dd55-111">この API では、世界では、その場所を検索するために必要なすべてのサポート センサー データをアンカーをバンドルし、別のデバイスでは、そのバンドルをインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-111">This API lets you bundle up an anchor with all the supporting sensor data needed to find that exact place in the world, and then import that bundle on another device.</span></span> <span data-ttu-id="4dd55-112">2 つ目のデバイスでアプリがそのアンカーをインポートすると、各アプリは現実の世界と同じ場所に表示されますが、空間のアンカーの座標システムの共有を使用してホログラムをレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-112">Once the app on the second device has imported that anchor, each app can render holograms using that shared spatial anchor's coordinate system, which will then appear in the same place in the real world.</span></span>

<span data-ttu-id="4dd55-113">空間アンカーは、各種デバイス間で転送することはできません、たとえば HoloLens 空間アンカーできない可能性があります、イマーシブ ヘッドセットを使用して場所を特定できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4dd55-113">Note that spatial anchors are not able to transfer between different device types, for example a HoloLens spatial anchor may not be locatable using an immersive headset.</span></span>  <span data-ttu-id="4dd55-114">転送されたアンカーは、いない iOS または Android デバイスと互換性があります。</span><span class="sxs-lookup"><span data-stu-id="4dd55-114">Transferred anchors are also not compatible with iOS or Android devices.</span></span>

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="4dd55-115">SpatialPerception 機能を使用するアプリをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="4dd55-115">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="4dd55-116">アプリに使用できる前に、spatialPerception 機能を使用するアクセス許可を与える必要があります、 [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-116">Your app must be granted permission to use the spatialPerception capability before it can use the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="4dd55-117">これは、機能は、機密情報を含めることが、その場所の近くで時間の経過と共に収集したセンサーのイメージを共有が含まれる空間アンカーを転送するため必要です。</span><span class="sxs-lookup"><span data-stu-id="4dd55-117">This is necessary because transferring a spatial anchor involves sharing sensor images gathered over time in vicinity of that anchor, which might include sensitive information.</span></span>

<span data-ttu-id="4dd55-118">アプリの package.appxmanifest ファイルでこの機能を宣言します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-118">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="4dd55-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-119">Here's an example:</span></span>

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="4dd55-120">機能に由来します**uap2**名前空間。</span><span class="sxs-lookup"><span data-stu-id="4dd55-120">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="4dd55-121">マニフェストでこの名前空間へのアクセスを取得するには、それを含める、 *xlmns*属性、&lt;パッケージ > 要素。</span><span class="sxs-lookup"><span data-stu-id="4dd55-121">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="4dd55-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-122">Here's an example:</span></span>

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

<span data-ttu-id="4dd55-123">**注:** アプリは、SpatialAnchor エクスポート/インポート Api にアクセスする前に、実行時に機能を要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dd55-123">**NOTE:** Your app will need to request the capability at runtime before it can access SpatialAnchor export/import APIs.</span></span> <span data-ttu-id="4dd55-124">参照してください[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx)次の例では。</span><span class="sxs-lookup"><span data-stu-id="4dd55-124">See [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) in the examples below.</span></span>

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a><span data-ttu-id="4dd55-125">アンカーのデータをシリアル化、SpatialAnchorTransferManager をエクスポートして</span><span class="sxs-lookup"><span data-stu-id="4dd55-125">Serialize anchor data by exporting it with the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="4dd55-126">ヘルパー関数がエクスポートするコード サンプルに含まれる (シリアル化) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)データ。</span><span class="sxs-lookup"><span data-stu-id="4dd55-126">A helper function is included in the code sample to export (serialize) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) data.</span></span> <span data-ttu-id="4dd55-127">このエクスポート API には、文字列をアンカーに関連付けるキー/値ペアのコレクション内のすべてのアンカーがシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-127">This export API serializes all anchors in a collection of key-value pairs associating strings with anchors.</span></span>

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

<span data-ttu-id="4dd55-128">最初に、データ ストリームを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dd55-128">First, we need to set up the data stream.</span></span> <span data-ttu-id="4dd55-129">これにより、1 にします。)アプリ、および 2 によって所有されているバッファーにデータを格納するのに TryExportAnchorsAsync を使用します。)std::vector は、独自のメモリ バッファーには WinRT データ ストリームがエクスポートされたバイトのバッファー ストリームからデータを読み取る&lt;バイト >。</span><span class="sxs-lookup"><span data-stu-id="4dd55-129">This will allow us to 1.) use TryExportAnchorsAsync to put the data in a buffer owned by the app, and 2.) read data from the exported byte buffer stream - which is a WinRT data stream - into our own memory buffer, which is a std::vector&lt;byte>.</span></span>

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

<span data-ttu-id="4dd55-130">システムによってエクスポートされるアンカーを含め、空間データにアクセスするためのアクセス許可を依頼する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dd55-130">We need to ask permission to access spatial data, including anchors that are exported by the system.</span></span>

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

<span data-ttu-id="4dd55-131">アクセス許可を取得しています、アンカーは、エクスポート、データ ストリームを読むことができます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-131">If we do get permission and anchors are exported, we can read the data stream.</span></span> <span data-ttu-id="4dd55-132">ここでは、また DataReader とデータの読み取りに使用して、InputStream を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-132">Here, we also show how to create the DataReader and InputStream we will use to read the data.</span></span>

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

<span data-ttu-id="4dd55-133">ストリームからバイトを読んだ後は、独自のデータ バッファーに保存しましたにできますようになります。</span><span class="sxs-lookup"><span data-stu-id="4dd55-133">After we read bytes from the stream, we can save them to our own data buffer like so.</span></span>

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a><span data-ttu-id="4dd55-134">アンカーのデータを SpatialAnchorTransferManager を使用して、システムにインポートすることによって逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-134">Deserialize anchor data by importing it into the system using the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="4dd55-135">ヘルパー関数は、以前エクスポートされたデータを読み込むコード サンプルに含まれます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-135">A helper function is included in the code sample to load previously exported data.</span></span> <span data-ttu-id="4dd55-136">この逆シリアル化関数は、ネットワーク ソケットなどの別のソースからこのデータを先ほどする点を除いて、SpatialAnchorStore の説明のようなキーと値のペアのコレクションを提供します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-136">This deserialization function provides a collection of key-value pairs, similar to what the SpatialAnchorStore provides - except that we got this data from another source, such as a network socket.</span></span> <span data-ttu-id="4dd55-137">処理することができますとを使用して、オフラインのアプリでメモリに格納する前にこのデータに関する理由 (該当する場合) またはアプリの SpatialAnchorStore します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-137">You can process and reason about this data before storing it offline, using in-app memory, or (if applicable) your app's SpatialAnchorStore.</span></span>

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

<span data-ttu-id="4dd55-138">最初に、アンカーのデータにアクセスするストリーム オブジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dd55-138">First, we need to create stream objects to access the anchor data.</span></span> <span data-ttu-id="4dd55-139">データが書き込まれる、バッファーから、システムのバッファーにバイト バッファーから SpatialAnchors としてシステムにアンカーを取得するという目標を実現するために、メモリ内のデータ ストリームに書き込みを行う DataWriter ので作成されます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-139">We will be writing the data from our buffer to a system buffer, so we will create a DataWriter that writes to an in-memory data stream in order to accomplish our goal of getting anchors from a byte buffer into the system as SpatialAnchors.</span></span>

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

<span data-ttu-id="4dd55-140">ここでも、アプリのアクセス許可、ユーザーの環境に関するプライベートな情報が含まれますアンカーの空間データをエクスポートすることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dd55-140">Once again, we need to ensure the app has permission to export spatial anchor data, which could include private information about the user's environment.</span></span>

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

<span data-ttu-id="4dd55-141">アクセスが許可されている場合、システム データ ストリームにバイト バッファーから作成できます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-141">If access is allowed, we can write bytes from the buffer to a system data stream.</span></span>

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

<span data-ttu-id="4dd55-142">データ ストリームにバイトを格納するのに成功した場合、SpatialAnchorTransferManager を使用してそのデータをインポートする試すことができます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-142">If we were successful in storing bytes in the data stream, we can try to import that data using the SpatialAnchorTransferManager.</span></span>

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

<span data-ttu-id="4dd55-143">データがインポートできる場合は、文字列をアンカーに関連付けるキー/値ペアのマップ ビューを取得します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-143">If the data is able to be imported, we get a map view of key-value pairs associating strings with anchors.</span></span> <span data-ttu-id="4dd55-144">これを独自のメモリ内のデータ コレクションに読み込むをそのコレクションを使用してに関心を持っているアンカーを検索できます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-144">We can load this into our own in-memory data collection, and use that collection to look for anchors that we are interested in using.</span></span>

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

<span data-ttu-id="4dd55-145">**注:** アンカーをインポートするには、必ずしもいってすぐに使用します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-145">**NOTE:** Just because you can import an anchor, doesn't necessarily mean that you can use it right away.</span></span> <span data-ttu-id="4dd55-146">アンカーが完全; の別のルーム、または別の物理的な場所である可能性があります。アンカーは、受信するデバイスには、アンカーが既知の現在の環境を基準と、アンカーの位置を復元するには、作成環境について visual 十分な情報まで、場所を特定できることができません。</span><span class="sxs-lookup"><span data-stu-id="4dd55-146">The anchor might be in a different room, or another physical location entirely; the anchor won't be locatable until the device that received it has enough visual information about the environment the anchor was created in, to restore the anchor's position relative to the known current environment.</span></span> <span data-ttu-id="4dd55-147">クライアントの実装では、ライブ コンテンツの使用を続行する前に、ローカルの座標システムまたは参照フレームの基準としたアンカーを検索してみてください。</span><span class="sxs-lookup"><span data-stu-id="4dd55-147">The client implementation should try locating the anchor relative to your local coordinate system or reference frame before continuing on to try to use it for live content.</span></span> <span data-ttu-id="4dd55-148">たとえば、アンカーを開始する場所を特定できるまでに定期的に、現在の座標系を基準としたアンカーを検索してみてください。</span><span class="sxs-lookup"><span data-stu-id="4dd55-148">For example, try locating the anchor relative to a current coordinate system periodically until the anchor begins to be locatable.</span></span>

## <a name="special-considerations"></a><span data-ttu-id="4dd55-149">特別な考慮事項</span><span class="sxs-lookup"><span data-stu-id="4dd55-149">Special Considerations</span></span>

<span data-ttu-id="4dd55-150">[TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API では、複数[SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)同じ不透明なバイナリの blob にエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="4dd55-150">The [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API allows multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) to be exported into the same opaque binary blob.</span></span> <span data-ttu-id="4dd55-151">ただし、どのようなデータを 1 回の呼び出しで SpatialAnchor を 1 つまたは複数の SpatialAnchors をエクスポートするかどうかに応じて、blob が含まれます微妙な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="4dd55-151">However, there is a subtle difference in what data the blob will include, depending on whether a single SpatialAnchor or multiple SpatialAnchors are exported in a single call.</span></span>

### <a name="export-of-a-single-spatialanchor"></a><span data-ttu-id="4dd55-152">1 つ SpatialAnchor のエクスポート</span><span class="sxs-lookup"><span data-stu-id="4dd55-152">Export of a single SpatialAnchor</span></span>

<span data-ttu-id="4dd55-153">Blob には、環境は、SpatialAnchor をインポートするデバイスで認識できるように、環境、SpatialAnchor ポインターの近くの表現が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4dd55-153">The blob contains a representation of the environment in the vicinity of the SpatialAnchor so that the environment can be recognized on the device that imports the SpatialAnchor.</span></span> <span data-ttu-id="4dd55-154">インポートが完了すると、新しい SpatialAnchor は同じデバイスにことができます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-154">After the import completes, the new SpatialAnchor will be available to the device.</span></span> <span data-ttu-id="4dd55-155">ユーザーは、アンカーの付近に最近されたと仮定すると場所を特定できることが、SpatialAnchor にアタッチされているホログラムをレンダリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-155">Assuming the user has recently been in vicinity of the anchor, it will be locatable and holograms attached to the SpatialAnchor can be rendered.</span></span> <span data-ttu-id="4dd55-156">これらホログラム、SpatialAnchor のエクスポート元のデバイスでその同じ物理的な場所に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-156">These holograms will show up in the same physical location that they did on the original device which exported the SpatialAnchor.</span></span>

![1 つ SpatialAnchor のエクスポート](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a><span data-ttu-id="4dd55-158">複数の SpatialAnchors のエクスポート</span><span class="sxs-lookup"><span data-stu-id="4dd55-158">Export of multiple SpatialAnchors</span></span>

<span data-ttu-id="4dd55-159">単一 SpatialAnchor、エクスポートなど、blob には、指定したすべての SpatialAnchors ポインターの近くの環境の表現が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4dd55-159">Like the export of a single SpatialAnchor, the blob contains a representation of the environment in the vicinity of all the specified SpatialAnchors.</span></span> <span data-ttu-id="4dd55-160">さらに、blob を同じ物理領域に配置されている場合、含まれる SpatialAnchors 間の接続に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-160">In addition, the blob contains information about the connections between the included SpatialAnchors, if they are located in the same physical space.</span></span> <span data-ttu-id="4dd55-161">つまり、2 つの近くにある SpatialAnchors がインポートされた場合、ホログラムに接続されている、 *2 番目*SpatialAnchor できれば、しなくても、デバイスでは、周りの環境のみが認識、*最初*SpatialAnchor、ため、2 つの SpatialAnchors 間で変換を計算するための十分なデータが blob に含まれています。</span><span class="sxs-lookup"><span data-stu-id="4dd55-161">This means that if two nearby SpatialAnchors are imported, then a hologram attached to the *second* SpatialAnchor would be locatable even if the device only recognizes the environment around the *first* SpatialAnchor, because enough data to compute transform between the two SpatialAnchors was included in the blob.</span></span> <span data-ttu-id="4dd55-162">2 つの SpatialAnchors が個別にエクスポートされた場合 (2 つの個別 TryExportSpatialAnchors への呼び出し) はできないかもしれませんが 1 つ目にあるときに場所を特定できる 2 つ目の SpatialAnchor ホログラム接続、blob 内に含まれるための十分なデータが存在し、します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-162">If the two SpatialAnchors were exported individually (two separate calls to TryExportSpatialAnchors) then there may not be enough data included in the blob for holograms attached to the second SpatialAnchor to be locatable when the first one is located.</span></span>

![1 つの TryExportAnchorsAsync 呼び出しを使用してエクスポートする複数のアンカー](images/multipleanchors.png) ![各アンカーの別個の TryExportAnchorsAsync 呼び出しを使用してエクスポートする複数のアンカー](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a><span data-ttu-id="4dd55-165">以下に例を示します。アンカーを Windows::Networking::StreamSocket を使用してデータを送信します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-165">Example: Send anchor data using a Windows::Networking::StreamSocket</span></span>

<span data-ttu-id="4dd55-166">ここでは、TCP ネットワーク経由で送信することでアンカーがエクスポートされたデータを使用する方法の例を提供します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-166">Here, we provide an example of how to use exported anchor data by sending it across a TCP network.</span></span> <span data-ttu-id="4dd55-167">これは、HolographicSpatialAnchorTransferSample です。</span><span class="sxs-lookup"><span data-stu-id="4dd55-167">This is from the HolographicSpatialAnchorTransferSample.</span></span>

<span data-ttu-id="4dd55-168">WinRT StreamSocket クラスは、PPL タスクのライブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-168">The WinRT StreamSocket class uses the PPL task library.</span></span> <span data-ttu-id="4dd55-169">ネットワークのエラーの場合は、再スローされる例外を使用して、チェーン内の次のタスクにエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-169">In the case of network errors, the error is returned to the next task in the chain using an exception that is re-thrown.</span></span> <span data-ttu-id="4dd55-170">例外には、エラー状態を示す HRESULT が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4dd55-170">The exception contains an HRESULT indicating the error status.</span></span>

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a><span data-ttu-id="4dd55-171">TCP で、Windows::Networking::StreamSocketListener を使用して、エクスポートされたアンカーのデータを送信するには</span><span class="sxs-lookup"><span data-stu-id="4dd55-171">Use a Windows::Networking::StreamSocketListener with TCP to send exported anchor data</span></span>

<span data-ttu-id="4dd55-172">接続を待機しているサーバー インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-172">Create a server instance that listens for a connection.</span></span>

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

<span data-ttu-id="4dd55-173">接続が受信したときに、アンカーのデータを送信するのにクライアント ソケットの接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-173">When a connection is received, use the client socket connection to send anchor data.</span></span>

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

<span data-ttu-id="4dd55-174">これで、アンカーのエクスポートされたデータを格納するデータ ストリームを送信する開始ことができます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-174">Now, we can begin to send a data stream that contains the exported anchor data.</span></span>

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

<span data-ttu-id="4dd55-175">ストリーム自体を送信することができます、私たちには、まずヘッダー パケットを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dd55-175">Before we can send the stream itself, we must first send a header packet.</span></span> <span data-ttu-id="4dd55-176">このヘッダーのパケットが長さの固定長にする必要があり。、アンカーのデータ ストリームはバイトの変数の配列の長さを指定する必要があります。場合はこの例ではないその他のヘッダーのデータを送信する、そのため、ヘッダー 4 バイト長と 32 ビット符号なし整数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4dd55-176">This header packet must be of fixed length, and it must also indicate the length of the variable array of bytes that is the anchor data stream; in the case of this example we have no other header data to send, so our header is 4 bytes long and contains a 32-bit unsigned integer.</span></span>

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

<span data-ttu-id="4dd55-177">(バイト単位) のストリームの長さが、クライアントに送信されたデータ ストリーム自体をソケットのストリームに書き込む続行できます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-177">Once the stream length, in bytes, has been sent to the client, we can proceed to write the data stream itself to the socket stream.</span></span> <span data-ttu-id="4dd55-178">これにより、クライアントに送信するアンカー ストア バイト。</span><span class="sxs-lookup"><span data-stu-id="4dd55-178">This will cause the anchor store bytes to get sent to the client.</span></span>

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

<span data-ttu-id="4dd55-179">このトピックで説明した、ネットワーク エラー ステータス メッセージを格納している例外を処理する準備をする必要があります予定。</span><span class="sxs-lookup"><span data-stu-id="4dd55-179">As noted earlier in this topic, we must be prepared to handle exceptions containing network error status messages.</span></span> <span data-ttu-id="4dd55-180">デバッグ コンソールに例外情報を書き込むときの予期しないエラーでは、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="4dd55-180">For errors that are not expected, we can write the exception info to the debug console like so.</span></span> <span data-ttu-id="4dd55-181">計算結果は、コード サンプルが、接続を完了できない場合、またはアンカー データの送信を完了することがない場合の変更点に関する手がかりとなります。</span><span class="sxs-lookup"><span data-stu-id="4dd55-181">This will give us a clue as to what happened if our code sample is unable to complete the connection, or if it is unable to finish sending the anchor data.</span></span>

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a><span data-ttu-id="4dd55-182">TCP で、Windows::Networking::StreamSocket を使用して、エクスポートされたアンカーのデータを受信するには</span><span class="sxs-lookup"><span data-stu-id="4dd55-182">Use a Windows::Networking::StreamSocket with TCP to receive exported anchor data</span></span>

<span data-ttu-id="4dd55-183">最初に、サーバーに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dd55-183">First, we have to connect to the server.</span></span> <span data-ttu-id="4dd55-184">このコード サンプルでは、作成して構成を StreamSocket、ソケット接続を使用してネットワーク データを取得するために使用できる DataReader を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-184">This code sample shows how to create and configure a StreamSocket, and create a DataReader that you can use to acquire network data using the socket connection.</span></span>

<span data-ttu-id="4dd55-185">**注:** このサンプル コードを実行する場合は、構成し、クライアントを開始する前に、サーバーを起動することを確認します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-185">**NOTE:** If you run this sample code, ensure that you configure and launch the server before starting the client.</span></span>

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

<span data-ttu-id="4dd55-186">接続したら、サーバーがデータを送信する待機できます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-186">Once we have a connection, we can wait for the server to send data.</span></span> <span data-ttu-id="4dd55-187">ストリームのデータ リーダーで LoadAsync を呼び出して、そいます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-187">We do this by calling LoadAsync on the stream data reader.</span></span>

<span data-ttu-id="4dd55-188">受信バイト数の最初のセットは、前のセクションで説明されているアンカー データ ストリーム バイトの長さを示すヘッダー パケットには常にします。</span><span class="sxs-lookup"><span data-stu-id="4dd55-188">The first set of bytes we receive should always be the header packet, which indicates the anchor data stream byte length as described in the previous section.</span></span>

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

<span data-ttu-id="4dd55-189">...</span><span class="sxs-lookup"><span data-stu-id="4dd55-189">...</span></span>

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

<span data-ttu-id="4dd55-190">ヘッダーのパケットを受け取って後、は、予想されるアンカー データのバイト数がわかっています。</span><span class="sxs-lookup"><span data-stu-id="4dd55-190">After we have received the header packet, we know how many bytes of anchor data we should expect.</span></span> <span data-ttu-id="4dd55-191">それらのバイトをストリームから読み取ったに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-191">We can proceed to read those bytes from the stream.</span></span>

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

<span data-ttu-id="4dd55-192">アンカーのデータ ストリームを受信するため、コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-192">Here's our code for receiving the anchor data stream.</span></span> <span data-ttu-id="4dd55-193">ここでも、私たちは最初のバイト ストリームからの読み込み;この操作は、ネットワークからその量のバイトを受信する、StreamSocket が待機するように完了した時間がかかる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4dd55-193">Again, we will first load the bytes from the stream; this operation may take some time to complete as the StreamSocket waits to receive that amount of bytes from the network.</span></span>

<span data-ttu-id="4dd55-194">読み込み操作が完了したら、そのバイト数を読むことができます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-194">When the loading operation is complete, we can read that number of bytes.</span></span> <span data-ttu-id="4dd55-195">一歩踏み込んで、アンカー データをインポートできる予定アンカー データ ストリームのバイト数を受信した場合それ以外の場合は、する必要がありますがあったなんらかのエラー。</span><span class="sxs-lookup"><span data-stu-id="4dd55-195">If we received the number of bytes that we expect for the anchor data stream, we can go ahead and import the anchor data; if not, there must have been some sort of error.</span></span> <span data-ttu-id="4dd55-196">たとえば、データ ストリームの送信を完了できるまたはクライアントでは、全体のデータ ストリームを受信できる前に、ネットワークがダウンする前に、サーバー インスタンスの終了時にこれことができます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-196">For example, this can happen when the server instance terminates before it can finish sending the data stream, or the network goes down before the entire data stream can be received by the client.</span></span>

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

<span data-ttu-id="4dd55-197">ここでも、不明なネットワーク エラーを処理する準備をする必要があります予定です。</span><span class="sxs-lookup"><span data-stu-id="4dd55-197">Again, we must be prepared to handle unknown network errors.</span></span>

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

<span data-ttu-id="4dd55-198">以上で作業は終了です。</span><span class="sxs-lookup"><span data-stu-id="4dd55-198">That's it!</span></span> <span data-ttu-id="4dd55-199">次に、十分な情報をネットワーク経由で受信したアンカー配置することが必要です。</span><span class="sxs-lookup"><span data-stu-id="4dd55-199">Now, you should have enough information to try locating the anchors received over the network.</span></span> <span data-ttu-id="4dd55-200">ここでも、クライアントはアンカー; を正常に配置する領域の場合は、十分なビジュアルの追跡データである必要がありますに注意してください。すぐに、うまくいかない場合は、しばらくの間を歩きながらお試しください。</span><span class="sxs-lookup"><span data-stu-id="4dd55-200">Again, note that the client must have enough visual tracking data for the space to successfully locate the anchor; if it doesn't work right away, try walking around for a while.</span></span> <span data-ttu-id="4dd55-201">それでもうまくいかない場合は、複数のアンカーを送信し、ネットワーク通信を使用して、クライアントが適していることに同意のサーバーを用意します。</span><span class="sxs-lookup"><span data-stu-id="4dd55-201">If it still doesn't work, have the server send more anchors, and use network communications to agree on one that works for the client.</span></span> <span data-ttu-id="4dd55-202">この設定は、HolographicSpatialAnchorTransferSample をダウンロード、クライアントおよびサーバーの Ip 構成、クライアントとサーバーの HoloLens デバイスにデプロイして、利用できます。</span><span class="sxs-lookup"><span data-stu-id="4dd55-202">You can try this out by downloading the HolographicSpatialAnchorTransferSample, configuring your client and server IPs, and deploying it to client and server HoloLens devices.</span></span>

## <a name="see-also"></a><span data-ttu-id="4dd55-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="4dd55-203">See also</span></span>
* [<span data-ttu-id="4dd55-204">並列パターン ライブラリ (PPL)</span><span class="sxs-lookup"><span data-stu-id="4dd55-204">Parallel Patterns Library (PPL)</span></span>](https://msdn.microsoft.com/library/dd492418.aspx)
* [<span data-ttu-id="4dd55-205">Windows.Networking.StreamSocket</span><span class="sxs-lookup"><span data-stu-id="4dd55-205">Windows.Networking.StreamSocket</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [<span data-ttu-id="4dd55-206">Windows.Networking.StreamSocketListener</span><span class="sxs-lookup"><span data-stu-id="4dd55-206">Windows.Networking.StreamSocketListener</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
