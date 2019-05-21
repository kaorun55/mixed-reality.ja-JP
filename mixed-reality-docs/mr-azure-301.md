---
title: MR および Azure 301 - 言語の翻訳
description: このコースでは、複合現実のアプリケーション内で Azure Translator Text API を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、translator のテキスト、没入型、hololens、vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603610"
---
>[!NOTE]
><span data-ttu-id="1b716-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1b716-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1b716-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="1b716-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1b716-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1b716-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1b716-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1b716-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="1b716-110">MR と Azure 301:言語翻訳</span><span class="sxs-lookup"><span data-stu-id="1b716-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="1b716-111">このコースでは、Translator Text API、Azure Cognitive Services を使用して、複合現実アプリケーションに翻訳機能を追加する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="1b716-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![最終的な製品](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="1b716-113">Translator Text API は、翻訳のほぼリアルタイムで機能するサービスです。</span><span class="sxs-lookup"><span data-stu-id="1b716-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="1b716-114">サービスはクラウド ベースであり、REST API 呼び出しを使用して、アプリが行うことができますを別の言語のテキストを翻訳するニューラル機械翻訳テクノロジを使用します。</span><span class="sxs-lookup"><span data-stu-id="1b716-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="1b716-115">詳細については、次を参照してください。、 [Translator Text API の Azure ページ](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)します。</span><span class="sxs-lookup"><span data-stu-id="1b716-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="1b716-116">このコースを修了、以下を実行できる必要が複合現実のアプリケーションが用意されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="1b716-117">ユーザーは、没入型の (VR) ヘッドセットに接続されているマイク (または、HoloLens の内蔵マイク) に向かって話します。</span><span class="sxs-lookup"><span data-stu-id="1b716-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="1b716-118">アプリは、ディクテーションをキャプチャし、Azure の Translator Text API に送信します。</span><span class="sxs-lookup"><span data-stu-id="1b716-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="1b716-119">Unity シーン内の単純な UI グループで、変換結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="1b716-120">このコースでは、Unity に基づくサンプル アプリケーションに Translator サービスから結果を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1b716-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="1b716-121">最大をカスタム アプリケーションをビルドしている場合にこれらの概念を適用することがあります。</span><span class="sxs-lookup"><span data-stu-id="1b716-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="1b716-122">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="1b716-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1b716-123">コース</span><span class="sxs-lookup"><span data-stu-id="1b716-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1b716-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1b716-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1b716-125"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="1b716-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1b716-126">MR と Azure 301:言語翻訳</span><span class="sxs-lookup"><span data-stu-id="1b716-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="1b716-127">✔️</span><span class="sxs-lookup"><span data-stu-id="1b716-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1b716-128">✔️</span><span class="sxs-lookup"><span data-stu-id="1b716-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="1b716-129">このコースが主に Windows Mixed Reality 没入型 (VR) ヘッドセットを重点的に Microsoft HoloLens には、このコースで学習する内容を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1b716-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="1b716-130">コースを実行するとき、HoloLens をサポートするために必要な場合があります変更でノートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="1b716-131">HoloLens を使用する場合は、音声キャプチャ中にいくつかのエコーが気付きです。</span><span class="sxs-lookup"><span data-stu-id="1b716-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1b716-132">前提条件</span><span class="sxs-lookup"><span data-stu-id="1b716-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="1b716-133">このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。</span><span class="sxs-lookup"><span data-stu-id="1b716-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="1b716-134">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 5 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1b716-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="1b716-135">内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)ことについては、このコースでとまったく同じで見つかりますの下に記載されているものよりも新しいソフトウェアでどのようなことは仮定されませんが、記事.</span><span class="sxs-lookup"><span data-stu-id="1b716-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="1b716-136">次のハードウェアとソフトウェアこのコースをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1b716-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="1b716-137">開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発</span><span class="sxs-lookup"><span data-stu-id="1b716-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="1b716-138">Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="1b716-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1b716-139">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="1b716-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1b716-140">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="1b716-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1b716-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1b716-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="1b716-142">A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効</span><span class="sxs-lookup"><span data-stu-id="1b716-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="1b716-143">(ヘッドセットには、組み込みのマイクとスピーカーを持っていない) 場合は、内蔵マイクでヘッドフォン</span><span class="sxs-lookup"><span data-stu-id="1b716-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="1b716-144">Azure のセットアップや変換の取得のためのインターネット アクセス</span><span class="sxs-lookup"><span data-stu-id="1b716-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="1b716-145">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="1b716-145">Before you start</span></span>

