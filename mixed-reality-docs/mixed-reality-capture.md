---
title: 複合現実キャプチャ
description: Mixed reality キャプチャの使用に関する情報。
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: mrc, mixed reality capture, 写真, ビデオ, カメラ, キャプチャ, 使用法, ストリーム, ライブストリーム, デモ
ms.openlocfilehash: 7af60682f78f624e6b41ded88c8a77e70d40194c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694509"
---
# <a name="mixed-reality-capture"></a>複合現実キャプチャ

HoloLens を使用すると、ユーザーは世界とデジタルの世界を混在させることができます。 Mixed reality キャプチャ (MRC) を使用すると、写真またはビデオとしてそのエクスペリエンスをキャプチャできます。 これにより、表示されているホログラムを確認することで、他のユーザーとのエクスペリエンスを共有できます。 このようなビデオや写真は、最初の人の視点から見たものです。 3人の観点では、 [spectator view](spectator-view.md)を使用します。

混合現実のキャプチャのユースケースは、ソーシャルサークル間でビデオを共有することを超えています。 ビデオは、アプリの使用方法について他のユーザーに指示するために使用できます。 開発者は、ビデオまたは静止画を使用して、再現手順の改善とアプリエクスペリエンスのデバッグを行うことができます。

## <a name="live-streaming-from-hololens"></a>HoloLens からのライブストリーミング

[Windows 10 10 月2018更新プログラム](release-notes-october-2018.md)は、HoloLens のサポートを HoloLens に追加します。 スタート メニューの下部にある **接続** ボタンを選択して、Miracast が有効なデバイスとアダプターのピッカーを開きます。 ストリーミングを開始するデバイスを選択します。 完了したら、スタート メニューの下部にある **切断** ボタンを選択します。  [クイックアクション] メニューでは、**接続**と**切断**も使用できます。

