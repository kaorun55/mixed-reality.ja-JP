---
title: 音声入力
description: 音声入力は、HoloLens および Windows Mixed Reality イマーシブヘッドセットの中核となる入力です。 音声は、コマンド、ディクテーション、Cortana などに使用できます。
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv、音声、cortana、音声、入力
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829953"
---
# <a name="voice-input"></a><span data-ttu-id="8770c-105">音声入力</span><span class="sxs-lookup"><span data-stu-id="8770c-105">Voice input</span></span>

<span data-ttu-id="8770c-106">Voice は、HoloLens での3つの主要な入力形式の1つです。</span><span class="sxs-lookup"><span data-stu-id="8770c-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="8770c-107">これにより、[ジェスチャ](gestures.md)を使用せずに、ホログラムに直接コマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="8770c-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="8770c-108">ホログラムを[見つめ](gaze.md)て、コマンドを話すだけです。</span><span class="sxs-lookup"><span data-stu-id="8770c-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="8770c-109">音声入力は、意図したとおりに通信するための自然な方法である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8770c-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="8770c-110">複雑なインターフェイスを走査するのは、ユーザーが1つのコマンドで入れ子になったメニューを使用できるようにするため、音声は特に便利です。</span><span class="sxs-lookup"><span data-stu-id="8770c-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="8770c-111">音声入力は、他のすべてのユニバーサル Windows アプリで音声をサポートするのと[同じエンジン](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)によって機能します。</span><span class="sxs-lookup"><span data-stu-id="8770c-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="8770c-112">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="8770c-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8770c-113"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="8770c-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="8770c-114"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8770c-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="8770c-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="8770c-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="8770c-116"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="8770c-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8770c-117">音声入力</span><span class="sxs-lookup"><span data-stu-id="8770c-117">Voice input</span></span></td>
        <td><span data-ttu-id="8770c-118">✔️</span><span class="sxs-lookup"><span data-stu-id="8770c-118">✔️</span></span></td>
        <td><span data-ttu-id="8770c-119">✔️</span><span class="sxs-lookup"><span data-stu-id="8770c-119">✔️</span></span></td>
        <td><span data-ttu-id="8770c-120">✔️ (マイクを使用)</span><span class="sxs-lookup"><span data-stu-id="8770c-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="8770c-121">"Select" コマンド</span><span class="sxs-lookup"><span data-stu-id="8770c-121">The "select" command</span></span>

