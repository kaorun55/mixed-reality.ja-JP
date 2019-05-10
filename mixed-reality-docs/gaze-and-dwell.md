---
title: 視線入力とドウェル
description: 視線入力とドウェルの入力モデルの概要
author: liamartinez
ms.author: liamar
ms.date: 03/31/2019
ms.topic: article
keywords: 複合現実、視線の先、ドウェルとの対話の設計します。
ms.openlocfilehash: d99180b6eb278eb6d7bf322c01a1c7cceb7fad1f
ms.sourcegitcommit: a4a53e6772805d89a47588857e3e8fb1fd8d9710
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469064"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="b64d2-104">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="b64d2-104">Gaze and dwell</span></span>

<span data-ttu-id="b64d2-105">手がの一部のツールおよび占有されているときに、ジェスチャは、面倒なまたは不可能に指定できます。</span><span class="sxs-lookup"><span data-stu-id="b64d2-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>  <span data-ttu-id="b64d2-106">音声コマンド、ジェスチャなどは、く信頼性が高く、非常に大きい条件などのことができます。</span><span class="sxs-lookup"><span data-stu-id="b64d2-106">Voice commands, like gesture, can be situationally unreliable, for example under excessively loud conditions.</span></span>  <span data-ttu-id="b64d2-107">さらに、コンピュータの管理に音声を使用してまだ主流の対話が間違いなく蒸気獲得が!</span><span class="sxs-lookup"><span data-stu-id="b64d2-107">Additionally, using voice to control computers isn't a mainstream interaction yet, but it certainly is gaining steam!</span></span>  <span data-ttu-id="b64d2-108">視線入力ドウェルには、最もよく理解しマスターにハンズフリー HoloLens で作業ヘッドアップ メカニズムが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b64d2-108">Gaze dwell offers the most familiar and easy-to-master mechanism for working heads-up hands-free on HoloLens.</span></span>  <span data-ttu-id="b64d2-109">視線入力ドウェルの 100% の信頼性がさらに、運用環境でノイズ干渉もサイレント状態の制約に依存しません。</span><span class="sxs-lookup"><span data-stu-id="b64d2-109">Additionally, gaze dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="goals"></a><span data-ttu-id="b64d2-110">目標</span><span class="sxs-lookup"><span data-stu-id="b64d2-110">Goals</span></span>

<span data-ttu-id="b64d2-111">音声を使用せず、相互作用の完全な楽にするためのメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="b64d2-111">Provide a mechanism for full hands-free interactions, without using voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="b64d2-112">設計原則</span><span class="sxs-lookup"><span data-stu-id="b64d2-112">Design principles</span></span>

1. <span data-ttu-id="b64d2-113">視線の先は、武器ではありません。</span><span class="sxs-lookup"><span data-stu-id="b64d2-113">Gaze is not a weapon</span></span>
    
    <span data-ttu-id="b64d2-114">視線入力、直感的な対話の視覚的なフィードバックが必要ですが、あまりフィードバックに関する不安を誘発できます。</span><span class="sxs-lookup"><span data-stu-id="b64d2-114">Gaze requires visual feedback for intuitive interaction, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="b64d2-115">フィードバックは、ユーザーが何が対象としている、いない自動選択の目的に対してが把握を支援する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b64d2-115">The feedback should help a user know what they're targeting, but not auto-select against their intent.</span></span> <span data-ttu-id="b64d2-116">テキストを読み取るには、追加の考慮事項を選択する前に、情報を吸収するユーザーのルームを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b64d2-116">Reading text requires extra consideration to provide a user room to absorb the info before selecting.</span></span>
    
