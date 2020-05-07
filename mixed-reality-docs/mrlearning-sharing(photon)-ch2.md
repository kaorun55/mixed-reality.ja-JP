---
title: マルチユーザー機能のチュートリアル - 3. 複数のユーザーの接続
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: a597aadbddb49fefc824d8c5b5193585fa9476a5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610932"
---
# <a name="2-connecting-multiple-users"></a><span data-ttu-id="af6c6-105">2.複数のユーザーの接続</span><span class="sxs-lookup"><span data-stu-id="af6c6-105">2. Connecting multiple users</span></span>

<span data-ttu-id="af6c6-106">このチュートリアルでは、ライブ共有エクスペリエンスの一部として複数のユーザーを接続する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="af6c6-107">チュートリアルを終えるときには、複数のデバイスでアプリケーションを実行して、各ユーザーが他のユーザーのアバターの動きをリアルタイムで確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="af6c6-107">By the end of the tutorial you will be able to run the application on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="af6c6-108">目標</span><span class="sxs-lookup"><span data-stu-id="af6c6-108">Objectives</span></span>

* <span data-ttu-id="af6c6-109">共有エクスペリエンスで複数のユーザーを接続する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="af6c6-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="af6c6-110">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="af6c6-110">Preparing the scene</span></span>

<span data-ttu-id="af6c6-111">このセクションでは、チュートリアルのプレハブをいくつか追加してシーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="af6c6-112">[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder.</span></span> <span data-ttu-id="af6c6-113">Ctrl ボタンを押しながら **[DebugWindow]** 、 **[NetworkLobby]** 、 **[SharedPlayground]** をクリックして、3 つのプレハブを選択します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-113">While holding down the CTRL button, click on **DebugWindow**, **NetworkLobby**, and **SharedPlayground** to select the three prefabs:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-1.png)

<span data-ttu-id="af6c6-115">3 つのプレハブを選択したまま、[Hierarchy]\(ヒエラルキー\) ウィンドウにドラッグしてこれらをシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-115">With the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="af6c6-117">ユーザー プレハブを作成する</span><span class="sxs-lookup"><span data-stu-id="af6c6-117">Creating the user prefab</span></span>

<span data-ttu-id="af6c6-118">このセクションでは、共有エクスペリエンスでユーザーを表すために使用されるプレハブを作成します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-118">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="af6c6-119">1.ユーザーの作成と構成</span><span class="sxs-lookup"><span data-stu-id="af6c6-119">1. Create and configure the user</span></span>

<span data-ttu-id="af6c6-120">[Hierarchy]\(ヒエラルキー\) ウィンドウで空の領域を右クリックし、 **[Create Empty]\(空のユーザーを作成\)** を選択してシーンに空のオブジェクトを追加し、オブジェクトに「**PhotonUser**」という名前を付けて、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-120">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="af6c6-121">[Transform]\(変換\) の **[Position]\(位置\)** が、X = 0、Y = 0、Z = 0 に設定されていることを確認する</span><span class="sxs-lookup"><span data-stu-id="af6c6-121">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-1.png)

<span data-ttu-id="af6c6-123">**PhotonUser** オブジェクトを引き続き選択した状態で、[Inspector]\(インスペクター\) ウィンドウの **[Add Component]\(コンポーネントの追加\)** ボタンを使用して **Photon User (Script)** コンポーネントを PhotonUser オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-123">With the **PhotonUser** object still selected, in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-2.png)

<span data-ttu-id="af6c6-125">[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して PhotonUser オブジェクトに **Generic Net Sync (Script)** コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-125">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="af6c6-126">**[Is User]\(ユーザーである\)** チェックボックスをオンにする</span><span class="sxs-lookup"><span data-stu-id="af6c6-126">Check the **Is User** checkbox</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-3.png)

<span data-ttu-id="af6c6-128">[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して PhotonUser オブジェクトに **Photon View (Script)** コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-128">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="af6c6-129">**"Observed Components"(観察されるコンポーネント)** フィールドに、Generic Net Sync (Script) コンポーネントを割り当てる</span><span class="sxs-lookup"><span data-stu-id="af6c6-129">To the **Observed Components** field, assign the Generic Net Sync (Script) component</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="af6c6-131">2.アバターを作成する</span><span class="sxs-lookup"><span data-stu-id="af6c6-131">2. Create the avatar</span></span>

<span data-ttu-id="af6c6-132">[Hierarchy]\(ヒエラルキー\) ウィンドウで、**PhotonUser** オブジェクトを右クリックして **[3D Object]\(3D オブジェクト\)**  >  **[Sphere]\(球体\)** を選択し、PhotonUser オブジェクトの子として球体オブジェクトを作成して次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-132">In the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="af6c6-133">[Transform]\(変換\) の **[Position]\(位置\)** が、X = 0、Y = 0、Z = 0 に設定されていることを確認する</span><span class="sxs-lookup"><span data-stu-id="af6c6-133">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="af6c6-134">[Transform]\(変換\) の **[Scale]\(スケール\)** を適切なサイズに変更する。例: X = 0.15、Y = 0.15、Z = 0.15</span><span class="sxs-lookup"><span data-stu-id="af6c6-134">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="af6c6-136">3.プレハブを作成する</span><span class="sxs-lookup"><span data-stu-id="af6c6-136">3. Create the prefab</span></span>

<span data-ttu-id="af6c6-137">[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Resources]\(リソース\)** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-1.png)

<span data-ttu-id="af6c6-139">[Resources]\(リソース\) フォルダーを選択したまま、[Hierarchy]\(ヒエラルキー\) ウィンドウから **PhotonUser** オブジェクトを **[Resources]\(リソース\)** フォルダーに**クリックしてドラッグ**し、PhotonUser オブジェクトをプレハブにします。</span><span class="sxs-lookup"><span data-stu-id="af6c6-139">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-2.png)

<span data-ttu-id="af6c6-141">[Hierarchy]\(ヒエラルキー\) ウィンドウで **PhotonUser** オブジェクトを右クリックし、 **[Delete]\(削除\)** を選択してシーンから削除します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-141">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="af6c6-143">PUN を構成してユーザー プレハブのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="af6c6-143">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="af6c6-144">このセクションでは、前のセクションで作成した PhotonUser プレハブを使用するようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-144">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="af6c6-145">[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Resources]\(リソース\)** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-145">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="af6c6-146">[Hierarchy]\(ヒエラルキー\) ウィンドウで **NetworkLobby** オブジェクトを展開して **NetworkRoom** 子オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **Photon Room (Script)** コンポーネントを探し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-146">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="af6c6-147">**"Photon User Prefab"(Photon ユーザー プレハブ)** フィールドに、[Resources]\(リソース\) フォルダーから **PhotonUser** プレハブを割り当てる</span><span class="sxs-lookup"><span data-stu-id="af6c6-147">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="af6c6-149">複数のユーザーのエクスペリエンスを試す</span><span class="sxs-lookup"><span data-stu-id="af6c6-149">Trying the experience with multiple users</span></span>

<span data-ttu-id="af6c6-150">Unity プロジェクトをビルドして HoloLens に配置してから Unity に戻り、HoloLens でアプリケーションが実行されている間に [Play]\(再生\) ボタンを押してゲーム モードに入ると、頭 (HoloLens) を動かした時に HoloLens のユーザー アバターが動くのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="af6c6-150">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="af6c6-152">HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af6c6-152">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="af6c6-153">アプリケーションは Photon に接続する必要があるため、お使いのコンピューター/デバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="af6c6-153">The application needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="af6c6-154">結論</span><span class="sxs-lookup"><span data-stu-id="af6c6-154">Congratulations</span></span>

<span data-ttu-id="af6c6-155">複数のユーザーが同じエクスペリエンスに接続して、互いの動きを確認できるようにプロジェクトを構成できました。</span><span class="sxs-lookup"><span data-stu-id="af6c6-155">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="af6c6-156">次のチュートリアルでは、オブジェクトの動きが複数のデバイスで共有されるようにする機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="af6c6-156">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

<span data-ttu-id="af6c6-157">[次のチュートリアル: 2.オブジェクトの動きの複数のユーザーとの共有](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="af6c6-157">[Next tutorial: 2. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
