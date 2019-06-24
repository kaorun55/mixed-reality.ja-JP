---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328110"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="1cdab-104">同期共有のオブジェクトの移動</span><span class="sxs-lookup"><span data-stu-id="1cdab-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="1cdab-105">このレッスンでは、共有セッションのすべての参加者が共同して、互いの相互作用を表示できるように、オブジェクトの動きを共有する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="1cdab-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="1cdab-106">このレッスンの一部として構築された、太陰暦ランチャーに磨き、[ベース モジュール チュートリアル](mrlearning-base.md)します。</span><span class="sxs-lookup"><span data-stu-id="1cdab-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="1cdab-107">目標:</span><span class="sxs-lookup"><span data-stu-id="1cdab-107">Objectives:</span></span>

- <span data-ttu-id="1cdab-108">3D モデルを共有すると、完了した太陰暦ランチャーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="1cdab-108">Import the completed Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="1cdab-109">3D モデルの動作を共有するプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="1cdab-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="1cdab-110">基本的なマルチ ユーザー コラボレーション アプリケーションを構築する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="1cdab-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="1cdab-111">手順</span><span class="sxs-lookup"><span data-stu-id="1cdab-111">Instructions</span></span>

1. <span data-ttu-id="1cdab-112">(コントロール + S) は、前のレッスンからシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="1cdab-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="1cdab-113">名前を付ける"HLSharedProjectMainPart4.unity"必要なときに見つけやすくなるようにします。</span><span class="sxs-lookup"><span data-stu-id="1cdab-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="1cdab-114">(を選択し、del キーを押します)、"NetworkLobby"オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="1cdab-114">Delete the "NetworkLobby" object (by selecting it and pressing delete).</span></span> <span data-ttu-id="1cdab-115">また、レッスン 2 から「プレハブ」フォルダーに移動し、そこからも"NetworkLobby"プレハブを削除します。</span><span class="sxs-lookup"><span data-stu-id="1cdab-115">Also, go into the "prefabs" folder from lesson 2 and delete the "NetworkLobby" prefab from there as well.</span></span>

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. <span data-ttu-id="1cdab-117">(手順 2、レッスン 2 から) のような場合は、新しいカスタム パッケージをインポートし、インポート、 [LunarModule.unitypackage](linkforModule1 lesson with the lunar module)と[NetworkLobbyReplacement.unitypackage します。](linkforNetworklobbyreplacement package here)</span><span class="sxs-lookup"><span data-stu-id="1cdab-117">Import a new custom package (like step 2 from the lesson 2) and import the [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) and the [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)</span></span>

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. <span data-ttu-id="1cdab-119">ここで、「プレハブ」フォルダーには、階層に新しい"NetworkLobby"プレハブをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1cdab-119">Now, in the "prefabs" folder, drag the new "NetworkLobby" prefab into the hierarchy .</span></span> 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> <span data-ttu-id="1cdab-121">注: 前の手順でインポートした 2 つのパッケージは、"NetworkLobby"プレハブを更新します。</span><span class="sxs-lookup"><span data-stu-id="1cdab-121">note: the two packages we imported in the previous steps updated the "NetworkLobby" prefab.</span></span> <span data-ttu-id="1cdab-122">多くの入力が省けます。</span><span class="sxs-lookup"><span data-stu-id="1cdab-122">It saves you from a lot of typing!</span></span>

