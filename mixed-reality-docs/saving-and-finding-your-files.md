---
title: 保存とファイルの検索
description: 検索、保存、および HoloLens のファイルを共有する方法。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: 操作方法、ファイル ピッカー、ファイル、写真、ビデオ、画像、OneDrive、ストレージ、ファイル エクスプ ローラー
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602684"
---
# <a name="saving-and-finding-your-files"></a>保存とファイルの検索

ファイルの保存し、その他の Windows 10 デスクトップおよびモバイル デバイスと同様の方法で管理されていることができます。
* ファイル エクスプ ローラーのアプリを使用してローカル フォルダーにアクセスするには
* アプリの独自の記憶域内
* で特別な既知のフォルダー (など、ビデオや音楽ライブラリ)
* (OneDrive など) のアプリやファイル ピッカーを含むストレージ サービスを使用します。
* MTP (Media Transfer Protocol) のサポートを使用して、HoloLens、usb に接続されているデスクトップ PC を使用します。

## <a name="file-explorer"></a>エクスプローラー

エクスプ ローラーのアプリを使用するには移動および HoloLens 内からファイルを削除します。

>[!NOTE]
>ファイル エクスプ ローラー内のファイルが見つからない場合は、「最近」フィルターがアクティブな可能性があります (時計のアイコンが左側のウィンドウで強調表示されます)。 これを解決するには、選択、**このデバイスを**(下に時計アイコン) で、左側のウィンドウでアイコンのドキュメントまたはメニューを開き、選択**このデバイスを**します。

## <a name="files-within-an-app"></a>アプリ内のファイル

アプリケーションでは、デバイス上のファイルを保存する場合は、それらにアクセスするアプリケーションを使用できます。

### <a name="where-are-my-photosvideos"></a>自分の写真/動画の検索

[実際のキャプチャを混合](mixed-reality-capture.md)写真やビデオは、デバイスのカメラ ロール フォルダーに保存されます。 使用してアクセスするには、[写真アプリ](see-your-photos.md#photos-app)します。 写真アプリを使用すると、写真やビデオを OneDrive に同期します。 写真やビデオの混在の実際のキャプチャ ページを介してをアクセスすることも、 [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture)します。

### <a name="requesting-files-from-another-app"></a>別のアプリからファイルを要求します。

アプリケーションがファイルの保存や経由で別のアプリからファイルを開くように要求できます[ファイル ピッカー](app-model.md#file-pickers)します。

## <a name="known-folders"></a>既知のフォルダー

サポートされる、数は HoloLens[既知のフォルダー](app-model.md#known-folders)アプリへのアクセス許可を要求できるようにします。

## <a name="files-in-a-service"></a>サービス内のファイル

ファイルを保存 (またはファイルからのアクセス) にインストールされるように、サービス、サービスに関連付けられているアプリが。 ファイルを保存し、OneDrive からファイルにアクセスするためにインストールする必要があります、 [OneDrive アプリ](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)します。

## <a name="mtp-media-transfer-protocol"></a>MTP (メディア転送プロトコル)

同様に他のモバイル デバイスでは、HoloLens をデスクトップ PC に接続し、転送ツールを HoloLens ライブラリ (写真、ビデオ、ドキュメント) にアクセスする PC にファイル エクスプ ローラーを開きます。

## <a name="clarifications"></a>明確にします。

* HoloLens では、外部ハード ディスク ドライブまたは SD カードに接続することはできません。
* [Windows 10 April 2018 HoloLens 用の更新プログラム (RS4)](release-notes-april-2018.md)HoloLens には、ファイル エクスプ ローラーには保存および管理デバイス上のファイルが含まれています。 ファイル エクスプ ローラーの追加は、(たとえば、保存、デバイスと OneDrive にファイル)、ファイル ピッカーを選択する機能も提供します。
