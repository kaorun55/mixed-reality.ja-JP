---
title: MR Learning ASA モジュール HoloLens 2 での Azure 空間アンカー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 4dc36aec4d885fa75ea490446c2d682264049725
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326891"
---
# <a name="persistence-and-sharing-of-azure-spatial-anchors"></a><span data-ttu-id="7795d-104">永続化と Azure の空間アンカーの共有</span><span class="sxs-lookup"><span data-stu-id="7795d-104">Persistence and Sharing of Azure Spatial Anchors</span></span>

<span data-ttu-id="7795d-105">このレッスンでは、HoloLens 2 のディスクにアンカー情報を保存することによって、複数のアプリケーション セッション間で、Azure の空間アンカーを永続化する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="7795d-105">In this lesson, we will learn how to persist our Azure Spatial Anchors across multiple app sessions by saving our anchor information to the HoloLens 2's disk.</span></span> <span data-ttu-id="7795d-106">マルチ デバイスのアンカーの配置に関するその他のデバイスには、このアンカー情報を共有する方法も説明します。</span><span class="sxs-lookup"><span data-stu-id="7795d-106">We will also learn how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="7795d-107">目標</span><span class="sxs-lookup"><span data-stu-id="7795d-107">Objectives</span></span>

* <span data-ttu-id="7795d-108">保存し、アプリ セッションの間で永続化のため、HoloLens 2 のローカル ディスクから Azure 空間アンカー情報を取得する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="7795d-108">Learn how to save and retrieve Azure Spatial Anchor information from the HoloLens 2 local disk, for persistence between app sessions</span></span>

* <span data-ttu-id="7795d-109">マルチ デバイスのシナリオでユーザーの間での Azure 空間アンカー情報を共有する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="7795d-109">Learn how to share Azure Spatial Anchor information between users in a multi-device scenario</span></span>

  

## <a name="instructions"></a><span data-ttu-id="7795d-110">手順</span><span class="sxs-lookup"><span data-stu-id="7795d-110">Instructions</span></span>

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="7795d-111">ディスクにアンカー ID 保存 - アプリのセッション間での Azure のアンカーを永続化します。</span><span class="sxs-lookup"><span data-stu-id="7795d-111">Persist Azure Anchors Between App Sessions - Save Anchor ID to Disk</span></span>

1. <span data-ttu-id="7795d-112">検索し、"SaveAnchorToDisk"プレハブをシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="7795d-112">Search for and add the "SaveAnchorToDisk" prefab to your scene.</span></span> <span data-ttu-id="7795d-113">これらには、2 つのボタン、HoloLens 2 ディスクとディスクから任意の Id を取得するために、使用可能な Azure アンカー Id を保存するための 1 つのボタンが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7795d-113">These include two buttons, one button for saving any available Azure Anchor IDs to the HoloLens 2 disk, and another for retrieving any IDs from the disk.</span></span>

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. <span data-ttu-id="7795d-115">以下の手順に従って各ボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="7795d-115">Configure Each button according to the instructions below</span></span>
   - <span data-ttu-id="7795d-116">"SaveToDisk"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7795d-116">For the Button named "SaveToDisk", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="7795d-117">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから SaveAzureAnchorIDToDisk() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7795d-117">Drag the ParentAnchor object into the empty field, and assign the SaveAzureAnchorIDToDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>
   
     > <span data-ttu-id="7795d-118">注: 他のボタン、シーン内の重複をボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="7795d-118">Note: some of the buttons may appear overlapping the other buttons in the scene.</span></span> <span data-ttu-id="7795d-119">自由に、ボタンの位置を調整します。</span><span class="sxs-lookup"><span data-stu-id="7795d-119">Feel free to adjust the button's positioning.</span></span>
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - <span data-ttu-id="7795d-123">"GetFromDisk"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7795d-123">For the Button named "GetFromDisk", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="7795d-124">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから LoadAzureAnchorIDsFromDisk() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7795d-124">Drag the ParentAnchor object into the empty field, and assign the LoadAzureAnchorIDsFromDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="7795d-125">デバイスに更新されたアプリケーションを作成するレッスン 1 の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="7795d-125">Follow the instructions from Lesson 1 to build the updated application to your device.</span></span> <span data-ttu-id="7795d-126">Azure アンカー"作成"ボタンをクリックして、前のレッスンで行ったよう保存すると Azure アンカー ID をディスクにキーを押してボタンをディスクに保存します。</span><span class="sxs-lookup"><span data-stu-id="7795d-126">After pressing the "Create Azure Anchor" button, as you did in the previous lesson, you may now save the Azure Anchor ID to disk by pressing the save to disk button.</span></span>

4. <span data-ttu-id="7795d-127">アプリケーションを再起動して、Azure セッションを開始、"負荷アンカー ID"をクリックし、およびディスクに保存した ID に関連付けられているアンカーを検索する「Azure アンカーの検索」ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="7795d-127">Restart the application, start the Azure Session, Press the "Load Anchor ID" button, and then press the "Locate Azure Anchor" button to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="7795d-128">シーン全体を今すぐスナップ位置に、位置の前に保存したアンカーです。</span><span class="sxs-lookup"><span data-stu-id="7795d-128">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

