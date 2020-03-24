---
title: マルチユーザー機能のチュートリアル - 1。 Photon Unity Networking の設定
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031331"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="90c6f-105">1.Photon Unity Networking の設定</span><span class="sxs-lookup"><span data-stu-id="90c6f-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="90c6f-106">概要</span><span class="sxs-lookup"><span data-stu-id="90c6f-106">Overview</span></span>

<span data-ttu-id="90c6f-107">このチュートリアルでは、Photon Unity Networking (PUN) を Unity プロジェクトにインポートして共有エクスペリエンスの作成準備をする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="90c6f-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="90c6f-108">Photon は、Mixed Reality の開発者が共有エクスペリエンスを作成するために使用できるいくつかのネットワーク オプションの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="90c6f-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="90c6f-109">Photon アカウントを作成し、Photon をインポートし、オプションのローカル サーバーを作成する方法について学習します</span><span class="sxs-lookup"><span data-stu-id="90c6f-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="90c6f-110">目標</span><span class="sxs-lookup"><span data-stu-id="90c6f-110">Objectives</span></span>

* <span data-ttu-id="90c6f-111">Photon アカウントを作成する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="90c6f-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="90c6f-112">Photon Unity Networking を検出してインポートする方法を学習する</span><span class="sxs-lookup"><span data-stu-id="90c6f-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="90c6f-113">ローカル Photon サーバーを設定する</span><span class="sxs-lookup"><span data-stu-id="90c6f-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="90c6f-114">前提条件</span><span class="sxs-lookup"><span data-stu-id="90c6f-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="90c6f-115">[入門チュートリアル](mrlearning-base.md)と [Azure Spatial Anchors の入門チュートリアル](mrlearning-asa-ch1.md)のチュートリアル シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="90c6f-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors started tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="90c6f-116">正しい[ツールがインストールされている](install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="90c6f-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="90c6f-117">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="90c6f-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="90c6f-118">基本的な C# プログラミング能力</span><span class="sxs-lookup"><span data-stu-id="90c6f-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="90c6f-119">[開発用に構成された](using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="90c6f-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="90c6f-120">このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.2.X です。</span><span class="sxs-lookup"><span data-stu-id="90c6f-120">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="90c6f-121">これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="90c6f-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="90c6f-122">Photon の設定</span><span class="sxs-lookup"><span data-stu-id="90c6f-122">Setting up Photon</span></span>

1. <span data-ttu-id="90c6f-123">[Photon](https://dashboard.photonengine.com//Account/SignUp) アカウントを設定します。</span><span class="sxs-lookup"><span data-stu-id="90c6f-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="90c6f-124">[こちらのリンク](https://dashboard.photonengine.com//Account/SignUp)をクリックして、Photon のサインアップ ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="90c6f-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="90c6f-125">サインアップ ページの指示に従って、アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="90c6f-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="90c6f-128">[Create a New App]\(新しいアプリの作成\) ボタンをクリックして、アプリケーション ID を作成します。</span><span class="sxs-lookup"><span data-stu-id="90c6f-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="90c6f-130">[Photon Type]\(Photon の種類\) の下のドロップダウン メニューから [Photon PUN] を選択します。</span><span class="sxs-lookup"><span data-stu-id="90c6f-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="90c6f-131">次に、それに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="90c6f-131">Then give it a name.</span></span> <span data-ttu-id="90c6f-132">この例では、HoloLensPhotonProject という名前を付けました。</span><span class="sxs-lookup"><span data-stu-id="90c6f-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="90c6f-133">完了したら、[Create]\(作成\) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="90c6f-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="90c6f-135">アプリケーションのページに戻ります。次の画像のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="90c6f-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="90c6f-136">アプリケーション ID をクリックしてコピーします。</span><span class="sxs-lookup"><span data-stu-id="90c6f-136">Click the application ID and copy it.</span></span> <span data-ttu-id="90c6f-137">すぐにアクセスできる任意の場所に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="90c6f-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="90c6f-139">新しい Unity プロジェクトを作成し、HLSharingProject という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="90c6f-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="90c6f-140">新しい Unity プロジェクトを作成する方法については、[ベース モジュールの "Unity プロジェクトの作成" に関するセクション](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90c6f-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="90c6f-141">プロジェクトを読み込んだら、次の図に示すように、[Assets Store]\(アセット ストア\) タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="90c6f-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="90c6f-142">次に、以下の図で強調表示されている検索ボックスに「PUN」と入力し、検索結果から [Photon PUN 2 - FREE] アセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="90c6f-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="90c6f-144">[Download]\(ダウンロード\) と [Import]\(インポート\) ボタンを押して、このアセットをダウンロードしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="90c6f-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="90c6f-146">Photon がインポート プロセスを完了すると、PUN ウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="90c6f-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="90c6f-147">手順 4 のアプリケーション ID (クリップボードにある) を [AppID] ボックスに貼り付けて、[Setup Project]\(プロジェクトの設定\) ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="90c6f-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="90c6f-149">AppID を正常に追加したら、アセット内で [Photon] -> [PhotonUnityNetworking] -> [Resources]\(リソース\) -> [PhotonServerSettings] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="90c6f-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="90c6f-150">[Use Name Server]\(ネーム サーバーを使用する\) オプションを選択し、固定リージョンを [US]\(米国\)、またはお使いの Photon サービス リージョンに設定します。</span><span class="sxs-lookup"><span data-stu-id="90c6f-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="90c6f-152">結論</span><span class="sxs-lookup"><span data-stu-id="90c6f-152">Congratulations</span></span>

<span data-ttu-id="90c6f-153">Photon アカウントを正常に作成し、ローカル Photon サーバーを設定し、PUN を Unity にインポートしました。</span><span class="sxs-lookup"><span data-stu-id="90c6f-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="90c6f-154">次の手順では、プロジェクトを設定し、他のユーザーとの接続を許可して複数のユーザーが作業を表示できるようにします。</span><span class="sxs-lookup"><span data-stu-id="90c6f-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="90c6f-155">[次のチュートリアル: 2.Unity の開発に向けた準備](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="90c6f-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
