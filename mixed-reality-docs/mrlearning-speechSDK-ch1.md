---
title: Azure Speech Services チュートリアル-1. 音声認識と議事録の統合と使用
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: defa33e56cfe4450a8d42855bd11dc23973dc401
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913442"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="377a7-105">1. 音声認識と議事録の統合と使用</span><span class="sxs-lookup"><span data-stu-id="377a7-105">1. Integrating and using speech recognition and transcription</span></span>

<span data-ttu-id="377a7-106">このチュートリアルでは、Azure Cognitive Services Speech SDK と HoloLens 2 の使用方法を紹介する Mixed Reality アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="377a7-106">This tutorial creates a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="377a7-107">このチュートリアルシリーズを終了すると、デバイスのマイクを使用して、音声をリアルタイムでテキストにしたり、音声を他の言語に翻訳したり、音声認識機能を活用して音声コマンドを理解したりすることができます。人工知能。</span><span class="sxs-lookup"><span data-stu-id="377a7-107">When finished with this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="377a7-108">目標</span><span class="sxs-lookup"><span data-stu-id="377a7-108">Objectives</span></span>

- <span data-ttu-id="377a7-109">Azure Speech SDK を HoloLens 2 アプリケーションに統合する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="377a7-109">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
- <span data-ttu-id="377a7-110">音声コマンドの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="377a7-110">Learn how to use voice commands</span></span>
- <span data-ttu-id="377a7-111">音声をテキストに変換する機能の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="377a7-111">Learn how to use speech-to-text capabilities</span></span>

## <a name="instructions"></a><span data-ttu-id="377a7-112">手順</span><span class="sxs-lookup"><span data-stu-id="377a7-112">Instructions</span></span>

### <a name="getting-started"></a><span data-ttu-id="377a7-113">作業の開始</span><span class="sxs-lookup"><span data-stu-id="377a7-113">Getting Started</span></span>

