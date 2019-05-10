---
title: マルチ モーダルな相互作用の概要
description: マルチ モーダルな相互作用の概要
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
keywords: 複合現実、視線の先を対象とする操作、視線の先をデザインします。
ms.openlocfilehash: c762518a224138dab248670eaef23ccb92016fce
ms.sourcegitcommit: a4a53e6772805d89a47588857e3e8fb1fd8d9710
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469104"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="2975f-104">Instinctual 相互作用の概要</span><span class="sxs-lookup"><span data-stu-id="2975f-104">Introducing instinctual interactions</span></span>
<span data-ttu-id="2975f-105">Instinctual、シンプルな相互作用の理念は、マイクロソフトの複合現実プラットフォーム全体で生み出します。</span><span class="sxs-lookup"><span data-stu-id="2975f-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="2975f-106">アプリケーションの設計者や開発者は、顧客向けの簡単で直感的な相互作用を提供できることを確認する 3 つの手順を使用しました。</span><span class="sxs-lookup"><span data-stu-id="2975f-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="2975f-107">最初に、シームレスなマルチ モーダルな対話モデルに、驚くようなセンサーと手の追跡、視線、自然言語など、入力のテクノロジを組み合わせることを確認しています。</span><span class="sxs-lookup"><span data-stu-id="2975f-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="2975f-108">1 つの入力に基づいていないを設計して multimodally--を開発し、調査に基づき--instinctual エクスペリエンスを作成するキー。</span><span class="sxs-lookup"><span data-stu-id="2975f-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="2975f-109">次に、認識して多くの開発者が、複数のデバイスをターゲット HoloLens 2 および HoloLens のことを意味するかどうか (第 1 世代) または HoloLens、VR します。</span><span class="sxs-lookup"><span data-stu-id="2975f-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="2975f-110">したがって、相互作用モデル (入力のテクノロジは、各デバイスでは異なります) 場合でも、デバイス間で作業を設計しました。</span><span class="sxs-lookup"><span data-stu-id="2975f-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="2975f-111">たとえば、6 dof コント ローラーと Windows イマーシブ ヘッドセットで相手側の対話と両方の HoloLens 2 での相手側の対話は同一アフォーとパターンを簡単にクロス デバイス アプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="2975f-111">For example, far interaction on a Windows Immersive headset with a 6DOF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="2975f-112">だけでなく、この便利の開発者とデザイナーが、エンドユーザーに自然な感覚です。</span><span class="sxs-lookup"><span data-stu-id="2975f-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="2975f-113">最後に、何千もの効率が高く、魅力的であることと、魔法のような相互作用を設定 MR で可能であることを意図的に採用 1 回の操作モデルでは、エンド ツー エンドを認識している間に、アプリケーションはユーザーが成功したことを確認する最善の方法と優れたエクスペリエンスを実現します。</span><span class="sxs-lookup"><span data-stu-id="2975f-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="2975f-114">そのために、この操作ガイドの次の 3 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="2975f-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="2975f-115">この 3 つの主要な対話モデルとコンポーネント、および各に必要なパターンのガイダンスを構成しましたしました</span><span class="sxs-lookup"><span data-stu-id="2975f-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="2975f-116">当社のプラットフォームを提供するその他の特典に関する補足的なガイダンスが掲載されています</span><span class="sxs-lookup"><span data-stu-id="2975f-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="2975f-117">シナリオでは、適切な対話モデルを選択できるようにするためのガイダンスが掲載されています</span><span class="sxs-lookup"><span data-stu-id="2975f-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>


## <a name="three-multimodal-interaction-models"></a><span data-ttu-id="2975f-118">次の 3 つのマルチ モーダルな相互作用モデル</span><span class="sxs-lookup"><span data-stu-id="2975f-118">Three multimodal interaction models</span></span>
<span data-ttu-id="2975f-119">マイクロソフトの調査と日付に顧客と連携に基づいて、3 つの主要な対話モデルが複合現実エクスペリエンスの大部分を合わせてが見つかりました。</span><span class="sxs-lookup"><span data-stu-id="2975f-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of Mixed Reality experiences.</span></span>

