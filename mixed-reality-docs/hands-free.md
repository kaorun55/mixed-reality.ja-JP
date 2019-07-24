---
title: ハンズフリー
description: アプリをハンズフリーに最適化する
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality、ハンズフリー、宝石、宝石をターゲット、相互作用、設計
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414389"
---
# <a name="hands-free"></a><span data-ttu-id="78e26-104">ハンズフリー</span><span class="sxs-lookup"><span data-stu-id="78e26-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="78e26-105">シナリオ</span><span class="sxs-lookup"><span data-stu-id="78e26-105">Scenarios</span></span>

<span data-ttu-id="78e26-106">[「相互作用モデルの概要](interaction-fundamentals.md)」で説明されているように、ユーザーとその目的を特定したら、作業を遂行するために機能する際に直面する可能性がある環境や状況の課題を自分で確認します。</span><span class="sxs-lookup"><span data-stu-id="78e26-106">As outlined in the [Interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="78e26-107">たとえば、多くのユーザーは、実際の目標を達成するためにユーザーを使用する必要があり、ハンズオンベースのインターフェイスとの対話が困難になります。</span><span class="sxs-lookup"><span data-stu-id="78e26-107">For example, many users need to use their hands to accomplish their real-world goals, and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="78e26-108">次のようなシナリオが考えられます。</span><span class="sxs-lookup"><span data-stu-id="78e26-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="78e26-109">タスクのガイドを示していますが、ハンドがビジー状態です</span><span class="sxs-lookup"><span data-stu-id="78e26-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="78e26-110">自分の手が混み合っている間の資料の参照</span><span class="sxs-lookup"><span data-stu-id="78e26-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="78e26-111">ハンド疲労</span><span class="sxs-lookup"><span data-stu-id="78e26-111">Hand fatigue</span></span>
* <span data-ttu-id="78e26-112">追跡できない手袋</span><span class="sxs-lookup"><span data-stu-id="78e26-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="78e26-113">何かを行う</span><span class="sxs-lookup"><span data-stu-id="78e26-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="78e26-114">ハンズフリーの感覚様相</span><span class="sxs-lookup"><span data-stu-id="78e26-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="78e26-115">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="78e26-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="78e26-116">音声を使用してコマンドを実行し、インターフェイスを制御するには、ユーザーが handsfree を操作できるだけでなく、複数の手順をスキップすることもできません。</span><span class="sxs-lookup"><span data-stu-id="78e26-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="78e26-117">このモダリティの使用方法は、ユーザーが任意のボタンの名前を読み取り専用にしてアクティブ化できるようにすること、つまり、会話のように、タスクを実行できるエージェントとの対話を可能にすることです。</span><span class="sxs-lookup"><span data-stu-id="78e26-117">The usage of this modality can range from allowing the user to simply read any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="78e26-118">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="78e26-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="78e26-119">実際には、音声を使用するのは理想的ではなく、可能な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="78e26-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="78e26-120">出荷時の環境、プライバシー、またはソーシャル規範はすべて制約となります。</span><span class="sxs-lookup"><span data-stu-id="78e26-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="78e26-121">Head の熟考モデルを使用すると、ユーザーはヘッドベクターをポイントすることによってアプリ内を移動できます。一方、ボタンの残留または dwelling では、一定の時間 (通常は1秒程度) 後にアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="78e26-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time, typically around 1 second or so.</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="78e26-122">ハンドフリーに移行する</span><span class="sxs-lookup"><span data-stu-id="78e26-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="78e26-123">これらのシナリオでは、コマンドの実行とナビゲーションのために、ホログラムを使用してハンドを解放することは、アプリケーションをエンドツーエンドで操作するための絶対的な要件から、ユーザーが自由に切り替えることができるようになります。ごと.</span><span class="sxs-lookup"><span data-stu-id="78e26-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="78e26-124">アプリケーションの要件によって、熟考、音声コマンド、または単一の音声コマンドを使用するかどうかにかかわらず、常にハンドフリーで使用する必要がある場合は、UI に適切な accomodations を作成してください。</span><span class="sxs-lookup"><span data-stu-id="78e26-124">If the requirement of the application is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="78e26-125">対象ユーザーが自由に自由に切り替えられるようにする必要がある場合は、次の原則を考慮することが重要です。</span><span class="sxs-lookup"><span data-stu-id="78e26-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="78e26-126">ユーザーが既に切り替え先のモードになっているとします。</span><span class="sxs-lookup"><span data-stu-id="78e26-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="78e26-127">たとえば、ユーザーが工場のフロアにいて、Hololens のビデオ参照を見ているときに、レンチを選択して作業を開始した場合、彼女は、レンチを押してボタンを押すことなく、handsfree で作業を開始する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="78e26-127">For instance, if the user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would start working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="78e26-128">彼女は、音声コマンドを使用して音声セッションを呼び出し、熟考を開始するために既に表示されている UI で熟考、"select" という単語を言い出すことができるはずです。</span><span class="sxs-lookup"><span data-stu-id="78e26-128">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="78e26-129">ユーザーは次のことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="78e26-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="78e26-130">ハンズフリーのまま、ハンドフリーに切り替える</span><span class="sxs-lookup"><span data-stu-id="78e26-130">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="78e26-131">手で手に切り替える</span><span class="sxs-lookup"><span data-stu-id="78e26-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="78e26-132">コントローラーを使用してコントローラーに切り替える</span><span class="sxs-lookup"><span data-stu-id="78e26-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="78e26-133">モードを切り替えるための冗長な方法を作成する</span><span class="sxs-lookup"><span data-stu-id="78e26-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="78e26-134">最初の原則はアクセスに関するものですが、2番目の原則は可用性です。</span><span class="sxs-lookup"><span data-stu-id="78e26-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="78e26-135">モードを切り替える方法は1つだけではありません。</span><span class="sxs-lookup"><span data-stu-id="78e26-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="78e26-136">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="78e26-136">Some examples would be:</span></span> 
* <span data-ttu-id="78e26-137">音声操作を開始するボタン</span><span class="sxs-lookup"><span data-stu-id="78e26-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="78e26-138">見つめ + 熟考を使用してに切り替えるための音声コマンド</span><span class="sxs-lookup"><span data-stu-id="78e26-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="78e26-139">ドラマのダッシュを追加する</span><span class="sxs-lookup"><span data-stu-id="78e26-139">Add a dash of drama</span></span>
<span data-ttu-id="78e26-140">モードの切り替えは大きな問題です。このような切り替えが行われたときに、ユーザーが何が起こったかをユーザーに知らせるために、これらの遷移が明示的でも劇的なスイッチであることが重要です。</span><span class="sxs-lookup"><span data-stu-id="78e26-140">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="78e26-141">使いやすさのチェックリスト</span><span class="sxs-lookup"><span data-stu-id="78e26-141">Usability checklist</span></span>

<span data-ttu-id="78e26-142">**エンドツーエンドであらゆることをユーザーが自由に実行できますか。**</span><span class="sxs-lookup"><span data-stu-id="78e26-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="78e26-143">すべての interactible に自由にアクセスできます</span><span class="sxs-lookup"><span data-stu-id="78e26-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="78e26-144">サイズ変更、配置、スワイプ、タップなどのすべてのカスタムジェスチャに代わるものがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="78e26-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="78e26-145">UI のプレゼンス、配置、および詳細度を常にユーザーが確実に制御できるようにする</span><span class="sxs-lookup"><span data-stu-id="78e26-145">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="78e26-146">UI の取得方法</span><span class="sxs-lookup"><span data-stu-id="78e26-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="78e26-147">ビューの外にある UI のアドレス指定 (視界)</span><span class="sxs-lookup"><span data-stu-id="78e26-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="78e26-148">表示する量 (</span><span class="sxs-lookup"><span data-stu-id="78e26-148">How much I see, where, when</span></span>

<span data-ttu-id="78e26-149">**相互作用のしくみは、適切な affordances を使用して学習し、補強するのでしょうか。**</span><span class="sxs-lookup"><span data-stu-id="78e26-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="78e26-150">ユーザーが理解している...</span><span class="sxs-lookup"><span data-stu-id="78e26-150">Does the user understand ...</span></span>
* <span data-ttu-id="78e26-151">[...]どのモードであるか。</span><span class="sxs-lookup"><span data-stu-id="78e26-151">... What mode they are in?</span></span>
* <span data-ttu-id="78e26-152">[...]このモードでできること</span><span class="sxs-lookup"><span data-stu-id="78e26-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="78e26-153">[...]現在の状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="78e26-153">... What is the current state?</span></span>
* <span data-ttu-id="78e26-154">[...]どのように移行できますか。</span><span class="sxs-lookup"><span data-stu-id="78e26-154">... How they can transition out?</span></span>
    
<span data-ttu-id="78e26-155">**UI はハンドフリーに最適化されていますか。**</span><span class="sxs-lookup"><span data-stu-id="78e26-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="78e26-156">例:熟考 affordances は、一般的な2D パターンに組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="78e26-156">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="78e26-157">例:オブジェクトの強調表示により、音声を対象とすることが適切です。</span><span class="sxs-lookup"><span data-stu-id="78e26-157">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="78e26-158">例:音声通話は、有効にする必要があるキャプションに適しています。</span><span class="sxs-lookup"><span data-stu-id="78e26-158">Example: Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="78e26-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="78e26-159">See also</span></span>
* [<span data-ttu-id="78e26-160">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="78e26-160">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="78e26-161">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="78e26-161">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="78e26-162">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="78e26-162">Point and commit with hands</span></span>](point-and-commit.md)
