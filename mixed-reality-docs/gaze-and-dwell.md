---
title: Head 注視しドウェル
description: Head 注視しドウェル入力モデルの概要
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: 複合現実、視線の先、ドウェルとの対話の設計します。
ms.openlocfilehash: ae4688da791fd3afb7be66069049bbe51102dd7e
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039194"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="6ef9d-104">Head 注視しドウェル</span><span class="sxs-lookup"><span data-stu-id="6ef9d-104">Head-gaze and dwell</span></span>

<span data-ttu-id="6ef9d-105">手がの一部のツールおよび占有されているときに、ジェスチャは、面倒なまたは不可能に指定できます。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="6ef9d-106">音声コマンド、ジェスチャなどは、非常に大きい状況など、特定のコンテキストで信頼性の高いことができます。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="6ef9d-107">さらに、普遍的に一般的なは、コンピュータの管理に音声を使用していないが、間違いなく蒸気得るは!</span><span class="sxs-lookup"><span data-stu-id="6ef9d-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="6ef9d-108">Head 注視しドウェル ヘッドアップとハンズフリー HoloLens で作業を行うのための最もよく理解しマスターにメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="6ef9d-109">さらに、視線入力の先頭とドウェルが 100% の信頼性の高いオペレーティング環境でノイズ干渉もサイレント状態の制約に依存しません。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="6ef9d-110">シナリオ</span><span class="sxs-lookup"><span data-stu-id="6ef9d-110">Scenarios</span></span>

<span data-ttu-id="6ef9d-111">ユーザーの手は、他のタスクでビジー状態、音声のない 100% の信頼性があり、環境またはソーシャルの制約のために使用できるシナリオで Head 注視しドウェルが優れています。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or availible due to environmental or social constraints.</span></span> <span data-ttu-id="6ef9d-112">良い例では、車のエンジンの修復中に参照情報を重ね合わせる、HoloLens を着ている人です。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="6ef9d-113">開発者は、ツールまたはエンジンのコンパートメントにリーン、として、本体をサポートしている多忙です。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="6ef9d-114">ガレージ領域は、打ちつけると窓辺ツール、音声コマンドを困難にするための定数と、大きな音です。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="6ef9d-115">Head 注視しドウェルは、ワークフローを停止することがなく、参考資料を自信を持って移動する HoloLens の担当者にできます。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-115">Head-gaze and dwell allows the person in the HoloLens to confidently navigate their reference material without interupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="6ef9d-116">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="6ef9d-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6ef9d-117"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="6ef9d-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="6ef9d-118"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="6ef9d-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="6ef9d-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6ef9d-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="6ef9d-120"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="6ef9d-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6ef9d-121">Head 注視しドウェル</span><span class="sxs-lookup"><span data-stu-id="6ef9d-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="6ef9d-122">推奨 ✔️</span><span class="sxs-lookup"><span data-stu-id="6ef9d-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="6ef9d-123">推奨 ✔️</span><span class="sxs-lookup"><span data-stu-id="6ef9d-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="6ef9d-124">推奨 ✔️</span><span class="sxs-lookup"><span data-stu-id="6ef9d-124">✔️ Recommended</span></span></td>
    </tr>
</table>

## <a name="goals"></a><span data-ttu-id="6ef9d-125">目標</span><span class="sxs-lookup"><span data-stu-id="6ef9d-125">Goals</span></span>

<span data-ttu-id="6ef9d-126">音声を使用せず、完全に楽の相互作用するためのメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-126">Provide a mechanism for fully hands-free interactions, without using Voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="6ef9d-127">設計原則</span><span class="sxs-lookup"><span data-stu-id="6ef9d-127">Design principles</span></span>