### <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="7795d-129">Azure のアンカーを複数のデバイス間で共有します。</span><span class="sxs-lookup"><span data-stu-id="7795d-129">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="7795d-130">このセクションで説明、複数のデバイス間で Azure アンカー ID を共有する方法をします。</span><span class="sxs-lookup"><span data-stu-id="7795d-130">In this section, we'll learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="7795d-131">これにより、複数のデバイスの同じアンカー ID を Azure のクエリを実行する、固定ホログラムとシーン空間的に配置することができます。</span><span class="sxs-lookup"><span data-stu-id="7795d-131">This will allow multiple devices to query Azure for the same anchor ID, allowing our anchored holograms and scenes to be spatially aligned.</span></span> <span data-ttu-id="7795d-132">(複数のデバイス間で同じ物理的な場所で同じホログラムが表示される) 空間の配置では、HoloLens 2 でのキーをローカルの共有エクスペリエンスです。</span><span class="sxs-lookup"><span data-stu-id="7795d-132">Spatial alignment (seeing the same holograms in the same physical location between multiple devices) is key to local shared experiences in the HoloLens 2.</span></span> <span data-ttu-id="7795d-133">チュートリアルの Azure 空間アンカーの共有エクスペリエンスで説明したメソッドを含む、すべてのデバイス間の関連の azure Id 情報を転送する方法はたくさんあります (TODO: リンクを追加します)。この例では、単純な web サービスを使用して、アップロードし、デバイス間でアンカー Id をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="7795d-133">There are many ways to transfer information regarding azure IDs between devices, including methods outlined in the Azure Spatial Anchors shared experiences tutorials (TODO: add link.) This example uses a simple web service to upload and download Anchor IDs between devices.</span></span>

1. <span data-ttu-id="7795d-134">階層に"ShareAnchor"プレハブを追加します。</span><span class="sxs-lookup"><span data-stu-id="7795d-134">Add the "ShareAnchor" prefab into your hierarchy.</span></span> <span data-ttu-id="7795d-135">このプレハブ; シーンに 2 つの新しいボタンを追加しますアンカー ID 情報とダウンロード用に別のアップロードの 1 つは、ID 情報を固定します。</span><span class="sxs-lookup"><span data-stu-id="7795d-135">This prefab adds two new buttons to your scene; one for uploading anchor ID information and another for downloading anchor ID information.</span></span> 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. <span data-ttu-id="7795d-137">以下の手順に従って各ボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="7795d-137">Configure Each button according to the instructions below</span></span>

   - <span data-ttu-id="7795d-138">"SendSharedAnchor"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7795d-138">For the Button named "SendSharedAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="7795d-139">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから ShareAnchor() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7795d-139">Drag the ParentAnchor object into the empty field, and assign the ShareAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - <span data-ttu-id="7795d-142">"GetSharedAnchor"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7795d-142">For the Button named "GetSharedAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="7795d-143">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから GetSharedAzureAnchor() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7795d-143">Drag the ParentAnchor object into the empty field, and assign the GetSharedAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="7795d-144">指示に従って[レッスン 1](mrlearning-base-ch1.md)します。</span><span class="sxs-lookup"><span data-stu-id="7795d-144">Follow the instructions from [Lesson 1](mrlearning-base-ch1.md).</span></span> <span data-ttu-id="7795d-145">デバイスに更新されたアプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="7795d-145">to build the updated application to your device.</span></span> <span data-ttu-id="7795d-146">Azure アンカー"作成"ボタンを押した後に、前のレッスンで行ったよう、その他のデバイスを共有するボタンを押して、他のデバイスに Azure アンカー ID を共有可能性がありますようになりました。</span><span class="sxs-lookup"><span data-stu-id="7795d-146">After pressing the "Create Azure Anchor" button, as you did in the previous lesson, you may now share the Azure Anchor ID to other devices by pressing the Share To Other Device button.</span></span>

   > <span data-ttu-id="7795d-147">注:親アンカーを選択して、親のアンカー スクリプトまで下へスクロールします。</span><span class="sxs-lookup"><span data-stu-id="7795d-147">Note: Select the parent anchor and scroll down to the parent anchor script.</span></span> <span data-ttu-id="7795d-148">共有した場合、これが共有しているお客様がわかるように、"パブリック共有 pin"が一意であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7795d-148">Ensure that your "public sharing pin" is unique, so that when you share it, you know it is yours that you are sharing.</span></span> <span data-ttu-id="7795d-149">これにより、正しい Azure アンカーを共有していることを確認するために、Azure のアンカーを共有しているユーザーの何千もの可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7795d-149">There could be thousands of users sharing their Azure Anchors, so doing this will allow you to ensure you are sharing the correct Azure Anchors.</span></span>

