---
title: ハンズフリー
description: ハンズフリー用のアプリを最適化します。
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: 複合現実、ハンズフリー、視線、視線を対象との相互作用、デザイン
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414389"
---
# <a name="hands-free"></a><span data-ttu-id="e9483-104">ハンズフリー</span><span class="sxs-lookup"><span data-stu-id="e9483-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="e9483-105">シナリオ</span><span class="sxs-lookup"><span data-stu-id="e9483-105">Scenarios</span></span>

<span data-ttu-id="e9483-106">」の説明に従って、[相互作用モデルの概要](interaction-fundamentals.md)ユーザーとの目標を識別する 1 回、そのタスクを実行する作業に直面可能性がありますどのような環境や状況の問題を確認してください。</span><span class="sxs-lookup"><span data-stu-id="e9483-106">As outlined in the [Interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="e9483-107">たとえば、多くのユーザーが手を使用して、実際の目標を達成する必要があり、手、およびコント ローラー ベースのインターフェイスとの対話が困難になります。</span><span class="sxs-lookup"><span data-stu-id="e9483-107">For example, many users need to use their hands to accomplish their real-world goals, and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="e9483-108">特定のシナリオは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e9483-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="e9483-109">手はビジー状態、タスクを使用してガイド付き中</span><span class="sxs-lookup"><span data-stu-id="e9483-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="e9483-110">手がビジー状態中には、資料を参照します。</span><span class="sxs-lookup"><span data-stu-id="e9483-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="e9483-111">手の形の疲労</span><span class="sxs-lookup"><span data-stu-id="e9483-111">Hand fatigue</span></span>
* <span data-ttu-id="e9483-112">グローブを追跡することはできません。</span><span class="sxs-lookup"><span data-stu-id="e9483-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="e9483-113">何かを実行します。</span><span class="sxs-lookup"><span data-stu-id="e9483-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="e9483-114">ハンズフリー モダリティ</span><span class="sxs-lookup"><span data-stu-id="e9483-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="e9483-115">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="e9483-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="e9483-116">コマンドと制御のインターフェイスは、音声を使用するだけでなくも複数の手順をスキップしてハンズフリー、動作をするユーザーを許可します。</span><span class="sxs-lookup"><span data-stu-id="e9483-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="e9483-117">このモードの使用状況の範囲から、ユーザーは単純にタスクを実現できるとしている担当者と会話しているを参照してください it-say it のようにアクティブにするに音量を上げるのいずれかのボタンの名前を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="e9483-117">The usage of this modality can range from allowing the user to simply read any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="e9483-118">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="e9483-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="e9483-119">ハンズフリー状況によっては、音声を使用したりはできません理想的なこともできます。</span><span class="sxs-lookup"><span data-stu-id="e9483-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="e9483-120">大きい音の工場出荷時の環境、プライバシー、またはソーシャル規範のすべての制約を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e9483-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="e9483-121">ヘッド視線 + 熟考モデルでは、接続を維持しながら、ポイント、ヘッドのベクターを使用して、アプリを移動するボタンにもたらすはアクティブ化したり、一定時間、通常は約 1 秒程度の後にします。</span><span class="sxs-lookup"><span data-stu-id="e9483-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time, typically around 1 second or so.</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="e9483-122">ハンズフリーとの間の移行</span><span class="sxs-lookup"><span data-stu-id="e9483-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="e9483-123">これらのシナリオについての動作して、アプリケーション、エンド ツー エンド ユーザーは、いずれかの遷移可能、追加の利便性を絶対条件の範囲はコマンドを実行およびナビゲーション ホログラム対話から手を解放時間です。</span><span class="sxs-lookup"><span data-stu-id="e9483-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="e9483-124">場合、アプリケーションの要件を満たすことが常に使用されること、ハンズフリー ドウェル、音声コマンド、または 1 つの音声コマンドを使用しているかどうか、"select"し、適切な宿泊施設の UI にすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e9483-124">If the requirement of the application is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="e9483-125">手から自分の裁量自在に切り替えることができる、対象ユーザーに必要な場合は、次の原則を考慮に入れて必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9483-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="e9483-126">既にユーザー モードに切り替えたいを前提としています。</span><span class="sxs-lookup"><span data-stu-id="e9483-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="e9483-127">たとえば、作業を開始するレンチ アイコンを選択して、ユーザーが自分の Hololens への参照をビデオを視聴、工場でが場合、彼女ほとんどの場合はで作業を開始ハンズフリー ボタンを押すレンチを配置する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e9483-127">For instance, if the user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would start working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="e9483-128">音声コマンドを使用して音声セッションを呼び出し、ドウェル、開始を既に表示されている UI について熟考する彼女できる必要がありますかと、単語"select"。</span><span class="sxs-lookup"><span data-stu-id="e9483-128">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="e9483-129">ユーザー機能があります。</span><span class="sxs-lookup"><span data-stu-id="e9483-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="e9483-130">ハンズフリー ハンズフリー中への切り替え</span><span class="sxs-lookup"><span data-stu-id="e9483-130">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="e9483-131">自分の手で手に切り替える</span><span class="sxs-lookup"><span data-stu-id="e9483-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="e9483-132">コント ローラーを使用してコント ローラーに切り替える</span><span class="sxs-lookup"><span data-stu-id="e9483-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="e9483-133">作成モードを切り替える方法は冗長</span><span class="sxs-lookup"><span data-stu-id="e9483-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="e9483-134">目の原則では、アクセスの詳細については、2 つ目は、可用性の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="e9483-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="e9483-135">いないだけが必要なモードとの間の遷移の 1 つの方法です。</span><span class="sxs-lookup"><span data-stu-id="e9483-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="e9483-136">いくつかの例は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e9483-136">Some examples would be:</span></span> 
* <span data-ttu-id="e9483-137">音声の相互作用を開始するためのボタン</span><span class="sxs-lookup"><span data-stu-id="e9483-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="e9483-138">音声コマンドを注視 + ドウェルを使用する移行する</span><span class="sxs-lookup"><span data-stu-id="e9483-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="e9483-139">ドラマのダッシュを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9483-139">Add a dash of drama</span></span>
<span data-ttu-id="e9483-140">モードの切り替えはたいした--がこれらの遷移が発生するときであることも印象的な明示的なスイッチ、何が起こったかユーザーに重要です。</span><span class="sxs-lookup"><span data-stu-id="e9483-140">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="e9483-141">使いやすさのチェックリスト</span><span class="sxs-lookup"><span data-stu-id="e9483-141">Usability checklist</span></span>

<span data-ttu-id="e9483-142">**ユーザーにすべておよびハンズフリー、エンド ツー エンドのものを実行できますか。**</span><span class="sxs-lookup"><span data-stu-id="e9483-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="e9483-143">すべての interactible アクセスできる必要があるに</span><span class="sxs-lookup"><span data-stu-id="e9483-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="e9483-144">(サイズ変更、配置、スワイプといった、タップなど) のすべてのカスタム ジェスチャに代わるものがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e9483-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="e9483-145">ユーザーが常に UI プレゼンス、配置、および詳細度のコントロールを自信を持っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e9483-145">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="e9483-146">UI を取得します。</span><span class="sxs-lookup"><span data-stu-id="e9483-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="e9483-147">視野 (FOV) 外のアドレス指定の UI</span><span class="sxs-lookup"><span data-stu-id="e9483-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="e9483-148">表示量、どこで、ときに</span><span class="sxs-lookup"><span data-stu-id="e9483-148">How much I see, where, when</span></span>

<span data-ttu-id="e9483-149">**相互作用のしくみされている学習し、適切なアフォーで補強ですか。**</span><span class="sxs-lookup"><span data-stu-id="e9483-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="e9483-150">ユーザーが理解しています.</span><span class="sxs-lookup"><span data-stu-id="e9483-150">Does the user understand ...</span></span>
* <span data-ttu-id="e9483-151">...いるモードは何ですか。</span><span class="sxs-lookup"><span data-stu-id="e9483-151">... What mode they are in?</span></span>
* <span data-ttu-id="e9483-152">...実行できるこのモードででしょうか。</span><span class="sxs-lookup"><span data-stu-id="e9483-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="e9483-153">...現在の状態とは何ですか。</span><span class="sxs-lookup"><span data-stu-id="e9483-153">... What is the current state?</span></span>
* <span data-ttu-id="e9483-154">...方法を移行できますか。</span><span class="sxs-lookup"><span data-stu-id="e9483-154">... How they can transition out?</span></span>
    
<span data-ttu-id="e9483-155">**UI に適して楽にしますか。**</span><span class="sxs-lookup"><span data-stu-id="e9483-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="e9483-156">以下に例を示します。ドウェル アフォーは 2D の通常のパターンに組み込まれていません</span><span class="sxs-lookup"><span data-stu-id="e9483-156">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="e9483-157">以下に例を示します。音声のターゲット設定は、オブジェクトが強調表示との連携強化</span><span class="sxs-lookup"><span data-stu-id="e9483-157">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="e9483-158">以下に例を示します。音声の相互作用がオンにする必要があるキャプションとの連携強化</span><span class="sxs-lookup"><span data-stu-id="e9483-158">Example: Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="e9483-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9483-159">See also</span></span>
* [<span data-ttu-id="e9483-160">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="e9483-160">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e9483-161">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="e9483-161">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e9483-162">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="e9483-162">Point and commit with hands</span></span>](point-and-commit.md)
