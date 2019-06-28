<span data-ttu-id="b8c9f-101">**Unity の開発の準備**</span><span class="sxs-lookup"><span data-stu-id="b8c9f-101">**Getting Unity Ready for Development**</span></span> 

<span data-ttu-id="b8c9f-102">このレッスンでは、Mixed Reality ツールキットをインポート、ビルドの設定を構成して、シーンの準備を含む、アプリ開発用の Unity の構成を準備の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-102">In this lesson, we will learn how to prepare and configure Unity for app development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="b8c9f-103">目標:</span><span class="sxs-lookup"><span data-stu-id="b8c9f-103">Objectives:</span></span>

- <span data-ttu-id="b8c9f-104">アプリ開発用の Unity を構成します。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-104">Configure Unity for app development</span></span>

- <span data-ttu-id="b8c9f-105">Mixed Reality ツールキットをインポートする</span><span class="sxs-lookup"><span data-stu-id="b8c9f-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="b8c9f-106">プロジェクト シーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="b8c9f-107">手順</span><span class="sxs-lookup"><span data-stu-id="b8c9f-107">Instructions</span></span>

1. <span data-ttu-id="b8c9f-108">ダウンロードし、クリックして、Mixed Reality Toolkit unity パッケージを保存[ここです。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="b8c9f-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>
2. <span data-ttu-id="b8c9f-109">Unity では、[資産] メニューをクリックし、パッケージのインポート"、"を選択し、「カスタム パッケージです」をクリックしてください</span><span class="sxs-lookup"><span data-stu-id="b8c9f-109">In Unity, click on the assets menu and select "Import Package," then click on "Custom Package."</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="b8c9f-111">手順 1. で指定されたリンクからダウンロードした Unity パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="b8c9f-112">Unity にインポートのポップアップ ウィンドウが表示されると、インポートを開始する [インポート] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-112">Once the import pop-up window appears in Unity, click the import button to begin importing.</span></span> <span data-ttu-id="b8c9f-113">MRTK をインポートするには数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="b8c9f-115">注:ダウンロードしたパッケージは、ファイルを保存したローカル フォルダーになります。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-115">Note: The downloaded package will be in your local folder where you have saved the file.</span></span> <span data-ttu-id="b8c9f-116">上の図は、パッケージをどこを提示していません。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="b8c9f-117">(これを行う"file"をクリックし、「新しいシーン」を選択)、新しいシーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-117">Create a new scene (this can be done by clicking "file" and selecting "new scene").</span></span> <span data-ttu-id="b8c9f-118">シーンを付けて保存"HLSharedProjectMain"</span><span class="sxs-lookup"><span data-stu-id="b8c9f-118">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="b8c9f-119">注: 次の図のようなポップアップが表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-119">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="b8c9f-120">ここでは、クリックするだけ「いいえ」</span><span class="sxs-lookup"><span data-stu-id="b8c9f-120">For now, just click "No."</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="b8c9f-122">"Mixed Reality Toolkit"クリック「シーンに追加して構成します」</span><span class="sxs-lookup"><span data-stu-id="b8c9f-122">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="b8c9f-124">完了すると、新しい構成ファイルが表示され選択してプロファイルをカスタマイズすること。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-124">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="b8c9f-125">「コピーし、カスタマイズ」をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-125">Click "copy and customize."</span></span>

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="b8c9f-129">下へスクロールし、「有効化」診断システムに診断ウィンドウを非表示にする場合をオフにします。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-129">Scroll down and uncheck "enable diagnostics system" if you would like to hide the diagnostics window.</span></span> <span data-ttu-id="b8c9f-130">パフォーマンスを監視するアプリの開発時に有効になっており、運用環境やアプリケーションのデモンストレーションの中に無効にすると、診断ウィンドウを維持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-130">We recommend keeping the diagnostics window enabled during app development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="b8c9f-132">ビルドの設定コントロール + shift + B を押すか、ファイルを開く > ビルドの設定。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-132">Open the build settings by pressing control+shift+B or going to File>Build Settings.</span></span> <span data-ttu-id="b8c9f-133">プログラムが「PC、Mac、Linux のスタンドアロン」プラットフォームで現在設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-133">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="b8c9f-134">「ユニバーサル Windows プラットフォーム」を使用するプラットフォームを設定すると、HoloLens 2 開発用</span><span class="sxs-lookup"><span data-stu-id="b8c9f-134">For HoloLens 2 development, set the platform to be "Universal Windows Platform."</span></span> <span data-ttu-id="b8c9f-135">選択して、「プラットフォームの切り替え」をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-135">Select it and click "switch platform."</span></span>![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="b8c9f-137">完了すると、「開いているシーンを追加します。」と書かれたボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-137">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="b8c9f-138">Inspector パネルに移動し、(下図参照) として「サポートされている仮想現実」の右側にあるチェック ボックスを確認するようになりましたがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-138">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> <span data-ttu-id="b8c9f-139">また、"シーン/HLSharedProjectMain"の横にあるチェック ボックスがオンも次の図に示すように。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-139">Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked, as shown in the image below.</span></span>![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="b8c9f-141">"発行の設定 の下で「機能」までインスペクター パネル スクロール セクションし、次のチェック ボックスがマークされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-141">Under the "Publishing Settings" section in the inspector panel scroll down to "Capabilities" and ensure the following check boxes are marked:</span></span>![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="b8c9f-143">ダウンロードできる"SharingAssetCollection"と呼ばれるカスタム パッケージをインポート[ここ](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)。![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span><span class="sxs-lookup"><span data-stu-id="b8c9f-143">Import the custom package called "SharingAssetCollection" which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span></span>

12. <span data-ttu-id="b8c9f-144">ここで、プロジェクト パネルで、フォルダーに移動「プレハブ」、いくつかのプレハブをシーンに次の手順で実装されるためです。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-144">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="b8c9f-145">「プレハブ」フォルダーにをクリックし、"DebugWindow"階層に、プレハブをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-145">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="b8c9f-146">完了すると、プロジェクトを保存 (ファイル、 をクリックし、保存、またはコントロール + S キーを押します)</span><span class="sxs-lookup"><span data-stu-id="b8c9f-146">Once finished, save the project (click file, then save, or press control+S)</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="b8c9f-148">注:TMP Essentials について質問する、プレハブをクリックすると表示されるポップアップ ウィンドウがあります。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-148">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="b8c9f-149">これらが必要になります"インポート TMP Essentials をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-149">Click "Import TMP Essentials" as they will be needed.</span></span> <span data-ttu-id="b8c9f-150">このポップアップが表示されている場合は、階層からプレハブを削除し再潜在的なテキストに関連するエラーを回避するために、階層にドラッグする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-150">If this pop-up appears, you may need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="b8c9f-152">結論</span><span class="sxs-lookup"><span data-stu-id="b8c9f-152">Congratulations</span></span>

<span data-ttu-id="b8c9f-153">Unity プロジェクトは Photon 準備ができました!</span><span class="sxs-lookup"><span data-stu-id="b8c9f-153">Your Unity Project is now ready for Photon!</span></span> <span data-ttu-id="b8c9f-154">今後のレッスンでは、このシーンと共有のエクスペリエンスを完全に Unity プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b8c9f-154">In the coming lessons, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="b8c9f-155">[次のレッスン:Sharing(Photon) レッスン 3](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="b8c9f-155">[Next Lesson: Sharing(Photon) Lesson 3](mrlearning-sharing(photon)-ch3.md)</span></span>

