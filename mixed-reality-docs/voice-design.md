---
title: 音声コマンド
description: 視線入力、ジェスチャ、音声 (GGV) は、HoloLens での対話の主な手段です。 この記事では、音声設計に関する思慮に富んだガイダンスを提供します。
author: shengkait
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
keywords: Windows Mixed Reality, 設計, 対話, 音声
ms.openlocfilehash: 350acfbe777869f150b7c90c93124e10e155168d
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926709"
---
# <a name="voice-commanding"></a><span data-ttu-id="15976-105">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="15976-105">Voice commanding</span></span>

<span data-ttu-id="15976-106">音声コマンドを使用する場合、通常、宝石はターゲットメカニズムとして使用されます。これは、ポインター ("select") として、またはコマンドをアプリケーションに送信する場合 ("参照してください。" と言います) に使用されます。</span><span class="sxs-lookup"><span data-stu-id="15976-106">When using voice commands, gaze is typically used as the targeting mechanism, whether as a pointer ("select") or to direct your command to an application ("see it, say it").</span></span> <span data-ttu-id="15976-107">もちろん、音声コマンドの中には、「スタートに移動」や「コルタナさん」のようにターゲットが必要ないものもあります。</span><span class="sxs-lookup"><span data-stu-id="15976-107">Of course, some voice commands don't require a target at all, like "go to start" or "Hey, Cortana."</span></span>


## <a name="device-support"></a><span data-ttu-id="15976-108">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="15976-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="15976-109"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="15976-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="15976-110"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="15976-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="15976-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="15976-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="15976-112"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="15976-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="15976-113">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="15976-113">Voice commanding</span></span></td>
        <td><span data-ttu-id="15976-114">✔️</span><span class="sxs-lookup"><span data-stu-id="15976-114">✔️</span></span></td>
        <td><span data-ttu-id="15976-115">✔️</span><span class="sxs-lookup"><span data-stu-id="15976-115">✔️</span></span></td>
        <td><span data-ttu-id="15976-116">✔️ (ヘッドセット付き)</span><span class="sxs-lookup"><span data-stu-id="15976-116">✔️ (with headset attached)</span></span></td>
    </tr>
</table>



## <a name="how-to-use-voice"></a><span data-ttu-id="15976-117">音声の使用方法</span><span class="sxs-lookup"><span data-stu-id="15976-117">How to use voice</span></span>

<span data-ttu-id="15976-118">構築するすべてのエクスペリエンスに対して、音声コマンドを加えることをご検討ください。</span><span class="sxs-lookup"><span data-stu-id="15976-118">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="15976-119">音声は、システムとアプリを制御するための強力かつ便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="15976-119">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="15976-120">ユーザーはさまざまな方言やアクセントで話すので、音声キーワードの適切な選択によって、ユーザーのコマンドが明確に解釈されるようになります。</span><span class="sxs-lookup"><span data-stu-id="15976-120">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="15976-121">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="15976-121">Best practices</span></span>

<span data-ttu-id="15976-122">スムーズな音声認識に役立ついくつかのプラクティスを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="15976-122">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="15976-123">**簡潔なコマンドを使用する** - 可能なら 2 音節以上から成るキーワードを選択します。</span><span class="sxs-lookup"><span data-stu-id="15976-123">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="15976-124">1 音節の単語は、アクセントが異なる人が読み上げると、別の母音が使用されやすくなります。</span><span class="sxs-lookup"><span data-stu-id="15976-124">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="15976-125">例: "ビデオの再生" は、"現在選択されているビデオを再生する" よりも優れています。</span><span class="sxs-lookup"><span data-stu-id="15976-125">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="15976-126">**単純な語彙を使用する**-例: "show プラカード" よりも "メモの表示" が適しています。</span><span class="sxs-lookup"><span data-stu-id="15976-126">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="15976-127">**コマンドが非破壊的であること** - 音声認識コマンドによって実行される可能性のあるすべての操作が非破壊的であり、ユーザーの近くで話している別の人によって誤ってコマンドがトリガーされた場合でも簡単に元に戻せることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="15976-127">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="15976-128">**発音が似ているコマンドを避ける** - 発音がよく似ている音声認識コマンドを複数登録しないようにします。</span><span class="sxs-lookup"><span data-stu-id="15976-128">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="15976-129">例: "more Show" と "Show store" は、よく似た発音です。</span><span class="sxs-lookup"><span data-stu-id="15976-129">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="15976-130">**使用していない場合、アプリの登録を解除する** - アプリの状態が、特定の音声認識コマンドが有効になる状態ではないなら、それが他のコマンドと混同されないよう、アプリを登録解除することをご検討ください。</span><span class="sxs-lookup"><span data-stu-id="15976-130">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="15976-131">**別のアクセントによるテスト** - 別のアクセントのユーザーによってアプリをテストします。</span><span class="sxs-lookup"><span data-stu-id="15976-131">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="15976-132">**音声コマンドの一貫性を維持** - 「戻る」で前のページに戻るようになっているなら、ご自分のアプリケーションでもこの動作を維持してください。</span><span class="sxs-lookup"><span data-stu-id="15976-132">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="15976-133">**システムのコマンドを使用しない** - 次の音声コマンドはシステムで予約されています。</span><span class="sxs-lookup"><span data-stu-id="15976-133">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="15976-134">これらのコマンドは、アプリケーションで使用することができません。</span><span class="sxs-lookup"><span data-stu-id="15976-134">These should not be used by applications.</span></span>
   * <span data-ttu-id="15976-135">「コルタナさん」</span><span class="sxs-lookup"><span data-stu-id="15976-135">"Hey Cortana"</span></span>
   * <span data-ttu-id="15976-136">「選択」</span><span class="sxs-lookup"><span data-stu-id="15976-136">"Select"</span></span>

