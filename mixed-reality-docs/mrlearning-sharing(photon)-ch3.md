---
title: マルチユーザー機能のチュートリアル - 4. 複数のユーザーとオブジェクトの移動を共有する
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610648"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="3b2c5-105">3.複数のユーザーとオブジェクトの移動を共有する</span><span class="sxs-lookup"><span data-stu-id="3b2c5-105">3. Sharing object movements with multiple users</span></span>

<span data-ttu-id="3b2c5-106">このチュートリアルでは、共有エクスペリエンスのすべての参加者が共同作業したり、相互の操作を表示したりできるように、オブジェクトの移動を共有する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3b2c5-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each others' interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="3b2c5-107">目標</span><span class="sxs-lookup"><span data-stu-id="3b2c5-107">Objectives</span></span>

* <span data-ttu-id="3b2c5-108">オブジェクトの移動を共有するようにプロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="3b2c5-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="3b2c5-109">基本的なマルチユーザー コラボレーション アプリケーションを構築する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="3b2c5-109">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="3b2c5-110">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="3b2c5-110">Preparing the scene</span></span>

<span data-ttu-id="3b2c5-111">このセクションでは、チュートリアルのプレハブを追加してシーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="3b2c5-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="3b2c5-112">[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動して、**TableAnchor** プレハブを [Hierarchy]\(ヒエラルキー\) ウィンドウの **SharedPlayground** オブジェクト上にドラッグし、SharedPlayground オブジェクトの子としてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="3b2c5-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab on top of the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="3b2c5-114">PUN を構成してオブジェクトのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="3b2c5-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="3b2c5-115">このセクションでは、前のセクションで作成した RocketLauncher_Complete_Variant プレハブを使うようにプロジェクトを構成して、そのインスタンスを作成する場所を定義します。</span><span class="sxs-lookup"><span data-stu-id="3b2c5-115">In this section, you will configure the project to use the RocketLauncher_Complete_Variant prefab you created in the previous section and define where it will be instantiated.</span></span>

<span data-ttu-id="3b2c5-116">[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Resources]\(リソース\)** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="3b2c5-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="3b2c5-117">[Hierarchy]\(ヒエラルキー\) ウィンドウで **NetworkLobby** オブジェクトを展開して **NetworkRoom** 子オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **Photon Room (Script)** コンポーネントを探し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="3b2c5-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="3b2c5-118">**"Photon User Prefab"(Photon ユーザー プレハブ)** フィールドに、[Resources]\(リソース\) フォルダーから **PhotonUser** プレハブを割り当てる</span><span class="sxs-lookup"><span data-stu-id="3b2c5-118">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

<span data-ttu-id="3b2c5-120">**NetworkRoom** 子オブジェクトを選択したまま [Hierarchy]\(ヒエラルキー\) ウィンドウで **TableAnchor** オブジェクトを展開し、[Inspector]\(インスペクター\) ウィンドウで **Photon Room (Script)** コンポーネントを探して次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="3b2c5-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="3b2c5-121">**"Rocket Launcher Location"(Rocket Launcher の場所)** フィールドに、[Hierarchy]\(ヒエラルキー\) ウィンドウから **Table** 子オブジェクトを割り当てる</span><span class="sxs-lookup"><span data-stu-id="3b2c5-121">To the **Rocket Launcher Location** field, assign the **Table** child object from the Hierarchy window</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="3b2c5-123">共有オブジェクト移動のエクスペリエンスを試す</span><span class="sxs-lookup"><span data-stu-id="3b2c5-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="3b2c5-124">Unity プロジェクトをビルドして HoloLens に配置してから Unity に戻り、HoloLens でアプリケーションが実行されている間に [Play]\(再生\) ボタンを押してゲーム モードに入ると、HoloLens でオブジェクトを動かした時に Unity でオブジェクトが移動するのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="3b2c5-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="3b2c5-126">結論</span><span class="sxs-lookup"><span data-stu-id="3b2c5-126">Congratulations</span></span>

<span data-ttu-id="3b2c5-127">オブジェクトの移動が同期するようにプロジェクトを構成できました。ユーザーがオブジェクトを移動すると、そのオブジェクトの移動が他のユーザーにも表示されます。</span><span class="sxs-lookup"><span data-stu-id="3b2c5-127">You have successfully configured your project so object movements are synchronized and users can see the objects move when other users move the objects.</span></span> <span data-ttu-id="3b2c5-128">次のチュートリアルでは、共有エクスペリエンスを現実世界に収め、ユーザーたちが互いの姿をその現実の物理的な位置に見られるようにしたり、オブジェクトがどのユーザーからも同じ物理的な位置と角度で表示されるようにしたりする機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="3b2c5-128">In the next tutorial, you will implement functionality so the shared experience is aligned in the physical world and the users see each other in their actual physical location and so the objects appear in the same physical position and rotation for all users.</span></span>

<span data-ttu-id="3b2c5-129">[次のチュートリアル: 4.Azure Spatial Anchors の共有エクスペリエンスへの統合](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="3b2c5-129">[Next tutorial: 4. Integrating Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch4.md)</span></span>
