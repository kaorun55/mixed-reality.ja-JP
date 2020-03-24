---
title: マルチユーザー機能のチュートリアル - 3. 複数のユーザーの接続
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031228"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="e5421-105">3.複数のユーザーの接続</span><span class="sxs-lookup"><span data-stu-id="e5421-105">3. Connecting multiple users</span></span>

<span data-ttu-id="e5421-106">このレッスンでは、ライブ共有エクスペリエンスの一部として複数のユーザーを接続する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="e5421-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="e5421-107">このレッスンを終了すると、複数のデバイスでアプリケーションを開き、球体で表される、参加する各ユーザーのアバターを表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e5421-107">By the end of this lesson, you'll be able to open the application on multiple devices and see the avatar, represented by a sphere for each person that joins.</span></span>

## <a name="objectives"></a><span data-ttu-id="e5421-108">目標</span><span class="sxs-lookup"><span data-stu-id="e5421-108">Objectives</span></span>

* <span data-ttu-id="e5421-109">アプリケーション内で PUN を構成する</span><span class="sxs-lookup"><span data-stu-id="e5421-109">Configure PUN within your application</span></span>
* <span data-ttu-id="e5421-110">プレーヤーを構成する</span><span class="sxs-lookup"><span data-stu-id="e5421-110">Configure players</span></span>
* <span data-ttu-id="e5421-111">共有エクスペリエンスで複数のユーザーを接続する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="e5421-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="e5421-112">手順</span><span class="sxs-lookup"><span data-stu-id="e5421-112">Instructions</span></span>

1. <span data-ttu-id="e5421-113">次の図に示すように、[Project]\(プロジェクト\) パネルの [Assets]\(アセット\) -> [Resources]\(リソース\) -> [Prefabs] フォルダーで、NetworkLobby プレハブを階層にドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="e5421-113">In the Assets->Resources->Prefabs folder of the Project panel, drag and drop the NetworkLobby prefab into the hierarchy as shown in the image below.</span></span>

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="e5421-115">NetworkLobby を展開すると、NetworkRoom という子オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e5421-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="e5421-116">NetworkRoom を選択した状態で、[Inspector]\(インスペクター\) パネルに移動し、[Add Component]\(コンポーネントの追加\) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5421-116">With NetworkRoom selected, go into the Inspector panel and click Add Component.</span></span> <span data-ttu-id="e5421-117">PhotonView を検索し、このコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="e5421-117">Search for PhotonView and add the component.</span></span>

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="e5421-119">階層内に新しい空のゲーム オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e5421-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="e5421-120">階層内を右クリックし、コンテキスト メニューから [Empty]\(空\) を選択します。</span><span class="sxs-lookup"><span data-stu-id="e5421-120">Right-click in the hierarchy and select Empty from the Context menu.</span></span> <span data-ttu-id="e5421-121">位置が x =0、y=0、z=0 に設定されていることを確認し、オブジェクトに PhotonUser という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="e5421-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="e5421-123">[Add Component]\(コンポーネントの追加\) をクリックし、「Generic Net Sync」と入力します。Generic Net Sync クラスを選択します。</span><span class="sxs-lookup"><span data-stu-id="e5421-123">Click Add Component and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="e5421-124">クラスが表示されたら、[User]\(ユーザー\) チェック ボックスをクリックしてオンにします。</span><span class="sxs-lookup"><span data-stu-id="e5421-124">When the class appears, click the User check box to turn it on.</span></span>

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="e5421-126">[Add Component]\(コンポーネントの追加\) をもう一度クリックし、「Photon View」と入力します。</span><span class="sxs-lookup"><span data-stu-id="e5421-126">Click Add Component again, and type Photon View.</span></span> <span data-ttu-id="e5421-127">ドロップダウン リストに表示される Photon View クラスを選択します。</span><span class="sxs-lookup"><span data-stu-id="e5421-127">Select the Photon View class that appears in the drop-down list.</span></span>

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="e5421-129">Generic Net Sync クラスの [File]\(ファイル\) アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5421-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="e5421-130">それを Photon View の[Observed Components]\(観測されたコンポーネント\) フィールドにドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="e5421-130">Drag and drop it in the Photon View's Observed Components field.</span></span>

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. <span data-ttu-id="e5421-132">次に、共有エクスペリエンスに参加する各ユーザーを表す球体を作成します。</span><span class="sxs-lookup"><span data-stu-id="e5421-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="e5421-133">先ほど作成した PhotonUser オブジェクトを右クリックし、[3D Object]\(3D オブジェクト\) まで下にスクロールして、[Sphere]\(球体\) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5421-133">Right-click the PhotonUser object you just created, scroll-down to "3D Object and click Sphere.</span></span> <span data-ttu-id="e5421-134">これにより、PhotonUser オブジェクトの子として球体ゲーム オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e5421-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="e5421-136">球体を x=0.06、y=0.06、z=0.06 にスケール ダウンします。</span><span class="sxs-lookup"><span data-stu-id="e5421-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="e5421-138">PhotonUser ゲーム オブジェクトを [Project]\(プロジェクト\) パネルの [Prefabs] フォルダーにドラッグし、シーンから削除します。</span><span class="sxs-lookup"><span data-stu-id="e5421-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel and then delete it from the scene.</span></span> <span data-ttu-id="e5421-139">これで、共有エクスペリエンスで新しいプレーヤーを生成またはインスタンス化するときに使用できるプレハブが作成されました。</span><span class="sxs-lookup"><span data-stu-id="e5421-139">You have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    ><span data-ttu-id="e5421-141">階層から削除する前に、ゲーム オブジェクトが [Prefabs] フォルダーに正常にコピーされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e5421-141">Ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="e5421-142">手順 3 の指示に従って階層内に新しいオブジェクトを作成し、SharedPlayground という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="e5421-142">Create a new object in the hierarchy by following the instructions in Step 3 and name it SharedPlayground.</span></span> <span data-ttu-id="e5421-143">次に、[Add Component]\(コンポーネントの追加\) をクリックし、Generic Network Manager を検索します。</span><span class="sxs-lookup"><span data-stu-id="e5421-143">Then, click Add Component and search for generic network manager.</span></span>  <span data-ttu-id="e5421-144">もう一度クリックして、Generic Network Manager コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="e5421-144">Click it again to add the Generic Network Manager component.</span></span> <span data-ttu-id="e5421-145">オブジェクトの位置を x=0、y=0、z=0 に変更します。</span><span class="sxs-lookup"><span data-stu-id="e5421-145">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a><span data-ttu-id="e5421-147">結論</span><span class="sxs-lookup"><span data-stu-id="e5421-147">Congratulations</span></span>

<span data-ttu-id="e5421-148">上記のすべての手順が完了し、ビルド プロセスも完了したら、[Play]\(プレイ\) ボタンを押し、HoloLens 2 を接続します。</span><span class="sxs-lookup"><span data-stu-id="e5421-148">Once all the steps above are complete and the build process is also complete, press the Play button and connect your HoloLens 2.</span></span> <span data-ttu-id="e5421-149">頭を動かすと球体が動きまわるのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e5421-149">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="e5421-150">これは、Unity プロジェクトに参加しているすべてのユーザーに対して表示されます。</span><span class="sxs-lookup"><span data-stu-id="e5421-150">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="e5421-151">[次のレッスン:4.オブジェクトの動きの複数のユーザーとの共有](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="e5421-151">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>
