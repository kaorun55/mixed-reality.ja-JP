---
title: MR、および Azure 308 - クロス デバイスの通知
description: このコースでは、複合現実のアプリケーション内で Azure Notification Hubs、Azure Functions と Azure Storage、およびテーブルを実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、通知、関数、テーブル、hololens、没入型、vr、notification hubs
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694603"
---
>[!NOTE]
><span data-ttu-id="5e365-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5e365-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5e365-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="5e365-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5e365-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5e365-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5e365-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="5e365-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="5e365-110">MR と Azure 308:クロス デバイスの通知</span><span class="sxs-lookup"><span data-stu-id="5e365-110">MR and Azure 308: Cross-device notifications</span></span>

![最終的な製品-開始](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="5e365-112">このコースでは、Azure Notification Hubs、Azure テーブル、および Azure Functions を使用して、複合現実のアプリケーションに Notification Hubs の機能を追加する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="5e365-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="5e365-113">**Azure Notification Hubs**はにより、開発者は、クラウド内ですべて電源任意のプラットフォームを対象となる、パーソナライズされたプッシュ通知を送信する、Microsoft のサービスです。</span><span class="sxs-lookup"><span data-stu-id="5e365-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="5e365-114">開発者は、エンドユーザーとの通信を効果的に許可したり、シナリオに応じて、さまざまなアプリケーション間の通信もできます。</span><span class="sxs-lookup"><span data-stu-id="5e365-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="5e365-115">詳細については、次を参照してください。、 **Azure Notification Hubs** [ページ](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="5e365-116">**Azure Functions**できる小規模なコードを実行する開発者の Microsoft サービス '関数'、Azure では、します。</span><span class="sxs-lookup"><span data-stu-id="5e365-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="5e365-117">これは、多くのメリットを持つことができる、ローカル アプリケーションではなく、クラウドに作業を委任する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="5e365-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="5e365-118">**Azure Functions** C をなど、複数の開発言語をサポートしている\#、F\#Node.js、Java、および PHP します。</span><span class="sxs-lookup"><span data-stu-id="5e365-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="5e365-119">詳細については、次を参照してください。、 **Azure Functions** [ページ](https://docs.microsoft.com/azure/azure-functions/functions-overview)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="5e365-120">**Azure テーブル**開発者が、クラウドで構造化された非 SQL データを格納する、Microsoft クラウド サービスを得ることが簡単にアクセスできる任意の場所。</span><span class="sxs-lookup"><span data-stu-id="5e365-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="5e365-121">サービスは、スキーマレス設計になっているため、必要に応じて、テーブルの進化は幅広いプラットフォーム、非常に柔軟なは。</span><span class="sxs-lookup"><span data-stu-id="5e365-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="5e365-122">詳細については、次を参照してください、 **Azure Tables** [ページ。](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="5e365-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="5e365-123">このコースを完了すると、複合現実、イマーシブ ヘッドセット アプリケーションと、以下を実行できる必要がデスクトップ PC のアプリケーションが用意されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="5e365-124">デスクトップ PC のアプリが (X および Y) の 2 次元空間でオブジェクトを移動するユーザーを許可する、マウスを使用します。</span><span class="sxs-lookup"><span data-stu-id="5e365-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="5e365-125">PC のアプリ内のオブジェクトの移動では、文字列の形式になります JSON を使用して、型、オブジェクト ID を格納しているクラウドに送信され、(X と Y 座標) の情報を変換します。</span><span class="sxs-lookup"><span data-stu-id="5e365-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="5e365-126">デスクトップ アプリに同一のシーンのある、mixed reality アプリでは、(これは、デスクトップ PC のアプリで更新されただけですが)、Notification Hubs サービスからオブジェクトの移動に関する通知を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5e365-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="5e365-127">オブジェクト ID、型、および変換の情報には、通知を受信すると、mixed reality アプリで受信した情報を独自のシーンに適用されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="5e365-128">アプリケーションでは、責任ですが、設計と、結果を統合する方法について。</span><span class="sxs-lookup"><span data-stu-id="5e365-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="5e365-129">このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。</span><span class="sxs-lookup"><span data-stu-id="5e365-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="5e365-130">複合現実アプリを強化するためには、このコース得た知識を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="5e365-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="5e365-131">このコースは、他の複合現実ラボに直接関係は自己完結型のチュートリアルです。</span><span class="sxs-lookup"><span data-stu-id="5e365-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="5e365-132">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="5e365-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5e365-133">コース</span><span class="sxs-lookup"><span data-stu-id="5e365-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5e365-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5e365-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5e365-135"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="5e365-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="5e365-136">MR と Azure 308:クロス デバイスの通知</span><span class="sxs-lookup"><span data-stu-id="5e365-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="5e365-137">✔️</span><span class="sxs-lookup"><span data-stu-id="5e365-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="5e365-138">✔️</span><span class="sxs-lookup"><span data-stu-id="5e365-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="5e365-139">このコースが主に Windows Mixed Reality 没入型 (VR) ヘッドセットを重点的に Microsoft HoloLens には、このコースで学習する内容を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5e365-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="5e365-140">コースを実行するとき、HoloLens をサポートするために必要な場合があります変更でノートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="5e365-141">HoloLens を使用する場合は、音声キャプチャ中にいくつかのエコーが気付きです。</span><span class="sxs-lookup"><span data-stu-id="5e365-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e365-142">前提条件</span><span class="sxs-lookup"><span data-stu-id="5e365-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="5e365-143">このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。</span><span class="sxs-lookup"><span data-stu-id="5e365-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="5e365-144">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 5 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5e365-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="5e365-145">内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)ことについては、このコースでとまったく同じで見つかりますの下に記載されているものよりも新しいソフトウェアでどのようなことは仮定されませんが、記事.</span><span class="sxs-lookup"><span data-stu-id="5e365-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="5e365-146">次のハードウェアとソフトウェアこのコースをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5e365-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="5e365-147">開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発</span><span class="sxs-lookup"><span data-stu-id="5e365-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="5e365-148">Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="5e365-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5e365-149">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="5e365-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5e365-150">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="5e365-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5e365-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="5e365-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="5e365-152">A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効</span><span class="sxs-lookup"><span data-stu-id="5e365-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="5e365-153">Azure のセットアップと Notification Hubs へのアクセスにインターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="5e365-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="5e365-154">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="5e365-154">Before you start</span></span>

- <span data-ttu-id="5e365-155">このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。</span><span class="sxs-lookup"><span data-stu-id="5e365-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="5e365-156">Microsoft 開発者ポータルと、アプリケーション登録ポータルの所有者である必要がある、それ以外の場合でアプリにアクセスする権限があるがない[第 2 章](#chapter-2---retrieve-your-new-apps-credentials)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="5e365-157">Chapter 1 - Microsoft 開発者ポータルでアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="5e365-158">使用する、 **Azure Notification Hubs**サービス、する必要があります、Microsoft 開発者ポータルでアプリケーションを作成するように、アプリケーションが送信して通知を受信できるように登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="5e365-159">ログイン、 [Microsoft 開発者ポータル](https://developer.microsoft.com/dashboard)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="5e365-160">Microsoft アカウントにログインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="5e365-161">ダッシュ ボードで、次のようにクリックします。**新しいアプリを作成**です。</span><span class="sxs-lookup"><span data-stu-id="5e365-161">From the Dashboard, click **Create a new app**.</span></span>

    ![アプリを作成します。](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="5e365-163">新しいアプリの名前を予約する必要があります、ポップアップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="5e365-164">ボックスに、適切な名前では; を挿入します。選択した名前を使用できる場合、テキスト ボックスの右側にチェック マークが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="5e365-165">挿入された、使用可能な名前を作成したら、 をクリックして、**製品名の予約**ポップアップの左下にボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![名前を反転します。](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="5e365-167">ここで作成したアプリケーション、[次へ] の章に移動する準備が完了したら。</span><span class="sxs-lookup"><span data-stu-id="5e365-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="5e365-168">Chapter 2 - 新しいアプリ資格情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="5e365-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="5e365-169">新しいアプリが表示され、セットアップに使用される資格情報を取得、アプリケーション登録ポータルにログイン、 **Notification Hubs サービス**内、 **Azure Portal**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="5e365-170">移動し、[アプリケーション登録ポータル](http://apps.dev.microsoft.com)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![アプリケーション登録ポータル](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="5e365-172">ログインに Microsoft アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="5e365-173">これは、**する必要があります**、以前使用した Microsoft アカウントである[章](#chapter-1---create-an-application-on-the-microsoft-developer-portal)、Windows ストア開発者ポータルを使用しました。</span><span class="sxs-lookup"><span data-stu-id="5e365-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="5e365-174">下でアプリが表示されます、**アプリケーション**セクション。</span><span class="sxs-lookup"><span data-stu-id="5e365-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="5e365-175">クリックして、アプリを新しいページに表示されますが見つかった場合、名前と**登録**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![新しく登録されたアプリ](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="5e365-177">スクロール登録ページを参照して、**アプリケーション シークレット**セクションおよび**パッケージ SID**アプリ。</span><span class="sxs-lookup"><span data-stu-id="5e365-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="5e365-178">セットアップで使用するための両方をコピー、 **Azure Notification Hubs サービス**[次へ] の章。</span><span class="sxs-lookup"><span data-stu-id="5e365-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![アプリケーション シークレット](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="5e365-180">3 - Azure ポータルのセットアップの章: Notification Hubs サービスの作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="5e365-181">Apps の資格情報を取得するには、Azure Notification Hubs サービスを作成する、Azure Portal に移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="5e365-182">[Azure ポータル](https://portal.azure.com) にログインします。</span><span class="sxs-lookup"><span data-stu-id="5e365-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="5e365-183">Azure アカウントがいない場合は、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="5e365-184">クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="5e365-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="5e365-185">ログインした後は、をクリックして**新規**左上隅にある検索して**Notification Hub**、 をクリック***Enter***。</span><span class="sxs-lookup"><span data-stu-id="5e365-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![通知ハブの検索](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="5e365-187">単語***新規***に置き換えられました**リソースの作成**、新しいポータルでします。</span><span class="sxs-lookup"><span data-stu-id="5e365-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="5e365-188">新しいページがの説明を入力、 *Notification Hubs*サービス。</span><span class="sxs-lookup"><span data-stu-id="5e365-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="5e365-189">このプロンプトの左下にある at、**作成**ボタンは、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![notification hubs のインスタンスを作成します。](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="5e365-191">クリックすると***作成***:</span><span class="sxs-lookup"><span data-stu-id="5e365-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="5e365-192">このサービス インスタンスのご希望の名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="5e365-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="5e365-193">提供、**名前空間**がこのアプリに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="5e365-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="5e365-194">選択、**場所。**</span><span class="sxs-lookup"><span data-stu-id="5e365-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="5e365-195">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="5e365-196">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="5e365-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="5e365-197">勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。</span><span class="sxs-lookup"><span data-stu-id="5e365-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="5e365-198">詳細にする場合について、Azure リソース グループに従ってくださいこの[リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="5e365-199">適切な選択**サブスクリプション**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="5e365-200">また、このサービスに適用される条件を理解したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="5e365-201">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5e365-201">Select **Create**.</span></span>

        ![サービスの詳細を入力します。](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="5e365-203">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="5e365-204">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![通知 (notification)](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="5e365-206">をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="5e365-207">実施する、新しい**Notification Hub**サービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="5e365-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![リソースに移動します。](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="5e365-209">概要 ページで、ページの真ん中からクリックして**Windows (WNS)。**</span><span class="sxs-lookup"><span data-stu-id="5e365-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="5e365-210">右側のパネルを必要とする 2 つの表示テキスト フィールドに変更は、**パッケージ SID**と**セキュリティ キー**、以前設定したアプリから。</span><span class="sxs-lookup"><span data-stu-id="5e365-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![新しく作成したハブのサービス](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="5e365-212">詳細は、適切なフィールドにコピーした、したら**保存**、通知ハブが正常に更新されたときに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![セキュリティの詳細をコピーします。](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="5e365-214">4 - Azure ポータルのセットアップの章: Table Service の作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="5e365-215">Notification Hubs のサービス インスタンスを作成した後は、ストレージ リソースを作成して、Azure テーブル サービスを作成する、Azure ポータルに戻る移動します。</span><span class="sxs-lookup"><span data-stu-id="5e365-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="5e365-216">サインインしていない場合のログイン、 [Azure Portal](https://portal.azure.com)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="5e365-217">ログインすると、をクリックして**新規**左上隅にある検索して**ストレージ アカウント**、 をクリック**Enter**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="5e365-218">単語***新規***に置き換えられました**リソースの作成**、新しいポータルでします。</span><span class="sxs-lookup"><span data-stu-id="5e365-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="5e365-219">選択**ストレージ アカウント - blob、ファイル、テーブル、キュー**一覧から。</span><span class="sxs-lookup"><span data-stu-id="5e365-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![ストレージ アカウントの検索](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="5e365-221">新しいページがの説明を入力、**ストレージ アカウント**サービス。</span><span class="sxs-lookup"><span data-stu-id="5e365-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="5e365-222">このプロンプトの左下にある at、**作成**ボタンは、このサービスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="5e365-224">クリックすると**作成**パネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="5e365-225">必要な挿入**名前**(すべて小文字にする必要があります)、このサービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="5e365-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="5e365-226">**デプロイ モデル**、 をクリックして**Resource manager**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="5e365-227">**アカウントの種類**、ドロップダウン メニューを使用して、選択**ストレージ (汎用 v1)** します。</span><span class="sxs-lookup"><span data-stu-id="5e365-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="5e365-228">適切な選択**場所**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="5e365-229">**レプリケーション**ドロップダウン メニューで、**読み取りアクセスの geo 冗長ストレージ (RA-GRS)** します。</span><span class="sxs-lookup"><span data-stu-id="5e365-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="5e365-230">**パフォーマンス**、 をクリックして**標準**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="5e365-231">内で、**転送が必須のセキュリティで保護された**セクションで、**無効**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="5e365-232">**サブスクリプション**ドロップダウン メニューで、適切なサブスクリプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="5e365-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="5e365-233">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="5e365-234">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="5e365-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="5e365-235">勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。</span><span class="sxs-lookup"><span data-stu-id="5e365-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="5e365-236">詳細にする場合について、Azure リソース グループに従ってくださいこの[リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="5e365-237">まま**仮想ネットワーク**として**無効になっている**するためのオプションの場合。</span><span class="sxs-lookup"><span data-stu-id="5e365-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="5e365-238">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-238">Click **Create**.</span></span>

        ![ストレージの詳細を入力します。](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="5e365-240">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="5e365-241">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="5e365-242">新しいサービス インスタンスを探索する通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-242">Click on the notifications to explore your new Service instance.</span></span>

    ![新しい記憶域の通知](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="5e365-244">をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="5e365-245">新しい記憶域のサービス インスタンスの概要ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![リソースに移動します。](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="5e365-247">概要 ページの右側にあるをクリックします。**テーブル**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="5e365-248">右側のパネルを表示する変更は、 **Table service**については、の新しいテーブルを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="5e365-249">クリックして、 **+** **テーブル**ボタンの左上隅をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![テーブルを開く](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="5e365-251">入力する必要があります、新しいページが表示されます、**テーブル名**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="5e365-252">これは、以降の章で、アプリケーションでデータを指すために使用する名前です。</span><span class="sxs-lookup"><span data-stu-id="5e365-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="5e365-253">適切な名前を挿入し、をクリックして**OK**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-253">Insert an appropriate name and click **OK**.</span></span>

    ![新しいテーブルを作成します。](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="5e365-255">新しいテーブルが作成されたら、できなく内を確認する、 **Table service** (下部) のページ。</span><span class="sxs-lookup"><span data-stu-id="5e365-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![新しいテーブルの作成](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="5e365-257">第 5 章 - Visual Studio で Azure テーブルの完了</span><span class="sxs-lookup"><span data-stu-id="5e365-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="5e365-258">これで、 **Table service**ストレージ アカウントを設定したら、情報格納および取得するために使用するデータを追加する時間。</span><span class="sxs-lookup"><span data-stu-id="5e365-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="5e365-259">テーブルの編集を実行できます**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="5e365-260">開いている**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="5e365-261">メニューから、次のようにクリックします。**ビュー** > **Cloud Explorer**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![クラウド エクスプ ローラーを開く](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="5e365-263">**Cloud Explorer** (に患者、読み込み時間がかかる場合があります) がドッキングされている項目として開きます。</span><span class="sxs-lookup"><span data-stu-id="5e365-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="5e365-264">サブスクリプションの作成に使用する場合、*ストレージ アカウント*が表示されないできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5e365-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="5e365-265">Azure Portal を使用したものと同じアカウントにログインします。</span><span class="sxs-lookup"><span data-stu-id="5e365-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="5e365-266">(アカウント設定からフィルターを適用する必要があります)、アカウント管理ページからサブスクリプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="5e365-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![サブスクリプションが見つかりません](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="5e365-268">Azure クラウド サービスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="5e365-269">検索**ストレージ アカウント**アカウントを展開するの左側にある矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![ストレージ アカウント を開きます](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="5e365-271">展開されている場合、新しく作成した後**ストレージ アカウント**できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5e365-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="5e365-272">ストレージの左側にある矢印をクリックしを展開したら探します**テーブル**を表示する横の矢印をクリックします、**テーブル**最後の章で作成しました。</span><span class="sxs-lookup"><span data-stu-id="5e365-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="5e365-273">ダブルクリックして、**テーブル**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-273">Double click your **Table**.</span></span>

    ![シーン オブジェクト テーブルを開く](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="5e365-275">テーブルには、Visual Studio ウィンドウの中央に開かれます。</span><span class="sxs-lookup"><span data-stu-id="5e365-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="5e365-276">テーブル アイコンをクリックして、 **+** には、(+)。</span><span class="sxs-lookup"><span data-stu-id="5e365-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![新しいテーブルを追加します。](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="5e365-278">ウィンドウがするためのプロンプトを表示する表示*エンティティの追加*します。</span><span class="sxs-lookup"><span data-stu-id="5e365-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="5e365-279">いくつかのプロパティを持つ、合計で 3 つのエンティティを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="5e365-280">わかります*PartitionKey*と*RowKey*が既に提供されている、使用される場合は、テーブルでデータを検索します。</span><span class="sxs-lookup"><span data-stu-id="5e365-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![パーティションと行キー](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="5e365-282">更新プログラム、*値*の**PartitionKey**と**RowKey**次のように (各行プロパティを追加すると、これを行っても、RowKey を毎回インクリメント)。</span><span class="sxs-lookup"><span data-stu-id="5e365-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![正しい値を追加します。](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="5e365-284">クリックして**プロパティを追加**余分なデータ行を追加します。</span><span class="sxs-lookup"><span data-stu-id="5e365-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="5e365-285">空テーブルの最初に一致する、次の表。</span><span class="sxs-lookup"><span data-stu-id="5e365-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="5e365-286">クリックして**OK**は終了するとき。</span><span class="sxs-lookup"><span data-stu-id="5e365-286">Click **OK** when you are finished.</span></span>

    ![実行時に、[ok] をクリックします。](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="5e365-288">変更したことを確認、**型**の**X**、 **Y**、および**Z**、エントリを**二重**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="5e365-289">テーブル内のデータ行のようになりましたが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="5e365-290">をクリックして、 **+** (+) アイコンをもう一度別のエンティティを追加します。</span><span class="sxs-lookup"><span data-stu-id="5e365-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![最初の行](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="5e365-292">追加のプロパティを作成し、次に示すものと一致する新しいエンティティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="5e365-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![キューブを追加します。](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="5e365-294">別のエンティティを追加する最後の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="5e365-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="5e365-295">次のように、このエンティティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="5e365-295">Set the values for this entity to those shown below.</span></span>

    ![円柱を追加します。](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="5e365-297">テーブルには、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5e365-297">Your table should now look like the one below.</span></span>

    ![完全なテーブル](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="5e365-299">この章は完了しました。</span><span class="sxs-lookup"><span data-stu-id="5e365-299">You have completed this Chapter.</span></span> <span data-ttu-id="5e365-300">保存してください。</span><span class="sxs-lookup"><span data-stu-id="5e365-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="5e365-301">第 6 章 - Azure Function App を作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="5e365-302">更新するデスクトップ アプリケーションによって呼び出される、Azure Function App を作成、**テーブル**サービスし、の通知を送信、 **Notification Hub**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="5e365-303">最初に、必要なライブラリの読み込みに、Azure 関数を許可するファイルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="5e365-304">開いている**メモ帳**(Windows キーと型のメモ帳にキーを押します)。</span><span class="sxs-lookup"><span data-stu-id="5e365-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![メモ帳を開く](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="5e365-306">メモ帳を開く、そこに以下の JSON 構造を挿入します。</span><span class="sxs-lookup"><span data-stu-id="5e365-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="5e365-307">完了したら、としてデスクトップに保存**project.json**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="5e365-308">名前の付け方が正しいことが重要になります: はことを確認 **、.txt が付いていない**ファイル拡張子。</span><span class="sxs-lookup"><span data-stu-id="5e365-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="5e365-309">分かります NuGet を使用している場合、このファイルは、関数を使用するには、ライブラリを定義します。</span><span class="sxs-lookup"><span data-stu-id="5e365-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="5e365-310">[Azure ポータル](https://portal.azure.com) にログインします。</span><span class="sxs-lookup"><span data-stu-id="5e365-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="5e365-311">ログインした後は、をクリックして**新規**左上隅にある検索して**Function App**、キーを押して**Enter**。</span><span class="sxs-lookup"><span data-stu-id="5e365-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![関数アプリの検索](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="5e365-313">単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。</span><span class="sxs-lookup"><span data-stu-id="5e365-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="5e365-314">新しいページがの説明を入力、 **Function App**サービス。</span><span class="sxs-lookup"><span data-stu-id="5e365-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="5e365-315">このプロンプトの左下にある at、**作成**ボタンは、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![関数アプリ インスタンス](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="5e365-317">クリックすると**作成**次を入力します。</span><span class="sxs-lookup"><span data-stu-id="5e365-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="5e365-318">**アプリ名**、このサービス インスタンスのご希望の名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="5e365-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="5e365-319">選択、**サブスクリプション**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="5e365-320">作成時刻の場合、これは、最初に、適切な価格レベルを選択、 **Function App サービス**、free レベルを使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="5e365-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="5e365-321">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="5e365-322">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="5e365-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="5e365-323">勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。</span><span class="sxs-lookup"><span data-stu-id="5e365-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="5e365-324">詳細にする場合について、Azure リソース グループに従ってくださいこの[リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="5e365-325">**OS**、目的のプラットフォームであるために、Windows をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="5e365-326">選択、**ホスティング プラン**(このチュートリアルを使用して、**従量課金プラン**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="5e365-327">選択、**場所** **(前の手順で作成したストレージと同じ場所を選択)**</span><span class="sxs-lookup"><span data-stu-id="5e365-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="5e365-328">**ストレージ**セクション **、前の手順で作成したストレージ サービスを選択する必要があります**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="5e365-329">必要はありません*Application Insights*このアプリでため、自由に**オフ**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="5e365-330">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-330">Click **Create**.</span></span>

        ![新しいインスタンスを作成します。](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="5e365-332">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="5e365-333">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新しい通知](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="5e365-335">新しいサービス インスタンスを探索する通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="5e365-336">をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![リソースに移動します。](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="5e365-338">をクリックして、 **+** (隣にアイコン +)*関数*を*新規作成*です。</span><span class="sxs-lookup"><span data-stu-id="5e365-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![新しい関数を追加します。](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="5e365-340">中央のパネル内、**関数**作成ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="5e365-341">パネルの上半分に情報を無視し、をクリックして**カスタム関数**、(次に示すよう青い領域) の下の方に配置されています。</span><span class="sxs-lookup"><span data-stu-id="5e365-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![カスタム関数](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="5e365-343">ウィンドウ内で新しいページには、さまざまな関数の型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="5e365-344">紫の種類を表示するスクロールし、をクリックして**HTTP PUT**要素。</span><span class="sxs-lookup"><span data-stu-id="5e365-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![http のリンクを配置します。](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="5e365-346">さらに、リストをスクロールする必要があります、ページ (と、このイメージが正確に同じですが、Azure ポータルの更新が行われた場合) と呼ばれる要素を検索するただし、 *HTTP PUT*します。</span><span class="sxs-lookup"><span data-stu-id="5e365-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="5e365-347">**HTTP PUT**ウィンドウが表示されます (以下参照イメージの) 機能を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="5e365-348">**言語**C を選択して、ドロップダウン メニューを使用して\#します。</span><span class="sxs-lookup"><span data-stu-id="5e365-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="5e365-349">**名、** 適切な名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="5e365-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="5e365-350">**認証レベル**ドロップダウン メニューで、**関数**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="5e365-351">**テーブル名** セクションで、作成するために使用する正確な名前を使用する必要があります、**テーブル**以前 (同じ大文字と小文字) などのサービスです。</span><span class="sxs-lookup"><span data-stu-id="5e365-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="5e365-352">内で、**ストレージ アカウント接続**セクションし、ドロップダウン メニューを使用して、そこから、ストレージ アカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="5e365-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="5e365-353">をクリックしない場合、**新規**と共に、ストレージ アカウントが表示されるはずのもう 1 つのパネルを表示する、セクション タイトルのハイパーリンクです。</span><span class="sxs-lookup"><span data-stu-id="5e365-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![新しい記憶域](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="5e365-355">クリックして**作成**設定が正常に更新されていることの通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![関数を作成します。](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="5e365-357">クリックすると**作成**関数のエディターにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="5e365-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![関数コードを更新します。](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="5e365-359">関数エディター (関数のコードを置き換える) には、次のコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="5e365-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="5e365-360">含まれるライブラリを使用して、関数が受け取った移動されたオブジェクトの場所と名前、Unity シーンで (として、C#と呼ばれるオブジェクト**UnityGameObject**)。</span><span class="sxs-lookup"><span data-stu-id="5e365-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="5e365-361">このオブジェクトは、作成されたテーブル内のオブジェクトのパラメーターを更新する、使用されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="5e365-362">次は、関数を作成した通知ハブ サービスにサブスクライブしているすべてのアプリケーションに通知する呼び出しを実行します。</span><span class="sxs-lookup"><span data-stu-id="5e365-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="5e365-363">コードの場所で、次のようにクリックします。**保存**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="5e365-364">次に、クリックして、 **\<** (矢印) アイコンをページの右側にあります。</span><span class="sxs-lookup"><span data-stu-id="5e365-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![開いているアップロード パネル](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="5e365-366">パネルは、右からにスライドします。</span><span class="sxs-lookup"><span data-stu-id="5e365-366">A panel will slide in from the right.</span></span> <span data-ttu-id="5e365-367">そのパネル で、**アップロード**、され、ファイル ブラウザーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="5e365-368">、に移動し、クリックすると、、 **project.json**ファイルで、で作成した**メモ帳**以前は、順にクリックします、**オープン**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="5e365-369">このファイルは、関数が使用するライブラリを定義します。</span><span class="sxs-lookup"><span data-stu-id="5e365-369">This file defines the libraries that your function will use.</span></span>

    ![json をアップロードします。](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="5e365-371">ファイルがアップロードされると、右側のパネルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="5e365-372">内で開くをクリックすると、**関数**エディター。</span><span class="sxs-lookup"><span data-stu-id="5e365-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="5e365-373">表示する必要があります**まったく**(手順 23) の下の [次へ] のイメージと同じです。</span><span class="sxs-lookup"><span data-stu-id="5e365-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="5e365-374">その後、左側のパネルで、下にある**関数**、 をクリックして、**統合**リンク。</span><span class="sxs-lookup"><span data-stu-id="5e365-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![関数を統合します。](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="5e365-376">画面右隅で、次のページで次のようにクリックします。**高度なエディター** (以下のとおり)。</span><span class="sxs-lookup"><span data-stu-id="5e365-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![詳細エディターの起動](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="5e365-378">A **function.json**ファイルは次のコード スニペットを置換する必要がある中央のパネルで開けません。</span><span class="sxs-lookup"><span data-stu-id="5e365-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="5e365-379">これは、関数を作成して、パラメーターを定義します。 関数に渡されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-379">This defines the function you are building and the parameters passed into the function.</span></span>

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. <span data-ttu-id="5e365-380">エディターは、次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="5e365-380">Your editor should now look like the image below:</span></span>

    ![標準のエディターに戻る](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="5e365-382">挿入した入力パラメーターは、テーブルおよびストレージの詳細一致しなくなり、お客様の情報に更新する必要がありますのでお気付きです。</span><span class="sxs-lookup"><span data-stu-id="5e365-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="5e365-383">**これは、ここは実行しないで**を次に説明しました。</span><span class="sxs-lookup"><span data-stu-id="5e365-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="5e365-384">クリックするだけで、**標準エディター**戻るには、ページの右上隅にあるリンクです。</span><span class="sxs-lookup"><span data-stu-id="5e365-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="5e365-385">戻り、**標準エディター**、] をクリックして**Azure Table Storage (テーブル)** [**入力**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![テーブルの入力](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="5e365-387">次の一致することを確認 **、** についてと異なる場合があります (は、イメージを次の手順を以下)。</span><span class="sxs-lookup"><span data-stu-id="5e365-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="5e365-388">**テーブル名**: Azure Storage、Table サービス内で作成したテーブルの名前。</span><span class="sxs-lookup"><span data-stu-id="5e365-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="5e365-389">**ストレージ アカウント接続:** クリックして**新しい**、と共にドロップダウン メニューで、表示されると、ウィンドウの右側にパネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![新しい記憶域](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="5e365-391">選択、**ストレージ アカウント**、ホストに先ほど作成した、**関数アプリです。**</span><span class="sxs-lookup"><span data-stu-id="5e365-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="5e365-392">表示になります、**ストレージ アカウント**接続値が作成されました。</span><span class="sxs-lookup"><span data-stu-id="5e365-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="5e365-393">キーを押して確認**保存**が完了します。</span><span class="sxs-lookup"><span data-stu-id="5e365-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="5e365-394">**入力**ページに一致する必要があります、以下では、示す **、** 情報。</span><span class="sxs-lookup"><span data-stu-id="5e365-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![入力を完了します。](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="5e365-396">次に、クリックして**Azure Notification Hub (通知)** -**出力**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="5e365-397">次が一致することを確認 **、** についてと異なる場合があります (下図を次の手順がある)。</span><span class="sxs-lookup"><span data-stu-id="5e365-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="5e365-398">**通知ハブの名前**: これは、名前の**Notification Hub**以前に作成したサービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="5e365-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="5e365-399">**Notification Hubs の名前空間の接続**: クリックして**新しい**、と共にドロップダウン メニューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![出力を確認してください。](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="5e365-401">**接続**ポップアップが表示されます (下図を参照) を選択する必要がある、 **Namespace**の**Notification Hub**、以前に設定します。</span><span class="sxs-lookup"><span data-stu-id="5e365-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="5e365-402">選択、 **Notification Hub**中間のドロップダウン メニューから名前。</span><span class="sxs-lookup"><span data-stu-id="5e365-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="5e365-403">設定、**ポリシー**ドロップダウン メニューを**DefaultFullSharedAccessSignature**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="5e365-404">をクリックして、**選択**戻るボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-404">Click the **Select** button to go back.</span></span>

        ![更新プログラムを出力します。](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="5e365-406">**出力**ページに一致する必要があります、以下では、ですが、 **、** 情報代わりにします。</span><span class="sxs-lookup"><span data-stu-id="5e365-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="5e365-407">キーを押して確認**保存**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="5e365-408">*通知ハブの名前を直接編集しないでください*(する必要がありますすべてこれを使用して、**詳細エディター**正しく前の手順に従っていれば、します。</span><span class="sxs-lookup"><span data-stu-id="5e365-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![完全な出力](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="5e365-410">この時点では、動作していることを確認する、関数をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="5e365-411">これには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="5e365-411">To do this:</span></span> 

    1. <span data-ttu-id="5e365-412">もう一度、関数のページに移動します。</span><span class="sxs-lookup"><span data-stu-id="5e365-412">Navigate to the function page once more:</span></span>

        ![完全な出力](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="5e365-414">関数 ページで、戻る をクリックして、**テスト** タブを開くには、ページの一番右側にある、*テスト*ブレード。</span><span class="sxs-lookup"><span data-stu-id="5e365-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![完全な出力](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="5e365-416">内で、**要求本文**貼り付け ブレードのテキスト ボックスに、次のコード。</span><span class="sxs-lookup"><span data-stu-id="5e365-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. <span data-ttu-id="5e365-417">テストのコードの場所で、をクリックして、**実行**ボタン右、下で、テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="5e365-418">テストの出力ログは、関数コードの下のコンソール領域に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![完全な出力](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="5e365-420">上記のテストに失敗した場合は設定が必要な二重チェックが正確には、上記の手順を実行したことを特に、内で、**パネルを統合**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="5e365-421">第 7 章 – デスクトップの Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="5e365-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e365-422">デスクトップ アプリケーションを作成するようになりました**されません**Unity エディターで作業します。</span><span class="sxs-lookup"><span data-stu-id="5e365-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="5e365-423">次の Visual Studio を使用して、アプリケーション (または、デプロイされたアプリケーション) の構成エディター以外では実行が必要です。</span><span class="sxs-lookup"><span data-stu-id="5e365-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="5e365-424">次のコード例が Unity を使用した開発と複合現実は、一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。</span><span class="sxs-lookup"><span data-stu-id="5e365-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="5e365-425">設定して、mixed reality イマーシブ ヘッドセットをテストします。</span><span class="sxs-lookup"><span data-stu-id="5e365-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="5e365-426">**いない**このコースのモーションのコント ローラーが必要です。</span><span class="sxs-lookup"><span data-stu-id="5e365-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="5e365-427">イマーシブ ヘッドセットの設定のサポートが必要な場合に従ってくださいこの[Windows Mixed Reality を設定する方法についてのリンク](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="5e365-428">開いている**Unity**クリック**新規**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-428">Open **Unity** and click **New**.</span></span>

    ![新しい unity プロジェクト](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="5e365-430">挿入、Unity プロジェクト名を指定する必要がある**UnityDesktopNotifHub**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="5e365-431">必ず、プロジェクトの種類に設定されて**3D**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="5e365-432">設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。</span><span class="sxs-lookup"><span data-stu-id="5e365-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="5e365-433">をクリックし、**プロジェクトの作成**です。</span><span class="sxs-lookup"><span data-stu-id="5e365-433">Then, click **Create project**.</span></span>

    ![プロジェクトを作成します。](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="5e365-435">既定値を確認する必要が開いている Unity、 **スクリプト エディター** に設定されている **Visual Studio** します。</span><span class="sxs-lookup"><span data-stu-id="5e365-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="5e365-436">移動して**編集** > **設定**し、新しいウィンドウに移動**外部ツール**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="5e365-437">変更 **External Script Editor** に **Visual Studio 2017** します。</span><span class="sxs-lookup"><span data-stu-id="5e365-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="5e365-438">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="5e365-438">Close the **Preferences** window.</span></span>

    ![VS tools の外部セット](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="5e365-440">次に移動**ファイル** > **Build Settings**選択**ユニバーサル Windows プラットフォーム**、をクリックして、**スイッチ プラットフォーム**選択内容を適用するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![プラットフォームを切り替える](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="5e365-442">**ファイル** > **Build Settings**、ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="5e365-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="5e365-443">**デバイスを対象に**に設定されている**任意のデバイス**</span><span class="sxs-lookup"><span data-stu-id="5e365-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="5e365-444">このアプリケーションがありますが、デスクトップようにする必要があります**任意のデバイス**</span><span class="sxs-lookup"><span data-stu-id="5e365-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="5e365-445">**ビルドの種類**に設定されている**D3D**</span><span class="sxs-lookup"><span data-stu-id="5e365-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="5e365-446">**SDK**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="5e365-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="5e365-447">**Visual Studio バージョン**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="5e365-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="5e365-448">**ビルドおよび実行**に設定されている**ローカル マシン**</span><span class="sxs-lookup"><span data-stu-id="5e365-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="5e365-449">ここでは、シーンを保存およびビルドに追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5e365-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="5e365-450">これには、選択**開くシーンを追加**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="5e365-451">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-451">A save window will appear.</span></span>

            ![開いているシーンを追加します。](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="5e365-453">新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![シーンの新しいフォルダー](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="5e365-455">新たに作成した開く**シーン**フォルダー、し、**ファイル名:** テキスト フィールドに「 **NH\_デスクトップ\_シーン**、キーを押します**保存**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![新しい NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="5e365-457">設定に残っている**Build Settings**、ここでは既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="5e365-458">同じウィンドウをクリックして、**プレーヤー設定**ボタン領域に関連するパネルが開き、**インスペクター**が配置されています。</span><span class="sxs-lookup"><span data-stu-id="5e365-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="5e365-459">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="5e365-460">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="5e365-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="5e365-461">**ランタイム バージョンをスクリプト**べき**試験的 (.NET 4.6 Equivalent)**</span><span class="sxs-lookup"><span data-stu-id="5e365-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="5e365-462">**バックエンドの scripting**べき **.NET**</span><span class="sxs-lookup"><span data-stu-id="5e365-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="5e365-463">**API の互換性レベル**べき **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="5e365-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![net 4.6 のバージョン](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="5e365-465">内で、**発行の設定**] タブの [**機能**、確認してください。</span><span class="sxs-lookup"><span data-stu-id="5e365-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="5e365-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="5e365-466">**InternetClient**</span></span>

            ![ティックのインターネット クライアント](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="5e365-468">戻り**Build Settings** *Unity C\#プロジェクト*が不要になったグレー; これの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="5e365-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="5e365-469">閉じる、 **Build Settings**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="5e365-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="5e365-470">シーンとプロジェクトを保存**ファイル** > **シーンを保存/ファイル** > **プロジェクトを保存**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="5e365-471">スキップする場合、 *Unity を設定する*このプロジェクト (デスクトップ アプリ) のコンポーネントのコードにまっすぐコンティニュし、自由に[ダウンロードこの .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage)、としてプロジェクトにインポート、 [**カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="5e365-472">スクリプト コンポーネントを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="5e365-473">第 8 章 - Unity で、Dll のインポート</span><span class="sxs-lookup"><span data-stu-id="5e365-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="5e365-474">Unity の Azure ストレージを使用する (それ自体を活用して、.Net SDK for Azure)。</span><span class="sxs-lookup"><span data-stu-id="5e365-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="5e365-475">詳細についてはこの後に[Unity 用の Azure Storage のリンク](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="5e365-476">インポート後に再構成するプラグインを必要とする Unity での既知の問題は現在します。</span><span class="sxs-lookup"><span data-stu-id="5e365-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="5e365-477">バグが解決された後、次の手順 (このセクションでは 4 ~ 7) は必要に不要になった。</span><span class="sxs-lookup"><span data-stu-id="5e365-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="5e365-478">独自のプロジェクトに SDK をインポートすることを最新バージョンをダウンロードしていることを確認して[ **.unitypackage** ](https://aka.ms/azstorage-unitysdk) GitHub から。</span><span class="sxs-lookup"><span data-stu-id="5e365-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="5e365-479">次に、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="5e365-479">Then, do the following:</span></span>

1.  <span data-ttu-id="5e365-480">追加、 **.unitypackage**に Unity を使用して、**資産\>パッケージのインポート\>カスタム パッケージ**メニュー オプション。</span><span class="sxs-lookup"><span data-stu-id="5e365-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="5e365-481">**Unity パッケージのインポート**ポップアップ、選択できることの下のすべてのボックス \* \**プラグイン* \> \* ストレージ \* \* \*。</span><span class="sxs-lookup"><span data-stu-id="5e365-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="5e365-482">このコースの必要がないと、その他のすべてをオフにします。</span><span class="sxs-lookup"><span data-stu-id="5e365-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![パッケージへのインポートします。](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="5e365-484">をクリックして、***インポート***をプロジェクトにアイテムを追加するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="5e365-485">移動して、**ストレージ**の下のフォルダー**プラグイン**プロジェクトを表示し、次のプラグインを選択*のみ*:</span><span class="sxs-lookup"><span data-stu-id="5e365-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="5e365-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="5e365-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="5e365-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="5e365-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="5e365-488">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="5e365-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="5e365-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="5e365-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="5e365-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="5e365-490">System.Spatial</span></span>

![任意のプラットフォームをオフにします。](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="5e365-492">*これら特定のプラグイン*選択すると、**をオフに** **Any プラットフォーム**と**をオフに** **WSAPlayer**クリックして**適用**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![プラットフォームの dll を適用します。](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="5e365-494">Unity エディターでのみ使用するこれらの特定のプラグインをマークするされます。</span><span class="sxs-lookup"><span data-stu-id="5e365-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="5e365-495">WSA フォルダー Unity からプロジェクトはエクスポート後に使用される同じプラグインのさまざまなバージョンがあるためにです。</span><span class="sxs-lookup"><span data-stu-id="5e365-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="5e365-496">**ストレージ**プラグイン フォルダーのみを選択します。</span><span class="sxs-lookup"><span data-stu-id="5e365-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="5e365-497">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="5e365-497">Microsoft.Data.Services.Client</span></span>

        ![dll のセットを処理しません。](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="5e365-499">チェック、**しないプロセス**ボックス**プラットフォームの設定** をクリック***適用***します。</span><span class="sxs-lookup"><span data-stu-id="5e365-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![処理は適用されません。](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="5e365-501">私たちはマークするこのプラグイン「プロセスはありません」Unity アセンブリのパッチャがあるこのプラグインを処理できないのためです。</span><span class="sxs-lookup"><span data-stu-id="5e365-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="5e365-502">このプラグインは処理されていない場合でも機能します。</span><span class="sxs-lookup"><span data-stu-id="5e365-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="5e365-503">章 9 - デスクトップの Unity プロジェクトで TableToScene クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="5e365-504">このアプリケーションを実行するコードを含むスクリプトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="5e365-505">最初のスクリプトを作成する必要があるは**TableToScene**は責任を負います。</span><span class="sxs-lookup"><span data-stu-id="5e365-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="5e365-506">Azure テーブル内のエンティティを読み取っています。</span><span class="sxs-lookup"><span data-stu-id="5e365-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="5e365-507">テーブルのデータを使用して生成するには、オブジェクトを判別し、どの位置。</span><span class="sxs-lookup"><span data-stu-id="5e365-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="5e365-508">2 番目のスクリプトを作成する必要があるは**CloudScene**は責任を負います。</span><span class="sxs-lookup"><span data-stu-id="5e365-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="5e365-509">ユーザーが、シーンを基準としてオブジェクトをドラッグできるようにする、左クリック イベントを登録しています。</span><span class="sxs-lookup"><span data-stu-id="5e365-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="5e365-510">この Unity シーンからオブジェクト データをシリアル化し、Azure 関数アプリに送信します。</span><span class="sxs-lookup"><span data-stu-id="5e365-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="5e365-511">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-511">To create this class:</span></span>

1.  <span data-ttu-id="5e365-512">右クリックし、**資産**フォルダーは、[プロジェクト] パネルにある**作成** > **フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="5e365-513">フォルダーの名前**スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-513">Name the folder **Scripts**.</span></span>

    ![scripts フォルダーを作成します。](images/AzureLabs-Lab8-66.png)

    ![2 の scripts フォルダーを作成します。](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="5e365-516">先ほど作成した、開くフォルダーをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="5e365-517">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="5e365-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="5e365-518">スクリプトの名前**TableToScene**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="5e365-519">![新しい c# スクリプト](images/AzureLabs-Lab8-68.png)
    ![TableToScene 名前の変更](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="5e365-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="5e365-520">Visual Studio 2017 で開くスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="5e365-521">次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="5e365-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="5e365-522">クラス内では、次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="5e365-522">Within the class, insert the following variables:</span></span>

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > <span data-ttu-id="5e365-523">代替、 **accountName**を Azure ストレージ サービスの名前と値および**accountKey** (「次の図) Azure Portal で、Azure ストレージ サービスで見つかったキー値を持つ値。</span><span class="sxs-lookup"><span data-stu-id="5e365-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![アカウント キーのフェッチ](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="5e365-525">ここで追加、 **Start()** と**Awake()** クラスを初期化するメソッド。</span><span class="sxs-lookup"><span data-stu-id="5e365-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  <span data-ttu-id="5e365-526">内で、 **TableToScene**クラスでは、Azure テーブルから値を取得し、シーン内の適切なプリミティブを生成するために使用するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="5e365-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  <span data-ttu-id="5e365-527">外側、 **TableToScene**クラス、および逆シリアル化するアプリケーションによって使用されるクラスを定義する必要があります、**テーブル エンティティ**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. <span data-ttu-id="5e365-528">必ず**保存**Unity エディターに戻る前にします。</span><span class="sxs-lookup"><span data-stu-id="5e365-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="5e365-529">をクリックして、 **Main Camera**から、**階層** パネルにそのプロパティが表示されるように、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="5e365-530">**スクリプト**フォルダーを開き、スクリプトを選択する**TableToScene ファイル**上にドラッグし、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="5e365-531">結果は、以下のとおり。</span><span class="sxs-lookup"><span data-stu-id="5e365-531">The result should be as below:</span></span>

    ![メイン カメラにスクリプトを追加します。](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="5e365-533">章 10 - デスクトップの Unity プロジェクトで CloudScene クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="5e365-534">2 番目のスクリプトを作成する必要があるは**CloudScene**は責任を負います。</span><span class="sxs-lookup"><span data-stu-id="5e365-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="5e365-535">ユーザーが、シーンを基準としてオブジェクトをドラッグできるようにする、左クリック イベントを登録しています。</span><span class="sxs-lookup"><span data-stu-id="5e365-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="5e365-536">この Unity シーンからオブジェクト データをシリアル化し、Azure 関数アプリに送信します。</span><span class="sxs-lookup"><span data-stu-id="5e365-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="5e365-537">2 番目のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e365-537">To create the second script:</span></span>

1.  <span data-ttu-id="5e365-538">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成**、 **C\#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="5e365-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="5e365-539">スクリプトの名前**CloudScene**</span><span class="sxs-lookup"><span data-stu-id="5e365-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="5e365-540">![新しい c# スクリプト](images/AzureLabs-Lab8-72.png)
    ![CloudScene の名前を変更](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="5e365-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="5e365-541">次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="5e365-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="5e365-542">次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="5e365-542">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  <span data-ttu-id="5e365-543">代替、 **azureFunctionEndpoint** Azure 関数アプリの URL を次の図に示すように、Azure Portal で、Azure Function App サービスで見つかった値。</span><span class="sxs-lookup"><span data-stu-id="5e365-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![関数の URL を取得します。](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="5e365-545">ここで追加、 **Start()** と**Awake()** クラスを初期化するメソッド。</span><span class="sxs-lookup"><span data-stu-id="5e365-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  <span data-ttu-id="5e365-546">内で、 **Update()** メソッド、ドラッグで、シーンの Gameobject を移動はさらに、マウス入力を検出する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5e365-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="5e365-547">ユーザーがドラッグし、オブジェクトの削除された場合、そのメソッド名とオブジェクトの座標を渡すは**UpdateCloudScene()** 、Azure テーブルおよびトリガーを更新する Azure Function App サービスを呼び出すが、通知します。</span><span class="sxs-lookup"><span data-stu-id="5e365-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  <span data-ttu-id="5e365-548">ここで追加、 **UpdateCloudScene()** 次に示すように、メソッド。</span><span class="sxs-lookup"><span data-stu-id="5e365-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  <span data-ttu-id="5e365-549">コードを保存し、Unity に戻る</span><span class="sxs-lookup"><span data-stu-id="5e365-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="5e365-550">ドラッグ、 **CloudScene**にスクリプト、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="5e365-551">をクリックして、 **Main Camera**から、**階層** パネルにそのプロパティが表示されるように、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="5e365-552">**スクリプト**フォルダーを開き、選択、 **CloudScene**スクリプトを作成し、上にドラッグ、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="5e365-553">結果は、以下のとおり。</span><span class="sxs-lookup"><span data-stu-id="5e365-553">The result should be as below:</span></span>

        > ![クラウドのスクリプトをメイン カメラにドラッグします。](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="5e365-555">第 11 章 – デスクトップ、UWP プロジェクトのビルド</span><span class="sxs-lookup"><span data-stu-id="5e365-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="5e365-556">このプロジェクトの Unity セクションに必要なものすべてが完了しましたようになりました。</span><span class="sxs-lookup"><span data-stu-id="5e365-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="5e365-557">移動します**ビルド設定**(**ファイル** > **ビルド設定**)。</span><span class="sxs-lookup"><span data-stu-id="5e365-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="5e365-558">**Build Settings**ウィンドウで、をクリックして**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-558">From the **Build Settings** window, click **Build**.</span></span>

    ![プロジェクトをビルドします。](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="5e365-560">A**ファイル エクスプ ローラー**ビルドする場所の入力を求めるウィンドウがポップアップします。</span><span class="sxs-lookup"><span data-stu-id="5e365-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="5e365-561">新しいフォルダーを作成 (をクリックして**新しいフォルダー**左上隅にある)、名前を付けます**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![ビルド用の新しいフォルダー](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="5e365-563">開き、新しい**ビルド**フォルダー、別のフォルダーを作成し、(を使用して**新しいフォルダー**もう一度)、名前を付けます**NH\_デスクトップ\_アプリ**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![フォルダー名 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="5e365-565">**NH\_デスクトップ\_アプリ**選択します。</span><span class="sxs-lookup"><span data-stu-id="5e365-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="5e365-566">クリックして**フォルダーの選択**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-566">click **Select Folder**.</span></span> <span data-ttu-id="5e365-567">プロジェクトは、ビルドを 1 分程度かかります。</span><span class="sxs-lookup"><span data-stu-id="5e365-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="5e365-568">次のビルド、**ファイル エクスプ ローラー**新しいプロジェクトの場所が示されますが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="5e365-569">ただし、他を作成する必要があると Unity プロジェクトの最初に、次のいくつかの章を開くと、する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5e365-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="5e365-570">第 12 章 - 混合現実の Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="5e365-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="5e365-571">次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。</span><span class="sxs-lookup"><span data-stu-id="5e365-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="5e365-572">開いている**Unity**クリック**新規**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-572">Open **Unity** and click **New**.</span></span>

    ![新しい unity プロジェクト](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="5e365-574">Unity プロジェクト名を指定する必要がありますこれで挿入**UnityMRNotifHub**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="5e365-575">必ず、プロジェクトの種類に設定されて**3D**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="5e365-576">設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。</span><span class="sxs-lookup"><span data-stu-id="5e365-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="5e365-577">をクリックし、**プロジェクトの作成**です。</span><span class="sxs-lookup"><span data-stu-id="5e365-577">Then, click **Create project**.</span></span>

    ![名前 UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="5e365-579">既定値を確認する必要が開いている Unity、 **スクリプト エディター** に設定されている **Visual Studio** します。</span><span class="sxs-lookup"><span data-stu-id="5e365-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="5e365-580">移動して**編集** > **設定**し、新しいウィンドウに移動**外部ツール**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="5e365-581">変更 **External Script Editor** に **Visual Studio 2017** します。</span><span class="sxs-lookup"><span data-stu-id="5e365-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="5e365-582">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="5e365-582">Close the **Preferences** window.</span></span>

    ![VS セット外部エディター](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="5e365-584">次に移動**ファイル** > **Build Settings**にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして、**プラットフォームの切り替え**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![UWP にプラットフォームを切り替える](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="5e365-586">移動して**ファイル** > **Build Settings**ことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5e365-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="5e365-587">**デバイスを対象に**に設定されている**任意のデバイス**</span><span class="sxs-lookup"><span data-stu-id="5e365-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="5e365-588">Microsoft HoloLens、設定**ターゲット デバイス**に*HoloLens*します。</span><span class="sxs-lookup"><span data-stu-id="5e365-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="5e365-589">**ビルドの種類**に設定されている**D3D**</span><span class="sxs-lookup"><span data-stu-id="5e365-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="5e365-590">**SDK**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="5e365-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="5e365-591">**Visual Studio バージョン**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="5e365-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="5e365-592">**ビルドおよび実行**に設定されている**ローカル マシン**</span><span class="sxs-lookup"><span data-stu-id="5e365-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="5e365-593">ここでは、シーンを保存およびビルドに追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5e365-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="5e365-594">これには、選択**開くシーンを追加**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="5e365-595">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-595">A save window will appear.</span></span>

            ![開いているシーンを追加します。](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="5e365-597">新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![シーンの新しいフォルダー](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="5e365-599">新たに作成した開く**シーン**フォルダー、し、**ファイル名:** テキスト フィールドに「 **NH\_MR\_シーン**、キーを押します**保存**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![新しいシーン - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="5e365-601">設定に残っている**Build Settings**、ここでは既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="5e365-602">同じウィンドウをクリックして、**プレーヤー設定**ボタン領域に関連するパネルが開き、**インスペクター**が配置されています。</span><span class="sxs-lookup"><span data-stu-id="5e365-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![プレーヤー設定を開く](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="5e365-604">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="5e365-605">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="5e365-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="5e365-606">**ランタイム バージョンをスクリプト**べき**試験的**(.NET 4.6 Equivalent)</span><span class="sxs-lookup"><span data-stu-id="5e365-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="5e365-607">**バックエンドの scripting**べき ***.NET***</span><span class="sxs-lookup"><span data-stu-id="5e365-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="5e365-608">**API の互換性レベル**べき **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="5e365-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![api の互換性](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="5e365-610">パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます</span><span class="sxs-lookup"><span data-stu-id="5e365-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![xr の設定の更新](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="5e365-612">内で、**公開設定**] タブの [**機能**いったい。</span><span class="sxs-lookup"><span data-stu-id="5e365-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="5e365-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="5e365-613">**InternetClient**</span></span>           

            ![ティックのインターネット クライアント](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="5e365-615">戻り**Build Settings**、 **UnityC#プロジェクト**が不要になったグレー: この横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="5e365-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="5e365-616">これらの変更完了ビルド設定ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="5e365-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="5e365-617">シーンとプロジェクトを保存**ファイル** > **シーンを保存/ファイル** > **プロジェクトを保存**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="5e365-618">スキップする場合、 *Unity を設定する*コンポーネント (複合現実アプリ)、このプロジェクトのコードにまっすぐコンティニュし、自由に[ダウンロードこの .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)、としてプロジェクトにインポート[**カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[14 章](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="5e365-619">スクリプト コンポーネントを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="5e365-620">第 13 章 - 複合現実の Unity プロジェクトで、Dll のインポート</span><span class="sxs-lookup"><span data-stu-id="5e365-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="5e365-621">(Azure 用 .Net SDK を使用) する Unity ライブラリの Azure Storage が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="5e365-622">これに従ってください[Unity を使用した Azure Storage を使用する方法についてのリンク](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="5e365-623">インポート後に再構成するプラグインを必要とする Unity での既知の問題は現在します。</span><span class="sxs-lookup"><span data-stu-id="5e365-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="5e365-624">バグが解決された後、次の手順 (このセクションでは 4 ~ 7) は必要に不要になった。</span><span class="sxs-lookup"><span data-stu-id="5e365-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="5e365-625">独自のプロジェクトに SDK をインポートすることを最新バージョンをダウンロードしていることを確認して[.unitypackage](https://aka.ms/azstorage-unitysdk)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="5e365-626">次に、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="5e365-626">Then, do the following:</span></span>

1.  <span data-ttu-id="5e365-627">Unity を使用して、上記でダウンロードした .unitypackage を追加、**資産** > **パッケージのインポート** > **カスタム パッケージ**メニュー オプション.</span><span class="sxs-lookup"><span data-stu-id="5e365-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="5e365-628">**Unity パッケージのインポート**ポップアップ、選択できることの下のすべてのボックス**プラグイン** > **ストレージ**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![パッケージのインポート](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="5e365-630">をクリックして、**インポート**をプロジェクトにアイテムを追加するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="5e365-631">移動して、**ストレージ**の下のフォルダー**プラグイン**プロジェクトを表示し、次のプラグインを選択*のみ*:</span><span class="sxs-lookup"><span data-stu-id="5e365-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="5e365-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="5e365-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="5e365-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="5e365-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="5e365-634">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="5e365-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="5e365-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="5e365-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="5e365-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="5e365-636">System.Spatial</span></span>

    ![プラグインを選択します。](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="5e365-638">*これら特定のプラグイン*選択すると、**をオフに** **Any プラットフォーム**と**をオフに** **WSAPlayer**クリックして**適用**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![プラットフォームの変更を適用します。](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="5e365-640">Unity エディターでのみ使用するこれらの特定のプラグインをマークすることができます。</span><span class="sxs-lookup"><span data-stu-id="5e365-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="5e365-641">WSA フォルダー Unity からプロジェクトはエクスポート後に使用される同じプラグインのさまざまなバージョンがあるためにです。</span><span class="sxs-lookup"><span data-stu-id="5e365-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="5e365-642">**ストレージ**プラグイン フォルダーのみを選択します。</span><span class="sxs-lookup"><span data-stu-id="5e365-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="5e365-643">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="5e365-643">Microsoft.Data.Services.Client</span></span>

        ![data services クライアントを選択します。](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="5e365-645">チェック、**しないプロセス**ボックス**プラットフォームの設定** をクリック**適用**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![処理はありません。](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="5e365-647">マークしているこのプラグイン「プロセスはありません」Unity アセンブリのパッチャがあるこのプラグインを処理できないのためです。</span><span class="sxs-lookup"><span data-stu-id="5e365-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="5e365-648">このプラグインは、処理されていない場合でも機能します。</span><span class="sxs-lookup"><span data-stu-id="5e365-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="5e365-649">第 14 章 – TableToScene クラスの複合現実の Unity プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="5e365-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="5e365-650">**TableToScene**クラスで説明されているものと同じ[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="5e365-651">同じクラスを作成で Unity プロジェクトの同様の手順が説明されている複合現実で[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)します。</span><span class="sxs-lookup"><span data-stu-id="5e365-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="5e365-652">この章では、両方が完了したら、 **Unity プロジェクト**このクラスの Main Camera を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="5e365-653">第 15 章「Mixed Reality Unity プロジェクトで NotificationReceiver クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="5e365-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="5e365-654">2 番目のスクリプトを作成する必要があるは**NotificationReceiver**は責任を負います。</span><span class="sxs-lookup"><span data-stu-id="5e365-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="5e365-655">アプリの初期化時、通知ハブに登録します。</span><span class="sxs-lookup"><span data-stu-id="5e365-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="5e365-656">通知ハブから通知をリッスンします。</span><span class="sxs-lookup"><span data-stu-id="5e365-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="5e365-657">受信した通知からオブジェクト データを逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="5e365-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="5e365-658">逆シリアル化されたデータに基づく、シーン内の Gameobject に移動します。</span><span class="sxs-lookup"><span data-stu-id="5e365-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="5e365-659">作成する、 **NotificationReceiver**スクリプト。</span><span class="sxs-lookup"><span data-stu-id="5e365-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="5e365-660">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成**、 **C\#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="5e365-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="5e365-661">スクリプトの名前**NotificationReceiver**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="5e365-662">![新しい c# スクリプト作成](images/AzureLabs-Lab8-95.png)
    ![NotificationReceiver という名前を付けます](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="5e365-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="5e365-663">これを開くためのスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="5e365-664">次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="5e365-664">Add the following namespaces:</span></span>

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  <span data-ttu-id="5e365-665">次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="5e365-665">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  <span data-ttu-id="5e365-666">代替、 **hubName**を Notification Hubs サービス名に、値と**hubListenEndpoint**アクセス ポリシー タブで、Azure Notification Hubs のサービスで見つかったエンドポイント値と、Azure Portal (下図を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="5e365-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![通知ハブのポリシー エンドポイントを挿入します。](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="5e365-668">ここで追加、 **Start()** と**Awake()** クラスを初期化するメソッド。</span><span class="sxs-lookup"><span data-stu-id="5e365-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  <span data-ttu-id="5e365-669">追加、 **WaitForNotification**アプリは、メイン スレッドと競合せず、通知ハブのライブラリからの通知を受信できるようにするメソッド。</span><span class="sxs-lookup"><span data-stu-id="5e365-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  <span data-ttu-id="5e365-670">次のメソッドでは、 **InitNotificationAsync()** 、通知ハブのサービスの初期化時にアプリケーションを登録します。</span><span class="sxs-lookup"><span data-stu-id="5e365-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="5e365-671">Unity では、プロジェクトをビルドできないため、コードをコメント アウトします。</span><span class="sxs-lookup"><span data-stu-id="5e365-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="5e365-672">Visual Studio で Azure メッセージング Nuget パッケージをインポートするときに、コメントが削除されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  <span data-ttu-id="5e365-673">次のハンドラー**チャネル\_PushNotificationReceived()** 通知が受信されるたびにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="5e365-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="5e365-674">デスクトップ アプリケーションに移動された Azure テーブル エンティティになるし、MR シーン内の同じ位置に対応する GameObject を移動すると、通知を逆シリアル化にされます。</span><span class="sxs-lookup"><span data-stu-id="5e365-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="5e365-675">コードは、Visual Studio 内で、Nuget パッケージ マネージャーを使用して、Unity プロジェクトをビルドした後は、追加、Azure メッセージング ライブラリを参照しているため、コードをコメント アウトします。</span><span class="sxs-lookup"><span data-stu-id="5e365-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="5e365-676">そのため、Unity プロジェクトされませんをビルドすることがコメント アウトされていない場合です。注意する必要があります、プロジェクトをビルドし、Unity に戻りたいが必要に**再びコメント化**コード。</span><span class="sxs-lookup"><span data-stu-id="5e365-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. <span data-ttu-id="5e365-677">Unity エディターに戻る前に、変更を保存してください。</span><span class="sxs-lookup"><span data-stu-id="5e365-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="5e365-678">をクリックして、 **Main Camera**から、**階層** パネルにそのプロパティが表示されるように、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="5e365-679">**スクリプト**フォルダーを開き、選択、 **NotificationReceiver**スクリプトを作成し、上にドラッグ、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="5e365-680">結果は、以下のとおり。</span><span class="sxs-lookup"><span data-stu-id="5e365-680">The result should be as below:</span></span>

    ![カメラに通知の受信側のスクリプトをドラッグします。](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="5e365-682">これは、Microsoft HoloLens の開発は、更新する必要があります、 **Main Camera**の*カメラ*コンポーネント、ように。</span><span class="sxs-lookup"><span data-stu-id="5e365-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="5e365-683">フラグをオフにします。純色</span><span class="sxs-lookup"><span data-stu-id="5e365-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="5e365-684">背景知識:黒</span><span class="sxs-lookup"><span data-stu-id="5e365-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="5e365-685">第 16 章 – UWP への複合現実プロジェクトをビルド</span><span class="sxs-lookup"><span data-stu-id="5e365-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="5e365-686">この章では、ビルド前のプロジェクトのプロセスと同じです。</span><span class="sxs-lookup"><span data-stu-id="5e365-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="5e365-687">このプロジェクトの Unity のセクションの必要なすべてが今すぐ完了したら、ので、Unity から構築するための時間。</span><span class="sxs-lookup"><span data-stu-id="5e365-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="5e365-688">移動します**ビルド設定**(**ファイル** > **ビルド設定**)。</span><span class="sxs-lookup"><span data-stu-id="5e365-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="5e365-689">**Build Settings** ] メニューの [確認**UnityC#プロジェクト**\* がオンになって (これにより、ビルドの後に、このプロジェクト内のスクリプトを編集すること)。</span><span class="sxs-lookup"><span data-stu-id="5e365-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="5e365-690">これが完了したら**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-690">After this is done, click **Build**.</span></span>

    ![プロジェクトをビルドします。](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="5e365-692">A**ファイル エクスプ ローラー**ビルドする場所の入力を求めるウィンドウがポップアップします。</span><span class="sxs-lookup"><span data-stu-id="5e365-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="5e365-693">新しいフォルダーを作成 (をクリックして**新しいフォルダー**左上隅にある)、名前を付けます**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![ビルド フォルダーを作成します。](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="5e365-695">開き、新しい**ビルド**フォルダー、別のフォルダーを作成し、(を使用して**新しいフォルダー**もう一度)、名前を付けます**NH\_MR\_アプリ**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![NH_MR_Apps フォルダーを作成します。](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="5e365-697">**NH\_MR\_アプリ**選択します。</span><span class="sxs-lookup"><span data-stu-id="5e365-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="5e365-698">クリックして**フォルダーの選択**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-698">click **Select Folder**.</span></span> <span data-ttu-id="5e365-699">プロジェクトは、ビルドを 1 分程度かかります。</span><span class="sxs-lookup"><span data-stu-id="5e365-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="5e365-700">次のビルド、**ファイル エクスプ ローラー**新しいプロジェクトの場所にウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="5e365-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="5e365-701">第 17 章 – UnityMRNotifHub ソリューションの NuGet パッケージの追加</span><span class="sxs-lookup"><span data-stu-id="5e365-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="5e365-702">次の NuGet パッケージを追加するに注意してください (次のコードをコメント解除します[章](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class))、コード、Unity プロジェクト内で再び開いたときにエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="5e365-703">戻るし、Unity エディターで編集を続行する場合は、その errosome コードにコメントし、したら、Visual Studio に戻った後でもう一度コメント解除し、必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="5e365-704">複合現実のビルドが完了したら、ビルドした複合現実プロジェクトに移動し、Visual Studio 2017 でのソリューションを開くには、そのフォルダー内のソリューション (.sln) ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="5e365-705">追加する必要がありますこれで、 **WindowsAzure.Messaging.managed** NuGet パッケージです。 これは、通知ハブから通知を受信するために使用するライブラリ。</span><span class="sxs-lookup"><span data-stu-id="5e365-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="5e365-706">NuGet パッケージをインポートするには。</span><span class="sxs-lookup"><span data-stu-id="5e365-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="5e365-707">**ソリューション エクスプ ローラー**ソリューションを右クリックして</span><span class="sxs-lookup"><span data-stu-id="5e365-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="5e365-708">をクリックして**NuGet パッケージの管理**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-708">Click on **Manage NuGet Packages**.</span></span>

    ![nuget マネージャーを開く](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="5e365-710">選択、***参照***タブし、検索**WindowsAzure.Messaging.managed**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![windows azure のメッセージング パッケージを検索します。](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="5e365-712">(次に示す) の結果を選択し、右側のウィンドウでに横にチェック ボックスをオン**プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="5e365-713">ティックを横にチェック ボックスをオンに配置これは**プロジェクト**、横のチェック ボックスと共に、**アセンブリ CSharp**と**UnityMRNotifHub**プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="5e365-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![すべてのプロジェクトをオンに](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="5e365-715">最初に指定されたバージョン**可能性がある**このプロジェクトを互換性があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="5e365-716">そのため、次に、ドロップダウン メニューをクリックします**バージョン**、 をクリック**バージョン 0.1.7.9**、 をクリックし、**インストール**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="5e365-717">NuGet パッケージのインストールが終了したようになりました。</span><span class="sxs-lookup"><span data-stu-id="5e365-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="5e365-718">入力したコメントが付けられたコードの検索、 **NotificationReceiver**クラスし、コメントを削除する.</span><span class="sxs-lookup"><span data-stu-id="5e365-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="5e365-719">第 18 章 - 編集 UnityMRNotifHub アプリケーション、NotificationReceiver クラス</span><span class="sxs-lookup"><span data-stu-id="5e365-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="5e365-720">次の追加した後、 **NuGet パッケージの**、する必要があります*をコメント解除します*内のコードの一部、 **NotificationReceiver**クラス。</span><span class="sxs-lookup"><span data-stu-id="5e365-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="5e365-721">たとえば、次のようなアニメーションや効果を作成できます。</span><span class="sxs-lookup"><span data-stu-id="5e365-721">This includes:</span></span>

1. <span data-ttu-id="5e365-722">上部にある名前空間:</span><span class="sxs-lookup"><span data-stu-id="5e365-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="5e365-723">内のすべてのコード、 **InitNotificationsAsync()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="5e365-723">All the code within the **InitNotificationsAsync()** method:</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> <span data-ttu-id="5e365-724">上記のコードにコメントを持つ: が誤っていることを確認*コメント解除された*(ように、コードはコンパイルされませんがあれば!) をコメントします。</span><span class="sxs-lookup"><span data-stu-id="5e365-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="5e365-725">最後に、 **Channel_PushNotificationReceived**イベント。</span><span class="sxs-lookup"><span data-stu-id="5e365-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

<span data-ttu-id="5e365-726">このコンピューターでは、保存、および、し、[次へ] の章に進むことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5e365-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="5e365-727">第 19 章 – ストア アプリに複合現実プロジェクトに関連付ける</span><span class="sxs-lookup"><span data-stu-id="5e365-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="5e365-728">これで、関連付ける必要があります、**複合現実**ラボの開始時に作成したストア アプリにプロジェクト。</span><span class="sxs-lookup"><span data-stu-id="5e365-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="5e365-729">ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="5e365-729">Open the solution.</span></span>

2.  <span data-ttu-id="5e365-730">ソリューション エクスプ ローラー パネルで、移動先の UWP アプリ プロジェクトを右クリックして**ストア**、および**アプリケーションをストアと関連付ける.** .</span><span class="sxs-lookup"><span data-stu-id="5e365-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![ストアのアソシエーションを開く](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="5e365-732">新しいウィンドウが呼び出された表示**アプリケーションを Windows ストアと関連付ける**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="5e365-733">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-733">Click **Next**.</span></span>

    ![次の画面に移動します。](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="5e365-735">ログインしたら、アカウントに関連付けられているすべてのアプリケーションを構成が読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="5e365-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="5e365-736">場合は、アカウントにログインしていない、**ログで**このページでします。</span><span class="sxs-lookup"><span data-stu-id="5e365-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="5e365-737">検索、**ストアのアプリ名**このチュートリアルの開始時に作成してそれを選択します。</span><span class="sxs-lookup"><span data-stu-id="5e365-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="5e365-738">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e365-738">Then click **Next**.</span></span>

    ![検索して、ストアの名前を選択します。](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="5e365-740">クリックして**関連付ける**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-740">Click **Associate**.</span></span>

    ![アプリを関連付ける](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="5e365-742">これで、アプリは**関連付けられている**ストア アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="5e365-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="5e365-743">これは、通知を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="5e365-744">第 20 章 - UnityMRNotifHub と UnityDesktopNotifHub アプリケーションの展開</span><span class="sxs-lookup"><span data-stu-id="5e365-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="5e365-745">この章は、実行中のアプリ、デスクトップ コンピューターで実行する 1 台の両方と、イマーシブ ヘッドセット内で、その他の結果が含まれますと 2 人のユーザーで、簡単に場合があります。</span><span class="sxs-lookup"><span data-stu-id="5e365-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="5e365-746">イマーシブ ヘッドセット アプリは、シーン (ローカルの Gameobject の位置変更) に変更を受信を待機しているし、ローカル シーン (位置変更)、MR アプリに共有されますが、デスクトップ アプリが変更を加えています。</span><span class="sxs-lookup"><span data-stu-id="5e365-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="5e365-747">理にかなって MR アプリのデプロイを最初に、デスクトップ アプリは、後に、受信側がリッスンを開始することができるようにします。</span><span class="sxs-lookup"><span data-stu-id="5e365-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="5e365-748">展開する、 **UnityMRNotifHub**ローカル コンピューター上のアプリ。</span><span class="sxs-lookup"><span data-stu-id="5e365-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="5e365-749">ソリューション ファイルを開き、 **UnityMRNotifHub**でアプリ**Visual Studio 2017**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="5e365-750">**ソリューション プラットフォーム**、 **x86、ローカル コンピューター**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="5e365-751">**ソリューション構成**選択**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![セットのプロジェクトの構成](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="5e365-753">移動して**ビルド メニューの** をクリック**ソリューションの配置**をコンピューターにアプリケーションをサイドローディングします。</span><span class="sxs-lookup"><span data-stu-id="5e365-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="5e365-754">アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="5e365-755">展開する、 **UnityDesktopNotifHub**ローカル コンピューター上のアプリ。</span><span class="sxs-lookup"><span data-stu-id="5e365-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="5e365-756">ソリューション ファイルを開き、 **UnityDesktopNotifHub**でアプリ**Visual Studio 2017**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="5e365-757">**ソリューション プラットフォーム**、 **x86、ローカル コンピューター**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="5e365-758">**ソリューション構成**選択**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="5e365-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![セットのプロジェクトの構成](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="5e365-760">移動して**ビルド メニューの** をクリック**ソリューションの配置**をコンピューターにアプリケーションをサイドローディングします。</span><span class="sxs-lookup"><span data-stu-id="5e365-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="5e365-761">アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="5e365-762">複合現実アプリケーション、デスクトップ アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="5e365-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="5e365-763">実行されている両方のアプリケーションは、デスクトップに (左マウス ボタンを使用して) シーンのオブジェクトを移動します。</span><span class="sxs-lookup"><span data-stu-id="5e365-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="5e365-764">これらの位置変更はローカルでできるし、シリアル化すると、Function App サービスに送信します。</span><span class="sxs-lookup"><span data-stu-id="5e365-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="5e365-765">そうすると、Function App サービスでは、通知ハブと共にテーブルが更新されます。</span><span class="sxs-lookup"><span data-stu-id="5e365-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="5e365-766">更新プログラムを受信すると、通知ハブは、更新されたデータに直接送信する受信のデータを逆シリアル化し、新しい位置指定データをローカルのオブジェクトに適用、(この場合は、イマーシブ ヘッドセット アプリ) をすべての登録済みアプリケーションシーン内に移動します。</span><span class="sxs-lookup"><span data-stu-id="5e365-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="5e365-767">Azure Notification Hubs アプリケーションの終了</span><span class="sxs-lookup"><span data-stu-id="5e365-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="5e365-768">これで、Azure Notification Hubs のサービスを活用し、アプリ間の通信を許可する mixed reality アプリを構築します。</span><span class="sxs-lookup"><span data-stu-id="5e365-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![最終的な製品-終了](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="5e365-770">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="5e365-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="5e365-771">手順 1</span><span class="sxs-lookup"><span data-stu-id="5e365-771">Exercise 1</span></span>

<span data-ttu-id="5e365-772">Gameobject の色を変更し、シーンを表示するその他のアプリに通知を送信する方法を操作することができますか。</span><span class="sxs-lookup"><span data-stu-id="5e365-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="5e365-773">手順 2</span><span class="sxs-lookup"><span data-stu-id="5e365-773">Exercise 2</span></span>

<span data-ttu-id="5e365-774">Gameobject の動きを MR アプリに追加し、デスクトップ アプリの更新されたシーンを参照してくださいか。</span><span class="sxs-lookup"><span data-stu-id="5e365-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