2. <span data-ttu-id="b64d2-117">ゴルディロックスの速度をシークします。</span><span class="sxs-lookup"><span data-stu-id="b64d2-117">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="b64d2-118">ドウェル塗りつぶしがナビゲーションの影響に基づいて別のタイマーを持つことができます - 頻繁に使用される関数一般的にメリットが塗りつぶし時間の短縮、塗りつぶしの時間が長くなるメリットより派生的損害関数が可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b64d2-118">The dwell fill can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="b64d2-119">アニメーション曲線の塗りつぶしの色は、塗りつぶしより高速の気に対し肯定的な影響します。</span><span class="sxs-lookup"><span data-stu-id="b64d2-119">Animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="b64d2-120">高速/中/低速なからユーザーの意思決定を有効にする考慮する必要がある速度のオーバーライドを入力します。</span><span class="sxs-lookup"><span data-stu-id="b64d2-120">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="b64d2-121">たとえばヨーヨー効果にタブー</span><span class="sxs-lookup"><span data-stu-id="b64d2-121">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="b64d2-122">ヨーヨー効果 (とも呼ばれます"夜間に、Roxbury") には、特定の配置のコンテンツと視線入力ベースのコントロールから発生する可能性が、不快パターンです。</span><span class="sxs-lookup"><span data-stu-id="b64d2-122">The yo-yo effect (also known as "Night at the Roxbury") is an uncomfortable pattern that can emerge from certain  placement of content and gaze-based controls.</span></span> <span data-ttu-id="b64d2-123">たとえばの塗りつぶし ボタンを下部にある一覧 nav は、下げなければ、結果見て、ドウェルなどを確認するダウンの外観のループを誘発します。この結果として得られるパターンは快適ではなく、未満の前後を必要とする、1 か所にナビゲーション コントロールを配置することで回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b64d2-123">For example, a list nav with the fill button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="b64d2-124">効果を基準としたドウェル ボタンの配置は、快適性にとって重要になります。</span><span class="sxs-lookup"><span data-stu-id="b64d2-124">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="b64d2-125">UI パターン</span><span class="sxs-lookup"><span data-stu-id="b64d2-125">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="b64d2-126">高頻度のボタン</span><span class="sxs-lookup"><span data-stu-id="b64d2-126">High frequency buttons</span></span>
    
* <span data-ttu-id="b64d2-127">[次へ/戻る] ボタン</span><span class="sxs-lookup"><span data-stu-id="b64d2-127">Next/Back buttons</span></span>
  * <span data-ttu-id="b64d2-128">非常に短い遅延の前の塗りつぶし (架ちらつきのバッファー)</span><span class="sxs-lookup"><span data-stu-id="b64d2-128">Very short delay pre-fill (flyover flicker buffer)</span></span>
  * <span data-ttu-id="b64d2-129">大きなボタンが視線の先にヒットしやすい</span><span class="sxs-lookup"><span data-stu-id="b64d2-129">Larger buttons are easier to hit with gaze</span></span>
  * <span data-ttu-id="b64d2-130">これらは、目の高さを操作するための歪みを保持する便利です</span><span class="sxs-lookup"><span data-stu-id="b64d2-130">Nice to keep these at eye height so no strain to interact</span></span>
  * <span data-ttu-id="b64d2-131">ドウェル リージョンが (バックアップ) を使用するが容易に非アクティブなアイコンより大きくすることができます。</span><span class="sxs-lookup"><span data-stu-id="b64d2-131">Dwell region can be larger than inactive icon to make it easier to use (Back)</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="b64d2-132">低頻度のボタン</span><span class="sxs-lookup"><span data-stu-id="b64d2-132">Low frequency buttons</span></span>
    
* <span data-ttu-id="b64d2-133">[設定] メニューをアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="b64d2-133">Activate settings menu</span></span>
  * <span data-ttu-id="b64d2-134">前の塗りつぶしはい (架ちらつきのバッファー) の遅延になった</span><span class="sxs-lookup"><span data-stu-id="b64d2-134">Longer delay pre-fill okay (flyover flicker buffer)</span></span>
  * <span data-ttu-id="b64d2-135">頻繁にカーソル経路支障がなく、これらのボタンを保持しようとしてください。</span><span class="sxs-lookup"><span data-stu-id="b64d2-135">Try to keep these buttons out of the way of frequent cursor pathways</span></span>

