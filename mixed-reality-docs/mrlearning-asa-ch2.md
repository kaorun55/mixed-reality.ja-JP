---
title: MR Learning ASA モジュール HoloLens 2 での Azure 空間アンカー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: f8a52660fe05b6ed4508321ed246b8e299b75bca
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523335"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="de575-104">2. 保存、取得、および Azure 空間アンカーの共有</span><span class="sxs-lookup"><span data-stu-id="de575-104">2. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="de575-105">このチュートリアルでは、HoloLens 2 のディスクにアンカー情報を保存することによって、複数のアプリケーション セッション間で、Azure の空間アンカーを保存する方法学習します。</span><span class="sxs-lookup"><span data-stu-id="de575-105">In this tutorial, we will learn how to save our Azure Spatial Anchors across multiple app sessions by saving our anchor information to the HoloLens 2's disk.</span></span> <span data-ttu-id="de575-106">マルチ デバイスのアンカーの配置に関するその他のデバイスには、このアンカー情報を共有する方法も説明します。</span><span class="sxs-lookup"><span data-stu-id="de575-106">We will also learn how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="de575-107">目標</span><span class="sxs-lookup"><span data-stu-id="de575-107">Objectives</span></span>

* <span data-ttu-id="de575-108">保存し、アプリ セッションの間で永続化のため、HoloLens 2 のローカル ディスクから Azure 空間アンカー情報を取得する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="de575-108">Learn how to save and retrieve Azure Spatial Anchor information from the HoloLens 2 local disk, for persistence between app sessions</span></span>

* <span data-ttu-id="de575-109">マルチ デバイスのシナリオでユーザーの間での Azure 空間アンカー情報を共有する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="de575-109">Learn how to share Azure Spatial Anchor information between users in a multi-device scenario</span></span>

  

## <a name="instructions"></a><span data-ttu-id="de575-110">手順</span><span class="sxs-lookup"><span data-stu-id="de575-110">Instructions</span></span>

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="de575-111">ディスクにアンカー ID 保存 - アプリのセッション間での Azure のアンカーを永続化します。</span><span class="sxs-lookup"><span data-stu-id="de575-111">Persist Azure Anchors Between App Sessions - Save Anchor ID to Disk</span></span>

1. <span data-ttu-id="de575-112">検索し、SaveAnchorToDisk プレハブをシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="de575-112">Search for and add the SaveAnchorToDisk prefab to your scene.</span></span> <span data-ttu-id="de575-113">これらには、2 つのボタン、HoloLens 2 ディスクとディスクから任意の Id を取得するために、使用可能な Azure アンカー Id を保存するための 1 つのボタンが含まれます。</span><span class="sxs-lookup"><span data-stu-id="de575-113">These include two buttons, one button for saving any available Azure Anchor IDs to the HoloLens 2 disk, and another for retrieving any IDs from the disk.</span></span>

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. <span data-ttu-id="de575-115">以下の手順に従って各ボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="de575-115">Configure Each button according to the instructions below</span></span>
   - <span data-ttu-id="de575-116">SaveToDisk をという名前のボタン、をクリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="de575-116">For the Button named SaveToDisk, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="de575-117">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから SaveAzureAnchorIDToDisk() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="de575-117">Drag the ParentAnchor object into the empty field, and assign the SaveAzureAnchorIDToDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>
   
     > <span data-ttu-id="de575-118">注: 他のボタン、シーン内の重複をボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="de575-118">Note: some of the buttons may appear overlapping the other buttons in the scene.</span></span> <span data-ttu-id="de575-119">自由に、ボタンの位置を調整します。</span><span class="sxs-lookup"><span data-stu-id="de575-119">Feel free to adjust the button's positioning.</span></span>
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - <span data-ttu-id="de575-123">GetFromDisk をという名前のボタン、をクリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="de575-123">For the Button named GetFromDisk, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="de575-124">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから LoadAzureAnchorIDsFromDisk() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="de575-124">Drag the ParentAnchor object into the empty field, and assign the LoadAzureAnchorIDsFromDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="de575-125">デバイスに更新されたアプリケーションをビルドする Tutoiral 1 の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="de575-125">Follow the instructions from Tutoiral 1 to build the updated application to your device.</span></span> <span data-ttu-id="de575-126">Azure アンカーの作成 ボタンを押した後、前のレッスンで行ったよう保存しますする Azure アンカー ID をディスクにキーを押してボタンをディスクに保存。</span><span class="sxs-lookup"><span data-stu-id="de575-126">After pressing the Create Azure Anchor button, as you did in the previous lesson, you may now save the Azure Anchor ID to disk by pressing the save to disk button.</span></span>

4. <span data-ttu-id="de575-127">アプリケーションを再起動して、キーを押してロード アンカー ID を Azure セッションを開始および Azure アンカーをディスクに保存した ID に関連付けられているアンカーを検索する検索キーを押します。</span><span class="sxs-lookup"><span data-stu-id="de575-127">Restart the application, start the Azure Session, Press Load Anchor ID, and then press Locate Azure Anchor to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="de575-128">シーン全体を今すぐスナップ位置に、位置の前に保存したアンカーです。</span><span class="sxs-lookup"><span data-stu-id="de575-128">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

