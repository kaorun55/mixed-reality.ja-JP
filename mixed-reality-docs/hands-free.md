---
title: ハンズフリー用のアプリを最適化します。
description: ハンズフリー用のアプリを最適化します。
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: 複合現実、ハンズフリー、視線、視線を対象との相互作用、デザイン
ms.openlocfilehash: f39a9524831161997b59be6cf89b124fa5b29c78
ms.sourcegitcommit: d6d96d552ec10cd7e6502fbbc1905432e2878325
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524328"
---
# <a name="optimizing-your-app-for-hands-free"></a><span data-ttu-id="40a32-104">ハンズフリー用のアプリを最適化します。</span><span class="sxs-lookup"><span data-stu-id="40a32-104">Optimizing your app for hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="40a32-105">シナリオ</span><span class="sxs-lookup"><span data-stu-id="40a32-105">Scenarios</span></span>

<span data-ttu-id="40a32-106">」の説明に従って、[相互作用モデルの概要](interaction-fundamentals.md)ユーザーとの目標を識別する 1 回、そのタスクを実行する作業に直面可能性がありますどのような環境や状況の問題を確認してください。</span><span class="sxs-lookup"><span data-stu-id="40a32-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="40a32-107">たとえば、多くのユーザーに、実際の目標を達成され、手を使用する必要があります。 手、およびコント ローラー ベースのインターフェイスとの対話が困難です。</span><span class="sxs-lookup"><span data-stu-id="40a32-107">For example, many users need to use their hands to accomplish their real-world goals and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="40a32-108">特定のシナリオは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="40a32-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="40a32-109">手はビジー状態、タスクを使用してガイド付き中</span><span class="sxs-lookup"><span data-stu-id="40a32-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="40a32-110">手がビジー状態中には、資料を参照します。</span><span class="sxs-lookup"><span data-stu-id="40a32-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="40a32-111">手の形の疲労</span><span class="sxs-lookup"><span data-stu-id="40a32-111">Hand fatigue</span></span>
* <span data-ttu-id="40a32-112">グローブを追跡することはできません。</span><span class="sxs-lookup"><span data-stu-id="40a32-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="40a32-113">何かを実行します。</span><span class="sxs-lookup"><span data-stu-id="40a32-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="40a32-114">ハンズフリー モダリティ</span><span class="sxs-lookup"><span data-stu-id="40a32-114">Hands-free modalities</span></span>

### <a name="voice-commanding"></a><span data-ttu-id="40a32-115">音声コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="40a32-115">Voice commanding</span></span>

<span data-ttu-id="40a32-116">コマンドと制御のインターフェイスは、音声を使用するだけでなくも複数の手順をスキップしてハンズフリー、動作をするユーザーを許可します。</span><span class="sxs-lookup"><span data-stu-id="40a32-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="40a32-117">このモードの使用状況の範囲からいずれかのボタンの名前を読み取るだけをユーザーにタスクを実現できるとしている担当者と会話しているを参照してください it-say it のようにアクティブにするに音量を上げるを許可します。</span><span class="sxs-lookup"><span data-stu-id="40a32-117">The usage of this modality can range from allowing the user to simply reading any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>

* [<span data-ttu-id="40a32-118">音声設計</span><span class="sxs-lookup"><span data-stu-id="40a32-118">Voice design</span></span>](voice-design.md)


### <a name="head-gaze-and-dwell"></a><span data-ttu-id="40a32-119">Head 注視しドウェル</span><span class="sxs-lookup"><span data-stu-id="40a32-119">Head gaze and dwell</span></span>

<span data-ttu-id="40a32-120">ハンズフリー状況によっては、音声を使用したりはできません理想的なこともできます。</span><span class="sxs-lookup"><span data-stu-id="40a32-120">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="40a32-121">大きい音の工場出荷時の環境、プライバシー、またはソーシャル規範のすべての制約を指定できます。</span><span class="sxs-lookup"><span data-stu-id="40a32-121">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="40a32-122">ヘッド視線 + 熟考モデルでは、接続を維持しながら、ポイント、ヘッドのベクターを使用して、アプリを移動するユーザーまたはもたらすボタンがアクティブ化後一定の時間 (通常は約 1 秒程度)。</span><span class="sxs-lookup"><span data-stu-id="40a32-122">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time (typically around 1 second or so).</span></span> 