* <span data-ttu-id="b64d2-136">確認 (つまりスキャン フロー、ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="b64d2-136">Confirmations (i.e. scan flow, dialogs)</span></span>
  * <span data-ttu-id="b64d2-137">メイン ボタンの選択範囲の強調表示を表示します。</span><span class="sxs-lookup"><span data-stu-id="b64d2-137">Show selection highlight on main button</span></span>
  * <span data-ttu-id="b64d2-138">表示は、選択範囲の強調表示と同時にターゲットを下げなければ</span><span class="sxs-lookup"><span data-stu-id="b64d2-138">Reveal dwell target at same time as selection highlight</span></span>
  * <span data-ttu-id="b64d2-139">使用対象のインターフェイスはシンプルにするにはアイコンを囲むについて詳しく説明しません</span><span class="sxs-lookup"><span data-stu-id="b64d2-139">Use dwell target surrounding icon to keep interface simple</span></span>
  * <span data-ttu-id="b64d2-140">強調表示がアクティブにならないように、重要な意思決定の再検討時間ドウェル ターゲットを表示します。</span><span class="sxs-lookup"><span data-stu-id="b64d2-140">Important decision, so highlight doesn't activate, reveals dwell target for reconsideration time</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="b64d2-141">トグル ボタン</span><span class="sxs-lookup"><span data-stu-id="b64d2-141">Toggle buttons</span></span>

* <span data-ttu-id="b64d2-142">Pin</span><span class="sxs-lookup"><span data-stu-id="b64d2-142">Pin</span></span>
  * <span data-ttu-id="b64d2-143">ビジュアルのクリア アクティブまたは非アクティブの状態</span><span class="sxs-lookup"><span data-stu-id="b64d2-143">Clear active/inactive visual state</span></span>
  * <span data-ttu-id="b64d2-144">放射状の塗りつぶしのユーザーがフォーカスと自然な進行状況を提供します。</span><span class="sxs-lookup"><span data-stu-id="b64d2-144">Radial fill helps focus user and provides natural progress</span></span> 

* <span data-ttu-id="b64d2-145">個々 の設定</span><span class="sxs-lookup"><span data-stu-id="b64d2-145">Individual settings</span></span>
  * <span data-ttu-id="b64d2-146">クリア アクティブまたは非アクティブの状態</span><span class="sxs-lookup"><span data-stu-id="b64d2-146">Clear active/inactive states</span></span>
  * <span data-ttu-id="b64d2-147">左の周囲のアイコン上のすべてのターゲットについて詳しく説明しません</span><span class="sxs-lookup"><span data-stu-id="b64d2-147">Dwell targets all on left surrounding icon</span></span>
  * <span data-ttu-id="b64d2-148">ドウェル ターゲットの選択がアクティブなを強調表示にのみ表示</span><span class="sxs-lookup"><span data-stu-id="b64d2-148">Dwell targets only show up when selection highlight active</span></span>
  * <span data-ttu-id="b64d2-149">設定のオン/オフの右側にある「スライダーについて熟考」</span><span class="sxs-lookup"><span data-stu-id="b64d2-149">"Dwell on slider" on right side for on/off settings</span></span>

### <a name="list-views"></a><span data-ttu-id="b64d2-150">リスト ビュー</span><span class="sxs-lookup"><span data-stu-id="b64d2-150">List views</span></span>

* <span data-ttu-id="b64d2-151">参照のリスト ビュー - ガイド ファイルを開く</span><span class="sxs-lookup"><span data-stu-id="b64d2-151">Browsing list view - guide files to open</span></span>
  * <span data-ttu-id="b64d2-152">カーソルの強調表示の行で任意の場所から行がドウェルが開始されていません</span><span class="sxs-lookup"><span data-stu-id="b64d2-152">Cursor highlights row from anywhere on row but doesn’t begin dwell</span></span>
  * <span data-ttu-id="b64d2-153">カーソルによって行が強調表示、左にドウェル ターゲットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b64d2-153">When row is highlighted by cursor, dwell target appears on left</span></span>
  * <span data-ttu-id="b64d2-154">常にすべてのリスト ビュー内のテキストの左側にある円のターゲットについて詳しく説明しません</span><span class="sxs-lookup"><span data-stu-id="b64d2-154">Dwell target always a circle on left side of text in all list views</span></span>
  * <span data-ttu-id="b64d2-155">反復的な UI を回避するには、一度にターゲットを下げなければすべてを表示しません。</span><span class="sxs-lookup"><span data-stu-id="b64d2-155">Don't show all dwell targets at once to avoid repetitive UI</span></span>
  * <span data-ttu-id="b64d2-156">UX に関する知識を確立するために、同じパターンを再利用します。</span><span class="sxs-lookup"><span data-stu-id="b64d2-156">Re-use the same pattern to establish UX familiarity</span></span>
        
* <span data-ttu-id="b64d2-157">リスト ビュー - タスク/手順ガイドでの階層を参照</span><span class="sxs-lookup"><span data-stu-id="b64d2-157">Browsing list view - hierarchy of tasks/steps in a guide</span></span>
  * <span data-ttu-id="b64d2-158">ターゲット テキストの左側にある円を常にについて詳しく説明しません</span><span class="sxs-lookup"><span data-stu-id="b64d2-158">Dwell target always a circle on left side of text</span></span>
  * <span data-ttu-id="b64d2-159">アフォー ダンスを下げなければ折りたたみ/展開</span><span class="sxs-lookup"><span data-stu-id="b64d2-159">Collapse/expand dwell affordance</span></span>
        
* <span data-ttu-id="b64d2-160">参照のリスト ビュー - モードの選択</span><span class="sxs-lookup"><span data-stu-id="b64d2-160">Browsing list view - mode select</span></span>
  * <span data-ttu-id="b64d2-161">上で確立されているパターンに従ってください。</span><span class="sxs-lookup"><span data-stu-id="b64d2-161">Follow patterns established above</span></span>

### <a name="contextual-buttons"></a><span data-ttu-id="b64d2-162">コンテキストのボタン</span><span class="sxs-lookup"><span data-stu-id="b64d2-162">Contextual buttons</span></span>

* <span data-ttu-id="b64d2-163">表示/非表示 3D で表示する 3D でホログラム近く tether に沿って</span><span class="sxs-lookup"><span data-stu-id="b64d2-163">Show/Hide 3D - shows up in 3D along tether near holograms</span></span> 
  * <span data-ttu-id="b64d2-164">ビジュアルのクリア アクティブまたは非アクティブの状態</span><span class="sxs-lookup"><span data-stu-id="b64d2-164">Clear active/inactive visual state</span></span>

### <a name="pivots"></a><span data-ttu-id="b64d2-165">ピボット</span><span class="sxs-lookup"><span data-stu-id="b64d2-165">Pivots</span></span>

* <span data-ttu-id="b64d2-166">最近使ったもの]、[すべてのガイドの一覧</span><span class="sxs-lookup"><span data-stu-id="b64d2-166">Recent/All guides list</span></span>
  * <span data-ttu-id="b64d2-167">どのタブがアクティブであることを示す残っている UI アフォー ダンスを塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="b64d2-167">Fill the UI affordance that remains to indicate which tab is active</span></span>
  * <span data-ttu-id="b64d2-168">私たちドウェルの対象パターンを使用しないことを選択の簡単な 1 つの単語のピボット</span><span class="sxs-lookup"><span data-stu-id="b64d2-168">For short single word pivots, we elected to forego the dwell target pattern</span></span>
  * <span data-ttu-id="b64d2-169">別の 2 つの円のターゲットと広い UI より使いやすいインターフェイスを優先します</span><span class="sxs-lookup"><span data-stu-id="b64d2-169">We favored the simplified interface over another 2 circle targets and a wider UI</span></span>
  * <span data-ttu-id="b64d2-170">ここでは、単語は短い遅延がいっぱいになる前に十分な快適性を提供します。</span><span class="sxs-lookup"><span data-stu-id="b64d2-170">In our case, the words are short enough that a delay provides enough comfort before filling</span></span>


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="b64d2-171">UX のガイドラインとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="b64d2-171">UX guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="b64d2-172">ターゲット サイズ</span><span class="sxs-lookup"><span data-stu-id="b64d2-172">Target sizes</span></span>

  * <span data-ttu-id="b64d2-173">ピン アイコンの最小サイズ:Unity では、30 の Mru (2 m @ 30 cm) ワールド空間における 6 cm</span><span class="sxs-lookup"><span data-stu-id="b64d2-173">Pin icon minimum size: 6cm in world space in Unity, 30 MRUs ( 30cm @ 2m)</span></span>
  * <span data-ttu-id="b64d2-174">ターゲット「帯びた」または"sticky"をまったくされますか。</span><span class="sxs-lookup"><span data-stu-id="b64d2-174">Are the targets "magnetized" or "sticky" at all?</span></span> <span data-ttu-id="b64d2-175">(つまり視線カーソル スムージング)</span><span class="sxs-lookup"><span data-stu-id="b64d2-175">(i.e. gaze cursor smoothing)</span></span>

### <a name="animation"></a><span data-ttu-id="b64d2-176">アニメーション</span><span class="sxs-lookup"><span data-stu-id="b64d2-176">Animation</span></span>

  * <span data-ttu-id="b64d2-177">ドウェル visual トリガー .5sec 前に遅延します。</span><span class="sxs-lookup"><span data-stu-id="b64d2-177">Delay before dwell visual triggers .5sec</span></span>
  * <span data-ttu-id="b64d2-178">ドウェル ビジュアル 1.2 秒の期間</span><span class="sxs-lookup"><span data-stu-id="b64d2-178">Duration of dwell visual 1.2sec</span></span>
  * <span data-ttu-id="b64d2-179">アニメーションに曲線でしょうか。</span><span class="sxs-lookup"><span data-stu-id="b64d2-179">Curve on animation?</span></span>

### <a name="visual-feedback"></a><span data-ttu-id="b64d2-180">視覚的なフィードバック</span><span class="sxs-lookup"><span data-stu-id="b64d2-180">Visual feedback</span></span>

  * <span data-ttu-id="b64d2-181">視線入力カーソルの開始位置から放射状の塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="b64d2-181">Radial fill from gaze cursor start location</span></span>
  * <span data-ttu-id="b64d2-182">ボタンの中心から常に放射状塗りつぶし。</span><span class="sxs-lookup"><span data-stu-id="b64d2-182">Always radial fill from center of button.</span></span> <span data-ttu-id="b64d2-183">一貫性のある応答がさまざまなボタン上のすべてのさまざまな方向よりも簡単です。</span><span class="sxs-lookup"><span data-stu-id="b64d2-183">A consistent response is less confusing than all different directions on different buttons.</span></span> 
    * <span data-ttu-id="b64d2-184">このルールは方向の相互作用 (たとえば、nav アップ/ダウン/左/右など) に対しても切断できます。</span><span class="sxs-lookup"><span data-stu-id="b64d2-184">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="b64d2-185">たとえば、ガイドは、次へ/戻るが残っている例外は、塗りつぶしを右します。</span><span class="sxs-lookup"><span data-stu-id="b64d2-185">For example, Guides makes an exception on Next/Back being left right fills.</span></span>
    * <span data-ttu-id="b64d2-186">外部から放射状の塗りつぶしを反転する (オフを切り替える) 場合に検討してください。</span><span class="sxs-lookup"><span data-stu-id="b64d2-186">Consider inverting radial fill from outside (if toggling off).</span></span> <span data-ttu-id="b64d2-187">ボタンを押すの逆の感情は、維持するために優れた visual パターンです。</span><span class="sxs-lookup"><span data-stu-id="b64d2-187">THe inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="b64d2-188">プログレッシブの公開</span><span class="sxs-lookup"><span data-stu-id="b64d2-188">Progressive disclosure</span></span>

 * <span data-ttu-id="b64d2-189">プログレッシブの公開はドウェル ターゲットに (たとえば、リスト コントロール) で強調表示を明らかになったことを意味します。</span><span class="sxs-lookup"><span data-stu-id="b64d2-189">Progressive disclosure means that the dwell target is revealed on highlight (e.g., in a list control)</span></span>
 * <span data-ttu-id="b64d2-190">テキストの任意の場所に視線の先にスポット ライトで、テキスト バーの強調表示を表示します。</span><span class="sxs-lookup"><span data-stu-id="b64d2-190">Text bar highlights with spotlight reveal on gaze anywhere on text</span></span>
 * <span data-ttu-id="b64d2-191">強調表示されているリスト項目に対してのみが、左側の視線の先の塗りつぶしのターゲットが常に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b64d2-191">Gaze fill target appears always on left, but only for the list item which is highlighted</span></span>
 * <span data-ttu-id="b64d2-192">積み上げ円の反復的な外観のため、すべてのドウェル対象を常に回避しようとしてください。</span><span class="sxs-lookup"><span data-stu-id="b64d2-192">Try to avoid having all dwell targets on at all times due to repetitive look of stacked circles</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="b64d2-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="b64d2-193">See also</span></span>
* [<span data-ttu-id="b64d2-194">直接操作</span><span class="sxs-lookup"><span data-stu-id="b64d2-194">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b64d2-195">ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="b64d2-195">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="b64d2-196">操作の基礎</span><span class="sxs-lookup"><span data-stu-id="b64d2-196">Interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="b64d2-197">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="b64d2-197">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="b64d2-198">視線入力と音声</span><span class="sxs-lookup"><span data-stu-id="b64d2-198">Gaze and voice</span></span>](voice-design.md)
