---
title: MR Learning SpeechSDK モジュール-音声認識と議事録
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: b13b22fcdce2e7fa1319d241302b764f457aabba
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485604"
---
# <a name="2----adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="00fe6-104">2.   音声からテキストへのローカル翻訳のオフラインモードの追加</span><span class="sxs-lookup"><span data-stu-id="00fe6-104">2.    Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="00fe6-105">このチュートリアルでは、Azure サービスに接続できない場合に、ローカルの音声からテキストへの変換を実行できるオフラインモードを追加します。</span><span class="sxs-lookup"><span data-stu-id="00fe6-105">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="00fe6-106">また、切断された状態を*シミュレート*します。</span><span class="sxs-lookup"><span data-stu-id="00fe6-106">We will also *simulate* a disconnected state.</span></span>

## <a name="instructions"></a><span data-ttu-id="00fe6-107">手順</span><span class="sxs-lookup"><span data-stu-id="00fe6-107">Instructions</span></span>

1. <span data-ttu-id="00fe6-108">階層内の Lunarcom_Base オブジェクトを選択し、[インスペクター] パネルの [コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00fe6-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the Inspector panel.</span></span> <span data-ttu-id="00fe6-109">Lunarcom のオフライン認識を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="00fe6-109">Search for and select the Lunarcom Offline Recognition.</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. <span data-ttu-id="00fe6-111">LunarcomOfflineRecognizer のドロップダウンをクリックし、[有効] を選択します。</span><span class="sxs-lookup"><span data-stu-id="00fe6-111">Click the drop-down in the LunarcomOfflineRecognizer, and select Enabled.</span></span> <span data-ttu-id="00fe6-112">このプログラムでは、ユーザーのように動作するプロジェクトは接続されていません。</span><span class="sxs-lookup"><span data-stu-id="00fe6-112">This programs the project to act like the user doesn't have a connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="00fe6-114">次に、Unity エディターで play を押し、テストします。</span><span class="sxs-lookup"><span data-stu-id="00fe6-114">Now, press play in Unity Editor, and test it.</span></span> <span data-ttu-id="00fe6-115">シーンの左下隅にあるマイクを押し、読み上げを開始します。</span><span class="sxs-lookup"><span data-stu-id="00fe6-115">Press the microphone in the bottom left hand corner in the scene, and begin speaking.</span></span> 

> [!NOTE]
> <span data-ttu-id="00fe6-116">オフラインになっているため、復帰ワードの機能が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="00fe6-116">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="00fe6-117">オフライン時に音声を認識させるには、マイクを物理的にクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="00fe6-117">You'll have to physically click the microphone every time you wish to have your speech recognized when offline.</span></span> 

<span data-ttu-id="00fe6-118">シーンの外観の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="00fe6-118">Below is an example of what your scene could look like.</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="00fe6-120">結論</span><span class="sxs-lookup"><span data-stu-id="00fe6-120">Congratulations</span></span>

<span data-ttu-id="00fe6-121">オフラインモードが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="00fe6-121">The offline mode has been enabled.</span></span> <span data-ttu-id="00fe6-122">これで、オフラインになっても、speech SDK を使用してプロジェクトを操作できます。</span><span class="sxs-lookup"><span data-stu-id="00fe6-122">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span> 


[<span data-ttu-id="00fe6-123">次のチュートリアル:3.Azure Cognitive Services speech translation コンポーネントの追加</span><span class="sxs-lookup"><span data-stu-id="00fe6-123">Next Tutorial: 3.  Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)