* [<span data-ttu-id="40a32-123">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="40a32-123">Gaze and dwell</span></span>](gaze-and-dwell.md)

## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="40a32-124">ハンズフリーとの間の移行</span><span class="sxs-lookup"><span data-stu-id="40a32-124">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="40a32-125">これらのシナリオでは、動作して、アプリでは、エンド ツー エンド、ユーザーをいつでもの遷移を追加、利便性を絶対条件の中からコマンドを実行およびナビゲーション ホログラム対話から手を解放できる範囲です。</span><span class="sxs-lookup"><span data-stu-id="40a32-125">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the app, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="40a32-126">場合、アプリの要件が常に使用すること、ハンズフリー ドウェル、音声コマンド、または 1 つの音声コマンドを使用しているかどうか、"select"し、適切な宿泊施設の UI にすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="40a32-126">If the requirement of the app is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="40a32-127">手から自分の裁量自在に切り替えることができる、対象ユーザーに必要な場合がこれらの原則を考慮に入れてに重要です。</span><span class="sxs-lookup"><span data-stu-id="40a32-127">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take these principles into account:</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="40a32-128">既にユーザー モードに切り替えたいを前提としています。</span><span class="sxs-lookup"><span data-stu-id="40a32-128">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="40a32-129">たとえば、ユーザーが自分の Hololens への参照をビデオを視聴、工場では、作業を開始するレンチ アイコンを選択することにした場合は、ほとんどの場合たいハンズフリー ボタンを押すレンチを配置することがなく作業を開始します。</span><span class="sxs-lookup"><span data-stu-id="40a32-129">For instance, if your user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would like to begin working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="40a32-130">音声コマンドを使用して音声セッションを呼び出し、ドウェル、開始を既に表示されている UI について熟考する彼女できる必要がありますかと、単語"select"。</span><span class="sxs-lookup"><span data-stu-id="40a32-130">She should be able to invoke a voice session with a voice command, dwell on already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="40a32-131">ユーザー機能があります。</span><span class="sxs-lookup"><span data-stu-id="40a32-131">The user should have the ability to:</span></span> 
* <span data-ttu-id="40a32-132">ハンズフリー ハンズフリー中に切り替える</span><span class="sxs-lookup"><span data-stu-id="40a32-132">Switch to handsfree while handsfree</span></span>
* <span data-ttu-id="40a32-133">自分の手で手に切り替える</span><span class="sxs-lookup"><span data-stu-id="40a32-133">Switch to hands with your hands</span></span>
* <span data-ttu-id="40a32-134">コント ローラーを使用してコント ローラーに切り替える</span><span class="sxs-lookup"><span data-stu-id="40a32-134">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="40a32-135">作成モードを切り替える方法は冗長</span><span class="sxs-lookup"><span data-stu-id="40a32-135">Create redundant ways to switch modes</span></span>
<span data-ttu-id="40a32-136">目の原則では、アクセスの詳細については、2 つ目は、可用性の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="40a32-136">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="40a32-137">いないだけが必要なモードとの間の遷移の 1 つの方法です。</span><span class="sxs-lookup"><span data-stu-id="40a32-137">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="40a32-138">いくつかの例は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="40a32-138">Some examples would be:</span></span> 
* <span data-ttu-id="40a32-139">音声の相互作用を開始するためのボタン</span><span class="sxs-lookup"><span data-stu-id="40a32-139">A button to begin voice interactions</span></span>
* <span data-ttu-id="40a32-140">音声コマンドを注視 + ドウェルを使用する移行する</span><span class="sxs-lookup"><span data-stu-id="40a32-140">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="40a32-141">ドラマのダッシュを追加します。</span><span class="sxs-lookup"><span data-stu-id="40a32-141">Add a dash of drama</span></span>
<span data-ttu-id="40a32-142">モードの切り替えはたいした問題で--ことが重要ですがこれらの遷移が発生する場合、何が起こったかユーザーに、明示的なでも大幅なスイッチであります。</span><span class="sxs-lookup"><span data-stu-id="40a32-142">A mode switch is a big deal -- it is important that when these transitions happen, that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="40a32-143">使いやすさのチェックリスト</span><span class="sxs-lookup"><span data-stu-id="40a32-143">Usability checklist</span></span>

