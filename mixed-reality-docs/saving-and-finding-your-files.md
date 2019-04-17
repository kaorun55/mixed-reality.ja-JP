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
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="b79d5-104">保存とファイルの検索</span><span class="sxs-lookup"><span data-stu-id="b79d5-104">Saving and finding your files</span></span>

<span data-ttu-id="b79d5-105">ファイルの保存し、その他の Windows 10 デスクトップおよびモバイル デバイスと同様の方法で管理されていることができます。</span><span class="sxs-lookup"><span data-stu-id="b79d5-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="b79d5-106">ファイル エクスプ ローラーのアプリを使用してローカル フォルダーにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="b79d5-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="b79d5-107">アプリの独自の記憶域内</span><span class="sxs-lookup"><span data-stu-id="b79d5-107">Within an app's own storage</span></span>
* <span data-ttu-id="b79d5-108">で特別な既知のフォルダー (など、ビデオや音楽ライブラリ)</span><span class="sxs-lookup"><span data-stu-id="b79d5-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="b79d5-109">(OneDrive など) のアプリやファイル ピッカーを含むストレージ サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="b79d5-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="b79d5-110">MTP (Media Transfer Protocol) のサポートを使用して、HoloLens、usb に接続されているデスクトップ PC を使用します。</span><span class="sxs-lookup"><span data-stu-id="b79d5-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="b79d5-111">エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="b79d5-111">File Explorer</span></span>

<span data-ttu-id="b79d5-112">エクスプ ローラーのアプリを使用するには移動および HoloLens 内からファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="b79d5-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="b79d5-113">ファイル エクスプ ローラー内のファイルが見つからない場合は、「最近」フィルターがアクティブな可能性があります (時計のアイコンが左側のウィンドウで強調表示されます)。</span><span class="sxs-lookup"><span data-stu-id="b79d5-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="b79d5-114">これを解決するには、選択、**このデバイスを**(下に時計アイコン) で、左側のウィンドウでアイコンのドキュメントまたはメニューを開き、選択**このデバイスを**します。</span><span class="sxs-lookup"><span data-stu-id="b79d5-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="b79d5-115">アプリ内のファイル</span><span class="sxs-lookup"><span data-stu-id="b79d5-115">Files within an app</span></span>

<span data-ttu-id="b79d5-116">アプリケーションでは、デバイス上のファイルを保存する場合は、それらにアクセスするアプリケーションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b79d5-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="b79d5-117">自分の写真/動画の検索</span><span class="sxs-lookup"><span data-stu-id="b79d5-117">Where are my photos/videos?</span></span>

<span data-ttu-id="b79d5-118">[実際のキャプチャを混合](mixed-reality-capture.md)写真やビデオは、デバイスのカメラ ロール フォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="b79d5-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="b79d5-119">使用してアクセスするには、[写真アプリ](see-your-photos.md#photos-app)します。</span><span class="sxs-lookup"><span data-stu-id="b79d5-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="b79d5-120">写真アプリを使用すると、写真やビデオを OneDrive に同期します。</span><span class="sxs-lookup"><span data-stu-id="b79d5-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="b79d5-121">写真やビデオの混在の実際のキャプチャ ページを介してをアクセスすることも、 [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture)します。</span><span class="sxs-lookup"><span data-stu-id="b79d5-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="b79d5-122">別のアプリからファイルを要求します。</span><span class="sxs-lookup"><span data-stu-id="b79d5-122">Requesting files from another app</span></span>

<span data-ttu-id="b79d5-123">アプリケーションがファイルの保存や経由で別のアプリからファイルを開くように要求できます[ファイル ピッカー](app-model.md#file-pickers)します。</span><span class="sxs-lookup"><span data-stu-id="b79d5-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="b79d5-124">既知のフォルダー</span><span class="sxs-lookup"><span data-stu-id="b79d5-124">Known folders</span></span>

<span data-ttu-id="b79d5-125">サポートされる、数は HoloLens[既知のフォルダー](app-model.md#known-folders)アプリへのアクセス許可を要求できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b79d5-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="b79d5-126">サービス内のファイル</span><span class="sxs-lookup"><span data-stu-id="b79d5-126">Files in a service</span></span>

<span data-ttu-id="b79d5-127">ファイルを保存 (またはファイルからのアクセス) にインストールされるように、サービス、サービスに関連付けられているアプリが。</span><span class="sxs-lookup"><span data-stu-id="b79d5-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="b79d5-128">ファイルを保存し、OneDrive からファイルにアクセスするためにインストールする必要があります、 [OneDrive アプリ](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)します。</span><span class="sxs-lookup"><span data-stu-id="b79d5-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="b79d5-129">MTP (メディア転送プロトコル)</span><span class="sxs-lookup"><span data-stu-id="b79d5-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="b79d5-130">同様に他のモバイル デバイスでは、HoloLens をデスクトップ PC に接続し、転送ツールを HoloLens ライブラリ (写真、ビデオ、ドキュメント) にアクセスする PC にファイル エクスプ ローラーを開きます。</span><span class="sxs-lookup"><span data-stu-id="b79d5-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="b79d5-131">明確にします。</span><span class="sxs-lookup"><span data-stu-id="b79d5-131">Clarifications</span></span>

* <span data-ttu-id="b79d5-132">HoloLens では、外部ハード ディスク ドライブまたは SD カードに接続することはできません。</span><span class="sxs-lookup"><span data-stu-id="b79d5-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="b79d5-133">[Windows 10 April 2018 HoloLens 用の更新プログラム (RS4)](release-notes-april-2018.md)HoloLens には、ファイル エクスプ ローラーには保存および管理デバイス上のファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b79d5-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="b79d5-134">ファイル エクスプ ローラーの追加は、(たとえば、保存、デバイスと OneDrive にファイル)、ファイル ピッカーを選択する機能も提供します。</span><span class="sxs-lookup"><span data-stu-id="b79d5-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
