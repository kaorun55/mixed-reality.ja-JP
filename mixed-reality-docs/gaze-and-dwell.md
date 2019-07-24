---
title: 頭の視線入力とドウェル
description: 頭の視線入力とドウェル入力モデルの概要
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality、視線入力、ドウェル、操作、デザイン
ms.openlocfilehash: d522ca3a6f36995959e8e6e87482279d05bf0aa3
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387540"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="ab769-104">頭の視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="ab769-104">Head-gaze and dwell</span></span>

<span data-ttu-id="ab769-105">工具や部品で手がふさがっていると、ジェスチャは面倒であったりできなかったりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="ab769-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="ab769-106">ジェスチャなど音声コマンドは、たとえばかなり騒々しい状況では、信頼性が低い場合があります。</span><span class="sxs-lookup"><span data-stu-id="ab769-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="ab769-107">さらに、音声でコンピューターを制御するのは万国共通ではありませんが、間違いなく勢いを増しています。</span><span class="sxs-lookup"><span data-stu-id="ab769-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="ab769-108">頭の視線入力とドウェルは、HoloLens でヘッドアップとハンズフリーを機能させるための最も使い慣れたマスターしやすいメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="ab769-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="ab769-109">さらに、頭の視線入力のドウェルは操作環境の雑音障害や無音の制約に左右されず、100% 信頼できます。</span><span class="sxs-lookup"><span data-stu-id="ab769-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="ab769-110">シナリオ</span><span class="sxs-lookup"><span data-stu-id="ab769-110">Scenarios</span></span>

<span data-ttu-id="ab769-111">人の手が他の作業でふさがっていて、環境や社会的な制約のために音声を 100% は信頼できない、または利用できないというシナリオでは、頭の視線入力とドウェルが優れています。</span><span class="sxs-lookup"><span data-stu-id="ab769-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or availible due to environmental or social constraints.</span></span> <span data-ttu-id="ab769-112">良い例は、車のエンジンの修理中に参考情報をオーバーレイするために HoloLens を付けている人です。</span><span class="sxs-lookup"><span data-stu-id="ab769-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="ab769-113">その人がエンジンルームに身を乗り出すとき、その手は工具でふさがっているか体を支えています。</span><span class="sxs-lookup"><span data-stu-id="ab769-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="ab769-114">ガレージのスペースは絶えず工具を打ちつける音やブーンという音がして騒々しいため、音声コマンドを使うのは困難です。</span><span class="sxs-lookup"><span data-stu-id="ab769-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="ab769-115">頭の視線入力とドウェルを使用すれば、HoloLens を付けている人は、作業の流れを妨げることなく自信を持って参考資料をナビゲーションすることができます。</span><span class="sxs-lookup"><span data-stu-id="ab769-115">Head-gaze and dwell allows the person in the HoloLens to confidently navigate their reference material without interupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="ab769-116">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="ab769-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ab769-117"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="ab769-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="ab769-118"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="ab769-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="ab769-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="ab769-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="ab769-120"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ab769-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ab769-121">頭の視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="ab769-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="ab769-122">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="ab769-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="ab769-123">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="ab769-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="ab769-124">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="ab769-124">✔️ Recommended</span></span></td>
    </tr>
</table>

## <a name="goals"></a><span data-ttu-id="ab769-125">目標</span><span class="sxs-lookup"><span data-stu-id="ab769-125">Goals</span></span>

<span data-ttu-id="ab769-126">音声を使用せず、完全にハンズフリーの操作のためのメカニズムを提供する。</span><span class="sxs-lookup"><span data-stu-id="ab769-126">Provide a mechanism for fully hands-free interactions, without using voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="ab769-127">設計原則</span><span class="sxs-lookup"><span data-stu-id="ab769-127">Design principles</span></span>

1. <span data-ttu-id="ab769-128">[武器としての視線入力] を回避する</span><span class="sxs-lookup"><span data-stu-id="ab769-128">Avoid "Gaze as a weapon"</span></span>

    <span data-ttu-id="ab769-129">頭の視線入力とドウェルでは視覚的なフィードバックが直感的である必要がありますが、フィードバックが多すぎると不安を誘発する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ab769-129">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="ab769-130">フィードバックは、ユーザーが何をターゲットにしているのかを知るのに役立ちますが、意図に反してそれを自動的に選択するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ab769-130">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="ab769-131">テキスト、アイコン、およびラベルを読み取るには、選択する前に情報を取り入れる余裕を人に提供するための、追加の考慮事項が必要です。</span><span class="sxs-lookup"><span data-stu-id="ab769-131">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