<span data-ttu-id="40a32-144">**ユーザーにすべておよびハンズフリー、エンド ツー エンドのものを実行できますか。**</span><span class="sxs-lookup"><span data-stu-id="40a32-144">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="40a32-145">すべての interactible アクセスできる必要があるに</span><span class="sxs-lookup"><span data-stu-id="40a32-145">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="40a32-146">(サイズ変更、配置、スワイプといった、タップなど) のすべてのカスタム ジェスチャに代わるものがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="40a32-146">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="40a32-147">ユーザーが常に確実にコントロールの UI のプレゼンス、配置、詳細度を持っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="40a32-147">Ensure that the user has confident control of UI presence, placement, verbosity at all times</span></span>
    * <span data-ttu-id="40a32-148">UI を取得します。</span><span class="sxs-lookup"><span data-stu-id="40a32-148">Getting UI out of the way</span></span>
    * <span data-ttu-id="40a32-149">視野 (FOV) 外のアドレス指定の UI</span><span class="sxs-lookup"><span data-stu-id="40a32-149">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="40a32-150">表示量、どこで、ときに</span><span class="sxs-lookup"><span data-stu-id="40a32-150">How much I see, where, when</span></span>

<span data-ttu-id="40a32-151">**相互作用のしくみされている学習し、適切なアフォーで補強ですか。**</span><span class="sxs-lookup"><span data-stu-id="40a32-151">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="40a32-152">ユーザーが理解しています.</span><span class="sxs-lookup"><span data-stu-id="40a32-152">Does the user understand ...</span></span>
* <span data-ttu-id="40a32-153">...いるモードは何ですか。</span><span class="sxs-lookup"><span data-stu-id="40a32-153">... What mode they are in?</span></span>
* <span data-ttu-id="40a32-154">...実行できるこのモードででしょうか。</span><span class="sxs-lookup"><span data-stu-id="40a32-154">... What they can do in this mode?</span></span>
* <span data-ttu-id="40a32-155">...現在の状態とは何ですか。</span><span class="sxs-lookup"><span data-stu-id="40a32-155">... What is the current state?</span></span>
* <span data-ttu-id="40a32-156">...方法を移行できますか。</span><span class="sxs-lookup"><span data-stu-id="40a32-156">... How they can transition out?</span></span>
    
<span data-ttu-id="40a32-157">**UI に適して楽にしますか。**</span><span class="sxs-lookup"><span data-stu-id="40a32-157">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="40a32-158">例:</span><span class="sxs-lookup"><span data-stu-id="40a32-158">Ex.</span></span> <span data-ttu-id="40a32-159">ドウェル アフォーは 2D の通常のパターンに組み込まれていません</span><span class="sxs-lookup"><span data-stu-id="40a32-159">Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="40a32-160">例:</span><span class="sxs-lookup"><span data-stu-id="40a32-160">Ex.</span></span> <span data-ttu-id="40a32-161">音声のターゲット設定は、オブジェクトが強調表示との連携強化</span><span class="sxs-lookup"><span data-stu-id="40a32-161">Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="40a32-162">例:</span><span class="sxs-lookup"><span data-stu-id="40a32-162">Ex.</span></span> <span data-ttu-id="40a32-163">音声の相互作用がオンにする必要があるキャプションとの連携強化</span><span class="sxs-lookup"><span data-stu-id="40a32-163">Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="40a32-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="40a32-164">See also</span></span>
* [<span data-ttu-id="40a32-165">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="40a32-165">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="40a32-166">直接操作</span><span class="sxs-lookup"><span data-stu-id="40a32-166">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="40a32-167">ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="40a32-167">Point and commit</span></span>](point-and-commit.md)
