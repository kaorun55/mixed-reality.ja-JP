# <a name="getting-unity-ready-for-development"></a><span data-ttu-id="54c46-101">Unity の開発の準備</span><span class="sxs-lookup"><span data-stu-id="54c46-101">Getting Unity ready for development</span></span> 

<span data-ttu-id="54c46-102">このチュートリアルでは、準備し、Mixed Reality ツールキットをインポート、ビルドの設定を構成して、シーンの準備など、アプリケーション開発の Unity を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="54c46-102">In this tutorial, we learn how to prepare and configure Unity for applicaiton development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="54c46-103">目標:</span><span class="sxs-lookup"><span data-stu-id="54c46-103">Objectives:</span></span>

- <span data-ttu-id="54c46-104">アプリケーション開発のための Unity を構成します。</span><span class="sxs-lookup"><span data-stu-id="54c46-104">Configure Unity for applicaiton development</span></span>

- <span data-ttu-id="54c46-105">Mixed Reality ツールキットをインポートする</span><span class="sxs-lookup"><span data-stu-id="54c46-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="54c46-106">プロジェクト シーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="54c46-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="54c46-107">手順</span><span class="sxs-lookup"><span data-stu-id="54c46-107">Instructions</span></span>

1. <span data-ttu-id="54c46-108">ダウンロードし、クリックして、Mixed Reality Toolkit unity パッケージを保存[ここです。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="54c46-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>
2. <span data-ttu-id="54c46-109">Unity では、[アセット] メニューをクリックし、パッケージのインポートしてカスタム パッケージをクリックします。</span><span class="sxs-lookup"><span data-stu-id="54c46-109">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="54c46-111">手順 1. で指定されたリンクからダウンロードした Unity パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="54c46-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="54c46-112">Unity にインポートのポップアップ ウィンドウが表示されると、インポートを開始する [インポート] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="54c46-112">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="54c46-113">MRTK をインポートするには数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="54c46-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="54c46-115">注:ダウンロードしたパッケージは、ファイルを保存したローカル フォルダーには。</span><span class="sxs-lookup"><span data-stu-id="54c46-115">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="54c46-116">上の図は、パッケージをどこを提示していません。</span><span class="sxs-lookup"><span data-stu-id="54c46-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="54c46-117">新しいシーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="54c46-117">Create a new scene.</span></span> <span data-ttu-id="54c46-118">%T この行うファイルをクリックすると、新しいシーンを選択して")。</span><span class="sxs-lookup"><span data-stu-id="54c46-118">Tthis can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="54c46-119">HLSharedProjectMain としてシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="54c46-119">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="54c46-120">注: 次の図のようなポップアップが表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="54c46-120">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="54c46-121">ここでは、次のようにクリックします。 いいえ。</span><span class="sxs-lookup"><span data-stu-id="54c46-121">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="54c46-123">混合の現実 Toolkit では、シーンおよび構成する追加をクリックします。</span><span class="sxs-lookup"><span data-stu-id="54c46-123">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="54c46-125">完了すると、新しい構成ファイルが表示され、プロファイルをカスタマイズするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="54c46-125">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="54c46-126">[コピー] をクリックし、カスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="54c46-126">Click Copy and Customize.</span></span>

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="54c46-130">下へスクロールし、[診断] ウィンドウを非表示にする場合は、Siagnostics を有効にするシステムをオフにします。</span><span class="sxs-lookup"><span data-stu-id="54c46-130">Scroll down and uncheck Enable Siagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="54c46-131">パフォーマンスを監視するアプリケーション開発時に有効になっており、運用環境やアプリケーションのデモンストレーションの中に無効にすると、診断ウィンドウを維持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="54c46-131">We recommend keeping the diagnostics window enabled during applicaiton development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="54c46-133">-> Build Settings をコントロール + shift + B を押すか、ファイルをビルド設定の開いています。</span><span class="sxs-lookup"><span data-stu-id="54c46-133">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="54c46-134">プログラムが、PC、Mac、Linux のスタンドアロン プラットフォームで現在設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="54c46-134">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="54c46-135">HoloLens 2 の開発用ユニバーサル Windows プラットフォームにするプラットフォームを設定します。</span><span class="sxs-lookup"><span data-stu-id="54c46-135">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="54c46-136">選択し、[Switch Platform] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="54c46-136">Select it and click Switch Platform.</span></span>![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="54c46-138">完了すると、開いているシーンを追加することを示すボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="54c46-138">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="54c46-139">今すぐ、[Inspector] パネルに移動し、仮想現実ようサポートされてください (下図) の右側にチェック ボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="54c46-139">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="54c46-140">また、シーン/HLSharedProjectMain 横のチェック ボックスは、次の図に示すようにチェックも確認します。</span><span class="sxs-lookup"><span data-stu-id="54c46-140">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="54c46-142">Inspector パネルの 発行の設定 セクションでは、機能、までスクロールし、次のチェック ボックスがマークされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="54c46-142">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="54c46-144">ダウンロードできる SharingAssetCollection と呼ばれるカスタム パッケージをインポート[ここ](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)。![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span><span class="sxs-lookup"><span data-stu-id="54c46-144">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span></span>

12. <span data-ttu-id="54c46-145">プロジェクト パネル Prefabs フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="54c46-145">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="54c46-146">次の手順では、シーンにいくつかのプレハブを実装します。</span><span class="sxs-lookup"><span data-stu-id="54c46-146">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="54c46-147">Prefabs フォルダー をクリックし、プレハブは、階層にデバッグ ウィンドウをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="54c46-147">In the Prefabs folder, click and drag the prefab, DebugWindow into the hierarchy.</span></span> <span data-ttu-id="54c46-148">完了すると、clckin ファイルで、プロジェクトを保存し、保存またはコントロール + S キーを押します。</span><span class="sxs-lookup"><span data-stu-id="54c46-148">Once finished, save the project by clckin File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="54c46-150">注:TMP Essentials について質問する、プレハブをクリックすると表示されるポップアップ ウィンドウがあります。</span><span class="sxs-lookup"><span data-stu-id="54c46-150">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="54c46-151">必要に応じて、インポート TMP Essentials をクリックします。</span><span class="sxs-lookup"><span data-stu-id="54c46-151">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="54c46-152">このポップアップが表示されている場合は、階層からプレハブを削除し再潜在的なテキストに関連するエラーを回避するために、階層にドラッグする必要があります。</span><span class="sxs-lookup"><span data-stu-id="54c46-152">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="54c46-154">結論</span><span class="sxs-lookup"><span data-stu-id="54c46-154">Congratulations</span></span>

<span data-ttu-id="54c46-155">Unity プロジェクトは、Photon の準備ができました。</span><span class="sxs-lookup"><span data-stu-id="54c46-155">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="54c46-156">今後のチュートリアルでは、このシーンと共有のエクスペリエンスを完全に Unity プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="54c46-156">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="54c46-157">[次のチュートリアル:複数のユーザーを接続します。](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="54c46-157">[Next tutorial: Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