### <a name="select"></a><span data-ttu-id="15976-137">「選択」</span><span class="sxs-lookup"><span data-stu-id="15976-137">"Select"</span></span>

<span data-ttu-id="15976-138">「選択」と言った場合はいつでも、何であれ視線入力カーソルでポイントされているものがアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="15976-138">Saying "select" at any time will activate whatever the gaze cursor is pointing at.</span></span> 

><span data-ttu-id="15976-139">注: HoloLens 2 では、"select" という単語を言うことによって、最初に見つめカーソルを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="15976-139">Note: In HoloLens 2, the gaze cursor needs to first be invoked by saying the word "select".</span></span> <span data-ttu-id="15976-140">もう一度「選択」と言うとアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="15976-140">Say, "select" again to activate.</span></span> <span data-ttu-id="15976-141">視線入力カーソルを非表示にするには、手を使ってオブジェクトをエアタップまたはタッチするだけです。</span><span class="sxs-lookup"><span data-stu-id="15976-141">To hide the gaze cursor, simply use your hands -- airtap or touch an object.</span></span> 

### <a name="see-it-say-it"></a><span data-ttu-id="15976-142">見て発音する</span><span class="sxs-lookup"><span data-stu-id="15976-142">See it, say it</span></span>

<span data-ttu-id="15976-143">Windows Mixed Reality では「see it, say it (見て発音する)」音声モデルを採用しています。この場合、**ボタンのラベルは関連付けられている音声コマンドと同じです**。</span><span class="sxs-lookup"><span data-stu-id="15976-143">Windows Mixed Reality has employed a "see it, say it" voice model where **labels on buttons are identical to the associated voice commands**.</span></span> <span data-ttu-id="15976-144">ラベルと音声コマンドの間で不一致がないため、ユーザーはシステムを制御するために何を言うべきかをよりよく理解できます。</span><span class="sxs-lookup"><span data-stu-id="15976-144">Because there isn’t any dissonance between the label and the voice command, users can better understand what to say to control the system.</span></span> <span data-ttu-id="15976-145">これを強化するため、ボタン上でドウェルしている間は、音声対応のボタンを示す **"音声ドウェル ヒント"** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="15976-145">To reinforce this, while dwelling on a button, a **"voice dwell tip"** appears to communicate which buttons are voice enabled.</span></span>


![「見て発音する」の例 1](images/voice-seeitsayit1-640px.jpg)

