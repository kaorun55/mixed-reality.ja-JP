---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523291"
---
#  <a name="setting-up-photon-unity-networking"></a><span data-ttu-id="5a57b-104">Photon Unity ネットワークを設定</span><span class="sxs-lookup"><span data-stu-id="5a57b-104">Setting up Photon Unity Networking</span></span>

<span data-ttu-id="5a57b-105">このチュートリアルでは、Photon Unity Networking (だじゃれ) を Unity プロジェクトにインポートすると、共有のエクスペリエンスを作成するために準備する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a57b-105">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="5a57b-106">Photon はいくつかのネットワーク オプション Mixed Reality 開発者が利用できる共有のエクスペリエンスを作成するのです。</span><span class="sxs-lookup"><span data-stu-id="5a57b-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="5a57b-107">私たちは Photon アカウントを作成、インポート Photon、および省略可能なローカル サーバーを作成する方法を説明します</span><span class="sxs-lookup"><span data-stu-id="5a57b-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="5a57b-108">目標:</span><span class="sxs-lookup"><span data-stu-id="5a57b-108">Objectives:</span></span>

* <span data-ttu-id="5a57b-109">Photon アカウントを作成する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="5a57b-109">Learn how to create a Photon account</span></span>

* <span data-ttu-id="5a57b-110">検索して Photon Unity ネットワークをインポートする方法について説明します</span><span class="sxs-lookup"><span data-stu-id="5a57b-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="5a57b-111">ローカル Photon サーバーを設定します。</span><span class="sxs-lookup"><span data-stu-id="5a57b-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="5a57b-112">Photon の設定</span><span class="sxs-lookup"><span data-stu-id="5a57b-112">Setting up Photon</span></span>

1. <span data-ttu-id="5a57b-113">セットアップ、 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)アカウント。</span><span class="sxs-lookup"><span data-stu-id="5a57b-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="5a57b-114">クリックして、Photon のサインアップ ページに移動します[このリンク](https://dashboard.photonengine.com/en-US/Account/SignUp)します。</span><span class="sxs-lookup"><span data-stu-id="5a57b-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="5a57b-115">サインアップ ページ、アカウントを作成するには、指示に従います。</span><span class="sxs-lookup"><span data-stu-id="5a57b-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="5a57b-118">新しいアプリのボタンの作成 をクリックして、アプリケーション ID を作成します。</span><span class="sxs-lookup"><span data-stu-id="5a57b-118">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="5a57b-120">Photon だじゃれを Photon の種類の下のドロップダウン メニューから選択します。</span><span class="sxs-lookup"><span data-stu-id="5a57b-120">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="5a57b-121">名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="5a57b-121">Then give it a name.</span></span> <span data-ttu-id="5a57b-122">この例では、という HoloLensPhotonProject します。</span><span class="sxs-lookup"><span data-stu-id="5a57b-122">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="5a57b-123">完了すると、[作成] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a57b-123">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="5a57b-125">完了すると、アプリケーション ページに戻るし、次の図のような画面を表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a57b-125">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="5a57b-126">アプリケーション ID をクリックし、それをコピーします。</span><span class="sxs-lookup"><span data-stu-id="5a57b-126">Click on the application ID and copy it.</span></span> <span data-ttu-id="5a57b-127">貼り付けがどこかに簡単にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="5a57b-127">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="5a57b-129">新しい unity プロジェクトを作成し、HLSharingProject という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="5a57b-129">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="5a57b-130">新しい Unity プロジェクトを作成する方法についてを参照してください[「Unity プロジェクトの作成」セクションのベース モジュールの](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)します。</span><span class="sxs-lookup"><span data-stu-id="5a57b-130">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="5a57b-131">プロジェクトを読み込んだらは、次の図に示すようにアセット ストア タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a57b-131">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="5a57b-132">検索結果から資産を次に、次の図で強調表示されている検索ボックスには、だじゃれを入力し、FRE Photon だじゃれ 2 - を選択します"。</span><span class="sxs-lookup"><span data-stu-id="5a57b-132">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FRE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="5a57b-134">ダウンロードし、ダウンロードとインポートのボタンを押してこのアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="5a57b-134">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="5a57b-136">Photon には、インポート プロセスが完了したら、だじゃれウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5a57b-136">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="5a57b-137">アプリケーション id (これはクリップボード上にある必要があります) を手順 4. から、AppID ボックスに貼り付けます、セットアップ プロジェクト をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a57b-137">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="5a57b-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="5a57b-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="5a57b-139">AppID が正常に追加した後には、Photon に移動します。 PhotonUnityNetworking]-> []-> [リソースの資産で PhotonServerSettings]-> [です。</span><span class="sxs-lookup"><span data-stu-id="5a57b-139">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="5a57b-140">名前のサーバーを使用するオプションを選択し、ご意見の固定のリージョンまたは yourPphoton サービス地域を設定します。</span><span class="sxs-lookup"><span data-stu-id="5a57b-140">Select the Use Name Server option, and set the fixed region to US or yourPphoton service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="5a57b-142">結論</span><span class="sxs-lookup"><span data-stu-id="5a57b-142">Congratulations</span></span>

<span data-ttu-id="5a57b-143">Photon アカウントを作成して、ローカル Photon サーバーをセットアップ、およびだじゃれを Unity にインポートが正常が。</span><span class="sxs-lookup"><span data-stu-id="5a57b-143">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="5a57b-144">次の手順では、プロジェクトを設定して、複数のユーザーは、作業内容を確認できるように他のユーザーとの接続を許可します。</span><span class="sxs-lookup"><span data-stu-id="5a57b-144">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="5a57b-145">[次のチュートリアル:Unity の開発の準備](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="5a57b-145">[Next tutorial: Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

