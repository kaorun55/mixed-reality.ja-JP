---
title: 複数ユーザー機能のチュートリアル-4. オブジェクトの移動を複数のユーザーと共有する
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, チュートリアル, hololens
ms.openlocfilehash: f523aabd74b9267b3f7f5024d8af46110e43c32a
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334282"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="86a1e-105">4. オブジェクトの移動を複数のユーザーと共有する</span><span class="sxs-lookup"><span data-stu-id="86a1e-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="86a1e-106">このチュートリアルでは、共有セッションのすべての参加要素が相互に共同作業したり、他のユーザーの操作を表示したりできるように、オブジェクトの移動を共有する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="86a1e-107">このレッスンは、[基本モジュールチュートリアル](mrlearning-base.md)の一部として作成された太陰暦ランチャーに基づいています。</span><span class="sxs-lookup"><span data-stu-id="86a1e-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="86a1e-108">目標</span><span class="sxs-lookup"><span data-stu-id="86a1e-108">Objectives</span></span>

- <span data-ttu-id="86a1e-109">共有する3D モデルとして旧暦ランチャーを使用する</span><span class="sxs-lookup"><span data-stu-id="86a1e-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="86a1e-110">3D モデルの移動を共有するようにプロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="86a1e-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="86a1e-111">基本的なマルチユーザーコラボレーションアプリケーションを構築する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="86a1e-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="86a1e-112">手順</span><span class="sxs-lookup"><span data-stu-id="86a1e-112">Instructions</span></span>

1. <span data-ttu-id="86a1e-113">前のレッスン (コントロール + S) からシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="86a1e-114">必要なときに簡単に見つけられるように、HLSharedProjectMainPart4 という名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="86a1e-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="86a1e-115">[プロジェクト] ウィンドウの [Assets-> Scripts] フォルダーで、[GenericNetSync] をダブルクリックして、Visual Studio または使用しているコードエディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="86a1e-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="86a1e-117">34および38行では、"//" を削除して、このレッスンで使用するテーブルのコードをアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="86a1e-118">次に、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="86a1e-120">[プロジェクト] ウィンドウで、[Assets-> Scripts] フォルダー内の PhotonRoom.cs ファイルをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="86a1e-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="86a1e-122">手順 3. と同じように、"//" を削除してコードをアクティブにする必要があります (25、26、106行)。</span><span class="sxs-lookup"><span data-stu-id="86a1e-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="86a1e-125">[階層] ビューで、NetworkRoom オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="86a1e-127">プロジェクト ビューで、資産-> Resources-> Prefabs に移動します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="86a1e-128">まず、テーブル prefab を PhotonRoom クラスの Tableprefab スロットにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="86a1e-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="86a1e-129">次に、RocketLauncherCompleteVariantprefab を PhotonRoom クラスのモジュール Prefab スロットにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="86a1e-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="86a1e-131">Prefab オブジェクトとリリースのいずれかをクリックすると、インスペクターがそのオブジェクトに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="86a1e-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="86a1e-132">各オブジェクトをクリックし、ドラッグしてドロップし、各オブジェクトを適切なスロットに解放します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="86a1e-133">MixedRealityPlayspace の左側にある矢印をクリックし、子ゲームオブジェクト MainCamera を SharedPlayground グラウンドに移動します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="86a1e-134">次に、prefab を削除し、キーボードの [削除] をタップして、MixedRealityPlayspace を削除します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="86a1e-136">メインカメラと SharedPlayground グラウンドの両方の位置が0、0、0に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="86a1e-137">"SharedPlayground グラウンド" オブジェクトを選択し、マウスを右クリックして [空の作成] オプションを選択し、空のゲームオブジェクトを "SharedPlayground グラウンド" ゲームオブジェクトの子として作成します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="86a1e-139">階層で新しいオブジェクトを選択し、[インスペクター] パネルでオブジェクトの名前を TableAnchor に変更します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="86a1e-140">また、[コンポーネントの追加] をクリックし、TableAnchor コンポーネントを検索します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="86a1e-141">それを選択してオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="86a1e-143">Prefabs フォルダーの [プロジェクト] パネルで、テーブル prefab を、先ほど作成した "TableAnchor" 子オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="86a1e-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. <span data-ttu-id="86a1e-145">DebugWindow オブジェクトで、幅を50に、高さを20に変更します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-145">In the DebugWindow object, change the width to 50 and the height to 20.</span></span>

    ![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="86a1e-147">結論</span><span class="sxs-lookup"><span data-stu-id="86a1e-147">Congratulations</span></span>

<span data-ttu-id="86a1e-148">この処理が完了したら、次のようにして、旧暦モジュールを見つけます。</span><span class="sxs-lookup"><span data-stu-id="86a1e-148">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="86a1e-149">その後、Unity プロジェクトに参加するすべてのユーザーが、旧暦ランチャーを移動できます。</span><span class="sxs-lookup"><span data-stu-id="86a1e-149">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="86a1e-150">すべての移動が同期されるため、各ユーザーが互いの相互作用を参照できます。</span><span class="sxs-lookup"><span data-stu-id="86a1e-150">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="86a1e-151">これらの概念は、すべての機能を備えた共有コラボレーションエクスペリエンスの基本的な構成要素として機能します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-151">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="86a1e-152">すべてのユーザーは共有エクスペリエンスの一部として接続されており、オブジェクトの相対的な移動を確認できますが、アプリケーションでは、ローカルユーザーが他のオブジェクトとオブジェクトを表示できないように、アバターとオブジェクトを正確に配置することはできません。物理的な世界。</span><span class="sxs-lookup"><span data-stu-id="86a1e-152">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="86a1e-153">ローカルの共有エクスペリエンスを固定するために、すべてのデバイスは物理環境についてよく理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="86a1e-153">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="86a1e-154">このモジュールでは、次のレッスンで実装する[Azure 空間アンカー](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) を使用してこれを実現します。</span><span class="sxs-lookup"><span data-stu-id="86a1e-154">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="86a1e-155">次のレッスンに進む前に、asa の基本、Azure アカウントとリソースの作成、およびその他の基本的なビルディングブロックについて説明する ASA Learning モジュールを完成させる必要があります。これは、共有エクスペリエンスに統合する前に必要です。</span><span class="sxs-lookup"><span data-stu-id="86a1e-155">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="86a1e-156">[次のレッスン: 5. Azure 空間アンカーを共有エクスペリエンスに統合する](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="86a1e-156">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>
