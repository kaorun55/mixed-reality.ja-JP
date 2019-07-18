---
title: HoloLens 2 用 MR Learning 共有モジュール
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 92bea1f3130f67645c10e36fe40cd4bc6f8b9151
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293665"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="77b35-104">複数のユーザーの接続</span><span class="sxs-lookup"><span data-stu-id="77b35-104">Connecting multiple users</span></span>

<span data-ttu-id="77b35-105">このレッスンでは、ライブ共有エクスペリエンスの一部として複数のユーザーを接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="77b35-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="77b35-106">このレッスンを終了すると、複数のデバイスでアプリケーションを開くことができます。また、アバターは、参加する各ユーザーの球体で表現されます。</span><span class="sxs-lookup"><span data-stu-id="77b35-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="77b35-107">事項</span><span class="sxs-lookup"><span data-stu-id="77b35-107">Objectives:</span></span>

- <span data-ttu-id="77b35-108">アプリケーション内でさしあたっを構成する</span><span class="sxs-lookup"><span data-stu-id="77b35-108">Configure PUN within your application</span></span>
- <span data-ttu-id="77b35-109">プレーヤーの構成</span><span class="sxs-lookup"><span data-stu-id="77b35-109">Configure players</span></span>
- <span data-ttu-id="77b35-110">共有エクスペリエンスで複数のユーザーを接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="77b35-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="77b35-111">手順</span><span class="sxs-lookup"><span data-stu-id="77b35-111">Instructions</span></span>

1. <span data-ttu-id="77b35-112">次の図に示すように、[アセット-> Resources-> Prefabs] フォルダーの [プロジェクト] パネルで、NetworkLobby prefab を階層にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="77b35-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="77b35-114">NetworkLobby を展開すると、Networklobby という子オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="77b35-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="77b35-115">NetworkRoom を選択した状態で、[インスペクター] パネルにアクセスし、[コンポーネントの追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77b35-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="77b35-116">PhotonView を検索し、コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="77b35-116">Search for PhotonView and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="77b35-118">階層内に新しい空のゲームオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="77b35-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="77b35-119">階層内を右クリックし、コンテキストメニューから [空] を選択します。</span><span class="sxs-lookup"><span data-stu-id="77b35-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="77b35-120">位置が x = 0、y = 0、z = 0 に設定されていることを確認し、オブジェクトに PhotonUser という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="77b35-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="77b35-122">[コンポーネントの追加] をクリックし、「Generic Net Sync」と入力します。汎用 Net Sync クラスを選択します。</span><span class="sxs-lookup"><span data-stu-id="77b35-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="77b35-123">クラスが表示されたら、[ユーザー] チェックボックスをクリックしてオンにします。</span><span class="sxs-lookup"><span data-stu-id="77b35-123">When the class appears, click on the User check box to turn it on.</span></span> 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="77b35-125">[コンポーネントの追加] をもう一度クリックし、「Photon View」と入力します。</span><span class="sxs-lookup"><span data-stu-id="77b35-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="77b35-126">ドロップダウンリストに表示される Photon View クラスを選択します。</span><span class="sxs-lookup"><span data-stu-id="77b35-126">Select the Photon View class that appears in the drop-down list.</span></span>

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="77b35-128">汎用 Net Sync クラスのファイルアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77b35-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="77b35-129">Photon ビューの [観測されたコンポーネント] フィールドにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="77b35-129">Drag and drop it in the Photon View's Observed Components field.</span></span> 

![module3chapter3updateStep6im](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="77b35-131">次に、共有エクスペリエンスに参加する各ユーザーを表す球体を作成します。</span><span class="sxs-lookup"><span data-stu-id="77b35-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="77b35-132">先ほど作成した PhotonUser オブジェクトを右クリックし、[3D オブジェクト] までスクロールして [球] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77b35-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="77b35-133">これにより、PhotonUser オブジェクトの子として球ゲームオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="77b35-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="77b35-135">球を x = 0.06、y = 0.06、ad z = 0.06 にスケールダウンします。</span><span class="sxs-lookup"><span data-stu-id="77b35-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="77b35-137">PhotonUser game オブジェクトを [プロジェクト] パネルの Prefabs フォルダーにドラッグし、シーンから削除します。</span><span class="sxs-lookup"><span data-stu-id="77b35-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="77b35-138">これで、共有エクスペリエンスで新しいプレーヤーを生成またはインスタンス化するときに使用できる事前 fab が作成されました。</span><span class="sxs-lookup"><span data-stu-id="77b35-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="77b35-140">注: Prefabs フォルダーを階層から削除する前に、game オブジェクトが正常にコピーされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="77b35-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="77b35-141">手順 3. の指示に従って、階層内に新しいオブジェクトを作成し、SharedPlayground グラウンドという名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="77b35-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="77b35-142">次に、[コンポーネントの追加] をクリックし、[汎用ネットワークマネージャー] を検索して、それをクリックして汎用ネットワークマネージャーコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="77b35-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="77b35-143">オブジェクトの位置を x = 0、y = 0、z = 0 に変更します。</span><span class="sxs-lookup"><span data-stu-id="77b35-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="77b35-145">結論</span><span class="sxs-lookup"><span data-stu-id="77b35-145">Congratulations</span></span>

<span data-ttu-id="77b35-146">上記のすべての手順が完了し、ビルドプロセスも完了したら、[再生] ボタンをクリックして HoloLens 2 に接続します。</span><span class="sxs-lookup"><span data-stu-id="77b35-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="77b35-147">頭を移動すると球が動いていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="77b35-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="77b35-148">これは、Unity プロジェクトに参加するすべてのユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="77b35-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="77b35-149">[次のレッスン:共有 (Photon) レッスン4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="77b35-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

