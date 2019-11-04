---
title: 複数ユーザー機能のチュートリアル-3. 複数のユーザーの接続
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: a6d1a269f45b4aaf7cbd8fea948ddcbdf0bf18e2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437736"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="c1019-105">3. 複数のユーザーを接続する</span><span class="sxs-lookup"><span data-stu-id="c1019-105">3. Connecting multiple users</span></span>

<span data-ttu-id="c1019-106">このレッスンでは、ライブ共有エクスペリエンスの一部として複数のユーザーを接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1019-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="c1019-107">このレッスンを終了すると、複数のデバイスでアプリケーションを開き、参加している各ユーザーの球体で表されるアバターを確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c1019-107">By the end of this lesson, you'll be able to open the application on multiple devices and see the avatar, represented by a sphere for each person that joins.</span></span> 

<span data-ttu-id="c1019-108">事項</span><span class="sxs-lookup"><span data-stu-id="c1019-108">Objectives:</span></span>

- <span data-ttu-id="c1019-109">アプリケーション内でさしあたっを構成する</span><span class="sxs-lookup"><span data-stu-id="c1019-109">Configure PUN within your application</span></span>
- <span data-ttu-id="c1019-110">プレーヤーの構成</span><span class="sxs-lookup"><span data-stu-id="c1019-110">Configure players</span></span>
- <span data-ttu-id="c1019-111">共有エクスペリエンスで複数のユーザーを接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1019-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="c1019-112">手順</span><span class="sxs-lookup"><span data-stu-id="c1019-112">Instructions</span></span>

1. <span data-ttu-id="c1019-113">次の図に示すように、[アセット-> Resources-> Prefabs] フォルダーの [プロジェクト] パネルで、NetworkLobby prefab を階層にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="c1019-113">In the Assets->Resources->Prefabs folder of the Project panel, drag and drop the NetworkLobby prefab into the hierarchy as shown in the image below.</span></span>

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="c1019-115">NetworkLobby を展開すると、Networklobby という子オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1019-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="c1019-116">NetworkRoom を選択した状態で、[インスペクター] パネルにアクセスし、[コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1019-116">With NetworkRoom selected, go into the Inspector panel and click Add Component.</span></span> <span data-ttu-id="c1019-117">PhotonView を検索し、コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="c1019-117">Search for PhotonView and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="c1019-119">階層内に新しい空のゲームオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1019-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="c1019-120">階層内を右クリックし、コンテキストメニューから [空] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c1019-120">Right-click in the hierarchy and select Empty from the Context menu.</span></span> <span data-ttu-id="c1019-121">位置が x = 0、y = 0、z = 0 に設定されていることを確認し、オブジェクトに PhotonUser という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1019-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="c1019-123">[コンポーネントの追加] をクリックし、「汎用 Net Sync」と入力します。汎用 Net Sync クラスを選択します。</span><span class="sxs-lookup"><span data-stu-id="c1019-123">Click Add Component and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="c1019-124">クラスが表示されたら、[ユーザー] チェックボックスをオンにしてオンにします。</span><span class="sxs-lookup"><span data-stu-id="c1019-124">When the class appears, click the User check box to turn it on.</span></span> 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="c1019-126">[コンポーネントの追加] をもう一度クリックし、「Photon View」と入力します。</span><span class="sxs-lookup"><span data-stu-id="c1019-126">Click Add Component again, and type Photon View.</span></span> <span data-ttu-id="c1019-127">ドロップダウンリストに表示される Photon View クラスを選択します。</span><span class="sxs-lookup"><span data-stu-id="c1019-127">Select the Photon View class that appears in the drop-down list.</span></span>

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="c1019-129">汎用 Net Sync クラスのファイルアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1019-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="c1019-130">Photon ビューの [観測されたコンポーネント] フィールドにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="c1019-130">Drag and drop it in the Photon View's Observed Components field.</span></span> 

![module3chapter3updateStep6im](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="c1019-132">次に、共有エクスペリエンスに参加する各ユーザーを表す球体を作成します。</span><span class="sxs-lookup"><span data-stu-id="c1019-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="c1019-133">先ほど作成した PhotonUser オブジェクトを右クリックし、[3D オブジェクト] までスクロールして [球] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1019-133">Right-click the PhotonUser object you just created, scroll-down to "3D Object and click Sphere.</span></span> <span data-ttu-id="c1019-134">これにより、PhotonUser オブジェクトの子として球ゲームオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c1019-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="c1019-136">球を x = 0.06、y = 0.06、ad z = 0.06 にスケールダウンします。</span><span class="sxs-lookup"><span data-stu-id="c1019-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="c1019-138">PhotonUser game オブジェクトを [プロジェクト] パネルの Prefabs フォルダーにドラッグし、シーンから削除します。</span><span class="sxs-lookup"><span data-stu-id="c1019-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel and then delete it from the scene.</span></span> <span data-ttu-id="c1019-139">これで、共有エクスペリエンスで新しいプレーヤーを生成またはインスタンス化するときに使用できる事前 fab が作成されました。</span><span class="sxs-lookup"><span data-stu-id="c1019-139">You have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="c1019-141">注: Prefabs フォルダーを階層から削除する前に、game オブジェクトが正常にコピーされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c1019-141">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="c1019-142">手順 3. の指示に従って、階層内に新しいオブジェクトを作成し、「SharedPlayground グラウンド」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1019-142">Create a new object in the hierarchy by following the instructions in Step 3 and name it SharedPlayground.</span></span> <span data-ttu-id="c1019-143">次に、[コンポーネントの追加] をクリックし、汎用ネットワークマネージャーを検索します。</span><span class="sxs-lookup"><span data-stu-id="c1019-143">Then, click Add Component and search for generic network manager.</span></span>  <span data-ttu-id="c1019-144">もう一度クリックして、一般的なネットワークマネージャーコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="c1019-144">Click it again to add the Generic Network Manager component.</span></span> <span data-ttu-id="c1019-145">オブジェクトの位置を x = 0、y = 0、z = 0 に変更します。</span><span class="sxs-lookup"><span data-stu-id="c1019-145">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="c1019-147">結論</span><span class="sxs-lookup"><span data-stu-id="c1019-147">Congratulations</span></span>

<span data-ttu-id="c1019-148">上記のすべての手順が完了し、ビルドプロセスも完了したら、[Play] \ (再生 \) ボタンを押して HoloLens 2 に接続します。</span><span class="sxs-lookup"><span data-stu-id="c1019-148">Once all the steps above are complete and the build process is also complete, press the Play button and connect your HoloLens 2.</span></span> <span data-ttu-id="c1019-149">頭を移動すると球が動いていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="c1019-149">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="c1019-150">これは、Unity プロジェクトに参加するすべてのユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1019-150">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="c1019-151">[次のレッスン: 4. オブジェクトの移動を複数のユーザーと共有する](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="c1019-151">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>