- <span data-ttu-id="1b716-146">このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。</span><span class="sxs-lookup"><span data-stu-id="1b716-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="1b716-147">このチュートリアルのコードは、PC に接続されている既定のマイク デバイスから記録できます。</span><span class="sxs-lookup"><span data-stu-id="1b716-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="1b716-148">既定のマイク デバイスが音声のキャプチャに使用する予定のデバイスに設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1b716-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="1b716-149">ディクテーションを有効にする PC を許可するには**設定 > プライバシーに関する > 読み上げ、手描き入力機能 (&) を入力する** ボタンを選択**音声サービスをオンにして、入力候補**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="1b716-150">マイク、ヘッドホンを接続されている (またはに組み込まれて) を使用している場合、ヘッドセット、オプションの確認で「マイ ヘッドセットを着用するときに切り替えるヘッドセット マイク」がオン**設定 > 複合現実 > オーディオおよび音声**。</span><span class="sxs-lookup"><span data-stu-id="1b716-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![複合現実の設定](images/AzureLabs-Lab1-00-5.png)

   ![マイクの設定](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="1b716-153">このラボのイマーシブ ヘッドセットを開発している場合は、オーディオ出力デバイスの問題を発生する可能性がありますに注意します。</span><span class="sxs-lookup"><span data-stu-id="1b716-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="1b716-154">これは、Unity、以降のバージョンの Unity (Unity 2018.2) での問題が原因です。</span><span class="sxs-lookup"><span data-stu-id="1b716-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="1b716-155">この問題は、Unity が実行時に既定のオーディオ出力デバイスを変更することを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="1b716-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="1b716-156">回避策としては、上記の手順を完了したことを確認して閉じて再エディターを開き、この問題がそれ自体を提示します。</span><span class="sxs-lookup"><span data-stu-id="1b716-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="1b716-157">第 1 章 – Azure Portal</span><span class="sxs-lookup"><span data-stu-id="1b716-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="1b716-158">Azure Translator API を使用するには、アプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="1b716-159">ログイン、 [Azure Portal](https://portal.azure.com)します。</span><span class="sxs-lookup"><span data-stu-id="1b716-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="1b716-160">Azure アカウントがいない場合は、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="1b716-161">クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="1b716-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="1b716-162">ログインした後は、をクリックして**新規**上で左上隅にある"Translator Text API です"を検索。</span><span class="sxs-lookup"><span data-stu-id="1b716-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="1b716-163">選択**入力**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-163">Select **Enter**.</span></span>

    ![新しいリソース](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="1b716-165">単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。</span><span class="sxs-lookup"><span data-stu-id="1b716-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="1b716-166">新しいページがの説明を入力、 *Translator Text API*サービス。</span><span class="sxs-lookup"><span data-stu-id="1b716-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="1b716-167">このページの左下にある at、**作成**ボタンは、この関連付けサービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1b716-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Translator Text API サービスを作成します。](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="1b716-169">クリックすると**作成**:</span><span class="sxs-lookup"><span data-stu-id="1b716-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="1b716-170">必要な挿入**名前**このサービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="1b716-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="1b716-171">適切な選択**サブスクリプション**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="1b716-172">選択、**価格レベル**場合、これは、最初に、適切な時間を作成する、 *Translator のテキスト サービス*、(F0 という名前)、free レベルを使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="1b716-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="1b716-173">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="1b716-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="1b716-174">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="1b716-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1b716-175">勧めします (例: これらのラボ) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。</span><span class="sxs-lookup"><span data-stu-id="1b716-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="1b716-176">詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="1b716-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="1b716-177">確認、**場所**(新しいリソース グループを作成する) 場合は、リソース グループ。</span><span class="sxs-lookup"><span data-stu-id="1b716-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="1b716-178">場所は、アプリケーションが実行リージョンにあるが理想的です。</span><span class="sxs-lookup"><span data-stu-id="1b716-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="1b716-179">一部の Azure 資産は特定のリージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1b716-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="1b716-180">また、このサービスに適用される条件を理解したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="1b716-181">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b716-181">Select **Create**.</span></span>

        ![[作成] ボタンを選択します。](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="1b716-183">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="1b716-184">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Azure サービスの作成の通知](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="1b716-186">新しいサービス インスタンスを探索する通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b716-186">Click on the notification to explore your new Service instance.</span></span> 

    ![リソースのポップアップに移動します。](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="1b716-188">をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b716-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="1b716-189">新しい Translator Text API のサービス インスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Translator Text API のサービス ページ](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="1b716-191">このチュートリアルでは、内でアプリケーションがサービスのサブスクリプション キーを使用して、これは、サービスへの呼び出しを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="1b716-192">*クイック スタート*のページ、 *Translator Text*サービスは、最初のステップに移動します*キーを取得する*、 をクリック**キー** (することできますまたこれは実現キー アイコンによって示される、サービスのナビゲーション メニューにある青いハイパーリンク キーをクリックして)。</span><span class="sxs-lookup"><span data-stu-id="1b716-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="1b716-193">これが明らかに、サービス*キー*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="1b716-194">このプロジェクトの後半で必要になるため、表示されているキーの 1 つのコピーを実行します。</span><span class="sxs-lookup"><span data-stu-id="1b716-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="1b716-195">第 2 章 – Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="1b716-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="1b716-196">設定して、mixed reality イマーシブ ヘッドセットをテストします。</span><span class="sxs-lookup"><span data-stu-id="1b716-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="1b716-197">アニメーション コント ローラーは、このコースの必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1b716-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="1b716-198">イマーシブ ヘッドセットの設定をサポートする場合は、次のようにしてください。[次の手順に従って](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)します。</span><span class="sxs-lookup"><span data-stu-id="1b716-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="1b716-199">次が複合現実での開発の一般的な設定と、そのため、他のプロジェクトの適切なテンプレートには。</span><span class="sxs-lookup"><span data-stu-id="1b716-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="1b716-200">開いている*Unity*クリック**新規**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-200">Open *Unity* and click **New**.</span></span> 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="1b716-202">これで、Unity プロジェクト名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="1b716-203">挿入**MR_Translation**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="1b716-204">必ず、プロジェクトの種類に設定されて**3D**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="1b716-205">設定、*場所*に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。</span><span class="sxs-lookup"><span data-stu-id="1b716-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="1b716-206">をクリックし、**プロジェクトの作成**です。</span><span class="sxs-lookup"><span data-stu-id="1b716-206">Then, click **Create project**.</span></span>

    ![新しい Unity プロジェクトの詳細を提供します。](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="1b716-208">既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="1b716-209">移動して**編集 > 設定**し、新しいウィンドウに移動**外部ツール**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="1b716-210">変更**External Script Editor**に**Visual Studio 2017**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="1b716-211">閉じる、**設定**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="1b716-211">Close the **Preferences** window.</span></span>

    ![スクリプト エディターの基本設定を更新します。](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="1b716-213">次に移動**ファイル > Build Settings**にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして、**プラットフォームの切り替え**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b716-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![[設定] ウィンドウ切り替え UWP プラットフォームをビルドします。](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="1b716-215">移動して**ファイル > Build Settings**ことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1b716-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="1b716-216">**デバイスを対象に**に設定されている**任意のデバイス**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="1b716-217">Microsoft HoloLens、設定**ターゲット デバイス**に*HoloLens*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="1b716-218">**ビルドの種類**に設定されている**D3D**</span><span class="sxs-lookup"><span data-stu-id="1b716-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="1b716-219">**SDK**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="1b716-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="1b716-220">**Visual Studio バージョン**に設定されている**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="1b716-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="1b716-221">**ビルドおよび実行**に設定されている**ローカル マシン**</span><span class="sxs-lookup"><span data-stu-id="1b716-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="1b716-222">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="1b716-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="1b716-223">これには、選択**開くシーンを追加**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="1b716-224">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-224">A save window will appear.</span></span>

            ![開いているシーン ボタンの追加 をクリック](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="1b716-226">新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新しいスクリプト フォルダーを作成します。](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="1b716-228">新たに作成した開く**シーン**フォルダー、し、*ファイル名*: テキスト フィールドに「 **MR_TranslationScene**、キーを押します**保存します**。</span><span class="sxs-lookup"><span data-stu-id="1b716-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![シーンの新しい名前を付けます。](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="1b716-230">注意してください、内の Unity シーンを保存する必要があります、*資産*フォルダー、Unity プロジェクトに関連付けられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="1b716-231">Unity プロジェクトの構造の一般的な方法は、シーン フォルダー (およびその他の同様のフォルダー) を作成します。</span><span class="sxs-lookup"><span data-stu-id="1b716-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="1b716-232">設定に残っている*Build Settings*、ここでは既定値として残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="1b716-233">*Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。</span><span class="sxs-lookup"><span data-stu-id="1b716-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![プレーヤー設定を開きます。](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="1b716-235">このパネルは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="1b716-236">**その他の設定** タブ。</span><span class="sxs-lookup"><span data-stu-id="1b716-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="1b716-237">**ランタイム バージョンをスクリプト**する必要があります**安定した**(.NET 3.5 相当)。</span><span class="sxs-lookup"><span data-stu-id="1b716-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="1b716-238">**バックエンドの scripting**べき **.NET**</span><span class="sxs-lookup"><span data-stu-id="1b716-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="1b716-239">**API の互換性レベル**べき **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="1b716-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![その他の設定を更新します。](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="1b716-241">内で、**発行の設定**] タブの [**機能**、確認してください。</span><span class="sxs-lookup"><span data-stu-id="1b716-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="1b716-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="1b716-242">**InternetClient**</span></span>
        2. <span data-ttu-id="1b716-243">**マイク**</span><span class="sxs-lookup"><span data-stu-id="1b716-243">**Microphone**</span></span>

            ![発行の設定を更新しています。](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="1b716-245">パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X の R の設定を更新します。](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="1b716-247">戻り**Build Settings**、 *UnityC#プロジェクト*が不要になったグレー; これの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1b716-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="1b716-248">ビルド設定ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1b716-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="1b716-249">シーンとプロジェクトを保存 (**ファイル > シーン保存/ファイル > プロジェクトを保存**)。</span><span class="sxs-lookup"><span data-stu-id="1b716-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="1b716-250">第 3 章 – メイン カメラのセットアップ</span><span class="sxs-lookup"><span data-stu-id="1b716-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b716-251">スキップする場合、 *Unity を設定する*のこのコンポーネントである、コース、コードにまっすぐコンティニュし、自由に[ダウンロードこの .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)、としてプロジェクトにインポート、 [ *カスタム パッケージ*](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 5 章](#chapter-5--create-the-results-class)します。</span><span class="sxs-lookup"><span data-stu-id="1b716-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="1b716-252">Unity プロジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="1b716-253">*階層パネル*、という名前のオブジェクトが表示されます**Main Camera**、「内部」アプリケーションが表示されたら、このオブジェクトは、"head"の観点を表します。</span><span class="sxs-lookup"><span data-stu-id="1b716-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="1b716-254">選択する前にある Unity ダッシュ ボードで、**メイン カメラの GameObject**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="1b716-255">表示になります、*インスペクター パネル*(一般にダッシュ ボードで、右側にあります) をさまざまなコンポーネントが表示されます*GameObject*で*変換*後に、上部にある*カメラ*、およびその他のコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="1b716-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="1b716-256">これが正しく配置されているため、メイン カメラの変換をリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="1b716-257">これを行うには、選択、**歯車**カメラの横にあるアイコン*変換*コンポーネント、および選択**リセット**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![メイン カメラの変換をリセットします。](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="1b716-259">*変換*し、コンポーネントのようになります。</span><span class="sxs-lookup"><span data-stu-id="1b716-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="1b716-260">*位置*に設定されている**0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="1b716-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="1b716-261">*回転*に設定されている**0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="1b716-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="1b716-262">*スケール*に設定されている**1, 1, 1**</span><span class="sxs-lookup"><span data-stu-id="1b716-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![カメラの情報を変換します。](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="1b716-264">[次へ]、 **Main Camera**選択したオブジェクトを参照してください、**コンポーネントの追加**の一番下にあるボタン、*インスペクター パネル*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="1b716-265">そのボタンを選択し、検索 (入力するか*オーディオ ソース*検索フィールドまたはセクションでは、移動に) と呼ばれるコンポーネントの**オーディオ ソース**次に示すようを選択します (enter キーを押しに機能します)。</span><span class="sxs-lookup"><span data-stu-id="1b716-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="1b716-266">*オーディオ ソース*コンポーネントに追加されます、 **Main Camera**、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="1b716-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![オーディオ ソース コンポーネントを追加します。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="1b716-268">Microsoft HoloLens のも、次を変更する必要がありますに含まれています、**カメラ**コンポーネントを**Main Camera**:</span><span class="sxs-lookup"><span data-stu-id="1b716-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="1b716-269">**フラグをオフにします。** 純色です。</span><span class="sxs-lookup"><span data-stu-id="1b716-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="1b716-270">**バック グラウンド**' 黒、アルファ 0' – 16 進カラー: #00000000 します。</span><span class="sxs-lookup"><span data-stu-id="1b716-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="1b716-271">第 4 章 – セットアップ デバッグ キャンバス</span><span class="sxs-lookup"><span data-stu-id="1b716-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="1b716-272">入力と変換の出力を表示するには、基本的な UI を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="1b716-273">このコースでは、いくつかの 'Text' オブジェクト データを表示すると、キャンバスの UI オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="1b716-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="1b716-274">空の領域で右クリックし、*階層パネル* **UI**、追加、**キャンバス**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![新しいキャンバス UI オブジェクトを追加します。](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="1b716-276">選択したら、キャンバス オブジェクトに、*インスペクター パネル*(コンポーネント内で、「キャンバス」)、次のように変更します。**レンダリング モード**に**ワールド空間**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="1b716-277">次のパラメーターを次に、変更、*インスペクター パネルの Rect 変換*:</span><span class="sxs-lookup"><span data-stu-id="1b716-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="1b716-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="1b716-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="1b716-279">*幅*500 -</span><span class="sxs-lookup"><span data-stu-id="1b716-279">*Width* -    500</span></span>
    3. <span data-ttu-id="1b716-280">*高さ*300 -</span><span class="sxs-lookup"><span data-stu-id="1b716-280">*Height* -   300</span></span>
    4. <span data-ttu-id="1b716-281">*スケール* - **X** 0.13 **Y** 0.13 **Z** 0.13</span><span class="sxs-lookup"><span data-stu-id="1b716-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![キャンバスの四角形の変換を更新します。](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="1b716-283">右クリックして、**キャンバス**で、*階層パネル* **UI**、追加、**パネル**。</span><span class="sxs-lookup"><span data-stu-id="1b716-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="1b716-284">これは、**パネル**シーンに表示されるテキストの背景を提供します。</span><span class="sxs-lookup"><span data-stu-id="1b716-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="1b716-285">右クリックして、**パネル**で、*階層パネル* **UI**、追加、**テキスト オブジェクト**。</span><span class="sxs-lookup"><span data-stu-id="1b716-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="1b716-286">合計で 4 つの UI テキスト オブジェクトを作成するまで、同じプロセスを繰り返します (ヒント: 押すだけ選択されている最初の 'Text' オブジェクトがあれば、 **Ctrl + が '** 合計で 4 つの操作をした後、複製する)。</span><span class="sxs-lookup"><span data-stu-id="1b716-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="1b716-287">各**テキスト オブジェクト**をことを選択して、次の表で、パラメーターを設定する、*インスペクター パネル*。</span><span class="sxs-lookup"><span data-stu-id="1b716-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="1b716-288">*Rect 変換*コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="1b716-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="1b716-289">名前</span><span class="sxs-lookup"><span data-stu-id="1b716-289">Name</span></span>                   | <span data-ttu-id="1b716-290">変換 -*位置*</span><span class="sxs-lookup"><span data-stu-id="1b716-290">Transform - *Position*</span></span>             | <span data-ttu-id="1b716-291">幅</span><span class="sxs-lookup"><span data-stu-id="1b716-291">Width</span></span>      | <span data-ttu-id="1b716-292">高さ</span><span class="sxs-lookup"><span data-stu-id="1b716-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="1b716-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="1b716-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="1b716-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="1b716-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="1b716-295">300</span><span class="sxs-lookup"><span data-stu-id="1b716-295">300</span></span>        | <span data-ttu-id="1b716-296">30</span><span class="sxs-lookup"><span data-stu-id="1b716-296">30</span></span>        |
        | <span data-ttu-id="1b716-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="1b716-297">AzureResponseLabel</span></span>     | <span data-ttu-id="1b716-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="1b716-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="1b716-299">300</span><span class="sxs-lookup"><span data-stu-id="1b716-299">300</span></span>        | <span data-ttu-id="1b716-300">30</span><span class="sxs-lookup"><span data-stu-id="1b716-300">30</span></span>        |
        | <span data-ttu-id="1b716-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="1b716-301">DictationLabel</span></span>         | <span data-ttu-id="1b716-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="1b716-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="1b716-303">300</span><span class="sxs-lookup"><span data-stu-id="1b716-303">300</span></span>        | <span data-ttu-id="1b716-304">30</span><span class="sxs-lookup"><span data-stu-id="1b716-304">30</span></span>        |
        | <span data-ttu-id="1b716-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="1b716-305">TranslationResultLabel</span></span> | <span data-ttu-id="1b716-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="1b716-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="1b716-307">300</span><span class="sxs-lookup"><span data-stu-id="1b716-307">300</span></span>        | <span data-ttu-id="1b716-308">30</span><span class="sxs-lookup"><span data-stu-id="1b716-308">30</span></span>        |


    2. <span data-ttu-id="1b716-309">**テキスト (スクリプト)** コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="1b716-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="1b716-310">名前</span><span class="sxs-lookup"><span data-stu-id="1b716-310">Name</span></span>                   | <span data-ttu-id="1b716-311">Text</span><span class="sxs-lookup"><span data-stu-id="1b716-311">Text</span></span>               | <span data-ttu-id="1b716-312">フォント サイズ</span><span class="sxs-lookup"><span data-stu-id="1b716-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="1b716-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="1b716-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="1b716-314">マイクの状態:</span><span class="sxs-lookup"><span data-stu-id="1b716-314">Microphone Status:</span></span> | <span data-ttu-id="1b716-315">20</span><span class="sxs-lookup"><span data-stu-id="1b716-315">20</span></span>           |
        | <span data-ttu-id="1b716-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="1b716-316">AzureResponseLabel</span></span>     | <span data-ttu-id="1b716-317">Azure の Web 応答</span><span class="sxs-lookup"><span data-stu-id="1b716-317">Azure Web Response</span></span> | <span data-ttu-id="1b716-318">20</span><span class="sxs-lookup"><span data-stu-id="1b716-318">20</span></span>           |
        | <span data-ttu-id="1b716-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="1b716-319">DictationLabel</span></span>         |   <span data-ttu-id="1b716-320">言っただけです。</span><span class="sxs-lookup"><span data-stu-id="1b716-320">You just said:</span></span>   | <span data-ttu-id="1b716-321">20</span><span class="sxs-lookup"><span data-stu-id="1b716-321">20</span></span>           |
        | <span data-ttu-id="1b716-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="1b716-322">TranslationResultLabel</span></span> |    <span data-ttu-id="1b716-323">変換:</span><span class="sxs-lookup"><span data-stu-id="1b716-323">Translation:</span></span>    | <span data-ttu-id="1b716-324">20</span><span class="sxs-lookup"><span data-stu-id="1b716-324">20</span></span>           |

        ![UI のラベルの対応する値を入力します。](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="1b716-326">また、フォント スタイルをください**太字**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="1b716-327">これは、テキストを読みやすきます。</span><span class="sxs-lookup"><span data-stu-id="1b716-327">This will make the text easier to read.</span></span>

        ![太字のフォント。](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="1b716-329">各*UI テキスト オブジェクト*で作成した[第 5 章](#chapter-5--create-the-results-class)を新規作成*子* **UI テキスト オブジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="1b716-330">これらの子は、アプリケーションの出力に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-330">These children will display the output of the application.</span></span> <span data-ttu-id="1b716-331">作成*子*、目的の親を右クリックしてからオブジェクト (例: *MicrophoneStatusLabel*) し、 **UI**し、**テキスト**.</span><span class="sxs-lookup"><span data-stu-id="1b716-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="1b716-332">これらの子のそれぞれについて、選択して、使用して、次の表は、[Inspector] パネルでのパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="1b716-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="1b716-333">**Rect 変換**コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="1b716-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="1b716-334">名前</span><span class="sxs-lookup"><span data-stu-id="1b716-334">Name</span></span>                  | <span data-ttu-id="1b716-335">変換 -*位置*</span><span class="sxs-lookup"><span data-stu-id="1b716-335">Transform - *Position*</span></span> | <span data-ttu-id="1b716-336">幅</span><span class="sxs-lookup"><span data-stu-id="1b716-336">Width</span></span>      | <span data-ttu-id="1b716-337">高さ</span><span class="sxs-lookup"><span data-stu-id="1b716-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="1b716-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="1b716-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="1b716-339">0 の Y-30 Z 0 X</span><span class="sxs-lookup"><span data-stu-id="1b716-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="1b716-340">300</span><span class="sxs-lookup"><span data-stu-id="1b716-340">300</span></span>        | <span data-ttu-id="1b716-341">30</span><span class="sxs-lookup"><span data-stu-id="1b716-341">30</span></span>        |
        | <span data-ttu-id="1b716-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="1b716-342">AzureResponseText</span></span>     | <span data-ttu-id="1b716-343">0 の Y-30 Z 0 X</span><span class="sxs-lookup"><span data-stu-id="1b716-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="1b716-344">300</span><span class="sxs-lookup"><span data-stu-id="1b716-344">300</span></span>        | <span data-ttu-id="1b716-345">30</span><span class="sxs-lookup"><span data-stu-id="1b716-345">30</span></span>        |
        | <span data-ttu-id="1b716-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="1b716-346">DictationText</span></span>         | <span data-ttu-id="1b716-347">0 の Y-30 Z 0 X</span><span class="sxs-lookup"><span data-stu-id="1b716-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="1b716-348">300</span><span class="sxs-lookup"><span data-stu-id="1b716-348">300</span></span>        | <span data-ttu-id="1b716-349">30</span><span class="sxs-lookup"><span data-stu-id="1b716-349">30</span></span>        |
        | <span data-ttu-id="1b716-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="1b716-350">TranslationResultText</span></span> | <span data-ttu-id="1b716-351">0 の Y-30 Z 0 X</span><span class="sxs-lookup"><span data-stu-id="1b716-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="1b716-352">300</span><span class="sxs-lookup"><span data-stu-id="1b716-352">300</span></span>        | <span data-ttu-id="1b716-353">30</span><span class="sxs-lookup"><span data-stu-id="1b716-353">30</span></span>        |

    2. <span data-ttu-id="1b716-354">**テキスト (スクリプト)** コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="1b716-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="1b716-355">名前</span><span class="sxs-lookup"><span data-stu-id="1b716-355">Name</span></span>                  | <span data-ttu-id="1b716-356">Text</span><span class="sxs-lookup"><span data-stu-id="1b716-356">Text</span></span>          | <span data-ttu-id="1b716-357">フォント サイズ</span><span class="sxs-lookup"><span data-stu-id="1b716-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="1b716-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="1b716-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="1b716-359">??</span><span class="sxs-lookup"><span data-stu-id="1b716-359">??</span></span>       | <span data-ttu-id="1b716-360">20</span><span class="sxs-lookup"><span data-stu-id="1b716-360">20</span></span>           |
        | <span data-ttu-id="1b716-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="1b716-361">AzureResponseText</span></span>     |      <span data-ttu-id="1b716-362">??</span><span class="sxs-lookup"><span data-stu-id="1b716-362">??</span></span>       | <span data-ttu-id="1b716-363">20</span><span class="sxs-lookup"><span data-stu-id="1b716-363">20</span></span>           |
        | <span data-ttu-id="1b716-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="1b716-364">DictationText</span></span>         |      <span data-ttu-id="1b716-365">??</span><span class="sxs-lookup"><span data-stu-id="1b716-365">??</span></span>       | <span data-ttu-id="1b716-366">20</span><span class="sxs-lookup"><span data-stu-id="1b716-366">20</span></span>           |
        | <span data-ttu-id="1b716-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="1b716-367">TranslationResultText</span></span> |      <span data-ttu-id="1b716-368">??</span><span class="sxs-lookup"><span data-stu-id="1b716-368">??</span></span>       | <span data-ttu-id="1b716-369">20</span><span class="sxs-lookup"><span data-stu-id="1b716-369">20</span></span>           |

9. <span data-ttu-id="1b716-370">次に、テキストの各コンポーネントの 'centre' の配置オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="1b716-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![テキストを配置します。](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="1b716-372">確認する、**子 UI テキスト**オブジェクトが読みやすく、変更、*色*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="1b716-373">これには (現在は ' 黒') の横に、バーをクリックすると、*色*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![対応する UI テキスト出力用の値を入力します。](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="1b716-375">次に、新しい、少し、*色*ウィンドウで、変更、 *16 進カラー*に。**0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="1b716-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![色を青を更新します。](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="1b716-377">以下は、方法、 **UI**になります。</span><span class="sxs-lookup"><span data-stu-id="1b716-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="1b716-378">*階層パネル*:</span><span class="sxs-lookup"><span data-stu-id="1b716-378">In the *Hierarchy Panel*:</span></span>

        ![指定された構造内の階層があります。](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="1b716-380">*シーン*と*ゲーム ビュー*:</span><span class="sxs-lookup"><span data-stu-id="1b716-380">In the *Scene* and *Game Views*:</span></span>

        ![同じ構造でシーンやゲームのビューがあります。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="1b716-382">第 5 章 – 結果のクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1b716-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="1b716-383">最初のスクリプトを作成する必要がありますが、*結果*クラスは、変換の結果を表示する方法を提供する責任を負います。</span><span class="sxs-lookup"><span data-stu-id="1b716-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="1b716-384">クラスを格納し、次が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="1b716-385">Azure からの応答の結果。</span><span class="sxs-lookup"><span data-stu-id="1b716-385">The response result from Azure.</span></span>
- <span data-ttu-id="1b716-386">マイクの状態です。</span><span class="sxs-lookup"><span data-stu-id="1b716-386">The microphone status.</span></span> 
- <span data-ttu-id="1b716-387">ディクテーション モード (音声テキストを) の結果。</span><span class="sxs-lookup"><span data-stu-id="1b716-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="1b716-388">変換の結果。</span><span class="sxs-lookup"><span data-stu-id="1b716-388">The result of the translation.</span></span>

<span data-ttu-id="1b716-389">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1b716-389">To create this class:</span></span> 

1.  <span data-ttu-id="1b716-390">右クリックし、*プロジェクト パネル*、し**作成 > フォルダー**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="1b716-391">フォルダーの名前**スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-391">Name the folder **Scripts**.</span></span> 
 
    ![[スクリプト] フォルダーを作成します。](images/AzureLabs-Lab1-31.png)

    ![スクリプト フォルダーを開きます。](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="1b716-394">**スクリプト**フォルダーの作成、アイコンをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="1b716-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="1b716-395">そのフォルダーを右クリックし、内**作成 >** し**C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="1b716-396">スクリプトの名前*結果*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-396">Name the script *Results*.</span></span> 

    ![最初のスクリプトを作成します。](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="1b716-398">新しいをダブルクリックします。*結果*スクリプト ファイルを開く**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="1b716-399">次の名前空間を挿入します。</span><span class="sxs-lookup"><span data-stu-id="1b716-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="1b716-400">クラス内には、次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="1b716-400">Inside the Class insert the following variables:</span></span>

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  <span data-ttu-id="1b716-401">追加し、 *Awake()* メソッドで、クラスを初期化するときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="1b716-402">最後に、UI にさまざまな結果の情報を出力することを担当するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="1b716-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  <span data-ttu-id="1b716-403">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="1b716-404">第 6 章 – 作成、 *MicrophoneManager*クラス</span><span class="sxs-lookup"><span data-stu-id="1b716-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="1b716-405">2 番目のクラスを作成するには、 *MicrophoneManager*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="1b716-406">このクラスは、責任を負います。</span><span class="sxs-lookup"><span data-stu-id="1b716-406">This class is responsible for:</span></span>

- <span data-ttu-id="1b716-407">ヘッドセットまたは (方は、既定値) のマシンにアタッチされた録音デバイスを検出します。</span><span class="sxs-lookup"><span data-stu-id="1b716-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="1b716-408">音声 (音声) を使用すると、キャプチャし、ディクテーションを使用して、文字列として保存します。</span><span class="sxs-lookup"><span data-stu-id="1b716-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="1b716-409">音声が一時停止すると、Translator クラスにディクテーションを送信します。</span><span class="sxs-lookup"><span data-stu-id="1b716-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="1b716-410">必要な場合は、音声でキャプチャを停止するメソッドをホストします。</span><span class="sxs-lookup"><span data-stu-id="1b716-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="1b716-411">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1b716-411">To create this class:</span></span> 
1.  <span data-ttu-id="1b716-412">ダブルクリック、**スクリプト**フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="1b716-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="1b716-413">内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="1b716-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="1b716-414">スクリプトの名前*MicrophoneManager*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="1b716-415">Visual Studio で開くことに新しいスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b716-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="1b716-416">上部にある、次と同じである名前空間の更新、 *MicrophoneManager*クラス。</span><span class="sxs-lookup"><span data-stu-id="1b716-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="1b716-417">次に、内部では、次の変数を追加、 *MicrophoneManager*クラス。</span><span class="sxs-lookup"><span data-stu-id="1b716-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  <span data-ttu-id="1b716-418">コードを*Awake()* と*Start()* 今すぐメソッドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="1b716-419">これらが、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-419">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  <span data-ttu-id="1b716-420">できます*削除*、 *Update()* メソッドのため、このクラスは使用されません。</span><span class="sxs-lookup"><span data-stu-id="1b716-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="1b716-421">メソッドに渡すの開始し、音声のキャプチャを停止する、アプリが使用する必要があります、 *Translator*クラスと、すぐにビルドします。</span><span class="sxs-lookup"><span data-stu-id="1b716-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="1b716-422">次のコードをコピーして貼り付ける下に、 *Start()* メソッド。</span><span class="sxs-lookup"><span data-stu-id="1b716-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > <span data-ttu-id="1b716-423">このアプリケーションのことはありませんが、使用、 *StopCapturingAudio()* メソッドも用意されていますここでは、アプリケーションでのオーディオのキャプチャを停止する機能を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="1b716-424">音声が停止したときに呼び出されるディクテーション ハンドラーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="1b716-425">このメソッドは、ディクテーションされたテキストに合格し、 *Translator*クラス。</span><span class="sxs-lookup"><span data-stu-id="1b716-425">This method will then pass the dictated text to the *Translator* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. <span data-ttu-id="1b716-426">Visual Studio で Unity に戻る前に変更を保存することを確認します。</span><span class="sxs-lookup"><span data-stu-id="1b716-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="1b716-427">この時点で表示されるエラーが表示されます、 *Unity エディターのコンソール*パネル (「名前 'トランスレーター' が存在しません...」)。</span><span class="sxs-lookup"><span data-stu-id="1b716-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="1b716-428">これは、コードを参照しているため、 *Translator*クラスで、[次へ] の章で作成されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="1b716-429">第 7 章 – Azure と translator サービスへの呼び出し</span><span class="sxs-lookup"><span data-stu-id="1b716-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="1b716-430">最後のスクリプトを作成する必要がありますが、 *Translator*クラス。</span><span class="sxs-lookup"><span data-stu-id="1b716-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="1b716-431">このクラスは、責任を負います。</span><span class="sxs-lookup"><span data-stu-id="1b716-431">This class is responsible for:</span></span>

-   <span data-ttu-id="1b716-432">使用してアプリを認証*Azure*、exchange の**Auth トークン**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="1b716-433">使用して、 **Auth トークン**テキストを送信する (から受信した、 *MicrophoneManager*クラス) を変換します。</span><span class="sxs-lookup"><span data-stu-id="1b716-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="1b716-434">変換された結果を受け取るに渡すと、*結果*UI で視覚化対象であるクラス。</span><span class="sxs-lookup"><span data-stu-id="1b716-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="1b716-435">このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1b716-435">To create this Class:</span></span> 
1.  <span data-ttu-id="1b716-436">移動して、**スクリプト**以前に作成したフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="1b716-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="1b716-437">右クリックし、**プロジェクト パネル**、**作成 >C#スクリプト**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="1b716-438">スクリプトを呼び出す*Translator*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="1b716-439">新しいをダブルクリックします。 *Translator*開くスクリプト**Visual Studio を使用した**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="1b716-440">ファイルの先頭には、次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="1b716-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="1b716-441">内で、次の変数を追加し、 *Translator*クラス。</span><span class="sxs-lookup"><span data-stu-id="1b716-441">Then add the following variables inside the *Translator* class:</span></span>

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - <span data-ttu-id="1b716-442">言語に挿入された言語**enum**は単なる例です。</span><span class="sxs-lookup"><span data-stu-id="1b716-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="1b716-443">場合; を追加してみてください。[API は、60 を超える言語をサポートしている](https://docs.microsoft.com/azure/cognitive-services/translator/languages)(クリンゴンを含む)。</span><span class="sxs-lookup"><span data-stu-id="1b716-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="1b716-444">[より対話的なページが使用可能な言語をカバーする](https://www.microsoft.com/translator/business/languages/)ページに設定されているサイトの言語にあるときにのみ表示されますが注意 'en-' (および、Microsoft のサイトがネイティブ言語へのリダイレクトを可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="1b716-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to 'en-us' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="1b716-445">または、URL を変更することにより、ページの下部にあるサイトの言語を変更できます。</span><span class="sxs-lookup"><span data-stu-id="1b716-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="1b716-446">**AuthorizationKey**上のコード スニペット内の値である必要があります、**キー**を申し込んだときに受信した、 *Azure Translator Text API*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="1b716-447">これで説明した[第 1 章](#chapter-1--the-azure-portal)します。</span><span class="sxs-lookup"><span data-stu-id="1b716-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="1b716-448">コードを*Awake()* と*Start()* 今すぐメソッドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="1b716-449">ここでは、コードが呼び出しを行うは*Azure*承認キーを使用して、*トークン*。</span><span class="sxs-lookup"><span data-stu-id="1b716-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="1b716-450">トークンは、10 分後に切れます。</span><span class="sxs-lookup"><span data-stu-id="1b716-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="1b716-451">によっては、アプリのシナリオでは、複数回呼び出して同じコルーチンを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="1b716-452">トークンを取得するコルーチン次に示します。</span><span class="sxs-lookup"><span data-stu-id="1b716-452">The coroutine to obtain the Token is the following:</span></span>

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > <span data-ttu-id="1b716-453">IEnumerator メソッドの名前を編集する場合**GetTokenCoroutine()**、更新する必要がある、 *StartCoroutine*と*StopCoroutine*上記のコードで文字列値を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1b716-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="1b716-454">[Unity のドキュメントに従って](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)特定を停止するには、*コルーチン*文字列値メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="1b716-455">次に、受信したテキストの翻訳を取得する (その下「サポート」ストリーム メソッド) を使用して、コルーチンを追加、 *MicrophoneManager*クラス。</span><span class="sxs-lookup"><span data-stu-id="1b716-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="1b716-456">このコードに送信するクエリ文字列の作成、 *Azure Translator Text API*、し、内部の Unity UnityWebRequest クラスを使用して、クエリ文字列のあるエンドポイントに 'Get' 呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="1b716-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="1b716-457">結果は、結果オブジェクトの翻訳を設定するのには使用されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="1b716-458">次のコードは、実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="1b716-458">The code below shows the implementation:</span></span>

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. <span data-ttu-id="1b716-459">変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="1b716-460">章 – 8 Unity シーンを構成します。</span><span class="sxs-lookup"><span data-stu-id="1b716-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="1b716-461">戻る Unity エディターで、をクリックし、ドラッグ、*結果*クラス*から*、**スクリプト**フォルダーを**Main Camera** 内のオブジェクト*階層パネル*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="1b716-462">をクリックして、 **Main Camera**を見て、*インスペクター パネル*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="1b716-463">内で、新しく追加した表示になります*スクリプト*コンポーネントでは、空の値の 4 つのフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="1b716-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="1b716-464">これらは、コード内のプロパティに出力参照です。</span><span class="sxs-lookup"><span data-stu-id="1b716-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="1b716-465">適切なドラッグ**テキスト**オブジェクトから、*階層パネル*これら 4 つのスロット、次の図に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="1b716-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![指定した値を持つターゲットの参照を更新します。](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="1b716-467">次に、をクリックし、ドラッグ、 *Translator*クラスから、**スクリプト**フォルダーを**Main Camera**オブジェクト、*階層パネル*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="1b716-468">次に、をクリックし、ドラッグ、 *MicrophoneManager*クラスから、**スクリプト**フォルダーを**Main Camera**オブジェクト、*階層パネル*。</span><span class="sxs-lookup"><span data-stu-id="1b716-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="1b716-469">最後に、をクリックして、 **Main Camera**を見て、*インスペクター パネル*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="1b716-470">上にドラッグした先のスクリプトである 2 つのドロップ ダウン ボックスは、言語を設定することがわかります。</span><span class="sxs-lookup"><span data-stu-id="1b716-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![目的の翻訳の言語の入力を確認します。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="1b716-472">第 9 章 – 複合現実でのテスト</span><span class="sxs-lookup"><span data-stu-id="1b716-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="1b716-473">この時点で、シーンが正しく実装されていることをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="1b716-474">次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1b716-474">Ensure that:</span></span>

- <span data-ttu-id="1b716-475">説明されているすべての設定[第 1 章](#chapter-1--the-azure-portal)が正しく設定されています。</span><span class="sxs-lookup"><span data-stu-id="1b716-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="1b716-476">*結果*、 *Translator*、および*MicrophoneManager*に関連付けられているスクリプト、 **Main Camera**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1b716-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="1b716-477">配置した、 *Azure Translator Text API*サービス**キー**内、 **authorizationKey**変数内で、 *Translator*スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="1b716-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="1b716-478">内のすべてのフィールド、*カメラ インスペクター [メイン] パネル*が適切に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="1b716-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="1b716-479">シーンを実行するときに、マイクの動作 (そうでない場合は、接続されているマイクことを確認、*既定*デバイス、およびある[Windows 内正しく設定して](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10))。</span><span class="sxs-lookup"><span data-stu-id="1b716-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="1b716-480">イマーシブ ヘッドセットをテストするにはキーを押して、**再生**ボタン、 *Unity エディター*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="1b716-481">アプリは、添付のイマーシブ ヘッドセットで機能している必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="1b716-482">変更する既定のオーディオ デバイスについて、Unity コンソールで、エラーが発生した場合期待どおりにシーンが機能しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="1b716-483">これは、複合現実ポータルが設定されているヘッドセットの組み込みのマイクを扱う方法に起因します。</span><span class="sxs-lookup"><span data-stu-id="1b716-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="1b716-484">このエラーを参照してください、単にシーンを停止、再開し、として動作する必要がありますが必要です。</span><span class="sxs-lookup"><span data-stu-id="1b716-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="1b716-485">章 – 10 ビルド UWP ソリューションおよびローカル コンピューター上のサイドロード</span><span class="sxs-lookup"><span data-stu-id="1b716-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="1b716-486">このプロジェクトの Unity のセクションの必要なすべてが今すぐ完了したら、ので、Unity から構築するための時間。</span><span class="sxs-lookup"><span data-stu-id="1b716-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="1b716-487">移動します**ビルド設定**:**ファイル > の設定を作成しています.**</span><span class="sxs-lookup"><span data-stu-id="1b716-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="1b716-488">**Build Settings**ウィンドウで、をクリックして**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Unity シーンを構築します。](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="1b716-490">まだ行っていない場合、ティック**UnityC#プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="1b716-491">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b716-491">Click **Build**.</span></span> <span data-ttu-id="1b716-492">Unity を起動、*ファイル エクスプ ローラー*ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="1b716-493">ここで、そのフォルダーを作成し、名前*アプリ*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="1b716-494">使用し、*アプリ*フォルダーを選択すると、キーを押して**フォルダーの選択**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="1b716-495">Unity にプロジェクトをビルドを開始、*アプリ*フォルダー。</span><span class="sxs-lookup"><span data-stu-id="1b716-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="1b716-496">1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、*ファイル エクスプ ローラー*ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。</span><span class="sxs-lookup"><span data-stu-id="1b716-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="1b716-497">第 11 章 – 展開アプリケーション</span><span class="sxs-lookup"><span data-stu-id="1b716-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="1b716-498">アプリケーションを配置します。</span><span class="sxs-lookup"><span data-stu-id="1b716-498">To deploy your application:</span></span>

1.  <span data-ttu-id="1b716-499">新しい Unity ビルドに移動します (、*アプリ*フォルダー) とソリューション ファイルを開くと*Visual Studio*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="1b716-500">ソリューション構成の選択で**デバッグ**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="1b716-501">ソリューション プラットフォーム で選択**x86**、**ローカル マシン**します。</span><span class="sxs-lookup"><span data-stu-id="1b716-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="1b716-502">Microsoft HoloLens にすることがあります方が簡単なこれを設定する*リモート マシン*、するは、コンピューターにテザリングされたしないようにします。</span><span class="sxs-lookup"><span data-stu-id="1b716-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="1b716-503">ただし、次の操作も必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="1b716-504">把握、 **IP アドレス**内では、HoloLens の*設定 > ネットワークとインターネット > Wi-fi > 詳細オプション*;、IPv4 では、アドレスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="1b716-505">確認*開発者モード*は**で**; で見つかった*設定 > 更新とセキュリティ > 開発者向け*します。</span><span class="sxs-lookup"><span data-stu-id="1b716-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="1b716-507">移動して**ビルド メニュー**  をクリック**ソリューションの配置**を PC にアプリケーションをサイドローディングします。</span><span class="sxs-lookup"><span data-stu-id="1b716-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="1b716-508">アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="1b716-509">起動するには、アプリには、マイクへのアクセスを承認することが求められます。</span><span class="sxs-lookup"><span data-stu-id="1b716-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="1b716-510">クリックして、**はい**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b716-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="1b716-511">翻訳を開始する準備ができました!</span><span class="sxs-lookup"><span data-stu-id="1b716-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="1b716-512">完成した翻訳テキスト API アプリケーション</span><span class="sxs-lookup"><span data-stu-id="1b716-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="1b716-513">これで、音声翻訳されたテキストに変換するには、Azure 翻訳テキスト API を利用している mixed reality アプリを構築します。</span><span class="sxs-lookup"><span data-stu-id="1b716-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![最終的な製品です。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="1b716-515">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="1b716-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="1b716-516">手順 1</span><span class="sxs-lookup"><span data-stu-id="1b716-516">Exercise 1</span></span>

<span data-ttu-id="1b716-517">できる機能を追加する音声合成をアプリに返されるテキストが話されているようにでしょうか。</span><span class="sxs-lookup"><span data-stu-id="1b716-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="1b716-518">手順 2</span><span class="sxs-lookup"><span data-stu-id="1b716-518">Exercise 2</span></span>

<span data-ttu-id="1b716-519">ユーザー自体には、アプリ内のソースと出力の言語 ('から' および 'to') を変更するので、アプリが言語を変更するたびに再構築する必要はありませんが可能にします。</span><span class="sxs-lookup"><span data-stu-id="1b716-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
