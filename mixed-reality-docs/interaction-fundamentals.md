---
title: マルチモーダル操作の概要
description: マルチモーダル操作の概要
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 視線入力, 視線入力ターゲット設定, 対話, 設計, HoloLens, MMR, マルチモーダル
ms.openlocfilehash: 7b04141c832597be4bb58447629e0ef6e248dc2b
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415252"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="11414-104">本能的な操作の概要</span><span class="sxs-lookup"><span data-stu-id="11414-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="11414-105">シンプルで本能的な操作の理念は、Mixed Reality プラットフォーム全体に織り込まれています。</span><span class="sxs-lookup"><span data-stu-id="11414-105">The philosophy of simple, instinctual interactions is interwoven throughout the Mixed Reality platform.</span></span>  <span data-ttu-id="11414-106">アプリケーションのデザイナーや開発者が顧客に簡単で直感的な操作を提供できるように、3 つの手順を使用しています。</span><span class="sxs-lookup"><span data-stu-id="11414-106">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="11414-107">1 つ目として、センサーと入力のテクノロジ (自然言語入力に加え、手の追跡と視線追跡が含まれます) をまとめることで、シームレスなマルチモーダル操作モデルを実現できるようにしました。</span><span class="sxs-lookup"><span data-stu-id="11414-107">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  <span data-ttu-id="11414-108">調査に基づくと、本能的なエクスペリエンスを作成する鍵となるのは、単一の入力をベースとせず、マルチモーダル フレームワーク内で設計や開発を行うことです。</span><span class="sxs-lookup"><span data-stu-id="11414-108">Based on our research, designing and developing within a multimodal framework, and not based on single inputs, is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="11414-109">2 つ目として、多くの開発者が複数の HoloLens デバイス (HoloLens 2 と HoloLens (第 1 世代) 、HoloLens と VR など) をターゲットにしていることを認識しています。</span><span class="sxs-lookup"><span data-stu-id="11414-109">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="11414-110">このため、各デバイスで入力テクノロジが異なる場合でも、複数のデバイスで動作するように操作モデルを設計しています。</span><span class="sxs-lookup"><span data-stu-id="11414-110">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  <span data-ttu-id="11414-111">たとえば、6DoF コントローラーによる Windows イマーシブ ヘッドセットの遠隔操作や、HoloLens 2 での遠隔操作は、どちらも同じアフォーダンスとパターンを使用しているため、エンド ユーザーが自然な感覚で操作できるクロス デバイス アプリケーションを簡単に開発できます。</span><span class="sxs-lookup"><span data-stu-id="11414-111">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use  identical affordances and patterns, making it easy for cross-device application development that provides a natural feel to end-user interactions.</span></span> 

<span data-ttu-id="11414-112">Mixed Reality (MR) では効果的、魅力的で魔法のような何千もの操作を実現できますが、ユーザーが成功と優れたエクスペリエンスを実感できる最善の方法は、アプリケーションで意図的にエンドツーエンドの単一操作モデルを使用することであることがわかっています。</span><span class="sxs-lookup"><span data-stu-id="11414-112">While we recognize that there are thousands of effective, engaging, and magical interactions possible in mixed reality (MR), we've found that intentionally employing a single interaction model, end-to-end, in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="11414-113">そのため、この操作ガイドに次の 3 つのことを含めました。</span><span class="sxs-lookup"><span data-stu-id="11414-113">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="11414-114">このガイダンスは、この 3 つの主要な操作モデルと、それぞれに必要なコンポーネントとパターンを中心とした構造になっています。</span><span class="sxs-lookup"><span data-stu-id="11414-114">This guidance is structured around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="11414-115">このプラットフォームが提供するその他のメリットに関する補足的なガイダンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="11414-115">Supplemental guidance has been included about other benefits that our platform provides.</span></span>
* <span data-ttu-id="11414-116">開発シナリオに適した操作モデルの選択に役立つガイダンスも含まれています。</span><span class="sxs-lookup"><span data-stu-id="11414-116">Guidance has also been included to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="11414-117">マルチモーダル操作モデル</span><span class="sxs-lookup"><span data-stu-id="11414-117">Multimodal interaction models</span></span>