5. <span data-ttu-id="1cdab-123">ここで、"MixedRealityPlayspace"の左側にある矢印をクリックし、子ゲーム オブジェクトの"MainCamera"を"SharedPlayground"プレハブを下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="1cdab-123">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="1cdab-124">(削除、プレハブを選択し、キーボードの「削除」をタップします) を prefab"MixedRealityPlayspace"を削除してください。</span><span class="sxs-lookup"><span data-stu-id="1cdab-124">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. <span data-ttu-id="1cdab-126">子オブジェクトとして設定 (新しいオブジェクトを作成、親オブジェクトを右クリックし、「空の作成」を選択) する"SharedPlayground"の親オブジェクトに新しいゲーム オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="1cdab-126">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span>
7. <span data-ttu-id="1cdab-127">新しいオブジェクトを階層内の選択、インスペクターのパネルでオブジェクトの名前を"TableAnchor"に変更します。</span><span class="sxs-lookup"><span data-stu-id="1cdab-127">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="1cdab-128">また、"コンポーネントの追加 をクリックし、"TableAnchor"コンポーネントを検索します。</span><span class="sxs-lookup"><span data-stu-id="1cdab-128">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="1cdab-129">これを選択し、オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="1cdab-129">Select it and add it to the object.</span></span>

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="1cdab-131">注: x 位置を設定 = 1、y =-0.55、および z = 2 です。</span><span class="sxs-lookup"><span data-stu-id="1cdab-131">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="1cdab-132">また、y に回転を設定 = 90 です。</span><span class="sxs-lookup"><span data-stu-id="1cdab-132">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. <span data-ttu-id="1cdab-134">今すぐプロジェクト パネルで、「プレハブ」フォルダーにドラッグ"table"プレハブ"TableAnchor"子オブジェクトを作成しました。</span><span class="sxs-lookup"><span data-stu-id="1cdab-134">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. <span data-ttu-id="1cdab-136">"NetworkRoom"、"NetworkLobby"の下で、階層内の子オブジェクトを選択して、"PhotonView"を検索してインスペクターのパネルで「コンポーネントの追加」をクリックし、スクリプトを追加、"*NetworkRoom*"オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1cdab-136">Select "NetworkRoom," a child object under "NetworkLobby" in the hierachy, and click "add component" in the inspector panel and search for "PhotonView" and add the script to the "*NetworkRoom*" object.</span></span>

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. <span data-ttu-id="1cdab-138">最後に、"DebugWindow"オブジェクトでは、80 と高さを 10 に幅を変更します。</span><span class="sxs-lookup"><span data-stu-id="1cdab-138">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="1cdab-140">結論</span><span class="sxs-lookup"><span data-stu-id="1cdab-140">Congratulations</span></span>

<span data-ttu-id="1cdab-141">これが完了すると、Unity プロジェクトに参加するすべてのユーザーを太陰暦ランチャーを移動できます。</span><span class="sxs-lookup"><span data-stu-id="1cdab-141">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="1cdab-142">各ユーザーが互いの相互作用を表示できるように、すべての動きが同期されます。</span><span class="sxs-lookup"><span data-stu-id="1cdab-142">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="1cdab-143">これらの概念は、全機能装備のコラボレーション エクスペリエンス用の基本的な構成要素として機能します。</span><span class="sxs-lookup"><span data-stu-id="1cdab-143">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="1cdab-144">アプリケーションがアバターとオブジェクトをローカル ユーザーと、同じ物理内でオブジェクトを参照してくださいように正確に配置することはできないが、すべてのユーザーは、共有のエクスペリエンスの一部として接続しているし、オブジェクトの相対的な動きを確認できます、世界です。</span><span class="sxs-lookup"><span data-stu-id="1cdab-144">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="1cdab-145">ローカルの共有エクスペリエンスを固定するためには、すべてのデバイスには、物理環境の共通理解が必要です。</span><span class="sxs-lookup"><span data-stu-id="1cdab-145">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="1cdab-146">このモジュールでこれを実現しますを使用して[Azure 空間アンカー](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) は、次のレッスンでは実装されています。</span><span class="sxs-lookup"><span data-stu-id="1cdab-146">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="1cdab-147">次のレッスンに進む前に、取り上げる ASA の基礎, Azure アカウントとリソースの作成、およびその他の基本的なビルディング ブロックが必要な共有のエクスペリエンスに組み込むことができます前に、ASA ラーニング モジュールを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1cdab-147">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="1cdab-148">[次のレッスン:Sharing(Photon) レッスン 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="1cdab-148">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

