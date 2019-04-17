---
title: MR と Azure 312 - Bot の統合
description: 作成し、Microsoft Bot Framework v4 を使用して、ボットをデプロイする方法については、このコースを完了し、複合現実のアプリケーションで通信します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、コンピューター ビジョン、hololens、没入型、vr、microsoft bot framework v4、web app bot、bot framework、microsoft bot
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604981"
---
>[!NOTE]
><span data-ttu-id="1a9ae-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1a9ae-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1a9ae-106">これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1a9ae-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1a9ae-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1a9ae-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="1a9ae-110">MR と Azure 312:ボットの統合</span><span class="sxs-lookup"><span data-stu-id="1a9ae-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="1a9ae-111">このコースでは、作成して、Microsoft Bot Framework V4 を使用してボットをデプロイし、Windows Mixed Reality アプリケーションを介して通信する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="1a9ae-112">**Microsoft Bot Framework V4**一連の Api は、拡張可能かつスケーラブルなボットをビルドするツールを開発者に提供するように設計されてアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="1a9ae-113">詳細については、次を参照してください。、 [Microsoft Bot Framework ページ](https://dev.botframework.com/)または[V4 の Git リポジトリ](https://github.com/Microsoft/botbuilder-dotnet/wiki)します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="1a9ae-114">このコースを完了するは、次のことが Windows Mixed Reality アプリケーションを構築したは。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="1a9ae-115">使用して、**タップ ジェスチャ**ボット ユーザー ボイスのリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="1a9ae-116">何か、ユーザーが話したが、ボットは、応答を提供しようとします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="1a9ae-117">Unity シーンでボットに近くに配置されたテキストとしてボットの応答を表示します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="1a9ae-118">アプリケーションでは、責任ですが、設計と、結果を統合する方法について。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="1a9ae-119">このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="1a9ae-120">複合現実アプリを強化するためには、このコース得た知識を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="1a9ae-121">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="1a9ae-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1a9ae-122">コース</span><span class="sxs-lookup"><span data-stu-id="1a9ae-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1a9ae-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1a9ae-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1a9ae-124"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="1a9ae-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1a9ae-125">MR と Azure 312:ボットの統合</span><span class="sxs-lookup"><span data-stu-id="1a9ae-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="1a9ae-126">✔️</span><span class="sxs-lookup"><span data-stu-id="1a9ae-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1a9ae-127">✔️</span><span class="sxs-lookup"><span data-stu-id="1a9ae-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="1a9ae-128">このコースは、HoloLens で主にフォーカスします、Windows Mixed Reality 没入型 (VR) ヘッドセットには、このコースで学習する内容を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="1a9ae-129">(VR) のイマーシブ ヘッドセットはアクセス可能な cameras があるないため、外部のカメラを PC に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="1a9ae-130">コースを実行するとき、没入型の (VR) ヘッドセットをサポートするために使用する必要があります変更でノートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1a9ae-131">前提条件</span><span class="sxs-lookup"><span data-stu-id="1a9ae-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="1a9ae-132">このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="1a9ae-133">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 7 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="1a9ae-134">内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)にする必要がありますが想定されていなかったことについては、このコースでとまったく同じで記載されているものよりも新しいソフトウェアで表示されますが、記事以下に。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="1a9ae-135">次のハードウェアとソフトウェアこのコースをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="1a9ae-136">開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発</span><span class="sxs-lookup"><span data-stu-id="1a9ae-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="1a9ae-137">Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1a9ae-138">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="1a9ae-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1a9ae-139">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="1a9ae-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1a9ae-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1a9ae-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="1a9ae-141">A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効</span><span class="sxs-lookup"><span data-stu-id="1a9ae-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="1a9ae-142">Azure と Azure Bot 取得するためのインターネット アクセス。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="1a9ae-143">詳細については、[このリンクに従ってください](https://dev.botframework.com/)します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="1a9ae-144">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="1a9ae-144">Before you start</span></span>

