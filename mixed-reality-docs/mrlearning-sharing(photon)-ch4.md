---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: b729de818dfa21df8fbce782a24a611a365ac795
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465223"
---
# <a name="synchronizing-shared-object-movements"></a><span data-ttu-id="a03ba-104">共有されたオブジェクトの動きを同期します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-104">Synchronizing shared object movements</span></span>

<span data-ttu-id="a03ba-105">このレッスンでは、共有セッションのすべての参加者が共同して、互いの相互作用を表示できるように、オブジェクトの動きを共有する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-105">In this lesson, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="a03ba-106">このレッスンの一部として構築された、太陰暦ランチャーに磨き、[ベース モジュール チュートリアル](mrlearning-base.md)します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="a03ba-107">目標:</span><span class="sxs-lookup"><span data-stu-id="a03ba-107">Objectives:</span></span>

- <span data-ttu-id="a03ba-108">共有する 3D モデルとして太陰暦ランチャーに表示します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="a03ba-109">3D モデルの動作を共有するプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="a03ba-110">基本的なマルチ ユーザー コラボレーション アプリケーションを構築する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="a03ba-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="a03ba-111">手順</span><span class="sxs-lookup"><span data-stu-id="a03ba-111">Instructions</span></span>


1. <span data-ttu-id="a03ba-112">前のレッスンでは、(コントロール + S) から、シーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="a03ba-113">という名前を HLSharedProjectMainPart4.unity 必要なときに見つけやすくなるようにします。</span><span class="sxs-lookup"><span data-stu-id="a03ba-113">You can name it HLSharedProjectMainPart4.unity so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="a03ba-114">プロジェクト ウィンドウで、Scripts フォルダー]-> [資産、Visual Studio またはコード エディターを使用することで開く GenericNetSync をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a03ba-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="a03ba-115">行 34 および 38 で、削除、//このレッスンで使用するテーブルのコードをアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="a03ba-115">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="a03ba-116">次に、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-116">next, Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="a03ba-117">プロジェクト ウィンドウで、資産で PhotonRoom.cs ファイルをダブルクリックしますに Scripts フォルダーは、Visual Studio で開く-> です。</span><span class="sxs-lookup"><span data-stu-id="a03ba-117">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="a03ba-118">ステップ 3 で、削除すると同様、//25、26、および 106 行でコードをアクティブにします。![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="a03ba-118">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="a03ba-119">階層ビューでは、NetworkRoom オブジェクトを選択します。![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="a03ba-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="a03ba-120">プロジェクト ビューに移動します。 資産のリソース]-> [プレハブ]-> [です。</span><span class="sxs-lookup"><span data-stu-id="a03ba-120">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="a03ba-121">最初に、ドラッグし、Tableprefab スロット PhotonRoom クラスにテーブルのプレハブをドロップします。</span><span class="sxs-lookup"><span data-stu-id="a03ba-121">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="a03ba-122">次にドラッグし、モジュール Prefab スロット PhotonRoom クラスに LunarModule プレハブをドロップします。</span><span class="sxs-lookup"><span data-stu-id="a03ba-122">Next drag and drop the LunarModule prefab to the Module Prefab slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="a03ba-123">注:Prefab オブジェクトとリリースのいずれかをクリックすると、インスペクターはそのオブジェクトに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="a03ba-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="a03ba-124">をクリックして、ドラッグ、ドロップ、および適切なスロットには、各オブジェクトを解放します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-124">Click, drag, drop, and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="a03ba-125">MixedRealityPlayspace の左側にある矢印をクリックし、SharedPlayground プレハブに下 MainCamera 子ゲーム オブジェクトに移動します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-125">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="a03ba-126">次に、削除、プレハブ、MixedRealityPlayspace、削除、プレハブを選択し、キーボードの「削除」をタップします)。</span><span class="sxs-lookup"><span data-stu-id="a03ba-126">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="a03ba-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="a03ba-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

<span data-ttu-id="a03ba-128">注:0,0,0 に Main Camera と SharedPlayground の両方の位置が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-128">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="a03ba-129">新しいオブジェクトを作成する SharedPlayground の親オブジェクトに子オブジェクトとして設定の新しいゲーム オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-129">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="a03ba-130">親オブジェクトを右クリックし、空アイテムの作成を選択します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-130">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="a03ba-131">新しいオブジェクトを階層内の選択、インスペクターのパネルでオブジェクトの名前を TableAnchor に変更します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-131">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="a03ba-132">また、コンポーネントの追加 をクリックし、TableAnchor コンポーネントを検索します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-132">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="a03ba-133">これを選択し、オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-133">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="a03ba-135">注:X 位置を設定 = 1、y =-0.55、および z = 2 です。</span><span class="sxs-lookup"><span data-stu-id="a03ba-135">Note: Set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="a03ba-136">また、y に回転を設定 = 90 です。</span><span class="sxs-lookup"><span data-stu-id="a03ba-136">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="a03ba-138">今すぐ Prefabs フォルダーに [プロジェクト] パネルから作成した"TableAnchor"の子オブジェクトにテーブルのプレハブをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a03ba-138">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="a03ba-140">最後に、DebugWindow オブジェクトでは、80 と高さを 10 に幅を変更します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-140">Finally, in the DebugWindow object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="a03ba-142">結論</span><span class="sxs-lookup"><span data-stu-id="a03ba-142">Congratulations</span></span>


<span data-ttu-id="a03ba-143">これが完了すると、Unity プロジェクトに参加するすべてのユーザーを太陰暦ランチャーを移動できます。</span><span class="sxs-lookup"><span data-stu-id="a03ba-143">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="a03ba-144">各ユーザーが互いの相互作用を表示できるように、すべての動きが同期されます。</span><span class="sxs-lookup"><span data-stu-id="a03ba-144">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="a03ba-145">これらの概念は、フル機能の共有のコラボレーション エクスペリエンス用の基本的な構成要素として機能します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-145">These concepts serve as the foundational building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="a03ba-146">アプリケーションがアバターとオブジェクトをローカル ユーザーと、同じ物理内でオブジェクトを参照してくださいように正確に配置することはできないが、すべてのユーザーは、共有のエクスペリエンスの一部として接続しているし、オブジェクトの相対的な動きを確認できます、世界です。</span><span class="sxs-lookup"><span data-stu-id="a03ba-146">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="a03ba-147">ローカルの共有エクスペリエンスを固定するためには、すべてのデバイスには、物理環境の共通理解が必要です。</span><span class="sxs-lookup"><span data-stu-id="a03ba-147">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="a03ba-148">このモジュールで私たちを得ることがこれを使用して[Azure 空間アンカー](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) は、次のレッスンで実装します。</span><span class="sxs-lookup"><span data-stu-id="a03ba-148">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="a03ba-149">次のレッスンに進む前にカバーする ASA の基礎, Azure アカウントとリソースの作成、およびその他の基本的なビルディング ブロックが必要な共有のエクスペリエンスに組み込むことができます前に、ASA ラーニング モジュールを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a03ba-149">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="a03ba-150">[次のレッスン:Sharing(Photon) レッスン 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="a03ba-150">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