<span data-ttu-id="15976-147">![「見て発音する」の例 2](images/voice-seeitsayit2-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="15976-147">![See it say it example 2](images/voice-seeitsayit2-640px.jpg)</span></span><br>
<span data-ttu-id="15976-148">*「見て発音する」の例*</span><span class="sxs-lookup"><span data-stu-id="15976-148">*Examples of "see it, say it"*</span></span>

### <a name="voices-strengths"></a><span data-ttu-id="15976-149">音声の長所</span><span class="sxs-lookup"><span data-stu-id="15976-149">Voice's strengths</span></span>

<span data-ttu-id="15976-150">音声入力は、意図を伝える自然な方法です。</span><span class="sxs-lookup"><span data-stu-id="15976-150">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="15976-151">音声は特にインターフェイスの**横断**に適しています。ユーザーがインターフェイスの複数のステップを省略するのに役立つためです (Web ページを見ているときに「戻る」と言えば、ユーザーはアプリの中で上まで行って [戻る] ボタンを押さなくても済みます)。</span><span class="sxs-lookup"><span data-stu-id="15976-151">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at Web page, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="15976-152">この小さな時間の節約は、このエクスペリエンスに対するユーザーの認識に強力な**感情的効果**をもたらすとともに、ユーザーにわずかながら強力な力を与えます。</span><span class="sxs-lookup"><span data-stu-id="15976-152">This small time savings has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="15976-153">音声の使用は、両手がふさがっているときや、**マルチタスク**中にも便利な入力方法です。</span><span class="sxs-lookup"><span data-stu-id="15976-153">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="15976-154">キーボードでの入力が難しいデバイスでは、**音声ディクテーション**が効率的な入力方法となる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="15976-154">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input.</span></span> <span data-ttu-id="15976-155">最後に、視線入力とジェスチャの**精度範囲**が限られている場合、音声がユーザーの唯一の信頼できる入力方法になることもあります。</span><span class="sxs-lookup"><span data-stu-id="15976-155">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, Voice might be a user’s only trusted method input.</span></span>

<span data-ttu-id="15976-156">**音声使用がユーザーにもたらすメリット**</span><span class="sxs-lookup"><span data-stu-id="15976-156">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="15976-157">時間の短縮 - 最終目的をより効率的にします。</span><span class="sxs-lookup"><span data-stu-id="15976-157">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="15976-158">労力の最小化 - タスクをよりスムーズかつ簡単にします。</span><span class="sxs-lookup"><span data-stu-id="15976-158">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="15976-159">認知負荷の軽減 - 直感的かつ簡単で、覚えるのが容易です。</span><span class="sxs-lookup"><span data-stu-id="15976-159">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="15976-160">社会的に受け入れられる - 動作の観点から社会規範に適合するものです。</span><span class="sxs-lookup"><span data-stu-id="15976-160">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="15976-161">日常的 - 音声はすぐに習慣的な動作となることができます。</span><span class="sxs-lookup"><span data-stu-id="15976-161">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="voices-weaknesses"></a><span data-ttu-id="15976-162">音声の短所</span><span class="sxs-lookup"><span data-stu-id="15976-162">Voice's weaknesses</span></span>

<span data-ttu-id="15976-163">音声には短所もいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="15976-163">Voice also has some weaknesses.</span></span> <span data-ttu-id="15976-164">詳細に制御することはその 1 つです。</span><span class="sxs-lookup"><span data-stu-id="15976-164">Fine-grained control is one of them.</span></span> <span data-ttu-id="15976-165">たとえば、ユーザーが「音を大きく」と言っても、どの程度大きくするかは言うことができません。</span><span class="sxs-lookup"><span data-stu-id="15976-165">(for example a user might say "louder," but can’t say how much.</span></span> <span data-ttu-id="15976-166">「少し」は程度の指定が困難です。</span><span class="sxs-lookup"><span data-stu-id="15976-166">"A little" is hard to quantify.</span></span> <span data-ttu-id="15976-167">音声では物の移動や拡大縮小も困難です (音声では詳細に制御することができません)。</span><span class="sxs-lookup"><span data-stu-id="15976-167">Moving or scaling things with voice is also difficult (voice does not offer the granularity of control).</span></span> <span data-ttu-id="15976-168">音声も不完全な場合があります。</span><span class="sxs-lookup"><span data-stu-id="15976-168">Voice can also be imperfect.</span></span> <span data-ttu-id="15976-169">音声システムでコマンドを誤認識したり、コマンドを聞き落としたりすることもあります。</span><span class="sxs-lookup"><span data-stu-id="15976-169">Sometimes a voice system incorrectly hears a command or fails to hear a command.</span></span> <span data-ttu-id="15976-170">このようなエラーからの回復は、すべてのインターフェイスにおける課題です。</span><span class="sxs-lookup"><span data-stu-id="15976-170">Recovering from such errors is a challenge in any interface.</span></span> <span data-ttu-id="15976-171">最後に、音声は、公共の場では社会的に受け入れられない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="15976-171">Lastly, voice may not be socially acceptable in public places.</span></span> <span data-ttu-id="15976-172">ユーザーが言うことができない、または言うべきではない言葉もあります。</span><span class="sxs-lookup"><span data-stu-id="15976-172">There are some things that users can’t or shouldn’t say.</span></span> <span data-ttu-id="15976-173">こうした崖があるので、音声はその得意分野でなら使えるということになります。</span><span class="sxs-lookup"><span data-stu-id="15976-173">These cliffs allow speech to be used for what it is best at.</span></span>

### <a name="voice-feedback-states"></a><span data-ttu-id="15976-174">音声のフィードバックの状態</span><span class="sxs-lookup"><span data-stu-id="15976-174">Voice feedback states</span></span>

<span data-ttu-id="15976-175">音声が適切に適用されると、**ユーザーは自分が何を言えるのかを理解し、**システムがそれを正しく認識した**という明確なフィードバックを得ます。**</span><span class="sxs-lookup"><span data-stu-id="15976-175">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="15976-176">こうした 2 つのシグナルにより、ユーザーは音声をメインの入力として使用することに自信を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="15976-176">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="15976-177">下の図は、音声入力が認識されたときにカーソルに何が発生するか、またそれがユーザーにどのように伝わるかを示す図です。</span><span class="sxs-lookup"><span data-stu-id="15976-177">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>

<span data-ttu-id="15976-178">![カーソルの音声のフィードバック状態](images/voicefeedbackstates.png)</span><span class="sxs-lookup"><span data-stu-id="15976-178">![Voice feedback states for cursor](images/voicefeedbackstates.png)</span></span><br>
<span data-ttu-id="15976-179">*カーソルの音声のフィードバック状態*</span><span class="sxs-lookup"><span data-stu-id="15976-179">*Voice feedback states for cursor*</span></span>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="15976-180">Mixed Reality における「音声」について、ユーザーが知っておくべき重要な事項</span><span class="sxs-lookup"><span data-stu-id="15976-180">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="15976-181">ボタンをターゲットにしながら **「選択」** と言います (ボタンをクリックする場所ならどこでもこれを使用できます)。</span><span class="sxs-lookup"><span data-stu-id="15976-181">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="15976-182">一部のアプリでは、アクションを実行するために**アプリ バー ボタンのラベル名**を言うことができます。</span><span class="sxs-lookup"><span data-stu-id="15976-182">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="15976-183">たとえば、ユーザーは、アプリを見ながらコマンド「削除」を発話することで、アプリを環境から削除することができます (これにより手動でクリックする手間が省けます)。</span><span class="sxs-lookup"><span data-stu-id="15976-183">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="15976-184">**「コルタナさん」と言うと、Cortana のリスニングを開始することができます。**</span><span class="sxs-lookup"><span data-stu-id="15976-184">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="15976-185">質問をしたり (「コルタナさん、エッフェル塔の高さは?」など)、アプリを開くように指示したり (「コルタナさん、Netflix を開いて」など)、スタート メニューを表示するように指示したり (「コルタナさん、ホームに戻って」など) することができます。</span><span class="sxs-lookup"><span data-stu-id="15976-185">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="15976-186">音声に関する一般的な質問と問題</span><span class="sxs-lookup"><span data-stu-id="15976-186">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="15976-187">音声操作の項目。</span><span class="sxs-lookup"><span data-stu-id="15976-187">What can I say?</span></span>
* <span data-ttu-id="15976-188">音声が正しく認識されているかどうかを確認する方法。</span><span class="sxs-lookup"><span data-stu-id="15976-188">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="15976-189">音声コマンドが継続的に誤認識される。</span><span class="sxs-lookup"><span data-stu-id="15976-189">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="15976-190">音声コマンドに対する反応がない。</span><span class="sxs-lookup"><span data-stu-id="15976-190">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="15976-191">音声コマンドを言ったが、間違った動作になる。</span><span class="sxs-lookup"><span data-stu-id="15976-191">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="15976-192">自分の音声のターゲットを特定のアプリやアプリ コマンドにする方法。</span><span class="sxs-lookup"><span data-stu-id="15976-192">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="15976-193">HoloLens のホログラフィック フレームから外れたものに音声でコマンドを出せるか。</span><span class="sxs-lookup"><span data-stu-id="15976-193">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="see-also"></a><span data-ttu-id="15976-194">関連項目</span><span class="sxs-lookup"><span data-stu-id="15976-194">See also</span></span>
* [<span data-ttu-id="15976-195">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="15976-195">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="15976-196">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="15976-196">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
