---
title: MR および Azure 305 - 関数およびストレージ
description: このコースでは、複合現実のアプリケーション内で Azure Storage と関数を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、関数、ストレージ、hololens、vr、没入型
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598301"
---
>[!NOTE]
><span data-ttu-id="45f92-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="45f92-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="45f92-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="45f92-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="45f92-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="45f92-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="45f92-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="45f92-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="45f92-110">MR と Azure 305:関数とストレージ</span><span class="sxs-lookup"><span data-stu-id="45f92-110">MR and Azure 305: Functions and storage</span></span>

![最終的な製品-開始](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="45f92-112">このコースでは、作成し、Azure Functions を使用する複合現実のアプリケーション内で、Azure Storage リソースにデータを格納する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="45f92-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="45f92-113">*Azure Functions*できる小規模なコードを実行する開発者の Microsoft サービス '関数'、Azure では、します。</span><span class="sxs-lookup"><span data-stu-id="45f92-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="45f92-114">これは、多くのメリットを持つことができる、ローカル アプリケーションではなく、クラウドに作業を委任する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="45f92-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="45f92-115">*Azure Functions* C をなど、複数の開発言語をサポートしている\#、F\#Node.js、Java、および PHP します。</span><span class="sxs-lookup"><span data-stu-id="45f92-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="45f92-116">詳細については、次を参照してください。、 [Azure Functions の記事](https://docs.microsoft.com/azure/azure-functions/functions-overview)します。</span><span class="sxs-lookup"><span data-stu-id="45f92-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="45f92-117">*Azure Storage*は、開発者が使用される高可用性、セキュリティで保護された、永続的な拡張性と冗長性保険、データの格納を Microsoft クラウド サービスです。</span><span class="sxs-lookup"><span data-stu-id="45f92-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="45f92-118">つまり、Microsoft のすべての保守、および重大な問題を処理します。</span><span class="sxs-lookup"><span data-stu-id="45f92-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="45f92-119">詳細については、次を参照してください。、 [Azure Storage の記事](https://docs.microsoft.com/azure/storage/common/storage-introduction)します。</span><span class="sxs-lookup"><span data-stu-id="45f92-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="45f92-120">このコースを完了すると、以下を実行できる必要が複合現実イマーシブ ヘッドセット アプリケーションが完成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="45f92-121">視線シーンの周囲にユーザーを許可します。</span><span class="sxs-lookup"><span data-stu-id="45f92-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="45f92-122">ユーザーが gazes 3D 'button' にあるときに、オブジェクトの生成をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="45f92-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="45f92-123">Azure 関数によって生成されたオブジェクトが選択されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="45f92-124">アプリケーションがオブジェクトの種類を格納するように、各オブジェクトが生成される、 *Azure File*にある*Azure Storage*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="45f92-125">再度読み込むときに、 *Azure File*データは取得、およびアプリケーションの以前のインスタンスからの起動元のアクションを再生するために使用します。</span><span class="sxs-lookup"><span data-stu-id="45f92-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="45f92-126">アプリケーションでは、責任ですが、設計と、結果を統合する方法について。</span><span class="sxs-lookup"><span data-stu-id="45f92-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="45f92-127">このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。</span><span class="sxs-lookup"><span data-stu-id="45f92-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="45f92-128">できるように、複合現実のアプリケーションを強化するためには、このコースからのナレッジを使用して、ジョブになります。</span><span class="sxs-lookup"><span data-stu-id="45f92-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="45f92-129">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="45f92-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="45f92-130">コース</span><span class="sxs-lookup"><span data-stu-id="45f92-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="45f92-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="45f92-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="45f92-132"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="45f92-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="45f92-133">MR と Azure 305:関数とストレージ</span><span class="sxs-lookup"><span data-stu-id="45f92-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="45f92-134">✔️</span><span class="sxs-lookup"><span data-stu-id="45f92-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="45f92-135">✔️</span><span class="sxs-lookup"><span data-stu-id="45f92-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="45f92-136">このコースが主に Windows Mixed Reality 没入型 (VR) ヘッドセットを重点的に Microsoft HoloLens には、このコースで学習する内容を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="45f92-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="45f92-137">コースを実行するとき、HoloLens をサポートするために必要な場合があります変更でノートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="45f92-138">前提条件</span><span class="sxs-lookup"><span data-stu-id="45f92-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="45f92-139">このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。</span><span class="sxs-lookup"><span data-stu-id="45f92-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="45f92-140">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 5 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="45f92-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="45f92-141">内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)ことについては、このコースでとまったく同じで見つかりますの下に記載されているものよりも新しいソフトウェアでどのようなことは仮定されませんが、記事.</span><span class="sxs-lookup"><span data-stu-id="45f92-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="45f92-142">次のハードウェアとソフトウェアこのコースをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="45f92-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="45f92-143">開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発</span><span class="sxs-lookup"><span data-stu-id="45f92-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="45f92-144">Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="45f92-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="45f92-145">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="45f92-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="45f92-146">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="45f92-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="45f92-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="45f92-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="45f92-148">A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効</span><span class="sxs-lookup"><span data-stu-id="45f92-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="45f92-149">Azure リソースを作成するため、Azure アカウントへのサブスクリプション</span><span class="sxs-lookup"><span data-stu-id="45f92-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="45f92-150">Azure のセットアップやデータの取得のためのインターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="45f92-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="45f92-151">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="45f92-151">Before you start</span></span>

<span data-ttu-id="45f92-152">このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。</span><span class="sxs-lookup"><span data-stu-id="45f92-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="45f92-153">第 1 章 - Azure Portal</span><span class="sxs-lookup"><span data-stu-id="45f92-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="45f92-154">使用する、 **Azure ストレージ サービス**、作成および構成する必要があります、**ストレージ アカウント**Azure portal でします。</span><span class="sxs-lookup"><span data-stu-id="45f92-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="45f92-155">ログイン、 [Azure Portal](https://portal.azure.com)します。</span><span class="sxs-lookup"><span data-stu-id="45f92-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="45f92-156">Azure アカウントがいない場合は、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="45f92-157">クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="45f92-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="45f92-158">ログインした後は、をクリックして**新規**左上隅にある検索して*ストレージ アカウント*、 をクリック**Enter**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![azure storage の検索](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="45f92-160">単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。</span><span class="sxs-lookup"><span data-stu-id="45f92-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="45f92-161">新しいページがの説明を入力、 *Azure Storage アカウント*サービス。</span><span class="sxs-lookup"><span data-stu-id="45f92-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="45f92-162">このプロンプトの左下にある at、**作成**ボタンは、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![サービスを作成します。](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="45f92-164">クリックすると**作成**:</span><span class="sxs-lookup"><span data-stu-id="45f92-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="45f92-165">挿入、*名前*お使いのアカウントに、数字と小文字のみこのフィールドを受け入れるに注意してください。</span><span class="sxs-lookup"><span data-stu-id="45f92-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="45f92-166">*デプロイ モデル*、 **Resource manager**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="45f92-167">*アカウントの種類*、**ストレージ (汎用 v1)** します。</span><span class="sxs-lookup"><span data-stu-id="45f92-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="45f92-168">確認、*場所*(新しいリソース グループを作成する) 場合は、リソース グループ。</span><span class="sxs-lookup"><span data-stu-id="45f92-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="45f92-169">場所は、アプリケーションが実行リージョンにあるが理想的です。</span><span class="sxs-lookup"><span data-stu-id="45f92-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="45f92-170">一部の Azure 資産は特定のリージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="45f92-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="45f92-171">*レプリケーション*選択**読み取りアクセスの geo 冗長ストレージ (RA-GRS)** します。</span><span class="sxs-lookup"><span data-stu-id="45f92-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="45f92-172">*パフォーマンス*、**標準**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="45f92-173">まま*転送が必須のセキュリティで保護された*として**無効になっている**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="45f92-174">選択、*サブスクリプション*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="45f92-175">選択、*リソース グループ*か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="45f92-176">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="45f92-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="45f92-177">勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。</span><span class="sxs-lookup"><span data-stu-id="45f92-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="45f92-178">詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="45f92-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="45f92-179">また、このサービスに適用される条件を理解したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="45f92-180">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="45f92-180">Select **Create**.</span></span>

        ![入力のサービス情報](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="45f92-182">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="45f92-183">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![azure portal で新しい通知](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="45f92-185">新しいサービス インスタンスを探索する通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45f92-185">Click on the notifications to explore your new Service instance.</span></span>

    ![リソースに移動します。](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="45f92-187">をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45f92-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="45f92-188">実施する、新しい*ストレージ アカウント*サービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="45f92-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![アクセス キー](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="45f92-190">をクリックして*アクセス キー*、このクラウド サービスのエンドポイントを表示します。</span><span class="sxs-lookup"><span data-stu-id="45f92-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="45f92-191">使用して、*メモ帳*と同様に、後で使用できる、キーの 1 つをコピーするか。</span><span class="sxs-lookup"><span data-stu-id="45f92-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="45f92-192">また、*接続文字列*値で使用するため、 *AzureServices*クラスは、後で作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![接続文字列をコピー](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="45f92-194">第 2 章 – Azure 関数の設定</span><span class="sxs-lookup"><span data-stu-id="45f92-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="45f92-195">記述して、 **Azure** **関数**で Azure サービスです。</span><span class="sxs-lookup"><span data-stu-id="45f92-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="45f92-196">使用することができます、 **Azure 関数**ほぼ何も行うでの操作とクラシックの関数を使用した、コードの違いは、この関数は、Azure アカウントへのアクセス資格情報を持つ任意のアプリケーションからアクセスできることです。</span><span class="sxs-lookup"><span data-stu-id="45f92-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="45f92-197">Azure 関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="45f92-198">*Azure Portal*、 をクリックして**新規**左上隅にある検索して*Function App*、 をクリック**Enter**。</span><span class="sxs-lookup"><span data-stu-id="45f92-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![function app を作成します。](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="45f92-200">単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。</span><span class="sxs-lookup"><span data-stu-id="45f92-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="45f92-201">新しいページがの説明を入力、 *Azure Function App*サービス。</span><span class="sxs-lookup"><span data-stu-id="45f92-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="45f92-202">このプロンプトの左下にある at、**作成**ボタンは、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![関数アプリの情報](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="45f92-204">クリックすると**作成**:</span><span class="sxs-lookup"><span data-stu-id="45f92-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="45f92-205">提供、*アプリ名*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-205">Provide an *App name*.</span></span> <span data-ttu-id="45f92-206">アルファベットと数字のみをここで使用することができます (上限または下限のいずれかのケースは許可されています)。</span><span class="sxs-lookup"><span data-stu-id="45f92-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="45f92-207">選択、優先*サブスクリプション*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="45f92-208">選択、*リソース グループ*か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="45f92-209">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="45f92-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="45f92-210">勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。</span><span class="sxs-lookup"><span data-stu-id="45f92-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="45f92-211">詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="45f92-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="45f92-212">この演習では、次のように選択します。 *Windows*として選択した**OS**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="45f92-213">選択*従量課金プラン*の**ホスティング プラン**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="45f92-214">確認、*場所*(新しいリソース グループを作成する) 場合は、リソース グループ。</span><span class="sxs-lookup"><span data-stu-id="45f92-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="45f92-215">場所は、アプリケーションが実行リージョンにあるが理想的です。</span><span class="sxs-lookup"><span data-stu-id="45f92-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="45f92-216">一部の Azure 資産は特定のリージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="45f92-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="45f92-217">最適なパフォーマンス、ストレージ アカウントと同じリージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="45f92-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="45f92-218">*ストレージ*を選択します**既存の**、以前に作成したストレージを検索し、ドロップダウン メニューを使用するとします。</span><span class="sxs-lookup"><span data-stu-id="45f92-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="45f92-219">まま*Application Insights*この演習ではオフです。</span><span class="sxs-lookup"><span data-stu-id="45f92-219">Leave *Application Insights* off for this exercise.</span></span>

        ![入力関数アプリの詳細](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="45f92-221">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45f92-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="45f92-222">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="45f92-223">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新しい azure portal の通知](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="45f92-225">新しいサービス インスタンスを探索する通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45f92-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![関数アプリのリソースに移動します。](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="45f92-227">をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45f92-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="45f92-228">実施する、新しい*Function App*サービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="45f92-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="45f92-229">*関数アプリ*ダッシュ ボードで、マウス カーソルを置く*関数*、左側のパネル内に存在し、クリックして、 **+ (正符号 +)** シンボル。</span><span class="sxs-lookup"><span data-stu-id="45f92-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![新しい関数を作成します。](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="45f92-231">次のページで確認**webhook+api**が選択されていると *、言語の選択*選択**CSharp**、このチュートリアルで使用されている言語があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="45f92-232">最後に、をクリックして、**この関数を作成**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45f92-232">Lastly, click the **Create this function** button.</span></span>

    ![web フック csharp を選択します。](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="45f92-234">コードが表示される、左側のパネル内の関数の一覧で、新しく作成された関数の いない場合 (run.csx) ページの します。</span><span class="sxs-lookup"><span data-stu-id="45f92-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![新しい関数を開く](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="45f92-236">関数には、次のコードをコピーします。</span><span class="sxs-lookup"><span data-stu-id="45f92-236">Copy the following code into your function.</span></span> <span data-ttu-id="45f92-237">この関数は、0 と 2 が呼び出されるとの間のランダムな整数を返しますだけです。</span><span class="sxs-lookup"><span data-stu-id="45f92-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="45f92-238">既存のコードについて心配ではなく自由に、その上に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="45f92-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. <span data-ttu-id="45f92-239">**[保存]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="45f92-239">Select **Save**.</span></span>

14. <span data-ttu-id="45f92-240">結果は、次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="45f92-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="45f92-241">をクリックして**関数の URL を取得する**メモ、*エンドポイント*が表示されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="45f92-242">挿入する必要があります、 *AzureServices*このコースの後半で作成するクラス。</span><span class="sxs-lookup"><span data-stu-id="45f92-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![関数のエンドポイントを取得します。](images/AzureLabs-Lab5-16.png)

    ![関数のエンドポイントを取得します。](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="45f92-245">第 3 章 - Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="45f92-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="45f92-246">次のコード例が Mixed Reality での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。</span><span class="sxs-lookup"><span data-stu-id="45f92-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="45f92-247">設定して、mixed reality イマーシブ ヘッドセットをテストします。</span><span class="sxs-lookup"><span data-stu-id="45f92-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="45f92-248">**いない**このコースのモーションのコント ローラーが必要です。</span><span class="sxs-lookup"><span data-stu-id="45f92-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="45f92-249">イマーシブ ヘッドセットの設定をサポートする場合は、次のようにしてください。[記事セットアップ複合現実を参照してください。](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)します。</span><span class="sxs-lookup"><span data-stu-id="45f92-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="45f92-250">Unity を開き、をクリックして**新規**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-250">Open Unity and click **New**.</span></span>

    ![新しい unity プロジェクトを作成します。](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="45f92-252">これで、Unity プロジェクト名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="45f92-253">挿入**MR_Azure_Functions**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="45f92-254">必ず、プロジェクトの種類に設定されて**3D**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="45f92-255">設定、*場所*に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。</span><span class="sxs-lookup"><span data-stu-id="45f92-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="45f92-256">をクリックし、**プロジェクトの作成**です。</span><span class="sxs-lookup"><span data-stu-id="45f92-256">Then, click **Create project**.</span></span>

    ![新しい unity プロジェクトに名前を付けます](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="45f92-258">既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="45f92-259">移動して **編集* > *設定** し、新しいウィンドウに移動 **外部ツール** します。</span><span class="sxs-lookup"><span data-stu-id="45f92-259">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="45f92-260">変更 **External Script Editor** に **Visual Studio 2017** します。</span><span class="sxs-lookup"><span data-stu-id="45f92-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="45f92-261">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="45f92-261">Close the **Preferences** window.</span></span>

    ![スクリプト エディターとして visual studio の設定](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="45f92-263">次に移動**ファイル > Build Settings**にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして、**プラットフォームの切り替え**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45f92-263">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![uwp にプラットフォームを切り替える](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="45f92-265">移動して**ファイル > Build Settings**ことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="45f92-265">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="45f92-266">**デバイスを対象に**に設定されている**任意のデバイス**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="45f92-267">Microsoft HoloLens、設定**ターゲット デバイス**に*HoloLens*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="45f92-268">**ビルドの種類**に設定されている**D3D**</span><span class="sxs-lookup"><span data-stu-id="45f92-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="45f92-269">**SDK**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="45f92-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="45f92-270">**Visual Studio バージョン**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="45f92-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="45f92-271">**ビルドおよび実行**に設定されている**ローカル マシン**</span><span class="sxs-lookup"><span data-stu-id="45f92-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="45f92-272">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="45f92-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="45f92-273">これには、選択**開くシーンを追加**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="45f92-274">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-274">A save window will appear.</span></span>

            ![開いているシーンを追加します。](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="45f92-276">新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![シーンのフォルダーを作成します。](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="45f92-278">新たに作成した開く**シーン**フォルダー、し、**ファイル名:** テキスト フィールドに「 **FunctionsScene**、キーを押します**保存します**。</span><span class="sxs-lookup"><span data-stu-id="45f92-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![関数のシーンを保存します。](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="45f92-280">設定に残っている**Build Settings**、ここでは既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![関数のシーンを保存します。](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="45f92-282">*Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。</span><span class="sxs-lookup"><span data-stu-id="45f92-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![インスペクターの player の設定](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="45f92-284">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="45f92-285">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="45f92-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="45f92-286">**ランタイム バージョンをスクリプト**する必要があります**試験的**(.NET 4.6 Equivalent)、エディターを再起動する必要があるします。</span><span class="sxs-lookup"><span data-stu-id="45f92-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="45f92-287">**バックエンドの scripting**べき **.NET**</span><span class="sxs-lookup"><span data-stu-id="45f92-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="45f92-288">**API の互換性レベル**べき **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="45f92-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="45f92-289">内で、**発行の設定**] タブの [**機能**、確認してください。</span><span class="sxs-lookup"><span data-stu-id="45f92-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="45f92-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="45f92-290">**InternetClient**</span></span>

            ![セットの機能](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="45f92-292">パネル、下の方に**XR 設定**(次に示します**発行の設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed RealitySDK**が追加されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![XR を設定します。](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="45f92-294">戻り*Build Settings* *UnityC#プロジェクト*が不要になったグレー; これの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="45f92-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![ティックの c# プロジェクト](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="45f92-296">ビルド設定ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="45f92-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="45f92-297">シーンとプロジェクトを保存 (**ファイル > シーン保存/ファイル > プロジェクトを保存**)。</span><span class="sxs-lookup"><span data-stu-id="45f92-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="45f92-298">第 4 章 - メイン カメラのセットアップ</span><span class="sxs-lookup"><span data-stu-id="45f92-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45f92-299">スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由に[ダウンロードこの .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)、としてプロジェクトにインポート、[カスタムパッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)します。</span><span class="sxs-lookup"><span data-stu-id="45f92-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="45f92-300">[次へ] の章から Dll が含まれます。</span><span class="sxs-lookup"><span data-stu-id="45f92-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="45f92-301">インポートの後から引き続き[第 7 章](#chapter-7---create-the-azureservices-class)します。</span><span class="sxs-lookup"><span data-stu-id="45f92-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="45f92-302">*階層パネル*、という名前のオブジェクトが表示されます**Main Camera**、「内部」アプリケーションが表示されたら、このオブジェクトは、"head"の観点を表します。</span><span class="sxs-lookup"><span data-stu-id="45f92-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="45f92-303">選択する前にある Unity ダッシュ ボードで、**メイン カメラの GameObject**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="45f92-304">表示になります、*インスペクター パネル*(一般にダッシュ ボードで、右側にあります) をさまざまなコンポーネントが表示されます*GameObject*で*変換*後に、上部にある*カメラ*、およびその他のコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="45f92-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="45f92-305">これが正しく配置されているため、メイン カメラの変換をリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="45f92-306">これを行うには、選択、**歯車**カメラの横にあるアイコン*変換*コンポーネント、および選択**リセット**。</span><span class="sxs-lookup"><span data-stu-id="45f92-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![変換をリセットします。](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="45f92-308">更新し、**変換**のようにコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="45f92-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="45f92-309">変換の位置</span><span class="sxs-lookup"><span data-stu-id="45f92-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="45f92-310">**X**</span><span class="sxs-lookup"><span data-stu-id="45f92-310">**X**</span></span>   | <span data-ttu-id="45f92-311">**Y**</span><span class="sxs-lookup"><span data-stu-id="45f92-311">**Y**</span></span>                     | <span data-ttu-id="45f92-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="45f92-312">**Z**</span></span> |
    | <span data-ttu-id="45f92-313">0</span><span class="sxs-lookup"><span data-stu-id="45f92-313">0</span></span>       | <span data-ttu-id="45f92-314">1</span><span class="sxs-lookup"><span data-stu-id="45f92-314">1</span></span>                         | <span data-ttu-id="45f92-315">0</span><span class="sxs-lookup"><span data-stu-id="45f92-315">0</span></span>     |    

    |       | <span data-ttu-id="45f92-316">変換の回転</span><span class="sxs-lookup"><span data-stu-id="45f92-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="45f92-317">**X**</span><span class="sxs-lookup"><span data-stu-id="45f92-317">**X**</span></span> | <span data-ttu-id="45f92-318">**Y**</span><span class="sxs-lookup"><span data-stu-id="45f92-318">**Y**</span></span>                | <span data-ttu-id="45f92-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="45f92-319">**Z**</span></span> |
    | <span data-ttu-id="45f92-320">0</span><span class="sxs-lookup"><span data-stu-id="45f92-320">0</span></span>     | <span data-ttu-id="45f92-321">0</span><span class="sxs-lookup"><span data-stu-id="45f92-321">0</span></span>                    | <span data-ttu-id="45f92-322">0</span><span class="sxs-lookup"><span data-stu-id="45f92-322">0</span></span>     |

    |       | <span data-ttu-id="45f92-323">変換のスケール</span><span class="sxs-lookup"><span data-stu-id="45f92-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="45f92-324">**X**</span><span class="sxs-lookup"><span data-stu-id="45f92-324">**X**</span></span> | <span data-ttu-id="45f92-325">**Y**</span><span class="sxs-lookup"><span data-stu-id="45f92-325">**Y**</span></span>             | <span data-ttu-id="45f92-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="45f92-326">**Z**</span></span> |
    | <span data-ttu-id="45f92-327">1</span><span class="sxs-lookup"><span data-stu-id="45f92-327">1</span></span>     | <span data-ttu-id="45f92-328">1</span><span class="sxs-lookup"><span data-stu-id="45f92-328">1</span></span>                 | <span data-ttu-id="45f92-329">1</span><span class="sxs-lookup"><span data-stu-id="45f92-329">1</span></span>     |

    ![セットのカメラの変換](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="45f92-331">第 5 章 - Unity シーンの設定</span><span class="sxs-lookup"><span data-stu-id="45f92-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="45f92-332">空の領域で右クリックし、*階層パネル* **3D オブジェクト**、追加、**平面**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![新しい面を作成します。](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="45f92-334">**平面**オブジェクトの選択されている、次のパラメーターを変更、*インスペクター パネル*:</span><span class="sxs-lookup"><span data-stu-id="45f92-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="45f92-335">変換の位置</span><span class="sxs-lookup"><span data-stu-id="45f92-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="45f92-336">**X**</span><span class="sxs-lookup"><span data-stu-id="45f92-336">**X**</span></span> | <span data-ttu-id="45f92-337">**Y**</span><span class="sxs-lookup"><span data-stu-id="45f92-337">**Y**</span></span>                | <span data-ttu-id="45f92-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="45f92-338">**Z**</span></span> |
    | <span data-ttu-id="45f92-339">0</span><span class="sxs-lookup"><span data-stu-id="45f92-339">0</span></span>     | <span data-ttu-id="45f92-340">0</span><span class="sxs-lookup"><span data-stu-id="45f92-340">0</span></span>                    | <span data-ttu-id="45f92-341">4</span><span class="sxs-lookup"><span data-stu-id="45f92-341">4</span></span>     |

    |       | <span data-ttu-id="45f92-342">変換のスケール</span><span class="sxs-lookup"><span data-stu-id="45f92-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="45f92-343">**X**</span><span class="sxs-lookup"><span data-stu-id="45f92-343">**X**</span></span> | <span data-ttu-id="45f92-344">**Y**</span><span class="sxs-lookup"><span data-stu-id="45f92-344">**Y**</span></span>             | <span data-ttu-id="45f92-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="45f92-345">**Z**</span></span> |
    | <span data-ttu-id="45f92-346">10</span><span class="sxs-lookup"><span data-stu-id="45f92-346">10</span></span>    | <span data-ttu-id="45f92-347">1</span><span class="sxs-lookup"><span data-stu-id="45f92-347">1</span></span>                 | <span data-ttu-id="45f92-348">10</span><span class="sxs-lookup"><span data-stu-id="45f92-348">10</span></span>    |

    ![平面の位置を設定してスケール](images/AzureLabs-Lab5-32.png)

    ![平面のシーン ビュー](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="45f92-351">空の領域で右クリックし、*階層パネル* **3D オブジェクト**、追加、**キューブ**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="45f92-352">キューブの名前を変更**GazeButton** (選択されているキューブを押して 'F2')。</span><span class="sxs-lookup"><span data-stu-id="45f92-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="45f92-353">次のパラメーターを変更、*インスペクター パネル*:</span><span class="sxs-lookup"><span data-stu-id="45f92-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="45f92-354">変換の位置</span><span class="sxs-lookup"><span data-stu-id="45f92-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="45f92-355">**X**</span><span class="sxs-lookup"><span data-stu-id="45f92-355">**X**</span></span> | <span data-ttu-id="45f92-356">**Y**</span><span class="sxs-lookup"><span data-stu-id="45f92-356">**Y**</span></span>                | <span data-ttu-id="45f92-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="45f92-357">**Z**</span></span> |
        | <span data-ttu-id="45f92-358">0</span><span class="sxs-lookup"><span data-stu-id="45f92-358">0</span></span>     | <span data-ttu-id="45f92-359">3</span><span class="sxs-lookup"><span data-stu-id="45f92-359">3</span></span>                    | <span data-ttu-id="45f92-360">5</span><span class="sxs-lookup"><span data-stu-id="45f92-360">5</span></span>     |


        ![セットの視線入力ボタンの変換](images/AzureLabs-Lab5-34.png)

        ![視線ボタン シーン ビュー](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="45f92-363">をクリックして、**タグ**ドロップダウン ボタンをクリックします**タグを追加**を開く、*レイヤー ペイン (&)、タグ*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![新しいタグを追加します。](images/AzureLabs-Lab5-36.png)

        ![プラス記号を選択します](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="45f92-366">選択、 **+ (正符号 +)** ボタン、し、*新しいタグ名*フィールドに、入力**GazeButton**、キーを押します**保存**。</span><span class="sxs-lookup"><span data-stu-id="45f92-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![新しいタグの名前](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="45f92-368">をクリックして、 **GazeButton**オブジェクト、*階層パネル*、し、*インスペクター パネル*、割り当て、新しく作成された**GazeButton**タグ。</span><span class="sxs-lookup"><span data-stu-id="45f92-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![視線入力ボタンをクリックして新しいタグを割り当てる](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="45f92-370">右クリックし、 **GazeButton**オブジェクトで、*階層パネル*、追加、**空の GameObject** (として追加されます、*子*オブジェクトの場合)。</span><span class="sxs-lookup"><span data-stu-id="45f92-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="45f92-371">新しいオブジェクトを選択し、名前変更**ShapeSpawnPoint**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="45f92-372">次のパラメーターを変更、*インスペクター パネル*:</span><span class="sxs-lookup"><span data-stu-id="45f92-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="45f92-373">変換の位置</span><span class="sxs-lookup"><span data-stu-id="45f92-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="45f92-374">**X**</span><span class="sxs-lookup"><span data-stu-id="45f92-374">**X**</span></span> |<span data-ttu-id="45f92-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="45f92-375">**Y**</span></span>                 | <span data-ttu-id="45f92-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="45f92-376">**Z**</span></span> |
        | <span data-ttu-id="45f92-377">0</span><span class="sxs-lookup"><span data-stu-id="45f92-377">0</span></span>     | <span data-ttu-id="45f92-378">-1</span><span class="sxs-lookup"><span data-stu-id="45f92-378">-1</span></span>                   | <span data-ttu-id="45f92-379">0</span><span class="sxs-lookup"><span data-stu-id="45f92-379">0</span></span>     |

        ![図形の生成のポイントの変換を更新します。](images/AzureLabs-Lab5-40.png)

        ![図形の起動ポイント シーン ビュー](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="45f92-382">次に作成、 **3D テキスト**Azure サービスの状態に関するフィードバックを提供するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="45f92-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="45f92-383">右クリックして、 **GazeButton**階層でもう一度 パネルを追加、 **3D オブジェクト > 3D テキスト**オブジェクトとして、*子*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object > 3D Text** object as a *child*.</span></span>

    ![新しい 3D テキスト オブジェクトを作成します。](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="45f92-385">名前の変更、 **3D テキスト**オブジェクトを**AzureStatusText**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="45f92-386">変更、 **AzureStatusText**オブジェクトの次のように変換します。</span><span class="sxs-lookup"><span data-stu-id="45f92-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="45f92-387">変換の位置</span><span class="sxs-lookup"><span data-stu-id="45f92-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="45f92-388">**X**</span><span class="sxs-lookup"><span data-stu-id="45f92-388">**X**</span></span> | <span data-ttu-id="45f92-389">**Y**</span><span class="sxs-lookup"><span data-stu-id="45f92-389">**Y**</span></span>                | <span data-ttu-id="45f92-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="45f92-390">**Z**</span></span> |
    | <span data-ttu-id="45f92-391">0</span><span class="sxs-lookup"><span data-stu-id="45f92-391">0</span></span>     | <span data-ttu-id="45f92-392">0</span><span class="sxs-lookup"><span data-stu-id="45f92-392">0</span></span>                    | <span data-ttu-id="45f92-393">-0.6</span><span class="sxs-lookup"><span data-stu-id="45f92-393">-0.6</span></span>  |

    |       | <span data-ttu-id="45f92-394">変換のスケール</span><span class="sxs-lookup"><span data-stu-id="45f92-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="45f92-395">**X**</span><span class="sxs-lookup"><span data-stu-id="45f92-395">**X**</span></span> | <span data-ttu-id="45f92-396">**Y**</span><span class="sxs-lookup"><span data-stu-id="45f92-396">**Y**</span></span>             | <span data-ttu-id="45f92-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="45f92-397">**Z**</span></span> |
    | <span data-ttu-id="45f92-398">0.1</span><span class="sxs-lookup"><span data-stu-id="45f92-398">0.1</span></span>   | <span data-ttu-id="45f92-399">0.1</span><span class="sxs-lookup"><span data-stu-id="45f92-399">0.1</span></span>               | <span data-ttu-id="45f92-400">0.1</span><span class="sxs-lookup"><span data-stu-id="45f92-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="45f92-401">センターをオフにこれは修正される場合に表示される場合も心配はありません、以下のテキストのメッシュ コンポーネントが更新されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="45f92-402">変更、**テキスト メッシュ**と一致するコンポーネントの下。</span><span class="sxs-lookup"><span data-stu-id="45f92-402">Change the **Text Mesh** component to match the below:</span></span>

    ![テキストの設定のメッシュ コンポーネント](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="45f92-404">ここで選択した色は、16 進数の色を示します。**000000FF**、ただし、自由に独自の選択、それを読み取ることが確認します。</span><span class="sxs-lookup"><span data-stu-id="45f92-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="45f92-405">パネルの階層構造は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="45f92-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![テキストは、シーン ビューでメッシュします。](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="45f92-407">シーンは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="45f92-407">Your scene should now look like this:</span></span>

    ![テキストは、シーン ビューでメッシュします。](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="45f92-409">第 6 章 - Unity 用の Azure Storage のインポート</span><span class="sxs-lookup"><span data-stu-id="45f92-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="45f92-410">Unity の Azure ストレージを使用する (それ自体を活用して、.Net SDK for Azure)。</span><span class="sxs-lookup"><span data-stu-id="45f92-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="45f92-411">詳細について、 [Unity 記事用の Azure Storage](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)します。</span><span class="sxs-lookup"><span data-stu-id="45f92-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="45f92-412">インポート後に再構成するプラグインを必要とする Unity での既知の問題は現在します。</span><span class="sxs-lookup"><span data-stu-id="45f92-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="45f92-413">バグが解決された後、次の手順 (このセクションでは 4 ~ 7) は必要に不要になった。</span><span class="sxs-lookup"><span data-stu-id="45f92-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="45f92-414">独自のプロジェクトに SDK をインポートすることを最新バージョンをダウンロードしていることを確認して[GitHub からの '.unitypackage'](https://aka.ms/azstorage-unitysdk)します。</span><span class="sxs-lookup"><span data-stu-id="45f92-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="45f92-415">次に、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="45f92-415">Then, do the following:</span></span>

1.  <span data-ttu-id="45f92-416">追加、 **.unitypackage** Unity を使用して、ファイル、**資産 > パッケージのインポート > カスタム パッケージ**メニュー オプション。</span><span class="sxs-lookup"><span data-stu-id="45f92-416">Add the **.unitypackage** file to Unity by using the **Assets > Import Package > Custom Package** menu option.</span></span>

2.  <span data-ttu-id="45f92-417"> *\*Unity パッケージのインポート** ポップアップ、選択できることの下のすべてのボックス *\*プラグイン* > \*ストレージ。</span><span class="sxs-lookup"><span data-stu-id="45f92-417">In the **Import Unity Package** box that pops up, you can select everything under \**Plugin* > \*Storage\*\*.</span></span> <span data-ttu-id="45f92-418">このコースの必要がないと、その他のすべてをオフにします。</span><span class="sxs-lookup"><span data-stu-id="45f92-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![パッケージへのインポートします。](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="45f92-420">をクリックして、**インポート**をプロジェクトにアイテムを追加するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45f92-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="45f92-421">移動して、*ストレージ*の下のフォルダー*プラグイン*、プロジェクトのビューを選び、次のプラグイン*のみ*:</span><span class="sxs-lookup"><span data-stu-id="45f92-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="45f92-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="45f92-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="45f92-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="45f92-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="45f92-424">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="45f92-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="45f92-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="45f92-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="45f92-426">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="45f92-426">System.Spatial</span></span>

        ![任意のプラットフォームをオフにします。](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="45f92-428">*これら特定のプラグイン*選択すると、**をオフに** *Any プラットフォーム*と**をオフに** *WSAPlayer*クリックして**適用**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![プラットフォームの dll を適用します。](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="45f92-430">Unity エディターでのみ使用するこれらの特定のプラグインをマークするされます。</span><span class="sxs-lookup"><span data-stu-id="45f92-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="45f92-431">WSA フォルダー Unity からプロジェクトはエクスポート後に使用される同じプラグインのさまざまなバージョンがあるためにです。</span><span class="sxs-lookup"><span data-stu-id="45f92-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="45f92-432">*ストレージ*プラグイン フォルダーのみを選択します。</span><span class="sxs-lookup"><span data-stu-id="45f92-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="45f92-433">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="45f92-433">Microsoft.Data.Services.Client</span></span>

        ![dll のセットを処理しません。](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="45f92-435">チェック、**しないプロセス**ボックス*プラットフォームの設定* をクリック**適用**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![処理は適用されません。](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="45f92-437">私たちはマークするこのプラグイン「プロセスはありません」Unity アセンブリのパッチャがあるこのプラグインを処理できないのためです。</span><span class="sxs-lookup"><span data-stu-id="45f92-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="45f92-438">このプラグインは処理されていない場合でも機能します。</span><span class="sxs-lookup"><span data-stu-id="45f92-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="45f92-439">7 -」の章の azure サービス クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="45f92-440">最初のクラスを作成するには、 *AzureServices*クラス。</span><span class="sxs-lookup"><span data-stu-id="45f92-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="45f92-441">*AzureServices*を担当するクラス。</span><span class="sxs-lookup"><span data-stu-id="45f92-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="45f92-442">Azure アカウントの資格情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="45f92-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="45f92-443">Azure アプリ関数を呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="45f92-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="45f92-444">アップロードと Azure のクラウド ストレージにデータ ファイルのダウンロード。</span><span class="sxs-lookup"><span data-stu-id="45f92-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="45f92-445">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-445">To create this Class:</span></span>

1.  <span data-ttu-id="45f92-446">右クリックし、*資産*フォルダーで、[プロジェクト] パネルにある**作成 > フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create > Folder**.</span></span> <span data-ttu-id="45f92-447">フォルダーの名前**スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-447">Name the folder **Scripts**.</span></span>

    ![新しいフォルダーを作成します。](images/AzureLabs-Lab5-50.png)

    ![フォルダーのスクリプトを呼び出す](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="45f92-450">先ほど作成した、開くフォルダーをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="45f92-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="45f92-451">フォルダー内を右クリックして**作成 >C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-451">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="45f92-452">スクリプトを呼び出す*AzureServices*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="45f92-453">新しいをダブルクリックします。 *AzureServices*クラス ファイルを開く*Visual Studio*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="45f92-454">先頭に次の名前空間を追加、 *AzureServices*:</span><span class="sxs-lookup"><span data-stu-id="45f92-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="45f92-455">内で、次のインスペクター フィールドを追加、 *AzureServices*クラス。</span><span class="sxs-lookup"><span data-stu-id="45f92-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  <span data-ttu-id="45f92-456">内の次のメンバー変数を追加し、 *AzureServices*クラス。</span><span class="sxs-lookup"><span data-stu-id="45f92-456">Then add the following member variables inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="45f92-457">置換するかどうかを確認、*エンドポイント*と*接続文字列*値と、Azure storage からの値が、Azure ポータルで確認</span><span class="sxs-lookup"><span data-stu-id="45f92-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="45f92-458">コードを*Awake()* と*Start()* 今すぐメソッドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="45f92-459">これらのメソッドが、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-459">These methods will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="45f92-460">コードの入力は*CallAzureFunctionForNextShape()* で、[将来章](#chapter-10---completing-the-AzureServices-class)します。</span><span class="sxs-lookup"><span data-stu-id="45f92-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-AzureServices-class).</span></span>

9.  <span data-ttu-id="45f92-461">削除、 *Update()* メソッドのため、このクラスは使用されません。</span><span class="sxs-lookup"><span data-stu-id="45f92-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="45f92-462">Visual Studio で、変更を保存し、Unity に戻ります。</span><span class="sxs-lookup"><span data-stu-id="45f92-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="45f92-463">クリックしてドラッグし、 *AzureServices* Scripts フォルダーからクラスの Main Camera オブジェクトを*階層パネル*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="45f92-464">メイン カメラを選択し、取得、 **AzureStatusText**から下に子オブジェクト、 **GazeButton**オブジェクト、および配置内で、 **AzureStatusText**参照先フィールドに、*インスペクター*への参照を提供する、 *AzureServices*スクリプト。</span><span class="sxs-lookup"><span data-stu-id="45f92-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![テキストの参照先の azure の状態を割り当てる](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="45f92-466">8 - 章 ShapeFactory クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="45f92-467">次のスクリプトを作成するには、 *ShapeFactory*クラス。</span><span class="sxs-lookup"><span data-stu-id="45f92-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="45f92-468">このクラスの役割は、要求されたときに、新しい図形を作成しで作成した図形の履歴を保持する*図形履歴リスト*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="45f92-469">図形が作成されるたびに、*図形履歴リスト*で更新、 *AzureService*クラス、およびに格納し、 *Azure Storage*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="45f92-470">アプリケーションの起動時、格納されているファイルが見つかった場合、 *Azure Storage*、*図形履歴リスト*が取得され、再生で、 **3D テキスト**オブジェクトを提供します。生成された図形がストレージから、または新しいかどうか。</span><span class="sxs-lookup"><span data-stu-id="45f92-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="45f92-471">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-471">To create this class:</span></span>

1.  <span data-ttu-id="45f92-472">移動して、**スクリプト**以前に作成したフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="45f92-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="45f92-473">フォルダー内を右クリックして**作成 >C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-473">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="45f92-474">スクリプトを呼び出す*ShapeFactory*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="45f92-475">新しいをダブルクリックします。 *ShapeFactory*スクリプト ファイルを開く*Visual Studio*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="45f92-476">確認、 *ShapeFactory*クラスには、次の名前空間が含まれています。</span><span class="sxs-lookup"><span data-stu-id="45f92-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="45f92-477">次に示す変数を追加、 *ShapeFactory*クラスし、置換、 *Start()* と*Awake()* と次の関数。</span><span class="sxs-lookup"><span data-stu-id="45f92-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  <span data-ttu-id="45f92-478">*CreateShape()* メソッドに基づいて、指定したプリミティブ図形は生成*整数*パラメーター。</span><span class="sxs-lookup"><span data-stu-id="45f92-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="45f92-479">ブール型パラメーターは、現在作成されている図形は、ストレージからかどうかを指定するために使用または新しいです。</span><span class="sxs-lookup"><span data-stu-id="45f92-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="45f92-480">次のコードを配置、 *ShapeFactory*クラスは、前のメソッドの下。</span><span class="sxs-lookup"><span data-stu-id="45f92-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  <span data-ttu-id="45f92-481">Visual Studio で Unity に戻る前に変更を保存することを確認します。</span><span class="sxs-lookup"><span data-stu-id="45f92-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="45f92-482">戻る Unity エディターで、をクリックし、ドラッグ、 *ShapeFactory*クラスから、**スクリプト**フォルダーを**Main Camera**オブジェクト、*階層パネル*.</span><span class="sxs-lookup"><span data-stu-id="45f92-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="45f92-483">選択したメイン カメラで表示されます、 *ShapeFactory*スクリプト コンポーネントが不足している、 *Spawn ポイント*参照。</span><span class="sxs-lookup"><span data-stu-id="45f92-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="45f92-484">これを修正するには、ドラッグ、 **ShapeSpawnPoint**オブジェクトから、*階層パネル*を**Spawn ポイント**参照先。</span><span class="sxs-lookup"><span data-stu-id="45f92-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![セット図形工場出荷時の参照先](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="45f92-486">9 - 章視線の先クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="45f92-487">最後のスクリプトを作成する必要がありますが、*視線*クラス。</span><span class="sxs-lookup"><span data-stu-id="45f92-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="45f92-488">作成するため、このクラスは、 **Raycast**ユーザーを見て、どのオブジェクトを検出するために、メイン カメラから転送投影されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="45f92-489">Raycast の必要があります、ユーザーが見る場合を識別するためにここで、 **GazeButton**シーン内のオブジェクトし、動作をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="45f92-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="45f92-490">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-490">To create this Class:</span></span>

1.  <span data-ttu-id="45f92-491">移動して、**スクリプト**以前に作成したフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="45f92-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="45f92-492">プロジェクト パネルで、右クリックして**作成 >C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-492">Right-click in the Project Panel, **Create > C# Script**.</span></span> <span data-ttu-id="45f92-493">スクリプトを呼び出す*視線*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="45f92-494">新しいをダブルクリックします。*視線*スクリプト ファイルを開く*Visual Studio。*</span><span class="sxs-lookup"><span data-stu-id="45f92-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="45f92-495">次の名前空間が、スクリプトの先頭に含まれることを確認するには。</span><span class="sxs-lookup"><span data-stu-id="45f92-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="45f92-496">内で、次の変数を追加し、*視線*クラス。</span><span class="sxs-lookup"><span data-stu-id="45f92-496">Then add the following variables inside the *Gaze* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> <span data-ttu-id="45f92-497">これらの変数の一部では編集できなく、*エディター*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="45f92-498">コードを*Awake()* と*Start()* 今すぐメソッドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="45f92-499">と共に開始位置でカーソル オブジェクトを作成する次のコードを追加、 *Update()* GazeEnabled ブール値を切り替えると、Raycast メソッドを実行するメソッド。</span><span class="sxs-lookup"><span data-stu-id="45f92-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. <span data-ttu-id="45f92-500">次を追加、 *UpdateRaycast()* メソッドでは、プロジェクト、Raycast され、ヒットのターゲットを検出します。</span><span class="sxs-lookup"><span data-stu-id="45f92-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. <span data-ttu-id="45f92-501">最後に、追加、 *ResetFocusedObject()* メソッドで、GazeButton オブジェクトの現在色、かどうか、新しい図形を作成しているかどうかを示すとオフが切り替わります。</span><span class="sxs-lookup"><span data-stu-id="45f92-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  <span data-ttu-id="45f92-502">Visual Studio で Unity に戻る前に、変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="45f92-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="45f92-503">クリックしてドラッグし、*視線*Scripts フォルダーからのクラス、 **Main Camera**オブジェクト、*階層パネル*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="45f92-504">第 10 章 – AzureServices クラスの完了</span><span class="sxs-lookup"><span data-stu-id="45f92-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="45f92-505">場所にその他のスクリプトを使用して行うことが今すぐ*完了*、 *AzureServices*クラス。</span><span class="sxs-lookup"><span data-stu-id="45f92-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="45f92-506">これは、によって実現されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="45f92-507">という名前の新しいメソッドを追加する*CreateCloudIdentityAsync()* Azure と通信するために必要な認証の変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="45f92-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="45f92-508">このメソッドは図形の一覧を含んでいる以前に格納されているファイルが存在することも確認します。</span><span class="sxs-lookup"><span data-stu-id="45f92-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="45f92-509">**ファイルが見つかった場合**、ユーザーを無効にするには、*視線*に格納されている、図形のパターンに従って、図形の作成をトリガーし、 **Azure Storage ファイル**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="45f92-510">ユーザーが、これとして表示、**テキスト メッシュ**表示が提供されます 'Storage' または図形の送信元によって ' New' をします。</span><span class="sxs-lookup"><span data-stu-id="45f92-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="45f92-511">**ファイルが見つからない場合**が有効になります、*視線*、見る際に図形を作成するユーザーを有効にすると、 **GazeButton**シーン内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="45f92-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  <span data-ttu-id="45f92-512">次のコード スニペットは、内から、 *Start()* メソッドは、呼び出しができる、 *CreateCloudIdentityAsync()* メソッド。</span><span class="sxs-lookup"><span data-stu-id="45f92-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="45f92-513">現在経由でコピーする自由*Start()* メソッドの下。</span><span class="sxs-lookup"><span data-stu-id="45f92-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  <span data-ttu-id="45f92-514">メソッドのコードを入力*CallAzureFunctionForNextShape()* します。</span><span class="sxs-lookup"><span data-stu-id="45f92-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="45f92-515">使用前に作成した*Azure Function App*図形のインデックスを要求します。</span><span class="sxs-lookup"><span data-stu-id="45f92-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="45f92-516">このメソッドが図形を送信する新しい図形を受信すると、 *ShapeFactory*シーン内に新しい図形を作成するクラス。</span><span class="sxs-lookup"><span data-stu-id="45f92-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="45f92-517">完了の本文を次のコードを使用して*CallAzureFunctionForNextShape()* します。</span><span class="sxs-lookup"><span data-stu-id="45f92-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  <span data-ttu-id="45f92-518">保存することで、図形の履歴リストに格納する整数を連結して文字列を作成するメソッドを追加、 *Azure Storage ファイル*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  <span data-ttu-id="45f92-519">あるファイルに格納されているテキストを取得するメソッドを追加、 *Azure Storage ファイル*と*逆シリアル化*一覧にします。</span><span class="sxs-lookup"><span data-stu-id="45f92-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="45f92-520">このプロセスが完了すると、メソッドを再度有効に、視線の先、ユーザーが図形をシーンに追加できるようにします。</span><span class="sxs-lookup"><span data-stu-id="45f92-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  <span data-ttu-id="45f92-521">Visual Studio で Unity に戻る前に、変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="45f92-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="45f92-522">第 11 章 – UWP ソリューションのビルド</span><span class="sxs-lookup"><span data-stu-id="45f92-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="45f92-523">ビルド プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="45f92-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="45f92-524">移動して**ファイル > のビルド設定**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-524">Go to **File > Build Settings**.</span></span>

    ![アプリをビルドします](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="45f92-526">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45f92-526">Click **Build**.</span></span> <span data-ttu-id="45f92-527">Unity を起動、*ファイル エクスプ ローラー*ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="45f92-528">ここで、そのフォルダーを作成し、名前*アプリ*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="45f92-529">使用し、*アプリ*フォルダーを選択すると、キーを押して**フォルダーの選択**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="45f92-530">Unity にプロジェクトをビルドを開始、*アプリ*フォルダー。</span><span class="sxs-lookup"><span data-stu-id="45f92-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="45f92-531">1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、*ファイル エクスプ ローラー*ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。</span><span class="sxs-lookup"><span data-stu-id="45f92-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="45f92-532">第 12 章 - アプリケーションのデプロイ</span><span class="sxs-lookup"><span data-stu-id="45f92-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="45f92-533">アプリケーションを配置します。</span><span class="sxs-lookup"><span data-stu-id="45f92-533">To deploy your application:</span></span>

1.  <span data-ttu-id="45f92-534">移動し、*アプリ*で作成されたフォルダー、[最後の章](#chapter-11---build-the-uwp-solution)します。</span><span class="sxs-lookup"><span data-stu-id="45f92-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="45f92-535">アプリ名に '.sln' の拡張機能は、する必要がありますをダブルクリックすると、ファイルが表示されます、内で開くために*Visual Studio*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="45f92-536">**ソリューション プラットフォーム**、 **x86、ローカル コンピューター**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="45f92-537">**ソリューション構成**選択**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="45f92-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="45f92-538">Microsoft HoloLens にすることがあります方が簡単なこれを設定する*リモート マシン*、するは、コンピューターにテザリングされたしないようにします。</span><span class="sxs-lookup"><span data-stu-id="45f92-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="45f92-539">ただし、次の操作も必要があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="45f92-540">把握、 **IP アドレス**内では、HoloLens の*設定 > ネットワークとインターネット > Wi-fi > 詳細オプション*;、IPv4 では、アドレスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45f92-540">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="45f92-541">確認**開発者モード**は**で**; で見つかった*設定 > 更新とセキュリティ > 開発者向け*します。</span><span class="sxs-lookup"><span data-stu-id="45f92-541">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![ソリューションを配置します。](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="45f92-543">移動して、**ビルド**メニューをクリックします**ソリューションの配置**をコンピューターにアプリケーションをサイドローディングします。</span><span class="sxs-lookup"><span data-stu-id="45f92-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="45f92-544">アプリが起動され、テストする準備が、インストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="45f92-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="45f92-545">完成した、Azure Functions と Storage アプリケーション</span><span class="sxs-lookup"><span data-stu-id="45f92-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="45f92-546">これで、Azure Functions と Azure Storage の両方のサービスを利用している mixed reality アプリを構築します。</span><span class="sxs-lookup"><span data-stu-id="45f92-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="45f92-547">アプリは格納されたデータは、上に描画し、そのデータに基づいてアクションを提供することになります。</span><span class="sxs-lookup"><span data-stu-id="45f92-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![最終的な製品-終了](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="45f92-549">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="45f92-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="45f92-550">手順 1</span><span class="sxs-lookup"><span data-stu-id="45f92-550">Exercise 1</span></span>

<span data-ttu-id="45f92-551">ポイントとから作成されたオブジェクトの状態を生成するレコードは、2 つ目の生成を作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="45f92-552">データ ファイルを読み込むときに、もともと作成された場所から子の図形を再生します。</span><span class="sxs-lookup"><span data-stu-id="45f92-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="45f92-553">手順 2</span><span class="sxs-lookup"><span data-stu-id="45f92-553">Exercise 2</span></span>

<span data-ttu-id="45f92-554">毎回を再び開くにせずに、アプリを再起動する方法を作成します。</span><span class="sxs-lookup"><span data-stu-id="45f92-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="45f92-555">**シーンを読み込む**は適切なスポットを開始します。</span><span class="sxs-lookup"><span data-stu-id="45f92-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="45f92-556">格納リストをクリアする方法を作成した後、 *Azure Storage*、アプリから簡単にリセットできるようにします。</span><span class="sxs-lookup"><span data-stu-id="45f92-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
