---
title: マルチ モーダルな相互作用の概要
description: マルチ モーダルな相互作用の概要
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 実際には、視線の先、対象とする操作、視線の先を混合設計、hololens、MMR、マルチ モーダル
ms.openlocfilehash: 9d0e639d7474c7e8728282acfa8d288cfeec7043
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974905"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="90f15-104">Instinctual 相互作用の概要</span><span class="sxs-lookup"><span data-stu-id="90f15-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="90f15-105">シンプルで instinctual の相互作用の理念はハードウェアのソフトウェアから、Microsoft Mixed Reality (MMR) プラットフォーム全体でウォーブンします。</span><span class="sxs-lookup"><span data-stu-id="90f15-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality (MMR) platform, from hardware to software.</span></span>

<span data-ttu-id="90f15-106">これらの instinctual 相互作用は、シームレスなマルチ モーダルな対話モデルでの徹底解剖の追跡、手の追跡、視線、および自然言語を含む、すべての利用可能な入力テクノロジを利用します。</span><span class="sxs-lookup"><span data-stu-id="90f15-106">These instinctual interactions utilize all available input technologies, including inside-out tracking, hand tracking, eye tracking, and natural language, in seamless multimodal interaction models.</span></span> <span data-ttu-id="90f15-107">調査、設計および開発に基づき multimodals、および 1 つの入力に基づいては重要な直感的な解決のエクスペリエンスを作成するときにします。</span><span class="sxs-lookup"><span data-stu-id="90f15-107">Based on our research, designing and developing multimodals, and not based on single inputs, is critical when creating instinctive experiences.</span></span>

<span data-ttu-id="90f15-108">Instinctual 相互作用モデルは、デバイスの種類も自然配置します。</span><span class="sxs-lookup"><span data-stu-id="90f15-108">The Instinctual Interaction models also naturally align across device types.</span></span>  <span data-ttu-id="90f15-109">たとえば、コント ローラーの自由度が 6、イマーシブ ヘッドセットの相手側の対話と HoloLens 2 での相手側の対話は、同じアフォー、パターン、および動作を使用します。</span><span class="sxs-lookup"><span data-stu-id="90f15-109">For example, far interaction on an immersive headset with a 6 degrees of freedom (DoF) controller and far interaction on a HoloLens 2 use the same affordances, patterns, and behaviors.</span></span>  <span data-ttu-id="90f15-110">だけでなく、この便利の開発者とデザイナーが、エンドユーザーに自然な感覚です。</span><span class="sxs-lookup"><span data-stu-id="90f15-110">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span>


<span data-ttu-id="90f15-111">最後に、何千もの効率が高く、魅力的であることと、魔法のような相互作用を設定 MR で可能であることを意図的に採用 1 回の操作モデルでは、エンド ツー エンドを認識している間に、アプリケーションはユーザーが成功したことを確認する最善の方法と優れたエクスペリエンスを実現します。</span><span class="sxs-lookup"><span data-stu-id="90f15-111">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="90f15-112">そのために、この操作ガイドの次の 3 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="90f15-112">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="90f15-113">この 3 つの主要な対話モデルとコンポーネント、および各に必要なパターンのガイダンスを構成しましたしました</span><span class="sxs-lookup"><span data-stu-id="90f15-113">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="90f15-114">当社のプラットフォームを提供するその他の特典に関する補足的なガイダンスが掲載されています</span><span class="sxs-lookup"><span data-stu-id="90f15-114">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="90f15-115">シナリオでは、適切な対話モデルを選択できるようにするためのガイダンスが掲載されています</span><span class="sxs-lookup"><span data-stu-id="90f15-115">We've included guidance to help select the appropriate interaction model for your scenario</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="90f15-116">マルチ モーダルな相互作用モデル</span><span class="sxs-lookup"><span data-stu-id="90f15-116">Multimodal interaction models</span></span>

<span data-ttu-id="90f15-117">マイクロソフトの調査と日付に顧客と連携に基づいて、多数の複合現実エクスペリエンスに合わせて次の 3 つの主要な対話モデルが見つかりました。</span><span class="sxs-lookup"><span data-stu-id="90f15-117">Based on our research and work with customers to date, we've discovered three primary interaction models that suit the majority of Mixed Reality experiences.</span></span>  

<span data-ttu-id="90f15-118">これらの相互作用モデル、フローを完了するため、ユーザーのメンタル モデルと考えます。</span><span class="sxs-lookup"><span data-stu-id="90f15-118">Think of these interaction models as the user's mental model for completing their flows.</span></span>

