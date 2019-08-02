---
title: カスタム Holographic リモート処理データチャネル
description: カスタムデータチャネルは、既に確立されている Holographic リモート処理接続を介してユーザーデータを送信するために使用できます。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: 9f7f20023d496412b331606e03d0c5110bb4864f
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718086"
---
# <a name="custom-holographic-remoting-data-channels"></a>カスタム Holographic リモート処理データチャネル

>[!NOTE]
>このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。

カスタムデータチャネルを使用して、確立されたリモート処理接続を介してカスタムデータを送信します。

>[!IMPORTANT]
>カスタムデータチャネルには、カスタムホストアプリとカスタムプレーヤーアプリが必要です。これは、2つのカスタムアプリ間の通信を可能にするためです。

>[!TIP]
>単純なピンポン方の例については、 [Holographic リモート処理サンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)内のホストとプレーヤーのサンプルを参照してください。 サンプル```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE```コードを有効にするには、samplehostmain .h/SamplePlayerMain ファイル内でコメントを解除します。


# <a name="create-a-custom-data-channel"></a>カスタムデータチャネルを作成する


カスタムデータチャネルを作成するには、次のフィールドが必要です。
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

接続が正常に確立されると、ホスト側とプレーヤー側のどちらからでも、新しいデータチャネルの作成を開始できます。 Remotecontext と PlayerContext はどちらも、これ```CreateDataChannel()```を行うための方法を提供します。 最初のパラメーターは、susequent 操作でデータチャネルを識別するために使用されるチャネル ID です。 2番目のパラメーターは、このチャネルのデータを相手側に転送する優先度を指定する優先順位です。 チャネル Id の有効な範囲は、ホスト64側の場合は63、プレーヤー側の場合は127を含む0になります。 有効な優先```Low```順位```Medium```は```High``` 、、または (両側) です。

**ホスト**側でデータチャネルの作成を開始するには、次のようにします。
```cpp
// Valid channel ids for channels created on the host side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

**プレーヤー**側でデータチャネルの作成を開始するには、次のようにします。
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>新しいカスタムデータチャネルを作成するには、1つの```CreateDataChannel```側 (ホストまたはプレーヤー) だけがメソッドを呼び出す必要があります。

## <a name="handling-custom-data-channel-events"></a>カスタムデータチャネルイベントの処理

カスタムデータチャネル```OnDataChannelCreated```を確立するには、(プレーヤーとホスト側の両方で) イベントを処理する必要があります。 このメソッドは、ユーザーデータチャネルがいずれかの側で作成され```IDataChannel``` 、このチャネルを介してデータを送受信するために使用できるオブジェクトを提供するときにトリガーされます。

```OnDataChannelCreated```イベントにリスナーを登録するには、次のようにします。
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

データを受信したときに通知を受け取るに```OnDataReceived```は、 ```OnDataChannelCreated```ハンドラー ```IDataChannel```によって提供されるオブジェクトのイベントに登録します。 データチャネルが```OnClosed```閉じられたときに通知を受け取るには、イベントに登録します。

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a>データの送信

カスタムデータチャネルを介して```IDataChannel::SendData()```データを送信するには、メソッドを使用します。 1つ目のパラメーター ```winrt::array_view<const uint8_t>```は、送信する必要があるデータのです。 2番目のパラメーターは、もう一方の側が受信を承認するまで、データを再送信するかどうかを指定します。 

>[!IMPORTANT]
>ネットワークの状態が正しくない場合は、同じデータパケットが複数回到着する可能性があります。 受信コードでは、この状況に対処できる必要があります。

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>カスタムデータチャネルを閉じる

カスタムデータチャネルを閉じるには、 ```IDataChannel::Close()```メソッドを使用します。 カスタムデータチャネルが閉じられる```OnClosed```と、イベントによって両方の側に通知されます。

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>関連項目
* [Holographic Remoting ホストアプリの作成](holographic-remoting-create-host.md)
* [カスタム Holographic リモート処理プレーヤーアプリの作成](holographic-remoting-create-player.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic リモート処理ソフトウェアライセンス条項](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)