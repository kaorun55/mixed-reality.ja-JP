---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: f2e8cef618ea2fbee398ce19f1ba60b712b5fe3e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326765"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="c1ff4-104">**複数のユーザーを接続します。**</span><span class="sxs-lookup"><span data-stu-id="c1ff4-104">**Connecting Multiple Users**</span></span> 

<span data-ttu-id="c1ff4-105">このレッスンでは、ライブの共有エクスペリエンスの一部として複数のユーザーを接続する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-105">In this lesson, we will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="c1ff4-106">このレッスンの目的は、することが、複数のデバイスでアプリケーションを開き、「アバター」表現 (アバターの球体をによって表される) を結合する各ユーザーの表示</span><span class="sxs-lookup"><span data-stu-id="c1ff4-106">By the end of this lesson, you will be able to open the application on multiple devices, and see "avatar" representations of each person that joins (avatars represented by a sphere.)</span></span> 

<span data-ttu-id="c1ff4-107">目標:</span><span class="sxs-lookup"><span data-stu-id="c1ff4-107">Objectives:</span></span>

- <span data-ttu-id="c1ff4-108">アプリケーション内でだじゃれを構成します。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-108">Configure PUN within your application</span></span>
- <span data-ttu-id="c1ff4-109">プレーヤーを構成します。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-109">Configure players</span></span>
- <span data-ttu-id="c1ff4-110">複数のユーザー エクスペリエンスの共有に接続する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="c1ff4-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="c1ff4-111">手順</span><span class="sxs-lookup"><span data-stu-id="c1ff4-111">Instructions</span></span>

1. <span data-ttu-id="c1ff4-112">資産 > リソース > Prefabs フォルダー プロジェクト パネル、ドラッグ アンド ドロップ"NetworkLobby"で、階層にプレハブの次の図に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-112">In the Assets>Resources>Prefabs folder of the project panel, drag and drop the "NetworkLobby" prefab in to the hierarchy, as shown in the image below.</span></span>


![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="c1ff4-114">Prefab"NetworkLobby"を展開すると、"NetworkRoom"と呼ばれる子オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-114">When you expand the prefab "NetworkLobby," you should see a child object called "NetworkRoom."</span></span> <span data-ttu-id="c1ff4-115">選択されていると、インスペクター パネルに移動し、「コンポーネントを追加します」をクリックしてください</span><span class="sxs-lookup"><span data-stu-id="c1ff4-115">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="c1ff4-116">"PhotonView"を検索し、コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-116">Search for "PhotonView" and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="c1ff4-118">階層内の新しい空のゲーム オブジェクトの作成 (階層内を右クリックし、コンテキスト メニューから「空」を選択します)。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-118">Create a new empty game object in the hierarchy (right click in the hierarchy and select "Empty" from the context menu).</span></span> <span data-ttu-id="c1ff4-119">位置 x に設定されていることを確認 = 0、y = 0、z = 0 およびオブジェクトの名前を"PhotonUser"。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-119">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="c1ff4-121">次に、共有のエクスペリエンスを結合する各ユーザーを表す球体を作成します。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-121">Next, we want to create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="c1ff4-122">作成した"PhotonUser"オブジェクトを右クリックし、「3D オブジェクト」に移動し、「球」をクリックしてください</span><span class="sxs-lookup"><span data-stu-id="c1ff4-122">Right click the "PhotonUser" object you just created, go down to "3D Object" and click "Sphere."</span></span> <span data-ttu-id="c1ff4-123">これにより、PhotonUser オブジェクトの子として、球体のゲーム オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-123">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

5. <span data-ttu-id="c1ff4-125">X に球をスケール = 0.06、y = 0.06、ad z 0.06 を = です。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-125">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

6. <span data-ttu-id="c1ff4-127">[プロジェクト] パネルで「プレハブ」フォルダーには、"PhotonUser"ゲーム オブジェクトをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-127">Drag the "PhotonUser" game object into the "prefabs" folder in the project panel.</span></span> <span data-ttu-id="c1ff4-128">次に、シーンから削除します。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-128">Then, delete it from the scene.</span></span> <span data-ttu-id="c1ff4-129">今すぐ生成または共有のエクスペリエンスで新しいプレーヤーをインスタンス化するときに使用されるプレハブを作成しました。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-129">We have now created a prefab that will be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="c1ff4-131">注: は、ゲーム オブジェクトが、階層から削除する前に正常に"prefabs"フォルダーにコピーされたいることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-131">Note: ensure that the game object has successfully copied into the "prefabs" folder before deleting it from your hierarchy.</span></span>

7. <span data-ttu-id="c1ff4-132">(手順 3 のような手順を使用)、階層内の新しいオブジェクトを作成し、"SharedPlayground"という名前を付けます</span><span class="sxs-lookup"><span data-stu-id="c1ff4-132">Create a new object in the hierarchy (using similar instructions to that of Step 3), and name it "SharedPlayground."</span></span> <span data-ttu-id="c1ff4-133">「コンポーネントの追加」と「一般的なネットワーク マネージャー」の検索 をクリックし、クリックして、汎用ネットワーク マネージャー コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-133">Then, click "Add Component" and search for "generic network manager" and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="c1ff4-134">オブジェクトの位置を x に変更 = 0、y = 0、および z = 0。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-134">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="c1ff4-136">結論</span><span class="sxs-lookup"><span data-stu-id="c1ff4-136">Congratulations</span></span>

<span data-ttu-id="c1ff4-137">上記すべての手順が完了すると、再生ボタンをクリックし、HoloLens 2 を接続するときに、ビルド プロセスが完了すると頭を移動すると、移動、球が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-137">Once all the steps above are complete, and the build process is complete, when you press the play button and connect your HoloLens 2, you should see a sphere moving around as you move your head!</span></span> <span data-ttu-id="c1ff4-138">これは、Unity プロジェクトを結合するすべてのユーザーに対して表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1ff4-138">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="c1ff4-139">[次のレッスン:Sharing(Photon) レッスン 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="c1ff4-139">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

