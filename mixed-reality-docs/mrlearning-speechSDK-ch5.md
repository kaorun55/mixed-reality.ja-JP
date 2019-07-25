---
title: MR Learning SpeechSDK モジュール-音声認識と議事録
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: fc65dccfcbc181af0c0b321374c721797e120e5d
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460337"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a><span data-ttu-id="03b32-104">Speech SDK Learning モジュール-音声コマンドを使用したロケットランチャーコントロール</span><span class="sxs-lookup"><span data-stu-id="03b32-104">Speech SDK Learning Module - Rocket Launcher Control Using Speech Commands</span></span>

<span data-ttu-id="03b32-105">このレッスンでは、Azure Speech Service のインテント機能を使用して、音声の意図を理解します。</span><span class="sxs-lookup"><span data-stu-id="03b32-105">In this lesson, we will be using Azure Speech Service's Intent feature to understand the intent of the speech.</span></span> <span data-ttu-id="03b32-106">検出された音声のインテントを音声コマンドとして使用して、ロケットランチャーを制御します。</span><span class="sxs-lookup"><span data-stu-id="03b32-106">We will be using the detected intent of speech as the voice commands to control the rocket launcher.</span></span> <span data-ttu-id="03b32-107">このレッスンでは、ロケットランチャーアセットをインポートします。検出されたインテント音声コマンドを事前に定義されたコントロールボタンにインターフェイスして、ロケットを制御します。</span><span class="sxs-lookup"><span data-stu-id="03b32-107">During this lesson, we will be importing the Rocket Launcher asset and We will interface the detected intent voice commands to predefined control buttons to control the rocket.</span></span> 

## <a name="objectives"></a><span data-ttu-id="03b32-108">目的</span><span class="sxs-lookup"><span data-stu-id="03b32-108">Objectives</span></span>

- <span data-ttu-id="03b32-109">音声の目的を音声コマンドとして接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="03b32-109">Learn how to connect speech intent as voice commands.</span></span>
- <span data-ttu-id="03b32-110">音声合成の音声コマンドを、ロケットコントロール入力コマンドとして使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="03b32-110">Learn how to use speech intent voice commands as rocket control input commands.</span></span>

## <a name="instructions"></a><span data-ttu-id="03b32-111">手順</span><span class="sxs-lookup"><span data-stu-id="03b32-111">Instructions</span></span>
1. <span data-ttu-id="03b32-112">このチュートリアルでは、"BaseModule" 資産を使用して、ロケットランチャーと音声コマンドを統合します。</span><span class="sxs-lookup"><span data-stu-id="03b32-112">In this tutorial, we will be using a "BaseModule" asset to integrate rocket launcher with the speech commands.</span></span> <span data-ttu-id="03b32-113">そのためには、プロジェクトにアセットをインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="03b32-113">For that, we need to import the asset into our project.</span></span> <span data-ttu-id="03b32-114">このリンクを使用して、"ロケットランチャー" 資産をダウンロードできます (リンクを添付します)。</span><span class="sxs-lookup"><span data-stu-id="03b32-114">You can download the "Rocket Launcher" asset using this link (Attach the link).</span></span> 

2. <span data-ttu-id="03b32-115">アセットをインポートするには、[> アセット]、[パッケージのインポート]、[カスタム > パッケージ >] の順に選択し、ダウンロードしたファイルに移動して、[インポート] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="03b32-115">To import the asset, please go to assets->Import package->Custom package-> navigate to the downloaded file and click import.</span></span>

![module4chapter5step1](images/module4chapter5step1.PNG)

3. <span data-ttu-id="03b32-117">"ロケットランチャー" 資産をインポートした後、"ロケットランチャー" フォルダー内を移動します。 > Prefabs-> [ロケット Launcher_Complete] を選択し、既存のシーン階層にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="03b32-117">After importing the "Rocket Launcher" asset, navigate inside the "Rocket Launcher" folder->Prefabs-> Select "Rocket Launcher_Complete", and then drag and drop it into the existing scene Hierarchy.</span></span>

![module4chapter5step2](images/module4chapter5step2.PNG)

