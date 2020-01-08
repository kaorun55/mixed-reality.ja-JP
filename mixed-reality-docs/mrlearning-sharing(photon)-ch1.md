---
title: 複数ユーザー機能のチュートリアル-1. Photon Unity ネットワークのセットアップ
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, チュートリアル, hololens
ms.openlocfilehash: 57a23e34404e4bff653d74b7f6afc65adff8b19c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334332"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="bb494-105">1. Photon Unity ネットワークを設定する</span><span class="sxs-lookup"><span data-stu-id="bb494-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="bb494-106">概要</span><span class="sxs-lookup"><span data-stu-id="bb494-106">Overview</span></span>

<span data-ttu-id="bb494-107">このチュートリアルでは、Photon Unity ネットワーク (さしあたっ) を Unity プロジェクトにインポートして、共有エクスペリエンスを作成するための準備方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="bb494-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="bb494-108">Photon は、混合環境の開発者が共有エクスペリエンスを作成するために使用できるいくつかのネットワークオプションの1つです。</span><span class="sxs-lookup"><span data-stu-id="bb494-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="bb494-109">Photon アカウントを作成し、Photon をインポートして、オプションのローカルサーバーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb494-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="bb494-110">目標</span><span class="sxs-lookup"><span data-stu-id="bb494-110">Objectives</span></span>

* <span data-ttu-id="bb494-111">Photon アカウントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb494-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="bb494-112">Photon Unity ネットワークを検索してインポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb494-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="bb494-113">ローカル Photon サーバーをセットアップする</span><span class="sxs-lookup"><span data-stu-id="bb494-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bb494-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="bb494-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="bb494-115">[概要チュートリアル](mrlearning-base.md)シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bb494-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="bb494-116">適切な[ツールがインストール](install-the-tools.md)されている WINDOWS 10 PC</span><span class="sxs-lookup"><span data-stu-id="bb494-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="bb494-117">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="bb494-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="bb494-118">基本的なC#プログラミング機能</span><span class="sxs-lookup"><span data-stu-id="bb494-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="bb494-119">[開発用に構成され](using-visual-studio.md#enabling-developer-mode)た HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="bb494-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
><span data-ttu-id="bb494-120">このチュートリアルシリーズでは<a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019.1</a>が必要であり、推奨されるバージョンは unity 2019.1.14 です。</span><span class="sxs-lookup"><span data-stu-id="bb494-120">This tutorial series requires <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019.1</a> and the recommended version is Unity 2019.1.14.</span></span> <span data-ttu-id="bb494-121">これは、前にリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="bb494-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="bb494-122">Photon の設定</span><span class="sxs-lookup"><span data-stu-id="bb494-122">Setting up Photon</span></span>

1. <span data-ttu-id="bb494-123">[Photon](https://dashboard.photonengine.com//Account/SignUp)アカウントを設定します。</span><span class="sxs-lookup"><span data-stu-id="bb494-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="bb494-124">[このリンク](https://dashboard.photonengine.com//Account/SignUp)をクリックして、Photon サインアップページに移動します。</span><span class="sxs-lookup"><span data-stu-id="bb494-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="bb494-125">サインアップページの指示に従って、アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="bb494-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="bb494-128">[新しいアプリの作成] ボタンをクリックして、アプリケーション ID を作成します。</span><span class="sxs-lookup"><span data-stu-id="bb494-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="bb494-130">[Photon Type] の下にあるドロップダウンメニューから [Photon さしあたっ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb494-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="bb494-131">次に、名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb494-131">Then give it a name.</span></span> <span data-ttu-id="bb494-132">この例では、HoloLensPhotonProject という名前を付けています。</span><span class="sxs-lookup"><span data-stu-id="bb494-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="bb494-133">完了したら、[作成] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb494-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="bb494-135">アプリケーションのページに戻ると、次の図のような内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb494-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="bb494-136">アプリケーション ID をクリックしてコピーします。</span><span class="sxs-lookup"><span data-stu-id="bb494-136">Click the application ID and copy it.</span></span> <span data-ttu-id="bb494-137">簡単にアクセスできる場所に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="bb494-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="bb494-139">新しい unity プロジェクトを作成し、HLSharingProject という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb494-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="bb494-140">新しい Unity プロジェクトを作成する方法については、[ベースモジュール「Unity プロジェクトの作成」セクション](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb494-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="bb494-141">プロジェクトが読み込まれたら、次の図に示すように、[アセットストア] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb494-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="bb494-142">次に、下の画像で強調表示されている検索ボックスで、「さしあたっ」と入力し、検索結果から Photon さしあたっ 2 FREE "資産を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb494-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="bb494-144">[ダウンロード] と [インポート] ボタンを押して、この資産をダウンロードしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="bb494-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="bb494-146">Photon がインポートプロセスを完了すると、さしあたっウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb494-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="bb494-147">手順 4. のアプリケーション ID (クリップボードにあるはずです) を取得し、[AppID] ボックスに貼り付けて、[Setup Project] ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="bb494-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="bb494-149">AppID が正常に追加されたら、Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings in Assets に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb494-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="bb494-150">[ネームサーバーを使用する] オプションを選択し、[固定] リージョンを [US] または [photon service region] に設定します。</span><span class="sxs-lookup"><span data-stu-id="bb494-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="bb494-152">結論</span><span class="sxs-lookup"><span data-stu-id="bb494-152">Congratulations</span></span>

<span data-ttu-id="bb494-153">Photon アカウントの作成、ローカル Photon サーバーの設定、Unity へのさしあたっのインポートが正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="bb494-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="bb494-154">次の手順では、複数のユーザーが作業を確認できるように、プロジェクトを設定し、他のユーザーとの接続を許可します。</span><span class="sxs-lookup"><span data-stu-id="bb494-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="bb494-155">[次のチュートリアル: 2. Unity を開発用に準備する](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="bb494-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