4. <span data-ttu-id="7795d-150">別の HoloLens 2 デバイスがあれば、アプリケーションを起動し、Azure セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="7795d-150">If you have another HoloLens 2 device, start the application and then start the Azure Session.</span></span> <span data-ttu-id="7795d-151">"共有アンカー ID の取得"ボタンを押すし、ディスクに保存した ID に関連付けられているアンカーを検索する"Azure アンカーの検索 ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="7795d-151">Press the "Get Shared Anchor ID" button, and then press the "Locate Azure Anchor" button to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="7795d-152">シーン全体を位置にスナップする必要があるようになりました where でその他の HoloLens 2 デバイスに配置された場合。</span><span class="sxs-lookup"><span data-stu-id="7795d-152">The entire scene should now snap into position, at the where it was placed on the other HoloLens 2 device!</span></span> <span data-ttu-id="7795d-153">HoloLens 2 を 1 つだけの場合する可能性がありますもテスト機能、アプリケーションを再起動することによって Azure セッションを開始して"共有アンカー ID の取得"ボタンを押し、Azure アンカー"検索"ボタンに関連付けられているアンカーを検索するキーを押しますID ディスクに保存しました。</span><span class="sxs-lookup"><span data-stu-id="7795d-153">If you only have one HoloLens 2, you may still test functionality by restarting the application, starting the Azure Session, and then Press the "Get Shared Anchor ID" button button, and then press the "Locate Azure Anchor" button to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="7795d-154">シーン全体を今すぐスナップ位置に、位置の前に保存したアンカーです。</span><span class="sxs-lookup"><span data-stu-id="7795d-154">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

## <a name="congratulations"></a><span data-ttu-id="7795d-155">結論</span><span class="sxs-lookup"><span data-stu-id="7795d-155">Congratulations</span></span>
<span data-ttu-id="7795d-156">このレッスンでは、アプリ セッションとアプリの再起動の間、HoloLens 2 のローカル ディスクに Azure 空間アンカー ID を保存することによって Azure 空間アンカーを永続化する方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="7795d-156">In this Lesson you learned how to persist Azure Spatial Anchors between app sessions and app restarts by saving the Azure Spatial Anchor ID to the local disk of the HoloLens 2.</span></span> <span data-ttu-id="7795d-157">複数のデバイス、共有、基本のマルチ ユーザーの静的なホログラム エクスペリエンスの間で Azure 空間アンカーを共有する方法も学習しました。</span><span class="sxs-lookup"><span data-stu-id="7795d-157">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience!</span></span>

<span data-ttu-id="7795d-158">共有モジュールの最後のレッスンの中に完全にインタラクティブなローカル共有エクスペリエンスの一部として Azure 空間アンカーを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7795d-158">We will learn how to implement Azure Spatial Anchors as part of a fully interactive local shared experience during the final lesson of the Sharing Module.</span></span> <span data-ttu-id="7795d-159">ローカル共有のエクスペリエンスは、各ユーザーの同期済みの 3D オブジェクトの位置、回転、およびスケール、識別子などの機能を含めることができ、アプリケーションの状態を共有します。</span><span class="sxs-lookup"><span data-stu-id="7795d-159">A local sharing experience may include functionality such as synchronized 3D object position, rotation, and scale, identifiers for each user, and shared application states.</span></span> <span data-ttu-id="7795d-160">Azure 空間アンカーは、物理的に同じ場所に仮想オブジェクトを表示するすべてのユーザーが共通のアンカーを持つ各参加者を提供することでこれらの共有のシナリオを強化します。</span><span class="sxs-lookup"><span data-stu-id="7795d-160">Azure Spatial Anchors enhances these shared scenarios by providing each participant with a common anchor which allows all users to see virtual objects in the same physical location.</span></span> <span data-ttu-id="7795d-161">これは、HoloLens、Android、および iOS デバイスを含め、デバイス プラットフォームの範囲にわたる場合は true。</span><span class="sxs-lookup"><span data-stu-id="7795d-161">This is true across a range of device platforms, including HoloLens, Android, and iOS devices.</span></span> <span data-ttu-id="7795d-162">共有のエクスペリエンスを開発する方法については、共有モジュール内のすべてのレッスンを完了してください。</span><span class="sxs-lookup"><span data-stu-id="7795d-162">To learn how to develop a shared experience, please complete all lessons in the Sharing module.</span></span>

<span data-ttu-id="7795d-163">次のレッスンでは、リアルタイムのフィードバックをユーザーに提供する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="7795d-163">In the next Lesson, we will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="7795d-164">このフィードバックは、アンカーの作成、環境の理解の品質および Azure のセッションの状態に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7795d-164">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="7795d-165">フィードバック、ユーザーご存じないアンカーを Azure にアップロードが正常かどうか、環境の品質がアンカーの作成、または現在の状態のための十分なかどうか。</span><span class="sxs-lookup"><span data-stu-id="7795d-165">Without feedback, users may not know whether an anchor has successfully been upload to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="7795d-166">次のレッスン:ASA Lesson 3</span><span class="sxs-lookup"><span data-stu-id="7795d-166">Next Lesson: ASA Lesson 3</span></span>](mrlearning-asa-ch3.md)

