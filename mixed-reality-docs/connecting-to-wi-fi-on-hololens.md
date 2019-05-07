---
title: HoloLens の Wi-fi に接続します。
description: HoloLens でワイヤレス インターネットに接続する方法とデバイスの IP アドレスを識別する方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, wifi, wireless, internet, ip, ip address
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670114"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>HoloLens の Wi-fi に接続します。

HoloLens には、802.11 ac が含まれています-対応、2 倍の 2 つの Wi-fi ラジオします。 HoloLens の Wi-fi ネットワークに接続することは、Windows 10 デスクトップまたはモバイル デバイスの Wi-fi ネットワークに接続に似ています。

![HoloLens の Wi-fi 設定](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>HoloLens の Wi-fi ネットワークに接続します。

1. [「Bloom](gestures.md#bloom)を、**開始**メニュー。
2. 選択、**設定**または開始からアプリ、**すべてのアプリ**スタート メニューの右側の一覧。
3. **設定**アプリは自動的に配置する前になります。
4. 選択**ネットワークとインターネット**します。
5. Wi-Fi がオンになっていることを確認します。
6. Wi-fi ネットワークを一覧から選択します。
7. (必要に応じて)、Wi-fi ネットワーク パスワードを入力します。

## <a name="disabling-wi-fi-on-hololens"></a>HoloLens で Wi-fi を無効にします。

### <a name="using-the-settings-app-on-hololens"></a>HoloLens で、設定アプリを使用します。

1. [「Bloom](gestures.md#bloom)を、**開始**メニュー。
2. 選択、**設定**または開始からアプリ、**すべてのアプリ**スタート メニューの右側の一覧。
3. **設定**アプリは自動的に配置する前になります。
4. 選択**ネットワークとインターネット**します。
5. [オフ] の位置に移動する Wi-fi スライダー スイッチを選択します。 Wi-fi ラジオの RF コンポーネントをオフにされ HoloLens ですべての Wi-fi 機能を無効にします。 

    >[!WARNING]
    >HoloLens を自動的にロードすることにすることはできません、[スペース](environment-considerations-for-hololens.md#WiFi fingerprint considerations)Wi-fi オプションが無効になっています。
    
6. スライダーのスイッチを Wi-fi オプションをオンにし、Microsoft HoloLens で Wi-fi 機能を復元"On"の位置に移動します。 選択した Wi-fi ラジオ状態 (「オン」の"Off") が再起動後も保持されます。

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>Wi-fi ネットワークに接続していることを確認する方法

1. [「Bloom](gestures.md#bloom)を起動、**開始**メニュー。
2. 上部で、Wi-fi の状態の [スタート] メニューのままにします。 状態の Wi Fi と接続されたネットワークの SSID が表示されます。

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>HoloLens、Wi-fi ネットワーク上の IP アドレスを識別します。

### <a name="using-the-settings-app"></a>[設定] アプリを使用します。

1. [「Bloom](gestures.md#bloom)を、**開始**メニュー。
2. 選択、**設定**または開始からアプリ、**すべてのアプリ**スタート メニューの右側の一覧。
3. **設定**アプリは自動的に配置する前になります。
4. 選択**ネットワークとインターネット**します。
5. 使用可能な Wi-fi ネットワークの一覧の下まで下へスクロールし、選択**ハードウェア プロパティ**します。

    ![Wi-fi 設定のハードウェア プロパティ](images/wifi-hololens-hwdetails.jpg)

IP アドレスが横に表示される**IPv4 アドレス**します。

### <a name="using-cortana"></a>Cortana を使ってください。

たとえば"*Hey Cortana、自分の IP アドレスは何ですか?*" Cortana が表示され、IP アドレスを読み取る。

### <a name="using-windows-device-portal"></a>Windows Device Portal を使用します。

1. 開く、[デバイス ポータル](using-the-windows-device-portal.md#networking)PC の web ブラウザーでします。
2. 移動し、**ネットワーク**セクション。

自分の IP アドレスとその他のネットワークの情報が表示されますがあります。 このメソッドは、簡単なコピーと、開発 PC 上の IP アドレスの貼り付けをできます。
