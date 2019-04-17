---
title: MR と Azure 302b - Custom vision
description: 機械学習モデルをトレーニングする方法については、このコースを完了し、トレーニング済みモデルを使用して、複合現実のアプリケーション内で類似のオブジェクトを認識します。
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、カスタム ビジョン、没入型、hololens、vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600001"
---
>[!NOTE]
><span data-ttu-id="03204-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="03204-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="03204-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="03204-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="03204-106">これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="03204-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="03204-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="03204-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="03204-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="03204-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="03204-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="03204-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="03204-110">MR と Azure 302b:カスタム ビジョン</span><span class="sxs-lookup"><span data-stu-id="03204-110">MR and Azure 302b: Custom vision</span></span>

<span data-ttu-id="03204-111">このコースでは複合現実のアプリケーションで Azure の Custom Vision 機能を使用して、指定されたイメージ内でカスタム ビジュアルのコンテンツを認識する方法については。</span><span class="sxs-lookup"><span data-stu-id="03204-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="03204-112">このサービスを使用して、オブジェクトのイメージを使用して機械学習モデルのトレーニングにはできます。</span><span class="sxs-lookup"><span data-stu-id="03204-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="03204-113">Microsoft HoloLens または没入型の (VR) ヘッドセットの PC に接続されているカメラのカメラ キャプチャによって提供される、類似のオブジェクトを認識するのにトレーニング済みモデルを使用するされます。</span><span class="sxs-lookup"><span data-stu-id="03204-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![コースの結果](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="03204-115">Azure の Custom Vision には、Microsoft の Cognitive サービスにより、カスタム イメージ分類モデルを構築する開発者ですが。</span><span class="sxs-lookup"><span data-stu-id="03204-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="03204-116">これらの分類モデルを認識して新しいイメージで、使用するまたは、その新しいイメージ内のオブジェクトを分類します。</span><span class="sxs-lookup"><span data-stu-id="03204-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="03204-117">サービスは、プロセスを合理化するシンプルで使いやすい、オンライン ポータルを提供します。</span><span class="sxs-lookup"><span data-stu-id="03204-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="03204-118">詳細については、次を参照してください。、 [Azure Custom Vision Service ページ](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)します。</span><span class="sxs-lookup"><span data-stu-id="03204-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="03204-119">このコースの完了したら、2 つのモードで動作できる必要が複合現実のアプリケーションが用意されます。</span><span class="sxs-lookup"><span data-stu-id="03204-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="03204-120">**分析モード**: Custom Vision Service 手動でセットアップ イメージをアップロードし、タグを作成し、トレーニング、サービスによって (このケースのマウスとキーボード) のさまざまなオブジェクトを認識します。</span><span class="sxs-lookup"><span data-stu-id="03204-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="03204-121">後は、カメラを使用してイメージをキャプチャし、現実の世界でこれらのオブジェクトを認識する HoloLens アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="03204-122">**トレーニング モード**: は、アプリで「トレーニング モード」は有効にするコードを実装します。</span><span class="sxs-lookup"><span data-stu-id="03204-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="03204-123">トレーニング モードを使用すると、HoloLens のカメラを使用してイメージをキャプチャ、キャプチャしたイメージをサービスにアップロードし、カスタム ビジョン モデルをトレーニングできます。</span><span class="sxs-lookup"><span data-stu-id="03204-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="03204-124">このコースでは、Custom Vision Service から Unity に基づくサンプル アプリケーションに結果を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="03204-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="03204-125">最大をカスタム アプリケーションをビルドしている場合にこれらの概念を適用することがあります。</span><span class="sxs-lookup"><span data-stu-id="03204-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="03204-126">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="03204-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="03204-127">コース</span><span class="sxs-lookup"><span data-stu-id="03204-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="03204-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="03204-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="03204-129"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="03204-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="03204-130">MR と Azure 302b:カスタム ビジョン</span><span class="sxs-lookup"><span data-stu-id="03204-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="03204-131">✔️</span><span class="sxs-lookup"><span data-stu-id="03204-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="03204-132">✔️</span><span class="sxs-lookup"><span data-stu-id="03204-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="03204-133">このコースは、HoloLens で主にフォーカスします、Windows Mixed Reality 没入型 (VR) ヘッドセットには、このコースで学習する内容を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="03204-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="03204-134">(VR) のイマーシブ ヘッドセットはアクセス可能な cameras があるないため、外部のカメラを PC に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="03204-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="03204-135">コースを実行するとき、没入型の (VR) ヘッドセットをサポートするために使用する必要があります変更でノートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03204-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="03204-136">前提条件</span><span class="sxs-lookup"><span data-stu-id="03204-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="03204-137">このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。</span><span class="sxs-lookup"><span data-stu-id="03204-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="03204-138">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 7 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="03204-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="03204-139">内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)にする必要がありますが想定されていなかったことについては、このコースでとまったく同じで記載されているものよりも新しいソフトウェアで表示されますが、記事以下に。</span><span class="sxs-lookup"><span data-stu-id="03204-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="03204-140">次のハードウェアとソフトウェアこのコースをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="03204-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="03204-141">開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発</span><span class="sxs-lookup"><span data-stu-id="03204-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="03204-142">Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="03204-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="03204-143">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="03204-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="03204-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="03204-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="03204-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="03204-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="03204-146">A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効</span><span class="sxs-lookup"><span data-stu-id="03204-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="03204-147">(イマーシブ ヘッドセット開発) は、PC に接続されているカメラ</span><span class="sxs-lookup"><span data-stu-id="03204-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="03204-148">Azure のセットアップおよび Custom Vision API 取得するためのインターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="03204-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="03204-149">一連の少なくとも 5 (5) イメージ (10 (10) を推奨) を認識する Custom Vision Service を希望するオブジェクトごとにします。</span><span class="sxs-lookup"><span data-stu-id="03204-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="03204-150">使用することができる場合は、 [(コンピューターのマウスとキーボード) は、このコースで既に提供されているイメージ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)します。</span><span class="sxs-lookup"><span data-stu-id="03204-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="03204-151">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="03204-151">Before you start</span></span>

