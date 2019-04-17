---
title: MR と Azure 313 - IoT Hub サービス
description: Ubuntu 16.4 を実行する仮想マシンを Azure IoT Hub サービスを実装する方法については、このコースを完了し、Microsoft HoloLens または没入型の (VR) ヘッドセットを使用してメッセージ データを視覚化します。
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure、mixed reality、academy、edge、iot edge、チュートリアル、api、通知、関数、テーブル、没入型、hololens、vr、iot、仮想マシン、ubuntu、python
ms.openlocfilehash: 1ab7c48ac3cff1cb2283cadb171098af9e148628
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597571"
---
>[!NOTE]
><span data-ttu-id="acd57-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="acd57-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="acd57-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="acd57-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="acd57-106">これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="acd57-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="acd57-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="acd57-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="acd57-110">MR と Azure 313:IoT Hub サービス</span><span class="sxs-lookup"><span data-stu-id="acd57-110">MR and Azure 313: IoT Hub Service</span></span>

![コースの結果](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="acd57-112">このコースでは、実装する方法について説明します、 **Azure IoT Hub Service**仮想マシン上には、Ubuntu 16.4 オペレーティング システムを実行します。</span><span class="sxs-lookup"><span data-stu-id="acd57-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="acd57-113">**Azure Function App** 、Ubuntu VM から送信されるメッセージを使用して、内で結果を格納する**Azure Table Service**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="acd57-114">使用してこのデータを表示できるが、 **Power BI** Microsoft HoloLens または没入型の (VR) ヘッドセット。</span><span class="sxs-lookup"><span data-stu-id="acd57-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="acd57-115">このコースの内容*適用*IoT Edge デバイスにこのコースでは、目的が、フォーカスがあり、仮想マシン環境でされる物理的なエッジ デバイスへのアクセスが必要ではありません。</span><span class="sxs-lookup"><span data-stu-id="acd57-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="acd57-116">このコースを完了するを学習します。</span><span class="sxs-lookup"><span data-stu-id="acd57-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="acd57-117">デプロイを**IoT Edge モジュール**IoT デバイスを表す仮想マシン (Ubuntu 16 OS) にします。</span><span class="sxs-lookup"><span data-stu-id="acd57-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="acd57-118">追加、 **Azure Custom Vision Tensorflow モデル**エッジ モジュールには、コンテナーに格納されているイメージを分析するコードにします。</span><span class="sxs-lookup"><span data-stu-id="acd57-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="acd57-119">分析結果のメッセージを送信する、モジュールの設定に戻す、 **IoT Hub Service**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="acd57-120">使用して、 **Azure Function App**内でメッセージを格納する、 **Azure Table**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="acd57-121">設定する**Power BI**を格納されたメッセージを収集してレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="acd57-122">内で IoT メッセージ データを視覚化する**Power BI**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="acd57-123">使用するサービスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="acd57-123">The Services you will use include:</span></span>

- <span data-ttu-id="acd57-124">**Azure IoT Hub**により、接続、監視、および IoT 資産の管理、開発者が Microsoft Azure サービスです。</span><span class="sxs-lookup"><span data-stu-id="acd57-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="acd57-125">詳細については、次を参照してください。、 [ **Azure IoT Hub Service**ページ](https://azure.microsoft.com/en-au/services/iot-hub/)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/en-au/services/iot-hub/).</span></span>

- <span data-ttu-id="acd57-126">**Azure Container Registry**は、開発者がさまざまな種類のコンテナーのコンテナー イメージを格納する Microsoft Azure サービスです。</span><span class="sxs-lookup"><span data-stu-id="acd57-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="acd57-127">詳細については、次を参照してください。、 [ **Azure コンテナー レジストリ サービス**ページ](https://azure.microsoft.com/en-au/services/container-registry/)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/en-au/services/container-registry/).</span></span>

- <span data-ttu-id="acd57-128">**Azure Function App**開発者が小規模なコードを実行する、Microsoft Azure のサービス '関数'、Azure では、します。</span><span class="sxs-lookup"><span data-stu-id="acd57-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="acd57-129">これは、多くのメリットを持つことができる、ローカル アプリケーションではなく、クラウドに作業を委任する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="acd57-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="acd57-130">**Azure Functions** C をなど、複数の開発言語をサポートしている\#、F\#Node.js、Java、および PHP します。</span><span class="sxs-lookup"><span data-stu-id="acd57-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="acd57-131">詳細については、次を参照してください。、 [ **Azure Functions**ページ](https://docs.microsoft.com/azure/azure-functions/functions-overview)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="acd57-132">**Azure Storage:テーブル**Microsoft Azure サービスで、開発者が格納する構造化、非 SQL、データ、クラウドで任意の場所で簡単にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="acd57-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="acd57-133">サービスは、スキーマなしの設計は幅広いプラットフォーム、必要に応じて、テーブルの進化のことができます、非常に柔軟なは。</span><span class="sxs-lookup"><span data-stu-id="acd57-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="acd57-134">詳細については、次を参照してください、 [ **Azure Tables**ページ。](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="acd57-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="acd57-135">このコースでは、セットアップし、IoT Hub サービスを使用し、デバイスによって提供される応答を視覚化する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="acd57-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="acd57-136">までにビルドしている場合カスタムの IoT Hub サービス設定でこれらの概念を適用することがあります。</span><span class="sxs-lookup"><span data-stu-id="acd57-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="acd57-137">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="acd57-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="acd57-138">コース</span><span class="sxs-lookup"><span data-stu-id="acd57-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="acd57-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="acd57-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="acd57-140"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="acd57-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="acd57-141">MR と Azure 313:IoT Hub サービス</span><span class="sxs-lookup"><span data-stu-id="acd57-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="acd57-142">✔️</span><span class="sxs-lookup"><span data-stu-id="acd57-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="acd57-143">✔️</span><span class="sxs-lookup"><span data-stu-id="acd57-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="acd57-144">前提条件</span><span class="sxs-lookup"><span data-stu-id="acd57-144">Prerequisites</span></span>

<span data-ttu-id="acd57-145">Microsoft HoloLens などの複合現実での開発の最新の前提条件をご覧ください、[ツールをインストールする](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)記事。</span><span class="sxs-lookup"><span data-stu-id="acd57-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="acd57-146">このチュートリアルは、Python を使用した基本的な経験を持っている開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="acd57-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="acd57-147">また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 7 月) の書き込み時に検証されたがどのようなことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="acd57-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="acd57-148">内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)記事、ただし、このコースの情報が一致は完全にするよりも下に示す新しいソフトウェアで表示されますは仮定されません。</span><span class="sxs-lookup"><span data-stu-id="acd57-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="acd57-149">次のハードウェアとソフトウェアが必要です。</span><span class="sxs-lookup"><span data-stu-id="acd57-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="acd57-150">Windows 10 Fall Creators Update (またはそれ以降)**開発者モードが有効になっています。**</span><span class="sxs-lookup"><span data-stu-id="acd57-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="acd57-151">Windows 10 Home エディションで、HYPER-V を使用して仮想マシンを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="acd57-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="acd57-152">Windows 10 SDK (最新バージョン)</span><span class="sxs-lookup"><span data-stu-id="acd57-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="acd57-153">HoloLens、a**開発者モードが有効になっています。**</span><span class="sxs-lookup"><span data-stu-id="acd57-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="acd57-154">Visual Studio 2017.15.4 (Azure のクラウド エクスプ ローラーへのアクセスにのみ使用)</span><span class="sxs-lookup"><span data-stu-id="acd57-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="acd57-155">Azure、および IoT Hub サービスのインターネット アクセス。</span><span class="sxs-lookup"><span data-stu-id="acd57-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="acd57-156">詳細についてに従ってくださいこの[IoT Hub サービスのページへのリンク](https://azure.microsoft.com/en-au/services/iot-hub/)</span><span class="sxs-lookup"><span data-stu-id="acd57-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/en-au/services/iot-hub/)</span></span>
- <span data-ttu-id="acd57-157">機械学習モデル。</span><span class="sxs-lookup"><span data-stu-id="acd57-157">A machine learning model.</span></span> <span data-ttu-id="acd57-158">モデルを使用する準備がない[、このコースで提供されるモデルを使用する](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="acd57-159">**HYPER-V**ソフトウェア、Windows 10 開発用コンピューターで有効にします。</span><span class="sxs-lookup"><span data-stu-id="acd57-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="acd57-160">開発用コンピューターまたは別の方法として実行されている Ubuntu (16.4 または 18.4) を実行する仮想マシンには、Linux (Ubuntu 16.4 または 18.4) を実行している別のコンピューターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="acd57-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="acd57-161">HYPER-V を使用して、Windows 上の VM を作成する方法の詳細についてを見つけることができます、 [「開始前の準備」の章](#before-you-start)(。 https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="acd57-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="acd57-162">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="acd57-162">Before you start</span></span>

1. <span data-ttu-id="acd57-163">設定して、HoloLens をテストします。</span><span class="sxs-lookup"><span data-stu-id="acd57-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="acd57-164">場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="acd57-165">実行することをお勧め**調整**と**センサー チューニング**(も役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときにします。</span><span class="sxs-lookup"><span data-stu-id="acd57-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="acd57-166">調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="acd57-167">センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="acd57-168">セットアップ、 **Ubuntu 仮想マシン**を使用して**HYPER-V**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="acd57-169">次のリソースでプロセスを役立ちます。</span><span class="sxs-lookup"><span data-stu-id="acd57-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="acd57-170">最初に、このリンクに従う[16.04.4 の Ubuntu LTS (Xenial Xerus) の ISO をダウンロード](http://au.releases.ubuntu.com/16.04/)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="acd57-171">選択、 **64 ビット PC (AMD64) デスクトップ イメージ**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="acd57-172">確認**HYPER-V**は、Windows 10 コンピューターで有効になっています。</span><span class="sxs-lookup"><span data-stu-id="acd57-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="acd57-173">ガイダンスについては、このリンクをフォローできます[インストールと Windows 10 で HYPER-V を有効化](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="acd57-174">HYPER-V を開始し、新しい Ubuntu VM を作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="acd57-175">このリンクを利用できる、 [、HYPER-V と VM を作成する方法についてステップ バイ ステップ ガイド](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="acd57-176">要求されると **「ブート イメージ ファイルからオペレーティング システムをインストールする」** を選択、 **Ubuntu ISO**以前ダウンロードがあります。</span><span class="sxs-lookup"><span data-stu-id="acd57-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="acd57-177">使用して **、HYPER-V のクイック作成**はお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="acd57-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="acd57-178">第 1 章 - カスタム ビジョン モデルを取得します。</span><span class="sxs-lookup"><span data-stu-id="acd57-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="acd57-179">このコースにアクセスすること、[構築済みのカスタム ビジョン モデル](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)キーボードとマウスの画像から検出します。</span><span class="sxs-lookup"><span data-stu-id="acd57-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="acd57-180">これを使用する場合に進みます[第 2 章](#chapter-2---the-container-registry-service)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="acd57-181">ただし、独自のカスタム ビジョン モデルを使用する場合は、次の手順にできます。</span><span class="sxs-lookup"><span data-stu-id="acd57-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="acd57-182">**カスタム ビジョン プロジェクト**に移動して、**パフォーマンス**タブ。</span><span class="sxs-lookup"><span data-stu-id="acd57-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="acd57-183">モデルを使用する必要があります、 *compact*ドメイン モデルをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="acd57-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="acd57-184">プロジェクトの設定でドメイン モデルを変更できます。</span><span class="sxs-lookup"><span data-stu-id="acd57-184">You can change your models domain in the settings for your project.</span></span>

    ![[パフォーマンス] タブ](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="acd57-186">選択、**イテレーション**エクスポートし、をクリックする**エクスポート**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="acd57-187">ブレードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-187">A blade will appear.</span></span>

    ![ブレードをエクスポートします。](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="acd57-189">ブレードで、 **Docker ファイル**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-189">In the blade click **Docker File**.</span></span>

    ![docker を選択します。](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="acd57-191">クリックして**Linux**クリックしてドロップダウン メニューで**ダウンロード**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![ダウンロードをクリックします。](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="acd57-193">コンテンツを解凍します。</span><span class="sxs-lookup"><span data-stu-id="acd57-193">Unzip the content.</span></span> <span data-ttu-id="acd57-194">このコースで後ほど使用します。</span><span class="sxs-lookup"><span data-stu-id="acd57-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="acd57-195">第 2 章 - コンテナー レジストリ サービス</span><span class="sxs-lookup"><span data-stu-id="acd57-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="acd57-196">**コンテナー レジストリ サービス**は、コンテナーをホストするために使用するリポジトリです。</span><span class="sxs-lookup"><span data-stu-id="acd57-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="acd57-197">**IoT Hub サービス**ビルドし、使用して、このコースでは参照する**コンテナー レジストリ サービス**Edge デバイスにデプロイするコンテナーを取得します。</span><span class="sxs-lookup"><span data-stu-id="acd57-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="acd57-198">最初に、これに従って[Azure ポータルへのリンク](https://portal.azure.com/)、資格情報を使用してログインします。</span><span class="sxs-lookup"><span data-stu-id="acd57-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="acd57-199">移動して**リソースの作成**を探して**Container Registry**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![コンテナー レジストリ](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="acd57-201">をクリックして**作成**です。</span><span class="sxs-lookup"><span data-stu-id="acd57-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="acd57-202">サービスのセットアップ パラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="acd57-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="acd57-203">この例では、プロジェクトの名前を挿入、呼び出された**IoTCRegistry**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="acd57-204">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="acd57-205">リソース グループは、監視、プロビジョニング、アクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="acd57-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="acd57-206">勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。</span><span class="sxs-lookup"><span data-stu-id="acd57-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="acd57-207">サービスの場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="acd57-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="acd57-208">設定**管理者ユーザー**に**を有効にする**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="acd57-209">設定**SKU**に**基本的な**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="acd57-210">クリックして**作成**し、サービスを作成するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="acd57-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="acd57-211">通知はポップアップ通知が正常に作成すると、 *Container Registry*、 をクリックして**リソースに移動**サービス ページにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="acd57-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="acd57-212">*Container Registry*サービス ページで、をクリックして**アクセス キー**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="acd57-213">メモしてをおきます (、メモ帳を使用する可能性があります)、次のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="acd57-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="acd57-214">**ログイン サーバー**</span><span class="sxs-lookup"><span data-stu-id="acd57-214">**Login Server**</span></span>
    2. <span data-ttu-id="acd57-215">**Username**</span><span class="sxs-lookup"><span data-stu-id="acd57-215">**Username**</span></span>
    3. <span data-ttu-id="acd57-216">**Password**</span><span class="sxs-lookup"><span data-stu-id="acd57-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="acd57-217">第 3 章 - IoT Hub サービス</span><span class="sxs-lookup"><span data-stu-id="acd57-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="acd57-218">作成とのセットアップを開始するようになりました、 **IoT Hub Service**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="acd57-219">サインインしていない場合のログイン、 [Azure Portal](https://portal.azure.com)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="acd57-220">ログインすると、をクリックして**リソースの作成**左上隅にある検索して**IoT Hub**、 をクリック**Enter**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![ストレージ アカウントの検索](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="acd57-222">新しいページがの説明を入力、**ストレージ アカウント**サービス。</span><span class="sxs-lookup"><span data-stu-id="acd57-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="acd57-223">このダイアログ ボックスの左下にある at をクリックして、**作成**ボタンは、サービスのこのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="acd57-225">クリックすると**作成**パネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="acd57-226">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="acd57-227">リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="acd57-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="acd57-228">勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。</span><span class="sxs-lookup"><span data-stu-id="acd57-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="acd57-229">詳細にする場合について、Azure リソース グループに従ってくださいこの[リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="acd57-230">適切な選択**場所**(同じ場所でこのコースを作成するすべてのサービスを使用して)。</span><span class="sxs-lookup"><span data-stu-id="acd57-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="acd57-231">必要な挿入**名前**このサービス インスタンス。</span><span class="sxs-lookup"><span data-stu-id="acd57-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="acd57-232">ページの下部にある をクリックして**次へ。サイズとスケール**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="acd57-234">このページで、選択、**価格とスケールティア**(最初の IoT Hub サービス インスタンスの場合は、free レベルできるようにする)。</span><span class="sxs-lookup"><span data-stu-id="acd57-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="acd57-235">をクリックして**確認および作成**です。</span><span class="sxs-lookup"><span data-stu-id="acd57-235">Click on **Review + Create**.</span></span>

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="acd57-237">設定を確認して、をクリックして**作成**です。</span><span class="sxs-lookup"><span data-stu-id="acd57-237">Review your settings and click on **Create**.</span></span>

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="acd57-239">通知はポップアップ通知が正常に作成すると、 *IoT Hub*サービス、 をクリックして**リソースに移動**サービス ページにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="acd57-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="acd57-241">左側のサイド パネルに表示されるまでスクロール*デバイスの自動管理*、 をクリック**IoT Edge**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="acd57-243">右側に表示されるウィンドウでクリックして**IoT Edge デバイスの追加**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="acd57-244">ブレードが右側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="acd57-245">ブレードで、新しいデバイスを提供する**デバイス ID** (好みの名前)。</span><span class="sxs-lookup"><span data-stu-id="acd57-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="acd57-246">をクリックし、**保存**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-246">Then, click **Save**.</span></span> <span data-ttu-id="acd57-247">*プライマリ*と*セカンダリ キー*は自動生成があれば**の自動生成**オンします。</span><span class="sxs-lookup"><span data-stu-id="acd57-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="acd57-249">移動するが、 *IoT Edge デバイス* セクションで、新しいデバイスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="acd57-250">新しいデバイスをクリックします (で赤で、イメージの下)。</span><span class="sxs-lookup"><span data-stu-id="acd57-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="acd57-252">*デバイスの詳細*が表示されたら、ページのコピーを作成する、**接続文字列**(主キー)。</span><span class="sxs-lookup"><span data-stu-id="acd57-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="acd57-254">、左側のパネルに戻り、をクリックして*共有アクセス ポリシー*、を開きます。</span><span class="sxs-lookup"><span data-stu-id="acd57-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="acd57-255">表示されるページで、をクリックして**iothubowner**、し、画面の右側のブレードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="acd57-256">書き留めて (上、メモ帳)、**接続文字列**(主キー) を設定するときに、後で使用、*接続文字列*デバイスにします。</span><span class="sxs-lookup"><span data-stu-id="acd57-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="acd57-258">第 4 章 - 開発環境を設定します。</span><span class="sxs-lookup"><span data-stu-id="acd57-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="acd57-259">作成、展開用モジュール*IoT Hub の Edge*、Windows 10 を実行している開発用コンピューターにインストールされている、次のコンポーネントが必要になります。</span><span class="sxs-lookup"><span data-stu-id="acd57-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="acd57-260">[Windows の docker](https://store.docker.com/editions/community/docker-ce-desktop-windows)、ダウンロードできるようにするアカウントを作成するよう求められます。</span><span class="sxs-lookup"><span data-stu-id="acd57-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="acd57-261">[![windows の docker をダウンロードします。](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="acd57-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="acd57-262">Docker 必要があります*Windows 10 PRO*、 *Enterprise 14393*、または*Windows Server 2016 RTM*を実行します。</span><span class="sxs-lookup"><span data-stu-id="acd57-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="acd57-263">その他のバージョンの Windows 10 を実行している場合、Docker を使用してをインストールしてくださいことができます、 [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="acd57-264">[Python 3.6](https://www.python.org/downloads/)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="acd57-265">[![python 3.6 をダウンロードします。](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="acd57-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="acd57-266">[Visual Studio Code (VS Code とも呼ばれます)](https://code.visualstudio.com/download)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="acd57-267">[![VS Code をダウンロードします。](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="acd57-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="acd57-268">上記で説明したソフトウェアのインストール後は、コンピューターを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="acd57-269">第 5 章 - Ubuntu 環境のセットアップ</span><span class="sxs-lookup"><span data-stu-id="acd57-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="acd57-270">デバイスのセットアップ移動できますようになりました**Ubuntu OS を実行している**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="acd57-271">ボード上、コンテナーをデプロイするために必要なソフトウェアをインストールするのには、下の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="acd57-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="acd57-272">ターミナル、コマンドの前に常に**sudo**管理者ユーザーとして実行します。</span><span class="sxs-lookup"><span data-stu-id="acd57-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="acd57-273">つまり、します。</span><span class="sxs-lookup"><span data-stu-id="acd57-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="acd57-274">開く、 **Ubuntu のターミナル**、次のコマンドを使用してインストールして**pip**:</span><span class="sxs-lookup"><span data-stu-id="acd57-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [!ヒント]<span data-ttu-id="acd57-275"> を開く\*ターミナル\*キーボード ショートカットを使用して非常に簡単に使用します。*\*Ctrl + Alt + T*\*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-275"> You can open \*Terminal* very easily through using the keyboard shortcut: *\*Ctrl + Alt + T*\*.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="acd57-276">この章では、する必要があります、によって*ターミナル*デバイス ストレージを使用するアクセス許可、および入力するを**はい/いいえ**(はいまたは no)、型 **'y'**、キーを押しますと、**Enter**を受け入れるためのキー。</span><span class="sxs-lookup"><span data-stu-id="acd57-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="acd57-277">そのコマンドが完了すると、次のコマンドを使用してをインストールする**curl**:</span><span class="sxs-lookup"><span data-stu-id="acd57-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="acd57-278">1 回**pip**と**curl**は、次のコマンドを使用してインストールする、インストールされている、 **IoT Edge ランタイム**を展開し、ボード上のモジュールを制御するために必要になります。</span><span class="sxs-lookup"><span data-stu-id="acd57-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. <span data-ttu-id="acd57-279">この時点で求められますを開く、*ランタイム構成ファイル*、挿入する、 **Device Connection String**、(、メモ帳で)、メモしたを作成するとき、 **IoT Hub サービス** ([第 3 章の手順 14 で](#chapter-3---the-iot-hub-service))。</span><span class="sxs-lookup"><span data-stu-id="acd57-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="acd57-280">そのファイルを開くターミナルで次の行を実行します。</span><span class="sxs-lookup"><span data-stu-id="acd57-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="acd57-281">**Config.yaml**ファイルが表示されている、編集するための準備完了になります。</span><span class="sxs-lookup"><span data-stu-id="acd57-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="acd57-282">このファイルが開いたら、やや混乱を招く場合があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="acd57-283">テキスト内で、このファイルを編集する必要がある、*ターミナル*自体。</span><span class="sxs-lookup"><span data-stu-id="acd57-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="acd57-284">キーボードの矢印キーを使用して、スクロール ダウン (少し方法下へスクロールする必要があります) を含む行に到達する"。</span><span class="sxs-lookup"><span data-stu-id="acd57-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="acd57-285">"**\<デバイス接続文字列をここでの追加 &GT;**"。</span><span class="sxs-lookup"><span data-stu-id="acd57-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="acd57-286">行を置き換える **、中かっこも含め**で、**デバイスの接続文字列**先ほどメモします。</span><span class="sxs-lookup"><span data-stu-id="acd57-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="acd57-287">キーボードの場所に、接続文字列とキーを押して、 **CTRL + X**キー ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="acd57-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="acd57-288">」と入力して確認するよう求められます**Y**します。次に、キーを押して、 **」と入力**キーを確認します。</span><span class="sxs-lookup"><span data-stu-id="acd57-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="acd57-289">通常に戻り、*ターミナル*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="acd57-290">インストールがこれらのコマンドがすべて正常に実行すると、 **IoT Edge ランタイム**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="acd57-291">初期化されると、ランタイムは、デバイスの電源が入っている独自たびに開始して、バック グラウンドでモジュールから展開するを待つ内に配置されます、 **IoT Hub Service**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="acd57-292">初期化するために次のコマンドラインの実行、 *IoT Edge ランタイム*:</span><span class="sxs-lookup"><span data-stu-id="acd57-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="acd57-293">.Yaml ファイル、または上記の設定を変更する場合、上記の再起動の行を再度実行する必要があります。 内*ターミナル*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="acd57-294">チェック、 *IoT Edge ランタイム*次のコマンドラインを実行している別の状態。</span><span class="sxs-lookup"><span data-stu-id="acd57-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="acd57-295">ランタイムが、状態で表示される必要があります**アクティブ (実行中)** を緑のテキスト。</span><span class="sxs-lookup"><span data-stu-id="acd57-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="acd57-296">キーを押して、 **Ctrl + C**キー、状態 ページを終了します。</span><span class="sxs-lookup"><span data-stu-id="acd57-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="acd57-297">確認することができます、 *IoT Edge ランタイム*次のコマンドを入力して、コンテナーを正しく引いています。</span><span class="sxs-lookup"><span data-stu-id="acd57-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="acd57-298">2 つのコンテナーの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="acd57-299">これらは、IoT Hub サービス (edgeAgent および edgeHub) によって自動的に作成される既定のモジュールです。</span><span class="sxs-lookup"><span data-stu-id="acd57-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="acd57-300">作成して、独自のモジュールを展開すると、既定の下に、この一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="acd57-301">第 6 章 - 拡張機能をインストールします。</span><span class="sxs-lookup"><span data-stu-id="acd57-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="acd57-302">次のいくつかの章 (6 ~ 9) では、Windows 10 コンピューターで実行します。</span><span class="sxs-lookup"><span data-stu-id="acd57-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="acd57-303">開いている**VS Code**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="acd57-304">をクリックして、**拡張機能**(正方形) ボタンの左側の VS、バーコードを開く、**拡張機能パネル**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="acd57-305">検索し、インストールの場合は、(次の図に示すように)、次の拡張機能。</span><span class="sxs-lookup"><span data-stu-id="acd57-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="acd57-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="acd57-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="acd57-307">Azure IoT Toolkit</span><span class="sxs-lookup"><span data-stu-id="acd57-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="acd57-308">Docker</span><span class="sxs-lookup"><span data-stu-id="acd57-308">Docker</span></span>   

    ![コンテナーを作成します。](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="acd57-310">拡張機能がインストールされると、VS Code を再度開くを閉じています。</span><span class="sxs-lookup"><span data-stu-id="acd57-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="acd57-311">VS Code で、もう一度開きに移動します**ビュー > 統合ターミナル**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-311">With VS Code open once more, navigate to **View > Integrated terminal**.</span></span>

6. <span data-ttu-id="acd57-312">インストールするようになりました**Cookiecutter**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="acd57-313">ターミナルで次の bash コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="acd57-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [!ヒント]<span data-ttu-id="acd57-314"> で次のコマンドに問題がある場合:</span><span class="sxs-lookup"><span data-stu-id="acd57-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="acd57-315">VS Code、および/またはコンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="acd57-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="acd57-316">切り替える必要があります、 **VS Code ターミナル**を使用してつまり、Python をインストールする 1 つ**Powershell** (特に場合に、Python 環境は、コンピューターに既にインストールされている)。</span><span class="sxs-lookup"><span data-stu-id="acd57-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="acd57-317">ターミナルを開き、端末の右側にあるメニューのドロップダウンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="acd57-318">![コンテナーを作成します。](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="acd57-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="acd57-319">確認、 **Python**としてのインストール パスが追加されます**環境変数**コンピューターにします。</span><span class="sxs-lookup"><span data-stu-id="acd57-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="acd57-320">Cookiecutter は、同じロケーション パスの一部にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="acd57-321">これに従ってください[環境変数の詳細については、リンク](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx)、</span><span class="sxs-lookup"><span data-stu-id="acd57-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="acd57-322">1 回**Cookiecutter** 、インストールが完了した、コンピューターを再起動する必要がありますように**Cookiecutter**はシステムの環境でのコマンドとして認識します。</span><span class="sxs-lookup"><span data-stu-id="acd57-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="acd57-323">7 -」の章のコンテナー ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="acd57-324">この時点では、モジュールにプッシュされると、コンテナーを作成する必要があります、 *Container Registry*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="acd57-325">使用するコンテナーをプッシュすると、 *IoT Hub の Edge*を実行しているデバイスにデプロイするサービス、 *IoT Edge ランタイム*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="acd57-326">VS Code からクリックして**ビュー > コマンド パレット**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-326">From VS Code, click **View > Command palette**.</span></span>

2. <span data-ttu-id="acd57-327">パレットで、検索し、実行**Azure IoT Edge:新しい Iot Edge ソリューション**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="acd57-328">ソリューションを作成する場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="acd57-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="acd57-329">キーを押して、 **」と入力**キー、場所をそのままにします。</span><span class="sxs-lookup"><span data-stu-id="acd57-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="acd57-330">ソリューションに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="acd57-330">Give a name to your solution.</span></span> <span data-ttu-id="acd57-331">キーを押して、 **Enter**キーを指定された名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="acd57-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="acd57-332">今すぐ求め、ソリューション テンプレートの framework を選択します。</span><span class="sxs-lookup"><span data-stu-id="acd57-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="acd57-333">クリックして**Python モジュール**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-333">Click **Python Module**.</span></span> <span data-ttu-id="acd57-334">キーを押して、 **Enter**キーは、この選択内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="acd57-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="acd57-335">モジュールの名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="acd57-335">Give a name to your module.</span></span> <span data-ttu-id="acd57-336">キーを押して、 **Enter**キーをモジュールの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="acd57-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="acd57-337">後で使用するために、モジュール名 (、メモ帳) をメモしてを実行することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="acd57-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="acd57-338">構築済みわかります*Docker イメージ リポジトリ*パレットにアドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="acd57-339">次のようになります。</span><span class="sxs-lookup"><span data-stu-id="acd57-339">It will look like:</span></span>

    <span data-ttu-id="acd57-340">**localhost:5000/名前、モジュールの**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="acd57-341">削除**localhost:5000**、およびその場所の挿入、*Container Registry* **ログイン サーバー**アドレスで、作成するときにメモしておいた、**コンテナーレジストリ サービス**([手順 8、第 2 章の](#chapter-2---the-container-registry-service))。</span><span class="sxs-lookup"><span data-stu-id="acd57-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="acd57-342">キーを押して、 **Enter**キー、アドレスを確認します。</span><span class="sxs-lookup"><span data-stu-id="acd57-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="acd57-343">この時点で、テンプレート、Python モジュールを含むソリューションが作成され、その構造が表示されます、**探索タブ**画面の左側にある、VS Code の。</span><span class="sxs-lookup"><span data-stu-id="acd57-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="acd57-344">場合、**探索タブ**が開いていない場合、開くことができますが、左側のバーで、最上位のボタンをクリックしています。</span><span class="sxs-lookup"><span data-stu-id="acd57-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![コンテナーを作成します。](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="acd57-346">この章の最後の手順は、をクリックして開く、 **.env ファイル**、内から、 **タブの調査**、追加、 *Container Registry* **ユーザー名**と**パスワード**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="acd57-347">このファイルは、git によって無視されますが、コンテナーでは、ビルドにへのアクセスに資格情報の設定は、**コンテナー レジストリ サービス**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![コンテナーを作成します。](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="acd57-349">第 8 章 - コンテナー ソリューションの編集</span><span class="sxs-lookup"><span data-stu-id="acd57-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="acd57-350">今すぐは、次のファイルを更新することで、コンテナー ソリューションを行います。</span><span class="sxs-lookup"><span data-stu-id="acd57-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="acd57-351">*メイン<span></span>.py* python スクリプト。</span><span class="sxs-lookup"><span data-stu-id="acd57-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="acd57-352">*requirements.txt*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-352">*requirements.txt*.</span></span>
- <span data-ttu-id="acd57-353">*deployment.template.json*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="acd57-354">*Dockerfile.amd64*</span><span class="sxs-lookup"><span data-stu-id="acd57-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="acd57-355">作成して、*イメージ*と照合するイメージを確認する python スクリプトで使用される、フォルダー、*カスタム ビジョン モデル*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="acd57-356">最後に、追加、 *labels.txt* 、モデルを読み取るためのファイルと*model.pb*ファイルで、これは、モデルです。</span><span class="sxs-lookup"><span data-stu-id="acd57-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="acd57-357">VS Code で開き、モジュール フォルダーに移動し、という名前のスクリプトを探して**メイン<span></span>.py**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="acd57-358">ダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="acd57-358">Double-click to open it.</span></span>

2. <span data-ttu-id="acd57-359">ファイルの内容を削除し、次のコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="acd57-359">Delete the content of the file and insert the following code:</span></span>

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  <span data-ttu-id="acd57-360">というファイルを開く**requirements.txt**、その内容を次に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="acd57-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="acd57-361">というファイルを開く**deployment.template.json**、その次のコンテンツを置き換えると、以下のガイドライン。</span><span class="sxs-lookup"><span data-stu-id="acd57-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="acd57-362">自分で、一意の JSON 構造を必要があります、ため (例をコピー) ではなく手動で編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="acd57-363">簡単にするを使用して、次のガイドとして画像。</span><span class="sxs-lookup"><span data-stu-id="acd57-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="acd57-364">次に、さまざまな領域がある**は変更しないでくださいは黄色で強調表示**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="acd57-365">**を削除する必要があるセクションでは、強調表示されている red です。**</span><span class="sxs-lookup"><span data-stu-id="acd57-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="acd57-366">正しいの角かっこを削除するように注意してくださいし、も、コンマを削除します。</span><span class="sxs-lookup"><span data-stu-id="acd57-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![コンテナーを作成します。](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="acd57-368">完了した JSON は、次の図のようになります (一意の相違点は、サーバーでは、:*モジュール/ユーザー名/パスワード/モジュール名参照*)。</span><span class="sxs-lookup"><span data-stu-id="acd57-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![コンテナーを作成します。](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="acd57-370">というファイルを開く**Dockerfile.amd64**、その内容を次に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="acd57-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  <span data-ttu-id="acd57-371">下にフォルダーを右クリックして**モジュール**(以前; 指定した名前になりますで例をそれをさらに、呼び出されます*pythonmodule*)、 をクリック**新しいフォルダー**.</span><span class="sxs-lookup"><span data-stu-id="acd57-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="acd57-372">フォルダーの名前**イメージ**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="acd57-373">フォルダー内には、マウスまたはキーボードを含む一部のイメージを追加します。</span><span class="sxs-lookup"><span data-stu-id="acd57-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="acd57-374">イメージ、Tensorflow モデルによって分析されるものになります。</span><span class="sxs-lookup"><span data-stu-id="acd57-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="acd57-375">独自のモデルを使用している場合は、独自のモデル データを反映するようにこれを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="acd57-376">取得する必要がありますこれで、 **labels.txt**と**model.pb**以前ダウンロード モデル フォルダーからファイルを (または独自から作成した**Custom Vision Service**) で[第 1 章](#chapter-1---retrieve-the-custom-vision-model)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="acd57-377">ファイルを作成したら、その他のファイルと共に、ソリューション内でそれらを配置します。</span><span class="sxs-lookup"><span data-stu-id="acd57-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="acd57-378">最終的な結果は、次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="acd57-378">The final result should look like the image below:</span></span>

    ![コンテナーを作成します。](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="acd57-380">第 9 章 – パッケージのコンテナーとしてソリューション</span><span class="sxs-lookup"><span data-stu-id="acd57-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="acd57-381">コンテナーとして、ファイルを「パッケージ」し、それをプッシュする準備が整いました、 **Azure Container Registry**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="acd57-382">VS Code 内で開く、*統合ターミナル*(**ビュー > 統合ターミナル/CTRL + '**) へのログインに次の行を使用して**Docker** (の値に置き換えてください、コマンドの資格情報を**Azure Container Registry (ACR)**)。</span><span class="sxs-lookup"><span data-stu-id="acd57-382">Within VS Code, open the *Integrated Terminal* (**View > Integrated Terminal / CTRL + \`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="acd57-383">ファイルを右クリックして**deployment.template.json**、 をクリック**IoT Edge ソリューションのビルド**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="acd57-384">このビルド プロセス (デバイス) によってはかなり時間のかかるので、待機します。</span><span class="sxs-lookup"><span data-stu-id="acd57-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="acd57-385">ビルド プロセスが完了した後、 **deployment.json**という名前の新しいフォルダー内のファイルが作成されているが**config**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![デプロイを作成します。](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="acd57-387">開く、**コマンド パレット**、もう一度検索して**Azure:サインイン**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="acd57-388">Azure アカウントの資格情報以外を使用して、画面の指示をに従ってください。VS Code の提供するためのオプション*コピーして開く*、どちらの間もなくし、既定の web ブラウザーを開きますが、デバイス コードをコピーします。</span><span class="sxs-lookup"><span data-stu-id="acd57-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="acd57-389">メッセージが表示されたら、コンピューターの認証に、デバイス コードを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="acd57-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![コピーを開きます](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="acd57-391">表示されますの下にある符号付き 1 回、*探索*パネル、という名前の新しいセクション**Azure IoT Hub デバイス**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="acd57-392">展開するには、このセクションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-392">Click this section to expand it.</span></span>

    ![エッジ デバイス](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="acd57-394">デバイスがここではない場合を右クリックする必要があります。 *Azure IoT Hub デバイス*、をクリックし、 **IoT Hub 接続文字列の設定**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="acd57-395">表示されますが、**コマンド パレット**(VS Code の上部) にはプロンプトで入力する、*接続文字列*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="acd57-396">これは、*接続文字列*の最後にメモした[第 3 章](#chapter-3---the-iot-hub-service)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="acd57-397">キーを押して、 **Enter**で文字列をコピーした後、キーします。</span><span class="sxs-lookup"><span data-stu-id="acd57-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="acd57-398">デバイスは、読み込み、および表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-398">Your device should load, and appear.</span></span> <span data-ttu-id="acd57-399">デバイス名を右クリックし、をクリック**1 つのデバイスの Create Deployment**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![デプロイを作成します。](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="acd57-401">表示されます、*ファイル エクスプ ローラー*プロンプトに移動することができます、 **config**フォルダー、および選択し、 **deployment.json**ファイル。</span><span class="sxs-lookup"><span data-stu-id="acd57-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="acd57-402">そのファイルを選択すると、クリックして、 **Edge 配置マニフェストの選択**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![デプロイを作成します。](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="acd57-404">この時点で指定した、 **IoT Hub Service**マニフェスト モジュールとしてから、コンテナーをデプロイするために、 **Azure Container Registry**、実質的に、デバイスに展開します。</span><span class="sxs-lookup"><span data-stu-id="acd57-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="acd57-405">デバイスから IoT Hub に送信されるメッセージを表示するには、もう一度右クリックで、デバイス名を**Azure IoT Hub デバイス**セクションで、**エクスプ ローラー**パネルをクリックします**監視の開始D2C メッセージ**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="acd57-406">VS ターミナルで、デバイスから送信されたメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="acd57-407">患者に、これは時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="acd57-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="acd57-408">デバッグ、および配置が成功したかどうかにチェックの次の章を参照してください。</span><span class="sxs-lookup"><span data-stu-id="acd57-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="acd57-409">内のイメージ間でこのモジュールに処理され、今すぐ、**イメージ**フォルダーの各イテレーションで分析したりと。</span><span class="sxs-lookup"><span data-stu-id="acd57-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="acd57-410">これは、単なる明らかに、IoT Edge デバイスの環境で動作する基本的な機械学習モデルを取得する方法のデモンストレーションです。</span><span class="sxs-lookup"><span data-stu-id="acd57-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="acd57-411">この例の機能を展開するには、いくつかの方法で続行する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="acd57-412">デバイスに接続されていて、images フォルダーにイメージを保存します。 web カメラから写真をキャプチャすると、コンテナーで 1 つの方法をいくつかのコードなどでした。</span><span class="sxs-lookup"><span data-stu-id="acd57-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="acd57-413">別の方法でしたするイメージのコピー、IoT デバイスからコンテナーにします。</span><span class="sxs-lookup"><span data-stu-id="acd57-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="acd57-414">そのための実用的な方法では、IoT デバイス (おそらく小規模なアプリがジョブを実行、プロセスを自動化する場合) のターミナルで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="acd57-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="acd57-415">このコマンドをテストするには、ファイルが格納されているフォルダーの場所から手動で実行します。</span><span class="sxs-lookup"><span data-stu-id="acd57-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="acd57-416">第 10 章 - IoT Edge ランタイムのデバッグ</span><span class="sxs-lookup"><span data-stu-id="acd57-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="acd57-417">コマンドライン、および監視およびのメッセージング アクティビティをデバッグするためのヒントの一覧を次に、 *IoT Edge ランタイム*から、 **Ubuntu デバイス**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="acd57-418">チェック、 *IoT Edge ランタイム*次のコマンドラインを実行している別の状態。</span><span class="sxs-lookup"><span data-stu-id="acd57-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="acd57-419">キーを押すように**Ctrl + C**ステータスの表示が完了する。</span><span class="sxs-lookup"><span data-stu-id="acd57-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="acd57-420">現在展開されているコンテナーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="acd57-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="acd57-421">場合、 *IoT Hub Service*コンテナーを正常にデプロイが次のコマンドラインを実行してが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="acd57-422">または</span><span class="sxs-lookup"><span data-stu-id="acd57-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="acd57-423">上記の適しているかどうか、モジュールのデプロイが正常にリストに表示されるかを確認するにはそれ以外の場合は、**のみ**を参照してください、 *edgeHub*と*edgeAgent*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="acd57-424">コンテナーのコードのログを表示するには、次のコマンドラインを実行します。</span><span class="sxs-lookup"><span data-stu-id="acd57-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="acd57-425">**IoT Edge ランタイムを管理する便利なコマンド:**</span><span class="sxs-lookup"><span data-stu-id="acd57-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="acd57-426">ホストのすべてのコンテナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="acd57-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="acd57-427">停止する、 *IoT Edge ランタイム*:</span><span class="sxs-lookup"><span data-stu-id="acd57-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="acd57-428">章 11 - Table Service を作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="acd57-429">ストレージ リソースを作成して、Azure テーブル サービスを作成する、Azure Portal に移動します。</span><span class="sxs-lookup"><span data-stu-id="acd57-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="acd57-430">サインインしていない場合のログイン、 [Azure Portal](https://portal.azure.com)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="acd57-431">ログインすると、をクリックして**リソースの作成**、左上の検索および上隅にある**ストレージ アカウント**、キーを押すと、 **」と入力**キー、検索を開始します。</span><span class="sxs-lookup"><span data-stu-id="acd57-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="acd57-432">表示されていますとクリックして**ストレージ アカウント - blob、ファイル、テーブル、キュー**一覧から。</span><span class="sxs-lookup"><span data-stu-id="acd57-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![ストレージ アカウントの検索](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="acd57-434">新しいページがの説明を入力、**ストレージ アカウント**サービス。</span><span class="sxs-lookup"><span data-stu-id="acd57-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="acd57-435">このダイアログ ボックスの左下にある at をクリックして、**作成**ボタンは、サービスのこのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="acd57-437">クリックすると**作成**パネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="acd57-438">必要な挿入**名前**このサービス インスタンスの (*すべて小文字である必要があります*)。</span><span class="sxs-lookup"><span data-stu-id="acd57-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="acd57-439">**デプロイ モデル**、 をクリックして**Resource manager**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="acd57-440">**アカウントの種類**、ドロップダウン メニューを使用して、クリックして**ストレージ (汎用 v1)** します。</span><span class="sxs-lookup"><span data-stu-id="acd57-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="acd57-441">適切なクリックして**場所**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="acd57-442">**レプリケーション**ドロップダウン メニューで、をクリックして**読み取りアクセスの geo 冗長ストレージ (RA-GRS)** します。</span><span class="sxs-lookup"><span data-stu-id="acd57-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="acd57-443">**パフォーマンス**、 をクリックして**標準**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="acd57-444">内で、**転送が必須のセキュリティで保護された**セクションで、**無効**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="acd57-445">**サブスクリプション**ドロップダウン メニューで、適切なサブスクリプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="acd57-446">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="acd57-447">リソース グループは、監視、プロビジョニング、アクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="acd57-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="acd57-448">勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。</span><span class="sxs-lookup"><span data-stu-id="acd57-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="acd57-449">詳細にする場合について、Azure リソース グループに従ってくださいこの[リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="acd57-450">まま**仮想ネットワーク**として**無効になっている**するためのオプションは、この場合、します。</span><span class="sxs-lookup"><span data-stu-id="acd57-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="acd57-451">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-451">Click **Create**.</span></span>

        ![ストレージの詳細を入力します。](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="acd57-453">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="acd57-454">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="acd57-455">新しいサービス インスタンスを探索する通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-455">Click on the notifications to explore your new Service instance.</span></span>

    ![新しい記憶域の通知](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="acd57-457">をクリックして、**リソースに移動**通知で、[新しい記憶域のサービス インスタンスの概要] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![リソースに移動します。](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="acd57-459">概要 ページの右側にあるをクリックします。**テーブル**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![テーブル](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="acd57-461">右側のパネルを表示する変更は、 **Table Service**については、の新しいテーブルを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="acd57-462">クリックして、 **+ テーブル**ボタンの左上隅をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![テーブルを開く](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="acd57-464">入力する必要があります、新しいページが表示されます、**テーブル名**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="acd57-465">これは、(関数アプリ、および Power BI の作成) 以降の章で、アプリケーションでデータを指すために使用する名前です。</span><span class="sxs-lookup"><span data-stu-id="acd57-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="acd57-466">挿入**IoTMessages**名として (、独自に選択することができますので、このドキュメントの後半で使用する場合) をクリック**OK**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="acd57-467">新しいテーブルが作成されたら、できなく内を確認する、 **Table Service** (下部) のページ。</span><span class="sxs-lookup"><span data-stu-id="acd57-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![新しいテーブルの作成](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="acd57-469">今すぐクリックして**アクセス キー**のコピーを作成し、**ストレージ アカウント名**と**キー** (、メモ帳を使用)、これらの値は使用、このコースの後半で作成するときに、**Azure Function App**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![新しいテーブルの作成](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="acd57-471">までスクロールし、左側のパネルを使用して、 *Table Service*セクションをクリックします**テーブル**(または**参照テーブル**、新しいポータル) のコピーを作成し、 **テーブルの URL** (、メモ帳を使用)。</span><span class="sxs-lookup"><span data-stu-id="acd57-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="acd57-472">テーブルをリンクするときに、このコースの後半でこの値が使用されます、 **Power BI**アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="acd57-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![新しいテーブルの作成](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="acd57-474">第 12 章 - Azure テーブルの完了</span><span class="sxs-lookup"><span data-stu-id="acd57-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="acd57-475">これで、 **Table Service**ストレージ アカウントを設定したら、情報格納および取得するために使用するデータを追加する時間。</span><span class="sxs-lookup"><span data-stu-id="acd57-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="acd57-476">テーブルの編集を実行できます**Visual Studio**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="acd57-477">開いている**Visual Studio** (**いない**Visual Studio Code)。</span><span class="sxs-lookup"><span data-stu-id="acd57-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="acd57-478">メニューから、次のようにクリックします。**ビュー > Cloud Explorer**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-478">From the menu, click **View > Cloud Explorer**.</span></span>

    ![クラウド エクスプ ローラーを開く](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="acd57-480">**Cloud Explorer** (に患者、読み込み時間がかかる場合があります) がドッキングされている項目として開きます。</span><span class="sxs-lookup"><span data-stu-id="acd57-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="acd57-481">サブスクリプションの作成に使用する場合、*ストレージ アカウント*が表示されないできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="acd57-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="acd57-482">Azure Portal を使用したものと同じアカウントにログインします。</span><span class="sxs-lookup"><span data-stu-id="acd57-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="acd57-483">(アカウント設定からフィルターを適用する必要があります)、アカウントの管理ページからサブスクリプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="acd57-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![サブスクリプションが見つかりません](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="acd57-485">Azure クラウド サービスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="acd57-486">検索**ストレージ アカウント**アカウントを展開するの左側にある矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![ストレージ アカウント を開きます](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="acd57-488">展開されている場合、新しく作成した後**ストレージ アカウント**できるようにします。</span><span class="sxs-lookup"><span data-stu-id="acd57-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="acd57-489">ストレージの左側にある矢印をクリックしを展開したら探します**テーブル**を表示する横の矢印をクリックします、**テーブル**最後の章で作成しました。</span><span class="sxs-lookup"><span data-stu-id="acd57-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="acd57-490">ダブルクリックして、**テーブル**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="acd57-491">テーブルには、Visual Studio ウィンドウの中央に開かれます。</span><span class="sxs-lookup"><span data-stu-id="acd57-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="acd57-492">テーブル アイコンをクリックして、 **+** には、(+)。</span><span class="sxs-lookup"><span data-stu-id="acd57-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![新しいテーブルを追加します。](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="acd57-494">ウィンドウがするためのプロンプトを表示する表示*エンティティの追加*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="acd57-495">3 つのプロパティである必要が 1 つだけのエンティティを作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="acd57-496">わかります*PartitionKey*と*RowKey*が既に提供されている、使用される場合は、テーブルでデータを検索します。</span><span class="sxs-lookup"><span data-stu-id="acd57-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![パーティションと行キー](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="acd57-498">次の値を更新します。</span><span class="sxs-lookup"><span data-stu-id="acd57-498">Update the following values:</span></span>

    - <span data-ttu-id="acd57-499">名前:**PartitionKey**値。**PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="acd57-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="acd57-500">名前:**RowKey**値。**RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="acd57-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="acd57-501">をクリックし、**プロパティを追加**(の左下に、*エンティティの追加*ウィンドウ) し、次のプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="acd57-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="acd57-502">**MessageContent**、として、*文字列*値を空のままにします。</span><span class="sxs-lookup"><span data-stu-id="acd57-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="acd57-503">次の図に、テーブルと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-503">Your table should match the one in the image below:</span></span>

    ![正しい値を追加します。](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="acd57-505">エンティティの数 1、行キーでがなぜ理由ためにである可能性があります、複数のメッセージを追加する実験をご希望する必要がありますこのコースでさらにします。</span><span class="sxs-lookup"><span data-stu-id="acd57-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="acd57-506">クリックして**OK**は終了するとき。</span><span class="sxs-lookup"><span data-stu-id="acd57-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="acd57-507">テーブルには、使用する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="acd57-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="acd57-508">章 13 - Azure Function App を作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="acd57-509">作成に時間をここでは、 *Azure Function App*、によって呼び出される、 *IoT Hub Service*を格納する、 *IoT Edge*デバイスにメッセージが、 **テーブル**サービスは、前の章で作成しました。</span><span class="sxs-lookup"><span data-stu-id="acd57-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="acd57-510">最初に、必要なライブラリの読み込みに、Azure 関数を許可するファイルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="acd57-511">開いている**メモ帳**(キーを押して、 *Windows キー*、および種類*メモ帳*)。</span><span class="sxs-lookup"><span data-stu-id="acd57-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![メモ帳を開く](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="acd57-513">メモ帳を開く、そこに以下の JSON 構造を挿入します。</span><span class="sxs-lookup"><span data-stu-id="acd57-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="acd57-514">完了したら、としてデスクトップに保存**project.json**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="acd57-515">このファイルは、関数を使用してライブラリを定義します。</span><span class="sxs-lookup"><span data-stu-id="acd57-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="acd57-516">NuGet を使用した場合は、使い慣れたが検索されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="acd57-517">名前の付け方が正しい; 重要です。確認は **、.txt が付いていない**ファイル拡張子。</span><span class="sxs-lookup"><span data-stu-id="acd57-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="acd57-518">参照に以下をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="acd57-518">See below for reference:</span></span>
    >
    > ![保存の JSON](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="acd57-520">[Azure ポータル](https://portal.azure.com) にログインします。</span><span class="sxs-lookup"><span data-stu-id="acd57-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="acd57-521">ログインした後は、をクリックして**リソースの作成**左上隅にある検索して**Function App**、キーを押すと、 **」と入力**キーを検索します。</span><span class="sxs-lookup"><span data-stu-id="acd57-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="acd57-522">クリックして*Function App*結果から、新しいパネルを開きます。</span><span class="sxs-lookup"><span data-stu-id="acd57-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![関数アプリの検索](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="acd57-524">新しいパネルがの説明を入力、 **Function App**サービス。</span><span class="sxs-lookup"><span data-stu-id="acd57-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="acd57-525">このパネルの下部にある左はで、をクリックして、**作成**ボタンは、この関連付けサービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![関数アプリ インスタンス](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="acd57-527">クリックすると**作成**次を入力します。</span><span class="sxs-lookup"><span data-stu-id="acd57-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="acd57-528">**アプリ名**、このサービス インスタンスのご希望の名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="acd57-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="acd57-529">選択、**サブスクリプション**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="acd57-530">作成時刻の場合、これは、最初に、適切な価格レベルを選択、 **Function App サービス**、free レベルを使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="acd57-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="acd57-531">選択、**リソース グループ**か新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="acd57-532">リソース グループは、監視、プロビジョニング、アクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="acd57-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="acd57-533">勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。</span><span class="sxs-lookup"><span data-stu-id="acd57-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="acd57-534">詳細にする場合について、Azure リソース グループに従ってくださいこの[リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。</span><span class="sxs-lookup"><span data-stu-id="acd57-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="acd57-535">**OS**、目的のプラットフォームであるために、Windows をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="acd57-536">選択、**ホスティング プラン**(このチュートリアルを使用して、**従量課金プラン**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="acd57-537">選択、**場所**(前の手順で作成したストレージと同じ場所を選択)</span><span class="sxs-lookup"><span data-stu-id="acd57-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="acd57-538">**ストレージ**セクション **、前の手順で作成したストレージ サービスを選択する必要があります**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="acd57-539">必要はありません*Application Insights*このアプリでため、自由に**オフ**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="acd57-540">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-540">Click **Create**.</span></span>

        ![新しいインスタンスを作成します。](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="acd57-542">クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="acd57-543">通知は、サービス インスタンスが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![新しい通知](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="acd57-545">デプロイが成功すると、通知をクリックします (終了)。</span><span class="sxs-lookup"><span data-stu-id="acd57-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="acd57-546">をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![リソースに移動します。](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="acd57-548">新しいパネルの左側にある クリックして、 **+** (隣にアイコン +)*関数*、新しい関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="acd57-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![新しい関数を追加します。](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="acd57-550">中央のパネル内、**関数**作成ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="acd57-551">さらに、下にスクロールし、をクリックして**カスタム関数**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-551">Scroll down further, and click on **Custom function**.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="acd57-553">次のページが表示されるまで下へスクロール**IoT Hub (イベント ハブ)** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="acd57-555">**IoT Hub (イベント ハブ)** ブレードで、設定、**言語**に**C#** し、**新しい**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="acd57-557">このウィンドウは表示されますが、ことを確認します**IoT Hub**が選択されているとの名前、 *IoT Hub*の名前を持つ対応するフィールド、 *IoT Hub サービス*必要のあります。以前に作成 ([手順 8、第 3 章の](#chapter-3---the-iot-hub-service))。</span><span class="sxs-lookup"><span data-stu-id="acd57-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="acd57-558">をクリックし、**選択**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-558">Then click the **Select** button.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="acd57-560">戻り、 **IoT Hub (イベント ハブ)** ブレードで、クリック**作成**です。</span><span class="sxs-lookup"><span data-stu-id="acd57-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="acd57-562">関数エディターにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="acd57-562">You will be redirected to the function editor.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="acd57-564">すべてのコードを削除し、次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="acd57-564">Delete all the code in it and replace it with the following:</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. <span data-ttu-id="acd57-565">適切な値に対応するように、次の変数を変更 (**テーブル**と**ストレージ**値から[11、13 をそれぞれ、第 11 章の手順](#chapter-11---create-table-service))、使用される、**ストレージ アカウント**:</span><span class="sxs-lookup"><span data-stu-id="acd57-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="acd57-566">**tableName**の名前を持つ、**テーブル**内にある、**ストレージ アカウント**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="acd57-567">**tableURL**の URL を使用して、**テーブル**内にある、**ストレージ アカウント**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="acd57-568">**storageAccountName**の名前に対応する値の名前を持つ、**ストレージ アカウント**名。</span><span class="sxs-lookup"><span data-stu-id="acd57-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="acd57-569">**storageAccountKey**、以前に作成したストレージ サービスで取得したキーを使用します。</span><span class="sxs-lookup"><span data-stu-id="acd57-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="acd57-571">コードの場所で、次のようにクリックします。**保存**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="acd57-572">次に、クリックして、 **\<** (矢印) アイコンをページの右側にあります。</span><span class="sxs-lookup"><span data-stu-id="acd57-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="acd57-574">パネルは、右からにスライドします。</span><span class="sxs-lookup"><span data-stu-id="acd57-574">A panel will slide in from the right.</span></span> <span data-ttu-id="acd57-575">そのパネル で、**アップロード**、および*ファイル ブラウザー*が表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="acd57-576">、に移動し、クリックすると、、 **project.json**ファイルで、で作成した**メモ帳**以前は、順にクリックします、**オープン**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="acd57-577">このファイルは、関数が使用するライブラリを定義します。</span><span class="sxs-lookup"><span data-stu-id="acd57-577">This file defines the libraries that your function will use.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="acd57-579">ファイルがアップロードされると、右側のパネルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="acd57-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="acd57-580">内で開くをクリックすると、**関数**エディター。</span><span class="sxs-lookup"><span data-stu-id="acd57-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="acd57-581">表示する必要があります**まったく**次のイメージと同じです。</span><span class="sxs-lookup"><span data-stu-id="acd57-581">It must look **exactly** the same as the next image.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="acd57-583">この時点でものメッセージを格納する、関数の機能をテストするよいでしょう、*テーブル*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="acd57-584">ウィンドウの上部右側にある、 をクリックして**テスト**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-584">On the top right side of the window, click on **Test**.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="acd57-586">メッセージの挿入、**要求本文**で上の図に示すように、**実行**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="acd57-587">関数が実行され、結果の状態を表示する (緑色で表示されます**ステータス 202 Accepted**、上記の*出力*ウィンドウで、正常な呼び出しが)。</span><span class="sxs-lookup"><span data-stu-id="acd57-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![出力結果](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="acd57-589">第 14 章 – アクティブなメッセージの表示</span><span class="sxs-lookup"><span data-stu-id="acd57-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="acd57-590">今すぐ Visual Studio を開く場合 (**いない**Visual Studio Code) で保存するように、テスト メッセージの結果を視覚化できます、 *MessageContent*領域の文字列します。</span><span class="sxs-lookup"><span data-stu-id="acd57-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![カスタム関数](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="acd57-592">Table Service で Function App と Ubuntu デバイスのメッセージが表示されます、 *IoTMessages*テーブル。</span><span class="sxs-lookup"><span data-stu-id="acd57-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="acd57-593">を実行していない場合、デバイスを再度起動して、Visual Studio を使用して、デバイス、および、テーブル内のモジュールから結果メッセージを表示することができます*Cloud Explorer*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![データを視覚化します。](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="acd57-595">第 15 章「Power BI のセットアップ</span><span class="sxs-lookup"><span data-stu-id="acd57-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="acd57-596">セットアップは、IOT デバイスからデータを視覚化する**Power BI** (デスクトップのバージョン) からデータを収集、*テーブル*サービスで、先ほど作成しました。</span><span class="sxs-lookup"><span data-stu-id="acd57-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="acd57-597">*HoloLens*バージョンの Power BI を使用してそのデータを結果を視覚化します。</span><span class="sxs-lookup"><span data-stu-id="acd57-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="acd57-598">Windows 10 の Microsoft Store を開き、検索**Power BI Desktop**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="acd57-600">アプリケーションをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="acd57-600">Download the application.</span></span> <span data-ttu-id="acd57-601">これには、ダウンロードが完了したら、したら、それを開きます。</span><span class="sxs-lookup"><span data-stu-id="acd57-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="acd57-602">ログイン*Power BI*で、 **Microsoft 365 アカウント**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="acd57-603">ブラウザー、サインアップにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="acd57-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="acd57-604">サインアップし、Power BI アプリに戻ってもう一度サインインします。</span><span class="sxs-lookup"><span data-stu-id="acd57-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="acd57-605">をクリックして**データの取得**し、**より.**.</span><span class="sxs-lookup"><span data-stu-id="acd57-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="acd57-607">クリックして**Azure**、 **Azure Table Storage**、をクリックして**Connect**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="acd57-609">挿入を求められます、**テーブル URL**以前に収集した ([第 11 章の 13 の手順で](#chapter-11---create-table-service))、Table Service の作成中にします。</span><span class="sxs-lookup"><span data-stu-id="acd57-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="acd57-610">URL を挿入した後は、テーブル「サブ フォルダー」(IoTMessages は、このコースでは) を参照するパスの部分を削除します。</span><span class="sxs-lookup"><span data-stu-id="acd57-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="acd57-611">次の図に表示される最終的な結果があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="acd57-612">をクリックして**OK**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="acd57-614">挿入を求め、**ストレージ キー**書き留めた ([手順 11 第 11 章の](#chapter-11---create-table-service))、Table Storage を作成するときに以前。</span><span class="sxs-lookup"><span data-stu-id="acd57-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="acd57-615">をクリックして**Connect**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="acd57-617">A**ナビゲーター パネル**が表示されます、テーブルの横にあるボックスをオンにしをクリックして**ロード**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="acd57-619">テーブルが Power BI に読み込まれているようになりました、クエリが値を表示する必要しますが、あります。</span><span class="sxs-lookup"><span data-stu-id="acd57-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="acd57-620">これを行うにあるテーブル名を右クリックし、**フィールド パネル**画面の右側にあります。</span><span class="sxs-lookup"><span data-stu-id="acd57-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="acd57-621">をクリックして**クエリの編集**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="acd57-623">A **Power Query エディター**として、テーブルを表示する、新しいウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="acd57-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="acd57-624">[単語] をクリックして**レコード**内、*コンテンツ*格納されているコンテンツを視覚化する、テーブルの列。</span><span class="sxs-lookup"><span data-stu-id="acd57-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="acd57-626">をクリックして**Into テーブル**ウィンドウの上部左にあります。</span><span class="sxs-lookup"><span data-stu-id="acd57-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="acd57-628">をクリックして**閉じて適用**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="acd57-630">内で、クエリの読み込みが完了すると、**フィールド パネル**、画面の右側にある、パラメーターに対応するボックスをオンに**名前**と**値**を視覚化、 **MessageContent**列のコンテンツ。</span><span class="sxs-lookup"><span data-stu-id="acd57-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="acd57-632">をクリックして、**青いディスク アイコン**で任意のフォルダーで作業内容を保存するには、ウィンドウの左上。</span><span class="sxs-lookup"><span data-stu-id="acd57-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="acd57-634">ワークスペースに、テーブルをアップロードする [発行] ボタンをクリックすることができますようになりました。</span><span class="sxs-lookup"><span data-stu-id="acd57-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="acd57-635">メッセージが表示されたら、 をクリックして**個人用ワークスペース** をクリック*選択*します。</span><span class="sxs-lookup"><span data-stu-id="acd57-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="acd57-636">送信の成功した結果を表示するには待機します。</span><span class="sxs-lookup"><span data-stu-id="acd57-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="acd57-639">次の章では、特定の HoloLens です。</span><span class="sxs-lookup"><span data-stu-id="acd57-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="acd57-640">Power BI は現在使用できません没入型アプリケーションとして Windows 混合現実ポータル (Cliff 家とも呼ばれます) で、デスクトップ バージョンを実行することができますが、デスクトップ アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="acd57-640">Power BI is not currently availble as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="acd57-641">第 16 章 – HoloLens でデータを Power BI の表示</span><span class="sxs-lookup"><span data-stu-id="acd57-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="acd57-642">HoloLens へログイン、 **Microsoft Store**アプリケーションの一覧で、アイコンをタップします。</span><span class="sxs-lookup"><span data-stu-id="acd57-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="acd57-644">検索し、ダウンロード、 **Power BI**アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="acd57-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="acd57-646">開始**Power BI**アプリケーションの一覧から。</span><span class="sxs-lookup"><span data-stu-id="acd57-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="acd57-647">**Power BI**にログインするよう求められます可能性があります、 **Microsoft 365 アカウント**します。</span><span class="sxs-lookup"><span data-stu-id="acd57-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="acd57-648">1 回、アプリ内次の図に示すように、ワークスペースが既定で表示します。</span><span class="sxs-lookup"><span data-stu-id="acd57-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="acd57-649">発生しない場合は、単にウィンドウの左側にあるワークスペース アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="acd57-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="acd57-651">IoT Hub のアプリケーションが完了しました</span><span class="sxs-lookup"><span data-stu-id="acd57-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="acd57-652">これで、シミュレートされた仮想マシンのエッジ デバイスで、IoT Hub サービスを作成しました。</span><span class="sxs-lookup"><span data-stu-id="acd57-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="acd57-653">デバイスは、machine learning のモデルを Power BI に読み取られ、Microsoft HoloLens 内で視覚化する Azure Function App によって容易になります、Azure Table Service の結果を通信できます。</span><span class="sxs-lookup"><span data-stu-id="acd57-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="acd57-655">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="acd57-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="acd57-656">手順 1</span><span class="sxs-lookup"><span data-stu-id="acd57-656">Exercise 1</span></span>

<span data-ttu-id="acd57-657">テーブルに格納されているメッセージの構造を展開し、グラフとして表示します。</span><span class="sxs-lookup"><span data-stu-id="acd57-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="acd57-658">多くのデータを収集し、後で表示される、同じテーブルに保存する場合があります。</span><span class="sxs-lookup"><span data-stu-id="acd57-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="acd57-659">手順 2</span><span class="sxs-lookup"><span data-stu-id="acd57-659">Exercise 2</span></span>

<span data-ttu-id="acd57-660">追加で作成するため、分析するカメラでイメージをキャプチャできます、IoT ボード上に展開する「カメラ キャプチャ」モジュール。</span><span class="sxs-lookup"><span data-stu-id="acd57-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
