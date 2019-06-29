---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 4625acfcb3353e9537961a444012452139705359
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465213"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="de0b5-104">**複数のユーザーを接続します。**</span><span class="sxs-lookup"><span data-stu-id="de0b5-104">**Connecting multiple users**</span></span> 

<span data-ttu-id="de0b5-105">このレッスンでは、ライブの共有エクスペリエンスの一部として複数のユーザーを接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="de0b5-106">このレッスンの目的は、複数のデバイスでアプリケーションを開き、球体の場合、結合する人の表現によって表される、アバターを表示するようになります。</span><span class="sxs-lookup"><span data-stu-id="de0b5-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="de0b5-107">目標:</span><span class="sxs-lookup"><span data-stu-id="de0b5-107">Objectives:</span></span>

- <span data-ttu-id="de0b5-108">アプリケーション内でだじゃれを構成します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-108">Configure PUN within your application</span></span>
- <span data-ttu-id="de0b5-109">プレーヤーを構成します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-109">Configure players</span></span>
- <span data-ttu-id="de0b5-110">複数のユーザー エクスペリエンスの共有に接続する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="de0b5-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="de0b5-111">手順</span><span class="sxs-lookup"><span data-stu-id="de0b5-111">Instructions</span></span>

1. <span data-ttu-id="de0b5-112">資産-> リソース メニューの プロジェクト パネルで Prefabs フォルダーにドラッグ アンド次の図に示すように、階層で NetworkLobby プレハブを削除します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="de0b5-114">NetworkLobby を展開すると、NetworkRoom と呼ばれる子オブジェクトを確認します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="de0b5-115">NetworkRoom が選択されている、Inspector パネルに移動し、コンポーネントの追加 をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de0b5-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="de0b5-116">PhotonView を検索し、コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-116">Search for PhotonView and add the component.</span></span>

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="de0b5-118">階層内の新しい空のゲーム オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="de0b5-119">階層内を右クリックし、コンテキスト メニューから空を選択します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="de0b5-120">位置 x に設定されていることを確認 = 0、y = 0、z = 0 および PhotonUser、オブジェクトの名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="de0b5-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="de0b5-122">[コンポーネントの追加] をクリックし、汎用の差分同期を入力します。ジェネリックの差分同期クラスを選択します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="de0b5-123">クラスが表示されたら、有効にするには、ユーザー チェック ボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="de0b5-123">When the class appears, click on the User check box to turn it on.</span></span> 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="de0b5-125">ここでも、コンポーネントの追加 をクリックし、Photon ビューを入力します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="de0b5-126">ドロップダウン リストで表示される Photon ビュー クラスを選択します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-126">Select the Photon View class that appears in the drop-down list.</span></span>

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="de0b5-128">ジェネリックの差分同期クラスのファイルのアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="de0b5-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="de0b5-129">ドラッグ アンド ドロップ Photon ビューのコンポーネントの検出フィールド。</span><span class="sxs-lookup"><span data-stu-id="de0b5-129">Drag and drop it in the Photon View's Observed Components field.</span></span> ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="de0b5-131">次に、共有のエクスペリエンスを結合する各ユーザーを表す球体を作成します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="de0b5-132">作成した PhotonUser オブジェクトと scrolldown を右クリックして"3 D オブジェクトをクリックして、球。</span><span class="sxs-lookup"><span data-stu-id="de0b5-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="de0b5-133">これにより、PhotonUser オブジェクトの子として、球体のゲーム オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="de0b5-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="de0b5-135">X に球をスケール = 0.06、y = 0.06、ad z 0.06 を = です。</span><span class="sxs-lookup"><span data-stu-id="de0b5-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="de0b5-137">プロジェクト パネルで、Prefabs フォルダーに PhotonUser ゲーム オブジェクトをドラッグし、シーンから削除します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="de0b5-138">今すぐ生成または共有のエクスペリエンスで新しいプレーヤーをインスタンス化するときに使用できるプレハブを作成しました。</span><span class="sxs-lookup"><span data-stu-id="de0b5-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="de0b5-140">注: は、ゲーム オブジェクトが、階層から削除する前に正常に Prefabs フォルダーにコピーされたいることを確認します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="de0b5-141">手順 3 での手順に従って、階層内の新しいオブジェクトを作成し、SharedPlayground という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="de0b5-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="de0b5-142">[コンポーネントの追加] をクリックし汎用ネットワーク マネージャーを検索し、クリックして、汎用ネットワーク マネージャー コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="de0b5-143">オブジェクトの位置を x に変更 = 0、y = 0、および z = 0。</span><span class="sxs-lookup"><span data-stu-id="de0b5-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="de0b5-145">結論</span><span class="sxs-lookup"><span data-stu-id="de0b5-145">Congratulations</span></span>

<span data-ttu-id="de0b5-146">上記の手順が完了すると、ビルド プロセスが完了することも、後は、再生ボタンをクリックし、HoloLens 2 を接続します。</span><span class="sxs-lookup"><span data-stu-id="de0b5-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="de0b5-147">頭の中を移動すると、移動、球が表示されます。</span><span class="sxs-lookup"><span data-stu-id="de0b5-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="de0b5-148">これは、Unity プロジェクトを結合するすべてのユーザーに対して表示されます。</span><span class="sxs-lookup"><span data-stu-id="de0b5-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="de0b5-149">[次のレッスン:Sharing(Photon) レッスン 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="de0b5-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

