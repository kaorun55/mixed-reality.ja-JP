---
title: Azure Speech Services チュートリアル-1. 音声認識と議事録の統合と使用
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 25e5aa05839845620a23c3dba6698ac7b5854d6d
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553976"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="9e3cc-105">1. 音声認識と議事録の統合と使用</span><span class="sxs-lookup"><span data-stu-id="9e3cc-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="9e3cc-106">概要</span><span class="sxs-lookup"><span data-stu-id="9e3cc-106">Overview</span></span>

<span data-ttu-id="9e3cc-107">このチュートリアルでは、Azure Cognitive Services Speech SDK と HoloLens 2 の使用方法を紹介する Mixed Reality アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-107">This tutorial creates a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="9e3cc-108">このチュートリアルシリーズを完了すると、デバイスのマイクを使用して、音声をリアルタイムでテキストにしたり、音声を他の言語に変換したり、音声認識 SDK の目的機能を活用して、人工の音声コマンドを理解したりすることができます。高度.</span><span class="sxs-lookup"><span data-stu-id="9e3cc-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="9e3cc-109">目標</span><span class="sxs-lookup"><span data-stu-id="9e3cc-109">Objectives</span></span>

* <span data-ttu-id="9e3cc-110">Azure Speech SDK を HoloLens 2 アプリケーションに統合する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="9e3cc-110">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
* <span data-ttu-id="9e3cc-111">音声コマンドの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-111">Learn how to use voice commands</span></span>
* <span data-ttu-id="9e3cc-112">音声をテキストに変換する機能の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-112">Learn how to use speech-to-text capabilities</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e3cc-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="9e3cc-113">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="9e3cc-114">[概要チュートリアル](mrlearning-base.md)シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-114">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="9e3cc-115">正しい[ツールがインストールされている](install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="9e3cc-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="9e3cc-116">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="9e3cc-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="9e3cc-117">基本的な C# プログラミング能力</span><span class="sxs-lookup"><span data-stu-id="9e3cc-117">Some basic C# programming ability</span></span>
* <span data-ttu-id="9e3cc-118">[開発用に構成された](using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="9e3cc-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="9e3cc-119">このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.2.X です。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="9e3cc-120">これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="getting-started"></a><span data-ttu-id="9e3cc-121">作業の開始</span><span class="sxs-lookup"><span data-stu-id="9e3cc-121">Getting Started</span></span>

1. <span data-ttu-id="9e3cc-122">Unity を起動し、新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-122">Start Unity, and create a new project.</span></span> <span data-ttu-id="9e3cc-123">Project name Speech SDK Learning モジュールを入力します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-123">Enter the project name Speech SDK Learning Module.</span></span> <span data-ttu-id="9e3cc-124">プロジェクトを保存する場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-124">Choose a location for where to save your project.</span></span> <span data-ttu-id="9e3cc-125">[プロジェクトの作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-125">Click Create Project.</span></span>

    ![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

    >[!NOTE]
    ><span data-ttu-id="9e3cc-127">上の図に示すように、テンプレートが3D に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-127">Ensure that the template is set to 3D, as shown in the image above.</span></span>

2. <span data-ttu-id="9e3cc-128">[Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation パッケージバージョン 2.3.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)をダウンロードし、PC 上のフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-128">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation package version 2.3.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage) and save it to a folder on your PC.</span></span> <span data-ttu-id="9e3cc-129">Unity プロジェクトにパッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-129">Import the package into your Unity project.</span></span> <span data-ttu-id="9e3cc-130">これを行う方法の詳細については、入門チュートリアルの「レッスン2」を参照してください[。プロジェクトと最初のアプリケーションを初期化して](mrlearning-base-ch1.md)います。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-130">For detailed instructions on how to do this, see the [Getting started tutorials - Lesson 2. Initializing your project and first application](mrlearning-base-ch1.md).</span></span>

3. <span data-ttu-id="9e3cc-131">Unity 資産パッケージ用の Azure [SPEECH SDK](https://aka.ms/csspeech/unitypackage)をダウンロードしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-131">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for the Unity asset package.</span></span> <span data-ttu-id="9e3cc-132">[アセット] をクリックし、[パッケージのインポート]、[カスタムパッケージ] の順に選択して、Speech SDK パッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-132">Import the Speech SDK package by clicking on Assets, selecting Import package, then selecting Custom Package.</span></span> <span data-ttu-id="9e3cc-133">先ほどダウンロードした Speech SDK パッケージを検索し、それを開いてインポートプロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-133">Find the Speech SDK package downloaded earlier, and open it to begin the importing process.</span></span>

    ![mrlearning-speech-ch1-1-step3a](images/mrlearning-speech-ch1-1-step3a.png)

    ![mrlearning-speech-ch1-1-step3b](images/mrlearning-speech-ch1-1-step3b.png)

4. <span data-ttu-id="9e3cc-136">次のポップアップウィンドウで [インポート] をクリックして、Speech SDK パッケージのインポートを開始します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-136">In the next pop-up window, click Import to begin importing the Speech SDK package.</span></span> <span data-ttu-id="9e3cc-137">次の図に示すように、すべての項目がチェックされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-137">Ensure all items are checked, as shown in the image below.</span></span>

    ![mrlearning-speech-ch1-1-step4](images/mrlearning-speech-ch1-1-step4.png)

5. <span data-ttu-id="9e3cc-139">チュートリアル資産をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-139">Download the tutorial assets:</span></span>
    * [<span data-ttu-id="9e3cc-140">MRTK。HoloLens2. 2.3.0.2. unitypackage を実行します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * <span data-ttu-id="9e3cc-141">[SpeechSDKAssets unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/Speech_2/SpeechSDKAssets.unitypackage) (バージョン 1.2)</span><span class="sxs-lookup"><span data-stu-id="9e3cc-141">[SpeechSDKAssets.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/Speech_2/SpeechSDKAssets.unitypackage) (version 1.2)</span></span>

    <span data-ttu-id="9e3cc-142">SpeechSDKAssets asset パッケージは、このチュートリアルシリーズ用に開発された資産とスクリプトのコレクションであり、Azure の Speech SDK の実際の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-142">The SpeechSDKAssets asset package is a collection of assets and scripts developed for this tutorial series to showcase practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="9e3cc-143">これは、入門チュートリアルで開発したロケットランチャーアセンブリエクスペリエンスに最終的にインターフェイスを提供する音声コマンド端末です[。レッスン 7.旧暦モジュールサンプルアプリケーションを作成する](mrlearning-base-ch6.md)。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-143">It is a voice-command terminal that will ultimately interface with the Rocket Launcher assembly experience developed in the [Getting started tutorials - Lesson 7. Creating a Lunar Module sample application](mrlearning-base-ch6.md).</span></span>

6. <span data-ttu-id="9e3cc-144">Mixed Reality Toolkit と Speech SDK をインポートする場合と同様の手順に従って、2つのチュートリアル資産パッケージを Unity プロジェクトにインポートします。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-144">Import the two tutorial asset packages into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>

7. <span data-ttu-id="9e3cc-145">Mixed Reality Toolkit (MRTK) を構成します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-145">Configure the Mixed Reality Toolkit (MRTK).</span></span>

    <span data-ttu-id="9e3cc-146">これを行うには、ウィンドウの上部にある [Mixed Reality Toolkit] パネルをクリックし、[シーンに追加] と [構成] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-146">To do this, click on the Mixed Reality Toolkit panel in the top of your window, and then select Add to Scene and Configure.</span></span>

    ![mrlearning-speech-ch1-1-step7a](images/mrlearning-speech-ch1-1-step7a.png)

    <span data-ttu-id="9e3cc-148">シーン階層で MixedRealityToolkit オブジェクトを選択した状態で、[インスペクター] ウィンドウで [DefaultHoloLens2ConfigurationProfile] を選択し、Mixed Reality Toolkit のアクティブなプロファイルにします。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-148">With the MixedRealityToolkit object selected in your scene hierarchy, in the Inspector window, select DefaultHoloLens2ConfigurationProfile to make it the Active Profile for the Mixed Reality Toolkit.</span></span>

    ![mrlearning-speech-ch1-1-step7b](images/mrlearning-speech-ch1-1-step7b.png)

8. <span data-ttu-id="9e3cc-150">これで、シーンに MRTK から複数の新しい項目が追加されました。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-150">Your scene now has several new items in it from the MRTK.</span></span> <span data-ttu-id="9e3cc-151">[ファイル]、[名前を付けて保存] の順にクリックし、シーンに SpeechScene という名前を付けて、シーンを別の名前で保存します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-151">Save your scene under a different name by clicking on "file," then "save as" and name your scene SpeechScene.</span></span>

    >[!NOTE]
    ><span data-ttu-id="9e3cc-152">プロジェクトに MRTK を追加した後にシーンで Play を押すと、再生モードにならない場合は、Unity の再起動が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-152">If you press Play on your scene after you add the MRTK to your project, and it doesn't enter play mode, you might need to restart Unity.</span></span>

9. <span data-ttu-id="9e3cc-153">シーン階層で MixedRealityToolkit オブジェクトを選択した状態で、[インスペクター] パネルの [& のコピー] をクリックして [複製プロファイル] ポップアップを開きます。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-153">With the MixedRealityToolkit object selected in your scene hierarchy, click Copy & Customize in the Inspector panel to open the Clone Profile popup.</span></span> <span data-ttu-id="9e3cc-154">[複製プロファイル] ポップアップで、カスタムプロファイルに適切な名前 (たとえば、Custom HoloLens2ConfigurationProfile) を入力します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-154">In the Clone Profile popup, enter a suitable name for your custom profile, for example, Custom HoloLens2ConfigurationProfile.</span></span> <span data-ttu-id="9e3cc-155">[複製] をクリックしてカスタム構成プロファイルを作成し、アクティブなプロファイルとして設定します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-155">Click Clone to create your custom configuration profile and set it as the active profile.</span></span>

    ![mrlearning-speech-ch1-1-step9](images/mrlearning-speech-ch1-1-step9.png)

10. <span data-ttu-id="9e3cc-157">また、[インスペクター] パネル (階層で MixedRealityToolkit オブジェクトが選択された状態) で、[診断システムを有効にする] の右側のチェックボックスをオフにして、診断システムを無効にします。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-157">Also in the Inspector panel (with the MixedRealityToolkit object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of Enable Diagnostics System.</span></span>

    ![mrlearning-speech-ch1-1-step10](images/mrlearning-speech-ch1-1-step10.png)

11. <span data-ttu-id="9e3cc-159">このチュートリアルでは、音声認識と議事録に入力音声コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-159">In this tutorial, we are using the input speech commands for speech recognition and transcription.</span></span> <span data-ttu-id="9e3cc-160">音声設定を変更するために、入力プロファイルを複製してみましょう。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-160">Let's clone the input profile to make changes to speech settings.</span></span>

    <span data-ttu-id="9e3cc-161">シーン階層で MixedRealityToolkit オブジェクトを選択した状態で、[インスペクター] パネルの [小さい複製] ボタンをクリックして、[複製プロファイル] ポップアップを開きます。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-161">With the MixedRealityToolkit object still selected in your scene hierarchy, click the small Clone button in the Inspector panel to open the Clone Profile popup.</span></span> <span data-ttu-id="9e3cc-162">[複製プロファイル] ポップアップで、カスタムプロファイルに適切な名前 (たとえば、Custom HoloLens2InputSystemProfile) を入力し、[複製] をクリックしてカスタム入力システムプロファイルを作成し、アクティブなプロファイルとして設定します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-162">In the Clone Profile popup, enter a suitable name for your custom profile, for example, Custom HoloLens2InputSystemProfile, and then click Clone to create your custom input system profile and set it as the active profile.</span></span>

    ![mrlearning-speech-ch1-1-step11](images/mrlearning-speech-ch1-1-step11.png)

12. <span data-ttu-id="9e3cc-164">入力プロファイルが複製されたら、Speech セクションを展開し、前の手順と同じプロセスに従って speech コマンドプロファイルを複製します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-164">Once the input profile is cloned, expand the Speech section and follow the same process as in the previous step to clone the speech commands profile.</span></span>

    ![mrlearning-speech-ch1-1-step12](images/mrlearning-speech-ch1-1-step12.png)

13. <span data-ttu-id="9e3cc-166">[音声] セクションで、[全般設定] に移動し、[開始動作] を [手動開始] に変更します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-166">Under the Speech section, go to General Settings and change Start Behavior to Manual Start.</span></span>

    ![mrlearning-speech-ch1-1-step13](images/mrlearning-speech-ch1-1-step13.png)

14. <span data-ttu-id="9e3cc-168">[プロジェクト] パネルで、[Lunarcom] フォルダーを展開し、Lunarcom_Base prefab をシーン階層にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-168">In the Project panel, expand the Lunarcom folder and drag the Lunarcom_Base prefab into your scene hierarchy.</span></span>

    ![mrlearning-speech-ch1-1-step14](images/mrlearning-speech-ch1-1-step14.png)

15. <span data-ttu-id="9e3cc-170">階層内の Lunarcom_Base オブジェクトを選択し、位置が x = 0、y = 0、z = 0 に設定されていること、および x = 0、y = 0、z = 0 に設定された回転を確認します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-170">Select the Lunarcom_Base object in your hierarchy, and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="9e3cc-171">Scale を read x = 0.008、y = 0.008、および z = 0.01 に設定します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-171">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

    ![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. <span data-ttu-id="9e3cc-173">[コンポーネントの追加] をクリックし、[Lunarcom コントローラー] を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-173">Click Add Component, and search for and select Lunarcom Controller.</span></span> <span data-ttu-id="9e3cc-174">このスクリプトは、手順 6. でインポートした Lunarcom アセットパックに含まれています。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-174">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

    ![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. <span data-ttu-id="9e3cc-176">アプリケーションを Azure Cognitive Services に接続するには、Speech サービスのサブスクリプションキー (API キーとも呼ばれます) を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-176">To connect our application to Azure Cognitive Services, you must enter a subscription key (also known as an API Key), for the Speech Service.</span></span> <span data-ttu-id="9e3cc-177">無料のサブスクリプションキーを取得するには、[こちら](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-177">Follow the instructions at [here](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="9e3cc-178">サブスクリプションキーを取得したら、次の図に示すように、[インスペクター] パネルの [LunarcomController] コンポーネントの [Speech Service API キー] フィールドに入力します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-178">Once you obtain the subscription key, enter it into the Speech Service API Key field of the LunarcomController component in the Inspector panel, as shown in the image below.</span></span>

18. <span data-ttu-id="9e3cc-179">[インスペクター] パネルの [LunarcomController] コンポーネントの [Speech Service Region] フィールドに、サブスクリプションキーにサインアップしたときに選択したリージョンを入力します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-179">Enter the Region that you chose when you signed up for the subscription key into the Speech Service Region field of the LunarcomController component in the Inspector panel.</span></span> <span data-ttu-id="9e3cc-180">たとえば、"westus" という地域では "米国西部" と入力します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-180">For example, for the region West US type in "westus".</span></span>

    ![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. <span data-ttu-id="9e3cc-182">階層で、左側の矢印をクリックして Lunarcom_Base オブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-182">In your hierarchy, expand the Lunarcom_Base object by clicking the arrow to the left of it.</span></span> <span data-ttu-id="9e3cc-183">その後、次の図に示すように、子オブジェクト "ターミナル" に対して同じ操作を行います。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-183">Then do the same for its child object, "Terminal, as shown in the image below.</span></span>

20. <span data-ttu-id="9e3cc-184">Lunarcom_Base を選択した状態で、次の図に示すように、階層の Lunarcom テキストをクリックして、[インスペクター] パネルの [LunarcomController] コンポーネントの出力テキストスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-184">While Lunarcom_Base is selected, click and drag Lunarcom Text from the hierarchy to the Output Text slot in the LunarcomController component in the Inspector panel, as shown in the image below.</span></span>

21. <span data-ttu-id="9e3cc-185">ターミナルオブジェクトをターミナルスロットに、接続光オブジェクトを接続ライトコントローラースロットに対して同じ操作を行います。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-185">Do the same thing with the Terminal object into the Terminal slot and the Connection Light object to the Connection Light Controller slot.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. <span data-ttu-id="9e3cc-187">[インスペクター] パネルの LunarcomController スクリプトの [Lunarcom ボタン] セクションの横にある矢印をクリックし、サイズを3に変更します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-187">Click the arrow next to the Lunarcom Buttons section of the LunarcomController script in the Inspector panel, and change the size to 3.</span></span> <span data-ttu-id="9e3cc-188">Enter キーを押すか、戻ります。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-188">Press Enter or Return.</span></span> <span data-ttu-id="9e3cc-189">これにより、3つの新しい要素フィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-189">This causes three new Element fields to appear.</span></span>

    ![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. <span data-ttu-id="9e3cc-191">[Lunarcom] ボタンを展開します。このボタンの横にある矢印をクリックし、上記と同じプロセスを使用して、Mic、衛星、およびロケットの各オブジェクトを、次のように、それぞれの LunarcomController コンポーネントの要素0、1、および2にドラッグします。インスペクターパネル。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-191">Expand the Lunarcom Buttons by clicking the arrow next to it in your hierarchy, and using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references, respectively, in the LunarcomController component in the Inspector panel.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. <span data-ttu-id="9e3cc-193">階層内の Lunarcom_Base のオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-193">Select the Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="9e3cc-194">[インスペクター] パネルの [コンポーネントの追加] をクリックし、[Lunarcom Speech レコグナイザー] を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-194">Click Add Component in the inspector panel and search for and select Lunarcom Speech Recognizer.</span></span> <span data-ttu-id="9e3cc-195">同じ手順を繰り返して、Lunarcom Wake Word レコグナイザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-195">Repeat the same steps to add Lunarcom Wake Word Recognizer.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. <span data-ttu-id="9e3cc-197">Wake Word スロットで、「Activate Terminal」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-197">In the Wake Word slot, type in Activate Terminal.</span></span> <span data-ttu-id="9e3cc-198">[Word のスロットを閉じる] に「ターミナルを閉じる」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-198">In the Dismiss Word slot, type Dismiss Terminal.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="9e3cc-200">デバイスへのアプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="9e3cc-200">Build your application to your device</span></span>

1. <span data-ttu-id="9e3cc-201">[ファイル > ビルドの設定] に移動して、[ビルドの設定] ウィンドウを再び開きます。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-201">Open the build settings window again by going to File>Build Settings.</span></span>

    ![images/mrlearning-ch1-2-ステップ1](images/mrlearning-speach-ch1-2-step1.jpg)

2. <span data-ttu-id="9e3cc-203">[開いているシーンの追加] ボタンをクリックして、試したいシーンが [ビルド内のシーン] リストに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-203">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>

3. <span data-ttu-id="9e3cc-204">[プレーヤーの設定] ボタンをクリックし、[発行の設定] にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-204">Press the Player Settings button and go to Publishing Settings.</span></span> <span data-ttu-id="9e3cc-205">[機能] で、[インターネット]、[インターネットクライアントサーバー]、[プライベートネットワーククライアントサーバー]、[マイクと空間認識] を有効にします。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-205">Under Capabilities, enable: Internet, Internet Client Server, Private Network Client Server, Microphone and Spatial Perception.</span></span>

4. <span data-ttu-id="9e3cc-206">同じプレーヤー設定で、XR settings にアクセスして、でサポートされている仮想現実を選択します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-206">In the same Player Settings, go to XR settings  and select the Virtual Reality Supported to ON.</span></span>

5. <span data-ttu-id="9e3cc-207">[ビルド] ボタンを押して、ビルド プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-207">Press the Build button to begin the build process.</span></span>

    ![mrlearning-ch1-2-手順5](images/mrlearning-speach-ch1-2-step5.jpg)

6. <span data-ttu-id="9e3cc-209">アプリケーション用の新しいフォルダーを作成して、名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-209">Create and name a new folder for your application.</span></span> <span data-ttu-id="9e3cc-210">下の図では、アプリケーションを含めるために [App] という名前のフォルダーが作成されています。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-210">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="9e3cc-211">[フォルダーの選択] をクリックして、新しく作成したフォルダーへのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-211">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="9e3cc-212">ビルドが完了したら、Unity の [ビルド設定] ウィンドウを閉じてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-212">After the build has completed, you may close the "Build Settings" window in Unity.</span></span>

    ![mrlearning-ch1-2-手順6](images/mrlearning-speach-ch1-2-step6.jpg)

    >[!NOTE]
    ><span data-ttu-id="9e3cc-214">ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-214">If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="9e3cc-215">"エラー: CS0246 = 型または名前空間名" XX "が見つかりませんでした (using ディレクティブまたはアセンブリ参照が不足していることを確認してください)" というエラーが表示された場合は、 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)のインストールが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-215">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span></span>

7. <span data-ttu-id="9e3cc-216">ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-216">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="9e3cc-217">".Sln" ソリューションファイルをダブルクリックして、Visual Studio でソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-217">Double-click on the “.sln” solution file to open the solution file in Visual Studio.</span></span>

    >[!NOTE]
    ><span data-ttu-id="9e3cc-218">新しく作成されたフォルダー (前の手順の名前付け規則に従っている場合は "App" フォルダー) を必ず開いてください。これは、ビルドフォルダー内の .sln ファイルとは異なる、同じ名前の .sln ファイルがそのフォルダー外に存在するためです。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-218">Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is different from the .sln file inside the build folder.</span></span> 

    ![mrlearning-ch1-2-step7](images/mrlearning-speach-ch1-2-step7.jpg)

    >[!NOTE]
    ><span data-ttu-id="9e3cc-220">Visual Studio で新しいコンポーネントのインストールを求められた場合は、 [[ツールのインストール] ページ](install-the-tools.md)で指定したとおりにすべての前提条件コンポーネントがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-220">If Visual Studio asks you to install new components, ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

8. <span data-ttu-id="9e3cc-221">USB ケーブルを使って HoloLens 2 を PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-221">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="9e3cc-222">これらのレッスンの手順では、HoloLens 2 デバイスを使ってテストをデプロイすることを前提としていますが、[HoloLens 2 エミュレーター](using-the-hololens-emulator.md)にデプロイすることも、[サイドローディング用のアプリ パッケージ](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)を作成することもできます</span><span class="sxs-lookup"><span data-stu-id="9e3cc-222">While these lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

9. <span data-ttu-id="9e3cc-223">デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-223">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="9e3cc-224">HoloLens 2 に初めてデプロイする場合は、Visual Studio により、PIN を使用して HoloLens 2 をペアリングするよう求められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-224">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="9e3cc-225">開発者モードを有効にするか、Visual Studio とペアリングする必要がある場合は、[こちらの手順](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-225">Please follow [these instructions](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

10. <span data-ttu-id="9e3cc-226">[リリース] 構成と [ARM] アーキテクチャを選択して、HoloLens 2 へのビルド用に Visual Studio を構成します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-226">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>

    ![mrlearning-ch1-2-step10](images/mrlearning-speach-ch1-2-step10.jpg)

11. <span data-ttu-id="9e3cc-228">最後の手順は、[デバッグ] > [デバッグなしで開始] を選択して、デバイスにビルドすることです。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-228">The final step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="9e3cc-229">[デバッグなしで開始] を選択すると、ビルドが成功した時点でアプリケーションがデバイスですぐに起動しますが、Visual Studio にデバッグ情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-229">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="9e3cc-230">これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-230">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="9e3cc-231">また、[ビルド] > [ソリューションの配置] を選択することで、アプリケーションを自動的に起動せずにデバイスに配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-231">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

    ![mrlearning-ch1-2-step11.JPG](images/mrlearning-speach-ch1-2-step11.jpg)

## <a name="congratulations"></a><span data-ttu-id="9e3cc-233">結論</span><span class="sxs-lookup"><span data-stu-id="9e3cc-233">Congratulations</span></span>

<span data-ttu-id="9e3cc-234">Azure を使用して、アプリケーションに音声認識を設定しました。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-234">You've set up voice recognition in your application, powered by Azure.</span></span> <span data-ttu-id="9e3cc-235">アプリケーションを実行して、すべての関数と機能が正常に動作していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-235">Run the application to ensure all functions and features are working properly.</span></span> <span data-ttu-id="9e3cc-236">まず、「手順 25. でターミナルをアクティブ化する」で入力したウェイクワードを言います。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-236">Start with saying the wake word you typed in Step 25, Activate Terminal.</span></span> <span data-ttu-id="9e3cc-237">マイクボタンをクリックして音声認識を開始します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-237">Select the Microphone button to start voice recognition.</span></span> <span data-ttu-id="9e3cc-238">読み上げを開始します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-238">Begin speaking.</span></span> <span data-ttu-id="9e3cc-239">書き起こしという単語がターミナルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-239">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="9e3cc-240">音声認識を停止するには、マイクボタンをもう一度押します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-240">Press the Microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="9e3cc-241">「ターミナルを閉じる」と言うと、Lunarcom ターミナルが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-241">Say Dismiss Terminal to hide the Lunarcom terminal.</span></span> <span data-ttu-id="9e3cc-242">次のレッスンでは、HoloLens 2 がオフラインであるために Azure の speech SDK が利用できない場合に、デバイスを使用した音声認識を使用してに動的に切り替える方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e3cc-242">In the next lesson, you'll learn how to dynamically switch to using device-powered voice recognition for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="9e3cc-243">次のチュートリアル: 2. ローカルの音声からテキストへの変換のオフラインモードの追加</span><span class="sxs-lookup"><span data-stu-id="9e3cc-243">Next tutorial: 2. Adding an offline mode for local speech-to-text translation</span></span>](mrlearning-speechSDK-ch2.md)
