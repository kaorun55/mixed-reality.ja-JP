---
title: MR Learning ASA モジュール Azure 空間アンカー (HoloLens 2)
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
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="8e3a4-104">Photon (間違っている場合は修正)</span><span class="sxs-lookup"><span data-stu-id="8e3a4-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="8e3a4-105">このレッスンでは、</span><span class="sxs-lookup"><span data-stu-id="8e3a4-105">In this lesson,</span></span> 

<span data-ttu-id="8e3a4-106">事項</span><span class="sxs-lookup"><span data-stu-id="8e3a4-106">Objectives:</span></span>

* <span data-ttu-id="8e3a4-107">詳細については、こちらを参照してください。 __ __ を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="8e3a4-108">詳細については、こちらを参照してください。 __ を参照してください。 __ __。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="8e3a4-109">手順</span><span class="sxs-lookup"><span data-stu-id="8e3a4-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="8e3a4-110">Photon の設定</span><span class="sxs-lookup"><span data-stu-id="8e3a4-110">Setting Up Photon</span></span>

1. <span data-ttu-id="8e3a4-111">[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)アカウントを設定します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-111">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="8e3a4-112">これを行うには、電子メールを送信し、いくつかの検証手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="8e3a4-114">サインアップしたら、[Sdk] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="8e3a4-115">このページが表示されたら、[サーバー] をクリックし、"自己ホスト型" と表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="8e3a4-116">下にスクロールし、次の2番目の図に示すように、[サーバー] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="8e3a4-119">これにより、テキストボックスに "read me" というラベルが付けられます。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="8e3a4-120">こちらからお読みください。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-120">Go ahead and read it.</span></span> <span data-ttu-id="8e3a4-121">完了したら、"downloadSDK" の横にあるリンクをクリックしてダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="8e3a4-123">ダウンロードが完了したら、フォルダーをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="8e3a4-124">ファイルエクスプローラーで SDK フォルダーが表示されたら、SDK フォルダーをコピーします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="8e3a4-125">次の手順では、windows C: ドライブにアクセスし、"server" という名前の新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="8e3a4-127">ここで、フォルダーを開き、先ほどコピーした SDK フォルダーを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="8e3a4-129">この操作が完了したら、SDK フォルダーを開き、[deploy]、[bin_Win64] の順に選択し、[photon control] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="8e3a4-131">注:IP アドレスについて質問がある場合、またはその他の同様の質問がある場合は、ツールバーでほとんどの情報を確認できます (次の図を参照)。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="8e3a4-133">サーバーがセットアップされ、開始されたので、Photon の web サイトに戻り、プロファイルアイコン (下の図のボックス) をクリックして、[your applications] \ (アプリケーション \) を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="8e3a4-135">[新しいアプリの作成] ボタンをクリックして、アプリケーション ID を作成します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="8e3a4-137">[Photon type] の下にあるドロップダウンメニューから [Photon RUN] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="8e3a4-138">次に、名前 (覚えているもの) を指定します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="8e3a4-139">この例では、"HoloLensPhotonProject" という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="8e3a4-140">完了したら、[作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="8e3a4-142">この操作が完了すると、アプリケーションのページに戻り、次の図のような結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="8e3a4-143">アプリ ID をクリックしてコピーします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="8e3a4-144">貼り付けは、簡単にアクセスできる任意の場所にあります。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="8e3a4-146">新しい unity プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-146">Create a new unity project.</span></span> <span data-ttu-id="8e3a4-147">Unity Hub を開き、[new] \ (新規 \) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="8e3a4-148">"HLSharingProject" という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="8e3a4-149">[作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-149">Then click create.</span></span> 

   > <span data-ttu-id="8e3a4-150">付箋コンピューターの速度によっては、読み込みに最大2分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="8e3a4-152">注: [場所] オプションを変更して、コンピューターにプロジェクトを保存する場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="8e3a4-153">覚えやすい場所に保存して、簡単にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="8e3a4-154">プロジェクトが読み込まれたら、[assets ストア] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="8e3a4-155">次に、下の画像に示されている検索ボックスに「さしあたっ」と入力し、"Photon さしあたっ-2 FREE" 資産を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="8e3a4-157">ダウンロードしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="8e3a4-159">**Unity プロジェクトの設定**</span><span class="sxs-lookup"><span data-stu-id="8e3a4-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="8e3a4-160">Unity で Photon を設定するために必要な新しい資産をダウンロードするには、ここをクリック[してください。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="8e3a4-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="8e3a4-161">Unity で、[アセット] メニューをクリックし、[アセットのインポート] を選択して、[カスタムアセット] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="8e3a4-163">手順 1. で指定したリンクからダウンロードした Unity パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="8e3a4-164">Unity に [インポート] ボタンが表示されたら、それをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="8e3a4-166">メモ: パッケージをダウンロードした場所はどこにありますか。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="8e3a4-167">上の図では、パッケージを検索する場所はされるません。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="8e3a4-168">新しいシーンを作成します (これを行うには、control/command + N を使用するか、[ファイル] をクリックして [新しいシーン] を選択します)。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="8e3a4-169">シーンを "HLSharedProjectMain" として保存します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="8e3a4-170">注: 次の図のようなポップアップが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="8e3a4-171">ここでは、[いいえ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="8e3a4-173">"Mixed Reality Toolkit" で、[シーンに追加して構成する] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="8e3a4-175">この処理が完了すると、新しい構成ファイルが表示され、プロファイルをカスタマイズするためのオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="8e3a4-176">[コピーとカスタマイズ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="8e3a4-178">下にスクロールし、[診断システムを有効にする] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="8e3a4-179">これにより、このプロジェクトのセットアップが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="8e3a4-181">ビルド設定を開きます (ctrl + shift + B)。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="8e3a4-182">このプログラムは、現在、"PC, Mac および Linux スタンドアロン" プラットフォームで設定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="8e3a4-183">このプロジェクトの場合は、プラットフォームを "ユニバーサル windows プラットフォーム" に設定します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="8e3a4-184">それを選択し、[switch platform] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="8e3a4-186">完了したら、[open シーンの追加] というボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="8e3a4-187">次に、[インスペクター] パネルにアクセスし、[virtual reality がサポートされています] の右側にあるチェックボックスがオンになっていることを確認します (下図を参照)。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="8e3a4-189">付箋また、[シーン/HLSharedProjectMain] の横にあるチェックボックスもオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="8e3a4-190">[インスペクター] パネルの [発行の設定] で、[機能] まで下にスクロールし、次のチェックボックスのみがマークされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="8e3a4-191">インターネットクライアント</span><span class="sxs-lookup"><span data-stu-id="8e3a4-191">internet client</span></span>
- <span data-ttu-id="8e3a4-192">インターネットクライアントサーバー</span><span class="sxs-lookup"><span data-stu-id="8e3a4-192">internet client server</span></span>
- <span data-ttu-id="8e3a4-193">プライベートネットワーククライアントサーバー</span><span class="sxs-lookup"><span data-stu-id="8e3a4-193">private network client server</span></span>
- <span data-ttu-id="8e3a4-194">カメラ/webcam</span><span class="sxs-lookup"><span data-stu-id="8e3a4-194">camera/webcam</span></span>
- <span data-ttu-id="8e3a4-195">マイク</span><span class="sxs-lookup"><span data-stu-id="8e3a4-195">microphone</span></span>

21. <span data-ttu-id="8e3a4-196">手順12と同じように、次の手順では、"レッスン 2" という名前の別のカスタムパッケージをインポートします。このパッケージはダウンロードできます (こちらを参照)。[レッスン 2. unitypackage link here]そのパッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="8e3a4-198">次に、[プロジェクト] パネルで、"prefabs" フォルダーにアクセスします。これは、次のいくつかの手順で、いくつかの prefabs をシーンに実装するためです。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="8e3a4-199">"Prefabs" フォルダーで、prefab "DebugWindow" をクリックして階層にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="8e3a4-200">完了したら、プロジェクトを保存します ([ファイル]、[保存]、または [コントロール + S] をクリックします)。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="8e3a4-202">付箋Prefab をクリックするとポップアップが表示され、TMP Essentials について質問されることがあります。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="8e3a4-203">必要に応じて [Import TMP Essentials] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="8e3a4-205">**複数のユーザーの接続**</span><span class="sxs-lookup"><span data-stu-id="8e3a4-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="8e3a4-206">手順 22. と同じように、[プロジェクト] パネルの "prefabs" フォルダーで、次の手順では、"NetworkLobby" の事前 fab を階層にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="8e3a4-208">親 prefab "NetworkLobby" を開くと、子 prefab "Networklobby" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="8e3a4-209">選択した状態で、[インスペクター] パネルにアクセスし、[コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="8e3a4-210">"PhotonView" を検索し、コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="8e3a4-212">階層内に新しい空のゲームオブジェクトを作成します (階層内を右クリックし、[空] を選択します)。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="8e3a4-213">位置が x = 0、y = 0、z = 0 に設定されていることを確認し、オブジェクトに "PhotonUser" という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="8e3a4-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="8e3a4-215">結論</span><span class="sxs-lookup"><span data-stu-id="8e3a4-215">Congratulations</span></span>