### <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="de575-129">Azure のアンカーを複数のデバイス間で共有します。</span><span class="sxs-lookup"><span data-stu-id="de575-129">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="de575-130">このセクションで説明、複数のデバイス間で Azure アンカー ID を共有する方法をします。</span><span class="sxs-lookup"><span data-stu-id="de575-130">In this section, we'll learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="de575-131">これにより、複数のデバイスの同じアンカー ID を Azure のクエリを実行する、固定ホログラムとシーン空間的に配置することができます。</span><span class="sxs-lookup"><span data-stu-id="de575-131">This will allow multiple devices to query Azure for the same anchor ID, allowing our anchored holograms and scenes to be spatially aligned.</span></span> <span data-ttu-id="de575-132">(複数のデバイス間で同じ物理的な場所で同じホログラムが表示される) 空間の配置では、HoloLens 2 でのキーをローカルの共有エクスペリエンスです。</span><span class="sxs-lookup"><span data-stu-id="de575-132">Spatial alignment (seeing the same holograms in the same physical location between multiple devices) is key to local shared experiences in the HoloLens 2.</span></span> <span data-ttu-id="de575-133">チュートリアルの Azure 空間アンカーの共有エクスペリエンスで説明したメソッドを含む、すべてのデバイス間の関連の azure Id 情報を転送する方法はたくさんあります (TODO: リンクを追加します)。この例では、単純な web サービスを使用して、アップロードし、デバイス間でアンカー Id をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="de575-133">There are many ways to transfer information regarding azure IDs between devices, including methods outlined in the Azure Spatial Anchors shared experiences tutorials (TODO: add link.) This example uses a simple web service to upload and download Anchor IDs between devices.</span></span>

1. <span data-ttu-id="de575-134">階層に ShareAnchor プレハブを追加します。</span><span class="sxs-lookup"><span data-stu-id="de575-134">Add the ShareAnchor prefab into your hierarchy.</span></span> <span data-ttu-id="de575-135">このプレハブ; シーンに 2 つの新しいボタンを追加しますアンカー ID 情報とダウンロード用に別のアップロードの 1 つは、ID 情報を固定します。</span><span class="sxs-lookup"><span data-stu-id="de575-135">This prefab adds two new buttons to your scene; one for uploading anchor ID information and another for downloading anchor ID information.</span></span> 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. <span data-ttu-id="de575-137">以下の手順に従って各ボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="de575-137">Configure Each button according to the instructions below</span></span>

   - <span data-ttu-id="de575-138">名前付き、SendSharedAnchor、ボタンのクリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="de575-138">For the Button named, SendSharedAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="de575-139">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから ShareAnchor() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="de575-139">Drag the ParentAnchor object into the empty field, and assign the ShareAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - <span data-ttu-id="de575-142">名前付き、GetSharedAnchor、ボタンのクリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="de575-142">For the Button named, GetSharedAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="de575-143">空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから GetSharedAzureAnchor() メソッドを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="de575-143">Drag the ParentAnchor object into the empty field, and assign the GetSharedAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="de575-144">指示に従って[チュートリアル 1](mrlearning-base-ch1.md)します。</span><span class="sxs-lookup"><span data-stu-id="de575-144">Follow the instructions from [Tutorial 1](mrlearning-base-ch1.md).</span></span> <span data-ttu-id="de575-145">デバイスに更新されたアプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="de575-145">to build the updated application to your device.</span></span> <span data-ttu-id="de575-146">Azure アンカーの作成 ボタンを押した後に、前のレッスンで行ったよう、その他のデバイスを共有するボタンを押して、他のデバイスに Azure アンカー ID を共有可能性がありますようになりました。</span><span class="sxs-lookup"><span data-stu-id="de575-146">After pressing the Create Azure Anchor button, as you did in the previous lesson, you may now share the Azure Anchor ID to other devices by pressing the Share To Other Device button.</span></span>

   > <span data-ttu-id="de575-147">注:親アンカーを選択して、親のアンカー スクリプトまで下へスクロールします。</span><span class="sxs-lookup"><span data-stu-id="de575-147">Note: Select the parent anchor and scroll down to the parent anchor script.</span></span> <span data-ttu-id="de575-148">共有した場合、これが共有しているお客様がわかるように、パブリック共有暗証番号 (pin) が一意であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="de575-148">Ensure that your public sharing pin is unique, so that when you share it, you know it is yours that you are sharing.</span></span> <span data-ttu-id="de575-149">これにより、正しい Azure アンカーを共有していることを確認するために、Azure のアンカーを共有しているユーザーの何千もの可能性があります。</span><span class="sxs-lookup"><span data-stu-id="de575-149">There could be thousands of users sharing their Azure anchors, so doing this will allow you to ensure you are sharing the correct Azure anchors.</span></span>

