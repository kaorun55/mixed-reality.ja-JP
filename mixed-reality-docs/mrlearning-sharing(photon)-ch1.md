---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416123"
---
# <a name="setting-up-photon"></a><span data-ttu-id="d0c12-104">Photon の設定</span><span class="sxs-lookup"><span data-stu-id="d0c12-104">Setting Up Photon</span></span>

<span data-ttu-id="d0c12-105">このレッスンでは、Photon Unity Networking (だじゃれ) を Unity プロジェクトにインポートすると、共有のエクスペリエンスを作成するための準備の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d0c12-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="d0c12-106">Photon はいくつかのネットワーク オプション Mixed Reality 開発者が利用できる共有のエクスペリエンスを作成するのです。</span><span class="sxs-lookup"><span data-stu-id="d0c12-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="d0c12-107">私たちは Photon アカウントを作成、インポート Photon、および省略可能なローカル サーバーを作成する方法を説明します</span><span class="sxs-lookup"><span data-stu-id="d0c12-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="d0c12-108">目標:</span><span class="sxs-lookup"><span data-stu-id="d0c12-108">Objectives:</span></span>

* <span data-ttu-id="d0c12-109">Photon アカウントを作成する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="d0c12-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="d0c12-110">検索して Photon Unity ネットワークをインポートする方法について説明します</span><span class="sxs-lookup"><span data-stu-id="d0c12-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="d0c12-111">ローカル Photon サーバーを設定します。</span><span class="sxs-lookup"><span data-stu-id="d0c12-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="d0c12-112">Photon の設定</span><span class="sxs-lookup"><span data-stu-id="d0c12-112">Setting Up Photon</span></span>

1. <span data-ttu-id="d0c12-113">セットアップ、 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)アカウント。</span><span class="sxs-lookup"><span data-stu-id="d0c12-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="d0c12-114">クリックして、Photon のサインアップ ページに移動します[このリンク](https://dashboard.photonengine.com/en-US/Account/SignUp)します。</span><span class="sxs-lookup"><span data-stu-id="d0c12-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="d0c12-115">サインアップ ページ、アカウントを作成するには、指示に従います。</span><span class="sxs-lookup"><span data-stu-id="d0c12-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="d0c12-118">アプリケーション ID を作成するには、「新しいアプリの作成」ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0c12-118">Create an application ID by clicking the "create a new app" button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="d0c12-120">「Photon の種類」の下のドロップダウン メニューから「Photon だじゃれ」を選択します。</span><span class="sxs-lookup"><span data-stu-id="d0c12-120">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="d0c12-121">名前、この例では、"HoloLensPhotonProject"という</span><span class="sxs-lookup"><span data-stu-id="d0c12-121">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="d0c12-122">完了すると、[作成] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0c12-122">Once finished, click the "CREATE" button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="d0c12-124">完了すると、アプリケーション ページに戻るし、次の図のような画面を表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0c12-124">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="d0c12-125">アプリケーション ID をクリックし、それをコピーします。</span><span class="sxs-lookup"><span data-stu-id="d0c12-125">Click on the app ID and copy it.</span></span> <span data-ttu-id="d0c12-126">貼り付けがどこかに簡単にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="d0c12-126">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="d0c12-128">新しい unity プロジェクトを作成し、"HLSharingProject"という名前を付けます</span><span class="sxs-lookup"><span data-stu-id="d0c12-128">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="d0c12-129">新しい Unity プロジェクトを作成する方法についてを参照してください[「Unity プロジェクトの作成」セクションのベース モジュールの](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)します。</span><span class="sxs-lookup"><span data-stu-id="d0c12-129">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="d0c12-130">プロジェクトが読み込まれたらは、次の図に示すように、「資産ストア」タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0c12-130">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="d0c12-131">次に、検索ボックスに次の図で強調表示されている、「から」を入力し、検索結果から「Photon だじゃれ 2 - 無料」の資産を選択します。</span><span class="sxs-lookup"><span data-stu-id="d0c12-131">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="d0c12-133">ダウンロードし、[ダウンロード] と [インポート] ボタンを押してこのアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="d0c12-133">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="d0c12-135">Photon には、インポート プロセスが完了したら、だじゃれウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d0c12-135">Once Photon has completed the importing process, the Pun Wizard will appear.</span></span> <span data-ttu-id="d0c12-136">手順 4 から、アプリケーション id (これはクリップボード上にある必要があります) と、[AppID] ボックスに貼り付けます「セットアップ プロジェクト」ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="d0c12-136">Take the application ID (which should be in your clipboard) from step 4 and paste it into the AppID box and press the "Setup Project" button.</span></span> 
<span data-ttu-id="d0c12-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="d0c12-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="d0c12-138">AppID を正常に追加した後は、"Photon"->"PhotonUnityNetworking"に移動]-> [->"PhotonServerSettings"資産を"Resources"。</span><span class="sxs-lookup"><span data-stu-id="d0c12-138">After successfully adding the AppID, navigate to "Photon"->"PhotonUnityNetworking" -> "Resources" ->  "PhotonServerSettings" in Assets.</span></span> <span data-ttu-id="d0c12-139">「名前のサーバーを使用する」オプションを選択し、固定の領域を photon サービス リージョンまたは「弊社」に設定します。</span><span class="sxs-lookup"><span data-stu-id="d0c12-139">Select "Use Name Server" option and set the fixed region to "us" or your photon service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="d0c12-141">結論</span><span class="sxs-lookup"><span data-stu-id="d0c12-141">Congratulations</span></span>

<span data-ttu-id="d0c12-142">Photon アカウントを作成して、ローカル Photon サーバーをセットアップ、およびだじゃれを Unity にインポートが正常が。</span><span class="sxs-lookup"><span data-stu-id="d0c12-142">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="d0c12-143">次の手順では、プロジェクトを設定して、複数のユーザーは、作業内容を確認できるように他のユーザーとの接続を許可します。</span><span class="sxs-lookup"><span data-stu-id="d0c12-143">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="d0c12-144">[次のレッスン:Sharing(Photon) レッスン 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="d0c12-144">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

