---
title: 音声入力
description: 音声入力は、HoloLens と Windows Mixed Reality イマーシブ ヘッドセットの中核となる入力です。 コマンド、ディクテーション、Cortana、音声を使用できます。
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv, voice, cortana, speech, input
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829953"
---
# <a name="voice-input"></a><span data-ttu-id="6da69-105">音声入力</span><span class="sxs-lookup"><span data-stu-id="6da69-105">Voice input</span></span>

<span data-ttu-id="6da69-106">音声では、3 つのキー入力での HoloLens の形式の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="6da69-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="6da69-107">ホログラムを使用することがなく直接コマンドできます[ジェスチャ](gestures.md)します。</span><span class="sxs-lookup"><span data-stu-id="6da69-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="6da69-108">単に[視線](gaze.md)ホログラムでと、コマンドを読み上げます。</span><span class="sxs-lookup"><span data-stu-id="6da69-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="6da69-109">音声入力には、ユーザーの意図を通信するために、自然な方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6da69-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="6da69-110">音声はユーザーが 1 つのコマンドを使用して入れ子になったメニューを切り抜けることができるため、複雑なインターフェイスを通過するに特に適してします。</span><span class="sxs-lookup"><span data-stu-id="6da69-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="6da69-111">音声入力が搭載されています、[同じエンジン](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)他のすべてのユニバーサル Windows アプリに音声認識をサポートします。</span><span class="sxs-lookup"><span data-stu-id="6da69-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="6da69-112">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="6da69-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6da69-113"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="6da69-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="6da69-114"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="6da69-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="6da69-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6da69-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="6da69-116"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="6da69-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6da69-117">音声入力</span><span class="sxs-lookup"><span data-stu-id="6da69-117">Voice input</span></span></td>
        <td><span data-ttu-id="6da69-118">✔️</span><span class="sxs-lookup"><span data-stu-id="6da69-118">✔️</span></span></td>
        <td><span data-ttu-id="6da69-119">✔️</span><span class="sxs-lookup"><span data-stu-id="6da69-119">✔️</span></span></td>
        <td><span data-ttu-id="6da69-120">(マイク) を使って ✔️</span><span class="sxs-lookup"><span data-stu-id="6da69-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="6da69-121">"Select"コマンド</span><span class="sxs-lookup"><span data-stu-id="6da69-121">The "select" command</span></span>