4. <span data-ttu-id="de575-150">別の HoloLens 2 デバイスがあれば、アプリケーションを起動し、Azure セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="de575-150">If you have another HoloLens 2 device, start the application and then start the Azure Session.</span></span> <span data-ttu-id="de575-151">共有アンカー ID の取得 をクリックして、ディスクに保存した ID に関連付けられているアンカーを検索する Azure アンカーの検索 ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="de575-151">Press the Get Shared Anchor ID button, and then press the Locate Azure Anchor button to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="de575-152">シーン全体を位置にスナップする必要があるようになりました where でその他の HoloLens 2 デバイスに配置された場合。</span><span class="sxs-lookup"><span data-stu-id="de575-152">The entire scene should now snap into position, at the where it was placed on the other HoloLens 2 device!</span></span> <span data-ttu-id="de575-153">1 つの HoloLens 2 のみがある、およびキーを押して、アンカーを検索する Azure アンカーの検索 ボタンに関連付けられてもテスト機能、アプリケーションを再起動することによって Azure セッションを開始して、"共有アンカー ID の取得"ボタンを押す場合、ID は、ディスクに保存しました。</span><span class="sxs-lookup"><span data-stu-id="de575-153">If you only have one HoloLens 2, you may still test functionality by restarting the application, starting the Azure Session, and then Press the "Get Shared Anchor ID" button button, and then press the Locate Azure Anchor button to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="de575-154">シーン全体を今すぐスナップ位置に、位置の前に保存したアンカーです。</span><span class="sxs-lookup"><span data-stu-id="de575-154">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

## <a name="congratulations"></a><span data-ttu-id="de575-155">結論</span><span class="sxs-lookup"><span data-stu-id="de575-155">Congratulations</span></span>
<span data-ttu-id="de575-156">このレッスンでは、HoloLens 2 で Azure 空間アンカー ID をローカル ディスクに保存することによって、アプリケーションのセッションとアプリケーションの再起動の間 Azure 空間アンカーを永続化する方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="de575-156">In this Lesson you learned how to persist Azure Spatial Anchors between application sessions and application restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens 2.</span></span> <span data-ttu-id="de575-157">また、共有、基本のマルチ ユーザーの静的なホログラム エクスペリエンスの複数のデバイス間で Azure 空間アンカーを共有する方法も学習しました。</span><span class="sxs-lookup"><span data-stu-id="de575-157">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="de575-158">共有モジュールの最後のレッスンの中に完全にインタラクティブなローカル共有エクスペリエンスの一部として Azure 空間アンカーを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de575-158">We learn how to implement Azure Spatial Anchors as part of a fully interactive local shared experience during the final lesson of the Sharing Module.</span></span> <span data-ttu-id="de575-159">ローカル共有のエクスペリエンスは、各ユーザーの同期済みの 3D オブジェクトの位置、回転、およびスケール、識別子などの機能を含めることができ、アプリケーションの状態を共有します。</span><span class="sxs-lookup"><span data-stu-id="de575-159">A local sharing experience may include functionality such as synchronized 3D object position, rotation, and scale, identifiers for each user, and shared application states.</span></span> <span data-ttu-id="de575-160">Azure 空間アンカーは、すべてのユーザーが物理的に同じ場所に仮想オブジェクトを参照してください。 できる一般的なアンカーを持つ各参加者を提供することでこれらの共有のシナリオを強化します。</span><span class="sxs-lookup"><span data-stu-id="de575-160">Azure Spatial Anchors enhances these shared scenarios by providing each participant with a common anchor that lets all users see virtual objects in the same physical location.</span></span> <span data-ttu-id="de575-161">これは、HoloLens、Android、および iOS デバイスを含め、デバイス プラットフォームの範囲にわたる場合は true。</span><span class="sxs-lookup"><span data-stu-id="de575-161">This is true across a range of device platforms, including HoloLens, Android, and iOS devices.</span></span> <span data-ttu-id="de575-162">共有のエクスペリエンスを開発する方法については、共有モジュール内のすべてのレッスンを完了します。</span><span class="sxs-lookup"><span data-stu-id="de575-162">To learn how to develop a shared experience, complete all lessons in the Sharing module.</span></span>

<span data-ttu-id="de575-163">次のレッスンでは、リアルタイムのフィードバックをユーザーに提供する方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="de575-163">In the next Lesson, we will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="de575-164">このフィードバックは、アンカーの作成、環境の理解の品質および Azure のセッションの状態に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="de575-164">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="de575-165">フィードバック、ユーザーご存じないアンカーを Azure にアップロードが正常かどうか、環境の品質がアンカーの作成、または現在の状態のための十分なかどうか。</span><span class="sxs-lookup"><span data-stu-id="de575-165">Without feedback, users may not know whether an anchor has successfully been upload to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="de575-166">次のレッスン:ASA のチュートリアル 3</span><span class="sxs-lookup"><span data-stu-id="de575-166">Next Lesson: ASA Tutorial 3</span></span>](mrlearning-asa-ch3.md)

