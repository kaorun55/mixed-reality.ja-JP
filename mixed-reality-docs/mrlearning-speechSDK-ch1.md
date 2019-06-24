# <a name="speech-sdk-learning-module"></a><span data-ttu-id="4cbb8-101">Speech SDK の機械学習モジュール</span><span class="sxs-lookup"><span data-stu-id="4cbb8-101">Speech SDK Learning Module</span></span>

<span data-ttu-id="4cbb8-102">このチュートリアルでは、Azure Cognitive Services の音声 SDK HoloLens 2 の使用について説明する複合現実のアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-102">In this tutorial you will create a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="4cbb8-103">このチュートリアル シリーズを完了したらは、デバイスのマイクを使用して、議事録の作成をリアルタイムでのテキストに音声、音声を他の言語に翻訳および Speech SDK のインテントの機能を使用して音声コマンドを理解するを活用するができます。人工知能します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-103">When finished with this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

<span data-ttu-id="4cbb8-104">目標:</span><span class="sxs-lookup"><span data-stu-id="4cbb8-104">Objectives:</span></span>

- <span data-ttu-id="4cbb8-105">HoloLens 2 アプリケーションに Azure の Speech SDK を統合する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="4cbb8-105">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
- <span data-ttu-id="4cbb8-106">音声コマンドを使用する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="4cbb8-106">Learn how to use voice commands</span></span>
- <span data-ttu-id="4cbb8-107">音声からテキストへの機能を使用する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="4cbb8-107">Learn how to use speech-to-text capabilities</span></span>

## <a name="instructions"></a><span data-ttu-id="4cbb8-108">手順</span><span class="sxs-lookup"><span data-stu-id="4cbb8-108">Instructions</span></span>

### <a name="getting-started"></a><span data-ttu-id="4cbb8-109">作業の開始</span><span class="sxs-lookup"><span data-stu-id="4cbb8-109">Getting Started</span></span>

1. <span data-ttu-id="4cbb8-110">Unity を起動し、新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-110">Start Unity and create a new project.</span></span> <span data-ttu-id="4cbb8-111">プロジェクト名「Speech SDK ラーニング モジュール」を入力します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-111">Enter the project name “Speech SDK Learning Module.”</span></span> <span data-ttu-id="4cbb8-112">プロジェクトの保存先の場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-112">Choose a location for where to save your project.</span></span> <span data-ttu-id="4cbb8-113">"プロジェクトの作成。"をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-113">Then click "Create Project."</span></span>

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> <span data-ttu-id="4cbb8-115">注:上記の図のようにテンプレートが"3 D"に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-115">Note: Ensure that the template is set to "3D," as shown in the image above.</span></span>