2. <span data-ttu-id="ab769-132">ゴルディロックス速度を追及する</span><span class="sxs-lookup"><span data-stu-id="ab769-132">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="ab769-133">ドウェル操作はナビゲーションの影響に基づいて異なるタイマーを持つことができます。より頻繁に使用される機能は一般的に塗りつぶし時間がより速いという利点がありますが、結果として生じる機能が増えると、塗りつぶし時間がより長くなることが利点になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ab769-133">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="ab769-134">塗りつぶし効果を使用してこれらのタイマーを表示する場合、塗りつぶしの色のアニメーション曲線は、塗りつぶし時間をより速く感じるという良い影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="ab769-134">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="ab769-135">高速/中速/低速の塗りつぶしの速度のオーバーライドからユーザーが決定できるようにすることを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab769-135">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="ab769-136">ヨーヨー効果を使ってはいけないことにする</span><span class="sxs-lookup"><span data-stu-id="ab769-136">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="ab769-137">ヨーヨー効果は不快な頭の動きのパターンであり、コンテンツと頭の視線入力、およびドウェルのコントロールの配置によって、人が継続的に繰り返し上下を見なければならないときに発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ab769-137">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="ab769-138">たとえば、頭の視線入力と下部にあるドウェル ボタンを使ってリストをナビゲーションすると、ドウェルのために下を見て、上で結果を見て、ドウェルのために下を見るといったループが引き起こされます。この結果として得られるパターンは快適ではなく、ナビゲーション コントロールを 1 か所に配置して行ったり来たりしなくても済むようにすることで回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab769-138">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="ab769-139">快適性のためには、ドウェル ボタンをその効果に応じて配置することが重要になります。</span><span class="sxs-lookup"><span data-stu-id="ab769-139">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="ab769-140">UX ガイドラインとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="ab769-140">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="ab769-141">ターゲット サイズ</span><span class="sxs-lookup"><span data-stu-id="ab769-141">Target sizes</span></span>
  <span data-ttu-id="ab769-142">簡単にアクセスできるように、頭の視線入力とドウェルのターゲットは、無理なくターゲットを設定し、人の頭を所定の時間ターゲットに安定してとどめておくのに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab769-142">To be easily accessible, head-gaze and dwell targets need to be large enough to comforatably target, and hold one's head stabily on the target for the prescribed time.</span></span> <span data-ttu-id="ab769-143">最も快適なエクスペリエンスを実現するには、最小 2 度のターゲット サイズをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ab769-143">We reccomend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="ab769-144">視覚的なフィードバック</span><span class="sxs-lookup"><span data-stu-id="ab769-144">Visual feedback</span></span>

<span data-ttu-id="ab769-145">放射状の塗りつぶしを使用してドウェル タイマーを表す場合は、ボタンの中心から開始します。</span><span class="sxs-lookup"><span data-stu-id="ab769-145">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="ab769-146">一貫した反応の方が、さまざまなボタンのさまざまな方向よりも混乱が少なくて済みます。</span><span class="sxs-lookup"><span data-stu-id="ab769-146">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="ab769-147">このルールは方向の操作 (上/下/左/右へのナビゲーションなど) では破られることがあります。</span><span class="sxs-lookup"><span data-stu-id="ab769-147">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="ab769-148">たとえば、Microsoft Dynamics 365 Guides では、NEXT/BACK を左右の塗りつぶしにするという例外を認めています。</span><span class="sxs-lookup"><span data-stu-id="ab769-148">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="ab769-149">ボタンをオフに切り替えるといったシナリオでは、外部からの放射状の塗りつぶしを逆にすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ab769-149">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="ab769-150">ボタンを押すことの反対の感覚は、維持すべき良好な視覚パターンです。</span><span class="sxs-lookup"><span data-stu-id="ab769-150">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="ab769-151">段階的表示</span><span class="sxs-lookup"><span data-stu-id="ab769-151">Progressive disclosure</span></span>

