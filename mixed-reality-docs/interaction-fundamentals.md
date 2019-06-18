---
title: マルチモーダル操作の概要
description: マルチモーダル操作の概要
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 視線入力, 視線入力ターゲット設定, 対話, 設計, HoloLens, MMR, マルチモーダル
ms.openlocfilehash: bea205edf484a55db701e8e0d1a233234882a272
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516020"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="5b3fa-104">本能的な操作の概要</span><span class="sxs-lookup"><span data-stu-id="5b3fa-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="5b3fa-105">シンプルで本能的な操作の理念は、Microsoft Mixed Reality プラットフォーム全体に織り込まれています。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="5b3fa-106">アプリケーションのデザイナーや開発者が顧客向けに簡単で直感的な操作を提供できるように、3 つの手順を使用しています。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="5b3fa-107">1 つ目として、驚くべきセンサーと、手の追跡、視線追跡、自然言語などの入力のテクノロジをまとめることで、シームレスなマルチモーダル操作モデルを実現できるようにしました。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="5b3fa-108">調査に基づくと、本能的なエクスペリエンスを作成する鍵となるのは、単一の入力をベースとせず、マルチモーダルで設計や開発を行うことです。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="5b3fa-109">2 つ目として、HoloLens 2 と HoloLens (第 1 世代) のことを意味するのか、HoloLens と VR のことを意味するのかにはよらず、多くの開発者が複数のデバイスをターゲットにしていることを認識しています。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="5b3fa-110">そのため、デバイスによらない操作モデルを設計しています (入力テクノロジはデバイスによって異なります)。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="5b3fa-111">たとえば、6DOF コントローラーによる Windows イマーシブ ヘッドセットの遠隔インタラクションや、HoloLens 2 での遠隔インタラクションは、どちらも同じアフォーダンスとパターンを使用しているので、クロス デバイス アプリケーションで簡単に活用できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-111">For example, far interaction on a Windows Immersive headset with a 6DOF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="5b3fa-112">これは、開発者やデザイナーにとって便利であるだけでなく、エンドユーザーにとって自然です。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="5b3fa-113">最後に、MR では効果的、魅力的で魔法のような何千もの操作が実現できますが、ユーザーが成功と優れたエクスペリエンスを実感できる最善の方法は、アプリケーションで意図的にエンドツーエンドの単一操作モデルを使用することであることがわかっています。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="5b3fa-114">そのため、この操作ガイドに次の 3 つのことを含めました。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="5b3fa-115">このガイダンスは、この 3 つの主要な操作モデルと、それぞれに必要なコンポーネントとパターンを中心とした構造にしています。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="5b3fa-116">このプラットフォームが提供するその他のメリットに関する補足的なガイダンスを含めます。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="5b3fa-117">シナリオに適した操作モデルの選択に役立つガイダンスを含めます。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="5b3fa-118">マルチモーダル操作モデル</span><span class="sxs-lookup"><span data-stu-id="5b3fa-118">Multimodal interaction models</span></span>

