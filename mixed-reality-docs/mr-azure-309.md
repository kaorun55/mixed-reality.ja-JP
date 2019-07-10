---
title: MR と Azure 309 - Application insights
description: このコースでは、複合現実のアプリケーション内でユーザーの行動に関する Azure の Application Insights サービスを使用して、分析情報を収集する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、application insights、没入型、hololens、vr
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694568"
---
>[!NOTE]
><span data-ttu-id="ca45b-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ca45b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ca45b-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ca45b-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ca45b-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ca45b-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ca45b-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="ca45b-110">MR と Azure 309:Application insights</span><span class="sxs-lookup"><span data-stu-id="ca45b-110">MR and Azure 309: Application insights</span></span>

![最終的な製品-開始](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="ca45b-112">このコースではユーザーの行動に関する分析情報を収集する Azure Application Insights API を使用して複合現実のアプリケーションに Application Insights の機能を追加する方法についてはします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="ca45b-113">Application Insights は開発者にはアプリケーションから分析情報を収集し、使いやすいポータルから管理できるよう、Microsoft サービスです。</span><span class="sxs-lookup"><span data-stu-id="ca45b-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="ca45b-114">分析は、カスタム情報を収集するパフォーマンスから設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="ca45b-115">詳細については、次を参照してください。、 [Application Insights のページ](https://azure.microsoft.com/services/application-insights/)します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="ca45b-116">このコースを完了すると、以下を実行できる必要が複合現実イマーシブ ヘッドセット アプリケーションが完成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="ca45b-117">された様子を確認し、シーン内を移動するユーザーを許可します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="ca45b-118">Analytics への送信をトリガー、 *Application Insights サービス*、視線の先およびシーン内のオブジェクトの近接度を使用しています。</span><span class="sxs-lookup"><span data-stu-id="ca45b-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="ca45b-119">アプリは、サービスは、過去 24 時間内で、ユーザーが最もに近づくとオブジェクトがされている情報をフェッチ時に呼び出すこともします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="ca45b-120">そのオブジェクトには、緑色にその色が変化します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-120">That object will change its color to green.</span></span>

<span data-ttu-id="ca45b-121">このコースでは、Unity に基づくサンプル アプリケーションに Application Insights サービスで、結果を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="ca45b-122">最大をカスタム アプリケーションをビルドしている場合にこれらの概念を適用することがあります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="ca45b-123">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="ca45b-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ca45b-124">コース</span><span class="sxs-lookup"><span data-stu-id="ca45b-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ca45b-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ca45b-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ca45b-126"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="ca45b-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ca45b-127">MR と Azure 309:Application insights</span><span class="sxs-lookup"><span data-stu-id="ca45b-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="ca45b-128">✔️</span><span class="sxs-lookup"><span data-stu-id="ca45b-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ca45b-129">✔️</span><span class="sxs-lookup"><span data-stu-id="ca45b-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="ca45b-130">このコースが主に Windows Mixed Reality 没入型 (VR) ヘッドセットを重点的に Microsoft HoloLens には、このコースで学習する内容を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="ca45b-131">コースを実行するとき、HoloLens をサポートするために必要な場合があります変更でノートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="ca45b-132">HoloLens を使用する場合は、音声キャプチャ中にいくつかのエコーが気付きです。</span><span class="sxs-lookup"><span data-stu-id="ca45b-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ca45b-133">前提条件</span><span class="sxs-lookup"><span data-stu-id="ca45b-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ca45b-134">このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ca45b-135">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 7 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ca45b-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="ca45b-136">内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)にする必要がありますが想定されていなかったことについては、このコースでとまったく同じで記載されているものよりも新しいソフトウェアで表示されますが、記事以下に。</span><span class="sxs-lookup"><span data-stu-id="ca45b-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="ca45b-137">次のハードウェアとソフトウェアこのコースをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ca45b-138">開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発</span><span class="sxs-lookup"><span data-stu-id="ca45b-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ca45b-139">Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="ca45b-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ca45b-140">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="ca45b-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ca45b-141">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="ca45b-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ca45b-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ca45b-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="ca45b-143">A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効</span><span class="sxs-lookup"><span data-stu-id="ca45b-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="ca45b-144">(組み込みのマイクとスピーカー、ヘッドセットはされていない) 場合は、内蔵マイクでヘッドフォン</span><span class="sxs-lookup"><span data-stu-id="ca45b-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="ca45b-145">Azure のセットアップと Application Insights のデータ取得のインターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="ca45b-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ca45b-146">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="ca45b-146">Before you start</span></span>

<span data-ttu-id="ca45b-147">このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。</span><span class="sxs-lookup"><span data-stu-id="ca45b-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="ca45b-148">しようとするデータを対応する*Application Insights*時間がかかり、患者があるためです。</span><span class="sxs-lookup"><span data-stu-id="ca45b-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="ca45b-149">サービスが、データを受信したかどうかにチェックする場合は、チェック アウト[14 章](#chapter-14---the-application-insights-service-portal)ポータルに移動する方法を説明するされます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="ca45b-150">第 1 章 - Azure Portal</span><span class="sxs-lookup"><span data-stu-id="ca45b-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="ca45b-151">使用する*Application Insights*、作成および構成する必要があります、 *Application Insights サービス*Azure portal でします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="ca45b-152">[Azure ポータル](https://portal.azure.com) にログインします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ca45b-153">Azure アカウントがいない場合は、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ca45b-154">クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="ca45b-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ca45b-155">ログインした後は、をクリックして**新規**左上隅にある検索して*Application Insights*、 をクリック**Enter**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ca45b-156">単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="ca45b-158">右側に新しいページがの説明を入力、 *Azure Application Insights*サービス。</span><span class="sxs-lookup"><span data-stu-id="ca45b-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="ca45b-159">このページの左下にある at、**作成**ボタンは、この関連付けサービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="ca45b-161">クリックすると**作成**:</span><span class="sxs-lookup"><span data-stu-id="ca45b-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="ca45b-162">必要な挿入**名前**このサービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="ca45b-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="ca45b-163">として**アプリケーションの種類**、**全般**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="ca45b-164">適切な選択**サブスクリプション**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="ca45b-165">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ca45b-166">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ca45b-167">勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。</span><span class="sxs-lookup"><span data-stu-id="ca45b-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="ca45b-168">詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="ca45b-169">選択、**場所**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="ca45b-170">また、このサービスに適用される条件を理解したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="ca45b-171">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-171">Select **Create**.</span></span>

        ![Azure Portal](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="ca45b-173">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="ca45b-174">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="ca45b-176">新しいサービス インスタンスを探索する通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="ca45b-178">をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="ca45b-179">実施する、新しい*Application Insights サービス*インスタンス。</span><span class="sxs-lookup"><span data-stu-id="ca45b-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="ca45b-181">この web ページを開いたままにして簡単にアクセスでき、ここに戻り、収集されたデータを表示するには、多くの場合。</span><span class="sxs-lookup"><span data-stu-id="ca45b-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ca45b-182">Application Insights を実装するには次の 3 つ (3) 特定値を使用する必要があります。**インストルメンテーション キー**、**アプリケーション ID**、および**API キー**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="ca45b-183">次のとおり、サービスからこれらの値を取得する方法が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="ca45b-184">空白でこれらの値をメモしておきます*メモ帳*ページのコードですぐに使用するがあるためです。</span><span class="sxs-lookup"><span data-stu-id="ca45b-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="ca45b-185">検索する、**インストルメンテーション キー**、サービスの機能の一覧を下までスクロールし、をクリックする必要があります**プロパティ**、表示されるタブが表示されます、**サービス キー**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="ca45b-187">少し下**プロパティ**、検索は**API アクセス**、 をクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="ca45b-188">右側にパネルを提供、**アプリケーション ID**アプリの。</span><span class="sxs-lookup"><span data-stu-id="ca45b-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="ca45b-190">**アプリケーション ID**パネル をクリックします**API キーの作成**、これが表示されます、 *API キーの作成*パネル。</span><span class="sxs-lookup"><span data-stu-id="ca45b-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="ca45b-192">ここで開く内*API キーの作成*パネルで、説明を入力および**3 つのボックスをオンに**。</span><span class="sxs-lookup"><span data-stu-id="ca45b-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="ca45b-193">クリックして**キー生成**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-193">Click **Generate Key**.</span></span> <span data-ttu-id="ca45b-194">**API キー**が作成され、表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-194">Your **API Key** will be created and displayed.</span></span> 

    ![Azure Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="ca45b-196">これは、唯一の時間、**サービス キー**が表示されます、ようにして今すぐそのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="ca45b-197">第 2 章 - Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="ca45b-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="ca45b-198">次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。</span><span class="sxs-lookup"><span data-stu-id="ca45b-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="ca45b-199">開いている*Unity*クリック**新規**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-199">Open *Unity* and click **New**.</span></span>

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="ca45b-201">Unity プロジェクト名を指定する必要がありますこれで挿入**MR\_Azure\_アプリケーション\_Insights**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="ca45b-202">必ず、*テンプレート*に設定されている**3D**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="ca45b-203">設定、*場所*に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。</span><span class="sxs-lookup"><span data-stu-id="ca45b-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ca45b-204">をクリックし、**プロジェクトの作成**です。</span><span class="sxs-lookup"><span data-stu-id="ca45b-204">Then, click **Create project**.</span></span>

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="ca45b-206">既定値を確認する必要が開いている Unity、 **スクリプト エディター** に設定されている **Visual Studio** します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ca45b-207">移動して**編集\>設定**し、新しいウィンドウに移動**外部ツール**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ca45b-208">変更 **External Script Editor** に **Visual Studio 2017** します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ca45b-209">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="ca45b-209">Close the **Preferences** window.</span></span>

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="ca45b-211">次に移動**ファイル\>Build Settings**にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして、**プラットフォームの切り替え**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="ca45b-213">移動して**ファイル\>Build Settings**ことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ca45b-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="ca45b-214">**デバイスを対象に**に設定されている**任意のデバイス**</span><span class="sxs-lookup"><span data-stu-id="ca45b-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="ca45b-215">Microsoft HoloLens、設定**ターゲット デバイス**に*HoloLens*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="ca45b-216">**ビルドの種類**に設定されている**D3D**</span><span class="sxs-lookup"><span data-stu-id="ca45b-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="ca45b-217">**SDK**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="ca45b-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="ca45b-218">**ビルドおよび実行**に設定されている**ローカル マシン**</span><span class="sxs-lookup"><span data-stu-id="ca45b-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="ca45b-219">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="ca45b-220">これには、選択**開くシーンを追加**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="ca45b-221">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-221">A save window will appear.</span></span>

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="ca45b-223">任意の将来のシーンとこれには、新しいフォルダーを作成し、をクリックして、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="ca45b-225">新たに作成した開く**シーン**フォルダー、し、*ファイル名:* テキスト フィールドに「 **ApplicationInsightsScene**、順にクリックします**を保存**.</span><span class="sxs-lookup"><span data-stu-id="ca45b-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="ca45b-227">設定に残っている**Build Settings**、ここでは既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="ca45b-228">**Build Settings**ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、**インスペクター**が配置されています。</span><span class="sxs-lookup"><span data-stu-id="ca45b-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="ca45b-230">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="ca45b-231">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="ca45b-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="ca45b-232">**Scripting** **ランタイム バージョン**する必要があります**試験的 (.NET 4.6 Equivalent)** エディターを再起動する必要があるします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="ca45b-233">**バックエンドの scripting**べき **.NET**</span><span class="sxs-lookup"><span data-stu-id="ca45b-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="ca45b-234">**API の互換性レベル**べき **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="ca45b-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="ca45b-236">内で、**発行の設定**] タブの [**機能**、確認してください。</span><span class="sxs-lookup"><span data-stu-id="ca45b-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="ca45b-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ca45b-237">**InternetClient**</span></span>     

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="ca45b-239">パネル、下の方に**XR 設定**(次に示します**発行の設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed RealitySDK**が追加されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="ca45b-241">戻り**Build Settings**、 **UnityC#プロジェクト**が不要になったグレー; これの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="ca45b-242">ビルド設定ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="ca45b-243">シーンとプロジェクトを保存 (**ファイル** > **シーン保存/file** > **プロジェクト保存**)。</span><span class="sxs-lookup"><span data-stu-id="ca45b-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="ca45b-244">第 3 章 - Unity パッケージのインポート</span><span class="sxs-lookup"><span data-stu-id="ca45b-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ca45b-245">スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[309.unitypackage MR-Azure の](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)、としてプロジェクトにインポート、 [**カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="ca45b-246">[次へ] の章から Dll が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="ca45b-247">インポートの後から引き続き[**第 6 章**](#chapter-6---create-the-applicationinsightstracker-class)します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ca45b-248">Unity 内での Application Insights を使用するには、DLL を Newtonsoft DLL と共にインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="ca45b-249">インポート後に再構成するプラグインを必要とする Unity での既知の問題は現在します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="ca45b-250">バグが解決された後、次の手順 (このセクションでは 4 ~ 7) は必要に不要になった。</span><span class="sxs-lookup"><span data-stu-id="ca45b-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="ca45b-251">独自のプロジェクトに Application Insights をインポートするには、必ず確保[ダウンロード、'.unitypackage'、プラグインを含む](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="ca45b-252">次に、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ca45b-252">Then, do the following:</span></span>

1.  <span data-ttu-id="ca45b-253">追加、 **.unitypackage**に Unity を使用して、**資産\>パッケージのインポート\>カスタム パッケージ**メニュー オプション。</span><span class="sxs-lookup"><span data-stu-id="ca45b-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="ca45b-254">**Unity パッケージのインポート**その pop をボックスで、(およびなど)、すべてのことを確認**プラグイン**が選択されています。</span><span class="sxs-lookup"><span data-stu-id="ca45b-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Unity パッケージをインポートします。](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="ca45b-256">をクリックして、**インポート**をプロジェクトにアイテムを追加するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="ca45b-257">移動して、 **Insights**の下のフォルダー**プラグイン**プロジェクトを表示し、次のプラグインを選択*のみ*:</span><span class="sxs-lookup"><span data-stu-id="ca45b-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="ca45b-258">Microsoft.ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="ca45b-258">Microsoft.ApplicationInsights</span></span>

    ![Unity パッケージをインポートします。](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="ca45b-260">この*プラグイン*ように選択すると、 **Any プラットフォーム**は**unchecked**、ことを確認します**WSAPlayer**も**unchecked**、 をクリックし、**適用**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="ca45b-261">これは、ファイルが正しく構成されていることを確認するだけです。</span><span class="sxs-lookup"><span data-stu-id="ca45b-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Unity パッケージをインポートします。](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="ca45b-263">このようなプラグインをマークするには、Unity エディターでのみ使用することを構成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="ca45b-264">Dll プロジェクトは Unity からエクスポートした後に使用される、WSA フォルダー内のさまざまなセットがあります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="ca45b-265">次を開く必要があります、 **WSA**フォルダー内で、 **Insights**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="ca45b-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="ca45b-266">構成した同じファイルのコピーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="ca45b-267">このファイルを選択し、インスペクターのことを確認します**Any プラットフォーム**は**unchecked**、ことを確認します**のみ** **WSAPlayer** は、**チェック**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="ca45b-268">**[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-268">Click **Apply**.</span></span>

    ![Unity パッケージをインポートします。](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="ca45b-270">次のようになりましたが必要**手順 4 ~ 6**が、 *Newtonsoft*プラグイン代わりにします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="ca45b-271">参照してください、次のスクリーン ショットのように、結果がなります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Unity パッケージをインポートします。](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="ca45b-273">第 4 章 - を設定すると、カメラとユーザー コントロール</span><span class="sxs-lookup"><span data-stu-id="ca45b-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="ca45b-274">この章では、ユーザーを表示し、シーン内を移動できるように、カメラとコントロールを設定します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="ca45b-275">階層 パネルで、空の領域で右クリックして**作成** > **空**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="ca45b-277">新しい空の GameObject に名前を変更**カメラ親**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="ca45b-279">[階層] パネルで空の領域で右クリックし**3D オブジェクト**、次に**球**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="ca45b-280">球体の名前を変更**右側**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="ca45b-281">設定、**スケールを変換**を右側の**0.1、0.1、0.1**</span><span class="sxs-lookup"><span data-stu-id="ca45b-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="ca45b-283">削除、**球 Collider**コンポーネント をクリックして右側から、**歯車**で、*球 Collider*コンポーネント、し**コンポーネントの削除**.</span><span class="sxs-lookup"><span data-stu-id="ca45b-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="ca45b-285">階層パネル ドラッグで、 **Main Camera**と**右側**オブジェクトを**カメラ親**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ca45b-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="ca45b-287">設定、**変換位置**両方の**Main Camera**と**右側**オブジェクトを**0, 0, 0**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-31.png)

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="ca45b-290">第 5 章 - Unity シーン内のオブジェクトを設定</span><span class="sxs-lookup"><span data-stu-id="ca45b-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="ca45b-291">ここでは、ユーザーが操作できる、シーンのいくつかの基本的な図形を作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="ca45b-292">空の領域で右クリックし、*階層パネル*、次に**3D オブジェクト**を選択し、**平面**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="ca45b-293">平面を設定**位置を変換**に**0、-1、0**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="ca45b-294">平面を設定**スケールを変換**に**5, 1, 5**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="ca45b-296">使用する基本的な素材を作成、**平面**オブジェクト、その他の図形がわかりやすくなるようにします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="ca45b-297">移動、*プロジェクト パネル*、右クリックし、**作成**、その後に**フォルダー**、新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="ca45b-298">名前を付けます**資料**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-298">Name it **Materials**.</span></span>

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-34.png) ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="ca45b-301">開く、**資料**フォルダー、し、右クリックし、 をクリックします**作成**、し**マテリアル**、新しい素材を作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="ca45b-302">名前を付けます**青い**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-302">Name it **Blue**.</span></span>

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-36.png) ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="ca45b-305">新しい**青**素材を選択すると、参照で、*インスペクター*、と共に四角形のウィンドウをクリックします。 **Albedo**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="ca45b-306">青の色を選択します (次の 1 つの図は、 **16 進数の色。\#3592FFFF**)。</span><span class="sxs-lookup"><span data-stu-id="ca45b-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="ca45b-307">選択した後は、閉じるボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-307">Click the close button once you have chosen.</span></span>

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="ca45b-309">新しいマテリアルをドラッグして、**資料**フォルダー、新たに作成した**平面**、シーン内で (またはの上にドロップ、**平面**オブジェクト内、 *階層*)。</span><span class="sxs-lookup"><span data-stu-id="ca45b-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="ca45b-311">空の領域で右クリックし、*階層パネル*、次に**3 D オブジェクト、Capsule**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="ca45b-312">**Capsule**変更選択すると、その\**変換\*\*\*位置*を: **-10, 1, 0**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="ca45b-313">空の領域で右クリックし、*階層パネル*、次に**3 D オブジェクト、Cube**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="ca45b-314">**キューブ**変更選択すると、その**変換\*\**位置*に。**0, 0, 10\*\*.</span><span class="sxs-lookup"><span data-stu-id="ca45b-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="ca45b-315">空の領域で右クリックし、*階層パネル*、次に**3 D オブジェクト、球体**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="ca45b-316">**球**変更選択すると、その**変換\*\**位置*に。**10, 0, 0\*\*.</span><span class="sxs-lookup"><span data-stu-id="ca45b-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="ca45b-318">これら*位置*値は*提案*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="ca45b-319">自由にカメラから遠すぎてオブジェクト間の距離がない場合は、アプリケーションのユーザーを簡単に好きなに、オブジェクトの位置を設定できます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="ca45b-320">アプリケーションが実行されている場合、これを実現するために、シーン内のオブジェクトを識別するためにできるようにする必要がある、タグ付けする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="ca45b-321">選択して、オブジェクトの 1 つ、*インスペクター*パネルで、をクリックして**タグを追加しています.** 、スワップされますが、*インスペクター*で、**タグし、レイヤー**パネル。</span><span class="sxs-lookup"><span data-stu-id="ca45b-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="ca45b-322">![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="ca45b-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="ca45b-323">をクリックして、 **+ (正符号 +)** 記号、としてタグの名前を入力**ObjectInScene**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="ca45b-325">別の名前、タグを使用する場合もこの変更が行われたことを確認する必要があります、 *DataFromAnalytics*、 *ObjectTrigger*、と*視線*、後で、スクリプトを、。オブジェクトが検出され、検出されると、シーン内で。</span><span class="sxs-lookup"><span data-stu-id="ca45b-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="ca45b-326">作成したタグを 3 つのオブジェクトのすべてに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="ca45b-327">*階層*、保持、 **Shift**キーをクリック、 **Capsule**、**キューブ**、および**球**、オブジェクトは、次に、*インスペクター*、と共にドロップダウン メニューをクリックします。**タグ**、順にクリックします、 *ObjectInScene*タグを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="ca45b-328">![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="ca45b-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="ca45b-329">第 6 章 - ApplicationInsightsTracker クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="ca45b-330">最初のスクリプトを作成する必要があるは**ApplicationInsightsTracker**は責任を負います。</span><span class="sxs-lookup"><span data-stu-id="ca45b-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="ca45b-331">Azure Application Insights に送信するためのユーザー操作に基づいてイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="ca45b-332">ユーザーの操作に応じて、適切なイベント名を作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="ca45b-333">Application Insights サービスのインスタンスにイベントを送信しています。</span><span class="sxs-lookup"><span data-stu-id="ca45b-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="ca45b-334">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-334">To create this class:</span></span>

1.  <span data-ttu-id="ca45b-335">右クリックし、*プロジェクト パネル*、し**作成** > **フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="ca45b-336">フォルダーの名前**スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-336">Name the folder **Scripts**.</span></span>

    ![ApplicationInsightsTracker クラスを作成します。](images/AzureLabs-Lab309-46.png)  ![ApplicationInsightsTracker クラスを作成します。](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="ca45b-339">**スクリプト**フォルダーが作成されると、ダブルクリックして、開きます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="ca45b-340">その後、そのフォルダー内で右クリックし、**作成** >   **C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="ca45b-341">スクリプトの名前**ApplicationInsightsTracker**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="ca45b-342">ダブルクリックして、新しい**ApplicationInsightsTracker**スクリプト ファイルを開く**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="ca45b-343">更新するスクリプトの上部にある名前空間以下のとおり。</span><span class="sxs-lookup"><span data-stu-id="ca45b-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="ca45b-344">クラス内には、次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-344">Inside the class insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > <span data-ttu-id="ca45b-345">設定、 **instrumentationKey、applicationId および API_Key**を使用して、適切な値、*サービス キー*で説明したように、Azure Portal から[第 1 章](#chapter-1---the-azure-portal)手順 9以降。</span><span class="sxs-lookup"><span data-stu-id="ca45b-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="ca45b-346">追加し、 **Start()** と**Awake()** メソッドで、クラスを初期化するときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  <span data-ttu-id="ca45b-347">イベントと、アプリケーションで登録されているメトリックの送信を行うメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  <span data-ttu-id="ca45b-348">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="ca45b-349">Chapter 7 - 視線入力スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="ca45b-350">次のスクリプトを作成するには、**視線**スクリプト。</span><span class="sxs-lookup"><span data-stu-id="ca45b-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="ca45b-351">このスクリプトは作成を担当する、 *Raycast*からフォワード投影は、 *Main Camera*ユーザーが見るオブジェクトを検出します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="ca45b-352">ここで、 *Raycast*を持つオブジェクトで、ユーザーが探している場合を識別する必要があります、 **ObjectInScene** 、タグを付けるし、ユーザーはどのくらいの時間をカウントし、 *gazes*でそのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ca45b-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="ca45b-353">ダブルクリックして、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="ca45b-354">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="ca45b-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="ca45b-355">スクリプトの名前**視線**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="ca45b-356">Visual Studio で開くことをスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="ca45b-357">次のように、既存のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-357">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  <span data-ttu-id="ca45b-358">コードを**Awake()** と**Start()** 今すぐメソッドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  <span data-ttu-id="ca45b-359">内で、**視線**クラスで、次のコードを追加、 **Update()** プロジェクトにメソッドを*Raycast*ターゲット ヒットの検出と。</span><span class="sxs-lookup"><span data-stu-id="ca45b-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  <span data-ttu-id="ca45b-360">追加、 **ResetFocusedObject()** メソッドは、データを送信する**Application Insights**オブジェクトで、ユーザーが検索する場合。</span><span class="sxs-lookup"><span data-stu-id="ca45b-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  <span data-ttu-id="ca45b-361">完了したので、**視線**スクリプト。</span><span class="sxs-lookup"><span data-stu-id="ca45b-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="ca45b-362">変更を保存*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="ca45b-363">8 - 章 ObjectTrigger クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="ca45b-364">次のスクリプトを作成する必要があるは**ObjectTrigger**は責任を負います。</span><span class="sxs-lookup"><span data-stu-id="ca45b-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="ca45b-365">メイン カメラの衝突の必要なコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="ca45b-366">カメラが近くとしてタグ付けされたオブジェクトがかどうかを検出する**ObjectInScene**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="ca45b-367">スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-367">To create the script:</span></span>

1.  <span data-ttu-id="ca45b-368">ダブルクリックして、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="ca45b-369">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="ca45b-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="ca45b-370">スクリプトの名前**ObjectTrigger**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="ca45b-371">Visual Studio で開くことをスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="ca45b-372">次のように、既存のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-372">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  <span data-ttu-id="ca45b-373">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="ca45b-374">9 - 章 DataFromAnalytics クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="ca45b-375">作成する必要がありますこれで、 **DataFromAnalytics**を担当するスクリプト。</span><span class="sxs-lookup"><span data-stu-id="ca45b-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="ca45b-376">どのオブジェクトがされてに近づくと、カメラで最も analytics データをフェッチしています。</span><span class="sxs-lookup"><span data-stu-id="ca45b-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="ca45b-377">使用して、*サービス キー*、Azure Application Insights のサービス インスタンスと通信できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="ca45b-378">シーン内のオブジェクトを並べ替え、これに基づいてが最上位のイベント数。</span><span class="sxs-lookup"><span data-stu-id="ca45b-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="ca45b-379">最も approached のオブジェクトのマテリアルの色を変更する*緑色*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="ca45b-380">スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-380">To create the script:</span></span>

1.  <span data-ttu-id="ca45b-381">ダブルクリックして、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="ca45b-382">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="ca45b-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="ca45b-383">スクリプトの名前**DataFromAnalytics**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="ca45b-384">Visual Studio で開くことをスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="ca45b-385">次の名前空間を挿入します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="ca45b-386">スクリプト内で、次のように挿入します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-386">Inside the script, insert the following:</span></span>

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  <span data-ttu-id="ca45b-387">内で、 **DataFromAnalytics**クラス、直後、 **Start()** メソッドと呼ばれる次のメソッドを追加**FetchAnalytics()** します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="ca45b-388">このメソッドは、キー値のペアのリストに追加、 *GameObject*とプレース ホルダーのイベントのカウント数。</span><span class="sxs-lookup"><span data-stu-id="ca45b-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="ca45b-389">初期化し、 **GetWebRequest()** コルーチンします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="ca45b-390">クエリ構造への呼び出しの*Application Insights*このメソッド内で見つかんだことができますも、として、*クエリ URL*エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="ca45b-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  <span data-ttu-id="ca45b-391">すぐ下、 **FetchAnalytics()** メソッドというメソッドを追加**GetWebRequest()** 、返された、 *IEnumerator*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="ca45b-392">このメソッドは、特定の対応するイベントを発生回数の合計を要求する責任を負います*GameObject*が内で呼び出された*Application Insights*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="ca45b-393">送信されたすべてのクエリが返されるときに、 **DetermineWinner()** メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="ca45b-394">次の方法は**DetermineWinner()** の一覧の並べ替え*GameObject*と*Int*最大イベント数に従ってのペア。</span><span class="sxs-lookup"><span data-stu-id="ca45b-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="ca45b-395">マテリアルの色を変更し、 *GameObject*に*緑色*(フィードバックの最大数を持つ) として。</span><span class="sxs-lookup"><span data-stu-id="ca45b-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="ca45b-396">これには、分析結果を含むメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-396">This displays a message with the analytics results.</span></span>

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  <span data-ttu-id="ca45b-397">受け取った JSON オブジェクトを逆シリアル化するために使用するクラスの構造を追加*Application Insights*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="ca45b-398">一番下にこれらのクラスを追加、 **DataFromAnalytics**クラス ファイル、**外**クラス定義の。</span><span class="sxs-lookup"><span data-stu-id="ca45b-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. <span data-ttu-id="ca45b-399">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="ca45b-400">章 10 - 移動クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="ca45b-401">**移動**スクリプトは、次のスクリプトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="ca45b-402">担当します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-402">It is responsible for:</span></span>

- <span data-ttu-id="ca45b-403">カメラの方向に応じて、メイン カメラの移動は、方向に求めています。</span><span class="sxs-lookup"><span data-stu-id="ca45b-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="ca45b-404">シーンのオブジェクトには、その他のすべてのスクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="ca45b-405">スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-405">To create the script:</span></span>

1.  <span data-ttu-id="ca45b-406">ダブルクリックして、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="ca45b-407">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="ca45b-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="ca45b-408">スクリプトの名前**移動**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="ca45b-409">ファイルを開くスクリプトをダブルクリックして*Visual Studio*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="ca45b-410">次のように、既存のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-410">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  <span data-ttu-id="ca45b-411">内で、**移動**クラス、*下*空**Update()** メソッド、手の形のコント ローラーを使用して仮想空間に移動するユーザーを許可する次のメソッドを挿入します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  <span data-ttu-id="ca45b-412">最後に、メソッドの呼び出し内の追加、 **Update()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="ca45b-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="ca45b-413">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="ca45b-414">第 11 章 – スクリプト参照の設定</span><span class="sxs-lookup"><span data-stu-id="ca45b-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="ca45b-415">この章では、配置する必要があります、**移動**にスクリプト、**カメラ親**し、その参照のターゲットを設定します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="ca45b-416">他のスクリプトに必要な場所に配置するスクリプトを処理し、します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="ca45b-417">**スクリプト**フォルダーで、*プロジェクト パネル*、ドラッグ、**移動**スクリプトを**カメラ親**内にあるオブジェクトは、*階層パネル*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Unity シーン内のスクリプト参照の設定](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="ca45b-419">をクリックして、**カメラ親**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="ca45b-420">*階層パネル*、ドラッグ、**右側**オブジェクトから、*階層パネル*、参照先を**コント ローラー**で、*インスペクター パネル*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="ca45b-421">設定、**ユーザー速度**に**5**、次の図に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Unity シーン内のスクリプト参照の設定](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="ca45b-423">第 12 章 - Unity プロジェクトをビルド</span><span class="sxs-lookup"><span data-stu-id="ca45b-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="ca45b-424">このプロジェクトの Unity のセクションの必要なすべてが今すぐ完了したら、ので、Unity から構築するための時間。</span><span class="sxs-lookup"><span data-stu-id="ca45b-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="ca45b-425">移動します**ビルド設定**、(**ファイル** > **ビルド設定**)。</span><span class="sxs-lookup"><span data-stu-id="ca45b-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="ca45b-426">**Build Settings**ウィンドウで、をクリックして**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-426">From the **Build Settings** window, click **Build**.</span></span>

    ![UWP のソリューションに Unity プロジェクトをビルドします。](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="ca45b-428">A**ファイル エクスプ ローラー**ウィンドウがポップアップで、ビルドの場所の入力を求めます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="ca45b-429">新しいフォルダーを作成 (をクリックして**新しいフォルダー**左上隅にある)、名前を付けます**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![UWP のソリューションに Unity プロジェクトをビルドします。](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="ca45b-431">開く、新しい**ビルド**フォルダー、別のフォルダーを作成し、(を使用して**新しいフォルダー**もう一度)、名前を付けます**MR\_Azure\_アプリケーション\_Insights**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![UWP のソリューションに Unity プロジェクトをビルドします。](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="ca45b-433">**MR\_Azure\_アプリケーション\_Insights**フォルダーを選択すると、クリックして**フォルダーの選択**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="ca45b-434">プロジェクトは、ビルドを 1 分程度かかります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="ca45b-435">次の*ビルド*、**ファイル エクスプ ローラー**新しいプロジェクトの場所が示されますが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a><span data-ttu-id="ca45b-436">第 13 章 - MR_Azure_Application_Insights アプリ、マシンをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="ca45b-437">展開する、 **MR\_Azure\_アプリケーション\_Insights**ローカル コンピューター上のアプリ。</span><span class="sxs-lookup"><span data-stu-id="ca45b-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="ca45b-438">ソリューション ファイルを開き、 **MR\_Azure\_アプリケーション\_Insights**でアプリ**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="ca45b-439">**ソリューション プラットフォーム**、 **x86、ローカル コンピューター**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="ca45b-440">**ソリューション構成**選択**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![UWP のソリューションに Unity プロジェクトをビルドします。](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="ca45b-442">移動して**ビルド メニューの** をクリック**ソリューションの配置**をコンピューターにアプリケーションをサイドローディングします。</span><span class="sxs-lookup"><span data-stu-id="ca45b-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="ca45b-443">アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="ca45b-444">複合現実のアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="ca45b-445">オブジェクトに近づいていると、それを見て、シーンの移動時に、 *Azure Insight サービス*十分なイベント データが収集が緑に最も対処されているオブジェクトが設定されます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="ca45b-446">平均待機時間を中に、*イベントとメトリック*約 15 分は、サービスによって収集されるように、いくつかの状況で最大 1 時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="ca45b-447">第 14 章 – Application Insights サービス ポータル</span><span class="sxs-lookup"><span data-stu-id="ca45b-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="ca45b-448">シーンを中心にローミングしたし、いくつかのオブジェクトで gazed で収集されたデータを表示できます、 *Application Insights サービス*ポータル。</span><span class="sxs-lookup"><span data-stu-id="ca45b-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="ca45b-449">Application Insights サービス ポータルに戻ります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="ca45b-450">をクリックして*メトリックス エクスプ ローラー*します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-450">Click on *Metrics Explorer*.</span></span>

    ![収集されたデータを見る](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="ca45b-452">表すグラフを含むタブが開きます、*イベントとメトリック*アプリケーションに関連します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="ca45b-453">前述のように、グラフに表示されるデータ (最大 1 時間) まで時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ca45b-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![収集されたデータを見る](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="ca45b-455">をクリックして、*イベント バー*で、*イベントの合計*でその名前を持つイベントの詳細な内訳を表示する、アプリケーションのバージョン。</span><span class="sxs-lookup"><span data-stu-id="ca45b-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![収集されたデータを見る](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="ca45b-457">Application Insights サービス アプリケーションの終了</span><span class="sxs-lookup"><span data-stu-id="ca45b-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="ca45b-458">これで、アプリ内のユーザーのアクティビティを監視する Application Insights サービスを利用している mixed reality アプリを構築します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![コースの結果](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="ca45b-460">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="ca45b-460">Bonus Exercises</span></span>

<span data-ttu-id="ca45b-461">**手順 1**</span><span class="sxs-lookup"><span data-stu-id="ca45b-461">**Exercise 1**</span></span>

<span data-ttu-id="ca45b-462">手動で作成する, ObjectInScene オブジェクトを起動し、スクリプト内で平面上の座標を設定します。</span><span class="sxs-lookup"><span data-stu-id="ca45b-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="ca45b-463">これにより、質問を入力できます Azure どのような最も人気のあるオブジェクトが (視線の先または近接検索の結果からいずれか) と生成、*余分な*それらのオブジェクトのいずれか。</span><span class="sxs-lookup"><span data-stu-id="ca45b-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="ca45b-464">**手順 2**</span><span class="sxs-lookup"><span data-stu-id="ca45b-464">**Exercise 2**</span></span>

<span data-ttu-id="ca45b-465">最も重要なデータを取得して、アプリケーションで時間その機微なデータを実装するように、時間で Application Insights 結果を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="ca45b-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