1. <span data-ttu-id="377a7-114">Unity を起動し、新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="377a7-114">Start Unity, and create a new project.</span></span> <span data-ttu-id="377a7-115">Project name Speech SDK Learning モジュールを入力します。</span><span class="sxs-lookup"><span data-stu-id="377a7-115">Enter the project name Speech SDK Learning Module.</span></span> <span data-ttu-id="377a7-116">プロジェクトを保存する場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="377a7-116">Choose a location for where to save your project.</span></span> <span data-ttu-id="377a7-117">次に、[プロジェクトの作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="377a7-117">Then click Create Project.</span></span>

    ![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

    >[!NOTE]
    ><span data-ttu-id="377a7-119">上の図に示すように、テンプレートが3D に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="377a7-119">Ensure that the template is set to 3D, as shown in the image above.</span></span>

2. <span data-ttu-id="377a7-120">[Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation パッケージバージョン 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)をダウンロードし、PC 上のフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="377a7-120">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation package version 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) and save it to a folder on your PC.</span></span> <span data-ttu-id="377a7-121">Unity プロジェクトにパッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="377a7-121">Import the package into your Unity project.</span></span> <span data-ttu-id="377a7-122">これを行う方法の詳細については、入門チュートリアルのレッスン2を参照してください[。プロジェクトと最初のアプリケーションを初期化して](mrlearning-base-ch1.md)います。</span><span class="sxs-lookup"><span data-stu-id="377a7-122">For detailed instructions on how to do this, please see the [Getting started tutorials - Lesson 2. Initializing your project and first application](mrlearning-base-ch1.md).</span></span>

3. <span data-ttu-id="377a7-123">Unity 資産パッケージ用の Azure [SPEECH SDK](https://aka.ms/csspeech/unitypackage)をダウンロードしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="377a7-123">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for the Unity asset package.</span></span> <span data-ttu-id="377a7-124">[アセット] をクリックし、[パッケージのインポート]、[カスタムパッケージ] の順に選択して、Speech SDK パッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="377a7-124">Import the Speech SDK package by clicking on Assets, selecting Import package, then selecting Custom Package.</span></span> <span data-ttu-id="377a7-125">先ほどダウンロードした Speech SDK パッケージを検索し、それを開いてインポートプロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="377a7-125">Find the Speech SDK package downloaded earlier, and open it to begin the importing process.</span></span>

    ![mrlearning-speech-ch1-1-step3a](images/mrlearning-speech-ch1-1-step3a.png)

    ![mrlearning-speech-ch1-1-step3b](images/mrlearning-speech-ch1-1-step3b.png)

4. <span data-ttu-id="377a7-128">次のポップアップウィンドウで [インポート] をクリックして、Speech SDK パッケージのインポートを開始します。</span><span class="sxs-lookup"><span data-stu-id="377a7-128">In the next pop-up window, click Import to begin importing the Speech SDK package.</span></span> <span data-ttu-id="377a7-129">次の図に示すように、すべての項目がオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="377a7-129">Ensure all items are checked as shown in the image below.</span></span>

    ![mrlearning-speech-ch1-1-step4](images/mrlearning-speech-ch1-1-step4.png)

5. <span data-ttu-id="377a7-131">Speech SDK モジュールアセットパックをダウンロードします。[このリンク](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2)をクリックして、Lunarcom パッケージとしても知られています。</span><span class="sxs-lookup"><span data-stu-id="377a7-131">Download the Speech SDK Module asset pack, also know as Lunarcom package by clicking on [this link](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2).</span></span> <span data-ttu-id="377a7-132">Lunarcom 資産パッケージは、このレッスンシリーズ用に開発された資産とスクリプトのコレクションであり、Azure の Speech SDK の実際の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="377a7-132">The Lunarcom asset package is a collection of assets and scripts developed for this lesson series to showcase a practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="377a7-133">これは、入門チュートリアルで開発した太陰暦モジュールのアセンブリエクスペリエンスに最終的にインターフェイスを提供する音声コマンドターミナルです[。レッスン 7.旧暦モジュールサンプルアプリケーションを作成する](mrlearning-base-ch6.md)。</span><span class="sxs-lookup"><span data-stu-id="377a7-133">It is a voice-command terminal that will ultimately interface with the lunar module assembly experience developed in the [Getting started tutorials - Lesson 7. Creating a Lunar Module sample application](mrlearning-base-ch6.md).</span></span>

6. <span data-ttu-id="377a7-134">Mixed Reality Toolkit と Speech SDK をインポートする場合と同様の手順に従って、Lunarcom 資産パッケージを Unity プロジェクトにインポートします。</span><span class="sxs-lookup"><span data-stu-id="377a7-134">Import the Lunarcom asset package into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>

7. <span data-ttu-id="377a7-135">Mixed Reality Toolkit (MRTK) を構成します。</span><span class="sxs-lookup"><span data-stu-id="377a7-135">Configure the Mixed Reality Toolkit (MRTK).</span></span>

    <span data-ttu-id="377a7-136">これを行うには、ウィンドウの上部にある [Mixed Reality Toolkit] パネルをクリックし、[シーンに追加] と [構成] を選択します。</span><span class="sxs-lookup"><span data-stu-id="377a7-136">To do this, click on the Mixed Reality Toolkit panel in the top of your window, and then select Add to Scene and Configure.</span></span>

    ![mrlearning-speech-ch1-1-step7a](images/mrlearning-speech-ch1-1-step7a.png)

    <span data-ttu-id="377a7-138">表示されるポップアップで、[DefaultHoloLens2ConfigurationProfile] を選択して、Mixed Reality Toolkit のアクティブなプロファイルにします。</span><span class="sxs-lookup"><span data-stu-id="377a7-138">In the popup that appears, select DefaultHoloLens2ConfigurationProfile to make it the Active Profile for the Mixed Reality Toolkit.</span></span>

    ![mrlearning-speech-ch1-1-step7b](images/mrlearning-speech-ch1-1-step7b.png)

8. <span data-ttu-id="377a7-140">これで、シーンに MRTK から複数の新しい項目が追加されました。</span><span class="sxs-lookup"><span data-stu-id="377a7-140">Your scene now has several new items in it from the MRTK.</span></span> <span data-ttu-id="377a7-141">[ファイル]、[名前を付けて保存] の順にクリックし、シーンに SpeechScene という名前を付けて、シーンを別の名前で保存します。</span><span class="sxs-lookup"><span data-stu-id="377a7-141">Save your scene under a different name by clicking on "file," then "save as" and name your scene SpeechScene.</span></span>

    >[!NOTE]
    ><span data-ttu-id="377a7-142">プロジェクトに MRTK を追加した後にシーンで Play を押すと、再生モードにならない場合は、Unity の再起動が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="377a7-142">If you press Play on your scene after you add the MRTK to your project, and it doesn't enter play mode, you might need to restart Unity.</span></span>

9. <span data-ttu-id="377a7-143">シーン階層で MixedRealityToolkit オブジェクトを選択した状態で、[インスペクター] パネルの [& のコピー] をクリックして [複製プロファイル] ポップアップを開きます。</span><span class="sxs-lookup"><span data-stu-id="377a7-143">With the MixedRealityToolkit object selected in your scene hierarchy, click Copy & Customize in the Inspector panel to open the Clone Profile popup.</span></span> <span data-ttu-id="377a7-144">[複製プロファイル] ポップアップで、カスタムプロファイルに適切な名前 (たとえば、Custom HoloLens2ConfigurationProfile) を入力し、[複製] をクリックしてカスタム構成プロファイルを作成し、アクティブなプロファイルとして設定します。</span><span class="sxs-lookup"><span data-stu-id="377a7-144">In the Clone Profile popup, enter a suitable name for your custom profile, for example, Custom HoloLens2ConfigurationProfile, and then click Clone to create your custom configuration profile and set it as the active profile.</span></span>

    ![mrlearning-speech-ch1-1-step9](images/mrlearning-speech-ch1-1-step9.png)

10. <span data-ttu-id="377a7-146">また、[インスペクター] パネル (階層で MixedRealityToolkit オブジェクトが選択された状態) で、[診断システムを有効にする] の右側のチェックボックスをオフにして、診断システムを無効にします。</span><span class="sxs-lookup"><span data-stu-id="377a7-146">Also in the Inspector panel (with the MixedRealityToolkit object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of Enable Diagnostics System.</span></span>

    ![mrlearning-speech-ch1-1-step10](images/mrlearning-speech-ch1-1-step10.png)

11. <span data-ttu-id="377a7-148">このチュートリアルでは、音声認識と議事録に入力音声コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="377a7-148">In this tutorial, we are using the input speech commands for speech recognition and transcription.</span></span> <span data-ttu-id="377a7-149">入力プロファイルを複製して、音声設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="377a7-149">Lets clone the input profile to make changes to speech settings.</span></span>

    <span data-ttu-id="377a7-150">シーン階層で MixedRealityToolkit オブジェクトを選択した状態で、[インスペクター] パネルの [小さい複製] ボタンをクリックして、[複製プロファイル] ポップアップを開きます。</span><span class="sxs-lookup"><span data-stu-id="377a7-150">With the MixedRealityToolkit object still selected in your scene hierarchy, click the small Clone button in the Inspector panel to open the Clone Profile popup.</span></span> <span data-ttu-id="377a7-151">[複製プロファイル] ポップアップで、カスタムプロファイルに適切な名前 (たとえば、Custom HoloLens2InputSystemProfile) を入力し、[複製] をクリックしてカスタム入力システムプロファイルを作成し、アクティブなプロファイルとして設定します。</span><span class="sxs-lookup"><span data-stu-id="377a7-151">In the Clone Profile popup, enter a suitable name for your custom profile, for example, Custom HoloLens2InputSystemProfile, and then click Clone to create your custom input system profile and set it as the active profile.</span></span>

    ![mrlearning-speech-ch1-1-step11](images/mrlearning-speech-ch1-1-step11.png)

12. <span data-ttu-id="377a7-153">入力プロファイルが複製されたら、Speech セクションを展開し、前の手順と同じプロセスに従って speech コマンドプロファイルを複製します。</span><span class="sxs-lookup"><span data-stu-id="377a7-153">Once the input profile is cloned, expand the Speech section and follow the same process as in the previous step to clone the speech commands profile.</span></span>

    ![mrlearning-speech-ch1-1-step12](images/mrlearning-speech-ch1-1-step12.png)

13. <span data-ttu-id="377a7-155">[音声] セクションで、[全般設定] に移動し、[開始動作] を [手動開始] に変更します。</span><span class="sxs-lookup"><span data-stu-id="377a7-155">Now under Speech section, go to General Settings and change Start Behavior to Manual Start.</span></span>

    ![mrlearning-speech-ch1-1-step13](images/mrlearning-speech-ch1-1-step13.png)

14. <span data-ttu-id="377a7-157">[プロジェクト] パネルで、[Lunarcom] フォルダーを展開し、Lunarcom_Base prefab をシーン階層にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="377a7-157">In the Project panel, expand the Lunarcom folder and drag the Lunarcom_Base prefab into your scene hierarchy.</span></span>

    ![mrlearning-speech-ch1-1-step14](images/mrlearning-speech-ch1-1-step14.png)

15. <span data-ttu-id="377a7-159">階層内の Lunarcom_Base オブジェクトを選択し、位置が x = 0、y = 0、z = 0 に設定されていること、および x = 0、y = 0、z = 0 に設定された回転を確認します。</span><span class="sxs-lookup"><span data-stu-id="377a7-159">Select the Lunarcom_Base object in your hierarchy, and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="377a7-160">Scale を read x = 0.008、y = 0.008、および z = 0.01 に設定します。</span><span class="sxs-lookup"><span data-stu-id="377a7-160">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

    ![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. <span data-ttu-id="377a7-162">[コンポーネントの追加] をクリックし、[Lunarcom コントローラー] を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="377a7-162">Click Add Component, and search for and select Lunarcom Controller.</span></span> <span data-ttu-id="377a7-163">このスクリプトは、手順 6. でインポートした Lunarcom アセットパックに含まれています。</span><span class="sxs-lookup"><span data-stu-id="377a7-163">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

    ![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. <span data-ttu-id="377a7-165">アプリケーションを Azure Cognitive Services に接続するには、Speech サービスのサブスクリプションキー (API キーとも呼ばれます) を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="377a7-165">To connect our application to Azure Cognitive Services, you must enter a subscription key (also known as an API Key), for the Speech Service.</span></span> <span data-ttu-id="377a7-166">無料のサブスクリプションキーを取得するには、[こちら](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="377a7-166">Follow the instructions at [here](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="377a7-167">サブスクリプションキーを取得したら、次の図に示すように、[インスペクター] パネルの [LunarcomController] コンポーネントの [Speech Service API キー] フィールドに入力します。</span><span class="sxs-lookup"><span data-stu-id="377a7-167">Once you obtain the subscription key, enter it into the Speech Service API Key field of the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

18. <span data-ttu-id="377a7-168">[インスペクター] パネルの [LunarcomController] コンポーネントの [Speech Service Region] フィールドに、サブスクリプションキーにサインアップしたときに選択したリージョンを入力します。</span><span class="sxs-lookup"><span data-stu-id="377a7-168">Enter the Region that you chose when you signed up for the subscription key into the Speech Service Region field of the LunarcomController component in the Inspector panel.</span></span> <span data-ttu-id="377a7-169">たとえば、"westus" という地域では "米国西部" と入力します。</span><span class="sxs-lookup"><span data-stu-id="377a7-169">For example, for the region West US type in "westus".</span></span>

    ![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. <span data-ttu-id="377a7-171">階層で、左側の矢印をクリックして Lunarcom_Base オブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="377a7-171">In your hierarchy, expand the Lunarcom_Base object by clicking the arrow to the left of it.</span></span> <span data-ttu-id="377a7-172">その後、次の図に示すように、子オブジェクト "ターミナル" に対して同じ操作を行います。</span><span class="sxs-lookup"><span data-stu-id="377a7-172">Then do the same for its child object, "Terminal, as shown in the image below.</span></span>

20. <span data-ttu-id="377a7-173">Lunarcom_Base を選択した状態で、次の図に示すように、階層の Lunarcom テキストをクリックして、[インスペクター] パネルの LunarcomController コンポーネントの出力テキストスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="377a7-173">While Lunarcom_Base is selected, click and drag Lunarcom Text from the hierarchy to the Output Text slot in the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

21. <span data-ttu-id="377a7-174">ターミナルオブジェクトをターミナルスロットに、接続光オブジェクトを接続ライトコントローラースロットに対して同じ操作を行います。</span><span class="sxs-lookup"><span data-stu-id="377a7-174">Do the same thing with the Terminal object into the Terminal slot and the Connection Light object to the Connection Light Controller slot.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. <span data-ttu-id="377a7-176">[インスペクター] パネルの LunarcomController スクリプトの [Lunarcom ボタン] セクションの横にある矢印をクリックし、サイズを3に変更します。</span><span class="sxs-lookup"><span data-stu-id="377a7-176">Click the arrow next to the Lunarcom Buttons section of the LunarcomController script in the Inspector panel, and change the size to 3.</span></span> <span data-ttu-id="377a7-177">Enter キーを押すか、戻ります。</span><span class="sxs-lookup"><span data-stu-id="377a7-177">Press Enter or Return.</span></span> <span data-ttu-id="377a7-178">これにより、3つの新しい要素フィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="377a7-178">This causes three new Element fields to appear.</span></span>

    ![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. <span data-ttu-id="377a7-180">[Lunarcom] ボタンを展開します。このボタンの横にある矢印をクリックし、上記と同じプロセスを使用して、Mic、衛星、およびロケットの各オブジェクトを、次のように、それぞれの LunarcomController コンポーネントの要素0、1、および2にドラッグします。インスペクターパネル。</span><span class="sxs-lookup"><span data-stu-id="377a7-180">Expand the Lunarcom Buttons by clicking the arrow next to it in your hierarchy, and using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references, respectively, in the LunarcomController component in the Inspector panel.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. <span data-ttu-id="377a7-182">階層内の Lunarcom_Base のオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="377a7-182">Select the Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="377a7-183">[インスペクター] パネルの [コンポーネントの追加] をクリックし、[Lunarcom Speech レコグナイザー] を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="377a7-183">Click Add Component in the inspector panel and search for and select Lunarcom Speech Recognizer.</span></span> <span data-ttu-id="377a7-184">同じ手順を繰り返して、Lunarcom Wake Word レコグナイザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="377a7-184">Repeat the same steps to add Lunarcom Wake Word Recognizer.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. <span data-ttu-id="377a7-186">Wake Word スロットで、「Activate Terminal」と入力します。</span><span class="sxs-lookup"><span data-stu-id="377a7-186">In the Wake Word slot, type in Activate Terminal.</span></span> <span data-ttu-id="377a7-187">[Word のスロットを閉じる] に「ターミナルを閉じる」と入力します。</span><span class="sxs-lookup"><span data-stu-id="377a7-187">In the Dismiss Word slot, type Dismiss Terminal.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a><span data-ttu-id="377a7-189">デバイスへのアプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="377a7-189">Build your application to your device</span></span>

1. <span data-ttu-id="377a7-190">[ファイル > ビルドの設定] に移動して、[ビルドの設定] ウィンドウを再び開きます。</span><span class="sxs-lookup"><span data-stu-id="377a7-190">Open the build settings window again by going to File>Build Settings.</span></span>

    ![images/mrlearning-ch1-2-ステップ1](images/mrlearning-speach-ch1-2-step1.jpg)

2. <span data-ttu-id="377a7-192">[開いているシーンの追加] ボタンをクリックして、試したいシーンが [ビルド内のシーン] リストに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="377a7-192">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>

3. <span data-ttu-id="377a7-193">[プレーヤーの設定] ボタンをクリックし、[発行の設定] にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="377a7-193">Press the Player Settings button and go to Publishing Settings.</span></span> <span data-ttu-id="377a7-194">[機能] で、[インターネット]、[インターネットクライアントサーバー]、[プライベートネットワーククライアントサーバー]、[マイクと空間認識] を有効にします。</span><span class="sxs-lookup"><span data-stu-id="377a7-194">Under Capabilities, enable: Internet, Internet Client Server, Private Network Client Server, Microphone and Spatial Perception.</span></span>

4. <span data-ttu-id="377a7-195">同じプレーヤー設定で、XR settings にアクセスして、でサポートされている仮想現実を選択します。</span><span class="sxs-lookup"><span data-stu-id="377a7-195">In the same Player Settings, go to XR settings  and select the Virtual Reality Supported to ON.</span></span>

5. <span data-ttu-id="377a7-196">[ビルド] ボタンを押して、ビルド プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="377a7-196">Press the Build button to begin the build process.</span></span>

    ![mrlearning-ch1-2-手順5](images/mrlearning-speach-ch1-2-step5.jpg)

6. <span data-ttu-id="377a7-198">アプリケーション用の新しいフォルダーを作成して、名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="377a7-198">Create and name a new folder for your application.</span></span> <span data-ttu-id="377a7-199">下の図では、アプリケーションを含めるために [App] という名前のフォルダーが作成されています。</span><span class="sxs-lookup"><span data-stu-id="377a7-199">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="377a7-200">[フォルダーの選択] をクリックして、新しく作成したフォルダーへのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="377a7-200">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="377a7-201">ビルドが完了したら、Unity の [ビルド設定] ウィンドウを閉じてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="377a7-201">After the build has completed, you may close the "Build Settings" window in Unity.</span></span>

    ![mrlearning-ch1-2-手順6](images/mrlearning-speach-ch1-2-step6.jpg)

    >[!NOTE]
    ><span data-ttu-id="377a7-203">ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。</span><span class="sxs-lookup"><span data-stu-id="377a7-203">If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="377a7-204">"エラー: CS0246 = 型または名前空間名" XX "が見つかりませんでした (using ディレクティブまたはアセンブリ参照がないことを確認してください)" というエラーが表示された場合は、 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)のインストールが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="377a7-204">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", then you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span></span>

7. <span data-ttu-id="377a7-205">ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="377a7-205">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="377a7-206">".Sln" ソリューションファイルをダブルクリックして、Visual Studio でソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="377a7-206">Double click on the “.sln” solution file to open the solution file in Visual Studio.</span></span>

    >[!NOTE]
    ><span data-ttu-id="377a7-207">必ず、新しく作成したフォルダー (つまり、前の手順で名前付け規則に従っている場合は、[App] フォルダー) を開いてください。そのフォルダーの外部に同じような名前の .sln ファイルがあり、ビルド フォルダー内の .sln ファイルと混同してはならないためです。</span><span class="sxs-lookup"><span data-stu-id="377a7-207">Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

    ![mrlearning-ch1-2-step7](images/mrlearning-speach-ch1-2-step7.jpg)

    >[!NOTE]
    ><span data-ttu-id="377a7-209">Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、[「ツールのインストール」ページ](install-the-tools.md)で示されている、前提条件となるすべてのコンポーネントがインストールされていることを確認してください</span><span class="sxs-lookup"><span data-stu-id="377a7-209">If Visual Studio asks you to install new components, please take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

8. <span data-ttu-id="377a7-210">USB ケーブルを使って HoloLens 2 を PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="377a7-210">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="377a7-211">これらのレッスンの手順では、HoloLens 2 デバイスを使ってテストをデプロイすることを前提としていますが、[HoloLens 2 エミュレーター](using-the-hololens-emulator.md)にデプロイすることも、[サイドローディング用のアプリ パッケージ](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)を作成することもできます</span><span class="sxs-lookup"><span data-stu-id="377a7-211">While these lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

9. <span data-ttu-id="377a7-212">デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="377a7-212">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="377a7-213">HoloLens 2 に初めてデプロイする場合は、Visual Studio により、PIN を使用して HoloLens 2 をペアリングするよう求められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="377a7-213">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="377a7-214">開発者モードを有効にするか、Visual Studio とペアリングする必要がある場合は、[こちらの手順](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="377a7-214">Please follow [these instructions](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

10. <span data-ttu-id="377a7-215">[リリース] 構成と [ARM] アーキテクチャを選択して、HoloLens 2 へのビルド用に Visual Studio を構成します。</span><span class="sxs-lookup"><span data-stu-id="377a7-215">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>

    ![mrlearning-ch1-2-step10](images/mrlearning-speach-ch1-2-step10.jpg)

11. <span data-ttu-id="377a7-217">最後の手順は、[デバッグ] > [デバッグなしで開始] を選択して、デバイスにビルドすることです。</span><span class="sxs-lookup"><span data-stu-id="377a7-217">The final step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="377a7-218">[デバッグなしで開始] を選択すると、ビルドが成功した時点でアプリケーションがデバイスですぐに起動しますが、Visual Studio にデバッグ情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="377a7-218">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="377a7-219">これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。</span><span class="sxs-lookup"><span data-stu-id="377a7-219">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="377a7-220">また、[ビルド] > [ソリューションの配置] を選択することで、アプリケーションを自動的に起動せずにデバイスに配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="377a7-220">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

    ![mrlearning-ch1-2-step11.JPG](images/mrlearning-speach-ch1-2-step11.jpg)

## <a name="congratulations"></a><span data-ttu-id="377a7-222">結論</span><span class="sxs-lookup"><span data-stu-id="377a7-222">Congratulations</span></span>

<span data-ttu-id="377a7-223">Azure を使用して、アプリケーションに音声認識を設定しました。</span><span class="sxs-lookup"><span data-stu-id="377a7-223">You've set up voice recognition in your application, powered by Azure.</span></span> <span data-ttu-id="377a7-224">アプリケーションを実行して、すべての関数と機能が正常に動作していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="377a7-224">Run the application to ensure all functions and features are working properly.</span></span> <span data-ttu-id="377a7-225">まず、「手順 22. ターミナルをアクティブ化する」で入力したウェイクワードを言います。</span><span class="sxs-lookup"><span data-stu-id="377a7-225">Start with saying the wake word you typed in Step 22, Activate Terminal.</span></span> <span data-ttu-id="377a7-226">マイクボタンをクリックして音声認識を開始します。</span><span class="sxs-lookup"><span data-stu-id="377a7-226">Select the Microphone button to start voice recognition.</span></span> <span data-ttu-id="377a7-227">読み上げを開始します。</span><span class="sxs-lookup"><span data-stu-id="377a7-227">Begin speaking.</span></span> <span data-ttu-id="377a7-228">書き起こしという単語がターミナルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="377a7-228">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="377a7-229">音声認識を停止するには、マイクボタンをもう一度押します。</span><span class="sxs-lookup"><span data-stu-id="377a7-229">Press the Microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="377a7-230">「ターミナルを閉じる」と言うと、Lunarcom ターミナルが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="377a7-230">Say Dismiss Terminal to hide the Lunarcom terminal.</span></span> <span data-ttu-id="377a7-231">次のレッスンでは、HoloLens 2 がオフラインであるために Azure の speech SDK が利用できない場合に、デバイスを使用した音声認識を使用してに動的に切り替える方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="377a7-231">In the next lesson, we'll learn how to dynamically switch to using device-powered voice recognition for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="377a7-232">次のチュートリアル: 2. ローカルの音声からテキストへの変換のオフラインモードの追加</span><span class="sxs-lookup"><span data-stu-id="377a7-232">Next tutorial: 2. Adding an offline mode for local speech-to-text translation</span></span>](mrlearning-speechSDK-ch2.md)
