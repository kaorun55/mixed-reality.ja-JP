---
title: HoloLens で Wi-fi に接続する
description: HoloLens を使用してワイヤレスインターネットに接続する方法と、デバイスの IP アドレスを識別する方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens、wifi、ワイヤレス、インターネット、ip、ip アドレス
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670114"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>HoloLens で Wi-fi に接続する

HoloLens には、802.11 ac 対応、2x2 Wi-fi 無線が搭載されています。 HoloLens を Wi-fi ネットワークに接続することは、Windows 10 デスクトップまたはモバイルデバイスを Wi-fi ネットワークに接続することと似ています。

![HoloLens Wi-fi 設定](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>HoloLens で Wi-fi ネットワークに接続する

1. **[スタート]** メニューに[ブルーム](gestures.md#bloom)ます。
2. スタート メニューまたは スタート メニューの右側にある **すべてのアプリ** の一覧から、**設定** アプリを選択します。
3. **設定**アプリが自動的に前面に配置されます。
4. **[ネットワーク & インターネット]** を選択します。
5. Wi-Fi がオンになっていることを確認します。
6. 一覧から Wi-fi ネットワークを選択します。
7. Wi-fi ネットワークパスワードを入力します (必要な場合)。

## <a name="disabling-wi-fi-on-hololens"></a>HoloLens で Wi-fi を無効にする

### <a name="using-the-settings-app-on-hololens"></a>HoloLens で設定アプリを使用する

1. **[スタート]** メニューに[ブルーム](gestures.md#bloom)ます。
2. スタート メニューまたは スタート メニューの右側にある **すべてのアプリ** の一覧から、**設定** アプリを選択します。
3. **設定**アプリが自動的に前面に配置されます。
4. **[ネットワーク & インターネット]** を選択します。
5. Wi-fi スライダースイッチを選択して、"Off" の位置に移動します。 これにより、Wi-fi ラジオの RF コンポーネントがオフになり、HoloLens の Wi-fi 機能がすべて無効になります。 

    >[!WARNING]
    >HoloLens は、Wi-fi ラジオが無効になっている場合、[スペース](environment-considerations-for-hololens.md#WiFi fingerprint considerations)を自動的に読み込むことができません。
    
6. スライダースイッチを "オン" の位置に移動して Wi-fi ラジオをオンにし、Wi-fi 機能を Microsoft HoloLens に復元します。 選択した Wi-fi 無線の状態 ("オフ") は、再起動後も保持されます。

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>Wi-fi ネットワークに接続していることを確認する方法

1. [ブルーム](gestures.md#bloom)を開き、 **[スタート]** メニューを表示します。
2. Wi-fi ステータスの [スタート] メニューの左上を確認します。 Wi-fi の状態と、接続されているネットワークの SSID が表示されます。

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>Wi-fi ネットワーク上の HoloLens の IP アドレスを識別する

### <a name="using-the-settings-app"></a>設定アプリの使用

1. **[スタート]** メニューに[ブルーム](gestures.md#bloom)ます。
2. スタート メニューまたは スタート メニューの右側にある **すべてのアプリ** の一覧から、**設定** アプリを選択します。
3. **設定**アプリが自動的に前面に配置されます。
4. **[ネットワーク & インターネット]** を選択します。
5. 使用可能な Wi-fi ネットワークの一覧の下までスクロールし、 **[ハードウェアのプロパティ]** を選択します。

    ![Wi-fi 設定のハードウェアプロパティ](images/wifi-hololens-hwdetails.jpg)

IP アドレスは**IPv4 アドレス**の横に表示されます。

### <a name="using-cortana"></a>Cortana の使用

「*Cortana さん、私の IP アドレスを教えてください*」と言います。 また、Cortana によって IP アドレスが表示され、読み取られます。

### <a name="using-windows-device-portal"></a>Windows デバイスポータルの使用

1. PC の web ブラウザーで[デバイスポータル](using-the-windows-device-portal.md#networking)を開きます。
2. **[ネットワーク]** セクションに移動します。

IP アドレスとその他のネットワーク情報が表示されます。 この方法では、開発用 PC に IP アドレスを簡単にコピーして貼り付けることができます。