<span data-ttu-id="90f15-119">これらの相互作用モデルの各は便利な強力かつ独自の権限で使用できるし、一連の顧客のニーズのすべて最適化されています。</span><span class="sxs-lookup"><span data-stu-id="90f15-119">Each of these interaction models is convenient, powerful, and usable in its own right, and all are optimized for a set of customer needs.</span></span> <span data-ttu-id="90f15-120">グラフの下、シナリオ、例、および各相互作用モデルの利点を表示します。</span><span class="sxs-lookup"><span data-stu-id="90f15-120">View the chart below, for scenarios, examples, and benefits of each interaction model.</span></span>  

<span data-ttu-id="90f15-121">**[モデル]**</span><span class="sxs-lookup"><span data-stu-id="90f15-121">**Model**</span></span> | <span data-ttu-id="90f15-122">**[手およびツール](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-and-tools)**</span><span class="sxs-lookup"><span data-stu-id="90f15-122">**[Hands and Tools](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-and-tools)**</span></span> | <span data-ttu-id="90f15-123">**[楽します。](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-free)**</span><span class="sxs-lookup"><span data-stu-id="90f15-123">**[Hands free](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-free)**</span></span> | <span data-ttu-id="90f15-124">**[視線入力とコミット](https://docs.microsoft.com/en-us/windows/mixed-reality/gaze-and-commit?)**</span><span class="sxs-lookup"><span data-stu-id="90f15-124">**[Gaze and Commit](https://docs.microsoft.com/en-us/windows/mixed-reality/gaze-and-commit?)**</span></span>
|--------- | --------------| ------------| ---------|
<span data-ttu-id="90f15-125">**シナリオ例**</span><span class="sxs-lookup"><span data-stu-id="90f15-125">**Example Scenarios**</span></span> | <span data-ttu-id="90f15-126">3D 空間エクスペリエンス、spatial などのレイアウトとデザイン、コンテンツの操作、またはシミュレーション</span><span class="sxs-lookup"><span data-stu-id="90f15-126">3D spatial experiences, e.g. spatial layout and design, content manipulation, or simulation</span></span> | <span data-ttu-id="90f15-127">コンテキスト対応のエクスペリエンスをユーザーの手占有されているなど、ジョブのメンテナンスを学習します。</span><span class="sxs-lookup"><span data-stu-id="90f15-127">Contextual experiences where a user's hands are occupied, e.g. on the-job learning, maintenance</span></span>| <span data-ttu-id="90f15-128">クリックスルー エクスペリエンス、3 D のプレゼンテーション、デモなど</span><span class="sxs-lookup"><span data-stu-id="90f15-128">Click-through experiences, e.g. 3D presentations, demos</span></span>
<span data-ttu-id="90f15-129">**サイズに合わせて**</span><span class="sxs-lookup"><span data-stu-id="90f15-129">**Fit**</span></span> | <span data-ttu-id="90f15-130">追跡またはヘッド視線の先を新しいユーザーは、結合された wit の音声に適していますに注目します。</span><span class="sxs-lookup"><span data-stu-id="90f15-130">Great for new users, coupled wit voice, eye tracking or head gaze.</span></span> <span data-ttu-id="90f15-131">習得が。</span><span class="sxs-lookup"><span data-stu-id="90f15-131">Low learning curve.</span></span> <span data-ttu-id="90f15-132">追跡と 6 の自由度のコント ローラーの間で一貫性のある UX。</span><span class="sxs-lookup"><span data-stu-id="90f15-132">Consistent UX across hand tracking and 6 DoF controllers.</span></span> | <span data-ttu-id="90f15-133">いくつか必要な学習します。</span><span class="sxs-lookup"><span data-stu-id="90f15-133">Some learning required.</span></span> <span data-ttu-id="90f15-134">手が音声と自然言語でうまく使用できないペアである場合</span><span class="sxs-lookup"><span data-stu-id="90f15-134">If hands are unavailable pairs well with voice and natural language</span></span> | <span data-ttu-id="90f15-135">Mobile ではなく HMDs のトレーニングが必要です。</span><span class="sxs-lookup"><span data-stu-id="90f15-135">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="90f15-136">アクセス可能なコント ローラーに最も適した HoloLens に最適な (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="90f15-136">Best for accessible controllers Best for HoloLens (1st gen)</span></span> |
<span data-ttu-id="90f15-137">**ハードウェア**</span><span class="sxs-lookup"><span data-stu-id="90f15-137">**Hardware**</span></span> | <span data-ttu-id="90f15-138">HoloLens 2 イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="90f15-138">HoloLens 2 Immersive headsets</span></span> | <span data-ttu-id="90f15-139">HoloLens 2 HoloLens (第 1 世代) イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="90f15-139">HoloLens 2 HoloLens (1st gen) Immersive headsets</span></span> | <span data-ttu-id="90f15-140">HoloLens 2 イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="90f15-140">HoloLens 2 Immersive headsets</span></span> | <span data-ttu-id="90f15-141">HoloLens 2 HoloLens (第 1 世代) イマーシブ ヘッドセット Mobile AR</span><span class="sxs-lookup"><span data-stu-id="90f15-141">HoloLens 2 HoloLens (1st gen) Immersive headsets Mobile AR</span></span> |

<span data-ttu-id="90f15-142">各対話モデルでシームレスに使用できるすべての入力を使用するための詳細については、図と、Unity MRTK からサンプルのコンテンツへのリンクと、次のページで です。</span><span class="sxs-lookup"><span data-stu-id="90f15-142">Detailed information for using all available inputs seamlessly together in each interaction model is on the pages that follow, as well as illustrations and links to sample content from our Unity MRTK.</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="90f15-143">お客様の相互作用モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="90f15-143">Choose an interaction model for your customer</span></span>


<span data-ttu-id="90f15-144">ほとんどの場合、開発者および作成者もが既にあるいくつかのアイデアの相互作用のエクスペリエンス、ユーザーが希望の種類に注意してください。</span><span class="sxs-lookup"><span data-stu-id="90f15-144">Most likely, developers and creators also already have some ideas in mind of the kinds of interaction experience they want their users to have.</span></span>
<span data-ttu-id="90f15-145">設計する顧客中心のアプローチをぜひお勧めします以下のガイダンスに従って、顧客向けに最適化された相互作用モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="90f15-145">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="90f15-146">このガイダンスに従うなぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="90f15-146">Why follow this guidance?</span></span>

* <span data-ttu-id="90f15-147">目標と物理的および cognitive 労力、intuitiveness、learnability などの主観的な基準に、相互作用モデルがテストされます。</span><span class="sxs-lookup"><span data-stu-id="90f15-147">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="90f15-148">相互作用が異なるため、ビジュアルおよびオーディオ アフォーとオブジェクトの動作異なる可能性がありますも相互作用モデル。</span><span class="sxs-lookup"><span data-stu-id="90f15-148">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="90f15-149">複数の操作モデルの一部をまとめて結合の重荷となっており、ユーザーが混乱する同時手光線と head 注視カーソルなどの競合アフォーのリスクを作成します。</span><span class="sxs-lookup"><span data-stu-id="90f15-149">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor, which overwhelm and confuse users.</span></span>

<span data-ttu-id="90f15-150">相互作用モデルごとにアフォーと動作を最適化する方法の例をいくつかを示します。</span><span class="sxs-lookup"><span data-stu-id="90f15-150">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="90f15-151">よく見られる新しいユーザーのような質問については、としてなど"知る方法は、システムが動作している知る方法は何ができるかを知る方法は私が先ほどが認識されるとでしょうか"。</span><span class="sxs-lookup"><span data-stu-id="90f15-151">We often see new users as similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="90f15-152"><strong>[モデル]</strong></span><span class="sxs-lookup"><span data-stu-id="90f15-152"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="90f15-153"><strong>知る方法が動作しますか?</strong></span><span class="sxs-lookup"><span data-stu-id="90f15-153"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="90f15-154"><strong>何ができるかを知る方法</strong></span><span class="sxs-lookup"><span data-stu-id="90f15-154"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="90f15-155"><strong>先ほど行った何かを確認する方法</strong></span><span class="sxs-lookup"><span data-stu-id="90f15-155"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="90f15-156"><a href="hands-and-tools.md">手およびツール</a></span><span class="sxs-lookup"><span data-stu-id="90f15-156"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="90f15-157">メッシュ手の形を表示、指先アフォー ダンスまたは手の形の表示]、[コント ローラー光線します。</span><span class="sxs-lookup"><span data-stu-id="90f15-157">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="90f15-158">Grabbable ハンドルまたは手が近くにある場合、表示境界ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="90f15-158">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="90f15-159">音を再生し、グラブとリリースのアニメーションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="90f15-159">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="90f15-160"><a href="gaze-and-commit.md">頭の視線入力とコミット</a></span><span class="sxs-lookup"><span data-stu-id="90f15-160"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="90f15-161">フィールドのビューの中央にカーソルが参照してください。</span><span class="sxs-lookup"><span data-stu-id="90f15-161">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="90f15-162">Head 注視カーソルでは、特定のオブジェクトの上に置いたときの状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="90f15-162">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="90f15-163">私を参照してください/処理を行うときに、音声と視覚的に確認メッセージを聞きます。</span><span class="sxs-lookup"><span data-stu-id="90f15-163">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="90f15-164"><a href="hands-free.md">ハンズフリー (ヘッド注視およびドウェル)</a></span><span class="sxs-lookup"><span data-stu-id="90f15-164"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="90f15-165">フィールドのビューの中央にカーソルが参照してください。</span><span class="sxs-lookup"><span data-stu-id="90f15-165">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="90f15-166">進行状況インジケーターが表示されるは、対話型のオブジェクトについて熟考するとします。</span><span class="sxs-lookup"><span data-stu-id="90f15-166">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="90f15-167">私を参照してください/処理を行うときに、音声と視覚的に確認メッセージを聞きます。</span><span class="sxs-lookup"><span data-stu-id="90f15-167">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="90f15-168"><a href="hands-free.md">楽に (音声コマンドの実行)</a></span><span class="sxs-lookup"><span data-stu-id="90f15-168"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="90f15-169">インジケーターをリッスンしていると、システムの音を表示するキャプションで表示します。</span><span class="sxs-lookup"><span data-stu-id="90f15-169">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="90f15-170">音声プロンプトとヒントを取得します。</span><span class="sxs-lookup"><span data-stu-id="90f15-170">I get voice prompts and hints.</span></span>  <span data-ttu-id="90f15-171">「どのような音声」言ったとき</span><span class="sxs-lookup"><span data-stu-id="90f15-171">When I say "what can I say?"</span></span> <span data-ttu-id="90f15-172">フィードバックを表示します。</span><span class="sxs-lookup"><span data-stu-id="90f15-172">I see feedback.</span></span></td>
        <td><span data-ttu-id="90f15-173">私を参照してください/をコマンドでは、曖昧性除去必要なときに、UX を取得するか、音声と視覚的に確認メッセージを聞きます。</span><span class="sxs-lookup"><span data-stu-id="90f15-173">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="90f15-174">わかりましたヘルプ チームの選択、相互作用モデル質問を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90f15-174">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="90f15-175">Q:ユーザーはホログラムをタッチし、有効桁数ホログラフィック操作を実行しますか。</span><span class="sxs-lookup"><span data-stu-id="90f15-175">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="90f15-176">A:そうである場合は、有効桁数を対象として、手やアニメーション コント ローラーを使用した操作の手とツールの対話モデルを確認します。</span><span class="sxs-lookup"><span data-stu-id="90f15-176">A:  If so, check out the Hands and tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="90f15-177">Q:ユーザーは、無料の実際のタスク、手を保持する必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="90f15-177">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span><br><br>
<span data-ttu-id="90f15-178">A:そうである場合を見てハンズフリー対話モデル注視し、音声ベースの対話を通じての楽に優れたエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="90f15-178">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="90f15-179">Q:ユーザーが、複合現実アプリケーションの相互作用の学習に時間または必要がある最下位の学習曲線との対話ことでしょうか。</span><span class="sxs-lookup"><span data-stu-id="90f15-179">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="90f15-180">A:最下位の学習曲線と最も直感的な間のやり取りの手とツールのモデルは、ユーザーは、相互作用に手を使用する限り、お勧めします。</span><span class="sxs-lookup"><span data-stu-id="90f15-180">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="90f15-181">Q:ユーザーは、ポイント、および操作のモーションのコント ローラーを使用するか。</span><span class="sxs-lookup"><span data-stu-id="90f15-181">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="90f15-182">A:手およびツールのモデルには、アニメーション コント ローラーですばらしい体験のすべてのガイダンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="90f15-182">A:  The Hands and tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="90f15-183">Q:アクセシビリティのコント ローラーまたは一般的な Bluetooth コント ローラーの場合、clicker など、ユーザーは使用でしょうか。</span><span class="sxs-lookup"><span data-stu-id="90f15-183">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="90f15-184">A:すべての非追跡コント ローラーの Head 注視とコミットのモデルをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="90f15-184">A:  We recommend the Head-gaze and Commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="90f15-185">単純な「ターゲットとコミット」整備士のエクスペリエンス全体を走査できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="90f15-185">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="90f15-186">Q:自分のユーザーのみ進行状況エクスペリエンスを通じて「クリック」することにより (たとえば、3 d のスライド ショーのような環境で)、密度の高いレイアウトの UI コントロールを移動するとは対照的ですか。</span><span class="sxs-lookup"><span data-stu-id="90f15-186">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="90f15-187">A:ユーザーは、UI の多くを制御する必要はありません場合、Head 注視し、コミットでユーザーを対象設定について心配する必要はありません learnable オプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="90f15-187">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="90f15-188">Q:ユーザーが両方 HoloLens を使用して (第 1 世代) と HoloLens 2/Windows 没入型 (VR ヘッドセット)</span><span class="sxs-lookup"><span data-stu-id="90f15-188">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets)</span></span><br><br>
<span data-ttu-id="90f15-189">A:Head 注視し、コミットは HoloLens の相互作用モデルであるため (第 1 世代) ことをお勧め creators HoloLens をサポートする (第 1 世代) がヘッド視線の先を使用し、機能やユーザーが、HoloLens で発生するモードをコミット (第 1 世代) ヘッドセット。</span><span class="sxs-lookup"><span data-stu-id="90f15-189">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="90f15-190">次のセクションを参照してくださいで*相互作用モデルの移行*HoloLens の複数の世代の優れたエクスペリエンスの方法の詳細について。</span><span class="sxs-lookup"><span data-stu-id="90f15-190">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="90f15-191">Q:については、(大きな領域をカバーするまたはスペース間での移動)、通常、モバイル ユーザーの 1 つのスペースで作業するユーザーとでしょうか。</span><span class="sxs-lookup"><span data-stu-id="90f15-191">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="90f15-192">A:相互作用モデルのいずれでも、これらのユーザーの動作します。</span><span class="sxs-lookup"><span data-stu-id="90f15-192">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="90f15-193">アプリの設計に固有のガイダンスについて[近日](index.md#news-and-notes)します。</span><span class="sxs-lookup"><span data-stu-id="90f15-193">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="90f15-194">遷移の相互作用モデル</span><span class="sxs-lookup"><span data-stu-id="90f15-194">Transition interaction models</span></span>
<span data-ttu-id="90f15-195">場所、ユース ケースが必要があります 1 つ以上の相互作用モデルを使用している場合もあります。</span><span class="sxs-lookup"><span data-stu-id="90f15-195">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="90f15-196">たとえば、フロー、アプリの"作成"手とツールの対話モデルを利用してが楽にモードを現場技術者の雇用します。</span><span class="sxs-lookup"><span data-stu-id="90f15-196">For example, your app's "creation flow" utilizes the Hands and tools interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="90f15-197">お客様のエクスペリエンスが複数の操作モデルを必要とする場合は、多くのエンドユーザー間 - 初心者様にはエンドユーザーに対して特に 1 つのモデルから移行難易度は発生可能性があります、わかりました。</span><span class="sxs-lookup"><span data-stu-id="90f15-197">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially end users who are new to MR.</span></span>

> [!Note]
> <span data-ttu-id="90f15-198">ガイドの設計者や MR で難しい場合がありますの選択は、開発者のため、複数の操作モデルを使用するための詳細ガイダンスに取り組んでいるところです。</span><span class="sxs-lookup"><span data-stu-id="90f15-198">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="90f15-199">関連項目</span><span class="sxs-lookup"><span data-stu-id="90f15-199">See also</span></span>
* [<span data-ttu-id="90f15-200">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="90f15-200">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="90f15-201">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="90f15-201">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="90f15-202">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="90f15-202">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="90f15-203">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="90f15-203">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="90f15-204">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="90f15-204">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="90f15-205">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="90f15-205">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="90f15-206">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="90f15-206">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="90f15-207">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="90f15-207">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="90f15-208">空間マッピングの設計</span><span class="sxs-lookup"><span data-stu-id="90f15-208">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="90f15-209">快適性</span><span class="sxs-lookup"><span data-stu-id="90f15-209">Comfort</span></span>](comfort.md)