1.  <span data-ttu-id="1a9ae-145">このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="1a9ae-146">設定して、HoloLens をテストします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="1a9ae-147">場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="1a9ae-148">(場合によって役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときに、調整とセンサーのチューニングを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="1a9ae-149">調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="1a9ae-150">センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="1a9ae-151">第 1 章 – ボット アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="1a9ae-152">最初の手順では、ローカル ASP.Net Core Web アプリケーションとしてのお客様のボットを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="1a9ae-153">完了し、テストが、Azure ポータルに発行します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="1a9ae-154">Visual Studio を開きます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-154">Open Visual Studio.</span></span> <span data-ttu-id="1a9ae-155">新しいプロジェクトを作成**ASP NET Core Web アプリケーション**(は検索、.NET Core のサブセクションの下) プロジェクトの種類として、呼び出す**MyBot**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="1a9ae-156">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-156">Click **OK**.</span></span>

2.  <span data-ttu-id="1a9ae-157">表示されるウィンドウで**空**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="1a9ae-158">またことを確認して、ターゲットに設定されて**ASP NET Core 2.0** 、認証に設定されてと**認証なし**。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="1a9ae-159">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-159">Click **OK**.</span></span>  

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="1a9ae-161">ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-161">The solution will now open.</span></span> <span data-ttu-id="1a9ae-162">ソリューションを右クリックして**Mybot**で、**ソリューション エクスプ ローラー**  をクリック**ソリューションの NuGet パッケージの管理**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="1a9ae-164">**参照** タブで、検索**Microsoft.Bot.Builder.Integration.AspNet.Core** (があるかどうかを確認**プレリリースを含める**チェック)。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="1a9ae-165">パッケージのバージョンを選択します。 **4.0.1-preview**、し、プロジェクトのボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="1a9ae-166">をクリックして**インストール**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-166">Then click on **Install**.</span></span> <span data-ttu-id="1a9ae-167">必要なライブラリがインストールされているようになりました、 **Bot Framework v4**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="1a9ae-168">NuGet ページを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-168">Close the NuGet page.</span></span>

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="1a9ae-170">右クリックし、*プロジェクト*、 **MyBot**の**ソリューション エクスプ ローラー**  をクリック**追加** **|\*\*\*\*クラス**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="1a9ae-172">クラスの名前**MyBot**  をクリック**追加**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="1a9ae-174">という名前の別のクラスを作成する前のポイントを繰り返して**ConversationContext**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="1a9ae-175">右クリックして**wwwroot**で、**ソリューション エクスプ ローラー** ] をクリック**追加** **|** **[新しい項目**.</span><span class="sxs-lookup"><span data-stu-id="1a9ae-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="1a9ae-176">選択**HTML ページ**(が見つかったら Web サブセクションの下)。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="1a9ae-177">ファイルに名前を**default.html**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-177">Name the file **default.html**.</span></span> <span data-ttu-id="1a9ae-178">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-178">Click **Add**.</span></span>

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="1a9ae-180">クラスの一覧内のオブジェクト/、**ソリューション エクスプ ローラー**次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="1a9ae-182">ダブルクリックして、 **ConversationContext**クラス。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="1a9ae-183">このクラスは、メッセージ交換のコンテキストを維持するために、ボットで使用される変数を保持する責任を負います。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="1a9ae-184">ため、これらのメッセージ交換コンテキスト値が、このクラスのインスタンスで保持されるの任意のインスタンス、 **MyBot**クラスは、アクティビティが受信されるたびに更新されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="1a9ae-185">このクラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-185">Add the following code to the class:</span></span>

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. <span data-ttu-id="1a9ae-186">ダブルクリックして、 **MyBot**クラス。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="1a9ae-187">このクラスは、顧客から任意の受信アクティビティによって呼び出されるハンドラーをホストします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="1a9ae-188">このクラスは、ボットと顧客の間でメッセージ交換を構築するために使用するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="1a9ae-189">前述のように、このクラスのインスタンスはアクティビティが受信されるたびに初期化されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="1a9ae-190">このクラスには、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-190">Add the following code to this class:</span></span>

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. <span data-ttu-id="1a9ae-191">ダブルクリックして、**スタートアップ**クラス。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="1a9ae-192">このクラスは、ボットを初期化します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-192">This class will initialize the bot.</span></span> <span data-ttu-id="1a9ae-193">このクラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-193">Add the following code to the class:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. <span data-ttu-id="1a9ae-194">開く、**プログラム**クラス ファイルおよび内のコードは、次の場合と同じことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. <span data-ttu-id="1a9ae-195">移動するためには、変更を保存する**ファイル** > **すべて保存**、Visual Studio の上部にあるツールバーから。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="1a9ae-196">Chapter 2 - Azure Bot Service を作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="1a9ae-197">インスタンスに公開がお客様のボットのコードを作成したら、これで、 *Web App Bot* Azure Portal でのサービスです。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="1a9ae-198">この章では、作成、azure Bot Service を構成して、コードを発行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="1a9ae-199">最初に、Azure ポータルにログイン (https://portal.azure.com)します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="1a9ae-200">Azure アカウントがいない場合は、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="1a9ae-201">クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="1a9ae-202">ログインした後は、をクリックして**リソースの作成**左上隅にある検索して*Web App bot*、 をクリック**Enter**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="1a9ae-204">新しいページがの説明を入力、 *Web App Bot*サービス。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="1a9ae-205">このページの左下にある at、**作成**ボタンは、この関連付けサービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="1a9ae-207">クリックすると**作成**:</span><span class="sxs-lookup"><span data-stu-id="1a9ae-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="1a9ae-208">必要な挿入**名前**このサービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="1a9ae-209">選択、**サブスクリプション**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="1a9ae-210">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="1a9ae-211">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1a9ae-212">勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="1a9ae-213">詳細にする場合、Azure リソース グループについて[このリンクに従ってください](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="1a9ae-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="1a9ae-214">(新しいリソース グループを作成する) 場合は、リソース グループの場所を決定します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="1a9ae-215">場所は、アプリケーションが実行リージョンにあるが理想的です。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="1a9ae-216">一部の Azure 資産は特定のリージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="1a9ae-217">選択、**価格レベル**場合、これは、最初に、適切な時間を作成する、 *Web App Bot*サービス、(F0 という名前)、free レベルを使用可能にする必要があります</span><span class="sxs-lookup"><span data-stu-id="1a9ae-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="1a9ae-218">**アプリ名**だけおくことができますと同じ、*ボット名*します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="1a9ae-219">ままに、 *Bot テンプレート*として**基本的な (C#)** します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="1a9ae-220">*App service プラン/場所*アカウントに自動的に入力されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="1a9ae-221">設定、 **Azure Storage**を使用して、ボットをホストします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="1a9ae-222">既にいずれかがあるない場合、ここで作成することができます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="1a9ae-223">また、このサービスに適用される条件を理解したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="1a9ae-224">[作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-224">Click Create.</span></span>
 
        ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="1a9ae-226">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="1a9ae-227">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="1a9ae-229">新しいサービス インスタンスを探索する通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="1a9ae-231">をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="1a9ae-232">新しい Azure サービス インスタンスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="1a9ae-234">この時点でと呼ばれる機能をセットアップする必要があります**Direct Line**このボット サービスと通信するクライアント アプリケーションを許可します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="1a9ae-235">をクリックして**チャネル**、次に、**おすすめチャンネルの追加**セクションで、をクリックして**構成 Direct Line channel**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="1a9ae-237">このページでは紹介、**秘密鍵**クライアント アプリ、ボットと認証を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="1a9ae-238">をクリックして、**表示**ボタンをクリックし、プロジェクトの後半で必要になるように、表示されているキーの 1 つのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="1a9ae-240">第 3 章 – ボットを Azure Web App Bot のサービスに発行します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="1a9ae-241">準備ができたら、サービス、以前は、新しく作成された Web App Bot Service を作成したボット コードを発行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="1a9ae-242">ボットのソリューションに変更を加えるたびに、Azure サービスにお客様のボットを発行する必要があります/コードします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="1a9ae-243">以前作成した Visual Studio ソリューションに戻ります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="1a9ae-244">右クリックし、 **MyBot**プロジェクトの**ソリューション エクスプ ローラー**の **発行**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![ボットを Azure Web App Bot Service に発行します。](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="1a9ae-246">*発行先を選択* ページで  **App Service**、し**既存の**、最後に、をクリックして**プロファイルの作成**(する必要があります横のドロップダウン矢印をクリックして、*発行*ボタンが表示されない場合)。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![ボットを Azure Web App Bot Service に発行します。](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="1a9ae-248">まだログインいない Microsoft アカウントに場合に、ここで行う必要。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="1a9ae-249">**発行**ページには、同じように設定する必要がある**サブスクリプション**に使用した、 *Web App Bot*サービスの作成。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="1a9ae-250">設定し、**ビュー**として**リソース グループ**し、フォルダー構造ドロップダウンで選択、**リソース グループ**以前に作成しました。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="1a9ae-251">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-251">Click **OK**.</span></span> 

    ![ボットを Azure Web App Bot Service に発行します。](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="1a9ae-253">ここでをクリックして、**発行**ボタンをクリックし、ボットを発行するまで待ちます (少し時間がかかる場合があります)。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![ボットを Azure Web App Bot Service に発行します。](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="1a9ae-255">第 4 章 – Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="1a9ae-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="1a9ae-256">次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="1a9ae-257">開いている*Unity*クリック**新規**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-257">Open *Unity* and click **New**.</span></span> 

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="1a9ae-259">これで、Unity プロジェクトの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="1a9ae-260">挿入**Hololens ボット**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-260">Insert **Hololens Bot**.</span></span> <span data-ttu-id="1a9ae-261">必ず、プロジェクト テンプレートに設定されて**3D**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="1a9ae-262">設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="1a9ae-263">をクリックし、**プロジェクトの作成**です。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-263">Then, click **Create project**.</span></span>

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="1a9ae-265">既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="1a9ae-266">移動して**編集 > 設定**し、新しいウィンドウに移動**外部ツール**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="1a9ae-267">変更**External Script Editor**に**Visual Studio 2017**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="1a9ae-268">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-268">Close the **Preferences** window.</span></span>

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="1a9ae-270">次に移動**ファイル > Build Settings**を選択し、**ユニバーサル Windows プラットフォーム**、をクリックして、**スイッチ プラットフォーム**選択内容を適用するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="1a9ae-272">**ファイル > Build Settings**ことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="1a9ae-273">**デバイスを対象に**に設定されている**Hololens**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-273">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="1a9ae-274">イマーシブ ヘッドセット、設定**ターゲット デバイス**に*任意のデバイス*します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="1a9ae-275">**ビルドの種類**に設定されている**D3D**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="1a9ae-276">**SDK**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="1a9ae-277">**Visual Studio バージョン**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="1a9ae-278">**ビルドおよび実行**に設定されている**ローカル マシン**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="1a9ae-279">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="1a9ae-280">これには、選択**開くシーンを追加**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="1a9ae-281">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-281">A save window will appear.</span></span>
        
            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="1a9ae-283">新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="1a9ae-285">新たに作成した開く**シーン**フォルダー、し、*ファイル名*: テキスト フィールドに「 **BotScene**、[] をクリック**保存**。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="1a9ae-287">設定に残っている**Build Settings**、ここでは既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="1a9ae-288">*Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="1a9ae-290">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="1a9ae-291">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="1a9ae-292">**ランタイム バージョンをスクリプト**する必要があります**試験的 (NET 4.6 Equivalent)**; を変更すると、エディターの再起動が必要です。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="1a9ae-293">**バックエンドの scripting**べき **.NET**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="1a9ae-294">**API の互換性レベル**べき **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="1a9ae-296">内で、**発行の設定**] タブの [**機能**、確認してください。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="1a9ae-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-297">**InternetClient**</span></span>
        - <span data-ttu-id="1a9ae-298">**マイク**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-298">**Microphone**</span></span>

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="1a9ae-300">パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="1a9ae-302">戻り*Build Settings* _Unity C#_ プロジェクトが不要になったグレー; これの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="1a9ae-303">ビルド設定ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="1a9ae-304">シーンとプロジェクトを保存 (**ファイル > SAVE SCENE/ファイル > プロジェクトの保存**)。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="1a9ae-305">第 5 章 – カメラのセットアップ</span><span class="sxs-lookup"><span data-stu-id="1a9ae-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1a9ae-306">スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[Azure MR 312 Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)、としてプロジェクトにインポート[**カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 7 章](#chapter-7-–-create-the-botobjects-class)します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-7-–-create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="1a9ae-307">*階層パネル*を選択、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="1a9ae-308">すべてのコンポーネントを参照してください。 選択すると、ができる、 **Main Camera**で、*インスペクター パネル*します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="1a9ae-309">**Camera オブジェクト**名前を指定する必要があります**Main Camera** (スペルに注意してください)</span><span class="sxs-lookup"><span data-stu-id="1a9ae-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="1a9ae-310">Main Camera**タグ**に設定する必要があります**MainCamera** (スペルに注意してください)</span><span class="sxs-lookup"><span data-stu-id="1a9ae-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="1a9ae-311">必ず、**変換位置**に設定されている**0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="1a9ae-312">設定**フラグをクリア**に**単色**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="1a9ae-313">設定、**バック グラウンド**にカメラのコンポーネントの色**黒、アルファ 0 (16 進コード: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![カメラのセットアップ](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="1a9ae-315">第 6 章 – Newtonsoft ライブラリのインポート</span><span class="sxs-lookup"><span data-stu-id="1a9ae-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="1a9ae-316">逆シリアル化し、Bot Service の送受信にオブジェクトをシリアル化するのに役立つダウンロードする必要があります、 **Newtonsoft**ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="1a9ae-317">[互換性のあるバージョンが既に適切な Unity のフォルダー構造を持つ編成](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="1a9ae-318">プロジェクトに Newtonsoft ライブラリをインポートするには、このコースに付属する Unity パッケージを使用します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="1a9ae-319">追加、 *.unitypackage*に Unity を使用して、**資産** > **パッケージのインポート** > **カスタム パッケージ**メニュー オプション。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Newtonsoft ライブラリをインポートします。](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="1a9ae-321">**Unity パッケージのインポート**その pop をボックスで、(およびなど)、すべてのことを確認**プラグイン**が選択されています。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Newtonsoft ライブラリをインポートします。](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="1a9ae-323">をクリックして、**インポート**をプロジェクトにアイテムを追加するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="1a9ae-324">移動して、 **Newtonsoft**の下のフォルダー**プラグイン**プロジェクト ビューと、Newtonsoft のプラグインを選びます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="1a9ae-325">Newtonsoft プラグインを選択することを確認**Any プラットフォーム**は**unchecked**、ことを確認します**WSAPlayer**も**unchecked**、クリックして**適用**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="1a9ae-326">これは、ファイルが正しく構成されていることを確認するだけです。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="1a9ae-327">これらのプラグインをマークする Unity エディターでのみ使用することを構成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="1a9ae-328">これらのプロジェクトは Unity からエクスポートした後に使用される、WSA フォルダー内の異なるセットがあります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="1a9ae-329">次を開く必要があります、 **WSA**フォルダー内で、 **Newtonsoft**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="1a9ae-330">構成した同じファイルのコピーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="1a9ae-331">ファイルを選択し、インスペクターのことを確認します</span><span class="sxs-lookup"><span data-stu-id="1a9ae-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="1a9ae-332">**任意のプラットフォーム**は**オフ**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="1a9ae-333">**のみ** **WSAPlayer**は**チェック**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="1a9ae-334">**処理されないように**は**チェック**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="1a9ae-335">第 7 – 章、BotTag を作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="1a9ae-336">新規作成**タグ**と呼ばれるオブジェクト**BotTag**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="1a9ae-337">シーンでは、メイン カメラを選択します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="1a9ae-338">タグのドロップダウン インスペクターのパネルでメニューをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="1a9ae-339">をクリックして**タグを追加**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-339">Click on **Add Tag**.</span></span>

    ![カメラのセットアップ](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="1a9ae-341">をクリックして、 **+** シンボル。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-341">Click on the **+** symbol.</span></span> <span data-ttu-id="1a9ae-342">新しい名前**タグ**として**BotTag**、*保存*します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![カメラのセットアップ](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="1a9ae-344">**しない**適用、 **BotTag**メイン カメラにします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="1a9ae-345">誤ってこれを実行して場合、タグを Main Camera の変更を必ず*MainCamera*します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="1a9ae-346">第 8 章 – BotObjects クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="1a9ae-347">最初のスクリプトを作成する必要がありますが、 **BotObjects**クラスは、空のクラスと同じスクリプト内で、一連の他のクラス オブジェクトを格納できるように、作成し、シーン内の他のスクリプトでアクセスします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="1a9ae-348">このクラスの作成はアーキテクチャの選択肢では純粋で、これらのオブジェクトは、このコースの後半で作成するボット スクリプトでホストされる代わりに可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="1a9ae-349">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-349">To create this class:</span></span> 

1.  <span data-ttu-id="1a9ae-350">右クリックし、*プロジェクト パネル*、し**作成 > フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="1a9ae-351">フォルダーの名前**スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-351">Name the folder **Scripts**.</span></span> 

    ![[スクリプト] フォルダーを作成します。](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="1a9ae-353">ダブルクリックして、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="1a9ae-354">そのフォルダーを右クリックし、内**作成 >C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="1a9ae-355">スクリプトの名前**BotObjects**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="1a9ae-356">ダブルクリックして、新しい**BotObjects**スクリプト ファイルを開く**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="1a9ae-357">スクリプトの内容を削除し、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-357">Delete the content of the script and replace it with the following code:</span></span>

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  <span data-ttu-id="1a9ae-358">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="1a9ae-359">第 9 章 – GazeInput クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="1a9ae-360">次のクラスを作成することには、 **GazeInput**クラス。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="1a9ae-361">このクラスは、責任を負います。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-361">This class is responsible for:</span></span>

- <span data-ttu-id="1a9ae-362">カーソルの作成を表す、*視線*プレーヤーの。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="1a9ae-363">ヒットして、player の視線入力オブジェクトを検出して、検出されたオブジェクトへの参照を保持しています。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="1a9ae-364">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-364">To create this class:</span></span> 

1.  <span data-ttu-id="1a9ae-365">移動して、**スクリプト**以前に作成したフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="1a9ae-366">フォルダー内を右クリックして**作成 >C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="1a9ae-367">スクリプトを呼び出す**GazeInput**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="1a9ae-368">ダブルクリックして、新しい**GazeInput**スクリプト ファイルを開く**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="1a9ae-369">クラス名の右側で最上位の次の行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="1a9ae-370">内で、次の変数を追加し、 **GazeInput**クラス上、 **Start()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

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

6.  <span data-ttu-id="1a9ae-371">コードを**Start()** メソッドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="1a9ae-372">これが、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-372">This will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="1a9ae-373">インスタンス化し、視線の先のカーソルを設定するメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  <span data-ttu-id="1a9ae-374">メイン カメラから Raycast をセットアップしはの追跡、現在フォーカスがあるオブジェクト メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

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
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
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
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  <span data-ttu-id="1a9ae-375">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="1a9ae-376">第 10 章 – ボット クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="1a9ae-377">作成しようとするスクリプトを呼び出すようになりました**ボット**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="1a9ae-378">これは、アプリケーションのコア クラス、格納されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="1a9ae-379">Web App Bot 資格情報</span><span class="sxs-lookup"><span data-stu-id="1a9ae-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="1a9ae-380">ユーザーの音声コマンドを収集する方法</span><span class="sxs-lookup"><span data-stu-id="1a9ae-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="1a9ae-381">Web アプリのボットと会話を開始するために必要なメソッド</span><span class="sxs-lookup"><span data-stu-id="1a9ae-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="1a9ae-382">Web アプリのお客様のボットにメッセージを送信するために必要なメソッド</span><span class="sxs-lookup"><span data-stu-id="1a9ae-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="1a9ae-383">ボット サービスにメッセージを送信する、 **SendMessageToBot()** コルーチンは、ユーザーによって送信されるデータとして、Bot Framework によって認識されるオブジェクトでは、アクティビティを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="1a9ae-384">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-384">To create this class:</span></span> 

1. <span data-ttu-id="1a9ae-385">ダブルクリックして、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="1a9ae-386">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="1a9ae-387">スクリプトの名前**ボット**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="1a9ae-388">Visual Studio で開くことに新しいスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="1a9ae-389">上部にある、次と同じである名前空間の更新、**ボット**クラス。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="1a9ae-390">内で、**ボット**クラスは、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-390">Inside the **Bot** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > <span data-ttu-id="1a9ae-391">挿入することを確認、**ボットのシークレット キー**に、 **botSecret**変数。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="1a9ae-392">メモは、**ボットのシークレット キー**のこのコースでは、先頭に**[第 2 章](#chapter-2---create-the-azure-bot-service)、手順 10**。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="1a9ae-393">コードを**Awake()** と**Start()** を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. <span data-ttu-id="1a9ae-394">音声のキャプチャの開始し、終了時に、音声ライブラリによって呼び出される 2 つのハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="1a9ae-395">*DictationRecognizer*言うと、ユーザーが停止したときに、ユーザーの声をキャプチャが自動的に停止します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. <span data-ttu-id="1a9ae-396">次のハンドラーでは、ユーザーの音声入力の結果を収集し、Web アプリのボット サービスにメッセージを送信、コルーチンを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. <span data-ttu-id="1a9ae-397">次のコルーチンがボットとのメッセージ交換を開始すると呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="1a9ae-398">メッセージ交換の呼び出しが完了したら、それを呼び出すことがわかります、 **SendMessageToCoroutine()** 一連の空のメッセージとして、Bot Service に送信するアクティビティを設定するパラメーターを渡すことによって。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="1a9ae-399">これは、ダイアログを開始するボット サービスを要求します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. <span data-ttu-id="1a9ae-400">次のコルーチンは、Bot Service に送信するアクティビティを構築すると呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. <span data-ttu-id="1a9ae-401">次のコルーチンがアクティビティ ボット サービスに送信される応答を要求すると呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. <span data-ttu-id="1a9ae-402">シーン内のメッセージを表示するには、このクラスは、追加する最後のメソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="1a9ae-403">見つからない場合の Unity エディターのコンソール内でエラーが生じる、 **SceneOrganiser**クラス。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="1a9ae-404">チュートリアルの後半でこのクラスを作成すると、このメッセージを無視してください。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="1a9ae-405">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="1a9ae-406">第 11 章 – 相互作用クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="1a9ae-407">作成しようとするクラスを今すぐ呼びます**の相互作用**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="1a9ae-408">このクラスは、ユーザーから、HoloLens をタップして入力を検出するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="1a9ae-409">見ながら、ユーザーがタップした場合、*ボット*ボット、シーン内のオブジェクトが音声入力をリッスンする準備ができて、ボットのオブジェクトが色を変更**赤い**および音声入力のリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="1a9ae-410">このクラスから継承、 **GazeInput**クラス、およびそのため、参照できるように、 **Start()** メソッドと変数を使用して示される、そのクラスから**基本**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="1a9ae-411">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-411">To create this class:</span></span>

1.  <span data-ttu-id="1a9ae-412">ダブルクリックして、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="1a9ae-413">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="1a9ae-414">スクリプトの名前**の相互作用**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="1a9ae-415">Visual Studio で開くことに新しいスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="1a9ae-416">名前空間と同一の上部にある、次のようにするクラスの継承を更新、**の相互作用**クラス。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="1a9ae-417">内で、**の相互作用**クラスは、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="1a9ae-418">追加し、 **Start()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-418">Then add the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="1a9ae-419">ユーザーは、HoloLens のカメラの前に、タップ ジェスチャを実行するときにトリガーされるハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. <span data-ttu-id="1a9ae-420">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="1a9ae-421">第 12 章 – SceneOrganiser クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="1a9ae-422">このラボで必要な最後のクラスと呼びます**SceneOrganiser**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="1a9ae-423">このクラスは、メイン カメラをコンポーネントとスクリプトを追加し、シーン内の適切なオブジェクトを作成するプログラムでは、シーンがセットアップされます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="1a9ae-424">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-424">To create this class:</span></span>

1.  <span data-ttu-id="1a9ae-425">ダブルクリックして、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="1a9ae-426">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="1a9ae-427">スクリプトの名前**SceneOrganiser**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="1a9ae-428">Visual Studio で開くことに新しいスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="1a9ae-429">内で、 **SceneOrganiser**クラスは、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  <span data-ttu-id="1a9ae-430">追加し、 **Awake()** と**Start()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-430">Then add the **Awake()** and **Start()** methods:</span></span>

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  <span data-ttu-id="1a9ae-431">シーンでボット オブジェクトを作成し、パラメーターとコンポーネントを設定する責任を負いますの次のメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  <span data-ttu-id="1a9ae-432">ボットからの応答を表す、シーン内の UI オブジェクトの作成を担当する次のメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  <span data-ttu-id="1a9ae-433">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="1a9ae-434">Unity エディターで、ドラッグ、 **SceneOrganiser** Main Camera をスクリプト フォルダーのスクリプト。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="1a9ae-435">シーンの開催者のコンポーネントは、次の図に示すようにようになりました、Main Camera オブジェクトに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="1a9ae-437">ビルド前に第 13 章</span><span class="sxs-lookup"><span data-stu-id="1a9ae-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="1a9ae-438">アプリケーションの徹底的なテストを実行するには、必要がありますをサイドロードすること、HoloLens にします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="1a9ae-439">実行する前にいることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="1a9ae-440">説明されているすべての設定、 [**第 4 章**](#Chapter-4-–-Set-up-the-unity-project)が正しく設定されています。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-440">All the settings mentioned in the [**Chapter 4**](#Chapter-4-–-Set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="1a9ae-441">スクリプト**SceneOrganiser**にアタッチされて、 **Main Camera**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="1a9ae-442">**ボット**クラスを挿入したかどうかを確認、**ボットのシークレット キー**に、 **botSecret**変数。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="1a9ae-443">第 14 章 – ビルドと、HoloLens へのサイドロード</span><span class="sxs-lookup"><span data-stu-id="1a9ae-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="1a9ae-444">このプロジェクトの Unity のセクションの必要なすべてが今すぐ完了したら、ので、Unity から構築するための時間。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="1a9ae-445">移動します**ビルド設定**、**ファイル > の設定を作成しています.**.</span><span class="sxs-lookup"><span data-stu-id="1a9ae-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="1a9ae-446">**Build Settings**ウィンドウで、をクリックして**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Unity からのアプリの構築](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="1a9ae-448">まだ行っていない場合、ティック**UnityC#プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="1a9ae-449">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-449">Click **Build**.</span></span> <span data-ttu-id="1a9ae-450">Unity を起動、**ファイル エクスプ ローラー**ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="1a9ae-451">ここで、そのフォルダーを作成し、名前**アプリ**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="1a9ae-452">使用し、**アプリ**フォルダーを選択すると、クリックして**フォルダーの選択**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="1a9ae-453">Unity にプロジェクトをビルドを開始、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="1a9ae-454">1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="1a9ae-455">HoloLens に章 – 15 をデプロイします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="1a9ae-456">HoloLens の展開。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="1a9ae-457">必要になります、HoloLens の IP アドレス (リモート) を展開し、HoloLens をことを確認するには**開発者モード**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="1a9ae-458">これには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-458">To do this:</span></span>

    1. <span data-ttu-id="1a9ae-459">ソックスを着けずに、HoloLens 中を開く、**設定**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="1a9ae-460">移動して**ネットワークとインターネット > Wi-fi > 詳細オプション**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="1a9ae-461">注、 **IPv4**アドレス。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="1a9ae-462">次に移動します**設定**、し**更新とセキュリティ > 開発者向け**</span><span class="sxs-lookup"><span data-stu-id="1a9ae-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="1a9ae-463">開発者モードを設定します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="1a9ae-464">新しい Unity ビルドに移動します (、**アプリ**フォルダー) とソリューション ファイルを開くと**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="1a9ae-465">**ソリューション構成**選択**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="1a9ae-466">**ソリューション プラットフォーム**、 **x86**、**リモート マシン**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="1a9ae-468">移動して、**ビルド メニューの** をクリック**ソリューションの配置**サイドロード、HoloLens をアプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="1a9ae-469">アプリが、起動する準備ができて、HoloLens にインストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="1a9ae-470">イマーシブ ヘッドセットを展開するには、設定、**ソリューション プラットフォーム**に*ローカル マシン*、設定と、**構成**に*デバッグ*で*x86*として、**プラットフォーム**します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="1a9ae-471">ローカルにデプロイし、machine を使用して、**ビルド メニューの**選択*ソリューションの配置*します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="1a9ae-472">第 16 章 –、HoloLens でアプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="1a9ae-473">アプリケーションを起動するとする前にある青い球としてボットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="1a9ae-474">使用して、**タップ ジェスチャ**メッセージ交換を開始する球体に gazing は中です。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="1a9ae-475">メッセージ交換を開始するまで待ちます (UI メッセージが表示されます、そのような場合)。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="1a9ae-476">ボットから最初のメッセージが表示されたら、もう一度タップ ボットで赤に変わり、音声にリッスンするように開始されます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="1a9ae-477">通信を停止して、ボットに、メッセージの送信は、アプリケーション UI に表示される応答が迅速に届きます。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="1a9ae-478">(たびにメッセージを送信する をタップする必要がある)、ボットにより多くのメッセージを送信するプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="1a9ae-479">このメッセージ交換では、ボットが (名)、情報を保持する方法を示します (在庫品目) などの既知の情報も提供中です。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="1a9ae-480">ボットに質問をいくつかの質問には:</span><span class="sxs-lookup"><span data-stu-id="1a9ae-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="1a9ae-481">完成した Web App Bot (v4) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="1a9ae-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="1a9ae-482">これで、Azure Web App Bot、Microsoft Bot Framework v4 を利用している mixed reality アプリを構築します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![最終的な製品](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="1a9ae-484">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="1a9ae-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="1a9ae-485">手順 1</span><span class="sxs-lookup"><span data-stu-id="1a9ae-485">Exercise 1</span></span>

<span data-ttu-id="1a9ae-486">このラボでは、メッセージ交換の構造は非常に基本的なです。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="1a9ae-487">Microsoft LUIS を使用して、お客様のボットに自然言語理解機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="1a9ae-488">手順 2</span><span class="sxs-lookup"><span data-stu-id="1a9ae-488">Exercise 2</span></span>

<span data-ttu-id="1a9ae-489">この例は、メッセージ交換を終了して、新しいものを再起動するには含まれません。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="1a9ae-490">ボットの機能を完了するために、メッセージ交換をクロージャを実装するためにしてください。</span><span class="sxs-lookup"><span data-stu-id="1a9ae-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
