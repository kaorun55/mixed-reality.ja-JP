---
title: Unreal でのデバイスへのデプロイ
description: 非 Real から HoloLens 2 にデバイスを展開するためのガイド
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、mixed reality、デバイスへのデプロイ、PC、ドキュメント
appliesto:
- HoloLens 2
ms.openlocfilehash: 2d0cd67db79c1970695334d826fbbaf0f2f92ec0
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408180"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="c2f0b-104">Unreal でのデバイスへのデプロイ</span><span class="sxs-lookup"><span data-stu-id="c2f0b-104">Deploy to device in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="c2f0b-105">概要</span><span class="sxs-lookup"><span data-stu-id="c2f0b-105">Overview</span></span>
<span data-ttu-id="c2f0b-106">HoloLens 2 に Unreal アプリケーションを展開するには、次の2つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-106">There are two ways to deploy an Unreal application to HoloLens 2:</span></span> 
* <span data-ttu-id="c2f0b-107">Unreal エディターから直接</span><span class="sxs-lookup"><span data-stu-id="c2f0b-107">Directly from the Unreal editor</span></span>
* <span data-ttu-id="c2f0b-108">デバイスポータルを使用してアップロードされたパッケージとして</span><span class="sxs-lookup"><span data-stu-id="c2f0b-108">As a package uploaded via the device portal</span></span>

<span data-ttu-id="c2f0b-109">どちらのオプションでも、開発用の[デバイスポータル](using-the-windows-device-portal.md)を使用するように HoloLens を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-109">Both options require you to set up your HoloLens to use the [device portal](using-the-windows-device-portal.md) for development.</span></span> 

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="c2f0b-110">Unreal エディターからデバイスへの配置</span><span class="sxs-lookup"><span data-stu-id="c2f0b-110">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="c2f0b-111">[**起動**] ボタンの横にあるドロップダウン矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-111">Click the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="c2f0b-112">最初は、HoloLens デバイスオプションが淡色表示になります。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-112">Initially, the HoloLens device option will be grayed out.</span></span>

![起動ドロップダウンオプション](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="c2f0b-114">**デバイスマネージャー**を開きます。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-114">Open the **Device Manager**.</span></span> <span data-ttu-id="c2f0b-115">HoloLens はデバイスの一覧に自動的に表示されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-115">Note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="c2f0b-116">[**一覧にないデバイスの追加**] セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-116">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="c2f0b-117">**プラットフォーム**として**HoloLens**を選択します。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-117">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="c2f0b-118">デバイスの IP アドレスとポート情報を、デバイス id としてコロンで区切って入力します。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-118">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="c2f0b-119">たとえば、"127.0.0.1: 10080" (USB 経由で接続されている場合) などです。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-119">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="c2f0b-120">デバイスポータルのユーザー名とパスワードの資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-120">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="c2f0b-121">[**追加**] をクリックし、デバイスマネージャーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-121">Hit **Add** and close the device manager.</span></span> 
    * <span data-ttu-id="c2f0b-122">エラー (アドレス、ユーザー名、パスワードなど) が間違っている場合は、メッセージが出力ログに出力されます。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-122">In the case of an error (such as wrong address, user name or password), a message will be printed to the Output Log.</span></span>

![一覧にないデバイスの追加](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="c2f0b-124">[**起動**] ボタンの横にあるドロップダウン矢印をもう一度クリックすると、追加した HoloLens デバイスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-124">Click the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="c2f0b-125">Hololens にビルドしてデプロイする HoloLens デバイスを選択します。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-125">Select the HoloLens device to build and deploy to your HoloLens.</span></span> 

>[!NOTE]
><span data-ttu-id="c2f0b-126">デバイスのビルドには、シェーダーの再コンパイルが含まれる場合があります (特に最初の実行時)。これには時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-126">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="c2f0b-127">デバイスは、アプリが実行されるまでスリープ状態にならないようにしてください (磨耗が必要な場合があります)。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-127">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="c2f0b-128">それ以外の場合、シェーダーのコンパイルは失敗します。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-128">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="c2f0b-129">デバイスポータルを使用したデバイスへの展開</span><span class="sxs-lookup"><span data-stu-id="c2f0b-129">Deploying to device via device portal</span></span>

<span data-ttu-id="c2f0b-130">[アプリのパッケージ化とデプロイ](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)に関する詳細な手順については、「unreal チュートリアルシリーズを使用したはじめに」の最後のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2f0b-130">You can find detailed instructions on [packaging and deploying an app](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) in the last section of the Getting Started with Unreal tutorial series.</span></span>
