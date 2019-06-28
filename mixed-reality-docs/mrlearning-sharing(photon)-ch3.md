---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 33f265c6333f12f7ec73ecb0c1e5730b168d4bde
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415913"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="bd6d1-104">**複数のユーザーを接続します。**</span><span class="sxs-lookup"><span data-stu-id="bd6d1-104">**Connecting Multiple Users**</span></span> 

<span data-ttu-id="bd6d1-105">このレッスンでは、ライブの共有エクスペリエンスの一部として複数のユーザーを接続する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-105">In this lesson, we will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="bd6d1-106">このレッスンの目的は、することが、複数のデバイスでアプリケーションを開き、「アバター」表現 (アバターの球体をによって表される) を結合する各ユーザーの表示</span><span class="sxs-lookup"><span data-stu-id="bd6d1-106">By the end of this lesson, you will be able to open the application on multiple devices, and see "avatar" representations of each person that joins (avatars represented by a sphere.)</span></span> 

<span data-ttu-id="bd6d1-107">目標:</span><span class="sxs-lookup"><span data-stu-id="bd6d1-107">Objectives:</span></span>

- <span data-ttu-id="bd6d1-108">アプリケーション内でだじゃれを構成します。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-108">Configure PUN within your application</span></span>
- <span data-ttu-id="bd6d1-109">プレーヤーを構成します。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-109">Configure players</span></span>
- <span data-ttu-id="bd6d1-110">複数のユーザー エクスペリエンスの共有に接続する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="bd6d1-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="bd6d1-111">手順</span><span class="sxs-lookup"><span data-stu-id="bd6d1-111">Instructions</span></span>

1. <span data-ttu-id="bd6d1-112">資産 > リソース > Prefabs フォルダー プロジェクト パネル、ドラッグ アンド ドロップ"NetworkLobby"で、階層にプレハブの次の図に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-112">In the Assets>Resources>Prefabs folder of the project panel, drag and drop the "NetworkLobby" prefab in to the hierarchy, as shown in the image below.</span></span>


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="bd6d1-114">Prefab"NetworkLobby"を展開すると、"NetworkRoom"と呼ばれる子オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-114">When you expand the prefab "NetworkLobby," you should see a child object called "NetworkRoom."</span></span> <span data-ttu-id="bd6d1-115">選択されていると、インスペクター パネルに移動し、「コンポーネントを追加します」をクリックしてください</span><span class="sxs-lookup"><span data-stu-id="bd6d1-115">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="bd6d1-116">"PhotonView"を検索し、コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-116">Search for "PhotonView" and add the component.</span></span>

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="bd6d1-118">階層内の新しい空のゲーム オブジェクトの作成 (階層内を右クリックし、コンテキスト メニューから「空」を選択します)。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-118">Create a new empty game object in the hierarchy (right click in the hierarchy and select "Empty" from the context menu).</span></span> <span data-ttu-id="bd6d1-119">位置 x に設定されていることを確認 = 0、y = 0、z = 0 およびオブジェクトの名前を"PhotonUser"。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-119">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="bd6d1-121">「コンポーネントの追加」ボタンをクリックしてと"汎用 Net Sync"を入力し、汎用の差分同期クラスを選択します。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-121">Click on the "Add Component" button and type "Generic Net Sync" and select the Generic Net Sync class.</span></span> <span data-ttu-id="bd6d1-122">クラスが表示されたらは、有効にする「ユーザー」のチェック ボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-122">Once the class appears, click on the "User" check box to turn it on.</span></span> 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="bd6d1-124">もう一度「コンポーネントの追加」をクリックし、入力"Photon View"し、ドロップダウン リストで表示される Photon ビュー クラスを選択します。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-124">Again click on "Add Component" and then type "Photon View" and select the Photon View class that appears in the drop down list.</span></span>

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="bd6d1-126">今すぐジェネリック Net 同期クラスの場合にファイルのアイコンをクリックし、ドラッグし、Photon ビューの「コンポーネントの監視」フィールドにドロップします。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-126">Now click on the File icon in for the Generic Net Sync class, then drag and drop it to the Photon View's "Observed Components" field.</span></span> ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="bd6d1-128">次に、共有のエクスペリエンスを結合する各ユーザーを表す球体を作成します。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-128">Next, we want to create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="bd6d1-129">作成した"PhotonUser"オブジェクトを右クリックし、「3D オブジェクト」に移動し、「球」をクリックしてください</span><span class="sxs-lookup"><span data-stu-id="bd6d1-129">Right click the "PhotonUser" object you just created, go down to "3D Object" and click "Sphere."</span></span> <span data-ttu-id="bd6d1-130">これにより、PhotonUser オブジェクトの子として、球体のゲーム オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-130">This will create a sphere game object as a child of the PhotonUser object.</span></span>

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="bd6d1-132">X に球をスケール = 0.06、y = 0.06、ad z 0.06 を = です。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-132">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="bd6d1-134">[プロジェクト] パネルで「プレハブ」フォルダーには、"PhotonUser"ゲーム オブジェクトをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-134">Drag the "PhotonUser" game object into the "prefabs" folder in the project panel.</span></span> <span data-ttu-id="bd6d1-135">次に、シーンから削除します。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-135">Then, delete it from the scene.</span></span> <span data-ttu-id="bd6d1-136">今すぐ生成または共有のエクスペリエンスで新しいプレーヤーをインスタンス化するときに使用されるプレハブを作成しました。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-136">We have now created a prefab that will be used when spawning or instantiating new players in a shared experience.</span></span>

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="bd6d1-138">注: は、ゲーム オブジェクトが、階層から削除する前に正常に"prefabs"フォルダーにコピーされたいることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-138">Note: ensure that the game object has successfully copied into the "prefabs" folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="bd6d1-139">(手順 3 のような手順を使用)、階層内の新しいオブジェクトを作成し、"SharedPlayground"という名前を付けます</span><span class="sxs-lookup"><span data-stu-id="bd6d1-139">Create a new object in the hierarchy (using similar instructions to that of Step 3), and name it "SharedPlayground."</span></span> <span data-ttu-id="bd6d1-140">「コンポーネントの追加」と「一般的なネットワーク マネージャー」の検索 をクリックし、クリックして、汎用ネットワーク マネージャー コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-140">Then, click "Add Component" and search for "generic network manager" and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="bd6d1-141">オブジェクトの位置を x に変更 = 0、y = 0、および z = 0。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-141">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="bd6d1-143">結論</span><span class="sxs-lookup"><span data-stu-id="bd6d1-143">Congratulations</span></span>

<span data-ttu-id="bd6d1-144">上記すべての手順が完了すると、再生ボタンをクリックし、HoloLens 2 を接続するときに、ビルド プロセスが完了すると頭を移動すると、移動、球が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-144">Once all the steps above are complete, and the build process is complete, when you press the play button and connect your HoloLens 2, you should see a sphere moving around as you move your head!</span></span> <span data-ttu-id="bd6d1-145">これは、Unity プロジェクトを結合するすべてのユーザーに対して表示されます。</span><span class="sxs-lookup"><span data-stu-id="bd6d1-145">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="bd6d1-146">[次のレッスン:Sharing(Photon) レッスン 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="bd6d1-146">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

