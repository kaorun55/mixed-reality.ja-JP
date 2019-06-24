---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327183"
---
# <a name="setting-up-photon"></a><span data-ttu-id="626d2-104">Photon の設定</span><span class="sxs-lookup"><span data-stu-id="626d2-104">Setting Up Photon</span></span>

<span data-ttu-id="626d2-105">このレッスンでは、Photon Unity Networking (だじゃれ) を Unity プロジェクトにインポートすると、共有のエクスペリエンスを作成するための準備の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="626d2-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="626d2-106">Photon はいくつかのネットワーク オプション Mixed Reality 開発者が利用できる共有のエクスペリエンスを作成するのです。</span><span class="sxs-lookup"><span data-stu-id="626d2-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="626d2-107">私たちは Photon アカウントを作成、インポート Photon、および省略可能なローカル サーバーを作成する方法を説明します</span><span class="sxs-lookup"><span data-stu-id="626d2-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="626d2-108">目標:</span><span class="sxs-lookup"><span data-stu-id="626d2-108">Objectives:</span></span>

* <span data-ttu-id="626d2-109">Photon アカウントを作成する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="626d2-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="626d2-110">検索して Photon Unity ネットワークをインポートする方法について説明します</span><span class="sxs-lookup"><span data-stu-id="626d2-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="626d2-111">ローカル Photon サーバーを設定します。</span><span class="sxs-lookup"><span data-stu-id="626d2-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="626d2-112">Photon の設定</span><span class="sxs-lookup"><span data-stu-id="626d2-112">Setting Up Photon</span></span>

1. <span data-ttu-id="626d2-113">セットアップ、 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)アカウント。</span><span class="sxs-lookup"><span data-stu-id="626d2-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="626d2-114">クリックして、Photon のサインアップ ページに移動します[このリンク](https://dashboard.photonengine.com/en-US/Account/SignUp)します。</span><span class="sxs-lookup"><span data-stu-id="626d2-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="626d2-115">サインアップ ページ、アカウントを作成するには、指示に従います。</span><span class="sxs-lookup"><span data-stu-id="626d2-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. <span data-ttu-id="626d2-117">、サインアップ後は、Sdk をクリックします。</span><span class="sxs-lookup"><span data-stu-id="626d2-117">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="626d2-118">そのページが、"server"をクリックし、書かれている、「自己ホスト型です」ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="626d2-118">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="626d2-119">下へスクロールし、"server"次の 2 つ目の図に示すようにをクリックします。</span><span class="sxs-lookup"><span data-stu-id="626d2-119">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. <span data-ttu-id="626d2-122">原因となるテキスト ボックスのラベルの付いた表示「お読みください」</span><span class="sxs-lookup"><span data-stu-id="626d2-122">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="626d2-123">読み取るしてみてください。</span><span class="sxs-lookup"><span data-stu-id="626d2-123">Go ahead and read it.</span></span> <span data-ttu-id="626d2-124">完了すると、ダウンロードするには、"downloadSDK"の横にあるリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="626d2-124">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. <span data-ttu-id="626d2-126">ダウンロードが完了したら、フォルダーをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="626d2-126">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="626d2-127">エクスプ ローラーを開くと、SDK のフォルダーを公開、したら、SDK フォルダーをコピーします。</span><span class="sxs-lookup"><span data-stu-id="626d2-127">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="626d2-128">Windows の c: ドライブに移動し、「サーバーです」と呼ばれる新しいフォルダーを作成する次の手順になります</span><span class="sxs-lookup"><span data-stu-id="626d2-128">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - <span data-ttu-id="626d2-130">今すぐ、フォルダーを開き、先ほどコピーした SDK のフォルダーを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="626d2-130">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. <span data-ttu-id="626d2-132">SDK フォルダーを開きますが完了すると、「展開、」"bin_Win64"しに移動し、「photon コントロール」をダブルクリックします</span><span class="sxs-lookup"><span data-stu-id="626d2-132">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> <span data-ttu-id="626d2-134">注:IP アドレスについてご質問またはその他同様の質問がある場合は、ツールバーで、情報の大部分を検索し、(次の図に示すように) とにします。</span><span class="sxs-lookup"><span data-stu-id="626d2-134">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. <span data-ttu-id="626d2-136">サーバーを設定すると、開始されたが、Photon web サイトに戻ると署名されても確認します (またはない場合にもう一度サインイン)。(次の図の右上隅でボックス化された) プロファイル アイコンをクリックし、「アプリケーションです。」を選択します。</span><span class="sxs-lookup"><span data-stu-id="626d2-136">Now that the server is set up and initiated, go back to the Photon website and ensure that you are still signed in (or sign back in, if you are not.) Click on the profile icon (boxed in the top right corner of the image below) and select "your applications."</span></span>
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. <span data-ttu-id="626d2-138">アプリケーション ID を作成するには、「新しいアプリの作成」ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="626d2-138">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - <span data-ttu-id="626d2-140">「Photon の種類」の下のドロップダウン メニューから「Photon だじゃれ」を選択します。</span><span class="sxs-lookup"><span data-stu-id="626d2-140">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="626d2-141">名前、この例では、"HoloLensPhotonProject"という</span><span class="sxs-lookup"><span data-stu-id="626d2-141">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="626d2-142">完了すると、[作成] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="626d2-142">Once finished, click the "CREATE" button.</span></span>

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. <span data-ttu-id="626d2-144">完了すると、アプリケーション ページに戻るし、次の図のような画面を表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="626d2-144">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="626d2-145">アプリケーション ID をクリックし、それをコピーします。</span><span class="sxs-lookup"><span data-stu-id="626d2-145">Click on the app ID and copy it.</span></span> <span data-ttu-id="626d2-146">貼り付けがどこかに簡単にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="626d2-146">Paste is somewhere you can easily access.</span></span>  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. <span data-ttu-id="626d2-148">新しい unity プロジェクトを作成し、"HLSharingProject"という名前を付けます</span><span class="sxs-lookup"><span data-stu-id="626d2-148">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="626d2-149">新しい Unity プロジェクトを作成する方法についてを参照してください[「Unity プロジェクトの作成」セクションのベース モジュールの](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)します。</span><span class="sxs-lookup"><span data-stu-id="626d2-149">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 


10. <span data-ttu-id="626d2-150">プロジェクトが読み込まれたらは、次の図に示すように、「資産ストア」タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="626d2-150">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="626d2-151">次に、次の図で強調表示されている検索ボックスに「から」を入力し、検索結果から「Photon だじゃれ 2 無料」の資産を選択します。</span><span class="sxs-lookup"><span data-stu-id="626d2-151">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset from the search results.</span></span> 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. <span data-ttu-id="626d2-153">ダウンロードし、[ダウンロード] と [インポート] ボタンを押してこのアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="626d2-153">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="626d2-155">結論</span><span class="sxs-lookup"><span data-stu-id="626d2-155">Congratulations</span></span>

<span data-ttu-id="626d2-156">Photon アカウントを作成して、ローカル Photon サーバーをセットアップ、およびだじゃれを Unity にインポートが正常が。</span><span class="sxs-lookup"><span data-stu-id="626d2-156">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="626d2-157">次の手順では、プロジェクトを設定して、複数のユーザーは、作業内容を確認できるように他のユーザーとの接続を許可します。</span><span class="sxs-lookup"><span data-stu-id="626d2-157">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="626d2-158">[次のレッスン:Sharing(Photon) レッスン 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="626d2-158">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