1. <span data-ttu-id="6ef9d-128">「武器として視線」を回避します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-128">Avoid "Gaze as a weapon"</span></span>

    <span data-ttu-id="6ef9d-129">Head 注視しドウェルに直感的に視覚的なフィードバックが必要ですが、あまりフィードバックに関する不安を誘発できます。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-129">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="6ef9d-130">フィードバックは、ユーザーが知ると、対象としている、自動選択ではありませんが、その目的に対してを支援する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-130">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="6ef9d-131">テキスト、アイコン、およびラベルを読み取るには、追加の考慮事項を選択する前に情報を吸収する人分のスペースが必要です。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-131">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
2. <span data-ttu-id="6ef9d-132">ゴルディロックスの速度をシークします。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-132">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="6ef9d-133">ドウェルの相互作用がナビゲーションの影響に基づいて別のタイマーを持つことができます - 頻繁に使用される関数一般的にメリットが塗りつぶし時間の短縮、塗りつぶしの時間が長くなるメリットより派生的損害関数が可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-133">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="6ef9d-134">塗りつぶし効果を使用して、これらのタイマーを表示する、塗りつぶしの色のアニメーション曲線対し肯定的な塗りつぶしより高速の気に影響します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-134">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="6ef9d-135">高速/中/低速なからユーザーの意思決定を有効にする考慮する必要がある速度のオーバーライドを入力します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-135">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="6ef9d-136">たとえばヨーヨー効果にタブー</span><span class="sxs-lookup"><span data-stu-id="6ef9d-136">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="6ef9d-137">ヨーヨー効果は、コンテンツと head 注視ドウェル コントロールの配置を継続的に検索を上下繰り返し人場合に発生する可能性がヘッドの移動のデメリットのパターンです。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-137">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="6ef9d-138">など、下部にあるヘッド注視しドウェル ボタンとリスト nav は、熟考に検索結果、参照下げなければなどにダウンの外観のループを誘発します。この結果として得られるパターンは快適ではなく、未満の前後を必要とする、1 か所にナビゲーション コントロールを配置することで回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-138">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="6ef9d-139">効果を基準としたドウェル ボタンの配置は、快適性にとって重要になります。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-139">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="6ef9d-140">UX のガイドラインとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="6ef9d-140">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="6ef9d-141">ターゲット サイズ</span><span class="sxs-lookup"><span data-stu-id="6ef9d-141">Target sizes</span></span>
  <span data-ttu-id="6ef9d-142">簡単にアクセスできるように、head 注視と comforatably のターゲットに十分な大きさにターゲットの必要性を熟考、1 つのヘッド stabily ターゲットで所定の時間します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-142">To be easily accessible, head-gaze and dwell targets need to be large enough to comforatably target, and hold one's head stabily on the target for the prescribed time.</span></span> <span data-ttu-id="6ef9d-143">最も快適なエクスペリエンスを実現するために 2 度の最小のターゲット サイズをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-143">We reccomend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="6ef9d-144">視覚的なフィードバック</span><span class="sxs-lookup"><span data-stu-id="6ef9d-144">Visual feedback</span></span>

<span data-ttu-id="6ef9d-145">円形の塗りを表すドウェル タイマーを使用する場合は、ボタンの中心から開始します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-145">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="6ef9d-146">一貫性のある応答がさまざまなボタン上のすべてのさまざまな方向よりも簡単です。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-146">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="6ef9d-147">このルールは方向の相互作用 (たとえば、nav アップ/ダウン/左/右など) に対しても切断できます。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-147">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="6ef9d-148">たとえば、Microsoft Dynamics 365 のガイドは、次へ/戻るで例外は右側の塗りつぶしに残っています。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-148">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="6ef9d-149">オフ ボタンを切り替えることのようなシナリオに、外部からの放射状塗りつぶしを反転することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-149">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="6ef9d-150">ボタンを押すの逆の感情は、維持するために優れた visual パターンです。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-150">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="6ef9d-151">プログレッシブの公開</span><span class="sxs-lookup"><span data-stu-id="6ef9d-151">Progressive disclosure</span></span>

