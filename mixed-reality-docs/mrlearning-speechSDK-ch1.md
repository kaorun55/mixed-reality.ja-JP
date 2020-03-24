---
title: Azure Speech Services のチュートリアル - 1. 音声認識と文字起こしの統合と使用
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure Speech SDK を実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: a72eb808adbc14df65c55e694ea985d97f9ec24c
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79032583"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="90f53-105">1.音声認識と文字起こしの統合と使用</span><span class="sxs-lookup"><span data-stu-id="90f53-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="90f53-106">概要</span><span class="sxs-lookup"><span data-stu-id="90f53-106">Overview</span></span>


<span data-ttu-id="90f53-107">このチュートリアル シリーズでは、HoloLens 2 での Azure Speech Services の使用を探索する Mixed Reality アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="90f53-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="90f53-108">このチュートリアル シリーズを完了すると、デバイスのマイクを使用して、リアルタイムで音声を文字に起こしたり、音声を他の言語に翻訳したり、意図認識機能を利用して、人工知能を使って音声コマンドを理解したりできるようになります。</span><span class="sxs-lookup"><span data-stu-id="90f53-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="90f53-109">目標</span><span class="sxs-lookup"><span data-stu-id="90f53-109">Objectives</span></span>

* <span data-ttu-id="90f53-110">Azure Speech Services と HoloLens 2 アプリケーションを統合する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="90f53-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="90f53-111">音声認識を使用して文字に起こす方法を学習する</span><span class="sxs-lookup"><span data-stu-id="90f53-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="90f53-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="90f53-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="90f53-113">[入門チュートリアル](mrlearning-base.md) シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="90f53-113">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="90f53-114">正しい[ツールがインストールされている](install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="90f53-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="90f53-115">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="90f53-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="90f53-116">基本的な C# プログラミング能力</span><span class="sxs-lookup"><span data-stu-id="90f53-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="90f53-117">[開発用に構成された](using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="90f53-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="90f53-118">Unity 2019.2.X がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="90f53-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90f53-119">このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.2.X です。</span><span class="sxs-lookup"><span data-stu-id="90f53-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="90f53-120">これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="90f53-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="90f53-121">Unity プロジェクトの作成と準備</span><span class="sxs-lookup"><span data-stu-id="90f53-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="90f53-122">このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備をします。</span><span class="sxs-lookup"><span data-stu-id="90f53-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="90f53-123">このためには、まず「[プロジェクトと最初のアプリケーションの初期化](mrlearning-base-ch1.md)」に従ってください (「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」の手順は除く)。これには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="90f53-123">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="90f53-124">[新しい Unity プロジェクトを作成](mrlearning-base-ch1.md#create-new-unity-project)して、適切な名前を付ける (たとえば、*MRTK Tutorials*)</span><span class="sxs-lookup"><span data-stu-id="90f53-124">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="90f53-125">Windows Mixed Reality 用に Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="90f53-125">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="90f53-126">TextMesh Pro の Essential Resources (重要なリソース) をインポートする</span><span class="sxs-lookup"><span data-stu-id="90f53-126">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="90f53-127">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="90f53-127">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="90f53-128">Mixed Reality Toolkit 用に Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="90f53-128">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="90f53-129">[Mixed Reality Toolkit を Unity シーンに追加](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)し、シーンに適切な名前を付ける (たとえば、*AzureSpeechServices*)</span><span class="sxs-lookup"><span data-stu-id="90f53-129">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="90f53-130">次に、「[Mixed Reality Toolkit プロファイルを構成する方法 (空間認識表示オプションの変更)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)」の手順に従って、シーンの MRTK 構成プロファイルを **[DefaultHoloLens2ConfigurationProfile]** に変更し、空間認識メッシュの表示オプションを **[Occlusion]\(オクルージョン\)** に変更します。</span><span class="sxs-lookup"><span data-stu-id="90f53-130">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="90f53-131">上のリンクの「[Mixed Reality Toolkit 用に Unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)」の手順で述べられているように、MSBuild for Unity を有効にしないことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="90f53-131">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="90f53-132">音声コマンドの開始動作の構成</span><span class="sxs-lookup"><span data-stu-id="90f53-132">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="90f53-133">音声認識と文字起こしには Speech SDK を使用するため、Speech SDK の機能の妨げにならないように、MRTK の音声コマンドを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90f53-133">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="90f53-134">これを実現するには、音声コマンドの開始動作を [Auto Start]\(自動開始\) から [Manual Start]\(手動開始\) に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="90f53-134">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="90f53-135">[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Input]\(入力\)** タブを選択し、**DefaultHoloLens2InputSystemProfile** と **DefaultMixedRealitySpeechCommandsProfile** を複製し、音声コマンドの **[Start Behavior]\(開始動作\)** を **[Manual Start]\(手動開始\)** に変更します。</span><span class="sxs-lookup"><span data-stu-id="90f53-135">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="90f53-137">MRTK プロファイルを複製して構成する方法については、「[Mixed Reality Toolkit プロファイルを構成する方法 (空間認識表示オプションの変更)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)」の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90f53-137">For a reminder on how to clone and configure MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="90f53-138">機能の構成</span><span class="sxs-lookup"><span data-stu-id="90f53-138">Configuring the capabilities</span></span>

<span data-ttu-id="90f53-139">Unity メニューで **[Edit]\(編集\)**  >  **[Project Settings]\(プロジェクトの設定\)** を選択して、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。次に、 **[Player]\(プレーヤー\)**  >   **[Publishing Settings]\(発行の設定\)** セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="90f53-139">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="90f53-141">**[Publishing Settings]\(発行の設定\)** で、下にスクロールして **[Capabilities]\(機能\)** セクションまで移動し、チュートリアルの開始時にプロジェクトを作成したときに有効にした **InternetClient**、**Microphone**、および **SpatialPerception** の機能が有効になっていることを再確認します。</span><span class="sxs-lookup"><span data-stu-id="90f53-141">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="90f53-142">次に、**InternetClientServer** と **PrivateNetworkClientServer** の機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="90f53-142">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="90f53-144">チュートリアルのアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="90f53-144">Importing the tutorial assets</span></span>

<span data-ttu-id="90f53-145">次の Unity カスタム パッケージを、**一覧に表示されている順序で**ダウンロードして**インポート**します。</span><span class="sxs-lookup"><span data-stu-id="90f53-145">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="90f53-146">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (最新バージョン)</span><span class="sxs-lookup"><span data-stu-id="90f53-146">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="90f53-147">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="90f53-147">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [<span data-ttu-id="90f53-148">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="90f53-148">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="90f53-149">Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90f53-149">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="90f53-150">チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="90f53-150">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a><span data-ttu-id="90f53-152">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="90f53-152">Preparing the scene</span></span>

<span data-ttu-id="90f53-153">このセクションでは、チュートリアルのプレハブを追加してシーンを準備し、シーンを制御するように Lunarcom Controller (Script) コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="90f53-153">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="90f53-154">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.AzureSpeechServices]**  >  **[Prefabs]** フォルダーに移動し、 **[Lunarcom]** プレハブを [Hierarchy]\(階層\) ウィンドウにドラッグしてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="90f53-154">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="90f53-156">[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Lunarcom Controller (Script)** コンポーネントを Lunarcom オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="90f53-156">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="90f53-158">Lunarcom Controller (Script) コンポーネントは MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="90f53-158">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="90f53-159">このチュートリアルのアセットと共に提供されました。</span><span class="sxs-lookup"><span data-stu-id="90f53-159">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="90f53-160">**[Lunarcom]** オブジェクトを選択した状態で、それを展開して子オブジェクトを表示し、次に **Terminal** オブジェクトを Lunarcom Controller (Script) コンポーネントの **[Terminal]\(ターミナル\)** フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="90f53-160">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="90f53-162">**Lunarcom** オブジェクトを選択した状態で、Terminal オブジェクトを展開して子オブジェクトを表示し、**ConnectionLight** オブジェクトを Lunarcom Controller (Script) コンポーネントの **[Connection Light]\(接続ライト\)** フィールドに、**OutputText** オブジェクトを **[Output Text]\(出力テキスト\)** フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="90f53-162">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="90f53-164">**Lunarcom** オブジェクトを選択した状態で、Buttons オブジェクトを展開して子オブジェクトを表示し、次に [Inspector]\(インスペクター\) ウィンドウで **[Buttons]\(ボタン\)** リストを展開し、その **[Size]\(サイズ\)** を 3 に設定し、**MicButton**、**SatelliteButton**、および **RocketButton** の各オブジェクトを **[Element]\(要素\)** 0、1、2 のフィールドにそれぞれドラッグします。</span><span class="sxs-lookup"><span data-stu-id="90f53-164">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="90f53-166">Unity プロジェクトを Azure リソースに接続</span><span class="sxs-lookup"><span data-stu-id="90f53-166">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="90f53-167">Azure Speech Services を使用するには、Azure リソースを作成し、Speech Service 用の API キーを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90f53-167">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="90f53-168">「[Speech Service を無料で試す](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)」の手順に従って、ご利用のサービス リージョン (ロケーションとも呼ばれる) と API キー (Key1 または Key2 とも呼ばれる) をメモします。</span><span class="sxs-lookup"><span data-stu-id="90f53-168">Follow the [Try the Speech service for free](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="90f53-169">[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択し、次に [Inspector]\(インスペクター\) ウィンドウで **Lunarcom Controller (Script)** コンポーネントの **[Speech SDK Credentials]\(Speech SDK 資格情報\)** セクションを見つけ、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="90f53-169">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="90f53-170">**[Speech Service API Key]\(Speech Service の API キー\)** フィールドに、API キー (Key1 または Key2) を入力します</span><span class="sxs-lookup"><span data-stu-id="90f53-170">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="90f53-171">**[Speech Service Region]\(Speech Service のリージョン\)** フィールドに、小文字を使用し、スペースを削除して、サービス リージョン (ロケーション) を入力します</span><span class="sxs-lookup"><span data-stu-id="90f53-171">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="90f53-173">音声認識を使用して音声を文字に起こす</span><span class="sxs-lookup"><span data-stu-id="90f53-173">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="90f53-174">[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Lunarcom Speech Recognizer (Script)** コンポーネントを Lunarcom オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="90f53-174">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="90f53-176">Lunarcom Speech Recognizer (Script) コンポーネントは MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="90f53-176">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="90f53-177">このチュートリアルのアセットと共に提供されました。</span><span class="sxs-lookup"><span data-stu-id="90f53-177">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="90f53-178">ゲーム モードに入ったら、まずマイクのボタンを押して音声認識をテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="90f53-178">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="90f53-180">次に、お使いのコンピューターにマイクがあると仮定して、何か話すと、音声がターミナルのパネル上に文字で表示されます。</span><span class="sxs-lookup"><span data-stu-id="90f53-180">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> <span data-ttu-id="90f53-182">アプリケーションは Azure に接続する必要があるため、お使いのコンピューター/デバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="90f53-182">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="90f53-183">結論</span><span class="sxs-lookup"><span data-stu-id="90f53-183">Congratulations</span></span>

<span data-ttu-id="90f53-184">Azure で提供される音声認識を実装しました。</span><span class="sxs-lookup"><span data-stu-id="90f53-184">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="90f53-185">デバイスでアプリケーションを実行して、機能が正常に動作していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="90f53-185">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="90f53-186">次のチュートリアルでは、Azure 音声認識を使用してコマンドを実行する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="90f53-186">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

[<span data-ttu-id="90f53-187">次のチュートリアル: 2.音声認識を使用したコマンドの実行</span><span class="sxs-lookup"><span data-stu-id="90f53-187">Next tutorial: 2. Using speech recognition to execute commands</span></span>](mrlearning-speechSDK-ch2.md)