<span data-ttu-id="8770c-122">特に音声サポートをアプリに追加しなくても、ユーザーは "select" と言って、ホログラムをアクティブにすることができます。</span><span class="sxs-lookup"><span data-stu-id="8770c-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="8770c-123">これは、HoloLens での[エアタップ](gestures.md#air-tap)と同じように動作します。また、 [hololens clicker](hardware-accessories.md#hololens-clicker)の [選択] ボタンを押すか、 [Windows Mixed Reality モーションコントローラー](motion-controllers.md)でトリガーを押します。</span><span class="sxs-lookup"><span data-stu-id="8770c-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="8770c-124">サウンドが聞こえ、[選択] というヒントが確認として表示されます。</span><span class="sxs-lookup"><span data-stu-id="8770c-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="8770c-125">"Select" は、低電力キーワード検出アルゴリズムによって有効にされているため、ユーザー側でも、バッテリ寿命の影響を最小限に抑えていつでもいつでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="8770c-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="8770c-126">HoloLens 2 に固有のその他のガイダンスは[近日対応予定](index.md#news-and-notes)です。</span><span class="sxs-lookup"><span data-stu-id="8770c-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="8770c-127">![選択に音声コマンドを使用するには、[選択] を言います。](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="8770c-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="8770c-128">*選択に音声コマンドを使用するには、[選択] を言います。*</span><span class="sxs-lookup"><span data-stu-id="8770c-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="8770c-129">[コルタナさん]</span><span class="sxs-lookup"><span data-stu-id="8770c-129">Hey Cortana</span></span>

<span data-ttu-id="8770c-130">また、いつでも cortana を立ち上げることができます。</span><span class="sxs-lookup"><span data-stu-id="8770c-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="8770c-131">自分の質問を続けたり、指示を与えたりすることができるようになるまで待つ必要はありません。たとえば、「Cortana はどうでしょうか。」と言ってください。</span><span class="sxs-lookup"><span data-stu-id="8770c-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="8770c-132">1つの文として。</span><span class="sxs-lookup"><span data-stu-id="8770c-132">as a single sentence.</span></span> <span data-ttu-id="8770c-133">Cortana とその対処方法の詳細については、</span><span class="sxs-lookup"><span data-stu-id="8770c-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="8770c-134">「Cortana が何を言うことができるか」と言ってください。</span><span class="sxs-lookup"><span data-stu-id="8770c-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="8770c-135">次に、作業と推奨されるコマンドの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="8770c-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="8770c-136">既に Cortana アプリを使用している場合は、[?] をクリックすることもでき**ます。**</span><span class="sxs-lookup"><span data-stu-id="8770c-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="8770c-137">同じメニューをプルするためのサイドバーのアイコン。</span><span class="sxs-lookup"><span data-stu-id="8770c-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="8770c-138">**HoloLens 固有のコマンド**</span><span class="sxs-lookup"><span data-stu-id="8770c-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="8770c-139">音声操作の項目</span><span class="sxs-lookup"><span data-stu-id="8770c-139">"What can I say?"</span></span>
* <span data-ttu-id="8770c-140">[[スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)を表示するには、[ブルーム](gestures.md#bloom)の代わりに [ホーム] または [スタートに移動] を実行します。</span><span class="sxs-lookup"><span data-stu-id="8770c-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="8770c-141">"起動<app>"</span><span class="sxs-lookup"><span data-stu-id="8770c-141">"Launch <app>"</span></span>
* <span data-ttu-id="8770c-142">"ここ<app>に移動"</span><span class="sxs-lookup"><span data-stu-id="8770c-142">"Move <app> here"</span></span>
* <span data-ttu-id="8770c-143">"写真を撮る"</span><span class="sxs-lookup"><span data-stu-id="8770c-143">"Take a picture"</span></span>
* <span data-ttu-id="8770c-144">"記録の開始"</span><span class="sxs-lookup"><span data-stu-id="8770c-144">"Start recording"</span></span>
* <span data-ttu-id="8770c-145">"記録の停止"</span><span class="sxs-lookup"><span data-stu-id="8770c-145">"Stop recording"</span></span>
* <span data-ttu-id="8770c-146">「明るさを上げる」</span><span class="sxs-lookup"><span data-stu-id="8770c-146">"Increase the brightness"</span></span>
* <span data-ttu-id="8770c-147">「明るさを下げる」</span><span class="sxs-lookup"><span data-stu-id="8770c-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="8770c-148">"ボリュームを増やす"</span><span class="sxs-lookup"><span data-stu-id="8770c-148">"Increase the volume"</span></span>
* <span data-ttu-id="8770c-149">"音量を下げる"</span><span class="sxs-lookup"><span data-stu-id="8770c-149">"Decrease the volume"</span></span>
* <span data-ttu-id="8770c-150">"ミュート" または "ミュート解除"</span><span class="sxs-lookup"><span data-stu-id="8770c-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="8770c-151">"デバイスをシャットダウンする"</span><span class="sxs-lookup"><span data-stu-id="8770c-151">"Shut down the device"</span></span>
* <span data-ttu-id="8770c-152">"デバイスを再起動する"</span><span class="sxs-lookup"><span data-stu-id="8770c-152">"Restart the device"</span></span>
* <span data-ttu-id="8770c-153">"スリープ状態に移行"</span><span class="sxs-lookup"><span data-stu-id="8770c-153">"Go to sleep"</span></span>
* <span data-ttu-id="8770c-154">"どのような時間がかかりますか。"</span><span class="sxs-lookup"><span data-stu-id="8770c-154">"What time is it?"</span></span>
* <span data-ttu-id="8770c-155">「どのくらいのバッテリが残っていますか?」</span><span class="sxs-lookup"><span data-stu-id="8770c-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="8770c-156">"通話<contact>" (Skype for HoloLens が必要)</span><span class="sxs-lookup"><span data-stu-id="8770c-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="8770c-157">「言ってください。</span><span class="sxs-lookup"><span data-stu-id="8770c-157">"See It, Say It"</span></span>

<span data-ttu-id="8770c-158">HoloLens には、音声入力用の "it it はこれを見る" モデルがあります。ボタンのラベルはユーザーに対して、どのような音声コマンドを伝えることもできます。</span><span class="sxs-lookup"><span data-stu-id="8770c-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="8770c-159">たとえば、2D アプリを見ると、ユーザーはアプリバーに表示される "調整" コマンドを使用して、世界中のアプリの位置を調整することができます。</span><span class="sxs-lookup"><span data-stu-id="8770c-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![2D アプリまたはホログラムを見ると、ユーザーはアプリバーに表示される "調整" コマンドを使用して、世界中のアプリの位置を調整することができます。](images/microphone-600px.png)

<span data-ttu-id="8770c-161">アプリがこの規則に従うと、ユーザーはシステムを制御する方法を簡単に理解できます。</span><span class="sxs-lookup"><span data-stu-id="8770c-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="8770c-162">これを補強するために、ボタンをクリックすると、ボタンが音声に対応している場合は1秒後に表示される "voice 熟考" というツールヒントが表示され、"press" を押すコマンドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8770c-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="8770c-163">![ボタンの下にコマンドが表示されるとします。](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="8770c-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="8770c-164">*「これを見ると、ボタンの下にコマンドが表示される*</span><span class="sxs-lookup"><span data-stu-id="8770c-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="8770c-165">迅速なホログラム操作のための音声コマンド</span><span class="sxs-lookup"><span data-stu-id="8770c-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="8770c-166">また、ホログラムを使用して操作を簡単に実行できる音声コマンドも多数あります。</span><span class="sxs-lookup"><span data-stu-id="8770c-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="8770c-167">これらの音声コマンドは、世界中に配置した3D オブジェクトだけでなく、2D アプリでも機能します。</span><span class="sxs-lookup"><span data-stu-id="8770c-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="8770c-168">**ホログラム操作コマンド**</span><span class="sxs-lookup"><span data-stu-id="8770c-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="8770c-169">顔</span><span class="sxs-lookup"><span data-stu-id="8770c-169">Face me</span></span>
* <span data-ttu-id="8770c-170">大規模 |用</span><span class="sxs-lookup"><span data-stu-id="8770c-170">Bigger | Enhance</span></span>
* <span data-ttu-id="8770c-171">小</span><span class="sxs-lookup"><span data-stu-id="8770c-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="8770c-172">ディクテーション</span><span class="sxs-lookup"><span data-stu-id="8770c-172">Dictation</span></span>

<span data-ttu-id="8770c-173">音声ディクテーションで入力するのでは[なく、アプリケーション](gestures.md#air-tap)にテキストを入力する方が効率的です。</span><span class="sxs-lookup"><span data-stu-id="8770c-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="8770c-174">これにより、ユーザーの負担を軽減しながら、入力を大幅に高速化できます。</span><span class="sxs-lookup"><span data-stu-id="8770c-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="8770c-175">![音声ディクテーションを開始するには、マイクボタンを選択します。](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="8770c-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="8770c-176">*音声ディクテーションを開始するには、キーボードのマイクボタンを選択します。*</span><span class="sxs-lookup"><span data-stu-id="8770c-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="8770c-177">Holographic キーボードがアクティブなときはいつでも、入力せずにディクテーションモードに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="8770c-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="8770c-178">開始するには、テキスト入力ボックスの横にあるマイクを選択します。</span><span class="sxs-lookup"><span data-stu-id="8770c-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="8770c-179">通信</span><span class="sxs-lookup"><span data-stu-id="8770c-179">Communication</span></span>

<span data-ttu-id="8770c-180">HoloLens が提供するカスタマイズされたオーディオ入力処理オプションを利用する必要があるアプリケーションでは、アプリが使用できるさまざまな[オーディオストリームのカテゴリ](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)を理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="8770c-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="8770c-181">Windows 10 では、さまざまなストリームカテゴリがサポートされています。 HoloLens では、これらのうちの3つを使用して、音声、通信、およびアンビエント環境のオーディオ用に調整されたマイクオーディオの品質を最適化するカスタム処理を可能にします。キャプチャ ("カムコーダー" など) シナリオ。</span><span class="sxs-lookup"><span data-stu-id="8770c-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="8770c-182">AudioCategory_Communications stream カテゴリは、通話の品質とナレーションのシナリオに合わせてカスタマイズされ、クライアントにユーザーの声の 16kHz 24bit mono オーディオストリームを提供します。</span><span class="sxs-lookup"><span data-stu-id="8770c-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="8770c-183">AudioCategory_Speech stream カテゴリは、HoloLens (Windows) 音声エンジン用にカスタマイズされており、ユーザーの声の 16kHz 24bit mono ストリームを提供します。</span><span class="sxs-lookup"><span data-stu-id="8770c-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="8770c-184">このカテゴリは、サードパーティの音声エンジンで必要に応じて使用できます。</span><span class="sxs-lookup"><span data-stu-id="8770c-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="8770c-185">AudioCategory_Other stream カテゴリはアンビエント環境オーディオ記録用にカスタマイズされており、クライアントには 48 Khz 24 ビットのステレオオーディオストリームが用意されています。</span><span class="sxs-lookup"><span data-stu-id="8770c-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="8770c-186">このようなオーディオ処理はすべてハードウェアアクセラレータです。これは、HoloLens CPU で同じ処理が行われた場合と比べて、機能の電力消費が多くなることを意味します。</span><span class="sxs-lookup"><span data-stu-id="8770c-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="8770c-187">システムのバッテリ寿命を最大化し、組み込みのオフロードオーディオ入力処理を活用するために、CPU で他のオーディオ入力処理を実行しないようにします。</span><span class="sxs-lookup"><span data-stu-id="8770c-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="8770c-188">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="8770c-188">Troubleshooting</span></span>

<span data-ttu-id="8770c-189">"Select" と "Cortana" を使用して問題が発生している場合は、静かな領域に移動するか、ノイズの発生源から離れるか、音を大きくしてみてください。</span><span class="sxs-lookup"><span data-stu-id="8770c-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="8770c-190">現時点では、HoloLens の音声認識はすべて米国英語のネイティブスピーカーに対して調整および最適化されています。</span><span class="sxs-lookup"><span data-stu-id="8770c-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="8770c-191">Windows Mixed Reality Developer Edition release 2017 では、オーディオエンドポイント管理ロジックは、最初の HMD 接続の後、いったんログアウトして PC デスクトップに戻すと、正常に機能します。</span><span class="sxs-lookup"><span data-stu-id="8770c-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="8770c-192">ユーザーは、WMR OOBE を通過した後に初めてサインアウト/イベントが発生する前に、HMD を初めて接続する前にシステムがどのように設定されているかによって、オーディオの切り替えなしのさまざまなオーディオ機能の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8770c-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8770c-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="8770c-193">See also</span></span>
* [<span data-ttu-id="8770c-194">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="8770c-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="8770c-195">Unity の音声入力</span><span class="sxs-lookup"><span data-stu-id="8770c-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="8770c-196">MR 入力 212:音声</span><span class="sxs-lookup"><span data-stu-id="8770c-196">MR Input 212: Voice</span></span>](holograms-212.md)