<span data-ttu-id="5b3fa-119">これまで顧客とともに調査や作業を行ってきた結果から、3 つの主要な操作モデルは大半の Mixed Reality エクスペリエンスに適したものであることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="5b3fa-120">多くの点で、この操作モデルはユーザーのフローを完了するためのメンタル モデルです。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-120">In many ways, the interaction model is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="5b3fa-121">各操作モデルは、一連の顧客ニーズのために最適化されていて、それぞれが便利な強力かつそれ自体で使用できます。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="5b3fa-122">次の表は、簡単な概要です。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="5b3fa-123">各操作モデルを使用するための詳細情報は、イメージとコード サンプルを含むページにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5b3fa-124"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="5b3fa-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="5b3fa-125"><strong>シナリオ例</strong></span><span class="sxs-lookup"><span data-stu-id="5b3fa-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="5b3fa-126"><strong>適した使用方法</strong></span><span class="sxs-lookup"><span data-stu-id="5b3fa-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="5b3fa-127"><strong>ハードウェア</strong></span><span class="sxs-lookup"><span data-stu-id="5b3fa-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5b3fa-128"><a href="hands-and-tools.md">手とモーション コントローラー</a></span><span class="sxs-lookup"><span data-stu-id="5b3fa-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="5b3fa-129">空間レイアウトやデザインなどの 3D 空間エクスペリエンス、コンテンツの操作、またはシミュレーション。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-129">3D spatial experiences, e.g. spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="5b3fa-130">音声、視線追跡、頭の視線入力と組み合わせると、新しいユーザーに最適。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-130">Great for new users, coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="5b3fa-131">習得が容易。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-131">Low learning curve.</span></span> <span data-ttu-id="5b3fa-132">手の追跡と 6 DoF コントローラーで一貫性のある UX。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-132">Consistent UX across hand tracking and 6 DoF controllers.</span></span></td>
        <td><span data-ttu-id="5b3fa-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5b3fa-133">HoloLens 2</span></span><br><span data-ttu-id="5b3fa-134">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="5b3fa-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5b3fa-135"><a href="hands-free.md">ハンズフリー</a></span><span class="sxs-lookup"><span data-stu-id="5b3fa-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="5b3fa-136">仕事を通じた学習、メンテナンスなど、ユーザーの手が占有されている場合のコンテキスト対応のエクスペリエンス。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-136">Contextual experiences where a user's hands are occupied, e.g. on-the-job learning, maintenance.</span></span></td>
        <td><span data-ttu-id="5b3fa-137">いくらかの学習が必要。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-137">Some learning required.</span></span> <span data-ttu-id="5b3fa-138">手が使えない場合、音声や自然言語と組み合わせる。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-138">If hands are unavailable pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="5b3fa-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5b3fa-139">HoloLens 2</span></span><br><span data-ttu-id="5b3fa-140">HoloLens (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="5b3fa-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="5b3fa-141">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="5b3fa-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5b3fa-142"><a href="gaze-and-commit.md">頭の視線入力とコミット</a></span><span class="sxs-lookup"><span data-stu-id="5b3fa-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="5b3fa-143">3D プレゼンテーション、デモなどのクリック スルー エクスペリエンス。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="5b3fa-144">移動を除く HMD のトレーニングが必要。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="5b3fa-145">アクセシビリティ コントローラーに最適。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-145">Best for accessible controllers.</span></span> <span data-ttu-id="5b3fa-146">HoloLens (第 1 世代) に最適。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="5b3fa-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5b3fa-147">HoloLens 2</span></span><br><span data-ttu-id="5b3fa-148">HoloLens (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="5b3fa-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="5b3fa-149">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="5b3fa-149">Immersive headsets</span></span><br><span data-ttu-id="5b3fa-150">モバイル AR</span><span class="sxs-lookup"><span data-stu-id="5b3fa-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="5b3fa-151">エクスペリエンスの操作でギャップや穴をなくす最善の方法は、1 つのモデルのガイダンスに最初から最後まで従うことです。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-151">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="5b3fa-152">設計と開発を高速化するため、各モデルの説明には、詳細な情報とイメージやコード サンプルへのリンクを含めています。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-152">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="5b3fa-153">まず、以下のセクションでは、これらの操作モデルからいずれかを選択して実装する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-153">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="5b3fa-154">このページでは、以下についてのガイダンスを理解することができます。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="5b3fa-155">顧客の操作モデルの選択</span><span class="sxs-lookup"><span data-stu-id="5b3fa-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="5b3fa-156">操作モデルのガイダンスの使用</span><span class="sxs-lookup"><span data-stu-id="5b3fa-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="5b3fa-157">操作モデル間の遷移</span><span class="sxs-lookup"><span data-stu-id="5b3fa-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="5b3fa-158">次の手順の設計</span><span class="sxs-lookup"><span data-stu-id="5b3fa-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="5b3fa-159">顧客の操作モデルを選択する</span><span class="sxs-lookup"><span data-stu-id="5b3fa-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="5b3fa-160">ほとんどの場合、開発者や作成者は、ユーザーに提供する操作エクスペリエンスの種類について、既にいくつかのアイデアを持っています。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-160">Most likely, developers and creators also already have some ideas in mind of the kinds of interaction experience they want their users to have.</span></span>
<span data-ttu-id="5b3fa-161">顧客中心の設計アプローチをお勧めするために、以下のガイダンスに従って、顧客向けに最適化された操作モデルを選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-161">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="5b3fa-162">ガイダンスに従う理由</span><span class="sxs-lookup"><span data-stu-id="5b3fa-162">Why follow this guidance?</span></span>

* <span data-ttu-id="5b3fa-163">操作モデルは、物理効果、認識効果、直感性、学習性など、主観的および客観的な基準でテストされます。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-163">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="5b3fa-164">操作が異なるため、操作モデル間でビジュアルおよびオーディオ アフォーダンスやオブジェクトの動作は異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-164">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="5b3fa-165">複数の操作モデルの一部を組み合わせると、アフォーダンスが競合するリスクが生まれます。たとえば、手の光線と頭の視線入力のカーソルが同時に表示されると、ユーザーが混乱します。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-165">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor, which can overwhelm and confuse users.</span></span>

<span data-ttu-id="5b3fa-166">アフォーダンスと動作を最適化する例を操作モデルごとに示します。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="5b3fa-167">新しいユーザーが「システムが動作していることはどうすればわかりますか、何ができるかはどうすればわかりますか。自分がしたことをシステムが理解していることはどうすればわかりますか」といった同じような質問をしているのをよく見かけます。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5b3fa-168"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="5b3fa-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="5b3fa-169"><strong>動作していることはどうすればわかりますか?</strong></span><span class="sxs-lookup"><span data-stu-id="5b3fa-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="5b3fa-170"><strong>何ができるかはどうすればわかりますか?</strong></span><span class="sxs-lookup"><span data-stu-id="5b3fa-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="5b3fa-171"><strong>自分が何をしたかはどうすればわかりますか?</strong></span><span class="sxs-lookup"><span data-stu-id="5b3fa-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5b3fa-172"><a href="hands-and-tools.md">手とモーション コントローラー</a></span><span class="sxs-lookup"><span data-stu-id="5b3fa-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="5b3fa-173">手のメッシュが見える、指先アフォーダンスまたは手やコントローラーの光線が見える。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-173">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="5b3fa-174">手を近づけると、グラブ可能なハンドルや境界ボックスが表示される。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-174">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="5b3fa-175">音が聞こえ、グラブやリリースのアニメーションが見える。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5b3fa-176"><a href="gaze-and-commit.md">頭の視線入力とコミット</a></span><span class="sxs-lookup"><span data-stu-id="5b3fa-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="5b3fa-177">視野の中央にカーソルが見える。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="5b3fa-178">特定のオブジェクトに重ねると、頭の視線入力カーソルの状態が変わる。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-178">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="5b3fa-179">行動を行うと、視覚または音声でわかる。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-179">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="5b3fa-180"><a href="hands-free.md">ハンズフリー (頭の視線入力とドウェル)</a></span><span class="sxs-lookup"><span data-stu-id="5b3fa-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="5b3fa-181">視野の中央にカーソルが見える。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="5b3fa-182">インタラクティブなオブジェクトにドウェルすると、進行状況のインジケーターが見える。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="5b3fa-183">行動を行うと、視覚または音声でわかる。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5b3fa-184"><a href="hands-free.md">ハンズフリー (音声コマンド)</a></span><span class="sxs-lookup"><span data-stu-id="5b3fa-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="5b3fa-185">リスニング インジケーターとシステムが聞いた音を表示するキャプションが見える。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="5b3fa-186">音声プロンプトとヒントが聞こえる。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-186">I get voice prompts and hints.</span></span>  <span data-ttu-id="5b3fa-187">「何を言えますか?」と言うと</span><span class="sxs-lookup"><span data-stu-id="5b3fa-187">When I say "what can I say?"</span></span> <span data-ttu-id="5b3fa-188">フィードバックが得られる。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="5b3fa-189">コマンドを与えると、視覚または音声でわかる。必要な場合は不明瞭解消用の UX が提供される。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="5b3fa-190">ヘルプ チームが操作モデルを選択する際に使用している質問を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="5b3fa-191">Q:ユーザーがホログラムにタッチして細かい操作を行うことはありますか?</span><span class="sxs-lookup"><span data-stu-id="5b3fa-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="5b3fa-192">A:その場合は、厳密なターゲット指定や、手またはモーション コントローラーによる操作を行うために、手とツールの操作モデルを確認します。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-192">A:  If so, check out the Hands and tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="5b3fa-193">Q:ユーザーは、現実世界でタスクを行うために、手を空けておく必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="5b3fa-193">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span><br><br>
<span data-ttu-id="5b3fa-194">A:その場合は、ハンズフリー操作モデルを確認します。このモデルは、視線入力または音声ベースの操作で優れたハンズフリー エクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="5b3fa-195">Q:ユーザーには Mixed Reality アプリケーションの操作を学習する時間はありますか? それとも、最低限の学習で操作を行う必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="5b3fa-195">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="5b3fa-196">A:ユーザーが手で操作を行うことができ、最低限の学習で最も直感的に操作を行いたい場合は、手とツールのモデルをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-196">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="5b3fa-197">Q:ユーザーがポイントしたり操作したりする際、モーション コントローラーを使用しますか?</span><span class="sxs-lookup"><span data-stu-id="5b3fa-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="5b3fa-198">A:手とツールのモデルには、モーション コントローラーを使ってすばらしいエクスペリエンスを実現するためのガイダンスがすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-198">A:  The Hands and tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="5b3fa-199">Q:ユーザーは、アクセシビリティ コントローラーやクリッカーなどの一般的な Bluetooth コントローラーを使用しますか?</span><span class="sxs-lookup"><span data-stu-id="5b3fa-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="5b3fa-200">A:すべての非追跡コントローラーには、頭の視線入力とコミットのモデルをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-200">A:  We recommend the Head-gaze and Commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="5b3fa-201">ユーザーが単純な「ターゲット指定とコミット」機構によるエクスペリエンス全体を利用できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="5b3fa-202">Q:ユーザーは、UI コントロールが詰まったレイアウトを操作するのではなく、「クリックスルー」によってのみエクスペリエンスを進行させることができますか (たとえば、3D スライド ショーのような環境) ?</span><span class="sxs-lookup"><span data-stu-id="5b3fa-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="5b3fa-203">A:ユーザーが多くの UI を制御する必要がない場合は、頭の視線入力とコミットを使うと、ターゲットの指定について悩むことなく学習できるオプションを提供できます。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="5b3fa-204">Q:ユーザーは HoloLens (第 1 世代) と HoloLens 2/Windows イマーシブ (VR ヘッドセット) の両方を使用しますか?</span><span class="sxs-lookup"><span data-stu-id="5b3fa-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets)</span></span><br><br>
<span data-ttu-id="5b3fa-205">A:頭の視点入力とコミットは HoloLens (第 1 世代) の操作モデルであるため、HoloLens (第 1 世代) をサポートする作成者は、ユーザーが HoloLens (第 1 世代) ヘッドセットを使う可能性があるすべての機能やモードで、頭の視線入力とコミットを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="5b3fa-206">複数の世代の HoloLens で優れたエクスペリエンスを作成する詳しい方法については、*操作モデルの遷移*について取り上げた次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="5b3fa-207">Q:通常は移動可能 (広い領域をカバーする、またはスペース間を移動する) なユーザーと、1 つのスペースで作業することが多いユーザーを比較するとどうなりますか?</span><span class="sxs-lookup"><span data-stu-id="5b3fa-207">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="5b3fa-208">A:どの操作モデルでも、これらのユーザーに対応できます。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="5b3fa-209">アプリの設計に特化したガイダンスは、[近日中に公開](index.md#news-and-notes)します。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="5b3fa-210">操作モデルの遷移</span><span class="sxs-lookup"><span data-stu-id="5b3fa-210">Transition interaction models</span></span>
<span data-ttu-id="5b3fa-211">複数の操作モデルが必要になるユース ケースもあります。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-211">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="5b3fa-212">たとえば、アプリの「作成フロー」で手とモーション コントローラー操作モデルを利用しつつ、現場技術者向けにハンズフリー モードを使う場合などです。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-212">For example, your app's "creation flow" utilizes the Hands and motion controllers interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="5b3fa-213">エクスペリエンスに複数の操作モデルが必要な場合、ある操作モデルから別の操作モデルに遷移する際に、多くのエンドユーザーが困難を感じることがわかっています。特に、Mixed Reality を初めて使用するユーザーはそれが顕著です。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-213">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="5b3fa-214">デザイナーや開発者が MR で難しくなる可能性がある選択を行う際に役立つように、現在、複数の操作モデルを使用するための詳細ガイダンスの作成を進めています。</span><span class="sxs-lookup"><span data-stu-id="5b3fa-214">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="5b3fa-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b3fa-215">See also</span></span>
* [<span data-ttu-id="5b3fa-216">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="5b3fa-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="5b3fa-217">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="5b3fa-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="5b3fa-218">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="5b3fa-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5b3fa-219">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="5b3fa-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="5b3fa-220">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="5b3fa-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="5b3fa-221">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="5b3fa-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="5b3fa-222">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="5b3fa-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="5b3fa-223">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="5b3fa-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="5b3fa-224">空間マッピングの設計</span><span class="sxs-lookup"><span data-stu-id="5b3fa-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="5b3fa-225">快適性</span><span class="sxs-lookup"><span data-stu-id="5b3fa-225">Comfort</span></span>](comfort.md)

