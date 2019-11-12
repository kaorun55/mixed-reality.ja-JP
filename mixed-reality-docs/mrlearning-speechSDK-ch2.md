---
title: Azure Speech Services チュートリアル-2. 音声からテキストへのローカル翻訳のオフラインモードの追加
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 962d7d4750cf59fe56de4af9088c90e8ecd0aa16
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913207"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="0ec50-105">2. ローカルの音声テキスト翻訳のオフラインモードを追加する</span><span class="sxs-lookup"><span data-stu-id="0ec50-105">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="0ec50-106">このチュートリアルでは、Azure サービスに接続できない場合に、ローカルの音声からテキストへの変換を実行できるオフラインモードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0ec50-106">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="0ec50-107">また、切断された状態を*シミュレート*します。</span><span class="sxs-lookup"><span data-stu-id="0ec50-107">We will also *simulate* a disconnected state.</span></span>

## <a name="instructions"></a><span data-ttu-id="0ec50-108">手順</span><span class="sxs-lookup"><span data-stu-id="0ec50-108">Instructions</span></span>

1. <span data-ttu-id="0ec50-109">階層内の Lunarcom_Base オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="0ec50-109">Select the Lunarcom_Base object in the hierarchy.</span></span>

2. <span data-ttu-id="0ec50-110">[インスペクター] パネルの [コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ec50-110">Click Add Component in the Inspector panel.</span></span> <span data-ttu-id="0ec50-111">Lunarcom のオフライン認識を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="0ec50-111">Search for and select the Lunarcom Offline Recognition.</span></span>

    ![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

3. <span data-ttu-id="0ec50-113">LunarcomOfflineRecognizer のドロップダウンをクリックし、[有効] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ec50-113">Click the drop-down in the LunarcomOfflineRecognizer and select Enabled.</span></span> <span data-ttu-id="0ec50-114">このプログラムでは、ユーザーのように動作するプロジェクトは接続されていません。</span><span class="sxs-lookup"><span data-stu-id="0ec50-114">This programs the project to act like the user doesn't have a connection.</span></span>

    ![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

4. <span data-ttu-id="0ec50-116">Unity エディターで Play を押し、テストします。</span><span class="sxs-lookup"><span data-stu-id="0ec50-116">Press Play in Unity Editor, and test it.</span></span> <span data-ttu-id="0ec50-117">シーンの左下隅にあるマイクを押し、読み上げを開始します。</span><span class="sxs-lookup"><span data-stu-id="0ec50-117">Press the microphone in the bottom-left corner in the scene and begin speaking.</span></span>

    >[!NOTE]
    ><span data-ttu-id="0ec50-118">オフラインになっているため、復帰ワードの機能が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="0ec50-118">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="0ec50-119">オフライン時に音声を認識させるには、マイクを物理的にクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ec50-119">You'll need to physically click the microphone every time you wish to have your speech recognized when offline.</span></span>

    <span data-ttu-id="0ec50-120">シーンの外観の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0ec50-120">Below is an example of what your scene could look like.</span></span>

    ![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="0ec50-122">結論</span><span class="sxs-lookup"><span data-stu-id="0ec50-122">Congratulations</span></span>

<span data-ttu-id="0ec50-123">オフラインモードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="0ec50-123">The offline mode has been enabled.</span></span> <span data-ttu-id="0ec50-124">これで、オフラインになっても、speech SDK を使用してプロジェクトを操作できます。</span><span class="sxs-lookup"><span data-stu-id="0ec50-124">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span>

[<span data-ttu-id="0ec50-125">次のチュートリアル: 3. Azure Cognitive Services speech translation コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="0ec50-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
