---
title: ケース スタディ - 3 HoloStudio UI と相互作用教訓を設計します。
description: HoloStudio UI との対話デザインの学習内容
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: 複合現実、HoloLens、HoloStudio、Windows
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974826"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="4d817-104">ケース スタディ - 3 HoloStudio UI と相互作用教訓を設計します。</span><span class="sxs-lookup"><span data-stu-id="4d817-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="4d817-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) HoloLens の最初の Microsoft アプリのいずれかでした。</span><span class="sxs-lookup"><span data-stu-id="4d817-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="4d817-106">このためは、3 d UI の新しいベスト プラクティスと対話デザインを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d817-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="4d817-107">多くのユーザーのテスト、プロトタイプ作成、および試行錯誤のようにしました。</span><span class="sxs-lookup"><span data-stu-id="4d817-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="4d817-108">この種類の調査を行うには自由に使用できるリソースのあるすべてのユーザー、HoloLens のアプリの UI との対話の設計に関する HoloStudio の開発中に学んだこと、シニア Holographic デザイナー、Marcus Ghaly、次の 3 つの共有がありましたのでことがわかっています。</span><span class="sxs-lookup"><span data-stu-id="4d817-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="4d817-109">ビデオを見る</span><span class="sxs-lookup"><span data-stu-id="4d817-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="4d817-110">問題 #1:ユーザーが作成、移動たくありませんでした。</span><span class="sxs-lookup"><span data-stu-id="4d817-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="4d817-111">もともと設計しました HoloStudio で workbench 四角形としてはるか現実の世界で見られるようにします。</span><span class="sxs-lookup"><span data-stu-id="4d817-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="4d817-112">問題は、ユーザーが机に向っているまたは、workbench の周囲に移動していないため、コンピューターの前に作業およびすべての辺から 3D の作成を調査している時にまだを維持するかを示すエクスペリエンスの有効期間があることです。</span><span class="sxs-lookup"><span data-stu-id="4d817-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![HoloStudio で workbench の四角形のデザインはないユーザーが移動し、すべての辺から、作成を確認します。](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="4d817-114">Workbench またはスタンバイを予定していた場所をオフに切り上げるには、「前面」ができるようにする情報を得ることがありました。</span><span class="sxs-lookup"><span data-stu-id="4d817-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="4d817-115">これをテストしましたが突然人起動内を移動し、自分で自分の作成を探索します。</span><span class="sxs-lookup"><span data-stu-id="4d817-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![循環 workbench デザインでは、ユーザーの作成までわざわざ行かずを推奨します。](images/circular-workbench-500px.jpg)

<span data-ttu-id="4d817-117">**学習内容**</span><span class="sxs-lookup"><span data-stu-id="4d817-117">**What we learned**</span></span>

<span data-ttu-id="4d817-118">ユーザーの新機能について考えるを常になります。</span><span class="sxs-lookup"><span data-stu-id="4d817-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="4d817-119">HoloLens とその他のデバイスで実行できないことの優れた機能は、その物理容量を活用します。</span><span class="sxs-lookup"><span data-stu-id="4d817-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="4d817-120">問題 2:モーダル ダイアログ ボックスが holographic フレーム外にあります。</span><span class="sxs-lookup"><span data-stu-id="4d817-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="4d817-121">場合によっては、ユーザーがアプリで、注意が必要なものから別の方向で表示されます。</span><span class="sxs-lookup"><span data-stu-id="4d817-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="4d817-122">PC では、ダイアログをポップアップだけができます。 が 3D 環境で他のユーザーの面でこれを実行する場合、ダイアログ ボックスがその方法で取得するように感じ、ことができます。</span><span class="sxs-lookup"><span data-stu-id="4d817-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="4d817-123">メッセージを読みする必要があるが、直感がこれから取得しようとするが。</span><span class="sxs-lookup"><span data-stu-id="4d817-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="4d817-124">この対応は、ゲームをプレイしているが、作業用に設計されたツールは遅くなります。</span><span class="sxs-lookup"><span data-stu-id="4d817-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="4d817-125">いくつかの異なる点を試用するには、後に最後に「バブルを考える」システムを使用して、ダイアログ ボックスの上に設置されたし、tendrils アプリケーションでは、注意が必要な場所を後に使用できるユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="4d817-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="4d817-126">暗黙の方向性を把握できるように、ユーザーが移動するかを知っている tendrils パルスを行いました。</span><span class="sxs-lookup"><span data-stu-id="4d817-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

![「と考えるバブル」システムには、アプリで、注意が必要な場所にユーザーを先頭方向性を提供するパルスを発する tendrils が含まれています。](images/thought-bubble-500px.jpg)

<span data-ttu-id="4d817-128">**学習内容**</span><span class="sxs-lookup"><span data-stu-id="4d817-128">**What we learned**</span></span>

<span data-ttu-id="4d817-129">注意を払う必要があることをユーザーに警告を 3D ではるかに困難になります。</span><span class="sxs-lookup"><span data-stu-id="4d817-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="4d817-130">などのアテンション ディレクターを使用して[空間サウンド](spatial-sound.md)光線、ライトや、思考をバブルする可能性がユーザーに必要な場所。</span><span class="sxs-lookup"><span data-stu-id="4d817-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="4d817-131">問題 3:その他のホログラムで UI をブロックすることがあります。</span><span class="sxs-lookup"><span data-stu-id="4d817-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="4d817-132">ユーザーがホログラムとその関連の UI コントロールを操作する場合も、別ホログラムがそれらの前にあるため、ビューからブロックされますがあります。</span><span class="sxs-lookup"><span data-stu-id="4d817-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="4d817-133">HoloStudio、開発中に試行錯誤を使用して、このソリューションに付属しました。</span><span class="sxs-lookup"><span data-stu-id="4d817-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![HoloLens ソックスを着けずにユーザーとの間のもう 1 つのホログラムがある場合は、ホログラムに関連付けられた UI コントロールをブロックになることができます。](images/ui-blocked-500px.jpg)

<span data-ttu-id="4d817-135">私たちは、ブロックされるが見つかったでした。 離れたいたホログラム同時にしている間に近くするがコントロールを検索するユーザーの満足を取得できませんでしたをユーザーに近い UI コントロールを移動しようとしました。</span><span class="sxs-lookup"><span data-stu-id="4d817-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="4d817-136">ただし、最も近いホログラムの前にコントロールを移動、ユーザーに場合、その影響を与えている必要がありますホログラムからデタッチされたように感じました。</span><span class="sxs-lookup"><span data-stu-id="4d817-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="4d817-137">私たちは最後に、最終的に、UI コントロールをゴーストし、配置同じ距離にあるユーザーからは、関連付けられたホログラムとしてどちらも、接続されているため。</span><span class="sxs-lookup"><span data-stu-id="4d817-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="4d817-138">これにより、ユーザーが隠される場合でも、コントロールと対話します。</span><span class="sxs-lookup"><span data-stu-id="4d817-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![ソリューション: コントロールとの対話を許可されているし、に影響を与えることがホログラムに接続されていると感じることの両方を UI コントロールは非実体化しました。](images/ghosting-ui-500px.jpg)

<span data-ttu-id="4d817-140">**学習内容**</span><span class="sxs-lookup"><span data-stu-id="4d817-140">**What we learned**</span></span>

<span data-ttu-id="4d817-141">ユーザーは、簡単に UI コントロールのアクセスがブロックされている場合でも、ユーザーがどこでも、ホログラム現実の世界でタスクを完了できるようにするメソッドを調べるためにできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d817-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="4d817-142">執筆者紹介</span><span class="sxs-lookup"><span data-stu-id="4d817-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="4d817-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="4d817-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="4d817-144">シニア Holographic デザイナー @Microsoft</span><span class="sxs-lookup"><span data-stu-id="4d817-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="4d817-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d817-145">See also</span></span>
* [<span data-ttu-id="4d817-146">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="4d817-146">Instinctual interactions</span></span>](interaction-fundamentals.md)

 
