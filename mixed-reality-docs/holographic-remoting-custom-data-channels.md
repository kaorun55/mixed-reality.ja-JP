---
title: カスタム Holographic リモート処理データチャネル
description: カスタムデータチャネルは、既に確立されている Holographic リモート処理接続を介してユーザーデータを送信するために使用できます。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: a862fa52695c7bfb94b58c6c0b85606a112835da
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434277"
---
# <a name="custom-holographic-remoting-data-channels"></a>カスタム Holographic リモート処理データチャネル

>[!NOTE]
>このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。

カスタムデータチャネルを使用して、確立されたリモート処理接続を介してカスタムデータを送信します。

>[!IMPORTANT]
>カスタムデータチャネルには、カスタムホストアプリとカスタムプレーヤーアプリが必要です。これは、2つのカスタムアプリ間の通信を可能にするためです。

>[!TIP]
>単純なピンポン方の例については、 [Holographic リモート処理サンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)内のホストとプレーヤーのサンプルを参照してください。 サンプルコードを有効にするには、SampleHostMain ファイル内の ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` をコメント解除します。


## <a name="create-a-custom-data-channel"></a>カスタムデータチャネルを作成する


カスタムデータチャネルを作成するには、次のフィールドが必要です。
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

接続が正常に確立されると、ホスト側とプレーヤー側のどちらからでも、新しいデータチャネルの作成を開始できます。 RemoteContext と PlayerContext はどちらも、これを行うための ```CreateDataChannel()``` 方法を提供します。 最初のパラメーターは、susequent 操作でデータチャネルを識別するために使用されるチャネル ID です。 2番目のパラメーターは、このチャネルのデータを相手側に転送する優先度を指定する優先順位です。 チャネル Id の有効な範囲は、ホスト64側の場合は63、プレーヤー側の場合は127を含む0になります。 有効な優先順位は、```Low```、```Medium``` または ```High``` (両側) です。

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
>新しいカスタムデータチャネルを作成するには、1つの側 (ホストまたはプレーヤー) だけが ```CreateDataChannel``` メソッドを呼び出す必要があります。

## <a name="handling-custom-data-channel-events"></a>カスタムデータチャネルイベントの処理

カスタムデータチャネルを確立するには、(プレーヤーとホスト側の両方で) ```OnDataChannelCreated``` イベントを処理する必要があります。 このメソッドは、ユーザーデータチャネルがいずれかの側で作成されたときにトリガーされ、```IDataChannel``` オブジェクトを提供します。このオブジェクトを使用して、このチャネルでデータを送受信できます。

```OnDataChannelCreated``` イベントにリスナーを登録するには、次のようにします。
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

データを受信したときに通知を受け取るには、```OnDataChannelCreated``` ハンドラーによって提供される ```IDataChannel``` オブジェクトの ```OnDataReceived``` イベントに登録します。 データチャネルが閉じられたときに通知を受け取るには、```OnClosed``` イベントに登録します。

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

カスタムデータチャネルを介してデータを送信するには、```IDataChannel::SendData()``` メソッドを使用します。 最初のパラメーターは、送信する必要があるデータへの ```winrt::array_view<const uint8_t>``` です。 2番目のパラメーターは、もう一方の側が受信を承認するまで、データを再送信するかどうかを指定します。 

>[!IMPORTANT]
>ネットワークの状態が正しくない場合は、同じデータパケットが複数回到着する可能性があります。 受信コードでは、この状況に対処できる必要があります。

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>カスタムデータチャネルを閉じる

カスタムデータチャネルを閉じるには、```IDataChannel::Close()``` メソッドを使用します。 カスタムデータチャネルが閉じられると、両方の側に ```OnClosed``` イベントによって通知されます。

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>参照
* [Holographic Remoting ホストアプリの作成](holographic-remoting-create-host.md)
* [カスタム Holographic リモート処理プレーヤーアプリの作成](holographic-remoting-create-player.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic Remoting ソフトウェア ライセンス条項](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
