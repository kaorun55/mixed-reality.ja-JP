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
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="87471-104">ファイルの保存と検索</span><span class="sxs-lookup"><span data-stu-id="87471-104">Saving and finding your files</span></span>

<span data-ttu-id="87471-105">ファイルは、他の Windows 10 デスクトップおよびモバイルデバイスと同様の方法で保存および管理できます。</span><span class="sxs-lookup"><span data-stu-id="87471-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="87471-106">エクスプローラーアプリを使用してローカルフォルダーにアクセスする</span><span class="sxs-lookup"><span data-stu-id="87471-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="87471-107">アプリ独自のストレージ内</span><span class="sxs-lookup"><span data-stu-id="87471-107">Within an app's own storage</span></span>
* <span data-ttu-id="87471-108">特別な既知のフォルダー (ビデオや音楽ライブラリなど)</span><span class="sxs-lookup"><span data-stu-id="87471-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="87471-109">アプリとファイルピッカー (OneDrive など) を含むストレージサービスを使用する</span><span class="sxs-lookup"><span data-stu-id="87471-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="87471-110">MTP (メディア転送プロトコル) を使用して、USB 経由で HoloLens に接続されたデスクトップ PC を使用する</span><span class="sxs-lookup"><span data-stu-id="87471-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="87471-111">エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="87471-111">File Explorer</span></span>

<span data-ttu-id="87471-112">ファイルエクスプローラーアプリを使用して、HoloLens 内からファイルを移動したり、削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="87471-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="87471-113">ファイルエクスプローラーにファイルが表示されない場合は、"最近" のフィルターがアクティブになっている可能性があります (時計のアイコンは左のウィンドウで強調表示されています)。</span><span class="sxs-lookup"><span data-stu-id="87471-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="87471-114">この問題を解決するには、左側のウィンドウ (時計のアイコンの下) で**このデバイス**ドキュメントアイコンを選択するか、メニューを開いて **[このデバイス]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="87471-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="87471-115">アプリ内のファイル</span><span class="sxs-lookup"><span data-stu-id="87471-115">Files within an app</span></span>

<span data-ttu-id="87471-116">アプリケーションがデバイスにファイルを保存する場合、そのアプリケーションを使用してファイルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="87471-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="87471-117">写真/ビデオはどこにありますか。</span><span class="sxs-lookup"><span data-stu-id="87471-117">Where are my photos/videos?</span></span>

<span data-ttu-id="87471-118">[Mixed reality capture](mixed-reality-capture.md)の写真とビデオは、デバイスのカメラロールフォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="87471-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="87471-119">これらには、 [Photos アプリ](see-your-photos.md#photos-app)を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="87471-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="87471-120">Photos アプリを使用して、写真とビデオを OneDrive に同期することができます。</span><span class="sxs-lookup"><span data-stu-id="87471-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="87471-121">また、 [Windows デバイスポータル](using-the-windows-device-portal.md#mixed-reality-capture)の [Mixed Reality キャプチャ] ページを使用して、写真やビデオにアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="87471-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="87471-122">別のアプリからのファイルの要求</span><span class="sxs-lookup"><span data-stu-id="87471-122">Requesting files from another app</span></span>

<span data-ttu-id="87471-123">アプリケーションは、ファイル[ピッカー](app-model.md#file-pickers)を使用して、ファイルを保存したり、別のアプリからファイルを開いたりするように要求できます。</span><span class="sxs-lookup"><span data-stu-id="87471-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="87471-124">既知のフォルダー</span><span class="sxs-lookup"><span data-stu-id="87471-124">Known folders</span></span>

<span data-ttu-id="87471-125">HoloLens では、アプリがアクセス許可を要求できる[既知のフォルダー](app-model.md#known-folders)がいくつかサポートされています。</span><span class="sxs-lookup"><span data-stu-id="87471-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="87471-126">サービス内のファイル</span><span class="sxs-lookup"><span data-stu-id="87471-126">Files in a service</span></span>

<span data-ttu-id="87471-127">サービスにファイルを保存する (またはファイルにアクセスする) には、サービスに関連付けられているアプリがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="87471-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="87471-128">OneDrive のファイルにファイルを保存してファイルにアクセスするには、 [onedrive アプリ](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="87471-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="87471-129">MTP (メディア転送プロトコル)</span><span class="sxs-lookup"><span data-stu-id="87471-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="87471-130">他のモバイルデバイスと同様に、HoloLens をデスクトップ PC に接続し、PC でファイルエクスプローラーを開き、HoloLens ライブラリ (写真、ビデオ、ドキュメント) にアクセスして転送ツールを簡単に使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="87471-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="87471-131">うち</span><span class="sxs-lookup"><span data-stu-id="87471-131">Clarifications</span></span>

* <span data-ttu-id="87471-132">HoloLens は、外部ハードドライブまたは SD カードへの接続をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="87471-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="87471-133">[Hololens には、Windows 10 April 2018 Update (RS4)](release-notes-april-2018.md)の時点で、デバイス上のファイルを保存および管理するためのファイルエクスプローラーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="87471-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="87471-134">ファイルエクスプローラーを追加すると、ファイルピッカーを選択できるようになります (たとえば、デバイスまたは OneDrive にファイルを保存することができます)。</span><span class="sxs-lookup"><span data-stu-id="87471-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