[Windows デバイスポータル](using-the-windows-device-portal.md)と[Microsoft HoloLens コンパニオンアプリ](https://www.microsoft.com/store/productId/9NBLGGH4QWNX)では、開発者モードのデバイスのライブストリーミングオプションが公開されます。

[Dynamics 365 Remote Assist](https://dynamics.microsoft.com/en-us/mixed-reality/remote-assist)は、リモートの場所にある HoloLens から従業員へのライブストリーミングをサポートしています。

## <a name="taking-mixed-reality-captures"></a>混合現実のキャプチャの取得

![[スタート] メニューの下部にあるカメラアイコンをクリックします。](images/cameraiconinpins-300px.png)<br>
*[スタート] メニューの下部にあるカメラアイコンをクリックします。*

Mixed reality キャプチャを開始するには、次のような複数の方法があります。
* Cortana は、現在実行中のアプリに関係なく、常に使用できます。 「Cortana、写真を撮る」、または「Cortana さん、録音を開始する」と言ってみましょう。 ビデオを停止するには、「Cortana について、録画を停止する」と言います。
* スタート メニューで、**カメラ** または **ビデオ** を選択します。 [エアタップ](gestures.md#air-tap)を使用して、組み込みの MRC カメラ UI を開きます。
* クイックアクション メニューで、**カメラ** または **ビデオ** を選択して、組み込みの MRC カメラ UI を開きます。
* アプリは、カスタムまたはを使用して、mixed reality キャプチャ用に独自の UI を公開できます。これには、 [Windows 10 10 月2018更新プログラム](release-notes-october-2018.md)の[組み込みの MRC カメラ UI が含ま](mixed-reality-capture-for-developers.md)れます。
* HoloLens に固有: 
    * [Windows デバイスポータル](using-the-windows-device-portal.md)には、画像、ビデオ、ライブストリーム、およびビューのキャプチャを撮影するために使用できる mixed reality キャプチャページがあります。
    * 現在実行中のアプリに関係なく、 **[音量]** ボタンと **[音量]** ボタンの両方を同時に押して、画像を撮影します。
    * ビデオの録画を開始するには、 **[音量アップ]** ボタンと **[音量]** ボタンを3秒間押したままにします。 ビデオを停止するには、 **[volume up]** ボタンと **[volume down]** ボタンの両方を同時にタップします。
* イマーシブヘッドセットに固有: 
    * モーションコントローラーを使用して、**ウィンドウ**ボタンを押したまま、**トリガー**をタップして画像を撮影します。 
    * モーションコントローラーを使用して、 **Windows**のボタンを押したまま、**メニュー**ボタンをタップしてビデオの録画を開始します。 **Windows**ボタンを押したまま、**トリガー**をタップしてビデオ録画を停止します。
    
>[!NOTE]
>[Windows 10 10 月2018更新プログラム](release-notes-october-2018.md)は、ブルームと Windows のボタンの動作を変更します。 更新の前に、ブルームジェスチャまたは Windows ボタンは記録を停止します。 更新後、ブルームジェスチャまたは [Windows] ボタンをクリックすると、[スタート] メニュー (アプリ内にある場合は [クイックアクション] メニュー) が開きます。 メニューで、 **[ビデオの停止]** を選択して記録を停止します。

### <a name="limitations-of-mixed-reality-capture"></a>Mixed reality キャプチャの制限事項

HoloLens では、レンダーレートが30Hz に調整されます。 これにより、MRC を実行するためのヘッドルームが作成されます。これにより、アプリは一定の予算予約を維持する必要がなくなり、(最大 30 fps) の MRC ビデオレコードレートにも一致します。

ビデオの最大長は5分です。

組み込みの MRC カメラ UI では、一度に1つの MRC 操作しかサポートされていません (画像を撮影することは、ビデオの記録とは相互に排他的です)。

### <a name="file-formats"></a>ファイル形式

Cortana 音声コマンドからの Mixed reality キャプチャと [スタート] メニューツールは、次の形式でファイルを作成します。

|  種類  |  Format  |  拡張子  |  解決方法  |  オーディオ | 
|----------|----------|----------|----------|----------|
|  Photo  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  3904x2196px (HoloLens 2)<br> 1408x792px (HoloLens)<br> 1920x1080px (イマーシブヘッドセット) |  なし | 
|  Video  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1920x1080px 30 fps (HoloLens 2)<br> 1216x684px 24 fps (HoloLens)<br> 1632x918px 30 fps (イマーシブヘッドセット) |  48 Khz ステレオ | 

>[!NOTE]
>写真/ビデオカメラが既に別のアプリケーションによって使用されている場合、ライブストリーミング中、システムリソースが少ない場合は、写真やビデオの解像度を小さくすることができます。

### <a name="video-stabilization"></a>ビデオ安定化

既定では、次のようになります。
* ゼロ待機時間のビデオ安定化は、Miracast を介したライブストリーミングの場合に適用されます。
* 長い待機時間のビデオ安定化は、組み込みの MRC カメラ UI、Cortana 音声コマンド、Windows デバイスポータルを使用してキャプチャされたビデオに適用されます。

## <a name="viewing-mixed-reality-captures"></a>混合現実のキャプチャを表示する

Mixed reality capture の写真とビデオは、デバイスの "カメラロール" フォルダーに保存されます。 これらのファイルには、 [Photos アプリ](see-your-photos.md#photos-app)またはエクスプローラーを使用してアクセスできます。

HoloLens に接続されている PC では、 [Windows デバイスポータル](using-the-windows-device-portal.md#mixed-reality-capture)または Pc のエクスプローラー ([MTP 経由](release-notes-april-2018.md#new-features-for-hololens)) を使用することもできます。

[Onedrive アプリ](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3)をインストールすると、**カメラのアップロード**を有効にすることができます。また、デジタル写真やビデオが onedrive を使用して onedrive やその他のデバイスと同期します。

>[!NOTE]
>Windows 10 の2018年4月更新の時点で、写真アプリは OneDrive に写真やビデオをアップロードしなくなります。

## <a name="see-also"></a>関連項目
* [Spectator View](spectator-view.md)
* [場所を特定できるカメラ](locatable-camera.md)
* [開発者向け複合現実キャプチャ](mixed-reality-capture-for-developers.md)
* [写真を表示する](see-your-photos.md)
* [Windows Device Portal を使用する](using-the-windows-device-portal.md)
