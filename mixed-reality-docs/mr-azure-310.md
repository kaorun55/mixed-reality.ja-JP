---
title: MR および Azure 310 - オブジェクトの検出
description: 機械学習モデルをトレーニングする方法については、このコースを完了し、同等のオブジェクトと複合現実のアプリケーション内から現実の世界での位置を認識して、トレーニング済みモデルを使用します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure では、カスタム ビジョンは、オブジェクトの検出、実際に、アカデミー、unity、チュートリアル、api、hololens の混在
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597651"
---
>[!NOTE]
><span data-ttu-id="fb123-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fb123-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="fb123-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="fb123-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="fb123-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="fb123-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="fb123-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="fb123-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="fb123-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="fb123-110">Mr と Azure 310:オブジェクトの検出</span><span class="sxs-lookup"><span data-stu-id="fb123-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="fb123-111">このコースでは方法を学習しますカスタム ビジュアルのコンテンツと、指定されたイメージに含まれる空間位置を認識して Azure の Custom Vision を使用して、複合現実のアプリケーションでは「オブジェクトの検出」機能します。</span><span class="sxs-lookup"><span data-stu-id="fb123-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="fb123-112">このサービスを使用して、オブジェクトのイメージを使用して機械学習モデルのトレーニングにはできます。</span><span class="sxs-lookup"><span data-stu-id="fb123-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="fb123-113">Microsoft HoloLens のカメラ キャプチャによって提供される同等のオブジェクトを認識し、おおよその現実の世界での場所に、トレーニング済みモデルを使用してまたは没入型の (VR) ヘッドセットの PC にカメラを接続します。</span><span class="sxs-lookup"><span data-stu-id="fb123-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![コースの結果](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="fb123-115">**Azure の Custom Vision、オブジェクトの検出**Microsoft サービスで、開発者がカスタム イメージ分類モデルを構築します。</span><span class="sxs-lookup"><span data-stu-id="fb123-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="fb123-116">提供することで、そのイメージ内のオブジェクトを検出するために新しいイメージでこれらの分類モデルが使用しできます**ボックス境界**はイメージ自体。</span><span class="sxs-lookup"><span data-stu-id="fb123-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="fb123-117">サービスは、このプロセスを効率化のシンプルで使いやすい、オンライン ポータルを提供します。</span><span class="sxs-lookup"><span data-stu-id="fb123-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="fb123-118">詳細については、次のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb123-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="fb123-119">Azure の Custom Vision ページ</span><span class="sxs-lookup"><span data-stu-id="fb123-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="fb123-120">制限とクォータ</span><span class="sxs-lookup"><span data-stu-id="fb123-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="fb123-121">このコースを修了、以下を実行できる必要が複合現実のアプリケーションが用意されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="fb123-122">ユーザーができるようになります*視線*Azure Custom Vision Service オブジェクトの検出を使用して、トレーニングがオブジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="fb123-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="fb123-123">ユーザーが使用する、*タップ*で目的のイメージをキャプチャするジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="fb123-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="fb123-124">アプリはイメージを Azure の Custom Vision Service に送信します。</span><span class="sxs-lookup"><span data-stu-id="fb123-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="fb123-125">ワールド空間テキストとして認識の結果が表示されるサービスからの応答があります。</span><span class="sxs-lookup"><span data-stu-id="fb123-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="fb123-126">これは、Microsoft HoloLens の空間追跡、認識されているオブジェクトのワールド位置を理解して使用し、方法として利用するによって実現されますが、*タグ*イメージ内に検出された内容に関連付けられています。ラベルのテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="fb123-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="fb123-127">コースは、タグを作成、アップロードを手動でのイメージも説明し、トレーニング異なるを認識する、サービス オブジェクト (指定の例では、杯) での設定、*境界ボックス*を送信する、イメージ内で。</span><span class="sxs-lookup"><span data-stu-id="fb123-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="fb123-128">次の作成とアプリの使用、開発者する必要があります Azure の Custom Vision Service に戻るを特定、サービスによって行われた予測しかどうかが正しいかどうかを判断する (サービスを何もタグ付けによってがなくと調整、*境界ボックス*)。</span><span class="sxs-lookup"><span data-stu-id="fb123-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="fb123-129">サービス、再トレーニングできます、現実世界のオブジェクトを認識することの可能性が高くなりますが。</span><span class="sxs-lookup"><span data-stu-id="fb123-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="fb123-130">このコースでは、Azure の Custom Vision Service、オブジェクトの検出から Unity に基づくサンプル アプリケーションに結果を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="fb123-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="fb123-131">最大をカスタム アプリケーションをビルドしている場合にこれらの概念を適用することがあります。</span><span class="sxs-lookup"><span data-stu-id="fb123-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="fb123-132">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="fb123-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="fb123-133">コース</span><span class="sxs-lookup"><span data-stu-id="fb123-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="fb123-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="fb123-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="fb123-135"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="fb123-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="fb123-136">MR と Azure 310:オブジェクトの検出</span><span class="sxs-lookup"><span data-stu-id="fb123-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="fb123-137">✔️</span><span class="sxs-lookup"><span data-stu-id="fb123-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="fb123-138">前提条件</span><span class="sxs-lookup"><span data-stu-id="fb123-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="fb123-139">このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。</span><span class="sxs-lookup"><span data-stu-id="fb123-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="fb123-140">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 7 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fb123-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="fb123-141">内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)にする必要がありますが想定されていなかったことについては、このコースでとまったく同じで記載されているものよりも新しいソフトウェアで表示されますが、記事以下に。</span><span class="sxs-lookup"><span data-stu-id="fb123-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="fb123-142">次のハードウェアとソフトウェアこのコースをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fb123-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="fb123-143">開発用 PC</span><span class="sxs-lookup"><span data-stu-id="fb123-143">A development PC</span></span>
- [<span data-ttu-id="fb123-144">Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="fb123-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="fb123-145">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="fb123-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="fb123-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="fb123-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="fb123-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fb123-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="fb123-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)開発者モードが有効</span><span class="sxs-lookup"><span data-stu-id="fb123-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="fb123-149">Azure のセットアップおよび Custom Vision Service 取得するためのインターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="fb123-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="fb123-150">一連のイメージには少なくとも 15 (15) が必要です) を認識するカスタム ビジョンを希望するオブジェクトごとにします。</span><span class="sxs-lookup"><span data-stu-id="fb123-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="fb123-151">かどうかに、既にこのコースで提供されるイメージを使用する[一連の cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。</span><span class="sxs-lookup"><span data-stu-id="fb123-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="fb123-152">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="fb123-152">Before you start</span></span>