1.  <span data-ttu-id="03204-152">このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。</span><span class="sxs-lookup"><span data-stu-id="03204-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="03204-153">設定して、HoloLens をテストします。</span><span class="sxs-lookup"><span data-stu-id="03204-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="03204-154">場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。</span><span class="sxs-lookup"><span data-stu-id="03204-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="03204-155">(場合によって役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときに、調整とセンサーのチューニングを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="03204-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="03204-156">調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。</span><span class="sxs-lookup"><span data-stu-id="03204-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="03204-157">センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。</span><span class="sxs-lookup"><span data-stu-id="03204-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="03204-158">第 1 章 - Custom Vision Service ポータル</span><span class="sxs-lookup"><span data-stu-id="03204-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="03204-159">使用する、 *Custom Vision Service* Azure では、アプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03204-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="03204-160">最初に、[に移動し、 *Custom Vision Service*メイン ページ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)します。</span><span class="sxs-lookup"><span data-stu-id="03204-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="03204-161">**[Get Started]** (開始) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="03204-161">Click on the **Get Started** button.</span></span>

    ![](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="03204-162">サインイン、 *Custom Vision Service*ポータル。</span><span class="sxs-lookup"><span data-stu-id="03204-162">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="03204-163">Azure アカウントがいない場合は、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03204-163">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="03204-164">クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="03204-164">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="03204-165">求められます初めてログインした後、*サービス利用規約*パネル。</span><span class="sxs-lookup"><span data-stu-id="03204-165">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="03204-166">条項に同意する チェック ボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="03204-166">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="03204-167">をクリックして**同意**します。</span><span class="sxs-lookup"><span data-stu-id="03204-167">Then click on **I agree**.</span></span>

    ![](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="03204-168">条項に同意したことに移動する、*プロジェクト*ポータルのセクション。</span><span class="sxs-lookup"><span data-stu-id="03204-168">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="03204-169">をクリックして**新しいプロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="03204-169">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="03204-170">プロジェクトの一部のフィールドを指定するように求められますが、右側にあるタブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03204-170">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="03204-171">挿入、*名前*プロジェクト用。</span><span class="sxs-lookup"><span data-stu-id="03204-171">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="03204-172">挿入、*説明*プロジェクト用 (*省略可能な*)。</span><span class="sxs-lookup"><span data-stu-id="03204-172">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="03204-173">選択、*リソース グループ*か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-173">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="03204-174">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="03204-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="03204-175">勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。</span><span class="sxs-lookup"><span data-stu-id="03204-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="03204-176">設定、*プロジェクトの種類*に**分類**</span><span class="sxs-lookup"><span data-stu-id="03204-176">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="03204-177">設定、*ドメイン*として**全般**します。</span><span class="sxs-lookup"><span data-stu-id="03204-177">Set the *Domains* as **General**.</span></span>

        ![](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="03204-178">詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="03204-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="03204-179">をクリックしたら後、**プロジェクトの作成**、Custom Vision Service で、プロジェクトのページにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="03204-179">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="03204-180">第 2 章 – Custom Vision プロジェクトのトレーニング</span><span class="sxs-lookup"><span data-stu-id="03204-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="03204-181">1 回、Custom Vision ポータルの主な目的はイメージ内の特定のオブジェクトを認識するようにプロジェクトのトレーニングには。</span><span class="sxs-lookup"><span data-stu-id="03204-181">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="03204-182">イメージには少なくとも 5 つ (5) 必要がありますが 10 (10) が、アプリケーションを認識したい各オブジェクトで、優先されます。</span><span class="sxs-lookup"><span data-stu-id="03204-182">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="03204-183">[(コンピューターのマウスとキーボード) は、このコースで提供されるイメージを使用する](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)します。</span><span class="sxs-lookup"><span data-stu-id="03204-183">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="03204-184">Custom Vision Service プロジェクトのトレーニング。</span><span class="sxs-lookup"><span data-stu-id="03204-184">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="03204-185">をクリックして、 **+** 横に**タグ。**</span><span class="sxs-lookup"><span data-stu-id="03204-185">Click on the **+** button next to **Tags.**</span></span>

    ![](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="03204-186">追加、**名前**オブジェクトを認識したいのです。</span><span class="sxs-lookup"><span data-stu-id="03204-186">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="03204-187">をクリックして**保存**します。</span><span class="sxs-lookup"><span data-stu-id="03204-187">Click on **Save**.</span></span>

    ![](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="03204-188">**タグ**が追加されました (表示するページを再読み込みする必要があります)。</span><span class="sxs-lookup"><span data-stu-id="03204-188">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="03204-189">チェックされていない場合は、新しいタグと共にチェック ボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="03204-189">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="03204-190">をクリックして**の画像の追加**ページの中央にします。</span><span class="sxs-lookup"><span data-stu-id="03204-190">Click on **Add Images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="03204-191">をクリックして**ローカル ファイルを参照**を検索し、最小の中で、アップロードするイメージを選択します。 5 (5)。</span><span class="sxs-lookup"><span data-stu-id="03204-191">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="03204-192">これらのイメージはすべてトレーニングは、オブジェクトを含める必要がありますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="03204-192">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="03204-193">一度にアップロードするいくつかのイメージを選択できます。</span><span class="sxs-lookup"><span data-stu-id="03204-193">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="03204-194">該当するタグを選択 タブで、イメージを確認できます、**マイ タグ**ボックス。</span><span class="sxs-lookup"><span data-stu-id="03204-194">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="03204-195">をクリックして**ファイルをアップロード**します。</span><span class="sxs-lookup"><span data-stu-id="03204-195">Click on **Upload files**.</span></span> <span data-ttu-id="03204-196">ファイル アップロードが開始されます。</span><span class="sxs-lookup"><span data-stu-id="03204-196">The files will begin uploading.</span></span> <span data-ttu-id="03204-197">アップロードの確認したら、クリックして**完了**します。</span><span class="sxs-lookup"><span data-stu-id="03204-197">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="03204-198">新たに作成するのと同じプロセスを繰り返します**タグ**という名前の**キーボード**の適切な写真をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="03204-198">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="03204-199">必ず\**をオフに\*\*\*マウス*を表示するために、新しいタグを作成したら、*イメージを追加*ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="03204-199">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="03204-200">両方のタグを設定したら、クリックして**トレーニング**、最初のトレーニングのイテレーションを始めましょう。</span><span class="sxs-lookup"><span data-stu-id="03204-200">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="03204-201">ビルドされたらという 2 つのボタンを表示できるが**既定**と**予測 URL**します。</span><span class="sxs-lookup"><span data-stu-id="03204-201">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="03204-202">をクリックして**既定**でクリックし、最初に、**予測 URL**します。</span><span class="sxs-lookup"><span data-stu-id="03204-202">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="03204-203">ここから、提供されているエンドポイントの URL どちらに設定されて*イテレーション*が既定としてマークされました。</span><span class="sxs-lookup"><span data-stu-id="03204-203">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="03204-204">このため、後で行った場合、新しい*イテレーション*と既定値として更新して、コードを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="03204-204">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="03204-205">クリックすると*予測 URL*開き、*メモ帳*、コピーして貼り付け、 **URL**と**予測キー**できるように、コードの後半で必要なときに取得します。</span><span class="sxs-lookup"><span data-stu-id="03204-205">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="03204-206">をクリックして、**歯車**上部にある画面の右。</span><span class="sxs-lookup"><span data-stu-id="03204-206">Click on the **Cog** at the top right of the screen.</span></span>

    ![](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="03204-207">コピー、**トレーニング キー**貼り付けます、*メモ帳*、後で使用します。</span><span class="sxs-lookup"><span data-stu-id="03204-207">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="03204-208">コピーも、**プロジェクト Id**に貼り付けることも、*メモ帳*ファイルは、後で使用します。</span><span class="sxs-lookup"><span data-stu-id="03204-208">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="03204-209">第 3 章 - Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="03204-209">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="03204-210">次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。</span><span class="sxs-lookup"><span data-stu-id="03204-210">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="03204-211">開いている*Unity*クリック**新規**します。</span><span class="sxs-lookup"><span data-stu-id="03204-211">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="03204-212">これで、Unity プロジェクトの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03204-212">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="03204-213">挿入**AzureCustomVision します。**</span><span class="sxs-lookup"><span data-stu-id="03204-213">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="03204-214">必ず、プロジェクト テンプレートに設定されて**3D**します。</span><span class="sxs-lookup"><span data-stu-id="03204-214">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="03204-215">設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。</span><span class="sxs-lookup"><span data-stu-id="03204-215">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="03204-216">をクリックし、**プロジェクトの作成**です。</span><span class="sxs-lookup"><span data-stu-id="03204-216">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="03204-217">既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="03204-217">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="03204-218">移動して**編集* > *設定** し、新しいウィンドウに移動**外部ツール**します。</span><span class="sxs-lookup"><span data-stu-id="03204-218">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="03204-219">変更**External Script Editor**に**Visual Studio 2017**します。</span><span class="sxs-lookup"><span data-stu-id="03204-219">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="03204-220">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="03204-220">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="03204-221">次に移動**ファイル > Build Settings**を選択し、**ユニバーサル Windows プラットフォーム**、をクリックして、**スイッチ プラットフォーム**選択内容を適用するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="03204-221">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="03204-222">**ファイル > Build Settings**ことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="03204-222">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="03204-223">**デバイスを対象に**に設定されている**Hololens**</span><span class="sxs-lookup"><span data-stu-id="03204-223">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="03204-224">イマーシブ ヘッドセット、設定**ターゲット デバイス**に*任意のデバイス*します。</span><span class="sxs-lookup"><span data-stu-id="03204-224">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="03204-225">**ビルドの種類**に設定されている**D3D**</span><span class="sxs-lookup"><span data-stu-id="03204-225">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="03204-226">**SDK**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="03204-226">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="03204-227">**Visual Studio バージョン**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="03204-227">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="03204-228">**ビルドおよび実行**に設定されている**ローカル マシン**</span><span class="sxs-lookup"><span data-stu-id="03204-228">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="03204-229">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="03204-229">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="03204-230">これには、選択**開くシーンを追加**します。</span><span class="sxs-lookup"><span data-stu-id="03204-230">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="03204-231">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03204-231">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="03204-232">新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="03204-232">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="03204-233">新たに作成した開く**シーン**フォルダー、し、*ファイル名:* テキスト フィールドに「 **CustomVisionScene**、[] をクリック**保存**。</span><span class="sxs-lookup"><span data-stu-id="03204-233">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="03204-234">注意してください、内の Unity シーンを保存する必要があります、*資産*フォルダー、Unity プロジェクトに関連付けられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="03204-234">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="03204-235">Unity プロジェクトの構造の一般的な方法は、シーン フォルダー (およびその他の同様のフォルダー) を作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-235">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="03204-236">設定に残っている*Build Settings*、ここでは既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="03204-236">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="03204-237">*Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。</span><span class="sxs-lookup"><span data-stu-id="03204-237">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="03204-238">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03204-238">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="03204-239">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="03204-239">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="03204-240">**ランタイム バージョンをスクリプト**する必要があります**試験的 (.NET 4.6 Equivalent)** エディターを再起動する必要があるします。</span><span class="sxs-lookup"><span data-stu-id="03204-240">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="03204-241">**バックエンドの scripting**べき **.NET**</span><span class="sxs-lookup"><span data-stu-id="03204-241">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="03204-242">**API の互換性レベル**べき **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="03204-242">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="03204-243">内で、**発行の設定**] タブの [**機能**、確認してください。</span><span class="sxs-lookup"><span data-stu-id="03204-243">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="03204-244">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="03204-244">**InternetClient**</span></span>

        2.  <span data-ttu-id="03204-245">**Web カメラ**</span><span class="sxs-lookup"><span data-stu-id="03204-245">**Webcam**</span></span>

        3. <span data-ttu-id="03204-246">**マイク**</span><span class="sxs-lookup"><span data-stu-id="03204-246">**Microphone**</span></span>

        ![](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="03204-247">パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。</span><span class="sxs-lookup"><span data-stu-id="03204-247">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="03204-248">戻り*Build Settings* *Unity C\#プロジェクト*が不要になったグレー; これの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="03204-248">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="03204-249">ビルド設定ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="03204-249">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="03204-250">シーンとプロジェクトを保存 (**ファイル > SAVE SCENE/ファイル > プロジェクトの保存**)。</span><span class="sxs-lookup"><span data-stu-id="03204-250">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="03204-251">第 4 章 - Unity で Newtonsoft DLL のインポート</span><span class="sxs-lookup"><span data-stu-id="03204-251">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="03204-252">スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[302b.unitypackage MR-Azure の](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)、としてプロジェクトにインポート、 [**カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 6 章](#chapter-6---create-the-customvisionanalyser-class)します。</span><span class="sxs-lookup"><span data-stu-id="03204-252">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="03204-253">このコースの使用を要求する、 **Newtonsoft**ライブラリで、アセットに DLL として追加することができます。</span><span class="sxs-lookup"><span data-stu-id="03204-253">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="03204-254">パッケージを含む[このライブラリは、このリンクからダウンロードできます。](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)します。</span><span class="sxs-lookup"><span data-stu-id="03204-254">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="03204-255">プロジェクトに Newtonsoft ライブラリをインポートするには、このコースに付属する Unity パッケージを使用します。</span><span class="sxs-lookup"><span data-stu-id="03204-255">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="03204-256">追加、 *.unitypackage*に Unity を使用して、 **資産* > *インポート\*\*パッケージ* > *カスタム\*\*パッケージ** メニュー オプション。</span><span class="sxs-lookup"><span data-stu-id="03204-256">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="03204-257">**Unity パッケージのインポート**その pop をボックスで、(およびなど)、すべてのことを確認**プラグイン**が選択されています。</span><span class="sxs-lookup"><span data-stu-id="03204-257">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="03204-258">をクリックして、**インポート**をプロジェクトにアイテムを追加するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="03204-258">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="03204-259">移動して、 **Newtonsoft**の下のフォルダー**プラグイン**プロジェクト ビューを選び、 *Newtonsoft.Json プラグイン*します。</span><span class="sxs-lookup"><span data-stu-id="03204-259">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="03204-260">*Newtonsoft.Json プラグイン*ように選択すると、 **Any プラットフォーム**は**unchecked**、ことを確認します**WSAPlayer**も**unchecked**、 をクリックし、**適用**します。</span><span class="sxs-lookup"><span data-stu-id="03204-260">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="03204-261">これは、ファイルが正しく構成されていることを確認するだけです。</span><span class="sxs-lookup"><span data-stu-id="03204-261">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="03204-262">これらのプラグインをマークする Unity エディターでのみ使用することを構成します。</span><span class="sxs-lookup"><span data-stu-id="03204-262">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="03204-263">これらのプロジェクトは Unity からエクスポートした後に使用される、WSA フォルダー内の異なるセットがあります。</span><span class="sxs-lookup"><span data-stu-id="03204-263">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="03204-264">次を開く必要があります、 **WSA**フォルダー内で、 **Newtonsoft**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="03204-264">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="03204-265">構成した同じファイルのコピーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03204-265">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="03204-266">ファイルを選択し、インスペクターのことを確認します</span><span class="sxs-lookup"><span data-stu-id="03204-266">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="03204-267">**任意のプラットフォーム**は**オフ**</span><span class="sxs-lookup"><span data-stu-id="03204-267">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="03204-268">**のみ** **WSAPlayer**は**チェック**</span><span class="sxs-lookup"><span data-stu-id="03204-268">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="03204-269">**処理されないように**は**チェック**</span><span class="sxs-lookup"><span data-stu-id="03204-269">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="03204-270">第 5 章 - カメラのセットアップ</span><span class="sxs-lookup"><span data-stu-id="03204-270">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="03204-271">[階層] パネルで、選択、 *Main Camera*します。</span><span class="sxs-lookup"><span data-stu-id="03204-271">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="03204-272">すべてのコンポーネントを参照してください。 選択すると、ができる、 *Main Camera*で、*インスペクター パネル*します。</span><span class="sxs-lookup"><span data-stu-id="03204-272">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="03204-273">*カメラ*オブジェクトを指定する必要があります**Main Camera** (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="03204-273">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="03204-274">Main Camera**タグ**に設定する必要があります**MainCamera** (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="03204-274">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="03204-275">必ず、**変換位置**に設定されている**0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="03204-275">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="03204-276">設定**フラグをクリア**に**単色**(イマーシブ ヘッドセットの無視) します。</span><span class="sxs-lookup"><span data-stu-id="03204-276">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="03204-277">設定、**バック グラウンド**、カメラの色コンポーネントを**黒、アルファ 0 (16 進コード: #00000000)** (イマーシブ ヘッドセットの無視) します。</span><span class="sxs-lookup"><span data-stu-id="03204-277">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="03204-278">第 6 章 - CustomVisionAnalyser クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-278">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="03204-279">この時点でコードを記述する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="03204-279">At this point you are ready to write some code.</span></span>

<span data-ttu-id="03204-280">開始するが、 *CustomVisionAnalyser*クラス。</span><span class="sxs-lookup"><span data-stu-id="03204-280">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="03204-281">呼び出し、 **Custom Vision Service**に示すコードで行われた以下を使用して作成、 **Custom Vision REST API**します。</span><span class="sxs-lookup"><span data-stu-id="03204-281">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="03204-282">これを使用して、実装して (ような画面が独自に実装する方法を理解するために役立ちます) この API を使用する方法が表示されます。</span><span class="sxs-lookup"><span data-stu-id="03204-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="03204-283">対応しており、Microsoft が提供する、 **Custom Vision Service SDK**をサービスを呼び出すことにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="03204-283">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="03204-284">詳細については、次を参照してください。、 [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)記事。</span><span class="sxs-lookup"><span data-stu-id="03204-284">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="03204-285">このクラスは、責任を負います。</span><span class="sxs-lookup"><span data-stu-id="03204-285">This class is responsible for:</span></span>

-   <span data-ttu-id="03204-286">バイト配列としてキャプチャされた最新のイメージを読み込んでいます。</span><span class="sxs-lookup"><span data-stu-id="03204-286">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="03204-287">バイト配列を Azure に送信する*Custom Vision Service*分析のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="03204-287">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="03204-288">JSON 文字列としての応答を受信します。</span><span class="sxs-lookup"><span data-stu-id="03204-288">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="03204-289">応答を逆シリアル化し、その結果を渡して*予測*を*SceneOrganiser*クラスは、応答の表示方法の考慮されます。</span><span class="sxs-lookup"><span data-stu-id="03204-289">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="03204-290">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-290">To create this class:</span></span>

1.  <span data-ttu-id="03204-291">右クリックし、*アセット フォルダー*内にある、*プロジェクト パネル*、順にクリックします**作成 > フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="03204-291">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="03204-292">フォルダーを呼び出す**スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="03204-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="03204-293">先ほど作成した、開くフォルダーをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="03204-293">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="03204-294">フォルダー内を右クリックし、をクリックして**作成** > **C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="03204-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="03204-295">スクリプトの名前*CustomVisionAnalyser*します。</span><span class="sxs-lookup"><span data-stu-id="03204-295">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="03204-296">ダブルクリックして、新しい*CustomVisionAnalyser*スクリプト ファイルを開く**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="03204-296">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="03204-297">次のように、ファイルの上部にある名前空間を更新します。</span><span class="sxs-lookup"><span data-stu-id="03204-297">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="03204-298">*CustomVisionAnalyser*クラスで、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="03204-298">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="03204-299">挿入することを確認、**予測キー**に、 **predictionKey**変数、および**予測エンドポイント**に、 **predictionEndpoint**変数。</span><span class="sxs-lookup"><span data-stu-id="03204-299">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="03204-300">これらをコピーした*メモ帳*コースで以前。</span><span class="sxs-lookup"><span data-stu-id="03204-300">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="03204-301">コードを**Awake()** インスタンス変数を初期化するために追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03204-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="03204-302">メソッドを削除**Start()** と**Update()** します。</span><span class="sxs-lookup"><span data-stu-id="03204-302">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="03204-303">コルーチンを次に、追加 (静的で**GetImageAsByteArray()** 下にあるメソッド)、によってキャプチャされたイメージの分析の結果を取得するが、 *ImageCapture*クラス。</span><span class="sxs-lookup"><span data-stu-id="03204-303">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="03204-304">**AnalyseImageCapture**コルーチンへの呼び出しがある、 *SceneOrganiser*クラスを作成することはまだです。</span><span class="sxs-lookup"><span data-stu-id="03204-304">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="03204-305">そのため、**は省略します線は、ここではコメント**します。</span><span class="sxs-lookup"><span data-stu-id="03204-305">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  <span data-ttu-id="03204-306">変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="03204-306">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="03204-307">7 - 章 CustomVisionObjects クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-307">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="03204-308">クラスの作成はここでは、 *CustomVisionObjects*クラス。</span><span class="sxs-lookup"><span data-stu-id="03204-308">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="03204-309">このスクリプトにはへの呼び出しを逆シリアル化およびシリアル化する他のクラスによって使用されるオブジェクト数が含まれています、 *Custom Vision Service*します。</span><span class="sxs-lookup"><span data-stu-id="03204-309">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="03204-310">として、Custom Vision Service が提供するエンドポイントをメモしてを実行することが重要では、次の JSON 構造体がされている設定を使用する[ *Custom Vision 予測 v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)します。</span><span class="sxs-lookup"><span data-stu-id="03204-310">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="03204-311">別のバージョンがあれば、更新する必要があります、以下の構造体。</span><span class="sxs-lookup"><span data-stu-id="03204-311">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="03204-312">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-312">To create this class:</span></span>

1.  <span data-ttu-id="03204-313">内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="03204-313">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="03204-314">スクリプトを呼び出す*CustomVisionObjects*します。</span><span class="sxs-lookup"><span data-stu-id="03204-314">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="03204-315">ダブルクリックして、新しい**CustomVisionObjects**スクリプト ファイルを開く**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="03204-315">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="03204-316">ファイルの先頭には、次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="03204-316">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="03204-317">削除、 **Start()** と**Update()** 内のメソッド、 *CustomVisionObjects*クラスです。 このクラスを空にする必要がありますするようになりました。</span><span class="sxs-lookup"><span data-stu-id="03204-317">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="03204-318">次のクラスを追加**外**、 *CustomVisionObjects*クラス。</span><span class="sxs-lookup"><span data-stu-id="03204-318">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="03204-319">これらのオブジェクトを使って、 *Newtonsoft*および応答データを逆シリアル化するライブラリ。</span><span class="sxs-lookup"><span data-stu-id="03204-319">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="03204-320">8 - 章 VoiceRecognizer クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-320">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="03204-321">このクラスは、ユーザーからの音声入力を認識します。</span><span class="sxs-lookup"><span data-stu-id="03204-321">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="03204-322">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-322">To create this class:</span></span>

1.  <span data-ttu-id="03204-323">内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="03204-323">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="03204-324">スクリプトを呼び出す*VoiceRecognizer*します。</span><span class="sxs-lookup"><span data-stu-id="03204-324">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="03204-325">ダブルクリックして、新しい**VoiceRecognizer**スクリプト ファイルを開く**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="03204-325">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="03204-326">上記の次の名前空間を追加、 *VoiceRecognizer*クラス。</span><span class="sxs-lookup"><span data-stu-id="03204-326">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="03204-327">内で、次の変数を追加し、 *VoiceRecognizer*クラス上、 *Start()* メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-327">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="03204-328">追加、 **Awake()** と**Start()** メソッド後者は、ユーザーの設定*キーワード*イメージにタグを関連付けるときに認識されるようにします。</span><span class="sxs-lookup"><span data-stu-id="03204-328">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="03204-329">削除、 **Update()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-329">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="03204-330">音声入力が認識されるたびに呼び出される次のハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="03204-330">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="03204-331">変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="03204-331">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="03204-332">心配しないでコードはこれらを修正する、すぐにそれ以上のクラスを提供すると、エラーが表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="03204-332">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="03204-333">9 - 章 CustomVisionTrainer クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-333">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="03204-334">このクラスは、一連のトレーニングに web の呼び出しをチェーン、 *Custom Vision Service*します。</span><span class="sxs-lookup"><span data-stu-id="03204-334">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="03204-335">各呼び出しは、コードのすぐ上に詳しく説明されます。</span><span class="sxs-lookup"><span data-stu-id="03204-335">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="03204-336">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-336">To create this class:</span></span>

1.  <span data-ttu-id="03204-337">内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="03204-337">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="03204-338">スクリプトを呼び出す*CustomVisionTrainer*します。</span><span class="sxs-lookup"><span data-stu-id="03204-338">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="03204-339">ダブルクリックして、新しい*CustomVisionTrainer*スクリプト ファイルを開く**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="03204-339">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="03204-340">上記の次の名前空間を追加、 *CustomVisionTrainer*クラス。</span><span class="sxs-lookup"><span data-stu-id="03204-340">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="03204-341">内で、次の変数を追加し、 *CustomVisionTrainer*クラス上、 **Start()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-341">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="03204-342">ここで使用するトレーニングの URL は用意されている、 *Custom Vision トレーニング 1.2*ドキュメントの構造体であり。 https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="03204-342">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="03204-343">詳細については、次を参照してください。、 [ *v1.2 リファレンスの Custom Vision トレーニング API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)します。</span><span class="sxs-lookup"><span data-stu-id="03204-343">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="03204-344">Custom Vision Service を提供するトレーニング モードで使用する JSON 構造体としてエンドポイントをメモしてを実行することが重要になります (内で、 **CustomVisionObjects**クラス) を使用するように設定されている[ *Custom Vision トレーニング v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)します。</span><span class="sxs-lookup"><span data-stu-id="03204-344">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="03204-345">別のバージョンがあれば、更新する必要があります、*オブジェクト*構造体。</span><span class="sxs-lookup"><span data-stu-id="03204-345">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="03204-346">追加することを確認、**サービス キー** (トレーニング キー) の値と**プロジェクト Id**値、以前書き留めておいたこれらは、値を[コース (前のポータルから収集された。第 2 章の手順 10 以降)](#chapter-2---training-your-custom-vision-oroject)します。</span><span class="sxs-lookup"><span data-stu-id="03204-346">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-oroject).</span></span>

5.  <span data-ttu-id="03204-347">次の追加**Start()** と**Awake()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-347">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="03204-348">これらのメソッドは、初期化時にと呼ばれ、UI を設定する呼び出しを含めます。</span><span class="sxs-lookup"><span data-stu-id="03204-348">Those methods are called on initialization and contain the call to set up the UI:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="03204-349">削除、 **Update()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-349">Delete the **Update()** method.</span></span> <span data-ttu-id="03204-350">このクラスでは、その必要はありません。</span><span class="sxs-lookup"><span data-stu-id="03204-350">This class will not need it.</span></span>

7.  <span data-ttu-id="03204-351">追加、 **RequestTagSelection()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-351">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="03204-352">このメソッドは、最初のイメージがキャプチャされ、デバイスに格納されているときに呼び出されるし、提出する準備ができて、 *Custom Vision Service*、トレーニングします。</span><span class="sxs-lookup"><span data-stu-id="03204-352">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="03204-353">このメソッドの場合、トレーニング、UI、ユーザーが、キャプチャしたイメージにタグ付けに使用できるキーワードのセットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03204-353">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="03204-354">警告、 *VoiceRecognizer*クラスをユーザーに音声入力のリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="03204-354">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="03204-355">追加、 **VerifyTag()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-355">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="03204-356">このメソッドによって認識される音声入力が表示されます、 **VoiceRecognizer**クラスし、その有効性を確認し、トレーニング プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="03204-356">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="03204-357">追加、 **SubmitImageForTraining()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-357">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="03204-358">このメソッドは Custom Vision Service トレーニング プロセスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="03204-358">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="03204-359">取得するには、まず、**タグ Id**ユーザーからの検証済みの音声入力に関連付けられているサービスから。</span><span class="sxs-lookup"><span data-stu-id="03204-359">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="03204-360">**タグ Id**し、イメージと一緒にアップロードされます。</span><span class="sxs-lookup"><span data-stu-id="03204-360">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="03204-361">追加、 **TrainCustomVisionProject()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-361">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="03204-362">イメージは、送信し、タグ付けされていますが、このメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="03204-362">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="03204-363">サービスと、イメージに送信されたすべての前イメージとトレーニングは新しいイテレーションを作成しますだけアップロードします。</span><span class="sxs-lookup"><span data-stu-id="03204-363">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="03204-364">このメソッドは、新しく作成したを設定するメソッドを呼び出す、トレーニングが完了したら、**イテレーション**として**既定**分析を使用しているエンドポイントが最新のトレーニング済み反復処理するようにします。</span><span class="sxs-lookup"><span data-stu-id="03204-364">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="03204-365">追加、 **SetDefaultIteration()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-365">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="03204-366">このメソッドは、以前に作成して、トレーニング済みのイテレーションとして設定は*既定*します。</span><span class="sxs-lookup"><span data-stu-id="03204-366">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="03204-367">完了すると、このメソッドは、既存のサービスで、前のイテレーションを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03204-367">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="03204-368">このコースの作成時は、イテレーションの最大 10 数、サービスで同時に存在できるの制限があります。</span><span class="sxs-lookup"><span data-stu-id="03204-368">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="03204-369">追加、 **DeletePreviousIteration()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-369">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="03204-370">このメソッドを検索し、前の既定以外のイテレーションを削除します。</span><span class="sxs-lookup"><span data-stu-id="03204-370">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="03204-371">このクラスに追加する最後のメソッド、 **GetImageAsByteArray()** メソッド、web の呼び出しでバイト配列にキャプチャされたイメージを変換するために使用します。</span><span class="sxs-lookup"><span data-stu-id="03204-371">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. <span data-ttu-id="03204-372">変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="03204-372">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="03204-373">10 - 章 SceneOrganiser クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-373">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="03204-374">このクラスは。</span><span class="sxs-lookup"><span data-stu-id="03204-374">This class will:</span></span>

-   <span data-ttu-id="03204-375">作成、**カーソル**Main Camera にアタッチするオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="03204-375">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="03204-376">作成、**ラベル**サービスが現実世界のオブジェクトを認識しているときに表示されるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="03204-376">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="03204-377">適切なコンポーネントにアタッチすることにより、メイン カメラを設定します。</span><span class="sxs-lookup"><span data-stu-id="03204-377">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="03204-378">場合に**分析モード**、メイン カメラの位置を基準とした適切なワールド空間における、実行時にラベルを生成、および、Custom Vision Service から受信したデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="03204-378">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="03204-379">場合に**トレーニング モード**、トレーニング プロセスのさまざまな段階を表示する UI を起動します。</span><span class="sxs-lookup"><span data-stu-id="03204-379">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="03204-380">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-380">To create this class:</span></span>

1.  <span data-ttu-id="03204-381">内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="03204-381">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="03204-382">スクリプトの名前*SceneOrganiser*します。</span><span class="sxs-lookup"><span data-stu-id="03204-382">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="03204-383">ダブルクリックして、新しい*SceneOrganiser*スクリプト ファイルを開く**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="03204-383">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="03204-384">1 つの名前空間は必要がありますのみ、上記の他の削除、 *SceneOrganiser*クラス。</span><span class="sxs-lookup"><span data-stu-id="03204-384">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="03204-385">内で、次の変数を追加し、 *SceneOrganiser*クラス上、 **Start()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-385">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="03204-386">削除、 **Start()** と**Update()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-386">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="03204-387">変数の右下にある追加の**Awake()** メソッドはクラスを初期化し、シーンを設定します。</span><span class="sxs-lookup"><span data-stu-id="03204-387">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="03204-388">ここで追加、 **CreateCameraCursor()** メソッドを作成して、メイン カメラ、カーソルを配置して、 **CreateLabel()** メソッドで、作成、**分析ラベル**オブジェクト.</span><span class="sxs-lookup"><span data-stu-id="03204-388">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="03204-389">追加、 **SetCameraStatus()** メソッドで、メッセージのテキスト メッシュ、カメラの状態を提供するためのものを処理します。</span><span class="sxs-lookup"><span data-stu-id="03204-389">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="03204-390">追加、 **PlaceAnalysisLabel()** と**SetTagsToLastLabel()** メソッドが生成されをシーンに Custom Vision Service からデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="03204-390">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="03204-391">最後に、追加、 **CreateTrainingUI()** メソッドで、アプリケーションがトレーニング モードの場合、トレーニング プロセスの複数のステージを表示する UI が生成されます。</span><span class="sxs-lookup"><span data-stu-id="03204-391">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="03204-392">このメソッドは、カメラ状態オブジェクトの作成にも利用されています。</span><span class="sxs-lookup"><span data-stu-id="03204-392">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="03204-393">変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="03204-393">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="03204-394">続行する前に開いて、 **CustomVisionAnalyser**クラス内で、 **AnalyseLastImageCaptured()** メソッド、*をコメント解除します*次の行。</span><span class="sxs-lookup"><span data-stu-id="03204-394">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="03204-395">11 - 章 ImageCapture クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-395">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="03204-396">次のクラスを作成することには、 *ImageCapture*クラス。</span><span class="sxs-lookup"><span data-stu-id="03204-396">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="03204-397">このクラスは、責任を負います。</span><span class="sxs-lookup"><span data-stu-id="03204-397">This class is responsible for:</span></span>

-   <span data-ttu-id="03204-398">HoloLens のカメラを使用して、格納することでイメージのキャプチャ、*アプリ*フォルダー。</span><span class="sxs-lookup"><span data-stu-id="03204-398">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="03204-399">ユーザーからのタップ ジェスチャを処理します。</span><span class="sxs-lookup"><span data-stu-id="03204-399">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="03204-400">保守、 *Enum*かどうか、アプリケーションは実行を決定する値*Analysis*モードまたは*トレーニング*モード。</span><span class="sxs-lookup"><span data-stu-id="03204-400">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="03204-401">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03204-401">To create this class:</span></span>

1.  <span data-ttu-id="03204-402">移動して、**スクリプト**以前に作成したフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="03204-402">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="03204-403">フォルダー内を右クリックし、をクリックして**作成 > C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="03204-403">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="03204-404">スクリプトの名前*ImageCapture*します。</span><span class="sxs-lookup"><span data-stu-id="03204-404">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="03204-405">ダブルクリックして、新しい**ImageCapture**スクリプト ファイルを開く**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="03204-405">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="03204-406">次のように、ファイルの上部にある名前空間に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="03204-406">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="03204-407">内で、次の変数を追加し、 *ImageCapture*クラス上、 **Start()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="03204-407">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="03204-408">コードを**Awake()** と**Start()** 今すぐメソッドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03204-408">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="03204-409">タップ ジェスチャが発生したときに呼び出されるハンドラーを実装します。</span><span class="sxs-lookup"><span data-stu-id="03204-409">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="03204-410">*Analysis*モード、 **TapHandler**メソッドを開始または写真キャプチャのループを停止するためのスイッチとして機能します。</span><span class="sxs-lookup"><span data-stu-id="03204-410">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="03204-411">*トレーニング*モードでは、カメラからのイメージがキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="03204-411">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="03204-412">カーソルが緑色の場合、カメラは、イメージを使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="03204-412">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="03204-413">カーソルが赤の場合は、カメラがビジー状態を意味します。</span><span class="sxs-lookup"><span data-stu-id="03204-413">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="03204-414">イメージのキャプチャ プロセスを開始し、イメージを格納するアプリケーションが使用するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="03204-414">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  <span data-ttu-id="03204-415">写真をキャプチャおよび分析する準備ができ次第の呼び出されるハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="03204-415">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="03204-416">渡されますが、結果、 *CustomVisionAnalyser*または*CustomVisionTrainer*モードによって、コードに設定します。</span><span class="sxs-lookup"><span data-stu-id="03204-416">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="03204-417">変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="03204-417">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="03204-418">これで、すべてのスクリプトが完了したら、Unity エディターでは、戻ってクリックしてアンド ドラッグ、 **SceneOrganiser**クラスから、**スクリプト**フォルダーを**Main Camera**オブジェクトに、*階層パネル*します。</span><span class="sxs-lookup"><span data-stu-id="03204-418">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="03204-419">第 12 章 - ビルドの前に</span><span class="sxs-lookup"><span data-stu-id="03204-419">Chapter 12 - Before building</span></span>

<span data-ttu-id="03204-420">アプリケーションの徹底的なテストを実行するには、必要がありますをサイドロードすること、HoloLens にします。</span><span class="sxs-lookup"><span data-stu-id="03204-420">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="03204-421">実行する前にいることを確認します。</span><span class="sxs-lookup"><span data-stu-id="03204-421">Before you do, ensure that:</span></span>

- <span data-ttu-id="03204-422">説明されているすべての設定、[第 2 章](#chapter-2---training-your-custom-vision-project)が正しく設定されています。</span><span class="sxs-lookup"><span data-stu-id="03204-422">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="03204-423">内のすべてのフィールド、 **Main Camera**インスペクターのパネルが適切に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="03204-423">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="03204-424">スクリプト**SceneOrganiser**にアタッチされて、 **Main Camera**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="03204-424">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="03204-425">挿入することを確認、**予測キー**に、 **predictionKey**変数。</span><span class="sxs-lookup"><span data-stu-id="03204-425">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="03204-426">挿入した、**予測エンドポイント**に、 **predictionEndpoint**変数。</span><span class="sxs-lookup"><span data-stu-id="03204-426">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="03204-427">挿入した、**トレーニング キー**に、 **trainingKey**の変数、 *CustomVisionTrainer*クラス。</span><span class="sxs-lookup"><span data-stu-id="03204-427">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="03204-428">挿入した、**プロジェクト ID**に、 **projectId**の変数、 *CustomVisionTrainer*クラス。</span><span class="sxs-lookup"><span data-stu-id="03204-428">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="03204-429">第 13 章 - ビルドおよびサイドロード アプリ</span><span class="sxs-lookup"><span data-stu-id="03204-429">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="03204-430">開始する、*ビルド*プロセス。</span><span class="sxs-lookup"><span data-stu-id="03204-430">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="03204-431">移動して**ファイル > のビルド設定**します。</span><span class="sxs-lookup"><span data-stu-id="03204-431">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="03204-432">ティック**Unity C\#プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="03204-432">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="03204-433">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="03204-433">Click **Build**.</span></span> <span data-ttu-id="03204-434">Unity を起動、**ファイル エクスプ ローラー**ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03204-434">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="03204-435">ここで、そのフォルダーを作成し、名前**アプリ**します。</span><span class="sxs-lookup"><span data-stu-id="03204-435">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="03204-436">使用し、**アプリ**フォルダーを選択すると、クリックして**フォルダーの選択**します。</span><span class="sxs-lookup"><span data-stu-id="03204-436">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="03204-437">Unity にプロジェクトをビルドを開始、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="03204-437">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="03204-438">1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。</span><span class="sxs-lookup"><span data-stu-id="03204-438">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="03204-439">HoloLens の展開。</span><span class="sxs-lookup"><span data-stu-id="03204-439">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="03204-440">必要になります、HoloLens の IP アドレス (リモート) を展開し、HoloLens をことを確認するには**開発者モード**します。</span><span class="sxs-lookup"><span data-stu-id="03204-440">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="03204-441">これには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="03204-441">To do this:</span></span>

    1.  <span data-ttu-id="03204-442">ソックスを着けずに、HoloLens 中を開く、**設定**します。</span><span class="sxs-lookup"><span data-stu-id="03204-442">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="03204-443">移動して**ネットワークとインターネット** > **Wi-fi** > **詳細オプション**</span><span class="sxs-lookup"><span data-stu-id="03204-443">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="03204-444">注、 **IPv4**アドレス。</span><span class="sxs-lookup"><span data-stu-id="03204-444">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="03204-445">次に移動します**設定**、し**更新とセキュリティ** > **開発者向け**</span><span class="sxs-lookup"><span data-stu-id="03204-445">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="03204-446">設定**で開発者モード**します。</span><span class="sxs-lookup"><span data-stu-id="03204-446">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="03204-447">新しい Unity ビルドに移動します (、**アプリ**フォルダー) とソリューション ファイルを開くと**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="03204-447">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="03204-448">*ソリューション構成*選択**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="03204-448">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="03204-449">*ソリューション プラットフォーム*、 **x86、リモート コンピューター**します。</span><span class="sxs-lookup"><span data-stu-id="03204-449">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="03204-450">挿入を求め、 **IP アドレス**のリモート デバイス (、HoloLens、ここでは、メモしたもの)。</span><span class="sxs-lookup"><span data-stu-id="03204-450">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="03204-451">移動して**ビルド**メニューをクリックします**ソリューションの配置**サイドロード、HoloLens をアプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="03204-451">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="03204-452">アプリが、起動する準備ができて、HoloLens にインストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="03204-452">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="03204-453">イマーシブ ヘッドセットを展開するには、設定、**ソリューション プラットフォーム**に*ローカル マシン*、設定と、**構成**に*デバッグ*で*x86*として、**プラットフォーム**します。</span><span class="sxs-lookup"><span data-stu-id="03204-453">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="03204-454">ローカルにデプロイし、machine を使用して、**ビルド**メニュー項目を選択すると*ソリューションの配置*します。</span><span class="sxs-lookup"><span data-stu-id="03204-454">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="03204-455">アプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="03204-455">To use the application:</span></span>

<span data-ttu-id="03204-456">アプリの機能との間を切り替える*トレーニング*モードと*予測*モードを更新する必要がある、 **AppMode**変数にある、 **Awake()** 内にあるメソッド、 *ImageCapture*クラス。</span><span class="sxs-lookup"><span data-stu-id="03204-456">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="03204-457">または</span><span class="sxs-lookup"><span data-stu-id="03204-457">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="03204-458">*トレーニング*モード。</span><span class="sxs-lookup"><span data-stu-id="03204-458">In *Training* mode:</span></span>

- <span data-ttu-id="03204-459">見て**マウス**または**キーボード**を使用して、**タップ ジェスチャ**します。</span><span class="sxs-lookup"><span data-stu-id="03204-459">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="03204-460">次に、テキストは、タグを指定するように求める表示されます。</span><span class="sxs-lookup"><span data-stu-id="03204-460">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="03204-461">どちらか**マウス**または**キーボード**します。</span><span class="sxs-lookup"><span data-stu-id="03204-461">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="03204-462">*予測*モード。</span><span class="sxs-lookup"><span data-stu-id="03204-462">In *Prediction* mode:</span></span>

- <span data-ttu-id="03204-463">オブジェクトを確認し、使用、**タップ ジェスチャ**します。</span><span class="sxs-lookup"><span data-stu-id="03204-463">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="03204-464">検出されると、確率が最も高い (これは正規化されます) オブジェクトを提供するテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03204-464">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="03204-465">14 -」の章を評価し、カスタム ビジョン モデルを改善</span><span class="sxs-lookup"><span data-stu-id="03204-465">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="03204-466">サービスをより正確なことには、予測に使用するモデルのトレーニングに続行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03204-466">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="03204-467">両方で、新しいアプリケーションを使用して、これは、*トレーニング*と*予測*モード、後者を必要とすると、ポータルでは、この章の内容を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03204-467">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="03204-468">何度も、ポータルを見直し、モデルを継続的に向上させるために準備してください。</span><span class="sxs-lookup"><span data-stu-id="03204-468">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="03204-469">Azure Custom Vision ポータルにもう一度、head し、プロジェクトでは、選択、*予測*(からページの上部中央) タブ。</span><span class="sxs-lookup"><span data-stu-id="03204-469">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="03204-470">アプリケーションの実行中に、サービスに送信されたすべてのイメージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03204-470">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="03204-471">イメージをポイントする場合は、そのイメージに対して行われた予測の提供は。</span><span class="sxs-lookup"><span data-stu-id="03204-471">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="03204-472">イメージを開くことのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="03204-472">Select one of your images to open it.</span></span> <span data-ttu-id="03204-473">開いている場合とは、そのイメージの右側に行われた予測が表示されます。</span><span class="sxs-lookup"><span data-stu-id="03204-473">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="03204-474">予測が正しいこと、およびサービスのモデルのトレーニングにこのイメージを追加するには、をクリックした場合、*マイ タグ*入力ボックス、およびに関連付けるタグを選択します。</span><span class="sxs-lookup"><span data-stu-id="03204-474">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="03204-475">完了したら、クリックして、*を保存して閉じます*右、下にボタンをクリックし、次のイメージを続行します。</span><span class="sxs-lookup"><span data-stu-id="03204-475">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="03204-476">イメージのグリッドに表示されたら、イメージにタグを追加 (して保存した)、これが表示されますは削除されます。</span><span class="sxs-lookup"><span data-stu-id="03204-476">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="03204-477">それらに含まれるタグが付けられた、項目がないと思われる任意のイメージを検索する場合は、(ようイメージがいくつかの) そのイメージに目盛りをクリックし、をクリックして削除することは、できる*削除*グリッド ページの右上隅にします。</span><span class="sxs-lookup"><span data-stu-id="03204-477">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="03204-478">次のポップアップで、いずれかをクリックできます*はい、削除*または*いいえ*削除の確認またはキャンセルするか、それぞれをします。</span><span class="sxs-lookup"><span data-stu-id="03204-478">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="03204-479">続行する準備ができたら、緑をクリックします。*トレーニング*右上のボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="03204-479">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="03204-480">すべてのイメージと指定したようになりましたが (これによりより正確な)、サービス モデルがトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="03204-480">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="03204-481">トレーニングが完了すると作成 をクリックすることを確認して、*既定*、もう一度ボタンをクリックしてように、*予測 URL*は、サービスの最新のイテレーションを使用し続けます。</span><span class="sxs-lookup"><span data-stu-id="03204-481">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="03204-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="03204-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="03204-483">完成した Custom Vision API アプリケーション</span><span class="sxs-lookup"><span data-stu-id="03204-483">Your finished Custom Vision API application</span></span>

<span data-ttu-id="03204-484">これで、現実世界のオブジェクトを認識する、サービス モデルのトレーニングおよび内容は、発生の信頼度を表示する Azure の Custom Vision API を利用している mixed reality アプリを構築します。</span><span class="sxs-lookup"><span data-stu-id="03204-484">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="03204-485">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="03204-485">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="03204-486">手順 1</span><span class="sxs-lookup"><span data-stu-id="03204-486">Exercise 1</span></span>

<span data-ttu-id="03204-487">トレーニング、 **Custom Vision Service**を複数のオブジェクトを認識します。</span><span class="sxs-lookup"><span data-stu-id="03204-487">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="03204-488">手順 2</span><span class="sxs-lookup"><span data-stu-id="03204-488">Exercise 2</span></span>

<span data-ttu-id="03204-489">学習した内容を展開する方法、として次の演習を行います。</span><span class="sxs-lookup"><span data-stu-id="03204-489">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="03204-490">オブジェクトが認識されると、サウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="03204-490">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="03204-491">手順 3</span><span class="sxs-lookup"><span data-stu-id="03204-491">Exercise 3</span></span>

<span data-ttu-id="03204-492">API を使用して、アプリの分析は、同じイメージのサービスの再トレーニングに、そのため、サービスをより正確に (予測と同時にトレーニングを行う)。</span><span class="sxs-lookup"><span data-stu-id="03204-492">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
