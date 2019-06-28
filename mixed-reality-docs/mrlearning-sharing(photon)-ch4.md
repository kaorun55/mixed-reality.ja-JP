---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416013"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="58e65-104">同期共有のオブジェクトの移動</span><span class="sxs-lookup"><span data-stu-id="58e65-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="58e65-105">このレッスンでは、共有セッションのすべての参加者が共同して、互いの相互作用を表示できるように、オブジェクトの動きを共有する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="58e65-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="58e65-106">このレッスンの一部として構築された、太陰暦ランチャーに磨き、[ベース モジュール チュートリアル](mrlearning-base.md)します。</span><span class="sxs-lookup"><span data-stu-id="58e65-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="58e65-107">目標:</span><span class="sxs-lookup"><span data-stu-id="58e65-107">Objectives:</span></span>

- <span data-ttu-id="58e65-108">共有する 3D モデルとして太陰暦ランチャーに表示します。</span><span class="sxs-lookup"><span data-stu-id="58e65-108">Bring in the Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="58e65-109">3D モデルの動作を共有するプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="58e65-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="58e65-110">基本的なマルチ ユーザー コラボレーション アプリケーションを構築する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="58e65-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="58e65-111">手順</span><span class="sxs-lookup"><span data-stu-id="58e65-111">Instructions</span></span>

