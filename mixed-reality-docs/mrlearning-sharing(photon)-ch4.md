---
title: マルチユーザー機能のチュートリアル - 4. 複数のユーザーとオブジェクトの移動を共有する
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031243"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="f41aa-105">4.複数のユーザーとオブジェクトの移動を共有する</span><span class="sxs-lookup"><span data-stu-id="f41aa-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="f41aa-106">このチュートリアルでは、共有セッションのすべての参加者が共同作業したり、相互の操作を表示したりできるように、オブジェクトの移動を共有する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f41aa-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="f41aa-107">このレッスンは、[ベース モジュール チュートリアル](mrlearning-base.md)の一部として作成された月着陸船ランチャーに基づいて進められます。</span><span class="sxs-lookup"><span data-stu-id="f41aa-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="f41aa-108">目標</span><span class="sxs-lookup"><span data-stu-id="f41aa-108">Objectives</span></span>

- <span data-ttu-id="f41aa-109">共有する 3D モデルとして月着陸船ランチャーを取り込む</span><span class="sxs-lookup"><span data-stu-id="f41aa-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="f41aa-110">3D モデルの移動を共有するようにプロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="f41aa-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="f41aa-111">基本的なマルチユーザー コラボレーション アプリケーションを構築する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="f41aa-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="f41aa-112">手順</span><span class="sxs-lookup"><span data-stu-id="f41aa-112">Instructions</span></span>

1. <span data-ttu-id="f41aa-113">前のレッスンのシーンを保存します (Ctrl + S)。</span><span class="sxs-lookup"><span data-stu-id="f41aa-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="f41aa-114">必要なときに簡単に見つけられるように、HLSharedProjectMainPart4.unity という名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="f41aa-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="f41aa-115">[Project]\(プロジェクト\) ウィンドウの [Assets]\(資産\) -> [Scripts]\(スクリプト\) フォルダーで、[GenericNetSync] をダブルクリックして、Visual Studio または使用している任意のコード エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="f41aa-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="f41aa-117">行 34 および 38 の "//" を削除して、このレッスンで使用するテーブルのコードをアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="f41aa-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="f41aa-118">次に、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="f41aa-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="f41aa-120">[Project]\(プロジェクト\) ウィンドウで、[Assets]\(資産\) -> [Scripts]\(スクリプト\) フォルダー内の PhotonRoom.cs ファイルをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="f41aa-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="f41aa-122">手順 3 と同じように、"//" を削除して、行 25、26、106 のコードをアクティブにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f41aa-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="f41aa-125">[Hierarchy]\(階層\) ビューで、[NetworkRoom] オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="f41aa-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="f41aa-127">[Project]\(プロジェクト\) ビューで、[Assets]\(資産\) -> [Resources]\(リソース\) -> [Prefabs]\(プレハブ\) に移動します。</span><span class="sxs-lookup"><span data-stu-id="f41aa-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="f41aa-128">まず、Table プレハブを PhotonRoom クラスの Tableprefab スロットにドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="f41aa-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="f41aa-129">次に、RocketLauncherCompleteVariantprefab を PhotonRoom クラスの Module Prefab スロットにドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="f41aa-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="f41aa-131">プレハブ オブジェクトのいずれかをクリックして解放した場合、インスペクターがそのオブジェクトに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="f41aa-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="f41aa-132">各オブジェクトをクリックし、適切なスロットにドラッグしてドロップし、解放します。</span><span class="sxs-lookup"><span data-stu-id="f41aa-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="f41aa-133">MixedRealityPlayspace の左側にある矢印をクリックし、子ゲーム オブジェクト MainCamera を SharedPlayground プレハブに移動します。</span><span class="sxs-lookup"><span data-stu-id="f41aa-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="f41aa-134">次に、プレハブ MixedRealityPlayspace を選択してキーボードの [Delete] キーを押して、そのプレハブを削除します。</span><span class="sxs-lookup"><span data-stu-id="f41aa-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="f41aa-136">Main Camera と SharedPlayground の両方の位置が 0、0、0 に設定されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f41aa-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="f41aa-137">"SharedPlayground" オブジェクトを選択し、マウスを右クリックして [Create Empty]\(空の作成\) オプションを選択し、空のゲーム オブジェクトを "SharedPlayground" ゲーム オブジェクトの子として作成します。</span><span class="sxs-lookup"><span data-stu-id="f41aa-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="f41aa-139">階層で新しいオブジェクトが選択された状態で、[Inspector]\(インスペクター\) パネルでオブジェクトの名前を TableAnchor に変更します。</span><span class="sxs-lookup"><span data-stu-id="f41aa-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="f41aa-140">また、[Add Component]\(コンポーネントの追加\) をクリックし、TableAnchor コンポーネントを検索します。</span><span class="sxs-lookup"><span data-stu-id="f41aa-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="f41aa-141">それを選択してオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="f41aa-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="f41aa-143">[Prefabs]\(プレハブ\) フォルダーの [Project]\(プロジェクト\) パネルで、Table プレハブを、先ほど作成した "TableAnchor" 子オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="f41aa-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a><span data-ttu-id="f41aa-145">結論</span><span class="sxs-lookup"><span data-stu-id="f41aa-145">Congratulations</span></span>

<span data-ttu-id="f41aa-146">これが完了したら、月着陸船を見つけます。</span><span class="sxs-lookup"><span data-stu-id="f41aa-146">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="f41aa-147">その後、Unity プロジェクトに参加するすべてのユーザーが月着陸船ランチャーをあちこちに移動できます。</span><span class="sxs-lookup"><span data-stu-id="f41aa-147">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="f41aa-148">すべての移動が同期されるため、各ユーザーがお互いの操作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="f41aa-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="f41aa-149">これらの概念は、すべての機能を備えた共有コラボレーション エクスペリエンスの基本的な構成要素となります。</span><span class="sxs-lookup"><span data-stu-id="f41aa-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="f41aa-150">すべてのユーザーは共有エクスペリエンスの一部として接続され、オブジェクトの相対的な移動を参照できますが、アプリケーションでは依然としてアバターとオブジェクトを正確に配置できないため、ローカル ユーザーは現実世界の中の同じ場所にあるお互いとオブジェクトを参照できませんでした。</span><span class="sxs-lookup"><span data-stu-id="f41aa-150">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="f41aa-151">ローカル共有エクスペリエンスを固定するために、すべてのデバイスで物理環境についての共通理解が必要です。</span><span class="sxs-lookup"><span data-stu-id="f41aa-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="f41aa-152">このモジュールでは、次のレッスンで実装する [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) を使用してこれを実現します。</span><span class="sxs-lookup"><span data-stu-id="f41aa-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="f41aa-153">次のレッスンに進む前に、ASA 学習モジュールを完了する必要があります。これには、ASA の基本、Azure アカウントとリソースの作成、および共有エクスペリエンスにこれを統合する前に必要なその他の基本的な構成要素が対象として含まれます。</span><span class="sxs-lookup"><span data-stu-id="f41aa-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="f41aa-154">[次のレッスン:5.Azure Spatial Anchors の共有エクスペリエンスへの統合](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="f41aa-154">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>