<span data-ttu-id="6ef9d-152">プログレッシブの公開は、関連する相互作用の各段階では、できるだけ詳しくしか表示されていないを意味します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-152">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="6ef9d-153">ドウェル、ドウェル ターゲット (など、リスト コントロール) で強調表示を明らかになったを意味します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-153">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="6ef9d-154">ターゲットのサイズの超過</span><span class="sxs-lookup"><span data-stu-id="6ef9d-154">Oversized targets</span></span>
<span data-ttu-id="6ef9d-155">ドウェル リージョンは、Microsoft Dynamics 365 のガイドの [戻る] ボタンのような使いやすくする非アクティブなアイコンより大きくすることができます。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-155">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="6ef9d-156">ちらつきの遅延のフィードバックを回避します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-156">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="6ef9d-157">視覚的なフィードバックを開始する前に、若干の遅延を使用すると、ドウェル ターゲット上のだれかが成功したとき、ちらつきを回避できます。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-157">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="6ef9d-158">頻繁にボタン inteacted、事後対応型アプリケーションを感じているので、非常に短い遅延を維持します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-158">For buttons inteacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="6ef9d-159">Infrequenctly 対話はボタンの待ち時間が長くなるに感じて twitchy インターフェイスを回避するために適切なことができます。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-159">For buttons that are interacted with infrequenctly a longer delay can be approprate to avoid the interface feeling twitchy.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="6ef9d-160">UI パターン</span><span class="sxs-lookup"><span data-stu-id="6ef9d-160">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="6ef9d-161">高頻度のボタン</span><span class="sxs-lookup"><span data-stu-id="6ef9d-161">High frequency buttons</span></span>
<span data-ttu-id="6ef9d-162">![Microsoft Dynamics 365 ガイド [次へ] ボタン](images/GuideNextButton.png "Microsoft Dynamics 365 ガイド [次へ] ボタン")高頻度のボタンは、アプリケーション全体でよく使用されるボタン。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-162">![Microsoft Dynamics 365 Guides Next Button](images/GuideNextButton.png "Microsoft Dynamics 365 Guides Next Button") High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="6ef9d-163">これらの良い例は、Microsoft Dynamics 365 のガイドの前と [次へ] ボタンです。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-163">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span>

<span data-ttu-id="6ef9d-164">高頻度のボタンにする必要があります.</span><span class="sxs-lookup"><span data-stu-id="6ef9d-164">High frequency buttons should...</span></span>
* <span data-ttu-id="6ef9d-165">ボタンのサイズの拡大をヘッド視線の先にヒットしやすくなります</span><span class="sxs-lookup"><span data-stu-id="6ef9d-165">be larger buttons, easier to hit with head-gaze</span></span>
* <span data-ttu-id="6ef9d-166">人間工学の負担を回避するために目の高さの近くのままです。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-166">stay near eye height to avoid ergonomic straining.</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="6ef9d-167">低頻度のボタン</span><span class="sxs-lookup"><span data-stu-id="6ef9d-167">Low frequency buttons</span></span>
<span data-ttu-id="6ef9d-168">低頻度のボタンは、アプリケーション全体で定期的と対話しないボタンです。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="6ef9d-169">良い例は、[設定] メニューにアクセスするためのボタンまたはすべての作業をオフにするためのボタンにあります。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="6ef9d-170">偶発的なアクティブ化を回避するために head 視線入力パスが頻繁に支障がなく、これらのボタンを維持しようとしてください。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

