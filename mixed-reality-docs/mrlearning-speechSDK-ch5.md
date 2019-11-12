---
title: MR Learning SpeechSDK モジュール-音声認識と議事録
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: da485f167ef3902dd75adf8da8181504fbc6c6df
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913166"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a><span data-ttu-id="3b559-104">Speech SDK Learning モジュール-音声コマンドを使用したロケットランチャーコントロール</span><span class="sxs-lookup"><span data-stu-id="3b559-104">Speech SDK Learning Module - Rocket Launcher Control Using Speech Commands</span></span>

<span data-ttu-id="3b559-105">このレッスンでは、Azure Speech Service のインテント機能を使用して、音声の意図を理解します。</span><span class="sxs-lookup"><span data-stu-id="3b559-105">In this lesson, we will be using Azure Speech Service's Intent feature to understand the intent of the speech.</span></span> <span data-ttu-id="3b559-106">検出された音声のインテントを音声コマンドとして使用して、ロケットランチャーを制御します。</span><span class="sxs-lookup"><span data-stu-id="3b559-106">We will be using the detected intent of speech as the voice commands to control the rocket launcher.</span></span> <span data-ttu-id="3b559-107">このレッスンでは、ロケットランチャーアセットをインポートします。検出されたインテント音声コマンドを事前に定義されたコントロールボタンにインターフェイスして、ロケットを制御します。</span><span class="sxs-lookup"><span data-stu-id="3b559-107">During this lesson, we will be importing the Rocket Launcher asset and We will interface the detected intent voice commands to predefined control buttons to control the rocket.</span></span>

## <a name="objectives"></a><span data-ttu-id="3b559-108">目標</span><span class="sxs-lookup"><span data-stu-id="3b559-108">Objectives</span></span>

- <span data-ttu-id="3b559-109">音声の目的を音声コマンドとして接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3b559-109">Learn how to connect speech intent as voice commands.</span></span>
- <span data-ttu-id="3b559-110">音声合成の音声コマンドを、ロケットコントロール入力コマンドとして使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3b559-110">Learn how to use speech intent voice commands as rocket control input commands.</span></span>

## <a name="instructions"></a><span data-ttu-id="3b559-111">手順</span><span class="sxs-lookup"><span data-stu-id="3b559-111">Instructions</span></span>

1. <span data-ttu-id="3b559-112">このチュートリアルでは、"BaseModule" 資産を使用して、ロケットランチャーと音声コマンドを統合します。</span><span class="sxs-lookup"><span data-stu-id="3b559-112">In this tutorial, we will be using a "BaseModule" asset to integrate rocket launcher with the speech commands.</span></span> <span data-ttu-id="3b559-113">そのためには、プロジェクトにアセットをインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b559-113">For that, we need to import the asset into our project.</span></span> <span data-ttu-id="3b559-114">この[リンク](https://github.com/Developer-OI/MixedRealityLearning/releases/download/1.2.1/BaseModuleAssets-1.2.1.unitypackage)を使用して、"ロケットランチャー" 資産をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="3b559-114">You can download the "Rocket Launcher" asset using this [link](https://github.com/Developer-OI/MixedRealityLearning/releases/download/1.2.1/BaseModuleAssets-1.2.1.unitypackage).</span></span>

2. <span data-ttu-id="3b559-115">アセットをインポートするには、[> アセット]、[パッケージのインポート]、[カスタム > パッケージ >] の順に選択し、ダウンロードしたファイルに移動して、[インポート] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b559-115">To import the asset, please go to assets->Import package->Custom package-> navigate to the downloaded file and click import.</span></span>

    ![module4chapter5step1](images/module4chapter5step1.PNG)

3. <span data-ttu-id="3b559-117">"Base Module Assets" 資産をインポートした後、"Base Module Assets" フォルダー内を移動し > Prefabs-> [ロケット Launcher_Complete] を選択し、既存のシーン階層にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="3b559-117">After importing the  "Base Module Assets" asset, navigate inside the "Base Module Assets" folder->Prefabs-> Select "Rocket Launcher_Complete", and then drag and drop it into the existing scene Hierarchy.</span></span>

    ![module4chapter5step2](images/module4chapter5step2.PNG)

