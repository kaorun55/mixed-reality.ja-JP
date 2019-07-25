---
title: MR Learning SpeechSDK モジュール-音声認識と議事録
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: e5d0919a69c9e6b0c4233d23bf6d370f3def6576
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460311"
---
# <a name="3----adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="eabc5-104">3.  Azure Cognitive Services speech translation コンポーネントの追加</span><span class="sxs-lookup"><span data-stu-id="eabc5-104">3.    Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="eabc5-105">このチュートリアルでは、プロジェクトの Azure Cognitive Services Speech Translation コンポーネントについて説明し、3つの異なる言語に翻訳します。</span><span class="sxs-lookup"><span data-stu-id="eabc5-105">In this tutorial, we learn aabout the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span> 

1. <span data-ttu-id="eabc5-106">階層内の Lunarcom_Base オブジェクトを選択し、[インスペクター] パネルの [コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eabc5-106">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="eabc5-107">LunarcomTranslationRecognizer を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="eabc5-107">Search for and select LunarcomTranslationRecognizer.</span></span>

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> <span data-ttu-id="eabc5-109">注:Speech SDK 変換プログラムをテストする前に、オフラインモードシミュレーターが無効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="eabc5-109">Note: Ensure the offline mode simulator is disabled before testing the Speech-SDK translator.</span></span> <span data-ttu-id="eabc5-110">を翻訳するには、インターネットに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="eabc5-110">In order to translate, you must be connected to the internet.</span></span> <span data-ttu-id="eabc5-111">この設定の場所については、下の画像を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eabc5-111">See image below on where to find this setting.</span></span> 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. <span data-ttu-id="eabc5-113">LunarcomTranslationRecognizer のドロップダウンをクリックし、翻訳する言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="eabc5-113">Click the drop-down in the LunarcomTranslationRecognizer, and select the language you would like to translate to.</span></span>

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="eabc5-115">次に、アプリケーションを実行し、[サテライト] ボタンをクリックして変換をテストし、読み上げを開始します。</span><span class="sxs-lookup"><span data-stu-id="eabc5-115">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="eabc5-116">[サテライト] ボタンをもう一度クリックして、認識を停止します。</span><span class="sxs-lookup"><span data-stu-id="eabc5-116">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="eabc5-117">シーンがどのように表示されるかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="eabc5-117">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="eabc5-118">[ターゲット言語] ドロップダウンの下にある言語を自由に変更し (上の図を参照)、他の言語への翻訳を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="eabc5-118">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

> <span data-ttu-id="eabc5-119">注:テストする前に、次の図に示すように、オフラインシミュレーターが無効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="eabc5-119">Note: Before testing, ensure that the offline simulator is disabled, as shown in the image below.</span></span>
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

<span data-ttu-id="eabc5-121">シーンの外観の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="eabc5-121">Below is an example of what your scene should look like:</span></span>

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="eabc5-123">結論</span><span class="sxs-lookup"><span data-stu-id="eabc5-123">Congratulations</span></span>

<span data-ttu-id="eabc5-124">これで、お客様のプロジェクトで、話す単語を複数の異なる言語に変換できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="eabc5-124">Now  your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="eabc5-125">自由に言語を自由に試して、翻訳の精度をテストしてください。</span><span class="sxs-lookup"><span data-stu-id="eabc5-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span> 

[<span data-ttu-id="eabc5-126">次のチュートリアル:4。インテントの設定と自然言語の理解</span><span class="sxs-lookup"><span data-stu-id="eabc5-126">Next tutorial: 4.  Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)