4. <span data-ttu-id="03b32-119">ここで、前のレッスンで作業した "ロケットランチャー" を LUIS プロジェクトと統合する必要があります (lesson4 のリンク)。</span><span class="sxs-lookup"><span data-stu-id="03b32-119">Now we need to integrate our "Rocket Launcher" with our LUIS project that we worked in our previous lesson (link for lesson4).</span></span> <span data-ttu-id="03b32-120">そのためには、階層の "ロケット Launcher_Complete" prefab を展開し、"LaunchRoundButton"、"ResetRoundButton"、および "Placement ヒント" の各ボタンを見つけます。</span><span class="sxs-lookup"><span data-stu-id="03b32-120">For that, expand the "Rocket Launcher_Complete" prefab in the hierarchy and find the "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons.</span></span>

![module4chapter5step3](images/module4chapter5step3.PNG)

5. <span data-ttu-id="03b32-122">"LaunchRoundButton" を選択し、[インスペクター] パネルで "対話型" に移動して、"OnClick ()" イベントの下にある "LunarModule" prefab をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="03b32-122">Select "LaunchRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="03b32-123">次に、[関数] ドロップダウンを選択し、"LunarModule" を選択します。次に、"StartThruster ()" 関数に移動して選択します。</span><span class="sxs-lookup"><span data-stu-id="03b32-123">Then, select the function drop down and select " LunarModule" and then navigate to "StartThruster()" function and select it.</span></span>

![module4chapter5step 3.0](images/module4chapter5step3.0.PNG)

![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. <span data-ttu-id="03b32-126">"ResetRoundButton" を選択し、[インスペクター] パネルで "対話型" に移動して、"OnClick ()" イベントの下にある "LunarModule" prefab をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="03b32-126">Select "ResetRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="03b32-127">次に、[関数] ドロップダウンを選択し、"LunarModule" を選択します。次に、"resetModule ()" 関数に移動して選択します。</span><span class="sxs-lookup"><span data-stu-id="03b32-127">Then, select the function drop down and select " LunarModule" and then navigate to "resetModule()" function and select it.</span></span>

![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. <span data-ttu-id="03b32-129">[配置ヒント] を選択し、[インスペクター] パネルで "対話型" に移動して、"OnClick ()" イベントの下にある "LunarModule" prefab をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="03b32-129">Select "Placement Hints" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="03b32-130">次に、[関数] ドロップダウンを選択し、"LunarModule" を選択します。次に、"TogglePlacementHints" 関数に移動し、[ToggleGameOBjects ()] を選択します。</span><span class="sxs-lookup"><span data-stu-id="03b32-130">Then, select the function drop down and select " LunarModule" and then navigate to "TogglePlacementHints" function and select ToggleGameOBjects().</span></span>

![module4chapter5step3c](images/module4chapter5step3c.PNG)

8.  <span data-ttu-id="03b32-132">次に、[Lunarcom_Completed prefab in Hierarchy] を選択し、[LaunchRoundButton]、[ResetRoundButton]、および [Placement ヒント] の各ボタンをそれぞれの場所にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="03b32-132">Next, Select the Lunarcom_Completed prefab in Hierarchy and navigate to "Lunarcom Intent Recognizer" script in Inspector and then drag and drop  "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons to their respective places.</span></span>

![module4chapter5step4](images/module4chapter5step4.PNG)

9. <span data-ttu-id="03b32-134">Unity エディターの [play] ボタンをクリックし、[ロケット] ボタンをクリックして、[utter] ボタンをクリックします。「プッシュボタンを押す」、「配置ヒントを表示する」、「rest ボタンを押す」、またはロケットランチャーに対する起動、リセット、またはヒントの要求に関連するその他の語句を選択します。</span><span class="sxs-lookup"><span data-stu-id="03b32-134">Press the play button in Unity Editor and click on the "Rocket" button and utter the phrases like "Push rocket launch button","show me a placement hint", "press the rest button" or any other phrases related to launch, reset or hint's request for the rocket launcher.</span></span>

![module4chapter5step5a](images/module4chapter5step5a.PNG)

![module4chapter5step5b](images/module4chapter5step5b.PNG)

![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a><span data-ttu-id="03b32-138">結論</span><span class="sxs-lookup"><span data-stu-id="03b32-138">Congratulations</span></span>

<span data-ttu-id="03b32-139">このレッスンでは、AI による音声認識コマンドを音声コマンドに接続して、入力方式として使用する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="03b32-139">In this lesson, we learned how to connect the AI-powered speech commands to voice commands to use it as an input method.</span></span> <span data-ttu-id="03b32-140">これで、プログラムは、スピーカーの意図を音声コマンドとして使用して、ロケットランチャーの入力を提供できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="03b32-140">Now our program can use the speakers intent as voice commands to give inputs for the rocket launcher.</span></span>

