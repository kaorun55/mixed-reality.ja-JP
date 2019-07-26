---
title: HoloLens 2 用 MR Learning 共有モジュール
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 77ae779b4bb32dd66a722c9793d1b83c4a64ae2e
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485672"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="956b6-104">4。オブジェクトの移動を複数のユーザーと共有する</span><span class="sxs-lookup"><span data-stu-id="956b6-104">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="956b6-105">このチュートリアルでは、共有セッションのすべての参加者が連携して相互作用を表示できるように、オブジェクトの移動を共有する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="956b6-105">In this Tutorial, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="956b6-106">このレッスンは、[基本モジュールチュートリアル](mrlearning-base.md)の一部として作成された太陰暦ランチャーに基づいています。</span><span class="sxs-lookup"><span data-stu-id="956b6-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="956b6-107">事項</span><span class="sxs-lookup"><span data-stu-id="956b6-107">Objectives:</span></span>

- <span data-ttu-id="956b6-108">共有する3D モデルとして旧暦ランチャーを使用する</span><span class="sxs-lookup"><span data-stu-id="956b6-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="956b6-109">3D モデルの移動を共有するようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="956b6-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="956b6-110">基本的なマルチユーザーコラボレーションアプリケーションを構築する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="956b6-110">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="956b6-111">手順</span><span class="sxs-lookup"><span data-stu-id="956b6-111">Instructions</span></span>


1. <span data-ttu-id="956b6-112">前のレッスン (コントロール + S) からシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="956b6-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="956b6-113">必要なときに簡単に見つけられるように、HLSharedProjectMainPart4 という名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="956b6-113">You can name it, HLSharedProjectMainPart4.unity, so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="956b6-114">[プロジェクト] ウィンドウの [Assets-> Scripts] フォルダーで [GenericNetSync] をダブルクリックして、Visual Studio または使用しているコードエディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="956b6-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="956b6-116">34および38行の場合は、このレッスンで使用するテーブルのコードをアクティブ化するために//を削除します。</span><span class="sxs-lookup"><span data-stu-id="956b6-116">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="956b6-117">次に、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="956b6-117">next, Save the file.</span></span> 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="956b6-119">プロジェクトウィンドウで、PhotonRoom.cs Scripts フォルダー > 内のファイルをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="956b6-119">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="956b6-121">手順 3. と同じように、//を削除して106コードをアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="956b6-121">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.</span></span>

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="956b6-124">[階層] ビューで、NetworkRoom オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="956b6-124">In the Hierarchy view, select the NetworkRoom object.</span></span>

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="956b6-126">プロジェクト ビューで、資産-> Resources-> Prefabs に移動します。</span><span class="sxs-lookup"><span data-stu-id="956b6-126">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="956b6-127">まず、テーブル prefab を PhotonRoom クラスの Tableprefab スロットにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="956b6-127">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="956b6-128">次に、RocketLauncherCompleteVariantprefab を PhotonRoom クラスのモジュール Prefab スロットにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="956b6-128">Next drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

   <span data-ttu-id="956b6-130">注:Prefab オブジェクトとリリースのいずれかをクリックすると、インスペクターがそのオブジェクトに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="956b6-130">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="956b6-131">各オブジェクトをクリックし、ドラッグしてドロップし、各オブジェクトを適切なスロットに解放します。</span><span class="sxs-lookup"><span data-stu-id="956b6-131">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="956b6-132">MixedRealityPlayspace の左側にある矢印をクリックし、子ゲームオブジェクトの MainCamera を SharedPlayground グラウンドに移動します。</span><span class="sxs-lookup"><span data-stu-id="956b6-132">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="956b6-133">次に、prefab、MixedRealityPlayspace を削除して削除し、事前 fab を選択して、キーボードの [削除] をタップします。</span><span class="sxs-lookup"><span data-stu-id="956b6-133">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="956b6-134">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="956b6-134">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

><span data-ttu-id="956b6-135">注:メインカメラと SharedPlayground グラウンドの両方の位置が0、0、0に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="956b6-135">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>
>

9. <span data-ttu-id="956b6-136">新しいオブジェクトを作成するために、SharedPlayground グラウンド親オブジェクトの子オブジェクトとして新しいゲームオブジェクトセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="956b6-136">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="956b6-137">親オブジェクトを右クリックし、[空の作成] を選択します。</span><span class="sxs-lookup"><span data-stu-id="956b6-137">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="956b6-138">階層で新しいオブジェクトを選択し、[インスペクター] パネルでオブジェクトの名前を TableAnchor に変更します。</span><span class="sxs-lookup"><span data-stu-id="956b6-138">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="956b6-139">また、[コンポーネントの追加] をクリックし、TableAnchor コンポーネントを検索します。</span><span class="sxs-lookup"><span data-stu-id="956b6-139">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="956b6-140">それを選択してオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="956b6-140">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="956b6-142">次に、[プロジェクト] パネルの [Prefabs] フォルダーで、先ほど作成した "TableAnchor" 子オブジェクトにテーブル prefab をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="956b6-142">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. <span data-ttu-id="956b6-144">最後に、DebugWindow オブジェクトで、幅を50に、高さを20に変更します。</span><span class="sxs-lookup"><span data-stu-id="956b6-144">Finally, in the DebugWindow object, change the width to 50 and the height to 20.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="956b6-146">結論</span><span class="sxs-lookup"><span data-stu-id="956b6-146">Congratulations</span></span>


<span data-ttu-id="956b6-147">この処理が完了すると、Unity プロジェクトに参加しているすべてのユーザーが、旧暦ランチャーを移動できるようになります。</span><span class="sxs-lookup"><span data-stu-id="956b6-147">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="956b6-148">すべての移動が同期されるため、各ユーザーが互いの相互作用を参照できます。</span><span class="sxs-lookup"><span data-stu-id="956b6-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="956b6-149">これらの概念は、すべての機能を備えた共有コラボレーションエクスペリエンスの基本的な構成要素として機能します。</span><span class="sxs-lookup"><span data-stu-id="956b6-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="956b6-150">すべてのユーザーは共有エクスペリエンスの一部として接続されており、オブジェクトの相対的な移動を確認できますが、ローカルユーザーが物理的に同じ場所にある他のオブジェクトとオブジェクトを参照できるように、アバターとオブジェクトを正確に配置することはできません。現実的.</span><span class="sxs-lookup"><span data-stu-id="956b6-150">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="956b6-151">ローカルの共有エクスペリエンスを固定するために、すべてのデバイスは物理環境についてよく理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="956b6-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="956b6-152">このモジュールでは、次のレッスンで実装する[Azure 空間アンカー](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) を使用してこれを実現します。</span><span class="sxs-lookup"><span data-stu-id="956b6-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="956b6-153">次のレッスンに進む前に、asa の基本、Azure アカウントとリソースの作成、およびその他の基本的なビルディングブロックについて説明している ASA Learning モジュールを完成させる必要があります。これは、共有エクスペリエンスに統合する前に必要です。</span><span class="sxs-lookup"><span data-stu-id="956b6-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="956b6-154">[次のレッスン:5。Azure Spatial Anchors の共有エクスペリエンスへの統合](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="956b6-154">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>

