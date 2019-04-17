---
title: 様、Azure の 302 - Computer vision
description: このコースでは、複合現実のアプリケーションで Azure の Computer Vision を使用して、指定されたイメージ内のビジュアルのコンテンツを認識する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、コンピューター ビジョン、没入型、hololens、vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597891"
---
>[!NOTE]
><span data-ttu-id="c8a71-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c8a71-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c8a71-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c8a71-106">これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c8a71-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c8a71-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c8a71-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="c8a71-110">MR と Azure 302:コンピューター ビジョン</span><span class="sxs-lookup"><span data-stu-id="c8a71-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="c8a71-111">このコースでは複合現実のアプリケーションで Azure の Computer Vision の機能を使用して、指定されたイメージ内のビジュアルのコンテンツを認識する方法についてはします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="c8a71-112">認識の結果がわかりやすいタグとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="c8a71-113">このサービスは、機械学習モデルをトレーニングすることがなく使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="c8a71-114">実装では、機械学習モデルをトレーニングする必要がある場合は、次を参照してください。 [MR と Azure 302b](mr-azure-302b.md)します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![ラボの結果](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="c8a71-116">Microsoft Computer Vision には、すべてクラウドから高度なアルゴリズムを使用してイメージ処理と (戻り値情報の場合) を使用した分析を開発者に提供するように設計 Api のセットです。</span><span class="sxs-lookup"><span data-stu-id="c8a71-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="c8a71-117">開発者は、イメージまたは画像の URL をアップロードし、Microsoft Computer Vision API アルゴリズムがビジュアルのコンテンツを分析し、情報を返すことができる、ユーザーを選択した入力に基づいて人の顔 (を検出を含む、型と、イメージの品質を識別します。それぞれの座標を返す)、およびタグ付け、または画像を分類します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="c8a71-118">詳細については、次を参照してください。、 [Azure Computer Vision API ページ](https://azure.microsoft.com/services/cognitive-services/computer-vision/)します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="c8a71-119">このコースを完了すると、複合現実は、次のことが、HoloLens のアプリケーションが用意されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="c8a71-120">タップ ジェスチャを使用して、HoloLens のカメラはイメージをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="c8a71-121">イメージは、Azure コンピューター ビジョンの API サービスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="c8a71-122">認識されるオブジェクトは、Unity シーンに配置されている単純な UI グループに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="c8a71-123">アプリケーションでは、責任ですが、設計と、結果を統合する方法について。</span><span class="sxs-lookup"><span data-stu-id="c8a71-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="c8a71-124">このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。</span><span class="sxs-lookup"><span data-stu-id="c8a71-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="c8a71-125">複合現実アプリを強化するためには、このコース得た知識を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="c8a71-126">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="c8a71-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c8a71-127">コース</span><span class="sxs-lookup"><span data-stu-id="c8a71-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c8a71-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c8a71-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c8a71-129"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="c8a71-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c8a71-130">MR と Azure 302:コンピューター ビジョン</span><span class="sxs-lookup"><span data-stu-id="c8a71-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="c8a71-131">✔️</span><span class="sxs-lookup"><span data-stu-id="c8a71-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c8a71-132">✔️</span><span class="sxs-lookup"><span data-stu-id="c8a71-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="c8a71-133">このコースは、HoloLens で主にフォーカスします、Windows Mixed Reality 没入型 (VR) ヘッドセットには、このコースで学習する内容を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="c8a71-134">(VR) のイマーシブ ヘッドセットはアクセス可能な cameras があるないため、外部のカメラを PC に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="c8a71-135">コースを実行するとき、没入型の (VR) ヘッドセットをサポートするために使用する必要があります変更でノートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c8a71-136">前提条件</span><span class="sxs-lookup"><span data-stu-id="c8a71-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="c8a71-137">このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="c8a71-138">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 5 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c8a71-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="c8a71-139">内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)ことについては、このコースでとまったく同じで見つかりますの下に記載されているものよりも新しいソフトウェアでどのようなことは仮定されませんが、記事.</span><span class="sxs-lookup"><span data-stu-id="c8a71-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="c8a71-140">次のハードウェアとソフトウェアこのコースをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="c8a71-141">開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発</span><span class="sxs-lookup"><span data-stu-id="c8a71-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="c8a71-142">Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="c8a71-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c8a71-143">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="c8a71-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c8a71-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="c8a71-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c8a71-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c8a71-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="c8a71-146">A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効</span><span class="sxs-lookup"><span data-stu-id="c8a71-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="c8a71-147">(イマーシブ ヘッドセット開発) は、PC に接続されているカメラ</span><span class="sxs-lookup"><span data-stu-id="c8a71-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="c8a71-148">Azure のセットアップおよび Computer Vision API 取得するためのインターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="c8a71-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c8a71-149">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="c8a71-149">Before you start</span></span>

1.  <span data-ttu-id="c8a71-150">このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。</span><span class="sxs-lookup"><span data-stu-id="c8a71-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="c8a71-151">設定して、HoloLens をテストします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="c8a71-152">場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="c8a71-153">(場合によって役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときに、調整とセンサーのチューニングを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="c8a71-154">調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="c8a71-155">センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="c8a71-156">第 1 章 – Azure Portal</span><span class="sxs-lookup"><span data-stu-id="c8a71-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="c8a71-157">使用する、 *Computer Vision API*サービス、Azure でアプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="c8a71-158">最初に、ログイン、 [Azure Portal](https://portal.azure.com)します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="c8a71-159">Azure アカウントがいない場合は、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="c8a71-160">クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="c8a71-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="c8a71-161">ログインした後は、をクリックして**新規**左上隅にある検索して*Computer Vision API*、 をクリック**Enter**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![Azure で新しいリソースを作成します。](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="c8a71-163">単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="c8a71-164">新しいページがの説明を入力、 *Computer Vision API*サービス。</span><span class="sxs-lookup"><span data-stu-id="c8a71-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="c8a71-165">このページの左下にある at、**作成**ボタンは、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![コンピューター ビジョンの api サービスについて](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="c8a71-167">クリックすると**作成**:</span><span class="sxs-lookup"><span data-stu-id="c8a71-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="c8a71-168">必要な挿入**名前**このサービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="c8a71-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="c8a71-169">選択、**サブスクリプション**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="c8a71-170">選択、**価格レベル**場合、これは、最初に、適切な時間を作成する、 *Computer Vision API*サービス、(F0 という名前)、free レベルを使用可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="c8a71-171">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c8a71-172">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c8a71-173">勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。</span><span class="sxs-lookup"><span data-stu-id="c8a71-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="c8a71-174">詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="c8a71-175">(新しいリソース グループを作成する) 場合は、リソース グループの場所を決定します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="c8a71-176">場所は、アプリケーションが実行リージョンにあるが理想的です。</span><span class="sxs-lookup"><span data-stu-id="c8a71-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="c8a71-177">一部の Azure 資産は特定のリージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="c8a71-178">また、このサービスに適用される条件を理解したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="c8a71-179">[作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-179">Click Create.</span></span>

        ![サービスの作成情報](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="c8a71-181">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="c8a71-182">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新しいサービスの新しい通知を参照してください。](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="c8a71-184">新しいサービス インスタンスを探索する通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-184">Click on the notification to explore your new Service instance.</span></span> 

    ![リソースに移動 ボタンを選択します。](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="c8a71-186">をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="c8a71-187">新しい Computer Vision API サービスのインスタンスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![Computer Vision API の新しいサービス](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="c8a71-189">このチュートリアルでは、内でアプリケーションがサービスのサブスクリプション キーを使用して、これは、サービスへの呼び出しを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="c8a71-190">*クイック スタート* ページの*Computer Vision API*サービスは、最初のステップに移動し、*キーを取得する*、 をクリック**キー** (これを行うキー アイコンによって示される、サービスのナビゲーション メニューにある青いハイパーリンク キーをクリックして)。</span><span class="sxs-lookup"><span data-stu-id="c8a71-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="c8a71-191">これが明らかに、サービス*キー*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="c8a71-192">このプロジェクトの後半で必要になるため、表示されているキーの 1 つのコピーを実行します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="c8a71-193">戻り、*クイック スタート*ページ、およびそこから、エンドポイントを取得します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="c8a71-194">自分、お住まいの地域に応じて異なる可能性がありますに注意してください (これは、後で、コードに、変更を行う必要があります)。</span><span class="sxs-lookup"><span data-stu-id="c8a71-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="c8a71-195">後で使用するには、このエンドポイントのコピーを作成するには。</span><span class="sxs-lookup"><span data-stu-id="c8a71-195">Take a copy of this endpoint for use later:</span></span>

    ![Computer Vision API の新しいサービス](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="c8a71-197">さまざまなエンドポイントをチェックする[ここ](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="c8a71-198">第 2 章 – Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="c8a71-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="c8a71-199">次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。</span><span class="sxs-lookup"><span data-stu-id="c8a71-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="c8a71-200">開いている*Unity*クリック**新規**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-200">Open *Unity* and click **New**.</span></span> 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="c8a71-202">これで、Unity プロジェクト名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="c8a71-203">挿入**MR_ComputerVision**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="c8a71-204">必ず、プロジェクトの種類に設定されて**3D**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="c8a71-205">設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。</span><span class="sxs-lookup"><span data-stu-id="c8a71-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="c8a71-206">をクリックし、**プロジェクトの作成**です。</span><span class="sxs-lookup"><span data-stu-id="c8a71-206">Then, click **Create project**.</span></span>

    ![新しい Unity プロジェクトの詳細を提供します。](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="c8a71-208">既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="c8a71-209">移動して**編集 > 設定**し、新しいウィンドウに移動**外部ツール**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="c8a71-210">変更**External Script Editor**に**Visual Studio 2017**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="c8a71-211">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="c8a71-211">Close the **Preferences** window.</span></span>

    ![スクリプト エディターの基本設定を更新します。](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="c8a71-213">次に移動**ファイル > Build Settings**を選択し、**ユニバーサル Windows プラットフォーム**、をクリックして、**スイッチ プラットフォーム**選択内容を適用するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![[設定] ウィンドウ切り替え UWP プラットフォームをビルドします。](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="c8a71-215">**ファイル > Build Settings**ことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c8a71-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="c8a71-216">**デバイスを対象に**に設定されている**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="c8a71-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="c8a71-217">イマーシブ ヘッドセット、設定**ターゲット デバイス**に*任意のデバイス*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="c8a71-218">**ビルドの種類**に設定されている**D3D**</span><span class="sxs-lookup"><span data-stu-id="c8a71-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="c8a71-219">**SDK**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="c8a71-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="c8a71-220">**Visual Studio バージョン**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="c8a71-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="c8a71-221">**ビルドおよび実行**に設定されている**ローカル マシン**</span><span class="sxs-lookup"><span data-stu-id="c8a71-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="c8a71-222">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="c8a71-223">これには、選択**開くシーンを追加**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="c8a71-224">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-224">A save window will appear.</span></span>
        
            ![開いているシーン ボタンの追加 をクリック](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="c8a71-226">新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新しいスクリプト フォルダーを作成します。](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="c8a71-228">新たに作成した開く**シーン**フォルダー、し、*ファイル名*: テキスト フィールドに「 **MR_ComputerVisionScene**、順にクリックします**保存**.</span><span class="sxs-lookup"><span data-stu-id="c8a71-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![シーンの新しい名前を付けます。](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="c8a71-230">注意してください、内の Unity シーンを保存する必要があります、*資産*フォルダー、Unity プロジェクトに関連付けられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="c8a71-231">Unity プロジェクトの構造の一般的な方法は、シーン フォルダー (およびその他の同様のフォルダー) を作成します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="c8a71-232">設定に残っている*Build Settings*、ここでは既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="c8a71-233">*Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。</span><span class="sxs-lookup"><span data-stu-id="c8a71-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![プレーヤー設定を開きます。](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="c8a71-235">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="c8a71-236">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="c8a71-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="c8a71-237">**ランタイム バージョンをスクリプト**する必要があります**安定した**(.NET 3.5 相当)。</span><span class="sxs-lookup"><span data-stu-id="c8a71-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="c8a71-238">**バックエンドの scripting**べき **.NET**</span><span class="sxs-lookup"><span data-stu-id="c8a71-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="c8a71-239">**API の互換性レベル**べき **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="c8a71-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![その他の設定を更新します。](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="c8a71-241">内で、**発行の設定**] タブの [**機能**、確認してください。</span><span class="sxs-lookup"><span data-stu-id="c8a71-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="c8a71-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="c8a71-242">**InternetClient**</span></span>
        2. <span data-ttu-id="c8a71-243">**Web カメラ**</span><span class="sxs-lookup"><span data-stu-id="c8a71-243">**Webcam**</span></span>

            ![発行の設定を更新しています。](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="c8a71-245">パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X の R の設定を更新します。](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="c8a71-247">戻り*Build Settings* _Unity C#_ プロジェクトが不要になったグレー; これの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="c8a71-248">ビルド設定ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="c8a71-249">シーンとプロジェクトを保存 (**ファイル > シーン保存/ファイル > プロジェクトを保存**)。</span><span class="sxs-lookup"><span data-stu-id="c8a71-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="c8a71-250">第 3 章 – メイン カメラのセットアップ</span><span class="sxs-lookup"><span data-stu-id="c8a71-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8a71-251">スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)、としてプロジェクトにインポート、[カスタム パッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 5 章](#chapter-5--create-the-resultslabel-class)します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="c8a71-252">*階層パネル*を選択、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="c8a71-253">すべてのコンポーネントを参照してください。 選択すると、ができる、 **Main Camera**で、*インスペクター パネル*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="c8a71-254">**Camera オブジェクト**名前を指定する必要があります**Main Camera** (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="c8a71-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="c8a71-255">Main Camera**タグ**に設定する必要があります**MainCamera** (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="c8a71-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="c8a71-256">必ず、**変換位置**に設定されている**0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="c8a71-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="c8a71-257">設定**フラグをクリア**に**単色**(イマーシブ ヘッドセットの無視) します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="c8a71-258">設定、**バック グラウンド**にカメラのコンポーネントの色**黒、アルファ 0 (16 進コード: #00000000)** (イマーシブ ヘッドセットの無視) します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![カメラのコンポーネントを更新します。](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="c8a71-260">次に接続されている単純な"Cursor"オブジェクトを作成する必要が、 **Main Camera**、画像分析を配置するのに役立つ出力は、アプリケーションが実行されています。</span><span class="sxs-lookup"><span data-stu-id="c8a71-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="c8a71-261">このカーソルでは、カメラのフォーカスの中心点を決定します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="c8a71-262">カーソルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="c8a71-263">*階層パネル*を右クリックし、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="c8a71-264">[ **3D オブジェクト**、] をクリックして**球**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![カーソル オブジェクトを選択します。](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="c8a71-266">名前の変更、**球**に**カーソル**(カーソル オブジェクトをダブルクリックまたはオブジェクトを選択した 'F2' キーボード ボタンを押す) の子であるかどうかを確認して、 **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="c8a71-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="c8a71-267">*階層パネル*、左クリックしてで、**カーソル**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="c8a71-268">カーソルが選択されている、調整では、次の変数、*インスペクター パネル*:</span><span class="sxs-lookup"><span data-stu-id="c8a71-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="c8a71-269">設定、*位置を変換*に**0, 0, 5**</span><span class="sxs-lookup"><span data-stu-id="c8a71-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="c8a71-270">設定、*スケール*に**0.02、0.02、0.02**</span><span class="sxs-lookup"><span data-stu-id="c8a71-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![変換の位置とスケールを更新します。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="c8a71-272">第 4 章 – ラベルのシステムのセットアップ</span><span class="sxs-lookup"><span data-stu-id="c8a71-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="c8a71-273">HoloLens のカメラでは、イメージをキャプチャした、そのイメージに送信する、 *Azure Computer Vision API*分析のためのサービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="c8a71-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="c8a71-274">分析の結果と呼ばれる、認識されているオブジェクトのリストが返されます**タグ**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="c8a71-275">(としてワールド空間における 3D テキスト)、写真の撮影場所にこれらのタグを表示するラベルは使用します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="c8a71-276">次の手順では説明を設定する方法、**ラベル**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c8a71-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="c8a71-277">階層のパネル (場所がこの時点で関係ありませんが)、任意の場所を右クリックして**3D オブジェクト**、追加、 **3D テキスト**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="c8a71-278">名前を付けます**LabelText**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-278">Name it **LabelText**.</span></span>

    ![3D テキスト オブジェクトを作成します。](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="c8a71-280">*階層パネル*、左クリックしてで、 **LabelText**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="c8a71-281">**LabelText**で次の変数を選択すると、調整、*インスペクター パネル*:</span><span class="sxs-lookup"><span data-stu-id="c8a71-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="c8a71-282">設定、**位置**に**0,0,0**</span><span class="sxs-lookup"><span data-stu-id="c8a71-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="c8a71-283">設定、**スケール**に**0.01、0.01、0.01**</span><span class="sxs-lookup"><span data-stu-id="c8a71-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="c8a71-284">コンポーネントで**テキスト メッシュ**:</span><span class="sxs-lookup"><span data-stu-id="c8a71-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="c8a71-285">内のすべてのテキストを置き換える**テキスト**、with「...」</span><span class="sxs-lookup"><span data-stu-id="c8a71-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="c8a71-286">設定、**アンカー**に**中央**</span><span class="sxs-lookup"><span data-stu-id="c8a71-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="c8a71-287">設定、**配置**に**センター**</span><span class="sxs-lookup"><span data-stu-id="c8a71-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="c8a71-288">設定、 **タブ サイズ**に**4**</span><span class="sxs-lookup"><span data-stu-id="c8a71-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="c8a71-289">設定、**フォント サイズ**に**50**</span><span class="sxs-lookup"><span data-stu-id="c8a71-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="c8a71-290">設定、**色**に **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="c8a71-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![テキストのコンポーネント](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="c8a71-292">ドラッグ、 **LabelText**から、*階層パネル*に、*アセット フォルダー*内での*プロジェクト パネル*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="c8a71-293">これは、ように、 **LabelText**プレハブ、コードでその it をインスタンス化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![LabelText オブジェクトのプレハブを作成します。](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="c8a71-295">削除する必要があります、 **LabelText**から、*階層パネル*、開くシーンでは表示されません。</span><span class="sxs-lookup"><span data-stu-id="c8a71-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="c8a71-296">プレハブを Assets フォルダーから個々 のインスタンスで呼び出すが、これは現在、シーン内に収まる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c8a71-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="c8a71-297">最終的なオブジェクトの構造、*階層パネル*次の図に示すようになります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![階層のパネルの最終的な構造体。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="c8a71-299">第 5 章 – ResultsLabel クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="c8a71-300">最初のスクリプトを作成する必要がありますが、 *ResultsLabel*クラスは、次の原因となっています。</span><span class="sxs-lookup"><span data-stu-id="c8a71-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="c8a71-301">カメラの位置を基準とした、適切なワールド空間で、ラベルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="c8a71-302">イメージれたからタグを表示します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="c8a71-303">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-303">To create this class:</span></span> 

1.  <span data-ttu-id="c8a71-304">右クリックし、*プロジェクト パネル*、し**作成 > フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="c8a71-305">フォルダーの名前**スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-305">Name the folder **Scripts**.</span></span> 

    ![[スクリプト] フォルダーを作成します。](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="c8a71-307">**スクリプト**フォルダーの作成、アイコンをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="c8a71-308">そのフォルダーを右クリックし、内**作成 >** し**C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="c8a71-309">スクリプトの名前*ResultsLabel*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="c8a71-310">新しいをダブルクリックします。 *ResultsLabel*スクリプト ファイルを開く**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="c8a71-311">クラス内で次のコードを挿入、 *ResultsLabel*クラス。</span><span class="sxs-lookup"><span data-stu-id="c8a71-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  <span data-ttu-id="c8a71-312">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="c8a71-313">戻り、 *Unity エディター* をクリックし、ドラッグ、 *ResultsLabel*クラスから、**スクリプト**フォルダーを**Main Camera** 内のオブジェクト*階層パネル*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="c8a71-314">をクリックして、 **Main Camera**を見て、*インスペクター パネル*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="c8a71-315">カメラにドラッグしたスクリプトからが 2 つのフィールドが表示されます。**カーソル**と**Prefab ラベル**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="c8a71-316">呼ばれるオブジェクトをドラッグして**カーソル**から、*階層パネル*という名前のスロットに**カーソル**、次の図に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="c8a71-317">呼ばれるオブジェクトをドラッグして**LabelText**から、 *Assets フォルダー*で、*プロジェクト パネル*という名前のスロットに**ラベル Prefab**ように、次の図。</span><span class="sxs-lookup"><span data-stu-id="c8a71-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![Unity 内で参照のターゲットを設定します。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="c8a71-319">第 6 章 – ImageCapture クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="c8a71-320">次のクラスを作成することには、 *ImageCapture*クラス。</span><span class="sxs-lookup"><span data-stu-id="c8a71-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="c8a71-321">このクラスは、責任を負います。</span><span class="sxs-lookup"><span data-stu-id="c8a71-321">This class is responsible for:</span></span>

-   <span data-ttu-id="c8a71-322">HoloLens のカメラを使用して、アプリ フォルダーに格納することとイメージをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="c8a71-323">ユーザーからのタップ ジェスチャをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="c8a71-324">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-324">To create this class:</span></span> 

1.  <span data-ttu-id="c8a71-325">移動して、**スクリプト**以前に作成したフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="c8a71-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="c8a71-326">フォルダー内を右クリックして**作成 >C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="c8a71-327">スクリプトを呼び出す*ImageCapture*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="c8a71-328">新しいをダブルクリックします。 *ImageCapture*スクリプト ファイルを開く**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="c8a71-329">ファイルの先頭には、次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="c8a71-330">内で、次の変数を追加し、 *ImageCapture*クラス上、 *Start()* メソッド。</span><span class="sxs-lookup"><span data-stu-id="c8a71-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="c8a71-331">**TapsCount**変数で、ユーザーからキャプチャされたタップ ジェスチャの数を格納します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="c8a71-332">この番号は、キャプチャしたイメージの名前付けで使用されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="c8a71-333">コードを*Awake()* と*Start()* 今すぐメソッドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="c8a71-334">これらが、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="c8a71-335">タップ ジェスチャが発生したときに呼び出されるハンドラーを実装します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
<span data-ttu-id="c8a71-336">*TapHandler()* メソッドは、ユーザーからキャプチャされたタップ数をインクリメントし、現在のカーソル位置を使用して、新しいラベルを配置する場所を決定します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="c8a71-337">このメソッドを呼び出して、 *ExecuteImageCaptureAndAnalysis()* メソッドをこのアプリケーションのコア機能を開始します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="c8a71-338">イメージをキャプチャして保存すると、以下のハンドラーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="c8a71-339">結果が渡されるプロセスが成功した場合、 *VisionManager* (まだ作成としています) を分析します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  <span data-ttu-id="c8a71-340">次に、イメージのキャプチャ プロセスを開始し、イメージを格納するアプリケーションが使用するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> <span data-ttu-id="c8a71-341">この時点で表示されるエラーが表示されます、 *Unity エディターのコンソール パネル*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="c8a71-342">これは、コードを参照しているため、 *VisionManager*クラスは次の章で作成されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="c8a71-343">第 7 章 – Azure と画像分析への呼び出し</span><span class="sxs-lookup"><span data-stu-id="c8a71-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="c8a71-344">最後のスクリプトを作成する必要がありますが、 *VisionManager*クラス。</span><span class="sxs-lookup"><span data-stu-id="c8a71-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="c8a71-345">このクラスは、責任を負います。</span><span class="sxs-lookup"><span data-stu-id="c8a71-345">This class is responsible for:</span></span>

-   <span data-ttu-id="c8a71-346">バイト配列としてキャプチャされた最新のイメージを読み込んでいます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="c8a71-347">送信するバイト配列、 *Azure Computer Vision API*分析のためのサービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="c8a71-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="c8a71-348">JSON 文字列としての応答を受信します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="c8a71-349">応答を逆シリアル化し、結果として得られるタグを渡す、 *ResultsLabel*クラス。</span><span class="sxs-lookup"><span data-stu-id="c8a71-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="c8a71-350">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-350">To create this class:</span></span>

1.  <span data-ttu-id="c8a71-351">ダブルクリック、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="c8a71-352">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="c8a71-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="c8a71-353">スクリプトの名前*VisionManager*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="c8a71-354">Visual Studio で開くことに新しいスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="c8a71-355">上部にある、次と同じである名前空間の更新、 *VisionManager*クラス。</span><span class="sxs-lookup"><span data-stu-id="c8a71-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="c8a71-356">スクリプトの上部にある*内*、 *VisionManager*クラス (上、 *Start()* メソッド)、2 つ作成する必要があります*クラス*ですAzure からの逆シリアル化された JSON 応答を表します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="c8a71-357">*TagData*と*AnalysedObject*クラスが必要です、 *[System.Serializable]* Unity で逆シリアル化できる宣言の前に追加された属性ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="c8a71-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="c8a71-358">VisionManager クラスでは、次の変数を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-358">In the VisionManager class, you should add the following variables:</span></span>

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > <span data-ttu-id="c8a71-359">挿入することを確認、**認証キー**に、 **authorizationKey**変数。</span><span class="sxs-lookup"><span data-stu-id="c8a71-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="c8a71-360">メモは、**認証キー**のこのコースでは、先頭に[第 1 章](#chapter-1--the-azure-portal)します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="c8a71-361">**VisionAnalysisEndpoint**変数は、この例で指定されている異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="c8a71-362">**西部、米国**厳密に言うと、米国西部リージョンに作成されたサービス インスタンスにします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="c8a71-363">これを更新、[エンドポイント URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)。 ここではその例をいくつかのようになります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="c8a71-364">西ヨーロッパ: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="c8a71-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="c8a71-365">東南アジア。 `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="c8a71-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="c8a71-366">オーストラリア東部: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="c8a71-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="c8a71-367">今すぐ、Awake のコードは、追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="c8a71-368">によってキャプチャされたイメージの分析の結果を取得する (ストリームの静的メソッドで下にある)、コルーチンを次に、追加、 *ImageCapture*クラス。</span><span class="sxs-lookup"><span data-stu-id="c8a71-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  <span data-ttu-id="c8a71-369">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="c8a71-370">戻る Unity エディターで、をクリックし、ドラッグ、 *VisionManager*と*ImageCapture*クラスを**スクリプト**フォルダーを**Main Camera**オブジェクト、*階層パネル*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="c8a71-371">第 8 章: ビルドする前に</span><span class="sxs-lookup"><span data-stu-id="c8a71-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="c8a71-372">アプリケーションの徹底的なテストを実行するには、必要がありますをサイドロードすること、HoloLens にします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="c8a71-373">実行する前にいることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="c8a71-374">説明されているすべての設定[第 2 章](#chapter-2--set-up-the-unity-project)が正しく設定されています。</span><span class="sxs-lookup"><span data-stu-id="c8a71-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="c8a71-375">関連付けられているすべてのスクリプト、 **Main Camera**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c8a71-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="c8a71-376">内のすべてのフィールド、*カメラ インスペクター [メイン] パネル*が適切に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="c8a71-377">挿入することを確認、**認証キー**に、 **authorizationKey**変数。</span><span class="sxs-lookup"><span data-stu-id="c8a71-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="c8a71-378">エンドポイントもチェックすることを確認、 *VisionManager*スクリプト、およびに合わせて配置 *、* リージョン (このドキュメントでは*西-ご*既定)。</span><span class="sxs-lookup"><span data-stu-id="c8a71-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="c8a71-379">9 – 章ビルド UWP ソリューションおよびサイドロード アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c8a71-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="c8a71-380">このプロジェクトの Unity のセクションの必要なすべてが今すぐ完了したら、ので、Unity から構築するための時間。</span><span class="sxs-lookup"><span data-stu-id="c8a71-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="c8a71-381">移動します*ビルド設定* - **ファイル > の設定を作成しています.**</span><span class="sxs-lookup"><span data-stu-id="c8a71-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="c8a71-382">*Build Settings*ウィンドウで、をクリックして**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-382">From the *Build Settings* window, click **Build**.</span></span>

    ![Unity からのアプリの構築](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="c8a71-384">まだ行っていない場合、ティック**UnityC#プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="c8a71-385">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-385">Click **Build**.</span></span> <span data-ttu-id="c8a71-386">Unity を起動、*ファイル エクスプ ローラー*ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="c8a71-387">ここで、そのフォルダーを作成し、名前*アプリ*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="c8a71-388">使用し、*アプリ*フォルダーを選択すると、キーを押して**フォルダーの選択**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="c8a71-389">Unity にプロジェクトをビルドを開始、*アプリ*フォルダー。</span><span class="sxs-lookup"><span data-stu-id="c8a71-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="c8a71-390">1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、*ファイル エクスプ ローラー*ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。</span><span class="sxs-lookup"><span data-stu-id="c8a71-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="c8a71-391">HoloLens に章 – 10 を展開します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="c8a71-392">HoloLens の展開。</span><span class="sxs-lookup"><span data-stu-id="c8a71-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="c8a71-393">必要になります、HoloLens の IP アドレス (リモート) を展開し、HoloLens をことを確認するには**開発者モード**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="c8a71-394">これには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-394">To do this:</span></span>

    1. <span data-ttu-id="c8a71-395">ソックスを着けずに、HoloLens 中を開く、**設定**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="c8a71-396">移動して**ネットワークとインターネット > Wi-fi > 詳細オプション**</span><span class="sxs-lookup"><span data-stu-id="c8a71-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="c8a71-397">注、 **IPv4**アドレス。</span><span class="sxs-lookup"><span data-stu-id="c8a71-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="c8a71-398">次に移動します**設定**、し**更新とセキュリティ > 開発者向け**</span><span class="sxs-lookup"><span data-stu-id="c8a71-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="c8a71-399">開発者モードを設定します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="c8a71-400">新しい Unity ビルドに移動します (、*アプリ*フォルダー) とソリューション ファイルを開くと*Visual Studio*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="c8a71-401">ソリューション構成の選択で**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="c8a71-402">ソリューション プラットフォーム で選択**x86**、**リモート マシン**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="c8a71-404">移動して、**ビルド メニューの** をクリック**ソリューションの配置**サイドロード、HoloLens をアプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="c8a71-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="c8a71-405">アプリが、起動する準備ができて、HoloLens にインストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8a71-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="c8a71-406">イマーシブ ヘッドセットを展開するには、設定、**ソリューション プラットフォーム**に*ローカル マシン*、設定と、**構成**に*デバッグ*で*x86*として、**プラットフォーム**します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="c8a71-407">ローカルにデプロイし、machine を使用して、**ビルド メニューの**選択*ソリューションの配置*します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="c8a71-408">完成した Computer Vision API アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c8a71-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="c8a71-409">これで、現実世界のオブジェクトを認識し、内容は、発生の信頼度を表示する Azure の Computer Vision API を利用している mixed reality アプリを構築します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![ラボの結果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="c8a71-411">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="c8a71-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="c8a71-412">手順 1</span><span class="sxs-lookup"><span data-stu-id="c8a71-412">Exercise 1</span></span>

<span data-ttu-id="c8a71-413">使用したのと同様、*タグ*パラメーター (内からわかるように、*エンドポイント*内で使用される、 *VisionManager*)、その他の情報を検出するためにアプリを拡張; を見てその他のパラメーターへのアクセスがある[ここ](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="c8a71-414">手順 2</span><span class="sxs-lookup"><span data-stu-id="c8a71-414">Exercise 2</span></span>

<span data-ttu-id="c8a71-415">おそらく、番号を非表示より会話で読みやすい方法で返される Azure のデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="c8a71-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="c8a71-416">いなくても、ボットは、ユーザーに話す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c8a71-416">As though a bot might be speaking to the user.</span></span>
