---
title: MR Learning ASA モジュール HoloLens 2 Azure 空間アンカー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328092"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="d3c9e-104">Photon (適切な me 私は正しくない場合)</span><span class="sxs-lookup"><span data-stu-id="d3c9e-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="d3c9e-105">このレッスンで</span><span class="sxs-lookup"><span data-stu-id="d3c9e-105">In this lesson,</span></span> 

<span data-ttu-id="d3c9e-106">目標:</span><span class="sxs-lookup"><span data-stu-id="d3c9e-106">Objectives:</span></span>

* <span data-ttu-id="d3c9e-107">について説明します _ _ _ する方法</span><span class="sxs-lookup"><span data-stu-id="d3c9e-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="d3c9e-108">について説明します _ _ _ する方法</span><span class="sxs-lookup"><span data-stu-id="d3c9e-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="d3c9e-109">手順</span><span class="sxs-lookup"><span data-stu-id="d3c9e-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="d3c9e-110">Photon の設定</span><span class="sxs-lookup"><span data-stu-id="d3c9e-110">Setting Up Photon</span></span>

1. <span data-ttu-id="d3c9e-111">セットアップ、 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)アカウント。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-111">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="d3c9e-112">これは、電子メールを置き換えると、いくつかの検証手順をで構成されます。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="d3c9e-114">、サインアップ後は、Sdk をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="d3c9e-115">そのページが、"server"をクリックし、書かれている、「自己ホスト型です」ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="d3c9e-116">下へスクロールし、"server"次の 2 つ目の図に示すようにをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="d3c9e-119">原因となるテキスト ボックスのラベルの付いた表示「お読みください」</span><span class="sxs-lookup"><span data-stu-id="d3c9e-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="d3c9e-120">読み取るしてみてください。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-120">Go ahead and read it.</span></span> <span data-ttu-id="d3c9e-121">完了すると、ダウンロードするには、"downloadSDK"の横にあるリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="d3c9e-123">ダウンロードが完了したら、フォルダーをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="d3c9e-124">エクスプ ローラーを開くと、SDK のフォルダーを公開、したら、SDK フォルダーをコピーします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="d3c9e-125">Windows の c: ドライブに移動し、「サーバーです」と呼ばれる新しいフォルダーを作成する次の手順になります</span><span class="sxs-lookup"><span data-stu-id="d3c9e-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="d3c9e-127">今すぐ、フォルダーを開き、先ほどコピーした SDK のフォルダーを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="d3c9e-129">SDK フォルダーを開きますが完了すると、「展開、」"bin_Win64"しに移動し、「photon コントロール」をダブルクリックします</span><span class="sxs-lookup"><span data-stu-id="d3c9e-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="d3c9e-131">注:IP アドレスについてご質問またはその他同様の質問がある場合は、ツールバーで、情報の大部分を検索し、(次の図に示すように) とにします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="d3c9e-133">サーバーを設定すると、開始されたが、Photon web サイトに戻って「アプリケーションです」を選択してと (次の図でボックス化された) プロファイル アイコンをクリックします</span><span class="sxs-lookup"><span data-stu-id="d3c9e-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="d3c9e-135">アプリケーション ID を作成するには、「新しいアプリの作成」ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="d3c9e-137">「Photon の種類」の下のドロップダウン メニューから [Photon 実行] を選択します</span><span class="sxs-lookup"><span data-stu-id="d3c9e-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="d3c9e-138">名前を付けます、(ものするには注意してください)。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="d3c9e-139">この例では、という名前に"HoloLensPhotonProject"</span><span class="sxs-lookup"><span data-stu-id="d3c9e-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="d3c9e-140">完了すると、クリックして「を作成します」</span><span class="sxs-lookup"><span data-stu-id="d3c9e-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="d3c9e-142">完了すると、アプリケーション ページに戻るし、次の図のような画面を表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="d3c9e-143">アプリケーション ID をクリックし、それをコピーします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="d3c9e-144">貼り付けがどこかに簡単にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="d3c9e-146">新しい unity プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-146">Create a new unity project.</span></span> <span data-ttu-id="d3c9e-147">Unity のハブを開き、"new"をクリックしてください</span><span class="sxs-lookup"><span data-stu-id="d3c9e-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="d3c9e-148">"HLSharingProject"という名前を付けます</span><span class="sxs-lookup"><span data-stu-id="d3c9e-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="d3c9e-149">クリックを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-149">Then click create.</span></span> 

   > <span data-ttu-id="d3c9e-150">注:読み込むには、最大 2 分間、コンピューターの速度に基づいてこれかかることができます。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="d3c9e-152">注:"location"オプションを変更することで、コンピューターで、プロジェクトを保存する場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="d3c9e-153">記憶され、簡単にアクセスする場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="d3c9e-154">プロジェクトが読み込まれたらを「アセット ストア」をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="d3c9e-155">次に、検索ボックスに次の図に示すように、「から」を入力し、「Photon だじゃれ 2 無料」の資産を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="d3c9e-157">ダウンロードしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="d3c9e-159">**Unity プロジェクトの設定**</span><span class="sxs-lookup"><span data-stu-id="d3c9e-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="d3c9e-160">クリックすると、Unity で Photon を設定するために必要な新しい資産をダウンロード[ここです。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="d3c9e-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="d3c9e-161">Unity では、資産 メニューと"資産、import"を選択し、カスタム アセット"をクリックしてください</span><span class="sxs-lookup"><span data-stu-id="d3c9e-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="d3c9e-163">手順 1. で指定されたリンクからダウンロードした Unity パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="d3c9e-164">Unity にインポート ボタンが表示されたら、それをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="d3c9e-166">注: 検索の場所にパッケージをダウンロードした場所になります。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="d3c9e-167">上の図は、パッケージをどこを提示していません。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="d3c9e-168">新しいシーンを作成する (これは、コントロールを使用して元に戻す/コマンド + N または"file"をクリックすると、「新しいシーンです。」を選択して)。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="d3c9e-169">シーンを付けて保存"HLSharedProjectMain"</span><span class="sxs-lookup"><span data-stu-id="d3c9e-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="d3c9e-170">注: 次の図のようなポップアップが表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="d3c9e-171">ここでは、クリックして"no"です。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="d3c9e-173">"Mixed Reality Toolkit"クリック「シーンに追加して構成します」</span><span class="sxs-lookup"><span data-stu-id="d3c9e-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="d3c9e-175">完了すると、新しい構成ファイルが表示され選択してプロファイルをカスタマイズすること。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="d3c9e-176">「コピーし、カスタマイズ」をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="d3c9e-178">下へスクロールし、「診断システムを有効にします。」オフにします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="d3c9e-179">これは、ため、このプロジェクトをセットアップしやすく、されます。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="d3c9e-181">ビルドの設定 (コントロール + shift + B) を開きます。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="d3c9e-182">プログラムが「PC、Mac、Linux のスタンドアロン」プラットフォームで現在設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="d3c9e-183">このプロジェクトで「ユニバーサル windows プラットフォーム」を使用するプラットフォームを設定します。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="d3c9e-184">選択して、「プラットフォームの切り替え」をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="d3c9e-186">完了すると、「開いているシーンを追加します。」と書かれたボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="d3c9e-187">Inspector パネルに移動し、(下図参照) として「サポートされている仮想現実」の右側にあるチェック ボックスを確認するようになりましたがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="d3c9e-189">注:また、"シーン/HLSharedProjectMain"の横にあるチェック ボックスをチェックすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="d3c9e-190">[インスペクター] パネルの「発行の設定」が「機能」までスクロールし、次のチェック ボックスのみがマークされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="d3c9e-191">インターネット クライアント</span><span class="sxs-lookup"><span data-stu-id="d3c9e-191">internet client</span></span>
