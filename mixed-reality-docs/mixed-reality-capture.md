---
title: 複合現実キャプチャ
description: 複合現実のキャプチャの使用に関する情報です。
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: 実際のキャプチャ、写真、ビデオ、カメラ、キャプチャ、使用状況、ストリーム、ライブ ストリーム、デモを混合 mrc
ms.openlocfilehash: 18a80083bd25974905874c6c2ec0de87dc7424ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604138"
---
# <a name="mixed-reality-capture"></a>複合現実キャプチャ

HoloLens は、デジタルの世界で現実世界の混在のエクスペリエンスをユーザーに提供します。 複合現実のキャプチャ (MRC) を使用して、写真やビデオのいずれかとしてそのエクスペリエンスをキャプチャできます。 ご覧のように、ホログラムを表示することにより、他のユーザー エクスペリエンスを共有できます。 このようなビデオや写真は、最初のユーザーの観点からです。 3 人目の観点を使用して[spectator ビュー](spectator-view.md)します。

キャプチャの複合現実のユース ケースを超えるソーシャル円の間でのビデオを共有します。 ビデオは、他のユーザーにアプリを使用する方法の指示を使用できます。 開発者は、動画または静止画を使用してステップの再現を改善し、アプリのエクスペリエンスをデバッグすることができます。

## <a name="live-streaming-from-hololens"></a>ライブ ストリーミング HoloLens から

[Windows 10 年 2018年 10 月 Update](release-notes-october-2018.md) HoloLens に Miracast サポートを追加します。 選択、 **Connect** Miracast 対応デバイスおよびアダプターのピッカーを起動する [スタート] メニューの下部にあるボタンをクリックします。 ストリーミングを開始するデバイスを選択します。 完了したら、選択、**切断**[スタート] メニューの下部にあるボタンをクリックします。  **接続**と**切断**もクイック アクション メニューを使用します。 

[Windows Device Portal](using-the-windows-device-portal.md)公開ライブ開発モードではデバイスでストリーミング オプション。

## <a name="taking-mixed-reality-captures"></a>キャプチャ複合現実の取得

![[スタート] メニューの下部にあるカメラ アイコンをクリックします。](images/cameraiconinpins-300px.png)<br>
*[スタート] メニューの下部にあるカメラ アイコンをクリックします。*

複合現実のキャプチャを開始する複数の方法はあります。
* Cortana できますですべての時刻現在実行中のアプリに関係なく。 単に"Hey Cortana、写真を撮る"または」「コルタナさん記録を開始します。 ビデオを停止するには、たとえば"Hey Cortana、記録を停止します"。
* [スタート] メニューには、いずれかを選択**カメラ**または**ビデオ**します。 使用[エア タップ](gestures.md#air-tap)組み込み MRC カメラ UI を開きます。
* [クイック アクション] メニューには、いずれかを選択**カメラ**または**ビデオ**組み込み MRC カメラ UI を開きます。
* アプリにカスタムを使用して複合現実キャプチャまたは、独自の UI を公開することが、 [Windows 10 年 2018年 10 月 Update](release-notes-october-2018.md)、[組み込み MRC カメラ UI](mixed-reality-capture-for-developers.md)します。
* HoloLens に固有。 
    * [Windows Device Portal](using-the-windows-device-portal.md)写真、ビデオ、ライブ ストリームを使用でき、キャプチャを表示する複合現実キャプチャ ページがあります。
    * どちらもキーを押して、**をボリューム**と**音量下げる**に対して同時に、現在実行中のアプリに関係なく、写真を撮るボタン。
    * 保持、**音量上げる**と**音量下げる**3 秒のビデオ記録を開始するためのボタン。 ビデオを停止するには、両方をタップ**音量上げる**と**音量下げる**ボタンを同時にします。
* 没入型に固有のヘッドセット。 
    * 保持、モーションのコント ローラーを使用して、 **Windows**ボタンをクリックし、順にタップ、**トリガー**画像を撮影します。 
    * 保持、モーションのコント ローラーを使用して、 **Windows**ボタンをクリックし、タップ、**メニュー**ビデオの録音を開始するボタン。 押したまま、 **Windows**ボタンをクリックし をタップし、**トリガー**ビデオ録画を終了します。
    
>[!NOTE]
>[Windows 10 年 2018年 10 月 Update](release-notes-october-2018.md)ブルームや Windows のボタンの動作を変更します。 更新前に、ブルーム ジェスチャまたは Windows のボタンでは記録は停止されます。 更新の後ブルーム ジェスチャまたは [Windows]、[スタート] メニュー (またはアプリの場合は、[クイック アクション] メニュー) を開きます。 メニューで、次のように選択します。**停止ビデオ**録音を停止します。

### <a name="limitations-of-mixed-reality-capture"></a>複合現実のキャプチャの制限事項

HoloLens で、システムは 30 Hz にレンダリングされたレートを調整します。 これは MRC、アプリは、定数の予算の予約を保持する必要があるために実行するためのいくつかのヘッドルームを作成し、30 fps の MRC レコードのビデオ フレーム レートとも一致します。

ビデオでは、5 分間の最大長があります。

組み込みの MRC カメラ UI が、一度に 1 つ MRC 操作のみがサポートされます (写真撮影はビデオの録画を相互に排他的)。

### <a name="file-formats"></a>ファイル形式

Cortana 音声コマンドから複合現実をキャプチャし、[スタート] メニューのツールは、次の形式でファイルを作成します。

|  種類  |  表記  |  拡張  |  解決方法  |  オーディオ | 
|----------|----------|----------|----------|----------|
|  Photo  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  1408x792px (HoloLens) 1920 x 1080 ピクセル (イマーシブ ヘッドセット) |  なし | 
|  Video  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1408x792px (HoloLens) 1632x918px (イマーシブ ヘッドセット) |  48 kHz ステレオ | 

## <a name="viewing-mixed-reality-captures"></a>キャプチャ複合現実を表示します。

複合現実のキャプチャの写真やビデオは、デバイスの「カメラ ロール」フォルダーに保存されます。 使用してアクセスするには、[写真アプリ](see-your-photos.md#photos-app)またはファイル エクスプ ローラー。

HoloLens に接続されている pc で使用することも[Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture)または PC のファイル エクスプ ローラー ([MTP を使用して](release-notes-april-2018.md#new-features-for-hololens))。

インストールする場合、 [OneDrive アプリ](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3)、オンにする**カメラのアップロード、** と MRC 写真やビデオを OneDrive と OneDrive を使用して、その他のデバイスに同期されます。

>[!NOTE]
>時点では、Windows 10 April 2018 Update、写真アプリは不要になった、写真やビデオを OneDrive にアップロードします。

## <a name="see-also"></a>関連項目
* [Spectator ビュー](spectator-view.md)
* [場所を特定できるカメラ](locatable-camera.md)
* [開発者向けの実際のキャプチャの混在](mixed-reality-capture-for-developers.md)
* [写真を参照してください。](see-your-photos.md)
* [Windows Device Portal のを使用](using-the-windows-device-portal.md)
