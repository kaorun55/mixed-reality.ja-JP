---
title: 音声コマンドの実行
description: 視線、ジェスチャ、音声 (GGV) は、HoloLens の相互作用の主要な手段です。 この記事では、音声の設計に思慮深いガイダンスを提供します。
author: shentan
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality、デザイン、対話、音声
ms.openlocfilehash: 084c1228d17c3e23b38d9b8918c13080598aea98
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039190"
---
# <a name="voice-commanding"></a><span data-ttu-id="a3354-105">音声コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="a3354-105">Voice commanding</span></span>

<span data-ttu-id="a3354-106">("Select") のポインターとしてかどうか、ターゲットの mechaninism として視線の先を通常使用音声コマンドを使用する場合、またはアプリケーションに、コマンドを送信する (「表示, に言って」)。</span><span class="sxs-lookup"><span data-stu-id="a3354-106">When using voice commands, gaze is typically used as the targeting mechaninism, whether as a pointer ("select") or to direct your command to an application ("see it, say it").</span></span> <span data-ttu-id="a3354-107">一部の音声コマンドに「移動を開始する」または「Hey, Cortana」のように、すべてのターゲットを必要としないもちろん、</span><span class="sxs-lookup"><span data-stu-id="a3354-107">Of course, some voice commands don't require a target at all, like "go to start" or "Hey, Cortana."</span></span>


## <a name="device-support"></a><span data-ttu-id="a3354-108">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="a3354-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a3354-109">機能</span><span class="sxs-lookup"><span data-stu-id="a3354-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="a3354-110"><a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></span><span class="sxs-lookup"><span data-stu-id="a3354-110"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="a3354-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a3354-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="a3354-112"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="a3354-112"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td></td><td style="text-align: center;"> <span data-ttu-id="a3354-113">✔️</span><span class="sxs-lookup"><span data-stu-id="a3354-113">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="a3354-114">✔️</span><span class="sxs-lookup"><span data-stu-id="a3354-114">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="a3354-115">✔️ (とヘッドセットがアタッチされている)</span><span class="sxs-lookup"><span data-stu-id="a3354-115">✔️ (with headset attached)</span></span></td>
</tr>
</table>



## <a name="how-to-use-voice"></a><span data-ttu-id="a3354-116">音声を使用する方法</span><span class="sxs-lookup"><span data-stu-id="a3354-116">How to use voice</span></span>

<span data-ttu-id="a3354-117">ビルドする経験に音声コマンドを追加することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a3354-117">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="a3354-118">音声は、強力かつ便利な方法は、システムとアプリを制御します。</span><span class="sxs-lookup"><span data-stu-id="a3354-118">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="a3354-119">ユーザーは、さまざまな言語とアクセントと話し、いるために、音声キーワードの適切な選択肢がユーザーのコマンドが明確に解釈されることを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="a3354-119">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="a3354-120">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="a3354-120">Best practices</span></span>

<span data-ttu-id="a3354-121">滑らかな音声認識に役立ついくつかのプラクティスを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a3354-121">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="a3354-122">**簡潔なコマンドを使用して**- 可能であれば、2 つ以上の音節文字のキーワードを選択します。</span><span class="sxs-lookup"><span data-stu-id="a3354-122">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="a3354-123">1 音節単語は、別のアクセントの担当者が読み上げるときに、別の母音サウンドを使用する傾向があります。</span><span class="sxs-lookup"><span data-stu-id="a3354-123">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="a3354-124">以下に例を示します。「現在選択されているビデオを再生」より優れた「ビデオを再生」が</span><span class="sxs-lookup"><span data-stu-id="a3354-124">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="a3354-125">**単純なボキャブラリを使用して、** -例。「Show プラカード」よりも優れていますが「表示に注意してください」</span><span class="sxs-lookup"><span data-stu-id="a3354-125">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="a3354-126">**コマンドが非破壊的な確認**- 音声認識コマンドを実行できるすべての操作は非破壊的なことを確認し、簡単にできる場合は、ユーザーの近くの読み上げを誤って別のユーザーがコマンドを開始します。</span><span class="sxs-lookup"><span data-stu-id="a3354-126">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="a3354-127">**ような発音コマンドを避ける**-非常に類似した複数の音声コマンドを登録しないようにします。</span><span class="sxs-lookup"><span data-stu-id="a3354-127">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="a3354-128">以下に例を示します。「詳細を表示する」と"store が表示"には、ほぼ発音を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a3354-128">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="a3354-129">**使用していない場合、アプリの登録を解除**- アプリが特定の音声コマンドが、有効な状態にないその他のコマンドは、1 つの混乱しないように登録を解除を検討してください。</span><span class="sxs-lookup"><span data-stu-id="a3354-129">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="a3354-130">**別のアクセント付きテスト**-別のアクセントのユーザーとアプリをテストします。</span><span class="sxs-lookup"><span data-stu-id="a3354-130">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="a3354-131">**音声コマンドの一貫性を維持**- 前のページには「戻る」の場合、アプリケーションでは、この動作を維持します。</span><span class="sxs-lookup"><span data-stu-id="a3354-131">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="a3354-132">**システムのコマンドを使用しないように**-次の音声コマンドは、システムの予約されています。</span><span class="sxs-lookup"><span data-stu-id="a3354-132">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="a3354-133">これらは、アプリケーションでない使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3354-133">These should not be used by applications.</span></span>
   * <span data-ttu-id="a3354-134">"こんにちは Cortana"</span><span class="sxs-lookup"><span data-stu-id="a3354-134">"Hey Cortana"</span></span>
   * <span data-ttu-id="a3354-135">"Select"</span><span class="sxs-lookup"><span data-stu-id="a3354-135">"Select"</span></span>

