---
title: ファイルの保存と検索
description: HoloLens でファイルを検索、保存、および共有する方法。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: 操作方法、ファイルピッカー、ファイル、写真、ビデオ、画像、OneDrive、ストレージ、ファイルエクスプローラー
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524603"
---
# <a name="saving-and-finding-your-files"></a>ファイルの保存と検索

ファイルは、他の Windows 10 デスクトップおよびモバイルデバイスと同様の方法で保存および管理できます。
* エクスプローラーアプリを使用してローカルフォルダーにアクセスする
* アプリ独自のストレージ内
* 特別な既知のフォルダー (ビデオや音楽ライブラリなど)
* アプリとファイルピッカー (OneDrive など) を含むストレージサービスを使用する
* MTP (メディア転送プロトコル) を使用して、USB 経由で HoloLens に接続されたデスクトップ PC を使用する

## <a name="file-explorer"></a>エクスプローラー

ファイルエクスプローラーアプリを使用して、HoloLens 内からファイルを移動したり、削除したりできます。

>[!NOTE]
>ファイルエクスプローラーにファイルが表示されない場合は、"最近" のフィルターがアクティブになっている可能性があります (時計のアイコンは左のウィンドウで強調表示されています)。 この問題を解決するには、左側のウィンドウ (時計のアイコンの下) で**このデバイス**ドキュメントアイコンを選択するか、メニューを開いて **[このデバイス]** を選択します。

## <a name="files-within-an-app"></a>アプリ内のファイル

アプリケーションがデバイスにファイルを保存する場合、そのアプリケーションを使用してファイルにアクセスできます。

### <a name="where-are-my-photosvideos"></a>写真/ビデオはどこにありますか。

[Mixed reality capture](mixed-reality-capture.md)の写真とビデオは、デバイスのカメラロールフォルダーに保存されます。 これらには、 [Photos アプリ](see-your-photos.md#photos-app)を使用してアクセスできます。 Photos アプリを使用して、写真とビデオを OneDrive に同期することができます。 また、 [Windows デバイスポータル](using-the-windows-device-portal.md#mixed-reality-capture)の [Mixed Reality キャプチャ] ページを使用して、写真やビデオにアクセスすることもできます。

### <a name="requesting-files-from-another-app"></a>別のアプリからのファイルの要求

アプリケーションは、ファイル[ピッカー](app-model.md#file-pickers)を使用して、ファイルを保存したり、別のアプリからファイルを開いたりするように要求できます。

## <a name="known-folders"></a>既知のフォルダー

HoloLens では、アプリがアクセス許可を要求できる[既知のフォルダー](app-model.md#known-folders)がいくつかサポートされています。

## <a name="files-in-a-service"></a>サービス内のファイル

サービスにファイルを保存する (またはファイルにアクセスする) には、サービスに関連付けられているアプリがインストールされている必要があります。 OneDrive のファイルにファイルを保存してファイルにアクセスするには、 [onedrive アプリ](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)をインストールする必要があります。

## <a name="mtp-media-transfer-protocol"></a>MTP (メディア転送プロトコル)

他のモバイルデバイスと同様に、HoloLens をデスクトップ PC に接続し、PC でファイルエクスプローラーを開き、HoloLens ライブラリ (写真、ビデオ、ドキュメント) にアクセスして転送ツールを簡単に使用できるようにします。

## <a name="clarifications"></a>うち

* HoloLens は、外部ハードドライブまたは SD カードへの接続をサポートしていません。
* [Hololens には、Windows 10 April 2018 Update (RS4)](release-notes-april-2018.md)の時点で、デバイス上のファイルを保存および管理するためのファイルエクスプローラーが含まれています。 ファイルエクスプローラーを追加すると、ファイルピッカーを選択できるようになります (たとえば、デバイスまたは OneDrive にファイルを保存することができます)。
