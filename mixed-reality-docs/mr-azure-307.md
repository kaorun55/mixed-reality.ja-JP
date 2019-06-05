---
title: 307 - MR と Azure の Machine learning
description: このコースでは、複合現実のアプリケーション内で Azure Machine Learning Studio を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、machine learning、ml、machine learning studio、hololens、没入型、vr
ms.openlocfilehash: 93263817df0fd809a09b32c1b34a636eab7026a1
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516042"
---
>[!NOTE]
><span data-ttu-id="a4a32-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a4a32-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a4a32-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a4a32-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a4a32-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a4a32-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a4a32-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="a4a32-110">MR と Azure 307 の場合:機械学習</span><span class="sxs-lookup"><span data-stu-id="a4a32-110">MR and Azure 307: Machine learning</span></span>

![最終的な製品-開始](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="a4a32-112">このコースでは、Azure Machine Learning Studio を使用して複合現実のアプリケーションに機械学習 (ML) の機能を追加する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="a4a32-113">*Azure Machine Learning Studio*は、開発者は多数の machine learning のアルゴリズムは、データ入力、出力、準備、およびビジュアル化に役立つ、Microsoft のサービスです。</span><span class="sxs-lookup"><span data-stu-id="a4a32-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="a4a32-114">これらのコンポーネントからの予測分析実験の開発、反復処理、およびモデルのトレーニングに使用することはします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="a4a32-115">次のトレーニングを行うことができます、モデル運用 Azure のクラウド内で新しいデータをスコア付けできるようにします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="a4a32-116">詳細については、次を参照してください。、 [Azure Machine Learning Studio ページ](https://azure.microsoft.com/en-au/services/machine-learning-studio/)します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span></span>

<span data-ttu-id="a4a32-117">このコースを完了すると、複合現実イマーシブ ヘッドセット アプリケーションとは、次の操作方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="a4a32-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="a4a32-118">テーブルを売上データの提供、 *Azure Machine Learning Studio*ポータル、および人気のある項目の将来の売上を予測するアルゴリズムを設計します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="a4a32-119">作成、 **Unity プロジェクト**、受信し、ML サービスからの予測データを解釈することができます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="a4a32-120">内の視覚的に predication データを表示、 **Unity プロジェクト**棚の上、最も人気のある販売品目を提供することにより、します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="a4a32-121">アプリケーションでは、責任ですが、設計と、結果を統合する方法について。</span><span class="sxs-lookup"><span data-stu-id="a4a32-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="a4a32-122">このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。</span><span class="sxs-lookup"><span data-stu-id="a4a32-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="a4a32-123">複合現実アプリを強化するためには、このコース得た知識を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="a4a32-124">このコースは、他の複合現実ラボに直接関係は自己完結型のチュートリアルです。</span><span class="sxs-lookup"><span data-stu-id="a4a32-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="a4a32-125">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="a4a32-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a4a32-126">コース</span><span class="sxs-lookup"><span data-stu-id="a4a32-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a4a32-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a4a32-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a4a32-128"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="a4a32-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="a4a32-129">MR と Azure 307 の場合:機械学習</span><span class="sxs-lookup"><span data-stu-id="a4a32-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="a4a32-130">✔️</span><span class="sxs-lookup"><span data-stu-id="a4a32-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="a4a32-131">✔️</span><span class="sxs-lookup"><span data-stu-id="a4a32-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="a4a32-132">このコースが主に Windows Mixed Reality 没入型 (VR) ヘッドセットを重点的に Microsoft HoloLens には、このコースで学習する内容を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="a4a32-133">コースを実行するとき、HoloLens をサポートするために必要な場合があります変更でノートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="a4a32-134">HoloLens を使用する場合は、音声キャプチャ中にいくつかのエコーが気付きです。</span><span class="sxs-lookup"><span data-stu-id="a4a32-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a4a32-135">前提条件</span><span class="sxs-lookup"><span data-stu-id="a4a32-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="a4a32-136">このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="a4a32-137">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 5 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a4a32-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="a4a32-138">内に一覧表示するには自由に最新のソフトウェアを使用して、[インストール ツール記事](install-the-tools.md)ことについては、このコースでとまったく同じで見つかりますの下に記載されているものよりも新しいソフトウェアでどのようなことは仮定されませんが、.</span><span class="sxs-lookup"><span data-stu-id="a4a32-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="a4a32-139">次のハードウェアとソフトウェアこのコースをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="a4a32-140">開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発</span><span class="sxs-lookup"><span data-stu-id="a4a32-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="a4a32-141">Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="a4a32-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a4a32-142">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="a4a32-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a4a32-143">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="a4a32-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a4a32-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a4a32-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="a4a32-145">A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効</span><span class="sxs-lookup"><span data-stu-id="a4a32-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="a4a32-146">Azure のセットアップと ML データ取得のインターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="a4a32-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="a4a32-147">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="a4a32-147">Before you start</span></span>

<span data-ttu-id="a4a32-148">このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。</span><span class="sxs-lookup"><span data-stu-id="a4a32-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="a4a32-149">第 1 章 - Azure のストレージ アカウントのセットアップ</span><span class="sxs-lookup"><span data-stu-id="a4a32-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="a4a32-150">Azure Translator API を使用するには、アプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="a4a32-151">ログイン、 [Azure Portal](https://portal.azure.com)します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="a4a32-152">Azure アカウントがいない場合は、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="a4a32-153">クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="a4a32-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="a4a32-154">ログインした後は、をクリックして**ストレージ アカウント**左側のメニュー。</span><span class="sxs-lookup"><span data-stu-id="a4a32-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="a4a32-156">単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="a4a32-157">**ストレージ アカウント** タブで、をクリックして**追加**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="a4a32-159">**ストレージ アカウントの作成**パネル。</span><span class="sxs-lookup"><span data-stu-id="a4a32-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="a4a32-160">挿入、**名前**お使いのアカウントに、数字と小文字のみこのフィールドを受け入れるに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a4a32-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="a4a32-161">**デプロイ モデルでは、** 選択**Resource manager**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="a4a32-162">**アカウントの種類**、**ストレージ (汎用 v1)** します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="a4a32-163">**パフォーマンス**、**標準**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="a4a32-164">**レプリケーション**選択**読み取りアクセスの geo 冗長ストレージ (RA-GRS)** します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="a4a32-165">まま**転送が必須のセキュリティで保護された**として**無効になっている**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="a4a32-166">選択、**サブスクリプション**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="a4a32-167">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="a4a32-168">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="a4a32-169">勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。</span><span class="sxs-lookup"><span data-stu-id="a4a32-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="a4a32-170">詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="a4a32-171">確認、**場所**(新しいリソース グループを作成する) 場合は、リソース グループ。</span><span class="sxs-lookup"><span data-stu-id="a4a32-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="a4a32-172">場所は、アプリケーションが実行リージョンにあるが理想的です。</span><span class="sxs-lookup"><span data-stu-id="a4a32-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="a4a32-173">一部の Azure 資産は特定のリージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="a4a32-174">また、このサービスに適用される条件を理解したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="a4a32-176">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="a4a32-177">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="a4a32-179">第 2 章 – Azure の Machine Learning Studio</span><span class="sxs-lookup"><span data-stu-id="a4a32-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="a4a32-180">使用する、 *Azure Machine Learning*アプリケーションに使用可能にする Machine Learning サービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="a4a32-181">Azure Portal をクリックして**新規**左上隅にある検索して**Machine Learning Studio ワークスペース**、キーを押して**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a4a32-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="a4a32-183">新しいページがの説明を入力、 **Machine Learning Studio ワークスペース**サービス。</span><span class="sxs-lookup"><span data-stu-id="a4a32-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="a4a32-184">このダイアログ ボックスの左下にある at をクリックして、**作成**ボタンは、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="a4a32-185">クリックすると**作成**、新しいに関するいくつかの詳細を提供する必要があるパネルが表示されます**Machine Learning Studio service**:</span><span class="sxs-lookup"><span data-stu-id="a4a32-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="a4a32-186">必要な挿入**ワークスペース名**このサービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="a4a32-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="a4a32-187">選択、**サブスクリプション**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="a4a32-188">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="a4a32-189">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="a4a32-190">勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。</span><span class="sxs-lookup"><span data-stu-id="a4a32-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="a4a32-191">詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="a4a32-192">確認、**場所**(新しいリソース グループを作成する) 場合は、リソース グループ。</span><span class="sxs-lookup"><span data-stu-id="a4a32-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="a4a32-193">場所は、アプリケーションが実行リージョンにあるが理想的です。</span><span class="sxs-lookup"><span data-stu-id="a4a32-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="a4a32-194">一部の Azure 資産は特定のリージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="a4a32-195">前の章で、Azure Storage を作成するために使用したのと同じリソース グループを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="a4a32-196">**ストレージ アカウント**セクションで、**既存**、ドロップダウン メニューで、をクリックしておよびそこから、をクリックして、**ストレージ アカウント**最後の章で作成しました。</span><span class="sxs-lookup"><span data-stu-id="a4a32-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="a4a32-197">適切な選択**ワークスペースの価格レベル**ドロップダウン メニューからできます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="a4a32-198">内で、 **Web サービス プラン**セクションで、**作成** **、新しい**テキスト フィールドに名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="a4a32-199">**Web サービス プランの価格レベル**セクションで、任意の価格レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="a4a32-200">テストと呼ばれる層開発**DEVTEST 標準**料金なしで利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="a4a32-201">また、このサービスに適用される条件を理解したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="a4a32-202">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-202">Click **Create**.</span></span>

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="a4a32-204">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="a4a32-205">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="a4a32-207">新しいサービス インスタンスを探索する通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-207">Click on the notification to explore your new Service instance.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="a4a32-209">をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="a4a32-210">表示されるページで、**その他のリンク**セクションで、 **Machine Learning Studio の起動**には、ブラウザーを直接は、 **Machine Learning Studio**ポータルです。</span><span class="sxs-lookup"><span data-stu-id="a4a32-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="a4a32-212">使用して、**サインイン**ボタン、右上にあるか、センターで、Machine Learning Studio にログインします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="a4a32-214">第 3 章 - Machine Learning Studio:データセットのセットアップ</span><span class="sxs-lookup"><span data-stu-id="a4a32-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="a4a32-215">機械学習アルゴリズムの動作方法の 1 つは既存のデータを分析し、将来の結果を予測しように基づいて既存のデータ セット。</span><span class="sxs-lookup"><span data-stu-id="a4a32-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="a4a32-216">通常、つまり、ほどアルゴリズムは将来の結果を予測するのにはするが、必要以上の既存のデータです。</span><span class="sxs-lookup"><span data-stu-id="a4a32-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="a4a32-217">サンプル テーブルは、このコースと呼ばれる[ProductsTableCSV ページでダウンロードできる](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a4a32-218">上記の .zip ファイルには、両方が含まれています、 **ProductsTableCSV**と **.unitypackage**で必要になる[第 6 章](#chapter-6---importing-the-mlproducts-unity-package)します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="a4a32-219">このパッケージが csv ファイルに個別にも、その章で提供されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="a4a32-220">このサンプル データ セットには、2017 年の日付ごとの 1 時間ごとにベストセラーのオブジェクトのレコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a4a32-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Machine Learning Studio:データセットのセットアップ](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="a4a32-222">たとえば、2017年の 1 日目、午後 1 時 (時間 13) で、ベストセラー項目が塩とコショウします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="a4a32-223">このサンプルのテーブルには、9998 エントリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a4a32-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="a4a32-224">戻って、 **Machine Learning Studio**ポータル、としては、このテーブルを追加し、**データセット**ML の。</span><span class="sxs-lookup"><span data-stu-id="a4a32-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="a4a32-225">これをクリックすると、 **+ 新規**画面の左下隅のボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Machine Learning Studio:データセットのセットアップ](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="a4a32-227">セクションを進めていくと内から下、左のナビゲーション パネルがあること。</span><span class="sxs-lookup"><span data-stu-id="a4a32-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="a4a32-228">クリックして**データセット**の右側に**ローカル ファイルから**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Machine Learning Studio:データセットのセットアップ](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="a4a32-230">新しいアップロード**データセット**次の手順。</span><span class="sxs-lookup"><span data-stu-id="a4a32-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="a4a32-231">可能な場合、アップロードのウィンドウが表示**参照**新しいデータセットのハード ドライブ。</span><span class="sxs-lookup"><span data-stu-id="a4a32-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Machine Learning Studio:データセットのセットアップ](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="a4a32-233">選択すると、し、[アップロード] ウィンドウに戻り、ティックのチェック ボックスをオンのままにします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="a4a32-234">次のテキスト フィールドに入力**ProductsTableCSV.csv**データセットの名前として (ただし、自動的に追加する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="a4a32-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="a4a32-235">ドロップダウン メニューを使用して**型**を選択します**汎用 CSV ファイル (.csv) ヘッダー**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="a4a32-236">アップロードのウィンドウの右下でチェック マークを押して、**データセット**がアップロードされます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="a4a32-237">第 4 章 - Machine Learning Studio:実験</span><span class="sxs-lookup"><span data-stu-id="a4a32-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="a4a32-238">機械学習システムを作成するには、理論的には、データについての検証に、実験を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="a4a32-239">結果と共に、データと考えられる結果の間の相関関係がない場合または複数のデータが必要かどうかがわかります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="a4a32-240">実験の作成を開始するには。</span><span class="sxs-lookup"><span data-stu-id="a4a32-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="a4a32-241">再びクリックして、 **+ 新規**、ページの左下のボタンをクリックし、**実験** > **空白の実験**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="a4a32-243">空白の実験では、新しいページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="a4a32-244">左側のパネルから展開 **保存されたデータセット* > *My Datasets** をドラッグし、 **ProductsTableCSV**に、**実験キャンバス**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-244">From the panel on the left expand **Saved Datasets* > *My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="a4a32-246">左側のパネルで**データ変換** > **サンプルおよび分割**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="a4a32-247">ドラッグし、**データの分割**で項目を**実験キャンバス**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="a4a32-248">分割されたデータ項目では、データ セットを 2 つの部分に分割します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="a4a32-249">機械学習アルゴリズムのトレーニングに使用する 1 つの部分。</span><span class="sxs-lookup"><span data-stu-id="a4a32-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="a4a32-250">2 番目の部分は生成されたアルゴリズムの精度を評価するためには。</span><span class="sxs-lookup"><span data-stu-id="a4a32-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="a4a32-252">(キャンバス上の項目が選択されている分割データ) の中に右側のパネルで編集、**最初の出力データセット内の行の割合**に**0.7**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="a4a32-253">これは、データの 2 つの部分の分割、最初の部分は、データの 70% になります、および 2 番目の部分は、残りの 30% になります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="a4a32-254">データがランダムに分割することを確認するため、確認、**ランダム分割**チェック ボックスが選択されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="a4a32-256">ベースからの接続をドラッグして、 **ProductsTableCSV**分割されたデータ項目の先頭に、キャンバス上の項目。</span><span class="sxs-lookup"><span data-stu-id="a4a32-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="a4a32-257">項目を接続が送信され、 **ProductsTableCSV**入力データを分割するデータセットの出力 (データ)。</span><span class="sxs-lookup"><span data-stu-id="a4a32-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="a4a32-259">**実験**左側のパネルで、展開 \**Machine Learning* > \* \* \* トレーニングします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-259">In the **Experiments** panel on the left side, expand \**Machine Learning* > \*Train\*\*.</span></span> <span data-ttu-id="a4a32-260">ドラッグ、**モデルのトレーニング**を実験キャンバスにアウト項目。</span><span class="sxs-lookup"><span data-stu-id="a4a32-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="a4a32-261">キャンバスは同じになりますの下。</span><span class="sxs-lookup"><span data-stu-id="a4a32-261">Your canvas should look the same as the below.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="a4a32-263">***左下にある***の**データの分割**項目への接続をドラッグして、**右を上位**の**モデルのトレーニング**項目。</span><span class="sxs-lookup"><span data-stu-id="a4a32-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="a4a32-264">アルゴリズムのトレーニングにモデルのトレーニングによってデータセットから最初の 70% の分割が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="a4a32-266">選択、**モデルのトレーニング**項目と、キャンバスで、**プロパティ**(ブラウザーのウィンドウの右側にある) [パネル] をクリックして、**列セレクターの起動**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="a4a32-267">テキスト ボックスに「**製品**しキーを押します**Enter**、*製品*予測をトレーニングする列として設定されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="a4a32-268">次に、をクリックして、**ティック**下部右上隅にある選択ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="a4a32-270">トレーニングする、**多クラス ロジスティック回帰**最も販売を予測するアルゴリズム**製品**曜日と日付の 1 時間に基づきます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="a4a32-271">ただし、Azure Machine Learning studio で提供されるさまざまなアルゴリズムの詳細については、このドキュメントの範囲を超えては次のようにから詳細情報を調べることができます、 [Machine Learning アルゴリズム チート シート](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="a4a32-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="a4a32-272">左側の実験項目パネルでは、次のように展開します \* **Machine Learning* > *モデルの初期化*> \* 分類 \* \* *、およびドラッグ、\*\*多クラス ロジスティック回帰。** を実験キャンバス上に項目。</span><span class="sxs-lookup"><span data-stu-id="a4a32-272">From the experiment items panel on the left, expand \*\**Machine Learning* > *Initialize Model* > \*Classification\*\*\*, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="a4a32-273">一番下から、出力を接続、**多クラス ロジスティック回帰**、左の入力に、**モデルのトレーニング**項目。</span><span class="sxs-lookup"><span data-stu-id="a4a32-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="a4a32-275">左側のパネルの 実験項目の一覧で展開 \**Machine Learning* > \* スコア \* \*、ドラッグ、**モデルのスコア付け**をキャンバス上に項目。</span><span class="sxs-lookup"><span data-stu-id="a4a32-275">In list of experiment items in the panel on the left, expand \**Machine Learning* > \*Score\*\*, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="a4a32-276">一番下から、出力を接続、**モデルのトレーニング**、左の入力に、**モデルのスコア付け**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="a4a32-277">右下の出力を接続**データの分割**、右の入力に、 \**モデルのスコア付け*項目\*します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model* item*.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="a4a32-279">一覧で**実験**、左側のパネルでアイテムの展開 \* \**Machine Learning* > \* 評価 \* \* \*、およびドラッグ、**モデルの評価**をキャンバスに項目。</span><span class="sxs-lookup"><span data-stu-id="a4a32-279">In the list of **Experiment** items in the panel on the left, expand \*\**Machine Learning* > \*Evaluate\*\*\*, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="a4a32-280">出力を接続、**モデルのスコア付け**の左の入力に、**モデルの評価**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="a4a32-282">最初の Machine Learning の実験を構築したとします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="a4a32-283">保存し、実験を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-283">You can now save and run the experiment.</span></span> <span data-ttu-id="a4a32-284">ページの下部にあるメニューをクリックして、**保存**ボタンをクリックして、実験を保存**実行**実験の先頭にします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="a4a32-286">確認できます、**状態**実験キャンバスの上部右にあるのです。</span><span class="sxs-lookup"><span data-stu-id="a4a32-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="a4a32-287">実験を完了するまで数分を待機します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="a4a32-288">ビッグ (実際) のデータセットがある場合は、実験に実行する時間がかかる場合があります、高くなります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="a4a32-290">右クリックして、**モデルの評価**キャンバスでは、コンテキスト メニュー ホバーからマウスで項目**評価の結果を**を選択し、**視覚化**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="a4a32-292">実際の結果と予測結果を表示、評価結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="a4a32-293">これは、モデルの評価が以前では、分割された元のデータセットの 30% を使用します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="a4a32-294">結果は優れた、理想的には必要があります最上位の番号各行の列に含められる、選択された項目を確認できます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="a4a32-296">閉じる、**結果**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-296">Close the **Results**.</span></span>

24. <span data-ttu-id="a4a32-297">として公開する必要がある、新しくトレーニングされた機械学習モデルを使用する、 **Web サービス**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="a4a32-298">これを行うには、をクリックして、 **Web サービスの設定**メニューで、ページの下部にあるメニュー項目をクリックします**予測 Web サービス**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="a4a32-300">新しいタブが作成され、モデルのトレーニングは、新しい web サービスを作成するマージします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="a4a32-301">ページの下部にあるメニューでクリックして**保存**、順にクリックします**実行**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="a4a32-302">実験キャンバスの右上隅にある更新の状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="a4a32-304">実行が完了すると、 **Web サービスのデプロイ**ボタンがページの下部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="a4a32-305">Web サービスをデプロイする準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="a4a32-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="a4a32-306">クリックして**Web サービスのデプロイ**ページの下部にあるメニューでは (クラシック)。</span><span class="sxs-lookup"><span data-stu-id="a4a32-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="a4a32-308">お使いのブラウザーが行う必要がありますポップアップを許可する要求があります**許可**キーを押す必要がありますが、 **Web サービスのデプロイ**、もう一度デプロイ ページが表示されない場合。</span><span class="sxs-lookup"><span data-stu-id="a4a32-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="a4a32-309">実験を作成した後にリダイレクトされます、**ダッシュ ボード**する必要があるページ、 **API キー**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="a4a32-310">今のところ、メモ帳にコピー、必要になるコードに非常に早くします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="a4a32-311">をクリックすると、API キーをメモ、**要求/応答**ボタン、**既定のエンドポイント**セクション、キーの下にあります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="a4a32-313">このページで [テスト] をクリックした場合は、入力データを入力し、出力を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="a4a32-314">入力、**日**と**時間**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="a4a32-315">ままに、**製品**空白エントリ。</span><span class="sxs-lookup"><span data-stu-id="a4a32-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="a4a32-316">をクリックし、**確認**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="a4a32-317">選択されている各製品の尤度を表す JSON は、ページの下部にある出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="a4a32-318">新しい web ページが指示と、Machine Learning Studio で必要な要求の構造について例をいくつかの表示を開きます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="a4a32-319">コピー、**要求 URI**メモ帳に、このページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="a4a32-321">Machine learning の日、年の通算日の時間に関連付け、購入履歴データに基づいて、販売できる可能性が最も高い製品を提供するシステムをビルドが完了しました。</span><span class="sxs-lookup"><span data-stu-id="a4a32-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="a4a32-322">Web サービスを呼び出すには、サービス エンドポイントとサービスの API キーの URL を必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="a4a32-323">をクリックして、 **Consume**  タブで、上部のメニューから。</span><span class="sxs-lookup"><span data-stu-id="a4a32-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="a4a32-324">**消費**情報 ページをコードから web サービスを呼び出す必要があります情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="a4a32-325">コピーを作成、**主キー**と**要求-応答**URL。</span><span class="sxs-lookup"><span data-stu-id="a4a32-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="a4a32-326">[次へ] の章で必要になります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="a4a32-327">第 5 章 - Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="a4a32-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="a4a32-328">設定し、混合 Reality イマーシブ ヘッドセットをテストします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="a4a32-329">**いない**このコースのモーションのコント ローラーが必要です。</span><span class="sxs-lookup"><span data-stu-id="a4a32-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="a4a32-330">イマーシブ ヘッドセットの設定をサポートする場合をクリックしてください[ここ](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="a4a32-331">開いている**Unity**という新しい Unity プロジェクトを作成および**MR\_MachineLearning します。**</span><span class="sxs-lookup"><span data-stu-id="a4a32-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="a4a32-332">必ず、プロジェクトの種類に設定されて**3D**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="a4a32-333">既定値を確認する必要が開いている Unity、 **スクリプト エディター** に設定されている **Visual Studio** します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="a4a32-334">移動して ***編集* > *設定*** し、新しいウィンドウに移動 **外部ツール** します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-334">Go to ***Edit* > *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="a4a32-335">変更 **External Script Editor** に **Visual Studio 2017** します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="a4a32-336">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="a4a32-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="a4a32-337">次に移動 ***ファイル* > *Build Settings*** にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして***スイッチ プラットフォーム***ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-337">Next, go to ***File* > *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="a4a32-338">確認します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="a4a32-339">**デバイスを対象に**に設定されている**任意のデバイス**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="a4a32-340">Microsoft HoloLens、設定**ターゲット デバイス**に*HoloLens*します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="a4a32-341">**ビルドの種類**に設定されている**D3D**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="a4a32-342">**SDK**に設定されている**インストールされている最新**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="a4a32-343">**Visual Studio バージョン**に設定されている**インストールされている最新**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="a4a32-344">**ビルドおよび実行**に設定されている**ローカル マシン**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="a4a32-345">設定する方法について気にかけないように**シーン**、現時点で、これらは後で説明します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="a4a32-346">残りの設定は、ここでは、既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-346">The remaining settings should be left as default for now.</span></span>

        ![Unity プロジェクトの設定](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="a4a32-348">**Build Settings**ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、**インスペクター**が配置されています。</span><span class="sxs-lookup"><span data-stu-id="a4a32-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="a4a32-349">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="a4a32-350">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="a4a32-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="a4a32-351">**Scripting** **ランタイム バージョン**べき**試験的**(.NET 4.6 Equivalent)</span><span class="sxs-lookup"><span data-stu-id="a4a32-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="a4a32-352">**バックエンドの scripting**べき ***.NET***</span><span class="sxs-lookup"><span data-stu-id="a4a32-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="a4a32-353">**API の互換性レベル**べき **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="a4a32-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Unity プロジェクトの設定](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="a4a32-355">内で、**発行の設定**] タブの [**機能**、確認してください。</span><span class="sxs-lookup"><span data-stu-id="a4a32-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="a4a32-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="a4a32-356">**InternetClient**</span></span>

            ![Unity プロジェクトの設定](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="a4a32-358">パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます</span><span class="sxs-lookup"><span data-stu-id="a4a32-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Unity プロジェクトの設定](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="a4a32-360">戻り**Build Settings** *Unity C#* プロジェクトが不要になったグレー; これの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="a4a32-361">ビルド設定ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="a4a32-362">プロジェクトを保存 (**ファイル > プロジェクトを保存**)。</span><span class="sxs-lookup"><span data-stu-id="a4a32-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="a4a32-363">第 6 章 – MLProducts Unity パッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="a4a32-364">このコースでは、という名前の Unity アセット パッケージをダウンロードする必要があります[ **Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="a4a32-365">このパッケージは、すべてのオブジェクトを使用した、シーンを構築済みので、すべての作業に集中できます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="a4a32-366">**ShelfKeeper**スクリプトを提供すると、ただしのみシーン セットアップ構造の目的で、パブリック変数が保持されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="a4a32-367">その他のすべてのセクションを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="a4a32-368">このパッケージをインポートするには。</span><span class="sxs-lookup"><span data-stu-id="a4a32-368">To import this package:</span></span>

1.  <span data-ttu-id="a4a32-369">前 Unity ダッシュ ボード をクリックして**資産**画面の上部にあるメニューでクリックして**Import Package、カスタム パッケージ**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![MLProducts Unity パッケージをインポートします。](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="a4a32-371">ファイル ピッカーを使用して、 **Azure-MR-307.unitypackage**パッケージ化し、をクリックして**オープン**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="a4a32-372">この資産のコンポーネントの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="a4a32-373">クリックして、インポートを確認します。**インポート**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-373">Confirm the import by clicking **Import**.</span></span>

    ![MLProducts Unity パッケージをインポートします。](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="a4a32-375">インポートが完了、いくつかの新しいフォルダーが、Unity で登場したことがわかりますが**プロジェクト パネル**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="a4a32-376">これらは、3 D モデルとそれぞれの資料では、事前に作成されたシーンの部分です。</span><span class="sxs-lookup"><span data-stu-id="a4a32-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="a4a32-377">このコースでは、コードの大部分を記述します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-377">You will write the majority of the code in this course.</span></span>

    ![MLProducts Unity パッケージをインポートします。](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="a4a32-379">内で、**プロジェクト パネル**フォルダーをクリックして、**シーン**フォルダー、double、シーン内をクリックする (と呼ばれる**MR_MachineLearningScene**)。</span><span class="sxs-lookup"><span data-stu-id="a4a32-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="a4a32-380">シーンが開きます (下図を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="a4a32-380">The scene will open (see image below).</span></span> <span data-ttu-id="a4a32-381">赤い菱形が不足している場合は、クリックして、**ギズモ**上部のボタンの右、**ゲーム パネル**。</span><span class="sxs-lookup"><span data-stu-id="a4a32-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![MLProducts Unity パッケージをインポートします。](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="a4a32-383">第 7 章 - Unity で Dll を確認</span><span class="sxs-lookup"><span data-stu-id="a4a32-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="a4a32-384">(シリアル化と逆シリアル化に使用)、JSON ライブラリの使用を活用して、Newtonsoft DLL で取り込まれたパッケージに実装されています。</span><span class="sxs-lookup"><span data-stu-id="a4a32-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="a4a32-385">ライブラリは、(特に問題が発生したコードが動作していない) 場合を確認する必要が、構成を適切にすることが必要です。</span><span class="sxs-lookup"><span data-stu-id="a4a32-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="a4a32-386">次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a4a32-386">To do so:</span></span>

-  <span data-ttu-id="a4a32-387">Plugins フォルダー内のファイルを Newtonsoft を左クリックを見て、**インスペクター パネル**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="a4a32-388">確認**Any プラットフォーム**がオンになっています。</span><span class="sxs-lookup"><span data-stu-id="a4a32-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="a4a32-389">移動、 **UWP タブ**も確認してください**処理しない**がオンになっています。</span><span class="sxs-lookup"><span data-stu-id="a4a32-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Unity で、Dll のインポート](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="a4a32-391">8 - 章 ShelfKeeper クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="a4a32-392">**ShelfKeeper**クラスは、UI とシーンで製品を制御するメソッドをホストします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="a4a32-393">インポート元のパッケージの一部としてが与えられているこのクラスは、不完全な場合。</span><span class="sxs-lookup"><span data-stu-id="a4a32-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="a4a32-394">そのクラスの所要時間はようになりました。</span><span class="sxs-lookup"><span data-stu-id="a4a32-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="a4a32-395">ダブルクリック、 **ShelfKeeper**スクリプト内で、**スクリプト**フォルダー、ファイルを開く**Visual Studio 2017**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="a4a32-396">既存の日付と時刻を設定し、製品を表示するメソッドを持つ次のコードでのスクリプトですべてのコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  <span data-ttu-id="a4a32-397">変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="a4a32-398">Unity エディターで戻ることを確認、 **ShelfKeeper**クラスの下。</span><span class="sxs-lookup"><span data-stu-id="a4a32-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![ShelfKeeper クラスを作成します。](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="a4a32-400">スクリプト参照のターゲットを持たない場合 (つまり *(テキスト メッシュ) 日付*) から対応するオブジェクトをドラッグするだけ、**階層パネル**、ターゲット フィールドにします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="a4a32-401">以下をご覧ください詳細については、必要な場合。</span><span class="sxs-lookup"><span data-stu-id="a4a32-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="a4a32-402">開く、 **Spawn ポイント**内で配列、 **ShelfKeeper**をクリックしてコンポーネントのスクリプト。</span><span class="sxs-lookup"><span data-stu-id="a4a32-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="a4a32-403">サブ セクションが呼び出された表示**サイズ**配列のサイズを示します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="a4a32-404">型**3**  の隣にテキスト ボックスに**サイズ**キーを押します**Enter**、下にある 3 つのスロットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="a4a32-405">内で、**階層**展開、**時間表示**(横にある矢印をクリック) でのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a4a32-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="a4a32-406">次にをクリックして、 ***Main Camera***内から、**階層**するように、**インスペクター**その情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="a4a32-407">選択、**メイン カメラ**で、**階層パネル**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="a4a32-408">ドラッグ、**日付**と**時間**オブジェクトから、**階層パネル**を**日付のテキスト**と**時テキスト**内のスロット、**インスペクター**の**Main Camera**で、 **ShelfKeeper**コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="a4a32-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="a4a32-409">ドラッグ、 **Spawn ポイント**から、**階層パネル**(下にある、*棚*オブジェクト) を**3** **要素**下にあるターゲットの参照、 **Spawn ポイント**配列を図のようにします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![ShelfKeeper クラスを作成します。](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="a4a32-411">9 - 章 ProductPrediction クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="a4a32-412">次のクラスを作成することには、 **ProductPrediction**クラス。</span><span class="sxs-lookup"><span data-stu-id="a4a32-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="a4a32-413">このクラスは、責任を負います。</span><span class="sxs-lookup"><span data-stu-id="a4a32-413">This class is responsible for:</span></span>

-   <span data-ttu-id="a4a32-414">クエリを実行する、 **Machine Learning サービス**インスタンス、現在の日付と時刻を提供します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="a4a32-415">使用可能なデータには、JSON 応答を逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="a4a32-416">推奨される 3 つの製品を取得する、データを解釈します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="a4a32-417">呼び出す、 **ShelfKeeper**クラス、シーン内のデータを表示するメソッド。</span><span class="sxs-lookup"><span data-stu-id="a4a32-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="a4a32-418">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-418">To create this class:</span></span>

1.  <span data-ttu-id="a4a32-419">移動して、**スクリプト**フォルダーで、**プロジェクト パネル**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="a4a32-420">フォルダー内を右クリックして**作成** > **C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-420">Right-click inside the folder, **Create** > **C\# Script**.</span></span> <span data-ttu-id="a4a32-421">スクリプトを呼び出す**ProductPrediction**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="a4a32-422">新しいをダブルクリックします。 **ProductPrediction**スクリプト ファイルを開く**Visual Studio 2017**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="a4a32-423">場合、**ファイル変更の検出**ダイアログ ポップアップ、 をクリック \***ソリューションの再読み込み**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="a4a32-424">ProductPrediction クラスの先頭に次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  <span data-ttu-id="a4a32-425">内で、 **ProductPrediction**クラスは、多数の入れ子になったクラスの構成は次の 2 つのオブジェクトを挿入します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="a4a32-426">これらのクラスは、Machine Learning サービスの JSON を逆シリアル化およびシリアル化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  <span data-ttu-id="a4a32-427">(その JSON では、コードは、以下の他のすべてのコードとの間の方法は、スクリプトの下部に関連する) は、前のコードの上、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="a4a32-428">挿入することを確認、**主キー**と**要求-応答エンドポイント**、マシン ラーニング ポータルでの変数をここにします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="a4a32-429">イメージの下には、場所が取得したキーとエンドポイントを表示します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Machine Learning Studio:実験](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio:実験](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="a4a32-432">このコード内で挿入、 **Start()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="a4a32-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="a4a32-433">**Start()** クラス初期化メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-433">The **Start()** method is called when the class initializes:</span></span>

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  <span data-ttu-id="a4a32-434">Windows から日付と時刻を収集し、Machine Learning の実験は、テーブルに格納されたデータを比較に使用できる形式に変換するメソッドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. <span data-ttu-id="a4a32-435">できます**削除**、 **Update()** メソッドのため、このクラスは使用されません。</span><span class="sxs-lookup"><span data-stu-id="a4a32-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="a4a32-436">現在の日付と時刻を Machine Learning のエンドポイントと通信、JSON 形式で応答を受信する次のメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialise the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. <span data-ttu-id="a4a32-437">JSON の応答を逆シリアル化およびを逆シリアル化の結果との通信を担当する次のメソッドを追加、 **ShelfKeeper**クラス。</span><span class="sxs-lookup"><span data-stu-id="a4a32-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="a4a32-438">この結果は、現在の日付と時刻にほとんどの販売を予測する 3 つの項目の名前になります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="a4a32-439">次のコードを挿入、 **ProductPrediction**前のメソッドの下のクラス。</span><span class="sxs-lookup"><span data-stu-id="a4a32-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. <span data-ttu-id="a4a32-440">保存**Visual Studio**に戻る**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="a4a32-441">ドラッグ、 **ProductPrediction**クラスからのスクリプト、**スクリプト**フォルダーに、 **Main Camera**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a4a32-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="a4a32-442">シーンとプロジェクトを保存**ファイル** >  ***Save Scene* / *ファイル***  >  **プロジェクトを保存**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-442">Save your scene and project **File** > ***Save Scene* / *File*** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="a4a32-443">第 10 章 – UWP ソリューションのビルド</span><span class="sxs-lookup"><span data-stu-id="a4a32-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="a4a32-444">今度は UWP ソリューションでプロジェクトをビルドするには、スタンドアロン アプリケーションとして実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="a4a32-445">作成する方法。</span><span class="sxs-lookup"><span data-stu-id="a4a32-445">To Build:</span></span>

1.  <span data-ttu-id="a4a32-446">現在のシーンを保存 をクリックして**ファイル** **保存シーン**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-446">Save the current scene by clicking on **File** **Save Scenes**.</span></span>

2.  <span data-ttu-id="a4a32-447">移動して**ファイル** **ビルド設定**</span><span class="sxs-lookup"><span data-stu-id="a4a32-447">Go to **File** **Build Settings**</span></span>

3.  <span data-ttu-id="a4a32-448">チェック ボックスと呼ばれる**Unity C\#プロジェクト**(これは重要なビルドが完了した後に、クラスを編集することを許可することがあるため)。</span><span class="sxs-lookup"><span data-stu-id="a4a32-448">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="a4a32-449">をクリックして**開くシーンを追加**、</span><span class="sxs-lookup"><span data-stu-id="a4a32-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="a4a32-450">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-450">Click **Build**.</span></span>

    ![UWP のソリューションを構築します。](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="a4a32-452">ソリューションをビルドするフォルダーを選択するように促されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="a4a32-453">作成、**ビルド**フォルダーとそのフォルダー内には、任意の適切な名前を別のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="a4a32-454">新しいフォルダーをクリックし、クリックして**フォルダーの選択**の場所にビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![UWP のソリューションを構築します。](images/AzureLabs-Lab7-55.png)

    ![UWP のソリューションを構築します。](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="a4a32-457">1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。</span><span class="sxs-lookup"><span data-stu-id="a4a32-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="a4a32-458">章 11 - アプリケーションをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="a4a32-459">アプリケーションを配置します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-459">To deploy your application:</span></span>

1.  <span data-ttu-id="a4a32-460">新しい Unity ビルドに移動します (、**アプリ**フォルダー) とソリューション ファイルを開くと**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="a4a32-461">Visual Studio を開き、NuGet パッケージの復元、MachineLearningLab_Build ソリューション、ソリューション エクスプ ローラーを (Visual Studio の右側にあります) を右クリックし、NuGet パッケージの復元を行うことが可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![NuGet パッケージを追加します。](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="a4a32-463">ソリューション構成の選択で**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="a4a32-464">ソリューション プラットフォーム で選択**x86**、**ローカル マシン**します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="a4a32-465">Microsoft HoloLens にすることがあります方が簡単なこれを設定する*リモート マシン*、するは、コンピューターにテザリングされたしないようにします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="a4a32-466">ただし、次の操作も必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="a4a32-467">把握、 **IP アドレス**内では、HoloLens の*設定 > ネットワークとインターネット > Wi-fi > 詳細オプション*;、IPv4 では、アドレスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a32-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="a4a32-468">確認**開発者モード**は**で**; で見つかった*設定 > 更新とセキュリティ > 開発者向け*します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![NuGet パッケージを追加します。](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="a4a32-470">移動して**ビルド メニュー**  をクリック**ソリューションの配置**を PC にアプリケーションをサイドローディングします。</span><span class="sxs-lookup"><span data-stu-id="a4a32-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="a4a32-471">アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="a4a32-472">複合現実のアプリケーションを実行するときに Unity シーンに設定されていたベンチは表示され、初期化、Azure 内で設定したデータのフェッチされます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="a4a32-473">データは、アプリケーション内に逆シリアル化して、現在の日付と時刻の上位 3 つの結果を視覚的に、3 つのモデル、ベンチで提供されます。</span><span class="sxs-lookup"><span data-stu-id="a4a32-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="a4a32-474">完成した Machine Learning アプリケーション</span><span class="sxs-lookup"><span data-stu-id="a4a32-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="a4a32-475">これで、データの予測を作成し、シーンに表示する Azure Machine Learning を利用している mixed reality アプリを構築します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![NuGet パッケージを追加します。](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="a4a32-477">演習</span><span class="sxs-lookup"><span data-stu-id="a4a32-477">Exercise</span></span>

<span data-ttu-id="a4a32-478">**手順 1**</span><span class="sxs-lookup"><span data-stu-id="a4a32-478">**Exercise 1**</span></span>

<span data-ttu-id="a4a32-479">実験で、アプリケーションの並べ替え順序あり、このデータ可能性のある役に立つことも、棚に表示される下部にある 3 つの予測が。</span><span class="sxs-lookup"><span data-stu-id="a4a32-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="a4a32-480">**手順 2**</span><span class="sxs-lookup"><span data-stu-id="a4a32-480">**Exercise 2**</span></span>

<span data-ttu-id="a4a32-481">使用して**Azure Tables**気象情報を含む新しいテーブルを設定して、データを使用して新しい実験を作成します。</span><span class="sxs-lookup"><span data-stu-id="a4a32-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