- <span data-ttu-id="d3c9e-192">インターネット クライアント サーバー</span><span class="sxs-lookup"><span data-stu-id="d3c9e-192">internet client server</span></span>
- <span data-ttu-id="d3c9e-193">プライベート ネットワーク クライアント サーバー</span><span class="sxs-lookup"><span data-stu-id="d3c9e-193">private network client server</span></span>
- <span data-ttu-id="d3c9e-194">カメラ/web カメラ</span><span class="sxs-lookup"><span data-stu-id="d3c9e-194">camera/webcam</span></span>
- <span data-ttu-id="d3c9e-195">マイク</span><span class="sxs-lookup"><span data-stu-id="d3c9e-195">microphone</span></span>

21. <span data-ttu-id="d3c9e-196">12 の手順と同じように次の手順は [こちら] ダウンロードできます「レッスン 2」と呼ばれる別のカスタム パッケージをインポートすること[lesson2.unitypackage リンクをここに挿入]そのパッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="d3c9e-198">ここで、プロジェクト パネルで、フォルダーに移動「プレハブ」、いくつかのプレハブをシーンに次の手順で実装されるためです。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="d3c9e-199">「プレハブ」フォルダーにをクリックし、"DebugWindow"階層に、プレハブをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="d3c9e-200">完了すると、プロジェクトを保存します ([] をクリック ファイルを保存して、またはコントロール + S)。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="d3c9e-202">注:TMP Essentials について質問する、プレハブをクリックすると表示されるポップアップ ウィンドウがあります。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="d3c9e-203">これらが必要になります"インポート TMP Essentials をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="d3c9e-205">**複数のユーザーを接続します。**</span><span class="sxs-lookup"><span data-stu-id="d3c9e-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="d3c9e-206">プロジェクト パネルで、「プレハブ」フォルダー内の 22 の手順と同様に、次の手順にドラッグ アンド ドロップ"NetworkLobby"プレハブ階層には。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="d3c9e-208">"NetworkLobby、"である親プレハブを開くときに子 prefab、"NetworkRoom"が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="d3c9e-209">選択されていると、インスペクター パネルに移動し、「コンポーネントを追加します」をクリックしてください</span><span class="sxs-lookup"><span data-stu-id="d3c9e-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="d3c9e-210">"PhotonView"を検索し、コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="d3c9e-212">階層 (階層し、"empty"内を右クリック) で、新しい空のゲーム オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="d3c9e-213">位置 x に設定されていることを確認 = 0、y = 0、z = 0 およびオブジェクトの名前を"PhotonUser"。</span><span class="sxs-lookup"><span data-stu-id="d3c9e-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="d3c9e-215">結論</span><span class="sxs-lookup"><span data-stu-id="d3c9e-215">Congratulations</span></span>



