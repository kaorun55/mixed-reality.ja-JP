---
title: MR と Azure 304 - 顔認識
description: このコースでは、複合現実のアプリケーション内で Azure の顔認識機能を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure では、顔認識、hololens、没入型、vr の実際に、アカデミー、unity、チュートリアル、api を混在
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603810"
---
>[!NOTE]
><span data-ttu-id="cac27-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cac27-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="cac27-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="cac27-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="cac27-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="cac27-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="cac27-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="cac27-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="cac27-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="cac27-110">MR と Azure 304:顔認識</span><span class="sxs-lookup"><span data-stu-id="cac27-110">MR and Azure 304: Face recognition</span></span>

![このコースを完了するの結果](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="cac27-112">このコースでは Microsoft Face API を使用した Azure Cognitive Services を使用して複合現実のアプリケーションに顔認識機能を追加する方法についてはします。</span><span class="sxs-lookup"><span data-stu-id="cac27-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="cac27-113">*Azure の Face API*は、開発者はすべてクラウドでの顔アルゴリズムの最も高度な Microsoft のサービスです。</span><span class="sxs-lookup"><span data-stu-id="cac27-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="cac27-114">*Face API* 2 つの主な機能: 属性を含む、検出して認識に直面します。</span><span class="sxs-lookup"><span data-stu-id="cac27-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="cac27-115">これにより、開発者、顔のグループのセットを設定するだけですし、次に、クエリ イメージ サービスへの送信後で、顔が属しているユーザーを決定します。</span><span class="sxs-lookup"><span data-stu-id="cac27-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="cac27-116">詳細については、次を参照してください。、 [Azure 顔認識ページ](https://azure.microsoft.com/services/cognitive-services/face/)します。</span><span class="sxs-lookup"><span data-stu-id="cac27-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="cac27-117">このコースを完了すると、複合現実は、次のことが、HoloLens のアプリケーションが用意されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="cac27-118">使用して、**タップ ジェスチャ**オンボード HoloLens カメラを使用してイメージのキャプチャを開始します。</span><span class="sxs-lookup"><span data-stu-id="cac27-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="cac27-119">キャプチャしたイメージの送信、 *Azure の Face API*サービス。</span><span class="sxs-lookup"><span data-stu-id="cac27-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="cac27-120">結果を受け取る、 *Face API*アルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="cac27-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="cac27-121">単純なユーザー インターフェイスを使用すると、一致したユーザーの名前を表示できます。</span><span class="sxs-lookup"><span data-stu-id="cac27-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="cac27-122">Face API のサービスから、Unity に基づく複合現実のアプリケーションに結果を取得する方法が説明されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="cac27-123">アプリケーションでは、責任ですが、設計と、結果を統合する方法について。</span><span class="sxs-lookup"><span data-stu-id="cac27-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="cac27-124">このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。</span><span class="sxs-lookup"><span data-stu-id="cac27-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="cac27-125">複合現実アプリを強化するためには、このコース得た知識を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="cac27-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="cac27-126">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="cac27-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="cac27-127">コース</span><span class="sxs-lookup"><span data-stu-id="cac27-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="cac27-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="cac27-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="cac27-129"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="cac27-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="cac27-130">MR と Azure 304:顔認識</span><span class="sxs-lookup"><span data-stu-id="cac27-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="cac27-131">✔️</span><span class="sxs-lookup"><span data-stu-id="cac27-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="cac27-132">✔️</span><span class="sxs-lookup"><span data-stu-id="cac27-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="cac27-133">このコースは、HoloLens で主にフォーカスします、Windows Mixed Reality 没入型 (VR) ヘッドセットには、このコースで学習する内容を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="cac27-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="cac27-134">(VR) のイマーシブ ヘッドセットはアクセス可能な cameras があるないため、外部のカメラを PC に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac27-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="cac27-135">コースを実行するとき、没入型の (VR) ヘッドセットをサポートするために使用する必要があります変更でノートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cac27-136">前提条件</span><span class="sxs-lookup"><span data-stu-id="cac27-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="cac27-137">このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。</span><span class="sxs-lookup"><span data-stu-id="cac27-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="cac27-138">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 5 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cac27-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="cac27-139">内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)ことについては、このコースでとまったく同じで見つかりますの下に記載されているものよりも新しいソフトウェアでどのようなことは仮定されませんが、記事.</span><span class="sxs-lookup"><span data-stu-id="cac27-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="cac27-140">次のハードウェアとソフトウェアこのコースをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cac27-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="cac27-141">開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発</span><span class="sxs-lookup"><span data-stu-id="cac27-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="cac27-142">Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="cac27-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="cac27-143">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="cac27-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="cac27-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="cac27-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="cac27-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="cac27-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="cac27-146">A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効</span><span class="sxs-lookup"><span data-stu-id="cac27-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="cac27-147">(イマーシブ ヘッドセット開発) は、PC に接続されているカメラ</span><span class="sxs-lookup"><span data-stu-id="cac27-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="cac27-148">Azure のセットアップおよび Face API 取得するためのインターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="cac27-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="cac27-149">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="cac27-149">Before you start</span></span>

1.  <span data-ttu-id="cac27-150">このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。</span><span class="sxs-lookup"><span data-stu-id="cac27-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="cac27-151">設定して、HoloLens をテストします。</span><span class="sxs-lookup"><span data-stu-id="cac27-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="cac27-152">場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。</span><span class="sxs-lookup"><span data-stu-id="cac27-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="cac27-153">(場合によって役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときに、調整とセンサーのチューニングを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cac27-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="cac27-154">調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。</span><span class="sxs-lookup"><span data-stu-id="cac27-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="cac27-155">センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。</span><span class="sxs-lookup"><span data-stu-id="cac27-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="cac27-156">第 1 章 - Azure Portal</span><span class="sxs-lookup"><span data-stu-id="cac27-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="cac27-157">使用する、 *Face API*サービス、Azure でアプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac27-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="cac27-158">最初に、ログイン、 [Azure Portal](https://portal.azure.com)します。</span><span class="sxs-lookup"><span data-stu-id="cac27-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="cac27-159">Azure アカウントがいない場合は、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac27-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="cac27-160">クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="cac27-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="cac27-161">ログインした後は、をクリックして**新規**左上隅にある検索して*Face API*、キーを押して**Enter**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![検索 api に直面](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="cac27-163">単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。</span><span class="sxs-lookup"><span data-stu-id="cac27-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="cac27-164">新しいページがの説明を入力、 *Face API*サービス。</span><span class="sxs-lookup"><span data-stu-id="cac27-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="cac27-165">このプロンプトの左下にある at、**作成**ボタンは、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="cac27-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![直面 api 情報](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="cac27-167">クリックすると**作成**:</span><span class="sxs-lookup"><span data-stu-id="cac27-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="cac27-168">このサービス インスタンスのご希望の名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="cac27-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="cac27-169">サブスクリプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="cac27-169">Select a subscription.</span></span>

    3. <span data-ttu-id="cac27-170">作成時刻の場合、これは、最初に、適切な価格レベルを選択、 *Face API サービス*、(F0 という名前)、free レベルを使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="cac27-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="cac27-171">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="cac27-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="cac27-172">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="cac27-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="cac27-173">勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。</span><span class="sxs-lookup"><span data-stu-id="cac27-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="cac27-174">詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="cac27-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="cac27-175">UWP アプリ、 **Person メーカー**、場所 '米国西部' の使用が必要です、後で使用します。</span><span class="sxs-lookup"><span data-stu-id="cac27-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="cac27-176">また、このサービスに適用される条件を理解したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac27-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="cac27-177">選択 **作成\*。** </span><span class="sxs-lookup"><span data-stu-id="cac27-177">Select **Create\*.**</span></span>

        ![作成直面 api サービス](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="cac27-179">クリックすると **作成**\* サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cac27-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="cac27-180">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![サービスの作成の通知](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="cac27-182">新しいサービス インスタンスを探索する通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cac27-182">Click on the notifications to explore your new Service instance.</span></span>

    ![リソース通知に移動します。](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="cac27-184">準備ができたら、クリックして**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cac27-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![アクセス直面 api キー](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="cac27-186">内でのこのチュートリアルでは、アプリケーションは、サービスのサブスクリプション 'key' を使用して、これは、サービスへの呼び出しを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac27-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="cac27-187">*クイック スタート* ページの*Face API*サービス、最初のポイントに番号は 1、*キーを取得します。*</span><span class="sxs-lookup"><span data-stu-id="cac27-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="cac27-188">*サービス*ページが青色のいずれかを選択します**キー**ハイパーリンク (クイック スタート ページの場合)、または**キー**サービスのナビゲーション メニューのリンク (によって示される、左側に、'キー ' アイコン)、キーを表示します。</span><span class="sxs-lookup"><span data-stu-id="cac27-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="cac27-189">キーのいずれかの注意を受け取り、後で必要になると、保護します。</span><span class="sxs-lookup"><span data-stu-id="cac27-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="cac27-190">第 2 章 – 'Person メーカー' UWP アプリケーションの使用</span><span class="sxs-lookup"><span data-stu-id="cac27-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="cac27-191">呼ばれる事前構築済みの UWP アプリケーションをダウンロードすることを確認[Person メーカー](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)します。</span><span class="sxs-lookup"><span data-stu-id="cac27-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="cac27-192">このアプリは、このコースでは、単なるツール、以降のプロジェクトが依存している、Azure のエントリを作成するための最終的な製品ではありません。</span><span class="sxs-lookup"><span data-stu-id="cac27-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="cac27-193">**Person メーカー** 、人のユーザーとグループのユーザーに関連付けられている Azure のエントリを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="cac27-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="cac27-194">アプリケーションは、後で使用できる、FaceAPI で追加した人物の顔を認識するための形式で、必要なすべての情報を配置します。</span><span class="sxs-lookup"><span data-stu-id="cac27-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="cac27-195">[重要]**Person メーカー**基本的な調整を使用して、サービス呼び出しの 1 分あたりの数を超えていないことを確保しやすく、**無料のサブスクリプション レベル**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="cac27-196">上部にある緑のテキストは赤に変更され、調整が行われているときに、'ACTIVE' と更新大文字と小文字の場合は、(を待機する 'IN アクティブ' としてもう一度使用すると、更新、顔のサービスへのアクセスを次に続行できます)、アプリケーションの待機だけです。</span><span class="sxs-lookup"><span data-stu-id="cac27-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="cac27-197">このアプリケーションを使用して、 *Microsoft.ProjectOxford.Face*ライブラリは、完全にすることができる Face API を使用します。</span><span class="sxs-lookup"><span data-stu-id="cac27-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="cac27-198">このライブラリは NuGet パッケージとして無料で使用できます。</span><span class="sxs-lookup"><span data-stu-id="cac27-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="cac27-199">詳細についてと似ていますが、Api [API リファレンスの記事を参照してください。 確認](https://docs.microsoft.com/azure/cognitive-services/face/apireference)します。</span><span class="sxs-lookup"><span data-stu-id="cac27-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="cac27-200">これらは、必要な手順だけ、これらの作業を行う方法については、ドキュメントの後半。</span><span class="sxs-lookup"><span data-stu-id="cac27-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="cac27-201">**Person メーカー**アプリでは、することはできます。</span><span class="sxs-lookup"><span data-stu-id="cac27-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="cac27-202">作成、*人物グループ*を関連付ける複数のユーザーのグループが構成します。</span><span class="sxs-lookup"><span data-stu-id="cac27-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="cac27-203">Azure アカウントでは、複数のユーザー グループをホストできます。</span><span class="sxs-lookup"><span data-stu-id="cac27-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="cac27-204">作成、 *Person*、人物グループのメンバーであります。</span><span class="sxs-lookup"><span data-stu-id="cac27-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="cac27-205">各ユーザーがさまざまな*Face*イメージが関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="cac27-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="cac27-206">割り当てる*イメージに直面*を*人*を認識する、Azure の Face API サービスのことを許可する、*人*、対応する*face*します。</span><span class="sxs-lookup"><span data-stu-id="cac27-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="cac27-207">*トレーニング*、 *API サービスを Azure に直面*します。</span><span class="sxs-lookup"><span data-stu-id="cac27-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="cac27-208">ある人を認識するには、このアプリをトレーニングする場合、10 の拡大写真、ユーザー グループに追加したいが各ユーザーの必要があります。 ため注意してください。</span><span class="sxs-lookup"><span data-stu-id="cac27-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="cac27-209">Windows 10 の Cam アプリは、これらの考慮をするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="cac27-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="cac27-210">それぞれの写真が明確であることを確認する必要があります (ぼかしやを隠ぺいすると、サブジェクトから離れすぎてを避ける)、jpg または png ファイル形式でないより大きいイメージ ファイルのサイズ、写真がある**4 MB**、いいえより小さい**1 KB**.</span><span class="sxs-lookup"><span data-stu-id="cac27-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="cac27-211">このチュートリアルに従っている場合は、上、HoloLens を保存する場合は、自分でを考察することはできません、トレーニングの独自の文字盤を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="cac27-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="cac27-212">仕事仲間や仲間の学生の顔を使用します。</span><span class="sxs-lookup"><span data-stu-id="cac27-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="cac27-213">実行している**Person メーカー**:</span><span class="sxs-lookup"><span data-stu-id="cac27-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="cac27-214">開く、 **PersonMaker**フォルダー をクリックして、 *PersonMaker ソリューション*ファイルを開く*Visual Studio*します。</span><span class="sxs-lookup"><span data-stu-id="cac27-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="cac27-215">1 回、 *PersonMaker ソリューション*を開いて、ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="cac27-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="cac27-216">*ソリューション構成*に設定されている**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="cac27-217">*ソリューション プラットフォーム*に設定されている**x86**</span><span class="sxs-lookup"><span data-stu-id="cac27-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="cac27-218">*ターゲット プラットフォーム*は**ローカル マシン**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="cac27-219">する必要があります*NuGet パッケージの復元*(を右クリックし、*ソリューション*選択**NuGet パッケージの復元**)。</span><span class="sxs-lookup"><span data-stu-id="cac27-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="cac27-220">クリックして*ローカル マシン*され、アプリケーションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="cac27-221">小さい画面に、注意してください、すべてのコンテンツは可能性がありますそれを表示するさらに下にスクロールできますが、表示されません。</span><span class="sxs-lookup"><span data-stu-id="cac27-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![人の作成者のユーザー インターフェイス](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="cac27-223">挿入、 **Azure 認証キー**、する必要がありますが、これから、 *Face API*内での Azure サービスです。</span><span class="sxs-lookup"><span data-stu-id="cac27-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="cac27-224">挿入します。</span><span class="sxs-lookup"><span data-stu-id="cac27-224">Insert:</span></span>

    1. <span data-ttu-id="cac27-225">*ID*に割り当てる、*人物グループ*します。</span><span class="sxs-lookup"><span data-stu-id="cac27-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="cac27-226">ID は、小文字、スペースなしである必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac27-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="cac27-227">この id をメモしておいて後で、Unity プロジェクトで必要になります。</span><span class="sxs-lookup"><span data-stu-id="cac27-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="cac27-228">*名前*に割り当てる、*人物グループ*(スペースを持つことができます)。</span><span class="sxs-lookup"><span data-stu-id="cac27-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="cac27-229">キーを押して**人物グループの作成**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cac27-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="cac27-230">確認メッセージは、ボタンの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="cac27-231">' アクセス拒否エラーが発生した場合は、Azure サービスに設定する場所を確認します。</span><span class="sxs-lookup"><span data-stu-id="cac27-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="cac27-232">前述のように、このアプリは米国西部"に設計されています。</span><span class="sxs-lookup"><span data-stu-id="cac27-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cac27-233">クリックすることできますも表示されます、**知られたグループをフェッチ**ボタン: 既にを作成したかどうか、人、新しく作成するのではなく、それを使用するには、グループ、および希望になります。</span><span class="sxs-lookup"><span data-stu-id="cac27-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="cac27-234">クリックする場合は注意*ユーザー グループを作成する*既知のグループと、グループをフェッチこれはもします。</span><span class="sxs-lookup"><span data-stu-id="cac27-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="cac27-235">挿入、*名前*の*Person*を作成します。</span><span class="sxs-lookup"><span data-stu-id="cac27-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="cac27-236">をクリックして、**ユーザーの作成**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cac27-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="cac27-237">確認メッセージは、ボタンの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="cac27-238">以前に作成した担当者を削除する場合は、キーを押してし、テキスト ボックスに名前を記述する**人物の削除**</span><span class="sxs-lookup"><span data-stu-id="cac27-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="cac27-239">10 人のグループに追加したいユーザーの写真の場所を確認してください。</span><span class="sxs-lookup"><span data-stu-id="cac27-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="cac27-240">キーを押して**の作成とフォルダーを開く**をユーザーに関連付けられているフォルダーに Windows エクスプ ローラーを開きます。</span><span class="sxs-lookup"><span data-stu-id="cac27-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="cac27-241">フォルダー内の 10 のイメージを追加します。</span><span class="sxs-lookup"><span data-stu-id="cac27-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="cac27-242">これらで必要があります*JPG*または*PNG*ファイル形式。</span><span class="sxs-lookup"><span data-stu-id="cac27-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="cac27-243">をクリックして**Azure に送信**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="cac27-244">カウンターでは、メッセージを後に完了すると、送信の状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="cac27-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="cac27-245">をクリック、カウンターが完了し、確認メッセージが表示されている**トレーニング**サービスをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="cac27-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="cac27-246">プロセスが完了すると、Unity に移動する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="cac27-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="cac27-247">第 3 章 - Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="cac27-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="cac27-248">次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。</span><span class="sxs-lookup"><span data-stu-id="cac27-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="cac27-249">開いている*Unity*クリック**新規**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-249">Open *Unity* and click **New**.</span></span> 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="cac27-251">これで、Unity プロジェクト名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac27-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="cac27-252">挿入**MR_FaceRecognition**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="cac27-253">必ず、プロジェクトの種類に設定されて**3D**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="cac27-254">設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。</span><span class="sxs-lookup"><span data-stu-id="cac27-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="cac27-255">をクリックし、**プロジェクトの作成**です。</span><span class="sxs-lookup"><span data-stu-id="cac27-255">Then, click **Create project**.</span></span>

    ![新しい Unity プロジェクトの詳細を提供します。](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="cac27-257">既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="cac27-258">移動して**編集 > 設定**し、新しいウィンドウに移動**外部ツール**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="cac27-259">変更**External Script Editor**に**Visual Studio 2017**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="cac27-260">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="cac27-260">Close the **Preferences** window.</span></span>

    ![スクリプト エディターの基本設定を更新します。](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="cac27-262">次に移動**ファイル > Build Settings**にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして、**プラットフォームの切り替え**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cac27-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![[設定] ウィンドウ切り替え UWP プラットフォームをビルドします。](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="cac27-264">移動して**ファイル > Build Settings**ことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="cac27-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="cac27-265">**デバイスを対象に**に設定されている**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="cac27-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="cac27-266">イマーシブ ヘッドセット、設定**ターゲット デバイス**に*任意のデバイス*します。</span><span class="sxs-lookup"><span data-stu-id="cac27-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="cac27-267">**ビルドの種類**に設定されている**D3D**</span><span class="sxs-lookup"><span data-stu-id="cac27-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="cac27-268">**SDK**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="cac27-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="cac27-269">**Visual Studio バージョン**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="cac27-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="cac27-270">**ビルドおよび実行**に設定されている**ローカル マシン**</span><span class="sxs-lookup"><span data-stu-id="cac27-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="cac27-271">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="cac27-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="cac27-272">これには、選択**開くシーンを追加**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="cac27-273">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-273">A save window will appear.</span></span>

            ![開いているシーン ボタンの追加 をクリック](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="cac27-275">選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新しいスクリプト フォルダーを作成します。](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="cac27-277">新たに作成した開く**シーン**フォルダー、し、**ファイル名**: テキスト フィールドに「 **FaceRecScene**、キーを押します**保存します**。</span><span class="sxs-lookup"><span data-stu-id="cac27-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![シーンの新しい名前を付けます。](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="cac27-279">設定に残っている*Build Settings*、ここでは既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac27-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="cac27-280">*Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。</span><span class="sxs-lookup"><span data-stu-id="cac27-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![プレーヤー設定を開きます。](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="cac27-282">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac27-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="cac27-283">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="cac27-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="cac27-284">**Scripting** **ランタイム バージョン**べき**試験的**(.NET 4.6 Equivalent)。</span><span class="sxs-lookup"><span data-stu-id="cac27-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="cac27-285">これを変更すると、エディターを再起動する必要があるされます。</span><span class="sxs-lookup"><span data-stu-id="cac27-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="cac27-286">**バックエンドの scripting**べき **.NET**</span><span class="sxs-lookup"><span data-stu-id="cac27-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="cac27-287">**API の互換性レベル**べき **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="cac27-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![その他の設定を更新します。](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="cac27-289">内で、**発行の設定**] タブの [**機能**、確認してください。</span><span class="sxs-lookup"><span data-stu-id="cac27-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="cac27-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="cac27-290">**InternetClient**</span></span>
        - <span data-ttu-id="cac27-291">**Web カメラ**</span><span class="sxs-lookup"><span data-stu-id="cac27-291">**Webcam**</span></span>

            ![発行の設定を更新しています。](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="cac27-293">パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X の R の設定を更新します。](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="cac27-295">戻り*Build Settings*、 **UnityC#プロジェクト**が不要になったグレー; これの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="cac27-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="cac27-296">ビルド設定ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="cac27-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="cac27-297">シーンとプロジェクトを保存 (**ファイル > シーン保存/ファイル > プロジェクトを保存**)。</span><span class="sxs-lookup"><span data-stu-id="cac27-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="cac27-298">第 4 章 - メイン カメラのセットアップ</span><span class="sxs-lookup"><span data-stu-id="cac27-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cac27-299">スキップする場合、 *Unity を設定する*のこのコンポーネントである、コース、コードにまっすぐコンティニュし、自由に[ダウンロードこの .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)、としてプロジェクトにインポート、[カスタムパッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)します。</span><span class="sxs-lookup"><span data-stu-id="cac27-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="cac27-300">このパッケージにも、インポートが含まれることに注意してください、 *Newtonsoft DLL*の中で説明、[第 5 章](#chapter-5--import-the-newtonsoft.json-library)します。</span><span class="sxs-lookup"><span data-stu-id="cac27-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoft.json-library).</span></span> <span data-ttu-id="cac27-301">このインポートから継続することができます[第 6 章](#chapter-6-create-the-faceanalysis-class)します。</span><span class="sxs-lookup"><span data-stu-id="cac27-301">With this imported, you can continue from [Chapter 6](#chapter-6-create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="cac27-302">*階層*パネルで、選択、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="cac27-303">すべてのコンポーネントを参照してください。 選択すると、ができる、 **Main Camera**で、*インスペクター パネル*します。</span><span class="sxs-lookup"><span data-stu-id="cac27-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="cac27-304">**Camera オブジェクト**名前を指定する必要があります**Main Camera** (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="cac27-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="cac27-305">Main Camera**タグ**に設定する必要があります**MainCamera** (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="cac27-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="cac27-306">必ず、**変換位置**に設定されている**0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="cac27-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="cac27-307">設定**フラグをクリア**に**純色**</span><span class="sxs-lookup"><span data-stu-id="cac27-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="cac27-308">設定、**バック グラウンド**にカメラのコンポーネントの色**黒、アルファ 0 (コードを 16 進数: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="cac27-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![カメラのコンポーネントを設定します。](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="cac27-310">第 5 章 – Newtonsoft.Json ライブラリのインポート</span><span class="sxs-lookup"><span data-stu-id="cac27-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cac27-311">'.Unitypackage' をインポートした場合、[最後の章](#chapter-4--main-camera-setup)、この章をスキップすることができます。</span><span class="sxs-lookup"><span data-stu-id="cac27-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4--main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="cac27-312">逆シリアル化し、Bot Service の送受信にオブジェクトをシリアル化するのに役立つダウンロードする必要があります、 *Newtonsoft.Json*ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="cac27-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="cac27-313">既にこの適切な Unity フォルダー構造を持つ構成されています。 互換性のあるバージョンを見つかります[Unity パッケージ ファイル](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)します。</span><span class="sxs-lookup"><span data-stu-id="cac27-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="cac27-314">ライブラリをインポートするには。</span><span class="sxs-lookup"><span data-stu-id="cac27-314">To import the library:</span></span>

1.  <span data-ttu-id="cac27-315">Unity パッケージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="cac27-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="cac27-316">をクリックして**資産**、**パッケージ インポート**、**カスタム パッケージ**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![Newtonsoft.Json ライブラリをインポートします。](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="cac27-318">Unity パッケージをダウンロードして、し、[開く] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cac27-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="cac27-319">確認、パッケージのすべてのコンポーネントがオン、を**インポート**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![Newtonsoft.Json ライブラリをインポートします。](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="cac27-321">第 6 章 - FaceAnalysis クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="cac27-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="cac27-322">FaceAnalysis クラスでは、Azure 顔の認識サービスとの通信に必要なメソッドをホストします。</span><span class="sxs-lookup"><span data-stu-id="cac27-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="cac27-323">キャプチャ イメージを送信すると、サービス、分析、および内で、顔の識別され既知のユーザーに属しているいずれかを判断します。</span><span class="sxs-lookup"><span data-stu-id="cac27-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="cac27-324">既知のユーザーが見つかった場合、このクラスは、シーン内の UI テキストとして、名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="cac27-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="cac27-325">作成する、 *FaceAnalysis*クラス。</span><span class="sxs-lookup"><span data-stu-id="cac27-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="cac27-326">右クリックし、 *Assets フォルダー*プロジェクト パネルにあるをクリックして**作成** > **フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="cac27-327">フォルダーを呼び出す**スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-327">Call the folder **Scripts**.</span></span> 

    ![FaceAnalysis クラスを作成します。](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="cac27-329">先ほど作成した、開くフォルダーをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cac27-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="cac27-330">フォルダー内を右クリックし、をクリックして**作成** >   **C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="cac27-331">スクリプトを呼び出す*FaceAnalysis*します。</span><span class="sxs-lookup"><span data-stu-id="cac27-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="cac27-332">新しいをダブルクリックします。 *FaceAnalysis*スクリプトを Visual Studio 2017 で開くことです。</span><span class="sxs-lookup"><span data-stu-id="cac27-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="cac27-333">上記の次の名前空間を入力、 *FaceAnalysis*クラス。</span><span class="sxs-lookup"><span data-stu-id="cac27-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="cac27-334">すべての deserialising に使用されるオブジェクトを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac27-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="cac27-335">これらのオブジェクトを追加する必要がある**外**の*FaceAnalysis* (下の中かっこ) の下のスクリプト。</span><span class="sxs-lookup"><span data-stu-id="cac27-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. <span data-ttu-id="cac27-336">*Start()* と*Update()* メソッドは使用されません、ようになりましたので削除します。</span><span class="sxs-lookup"><span data-stu-id="cac27-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="cac27-337">内で、 *FaceAnalysis*クラスで、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="cac27-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > <span data-ttu-id="cac27-338">置換、**キー**と**personGroupId**サービス キーと以前に作成したグループの Id。</span><span class="sxs-lookup"><span data-stu-id="cac27-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="cac27-339">追加、 *Awake()* メソッドで、クラスを初期化するには、追加、 *ImageCapture* Main Camera クラス ラベルの作成メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cac27-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. <span data-ttu-id="cac27-340">追加、 *CreateLabel()* メソッドで、作成、*ラベル*分析結果を表示するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="cac27-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. <span data-ttu-id="cac27-341">追加、 *DetectFacesFromImage()* と*GetImageAsByteArray()* メソッド。</span><span class="sxs-lookup"><span data-stu-id="cac27-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="cac27-342">前者は後者は、キャプチャしたイメージをバイト配列に変換するために必要な送信済みのイメージのすべての可能な顔を検出するために、顔認識サービスを要求します。</span><span class="sxs-lookup"><span data-stu-id="cac27-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. <span data-ttu-id="cac27-343">追加、 *IdentifyFaces()* メソッドで、要求、*顔認識サービス*以前に送信されたイメージで検出された、既知の顔を識別するためにします。</span><span class="sxs-lookup"><span data-stu-id="cac27-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="cac27-344">要求には、特定の人が名ではなく id が返されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-344">The request will return an id of the identified person but not the name:</span></span>

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. <span data-ttu-id="cac27-345">追加、 *GetPerson()* メソッド。</span><span class="sxs-lookup"><span data-stu-id="cac27-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="cac27-346">ユーザー id、このメソッドからの要求を提供することで、*顔認識サービス*識別されたユーザーの名前を返します。</span><span class="sxs-lookup"><span data-stu-id="cac27-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  <span data-ttu-id="cac27-347">**保存**Unity エディターに戻る前に変更します。</span><span class="sxs-lookup"><span data-stu-id="cac27-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="cac27-348">Unity エディターで、[プロジェクト] パネルで、Scripts フォルダーから Main Camera オブジェクトに FaceAnalysis スクリプトをドラッグする、*階層パネル*します。</span><span class="sxs-lookup"><span data-stu-id="cac27-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="cac27-349">新しいスクリプト コンポーネントは、メイン カメラにので追加されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-349">The new script component will be so added to the Main Camera.</span></span> 

![メイン カメラに FaceAnalysis を配置します。](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="cac27-351">7 - 章 ImageCapture クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="cac27-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="cac27-352">目的、 *ImageCapture*クラスとの通信に必要なメソッドをホストする、 *Azure 顔認識サービス*をそれに含まれる面を識別する、キャプチャするイメージを分析して既知のユーザーに属しているかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="cac27-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="cac27-353">既知のユーザーが見つかった場合、このクラスは、シーン内の UI テキストとして、名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="cac27-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="cac27-354">作成する、 *ImageCapture*クラス。</span><span class="sxs-lookup"><span data-stu-id="cac27-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="cac27-355">内側を右クリックし、**スクリプト**フォルダーをクリックし、以前は、作成した**作成**、  **C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="cac27-356">スクリプトを呼び出す*ImageCapture*します。</span><span class="sxs-lookup"><span data-stu-id="cac27-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="cac27-357">新しいをダブルクリックします。 *ImageCapture*スクリプトを Visual Studio 2017 で開くことです。</span><span class="sxs-lookup"><span data-stu-id="cac27-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="cac27-358">ImageCapture クラス上の次の名前空間を入力します。</span><span class="sxs-lookup"><span data-stu-id="cac27-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="cac27-359">内で、 *ImageCapture*クラスで、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="cac27-359">Inside the *ImageCapture* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  <span data-ttu-id="cac27-360">追加、 *Awake()* と*Start()* クラスを初期化し、ユーザーのジェスチャをキャプチャする HoloLens をできるようにするために必要なメソッド。</span><span class="sxs-lookup"><span data-stu-id="cac27-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  <span data-ttu-id="cac27-361">追加、 *TapHandler()* 、ユーザーが実行するときに呼び出されるか、*タップ*ジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="cac27-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  <span data-ttu-id="cac27-362">追加、 *ExecuteImageCaptureAndAnalysis()* メソッドで、イメージのキャプチャのプロセスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  <span data-ttu-id="cac27-363">写真のキャプチャ プロセスが完了したときに呼び出されるハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="cac27-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. <span data-ttu-id="cac27-364">**保存**Unity エディターに戻る前に変更します。</span><span class="sxs-lookup"><span data-stu-id="cac27-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="cac27-365">第 8 章 - ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="cac27-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="cac27-366">アプリケーションの徹底的なテストを実行するには、必要がありますをサイドロードすること、HoloLens にします。</span><span class="sxs-lookup"><span data-stu-id="cac27-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="cac27-367">実行する前にいることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cac27-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="cac27-368">第 3 章で説明されているすべての設定が正しく設定されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="cac27-369">スクリプト*FaceAnalysis* Main Camera オブジェクトに接続されています。</span><span class="sxs-lookup"><span data-stu-id="cac27-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="cac27-370">両方の**認証キー**と**グループ Id**内で設定されている、 *FaceAnalysis*スクリプト。</span><span class="sxs-lookup"><span data-stu-id="cac27-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="cac27-371">これをポイントするソリューションをビルドする準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="cac27-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="cac27-372">ソリューションが作成されると、アプリケーションをデプロイする準備ができます。</span><span class="sxs-lookup"><span data-stu-id="cac27-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="cac27-373">ビルド プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="cac27-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="cac27-374">現在のシーンを保存するには、保存、ファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cac27-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="cac27-375">開いているシーンを追加するファイル、ビルド設定 をクリックしてに移動します。</span><span class="sxs-lookup"><span data-stu-id="cac27-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="cac27-376">Unity のティックにことを確認C#プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="cac27-376">Make sure to tick Unity C# Projects.</span></span>

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="cac27-378">ビルドがキーを押します。</span><span class="sxs-lookup"><span data-stu-id="cac27-378">Press Build.</span></span> <span data-ttu-id="cac27-379">これを行う時に Unity が作成しにアプリをビルドするフォルダーを選択する必要がある、ファイル エクスプ ローラー ウィンドウを起動します。</span><span class="sxs-lookup"><span data-stu-id="cac27-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="cac27-380">Unity プロジェクト内で次に、そのフォルダーを作成し、アプリを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cac27-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="cac27-381">選択したアプリのフォルダー、フォルダーの選択キーを押します。</span><span class="sxs-lookup"><span data-stu-id="cac27-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="cac27-382">Unity では、アプリ フォルダーに、プロジェクトを構築が開始されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="cac27-383">1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了した、ビルドの場所にファイル エクスプ ローラー ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="cac27-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="cac27-385">[アプリ] フォルダーを開き、(上記のよう、MR_FaceRecognition.sln) 新しいプロジェクトのソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="cac27-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="cac27-386">第 9 章 - アプリケーションのデプロイ</span><span class="sxs-lookup"><span data-stu-id="cac27-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="cac27-387">HoloLens の展開。</span><span class="sxs-lookup"><span data-stu-id="cac27-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="cac27-388">必要になります、HoloLens の IP アドレス (リモート) を展開し、HoloLens をことを確認するには**開発者モード**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="cac27-389">これには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="cac27-389">To do this:</span></span>

    1. <span data-ttu-id="cac27-390">ソックスを着けずに、HoloLens 中を開く、**設定**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="cac27-391">移動して**ネットワークとインターネット > Wi-fi > 詳細オプション**</span><span class="sxs-lookup"><span data-stu-id="cac27-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="cac27-392">注、 **IPv4**アドレス。</span><span class="sxs-lookup"><span data-stu-id="cac27-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="cac27-393">次に移動します**設定**、し**更新とセキュリティ > 開発者向け**</span><span class="sxs-lookup"><span data-stu-id="cac27-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="cac27-394">開発者モードを設定します。</span><span class="sxs-lookup"><span data-stu-id="cac27-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="cac27-395">新しい Unity ビルドに移動します (、*アプリ*フォルダー) とソリューション ファイルを開くと*Visual Studio*します。</span><span class="sxs-lookup"><span data-stu-id="cac27-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="cac27-396">ソリューション構成の選択で**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="cac27-397">ソリューション プラットフォーム で選択**x86**、**リモート マシン**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="cac27-399">移動して、**ビルド メニューの** をクリック**ソリューションの配置**サイドロード、HoloLens をアプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="cac27-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="cac27-400">アプリが、起動する準備ができて、HoloLens にインストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="cac27-401">イマーシブ ヘッドセットを展開するには、設定、**ソリューション プラットフォーム**に*ローカル マシン*、設定と、**構成**に*デバッグ*で*x86*として、**プラットフォーム**します。</span><span class="sxs-lookup"><span data-stu-id="cac27-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="cac27-402">ローカルにデプロイし、machine を使用して、**ビルド メニューの**選択*ソリューションの配置*します。</span><span class="sxs-lookup"><span data-stu-id="cac27-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="cac27-403">第 10 章 - アプリケーションの使用</span><span class="sxs-lookup"><span data-stu-id="cac27-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="cac27-404">HoloLens、ソックスを着けずに、アプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="cac27-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="cac27-405">登録したユーザーを見て、 *Face API*します。</span><span class="sxs-lookup"><span data-stu-id="cac27-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="cac27-406">次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="cac27-406">Make sure that:</span></span>

    -  <span data-ttu-id="cac27-407">個人の顔がないと、遠と明確に表示</span><span class="sxs-lookup"><span data-stu-id="cac27-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="cac27-408">環境光が暗すぎます。</span><span class="sxs-lookup"><span data-stu-id="cac27-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="cac27-409">個人の写真をキャプチャするのにには、タップ ジェスチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="cac27-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="cac27-410">分析要求送信し、応答を受信するアプリを待ちます。</span><span class="sxs-lookup"><span data-stu-id="cac27-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="cac27-411">ユーザーが正常に認識された場合、ユーザーの名前は、UI テキストとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="cac27-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="cac27-412">数秒ごと、タップ ジェスチャを使用して、キャプチャ プロセスを繰り返すことができます。</span><span class="sxs-lookup"><span data-stu-id="cac27-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="cac27-413">完成した Azure Face API アプリケーション</span><span class="sxs-lookup"><span data-stu-id="cac27-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="cac27-414">これで、イメージ内の顔を検出して、任意の既知の顔を識別する顔認識の Azure サービスを利用している mixed reality アプリを構築します。</span><span class="sxs-lookup"><span data-stu-id="cac27-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![このコースを完了するの結果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="cac27-416">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="cac27-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="cac27-417">手順 1</span><span class="sxs-lookup"><span data-stu-id="cac27-417">Exercise 1</span></span>

<span data-ttu-id="cac27-418">**Azure の Face API** 1 つのイメージで最大 64 個の顔を検出するのに十分な強力です。</span><span class="sxs-lookup"><span data-stu-id="cac27-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="cac27-419">アプリケーションを拡張で他の多くの人々 の間で、2 つまたは 3 つの顔を認識する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cac27-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="cac27-420">手順 2</span><span class="sxs-lookup"><span data-stu-id="cac27-420">Exercise 2</span></span>

<span data-ttu-id="cac27-421">**Azure の Face API**がバックアップのすべての種類の属性情報を提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="cac27-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="cac27-422">これをアプリケーションに統合します。</span><span class="sxs-lookup"><span data-stu-id="cac27-422">Integrate this into the application.</span></span> <span data-ttu-id="cac27-423">これは、さらに興味深いと組み合わせて、 [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/)します。</span><span class="sxs-lookup"><span data-stu-id="cac27-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span></span>
