---
title: MR とビデオのストリーミング - Azure 306
description: このコースでは、複合現実のアプリケーション内で Azure Media Services を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、メディア サービス、ストリーミング ビデオ、360、没入型、vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599484"
---
>[!NOTE]
><span data-ttu-id="4bc9e-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="4bc9e-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="4bc9e-106">これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="4bc9e-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="4bc9e-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="4bc9e-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="4bc9e-110">MR と Azure 306:ビデオのストリーミング</span><span class="sxs-lookup"><span data-stu-id="4bc9e-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="4bc9e-111">![最終的な製品-開始](images/AzureLabs-Lab6-00.png)
![最終製品-開始](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="4bc9e-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="4bc9e-112">このコースでは、学習イマーシブ ヘッドセットでビデオの再生を 360 度のストリーミングを許可する Windows Mixed Reality VR エクスペリエンスに、Azure Media Services を接続する方法。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="4bc9e-113">**Azure Media Services**は今日の最も人気のあるモバイル デバイスでより多くのユーザーに到達するブロードキャスト品質ビデオ ストリーミング サービスを提供するサービスのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="4bc9e-114">詳細については、次を参照してください。、 [Azure Media Services ページ](https://azure.microsoft.com/services/media-services)します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="4bc9e-115">このコースを完了するは、次のことが、複合現実イマーシブ ヘッドセット アプリケーションが用意されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="4bc9e-116">360 度のビデオを取得、 **Azure Storage**を使用して、 **Azure Media Service**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="4bc9e-117">Unity シーン内で取得した 360 度のビデオを表示します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="4bc9e-118">2 つの異なるビデオで、2 つのシーン間を移動します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="4bc9e-119">アプリケーションでは、責任ですが、設計と、結果を統合する方法について。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="4bc9e-120">このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="4bc9e-121">複合現実アプリを強化するためには、このコース得た知識を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="4bc9e-122">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="4bc9e-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4bc9e-123">コース</span><span class="sxs-lookup"><span data-stu-id="4bc9e-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="4bc9e-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="4bc9e-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="4bc9e-125"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="4bc9e-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="4bc9e-126">MR と Azure 306:ビデオのストリーミング</span><span class="sxs-lookup"><span data-stu-id="4bc9e-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="4bc9e-127">✔️</span><span class="sxs-lookup"><span data-stu-id="4bc9e-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="4bc9e-128">前提条件</span><span class="sxs-lookup"><span data-stu-id="4bc9e-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="4bc9e-129">このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="4bc9e-130">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 5 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="4bc9e-131">内に一覧表示するには自由に最新のソフトウェアを使用して、[インストール ツール記事](install-the-tools.md)ことについては、このコースでとまったく同じで見つかりますの下に記載されているものよりも新しいソフトウェアでどのようなことは仮定されませんが、.</span><span class="sxs-lookup"><span data-stu-id="4bc9e-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="4bc9e-132">次のハードウェアとソフトウェアこのコースをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="4bc9e-133">開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発</span><span class="sxs-lookup"><span data-stu-id="4bc9e-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="4bc9e-134">Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="4bc9e-135">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="4bc9e-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="4bc9e-136">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="4bc9e-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="4bc9e-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="4bc9e-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="4bc9e-138">A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="4bc9e-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="4bc9e-139">Azure のセットアップやデータの取得のためのインターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="4bc9e-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="4bc9e-140">Mp4 形式で 2 つの 360 度ビデオ (いくつか使用料無料のビデオを検索する[このダウンロードのページにある](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span><span class="sxs-lookup"><span data-stu-id="4bc9e-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="4bc9e-141">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="4bc9e-141">Before you start</span></span>

1.  <span data-ttu-id="4bc9e-142">このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="4bc9e-143">設定し、混合 Reality イマーシブ ヘッドセットをテストします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4bc9e-144">**いない**このコースのモーションのコント ローラーが必要です。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="4bc9e-145">イマーシブ ヘッドセットの設定をサポートする場合をクリックしてください[Windows Mixed Reality を設定する方法についてのリンク](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="4bc9e-146">1 - Azure Portal の章: Azure ストレージ アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="4bc9e-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="4bc9e-147">使用する、 **Azure ストレージ サービス**、作成および構成する必要があります、**ストレージ アカウント**Azure portal でします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="4bc9e-148">[Azure ポータル](https://portal.azure.com) にログインします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="4bc9e-149">Azure アカウントがいない場合は、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="4bc9e-150">クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="4bc9e-151">ログインした後は、をクリックして**ストレージ アカウント**左側のメニュー。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="4bc9e-153">**ストレージ アカウント** タブで、をクリックして**追加**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="4bc9e-155">**ストレージ アカウントを作成する** タブ。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="4bc9e-156">挿入、**名前**お使いのアカウントに、数字と小文字のみこのフィールドを受け入れるに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="4bc9e-157">**デプロイ モデルでは、** 選択**Resource manager**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="4bc9e-158">**アカウントの種類**、**ストレージ (汎用 v1)** します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="4bc9e-159">**パフォーマンス**、 **Standard\*。**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="4bc9e-160">**レプリケーション**選択**ローカル冗長ストレージ (LRS)** します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="4bc9e-161">まま**転送が必須のセキュリティで保護された**として**無効になっている**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="4bc9e-162">選択、**サブスクリプション**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="4bc9e-163">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="4bc9e-164">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="4bc9e-165">確認、**場所**(新しいリソース グループを作成する) 場合は、リソース グループ。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="4bc9e-166">場所は、アプリケーションが実行リージョンにあるが理想的です。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="4bc9e-167">一部の Azure 資産は特定のリージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="4bc9e-168">このサービスに適用される条件を読んで理解したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="4bc9e-170">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="4bc9e-171">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="4bc9e-173">この時点で次のリソースは、[次へ] の章に進みます。 単純にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="4bc9e-174">2 - Azure Portal の章: メディア サービスの作成</span><span class="sxs-lookup"><span data-stu-id="4bc9e-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="4bc9e-175">Azure メディア サービスを使用するには、(アカウント保有者が必要管理者である場合)、アプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="4bc9e-176">Azure Portal をクリックして**リソースの作成**左上隅にある検索して**メディア サービス、** キーを押して **」と入力**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="4bc9e-177">現在、目的のリソースがピンク色のアイコン。この新しいページを表示する をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="4bc9e-179">新しいページがの説明を入力、**メディア サービス**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="4bc9e-180">このダイアログ ボックスの左下にある at をクリックして、**作成**ボタンは、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="4bc9e-182">クリックすると**作成**新しいメディア サービスについての詳細を提供する必要があるパネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="4bc9e-183">必要な挿入**アカウント名**このサービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="4bc9e-184">選択、**サブスクリプション**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="4bc9e-185">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="4bc9e-186">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="4bc9e-187">勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="4bc9e-188">詳細にする場合は、Azure リソース グループに従ってくださいこの[Azure リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="4bc9e-189">確認、**場所**(新しいリソース グループを作成する) 場合は、リソース グループ。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="4bc9e-190">場所は、アプリケーションが実行リージョンにあるが理想的です。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="4bc9e-191">一部の Azure 資産は特定のリージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="4bc9e-192">**ストレージ アカウント**セクションで、、**を選択してください.** セクションで、クリック、**ストレージ アカウント**最後の章で作成しました。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="4bc9e-193">また、このサービスに適用される条件を理解したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="4bc9e-194">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-194">Click **Create**.</span></span>

        ![Azure Portal](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="4bc9e-196">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="4bc9e-197">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="4bc9e-199">新しいサービス インスタンスを探索する通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-199">Click on the notification to explore your new Service instance.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="4bc9e-201">をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="4bc9e-202">新しいメディア サービス ページの左側で、パネル内では、をクリックして、**資産**偶数の一覧については、リンク。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="4bc9e-203">次のページで、ページの左上隅にある クリックして**アップロード**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="4bc9e-205">をクリックして、**フォルダー**アイコン ファイルを参照し、最初に 360 ビデオをストリーミングしたいを選択します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="4bc9e-206">これを利用できる[サンプル ビデオをダウンロードするリンク](https://vimeo.com/214401712)します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="4bc9e-208">長いファイル名は、エンコーダーで問題を生じさせる可能性があります: ためにビデオの問題がないことを確認するには、ビデオ ファイル名の長さを短縮することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="4bc9e-209">ビデオのアップロードが完了すると、進行状況バーが緑色になります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="4bc9e-211">上記のテキストをクリックして (**yourservicename - 資産**) に戻る、**資産**ページ。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="4bc9e-212">ビデオが正常にアップロードされていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="4bc9e-213">これをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-213">Click on it.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="4bc9e-215">ビデオに関する詳細情報にリダイレクトされるページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="4bc9e-216">をクリックして、エンコードする必要がある、ビデオを使用できる、**エンコード**ページの上部左にあるボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="4bc9e-218">いることができます、ファイルのオプションのエンコーディングを設定する右側で、新しいパネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="4bc9e-219">(一部は既に既定で設定)、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="4bc9e-220">**メディア エンコーダー名\*Media Encoder Standard**\*</span><span class="sxs-lookup"><span data-stu-id="4bc9e-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="4bc9e-221">**エンコード プリセット\*コンテンツ アダプティブ マルチビット レート MP4**\*</span><span class="sxs-lookup"><span data-stu-id="4bc9e-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="4bc9e-222">**ジョブ名\*Video1.mp4 の Media Encoder Standard の処理**\*</span><span class="sxs-lookup"><span data-stu-id="4bc9e-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="4bc9e-223">**出力メディア資産名\*Video1.mp4--Media Encoder Standard のエンコード**\*</span><span class="sxs-lookup"><span data-stu-id="4bc9e-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Azure Portal](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="4bc9e-225">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="4bc9e-226">使用して、バーが表示されます**追加エンコード ジョブ**そのバーをクリックして、パネルが表示されているエンコードの進行状況で表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-17.png)

    ![Azure Portal](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="4bc9e-229">ジョブが完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="4bc9e-230">これを完了すると、自由に、そのパネルの右上にある 'X' でパネルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-19.png)

    ![Azure Portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="4bc9e-233">これにより、時間は、ビデオのファイルのサイズによって異なります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="4bc9e-234">このプロセスには、かなりの時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="4bc9e-235">ビデオのエンコードされたバージョンを作成すると、アクセスできるようにすることを発行できます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="4bc9e-236">これを行うには、青色のリンクをクリックします。**資産**資産のページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="4bc9e-238">別のあると共に、ビデオが表示されます \*\*資産の種類 \*マルチビット レート MP4\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-238">You will see your video along with another, which is of \*\*Asset Type \*Multi-Bitrate MP4\*\*\*.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="4bc9e-240">初期ビデオ、と共に、新しい資産がであることがわかります*不明な*、に対しては、'0' バイトを持つと**サイズ**、だけを更新するため、ウィンドウを更新します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="4bc9e-241">この新しい資産をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-241">Click this new asset.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="4bc9e-243">前に、さまざまな資産は、これを使用したものと同様のパネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="4bc9e-244">をクリックして、**発行**ページの上部中央にあるボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="4bc9e-246">設定を求め、**ロケーター**ファイル/秒で、資産へのエントリ ポイントであります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="4bc9e-247">自分のシナリオには、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="4bc9e-248">**ロケーターの種類** > **プログレッシブ**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="4bc9e-249">**日付**と**時間**に設定されますが、現在の日付から、将来の時刻 (ここでは 100 年)。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="4bc9e-250">か、変更に合わせてままにします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4bc9e-251">詳細については、ロケーター、および選択することができます、次を参照してください。、 [Azure Media Services のドキュメント](https://docs.microsoft.com/azure/media-services/media-services-concepts)します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="4bc9e-252">そのパネルの下部で、をクリックして、**追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="4bc9e-254">ビデオが発行されましたと、そのエンドポイントを使用してストリーミングできます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="4bc9e-255">ページがダウンをさらに、**ファイル**セクション。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="4bc9e-256">これは、ビデオのエンコードされたバージョンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="4bc9e-257">いずれかの最も高い解像度を選択します (下の画像が 1920 x 960 ファイル) とし、右側のパネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="4bc9e-258">サイトでは、**ダウンロード URL**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="4bc9e-259">このコピー**エンドポイント**コードで使用するためです。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-26.png)    

    ![Azure Portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="4bc9e-262">押すことも、**再生**ボタン、ビデオを再生し、テストします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="4bc9e-263">このラボで使用する 2 番目のビデオをアップロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="4bc9e-264">2 番目のビデオに同じプロセスを繰り返し、上記の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="4bc9e-265">2 番目のコピー**エンドポイント**もします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="4bc9e-266">次を使用して、 [2 番目のビデオをダウンロードするリンク](https://vimeo.com/214402865)します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="4bc9e-267">両方のビデオが公開されると、次のチャプターに移動する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="4bc9e-268">第 3 章 - Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="4bc9e-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="4bc9e-269">次のコード例が Mixed Reality での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="4bc9e-270">開いている**Unity**クリック**新規**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-270">Open **Unity** and click **New**.</span></span> 

    ![Azure Portal](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="4bc9e-272">Unity プロジェクト名を指定する必要がありますこれで挿入**MR\_360VideoStreaming。** します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="4bc9e-273">必ず、プロジェクトの種類に設定されて**3D**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="4bc9e-274">場所で該当する別の場所を設定します (ただし、ルート ディレクトリに近づけるためのより良い)。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="4bc9e-275">をクリックし、**プロジェクトの作成**です。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-275">Then, click **Create project**.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="4bc9e-277">既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="4bc9e-278">移動して***編集\*\*設定*** し、新しいウィンドウに移動**外部ツール**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="4bc9e-279">変更**External Script Editor**に**Visual Studio 2017**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="4bc9e-280">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-280">Close the **Preferences** window.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="4bc9e-282">次に移動***ファイル* *Build Settings*** にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**をクリックして**スイッチ プラットフォーム**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="4bc9e-283">確認します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-283">Also make sure that:</span></span>

    1. <span data-ttu-id="4bc9e-284">**デバイスを対象に**に設定されている**任意のデバイス。**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="4bc9e-285">**ビルドの種類**に設定されている**D3D します。**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="4bc9e-286">**SDK**に設定されている**最新バージョンをインストールします。**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="4bc9e-287">**Visual Studio バージョン**に設定されている**最新バージョンをインストールします。**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="4bc9e-288">**ビルドおよび実行**に設定されている**ローカル コンピューター。**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="4bc9e-289">設定する方法について気にかけないように**シーン**今を後でこの設定は、します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="4bc9e-290">残りの設定は、ここでは、既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-290">The remaining settings should be left as default for now.</span></span>

        ![Unity プロジェクトの設定](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="4bc9e-292">**Build Settings**ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、**インスペクター**が配置されています。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="4bc9e-293">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="4bc9e-294">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="4bc9e-295">**Scripting** **ランタイム バージョン**する必要があります**安定した**(.NET 3.5 相当)。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="4bc9e-296">**バックエンドの scripting**べき **.NET。**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="4bc9e-297">**API の互換性レベル**べき **.NET 4.6 です。**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![Unity プロジェクトの設定](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="4bc9e-299">パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Unity プロジェクトの設定](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="4bc9e-301">内で、**発行の設定**] タブの [**機能**、確認してください。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="4bc9e-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-302">**InternetClient**</span></span>

            ![Unity プロジェクトの設定](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="4bc9e-304">これらの変更を行った場合、閉じる、 **Build Settings**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="4bc9e-305">プロジェクトを保存 \**ファイル* \*\*\*プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="4bc9e-306">第 4 章 - InsideOutSphere Unity パッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4bc9e-307">スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)、としてプロジェクトにインポート、 [ **カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて**第 5 章**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="4bc9e-308">Unity プロジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="4bc9e-309">このコースは Unity Asset のパッケージをダウンロードする必要がありますと呼ばれる[ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="4bc9e-310">インポートの操作方法に関する、 **unitypackage**:</span><span class="sxs-lookup"><span data-stu-id="4bc9e-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="4bc9e-311">前 [Unity ダッシュ ボード] をクリックして**資産**画面の上部にあるメニューでクリックして**パッケージのインポート > カスタム パッケージ**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="4bc9e-313">ファイル ピッカーを使用して、 **InsideOutSphere.unitypackage**パッケージ化し、をクリックして**オープン**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="4bc9e-314">この資産のコンポーネントの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="4bc9e-315">クリックして、インポートを確認します。**インポート**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-315">Confirm the import by clicking **Import**.</span></span>

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="4bc9e-317">これには、インポートが完了したら後、は、3 つの新しいフォルダーが表示されます**資料**、**モデル**、および**プレハブ**に追加されている、**資産**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="4bc9e-318">このようなフォルダー構造は、Unity プロジェクトの一般的なものです。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="4bc9e-320">開く、**モデル**フォルダーが表示されますが、 **InsideOutSphere**モデルがインポートされています。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="4bc9e-321">内で、**資料**フォルダーが表示されます、 **InsideOutSpheres**マテリアル*lambert1*と呼ばれるマテリアルと共に*ButtonMaterial*、すぐに表示される GazeButton によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="4bc9e-322">**プレハブ**フォルダーが含まれています、 **InsideOutSphere**プレハブの両方を含む、 **InsideOutSphere** *モデル*と、 *GazeButton*します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="4bc9e-323">**コードが含まれていない**、このコースで、コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="4bc9e-324">内で、**階層**を選択、 **Main Camera**オブジェクトし、次のコンポーネントの更新します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="4bc9e-325">**変換**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-325">**Transform**</span></span>

        1.  <span data-ttu-id="4bc9e-326">位置 = **X**:0、 **Y**:0、 **Z**:0。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="4bc9e-327">回転 = **X**:0、 **Y**:0、 **Z**:0。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="4bc9e-328">スケール**X**:1、 **Y**:1、 **Z**:1. </span><span class="sxs-lookup"><span data-stu-id="4bc9e-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="4bc9e-329">**カメラ**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-329">**Camera**</span></span>

        1. <span data-ttu-id="4bc9e-330">**フラグをクリア**:純色です。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="4bc9e-331">**Clipping**:ほぼ。0.1、はるかに:6。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="4bc9e-333">移動し、**プレハブ**フォルダー、およびドラッグ、 **InsideOutSphere**にプレハブ、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="4bc9e-335">展開、 **InsideOutSphere**オブジェクト内の**階層**を横にある小さな矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="4bc9e-336">表示されます、**子**と呼ばれるその下にあるオブジェクト**GazeButton**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="4bc9e-337">シーンおよびビデオを変更するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-337">This will be used to change scenes and thus videos.</span></span>

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="4bc9e-339">インスペクター ウィンドウをクリックして、 **InsideOutSphere**の変換コンポーネントを次のプロパティを設定することを確認します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="4bc9e-340">変換の位置</span><span class="sxs-lookup"><span data-stu-id="4bc9e-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="4bc9e-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="4bc9e-341">**X** 0</span></span>  |          <span data-ttu-id="4bc9e-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="4bc9e-342">**Y** 0</span></span>          |  <span data-ttu-id="4bc9e-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="4bc9e-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="4bc9e-344">変換の回転</span><span class="sxs-lookup"><span data-stu-id="4bc9e-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="4bc9e-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="4bc9e-345">**X** 0</span></span>  |          <span data-ttu-id="4bc9e-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="4bc9e-346">**Y** -50</span></span>        |  <span data-ttu-id="4bc9e-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="4bc9e-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="4bc9e-348">変換のスケール</span><span class="sxs-lookup"><span data-stu-id="4bc9e-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="4bc9e-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="4bc9e-349">**X** 1</span></span>   |          <span data-ttu-id="4bc9e-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="4bc9e-350">**Y** 1</span></span>          |  <span data-ttu-id="4bc9e-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="4bc9e-351">**Z** 1</span></span>  |

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="4bc9e-353">をクリックして、 **GazeButton** 、子オブジェクトとその**変換**次のように。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="4bc9e-354">変換の位置</span><span class="sxs-lookup"><span data-stu-id="4bc9e-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="4bc9e-355">**X** 3.6</span><span class="sxs-lookup"><span data-stu-id="4bc9e-355">**X** 3.6</span></span>|          <span data-ttu-id="4bc9e-356">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="4bc9e-356">**Y** 1.3</span></span>        |  <span data-ttu-id="4bc9e-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="4bc9e-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="4bc9e-358">変換の回転</span><span class="sxs-lookup"><span data-stu-id="4bc9e-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="4bc9e-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="4bc9e-359">**X** 0</span></span>  |          <span data-ttu-id="4bc9e-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="4bc9e-360">**Y** 0</span></span>          |  <span data-ttu-id="4bc9e-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="4bc9e-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="4bc9e-362">変換のスケール</span><span class="sxs-lookup"><span data-stu-id="4bc9e-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="4bc9e-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="4bc9e-363">**X** 1</span></span>   |          <span data-ttu-id="4bc9e-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="4bc9e-364">**Y** 1</span></span>          |  <span data-ttu-id="4bc9e-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="4bc9e-365">**Z** 1</span></span>  |

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="4bc9e-367">5 - 章 VideoController クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="4bc9e-368">**VideoController**クラスは、Azure メディア サービスからコンテンツをストリーミングに使用される 2 つのビデオのエンドポイントをホストします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="4bc9e-369">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-369">To create this class:</span></span>

1.  <span data-ttu-id="4bc9e-370">右クリックし、**アセット フォルダー**にある、**プロジェクト**パネル をクリックします**作成 > フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="4bc9e-371">フォルダーの名前**スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-371">Name the folder **Scripts**.</span></span>

    ![VideoController クラスを作成します。](images/AzureLabs-Lab6-43.png)

    ![VideoController クラスを作成します。](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="4bc9e-374">ダブルクリック、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="4bc9e-375">フォルダー内を右クリックし、をクリックして**作成 > C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="4bc9e-376">スクリプトの名前**VideoController**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-376">Name the script **VideoController**.</span></span>

    ![VideoController クラスを作成します。](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="4bc9e-378">新しいをダブルクリックします。 **VideoController**スクリプト ファイルを開く**Visual Studio 2017。**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![VideoController クラスを作成します。](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="4bc9e-380">次のように、コード ファイルの上部にある名前空間を更新します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="4bc9e-381">次の変数を入力、 **VideoController**クラス、と共に、 **Awake()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  <span data-ttu-id="4bc9e-382">ここは、Azure Media Service のビデオから、エンドポイントを入力します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="4bc9e-383">最初に、 *video1endpoint*変数。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="4bc9e-384">2 番目に、 *video2endpoint*変数。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="4bc9e-385">使用して既知の問題がある*https*バージョン 2017.4.1f1 で、Unity 内で。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="4bc9e-386">ビデオでは、プレイのエラーを提供する場合、は、'http' を代わりを使用してみてください。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="4bc9e-387">次に、 **Start()** メソッドを編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="4bc9e-388">このメソッドは、ユーザーは、視線のボタンを調べることでシーン (その結果、ビデオの切り替え) を切り替えるたびにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="4bc9e-389">次の**Start()** メソッド、挿入、 **PlayVideo()** *IEnumerator*メソッドは、シームレスに (そのため途切れるは表示されません)、ビデオを開始するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. <span data-ttu-id="4bc9e-390">このクラスは必要がある最後のメソッド、 **ChangeScene()** メソッドは、シーンの間でスワップするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="4bc9e-391">**ChangeScene()** メソッドは便利な C を使用して\#と呼ばれる機能、*条件演算子*します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="4bc9e-392">これにより、条件をチェックできるし、値に基づいて返される 1 つのステートメント内ですべてのチェックの結果。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="4bc9e-393">この後に[条件演算子の詳細へのリンク](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="4bc9e-394">Visual Studio で Unity に戻る前に、変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="4bc9e-395">戻る Unity エディターで、をクリックし、ドラッグ、 **VideoController** [から] {.underline} クラス、**スクリプト**フォルダーを**Main Camera**オブジェクト、 **階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="4bc9e-396">をクリックして、 **Main Camera**を見て、**インスペクター パネル**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="4bc9e-397">新しく追加されたスクリプト コンポーネント内が空の値を持つフィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="4bc9e-398">これは、参照フィールドが、コード内のパブリック変数を対象としたものです。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="4bc9e-399">ドラッグ、 **InsideOutSphere**オブジェクトから、**階層パネル**を**球**スロット、次の図に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="4bc9e-400">![VideoController クラスを作成](images/AzureLabs-Lab6-47.png)
    ![VideoController クラスを作成](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="4bc9e-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="4bc9e-401">第 6 章 - 視線の先クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="4bc9e-402">作成するため、このクラスは、 **Raycast**は beprojected を転送することから、 **Main Camera**ユーザーが見るオブジェクトを検出します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-402">This class is responsible for creating a **Raycast** that will beprojected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="4bc9e-403">この場合、 **Raycast**で、ユーザーが探している場合を識別する必要があります、 **GazeButton**シーン内のオブジェクトし、動作をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="4bc9e-404">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-404">To create this Class:</span></span>

1.  <span data-ttu-id="4bc9e-405">移動して、**スクリプト**以前に作成したフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="4bc9e-406">右クリックし、**プロジェクト**パネルで、**作成** C\#スクリプト\*\*。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="4bc9e-407">スクリプトの名前**視線**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="4bc9e-408">新しいをダブルクリックします。***視線***スクリプト ファイルを開く**Visual Studio 2017。**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="4bc9e-409">次の名前空間は、スクリプトの上部にあることを確認し、その他の要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="4bc9e-410">内で、次の変数を追加し、**視線**クラス。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-410">Then add the following variables inside the **Gaze** class:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  <span data-ttu-id="4bc9e-411">コードを**Awake()** と**Start()** 今すぐメソッドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  <span data-ttu-id="4bc9e-412">次のコードを追加、 **Update()** メソッドは、Raycast のプロジェクトをターゲット ヒットを検出します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  <span data-ttu-id="4bc9e-413">Visual Studio で Unity に戻る前に、変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="4bc9e-414">クリックしてドラッグし、**視線**Scripts フォルダーからクラスの Main Camera オブジェクトを**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="4bc9e-415">第 7 章 – セットアップ、2 つの Unity シーン</span><span class="sxs-lookup"><span data-stu-id="4bc9e-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="4bc9e-416">この章の目的は、2 つのシーンでは、ビデオ ストリームを各ホストをセットアップすることです。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="4bc9e-417">既に作成してシーンを重複していますが必要はありません、もう一度設定するには、新しいシーンを編集し、ように、 *GazeButton*オブジェクトは、別の場所ではあり、異なる外観です。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="4bc9e-418">これは、シーンの間で変更する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="4bc9e-419">これには**ファイル > としてシーンを保存しています.**.保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="4bc9e-420">をクリックして、**新しいフォルダー**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-420">Click the **New folder** button.</span></span>

    ![第 7 章 – セットアップ、2 つの Unity シーン](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="4bc9e-422">フォルダーの名前**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="4bc9e-423">**Save Scene**ウィンドウは開いたままになっています。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="4bc9e-424">新たに作成した開く**シーン**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="4bc9e-425">**ファイル名:** テキスト フィールドに「 **VideoScene1**、キーを押します**保存**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="4bc9e-426">Unity で開く、**シーン**フォルダー、および左クリック、 **VideoScene1**ファイル。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="4bc9e-427">キーボードを使用してキーを押します**Ctrl + D**そのシーンは、重複します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="4bc9e-428">**複製**に移動してコマンドを実行することも**編集 > が重複しています**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="4bc9e-429">Unity は自動的に、シーン名の番号をインクリメントが、以前に挿入されたコードと一致することを確認するか、チェックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="4bc9e-430">おく**VideoScene1**と**VideoScene2**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="4bc9e-431">移動すると、2 つのシーン**ファイル > Build Settings**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="4bc9e-432">**Build Settings**ウィンドウを開いて、ドラッグ、シーン、**ビルド内のシーン**セクション。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="4bc9e-434">シーンの両方を選択することができます、**シーン**で保持しているフォルダに、 **Ctrl**ボタンをクリックすると、各シーンを左クリックし、最後に両方の間でドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="4bc9e-435">閉じる、 **Build Settings**ウィンドウ、およびダブルクリック**VideoScene2**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="4bc9e-436">開いている 2 つ目のシーンを をクリックして、 **GazeButton**の子オブジェクト、 **InsideOutSphere**、し、その変換を次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="4bc9e-437">変換の位置</span><span class="sxs-lookup"><span data-stu-id="4bc9e-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="4bc9e-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="4bc9e-438">**X** 0</span></span>  |         <span data-ttu-id="4bc9e-439">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="4bc9e-439">**Y** 1.3</span></span>         | <span data-ttu-id="4bc9e-440">**Z** 3.6</span><span class="sxs-lookup"><span data-stu-id="4bc9e-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="4bc9e-441">変換の回転</span><span class="sxs-lookup"><span data-stu-id="4bc9e-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="4bc9e-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="4bc9e-442">**X** 0</span></span>  |          <span data-ttu-id="4bc9e-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="4bc9e-443">**Y** 0</span></span>          |  <span data-ttu-id="4bc9e-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="4bc9e-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="4bc9e-445">変換のスケール</span><span class="sxs-lookup"><span data-stu-id="4bc9e-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="4bc9e-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="4bc9e-446">**X** 1</span></span>   |          <span data-ttu-id="4bc9e-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="4bc9e-447">**Y** 1</span></span>          |  <span data-ttu-id="4bc9e-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="4bc9e-448">**Z** 1</span></span>  |

10. <span data-ttu-id="4bc9e-449">**GazeButton**が選択されている参照に子、**インスペクター**で、**メッシュ フィルター**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="4bc9e-450">次に、ほとんどのターゲットをクリックして、**メッシュ**参照フィールド。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="4bc9e-452">A**メッシュ選択**ポップアップ ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="4bc9e-453">ダブルクリックして、**キューブ**の一覧からメッシュ**資産**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="4bc9e-455">**メッシュ フィルター**更新、およびようになりますが、**キューブ**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="4bc9e-456">をクリックして、**歯車**隣にアイコン**球 Collider**  をクリック**コンポーネントの削除**、このオブジェクトから、コライダーを削除します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="4bc9e-458">**GazeButton**クリックしてが選択されている、**コンポーネントの追加**の下部にあるボタン、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="4bc9e-459">検索フィールドに「**ボックス**、および**足場に Box Collider**オプションを選択できます--を追加する をクリック、**足場に Box Collider**を**GazeButton**オブジェクト.</span><span class="sxs-lookup"><span data-stu-id="4bc9e-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="4bc9e-461">**GazeButton**が部分的に更新されました、外観が異なる、ただしはこれで新規に作成する**マテリアル**いるため、まったく違ってしてよりも、別のオブジェクトとして認識する方が簡単ですが、最初のシーン内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="4bc9e-462">移動し、**資料**フォルダー内で、**プロジェクト パネル**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="4bc9e-463">重複しています、 **ButtonMaterial**マテリアル (キーを押して**Ctrl** + **D**キーボード、または左クリックで、**マテリアル**、し、**編集**ファイル メニュー オプションを選択し**複製**)。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="4bc9e-464">![第 7 章 - セットアップ、2 つの Unity シーン](images/AzureLabs-Lab6-55.png)
    ![章 7 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="4bc9e-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="4bc9e-465">新しい**ButtonMaterial**マテリアル (という名前**ButtonMaterial 1**)、内で、**インスペクター**、クリックして、 **Albedo**色ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="4bc9e-466">ポップアップが表示され、別の色を選択できます (などのどちらを選択) し、ポップアップを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="4bc9e-467">マテリアルは独自のインスタンスをしては異なる元。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-467">The Material will be its own instance, and different to the original.</span></span>

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="4bc9e-469">新しいドラッグ**マテリアル**上に、 **GazeButton**子がここでは最初のシーン ボタンから簡単に区別できるように完全にそのファイルの場所を更新します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="4bc9e-471">この時点で、UWP プロジェクトをビルドする前に、エディターでプロジェクトをテストできます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="4bc9e-472">キーを押して、**再生**ボタン、**エディター**ヘッドホンを着用とします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="4bc9e-474">2 つを見て**GazeButton**最初と 2 番目のビデオを切り替えるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="4bc9e-475">第 8 章 - UWP ソリューションのビルド</span><span class="sxs-lookup"><span data-stu-id="4bc9e-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="4bc9e-476">エディターにエラーが含まれていないことを確認して後、は、ビルドする準備が整ったらします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="4bc9e-477">作成する方法。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-477">To Build:</span></span>

1.  <span data-ttu-id="4bc9e-478">現在のシーンを保存 をクリックして**ファイル > 保存**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="4bc9e-479">チェック ボックスと呼ばれる**Unity C\#プロジェクト**(これは重要なビルドが完了した後に、クラスを編集することを許可することがあるため)。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="4bc9e-480">移動して**ファイル > Build Settings**、 をクリックして**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="4bc9e-481">ソリューションを構築するフォルダーを選択するように促されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-481">You will be prompted to select the folder where you want to buildthe Solution.</span></span>

5.  <span data-ttu-id="4bc9e-482">作成、**ビルド**フォルダーとそのフォルダー内には、任意の適切な名前を別のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="4bc9e-483">新しいフォルダーをクリックし、クリックして**フォルダーの選択**、その場所にビルドを開始する、そのフォルダーを選択するようにします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="4bc9e-484">![第 8 章 - UWP ソリューションをビルドする](images/AzureLabs-Lab6-60.png)
    ![章 - 8 UWP ソリューションをビルドします。](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="4bc9e-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="4bc9e-485">1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="4bc9e-486">9 -」の章をローカル コンピューターに展開します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="4bc9e-487">ビルドが完了したら、**ファイル エクスプ ローラー**ビルドの場所にウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="4bc9e-488">という名前のフォルダーをビルドを開き、Visual Studio 2017 でのソリューションを開くには、そのフォルダー内のソリューション (.sln) ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="4bc9e-489">実行するですだけが、コンピューターにアプリのデプロイ (または*ローカル マシン*)。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="4bc9e-490">ローカル コンピューターに展開します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="4bc9e-491">**Visual Studio 2017**が作成されたソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="4bc9e-492">**ソリューション プラットフォーム**、 **x86、ローカル コンピューター**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="4bc9e-493">**ソリューション構成**選択**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![ローカル コンピューター上の第 9 章 - 展開します。](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="4bc9e-495">これで、ソリューションにすべてのパッケージを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="4bc9e-496">右クリックし、**ソリューション**、 をクリック**ソリューションの NuGet パッケージを復元しています.**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="4bc9e-497">これは Unity が組み込まれているパッケージは、ローカル コンピューターの参照を使用する対象とする必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="4bc9e-498">移動して**ビルド メニューの** をクリック**ソリューションの配置**をコンピューターにアプリケーションをサイドローディングします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="4bc9e-499">Visual Studio は最初にビルドし、アプリケーションをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="4bc9e-500">アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![ローカル コンピューター上の第 9 章 - 展開します。](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="4bc9e-502">内には、複合現実のアプリケーションを実行するときに、 **InsideOutSphere**アプリ内で使用したモデル。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="4bc9e-503">この球体になります、ビデオをストリーミングするのには、(これは、この種類のパースペクティブのアスペクトが)、受信するビデオの 360 度ビューを提供します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="4bc9e-504">驚かないでください、アプリが、使用可能なインターネットの速度の対象は、ビデオがいくつかの読み込みに数秒を受け取る場合にフェッチされ、ダウンロードし、アプリにストリーミングするために、ビデオが必要です。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="4bc9e-505">準備ができたら、シーンを変更して、gazing 赤い球にして、2 番目のビデオを開きます。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="4bc9e-506">自由に戻ると、2 つ目のシーン内の青色の立方を使用して!</span><span class="sxs-lookup"><span data-stu-id="4bc9e-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="4bc9e-507">完成した Azure Media Service アプリケーション</span><span class="sxs-lookup"><span data-stu-id="4bc9e-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="4bc9e-508">これで、360 ビデオをストリーミングする Azure Media Service を利用している mixed reality アプリを構築します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![ラボの結果](images/AzureLabs-Lab6-00.png)

![ラボの結果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="4bc9e-511">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="4bc9e-511">Bonus Exercises</span></span>

<span data-ttu-id="4bc9e-512">**手順 1**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-512">**Exercise 1**</span></span>

<span data-ttu-id="4bc9e-513">のみ 1 つのシーンを使用して、このチュートリアルでビデオを変更することは可能になります。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="4bc9e-514">アプリケーションを試してみてを 1 つのシーンに!</span><span class="sxs-lookup"><span data-stu-id="4bc9e-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="4bc9e-515">おそらく、ミックスにも別のビデオを追加します。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="4bc9e-516">**手順 2**</span><span class="sxs-lookup"><span data-stu-id="4bc9e-516">**Exercise 2**</span></span>

<span data-ttu-id="4bc9e-517">Azure と Unity、実験し、ビデオをインターネット接続の強度によって、別のファイル サイズを自動的に選択するアプリの機能を実装しようとしてください。</span><span class="sxs-lookup"><span data-stu-id="4bc9e-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


