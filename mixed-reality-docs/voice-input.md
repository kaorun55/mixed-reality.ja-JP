---
title: 音声入力
description: 音声入力は、HoloLens および Windows Mixed Reality イマーシブヘッドセットの中核となる入力です。 音声は、コマンド、ディクテーション、Cortana などに使用できます。
author: Hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv、音声、cortana、音声、入力
ms.openlocfilehash: f2ae18d4063c7c4a63346a1202cacaa7fbbdf959
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723191"
---
# <a name="voice-input"></a><span data-ttu-id="1a09b-105">音声入力</span><span class="sxs-lookup"><span data-stu-id="1a09b-105">Voice input</span></span>

![音声入力](images/UX/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="1a09b-107">音声は、HoloLens の主な入力形式の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="1a09b-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="1a09b-108">[ハンドジェスチャ](gaze-and-commit.md#composite-gestures)を使用しなくても、ホログラムに直接コマンドを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="1a09b-109">音声入力は、意図を伝える自然な方法として使用できます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="1a09b-110">複雑なインターフェイスを走査するのは、ユーザーが1つのコマンドで入れ子になったメニューを使用できるため、音声は特に便利です。</span><span class="sxs-lookup"><span data-stu-id="1a09b-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="1a09b-111">音声入力は、他のすべての_ユニバーサル Windows アプリ_で音声をサポートするのと[同じエンジン](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)によって機能します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other _Universal Windows Apps_.</span></span> <span data-ttu-id="1a09b-112">HoloLens では、音声認識は常に [設定] で構成された Windows 表示言語で機能します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-112">On HoloLens, speech recognition will always function in the Windows display language configured in Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="1a09b-113">音声と宝石</span><span class="sxs-lookup"><span data-stu-id="1a09b-113">Voice and gaze</span></span>

<span data-ttu-id="1a09b-114">音声コマンド (ヘッドまたはアイ) を使用する場合は、通常、ターゲットメカニズムとして、カーソルを使用するか (select)、または対象のアプリケーションにコマンドを暗黙的にチャネル化するかを使用します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-114">When using voice commands, (head or eye) gaze is typically used as the targeting mechanism, whether with a cursor ("select") or to implicitly channel your command to an application that you are looking at.</span></span> <span data-ttu-id="1a09b-115">このため、どのような場合でも、そのカーソルを表示する必要がない場合があります _(「参照してください」と言います)_ 。</span><span class="sxs-lookup"><span data-stu-id="1a09b-115">For this, it may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="1a09b-116">もちろん、一部の音声コマンドでは、"start to start" や "Cortana のこんにちは" など、ターゲットがまったく必要ありません。</span><span class="sxs-lookup"><span data-stu-id="1a09b-116">Of course, some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="1a09b-117">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="1a09b-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1a09b-118"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="1a09b-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="1a09b-119"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="1a09b-119"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="1a09b-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="1a09b-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="1a09b-121"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="1a09b-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1a09b-122">音声入力</span><span class="sxs-lookup"><span data-stu-id="1a09b-122">Voice input</span></span></td>
        <td><span data-ttu-id="1a09b-123">✔️</span><span class="sxs-lookup"><span data-stu-id="1a09b-123">✔️</span></span></td>
        <td><span data-ttu-id="1a09b-124">✔️</span><span class="sxs-lookup"><span data-stu-id="1a09b-124">✔️</span></span></td>
        <td><span data-ttu-id="1a09b-125">✔️ (マイクを使用)</span><span class="sxs-lookup"><span data-stu-id="1a09b-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="1a09b-126">"Select" コマンド</span><span class="sxs-lookup"><span data-stu-id="1a09b-126">The "select" command</span></span>

<span data-ttu-id="1a09b-127">**HoloLens (第 1 世代)**</span><span class="sxs-lookup"><span data-stu-id="1a09b-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="1a09b-128">特に音声サポートをアプリに追加しなくても、ユーザーはシステム音声コマンド "select" を指定するだけで、ホログラムをアクティブにすることができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="1a09b-129">これは、HoloLens での[エアタップ](gaze-and-commit.md#composite-gestures)と同じように動作します。また、 [hololens clicker](hardware-accessories.md#hololens-clicker)の [選択] ボタンを押すか、 [Windows Mixed Reality モーションコントローラー](motion-controllers.md)でトリガーを押します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="1a09b-130">サウンドが聞こえ、[選択] というヒントが確認として表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-130">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="1a09b-131">"Select" は、低電力キーワード検出アルゴリズムによって有効にされているため、ユーザー側でも、バッテリ寿命の影響を最小限に抑えていつでもいつでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-131">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="1a09b-132">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="1a09b-132">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="1a09b-133">HoloLens 2 で "選択" 音声コマンドを使用するには、まず、ポインターとして使用するために、最初に見つめカーソルを表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a09b-133">In order to use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="1a09b-134">これを起動するためのコマンドは覚えやすいものです。 "select" と言うだけです。</span><span class="sxs-lookup"><span data-stu-id="1a09b-134">The command to bring it up is easy to remember -- just say, "select".</span></span><br><br>
        <span data-ttu-id="1a09b-135">モードを終了するには、空中にタップするか、指でボタンに近づくか、またはシステムジェスチャを使用して、もう一度両手を使用します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-135">To exit the mode, simply use your hands again, either by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br>
        <span data-ttu-id="1a09b-136">*イメージ: 音声コマンドを選択に使用するには、[選択] を言います。*</span><span class="sxs-lookup"><span data-stu-id="1a09b-136">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![ユーザーは、[選択] を選択して、音声コマンドを選択に使用できます。](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a><span data-ttu-id="1a09b-138">[コルタナさん]</span><span class="sxs-lookup"><span data-stu-id="1a09b-138">Hey Cortana</span></span>

<span data-ttu-id="1a09b-139">また、いつでも cortana を立ち上げることができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-139">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="1a09b-140">自分の質問を続けたり、指示を出したりすることができるようになるまで待つ必要はありません。たとえば、「Cortana について言っていますか?」と言います。</span><span class="sxs-lookup"><span data-stu-id="1a09b-140">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="1a09b-141">1つの文として。</span><span class="sxs-lookup"><span data-stu-id="1a09b-141">as a single sentence.</span></span> <span data-ttu-id="1a09b-142">Cortana とその対処方法の詳細については、</span><span class="sxs-lookup"><span data-stu-id="1a09b-142">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="1a09b-143">「Cortana とはどういうことですか。」と言います。</span><span class="sxs-lookup"><span data-stu-id="1a09b-143">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="1a09b-144">次に、作業と推奨されるコマンドの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-144">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="1a09b-145">既に Cortana アプリを使用している場合は、[?] をクリックすることもでき**ます。**</span><span class="sxs-lookup"><span data-stu-id="1a09b-145">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="1a09b-146">同じメニューをプルするためのサイドバーのアイコン。</span><span class="sxs-lookup"><span data-stu-id="1a09b-146">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="1a09b-147">**HoloLens 固有のコマンド**</span><span class="sxs-lookup"><span data-stu-id="1a09b-147">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="1a09b-148">音声操作の項目</span><span class="sxs-lookup"><span data-stu-id="1a09b-148">"What can I say?"</span></span>
* <span data-ttu-id="1a09b-149">[ブルーム](system-gesture.md#bloom)の代わりに [スタート] メニューから [スタート][メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)に移動する</span><span class="sxs-lookup"><span data-stu-id="1a09b-149">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="1a09b-150">"起動 <app>"</span><span class="sxs-lookup"><span data-stu-id="1a09b-150">"Launch <app>"</span></span>
* <span data-ttu-id="1a09b-151">"ここに移動 <app></span><span class="sxs-lookup"><span data-stu-id="1a09b-151">"Move <app> here"</span></span>
* <span data-ttu-id="1a09b-152">"写真を撮る"</span><span class="sxs-lookup"><span data-stu-id="1a09b-152">"Take a picture"</span></span>
* <span data-ttu-id="1a09b-153">"記録の開始"</span><span class="sxs-lookup"><span data-stu-id="1a09b-153">"Start recording"</span></span>
* <span data-ttu-id="1a09b-154">"記録の停止"</span><span class="sxs-lookup"><span data-stu-id="1a09b-154">"Stop recording"</span></span>
* <span data-ttu-id="1a09b-155">「明るさを上げる」</span><span class="sxs-lookup"><span data-stu-id="1a09b-155">"Increase the brightness"</span></span>
* <span data-ttu-id="1a09b-156">「明るさを下げる」</span><span class="sxs-lookup"><span data-stu-id="1a09b-156">"Decrease the brightness"</span></span>
* <span data-ttu-id="1a09b-157">"ボリュームを増やす"</span><span class="sxs-lookup"><span data-stu-id="1a09b-157">"Increase the volume"</span></span>
* <span data-ttu-id="1a09b-158">"音量を下げる"</span><span class="sxs-lookup"><span data-stu-id="1a09b-158">"Decrease the volume"</span></span>
* <span data-ttu-id="1a09b-159">"ミュート" または "ミュート解除"</span><span class="sxs-lookup"><span data-stu-id="1a09b-159">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="1a09b-160">"デバイスをシャットダウンする"</span><span class="sxs-lookup"><span data-stu-id="1a09b-160">"Shut down the device"</span></span>
* <span data-ttu-id="1a09b-161">"デバイスを再起動する"</span><span class="sxs-lookup"><span data-stu-id="1a09b-161">"Restart the device"</span></span>
* <span data-ttu-id="1a09b-162">"スリープ状態に移行"</span><span class="sxs-lookup"><span data-stu-id="1a09b-162">"Go to sleep"</span></span>
* <span data-ttu-id="1a09b-163">"どのような時間がかかりますか。"</span><span class="sxs-lookup"><span data-stu-id="1a09b-163">"What time is it?"</span></span>
* <span data-ttu-id="1a09b-164">「どのくらいのバッテリが残っていますか?」</span><span class="sxs-lookup"><span data-stu-id="1a09b-164">"How much battery do I have left?"</span></span>



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="1a09b-165">「言ってください。</span><span class="sxs-lookup"><span data-stu-id="1a09b-165">"See It, Say It"</span></span><br>
        <span data-ttu-id="1a09b-166">HoloLens には、音声入力用の "it it はこれを見る" モデルがあります。ボタンのラベルはユーザーに対して、どのような音声コマンドを伝えることもできます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-166">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="1a09b-167">たとえば、HoloLens (第1世代) のアプリウィンドウを見ると、ユーザーはアプリバーに表示される "調整" コマンドを使用して、世界中のアプリの位置を調整することができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-167">For example, when looking at an app window in HoloLens (1st gen), a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="1a09b-168">*イメージ: ユーザーはアプリバーに表示される "調整" コマンドを使用してアプリの位置を調整できます。*</span><span class="sxs-lookup"><span data-stu-id="1a09b-168">*Image: A user can say the "Adjust" command which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="1a09b-169">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="1a09b-169">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="1a09b-170">アプリウィンドウまたはホログラムを見ると、ユーザーはアプリバーに表示される "調整" コマンドを使用して、世界中のアプリの位置を調整](images/microphone-600px.png) ことができ ![</span><span class="sxs-lookup"><span data-stu-id="1a09b-170">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        <span data-ttu-id="1a09b-171">アプリがこの規則に従うと、ユーザーはシステムを制御する方法を簡単に理解できます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-171">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="1a09b-172">これを補足するために、HoloLens のボタン (第1世代) で、"音声熟考" というツールヒントが表示されるようになりました。ボタンの音声が有効になっている場合は、2回目の後に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-172">To reinforce this, while gazing at a button in HoloLens (1st gen), you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="1a09b-173">HoloLens 2 の音声ツールヒントを表示するには、"選択" または "どのように言ってください" (画像を参照) と言って、音声カーソルを表示します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-173">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="1a09b-174">*イメージ: ボタンの下にコマンドが表示されます。*</span><span class="sxs-lookup"><span data-stu-id="1a09b-174">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![ボタンの下にコマンドが表示されるとします。](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="1a09b-176">迅速なホログラム操作のための音声コマンド</span><span class="sxs-lookup"><span data-stu-id="1a09b-176">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="1a09b-177">ホログラムを使用して操作を簡単に実行できるように、音声コマンドがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="1a09b-177">There are a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="1a09b-178">これらの音声コマンドは、アプリウィンドウだけでなく、世界中に配置した3D オブジェクトでも動作します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-178">These voice commands work on app windows as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="1a09b-179">**ホログラム操作コマンド**</span><span class="sxs-lookup"><span data-stu-id="1a09b-179">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="1a09b-180">顔</span><span class="sxs-lookup"><span data-stu-id="1a09b-180">Face me</span></span>
* <span data-ttu-id="1a09b-181">大規模 |用</span><span class="sxs-lookup"><span data-stu-id="1a09b-181">Bigger | Enhance</span></span>
* <span data-ttu-id="1a09b-182">小</span><span class="sxs-lookup"><span data-stu-id="1a09b-182">Smaller</span></span>

<span data-ttu-id="1a09b-183">HoloLens 2 では、参照している内容についてのコンテキスト情報を暗黙的に提供する、視線との組み合わせでより自然な対話を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-183">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="1a09b-184">たとえば、ホログラムを見て "put _this_" と言い、どこに配置するかを見て、「_ここでは_」と言うことができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-184">For example, you could simply look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="1a09b-185">または、複雑なコンピューター上の holographic の部分を見て、「_これ_に関する詳細情報を提供する」と言います。</span><span class="sxs-lookup"><span data-stu-id="1a09b-185">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>



## <a name="discovering-voice-commands"></a><span data-ttu-id="1a09b-186">音声コマンドの検出</span><span class="sxs-lookup"><span data-stu-id="1a09b-186">Discovering voice commands</span></span>

<span data-ttu-id="1a09b-187">上記の高速操作のコマンドのように、一部のコマンドは非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-187">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="1a09b-188">使用できるコマンドの詳細については、オブジェクトを見つめ、「どうしたら言いますか」と言うことができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-188">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="1a09b-189">使用可能なコマンドの一覧がポップアップ表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-189">A list of possible commands pops up.</span></span> <span data-ttu-id="1a09b-190">また、頭を見つめたカーソルを使用して、前の各ボタンの音声ツールヒントを見たり、表示したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-190">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="1a09b-191">完全な一覧が必要な場合は、いつでも [すべてのコマンドを表示] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-191">If you want a complete list, just say, "Show all commands" anytime.</span></span> 


## <a name="dictation"></a><span data-ttu-id="1a09b-192">ディクテーション</span><span class="sxs-lookup"><span data-stu-id="1a09b-192">Dictation</span></span>

<span data-ttu-id="1a09b-193">音声ディクテーションで入力[するのではなく、アプリケーション](gaze-and-commit.md#composite-gestures)にテキストを入力する方が効率的です。</span><span class="sxs-lookup"><span data-stu-id="1a09b-193">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="1a09b-194">これにより、ユーザーの負担を軽減しながら、入力を大幅に高速化できます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-194">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="1a09b-195">音声ディクテーションを開始 ![には、マイクボタンを選択し](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="1a09b-195">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="1a09b-196">*音声ディクテーションを開始するには、キーボードのマイクボタンを選択します。*</span><span class="sxs-lookup"><span data-stu-id="1a09b-196">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="1a09b-197">Holographic キーボードがアクティブなときはいつでも、入力せずにディクテーションモードに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-197">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="1a09b-198">開始するには、テキスト入力ボックスの横にあるマイクを選択します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-198">Select the microphone on the side of the text input box to get started.</span></span>


## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="1a09b-199">音声コマンドをアプリに追加する</span><span class="sxs-lookup"><span data-stu-id="1a09b-199">Adding voice commands to your app</span></span>

<span data-ttu-id="1a09b-200">構築するすべてのエクスペリエンスに対して、音声コマンドを加えることをご検討ください。</span><span class="sxs-lookup"><span data-stu-id="1a09b-200">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="1a09b-201">音声は、システムとアプリを制御するための強力かつ便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="1a09b-201">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="1a09b-202">ユーザーはさまざまな方言やアクセントで話すので、音声キーワードの適切な選択によって、ユーザーのコマンドが明確に解釈されるようになります。</span><span class="sxs-lookup"><span data-stu-id="1a09b-202">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="1a09b-203">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="1a09b-203">Best practices</span></span>

<span data-ttu-id="1a09b-204">スムーズな音声認識に役立ついくつかのプラクティスを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-204">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="1a09b-205">**簡潔なコマンドを使用する** - 可能なら 2 音節以上から成るキーワードを選択します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-205">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="1a09b-206">1 音節の単語は、アクセントが異なる人が読み上げると、別の母音が使用されやすくなります。</span><span class="sxs-lookup"><span data-stu-id="1a09b-206">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="1a09b-207">例: "ビデオの再生" は、"現在選択されているビデオを再生する" よりも優れています。</span><span class="sxs-lookup"><span data-stu-id="1a09b-207">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="1a09b-208">**単純な語彙を使用する**-例: "show プラカード" よりも "メモの表示" が適しています。</span><span class="sxs-lookup"><span data-stu-id="1a09b-208">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="1a09b-209">**コマンドが非破壊的であること** - 音声認識コマンドによって実行される可能性のあるすべての操作が非破壊的であり、ユーザーの近くで話している別の人によって誤ってコマンドがトリガーされた場合でも簡単に元に戻せることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="1a09b-209">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="1a09b-210">**発音が似ているコマンドを避ける** - 発音がよく似ている音声認識コマンドを複数登録しないようにします。</span><span class="sxs-lookup"><span data-stu-id="1a09b-210">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="1a09b-211">例: "more Show" と "Show store" は、よく似た発音です。</span><span class="sxs-lookup"><span data-stu-id="1a09b-211">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="1a09b-212">**使用していない場合、アプリの登録を解除する** - アプリの状態が、特定の音声認識コマンドが有効になる状態ではないなら、それが他のコマンドと混同されないよう、アプリを登録解除することをご検討ください。</span><span class="sxs-lookup"><span data-stu-id="1a09b-212">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="1a09b-213">**別のアクセントによるテスト** - 別のアクセントのユーザーによってアプリをテストします。</span><span class="sxs-lookup"><span data-stu-id="1a09b-213">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="1a09b-214">**音声コマンドの一貫性を維持** - 「戻る」で前のページに戻るようになっているなら、ご自分のアプリケーションでもこの動作を維持してください。</span><span class="sxs-lookup"><span data-stu-id="1a09b-214">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="1a09b-215">**システムのコマンドを使用しない** - 次の音声コマンドはシステムで予約されています。</span><span class="sxs-lookup"><span data-stu-id="1a09b-215">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="1a09b-216">これらのコマンドは、アプリケーションで使用することができません。</span><span class="sxs-lookup"><span data-stu-id="1a09b-216">These should not be used by applications.</span></span>
   * <span data-ttu-id="1a09b-217">「コルタナさん」</span><span class="sxs-lookup"><span data-stu-id="1a09b-217">"Hey Cortana"</span></span>
   * <span data-ttu-id="1a09b-218">「選択」</span><span class="sxs-lookup"><span data-stu-id="1a09b-218">"Select"</span></span>
   * <span data-ttu-id="1a09b-219">"スタート画面に進む"</span><span class="sxs-lookup"><span data-stu-id="1a09b-219">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="1a09b-220">音声入力の利点</span><span class="sxs-lookup"><span data-stu-id="1a09b-220">Advantages of voice input</span></span>

<span data-ttu-id="1a09b-221">音声入力は、意図を伝える自然な方法です。</span><span class="sxs-lookup"><span data-stu-id="1a09b-221">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="1a09b-222">ユーザーがインターフェイスの複数のステップを切り取ることができるので、音声はインターフェイス**トラバーサル**で特に優れています (ユーザーは、アプリの [戻る] ボタンをクリックするのではなく、web ページの閲覧中に "戻る" と言います)。</span><span class="sxs-lookup"><span data-stu-id="1a09b-222">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="1a09b-223">この小さな節約には、ユーザーによるエクスペリエンスの認識に対する大きな**影響**があるため、少量のスーパーパワーが得られます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-223">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="1a09b-224">音声の使用は、両手がふさがっているときや、**マルチタスク**中にも便利な入力方法です。</span><span class="sxs-lookup"><span data-stu-id="1a09b-224">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="1a09b-225">キーボードでの入力が難しいデバイスでは、**音声ディクテーション**を使用してテキストを入力する方法が効率的です。</span><span class="sxs-lookup"><span data-stu-id="1a09b-225">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="1a09b-226">最後に、宝石とジェスチャの**精度の範囲**が限られている場合は、音声を使用してユーザーの意図を明確にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-226">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="1a09b-227">**音声使用がユーザーにもたらすメリット**</span><span class="sxs-lookup"><span data-stu-id="1a09b-227">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="1a09b-228">時間の短縮 - 最終目的をより効率的にします。</span><span class="sxs-lookup"><span data-stu-id="1a09b-228">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="1a09b-229">労力の最小化 - タスクをよりスムーズかつ簡単にします。</span><span class="sxs-lookup"><span data-stu-id="1a09b-229">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="1a09b-230">認知負荷の軽減 - 直感的かつ簡単で、覚えるのが容易です。</span><span class="sxs-lookup"><span data-stu-id="1a09b-230">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="1a09b-231">社会的に受け入れられる - 動作の観点から社会規範に適合するものです。</span><span class="sxs-lookup"><span data-stu-id="1a09b-231">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="1a09b-232">日常的 - 音声はすぐに習慣的な動作となることができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-232">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="1a09b-233">音声入力の課題</span><span class="sxs-lookup"><span data-stu-id="1a09b-233">Challenges for voice input</span></span>

<span data-ttu-id="1a09b-234">音声入力は多くのさまざまなアプリケーションにとって優れていますが、いくつかの課題に直面しています。</span><span class="sxs-lookup"><span data-stu-id="1a09b-234">While voice input is great for a lot of different applications, it also faces several challenges.</span></span> <span data-ttu-id="1a09b-235">音声入力の利点と課題の両方を理解することで、アプリ開発者は、音声入力を使用する方法とタイミング、およびユーザーのエクスペリエンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-235">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="1a09b-236">**連続入力コントロールの音声入力**細かい制御はその1つです。</span><span class="sxs-lookup"><span data-stu-id="1a09b-236">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="1a09b-237">たとえば、ユーザーが音楽アプリでボリュームを変更する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1a09b-237">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="1a09b-238">単に "音を大きくする" ことができますが、ボリュームを作成するためにシステムがどの程度大きくなっているかが明確ではありません。</span><span class="sxs-lookup"><span data-stu-id="1a09b-238">She can simply say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="1a09b-239">ユーザーは、"少し大きくする" ようにすることができますが、"少し" は定量化が困難です。</span><span class="sxs-lookup"><span data-stu-id="1a09b-239">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="1a09b-240">音声を使用したホログラムの移動またはスケーリングも難しくなります。</span><span class="sxs-lookup"><span data-stu-id="1a09b-240">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="1a09b-241">**音声入力の検出の信頼性**音声入力システムの品質と品質が向上しても、音声コマンドが誤って聞こえたり、解釈されたりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="1a09b-241">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="1a09b-242">重要なのは、システムがリッスンしているときにユーザーにフィードバックを提供することと、ユーザーを正しく理解するうえで潜在的な問題を明確にするためにシステムを認識することによって、アプリケーションのこの課題に対処することです。</span><span class="sxs-lookup"><span data-stu-id="1a09b-242">The key is to address this challenge in your application by providing feedback to the user when the system is listening and what the system understood to create clarity on potential issues in correctly understanding the user.</span></span>  

<span data-ttu-id="1a09b-243">**共有スペースでの音声入力**他のユーザーと共有するスペースでは、音声をソーシャルことができない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1a09b-243">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="1a09b-244">以下は例です。</span><span class="sxs-lookup"><span data-stu-id="1a09b-244">Here are a few examples:</span></span>
* <span data-ttu-id="1a09b-245">ユーザーが他のユーザーを妨害したくない場合があります (たとえば、quiet ライブラリや共有オフィスなど)。</span><span class="sxs-lookup"><span data-stu-id="1a09b-245">The user may not want to disturb others (e.g., in a quiet library or shared office)</span></span>
* <span data-ttu-id="1a09b-246">ユーザーは、公開されていないように見えにくいかもしれません。</span><span class="sxs-lookup"><span data-stu-id="1a09b-246">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="1a09b-247">他のユーザーがリッスンしているときに、個人または機密のメッセージ (パスワードを含む) がディクテーションされることが不快に感じられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1a09b-247">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="1a09b-248">**一意または不明な単語の音声入力**また、ユーザーがシステムに知られていない単語 (ニックネーム、特定のスラング語、略語など) をディクテーションしている場合にも、音声入力の問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-248">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words or abbreviations.</span></span> 

<span data-ttu-id="1a09b-249">**音声コマンドの学習**最終的な目標はシステムと自然に逆のことですが、多くの場合、アプリは特定の定義済み音声コマンドに依存します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-249">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often times apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="1a09b-250">音声コマンドの大規模なセットに関連する課題は、ユーザーをオーバーロードすることなくユーザーを教える方法と、ユーザーがそれらを保持できるようにする方法です。</span><span class="sxs-lookup"><span data-stu-id="1a09b-250">A challenge associated with a big set of voice commands is how to teach them without overloading the user and how to help the user to retain them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="1a09b-251">音声のフィードバックの状態</span><span class="sxs-lookup"><span data-stu-id="1a09b-251">Voice feedback states</span></span>

<span data-ttu-id="1a09b-252">音声が適切に適用されると、**ユーザーは自分が何を言えるのかを理解し、**システムがそれを正しく認識した**という明確なフィードバックを得ます。**</span><span class="sxs-lookup"><span data-stu-id="1a09b-252">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="1a09b-253">こうした 2 つのシグナルにより、ユーザーは音声をメインの入力として使用することに自信を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-253">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="1a09b-254">下の図は、音声入力が認識されたときにカーソルに何が発生するか、またそれがユーザーにどのように伝わるかを示す図です。</span><span class="sxs-lookup"><span data-stu-id="1a09b-254">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="1a09b-255">![1 です。標準のカーソルの状態](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="1a09b-255">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="1a09b-256">**1. 標準のカーソル状態**</span><span class="sxs-lookup"><span data-stu-id="1a09b-256">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="1a09b-257">![2音声フィードバックを通知してから、表示されなくなり](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="1a09b-257">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="1a09b-258">**2. 音声フィードバックを通知してから、非表示にします。**</span><span class="sxs-lookup"><span data-stu-id="1a09b-258">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="1a09b-259">![\* 3.</span><span class="sxs-lookup"><span data-stu-id="1a09b-259">![\*3.</span></span> <span data-ttu-id="1a09b-260">標準のカーソルの状態](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="1a09b-260">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="1a09b-261">**3. 通常のカーソル状態に戻ります。**</span><span class="sxs-lookup"><span data-stu-id="1a09b-261">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="1a09b-262">Mixed Reality における「音声」について、ユーザーが知っておくべき重要な事項</span><span class="sxs-lookup"><span data-stu-id="1a09b-262">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="1a09b-263">ボタンをターゲットにしながら **「選択」** と言います (ボタンをクリックする場所ならどこでもこれを使用できます)。</span><span class="sxs-lookup"><span data-stu-id="1a09b-263">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="1a09b-264">一部のアプリでは、アクションを実行するために**アプリ バー ボタンのラベル名**を言うことができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-264">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="1a09b-265">たとえば、ユーザーは、アプリを見ながらコマンド「削除」を発話することで、アプリを環境から削除することができます (これにより手動でクリックする手間が省けます)。</span><span class="sxs-lookup"><span data-stu-id="1a09b-265">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="1a09b-266">**「コルタナさん」と言うと、Cortana のリスニングを開始することができます。**</span><span class="sxs-lookup"><span data-stu-id="1a09b-266">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="1a09b-267">質問をしたり (「コルタナさん、エッフェル塔の高さは?」など)、アプリを開くように指示したり (「コルタナさん、Netflix を開いて」など)、スタート メニューを表示するように指示したり (「コルタナさん、ホームに戻って」など) することができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-267">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="1a09b-268">音声に関する一般的な質問と問題</span><span class="sxs-lookup"><span data-stu-id="1a09b-268">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="1a09b-269">音声操作の項目。</span><span class="sxs-lookup"><span data-stu-id="1a09b-269">What can I say?</span></span>
* <span data-ttu-id="1a09b-270">音声が正しく認識されているかどうかを確認する方法。</span><span class="sxs-lookup"><span data-stu-id="1a09b-270">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="1a09b-271">音声コマンドが継続的に誤認識される。</span><span class="sxs-lookup"><span data-stu-id="1a09b-271">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="1a09b-272">音声コマンドに対する反応がない。</span><span class="sxs-lookup"><span data-stu-id="1a09b-272">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="1a09b-273">音声コマンドを言ったが、間違った動作になる。</span><span class="sxs-lookup"><span data-stu-id="1a09b-273">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="1a09b-274">自分の音声のターゲットを特定のアプリやアプリ コマンドにする方法。</span><span class="sxs-lookup"><span data-stu-id="1a09b-274">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="1a09b-275">HoloLens のホログラフィック フレームから外れたものに音声でコマンドを出せるか。</span><span class="sxs-lookup"><span data-stu-id="1a09b-275">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="1a09b-276">通信</span><span class="sxs-lookup"><span data-stu-id="1a09b-276">Communication</span></span>

<span data-ttu-id="1a09b-277">HoloLens が提供するカスタマイズされたオーディオ入力処理オプションを利用する必要があるアプリケーションでは、アプリが使用できるさまざまな[オーディオストリームのカテゴリ](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)を理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="1a09b-277">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="1a09b-278">Windows 10 では、さまざまなストリームカテゴリがサポートされています。 HoloLens では、これらのうちの3つを使用して、音声、通信、およびアンビエント環境のオーディオ用に調整されたマイクオーディオの品質を最適化するカスタム処理を可能にします。キャプチャ ("カムコーダー" など) シナリオ。</span><span class="sxs-lookup"><span data-stu-id="1a09b-278">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="1a09b-279">AudioCategory_Communications ストリームカテゴリは、通話の品質とナレーションのシナリオに合わせてカスタマイズされ、クライアントにユーザーの声の 16kHz 24bit mono オーディオストリームを提供します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-279">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="1a09b-280">AudioCategory_Speech ストリームカテゴリは、HoloLens (Windows) 音声エンジン用にカスタマイズされており、ユーザーの声の 16kHz 24bit mono ストリームを提供します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-280">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="1a09b-281">このカテゴリは、サードパーティの音声エンジンで必要に応じて使用できます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-281">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="1a09b-282">AudioCategory_Other ストリームカテゴリは、アンビエント環境オーディオ記録用にカスタマイズされており、クライアントには 48 Khz 24 ビットのステレオオーディオストリームが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1a09b-282">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="1a09b-283">このようなオーディオ処理はすべてハードウェアアクセラレータです。これは、HoloLens CPU で同じ処理が行われた場合と比べて、機能の電力消費が多くなることを意味します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-283">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="1a09b-284">システムのバッテリ寿命を最大化し、組み込みのオフロードオーディオ入力処理を活用するために、CPU で他のオーディオ入力処理を実行しないようにします。</span><span class="sxs-lookup"><span data-stu-id="1a09b-284">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="1a09b-285">言語</span><span class="sxs-lookup"><span data-stu-id="1a09b-285">Languages</span></span>

<span data-ttu-id="1a09b-286">HoloLens 2 では、追加の言語もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1a09b-286">HoloLens 2 also supports additional languages.</span></span> <span data-ttu-id="1a09b-287">複数のキーボードがインストールされている場合や、アプリが別の言語で音声認識エンジンを作成しようとした場合でも、音声コマンドは常にシステムの表示言語で実行されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1a09b-287">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="1a09b-288">[トラブルシューティング]</span><span class="sxs-lookup"><span data-stu-id="1a09b-288">Troubleshooting</span></span>

<span data-ttu-id="1a09b-289">"Select" と "Cortana" を使用して問題が発生している場合は、静かな領域に移動するか、ノイズの発生源から離れるか、音を大きくしてみてください。</span><span class="sxs-lookup"><span data-stu-id="1a09b-289">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="1a09b-290">現時点では、HoloLens の音声認識はすべて米国英語のネイティブスピーカーに対して調整および最適化されています。</span><span class="sxs-lookup"><span data-stu-id="1a09b-290">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="1a09b-291">Windows Mixed Reality Developer Edition release 2017 では、オーディオエンドポイント管理ロジックは、最初の HMD 接続の後、いったんログアウトして PC デスクトップに戻すと、正常に機能します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-291">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="1a09b-292">ユーザーは、WMR OOBE を通過した後に初めてサインアウト/イベントが発生する前に、HMD を初めて接続する前にシステムがどのように設定されているかによって、オーディオの切り替えなしのさまざまなオーディオ機能の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1a09b-292">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="1a09b-293">Unity 用の MRTK (Mixed Reality Toolkit) での音声入力</span><span class="sxs-lookup"><span data-stu-id="1a09b-293">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="1a09b-294">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** では、任意のオブジェクトに音声コマンドを簡単に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-294">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="1a09b-295">MRTK の**音声入力プロファイル**を使用して、キーワードを定義します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-295">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="1a09b-296">**SpeechInputHandler**スクリプトを割り当てることにより、音声入力プロファイルで定義されているキーワードにオブジェクトを応答させることができます。</span><span class="sxs-lookup"><span data-stu-id="1a09b-296">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="1a09b-297">また、SpeechInputHandler は、ユーザーの信頼度を向上させるための音声確認ラベルも提供します。</span><span class="sxs-lookup"><span data-stu-id="1a09b-297">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="1a09b-298">MRTK-Voice コマンド</span><span class="sxs-lookup"><span data-stu-id="1a09b-298">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a><span data-ttu-id="1a09b-299">「</span><span class="sxs-lookup"><span data-stu-id="1a09b-299">See also</span></span>
* [<span data-ttu-id="1a09b-300">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="1a09b-300">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="1a09b-301">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="1a09b-301">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="1a09b-302">MR 入力 212: 音声</span><span class="sxs-lookup"><span data-stu-id="1a09b-302">MR Input 212: Voice</span></span>](holograms-212.md)
* [<span data-ttu-id="1a09b-303">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="1a09b-303">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="1a09b-304">Unity の音声入力</span><span class="sxs-lookup"><span data-stu-id="1a09b-304">Voice input in Unity</span></span>](voice-input-in-unity.md)