### <a name="select"></a><span data-ttu-id="a3354-136">"Select"</span><span class="sxs-lookup"><span data-stu-id="a3354-136">"Select"</span></span>

<span data-ttu-id="a3354-137">いつでも"select"と答えるとするには、視線の先のカーソルをポイントはすべてアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="a3354-137">Saying "select" at any time will activate whatever the gaze cursor is pointing at.</span></span> 

><span data-ttu-id="a3354-138">注:HoloLens 2 で単語を言うことにより最初に呼び出される注視カーソル ニーズ"select"です。</span><span class="sxs-lookup"><span data-stu-id="a3354-138">Note: In HoloLens 2, the gaze cursor needs to first be invoked by saying the word "select".</span></span> <span data-ttu-id="a3354-139">たとえば、"select"もう一度アクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="a3354-139">Say, "select" again to activate.</span></span> <span data-ttu-id="a3354-140">視線の先のカーソルを非表示にするには、手--airtap を使ってか、オブジェクトをタッチします。</span><span class="sxs-lookup"><span data-stu-id="a3354-140">To hide the gaze cursor, simply use your hands -- airtap or touch an object.</span></span> 

### <a name="see-it-say-it"></a><span data-ttu-id="a3354-141">表示、」ということ</span><span class="sxs-lookup"><span data-stu-id="a3354-141">See it, say it</span></span>

<span data-ttu-id="a3354-142">Windows Mixed Reality で「認識, に言って」音声モデルが採用されている場所**ボタンにラベルが関連付けられている音声コマンドと同一**します。</span><span class="sxs-lookup"><span data-stu-id="a3354-142">Windows Mixed Reality has employed a "see it, say it" voice model where **labels on buttons are identical to the associated voice commands**.</span></span> <span data-ttu-id="a3354-143">ラベルと音声コマンドの間の任意の dissonance 存在しないため、ユーザーを理解できる何を言おうシステムを制御します。</span><span class="sxs-lookup"><span data-stu-id="a3354-143">Because there isn’t any dissonance between the label and the voice command, users can better understand what to say to control the system.</span></span> <span data-ttu-id="a3354-144">このボタンをもたらす中に補強するために、 **「音声は、ヒントを下げなければ」** ボタンが有効になっている音声通信が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3354-144">To reinforce this, while dwelling on a button, a **"voice dwell tip"** appears to communicate which buttons are voice enabled.</span></span>


![例 1」ということを確認します。](images/voice-seeitsayit1-640px.jpg)

