# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="cb17c-101">2. Unity を開発用に準備する</span><span class="sxs-lookup"><span data-stu-id="cb17c-101">2. Getting Unity ready for development</span></span> 


<span data-ttu-id="cb17c-102">このチュートリアルでは、Mixed Reality Toolkit のインポート、ビルド設定の構成、シーンの準備など、アプリケーション開発のために Unity を準備して構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb17c-102">In this tutorial, we learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="cb17c-103">事項</span><span class="sxs-lookup"><span data-stu-id="cb17c-103">Objectives:</span></span>

- <span data-ttu-id="cb17c-104">アプリケーション開発のための Unity の構成</span><span class="sxs-lookup"><span data-stu-id="cb17c-104">Configure Unity for application development</span></span>

- <span data-ttu-id="cb17c-105">Mixed Reality ツールキットをインポートする</span><span class="sxs-lookup"><span data-stu-id="cb17c-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="cb17c-106">プロジェクトシーンを準備する</span><span class="sxs-lookup"><span data-stu-id="cb17c-106">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="cb17c-107">手順</span><span class="sxs-lookup"><span data-stu-id="cb17c-107">Instructions</span></span>

1. <span data-ttu-id="cb17c-108">ここをクリックして、Mixed Reality Toolkit unity パッケージをダウンロードして保存し[ます。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="cb17c-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>

2. <span data-ttu-id="cb17c-109">Unity で、[アセット] メニューをクリックし、[パッケージのインポート] をクリックして、[カスタムパッケージ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb17c-109">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="cb17c-111">手順 1. で指定したリンクからダウンロードした Unity パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="cb17c-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="cb17c-112">[インポート] ポップアップウィンドウが Unity に表示されたら、[インポート] ボタンをクリックしてインポートを開始します。</span><span class="sxs-lookup"><span data-stu-id="cb17c-112">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="cb17c-113">MRTK のインポートには数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cb17c-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="cb17c-115">注:ダウンロードしたパッケージは、ファイルを保存したローカルフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="cb17c-115">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="cb17c-116">上の図では、パッケージを検索する場所はされるません。</span><span class="sxs-lookup"><span data-stu-id="cb17c-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="cb17c-117">新しいシーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb17c-117">Create a new scene.</span></span> <span data-ttu-id="cb17c-118">これを行うには、[ファイル] をクリックし、[新しいシーン] を選択します)。</span><span class="sxs-lookup"><span data-stu-id="cb17c-118">This can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="cb17c-119">シーンを HLSharedProjectMain として保存します。</span><span class="sxs-lookup"><span data-stu-id="cb17c-119">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="cb17c-120">注: 次の図のようなポップアップが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="cb17c-120">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="cb17c-121">ここでは、[いいえ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb17c-121">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="cb17c-123">Mixed Reality Toolkit の [シーンに追加] をクリックし、[構成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb17c-123">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="cb17c-125">この処理が完了すると、新しい構成ファイルが表示され、プロファイルをカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="cb17c-125">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="cb17c-126">[コピーとカスタマイズ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb17c-126">Click Copy and Customize.</span></span>

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="cb17c-130">[診断] ウィンドウを非表示にする場合は、下にスクロールし、[診断システムを有効にする] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="cb17c-130">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="cb17c-131">アプリケーションの開発中に、パフォーマンスを監視し、運用またはアプリケーションのデモンストレーション中に無効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cb17c-131">We recommend keeping the diagnostics window enabled during application development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="cb17c-133">Ctrl + shift + B キーを押すか、[ファイル > ビルド設定] に移動して、ビルド設定を開きます。</span><span class="sxs-lookup"><span data-stu-id="cb17c-133">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="cb17c-134">プログラムは、現在 PC、Mac、および Linux スタンドアロンプラットフォームで設定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cb17c-134">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="cb17c-135">HoloLens 2 開発の場合は、プラットフォームをユニバーサル Windows プラットフォームに設定します。</span><span class="sxs-lookup"><span data-stu-id="cb17c-135">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="cb17c-136">それを選択し、[プラットフォームの切り替え] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb17c-136">Select it and click Switch Platform.</span></span>

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="cb17c-138">完了したら、[Open シーンの追加] というボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb17c-138">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="cb17c-139">次に、[インスペクター] パネルにアクセスし、[サポートされている仮想現実 (下の図を参照)] の右側にあるチェックボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cb17c-139">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="cb17c-140">また、次の図に示すように、[シーン/HLSharedProjectMain] の横のチェックボックスもオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cb17c-140">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="cb17c-142">[インスペクター] パネルの [発行の設定] セクションで、[機能] まで下にスクロールし、次のチェックボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cb17c-142">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="cb17c-144">ここでダウンロードできる SharingAssetCollection というカスタムパッケージをインポートし[ます。](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span><span class="sxs-lookup"><span data-stu-id="cb17c-144">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span></span>

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. <span data-ttu-id="cb17c-146">[プロジェクト] パネルで、Prefabs フォルダーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="cb17c-146">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="cb17c-147">次のいくつかの手順では、いくつかの prefabs をシーンに実装します。</span><span class="sxs-lookup"><span data-stu-id="cb17c-147">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="cb17c-148">Prefabs フォルダーで、[prefab]、[デバッグ] ウィンドウをクリックし、階層にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="cb17c-148">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="cb17c-149">完了したら、[ファイル] をクリックし、[保存] をクリックしてプロジェクトを保存するか、ctrl + S キーを押します。</span><span class="sxs-lookup"><span data-stu-id="cb17c-149">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="cb17c-151">注:Prefab をクリックするとポップアップが表示され、TMP Essentials について質問されることがあります。</span><span class="sxs-lookup"><span data-stu-id="cb17c-151">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="cb17c-152">必要に応じて、[TMP Essentials のインポート] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb17c-152">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="cb17c-153">このポップアップが表示された場合は、テキスト関連のエラーが発生しないように、階層から prefab を削除し、階層に再ドラッグする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="cb17c-153">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="cb17c-155">結論</span><span class="sxs-lookup"><span data-stu-id="cb17c-155">Congratulations</span></span>

<span data-ttu-id="cb17c-156">Unity プロジェクトは Photon の準備ができました。</span><span class="sxs-lookup"><span data-stu-id="cb17c-156">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="cb17c-157">今後のチュートリアルでは、このシーンと Unity プロジェクトを完全な共有エクスペリエンスに向けて構築します。</span><span class="sxs-lookup"><span data-stu-id="cb17c-157">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="cb17c-158">[次のチュートリアル:3.複数ユーザーの接続](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="cb17c-158">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