<span data-ttu-id="6da69-122">具体的には、アプリに音声のサポートを追加、しなくてもユーザーは、ホログラムを"select"と答えるとするだけでアクティブ化することができます。</span><span class="sxs-lookup"><span data-stu-id="6da69-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="6da69-123">これは、動作は同じ、[エア タップ](gestures.md#air-tap)HoloLens、上の select ボタンを押して、 [HoloLens clicker](hardware-accessories.md#hololens-clicker)トリガーを押したり、 [Windows Mixed Reality アニメーション コント ローラー](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="6da69-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="6da69-124">音が聞こえるされ、"select"を含む確認として表示されるヒントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6da69-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="6da69-125">低電力キーワードの検出アルゴリズムでは"select"が有効になっているため、いつでもあなたの側に手を使用しても、最小限のバッテリ寿命の影響をいつでも記述することができます。</span><span class="sxs-lookup"><span data-stu-id="6da69-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="6da69-126">HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。</span><span class="sxs-lookup"><span data-stu-id="6da69-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="6da69-127">![選択範囲に音声コマンドを使用するには、"select"](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="6da69-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="6da69-128">*選択範囲に音声コマンドを使用するには、"select"*</span><span class="sxs-lookup"><span data-stu-id="6da69-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="6da69-129">[コルタナさん]</span><span class="sxs-lookup"><span data-stu-id="6da69-129">Hey Cortana</span></span>

<span data-ttu-id="6da69-130">コルタナさん」はいつでも、Cortana を起動することも言えます。</span><span class="sxs-lookup"><span data-stu-id="6da69-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="6da69-131">彼女に質問は彼女の続行またはという命令に与えることなど、表示されるまで待機する必要はありません"Hey Cortana、天気とは何ですか"。</span><span class="sxs-lookup"><span data-stu-id="6da69-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="6da69-132">として 1 つの文。</span><span class="sxs-lookup"><span data-stu-id="6da69-132">as a single sentence.</span></span> <span data-ttu-id="6da69-133">Cortana と何ができるかについての詳細については、単にもらいます。</span><span class="sxs-lookup"><span data-stu-id="6da69-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="6da69-134">たとえば「what can Hey Cortana と言ったでしょうか。」</span><span class="sxs-lookup"><span data-stu-id="6da69-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="6da69-135">機能し、推奨されるコマンドの一覧を彼女をプルします。</span><span class="sxs-lookup"><span data-stu-id="6da69-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="6da69-136">Cortana アプリになっている場合は、クリックすることも、**でしょうか。**</span><span class="sxs-lookup"><span data-stu-id="6da69-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="6da69-137">このメニューを取得するサイドバー上のアイコン。</span><span class="sxs-lookup"><span data-stu-id="6da69-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="6da69-138">**HoloLens に固有のコマンド**</span><span class="sxs-lookup"><span data-stu-id="6da69-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="6da69-139">音声操作の項目</span><span class="sxs-lookup"><span data-stu-id="6da69-139">"What can I say?"</span></span>
* <span data-ttu-id="6da69-140">「家に帰る」または"の先頭へ移動"- の代わりに[ブルーム](gestures.md#bloom)に[[スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="6da69-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="6da69-141">"起動<app>"</span><span class="sxs-lookup"><span data-stu-id="6da69-141">"Launch <app>"</span></span>
* <span data-ttu-id="6da69-142">"移動<app>ここで"</span><span class="sxs-lookup"><span data-stu-id="6da69-142">"Move <app> here"</span></span>
* <span data-ttu-id="6da69-143">「画像を撮影する」</span><span class="sxs-lookup"><span data-stu-id="6da69-143">"Take a picture"</span></span>
* <span data-ttu-id="6da69-144">「記録の開始」</span><span class="sxs-lookup"><span data-stu-id="6da69-144">"Start recording"</span></span>
* <span data-ttu-id="6da69-145">[記録を停止する]</span><span class="sxs-lookup"><span data-stu-id="6da69-145">"Stop recording"</span></span>
* <span data-ttu-id="6da69-146">「明るさを」</span><span class="sxs-lookup"><span data-stu-id="6da69-146">"Increase the brightness"</span></span>
* <span data-ttu-id="6da69-147">「明るさを下げる」</span><span class="sxs-lookup"><span data-stu-id="6da69-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="6da69-148">「の音量を上げる」</span><span class="sxs-lookup"><span data-stu-id="6da69-148">"Increase the volume"</span></span>
* <span data-ttu-id="6da69-149">「の音量を下げる」</span><span class="sxs-lookup"><span data-stu-id="6da69-149">"Decrease the volume"</span></span>
* <span data-ttu-id="6da69-150">「ミュート」または「ミュートを解除」</span><span class="sxs-lookup"><span data-stu-id="6da69-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="6da69-151">「デバイスをシャット ダウン」</span><span class="sxs-lookup"><span data-stu-id="6da69-151">"Shut down the device"</span></span>
* <span data-ttu-id="6da69-152">[デバイスを再起動する]</span><span class="sxs-lookup"><span data-stu-id="6da69-152">"Restart the device"</span></span>
* <span data-ttu-id="6da69-153">"スリープ状態に移動</span><span class="sxs-lookup"><span data-stu-id="6da69-153">"Go to sleep"</span></span>
* <span data-ttu-id="6da69-154">「どのような時間は?」</span><span class="sxs-lookup"><span data-stu-id="6da69-154">"What time is it?"</span></span>
* <span data-ttu-id="6da69-155">「どのくらいのバッテリは残っているでしょうか。」</span><span class="sxs-lookup"><span data-stu-id="6da69-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="6da69-156">"呼び出す<contact>"(HoloLens の Skype が必要)</span><span class="sxs-lookup"><span data-stu-id="6da69-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="6da69-157">「認識, に言って」</span><span class="sxs-lookup"><span data-stu-id="6da69-157">"See It, Say It"</span></span>

<span data-ttu-id="6da69-158">HoloLens がも言うことがどのような音声コマンド ボタンにラベル指示がユーザーの音声入力、モデルを「認識,」ということ」を持ちます。</span><span class="sxs-lookup"><span data-stu-id="6da69-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="6da69-159">たとえば、2D アプリを調べるときにユーザーには、世界中で、アプリの位置を調整して、アプリ バーに表示されている「調整」コマンドは、できるとします。</span><span class="sxs-lookup"><span data-stu-id="6da69-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![2D アプリまたはホログラムを見ると、ユーザー、アプリの世界での位置を調整して、アプリ バーに表示されている「調整」コマンドと言いますできます。](images/microphone-600px.png)

<span data-ttu-id="6da69-161">アプリでは、この規則に従う、ときにユーザー簡単に理解できる何を言おうシステムを制御します。</span><span class="sxs-lookup"><span data-stu-id="6da69-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="6da69-162">ボタンに gazing 中に、これを補強、するために、ボタンは、ボイスが有効なし、「押す」ことを話すコマンドが表示される場合、その後話題になる「音声ドウェル」ツールヒントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6da69-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="6da69-163">![表示に言って、ボタンの下にコマンドが表示されます](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="6da69-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="6da69-164">*ボタンの下に表示されるコマンド「に言ってを参照してください」*</span><span class="sxs-lookup"><span data-stu-id="6da69-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="6da69-165">高速ホログラム操作の音声コマンド</span><span class="sxs-lookup"><span data-stu-id="6da69-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="6da69-166">さまざまな音声コマンドにすばやく操作タスクを実行するホログラム gazing 中に指定するとします。</span><span class="sxs-lookup"><span data-stu-id="6da69-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="6da69-167">これらの音声コマンドは、2D アプリだけでなく、世界中に配置した 3D オブジェクトで機能します。</span><span class="sxs-lookup"><span data-stu-id="6da69-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="6da69-168">**ホログラム操作コマンド**</span><span class="sxs-lookup"><span data-stu-id="6da69-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="6da69-169">私が発生します。</span><span class="sxs-lookup"><span data-stu-id="6da69-169">Face me</span></span>
* <span data-ttu-id="6da69-170">大きな |強化</span><span class="sxs-lookup"><span data-stu-id="6da69-170">Bigger | Enhance</span></span>
* <span data-ttu-id="6da69-171">小</span><span class="sxs-lookup"><span data-stu-id="6da69-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="6da69-172">ディクテーション</span><span class="sxs-lookup"><span data-stu-id="6da69-172">Dictation</span></span>

<span data-ttu-id="6da69-173">型指定ではなく[エア タップ](gestures.md#air-tap)、音声認識をアプリにテキストを入力する方が効率的にすることができます。</span><span class="sxs-lookup"><span data-stu-id="6da69-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="6da69-174">入力をユーザーには、少ない労力でこれが大幅に迅速に行えます。</span><span class="sxs-lookup"><span data-stu-id="6da69-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="6da69-175">![音声認識がマイク ボタンを選択して開始します。](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="6da69-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="6da69-176">*音声認識をキーボード上にあるマイク ボタンを選択して開始します。*</span><span class="sxs-lookup"><span data-stu-id="6da69-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="6da69-177">Holographic キーボードがアクティブで、いつでも入力する代わりにディクテーション モードに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="6da69-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="6da69-178">開始するのには、テキスト入力ボックスの横のマイクを選択します。</span><span class="sxs-lookup"><span data-stu-id="6da69-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="6da69-179">通信</span><span class="sxs-lookup"><span data-stu-id="6da69-179">Communication</span></span>

<span data-ttu-id="6da69-180">処理オプションの HoloLens によって提供されるカスタマイズされたオーディオ入力を活用する必要があるアプリケーションは、さまざまなを理解しておく必要[オーディオ ストリーム カテゴリ](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)アプリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6da69-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="6da69-181">これらの 3 つのいくつかの別のストリームのカテゴリと HoloLens では、Windows 10 のサポートを使用して、音声、通信、およびその他に使用できるオーディオのアンビエント環境に合わせたマイクのオーディオの品質を最適化するためにカスタム処理を有効にするにはキャプチャ (つまり"camcorder") のシナリオ。</span><span class="sxs-lookup"><span data-stu-id="6da69-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="6da69-182">AudioCategory_Communications ストリーム カテゴリの呼び出しの品質とナレーションのシナリオ用にカスタマイズされた、ユーザーの声の 16 kHz 24 ビットのモノラル オーディオ ストリームをクライアントに提供</span><span class="sxs-lookup"><span data-stu-id="6da69-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="6da69-183">AudioCategory_Speech ストリーム カテゴリでは、HoloLens (Windows) の音声認識エンジン用にカスタマイズされた、ユーザーの声の 16 kHz 24 ビット mono ストリームが提供されます。</span><span class="sxs-lookup"><span data-stu-id="6da69-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="6da69-184">このカテゴリは、必要な場合は、サード パーティの音声認識エンジンによって使用できます。</span><span class="sxs-lookup"><span data-stu-id="6da69-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="6da69-185">AudioCategory_Other ストリーム カテゴリでは、オーディオ録音のアンビエント環境用にカスタマイズされた、48 kHz 24 ビットのステレオ オーディオ ストリームをクライアントに提供します。</span><span class="sxs-lookup"><span data-stu-id="6da69-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="6da69-186">このオーディオのすべての処理は、ハードウェア アクセラレーション機能は、ドレイン、HoloLens CPU 上で同じ処理が行った場合よりも大幅 power つまりです。</span><span class="sxs-lookup"><span data-stu-id="6da69-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="6da69-187">その他のオーディオの入力をシステムのバッテリ寿命を最大化し、組み込みの利用、CPU 上で処理を実行しないように、オーディオ入力の処理をオフロードします。</span><span class="sxs-lookup"><span data-stu-id="6da69-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="6da69-188">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6da69-188">Troubleshooting</span></span>

<span data-ttu-id="6da69-189">コルタナさん」、"select"を使用して問題が生じる場合は、ノイズ、または大きな声で話すことによって、ソースから離れた場所にすると、静か空間に移動してみてください。</span><span class="sxs-lookup"><span data-stu-id="6da69-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="6da69-190">現時点では、HoloLens のすべての音声認識はチューニングし、米国英語を母国に特に最適化します。</span><span class="sxs-lookup"><span data-stu-id="6da69-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="6da69-191">Windows Mixed Reality Developer Edition リリース 2017 では、オーディオ エンドポイント管理のロジックが数列 (無限) 後、最初のッドマウント接続後に PC のデスクトップ アウトされ、ログ記録します。</span><span class="sxs-lookup"><span data-stu-id="6da69-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="6da69-192">その最初の兆候アウト/経由 WMR OOBE 後のイベントで、前に、ユーザーから音声の入っていない切り替え、システムが、ッドマウントを最初に接続する前に設定する方法に応じて音声の入っていないまでさまざまなのオーディオ機能問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6da69-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="6da69-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="6da69-193">See also</span></span>
* [<span data-ttu-id="6da69-194">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="6da69-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="6da69-195">Unity の音声入力</span><span class="sxs-lookup"><span data-stu-id="6da69-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="6da69-196">MR 入力 212:音声</span><span class="sxs-lookup"><span data-stu-id="6da69-196">MR Input 212: Voice</span></span>](holograms-212.md)