<span data-ttu-id="a3354-146">![例 2 と答えるを参照してください。](images/voice-seeitsayit2-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3354-146">![See it say it example 2](images/voice-seeitsayit2-640px.jpg)</span></span><br>
<span data-ttu-id="a3354-147">*例については「を参照してください、たとえば、」*</span><span class="sxs-lookup"><span data-stu-id="a3354-147">*Examples of "see it, say it"*</span></span>

### <a name="voices-strengths"></a><span data-ttu-id="a3354-148">音声の長所</span><span class="sxs-lookup"><span data-stu-id="a3354-148">Voice's strengths</span></span>

<span data-ttu-id="a3354-149">音声入力は、当社のインテントを通信するために自然な方法です。</span><span class="sxs-lookup"><span data-stu-id="a3354-149">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="a3354-150">音声がインターフェイスに特に適して**トラバーサル**(ユーザーがあります「と言います戻る」を検索中に Web ページのセットアップし、アプリに戻る ボタンをクリックすることではなく) インターフェイスの複数の手順をユーザーがカットのに役立つためです。</span><span class="sxs-lookup"><span data-stu-id="a3354-150">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at Web page, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="a3354-151">この小さな時間の節約は、強力な**感情的な効果**でユーザーのエクスペリエンスの認識と少量の後押しを提供します。</span><span class="sxs-lookup"><span data-stu-id="a3354-151">This small time savings has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="a3354-152">音声を使用しても便利な入力方法または完全な腕をしましたが、ときに**マルチタスク**します。</span><span class="sxs-lookup"><span data-stu-id="a3354-152">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="a3354-153">キーボードで入力することは困難であり、デバイスで**ディクテーションを音声**効率的な方法を入力することができます。</span><span class="sxs-lookup"><span data-stu-id="a3354-153">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input.</span></span> <span data-ttu-id="a3354-154">最後に、場合によってはときに、**精度の範囲**視線、ジェスチャは、制限は、音声がありますユーザーの入力メソッドを信頼できるのみです。</span><span class="sxs-lookup"><span data-stu-id="a3354-154">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, Voice might be a user’s only trusted method input.</span></span>

<span data-ttu-id="a3354-155">**音声を使用してがどのようにメリット ユーザー**</span><span class="sxs-lookup"><span data-stu-id="a3354-155">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="a3354-156">時間の短縮、最終目的をより効率的に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3354-156">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="a3354-157">-労力を最小限に抑えられますよりスムーズになり、簡単なタスクください。</span><span class="sxs-lookup"><span data-stu-id="a3354-157">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="a3354-158">Cognitive 負荷の軽減が直感的で簡単に学び、注意してください。</span><span class="sxs-lookup"><span data-stu-id="a3354-158">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="a3354-159">これはしれませんで、動作の観点から社会に関する規範を適合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3354-159">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="a3354-160">これのルーチンの音声が常習的な動作になることができます簡単にします。</span><span class="sxs-lookup"><span data-stu-id="a3354-160">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="voices-weaknesses"></a><span data-ttu-id="a3354-161">音声の短所</span><span class="sxs-lookup"><span data-stu-id="a3354-161">Voice's weaknesses</span></span>

<span data-ttu-id="a3354-162">音声では、いくつか短所もあります。</span><span class="sxs-lookup"><span data-stu-id="a3354-162">Voice also has some weaknesses.</span></span> <span data-ttu-id="a3354-163">詳細に制御は、その 1 つです。</span><span class="sxs-lookup"><span data-stu-id="a3354-163">Fine-grained control is one of them.</span></span> <span data-ttu-id="a3354-164">(たとえば、ユーザー「発生」と言うことがどの程度と答えることはできません。</span><span class="sxs-lookup"><span data-stu-id="a3354-164">(for example a user might say "louder," but can’t say how much.</span></span> <span data-ttu-id="a3354-165">「少し」を定量化する困難です。</span><span class="sxs-lookup"><span data-stu-id="a3354-165">"A little" is hard to quantify.</span></span> <span data-ttu-id="a3354-166">移動または音声でモ ノのスケーリングは困難です (音声はコントロールの粒度を提供していません)。</span><span class="sxs-lookup"><span data-stu-id="a3354-166">Moving or scaling things with voice is also difficult (voice does not offer the granularity of control).</span></span> <span data-ttu-id="a3354-167">音声が完璧なこともできます。</span><span class="sxs-lookup"><span data-stu-id="a3354-167">Voice can also be imperfect.</span></span> <span data-ttu-id="a3354-168">場合ボイス システムは正しくコマンドを聞くことや、お待ちしておりますコマンドが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="a3354-168">Sometimes a voice system incorrectly hears a command or fails to hear a command.</span></span> <span data-ttu-id="a3354-169">このようなエラーからの回復は、任意のインターフェイスに課題です。</span><span class="sxs-lookup"><span data-stu-id="a3354-169">Recovering from such errors is a challenge in any interface.</span></span> <span data-ttu-id="a3354-170">最後に、音声はソーシャル許容できない公共の場所にします。</span><span class="sxs-lookup"><span data-stu-id="a3354-170">Lastly, voice may not be socially acceptable in public places.</span></span> <span data-ttu-id="a3354-171">ユーザーがならまたはできないいくつかの点があります。</span><span class="sxs-lookup"><span data-stu-id="a3354-171">There are some things that users can’t or shouldn’t say.</span></span> <span data-ttu-id="a3354-172">これらの崖が最も得意使用する音声認識を許可します。</span><span class="sxs-lookup"><span data-stu-id="a3354-172">These cliffs allow speech to be used for what it is best at.</span></span>

### <a name="voice-feedback-states"></a><span data-ttu-id="a3354-173">音声のフィードバックの状態</span><span class="sxs-lookup"><span data-stu-id="a3354-173">Voice feedback states</span></span>

<span data-ttu-id="a3354-174">音声が正しく適用されると、ユーザーが理解**何ができるし、答えて、フィードバックを取得**システム**正しくを聞いた**します。</span><span class="sxs-lookup"><span data-stu-id="a3354-174">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="a3354-175">これら 2 つのシグナルは、プライマリの入力として音声を使用して確信を持てるユーザーを確認します。</span><span class="sxs-lookup"><span data-stu-id="a3354-175">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="a3354-176">何を示す図が音声入力が認識されると、カーソルとユーザーに通信する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a3354-176">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>

<span data-ttu-id="a3354-177">![カーソルの音声フィードバック状態](images/voicefeedbackstates.png)</span><span class="sxs-lookup"><span data-stu-id="a3354-177">![Voice feedback states for cursor](images/voicefeedbackstates.png)</span></span><br>
<span data-ttu-id="a3354-178">*カーソルの音声フィードバック状態*</span><span class="sxs-lookup"><span data-stu-id="a3354-178">*Voice feedback states for cursor*</span></span>

## <a name="top-things-users-should-know-about-speech-on-windows-mixed-reality"></a><span data-ttu-id="a3354-179">最上位のモ ノのユーザーは、"speech"Windows Mixed Reality on について 必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3354-179">Top things users should know about "speech" on Windows Mixed Reality</span></span>
* <span data-ttu-id="a3354-180">たとえば **"Select"** (anywhere を使用このボタンをクリックする) ボタンを対象とします。</span><span class="sxs-lookup"><span data-stu-id="a3354-180">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="a3354-181">指定すると、**アプリ バー ボタンのラベル名**処置を実行する一部のアプリでします。</span><span class="sxs-lookup"><span data-stu-id="a3354-181">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="a3354-182">たとえば、アプリを見ているときに、ユーザーことができますコマンドを言う"Remove"、世界中からアプリを削除する (この時間を節約、手でそれをクリックする必要がなくなります)。</span><span class="sxs-lookup"><span data-stu-id="a3354-182">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="a3354-183">Cortana のことを示すリッスンを開始する**コルタナさん」。**</span><span class="sxs-lookup"><span data-stu-id="a3354-183">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="a3354-184">自分の質問 (」「コルタナさん高さは Eiffel tower)、(」「コルタナさん Netflix がオープン)、アプリを開くするように指示するまたは ("「コルタナさん、ホームを) [スタート] メニューを表示するように指示するとします。</span><span class="sxs-lookup"><span data-stu-id="a3354-184">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="a3354-185">音声に関する質問や問題の一般的なユーザーがあります。</span><span class="sxs-lookup"><span data-stu-id="a3354-185">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="a3354-186">何も言えません。</span><span class="sxs-lookup"><span data-stu-id="a3354-186">What can I say?</span></span>
* <span data-ttu-id="a3354-187">システムが正しく me 聞こえるかを確認する方法</span><span class="sxs-lookup"><span data-stu-id="a3354-187">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="a3354-188">システムに続けて、音声コマンドが正しくないいます。</span><span class="sxs-lookup"><span data-stu-id="a3354-188">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="a3354-189">音声コマンドを指定すると、反応がないです。</span><span class="sxs-lookup"><span data-stu-id="a3354-189">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="a3354-190">音声コマンドを指定すると、間違ったやり方を反応します。</span><span class="sxs-lookup"><span data-stu-id="a3354-190">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="a3354-191">自分の音声を特定のアプリまたはアプリのコマンドを対象する方法を教えてください。</span><span class="sxs-lookup"><span data-stu-id="a3354-191">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="a3354-192">HoloLens で音声コマンドいろいろ holographic のフレームを使用できますか。</span><span class="sxs-lookup"><span data-stu-id="a3354-192">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="see-also"></a><span data-ttu-id="a3354-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3354-193">See also</span></span>
* [<span data-ttu-id="a3354-194">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="a3354-194">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="a3354-195">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="a3354-195">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
