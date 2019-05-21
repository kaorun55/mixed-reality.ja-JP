---
title: MR と Azure 303 の自然言語の理解 (LUIS)
description: このコースでは、複合現実のアプリケーション内で Azure Language Understanding Intelligence Service (LUIS) を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality, academy、unity、チュートリアル、api、language understanding インテリジェンス サービス, luis、hololens、没入型、vr
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603074"
---
>[!NOTE]
><span data-ttu-id="f99ae-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f99ae-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f99ae-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f99ae-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f99ae-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f99ae-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f99ae-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="f99ae-110">MR と Azure 303:自然言語の理解 (LUIS)</span><span class="sxs-lookup"><span data-stu-id="f99ae-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="f99ae-111">このコースでは、Language Understanding API を使用した Azure Cognitive Services を使用して、複合現実のアプリケーションに言語理解機能を統合する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![ラボの結果](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="f99ae-113">*Language Understanding (LUIS)* にどのような人が必要で、ユーザーの声の抽出をユーザー入力からの意味を確保できるアプリケーションを提供する Microsoft Azure サービスです。</span><span class="sxs-lookup"><span data-stu-id="f99ae-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="f99ae-114">これを実現するには、機械学習を理解および入力の情報では、学習し、関連する詳細な情報に応答できます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="f99ae-115">詳細については、次を参照してください。、 [Azure Language Understanding (LUIS) ページ](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="f99ae-116">このコースを完了すると、以下を実行できる必要が複合現実イマーシブ ヘッドセット アプリケーションが完成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="f99ae-117">イマーシブ ヘッドセットにアタッチされているマイクを使用して、ユーザーの入力音声をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="f99ae-118">キャプチャされたディクテーションの送信、 *Azure Language Understanding Intelligent Service* (*LUIS*)。</span><span class="sxs-lookup"><span data-stu-id="f99ae-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="f99ae-119">LUIS の抽出、分析され、ユーザーの要求の目的が行われるかを判断しようとする情報送信から意味があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="f99ae-120">開発では、ユーザーを使用して、音声または視線、サイズと、シーン内のオブジェクトの色を変更することが、アプリの作成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="f99ae-121">アニメーション コント ローラーの使用は扱いません。</span><span class="sxs-lookup"><span data-stu-id="f99ae-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="f99ae-122">アプリケーションでは、責任ですが、設計と、結果を統合する方法について。</span><span class="sxs-lookup"><span data-stu-id="f99ae-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="f99ae-123">このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。</span><span class="sxs-lookup"><span data-stu-id="f99ae-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="f99ae-124">複合現実アプリを強化するためには、このコース得た知識を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="f99ae-125">複数回が LUIS をトレーニングする準備が、これは、「[第 12 章](#chapter-12--improving-your-luis-service)します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="f99ae-126">LUIS がトレーニングされている詳細度より良い結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="f99ae-127">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="f99ae-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f99ae-128">コース</span><span class="sxs-lookup"><span data-stu-id="f99ae-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f99ae-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f99ae-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f99ae-130"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="f99ae-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="f99ae-131">MR と Azure 303:自然言語の理解 (LUIS)</span><span class="sxs-lookup"><span data-stu-id="f99ae-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="f99ae-132">✔️</span><span class="sxs-lookup"><span data-stu-id="f99ae-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f99ae-133">✔️</span><span class="sxs-lookup"><span data-stu-id="f99ae-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="f99ae-134">このコースが主に Windows Mixed Reality 没入型 (VR) ヘッドセットを重点的に Microsoft HoloLens には、このコースで学習する内容を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="f99ae-135">コースを実行するとき、HoloLens をサポートするために必要な場合があります変更でノートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="f99ae-136">HoloLens を使用する場合は、音声キャプチャ中にいくつかのエコーが気付きです。</span><span class="sxs-lookup"><span data-stu-id="f99ae-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f99ae-137">前提条件</span><span class="sxs-lookup"><span data-stu-id="f99ae-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="f99ae-138">このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="f99ae-139">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 5 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f99ae-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="f99ae-140">内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)ことについては、このコースでとまったく同じで見つかりますの下に記載されているものよりも新しいソフトウェアでどのようなことは仮定されませんが、記事.</span><span class="sxs-lookup"><span data-stu-id="f99ae-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="f99ae-141">次のハードウェアとソフトウェアこのコースをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="f99ae-142">開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発</span><span class="sxs-lookup"><span data-stu-id="f99ae-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="f99ae-143">Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="f99ae-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="f99ae-144">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="f99ae-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="f99ae-145">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="f99ae-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="f99ae-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f99ae-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="f99ae-147">A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効</span><span class="sxs-lookup"><span data-stu-id="f99ae-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="f99ae-148">(ヘッドセットには、組み込みのマイクとスピーカーを持っていない) 場合は、内蔵マイクでヘッドフォン</span><span class="sxs-lookup"><span data-stu-id="f99ae-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="f99ae-149">Azure のセットアップおよび LUIS 取得するためのインターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="f99ae-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="f99ae-150">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="f99ae-150">Before you start</span></span>

1.  <span data-ttu-id="f99ae-151">このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。</span><span class="sxs-lookup"><span data-stu-id="f99ae-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="f99ae-152">ディクテーションを有効にするためにコンピューターを許可するには**Windows の設定 > プライバシーに関する > 読み上げ、手描き入力機能 (&) を入力する** ボタンを押すと**音声サービスをオンにして、入力候補**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="f99ae-153">このチュートリアルでは、コードから記録することにより、**マイク デバイスの既定の**コンピューターに設定します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="f99ae-154">マイクの既定のデバイスが音声のキャプチャに使用する 1 つとして設定することを確認します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="f99ae-155">ヘッドセットに内蔵マイクがある場合は、必ずオプション *「マイ ヘッドセットを着用するときに切り替えるヘッドセット マイク」* でオンに、 *Mixed Reality ポータル*設定します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![イマーシブ ヘッドセットの設定](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="f99ae-157">第 1 章 – Azure Portal のセットアップ</span><span class="sxs-lookup"><span data-stu-id="f99ae-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="f99ae-158">使用する、 *Language Understanding*サービス、Azure でアプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="f99ae-159">[Azure ポータル](https://portal.azure.com) にログインします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="f99ae-160">Azure アカウントがいない場合は、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="f99ae-161">クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="f99ae-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="f99ae-162">ログインした後は、をクリックして**新規**左上隅にある検索して*Language Understanding*、 をクリック**Enter**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![LUIS のリソースを作成します。](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="f99ae-164">単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="f99ae-165">右側に新しいページは、Language Understanding サービスの説明を提供します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="f99ae-166">このページの左下にある at、**作成**ボタンは、このサービスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![LUIS サービスの作成 - 法的通知](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="f99ae-168">作成した 1 回。</span><span class="sxs-lookup"><span data-stu-id="f99ae-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="f99ae-169">必要な挿入**名前**このサービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="f99ae-170">選択、**サブスクリプション**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="f99ae-171">選択、**価格レベル**場合、これは、最初に、適切な時間を作成する、 *LUIS サービス*、(F0 という名前)、free レベルを使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="f99ae-172">無料の割り当ては、このコースのための十分な複数の必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="f99ae-173">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f99ae-174">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f99ae-175">勧めします (例: これらのコース) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。</span><span class="sxs-lookup"><span data-stu-id="f99ae-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="f99ae-176">詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="f99ae-177">確認、**場所**(新しいリソース グループを作成する) 場合は、リソース グループ。</span><span class="sxs-lookup"><span data-stu-id="f99ae-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="f99ae-178">場所は、アプリケーションが実行リージョンにあるが理想的です。</span><span class="sxs-lookup"><span data-stu-id="f99ae-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="f99ae-179">一部の Azure 資産は特定のリージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="f99ae-180">また、このサービスに適用される条件を理解したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="f99ae-181">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-181">Select **Create**.</span></span>

        ![LUIS サービス - ユーザー入力を作成します。](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="f99ae-183">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="f99ae-184">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![新しい Azure の通知の画像](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="f99ae-186">新しいサービス インスタンスを探索する通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-186">Click on the notification to explore your new Service instance.</span></span>

    ![成功したリソースの作成の通知](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="f99ae-188">をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="f99ae-189">新しい LUIS サービス インスタンスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![LUIS のキーにアクセスします。](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="f99ae-191">このチュートリアルでは、内でアプリケーションがサービスのサブスクリプション キーを使用して、これは、サービスへの呼び出しを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="f99ae-192">*クイック スタート* ページの*LUIS API*サービスは、最初のステップに移動し、*キーを取得する*、 をクリック**キー** (することもできますこれは実現キー アイコンによって示される、サービスのナビゲーション メニューにある青いハイパーリンク キーをクリックして)。</span><span class="sxs-lookup"><span data-stu-id="f99ae-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="f99ae-193">これが明らかに、サービス*キー*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="f99ae-194">このプロジェクトの後半で必要になるため、表示されているキーの 1 つのコピーを実行します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="f99ae-195">*サービス* ページで、をクリックして*Language Understanding ポータル*に LUIS アプリ内で、新しいサービスの作成に使用する web ページにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="f99ae-196">第 2 章 –、Language Understanding ポータル</span><span class="sxs-lookup"><span data-stu-id="f99ae-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="f99ae-197">このセクションでは、LUIS ポータルに LUIS アプリを作成する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="f99ae-198">わけを設定する、*エンティティ*、*インテント*、および*発話*この章では、LUIS サービスの構築の最初の手順のみ: にも必要になりますサービスの再トレーニング、何回かためより正確にします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="f99ae-199">については、サービスの再トレーニング、[最後の章](#chapter-12--improving-your-luis-service)のこのコースでは、これを完了するようにします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="f99ae-200">達すると、 *Language Understanding ポータル*、ない場合に、既に、Azure portal と同じ資格情報でログインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![LUIS のログイン ページ](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="f99ae-202">これは、LUIS を使用して、最初に、検索 をクリックして、ウェルカム ページの一番下までスクロールする必要があります、**作成 LUIS アプリ**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![LUIS アプリのページを作成します。](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="f99ae-204">ログインすると、クリックして**のマイ アプリ**(ない場合そのセクションでは現在)。</span><span class="sxs-lookup"><span data-stu-id="f99ae-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="f99ae-205">クリックし、**新しいアプリの作成**です。</span><span class="sxs-lookup"><span data-stu-id="f99ae-205">You can then click on **Create new app**.</span></span>

    ![LUIS のマイ アプリのイメージ](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="f99ae-207">アプリを指定する*名前*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="f99ae-208">変更する必要がある場合は、アプリは、英語以外の言語を理解することになって、*カルチャ*適切な言語です。</span><span class="sxs-lookup"><span data-stu-id="f99ae-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="f99ae-209">ここで追加することも、*説明*新しい LUIS アプリの。</span><span class="sxs-lookup"><span data-stu-id="f99ae-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS - 新しいアプリを作成します。](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="f99ae-211">キーを押すと**完了**、入力する、*ビルド*の新しいページ*LUIS*アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="f99ae-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="f99ae-212">ここで理解するいくつかの重要な概念があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="f99ae-213">*インテント*、次のクエリをユーザーから呼び出されるメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="f99ae-214">*インテント*1 つまたは複数あります*エンティティ*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="f99ae-215">*エンティティ*、関連する情報を示すクエリのコンポーネントである、*インテント*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="f99ae-216">*発話*クエリの例については、開発者でその LUIS が自体のトレーニングに使用されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="f99ae-217">これらの概念が完全がない場合は、クリア、問題なく、このコースはこの章でさらにそれらを明確です。</span><span class="sxs-lookup"><span data-stu-id="f99ae-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="f99ae-218">作成は、まず、*エンティティ*このコースを構築するために必要です。</span><span class="sxs-lookup"><span data-stu-id="f99ae-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="f99ae-219">ページの左側にある、] をクリックして*エンティティ*の [**新しいエンティティを作成**です。</span><span class="sxs-lookup"><span data-stu-id="f99ae-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![新しいエンティティを作成します。](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="f99ae-221">新しいエンティティを呼び出す*色*、その型に設定*単純*、キーを押します**完了**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![色の単純なエンティティを作成します。](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="f99ae-223">3 個以上単純なエンティティという名前を作成するには、このプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="f99ae-224">*upsize*</span><span class="sxs-lookup"><span data-stu-id="f99ae-224">*upsize*</span></span>
    -   <span data-ttu-id="f99ae-225">*downsize*</span><span class="sxs-lookup"><span data-stu-id="f99ae-225">*downsize*</span></span>
    -   <span data-ttu-id="f99ae-226">*ターゲット*</span><span class="sxs-lookup"><span data-stu-id="f99ae-226">*target*</span></span>

<span data-ttu-id="f99ae-227">結果は、次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-227">The result should look like the image below:</span></span>

![エンティティの作成の結果](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="f99ae-229">作成を開始する時点でこの*インテント*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="f99ae-230">削除しないでください、 **None**インテントです。</span><span class="sxs-lookup"><span data-stu-id="f99ae-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="f99ae-231">ページの左側にある、 をクリックして**インテント**、をクリックして**新しいインテント作成**です。</span><span class="sxs-lookup"><span data-stu-id="f99ae-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![新しいインテントを作成します。](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="f99ae-233">新しい*インテント* **ChangeObjectColor**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="f99ae-234">これは、*インテント*名が使用されるこのコースの後半で、コード内でそのため最良の結果を使用して、この名前指定されたとおりです。</span><span class="sxs-lookup"><span data-stu-id="f99ae-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="f99ae-235">インテント ページに表示される名前のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS のインテント ページ](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="f99ae-237">5 個以上の異なる型に求めるテキスト ボックスがあることがわかります*発話*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="f99ae-238">LUIS では、すべての発話を小文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="f99ae-239">次を挿入します*発話*上部のテキスト ボックスに (テキストと現在 *... 約 5 の例の型*</span><span class="sxs-lookup"><span data-stu-id="f99ae-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="f99ae-240">)、キーを押します**Enter**:</span><span class="sxs-lookup"><span data-stu-id="f99ae-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="f99ae-241">その新しい*発話*の下に一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="f99ae-242">次の同じプロセスでは、次の 6 発話を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="f99ae-243">作成したそれぞれの発話エンティティとして LUIS がどの単語を使用する必要がありますを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="f99ae-244">この例では、としてすべての色のラベルを付ける必要があります、*色*エンティティ、および可能なすべての参照をターゲットとして、*ターゲット*エンティティ。</span><span class="sxs-lookup"><span data-stu-id="f99ae-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="f99ae-245">これを行うには、という語をクリックを再試行してください*円柱*でクリックし、最初の発話*ターゲット*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![発話のターゲットを特定します。](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="f99ae-247">ここで単語をクリックして*赤い*でクリックし、最初の発話*色*。</span><span class="sxs-lookup"><span data-stu-id="f99ae-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![発話のエンティティを識別します。](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="f99ae-249">また、次の行のラベルを付ける場所*キューブ*する必要があります、*ターゲット*と*黒い*する必要があります、*色*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="f99ae-250">単語の使用も注意してください。 *'this'*、 *'it'*、と *'オブジェクト'*、提供しています、これも使用できる非固有のターゲット型にします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="f99ae-251">上記のプロセスを繰り返して、すべての発話にというラベルが付いたエンティティが存在します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="f99ae-252">参照してください、次の画像が必要な場合。</span><span class="sxs-lookup"><span data-stu-id="f99ae-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="f99ae-253">ときに、それらのエンティティとしてラベル付けに単語を選択します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="f99ae-254">1 つの単語だけをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-254">For single words just click them.</span></span>
    > - <span data-ttu-id="f99ae-255">一連の 2 つ以上の単語の先頭にしてから、セットの末尾でをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f99ae-256">使用することができます、*トークン ビュー*を切り替えるトグル ボタン**エンティティ/トークン ビュー**!</span><span class="sxs-lookup"><span data-stu-id="f99ae-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="f99ae-257">結果は、次の画像に示すように、表示する必要があります、**エンティティ/トークン ビュー**:</span><span class="sxs-lookup"><span data-stu-id="f99ae-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![エンティティのビュー (&)、トークン](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="f99ae-259">この時点でキーを押して、**トレーニング**ページの右上にあるボタンをクリックし、緑を有効にする上で小さな丸いインジケーターを待機します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="f99ae-260">これは、この目的を認識する LUIS が正常にトレーニングされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![LUIS をトレーニング](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="f99ae-262">演習として作成すると呼ばれる新しい目的**ChangeObjectSize**、エンティティを使用して*ターゲット*、*アップサイズ*、および*ダウンサイズ*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="f99ae-263">次の以前のインテントと同じプロセスの次の 8 (8) 発話を挿入*サイズ*を変更します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. <span data-ttu-id="f99ae-264">結果は、次の図に示すようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-264">The result should be like the one in the image below:</span></span>

    ![ChangeObjectSize トークンのセットアップ/エンティティ](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="f99ae-266">両方のインテント、1 回**ChangeObjectColor**と**ChangeObjectSize**作成されているし、トレーニングをクリックして、**発行**ページ上部にあるボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![LUIS サービスを発行します。](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="f99ae-268">*発行*ページの最終処理して、コードでアクセスできるように、LUIS アプリを発行します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="f99ae-269">セットをスケール ダウン、ドロップ*Publish To*として**運用**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="f99ae-270">設定、*タイムゾーン*タイム ゾーンにします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="f99ae-271">チェック ボックスをオン**すべて含む予測スコアのインテント**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="f99ae-272">をクリックして**運用スロットに発行**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-272">Click on **Publish to Production Slot**.</span></span>

        ![発行の設定](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="f99ae-274">セクションで*リソースとキー*:</span><span class="sxs-lookup"><span data-stu-id="f99ae-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="f99ae-275">Azure Portal でのサービス インスタンスに設定するリージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="f99ae-276">表示されます、 **Starter_Key** 、下の要素を無視します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="f99ae-277">をクリックして**キーの追加**を挿入し、*キー*サービス インスタンスを作成したときに、Azure Portal で取得しました。</span><span class="sxs-lookup"><span data-stu-id="f99ae-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="f99ae-278">ドロップダウン メニューを指定した場合は、Azure と LUIS ポータルは、同じユーザーにログインしている、*テナント名*、*サブスクリプション名*、および*キー* (を使用します。Azure Portal で以前に指定したように、同じ名前になります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="f99ae-279">下に*エンドポイント*キーに対応するエンドポイントのコピーを挿入した、コードですぐに使用されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="f99ae-280">第 3 章 – Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="f99ae-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="f99ae-281">次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。</span><span class="sxs-lookup"><span data-stu-id="f99ae-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="f99ae-282">開いている*Unity*クリック**新規**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-282">Open *Unity* and click **New**.</span></span> 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="f99ae-284">Unity プロジェクト名を指定する必要がありますこれで挿入**MR_LUIS**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="f99ae-285">必ず、プロジェクトの種類に設定されて**3D**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="f99ae-286">設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。</span><span class="sxs-lookup"><span data-stu-id="f99ae-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="f99ae-287">をクリックし、**プロジェクトの作成**です。</span><span class="sxs-lookup"><span data-stu-id="f99ae-287">Then, click **Create project**.</span></span>

    ![新しい Unity プロジェクトの詳細を提供します。](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="f99ae-289">既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="f99ae-290">編集 > 設定し、新しいウィンドウに移動**外部ツール**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="f99ae-291">変更**External Script Editor**に**Visual Studio 2017**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="f99ae-292">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="f99ae-292">Close the **Preferences** window.</span></span>

    ![スクリプト エディターの基本設定を更新します。](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="f99ae-294">次に移動**ファイル > Build Settings**にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして、**プラットフォームの切り替え**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![[設定] ウィンドウ切り替え UWP プラットフォームをビルドします。](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="f99ae-296">移動して**ファイル > Build Settings**ことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f99ae-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="f99ae-297">**デバイスを対象に**に設定されている**任意のデバイス**</span><span class="sxs-lookup"><span data-stu-id="f99ae-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="f99ae-298">Microsoft HoloLens、設定**ターゲット デバイス**に*HoloLens*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="f99ae-299">**ビルドの種類**に設定されている**D3D**</span><span class="sxs-lookup"><span data-stu-id="f99ae-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="f99ae-300">**SDK**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="f99ae-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="f99ae-301">**Visual Studio バージョン**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="f99ae-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="f99ae-302">**ビルドおよび実行**に設定されている**ローカル マシン**</span><span class="sxs-lookup"><span data-stu-id="f99ae-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="f99ae-303">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="f99ae-304">これには、選択**開くシーンを追加**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="f99ae-305">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-305">A save window will appear.</span></span>
        
            ![開いているシーン ボタンの追加 をクリック](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="f99ae-307">新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新しいスクリプト フォルダーを作成します。](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="f99ae-309">新たに作成した開く**シーン**フォルダー、し、*ファイル名*: テキスト フィールドに「 **MR_LuisScene**、キーを押します**保存します**。</span><span class="sxs-lookup"><span data-stu-id="f99ae-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![シーンの新しい名前を付けます。](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="f99ae-311">設定に残っている*Build Settings*、ここでは既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="f99ae-312">*Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。</span><span class="sxs-lookup"><span data-stu-id="f99ae-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![プレーヤー設定を開きます。](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="f99ae-314">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="f99ae-315">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="f99ae-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="f99ae-316">**ランタイム バージョンをスクリプト**する必要があります**安定した**(.NET 3.5 相当)。</span><span class="sxs-lookup"><span data-stu-id="f99ae-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="f99ae-317">**バックエンドの scripting**べき **.NET**</span><span class="sxs-lookup"><span data-stu-id="f99ae-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="f99ae-318">**API の互換性レベル**べき **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="f99ae-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![その他の設定を更新します。](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="f99ae-320">内で、**発行の設定**] タブの [**機能**、確認してください。</span><span class="sxs-lookup"><span data-stu-id="f99ae-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="f99ae-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="f99ae-321">**InternetClient**</span></span>
        2. <span data-ttu-id="f99ae-322">**マイク**</span><span class="sxs-lookup"><span data-stu-id="f99ae-322">**Microphone**</span></span>

            ![発行の設定を更新しています。](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="f99ae-324">パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X の R の設定を更新します。](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="f99ae-326">戻り*Build Settings* _Unity C#_ プロジェクトが不要になったグレー; これの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="f99ae-327">ビルド設定ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="f99ae-328">シーンとプロジェクトを保存 (**ファイル > シーン保存/ファイル > プロジェクトを保存**)。</span><span class="sxs-lookup"><span data-stu-id="f99ae-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="f99ae-329">第 4 章 – シーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f99ae-330">スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)、としてプロジェクトにインポート、[カスタム パッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 5 章](#chapter-5--create-the-microphonemanager-class)します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="f99ae-331">空の領域で右クリックし、*階層パネル* **3D オブジェクト**、追加、**平面**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![平面を作成します。](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="f99ae-333">注意を内で右クリックすると、*階層*もう一度選択されている最後のオブジェクトがある場合は、複数のオブジェクトを作成、選択したオブジェクトをする、新しいオブジェクトの親。</span><span class="sxs-lookup"><span data-stu-id="f99ae-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="f99ae-334">階層内の空白領域をクリックし、右クリックし、この問題を回避します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="f99ae-335">次のオブジェクトを追加する上記の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="f99ae-336">*球*</span><span class="sxs-lookup"><span data-stu-id="f99ae-336">*Sphere*</span></span>
    2. <span data-ttu-id="f99ae-337">*円柱*</span><span class="sxs-lookup"><span data-stu-id="f99ae-337">*Cylinder*</span></span>
    3. <span data-ttu-id="f99ae-338">*Cube*</span><span class="sxs-lookup"><span data-stu-id="f99ae-338">*Cube*</span></span>
    4. <span data-ttu-id="f99ae-339">*3D テキスト*</span><span class="sxs-lookup"><span data-stu-id="f99ae-339">*3D Text*</span></span>

4.  <span data-ttu-id="f99ae-340">結果として得られるシーン*階層*次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![シーン階層の設定。](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="f99ae-342">左クリックしてで、 **Main Camera**ことを選択するために見て、*インスペクター パネル*すべて Camera オブジェクトが表示されます、そのコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="f99ae-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="f99ae-343">をクリックして、**コンポーネントの追加**の一番下にあるボタン、*インスペクター パネル*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![オーディオ ソースを追加します。](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="f99ae-345">呼ばれるコンポーネントの検索*オーディオ ソース*の上に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="f99ae-346">確認、*変換*Main Camera のコンポーネント (0,0,0) に設定されて、これを行うキーを押して、**歯車**カメラの横にあるアイコン*変換*コンポーネント選択と**リセット**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="f99ae-347">*変換*し、コンポーネントのようになります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="f99ae-348">*位置*に設定されている**0, 0, 0**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="f99ae-349">*回転*に設定されている**0, 0, 0**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="f99ae-350">Microsoft HoloLens のも、次を変更する必要がありますに含まれています、**カメラ**このコンポーネントでは、 **Main Camera**:</span><span class="sxs-lookup"><span data-stu-id="f99ae-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="f99ae-351">**フラグをオフにします。** 純色です。</span><span class="sxs-lookup"><span data-stu-id="f99ae-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="f99ae-352">**バック グラウンド**' 黒、アルファ 0' – 16 進カラー: #00000000 します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="f99ae-353">左クリックしてで、**平面**をオンにします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="f99ae-354">*インスペクター パネル*設定、*変換*コンポーネントを次の値。</span><span class="sxs-lookup"><span data-stu-id="f99ae-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="f99ae-355">変換 -*位置*</span><span class="sxs-lookup"><span data-stu-id="f99ae-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="f99ae-356">**X**</span><span class="sxs-lookup"><span data-stu-id="f99ae-356">**X**</span></span> | <span data-ttu-id="f99ae-357">**Y**</span><span class="sxs-lookup"><span data-stu-id="f99ae-357">**Y**</span></span>                  | <span data-ttu-id="f99ae-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="f99ae-358">**Z**</span></span> |
    | <span data-ttu-id="f99ae-359">0</span><span class="sxs-lookup"><span data-stu-id="f99ae-359">0</span></span>     | <span data-ttu-id="f99ae-360">-1</span><span class="sxs-lookup"><span data-stu-id="f99ae-360">-1</span></span>                     | <span data-ttu-id="f99ae-361">0</span><span class="sxs-lookup"><span data-stu-id="f99ae-361">0</span></span>     |


10. <span data-ttu-id="f99ae-362">左クリックしてで、**球**をオンにします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="f99ae-363">*インスペクター パネル*設定、*変換*コンポーネントを次の値。</span><span class="sxs-lookup"><span data-stu-id="f99ae-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="f99ae-364">変換 -*位置*</span><span class="sxs-lookup"><span data-stu-id="f99ae-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="f99ae-365">**X**</span><span class="sxs-lookup"><span data-stu-id="f99ae-365">**X**</span></span> | <span data-ttu-id="f99ae-366">**Y**</span><span class="sxs-lookup"><span data-stu-id="f99ae-366">**Y**</span></span>                  | <span data-ttu-id="f99ae-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="f99ae-367">**Z**</span></span> |
    | <span data-ttu-id="f99ae-368">2</span><span class="sxs-lookup"><span data-stu-id="f99ae-368">2</span></span>     | <span data-ttu-id="f99ae-369">1</span><span class="sxs-lookup"><span data-stu-id="f99ae-369">1</span></span>                      | <span data-ttu-id="f99ae-370">2</span><span class="sxs-lookup"><span data-stu-id="f99ae-370">2</span></span>     |

11. <span data-ttu-id="f99ae-371">左クリックしてで、**円柱**をオンにします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="f99ae-372">*インスペクター パネル*設定、*変換*コンポーネントを次の値。</span><span class="sxs-lookup"><span data-stu-id="f99ae-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="f99ae-373">変換 -*位置*</span><span class="sxs-lookup"><span data-stu-id="f99ae-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="f99ae-374">**X**</span><span class="sxs-lookup"><span data-stu-id="f99ae-374">**X**</span></span> | <span data-ttu-id="f99ae-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="f99ae-375">**Y**</span></span>                  | <span data-ttu-id="f99ae-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="f99ae-376">**Z**</span></span> |
    | <span data-ttu-id="f99ae-377">-2</span><span class="sxs-lookup"><span data-stu-id="f99ae-377">-2</span></span>    | <span data-ttu-id="f99ae-378">1</span><span class="sxs-lookup"><span data-stu-id="f99ae-378">1</span></span>                      | <span data-ttu-id="f99ae-379">2</span><span class="sxs-lookup"><span data-stu-id="f99ae-379">2</span></span>     |

12. <span data-ttu-id="f99ae-380">左クリックしてで、**キューブ**をオンにします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="f99ae-381">*インスペクター パネル*設定、*変換*コンポーネントを次の値。</span><span class="sxs-lookup"><span data-stu-id="f99ae-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="f99ae-382">変換 -*位置*</span><span class="sxs-lookup"><span data-stu-id="f99ae-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="f99ae-383">変換 -*回転*</span><span class="sxs-lookup"><span data-stu-id="f99ae-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="f99ae-384">**X**</span><span class="sxs-lookup"><span data-stu-id="f99ae-384">**X**</span></span> | <span data-ttu-id="f99ae-385">**Y**</span><span class="sxs-lookup"><span data-stu-id="f99ae-385">**Y**</span></span>                   | <span data-ttu-id="f99ae-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="f99ae-386">**Z**</span></span> |  \| | <span data-ttu-id="f99ae-387">**X**</span><span class="sxs-lookup"><span data-stu-id="f99ae-387">**X**</span></span> | <span data-ttu-id="f99ae-388">**Y**</span><span class="sxs-lookup"><span data-stu-id="f99ae-388">**Y**</span></span>                  | <span data-ttu-id="f99ae-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="f99ae-389">**Z**</span></span> |
    | <span data-ttu-id="f99ae-390">0</span><span class="sxs-lookup"><span data-stu-id="f99ae-390">0</span></span>     | <span data-ttu-id="f99ae-391">1</span><span class="sxs-lookup"><span data-stu-id="f99ae-391">1</span></span>                       | <span data-ttu-id="f99ae-392">4</span><span class="sxs-lookup"><span data-stu-id="f99ae-392">4</span></span>     |  \| | <span data-ttu-id="f99ae-393">45</span><span class="sxs-lookup"><span data-stu-id="f99ae-393">45</span></span>    | <span data-ttu-id="f99ae-394">45</span><span class="sxs-lookup"><span data-stu-id="f99ae-394">45</span></span>                     | <span data-ttu-id="f99ae-395">0</span><span class="sxs-lookup"><span data-stu-id="f99ae-395">0</span></span>     | 

13. <span data-ttu-id="f99ae-396">左クリックしてで、**新しいテキスト**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="f99ae-397">*インスペクター パネル*設定、*変換*コンポーネントを次の値。</span><span class="sxs-lookup"><span data-stu-id="f99ae-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="f99ae-398">変換 -*位置*</span><span class="sxs-lookup"><span data-stu-id="f99ae-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="f99ae-399">変換 -*スケール*</span><span class="sxs-lookup"><span data-stu-id="f99ae-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="f99ae-400">**X**</span><span class="sxs-lookup"><span data-stu-id="f99ae-400">**X**</span></span> | <span data-ttu-id="f99ae-401">**Y**</span><span class="sxs-lookup"><span data-stu-id="f99ae-401">**Y**</span></span>                  | <span data-ttu-id="f99ae-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="f99ae-402">**Z**</span></span> |  \| | <span data-ttu-id="f99ae-403">**X**</span><span class="sxs-lookup"><span data-stu-id="f99ae-403">**X**</span></span> | <span data-ttu-id="f99ae-404">**Y**</span><span class="sxs-lookup"><span data-stu-id="f99ae-404">**Y**</span></span>               | <span data-ttu-id="f99ae-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="f99ae-405">**Z**</span></span> |
    | <span data-ttu-id="f99ae-406">-2</span><span class="sxs-lookup"><span data-stu-id="f99ae-406">-2</span></span>    | <span data-ttu-id="f99ae-407">6</span><span class="sxs-lookup"><span data-stu-id="f99ae-407">6</span></span>                      | <span data-ttu-id="f99ae-408">9</span><span class="sxs-lookup"><span data-stu-id="f99ae-408">9</span></span>     |  \| | <span data-ttu-id="f99ae-409">0.1</span><span class="sxs-lookup"><span data-stu-id="f99ae-409">0.1</span></span>   | <span data-ttu-id="f99ae-410">0.1</span><span class="sxs-lookup"><span data-stu-id="f99ae-410">0.1</span></span>                 | <span data-ttu-id="f99ae-411">0.1</span><span class="sxs-lookup"><span data-stu-id="f99ae-411">0.1</span></span>   | 

14. <span data-ttu-id="f99ae-412">変更**フォント サイズ**で、**テキスト メッシュ**コンポーネントを**50**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="f99ae-413">変更、*名前*の**テキスト メッシュ**オブジェクトを**テキストのディクテーション**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![3D テキスト オブジェクトを作成します。](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="f99ae-415">パネルの階層構造は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![テキストは、シーン ビューでメッシュします。](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="f99ae-417">最終的なシーンは、次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-417">The final scene should look like the image below:</span></span>

    ![シーンのビュー。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="f99ae-419">第 5 章 – MicrophoneManager クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="f99ae-420">最初のスクリプトを作成するには、 *MicrophoneManager*クラス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="f99ae-421">次に、作成、 *LuisManager*、*ビヘイビアー*クラス、最後に、*視線*クラス (自由と説明がここでは、これらすべてを作成するには各章に到達) します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="f99ae-422">*MicrophoneManager*クラスは責任を負います。</span><span class="sxs-lookup"><span data-stu-id="f99ae-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="f99ae-423">ヘッドセットまたは (方は、既定のものです) のマシンにアタッチされた録音デバイスを検出します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="f99ae-424">音声 (音声) を使用すると、キャプチャし、ディクテーションを使用して、文字列として保存します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="f99ae-425">音声が一時停止すると後でディクテーションを送信、 *LuisManager*クラス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="f99ae-426">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-426">To create this class:</span></span> 

1.  <span data-ttu-id="f99ae-427">右クリックし、*プロジェクト パネル*、**作成 > フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="f99ae-428">フォルダーを呼び出す**スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-428">Call the folder **Scripts**.</span></span> 

    ![[スクリプト] フォルダーを作成します。](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="f99ae-430">**スクリプト**フォルダーが作成されるをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="f99ae-431">その後、そのフォルダー内で右クリックし、**作成 >C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="f99ae-432">スクリプトの名前*MicrophoneManager*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="f99ae-433">ダブルクリックします。 *MicrophoneManager*ファイルを開く*Visual Studio*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="f99ae-434">ファイルの先頭には、次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="f99ae-435">内で、次の変数を追加し、 *MicrophoneManager*クラス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="f99ae-436">コードを*Awake()* と*Start()* 今すぐメソッドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="f99ae-437">これらが、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-437">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  <span data-ttu-id="f99ae-438">メソッドに渡すの開始し、音声のキャプチャを停止する、アプリが使用する必要があります、 *LuisManager*クラスと、すぐにビルドします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  <span data-ttu-id="f99ae-439">追加、*ディクテーション ハンドラー*ですが、音声を置いたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="f99ae-440">このメソッドは合格するテキストをディクテーション、 *LuisManager*クラス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="f99ae-441">削除、 *Update()* メソッドのため、このクラスは使用されません。</span><span class="sxs-lookup"><span data-stu-id="f99ae-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="f99ae-442">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f99ae-443">この時点で表示されるエラーが表示されます、 *Unity エディターのコンソール パネル*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="f99ae-444">これは、コードを参照しているため、 *LuisManager*クラスは次の章で作成されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="f99ae-445">第 6 章 – LUISManager クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="f99ae-446">作成するための時間は、 *LuisManager*クラスは、Azure LUIS サービスへの呼び出しになります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="f99ae-447">このクラスの目的からテキストをディクテーションを受信する、 *MicrophoneManager*クラスし、送信、 *Azure Language Understanding API*分析します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="f99ae-448">このクラスが逆シリアル化、 *JSON*応答の適切なメソッドを呼び出すと、*ビヘイビアー*クラス アクションをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="f99ae-449">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-449">To create this class:</span></span> 

1.  <span data-ttu-id="f99ae-450">ダブルクリック、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="f99ae-451">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="f99ae-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="f99ae-452">スクリプトの名前*LuisManager*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="f99ae-453">Visual Studio で開くことをスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="f99ae-454">ファイルの先頭には、次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="f99ae-455">3 つのクラスを作成して開始する**内**、 *LuisManager*クラス (に同じスクリプト ファイル内の上、 *Start()* メソッド) を表す、逆シリアル化されました。Azure からの JSON 応答です。</span><span class="sxs-lookup"><span data-stu-id="f99ae-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  <span data-ttu-id="f99ae-456">次に、内部では、次の変数を追加、 *LuisManager*クラス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="f99ae-457">で LUIS エンドポイントを今すぐ配置してください (これは、LUIS ポータルから必要があります)。</span><span class="sxs-lookup"><span data-stu-id="f99ae-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="f99ae-458">コードを*Awake()* メソッドは今すぐ追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="f99ae-459">このメソッドが、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="f99ae-460">このアプリケーションは、送信から受信したディクテーションに使用する方法を作成する必要があるので、 *MicrophoneManager*クラスを*LUIS*、受信して、応答を逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="f99ae-461">インスタンスに渡される目的、および関連付けられているエンティティは、の値が決まると、*ビヘイビアー*目的のアクションをトリガーするクラス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. <span data-ttu-id="f99ae-462">という新しいメソッドを作成する*AnalyseResponseElements()* 、その結果を読み取ることが*AnalysedQuery*し、エンティティを決定します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="f99ae-463">これらのエンティティが決まったらのインスタンスに渡されます、*ビヘイビアー*アクションで使用するクラス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognised intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="f99ae-464">削除、 *Start()* と*Update()* メソッドをこのクラスはそれらを使用しないためです。</span><span class="sxs-lookup"><span data-stu-id="f99ae-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="f99ae-465">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="f99ae-466">表示されているいくつかのエラーが表示されますこの時点で、 *Unity エディターのコンソール パネル*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="f99ae-467">これは、コードを参照しているため、*ビヘイビアー*クラスは次の章で作成されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="f99ae-468">第 7 章 – 動作クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="f99ae-469">*ビヘイビアー*クラスによって提供されるエンティティを使用してアクションをトリガーする、 *LuisManager*クラス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="f99ae-470">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-470">To create this class:</span></span> 

1.  <span data-ttu-id="f99ae-471">ダブルクリック、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="f99ae-472">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="f99ae-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="f99ae-473">スクリプトの名前*ビヘイビアー*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="f99ae-474">ファイルを開くスクリプトをダブルクリックします。 *Visual Studio*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="f99ae-475">内で、次の変数を追加し、*ビヘイビアー*クラス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="f99ae-476">追加、 *Awake()* メソッドのコード。</span><span class="sxs-lookup"><span data-stu-id="f99ae-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="f99ae-477">このメソッドが、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="f99ae-478">によって、次のメソッドが呼び出される、 *LuisManager*オブジェクトが、クエリの対象であることを確認し、適切なアクションをトリガーして (これは、先ほど作成した) クラス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  <span data-ttu-id="f99ae-479">追加、 *FindTarget()* メソッドの判断するために、 *GameObjects*目的は、現在のターゲットであります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="f99ae-480">このメソッドの既定値をターゲット、 *GameObject*される"gazed"エンティティの明示的なターゲットが定義されていない場合。</span><span class="sxs-lookup"><span data-stu-id="f99ae-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="f99ae-481">削除、 *Start()* と*Update()* メソッドをこのクラスはそれらを使用しないためです。</span><span class="sxs-lookup"><span data-stu-id="f99ae-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="f99ae-482">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="f99ae-483">章 – 8 視線の先クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="f99ae-484">このアプリを完了する必要がある最後のクラスは、*視線*クラス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="f99ae-485">このクラスへの参照を更新する、 *GameObject*現在のユーザーのビジュアル フォーカスします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="f99ae-486">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-486">To create this Class:</span></span> 

1.  <span data-ttu-id="f99ae-487">ダブルクリック、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="f99ae-488">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="f99ae-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="f99ae-489">スクリプトの名前*視線*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="f99ae-490">ファイルを開くスクリプトをダブルクリックします。 *Visual Studio*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="f99ae-491">このクラスに次のコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-491">Insert the following code for this class:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  <span data-ttu-id="f99ae-492">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="f99ae-493">第 9 章 – シーンのセットアップの完了</span><span class="sxs-lookup"><span data-stu-id="f99ae-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="f99ae-494">シーンのセットアップを完了するには、Scripts フォルダーから作成した各スクリプトをドラッグして、 **Main Camera**オブジェクト、*階層パネル*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="f99ae-495">選択、 **Main Camera**を見て、*インスペクター パネル*、アタッチした各スクリプトに表示できるし、まだ設定している各スクリプトにパラメーターがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![カメラの参照のターゲットを設定します。](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="f99ae-497">これらのパラメーターを正しく設定するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="f99ae-498">*MicrophoneManager*:</span><span class="sxs-lookup"><span data-stu-id="f99ae-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="f99ae-499">*階層パネル*、ドラッグ、**テキストのディクテーション**オブジェクトを**ディクテーション テキスト**パラメーター値のボックスです。</span><span class="sxs-lookup"><span data-stu-id="f99ae-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="f99ae-500">*ビヘイビアー*から、*階層パネル*:</span><span class="sxs-lookup"><span data-stu-id="f99ae-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="f99ae-501">ドラッグ、**球**オブジェクトを*球*参照ターゲット ボックス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="f99ae-502">ドラッグ、**円柱**に、*円柱*参照ターゲット ボックス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="f99ae-503">ドラッグ、**キューブ**に、*キューブ*参照ターゲット ボックス。</span><span class="sxs-lookup"><span data-stu-id="f99ae-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="f99ae-504">*視線*:</span><span class="sxs-lookup"><span data-stu-id="f99ae-504">*Gaze*:</span></span>

        - <span data-ttu-id="f99ae-505">設定、*最大距離の視線*に**300** (されていない) 場合。</span><span class="sxs-lookup"><span data-stu-id="f99ae-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="f99ae-506">結果は、次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-506">The result should look like the image below:</span></span>

    ![設定、カメラの参照のターゲットを表示するようになりました。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="f99ae-508">第 10 章 – Unity エディターでのテスト</span><span class="sxs-lookup"><span data-stu-id="f99ae-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="f99ae-509">シーンのセットアップを正しく実装することをテストします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="f99ae-510">次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f99ae-510">Ensure that:</span></span>

-   <span data-ttu-id="f99ae-511">関連付けられているすべてのスクリプト、 **Main Camera**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f99ae-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="f99ae-512">内のすべてのフィールド、*カメラ インスペクター [メイン] パネル*が適切に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="f99ae-513">キーを押して、**再生**ボタン、 *Unity エディター*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="f99ae-514">アプリは、添付のイマーシブ ヘッドセット内で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="f99ae-515">など、いくつかの発話を試してください。</span><span class="sxs-lookup"><span data-stu-id="f99ae-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="f99ae-516">変更する既定のオーディオ デバイスについて、Unity コンソールで、エラーが発生した場合期待どおりにシーンが機能しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="f99ae-517">これは、複合現実ポータルが設定されているヘッドセットの組み込みのマイクを扱う方法に起因します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="f99ae-518">このエラーを参照してください、単にシーンを停止、再開し、として動作する必要がありますが必要です。</span><span class="sxs-lookup"><span data-stu-id="f99ae-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="f99ae-519">第 11 章 – ビルドおよびサイドロード UWP ソリューション</span><span class="sxs-lookup"><span data-stu-id="f99ae-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="f99ae-520">アプリケーションが Unity エディターでの作業でことを確認して後、は、構築およびデプロイする準備が完了したら。</span><span class="sxs-lookup"><span data-stu-id="f99ae-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="f99ae-521">作成する方法。</span><span class="sxs-lookup"><span data-stu-id="f99ae-521">To Build:</span></span>

1.  <span data-ttu-id="f99ae-522">現在のシーンを保存 をクリックして**ファイル > 保存**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="f99ae-523">移動して**ファイル > のビルド設定**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="f99ae-524">というボックスをオンに**UnityC#プロジェクト**(が表示されると、UWP プロジェクトが作成されると、コードのデバッグに便利です。</span><span class="sxs-lookup"><span data-stu-id="f99ae-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="f99ae-525">をクリックして**開くシーンを追加**、 をクリックし、**ビルド**。</span><span class="sxs-lookup"><span data-stu-id="f99ae-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![ビルド設定ウィンドウ](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="f99ae-527">ソリューションをビルドするフォルダーを選択するように促されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="f99ae-528">作成、*ビルド*フォルダーとそのフォルダー内には、任意の適切な名前を別のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="f99ae-529">クリックして**フォルダーの選択**をその場所にビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="f99ae-530">![ビルド フォルダーを作成する](images/AzureLabs-Lab3-44.png)
    ![選択フォルダーを作成します。](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="f99ae-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="f99ae-531">1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了した、開く必要がありますが、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="f99ae-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="f99ae-532">ローカル コンピューターの展開。</span><span class="sxs-lookup"><span data-stu-id="f99ae-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="f99ae-533">*Visual Studio*で作成されたソリューション ファイルを開き、[前のチャプター](#chapter-10--test-in-the-unity-editor)します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="f99ae-534">**ソリューション プラットフォーム**、 **x86**、**ローカル マシン**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="f99ae-535">**ソリューション構成**選択**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="f99ae-536">Microsoft HoloLens にすることがあります方が簡単なこれを設定する*リモート マシン*、するは、コンピューターにテザリングされたしないようにします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="f99ae-537">ただし、次の操作も必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="f99ae-538">把握、 **IP アドレス**内では、HoloLens の*設定 > ネットワークとインターネット > Wi-fi > 詳細オプション*;、IPv4 では、アドレスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="f99ae-539">確認**開発者モード**は**で**; で見つかった*設定 > 更新とセキュリティ > 開発者向け*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![アプリをデプロイします。](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="f99ae-541">移動して、**ビルド メニューの** をクリック**ソリューションの配置**をコンピューターにアプリケーションをサイドローディングします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="f99ae-542">アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="f99ae-543">アプリがアクセスを承認することを求められます、起動されると、_マイク_します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="f99ae-544">使用して、*モーションのコント ローラー*、または*音声入力*、または*キーボード*キーを押す、**はい**ボタン。</span><span class="sxs-lookup"><span data-stu-id="f99ae-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="f99ae-545">第 12 章 –、LUIS サービスの向上</span><span class="sxs-lookup"><span data-stu-id="f99ae-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="f99ae-546">この章では非常に重要ですし、LUIS サービスの精度を向上させるため、バッキングストアファイルに繰り返しを複数回に付けする必要があります。 これを完了することを確認します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-546">This chapter is incredibly important, and may need to be interated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="f99ae-547">LUIS によって提供される知識のレベルを向上させるためには、新しい発話をキャプチャして LUIS アプリを再トレーニングに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="f99ae-548">たとえば、LUIS"Increase"を理解して「アップサイズ」のトレーニングが可能性がありますが、アプリ「拡大」などの単語についても理解を使用することはありませんか。</span><span class="sxs-lookup"><span data-stu-id="f99ae-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="f99ae-549">アプリケーションは、何回か使用している、LUIS によって収集されると、LUIS のポータルで使用可能なすべての説明になります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="f99ae-550">その後、ポータル アプリケーションに移動[リンク](https://www.luis.ai/home)、およびログイン。</span><span class="sxs-lookup"><span data-stu-id="f99ae-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="f99ae-551">MS の資格情報でログインした後は、をクリックして*アプリ名*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="f99ae-552">をクリックして、**エンドポイント発話を確認**ページの左側にボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![発話を確認してください。](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="f99ae-554">複合現実のアプリケーションが送信に LUIS 発話の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![発話の一覧](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="f99ae-556">強調表示されたいくつかがわかります*エンティティ*します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="f99ae-557">強調表示されている各単語、ポインターを合わせるとすると、それぞれの発話を確認でき、エンティティが認識されている正しく、エンティティが正しくないが、エンティティが欠落を判断することができます。</span><span class="sxs-lookup"><span data-stu-id="f99ae-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="f99ae-558">上記の例では、それが見つかったこと「スピア型」という単語が強調表示されて、ターゲットとしてそのため、ポインターを合わせると、マウスを使用して単語をクリックして実行されると、誤りを修正するために必要な**ラベルの削除**します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="f99ae-559">![発話の確認](images/AzureLabs-Lab3-49.png)
![ラベル イメージの削除](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="f99ae-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="f99ae-560">言葉を完全に間違っている場合は、削除するを使用して、**削除**画面の右側にあるボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![間違った発話を削除します。](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="f99ae-562">使用して内容を理解を検証するには、LUIS が発話を正しく解釈がある場合、または、**配置目的に追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99ae-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![配置済みのインテントに追加します。](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="f99ae-564">表示されているすべての発話を並べ替えた後以上が使用可能なかどうかに表示するページを再読み込みをしてください。</span><span class="sxs-lookup"><span data-stu-id="f99ae-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="f99ae-565">アプリケーションについての理解を向上させるために可能な回数だけこのプロセスを繰り返す非常に重要ですが。</span><span class="sxs-lookup"><span data-stu-id="f99ae-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="f99ae-566">**楽しんでください！**</span><span class="sxs-lookup"><span data-stu-id="f99ae-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="f99ae-567">完成した LUIS 統合アプリケーション</span><span class="sxs-lookup"><span data-stu-id="f99ae-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="f99ae-568">これで、Azure Language Understanding Intelligence Service、ユーザーの質問を理解して、その情報を活用する mixed reality アプリを構築します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![ラボの結果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="f99ae-570">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="f99ae-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="f99ae-571">手順 1</span><span class="sxs-lookup"><span data-stu-id="f99ae-571">Exercise 1</span></span>

<span data-ttu-id="f99ae-572">このアプリケーションの使用中にいる場合、Floor オブジェクトを見つめます、色を変更するように要求して、その処理を行いますがわかります。</span><span class="sxs-lookup"><span data-stu-id="f99ae-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="f99ae-573">床面の色を変更することから、アプリケーションを停止する方法を操作することができますか。</span><span class="sxs-lookup"><span data-stu-id="f99ae-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="f99ae-574">手順 2</span><span class="sxs-lookup"><span data-stu-id="f99ae-574">Exercise 2</span></span>

<span data-ttu-id="f99ae-575">シーン内のオブジェクトの機能の追加の LUIS とアプリの機能の拡張をお試しください。たとえば、ヒット ポイントは、どのようなユーザーによって言うし、現在のシーン オブジェクトと共にそれらのオブジェクトを使用して、既存のコマンドを使用できる視線の先に新しいオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99ae-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