4. <span data-ttu-id="3b559-119">次に、前のレッスンの[レッスン](mrlearning-speechSDK-ch4.md)で扱った "ロケットランチャー" を LUIS プロジェクトと統合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b559-119">Now we need to integrate our "Rocket Launcher" with our LUIS project that we worked in our previous lesson [lesson](mrlearning-speechSDK-ch4.md).</span></span> <span data-ttu-id="3b559-120">そのためには、階層で "ロケット Launcher_Complete" prefab を展開し、"LaunchRoundButton"、"ResetRoundButton"、および "Placement ヒント" の各ボタンを見つけます。</span><span class="sxs-lookup"><span data-stu-id="3b559-120">For that, expand the "Rocket Launcher_Complete" prefab in the hierarchy and find the "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons.</span></span>

    ![module4chapter5step3](images/module4chapter5step3.PNG)

5. <span data-ttu-id="3b559-122">"LaunchRoundButton" を選択し、[インスペクター] パネルで "対話型" に移動して、"OnClick ()" イベントの下にある "LunarModule" prefab をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="3b559-122">Select "LaunchRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="3b559-123">次に、[関数] ドロップダウンを選択し、"LunarModule" を選択します。次に、"StartThruster ()" 関数に移動して選択します。</span><span class="sxs-lookup"><span data-stu-id="3b559-123">Then, select the function drop down and select " LunarModule" and then navigate to "StartThruster()" function and select it.</span></span>

    ![module4chapter5step 3.0](images/module4chapter5step3.0.PNG)

    ![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. <span data-ttu-id="3b559-126">"ResetRoundButton" を選択し、[インスペクター] パネルで "対話型" に移動して、"OnClick ()" イベントの下にある "LunarModule" prefab をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="3b559-126">Select "ResetRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="3b559-127">次に、[関数] ドロップダウンを選択し、"LunarModule" を選択します。次に、"resetModule ()" 関数に移動して選択します。</span><span class="sxs-lookup"><span data-stu-id="3b559-127">Then, select the function drop down and select " LunarModule" and then navigate to "resetModule()" function and select it.</span></span>

    ![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. <span data-ttu-id="3b559-129">[配置ヒント] を選択し、[インスペクター] パネルで "対話型" に移動して、"OnClick ()" イベントの下にある "LunarModule" prefab をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="3b559-129">Select "Placement Hints" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="3b559-130">次に、[関数] ドロップダウンを選択し、"LunarModule" を選択します。次に、"TogglePlacementHints" 関数に移動し、[ToggleGameOBjects ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b559-130">Then, select the function drop down and select " LunarModule" and then navigate to "TogglePlacementHints" function and select ToggleGameOBjects().</span></span>

    ![module4chapter5step3c](images/module4chapter5step3c.PNG)

8. <span data-ttu-id="3b559-132">次に、階層内の Lunarcom_Completed prefab を選択し、"LaunchRoundButton"、"ResetRoundButton"、および "Placement ヒント" の各ボタンをそれぞれの場所にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="3b559-132">Next, Select the Lunarcom_Completed prefab in Hierarchy and navigate to "Lunarcom Intent Recognizer" script in Inspector and then drag and drop  "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons to their respective places.</span></span>

    ![module4chapter5step4](images/module4chapter5step4.PNG)

9. <span data-ttu-id="3b559-134">Unity エディターの [play] ボタンをクリックし、[ロケット] ボタンをクリックして、[utter] ボタンをクリックします。「プッシュボタンを押す」、「配置ヒントを表示する」、「rest ボタンを押す」、またはロケットランチャーに対する起動、リセット、またはヒントの要求に関連するその他の語句を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b559-134">Press the play button in Unity Editor and click on the "Rocket" button and utter the phrases like "Push rocket launch button","show me a placement hint", "press the rest button" or any other phrases related to launch, reset or hint's request for the rocket launcher.</span></span>

    ![module4chapter5step5a](images/module4chapter5step5a.PNG)

    ![module4chapter5step5b](images/module4chapter5step5b.PNG)

    ![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a><span data-ttu-id="3b559-138">結論</span><span class="sxs-lookup"><span data-stu-id="3b559-138">Congratulations</span></span>

<span data-ttu-id="3b559-139">このレッスンでは、AI による音声認識コマンドを音声コマンドに接続して、入力方式として使用する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="3b559-139">In this lesson, we learned how to connect the AI-powered speech commands to voice commands to use it as an input method.</span></span> <span data-ttu-id="3b559-140">これで、プログラムは、スピーカーの意図を音声コマンドとして使用して、ロケットランチャーの入力を提供できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="3b559-140">Now our program can use the speakers intent as voice commands to give inputs for the rocket launcher.</span></span>