<span data-ttu-id="2975f-120">多くの点では、相互作用モデルは、そのフローを完了するため、ユーザーのメンタル モデルをします。</span><span class="sxs-lookup"><span data-stu-id="2975f-120">In many ways, the interaction model  is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="2975f-121">各相互作用モデルは、顧客のニーズの一連の最適化され、それぞれが便利な強力かつそれ自体で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2975f-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="2975f-122">次の表は、簡単な概要です。</span><span class="sxs-lookup"><span data-stu-id="2975f-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="2975f-123">各相互作用モデルを使用するための詳細については、イメージ、およびコード サンプルでは、下のページにリンクされます。</span><span class="sxs-lookup"><span data-stu-id="2975f-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span>  

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2975f-124"><strong>[モデル]</strong></span><span class="sxs-lookup"><span data-stu-id="2975f-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="2975f-125"><strong>シナリオ例</strong></span><span class="sxs-lookup"><span data-stu-id="2975f-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="2975f-126"><strong>サイズに合わせて</strong></span><span class="sxs-lookup"><span data-stu-id="2975f-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="2975f-127"><strong>ハードウェア</strong></span><span class="sxs-lookup"><span data-stu-id="2975f-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2975f-128"><a href="hands-and-tools.md">手およびツール</a></span><span class="sxs-lookup"><span data-stu-id="2975f-128"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="2975f-129">3D 空間エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="2975f-129">3D spatial experiences</span></span><br><span data-ttu-id="2975f-130">空間のレイアウトとデザイン、コンテンツの操作、またはシミュレーションなど</span><span class="sxs-lookup"><span data-stu-id="2975f-130">e.g. spatial layout and design, content manipulation, or simulation</span></span></td>
        <td><span data-ttu-id="2975f-131">新しいユーザーに適しています</span><span class="sxs-lookup"><span data-stu-id="2975f-131">Great for new users</span></span><br><span data-ttu-id="2975f-132">習得</span><span class="sxs-lookup"><span data-stu-id="2975f-132">Low learning curve</span></span><br><span data-ttu-id="2975f-133">基盤の簡単な visual アフォー</span><span class="sxs-lookup"><span data-stu-id="2975f-133">Grounded in easy visual affordances</span></span><br><span data-ttu-id="2975f-134">追跡と 6 の自由度のコント ローラーの間で一貫性のあるユーザー エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="2975f-134">Consistent UX across hand tracking and 6 DoF controllers</span></span><br><span data-ttu-id="2975f-135">優れたの音声と組み合わせると、追跡、監視または head 視線します。</span><span class="sxs-lookup"><span data-stu-id="2975f-135">Great when coupled with voice, eye tracking, or head gaze</span></span></td>
        <td><span data-ttu-id="2975f-136">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2975f-136">HoloLens 2</span></span><br><span data-ttu-id="2975f-137">6 dof コント ローラーを使用した没入型の Windows</span><span class="sxs-lookup"><span data-stu-id="2975f-137">Windows Immersive w/ 6DOF Controllers</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2975f-138"><a href="hands-free.md">ハンズフリー</a></span><span class="sxs-lookup"><span data-stu-id="2975f-138"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="2975f-139">コンテキスト対応のエクスペリエンスをユーザーの手占有されているなど、ジョブのメンテナンスを学習します。</span><span class="sxs-lookup"><span data-stu-id="2975f-139">Contextual experiences where a user's hands are occupied e.g. on the-job learning, maintenance</span></span></td>
        <td><span data-ttu-id="2975f-140">いくつか必要な学習</span><span class="sxs-lookup"><span data-stu-id="2975f-140">Some learning required</span></span><br><span data-ttu-id="2975f-141">手が利用できない場合</span><span class="sxs-lookup"><span data-stu-id="2975f-141">If hands are unavailable</span></span><br><span data-ttu-id="2975f-142">音声および自然言語のペア</span><span class="sxs-lookup"><span data-stu-id="2975f-142">pairs well with voice and natural language</span></span></td>
        <td><span data-ttu-id="2975f-143">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2975f-143">HoloLens 2</span></span><br><span data-ttu-id="2975f-144">HoloLens (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="2975f-144">HoloLens (1st gen)</span></span><br> <span data-ttu-id="2975f-145">Windows の没入型</span><span class="sxs-lookup"><span data-stu-id="2975f-145">Windows Immersive</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2975f-146"><a href="gaze-and-commit.md">頭の視線入力とコミット</a></span><span class="sxs-lookup"><span data-stu-id="2975f-146"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="2975f-147">例: 3 D プレゼンテーション、デモが発生したクリック スルー</span><span class="sxs-lookup"><span data-stu-id="2975f-147">Click-through experiences e.g. 3D presentations, demos</span></span></td>
        <td><span data-ttu-id="2975f-148">Mobile ではなく HMDs のトレーニングが必要です。</span><span class="sxs-lookup"><span data-stu-id="2975f-148">Requires training on HMDs but not on mobile</span></span><br><span data-ttu-id="2975f-149">アクセス可能なコント ローラーに最も適した</span><span class="sxs-lookup"><span data-stu-id="2975f-149">Best for accessible controllers</span></span><br><span data-ttu-id="2975f-150">HoloLens の最適な (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="2975f-150">Best for HoloLens (1st gen)</span></span></td>
        <td><span data-ttu-id="2975f-151">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2975f-151">HoloLens 2</span></span><br><span data-ttu-id="2975f-152">HoloLens (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="2975f-152">HoloLens (1st gen)</span></span><br> <span data-ttu-id="2975f-153">Windows の没入型</span><span class="sxs-lookup"><span data-stu-id="2975f-153">Windows Immersive</span></span><br> <span data-ttu-id="2975f-154">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="2975f-154">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="2975f-155">ギャップやお客様のエクスペリエンスの相互作用に穴がないことを確認する最善の方法では、最初から最後までの 1 つのモデルの指示に従います。</span><span class="sxs-lookup"><span data-stu-id="2975f-155">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="2975f-156">設計と開発を高速化するには、詳細な情報とイメージ、およびコード サンプルへのリンクをカバレッジの各モデル内に含めています。</span><span class="sxs-lookup"><span data-stu-id="2975f-156">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="2975f-157">最初に、以下のセクションを選択し、これらの相互作用モデルのいずれかを実装する次の手順をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2975f-157">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="2975f-158">このページの目的は、ガイダンスを理解するのには。</span><span class="sxs-lookup"><span data-stu-id="2975f-158">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="2975f-159">お客様の相互作用モデルの選択</span><span class="sxs-lookup"><span data-stu-id="2975f-159">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="2975f-160">相互作用モデルのガイダンスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="2975f-160">Using the interaction model guidance</span></span>
* <span data-ttu-id="2975f-161">相互作用モデル間で移行</span><span class="sxs-lookup"><span data-stu-id="2975f-161">Transitioning between interaction models</span></span>
* <span data-ttu-id="2975f-162">次の手順を設計します。</span><span class="sxs-lookup"><span data-stu-id="2975f-162">Design next steps</span></span>

## <a name="choosing-an-interaction-model-for-your-customer"></a><span data-ttu-id="2975f-163">お客様の相互作用モデルの選択</span><span class="sxs-lookup"><span data-stu-id="2975f-163">Choosing an interaction model for your customer</span></span>

<span data-ttu-id="2975f-164">ほとんどの場合、開発者および作成者が既にあるいくつかのアイデア、ユーザー エクスペリエンスが相互作用の種類に注意してください。</span><span class="sxs-lookup"><span data-stu-id="2975f-164">Most likely, developers and creators already have some ideas in mind of the kinds of interaction experience they want for their users.</span></span>
<span data-ttu-id="2975f-165">設計する顧客中心のアプローチをぜひお勧めします以下のガイダンスに従って、顧客向けに最適化された相互作用モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2975f-165">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="2975f-166">このガイダンスに従うなぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2975f-166">Why follow this guidance?</span></span>

* <span data-ttu-id="2975f-167">目標と物理的および cognitive 労力、intuitiveness、learnability などの主観的な基準に、相互作用モデルがテストされます。</span><span class="sxs-lookup"><span data-stu-id="2975f-167">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="2975f-168">相互作用が異なるため、ビジュアルおよびオーディオ アフォーとオブジェクトの動作異なる可能性がありますも相互作用モデル。</span><span class="sxs-lookup"><span data-stu-id="2975f-168">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="2975f-169">複数の操作モデルの一部をまとめて結合などの重荷となっており、ユーザーが混乱する同時手光線と視線の先のカーソルでは、競合のアフォーのリスクを作成します。</span><span class="sxs-lookup"><span data-stu-id="2975f-169">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a gaze cursor, which overwhelm and confuse users.</span></span>

<span data-ttu-id="2975f-170">相互作用モデルごとにアフォーと動作を最適化する方法の例をいくつかを示します。</span><span class="sxs-lookup"><span data-stu-id="2975f-170">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="2975f-171">よく見られる新しいユーザーのような質問については、としてなど"知る方法は、システムが動作している知る方法は何ができるかを知る方法は私が先ほどが認識されるとでしょうか"。</span><span class="sxs-lookup"><span data-stu-id="2975f-171">We often see new users as similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2975f-172"><strong>[モデル]</strong></span><span class="sxs-lookup"><span data-stu-id="2975f-172"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="2975f-173"><strong>知る方法が動作しますか?</strong></span><span class="sxs-lookup"><span data-stu-id="2975f-173"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="2975f-174"><strong>何ができるかを知る方法</strong></span><span class="sxs-lookup"><span data-stu-id="2975f-174"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="2975f-175"><strong>先ほど行った何かを確認する方法</strong></span><span class="sxs-lookup"><span data-stu-id="2975f-175"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2975f-176"><a href="hands-and-tools.md">手およびツール</a></span><span class="sxs-lookup"><span data-stu-id="2975f-176"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="2975f-177">メッシュ手の形を表示、指先アフォー ダンスまたは手の形の表示]、[コント ローラー光線します。</span><span class="sxs-lookup"><span data-stu-id="2975f-177">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="2975f-178">Grabbable ハンドルまたは手が近くにある場合、表示境界ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2975f-178">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="2975f-179">音を再生し、グラブとリリースのアニメーションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2975f-179">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2975f-180"><a href="gaze-and-commit.md">頭の視線入力とコミット</a></span><span class="sxs-lookup"><span data-stu-id="2975f-180"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="2975f-181">フィールドのビューの中央にカーソルが参照してください。</span><span class="sxs-lookup"><span data-stu-id="2975f-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="2975f-182">視線の先のカーソルでは、特定のオブジェクトの上に置いたときの状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="2975f-182">The gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="2975f-183">私を参照してください/処理を行うときに、音声と視覚的に確認メッセージを聞きます。</span><span class="sxs-lookup"><span data-stu-id="2975f-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="2975f-184"><a href="hands-free.md">ハンズフリー (視線の先およびドウェル)</a></span><span class="sxs-lookup"><span data-stu-id="2975f-184"><a href="hands-free.md">Hands-free (Gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="2975f-185">フィールドのビューの中央にカーソルが参照してください。</span><span class="sxs-lookup"><span data-stu-id="2975f-185">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="2975f-186">進行状況インジケーターが表示されるは、対話型のオブジェクトについて熟考するとします。</span><span class="sxs-lookup"><span data-stu-id="2975f-186">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="2975f-187">私を参照してください/処理を行うときに、音声と視覚的に確認メッセージを聞きます。</span><span class="sxs-lookup"><span data-stu-id="2975f-187">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2975f-188"><a href="hands-free.md">楽に (音声コマンドの実行)</a></span><span class="sxs-lookup"><span data-stu-id="2975f-188"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="2975f-189">インジケーターをリッスンしていると、システムの音を表示するキャプションで表示します。</span><span class="sxs-lookup"><span data-stu-id="2975f-189">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="2975f-190">音声プロンプトとヒントを取得します。</span><span class="sxs-lookup"><span data-stu-id="2975f-190">I get voice prompts and hints.</span></span>  <span data-ttu-id="2975f-191">「どのような音声」言ったとき</span><span class="sxs-lookup"><span data-stu-id="2975f-191">When I say "what can I say?"</span></span> <span data-ttu-id="2975f-192">フィードバックを表示します。</span><span class="sxs-lookup"><span data-stu-id="2975f-192">I see feedback.</span></span></td>
        <td><span data-ttu-id="2975f-193">私を参照してください/をコマンドでは、曖昧性除去必要なときに、UX を取得するか、音声と視覚的に確認メッセージを聞きます。</span><span class="sxs-lookup"><span data-stu-id="2975f-193">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="2975f-194">わかりましたヘルプ チームの選択、相互作用モデル質問を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2975f-194">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="2975f-195">Q:ユーザーはホログラムをタッチし、有効桁数ホログラフィック操作を実行しますか。</span><span class="sxs-lookup"><span data-stu-id="2975f-195">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span>
<span data-ttu-id="2975f-196">A:そうである場合は、有効桁数を対象として、手やアニメーション コント ローラーを使用した操作の手とツールの対話モデルを確認します。</span><span class="sxs-lookup"><span data-stu-id="2975f-196">A:  If so, check out the Hands and Tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="2975f-197">Q:ユーザーは、無料の実際のタスク、手を保持する必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="2975f-197">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span>
<span data-ttu-id="2975f-198">A:そうである場合を見てハンズフリー対話モデル注視し、音声ベースの対話を通じての楽に優れたエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2975f-198">A:  If so, take a look at the Hands-Free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="2975f-199">Q:ユーザーが、複合現実アプリケーションの相互作用の学習に時間または必要がある最下位の学習曲線との対話ことでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2975f-199">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span>
<span data-ttu-id="2975f-200">A:最下位の学習曲線と最も直感的な間のやり取りの手とツールのモデルは、ユーザーは、相互作用に手を使用する限り、お勧めします。</span><span class="sxs-lookup"><span data-stu-id="2975f-200">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="2975f-201">Q:ユーザーは、ポイント、および操作のモーションのコント ローラーを使用するか。</span><span class="sxs-lookup"><span data-stu-id="2975f-201">Q:  Do my users use motion controllers for pointing and manipulation?</span></span>
<span data-ttu-id="2975f-202">A:手およびツールのモデルには、アニメーション コント ローラーですばらしい体験のすべてのガイダンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2975f-202">A:  The Hands and Tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="2975f-203">Q:アクセシビリティのコント ローラーまたは一般的な Bluetooth コント ローラーの場合、clicker など、ユーザーは使用でしょうか。</span><span class="sxs-lookup"><span data-stu-id="2975f-203">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span>
<span data-ttu-id="2975f-204">A:すべての非追跡コント ローラーの Head 注視とコミットのモデルをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2975f-204">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="2975f-205">単純な「ターゲットとコミット」整備士のエクスペリエンス全体を走査できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="2975f-205">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="2975f-206">Q:自分のユーザーのみ進行状況エクスペリエンスを通じて「クリック」することにより (たとえば、3 d のスライド ショーのような環境で)、密度の高いレイアウトの UI コントロールを移動するとは対照的ですか。</span><span class="sxs-lookup"><span data-stu-id="2975f-206">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span>
<span data-ttu-id="2975f-207">A:ユーザーは、UI の多くを制御する必要はありません場合、Head 注視し、コミットでユーザーを対象設定について心配する必要はありません learnable オプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="2975f-207">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="2975f-208">Q:ユーザーが両方 HoloLens を使用して (第 1 世代) と HoloLens 2/Windows 没入型 (VR ヘッドセット) a:Head 注視し、コミットは HoloLens の相互作用モデルであるため (第 1 世代) ことをお勧め creators HoloLens をサポートする (第 1 世代) がヘッド視線の先を使用し、機能やユーザーが、HoloLens で発生するモードをコミット (第 1 世代) ヘッドセット。</span><span class="sxs-lookup"><span data-stu-id="2975f-208">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets) A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="2975f-209">次のセクションを参照してくださいで*相互作用モデルの移行*HoloLens の複数の世代の優れたエクスペリエンスの方法の詳細について。</span><span class="sxs-lookup"><span data-stu-id="2975f-209">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="2975f-210">Q:については、(大きな領域をカバーするまたはスペース間での移動)、通常、モバイル ユーザーの 1 つのスペースで作業するユーザーとでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2975f-210">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span>  
<span data-ttu-id="2975f-211">A:相互作用モデルのいずれでも、これらのユーザーの動作します。</span><span class="sxs-lookup"><span data-stu-id="2975f-211">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="2975f-212">アプリの設計に固有のガイダンスについて[近日](index.md#news-and-notes)します。</span><span class="sxs-lookup"><span data-stu-id="2975f-212">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="2975f-213">遷移の相互作用モデル</span><span class="sxs-lookup"><span data-stu-id="2975f-213">Transition interaction models</span></span>
<span data-ttu-id="2975f-214">場所、ユース ケースが必要があります 1 つ以上の相互作用モデルを使用している場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2975f-214">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="2975f-215">たとえば、フロー、アプリの"作成"手とツールの対話モデルを利用してが楽にモードを現場技術者の雇用します。</span><span class="sxs-lookup"><span data-stu-id="2975f-215">For example, your app's "creation flow" utilizes the Hands and tools interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="2975f-216">お客様のエクスペリエンスが複数の操作モデルを必要とする場合は、多くのエンドユーザー間 - 初心者様にはエンドユーザーに対して特に 1 つのモデルから移行難易度は発生可能性があります、わかりました。</span><span class="sxs-lookup"><span data-stu-id="2975f-216">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially end users who are new to MR.</span></span>

> [!Note]
> <span data-ttu-id="2975f-217">ガイドの設計者や MR で難しい場合がありますの選択は、開発者のため、複数の操作モデルを使用するための詳細ガイダンスに取り組んでいるところです。</span><span class="sxs-lookup"><span data-stu-id="2975f-217">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="2975f-218">関連項目</span><span class="sxs-lookup"><span data-stu-id="2975f-218">See also</span></span>
* [<span data-ttu-id="2975f-219">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="2975f-219">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="2975f-220">直接操作</span><span class="sxs-lookup"><span data-stu-id="2975f-220">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="2975f-221">ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="2975f-221">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="2975f-222">視線入力ターゲット設定</span><span class="sxs-lookup"><span data-stu-id="2975f-222">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="2975f-223">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="2975f-223">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="2975f-224">音声設計</span><span class="sxs-lookup"><span data-stu-id="2975f-224">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="2975f-225">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="2975f-225">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="2975f-226">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="2975f-226">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="2975f-227">空間マッピングの設計</span><span class="sxs-lookup"><span data-stu-id="2975f-227">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="2975f-228">快適性</span><span class="sxs-lookup"><span data-stu-id="2975f-228">Comfort</span></span>](comfort.md)
