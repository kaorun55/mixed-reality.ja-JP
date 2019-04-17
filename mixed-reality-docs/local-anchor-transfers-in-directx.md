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
# <a name="local-anchor-transfers-in-directx"></a>DirectX では、ローカルのアンカー転送

使用できない状況で<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>、ローカルのアンカーの転送には、2 番目の HoloLens デバイスによってインポートされるアンカーをエクスポートする 1 つの HoloLens デバイスが有効にします。

>[!NOTE]
>ローカルのアンカー転送よりも堅牢性のアンカー再現率を提供する<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>、iOS および Android デバイスは、このアプローチではサポートされていないとします。

>[!NOTE]
>この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。  概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。

## <a name="transferring-spatial-anchors"></a>空間のアンカーを転送します。

Windows Mixed Reality を使用してデバイス間で空間アンカーを転送することができます、 [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)します。 この API では、世界では、その場所を検索するために必要なすべてのサポート センサー データをアンカーをバンドルし、別のデバイスでは、そのバンドルをインポートすることができます。 2 つ目のデバイスでアプリがそのアンカーをインポートすると、各アプリは現実の世界と同じ場所に表示されますが、空間のアンカーの座標システムの共有を使用してホログラムをレンダリングできます。

空間アンカーは、各種デバイス間で転送することはできません、たとえば HoloLens 空間アンカーできない可能性があります、イマーシブ ヘッドセットを使用して場所を特定できることに注意してください。  転送されたアンカーは、いない iOS または Android デバイスと互換性があります。

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>SpatialPerception 機能を使用するアプリをセットアップします。

アプリに使用できる前に、spatialPerception 機能を使用するアクセス許可を与える必要があります、 [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)します。 これは、機能は、機密情報を含めることが、その場所の近くで時間の経過と共に収集したセンサーのイメージを共有が含まれる空間アンカーを転送するため必要です。

アプリの package.appxmanifest ファイルでこの機能を宣言します。 次に例を示します。

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

機能に由来します**uap2**名前空間。 マニフェストでこの名前空間へのアクセスを取得するには、それを含める、 *xlmns*属性、&lt;パッケージ > 要素。 次に例を示します。

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**注:** アプリは、SpatialAnchor エクスポート/インポート Api にアクセスする前に、実行時に機能を要求する必要があります。 参照してください[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx)次の例では。

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>アンカーのデータをシリアル化、SpatialAnchorTransferManager をエクスポートして

ヘルパー関数がエクスポートするコード サンプルに含まれる (シリアル化) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)データ。 このエクスポート API には、文字列をアンカーに関連付けるキー/値ペアのコレクション内のすべてのアンカーがシリアル化します。

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

最初に、データ ストリームを設定する必要があります。 これにより、1 にします。)アプリ、および 2 によって所有されているバッファーにデータを格納するのに TryExportAnchorsAsync を使用します。)std::vector は、独自のメモリ バッファーには WinRT データ ストリームがエクスポートされたバイトのバッファー ストリームからデータを読み取る&lt;バイト >。

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

システムによってエクスポートされるアンカーを含め、空間データにアクセスするためのアクセス許可を依頼する必要があります。

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

アクセス許可を取得しています、アンカーは、エクスポート、データ ストリームを読むことができます。 ここでは、また DataReader とデータの読み取りに使用して、InputStream を作成する方法を示します。

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

ストリームからバイトを読んだ後は、独自のデータ バッファーに保存しましたにできますようになります。

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>アンカーのデータを SpatialAnchorTransferManager を使用して、システムにインポートすることによって逆シリアル化します。

ヘルパー関数は、以前エクスポートされたデータを読み込むコード サンプルに含まれます。 この逆シリアル化関数は、ネットワーク ソケットなどの別のソースからこのデータを先ほどする点を除いて、SpatialAnchorStore の説明のようなキーと値のペアのコレクションを提供します。 処理することができますとを使用して、オフラインのアプリでメモリに格納する前にこのデータに関する理由 (該当する場合) またはアプリの SpatialAnchorStore します。

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