1. <span data-ttu-id="58e65-112">(コントロール + S) は、前のレッスンからシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="58e65-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="58e65-113">名前を付ける"HLSharedProjectMainPart4.unity"必要なときに見つけやすくなるようにします。</span><span class="sxs-lookup"><span data-stu-id="58e65-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="58e65-114">プロジェクト ウィンドウの 資産 > Scripts フォルダーでは、Visual Studio またはコード エディターを使用することで開く GenericNetSync ダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="58e65-114">In the Project window, in the Assets > Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="58e65-115">34 と 38 の行では、削除、"//"このレッスンで使用するテーブルのコードをアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="58e65-115">On lines 34 and 38, remove the "//" to activate the code for the Table that we will use in this lesson.</span></span>  <span data-ttu-id="58e65-116">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="58e65-116">Then Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="58e65-117">[プロジェクト] ウィンドウで、資産の PhotonRoom.cs ファイルをダブルクリックします。 > Scripts フォルダーをもう一度 Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="58e65-117">In the project window, double click on the PhotonRoom.cs file in the Assets > Scripts folder to again open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="58e65-118">同じように手順 3 で削除する必要があります、"//"25、26、および 106 行でコードをアクティブにします。![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="58e65-118">Just like in step 3 we need to remove the "//" to activate the code at lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="58e65-119">階層ビューでは、NetworkRoom オブジェクトを選択します。![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="58e65-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="58e65-120">プロジェクト ビューでは、資産に移動します > リソース > プレハブします。</span><span class="sxs-lookup"><span data-stu-id="58e65-120">In the project view, navigate to Assets > Resources > Prefabs.</span></span> <span data-ttu-id="58e65-121">最初に、ドラッグし、テーブル プレハブを PhotonRoom クラスの"Tableprefab"スロットにドロップします。</span><span class="sxs-lookup"><span data-stu-id="58e65-121">First, drag and drop the Table prefab to the "Tableprefab" slot on the PhotonRoom class.</span></span> <span data-ttu-id="58e65-122">次にドラッグし、PhotonRoom クラスのプレハブ"モジュール"スロットに LunarModule プレハブをドロップします。</span><span class="sxs-lookup"><span data-stu-id="58e65-122">Next drag and drop the LunarModule prefab to the "Module Prefab" slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="58e65-123">注:Prefab オブジェクトとリリースのいずれかをクリックすると、インスペクターはそのオブジェクトに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="58e65-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="58e65-124">をクリックして、ドラッグ、ドロップおよび適切なスロットには、各オブジェクトを解放します。</span><span class="sxs-lookup"><span data-stu-id="58e65-124">Click, drag, drop and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="58e65-125">ここで、"MixedRealityPlayspace"の左側にある矢印をクリックし、子ゲーム オブジェクトの"MainCamera"を"SharedPlayground"プレハブを下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="58e65-125">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="58e65-126">(削除、プレハブを選択し、キーボードの「削除」をタップします) を prefab"MixedRealityPlayspace"を削除してください。</span><span class="sxs-lookup"><span data-stu-id="58e65-126">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

<span data-ttu-id="58e65-128">注:0,0,0 に Main Camera と SharedPlayground の両方の位置が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="58e65-128">note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="58e65-129">子オブジェクトとして設定 (新しいオブジェクトを作成、親オブジェクトを右クリックし、「空の作成」を選択) する"SharedPlayground"の親オブジェクトに新しいゲーム オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="58e65-129">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span> 

10. <span data-ttu-id="58e65-130">新しいオブジェクトを階層内の選択、インスペクターのパネルでオブジェクトの名前を"TableAnchor"に変更します。</span><span class="sxs-lookup"><span data-stu-id="58e65-130">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="58e65-131">また、"コンポーネントの追加 をクリックし、"TableAnchor"コンポーネントを検索します。</span><span class="sxs-lookup"><span data-stu-id="58e65-131">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="58e65-132">これを選択し、オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="58e65-132">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="58e65-134">注: x 位置を設定 = 1、y =-0.55、および z = 2 です。</span><span class="sxs-lookup"><span data-stu-id="58e65-134">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="58e65-135">また、y に回転を設定 = 90 です。</span><span class="sxs-lookup"><span data-stu-id="58e65-135">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="58e65-137">今すぐプロジェクト パネルで、「プレハブ」フォルダーにドラッグ"table"プレハブ"TableAnchor"子オブジェクトを作成しました。</span><span class="sxs-lookup"><span data-stu-id="58e65-137">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="58e65-139">最後に、"DebugWindow"オブジェクトでは、80 と高さを 10 に幅を変更します。</span><span class="sxs-lookup"><span data-stu-id="58e65-139">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="58e65-141">結論</span><span class="sxs-lookup"><span data-stu-id="58e65-141">Congratulations</span></span>

<span data-ttu-id="58e65-142">これが完了すると、Unity プロジェクトに参加するすべてのユーザーを太陰暦ランチャーを移動できます。</span><span class="sxs-lookup"><span data-stu-id="58e65-142">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="58e65-143">各ユーザーが互いの相互作用を表示できるように、すべての動きが同期されます。</span><span class="sxs-lookup"><span data-stu-id="58e65-143">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="58e65-144">これらの概念は、全機能装備のコラボレーション エクスペリエンス用の基本的な構成要素として機能します。</span><span class="sxs-lookup"><span data-stu-id="58e65-144">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="58e65-145">アプリケーションがアバターとオブジェクトをローカル ユーザーと、同じ物理内でオブジェクトを参照してくださいように正確に配置することはできないが、すべてのユーザーは、共有のエクスペリエンスの一部として接続しているし、オブジェクトの相対的な動きを確認できます、世界です。</span><span class="sxs-lookup"><span data-stu-id="58e65-145">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="58e65-146">ローカルの共有エクスペリエンスを固定するためには、すべてのデバイスには、物理環境の共通理解が必要です。</span><span class="sxs-lookup"><span data-stu-id="58e65-146">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="58e65-147">このモジュールでこれを実現しますを使用して[Azure 空間アンカー](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) は、次のレッスンでは実装されています。</span><span class="sxs-lookup"><span data-stu-id="58e65-147">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="58e65-148">次のレッスンに進む前に、取り上げる ASA の基礎, Azure アカウントとリソースの作成、およびその他の基本的なビルディング ブロックが必要な共有のエクスペリエンスに組み込むことができます前に、ASA ラーニング モジュールを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58e65-148">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="58e65-149">[次のレッスン:Sharing(Photon) レッスン 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="58e65-149">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

