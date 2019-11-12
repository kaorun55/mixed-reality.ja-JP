---
title: Azure Speech Services チュートリアル-3. Azure Cognitive Services speech translation コンポーネントの追加
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 490b9f6142208a190748b6d76c57be493172c1e5
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913201"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="8534b-105">3. Azure Cognitive Services speech 変換コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="8534b-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="8534b-106">このチュートリアルでは、プロジェクトの Azure Cognitive Services Speech Translation コンポーネントについて説明し、3つの異なる言語に翻訳します。</span><span class="sxs-lookup"><span data-stu-id="8534b-106">In this tutorial, we learn about the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span>

## <a name="instructions"></a><span data-ttu-id="8534b-107">手順</span><span class="sxs-lookup"><span data-stu-id="8534b-107">Instructions</span></span>

1. <span data-ttu-id="8534b-108">階層内の Lunarcom_Base オブジェクトを選択し、[インスペクター] パネルの [コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8534b-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="8534b-109">[Lunarcom Translation レコグナイザー] を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="8534b-109">Search for and select Lunarcom Translation Recognizer.</span></span>

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    <span data-ttu-id="8534b-111">オフラインモードシミュレーターを無効にします。</span><span class="sxs-lookup"><span data-stu-id="8534b-111">Disable the offline mode simulator.</span></span>

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    ><span data-ttu-id="8534b-113">前の図に示すように、オフラインモードシミュレーターが無効になっていることを確認してから、Speech SDK 変換プログラムをテストしてください。</span><span class="sxs-lookup"><span data-stu-id="8534b-113">Before moving on, ensure the offline mode simulator is disabled, as shown in the image above, before testing the Speech-SDK translator.</span></span> <span data-ttu-id="8534b-114">を翻訳するには、インターネットに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8534b-114">In order to translate, you must be connected to the internet.</span></span>

2. <span data-ttu-id="8534b-115">[Lunarcom 変換認識エンジン] のドロップダウンをクリックし、変換する言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="8534b-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span></span>

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="8534b-117">次に、アプリケーションを実行し、[サテライト] ボタンをクリックして変換をテストし、読み上げを開始します。</span><span class="sxs-lookup"><span data-stu-id="8534b-117">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="8534b-118">[サテライト] ボタンをもう一度クリックして、認識を停止します。</span><span class="sxs-lookup"><span data-stu-id="8534b-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="8534b-119">シーンがどのように表示されるかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8534b-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="8534b-120">[ターゲット言語] ドロップダウンの下にある言語を自由に変更し (上の図を参照)、他の言語への翻訳を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="8534b-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

    <span data-ttu-id="8534b-121">シーンの外観の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8534b-121">Below is an example of what your scene should look like:</span></span>

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="8534b-123">結論</span><span class="sxs-lookup"><span data-stu-id="8534b-123">Congratulations</span></span>

<span data-ttu-id="8534b-124">これで、お客様のプロジェクトで、話す単語を複数の異なる言語に変換できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8534b-124">Now your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="8534b-125">自由に言語を自由に試して、翻訳の精度をテストしてください。</span><span class="sxs-lookup"><span data-stu-id="8534b-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span>

[<span data-ttu-id="8534b-126">次のチュートリアル: 4. インテントと自然言語の理解の設定</span><span class="sxs-lookup"><span data-stu-id="8534b-126">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