### <a name="confirmations"></a><span data-ttu-id="6ef9d-171">確認</span><span class="sxs-lookup"><span data-stu-id="6ef9d-171">Confirmations</span></span>
<span data-ttu-id="6ef9d-172">![Microsoft Dynamics 365 ガイドの確認ダイアログ](images/GuidesConfirmation.png "Microsoft Dynamics 365 ガイド確認のダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="6ef9d-172">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesConfirmation.png "Microsoft Dynamics 365 Guides Confirmation Dialog")</span></span>

<span data-ttu-id="6ef9d-173">アクションにお金を充電中、作業を削除する、長いプロセスの起動などの大きな影響がある場合は、個人させようと、ボタンを選択していることを確認すると便利です。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-173">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span> <span data-ttu-id="6ef9d-174">Head 注視しドウェルの Ui がありますが、いくつかのパターンと確認のダイアログ ボックスに関する考慮事項です。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-174">For head-gaze and dwell UIs there are some patterns and considerations for confirmation dialogs:</span></span>

  * <span data-ttu-id="6ef9d-175">メイン ボタンの選択範囲の強調表示を表示します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-175">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="6ef9d-176">表示は、選択範囲の強調表示と同時にターゲットを熟考します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-176">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="6ef9d-177">セカンダリのボタンの head 視線の先にドウェル ターゲットを明らかになります。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-177">For the secondary button, reveal the dwell target on head-gaze.</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="6ef9d-178">トグル ボタン</span><span class="sxs-lookup"><span data-stu-id="6ef9d-178">Toggle buttons</span></span>
<span data-ttu-id="6ef9d-179">トグル ボタンでは、適切に機能するいくつかの微妙ロジックが必要です。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-179">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="6ef9d-180">個人 dwells トグル ボタンと在職者が、ときに、ボタンを終了してドウェル ロジックを再起動し、戻る必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-180">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="6ef9d-181">ボタンを指定することがある非アクティブな状態とクリア アクティブが重要です。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-181">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

### <a name="list-views"></a><span data-ttu-id="6ef9d-182">リスト ビュー</span><span class="sxs-lookup"><span data-stu-id="6ef9d-182">List views</span></span>
<span data-ttu-id="6ef9d-183">![Microsoft Dynamics 365 ガイドの確認ダイアログ](images/GuidesListView.png "Microsoft Dynamics 365 ガイドの確認ダイアログ")リスト ビューが head 視線の先の特定の課題を提示する、入力について詳しく説明しません。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-183">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesListView.png "Microsoft Dynamics 365 Guides Confirmation Dialog") List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="6ef9d-184">ユーザーは、tiptoe ドウェル ターゲットの周囲にあるような気分せず、コンテンツをスキャンすることができる必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-184">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span> 

<span data-ttu-id="6ef9d-185">リスト ビューのデザインに関するヒント。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-185">Some tips for designing list views:</span></span>
* <span data-ttu-id="6ef9d-186">head gazed しますが、head 注視で特定ドウェル ターゲットでない限り、ドウェルの先頭がないときに強調表示は全体の行があります。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-186">have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
* <span data-ttu-id="6ef9d-187">ビジュアルのノイズを減らすに行が強調表示されているときにのみドウェル ターゲットを表示します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-187">only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
* <span data-ttu-id="6ef9d-188">明確で一貫性のあるドウェル ターゲットの位置にあります。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-188">be clear and consistent with the position of dwell targets.</span></span>
* <span data-ttu-id="6ef9d-189">反復的な UI を回避するには、一度にターゲットを下げなければすべてを表示しません。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-189">don't show all dwell targets at once to avoid repetitive UI</span></span>
* <span data-ttu-id="6ef9d-190">同じパターンを限り UX に関する知識を確立するために頻繁に再利用します。</span><span class="sxs-lookup"><span data-stu-id="6ef9d-190">re-use the same pattern as often as possible to establish UX familiarity</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="6ef9d-191">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ef9d-191">See also</span></span>
* [<span data-ttu-id="6ef9d-192">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="6ef9d-192">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6ef9d-193">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="6ef9d-193">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="6ef9d-194">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="6ef9d-194">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="6ef9d-195">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="6ef9d-195">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="6ef9d-196">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="6ef9d-196">Voice commanding</span></span>](voice-design.md)