<span data-ttu-id="ab769-152">段階的表示は、操作の各段階で関連性のあるものだけを可能な限り詳細に表示することを意味します。</span><span class="sxs-lookup"><span data-stu-id="ab769-152">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="ab769-153">つまり、ドウェルの場合は、ドウェルのターゲットが強調表示されます (たとえば、リスト コントロールで)。</span><span class="sxs-lookup"><span data-stu-id="ab769-153">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="ab769-154">サイズ超過のターゲット</span><span class="sxs-lookup"><span data-stu-id="ab769-154">Oversized targets</span></span>
<span data-ttu-id="ab769-155">ドウェル領域は、Microsoft Dynamics 365 Guides の [戻る] ボタンのように、使いやすくするためにアクティブでないアイコンより大きくすることができます。</span><span class="sxs-lookup"><span data-stu-id="ab769-155">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="ab769-156">フィードバックの遅延によるちらつきを防止する</span><span class="sxs-lookup"><span data-stu-id="ab769-156">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="ab769-157">視覚的なフィードバックを開始する前に若干の遅延を使用すると、だれかがドウェルのターゲットを横切ったときのちらつきを回避できます。</span><span class="sxs-lookup"><span data-stu-id="ab769-157">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="ab769-158">頻繁に操作するボタンの場合、アプリケーションが敏感に感知するため、遅延を非常に短くしてください。</span><span class="sxs-lookup"><span data-stu-id="ab769-158">For buttons inteacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="ab769-159">あまり頻繁に操作しないボタンの場合は、過敏に感知するインターフェイスを避けると適切な場合があります。</span><span class="sxs-lookup"><span data-stu-id="ab769-159">For buttons that are interacted with infrequenctly a longer delay can be approprate to avoid the interface feeling twitchy.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="ab769-160">UI のパターン</span><span class="sxs-lookup"><span data-stu-id="ab769-160">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="ab769-161">使用頻度の高いボタン</span><span class="sxs-lookup"><span data-stu-id="ab769-161">High frequency buttons</span></span>
<span data-ttu-id="ab769-162">![Microsoft Dynamics 365 ガイド [次へ] ボタン](images/GuideNextButton.png "Microsoft Dynamics 365 ガイド [次へ] ボタン")</span><span class="sxs-lookup"><span data-stu-id="ab769-162">![Microsoft Dynamics 365 Guides Next Button](images/GuideNextButton.png "Microsoft Dynamics 365 Guides Next Button")</span></span><br>
<span data-ttu-id="ab769-163">*高頻度のボタンは、アプリケーション全体で一般的に使用されるボタンです。これらの例として、Microsoft Dynamics 365 ガイドの [次へ] ボタンと [戻る] ボタンがあります。*</span><span class="sxs-lookup"><span data-stu-id="ab769-163">*High frequency buttons are buttons that are used commonly throughout an application. A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.*</span></span>

<span data-ttu-id="ab769-164">使用頻度の高いボタンは、次のようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab769-164">High frequency buttons should...</span></span>
* <span data-ttu-id="ab769-165">頭の視線入力でヒットしやすいよう、大きめのボタンにする</span><span class="sxs-lookup"><span data-stu-id="ab769-165">be larger buttons, easier to hit with head-gaze</span></span>
* <span data-ttu-id="ab769-166">人間工学的な負担を回避するために目の高さからあまり離れないようにする。</span><span class="sxs-lookup"><span data-stu-id="ab769-166">stay near eye height to avoid ergonomic straining.</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="ab769-167">使用頻度の低いボタン</span><span class="sxs-lookup"><span data-stu-id="ab769-167">Low frequency buttons</span></span>
<span data-ttu-id="ab769-168">使用頻度の低いボタンは、アプリケーション全体を通してあまり定期的には操作しないボタンです。</span><span class="sxs-lookup"><span data-stu-id="ab769-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="ab769-169">良い例は、設定メニューにアクセスするためのボタンや、すべての作業を消去するためのボタンです。</span><span class="sxs-lookup"><span data-stu-id="ab769-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="ab769-170">誤ってアクティブ化することのないよう、これらのボタンは頻繁な頭の視線入力の経路の邪魔にならないようにしてみてください。</span><span class="sxs-lookup"><span data-stu-id="ab769-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

### <a name="confirmations"></a><span data-ttu-id="ab769-171">確認</span><span class="sxs-lookup"><span data-stu-id="ab769-171">Confirmations</span></span>
<span data-ttu-id="ab769-172">![Microsoft Dynamics 365 Guides の確認ダイアログ](images/GuidesConfirmation.png "Microsoft Dynamics 365 Guides の確認のダイアログ")</span><span class="sxs-lookup"><span data-stu-id="ab769-172">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesConfirmation.png "Microsoft Dynamics 365 Guides Confirmation Dialog")</span></span>