最初に、アンカーのデータにアクセスするストリーム オブジェクトを作成する必要があります。 データが書き込まれる、バッファーから、システムのバッファーにバイト バッファーから SpatialAnchors としてシステムにアンカーを取得するという目標を実現するために、メモリ内のデータ ストリームに書き込みを行う DataWriter ので作成されます。

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

ここでも、アプリのアクセス許可、ユーザーの環境に関するプライベートな情報が含まれますアンカーの空間データをエクスポートすることを確認する必要があります。

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

アクセスが許可されている場合、システム データ ストリームにバイト バッファーから作成できます。

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

データ ストリームにバイトを格納するのに成功した場合、SpatialAnchorTransferManager を使用してそのデータをインポートする試すことができます。

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

データがインポートできる場合は、文字列をアンカーに関連付けるキー/値ペアのマップ ビューを取得します。 これを独自のメモリ内のデータ コレクションに読み込むをそのコレクションを使用してに関心を持っているアンカーを検索できます。

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

**注:** アンカーをインポートするには、必ずしもいってすぐに使用します。 アンカーが完全; の別のルーム、または別の物理的な場所である可能性があります。アンカーは、受信するデバイスには、アンカーが既知の現在の環境を基準と、アンカーの位置を復元するには、作成環境について visual 十分な情報まで、場所を特定できることができません。 クライアントの実装では、ライブ コンテンツの使用を続行する前に、ローカルの座標システムまたは参照フレームの基準としたアンカーを検索してみてください。 たとえば、アンカーを開始する場所を特定できるまでに定期的に、現在の座標系を基準としたアンカーを検索してみてください。

## <a name="special-considerations"></a>特別な考慮事項

[TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API では、複数[SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)同じ不透明なバイナリの blob にエクスポートします。 ただし、どのようなデータを 1 回の呼び出しで SpatialAnchor を 1 つまたは複数の SpatialAnchors をエクスポートするかどうかに応じて、blob が含まれます微妙な違いがあります。

### <a name="export-of-a-single-spatialanchor"></a>1 つ SpatialAnchor のエクスポート

Blob には、環境は、SpatialAnchor をインポートするデバイスで認識できるように、環境、SpatialAnchor ポインターの近くの表現が含まれています。 インポートが完了すると、新しい SpatialAnchor は同じデバイスにことができます。 ユーザーは、アンカーの付近に最近されたと仮定すると場所を特定できることが、SpatialAnchor にアタッチされているホログラムをレンダリングすることができます。 これらホログラム、SpatialAnchor のエクスポート元のデバイスでその同じ物理的な場所に表示されます。

![1 つ SpatialAnchor のエクスポート](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>複数の SpatialAnchors のエクスポート

単一 SpatialAnchor、エクスポートなど、blob には、指定したすべての SpatialAnchors ポインターの近くの環境の表現が含まれています。 さらに、blob を同じ物理領域に配置されている場合、含まれる SpatialAnchors 間の接続に関する情報を格納します。 つまり、2 つの近くにある SpatialAnchors がインポートされた場合、ホログラムに接続されている、 *2 番目*SpatialAnchor できれば、しなくても、デバイスでは、周りの環境のみが認識、*最初*SpatialAnchor、ため、2 つの SpatialAnchors 間で変換を計算するための十分なデータが blob に含まれています。 2 つの SpatialAnchors が個別にエクスポートされた場合 (2 つの個別 TryExportSpatialAnchors への呼び出し) はできないかもしれませんが 1 つ目にあるときに場所を特定できる 2 つ目の SpatialAnchor ホログラム接続、blob 内に含まれるための十分なデータが存在し、します。

![1 つの TryExportAnchorsAsync 呼び出しを使用してエクスポートする複数のアンカー](images/multipleanchors.png) ![各アンカーの別個の TryExportAnchorsAsync 呼び出しを使用してエクスポートする複数のアンカー](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>以下に例を示します。アンカーを Windows::Networking::StreamSocket を使用してデータを送信します。

ここでは、TCP ネットワーク経由で送信することでアンカーがエクスポートされたデータを使用する方法の例を提供します。 これは、HolographicSpatialAnchorTransferSample です。

WinRT StreamSocket クラスは、PPL タスクのライブラリを使用します。 ネットワークのエラーの場合は、再スローされる例外を使用して、チェーン内の次のタスクにエラーが返されます。 例外には、エラー状態を示す HRESULT が含まれています。

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>TCP で、Windows::Networking::StreamSocketListener を使用して、エクスポートされたアンカーのデータを送信するには

接続を待機しているサーバー インスタンスを作成します。

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

接続が受信したときに、アンカーのデータを送信するのにクライアント ソケットの接続を使用します。

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

これで、アンカーのエクスポートされたデータを格納するデータ ストリームを送信する開始ことができます。

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

ストリーム自体を送信することができます、私たちには、まずヘッダー パケットを送信する必要があります。 このヘッダーのパケットが長さの固定長にする必要があり。、アンカーのデータ ストリームはバイトの変数の配列の長さを指定する必要があります。場合はこの例ではないその他のヘッダーのデータを送信する、そのため、ヘッダー 4 バイト長と 32 ビット符号なし整数が含まれています。

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

(バイト単位) のストリームの長さが、クライアントに送信されたデータ ストリーム自体をソケットのストリームに書き込む続行できます。 これにより、クライアントに送信するアンカー ストア バイト。

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

このトピックで説明した、ネットワーク エラー ステータス メッセージを格納している例外を処理する準備をする必要があります予定。 デバッグ コンソールに例外情報を書き込むときの予期しないエラーでは、次のようにします。 計算結果は、コード サンプルが、接続を完了できない場合、またはアンカー データの送信を完了することがない場合の変更点に関する手がかりとなります。

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>TCP で、Windows::Networking::StreamSocket を使用して、エクスポートされたアンカーのデータを受信するには

最初に、サーバーに接続する必要があります。 このコード サンプルでは、作成して構成を StreamSocket、ソケット接続を使用してネットワーク データを取得するために使用できる DataReader を作成する方法を示します。

**注:** このサンプル コードを実行する場合は、構成し、クライアントを開始する前に、サーバーを起動することを確認します。

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

接続したら、サーバーがデータを送信する待機できます。 ストリームのデータ リーダーで LoadAsync を呼び出して、そいます。

受信バイト数の最初のセットは、前のセクションで説明されているアンカー データ ストリーム バイトの長さを示すヘッダー パケットには常にします。

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

...

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

ヘッダーのパケットを受け取って後、は、予想されるアンカー データのバイト数がわかっています。 それらのバイトをストリームから読み取ったに進むことができます。

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

アンカーのデータ ストリームを受信するため、コードを次に示します。 ここでも、私たちは最初のバイト ストリームからの読み込み;この操作は、ネットワークからその量のバイトを受信する、StreamSocket が待機するように完了した時間がかかる可能性があります。

読み込み操作が完了したら、そのバイト数を読むことができます。 一歩踏み込んで、アンカー データをインポートできる予定アンカー データ ストリームのバイト数を受信した場合それ以外の場合は、する必要がありますがあったなんらかのエラー。 たとえば、データ ストリームの送信を完了できるまたはクライアントでは、全体のデータ ストリームを受信できる前に、ネットワークがダウンする前に、サーバー インスタンスの終了時にこれことができます。

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

ここでも、不明なネットワーク エラーを処理する準備をする必要があります予定です。

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

以上で作業は終了です。 次に、十分な情報をネットワーク経由で受信したアンカー配置することが必要です。 ここでも、クライアントはアンカー; を正常に配置する領域の場合は、十分なビジュアルの追跡データである必要がありますに注意してください。すぐに、うまくいかない場合は、しばらくの間を歩きながらお試しください。 それでもうまくいかない場合は、複数のアンカーを送信し、ネットワーク通信を使用して、クライアントが適していることに同意のサーバーを用意します。 この設定は、HolographicSpatialAnchorTransferSample をダウンロード、クライアントおよびサーバーの Ip 構成、クライアントとサーバーの HoloLens デバイスにデプロイして、利用できます。

## <a name="see-also"></a>関連項目
* [並列パターン ライブラリ (PPL)](https://msdn.microsoft.com/library/dd492418.aspx)
* [Windows.Networking.StreamSocket](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [Windows.Networking.StreamSocketListener](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