2. <span data-ttu-id="4cbb8-116">ダウンロード、 [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity パッケージ化し、PC 上のフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-116">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity package and save it to a folder on your PC.</span></span> <span data-ttu-id="4cbb8-117">Unity プロジェクトにパッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-117">Import the package into your Unity project.</span></span> <span data-ttu-id="4cbb8-118">これを行う方法の詳細についてを参照してください[ベース モジュール レッスン 1](mrlearning-base-ch1.md)します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-118">For detailed instructions on how to do this, please see [base module lesson 1](mrlearning-base-ch1.md).</span></span> 

3. <span data-ttu-id="4cbb8-119">ダウンロードして、Azure のインポート[Speech SDK](https://aka.ms/csspeech/unitypackage) for Unity asset パッケージ。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-119">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for Unity asset package.</span></span> <span data-ttu-id="4cbb8-120">アセット、"選択「パッケージのインポート、」「カスタムのパッケージ」を選択しをクリックして、Speech SDK パッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-120">Import the Speech SDK package by clicking on "assets," selecting "import package," then selecting "custom package."</span></span> <span data-ttu-id="4cbb8-121">以前にダウンロードした Speech SDK パッケージを検索してインポート プロセスを開始することを開きます。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-121">Find the Speech SDK package downloaded earlier and open it to begin the importing process.</span></span> 

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. <span data-ttu-id="4cbb8-123">次のポップアップ ウィンドウで、Speech SDK パッケージのインポートを開始するには、[インポート] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-123">In the next pop-up window, click “Import” to begin importing the Speech SDK package.</span></span> <span data-ttu-id="4cbb8-124">次の図に示すように、すべての項目が確認を確認します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-124">Ensure all items are checked, as shown in the image below.</span></span>

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)


5. <span data-ttu-id="4cbb8-126">ダウンロード、 [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage)資産パッケージ。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-126">Download the [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage) asset package.</span></span> <span data-ttu-id="4cbb8-127">Lunarcom アセット パッケージは、資産と Azure の Speech SDK の実際の使用を紹介するこのレッスンのシリーズで開発したスクリプトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-127">The Lunarcom asset package is a collection of assets and scripts developed for this lesson series to showcase a practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="4cbb8-128">開発された旧暦モジュール アセンブリのエクスペリエンスとのインターフェイスが最終的に音声コマンド ターミナルは、[ベース モジュールのチュートリアル。](mrlearning-base-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="4cbb8-128">It is a voice-command terminal that will ultimately interface with the lunar module assembly experience developed in the [Base Module Tutorial.](mrlearning-base-ch6.md)</span></span>
6. <span data-ttu-id="4cbb8-129">Mixed Reality Toolkit および Speech SDK をインポートする際と同様の手順に従って、Unity プロジェクトに Lunarcom アセット パッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-129">Import the Lunarcom asset package into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>
7. <span data-ttu-id="4cbb8-130">Mixed Reality ツールキット (MRTK) を構成します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-130">Configure the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="4cbb8-131">この場合、ウィンドウの上部にある"Mixed Reality Toolkit"パネルをクリックし、「シーンと構成に追加します」を選択し、</span><span class="sxs-lookup"><span data-stu-id="4cbb8-131">To do this, click on the "Mixed Reality Toolkit" panel in the top of your window, and then select "Add to Scene and Configure."</span></span>

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

8. <span data-ttu-id="4cbb8-133">シーンようになりましたがいくつかの新しい項目が、MRTK から。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-133">Your scene will now have several new items in it from the MRTK.</span></span> <span data-ttu-id="4cbb8-134">"File"をクリックして別の名前でシーンを保存し"として保存、シーン"SpeechScene"という名前をします。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-134">Save your scene under a different name by clicking on "file," then "save as" and name your scene “SpeechScene”.</span></span> 

   > <span data-ttu-id="4cbb8-135">注:プロジェクトに、MRTK を追加すると、「再生」モードを入力しないシーンの再生 ボタンを押した場合は、Unity を再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-135">Note: If you press the play button on your scene after you add the MRTK to your project, and it doesn't enter the "play" mode, you may need to restart Unity.</span></span> 

9. <span data-ttu-id="4cbb8-136">"MixedRealityToolkit"オブジェクトを階層内の選択、インスペクターのパネルで「コピーし、カスタマイズ」をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-136">With the “MixedRealityToolkit" object selected in your hierarchy, click "copy and customize" in the inspector panel.</span></span>

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. <span data-ttu-id="4cbb8-138">(の階層で選択されている"MixedRealityToolkit"オブジェクト) と [inspector] パネルで、「有効にする診断システム」の右側にボックスをオフにして、診断システムを無効にします。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-138">Also in the inspector panel (with the “MixedRealityToolkit" object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of "Enable Diagnostics System."</span></span>

![Module4Chapter1step10im](images/module4chapter1step10im.PNG)

11. <span data-ttu-id="4cbb8-140">プロジェクト パネルで、"Lunarcom"フォルダーを展開し、階層に"Lunarcom_Base"プレハブをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-140">In the project panel, expand the "Lunarcom" folder and drag the "Lunarcom_Base" prefab into your hierarchy.</span></span>

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

12. <span data-ttu-id="4cbb8-142">階層内の"Lunarcom_Base"オブジェクトを選択し、位置が x に設定されていることを確認 = 0、y = 0、および z = 0、x に設定する回転と = 0、y = 0、および z = 0。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-142">Select the "Lunarcom_Base" object in your hierarchy and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="4cbb8-143">読み取りスケールを設定する x = 0.008、y = 0.008、および z 0.01 を =。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-143">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

13. <span data-ttu-id="4cbb8-145">"コンポーネントの追加 をクリックし、検索し、"LunarcomController"を選択します</span><span class="sxs-lookup"><span data-stu-id="4cbb8-145">Click "add component" and search for and select “LunarcomController.”</span></span> <span data-ttu-id="4cbb8-146">このスクリプトは、手順 6. でインポートした Lunarcom 資産パックに含まれます。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-146">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

14. <span data-ttu-id="4cbb8-148">アプリを Azure Cognitive Services に接続するには、必要がありますキーを入力する"サブスクリプション"とも呼ばれます「API キー」の音声サービス。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-148">To connect our app to Azure Cognitive Services, you must enter a "subscription key" also known as an "API Key" for the Speech Service.</span></span> <span data-ttu-id="4cbb8-149">手順に従って[このリンク](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started)無料のサブスクリプション キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-149">Follow the instructions at [this link](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="4cbb8-150">サブスクリプション キーを取得した後は、次の図に示すように、[inspector] パネルで"LunarcomController"のコンポーネントの「音声認識サービス API キー」フィールドに入力します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-150">Once you obtain the subscription key, enter it into the “Speech Service API Key” field of the "LunarcomController" component in the inspector panel, as shown in the image below.</span></span>

15. <span data-ttu-id="4cbb8-151">インスペクター ウィンドウで"LunarcomController"コンポーネントの「音声サービス地域」フィールドにサブスクリプション キーのサインアップ時に選択したリージョンを入力します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-151">Enter the Region that you chose when you signed up for the subscription key into the “Speech Service Region” field of the "LunarcomController" component in the inspector panel.</span></span>

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

16. <span data-ttu-id="4cbb8-153">階層内にはの左側にある矢印をクリックして"Lunarcom_Base"オブジェクトを展開し、「ターミナル」次の図に示すように、その子オブジェクトの同じ操作を行います。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-153">In your hierarchy, expand the "Lunarcom_Base" object by clicking the arrow to the left of it, then do the same for its child object, "Terminal" as shown in the image below.</span></span>

17. <span data-ttu-id="4cbb8-154">"Lunarcom_Base"を選択したら、クリックし、テキストをドラッグ"Lunarcom"階層から「出力テキスト」スロットに"LunarcomController"コンポーネントで、[inspector] パネルで次の図に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-154">While "Lunarcom_Base" is selected, click and drag “Lunarcom Text” from the hierarchy to the "Output Text" slot in the "LunarcomController" component in the inspector panel, as shown in the image below.</span></span>
18. <span data-ttu-id="4cbb8-155">「ターミナル」スロットに「接続機コント ローラー」スロットに"接続 Light"オブジェクト「ターミナル」のオブジェクトと同じことを行うようになりました。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-155">Now do the same thing with the "Terminal" object into the "terminal" slot and the "Connection Light" object to the "Connection Light Controller" slot.</span></span>

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

19. <span data-ttu-id="4cbb8-157">Inspector パネル内の"LunarcomController"スクリプトの「Lunarcom ボタン」セクションの横の矢印をクリックして、3 にサイズを変更し、キーボードの Enter または戻り値のキーを押します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-157">Click the arrow next to the "Lunarcom Buttons" section of the "LunarcomController" script in the inspector panel and change the size to 3 and press the Enter or Return key on your keyboard.</span></span> <span data-ttu-id="4cbb8-158">これにより新しい 3 つの"Element"フィールドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-158">This will cause three new "Element" fields to appear.</span></span>

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

20. <span data-ttu-id="4cbb8-160">階層内の横の矢印をクリックして「Lunarcom ボタン」を展開し、上記と同じプロセスを使用して"LunarcomController"のコンポーネントでそれぞれ 0、1、および 2 の要素の参照に Mic、サテライト、およびロケット gameobject にドラッグしますinspector パネル。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-160">Expand the "Lunarcom Buttons" by clicking the arrow next to it in your hierarchy and, using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references respectively in the "LunarcomController" component in the inspector panel.</span></span> 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

21. <span data-ttu-id="4cbb8-162">階層内の"Lunarcom_Base"オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-162">Select the "Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="4cbb8-163">インスペクター ウィンドウで"コンポーネントの追加 をクリックして、検索し、"LunarcomWakeWordRecognizer。"を選択します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-163">Click “Add Component” in the inspector panel and search for and select “LunarcomWakeWordRecognizer.”</span></span>

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

22. <span data-ttu-id="4cbb8-165">"Wake Word"スロットで「ターミナルをアクティブ化します。」に入力します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-165">In the "Wake Word" slot, type in "Activate Terminal."</span></span> <span data-ttu-id="4cbb8-166">また、"Word を閉じます"スロットでは、「Dismiss ターミナル」で入力します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-166">Also, in the "Dismiss Word" slot, type in "Dismiss Terminal."</span></span>

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="congratulations"></a><span data-ttu-id="4cbb8-168">結論</span><span class="sxs-lookup"><span data-stu-id="4cbb8-168">Congratulations</span></span>

<span data-ttu-id="4cbb8-169">音声認識は、Azure を利用した、アプリケーションでセットアップしました。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-169">You've set up voice recognition in your application, powered by Azure!</span></span> <span data-ttu-id="4cbb8-170">すべての関数が正常に動作することを確認するアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-170">Run the application to ensure all functions are working properly.</span></span> <span data-ttu-id="4cbb8-171">手順 22,「ターミナルをアクティブ化します」で型指定されたウェイクという単語を示すと開始します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-171">Start with saying the wake word you typed in step 22, "Activate Terminal."</span></span> <span data-ttu-id="4cbb8-172">次に、音声認識を起動し、読み上げを開始するには、あるマイク ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-172">Then, select the microphone button to start voice recognition and begin speaking.</span></span> <span data-ttu-id="4cbb8-173">話すと、ターミナルで書き起こし、単語が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-173">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="4cbb8-174">音声認識を停止する [マイク] ボタンをもう一度キーを押します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-174">Press the microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="4cbb8-175">Lunarcom ターミナルを非表示にするには「ターミナル無視」とします。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-175">Say "Dismiss Terminal" to hide the Lunarcom terminal.</span></span> <span data-ttu-id="4cbb8-176">次のレッスンでは、デバイスを利用した音声認識を使用して、Azure の speech SDK がオフラインになった HoloLens 2 のために使用されていない場合に動的に切り替える方法説明します。</span><span class="sxs-lookup"><span data-stu-id="4cbb8-176">In the next lesson, we'll learn how to dynamically switch to using device-powered voice recognition, for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="4cbb8-177">次のレッスン:Speech SDK レッスン 2</span><span class="sxs-lookup"><span data-stu-id="4cbb8-177">Next Lesson: Speech SDK Lesson 2</span></span>](mrlearning-speechSDK-ch2.md)

