---
title: MR と Azure 311 - Microsoft Graph
description: このコースでは、Microsoft Graph を利用し、複合現実のアプリケーション内での生産性を高めるデータに接続する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、graph、没入型、hololens、vr
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694526"
---
>[!NOTE]
><span data-ttu-id="f072d-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f072d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f072d-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="f072d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f072d-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="f072d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f072d-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="f072d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f072d-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="f072d-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f072d-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="f072d-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="f072d-110">MR と Azure 311 - Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="f072d-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="f072d-111">このコースでは、場合、使用する方法について説明します。 *Microsoft Graph*複合現実のアプリケーション内でセキュリティで保護された認証を使用して、Microsoft アカウントにログインします。</span><span class="sxs-lookup"><span data-stu-id="f072d-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="f072d-112">取得し、アプリケーションのインターフェイスで、スケジュールされた会議が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f072d-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="f072d-113">*Microsoft Graph*は多くの Microsoft のサービスにアクセスできるようにする Api のセットです。</span><span class="sxs-lookup"><span data-stu-id="f072d-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="f072d-114">Microsoft は、これにより、あらゆる種類の接続しているユーザー データにアクセスするアプリケーションを意味する場合のリレーションシップによって接続されているリソースのマトリックスとして Microsoft Graph をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f072d-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="f072d-115">詳細については、次を参照してください。、 [Microsoft Graph ページ](https://developer.microsoft.com/graph)します。</span><span class="sxs-lookup"><span data-stu-id="f072d-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="f072d-116">開発を見つめますな球体では、Microsoft アカウントに安全にログインするユーザーを促しますの順にタップしてユーザーを指示は、アプリの作成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f072d-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="f072d-117">自分のアカウントにログインすると、ユーザーは同じ日のスケジュールされた会議の一覧を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="f072d-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="f072d-118">このコースを完了すると、複合現実は、次のことが、HoloLens のアプリケーションが用意されます。</span><span class="sxs-lookup"><span data-stu-id="f072d-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="f072d-119">(移動にログインし、もう一度アプリにバックアップし、アプリ外) の Microsoft アカウントにログインするユーザーに通知するオブジェクトのタップ ジェスチャを使用して、タップします。</span><span class="sxs-lookup"><span data-stu-id="f072d-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="f072d-120">その日のスケジュールされた会議の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="f072d-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="f072d-121">アプリケーションでは、責任ですが、設計と、結果を統合する方法について。</span><span class="sxs-lookup"><span data-stu-id="f072d-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="f072d-122">このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。</span><span class="sxs-lookup"><span data-stu-id="f072d-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="f072d-123">複合現実アプリを強化するためには、このコース得た知識を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="f072d-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="f072d-124">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="f072d-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f072d-125">コース</span><span class="sxs-lookup"><span data-stu-id="f072d-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f072d-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f072d-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f072d-127"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="f072d-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="f072d-128">MR と Azure 311:Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="f072d-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="f072d-129">✔️</span><span class="sxs-lookup"><span data-stu-id="f072d-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="f072d-130">前提条件</span><span class="sxs-lookup"><span data-stu-id="f072d-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="f072d-131">このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。</span><span class="sxs-lookup"><span data-stu-id="f072d-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="f072d-132">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 7 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f072d-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="f072d-133">内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)にする必要がありますが想定されていなかったことについては、このコースでとまったく同じで記載されているものよりも新しいソフトウェアで表示されますが、記事以下に。</span><span class="sxs-lookup"><span data-stu-id="f072d-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="f072d-134">次のハードウェアとソフトウェアこのコースをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f072d-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="f072d-135">開発用 PC</span><span class="sxs-lookup"><span data-stu-id="f072d-135">A development PC</span></span>
- [<span data-ttu-id="f072d-136">Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="f072d-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f072d-137">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="f072d-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f072d-138">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="f072d-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f072d-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f072d-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="f072d-140">A [Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効</span><span class="sxs-lookup"><span data-stu-id="f072d-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="f072d-141">Azure のセットアップと Microsoft Graph データの取得のインターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="f072d-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="f072d-142">有効な**Microsoft アカウント**(個人または職場/学校)</span><span class="sxs-lookup"><span data-stu-id="f072d-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="f072d-143">同じ Microsoft アカウントを使用して、いくつかの会議は現在の日のスケジュール</span><span class="sxs-lookup"><span data-stu-id="f072d-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="f072d-144">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="f072d-144">Before you start</span></span>

1.  <span data-ttu-id="f072d-145">このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。</span><span class="sxs-lookup"><span data-stu-id="f072d-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="f072d-146">設定して、HoloLens をテストします。</span><span class="sxs-lookup"><span data-stu-id="f072d-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="f072d-147">場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。</span><span class="sxs-lookup"><span data-stu-id="f072d-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="f072d-148">(場合によって役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときに、調整とセンサーのチューニングを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f072d-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="f072d-149">調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。</span><span class="sxs-lookup"><span data-stu-id="f072d-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="f072d-150">センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。</span><span class="sxs-lookup"><span data-stu-id="f072d-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="f072d-151">1 -」の章では、アプリケーション登録ポータルでアプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="f072d-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="f072d-152">作成し、アプリケーションを登録する必要がありますはまず、**アプリケーション登録ポータル**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="f072d-153">この章に通話を行うことを許可するサービスのキーも検索が*Microsoft Graph*アカウント コンテンツにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="f072d-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="f072d-154">移動し、 [Microsoft アプリケーション登録ポータル](https://apps.dev.microsoft.com)Microsoft アカウントを使用してログインします。</span><span class="sxs-lookup"><span data-stu-id="f072d-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="f072d-155">ログインしたら後に、リダイレクトされます、**アプリケーション登録ポータル**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="f072d-156">**アプリケーション**セクションで、ボタンをクリックして、**アプリの追加**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="f072d-157">**アプリケーション登録ポータル**、以前に学習したかどうかに応じて異なるよう*Microsoft Graph*します。</span><span class="sxs-lookup"><span data-stu-id="f072d-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="f072d-158">以下のスクリーン ショットには、これらの異なるバージョンを表示します。</span><span class="sxs-lookup"><span data-stu-id="f072d-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="f072d-159">クリックして、アプリケーションの名前を追加**作成**です。</span><span class="sxs-lookup"><span data-stu-id="f072d-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="f072d-160">アプリケーションが作成されたら、アプリケーションのメイン ページにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="f072d-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="f072d-161">コピー、**アプリケーション Id**を安全な場所にこの値をメモしておきますとは、コードですぐに使用されます。</span><span class="sxs-lookup"><span data-stu-id="f072d-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="f072d-162">**プラットフォーム**セクションで、必ず**ネイティブ アプリケーション**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f072d-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="f072d-163">場合*いない* をクリックして**プラットフォームの追加**選択**ネイティブ アプリケーション**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="f072d-164">下へスクロールし、同じページで」というセクション**Microsoft Graph のアクセス許可**アプリケーションのアクセス許可を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f072d-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="f072d-165">をクリックして**追加**横に**委任されたアクセス許可**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="f072d-166">アプリケーションへのユーザーの予定表にアクセスするためのチェックと呼ばれるボックス**Calendars.Read**  をクリック**OK**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="f072d-167">下部までスクロールし、**保存**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f072d-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="f072d-168">保存を確認してからログアウトしたことができます、**アプリケーション登録ポータル**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="f072d-169">第 2 章 - Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="f072d-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="f072d-170">次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。</span><span class="sxs-lookup"><span data-stu-id="f072d-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="f072d-171">開いている*Unity*クリック**新規**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="f072d-172">Unity プロジェクトの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f072d-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="f072d-173">挿入**MSGraphMR**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="f072d-174">必ず、プロジェクト テンプレートに設定されて**3D**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="f072d-175">設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。</span><span class="sxs-lookup"><span data-stu-id="f072d-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="f072d-176">をクリックし、**プロジェクトの作成**です。</span><span class="sxs-lookup"><span data-stu-id="f072d-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="f072d-177">既定値を確認する必要が開いている Unity、 **スクリプト エディター** に設定されている **Visual Studio** します。</span><span class="sxs-lookup"><span data-stu-id="f072d-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="f072d-178">移動して**編集** > **設定**し、新しいウィンドウに移動**外部ツール**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-178">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="f072d-179">変更 **External Script Editor** に **Visual Studio 2017** します。</span><span class="sxs-lookup"><span data-stu-id="f072d-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="f072d-180">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="f072d-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="f072d-181">移動**ファイル** > **Build Settings**選択と**ユニバーサル Windows プラットフォーム**、 をクリックし、**スイッチ プラットフォーム**選択内容を適用するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f072d-181">Go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="f072d-182">**ファイル** > **Build Settings**、ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f072d-182">While still in **File** > **Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="f072d-183">**デバイスを対象に**に設定されている**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="f072d-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="f072d-184">**ビルドの種類**に設定されている**D3D**</span><span class="sxs-lookup"><span data-stu-id="f072d-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="f072d-185">**SDK**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="f072d-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="f072d-186">**Visual Studio バージョン**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="f072d-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="f072d-187">**ビルドおよび実行**に設定されている**ローカル マシン**</span><span class="sxs-lookup"><span data-stu-id="f072d-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="f072d-188">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="f072d-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="f072d-189">これには、選択**開くシーンを追加**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="f072d-190">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f072d-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="f072d-191">これと、任意の将来、シーンの新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f072d-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="f072d-192">選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="f072d-193">新たに作成した開く**シーン**フォルダー、し、*ファイル名*: テキスト フィールドに「 **MR_ComputerVisionScene**、順にクリックします**保存**.</span><span class="sxs-lookup"><span data-stu-id="f072d-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="f072d-194">注意してください、内の Unity シーンを保存する必要があります、*資産*フォルダー、Unity プロジェクトに関連付けられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f072d-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="f072d-195">Unity プロジェクトの構造の一般的な方法は、シーン フォルダー (およびその他の同様のフォルダー) を作成します。</span><span class="sxs-lookup"><span data-stu-id="f072d-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="f072d-196">設定に残っている*Build Settings*、ここでは既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f072d-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="f072d-197">*Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。</span><span class="sxs-lookup"><span data-stu-id="f072d-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="f072d-198">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f072d-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="f072d-199">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="f072d-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="f072d-200">**Scripting** **ランタイム バージョン**する必要があります**試験的**(.NET 4.6 Equivalent)、エディターを再起動する必要があるします。</span><span class="sxs-lookup"><span data-stu-id="f072d-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="f072d-201">**バックエンドの scripting**べき **.NET**</span><span class="sxs-lookup"><span data-stu-id="f072d-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="f072d-202">**API の互換性レベル**べき **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="f072d-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="f072d-203">内で、**発行の設定**] タブの [**機能**、確認してください。</span><span class="sxs-lookup"><span data-stu-id="f072d-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="f072d-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="f072d-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="f072d-205">パネル、下の方に**XR 設定**(次に示します**発行設定**)、確認**仮想現実サポート**、ことを確認します、 **Windows Mixed RealitySDK**が追加されます。</span><span class="sxs-lookup"><span data-stu-id="f072d-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="f072d-206">戻り*Build Settings*、 *UnityC#プロジェクト*が不要になったグレー; これの横にあるチェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="f072d-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="f072d-207">閉じる、 *Build Settings*ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="f072d-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="f072d-208">シーンとプロジェクトを保存 (**ファイル** > **保存シーン/file** > **プロジェクトの保存**)。</span><span class="sxs-lookup"><span data-stu-id="f072d-208">Save your scene and project (**FILE** > **SAVE SCENES / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="f072d-209">第 3 章 - Unity でのインポート ライブラリ</span><span class="sxs-lookup"><span data-stu-id="f072d-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f072d-210">スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[311.unitypackage MR-Azure の](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)、としてプロジェクトにインポート、 [**カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 5 章](#chapter-5---create-meetingsui-class)します。</span><span class="sxs-lookup"><span data-stu-id="f072d-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="f072d-211">使用する*Microsoft Graph*する必要がある Unity 内での使用、 **Microsoft.Identity.Client** DLL。</span><span class="sxs-lookup"><span data-stu-id="f072d-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="f072d-212">(つまり、プロジェクトのビルド後の編集) Unity プロジェクトをビルドした後に NuGet パッケージを追加する必要があるただし、Microsoft Graph の SDK を使用することです。</span><span class="sxs-lookup"><span data-stu-id="f072d-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="f072d-213">必要な Dll を Unity に直接インポートする方が簡単と見なされます。</span><span class="sxs-lookup"><span data-stu-id="f072d-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="f072d-214">インポート後に再構成するプラグインを必要とする Unity での既知の問題は現在します。</span><span class="sxs-lookup"><span data-stu-id="f072d-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="f072d-215">バグが解決された後、次の手順 (このセクションでは 4 ~ 7) は必要に不要になった。</span><span class="sxs-lookup"><span data-stu-id="f072d-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="f072d-216">インポートする*Microsoft Graph*独自のプロジェクトに[MSGraph_LabPlugins.zip ファイルをダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)します。</span><span class="sxs-lookup"><span data-stu-id="f072d-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="f072d-217">テスト済みのライブラリのバージョンでは、このパッケージが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f072d-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="f072d-218">カスタム Dll を Unity プロジェクトに追加する方法を詳しく把握したい場合[こちらのリンク](https://docs.unity3d.com/Manual/UsingDLL.html)します。</span><span class="sxs-lookup"><span data-stu-id="f072d-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="f072d-219">パッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="f072d-219">To import the package:</span></span>

1.  <span data-ttu-id="f072d-220">使用して、Unity に Unity パッケージを追加、**資産** > **パッケージのインポート** > **カスタム パッケージ**メニュー オプション。</span><span class="sxs-lookup"><span data-stu-id="f072d-220">Add the Unity Package to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span> <span data-ttu-id="f072d-221">ダウンロードしたパッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="f072d-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="f072d-222">**Unity パッケージのインポート**その pop をボックスで、(およびなど)、すべてのことを確認**プラグイン**が選択されています。</span><span class="sxs-lookup"><span data-stu-id="f072d-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="f072d-223">をクリックして、**インポート**をプロジェクトにアイテムを追加するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f072d-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="f072d-224">移動して、 **MSGraph**の下のフォルダー**プラグイン**で、*プロジェクト パネル*というプラグインを選択します。 **Microsoft.Identity.Client**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="f072d-225">*プラグイン*ように選択すると、**任意のプラットフォーム**が選択されていない、いることを確認し、 **WSAPlayer**もが選択されていないクリック**適用**.</span><span class="sxs-lookup"><span data-stu-id="f072d-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="f072d-226">これは、ファイルが正しく構成されていることを確認するだけです。</span><span class="sxs-lookup"><span data-stu-id="f072d-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="f072d-227">これらのプラグインをマークする Unity エディターでのみ使用することを構成します。</span><span class="sxs-lookup"><span data-stu-id="f072d-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="f072d-228">WSA フォルダーにプロジェクトがユニバーサル Windows アプリケーションとして Unity からエクスポートされた後に使用される Dll のさまざまなセットがあります。</span><span class="sxs-lookup"><span data-stu-id="f072d-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="f072d-229">次を開く必要があります、 **WSA**フォルダー内で、 **MSGraph**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="f072d-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="f072d-230">構成した同じファイルのコピーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f072d-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="f072d-231">ファイルを選択し、次に、インスペクター。</span><span class="sxs-lookup"><span data-stu-id="f072d-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="f072d-232">いることを確認**任意のプラットフォーム**は**unchecked**、および**のみ** **WSAPlayer**は**チェック**。</span><span class="sxs-lookup"><span data-stu-id="f072d-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="f072d-233">確認**SDK**に設定されている**UWP**、および**Scripting バックエンド**に設定されている**Dot Net**</span><span class="sxs-lookup"><span data-stu-id="f072d-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="f072d-234">いることを確認**処理しない**は**チェック**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="f072d-235">**[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f072d-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="f072d-236">第 4 章 - カメラのセットアップ</span><span class="sxs-lookup"><span data-stu-id="f072d-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="f072d-237">この章では、シーンのメイン カメラを設定します。</span><span class="sxs-lookup"><span data-stu-id="f072d-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="f072d-238">*階層パネル*を選択、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="f072d-239">すべてのコンポーネントを参照してください。 選択すると、ができる、 **Main Camera**で、*インスペクター*パネル。</span><span class="sxs-lookup"><span data-stu-id="f072d-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="f072d-240">**Camera オブジェクト**名前を指定する必要があります**Main Camera** (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="f072d-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="f072d-241">Main Camera**タグ**に設定する必要があります**MainCamera** (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="f072d-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="f072d-242">必ず、**変換位置**に設定されている**0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="f072d-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="f072d-243">設定**フラグをクリア**に**純色**</span><span class="sxs-lookup"><span data-stu-id="f072d-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="f072d-244">設定、**背景色**にカメラのコンポーネントの**黒、アルファ 0** **(コードを 16 進数: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="f072d-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="f072d-245">最終的なオブジェクトの構造、*階層パネル*次の図に示すようになります。</span><span class="sxs-lookup"><span data-stu-id="f072d-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="f072d-246">第 5 章「MeetingsUI クラスを作成</span><span class="sxs-lookup"><span data-stu-id="f072d-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="f072d-247">最初のスクリプトを作成する必要があるは**MeetingsUI**、これはホストと (ウェルカム メッセージ、手順、および会議の詳細) のアプリケーションの UI の作成を担当します。</span><span class="sxs-lookup"><span data-stu-id="f072d-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="f072d-248">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f072d-248">To create this class:</span></span>

1.  <span data-ttu-id="f072d-249">右クリックし、**資産**フォルダーで、*プロジェクト パネル*を選択し、**作成** > **フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-249">Right-click on the **Assets** folder in the *Project Panel*, then select **Create** > **Folder**.</span></span> <span data-ttu-id="f072d-250">フォルダーの名前**スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="f072d-251">開く、**スクリプト**フォルダー、そのフォルダー内で右クリックし、**作成** >   **C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-251">Open the **Scripts** folder then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="f072d-252">スクリプトの名前**MeetingsUI します。**</span><span class="sxs-lookup"><span data-stu-id="f072d-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="f072d-253">ダブルクリックして、新しい**MeetingsUI**スクリプト ファイルを開く*Visual Studio*します。</span><span class="sxs-lookup"><span data-stu-id="f072d-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="f072d-254">次の名前空間を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f072d-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="f072d-255">クラス内には、次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f072d-255">Inside the class insert the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  <span data-ttu-id="f072d-256">置換し、 **Start()** メソッドを追加し、 **Awake()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="f072d-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="f072d-257">これらが、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f072d-257">These will be called when the class initializes:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  <span data-ttu-id="f072d-258">作成を担当するメソッドを追加、*会議 UI*し、要求されたときに、現在の会議を設定します。</span><span class="sxs-lookup"><span data-stu-id="f072d-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. <span data-ttu-id="f072d-259">**削除**、 **Update()** メソッドをおよび**変更を保存**Unity に戻る前に Visual Studio で。</span><span class="sxs-lookup"><span data-stu-id="f072d-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="f072d-260">第 6 章 - Graph クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f072d-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="f072d-261">次のスクリプトを作成するには、**グラフ**スクリプト。</span><span class="sxs-lookup"><span data-stu-id="f072d-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="f072d-262">このスクリプトは、ユーザーを認証し、ユーザーの予定表から現在の日付のスケジュールされた会議を取得する呼び出しを行う責任を負います。</span><span class="sxs-lookup"><span data-stu-id="f072d-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="f072d-263">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f072d-263">To create this class:</span></span>

1.  <span data-ttu-id="f072d-264">ダブルクリックして、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f072d-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="f072d-265">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="f072d-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="f072d-266">スクリプトの名前**グラフ**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="f072d-267">Visual Studio で開くことをスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f072d-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="f072d-268">次の名前空間を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f072d-268">Insert the following namespaces:</span></span>

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="f072d-269">このスクリプトでは、コードの部分にラップされることがわかります[プリコンパイル ディレクティブ](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)、これは、Visual Studio のソリューションを構築するときに、ライブラリでの問題を回避するためにします。</span><span class="sxs-lookup"><span data-stu-id="f072d-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="f072d-270">削除、 **Start()** と**Update()** メソッドを使用できません。</span><span class="sxs-lookup"><span data-stu-id="f072d-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="f072d-271">外側、**グラフ**クラス、毎日のスケジュールされた会議を表す JSON オブジェクトを逆シリアル化するために必要な次のオブジェクトを挿入します。</span><span class="sxs-lookup"><span data-stu-id="f072d-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  <span data-ttu-id="f072d-272">内で、**グラフ**クラスで、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="f072d-272">Inside the **Graph** class, add the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > <span data-ttu-id="f072d-273">変更、 **appId** 値を **アプリ Id** で書き留めたが **[第 1 章](#chapter-1---create-your-app-in-the-application-registration-portal)、手順 4.** します。</span><span class="sxs-lookup"><span data-stu-id="f072d-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="f072d-274">この値で表示される内容と同じである、**アプリケーション登録ポータルでは、** アプリケーション登録ページにします。</span><span class="sxs-lookup"><span data-stu-id="f072d-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="f072d-275">内で、**グラフ**クラス、メソッドを追加します**SignInAsync()** と**AquireTokenAsync()** ログインの資格情報を挿入するユーザーを促します。</span><span class="sxs-lookup"><span data-stu-id="f072d-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  <span data-ttu-id="f072d-276">次の 2 つのメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="f072d-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="f072d-277">**BuildTodayCalendarEndpoint()** 日、スケジュールされた会議を取得する期間を指定する URI を構築します。</span><span class="sxs-lookup"><span data-stu-id="f072d-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="f072d-278">**ListMeetingsAsync()** 、要求からスケジュールされた会議*Microsoft Graph*します。</span><span class="sxs-lookup"><span data-stu-id="f072d-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. <span data-ttu-id="f072d-279">完了したので、**グラフ**スクリプト。</span><span class="sxs-lookup"><span data-stu-id="f072d-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="f072d-280">**変更を保存**Visual studio を Unity に返す前にします。</span><span class="sxs-lookup"><span data-stu-id="f072d-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="f072d-281">Chapter 7 - GazeInput スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f072d-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="f072d-282">作成、 **GazeInput**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="f072d-283">このクラスを処理しを使用して、ユーザーの視線の先の追跡、 **Raycast**から、 **Main Camera**、前方に射影します。</span><span class="sxs-lookup"><span data-stu-id="f072d-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="f072d-284">スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f072d-284">To create the script:</span></span>

1.  <span data-ttu-id="f072d-285">ダブルクリックして、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f072d-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="f072d-286">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="f072d-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="f072d-287">スクリプトの名前**GazeInput**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="f072d-288">Visual Studio で開くことをスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f072d-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="f072d-289">追加すると共に、以下と一致する名前空間のコードを変更、' **\[System.Serializable\]** ' 上記のタグ、 **GazeInput**クラスをシリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f072d-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="f072d-290">内で、 **GazeInput**クラスで、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="f072d-290">Inside the **GazeInput** class, add the following variables:</span></span>

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  <span data-ttu-id="f072d-291">追加、 **CreateCursor()** 、シーンの HoloLens のカーソルを作成しからメソッドを呼び出すメソッドを**Start()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="f072d-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  <span data-ttu-id="f072d-292">次のメソッドは、Raycast 視線の先を有効にして、フォーカスがあるオブジェクトの追跡。</span><span class="sxs-lookup"><span data-stu-id="f072d-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="f072d-293">**変更を保存**Visual studio を Unity に返す前にします。</span><span class="sxs-lookup"><span data-stu-id="f072d-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="f072d-294">8 -」の章の相互作用クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f072d-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="f072d-295">作成する必要がありますこれで、**の相互作用**を担当するスクリプト。</span><span class="sxs-lookup"><span data-stu-id="f072d-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="f072d-296">処理、**タップ**相互作用と**カメラ視線**、「ボタン」が、シーン内のログと対話するユーザーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f072d-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="f072d-297">ユーザーと対話するため、シーン内の「ボタン」オブジェクトでログを作成します。</span><span class="sxs-lookup"><span data-stu-id="f072d-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="f072d-298">スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f072d-298">To create the script:</span></span>

1.  <span data-ttu-id="f072d-299">ダブルクリックして、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f072d-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="f072d-300">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="f072d-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="f072d-301">スクリプトの名前**の相互作用**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="f072d-302">Visual Studio で開くことをスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f072d-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="f072d-303">次の名前空間を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f072d-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="f072d-304">継承の変更、**相互作用**クラス*MonoBehaviour*に**GazeInput**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="f072d-305">~~パブリック クラスの相互作用します。MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="f072d-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="f072d-306">内で、**相互作用**クラスは、次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f072d-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="f072d-307">置換、**開始**メソッドは、'base' 注視クラスのメソッドを呼び出すオーバーライド メソッドであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f072d-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="f072d-308">**Start()** クラスが初期化、入力の認識のための登録とサインインを作成するときに呼び出される*ボタン*シーン内。</span><span class="sxs-lookup"><span data-stu-id="f072d-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  <span data-ttu-id="f072d-309">追加、 **CreateSignInButton()** メソッドは、サインインをインスタンス化は*ボタン*シーン内とプロパティの設定。</span><span class="sxs-lookup"><span data-stu-id="f072d-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  <span data-ttu-id="f072d-310">追加、 **GestureRecognizer_Tapped()** メソッド応答、*タップ*ユーザー イベント。</span><span class="sxs-lookup"><span data-stu-id="f072d-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. <span data-ttu-id="f072d-311">**削除**、 **Update()** メソッドし**変更を保存**Unity に戻る前に Visual Studio でします。</span><span class="sxs-lookup"><span data-stu-id="f072d-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="f072d-312">第 9 章 – は、スクリプト参照を設定</span><span class="sxs-lookup"><span data-stu-id="f072d-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="f072d-313">この章では、配置する必要があります、**の相互作用**にスクリプト、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="f072d-314">他のスクリプトに必要な場所に配置するスクリプトを処理し、します。</span><span class="sxs-lookup"><span data-stu-id="f072d-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="f072d-315">**スクリプト**フォルダーで、*プロジェクト パネル*、スクリプトをドラッグして**の相互作用**を**Main Camera**オブジェクトを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f072d-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="f072d-316">第 10 章 – タグを設定</span><span class="sxs-lookup"><span data-stu-id="f072d-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="f072d-317">タグの使用、視線入力を処理するコードと、 **SignInButton**オブジェクトを識別するために、ユーザーにサインインするやり取り*Microsoft Graph*します。</span><span class="sxs-lookup"><span data-stu-id="f072d-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="f072d-318">タグを作成します。</span><span class="sxs-lookup"><span data-stu-id="f072d-318">To create the Tag:</span></span>

1.  <span data-ttu-id="f072d-319">Unity エディターでのクリックして、 **Main Camera**で、*階層パネル*します。</span><span class="sxs-lookup"><span data-stu-id="f072d-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="f072d-320">*インスペクター パネル* をクリックして、 **MainCamera** *タグ*をドロップダウン リストを開きます。</span><span class="sxs-lookup"><span data-stu-id="f072d-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="f072d-321">をクリックして**タグを追加しています.**</span><span class="sxs-lookup"><span data-stu-id="f072d-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="f072d-322">をクリックして、 **+** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f072d-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="f072d-323">タグの名前を書き込み**SignInButton** [保存] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f072d-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="f072d-324">第 11 章 - UWP を Unity プロジェクトをビルド</span><span class="sxs-lookup"><span data-stu-id="f072d-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="f072d-325">このプロジェクトの Unity のセクションの必要なすべてが今すぐ完了したら、ので、Unity から構築するための時間。</span><span class="sxs-lookup"><span data-stu-id="f072d-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="f072d-326">移動します *ビルド設定* (**ファイル* >* 設定\*\* を作成) します。</span><span class="sxs-lookup"><span data-stu-id="f072d-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="f072d-327">まだ行っていない場合、ティック**Unity C\#プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="f072d-328">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f072d-328">Click **Build**.</span></span> <span data-ttu-id="f072d-329">Unity を起動、**ファイル エクスプ ローラー**ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f072d-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="f072d-330">ここで、そのフォルダーを作成し、名前**アプリ**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="f072d-331">使用し、**アプリ**フォルダーを選択すると、クリックして**フォルダーの選択**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="f072d-332">Unity にプロジェクトをビルドを開始、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="f072d-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="f072d-333">1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。</span><span class="sxs-lookup"><span data-stu-id="f072d-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="f072d-334">HoloLens に 12 -」の章をデプロイします。</span><span class="sxs-lookup"><span data-stu-id="f072d-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="f072d-335">HoloLens の展開。</span><span class="sxs-lookup"><span data-stu-id="f072d-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="f072d-336">必要になります、HoloLens の IP アドレス (リモート) を展開し、HoloLens をことを確認するには**開発者モード。**</span><span class="sxs-lookup"><span data-stu-id="f072d-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="f072d-337">これには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f072d-337">To do this:</span></span>

    1.  <span data-ttu-id="f072d-338">ソックスを着けずに、HoloLens 中を開く、**設定**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="f072d-339">移動して**ネットワークとインターネット** > **Wi-fi** > **詳細オプション**</span><span class="sxs-lookup"><span data-stu-id="f072d-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="f072d-340">注、 **IPv4**アドレス。</span><span class="sxs-lookup"><span data-stu-id="f072d-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="f072d-341">次に移動します**設定**、し**更新とセキュリティ** > **開発者向け**</span><span class="sxs-lookup"><span data-stu-id="f072d-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="f072d-342">設定**で開発者モード**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="f072d-343">新しい Unity ビルドに移動します (、**アプリ**フォルダー) とソリューション ファイルを開くと**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="f072d-344">**ソリューション構成**選択**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="f072d-345">**ソリューション プラットフォーム**、 **x86、リモート コンピューター**します。</span><span class="sxs-lookup"><span data-stu-id="f072d-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="f072d-346">挿入を求め、 **IP アドレス**のリモート デバイス (、HoloLens、ここでは、メモしたもの)。</span><span class="sxs-lookup"><span data-stu-id="f072d-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="f072d-347">移動して**ビルド**メニューをクリックします**ソリューションの配置**サイドロード、HoloLens をアプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="f072d-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="f072d-348">アプリが、起動する準備ができて、HoloLens にインストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f072d-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="f072d-349">Microsoft Graph HoloLens アプリケーション</span><span class="sxs-lookup"><span data-stu-id="f072d-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="f072d-350">これで、読み取り、ユーザーの予定表データの表示、Microsoft Graph を利用している mixed reality アプリを構築します。</span><span class="sxs-lookup"><span data-stu-id="f072d-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="f072d-351">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="f072d-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="f072d-352">手順 1</span><span class="sxs-lookup"><span data-stu-id="f072d-352">Exercise 1</span></span>

<span data-ttu-id="f072d-353">Microsoft Graph を使用して、ユーザーに関するその他の情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="f072d-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="f072d-354">ユーザーの電子メール プロファイルの画像/電話番号</span><span class="sxs-lookup"><span data-stu-id="f072d-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="f072d-355">手順 1</span><span class="sxs-lookup"><span data-stu-id="f072d-355">Exercise 1</span></span>

<span data-ttu-id="f072d-356">Microsoft Graph の UI を移動する音声コントロールを実装します。</span><span class="sxs-lookup"><span data-stu-id="f072d-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