1.  <span data-ttu-id="fb123-153">このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。</span><span class="sxs-lookup"><span data-stu-id="fb123-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="fb123-154">設定して、HoloLens をテストします。</span><span class="sxs-lookup"><span data-stu-id="fb123-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="fb123-155">場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。</span><span class="sxs-lookup"><span data-stu-id="fb123-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="fb123-156">(場合によって役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときに、調整とセンサーのチューニングを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fb123-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="fb123-157">調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。</span><span class="sxs-lookup"><span data-stu-id="fb123-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="fb123-158">センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。</span><span class="sxs-lookup"><span data-stu-id="fb123-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="fb123-159">第 1 章 - Custom Vision ポータル</span><span class="sxs-lookup"><span data-stu-id="fb123-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="fb123-160">使用する、 **Azure Custom Vision Service**、そのアプリケーションに使用可能にするインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb123-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="fb123-161">移動[を**Custom Vision Service**メイン ページ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)します。</span><span class="sxs-lookup"><span data-stu-id="fb123-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="fb123-162">をクリックして**Getting Started**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="fb123-163">Custom Vision ポータルにサインインします。</span><span class="sxs-lookup"><span data-stu-id="fb123-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="fb123-164">Azure アカウントがいない場合は、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb123-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="fb123-165">クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="fb123-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="fb123-166">求められます初めてログインした後、*サービス利用規約*パネル。</span><span class="sxs-lookup"><span data-stu-id="fb123-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="fb123-167">チェック ボックスをクリックして*条項に同意*します。</span><span class="sxs-lookup"><span data-stu-id="fb123-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="fb123-168">クリックして**同意**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="fb123-169">条項に同意したこと、れるので、*マイ プロジェクト*セクション。</span><span class="sxs-lookup"><span data-stu-id="fb123-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="fb123-170">をクリックして**新しいプロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="fb123-171">プロジェクトの一部のフィールドを指定するように求められますが、右側にあるタブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="fb123-172">プロジェクトの名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="fb123-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="fb123-173">プロジェクトの説明を挿入 ( **(省略可能)** )</span><span class="sxs-lookup"><span data-stu-id="fb123-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="fb123-174">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="fb123-175">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="fb123-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="fb123-176">勧めします (例: これらのコース) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。</span><span class="sxs-lookup"><span data-stu-id="fb123-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="fb123-177">たい場合[読み取りの詳細は、Azure リソース グループの詳細については、関連付けられているドキュメントに移動します。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="fb123-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="fb123-178">設定、**プロジェクトの種類**として**オブジェクトの検出 (プレビュー)** します。</span><span class="sxs-lookup"><span data-stu-id="fb123-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="fb123-179">終了したらをクリックして**プロジェクトの作成**、し、Custom Vision Service プロジェクトのページにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="fb123-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="fb123-180">第 2 章 – Custom Vision プロジェクトのトレーニング</span><span class="sxs-lookup"><span data-stu-id="fb123-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="fb123-181">1 回、Custom Vision ポータルの主な目的はイメージ内の特定のオブジェクトを認識するようにプロジェクトのトレーニングには。</span><span class="sxs-lookup"><span data-stu-id="fb123-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="fb123-182">各オブジェクトを認識するアプリケーションを少なくとも 15 (15) イメージが必要です。</span><span class="sxs-lookup"><span data-stu-id="fb123-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="fb123-183">このコースで提供されるイメージを使用することができます ([一連の cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。</span><span class="sxs-lookup"><span data-stu-id="fb123-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="fb123-184">Custom Vision プロジェクトのトレーニング。</span><span class="sxs-lookup"><span data-stu-id="fb123-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="fb123-185">をクリックして、 **+** 横に**タグ**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="fb123-186">追加、**名前**タグのによって、イメージを関連付けるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="fb123-187">認識のため、これは、タグを付けた、カップのイメージを使用しているがこの例では**Cup**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="fb123-188">クリックして**保存**完了後します。</span><span class="sxs-lookup"><span data-stu-id="fb123-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="fb123-189">**タグ**が追加されました (表示するページを再読み込みする必要があります)。</span><span class="sxs-lookup"><span data-stu-id="fb123-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="fb123-190">をクリックして**イメージを追加**ページの中央にします。</span><span class="sxs-lookup"><span data-stu-id="fb123-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="fb123-191">をクリックして**ローカル ファイルを参照**とに 1 つのオブジェクト、15、最小されていると (15) をアップロードするイメージを参照します。</span><span class="sxs-lookup"><span data-stu-id="fb123-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="fb123-192">一度にアップロードするいくつかのイメージを選択できます。</span><span class="sxs-lookup"><span data-stu-id="fb123-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="fb123-193">キーを押して**ファイルをアップロード**トレーニングを使用してプロジェクトにするすべてのイメージを選択するとします。</span><span class="sxs-lookup"><span data-stu-id="fb123-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="fb123-194">ファイル アップロードが開始されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-194">The files will begin uploading.</span></span> <span data-ttu-id="fb123-195">アップロードの確認したら、クリックして**完了**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="fb123-196">この時点で、イメージがアップロードされるが、タグ付けされていません。</span><span class="sxs-lookup"><span data-stu-id="fb123-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="fb123-197">イメージをタグにマウスを使用します。</span><span class="sxs-lookup"><span data-stu-id="fb123-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="fb123-198">イメージをポイントするよう選択の強調表示する助けとなります、オブジェクトの周りに選択範囲を自動的に描画することで。</span><span class="sxs-lookup"><span data-stu-id="fb123-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="fb123-199">正確でない場合を描画できます独自。</span><span class="sxs-lookup"><span data-stu-id="fb123-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="fb123-200">これは、マウスの左クリックを保持していると、オブジェクトを囲むように選択した領域にドラッグすることによって実現されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="fb123-201">次のイメージ内のオブジェクトの選択、小規模なプロンプトがするように求められます*リージョン タグを追加*します。</span><span class="sxs-lookup"><span data-stu-id="fb123-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="fb123-202">以前に作成したタグ ('Cup'、上記の例では) を選択するかその他のタグを追加する場合でを入力し、をクリックして、 **+ (正符号 +)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb123-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="fb123-203">次の画像をタグ付けする、ブレードの右側にある矢印をクリックします。 または、[タグ] ブレードを閉じます (をクリックして、 **X**ブレードの右上隅にある) を次の画像をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb123-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="fb123-204">次のイメージを準備した後は、同じ手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="fb123-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="fb123-205">これまで、すべてタグ付けされている、アップロードしたすべてのイメージを行います。</span><span class="sxs-lookup"><span data-stu-id="fb123-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="fb123-206">次の図のように、同じイメージでは、いくつかのオブジェクトを選択できます。</span><span class="sxs-lookup"><span data-stu-id="fb123-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="fb123-207">それらすべてにタグが、クリックして、**タグが付けられた**タグが付けられたイメージを表示する画面の左側にボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb123-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="fb123-208">サービスをトレーニングする準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="fb123-208">You are now ready to train your Service.</span></span> <span data-ttu-id="fb123-209">をクリックして、**トレーニング**ボタン、および最初のトレーニングのイテレーションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="fb123-210">ビルドされたらという 2 つのボタンを表示できるが**既定**と**予測 URL**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="fb123-211">をクリックして**既定**でクリックし、最初に、**予測 URL**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="fb123-212">これにより、提供されているエンドポイントがどちらに設定されている*イテレーション*が既定としてマークされました。</span><span class="sxs-lookup"><span data-stu-id="fb123-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="fb123-213">このため、後で行った場合、新しい*イテレーション*と既定値として更新して、コードを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fb123-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="fb123-214">クリックすると**予測 URL**、オープン*メモ帳*、コピーして貼り付け、 **URL** (とも呼ばれます、**予測エンドポイント**)**サービス予測キー**コードの後半で必要なときに取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="fb123-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="fb123-215">第 3 章 - Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="fb123-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="fb123-216">次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。</span><span class="sxs-lookup"><span data-stu-id="fb123-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="fb123-217">開いている**Unity**クリック**新規**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="fb123-218">これで、Unity プロジェクトの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb123-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="fb123-219">挿入**CustomVisionObjDetection**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="fb123-220">必ず、プロジェクトの種類に設定されて**3D**、設定と、**場所**で該当する別の場所を (ただし、ルート ディレクトリに近づけるためのより良い)。</span><span class="sxs-lookup"><span data-stu-id="fb123-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="fb123-221">をクリックし、**プロジェクトの作成**です。</span><span class="sxs-lookup"><span data-stu-id="fb123-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="fb123-222">既定値を確認する必要が開いている Unity、 **スクリプト エディター** に設定されている **Visual Studio** します。</span><span class="sxs-lookup"><span data-stu-id="fb123-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="fb123-223">移動して **編集* > *設定** し、新しいウィンドウに移動 **外部ツール** します。</span><span class="sxs-lookup"><span data-stu-id="fb123-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="fb123-224">変更 **External Script Editor** に **Visual Studio** します。</span><span class="sxs-lookup"><span data-stu-id="fb123-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="fb123-225">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="fb123-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="fb123-226">移動して次に、**ファイル > Build Settings**スイッチと、**プラットフォーム**に*ユニバーサル Windows プラットフォーム*をクリックし、 **プラットフォームの切り替え**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb123-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="fb123-227">同じ**Build Settings**ウィンドウで、次を設定してください。</span><span class="sxs-lookup"><span data-stu-id="fb123-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="fb123-228">**デバイスを対象に**に設定されている**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="fb123-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="fb123-229">**ビルドの種類**に設定されている**D3D**</span><span class="sxs-lookup"><span data-stu-id="fb123-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="fb123-230">**SDK**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="fb123-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="fb123-231">**Visual Studio バージョン**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="fb123-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="fb123-232">**ビルドおよび実行**に設定されている**ローカル マシン**</span><span class="sxs-lookup"><span data-stu-id="fb123-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="fb123-233">設定に残っている**Build Settings**、ここでは既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb123-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="fb123-234">同じ**Build Settings**ウィンドウで、をクリックして、**プレーヤー設定**ボタン、領域に関連するパネルが開き、**インスペクター**が配置されています。</span><span class="sxs-lookup"><span data-stu-id="fb123-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="fb123-235">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb123-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="fb123-236">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="fb123-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="fb123-237">**ランタイム バージョンをスクリプト**する必要があります**試験的**(.NET 4.6 Equivalent)、エディターを再起動する必要があるします。</span><span class="sxs-lookup"><span data-stu-id="fb123-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="fb123-238">**バックエンドの scripting**べき **.NET**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="fb123-239">**API の互換性レベル**べき **.NET 4.6**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="fb123-240">内で、**発行の設定**] タブの [**機能**、確認してください。</span><span class="sxs-lookup"><span data-stu-id="fb123-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="fb123-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="fb123-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="fb123-242">**Web カメラ**</span><span class="sxs-lookup"><span data-stu-id="fb123-242">**Webcam**</span></span>

        3. <span data-ttu-id="fb123-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="fb123-243">**SpatialPerception**</span></span>

            <span data-ttu-id="fb123-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="fb123-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="fb123-245">パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、確認してください、 **Windows 混在実際には SDK**が追加されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="fb123-246">戻り**Build Settings**、 *Unity C\#プロジェクト*が不要になったグレー: この横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="fb123-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="fb123-247">閉じる、 **Build Settings**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="fb123-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="fb123-248">**エディター**、 をクリックして**編集** > **プロジェクト設定** > **グラフィックス**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="fb123-249">**インスペクター パネル**、*グラフィックス設定*開きます。</span><span class="sxs-lookup"><span data-stu-id="fb123-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="fb123-250">呼ばれる配列が表示されるまで下にスクロール**シェーダーを常に含める**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="fb123-251">スロットの追加を増やすことで、**サイズ**で 1 つは、変数 (この例でこれが 8 のでが 9)。</span><span class="sxs-lookup"><span data-stu-id="fb123-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="fb123-252">新しいスロットが表示されます、配列の最後の位置に次に示すよう。</span><span class="sxs-lookup"><span data-stu-id="fb123-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="fb123-253">スロットでは、シェーダーのリストを開いて、スロットの横にあるターゲットの小さな円をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb123-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="fb123-254">探して、**レガシ シェーダー/Transparent 拡散**シェーダーし、ダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb123-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="fb123-255">第 4 章 - CustomVisionObjDetection Unity パッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="fb123-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="fb123-256">このコースには、Unity Asset のパッケージと呼ばれる**Azure-MR-310.unitypackage**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="fb123-257">[ヒント]シーンの全体を含む、Unity でサポートされているすべてのオブジェクトをパッケージ化できます、 **.unitypackage**ファイル、およびエクスポート/その他のプロジェクトにインポートされています。</span><span class="sxs-lookup"><span data-stu-id="fb123-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="fb123-258">別の間で資産を移動する最も安全な最も効率的な方法は**Unity プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="fb123-259">検索することができます、[ここからダウンロードする必要がある Azure-MR-310 パッケージ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)します。</span><span class="sxs-lookup"><span data-stu-id="fb123-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="fb123-260">前 [Unity ダッシュ ボード] をクリックして**資産**画面の上部にあるメニューでクリックして**パッケージのインポート > カスタム パッケージ**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="fb123-261">ファイル ピッカーを使用して、 **Azure-MR-310.unitypackage**パッケージ化し、をクリックして**オープン**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="fb123-262">この資産のコンポーネントの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="fb123-263">クリックして、インポートの確認、**インポート**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb123-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="fb123-264">これには、インポートが完了したら後に、パッケージからのフォルダーが追加されたようになりましたことがわかりますが、**資産**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="fb123-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="fb123-265">このようなフォルダー構造は、Unity プロジェクトの一般的なものです。</span><span class="sxs-lookup"><span data-stu-id="fb123-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="fb123-266">**資料**フォルダーにはで使用される材料が含まれています、**視線カーソル**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="fb123-267">**プラグイン**フォルダーには、サービスの web 応答を逆シリアル化するコードで使用、Newtonsoft DLL が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb123-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="fb123-268">2 つの異なるバージョンにフォルダーとサブフォルダーに含まれているを使用でき、Unity エディターと UWP ビルドの両方でビルドされたライブラリを許可するために必要です。</span><span class="sxs-lookup"><span data-stu-id="fb123-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="fb123-269">**プレハブ**フォルダーには、シーン内に含まれているプレハブが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb123-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="fb123-270">これらは。</span><span class="sxs-lookup"><span data-stu-id="fb123-270">Those are:</span></span>

        1.  <span data-ttu-id="fb123-271">**GazeCursor**アプリケーションで使用するカーソル。</span><span class="sxs-lookup"><span data-stu-id="fb123-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="fb123-272">物理オブジェクト上にシーンに配置することができる SpatialMapping プレハブと共に動作します。</span><span class="sxs-lookup"><span data-stu-id="fb123-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="fb123-273">**ラベル**、必要な場合に、シーン内のオブジェクト タグの表示に使用される UI オブジェクトであります。</span><span class="sxs-lookup"><span data-stu-id="fb123-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="fb123-274">**SpatialMapping**これを使用するアプリケーションを有効にするオブジェクトは、Microsoft HoloLens の空間の追跡を使用して、仮想のマップを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="fb123-275">**シーン**フォルダーには現在このコースの既成のシーンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb123-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="fb123-276">開く、**シーン**フォルダーで、**プロジェクト パネル**、ダブルクリックして、 **ObjDetectionScene**、このコースで使用するシーンを読み込む。</span><span class="sxs-lookup"><span data-stu-id="fb123-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="fb123-277">**コードが含まれていない**、このコースで、コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="fb123-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="fb123-278">5 -」の章では、CustomVisionAnalyser クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="fb123-279">この時点でコードを記述する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="fb123-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="fb123-280">開始するが、 **CustomVisionAnalyser**クラス。</span><span class="sxs-lookup"><span data-stu-id="fb123-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="fb123-281">呼び出し、 **Custom Vision Service**、以下に示すコードで行われたを使用して、 **Custom Vision REST API**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="fb123-282">これを使用して、実装して (ような画面が独自に実装する方法を理解するために役立ちます) この API を使用する方法が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="fb123-283">対応しており、Microsoft が提供する、**カスタム ビジョン SDK**をサービスを呼び出すことにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="fb123-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="fb123-284">詳細については、次を参照してください。、[カスタム ビジョン SDK の記事](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)します。</span><span class="sxs-lookup"><span data-stu-id="fb123-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="fb123-285">このクラスは、責任を負います。</span><span class="sxs-lookup"><span data-stu-id="fb123-285">This class is responsible for:</span></span>

- <span data-ttu-id="fb123-286">バイト配列としてキャプチャされた最新のイメージを読み込んでいます。</span><span class="sxs-lookup"><span data-stu-id="fb123-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="fb123-287">バイト配列を Azure に送信する**Custom Vision Service**分析のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="fb123-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="fb123-288">JSON 文字列としての応答を受信します。</span><span class="sxs-lookup"><span data-stu-id="fb123-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="fb123-289">応答を逆シリアル化し、その結果を渡して**予測**を**SceneOrganiser**クラスは、応答の表示方法の考慮されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="fb123-290">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-290">To create this class:</span></span>

1.  <span data-ttu-id="fb123-291">右クリックし、**アセット フォルダー**にある、**プロジェクト パネル**、順にクリックします**作成** > **フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="fb123-292">フォルダーを呼び出す**スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="fb123-293">新しく作成された フォルダーを開きをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb123-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="fb123-294">フォルダー内を右クリックし、をクリックして**作成** > **C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="fb123-295">スクリプトの名前**CustomVisionAnalyser します。**</span><span class="sxs-lookup"><span data-stu-id="fb123-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="fb123-296">ダブルクリックして、新しい**CustomVisionAnalyser**スクリプト ファイルを開く**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="fb123-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="fb123-297">次のファイルの上部にある参照される名前空間を確認してください。</span><span class="sxs-lookup"><span data-stu-id="fb123-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="fb123-298">**CustomVisionAnalyser**クラスで、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="fb123-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="fb123-299">挿入することを確認、**サービス予測キー**に、 **predictionKey**変数、および**予測エンドポイント**に、 **predictionEndpoint**変数。</span><span class="sxs-lookup"><span data-stu-id="fb123-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="fb123-300">これらをコピーした[メモ帳以前では、第 2 章の手順 14](#chapter-2---training-your-custom-vision-project)します。</span><span class="sxs-lookup"><span data-stu-id="fb123-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="fb123-301">コードを**Awake()** インスタンス変数を初期化するために追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb123-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="fb123-302">コルーチンを追加 (静的で**GetImageAsByteArray()** 下にあるメソッド)、によってキャプチャされたイメージの分析の結果を取得するが、 **ImageCapture**クラス。</span><span class="sxs-lookup"><span data-stu-id="fb123-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fb123-303">**AnalyseImageCapture**コルーチンへの呼び出しがある、 **SceneOrganiser**クラスを作成することはまだです。</span><span class="sxs-lookup"><span data-stu-id="fb123-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="fb123-304">そのため、**は省略します線は、ここではコメント**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-304">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

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

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
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

9. <span data-ttu-id="fb123-305">削除、 **Start()** と**Update()** メソッドを使用できません。</span><span class="sxs-lookup"><span data-stu-id="fb123-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="fb123-306">変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fb123-307">前述のように、あまり心配しないでコード クラスすぐに、これらを修正するをさらに提供されますが、エラーを表示する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fb123-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="fb123-308">第 6 章 - CustomVisionObjects クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="fb123-309">クラスの作成はここでは、 **CustomVisionObjects**クラス。</span><span class="sxs-lookup"><span data-stu-id="fb123-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="fb123-310">このスクリプトには、Custom Vision Service への呼び出しを逆シリアル化およびシリアル化する他のクラスによって使用されるオブジェクト数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb123-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="fb123-311">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-311">To create this class:</span></span>

1.  <span data-ttu-id="fb123-312">内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="fb123-313">スクリプトを呼び出す**CustomVisionObjects します。**</span><span class="sxs-lookup"><span data-stu-id="fb123-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="fb123-314">ダブルクリックして、新しい**CustomVisionObjects**スクリプト ファイルを開く**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="fb123-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="fb123-315">次のファイルの上部にある参照される名前空間を確認してください。</span><span class="sxs-lookup"><span data-stu-id="fb123-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="fb123-316">削除、 **Start()** と**Update()** 内のメソッド、 **CustomVisionObjects**クラス、このクラスは空になります。</span><span class="sxs-lookup"><span data-stu-id="fb123-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="fb123-317">慎重に次の手順に従ってくださいが重要です。</span><span class="sxs-lookup"><span data-stu-id="fb123-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="fb123-318">新しいクラスの宣言内に配置した場合、 **CustomVisionObjects**クラスにコンパイル エラーが表示されます[第 10 章](#chapter-10---create-the-imagecapture-class)というを**AnalysisRootObject**と**BoundingBox**が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="fb123-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="fb123-319">次のクラスを追加*外*、 **CustomVisionObjects**クラス。</span><span class="sxs-lookup"><span data-stu-id="fb123-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="fb123-320">これらのオブジェクトを使って、 **Newtonsoft**および応答データを逆シリアル化するライブラリ。</span><span class="sxs-lookup"><span data-stu-id="fb123-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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
    /// JSON of images submitted
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
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  <span data-ttu-id="fb123-321">変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="fb123-322">7 - 章 SpatialMapping クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="fb123-323">このクラスは設定、**空間マッピング Collider**仮想オブジェクトと実際のオブジェクト間の競合を検出できるようにするシーンにします。</span><span class="sxs-lookup"><span data-stu-id="fb123-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="fb123-324">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-324">To create this class:</span></span>

1.  <span data-ttu-id="fb123-325">内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="fb123-326">スクリプトを呼び出す**SpatialMapping します。**</span><span class="sxs-lookup"><span data-stu-id="fb123-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="fb123-327">ダブルクリックして、新しい**SpatialMapping**スクリプト ファイルを開く**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="fb123-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="fb123-328">上記の次の名前空間があるかどうかを確認、 **SpatialMapping**クラス。</span><span class="sxs-lookup"><span data-stu-id="fb123-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="fb123-329">次に、内部では、次の変数を追加、 **SpatialMapping**クラス上、 **Start()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="fb123-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  <span data-ttu-id="fb123-330">追加、 **Awake()** と**Start()** :</span><span class="sxs-lookup"><span data-stu-id="fb123-330">Add the **Awake()** and **Start()**:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  <span data-ttu-id="fb123-331">削除、 **Update()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="fb123-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="fb123-332">変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="fb123-333">8 - 章 GazeCursor クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="fb123-334">このクラスは実際の領域で、正しい位置にカーソルを設定するための使用することで、 **SpatialMappingCollider**前の章で作成された。</span><span class="sxs-lookup"><span data-stu-id="fb123-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="fb123-335">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-335">To create this class:</span></span>

1.  <span data-ttu-id="fb123-336">内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="fb123-337">スクリプトを呼び出す**GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="fb123-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="fb123-338">ダブルクリックして、新しい**GazeCursor**スクリプト ファイルを開く**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="fb123-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="fb123-339">上記の次の名前空間があるかどうかを確認、 **GazeCursor**クラス。</span><span class="sxs-lookup"><span data-stu-id="fb123-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="fb123-340">内の次の変数を追加し、 **GazeCursor**クラス上、 **Start()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="fb123-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="fb123-341">更新プログラム、 **Start()** メソッドを次のコード。</span><span class="sxs-lookup"><span data-stu-id="fb123-341">Update the **Start()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  <span data-ttu-id="fb123-342">更新プログラム、 **Update()** メソッドを次のコード。</span><span class="sxs-lookup"><span data-stu-id="fb123-342">Update the **Update()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="fb123-343">エラーをあまり心配しないで、 **SceneOrganiser**クラスが、[次へ] の章では作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="fb123-344">変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="fb123-345">9 - 章 SceneOrganiser クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="fb123-346">このクラスは。</span><span class="sxs-lookup"><span data-stu-id="fb123-346">This class will:</span></span>

-   <span data-ttu-id="fb123-347">設定する、 *Main Camera*に適切なコンポーネントをアタッチしています。</span><span class="sxs-lookup"><span data-stu-id="fb123-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="fb123-348">オブジェクトが検出されたときに、現実の世界と配置内の位置を計算する責任を負いますなります、**タグ ラベル**と、該当の近く**タグ名**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="fb123-349">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-349">To create this class:</span></span>

1.  <span data-ttu-id="fb123-350">内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="fb123-351">スクリプトの名前**SceneOrganiser**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="fb123-352">ダブルクリックして、新しい**SceneOrganiser**スクリプト ファイルを開く**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="fb123-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="fb123-353">上記の次の名前空間があるかどうかを確認、 **SceneOrganiser**クラス。</span><span class="sxs-lookup"><span data-stu-id="fb123-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="fb123-354">内で、次の変数を追加し、 **SceneOrganiser**クラス上、 **Start()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="fb123-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  <span data-ttu-id="fb123-355">削除、 **Start()** と**Update()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="fb123-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="fb123-356">変数の下に追加、 **Awake()** メソッドはクラスを初期化し、シーンを設定します。</span><span class="sxs-lookup"><span data-stu-id="fb123-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  <span data-ttu-id="fb123-357">追加、 **PlaceAnalysisLabel()** メソッドは*Instantiate* (これは、この時点では、ユーザーに表示される)、シーン内のラベル。</span><span class="sxs-lookup"><span data-stu-id="fb123-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="fb123-358">クアッド (も非表示)、イメージが配置されると、し、現実の世界と重複しても配置されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="fb123-359">これは、機能は、分析は、実際のオブジェクトのおおよその場所を決定するには、このクアッドにまでトレースした後、ボックスの座標が、サービスから取得したため、重要です。</span><span class="sxs-lookup"><span data-stu-id="fb123-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  <span data-ttu-id="fb123-360">追加、 **FinaliseLabel()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="fb123-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="fb123-361">担当します。</span><span class="sxs-lookup"><span data-stu-id="fb123-361">It is responsible for:</span></span>

    *   <span data-ttu-id="fb123-362">設定、*ラベル*テキストを*タグ*の最高の信頼性と予測します。</span><span class="sxs-lookup"><span data-stu-id="fb123-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="fb123-363">計算を呼び出す、*境界ボックス*クアッドのオブジェクトでは、以前は、配置およびシーン内のラベルを配置することにします。</span><span class="sxs-lookup"><span data-stu-id="fb123-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="fb123-364">に向けての Raycast を使用して、ラベルの深さを調整すること、*境界ボックス*、現実の世界でオブジェクトが衝突する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb123-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="fb123-365">別のイメージをキャプチャするユーザーを許可するキャプチャ プロセスをリセットしています。</span><span class="sxs-lookup"><span data-stu-id="fb123-365">Resetting the capture process to allow the user to capture another image.</span></span>

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  <span data-ttu-id="fb123-366">追加、 **CalculateBoundingBoxPosition()** メソッドは、さまざまな変換に必要な計算をホストする、*境界ボックス*座標は、サービスから取得され、再作成します。クアッド比例的に。</span><span class="sxs-lookup"><span data-stu-id="fb123-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. <span data-ttu-id="fb123-367">変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fb123-368">続行する前に開いて、 **CustomVisionAnalyser**クラス内で、 **AnalyseLastImageCaptured()** メソッド、*をコメント解除します*次の行。</span><span class="sxs-lookup"><span data-stu-id="fb123-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> <span data-ttu-id="fb123-369">心配しないで、 **ImageCapture** '見つかりませんでした' メッセージのクラス、[次へ] の章では作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="fb123-370">10 - 章 ImageCapture クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="fb123-371">次のクラスを作成することには、 **ImageCapture**クラス。</span><span class="sxs-lookup"><span data-stu-id="fb123-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="fb123-372">このクラスは、責任を負います。</span><span class="sxs-lookup"><span data-stu-id="fb123-372">This class is responsible for:</span></span>

*   <span data-ttu-id="fb123-373">HoloLens のカメラを使用して、格納することでイメージのキャプチャ、*アプリ*フォルダー。</span><span class="sxs-lookup"><span data-stu-id="fb123-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="fb123-374">処理*タップ*ユーザーからのジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="fb123-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="fb123-375">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb123-375">To create this class:</span></span>

1.  <span data-ttu-id="fb123-376">移動して、**スクリプト**以前に作成したフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="fb123-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="fb123-377">フォルダー内を右クリックし、をクリックして**作成** > **C\#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="fb123-378">スクリプトの名前**ImageCapture**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="fb123-379">ダブルクリックして、新しい**ImageCapture**スクリプト ファイルを開く**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="fb123-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="fb123-380">次のように、ファイルの上部にある名前空間に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="fb123-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="fb123-381">内で、次の変数を追加し、 **ImageCapture**クラス上、 **Start()** メソッド。</span><span class="sxs-lookup"><span data-stu-id="fb123-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="fb123-382">コードを**Awake()** と**Start()** 今すぐメソッドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb123-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="fb123-383">タップ ジェスチャが発生したときに呼び出されるハンドラーを実装します。</span><span class="sxs-lookup"><span data-stu-id="fb123-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="fb123-384">カーソルがある場合**緑色**カメラが、イメージを意味します。</span><span class="sxs-lookup"><span data-stu-id="fb123-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="fb123-385">カーソルがある場合**赤い**カメラがビジー状態になります。</span><span class="sxs-lookup"><span data-stu-id="fb123-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="fb123-386">イメージのキャプチャ プロセスを開始し、イメージを格納するアプリケーションが使用するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="fb123-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
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

9.  <span data-ttu-id="fb123-387">写真をキャプチャおよび分析する準備ができ次第の呼び出されるハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="fb123-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="fb123-388">渡されますが、結果、 **CustomVisionAnalyser**分析します。</span><span class="sxs-lookup"><span data-stu-id="fb123-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="fb123-389">変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="fb123-390">第 11 章 – シーン内のスクリプトの設定</span><span class="sxs-lookup"><span data-stu-id="fb123-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="fb123-391">これですべてのこのプロジェクトに必要なコードを記述して、シーンと正しく動作するように、プレハブのスクリプトを設定するには</span><span class="sxs-lookup"><span data-stu-id="fb123-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="fb123-392">内で、 **Unity エディター**の**階層パネル**を選択、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="fb123-393">**インスペクター パネル**で、 **Main Camera**選択すると、をクリックして**コンポーネントの追加**、検索し**SceneOrganiser**スクリプトと追加するをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb123-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="fb123-394">**プロジェクト パネル**、オープン、 **Prefabs フォルダー**、ドラッグ、**ラベル**にプレハブ、*ラベル*空の参照先の領域を入力する、**SceneOrganiser**に追加したスクリプト、 *Main Camera*次の図に示すように、します。</span><span class="sxs-lookup"><span data-stu-id="fb123-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="fb123-395">**階層パネル**を選択、 **GazeCursor**の子、 **Main Camera**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="fb123-396">**インスペクター パネル**で、 **GazeCursor**選択すると、をクリックして**コンポーネントの追加**を検索し**GazeCursor**スクリプトと追加するをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb123-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="fb123-397">もう一度、**階層パネル**を選択、 **SpatialMapping**の子、 **Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="fb123-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="fb123-398">**インスペクター パネル**で、 **SpatialMapping**選択すると、をクリックして**コンポーネントの追加**を検索し**SpatialMapping**スクリプトそれを追加する をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb123-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="fb123-399">残りのスクリプトをするがないセット内のコードで追加されます、 **SceneOrganiser**スクリプトの実行時に、します。</span><span class="sxs-lookup"><span data-stu-id="fb123-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="fb123-400">第 12 章 - ビルドの前に</span><span class="sxs-lookup"><span data-stu-id="fb123-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="fb123-401">アプリケーションの徹底的なテストを実行するには、必要がありますをサイドロードすること、Microsoft HoloLens にします。</span><span class="sxs-lookup"><span data-stu-id="fb123-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="fb123-402">実行する前にいることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fb123-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="fb123-403">説明されているすべての設定、[第 3 章](#chapter-3---set-up-the-unity-project)が正しく設定されています。</span><span class="sxs-lookup"><span data-stu-id="fb123-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="fb123-404">スクリプト**SceneOrganiser**にアタッチされて、 **Main Camera**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fb123-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="fb123-405">スクリプト**GazeCursor**にアタッチされて、 **GazeCursor**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fb123-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="fb123-406">スクリプト**SpatialMapping**にアタッチされて、 **SpatialMapping**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fb123-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="fb123-407">[第 5 章](#chapter-5---create-the-customvisionanalyser-class)手順 6。</span><span class="sxs-lookup"><span data-stu-id="fb123-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="fb123-408">挿入することを確認、**サービス予測キー**に、 **predictionKey**変数。</span><span class="sxs-lookup"><span data-stu-id="fb123-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="fb123-409">挿入した、**予測エンドポイント**に、 **predictionEndpoint**クラス。</span><span class="sxs-lookup"><span data-stu-id="fb123-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="fb123-410">章 13 - アプリケーションを作成、UWP のソリューションとサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="fb123-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="fb123-411">Microsoft HoloLens にデプロイすることができますを UWP ソリューションとしてのアプリケーションを構築する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="fb123-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="fb123-412">ビルド プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="fb123-412">To begin the build process:</span></span>

1.  <span data-ttu-id="fb123-413">移動して**ファイル > のビルド設定**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="fb123-414">ティック**Unity C\#プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="fb123-415">をクリックして**開くシーンを追加**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="fb123-416">これにより、ビルドに現在開いているシーンが追加されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="fb123-417">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb123-417">Click **Build**.</span></span> <span data-ttu-id="fb123-418">Unity を起動、*ファイル エクスプ ローラー*ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb123-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="fb123-419">ここで、そのフォルダーを作成し、名前**アプリ**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="fb123-420">使用し、**アプリ**フォルダーを選択すると、クリックして**フォルダーの選択**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="fb123-421">Unity にプロジェクトをビルドを開始、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="fb123-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="fb123-422">1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。</span><span class="sxs-lookup"><span data-stu-id="fb123-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="fb123-423">Microsoft HoloLens を展開する必要がありますそのデバイスの IP アドレス (リモート) をデプロイ用ともいることを確認するのには**開発者モード**を設定します。</span><span class="sxs-lookup"><span data-stu-id="fb123-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="fb123-424">これには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fb123-424">To do this:</span></span>

    1.  <span data-ttu-id="fb123-425">ソックスを着けずに、HoloLens 中を開く、**設定**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="fb123-426">移動して**ネットワークとインターネット** > **Wi-fi** > **詳細オプション**</span><span class="sxs-lookup"><span data-stu-id="fb123-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="fb123-427">注、 **IPv4**アドレス。</span><span class="sxs-lookup"><span data-stu-id="fb123-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="fb123-428">次に移動します**設定**、し**更新とセキュリティ** > **開発者向け**</span><span class="sxs-lookup"><span data-stu-id="fb123-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="fb123-429">設定**開発者モード** *で*します。</span><span class="sxs-lookup"><span data-stu-id="fb123-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="fb123-430">新しい Unity ビルドに移動します (、**アプリ**フォルダー) とソリューション ファイルを開くと**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="fb123-431">ソリューション構成の選択で**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="fb123-432">ソリューション プラットフォーム で選択**x86、リモート コンピューター**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="fb123-433">挿入を求め、 **IP アドレス**のリモート デバイス (、Microsoft HoloLens、ここでは、メモしたもの)。</span><span class="sxs-lookup"><span data-stu-id="fb123-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="fb123-434">移動して、**ビルド**メニューをクリックします**ソリューションの配置**サイドロード、HoloLens をアプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="fb123-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="fb123-435">アプリが、Microsoft HoloLens、起動の準備完了にインストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="fb123-436">アプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="fb123-436">To use the application:</span></span>

* <span data-ttu-id="fb123-437">トレーニングがオブジェクトを見て、 **Azure Custom Vision Service、オブジェクトの検出**を使用して、**タップ ジェスチャ**します。</span><span class="sxs-lookup"><span data-stu-id="fb123-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="fb123-438">場合は、オブジェクトが正常に検出されると、ワールド空間*ラベル テキスト*タグ名と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb123-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fb123-439">写真をキャプチャして、サービスに送信するたびには、サービスのページに戻るし、新しくキャプチャされたイメージのサービスの再トレーニングします。</span><span class="sxs-lookup"><span data-stu-id="fb123-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="fb123-440">を先頭には、おそらく修正する必要も、*境界ボックス*より正確になるし、サービスの再トレーニングします。</span><span class="sxs-lookup"><span data-stu-id="fb123-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="fb123-441">配置ラベルのテキストは可能性があります、現実世界のオブジェクトを基準とした、適切なコライダーを配置する Microsoft HoloLens のセンサーや Unity で SpatialTrackingComponent が失敗したときに、オブジェクトの近くは表示されません。</span><span class="sxs-lookup"><span data-stu-id="fb123-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="fb123-442">その場合は、異なる画面で、アプリケーションを使用してください。</span><span class="sxs-lookup"><span data-stu-id="fb123-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="fb123-443">カスタム ビジョン、アプリケーションのオブジェクトの検出</span><span class="sxs-lookup"><span data-stu-id="fb123-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="fb123-444">これで、Azure の Custom Vision がイメージからオブジェクトを認識して 3D 空間でそのオブジェクトのおおよその位置を提供し、オブジェクト検出 API を利用している mixed reality アプリを構築します。</span><span class="sxs-lookup"><span data-stu-id="fb123-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="fb123-445">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="fb123-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="fb123-446">手順 1</span><span class="sxs-lookup"><span data-stu-id="fb123-446">Exercise 1</span></span>

<span data-ttu-id="fb123-447">3D に実際のオブジェクトをラップする半透明にするキューブを使用して、テキスト ラベルを追加する*境界ボックス*します。</span><span class="sxs-lookup"><span data-stu-id="fb123-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="fb123-448">手順 2</span><span class="sxs-lookup"><span data-stu-id="fb123-448">Exercise 2</span></span>

<span data-ttu-id="fb123-449">複数のオブジェクトを認識する、Custom Vision Service をトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="fb123-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="fb123-450">手順 3</span><span class="sxs-lookup"><span data-stu-id="fb123-450">Exercise 3</span></span>

<span data-ttu-id="fb123-451">オブジェクトが認識されると、サウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="fb123-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="fb123-452">手順 4</span><span class="sxs-lookup"><span data-stu-id="fb123-452">Exercise 4</span></span>

<span data-ttu-id="fb123-453">API を使用して、アプリの分析は、同じイメージのサービスの再トレーニングに、そのため、サービスをより正確に (予測と同時にトレーニングを行う)。</span><span class="sxs-lookup"><span data-stu-id="fb123-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