<span data-ttu-id="11414-118">調査とお客様からのフィードバックに基づき、3 つの主要な操作モデルは大半の Mixed Reality エクスペリエンスに適していることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="11414-118">Based on our research as well as feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="11414-119">多くの点で、この操作モデルはユーザーのフローを完了するためのメンタル モデルです。</span><span class="sxs-lookup"><span data-stu-id="11414-119">In many ways, the interaction model is the user's mental model for completing their flows.</span></span> <span data-ttu-id="11414-120">これらの各操作モデルは、お客様の一連のニーズに合わせて最適化されています。</span><span class="sxs-lookup"><span data-stu-id="11414-120">Each of these interaction models is optimized for a set of customer needs.</span></span> <span data-ttu-id="11414-121">それぞれ便利で強力であり、それ自体で使用できます。</span><span class="sxs-lookup"><span data-stu-id="11414-121">Each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="11414-122">次の表は、簡単な概要です。</span><span class="sxs-lookup"><span data-stu-id="11414-122">The chart below is a simplified overview.</span></span> <span data-ttu-id="11414-123">各操作モデルを使用するための詳細情報は、イメージとコード サンプルを含むページにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="11414-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="11414-124"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="11414-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="11414-125"><strong>シナリオ例</strong></span><span class="sxs-lookup"><span data-stu-id="11414-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="11414-126"><strong>適した使用方法</strong></span><span class="sxs-lookup"><span data-stu-id="11414-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="11414-127"><strong>ハードウェア</strong></span><span class="sxs-lookup"><span data-stu-id="11414-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="11414-128"><a href="hands-and-tools.md">手とモーション コントローラー</a></span><span class="sxs-lookup"><span data-stu-id="11414-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="11414-129">空間レイアウトやデザインなどの 3D 空間エクスペリエンス、コンテンツの操作、またはシミュレーション。</span><span class="sxs-lookup"><span data-stu-id="11414-129">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="11414-130">音声、視線追跡、頭の視線入力と組み合わせると、新しいユーザーに最適。</span><span class="sxs-lookup"><span data-stu-id="11414-130">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="11414-131">習得が容易。</span><span class="sxs-lookup"><span data-stu-id="11414-131">Low learning curve.</span></span> <span data-ttu-id="11414-132">手の追跡と 6 DoF コントローラーで一貫性のある UX。</span><span class="sxs-lookup"><span data-stu-id="11414-132">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="11414-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="11414-133">HoloLens 2</span></span><br><span data-ttu-id="11414-134">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="11414-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="11414-135"><a href="hands-free.md">ハンズフリー</a></span><span class="sxs-lookup"><span data-stu-id="11414-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="11414-136">実地学習、メンテナンスなど、ユーザーの手が占有されている場合のコンテキスト対応のエクスペリエンス。</span><span class="sxs-lookup"><span data-stu-id="11414-136">Contextual experiences where a user's hands are occupied, such as on-the-job learning, and maintenance.</span></span></td>
        <td><span data-ttu-id="11414-137">いくらかの学習が必要。</span><span class="sxs-lookup"><span data-stu-id="11414-137">Some learning required.</span></span> <span data-ttu-id="11414-138">手が使用できない場合、デバイスにより音声と自然言語が組み合わされる。</span><span class="sxs-lookup"><span data-stu-id="11414-138">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="11414-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="11414-139">HoloLens 2</span></span><br><span data-ttu-id="11414-140">HoloLens (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="11414-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="11414-141">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="11414-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="11414-142"><a href="gaze-and-commit.md">頭の視線入力とコミット</a></span><span class="sxs-lookup"><span data-stu-id="11414-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="11414-143">3D プレゼンテーション、デモなどのクリック スルー エクスペリエンス。</span><span class="sxs-lookup"><span data-stu-id="11414-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="11414-144">移動を除く HMD のトレーニングが必要。</span><span class="sxs-lookup"><span data-stu-id="11414-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="11414-145">アクセシビリティ コントローラーに最適。</span><span class="sxs-lookup"><span data-stu-id="11414-145">Best for accessible controllers.</span></span> <span data-ttu-id="11414-146">HoloLens (第 1 世代) に最適。</span><span class="sxs-lookup"><span data-stu-id="11414-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="11414-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="11414-147">HoloLens 2</span></span><br><span data-ttu-id="11414-148">HoloLens (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="11414-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="11414-149">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="11414-149">Immersive headsets</span></span><br><span data-ttu-id="11414-150">モバイル AR</span><span class="sxs-lookup"><span data-stu-id="11414-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="11414-151">ユーザー操作エクスペリエンスのギャップや欠陥をなくす最善の方法は、1 つのモデルのガイダンスに最初から最後まで従うことです。</span><span class="sxs-lookup"><span data-stu-id="11414-151">To ensure that there are no gaps or holes in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="11414-152">設計と開発を高速化するために、各モデルの説明には、詳細な情報が含まれており、またイメージとコード サンプルへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="11414-152">To speed up design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="11414-153">次のセクションでは、これらの操作モデルからいずれかを選択して実装する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="11414-153">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="11414-154">このページでは、以下についてのガイダンスを理解することができます。</span><span class="sxs-lookup"><span data-stu-id="11414-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="11414-155">顧客の操作モデルの選択</span><span class="sxs-lookup"><span data-stu-id="11414-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="11414-156">操作モデルのガイダンスの使用</span><span class="sxs-lookup"><span data-stu-id="11414-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="11414-157">操作モデル間の遷移</span><span class="sxs-lookup"><span data-stu-id="11414-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="11414-158">次の手順の設計</span><span class="sxs-lookup"><span data-stu-id="11414-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="11414-159">顧客の操作モデルを選択する</span><span class="sxs-lookup"><span data-stu-id="11414-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="11414-160">通常、開発者と作成者は、顧客が使用できる操作の種類を考慮しています。</span><span class="sxs-lookup"><span data-stu-id="11414-160">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="11414-161">顧客中心の設計アプローチを促進するために、次のガイダンスに従って、顧客向けに最適化された操作モデルを選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="11414-161">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="11414-162">ガイダンスに従う理由</span><span class="sxs-lookup"><span data-stu-id="11414-162">Why follow this guidance?</span></span>

* <span data-ttu-id="11414-163">操作モデルは、物理効果、認識効果、直感性、学習性など、主観的および客観的な基準でテストされます。</span><span class="sxs-lookup"><span data-stu-id="11414-163">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="11414-164">操作が異なるため、操作モデル間でビジュアルおよびオーディオ アフォーダンスやオブジェクトの動作が異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="11414-164">Because interactions differ, visual and audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="11414-165">複数の操作モデルの一部を組み合わせると、アフォーダンスが競合するリスクが発生します。たとえば、手の光線と頭の視線カーソルが同時に表示されると、ユーザーが混乱します。</span><span class="sxs-lookup"><span data-stu-id="11414-165">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor that can overwhelm and confuse users.</span></span>

<span data-ttu-id="11414-166">アフォーダンスと動作を最適化する例を操作モデルごとに示します。</span><span class="sxs-lookup"><span data-stu-id="11414-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="11414-167">新しいユーザーが「システムが動作していることはどうすればわかりますか、何ができるかはどうすればわかりますか。自分がしたことをシステムが理解していることはどうすればわかりますか」といった同じような質問をしているのをよく見かけます。</span><span class="sxs-lookup"><span data-stu-id="11414-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="11414-168"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="11414-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="11414-169"><strong>動作していることはどうすればわかりますか?</strong></span><span class="sxs-lookup"><span data-stu-id="11414-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="11414-170"><strong>何ができるかはどうすればわかりますか?</strong></span><span class="sxs-lookup"><span data-stu-id="11414-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="11414-171"><strong>自分が何をしたかはどうすればわかりますか?</strong></span><span class="sxs-lookup"><span data-stu-id="11414-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="11414-172"><a href="hands-and-tools.md">手とモーション コントローラー</a></span><span class="sxs-lookup"><span data-stu-id="11414-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="11414-173">手のメッシュが見える、指先アフォーダンスまたは手やコントローラーの光線が見える。</span><span class="sxs-lookup"><span data-stu-id="11414-173">I see a hand mesh, I see a fingertip affordance or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="11414-174">手を近づけると、グラブ可能なハンドルや境界ボックスが表示される。</span><span class="sxs-lookup"><span data-stu-id="11414-174">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="11414-175">音が聞こえ、グラブやリリースのアニメーションが見える。</span><span class="sxs-lookup"><span data-stu-id="11414-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="11414-176"><a href="gaze-and-commit.md">頭の視線入力とコミット</a></span><span class="sxs-lookup"><span data-stu-id="11414-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="11414-177">視野の中央にカーソルが見える。</span><span class="sxs-lookup"><span data-stu-id="11414-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="11414-178">特定のオブジェクトに重ねると、頭の視線入力カーソルの状態が変わる。</span><span class="sxs-lookup"><span data-stu-id="11414-178">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="11414-179">行動を行うと、視覚または音声でわかる。</span><span class="sxs-lookup"><span data-stu-id="11414-179">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="11414-180"><a href="hands-free.md">ハンズフリー (頭の視線入力とドウェル)</a></span><span class="sxs-lookup"><span data-stu-id="11414-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="11414-181">視野の中央にカーソルが見える。</span><span class="sxs-lookup"><span data-stu-id="11414-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="11414-182">インタラクティブなオブジェクトにドウェルすると、進行状況のインジケーターが見える。</span><span class="sxs-lookup"><span data-stu-id="11414-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="11414-183">行動すると、視覚または音声でわかる。</span><span class="sxs-lookup"><span data-stu-id="11414-183">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="11414-184"><a href="hands-free.md">ハンズフリー (音声コマンド)</a></span><span class="sxs-lookup"><span data-stu-id="11414-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="11414-185">リスニング インジケーターとシステムが聞いた音を表示するキャプションが見える。</span><span class="sxs-lookup"><span data-stu-id="11414-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="11414-186">音声プロンプトとヒントが聞こえる。</span><span class="sxs-lookup"><span data-stu-id="11414-186">I get voice prompts and hints.</span></span> <span data-ttu-id="11414-187">「何を言えますか?」と言うと</span><span class="sxs-lookup"><span data-stu-id="11414-187">When I say: "what can I say?"</span></span> <span data-ttu-id="11414-188">フィードバックが得られる。</span><span class="sxs-lookup"><span data-stu-id="11414-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="11414-189">コマンドを与えると、視覚または音声でわかる。必要な場合は不明瞭解消用の UX が提供される。</span><span class="sxs-lookup"><span data-stu-id="11414-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="11414-190">ヘルプ チームが操作モデルを選択する際に使用している質問を次に示します。</span><span class="sxs-lookup"><span data-stu-id="11414-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="11414-191">Q:ユーザーがホログラムにタッチして細かい操作を行うことはありますか?</span><span class="sxs-lookup"><span data-stu-id="11414-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="11414-192">A:その場合は、厳密なターゲット指定や、手またはモーション コントローラーによる操作を行うために、手とモーション コントローラーの操作モデルを確認します。</span><span class="sxs-lookup"><span data-stu-id="11414-192">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="11414-193">Q:ユーザーは、現実世界で作業を行うために、手を空けておく必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="11414-193">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="11414-194">A:その場合は、ハンズフリー操作モデルを確認します。このモデルは、視線入力または音声ベースの操作で優れたハンズフリー エクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="11414-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="11414-195">Q:ユーザーには MR アプリケーションの操作を学習する時間はありますか? それとも、最低限の学習で操作を行う必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="11414-195">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="11414-196">A:ユーザーが手で操作を行うことができ、最低限の学習で最も直感的に操作を行いたい場合は、手とモーション コントローラーのモデルをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="11414-196">A:  We recommend the Hands and motion controllers model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="11414-197">Q:ユーザーがポイントしたり操作したりする際、モーション コントローラーを使用しますか?</span><span class="sxs-lookup"><span data-stu-id="11414-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="11414-198">A:手とモーション コントローラーのモデルには、モーション コントローラーを使用してすばらしいエクスペリエンスを実現するためのガイダンスがすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="11414-198">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="11414-199">Q:ユーザーは、アクセシビリティ コントローラーやクリッカーなどの一般的な Bluetooth コントローラーを使用しますか?</span><span class="sxs-lookup"><span data-stu-id="11414-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="11414-200">A:すべての非追跡コントローラーには、頭の視線入力とコミットのモデルをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="11414-200">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="11414-201">ユーザーが単純な「ターゲット指定とコミット」機構によるエクスペリエンス全体を利用できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="11414-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="11414-202">Q:ユーザーは、UI コントロールが詰まったレイアウトを操作するのではなく、「クリックスルー」によってのみエクスペリエンスを進行させることができますか (たとえば、3D スライド ショーのような環境)?</span><span class="sxs-lookup"><span data-stu-id="11414-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="11414-203">A:ユーザーが多くの UI を制御する必要がない場合は、頭の視線入力とコミットを使うと、ターゲットの指定について悩むことなく学習できるオプションを提供できます。</span><span class="sxs-lookup"><span data-stu-id="11414-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="11414-204">Q:ユーザーは HoloLens (第 1 世代) と HoloLens 2/Windows Mixed Reality イマーシブ ヘッドセット (VR) の両方を使用しますか?</span><span class="sxs-lookup"><span data-stu-id="11414-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="11414-205">A:頭の視線入力とコミットは HoloLens (第 1 世代) の操作モデルであるため、HoloLens (第 1 世代) をサポートする作成者は、ユーザーが HoloLens (第 1 世代) ヘッドセットを使用する可能性があるすべての機能やモードで、頭の視線入力とコミットを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="11414-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="11414-206">複数の世代の HoloLens で優れたエクスペリエンスを作成する詳しい方法については、*操作モデルの遷移*について取り上げた次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="11414-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="11414-207">Q:通常は移動可能 (広い領域をカバーする、またはスペース間を移動する) なユーザーと、1 つのスペースで作業することが多いユーザーを比較するとどうなりますか?</span><span class="sxs-lookup"><span data-stu-id="11414-207">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="11414-208">A:どの操作モデルでも、これらのユーザーに対応できます。</span><span class="sxs-lookup"><span data-stu-id="11414-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="11414-209">アプリの設計に特化したガイダンスは、[近日中に公開](index.md#news-and-notes)します。</span><span class="sxs-lookup"><span data-stu-id="11414-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="11414-210">操作モデルの遷移</span><span class="sxs-lookup"><span data-stu-id="11414-210">Transitioning interaction models</span></span>
<span data-ttu-id="11414-211">複数の操作モデルが必要になるユース ケースもあります。</span><span class="sxs-lookup"><span data-stu-id="11414-211">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="11414-212">たとえば、アプリケーションの作成フローで手とモーション コントローラー操作モデルを利用しつつ、現場技術者向けにハンズフリー モードを使用する場合などです。</span><span class="sxs-lookup"><span data-stu-id="11414-212">For example, your application's creation flow utilizes the Hands and motion controllers interaction model, but you want to employ a hands-free mode for field technicians.</span></span>  

<span data-ttu-id="11414-213">エクスペリエンスに複数の操作モデルが必要な場合、一方のモデルから他方のモデルに遷移するときに、多くのエンド ユーザーが困難を感じるので注意してください。特に、Mixed Reality を初めて使用するユーザーはそれが顕著です。</span><span class="sxs-lookup"><span data-stu-id="11414-213">If your experience does require multiple interaction models, keep in mind that many end users might encounter difficulty when transitioning from one model to another--especially for users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="11414-214">開発者やデザイナーが使用できるガイダンスの作成に常に取り組んでおり、複数の MR 操作モデルを使用するための方法、タイミング、および理由についてお知らせしています。</span><span class="sxs-lookup"><span data-stu-id="11414-214">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="11414-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="11414-215">See also</span></span>
* [<span data-ttu-id="11414-216">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="11414-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="11414-217">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="11414-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="11414-218">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="11414-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="11414-219">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="11414-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="11414-220">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="11414-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="11414-221">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="11414-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="11414-222">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="11414-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="11414-223">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="11414-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="11414-224">空間マッピングの設計</span><span class="sxs-lookup"><span data-stu-id="11414-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="11414-225">快適性</span><span class="sxs-lookup"><span data-stu-id="11414-225">Comfort</span></span>](comfort.md)