<span data-ttu-id="ab769-173">料金の請求、作業の削除、長いプロセスの開始のように、アクションに大きな影響がある場合に、人が意図してボタンを選択していることを確認するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ab769-173">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span> <span data-ttu-id="ab769-174">頭の視線入力とドウェルの UI の場合、確認ダイアログにはいくつかのパターンと考慮事項があります。</span><span class="sxs-lookup"><span data-stu-id="ab769-174">For head-gaze and dwell UIs there are some patterns and considerations for confirmation dialogs:</span></span>

  * <span data-ttu-id="ab769-175">メイン ボタンに選択内容を強調表示にして表示してください。</span><span class="sxs-lookup"><span data-stu-id="ab769-175">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="ab769-176">選択内容の強調表示と同時にドウェルのターゲットを表示してください。</span><span class="sxs-lookup"><span data-stu-id="ab769-176">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="ab769-177">セカンダリ ボタンでは、頭の視線入力にドウェルのターゲットを表示してください。</span><span class="sxs-lookup"><span data-stu-id="ab769-177">For the secondary button, reveal the dwell target on head-gaze.</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="ab769-178">トグル ボタン</span><span class="sxs-lookup"><span data-stu-id="ab769-178">Toggle buttons</span></span>
<span data-ttu-id="ab769-179">トグル ボタンを適切に機能させるには、何らかの微妙なロジックが必要です。</span><span class="sxs-lookup"><span data-stu-id="ab769-179">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="ab769-180">人がトグル ボタンをドウェルしてアクティブにするときは、ボタンから離れてから、戻ってドウェル ロジックを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab769-180">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="ab769-181">トグル可能なボタンには、明確にアクティブな状態とアクティブでない状態があることが重要です。</span><span class="sxs-lookup"><span data-stu-id="ab769-181">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

### <a name="list-views"></a><span data-ttu-id="ab769-182">リスト ビュー</span><span class="sxs-lookup"><span data-stu-id="ab769-182">List views</span></span>
<span data-ttu-id="ab769-183">![Microsoft Dynamics 365 Guides の確認ダイアログ](images/GuidesListView.png "Microsoft Dynamics 365 Guides の確認のダイアログ")</span><span class="sxs-lookup"><span data-stu-id="ab769-183">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesListView.png "Microsoft Dynamics 365 Guides Confirmation Dialog")</span></span><br>
<span data-ttu-id="ab769-184">*リストビューでは、熟考入力に特定の課題があります。熟考のターゲットを気にすることなく、コンテンツをスキャンできるようにする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ab769-184">*List views present a particular challenge for head-gaze and dwell input. People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.*</span></span>

<span data-ttu-id="ab769-185">リスト ビューのデザインに関するヒント:</span><span class="sxs-lookup"><span data-stu-id="ab769-185">Some tips for designing list views:</span></span>
* <span data-ttu-id="ab769-186">頭の視線入力のときに行全体が強調表示されるようにしても、頭の視線入力が特定のドウェルのターゲット上にない限り、ドウェルを開始しないでください。</span><span class="sxs-lookup"><span data-stu-id="ab769-186">have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
* <span data-ttu-id="ab769-187">視覚的なノイズを減らすために行を強調表示するときは、ドウェルのターゲットのみを表示してください。</span><span class="sxs-lookup"><span data-stu-id="ab769-187">only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
* <span data-ttu-id="ab769-188">明確にして、ドウェルのターゲットの位置と一致させてください。</span><span class="sxs-lookup"><span data-stu-id="ab769-188">be clear and consistent with the position of dwell targets.</span></span>
* <span data-ttu-id="ab769-189">反復的な UI を回避するため、一度にすべてのドウェルのターゲットを表示しないでください</span><span class="sxs-lookup"><span data-stu-id="ab769-189">don't show all dwell targets at once to avoid repetitive UI</span></span>
* <span data-ttu-id="ab769-190">UX に関する知識を定着させるため、同じパターンをできるだけ頻繁に再利用してください</span><span class="sxs-lookup"><span data-stu-id="ab769-190">re-use the same pattern as often as possible to establish UX familiarity</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="ab769-191">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab769-191">See also</span></span>
* [<span data-ttu-id="ab769-192">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="ab769-192">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ab769-193">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="ab769-193">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="ab769-194">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="ab769-194">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="ab769-195">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="ab769-195">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="ab769-196">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="ab769-196">Voice commanding</span></span>](voice-design.md)
